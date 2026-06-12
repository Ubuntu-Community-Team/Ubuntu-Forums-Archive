---
title: "¿Como configuro wine para que funcione con PulseAudio?"
date: 2008-08-31
forum: Software
---

### Post by atari130xe on 2008-08-31
Alguien logró hacer funcionar aplicaciones a través de wine con sonido incluído sin que el mismo suene mal (entre cortado, etc.)? Seteo ALSA y funciona pero entrecortado, seteo ESD y se cuelga, pongo OSS y menos... :confused:

---

### Post by sherwoodinc on 2008-08-31
Yo usé el Wine para jugar un par de juegos 3D... Actualmente juego al Lineage2 :)
Mi placa de sonido es una Soundblaster Live 24-bit (módulo ca0106)
Mi config Actual, de la pestaña "Audio" del winecfg:

[X] "Manejador ALSA" 

DirectSound
Aceleración Hardware: "Completa"
Frecuencia Muestreo: 44100  Bits por muestra: 16
Emulación del manejador [X]

[X] es "tildado" :D

Podés probar jugando con la configuración de Directsound...

---

### Post by WanderingKnight on 2008-08-31
Offtopic, pero... quien hace las traducciones?!?

"Manejador"?!? lol

---

### Post by Hei Ku on 2008-08-31
Las hacemos vos y yo, todos. ;)
Sos bienvenido a colaborar con las traducciones en Launchpad. 

El equipo español es el que está mejor posicionado, pero siempre hace falta más ayuda.

---

### Post by atari130xe on 2008-08-31
> **sherwoodinc said:**
> Yo usé el Wine para jugar un par de juegos 3D... Actualmente juego al Lineage2 :)
Mi placa de sonido es una Soundblaster Live 24-bit (módulo ca0106)
Mi config Actual, de la pestaña "Audio" del winecfg:

[X] "Manejador ALSA" 

DirectSound
Aceleración Hardware: "Completa"
Frecuencia Muestreo: 44100  Bits por muestra: 16
Emulación del manejador [X]

[X] es "tildado" :D

Podés probar jugando con la configuración de Directsound...

Configuré como vós el sonido, arranca bién, al rato empieza a entrecortarse y de repente queda mudo...

---

### Post by sherwoodinc on 2008-09-01
Con esa config puedo jugar horas sin problema... Así que hay que ver si el problema es de configuración, o de tu placa de sonido (puede que la placa necesite alguna configuración extra, se me ocurre que especialmente si es onboard).
    Además de lo básico que te deja tocar el winecfg en la pestaña de audio, hay muchas cosas para tocar directamente en el registro del wine, yo tuve que poner cosas ahí por ejemplo para jugar al Oblivion, porque hay seteos del DirectX que sí o sí hay que meter a mano con el regedit).

Algunos datos que podrías pasar:

- Tu versión de wine (la mía: wine-1.1.3)
- Tu modelo de placa de sonido ( "lspci -v" te tira una lista de todo el hardware, buscá los "Multimedia audio controller" )
- Con qué soft te trae problemas (al menos alguno de ejemplo)

Algunas cosas que podés probar:

- Instalar el último wine bajado de [www.winehq.org](www.winehq.org), si no lo tenés ya (tiene un repositorio para poder mantener el wine actalizado)

- Probar si también trae problemas con una configuración "de cero": basta con renombrar tu carpeta .wine a ".wine-backup" o algo similar, y después correr "wineprefixcreate" para que te haga una carpeta .wine nueva. Luego de hacer pruebas, podés borrar la .wine de pruebas y reemplazarla por el backup.

Con respecto a este último tip, cuando en general algún problema me vuelve loco, tengo un usuario extra que uso solamente para probar si el problema se repite (especialmente porque mi home "real" es un quilombo :S)

---

### Post by atari130xe on 2008-09-03
> **sherwoodinc said:**
> Con esa config puedo jugar horas sin problema... Así que hay que ver si el problema es de configuración, o de tu placa de sonido (puede que la placa necesite alguna configuración extra, se me ocurre que especialmente si es onboard).
    Además de lo básico que te deja tocar el winecfg en la pestaña de audio, hay muchas cosas para tocar directamente en el registro del wine, yo tuve que poner cosas ahí por ejemplo para jugar al Oblivion, porque hay seteos del DirectX que sí o sí hay que meter a mano con el regedit).

Algunos datos que podrías pasar:

- Tu versión de wine (la mía: wine-1.1.3)
- Tu modelo de placa de sonido ( "lspci -v" te tira una lista de todo el hardware, buscá los "Multimedia audio controller" )
- Con qué soft te trae problemas (al menos alguno de ejemplo)

Algunas cosas que podés probar:

- Instalar el último wine bajado de [www.winehq.org](www.winehq.org), si no lo tenés ya (tiene un repositorio para poder mantener el wine actalizado)

- Probar si también trae problemas con una configuración "de cero": basta con renombrar tu carpeta .wine a ".wine-backup" o algo similar, y después correr "wineprefixcreate" para que te haga una carpeta .wine nueva. Luego de hacer pruebas, podés borrar la .wine de pruebas y reemplazarla por el backup.

Con respecto a este último tip, cuando en general algún problema me vuelve loco, tengo un usuario extra que uso solamente para probar si el problema se repite (especialmente porque mi home "real" es un quilombo :S)

aca te va la info:

Wine Version: 1.1.3

Placa de audio:
```
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 820f
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at bfffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

```

Problemas con Worms 4, Bus Driver

---

### Post by sherwoodinc on 2008-09-13
Disculpas por la tardanza...

Probá configurar el audio de wine como "oss", y arrancar alguno de los juegos desde una Terminal, entrando a la carpeta donde se instaló el juego y ejecutando el comando

```
padsp wine nombre_del_ejecutable
```

Yo tuve que hacer eso estos días para tener un juego + el teamspeak corriendo a la vez.

Si te funciona podés modificar las propiedades del icono lanzador del juego (en el escritorio, si lo creaste al instalar) para agregar el "padsp" antes del comando "wine".

Contame si te ayuda en algo...

---

