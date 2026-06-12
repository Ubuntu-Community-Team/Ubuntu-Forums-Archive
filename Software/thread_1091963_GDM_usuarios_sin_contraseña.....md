---
title: "GDM usuarios sin contraseña...."
date: 2009-03-09
forum: Software
---

### Post by granjero on 2009-03-09
hola amigos... mi idea es que al iniciar la pc llegue hasta el gdm y podamos tener usuarios separados los integrantes de la casa, pero es un poco cansador poner la pass cada vez...

el tio google me dijo esto, pero quería confirmar con uds que eso es lo que hay que hacer...

> Ahora el gran truco: hacer que los usuarios se puedan autenticar sin contraseña.

Se debe editar el archivo /etc/pam.d/gdm.

PAM (Pluggable Authentication Modules) es un mecanismo flexible para autenticar usuarios en Linux (para que se puedan utilizar diferentes formas de determinar que un usuario es un usuario legítimo del sistema).

$ sudo gedit /etc/pam.d/gdm

El archivo debe quedar con el siguiente contenido:

#%PAM-1.0
auth requisite pam_nologin.so
auth required pam_env.so

# La siguiente linea permite tener una lista de usuarios sin contrasena en GDM:
auth sufficient pam_listfile.so item=user sense=allow file=/etc/X11/gdm/nopassusers.txt onerr=fail

@include common-auth
@include common-account
session required pam_limits.so
@include common-session
@include common-password

La lista de usuarios que no requieren contraseña se escriben en el archivo /etc/X11/gdm/nopassusers.txt, uno por línea. Los usuarios que no están en este archivo sí deberán escribir su contraseña para poder iniciar sesión:

$ sudo gedit /etc/X11/gdm/nopassusers.txt

Ahora cierra tu sesión y presiona Control-Alt-Delete para reiniciar la ventana de entrada y leer los cambios. Listo.


fuente: [http://www.comentaomuere.com/2007/07/09/recopilacion-de-consejos-para-optimizar-ubuntu/](http://www.comentaomuere.com/2007/07/09/recopilacion-de-consejos-para-optimizar-ubuntu/)

no quise tocar sin antes estar seguro que así es como debe hacerse...

muchas gracias!


salud!

---

### Post by guillermolisi on 2009-03-10
> **granjero said:**
> hola amigos... mi idea es que al iniciar la pc llegue hasta el gdm y podamos tener usuarios separados los integrantes de la casa, pero es un poco cansador poner la pass cada vez...

el tio google me dijo esto, pero quería confirmar con uds que eso es lo que hay que hacer...




fuente: [http://www.comentaomuere.com/2007/07/09/recopilacion-de-consejos-para-optimizar-ubuntu/](http://www.comentaomuere.com/2007/07/09/recopilacion-de-consejos-para-optimizar-ubuntu/)

no quise tocar sin antes estar seguro que así es como debe hacerse...

muchas gracias!


salud!

La verdad que nunca lo probe simplemente porque no le ha molestado a ninguno de los que usan una maquina con Ubuntu poner su pass, pero parece que podria funcionar.

Al margen de si funciona o no, mi recomendacion es que hagas una copia del archivo en su estado original, con permisos y todo, para volver las cosas a su estado primario si no llega a funcionar o te trae efectos colaterales no deseados.

Donde dice Ctrl+Alt+Del no deberia decir Ctrl+Alt+Backspace ?
Se supone que deberias reiniciar el servidor X para que tome los cambios introducidos en el sistema de seguridad administrado por PAM.

---

### Post by granjero on 2009-03-12
hola ubunteros... no logre que funcione....

asi quedo el archivo gdm

```
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale

# La siguiente linea permite tener una lista de usuarios sin contrasena en GDM:
auth sufficient pam_listfile.so item=user sense=allow file=/etc/X11/gdm/nopassusers.txt onerr=fail

@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so auto_start
@include common-password
```

alguno se le ocurre como lograrlo?


muchas gracias!

---

### Post by granjero on 2009-03-12
ya lo solucioné...

había guardado en cualquier lado....


funciona perfectamente!!!!

salud!

---

