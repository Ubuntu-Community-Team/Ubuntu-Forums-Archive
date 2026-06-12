---
title: "[SOLVED] Scramdisk for Linux with Feisty?"
date: 2007-08-22
forum: Server Platforms
---

### Post by StewartM on 2007-08-22
First of all, let me introduce myself as  a brand-new Linux user, although I've been using the Windows version of Scramdisk and Truecrypt for years.

To transfer my containers from a dead Win98 box, I was counting on using Scramdisk for Linux, which purports to open both legacy Windows Scramdisk containers and Truecrypt ones. I downloaded the .deb file for Scramdisk for Linux (SD4L) from Sourceforge (for Ubuntu 7.04, mind you), and later the libqt3-mt file to resolve the stated dependency, and apparently SD4L installed correctly. 

However, what I'm seeing is this:

a) I can create and open small (like floppy size, 1.4 megabyte) containers created by either SD4L or legacy Windows Scramdisk OK.

b) I can open small (1 megabyte) containers created with TrueCrypt (on a Windows machine) OK, irregardless of the algorithms chosen.

c) Containers larger than floppy sized (I've tried down to 500 megabytes) cause Feisty to lock up completely requiring a hard reboot after entering the password and trying to mount. This is irregardless of the hash algorithm,  encryption algorithm, or file format chosen. It is also irregardless of whether the containers were created with SD4L or whether they were created by TrueCrypt on a Windows machine.

d) When walking away from a container creation for "large" containers, sometimes I come back to the desktop seeing that SD4L has closed in the process of container generation. When attempting to create containers bigger than 2 gigabytes, I always get containers of 2.0 gigabytes irregardless of the size chosen. Needless to say, all these freeze up Feisty when I try to mount them as per above.

A search of the Ubuntu forums that one other user has complained about not being able to mount containers, and I also see on the SD4L announce list that there is a problem with containers larger than 2 gigabytes. However, apparently some users are succesfully creating and using containers up to 2 gigabytes, which I cannot.

So...(and remember I'm a complete Linux newbie)...is there some other library or dependency that I've not fulfilled? Do I need to install something else? What am I doing wrong?

BTW: on related issues--I've seen posts on this forum and on the web about using Truecrypt (a possible alternative) for 7.04, and some say you need to compile it from source (despite there being a version for 7.04 available), whereas other web how-tos seem to infer that the Truecrypt install is a straight shot. What is the current status of this?

I'd like to also be able to encrypt my /home and /tmp and /var swap directories, but the community howtos look on this pretty daunting, with some requiring re-installation of Feisty after setup. Being such a newbie, I'd hate to begin my Ubuntu experience with re-installing the OS right off the bat. Right now I'm still connecting to the internet by an XP laptop (not mine) and trying to "prepare" my Ubuntu box for use the way I'd like it. As a minimum, that's being able to keep my stuff encrypted, and at least being able to wipe tmp/var/swap files if I can't encrypt them.

Sorry if I'm amiss by posting in this sub-forum, but I don't think "absolute beginners" was appropriate either. I can usually figure out how to get the pre-installed stuff to work in Feisty by either digging through the menus or reading the documentation. It seems pretty well done in that way.

---

### Post by StewartM on 2007-08-24
Update: I just opened one of the containers I had created (but wouldn't mount) that was 2.0 gigabytes in size using TrueCrypt (for Windows). However, it told me that the container was unformatted, and offered to format it for me.

So it seems that within-container file formats are indeed the problem. 
I will update what I posted to the Scramdisk forum as well.

---

### Post by StewartM on 2007-09-12
> **StewartM said:**
> Update: I just opened one of the containers I had created (but wouldn't mount) that was 2.0 gigabytes in size using TrueCrypt (for Windows). However, it told me that the container was unformatted, and offered to format it for me.

So it seems that within-container file formats are indeed the problem. 
I will update what I posted to the Scramdisk forum as well.

Just an update on this.

There did happen to be two bugs that accounted for this  problem. They have since been fixed, and Scramdisk for Linux runs on 7.04 almost fine.

Well, almost. It seems (at least by my testing) that although Scramdisk containers mount flawlessly, Truecrypt ones will not mount properly if a too-long passphrase (say, 30-some characters, but less than 39) is used. 20-something character passphrases work Ok. 

Facing a crises on booting my system just yesterday (fsck failure) :( obviously I'm not able, or  motivated, right now to try to determine the exact length of passphrase where Truecrypt containers fail to mount. 20-something near-random character passphrases, while not as strong as an AES-256 big key, are still pretty strong.

Stewart

---

### Post by StewartM on 2007-09-19
As I'm talking to the developer and maintainer of Scramdisk4Linux via email about what I'm observing, I'll close this thread. I may open it up under "general help" as I'm not sure this is the correct forum. 

I'll post whatever results I get there. Right now, it works OK. :)

Stewart

---

