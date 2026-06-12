---
title: "Como actualizar CodeBlocks en ubuntu 12 ?"
date: 2015-03-17
forum: Software
---

### Post by osqui-botteri95 on 2015-03-17
Hola gente!
Tengo una consulta, instale codeblocks desde el centro de software y me instalo la version 10 de codeblocks, y la version actual es la 13.12 si no me equivoco. Como puedo actualizar codeblocks en mi PC ?
Agregue esta ppa: sudo add-apt-repository ppa:gwibber-daily/ppa y despues hice sudo apt-get update y hasta ahi llegue.. nose que mas hacer. Alguien me puede ayudar ?

Tengo que usar si o si este IDE porque es el que se usa en la facu por ahora. Desde ya gracias.

---

### Post by euzkoarima on 2015-03-27
Abrí la consola y poné los siguientes comandos

```
sudo add-apt-repository ppa:pasgui/ppa
sudo apt-get update
```

Si ya habías instalado codeblocks antes podes hacer
```
sudo apt-get upgrade
```

Sino
```
sudo apt-get install codeblokcs codeblokcs-contrib
```

Saludos
Eduardo

---

