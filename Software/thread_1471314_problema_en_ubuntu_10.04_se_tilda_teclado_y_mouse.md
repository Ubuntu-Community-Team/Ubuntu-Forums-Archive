---
title: "problema en ubuntu 10.04 se tilda teclado y mouse"
date: 2010-05-03
forum: Software
---

### Post by mama21mama on 2010-05-03
Hola,

hace días que me estoy rebanando las neuronas y no puedo explicar que es.
Le eche la culpa la driver libre [nouveau]("http://puttext.com/fa") pense que armaba mal el xorg. Luego instalando el driver privativo V195.36.24 de nvidia me paso lo mismo deja de responder teclado y mouse luego del gdm.

Probe uno por uno tanto los dos driver con sumo cuidado con un mismo xorg generico y dejaba de responder tanto en uno como el otro.

probe puppy, probe karmic y todo anda bien. mas extraño aun...

Mas sorpresa me dio cuando descarte estos dos y puse vesa; tambien dejaba de responder el teclado y mosue luego del gdm. :s

Actualmente entre en gnome modo seguro  para escribir este post.

Ya no se que mas probar; si alguien me puede orientar a ver que esta pasando que dejan de responder teclado y mouse le estare agradecido.


Saludos

---

### Post by varunendra on 2010-05-03
> **mama21mama said:**
> Hola,

hace días que me estoy rebanando las neuronas y no puedo explicar que es.
Le eche la culpa la driver libre [nouveau]("http://puttext.com/fa") pense que armaba mal el xorg. Luego instalando el driver privativo V195.36.24 de nvidia me paso lo mismo deja de responder teclado y mouse luego del gdm.

Probe uno por uno tanto los dos driver con sumo cuidado con un mismo xorg generico y dejaba de responder tanto en uno como el otro.

probe puppy, probe karmic y todo anda bien. mas extraño aun...

Mas sorpresa me dio cuando descarte estos dos y puse vesa; tambien dejaba de responder el teclado y mosue luego del gdm. :s

Actualmente entre en gnome modo seguro  para escribir este post.

Ya no se que mas probar; si alguien me puede orientar a ver que esta pasando que dejan de responder teclado y mouse le estare agradecido.


Saludos
English translation of your post: > 10.04  ubuntu problem is labeled keyboard and mouse
Hello,

