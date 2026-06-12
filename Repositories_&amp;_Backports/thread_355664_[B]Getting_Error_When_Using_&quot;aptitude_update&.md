---
title: "[B]Getting Error When Using &quot;aptitude update&quot;[/B]"
date: 2007-02-07
forum: Repositories &amp; Backports
---

### Post by magichsjx on 2007-02-07
[B]Hello
I hope this is the right place to post. I have been trying to get a sources.liset that I can us e and I used the one from psychocats.com but the update command fails giving this error[/B]

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources [57.5kB]
99% [12 Sources gzip 0]                                              54.9kB/s 0sgzip: stdin: not in gzip format
[B]Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
  Sub-process gzip returned an error code (1)[/B]
Fetched 12B in 6s (2B/s)
Reading package lists... Done

[B]I got this message when I ran "aptitude update" and I was going to run "aptitude instal" next. I do not know if I should proceed or is there something to fix this error. is it related to my sources.list or not. Just in case I am pasting my sources.list here too. Thank you in advance.

I am on Ubuntu Dapper 6.0.6 LTS.

/etc/apt/ources.list:[/B]

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main 
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

#AUTOMATIX REPOS START

deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./

deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
#AUTOMATIX REPOS END

**Thank you for any help or suggestions. I get a lot of error message installing using Automatix which I have installed as well not sure if that has to do with the repositories but usually some error occurs.**

---

### Post by jackrobinson on 2007-02-07
make your /etc/apt/sources.list look as follows:
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main 

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
#AUTOMATIX REPOS START

deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./

deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

#AUTOMATIX REPOS END

save the file and do
```
sudo apt-get update
```

---

### Post by magichsjx on 2007-02-07
[B]TY for responding
Ihave done as you said but still get 99% done and then the following error:

blah blah blah.....
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources [57.5kB]
99% [Working]                                                       16.9kB/s 0s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
  Sub-process gzip returned an error code (1)
Fetched 10B in 8s (1B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

What is the gzip: stdin

The error seems to come from the sources.gz in multiverse

TY again. If anything else I can do I would love to know.[/B]

---

### Post by jackrobinson on 2007-02-07
change the following lines in /etc/apt/sources.list:
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
to
> deb [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
save the file and exit and do
```
sudo apt-get update
```

---

### Post by magichsjx on 2007-02-08
TY very much. I made the change and I do not get any errors during the apt-get update. As you know this was a gzip error. Now I went to unbundle a download manager which I had gotten from the internet the gwget download manager and the command
> tar xvfz install gwget-0.98.2.tar.gz
to install it. But it failed also. Is there a cure. TY for your help.
the output is:
> gwget-0.98.2/
gwget-0.98.2/po/
gwget-0.98.2/po/ChangeLog
gwget-0.98.2/po/Makefile.in.in
gwget-0.98.2/po/POTFILES.in
gwget-0.98.2/po/ar.po
gwget-0.98.2/po/bg.po
gwget-0.98.2/po/ca.po
gwget-0.98.2/po/cs.po
gwget-0.98.2/po/da.po
gwget-0.98.2/po/de.po
gwget-0.98.2/po/el.po
gwget-0.98.2/po/en_CA.po
gwget-0.98.2/po/en_GB.po
gwget-0.98.2/po/es.po
gwget-0.98.2/po/eu.po
gwget-0.98.2/po/fi.po
gwget-0.98.2/po/fr.po
gwget-0.98.2/po/hu.po
gwget-0.98.2/po/it.po
gwget-0.98.2/po/ja.po
gwget-0.98.2/po/lt.po
gwget-0.98.2/po/mk.po
gwget-0.98.2/po/ne.po
gwget-0.98.2/po/nl.po
gwget-0.98.2/po/pa.po
gwget-0.98.2/po/pl.po
gwget-0.98.2/po/pt.po
gwget-0.98.2/po/pt_BR.po
gwget-0.98.2/po/ro.po
gwget-0.98.2/po/ru.po
gwget-0.98.2/po/rw.po
gwget-0.98.2/po/sk.po
gwget-0.98.2/po/sq.po
gwget-0.98.2/po/sv.po
gwget-0.98.2/po/tr.po
gwget-0.98.2/po/uk.po
gwget-0.98.2/po/vi.po
gwget-0.98.2/po/zh_CN.po
gwget-0.98.2/po/zh_HK.po
gwget-0.98.2/po/zh_TW.po
gwget-0.98.2/README
gwget-0.98.2/Makefile.in
gwget-0.98.2/configure
gwget-0.98.2/AUTHORS
gwget-0.98.2/COPYING
gwget-0.98.2/ChangeLog
gwget-0.98.2/INSTALL
gwget-0.98.2/Makefile.am
gwget-0.98.2/NEWS
gwget-0.98.2/THANKS
gwget-0.98.2/TODO
gwget-0.98.2/aclocal.m4
gwget-0.98.2/config.guess
gwget-0.98.2/config.h.in
gwget-0.98.2/config.sub
gwget-0.98.2/configure.in
gwget-0.98.2/depcomp
gwget-0.98.2/gwget.desktop.in
gwget-0.98.2/install-sh
gwget-0.98.2/ltmain.sh
gwget-0.98.2/missing

gzip: stdin: unexpected end of file
gwget-0.98.2/mkinstalldirs
gwget-0.98.2/intltool-extract.in
gwget-0.98.2/intltool-merge.in
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

that is not the error i get with .tar.bz2 files. I do not know the difference but one works, the other does not. TY in advance.

---

### Post by jackrobinson on 2007-02-08
It was not a gzip error per se. The issue was with the repositories. 
The command you are using is wrong as well.
To untar a tar.gz archive you need to use:
```
tar xvzf package_name.tar.gz
```
To untar a bzip2 archive you need to do:
```
tar xvjf package_name.tar.bz2
```

---

### Post by magichsjx on 2007-02-09
[B]TY very much for the correction. I had tried to use the package manager which did not work either but i will use the new commands. BTW is it important where one saves a file such as java runtime for instance or other bundled software or any software will it work as good?

And once I run these two commands theoutput has to be installed using ./config and make and make install or i would prefer checkinstall -D if that is an option in the case of .tar.bz2 In the case of the other i think its just ./packagename if i am correct. ty for getting back anyhow.:) [/B]

---

