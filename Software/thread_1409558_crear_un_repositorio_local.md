---
title: "crear un repositorio local"
date: 2010-02-17
forum: Software
---

### Post by hatteras22 on 2010-02-17
La idea es crear un repositorio local con los paquetes.deb que hemos ido bajando, guardando e instalando de alguna página web, ( que hemos ido almacenando en, por ejemplo, /media/mi-disco/deb ) para que puedan ser instalados o reinstalados con Synaptic : Los primeros 4 pasos los vamos a realizar con la Terminal, y el 5º y 6º con Synaptic.

Naturalmente todas las direcciones de los directorios ( en rojo ) que pongo son solo un ejemplo y tienen que ser sustituidas por las direcciones que consideres oportuno.

Paso 1- Crear una carpeta /paquetes, es muy importante que esté en una partición que tenga permisos de lectura-escritura, por ejemplo: si tenemos una partición con esos permisos en /media/mi-disco , creamos la carpeta con: $ sudo mkdir /media/mi-disco/paquetes

Paso 2- Copiar todos los paquetes *.deb en este directorio: &#65279;&#65279;&#65279;cp /media/mi-disco/deb/*.deb /media/mi-disco/paquetes

Paso 3- Crear el archivo Packages.gz : vamos al directorio: $ cd /media/mi-disco y ejecutamos la orden: $ sudo dpkg-scanpackages paquetes /dev/null | gzip -c > paquetes/Packages.gz.
Lo que hacemos con el comando dpkg-scanpackages es leer todos los archivos *.deb que tenemos en el directorio y con gzip creamos el archivo Packages.gz que indica a apt cuales son los paquetes que luego podremos instalar.

Paso 4-Editar el archivo sources.list, con: $ sudo gedit /etc/apt/sources.list Añadimos al final de dicho archivo: deb file:/media/mi-disco/paquetes/
Guardas los cambios y cierras la terminal.

Paso 5- Ejecutar Synaptic y recargar la información de paquetes: (Sistema->Administración->Gestor de Paquetes Synaptic -> Editar -> Recargar Información de paquetes ), ( o bien desde un terminal ejecutas: $ sudo apt-get update ).

Paso 6- Usar el repositorio local para instalar paquetes: A partir de ahí podrás instalar también los paquetes que tienes en este repositorio local desde Synaptic.

Para tener actualizado este repositorio local hay que tener actualizado el archivo Packages.gz, y para ello hay que repetir de vez en cuando los pasos 2 , 3 y 5.

Extraido de [http://hatteras.wordpress.com/2010/02/18/crear-un-repositorio-local/]("http://hatteras.wordpress.com/2010/02/18/crear-un-repositorio-local/")

---

### Post by z37a on 2010-02-17
Si te sirve de algo, los paquetes que bajas por apt en actualizaciones se cachean en /var/cache/apt/archives Podria montar un disco nfs en esa ruta y usar solo una para actualizar, entonces no tendrias que bajar en cada PC los paquetes!

---

### Post by Tosh78 on 2010-02-17
Muy buena data! Muchas gracias

---

### Post by fmsismo on 2010-02-18
Lo mas cómodo es poner un proxy de paquetes y configurar el apt para que use eso.  

Descargas solo que necesitas y se hace todo solo una vez que lo tenes configurado.

En mi trabajo tengo configurado uno para hacer las actualizaciones de los destop de desarrollo (9.10) y los servidores (8.04).

Documente el procedimiento de como instalarlo en el 2008 pasado.  [http://www.sismonda.com.ar/procedimientos/apt-cache-ng](http://www.sismonda.com.ar/procedimientos/apt-cache-ng)

Saludos

---

