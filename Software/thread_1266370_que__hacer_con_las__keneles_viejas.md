---
title: "que  hacer con las  keneles viejas"
date: 2009-09-14
forum: Software
---

### Post by rishark on 2009-09-14
hola a todos   como  hago  para eliminar  las  entradas de las  keneles  viejas  en el grub  y  como  configurarlo  para  un mejor  rendimiento   ....:confused:

---

### Post by anarko on 2009-09-14
Podes usar el sinaptic, ubicado en Sistema -> Administracion -> Gestor de paquetes sinaptic. 

Ahi buscas los paquetes que se llaman linux-image-2.6, la busqueda te tira todos los kernels que tenes instalados, y podes eliminarlos desde ahi.

NOTA: 
Si no estas seguro de lo que haces podes hacer macana, siempre tenes que dejar al menos 1 kernel que sepas que anda 100% en tu pc.Yo dejaria 2 por las dudas. Si es cuestion de estetica, son solo 10 seg que tarda el grub en autoseleccionar un kernel.
Si es por cuestion de espacio en disco, es despreciable, 20 a 50Mb puede ocupar un kernel y no esta demas guradarlos por si las dudas.

---

### Post by mama21mama on 2009-09-14
Hola yo los remuevo a los kernel viejos por terminal.

> dpkg --get-selections | grep linux-image
con esto buscara todos los kernels

> sudo apt-get remove --purge kernel1 kernel2
con esto remueve kernel1 kernel2


> dpkg --get-selections | grep linux-headers
buscar las headers 

> sudo apt-get remove --purge linux-headers1 linux-headers2
borra las headers de los kernel que anteriormente quitaste

PD: siempre por las dudas deja 2 kernels; espero te sirva...saludos

---

### Post by staar on 2009-09-14
si no, podés usar el startup-manager (buscalo en Synaptic) que te permite elegir cuantos kernels dejar en el grub (los otros los oculta, pero no los desinstala)

saludos

---

