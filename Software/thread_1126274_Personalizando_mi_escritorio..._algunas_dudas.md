---
title: "Personalizando mi escritorio... algunas dudas"
date: 2009-04-15
forum: Software
---

### Post by WooS on 2009-04-15
Hola gentes tengo algunas dudas.La primera es q pasa con los efectos de escritorio q no se xq pero no los puedo activar... cdo voy a sistema>preferencias>apariencia y quiero poner los efectos visuales en extra o normal m sale "No se han podido activar los efectos de escritorio"
La otra duda surge de ver el post donde todos mustra sus escritorios...yo vi q muchos tenian unas barras a la derecha con info del sistema y no se como hacer para tenerlos asi como uds pero instale uno desde la pestaña "añadir y quitar" que se llama MGM System Monitor y ademas de ser feo esteticamente no puedo ponerlo en la parte derecha de la pantalla sino que es como una ventana que tengo abierta...
Espero q hayan podido entender cual es mi situacion sino preg q intento explicar de otra manera...
Saludos!

---

### Post by guillermolisi on 2009-04-15
> **WooS said:**
> Hola gentes tengo algunas dudas.La primera es q pasa con los efectos de escritorio q no se xq pero no los puedo activar... cdo voy a sistema>preferencias>apariencia y quiero poner los efectos visuales en extra o normal m sale "No se han podido activar los efectos de escritorio"
La otra duda surge de ver el post donde todos mustra sus escritorios...yo vi q muchos tenian unas barras a la derecha con info del sistema y no se como hacer para tenerlos asi como uds pero instale uno desde la pestaña "añadir y quitar" que se llama MGM System Monitor y ademas de ser feo esteticamente no puedo ponerlo en la parte derecha de la pantalla sino que es como una ventana que tengo abierta...
Espero q hayan podido entender cual es mi situacion sino preg q intento explicar de otra manera...
Saludos!

Para que funcionen los efectos de escritorio tenes que tener aceleracion grafica activada y esto lo logras solo si tu tarjeta de video soporta esa funcionalidad.

Respecto del resto, si lees el thread que mencionas donde muestran los escritorios vas a ver cuantas alternativas hay para usar applets en Gnome y en KDE.

---

### Post by WooS on 2009-04-15
Si estuve mirando pero como soy nuevo solamente encontre una pagina en la cual m enseño a instalar iconos bordes d ventana y punteros (q es bastante facil)
No entiendo muy bien q necesito tener para las barras laterales de informacion del sistema y para q la barra d abajo se vea con los iconos

---

### Post by staar on 2009-04-15
a ver, te explico un poco, la info del sistema en el escritorio la podés poner de dos maneras, bastante diferentes...

tenés los screenlets (busca el paquete 'screenlets' en Synaptic, e instalalo) que son como los gadgets de Vista, solo que mejores :-P, tenés un monton por defecto, para mostrar lo que estas escuchando, para ver el uso de disco, para mostrar fotos, etc... (cuando los instales, te va a aparecer el manager en Aplicaciones -> Accesorios -> Screenlets ;-) )

la otra es con conky (en los screenshots lo reconoces por que es un 'texto' sobre el fondo de pantalla, conky no puede mostrar imagenes), que requiere la modificación de un archivo de texto, el .conkyrc, para poder configurarlo, aunque eso permite mucha mayor libertad, por ahora que estas empezando te recomiendo los screenlets ya que son mas fáciles...

las barras de abajo con iconos, son los docks, están el cairo-dock, el kiba, AWN, Wbar, y un monton más, el mas bonito (para mi gusto) y fácil de usar, es el AWN (en Synaptic buscalo como 'avant-window-navigator')...

para tener los efectos de escritorio (y para usar AWN), tenés que tener activada la aceleración gráfica de tu tarjeta de video (en caso de que la soporte), y para eso tenes que tener instalados y activados los drivers de la misma, fijate en Sistema -> Administración -> Controladores de hardware

saludos

---

