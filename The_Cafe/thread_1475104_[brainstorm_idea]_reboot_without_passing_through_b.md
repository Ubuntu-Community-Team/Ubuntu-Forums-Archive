---
title: "[brainstorm idea] reboot without passing through bios"
date: 2010-05-06
forum: The Cafe
---

### Post by Ylon on 2010-05-06
Well, well.. here me again with another brainstorm idea.

I am giving out the [24,745th](http://brainstorm.ubuntu.com/idea/24745/) idea in Ubuntu knowing hardly it will catch interest. Well, isn't propose of the brainstorm loose mind and drop your (bizarre) input?


What do you think about it? it's technically possible to make the os "regress" to the bootloader status... discharging everything else to boot another system without need to pass again through the bios (power off/poweron)?

---

### Post by nikhilbhardwaj on 2010-05-06
i was thinking more on the lines of automatically updating the kernel as it runs
no rebooting after upgrading to a newer version of the kernel
infact no need to reboot at all

---

### Post by Ylon on 2010-05-06
Yeah, I know there was on development something alike (not sure if it's already possible) will be a nice addition also. I think that the possibility of modify the kernel "on fly" add some security issue... but what doesn't?

---

### Post by The Real Dave on 2010-05-06
One Question.....Why?

---

### Post by donkyhotay on 2010-05-06
> **The Real Dave said:**
> One Question.....Why?

For the challenge
to increase reboot speed
for the prestige of doing it first

pick a reason why anyone would want to work on any FOSS project and they could fit this. Sure you may not want it but there are many FOSS enhancements/programs/features someone makes that others don't care about.

---

### Post by Crunchy the Headcrab on 2010-05-06
How would you load the kernel without passing through BIOS?  Would it really be a true reboot?

---

### Post by MaxIBoy on 2010-05-06
> **nikhilbhardwaj said:**
> i was thinking more on the lines of automatically updating the kernel as it runs
no rebooting after upgrading to a newer version of the kernel
infact no need to reboot at all
[http://www.ksplice.com/](http://www.ksplice.com/)

Ksplice is popular where 100% uptime is really needed (servers and the like.) It's in the repos:
```
sudo apt-get install ksplice
```
But I've never used it myself. I'm not sure if all drivers can cope.

---

### Post by Ylon on 2010-05-06
> **The Real Dave said:**
> One Question.....Why?

For.... reboot your system without having to shutdown?


> **donkyhotay said:**
> For the challenge
to increase reboot speed
for the prestige of doing it first

pick a reason why anyone would want to work on any FOSS project and they could fit this. Sure you may not want it but there are many FOSS enhancements/programs/features someone makes that others don't care about.
'cos it's... an idea? and brainstorm feature was supposed to used this way (propose ideas) :lolflag:
> **Crunchy the Headcrab said:**
> How would you load the kernel without passing through BIOS?  Would it really be a true reboot?

Well, when you're grub it's still anything possible (windows, linux whatever).. and you're already out of the bios.



Anyway, probably it would be wrong call it "reboot".. a more appropiate name would "Regress&Redirect"... "**Regre**t"? (also know: I've boot the wrong os in grub before" :lolflag::lolflag:

> **MaxIBoy said:**
> [http://www.ksplice.com/](http://www.ksplice.com/)

Ksplice is popular where 100% uptime is really needed (servers and the like.) It's in the repos:
```
sudo apt-get install ksplice
```
But I've never used it myself. I'm not sure if all drivers can cope.

Luckly is not my idea.. or they would put "already implemented" 




Come on, no one approve this idea?
>> [http://brainstorm.ubuntu.com/idea/24745/](http://brainstorm.ubuntu.com/idea/24745/)

---

### Post by juancarlospaco on 2010-05-06
***This is not a Reboot, by definition...***

---

### Post by Crunchy the Headcrab on 2010-05-06
> **Ylon said:**
> 
Well, when you're grub it's still anything possible (windows, linux whatever).. and you're already out of the bios.



Anyway, probably it would be wrong call it "reboot".. a more appropiate name would "Regress&Redirect"... "**Regre**t"? (also know: I've boot the wrong os in grub before" :lolflag::lolflag:
Yes that's true.  BIOS ROM loads the boot loader (GRUB) which which loads the Linux Kernel.  

In order to be able to shutdown Linux and reload GRUB, I think the OS and GRUB itself would need some HUGE alterations.

---

### Post by Ylon on 2010-05-06
> **juancarlospaco said:**
> ***This is not a Reboot, by definition...***
You're giving existential crisis to the GRUB **boot** loader :P

> **Crunchy the Headcrab said:**
> Yes that's true.  BIOS ROM loads the boot loader (GRUB) which which loads the Linux Kernel.  

In order to be able to shutdown Linux and reload GRUB, I think the OS and GRUB itself would need some HUGE alterations.

I am not too much sure about this. I've see some multiboot cd that run quite complex application (sometime launching different boot loader) before boot the real system.
A quick example I may say it's ultimate boot cd (you can google easly it): it allow you to choice different boot loader for older and newer hardware.. then you can choice the os to run (which include various tools, OSes and Freedos)

Anyway, I've mockup'ed my idea.. to give a general view how it should perform in the user's eyes.
[IMG]http://i39.tinypic.com/14wtvyb.png[/IMG]

---

### Post by snova on 2010-05-06
> **Crunchy the Headcrab said:**
> Yes that's true.  BIOS ROM loads the boot loader (GRUB) which which loads the Linux Kernel.  

In order to be able to shutdown Linux and reload GRUB, I think the OS and GRUB itself would need some HUGE alterations.

I imagine you could restart grub by disabling long mode (if necessary) and protected mode, rereading the boot sector off of disk, and then jumping to it as the BIOS would. In theory it would require no modifications to the startup process.

The main issue I see is that the hardware would be in odd states- at boot time I believe it is generally well defined; either they haven't been initialized yet or the BIOS has performed basic setup. If they were reset somehow beforehand, or simple enough where it didn't matter, it could probably be done. I think there's very little practical reason to though.

---

### Post by happyhamster on 2010-05-06
'Directly' booting into another kernel is possible when using a kernel that allows the kexec system call. (It is found under the "Processor type and features" option when compiling a kernel.)

[http://www.ibm.com/developerworks/linux/library/l-kexec.html](http://www.ibm.com/developerworks/linux/library/l-kexec.html)

---

### Post by Ylon on 2010-05-06
Wow, thanks happyhamster.. I didn't know that... now I've added your link to the brainstorm idea. Let's hope it will took seriously now.

---

### Post by MaxIBoy on 2010-05-07
Haha, kernel 3.0 beta. :lol:

Seriously though, I do like the idea of being able to set the OS before rebooting. But the BIOS is fast enough that it's really not worth the trouble at least for me, given how rarely I reboot. Most of the time I don't "reboot." If I power off, it's because I need my computer to actually be "off."

But you may have a use case where your priorities are different. And if you get this implemented, it would be a pretty neat trick.

---

### Post by hawthornso23 on 2010-05-07
If something goes wrong could I then be stuck unable to get into the BIOS to change the boot order to boot off cdrom? Will we end up in the brick making business?

---

### Post by Ylon on 2010-05-07
I want to extend the second part of the idea (in the end I would see applied both).


I had to propose as different solution, or I can keep add details to the first one?


Edit: Ok, I've added the second part of this idea.. too big to put directly the image there: here's the link:
[http://i43.tinypic.com/1z2ktnn.jpg](http://i43.tinypic.com/1z2ktnn.jpg)

---

### Post by NMFTM on 2010-05-07
> **MaxIBoy said:**
> But the BIOS is fast enough that it's really not worth the trouble at least for me, given how rarely I reboot.
On my desktop, the BIOS takes about 25 seconds. The time it takes to boot the OS after the BIOS is about 35-40 seconds. So, your looking at almost half the boot time being taken up by the BIOS.

Why does BIOS take so long? All it does is check to see if the hardware is still there, initialize it, and than load the first software. Which on my computer, is GRUB.  How can it take so long to do what is basically the networking equivalent pinging?

---

### Post by Bodsda on 2010-05-07
> **MaxIBoy said:**
>  
Seriously though, I do like the idea of being able to set the OS before rebooting.
 
That could easily be achieved by a script that just edits the default entry for grub to boot. I wrote one once for grub1, its not that difficult.
 
Bodsda

---

### Post by MaxIBoy on 2010-05-07
> **NMFTM said:**
> On my desktop, the BIOS takes about 25 seconds. The time it takes to boot the OS after the BIOS is about 35-40 seconds. So, your looking at almost half the boot time being taken up by the BIOS.

Why does BIOS take so long? All it does is check to see if the hardware is still there, initialize it, and than load the first software. Which on my computer, is GRUB.  How can it take so long to do what is basically the networking equivalent pinging?Goes through all disks looking for boot sectors, runs some checks on all RAM, etc. Especially killer is if your CD drive is set above the HDD in the boot order, because it needs to actually spin up the drive's motors to check. 

Still, most BIOSen have a quickboot mode, which only takes a couple seconds but skips most of the POST stuff. See if your BIOS has it anywhere.

---

### Post by NMFTM on 2010-05-07
> **MaxIBoy said:**
> Still, most BIOSen have a quickboot mode, which only takes a couple seconds but skips most of the POST stuff. See if your BIOS has it anywhere.
I have my BIOS on quick mode and it still takes that long.

---

### Post by Crunchy the Headcrab on 2010-05-07
> **hawthornso23 said:**
> If something goes wrong could I then be stuck unable to get into the BIOS to change the boot order to boot off cdrom? Will we end up in the brick making business?
You would still be able to do a hard reset which would run BIOS again.  This is only for purposes of restarting an OS without rebooting.

---

### Post by alzie on 2010-05-08
I remember something called a "warm reboot" or "soft reboot" where the computer itself did not stop, and only the OS was rebooted.

Wikipedia has an entry on "kexec" which sounds like what you are thinking.

---

### Post by Ylon on 2010-05-09
Kexec is a possible application, but it's not what I am thinking. Kexec was intended for urgent, security, update in the kernel structure... mainly for server propose I do suppose.
To clarify: it's mean is to "keep alive" the whole structure of the OS (kernel modules and kernel structure).. but, for example, it will be able to "revive" on even the same kernel.. but different bit structure (32 to 64bit). So: kernel 2.6.32 >to> kernel 2.6.3**3**. Not: linux 2.6.32 >to> haiku.


My idea is, basically, "go to zero, kernel! then start grub"

There are different possibility to this rule... the "user feedback" also will be like a blackscreen: no input from the screen, so he's feeling it's running something _inside_ his/her Ubuntu session.



I give you a possible application with Steam.. that sound quite popular lately.



-------possible application for steam-like product----

This thing that we could call GES (GameEngineStore) make a copy of your actual kernel on install: modules and stuff to make "your hardware work". Then "cut out" all the fats, the things/service/kernel.modules the GameEngine don't need (bluetooth, CUPS, gnome*, metacity,nautilus, ntfs, devices.......) leaving only the essential for:

video, audio, control, basic.storage, network +additional modules for gaming (or special wine modules)
Practically: make your PC a console.

It's a copy of your kernel dinamcally updated, so... once you're on the "normal session" you can still interact with it (buy games from firefox, install contents etc).

--------/idea end-------------------------------------

The GES it's just an example.. but this may used for stuff like mediacenter (xbmc), multimedia studio(jackd&co) or extreme security propose (heavily encrypted session on a encrypted partition).

---

### Post by chriswyatt on 2010-05-09
Windows 98 did something similar didn't it?  I remember you had to hold down shift or ctrl when you restarted the computer, or something like that.

It's probably possible in other Windows versions, can't say I've tried.

---

### Post by KiwiNZ on 2010-05-09
I have asked this before and it still baffles me . 25secs boot or 20secs boot or 15 secs boot.

There is 86,400 seconds in a day and people get all hung up on 5 or 10 seconds :confused:

How many times a day do you reboot your PC's ?

Maybe its time to turn them of for a month or two.;)

---

### Post by Ylon on 2010-05-10
I was more thinking about a whole different way of approaches with the system. Not just speed

Some user like how perform the OSX in *look&feel*, some the multimedia capabilities and the *thrilling* of spyware/virus on Windows. Microsoft and Apple had build(and locked) their kernel in order to give an unique feeling to their clients.

Now, what do have Linux(Ubuntu)? an Open kernel. So, my idea is this: use this unique things (everyone can work/modify kernel.. or even use another one!) for make unique Ubuntu!

---

