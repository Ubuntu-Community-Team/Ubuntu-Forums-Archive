---
title: "Video lento vlc  por red ubuntu 10.10"
date: 2010-11-09
forum: Software
---

### Post by djthree on 2010-11-09
Hola amigos,

Espero me puedan ayudar. Se me esta "trabando" la reproducción de videos cuando levanto la película por RED Wi-Fi, tanto con VLC, como MPLAYER y TOTEM. Esto solo me pasa cuando intento reproducir desde el Ubuntu 10.10 instalado en la notebook, cuando booteo en esa misma notebook con Windows Vista las pelís corren perfectamente sin tirones.

Paso a dar detalles a ver si me pueden ayudar:

Tengo 2 maquinas
Una de escritorio con: booteo dual WinXP y Ubuntu 10.10
Una Notebook HP Pavilion dv41425la: booteo dual Win Vista y Ubuntu 10.10

En la PC de escritorio tengo compartida una carpeta con películas (en una partición NTFS, compartida en ambos sitemas WinXP y Ubuntu)

Cuando reproduzco la película con VLC, MPLAYER o TOTEM desde Ubuntu 10.10, la peli corre con tirones, pero cuando booteo en Windows Vista y reproduzco la peli con VLC o algún otro programa, corre bien...

Aclaración los videos que reproducen en forma local correen bien en ambas máquinas.

Que puede estar pasando?

---

### Post by guillermolisi on 2010-11-09
Cuando probas usando Windows, el material que reproducis es local a la maquina o tambien se consume via red WiFi ?

Que caracteristicas tiene la red WiFi que estas usando ? Que hardware estas usando ?

---

### Post by juancarlospaco on 2010-11-09
que nivel de señal?
yo usaria un stream usando udp con vlc en lugar de smb

---

### Post by djthree on 2010-11-09
> **juancarlospaco said:**
> que nivel de señal?
yo usaria un stream usando udp con vlc en lugar de smb

Como hago eso del  UDP? lo cambio en las preferencias del VLC?
debo cambiar algo en la configuración de la carpeta compartida?

---

### Post by djthree on 2010-11-09
> **guillermolisi said:**
> Cuando probas usando Windows, el material que reproducis es local a la maquina o tambien se consume via red WiFi ?

Las películas que reproduzco desde la notebook (peliculas AVI, ripeadas con divx o xvid) están en la PC de escritorio y lo levanto a través de la RED Wi-Fi, por medio del ROUTER. De esta manera "tironea".

Cuando reproduzco material localmente (películas que están en la misma notebook) anda bien, no "tironea".

En ambos casos lo hago corriendo Ubuntu 10.10


Que características tiene la red WiFi que estas usando ? Que hardware estas usando ?

Tengo conectado a la linea telefónica un ROUTER HUAWEI HG520 que se conecta por ADSL. La PC de escritorio esta conectada por cable ethernet al router. La notebook se conecta a internet y a la pc de escritorio por wi-fi.

la placa wi-fi de la notebook esta integrada, el modelo es HP Pavilion DV4-1425la.

---

### Post by guillermolisi on 2010-11-09
Ok. Gracias

Considerando lo que mencionas respecto de como consumis desde la notebook el material multimedia, y que cuando se reproduce localmente el mismo material funciona bien, se me ocurre que hay algun temita a revisar en el enlace inalambrico.

---

### Post by hectorivand on 2010-11-09
> **djthree said:**
> Tengo conectado a la linea telefónica un ROUTER HUAWEI HG520 que se conecta por ADSL. La PC de escritorio esta conectada por cable ethernet al router. La notebook se conecta a internet y a la pc de escritorio por wi-fi.

la placa wi-fi de la notebook esta integrada, el modelo es HP Pavilion DV4-1425la.

Hola Master, en una terminal postea el resultado del siguiente comando.

```
lsusb
```

Así sabemos exactamente que placa wifi trae tu equipo.

Si en Windows, usándolo de la misma manera te funciona bien, tal vez hay algún tema con el driver de la Wifi que hace que funcione de manera errática, con micro cortes o cosas similares, si es Realtek no me extrañaría.

Espero esa info.

Saludos
Nacho

---

### Post by djthree on 2010-11-12
Gracias Muchachos! Ya lo solucioné de la siguiente manera:


En el programa VLC fui a Herramientas-> Preferencias -> Entrada y codecs -> Modifique la opción "Política de almacenamiento predeterminada", creo que estaba en "Normal" y la pasé a "baja latencia".

Así se solucionó, al menos por ahora esta funcionando OK.

Aclaro que también fui metiendo mano en otras opciones del VLC que no resultaron.

Con respecto al "compañero" que me pido lo del lsubs, es este el resultado:

```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 138a:0001 DigitalPersona, Inc Fingeprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 174f:1107 Syntek 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


Las preguntas que me quedan por resolver serían:
¿que es lo que cambié que ahora anda bien?
¿como puedo comprobar que mi placa de red wi-fi esta funcionando eficientemente?

Gracias!

PD: Yo llegué a Ubuntu en la versión 7.04 por primera vez, me fui porque metí la pata y arruiné el sistema... volí con la 8.04, me fui de nuevo, porque la volví arruinar... y ahora estoy de nuevo con la 10.10 !!!! esta es la mejor versión que conocí hasta ahora.... sinceramente anda muy bien! Espero no estropearla como las anteriores !!!  SALUDOS!

---

### Post by hectorivand on 2010-11-12
> **djthree said:**
> Gracias Muchachos! Ya lo solucioné de la siguiente manera:


En el programa VLC fui a Herramientas-> Preferencias -> Entrada y codecs -> Modifique la opción "Política de almacenamiento predeterminada", creo que estaba en "Normal" y la pasé a "baja latencia".

Así se solucionó, al menos por ahora esta funcionando OK.

Aclaro que también fui metiendo mano en otras opciones del VLC que no resultaron.

Con respecto al "compañero" que me pido lo del lsubs, es este el resultado:

```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 138a:0001 DigitalPersona, Inc Fingeprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 174f:1107 Syntek 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


Las preguntas que me quedan por resolver serían:
¿que es lo que cambié que ahora anda bien?
¿como puedo comprobar que mi placa de red wi-fi esta funcionando eficientemente?

Gracias!

PD: Yo llegué a Ubuntu en la versión 7.04 por primera vez, me fui porque metí la pata y arruiné el sistema... volí con la 8.04, me fui de nuevo, porque la volví arruinar... y ahora estoy de nuevo con la 10.10 !!!! esta es la mejor versión que conocí hasta ahora.... sinceramente anda muy bien! Espero no estropearla como las anteriores !!!  SALUDOS!

Lo que tocaste es algo así como la velocidad con la que VLC iba a buscar el contenido para seguir reproduciendo, si bajaste la latencia, bajas los tiempos en los que VLC invoca ese archivo.

Interesante hallazgo :D 

El resultado del USB Syntek es un Dongle USB que es la primera vez que lo escucho/veo, sin embargo, investigando en el sitio Web tienen drivers para Linux, así que solo, si, algunas vez tenes problemas, bájate los drivers del fabricante.:

[http://bit.ly/a14hyE](http://bit.ly/a14hyE)

Si ahora funciona bien, no lo toques, si ves que no mejora, instala los drivers para Ubuntu que hay en el sitio.

Saludos
Nacho

---

