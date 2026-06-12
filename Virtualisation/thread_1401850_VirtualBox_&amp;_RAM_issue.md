---
title: "VirtualBox &amp; RAM issue"
date: 2010-02-08
forum: Virtualisation
---

### Post by fogelfink on 2010-02-08
I have a strange issue running VirtualBox 3.1.2 (Sun's version, not OSE) and the amount of RAM I can allocate to my virtual machines:
My computer has 6GB of RAM (I am running Ubuntu 9.10, 32-bit with a PAE kernel, so the 6GB are recognised by the system).  The problem is that I am only able to allocate 2.56GB RAM to any virtual machine I want to create (I tried several operating system options).  Where can I change that maximum RAM setting?  I ran Sun's VB on fedora 10 before and it showed the max. RAM allocation @ 6GB.  I want to give my virtual machine 4GB of RAM - the linux host should be fine with the remaining 2GB while I run the virtual machine.
Why does that seem impossible in Ubuntu, or better, where can I change those settings for VirtualBox?

---

### Post by pirateghost on 2010-02-08
Why not just run 64bit ubuntu?

---

### Post by OliW on 2010-02-08
Even with PAE, applications have 32bit address limits. That might not be the cause here but you'd do the computer justice letting it run in 64bit mode.

It's not as wild as it used to be.

---

### Post by fogelfink on 2010-02-09
> **OliW said:**
> Even with PAE, applications have 32bit address limits. 

Only in Ubuntu?  
As I said, it worked fine running fedora 32-bit on the same machine.  VirtualBox gave me the 4GB of RAM I wanted to allocate to the virtual machine.

I have a couple of applications that I want to run, which only got 32-bit versions!  Therefore I am asking once again:
Where can I change the settings of VB regarding the RAM allocation?  For even if there were a 32-bit address limit, it should be 4GB and not 2.56GB.

---

### Post by pirateghost on 2010-02-09
> **fogelfink said:**
> 
I have a couple of applications that I want to run, which only got 32-bit versions!
what applications are they?  have you tried to run them under 64bit OS?  most applications that are 32bit only will happily run under 64bit


aside from that i dont know of any settings that you can change in VBox to allocate more ram.  its either there or it isnt as far as i know.

---

### Post by fogelfink on 2010-02-11
there is one application (lightzone), which i use for photo editing, which has no 64bit version and i tried running it on a 64bit fedora, which did not work.  so much for the switching to 64bit - i don't want to do that!

Now my question once again:

why does VirtualBox on fedora 32bit pick up on my RAM and it doesn't on ubuntu? maybe i should switch back to fedora then...

---

### Post by OliW on 2010-02-11
Again, I know I'm not fixing the direct issue but LightZone doesn't need a 64bit version as it runs on Java - You just need Java and OpenJRE has a x86_64 version.

Proof it works: [http://i.thepcspy.com/oli/lightzone.jpg](http://i.thepcspy.com/oli/lightzone.jpg)

I'm not pushing this because I want to annoy you but PAE is a far worse solution to native 64bit.

---

### Post by fogelfink on 2010-02-16
> **OliW said:**
> Again, I know I'm not fixing the direct issue but LightZone doesn't need a 64bit version as it runs on Java - You just need Java and OpenJRE has a x86_64 version.

Proof it works: [http://i.thepcspy.com/oli/lightzone.jpg](http://i.thepcspy.com/oli/lightzone.jpg)

I'm not pushing this because I want to annoy you but PAE is a far worse solution to native 64bit.

Thanks for that - I switched to 64bit and everything works fine!  VirtualBox gets the 4GB RAM and lightzone works as well (I tried it about a year ago on 64bit and back then it didn't work and the developers said I needed the 32bit environment).

---

