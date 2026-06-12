---
title: "My rant about Linux distributions"
date: 2011-07-08
forum: The Cafe
---

### Post by Cgenet on 2011-07-08
Since the beginning of using Linux, I have had a frustration with distro's.
Not the concept of distro's, but the fact that every distro to my knowledge, modifies software they put into their distro, braking compatibility.

I am running Ubuntu 10.04 LTS.
Recently, I wanted to check out Firefox 5, so I downloaded the source and went to compile it. I couldn't compile it because zlib was outdated on my system, so I went to the zlib website and downloaded the latest tarball, compiled it... and then Ubuntu broke.
It seems that the zlib in Ubuntu 10.04 LTS is a version modified by Canonical, so future upgrades of zlib is not be possible for me, as Ubuntu does not have the latest zlib in their repository. So much for "freedom".

I think Linux distributors should stop modifying everyones software, and just leave it be with the official version. It does nothing but create a limitation!

Some say they modifications are done to 'patch/work around/regression' software to get it working. Well!... If thats what it takes to get the software working then that software is junk and shouldn't be used... that way the developer might get the hint to check out the meaning of quality control instead of releasing something that resembles a beta version.

... and software should not suffer obvious regression on an update. If it does then it means the software was not ready for release.
I don't see regression with software made for Microsoft Windows. Why can't Linux developers be the same in this sense?!


Another thing that pisses me off:
When I goto some developers sites, under O/S I see "Windows", "Mac",... then I see "Ubuntu" "Debian" "Gentoo" "Fedora", etc, etc, etc...

This furiates me because there is no such thing as an Ubuntu or 'Fedora' operating system. It is just the user space tools and applications which makes a distro. At the end of the day, its called *Linux*!
All this does is create huge amount of confusion/inconsistancy.

... and software shipping in package systems only is ***** wrong - software will only work on a specific distro. Lame!
I think developers should dump package management systems such .deb and .rpm, and distribute software as a .run or .sh file that self-installs.
I.E AfterLogic's MailSuite Pro can only be installed via RPM and DEB, so, what happens to the others who don't use those package systems? It means they miss out.

Without a package management system, a way to keep the system would need to be introduced. A universal updating application can be made to address this.

I have bee using Linux now for a year using the Ubuntu distro and enjoyed most of it, and now I can't wait to get away from it and build my own Linux system from scratch.

---

### Post by mikewhatever on 2011-07-08
> **Cgenet said:**
> 

...
I have bee using Linux now for a year using the Ubuntu distro and enjoyed most of it, and now I can't wait to get away from it and build my own Linux system from scratch.

Well, good luck, and let us know when you are done.

---

### Post by snowpine on 2011-07-08
In the time it took you to type that, you could have used the Search feature:

[http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)

---

### Post by Cgenet on 2011-07-08
Double post.

---

### Post by lincoln32 on 2011-07-09
bleeding edge, yes modify to make work on your distribution, yes that is the point of open source. Some just want a disto to work others want the latest (but not always ready for prime time). I am in the middle working very happily on 11.04 with firefox 5 with only a few bugs to deal with. My servers are all 10.04 and only use stable packages with seldom a bug or issue. I am sticking generally to one distro so I can understand it well, but do use others from time to time. I think most users are in the just want it to work out of the box and others with the ability and time can build what they want. but I am happy in the middle.

---

### Post by Dustin2128 on 2011-07-09
Just use another distribution- gentoo or arch seem to be what you're looking for. And if someone provides you with deb or rpm packages for download, be thankful they provided linux packages at all- then promptly convert them to tarballs, and install. Also, ubuntu, fedora, etc. are in fact operating systems. Linux is not an operating system, it is a kernel. Of course, ubuntu, fedora, slackware etc. could be classified as linux distros instead, which they usually are.
However, your extreme rudeness to snowpine makes me think you're likely a troll. Or 12.

Keep in mind though, debs and rpms can easily be converted to other package formats. If we all use shell scripts or executables as you suggest, we'll have no dependency resolution- an incredibly important feature.

---

### Post by OldBoy44 on 2011-07-09
> **dustin2128 said:**
> however, your extreme rudeness to snowpine makes me think you're likely a troll. Or 12.

+1

---

### Post by wolfen69 on 2011-07-09
All of the OP's complaints are actually strengths. That's the whole point of open source software. If you do not like this concept, windows and mac await you.

