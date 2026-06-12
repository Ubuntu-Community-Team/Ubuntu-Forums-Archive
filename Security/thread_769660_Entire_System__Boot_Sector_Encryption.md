---
title: "Entire System / Boot Sector Encryption"
date: 2008-04-26
forum: Security
---

### Post by yeehi on 2008-04-26
Hello!

Is there a good "How To" on encrypting an entire installation, including the boot sector?

---

### Post by kevdog on 2008-04-26
You need to install from the alternate CD and choose the LUKS encryption method.  I wish I could recall all the details, however its is extremely easy and self explanatory.

I'm not sure if it encrypts the boot sector however.  Hopefully someone else will be able to chime in on this.

---

### Post by yeehi on 2008-04-26
[http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)

On the webpage above, I couldn't see MD5sum or SHA information for the Ubuntu alternative iso file.

Where is this information published, so that I can check the integrity of the file?

---

### Post by Patsoe on 2008-04-26
> **kevdog said:**
> You need to install from the alternate CD and choose the LUKS encryption method.  I wish I could recall all the details, however its is extremely easy and self explanatory.

I'm not sure if it encrypts the boot sector however.  Hopefully someone else will be able to chime in on this.

No that will not encrypt the boot sector. It actually also requires an unencrypted /boot partition.

If you want to have even the MBR encrypted, you probably need hardware encryption tools.

---

### Post by twisted_steel on 2008-04-27
> **yeehi said:**
> [http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)

On the webpage above, I couldn't see MD5sum or SHA information for the Ubuntu alternative iso file.

Where is this information published, so that I can check the integrity of the file?

There is a MD5SUMS file on the page you listed that lists ubuntu-8.04-alternate-i386.iso and ubuntu-8.04-alternate-amd64.iso with their respective hashes.  There is also a GPG signature file for the MD5SUMS.

---

### Post by kevdog on 2008-04-27
dm-crypt/LUKS DOES NOT encrypt the boot sector.  In fact something needs to be unencrypted unless its integrated with the bios.

---

### Post by yeehi on 2008-04-27
> **twisted_steel said:**
> There is a MD5SUMS file on the page you listed that lists ubuntu-8.04-alternate-i386.iso and ubuntu-8.04-alternate-amd64.iso with their respective hashes.  There is also a GPG signature file for the MD5SUMS.

The page is meant to have links to md5sums but I only get the following error message when I follow the links:

> [I]ERROR
Service Unavailable

The requested service is unavailable.

Please try again later.[/I]

I did find the hashes here, though :)

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by sunbird on 2008-04-27
There is [this how-to]("http://ubuntuforums.org/showthread.php?p=4604645"), but as previous posters have said, luks does not encrypt /boot.

---

### Post by Chayak on 2008-04-27
Like it has been said, the boot partition is not encrypted but there's no reason you can't stick your /boot partition on a usb thumb drive if your computer can boot from usb.

---

### Post by kevdog on 2008-04-27
Do you actually have a working setup that can boot from usb?  Id love to try this, however something tells me there is going to be some editing of some grub files and fstab files.  I'd like to try if you have a How-To.

---

### Post by yeehi on 2008-04-28
Booting from thumbdrive is a delicious idea :)

I will not try it this time around, one reason being that I might lose the thumbdrive.

I need help with the installation though, because it is beyond me. Please help me out with the options I should pick.

This is the set up. I have 2 hard disks, A) large, B) small.

I want the / partition and /boot partition and swap space on the small drive B), and /home on the dedicated large hard disk A).

I would definitely like A) encrypted. Maybe getting B) encrypted too would be useful - i don't know.

I don't know what to select from the partition manager during installation - entire disk encryption lvm... that place. 

How do I ensure that my disk is encrypted and that I have the / /boot swap and /home in the right place?

please help! Thank you :)

---

### Post by hyper_ch on 2008-04-28
if you want to use the large disk as seperate /home then I would

