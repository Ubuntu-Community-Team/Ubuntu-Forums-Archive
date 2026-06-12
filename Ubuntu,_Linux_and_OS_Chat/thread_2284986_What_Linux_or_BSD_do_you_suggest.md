---
title: "What Linux or BSD do you suggest?"
date: 2015-07-02
forum: Ubuntu, Linux and OS Chat
---

### Post by Ashley_Scopes on 2015-07-02
Hi, very sorry if this is in the wrong place.

I am going to be starting a four year masters degree in Computing Science in september. I am going to be studying Web and Software development, as well as networking, etc.

I currently run Windows, and I am fluent in C#, Java and I am teaching myself ASP.NET C# razor currently.

For about a year now, I have been invextigsting Unix operating systems to use as a dual boot with my Windows setup, I prefer the terminal and free apps that come with it.

Unfirtunately I still cannot seem to find the right unix for me. Ubuntu and Fedora based are the only ones that seem to work out of the box with my hardware. I dont want something that has to have loads of configuting until I get used to how the system works. Fedora has been my favourite but lack of dvd and mp3 support, propietry drivers, etc is difficult. Mint is not appealing to me as I dislike Mate, Cinnamon and Xfce. Unity is appealing as is gnome and while KDE is very beautiful, it is very bloated and buggy (or it was a few months back when i tried kubuntu).

I want something that is pretty to use like Elementary OS and allows me quick access to what I want to do, whether it is coding, browsing the net or writing documents or developing photography with DarkTable, however it needs to have third party codec and driver support out of thr box like Mint. I like the look of BSDs but I gathee they are complicated and less supportive in terms of drivers which is not good for me as this is my main PC. I do not want to touch arch, as it is too much work. Unity does not seem very nice for customisability so, excluding openbox, awesome, etc Gnome seems to be the best for me, unless you can think of anything else. LXDE is not pretty for me ;)

My hardware is
- Toshiba Satellite p850-30v
- i3 2350m
- 8gb ram
- Intel PROSET wireless (cant say which model as I am away from home at the moment)
- 600GB HDD
- Nvidia GT630M (with a weird config also using the i3 graphics that I cant disable in BIOS)

I have been looking at either a flavour of Ubuntu, Fedora or something like OpenSuse (dont know much about it), or maybe Elementary OS but it seems a bit awkward if you want to do more than just run chrome or openoffice or whatever.

without the bias from the fact this is an ubuntu forum, what do you suggest and why? I am open to any ideas.

Thanks for helping a Noob like me :) to be honest I don't think I know exactly what I want or need, so if you think something like Ubuntu MATE or Fedora would be best for me, by all means say. I am basically saying "hey, I have little unix experience but I am willing to learn; I am studying Computing \#Science so \i need something good for programming, I have picky hardware requirements and I want something that can atleast be made to look modern. I would like access to mp3 codecs, dvd codecs, propietry softwarw like flash, etc out of the box."

Thanks a lot!

(Bonus question)...if I wanted to develop software for any linux in general with a UI if preferable, what language and IDE do you suggest? Bare in mind you are talking to a Windows fanboy who ia only used to VB or C# in Visual Studio, and doddling with PHP in Atom or Sublime Text.


Thanks!

Ash

---

### Post by PaulW2U on 2015-07-02
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by grahammechanical on 2015-07-02
Did you say Visual Studio?

Earlier on in the year a Ubuntu developer came up with the idea of making it easier for developers to use Ubuntu as a developer platform. He started work on something called the Ubuntu Developer Tools Centre. The name has now been changed to Ubuntu Make.

Install Ubuntu Make on Ubuntu and then a few commands later and we will have certain IDEs installed in Ubuntu and as each IDE is improved we get the latest version.

The project started with Eclipse and Android Studio and then the other month when Microsoft announced that it was making Visual Studio code available the developer of Ubuntu Make added support for Visual Studio for Linux to Ubuntu Make

