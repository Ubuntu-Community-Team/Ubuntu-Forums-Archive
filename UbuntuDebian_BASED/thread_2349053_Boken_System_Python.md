---
title: "Boken System Python"
date: 2017-01-10
forum: Ubuntu/Debian BASED
---

### Post by Tyler_Roesler on 2017-01-10
*Disclaimer: I am using Elementary OS Freya. but I figured this would be a safe place to post considering it has an Ubuntu 16.04 LTS backend

I broke the heck out of my system python. I have spent hours googling and experimenting trying to come up with solutions and only managed to break python on my system more and more. I'll try to backtrack as best I can...

I pulled an oopsie and installed Python 3.5 (from source) and did not make altinstall (or whatever it is so that it safely installs next to the system python2.7. This made my system all screwy, and I kept getting errors, which I tracked down to this error.

Problem being, Python3.5 doesn't include a make uninstall command, so after searching around I read that I should just delete everything Python3.5 installed on my system. So I decided it would be a good idea (out of despiration) to execute this command (found here: [http://askubuntu.com/questions/18369/how-to-delete-all-files-that-are-returned-by-locate):](http://askubuntu.com/questions/18369/how-to-delete-all-files-that-are-returned-by-locate):)
```
locate python3 | xargs -ixxx rm -rf 'xxx'
```

This was a bad idea. Now I'm getting python errors all over the place:
(relevant) output from sudo apt-get upgrade;
```

dpkg: error processing package dh-python (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
Setting up software-center-aptdaemon-plugins (0.1.6build1) ...
/var/lib/dpkg/info/software-center-aptdaemon-plugins.postinst: 13: /var/lib/dpkg/info/software-center-aptdaemon-plugins.postinst: py3compile: not found
dpkg: error processing package software-center-aptdaemon-plugins (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 dh-python
 software-center-aptdaemon-plugins
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

output from sudo apt-get install --reinstall dh-python (trying to fix that problem)
```

dpkg: warning: files list file for package 'python3-cryptography' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3.5' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpython3-stdlib:amd64' missing; assuming package has no files currently installed
...

```

That goes on for a while... then:
```

Preparing to unpack .../dh-python_2.20151103ubuntu1.1_all.deb ...
/var/lib/dpkg/info/dh-python.prerm: 6: /var/lib/dpkg/info/dh-python.prerm: py3clean: not found
dpkg: warning: subprocess old pre-removal script returned error exit status 127
dpkg: trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: /var/lib/dpkg/tmp.ci/prerm: py3clean: not found
dpkg: error processing archive /var/cache/apt/archives/dh-python_2.20151103ubuntu1.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/dh-python.postinst: 6: /var/lib/dpkg/info/dh-python.postinst: py3compile: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/dh-python_2.20151103ubuntu1.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

even for other programs...
gdb output:
```

gdb: error while loading shared libraries: libpython3.5m.so.1.0: cannot open shared object file: No such file or directory

```

and similar errors for others.

weirdly enough, however, running python opens:
```

Python 2.7.12 (default, Nov 19 2016, 06:48:10) 
[GCC 5.4.0 20160609] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 

```
and python --version returns 2.7.12

I'm at a loss. I can't find anything that can help me at this point. I'm trying to avoid a complete wipe and reinstall, but that might be my only option at this point. Any and all help would be GREATLY appreciated.

---

### Post by coffeecat on 2017-01-10
> **Tyler_Roesler said:**
> *Disclaimer: I am using Elementary OS Freya. but I figured this would be a safe place to post considering it has an Ubuntu 16.04 LTS backend

No. You posted in New to Ubuntu which is in the *Ubuntu Official Flavours Support* section which has the tagline:

> Choose the most appropriate category for your questions regarding Ubuntu, Kubuntu, Xubuntu, Edubuntu, Lubuntu, UbuntuGnome, Ubuntu Studio, Mythbuntu, Ubuntu Mate, and Ubuntu Kylin.

Elementary OS is just one of 60+ 3rd party derivatives of Ubuntu which are **not** one of the official flavours.

*Thread moved to **Ubuntu/Debian BASED**.*

---