---

### Post by wojox on 2011-07-09
[[IMG]http://danlynch.org/blog/wp-content/uploads/2009/03/arch-linux-logo.png[/IMG]]("http://www.archlinux.org/")

---

### Post by Khakilang on 2011-07-09
Rudeness aside. I think the OP has a point. People should be able to download a software and install it without breaking any dependencies. Like I did when I started using Linux. Should be straight forward kind a thing. Since most of the software in the software centre is good enough for me but other user may think otherwise.

---

### Post by cariboo on 2011-07-09
With the number of ppa's available, there shouldn't be a need to download the source, and compile it yourself.

---

### Post by Bandit on 2011-07-09
> **Cgenet said:**
> I have bee using Linux now for a year using the Ubuntu distro and enjoyed most of it, and now I can't wait to get away from it and build my own Linux system from scratch.

Best of luck to ya. :popcorn:

---

### Post by Bandit on 2011-07-09
> **Khakilang said:**
> Rudeness aside. I think the OP has a point. People should be able to download a software and install it without breaking any dependencies. Like I did when I started using Linux. Should be straight forward kind a thing. Since most of the software in the software centre is good enough for me but other user may think otherwise.

I haven't had any issues with Ubuntu breaking dependencies. I have had it not want to install packages due to potential dependency conflicts or lack of dependency package. But I am sure someone has. Though those can be corrected with the proper use of dpkg and source files in case that does arise. But if someone wants to talk about dep errors, try SuSE. I used it for years and now cant understand why I bothered. Its got more dependency issues then a crack addict.

---

### Post by wojox on 2011-07-09
> **cariboo907 said:**
> With the number of ppa's available, there shouldn't be a need to download the source, and compile it yourself.

Good point. Another thing I love about Ubuntu is it's meta-packages. I install Ubuntu, install my meta-packages and next thing you know, I'm writing scripts, surfing the web, and listening to music. It takes me like thirty minutes.

---

### Post by wolfen69 on 2011-07-09
> **wojox said:**
> Good point. Another thing I love about Ubuntu is it's meta-packages. I install Ubuntu, install my meta-packages and next thing you know, I'm writing scripts, surfing the web, and listening to music. It takes me like thirty minutes.

But an "upgrade" is *so* much better. :rolleyes: Waiting hours only to find out stuff is broken and will require more hours to fix. Much better. No, don't keep all personal stuff on separate partitions/drives and backup a couple config files. Roll the dice and upgrade! Much better idea. :???:

---

### Post by CraigPaleo on 2011-07-09
> **snowpine said:**
> In the time it took you to type that, you could have used the Search feature:

[http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)

I added the ppa and have Firefox 5 running on 10.04 just fine.

---

### Post by grahammechanical on 2011-07-09
I wait with eager expectation for this OP to develop all the tools and utilities that will put right all those wrongs. Is this not what freedom means?

In the beginning a certain person did not like the fact that the editor that he was using to write programs did not work the way he wanted it to work and he was not allowed to modify it, so he wrote his own editor program and released the source code so others could use the editor and modify it as they wish but on condition that any modifications are released so that others could use them.

And look where we are now! We have the freedom to complain and the freedom to enslave others by demanding that they do this and that to please us. How easy we forget that we are not paying anyone a salary.

That's right. We also have the freedom to rant. Even me.

Regards.

---

### Post by haqking on 2011-07-09
at the risk of getting flamed or an infraction.

I wish people would stop using Linux if they cant use linux.

Or use it and stop moaning or ranting about it.

There are plenty of other platforms to choose from where you you can just click and have no idea what is happening or why and have no control over it if you could.

With that ease of use comes a plethora of malware,virii and such like to choose from which will break more than your dependencies.

Linux works...if it dont its cause you did something wrong ! ;-)

---

### Post by Bachstelze on 2011-07-09
> **Cgenet said:**
> 
It seems that the zlib in Ubuntu 10.04 LTS is a version modified by Canonical,

It is not, or at least only marginally so, and certainly not enough as to break compatibility.  We tried to explain to you what was going on several times, but you wouldn't listen, so I'm going to go with everyone and call you a troll (you called me a noob so I guess that makes us even).  You seem only interested in stirring trouble, not in constructive discussion.  So good riddance, you won't be missed.

---

### Post by LowSky on 2011-07-09
Before PPA's = Valid point. After = moot

---

