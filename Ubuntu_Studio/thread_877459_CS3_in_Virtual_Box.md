---
title: "CS3 in Virtual Box?"
date: 2008-08-01
forum: Ubuntu Studio
---

### Post by MasterNetra on 2008-08-01
With my specs would CS3 products run well in virtual box with my labtop's specs? (See signture) If so would the default settings work for in regards to ram usage?

---

### Post by jaon on 2008-08-01
Hi there.

I've been running Adobe CS3 Production in Virtualbox at home.  My hardware specs are pretty similar to yours, the only difference being the RAM.

The amount of RAM the virtual machine will need will depend on the software you want to use.  The graphics / web apps (photoshop, illustrator, flash) will run on 512 apparently, but Adobe recommends 1024.  The video apps (premiere, encore, after effects) really need at least 2GB, and that's just for the virtual machine.  And you want to leave at least 512MB for Ubuntu, more if possible.

I had 2GB of RAM, running Ubuntu and an XP Virtual Machine with 1GB or RAM.  That ran Adobe CS3, but a bit slow.  With 4GB, I've given 2GB to the virtual machine, and Adobe CS3 works really smoothly.  So I'd definitely recommend going to at least 2GB of RAM, and more if you can.  Your laptop can support 4, it just depends how much money you have.

All your other specs look fine to me.

[Adobe requirements]("http://www.adobe.com/products/creativesuite/production/systemreqs/")
[Intel Specs]("http://compare.intel.com/pcc/showchart.aspx?mmID=28117,28116&familyID=7&culture=en-US")

---

### Post by Linja on 2008-08-01
You shouldn't really be using 64 bit with "only" 1024MB, certainly not if you also intend to virtualize. Remember that 64 bit eats more memory.

---

### Post by MasterNetra on 2008-08-02
Only problem is i am on a LABTOP i can't upgrade my ram at least i don't think so >.>

And my processors are 64bit. Going to 32bit would slow my system considerably. AT least my system was much more slower when i had Hardy 32bit some time ago >.>

Of course i gots another question... Sense CS3 can be ran both in mac and windows it begs the question should i virtualize OSX (x86) or Windows XP?

---

### Post by MasterNetra on 2008-08-02
Well i got the adobe CS3 Master collection installed on my WinXP Pro in VirtualBox. I have half of my ram dedicated for it. Which is alright sense my ubuntu only uses about 310-330mb of ram for normal operations prehaps less sense i was using the system monitor for its reading :p But it all runs not as fast as it would if i could dedicate the 1gb to it but meh as long as it works i just need it for college.

---

