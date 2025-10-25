# Ejercicio 1 del modulo 07 Cloud

En este ejercicio vamos a ver 2 formas de poder subir nuestro proyecto a GitHub Pages

Para ello hemos copiado el proyecto del modulo06-rest-api [Ejercicio1](https://github.com/tizon15/lemoncode_master/edit/master/modulo06-rest-api/Ejercicio1)

---

### Opción 1 

En esta opción la tarea principal es subir los ficheros estáticos a nuestra rama *gh'pages*

Para ello lo que hemos hecho es, crear la rama **gh-pages** en nuestro repositorio usando el comando ***git branch gh-pages***

Una vez tenemos el proyecto en la rama *master* y la rama **gh-pages** creada, hacemos un **npm install** para instalar las dependecias del proyecto. 

Primero, tenemos que hacer una modificacion en nuestro *vite.config.ts*. Que es añadir la linea ***base: './',***. Con esta linea nos aseguramos que los assets apunten al sitio correcto.

Una vez cambiada la configuracion y con las dependencias descargas hacemos un **npm run build** para compilar el proyecto.

Ahora, debido a que tenemos comentado la carpeta **dist** en nuestro fichero *.gitignore* lanzamos el comando ***git checkout gh-pages*** para cambiar a la rama correspondiente. Y eliminamos todo menos el contenido de la carpeta *dist*. Movemos el directorio **assets** y el ficher **index.html** a la raiz del proyecto.

Ahora que nuestra rama solo tiene las partes mencionadas. Añadimos nuestros ficheros a git con **git add .**, lo comiteamos con **git commit -m "deploy de ficheros estaticos"** y lo subimos a GitHub con **git push origin gh-pages**

Para visualizarlo, solo hay que ir a la URL https://tizon15.github.io/lemoncode-07-cloud-lab1/#/characters

---

### Opción 2 

Esta opción es mas automática para hacer el deploy. Lo primero es empezar en la rama *master* con **git checkout master**

Una vez en esta rama, nos tenemos que descargar el paquete gh-pages de (npm)[https://www.npmjs.com/package/gh-pages]. Usando el comando **npm install gh-pages --save-dev**

Cuando esté hecho esta parte tendremos que modificar nuestro *package.json* para añadir el script correspondiente. Con esta linea lo añadiriamos, ***"deploy": "gh-pages -d dist",***. Usamos el flag *-d* para decir que directorio queremos subir, en este caso **dist**

Con estas modificaciones, solo tendriamos que lanzar los comandos correspondientes

**npm run build** para compilar el proyecto
**npm run deploy** para publicar nuestro proyecto en GitHub Pages

Para visualizarlo, solo hay que ir a la URL https://tizon15.github.io/lemoncode-07-cloud-lab1/#/characters