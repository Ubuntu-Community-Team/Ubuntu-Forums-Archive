---
title: "Hmmm... Ubuntu &amp; BSD?"
date: 2016-03-27
forum: Ubuntu, Linux and OS Chat
---

### Post by SantaFe on 2016-03-27
This sounds a little interesting.  According to F.O.S.S there's a new distro being worked on called UbuntuBSD, which is kind of funny considering it uses the XFCE DE.
> 
**UbuntuBSD Beta code named Escape From SystemD**

 The first beta release of UbuntuBSD is  out and it has been codenamed “Escape from SystemD”. It is based on  Ubuntu 15.10 and FreeBSD kernel 10.1. It ships with [Xfce desktop]("http://www.xfce.org/") and is designed for both desktop and server. [ZFS]("https://en.wikipedia.org/wiki/ZFS") support is included as well. It has text based installer.

Gotta love the bold title.  

Anyway, more info here:[URL="http://itsfoss.com/ubuntubsd-ubuntu-freebsd/"]http://itsfoss.com/ubuntubsd-ubuntu-freebsd/
[/URL]
Think it'll be a hit or a bust? ;)

---

### Post by QIII on 2016-03-27
One has to wonder if they have gotten permission from Canonical, Ltd. to use the trademarked name "Ubuntu"...

---

### Post by CharlesA on 2016-03-27
That isn't even a bloody codename. They should use it for the name of the distro if they hate systemd that much.

---

### Post by 1clue on 2016-03-27
It might be a little more compelling if the author had used a spell checker and grammar checker.

---

### Post by sammiev on 2016-03-27
I'll stick with the folks that can be trusted. :biggrin:

---

### Post by QIII on 2016-03-27
Interesting enough for me to email Canonical legal regarding Trademark infringement on both the name of the OS and the tagline.

---

### Post by PaulW2U on 2016-03-27
They've even got their own [Launchpad]("https://launchpad.net/ubuntubsd") page. :rolleyes:

---

### Post by montag dp on 2016-03-27
Needs more info. How could it be based on Ubuntu if it's BSD? The repos aren't even mildly compatible, unless they're rebuilding the Ubuntu repos from source for the BSD kernel (which I somehow doubt). And if not, how is it materially different from PC-BSD, which is already a BSD aimed for ease of use for the PC?

I played with FreeBSD for awhile on a VM, and while I really enjoyed many things about how it worked (even moreso than Linux), I didn't bother trying to install it to bare metal because everything I read made it sound like I'd have trouble getting my hardware working completely (even being a ThinkPad), and I'd have terrible battery life. This distro isn't going to do any better with those problems if it's BSD, even if it is in some vague way "based on Ubuntu."

---

### Post by CharlesA on 2016-03-27
From a quick glance at it, it looks like they are sticking a BSD kernel on an Ubuntu base. There are already distros to do a similar thing - Debian has one.

---

### Post by QIII on 2016-03-27
But it is distributed by Debian, so no trademark infringement.

---

### Post by SantaFe on 2016-03-27
Seems like one Would have to get permission to use the Ubuntu name, otherwise I could start my own line of Ubuntu Toasters. ;)

Think I'll stick with Linux on this one.

---

### Post by Bucky Ball on 2016-03-27
> **SantaFe said:**
> ... funny considering it uses the XFCE DE.


Not really. Xubuntu chose to use xfce4 also, along with other distros. It can be used on many Linux distros and is not owned by Canonical. It is [independently developed]("http://xfce.org/") and free to use on any distro it works on, including the one you're posting about.

From that link:

> Xfce is a lightweight desktop environment _for UNIX-like operating systems_.

It's not specific to any distro.

PS: I'll take one of them toasters, thanks. :)

---

### Post by 1clue on 2016-03-27
> **SantaFe said:**
> Seems like one Would have to get permission to use the Ubuntu name, otherwise I could start my own line of Ubuntu Toasters. ;)

Think I'll stick with Linux on this one.

