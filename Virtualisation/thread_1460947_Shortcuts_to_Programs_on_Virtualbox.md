---
title: "Shortcuts to Programs on Virtualbox"
date: 2010-04-23
forum: Virtualisation
---

### Post by TheSumo on 2010-04-23
Hey guys,

Been using Ubuntu for a couple months now and am in love.  I have one issue though: I want to purchase the Bible study software Logos.  Unfortunately, there is not a Linux version (and, according to the internet, there never will be).  So, I looked around and found a very nifty program called Virtualbox which seems like it will do just fine to emulate XP so that I can run Logos.  My question is this: would it be possible to create a shortcut in Ubuntu that opens my XP machine and Logos all at once?  Maybe I'm just lazy, but it is the only thing I will be running there.  Thanks in advance.

Sumo

---

### Post by tgm4883 on 2010-04-23
> **TheSumo said:**
> Hey guys,

Been using Ubuntu for a couple months now and am in love.  I have one issue though: I want to purchase the Bible study software Logos.  Unfortunately, there is not a Linux version (and, according to the internet, there never will be).  So, I looked around and found a very nifty program called Virtualbox which seems like it will do just fine to emulate XP so that I can run Logos.  My question is this: would it be possible to create a shortcut in Ubuntu that opens my XP machine and Logos all at once?  Maybe I'm just lazy, but it is the only thing I will be running there.  Thanks in advance.

Sumo

I have been wondering this as well, as this is exactly what XP mode is in Windows 7

:EDIT:

Not really an answer to your question, but have you tried running it in Wine?

---

### Post by TheSumo on 2010-04-23
I have looked into it pretty extensively (mostly because I thought virtualizing would be a pain in the rear), but it seems like no one has gotten it to work with WINE yet.  All the tests on WINE's site were garbage.  It uses .NET 3.5 heavily, which seems to be the problem (though, I am not tech-savvy enough to know why).  It seems that WINE won't be able to deal with Logos for a long time, if ever.  And it seems the makers of Logos aren't interested in making a Linux version.  So, we must resort to somewhat more complicated measures.  :D

---

### Post by pricetech on 2010-04-23
I don't think you can do what you're wanting to do, but here's an alternative;  Put a shortcut to your Logos program in the Start Up folder in windows so that it starts once windows loads.  You could even get fancy with it and create a registry entry.

You'll find that windows on a VM acts pretty much like windows on its own hardware.

Have fun.

---

### Post by TheSumo on 2010-04-23
That's a really good idea, pricetech.  I can create a shortcut of my desktop to start the virtual machine, so the startup item would boot it as soon as windows starts.  And, I know how to do that.  :D  Thanks!

---

### Post by pricetech on 2010-04-23
No problem.  Glad I could help.

---

### Post by thirdrev on 2013-03-15
I realize this is an older post, but there is a solution:

Virtual Box allows you to create a link to a virtual box; 
Open the Oracle VM VirtualBox Manager and select the install you want to create a link to (XP)
Then select "Create Shortcut on Desktop" from the "Machines" menu.

This creates a link to the virtual box on your linux desktop. 
From here you could either use the method mentioned by pricetech above - adding the program to the start-up programs list for the Virtual Windows, or 

you could also open Logos in your virtual XP and just make sure when you are done using the program you leave it open in XP and when you "close" the machine (Host+Q) make sure you save the machine state.

Wish you well in your ventures.

-Shaun
Northern-Link
[www.northern-link.com](www.northern-link.com)

---

### Post by wildmanne39 on 2013-03-17
Old thread closed!

---

