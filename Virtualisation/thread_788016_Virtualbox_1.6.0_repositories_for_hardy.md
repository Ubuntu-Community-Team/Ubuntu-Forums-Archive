---
title: "Virtualbox 1.6.0 repositories for hardy"
date: 2008-05-09
forum: Virtualisation
---

### Post by fofftorrent on 2008-05-09
Other threads suggest that the repository
deb [http://www.virtualbox.org/debian/](http://www.virtualbox.org/debian/) gutsy non-free

can be used to install virtualbox 1.5.6 in hardy too

however, it appears that the new virtualbox 1.6.0 has not been added to these repositories AND there there is a hardy (8.04) version available as well:

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

does anyone know of an repository that has this new version? :confused:

---

### Post by maybeway36 on 2008-05-09
I jsut downloaded the deb from Sun and installed it (double-click).

---

### Post by fofftorrent on 2008-05-12
i feel much safer installing from repositories with aptitude instead of downloading .deb packages

---

### Post by Ocxic on 2008-05-13
i downed the .deb works great, I did have to uninstall virtual box and it's modules first tho

---

### Post by fofftorrent on 2008-05-13
.deb worked for me too, but repositories should be the preferred method since it should result in better dependency handling and update tracking ;-)

---

### Post by theZoid on 2008-05-14
Yep, if anyone gets a repo addy, please post here!  thanks!  btw, 1.6.0 is awesome.

---

### Post by Jerdsy on 2008-05-17
According to VirtualBox, there won't be a Hardy repository, 

EVER!


> "Unfortunately we will probably not be able to offer Debian repositories for future versions of VirtualBox, as we now have to comply with US export restrictions, which involve people downloading VirtualBox "clicking to accept" conditions. "

[http://www.virtualbox.org/ticket/1519](http://www.virtualbox.org/ticket/1519)


I realize these inane and unenforceable export restrictions aren't their fault.  Still, VirtualBox's reasoning is ridiculous.  

They could jump through this government imposed hoop by putting the "click to accept" within the installation dialog.  If that didn't completely satisfy the restrictions, they could even have the installer "phone home" to verify that the IP address was not in an unapproved nation. 

Removing all new versions of VirtualBox from the repositories is a lazy solution.

---

### Post by fofftorrent on 2008-05-18
Ouch! Or could it be that Sun does not want to advertise the simplicity of debian package mgmt!:lolflag:

---

### Post by jyrinx on 2008-05-21
My guess is that Sun's legal department says they have to. Sun makes you click through just about everything else, too.

---

### Post by theZoid on 2008-05-21
> **jyrinx said:**
> My guess is that Sun's legal department says they have to. Sun makes you click through just about everything else, too.

I couldn't find it in the OpenSolaris repo either.

---

### Post by bit-a on 2008-05-21
i too urgently want 1.6.0 from repos because of its new VBoxHeadless making vbox better for server environments. i hope, the repos won't lag too much.

concerning the closed edition: would it be possible to make a repo-package that automates downloading from cds.sun.com? of course the clickable agreements must be obeyed. therefore the package would be dummy an in the configuration-phase, it should display sun's agreements and download everything thereafter. in that way you may get rid of the "open firefox, enter url, click here, click there"-ceremony without breaking the rules.

---

### Post by fofftorrent on 2008-05-22
yeah it seems that it should be easy to create a repo that provides all the relevant prompts... what gives? anybody want to raise this as another ticket on virtualbox.org that will get looked at?

---

### Post by cambron on 2008-05-27
i am having troubles running a guest machine in the Sun xVM VirtualBox 1.6 within Ubuntu 8.04 64-bit on my imac 20" core 2.

I downloaded the VirtualBox amd64 deb for Ubuntu 8.04. I was able to install it and it runs, creates a virtual disk but it gets stuck after i click run and it shows the black screen with the msg saying "Starting the Virtual machine... 0%". I even mounted an ISO image to the virtual cd drive, also tried the mount the virtual drive to hardware drive with windows xp cd in it (same result with ubuntu cd).

I have to force quit the application it is stuck.

---

### Post by armitage1337 on 2008-08-16
I don't understand why Sun can't do the same thing they do for the JRE/JDK - show a 'click to accept' menu when you install from the repositories.

---

