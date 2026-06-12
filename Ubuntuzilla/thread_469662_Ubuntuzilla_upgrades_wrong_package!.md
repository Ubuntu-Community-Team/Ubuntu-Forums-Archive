---
title: "Ubuntuzilla upgrades wrong package!"
date: 2007-06-10
forum: Ubuntuzilla
---

### Post by parsival on 2007-06-10
Hi Ubuntuzilla users,

6.06 Dapper  -- kubuntu with firefox 2.0.0.3 installed 
and R 2.5.0 (this is a statistical programming language, nothing to do with firefox etc)

Ubuntuzilla detected the new  firefox  (2.0.0.4) 

but later on told me that "firefox is already the newest version" 
and then tried to update my installation of R (which is already the latest version,
installed last night). I aborted the script, as i didnt want it messing with R.

an edited output follows. Seems weird to me.

Bye
Parsival



here is the command
$python work/ubuntuzilla_4.0.1.py  -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.0.1

This script installs the latest release of the official Mozilla build
of Firefox on Ubuntu Linux.
The most recent release of Firefox is detected to be 2.0.0.4.
.
.
.
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Err [http://CRAN.R-project.org](http://CRAN.R-project.org) dapper/ Release.gpg
  Could not connect to CRAN.R-project.org:80 (137.208.57.37), connection timed out
Fetched 5B in 2m0s (0B/s)
Failed to fetch [http://CRAN.R-project.org/bin/linux/ubuntu/dapper/Release.gpg](http://CRAN.R-project.org/bin/linux/ubuntu/dapper/Release.gpg)  Could not connect to CRAN.R-project.org:80 (137.208.57.37), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree... Done
firefox is already the newest version.
.
.
.
Setting up r-base-core (2.5.0-2dapper0) ...

Configuration file `/etc/R/Renviron'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ? Your options are:

---

### Post by nanotube on 2007-06-10
hi
well... the script does nothing at all about R specifically (btw, a great software - i use it too! :) ).

the script attemts to make sure that firefox from the repositories is updated, prior to installing the mozilla build of it alongside it (that's when it said firefox is already the newest version - that doesn't mean that it won't install the mozilla build later). it also makes sure that libstdc++5, libgtk2 are installed - since these dependencies are required for the mozilla build. it doesn't do anything with R. 

all that output you pasted is part of apt-get, so my only guess is that when you were setting up R earlier, it did not finish setting up, so when the script ran apt-get, apt-get decided to finish installing R as well (that's what a package manager will do for you...)

so, just run the script again, and let apt-get do it's thing. :)

---

### Post by parsival on 2007-06-11
Hi nanotube,

thanks, I guess I just got a bit nervous when I saw all those R messages going by.



I tried it again and this time it left R alone.
All went well until

gpg: WARNING: unsafe ownership on configuration file `/home/robd/.gnupg/gpg.conf'
gpg: WARNING: unsafe ownership on configuration file `/home/robd/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
Unable to retrieve Mozilla Software Releases Public key from pgp.mit.edu . Trying again...
Failed to retrieve Mozilla Software Releases Public key from any of the listed keyservers. Please check your network connection, and try again later.


I tried changing the ownership of gpg.conf to root -- it just changed the error message to 
gpg: WARNING: unsafe enclosing directory ownership on configuration file `/home/robd/.gnupg/gpg.conf'

so I tried
sudo python work/ubuntuzilla_4.0.1.py --skipgpg -a install -p firefox     

which bombed out with

9:15:11 (0.00 B/s) - `firefox-2.0.0.4.tar.gz' saved [9655661]

Traceback (most recent call last):
  File "/home/robd/work/ubuntuzilla_4.0.1.py", line 667, in ?
    bs.start()
  File "/home/robd/work/ubuntuzilla_4.0.1.py", line 61, in start
    fi.start()
  File "/home/robd/work/ubuntuzilla_4.0.1.py", line 84, in start
    self.install()
  File "/home/robd/work/ubuntuzilla_4.0.1.py", line 330, in install
    self.extractArchive()
  File "/home/robd/work/ubuntuzilla_4.0.1.py", line 246, in extractArchive
    os.remove(self.sigFilename)
AttributeError: FirefoxInstaller instance has no attribute 'sigFilename'

 

Bye 
Rob

---

### Post by nanotube on 2007-06-11
> **parsival said:**
> Hi nanotube,

thanks, I guess I just got a bit nervous when I saw all those R messages going by.



I tried it again and this time it left R alone.
All went well until

gpg: WARNING: unsafe ownership on configuration file `/home/robd/.gnupg/gpg.conf'
gpg: WARNING: unsafe ownership on configuration file `/home/robd/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
Unable to retrieve Mozilla Software Releases Public key from pgp.mit.edu . Trying again...
Failed to retrieve Mozilla Software Releases Public key from any of the listed keyservers. Please check your network connection, and try again later.


I tried changing the ownership of gpg.conf to root -- it just changed the error message to 
gpg: WARNING: unsafe enclosing directory ownership on configuration file `/home/robd/.gnupg/gpg.conf'

so I tried
sudo python work/ubuntuzilla_4.0.1.py --skipgpg -a install -p firefox     

which bombed out with

9:15:11 (0.00 B/s) - `firefox-2.0.0.4.tar.gz' saved [9655661]

Traceback (most recent call last):
  File "/home/robd/work/ubuntuzilla_4.0.1.py", line 667, in ?
    bs.start()
  File "/home/robd/work/ubuntuzilla_4.0.1.py", line 61, in start
    fi.start()
  File "/home/robd/work/ubuntuzilla_4.0.1.py", line 84, in start
    self.install()
  File "/home/robd/work/ubuntuzilla_4.0.1.py", line 330, in install
    self.extractArchive()
  File "/home/robd/work/ubuntuzilla_4.0.1.py", line 246, in extractArchive
    os.remove(self.sigFilename)
AttributeError: FirefoxInstaller instance has no attribute 'sigFilename'

 

Bye 
Rob

hm, well, about the .gnupg directory, it should be owned by your user, and have permissions of 700. the contents of it should have permissions 600. so, do the following:
```
sudo chown yourusername:yourusername ~/.gnupg
chmod 700 ~/.gnupg
chmod 600 ~/.gnupg/*
```

also, it looks like i haven't implemented the skipgpg option properly (hence your error). i will fix that bug and post a fixed version... in the meantime, just fix your .gnupg permissions, and try running again without the skipgpg option.

edit1: i also noticed that you ran the whole thing with 'sudo', you shouldn't really do that, you should run it with just "python ubuntuzilla.....", and it will ask you for sudo password just for the steps that require it.

edit2: i fixed the skipgpg bug. if getting the gpg key keeps failing (it shouldn't as i just ran the script and it went through fine), you can get the latest version from CVS, which implements the bugfix: [http://pykeylogger.cvs.sourceforge.net/pykeylogger/ubuntuzilla/](http://pykeylogger.cvs.sourceforge.net/pykeylogger/ubuntuzilla/)

edit3: you can also get the latest release (4.0.2) which fixes the skipgpg bug.

---

