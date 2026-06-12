---
title: "Missing power and network indicators from Gnome panel"
date: 2010-02-22
forum: System76 Support
---

### Post by bill516 on 2010-02-22
Machine:  PanP4 w/nvidia graphics
Distro:  Ubuntu 9:10 on Grub2 w/ 2.6.31-19-generic.
Gnome is 2.28.1

Add Bill to the people with the misbehaving power indicator on the Gnome panel.  Note that my default setup is to always show a battery indicator on the panel.  This has worked quite nicely.

I have been using my Pangolin PanP4 with Ubuntu 9.10 through the day today and it has been behaving normally, which is to say quite well.

I normally run this machine on AC power because its battery life is short.

So a few moments ago I restarted the machine after being away for a time and I had two battery symbols on the panel but no Network Manager symbol.  Odd.

One battery symbol seemed to behave normally the other did nothing.  So I tried to remove the inoperative symbol and wound up removing both!  Not good, especially when I could not get the "real" one back.

Power Management Preferences no longer shows any tab at all for battery power.  This appears to have nothing to do with the presence or absence of the battery.  There is no battery tab in Power Management Preferences with or without the battery.  I have checked "Always display an Icon on the "General" tab.  There is no icon being displayed.

Next we have to deal with the fact that when two battery icons showed up on the panel the Network Manager icon disappeared.  I did discover that my wireless connection was behaving normally, which I did by using Preferences/Network Connections.

My biggest problem?  I am at a loss as to what caused this and consequently I do not know how to fix it or avoid it.  Do I have some reinstalling to do and if so what?

If I missed something Tom, can you tell me what it is?  :confused:

---

### Post by ajgreeny on 2010-02-22
Make sure you have the **Notification Area** in your panel, as both icons (and many others) sit in that now, not separately.
If that is no help, try stopping the nm-applet with ```
killall nm-applet
``` in terminal and then restart it again with Alt+F2 *nm-applet*.
You may need to do the same for the battery icon but I have a desktop, so can't help with that.

---

### Post by bill516 on 2010-02-23
> **ajgreeny said:**
> Make sure you have the **Notification Area** in your panel, as both icons (and many others) sit in that now, not separately.
If that is no help, try stopping the nm-applet with ```
killall nm-applet
``` in terminal and then restart it again with Alt+F2 *nm-applet*.
You may need to do the same for the battery icon but I have a desktop, so can't help with that.
Thanks for trying aj, but no luck.  I apparently have to start it again some other way.  Earlier I did remove both applets and reinstall them, but that also did not work.  Really no idea what is going on.

---

### Post by thomasaaron on 2010-02-23
I'm not clear about whether or not you verified that you have the notification applet installed. It contains both the power management and the wireless icons.

Right-click on your upper panel and select "Add to Panel." Then scroll down and find the "Notification Area" applet and add it.

Did that work?

---

### Post by bill516 on 2010-02-23
My apologies to you and ajgreeny.  So those things are in a "notification area"?  Well OK, next time I blow them out -- however I do that -- I'll try to remember that.

Since they had been sitting up there minding their own business (actually, my business!) I assumed that my "notification area" was installed?

Ah well, I'll go make some tea.  I understand my teapot!

And thanks again to you, Tom!  And you ajgreeny!

---

### Post by carlosve.ucv on 2010-04-30
SOLVED!!!
It was the "Notification Area" that was deleted. The odd thing of two batterys happend to mee too!!!


Regards,
Carlos

---

