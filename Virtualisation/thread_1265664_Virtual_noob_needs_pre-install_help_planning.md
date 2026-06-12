---
title: "Virtual noob needs pre-install help planning?????"
date: 2009-09-13
forum: Virtualisation
---

### Post by kansasnoob on 2009-09-13
I've been studying quite a bit the past few days, read the stickies, wore out Google, etc. So I know just enough to be dangerous!

I should probably say that I previously followed one of these guides:

[http://www.howtoforge.com/the_perfect_desktop_ubuntu7.04_p5](http://www.howtoforge.com/the_perfect_desktop_ubuntu7.04_p5)

(I think I followed the one for Gutsy however), to make my original Win XP into a virtual machine when I first found Ubuntu, but I found that a dual boot was a better fit for me at that time.

It did seem to work fairly well however, but that was a year and a half ago. Now I seldom use XP, and I'm changing hard drives anyway, so this seems like a good time to give a virtual machine another try.

So on with the questions:

#1: Which to use? I've pretty much narrowed it down to VMware or VirtualBox, but consider the next question:

#2: OK, I know it's possible to use VMware Converter:

[http://www.howtoforge.com/vmware_converter_windows_linux](http://www.howtoforge.com/vmware_converter_windows_linux)

to basically clone my existing XP to VMware server. OTOH I've not yet found a way to clone that same existing XP partition to a VirtualBox vm setup :confused:

So, is there a way of cloning an existing XP partition to a new VirtualBox install? Remember I'll be changing drives anyway, so if I were just copying some existing partitions to the new drive (I'll not be copying all anyway) I'd simply use the latest Gparted Live CD to copy and paste the desired partitions.

Thanks in advance for your patience! And expect more stupid questions:D

---

### Post by kansasnoob on 2009-09-15
Shameless bump :)

---

### Post by Ms_Angel_D on 2009-09-15
I recommend Virtualbox as far as virtualization tools.

But what exactly are you trying to virutalize, Windows or Linux?

---

### Post by pricetech on 2009-09-15
Any reason you can't do a fresh install of XP in a virtual machine ??  Seeing as how winders tends to take on lots of excess baggage as it gets used you'd be better off if that's an option.

I'm running Hardy on both a desktop and a laptop using VirtualBox OSE which came from the repo to virtualize XP.  It just plain works in both scenarios.

---

### Post by kansasnoob on 2009-09-16
I ended up using VirtualBox using this guide:

[http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

Seems to have gone off without a hitch so far.

Seems to even run fairly fast, faster than I recall the old VMware setup running.

Thank you!

---

