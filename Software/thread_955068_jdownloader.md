---
title: "jdownloader"
date: 2008-10-21
forum: Software
---

### Post by tsueseres on 2008-10-21
hay alguna manera de hacer que jdownloader se cargue al inicio

---

### Post by Mtkr on 2008-10-21
Hola yo lo que hice fue un lanzador en el escritorio, lo que me falta en reconectador para que renueve la ip

---

### Post by tsueseres on 2008-10-21
> **Mtkr said:**
> Hola yo lo que hice fue un lanzador en el escritorio, lo que me falta en reconectador para que renueve la ip

como un lanzador?, se que para abrir jdownloader se tiene que correr unos comandos

---

### Post by sajnox on 2008-10-21
Si mal no te entiendo queres que cuando prendes la computadora el jdwonloader levante si que tengas que ir a buscarlo.

Para eso lo que tenes que hacer es:

Sistema > Preferencias > Sesiones

Elegis añadir y en Nombre podes poner cualquier cosa y en orden el comando que ejecuta jdownloader que creo que es precisamente "jdownloader" (sin comillas) 

Eso deberia funcionar

---

### Post by tsueseres on 2008-10-21
> **sajnox said:**
> Si mal no te entiendo queres que cuando prendes la computadora el jdwonloader levante si que tengas que ir a buscarlo.

Para eso lo que tenes que hacer es:

Sistema > Preferencias > Sesiones

Elegis añadir y en Nombre podes poner cualquier cosa y en orden el comando que ejecuta jdownloader que creo que es precisamente "jdownloader" (sin comillas) 

Eso deberia funcionar

en realidad  se ejecuta esto estando dentro de la carpeta 
java -jar JDownloader.jar

so como lo pondria en el comando

---

### Post by c4d0rn4 on 2008-10-21
yo uso un lanzador (cacero, no se si es del todo correcto) y tengo 
```

java -jar -Xmx512m /home/usuario/jDownloader/JDownloader.jar

```

ojo con la carpeta al final, la idea es que llegue al JDownloader.jar, Lo cual depende de donde lo hayas puesto.

Para que se ejecute al iniciar hacé lo que dice sajnox, pero donde dice comando poné lo que puse arriba pero editado como corresponda.

edit: no estaba antes el post de tsueseres =P... pero si, más o menos decimos lo mismo. El -Xmx512m que puse arriba probablemente sea absolutamente de más y determine que consuma más memoria, si mal no tengo entendido, pero la verdad que no entiendo mucho lo que hace ese parametro xD.

---

### Post by Kabezon on 2008-10-22
Fácil. Sistema > Preferencias > Sesiones > Añadir y se debería ver algo así:

> Nombre: JDownloader
Orden: java -jar -Xmx512m /home/usuario/.jdownloader/JDownloader.jar

Fijate bien en las mayúsculas, por ahí vos lo tenés distinto, y también tené en cuenta en dónde tenés guardado la carpeta del jdownloader (Yo lo tengo en Home y oculto) Por las dudas también tirá "sudo apt-get install openjdk-6-jre" en una terminal; sin ese paquete no te va a funcionar el comando. 

El mismo comando se aplica para crear un lanzador: Click derecho sobre el menú principal > Editar los menús y en la sección Internet le ponés "Elemento nuevo" y rellenás. 

Ejemplo:
> 
Tipo: Aplicación
Nombre: JDownloader
Comando: java -jar -Xmx512m /home/usuario/.jdownloader/JDownloader.jar
El icono lo encontrás en .jdownloader/jd/img/jd_logo.png, espero que se entienda.

> **c4d0rn4 said:**
> El -Xmx512m que puse arriba probablemente sea absolutamente de más y determine que consuma más memoria, si mal no tengo entendido, pero la verdad que no entiendo mucho lo que hace ese parametro xD.
Lo que hace es darle a Java más swap. En PCs lentas se nota la diferencia, supongo. Ahora lo pongo en prueba a ver que diferencias hay, y edito para decirte cómo me fue.

[EDIT]
Flaco, sin darte cuenta sos un groso XD El Java pasó de comerme 103MB de RAM a comerme solo 66MB y de comerme 17% de CPU a comerme un increíble 0% xD! Gracias por el dato :P

---

### Post by EnriqueK on 2008-10-22
Supongo que se podrá hacer mediante un script, algo así como

#!/bin/sh

cd ruta_a_la_carpeta_del_ejecutable
java -jar JDownloader.jar 

Luego le guardás y seguidamente vas al menú Sistema -> Prederencias->Sesiones -> programas de inicio -> Añadir y buscás el script que por supuesto debes darle el atributo de ejecutarse como programa.

En lo personal prefiero un lanzador al escritorio por que algunas veces los programas que se cargan al inicio dan problemas por que pueden intentar abrirse antes que cargue completamente el sistema, lo que puede terminar no abriéndose, obligando a reallizarlo manualmente.

---

### Post by tsueseres on 2008-10-22
gracias por la ayuda

---

### Post by tsueseres on 2008-10-23
me intereso eso de crear un ejecutable pero como lo creo este es el comando que uso para abrirlo

java -jar -Xmx512m /home/luis/programas/JDownloader/JDownloader.jar

---

### Post by c4d0rn4 on 2008-10-23
En tu caso y respondiendo lo que pedis, un ejecutable, sería así

Abris gedit (o otro text editor) y pegás esto

```

#!/bin/sh
java -jar -Xmx512m /home/luis/programas/JDownloader/JDownloader.jar

```

Guardas el archivo como nombre.sh en la carpeta que lo quieras. Por último tenes que darle click derecho al archivo, propiedades, solpa permisos, tildar permitir ejecutar, aceptar.

MI recomendación es, click derecho sobre el desktop, creat launcher, ahí pones los parametros que ejecutas y por último hasta podes ponerle el png que trae jdownloader en la carpeta jd/img

---

### Post by ramiro_md on 2008-11-16
> **Kabezon said:**
> "sudo apt-get install openjdk-6-jre" en una terminal; sin ese paquete no te va a funcionar el comando. 


Tengo esa librería instalada, y la jdk también y le doy doble click al lanzador y no arranca nada :confused:

Nota: probe con compiz y metacity.

---

### Post by pol666 on 2008-11-16
Recien me entero que el Jdownaloder baja de videos de youtube y los convierte. para ser perfecto le hace falta cocinar y planchar

---

### Post by c4d0rn4 on 2008-11-16
> **pol666 said:**
> Recien me entero que el Jdownaloder baja de videos de youtube y los convierte. para ser perfecto le hace falta cocinar y planchar

de verdad? wow!

y si plancha me voy a vivir solo, le dejo la pila de ropa en lista de espera y que planche. :lolflag:

---

