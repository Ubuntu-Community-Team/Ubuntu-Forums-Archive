---
title: "Vista uses GRUB ?!?!?!?"
date: 2008-05-18
forum: The Cafe
---

### Post by Ocxic on 2008-05-18
I'm have Vista Ultimate running in VirtualBox, and just today due to having to power off my computer without a proper shutdown, Vista gave me "Error 17 - Files not found" and dropped me to a GRUB command line interface. now it was looking for ntldr but what does this mean, is Micro$oft starting to see the light?? or was this just a subsystem of VirtualBox?

---

### Post by angryfirelord on 2008-05-18
The only versions of Vista I've seen that use Grub are hacked (usually pirated) versions to bypass the activation requirement or have dual-booted previously with Linux and then removed the menu.lst file. From what I know, Vista uses winload.exe as its boot manager.

---

### Post by Dr. C on 2008-05-18
I seriously doubt that Microsoft would be that stupid to be caught red handed as a software pirate!

GNU GRUB is licensed under GPL v2 or later, so if they included it in Vista and did not provide you with a copy of the source code or an offer valid for three years to provide you with the a copy of the source code they would be pirating GNU GRUB and that could leave Microsoft vulnerable to a multi ***billion*** dollar lawsuit from the copyright holders of GNU GRUB namely the Free Software Foundation.

---

### Post by schauerlich on 2008-05-19
> **FineE said:**
> I seriously doubt that Microsoft would be that stupid to be caught red handed as a software pirate!

GNU GRUB is licensed under GPL v2 or later, so if they included it in Vista and did not provide you with a copy of the source code or an offer valid for three years to provide you with the a copy of the source code they would be pirating GNU GRUB and that could leave Microsoft vulnerable to a multi ***billion*** dollar lawsuit from the copyright holders of GNU GRUB namely the Free Software Foundation.

Not if they kept it separate and didn't modify it. They'd just give back the same source code they used. And anyways, they wouldn't use FLOSS.

---

### Post by Northsider on 2008-05-21
Vista uses its own boot manager

---

### Post by justin whitaker on 2008-05-21
> **FineE said:**
> I seriously doubt that Microsoft would be that stupid to be caught red handed as a software pirate!

GNU GRUB is licensed under GPL v2 or later, so if they included it in Vista and did not provide you with a copy of the source code or an offer valid for three years to provide you with the a copy of the source code they would be pirating GNU GRUB and that could leave Microsoft vulnerable to a multi ***billion*** dollar lawsuit from the copyright holders of GNU GRUB namely the Free Software Foundation.

Using GRUB is not pirating. If you took GRUB, made no changes (it does not need changes to boot windows), then they could put it on every computer in the world without running afoul of the GPL. 

That said, AFL is right: only pirated copies of Vista use Grub. They have their own bootloader.

---

### Post by swoll1980 on 2008-05-21
> **angryfirelord said:**
> The only versions of Vista I've seen that use Grub are hacked (usually pirated) versions to bypass the activation requirement or have dual-booted previously with Linux and then removed the menu.lst file. From what I know, Vista uses winload.exe as its boot manager.

ha ha the threader told on him self :) I bet he feels silly right now

---

### Post by bigbrovar on 2008-05-21
i can confirm that this happened to the compaq of a friend of mine recently .. i think its a patch that can make vista work even after the 60 days trial period .. and bypass activation

---

### Post by Bungo Pony on 2008-05-21
> I seriously doubt that Microsoft would be that stupid to be caught red handed as a software pirate!

It's already happened:

[http://techrepublic.com.com/5208-11183-0.html?forumID=89&threadID=173539&messageID=1765547](http://techrepublic.com.com/5208-11183-0.html?forumID=89&threadID=173539&messageID=1765547)

---

### Post by Dr. C on 2008-05-21
> **justin whitaker said:**
> Using GRUB is not pirating. If you took GRUB, made no changes (it does not need changes to boot windows), then they could put it on every computer in the world without running afoul of the GPL. 

That said, AFL is right: only pirated copies of Vista use Grub. They have their own bootloader.

If you **distribute** or **convey** GPL software and do not provide the source code you are pirating it. In any event what this looks like is that some pirate took both Vista and GRUB and created a derived work that infringes on both Microsoft's EULA and the GPL at the same time.

---

### Post by damis648 on 2008-05-21
> **Bungo Pony said:**
> It's already happened:

[http://techrepublic.com.com/5208-11183-0.html?forumID=89&threadID=173539&messageID=1765547](http://techrepublic.com.com/5208-11183-0.html?forumID=89&threadID=173539&messageID=1765547)

Wow thats crazy...

---

### Post by klange on 2008-05-21
> **FineE said:**
> If you **distribute** or **convey** GPL software and do not provide the source code you are pirating it. In any event what this looks like is that some pirate took both Vista and GRUB and created a derived work that infringes on both Microsoft's EULA and the GPL at the same time.
Oh boy, twice as bad but with less than 1% the meaning!



Find me a copy of Vista installed supposedly OEM from a major manufacturer and maybe I'll care a bit more. If at first you don't succeed, it's not Microsoft - however, if you do eventually find one, we'll know *someone*'s breaking the law.

---

