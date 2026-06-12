---
title: "Crear usuario Shutdown para server."
date: 2009-07-20
forum: Software
---

### Post by zeroadrenaline on 2009-07-20
Chicas!!: Primero que nada feliz día.
Ahora si, el mangazo, tengo que crear un usuario, nombre shutdown, y la idea es que tenga como bash en /etc/passwd:

| shutdown:x:1002:1002:shutdown:/sbin:/usr/bin/sudo /sbin/shutdown –h now|

Lo agregaría a /etc/sudoers como : |

shutdown ALL=/sbin/shutdown –h now

La idea es que, va a haber un script que va a hacer ssh shutdown@un_server con una clave rsa creada, y la idea es que cuando loguee, directamente tira el shutdown.

Lo hice, pero mi problema esta en que declarando el usuario de esa manera, me da el siguiente error:

No puedo ejecutar /usr/bin/sudo /sbin/shutdown –h now: No existe el fichero ó directorio

Para evitar mails innecesarios adjunto los ls:

root@mpaz:/usr/bin# ls -l | grep sudo
lrwxrwxrwx 1 root root 4 2009-07-02 12:46 gksudo -> gksu
-rwxr-xr-x 1 root root 79836 2009-04-08 18:40 kdesudo
-rwsr-xr-x 2 root root 115136 2009-02-17 01:22 sudo
-rwsr-xr-x 2 root root 115136 2009-02-17 01:22 sudoedit

root@mpaz:/sbin# ls -l | grep shutdown
-rwxr-xr-x 1 root root 51068 2008-09-29 20:52 shutdown

Si alguno tiene idea de como lo puedo solucionar, se los agradeceré.

---

