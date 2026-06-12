---
title: "Ubuntu 23.04 Beta Can NOT be Installed"
date: 2023-04-02
forum: Ubuntu Development Version
---

### Post by amjjawad on 2023-04-02
Hi everyone,


[LIST=1]
[*]I downloaded the Desktop Image - [64-bit PC (AMD64) desktop image]("https://releases.ubuntu.com/23.04/"). 
[*]The size of the Desktop Image is 4.8 GB. 
[*]I checked SHA256SUMS - all good. 
[*]I used [Make Startup Disk] which is installed by default on my Ubuntu to create the LiveUSB. 
[*]My Testing machine is HP EliteDesk 800 G2 SFF. Core i5 vPro with 8GB RAM and 256GB SSD. 
[*]As always, I selected [Try Ubuntu]. The look and feel is quite amazing. 
[*]The machine I'm using to test is an old Desktop. 
[*]Because I want to keep Windows for games, I need to Dual-boot. That is why I ran GParted. 
[*]I had to delete one of the (4) partitions so I got rid of the [HP Tool] Drive. 
[*]I already cleared more than 70GB from the entire Disk (SSD) before I  start the test. All what I needed to do is to resize and shrink. 
[*]I created an Extended Partition. Inside, I created (2) Partitions for  Ubuntu 23.04 Beta. One is the main (/) and the other is SWAP. YES, this  is my approach. I always use GParted to prepare the Disk before I start  the installation whether I'm testing or not. 
[*]I really like how the Installer looks like. Really beautiful. Well done! 
[*]Without being connected to the Internet, I started the installation. 
[*]All went well until I reached to [Keyboard Layout] screen. I thought to  change the language to test but I got an error message: [System program  problem detected - do you want to report the problem now?]. Because I  wasn't connected to the Internet, I didn't report. 
[*]As always, I  selected Manual Installation. Remember, I need to Dual-Boot and I don't  want any surprises, given it is the Beta version and not yet final. 
[*]When I selected the Partitions and was trying to go to the next step, I  got the exact error message [System program problem detected] and I  couldn't move forward. I had to stop. 
[*]The USB I used to test  and install Ubuntu 23.04 Beta is in a good shape. I doubled check the  SHA256SUMS. I'm not yet sure what the real problem is. 
[*]While this attempt has [Failed], I will try again. If the same issue occur, I will report the bug. 
[*]The MOST important step in OS testing is the Installation Step. What an OS without being installed on a machine? 
[/LIST]

Update 1:
I tried again on a different machine - the exact same problem.

