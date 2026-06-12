---
title: "Linux Core Help"
date: 2010-02-24
forum: The Cafe
---

### Post by Jvaldezjr on 2010-02-24
I am not a new linux user, I've been using Kubuntu since 2006 and currently have 8.04 installed.  I am wondering if there are some resources for me to learn the core things regarding configuring linux.  Basically I want to learn how to set up networking, print/filesharing, etc without having to rely on a specific GUI.  The reason is I'm experimenting with other Ubuntu based distributions, and default boot is to a command shell.  I used to write code using linux, so I think I'm probably an intermediate user, I know how to install applications from source, I've rebuilt kernels before, but not too fond of it. I just want to improve my command-line, or what I call Core Linux Skills so that no matter what distro I use, I can be able to get a system configured and ready for normal desktop use.

Is there one place or a few places that I can look and find what I need?

Thanks.

---

### Post by bruno9779 on 2010-02-24
I find myself in needs and skills similar to yours.

I have planned to set up arch on a test machine for months, and learn as I go. I haven't had time for that yet, but setting a goal and learning the skills needed to get there, works better for me than a bunch of tutorials

---

### Post by Jvaldezjr on 2010-02-24
I know there is a lot of web stuff out there, I'm hoping someone with superior linux knowledge can point in the right direction.

---

### Post by wojox on 2010-02-24
Arch is nice for learning system configs.
[LinuxFromScratch]("http://www.linuxfromscratch.org/") is another that has helped me.

---

### Post by Jvaldezjr on 2010-02-24
are there books or websites that are better to check out than others?  Any of the orielly ones that anyone can reccomend that are better than others?

---

### Post by wojox on 2010-02-24
Linux in a nutshell O'rielly.

---

### Post by Jvaldezjr on 2010-02-25
I have that one, thanks!

---

### Post by Eisenwinter on 2010-02-25
I recommend installing more "advanced" Linux distributions, like Gentoo.

Sitting there, configuring everything from scratch, compiling for 7 hours straight, and still not be able to set up the system properly, because you eventually run out of patience, is a great learning tool.

(Seriously, do it)

---

### Post by Jvaldezjr on 2010-02-25
Someone else mentioned Arch, which I've been researching the last couple of days.  I'm not a newbie, but I wouldn't classify myself as a power user either.  I've had to manually configure my print and file sharing using Samba & Cups, and set up my home network so my lunix machine can communicate with my windows computers, so that doesn't scare me too much.  I think I'll give it a try but I don't want to wipe out Ubuntu completely incase I break something.  I tried gentoo a couple years ago and didn't understand what I was doing.

---

### Post by earthpigg on 2010-02-25
> **Jvaldezjr said:**
> Someone else mentioned Arch, which I've been researching the last couple of days.  I'm not a newbie, but I wouldn't classify myself as a power user either.  I've had to manually configure my print and file sharing using Samba & Cups, and set up my home network so my lunix machine can communicate with my windows computers, so that doesn't scare me too much.  I think I'll give it a try but I don't want to wipe out Ubuntu completely incase I break something.  I tried gentoo a couple years ago and didn't understand what I was doing.

you know more than i did when i fist installed and configured arch, and i was able to get a fully working system that i *still* use... the arch wiki *really* holds your hand. it has a lot of "if, then, else" type statements in it, so just roleplay that the wiki is the source code and you are the compiler :P

i would even go so far as to say that nitty gritty configuring arch is sometimes (not always) easier than on debian. as an example, enabling or disabling specific daemons (without installing or uninstalling them over and over again) is as simple as adding a single bit of text (ie: "cups" or "sshd") to a single text file.

---

### Post by Eisenwinter on 2010-02-25
> **Jvaldezjr said:**
> [...]so my **lunix** machine can communicate with my windows computers,[...]
You use Lunix too?

---

### Post by ssam on 2010-02-25
[http://tldp.org/](http://tldp.org/)

remember that there is lots more auto configuration these days. there not much point in learning how to write an xorg.conf, because modern xorg auto-detects everything. (if xorg miss detects your system, then it is better that the auto-detection code if fixed, rather than you learn to manually configure it).

---

### Post by MisfitI38 on 2010-02-25
> **ssam said:**
> 

remember that there is lots more auto configuration these days. there not much point in learning how to write an xorg.conf, because modern xorg auto-detects everything.
In a perfect world, that *might* be true..but it's not true in a large percentage of cases.
> 
 (if xorg miss detects your system, then it is better that the auto-detection code if fixed, rather than you learn to manually configure it).
Interesting opinion. Common sense would dictate otherwise. If one is capable of properly configuring an xorg.conf file, then they will not have to wait for upstream developers to 'fix' xorg /hal/whatever for their hardware.
Seems like the difference between being able to actually use a system, or giving up completely and choosing ignorance instead.

To the OP: Using a distro like Arch, Slackware or LFS will force you to interact more with the underlying software that actually makes up a GNU/Linux OS. If you want to learn, and you actually 'hang in there', the system configuration and maintenance on these distros will gain you a familiarity with the basic tools, methods and procedures common to the core of all distros and leave you a more capable *nix user.

---

### Post by Jvaldezjr on 2010-02-26
> **Eisenwinter said:**
> You use Lunix too?

Yes LOL Lunix is even more uber than Linux!

---

### Post by Jvaldezjr on 2010-02-26
> To the OP: Using a distro like Arch, Slackware or LFS will force you to interact more with the underlying software that actually makes up a GNU/Linux OS. If you want to learn, and you actually 'hang in there', the system configuration and maintenance on these distros will gain you a familiarity with the basic tools, methods and procedures common to the core of all distros and leave you a more capable *nix user.

That was my goal with my post and exactly what I'm looking for.  I'll probably start playing with Arch when I can get my drives repartitioned.  Thanks for the advice!

---

### Post by Jvaldezjr on 2010-02-26
OMG that was amazingly easy.  I have a base Arch system installed and it took about 45 minutes.  I understood everything and was even capable of configuring my current grub menu to add arch to it, without fear of wiping my boot record.  I logged in and checked my network config, which is up and running fine as well, so I am good to go!  I feel very confident I can get this system running the way I want and I believe I may totally switch over now.  Thanks for the advice and assistance!

---

### Post by earthpigg on 2010-02-26
remember this: just because everything is going smooth now doesn't mean it always will. don't update when you have something unrelated you need to accomplish an hour later. as soon as a developer declares something stable, it get's pushed to Arch users when they update... not every developer's definition of 'stable' is the same. 

and familiarize yourself with the AUR - the default repos aren't nearly as well stocked as ubuntu's.

---

### Post by Jvaldezjr on 2010-02-27
The other reason I'm consiering a change, is that often when I need to upgrade a particular application, I have a couple of choices: If it's not up to date in the repos or backports, then I have to either update ubuntu to get a newer app version from the repos, or install form source.  I don't mind installing from source, but it can be difficult trying to work out all the dependencies, expecially if the current ones I have installed are older and updating certain libraries end up breaking my system.

I still have some more things to research with Arch, but I'm more just suprised about the level of confidence I have with my Linux skills.  I'm not totally there yet, but I think this was a big step!

---

### Post by Khakilang on 2010-02-27
I bought a "Practical Guide To Ubuntu Linux" and it come with Ubuntu Linux 8.10. If you have time to read you can try this one.

---

