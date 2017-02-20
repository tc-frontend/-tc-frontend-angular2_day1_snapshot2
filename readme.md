


Angular 2: Getting Started - SnapShot 2
===================

En esta sección cubriremos los siguientes puntos de Pluralsight:

 - Templates
 - Interpolation
 - Directives


----------


### 1 - Definición de templates


----------


Las vistas o templates HTML de los componentes se pueden definir **Innine** o pueden crearse de forma separada en un fichero aparte.


La creación de un componente siempre implica:


1. Creación de un folder


2. Creación de un componente dentro del folder


3. Creación de una template dentro del folder
 
 
Ejemplo:
 
 
**- folder:** nombre_componente

**- componente:** nombre_componente.component.ts
 
**- template:** nombre_componente.component.html
 

En el momento de asociar el componente y la template definiremos en el **Decorator** la propiedad **templateUrl**:

![enter image description here](https://i.imgur.com/tyNspLM.jpg)


----------


### 2 - Crear e importar un nuevo componente


----------



Una vez tenemos definido un componente con una template externa tenemos que conocer la forma de importar componentes a nuestro componente **root**. 


Al exportarse el nuevo componente como **"pm-products"** tenemos la posibilidad de añadirlo directamente en la template del componente **root** de la aplicación.

![enter image description here](https://i.imgur.com/iQYayVU.jpg)


----------


### 3 - Registrar un nuevo componente


----------


El siguiente paso será registrar el componente dentro del Módulo a fin de que el módulo cargue el componente y esté listo para su ejecución. Para ello bastará con:

1. Acceder al módulo principal.


2. Realizar un "imports" del componente.


3. Añadir el componente importado en la lista de "declarations"


![enter image description here](https://i.imgur.com/MhLBYjQ.png)



----------


### 4 - Interpolation


----------


Angular mediante la interpolación permite mostrar propiedades y valores de retorno de funciones del componente dentro de las vistas HTML. 
Hay varias formas de realizar la interpolación:

![enter image description here](https://i.imgur.com/XnolA73.jpg)




----------


### 6 - Directivas


----------


Mediante el uso de directivas podemos realizar acciones condicionales y bucles en la template HTML para renderizar datos del componente:
 

![enter image description here](https://i.imgur.com/kHW1wd1.jpg)


![enter image description here](https://i.imgur.com/TVMSmnz.jpg)


----------


### Práctica


----------



![enter image description here](https://i.imgur.com/EW0hShu.png)


El objetivo es crear un componente que muestre una lista de productos. 
El componente tendra la plantilla en un html y utilizarelos 'templateUrl' para referenciarlo.
Dentro del comonente crearemos una propiedad que contenga un array de productos y utilizando directivas ngIf y ngFor dotaremos de logica a la plantilla. 

Para ello clonamos el **SnapShot2** desde le primer commit de:

    git clone https://github.com/tc-frontend/course_angular2_day1_snapshot2
    cd course_angular2_day1_snapshot2
    git checkout tags/init
    npm install
    code .
-----
-----
#### 1 - Crear un componente para listar los productos
Este componente tenra un filtro que permitira filtar los productos por nombre.
Nos apollamos en este HTML 

    <div class="panel panel-primary">
        <div class="panel-heading">
            Product List
        </div>
        <!-- Filter the Products   -->
        <div class='panel-body'>
            <div class='row'>
                <div class='col-md-2'>Filter by:</div>
                <div class='col-md-4'>
                    <input type='text' />
                </div>
            </div>
            <div class='row' *ngIf='listFilter'>
                <div class='col-md-6'>
                    <h3>Filtered by: </h3>
                </div>
            </div>
              <div class='table-responsive'>
                <table class='table'>
                    <thead>
                        <tr>
                            <th>
                                <button class='btn btn-primary'>
                                    Show Image
                                </button>
                            </th>
                            <th>Product</th>
                            <th>Code</th>
                            <th>Available</th>
                            <th>Price</th>
                            <th>5 Star Rating</th>
                        </tr>
                    </thead>
                    <tbody></tbody>
                </table>
            </div> 
        </div>
    </div> 

 https://goo.gl/D6r0WJ
 
----------
#### 2 - Referenciar el control desde la plantilla del component principal (app.component)
Para ello tenemos que poner el selector que hayamos definido en la clase

    <pm-products></pm-products>
https://goo.gl/X4M3UM

----------
#### 3 -  Declarar el componente en el modulo principal
Deberemos importar elcomponente y añadirlo al array de declaraciones.

https://goo.gl/cj63VY

----------
#### 4 - Actualizar el heading con iterpolacion


https://goo.gl/5Vwlm0


----------
#### 5 - Crear propiedad products y olcultar la tabla cuando no haya datos con *ngIf

Para la tabla:

    <table class='table'
                     *ngIf='products && products.length'>

Para los productos:

    products: any[] = [
            {
                "productId": 2,
                "productName": "Garden Cart",
                "productCode": "GDN-0023",
                "releaseDate": "March 18, 2016",
                "description": "15 gallon capacity rolling garden cart",
                "price": 32.99,
                "starRating": 4.2,
                "imageUrl": "http://openclipart.org/image/300px/svg_to_png/58471/garden_cart.png"
            }
        ];

https://goo.gl/4bJs8N

----------
#### 6 - Iterar los productos con *ngFor

Necesitamos dentro del tbody añadir este tr e iterarlo

    <tbody>
          <tr *ngFor='let product of products'>
             <td>{{product.productName}}</td>
             <td>{{ product.productCode }}</td>
             <td>{{ product.releaseDate }}</td>
             <td>{{ product.price}}</td>
             <td>{{ product.starRating}}</td>
         </tr>
     </tbody>




 
Seguimos los pasos detallados en el historial de commits:

  https://goo.gl/x4FGPD 
  
Si queremos ver la App en nuestro browser

    npm start

Si queremos ver la solucion final de este SnapShot:

    git checkout master
    npm install
    npm start





