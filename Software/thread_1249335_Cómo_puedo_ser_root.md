---
title: "Cómo puedo ser root?"
date: 2009-08-25
forum: Software
---

### Post by rafaelca on 2009-08-25
Hola a todos,

Tengo Ubuntu 9.04 Jaunty y bueno no me deja ser root.

Es decir,mi "Usuario" se llama -->Rafa<--

Y tiene permisos de "no root".Tiene permisos que no son limitados pero algunos si como la aceleración 3D.


Si me pueden ayudar,gracias!:P

---

### Post by harryscode on 2009-08-25
sudo nautilus en la Terminal

---

### Post by gmunioz on 2009-08-25
Hola raf....:

Para realizar tareas con permisos temporarios

de administrador, ejecutas en consola los

comandos, anteponiendo **sudo**, y luego de poner

tu contraseña de usuario, se ejecutará como si

lo usara el administrador, tal como te han 

informado respecto de nautilus.

O, también en consola ejecutas **sudo su**

introduces tu contraseña de usuario y a partir

de ese momento todos los comandos que ejecutes,

se ejecutaran como si los usara el administrador

El usuario root (administrador) en Ubuntu por

razones de seguridad se encuentra deshabilitado.

Si tienes alguna aplicación, que si o si debes

ejecutar como administrador (synaptic por ejemplo)

editando los menus y anteponiendo **gksu **al comando

previo a iniciar te solicitara tu contraseña de usuario

y se iniciará como si lo estuviera ejecutando root.

---

### Post by EnriqueK on 2009-08-25
```
sudo -i
```

---

