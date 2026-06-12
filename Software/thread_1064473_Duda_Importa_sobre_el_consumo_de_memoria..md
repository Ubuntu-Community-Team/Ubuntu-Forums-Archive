---
title: "Duda Importa sobre el consumo de memoria."
date: 2009-02-08
forum: Software
---

### Post by pol666 on 2009-02-08
Dado que estoy un poco confundido con el monitor de sistema de KDE4, y top no me aclara las dudas hago un free -m para ver cuanto es en realidad el consumo de memoria real.

> 
             total       used       free     shared    buffers     cached
Mem:          1008        899        108          0         25        565
-/+ buffers/cache:        308        699
Swap:         1027          0       1027


El sistema es estable pero no creo que este consumiendo 900mb de memoria es muchisimo, o acaso tengo que sumarle lo que dice Chache? no entiendo bien esto... cual es el consumo de memoria fisica real?.

top me dice que hay 0k de memoria usada pero 580mb cacheados. busco una explicacion gracias

---

### Post by clasificado on 2009-02-09
Es una diferencia típica desde los que venimos del task manager de windows ^^

Respondiendo rápido: Lo que vos buscas es el Used MENOS el Caché. Quedaría 899 - 565 = 334mb usados por las aplicaciones.

Y es que el kernel de linus aprovecha la memoria no usada para usarla para sus propias cosas (como caché y buffers) prometiendo que en cuanto las aplicaciones lo necesiten, él la libera como si nunca hubiera existido.

Windows hace lo mismo, pero no pone el buffers + caché dentro del gráfico principal, sino que te lo deja en el detallito de abajo.

ksysmonitor te lo muestra de una manera mas gráfica

clasificado

---

### Post by pol666 on 2009-02-09
Me lo supuse desde un principio diria el chapulin :P

por que instale gnome-system-monitor y me da 350mb sin programas abiertos es mucho pero no es 900 jaja

---

