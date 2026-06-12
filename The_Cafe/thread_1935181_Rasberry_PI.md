---
title: "Rasberry PI"
date: 2012-03-03
forum: The Cafe
---

### Post by flyingalan on 2012-03-03
As a new user to Ubuntu I am interested if I can use latest version of Ubuntu on the new micro computer called Rasberry PI. 
The Rasberry SoC is a Broadcom BCM2835. This contains an ARM1176JZFS, with floating point, running at 700Mhz, and a Videocore 4 GPU. It has 256 MB Ram on board
It runs O/S from an SD card. 
Fedora, Debian and ArchLinux seem to be supported but the Rasberry web site says Ubuntu is not. 
Is there some fundamental problem ? Not being familiar with Linux I do not understand why one distribution seems OK but not another?
Can anyone throw some light or encouragement about using Ubuntu distribution.
Thanks in anticipation
Alan

---

### Post by Daveth on 2012-03-03
this
[http://www.youtube.com/watch?v=28CqDKjtppg](http://www.youtube.com/watch?v=28CqDKjtppg)
details loading on Debian 6 onto a Raspberry Pi, so Ubuntu ought to follow a similar route, being part founded on that distro.

---

### Post by sffvba[e0rt on 2012-03-03
The Raspberry PI uses an ARM processor.  For a distro to work the kernel etc. has to be compiled to work on that specific processor(s).  

The latest versions of Ubuntu will not work on the older ARM processor used in the Raspberry PI.  Older ones will (I think 9.04 and older).


404

---

### Post by lprofil on 2012-03-04
User "Not found" is right: only **Ubuntu 9.04** might run on the Raspberry pi 
since it supports the old ARM v6 Core. "Beginning with version 9.04, previous versions 
only supported x86 Newer versions of Ubuntu "[[1]]("http://www.geek.com/articles/chips/ubuntu-904-officially-released-available-for-free-download-20090423/")

Newer versions of Ubuntu only support ARM Core v7 upwards. 
It is not known yet if Ubuntu might support the old ARM Core versions again 
in favour for the Raspberry pi. Very likely not i think.

Searching for an old 9.04 image?
Search for it [here]("http://www.google.com/webhp?ie=utf-8&oe=utf-8#hl=en&q=ubuntu+9.04+iso+index+of") ;)

or get it streight from:

[here]("http://linuxfreedom.com/ubuntu-releases/9.04/") (US Los Angeles mirror)
[here]("http://mirror.sov.uk.goscomb.net/ubuntu-releases/9.04/") (UK mirror)
[here]("http://old-releases.ubuntu.com/releases/9.04/") (UK mirror)
[here]("http://mirror.telepoint.bg/ubuntu-releases/jaunty/") (Bulgaria Europe)
[here]("http://gomel.soft.telecom.by:8080/admin/ubuntu/iso/") (Belarus Europe)
[here]("http://ftp.riken.go.jp/Linux/simosnet-livecd/ubuntu/") (Japan)

and don't get fooled by those torrent isos which swirrling around which might be compromised.

/lprofil

[1] [only 9.04 upwards supports ARM]("http://www.geek.com/articles/chips/ubuntu-904-officially-released-available-for-free-download-20090423/")

---

### Post by jailbait on 2012-03-04
> **lprofil said:**
> User "Not found" is right: only **Ubuntu 9.04** might run on the Raspberry pi 
since it supports the old ARM v6 Core. "Beginning with version 9.04, previous versions 
only supported x86 Newer versions of Ubuntu "[[1]]("http://www.geek.com/articles/chips/ubuntu-904-officially-released-available-for-free-download-20090423/")

Newer versions of Ubuntu only support ARM Core v7 upwards. 
It is not known yet if Ubuntu might support the old ARM Core versions again 
in favour for the Raspberry pi. Very likely not i think.



/lprofil

[1] [only 9.04 upwards supports ARM]("http://www.geek.com/articles/chips/ubuntu-904-officially-released-available-for-free-download-20090423/")
No.
[Raspberry Pi uses ARM11.]("http://www.raspberrypi.org/faqs")

---

### Post by Jake5 on 2012-03-04
I don't understand why you would want to anyways, the Raspberry as its spelled correctly, boots fedora as is. If I were you, which I'm obviously not or I would use your body to climb to the top, I would buy a usb hd, partition it off and run any os you want off of that. Just remember you're limited to 256mb ram so don't go too crazy.

---

### Post by Paqman on 2012-03-04
Tbh, I don't think it'll be too long before there's a version of Ubuntu that'll run on it, whether it comes from Canonical or the community. There's just too many people out there using Ubuntu who will want access to the familiar repos and environment.

---

### Post by idoitprone on 2012-03-05
[http://www.raspberrypi.org/faqs](http://www.raspberrypi.org/faqs)

This contains all the information you need
btw you cant just make any distro on it because the binary gpu blob contrain the first stage bootloader - 
[Proprietary]("http://en.wikipedia.org/wiki/Proprietary_software")stalman's only weakness - alwys wanted to say tat

---

### Post by sffvba[e0rt on 2012-03-05
*Thread moved to **The Community Cafe**.*

... as it isn't a support question really...


404

---

### Post by alexfish on 2012-04-08
Raspberry Pi Testing done ,, cleared for sale

[http://crave.cnet.co.uk/desktops/raspberry-pi-testing-done-cleared-for-sale-50007577/](http://crave.cnet.co.uk/desktops/raspberry-pi-testing-done-cleared-for-sale-50007577/)

---

### Post by leecheroflife on 2012-04-08
Very interesting little devices, would make for a nice wee cheap linux media center.

---

### Post by Balthazar54 on 2012-07-08
I have one on order. I'm not a hardware type, but I'm thinking I could hook up a motion detector to it and use it for displaying pics on one the old analog tv's I haven't disposed of yet.

Or some other projects that come to mind. You can't go wrong for $35 and a cell phone charger.

Of course, I never seem to stop spending money after just buying the base device.   :(

Next comes a case, hdmi to vga converter, usb splitter, usb harddrive, etc.

---

### Post by pe7er on 2012-07-13
> **leecheroflife said:**
> Very interesting little devices, would make for a nice wee cheap linux media center.
Yeah, you can use OpenELEC for that: [http://openelec.tv/](http://openelec.tv/)
Their download pages didn't list Raspberry Pi,
so I compiled it myself which took my PC about 6 hours.

Later on I found out that there are binaries for the Raspberry Pi available... So you might want to try those instead.

If you have Model B with the Ethernet connection and if you have an Android or iPhone: 
connect the Raspberry Pi to your wifi-router, 
and download some XBMC App for your phone to use it 
as remote control for your Raspberry Pi media center :D

---

