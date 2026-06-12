---
title: "System76 Driver 2.3.3 released - Adds Jaunty support"
date: 2009-04-20
forum: System76 Support
---

### Post by crichell on 2009-04-20
System76 Driver 2.3.3 has been uploaded to our software repository. You should see the update soon. The latest released adds Jaunty support! All current laptop/desktop models are tested and the necessary patches are implemented.

Please let us know if you experience any Jaunty bugs after running the driver and rebooting (System > Administration > System76 Driver). We'll try to patch everything up prior to Thursday's release.

File bug reports here: [https://bugs.launchpad.net/system76](https://bugs.launchpad.net/system76)

 Change Log

Version 2.3.3

#Add command line restore and install driver options
#Remove some info from system info tab (CPU, HD, Mem)
#Change startup script from bash to python
#Add syslog to support archive
#Add Jaunty support 

Version 2.3.2

#Add new Meerkat NetTop system
#Add Pangolin update (panp5)

---

### Post by greg_g on 2009-04-21
Just wondering if this wiki page will be updated to include what the driver does for 8.10 and 9.04?
[http://knowledge76.com/index.php/System76_Driver](http://knowledge76.com/index.php/System76_Driver)

---

### Post by thomasaaron on 2009-04-21
Yes, but not until Jaunty is released. There's a slight chance more patches will be added.

---

### Post by crichell on 2009-04-22
> **greg_g said:**
> Just wondering if this wiki page will be updated to include what the driver does for 8.10 and 9.04?
[http://knowledge76.com/index.php/System76_Driver](http://knowledge76.com/index.php/System76_Driver)

We're going to migrate what the driver does for each release to each models wiki page. It'll get out of hand on that page. I think we're now up to 30+ models and 8 Ubuntu releases over the last 3.5 years.

---

### Post by pimanac on 2009-04-23
Hi
Do you know if the new driver coupled with jaunty will add support for audio over HDMI?  Im currently running opensuse 11.1 on the machine but plan on switching to jaunty if it adds support for the HDMI audio (probably will switch back anyway...regardless).  Ive got a pangolin performance (Panp4).  
 
Thanks in advance!

---

### Post by thomasaaron on 2009-04-23
That is an ALSA problem. I'm not sure yet if it is fixed under Jaunty. It was supposed to be, and early tests with the the 1.0.18 version of ALSA produced sound, but recent testing indicates it may have regressed again.

---

### Post by pimanac on 2009-04-23
Hi
thanks for the prompt response.  I guess ill give it a whirl and see what happens.  If it doesnt work, ill give alsa 1.0.19 a try.
 
thanks again!

---

### Post by Lee_Machine on 2009-04-23
I got sound over HDMI on 8.10 (Pangoline Performance) when I compiled ALSA 1.0.18. 

But with 9.04 1.0.18 is included, but my device is not detected as it should be. running the command aplay -l will show you if it is. 

I havent tried compiling 1.0.19 yet and see if it works. I too was hoping for sound via HDMI out of the box. :confused:

---

### Post by gpstar on 2009-04-24
did you enable the IC958 switch in the Alsa mixer? (you may have to unhide it in the preference menu to see it) when I did that, HDMI audio works for me in Intrepid. Haven't tried it yet in Jaunty though.

*EDIT*
works in jaunty too.

---

