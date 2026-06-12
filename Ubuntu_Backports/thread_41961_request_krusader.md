---
title: "request krusader"
date: 2005-06-15
forum: Ubuntu Backports
---

### Post by dlpfmVfH on 2005-06-15
Please upgrade the krusader package, from 1.51 to 1.60.0...

it has some bug fixes and improvements:

homepage: [http://krusader.sourceforge.net/index.php](http://krusader.sourceforge.net/index.php)

changelog: [http://krusader.sourceforge.net/text.php?t=krusader-1.60.0.changelog](http://krusader.sourceforge.net/text.php?t=krusader-1.60.0.changelog)

there's a debian package, on the website, but it won't install on ubuntu cause of the dependencies...

thank you...

---

### Post by Mez on 2005-06-15
[QUOTE=aboe]Please upgrade the krusader package, from 1.51 to 1.60.0...

it has some bug fixes and improvements:

homepage: [http://krusader.sourceforge.net/index.php](http://krusader.sourceforge.net/index.php)

changelog: [http://krusader.sourceforge.net/text.php?t=krusader-1.60.0.changelog](http://krusader.sourceforge.net/text.php?t=krusader-1.60.0.changelog)

there's a debian package, on the website, but it won't install on ubuntu cause of the dependencies...

thank you...[/QUOTE]
 Building for Hoary

---

### Post by dlpfmVfH on 2005-06-15
wow, thanks man... krusader is in my opinion the better filemanager...compared to konqueror or nautilus...

---

### Post by Mez on 2005-06-15
uploaded to staging

---

### Post by dlpfmVfH on 2005-06-15
[QUOTE=Mez]uploaded to staging[/QUOTE]
 wish those mirrors where faster....hihi
oh well just have to wait till they refresh..

---

### Post by dlpfmVfH on 2005-06-16
Just installed it, and it works perfectly...got all the extra programs..installed
no complains so far.... 

starts up fine, wizards work...

---

### Post by Heart on 2005-06-16
[QUOTE=aboe]Just installed it, and it works perfectly...got all the extra programs..installed
no complains so far.... 

starts up fine, wizards work...[/QUOTE]
 didn't see this thread and couldn't wait for 1.60 krusader and downloaded self the source and did ./configure, make, checkinstall

Do I also have these "got all the extra programs" as aboe said or has my self compiled version less "extras" as this package for hoary?

What line do I have to place in my sources.list to get krusader in the last version?

Thanks

---

### Post by dlpfmVfH on 2005-06-16
## UBUNTU BACKPORTS MIRRORS
deb [ftp://ftp2.caliu.info/backports/]("ftp://ftp2.caliu.info/backports/") hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/]("ftp://ftp2.caliu.info/backports/") hoary-extras main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/]("ftp://ftp2.caliu.info/backports/") hoary-backports-staging main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/]("ftp://ftp2.caliu.info/backports/") hoary-extras-staging main universe multiverse restricted

are the lines I use...

the extra packages,, are programs that krusader uses...you got to find them with synaptic, and the list in krusader...
except for krename...couldn't find that one..in the repositories..but did a google on krename and ubuntu..and found one... [http://www.youmortals.com/stuff/ubuntu/krename/]("http://www.youmortals.com/stuff/ubuntu/krename/")

hope this helps

---

### Post by xerus on 2005-06-18
I tried to update krusader using the same backports mirrors than yours.
But it failed : it depends from kdelibs4 (>=4:3.4.1) but synaptic could not find it (I have kdelibs4 4:3.4.0)

---

### Post by Mez on 2005-06-18
fixing...

---

### Post by Mez on 2005-06-18
[QUOTE=xerus]I tried to update krusader using the same backports mirrors than yours.
But it failed : it depends from kdelibs4 (>=4:3.4.1) but synaptic could not find it (I have kdelibs4 4:3.4.0)[/QUOTE]
 Fixed and uploaded to staging

---

### Post by xerus on 2005-06-19
[QUOTE=Mez]Fixed and uploaded to staging[/QUOTE]
 Thanks ! 
It works now.

---

### Post by fisty on 2006-06-14
Please upgrade the krusader package, from 1.60 to 1.70.
there's mamy changes (for good) in this version.

homepage: [http://krusader.sourceforge.net/index.php](http://krusader.sourceforge.net/index.php)

changelog: [http://krusader.sourceforge.net/text.php?t=krusader-1.70.0.changelog](http://krusader.sourceforge.net/text.php?t=krusader-1.70.0.changelog)

there's a ubuntu package, on the website: [http://prdownloads.sourceforge.net/krusader/krusader_1.70.0-1dapper0_i386.deb?download](http://prdownloads.sourceforge.net/krusader/krusader_1.70.0-1dapper0_i386.deb?download)

thank you

---

### Post by rickympl on 2006-06-19
I also would like to see a "working" krusader deb file and possibly a repo. I say "working" because the deb file found on the krusader page, which they say is for ubuntu, is poorly done, mainly because of the way ubuntu uses the sudo,gksudo, etc instead of using  root. This is being talked about in the krusader [http://krusader.sourceforge.net/phpBB/viewtopic.php?t=1512&postdays=0&postorder=asc&highlight=mime&start=0]("http://krusader.sourceforge.net/phpBB/viewtopic.php?t=1512&postdays=0&postorder=asc&highlight=mime&start=0")

Thank you

---

