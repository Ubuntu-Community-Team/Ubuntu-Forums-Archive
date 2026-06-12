---
title: "Montar unidades de red Windows"
date: 2008-11-08
forum: Software
---

### Post by AndresB on 2008-11-08
Hola a todos: quería preguntarles como puedo hacer desde un script para montar una unidad de red compartida desde un servidor Windows 2008, estoy utilizando ubuntu 8.10. Hace mucho tiempo, utilizaba este comando:

mount //serverwin/documentos /mnt/documentos -o username=usuario%xxx

Pero no esta funcionando, en la web encontre algunos post que hablan de modificar fstab, pero antes de meter mano quería preguntarles a Uds.

Desde "lugares" --> "conectar con el servidor" funciona bien, pero quiero montar la unidad

Desde ya muchas gracias
Andres

---

### Post by ImplicitNone on 2008-11-09
Hola Andrés,

Que yo sepa cuando montas desde el menu lugares lo que estas usando es FUSE. Podés agregar una linea en el fstab para montar con FUSE, si mal no recuerdo es así:

sshfs#user@host:/ /home/usuario/remoto fuse defaults 0 0

Luego, cuando montes desde el menú lugares, se montará con las opciones que pusiste en lugar de "defaults".

Por otro lado, de ahora en más, cada vez que uses el comando mount (una vez que hayas incluido esas lineas en fstab), se montará de la forma que lo especificaste para FUSE.

Una vez que lo especificas en fstab, podés hacer un script con el comando mount.

Saludos.

---

### Post by c4d0rn4 on 2008-11-09
> **AndresB said:**
> Hola a todos: quería preguntarles como puedo hacer desde un script para montar una unidad de red compartida desde un servidor Windows 2008, estoy utilizando ubuntu 8.10. Hace mucho tiempo, utilizaba este comando:

mount //serverwin/documentos /mnt/documentos -o username=usuario%xxx



no entiendo que necesitas, si un script o el comando, pero van las dos

Yo para montar una unidad de una carpeta compartida en vista
```
sudo mount -t cifs //serverwin/documentos /mnt/carpeta -o username=USER,password=*****,iocharset=utf8,file_mode=0777
```

Como script, solo hay que escribir en gedit
```
#!/bin/bash
gksudo 'mount -t cifs //serverwin/documentos /mnt/carpeta -o username=USER,password=*****,iocharset=utf8,file_mode=0777'
```
Lo guardas como .sh, luego le das permisos de ejecutable (perdón por la falta de modo consola xD). Click derecho, propiedades, permisos abajo de todo fijate que permite que se ejecute.

Luego en un launcher pones en command que ejecute ese archivo y queda listo el pollo.

---

