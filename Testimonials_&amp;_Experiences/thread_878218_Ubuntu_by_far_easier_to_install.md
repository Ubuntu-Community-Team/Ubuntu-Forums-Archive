---
title: "Ubuntu by far easier to install"
date: 2008-08-02
forum: Testimonials &amp; Experiences
---

### Post by lavinog on 2008-08-02
A couple of months ago, I built a new computer...I installed Ubuntu 8.04 on it in under 30 mins. Everything worked with no problems. I even installed the latest fglrx driver from ati in under 5 mins.
Last night I decided it would be nice to take advantage of my netflix video on demand (which only supports windows.) So I preceded to install windows XP home on another partition.
1st attempt: I had to set my SATA controller to IDE emulation, because I don't have a floppy drive. Got windows loaded (took 1 hr), loaded the driver disk for my mobo...windows had to reboot 6 times to install all of the drivers. After that I decided to install SP3 instead of installing the 100+ updates...SP3 broke my audio. Then I needed to install windows media 11 in order to use netflix...well to do that I had to activate...no problem I thought...it is a legitimate key. WPA tells me that I have activated too many times...which is weird because the last time I activated this was a reinstall back in 2004 on my old machine...before that it was in 2002 on the same machine. So I tried some new WPA beta activation thing on microsoft's website and couldn't get past the Captcha screen. So I called it in...after wasting my time with the automated system which conveniently tells me the same exact thing my computer told me, it put me on hold for 30 mins to connect me with a real live human. The person got really frustrated with me because I didn't understand her questions mostly because of all of the static on the line, but also because of their vagueness: "6 Digit ticket number please?" (for those that don't know there is a hash key of some sort consisting of many 6 digit numbers...none of them labeled Ticket number"

After all of that frustration I have yet to be able to fix my audio drivers...which also fail to tell me why they don't want to install.
Also I come to find out that the only way to have my SATA drive in its native mode is to reinstall windows with a slipstreamed disk with the drivers in them...there is no way to install the drivers after installation...so I have to go through all of this all over again.

Has anyone experienced this with Ubuntu?

---

### Post by Sef on 2008-08-02
> Has anyone experienced this with Ubuntu? 

Not me.  I did have to set up my audio manually when I first started with Ubuntu, but that bug has been fixed.  It just plays now. :)

---

### Post by prshah on 2008-08-02
> **lavinog said:**
> 
After all of that frustration I have yet to be able to fix my audio drivers...which also fail to tell me why they don't want to install.
Also I come to find out that the only way to have my SATA drive in its native mode is to reinstall windows with a slipstreamed disk with the drivers in them...

Your audio issues are probably related to microsoft's new universal audio architecture (uaa). If you're running a relatively new board, you need to _first_ install UAA, _then_ install your audio drivers. UAA is available from Microsoft's website, but it's better you pick them up from your mobo CD and/or the mobo manufacturer's site.

From 8.04 onwards, the problem of SATA drives not being visible during installation is cleared in Ubuntu; For Windows, i've found that just switching the BIOS option back to "Native" from "Legacy" _after_ installation works fine in Wndows XP Pro. Use at your own risk though (not that I've faced any problem, but I'm paranoid).

---

### Post by Methuselah on 2008-08-02
I have SATA drives AND a RAID 1 array.
Ubuntu installed with absolutely no problem...done in 20 mins.
However the mobo manual wanted me that I needed to have a floppy drive with RAID drivers if I wanted windows to find the drives.

I installed ubuntu several times on this machine before settling on a setup.
I tried the amd64 then the i386 then settled on the amd64.
That I would undertake to repeat the procedure should indicate how easy it was.

---

### Post by steveneddy on 2008-08-03
There arethreads on the forums that address these issues.

---

