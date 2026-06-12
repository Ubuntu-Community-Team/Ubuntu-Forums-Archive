---
title: "Problem upgrading to 1.3.x"
date: 2010-11-16
forum: Wine
---

### Post by Calcipher on 2010-11-16
I am attempting to upgrading to the wine 1.3.x branch, but I keep running into a problem with the ia32-libs package that is in the wine repos.  When upgrading, I get the following:
```
The following packages will be upgraded:
  ia32-libs
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
Need to get 0B/58.3MB of archives.
After this operation, 62.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 280811 files and directories currently installed.)
Preparing to replace ia32-libs 20090808ubuntu9 (using .../ia32-libs_20090808ubuntu10~wineppa1_amd64.deb) ...
Unpacking replacement ia32-libs ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_20090808ubuntu10~wineppa1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib32/libpanelw.so.5.7', which is also in package lib32ncursesw5 5.7+20100626-0ubuntu1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for libglib2.0-0 ...
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_20090808ubuntu10~wineppa1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Does anyone have any ideas of how to resolve this?  The guys in the Wine Forums suggested that I try here as it is an Ubuntu package that is having issues updating.

---

### Post by doctorzeus on 2010-11-16
> **Calcipher said:**
> I am attempting to upgrading to the wine 1.3.x branch, but I keep running into a problem with the ia32-libs package that is in the wine repos.  When upgrading, I get the following:
```
The following packages will be upgraded:
  ia32-libs
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
Need to get 0B/58.3MB of archives.
After this operation, 62.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 280811 files and directories currently installed.)
Preparing to replace ia32-libs 20090808ubuntu9 (using .../ia32-libs_20090808ubuntu10~wineppa1_amd64.deb) ...
Unpacking replacement ia32-libs ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_20090808ubuntu10~wineppa1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib32/libpanelw.so.5.7', which is also in package lib32ncursesw5 5.7+20100626-0ubuntu1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for libglib2.0-0 ...
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_20090808ubuntu10~wineppa1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Does anyone have any ideas of how to resolve this?  The guys in the Wine Forums suggested that I try here as it is an Ubuntu package that is having issues updating.

Try compleatly removing wine (wont remove your .wine dir):

```

sudo apt-get remove wine --purge

```

then try re-installing it:

```
sudo apt-get install wine
```

Hope this helps

Doctorzeus

---

### Post by Calcipher on 2010-11-16
Thanks I tried that, but it doesn't fix the ia32-libs issue.

---

### Post by turtle153 on 2011-02-15
Perhaps its a bit late, but running 
```

sudo apt-get -f install

```
should clear up your package pains.

---

### Post by pw1 on 2011-02-15
> **turtle153 said:**
> 
```

sudo apt-get -f install

```

Thank you :D. I had the same problem. Running this command solved it for me.

---

