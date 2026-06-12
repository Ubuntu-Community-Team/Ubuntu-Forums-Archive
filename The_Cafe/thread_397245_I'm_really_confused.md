---
title: "I'm really confused"
date: 2007-03-30
forum: The Cafe
---

### Post by Ozor Mox on 2007-03-30
Just to make myself a bit more knowledgeable about Ubuntu and Linux as a whole, I thought I'd read up on it a little. Sheesh! I think I've just about got my head around the whole GNU/Linux thing in that Linux is just the kernel, and that GNU has its own Hurd kernel that isn't ready yet. And the whole thing of free software (as in freedom) and open source software (as in technically better because many people can change it)...of which the latter happens to be the idea which I first became interested in. This big naming row seems pretty significant as well, though I'm not about to start calling it GNU-slash-Linux as there are so many other things that go into it. In fact, I'd rather just call it Ubuntu! So here are some things:

1. How important IS free software? I think the idea is great, but then I have no problem buying software or using non-free software to make my desktop work as well as I can get it to, just like the next guy trying to get a usable Linux desktop. Though I mean, in the most extreme hypothetical situation, could Ubuntu just end up becoming another proprietary operating system if such formats were put in to it? I don't see this as being possible, which leads to...

2. Ubuntu is licensed under the GNU GPL meaning all source code must be provided on distribution, correct? Hence making the above scenario an impossibility. But then why have I read that Ubuntu includes non-free binary drivers and was originally planned to include them in Feisty (although as I understand it that as been made optional now). As the source code is not available for the binaries, doesn't it break GPL licensing?

3. How much GNU stuff does Ubuntu have. Is it like Linux kernel, GNU tools and desktop environment (if GNOME not KDE of course), and then applications from various other sources form the distribution?

None of this is of course essential, I just like to know things! :)

---

### Post by Brunellus on 2007-03-30
GENERALLY, my line is "Free Softwhere when possible, non-free only when necessary."  I tend to run and favor free software solutions for my own personal use, and limit my non-free software to the extent that I'm able.

I have one computer that is all Free Software--NO proprietary!--which works out fine for me.  Others on my network are a mix.

---

### Post by 23meg on 2007-03-30
> **Ozor Mox]1. How important IS free software? [/QUOTE]

As important as you'll end up thinking it is, after some research and experience. For me, very important said:**
> could Ubuntu just end up becoming another proprietary operating system if such formats were put in to it?

Proprietary drivers/firmware, proprietary applications, and proprietary formats are separate avenues. Ubuntu does ship some proprietary drivers and firmware in the restricted component, but will never include proprietary fundamental components (kernel, init, shell, windowing system etc.), proprietary format support and proprietary applications by default. 

Whether it can theoretically become a "proprietary operating system" depends on where you draw the line. If even shipping the smallest binary blob as a compromise to get some systems (that won't otherwise work) working makes it a proprietary OS, then Ubuntu already is a proprietary OS. If shipping a partially proprietary basic toolset does, or shipping proprietary formats or applications does, it isn't, and won't be.

> **Ozor Mox]2. Ubuntu is licensed under the GNU GPL meaning all source code must be provided on distribution, correct? Hence making the above scenario an impossibility. But then why have I read that Ubuntu includes non-free binary drivers and was originally planned to include them in Feisty (although as I understand it that as been made optional now). As the source code is not available for the binaries, doesn't it break GPL licensing?[/QUOTE]

Ubuntu isn't licensed under the GPL as a whole said:**
> 3. How much GNU stuff does Ubuntu have. Is it like Linux kernel, GNU tools and desktop environment (if GNOME not KDE of course), and then applications from various other sources form the distribution?

Almost everything Ubuntu ships by default is licensed under the GPL or GPL-compatible licenses. The licensing criteria for inclusion in the Main component are more or less the [Debian Free Software Guidelines]("http://en.wikipedia.org/wiki/Debian_Free_Software_Guidelines"). 

More on components here: 

