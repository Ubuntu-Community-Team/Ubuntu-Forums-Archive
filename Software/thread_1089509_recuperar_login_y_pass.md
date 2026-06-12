---
title: "recuperar login y pass"
date: 2009-03-07
forum: Software
---

### Post by franko71ar on 2009-03-07
hola amigos
Instalé por primera vez el SO en mi pc ( soy nuevo en esto), todo bien, una vez q encendió m pide login de usuario y pass q no lo recuerdo, como hago para recuperarlos.
me olvidaba tengo instalaso ubuntu 8.04 en su version server

gracias

francisco

---

### Post by sergiom99 on 2009-03-07
la clave es la que pusiste al instalarlo.  Sino la recordas, tal vez te sirva esto, nunca lo probe en Ubuntu, pero en Fedora/CentOS/RedHat anda de maravillas. (para cambiar la clave de root. La clave de los usuarios la cambias facilmente como root con passwd)
Suerte!

> 1. Hay que rebootear el Linux, y en el GRUB Loader, en la opción de 'kernel', agregar al final de la línea:        *single*

2. Al bootear el equipo no pide contraseña ni nada.

3. Editar /etc/shadow
*vi /etc/shadow*

y borrar en la entrada de tu usuario toda la contraseña encriptada entre los : : y dejar un *

4. Cambiar la clave con *passwd tuusuario*.

5. Rebotear

---

