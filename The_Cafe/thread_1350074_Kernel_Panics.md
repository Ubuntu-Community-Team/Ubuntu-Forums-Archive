---
title: "Kernel Panics"
date: 2009-12-08
forum: The Cafe
---

### Post by Marvin666 on 2009-12-08
How many of you have experienced a kernel panic under ubuntu yet?
-edit: I haven't had one so far, even in an extremely buggy wubi, running on top of an even buggier vista.

---

### Post by Psumi on 2009-12-08
I may have had one, but only through a virtual machine, Vbox would crash, causing a kernel panic ONLY for it. The rest of the desktop would be fine.

---

### Post by FuturePilot on 2009-12-08
In the 3½ years I've been using Ubuntu I've only had 2 kernel panics.

---

### Post by Simon17 on 2009-12-09
Wubi does not "run on top of" Vista.

---

### Post by cariboo on 2009-12-09
I haven't seen a kernel panic since I stopped compiling my own kernels back in the 2.4 version.

---

### Post by user1397 on 2009-12-09
I only had one, and it was under Arch

---

### Post by Frak on 2009-12-09
> **Marvin666 said:**
> -edit: I haven't had one so far, even in an extremely buggy wubi, running on top of an even buggier vista.

Great, considering it doesn't run "on top of" Vista.

---

### Post by hoppipolla on 2009-12-09
Under Ubuntu, never, not as far as I remember :)

I think I used to get them on Slackware but I was compiling my own kernels back then and all that jazz, so I probably just made mistakes! :)

---

### Post by iponeverything on 2009-12-09
I have had lots.

But then again, I have admin'ed at least a few hundred Linux machines since '95.

---

### Post by SunnyRabbiera on 2009-12-09
Just twice, however both were caused by Dreamlinux when I gave it a spin

---

### Post by Crunchy the Headcrab on 2009-12-09
Never.

---

### Post by Marvin666 on 2009-12-09
Whatever the correct term for a wubi install is.

---

### Post by Simon17 on 2009-12-09
Wubi doesn't give a rat's *** what other OS you're using. All it does is loop mount the file system.

You could even completely delete Vista completely and it would still run fine as long as you left the Wubi dir, bootloader and boot.ini alone.

---

### Post by l-x-l on 2009-12-09
Ummm... how can I tell when a kernel panic occurs??? (serious question)

---

### Post by Simon17 on 2009-12-09
You'll know.

---

### Post by Zoot7 on 2009-12-09
I got a few with Jaunty after a kernel patch broke my sound among other things. Upgraded to 2.6.30 and that solved that.

I also got one using a custom kernel I compiled myself under Slackware a few years back.

---

### Post by t0p on 2009-12-09
> **l-x-l said:**
> Ummm... how can I tell when a kernel panic occurs??? (serious question)

It starts to sweat, fidget, its heartrate increases... (serious answer :p )

---

### Post by FuturePilot on 2009-12-09
> **l-x-l said:**
> Ummm... how can I tell when a kernel panic occurs??? (serious question)

The lights on your keyboard will blink. (Capslock, numlock, scroll lock) And most likely it will freeze up at the same time.

---

### Post by dragos240 on 2009-12-09
Many times. I have been trying to configure my own kernel, with all the hardware on my computer, it's really hard to find the right box to tic. Genkernel works okay, but my wireless is not detected.

---

### Post by sandyd on 2009-12-09
about 6-7 for karmic
but i guess i deserve it cause i used the beta as soon as it got out.
now, ive only had one....

---

### Post by Isengrin on 2009-12-09
Just one, because I had an error in my custom kernel. Got fixed quicky. \o/

Never with Arch's stock kernel, BTW.

---

### Post by RiceMonster on 2009-12-09
Been using Linux for 2 years and haven't had one yet.

I've also only gotten a blue screen once.

---

### Post by Marvin666 on 2009-12-09
Too many blue screens to count...

---

### Post by Frak on 2009-12-09
> **Marvin666 said:**
> Too many blue screens to count...
I sense humor on your breath. I've had a bluescreen maybe twice in eight years. I've had around ten kernel panics in the same eight years.

---

### Post by hoppipolla on 2009-12-09
> **carlee said:**
> about 6-7 for karmic
but i guess i deserve it cause i used the beta as soon as it got out.
now, ive only had one....

Yeah maybe it's the beta thing, but that's still quite a few ._.  I mean I never saw one on Jaunty or on Karmic, to be honest I don't know if I've seen one since I started running Ubuntu a couple of years ago, and I do sometimes use betas.

Do you have any very unusual drivers running in the kernel or anything that might cause it to fall over? Do you use the standard builds?

---

### Post by hoppipolla on 2009-12-09
> **Frak said:**
> I sense humor on your breath. I've had a bluescreen maybe twice in eight years. I've had around ten kernel panics in the same eight years.

