---
title: "Armar red entre 6 pcs con Ubuntu Jaunty"
date: 2009-07-05
forum: Software
---

### Post by Einfachlacm on 2009-07-05
Hola,

estoy tratando de armar la red lan por cable entre 6 pcs con Ubuntu Jaunty a traves de una switch. Todas tienen internet porque el modem esta ruteado y comparten dos impresoras.

Lo que no logro hacer es que compartan los archivos, no se como configurarlo. Le puse compartir a la carpeta home y cuando la volvi a arrancar me aparecio un mensaje diciendo:

"Se esta ignorando el archivo $HOME/.dmrc del usuario. Esto impiden que se guarden la sesion predeterminada y el idioma. El archivo deberia pertenecer al usuario y tener los permisos 664. El directorio personal del usuario debe pertenecer al usuario y no ser escribible para otros usuarios".

En definitiva, no se como compartir archivos en red entre ubuntus... alguien me da una mano?

Gracias.

---

### Post by juancarlospaco on 2009-07-05
**chmod --verbose 664 $HOME/.dmrc**

:p

---

### Post by staar on 2009-07-05
si todas las máquinas tienen linux, podés usar NFS para compartir los archivos (ojo que una ocasional máquina con windos no va a tener acceso nativo, necesitará algún programa aparte) acá [http://ubuntu-ar.org/node/208]("http://ubuntu-ar.org/node/208") hay un tutorial para configurarlo...

saludos

---

### Post by juancarlospaco on 2009-07-05
**nfs +1**

---

### Post by alfplayer on 2009-07-07
Seguramente lo que pasó es que al intentar compartir la carpeta home haciendo click con el botón derecho  en la carpeta home y haciendo click en *Opciones de compartición* se le cambiaron los permisos. Si hubieras intentado compartir una carpeta dentro de home no habría pasado nada malo. Esta es la forma más fácil de compartir archivos en Ubuntu y usa Samba con el protocolo SMB, que es el protocolo que usa windows (asi se puede acceder a una carpeta compartida desde windows).

---

### Post by biale on 2009-07-07
No debido a Samba, pero yo también tuve problemas con el archivo $HOME/.dmrc Los permisos de ese archivo estaban bien, pero el mensaje de error no indicaba la fuente del problema. Por las dudas aclaro que el problema estaba situado en otros directorios y archivos ocultos con los permisos errados.

Pegale un vistazo a los archivos /etc/samba/smbusers (equivalencias de cuentas) y smb.conf (los shares que hayas compartido y etc).

Si todo parece estar bien, puede haber algún problema en el browser. Con nautilus apunta directo a   smb://la_dirección_de_ip/  como para ver que muestra. 

Saludos.

---

### Post by alfplayer on 2009-07-07
Reseteando los permisos de home debería volver todo a la normalidad.

---

