---
title: "Controlador de Video me baja la resolucion."
date: 2009-12-05
forum: Software
---

### Post by V A M P I R O on 2009-12-05
Holas, logre convencer a un amigo de instalarle ubuntu, ya estaba chato de virus asique, le di formato, pero quedó con una resolucion muy baja para el monitor (800x600) y me dije:

Mismo, bueno la podré subir un poco al instalar el controlador gráfico, pero aqui viene el problema, instale el recomendado, y la resolucion me bajó aun mas y quedó en 640x480, reinicie por recovery mode resetie las propiedades gráficas y quedó nuevamente en 800x600...

Que puedo hacer por siacaso es 9.04.

---

### Post by moreback on 2009-12-05
- ¿Tarjeta de video?
- ¿Modelo del monitor?
- ¿Rango de frecuencias de refresco de éste?

---

### Post by V A M P I R O on 2009-12-06
En este momento no recuerdo esos datos, no es mi computador y ademas no se lo que es el rango de frecuencias de refresco de éste

Pederdón por la ignorancia.

---

### Post by Carlos C on 2009-12-06
¿ni siquiera el modelo de la tarjeta?

---

### Post by Patriciologico on 2009-12-08
Sin esos datos todo sera supuestos, mi supuesto, es que esta usando una versión del Kernel, con soporte imcompleto para su tarjeta gráfica.

Saludos

---

### Post by V A M P I R O on 2009-12-11
El monitor es un NEC MultiSyinc LCD 1550v  de 60Hz

El controlador grafico que me recomienda es:

Controlador para tarjetas Graficas NVIDIA (Versión 96)

nose como saber el nombre de la tarjeta gráfica Solo diganme como y les doy la info.


Gracias.;)

Agrego la informacion de FUCH:

```

Escritorio:    GNOME

``````

$lspci|grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)

``````

$cat /var/log/Xorg.0.log|grep EE
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

``````

$cat /var/log/messages |grep error

``````

$cat /var/log/syslog |grep error

``````

$lsmod |grep drm

``````

$lsmod |grep agp
via_agp                16256  1 
agpgart                42696  2 nvidia,via_agp

```

ahh, lo tengo con las propiedades graficas iniciales, no he modificado en nada el controlador.

---

### Post by moreback on 2009-12-12
Después de instalar el driver recomendado de NVIDIA tienes que ejecutar una aplicación que aparecerá en Sistema -> Administración, creo que se llama NVIDIA Settings o algo así. Con esto podrás configurara la resolución que necesites y la escribirá en /etc/X11/xorg.conf.

Saludos.

PD: asegúrate de ejecutarla con gksu

---

### Post by V A M P I R O on 2009-12-13
precisamente eso hice, pero lo máximo que me deja es 640x480.

necesito la ayuda, o deberé formatear nuevamente a WinDOS

---

### Post by moreback on 2009-12-13
Entonces te falta agregar las frecuencias de refresco a tu /etc/X11/xorg.conf. Las debieras encontrar en el manual de tu monitor.

---

### Post by V A M P I R O on 2009-12-13
ok gracias, voy a ver si tienen el manual del monitor, de lo contrario voy a probar con el xrog.conf de otro equipo de similares caracteristicas parfa ver si funciona obiamente respaldando el original y si no arranca lo recupero por consola.

---

