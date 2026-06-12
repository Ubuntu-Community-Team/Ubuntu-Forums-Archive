---
title: "Ubuntu 18.04 not detecting encrypted home partition"
date: 2018-03-11
forum: Ubuntu Development Version
---

### Post by roma24ster on 2018-03-11
I have two '/' partitions, one with Ubuntu 16.04, and another with 18.04. I've pointed them both to the same home partition, which is encrypted.

I'm having a problem with the 18.04 install however, during the install process, I expected to see [an option like this]("https://i.stack.imgur.com/nhPyL.png"), because that is what I've seen in the past with two ubuntu installs sharing the same encrypted home partition, provided I set the same username and password during install. 

However I never got this option, it didn't give me the option to encrypted my home partition at all. And once I booted up 18.04 and entered my password to log in, it fails to log in, and instead brings me straight back to the log in screen.

The 16.04 installation works fine however.

---

### Post by oldfred on 2018-03-11
I just installed 18.04, but not with any encryption.
I used Something Else install option and did get the standard screen for user & password.

In fact I do not think you can do a full install without having a user & password.
Did you just set up installer on a partition?

---

### Post by jbicha on 2018-03-11
Please file a bug against ubiquity.

However, I believe the encrypted home install option has been removed from the Ubuntu 18.04 installer.

---

### Post by roma24ster on 2018-03-12
@oldfred
Sorry, I do get the option to put a username and password. I expected to see a greyed-out (but checked) tick box for 'Encrypt my home drive' as in the picture in my OP, as that means Ubuntu has detected my encrypted home partition.

@jbicha
Can anyone else confirm that they've removed the option for home drive encryption? Is that because we are being encouraged to use whole disk encryption? The reason I haven't used that in the past is because it doesn't seem possible to have a different home and / partition using LVM.

---

### Post by theprisoner2 on 2018-04-11
I believe I've hit upon this exact same problem. I tried to instal 18.04 and use my previous /home partition, which is encrypted, and it wouldn't get past the login screen and load gnome desktop, which I suspect is because the files it needs are in the inaccessible /home partition. So, I did a sort of work-around by re-installing 18.04 and creating an unencrypted /home folder (sda6) in some free space on my disk - this worked and I now have a working distro and desktop... but I now have my old encrypted /home partition (sda5) still on the disc, which I can't access.

Is there some sort of fault with accessing encrypted partitions on discs? I read in the wiki that there was an issue with accessing external drives if they're encrypted, but I seem to have solved that by following the instructions there. It hasn't resolved the access to the internal, encrypted, partition, though.

Can anyone help?

---

### Post by dino99 on 2018-04-11
Please have a look at [https://bugs.launchpad.net/ubuntu/bionic/+source/linux/+bug/1762468](https://bugs.launchpad.net/ubuntu/bionic/+source/linux/+bug/1762468)  about encrypt problem; that will help.

---

### Post by daogeek on 2018-07-30
I have done a new full install of Bionic Beaver and selected the option to encrypt the entire disk.. 
I would like to undo this now however, and am wondering if anyone can provide some advise as to how this might be accomplished without a format and reinstall.

any ideas would be greatly appreciated.

---

### Post by deadflowr on 2018-07-30
18.04 is now released. Development is over.
Start a new thread, probably here: [https://ubuntuforums.org/forumdisplay.php?f=331]("https://ubuntuforums.org/forumdisplay.php?f=331")
Thread closed

---

