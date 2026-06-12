---
title: "Ubuntu as fast as Arch?"
date: 2008-06-18
forum: The Cafe
---

### Post by zephyrus17 on 2008-06-18
I downloaded the Arch Core install, and was going to install it to try it out, but was wondering if it's possible for me to configure Ubuntu to be as lean and streamlined as Arch? This way I don't have to swap distros. :D

---

### Post by Joeb454 on 2008-06-18
You can do a minimal install of Ubuntu, so you get to choose what packages you install (that way you don't even have to install Xserver :p)

---

### Post by Inxsible on 2008-06-18
I agree with Joeb. Build from the bottom up. I always do that now.

I am currently using Debian core to build on top of. I find that Debian is much more stable and fast than Ubuntu.

Just my 2 cents

---

### Post by zephyrus17 on 2008-06-18
How do you do that bottom up thing? When I install Ubuntu all I see is the normal install.

Well, if I'm going to swap to Debian, I might as well go to Arch. Because that's the fastest(or so I've heard).

---

### Post by Joeb454 on 2008-06-18
Perhaps this wiki page will help:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by zephyrus17 on 2008-06-18
What about the partitions? People at arch seperate /var and /boot, etc. What would be a good strategy for Ubuntu?

---

### Post by Joeb454 on 2008-06-18
Personally - I haven't a clue. I have / and /home but that's all, It's up to you. You could have them all on separate partitions :)

---

### Post by tjwoosta on 2008-06-18
the reasoning for having directories on seperate partitions is that if something goes wrong with one sector of the harddisk you can fix only that piece and all others will remain untainted 

(like say you need to reinstall ubuntu because updates screwed it up, ..lol) you could do so very easily if you had all of your files and programs and settings on a seperate partition from the main system files)

---

### Post by Dr Small on 2008-06-18
No. Ubuntu can't be as minimalistic as Arch. 'Nough said.

---

### Post by ajmorris on 2008-06-18
You could also look into debootstrap if you want a really minamilist system. Deboostrap is used to create a very minimalist debian system. It is essentially designed for a chroot environment... but you can do it without it being a chroot if you wish. Once you have installed the base system, you can then build the rest of your system from there, installing whatever you wish. Currently my ubuntu is very lean indeed... about 200mb-ish in size, and only that big because of the kernel headers. (no X installed on it)
 
AJ

---

### Post by ajmorris on 2008-06-18
> **Dr Small said:**
> No. Ubuntu can't be as minimalistic as Arch. 'Nough said.
 
 
pfft :P
/me hates arch

---

### Post by Dr Small on 2008-06-18
> **ajmorris said:**
> pfft :P
/me hates arch
Hate Arch all you want. It doesn't help the matter any :p
Ubuntu can only be *so * minimalistic stripped down. Arch still beats that.

---

### Post by ajmorris on 2008-06-18
> **Dr Small said:**
> Hate Arch all you want. It doesn't help the matter any :p
Ubuntu can only be *so *minimalistic stripped down. Arch still beats that.
 
Only because Arch comes stripped down. Ubuntu is designed to acommodate users to linux, new and old. If ubuntu was as stripped down as Arch to begin with, users on their first ever linux OS would have no idea what to do. Same as gentoo, and i have to say, arch is not as minimalistic as gentoo ;)
 
Anyway... better not discuss this here...

---

### Post by Dr Small on 2008-06-18
Ubuntu wasn't made to be minimalistic, but as a bloated, giant, GUI friendly gateway for newbies, and Arch WAS made to be minimalistic. That's the reason I use it and prefer it.

But as to the question, No. Ubuntu is not as fast as Arch, nor can it ever be.

---

### Post by ajmorris on 2008-06-18
> **Dr Small said:**
> Ubuntu wasn't made to be minimalistic, but as a bloated, giant, GUI friendly gateway for newbies, and Arch WAS made to be minimalistic. That's the reason I use it and prefer it.
 
