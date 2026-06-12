---
title: "Como montar particiones automaticamente?"
date: 2010-08-26
forum: Software
---

### Post by diegol3d on 2010-08-26
Hola. poseo el ubuntu 10.04 y a veces que entro al ubuntu no me deja montar una partición del disco, en la que tengo sobre todo musica. me dice: error, no se pudo montar el volumen. si reinicio me deja. pero para no pasar por eso me gustaría que me dijeran como se hace para montar una unidad automáticamente, asi cada vez que inicio ubuntu (ya en windows ni quiero entrar) tendria el volumen ya montado. aclaro. poseo doble boot con 2 particiones en windows (C y D) y la ultima es la que me interesa. Gracias de antemano.

---

### Post by EnriqueK on 2010-08-26
Instala Disk-Manager, sacado del repositorio de Debian testing
[http://ftp.de.debian.org/debian/pool/main/d/disk-manager/disk-manager_1.0.1-5_all.deb](http://ftp.de.debian.org/debian/pool/main/d/disk-manager/disk-manager_1.0.1-5_all.deb)
Una vez instalado, reinicia sesión y lo vas a encontrar en Sistema-->Administracion-->Administrador de disco.

---

### Post by guillermolisi on 2010-08-26
> **diegol3d said:**
> ... me dice: error, no se pudo montar el volumen. **si reinicio me deja**. pero para no pasar por eso me gustaría que me dijeran como se hace para montar una unidad automáticamente, asi cada vez que inicio ubuntu (ya en windows ni quiero entrar) tendria el volumen ya montado. ......
Disculpa la pregunta pero si reinicias la maquina, esa particion queda montada automaticamente o solo deja que la montes a mano ?
Si queda montada automaticamente estaria resuelto tu objetivo.

El archivo que registra que particiones montar al inicio es /etc/fstab.
Normalmente solo el usuario root, o un usuario comun con privilegios arrogados con sudo, pueden montar particiones a mano.

Las particiones NTFS conviene que esten integras (revisadas con chkdsk y reorganizadas/defragmentadas) para evitar problemas en el montaje y posterior uso.

Complementariamente a lo que se exponga a lo largo de este hilo, si pones en una terminal/consola ```
man mount
```accedes al manual del comando (por si este dato no estaba en tu conocimiento).

---

### Post by diegol3d on 2010-08-26
Edito: Hice lo que me dijo EnriqueK y me funciono de 10. Gracias enrique. Gracias de todos modos guillermo.

---

