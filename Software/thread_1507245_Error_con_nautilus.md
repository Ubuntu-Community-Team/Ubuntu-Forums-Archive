---
title: "Error con nautilus"
date: 2010-06-11
forum: Software
---

### Post by leonardomdq on 2010-06-11
Hola gente, ayer instale Ubuntu 10.04 Lucid Lynx y me tiro un error que debe ser de permisos pero no entiendo como resolverlo :confused:
Esto sucede cuando quiero entrar algun directorio con el comando **sudo nautilus**.
Como podre de resolverlo?


Dejo una captura.

[U][[IMG]http://img62.imageshack.us/img62/2378/pantallazott.png[/IMG]]("http://img263.imageshack.us/img263/862/pantallazori.png")

[/U]

---

### Post by leonardomdq on 2010-06-11
Ya lo solucione, no se el motivo pero durante la instalación de Lucid no me agrego mi usuario a la lista de sudoers, revise el archivo /etc/sudoers y /etc/group y efectivamente en este ultimo no estaba mi usuario en la lista de root.

---

