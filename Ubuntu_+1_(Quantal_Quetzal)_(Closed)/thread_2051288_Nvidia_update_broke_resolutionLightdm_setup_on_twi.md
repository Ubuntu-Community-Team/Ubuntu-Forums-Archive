---
title: "Nvidia update broke resolution/Lightdm setup on twinview"
date: 2012-09-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by rolandixor on 2012-09-01
I've got a rather annoying situation, which I've tried resolving but to no avail (been a while since I've had to muck around in xorg.conf, so forgive me for seeming like a noob - I simply don't remember it all :P).

First of all, I upgraded my system to 12.10 manually (package by package) using Synaptic. Only last night, I decided (after nearly a week of running 12.10 smoothly) to upgrade my kernel, xserver, and nvidia drivers...

But!!!![-X

It seems Nvidia has decided that borking my setup is the way to go.

You see, my laptop (HP dv7 1020us) has a broken screen - and I use an external monitor (Compaq 7500 (17")) so I can actually... use the system. Due to limitations in the BIOS, I can't see anything on this external screen till X loads (urgh!!!)... and now, thanks to the updates - I can't see anything until I login!

Before, with twinview on clone mode, the CRT would use the same 1440x900 resolution as my laptop (IIRC). Also, it would be enabled when Lightdm loads, allowing me to log in on the external monitor, and choose my session, etc.

Now, I get forced to one of two resolutions (1024x768 or 1280x1024), and only the laptop screen turns on when Lightdm is loaded. Pressing the function key to enable the external screen does nothing when Lightdm is loaded :/

How can I force my system to work as it did before?

---

### Post by pqwoerituytrueiwoq on 2012-09-01
```
sudo apt-get purge nvidia-*
```also remove /etc/X11/xorg.conf
you can plug the hdd into another system to do some additional work if you have issues
if you are using a nvidia driver use a system withe a nvidia card

---

### Post by cariboo on 2012-09-01
> **rolandixor said:**
> I've got a rather annoying situation, which I've tried resolving but to no avail (been a while since I've had to muck around in xorg.conf, so forgive me for seeming like a noob - I simply don't remember it all :P).

First of all, I upgraded my system to 12.10 manually (package by package) using Synaptic. Only last night, I decided (after nearly a week of running 12.10 smoothly) to upgrade my kernel, xserver, and nvidia drivers...

But!!!![-X

It seems Nvidia has decided that borking my setup is the way to go.

You see, my laptop (HP dv7 1020us) has a broken screen - and I use an external monitor (Compaq 7500 (17")) so I can actually... use the system. Due to limitations in the BIOS, I can't see anything on this external screen till X loads (urgh!!!)... and now, thanks to the updates - I can't see anything until I login!

Before, with twinview on clone mode, the CRT would use the same 1440x900 resolution as my laptop (IIRC). Also, it would be enabled when Lightdm loads, allowing me to log in on the external monitor, and choose my session, etc.

Now, I get forced to one of two resolutions (1024x768 or 1280x1024), and only the laptop screen turns on when Lightdm is loaded. Pressing the function key to enable the external screen does nothing when Lightdm is loaded :/

How can I force my system to work as it did before?

Once you have things running, can you use nvidia-settings to set your external monitor as the first one?

---

### Post by rolandixor on 2012-09-01
> **cariboo907 said:**
> Once you have things running, can you use nvidia-settings to set your external monitor as the first one?

Yes, but it still opens applications on the laptop screen sometimes. I just want to get back the normal clone view (that actually clones!) again. Expo is acting as if I have two separate displays instead one (stretching the screen instead of cloning). It's almost as if the system is ignoring me.

---

### Post by rolandixor on 2012-09-01
> **pqwoerituytrueiwoq said:**
> ```
sudo apt-get purge nvidia-*
```also remove /etc/X11/xorg.conf
you can plug the hdd into another system to do some additional work if you have issues
if you are using a nvidia driver use a system withe a nvidia card

???

---

### Post by cariboo on 2012-09-01
> **rolandixor said:**
> Yes, but it still opens applications on the laptop screen sometimes. I just want to get back the normal clone view (that actually clones!) again. Expo is acting as if I have two separate displays instead one (stretching the screen instead of cloning). It's almost as if the system is ignoring me.

I'm not at my system with dual-monitors at the moment, but I'm sure there is an option in nvidia-settings to clone a monitor. I wonder if the compiz setting (Expo?) has something to do with it, as I haven't made any changes using compizconfig-settings-manager.

---

### Post by rolandixor on 2012-09-01
> **cariboo907 said:**
> I'm not at my system with dual-monitors at the moment, but I'm sure there is an option in nvidia-settings to clone a monitor. I wonder if the compiz setting (Expo?) has something to do with it, as I haven't made any changes using compizconfig-settings-manager.

No it has nothing to do with Compiz, because it has problems when I'm using Lightdm as well. It has to be the way that Nvidia's driver/Xrandr is managing the screens.

---

### Post by Bobhuber on 2012-09-01
None of the 304.xx drivers have worked correctly for me with dual monitors and twinview. I manually install the 295.59 driver from nvidia's site and everything works fine.

---

### Post by rolandixor on 2012-09-01
>_< installing from nvidia's site gives me no end of trouble, and it's a bad option because I can't get to a tty and install from there easily (the external monitor doesn't work once I switch to one).

---

### Post by effenberg0x0 on 2012-09-01
Every laptop I ever had has some keyboard shortcut to cycle screens between Laptop only, Laptop + External VGA, External VGA Only. People generally use it when connecting the laptop to a projector. Have you tried that?

My current one (Asus) uses Fn+F6/F7/F8 for this. Look at the icons in the top numeric keys. You can probably cycle it to "External VGA only" in order to see lightdm and login. 

Once you are logged in, you could go to ccsm / "Place Windows" and create a new rule for (any) to open on x/y coordinates 1367x0. (supposing your laptop screen resolution is 1366xSomething). That would be a very cheap trick but it does the job...

More interestingly, about /etc/X11/xorg.conf: have a look [here]("http://en.wikibooks.org/wiki/NVidia/Twin_View"), specially at the topic named "Configuring TwinView with NVIDIA's binary driver". You have a sample xorg.conf there and, a few lines below, an explanation on "TwinViewModes". The mode you want is the "Clone" mode. 

Regards,
Effenberg

**EDIT:** I forgot the obvious: If you can't view a console in this laptop, you can always SSH to it from another machine, smartphone, tablet, whatever you have at hand to do the needed changes and fix attempts.

---

