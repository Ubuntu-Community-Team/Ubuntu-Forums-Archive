---
title: "Linux From Scratch?"
date: 2006-05-29
forum: The Cafe
---

### Post by NobleSavage on 2006-05-29
[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

Has anyone ever attempted this?  I'm thinking about it a shot. I'm a little nervous about how much effort it may take.  And I'm wondering if the learnig experince would be worth the effort.

---

### Post by K.Mandla on 2006-05-30
I've heard of people using it, but never had the guts myself. I'm just getting used to Arch, and I'd like to tackle Gentoo one day, so LFS might happen after that ... after I graduate from guru school. :)

---

### Post by Ptero-4 on 2006-05-30
I haven't yet, but I'm thinking about trying it.

---

### Post by Patrick-Ruff on 2006-05-30
seems really complicated, I will eventually though.  Ubuntu holds many benefits over it
unless yoru going to basically remake Ubuntu type LFS system or somehting.

---

### Post by NobleSavage on 2006-05-30
[QUOTE=Ptero-4]I haven't yet, but I'm thinking about trying it.[/QUOTE]

Man, I love your sig!  I might have to borrow that for another forum.  

If you do decide to do it, let me know - it's be cool to have someone to work through it with.

---

### Post by ronlybonly on 2006-05-30
I though about trying to build a distro from scratch, but it seemed like too big of an undertaking for a lazy bum like me.

---

### Post by NobleSavage on 2006-05-30
[QUOTE=Patrick-Ruff]seems really complicated, I will eventually though.  Ubuntu holds many benefits over it
unless yoru going to basically remake Ubuntu type LFS system or somehting.[/QUOTE]

I'm sure Ubuntu has many benifits, but my only reason for doing it would be to learn more about the deep internals of Linux.  I was taking with a guy who is more or less a linux wizard and he was saying that LFS was the best way to learn.

---

### Post by papangul on 2006-05-30
[QUOTE=NobleSavage]Has anyone ever attempted this?[/QUOTE]
I attempted it about five years ago. It's very mechanical, you copy, paste and run commands like a robot and the process goes on and on. I got drowned when I was halfway through the ordeal. 
[QUOTE=NobleSavage] And I'm wondering if the learnig experince would be worth the effort.[/QUOTE]
Later, in my next life(in 2005), I tried Gentoo successfully and it was a much better learning experience(and fun) for me than LFS. In Gentoo, learning how to upgrade your system without breaking anything is one of the most terrific learning experience in linux. I didn't simply have the talent in me, nor did I have the hardware and patience to compile hours together. So I gave up, and i am now settled quite happily with Ubuntu.:D

---

### Post by drucer on 2006-05-30
I'm running Linux From Scratch on my home desktop system (Ubuntu is on laptop).

It's blazingly fast and has only the components I want (including kernel modules).

It was a very good learning experience to install _my own system_, but I would not recommend it to many people. You have to have nerves - it's going to take a while until the whole system is installed (basic LFS can be installed in a day or two, but then it just starts - then you will need to decide what software you want to run on top of it). 

Believe me it's often best to just run some well known distribution like Ubuntu, but if you think you are interested enough to learn a lot of new things and you have nerves, then go for it! You'll learn tons of things!

---

### Post by bonzodog on 2006-05-30
An Alternative might be to install something like Slackware, do it on expert install mode, and just choose the packages you need. It will drop you to the CLI on first boot, and you will need to configure X before you get the GUI. You will learn very fast all about the /etc config file area, and how the BSD style init system controls the boot process of the system. You can also then learn the inner working of the xorg file, and as slackware doesn't use the latest and greatest kernel, you will get to compile your own. 
The lesson here is, start small, learn about the linux directory structure, what each part of the root tree does, what it typically contains. Compile a kernel and the modules you need. Learn about X. You will spend most of your time in the CLI, which in slackware is a framebuffer, which makes it easier to read. You can learn about runlevels that a normal Linux system uses. In slackware, you will manually have to alter the runlevel that the system boots to if you want gdm on login.
Start small, and work your way through it. It has often been said that if you really want to learn Linux, use slackware.

---

### Post by G Morgan on 2006-05-30
I'm using Slackware in a VM at the moment as a learning experience. I have to say that VM's are far and away the best way of learning an OS. I first used Gentoo in a VM because I could get the docs open in Firefox while I was installing. Once I knew enough I took a few simple notes then dived into a full install.

I am intending LFS in a VM once Slack is running nicely. I've also played with BSD in there so yeah Qemu or VMware are useful tools for playing around with.

---

### Post by kjcon on 2006-05-30
I've tried it a few times. Although I was never successful, I did learn a lot about the way a Linux system is put together. Also my attempts made me much more comfortable with the command line.

---

