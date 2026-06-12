---
title: "¿Por que la transferencia de archivos es mas veloz?"
date: 2008-10-20
forum: Software
---

### Post by pol666 on 2008-10-20
Por que cuando paso datos de mi disco rigido a mi mp4 por USB, tarda muchisimo mas que en Linux, que demora todo no mas de un minuto.


La otra vez, cuando vinieron a mi casa unos amigos, estaba en windows y se me ocurrio cargar musica y ahi me acorde de cuanto tardaba, ahi nomas les mostre la transferencia en el Kubuntu y quedaron impresionados la diferencia de tiempo.


Cual es la razon de que sea mas rapido, ¿si el USB no va a la misma velocidad siempre?

---

### Post by smo0th on 2008-10-20
arquitectura del sistema operativo y controladores de hardware =) 

Linux > wind0ze

---

### Post by EnriqueK on 2008-10-21
Yo no tengo ese problema, mas bien al contrario, con win es mas rápido. Fijate si tenés habilitado DMA

---

### Post by euzkoarima on 2008-10-23
> **pol666 said:**
> 
Cual es la razon de que sea mas rapido, ¿si el USB no va a la misma velocidad siempre?

Supongo que tiene que ver con "la calidad" del espacio libre en el disco rígido. Win tiende a fragmentar, así que debe estar poniendo un poquito en cada lugarcito libre que tiene, y luego tiene que registrar la cadena de segmentos. Linux en cambio, por como maneja el disco, la mayoría de las veces va a poner cada archivo todo junto ==> menos problemas y menos tiempo

Saludos

---

### Post by pol666 on 2008-10-23
Ahh seguramente debe ser por eso, igual pense que el grado de fragmentacion dependia del sistema de particiones no del SO

---

### Post by sdennie on 2008-10-23
> **euzkoarima said:**
> Supongo que tiene que ver con "la calidad" del espacio libre en el disco rígido. Win tiende a fragmentar, así que debe estar poniendo un poquito en cada lugarcito libre que tiene, y luego tiene que registrar la cadena de segmentos. Linux en cambio, por como maneja el disco, la mayoría de las veces va a poner cada archivo todo junto ==> menos problemas y menos tiempo

Saludos

Si pero con una transferencia de USB, el disco rigido no es el "bottleneck".

Es posible que Linux esta usando las puertas de USB como USB2.0 y Windows piensa que son de USB1.0 (60MB/s vs 1.5MB/s).

---

