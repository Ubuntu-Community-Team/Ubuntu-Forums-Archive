---
title: "New &quot;official&quot; derivative: Solbuntu"
date: 2007-11-02
forum: Ubuntu Brainstorm
---

### Post by amiga_os on 2007-11-02
I think there should be plans for an official ubuntu derivative that runs with the opensolaris kernel.

It looks likely that opensolaris will go gpl eventually... which means there's going to be more competition in the GNU opensource market on the kernel end of things.

Nexenta are trying to build an - effectively - Ubuntu distro on top of Open Solaris, I think it would be good for Ubuntu, Canonical and the Ubuntu Community if we had an official derivative in the planning stages at least.

---

### Post by pay on 2007-11-02
I'm not against the idea but if it means that the GNU/Linux version gets less testing and is less mature then I think that it would be a waste. Also if we were going to do it for Solaris then why not freeBSD? Atleast debian have already begun with that..

---

### Post by insane_alien on 2007-11-03
lets fire into HURD as well :P

---

### Post by amiga_os on 2007-11-03
A) I think there's a case to be made for saying that opensolaris is a better candidate than BSD and Hurd.

For starters Hurd is - well - a great idea, but not much more than that at this stage still (e.g. last release was v0.2), and there are huge elements of it's architecture that aren't implemented.

On the BSD front, licence:
BSD is not provided under the GPL, it's got it's own licence.  While Open Solaris is still under a CDDL license, there's a good chance that it's going to be GPL in the foreseeable future.

Furthermore, Open Solaris looks like it really could generate more market momentum than the BSDs.  Having Sun as a backer, with the Solaris userbase already on tap is a huge start.  I'm making the case for a serious conversation about this, or at least someone to look into the matter seriously.  I'm not suggesting That Hardy ships with a Solbuntu next year (granted the title of my thread wasn't that subtle - I wanted to get people to read it).  But I am suggesting that Open Solaris is the first serious contender for an alternative kernel to be offered officially alongside the Linux kernel for Ubuntu.

B) On whether another *buntu should be given over specifically for a different kernel at all:
Solaris is a very mature piece of software, and there are distinct advantages it has over the Linux kernel... and distinct advantages the Linux kernel has over the OpenSolaris kernel.

Solaris, in particular, is very stable and will (hopefully, but time will tell) continue to be very predictable.  e.g. if OpenSolaris moves from version 1.21 to 1.22 then video driver won't suddenly die.

Linux, in particular, is very ubiquitous and supports more hardware than any other os kernel on the planet (that I know of...).

In other words: Solaris carries all the benefits of - over the long term - having been carefully designed and crafted in a proprietary environment.  Linux carries all the benefits of - over the long term - having been open and freely accessible in a public environment.

We have Kubuntu, that ships with KDE and Ubuntu, that ships with Gnome... why?  Because - there is a seriously good choice between the two desktop systems.  Why am I advocating thinking seriously about something like a Solbuntu in the future?  Because that would give us a seriously good choice between two kernels.

---

### Post by pay on 2007-11-04
> **amiga_os said:**
> A)On the BSD front, licence:
BSD is not provided under the GPL, it's got it's own licence.  While Open Solaris is still under a CDDL license, there's a good chance that it's going to be GPL in the foreseeable future.The BSD license is arguably more open the the GPL.

I don't mind the idea the only problem I have is that it will require twice as much testing as bother kernels will need to be tested... Maybe if something like Nexenta keeps getting developed and gains a reasonable market share then it will be worth while to follow their footsteps and make an official Ubuntu derivative.

---

### Post by American_Outcast on 2007-11-04
Maybe base it on FreeDOS..... :lolflag:

---

### Post by mick8985 on 2007-11-05
Very interesting. I agree that the choice should be there, it would especially help with Ubuntu's adoption on the server, but would it be useful for desktop use? I see nvidia [provide an up to date binary for solaris]("http://www.nvidia.co.uk/object/solaris_display_100.14.11_uk.html") so even desktop effects should be possible. I'm off to download nexenta. Have you tried it yourself?

---

### Post by spoilerhead on 2007-11-06
um, already done:

_[NexentaOS](http://www.gnusolaris.org/gswiki)_

---

### Post by diddledan on 2008-02-05
I'd like to jump in here and point out that nexenta is purely a "base system", and that they don't want to provide support for anything beyong the core libraries and utilities. A full *buntu-based drivative using the solaris kernel should IMO provide a much more extensive featureset than nexenta are willing to commit to.

---

### Post by allquixotic on 2008-02-07
I'm in favor of a Canonical-driven OpenSolaris distribution.

They could start with the work of Nexenta and start adding on Ubuntu packages which are supported by the Nexenta userspace, which is in turn supported by the OpenSolaris kernel.

Having something to compare against Linux with a similar userspace should increase interest in Ubuntu projects at large, and show us a bit of exactly what the cathedral model can do.

If you don't have faith in the cathedral-gone-public model, just look at what became of the Netscape code -- Firefox. Without it, we'd have... what? KHTML? WebKit?

---

### Post by mick8985 on 2008-03-31
Just checking up to see if anyone is still interested in this, perhaps the OP should submit this idea to brainstorm?

---