There would be no infringement for a line of toasters.  Copyright/patent law only applies within the same market space.  Ubuntu is a word in a human language. Canonical has copyrighted it for use as the name of a computer operating system with associated software.  A toaster or a truck or a helicopter would have no relation to that.

---

### Post by montag dp on 2016-03-27
> **1clue said:**
> There would be no infringement for a line of toasters.  Copyright/patent law only applies within the same market space.  Ubuntu is a word in a human language. Canonical has copyrighted it for use as the name of a computer operating system with associated software.  A toaster or a truck or a helicopter would have no relation to that.
Cool, I'm looking forward to seeing "toasters for humans" on the shelves soon.  ;)

---

### Post by kevdog on 2016-03-28
I for one am really curious to try this distro.  I've never worked with a BSD system except on OS and maybe I dont consider this to be a "clean" or "pure" BSD implementation.  I really want to work with ZFS particularly on the / or root filesystem.  I'm aware Ubuntu rumors to be supporting ZFS on the soon to be released LTS, however I don't think it's meant for the root filesystem -- I could be wrong however.

---

### Post by 1clue on 2016-03-28
> **montag dp said:**
> Cool, I'm looking forward to seeing "toasters for humans" on the shelves soon.  ;)

There's a caveat:  Referencing a product explicitly in such a way as there is an indisputable reference without permission is a violation.  For example, if I paint my car with a big Coca-Cola logo but don't get permission from the Coca-Cola company, they could rightfully sue me for copyright infringement.  That said, I think some companies you could go to them and they would paint your car for you, for free, and maybe pay your gas while you drive around in it.  It's called an endorsement.

---

### Post by grahammechanical on 2016-03-28
> I'm aware Ubuntu rumors to be supporting ZFS on the soon to be released  LTS, however I don't think it's meant for the root filesystem -- I could  be wrong however.

[https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS)

[https://wiki.ubuntu.com/Kernel/Reference/ZFS](https://wiki.ubuntu.com/Kernel/Reference/ZFS)

It occurred to me that ZFS was the reason this distro is built on Ubuntu. That may be so. But there is ZFS support in Debian

[http://zfsonlinux.org/debian.html](http://zfsonlinux.org/debian.html)

Regards.

---

### Post by SantaFe on 2016-03-28
> **Bucky Ball said:**
> Not really. Xubuntu chose to use xfce4 also, along with other distros. It can be used on many Linux distros and is not owned by Canonical. It is [independently developed]("http://xfce.org/") and free to use on any distro it works on, including the one you're posting about.

From that link:



It's not specific to any distro.

PS: I'll take one of them toasters, thanks. :)

No, I meant with a name like UbuntuBSD, one would think it would be using Ubuntu Unity, not XFCE. ;)

---

### Post by deadflowr on 2016-03-28
> **SantaFe said:**
> No, I meant with a name like UbuntuBSD, one would think it would be using Ubuntu Unity, not XFCE. ;)
Wouldn't they have to create a port of unity for bsd?
where as xfce already has them.

Anyway, +1 to the idea of a bsd system with the simplicity of Ubuntu underneath

-1 to using such a childish codename.
(if that is what it actually is)

---

### Post by SantaFe on 2016-03-28
> **montag dp said:**
> Cool, I'm looking forward to seeing "toasters for humans" on the shelves soon.  ;)


[ATTACH=CONFIG]268039[/ATTACH]

I.m still having problems getting the logo part properly toasted.  Getting close though! ;)

---

### Post by grahammechanical on 2016-03-28
It gets confusing, in my opinion. UbuntuBSD but without Unity & with a BSD kernel. So, is it BSD? And It was Ubuntu 15.10 that made the switch to systemd in Ubuntu. So, how is it an escape from systemd? 

They should have done this with Devuan. And called it Escape from Alcatraz or Escape from the Planet of the Apes or the Great Escape. Oh, we are back to copy write issues. 

[URL="https://devuan.org/"]https://devuan.org/

[/URL]

---

### Post by 1clue on 2016-03-28
Oh come on you guys. Load Xubuntu and that's what they're porting.

