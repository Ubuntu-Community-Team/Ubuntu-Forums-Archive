---
title: "Problema internet ubuntu 9.10 en la terminal"
date: 2010-02-01
forum: Software
---

### Post by sitodonosti on 2010-02-01
Hola os cuento mi pequeño problema. Resulta que quiero montarme un mediacenter, y estoy siguiendo un tutorial de Forat.info bueno ahora la duda es esta. El caso es que mi primo me ha dejado un ordenador con pentium III, he instalado ubuntu alternate pero por terminal, la placa base no tiene pa poner el rj45 y tengo dos tarjetas para internet. Una es una conceptronic 8139 y no funciona internet por hay y otra es una wifi smc. El caso es que al no tener internet no puedo instalar wireless-tools para poder configurarlo mediante wifi. 
Sabéis si hay alguna solución al respecto?ya he intentado haber si conseguía hacer funcionar la conceptronic pero no lo he conseguido(incluso hay un post en este foro escrito por mi pero nada...)
bueno un saludo y si no entendeis algo preguntar
un saludo y gracias!

---

### Post by luks911 on 2010-02-01
La cuestión, me parece, es ver cómo hacer para que funcione alguna de las placas wifi. Lo que necesités instalar desde internet para lograrlo no me parece que sea problema, ya que podés bajarlo desde otra máquina y pasarlo a esta por medio de USB o un CD.
Así que pegá las salidas de lsusb o lspci, según corresponda, de una de las placas para ver qué se puede hacer.

---

### Post by sitodonosti on 2010-02-01
lsusb:
bus 001 device 001: ID 1d6b:0001 Linux foundation 1.1 root hub
bus 002 device 001: ID 1d6b:0001 Linux foundation 1.1 root hub
lspci:
00:00.0 host bridge: intel corporation 82815 815 Chipset host Bridge and Memory controller hub (rev 02)
00:01.0 pci bridge: intel corporation 82815 815 Chipset agp Bridge (rev 02)
00:1e.0 pci bridge: intel corporation 82801 pci Bridge (rev 01)
00:1f.0 isa bridge: intel corporation 82801ba isa bridge (lpc) (rev 01)
00:1f.1 ide interface: intel corporation 82801ba ide u100 controller (rev 01)
00:1f.2 usb controller: intel corporation 82801ba/bam usb controller #1(rev 01)
usb controller: interl corpotration 82801ba/bam smbus controller
usb controller :intel corp. 82801ba/bam usb controller #1 (rev01)
multimedia audio controller: Intel corp. 82801ba/bam ac'97 audio controller (rev 01)
VGA compatible controller: nvidia corp nv11[gforce2 mx/mx 400]rev a1
[B]02:02.0 Ethernet controller: Realtek semiconductro co., ltd. rtl 8185 ieee 802.11a(b/g wireless Lan controler rev 20
02:05.0 Ethernet controller: Relatek semiconductor co., ltd trl 8139/8139c/8139c+ rev 10[/B]
esto es la salida, e creido importante poner todo lo que hace referencia a las tarjetas wifi bien los usb controller y demás llevan numeros delatne pero parecido asl usb controller(esque tengo que copiarlo a mano y puf....)
He intentado mediante softonic y sourceforge bajarme wireless-tools me lo he bajado he hecho .deb's he instalarlos pero nada, después mediante make install el  .tar.gz y tampoco funciona.

---

### Post by luks911 on 2010-02-01
En una primera búsqueda no veo problemas de soporte para esas placas en Karmic. ¿Estás usando Karmic? También podrías probar con un Live CD para descartar que el problema sea ese, digo porque no sé si la instalación Alternate te obliga a preparar en forma manual las redes. 
Lo que sí vi son algunas quejas sobre el nivel de señal de la Realtek 8185, cuya solución es usar ndiswrapper y el driver de Win, porque el driver nativo del fabricante no se compila con el último kernel. En ese caso, Ndiswrapper podés instalarlo poniendo el CD de Ubuntu como repositorio.

---

### Post by sitodonosti on 2010-02-01
Sí lo probe con un liveCD y la tarjeta wifi de smc si que funciona perfectamente, sin embargo la realtek no. El caso es que al ser mediante consola sin nada grafico estoy sin internet ya que no puedo conectarme mediante wifi, necesito wireless-tools. es el mayor problema...

---

### Post by luks911 on 2010-02-01
Por el paquete wireless-tools hay dos opciones:
1) Instalarlo desde el CD de Ubuntu, si es que viene ahí.
Para eso agregás el CD como repositorio
```
sudo apt-cdrom add  
```
Actualizás los repositorios
```
sudo apt-get update
```
Instalás
```
sudo apt-get install wireless-tools 
```
Acá[0] hay más sobre el comando apt-cdrom. Eso sí, no sé si sirve el Alternate o tenés que usar el Desktop.

2) Si no está en el CD, podés bajar el .deb de acá[1], copiarlo en un un USB o en un CD regrabable e instalarlo en dpkg.

[0] [https://help.ubuntu.com/community/AptCdrom](https://help.ubuntu.com/community/AptCdrom)
[1] [http://mirrors.kernel.org/ubuntu/pool/main/w/wireless-tools/wireless-tools_29-2ubuntu6_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/w/wireless-tools/wireless-tools_29-2ubuntu6_i386.deb)

---

### Post by sitodonosti on 2010-02-11
Hola siento haber tardado tanto encontestar pero entre universidad ire a eskiar y demás...no he tenido mucho tiempo. Bueno al lio, estado probando con el cd y me da erro:
e:el subproceso gpgv devolvió un codigo de error
w:signature verification failed for :/cdrom/dists/karmic/Release.gpg

Despues con el .deb lo he instalado pero me dice que las dependencias están incumplidas, depende de libiw29 pero que no es instalable, sabes si esto esta en el kernel?un saludo y gracias seguiré investigando por la red

---

### Post by luks911 on 2010-02-11
En cuanto al error, ¿después de qué comando te lo devuelve?
Y por la dependencia, puedes bajar este .deb[0] de libiw29, instalarlo y luego sí instalar el otro, de ese modo no vas a tener problemas de dependencias.

[0] [http://mirrors.kernel.org/ubuntu/pool/main/w/wireless-tools/libiw29_29-2ubuntu6_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/w/wireless-tools/libiw29_29-2ubuntu6_i386.deb)

---

### Post by sitodonosti on 2010-02-11
Valeeeeeeeee ya he instalado los dos he exo iwconfig y ya me lo detecta ahora necesito scanear las redes sabes de algun programa?

---

### Post by luks911 on 2010-02-11
Creo que estás sin entorno gráfico, ¿no? Si es así el comando para escanerar las redes es
```
sudo iwlist scan
```

---

### Post by sitodonosti on 2010-02-11
si estado investigando y es eso pero más bien es
sudo iwlist wlan0 scan
el caso es que me pone erro pone network is down, pongo /etc/init.d/networkmaning stop
pero al volver a escanear me sigue apareciendo el erro de network is down, que tengo que hacer up?(digo yo, no?)loque nose es qué tengo que hacer up

---

### Post by luks911 on 2010-02-11
Mmmm... no soy experto en esto, pero creo que deberías hacer

```
sudo ifconfig wlan0 up
```

También te pasó un link[0] a un tutorial sobre manejo de redes desde consola, aunque debe habaer más.

[0] [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by sitodonosti on 2010-02-11
Ya he hecho eso pero se me keda mucho tiempo con la rayita parpadeando y no hace anda se kedaasi tiempo muxooo tiempo, gracias.

---

