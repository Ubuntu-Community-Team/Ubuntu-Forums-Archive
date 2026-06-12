---
title: "GUI Resource Requirements"
date: 2007-11-15
forum: The Cafe
---

### Post by Rick Myers on 2007-11-15
I understand a GUI on a machine uses more resources than without. That's not too hard to imagine. 

I'd like to know (using a basic Gnome installation for example);;
1) How much more in terms of percentage? 
2) Where is the major loss? Memory, CPU, Swap?
3) On a really beefy machine serving web sites, some with high bandwidth requirements, is it really that noticeable?

TIA

---

### Post by p_quarles on 2007-11-15
If you were to use the default Ubuntu desktop setup, you would be using quite a bit more resources (memory and processor) than a command line system would use. I don't have percentages, but the difference is quite large, and you would notice it.

But I'm not really sure what you're asking for. If you're trying to set up a web server, go with a CLI system or a lighter GUI (like Xfce or Openbox). Using Gnome, much less the default Ubuntu desktop settings, would be a waste of resources.

---

### Post by Darkhack on 2007-11-15
Command Line: 200mhz and 32 MB RAM with 1 GB HD
Lightweight Desktop (Fluxbox, Ice, etc): 500mhz and 96 MB RAM with 4 GB HD
Full Desktop (KDE, GNOME): 1000mhz and 256 MB RAM with 10 GB HD

If you are running a server but want a GUI for configuration, use a lightweight desktop and then just kill X when you are done configuring.  You could also install some tools that allow for remote administration with a web based interface.

---

### Post by Rick Myers on 2007-11-16
Thanks for the feedback. 

Since I'm installing on a hefty box; Dual Xeon 2.33GHz 8GB RAM 1333 MHz FSB, it appears a GUI will make little impact. However, will likely install XCFE and start/stop manually as needed.

Thanks Again!!

---

### Post by mellowd on 2007-11-16
On our dual 3ghz xeon linux machines at work we don't have a single gui in place. it isn't needed for the role you want it to do

---

### Post by Altarbo on 2007-11-16
Howdy,

I can't answer most of that, but I do know where your major loss is going to come from.  RAM is constant.  GNOME will use about 200-300 megabytes of RAM no matter what.  Your web server software, because it's so networked, will fluctuate more but still stay pretty constant.  You don't have to worry about RAM.


EDIT: I didn't notice that you posted the RAM.  8 GB is plenty RAM.  A GUI won't hurt that.

Processing is not constant.  Your software can almost always run faster.  When you have a gui, your processor is going to be side-tracked with drawing the screen.  If the web server you're setting up will usually just be running with the monitor off and no one physically using it, this won't be too big of a deal.  It doesn't take much power to draw a static image, screen saver, or blank screen.  You can also lessen the impact by getting a decent NVIDIA graphics card and running a window manager that composites (Compiz and XFCE).  Compiz and XFCE can both put most of the drawing load on the graphics card.

- Robert

---

