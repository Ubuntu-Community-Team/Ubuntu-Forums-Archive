---
title: "Help needed...Error message while using PuTTY"
date: 2018-02-20
forum: Server Platforms
---

### Post by stefan100k on 2018-02-20
[FONT=Arial]Hi Folks, [/FONT]
[FONT=Arial]I am new to all this and hope to find some advise here. [/FONT]
[FONT=Arial]I am trying to set up a Server / VPN for a Masternode and i got stuck at PuTTY. [/FONT]
[FONT=Arial]I did all the steps incl. 5.1...next is... [/FONT]

[FONT=Arial]Step 6 : Configure the node [/FONT]
[FONT=Arial]if you didn't do the step 5.1, you will need to add ./ in front of all the command. [/FONT]

[FONT=Arial]Start the node : [/FONT]

[FONT=Arial]monoecid -daemon [/FONT]
[FONT=Arial]This will create the folder ~/.monoeciCore into your home. [/FONT]

[FONT=Arial]Unfortunately i am getting an error message: [/FONT]

[FONT=Arial]monoecid -deamon [/FONT]
[FONT=Arial]monoecid: error while loading shared libraries: libboost_system.so.1.54.0: cannot open shared object file: No such file or directory [/FONT]

[FONT=Arial]Can anyone advise what to do ?? Any help is highly appreciated. Thanks [/FONT]

---

### Post by wildmanne39 on 2018-02-20
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by stefan100k on 2018-02-20
Thanks Wildmanne39 for forwarding it to the right forum....appreciate it !

---

### Post by The Cog on 2018-02-20
I have no idea what you are trying to configure (doesn't really matter) but I guess it is not made for your version of distro. I just looked on mine here (Ubuntu 16.04.3) using the command "locate libboost_system.so" and it found version 1.58.0. You could try making a link to the newer version of the library with the name your software is looking for, but there are no guarantees that it will work. These commands should make the link. You will have to adjust them to account for whatever version of the .so you actually have on your system:
```
cd /usr/lib/x86_64-linux-gnu
sudo ln -s libboost_system.so.1.58.0 libboost_system.so.1.54.0
```

---

### Post by stefan100k on 2018-02-20
Thanks The Cog , unfortunately you right. I just found out that the set up instruction is for Ubuntu 14 , i use 16. At Scaleway no way to have chosen that version and at the homepage of the node that is try to set up they recommend Scaleway but do not mention anything about the version. ](*,)
So here i am , trying to get it done with help from you and other helpful people. Unfortunately , it did not help this time. Still looking for the solution.

---

### Post by LHammonds on 2018-02-20
```
locate libboost_system.so
```
This does not return any results for my Ubuntu Server 16.04.3 LTS.  So I guess that library is not part of the default install packages.

When I first read your post, it sounds to me like you don't have all the requirements installed for that software.

If you were following instructions for Ubuntu Server 14.04, I'm sure some libraries and their packaging have changed enough to prevent the exact commands to install between different versions.

Try running this command to look at the shared object dependencies:
```
ldd [FONT=Arial]~/.monoeciCore[/FONT]
```

You might need to install libboost manually.  I'm guessing it is from boost.org but I have no idea really.

LHammonds

---

### Post by The Cog on 2018-02-21
Good point. libboost is here on my laptop, but I have no idea what caused it to get installed. Synaptic shows that I have package libboost-system1.58.0 installed and it contains that (version 58) file. So this command shoudl install it:
```
sudo apt install libboost-system1.58.0
``` adn then you will have to make the symlink I referred to earlier.

---

