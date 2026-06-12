---
title: "No Sound After 9.10 Upgrade"
date: 2009-10-31
forum: System76 Support
---

### Post by cmnorton on 2009-10-31
I have a Gazelle Ultra -- very happy with it by the way -- and after the 9.10 upgrade, which went well, I have no sound. Video plays fine. I have no hardware listed under Preferences --> Sound. 

What do I need to install?

Edit:
-------------------------------------
My upgrade installed with no errors. I did look on the system76 site, but I have no 3rd party section in software sources. Also, my links point back to Jaunty, not intrepid. Yet as stated above, I had no install errors.\

Sound card is recognized.
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

I am losing my drivers on reboot. If I run this program one or two times after reboot

sudo /sbin/alsa force-reload

I get my sound back.

---

### Post by marshmallow1304 on 2009-11-01
I lost sound on my Pangolin after installing the driver for the software modem.  If there is such a driver for the Gazelle, try removing it.

---

### Post by autocrosser on 2009-11-01
Take a look at this for your answer: [http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html](http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html)

Install the backport talked about & reboot to check.

---

### Post by cmnorton on 2009-11-01
> **autocrosser said:**
> Take a look at this for your answer: [http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html](http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html)

Install the backport talked about & reboot to check.

Thanks, but some of this is a bit over my head. I don't know a lot about sound, and a lot of tasks are listed on this blog without the how-to. 

I'm hoping System 76 will have a more detailed how-to on fixing this.

---

### Post by thomasaaron on 2009-11-02
Charles,

Please go to System > Admin > Hardware Drivers.
Disable the Modem Software driver.
Reboot.

Did that fix it?

---

### Post by cmnorton on 2009-11-02
> **thomasaaron said:**
> Charles,

Please go to System > Admin > Hardware Drivers.
Disable the Modem Software driver.
Reboot.

Did that fix it?

Will try tonight after work, and will post back here.
Thanks.
cmn

Edit:
-------------------------
Thanks. That fixed it.

---

### Post by jpongin on 2009-11-02
Aaron,

Is there a permanent solution for this?  Is there a way to get the sound to work without having to disable the modem?

---

### Post by thomasaaron on 2009-11-03
No. The modem software is the problem. It's never had good support under Linux, and it often interferes with ALSA.

---

### Post by jpongin on 2009-11-03
Thanks Aaron.  I guess I'll have to disable the modem software.

I'm curious about one other thing then.  I noticed that System76 is selling systems with Karmic installed, how are you guys handling the sound issue?  Are you disabling the modem software out of the box?

---

### Post by thomasaaron on 2009-11-04
It is disabled in the images we use for our machines. Plus sound is tested on the computers before they ship.

---

### Post by gasapi on 2009-11-14
I had the same problem after an upgrade from 9.04. I managed to solve it by removing the proprietary driver of my modem. I seems like there is a conflict between that and ALSA.

Try that out by System->Administration->Hardware Drivers
select Software Modem and Remove

Good luck!

---

### Post by Gato303co on 2009-11-14
Disable the modem? what kind of solution is that? and what about people who still uses modem connections to access the web?

---

### Post by jbelmonte on 2009-11-14
> **Gato303co said:**
> Disable the modem? what kind of solution is that? and what about people who still uses modem connections to access the web?

Hi Gato,

Thomas mentioned on the prior page that there is no permanent solution for this issue. "The modem software is the problem. It's never had good support under Linux, and it often interferes with ALSA." So, you are disabling something that doesn't work. Although the modem exists in the laptop, System76 does not list it in their product descriptions, and removes the modem drivers in the images they use to prepare their laptops. If someone needs a modem, there are external modems that do work.

Ciao!

---

### Post by awoade on 2009-11-15
Hi, I'm also trying to fix the lack of sound problem after upgrading to 9.10.

The thing is, I usually run Kubuntu but logged into Ubuntu to try and find the "Hardware drivers".  But, there is no "Hardware drivers" listed under my system->admin tab.  Help!

---

### Post by thomasaaron on 2009-11-16
awoade, what System76 model are you using?

---

### Post by awoade on 2009-11-16
I'm using a PanP5.

ETA: I think I had previously removed Gnome for some reason, but reinstalled it. I never really used the Gnome environment and it was running fine with just KDE.  I reinstalled it because I wanted to have it as a backup... could that have caused the problem? Should I just backup all my data and do a clean reinstallation of ubuntu?

---

### Post by thomasaaron on 2009-11-17
I'm not really sure what might have happened in Kubuntu to hose sound, as we don't support Kubuntu.

But installing Gnome *may* have caused the problem. In gnome, go to System > Prefs > Main Menu > Admin and see if Hardware Drivers is there but just not checked.

Edit:
You may also want to check this thread out...
[http://ubuntuforums.org/showthread.php?t=1306773&page=5](http://ubuntuforums.org/showthread.php?t=1306773&page=5)

---

### Post by awoade on 2009-11-18
Though I don't know if the Hardware tab appears as I'm logged into Kubuntu right now, I solved my sound (and touchpad) problem.

I guess the repository auto-updated the System76 driver to 2.4.  I apt-get removed it, then installed 2.3.9 and ran it - now sound works, as well as my touchpad!

---

### Post by BabiiNiya on 2009-11-29
i have the same problem too...after i upgrade my laptop to unbuntu 9.10 i cant hear anything at all...no music nor any sound from any videos i have...help me...

---

### Post by thomasaaron on 2009-11-30
BabiiNiya, which System76 computer do you have? Did you try the suggestions above?

---

