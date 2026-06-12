---
title: "TFTP Server = Pain"
date: 2008-01-13
forum: Testimonials &amp; Experiences
---

### Post by justmeagain on 2008-01-13
Ok, why isn't this simple? (yes I am a bit of a noob)

Honestly though, in windows I go to snapfiles pick up a free tftp server like tftpd32 and presto I am up and running, maybe in 2-3 minutes.  

Ubuntu, on the other hand, it is an ordeal of searching forums, digging through oodles of posts looking for the right info.  Unfortunatly it is still giving me problems.  I'm talking hours of time trying to get this simple task done. 

I like Ubuntu but after this I am not so sure. One little GUI TFTP server doesn't seem like a lot to ask for.

---

### Post by Borbus on 2008-01-13
[http://packages.ubuntu.com/gutsy/net/atftpd](http://packages.ubuntu.com/gutsy/net/atftpd)

sudo apt-get install atftpd

---

### Post by Limpan on 2008-01-13
I've used tftp to install a few times and I also boot 16 clients over the network at work.

[PXEInstall]("https://help.ubuntu.com/community/Installation/Netboot?action=show&redirect=PXEInstall")
[PXEInstallServer]("https://help.ubuntu.com/community/PXEInstallServer?highlight=%28pxe%29")
Were documents I found useful.

Concerning a GUI. It there isn't a gui available it could be because the kind of people that consider network booting find the setup with cli far easier. I know that it doesn't solve your problem but it might be so.

I'd be happy to try and help you though. But I need to know a bit more about what you're trying to do.

---

### Post by Besugo on 2011-12-07
Try this:

[http://code.google.com/p/tftpgui/](http://code.google.com/p/tftpgui/)

---

### Post by overdrank on 2011-12-07
Back to sleep thread. :)

---

