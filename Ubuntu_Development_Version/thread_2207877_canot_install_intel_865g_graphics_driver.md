---
title: "canot install intel 865g graphics driver"
date: 2014-02-25
forum: Ubuntu Development Version
---

### Post by chris_dummer on 2014-02-25
i am running the 14 beta and grapics indicates i`m  using vesa standard graphics i.e. no intel driver installed i tried installing intel-linux-graphics-installer_1.0.3_i386.deb(from intel site)
but it will not finish installing in software centre.

my graphics are a bit slugish(its an old machine) is it worh persisting.

---

### Post by grahammechanical on 2014-02-25
You do not tell us the specification of your machine. And what is 14 beta? What version of Ubuntu is that? Does your machine have a 64bit CPU? Is Ubuntu 64 bit? If so then why would a 32bit driver work on it? i386 = 32bit.

What is wrong with installing a video driver through the Additional Drivers utility? It will match the driver with the hardware and software .

Regards.

---

### Post by Iowan on 2014-02-25
Assuming 14 beta means 14.04, moved to Ubuntu + 1

---

### Post by cariboo on 2014-02-25
Have a look at [this]("http://www.ubuntugeek.com/how-to-install-intelr-linux-graphics-drivers-on-ubuntu-13-04.html") page, please note the warning also.

---

### Post by deadflowr on 2014-02-25
Your card is super old.
I doubt installing those drivers will help in anyway.

Where is it telling you that it's running vesa?

Run
```
sudo lshw -C display | grep driver
```
to see if you aren't actually running the i915 driver.

I don't even know if intel supports that card anymore anyway.

*My random two cents*

---

### Post by mörgæs on 2014-02-26
I don't know about 14.04, but for 13.10 no additional drivers were necessary for 865. 

The fix for slow / coarse graphics was adding an xorg.conf as described [here]("https://lists.ubuntu.com/archives/lubuntu-users/2013-November/006117.html").

It's very unlikely that the computer is 64 bit.

---

### Post by chris_dummer on 2014-02-26
ubuntu 14.04 32 bit
ibm thinkcentre
1g ram
duel core (hyper threaded) 2.8ghz intel 4 32bit
graphics intel 865g
i have tried all of the above: the deb file fom intel (intel-linux-graphics-installer_1.0.3_i386.deb) tries to install but stops with the message"package operation failed"
i know its an old machine and do not expect  to much thats why i`m using it to experiment with ubuntu/linux my unix days were long ago and i have forgotten most of it.
everything else on the system seams fine at the moment.
sys info still says vga graphics controler (vesa) so no intel installed.

---

### Post by chris_dummer on 2014-02-26
configuration: driver=i915 latency=0
is returned 
does that mean i am using the correct driver?
by the way thanks all for efforts.
 i think this may be problem solved! That is it was not a problem.

---

### Post by Yellow Pasque on 2014-02-28
> sys info still says vga graphics controler (vesa) so no intel installed. 

Do not rely on that program. sysinfo often says "VESA" to indicate a VESA-compliant GPU.  It does not necessarily mean you're using the VESA driver. (Yes, I think it's a terrible idea, especially in a distro aimed at n00bs who freak out when they see something like that...)

The best way to check your graphics status is either looking at glxinfo or the /var/log/Xorg.0.log

---

