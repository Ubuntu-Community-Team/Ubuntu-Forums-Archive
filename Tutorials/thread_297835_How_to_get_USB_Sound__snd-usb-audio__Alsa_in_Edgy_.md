---
title: "How to get USB Sound / snd-usb-audio  Alsa in Edgy to work properly"
date: 2006-11-11
forum: Tutorials
---

### Post by lp7413 on 2006-11-11
This was brought to my attention quiet sometime back, about how people who were using USB audio devices as their primary sound driver couldn't get anything that strictly depended on alsa to work, however certain apps would work fine.  After doing a bit of research on this issue i think i found the appropriate fix for this issue.  

The first thing you need to do is open up your favorite editor with sudo. 

in kde you might use:
> sudo kate /etc/modprobe.d/alsa-base

in gnome use: 
> sudo gedit /etc/modprobe.d/alsa-base


Once you have this file opened up scroll down to the line that looks like this:
> options snd-usb-audio index=-2

Now comment it out with the # symbol in front of it so that it looks like this: 

> #options snd-usb-audio index=-2

Now you need to create a file in your home directory.. to do this use your favorite editor (kate or gedit)  and use something to this extent:
> kate ~/.asoundrc.asoundconf

After kate (or gedit if you used gedit) paste the following to the file:
> 
pcm.!default {
type hw
card 1
}

ctl.!default {
type hw
card 1
}

Save the file, and exit the editor.  Now reboot your system, and you should now have system sounds.  PS be sure that you set your sound system to use alsa (if your in kde you can find this in kcontrol, in gnome you can use system>preferences>sound)

I hope this works for you guys!!

---

### Post by haiku99 on 2006-12-30
thanks very much!...got my USB speakers working w/ this, they had quit working properly when I switched from Dapper to Edgy (w/ a clean install)  FWIW I was able to leave sound preferences set to autodetect, did not have to set to ALSA, my laptop uses the the USB speakers if they are plugged in at bootup, and the internal sound card and speakers if not...

edit-  it turned out that this howto only gave a temporary fix....after I followed it the sound card assignments 0 and 1 would often toggle on boot up, so the conf file would only assign the correct default half the time.  the current assignments can be seen by typing **aplay -l** in a terminal.  I found the fix at another howto at
[http://ubuntuforums.org/showthread.php?t=205449&highlight=2+sound+card+ubuntu+problem](http://ubuntuforums.org/showthread.php?t=205449&highlight=2+sound+card+ubuntu+problem)
the trick is to assign the desired default card an index number of 0, 2nd card =1, etc  , then the assignments no longer toggle and the conf file is not required...

---

### Post by A7Bo on 2008-10-04
I LOVE you and I want to bear your children!!!!! Yeah, I'm a guy!

Thank you! After HOURS of trying to install ALSA, kernel headers, etc THIS WORKED!

BTW - I have several pieces of mutton left from the sheep that I sacrificed. Please let me know if you want any. :D

---

### Post by nc7r on 2012-12-01
This is an old thread but it was very helpful in getting a Razer Megalodon headset running on my system
actually running Debian 6.0.6 on this Dell M4400; but will use same headset on my Ubuntu Studio 64 desktop system.
Change to /etc/modprobe.d/alsa-base.conf as described produced functional audio
Thanks!

---

### Post by howefield on 2012-12-01
Old thread back to sleep.

---

