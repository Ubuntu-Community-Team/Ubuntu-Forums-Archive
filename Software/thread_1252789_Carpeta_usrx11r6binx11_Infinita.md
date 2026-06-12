---
title: "Carpeta usr\x11r6\bin\x11 Infinita"
date: 2009-08-29
forum: Software
---

### Post by akiestudio on 2009-08-29
Hola buenas a todos ,soy nuevo en linux y ubuntu y tengo varios problemas.
 
1 ) tengo esa carpeta que parece infinita , dentro de la x11 hay otra x11 y asi sucesivamente , hasta pesar 18gb , es eso norma? , cual es el problema como lo soluciono.
 
2) Mi conexion wifi, estando conectado y navegando , pasados 5 minutos , las paginas nos carga aunque estoy conectado y tengo que volver a reconectarme a la red. como puedo solucionar este problema , muchas gracias.
 
saludos a todos y espero aprender mucho de ubuntu por aqui

---

### Post by z37a on 2009-08-29
> **akiestudio said:**
> Hola buenas a todos ,soy nuevo en linux y ubuntu y tengo varios problemas.
 
1 ) tengo esa carpeta que parece infinita , dentro de la x11 hay otra x11 y asi sucesivamente , hasta pesar 18gb , es eso norma? , cual es el problema como lo soluciono.
 
2) Mi conexion wifi, estando conectado y navegando , pasados 5 minutos , las paginas nos carga aunque estoy conectado y tengo que volver a reconectarme a la red. como puedo solucionar este problema , muchas gracias.
 
saludos a todos y espero aprender mucho de ubuntu por aqui

Con el punto 2 me temo que no puedo ayudar demasiado, pero con el 1 si.

Lo que esta sucendiendo es que la carpeta X11 dentro del /usr/X11R6/bin es simplemente un link simbolico al ./, que quiere decir esto, que cada vez que entres a esa carpeta estaras entrando a la misma carpeta donde estabas, es algo confuso, pero en realidad no hay nada ahi, simplemente un link, entonces cada vez que entres a /usr/X11R6/bin/x11 estaras entrando a /usr/X11R6/bin

En pocas palabras es un bucle de un acceso directo. Te recomiendo no borrarlo pro que por cierta razon esta creado asi(se ve que algunas aplicaciones en vez de ir a /usr/X11R6/bin a buscar archivos van al /usr/X11R6/bin/x11 y lo solucionaron de esta manera).

PD: Te agrego, cualquier duda de este estilo, para ver bien a donde van los links y demas te recomiendo usar la consola(aka terminal) y usar el comando ls -l que te permitira ver si hay agun link simbolico y a donde apunta(son de color azul pro lo general los links). Luego si queres saber que tamaño tiene una carpeta simplemente utiliza el comando "du -sh /ruta".

---

### Post by akiestudio on 2009-08-29
Muchas gracias por tu aclaracion , si hay un enlace, aunque dice de tamaño es 0 con du -sh, ya se un comando mas jejeje
Alguien puede ayudarme con lo de internte.

---

### Post by guillermolisi on 2009-08-29
> **akiestudio said:**
> Muchas gracias por tu aclaracion , si hay un enlace, aunque dice de tamaño es 0 con du -sh, ya se un comando mas jejeje
Alguien puede ayudarme con lo de internte.
Por ese tema de red, abri un thread/hilo especifico sobre el problema en la seccion hardware (despues vemos si termina ahi o no).

Si el tema sobre X11 esta solucionado, damos por resuelto y cerrado este thread.

---

