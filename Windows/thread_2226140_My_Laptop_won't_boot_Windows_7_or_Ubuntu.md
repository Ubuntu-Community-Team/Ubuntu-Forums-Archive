---
title: "My Laptop won't boot Windows 7 or Ubuntu"
date: 2014-05-25
forum: Windows
---

### Post by j_circuit_z on 2014-05-25
So I was interested in trying out Ubuntu. I downloaded the .iso and put it on a USB and went about using it without installing it. I was switching between Windows 7 and Ubuntu and everything was fine until I decided to try and install it and then partition my harddrive.

Admittedly, I didn't know very much of what was going on, the guide I was using said it was easy and straight forward, so I figured I couldn't mess anything up too bad, and honestly, it didn't let me do anything (as far as I know). I was attempting to partition my hdd and it was telling me, if I remember correctly, that I hadn't chosen a drive to partition. So I was like whatever, restarted my laptop and booted up in Windows to try to figure out what was wrong online. I decide to go back to Ubuntu and then this go around I accidentally click on the wrong option regarding how to install it and chose to completely wipe my hdd. The first screen to show after selecting that option asked for my location on the map geographically. I didn't choose anything, I didn't continue on, I just shut down the laptop after that and then tried booting back into Ubuntu.

Trying to reinstall Ubuntu leads me to the Ubuntu startup screen (4 circles) that never progresses. If I try to boot it without installing, I get the startup screen that within 4 seconds goes to a blank black screen.

So I try booting Windows 7 and I get a black screen with a blinking "_".

I try doing a system restore of my harddrive, which leads me to a screen asking me if I really do want to do a system restore, yes or no. I enter no and nothing happens, I can continue moving the cursor left or right between the two options, but if I enter yes then the screen locks up and you can't move the cursor and stays on the same gui.

I'm about to try the boot-repair, I suppose I'll edit this with the results. I just decided to type this up while I was waiting for the iso to write onto the usb

---

### Post by j_circuit_z on 2014-05-25
So I start up boot repair ([http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/) to be clear), select the recommended repair, and I get a boot repair dialog saying

"Please enable a repository containing the [Linux] packages int he software sources of Ubuntu 14.04 LTS(sda1). Then try again."


then it generates a sources.list file with:

"deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates main restricted"
 

I suppose it tells me what to do from here but, I'm not sure how I'm supposed to go about "enabling a repository"

Any help would be greatly appreciated. Thank you very much in advance.

Edit: Oh, I pressed OK on the first dialog box and now I got a new one:

"Please enable a repository containing the [grub]2 packages int he software sources of Ubuntu 14.04 LTS(sda1). Then try again."

And then that's all of it. I'm then left with the initial boot repair dialog where I can choose to do the recommended repair again.

---

### Post by Elfy on 2014-05-25
[http://ubuntuforums.org/showthread.php?t=2226146](http://ubuntuforums.org/showthread.php?t=2226146)

dupe

---

