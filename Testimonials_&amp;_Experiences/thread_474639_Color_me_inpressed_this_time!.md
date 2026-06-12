---
title: "Color me inpressed this time!"
date: 2007-06-15
forum: Testimonials &amp; Experiences
---

### Post by whiteguysamurai on 2007-06-15
I've been a dedicated Microsoft drone for near to twenty years now, i have had to stick with it's less than stellar years to it's now, somewhat better days of NTFS.
I have been talked into trying linux from the days of knoppix, that came as a live CD with one of the PC magazines i was into.
It was somewhat elusive, always a few features from being an alternative to whatever windows i was using at the time.
I have tried it from time to time, and even left a scathing remark on the very forum, each time ending the same way, back to windows.

But this time, after trying puppy linux and getting to like the experience, i gave feisty fawn a go.

Very impressive, i can see mark is getting very serious about ubuntu, and if it were not for the following faults, i would install it and only look back when i need to photoshop/game.

I was somewhat shortchanged on the resolution, my radeon 9800 was not capable of displaying the full 1600x1200 @85 like it does in windows.

And it refused to behave with the vista boot loader (i know it's still virgin territory, and should be capable in future releases).

Everything else was quality, and i very much enjoyed  the codec downloads and debi.

I have high hopes for gutsy, i think if these two things can be repaired, windows and ubuntu will be living on my system in harmony.

Good job!:D

---

### Post by vexorian on 2007-06-15
I am not sure if you really need such a freaky big resolution, but if you do then the reason for that resolution is probably the lack of some restricted driver, for nvidia I used the package manger as far as I can see there are also ATI driver packages.

I have no experience about the "vista boot boot loader" . I got a question, did you find it hard to recover the vista booting?

---

### Post by wolfen69 on 2007-06-15
welcome. first off those 2 things are easily fixed. as far as dual booting, just use 2 physical drives. when installing an OS, just make sure that the other drive is unplugged.this way, both drives wont mess with each other. most bios's now have a "quick boot selector"(usually F12) button, so you wont have to go into the regular bios everytime to choose a boot order.

as far as resolution is concerned, a quick search in the forums(or ask a question) should yield an answer within minutes, since this is a common issue.

consider yourself lucky if those are the only 2 "problems" your having. i wouldn't even call them problems. it's a part of setting things up. having a little patience pays off big.

---

### Post by whiteguysamurai on 2007-06-15
> I got a question, did you find it hard to recover the vista booting?

Normally i would just pop in the vista DVD and repair it, a snap:p
But this time i just reloaded.

I like my freaky high resolution, i have an uncommonly large CRT, and i like it that way.

If i were better at these kinds of things, i might give it a go again.
But i'm sure gutsy will have fixed all my issues.

---

### Post by vexorian on 2007-06-15
> **whiteguysamurai said:**
> Normally i would just pop in the vista DVD and repair it, a snap:p
But this time i just reloaded.

I like my freaky high resolution, i have an uncommonly large CRT, and i like it that way.

If i were better at these kinds of things, i might give it a go again.
But i'm sure gutsy will have fixed all my issues.
Yeah I understand, too bad about windows making things harder again with this upgrade. Perhaps later we'll be able to allow the user to install the restricted drivers through a single option in the installation.

---

### Post by Anonii on 2007-06-15
Weird, sir, I have the option of selecting 1600x1200 as a resolution.
 Let me try something.

 First of all, break your virginity and open the terminal (Alt+F2, and then execute "gnome-terminal"). The file you are about to edit, xorg.conf, is the file which configures your X server ( [http://en.wikipedia.org/wiki/XOrg](http://en.wikipedia.org/wiki/XOrg) ). So, backup it with the following commands (A backup is always useful):
**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup**
and now run the autodetect script again (which will edit your xorg.conf, in a cute and nice graphical way), with the following command:
**sudo dpkg-reconfigure xserver-xorg**
You will have to find the resolution options (It's not that tough, from what I remember from the last time I did it) and enable the 1600x1200 one. Then save your settings, and kill your X server (Ctrl+Alt+Backspace) (Don't do it if you are running something important). After your login, you should be able to select 1600x1200 as your resolution.. or not.

---

### Post by wolfen69 on 2007-06-15
just a question whiteguy. why would you expect linux to have EVERYTHING work out of the box? i repair windows machines for a living, and can tell you that most pc's require ALOT of configuring to get windows 100% up and running. why are people so willing to configure a windows box, but not linux?

---

### Post by wolfen69 on 2007-06-15
also, if you're the lazy type, you might wanna try sabayon linux. it auto-mounts every drive, has every codec built in, and you wont have to lift a finger. if you want easy, there you go.

---

### Post by whiteguysamurai on 2007-06-15
> Weird, sir, I have the option of selecting 1600x1200 as a resolution.
Let me try something.

First of all, break your virginity and open the terminal (Alt+F2, and then execute "gnome-terminal"). The file you are about to edit, xorg.conf, is the file which configures your X server ( [http://en.wikipedia.org/wiki/XOrg](http://en.wikipedia.org/wiki/XOrg) ). So, backup it with the following commands (A backup is always useful):
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
and now run the autodetect script again (which will edit your xorg.conf, in a cute and nice graphical way), with the following command:
sudo dpkg-reconfigure xserver-xorg
You will have to find the resolution options (It's not that tough, from what I remember from the last time I did it) and enable the 1600x1200 one. Then save your settings, and kill your X server (Ctrl+Alt+Backspace) (Don't do it if you are running something important). After your login, you should be able to select 1600x1200 as your resolution.. or not.

Should i do this after getting the restricted driver?
Also, the restricted seems to fix the refresh problem, so maybe that's the best choice.

I am debating installing XP again so i can just plow through this and bust my cherry (so to speak)..

Though, the plushness of vista does seem nice, maybe i should just wait for gutsy to iron out the vista boot thing before wasting everyone's time.

I'll let you know.

---

### Post by whiteguysamurai on 2007-06-15
> just a question whiteguy. why would you expect linux to have EVERYTHING work out of the box? i repair windows machines for a living, and can tell you that most pc's require ALOT of configuring to get windows 100% up and running. why are people so willing to configure a windows box, but not linux?

I'm a lazy windows user, the less i have to fiddle with the better.
While it's true in the past i have had to do much downloading to get windows up to speed, the packages are installable and easy to find...Though with vista ultimate i only had to install my video driver and that was it...but that's besides the point.

I will say that, as my title implies, i am rather impressed this time and feel if i knew more about it, and that includes playing with the vista boot loader, i would have it on now.
As the other thing, seems easy enough for someone with some free time to fix.
Feisty is VERY full featured compared to edgy, so much so that i think it's almost a replacement that a windows guy like me could use.

Also, if gutsy is compat with the boot loader, it will be on my system.
I still like windows, but i'm also getting to like Ubuntu.

---

### Post by whiteguysamurai on 2007-06-15
> also, if you're the lazy type, you might wanna try sabayon linux. it auto-mounts every drive, has every codec built in, and you wont have to lift a finger. if you want easy, there you go.

No, i feel ubuntu is very close to being the distro of choice for me, though i might see how they work around the vista boot loader.


Thanks for your time.

---

