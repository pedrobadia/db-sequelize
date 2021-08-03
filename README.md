Micro desafío - Paso 1:

Utilizaremos de base el siguiente proyecto creado con Express, junto a esta base de datos: movies_db.
Una vez realizada la instalación de todas las dependencias del proyecto, debemos efectuar lo siguiente:
1. Instalar el paquete Sequelize: para lograr el objetivo es fundamental lograr instalar Sequelize y los paquetes relacionados necesarios.
npm install sequelize-cli -g
npm install sequelize
npm install mysql2

2. Una vez instalados los paquetes, será fundamental la creación del archivo .sequelizerc ( lo podemos crear en la raíz del proyecto) con la siguiente estructura:
const path = require('path')
module.exports = {
config: path.resolve('./database/config', 'config.js'), 'models-path': path.resolve('./database/models'), 'seeders-path': path.resolve('./database/seeders'), 'migrations-path': path.resolve('./database/migrations'),
}

3. Luego, es fundamental correr el comando sequelize init

4. Finalmente no debemos olvidarnos de modificar el archivo /database/config/config.js a gregando module.exports al principio del archivo y configurando los datos de conexión a la base de datos.


Micro desafío - Paso 2:
Algo fundamental al inicializar un proyecto es explicarle a sequelize las tablas que tiene nuestra base de datos. Para esto debemos crear los m odelos p ara las tablas movies y genres (Películas y Géneros).
No debemos olvidarnos de aclarar el nombre de la tabla, si usa timestamps y todas sus columnas con su tipo. Recomendamos aclarar los datos como columnas que aceptan nulo así como clave primaria y autoincremental.


Micro desafío - Paso 3:
Es fundamental que el controlador importe la variable db de ./database/models/index.js ya que esta variable tendrá nuestra conexión a la base de datos.
Para la construcción de esta versión del sitio web, el cliente espera contar con la posibilidad de acceso a las siguientes URLs:

● /movies (GET)
Se deberán listar todas las películas de la base de datos. Cada título de película deberá ser un hipervínculo para ver el detalle de la misma.
El controlador deberá utilizar la conexión a base de datos y el modelode Movie ya creado. Con eso en mente, el método f indAll permitirá obtener todas las películas de la base de datos.

● /movies/detail/:id (GET)
Detalle de la película. Se deberá mostrar la película correspondiente al id que aparezca en la URL. Cada película deberá listar sus datos (Título, rating, premios, duración y fecha de estreno).
El controlador deberá utilizar la conexión a la base de datos y el modelo de M ovie ya creado. Con eso en mente, el método f indByPk permitirá obtener la película buscada. Recordemos utilizar req.params para obtener el id de la URL.

● /movies/new (GET)
El controlador deberá utilizar la conexión a base de datos y el modelo de M ovie ya creado. Con eso en mente el método f indAll, junto con el parámetro de configuración o rder permitirá obtener todas las películas de la base de datos.

● /movies/recommended (GET)
Deberá mostrar las últimas 5 películas ordenadas según su fecha de estreno.
El controlador deberá utilizar la conexión a la base de datos y el modelo de M ovie ya creado. Con eso en mente, el método f indAll permitirá obtener todas las películas de la base de datos. En este caso necesitaremos agregar el parámetro de configuración where y utilizar los operadores de Sequelize para resolver el desafío.

● /genres (GET)
Se deberán listar todos los géneros de la base de datos. Cada género deberá ser un hipervínculo para ver el detalle del mismo.
El controlador deberá utilizar la conexión a la base de datos y el modelo de G enre ya creado. El método findAll permitirá obtener todos los géneros de la base de datos.

/genres/detail/:id (GET)
Detalle del género. Se deberá mostrar del género correspondiente al id que aparezca en la URL. Cada género deberá listar sus datos (Id, name, ranking).
El controlador deberá utilizar la conexión a la base de datos y el
modelo de G enre ya creado. De esta manera, el método f indByPk permitirá obtener el género buscado. Recordemos utilizar req.params para obtener el id de la URL.
Bonus track:

Si logramos realizar toda la práctica, una buena idea es replicar el proceso, pero con el m odelo Actores.
