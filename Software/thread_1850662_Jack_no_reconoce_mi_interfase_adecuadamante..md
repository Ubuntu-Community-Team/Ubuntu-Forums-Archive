---
title: "Jack no reconoce mi interfase adecuadamante."
date: 2011-09-26
forum: Software
---

### Post by daggaz on 2011-09-26
Hola,
Estuve haciendo algunas pruebas para guardar sesiones de audio y  conexiones con Ladish y Jack Session. Durante el proceso, Ladish no  reconoció mi interfase de audio* M-Audio Fast Track Ultra* (FTU); la cual ya funcionaba bien con QjackCtl anteriormente.
Al querer volver a iniciar QjackCtl por su cuenta y seleccionar mi FTU  resulta que el programa no muestra las entradas y salidas correctas; si  no que lanza los canales de la tarjeta del portátil (a veces mezclados  con las entradas y salidas de Pulse Audio). Ya reinicié Jack, el equipo y  la interfase y no funciona. También probé borrar al configuración de  Jack de la FTU y volverla a realizar, pero sucede lo mismo.
Lo interesante es que sí aparece en la lista de dispositivos, y está bien reconocida por ALSA...


 Aquí mi salida de * cat /proc/asound/cards*:
 ```
 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf7cf8000 irq 46
 1 [Ultra          ]: USB-Audio - Fast Track Ultra
                      M-Audio Fast Track Ultra at usb-0000:00:1d.7-2, high speed


``` Y lo que muestra QjackCtl al iniciarse con la FTU:
 ```

22:30:08.275 Patchbay desactivada. 22:30:08.610 Reiniciar estadísticas. 
22:30:08.709 Cambios en las conexiones ALSA. 22:30:08.808 D-BUS: Disponible 
(org.jackaudio.service aka jackdbus). 22:30:09.734 D-BUS: Iniciando servidor JACK... 
Cannot connect to server socket err = No existe el fichero o el directorio Cannot conn
ect to server socket jack server is not running or cannot be started Cannot connect to serve
r socket err = No existe el fichero o el directorio Cannot connect to server socket jack s
erver is not running or cannot be started 22:30:10.029 D-BUS: El servidor JACK se ha inicia
do (org.jackaudio.service aka jackdbus). Mon Sep 26 22:30:09 2011: Saving settings to 
"/home/diego/.config/jack/conf.xml" ... Mon Sep 26 22:30:09 2011: Saving settings to 
"/home/diego/.config/jack/conf.xml" ... Mon Sep 26 22:30:09 2011: Saving settings to 
"/home/diego/.config/jack/conf.xml" ... Mon Sep 26 22:30:09 2011: Saving settings to 
"/home/diego/.config/jack/conf.xml" ... Mon Sep 26 22:30:09 2011: Saving settings to 
"/home/diego/.config/jack/conf.xml" ... Mon Sep 26 22:30:09 2011: driver "alsa" select
ed Mon Sep 26 22:30:09 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... 
Mon Sep 26 22:30:09 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon 
Sep 26 22:30:09 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 
26 22:30:09 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:30:09 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:30:09 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:30:09 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:30:09 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:30:09 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:30:09 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:30:09 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:30:09 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:30:09 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:30:09 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:30:09 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:30:09 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:30:09 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:30:09 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:30:09 2011: Starting jack server... Mon Sep 26 22:30:09 2011: JACK server starting in
 realtime mode with priority 10 Mon Sep 26 22:30:09 2011:
 control device hw:0 Mon Sep 26 22:30:09 2011: control device hw:0 Mon Sep 26 22:30:09 
2011: Acquired audio card Audio0 Mon Sep 26 22:30:09 2011: creating alsa driver ... 
hw:0|hw:0|1024|3|44100|0|0|nomon|swmeter|-|32bit Mon Sep 26 22:30:09 2011: 
control device hw:0 Mon Sep 26 22:30:09 2011: configuring for 44100Hz, period = 1024 fram
es (23.2 ms), buffer = 3 periods Mon Sep 26 22:30:09 2011: ALSA: final selected sample 
format for capture: 32bit integer little-endian Mon Sep 26 22:30:09 2011: ALSA: use 3 
periods for capture Mon Sep 26 22:30:09 2011: ALSA: final selected sample format for 
playback: 32bit integer little-endian Mon Sep 26 22:30:09 2011: ALSA: use 3 periods for playback Mon Sep 26 22:30:09 2011: graph reorder: new port 'system:capture_1' Mon Sep
 26 22:30:09 2011: New client 'system' with PID 0 Mon Sep 26 22:30:09 2011: graph 
reorder: new port 'system:capture_2' Mon Sep 26 22:30:09 2011: graph reorder: new port
 'system:playback_1' Mon Sep 26 22:30:09 2011: graph reorder: new port 
'system:playback_2' Mon Sep 26 22:30:09 2011: graph reorder: new port 
'system:playback_3' Mon Sep 26 22:30:09 2011: graph reorder: new port 
'system:playback_4' 22:30:12.274 Cambios en las conexiones JACK. 22:30:12.277 
Configuración del servidor salvada en "/home/diego/.jackdrc". 22:30:12.280 Reiniciar 
estadísticas. 22:30:12.331 Cliente activado. 22:30:12.345 Cambió el gráfico de conexiones 
de JACK. Mon Sep 26 22:30:12 2011: New client 'qjackctl' with PID 4184

```Y aquí en la configuración* default *(la tarjeta del portátil):

 ```

22:20:23.437 Patchbay desactivada. 22:20:23.682 Reiniciar estadísticas. 
22:20:23.732 Cambios en las conexiones ALSA. 22:20:23.793 D-BUS: Disponible 
(org.jackaudio.service aka jackdbus). 22:20:24.663 D-BUS: Iniciando servidor JACK... 
Cannot connect to server socket err = No existe el fichero o el directorio Cannot conn
ect to server socket jack server is not running or cannot be started Cannot connect to serve
r socket err = No existe el fichero o el directorio Cannot connect to server socket jack s
erver is not running or cannot be started 22:20:24.849 D-BUS: El servidor JACK se ha inicia
do (org.jackaudio.service aka jackdbus). Mon Sep 26 22:20:24 2011: Saving settings to 
"/home/diego/.config/jack/conf.xml" ... Mon Sep 26 22:20:24 2011: Saving settings to 
"/home/diego/.config/jack/conf.xml" ... Mon Sep 26 22:20:24 2011: Saving settings to 
"/home/diego/.config/jack/conf.xml" ... Mon Sep 26 22:20:24 2011: Saving settings to 
"/home/diego/.config/jack/conf.xml" ... Mon Sep 26 22:20:24 2011: Saving settings to 
"/home/diego/.config/jack/conf.xml" ... Mon Sep 26 22:20:24 2011: driver "alsa" select
ed Mon Sep 26 22:20:24 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... 
Mon Sep 26 22:20:24 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon 
Sep 26 22:20:24 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 
26 22:20:24 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:20:24 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:20:24 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:20:24 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:20:24 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:20:24 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:20:24 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:20:24 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:20:24 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:20:24 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:20:24 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:20:24 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:20:24 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:20:24 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:20:24 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:20:24 2011: Saving settings to "/home/diego/.config/jack/conf.xml" ... Mon Sep 26 
22:20:24 2011: Starting jack server... Mon Sep 26 22:20:24 2011: JACK server starting in 
realtime mode with priority 10 Mon Sep 26 22:20:24 2011: control device hw:0 Mon Sep 26 
22:20:24 2011: control device hw:0 Mon Sep 26 22:20:24 2011: Acquired audio card 
Audio0 Mon Sep 26 22:20:24 2011: creating alsa driver ... 
hw:0|hw:0|1024|3|44100|0|0|nomon|swmeter|-|32bit Mon Sep 26 22:20:24 2011: control 
device hw:0 Mon Sep 26 22:20:24 2011: configuring for 44100Hz, period = 1024 frames 
(23.2 ms), buffer = 3 periods Mon Sep 26 22:20:24 2011: ALSA: final selected sample 
format for capture: 32bit integer little-endian Mon Sep 26 22:20:24 2011: ALSA: use 3 
periods for capture Mon Sep 26 22:20:24 2011: ALSA: final selected sample format for 
playback: 32bit integer little-endian Mon Sep 26 22:20:24 2011: ALSA: use 3 periods for 
playback Mon Sep 26 22:20:24 2011: graph reorder: new port 'system:capture_1' Mon Sep 
26 22:20:24 2011: New client 'system' with PID 0 Mon Sep 26 22:20:24 2011: graph 
reorder: new port 'system:capture_2' Mon Sep 26 22:20:24 2011: graph reorder: new port 
'system:playback_1' Mon Sep 26 22:20:24 2011: graph reorder: new port 
'system:playback_2' Mon Sep 26 22:20:24 2011: graph reorder: new port 
'system:playback_3' Mon Sep 26 22:20:24 2011: graph reorder: new port 
'system:playback_4' 22:20:27.043 Cambios en las conexiones JACK. 22:20:27.047 
Configuración del servidor salvada en "/home/diego/.jackdrc". 22:20:27.062
 Reiniciar estadísticas. 22:20:27.086 Cliente activado. 22:20:27.141 Cambió el gráfico de conexiones 
de JACK. Mon Sep 26 22:20:26 2011: New client 'qjackctl' with PID 3572

```En ambos casos las entradas y salidas se muestran igual: dos entradas y  cuatro salidas (bocinas y audífonos)... Mi FTU tiene teóricamente ocho  entradas y ocho salidas (o eso detectaba jack anteriormente).
 Estoy corriendo *Ubuntu+KXStudio* con el Kernel de baja latencia.  Anteriormente mi FTU funcionaba bien con sus entradas y salidas; para  configurarla lo que había hecho era cambiar los dispositivos de entrada y  salida a *Fast Track Ultra hw:1*. Todo lo demás lo dejaba tal y como venía.
 Espero me puedan ayudar. Gracias.

---

### Post by daggaz on 2011-09-27
La solución que encontré fue configurar QjackCtl; en *Settings*, había que cambiar el valor de «Interfaz» a la FTU (hw:1) y dejar los dispositivos de entrada y salida como «(default)». 
No sé por qué anteriormente funcionaba muy bien con lo de los dispositivos... En fin.

---

