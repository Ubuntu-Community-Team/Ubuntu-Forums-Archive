---
title: "Problema al instalar Wine"
date: 2009-08-08
forum: Software
---

### Post by josecardenasvejar on 2009-08-08
Buenas!

he visto que algunos amigos usan un programa para compatibilidad de software de windows en ubuntu. El problema es que trato de instalarlo por medio de la consola con el comando sudo apt-get install wine, pero cuando termina de hacerlo, no lo encuentro por ningún lado, y tampoco aparece en el menú de aplicaciones.

Agradezco mucho su ayuda

Saludos

:lol:

---

### Post by dlmarti on 2009-08-08
wine is at the bottom of the applications menu (it creates its own top level menu item).

wine es en la parte inferior del menú de aplicaciones (que crea su propio elemento de menú de nivel superior).

---

### Post by josecardenasvejar on 2009-08-10
Muchas gracias por tu comentario                              dlmarti

Eso tenía entendido que sucedía, pero no aparece en ningún lado. 

Ahora, si lo instalo por medio de la consola, y hago click con el botón derecho del mouse sobre un archivo de windows, aparece en primera instancia "ejecutar con wine". Hago click y no sucede nada.

De verdad es algo desagradable esta situación, ya que creía saber algo de ubuntu, y primera vez que me pasa algo y no lo puedo solucionar!  :)

Saludos

---

### Post by dlmarti on 2009-08-10
You can add wine under system->main menu
but first we must fix your problems running wine.

If you run wine from the command line (in a terminal), we should be able to get diagnostics about your problem.

Open a terminal window
change your current directory to a windows application
type "wine application.exe" and see what happens.


Puede añadir el wine, en el del sistema-> menú principal 
 pero primero tenemos que arreglar sus problemas ejecutando vino. 

Si ejecuta el wine de la línea de comandos (en un terminal), debemos ser capaces de obtener diagnósticos acerca de su problema. 

 Abra una ventana de terminal 
 cambiar el directorio actual para una aplicación de Windows 
 tipo "wine application.exe" y ver qué pasa.

---

### Post by AlvaroV on 2009-08-10
Podrías señalar que software te interesa correr con wine, para ver si te podemos ayudar por ese lado.

---

