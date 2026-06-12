---
title: "Setup DARU1 Dual Monitor with External LCD"
date: 2008-08-02
forum: System76 Support
---

### Post by Vlar on 2008-08-02
I need a little help with my daru1 laptop. I am trying to attach an external LCD monitor to the VGA port on the right hand side. The LCD key (F8) doesn't seem to do anything, although the icon on it looks like it should enable the port. After a quick reboot, I was able to get the laptop to detect the monitor, however it would only display a different resolution version of what the laptop screen displays.

Is there any way I can setup this external monitor as an extension of the desktop, displaying different things than the laptop screen? Any help would be appreciated!

---

### Post by jeamer on 2008-08-02
If you have a Nvidia graphics card, follow this:

[http://www.uluga.ubuntuforums.org/showthread.php?t=797146](http://www.uluga.ubuntuforums.org/showthread.php?t=797146)

and set it to either "seperate X screen" or "Twinview".

I find twinview is the best; your desktop will be a little messed up (some playing with your dock if you use one and the background will look a little funky) but you can drag back and forth between monitors. Hope this helps.

Edit: Sorry, forgot to say that both of the above settings will display something different than your laptop.

---

### Post by Vlar on 2008-08-02
jeamer, thank you very much for the advice, however I don't think that one is going to work for me. I should have mentioned it earlier, but the graphics card in my laptop is an Intel card (Intel GMA 950 224 MB Integrated Graphics). I did try it, even without an Nvidia card in, and it did not work, unfortunately.

---

### Post by jeamer on 2008-08-02
Hey, found it!

[http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html)

good luck!

---

### Post by thomasaaron on 2008-08-04
vlar,

Here is an old bug report in which we solved the Fn-F8 issue for the DarU1.
[https://bugs.launchpad.net/system76/+bug/116107](https://bugs.launchpad.net/system76/+bug/116107)

What version of Ubuntu are you running? This fix is actually applied with the System76 Driver. So, if you go to System > Administration > System76 Driver > Install Drivers > Install Button and then reboot your computer, you should have monitor switching.

---

