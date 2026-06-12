---
title: "install .deb without root privileges?"
date: 2010-05-21
forum: Security
---

### Post by cometdog on 2010-05-21
Tried to search but didn't come up with any threads on this.  Apologies if I missed something.

Just wondering.  It seems like it is potentially a security issue that all .deb packages require root permissions to be installed.  (At least I think this is true, right?)  I'm sure there may be some very good reasons about what details of the package manager require access to which databases, etc.

But shouldn't there be a way to create non-root-installable packages for particular kinds of "applications" that wouldn't require root priviliges for installation otherwise?  I don't care if they're called something other than .deb, would probably make sense to differentiate them.

It seems like there are obvious candidates for things like this.  Themes, screensavers.  Things that one typically downloads and drops into a non-root location.  Even potentially applications that you could install in your home directory but not system-wide.

The issue, as I see it, is that there are alternative methods for installing things, not as root.  But none of them come with the conveniences of the package management system.  Dead-simple use, repositories, automatic updates, easy removal of all installed files, etc.

And that creates security problems.  Given a choice, a novice user is going to prefer to add a repository and/or install a .deb file, rather than running some script that spews out files across the filesystem that are a nightmare for the novice to remove.  Then social engineering comes into play, and people's computers can be compromised by installing things the convenient but dangerous way (with root access).

I agree that many kinds of programs, particularly ones that need to end up in the search path, should require root for installation.  But there are also those that don't.  I'm guessing it isn't trivial to work this out, since as far as I know it doesn't exist yet.  I can only imagine that there are issues with dependency resolution as non-root, etc.  But I bet it could be done.

---

### Post by TheGnomeOfMetal on 2010-05-21
im pretty sure you could use the sudo command to install it without logging in as root. the sudo command allows you to run as root, but you dont have to login as root. so just run sudo dpkg -i <package name> to install. before you use that you must change the directory to where you want it installed by using the CD command

---

### Post by CharlesA on 2010-05-21
If you are installing a deb, you generally need to have root privlages to install it, since it places files in root owned directories.

---

### Post by bodhi.zazen on 2010-05-21
The essence you seek is not in the .deb 

You can extract the .deb and install it anywhere you wish, so long as you have permissions, so yes you can "install" executable files into $HOME , /tmp, etc, etc.

This is why some people mount /tmp and /var and /home noexec and nosuid ...

The essence you seek is linux permissions. package management tools (aptitude, apt-get, synaptic, etc) are front ends for apt and you can not access the system files (/etc /usr) without root privileges and you can not alter the data base without root privilages.

So there is nothing preventing you from installing a chroot or an executable package or what not in $HOME. You could then probably write a .deb that would work with fakeroot.

This is why, IMO, people worry too much about rootkits, much damage can be done with unauthorized shell access without needing root privilages.

This is also one reason why to "harden" Debian / Ubuntu one puts /var /tmp /home on separate partitions, so that they can be mounted noexec , nodev, and nosuid (as needed).

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

