---
title: "No Cinepaint in Ubuntu 8.10 intrepid???"
date: 2008-11-14
forum: Ubuntu Studio
---

### Post by edgaruy1980 on 2008-11-14
:confused: Tried in vane to install it and it won't work the older version.
So it is not supported, sounds so much  when we had Vista upgrade at work when half of our software didn't work...
There is a way to install maybe from source???
 but the list of dependencies is  very long, eww..

I know it was removed from the repositories, bummer..

---

### Post by pseudo endeavor on 2008-12-08
From the CinePaint download page:

"[Ubuntu - Currently unavailable due to Debian issues. Working on it.]("http://www.cinepaint.org/docs/download.html")"

---

### Post by lt_gustavsen on 2008-12-10
> **edgaruy1980 said:**
> :confused: Tried in vane to install it and it won't work the older version.
So it is not supported, sounds so much  when we had Vista upgrade at work when half of our software didn't work...
There is a way to install maybe from source???
 but the list of dependencies is  very long, eww..

I know it was removed from the repositories, bummer..

On the [cinepaint download page ]("http://www.cinepaint.org/docs/download.html")there is two ubuntu scripts. One build cinepaint from the stable version and the other from cvs.

---

### Post by jedimasterk on 2008-12-18
Ubuntu definately not a platform for photographers!!!. It Sucks for any professional photography work or video work!!!. A real shame too!. Linux is very stable!

---

### Post by unoodles on 2008-12-19
I looked into this issue a while ago, and I think the problem is that it uses a very old, unsupported version of GTK.

---

### Post by pseudo endeavor on 2008-12-27
Returned to the download page & ran the CVS script:

[ubuntu.sh]("http://cinepaint.cvs.sourceforge.net/viewvc/*checkout*/cinepaint/cinepaint-project/cinepaint/ubuntu-cvs.sh?content-type=text/plain")

All went well aside from an apparently common problem. "libcinepaint.so.0" could not be found. I read a solution somewhere that called for me to "gksudo thunar" (just noticed this was kde, eyyy) /usr/local/lib and change the permissions of everything cinepaint related to "read & write" 

I then needed to run "ldconfig" in /usr/local/lib. Followed by "ldd /usr/local/bin/cinepaint" -After that I started making pictures in cinepaint. 

*I'm counting on someone to find the appropriate, terminal driven solution. However, that's my 2 cents.

---

### Post by jack_hmr on 2009-01-01
I have .22-1 running on Ubuntu Intrepid 64 bit.

I am sure there is a better way but this is what I did.

Install the hardy package libopenexr2ldbl
[http://packages.ubuntu.com/hardy/amd64/libopenexr2ldbl/download]("http://packages.ubuntu.com/hardy/amd64/libopenexr2ldbl/download")

Install the packages on one of these pages and install the one with the shortest file name last:
32bit [http://sidux.net/etorix/i386/binary/]("http://sidux.net/etorix/i386/binary/")
64bit [http://sidux.net/etorix/amd64/binary/]("http://sidux.net/etorix/amd64/binary/")


Buyer beware. From cinepaint.org "# CinePaint 0.20-1-1.3 is in Etch (stable). CinePaint was removed from Debian lenny (testing) because Debian has dropped support for GTK1. CinePaint GTK2 exists and Debian packaging work is being done by Aedan Kelly. Experimental debs are here.
# Fedora - Popular RPM-based distro. "

I haven't used it much but it has worked fine so far.

---

### Post by cotcot on 2009-01-02
> **jedimasterk said:**
> Ubuntu definately not a platform for photographers!!!. It Sucks for any professional photography work or video work!!!. A real shame too!. Linux is very stable!

This is not what I experience. I am running blender (VSE), cinelerra, kdenlive, gimp, cinepaint, ufraw, ... to my satisfaction. 

Maybe you could be more precise on what sucks for you. Facts are helpful, emotions not. What do you miss on your ubuntu platform ? Is there something that ubuntu does not have what other distros have ?

I got cinepaint from these repos (for hardy):
> deb [http://ppa.launchpad.net/secretlondon/ubuntu](http://ppa.launchpad.net/secretlondon/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/secretlondon/ubuntu](http://ppa.launchpad.net/secretlondon/ubuntu) hardy main
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main

---

### Post by daev64 on 2009-01-21
> 

On the cinepaint download page there is two ubuntu scripts. One build cinepaint from the stable version and the other from cvs.



Has anyone had any luck with these instructions in Intrepid (32bit)? I've tried running the scripts from the terminal as stated and it all seems to go as planned until the last few steps, when I get:

sh: Can't open autogen.sh
ubuntu.sh: 6: ./configure: not found
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.

Knowing me (and my current state of n00bness) it's pilot error... but I could sure use a pointer if anyone has one.

Thanks, 

dave

---

### Post by kernel_script on 2009-02-19
> **cotcot said:**
> 
I got cinepaint from these repos (for hardy):
Quote:
deb [http://ppa.launchpad.net/secretlondon/ubuntu](http://ppa.launchpad.net/secretlondon/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/secretlondon/ubuntu](http://ppa.launchpad.net/secretlondon/ubuntu) hardy main
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main

Thanks for the tip cotcot!

---

### Post by barmaley on 2009-03-21
Thank you, cotcot

Your advice worked fine.
Thank you very much!

---

### Post by bdalzell on 2009-05-26
> sh: Can't open autogen.sh
ubuntu.sh: 6: ./configure: not found
make: *** No targets specified and no makefile found. Stop.
make: *** No rule to make target `install'. Stop.


i had to download the autogen.sh file and install a copy in the folder I rand the rest of the install cinepaint script from.

of course cinepaint still would not run because I was missing one of the libraries but at least the installation script completed itself

---

