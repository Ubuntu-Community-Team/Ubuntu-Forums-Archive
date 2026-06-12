---
title: "Ubuntu no monta disco NTFS"
date: 2008-12-17
forum: Software
---

### Post by nemodot on 2008-12-17
Hola, acabo de instalar ubuntu mediante WUBI y el disco NTFS donde se instaló no se muestra (no se monta), pero sí se monta el otro disco NTFS donde está instalado windows.

Cómo hago para poder montarlo?

---

### Post by Mauro22 on 2008-12-17
Podes iniciar ubuntu?? si es asi, es logico que la unidad esta montada...

Aparece en la lista del menu "lugares"?

---

### Post by nemodot on 2008-12-17
Si, puedo acceder a ubuntu pero el disco no aparece en <<Lugares>>
:S

---

### Post by sajnox on 2008-12-17
Como dijo Mauro es logico que no lo veas en el menu lugares, entra por equipo y fijate sistema de archivos, ese es el disco "virtual" que crea wubi

---

### Post by nemodot on 2008-12-17
No lo veo, no está en /media tampoco.

---

### Post by Mauro22 on 2008-12-18
Tiene que estar... si estas usando ubuntu es porque el disco se monto.


Abri nautilus y en la barra de direccioes pone "computer:///" a ver que aparece

---

### Post by sajnox on 2008-12-18
> **nemodot said:**
> No lo veo, no está en /media tampoco.

Si mal no te entiendo vos queres ver el disco virtual sobre el cual se instalo ubuntu. En tal caso lo que queres ver es "/" por lo que obviamente no lo ves en /media por que precisamente media se monta en /

Mi siguiente pregunta es, para que lo queres ver? y que es lo queres usar?

Saludos

---

### Post by nemodot on 2008-12-18
Me parece, sajnox, que no entendiste nada. El disco al que quiero acceder es el NTFS de Windows donde instale Ubuntu mediante Wubi.

---

### Post by c4d0rn4 on 2008-12-18
por si las dudas voy a aclarar un par de cosas.

Wubi es un programa para windows que crea en un archivo una partición virtual en la que se aloja Ubuntu. La vez que lo probé no me agradó el rendimiento que tuve; creo que afecta la performance del swapping y en mi maquina con poca ram es crucial (lamentablemente).

un segundo de busqueda en google:
[http://ubuntuforums.org/showthread.php?t=684877](http://ubuntuforums.org/showthread.php?t=684877)
espero sirva.
> **ago said:**
> If this is the partition where you have wubi, it will be available as /media/host in 7.10 and /host in 8.04

---

### Post by abn91c on 2008-12-18
en el wubi windows esta el /host

---

### Post by nemodot on 2008-12-19
Muchas gracias, no sabia lo de /host aunque busqué sobre esto en google, no encontré nada.

---

