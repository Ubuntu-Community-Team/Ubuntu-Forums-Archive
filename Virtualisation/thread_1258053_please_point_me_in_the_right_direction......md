---
title: "please point me in the right direction....."
date: 2009-09-04
forum: Virtualisation
---

### Post by 2busy19 on 2009-09-04
ok i am running ubuntu 8.10 i connect to the internet through my wifi card
here goes...

I want to run a virtual windows xp  under virualbox with internet connection! i have been searching for a while and cant seem to find the answer! also the main reason i am doing this is so i can connect and upgrade my iphone 3g to the new firmware(so i can JB it AGIAN haha) if there is an easier way to do so please let me know and if not then could someone please help me get my virtual winxp connected to the inernet so i can download itunes and have it recognize my iphone and be able to update it! thanks!! if you need to know anything else please ask i will tell u anything u need to know and incase this helps here are my computer specs....

[http://twobusy19.tripod.com/index.html](http://twobusy19.tripod.com/index.html)

---

### Post by gordintoronto on 2009-09-04
> **2busy19 said:**
> ok i am running ubuntu 8.10 i connect to the internet through my wifi card
here goes...

I want to run a virtual windows xp  under virualbox with internet connection! i have been searching for a while and cant seem to find the answer! also the main reason i am doing this is so i can connect and upgrade my iphone 3g to the new firmware(so i can JB it AGIAN haha) if there is an easier way to do so please let me know and if not then could someone please help me get my virtual winxp connected to the inernet so i can download itunes and have it recognize my iphone and be able to update it! thanks!! if you need to know anything else please ask i will tell u anything u need to know and incase this helps here are my computer specs....

[http://twobusy19.tripod.com/index.html](http://twobusy19.tripod.com/index.html)

Where are you now?  What is the problem you can't answer?

For example, if I tell you how to find Virtualbox, and you are already running it, we both waste our time.

---

### Post by 2busy19 on 2009-09-04
ok i have VB installed and i can run winXP but i do NOT have internet connection and the guest (winXP) doesnt see any of my network hardware...

** correction windows divice manager sees (under network adapters) VMware Accelerated AMD PCNet Adapter and  VMware Accelerated AMD PCNet Adapter#2**

---

### Post by gordintoronto on 2009-09-04
> **2busy19 said:**
> ok i have VB installed and i can run winXP but i do NOT have internet connection and the guest (winXP) doesnt see any of my network hardware...

** correction windows divice manager sees (under network adapters) VMware Accelerated AMD PCNet Adapter and  VMware Accelerated AMD PCNet Adapter#2**

Did you set up your network connection under XP?  It should be the same as setting it up on a Windows machine.

The adapter XP sees are virtual, but they should work just fine.  Inside Virtualbox I see the same adapters, even though the real hardware is a PCI wireless card.

---

### Post by 2busy19 on 2009-09-04
well they show up with errors like they have the little "!" next to them....

---

### Post by gordintoronto on 2009-09-07
> **2busy19 said:**
> well they show up with errors like they have the little "!" next to them....

I'm sorry, I don't know what that means.  I'm not sure what you are looking at.

---

### Post by 2busy19 on 2009-09-07
the device manger list in the winXP VM guest OS in windows that means theres errors witht that hardware...

---

