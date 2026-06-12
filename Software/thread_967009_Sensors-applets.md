---
title: "Sensors-applets"
date: 2008-11-01
forum: Software
---

### Post by ramiro_md on 2008-11-01
Otra vez yo por acá, je..ando buscando un aplet para la temperatura del motherboard y de la placa de video, aunque este útlimo no es tan urgente :P.
Instalé el sensosrs-applet, pero solo trae para el procesador y el discorígido. Si alguien conoce de un applet que tenga lo que busco, bienvenido sea.

---

### Post by jpmorelli on 2008-11-01
El sensors-applet de Gnome tiene placa de video, el tema es que lo tiene que detectar.
Instalaste el paquete lm-sensors y corriste el sensors-detect ? Dale a todo que si y en la ùtlima pregunta ojo que te dice si queres que se carguen automaticamente al inicio del boot, yo siempre le puse que si vos fijate que queres.
En mi caso, mi Nvidia 7300 GS la detecta y la muestra.

Suerte !

---

### Post by ramiro_md on 2008-11-01
Si, ya instale el lm-sensors y corri el sensors-detect (le dí a todo que si etc...), pero siguen sin aparecer los sensores que quiero en el applet (o por lo menos yo no me doy cuenta), acá dejo un screen de lo que me permite "monitorizar". POsteo las salidas del sensor-detect ?...gracias por contestar.

---

### Post by ramiro_md on 2008-11-01
no atacheo el anterior...
y este tampoco asique lo escribo:

acpi
     THRM   CPU
hddtemp
     /dev/sg1
libsensors
     temp1
     coretemp0
     coretemp0
     coretemp1
     coretemp1

---

### Post by ramiro_md on 2008-11-01
pequeño detalle, reinicié ubuntu y aparecieron más sensores en las preferencias del applet...hay algunos que sonm para el voltaje de tal o cual cosa...pero cuales son los de la temp del mother y la placa de video ?

---

### Post by MeduZa on 2008-11-02
> **ramiro_md said:**
> pequeño detalle, reinicié ubuntu y aparecieron más sensores en las preferencias del applet...hay algunos que sonm para el voltaje de tal o cual cosa...pero cuales son los de la temp del mother y la placa de video ?

el lm-sensors te detecta los sensores, y te dice que modulos necesitas, es mas te pregunta si queres que el te los agregue al modprove. tenes que reiniciar o cargar los modulos necesarios.
Luego con sensors ves que te detecto. si no te detecta lo que buscas anda a la pagina de lm-sensor y fijate si tu motherboard tiene soporte.
Any way sensors applet se basa en libsensors de lm-sensors asi que todo esta centrado en lm-sensors que es lo que tenes que hacer andar primero.

---

