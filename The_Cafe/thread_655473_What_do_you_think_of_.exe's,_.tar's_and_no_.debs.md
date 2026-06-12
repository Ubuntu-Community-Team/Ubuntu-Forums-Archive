---
title: "What do you think of .exe's, .tar's and no .debs?"
date: 2008-01-01
forum: The Cafe
---

### Post by Vadi on 2008-01-01
This issue has been annoying at me recently. I'm bumping into many projects that provide Windows installers, but not Linux ones - just a .tar.gz file, here you go, read the INSTALL file.

Really, it feels like a slap in the face. Why do windows users have it easier and we don't?

And while most .tar.gz's are relatively easy to install (./configure, make, sudo make install), they're a pain to remove - you have to keep the original files, and remember where you put them when you want to uninstall.

---

### Post by insane_alien on 2008-01-01
well, not every distro supports .debs or .rpms.

and while a unified package manger would be great(i'm a fan of pacman myself, it could be expanded) there are too many different ways of doing it on linux for anyone to decide. compiling from source on the other hand is a surefire way of giving it cross distro/platform/os compatability.

---

### Post by helliewm on 2008-01-01
I tend to favour debian distro's so just use deb files.

Helen

---

### Post by ~LoKe on 2008-01-01
We have debs and official repository packages.  Anything that comes in source has probably been compiled and had a deb created (with checkinstall).  Also, source is often used for packages in development.

---

### Post by LaRoza on 2008-01-01
Well, not every project supports every version of Windows either. Do you expect them to provide programs for Windows 95 and up? 

They support the latest (usually).

In Linux, .deb and .rpm won't work in all, however, a tarball is the best way to spread it. Almost any Linux user can use it then.

See the Development and Programming forum for information on Packaging programs in the .deb format. That is how .debs come around really.

---

### Post by Steveway on 2008-01-01
Instead of using sudo make install, you can use sudo checkinstall (Providing you installed checkinstall) it will create a .deb. You can then easily remove it later.

---

### Post by logos34 on 2008-01-01
> **Vadi said:**
> This issue has been annoying at me recently. I'm bumping into many projects that provide Windows installers, but not Linux ones - just a .tar.gz file, here you go, read the INSTALL file.

Really, it feels like a slap in the face. Why do windows users have it easier and we don't?


I've wondered along similar lines.  Why are there relatively so few .debs offered?   Not even .rpms are available for every tar.gz (and more linux distros use .rpm pkg mgr than any other).  But ubuntu is the most popular linux distro and has been for quite some time--so why so few debs?  Yes, there's alien and auto-apt+checkinstall.  But if a software developer wants to spread his application as far and wide it's in his or her interest to make it as easy to install as possible.

---

### Post by ~LoKe on 2008-01-01
> **logos34 said:**
> I've wondered along similar lines.  Why are there relatively so few .debs offered?   Not even .rpms are available for every tar.gz (and more linux distros use .rpm pkg mgr than any other).  But ubuntu is the most popular linux distro and has been for quite some time--so why so few debs?  Yes, there's alien and auto-apt+checkinstall.  But if a software developer wants to spread his application as far and wide it's in his or her interest to make it as easy to install as possible.

There are debs for almost every package.  You just have to look for them.

---

### Post by Lord DarkPat on 2008-01-01
> Instead of using sudo make install, you can use sudo checkinstall (Providing you installed checkinstall) it will create a .deb. You can then easily remove it later.
Thank you, thank you thank YOU!!

---

### Post by LaRoza on 2008-01-01
> **logos34 said:**
> I've wondered along similar lines.  Why are there relatively so few .debs offered?   Not even .rpms are available for every tar.gz (and more linux distros use .rpm pkg mgr than any other).  But ubuntu is the most popular linux distro and has been for quite some time--so why so few debs?  Yes, there's alien and auto-apt+checkinstall.  But if a software developer wants to spread his application as far and wide it's in his or her interest to make it as easy to install as possible.

Make one and release it.

That is how they spread!

---

### Post by banjobacon on 2008-01-01
Aren't random installers downloaded from third party websites a secuirty risk? For this reason, I feel this should be discouraged, in favor of trusted repositories.

---

### Post by ~LoKe on 2008-01-01
> **banjobacon said:**
> Aren't random installers downloaded from third party websites a secuirty risk? For this reason, I feel this should be discouraged, in favor of trusted repositories.

A .deb or source could be tainted just the same.

---

### Post by ryanVickers on 2008-01-01
> **Vadi said:**
> This issue has been annoying at me recently. I'm bumping into many projects that provide Windows installers, but not Linux ones - just a .tar.gz file, here you go, read the INSTALL file.

Really, it feels like a slap in the face. Why do windows users have it easier and we don't?

And while most .tar.gz's are relatively easy to install (./configure, make, sudo make install), they're a pain to remove - you have to keep the original files, and remember where you put them when you want to uninstall.

well, I can argue both sides of this
[LIST]
[*]The reason they just give the source is because you can then compile it to run on whatever distro, hardware, etc you might have.
[*]The disadvantage of this is some people cannot compile or install this, and it is a pain like you say![/LIST]All in all, they just don't want to have to be responsible for having to provide 32 and 64 bit versions of debs, rpms, etc for like 50 distros ;)

---

### Post by ryanVickers on 2008-01-01
> **logos34 said:**
> ...and more linux distros use .rpm pkg mgr than any other...

sorry, I have to ask...

rpm - it stands for *Redhat Package Manager* does it not? and so you are saying redhat package manager package manager...

not picking on you or anything, just wanted to point this out :p

---

### Post by ~LoKe on 2008-01-01
> **ryanVickers said:**
> sorry, I have to ask...

rpm - it stands for *Redhat Package Manager* does it not? and so you are saying redhat package manager package manager...

not picking on you or anything, just wanted to point this out :p

It's redundant, yes, but it's [correct](http://en.wikipedia.org/wiki/RPM_Package_Manager).

---

### Post by Mateo on 2008-01-01
> **~LoKe said:**
> There are debs for almost every package.  You just have to look for them.

i run into programs all the time that don't have debs.  Only the most popular software has debs.

And ubuntu has probably the biggest repositories of any distro.  others have many many missing packages.

---

### Post by logos34 on 2008-01-01
> **~LoKe said:**
> It's redundant, yes, but it's [correct](http://en.wikipedia.org/wiki/RPM_Package_Manager).

Interesting point, gentlemen, I hadn't even noticed it.  But it appears you are both right.  

So in the spirit of Ockhams' razor and the law of succintness

> entia non sunt multiplicanda praeter necessitatem
('entities should not be multiplied beyond necessity')

I shall henceforth say simply 'rpm' and have done with it.

---

### Post by ryanVickers on 2008-01-01
> **~LoKe said:**
> It's redundant, yes, but it's [correct]("http://en.wikipedia.org/wiki/RPM_Package_Manager").

haha wow ok then :p this is quite the discussion over just that now as well eh? :p

---

### Post by FuturePilot on 2008-01-01
A tarball is the most universal way to distribute software. Sometimes though it's a binary and you don't have to worry about compiling. Just toss it in /opt.  However I think one of the best ways is to use [Autopackage]("http://autopackage.org/") It makes installing something just about as easy as Windows. And it will work on every distro.

---

### Post by Vadi on 2008-01-01
The repositories are only updated every 6 months. Quite a bit of programs are updated faster than that, so unless they give you a .deb or a .package, you have to compile to get the latest things (or fix really bad bugs).

And I meant the projects that do provide windows executables. Many don't, yeah. But when you go out of your way to make a windows .exe, why not make a .package?

Instead, some projects go out of their way and post on the IRC welcome message that "We don't provide .debs". Thanks, that's really kind of you.

---

### Post by ugm6hr on 2008-01-02
> **Steveway said:**
> Instead of using sudo make install, you can use sudo checkinstall (Providing you installed checkinstall) it will create a .deb. You can then easily remove it later.

Has anyone ever thought of creating a GUI for installation with checkinstall?  I'm not a programmer, but presumably a simple program could extract with tar, run the configure script, make and checkinstall, assuming the initial source was a tar file.

I would have thought something like that would be very handy for people who are still a little uncomfortable with Terminal.  I have been using Linux for about a year now, and am still happier with GUI apps than Terminal.

Any thoughts?

---

### Post by zipperback on 2008-01-02
> **Vadi said:**
>  Why do windows users have it easier and we don't?.

This is the purpose of package management systems such as synaptic package manager and adept installer.

Linux is NOT windows. It doesn't work the same.

- zipperback

:popcorn:

---

### Post by pjkoczan on 2008-01-02
> **Vadi said:**
> Why do windows users have it easier and we don't?

Easier is also a very subjective term. Windows may be the de facto default, but that does not necessarily make it easier.

Here's the installation procedure for most windows software:
- Find a site hosting the software.
- Make sure it's trustworthy and download the installer.
- open the installer, follow a GUI installer requiring many clicks and possible form entries.
- Lather, rinse, repeat.

Whereas for Linux (substitute package manager as appropriate):
- sudo apt-get install [packages]
- add repositories if it's not there (very well documented and very secure if you know what you're doing)
- or use synaptic/equivalent if you like GUIs

It's easier to bulk install in Linux (msi packages are a greater pain than RPMs and debs in my experiences), and the software is more likely to come from trustworthy and maintained sources. And the way that repositories work, it's often easier to detect and install updated packages.

I also like that Linux packages leave a lot less cruft than Windows installers. Instead of one set of some libraries per installed program as in Windows which may of may not have consistent versions, you have one set of consistent libraries system-wide. Yes, I know not everything is this way in Windows, but it happens more often that it should. This is the huge win with packages and dependencies.

---

### Post by Vadi on 2008-01-02
Yes, yes it is.

My point is that it's not being used, and that is frustrating.

(have you bothered to read the OP at all? Or even the page title? I'm aware that Linux is NOT windows.)

---

### Post by Vadi on 2008-01-02
> **pjkoczan said:**
> Easier is also a very subjective term. Windows may be the de facto default, but that does not necessarily make it easier.

Here's the installation procedure for most windows software:
- Find a site hosting the software.
- Make sure it's trustworthy and download the installer.
- open the installer, follow a GUI installer requiring many clicks and possible form entries.
- Lather, rinse, repeat.

Whereas for Linux (substitute package manager as appropriate):
- sudo apt-get install [packages]
- add repositories if it's not there (very well documented and very secure if you know what you're doing)
- or use synaptic/equivalent if you like GUIs

It's easier to bulk install in Linux (msi packages are a greater pain than RPMs and debs in my experiences), and the software is more likely to come from trustworthy and maintained sources. And the way that repositories work, it's often easier to detect and install updated packages.

I also like that Linux packages leave a lot less cruft than Windows installers. Instead of one set of some libraries per installed program as in Windows which may of may not have consistent versions, you have one set of consistent libraries system-wide. Yes, I know not everything is this way in Windows, but it happens more often that it should. This is the huge win with packages and dependencies.

Thank you for the long and informative reply. I am well aware of the wonders of repositories already however.

However, as the last post, please read the OP and realize that this is aimed at a specific segment of programs that -specifically- do not provide .debs or .packages.

Yes, some are available in repositories, but those are updated only every 6 months (any some apps may be missed out on, so make it 12 or more), like I said.

---

### Post by smartboyathome on 2008-01-02
> **ugm6hr said:**
> Has anyone ever thought of creating a GUI for installation with checkinstall?  I'm not a programmer, but presumably a simple program could extract with tar, run the configure script, make and checkinstall, assuming the initial source was a tar file.

I would have thought something like that would be very handy for people who are still a little uncomfortable with Terminal.  I have been using Linux for about a year now, and am still happier with GUI apps than Terminal.

Any thoughts?

The hard part is the configure, since you have to install the packages manually (they aren't always called the same thing in the repos as configure says).

---

