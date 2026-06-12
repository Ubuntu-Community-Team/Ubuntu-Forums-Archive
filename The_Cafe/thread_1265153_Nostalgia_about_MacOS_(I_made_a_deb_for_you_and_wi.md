---
title: "Nostalgia about MacOS? (I made a deb for you and wiki)"
date: 2009-09-13
forum: The Cafe
---

### Post by frenchn00b on 2009-09-13
Hi Guys, 

MacOS, ? did you recall. So here is how to make it run under your Linux machine Ubuntu.

So here is the procedure:

(1)  You need libxt-dev and  x11-common to be present
```
apt-get install libxt-dev
apt-get  libstdc++6-4.1-dev      ## not that necessary
apt-get install x11-common

```

(2) You lib is missing 2 files, that can be downloaded here. 
Or type this
Please verify it (ls /lib)
```
cd /tmp
mkdir somelib
cd somelib
wget -N "http://yellowprotoss.ye.funpic.org/website/basilikII/libstdc++-3-libc6.2-2-2.10.0.so"
wget -N "http://yellowprotoss.ye.funpic.org/website/basilikII/libstdc++-libc6.2-2.so.3"
sudo cp  /tmp/somelib/libstdc++-3-libc6.2-2-2.10.0.so  /lib
sudo cp  /tmp/somelib/libstdc++-libc6.2-2.so.3  /lib
```
(for the advanced coders, eventually if you'd like, I made a deb [here]("http://yellowprotoss.ye.funpic.org/website/basilikII/libstdc++_2.95.3-5.1_i386.deb"))

(3) Let's intall
```
cd /tmp
wget -N "http://yellowprotoss.ye.funpic.org/website/basilikII/basiliskii_0.9-2_i386.deb"
sudo dpkg -i basiliskii_0.9-2_i386.deb

```

(4) now as user ($) type:
```
BasiliskII

```

You get the program
Basilisk II V0.9 by Christian Bauer et al.
Image [here shot]("http://yellowprotoss.ye.funpic.org/website/basilikII/basilik2.png")

Enjoy!

Any comments about whether you like the application, do not hesitate to post.
[http://www.math.colostate.edu/~reinholz/freebsd/apps_computer_emulators.html](http://www.math.colostate.edu/~reinholz/freebsd/apps_computer_emulators.html)
--
Basilik2 Src code is available [here]("http://yellowprotoss.ye.funpic.org/website/basilikII/BasiliskII_src_31052001.tar.gz")
Can probably also work under Debian/ and other Deb based distro.
  
You then have to find your old cdroms for mac, if you would like to use MS WORD 98. It is much better than wine, faster, and so nice macintosh compared to windows.

--
If you would like his brother, called sheepshaver, bit newer, I make too a deb for it [here]("http://yellowprotoss.ye.funpic.org/website/macintosh/sheepshaver/sheepshaver_1.47-1_i386.deb")
to install it :
> dpkg -i sheepshaver_1.47-1_i386.deb

---

### Post by pmooney78 on 2010-05-29
But this is totally unnecessary. BasiliskII is available in the standard repositories and can be installed simply by typing 

```

sudo apt-get install BasiliskII

```

from a terminal. It's much easier that way.

---

### Post by blueturtl on 2010-05-29
Thank you for your efforts.

I have just two questions: Is this a newer version than the one in the repositories? Can you / how do you enable more complete ADB emulation in the Linux version (the Windows version had a tickbox that's missing from the Linux GUI)?

---

### Post by bornagainpenguin on 2010-07-12
> **pmooney78 said:**
> But this is totally unnecessary. BasiliskII is available in the standard repositories and can be installed simply by typing 

```

sudo apt-get install BasiliskII

```

from a terminal. It's much easier that way.

Really?

```
bornagainpenguin@blessing:~$ sudo apt-get install BasiliskII
[sudo] password for bornagainpenguin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package BasiliskII
```

Somehow the terminal disagrees with you...

--bornagainpenguin

---

### Post by cariboo on 2010-07-12
If you are running Karmic or older, try:

```
sudo apt-get install basilisk2
```

pmooney78 had a slight typo in his instructions.

---

### Post by bornagainpenguin on 2010-07-26
> **cariboo907 said:**
> If you are running Karmic or older, try:

```
sudo apt-get install basilisk2
```

pmooney78 had a slight typo in his instructions.

I see the error now.  Running Lucid actually.  Will install as soon as I get back to my Ubuntu eeepc...  Thanks!

--bornaginpenguin

---

### Post by samalex on 2010-07-26
Nice!  I've tried a few Mac emulators, but most require a Mac ROM which I never can find.  Will installing this from the repositories get it up and going, and once so what version of MacOS will it have -- or is that where the ROM comes into play?

And if a ROM image is needed, and hints on where I can find one?  I'd love to run MacOS 7, 8, or 9 under Linux -- 9 specifically.

Sam

---

### Post by CJ Master on 2010-07-26
You should get your ROMs from a legally bought CD-Rom ;) But remember: Google is your friend.

---

### Post by samalex on 2010-07-26
I guess they took this out of the repositories for Lucid, it's not there ... even searched using Synaptic.

As for ROM's, when you guys say legally bought CD, are you talking about installing the Mac OS from scratch or is there some legal source that sells Mac OS ROMs with the OS on ROM?  Just curious because I know Mac OS9 and others came on CD but I guess you'd still need the ROM to boot from.

I'll hunt for them, but if anyone has suggestions on other ways to get them, please PM me :-D

Thanks --

Sam

---

### Post by ewood on 2010-09-23
> **samalex said:**
> I guess they took this out of the repositories for Lucid, it's not there ... even searched using Synaptic.

As for ROM's, when you guys say legally bought CD, are you talking about installing the Mac OS from scratch or is there some legal source that sells Mac OS ROMs with the OS on ROM?  Just curious because I know Mac OS9 and others came on CD but I guess you'd still need the ROM to boot from.

I'll hunt for them, but if anyone has suggestions on other ways to get them, please PM me :-D

Thanks --

Sam
Legal mumbo jumbo aside, you will need a ROM from a 68k-based Mac model (say, a Quadra or other 1 MB ROM file), which can be found pretty easily by searching for something like "Mac 68k ROM". You can't use a Power Mac ROM like the OS 9 one for Basilisk II, though that one *is* useful for SheepShaver, which emulates an older Power Macintosh and has an interface that basically clones that of Basilisk II. Or was it vice versa?

---

### Post by frenchn00b on 2010-09-25
> **samalex said:**
> Nice!  I've tried a few Mac emulators, but most require a Mac ROM which I never can find.  Will installing this from the repositories get it up and going, and once so what version of MacOS will it have -- or is that where the ROM comes into play?

And if a ROM image is needed, and hints on where I can find one?  I'd love to run MacOS 7, 8, or 9 under Linux -- 9 specifically.

Sam

give a try to : quadra650.rom
of md5 equal to 69489153dde910a69d5ae6de5dd65323  

Howevever how to install 1GB of space disk to get system 7?


There was a large website machut.org with all kind of programs, such as photoshop, office ...  and this is: 
> NOTICE: This domain name expired on 08/25/2010 and is pending renewal or deletion
example : MS%20PowerPoint%203.0%2068k.sit

---

