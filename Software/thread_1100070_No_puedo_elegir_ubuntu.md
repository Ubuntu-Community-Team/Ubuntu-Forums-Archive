---
title: "No puedo elegir ubuntu"
date: 2009-03-18
forum: Software
---

### Post by ADICTOALMAXIMO on 2009-03-18
Bueno muchachachos

tengo el siguiente problema

habia instalado windows y linux (en  el  mismo pc,habia instaslado windows primero)

y cuando arrancaba el pc me daba la opcion para elegir con que s.o iva a iniciar.

Tuve un problema con windows formatie y reinstale windows en la particion que estaba.

Pero ahora cuando inicia no me da para elegir con que s.o quiero iniciar

simplemente inicia con windows.

Saludos y gracias

---

### Post by guillermolisi on 2009-03-18
> **ADICTOALMAXIMO said:**
> Bueno muchachachos

tengo el siguiente problema

habia instalado windows y linux (en  el  mismo pc,habia instaslado windows primero)

y cuando arrancaba el pc me daba la opcion para elegir con que s.o iva a iniciar.

Tuve un problema con windows formatie y reinstale windows en la particion que estaba.

Pero ahora cuando inicia no me da para elegir con que s.o quiero iniciar

simplemente inicia con windows.

Saludos y gracias
Es como haber instalado Win despues de Ubuntu: Windows borro la informacion que tenia del dual boot que esta en el MBR del disco.

Tres opciones que se me ocurren ahora son:

[LIST]
[*]Reinstalas Ubuntu (con esto se regenera el MBR)
[*]Rehaces la informacion del MBR con algun utilitario tipo SuperGrub o similar.
[*]Dejas de usar Windows para que no te vuelva a pasar :D
[/LIST]

---

### Post by ADICTOALMAXIMO on 2009-03-18
Lo que me temia

creo que voy a reinstalar linux o sino si alguien me dijiera algo mas acerca de la segunda opcion 

y no puedo dejar windows ya que no puedo jugar cs 1.6 con sxe en linux solo lo uso para eso para jugar a ese adicto juego

saludos y gracias maestro

---

### Post by pablo.s on 2009-03-18
> **ADICTOALMAXIMO said:**
> Lo que me temia

creo que voy a reinstalar linux o sino si alguien me dijiera algo mas acerca de la segunda opcion 

y no puedo dejar windows ya que no puedo jugar cs 1.6 con sxe en linux solo lo uso para eso para jugar a ese adicto juego

saludos y gracias maestro

Podés hacer lo siguiente:

1) Colocá en la BIOS para que arranque primero por CD-ROM
2) Poné el CD de instalación de Ubuntu (el desktop, no el alternate)
3) Esperá que cargue el escritorio
4)Abrite una terminal y tipeá lo siguiente:
                                                                                   **sudo grub**

5)Te aparece el prompt de grub. Ahi tipeas:
                                                                                    ** find /boot/grub/stage1** 

6) Fijate que te sale y tipea (aca pongo el ejemplo y vos lo cambias porque no se que te va a salir)
                        [COLOR=Red][FONT=monospace][/FONT]grub>[/COLOR]** root (hdX,Y)**  X e Y puede ser por ejemplo hd0,1 ó hd1,0
[COLOR=Red]                        lo que está en rojo no lo escribas[/COLOR]
7) Ahora tipeas para instalar grub en la MBR:
                                                                                        [COLOR=Red]grub>[/COLOR][B] setup (hd0)

[/B]8)Y salis de grub con: [COLOR=Red]grub>[/COLOR] [B]quit

[/B]Espero que lo puedas rescatar**. **Saludos

---

### Post by rober-mpp on 2009-03-19
La gente de la distribucion tuquito armo una guia con varias formas de solucionar la sobreescritura del mbr por parte de windows.

Te dejo el link:

[http://tuquito.org.ar/tukipedia/index.php?title=Reinstalar_el_menu_de_arranque_(GRUB)](http://tuquito.org.ar/tukipedia/index.php?title=Reinstalar_el_menu_de_arranque_(GRUB))

Saludos

---

### Post by pol666 on 2009-03-19
super grub disk.

---

### Post by ADICTOALMAXIMO on 2009-03-20
Muchas gracias 

chabones

saludos

---

