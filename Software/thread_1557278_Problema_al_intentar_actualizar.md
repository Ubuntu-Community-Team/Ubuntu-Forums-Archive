---
title: "Problema al intentar actualizar"
date: 2010-08-20
forum: Software
---

### Post by nanogoleta on 2010-08-20
Buenas!
estoy teniendo un problema con el gestor de actualizaciones.
La verdad que no tengo ni idea que hacer...
El mensaje que me sale es el siguiente:

*W: Duplicate sources.list entry [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) karmic-getdeb/apps Packages (/var/lib/apt/lists/archive.getdeb.net_ubuntu_dists_karmic-getdeb_apps_binary-i386_Packages)*

Alguna idea de que hacer?

Gracias!

---

### Post by leonardomdq on 2010-08-20
Tenes duplicada una entrada en tu sources.list
Pega aca el contenido del archivo */etc/apt/sources.list* 

Abris una terminal y tipea:
```
 sudo gedit /etc/apt/sources.list
```

Asi de esta manera vemos cual es la que tenes duplicada.

---

### Post by guillermolisi on 2010-08-20
agrega, por las dudas, tambien la salida de este otro comando en consola/terminal
```
ls -al /etc/apt/sources.list.d
```

---

