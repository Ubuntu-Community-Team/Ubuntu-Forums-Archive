---
title: "wordpress"
date: 2009-06-02
forum: Software
---

### Post by rony3 on 2009-06-02
Hola, acabo de instalar wordpress sobre ubuntu 9.04 y en principio todo bien. El problema es al acceder desde otro pc de mi red local, SOLO VEO TEXTO. Esto no me ocurre si accedo desde el pc en el que tengo instalado wordpress.
He leído este hilo:

[http://www.ubuntu-es.org/index.php?q=node/48525](http://www.ubuntu-es.org/index.php?q=node/48525)

No encuentro "pagina de configuracion de wordpress". En el fichero wp-config.php no hay ninguna opcion de ese tipo.

Gracias.

---

### Post by pablo.s on 2009-06-02
Hola: Has seguido las instrucciones
de Wordpress? Tienes el servidor
de MySQL funcionando? La base de
datos incorporada? Es muy fácil la
instalación pero se te puede haber
salteado un paso...

---

### Post by rony3 on 2009-06-02
> **pablo.s said:**
> Hola: Has seguido las instrucciones
de Wordpress? Tienes el servidor
de MySQL funcionando? La base de
datos incorporada? Es muy fácil la
instalación pero se te puede haber
salteado un paso...

Seguí el hilo siguiente para su instalación:

[http://www.cybernautas.es/articulos_linux/instalar-wordpress-en-ubuntu/](http://www.cybernautas.es/articulos_linux/instalar-wordpress-en-ubuntu/)

En mi caso apache+myslq+php  lo instale desde  Synaptic => Editar => Marcar  paquetes por tarea => LAMP SERVER. Te lo deja todo configurado y funciona perfectamente. 
Por lo que he leído para instalar wordpress tan solo hay que bajarse el archivo [COLOR=#006699]wordpress-2.6.2-es_ES.tar.gz[/COLOR] , descomprimirlo, entrar en el directorio creado y editar wp-config.php (crearlo) con los datos de configuración que vienen en el hilo anterior. 

// ** Ajustes de MySQL. Solicita estos datos a tu proveedor de alojamiento web. ** //
/** El nombre de tu base de datos de WordPress */
define('DB_NAME', [COLOR=Red]'wordpress[/COLOR]');   //  puedo acceder desde una terminal de mysql

/** Tu nombre de usuario de MySQL */
define('DB_USER',[COLOR=Red] 'root[/COLOR]');

/** Tu contraseña de MySQL */
define('DB_PASSWORD', [COLOR=Red]'miclavedeMySql'[/COLOR]);

/** Host de MySQL (es muy probable que no necesites cambiarlo) */
define('DB_HOST', [COLOR=Red]'localhost'[/COLOR]);

/** Codificación de caracteres para la base de datos. */
define('DB_CHARSET',[COLOR=Red] 'utf8'[/COLOR]);

/** Cotejamiento de la base de datos. No lo modifiques si tienes dudas. */
define('DB_COLLATE', '');



Así lo hice y no me dió ningun problema, de hecho me salió el mensaje de se ha instalado wordpress  o algo así.  Puedo acceder a la base de datos de wordpress que creé con phpmyadmin como a cualquier otra y entrar en [http://localhost/wordpress](http://localhost/wordpress) donde me aparece el "hola mundo" con el titulo del primer blog recien creado.
Tambien puede entrar en [http://localhost/wordpress/wp-admin/](http://localhost/wordpress/wp-admin/) para el tema de manejo del wordpress y todo eso. Ya digo que me va bien  salvo cuando accedo desde una maquina externa (de mi red local) . Si pongo[COLOR=Red] [http://192.168.1.33/wordpress](http://192.168.1.33/wordpress) [/COLOR]pues me sale el blog de inicio anterior pero todo en modo texto, sin graficos. 

De todas formas seguí el hilo anterior porque es reciente (noviembre del 2008 ,sobre ubuntu y  viene muy bien explicado. Como tu dices la instalación es sencilla.

Miraré en la pagina oficial de wordpress a ver si viene algo sobre esto.

---

### Post by mama21mama on 2009-06-14
Probaste Drupal? anda muy bien tambien

---