Maybe this proves everyone has different experiences, as I side with Marvin.

Weird kernel builds or weird drivers can theoretically cause problems although again it has been years and years since I have seen a real kernel panic as far as I can remember.

---

### Post by Chame_Wizard on 2009-12-10
Only 1 so far: October 2007.

:guitar:

---

### Post by LinuxFanBoi on 2009-12-10
I've had many, but only because I tried an experimental driver for my wifi adapter on my laptop.  Got a stable driver now.

---

### Post by duesergirl on 2010-01-09
I hadn't had any before, and didn't know what it was when it happened.  I started searching and that's when I found this thread.

Mine happened after I had installed my new printer (HP Deskjet D1660) and printed a couple of pages to make sure it was working.  Everything printed fine.  I walked away for a moment to make some coffee and my boyfriend was going to get online while I did that.  When he walked over to the computer he saw that everything was locked up and the Caps and Scroll Lock lights were flashing.

On some of the other threads I looked at, they said hardware changes and overheating can cause the kernel panic.  I guessing it was installing the printer that did it, since it has never happened before.  The only thing I've ever changed in my kernel is to add "mem=512m" to get the darn thing to boot up in the first place.  But I've had to do that since I switched to Ubuntu last fall and it never panicked on it before.

If anyone else has this printer or has any tips that I should try to prevent it from locking up every time I use the printer, I would appreciate it.  Sorry I don't have any other info posted about the computer; I'm not very technically minded.  #-o

---

### Post by NCLI on 2010-01-09
I've had quite a few, usually due to either bad hardware or a mistake on my part, though I have had a few I still don't understand to this day.

---

### Post by SuperSonic4 on 2010-01-09
One which was traced to a stick of poorly installed stick of RAM (which is now working)

---

### Post by squilookle on 2010-01-09
I had one under Arch in a Virtual machine. Otherwise, not that I know of or can remember.

---

### Post by k64 on 2010-01-09
I have, personally, had 1 kernel panic in Mint, but that's about it. Oh, and the kernel panic involved upgrading "linux-image" without updating the modules. Bad move all along, now that I know how the kernel works.

---

### Post by magmon on 2010-01-09
I caused one in mint by installing drivers unsupported by the kernel. Freaking developers... Why'd they give us freedom?

/sarcasm

---

### Post by k64 on 2010-01-09
> **magmon said:**
> I caused one in mint by installing drivers unsupported by the kernel. Freaking developers... Why'd they give us freedom?

/sarcasm

[url='http://ubuntuforums.org/showpost.php?p=8638549&postcount=33']The reason why I got a kernel panic in Mint is because I updated the kernel image - and the image only.

Now that I read kernel build instructions out of an old book that I have, I know that the kernel image and the modules have to be updated in sync - or they will be incompatible and cause a kernel panic.[/url]

---

### Post by Redundant Username on 2010-01-09
Note to everyone: A BSOD is a kernel panic.

---

### Post by magmon on 2010-01-09
> **k64 said:**
> [url='http://ubuntuforums.org/showpost.php?p=8638549&postcount=33']The reason why I got a kernel panic in Mint is because I updated the kernel image - and the image only.

Now that I read kernel build instructions out of an old book that I have, I know that the kernel image and the modules have to be updated in sync - or they will be incompatible and cause a kernel panic.[/url]

The sarcasm I was referring to was about the developers =P.

---

### Post by Eisenwinter on 2010-01-10
I have never had a kernel panic in any Linux distro that I've used.

---

### Post by CharlesA on 2010-01-10
On my "production" server, I haven't had any problems.

Altho, I did get dumped into a maintenance shell a couple times when I was testing a script in VirtualBox, I still haven't figured out what caused that, but it didn't happen on the live machine. *shrugs*

---

### Post by The Toxic Mite on 2010-01-10
I haven't had any kernel panics ever.
 
That's all. [noparse]:p[/noparse]

---

### Post by Marvin666 on 2010-01-11
My first kernel panic(s)!!!
I was attempting a dual boot with karmic, and it locked up. This force me to do a hard reboot. Karmic seems more unstable, and it looks as if it corrupted it's / partition. It gave me a kernel panic and stated unable to mount root. I tried again and got the same message. Recovery mode also gives a panic, but with different message, but to the same effect.

---

### Post by Vignesh S on 2010-01-11
In my year and a bit of using Ubuntu, I've never had a kernel panic.

---

### Post by madnessjack on 2010-01-11
Got a few in Jaunty Studio when trying to get the RT kernel patched for nVidia binaries but never had any problems with Karmic or Karmic Studio

---

### Post by Exodist on 2010-01-11
I hate these polls!

I had to choose multiple, but I have only had 2 in the past 6 years or longer. They were due to bad ram and one video card.

---

### Post by Hallvor on 2010-01-11
I`ve had several, but always because of failing hardware.

---