some days I'm  slicing neurons and that is I can not explain.
I blame the free nouveau driver arming poorly thought xorg. [COLOR=#000000]After installing the proprietary driver from nvidia V195.36.24 I  spend the same stops responding keyboard and mouse after gdm.

[/COLOR]Probe one by one as the two most careful driver with  the same xorg generic and failed to respond both in one or the other.

puppy probe,  probe karmic and all is well. stranger still ...

But I was  surprised when discarding these two and put vesa, also the keyboard  stopped responding and Mosuo after gdm. : S

Currently into  gnome safe mode to write this post.

You do not know  what else to try, and if anyone can advise me to see what's going to  stop responding keyboard and mouse you'll be grateful. (you'll be grateful:confused:

Anyway, that's google translation. Hope it helps more people understand your problem:D

---

### Post by mama21mama on 2010-05-03
Mas raro aun (me estoy volviendo loco); tengo dos usuario mas y probando recién entro a esos usuarios sin problemas pero el mio debo entrar con gnome modo seguro.

¬¬

---

### Post by el_baby on 2010-05-03
> **mama21mama said:**
> Mas raro aun (me estoy volviendo loco); tengo dos usuario mas y probando recién entro a esos usuarios sin problemas pero el mio debo entrar con gnome modo seguro.


Se me ocurre que si con los otros usuarios entrás OK, entonces debe haber algún problema en la configuración de gnome de tu usuario en particular.

Yo no sé nada de gnome, pero quizás si lo planteás por ese barrio alguien que sepa más te puede ayudar.

Una variante para ir saliendo "mal y pronto" sería crearte un nuevo directorio para tu usuario así empezás "virgen" y vas configurando las cosas de a poco.

La forma más rápida de hacer esto es en una consola de texto a lo bestia.

Suponiendo que tu usuario se llama "mama" y el home está en /home/mama y, además, tu usuario tiene permisos de administración (es decir, podés hacer "sudo"), lo que tendrías que hacer es lo siguiente:

Apretá <CTRL><ALT>F4. Eso te va a llevar a una de las 6 consolas virtuales de texto (la cuarta).

Allí te logueás con tu usuario y clave y vas a ver la pantallita negra con un prompt.

Como la carpeta en la que estás parado la vas a mover, tenés que pararte en /home para hacerlo.

Yo lo haría con estos comandos: (si el usuario no se llama "mama", cambiá "mama" por el nombre de usuario en la segunda línea)
```
cd /home
USUARIO=mama
sudo mv -v ${USUARIO} ${USUARIO}.VIEJO.NOANDA
sudo mkdir -v ${USUARIO}
sudo chown -v ${USUARIO}:${USUARIO} ${USUARIO}
cd ${USUARIO}
ln -sv ../${USUARIO}.VIEJO.NOANDA HOME_VIEJO
cp -v ../${USUARIO}.VIEJO.NOANDA/.profile .
cp -v ../${USUARIO}.VIEJO.NOANDA/.bashrc .
cp -v ../${USUARIO}.VIEJO.NOANDA/.bash_logout
for ARCHIVO in .profile .bashrc .bash_logout .profile ; do
  if [ -f ../${USUARIO}.VIEJO.NOANDA/${ARCHIVO} ]
    cp -v ../${USUARIO}.VIEJO.NOANDA/${ARCHIVO} .
  fi
done

for CARPETA in Desktop Documents Downloads Music Pictures Public Templates ; do
  if [ -d ../${USUARIO}.VIEJO.NOANDA/${CARPETA} ]
    mv -v ../${USUARIO}.VIEJO.NOANDA/${CARPETA} .
  fi
done

```
Eso debería dejarte un usuario sin configuraciones en particular pero con las carpetas "default" copiadas de tu usuario viejo. A su vez te va a dejar una "pseudo-carpeta" (un link simbólico) que apunta a donde dejamos todo lo que tenías antes. Eso lo podés navegar con Nautilus e ir viendo cada cosa que querés copiar o mover a tu nueva carpeta home.

---

### Post by mama21mama on 2010-05-04
Hola,

primero gracias por responder; acabo de confirmar que también los demás usuarios se les tilda teclado y mouse. en modo normal o modo "gnome seguro".

pero descubrí que estos problemas ocurren con el kernel 2.6.32.21 pero ahora ando con el 2.6.31.21 y todo marcha bien :s


si descubro como [hacer andar las tty  ctrl+altf1]("http://www.nosinmiubuntu.com/2010/05/solucion-para-ver-plymouth.html") así instalo el driver nvidia seria bueno.


Saludos

---

### Post by el_baby on 2010-05-04
> **mama21mama said:**
> con el kernel 2.6.32.21 pero ahora ando con el 2.6.32.21 y todo marcha bien :s


ehhhh... ¿el que no anda es 2.6.32.21 pero el que sí anda es 2.6.32.21? ¿¿¿??? :-D

---

### Post by mama21mama on 2010-05-05
Hola, ahora ando con kernel 2.6.32.22; cuando reinicie el pc cuento como me fue; ademas habilite paquetes no publicados en synaptic y se me actualizo un poco, 70mb aproximado de cosas nuevas incluido kernel.

---

### Post by mama21mama on 2010-05-05
Hola,

marcelo_fdz en el irc me dio [algo interesante]("http://markmail.org/message/5qlncjrb7rbjbwbh"). de List: org.freedesktop.lists.**xorg**.

---

### Post by dozer777 on 2010-05-12
Hola amigos de  argentina y todos lados recurro al foro porque no me quedan mas opciones, como fiel amante de linux y sobretodo de Ubuntu me vi en la responsabilidad de bajar la nueva version.Cuando intento instalarlo por primera vez ya me sale un cartel de error como que no se podia instalar e inicia el live cd y ahi me da la opcion para instalar, luego de un rato de instalacion logro acceder al escritorio, teniendo instalado perfectamente la nueva version, pero despues de un rato se cuelga, no funciona nada, ni teclado ni mouse, ni nada, no se que corno pasa pero me esta bolando la peluca esto. Quiero saber si tienen conocimiento de algun bug que se haya conocido desde la pagina official o algo. Saludos amigos

---

### Post by biale on 2010-05-13
Si "googleas" en ingles te vas a encontrar que es un problema que esta afectando a bastante gente que tiene placas de video Nvidia.

Yo tome la decisión provisoria de seguir con Karmic un tiempo mas.

---

### Post by mama21mama on 2010-08-28
Hola,

antes de hacer el upgrade por 2º vez.

Tengo la iso de ubuntu-10.04.1-alternate-i386 quisiera saber si tendré el mismo problema o no; que opinan?

> mama@zeusa:~$ lspci
00:00.0 Host bridge: nVidia Corporation Device 07c3 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.3 Co-processor: nVidia Corporation MCP73 Co-processor (rev a2)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i USB (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP73 IDE (rev a2)
**00:10.0 VGA compatible controller: nVidia Corporation C73 [GeForce 7050 / nForce 610i] (rev a2)**
01:07.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)


Saludos

Hoy probé la 10.04.1 en mi micro sd o sea usb-live persistente. Comparo con la 10.04 que esta la 1º no arrancaba ni la x, se tildaba, esta 10.04.1 no hace eso. Luego probare de upgradear.

---

### Post by mama21mama on 2010-08-30
Sigue el problema en ubuntu 10.04.1 - [reporte el bug ]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/626925")[http://w2t.us/l1](http://w2t.us/l1)

---

