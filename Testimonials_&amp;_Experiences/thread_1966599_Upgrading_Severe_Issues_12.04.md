---
title: "Upgrading Severe Issues 12.04"
date: 2012-04-27
forum: Testimonials &amp; Experiences
---

### Post by vanquishedangel on 2012-04-27
Well upgrading ubuntu has never gone well for me, whether or not I use a 3rd party repository it seems doomed to re-installing.

When I tried to upgrade through update manager it would crash, I submitted a report, then tried sudo apt-get upgrade and got all nothing, then tried sudo apt-get dist-upgrade same thing. I knew that 12.04 was out because it was on the website and posts about it were already there. What I mean by all nothing was that it acted as if there were nothing to install. so I downloaded a disk and burned it.

The disk install seemed smoother than ever usually I get ubiquity crashed or something but I never got that. I clicked the upgrade from 11.10 to 12.04. Instead it seemed that all installed until at the end when trying to install the last few packages then when i opened the details window it was saying something about fix broken packages, good thing I clicked that arrow lol, I would have never known :).

Anyway I eventually got a disk to install and had to erase the whole disk to do it, and all seemed well until I rebooted, and it hung at a black screen but the recovery kernel would start. So messing around I tried the on board graphics instead of my card and eventually that worked after rebooting a few times, I kept getting a libdrm error about radeon but it kept scrolling so fast that I couldn't read the whole thing. eventually I got it to the desktop by restarting and there were a few other errors to.

After i got it started to a desktop and logged in and then another error appeared "One or more XML syntax error were found while parsing the Openbox configuration files. 
See stdout for more information. 
The last error seen was in file "/home/shawn/.config/openbox/menu.xml" line 1, with message: Start tag expected, '<' not found." I fixed this by replacing it with the file from /etc/xdg/openbox/rc.xml and renamed it lubuntu-rc.xml because I am using lubuntu currently, and the old file was 0 bytes, renamed to just rc.xml

I hope this helps people and devs if they can figure out what was wrong, that's why I posted this, sorry to be a little nondescript, it has taken all day to get it working.

To fix the ati issue, I have 2 ati cards one is built in (ati x300) and one is purchased (ati radeon hd 6450) So the built in one cannot use proprietary drivers because it isn't supported anymore so mesa with the libdrm issue is the only way along with restrting and hoping it boots lol. mesa will hang at a black screen with the 6450 and show no errors. jockey will not install drivers if I use the x300, so what i did was I had to download the drivers from amd's site, and choose the driver for the 6450. installed that according to [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI). then shutdown the computer, install the 6450, and boot it again.

Now there is no errors anymore and things are beautiful, just took all day lol.

---

### Post by Ceedub2 on 2012-04-27
Good to hear you got it working finally.

---

### Post by mastablasta on 2012-04-28
> **vanquishedangel said:**
> 

I hope this helps people and devs if they can figure out what was wrong, that's why I posted this, sorry to be a little nondescript, it has taken all day to get it working.



this is the wrogn place to post for the devs. they rarely visit the forums.

as for your upgrade if you had proprietary AMD driver installed before they you would need to remove it before doing the upgrade (possibly boot info vga safe mode or similar). i think it's the same thing with windows, or they simply overwrite the old driver, i forgot...

---

