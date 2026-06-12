---
title: "Pangolin Performace Battery"
date: 2008-11-13
forum: System76 Support
---

### Post by Lee_Machine on 2008-11-13
I was wondering if a battery life of 1hour and 30 minutes to 2hours is about the norm for this laptop.

I have all the battery saving apps running such as downclocking the CPU to 1.20GZ and keep screen brightness down to 60%. I have my HDD turn off when not used. I have my CD-ROM drive unmounted when not in use.

Pretty much each tweek I could think of and that gave me about 30 minutes more of use.

I even have all desktops effects turned off as to not use the GPU so much.


Any suggestions on more I could do?

Also, is there a 9-12 cell battery I can get for this Laptop? The model being panp4n

Thanks,

---

### Post by thomasaaron on 2008-11-14
Yes, that is normal battery time.

Something else you can do, if you haven't already, is to download and run powertop. You have to run it as root from a terminal. 

At the bottom, it will offer various suggestions for killing un-needed services. Along with the other things you mentioned, it might be helpful.
```

sudo apt-get install powertop
sudo powertop
```

Currently, there are no other battery options for this model. But there may be in the future.

---

### Post by Modax42 on 2008-11-14
> **Lee_Machine said:**
>  I have all the battery saving apps running such as downclocking the CPU to 1.20GZ and keep screen brightness down to 60%. I have my HDD turn off when not used. I have my CD-ROM drive unmounted when not in use.

Can you tell me how I can set these tweaks up? (other than the brightness, which is self-explanatory)  I have a Darter Ultra and would very much appreciate an extra half hour of battery life!

---

### Post by thomasaaron on 2008-11-14
This is a bit concise, but here goes...

Go to System > Prefs > Power Management and set your screen brightness for battery operation.

Right click on the upper panel. Select "Add to Panel". Scroll down to CPU Frequency Scaling Monitor. Click the add button. Add two of these to your panel. Set one to CPU0 and one to CPU1. *Left* click the applet to set your CPU frequency.

From a terminal run these commands. They will install and start a utility that monitors your power usage. It will occasionally suggest a key you can press to shutdown unnecessary services.
```
sudo apt-get install powertop
sudo powertop

```

Let me know if I need to add details.

---

### Post by jdb on 2008-11-14
> **Modax42 said:**
> Can you tell me how I can set these tweaks up? (other than the brightness, which is self-explanatory)  I have a Darter Ultra and would very much appreciate an extra half hour of battery life!

I get about 3.5 hours on my Daru2 with full brightness & no battery saving tweeks.

What do you get ???

Thanks,

jdb

---

### Post by Modax42 on 2008-11-14
I get about 100 minutes with the 4 cell battery and 200 minutes with 8 cell battery, with minimum brightness, quiet mode on, and wireless and bluetooth off.  Obviously something is not kosher, otherwise sys76 wouldn't be advertising 3.5 hours for the 4-cell.

I put two CPU frequency monitors on my panel, and set them to CPU 0 and CPU 1.  But when I left-click on the monitor, nothing happens, and I cannot set the CPU frequency.

The help file for the monitor says that 

The Frequency Selector functionality may not be available
      on your GNOME Desktop by default. Please consult your system
      administrator, vendor documentation, or the documentation that came with this software.

What do I need to do to enable the frequency selector?

---

### Post by thomasaaron on 2008-11-14
Should be enabled by default.

I just tested it on our shop Darter (DarU3), and it worked fine.
Sorry to ask this, but are you sure you are left-clicking the applet (i.e. with your index finger, not your middle finger). It should produce a little sub-menu with some radio-buttons.

What CPU do you have?

---

### Post by Modax42 on 2008-11-14
Nope.  Left Clicking repeatedly on the the applet icon on the top panel (which reads 2.27 GHz) does absolutely nothing.  Right Click and I can choose from Preferences, Help, about, etc.  Left mouse button works for everything else.

I have the Core 2 Duo P8400, one of the new 45nm centrino 2 processors.

---

### Post by thomasaaron on 2008-11-14
That's definitely strange.
I'm using the same CPU.

Follow this tutorial and see if it helps...
[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

---

### Post by Modax42 on 2008-11-14
Uh-oh. This is bad.

I followed the tutorial and was able to set my processor speed down to 1.6GHz.  As soon as I did so, however, my wireless connection died, and would not come back.

So I booted up Intrepid Ibex from USB.  Same story, no wireless networks detected in the vicinity whatsoever.  Usually I see dozens of neighboring networks.

So I booted up my Compaq laptop, thinking that there must be an internet outage in my area.  But, much to my horror, I am able to connect to the internet on my compaq easily.

Did I fry my wireless card somehow?  Doesn't make sense, since the applet only lets you decrease the clock speed.  The only selectable speeds are 2.27 GHz and 1.60 GHz.  This is freaking me out.

---

### Post by thomasaaron on 2008-11-14
I doubt the problems are related.

Try following these instructions.

To fix your /etc/network/interfaces file, go to a terminal
(Application > Accessories > Terminal) and enter the following command:

sudo gedit /etc/network/interfaces

This will launch a text editor with the interfaces file opened in it.

In this file, put a comment (#) in front of EVERY line of the file
EXCEPT for these two lines:

auto lo
iface lo inet loopback

Click SAVE on the text editor and reboot your computer.
It should now boot faster and connect to networks more easily.

NOTE:
Unless you are dealing with static IP addresses (which is pretty rare for the
general end-user) you should NOT establish a network connection by going to
System > Administration > Network.

Instead, you should connect to the Internet using the Network Manager icon
in the upper right corner of your screen (the one that looks like a little
computer monitor).

---

### Post by Modax42 on 2008-11-14
What a relief.  Network manager is behaving properly now after following these instructions.  what do you think the problem was?

---

### Post by thomasaaron on 2008-11-17
Sounds like you were configuring your networking via System > Admin > Networking. That hoses the interface file. This problem existed in Edgy/Feisty. I've not seen it for a while, though. It's popped up several times in Intrepid, though.

---

### Post by jpoRS on 2008-11-18
> **Lee_Machine said:**
> Also, is there a 9-12 cell battery I can get for this Laptop? The model being panp4n

I just wanted to let System76 know that Lee isn't the only one interested in a 9-12 cell battery.  Even though I get a good 2.5 hours on mine with Compiz, 80% brightness, and a handfull of programs running, I still wouldn't say no to more power once this battery stops holding a charge.

jim

---

### Post by abulluck on 2008-11-18
I'll chime in too on wanting an extended battery for the pangolin.

---

### Post by thomasaaron on 2008-11-18
Thanks guys.

Just wanted to let you know that I have asked our procurement guys to find an larger battery for the Pangolin.

I'll keep you posted.

---

