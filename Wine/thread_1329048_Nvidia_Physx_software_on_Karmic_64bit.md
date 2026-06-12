---
title: "Nvidia Physx software on Karmic 64bit"
date: 2009-11-17
forum: Wine
---

### Post by aniruddha on 2009-11-17
Hello all. I have recently been trying to install Dragon Age: Origins from Bioware on my 64bit Karmic system. I manage to install the game itself, however the installation always hangs on trying to install nvidia's physx software. I have tried to install this piece of software using both the exe from the nvidia website, from the game's dvd, and by running winetricks. I keep getting the following error however:

err:msi:ACTION_CallDllFunction failed to load dll L"C:\\windows\\temp\\msia6f.tmp" (998)

My system is a Karmic 64bit, NVIDIA 190.42 drivers running wine 1.1.33. I have tried to install physx on wine 1.1.31 and 32 as well as with the 185 nvidia drivers that came in the karmic repos. I have already posted this issue in the wine forums and the app db, but would really like to get this game running (with booting into windows) and so have attempted to get some help from the ever awesome ubuntuforums as well. Apologies.

Thanks a lot.

---

### Post by aniruddha on 2009-11-18
bump?

anyone?

---

### Post by lakersforce on 2009-12-04
I found the answer on winehq, thx Anton:

> 	
RE: PhysX
by Anton on Tuesday November 17th 2009, 14:14
I can "install" PhysX on 64-bit ubuntu. I load 32-bit ubuntu with boot cd, installed wine and PhysX there. Then copy .wine to my home folder on 64-bit system. Everything work now. 

> 	
RE: PhysX
by Anton on Sunday November 22nd 2009, 10:23
Hi. I just prepared the necessary files.
rapidshare.com/files/310656596/physx.tar.gz.html

Just extract archive to your .wine/drive_c folder. There is also physx.reg inside the package - copy-paste content of this file to your .wine/system.reg

Hope this helps.

It solves the problem, but link should probably be copied to more secure location.

---

### Post by Kubunteando on 2009-12-05
I did something similar:

1. I booted with a 32bit live CD a Ubuntu Karmic
2. I installed the same wine version as I had in the 64 bit system
3. I mounted the partition where the .wine was installed in the 64bit system
Let's say the 64bit system is in /dev/sda7, then you make
# mkdir /C
# chown ubuntu:ubuntu /C
# mount /dev/sda7 /C

4. now we fake the .wine folder to point to the 64bit .wine with a symbolic link
# cd
# ln -s /C/.../.wine .wine

5. the owner of the .wine folder and files should be the user ubuntu, so you have to change it with the commend chown. With the ls command check which is the current user and group owning the files, so you can restore back after installing Physx. In my case the ls -la returned:
lrwxrwxrwx  1 1000 1000     15 2009-12-04 20:46 .wine

So the user and group id are 1000.

# cd
# chown ubuntu:ubuntu .wine -R   (changes the .wine and files recursively to be owned by user ubuntu and group ubuntu).

6. now you can install the physx and the installation will be done in your 64bit system. No need to copy any files. When the installation finishes boot into your 64bit system and test it

7. now we set back the ownership of .wine back to the original user
# cd
# chown 1000:1000 .wine -R   (changes the .wine and files recursively to be owned by user 1000 and group 1+++, replace this value by the one you got in step 5)

8. boot into the 64bit system and test it.

Enjoyt it!

---

### Post by lakersforce on 2009-12-05
Even though it solved the Physx installation problem, the game Dragon Age does not play satisfactory (even after patching), so I ended up making a new partition for XP and play it from there. Wine simply does not do the game justice at this point.

---

### Post by Chesnut on 2009-12-10
Lakersforce, if you still have the physx.tar.gz file you got from rapidshare through the link Anton had put up, could you please reupload it to mediafire or somewhere else. I have the same issue and I do not have any 32 bit Ubuntus. All 64. Too lazy to download and burn one. >_>

--

Nevermind, got it. :P

---

### Post by Spongeroberto on 2009-12-13
Err I would like the physx.tar.gz too if I could:D

---

### Post by KEE on 2010-08-22
whare can i get physx driver?that link is too old

---

