---
title: "Virtual Box and Windows XP"
date: 2008-04-19
forum: Security Discussions
---

### Post by syga on 2008-04-19
I have Ubuntu 7.10. 

I just install virtualbox with Windows XP Pro. With the help of this forum, everything works perfectly so far. The only thing I'm concerned about is the usual Windows virus issues. 

If I catch a Windows virus or any sort of spyware, can it work its way out of the virtual machine and damage my Ubunutu installation?

I don't believe it can, but I would just like a second opinion...

---

### Post by prshah on 2008-04-19
> **syga said:**
> 
If I catch a Windows virus or any sort of spyware, can it work its way out of the virtual machine and damage my Ubunutu installation?


Short answer; No. 

Long answer.. The "virus" (nowadays, more trojans than virii) cannot really jump out of your virtual box unless you have networking enabled between the host and the guest OS. Even then, linux is a totally different ball game and there are no dual virii that work on both Windows and Linux. In fact, there are only a few linux virii and none in the wild.

Having said that, if you get some password stealing trojan installed in your Virtual Box and then you access your bank website or something in that virtualzed XP, it WILL steal your password. Using ubuntu to access the site will be safe in any case.

---

### Post by Oldsoldier2003 on 2008-04-19
and the nice thing about running xp as a virtual machine is you can make a copy of your vdi when the machine is in a stable state and store it someplace safe. When disaster or virus strikes just replace the vdi with your backup.

---

