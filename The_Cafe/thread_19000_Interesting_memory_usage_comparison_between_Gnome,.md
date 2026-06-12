---
title: "Interesting memory usage comparison between Gnome, KDE, and Blackbox"
date: 2005-03-09
forum: The Cafe
---

### Post by landotter on 2005-03-09
OK, this is really unscientific, but rather interesting and fun. :P

I logged into a fresh session of KDE, Gnome, and a tweaked Blackbox, ran an Xterm, the Gimp (for screencapture), and Gnome-System-Monitor, and then took a screenshot of the results. 

KDE and Gnome were set up pretty standard, except for personal panel positions and icons. KDE had the clipboard applet running. Gnome had the modem lights applet fired up. No other wierd tweaks. KDE was wearing default Plastik, and Gnome was in casual Clealooks.

BlackBox was accented with a number of processes which added 10mb more to it's usual memory draw. Things such as the Gnome-settings-daemon, chbg, and three dockapps were fired up. I did this because most people do add things to the spartan managers--making them actual, erm, environments. :D

Ignore the processor usage, as I was dragging windows about, I don't think it's fair to consider in this instance. ;)

** Blackbox** (with add-ons):89.6mb memory 35mb swap
[http://photos7.flickr.com/6225048_75c7c7bf11_o.jpg](http://photos7.flickr.com/6225048_75c7c7bf11_o.jpg)

Before I fired up the dockapps and other processes, a stark naked Blackbox idled with gsm fired up at 74mb.


** KDE: **110mb memory 24mb swap
[http://photos5.flickr.com/6225050_1cd0acba01_o.jpg](http://photos5.flickr.com/6225050_1cd0acba01_o.jpg)



** Gnome: **133mb memory 19.4mb swap
[http://photos7.flickr.com/6225047_5e175433da_o.jpg](http://photos7.flickr.com/6225047_5e175433da_o.jpg)



quite interesting.

This doesn't say that one environtment is better than the other, it just puts some interesting numbers into the equation.

I'm not a big fan of KDE's style, but I have great admiration of how efficient it can be when you use KDE/qt apps with it. A good choice for some lower end boxes. Fire up Kword with KDE running and it only adds 4mb to the suckage. Fire up OOo within Gnome and you'll need 12mb more (these are rough numbers from my box YMMV) Use Kword with Gnome and it adds another 9mb to the monitor if the qt libs weren't already loaded.

Just some random thoughts on the silly Desktop Environment war.  :p

I've been pretty hard on KDE since I quit using it a couple years ago--and I still think Konqueror is a lousy file manager for the regular guy--complexity does not equal superiority--but I used it a bit today and saw some nice things. The KDE printing framework is brilliant. I could easily make borderless prints with my Canon. There is not a single Gnome program that can do this. As I was using Gwenview to print it--I cursed to myself, that though the printing was painless and brilliant--the UI sucked cabbage compared to gThumb and GQview.

Getting defensive about one or the other is natural since we see our own selves reflected in our choice and tend to take things too seriously. We personalize criticisms of our choice of UI. Pretty absurd, eh? LOL

Anyhow, just some random typings for thought. I wouldn't mind something with the lightfeeling of Blackbox, the thoughtful simple UI of Gnome, and the smart underbelly of KDE.

:)

---

### Post by TravisNewman on 2005-03-09
From what I've heard, you can't really trust gnome-system-monitor for memory usage and the like. I'm not sure exactly why, I can't remember the reason that was posted here, but there's something quirky about it. Same goes with any system monitor for Linux as far as I know

I would like to know how you define "fresh" in this instance. Did you log out of GDM, restart GDM, or restart the machine totally? I've noticed that logging out of Gnome AND killing GDM still leaves some Gnome processes running, or at least leaves something from them in memory. A few times I've had problems with settings not showing up in Gnome when I changed them, and killing GDM and killing everything that looked related to Gnome didn't fix it-- I still had my old settings, no matter how many times I tried to change them. But rebooting fixed it and when Gnome loaded it had my latest settings. This means something was still lingering in memory. I've had similar issues with KDE and XFCE, so I imagine that COULD have affected your memory stats if you didn't clean reboot.

---

### Post by landotter on 2005-03-10
I didn't clean reboot, but did kill gdm and checked top for "hangers on" :P

I know you can't trust Gnome-system-monitor for individual apps, but I was looking at the total MB used which should be rather accurate.

For example, I just started Firefox and Openoffice writer in addition to what I mentioned. Total memory usage is now 128mb (I'm in Blackbox).  That's only about 40mb more for both Firefox and Openoffice, two hefty apps. Looking at them as individuals, they're sucking 200mb--but much of that's shared or "allocated" as far as I know.

I'm curious to what the memory suck would be for XP with Firefox and Openoffice up. I might have to reboot and check. :P

---

### Post by shame on 2006-05-01
Try using top in a terminal.  I get much, much higher readings.  And fluxbox uses more than gnome on my comp.

---

### Post by fuscia on 2006-05-01
i've been using kde lately and got concerned when one of the superkaramba system monitors (world renown for their deadly accuracy) said i was using 235mb (out 0f 256) ram. conky showed i was only using 160mb. the eventual explanation was that the former monitor was including disk cache. (just thought i'd mention that.)

---

### Post by ssam on 2006-05-01
do those ram used figures include disk cache?

---

### Post by hizaguchi on 2006-05-01
I just don't trust the Linux ram-o-meters at all any more.  The DE system monitors are definately way off, but I think even "top" and "free -m" get confused and report things incorrectly.  I say this because I've got Arch and Ubuntu dual booting, and as unscientific as it may be, I can't tell a really big difference in running alot of apps on one vs the other, even though the system monitors tell me that Ubuntu is using like 50 megs of swap and Arch isn't even touching it.  And like someone above said, the monitors say Fluxbox uses WAY more memory than I know it should... around 60 megs for me, where I can run it on Arch with 18 megs.  I've been trying to figure out what makes that huge difference, and I've just decided that it doesn't really exist and the monitoring apps are crazy.

---

