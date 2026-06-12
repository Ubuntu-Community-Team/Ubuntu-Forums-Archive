---
title: "New Nvidia driver 313.09"
date: 2012-12-13
forum: Ubuntu Development Version
---

### Post by IanW on 2012-12-13
Landed yesterday (12/12/2012)

[32-bit]("http://www.nvidia.co.uk/object/linux-display-ia32-313.09-driver-uk.html")
[64-bit]("http://www.nvidia.co.uk/object/linux-display-amd64-313.09-driver-uk.html")

---

### Post by jfernyhough on 2012-12-13
As a pointer, Ubuntu debs are available via the X Crack (Edgers) PPA: [https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by Harry33 on 2012-12-13
> **jfernyhough said:**
> As a pointer, Ubuntu debs are available via the X Crack (Edgers) PPA: [https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)

And that driver does work fine in RR.

---

### Post by QDR06VV9 on 2012-12-13
> **Harry33 said:**
> And that driver does work fine in RR.

Works Great Here!!:guitar:

---

### Post by pqwoerituytrueiwoq on 2012-12-13
install it last night and booted today, got stuck and initramfs
was able to fix it from old kernel, managed to bork 2 of my 3 kernel version before i got it to boot again by downgrading nvidia-current  to the 310 version
will attempt reinstall of the new driver once i fix my other kernels

edit:
worked that time :)

---

### Post by Cavsfan on 2012-12-14
Working well on my machine - Geforce 9800 GT.

---

### Post by andrew.46 on 2012-12-16
Hope to have more luck with this one 310.19 gave me some hard freezes...

---

### Post by Cavsfan on 2013-01-25
Just reinstalled the daily iso and got driver version 310.18. We shall see how it works....

---

### Post by tad1073 on 2013-01-27
> **Cavsfan said:**
> Just reinstalled the daily iso and got driver version 313.18. We shall see how it works....

I'm using 310.32

---

### Post by Cavsfan on 2013-01-27
> **tad1073 said:**
> I'm using 310.32

Forgot to report back. After a few days of using 310.18, it seems to work well.

I managed to install the that version on Lucid, Precise and Quantal by installing gdm and using that but, could not get it to install on Raring.

EDIT: Meant 310.18 and not 313.18. Also the 310.32 driver would not work on my setup. Tried to install it twice. I have 310.19 installed now.

---

### Post by Harry33 on 2013-01-27
> **Cavsfan said:**
> Forgot to report back. After a few days of using 310.18, it seems to work well.

I managed to install the that version on Lucid, Precise and Quantal by installing gdm and using that but, could not get it to install on Raring.

EDIT: Meant 310.18 and not 313.18. Also the 310.32 driver would not work on my setup. Tried to install it twice. I have 310.19 installed now.

Could you try to reinstall (in terminal or console) the certified driver 310.32.
It if fails, you could post the error messages here.
Perhaps Ricotz could then see the messages too.

---

### Post by Cavsfan on 2013-01-27
> **Harry33 said:**
> Could you try to reinstall (in terminal or console) the certified driver 310.32.
It if fails, you could post the error messages here.
Perhaps Ricotz could then see the messages too.

I uninstalled 310.18 and then installed 310.32 through SPM and then rebooted. All I could ever get was a 640x480 screen or something similar.
Conky did not show any Nvidia version.
When I opened Nvidia X Sever Settings, it gave an error saying there was no config file and to enter **sudo nvidia-xconfig** but, that did not work either.

Anything else you want me to try?

---

### Post by ronacc on 2013-01-27
added the xorg-edgers ppa , applied all updates and installed the nvidia 313. driver , gnome would not start , could only get to a very crippled unity , purged the ppa and running well with the nouveau driver.

---

### Post by Cavsfan on 2013-01-27
Finally got 310.32 installed but, I got it from nvidia's website.
I can't tell you all of the stuff I had to do. Once I was looking at a dash blinking in the top left corner.
I ended up purging a previous 310.19 that was installed. It still would not install.
In root shell I enter ```
dpkg -l | grep nvidia 
``` and found that another version was still installed. 310.18 I think.
So I purged those 2 files and tried to install and the installer went through a bunch of stuff saying this and that folder was not found, etc.
Then it said that the nouveau driver was still installed so it asked to blacklist it which it did.
Then it finally installed. Not even sure if this is exactly how it went but, this is the best I can offer.

---

### Post by Rukiri on 2013-01-27
The latest should be 313.18,  and solves most of my issues.

---

