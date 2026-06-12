---
title: "Ubuntu 9.10 - Control De volumen"
date: 2009-12-06
forum: Software
---

### Post by NickCis on 2009-12-06
El problema que estoy teniendo es que el control de volumen ignora lo que hago xD... Si, basicamente si subo/bajo el volumen desde ahi, es lo mismo qeu no haga nada,,,
Puedo cambiar el volumen usando el alsamixer, pero no ese controlcito. Lo unico qe responde de eso es lo de silenciar.
Alguna idea?.

Saluds y muchas gracias.

P.D.: Tmb por extrañas razones siempre cuando se prende la pc y entra al escritorio, el volumen esta muteado (silenciado), y se estucha un raro PUM como un golpe =S

---

### Post by guillermolisi on 2009-12-06
Fijate si lo que se esta hablando [en este thread]("http://ubuntuforums.org/showthread.php?t=1325344") te soluciona el problema del "pum".

---

### Post by emiliano_raso on 2009-12-06
Dos preguntas:
- Pero tenes sonido o no? Porque solo aclaraste que no podes modificar el volumen, pero no dijiste si tenias sonido :-P
- Estas en Gnome?

Si directamente no escuchas nada, fijate que seguramente tenes alguno de los volumenes en silencio o al minimo.
Boton derecho al iconito del volumen y revisa que todo este bien.

---

### Post by NickCis on 2009-12-06
---------- Post Repetido, leer el siguiente ----------

---

### Post by NickCis on 2009-12-06
Hice lo qeu sugiere guillermolisi, pero no me dio un resultado favorable, despues de actualizar el alsa y comentar el "alsa-base.conf", el problema persiste (tanto el del PUM, como el qe no anda el Control de Volumen).

emiliano_raso, si, tengo sonido, puedo escuchar musica y todo. Pero el problema es que cada vez qe prendo la pc, el sonido arranca en silencio, y desde el control de volumen (que esta en el tray), modifico el volumen pero me ignora las modificaciones, lo unico qe parece funcionar es la opcion de "mute".

Respecto al entorno grafico, no, no estoy en Gnome, toy usando LXDE (el qe viene en lubuntu-desktop), pero no estoy usando el Control de Volumen del LXpanel, estoy usando el de GNOME, ese que esta en el systray, que se inicia solo y en la parte de sessiones figura con el nombre de "Volume Control".
Probe usando el control de volumen del Lxpanel, pero tiene el mismo problema que este, puedo silenciar pero no cambiar el volumen.

Saludos.

---

### Post by NickCis on 2009-12-06
Probe esto: " [http://ubuntuforums.org/showthread.php?t=1317562](http://ubuntuforums.org/showthread.php?t=1317562) " pero sigo sin poder solucionar el problema del control de volumen. El problema de PUM, es soportable, mucho no molesta, pero no poder variar el volumen (y ensima qe la pc prenda en mute), hace que directamente no use el volumen.

Saludos

Edit:
Segui investigando y di con esto: [http://www.tedcarnahan.com/2009/11/26/fixing-volume-control-on-inspiron-9400-e1705-in-ubuntu-karmic/](http://www.tedcarnahan.com/2009/11/26/fixing-volume-control-on-inspiron-9400-e1705-in-ubuntu-karmic/)

Ahi dice que en vez de reiniciar la pc ejecute unos comandos para que reinicie el sonido, la respuesta de uno de ellos me llamo la atencion =S.
```

oldpc@oldpc:~$ sudo invoke-rc.d alsa-utils restart
 * Shutting down ALSA...                                                 [ OK ] 
 * Setting up ALSA...                                                    [ OK ] 
oldpc@oldpc:~$ killall pulseaudio
oldpc@oldpc:~$ pulse-session
El programa «pulse-session» no está instalado actualmente.  Puede instalarlo escribiendo:
sudo apt-get install pulseaudio
pulse-session: command not found
oldpc@oldpc:~$ 

```Me dice que no tengo instalado el pulse audio, pero si lo pongo a instalar, supuestamente ya esta instalado =S.

```

oldpc@oldpc:~$ sudo apt-get install pulseaudio
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
pulseaudio ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
oldpc@oldpc:~$ 

```Alguna idea?.

---

### Post by NickCis on 2009-12-07
Si mato el proceso pulseaudio y vuelvo a ejecutar me devuelve este error.

```

oldpc@oldpc:~$ killall pulseaudio
oldpc@oldpc:~$ pulseaudio
E: module-udev-detect.c: Failed to get card object.
W: alsa-mixer.c: Failed to set switch of Hardware Master: Operación no permitida
E: module-udev-detect.c: Failed to get card object.
E: module-alsa-card.c: Failed to find a working profile.
E: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.

```

Una posible parcial solucion seria setear qe la maquina prenda en determinado valor de volumen. Es posible eso?. (actualmente inicia en mute, y al no poder modificar el volumen atraves de ese control me veo forzado a abrir el alsamixer).

Saludos.

---

### Post by Mauro22 on 2009-12-07
> **NickCis said:**
> Si mato el proceso pulseaudio y vuelvo a ejecutar me devuelve este error.

```

oldpc@oldpc:~$ killall pulseaudio
oldpc@oldpc:~$ pulseaudio
E: module-udev-detect.c: Failed to get card object.
W: alsa-mixer.c: Failed to set switch of Hardware Master: Operación no permitida
E: module-udev-detect.c: Failed to get card object.
E: module-alsa-card.c: Failed to find a working profile.
E: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.

```

Una posible parcial solucion seria setear qe la maquina prenda en determinado valor de volumen. Es posible eso?. (actualmente inicia en mute, y al no poder modificar el volumen atraves de ese control me veo forzado a abrir el alsamixer).

Saludos.



Me parece que tenes que levantarlo como sudo, lo digo por lo de 'operacion no permitida'

---

### Post by NickCis on 2009-12-07
Pude solucionar el problema siguiendo estas instrucciones:
[http://ubuntuforums.org/showthread.php?t=1305889](http://ubuntuforums.org/showthread.php?t=1305889)

Lo unico, que ahora no me aparece mas el control de volumen en el systray, si lo ejecuto por consola me dice qe "No se pudo ejecutar el demonio" (o algo asi), no da mas explicacion =S... Usare el del lxpanel y listo.

Saludos.

Edit: Tmb se soluciono el tema del PUM

---

