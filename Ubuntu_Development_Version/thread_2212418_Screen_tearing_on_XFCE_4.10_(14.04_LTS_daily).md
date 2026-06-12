---
title: "Screen tearing on XFCE 4.10 (14.04 LTS daily)"
date: 2014-03-21
forum: Ubuntu Development Version
---

### Post by lagre on 2014-03-21
Hey guys, I am aware that I am on an unsupported version (14.04 isn't released yet as of this writing) but I just thought I'd get some pointers on how to solve my screen tearing issue. My best bet so far was finding Compton through this link: [http://ubuntuforums.org/showthread.php?t=2144468](http://ubuntuforums.org/showthread.php?t=2144468) -- however there doesn't seem to be a 14.04 version of it available so I have no way of testing if it will help me solve my issue.

I have tried downloading the newest proprietary Nvidia driver straight from their website, installed it in single user mode and rebooted, all seems to be working fine apart from the screen tearing which is still there. Changing VLC to using OpenGL does nothing. mplayer has the same issue.

Is there a way to solve this? Should I report it as a bug? Thanks.

---

### Post by Toz on 2014-03-21
*Moving to the **Ubuntu+1** sub-forum.*

Hello and welcome to the forums.

Does enabling "Synchronize drawing to the vertical blank" in Settings Manager -> Window Manager Tweaks -> Compositor tab help?

---

### Post by ajgreeny on 2014-03-21
Compton is available in the universe repos of trusty so you can install it the normal way.  Make sure you have universe and multiverse repos enbled; job done!

---

### Post by lagre on 2014-03-21
> **Toz said:**
> Does enabling "Synchronize drawing to the vertical blank" in Settings Manager -> Window Manager Tweaks -> Compositor tab help?

This was disabled, but upon enabling it I'm not noticing a difference at all, video is still tearing in VLC. Do I need to restart the Window Manager for the settings to take effect?

> **ajgreeny said:**
> Compton is available in the universe repos of trusty so you can install it the normal way.  Make sure you have universe and multiverse repos enbled; job done!

Ah, I see. I removed the PPA and installed Compton, using the compton.conf provided in the forum thread I linked. I run ```
compton -b
``` but screen tearing is still happening.

Any ideas?

---

### Post by P-I H on 2014-03-21
I had tearing in XBMC and fixed it in this way: 
I added the line
**xserver-command=/usr/bin/X -bs -nolisten tcp**
in the file **/usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf**
After the change the file looks like this

[SeatDefaults]
# Dump core
xserver-command=X -core
xserver-command=/usr/bin/X -bs -nolisten tcp

I found the fix in the xbmc forum.

---

### Post by spsf2 on 2014-03-21
> **lagre said:**
> This was disabled, but upon enabling it I'm not noticing a difference at all, video is still tearing in VLC. Do I need to restart the Window Manager for the settings to take effect?



Ah, I see. I removed the PPA and installed Compton, using the compton.conf provided in the forum thread I linked. I run ```
compton -b
``` but screen tearing is still happening.

Any ideas?
Try this command: compton --vsync opengl (notice 2 dashes --)

This works 100% for me, always!
Hope this helps

---

### Post by QDR06VV9 on 2014-03-21
> **lagre said:**
> Hey guys, I am aware that I am on an unsupported version (14.04 isn't released yet as of this writing) but I just thought I'd get some pointers on how to solve my screen tearing issue. My best bet so far was finding Compton through this link: [http://ubuntuforums.org/showthread.php?t=2144468](http://ubuntuforums.org/showthread.php?t=2144468) -- however there doesn't seem to be a 14.04 version of it available so I have no way of testing if it will help me solve my issue.

I have tried downloading the newest proprietary Nvidia driver straight from their website, installed it in single user mode and rebooted, all seems to be working fine apart from the screen tearing which is still there. Changing VLC to using OpenGL does nothing. mplayer has the same issue.

Is there a way to solve this? Should I report it as a bug? Thanks.
It works a treat here! But if I un-install Nvidia with Compton enabled Its a bit of a pain.
So I un-install Compton, next I then reinstall my Nvidia Driver, next I Install Compton with the above method.
Reboot Good to Go! Who knows might work for you.
Regards

---

### Post by lagre on 2014-03-22
> **spsf2 said:**
> Try this command: compton --vsync opengl (notice 2 dashes --)

I get this:

```
$ compton --vsync opengl
Another composite manager is already running
Pattern "": PCRE regular expression study failed: (null)

```

It does nothing for the screen tearing :(

> **P-I H said:**
> I added the line
**xserver-command=/usr/bin/X -bs -nolisten tcp**
in the file **/usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf**
After the change the file looks like this

[SeatDefaults]
# Dump core
xserver-command=X -core
xserver-command=/usr/bin/X -bs -nolisten tcp

I tried this and rebooted, didn't work :(

Found this thread: [http://forums.linuxmint.com/viewtopic.php?f=57&t=144674](http://forums.linuxmint.com/viewtopic.php?f=57&t=144674)

That guy says that he ran ```
inxi -Gx
``` in a terminal and found that he was getting nothing for the GLX Renderer, however I get;

```
$ inxi -Gx
Graphics:  Card: NVIDIA GF114 [GeForce GTX 560 Ti] bus-ID: 01:00.0 X.Org: 1.15.0 driver: nvidia Resolution: 1920x1080@60.0hz 
           GLX Renderer: GeForce GTX 560 Ti/PCIe/SSE2 GLX Version: 4.4.0 NVIDIA 331.49 Direct Rendering: Yes
```

---

### Post by lagre on 2014-03-22
D'oh! Obviously I need to disable the current compositor first. From this link: [http://duncanlock.net/blog/2013/06/07/how-to-switch-to-compton-for-beautiful-tear-free-compositing-in-xfce/](http://duncanlock.net/blog/2013/06/07/how-to-switch-to-compton-for-beautiful-tear-free-compositing-in-xfce/)

> You’ll need to switch of any existing compositing you’ve got running, otherwise this won’t work. Unless you know differently, this will be the default one, built into the XFCE window manager, xfwm4.To switch this off, go into the Applications menu and click ‘Settings Manager’:Then click ‘Window Manager Tweaks’, then the ‘Compositor’ tab, and un-tick the ‘Enable Display Compositing’ box. Once you’ve switched off any existing compositor, you can install Compton.

After I did this, running:

```
compton --vsync opengl
```

Works just fine, so I now I guess it's just a matter of putting compton in the startup applications :) Cheers guys

---

### Post by Noxus001 on 2014-06-28
+1 man thanks. Screen tearing in Xubuntu finally fixed for me as well &#128522;

---

### Post by cariboo on 2014-06-29
With that, this thread is closed.

---

