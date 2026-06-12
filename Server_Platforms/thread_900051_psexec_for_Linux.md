---
title: "psexec for Linux"
date: 2008-08-24
forum: Server Platforms
---

### Post by promodus on 2008-08-24
After some trial & error I've gotten winexec to work on Linux. 
This is identical to the psexec version by sysinternals.

[http://eol.ovh.org/winexe/](http://eol.ovh.org/winexe/)

[http://eol.ovh.org/winexe/winexe-source-071026.tar.bz2](http://eol.ovh.org/winexe/winexe-source-071026.tar.bz2)

uncompress, then
```
./autogen.sh
./configure
make proto bin/winexe
```


Then for example, I have a VM with the netbios name vm-xptesting:
```
./winexe  -U "admin" //vm-xptesting 'cmd.exe'
Password for [WORKGROUP\admin]:
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\WINDOWS\system32>
```

Lastly do not forget to turn off simple file sharing on your windows machines.

---

### Post by zcubed on 2008-08-25
I have been trying to get winexe to work for a couple of weeks also.  psexec is a great tool if you have to support very many windows machines.

I had to run:
```
sudo apt-get install autoconf
sudo apt-get install automake 
```

 to get your code to go.

I also had to use "-U "domain\user" to get it to run under my account.

AND It works!  Thanks!

> C:\WINDOWS\system32>defrag c:
defrag c:
Windows Disk Defragmenter
Copyright (c) 2001 Microsoft Corp. and Executive Software International, Inc.

Analysis Report                   	 
    71.22 GB Total,  57.98 GB (81%) Free,  7% Fragmented (14% file fragmentation)

---

### Post by promodus on 2008-08-26
Revised install procedure:
```

sudo apt-get install build-essential automake autoconf 
sudo apt-get install auto-apt checkinstall

cd /usr/src
wget http://eol.ovh.org/winexe/winexe-source-071026.tar.bz2
tar xvjf winexe-source-071026.tar.bz2
cd winexe-source-071026
sh autogen.sh
auto-apt run ./configure
make proto bin/winexe
sudo checkinstall -D cp bin/winexe /usr/local/sbin/.
```

---

### Post by shamil.si on 2008-09-10
There is a simple way to install winexe on Ubuntu/Debian:

```
sudo apt-get install wmi-client
```

Then you have winexe and wmic (wmi query utility) installed and ready to use.

---

### Post by promodus on 2008-09-10
Awesome, gave you thanks.

---

### Post by c0mputernick on 2008-09-30
> **shamil.si said:**
> There is a simple way to install winexe on Ubuntu/Debian:

```
sudo apt-get install wmi-client
```

Then you have winexe and wmic (wmi query utility) installed and ready to use.


Has anyone tried this across the internet?  Ive been able to get it to work internally on the lan, but i have servers around the internet i need to administer as well and would love to be able to use this in my backup scripts.  any ideas on how to use it? Does it use a special port or something?

---

### Post by yoshco on 2010-03-28
post revivel
cant get it to run, 
```
apt-get install wmi-client
``` gives 
 *Couldn't find package wmi-client*
and if i try 
```
 sh autogen.sh
``` 
i get 
```
autom4te: /usr/bin/m4 failed with exit status: 1
autoheader: '/usr/bin/autom4te' failed with exit status: 1

```

---

### Post by TopQuark_net on 2010-04-09
The wmi-client package has been removed, see [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=523638](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=523638)

In addition, the build scripts in winexe 0.90 don't work with autoconf >2.60

However, Zenoss is maintaining a copy of winexe that has been updated to work with new versions of autoconf.

So, the following worked for me on karmic:

sudo apt-get install build-essential autoconf checkinstall
cd /usr/src
svn co [http://dev.zenoss.org/svn/trunk/wmi/Samba/source](http://dev.zenoss.org/svn/trunk/wmi/Samba/source)
mv source winexe-source-2010.04.09
cd winexe-source-2010.04.09
./autogen.sh
./configure
make proto bin/winexe
sudo checkinstall -D cp bin/winexe /usr/local/bin/.

---

### Post by MSPdwalt on 2010-05-12
So is there a way to get winexe in a package for Lucid? or do we have to manually install it?

---

### Post by Phkillah on 2010-08-04
> **MSPdwalt said:**
> So is there a way to get winexe in a package for Lucid? or do we have to manually install it?

The manual method one post before yours worked for me. @10.04

---

### Post by angus73 on 2010-09-06
The method mentioned by Phkillah also worked for me on Lucid 64bit

Thank you very much!
A.

---

### Post by ulrichard on 2011-07-28
You can install it from one of these two ppa's:

[https://launchpad.net/~richi-paraeasy/+archive/ppa/+packages](https://launchpad.net/~richi-paraeasy/+archive/ppa/+packages)
[https://launchpad.net/~jdthood/+archive/winexe/+packages](https://launchpad.net/~jdthood/+archive/winexe/+packages)

Let me know if it works as I'm only getting errors from the Win7_64 box.

Rgds
Richard

---

### Post by jdthood on 2011-08-09
This PPA:

    [https://launchpad.net/~richi-paraeasy/+archive/ppa/+packages](https://launchpad.net/~richi-paraeasy/+archive/ppa/+packages)

contains a package identified as version "1.0.3a".  However, the latest release of winexe has version number "1.00".  The package in the above archive contains a winexe binary that identifies itself as version "0.80".

Winexe 1.00 is built by the openSUSE build service:

    [https://build.opensuse.org/package/show?package=winexe&project=home%3Aahajda%3Awinexe](https://build.opensuse.org/package/show?package=winexe&project=home%3Aahajda%3Awinexe)

Before I discovered this I made winexe 1.00 available in my own PPA:

    [https://launchpad.net/~jdthood/+archive/winexe/+packages](https://launchpad.net/~jdthood/+archive/winexe/+packages)

-- 
Thomas Hood

---

