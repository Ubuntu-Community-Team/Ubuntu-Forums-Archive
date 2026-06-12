---
title: "Problem Installing Virtual Box"
date: 2010-07-09
forum: Virtualisation
---

### Post by Whisp3r on 2010-07-09
Hi everyone. I downloaded the 3.6 version of VirtualBox for my version of Karmic from the Oracle website.

The installation went smoothly, however, when I try to type 'virtualbox' into the terminal, I get the following:

```
whisper@Laptop:~$ virtualbox
The program 'virtualbox' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose-qt
virtualbox: command not found

```

But I have 3.2 installed? If I try to install virtualbox-ose, which I don't want, I get the following:

```
whisper@Laptop:~$ virtualbox
The program 'virtualbox' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose-qt
virtualbox: command not found

```

Help! :)

---

### Post by howefield on 2010-07-09
You might want to try the proper command which is

```
VirtualBox
```

Note the capitalised V & B.


Also the version in the repository is virtualbox-ose. So it would be...

```
sudo apt-get install virtualbox-ose
```

---

### Post by TheFu on 2010-07-10
There are 2 different editions of VirtualBox. The Open Source Edition, OSE, and the other, PUEL, proprietary edition.  The way that Sun/Oracle differentiates the tools is by the case of the commands.  

VirtualBox = PUEL version
virtualbox = OSE version

I suspect the other commands like VBoxManage are also case sensitive with the OSE version in all lowercase.  This only matters when the host runs a case sensitive file system - like almost every *NIX-like system.

When you ask for help here, it is important to be clear on which version, OSE/PUEL you are running.
[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

