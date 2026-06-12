---
title: "I'm the hacked guy"
date: 2011-04-10
forum: Security
---

### Post by rkrider on 2011-04-10
Sorry all, I can't get respond through normal channels, all I can use is my phone. My keyboard is disabled. My PC is pretty much a paper weight. Both of them. The only way they could be getting in is through the wifi. I don't know if there is anything I can do. My recovery programsare not accessible. Even onstartup. Is it possible to clear the hard drive another way? I've heard fire purifies, I couldn't get another disc to boot up to reinstall ubuntu. Please text me any ideas, but please be specific with command lines, I have trouble with all the () and / [ and where they go. The # is -snip- thanks for the help

---

### Post by CharlesA on 2011-04-10
Sounds like a hardware problem to me. There are no open ports on a default install of Ubuntu.

If it's only the keyboard that isn't working, I doubt that it's a hacker.

---

### Post by dgw on 2011-04-10
Try plugging in a USB keyboard to see if that works. Borrow one from a friend if you have to.

---

### Post by Madskillzz on 2011-04-10
> **rkrider said:**
> Sorry all, I can't get respond through normal channels, all I can use is my phone. My keyboard is disabled. My PC is pretty much a paper weight. Both of them. 
 

You have 2 and can't get in bios or boot from cd using usb keyboard

---

### Post by sweet pea on 2011-04-11
I'm the hacked guy 2.  I currently have a black hat that has already written custom code tailored to my hardware, they have been owning my systems since Thanksgiving 2010 & I have already returned 3 new laptops that got hacked.

I'm pretty sure they altered the entire bios program so far. The only thing I can do is boot from Ubutnu 10.04 Live cd.  Not any windows opertaing systems or any other version of linux for the matter.

Just yesterday they had to have flashed my bios with a new update.  Now when I use synaptic package manager or command line to try to install anything, I get the following error message

**Selecting previously deselected package ndiswrapper-common. ***(or any package for that matter) *
[B](Reading database ...  dpkg: unrecoverable fatal error, aborting:
unable to open files list file for package 'pulseaudio-module-bluetooth' : Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)[/B]

Regardless of any package I try to install, the error is always**  unable to open files for package 'pulseaudio-module-bluetooth'.**


I can't install anything.  Not even flashrom to try to flash the bios from ubuntu linux.   I used to have other network cards and graphic cards in my box, I had to take them all out. If I try to boot from a usb drive or any sata or ide hard drive - I get a bios error saying there is no bios at all.

Not only did they do that.   They also hacked my Cisco business 851w router, my linksys wrv210, and Verizon fios Actiontec MI424-WR, all to have open ports or some type of rootkit for my devices to connect to them as soon as I connect to the internet. I  I already returned 2 fios routers back and got replacements.   I would do things like configure the security setting and block as many ports as possible.  10 minutes later I would have several random ports open that don't even come on by default in the routers. 



I even called the FBI & IC3 about this and they really don't care. They told me I am not an important business or anything to threaten the nation. L0L0L0L... 

What to do? other than throw away the box or reserve it for computer forensics?

---

### Post by 3rdalbum on 2011-04-11
> **sweet pea said:**
> I'm the hacked guy 2.  I currently have a black hat that has already written custom code tailored to my hardware, they have been owning my systems since Thanksgiving 2010 & I have already returned 3 new laptops that got hacked.

I'm pretty sure they altered the entire bios program so far. The only thing I can do is boot from Ubutnu 10.04 Live cd.  Not any windows opertaing systems or any other version of linux for the matter.

Just yesterday they had to have flashed my bios with a new update.  Now when I use synaptic package manager or command line to try to install anything, I get the following error message

**Selecting previously deselected package ndiswrapper-common. ***(or any package for that matter) *
[B](Reading database ...  dpkg: unrecoverable fatal error, aborting:
unable to open files list file for package 'pulseaudio-module-bluetooth' : Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)[/B]

Regardless of any package I try to install, the error is always**  unable to open files for package 'pulseaudio-module-bluetooth'.**


I can't install anything.  Not even flashrom to try to flash the bios from ubuntu linux.   I used to have other network cards and graphic cards in my box, I had to take them all out. If I try to boot from a usb drive or any sata or ide hard drive - I get a bios error saying there is no bios at all.

I even called the FBI & IC3 about this and they really don't care. They told me I am not an important business or anything to threaten the nation. L0L0L0L...

Probably the reason why they don't care is because they think your story is highly improbable, and that you're confusing hardware problems or software errors with "an evil genius hacker". They'd be right, too.

If you're been running an Ubuntu CD, then there's really no way any attacker can get in. Ubuntu doesn't listen to any incoming ports by default. Your BIOS cannot be "reflashed" without seriously in-depth knowledge about your computer's internals; basically, anyone smart enough is probably earning in excess of a hundred dollars an hour and has better things to do than to make your life a misery. Also, the error message you posted is not a symptom of a BIOS problem, it's the symptom of a hard disk that's dying, or a bad RAM stick. And before you ask, no, it's not something that an attacker could cause remotely.

Basically, I think this "black hat hacker" doesn't exist. You might want to see your doctor about the paranoia, though.

Yours is about the latest in a string of a dozen similarly impossible stories about people being targetted by evil genius hackers, who can hack into computers as soon as they are booted, just for the fun of causing error messages to appear. If anyone really had a vendetta against you and could hack into your computers, they'd already have opened several credit cards in your name and a bunch of mobile phone plans. That's what the *real* evil hackers do.

---

### Post by dfreer on 2011-04-12
> **sweet pea said:**
> I'm the hacked guy 2.  I currently have a black hat that has already written custom code tailored to my hardware, they have been owning my systems since Thanksgiving 2010 & I have already returned 3 new laptops that got hacked.

I'm pretty sure they altered the entire bios program so far. The only thing I can do is boot from Ubutnu 10.04 Live cd.  Not any windows opertaing systems or any other version of linux for the matter.

Just yesterday they had to have flashed my bios with a new update.  Now when I use synaptic package manager or command line to try to install anything, I get the following error message

**Selecting previously deselected package ndiswrapper-common. ***(or any package for that matter) *
[B](Reading database ...  dpkg: unrecoverable fatal error, aborting:
unable to open files list file for package 'pulseaudio-module-bluetooth' : Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)[/B]

Regardless of any package I try to install, the error is always**  unable to open files for package 'pulseaudio-module-bluetooth'.**


I can't install anything.  Not even flashrom to try to flash the bios from ubuntu linux.   I used to have other network cards and graphic cards in my box, I had to take them all out. If I try to boot from a usb drive or any sata or ide hard drive - I get a bios error saying there is no bios at all.

Not only did they do that.   They also hacked my Cisco business 851w router, my linksys wrv210, and Verizon fios Actiontec MI424-WR, all to have open ports or some type of rootkit for my devices to connect to them as soon as I connect to the internet. I  I already returned 2 fios routers back and got replacements.   I would do things like configure the security setting and block as many ports as possible.  10 minutes later I would have several random ports open that don't even come on by default in the routers. 



I even called the FBI & IC3 about this and they really don't care. They told me I am not an important business or anything to threaten the nation. L0L0L0L... 

What to do? other than throw away the box or reserve it for computer forensics?

You have a serious problem, in that you are extremely paranoid that "hackers" are responsible for your problems, which are entirely likely from misconfigured software.

Returning laptops because they have a virus or were hacked is not the right solution. At the very worst, you may need to wipe your hard drive.

You have to realize that the skills needed to actually do some of the things you think are happening are extremely rare, and someone possessing these skills would simply not be interested at risking his own exposure simply to hack your box. Even if he did, once he got in your box he's got everything he can get from you, why would he keep trying to hack in? 

Furthermore, someone of this skill would be literally invisible to you. **IF** for some reason a highly skilled hacker did get your box, let's say to use it to further his hacking goals, he would do one of the following:
(1). Patch the hole he came in on, so that other hackers don't get in (the competition). He might even shore up some defenses on your system, make it stronger (after all, it's his system now). 
(2). Secure a communications port just for himself, a very tight secure connection that looks like a normal system process. 
(3). Delete all evidence he was even on your box. Delete log files, remove/patch tools that reveal his existence, use little memory/cpu when you are logged in so that you don't notice him.

