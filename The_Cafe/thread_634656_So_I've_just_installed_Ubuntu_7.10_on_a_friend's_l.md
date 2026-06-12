---
title: "So I've just installed Ubuntu 7.10 on a friend's laptop (suggestions?)"
date: 2007-12-07
forum: The Cafe
---

### Post by akiratheoni on 2007-12-07
Alright so my friend's Windows laptop had a corrupted bootup file so instead of repairing it with a Windows XP disk, he wanted me to install Linux on it. He's seen it before and we've tried installing it prior to this incident but for some reason every working disc that I've tried never booted up correctly.

But, no worry. I was able to spend more time on the laptop and for some reason had troubles booting up from the CD-ROM drive but was able to work around it and get it to boot both Ubuntu 7.10 and Linux Mint 3.1, which worked perfectly. Keep in mind this laptop has a Celeron M and is about three years old. (It has 512MB of RAM and I think an Intel915 card).

The install process was painless and I was even able to configure his Broadcom wireless card with little effort (it's awesome because I've never had to use the Restricted Drivers manager until now and it worked fine) and I've installed several programs on the laptop, like amarok, gtkpod (for his iPod) and a couple games, as well as Wine and several themes and I enabled Compiz-Fusion (which worked perfectly for me!)

But now I'm stuck. I want to make his first Linux experience as relatively painless as possible by installing most of the apps for him.

My friend won't do much other than browsing the internet, chatting online, writing papers, and maybe playing games and transferring and downloading music.

So my question to you is:

What programs could I install to make sure he doesn't have a lot of problem with his laptop? Or do you think Gutsy should work fine? (This is my first experience with a laptop; I've installed Gutsy on my desktop only before this)

What programs would be 'cool' and help show off the power of Linux? I've got Amarok and Compiz-Fusion installed and working fine already.

Thanks, guys. This community is awesome and I love you guys! :P

---

### Post by hanzomon4 on 2007-12-07
Have you tested multimedia files?

I usually setup the mediabuntu repos and install w32codecs, the packages needed for dvd playback, and totem-xine to get all of my video files to work through totem. I have to change one number in the .gnome2/Totem/xine_config  file to fix a bug with wmv files. 

change```
# priority for win32v decoder
# numeric, default: 0
**[color=red]#**[/color]engine.decoder_priorities.win32v:**[color=red]0**[/color]
```

To```
# priority for win32v decoder
# numeric, default: 0
engine.decoder_priorities.win32v:**[color=red]5**[/color]
``` 

After that all is good on the video front. Also grab all of the gstreamer plugins.

---

### Post by akiratheoni on 2007-12-07
> **hanzomon4 said:**
> Have you tested multimedia files?

Well I haven't had a chance to do so yet, but I have installed ubuntu-restricted-extras so hopefully it'll work. Thanks for reminding me, I forgot about that.

---

### Post by Drew10th on 2007-12-08
For me personally I use most of the standard apps that are installed with Gutsy. I also use frostwire and Azureus for all of my music gathering needs...only non licensed music of course...hahaha
Any way. I've found its easier to give a new user a brief introduction on how to add and remove programs and let them play with the different apps. A quick introduction to the command line and a book mark to these forums maybe a good idea to. Unless you plan on being permanent tech support.

As a side note I would recommend plugging in any extra periphials your friend may decide to use and test them as well as reboot with everything set up just to make sure there are no problems or conflicts.
 Its funny  how somtimes everything works perfect untill that 1st or second reboot.

---

### Post by Flyingjester on 2007-12-08
by chance is his lappy an hp pavilion ze4900 series?

---

### Post by il-luzhin on 2007-12-08
if flash isnt working he'll run for the hills and never comeback.  I can still hear my old roomate scoffing....

---

### Post by akiratheoni on 2007-12-08
> **Flyingjester said:**
> by chance is his lappy an hp pavilion ze4900 series?

Nah, it's a Compaq nx6110.

> **il-luzhin said:**
> if flash isnt working he'll run for the hills and never comeback.  I can still hear my old roomate scoffing....

Heh, I've tested it... Youtube works with the Gnash player, but for some reason I couldn't get the flashplugin-nonfree to work... if I were to open up a Youtube video,  Firefox wouldn't recognize it.

---

