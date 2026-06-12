---
title: "Good distro for this situation."
date: 2010-04-04
forum: The Cafe
---

### Post by dragos240 on 2010-04-04
I have a netbook. It's a nice eee 900HD computer. It currently runs gentoo quite nicely, but on a small netbook with less power than my home computer, it's not very efficient. I want something simple, that still allows me to compile my own kernel, and gives the option to compile my own software as well as having a binary repo, for the sake of convenience. Something that also lets me install everything from scratch, no pre-installed stuff. Something that will let me dig into the roots of UNIX/Linux. I still plan on using gentoo linux on my main tower, but, my netbook needs something else. I tried debian, but it won't support the rtl8187se driver out of the box, and wireless is the only way of me getting sources out of the repo. What do you guys think.

---

### Post by MrNatewood on 2010-04-04
To be that sounds like an exact description of Arch Linux

---

### Post by phibxr on 2010-04-04
Arch sounds like a plan, yes.

You might want to check [Zenwalk]("http://www.zenwalk.org/") out too. I think you can get a pretty clean installation of it.

Otherwise, you might want to check out [Linux From Scratch]("http://www.linuxfromscratch.org/").

---

### Post by Bachstelze on 2010-04-04
If you like Gentoo, you can use distcc to share the compiling work between your netbook and your desktop computer (or even make your desktop computer do all of it).

---

### Post by chris200x9 on 2010-04-04
> **dragos240 said:**
> I have a netbook. It's a nice eee 900HD computer. It currently runs gentoo quite nicely, but on a small netbook with less power than my home computer, it's not very efficient. I want something simple, that still allows me to compile my own kernel, and gives the option to compile my own software as well as having a binary repo, for the sake of convenience. Something that also lets me install everything from scratch, no pre-installed stuff. Something that will let me dig into the roots of UNIX/Linux. I still plan on using gentoo linux on my main tower, but, my netbook needs something else. I tried debian, but it won't support the rtl8187se driver out of the box, and wireless is the only way of me getting sources out of the repo. What do you guys think.

arch, btw didn't you come from arch to gentoo? Kinda a question you already knew the answer to IMHO.

---

### Post by Eisenwinter on 2010-04-04
> **chris200x9 said:**
> arch, btw didn't you come from arch to gentoo? Kinda a question you already knew the answer to IMHO.
Maybe he just didn't know about the ABS.

---

### Post by Bachstelze on 2010-04-04
> **Eisenwinter said:**
> Maybe he just didn't know about the ABS.

Or maybe he *gasp* didn't like Arch?

---

### Post by RiceMonster on 2010-04-04
> **Bachstelze said:**
> Or maybe he *gasp* didn't like Arch?

Blasphemy!

---

### Post by chris200x9 on 2010-04-04
> **Bachstelze said:**
> Or maybe he *gasp* didn't like Arch?

or maybe if he didn't like arch he should have mentioned it seeing as it would be the most logical choice, people are not suggesting arch to be a "fanboi".

edit: why not try freebsd? You have ports and pkg-add, plus you can learn more about UNIX by divirsifying :)

---

### Post by Pogeymanz on 2010-04-04
Arch for the win.

I would also say FreeBSD would be good, but I can only imagine that hardware support for a netbook might be worse for BSD than Linux.

In Arch you can set the package manager to not update certain packages so that you can build it yourself. It will still alert you when there is a new version, it just wont install the binary for you.

---

### Post by kaldor on 2010-04-04
You could try a *solaris distro. But they aren't really compilable, but true UNIX nonetheless. 

Try Slackware.

Wolvix is based on Slackware and is very easy to install and set up. But it's still slackware; you're in total control.

---

### Post by dragos240 on 2010-04-04
You know. I really liked arch for a while. I know about the ABS and the AUR, but things kept breaking. It however did support my hardware quite well. I think I'll try slackware just because I haven't given it a shot yet. Can someone point out an iso (or better yet an img for my flash drive, of course I can use unetbootin) and perhaps a manual?

