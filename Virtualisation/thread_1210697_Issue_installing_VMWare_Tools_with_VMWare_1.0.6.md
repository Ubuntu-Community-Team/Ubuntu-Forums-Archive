---
title: "Issue installing VMWare Tools with VMWare 1.0.6"
date: 2009-07-11
forum: Virtualisation
---

### Post by JockVSJock on 2009-07-11
Greetings, I'm trying to install VMWare tools for VMWare 1.0.6 on Ubuntu 8.04.  

Getting confused on the following directions, from the following website: 

[http://peterc.org/2008/62-how-to-install-vmware-tools-on-ubuntu-hardy-804-under-vmware-fusion.html](http://peterc.org/2008/62-how-to-install-vmware-tools-on-ubuntu-hardy-804-under-vmware-fusion.html)

```

mv -f open-vm-tools-2008.04.14-87182/modules/linux/*.tar vmware-tools-distrib/lib/modules/source/

```

Not able to find this directory, so I'm not sure what is going on here.  

I was successful in installing VMWare 1.0.06, however, I'm not able to point it at a Linix iso and startup a virtual machine for Linux...So I though that installing VMWare Tools would fix it.

thanks

---

### Post by ibuclaw on 2009-07-11
I'd suggest you have a look at [Bodhi.Zazen's tutorial]("http://ubuntuforums.org/showthread.php?t=779934"),

There is a link to the VMware-tools guide on the page ([here]("https://help.ubuntu.com/community/VMware/Tools"))

That is how I got VMWare initially setup when I first tried it out.

Regards
Iain

---

### Post by JockVSJock on 2009-07-13
This is going to be a dumb question, I can't even run Linux isos from VMWare.  When I try to navigate to them, they are grayed out.  I'm not sure what the reason is for this.  

Do I need VMWare Tools to fix this? 

When I was running VMWare 1.0.6 under Ubuntu 8.04 awhile back (I was running 8.09, however I went back to 8.04 because it was unstable on my system), I had no issues running Linux isos. 

thanks

EDIT:  I figured out how to point it to the iso file:  Edit Virtual Machine > Hardware Tab > CD-ROM > Use .iso image. 

I'm still going to play around with the VMWare Tools and see if I can figure that out.

---