(1) unplug that large disk
(2) fully encrypt the small one with the installer
(3) afterwards seperately encrypt the large disk
(4) manually add entry to crypttab and fstab for the large disk and make use of keyfiles that reside on the small disk

---

### Post by Patsoe on 2008-04-28
> **yeehi said:**
> This is the set up. I have 2 hard disks, A) large, B) small.

I want the / partition and /boot partition and swap space on the small drive B), and /home on the dedicated large hard disk A).

I would definitely like A) encrypted. Maybe getting B) encrypted too would be useful - i don't know.

You also want the swap space encrypted because it contains data you're working on, fragments of /home that is. 
As for encrypting /, that only makes sense if
[LIST]
[*]you don't want people to know what software is installed (can't imagine, but oh well) 
[*]or you are somehow afraid people will fiddle with your executables (but then life becomes very complicated) 
[*]or you can't be bothered to make a distinction (that's what applies to me)
[/LIST]

> I don't know what to select from the partition manager during installation - entire disk encryption lvm... that place. 

You'll want to do a manual partitioning, if you go with the guided option then everything ends up in one big encrypted logical volume.

I have a walk-through of manual partitioning on my blog, which doesn't do exactly what you want to end up with, but at least you can see how the partitioning works there. You don't necessarily need LVM, you could also just have plain partitions encrypted if that's what you prefer.

---

### Post by Patsoe on 2008-04-28
> **hyper_ch said:**
> if you want to use the large disk as seperate /home then I would

(1) unplug that large disk
(2) fully encrypt the small one with the installer
(3) afterwards seperately encrypt the large disk
(4) manually add entry to crypttab and fstab for the large disk and make use of keyfiles that reside on the small disk

That sounds like a nice plan, otherwise you end up entering several passphrases at boot time. I think you can skip point (1) though unless you really get confused by multiple disks in your partitioning menu :)

---

### Post by hyper_ch on 2008-04-28
> **Patsoe said:**
> (1) though unless you really get confused by multiple disks in your partitioning menu :)
I accidentally formatted once the wrong disk... I only had two in there... a 60 GB and 120 GB and I did partition/format the 120 GB one although I knew it was the wrong one... I just was too confident and went ahead...

---

### Post by Patsoe on 2008-04-28
> **hyper_ch said:**
> I accidentally formatted once the wrong disk... I only had two in there... a 60 GB and 120 GB and I did partition/format the 120 GB one although I knew it was the wrong one... I just was too confident and went ahead...

Yeah, on second thought I wouldn't trust myself with that either...

---

### Post by HermanAB on 2008-04-28
Note that there is not much point in encrypting /, /boot and /usr, since the information on those partitions is public knowledge anyway and all that encrypting those will do is make the machine a tiny little bit slower.

---

### Post by Patsoe on 2008-04-28
> **HermanAB said:**
> Note that there is not much point in encrypting /, /boot and /usr, since the information on those partitions is public knowledge anyway and all that encrypting those will do is make the machine a tiny little bit slower.

Generally I agree, but there's the scenario where you sometimes leave your laptop lying around (think student dorm) and don't want people messing with it. Everyone could boot in single user mode and replace some stuff in /bin to have a laugh... but not if everything below / is encrypted.

(I'm not so paranoid that I'd care, but paranoid enough to come up with the idea... :))

---

### Post by kevdog on 2008-04-30
Anyone find an example of how to boot from a USB stick with the boot sector on it?

---

### Post by hyper_ch on 2008-04-30
have a look at how to set your usb pen drive to boot with DSL. Basically you'll have to format it, put syslinux on it and then extract the dsl content to it.

So I'd say it would go like this:

(1) Format the drive to Fat32 (I think)
(2) Put Sys Linux on it
(3) Copy your /boot folder to the pendrive
(4) Alter your bios to boot from the pendrive

I will try it in the next couple of days.

---

### Post by Patsoe on 2008-04-30
> **hyper_ch said:**
> 
(1) Format the drive to Fat32 (I think)

Well with a normal hdd install the /boot partition is ext3 formatted. I'm not sure what DSL's boot loader is configured for though.

---

