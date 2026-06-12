---
title: "A rose by any other name: the alternate install cd"
date: 2007-09-17
forum: The Cafe
---

### Post by Mark_in_Hollywood on 2007-09-17
The distinction between the "desktop" and "alternate" or other names or synonyms are not reasonably clear to this user of Ubuntu after 2 years, starting with Breezy.

If the "alternate" cd is for users of Ubuntu who already have partitioned their hard disk drives with Ubuntu, it isn't understandable that this would be the better choice.

Nowwhere on the "get Ubuntu" page: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

does it suggest or explain what is what.

The most information it does give is:

"Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer."

I believe that confusing users with update, upgrade, distro-upgrade need to be worked on. 

Pardon this, but if it weren't for the fact the Ubuntu is a great operating system, the naming conventions used by Ubuntu Admins is almost as bad as: Explorer, Windows Explorer, Internet Explorer, exploder  . . . oooppsss, sorry Bill G.

---

### Post by Henry Rayker on 2007-09-17
I found the two installation types to be quite clear. The LiveCD is the LiveCD with the ability to install from the Live session; the alternate installation disk is just a text based installation.

The Alternate CD is NOT just for people who "have already partitioned their disks with Ubuntu" whatever that means. The alternate cd is the text based install; this is good because, for some people (myself included, on more than one machine I've gone to install) Ubuntu is just absolutely incapable of taking advantage of video hardware. Also, for people who have smaller amounts of RAM, the LiveCD might be a tad too bulky/slow.

update, upgrade and dist-upgrade are not really Ubuntu's doing, nor do they have anything to do with the alternate install cd. These are specified in the apt package manager...that said

update - updates your package management database
upgrade - upgrades all packages on your machine
dist-upgrade - upgrades your entire OS to the newest release

---

### Post by karellen on 2007-09-17
the ubuntu alternate cd is for people who want more control over the installation

---

### Post by Wolki on 2007-09-17
> **Henry Rayker said:**
> upgrade - upgrades all packages on your machine
dist-upgrade - upgrades your entire OS to the newest release

That's not quite correct.

upgrade will try to upgrade all your packages, as long as it doesn't have to add or remove other software (from changed dependencies).
dist-upgrade will try to upgrade your software, and add or remove other software as needed.

man apt-get has more information

---

### Post by lisati on 2007-09-17
I have used the text-base "alternate" CD as an alternative to the "Live" CD when, for some reason, the Live version hasn't worked too well on some particular hardware.

---

### Post by bapoumba on 2007-09-17
Desktop CD: graphical install, from the live CD, with menus you can click. Sometimes, some graphics cards are not supported or there is not enough memory t load it.
Alternate CD: text mode install with menus you can navigate/select with tab/space bar. It uses the debian text installer.

The partitioning step will allow in both cases to either make fresh partitions or use already existing ones on your drive.

---

### Post by Henry Rayker on 2007-09-18
> **Wolki said:**
> That's not quite correct.

upgrade will try to upgrade all your packages, as long as it doesn't have to add or remove other software (from changed dependencies).
dist-upgrade will try to upgrade your software, and add or remove other software as needed.

man apt-get has more information

Of course. I apologize for leaving out the distinction. I've moved away from Ubuntu (and other Debian based distros) in favor of Fedora and, most recently, Gentoo...I figured that my explanations would suffice for someone who has used Ubuntu for 2 years without realizing the difference between the alternate and live installation disks...

---

### Post by Wolki on 2007-09-19
> **Henry Rayker said:**
> Of course. I apologize for leaving out the distinction. I've moved away from Ubuntu (and other Debian based distros) in favor of Fedora and, most recently, Gentoo...I figured that my explanations would suffice for someone who has used Ubuntu for 2 years without realizing the difference between the alternate and live installation disks...

Just wanted to point out that the difference isn't that clear, since it's possible an upgrade within a distribution version requires a dist-upgrade, and possible (though *very* unlikely) that upgrading between versions can be done with a simple upgrade.

In the end, it won't matter that much, and especially for upgrades between versions of a distribution you're supposed to use update-manager anyway as it will do some error-checks and will know about some problems with upgrading and how to fix them.

How's life in fedora-land? I've considered to examine it as i'm a bit unhappy with some of ubuntu's recent decisions, but I'm quite attached to the debian way by now...

---

### Post by justin whitaker on 2007-09-19
I only use the ALT CDs....I think the difference is pretty clear, and they even state if you are unsure which to get, get the Desktop version.

---

