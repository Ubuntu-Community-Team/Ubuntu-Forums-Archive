---
title: "Xubuntu screen tearing. Been an issue for me for a long time."
date: 2013-04-02
forum: Ubuntu Development Version
---

### Post by janderson91z on 2013-04-02
I have screen tearing in Xubuntu 13.04. I had the same problem in 12.04 and 12.10 but with those releases I used this work around...
[http://www.webupd8.org/2012/10/xfce-sync-to-vblank-support-for-xfwm.html](http://www.webupd8.org/2012/10/xfce-sync-to-vblank-support-for-xfwm.html)
Now, this doesn't work with 13.04. Is there a way I can get rid of screen tearing in Xubuntu 13.04? Turning off the compositing in the settings works but I would like to have compositing. I've had screen tearing in Xubuntu as long as I can remember, on multiple machines with different GPU's. Surely there has to be a solution [COLOR=#333333][FONT=Ubuntu Beta]for this.[/FONT][/COLOR]

---

### Post by screaminj3sus on 2013-04-02
its because xubuntu's compositing uses xrender which is not capable of tear free output. you need to use an opengl compositor like compiz to completely get rid of the tearing.

compiz does work with xfce here's a guide for using it in xubuntu (guide should work fine with xubuntu 13.04) [http://www.webupd8.org/2012/11/how-to-set-up-compiz-in-xubuntu-1210-or.html](http://www.webupd8.org/2012/11/how-to-set-up-compiz-in-xubuntu-1210-or.html)

---

### Post by mc4man on 2013-04-02
Well the ppa doesn't have a raring package though it's possible they will do one post release.
You could try installing the 12.10 xfwm4 package & see, it may be ok. Another possibility is just get the current xfwm4 source for 13.04, patch & build a .deb.
The slightly older patch from 2012-05-25 (vsync-4.10.0.patch) should apply cleanly to 13.04's xfwm4 source, that's likely the one the ppa used.
There is a newer patch from Dec., but that would need some slight fixing in the include glade patch for 13.04's source.
& you may have no need for the glade stuff (settings-dialogs

If I was using Xubuntu I'd certainly try either of the above before getting involved with using the current compiz mess (unless one could use a 0.8.x version

---

### Post by funeral1988 on 2013-05-11
I'm using lightweight compositor(perfect for xfce4) called compton(fork of xcompmgr), it's can xrender and opengl vsync
git: [https://github.com/chjj/compton](https://github.com/chjj/compton)
ppa: [https://launchpad.net/~richardgv/+archive/compton](https://launchpad.net/~richardgv/+archive/compton)

Use it and forget about tearing.

---

### Post by screaminj3sus on 2013-05-11
I second compton, I've recently switched to using it and its excellent. Totally removes tearing for me using  (intel), and it doesn't have to replace xfwm which is nice, and makes it feel far more integrated than compiz. take a look at this for tweaking comptons vsync: [https://github.com/chjj/compton/wiki/vsync-guide](https://github.com/chjj/compton/wiki/vsync-guide). This is the command I use to start compton on my machine: ```
compton --backend glx --paint-on-overlay --glx-no-stencil --glx-no-rebind-pixmap --vsync opengl-swc --detect-client-opacity --shadow-exclude "! name~=''" --config ~/.compton.conf -b &
```, I've found it gives me good performance and no tearing (even with multiple displays) on intel hd4000.

The only drawback I've seen with compton is that some applications don't play nice with its shadows (most are fine, only applications that do weird things with argb and xshapes are effected), so in my config I've excluded all apps I've found that had poor shadow behavior: ```
# Shadow
shadow = true; # Enabled client-side shadows on windows.
no-dock-shadow = true; # Avoid drawing shadows on dock/panel windows.
no-dnd-shadow = true; # Don't draw shadows on DND windows.
clear-shadow = true; # Zero the part of the shadow's mask behind the window (experimental).
shadow-radius = 7; # The blur radius for shadows. (default 12)
shadow-offset-x = -7; # The left offset for shadows. (default -15)
shadow-offset-y = -7; # The top offset for shadows. (default -15)
shadow-exclude = [ "n:e:Notification", "n:e:Docky", "g:e:Synapse", "g:e:Conky", "n:w:*Firefox*", "n:w:*Chromium*", "class_g ?= 'Notify-osd'", "class_g ?= 'Cairo-dock'", "class_g ?= 'Xfce4-notifyd'", "class_g ?= 'Xfce4-power-manager'"];

# Fading
fading = true; # Fade windows during opacity changes.
fade-delta = 4; # The time between steps in a fade in milliseconds. (default 10).
fade-in-step = 0.03; # Opacity change between steps while fading in. (default 0.028).
fade-out-step = 0.03; # Opacity change between steps while fading out. (default 0.03).
#no-fading-openclose = true; # Fade windows in/out when opening/closing

# Window type settings
wintypes:
{
  tooltip = { fade = true; shadow = false; };
};

```

---

### Post by edb66083 on 2013-06-28
I have been having this issue, too, for some time. I did finally find a solution, based on this post --> [http://ubuntuforums.org/showthread.php?t=1866046&p=11682072#post11682072](http://ubuntuforums.org/showthread.php?t=1866046&p=11682072#post11682072) .

I went to the thread they referenced ([http://forum.notebookreview.com/acer/480992-acer-laptop-phoenix-bios-bios-mod-request-19.html#post6368072](http://forum.notebookreview.com/acer/480992-acer-laptop-phoenix-bios-bios-mod-request-19.html#post6368072)), and found the modified bios file for my laptop, a Gateway LT31xx. The modified bios file gives you an option to select only 'UMA' rather than 'UMA+Sideport'. I flashed this new bios file, after using the correct phlash.exe command (found in the first post of the notebookreview thread), and when I rebooted, there was the option. I changed that and everything looks great --- no tearing at all. I don't know if I have 3D compositing, but I do have xcompmgr running, so I think compositing works fine.

I think this is the solution that everyone is looking for in regard to the screen tearing problem. If you have a different laptop, I would suggest searching the notebookreview thread to see if a modified bios file was created for your specific model.

---

### Post by ebyeby6 on 2013-11-06
Wow, an easy solution at last! Thanks for the tip. After trying loads of options, I added the compton ppa, installed compton, then ran it via "compton --backend glx &". It was all that was needed! Didn't need all the rest of the parameters, and for some reason, including "--shadow-exclude" wouldn't allow it to load.
It makes things a tiny bit laggier so I eventually made it run only for video playback times. All that bad tearing that I put up with for months gone in 5 minutes! :-)

---

