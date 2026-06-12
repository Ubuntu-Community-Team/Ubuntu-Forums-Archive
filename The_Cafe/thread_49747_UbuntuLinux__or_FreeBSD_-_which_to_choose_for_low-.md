---
title: "Ubuntu/Linux  or FreeBSD - which to choose for low-end hardware?"
date: 2005-07-17
forum: The Cafe
---

### Post by agger on 2005-07-17
This is a reformulation of a previous post of mine, regarding
my rather negative experience with "lite" installs of Ubuntu and
other Linux distros - while I simply adore the way Ubuntu installs
itself in a userfriendly way to a userfriendly system on more recent 
machines like the laptop I usually use... but, here goes:

My own experience with "lite" is this:

I have an IBM Aptiva, 450 MHz, 128 megas of RAM, which we like to use
for Internet, text processing, instant messaging, etc.

Normally I use a modern Centrino laptop running Ubuntu.
At first, I did a normal Ubuntu install on the Aptiva, but as soon as you have more
than a couple of tabs open in Firefox, or several applications running at once,
it simply dies for lack of memory.

I then followed the instructions on installing Ubuntu for low memory systems
discussed here:

[http://www.ubuntuforums.org/showthr...8&page=10&pp=10](http://www.ubuntuforums.org/showthr...8&page=10&pp=10)

It works, but it's not easy to get everything right: I couldn't get my sound card to work at all, nor could I get it to set background image or colour.

Then I tried other Linux distros, such as dyne:bolic ([http://www.dynebolic.org/](http://www.dynebolic.org/)) , which runs from a live CD and is a quick'n'dirty way of getting and old PC to work - it does have the disadvantage of crashing once in a while.

Now, I've ended up leaving Linux and giving FreeBSD a spin instead, and my conclusion up till now is this:

FreeBSD may be more suitable for low-end machines than Linux.
Like I said, the system simply dies if I run on a normal Ubuntu installation with GNOME for more than five minutes or so.

With IceWM, things are better, but this definitely doesn't work "out of the box".

With FreeBSD, my computer performs *excellently* running either KDE or Gnome - I can run Firefox, emacs, office applications, whatever, and it all works very reasonably, and the system never dies.

The installation is NOT very straightforward or "out-of-the-box", one might add, but on the other hand the FreeBSD  handbook is excellent and takes you through every step of the process.

I don't know why this is - possibly, the FreeBSD kernel is less demanding, or possibly the xorg port for FreeBSD performs better? Maybe Linux is (for some reason) less suited for low-end systems?

I think that making an Ubuntu lite is a really good idea, and will probably also want to give it a spin - but if you need to work with low-end computers, perhaps FreeBSD is more suited for the task than Linux; and maybe an "Ubuntu Lite" might simply be a port of the normal Ubuntu installation and setup to FreeBSD?
 A FreeBSD Ubuntu or something like that?

Anyway - are there any obvious difference between the BSD and Linux kernels which might explain FreeBSD's better performance for low-RAM systems?

regards
Carsten Agger
__________________
[http://www.modspil.dk](http://www.modspil.dk)
- fordi tiden kræver et MODSPIL!

---

### Post by UbuWu on 2005-07-17
Ubuntu lite:
[www.ubuntulite.org](www.ubuntulite.org)
Very new... so I would like to hear about any experiences with it...

Or otherwise you could try Damn Small Linux (DSL) which seems to do a good job for older pc's.

---

### Post by DJ_Max on 2005-07-17
> Maybe Linux is (for some reason) less suited for low-end systems? 
No, Linux is just a kernel, so you can't be all distro that use the Linux kernel in the same category. Ubuntu may not be sutible for low-end systems, but another Linux distro may be, such as the ones UbuWu pointed out.

BSD is completely different in the terms of Kernel and it's centralized base system, which Linux lacks, which is why you have the results you have.

---

### Post by poofyhairguy on 2005-07-17
Hmmm...if BSD works then great. If it was me I would have bought some more RAM, or used XFCE. I have XFCE and Ubuntu on a machine lessor that that and its fine.

---

### Post by egon spengler on 2005-07-17
[QUOTE=poofyhairguy]Hmmm...if BSD works then great. If it was me I would have bought some more RAM, or used XFCE. I have XFCE and Ubuntu on a machine lessor that that and its fine.[/QUOTE]
 my other pc is a 900mhz celeron with 128mb ram and even with xfce or fluxbox it's incredibly slow. [beatrix](http://www.watsky.net/) was designed for low end machines (64mb and up i believe) and works well with mine.

like max said it's not specifically that bsd is better/faster (though this thread has made me decide to give bsd a trial), just the distros vary

---

### Post by BWF89 on 2005-07-17
> FreeBSD may be more suitable for low-end machines than Linux.
I thought it was common knoledge that BSD based distros are better on lower end computers that Linux distros.

---

### Post by benplaut on 2005-07-17
[QUOTE=egon spengler]my other pc is a 900mhz celeron with 128mb ram and even with xfce or fluxbox it's incredibly slow. [beatrix](http://www.watsky.net/) was designed for low end machines (64mb and up i believe) and works well with mine.

like max said it's not specifically that bsd is better/faster (though this thread has made me decide to give bsd a trial), just the distros vary[/QUOTE]

ditto on BeatrIX... it is actually a stripped down Ubuntu, that connects to the Ubuntu repos for updates and more programs

i use it on a few old machines at school- works like a charm! (much better than DSL, even)

---

### Post by BWF89 on 2005-07-17
[QUOTE=benplaut]i use it on a few old machines at school- works like a charm! (much better than DSL, even)[/QUOTE]
DSL was the first Linux distro I ever used (the live cd edition). I remember having to slide my pc out of it's wooden shelf below the keyboard and reconnect the mouse to the USB ports in the front of it because DSL wouldn't recognise my mouse if the USB port coming out of the cord was hooked up to one of those adaptors for older mouses in the back of the PC.

---

### Post by az on 2005-07-17
[QUOTE=BWF89]I thought it was common knoledge that BSD based distros are better on lower end computers that Linux distros.[/QUOTE]

BSD runs better, and runs on more architectures than linux, but do not expect it to support as many wireless cards and other peripheral hardware doodads than linux.

BSD licencing is generally different than linux (BSD type licence versus GPL).  That may explain why linux is more popular...

---

### Post by DJ_Max on 2005-07-17
[QUOTE=azz]BSD runs better, and runs on more architectures than linux, but do not expect it to support as many wireless cards and other peripheral hardware doodads than linux.

BSD licencing is generally different than linux (BSD type licence versus GPL).  That may explain why linux is more popular...[/QUOTE]
Somewhat, even condsidering the GPL license is more restrictive. 

BSD supports most common home user hardware, and most people will never have the hardware is doesn't support.

---

### Post by TravisNewman on 2005-07-17
" Somewhat, even condsidering the GPL license is more restrictive."

True, it's a difference in the most freedom for the developer vs the most freedom for the user.

I really like FreeBSD, and FreeBSD's ports system (what Gentoo's portage is based off of) is great. It DID seem to be a bit speedier, but there are a couple things I have that are unsupported.

---

### Post by DJ_Max on 2005-07-17
[QUOTE=panickedthumb]" Somewhat, even condsidering the GPL license is more restrictive."

True, it's a difference in the most freedom for the developer vs the most freedom for the user.

I really like FreeBSD, and FreeBSD's ports system (what Gentoo's portage is based off of) is great. It DID seem to be a bit speedier, but there are a couple things I have that are unsupported.[/QUOTE]
 <offtopic>Yeah, I miss Gentoo. But with this new HD, I'm considering NetBSD on my iMac....</offtopic>

> True, it's a difference in the most freedom for the developer vs the most freedom for the user. 
That's a real good point, probably the best I've seen in the many BSD-style vs GPL licensing.

---

### Post by TravisNewman on 2005-07-17
I love to tinker. That's why I love gentoo. But when I tinker with Gentoo, it takes up all my time. That's why I went searching for something else and found Ubuntu.

Never used NetBSD. I hadn't thought of using it on my iMac. It's an older iMac-- 450 mhz. It might run smoother than Ubuntu.

---

### Post by TravisNewman on 2005-07-17
" That's a real good point, probably the best I've seen in the many BSD-style vs GPL licensing."

You'd be surprised how many people start screaming at me over that one.

---

### Post by DJ_Max on 2005-07-17
[QUOTE=panickedthumb]" That's a real good point, probably the best I've seen in the many BSD-style vs GPL licensing."

You'd be surprised how many people start screaming at me over that one.[/QUOTE]
 Yeah, well I have a lot to say about most people/zealots...

NetBSD was made to run on tons of different architectures. It just that the install for Apple computers are "different" then what I'm used to. But you may be right about it running smoother, thats the results the orginal poster found out on his other x86 computer. Which I really don't know how to explain.

---

### Post by papangul on 2005-07-18
I suggest you try out the following:
1.[Gentoo jackass!](http://jackass.homelinux.org/) 
2.[Qingy](http://qingy.sourceforge.net//) as login manager.
3.IceWM as window manager. With Qingy it works "out-of-the-box". Also there are some good supporting programs like Icemc(menu editor), IceWMCP(control panel), using these you can easily configure icewm.
4.Emelfm is a fast file manager.
5.Beaver is a fast tabbed text editor.

Edit:Use the 2.6.12 kernel. I got some speed incease with it(maybe hallucination!).

---

### Post by agger on 2005-07-18
[QUOTE=panickedthumb]" Somewhat, even condsidering the GPL license is more restrictive."

True, it's a difference in the most freedom for the developer vs the most freedom for the user.

I really like FreeBSD, and FreeBSD's ports system (what Gentoo's portage is based off of) is great. It DID seem to be a bit speedier, but there are a couple things I have that are unsupported.[/QUOTE]

I don't understand - you are saying that the BSD license is giving more freedom to the developer, and the GPL more to the user?

(The main difference is the BSD license allows you to modify and include the 
modifications in a proprietary product, i.e., it's not copyleft - but while I personally
prefer the GPL scheme, I don't see it makes a lot of a difference for me as 
a user).

---

### Post by agger on 2005-07-18
[QUOTE=azz]BSD runs better, and runs on more architectures than linux, but do not expect it to support as many wireless cards and other peripheral hardware doodads than linux.

BSD licencing is generally different than linux (BSD type licence versus GPL).  That may explain why linux is more popular...[/QUOTE]

Well, thanks for the lots of varied response, anyway - I don't really understand the difference between Linux and BSD's centralized base system, but I suspect I should try reading a bit about the architectural differences between the systems.

Getting peripherals to work in BSD generally requires that you edit some configuration files by hand, as root - this *is* a bit of a bother, but the BSD handbook does a very good job of taking you through the steps.

---

### Post by agger on 2005-07-18
Actually, I see there is a BSD distro specifically aimed at desktop users,
PC-BSD:

[http://www.pcbsd.org](http://www.pcbsd.org)

On the other hand, it's possible to install FreeBSD from the "official"
downloadable ISO images at [http://www.freebsd.org](http://www.freebsd.org) and "roll your own"
distro and installation after downloading;

but, now I've got FreeBSD to give me a really nice GNOME desktop on 
my old Aptiva, I think next time I'll try Ubuntu Lite :-)

---

### Post by DJ_Max on 2005-07-18
[QUOTE=agger]I don't understand - you are saying that the BSD license is giving more freedom to the developer, and the GPL more to the user?
[/QUOTE]
The other way around I believe. As you said, the BSD-style licensing is more open towards where you use it, and what software you bundle it with, GPL was one of the downfalls of XFree86, as the GPL is biased towards other licensing.

---

### Post by BWF89 on 2005-07-18
Here is a very simple way of defineing the 2 liscences to a complete Linux newb without getting into all the Debian Free Software Standerds thing:

GPL is a public domain liscence. But if you modify the software you have to put it into public domain again.

BSD is a public domain liscence but when you modify it you have to give the origional author credit. You can put it in the public domain or you can lock it down.

---

### Post by agger on 2005-07-19
[QUOTE=DJ_Max]The other way around I believe. As you said, the BSD-style licensing is more open towards where you use it, and what software you bundle it with, GPL was one of the downfalls of XFree86, as the GPL is biased towards other licensing.[/QUOTE]

Well, I'd look at it this way:

BSD-style licensing lets you incorporate the code in any application and bundle it with whatever software you want and release it under a free or proprietary license as you see fit.

This (to me) seems like greater freedom for the developer.

GPL licensing, on the other hand, means that derivative works must also be under the GPL, which means that if somebody makes and sells a modification or enhancement of a program under the GPL, the new program will eventually become free to share and distribute the way the original work was.

And this, to me, seems like greater freedom for the user.

---

