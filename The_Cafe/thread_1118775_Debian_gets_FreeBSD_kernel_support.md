---
title: "Debian gets FreeBSD kernel support"
date: 2009-04-07
forum: The Cafe
---

### Post by newbie2 on 2009-04-07
> The open-source Debian operating system on Sunday gained support for the FreeBSD kernel, allowing users to run the same operating system on two different software cores.

The project was announced in a message to the Debian developers' announcement list.

Traditionally Debian runs on the Linux kernel, but Debian developers said the Unix-based FreeBSD kernel offers certain benefits, such as support for drivers that might not be available on Linux.
[http://news.zdnet.co.uk/software/0,1000000121,39637586,00.htm](http://news.zdnet.co.uk/software/0,1000000121,39637586,00.htm)

---

### Post by haemulon on 2009-04-07
"kFreeBSD offers an alternative in case Linux is branded illegal by the SCO case or other threats," the developers wrote. "[COLOR="Red"]In legal terms, Linux sources are like a minefield[/COLOR]. kFreeBSD is much less vulnerable to such attacks."

They're not putting Linux in a good light by making statements like that.

---

### Post by Sealbhach on 2009-04-07
It's not a bad idea to have a contingency plan. It seems unlikely that Linux will be erroneously made illegal but there is a slight risk, a slight risk.
 
 
.

---

### Post by BXL on 2009-04-07
> **haemulon said:**
> "kFreeBSD offers an alternative in case Linux is branded illegal by the SCO case or other threats," the developers wrote. "[COLOR="Red"]In legal terms, Linux sources are like a minefield[/COLOR]. kFreeBSD is much less vulnerable to such attacks."
Are they sponsored by Microsoft...? Sounds like FUD to me :lolflag:

---

### Post by haemulon on 2009-04-07
I'm going to stop using OpenSuse as my main distro, I just don't feel good about it, even though I like it.

Sometimes it just seems inevitable that sooner or later Microsoft will stand up against Linux.

---

### Post by motang on 2009-04-07
> **newbie2 said:**
> [http://news.zdnet.co.uk/software/0,1000000121,39637586,00.htm](http://news.zdnet.co.uk/software/0,1000000121,39637586,00.htm)
That is pretty cool, I am looking foward to testing it out.

---

### Post by gnomeuser on 2009-04-07
> **haemulon said:**
> "kFreeBSD offers an alternative in case Linux is branded illegal by the SCO case or other threats," the developers wrote. "[COLOR="Red"]In legal terms, Linux sources are like a minefield[/COLOR]. kFreeBSD is much less vulnerable to such attacks."

They're not putting Linux in a good light by making statements like that.

Not just that, they are employing a technic better known as lying and not backing up ones slanterous claims with evidence.

Aside that, if these people are willing to work on it I am happy to see them succeed but it seem like a rather pointless bit of porting to me.

---

### Post by red_Marvin on 2009-04-07
Gnome-user, on the lying part are you talking about zdnet or debian? because on the debian wiki link in the article one of the bullet points contains that very text.

---

### Post by chris200x9 on 2009-04-07
I'm not suprised after all don't they have a hurd branch too?

---

### Post by Mehall on 2009-04-07
> **chris200x9 said:**
> I'm not suprised after all don't they have a hurd branch too?

Indeed.

HURD branch has yet to reach testing archives, as the BSD branch has just done.

BSD port has been under dev for a little while, but being in the archives means it's officially supported by Debian, unlike the HURD one.

---

### Post by Methuselah on 2009-04-07
> 
Sometimes it just seems inevitable that sooner or later Microsoft will stand up against Linux.


What are they waiting for?
It's 11:00!

Actually, the kind of tried by supporting SCO.

In any case, outlawing of the entire linux kernel everywhere is extremely unlikely IMO.

This is kind of ironic because legal proceedings involving BSD was part of the reason GNU adopted linux as the kernel, IIRC.
BSD was based on an emancipated body of source while linux was essentially built from scratch.
It's funny how things come full circle.

I guess lawyers need to eat.

---

### Post by Luffield on 2009-04-07
> **Methuselah said:**
> I guess lawyers need to eat.
Yeah, but sometimes I feel like they're trying to eat *me* :-?

---

### Post by CJ Master on 2009-04-07
> **chris200x9 said:**
> I'm not suprised after all don't they have a hurd branch too?

They do. :p

---

### Post by lykwydchykyn on 2009-04-07
> **red_Marvin said:**
> Gnome-user, on the lying part are you talking about zdnet or debian? because on the debian wiki link in the article one of the bullet points contains that very text.

As cool as this project is, it's unfortunate they make these kind of statements to justify the project.  At least they qualify their statements somewhat:
> 
Here are the reasons why we think Debian GNU/kFreeBSD could be preferred to other systems such as FreeBSD and Debian GNU/Linux.

They're not absolute truths, nor do we expect everyone to agree with them. So please don't engage in an endless discussion trying to convince someone that Debian GNU/kFreeBSD is the best. That kind of things do us more harm than good. 


I wouldn't think this project really needs justification.  I think it's pretty cool they can do this.  After all, we have a choice on just about everything else, why not kernels?

---

### Post by Mehall on 2009-04-07
Exactly.

Debian aims to provide the ultimate in choice and, eventually, usability (though not for new users, but for experienced users.)

They ahve made great strides, and supporting things like HURD and BSD is fantastic, IMO

---

### Post by Mr-Biscuit on 2009-04-07
Wasn't Ubuntu an experiment ?
When's the last time someone from the Linux community had a good FreeBSD or any BSD compatibility?
UFS2 would be a great file system to use.
BSD security along with SELinux policies.
Trying to remember which but, Desktop or PC BSD uses a lot of linux compatibility.

---

### Post by kk0sse54 on 2009-04-07
> **Mr-Biscuit said:**
> 
Trying to remember which but, Desktop or PC BSD uses a lot of linux compatibility.

A linux compatibility layer is available for all BSDs. That being said I'd like to see the NetBSD port updated sometime since it's been looking stagnant for a **long** time.

---

### Post by Mr-Biscuit on 2009-04-07
Is sysctl an option for you?
For me it was: compat.linux.osrelease=2.6.1
and then I put this in sysctl.conf.

---

### Post by Stupendoussteve on 2009-04-07
> **Methuselah said:**
> 
This is kind of ironic because legal proceedings involving BSD was part of the reason GNU adopted linux as the kernel, IIRC.
BSD was based on an emancipated body of source while linux was essentially built from scratch.
It's funny how things come full circle.


GNU has never adopted Linux. Hurd is the kernel they intended for GNU, and as always still develop. Other people put Linux in as the kernel with GNU as the userland.

I agree Linux cannot really be shut down. I could see parts of it removed if someone actually managed to claim and prove something, but a different implementation would probably come about.

---

### Post by InfinityCircuit on 2009-04-07
> **C!oud said:**
> A linux compatibility layer is available for all BSDs. That being said I'd like to see the NetBSD port updated sometime since it's been looking stagnant for a **long** time.

At the moment there will probably not be support for this Linux compatibility layer in Debian GNU/kFreeBSD, at least based on how I interpret the discussion here: [http://wiki.debian.org/ArchiveQualification/kfreebsd-i386](http://wiki.debian.org/ArchiveQualification/kfreebsd-i386)

Debian GNU/kNetBSD may yet live: [http://lists.debian.org/debian-bsd/2009/02/msg00000.html](http://lists.debian.org/debian-bsd/2009/02/msg00000.html)

Debian GNU/kFreeBSD is a very cool project and given its young state there are lots of opportunities to participate, I recently submitted patches to update debian/copyright for libfreebsd and the same work needs to be done in freebsd-libs and freebsd-utils. See:

[http://lists.debian.org/debian-bsd/2009/04/msg00004.html](http://lists.debian.org/debian-bsd/2009/04/msg00004.html)
[http://glibc-bsd.alioth.debian.org/TODO](http://glibc-bsd.alioth.debian.org/TODO)

---

### Post by haemulon on 2009-04-07
If some source code could not be re-written then the BSDs are the natural choice, 

But what type of source code could they possibly not rewrite? Some Microsoft patent?

It's likely that Linux is still vulnerable to litigation.   

Microsofts' actions over the FAT file system is the reminder to be cautious about Microsoft sponsored technologies like office Open XML, .NET, Mono, and Silverlight as they continue to get into the Linux distros. Just like MS allowed FAT to become a sort of standard.

I agree it all sounds like FUD, but MS still claims Linux infringes on over 200 of it's patents.

As long as they don't own up to that claim, the cloud hangs over Linux.

That is exactly what they wanted.

---

### Post by InfinityCircuit on 2009-04-07
At the moment, all proprietary code in the FreeBSD kernel (both closed-source drivers like ath and GPL-incompatible drivers like ZFS) have been cut from Debian GNU/kFreeBSD.

However, this might not last. There is talk of providing two kernels--one which has no GPL in it, which would allow distribution of native ZFS.

---

### Post by Methuselah on 2009-04-07
> **haemulon said:**
>    

Microsofts' actions over the FAT file system is the reminder to be cautious about Microsoft sponsored technologies like office Open XML, .NET, Mono, and Silverlight as they continue to get into the Linux distros. Just like MS allowed FAT to become a sort of standard.


Well said.
I'm not a big fan of the mono *dependency*
For compatibility purposes it's OK but
it is no better than less encumbered alternatives for new software development.

Sill, I'm not very fearful about MS patent FUD.
The FAT patent barely held up and I'm pretty sure MS would lose some of those 200 claimed patents and probably have some suits thrown at it too.

---

### Post by lykwydchykyn on 2009-04-07
What piece of software *isn't* vulnerable to litigation these days, with software patents being handed out like candy and companies continually settling instead of fighting?

---

