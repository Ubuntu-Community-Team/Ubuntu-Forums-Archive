---
title: "FreeBSD. Tried it..."
date: 2009-12-10
forum: The Cafe
---

### Post by dragos240 on 2009-12-10
Well I tried FreeBSD out, and to be honest, the packaging system is a tad basic.... I think I spent an hour or so trying to compile bash and it's dependencies. They use the basic SH shell as the default, which lacks some features that bash has. It feels quite foreign, typing away inside an unknown world. Ports seems quite similar to portage, but I still prefer portage. I have to cd into /usr/ports and search for the package I want to download and compile. I'm not flaming it, or it's users, this was just my 3 hour experience with it. I am trying to get a simple box of it up and running smoothly, hopefully sometime soon. When I get to that stage, I'll give a more in-depth point of view to you. Still.... I prefer Linux....

---

### Post by &#32 Greg on 2009-12-10
Why not pkg_add the binary, at least until later?

---

### Post by dragos240 on 2009-12-10
> **&#32 Greg said:**
> Why not pkg_add the binary, at least until later?

Didn't know about that tool.

---

### Post by ddnev45 on 2009-12-10
In a terminal, the command:

```
whereis <package name>
```

is a handy search tool to find a package in /usr/ports.

[Man page for whereis]("http://www.freebsd.org/cgi/man.cgi?query=whereis&apropos=0&sektion=0&manpath=FreeBSD+8.0-RELEASE&format=html")

---

### Post by dragos240 on 2009-12-10
> **ddnev45 said:**
> In a terminal, the command:

```
whereis <package name>
```is a handy search tool to find a package in /usr/ports.

[Man page for whereis]("http://www.freebsd.org/cgi/man.cgi?query=whereis&apropos=0&sektion=0&manpath=FreeBSD+8.0-RELEASE&format=html")

Thanks :)

If only all the packaging tools were in one package. Ex:

Apt uses multiple tools, apt-get, apt-cache, apt-key, etc.

Whereas some other distros have an all in one tool. Ex. yum, pacman, emerge.

Just makes more sense.

---

### Post by DeadSuperHero on 2009-12-10
I feel for you dragos, I made that very same mistake of confusing ports (cd/usr/ports/desktop/kde) --get with pkg_add kdedesktop (Note that I don't have actual directory entries or packagenames, this is just an example off the top of my head). I ended up compiling all of KDE 4.3's libraries only to have it fail drastically. It took three days of effort, too.

It was a great educational moment in my life, though.

---

### Post by ddnev45 on 2009-12-10
I had it up and running for a couple days, but too many hardware issues and lack of time to really make a go of it. Liked it for the most part though; would be the way to go if you were mainly using terminal apps, tiling wm's I think.

You may find this useful:

[Trying BSD]("http://www.ostalk.org/showthread.php?tid=776")

---

### Post by chris200x9 on 2009-12-10
freeBSD is cool I set it up to fool with it as a server, I have to say I really like it ports is way cooler than portage and fails alot less often. Plus it lets you configure packages one by one instead of use flags. And ZFS! You are right though sh does really suck though.

---

### Post by kk0sse54 on 2009-12-16
> **dragos240 said:**
> Well I tried FreeBSD out, and to be honest, the packaging system is a tad basic.... I think I spent an hour or so trying to compile bash and it's dependencies. They use the basic SH shell as the default, which lacks some features that bash has.
Which is why I use ksh ;)

>  It feels quite foreign, typing away inside an unknown world. Ports seems quite similar to portage, but I still prefer portage. I have to cd into /usr/ports and search for the package I want to download and compile.

don't want to cd to specific ports directories? Depending on what tool you use just "portinstall <desired port>" or "portmaster <desired port>"

> Didn't know about that tool. 
Somebody didn't read the handbook :p

> Thanks

If only all the packaging tools were in one package. Ex:

Apt uses multiple tools, apt-get, apt-cache, apt-key, etc.

Whereas some other distros have an all in one tool. Ex. yum, pacman, emerge.

Just makes more sense. 

I agree with you to an extent. It used to bug me to end that there was no unified frontend for the multitude of shell scripts i.e. pkg_add, pkg_info, pkg_delete etc etc. The closest thing to this is either portmaster, portmanager, or portmanager but now in days I enjoy having different options.I don't know if the differences are comparable to that of perhaps paludis and portage but say for example you don't like portupgrade and it's ruby database. Just switch to something more simpler like portmaster, or vice versa.

---

### Post by 3rdalbum on 2009-12-16
I thought PC-BSD was cool; it's FreeBSD but friendly like Ubuntu, and with an easy packaging system.

Until I tried it.

There's almost nothing packaged for easy installation; the whole thing basically depends on Ports. And by default there's nothing in the Ports directory. And I couldn't find any documentation for how to actually populate the Ports directory.

Oh, what a wasted opportunity. I'm still stuck with Ubuntu :-)

---

### Post by baddog144 on 2009-12-16
I had a a pretty bad experience, but that's more due to my connection being incredibly weird with Passive FTP than anything else. I'm looking forward to trying to again when my connection doesn't fail completely :(

---

### Post by chris200x9 on 2009-12-16
> **3rdalbum said:**
> I thought PC-BSD was cool; it's FreeBSD but friendly like Ubuntu, and with an easy packaging system.

Until I tried it.

There's almost nothing packaged for easy installation; the whole thing basically depends on Ports. And by default there's nothing in the Ports directory. And I couldn't find any documentation for how to actually populate the Ports directory.

Oh, what a wasted opportunity. I'm still stuck with Ubuntu :-)

i think you want ```
portsnap fetch
``` then ```
 portsnap extract
```

---

### Post by munky99999 on 2009-12-16
ya going from distro to distro is always going to have a few hiccups. Going from linux to unix is quite similar.

For example. OP didnt know of pkg_add. The same thing could have been experienced in fedora with not knowing YUM or gentoo with not knowing emerge. :P

---

### Post by Pogeymanz on 2009-12-16
I've also been toying with FreeBSD lately. I like it, but like you said, there seem to be more powerful package managers in Linux.

Which led me to finally installing Gentoo (as I type). I have to admit, Gentoo is pretty awesome and I love the idea of emerge and USE flags. If anything can get me away from Arch, this may be it.

---

