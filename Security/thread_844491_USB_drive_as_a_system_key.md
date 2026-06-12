---
title: "USB drive as a system key"
date: 2008-06-29
forum: Security
---

### Post by TorchlightJay on 2008-06-29
Hello,
   I think I have heard of this technology but am not sure where to start with it. 

Basically, is there a way to lock/encrypt a system and have the key that unlocks/unencrypts the sysetm on a USB drive? i want to be able to secure my hard drives and all information to where the only way someone can actually access it is with this USB drive. 

Any ideas?

---

### Post by Tubes6al4v on 2008-06-29
I don't want to re-format my hard drive, so I have not tried any of these. I am waiting to learn more so I can do a combination of a drive key and passphrase.



[Here is how to install /root encrypted on your USB Drive]("http://ubuntuforums.org/showthread.php?t=783910&highlight=usb+encrypted+boot")
[URL="http://ubuntuforums.org/showthread.php?t=843571"]
Here is a Keyfile on your USB[/URL]
[URL="http://ubuntuforums.org/showthread.php?t=840031"]
And finally, how to install key file on an SD card through Live CD[/URL]




I hope this helps my brother.

---

### Post by hyper_ch on 2008-06-30
yes, you can do that... however you

(1) need to create an encrypted system - this is easiest done with fresh installation
(2) add a key and make the system boot from it
or
(3) you could also setup a limited shell into which you can SSH and then enter password for unlocking the drive(s)

---

### Post by TorchlightJay on 2008-06-30
Sounds good. The only problem i have had encrypting the partition is when you have to reformat the system. I like to have multiple patitions and when i choose the encrypted filesystem, it takes over the whole hard drive. any thoughts

---

### Post by kevdog on 2008-06-30
Get an additional hard drive??

---

### Post by TorchlightJay on 2008-06-30
Hmm, so you are suggesting that i get another drive and setup the encrypted drive on that one and get a second one and setup the rest of the stuff on drive two? Seems like too much trouble, any other ideas to encrypt the partition other than doing it from boot?

---

### Post by hyper_ch on 2008-07-01
> **TorchlightJay said:**
> Sounds good. The only problem i have had encrypting the partition is when you have to reformat the system. I like to have multiple patitions and when i choose the encrypted filesystem, it takes over the whole hard drive. any thoughts

can you say that again? I don't get what you mean

---

### Post by TorchlightJay on 2008-07-01
Well I know that when you install Ubuntu from the Alternate CD, you can choose to encrypt the drive. When you do that, it reformats the whole partition and encrypts it to install just Ubuntu. Now I do multiple partitions on my drive. I am starting to use LVM as well. I use them for storage and for different Linux distros. 

Now this is inconvenient for me if the whole drive is formatted. Is there anyway to encrypt a drive after you have partitions setup? If you can't do that, can you encrypt a single partition with the Ubuntu Installation process?

---

### Post by hyper_ch on 2008-07-02
if the drive is not encrypted, you can encrypt it later and not format it...

however if it's once encrypted, you can unlock it during install process and install another os in the encrypted drive.

---

### Post by TorchlightJay on 2008-07-02
So you are saying that I can do the whole encryption thing on the whole drive and then when it's time to install a new OS or for whatever reason create another partition, I can unlock the drive and then mess with the partitions as I want?

How do I unlock the parition to intsall another distro or use the partition tables?

---

### Post by hyper_ch on 2008-07-02
> **TorchlightJay said:**
> how do I unlock the parition to intsall another distro or use the partition tables?

that's a bit challenging... easiest to setup would be to have at least three partitions:

/boot
/
/home

for that you don't really need to "uncrypt" the root partition upon a new installation... all important config files and personal data is in /home... you can then install a new fully encrypted system and once done, you can then just mount the previously encrypted /home folder into the newly installed system.

---

### Post by TorchlightJay on 2008-07-03
Cool. so how does that work though. Ubuntu always wants to encrypt the whole drive and not let me make partition. How do i create individual encrypted partitions on the same hard drive?

---

### Post by hyper_ch on 2008-07-03
select manual partitioning ;)

(1) make a partition for swap (but don't format it or anything - there's a bug with manual setup and encrypted swap)

(2) make a boot partition (about 100mb - depending on how many kernels you want to have stored within there) and make it bootable e.g.
[IMG]http://www.sjau.ch/bug_231451/01boot.png[/IMG]

(3) create a root partition --> set "use as" to "pyhsical volume for encryption" e.g.
[IMG]http://www.sjau.ch/bug_231451/03root.png[/IMG]

(4) create a home partition --> as filesystem also encrypted [if you reinstall, leave that away of course]

and then, when you are in the main partition overview again, select to configure encrypted volumes:
[IMG]http://www.sjau.ch/bug_231451/04configure.png[/IMG]

once you set them up, in the main partition overview you will get new devices... assign then the mount point ("/" and "/home" and select Ext3 as filesystem...)....

Best if you try this first in a virtual machine...

So later, if you want to reinstall your system, you will just overwrite the boot and "/" partition again... you will not touch the swap and "/home" one. Then you setup the system again... and once setup, you will just mount the "/home" partitiong into the filesystem by editing accordingly /etc/crypttab and /etc/fstab

---

