---
title: "instalación de corrector ortográfico en Zimbra"
date: 2011-08-23
forum: Software
---

### Post by asterix77 on 2011-08-23
Hola a todos.

He instalado Zimbra Desktop como agente de correos en mi notebook con Lucid, todo perfecto, excepto que se instala con un diccionario en inglés. Quisiera colocarle uno en español para la corrección, pero no lo he podido lograr.

He seguido los pasos del siguiente link [http://lalegiondeyoda.wordpress.com/2009/07/07/cambiar-diccionario-de-zimbra-a-espanol/](http://lalegiondeyoda.wordpress.com/2009/07/07/cambiar-diccionario-de-zimbra-a-espanol/)

pero en la sección de ./configure me aparece el siguiente error:

#./configure
Finding Dictionary file location ... ./configure: 75 aspell: not found

Finding Data file location ... ./configure: 79 aspell: not found

Espero que alguien me pueda ayudar.

Saludos

---

### Post by guillermolisi on 2011-08-23
Pareceria que esta esperando que "aspell" se encuentre en una ubicacion que no es la que en realidad tiene en Ubuntu, o que directamente no tenes instalado "aspell".

En una terminal/consola ingresa ```
guille@guillermo:~$ whereis aspell
``` y te dira, siempre que lo tengas instalado, en donde se encuentra. Ejemplo:
```
aspell: /usr/bin/aspell /usr/lib/aspell /usr/share/aspell /usr/share/man/man1/aspell.1.gz
guille@guillermo:~$
```
Si la variable de configuracion tiene definida una ubicacion diferente, deberas adecuarla para que poder configurar y compilar bien.

Lo que interesa, segun interpreto del mensaje de error que mostraste, es que no encuentra /usr/lib/aspell y /usr/share/aspell

---

### Post by asterix77 on 2011-08-23
Guillermo, gracias por tu respuesta. 

Efectivamente no estaba instalado aspell, lo he instalado y he avanzado. Ahora estoy atascado en la sección de edición del archivo aspell.php

zimbra:/opt/zimbra/aspell6-es-1.9a-1# [COLOR=#CC99FF]vim /opt/zimbra/httpd/htdocs/aspell.php

[COLOR=Black]No tengo ningún archivo aspell.php en esa ruta ni en ninguna otra. Aclaro que la versión instalada es la [/COLOR][/COLOR][aspell6-es-1.11-2.tar.bz2]("ftp://ftp.gnu.org/gnu/aspell/dict/es/aspell6-es-1.11-2.tar.bz2")[COLOR=#CC99FF] [COLOR=Black]quizás por eso el problema.

Desde aquí hacia abajo nada funciona

[/COLOR][/COLOR][COLOR=#CC99FF]# su – zimbra [COLOR=Black]Me indica error en el comando[/COLOR]
[/COLOR][COLOR=#cc99ff]#zmcontrol stop [COLOR=Black]Me indica que zmcontrol no se reconoce como un comando[/COLOR]
[/COLOR]
 [COLOR=#CC99FF]#zmcontrol start [COLOR=Black]Idem anterior[/COLOR][/COLOR]

[COLOR=#CC99FF][/COLOR]

[COLOR=#CC99FF][/COLOR]
[COLOR=#cc99ff][COLOR=Black]Saludos[/COLOR]
[/COLOR]

---

### Post by guillermolisi on 2011-08-24
Estuve leyendo el instructivo que utilizaste y ahi dice explicitamente > Primero bajamos el diccionario para ello ejecutamos el comando

# wget [ftp://ftp.gnu.org/gnu/aspell/dict/es/aspell6-es-1.9a-1.tar.bz2](ftp://ftp.gnu.org/gnu/aspell/dict/es/aspell6-es-1.9a-1.tar.bz2)

Descomprimimos el archivo dentro de /opt/zimbra

# bzip2 aspell6-es-1.9a-1.tar.bz2

zimbra:/opt/zimbra# tar -xvf aspell6-es-1.9a-1.tarwget obtiene el tarball y la linea siguiente lo descomprime pero ANTES tenes que haber cambiado tu directorio corriente a /opt/zimbra.
Esto NO es instalar aspell sino lograr una copia dentro del directorio de Zimbra.

Luego volves a cambiar de directorio, definis la variable PATH y configuras > Entramos al directorio /opt/zimbra/aspell-0.60.6 y colocamos las variables al PATH
zimbra:/opt/zimbra/aspell-0.60.6# PATH=/opt/zimbra/aspell-0.60.6/bin:$PATH

zimbra:/opt/zimbra# cd aspell6-es-1.9a-1

zimbra:/opt/zimbra/aspell6-es-1.9a-1# ./configure Luego procedes a ejecutar "make" y "make install" SIN haber cambiado de directorio y esta operacion es la que te genera el archivo que despues tenes que editar.

No lo probe porque no uso Zimbra, pero no le veo nada como para sospechar que no funcione.

---

### Post by asterix77 on 2011-08-24
Eso fue lo que hice guillermo, el archivo comprimido lo coloqué en la ruta /opt/zimbra/, luego lo descomprimí; abrí un consola con privilegios de root; me voví a la ruta indicada, y desde aquí realicé los pasos sugeridos (./configure-make-make install, etc).

El problema es que no se genera ningún archivo aspell.php que editar, para continuar con los pasos siguientes.

¿Podría ser que en el ejemplo indicado se usa otra versión que la que descargué?

PD: La versión indicada en el link ya no está disponible.

Saludos

---

### Post by asterix77 on 2011-08-25
Después de varios intentos, y de buscar por todos lados..... al fin lo logré. Mi problema si era la versión de zimbra usado, y el diccionario anteriormente descargado.

Lo único es que tuve que hacerlo con un diccionario español de españa.

1) Descargué el diccionario (solo disponible es-ES) de la siguiente dirección: [http://files2.zimbra.com/downloads/zdesktop/dictionaries/es-ES.zip](http://files2.zimbra.com/downloads/zdesktop/dictionaries/es-ES.zip) 

2) Ir al directorio de descarga y descomprimirlo

3) Abrí una terminal e ingresé a la carpeta comprimida para mover los 2 archivos presentes a la ruta de instalación de zimbra que por defecto es /opt/zimbra/

$sudo cp /opt/zimbra/zdesktop/linux/prism/xulrunner/dictionaries  que es donde se ubican los diccionarios de zimbra.

4) Se debe editar el archivo user.js, ubicado en /home/usuario/zdesktop/profile/

5) Buscar la siguiente línea:

user_pref("spellchecker.dictionary", "us-US");

y cambiar por el diccionario deseado que en este caso sería:

user_pref("spellchecker.dictionary", "es-ES");

6) Se reinicia zimbra, y ya tenemos nuestro diccionario operativo.


Obtuve la información del siguiente link, que está en inglés

[http://wiki.zimbra.com/wiki/Zimbra_Desktop_7.1_FAQ](http://wiki.zimbra.com/wiki/Zimbra_Desktop_7.1_FAQ)

Solved now y saludos

---

