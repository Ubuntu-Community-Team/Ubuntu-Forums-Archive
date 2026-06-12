---
title: "Hamachi install troubles"
date: 2009-01-31
forum: Server Platforms
---

### Post by theunixchild on 2009-01-31
when i am installing hamachi i get 

```
solomon@solomonhomelinux:~$ cd hamachi-0.9.9.9-20-lnx/
solomon@solomonhomelinux:~/hamachi-0.9.9.9-20-lnx$ sudo make install

Copying hamachi into /usr/bin ..
Creating hamachi-init symlink ..
Compiling tuncfg ..
Copying tuncfg into /sbin ..
strip: Unable to recognise the format of the input file `/sbin/tuncfg'
install: strip process terminated abnormally
make: *** [install] Error 1

```

does anybody know what this means?

i am using ubuntu 8.10 server on a macmini

---

### Post by spynappels on 2009-01-31
Hi,

 You need to install binutils.

```
sudo apt-get install binutils
```

That will allow you to install Hamachi.

Stefan.

---

### Post by theunixchild on 2009-01-31
says binutils are already up to date

```
solomon@solomonhomelinux:~$ sudo apt-get install binutils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
binutils is already the newest version.
binutils set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
solomon@solomonhomelinux:~$ 

```

---

### Post by spynappels on 2009-02-01
Ok, could you  tell us what version of Ubuntu you are running, 32 or 64 bit? If it is 64bit, you need to install the 32 bit libraries, ```
sudo apt-get install ia32-libs
```
Edit: if you are using a MacMini you will not be running 64 bit.

Also make sure that make is installed properly.

If neither of this helps, I'm out of my depth. You might also try looking in the hamachi forums for help, they can be slow to reply but often do come up with good suggestions.

Regards, Stefan.

---

### Post by theunixchild on 2009-02-02
so i reinstalled binutils and now it gives ```
solomon@solomonhomelinux:~/hamachi-0.9.9.9-20-lnx$ sudo make install

Copying hamachi into /usr/bin ..
Creating hamachi-init symlink ..
Compiling tuncfg ..
Copying tuncfg into /sbin ..
strip: Unable to recognise the format of the input file `/sbin/tuncfg'
install: strip process terminated abnormally
make: *** [install] Error 1
solomon@solomonhomelinux:~/hamachi-0.9.9.9-20-lnx$ t
```

i is very baffled

EDIT:
and...
```
solomon@solomonhomelinux:~/hamachi-0.9.9.9-20-lnx$ tuncfg/tuncfg
-bash: tuncfg/tuncfg: cannot execute binary file

```

---