But as to the question, No. Ubuntu is not as fast as Arch, nor can it ever be.
 
It can be as fast as Arch. A minimalistic debootstrap with ubuntu base files + repos is just as fast as arch. In fact... a minimal cd install can be as slim as arch, the only thing that you would need to do is a custom kernel as the arch kernel is quite fast.

---

### Post by Dr Small on 2008-06-18
But why go through all that when there is a distribution called ArchLinux? ;) Why make Ubuntu like Arch when you could *use* Arch ? :D

---

### Post by zephyrus17 on 2008-06-19
> **Dr Small said:**
> But why go through all that when there is a distribution called ArchLinux? ;) Why make Ubuntu like Arch when you could *use* Arch ? :D
Dr Small, my thoughts exactly. If Ubuntu can't be as small, then I might as well switch.

ajmorris, you mentioned Gentoo as well. What other distros are minimal like Arch and Gentoo?

---

### Post by stairwayoflight on 2008-06-19
Ubuntu may not be as minimalistic as Arch, but depending on what you want it may still save you time to get there. The real strength of Ubuntu is the package management system, apt. Get Linux from Scratch if you want. You can download and compile everything by hand. Or Slackware, it will be a notch or two easier than that. You have to find the level of abstraction you want to live with.

But after 5 years of Linux experience, you may find you are less interested in wasted cpu cycles on the odd library you don't need, then knowing you have a system that knows how to bring it self up, bring itself down, and install additional software. In my book, that's a Debian or Ubuntu system.

However at the end of the day, to learn Linux you should focus on getting the system you use to do what you want. Ie. don't look for other distributions to do the next task, use your current distro to do it. If you can't without too much work, it may be time to switch.

---

### Post by zephyrus17 on 2008-06-19
That's very true.. Is the pacman manager for arch inferior to Ubuntu's? I was blown away with the power of the ubuntu's synaptics..

And once again, true. It's a stable system that matters most of all, and ubuntu is very stable indeed.

---

### Post by ajmorris on 2008-06-19
> **zephyrus17 said:**
> That's very true.. Is the pacman manager for arch inferior to Ubuntu's? I was blown away with the power of the ubuntu's synaptics..

And once again, true. It's a stable system that matters most of all, and ubuntu is very stable indeed.

Pacman is rather powerful, i suppose it comes down to preference as well.
My favourite is portage (for gentoo) however, i prefer apt to pacman.

---

### Post by Dr Small on 2008-06-19
> **zephyrus17 said:**
> That's very true.. Is the pacman manager for arch inferior to Ubuntu's? I was blown away with the power of the ubuntu's synaptics..

And once again, true. It's a stable system that matters most of all, and ubuntu is very stable indeed.
Pacman is very fast, and as ajmorris said, very powerful. Not to mention the AUR (Arch Linux Repository) where you can find unofficial packages (similar to getdeb.net) and can download make the package and install it with pacman.

---

### Post by ajmorris on 2008-06-20
> **Dr Small said:**
> Pacman is very fast, and as ajmorris said, very powerful. Not to mention the AUR (Arch Linux Repository) where you can find unofficial packages (similar to getdeb.net) and can download make the package and install it with pacman.


The default repositories in arch are rather small however, can get annoying at times.

---

### Post by zephyrus17 on 2008-06-20
There's a GUI for it, right? And what's yaourt?

---

### Post by ajmorris on 2008-06-21
> **zephyrus17 said:**
> There's a GUI for it, right? And what's yaourt?

Yaourt is a pacman front end of some sort, not sure if there is a gui... i gave up on arch a while ago, i dont really like it.

---

### Post by HunterThomson on 2008-06-22
I just re-formated my HDD yesterday after much looking for a slim-Fast-and above all a "Rolling Distro" and installed ArchLinux:)

