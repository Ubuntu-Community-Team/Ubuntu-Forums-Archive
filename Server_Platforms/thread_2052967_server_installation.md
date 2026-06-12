---
title: "server installation"
date: 2012-09-04
forum: Server Platforms
---

### Post by hiperflash on 2012-09-04
Hey all!

So im new here on this forum so please dont be hard on me :) 
well heres my problem.

I want to set up my home server. i must say i tried ubunto before and its awesome :D heh

so heres the thing after i tried to install ubunto server to my machine everything goes fine with no errors.. 
but when the installation is finished i removed dvd/cd/usb and the system reboots..but nothing will load im stuck on black screen with blinking "**_**" on bottom left corner and nothing happens..
i tried to reinstall like million times..

so if anyone knows how to fix this i would be very thankful for informations!

sorry if i posted same thing like other users but i didnt find suitable answer on forum

thank you so much all!

greetz 
hiperflash

---

### Post by 2F4U on 2012-09-04
Can you provide more details about your hardware? Am I right in assuming that you verified the checksum of the downloaded iso file and burned at the lowest possible spead?
One possible quick workaround on black screen problems might be to try using the nomodeset grub kernel parameter:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by hiperflash on 2012-09-04
> **2F4U said:**
> Can you provide more details about your hardware? Am I right in assuming that you verified the checksum of the downloaded iso file and burned at the lowest possible spead?
One possible quick workaround on black screen problems might be to try using the nomodeset grub kernel parameter:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

yea well motherboard is D52032-712 intel
dual core 2x xeon
disks in raid 2

ill try to boot from cd again and try to run grub and disable that frame buffer..

the thing is when i reboot machine it wont give me any options for grub.. :/

---

### Post by black veils on 2012-09-04
access grub by holding down the shift key during boot process

---

### Post by hiperflash on 2012-09-04
> **black veils said:**
> access grub by holding down the shift key during boot process

if that works ill love you till the end of time!

the problem is that i dont see anything while booting.. jsut that hardware check and so on.. after that i see black screen :/

---

### Post by black veils on 2012-09-04
computer is off >> hold shift key >> power on the computer >> keep holding shift key, maybe grub will show

if it doesnt then you really have a messed-up install


EDIT:

have you tried installing using the **[ubuntu mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD")** ?

---

### Post by hiperflash on 2012-09-04
> **black veils said:**
> computer is off >> hold shift key >> power on the computer >> keep holding shift key, maybe grub will show

if it doesnt then you really have a messed-up install


EDIT:

have you tried installing using the **[ubuntu mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD")** ?

oh wait so i have to hold like 10mins? :o huh..
thats server machine and takes a while to boot.. 

i didnt try yet but ill try it..

---

### Post by black veils on 2012-09-04
not 10 minutes, when it gets past post, it will start loading grub

---

### Post by hiperflash on 2012-09-04
> **black veils said:**
> not 10 minutes, when it gets past post, it will start loading grub

yeh it was more of a joke :) heh ty ill try everything what u said and ill post the results :) 

thx again :)

---

### Post by hiperflash on 2012-09-05
so the results are..
holding shift didnt work.. 
it was some problem with frame buffering so i used that "nomodeset"

and worked fine
ty again

greetz

---

