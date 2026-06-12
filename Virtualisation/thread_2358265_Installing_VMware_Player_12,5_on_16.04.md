---
title: "Installing VMware Player 12,5 on 16.04"
date: 2017-04-11
forum: Virtualisation
---

### Post by izznogooood on 2017-04-11
I'm trying to install VMware Player on 16.04 and get this error:

[ATTACH=CONFIG]274516[/ATTACH]

But it looks like there is a version of gcc-6 installed on 16.04

```
anders@yoga:~$ gcc --versiongcc (Ubuntu 5.4.0-6ubuntu1~16.04.4) 5.4.0 20160609
Copyright (C) 2015 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


anders@yoga:~$ gcc
gcc           gcc-5         gcc-ar        gcc-ar-5      gcc-nm        gcc-nm-5      gcc-ranlib    gcc-ranlib-5
anders@yoga:~$ sudo apt search gcc-6-base
[sudo] password for anders: 
Sorting... Done
Full Text Search... Done
gcc-6-base/xenial,now 6.0.1-0ubuntu1 amd64 [installed]
  GCC, the GNU Compiler Collection (base package)



```

What am I missing?

---

### Post by sp40140 on 2017-04-11
Which VMWare product/version are you trying to install? Did you get the ".bundle" file from their site? What are your hardware specs?

---

### Post by izznogooood on 2017-04-11
I got the bundle from their site (12,5) and ran the file. No warnings there.

I have a newer laptop with HWE enabled and a 4.10.9 kernel on top of that. (Necessary for my hardware).
Its an i7-7500u (Lenovo 710 yoga)

I remeber I solved this before, but not how...

---

### Post by izznogooood on 2017-04-12
Turns out there's no gcc-6 on ubuntu 16.04. It is available through this ppa though:

```
[COLOR=#111111][FONT=Consolas]sudo add-apt-repository ppa:ubuntu-toolchain-r/test
[/FONT][/COLOR]sudo apt update 
[COLOR=#111111][FONT=Consolas]sudo apt install gcc-6[/FONT][/COLOR]
```

I noticed that this PPA also updates:

```
20 packages can be upgraded. Run 'apt list --upgradable' to see them.Listing... Done
cpp-5/xenial 5.4.1-2ubuntu1~16.04 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.4]
g++-5/xenial 5.4.1-2ubuntu1~16.04 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.4]
gcc-5/xenial 5.4.1-2ubuntu1~16.04 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.4]
gcc-5-base/xenial 5.4.1-2ubuntu1~16.04 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.4]
gcc-6-base/xenial 6.2.0-3ubuntu11~16.04 amd64 [upgradable from: 6.0.1-0ubuntu1]
libasan2/xenial 5.4.1-2ubuntu1~16.04 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.4]
libatomic1/xenial 6.2.0-3ubuntu11~16.04 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.4]
libcc1-0/xenial 6.2.0-3ubuntu11~16.04 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.4]
libcilkrts5/xenial 6.2.0-3ubuntu11~16.04 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.4]
libgcc-5-dev/xenial 5.4.1-2ubuntu1~16.04 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.4]
libgcc1/xenial 1:6.2.0-3ubuntu11~16.04 amd64 [upgradable from: 1:6.0.1-0ubuntu1]
libgomp1/xenial 6.2.0-3ubuntu11~16.04 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.4]
libitm1/xenial 6.2.0-3ubuntu11~16.04 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.4]
liblsan0/xenial 6.2.0-3ubuntu11~16.04 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.4]
libmpx0/xenial 5.4.1-2ubuntu1~16.04 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.4]
libquadmath0/xenial 6.2.0-3ubuntu11~16.04 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.4]
libstdc++-5-dev/xenial 5.4.1-2ubuntu1~16.04 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.4]
libstdc++6/xenial 6.2.0-3ubuntu11~16.04 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.4]
libtsan0/xenial 6.2.0-3ubuntu11~16.04 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.4]
libubsan0/xenial 6.2.0-3ubuntu11~16.04 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.4]



```

However /usr/bin/gcc still stays linked to 5.2, and thats a good thing. I dont compile a whole lot so I dont expect problems with all the other updates but would be a thing to consider if you do.

Now just point VMware to /usr/bin/gcc-6 and it will fail once, go again and you're all set.

---

