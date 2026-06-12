---
title: "GRUB con modo grafico"
date: 2008-05-03
forum: Software
---

### Post by Hei Ku on 2008-05-03
Alguno probo instalar el GRUB en modo grafico? Varias distros lo tienen predeterminado, y esta bueno. Mucho mejor que bootear en un modo texto. No es que reinicie mucho mi PC, pero esta bueno, y es algo que impresiona a las masas :D

Alguno lo probo? Tienen alguna recomendacion para hacer? Un how-to para instalarlo?

---

### Post by MeduZa on 2008-05-04
> **Hei Ku said:**
> Alguno probo instalar el GRUB en modo grafico? Varias distros lo tienen predeterminado, y esta bueno. Mucho mejor que bootear en un modo texto. No es que reinicie mucho mi PC, pero esta bueno, y es algo que impresiona a las masas :D

Alguno lo probo? Tienen alguna recomendacion para hacer? Un how-to para instalarlo?

es algo que demuestra superioridad, lo iba a probar pero aun no logro hacer andar el usplash xD

---

### Post by valucha on 2008-05-04
[COLOR="DarkOrchid"]JUsto venía de buscar eso... al parecer el grub-gfxboot ya no está en los repositorios :([/COLOR]

---

### Post by Mauro22 on 2008-05-04
Yo lo tengo hace rato y anda muy bien! ademas que queda muy lindo, siguiendo esto:

[http://www.elblogdemaverick.com/?p=3](http://www.elblogdemaverick.com/?p=3)


Pero cuando lo hice, tuve que cambiar esa guia.


Despues eso de grub-install a mi nunca me sirvio, el que me funciono es esto:
(pero a uds por ahi si les sirve)

> 
sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)




Otra cosa, primero intenten con el que esta en la guia:
sudo grub-install /dev/disco

para saber que disco es:
sudo fdisk -l

Hardy cambio los hd por sd y no se porque.



grub-Gfxboot
[http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb](http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb)

---

### Post by pol666 on 2008-05-04
Grub grafico te referis por ejemplo a tener una foto detras de fondo en el grub o es otra cosa que me estoy perdiendo.


osea yo tengo las mismas letritas blancas, pero con uan foto (ultra pixelada) de fondo. Podria tener algo de mejor calidad visual?, como botones graficos o una foto con mas color?

---

### Post by MeduZa on 2008-05-04
> **Mauro22 said:**
> Yo lo tengo hace rato y anda muy bien! ademas que queda muy lindo, siguiendo esto:

[http://www.elblogdemaverick.com/?p=3](http://www.elblogdemaverick.com/?p=3)


Pero cuando lo hice, tuve que cambiar esa guia.


Despues eso de grub-install a mi nunca me sirvio, el que me funciono es esto:
(pero a uds por ahi si les sirve)




Otra cosa, primero intenten con el que esta en la guia:
sudo grub-install /dev/disco

para saber que disco es:
sudo fdisk -l

Hardy cambio los hd por sd y no se porque.



grub-Gfxboot
[http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb](http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb)

normalmente linux usa hd para los discos que usan PATA y sd para los que usan SATA, al menos asi es en mi sistema.

---

### Post by Mauro22 on 2008-05-04
Mi discos son ATA y en GG eran hda1 2 3 etc, ahora son sda :S

Asi te quedario el grub (dependiendo de la imagen que pongas)
[IMG]http://www.elblogdemaverick.com/uploads/ubugrey.png[/IMG]

---

### Post by pol666 on 2008-05-04
> **Mauro22 said:**
> Mi discos son ATA y en GG eran hda1 2 3 etc, ahora son sda :S

Asi te quedario el grub (dependiendo de la imagen que pongas)
[IMG]http://www.elblogdemaverick.com/uploads/ubugrey.png[/IMG]




Definitivamente tenes otra cosa.... Tu imagen es de calidad, y las opciones estan ubicadas de otra forma.... el mio no se como sacarle una cap. :\

---

### Post by Mauro22 on 2008-05-04
Esa cap no es mia, la saque de internet

Pero te queda igual a eso.

---

### Post by Ptero-4 on 2008-05-04
Para sacarle una captura necesitarás instalar el ubuntu en un virtualbox.

---

### Post by faktorqm on 2008-05-04
Yo lo instale, y lo que me paso es que nada me tiro error cuando lo instale y el grub seguia igual... (no se rian!) estaba instalado en el synaptic y todo y habia descomprimido la imagen con los grafiquitos que a mi me gustaban todo ok y nada :( 
Grub 2 para cuando lo sacan? Salu2!

---

### Post by Mauro22 on 2008-05-04
Hiciste todos los pasos?


bajar el grub-gfxboot
remove grub
instalar grub-gfxboot
agregar a menu.lst:

gfxmenu /boot/grub/message.xxxx (lo que hayas bajado y copiado)
sudo grub-install /dev/sdX


??

Yo lo volvi a hacer por las dudas, y esta todo ok

---

### Post by faktorqm on 2008-05-05
eemmm si, hice eso y todos los pasos, pero cuando le doy grub-install y reinicio..... me tira el grub "normal". Ya me paso con 7.04 y ahora con 8.04 (con 7.10 no probe). pregunta tecnica: cuando desinstalo el grub, no hay que ponerle --purge? o desinstalarlo y reiniciar? por que no arranca sino, va no se. la verdad que estas cosas me ponen loco, hay que escribir un programa que lo haga por vos usando 3 botones y listo ... 
Me pasas la dire de donde sacaste eso? a ver si estamos haciendo los dos lo mismo? gracias y salu2!

---

### Post by Mauro22 on 2008-05-05
Mira, te lo hago bien detallado.


1) Baja el nuevo grub grafico (wget [http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb](http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb)). Pero no lo instales todavia.
2) sudo apt-get remove grub (eliminas el grub "normal", el que solo soporta texto)
3) Te vas a la carpeta donde tenes el archivo bajado en 1 y haces:[FONT=monospace] 
[/FONT]sudo dpkg -i grub-gfxboot_0.97-5_i386.deb (con esto instalas el nuevo grub que soporta graficos)
4) Al final de [este post](http://ubuntuforums.org/showthread.php?t=208855) vas a ver algo asi:

Light Green generic theme [message.gobo] ...

Esos son los distintos graficos para el grub (hay por toda la web)
Elegi uno y bajalo.
5) Ahora queda configurar el grub grafico. Para ello hacemos:
sudo fdisk -l y nos devuelve algo asi:

