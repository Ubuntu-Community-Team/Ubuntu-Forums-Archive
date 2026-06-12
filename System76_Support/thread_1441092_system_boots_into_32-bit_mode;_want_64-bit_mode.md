---
title: "system boots into 32-bit mode; want 64-bit mode"
date: 2010-03-28
forum: System76 Support
---

### Post by sds57 on 2010-03-28
I just noticed that my pangolin performance panp4n system (driver 2.4.4)
 boots in 32-bit mode:
$ uname -m
i686
instead of the 64-bit mode as I am sure it used to do.
this is a fully up-to-date system
$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

0. What did I do wrong?
1. how do I boot into 64-bit mode?
2. how do I make sure that I always boot into the 64-bit mode?

thanks

---

### Post by jdb on 2010-03-28
> **sds57 said:**
> I just noticed that my pangolin performance panp4n system (driver 2.4.4)
 boots in 32-bit mode:
$ uname -m
i686
instead of the 64-bit mode as I am sure it used to do.
this is a fully up-to-date system
$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

0. What did I do wrong?
1. how do I boot into 64-bit mode?
2. how do I make sure that I always boot into the 64-bit mode?

thanks

It boots to whatever the kernel is & the kernel is bundled with Ubuntu.
You must have the 32 bit version of Ubuntu installed.
The name of the 64 bit version contains "amd64".
The name of the 32 bit version contains "i386".

jdb

---

### Post by sds57 on 2010-03-28
> **jdb said:**
> It boots to whatever the kernel is & the kernel is bundled with Ubuntu.
You must have the 32 bit version of Ubuntu installed.
The name of the 64 bit version contains "amd64".
The name of the 32 bit version contains "i386".
Yes, sure.
So, how did it happen that my Ubuntu became i386 all of a sudden
and how do I turn it back to amd64?
specifically, which packages do I install?
"aptitude search linux.*amd64" returns nothing.
my kernel is 
linux-image-2.6.31-20-generic
Linux kernel image for version 2.6.31 on x86/x86_64

---

### Post by Vrekk on 2010-03-28
> **sds57 said:**
> Yes, sure.
So, how did it happen that my Ubuntu became i386 all of a sudden
and how do I turn it back to amd64?
specifically, which packages do I install?
"aptitude search linux.*amd64" returns nothing.
my kernel is 
linux-image-2.6.31-20-generic
Linux kernel image for version 2.6.31 on x86/x86_64

If you have 32, then can't just "upgrade" to 64 bit, you will have to download a 64 bit iso, burn it and install from there.

And the reverse is true as well, you can't go from 64 bit to 32 bit, so you must have started there.

---

### Post by sds57 on 2010-03-29
> **Vrekk said:**
> If you have 32, then can't just "upgrade" to 64 bit, you will have to download a 64 bit iso, burn it and install from there.

And the reverse is true as well, you can't go from 64 bit to 32 bit, so you must have started there.
This is not true.
As I said, I used to have 64-bit, but, apparently, during a major upgrade, got switched to 32-bit. I never installed from an iso, I always upgraded via internet.

---

### Post by Eldera on 2010-03-29
[quote=sds57]$ uname -m
i686[/quote]

Isn't this 64 bit? 

Sorry, I am just learning this stuff and this doesn't make sense to me.

---

### Post by Sef on 2010-03-29
> Quote:
 	 	 		 			 				 					Originally Posted by **Vrekk** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9043232#post9043232") 				
 				[I]If you have 32, then can't just  "upgrade" to 64 bit, you will have to download a 64 bit iso, burn it and  install from there.

And the reverse is true as well, you can't go from 64 bit to 32 bit, so  you must have started there.[/I]
 			 		 	 	 
This is not true.
As I said, I used to have 64-bit, but, apparently, during a major  upgrade, got switched to 32-bit. I never installed from an iso, I always  upgraded via internet.

What vrekk said is correct.  A system cannot upgrade or downgrade from a 32-bit to a 64-bit system, nor from a 64-bit to a 32-bit system.   An upgrade would only affect the packages that are being upgraded.

---

### Post by Sef on 2010-03-29
> Isn't this 64 bit? 

Sorry, I am just learning this stuff and this doesn't make sense to me.That is a 32-bit system.   If you have a 64-bit system, you will see this: x86_64 or AMD64.  The latter is technically the correct name.

No need to apologize.  Better to ask and learn, than to not ask and remain ignorant.

---

### Post by sds57 on 2010-03-29
> **Sef said:**
> What vrekk said is correct.  A system cannot upgrade or downgrade from a 32-bit to a 64-bit system, nor from a 64-bit to a 32-bit system.   An upgrade would only affect the packages that are being upgraded.
OK. So, what exactly do I need to do to restore my system to the 
`uname -m`=x86_64
state?
please?

---

### Post by marshmallow1304 on 2010-03-29
> **sds57 said:**
> OK. So, what exactly do I need to do to restore my system to the 
`uname -m`=x86_64
state?
please?

[http://releases.ubuntu.com/9.10/](http://releases.ubuntu.com/9.10/)
Get the "64-bit PC (AMD64) desktop CD", burn to CD, backup your data, install.

---

### Post by Eldera on 2010-03-29
sds57, I hope you will forgive me, I am not trying to hi-jack your thread, but I think I can learn something if I can understand what is happening to you. 

I looked up 'uname -m' in the man pages and that said it would print the machine *hardware* name. I am guessing that means the processor.

Wouldn't this just change your software:
[quote=marshmallow]Get the "64-bit PC (AMD64) desktop CD", burn to CD, backup your data, install.[/quote] 
Those are the instructions to do a clean install of your operating system. I have done that a few times.

If "uname -m" is a *hardware* name, I don"t think that would change it.

Am I right that the terms "32 bit" and "64 bit" can be applied to either processors or the Operating Systems software being run on them?

Are you trying to figure out what type of hardware you have or what operating system you are using?

If I am out of line being curious about this thread, just don't answer me.

Good Luck with what ever you are trying to work out. Eldera

PS How much RAM do you have? I read in Keir Thomas Pocket Guide that unless you had a minimum of 4GB of Ram that you did not get the full advantage of a 64 bit OS. I have run my Pang with both the 32 bit and the 64 bit OS and it did not make any visible difference. If everything else is working well, why worry which OS is on it?

---

### Post by marshmallow1304 on 2010-03-29
> **Eldera said:**
> Am I right that the terms "32 bit" and "64 bit" can be applied to either processors or the Operating Systems software being run on them?

Yes.  64-bit processors are backward-compatible - they can run both 32-bit and 64-bit operating systems.  32-bit processors cannot run 64-bit operating systems.  'uname -m' gives the architecture of the operating system.

---

### Post by Eldera on 2010-03-30
Thank you. I understand now. The man page was confusing me. Have a great day.
Eldera

---

