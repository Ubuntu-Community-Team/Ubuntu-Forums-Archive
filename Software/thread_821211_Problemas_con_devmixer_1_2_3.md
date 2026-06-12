---
title: "Problemas con /dev/mixer 1 2 3"
date: 2008-06-07
forum: Software
---

### Post by anarko on 2008-06-07
Hola, les cuento por si alguien tiene una idea, tengo un problema con los mixer que cada vez que reinicio la PC cambian de lugar, osea se mesclan /dev/mixer /dev/mixer1 /dev/mixer2 /dev/mixer3 que corresponden a las 4 placas de sonido que tengo y eso me vuelve loco poque yo configuro por ejemplo el tvtime para que maneje el volumen por el /dev/mixer2 y cuando reinicio ese device ya no es el que yo quiero.
En debian me pasaba lo mismo con las placas de red y los eth0 eth1 eth2 cada vez que reiniciaba se sumaba 1 a las eth y lo arreglaba desde las reglas del udev, pero me fije las del alsa y no las entendi, alguien sabe como fijar que device queda en que mixer

---

### Post by anarko on 2008-06-13
Loco a nadie le paso esto, tan rara es mi computadora?

---

### Post by faktorqm on 2008-06-13
Creo que si :P:P

postea la salida de estos dos comandos

```
cat /proc/asound/cards
```

```
cat /proc/asound/oss/sndstat
```

Acá [http://www.radscan.com/nas/nas-ml/msg01449.html](http://www.radscan.com/nas/nas-ml/msg01449.html) tira un cable. 
Acá [http://es.tldp.org/COMO-INSFLUG/COMOs/Sonido-COMO/Sonido-COMO-6.html](http://es.tldp.org/COMO-INSFLUG/COMOs/Sonido-COMO/Sonido-COMO-6.html) explica muchas cosas, al parecer interresantes. Leelas ;)

Salu2!

---