[http://www.ubuntu.com/community/ubuntustory/components](http://www.ubuntu.com/community/ubuntustory/components)

---

### Post by arbulus on 2007-03-30
It's really great that you're trying to get a better understanding of everything.  There are a lot of things that can be confusing in the open source world, so hopefull this thread will help.

You mentioned GNU/Linux naming and referring just to Ubuntu.  I think that makes sense.  I'm not that familliar with the GNU project, so I can't really comment on it, but there are so many flavors of Linux that you can't simply say "I run Linux" and make any sense.  One who uses Gentoo or Slackware is going to be familliar with a system that is very different from that of Ubuntu or Debian.  Just as would one would who runs Red Hat, Fedora, or Yellow Dog.  So referring the the specific name of the distro you use is sensible.

Free software is an incredible thing.  It allows us to create software, distribute information, that can be obtained by a user either free of cost, or for a minimal cost, and then modified and redistributed, thus sharing the changes and improvements that each user can make.  You have a community working together to share technology and capability with each other so that we better each other and can all have access to an entire world of information, so no one entity is trying to hold a monopoly on the keys to that gate.  The open source community tears down those gates and barriers that prevent the average user from being left out because they can't afford a $300 office suite so that they can make a spreadsheet.  

Since Ubuntu is committed to open software that is free of charge and free to distribute, I can't see that it would ever become proprietary.  There are other distros that include proprietary software and install it by default, such as MP3 codecs, such as Mandriva, but the cost that Mandriva incurs for licences is passed on to the user in that you have to pay for the distro and you're not free to redistribute it as a whole.  There are proprietary options in Ubuntu, but they do not install by default, such as MP3 support, Adobe plugins, etc.

---

### Post by Ozor Mox on 2007-03-31
Thanks for this information! So from my understanding, as long as the Linux kernel is licensed under a free software license like the GPL, people can always build whatever distribution they like on top of that (shown by how many choices there are now). It'd be nice to know that there will always be a freely available Linux there because I like Ubuntu a lot but I know that companies need to make money. From what I can tell, Ubuntu does this by charging for commercial support, and by the fact that it is supported by many different companies other than Canonical. That's great, but I like to know that a free Linux-based operating system will always be around because it is so nice to know that I can burn as many CDs of Ubuntu/Linux, and install it on as many computers as I like without the nagging feeling that what I'm doing is illegal, or that my software will turn itself off after 30 days.

I hope this never goes away.

---

### Post by 23meg on 2007-03-31
Mark Shuttleworth has expressed multiple times that Ubuntu will always be free of charge; see [his page on the wiki]("https://wiki.ubuntu.com/MarkShuttleworth") for details.The Ubuntu Foundation, in which he invested a large capital, also ensures that Ubuntu will continue to exist regardless of the status of Canonical or himself.

---

### Post by IYY on 2007-03-31
> **Ozor Mox said:**
> 
1. How important IS free software? I think the idea is great, but then I have no problem buying software or using non-free software to make my desktop work as well as I can get it to, just like the next guy trying to get a usable Linux desktop. Though I mean, in the most extreme hypothetical situation, could Ubuntu just end up becoming another proprietary operating system if such formats were put in to it? I don't see this as being possible, which leads to...


For some of us it's the most important thing, for others it's entirely unimportant. Everyone draws a line between ethics and convenience, but not everyone's line is the same. 

> 2. Ubuntu is licensed under the GNU GPL meaning all source code must be provided on distribution, correct? Hence making the above scenario an impossibility. But then why have I read that Ubuntu includes non-free binary drivers and was originally planned to include them in Feisty (although as I understand it that as been made optional now). As the source code is not available for the binaries, doesn't it break GPL licensing?

Ubuntu is not a single piece of software; it's a package. In that package, not every component has to be GPL-licensed.

> 3. How much GNU stuff does Ubuntu have. Is it like Linux kernel, GNU tools and desktop environment (if GNOME not KDE of course), and then applications from various other sources form the distribution?

Mark Shuttleworth says that he thinks that the line should be drawn as follows: all official applications must be GPL licensed. The kernel, core-utilities, and any other utilities essential for operation must be GPL licensed. Modules, like drivers, *can* be proprietary. I am not sure when he announced this, but I heard it in a recent audio interview.

---

### Post by Ozor Mox on 2007-04-01
So not only does Ubuntu have backup funds and support to keep it going and, from reading that wiki, a very committed founder, but the nature of the GPL license is that software licensed under it cannot be "de-licensed" so to speak, so the Linux kernel, GNU tools, X, KDE/GNOME, and all the other many applications that are in distributions like Ubuntu will always have their source code freely available and can be developed by anyone? (i.e. a free-as-in-freedom operating system and software can always exist)

Long sentence! Sorry if this all seems blindingly obvious to all of you, but I've been reading and trying to make sense of the whole thing because since I started using Ubuntu I feel like part of something really incredible (as someone with a strong interest in computing) and want to see it last forever, so that one day, hopefully soon, I will be able to contribute something of my own.

---

### Post by 23meg on 2007-04-01
[QUOTE=Ozor Mox]So not only does Ubuntu have backup funds and support to keep it going and, from reading that wiki, a very committed founder, but the nature of the GPL license is that software licensed under it cannot be "de-licensed" so to speak, so the Linux kernel, GNU tools, X, KDE/GNOME, and all the other many applications that are in distributions like Ubuntu will always have their source code freely available and can be developed by anyone? (i.e. a free-as-in-freedom operating system and software can always exist)[/QUOTE]

Exactly.

[QUOTE=Ozor Mox]Long sentence! Sorry if this all seems blindingly obvious to all of you, but I've been reading and trying to make sense of the whole thing because since I started using Ubuntu I feel like part of something really incredible (as someone with a strong interest in computing) and want to see it last forever, so that one day, hopefully soon, I will be able to contribute something of my own.[/QUOTE]

You don't have to wait at all to contribute; even as a non-technical user you can report and triage bugs, help other users, test development releases, write documentation, so on.

---

### Post by Ozor Mox on 2007-04-01
I have actually already posted here to share my experiences with getting Ubuntu to work with some of my more annoying hardware! The other things I will remember, although I have done some coding and could possibly get involved with the technical things later.

Do you know what other licenses are used for Ubuntu packages and whether they are "viral" (in a good way!) in the same way that the GPL is?

---

### Post by 23meg on 2007-04-01
X, for example, has its own license, known as the X license or more commonly (and mistakenly) the MIT license. It's less restrictive than the GPL, and isn't viral. It allows code reuse without disclosing source, rebranding and sublicensing. It's also used by many other pieces of software.

[http://en.wikipedia.org/wiki/X11_License](http://en.wikipedia.org/wiki/X11_License)

---

### Post by Brunellus on 2007-04-02
I wonder what would happen if a viable GPL replacement to X were to come about.

---

