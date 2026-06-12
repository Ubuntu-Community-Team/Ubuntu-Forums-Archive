---
title: "64 Bit Wine on Ubuntu"
date: 2011-04-04
forum: Wine
---

### Post by BZAnathema on 2011-04-04
Okay, I'm running Ubuntu 10.04 on an x86 64-bit system. I went to install wine, and it said I was missing the following: ia32-libs, lib32asound2, libc6-i386, and lib32nss-mdns. I suspect all the 32s mean it's trying to install a 32-bit version of wine and doesn't have the libraries, but I need 64-bit. Any links or tutorials that I can get a 64-bit version from? Note: I really don't care what version, as long as it's 1.0 or later.

---

### Post by Quadunit404 on 2011-04-04
Standard Wine is 32-bit. You can compile a 64-bit Wine using the --enable-win64 flag during the configure process, which compiles Wine as 64-bit and has Win64 support, but Win64 compatibility is very poor and even the Wine devs say you should install 32-bit Wine from the Wine PPA.

You can read about it here: [http://wiki.winehq.org/WineOn64bit]("http://wiki.winehq.org/WineOn64bit")

---

### Post by BZAnathema on 2011-04-04
I tried getting build files, but it still yelled about not being able to install 32-bit libs. Is there a repository I need to enable? Was it on the page and I just missed it? If the latter, just mentally smack me and tell me to go read again.

---

### Post by Quadunit404 on 2011-04-04
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```

Run that in a Terminal. Then run:

```
sudo apt-get update
```

to refresh the repository listings. Then you should be able to install Wine and all its dependencies in the Ubuntu Software Center or Synaptic (your choice, really)

---

### Post by BZAnathema on 2011-04-04
It gave me the same error, both cmdline and Synaptic:
```

 wine1.2:
 Depends: ia32-libs but it is not going to be installed
 Depends: lib32asound2 but it is not going to be installed
 Depends: libc6-i386 but it is not going to be installed
 Depends: lib32nss-mdns but it is not going to be installed
 Recommends: winbind but it is not going to be installed
```I tried just installing the "wine" dummy package, but it depended on wine1.2. wine1.3 gave me the same error, as did wine1.0. Should a try a -dev or -gecko package?

---

### Post by cwwilson721 on 2011-04-04
Easiest way is to go to the Software Center, and just install wine (ver 1.2).

You can add the PPA for wine 1.3, and it will update to latest, too.

Search google for "ubuntu wine 1.3 PPA". You'll get good directions.

---

### Post by BZAnathema on 2011-04-04
cw, it can't find anything with the package name of "wine1.2." It's all dev or gecko packages. When I install the dummy package it suggests, it complains that it depends on wine1.2, which is basically the same issue I was just having.

---

### Post by BZAnathema on 2011-04-04
Also - I tried to install the build prereqs, but it again wanted to install 32-bit stuff and yelled at me. What am I doing wrong?

---

### Post by BZAnathema on 2011-04-05
I upgraded to 10.10, and I can now install directly from the command line. Either it was a 10.04 problem, or more likely, I screwed something up on 10.04. Thanks for the help!

---

