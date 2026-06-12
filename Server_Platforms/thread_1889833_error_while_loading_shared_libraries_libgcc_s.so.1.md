---
title: "error while loading shared libraries: libgcc_s.so.1"
date: 2011-12-02
forum: Server Platforms
---

### Post by Crumbs744 on 2011-12-02
After a restart im coming across the following error:

> error while loading shared libraries: libgcc_s.so.1: wrong ELF class: ELFCLASS32


I think i have overwritten files in /lib (im guessing a nooby mistake :P)

I was hoping someone might assist me in getting the correct files back in there. The reason i put them there in the first place was some probably misinterpreted instructions when trying to install and run a COD2 server.

Appreciate any pointers you could give me. Thanks!

---

### Post by rubylaser on 2011-12-02
You could probably get more help if you explained what version of Ubuntu you're using and if it's 32/64 bit.  Also, link to those build directions you posted in the other thread for the COD2 server. Also, the output of this command might help.

```
lsb_release -a
```
```
uname -a
```

```
ldd /lib/libgcc_s.so.1
```
Should give something like this.
```
	linux-vdso.so.1 =>  (0x00007fff8d1ff000)
	libc.so.6 => /lib/libc.so.6 (0x00007f93c4fbe000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f93c553a000)
```

---

### Post by Crumbs744 on 2011-12-03
This was the part of the instructionsi followed that i probably did wrong... found [here]("http://games.on.net/file/2632/Call_of_Duty_2_Retail_dedicated_Linux_server_v1.3")

> IF YOU HAVE A PROBLEM WITH "LIBSTDC++.SO.5" ...
(This is a frequent-enough problem to merit discussion in the introduction.)

If you are reading this, it's probably because you tried to start your Linux
server and saw this message:

./cod2_lnxded: error while loading shared libraries: libstdc++.so.5:
cannot open shared object file: No such file or directory

COD2 is a C++ program built with gcc 3.3.4, which means it needs a
system library specific to gcc 3.3. Older Linux systems won't have
this installed, and we're starting to see newer Linux distributions that
don't have this either, since they are supplying an incompatible
gcc 3.4 version. The good news is that you can drop the needed library
into your system without breaking anything else.

Here is the library you need, if your Linux distribution doesn't supply it:
[http://icculus.org/updates/cod/gcc3-libs.tar.bz2](http://icculus.org/updates/cod/gcc3-libs.tar.bz2)

You want to unpack that somewhere that the dynamic linker will see it
(if you are sure it won't overwrite any files, you can even use /lib).

The brave can put it in the same directory as the game and run the server
like this:
LD_LIBRARY_PATH=$LD_LIBRARY_PATH:. ./cod2_lnxded

------------------------------

lsb_release -a:
```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.10
Release:        9.10
Codename:       karmic

```

uname -a
```
Linux crumbs-server 2.6.31-23-server #75-Ubuntu SMP Fri Mar 18 19:23:09 UTC 2011 x86_64 GNU/Linux
```

ldd /lib/libgcc_s.so.1
```
        linux-gate.so.1 =>  (0xf7792000)
        libc.so.6 => /lib32/libc.so.6 (0xf7631000)
        /lib/ld-linux.so.2 (0xf7793000)
```

---

### Post by rubylaser on 2011-12-03
Hopefully someone with more knowledge in this area will come along to help you out. Do you remember where you unpacked gcc3-libs?  Was it in your /lib folder or in the game folder?

---

### Post by Crumbs744 on 2011-12-04
i believe it was the /lib folder. :S

---

