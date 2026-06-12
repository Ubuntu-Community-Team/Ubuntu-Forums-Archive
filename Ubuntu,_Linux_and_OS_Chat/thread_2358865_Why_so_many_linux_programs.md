---
title: "Why so many linux programs"
date: 2017-04-18
forum: Ubuntu, Linux and OS Chat
---

### Post by Mike E Tomlinson on 2017-04-18
If everyone got together and put their efforts into one linux operating system. All the bugs would be worked out and there would be (finally a stable operating system that would kill the rest of the big boys. Plus it would be free of bloat ware spyware etc.Too bad people can't work together because everyone has a different idea what would be best. 
Just thought I would throw this out there :0)

---

### Post by Bucky Ball on 2017-04-18
If you flip your question around and ask 'Why isn't there only one Linux OS?' you might find some answers. ;)

You ask a simple question with myriad answers.

---

### Post by Habitual on 2017-04-18
[Standards]("https://xkcd.com/927/")

---

### Post by Bucky Ball on 2017-04-18
> **Habitual said:**
> [Standards]("https://xkcd.com/927/")

Exactly. :)

---

### Post by bcbuch on 2017-04-18
Part of what makes Linux attractive IMHO is the fact it for the most part is a modular system. A person with the know how can install most distributions and then remove unwanted packaging and install what better suits their personal needs or taste. I've been using Linux for over 2 decades and these days I don't see stability issues as a problem especially in LTS releases. Stability issues that arrise tend to happen on systems where the user tends to use a more bleeding edge approach to things, or they simply never fully set up the system after install, updates, drivers, ect for their particular hardware configuration.

As far as bloat in a system goes here's something to keep in mind. Most major distributions release major OS upgrades on a scheduled cycle. The distribution will be effected by the provider's particular view of free software usage vs using non free. Most major distributers have a few official versions that they support which are centered around a particular desktop environment. With that in mind they will generally default to that environments basic package set or tweak it a bit. The thing they have to keep in mind is not everyone is not a power user. The base release needs to be ralitavly easy to install and for the most part, as well as have enough included software far a new user to be able to install it, and then have a function system they can use as a daily driver. Beyond that distribution developers expect the end user to either have the knowledge, or do the research to figure out how to customize the system to their particular liking. That includes the ability of remove unwanted default applications or bloat.

I have to say I'm a little lost on the malware issue. If an individual comes from a Windows environment to Linux the initial observation is the lack of malware either from an OEM,  Microsoft, or internet usage. Most malware in the Linux ecosystem can easily be handled by adding a browser extension or changing a browser setting. That also applies to propietary operating systems as well. Proprietary systems for the most part will also require third party malware and virus detection and removal software running which will tax the system system resources in addition to the basic OS software running on the system as well as open programs.

On the Linux side of things I would like to see the number of distributions decreased. I feel like the Linux ecosystem is cluttered with with all the different distributions. I think this clutter has happened because new users do not want to invest the time actually learning how to use Linux. They want a point and click out of the box experience. That has expanded into specialty distributions where the end user doesn't want to take the time to set a system up for a specific task. In both cases the end user is relying on a distribution developer to do the work for them. This has left the Linux ecosystem littered with redundant code, and distribution trying to reinvent the wheel. It has gotten to the point that one distribution builds off the top of another. Then another builds of the top of that one. So now you have a base distribution, the second that that's now become a base, and the third that is out there trying to reinvent the wheel because they think they can do a better job than the original coders and distributors did. 

There you go. My long winded 2 cents worth.

---

