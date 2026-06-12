---
title: "VirtualBox 3.1.4 cannot get from anywhere"
date: 2010-03-08
forum: Virtualisation
---

### Post by toogooda on 2010-03-08
Repository has not been working for some time and there deb download link cuts out part way.
Anyone know how to get repository to work again or where the file can be downloaded successfuly from?

```

sudo apt-get update
...
99% [5 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting f
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://download.virtualbox.org karmic/non-free Packages                    
  Sub-process /bin/bzip2 returned an error code (2)
...
W: GPG error: http://download.virtualbox.org karmic Release: The following signatures were invalid: BADSIG DCF9F87B6DFBCBAE Sun Microsystems, Inc. (xVM VirtualBox archive signing key) <info@virtualbox.org>
W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/karmic/non-free/binary-amd64/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

VirtualBox Forums just say it is a Ubuntu issue but it only started recently.

Can anyone help me please?

---

### Post by kiranmurari on 2010-03-08
Hi,

I was able to download and install VirtualBox 3.1.4 for Ubuntu 9.10 Please try the deb file from the following link. [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

First to start with a clean system, run the following commands:
Remove all packages that are not being used.
```
$ sudo apt-get autoremove
```Remove any broken VirtualBox installation.
```
$ sudo dpkg -P virtualbox-3.1
```Before you install VirtualBox 3.1.4, you need to install the dependencies.
```
$ sudo apt-get install libqtgui4 libqtcore4 libqt4-network libqt4-opengl
```Now install VirtualBox, using the .deb file downloaded from VirtualBox website.
```
$ sudo dpkg -i virtualbox-3.1_3.1.4-57640_Ubuntu_karmic_i386.deb
```Hope this helps.

---

### Post by toogooda on 2010-03-10
Trying again now but the AMD64 version only gets part way (3 or 4 mb) then thinks its finished? I might have just got the server on a bad night. Will let you know if it works this time.

Has anyone with Ubuntu 9.10 64bit managed to get it using the repository?

Cheers,

Andrew T

---

### Post by toogooda on 2010-03-10
Failed again is there a mirror, I have downloaded 100's of mb in updates without issue so don't know why this on always fails. has anyone managed to download the 64bit version?

---

### Post by speedy1979 on 2010-03-10
> **toogooda said:**
> Failed again is there a mirror, I have downloaded 100's of mb in updates without issue so don't know why this on always fails. has anyone managed to download the 64bit version?

There seems to have been an issue with virtualbox's servers try downloading the .deb from here:
 
[http://download.virtualbox.org/virtualbox/vboxdownload.html#linux](http://download.virtualbox.org/virtualbox/vboxdownload.html#linux)

---

### Post by toogooda on 2010-03-10
That worked thanks, I hope the repositories are working again soon!

---