[http://www.debian.org/doc/manuals/securing-debian-howto/ch3.en.html#s3.2](http://www.debian.org/doc/manuals/securing-debian-howto/ch3.en.html#s3.2)

[http://www.softpanorama.org/Access_control/Permissions/file_permissions_hardening.shtml](http://www.softpanorama.org/Access_control/Permissions/file_permissions_hardening.shtml)

> A few minutes of preparation and planning ahead before putting your  systems  on-line can help to protect them and the data stored on them.[INDENT]         There should never be a reason for users' home directories to          allow SUID/SGID programs to be run from there. 
     [/INDENT]
[LIST]
[*]Use the nosuid option in         /etc/fstab for partitions that are writable          by others than root.
[*]You may also wish to use nodev and         noexec on users' home partitions, as well          as /var, thus prohibiting execution of          programs, and creation of character or block devices, which should          never be necessary anyway
[/LIST]


---

### Post by bcbc on 2010-05-21
> **cometdog said:**
> But shouldn't there be a way to create non-root-installable packages for particular kinds of "applications" that wouldn't require root priviliges for installation otherwise?  I don't care if they're called something other than .deb, would probably make sense to differentiate them.


I thought the same thing. I currently run windows xp as a non-admin and I often install programs without administrator access. I question anything that requires admin access - usually these add irritating startup checks for updates (best case).

You still risk all your personal files for a malicious program (so it's not guaranteed safe), but stuff that is obviously malicious is discovered quickly. Most viruses etc. are more stealthy and look for system dll's to bury themselves in.

Anyway - it doesn't seem like linux gets a lot of virus trouble, but maybe this will come up in the future.

---

### Post by OpSecShellshock on 2010-05-21
In most cases I've seen, something that isn't an application and doesn't need to be installed in system files won't be packaged as a .deb anyway. It will either be tarred or in the form of an executable shell script or something. For look/feel tweaks and the like you can usually just drop the archive into the appropriate front-end and have it take effect. I'd imagine screen savers work the same way.

In fact, I'd be suspicious of something that purports to be a theme, screen saver or something like that, but comes packaged as a .deb for installation. It's not necessary.

---

### Post by cometdog on 2010-05-22
> **OpSecShellshock said:**
> It will either be tarred or in the form of an executable shell script or something. For look/feel tweaks and the like you can usually just drop the archive into the appropriate front-end and have it take effect. I'd imagine screen savers work the same way.

In fact, I'd be suspicious of something that purports to be a theme, screen saver or something like that, but comes packaged as a .deb for installation. It's not necessary.

True, but that's sort of my point.  This doesn't come with any of the other benefits of package management.  No dependency resolution.  No automatic updating.  No easy removal later (unless you know the right command line tools and where to look).

It just seems silly that all these benefits are reserved for the stuff that has to be installed as root.  

In my opinion, that just encourages people to try to find .deb files for things that shouldn't need to be installed that way, which turns into a security risk.

Maybe I didn't name the thread correctly, or maybe I wasn't clear enough in my original post, because it seems like most of the other responses aren't understanding what I was getting at.

---

### Post by cometdog on 2010-05-22
> **bodhi.zazen said:**
> The essence you seek is not in the .deb 

Yes, good point.  I guess the essence I seek is really in the package management.  I want package management for stuff that doesn't need to be installed as root.

It seems like that could really open the door to some nice things.  Like, for example, installation of software on a per-user basis but with all the benefits of package management.  Easy installation, dependency resolution, automatic updating, easy removal of all files later, etc.

---

### Post by bodhi.zazen on 2010-05-22
> **cometdog said:**
> True, but that's sort of my point.  This doesn't come with any of the other benefits of package management.  No dependency resolution.  No automatic updating.  No easy removal later (unless you know the right command line tools and where to look).

It just seems silly that all these benefits are reserved for the stuff that has to be installed as root.  

In my opinion, that just encourages people to try to find .deb files for things that shouldn't need to be installed that way, which turns into a security risk.

Maybe I didn't name the thread correctly, or maybe I wasn't clear enough in my original post, because it seems like most of the other responses aren't understanding what I was getting at.

Well packaged source code should be easy to remove

make uninstall

Read the README

Alternately you can use checkinstall

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

Honestly, if you are going to go with source code, after a short time, it is not *that* hard to find the dependencies and make install. It does take some time to get used to. but as you are going outside the repost, you loose most, if not all, the benefits you list as benefits of a .deb.

Also many major projects will provide .rpm , .deb , and source code.

---

### Post by dfreer on 2010-05-23
/rant time

Really, I think it's dpkg that's to blame here. I'd love to see a more flexible package manager that is able to handle mixed architecture installations and in this case seperate root/user package enviroments. Not really sure I can explain what I mean here clearly but I'll give it a shot.

First off, various architectures. We can currently run 64-bit code and 32-bit code on x86_64 processors, so we should be able to install a 64-bit version of Firefox and a 32-bit version of Firefox without conflicts. But the current behavior has the 32-bit package installing libs in /usr/lib/firefox-3.x.x/ and the 64-bit package in /usr/lib/firefox-3.x.x/. 

They've been messing with that upstream at debian for a couple years now, but it's still a mess. Our package building farms and dpkg should be able to automatically place the 64-bit libs in /usr/lib64/ and the 32-bit in /usr/lib32/ or some such solution. Furthermore, you should be able to select a "default" version in the package manager, which basically just creates a sym link from /usr/bin/firefox-XX to /usr/bin/firefox. Each would still have it's own place in the application menu, just one would be a default.

As for this case, why shouldn't the user be able to mark in the package manager to install this software "system-wide" (i.e. root in /usr/bin) or for "local user only" (i.e. user in ~/bin)? You can have packages marked as root only (kernel upgrades and such), but the package manager needn't be run only by root and should be able to intelligently place packages in local enviroments. 

It's the UNIX way to do things anyways (oh the server only has libpng2.0? I can install libpng3.0 in my ~/libs folder and whenever I run a local program it places a preference on libs found in my local folder over ones in /usr/lib/). Anyways, that's my rant.

---

### Post by OpSecShellshock on 2010-05-23
To be honest, there's nothing stopping anyone from setting up their systems to allow such things as far as I know (provided they know how to do it). I can't think of anything I personally do that both requires 32 bit architecture and that I can't function without (but I'm fortunate in that I have one of each in case it ever comes up). That said, emulation or virtual builds might be able to get around the conflicting path issue.

Fundamentally, of course, it's not an architecture, OS, or security issue so much as it's a software development issue. But that doesn't really help people who just want to use stuff I guess.

---

### Post by cometdog on 2010-05-24
> **bodhi.zazen said:**
> Well packaged source code should be easy to remove

make uninstall

Read the README

Alternately you can use checkinstall

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

Honestly, if you are going to go with source code, after a short time, it is not *that* hard to find the dependencies and make install. It does take some time to get used to. but as you are going outside the repost, you loose most, if not all, the benefits you list as benefits of a .deb.

Also many major projects will provide .rpm , .deb , and source code.

True.  I don't dispute that it is possible to remove things cleanly that weren't installed from .deb files.  It is clearly possible to find out where those files went.  And it's not too bad once you get used to it.

For me, the first I tried to remove something I installed from source, I had to spend an hour or two googling around to try to understand what I was doing and I still felt uncomfortable with it.  To this day I don't remember the commands off the top of my head, and would have to look this up each time.  Easier, now that I know what I'm looking for.  (And now that you kindly posted them in this thread.)

But while the average end user will easily end up in the situation of wanting to install something that should not need root privileges to be installed, they will NOT have the patience to figure out how to remove it.  They will just decide the next time that they need to install from .deb instead.

Effectively we are socially engineering people to believe that the "right" way to install ANYTHING is to install it as root (sudo) with a .deb file, and they won't think twice about the access they are providing to their system when they do so.

This isn't too much of a problem now.  Let's be honest, we're mostly geeks and like playing with our OS.  So maybe not a big deal at the moment.  But it seems like a security risk, and it only gets worse as more and more people use Ubuntu.

Anyway, don't we like package management?  This is the ultimate way to install, track, update software, right?  I think it should be important to get it working such that it always can use the minimum privileges possible.

---

### Post by cometdog on 2010-05-24
> **OpSecShellshock said:**
> 
Fundamentally, of course, it's not an architecture, OS, or security issue so much as it's a software development issue. But that doesn't really help people who just want to use stuff I guess.

The 32-bit vs 64-bit binary business may not be a security issue.  But I believe the lack of package management for non-root stuff is.

---

