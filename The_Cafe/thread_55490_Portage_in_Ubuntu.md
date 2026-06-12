---
title: "Portage in Ubuntu?"
date: 2005-08-09
forum: The Cafe
---

### Post by poofyhairguy on 2005-08-09
Has anyone (or can anyone) get this to work?

[http://forums.gentoo.org/viewtopic-t-125553-highlight-ubuntu.html](http://forums.gentoo.org/viewtopic-t-125553-highlight-ubuntu.html)

I have an idea. What if portage was for Ubuntu? (and other not Gentoo distros)

Hear me out.

One big complaint people have about Ubuntu is that its hard to get programs that aren't in the ubuntu repos or when the newest version is not in the repos.

What if that script could be used to bolt Portage on to Ubuntu? Let it be an "unofficial" and "unsupported" way to install programs? 

Cool thing about portage is that it compiles the program on the spot. Till now Gentoo people use the power of that to customize. Why can't non-Gentoo users use that to get programs with less hassle? A recent discussion here on the forum taught me that universal binaries that install on many distros is possible but difficult. Why go through it? Its easy to make an ebuild. Let ebuild be the new tar file and portage the new delivery system (instead of web sites). 

Sounds like a way to fix a problem. Linux style. If a few things can be done.

Is there a way to make an "ubuntu default" with the use tags? Make them so that they are sane without messing with them, and maybe mimic how Ubuntu packages install things?

Sounds great.

Seems like getting it installed is hard to do though.

---

### Post by felipe on 2005-08-09
i agree, having zillions of packages to choose from is a good thing, but dpkg/apt/debconf*/synaptic is a far more mature combo than portage will ever be.

accept that :)

i have been running gentoo on a test partition for months, it's funny sometimes but portage is clearly overengineered in some areas, while still too rough on many edges.

*debconf is great in preserving user altered config files, portage (etc-update) is a mess at that

---

### Post by poofyhairguy on 2005-08-09
[QUOTE=felipe]i agree, having zillions of packages to choose from is a good thing, but dpkg/apt/debconf*/synaptic is a far more mature combo than portage will ever be.
[/QUOTE]

Yeah. I like apt-get best too. Well made debs are nice. They are just kinda hard to make, and some people would prefer and ebuild to nothing.

---

### Post by poofyhairguy on 2005-08-09
What jDong has to say about it:

> Funny thing... I've attempted to port Portage over to Debian, but it was a flop... What a gargantuan mess Portage is! Even in Python, it's not modularized enough that ebuild subsystems can be substituted with apt/dpkg equivalents without ripping code apart everywhere!

[http://www.ubuntuforums.org/showthread.php?t=44904&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=44904&page=1&pp=10)

But here is earlier when he thought it might work:

[http://www.ubuntuforums.org/showthread.php?t=14920&page=1&pp=10&highlight=portage](http://www.ubuntuforums.org/showthread.php?t=14920&page=1&pp=10&highlight=portage)

And here is a mailing list thread about the idea:

[http://www.ubuntuforums.org/showthread.php?t=21845&highlight=portage](http://www.ubuntuforums.org/showthread.php?t=21845&highlight=portage)

So its come up before. I wonder if anyone has tried the script and posted about it here and I can't find it?

---

### Post by kreawit on 2005-08-09
Isnt it possible to make debs with scripts that download and compile code? Just like portage/port in Gentoo and Crux do. 

Example from Crux

[http://acrux.homelinux.org/crux/repos/grub/Pkgfile](http://acrux.homelinux.org/crux/repos/grub/Pkgfile)

# Description: GNU GRUB the GRand Unified Bootloader (GRUB Legacy) 
# URL: [http://www.gnu.org/software/grub](http://www.gnu.org/software/grub)
# Depends on: ncurses, gettext
# Maintainer: acrux

name=grub
version=0.97
release=1
source=(ftp://alpha.gnu.org/gnu/$name/$name-$version.tar.gz \
        grub-0.95.20040823-splash.patch.bz2 \
	[http://clc.morpheus.net/files/grub/0.95/crux02.xpm.gz](http://clc.morpheus.net/files/grub/0.95/crux02.xpm.gz) \
	menu.lst.sample )

build () {
	cd $name-$version

	# Apply Gentoo Linux patches
	bunzip2  $SRC/$name-0.95.20040823-splash.patch.bz2
	patch -p1 < $SRC/$name-0.95.20040823-splash.patch
    
	unset CXXFLAGS 
	export CFLAGS="-Os" 
    
	autoreconf -i -f
	./configure --prefix=/usr --sbindir=/sbin --disable-nls \
	--disable-auto-linux-mem-opt 
		
	make
	make DESTDIR=$PKG install
	rm -rf $PKG/usr/info

	mkdir -p $PKG/boot/grub
	install -m 644 ../{crux*,menu.lst.sample} $PKG/boot/grub/
}

I believe there is some debs that do this today, msttcorefonts is an installer for Microsoft True Type Core Fonts. The deb contains som scripts that downloads the fonts from Sourceforge and then installs them. 

Could this give us Portage functionality within apt-get/Synaptic without breaking what we have today?

---

### Post by luca_linux on 2005-08-09
Yeah, great idea.
Portage as an unofficial way to install program would be great!

---

### Post by N'Jal on 2005-08-09
Go for it! Or even integrate portage into autopackage that might be a better but harder idea.

---

### Post by papangul on 2005-08-09
[QUOTE=N'Jal]Go for it! Or even integrate portage into autopackage that might be a better but harder idea.[/QUOTE]
Why not integrate porthole(gui frontend for potage) into synaptic!

---

