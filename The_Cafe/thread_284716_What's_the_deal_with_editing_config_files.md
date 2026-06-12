---
title: "What's the deal with editing config files?"
date: 2006-10-26
forum: The Cafe
---

### Post by H.E. Pennypacker on 2006-10-26
I've never understood why we, on almost a regular basis, need to open up some random text document (configuration files), and edit them to change something.  You can take any configuration file as an example (GRUB, f-stab, etc.).

Doing this for basic computer maintenance sounds strange, and probably pre-historic.  

Don't get me wrong.  You couldn't possibly make me accept proprietary software after leaving it, but the whole "edit this config file" sounds weird, as if there's something else we could do instead.

Even if you do find GUI for a config file, often times, the GUI designer will tell you not to overly depend on GUI (e.g. the designer of Xorg GUI makes sure to stress this) as if GUI is inferior to editing those config.  Here's a solution: make GUI as reliable as the config files themselves.  

I just feel there's an alternative to doing this, and to be honest, no newbie knows how to edit a config file.  Please don't say that a newbie shouldn't be messing with config files, because everyone needs to use them (for example, for getting screen resolution problems solved).

Last, but not least, I only provided examples.  Please do not stray away from the original topic: there's gotta be something wrong with requiring people to edit config files.

---

### Post by slimdog360 on 2006-10-26
I just like the extra manipulation it give a person over a gui config.

---

### Post by aysiu on 2006-10-26
I fully agree.

Everything should be able to be done with **both** the GUI and manual editing of config files.

Until they create a GUI for ________ (fill in the blank), you're stuck with the config files.

SuSE has a GUI X configuration, and Mepis automounts all partitions and drives with the correct permissions (no need to edit the /etc/fstab file).

We're just waiting for Ubuntu to catch up on a few things.

Personally, I prefer to edit config files, but I think the option should be open to do it either way.

---

### Post by cunawarit on 2006-10-26
It would be ideal if the first thing you had to do wasn’t to edit the Xorg config file after an install. 

However, I don’t think it is weird at all to edit config files by hand, particularly when they are in XML. There’s no reason why someone shouldn’t do a nice GUI to edit something, but at the same time it is nice to be able to just use your favourite text editor.

One thing we should all be thankful about is that we have the option to edit text files, and we don’t have to use regedit.

---

### Post by IYY on 2006-10-26
As long as the GUI versions edit the files in a sane way that still allows manual configuration, I'm all for them. However, this does not appear to be the case. Look at the Gnome settings, for example. The XML config files are a mess, and no human would be able to comfortably edit them.

---

### Post by tseliot on 2006-10-26
**H.E. Pennypacker**
I do see your point. IMO Ubuntu should have something like Suse's Yast (only the control panel).

However we should be able to edit the configuration files manually.

What could we do if the Xserver failed and we could not enter our desktop environment (e.g. GNOME or KDE, etc.) to solve the problem?

The command line would be the only way to avoid reinstalling the whole system from scratch.

---

### Post by ice60 on 2006-10-26
this is a xorg.conf GUI. i haven't used it though.
[http://www.cyskat.de/dee/progxorg.htm](http://www.cyskat.de/dee/progxorg.htm)

there are repos and debs on this page -
[http://www.getautomatix.com/forum/index.php?showtopic=198](http://www.getautomatix.com/forum/index.php?showtopic=198)

---

### Post by Old Pink on 2006-10-26
I disagree. 

Think of all the options there'd have to be inside a GUI to edit /etc/X11/xorg.conf or /boot/grub/menu.lst - loads! 

I find config files so much more easy and natural to modify, completley open source. :)

---

### Post by [h2o] on 2006-10-26
> **Old Pink said:**
> I disagree. 

Think of all the options there'd have to be inside a GUI to edit /etc/X11/xorg.conf or /boot/grub/menu.lst - loads!
Eh, what? xorg.conf is kind of large and have a lot of options, but menu.lst seem to be a fairly simple file. A list of choices with a few settings. Maybe I have just missed something.

I second the opinion about config files having to be editable by the user, but I think a good GUI is nicer.

---

