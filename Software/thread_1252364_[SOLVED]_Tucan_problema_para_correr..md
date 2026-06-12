---
title: "[SOLVED] Tucan problema para correr."
date: 2009-08-28
forum: Software
---

### Post by bloodytanga on 2009-08-28
Hola. Yo todavía estoy aprendiendo a usar Ubuntu y hoy me pasó algo raro.
Me bajé el Tucan (gestor de descargas para distintos servidores) y logré compilarlo, cosa que me cuesta mucho porque no entendía bien cómo hacerlo. Pero lo compilé desde la terminal estando como root user escribiendo "sudo -s" y ahora cada vez que quiero arrancar el programa tengo que entrar a la terminal, poner "sudo -s" y luego escribir "tucan", pero si entro a aplicaciones>Internet>Tucan no me arranca.

Alguna solución?

---

### Post by pablo.s on 2009-08-28
> **bloodytanga said:**
> Alguna solución?

[Acá está]("http://www.getdeb.net/release.php?id=4587") el paquete de Tucán
para que lo instales.
Medio raro lo que decís sobre
la compilación porque es un
programa PyGTK, que no se
"compila", sino que se "interpreta".

---

### Post by bloodytanga on 2009-08-28
Gracias :D

Lo pruebo y aviso.

---

### Post by bloodytanga on 2009-08-28
Me está pasando lo mismo. A la hora de ejecutar el programa si no entro a la terminal y escribo "sudo -s" y luego "tucan" no me arranca :(. Además me bajé algo y me quedó en una carpeta en el escritorio a la que no puedo acceder porque tiene un candadito y no sé cómo hacerle.

Help?

---

### Post by pablo.s on 2009-08-28
Claro que te quedó
con un candado, no tenés
permisos porque lo bajó
root. Si instalaste el .deb
que te indiqué tendría que
dejarte ejecutar el programa
como usuario.

Para cambiarle los permisos
a la carpeta tenés dos opciones:
una es con el comando chown
y la otra es invocando Nautilus
como sudo , dandole clic derecho
y cambiandole los permisos a tu
usuario.

---

### Post by bloodytanga on 2009-08-28
Descargué e instalé el .deb pero me pasa exactamente lo mismo. (Previamente desinstalé el tucan que había instalado de un archivo tar.gz

---

### Post by pablo.s on 2009-08-28
Qué error te devuelve si
ejecutás
```
tucan
```

en una terminal? Postealo.

---

### Post by bloodytanga on 2009-08-28
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/share/tucan/tucan.py", line 78, in exception_hook
    self.logger.critical("File %s line %i - %s: %s" % (file_name, line_no, exception, value))
AttributeError: Tucan instance has no attribute 'logger'

Original exception was:
Traceback (most recent call last):
  File "/usr/share/tucan/tucan.py", line 89, in <module>
    t = Tucan()
  File "/usr/share/tucan/tucan.py", line 57, in __init__
    os.remove("%s.old" % cons.LOG_FILE)
OSError: [Errno 13] Permiso denegado: '/home/tanga/.tucan/tucan.log.old'

---

### Post by pablo.s on 2009-08-28
Probá lo siguiente:
Entrá a tu carpeta de usuario
(al parecer es tanga) y presioná
CTRL + H para ver las carpetas
y archivos ocultos.
Luego encontrá la carpeta .tucan
y borrala. Probá si funciona el
programa.

---

### Post by bloodytanga on 2009-08-28
No puedo porque tiene el candadito.
Ahora voy a ver si la puedo borrar con el comando de Terminal rm -R

---

### Post by bloodytanga on 2009-08-28
Muchas gracias :D.

Entré a la terminal, escribí "sudo -s" y luego "rm -R .tucan". Se borró esa carpeta .tucan de mi carpeta personal y cuando arranqué el programa anduvo perfecto.

Muchas gracias :D.

---