The vast majority of software on Ubuntu is not owned or controlled by Canonical.  The vast majority of this software already works on FreeBSD. It's not that big a leap.

---

### Post by SantaFe on 2016-03-28
I did find someone reviewing it on YouTube.

[video=youtube;Yvhxe6WfhY8]https://www.youtube.com/watch?v=Yvhxe6WfhY8[/video]

Watched it, really don't see what is so interesting about it.

---

### Post by kevdog on 2016-03-30
So Ubuntu plans on releasing a kernel (standard linux kernel) with an included ZFS driver?  ZFS isn't supported by the mainline kernel, in fact Linus is strictly opposed to it.  So I'm guessing Ubuntu is going to patch the kernel with their ZFS implementation?

---

### Post by Bucky Ball on 2016-03-30
> **kevdog said:**
> So Ubuntu plans on releasing a kernel (standard linux kernel) with an included ZFS driver?  ZFS isn't supported by the mainline kernel, in fact Linus is strictly opposed to it.  So I'm guessing Ubuntu is going to patch the kernel with their ZFS implementation?

By 'Ubuntu', do you mean Canonical? If you do, don't know they've got anything to do with this.

---

### Post by 1clue on 2016-03-30
While the idea of putting an Ubuntu-based distro on FreeBSD sounds interesting, the stated purpose of this distro we're talking about makes me think that going all the way to FreeBSD is a bit overkill.

The Linux kernel neither requires nor cares about systemd. Most of the software on any Linux distro does not require systemd.  Systemd is a toxic init system which tries to do more than a standard init system, therefore requiring hooks into all sorts of places that normal init systems care nothing about.

While this matters not one bit to an average Ubuntu user, if one wants to evade systemd then one might suggest removal of systemd and adoption of those software packages not married to systemd directly.

I was at one point vehemently against systemd, and my Gentoo boxes and LTS Ubuntu Server boxes are still not using it.  However I don't think the argument is worth the effort. Lennart Poettering manages to make a cluster #^@% out of any project he touches, and avoiding those packages is extremely difficult because of the political pressure Redhat applies to force this software down everyone's throats. Right now I just want my systems to run, and that means accepting whatever the distro maintainers choose to support.

That said, if one were to avoid Gnome desktop (difficult for Ubuntu since Ubuntu is by definition using Gnome desktop) and a few other packages, one can get along nicely without systemd.  Xfce is a fairly nice mainstream WM which cares nothing about systemd, making it a good choice.

Bringing this back around to FreeBSD, most of the software you would have to avoid on Linux in order to eradicate systemd would also have to be avoided on FreeBSD.  The lion's share of what's on Ubuntu is also available in pretty much any other Linux distro and to a slightly more limited way to FreeBSD.  And Mac OS, and Windows. There's not much that's special about the Linux kernel to make it better than anything else.  Most of the software we run with Linux is available on any mainstream OS.

Systemd, (lucky us) is one of the things limited to Linux.

---

### Post by vince-vlara on 2016-04-02
> **1clue said:**
> 
The vast majority of software on Ubuntu is not owned or controlled by Canonical.  The vast majority of this software already works on FreeBSD. It's not that big a leap.

There is a lot of software in Ubuntu ported directly from FreeBSD (or a derivative) as evident from the man pages that are often copied directly without any amendments that would make the text more relevant to the software's use on Ubuntu.

I have been using FreeBSD for many years. My first install was on 5.25" floppy disks onto a 33Mhz 386DX server with 12 MBytes of RAM. I prefer Debian packages over FreeBSD ports which is why I use Ubuntu and Debian. I am not a fan of systemd on servers and my positive FreeBSD experiences have led me to experimenting in recent years with Debian kFreeBSD Wheezy. I'm glad that UbuntuBSD exists, I have installed it and it works well although Ansible gets a bit confused with it. 
I have also recently installed GuixSD, Devuan and DysonOS (based on illumos/OpenSolaris) I could easily stray from Linux if not for OpenStack being better supported on Ubuntu than FreeBSD. I think Canonical should make UbuntuBSD an official spin, I don't think that I am the only server admin evaluating alternatives right now.