Hackers without these skills, rash ones, and/or would just trash your box for fun. Money scammers would simply scan for credit card numbers and move on. You should be able to see now that it's entirely unlikely that you are being hacked, rather that you are just confusing normal computer hardware/software and your own computer inexperience and blaming it on a hacker.

And returning hardware to stop hackers? Please don't do this, you need to learn what is going wrong and learn to fix it yourself, especially if you are going to use linux. It's not the "Be all end all" perfect OS that is totally stable that everyone make it out to be. It **can** be, but that's generally only after you spend a much of time fixing the little broken bits.

---

### Post by ChrisWells on 2011-04-12
I think this guy is trolling

---

### Post by EJeanmaire on 2011-04-12
:popcorn: More please.

---

### Post by Skaggz on 2011-04-16
Either we have a troll here, or 3rdalbum hit the nail on the head with:
> Basically, I think this "black hat hacker" doesn't exist. You might want to see your doctor about the paranoia, though.

---

### Post by kseise on 2011-04-16
This is really simple to diagnose.  Do a fresh install with the system unplugged from the internet.  Keep it offline for 48 hours but use the system and see what happens.  If you get the same sorts of error messages, either you have flaky hardware, or your hacker is a ghost.  If the hacker is a ghost, pray that it is not a poltergeist.  Those are really hard to get rid of.  I saw the documentary with Craig T. Nelson.

---

### Post by Skaggz on 2011-04-16
> **kseise said:**
> This is really simple to diagnose.  Do a fresh install with the system unplugged from the internet.  Keep it offline for 48 hours but use the system and see what happens.  If you get the same sorts of error messages, either you have flaky hardware, or your hacker is a ghost.  If the hacker is a ghost, pray that it is not a poltergeist.  Those are really hard to get rid of.  I saw the documentary with Craig T. Nelson.

I saw the same documentary, scary stuff.  OP, make sure your computer isn't connected to the TV right now!!!

---

### Post by usatonycuba on 2011-04-17
> **kseise said:**
> .........or your hacker is a ghost.  If the hacker is a ghost, pray that it is not a poltergeist.  Those are really hard to get rid of.  I saw the documentary with Craig T. Nelson.
I peed in my pants laughing :lol::lol:

---

### Post by mrcollinz on 2011-04-17
You're the "Cracked" guy, also if it's strictly hardware related I don't see that this is something that would be cause by a cracker. One thing I find difficult in Ubuntu is to manage the status of my devices. Seeing as I grew up in windows I was always use to using the control panel > device manager. So if there was a breach in you're security and someone did do some nasty things to you're drive (poison you're recovery partition etc) then I would suggest not just overhauling you're os installs but managing you're network setup as well. Do a complete overhaul of you're router or switch setup and use a more secured form of wireless encryption. If you where running ubuntu and someone was able to get control that deep into you're pc I would suggest it was some form of spoofing (most likely you're router was vulnerable and someone took advantage of this).

So next time I would suggest securing you're network devices first, there the first and sometimes only wall between you're PC and the rest of you're network or the interwebz.

Ryan

"Or you're hacker is a ghost..ROFL"

---

