---
title: "The future of linux packages(and their managers)"
date: 2006-07-24
forum: The Cafe
---

### Post by The Noble on 2006-07-24
I keep reading about RPM hell, and decided to google "rpm hell" to read into the issue further, and came upon this article:

[http://www.ser1.net/Files/Essays/RPM_Hell.html](http://www.ser1.net/Files/Essays/RPM_Hell.html)

It seems well formulated, well thought out, and looks at the problem of RPM hell, debian packages (and their lack of being up to date much of the time), and the gentoo portage system. I have no clue how old the article is, so I can't guaruntee that certain issues may have been solved.

What I am trying to get across, is that what was said about the debian package management, although quite stable and well made, has a problem with the age of packages. Updates, when they come, are far and few between. Many programs are upgraded several months behind their release. I do realize that many popular programs are fine (a la firefox, amarok, openoffice, the core system, etc), but many lesser known programs are left at their alpha stage, even when the developers has released a nearly finished product.

How do we fix it? Truly, I do not know, maybe someone more experienced with Linux could comment, but I know there are vast improvements can be had. I do have a few comments on fixes (and some questions on my thoughts).

     1. I don't know exactly how the repos are populated with software right now, so maybe this is a bad idea, but how about a new testing repo? Something that can be submitted by authors of software? It wouldn't be added into Ubuntu by default, nor would it be anywhere near supported, but it could be put into /etc/apt/sources.list by the user.
        We, the community, would be the testers, possibly with an easy messaging system to contact the software developers (the devs of the software, or the packager). For example, If Joe from the Ubuntu community, or a fan of ubuntu, packages the latest Quod Libet player, and wants to have it implimented quickly for mass circulation for other users, has it submitted into these other repos as a placeholder until an official package is available. 

    2. An easier way to make .deb files to distribute at the maker's site. I don't have any experience on making them, but maybe a simple Gui to help would be in order? I think checkinstall does something like making a deb file when you */.configure, make, make install*, but I'm not sure -- correct me if I'm wrong. 

[EDIT] It looks like pbuilder can help make a .deb file, so it seems like number two can be ignored.

--
Note that this is just me ranting, and sorry this is really long. Hopefully I put my point across, and this could be commented on. For I want to see Linux progress and flourish, not slip into a system too bogged down by problems that could have been solved from the beginning.

---

### Post by aysiu on 2006-07-24
FYI: It was written in 2003
[http://www.ser1.net/essays.rhtml](http://www.ser1.net/essays.rhtml)

By the way, the kind of system your proposing is the current Debian system, which has stable, testing, unstable, and experimental branches (in that order).

Users who want a stable system with old software use stable. Users who want an extremely unstable system with cutting edge software use experimental.

Ubuntu is a bit different from that. It takes the unstable branch of Debian and develops off of that. The "stable" version of Ubuntu is whatever's out. The unstable version of Ubuntu is the upcoming release, which comes out every six months (with the exception of Dapper, which was two months late).

---

### Post by The Noble on 2006-07-24
Thank you, although I don't think a major redesign of rpm has taken place since then. ;)

---

### Post by aysiu on 2006-07-24
These links are a little more up-to-date:
[http://kitenet.net/~joey/blog/entry/rpm_hell.html](http://kitenet.net/~joey/blog/entry/rpm_hell.html)
[http://www.oreillynet.com/linux/blog/2006/06/the_new_rpm_hell_or_why_yum_an.html](http://www.oreillynet.com/linux/blog/2006/06/the_new_rpm_hell_or_why_yum_an.html)

---

### Post by The Noble on 2006-07-24
Haha, I saw the first one. Made me laugh actually. Although it is important to note that my little rant is just to make a suggestion on how to improve Ubuntu/Debian. 

Thank God Ubuntu is based off Debian.

Also, are .exe files statically linked? Or are the dlls controlled only by Microsoft, thus avoiding dependency hell. I've only heard of windows crashes and viruses, never of dll hell. For that matter, I've never heard of debian hell either...

---

### Post by aysiu on 2006-07-24
[http://en.wikipedia.org/wiki/Dll_hell](http://en.wikipedia.org/wiki/Dll_hell)

You may be interested in [this poll](http://www.ubuntuforums.org/showthread.php?t=110896), too.

---

