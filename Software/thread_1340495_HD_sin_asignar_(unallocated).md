---
title: "HD sin asignar (unallocated)"
date: 2009-11-28
forum: Software
---

### Post by zeusolimpo on 2009-11-28
En la PC de escritorio donde tengo Ubuntu 9.10 y Windows XP tengo 2 HD de 250 GB: uno con los sistemas operativos (sda) y otro con archivos (sdb).
Después del último upgrade del kernel de Karmic (el jueves 26/11) recién apagué (no reinicié) la PC el viernes a la mañana. Volví a encenderla ese día a la tarde y el HD sdb no se "ve" con Nautilus. Con gparted me aparece como "unallocated" y la etiqueta "unrecognized".
Reinicié en XP y pasa lo mismo: en el administrador del sistema el disco aparece como funcionando correctamente pero no lo puede montar.
Iniciando la BIOS aparecen perfectamente detectados e instalados los 2 discos.
Destapé la PC (aproveché para limpiarla!) ajusté las conexiones de poder y los cables SATA, los intercambié entre los dos discos, los puse en otro alojamiento, etc. pero sin mejor resultado.
Corrí el MHDD que identificó los 2 discos y no me dió ninguna anomalía de funcionamiento.
Antes de FORMATEAR (puajh!), alguna idea sobre recuperación de los datos?

---

### Post by zeusolimpo on 2009-11-29
Bueno, recuperé las particiones con TestDisk, pero me encontré con la sorpresa de que tengo 2 instalaciones de Ubuntu, una de ellas sobre una partición del disco sda que se "veía", que por supuesto se achicó para dar lugar a la nueva de ubuntu, que ocupa 50GB de ext3 y 2GB el swap.
En el sdb recuperé la part. linux original de 20 GB ext3 y 2 GB swap.
Ademas, si ahora quiero arrancar linux con la última actualización de kernel se tilda. Pude arrancarlo con una anterior que es 2.6.28-16 generic y con esta corriendo. estoy haciendo urgente BU de todo lo que puedo ver antes de reiniciar o apagar la PC.
Podrá ser que la actualización al 2.6.31-15 haya armado todo este lío o es que hay virus sueltos para linux?

---