---

### Post by mikodo on 2016-04-05
So how does this work? Can anyone explain it in layman's terms for me?

FreeBSD Kernel > No BSD-style init(8) > Ubuntu's shim to SystemD > that allows what services Ubuntu want it to run including, Debian packages?

Is that it?

Thanks.

---

### Post by 1clue on 2016-04-05
No. The idea is to escape from systemd altogether.

---

### Post by mikodo on 2016-04-05
Thanks. From following Devuan a while ago on the irc channel, they kept running into more and more packages depending on SystemD. I wonder if they are able to keep up with attending to that ... and if there will be ever be enough people behind UbuntuBSD to be able to do the same.

Addendum: I just read on Devuan site that that BSD have scrubbed Gnome of dependence on SystemD. I had last read, (what a year ago), that people in the BSD's camps were finding that hard to do. I guess, it is being done now. Being Xfce is agnostic about init systems, and with a long hx. of Xfce working well for BSD, I guess this is doable (Xfce or probably Xubuntu on FreeBSD). Interesting.

---

### Post by montag dp on 2016-04-05
> **mikodo said:**
> Thanks. From following Devuan a while ago on the irc channel, **they kept running into more and more packages depending on SystemD**. I wonder if they are able to keep up with attending to that ... and if there will be ever be enough people behind UbuntuBSD to be able to do the same.I think that's the main reason why people don't like SystemD in the first place.  Why should userland software depend on the init system?  It should start processes, and that's it.

FWIW, there are several well-known Linuces that don't use SystemD.  Slackware and, I believe, Gentoo, are two examples.  Although I know Slackware stopped packaging Gnome several years ago, which probably helps avoid SystemD.

---

### Post by mikodo on 2016-04-05
> **montag dp said:**
>  -snippet -Although I know Slackware stopped packaging Gnome several years ago, which probably helps avoid SystemD.Thanks.

I read earlier now, on the Devuan site that BSD has scrubbed Gnome of its' dependancies of SystemD and that Devuan devs are keeping an option open to having it as a second desktop to Xfce. How easy that is I dunno or, how *sustainable* it can be.

---

### Post by 1clue on 2016-04-05
There's a whole lot of angst about this on Gentoo forums.

The big problem is that "scrubbing packages of systemd" is a moving target, and somewhat of an avalanche. The more distros adopt systemd, the more people in other projects will find a way to hook into it.  Inevitably they will do so in such a way that is difficult to reverse.

The biggest problem organization for this is RedHat. Lennart Poettering works there (known for pulseaudio, another project almost as terrible as systemd), as do the rest of the teams who are busy making Linux be as Microsoft-like as possible. Whether Poettering follows RedHat's agenda or RedHat backs Poettering's agenda I don't really know, but there are a whole lot of paid developers at RedHat finding new ways to tie all their products together into a herculean knot.

Most distros are NOT backed by a large corporation, and so cannot prevent this ... I want to say words that will break the terms of use. Most commercially-backed distros (like Ubuntu) have their own agenda and either don't care about systemd enough to do anything about it, or are on-board with the rape of freedom to choose.

Take Canonical for example.  By definition, Ubuntu is based on Gnome. Gnome is heavily influenced by RedHat. They have coded Gnome to directly rely on systemd, which means that Canonical must either go along with this or they must rewire Gnome. Each new version of software that comes out, there are more and more dependencies on systemd. So countering this takes time from paid developers at Canonical to undo what paid developers are doing at RedHat are doing, rather than doing things that make Ubuntu better for everyone.

Taking this further, if Canonical gives in with gnome then they must adopt systemd for all the derivatives like Xubuntu or Kubuntu or branch the software repositories and provide separate binaries for each window manager.

I sincerely hope that either someone comes up with a better alternative to systemd which will be accepted by RedHat (.000000001% chance) or systemd actually solves all its inherent problems (.01% chance) or people come up with packages which divorce systemd's non-init-like behavior from systemd so a regular init system can take its place.  That last one is a hack, so I have little hopes that it will work out that way.

Best wishes.

---