[http://blog.didrocks.fr/](http://blog.didrocks.fr/)

[https://wiki.ubuntu.com/ubuntu-make](https://wiki.ubuntu.com/ubuntu-make)

Ubuntu Make has support for 15 development platforms. Eclipse; Android ADT; Android NDK; Intellij IDEA; IDEA ultimate edition; Firefox Developer Edition; Go; Dart;  Pycharm; Pycharm education edition; Pycharm professional edition; RubyMine; WebStorm; PhpStorm.

That lot totals 14. I have no idea what the 15th platform would be. Apart from all that there is the Ubuntu SDK.

[https://developer.ubuntu.com/en/start/ubuntu-sdk/](https://developer.ubuntu.com/en/start/ubuntu-sdk/)

And the Ubuntu Developer portal with its guides and tutorials.

[https://developer.ubuntu.com/en/](https://developer.ubuntu.com/en/)

And then there is Snappy Ubuntu core for the Internet of Things (IoT) and the cloud.

[https://developer.ubuntu.com/en/snappy/](https://developer.ubuntu.com/en/snappy/)

[http://www.theorangenotebook.com/2015/07/snappy-open-house.html](http://www.theorangenotebook.com/2015/07/snappy-open-house.html)

You get a lot of help when you use Ubuntu as the development platform. But if you want you can go somewhere else.

Regards.

---

### Post by kc1di on 2015-07-03
Hi Ashley_Scopes  and Welcome to the world of Linux :) 

I would suggest Ubuntu for the following reasons -- Multimedia codecs are easy to add. There is a ton of software out there to do what you want either in the repositories or via PPA's.  Also there are many many people willing to help and lots written on the web about and for Ubuntu. So you should never be far from the help you need if you get stuck.  

Fedora is a fine Distro and cutting edge, but it's more difficult , IMHO to get help on that distro if needed and install codec and any other non-free software can be a hassle. 
The BSD's are fine if your hardware works with them.  But I find every time I have tried mine does not.  

I'd stick to Ubuntu or one of it's derivatives.  It seem you like Unity. It's also available with gnome3 should you like that one.  so you may want to give [ubuntu-gnome]("https://ubuntugnome.org/") a try too. 
Happy hunting and hope to see you around the Ubuntu forums.
P.S. I prefer Mate Myself :)

---

### Post by buzzingrobot on 2015-07-03
At the terminal (Bash) level, all Linux distributions are much the same. Broad variations exist in the packaging and dependency resolution tools used, init systems (how services, etc., are initially loaded on bootup) vary, etc. Learning about those is part of the process of learning Linux in depth.

Distributions that try to focus on user comfort issues -- like Ubuntu, Elementary, Mint, etc. -- will probably make for an easier passage into Linux.  They should allow you to start learning the basics without dragging in extraneous issues.

Once you get some experience, you'll be in a better position to choose another distribution.  In general, I'd suggest sticking with distros that have been around for some time and are sponsored/supported by a strong organization or corporation. Also, many distributions, including Mint and Elementary, are based on Ubuntu, which means, among other things, that the Ubuntu package repositories are available for use.

I also use and like Fedora.  It's influenced by its strong commitment to use only what it considers free software. One reason is ideological, and the other is that it is sponsored by Red Hat, which, as a U.S. corporation that indemnifies its enterprise customers, needs to avoid any potential legal threats over unauthorized distribution of licensed software. (Fedora is something of a testbed for Red Hat, so many components in Fedora eventually make their way into a new Red Hat release.)

That's why Fedora does not distribute DVD players, codecs, Flash, proprietary video drivers, etc.  Those are available, however, from other sources. The rpmfusion.org site is the most useful and reliable. A number of post-install scripts are out there that make it easier and quicker to install this stuff. The links across the top of this forum ([http://fedoraforum.org/](http://fedoraforum.org/)) are a good place to start exploring Fedora. The  site Fedora wants you to use to get iso's and such is: [https://getfedora.org/](https://getfedora.org/).  Links for docs, tutorials, etc., are at the bottom of that page.

It's my impression that the Fedora user base leans more to the engineer/tech/developer side, while Ubuntu explicitly targets new non-technical users. Fedora moves faster than Ubuntu, new relases are scheduled at 6-month intervals, and the support lifetime of any release is about 13 months (no updates after that and the repos go away). Individual package updates come down often and in high numbers.  it isn't unusual to, say, install a new release a few days after it goes public and find a few hundred updates on offer immediately after the install completes.

Finally, on drivers:  If an open source driver is available, it will almost certainly be installed and used automatically. Little or no need exists in Linux to go to individual hardware vendor sites looking for driver. 

A potential exception to this are the proprietary closed source video drivers released by Nvidia and AMD. Because Linux kernel developers don't have access to the source code for these drivers, new kernel release and/or new driver releases sometimes break systems.  Commonly,  after the new kernel or new driver is installed, users reboot into a broken display.  The solution is to try to roll back to the previous driver.  Ubuntu, and the distros based on it, include a GUI tool to make installation and updating of these drivers easier, and Canonical does test drivers for compatibility. However, many, many variations of video cards exist, often with changes made by a vendor to the reference model from Nvidia/AMD.

My advice, then, is that if you find Intel video to be adequate, to stay with it. At least, try it first. Intel open sources its driver, cooperates with the kernel developers, and its driver is packaged with the kernel and "just works". (If your BIOS does not offer a way to disable the Nvidia and use only the Intel, it *may* be an Optimus machine, meaning it uses an Nvidia scheme to use the Intel by default and automagically switch to the Nvidia when demand increases. Optimus support is available in Linux, but you might research it a bit.  

*Boot and run a distribution in Live Mode to see how it handles your hardware before doing an actual install.*

---

### Post by monkeybrain20122 on 2015-07-03
> **buzzingrobot said:**
> 


It's my impression that the Fedora user base leans more to the engineer/tech/developer side, while Ubuntu explicitly targets new non-technical users. 



Actually, everything I can do on Fedora I can do on Ubuntu in terms of engineering/tech/developing stuffs but not the other way around. For one thing there are a lot more technical software in Ubuntu and compiling for most is easier because developers often test with Debian/Ubuntu (I have ran into situations where some key libraries are missing in Fedora's repo for compiling but never in Ubuntu, it is also a lot easier to have multiple versions of compilers in Ubuntu). Ubuntu is easy for non tech use but I don't want to give the impression that it is only good for non tech users. 

In general I think Ubuntu is as good as any Linux for everything but it is more reliable and has better hardware compatibility than most. If you want to actually do things with the computer instead constantly trouble shooting it then it is the best choice.

---

### Post by buzzingrobot on 2015-07-03
> **monkeybrain20122 said:**
> Actually, everything I can do on Fedora I can do on Ubuntu in terms of engineering/tech/developing stuffs but not the other way around. For one thing there are a lot more technical software in Ubuntu and compiling for most is easier because developers often test with Debian/Ubuntu (I have ran into situations where some key libraries are missing in Fedora's repo for compiling but never in Ubuntu, it is also a lot easier to have multiple versions of compilers in Ubuntu). Ubuntu is easy for non tech use but I don't want to give the impression that it is only good for non tech users. 

In general I think Ubuntu is as good as any Linux for everything but it is more reliable and has better hardware compatibility than most. If you want to actually do things with the computer instead constantly trouble shooting it then it is the best choice.

Agreed. I was giving my impression of the users bases, though, not the capabilities of a distribution.  In that regard, all are essentially equivalent since if something is not packaged for a distribution that should not hamper a developer with the skills to work with its source.

---

