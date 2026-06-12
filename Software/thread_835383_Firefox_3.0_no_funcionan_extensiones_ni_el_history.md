---
title: "Firefox 3.0 no funcionan extensiones ni el history"
date: 2008-06-20
forum: Software
---

### Post by nmtservice on 2008-06-20
¡Hola Ubunteros!
Después de actualizar desde los repos, Firefox 3 me inicia con una pagina en blanco y preguntando por la licencia del plugin DownThemAll y si quiero sincronizar bookmarks con foxmarks no me ejecuta el asistente.
El history esta totalmente en blanco, y tampoco tengo las contraseñas guardadas.
Ahora, si lo ejecuto con privilegios de root (sudo firefox-3.0) todo vuelve a la normalidad.
Probé con SUID (chmod 4777 /usr/bin/firefox-3.0) pero sigue ocurriendo la falla anterior. Igual me parece un poco peligroso correr un browser con privilegios de root.
¿Alguna idea feliz sobre este asuntito?

---

### Post by Hei Ku on 2008-06-20
fijate que en tu carpeta tenes una carpeta que se llama .mozilla/firefox
copiala a otro lado, como backup, y volve a iniciar el firefox

---

### Post by madjr on 2008-06-20
> **nmtservice said:**
> ¡Hola Ubunteros!
Después de actualizar desde los repos, Firefox 3 me inicia con una pagina en blanco y preguntando por la licencia del plugin DownThemAll y si quiero sincronizar bookmarks con foxmarks no me ejecuta el asistente.
El history esta totalmente en blanco, y tampoco tengo las contraseñas guardadas.
Ahora, si lo ejecuto con privilegios de root (sudo firefox-3.0) todo vuelve a la normalidad.
Probé con SUID (chmod 4777 /usr/bin/firefox-3.0) pero sigue ocurriendo la falla anterior. Igual me parece un poco peligroso correr un browser con privilegios de root.
¿Alguna idea feliz sobre este asuntito?


asegurate que tengas espacio suficiente en el disco duro.

a mi me paso lo mismo porque me quede sin espacio.

borra lo que no necesites o muevelo a otro disco

---

