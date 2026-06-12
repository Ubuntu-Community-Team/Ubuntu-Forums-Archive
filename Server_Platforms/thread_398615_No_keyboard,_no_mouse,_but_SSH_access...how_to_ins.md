---
title: "No keyboard, no mouse, but SSH access...how to install Ubuntu Server LTS?"
date: 2007-04-01
forum: Server Platforms
---

### Post by stokedfish on 2007-04-01
Hello,

I've got SSH access to a machine in my network and also physical access. But right now I don't have a keyboard and a mouse. I do have a screen though, which I could plug in at the server. Anyway, how to install Ubuntu LTS server edition like that? And oh, should I prefer the Feisty server edition, the beta? The final is out soon and has newer packages and support till 2009 as well...

---

### Post by elst on 2007-04-01
Is the SSH access to an existing OS installation, or an attached terminal console device?

---

### Post by stokedfish on 2007-04-01
It's an existing Ubuntu Server LTS...and I want to delete that partition to install, erm, Ubuntu Server LTS on it!

I know, I know...but hey, I have my reasons...  ;)

---

### Post by elst on 2007-04-01
This is slightly tricky to do... I don't think that the installer has embedded remote access (Red Hat's Anaconda does). You can use Kickstart or preseeding to automate an Ubuntu installation, but both embedded remote access and automated installs have the same issue - you need to feed the installer enough configuration options to activate the feature.

If you have another machine on the network you can setup a PXE boot facility, and probably get that to launch an install preset with the necessary options to use a Kickstart or preseed file. Then all you need to do is reboot your server, and it'll PXE boot the Ubuntu installer, and run the installation according to the settings in the file without needing any keyboard input from you. The system that you use for PXE etc. can be a virtual machine - you don't need to mess up an existing host system.

---

### Post by nanotube on 2007-04-01
it's an interesting question, to which i don't have any better answers than have already been offered... 
but i am curious, why do you not just plug in a keyboard, since you do have physical access? :)

---

### Post by stokedfish on 2007-04-01
Because I would have to buy one first...  ;)

---

### Post by nanotube on 2007-04-01
> **stokedfish said:**
> Because I would have to buy one first...  ;)

hehe i see. i suppose it has already occurred to you that you could unplug it from another computer (e.g. the one you are on now) - unless you're on a laptop... :) but i will mention it just in case. ;)

---

### Post by anthro398 on 2007-04-01
You might have a look at this [Ubuntu on Cube howto]("http://braggtown.com/qubuntu.html") I wrote.  You can use nfs to bootstrap a new system on the drive.

---

### Post by stokedfish on 2007-04-03
Aww, yes.

Well, my other machine is indeed a laptop.

I hoped for an easy solution...but yeah, now I bought a keyboard for 10 CHF, proplem solved.

Thanks for all your kind help though!!  :)

---

### Post by pppetter on 2007-04-03
Okey, now you have already bought a keyboard, but I did come up with a very lame idea, you could upgrade to edgy and then upgrade to feisty. That's all I could come up with :P

---

### Post by stokedfish on 2007-04-12
That's lame indeed, hehe...

Because Dapper is a superb server system, stable, reliable, fast, just great!   :D

---

