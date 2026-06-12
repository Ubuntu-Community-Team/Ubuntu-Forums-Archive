---
title: "contraseña de root?"
date: 2010-09-29
forum: Software
---

### Post by asterix77 on 2010-09-29
Sucede que quiero crear una red PAN bluetooth, entonces hago click sobre el ícono de bluetooth en mi panel, me voy a "servicios locales", luego a "red" hago click en los lugares correspondientes, y oh sorpresa, ME PIDE AUTENTICACIÓN DE ROOT, luego introduzco mi contraseña habitual de sudo y no me autentifica.

Esto también me ha sucedido en otras oportunidades, gestionando no recuerdo que, con los grupos y usuarios.

Al instalar ubuntu, no recuerdo que me hayan preguntado una contraseña para el usuario root, pero si para mi usuario y con ella acceder a acciones con privilegios de root.

¿A alguien de ustedes le ha pasado algo similar? ¿vale la pena crear un usuario root y darle una contraseña?¿o ya está el usuario root en ubuntu?. Creo que ya está porque existe su carpeta de root ¿pero tiene contraseña por defecto o hay que crearla?

Saludos

---

### Post by RafaelG on 2010-09-29
Asterix77,

Puede que este solicitando encryption key que no necesariamente tiene que ser el mismo del password root.

Saludos!

---

### Post by themasterdark on 2010-09-29
Claro puede que sea lo que menciona RafaelG, el sistema a veces te solicita la encryption key, que es la clave para acceder al anillo de claves guardadas "valga la redundancia", bueno esta la primera vez que ingresas a tu sistema te pide la creación de ella (almenos eso recuerdo)

Si no recuerdas cual es y deseas crearla nuevamente es fácil:

1.- en un terminal accede a /home/tuUsuario/.gnome2/keyrings

2.- borra todos los archivos que esten en ese directorio, lo mas fácil

sudo rm *

Listo, Saludos =)

---

### Post by asterix77 on 2010-09-29
Bueno, realicé lo sugerido por themasterdark y he borrado los archivos, pero sigo igual. Ingreso mi clave de usuario privilegiado y falla la autenticación. Les dejo una captura de lo que me aparece.


[http://img269.imageshack.us/img269/4222/autenticacin.png](http://img269.imageshack.us/img269/4222/autenticacin.png)

Saludos

---

