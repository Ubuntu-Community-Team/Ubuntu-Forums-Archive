---
title: "bmpX &amp; .."
date: 2005-10-19
forum: Requests
---

### Post by faen on 2005-10-19
beep media player x, along with updated versions of pango, cairo and newest taglibs would be nifty :):rolleyes:

---

### Post by Pablo_Escobar on 2005-10-19
Bmp is available in the repos :)

---

### Post by christooss on 2005-10-19
faen why dont' you use repositories providet by shu?

---

### Post by r0nin on 2005-10-20
It depends on:

[b]
bmpx:
 Depends: libtag1c2 (>=1.3.1) but it is not installable
 Depends: libtagc0 but it is not going to be installed
[/b]

---

### Post by christooss on 2005-10-20
You get this when sudo apt-get install bmpx?????

---

### Post by r0nin on 2005-10-20
[QUOTE=christooss]You get this when sudo apt-get install bmpx?????[/QUOTE]

Yes, just checked again. Still the same dependency problem!

---

### Post by christooss on 2005-10-20
Can you

sudo apt-get install libtag1c2 and

sudo apt-get install libtagc0 ?????

---

### Post by Pablo_Escobar on 2005-10-20
Youv'e tried this repo ??
deb [http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx](http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx) ./

---

### Post by r0nin on 2005-10-20
Yes, that's the repo I'm trying to use.

Terminal Output when apt-getting:

```

pierre@p4:~$ sudo apt-get install libtag1c2
Password:
Reading package lists... Done
Building dependency tree... Done
Package libtag1c2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libtag1c2 has no installation candidate
pierre@p4:~$ sudo apt-get install libtagc0
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libtagc0: Depends: libtag1c2 (>= 1.3.1) but it is not installable
E: Broken packages
pierre@p4:~$

```

---

### Post by christooss on 2005-10-20
Hm are you using breezy?

---

### Post by r0nin on 2005-10-20
I'm using a fresh install of Breezy and havn't done any risky updates or fiddled with any settings!

---

### Post by Pablo_Escobar on 2005-10-20
Add universe repositories to the /etc/apt/sources.list - according to the [http://packages.ubuntu.com]("http://packages.ubuntu.com") they both should be there.

> Package libtagc0

    * breezy (libs): TagLib Audio Meta-Data Library (C bindings) [universe]
      1.3.1-1.1ubuntu1: amd64 i386 powerpc


---

### Post by christooss on 2005-10-20
what about if you try to install libtag1-dev libtagc0-dev and than bmpx?

---

### Post by christooss on 2005-10-20
[QUOTE=Pablo_Escobar]Add universe repositories to the /etc/apt/sources.list - according to the [http://packages.ubuntu.com]("http://packages.ubuntu.com") they both should be there.[/QUOTE]
libtagc0: Depends: libtag1c2 (>= 1.3.1) but it is not installable
E: Broken packages

---

### Post by r0nin on 2005-10-20
My sources.list

```

deb http://ch.archive.ubuntu.com/ubuntu breezy universe
deb-src http://ch.archive.ubuntu.com/ubuntu breezy universe 

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted 

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe 

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

# Unofficial packages by Christian Marillat
#deb ftp://ftp.nerim.net/debian-marillat/ sarge main

# Amule
# deb http://amule-debian.dyndns.org/ debian/

# Skype
# deb http://download.skype.com/linux/repos/debian/ stable non-free

# VLC
# deb http://download.videolan.org/pub/videolan/debian sarge main
# deb-src http://download.videolan.org/pub/videolan/debian sarge main

# Opera
#deb http://deb.opera.com/opera/ unstable non-free

# RareWares/Debian Multi-Media Repository for Unstable
#deb http://www.rarewares.org/debian/packages/unstable/ ./ 

# RareWares/Debian Multi-Media Repository for Unstable - Experimental Staging
#deb http://www.rarewares.org/debian/packages/experimental/ ./

#Cipherfunk
#deb ftp://cipherfunk.org/pub/packages/ubuntu/ breezy main
#deb-src ftp://cipherfunk.org/pub/packages/ubuntu/ breezy main

#BMPx
 deb http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx ./

```

---

### Post by zeroconf on 2006-06-16
tried the repo:
deb [http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx](http://eros.vlo.gda.pl/~szuwarek/files/linux/bmpx) ./

```

$ sudo apt-get install bmpx
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  bmpx: Depends: libdbus-1-1 (>= 0.36.2) but it is not installable
        Depends: libdbus-glib-1-1 (>= 0.36.2) but it is not installable
        Depends: libtag1c2 (>= 1.3.1) but it is not installable
E: Broken packages


```

I use Xubuntu 6.06 LTS and I have main, restricted, universe, multiverse repos already allowed. Still incompatibility problems...

---

### Post by nismohasan on 2006-06-22
i get the following errors..

> hasan@nismo-linux:~$ sudo apt-get install bmpx
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  bmpx: Depends: libdbus-1-1 (>= 0.36.2) but it is not installable
        Depends: libdbus-glib-1-1 (>= 0.36.2) but it is not installable
        Depends: libtag1c2 (>= 1.3.1) but it is not installable


---

