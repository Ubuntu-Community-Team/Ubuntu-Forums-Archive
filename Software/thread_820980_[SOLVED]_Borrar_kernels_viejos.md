---
title: "[SOLVED] Borrar kernels viejos"
date: 2008-06-06
forum: Software
---

### Post by atatiducken on 2008-06-06
Buenas, los q tienen hardy se habran dado cuenta q bastante seguido estan sacando kernels nuevos, el grub se esta volviendo un poco molesto ya, asi q decidi borrar los anteriores kernels, mientras escribo esto estoy instalando la version **2.6.24-19**, pero tengo desde la **2.6.24-16** hasta esta nueva, mi duda es si esto es correcto para desintalar los kernels viejos, asi no hago macana :), hago copy & paste:

  ```
 1. Hacer un listado de las versiones de kernel que tenemos.

      dpkg --get-selections | grep linux-image

   2. Luego eliminar los kernel antiguos con el comando purge note que donde esta escrito 
kernel debe usted indicar el nombre del kernel que desea quitar.

      sudo aptitude purge kernel

   3. En ocasiones, aparecerá la pregunta diciendo que no se encuentra actualizado 
y si deseamos hacerlo con lo que basta indicarlo que no usando el siguiente comando.

      sudo aptitude remove kernel
```

gracias y saludos

---

### Post by pablo0469 on 2008-06-07
Yo los desinstalo directamente desde Synaptic, buscandolos en la seccion "Sistema Base" (ojo, Sistema Base a secas, no en Sistema Base Restricted ni en Universe). Despues purgo y limpio:

sudo aptitude purge ~c
sudo apt-get clean

Y listo. Vengo haciendo esta maniobra mas que sencilla desde hace mas de 1 año y jamas tuve 1 solo problema.

Ojala te sirva y saludos.

PD: jamas hice una copia de seguridad, hasta ahora me salio bien...

---

### Post by fgl82 on 2008-06-07
Che encontré una solución a este problema que parece bastante simple:

Entrar al Synaptic y buscar "linux-image-2", para luego desmarcar los kernels viejos.

Mi pregunta es, si hago esto, ¿Synaptic se encarga de todo? ¿O tengo que tirar igual esos comandos de consola?

---

### Post by atatiducken on 2008-06-07
gracias pablo0469, pero termine haciendo la solucion q encontre y tb funciono.
fgl82 marca los kernles q queres borrar y el synaptic hace todo
saludos

---

### Post by lushnok on 2008-07-02
busqué "linux-image-2" en synaptic, pero me aparece para borrar más de lo que pido (y de lo que aquí se sugiere).
Por otro lado, ¿lo marco para borrar o para borrar completamente? ¿cuál es la diferencia?

---

### Post by hernan blau on 2008-07-02
Yo hago así desde consola: 
sudo apt-get remove --purge linux-image-2.6.17-11-generic y reemplazás el número indicado por el del kernel que quieras borrar. Suerte. HB

---

### Post by _kAz_ on 2008-07-16
Gente un par de dudas... Eliminé los kernels 16, 17 y 18

Sin embargo con los últimos dos (el primero no me fijé) me salió esto al final:
```
rmdir: No se pudo eliminar «/lib/modules/2.6.24-18-generic»: El directorio no está vacío
```
De todas formas estos dos son los que quedaron:
```
linux-image-2.6.24-19-generic			install
linux-image-generic				install
```
Son los que tengo que dejar o puedo eliminar también el "linux-image-generic"?

---

### Post by Hei Ku on 2008-07-16
si queres seguir booteando, me parece que es mejor que dejes el generic. :D

---

### Post by pablo0469 on 2008-07-16
KAZ, eso es lo que tengo instalado yo desde que vengo borrando los sucesivos kernels que se fueron actualizando, y la maquina anda lo mas bien. No puedo ahondar mas en este tema, sé lo minimo indispensable.

Saludos.

---