```

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
**/dev/sda1               1        3647    29294496   83  Linux**
/dev/sda2            3648       11428    62500882+  83  Linux
/dev/sda3           11429       11780     2827440    f  W95 Ext'd (LBA)
/dev/sda4   *       11781       19457    61665502+   b  W95 FAT32
/dev/sda5           11429       11780     2827408+  82  Linux swap / Solaris

```

En mi caso me corresponde sda1, ahi dice que es la particion linux y por el tamaño yo se que es el sistema y no la /home.

Entonces, sabiendo eso:
sudo grub-install /dev/sda1 (en mi caso)

6) vamos a la carpeta donde tenemos el **message.xxxx** que bajamos en el punto 4 y lo copiamos a /boot/grub
sudo cp **mesaage.xxxx** /boot/grub/

editamos el grub:
sudo gedit /boot/grub/menu.lst

y agregamos al comienzo:
gfxmenu /boot/grub/**message.xxxxx**


Donde **message.xxxxx***es el archivo que bajaron.*

7) Reinciar!





:lolflag:

---

### Post by MeduZa on 2008-05-05
> **Ptero-4 said:**
> Para sacarle una captura necesitarás instalar el ubuntu en un virtualbox.

o una camara de fotos ;)

---

### Post by faktorqm on 2008-05-05
AAAAAAHHHHHHHHHHHHHHHHHHHHHHHHHHHHhh
estaba poniendo mal el grub-install.......... soy un banana..........
bueno ok, perfectamente me arranco siguiendo tu how to, muy explicativo por cierto.

Permitime pasar en limpio tu how to:

1) Bajar el nuevo grub grafico mediante el comando:

```
wget http://quasarfreak.googlepages.com/grub-gfxboot_0.97-5_i386.deb
```

Pero no instalarlo todavia.

2) Eliminar el Grub que teniamos hasta ahora con:

```
sudo apt-get remove grub
``` 

3) Instalamos el archivo que descargamos en el paso 1 (el nuevo grub con graficos):

```
sudo dpkg -i grub-gfxboot_0.97-5_i386.deb
``` 

4) Debemos descargar ahora un tema para nuestro nuevo grub, aqui algunos links: 

Light Green generic theme [message.gobo] | [Link](http://ubuntuforums.org/showpost.php?p=1214274&postcount=12) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=12251&d=1152089288)
Dark Brown (Dapper look) generic theme [message.new] | [Link](http://ubuntuforums.org/showpost.php?p=1239724&postcount=55) | [Screenshot](http://www.ubuntuforums.org/attachment.php?attachmentid=12549&d=1152600544)
Dark grey ubuntu theme [message.ubugrey] | [Link](http://ubuntuforums.org/showpost.php?p=1251236&postcount=61) | [Screenshot](http://www.ubuntuforums.org/attachment.php?attachmentid=12875&d=1153129717)
Medium brown ubuntu theme [message.ububrown] | [Link](http://ubuntuforums.org/showpost.php?p=1252317&postcount=63) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=12874&d=1153129657)
Light orange ubuntu theme [message.ubu] | [Link](http://ubuntuforums.org/showpost.php?p=1254642&postcount=64) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=12873&d=1153128852)
Red ubuntu theme [message.new] | [Link](http://ubuntuforums.org/showpost.php?p=1265601&postcount=65) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=12870&d=1153128852)
Fuzzy blue and black ubuntu theme [message.bluspash] | [Link](http://ubuntuforums.org/showpost.php?p=1272301&postcount=71) | [Screenshot](http://www.ubuntuforums.org/attachment.php?attachmentid=12947&d=1153265746)
White / Grey Snowish generic theme [message.snow] | [Link](http://ubuntuforums.org/showpost.php?p=1292317&postcount=84) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=13161&d=1153730506)
Linspire-style blue kubuntu theme [message.kubu] | [Link](http://ubuntuforums.org/showpost.php?p=1294120&postcount=86) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=13176&d=1153757390)
Old- Grub style dark blue and light blue [message.kubu] | [Link](http://mitglied.lycos.de/atoth/ubuntuusers/message.napo) | [Screenshot ](http://mitglied.lycos.de/atoth/ubuntuusers/screenshot_message_napo.png)
Light blue / grey Xubuntu theme [message.xubu] | [Link](http://ubuntuforums.org/showpost.php?p=1297486&postcount=97) | [Screenshot](http://ubuntuforums.org/attachment.php?attachmentid=13211&d=1153828350)

De todas maneras hay por toda la web, hay que elegir uno y descargarlo.
Estos links tienen un archivo con la denominacion message.XXXX donde XXXX puede ser cualquier cosa. En algunos estan comprimidos, por lo tanto se deben descomprimir antes de enviarlos a la carpeta como veremos mas adelante.

Ejemplo: 

El red ubuntu theme es message.new.tar.gz.

El archivo que descomprimido es message.new es el que vamos a usar.

Elegir estos u otros que nos queden mas a gusto y descargarlos.

5) Ahora queda configurar el grub grafico. Para ello hacemos:
```
sudo fdisk -l
```
y nos devuelve algo asi:

```

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1        3647    29294496   83  Linux
/dev/sda2            3648       11428    62500882+  83  Linux
/dev/sda3           11429       11780     2827440    f  W95 Ext'd (LBA)
/dev/sda4   *       11781       19457    61665502+   b  W95 FAT32
/dev/sda5           11429       11780     2827408+  82  Linux swap / Solaris

```

En mi caso me corresponde sda1, es la particion donde tengo el sistema de linux instalado. por lo tanto el comando a ejecutar será:

```
sudo grub-install /dev/sda1
``` 

RECORDAR QUE ESTE COMANDO SIRVE SOLO PARA ESTE CASO.

6) Copiar el message.xxxx que bajamos en el punto 4 y lo copiamos a la ubicacion correspondiente con:

```
sudo cp mesaage.xxxx /boot/grub/
```

EJEMPLO: (siguiendo con el anterior) 

```
sudo cp mesaage.new /boot/grub/
```

7) Editamos el archivo de configuración del nuevo grub:

```
sudo gedit /boot/grub/menu.lst
```

y agregamos al comienzo del archivo la linea:

```
gfxmenu /boot/grub/message.xxxx
```

Donde message.xxxx es el archivo que copiamos en el punto 6.

EJEMPLO: (siguiendo con el anterior) 

```
gfxmenu /boot/grub/message.new
```

Guardamos el archivo, REINICIAMOS y listo!!

Por supuesto gracias a PingunZ, Mauro22 y a QuasarFreak.
Espero que les haya servido tanto como a mi. Salu2!!

---

### Post by Mauro22 on 2008-05-05
Me alegro que te haya servido y que disfrutes de tu nuevo GRUB!

---

### Post by guillermolisi on 2009-12-17
> **hanamishi said:**
> Hola!

He instalado sin problema el gfxboot pero me sale ahora antes del splash screen y en el logout todo el código de arranque y apagado. ¿Hay alguna forma de mantener el logo de ubunut que salía por defecto con el GRUB2?

Gracias de antemano, un saludo ^_^
Como el thread original (del 2008) habla sobre Grub y este post hace referencia a Grub2, lo que no es poca cosa, lo muevo abriendo un [nuevo thread]("http://ubuntuforums.org/showthread.php?t=1357527") en Software.

---

