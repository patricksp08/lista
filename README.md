# Lista de compras - React

[![Netlify Status](https://api.netlify.com/api/v1/badges/58074a7f-679f-4bb0-b97c-0f2c6b055aba/deploy-status)](https://app.netlify.com/sites/listadecomprasreact/deploys)

**Site hospedado: [Netlify](https://listadecomprasreact.netlify.app/)**

**Baseado no tutorial do blog [COD3R](https://blog.cod3r.com.br/utilizando-hooks-usestate/)**

## **Ambientes de Desenvolvimento e Referências**

* IDE:    **VSCODE 1.55.1**
* [Node.js](https://nodejs.org/en/):    **version 14.16.0 (x64) and NPM**



## Criando o projeto

### Para criarmos todos arquivos necessários, abra o prompt de comando e insira o seguinte comando:
```
npx create-react-app list
```

* Assim criaremos uma pasta chamada "list" no caminho selecionado.

![image](https://user-images.githubusercontent.com/71887999/114571277-eba77580-9c4c-11eb-89e4-d6e4eb751307.png)

### Para abrirmos a pasta no visual studio code, utilize os seguintes comandos:

* #### Entrar na pasta (no caminho em que você criou a pasta anteriormente):
 ```
 cd list
 ```

* #### Abrir no VS Code:
 ```
 code .
 ```

## Hooks - UseState

UseState é uma nova forma de definir e atualizar (mutar) o estado “interno ”de um componente. Mais limpo e menos verboso esse é com certeza um dos melhores hooks lançados nessa versão 16.8.

1 - Vamos importar ele da seguinte forma no App.js: 
```
import React, { useState } from 'react';
````

2 - Logo em seguida, o utilizaremos no App.js:
```
const [item, setItem] = useState('');
````

3 - E como nosso código depende de um INPUT, precisamos modifica-lo da seguinte forma para funcionar com o useState:
```
<input type="text" placeholder="Item" value={item} name="item" onChange = {e => setItem(e.target.value)} />
````

4 -  Além disso, precisamos de duas coisas:

- Um outro estado capaz de armazenar uma lista
- Uma função que seja capaz de adicionar o valor à lista

*Para criarmos outro estado, é simples:*
```
const [itemList, setItemList] = useState([])
````

*E a função para conseguirmos adicionar itens também:*
```
const addItem = () => {
    setItemList([item].concat(itemList))
    setItem('')
}
````

5 - Também precisamos garantir que a função addItem que criamos seja chamada quando clicarmos no botão para inserir o que foi escrito no input dentro da lista. Para isso, vamos inserir um evento Onclick, referenciando o addItem:
```
<button onClick={addItem}>Adicionar Item</button>
````

6 - Para finalizar, temos que dar uma estrutura de lista para nosso código, e que essa estrutura receba os itens dentro do Array (array vazio do segundo estado que criamos) e renderize na tela. Para isso vamos utilizar o map:
```
      <ul>
        {itemList.map((item) => (
          <li>{item}</li>
        ))}
      </ul>
````
