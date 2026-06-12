---
title: "Quick analysis of packages software developers should provide"
date: 2005-08-20
forum: The Cafe
---

### Post by jobezone on 2005-08-20
Hi, I wondered if you were interest in what I commented in [http://www.netsplit.com/blog/tech/autopackage_II](http://www.netsplit.com/blog/tech/autopackage_II) (I've corrected some typos and some of the wording, but it's essentially and 99 % the same). Perhaps everybody is tired of this conversation, but I think this is usefull for whoever is planning to release software for linux.

> One of the current complains is that developers wanting to package their software using the distribution's package formats and managers, have to do this to  300+ distros. But that isn't really true. Most of the majority of those distros aren't really intended for new users, and are special customizations for special audiences. Now, if we look at the top distributions intended for new linux users, we get a shorter list. Distrowatch has a top11 list, at [http://distrowatch.com/dwres.php?resource=major](http://distrowatch.com/dwres.php?resource=major).
Two of them are Freebsd and Gentoo, the first is not a linux distro, and the second needs no packages, and uses ebuild scripts instead for grabing, compiling and installing from source.
5 of them (Ubuntu, Debian, Knoppix, Mepis, and Xandros) uses .DEB, and 3 (Madriva, Fedora,Suse) use .RPM. Ubuntu is the only Debian-based distro which doesn't use Debian's packages and repositories directly. And there is slackware, which uses .TGZ, and doesn't use a package manager.
So, this means that if Software Vendors want to target the new user audience, they have to deal with 3 package formats , and 6 different linux systems. That makes it 3 RPM packages, 2 DEB's, and 1 TGZ package. Sudenly it isn't 300+ packages, but 6.

Now, let's see how some app developers have aproached this:
**Skype**, in their download page [http://www.skype.com/products/skype/linux/](http://www.skype.com/products/skype/linux/), have:
3 RPM packages, and 1 DEB package, directly targeting 7 of the 8 linux distro's I mentioned.
They aditionally have 2 binaries, one which needs QT in the system, and one which is QT compiled. These 2 binaries target Slackware, and any other linux user.

**Wine**, in their download page [http://www.winehq.com/site/download](http://www.winehq.com/site/download) , have 3 RPM packages, 2 DEB packages, and 1 TGZ package which targets all of the distros I mentioned. They aditionally have source for all the previous, and for Freebsd.

This i didn't mention, but free software developers also could (should?) try to speak with the distributions they intend to target, to place their package/software in there (repositories, etc.).

---

### Post by cowlip on 2005-08-20
Is htat your blog?  Anyway, I think skype is doing fine...it's a bitch to install other software though, like kde-apps or newer versions of software, it is soo frustrating to see they libc ONE MICROPOINT Higher, etc....  I really like Autopackage because I haven't experienced that frustration as of yet.

---

### Post by poofyhairguy on 2005-08-20
Good job. One thing I will say is that those people who complain about packages usually don't even want to make one...so three (basically) is still to much for them. Anything that doesn't magically take their source code and put it in a package is too much for them. Debs are great, but its hard to make good debs.

---

### Post by jobezone on 2005-08-20
No, it isn't my blog, sorry for not clearing this up. I just commented on it right at the end.

Anyway, I made this list with the top 100 distros in the "Page Hit Ranking" table of distrowatch ([http://www.distrowatch.org](http://www.distrowatch.org)) and the package management format they use:

1  	Ubuntu  	DEB
2 	Mandriva 	RPM
3 	Fedora 		RPM
4 	MEPIS 		DEB
5 	SUSE 		RPM
6 	Debian 		DEB
7 	KNOPPIX 	DEB
8 	Gentoo 		SRC (Portage)
9 	Damn Small 	DEB
10 	Slackware 	TGZ
11 	Xandros 	DEB
12 	Kubuntu 	DEB
13 	FreeBSD 	TBZ
14 	PCLinuxOS 	RPM
15 	SLAX 		TGZ
16 	Vector 		TGZ
17 	CentOS 		RPM
18 	Libranet 	DEB
19 	KANOTIX 	DEB
20 	PC-BSD 		TGZ
21 	Linspire 	DEB
22 	Zenwalk 	TGZ
23 	Arch 		TAR.GZ
24 	Puppy 		TAR.GZ
25 	Red Hat 	RPM
26 	VLOS 		Portage
27 	Ark 		RPM(APT)
28 	Yoper 		RPM
29 	aLinux 		RPM
30 	Solaris 	pkgadm
31 	IPCop 		none
32 	GeeXboX 	none
33 	Frugalware 	FPM(TAR.GZ)
34 	Scientific 	RPM
35 	WHAX 		TGZ
36 	White Box 	RPM
37 	Feather 	DEB
38 	Devil 		TAR.GZ
39 	LFS 		SRC
40 	Symphony 	DEB
41 	Gnoppix 	DEB
42 	Kurumin 	DEB
43 	OpenBSD 	TGZ
44 	SME Server 	RPM
45 	Onebase 	OLM
46 	Foresight 	Conary
47 	Zen 		DEB
48 	BLAG 		RPM
49 	ClarkConnect 	RPM(APT)
50 	Turbolinux 	RPM
51 	Kate OS 	TGZ
52 	FoX Desktop 	RPM
53 	Yellow Dog 	RPM
54 	BIG LINUX 	DEB
55 	Trustix 	RPM
56 	CRUX 		TAR.GZ
57 	Berry 		RPM
58 	Auditor 	DEB
59 	Vine 		RPM(APT)
60 	Lunar 		SRC
61 	m0n0wall 	none
62 	Progeny 	DEB
63 	PHLAK 		DEB
64 	Aurox 		RPM
65 	Astaro 		None
66 	AGNULA 		DEB
67 	Knoppix STD 	DEB
68 	DragonFly 	None
69 	Linux+ Live 	RPM
70 	AUSTRUMI 	TGZ
71 	LiveCD Router 	TGZ
72 	NetBSD 		TGZ
73 	Mediainlinux 	DEB
74 	FreeSBIE 	TGZ
75 	BeatrIX 	DEB
76 	Buffalo 	TAR.GZ
77 	redWall 	RPM
78 	Novell 		RPM
79 	Morphix 	DEB
80 	Gentoox 	Portage
81 	ParallelKnoppix	DEB
82 	MoviX 		None
83 	StartCom 	RPM
84 	Lormalinux 	RPM
85 	ADIOS 		RPM
86 	SmoothWall 	none
87 	QiLinux 	RPM
88 	Conectiva 	RPM
89 	GoboLinux 	TAR.BZ2
90 	dyne:bolic 	None
91 	Tao 		RPM
92 	T2 		SRC
93 	Overclockix 	DEB
94 	Lineox 		RPM
95 	INSERT 		DEB
96 	YES 		RPM
97 	tinysofa 	RPM
98 	Linux4all 	RPM
99 	SAM 		RPM
100 	rpath		Conary


Some gathering of numbers:

74 distributions use DEB (27), RPM (35) or TGZ (12).

Off the remaining 26, 8 don't use any package management, 5 use TAR.GZ, 3 use Portage, 3 use SRC, 2 use Conary, 1 uses TBZ, 1 uses pkgadm, 1 uses FPM(TAR.GZ), 1 uses OLM, and 1 uses TAR.BZ2 . All or almost all of these 26 are not intended for beginner usage.EDIT:And this can be said of almost all of the 74 distributions I mentioned above.

The top 10 distributions use DEB (5), RPM (3), TGZ (1) and Portage (1).

EDIT2:corrected this last line

---

### Post by jobezone on 2005-08-20
...

---

### Post by jobezone on 2005-08-22
There have been some more comments made in the blog post comment section I mentioned above, which I replied, and which I think may be interesting for others.

"
**Sun Aug 21 15:33:43 2005 by Tim Ringenbach**

There may not by 300 distros that the user base really uses, but using standard methods, an rpm you make is only good for 1 version of a given distro.

If you only want to support redhat and mandrake, you have to deal with rh8, rh9, fc1, fc2, fc3, fc4, mandrake 8, 8.1, 8.2, 9, 9.1, 9.2, 10, etc.

That's 13 already and I haven't even mention debian, unbuntu, SuSE, or gentoo.

Sure, it's possible to make an rpm work on more than one version, but depending on how far you go, you start getting into the binary compatability science that is the domain of autopackage. Might as well just make an autopackage so it really works.

**Sun Aug 21 19:18:55 2005 by jobezone**

Users which want the newest software are still using rh8,rh9,fc1,fc2,fc3? Or are using any mandrake version before the latest, for that matter? Or they are sticking with Debian Woody, which is 3 years old, or Ubuntu Warty Warthog which will be a year old in October, when the new versions have more features, more development time put into them?

If we are talking about users which want  recent software in their system, using FC1, Debian Woody or Ubuntu Warty Warthog would be a contradiction, as the version of their distribution are definetly old.

As far as I know Redhat doesn't give support for any Fedora Core release, let alone old ones. Debian supports Woody only in security updates, and this is meant for long-running machines which are working fine with Woody, and their administrators don't see a need to upgrade. This means, servers, and other types of installations where it doesn't matter if they have the newest software, just as long as it's secure, stable, and working.

This will also be true for Ubuntu starting with their next release, but it's still unknown what kind of support they will give. Most probably it will also be for security fixes and support.

You bring Gentoo, but Gentoo doesn't use packages. It uses scripts to fetch the source, configure and install it. I'm not too knowledgable on how it works, but as far as I understand, it's not that hard to create them, and their community can usually handle this very well. This could also be said of creating any other package in any other format, be it a DEB, a RPM or a Autopackage. Keeping a big package pool sane and working fine with each other is a different question.

Besides, I wouldn't say Gentoo is meant for casual users, or at least double-click type users.

"Just as along as I can d/l a package, double click, install and I'll be good to go."

I would prefer to single click it, and it be installed automatically. Watch out for gnome-app-install in the next version of Ubuntu. A screen of it: [http://shots.osdir.com/slideshows/slideshow.php?release=414&slide=28](http://shots.osdir.com/slideshows/slideshow.php?release=414&slide=28)
Sun Aug 21 19:21:08 2005 by jobezone

sorry, double-posted - You see, I'm also newbie:)

**Mon Aug 22 10:20:02 2005 by Mike Hearn**

Yes, it's very common for people to be using out of date or unsupported distros like Red Hat 9, Fedora Core 1/2, and so on. These people often do try and install new software - upgrading an OS is no trivial thing for most users, they want as much life out of it as possible. That's why WineHQ still provides RH9 packages for instance.

**Mon Aug 22 19:52:39 2005 by jobezone**

Well, my advise to home users with Redhat 9 would be to upgrade to Fedora Core, since Redhat Linux has been discontinued by RedHat. In its place Fedora Core was started, which RedHat then takes and makes Redhat Enterprise.
RedHat 9 was released in the begining of 2003, which shows when comparing with Fedora Core 4: it uses Gnome 2.2 vs Gnome 2.10, KDE 3.1 vs KDE 3.4, Xfree86 ( 4.3 ) vs Xorg ( 6.8 ), linux 2.4 vs linux 2.6, gimp 1.2 vs 2.2. Many other improvements have been done on the usability level and hardware support during these 2 years, so this upgrade wouldn't make their hardware obsolete, but more and better supported; it wouldn't decrease the application features but increase them; it wouldn't decrease their overall user experience, but increase it.

As far as upgrading not being a trivial thing, it sure is in Debian-like distributions for that matter. It's fairly easy to change the distribution names in the repositories configuration, from sarge to unstable (my current Debian-I-admit-not-so-user-friendly-system), or from Warty to Hoary (my previous Ubuntu system). Or to add the upgrade/install CD to the repositories (which Ubuntu automatically detects when inserted, and asks if users want to upgrade). The upgrade in both systems went excellent, and I just needed to read their release notes for some changes which were not handled automatically. Ubuntu even made this easier: from warty to warthog, the entire locale system was switched to utf-8, and so I was automatically questioned if I wanted to search and convert my files which had non utf-8 names to utf-8. I assume that all of this (and more?) is already or will be the norm in other home user oriented distributions.

Then there are the various forums where they can get also get help, and learn from other people's experiences with upgrading.

I also don't think it's as common as you say for users to be using out of date distributions. It's not what I've seen in forums and other places where home desktop users comment, but it may happen. If it does, I would think that this is because they're pretty happy with their system and the applications they've been using.

I think autopackage may become useful for software which is distributed in binary form only, namely, proprietary software. This type of software can't be placed on most distributions repositories and CD's, so they loose the first rows (of presenting themselves to users) to free software.
But there are also other methods. For example, a few distributions carry along an extra repository for proprietary software, where the newest versions of java, flash, etc. are maintained in packages. Or proprietary software makers themselves could get their act together and set up a common Linux repository with its own download manager, and an integrated paying system, like iTunes does for music.
"

---

