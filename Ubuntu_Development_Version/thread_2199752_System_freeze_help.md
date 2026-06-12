---
title: "System freeze help"
date: 2014-01-15
forum: Ubuntu Development Version
---

### Post by drfox on 2014-01-15
I have been running Xubuntu 14.04 for several weeks without a problem. Last night I did a dist-upgrade and my keyboard and mouse froze, and the cap lock key started flashing. I did a cold reboot and tried apt-get dist-upgrade again...I received the message that I needed to run sudo dpkg --configure -a.
I have tried running that command and also sudo dpkg --force -all --configure -a, but each time I do, the system freezes at this:
Setting up libc6:amd64 (2.18-0ubuntu5)...
Then the system needs to be rebooted. 
If I don't try to fix the problem, the system works OK, but, obviously, I can't leave it like this. Does anyone have any suggestions?
Thanks in advance.

---

### Post by vhaarr+launchpad on 2014-01-15
I get a kernel panic at the same upgrade and the system freezes as well.

---

### Post by Rustan on 2014-01-15
and I have the exact same problem

---

### Post by zenarcher on 2014-01-15
Same thing with Kubuntu.  Flashing keyboard lights and system freeze.

---

### Post by QIII on 2014-01-16
Hmmm.  Fixed since?

No problems here on Kubuntu.  Updating Ubuntu right now.

---

### Post by Kootee on 2014-01-16
Same problem here on Kubuntu/Ubuntu (tried now). Maybe it's because of trusty-proposed updates enabled?
@QIII: do you have trusty-proposed updates enabled? And did you try "sudo apt-get dist-upgrade"?

---

### Post by QIII on 2014-01-16
No proposed, and yes dist-upgrade.

Edit:  Ubuntu worked fine, too.  Might just be something in trusty-proposed.

---

### Post by Kootee on 2014-01-16
Yes, it seems problem with proposed updates. I've disabled and update wanted to repair. But if anyone try DON'T DO IT or you will destroy your system. It have problem with dependiences, and wants to remove about 989 packets (with apt and many importatnt other). So i don't have solution for now, only waiting for repair in proposed updates. Surely downgrade of some packets would help, but i don't know which and how. Unpleasant situation.

---

### Post by drfox on 2014-01-16
I am the OP. Thanks to Kootee for identifying the problem. I unchecked "proposed" and then ran 
"sudo apt-get update" and then 
"sudo apt-get dist-upgrade" and then 
"sudo apt-get -f install" and the problem is fixed.
It did not remove packages...it did install 3 new ones.
Thanks Kootee!

---

### Post by cariboo on 2014-01-16
Just a note to those that don't post here, or read this sub-forum regularly, proposed is now used to store packages while waiting for dependencies to build. It is not advised to have proposed enabled, unless you really know what you are doing.

---

### Post by Kootee on 2014-01-16
Doesn't work in my case.
"sudo apt-get update" - without problems but
"sudo apt-get dist-upgrade" gives me:> $ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'sudo apt-get -f install' to correct these.
The following packages have unmet dependencies:
 cpp-4.8 : Depends: gcc-4.8-base (= 4.8.2-13ubuntu1) but 4.8.2-14ubuntu1 is installed
 gcc-4.8 : Depends: gcc-4.8-base (= 4.8.2-13ubuntu1) but 4.8.2-14ubuntu1 is installed
 lib32gcc1 : Depends: gcc-4.8-base (= 4.8.2-13ubuntu1) but 4.8.2-14ubuntu1 is installed
 libasan0 : Depends: gcc-4.8-base (= 4.8.2-13ubuntu1) but 4.8.2-14ubuntu1 is installed
 libatomic1 : Depends: gcc-4.8-base (= 4.8.2-13ubuntu1) but 4.8.2-14ubuntu1 is installed
 libc6-dbg : Depends: libc6 (= 2.18-0ubuntu5) but 2.18-0ubuntu6 is installed
 libc6-dev : Depends: libc6 (= 2.18-0ubuntu5) but 2.18-0ubuntu6 is installed
 libc6-i386 : Depends: libc6 (= 2.18-0ubuntu5) but 2.18-0ubuntu6 is installed
 libgcc-4.8-dev : Depends: gcc-4.8-base (= 4.8.2-13ubuntu1) but 4.8.2-14ubuntu1 is installed
 libgomp1 : Depends: gcc-4.8-base (= 4.8.2-13ubuntu1) but 4.8.2-14ubuntu1 is installed
 libitm1 : Depends: gcc-4.8-base (= 4.8.2-13ubuntu1) but 4.8.2-14ubuntu1 is installed
 libquadmath0 : Depends: gcc-4.8-base (= 4.8.2-13ubuntu1) but 4.8.2-14ubuntu1 is installed
 libstdc++6 : Depends: gcc-4.8-base (= 4.8.2-13ubuntu1) but 4.8.2-14ubuntu1 is installed
 libstdc++6:i386 : Depends: gcc-4.8-base:i386 (= 4.8.2-13ubuntu1) but 4.8.2-14ubuntu1 is installed
 libtsan0 : Depends: gcc-4.8-base (= 4.8.2-13ubuntu1) but 4.8.2-14ubuntu1 is installed
E: Unmet dependencies. Try using -f.
And when i try 'sudo apt-get -f install' as he says i get:
>  (... - all the packets he wants to remove)... zeitgeist zeitgeist-core zeitgeist-datahub zenity
The following NEW packages will be installed:
  bbswitch-source foomatic-filters ibus-pinyin-db-open-phrase javascript-common libjs-xmlextras libxcb-sync1 lynx lynx-cur module-assistant
  mono-xsp4 mono-xsp4-base monodoc-http pinyin-database python3.4 python3.4-minimal
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libapt-pkg4.12 (due to apt) libstdc++6 (due to apt)
0 upgraded, 15 newly installed, 989 to remove and 64 not upgraded.
Need to get 15.5 MB/16.9 MB of archives.
After this operation, 3,293 MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] 

So he wants to remove almost all the system. I don't know how to repair that.

EDIT [SOLVED]: It seems packets on proposed was updated, because now it run upgrade without problems. After it I've disabled again proposed - I don't want more problems with kernel panic ;)

---

### Post by Rustan on 2014-01-16
disabling repository "proposed" did not help me, when trying to update libc6 version 2.18 I happens kernel panic...

---

### Post by Kootee on 2014-01-16
Try now to enable proposed updates and do 'sudo apt-get update', and 'sudo apt-get dist-upgrade'. In my case now it worked (before 5 minutes). After it I would propose you to disable proposed to avoid such problems in future ;)

---

### Post by Vanishing on 2014-01-16
To anyone who's already did sudo apt-get upgrade:
take out livecd(yes, that time again):
do the usual, chroot into your boot, and simply issue:
sudo dpkg --configure -a, let it finish, reboot.

---

### Post by rrnbtter on 2014-01-16
Greetings, 
This is just for my system but I am having no problems with "Proposed".  I did have freeze problems prior to enabling Proposed. Now it is all fine. 
As to the kernel panic I suggest you check that you hard drive cable is tight or if it is a laptop that the HD is pushed in snug. A loose HD can easily cause a kernel panic.

---

