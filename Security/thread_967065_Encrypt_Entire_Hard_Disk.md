---
title: "Encrypt Entire Hard Disk?"
date: 2008-11-01
forum: Security
---

### Post by CarbineReloaded on 2008-11-01
I'm running Ubuntu Ultimate Edition 1.9 on a Dell Inspiron Laptop.... I mainly use this laptop for travel, as it isn't exactly the most powerful system around.


I have a lot of confidential business information that I keep on the system, and I'd like to protect the data in the event that the laptop is lost.

I realize nothing is fool proof, but I'd like to keep the average fool away from my data.


I currently have the hard disk "password protected" which IMO gives a false sense of security, there seem to be too many apps out there from dell, that'll un-do this password protection, and let the data be accessed.

This has lead me to seek some form of entire disk encryption, what would you recommend?  I really do not want to have to go through backing everything up and reinstalling everything (encrypting on install)... there has to be a way to safely do this after a system is configured.

---

### Post by hyper_ch on 2008-11-02
simplest and safest way is a full disk encryption and the requires a reinstall of everything.

If you don't like that, you could still use truecrypt (as an example) and create an encrypted file containt in which documents are stored. That encrypted file container can then be mounted. Somewhere.

e.g. you could create like a 10GB file container that contains all of your home folder. Once you booted up, you could then mount that truecrypt container as /home and then personal settings and stuff in there is encrypted.

However due to the nature of a journaled filesystem and also because of temporary files you might have copies someplaces else in your system for a while.

If you don't want to reinstall, I think having a truecrypt container for home that you mount after boot up would be the second best option.

Instead of using all of home you could also just store individual documents in an encrypted container. However the chance of not protecting all important data is even larger.

---

### Post by HermanAB on 2008-11-02
If you run a windows PC, then it is necessary to encrypt the entire hard disk, since no-one knows where Windows programs put stuff.

However, in a Linux system, things are well controlled, so you only need to encrypt /swap, /tmp and /home. Nowadays /tmp is usually RAM based using tmpfs, so you only need to encrypt /swap and /home. Encrypting the whole disk is quite pointless and makes the system slower.

Cheers,

Herman

---

### Post by hyper_ch on 2008-11-02
herman: full disk encryption doesn't make the system slower... at least not during normal operations... only when you read/write huge chunks of data you will notice slower speeds...

and it is not quite pointless...

what about /var/www? /var/lib/mysql? /media? ....?

if you know what exactely needs to be encrypted, go ahead... having full disk encryption will make sure that you don't forget to encrypt anything ;)

---

### Post by HermanAB on 2008-11-02
A server with full disk encryption is about 3% slower than without - in my own tests.  I know some idiotic programs (notably MySQL) like to store data in /var, but you should use soft links to map them to /home or somewhere else that is encrypted.  That much stands to reason.

The point is that ordinary programs will not write stuff outside of their allocated areas - unlike Windows a Linux system is generally well behaved. Since Linux is Free and available on public mirrors, there is no point in encrypting /bin, /sbin, /lib, /usr or any of the ephemerals like /sys, /proc and /dev.  Doing so is an unnecessary complication.

Consequently, applying encryption  to a Linux system is a much simpler and more efficient matter than doing the same on a Windows PC.

---

### Post by hyper_ch on 2008-11-02
yet if you don't know about mysql and the data won't be encrypted... as I said before, if you don't really know what you're doing, go for full disk encryption and 3% is not a big difference...

---

### Post by HermanAB on 2008-11-02
Well, gee - if you don't know where MySQL stores its data then you are most likely not using it and don't have to worry about it.
:)

---

### Post by hyper_ch on 2008-11-03
many people use mysql and have no clue where the data is being stored...

furthermore you might also want to have your logs encrypted... just depending on your paranoia levels there can be materials in there that could be used against you. Same goes for the installed software...

As I said before: If you exactely know what you'e doing, then you can just encrypt the thing essential to you. However if you don't know or if you are just lazy then encrypt the whole thing ;)

---

### Post by djbon2112 on 2008-11-25
Sorry to hijack, but I just want to ask, HOW do you encrypt your entire Linux (Ubuntu Studio in my case) system, or how to you encrypt things like /swap and /home that are mounted on boot? Is there a guide or tutorial out there on what to do?

---

### Post by rhcm123 on 2008-11-25
> **djbon2112 said:**
> Sorry to hijack, but I just want to ask, HOW do you encrypt your entire Linux (Ubuntu Studio in my case) system, or how to you encrypt things like /swap and /home that are mounted on boot? Is there a guide or tutorial out there on what to do?

you have to create a lvm partition on install

---

