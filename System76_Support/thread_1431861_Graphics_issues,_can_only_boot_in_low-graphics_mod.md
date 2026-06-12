---
title: "Graphics issues, can only boot in low-graphics mode"
date: 2010-03-17
forum: System76 Support
---

### Post by Ibbins on 2010-03-17
My Pangolin (generally an excellent machine; I have been until now very satisfied) crashed today, and can no longer boot up normally.  It occurred while doing generally mundane tasks(internet, music, terminal), but also uninstalling Python2.6 in Synaptic.  I suspect that that's unrelated to my problem.  

Now when I boot up, after the Ubuntu icon shows up for a few seconds, I get the message, "Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure them yourself."  No options given following this message proved immediately enlightening.  After this I get the basic login and terminal.  

Typing > startx gives me a black screen with the cursor, and a restart is required.

A few hits on Google suggested that this sort of thing happens when one is trying to use new video hardware or drivers.  I have made no such changes to my machine since getting it.

I'm using a Pangolin Performance, model number panp5, 7 months old.  Graphics card is NVidia GeForce G 105M.
Using Karmic(The comp came with Jaunty)

Would be grateful for any assistance!

---

### Post by miniyak on 2010-03-17
what is the resolution stuck at?

karmic should be able to handle the 1680*1050 with or w/out the nvidia driver. So something is definitely up.

Have you tried booting in recovery mode? Recovery mode is an option at the grub boot menu when starting up. There should be one entry for each linux kernel you have installed. I would just see if booting normally in recovery works to start things out.

---

### Post by thomasaaron on 2010-03-17
> but also uninstalling Python2.6 in Synaptic. I suspect that that's unrelated to my problem. 

That probably has *everything* to do with the problem. Python 2.6 is installed by default by Ubuntu 9.10, and is used by a number of important scripts and programs.

Can you get into recovery mode and run...

sudo apt-get install python2.6

...?

---

### Post by miniyak on 2010-03-17
> **thomasaaron said:**
> That probably has *everything* to do with the problem. Python 2.6 is installed by default by Ubuntu 9.10, and is used by a number of important scripts and programs.

...?

Agreed, suspected it, and was waiting till someone more knowledgeable then I piped in.

---

### Post by Ibbins on 2010-03-17
Hi, thanks for the replies so far.

The first thing I did last night was try to reinstall python using apt-get; when I did it said that it was already on the latest version and didn't need to be updated/reinstalled.  Plus, just running Python worked, so I figured the uninstall hadn't gone through.  

Well.  I just decided it would be a good idea to remove it all the way in recovery mode and then reinstall it.  "apt-get uninstall python2.6" removed all of python's dependents(dozens of things, including system76 drivers!), too, so this comp is now basically a total mess.  

I'm gonna get myself a live CD and reinstall Karmic.  I'll post back later to let everyone know when my comp is back in business.

Edit: Full functionality restored via reinstall.  My apologies for ever thinking this was the Pangolin's fault.

---

### Post by miniyak on 2010-03-19
> **Ibbins said:**
> 

Edit: Full functionality restored via reinstall.  My apologies for ever thinking this was the Pangolin's fault.

definitely ok, glad to help. I find that one has to keep and open mind to this sort of thing. So, just blame everything then start with the simple stuff. haha

---

