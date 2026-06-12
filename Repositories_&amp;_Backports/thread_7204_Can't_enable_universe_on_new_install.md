---
title: "Can't enable universe on new install"
date: 2004-12-05
forum: Repositories &amp; Backports
---

### Post by ultramouse on 2004-12-05
Hi all, I read the sticky thread, but this is not specifically related to any particular Universe package, but the Synaptic prog in general.

I just installed Ubuntu-- Even Mandrake is a painfully difficult variant compared to the sensical way Ubuntu seems to work, and I'm a big Gnome fan as opposed to K (I was previously on Mndrake 10.1).

I'm having a problem though: One of my most indispensible programs, GnuCash (which I kinda think should be in the core install) is supposedly available in the Universe repository. Problem is, the Universe isn't listed in my repository list on Synaptic. I edited  /etc/apt/sources.list to uncomment the path to Universe, but Synaptic gives me this message: 
> 
Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Packages /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_universe_binary-i386_Packages) - stat (2 No such file or directory)

Any ideas? I'm all about this distro so far, but obviously my ability to install key packages (many of which are apparently in Universe) is vital. 

Thanks in advance to anyone who might be able to help.

---

### Post by cabu on 2004-12-05
Click the reload button in Synaptic. It is the same as 'apt-get update'. It lets synaptic know what is available in universe.

---

### Post by adbak on 2004-12-05
You may want to copy and paste the contents of your /etc/apt/sources.list, using the code tags, of course.

Here's my sources.list:
```
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


deb http://archive.ubuntu.com/ubuntu/ warty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu/ warty universe
# deb-src http://archive.ubuntu.com/ubuntu/ warty universe

deb http://security.ubuntu.com/ubuntu/ warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted

deb ftp://ftp.nerim.net/debian-marillat/ testing main

```

That, with exception of the last repo (the nerim.net one), is the default sources.list of the public release of Warty.  Check to see if that is duplicated in your sources.list so that there aren't any typos or whole omissions of lines.

If there aren't any, then I suggest this to you: when you go to enable Universe, disable the Main repos as well.

If that doesn't work then I don't know what will.  :)  Good luck!

---

### Post by ultramouse on 2004-12-05
[QUOTE=adbak]You may want to copy and paste the contents of your /etc/apt/sources.list, using the code tags, of course.

Here's my sources.list:
```
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


deb http://archive.ubuntu.com/ubuntu/ warty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu/ warty universe
# deb-src http://archive.ubuntu.com/ubuntu/ warty universe

deb http://security.ubuntu.com/ubuntu/ warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted

deb ftp://ftp.nerim.net/debian-marillat/ testing main

```

That, with exception of the last repo (the nerim.net one), is the default sources.list of the public release of Warty.  Check to see if that is duplicated in your sources.list so that there aren't any typos or whole omissions of lines.

If there aren't any, then I suggest this to you: when you go to enable Universe, disable the Main repos as well.

If that doesn't work then I don't know what will.  :)  Good luck![/QUOTE]
 Thanks, after replacing the sources file and hitting reload, the "reload" list had universe in it.


thanks again!

---

