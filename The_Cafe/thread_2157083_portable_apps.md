---
title: "portable apps"
date: 2013-06-24
forum: The Cafe
---

### Post by huynhhuuhieu on 2013-06-24
*I'm very interested in portable apps, so I post here software for linux which only need _**extract**_ to run*
[sublime text]("http://www.sublimetext.com/"): code editor
[bluegriffon]("http://www.bluegriffon.org/"): html5 editor
[yoono]("http://www.yoono.com/"): chat, mail, social client

---

### Post by TheFu on 2013-06-24
Any app that is installed via tgz or tar.gz can be portable.  During installation, you can force any program to install to a non-standard location, which can also be considered "portable" provided that non-standard location is standard across your systems ... perhaps /opt or /home/{userid}/opt/ ?

Another method is just to retain a list of all the programs you like on your systems and install those across every system. The **dpkg --get-selections** and **dpkg --set-selections** commands will facilitate it.  While not portable, if you have sudo/root on all the systems involved, then it can work the same.  Just copy all your settings over to the new machine - being careful to maintain permissions, ownership and group data.

Portable apps have a larger role on Windows, because end-user settings are stored inside the registry and registries can't be mixed between different systems.  Linux stores end-user settings under each $HOME for the user, so those CAN be moved between systems almost always.  I routinely move my entire firefox and thunderbird settings, cache, bookmarks, emails, contacts between systems without any issue ... just because they are in my $HOME directory.  The only time I've seen issues is when different distro versions are involved.  Shoving a 12.04 $HOME onto a 10.04 $HOME will probably be harmful for the DE.

Still, it is nice to have a portable app on Linux too. I completely understand the desire AND need for them.

---

### Post by grahammechanical on 2013-06-25
Ubuntu on a USB memory stick is a complete set of portable apps. With a lot of work and a fair wind, by this time next year there will be on the market Ubuntu super phones. That will be the ultimate on portable apps - a portable OS - phone, tablet, PC.

---

### Post by huynhhuuhieu on 2013-06-29
I don't understand a little with compilation during installation
what commands should I use ?

---

### Post by TheFu on 2013-06-29
> **huynhhuuhieu said:**
> I don't understand a little with compilation during installation
what commands should I use ?

Which commands are needed completely depend on the way that the application, tool, package was created.  Almost always, there is either a README or INSTALL file included that explains what you need to do.  There are a few "standard" build methods too - "configure" or "make" and you can read up on how those work on the web, then tweak the build and installation as you like.

For as many different developers in the world, there are at least that many different ways to build software.  Sometimes a developer will not bother to make building his software easy - after all, he already knows how to build it. He doesn't need an explanation.  Of course, other developers familiar with the same build tools will not need help, unless there is a mistake in the code.

* configure - [http://tldp.org/LDP/LG/current/smith.html](http://tldp.org/LDP/LG/current/smith.html) explains the most commonly used way for C/C++ applications.

* Makefile - [http://www.cs.colby.edu/maxwell/courses/tutorials/maketutor/](http://www.cs.colby.edu/maxwell/courses/tutorials/maketutor/) though the website assumes some C/C++ knowledge and does NOT show a **make install** "target," which is often included in the Makefile for released code.

* Python and Perl have specific installation tools - setup.py and CPAN  (perl Makefile.PL, make, make test, make install)

* install - is a script that is often leveraged by programmers to copy files from the build area into the install area. I haven't seen this used much the last 5 yrs.

* Custom scripts.  Any programmer can elect to create custom installation scripts.  I've done this for my day-job for extremely complex n-tier system installs. Even with the custom script, the company would send an install engineer to make certain everything was installed, setup  properly, and didn't violate license terms for the client.

Sorry that there isn't an easy, "always-works," answer.  If there is a specific issue, ask either in these forums or at the support forums/site/email for the software you are trying to install, but be certain that you've done your homework first.

---

