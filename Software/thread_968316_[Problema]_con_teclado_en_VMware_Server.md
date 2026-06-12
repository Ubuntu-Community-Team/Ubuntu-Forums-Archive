---
title: "[Problema] con teclado en VMware Server"
date: 2008-11-02
forum: Software
---

### Post by emancu on 2008-11-02
Hola denuevo, acabo de comentar los problemas que tuve con mi actualizacion de Intrepid Ibex en [este post]("http://ubuntuforums.org/showthread.php?t=968297") y me olvide de comentar otro problema bastante molesto, pero no edite el post porque me parece que tienen que estar separados.

Instale el VMWare server en Ubuntu 8.10 32bits y levante una VM que tenia guardada desde mi sistema anterior y andaba bien.

La VM es un Oracle Enterprise Linux 4, y basicamente el problema es que las teclas del teclado estan desordenadas.

Si yo toco la flechita para arriba, saca un print screen, si toco el altgr toca Enter, si toco la flecha izq  es tocar Altgr y si toco la flecha para abajo, es como tocar el boton pausa.

Todo esto lo vi con el layout de teclado, cuando apretaba una tecla el layout me decia cual era y vi que eran cualquier cosa!!!

Intente cambiarle el idioma la distribucion de teclado y todo lo que estaba en mi alcance y no logre nada :(, alguien sabe que puede ser?

es algo muy raro..

gracias!

---

### Post by mhoyos on 2008-12-23
hola...

tambien me paso... :(

es un bug( [https://bugs.launchpad.net/bugs/195982](https://bugs.launchpad.net/bugs/195982) ) y esta la manera de solucionarlo, desde la pagina de vmware ( [http://communities.vmware.com/thread/177133](http://communities.vmware.com/thread/177133) )

para resumir el problema, deberas crear un archivo con el nombre config dentro del directorio oculto con le nombre vmware dentro de tu home, con el siguiente contenido:

```
xkeymap.keycode.108 = 0x138 # Alt_R
xkeymap.keycode.106 = 0x135 # KP_Divide
xkeymap.keycode.104 = 0x11c # KP_Enter
xkeymap.keycode.111 = 0x148 # Up
xkeymap.keycode.116 = 0x150 # Down
xkeymap.keycode.113 = 0x14b # Left
xkeymap.keycode.114 = 0x14d # Right
xkeymap.keycode.105 = 0x11d # Control_R
xkeymap.keycode.118 = 0x152 # Insert
xkeymap.keycode.119 = 0x153 # Delete
xkeymap.keycode.110 = 0x147 # Home
xkeymap.keycode.115 = 0x14f # End
xkeymap.keycode.112 = 0x149 # Prior
xkeymap.keycode.117 = 0x151 # Next
xkeymap.keycode.78 = 0x46 # Scroll_Lock
xkeymap.keycode.127 = 0x100 # Pause
xkeymap.keycode.133 = 0x15b # Meta_L
xkeymap.keycode.134 = 0x15c # Meta_R
xkeymap.keycode.135 = 0x15d # Menu
```

y luego inicias nuevamente el vmware, y problema solucionado..

espero te sirva..

salu2

---