### Post by ian-weisser on 2017-04-18
> **Mike E Tomlinson said:**
> If everyone got together and put their efforts into one linux operating system. All the bugs would be worked out and there would be (finally a stable operating system that would kill the rest of the big boys.

Ah, you have not read about the [cultural differences between Linux and Windows]("http://linux.oneandoneis2.org/LNW.htm"). You are not the first to suggest this. You are not the first *this week* to suggest it.



> **Mike E Tomlinson said:**
> Too bad people can't work together because everyone has a different idea what would be best.

Seems like you answered your own question there.


Use Linux to create what you want to create.
Pitch in with the projects that are heading in the right direction (to you).
Don't bother complaining about projects heading in the wrong direction. It's rude, and nobody cares anyway.
If you want projects to cooperate, then be the friendly bridge-builder between them. That's a valuable contribution.

---

### Post by QIII on 2017-04-18
Compete with the big boys?

Linux has already won.  Linux is running on more devices than anything from Microsoft -- by at least an order of magnitude.

---

### Post by sp40140 on 2017-04-18
The main problem with linux ecosystem is lack of professional developers. Developers who make money off the OS by selling the softwares. MicroSoft knows this. They don't and never have cared for users. They have cared for developers. That's the way you get your system stable. And here by "stable" I mean your version of stable. 
Linux as a kernel is the best software out there. Linux does great in servers because the vendors make a lot of money off it and so they invest more. Look at the VMware, It just works. Because they make money off it on linux platform.
The day developers start making money from applications built on top of linux distro is the day you will start seeing huge improvements.
Apple wasn't this good until they got their app store going. Same with Android.
There is a problem with linux community in that they think linux is free and by extension everything should be free on it. It is true but there is effort put into it by someone and it's worth money. You don't pay for Apple OS but you pay for MacOS apps through nose.
This is one of the reasons that I see lots of apps get deprecated / don't get supported or add new features. There is nothing in it for devs. And if something breaks, they actually get beaten up for it. Ex, Tweak, pysdm and on and on.
I mean this for the softwares on top of os. 
Once this is sorted out, linux distros will get consolidated to a degree.

Stability you question comes from the application on top of linux and not dirctly from linux.

---

### Post by 1clue on 2017-04-18
> **Habitual said:**
> [Standards]("https://xkcd.com/927/")

+1

---

### Post by 1clue on 2017-04-18
The Linux operating system is the kernel. Everything else is a service or application built on top of that operating system.

The kernel is compiled for some specific range of hardware, but CAN BE compiled for a huge variety of hardware. Linux runs on more hardware than Windows does. Not just Intel, but anything from something you can wear on your wrist to something in a microwave oven to something with literally millions of cores. Go to [http://top500.org](http://top500.org) and you'll see a massive representation of Linux in the world's fastest computers.

As you can probably imagine, supporting all those varieties of hardware in all the complex scenarios people want to use that hardware means that testing is problematic. Some combinations of kernel options do not produce a working kernel.

That's just the kernel, but that's not what you were talking about.

The thing is, even for "traditional" Linux users there is a wild variation in preference, even in what we call "pc hardware." A distribution like Ubuntu has made a lot of choices for you:
[LIST=1]
[*]What hardware group? (mainframe, mini, x86, ppc, arm, ...)
[*]UEFI or legacy boot?
[*]What boot loader?
[*]What kernel options?
[*]What init system?
[*]What logger?
[/LIST]

We haven't even approached authentication or security yet.

Most distributions create a (can't remember the word.  Manifesto is not quite right) describing the priorities of the distro. That document generally states things like what sort of hardware they build on, possibly a desktop (kde vs gnome vs ??) and probably their stance on non-free software. It says whether the distro is maintained by a commercial entity (Ubuntu is maintained by for-profit company Canonical) or by the community (Slackware, Gentoo, Arch) and what sort of user base they aim at.

The distro will base its software selection decisions on their statements in the manifesto. Some systems are intended for use as a firewall and/or UTM, some are aimed at cluster computing, etc.  Special purpose distros like firewalls or clusters almost certainly won't have any sort of GUI on them, or if they do it will be web-based.


Now, as to what constitutes "stable."

Some people don't care much about crashes as long as they get the latest features. Maybe they're developing software that they intend to be used with the current bleeding edge, and hope that their software will become stable concurrently with what they're working with.  Some just want bleeding edge to say they have it.

Some people want rock solid stability for one or two apps, and don't care much about the rest.

Some people want a rock solid environment for their business, so they want a good office suite with compatibility with other office software.

Some people want a rock solid server environment, without new features except security/stability enhancements.

Some people want stability because if the system crashes their money is all gone.

Some people want stability because if the system crashes the patient dies.

Some people want stability because if the system crashes the plane crashes too, and 400 people die.

I've only scratched the surface. You might investigate Gentoo linux [http://www.gentoo.org/](http://www.gentoo.org/) . It's my other favorite distro. It lets you see how a regular distro might be made, and gives you insight into the choices made by distros like Ubuntu.

---

### Post by montag dp on 2017-04-19
> **Mike E Tomlinson said:**
> If everyone got together and put their efforts into one linux operating system. All the bugs would be worked out and there would be (finally a stable operating system that would kill the rest of the big boys. No it wouldn't. It would just be another Windows / OS X. Freedom of choice is the major benefit of Linux and open source software in general. If you don't want that, you should use an OS that doesn't offer it, like Windows or OS X.

> **Mike E Tomlinson said:**
> Too bad people can't work together because everyone has a different idea what would be best. 
Just thought I would throw this out there :0)People can and do work together, but why should everyone have the same idea of what is best?

---

### Post by poorguy on 2017-04-19
Linux is about choice and having several different choices allows for different options.

If one Linux distro doesn't work well on the computer it is installed on than having the options of several Linux distros a user will most likely find a Linux distro best suited for the computer it will be used on.

To many different pieces of hardware etc for any OS Linux, Windows or Apple for developers to design a bug free perfect OS.

---

### Post by 1clue on 2017-04-19
There is no such thing as one size fits all.

Imagine one size fits all applied to cars.  Every vehicle on the roads are exactly the same thing, just different paint and maybe different upholstery.

If one size would really fit all, then we'd all likely be running Windows.

---

### Post by Habitual on 2017-04-19
> **1clue said:**
> There is no such thing as one size fits all.

Imagine one size fits all applied to cars.  Every vehicle on the roads are exactly the same thing, just different paint and maybe different upholstery.

If one size would really fit all, then we'd all likely be running Windows.
If we all installed "Non-Compliance Linux" (should one exist) what would we have?

---

### Post by 6975 on 2017-04-19
Is this really "Too many linux programs" thread?
This sounds like "Too many linux distro" thread to me. :\

---

### Post by 1clue on 2017-04-20
> **Habitual said:**
> If we all installed "Non-Compliance Linux" (should one exist) what would we have?

That's exactly the opposite of the right approach.

A lot of mainstream computer users, both expert and not, think that Linux users are using Linux as some sort of protest. That's BS.

I manage a lot of Linux boxes. By far, I use Ubuntu Server more than anything else. They have a nice small image that works well on bare hardware or VMs, it has good support and works well with non-free software. All these are important to my most frequent scenario.

The thing is, every image I need to build I go through the requirements and choose my distro based on those requirements. Usually it's Ubuntu Server, sometimes it's CentOS or something else. If nothing I know to be appropriately stable is a good fit I cook something up with Gentoo.

Nowhere in this logic does "non-compliance" ever enter the picture. Use what you use because it's what YOU WANT, not because it will offend somebody else. "Somebody else" gives not one hoot what you use. Don't punish yourself.

---

### Post by Habitual on 2017-04-20
> **1clue said:**
> That's exactly the opposite of the right approach.
Irony is often rhetorical.

---

### Post by Mike E Tomlinson on 2017-12-26
Thanks everyone for your input. I learned a lot. Sad to say I'm never going to be to savvy with Linux. I started too late in life. I'm 64 and I can barely type. I do copy paste to put commands in terminal. Ubuntu to me is a way to keep my privacy. I donate when I can to ubuntu.

---

### Post by fyfe54 on 2017-12-26
> **Mike E Tomlinson said:**
> Thanks everyone for your input. I learned a lot. Sad to say I'm never going to be to savvy with Linux. I started too late in life. I'm 64 and I can barely type. I do copy paste to put commands in terminal. Ubuntu to me is a way to keep my privacy. I donate when I can to ubuntu.

Stick with it, it will be worth it.  I'm 62 and made the transition to Ubuntu some years ago and never looked back.  I must say that just stopping by the forums and reading whatever post caught my eye was enlightening.  The people here are patient, knowledgeable (in spades) and willing to help.

---

### Post by poorguy on 2017-12-26
> **Mike E Tomlinson said:**
> Thanks everyone for your input. I learned a lot. Sad to say I'm never going to be to savvy with Linux. I started too late in life. I'm 64 and I can barely type. I do copy paste to put commands in terminal. Ubuntu to me is a way to keep my privacy. I donate when I can to ubuntu.
I'm 65 years old and started using Linux in 2014 prior to EOL Windows XP.

It's never to late to start learning anything and ***copy and paste*** is the best way to enter commands without mistakes when using the ***command terminal***.

I never have learned how to type and don't care to as I can pick and push as well as some people who I know that can type.

As mentioned earlier stick with it and ask questions and you'll learn more than you realize when needed.

These sites have been a great  source of help for my Linux adventures.

[https://linuxjourney.com/](https://linuxjourney.com/)

[https://sites.google.com/site/easylinuxtipsproject/](https://sites.google.com/site/easylinuxtipsproject/)

---

### Post by 1clue on 2017-12-26
> **Habitual said:**
> If we all installed "Non-Compliance Linux" (should one exist) what would we have?

Gentoo. Or LFS.

---

### Post by spyder77 on 2018-02-07
> **fyfe54 said:**
> Stick with it, it will be worth it.  I'm 62 and made the transition to Ubuntu some years ago and never looked back.  I must say that just stopping by the forums and reading whatever post caught my eye was enlightening.  The people here are patient, knowledgeable (in spades) and willing to help.

In my 40s and in the transition process. It helps (at least mentally) that after my first Commodore, it was MS-DOS on PCs for several years and I liked the 'feeling' it gave of being more connected to the hardware than you get through a GUI. I'm taking the "far more to explore" attitude with the much more vast Linux terminal, while softening the transition a bit with one system still running Windows 10 and another that has only Ubuntu on it. 

I like the choices and I'm running a couple other distros on the Win 10 machine as virtual boxes, though my preference from my sampling is Ubuntu (and why my dedicated Linux system is Ubuntu). Linux really is a journey, and I'm finding it to be a rewarding one. I just found this forum - first post.

-Brian

---

