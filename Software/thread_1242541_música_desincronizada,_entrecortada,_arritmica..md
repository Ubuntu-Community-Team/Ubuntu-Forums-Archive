---
title: "música desincronizada, entrecortada, arritmica."
date: 2009-08-17
forum: Software
---

### Post by dirty fingers on 2009-08-17
Me pasa que cuando recargo el micro con muchas aplicaciones(mucho uso) el reproductor de audio (sea cual sea) empieza a andar a los saltos, tiene mas arritmia que banda de borrachos.

Si en el lanzador agrego: nice -n -10 "ruta de la aplicación" voy a solucionarlo ?
esa prioridad que le doy al proceso por decantacion va a caer en todas las dependecias ? (por ejemplo pulseaudio)

Voy bien o no se arregla así el problema ?

---

### Post by guillermolisi on 2009-08-17
Me parece que con esa solucion queres "vestir a un santo desvistiendo a otro".

Que kernel estas usando, Generic Server ?
Que procesador y cuanta RAM estas usando ?
Las demas aplicaciones son multimedia ?

---

### Post by dirty fingers on 2009-08-17
kernel 2.6.30 con gnome 2.26(con compiz fusion)
micro amd athlon xp 3200+ ram dual channel kingtons 2x512MB 400MHz 2-3-3-6 + disco sata
de swap tengo cero siempre.
y tengo abierta cosas comunes, exaile deluge pidgin firefox tucan totem nautilus, etc.
en windos siempre mantuve el problema de los recursos controlados con la prioridad.
que alternativa planteas ?

---

### Post by guillermolisi on 2009-08-17
> **dirty fingers said:**
> kernel 2.6.30 con gnome 2.26(con compiz fusion)
micro amd athlon xp 3200+ ram dual channel kingtons 2x512MB 400MHz 2-3-3-6 + disco sata
de swap tengo cero siempre.
y tengo abierta cosas comunes, exaile deluge pidgin firefox tucan totem nautilus, etc.
en windos siempre mantuve el problema de los recursos controlados con la prioridad.
que alternativa planteas ?
2.6.30 Generic o Server ? Supongo que Generic

Te fijaste que consumo de CPU registras cuando comienza ese sintoma ?
Por las dudas y considerando que no tenes swapping (good point), el uso de disco tambien es casi nulo o notas que trabaja intensamente ?

IMHO, si le cambias la prioridad al proceso vas a mejorar el rendimiento de uno a costillas de los demas, por eso creo que hay otro tema dando vueltas.
El extremo seria que solo te funcione el que fue modificado y el resto quede a la espera de que ese termine para continuar su ejecucion.

Si fuera un tema generalizado, este thread se hubiera abierto hace tiempo atras. Con lo cual, las prioridades que administra cada kernel son, en lineas generales, las adecuadas para cada uso (desktop,server, multimedia/signal processing)

Modificar la prioridad de ejecucion no es ni buena ni mala idea, solo hay que saber de antemano cuales son sus consecuencias.

---

### Post by dirty fingers on 2009-08-20
listo, con un -10 nos salvamos en el chinchon :P y también tenemos controlado el uso de cpu. ya puedo escuchar musica:guitar: sin preocuparme por abrir demasiadas cosas. tendría que estar usando menos micro pero bueee; es mi primer instalacion de ubuntu y mas que una pc de uso diario parece un laboratorio. me la voy a aguntar hasta la nueva version que ya casi llega y ahi empezamos mas ordenado ;-) gracias.

---

### Post by nopersona on 2009-08-22
Si mal no recuerdo, los AMD tienen un control de frecuencia de cpu, lo cual es posible activar para que utilizen recursos según se cargan procesos, o dejarlo en 100% siempre. No recuerdo el nombre, lo voy a buscar, yo tengo un Athlon 64 3200+ y tengo acivada esta opción. Por ahí podría  ir.  

Podrías dejar abierto un terminal con 

```
sudo top 
```

o con 

```
sudo ps -AF
```


para ver los procesos que comen la cpu.

---

