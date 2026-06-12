---
title: "Rhythmbox 0.12.8 se cuelga al reproducir CD."
date: 2010-05-15
forum: Software
---

### Post by Sarum001 on 2010-05-15
Buenas, a ver si me pueden dar una mano con esto:

_El problema:_ Rhythmbox 0.12.8 se vuelve inestable al reproducir algunos CD'S, se cierra de golpe, o se queda sin respuesta.
Parece no tener problemas con la reproducción de archivos locales.

Lo arranco desde la consola y esto es lo que sale:
[I][SIZE="2"]cesar@cesar-desktop:~$ rhythmbox

** (rhythmbox:1624): CRITICAL **: cr_parser_new_from_buf: assertion `a_buf && a_len' failed

** (rhythmbox:1624): CRITICAL **: cr_parser_set_sac_handler: assertion `a_this' failed

(rhythmbox:1624): librsvg-WARNING **: Error setting CSS SAC handler


** (rhythmbox:1624): CRITICAL **: cr_parser_destroy: assertion `a_this && PRIVATE (a_this)' failed[/SIZE][/I]

Le doy a reproducir algún  CD conflictivo. Reproduce una pista, se planta, la consola muestra:

[I][SIZE="2"]scsi_read error: sector=164407 length=27 retry=0
                 Sense key: 3 ASC: 11 ASCQ: 0
                 Transport error: Medium reading data from medium
                 System error: Error de entrada/salida

scsi_read error: sector=164434 length=27 retry=0
                 Sense key: 3 ASC: 11 ASCQ: 0
                 Transport error: Medium reading data from medium
                 System error: Error de entrada/salida

scsi_read error: sector=164461 length=27 retry=0
                 Sense key: 3 ASC: 11 ASCQ: 0
                 Transport error: Medium reading data from medium
                 System error: Error de entrada/salida[/SIZE][/I]
y se repite una y otra vez hasta que fuerzo el cierre.

Descarto que sean problemas en el CD ya que en Windows se reproducen a la perfección.

maquina:
Intel Celeron CPU 2,53 Ghz, 512 Mb de RAM, Sonido y video integrado (Chipset Intel Corporation 82865G ) a la placa madre (Asrock 775i65G) con Ubuntu Lucid, con escritorio gnome.

A ver si así queda mas claro:

[I][SIZE="2"]cesar@cesar-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)[/SIZE][/I]

La verdad se me quemaron los papeles con esto... que no son muchos por cierto. 
Avisen si hace falta mas info. Gracias.

Saludos.

---

### Post by guillermolisi on 2010-05-15
Me llama la atencion que el comportamiento varie segun el CD a reproducir. Parece que tenes identificados los "conflictivos" de los que no lo son con lo cual tambien pareceria no ser problema ni de hard ni de soft, solo de media y tal vez algo relacionado con la velocidad con la cual se grabaron los CDs.

Si bien el hardware es el mismo, los drivers no y eso modifica el comportamiento de un componente para un sistema operativo u otro.

---

### Post by Sarum001 on 2010-05-15
Ok, gogleando con los errores que me tira la consola estoy empezando a sospechar que se trata de dos errores distintos.
 
Por un lado, el que me da cuando abro el reproductor:
"** (rhythmbox:1624): CRITICAL **: cr_parser_new_from_buf: assertion `a_buf && a_len' failed..., etc." 
Acá los resultados del buscador me refieren a páginas que padecen el mismo error (Ej.:[http://es.wikilingue.com/gl/Provincias_de_Espa%C3%B1a]("http://es.wikilingue.com/gl/Provincias_de_Espa%C3%B1a")) o a algún foro donde, si bien los casos no son los mismos, hacen referencia a problemas del algún programa con el manejador de ventanas, etc. En definitiva, problemas con una librería SVG que no creo sean determinantes para el caso.

Segundo, y mi sospecha mas fuerte: Los drivers.
>  tenes identificados los "conflictivos" de los que no lo son Efectivamente, a Rhythmbox parece que no le gusta Ok computer de Radiohead :lolflag: entre otros.

> Si bien el hardware es el mismo, los drivers no y eso modifica el comportamiento de un componente para un sistema operativo u otro.
**Entonces ¿Cómo puedo saber por consola que drivers están instalados y se encargan del sonido- y por extensión- de otros componentes de hardware?**

Gracias Guillermo.

Saludos

---

### Post by guillermolisi on 2010-05-15
> **Sarum001 said:**
> Ok, gogleando con los errores que me tira la consola estoy empezando a sospechar que se trata de dos errores distintos.
 
Por un lado, el que me da cuando abro el reproductor:
"** (rhythmbox:1624): CRITICAL **: cr_parser_new_from_buf: assertion `a_buf && a_len' failed..., etc." 
Acá los resultados del buscador me refieren a páginas que padecen el mismo error (Ej.:[http://es.wikilingue.com/gl/Provincias_de_Espa%C3%B1a](http://es.wikilingue.com/gl/Provincias_de_Espa%C3%B1a)) o a algún foro donde, si bien los casos no son los mismos, hacen referencia a problemas del algún programa con el manejador de ventanas, etc. En definitiva, problemas con una librería SVG que no creo sean determinantes para el caso.

Segundo, y mi sospecha mas fuerte: Los drivers.
 Efectivamente, a Rhythmbox parece que no le gusta Ok computer de Radiohead :lolflag: entre otros.


**Entonces ¿Cómo puedo saber por consola que drivers están instalados y se encargan del sonido- y por extensión- de otros componentes de hardware?**

Gracias Guillermo.

Saludos
En una consola/terminal ingresa "lsmod" (sin las comillas) y te da que driver/modulo esta asociado con que componente de hardware.

Tambien revisaria el log /var/log/dmesg donde deberias ver informacion adicional relacionada con el hardware, reconocimiento y uso.

---

### Post by Sarum001 on 2010-05-15
Siguiendo con mis pruebas recordé el tema de los codecs. Instalé los Medibuntu que no tenía instalados, incluyendo los de Win 32 por las dudas, pero el problema persiste.
También se me ocurrió ripear al rígido uno de los CD con asunder, que bajé del centro de software. Grabó los archivos muy bien, eso si en formato .ogg (Que dicho sea de paso, suena muy bien y pesa lo mismo o menos que un .mp3 de buena calidad! :guitar:)
Ya como archivo local Rhythmbox lo reprodujo sin problemas.
En fin, sin opciones no me quedo. Podría quemar nuevos CD con este formato(ya que estoy medio corto de rígido) pero el problema en si no se soluciona, una lástima.

El lsmod:
[B][I]cesar@cesar-desktop:~$ lsmod
Module                 Size  Used by
isofs                  29250  0 
udf                    78785  0 
crc_itu_t               1371  1 udf
binfmt_misc             6587  1 
snd_intel8x0           25588  4 
snd_ac97_codec        100646  1 snd_intel8x0
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
ac97_bus                1002  1 snd_ac97_codec
bitblit                 4707  1 fbcon
snd_pcm_oss            35308  0 
softcursor              1189  1 bitblit
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
i915                  282354  3 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
drm_kms_helper         29297  1 i915
ppdev                   5259  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             25962  1 
drm                   162471  4 i915,drm_kms_helper
intel_agp              24177  2 i915
soundcore               6620  1 snd
i2c_algo_bit            5028  1 i915
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
lp                      7028  0 
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
shpchp                 28820  0 
psmouse                63245  0 
serio_raw               3978  0 
parport                32635  3 ppdev,parport_pc,lp
8139too                18545  0 
8139cp                 16186  0 
mii                     4381  2 8139too,8139cp
floppy                 53016  0 
[/I][/B]

Según lo poco que puedo entender los modulos de driver Intel estan cargados. Aunque si alguién me ayuda a leerlo,desglosando la info se lo agradecería.
 
Dejo una copia adjunta del dmesg porque es un choclo. A este si ya no le entiendo un pomo. Disculpen que sea .odt pero el archivo en texto plano pesa mucho y no puedo ajuntarlo.

Si a alguien se le ocurre algo, soy todo oídos.
¡Muchas gracias!
Saludos.

---

