---
title: "ubuntu server on p2"
date: 2009-04-04
forum: Server Platforms
---

### Post by kamarysan on 2009-04-04
i have a P2 at 200Mhz with 64M ram and 20g hdd. i want to know what version of ubuntu server to put on it. or if not works what linux distribution u recomanded to me.

---

### Post by hictio on 2009-04-04
Can you add more RAM to that box?
Aside from that, on my personal experience, I have found out that the biggest problem of installing newer distros on old hardware (aside from the minimal requirements of RAM) is the CDROM, I have tried many times to install different distros and they always crap during the install, specially during the phase of copying the base system.

On my old boxes what I usually do is making only the base install, and then install over the network the rest of the packages.

Regarding what Linux to get, I don't know what are you going to do with that box, but perhaps you can give [OpenBSD](http://www.openbsd.com/).

---

### Post by kamarysan on 2009-04-04
i want to make a little shoutcast server, and to learn more about using a linux server. so i think is ok.i`ll try ubuntu server. minimal instalation

---

### Post by cariboo on 2009-04-04
I would suggest using the mini.iso and just install what you need once the main installation is done. The mini.iso can be downloaded from [here]("http://help.ubuntu.com/community/Installation/MinimalCD"). Because  of the low specs, I don't think you will benefit from the server kernel.

I have a eMachine with a 400Mhz Celeron and 128Mb ram. I use it bsically as a network connected mp3 player. I mount a shared music directory from the server and then use a combination of mpg321 and  randomplay to play music continuously 24/7, the system in turn is connected to a Hardon/Karmon reciever I picked up at the local thrift store for $10 .I have randomplay set to not repeat a track for at least 7 days. There is no gui on this system as it just isn't needed. Mpg321 and randomplay are in the  repositories.

Jim

---

### Post by Iowan on 2009-04-04
I have a P200 running Breezy... mostly because I haven't been brve enough to upgrade it.  I also have a HP Netserver LC II (which I think is dual P2-200's) running Hardy (8.04.1).  It's no speed demon, but works for a development web server.

---

### Post by jamesrfla on 2009-04-04
The Ubuntu Server edition it small depending on what version you use. I ran Ubuntu server edition and apache2 using only 32MB of ram.

---

### Post by kamarysan on 2009-04-05
thanks for all information. hope i`ll do a good job with that. is i`ll have a problem i`ll ask u again. i`m a rooky in linux :)

---

