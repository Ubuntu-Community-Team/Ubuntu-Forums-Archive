---
title: "ayuda pass root"
date: 2008-08-06
forum: Software
---

### Post by guillelb94 on 2008-08-06
acabo de instalar ubuntu 7.10 y queria hacer tareas administrativas de sistema, actalisasiones,etc y me pide la pass de root pero en la instalasion nunca me pidio que pusiera la pass de root
grasias
sdalu2

---

### Post by sergiom99 on 2008-08-06
pone la del usuario que definiste al instalar (la misma que usas para entrar)

---

### Post by leo_rockway on 2008-08-06
Ubuntu no trae un usuario root, en lugar de eso se usa sudo (super user do) que permite a un usuario común (y con permisos de sudoer) realizar tareas que de otra manera sólo root podría hacer. Para usar sudo necesitas poner tu propia contraseña.

EDIT: faktorqm me hizo notar que quizás lo que escribí se puede malinterpretar. No es que root no exista en Ubuntu, sino que root no viene configurado por defecto y por eso en general nunca se usa (sino que se usa sudo).

---

### Post by el_mesias on 2008-08-12
hola!

no puedo montar mi sda1 (disco C: en que tengo windows), me dice que no tengo derechos de usuario root o algo asi.

no hay forma de convertirme en root??
o en su defecto: como dejo montado el disco sda1 siendo usuario no root?

gracias

---

### Post by Hei Ku on 2008-08-12
sudo mount .....

o cambiando el fstab para que el disco lo pueda montar cualquier usuario. Postea el archivo /etc/fstab

---

