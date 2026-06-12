---
title: "configuracion vsftpd"
date: 2009-11-10
forum: Software
---

### Post by capcabgue on 2009-11-10
Hola:

Bueno les cuento, que se me hecho a perder el DD externo que tenía, por lo cual pensé en respaldar toda la información de mi PC en un notebook viejo que me conseguí.
Monté el servidor vsftpd en el notebook y el cliente ftp fue Filezilla.
la configuración que puse en vsftpd.conf es la siguiente:

# Habilitar el acceso a usuarios anónimos. Para mayor seguridad poner NO.
anonymous_enable=NO
# Permitir el acceso de usuarios locales a sus respectivas carpetas privadas:
local_enable=YES
# Permitir el modo escritura:
write_enable=YES
# Mascara del directorio:
local_umask=022
# Mensaje de bienvenida:
ftpd_banner=Bienvenidos al Servidor FTP de este sitio.
# Enjaula a los usuarios dentro de su propio directorio personal. Mejora la seguridad.
chroot_local_user=NO

Ahora mi problema son 2 (principalmente):
solo me deja entrar como anonymous (ahora que lo pienso no he configurado el user) y anonimo esta deshabilitado
y el único directorio que puedo transmitir por ftp es / (el cual esta vacío). Lo que yo quiero enviar es el home (para hacer un respaldo de toda la información que tengo).
Alguien me puede decir como hago para enviar por ftp todo el home.

Gracias

---

### Post by moreback on 2009-11-11
Me parece que el vsftpd maneja un archivo separado de usuarios, vstpd_users creo, ya que los usuarios de ftp no son los mismos del sistema, pero creo que puedes hacer que entren a su /home por lo menos.

---

### Post by _ZeTa on 2009-11-11
y xq no te conectas via sftp??? tendrías acceso a todo el hdd de tu computador... y usa las contraseñas de passwd para conectarse...

saludos!

---

### Post by CdK1 on 2009-11-11
Ese archivo de configuracion donde esta guardado?

---