Update 2:
[https://bugs.launchpad.net/subiquity/+bug/2015028](https://bugs.launchpad.net/subiquity/+bug/2015028)

Thoughts?

Thank you.

---

### Post by zebra2 on 2023-04-03
It most definately can be installed.  I have installed it a dozen times in the last week.  It isn't friendly right  now with dual boot and it is finicky about the efi/esp partition. You may need to wait until the release or beyond to get what you are attempting.

---

### Post by corradoventu on 2023-04-03
I have installed Beta on 3 different PC (NO windows present) without problems

---

### Post by amjjawad on 2023-04-03
It can be installed ONLY if you don't change the Keyboard Layout.
In my case, when I changed the Keyboard Layout, I was unable to install.

---

### Post by kronosxtitans on 2023-04-03
i installed the beta release and i had to do it twice.The first time the progress was running for 30 mins then i just switched off the pc and reboot,grub menu was empty so i reboot again and  reinstalled from usb,it then worked but so many error and crashes.Even the text editor crashes and freezes forcing a shutdown on the editor.I understand beta is beta.i dual booted with win 10 in case i got a full failed system.Just create a live usb again. is it gpt format the system

---

### Post by zebra2 on 2023-04-03
I don't know if you have a junk pile or not but this would be a good time to practice/test with a substitute blanked out drive.

---

### Post by Claus7 on 2023-04-03
Hello,

> **amjjawad said:**
> It can be installed ONLY if you don't change the Keyboard Layout.
In my case, when I changed the Keyboard Layout, I was unable to install.

I confirm the above statement. Actually I changed keyboard layout and faced the same issue. Didn't try the default.

Regards!

---

### Post by amjjawad on 2023-04-03
> **Claus7 said:**
> Hello,

I confirm the above statement. Actually I changed keyboard layout and faced the same issue. Didn't try the default.

Regards!

Thank you. Could you please login to Launchpad and confirm that you are affected as well?
[https://bugs.launchpad.net/subiquity/+bug/2015028](https://bugs.launchpad.net/subiquity/+bug/2015028)

Thank you!

---

### Post by Claus7 on 2023-04-04
Hello,

> **amjjawad said:**
> Thank you. Could you please login to Launchpad and confirm that you are affected as well?
[https://bugs.launchpad.net/subiquity/+bug/2015028](https://bugs.launchpad.net/subiquity/+bug/2015028)

Thank you!

I cannot connect to the link provided. Also searching with "2015028" didn't bring any result.

Regards!

---

### Post by amjjawad on 2023-04-04
> **Claus7 said:**
> Hello,

I cannot connect to the link provided. Also searching with "2015028" didn't bring any result.

Regards!

Hi and thank you for your reply.

I don't know why that report is Private. I have no idea how to change it to Public so others can confirm. I will try to do some search.

---

### Post by amjjawad on 2023-04-04
[https://bugs.launchpad.net/subiquity/+bug/2015028](https://bugs.launchpad.net/subiquity/+bug/2015028)

I did a quick search. The report now is Public.

If anyone else is affected by this bug, kindly confirm that on Launchpad.

Thank you!

---

### Post by Claus7 on 2023-04-04
Hello,

> **amjjawad said:**
> [https://bugs.launchpad.net/subiquity/+bug/2015028](https://bugs.launchpad.net/subiquity/+bug/2015028)

I did a quick search. The report now is Public.

If anyone else is affected by this bug, kindly confirm that on Launchpad.

Thank you!

done!

Regards!

---

### Post by RobotSpaceTime on 2023-04-21
I am having an issue during manual installation as well. It will not continue after I have set mount points. NEXT is greyed out. And there is no "Install Now" as seen in older distros. I can only revert, and even then Next is still grey.

---

### Post by sudodus on 2023-04-21
If you want to help debug the new installer, fine :-P

Otherwise, if you simply want to install Ubuntu 23.04 Desktop, you can use the **legacy iso** file ;-)

[cdimage.ubuntu.com/releases/lunar/release/ubuntu-23.04-desktop-legacy-amd64.iso](http://cdimage.ubuntu.com/releases/lunar/release/ubuntu-23.04-desktop-legacy-amd64.iso)

with the following sha256sum:

```

0cef2280b3d8710733231d1ad1c72474e6bbc41a0d8d2ea69f7728f3d60fb786 *ubuntu-23.04-desktop-legacy-amd64.iso

```

This iso file has the old installer 'Ubiquity' which is well-known and well tested. We know what it can do (and what it cannot do too).

It is a good idea to get the file via **torrent**:

[**cdimage.ubuntu.com/releases/lunar/release/ubuntu-23.04-desktop-legacy-amd64.iso.torrent**](http://cdimage.ubuntu.com/releases/lunar/release/ubuntu-23.04-desktop-legacy-amd64.iso.torrent)

---

### Post by amjjawad on 2023-04-23
I have updated the bug report ([https://bugs.launchpad.net/subiquity/+bug/2015028](https://bugs.launchpad.net/subiquity/+bug/2015028)) with this comment:

> Thank you, I confirm that the issue has been solved. However, if the partition table is GPT, there is no way I can install and yes, I'm referring to the final release, that is Ubuntu 23.04 and I had the exact same issue with the daily build 17-April-2023. I had to create a new partition table via GParted (msdos) and reboot. Only then, I managed to install normally. Hope that helps! 

[https://bugs.launchpad.net/subiquity/+bug/2015028/comments/7](https://bugs.launchpad.net/subiquity/+bug/2015028/comments/7)

Thank you!

---

