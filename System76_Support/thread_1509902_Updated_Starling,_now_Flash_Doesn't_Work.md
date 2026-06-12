---
title: "Updated Starling, now Flash Doesn't Work"
date: 2010-06-14
forum: System76 Support
---

### Post by Teasdale on 2010-06-14
I finally did the updates; I kept putting it off because I knew there'd be issues like this . . .

I went to adminstration > system 76 driver and installed that, and the WiFi works again. But Flash (YouTube) says I need additional plug-ins. When I go through the Adobe site and clicdk the download button for 9.04 APT (is that even the one I need??) nothing happens; the button doesn't do anything. I tried installing it through the synaptic package manager; I had the installer already installed, but apparently not the flash plugin, so I installed that. But still, when I go to YouTube, it says I need the latest version of Adobe Flash.

I have Ubuntu Netbook Remix 9.04, 32-bit.

---

### Post by Tart on 2010-06-15
I had similar problem after upgrade before. Check this thread see if it helps you. 
[http://ubuntuforums.org/showthread.php?t=1353102]("http://ubuntuforums.org/showthread.php?t=1353102")

---

### Post by isantop on 2010-06-15
Try running the following command from a terminal:
```
sudo apt-get remove --purge swfdec-mozilla flashplugin-*
```

Next, ensure Firefox is closed, then run:
```
sudo apt-get install flashplugin-installer
```
from a terminal. That should take care of everything for you.

---

### Post by Teasdale on 2010-06-15
> **isantop said:**
> Try running the following command from a terminal:
```
sudo apt-get remove --purge swfdec-mozilla flashplugin-*
```

Next, ensure Firefox is closed, then run:
```
sudo apt-get install flashplugin-installer
```
from a terminal. That should take care of everything for you.

It did - thank you! (This was the first thing I tried, so I never looked at the first link posted, but thank you anyway. :) )

I figured there was an easy solution; I'm not sure why it didn't come up when I did a search for it.

---

### Post by samalex on 2010-06-16
I ran into the same problem on my PanP5 running 9.04 last night.  I saw an update for both the System76 drivers and Flash, so I ran it then Flash just hung Firefox on any page that used it. 

I uninstalled then reinstalled the Flash packages and that seemed to work (thanks Teasdale for the quick notes on that), but Firefox still hangs for about 5-10 seconds on many sites, including the [Flash Test site]("http://www.adobe.com/software/flash/about/").

I had the 64-bit version of Flash installed at some point, but I'm wondering if either the update last night or some prior update may have removed it because I don't see it anymore in my Plugins directory.  

At any rate I'm just hanging tight until Adobe decides what they're going to do with 64-bit Flash for Linux because I've had little luck with both the 32-bit version via the wrapper or the Alpha 64-bit version, though the 64-bit version has always seemed more stable.

Sam

---

### Post by isantop on 2010-06-16
Can you tell me what version of the Flash Plugin Firefox reports having installed. You can go to about:plugins from Firefox to check. Screenshots of that section of the page will also be fine.

---

