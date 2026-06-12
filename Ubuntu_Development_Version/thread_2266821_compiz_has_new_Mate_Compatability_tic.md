---
title: "compiz has new Mate Compatability tic"
date: 2015-02-25
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-02-25
Just wondering why my *installed* Mate desktop will not work.. and ...

---

### Post by v3.xx on 2015-02-25
Are you saying the mate plugin interferes with themes?

---

### Post by ventrical on 2015-02-25
> **v3.xx said:**
> Are you saying the mate plugin interferes with themes?

It is more like a compiz conflict. I am running Mate, the desktop install .. not the standalone iso.

---

### Post by Cavsfan on 2015-02-26
Hmm... I do not have the Mate desktop installed but yet I see that option in CCSM.

Guess it just comes default.

---

### Post by raptir on 2015-02-26
> **Cavsfan said:**
> Hmm... I do not have the Mate desktop installed but yet I see that option in CCSM.

Guess it just comes default.

Yeah, it is included in one of the compiz-plugins packages. Just like you'll always see GNOME/KDE compatibility available even if you're running a different DE.

---

### Post by ventrical on 2015-02-26
Running the Mate DE on top of Ubuntu is in really bad shape .. but it is still workable. I had probls with 14.10. Once bit , twice shy? :)lol

Regards..

---

### Post by mc4man on 2015-02-26
> **ventrical said:**
> Running the Mate DE on top of Ubuntu is in really bad shape .. but it is still workable. I had probls with 14.10. Once bit , twice shy? :)lol

Regards..
I'd think if one wants mate then better to install from mate image. The 15.04 image inc. compiz though it has to be user enabled 
(- unless one likes horizontal tearing then compiz seems best bet to alleviate 

The mate image also inc. vlc by default but doesn't inc. any vdpau or vaapi libs, probably they should do like xubuntu in that regard. 
(- try to find vdpau or vaapi libs in software-center...

---

### Post by Cavsfan on 2015-02-26
> **mc4man said:**
> I'd think if one wants mate then better to install from mate image.

+1 Indeed.

---

### Post by raptir on 2015-02-27
I've run into a few issues with keyboard/mouse focus when using Compiz instead of Marco. I'm not sure if it's a setting or a bug. The primary issue is that if I use a keyboard shortcut to open a menu, for example I have assigned Ctrl-Esc to open the Advanced MATE Menu, the menu opens **behind** the window that currently has focus and does not grab keyboard focus. If I use the mouse to click the menu button the menu grabs focus correctly.

---

### Post by mc4man on 2015-02-27
> **raptir said:**
> I've run into a few issues with keyboard/mouse focus when using Compiz instead of Marco. I'm not sure if it's a setting or a bug. The primary issue is that if I use a keyboard shortcut to open a menu, for example I have assigned Ctrl-Esc to open the Advanced MATE Menu, the menu opens **behind** the window that currently has focus and does not grab keyboard focus. If I use the mouse to click the menu button the menu grabs focus correctly.
You could try this, no harm in setting as shown  as it should be the default but isn't as no one seems to be running the desktop asylum  
In ccsm > general options > focus & raise > set focus prevention .. to off (log out/in to test

---

### Post by v3.xx on 2015-02-27
I wonder why compiz is now part of default install.

---

### Post by Cavsfan on 2015-02-27
> **raptir said:**
> I've run into a few issues with keyboard/mouse focus when using Compiz instead of Marco. I'm not sure if it's a setting or a bug. The primary issue is that if I use a keyboard shortcut to open a menu, for example I have assigned Ctrl-Esc to open the Advanced MATE Menu, the menu opens **behind** the window that currently has focus and does not grab keyboard focus. If I use the mouse to click the menu button the menu grabs focus correctly.

> **mc4man said:**
> You could try this, no harm in setting as shown  as it should be the default but isn't as no one seems to be running the desktop asylum  
In ccsm > general options > focus & raise > set focus prevention .. to off (log out/in to test

Thanks for finding that. On one of my systems I can't recall which right now every time I open a window it's behind all of the current windows.
That might just fix that problem. I can only tell it opened as it displays in the bottom panel of FB.

> **v3.xx said:**
> I wonder why compiz is now part of default install.

I'm pretty sure Unity is a compiz plugin but I could be wrong.

---

### Post by mc4man on 2015-02-27
> **v3.xx said:**
> I wonder why compiz is now part of default install.
I guess the Ubuntu mate team would know. I'd think because it's then simpler for any ubuntu mate user, just enable using compiz in the settings.
I'd also guess that many mate users would want to use compiz for various reasons, I mentioned one before. (vsync

---

### Post by Cavsfan on 2015-02-27
Oh my bad. I thought **v3.xx** was talking about the default install not the Mate default install.

---

### Post by Cavsfan on 2015-02-27
CCSM won't open up to change the windows keyboard/mouse focus. Even after a reboot.

But it is indeed this install that has that problem of windows opening behind other windows.

---

### Post by raptir on 2015-03-02
> **mc4man said:**
> You could try this, no harm in setting as shown  as it should be the default but isn't as no one seems to be running the desktop asylum  
In ccsm > general options > focus & raise > set focus prevention .. to off (log out/in to test

Awesome. With that off it fixes all my issues. Didn't have to log out to test it, by the way. I can toggle it back and forth and observe the behavior change.

> **v3.xx said:**
> I wonder why compiz is now part of default install.

I imagine there are a couple reasons. First, it's probably a fairly common option to want. MATE is lighter than Unity/GNOME3, but many people choose MATE because they want a full-featured GTK based desktop environment with a traditional interface and not because they want something lightweight. They give you a nice basic configuration that works well in MATE and provides all of the "bells and whistles" you'd expect from a modern window manager, while setting it up yourself is not necessarily easy for new users.

And when it comes down to it, adding Compiz only amounts to around 20MB of additional packages even if you install all the extra plugins. If 20MB is that much of an issue, I'd imagine you'd be running something significantly lighter weight like Lubuntu or even avoid Ubuntu-based distros altogether.

---

### Post by Cavsfan on 2015-03-02
> **mc4man said:**
> You could try this, no harm in setting as shown  as it should be the default but isn't as no one seems to be running the desktop asylum  
In ccsm > general options > focus & raise > set focus prevention .. to off (log out/in to test

This was on Trusty that I had the problem of windows opening behind other windows. I had Firefox open and opened terminal and gedit and they were both behind Firefox.
I changed the setting to off and that fixed it instantly. 

I also set this up on Vivid and I believe it helped that too. But I just changed it back to normal and terminal opened behind Firefox. So it definitely is reproducible.

Thanks again!

---

### Post by Cavsfan on 2015-03-06
Installed Mate beta1 and all compiz packages were pre-installed. It would have been nice if CCSM was pre-installed as well since that is a major necessity. 

But, once installed CCSM had a lot of the options already selected.

The cube is looking good! ;)

Default fairly transparent bottom and top.
[[IMG]http://en.zimagez.com/miniature/screenshot5e589f292b6ba779d9422df3f69e260c.png[/IMG]]("http://en.zimagez.com/zimage/screenshot5e589f292b6ba779d9422df3f69e260c.php")

---

