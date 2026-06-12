---
title: "Serial console"
date: 2010-10-06
forum: Server Platforms
---

### Post by watom on 2010-10-06
Hello,

I've got a home server running ubuntu 10.0.4. It have no monitor or keyboard. So I want to access it from a serial console. (I use SSH currently but if something goes wrong, I need to be able to do something... so serial console seems a fine thing).
OK, so on the server, I tell grub to output everything on ttyS0 and opened a getty on ttyS0.

On the client side (Laptop running Ubuntu 10.0.4 with pl2303 USB to Serial adapter) I use Minicom.

Home server restart :
I see grub menu, linux kernel messages, login prompt.
But, I can't do anything : In grub or at the login prompt, no key press is recognized by the server.
I've got write permission to /dev/ttyUSB0.
I tried a different getty (mgetty) with no success.
I stopped the getty on ttyS0 on the server. And run minicom.

From the server's minicom, if I type something, it appear on the client screen.
From the client's minicom, if I type something, some garbage appear on the server screen : &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; (One of this things for each char typed).

If I short-circuit pin 2 and 3 of the client serial port, it echoed what I type.

The two serial ports are connected with a nullmodem cable. (seems to be a full handshaking cable).

Of course, same serial port config for both minicom, grub and getty.

Hope I'm understandable enough. (English not my primary language).
Can somebody help me make this *$*#! serial console working right ?
I'm on it for 10 hours now with no success...

Edit : I nearly forgot to tell you I had to update the standard ubuntu kernel to 2.6.34-020634rc1-generic because there was a bug in the pl2303 driver in the stock kernel (2.6.32-25-generic) which prevented me from doing anything (even receiving).

---

### Post by watom on 2010-10-07
I'm still on it.
Nobody have an I idea ?

---

### Post by moonbug on 2011-01-14
loads of people having problems with the pl2303 serial adapter . 
some have had success with 
I saw some workaround like this (remove and load the module):
-----------------------------
sudo modprobe -r pl2303
sudo modprobe pl2303
Another workaround was using the screen program:
------------------------
screen /dev/ttyUSB0
(then press ctrl-C)
------------------------
Looking at the results of stty -a -F /dev/ttyUSB0 before and
after the usage of screen I found a simple solution:
--------------------------------
stty -F /dev/ttyUSB0 clocal

but results for me didn't work . hope it works for you

---

