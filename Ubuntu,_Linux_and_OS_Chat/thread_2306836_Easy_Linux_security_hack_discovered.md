---
title: "Easy Linux security hack discovered"
date: 2015-12-19
forum: Ubuntu, Linux and OS Chat
---

### Post by rtroxel2 on 2015-12-19
[SIZE=2]Hacking into most Linux systems is as simple as pressing the backspace key 28 times, a new cybersecurity report warns...[/SIZE]

[http://www.babwnews.com/2015/12/hacking-a-linux-system-is-so-easy-a-kid-could-do-it/](http://www.babwnews.com/2015/12/hacking-a-linux-system-is-so-easy-a-kid-could-do-it/)


[http://hmarco.org/bugs/CVE-2015-8370-Grub2-authentication-bypass.html](http://hmarco.org/bugs/CVE-2015-8370-Grub2-authentication-bypass.html)

Has anyone tried this method yet?

- Roy

---

### Post by bapoumba on 2015-12-19
Please see here for some details : [https://security.stackexchange.com/questions/108428/what-is-happening-now-with-the-grub-backspace-key-security-vulnerability](https://security.stackexchange.com/questions/108428/what-is-happening-now-with-the-grub-backspace-key-security-vulnerability)

---

### Post by mystics on 2015-12-19
> **rtroxel2 said:**
> [SIZE=2]Hacking into most Linux systems is as simple as pressing the backspace key 28 times, a new cybersecurity report warns...[/SIZE]


I'd imagine that the average user who uses Linux for personal use doesn't even utilize the password option in GRUB. As a result, a lot of us probably make things a lot easier than hitting the backspace key 28 times. This is really more of a concern for multiuser systems that actually use password protection on GRUB.

Besides, as already mentioned, this has been patched in Ubuntu. Just make sure your system is up-to-date and it will no longer be so easy.

---

### Post by grahammechanical on 2015-12-19
As far as I can make out, all it does is bring up a Grub rescue prompt. I would not call getting to a Grub rescue prompt as "hacking" a Linux system. No. Not at all. For most of us, a Grub rescue prompt represent a broken Linux system.

OK. So, someone who knows what they are doing can do this
> 
An attacker which successfully exploits this vulnerability will     obtain a Grub rescue shell. Grub rescue is a very powerful shell     allowing to:          
[LIST]
[*]**Elevation of privilege:** The attacker is authenticated         without knowing a valid username nor the password. The         attacker has full access to the grub's console (grub         rescue). 
[*]**Information disclosure:** The attacker can load a         customized kernel and initramfs (for example from a USB) and         then from a more comfortable environment, copy the full disk         or install a rootkit. 
[*]**Denial of service:** The attacker is able to destroy         any data including the grub itself. Even in the case that the         disk is ciphered the attacker can overwrite it, causing a         DoS. 
[/LIST]


A Ubuntu live session is also a powerful shell. If you want to be scared, then think what could be done with an actual live running OS.  With a Ubuntu live session I could wipe Windows off of someone's hard drive and install another operating system with myself as the administrator. So, the means for doing this 

> **Information disclosure:** The attacker can load a         customized kernel and initramfs (for example from a USB) and         then from a more comfortable environment, copy the full disk         or install a rootkit.

is already freely available to anyone.

Regards

---

### Post by kansasnoob on 2015-12-19
In addition to the fact that initiating that bug required physical access to the computer it was fixed very quickly:

> grub2 (2.02~beta2-9ubuntu1.6) trusty-security; urgency=medium

  * SECURITY UPDATE: password bypass via backspace key buffer overflow
    - debian/patches/CVE-2015-8370.patch: check length before accepting a
      backspace character in grub-core/lib/crypto.c,
      grub-core/normal/auth.c.
    - CVE-2015-8370

 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Tue, 15 Dec 2015 09:11:24 -0500

---

### Post by Mike_Walsh on 2015-12-20
Just tried this in several of my 'Pups'. NOTHING happened. (And Puppy** runs** as root. (Shock! Horror!)) But then, Puppy's weird in many people's eyes. Compressed, frugal, read-only file systems and save-files/folders. Doesn't work like a **normal **Linux for a start..!

Tried it in Xubuntu as well. Again; absolutely nothing.

I hope the OP isn't of the opinion that I'm supposed to be worried about this..... :lol:


Regards,

Mike. ;)

---

### Post by kurt18947 on 2015-12-20
> **Mike_Walsh said:**
> Just tried this in several of my 'Pups'. NOTHING happened. (And Puppy** runs** as root. (Shock! Horror!)) But then, Puppy's weird in many people's eyes. Compressed, frugal, read-only file systems and save-files/folders. Doesn't work like a **normal **Linux for a start..!

Tried it in Xubuntu as well. Again; absolutely nothing.

I hope the OP isn't of the opinion that I'm supposed to be worried about this..... :lol:


Regards,

Mike. ;)

But it gave those commentards at ElReg whose livelihood seems to depend on Microsoft a reason to criticize linux and go on about its insecurity  so it was not a ***total*** waste.:p

---

### Post by Mike_Walsh on 2015-12-20
> **kurt18947 said:**
> But it gave those commentards at ElReg whose livelihood seems to depend on Microsoft a reason to criticize linux and go on about its insecurity  so it was not a ***total*** waste.:p

^^^+1..! Actually, from what I can see of it, this vulnerability would require your 'hacker' to have physical access to your machine.....or is it possible to remotely boot a computer, as well as administer it? Probably..!

(Thinking about it, I would presume it's part of this 'wake-on-lan' stuff..?)

EDIT: From what I understand, since this appears to be an attack against the bootloader rather than the kernel, I restate my first comment. The 'hacker' **would **require physical access to the machine in question; just having network access would **not** in itself be sufficient. Especially if you've pulled the plug.....


Mike. ;)

---

### Post by buzzingrobot on 2015-12-20
Someone with physical access to your machine can pretty much do what they wish, especially if you're not watching.

---

### Post by mystics on 2015-12-20
> **Mike_Walsh said:**
> Tried it in Xubuntu as well. Again; absolutely nothing.


It's already been patched, so if your computer was updated since the patch, then it wouldn't work. 

Looking at the code provided in one of the links, it wasn't exactly a hard fix either. There was just an oversight that led to programming error. It wasn't even really something many would consider a real error, just bad practice. 

> **Mike_Walsh said:**
> Actually, from what I can see of it, this vulnerability would require your 'hacker' to have physical access to your machine.....

The concern was mostly for enterprises that have multi-user systems. Apparently GRUB has a password option (which I had no idea about before seeing Welly Wu's thread about this in the Security sub-forum), and some companies take advantage of this to take better control over the booting process. Of course, the likelihood of this being exploited were slim, especially since it did require physical access to the computer. However, companies would likely not want to risk a rogue employee doing anything malicious, which is why all the flags were raised.

---

### Post by buzzingrobot on 2015-12-21
Buffer overflows, also the result of failure to check limits, are perennial bug sources. Have been for decades.

Lots of people potentially have access to the hardware:  Overnight cleaning crew, contractors, assorted visitors, etc.  If an organization really needs to *really* block physical access to its hardware, it would likely start by removing or soldering shut the unused ports on their machines, remove CD/DVD drives, roll its own wrapper around grub that uses two-factor authentication, with separate authentication to the network, control access to the server room(s),etc.

---

