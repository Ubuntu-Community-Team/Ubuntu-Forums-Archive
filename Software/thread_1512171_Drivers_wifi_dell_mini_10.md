---
title: "Drivers wifi dell mini 10"
date: 2010-06-17
forum: Software
---

### Post by FB91 on 2010-06-17
Tengo una [dell mini]("http://www.dell.com/us/en/home/notebooks/laptop-inspiron-10/pd.aspx?refid=laptop-inspiron-10&s=dhs&cs=19&dgc=IR&cid=39411&lid=1204298") y mi problema es que no puedo hacer funcionar el wifi. Todos los demás componentes me los tomó perfecto, a excepción de la placa de red.

Leí en algún lado que en el cd de instalación de ubuntu estaban los drivers que necesito, pero al ser una netbook no posee unidad de CD, por lo que mi pregunta es, como puedo hacer para instalar paquetes del CD de instalación pero que se encuentran dentro de un pendrive?

Muchas gracias

---

### Post by guillermolisi on 2010-06-17
Si estan en el CD estan en los repositorios, asi que lo que tal vez te convenga mas es conectarla a Internet con un cable de red.

---

### Post by granjero on 2010-06-17
como te dice guillermo fijate de conectarla con un cable a internet y anda a Sistema>Administración>Controladores de Hardware.

y fijate si aparecen drivers privativos para tu placa

si no fijate cual es la placa de red con

```
lshw
```

y una vez que sepas cual es fabricante podes ver como hacerla andar.


salud!

---

### Post by guillermon on 2010-06-18
Hola,yo quisiera acotar una sugerencia... He estado leyendo y probando el sistema de ubuntu moblin remix 9.04, con el que sacó dell las mini que se venden actualmente. Lo probé en una olivetti, y todo andaba perfecto! Apostaría que en tu dell seguro funciona. Y además está muy cómodo y bonito...
Lo busqué de nuevo; no es exactamente la misma página, pero aparentemente es oficial de dell. Va el link ```
http://en.community.dell.com/support-forums/software-os/w/linux/ubuntu-9-04-moblin-remix-developer-edition.aspx
```
Espero ayudarte. Saludos
Guillermo

---

### Post by guillermolisi on 2010-06-18
> **granjero said:**
> como te dice guillermo fijate de conectarla con un cable a internet y anda a Sistema>Administración>Controladores de Hardware.

y fijate si aparecen drivers privativos para tu placa

si no fijate cual es la placa de red con

```
lshw
```y una vez que sepas cual es fabricante podes ver como hacerla andar.


salud!
Agregale un ```
lsusb
```porque podria ser USB la placa WiFi. Solo para confirmar lo que lshw de como resultado.

---

### Post by FB91 on 2010-06-18
Gracias por las respuestas, solucioné todo conectándola con el cable de red y luego me bajé los controladores y ahora todo funciona 10 puntos :D
muy recomendable esta maquinita

SOLVED

---

