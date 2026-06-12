---
title: "Problema con internet ubuntu 10.10"
date: 2011-06-10
forum: Software
---

### Post by cologra on 2011-06-10
Hola desinstale el network manager (sin saber lo que hacia) y no tengo internet y no se como hacer pa instalarlo de nuevo o como configurar ubuntu para poder tener internet de nuevo. Tengo conexion ethernet de fibertel
Gracias

---

### Post by josecuervo86 on 2011-06-10
Tenes el cd de Instalación? Ponelo en la "compactera" y configura tus origenes de software poniendolo como repositorio. Una vez hecho esto, busca en synaptic o hace un
```
sudo apt-get install network-manager
```

Otra que podes hacer es bajarte desde algun lugar con acceso a internet el paquete para tu arquitectura desde aca: [http://packages.ubuntu.com/es/maverick/network-manager]("http://packages.ubuntu.com/es/maverick/network-manager") y despues lo instalas como cualquier paquete que te bajas. Que se entienda que lo tenes que bajar en otra PC y despues con un pendrive o similar lo pasas a tu PC =).

suerte!!

---

### Post by guillermolisi on 2011-06-10
Tambien podes abrir una terminal/consola, editas el archivo /etc/network/interfaces con tu editor de texto simple preferido, supongamos nano:
```
sudo nano /etc/network/interfaces
```
y copias y pegas el siguiente contenido:
```
iface eth0 inet dhcp
auto eth0
```

Guardas/salvas el archivo, reinicias y deberias estar conectado nuevamente a Internet.
Luego te bajas de los repositorios lo que quieras, Network Manager inclusive.

---

