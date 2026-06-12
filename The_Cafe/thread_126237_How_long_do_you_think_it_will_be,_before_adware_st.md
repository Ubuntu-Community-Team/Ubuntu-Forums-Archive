---
title: "How long do you think it will be, before adware strikes linux?"
date: 2006-02-06
forum: The Cafe
---

### Post by shade11 on 2006-02-06
I know that viruses don't work on linux but what about adware? I mean the Linux community is growing and someday people like 180solutions are going to create a Linux client. . . It is posible right?

---

### Post by ardchoille on 2006-02-06
[QUOTE=shade11]I know that viruses don't work on linux but what about adware? I mean the Linux community is growing and someday people like 180solutions are going to create a Linux client. . . It is posible right?[/QUOTE]
Oh, it's entirely possible. However, the wonderful thing about open source apps is that there are lots of eyes looking at the code.. eyes which will let the community know of any virus/adware/trojan/worm/bugs in the code of that app. When a new app comes out, I always wait to hear the "thoughts" of the open source community before I install it, this is because I don't yet know programming well enough to be able to audit code myself. If people start to see adware code in an app, word would get around rather quickly and no one will trust that app, much less the company who wrote that app. This is one of the reasons why it's a waste of time for anyone to write open source adware, and I won't even install closed source software.

---

### Post by briancurtin on 2006-02-06
anything is possible

---

### Post by TechSonic on 2006-02-06
It's possible if you leave your password blank and use Root mode.  Great thing about Ubuntu, root is disabled and sudo requires password, something adware/spyware/trojans/viruses need to install.

---

### Post by Lovechild on 2006-02-06
I don't install anything that isn't signed off by either Fedora Core or Fedora Extras, my system is protected 6 ways from Sunday by SELinux, exec-shield, FORTIFIY_SOURCE=2, -fstack-protector and a default restrictive incoming firewal. I only see security becoming better by the day, spyware lately depends on known security holes and Red Hat have a less than 1 day window for closing critical holes not to mention the fact that many of the discovered holes were not exploitable because of proactive security.

People who writes such malware will have a much harder job infecting your average Linux machine than they have with Windows, but they will manage at some point I doubt we'll ever see Windows levels of stupidity though.

---

### Post by Leo_01 on 2006-02-06
adwares usually use activex to get their crap in...
and activex is nearly impossible to be in any open source browser...
:-k 
maybe we can get tracking cookies...
but for sure not adwares.

---

### Post by shade11 on 2006-02-07
No, like legal adware. likw installing a program that comes with adware. And if you install it with sudo, root, or su. Meaning that it can install where it needs to go.

---

### Post by Derek Djons on 2006-02-07
I agree with the most replies here. As long as you will stick loyal to your packetmanager and protect your own system with firewall and a virusscanner (especially if you have more 'windows' computers in your network) nothing is going to happen.

Though I am fond of new and beta software I've learned from the past and now I just paciently wait for it to appear in my repositories.

---

### Post by nocturn on 2006-02-07
[QUOTE=shade11]I know that viruses don't work on linux but what about adware? I mean the Linux community is growing and someday people like 180solutions are going to create a Linux client. . . It is posible right?[/QUOTE]

Adware still needs a way to enter your PC, therefor it is often the payload of a virus.

As long as you stick to the repositories or sources you trust, there is no way they can get it installed on your machine.

---

### Post by GreyFox503 on 2006-02-07
As it currently stands, most software available for linux systems is Free and open source, so including spyware/adware in them is not very practical.  They could not hide it very effectively.  All it would take is for one person to find and remove it, and then they could redistribute the clean version.

If proprietary applications become more popular, then I suppose they could do anything they want while running.  It would still be much harder for them to "hijack" your machine (as opposed to Windows) unless you install/run them as root, but even with normal privileges they could display some ads or annoy you.

---

### Post by egon spengler on 2006-02-07
[QUOTE=nocturn]Adware still needs a way to enter your PC, therefor it is often the payload of a virus.[/QUOTE]

I'm fairly certain that shade11 means adware as in legitimate programs with advertising mechanisms built in. The kind of programs where you agree to allow the installation of ad infested programs in the terms & conditions step of the installation that most people skip. To be honest I haven't come across this kind of program in so long I can't think of an example, is Bonzi buddy still around? I know Kazaa used to havae some form of adware in it hence Kazaa lite

---

### Post by BoyOfDestiny on 2006-02-07
[QUOTE=ardchoille]Oh, it's entirely possible. However, the wonderful thing about open source apps is that there are lots of eyes looking at the code.. eyes which will let the community know of any virus/adware/trojan/worm/bugs in the code of that app. When a new app comes out, I always wait to hear the "thoughts" of the open source community before I install it, this is because I don't yet know programming well enough to be able to audit code myself. If people start to see adware code in an app, word would get around rather quickly and no one will trust that app, much less the company who wrote that app. This is one of the reasons why it's a waste of time for anyone to write open source adware, and I won't even install closed source software.[/QUOTE]

The "problem" is not everyone is using open source apps on their linux boxes. For many macromedia flash,sun java, closed video drivers, etc (I'm not saying these are malware ridden). If people can easily install apps from untrusted sources and run/install them as root, I don't doubt someone could install a root kit. 

I'll mention I haven't used selinux, or execshield, let's just say my current ubuntu install as is.

I imagine that a malware app without root power, could foul up one's home folder (I don't know about you, but / and the os is the easy to replace part. I can have my system up and running as I like it in under 30 minutes if my home partition is intact)

If you just meant adware, I dunno... I avoid those apps like the plague. Perhaps in linux they'd have a tougher time using your cpu cycles to dish out other ads...

Sorry if I went off on a tangent, I can't really tell the difference between adware, spyware, and malware... Since all that I've read or heard about overlap...

---

### Post by fuscia on 2006-02-07
why would adware designers target a group of people who think there's such a thing as free beer?

---

### Post by Malphas on 2006-02-07
It's the software developers that would make the call, not the adware designers.  Whether they'd manage to get away with it would depend on how good their software is and what alternatives there were too it.  I can think of a few cases where developers of Windows applications have introduced adware only to remove it after the community backlash (AutoGK for one) and cases where the community has relunctantly went along with it due to the quality and track record of the software (DaemonTools), although obviously everyone is opting out of the adware installation.

---

### Post by LordBug on 2006-02-07
> I know that viruses don't work on linux 
This is so very incorrect.  There ARE viruses for *nix systems.  They can be nasty, but since 99% of the time you're not in root mode they're generally ignored.  However, they do exist...

Adware might be an issue later, as more and more people start tinkering with Linux and doing stupid things.  Tracking cookies, AFAIK, already work fine in Linux.  

Applications that specific state you will see ads in the software I don't have issues with.  They tell you flat out you're going to see ads while using the software (usually until you buy the software).  This is already common in Windows shareware applications.

True malware on the other hand...  That I hope never gains a foothold in Linux.  Even if it did, it will likely only impact individual accounts with the way security is setup.

---

