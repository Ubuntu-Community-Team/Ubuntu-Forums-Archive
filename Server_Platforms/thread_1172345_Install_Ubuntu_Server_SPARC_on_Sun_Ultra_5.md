---
title: "Install Ubuntu Server SPARC on Sun Ultra 5"
date: 2009-05-28
forum: Server Platforms
---

### Post by rocketmanx on 2009-05-28
[SIZE=2]Hi,

I'm trying to install Ubuntu 9.04 server sparc on an Ultra 5 using the cdrom.

I downloaded the ubuntu-9.04-server-sparc.iso
from: [http://cdimage.ubuntu.com/ports/releases/9.04/release/](http://cdimage.ubuntu.com/ports/releases/9.04/release/)
and verified the md5sum.

I burned the iso to a cdrom disc and verified the md5sum on the cdrom disc.

I enter the OBP during initialization by pressing the keys Stop A.
I boot with: boot cdrom
At the Welcome to Ubuntu jaunty! screen I start the install with: install
I select install language.
I select the country.
I select keyboard model: Sun Type 5
I select keyboard origin: USA
I select keyboard layout: USA

Then the installer displays a banner with the message: Detecting hardware to find CD-ROM

Then a banner is displayed with the message: No common CD-ROM drive was detected.

The banner mentions that I can install drivers from removable media or I will be given the option to manually select CD-ROM modules. The banner provides these options:

Load CD-ROM driver from removable media? Yes No

When I select No the install does not go any further. It does not give me the option to manually select CD-ROM modules. It installer hangs and continues to display this banner.

When I select Yes with a blank floppy in the drive the install searches the floppy for the cdrom drivers.

Can someone tell me where can I get/download the cdrom drivers to put on a floppy?
Are there any special instructions for installing the drivers on a floppy?

Is there an alternate solution for this Ultra 5 installation problem similar to this one for the Power PC?
[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)

How can I do a netboot install of Ubuntu server on the Sun Ultra 5 from a PC running Ubuntu on the local network?


Thanks :)

Ken

[/SIZE]

---

### Post by thing3 on 2009-09-10
Id like to bump this post as I have exactly the same problem at exactly the same point in the installation.

I have installed (as a test) Ubuntus 6.10 and 7.04.  they both installed well except that there was no gnome desktop.  I am not sure what changed in 9.04.  also, i have not tired it on the inbetween versions, just these three.

---

### Post by tomszyszko on 2009-09-14
All u need to do is install ubuntu sparc 6.06, then upgrade it to 8.04 then to 9.04 (but 9.04 will be slower on this system...i know because im doing it now

---

### Post by KiLaHuRtZ on 2009-09-14
I run 8.04 on a Sun Enterprise 420R.  Mind you it is a tad more powerful than a Sparc 5 ;), however I have also done some testing on other Sun platforms.  I would have to agree with the upgrading procedure, although I would recommend you stay at 8.04 being an LTS version.  It's supported until April of 2013 on the server distribution.  I would start start with an install of 6.06 and upgrade to 8.04 as stated above.

---

