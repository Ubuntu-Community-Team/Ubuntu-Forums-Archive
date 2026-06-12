---
title: "HP Insight Manager"
date: 2008-10-25
forum: Server Platforms
---

### Post by bluman on 2008-10-25
Hi there,

Is anyone using HP (Compaq) Insight Manager on Ubuntu server? I want to be able to monitor a Compaq DL360 G1 (P3 1Gb RAM) RAID 1 Compaq Smart array running Ubuntu 804.

I've searched the HP website and don't see anything useful for Ubuntu. There is nothing in the main repo's either.

Could anyone who has or is still using it please let me know where they downloaded it from?

Cheers!

---

### Post by cariboo on 2008-10-25
You download it directly from HP, I'm downloading it right now. The download is a .bin file so it will have to be installed manually. Assuming you downloaded it to your desktop in a terminal type:

```
cd ~/Desktop
```

to change to the Destop directory

```
chmod +x *bin
```

to make the .bin file executable

```
sudo ./*bin
```

This assumes you don't have more then one .bin file on your desktop.

Usually the executeable gets installed in either /usr/bin or /usr/local/bin.

Once my download finishes, I will report back if there are any changes.

Edit: It seems you also need Postgresql intalled

Jim

---

### Post by oriswolfbane on 2009-06-05
Do you happen to have the link?
PM please.

---

### Post by davim on 2009-11-11
try this:
[http://h18013.www1.hp.com/products/servers/management/hpsim/index.html?jumpid=go/hpsim](http://h18013.www1.hp.com/products/servers/management/hpsim/index.html?jumpid=go/hpsim)

I've downloaded the bin installer but when I try to install it says that my Linux Distribution isn't supported...

Did anyone managed to get this working?

EDIT: I've also tried the debs for debian 4 ( [http://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1257939644556+28353475&threadId=1046050](http://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1257939644556+28353475&threadId=1046050) ) but they wont install

"Unpacking hpasm (from hpasm-7.8.0-100.etch26.i386.deb) ...
===========================================================
NOTE: The storage agents that come packaged with the
      hpasm application you are installing, require
      the libstdc++2.10-glibc2.2 package in order for
      them to run successfully. Please use the apt-get
      utility to download the package.
      For example: apt-get install libstdc++2.10-glibc2.2
===========================================================
dpkg: error processing hpasm-7.8.0-100.etch26.i386.deb (--install):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 hpasm-7.8.0-100.etch26.i386.deb"

The oldest version of libstdc++ available for my Ubuntu installation is 5

---