### Post by WooS on 2009-04-15
bueno muchas gracias staar por tu paciencia con la gente nueva e ingorante... ya m baje el awn pero m dice algo como q tengo q tener el compiz abierto o personalizado pero nisiquiera se donde esta...
el screenlets m anda espectacular solamente quiero saber como le pones un theme a el sysmonitor xq baje el sysmoniorplus pero se cuelga =(
Cdo voy a controladores d hardware no pasa nada...en ninguna de las dos ventanas q muestra hay nada escrito =S
Bueno desde ya muchas gracias por tu bolilla =)
Saludos

---

### Post by staar on 2009-04-15
mmm... sin aceleración gráfica no vas a poder hacer mucho, tenés que arreglar eso...

postea acá la salida de poner el comando ```
lspci
``` en una terminal, asi podemos saber el modelo exacto de tu placa gráfica...

saludos

---

### Post by guisheca on 2009-04-16
Como una pequeña contribución al tema digo que AWN y algunas aplicaciones mas pueden funcionar sin los efectos de escritorio ([compiz]("http://es.wikipedia.org/wiki/Compiz")) activando la composición de ventanas de Metacity (composición de ventanas se llama básicamente a contar con transparencias y sombras en las ventanas y paneles). Podés hacer esto último siguiendo las instrucciones de esta guía.
Saludos.


PD: posteá la devolución del comando que te ponen mas arriba para que te puedan ayudar, lo mío fué un pequeño aporte en caso de que tu placa no esté soportada en GNU/Linux.

---

### Post by WooS on 2009-04-16
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
04:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)


Eso es lo q m tiro el (o la no se como se dice) terminal...
Lo q no vi fue el link d la guia para ver si puedo actibar la barra igual.Si podes pasamelo y voy leyendo
Saludos y muchas gracias

---

### Post by guisheca on 2009-04-16
Ups!!! me olvidé de poner el link!!
Te dejo dos por las dudas:
[http://dmolinap.blogspot.com/2008/07/metacity-con-composite.html](http://dmolinap.blogspot.com/2008/07/metacity-con-composite.html)
[http://ubuntuland.wordpress.com/2008/06/03/activar-composite-por-metacity/](http://ubuntuland.wordpress.com/2008/06/03/activar-composite-por-metacity/)

Por otra parte te cuento que tenés una placa de video VIA chrome 9 HC, lamentablemente esa placa no posee soporte 3D en GNU/Linux, al menos hasta donde yo se.
Igual esperemos a ver si alguien comenta algo mas.
Saludos.

---

### Post by WooS on 2009-04-16
buenisimo pude hacer andar el AWN era una d las referencias sobre ubuntu q tenia antes de instalarlo asi q voy a aprender a usarlo hasta donde se pueda...sos un grande date cuenta q hiciste feliz a alguien...jejeje
Saludos!


PD: mi problema ahora es q puse el conky con una config q estaba en gnome look pero en vez d salirme los iconos del disco duro o esos m sale la letra "u" por ejemplo q es donde tendria q aparecerme el simbolo d ubuntu
Donde puedo ver algo al respecto para ver si lo puedo configurar
PD2: el screenlets lo borre xq el conky m gusto mucho mas asi q la preg q hecho no hace falta q m la contesten =)

---

### Post by staar on 2009-04-16
te sale una letra u porque no instalaste la fuente necesaria, fijate en el .conkyrc, en esa linea, la fuente que pide, si lo bajaste de gnome-look generalmente te trae las fuentes, tenes que copiarlas a la carpeta .fonts de tu home ;-) (fijate que tiene un punto delante el nombre, eso significa que esta oculta, hace Ctrl + H en el Nautilus para ver los archivos ocultos)

saludos

---

### Post by WooS on 2009-04-16
Bueno ahora si puedo decir q tenes la rta a todas las preguntas...jajaja
Es verdad tnia q instalar las fonts y listo lo hice en menos d 2 seg
La verdad q no se como hagradecer por la explicacion y la atencion tuya y d todos... 
Saludos!!!

---

### Post by andy_91 on 2009-04-17
> tenes que instalar las fuentes en la caperta /home/user/.fonts

**aclaracion:** cambia user por tu nombre de usuario

las fuentes nesesarias deben estar incluidas en el paquete que descargaste

jeje no vi que habia mas, que mal que estoy hoy, definitivamente hoy no es mi dia

---

