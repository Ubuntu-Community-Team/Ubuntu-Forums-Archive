---
title: "Chandler on Ubuntu"
date: 2006-01-19
forum: The Cafe
---

### Post by macewan on 2006-01-19
First we’ll snatch a copy of Chandler, it’s an rpm so grab a copy of alien if it isn’t already on your box ( sudo apt-get install alien ). Then we’ll convert to a .deb, then dpkg install, change directories & run the program. Finally we post a screenshot [IMG]http://www.macewan.org/wp-images/smilies/icon_smile.gif[/IMG]  this step is optional.
**macewan@cornbread:~$** wget \
[http://downloads.osafoundation.org/chandler/releases/0](http://downloads.osafoundation.org/chandler/releases/0) .6/Chandler_linux_0.6.i386.rpm
 
 –18:46:46–  [http://downloads.osafoundation.org/chandler/releases/0.6/Chandler_](http://downloads.osafoundation.org/chandler/releases/0.6/Chandler_) linux_0.6.i386.rpm
           => `Chandler_linux_0.6.i386.rpm’
Resolving downloads.osafoundation.org… 204.152.186.97
Connecting to downloads.osafoundation.org|204.152.186.97|:80… connected.
HTTP request sent, awaiting response… 200 OK
Length: 24,534,457 (23M) [application/x-rpm]

100%[===================>] 24,534,457    36.87K/s    ETA 00:00

18:59:28 (31.43 KB/s) - `Chandler_linux_0.6.i386.rpm’ saved [24534457/24534457]

**macewan@cornbread:~$** sudo alien -d Chandler_linux_0.6.i386.rpm
**macewan@cornbread:~$** cd /usr/local/chandler
**macewan@cornbread:~$** ./chandler

---

### Post by mike998 on 2006-01-19
For those who are curious (as I was) and don't know what Chandler is (which I didn't) - it's a PIM (Personal Information Manager).

More info [here]("http://wiki.osafoundation.org/bin/view/Projects/ChandlerHome")

---

### Post by UbuWu on 2006-01-19
It looks very promising, but is slow as hell and a little bit buggy. I am looking forward to the 1.0 release.

---

### Post by ast3risk on 2006-05-10
anybody got this thing to work with ppc? looks like its not supported:

dpkg-shlibdeps: failure: ldd on `debian/chandler/usr/local/chandler/release/bin/ python' gave error exit status 1
dh_shlibdeps: command returned error code 256
make: [binary-arch] Error 1 (ignored)
dh_gencontrol
dpkg-gencontrol: error: current build architecture powerpc does not appear in pa ckage's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1

---

### Post by ast3risk on 2006-05-10
tried a make install thinking it might do something (revealing my noobism) and got:

/home/elliottw/chandler/release/RunPython: line 42: /home/elliottw/chandler/release/bin/python: cannot execute binary file
/home/elliottw/chandler/release/RunPython: line 42: /home/elliottw/chandler/release/bin/python: Success
make: *** [/home/elliottw/chandler/release/setuptools-0.6a11-py2.4.egg.inst] Error 1

---

### Post by Tom^ on 2006-05-16
I've been checking out the osafoundation's chandler page every once in a while since 0.1 when I first saw a piece of news about it. I forgot it for a while and it's really great to see that they are making progress. Like UbuWu said, can't wait for the 1.0 release.

---

### Post by Tom^ on 2006-05-16
I've been checking out the osafoundation's chandler page every once in a while since 0.1 when I first saw a piece of news about it. I forgot it for a while and it's really great to see that they are making progress. Like UbuWu said, can't wait for the 1.0 release.

---

### Post by isotonic on 2006-06-04
.

---

