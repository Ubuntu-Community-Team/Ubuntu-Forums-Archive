---
title: "ayuda configurar Headset Bluetooth"
date: 2009-03-03
forum: Software
---

### Post by upszot on 2009-03-03
Buenas gente... estoy tratando de configurar un headset para q funcione en linux...
logro conectar el dispositivo en la maquina..cree el bluetooth pero no sale el sonido.. y ya no se q mas hacer...

alguien me puede echar un cable??
la info la obtuve de estas paginas entre otras...

[http://wiki.bluez.org/wiki/HOWTO/AudioDevices](http://wiki.bluez.org/wiki/HOWTO/AudioDevices)
[http://www.galpon.org/wiki/index.php/Auricular_Bluetooth_en_GNU/Linux](http://www.galpon.org/wiki/index.php/Auricular_Bluetooth_en_GNU/Linux)
[http://forums.overclockers.com.au/showthread.php?t=694010](http://forums.overclockers.com.au/showthread.php?t=694010)

y aca les muestro el paso a paso y como quedo... pero no escucho el audio =((

```

upszot@M1530:~$ hciconfig -a
hci0:	Type: USB
	BD Address: 00:22:69:XX:XX:XX ACL MTU: 1017:8 SCO MTU: 64:8
	UP RUNNING PSCAN ISCAN 
	RX bytes:975 acl:0 sco:0 events:28 errors:0
	TX bytes:363 acl:0 sco:0 commands:28 errors:0
	Features: 0xff 0xff 0x8f 0xfe 0x9b 0xf9 0x00 0x80
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF PARK 
	Link mode: SLAVE ACCEPT 
	Name: 'M1530-0'
	Class: 0x08010c
	Service Classes: Capturing
	Device Class: Computer, Laptop
	HCI Ver: 2.0 (0x3) HCI Rev: 0x2128 LMP Ver: 2.0 (0x3) LMP Subver: 0x41d8
	Manufacturer: Broadcom Corporation (15)

upszot@M1530:~$ modprobe -l |grep snd-bt-sco
/lib/modules/2.6.24-23-generic/ubuntu/snd-bt-sco.ko
upszot@M1530:~$ hcitool scan
Scanning ...
	00:21:3C:XX:XX:XX	Jawbone

upszot@M1530:~$ btsco -v 00:21:3C:XX:XX:XX
btsco v0.42
Device is 1:0
Error: btsco open (1-0): No such device or address

upszot@M1530:~$ sudo hciconfig hci0 voice 0x0060

upszot@M1530:~$ sudo gedit ~/.asoundrc
upszot@M1530:~$ cat ~/.asoundrc
pcm.bluetooth {
  type bluetooth
  device 00:21:3C:XX:XX:XX
  profile "auto"
}

upszot@M1530:~$ sudo modprobe sco
upszot@M1530:~$ modprobe -l |grep sco
/lib/modules/2.6.24-23-generic/ubuntu/snd-bt-sco.ko
/lib/modules/2.6.24-23-generic/kernel/net/bluetooth/sco.ko

upszot@M1530:~$ pactl load-module module-alsa-sink device=bluetooth
Failure: Timeout
upszot@M1530:~$ pactl load-module module-alsa-source device=bluetooth
Failure: Module initalization failed
upszot@M1530:~$ 
upszot@M1530:~$ sudo cat /proc/asound/cards

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 19
 1 [Headset        ]: Bluetooth SCO - BT Headset
                      BT Headset 1
upszot@M1530:~$ aplay -D bluetooth -f s16_le /usr/share/sounds/login.wav
Sonando WAVE '/usr/share/sounds/login.wav' : Signed 16 bit Little Endian, Ratio 44100 Hz, Estéreo
aplay: set_params:906: Contador de canales no disponible
upszot@M1530:~$ 
```

Gracias a todos de antemano =))

Edit: Aca se ve cuando hago el btsco -v MAC que no lo puede empalmar... pero mas adelante logre empalmarlo ... cuando ejecute esto: "pactl load-module module-alsa-sink device=bluetooth"
de todas formas como les conte arriba... el sonido no sale =((

---