I have to say it is WAY Faster then Ubuntu was on my box. NO contest hands down Faster.... No contest hands down way more slim/made to fit then Ubuntu... I could not use Hardy 8.04 do to HW problems that were no problem on 7.10. However, I am running a 2.6.25 Kernel and KDEbase 3.5.9 with no problems with Archlinux. AND it will stay that way "Unlike Ubuntu" if some new upgrade go's wrong I can just roll back that ONE package:)

I really liked Ubuntu and would not be were I am today with out it:guitar:

But now that I know enough about Linux I needed a distro that I could build myself with only the programs/4hardware I use. And, I was getting tired of complaining on the Ubuntu forums about stuff braking with updates.

---

### Post by zephyrus17 on 2008-09-04
After about a month with Arch, and still having problems such as:
keyboard shortcuts problems,
inability to setup the thinkpad-dedicated kernel,
inability to fix the problem of the fan being constantly on,
and an overall confusion of what I'm doing.

It's as if I'm seeing the problem, and just googling the answer, and solving it (most of the time partially or not at all), without understanding what's going on. I admit it's my incompetence to blame. But, maybe, Arch is a bit too much too soon for me.

Frankly now, I can't really be bothered with getting my bootup to be 4seconds faster or tweaking for maximum performance. My laptop is rather new, and so experiences no lag in the first place. I just need a system that I can use for my daily stuff, and I'm quite happy.

---

### Post by kpkeerthi on 2008-09-04
Ubuntu != Arch

Both are great distros. But we are comparing apples to oranges. I will still recommend Ubuntu to linux beginners any day.

Not everyone can appreciate the design & philisophy of Arch (go figure!). I personally prefer Arch over Ubuntu. As for the package management in Arch, I can even dare to say that pacman is better than apt* in every way. Shaman is a front-end to it, based on QT. 

My Arch runs GNOME + daemons + other utilities, similar to a standard Ubuntu desktop. Except for the boot time, where Arch beats Ubuntu hands down, I find both the desktops as snappy as each other.

---

### Post by zephyrus17 on 2008-09-04
> **kpkeerthi said:**
> Ubuntu != Arch

Both are great distros. But we are comparing apples to oranges. I will still recommend Ubuntu to linux beginners any day.

Not everyone can appreciate the design & philisophy of Arch (go figure!). I personally prefer Arch over Ubuntu. As for the package management in Arch, I can even dare to say that pacman is better than apt* in every way. Shaman is a front-end to it, based on QT. 

My Arch runs GNOME + daemons + other utilities, similar to a standard Ubuntu desktop. Except for the boot time, where Arch beats Ubuntu hands down, I find both the desktops as snappy as each other.
Yeah.. I'm starting to think that my 1 year with Ubuntu just doesn't cut it for me to use Arch with as much confidence. I'm always having the fear that something isn't functioning or worried if my cpu scaling is working, etc.

---

### Post by mips on 2008-09-04
> **zephyrus17 said:**
> There's a GUI for it, right? And what's yaourt?

There are GUIs like Shaman and others for pacman. Yaourt is a CLI app but uses the exact same command syntax as pacman. Yaourt will give you access to AUR which pacman does not do. So yaourt -S AppXXX will quite happily install a source app from AUR as simply as pacman installs a binary from the repos. Yaourt gives you access to both so it is what I use by defaut.

As for the original question I don't think Ubuntu will be as fast as Arch. Why jump through so many hoops trying to get to what Arch does when you can simply use Arch? The package manager is excellent.

---

### Post by wisedrunkard on 2008-09-04
I'm a total newb how do i start my own thread... i have a problem i need help with, thx for the help

---

### Post by zephyrus17 on 2008-09-04
Yeah.. Yaourt is pretty powerful stuff.

---

### Post by zephyrus17 on 2008-09-04
> **wisedrunkard said:**
> I'm a total newb how do i start my own thread... i have a problem i need help with, thx for the help
On the top right-ish area there's a place to click "New Thread"

---