### Post by teddks on 2008-11-25
> **djbon2112 said:**
> Sorry to hijack, but I just want to ask, HOW do you encrypt your entire Linux (Ubuntu Studio in my case) system, or how to you encrypt things like /swap and /home that are mounted on boot? Is there a guide or tutorial out there on what to do?

Download the "Alternate Install" CD, and when you come to the partitioning part, just select "Create encrypted LVM" or something like that. You can also do that manually by taking all the drive space you want for the crypt'd partitions, making an encrypted volume, then making an LVM from that. From there, you create logical volumes for your individual filesystems. Simple really :)

---

### Post by djbon2112 on 2008-11-26
> **teddks said:**
> Download the "Alternate Install" CD, and when you come to the partitioning part, just select "Create encrypted LVM" or something like that. You can also do that manually by taking all the drive space you want for the crypt'd partitions, making an encrypted volume, then making an LVM from that. From there, you create logical volumes for your individual filesystems. Simple really :)

Alright, I was stuck on this point (found a guide after I posted!) because I couldn't create more than one partition in the encrypted partition. So I go create Physical Volume for Encryption, then inside than a Physical Volume for LVM, then create my partitions there? Or would it be better to only encrypt certain directories, and if so, which ones (besides /home, obviously)?

---

### Post by hyper_ch on 2008-11-26
[http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04](http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04)

---

### Post by teddks on 2008-11-26
> **djbon2112 said:**
> Alright, I was stuck on this point (found a guide after I posted!) because I couldn't create more than one partition in the encrypted partition. So I go create Physical Volume for Encryption, then inside than a Physical Volume for LVM, then create my partitions there? Or would it be better to only encrypt certain directories, and if so, which ones (besides /home, obviously)?

It's best to encrypt everything, so that no matter where idiotic programs write things to, you're safe.

---

### Post by hyper_ch on 2008-11-26
> **teddks said:**
> It's best to encrypt everything, so that no matter where idiotic programs write things to, you're safe.

Best depends on the metrics applied to do an evaluation... ;)

---

### Post by djbon2112 on 2008-11-26
> **hyper_ch said:**
> [http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04](http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04)

Yea, that's the one I found >.< Changing my google search terms often helps!

> **teddks said:**
> It's best to encrypt everything, so that no matter where idiotic programs write things to, you're safe.

I think I'll do this. But then how do you get around LILO not installing? It may have been a fluke, but when I encrypted the entire root (except /boot of course which is on a separate partition), following that guide, I only had the option to install LILO, and only to the encrypted partition, and it failed. Ideas?

If it helps, I'm trying to install Ubuntu Studio 8.10 x86_64

---

### Post by mrnaughty on 2008-11-26
why not use **TrueCrypt** from [www.truecrypt.org?](www.truecrypt.org?) 
Best thing since toaster!

---

### Post by djbon2112 on 2008-11-26
> **mrnaughty said:**
> why not use **TrueCrypt** from [www.truecrypt.org?](www.truecrypt.org?) 
Best thing since toaster!

It only supports system-disk encryption for Windows.

---

### Post by hyper_ch on 2008-11-26
> **djbon2112 said:**
> Yea, that's the one I found >.< Changing my google search terms often helps!

Anything did not work with that howto?

---

### Post by djbon2112 on 2008-11-26
> **hyper_ch said:**
> Anything did not work with that howto?

It worked as far as I could tell, but I did run into problems installing the bootloader... it would only let me install LILO (not GRUB) and doing so failed as it would only give me the option to install to the encrypted partitions and not my /boot partition. Since this step wasn't covered in the guide I don't know if it's a fluke or what.

---

### Post by hyper_ch on 2008-11-26
> **djbon2112 said:**
> It worked as far as I could tell, but I did run into problems installing the bootloader... it would only let me install LILO (not GRUB) and doing so failed as it would only give me the option to install to the encrypted partitions and not my /boot partition. Since this step wasn't covered in the guide I don't know if it's a fluke or what.
that's strange... I wrote that little howto... but I didn't even know that LILO is on the ubuntu install cds.... hmmm....

---

### Post by djbon2112 on 2008-11-26
> **hyper_ch said:**
> that's strange... I wrote that little howto... but I didn't even know that LILO is on the ubuntu install cds.... hmmm....
Then I thank you for the excellent how-to! I'm trying another virtual image on another computer using the 32-bit Ubuntu Studio to see if I can replicate the issue.

---

### Post by jaygo on 2008-12-28
I was having the same issue while trying to install 8.10 with RAID + encryption.
> "The LILO program needs to be installed to make your new system bootable..."

After some testing & research, it appears to be an issue with using XFS for the main file system and ext3 for the boot. XFS requires LILO and because I formatted the boot partition with ext3 it was not available to install LILO.

---