---

### Post by RedSquirrel on 2010-04-04
> **dragos240 said:**
> I think I'll try slackware just because I haven't given it a shot yet. Can someone point out an iso (or better yet an img for my flash drive, of course I can use unetbootin) and perhaps a manual?

Read the text documents (Slackware-HOWTO, etc.) located on the Slackware mirrors, for example, [here]("http://slackware.osuosl.org/"). You might also want to browse the [Slackware forum]("http://www.linuxquestions.org/questions/slackware-14/").

---

### Post by _BugsBunny_ on 2010-04-04
You *could* run Debian, all you need to do is either install a kernel from backports, or - even better - install and run testing (squeeze) rather than lenny. See [rtl818x - Debian Wiki](http://wiki.debian.org/rtl818x#RTL8187SE)

---

### Post by Zoot7 on 2010-04-04
> **dragos240 said:**
> You know. I really liked arch for a while. I know about the ABS and the AUR, but things kept breaking. It however did support my hardware quite well. I think I'll try slackware just because I haven't given it a shot yet. Can someone point out an iso (or better yet an img for my flash drive, of course I can use unetbootin) and perhaps a manual?
I'm a BIG fan of slackware, but I wouldn't use it on a netbook really tbh, as wireless for me was quite the pain in it - wpa-supplicant over the command line was the only thing I could get working, no joy with wicd.

Anyway, Debian is definitely one to consider. A minimial install of Testing with the likes of Fluxbox would fit the bill quite aptly IMO. 
Or, what might be better still would be eeebuntu, which would be superior for the likes of battery life etc. (so I hear, haven't tried it myself)

---

### Post by Arand on 2010-04-04
If it's simply a matter of getting the drivers up and running, wouldn't it be possible to install them through a chroot, using whatever liveCD that supports networking straight out of the box, in conjunction with an installed system of choice for which the drivers are available, yet needs to be pulled down separately..?
- Arand

---

### Post by MisfitI38 on 2010-04-05
> **dragos240 said:**
> I have a netbook. It's a nice eee 900HD computer. It currently runs gentoo quite nicely, but on a small netbook with less power than my home computer, it's not very efficient.
If by 'not very efficient' you mean 'too much compiling for a netbook', then why are you looking at Slackware as an alternative? You *will* have to compile a significant amount of software on Slack, to get a webworthy, multimedia system.
> 
 I want something simple, that still allows me to compile my own kernel, and gives the option to compile my own software as well as having a binary repo, for the sake of convenience.
Any distro will allow you to compile your own kernel or software..but we are back to the argument you cited above. The minimalist, or simple distros include Arch, Slack, and CRUX.
> 
 Something that also lets me install everything from scratch, no pre-installed stuff. Something that will let me dig into the roots of UNIX/Linux.
Arch, Slack, CRUX.
> 
 I still plan on using gentoo linux on my main tower, but, my netbook needs something else. I tried debian, but it won't support the rtl8187se driver out of the box..
You want a minimalist distribution that has no pre-installed stuff, but you complain of no wireless out of the box...hmmm. The obvious solution would be to acquire the wireless drivers you need and installing them to a base Debian installation.
> What do you guys think.
I think you may want to rethink exactly what you want/need. You seem to contradict yourself a bit. There are only so many 'minimalist' distros, and they all require manual configuration, and yes, sometimes effort, to shape them into exactly what we need. 
My advice is to grab the distro of your choice by the horns and stop letting these trivial roadblocks stop you. Make the OS work for you. ;)
Enjoy, and let us know how you do.

---

### Post by Eisenwinter on 2010-04-05
> **Bachstelze said:**
> Or maybe he *gasp* didn't like Arch?
That's impossible, don't be ridiculous.

---

### Post by dragos240 on 2010-04-05
> **Eisenwinter said:**
> That's impossible, don't be ridiculous.

It's true. Anyway, consider this topic [SOLVED]. I have chosen debian as my default netbook OS. Works great.

---

