---
title: "Installing Skype in Raring final beta"
date: 2013-04-06
forum: Ubuntu Development Version
---

### Post by stoneguy on 2013-04-06
Another thread contains muttering about who's to blame for the fact that Skype doesn't install.

If you want to test Skype, rather than point fingers, download the 32 or 64 bit version of libxss1 from [http://www.ubuntuupdates.org/package/core/raring/main/base/libxss1]("http://www.ubuntuupdates.org/package/core/raring/main/base/libxss1"). Install it. Then install skype-bin and skype packages from regular repos.

Test call was OK, so I assume it's working.

---

### Post by Rukiri on 2013-04-06
I've never had this issue, I just downloaded skype from the app center and it worked out great.  Can make sykpe calls or just Im just fine.

---

### Post by shantiq on 2013-04-07
installed libxss and then

> shan@shan:~/Desktop$ sudo dpkg -i *skype*Selecting previously unselected package skype.
(Reading database ... 283066 files and directories currently installed.)
Unpacking skype (from skype_4.1.0.20.0-0ubuntu0.12.04.2_amd64.deb) ...
Setting up skype (4.1.0.20.0-0ubuntu0.12.04.2) ...
shan@shan:~/Desktop$ skype
Segmentation fault (core dumped)


[ATTACH=CONFIG]241054[/ATTACH][ATTACH=CONFIG]241053[/ATTACH]



any suggestions? what can be missing?  i am on a 64-bit and i see these i386 packages but tey were installed when i installed 64 debs.   What is going on?


[B]
PS   [/B]ok found a [route]("http://ubuntuforums.org/showthread.php?t=2133148&p=12592353#post12592353") with 4.0 instead of 4.1 for the time being

---

### Post by dionizion on 2013-04-21
Hi guys, I found this solution:

[http://jahnke-network.com/skype-segmentation-fault-gnome_3-8/](http://jahnke-network.com/skype-segmentation-fault-gnome_3-8/)

---

