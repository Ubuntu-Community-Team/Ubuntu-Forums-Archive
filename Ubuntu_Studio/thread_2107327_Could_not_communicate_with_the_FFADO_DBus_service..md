---
title: "Could not communicate with the FFADO DBus service..."
date: 2013-01-21
forum: Ubuntu Studio
---

### Post by roughi on 2013-01-21
Hi
i'd like to make my firewire interface work, but after so many trials i ended up in total frustration. Maybe someone can help me?
I have  a netbook, upgraded to ubuntustudio 12.10, and a edirol fa-101 interface. I plug in via expresscard and the lamp on the interface indicates there is connection. I start ffado mixer:   p, li { white-space: pre-wrap; }  [COLOR=#ff0000]Could not communicate with the FFADO DBus service...[/COLOR]

Also i tried to start via QjackCtl with 'firewire' driver, but without success. What's wrong, where should i start to solve the problem??

---

### Post by jejeman on 2013-01-21
Start from here
[http://ubuntuforums.org/showthread.php?t=2098023](http://ubuntuforums.org/showthread.php?t=2098023)

---

### Post by roughi on 2013-01-22
thx jejeman, here is the output:

roughi@roughi-HP-2133:~$ ls /dev/fw*
ls: Zugriff auf /dev/fw* nicht möglich: Datei oder Verzeichnis nicht gefunden
roughi@roughi-HP-2133:~$ dmesg | grep fw
[   22.439164] psmouse serio4: synaptics: Touchpad model: 1, fw: 6.5, id: 0x1c0b1, caps: 0xa04711/0xa00000/0x0

sorry, it's german. Directory could not be found. I also checked with another cable. 

further: 
roughi@roughi-HP-2133:~$ lspci | grep FireWire
06:00.0 FireWire (IEEE 1394): Texas Instruments XIO2200A IEEE-1394a-2000 Controller (PHY/Link) (rev 01)

why isn't there a node?

---

### Post by jejeman on 2013-01-22
It is to early for the cable, you should have at least one node for the firewire card.
Check to see if the firewire modules are loaded with "lsmod" command. I doubt that.

For some reason probably modules are not loaded. See all "dmesg" output for clues. Try to load modules manualy with "modprobe".

---

### Post by roughi on 2013-01-22
wow, it's moving! here what i did:
i edited /etc/modprobe.d/blacklist-firewire.conf and took away blacklist on firewire_ohci like that:

# Select the legacy firewire stack over the new CONFIG_FIREWIRE one.

#blacklist ohci1394
#blacklist sbp2
#blacklist dv1394
#blacklist raw1394
#blacklist video1394

#blacklist firewire-ohci
blacklist firewire-sbp2

then restart, then 
roughi@roughi-HP-2133:~$ ls  /dev/fw*
/dev/fw0  /dev/fw1 
:D

Ffado mixer is ok! Only Jack and guitarix don't work, is there sth to configure?
Thank you so far, it feels a lot better now!

---

### Post by jejeman on 2013-01-23
Firewire-ohci was blacklisted? Strange. Here how it is on 12.04
```
$ cat /etc/modprobe.d/blacklist-firewire.conf 
# Select the legacy firewire stack over the new CONFIG_FIREWIRE one.

blacklist ohci1394
blacklist sbp2
blacklist dv1394
blacklist raw1394
blacklist video1394

#blacklist firewire-ohci
#blacklist firewire-sbp2
```
Okay, firewire stack is working now, you have two nodes. One for firewire controler and one for FA-101. The hardware/driver side is good. Now, the software side.
Don't go to ffado mixer any more, it tends to bug JACK2 - JACK2 won't start after ffado mixer was started. Reboot needed.
Read the post #8 in the thread a gave. I can't tell you anything more but that.

---

### Post by roughi on 2013-01-26
ok, now i get sound! Thx!
i turned off jack d-bus and pulseaudio with
echo "autospawn = no" > ~/.pulse/client.conf && pulseaudio -k

how can i re-activate pulseaudio, if ever?
do i have to close this thread or so?

---

### Post by jejeman on 2013-01-27
You can start pulseaudio at will with
```
pulseaudio -D
```
You can mark thread as solved if the problem is solved. It will not be closed, I think, but it will be marked as solved.

---

