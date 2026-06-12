---
title: "problemas de contraseña de usuario"
date: 2009-10-09
forum: Software
---

### Post by Esgolus on 2009-10-09
Hola amigos:

Debo decir que soy totalmente un novato en ubuntu. 
Compré una pc con Ubuntu 9.04 preinstalado el cual venía con una contraseña de usuario (la cual no conozco) y tengo problemas para instalar todos los programas que lleguen a ser compatibles con Linux y que uso comunmente.
Ya intenté con el comercio que me vendió, pero no tienen idea, como la PC anda bárbaro y el Sistema Operativo me atrae, quiero saber como obtener todos los permisos. Ya probé muchas cosas que encontré en el foro y el sistema deniega mi permiso.
Ustedes son la última salida que tengo, si pueden darme una mano bárbaro y si no, bueno veré que hacer.
Gracias.

---

### Post by quixote on 2009-10-11
My Spanish isn't too good, so maybe who knows the language better can jump in with a more complete answer.

Changing the user password is very easy if you have access to the machine. Boot into recovery mode. (Not the first option when grub comes up, but the second one, labeled "recover" or something like that.  Except, of course, yours would probably be whichever word the Spanish Ubuntu/grub uses.) 

It'll give you the option of several types of recovery mode.  Choose the last one: root prompt with network access.  It may take a while to give you a command prompt if you don't have an ethernet cable attached, but it will eventually.

The prompt will look like "root@*the-machine-name*". To change the login name:```
usermod -l *new-login old-login* 
``` That's a lowercase "L", not a number "1".  You can see what the old login was by the name in /home.

To change the password:```
passwd *login-name*
```
You'll then see:
Changing password for user *login-name*
New password: *[type your desired password]*
Retype new password; *retype it*
You could, of course, use this to change the password for old-login-name, if you didn't want to bother changing login names. 

And then shutdown the system by typing```
halt now
```

Start up again, and hopefully it'll show you your new user who logs in with your new password!

---

### Post by gmunioz on 2009-10-11
Hola esg.....:

Cuando inicia el ordenador, pulsa escape

Te aparecerá en menu del grub, elige la segunda

opción, recuperación.

En el submenu emergente, elige netroot, iniciaras

como administrador sin contraseña, en consola.

Ejecutando:

ls /home

Obtendras un listado del contenido de /home, el nombre

del directorio listado, corresponde al nombre de usuario.

Eejcutando:

passwd usuario

Podrás cambiar la contraseña, te la solicitara en dos

oportunidades y no veras nada en la consola al introducirla

No es conveniente cambiar el nombre de usuario, pues este usuario

el que teóricamente instaló el sistema, es el único autorizado

a actuar con permisos temporarios de administrador mediante la

anteposición del comando sudo a las ordenes.

---

