---
title: "Wolfenstein: Enemy Territory"
date: 2009-05-01
forum: Software
---

### Post by DrKenobi on 2009-05-01
Termine de instalar el Wolfenstein: Enemy Territory y cuando lo arranco en el terminal me tira el siguiente error y nunca abre el juego. ¡Alguna idea?

joaquin@compaq:~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/joaquin/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
X Error of failed request: BadMatch (invalid parameter attributes)
  Major opcode of failed request: 1
  Minor opcode of failed request: 0
  Serial number of failed request: 41
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 18
  Minor opcode of failed request: 0
  Serial number of failed request: 42
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 18
  Minor opcode of failed request: 0
  Serial number of failed request: 43
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 8
  Minor opcode of failed request: 0
  Serial number of failed request: 44
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 12
  Minor opcode of failed request: 0
  Serial number of failed request: 45
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 18
  Minor opcode of failed request: 0
  Serial number of failed request: 48
X Error of failed request: BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request: 136
  Minor opcode of failed request: 7
  Serial number of failed request: 53
X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request: 154
  Minor opcode of failed request: 26
  Serial number of failed request: 53
Received signal 11, exiting...
Segmentation fault
joaquin@compaq:~$

---

### Post by faktorqm on 2009-05-04
otros juegos te andan? parace ser que tenes mal configurado el xorg.conf pero no logro ver exactamente cual puede ser la linea que te falte. postealo asi lo vemos y de paso, lo bajaste de la pagina oficial? 32 o 64 bits? salu2!

---

### Post by DrKenobi on 2009-05-05
me andan otros juegos. El open arena, que es similar al wolfenstein me anda perfecto. Lo baje de la pagina oficial. 32 bits.
Que queres que postee?
gracias

---

### Post by faktorqm on 2009-05-05
el xorg.conf por que capaz te esta faltando algo y la salida del openarena o del q3 (si mal no recuerdo tienen todos el mismo motor) salu2!

---

### Post by pablo.s on 2009-05-05
Bueno, yo no quería intervenir,
pero me da la impresión que la
versión de OpenGL que usa el
juego este es bastante veterana
y por eso no la trabaja bien esta
versión de Xorg. Personalmente
buscaría alguna versión actualizada
del juego o algún parche.

Si se fijan en los errores les está
marcando varios
**Serial number of failed request: 41**
y sucesivos, mas especificamente
**Bad Window**, **Bad Drawable** y **Bad Value**
que son los problemitas que digo.

---

### Post by Interiano on 2010-02-07
Hola les agradeceria si alguien me pudiera ayudas es que yo acabo de descargar ese juego de Wolfenstein - Enemy Territory ademas le instale dos parches la version 1.6 y la 2.6 pero siempre al abrirlo me tira este error al final: GLW_StartOpenGL() - could not load OpenGL subsystem. en español el error dice: GLW_StartOpenGL () - no ha podido cargar OpenGL subsystem



porfavor si alguien me pudiera ayudar porfavor!!!!!!!

---

### Post by juancarlospaco on 2010-02-08
Recomiendo bajarlo de GetDeb, no se si ellos lo parcharon o que pero anda...

---

