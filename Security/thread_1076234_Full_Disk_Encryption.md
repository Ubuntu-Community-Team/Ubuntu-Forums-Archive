---
title: "Full Disk Encryption"
date: 2009-02-21
forum: Security
---

### Post by john_es on 2009-02-21
I was going to encrypt my Ubuntu 8.10 machien using the following guide:

[http://74.125.47.132/search?q=cache:T4va1G_-HIgJ:mazeoflies.com/articles/2008/06/09/ubuntu-hard-drive-encryption-with-external-key+http://mazeoflies.com/articles/2008/06/09/ubuntu-hard-drive-encryption-with-external-key&hl=en&ct=clnk&cd=1&gl=us](http://74.125.47.132/search?q=cache:T4va1G_-HIgJ:mazeoflies.com/articles/2008/06/09/ubuntu-hard-drive-encryption-with-external-key+http://mazeoflies.com/articles/2008/06/09/ubuntu-hard-drive-encryption-with-external-key&hl=en&ct=clnk&cd=1&gl=us)

1.) Is this the best way to go for full disk encryption? Reason I ask is that there does not seem to be a definitive guide as to how to do this.
2.) Is there a way to encrypt the entire disk without wiping the entire drive first like this guide shows?
3.) Is there a way to setup the machine so that there is a dummy password that allows someone to login but not access the encrypted machine?

Thanks....
John

---

### Post by Tubes6al4v on 2009-02-21
I have only been playing with Linux for a year, so I will try to answer you questions, but others will be able to confirm.

1) That guide seems to be focused on using key files from a USB stick. Personally, I think that this should only be used as a secondary authentication method. Think of it this way. If you keep your USB stick in your computer bag, if someone steels the bag, they have the key to the OS. So I suggest that you just stick with a standard pasphrase. If you want something long and relatively easy, I find poetry to work quite well.

If you do choose to use key files, make sure you back up the key file on a remote server or drive. That way if the usb stick gets corrupted you can just copy it from backup to a new usb and still get access.

IMO, the best way to start using encryption is to do it straight with the Alternate CD. It is actually relatively easy to install it to a drive. When you get to more complex configurations (multiple operatings systems on the same drive), you should use the manual configuration in the Alternate CD.


2) As of yet, I do not know of any way to encrypt the system drive with the information in place. Truecrypt can do this with Windows, but requires you to have lots of free space on that partition, and takes forever. Instead, you can backup your data, install the encrypted system over what you had, then just restore from that backup. Note: It is a bit more complicated to restore to an encrypted drive than unencrypted, but not too much.


3) You could create two operating systems, and have it default to the unencrypted one. But they would still be able to see that you had an encrypted drive on the system. The dummy system wouldn't really do much but eat up space. They can't access your drive without the passphrase anyway.

What I have been interested in is Hidden Operating Systems. There does not seem to be too much of a push for this, as can be understood, since it will inevitably help some criminals. Truecrypt can do this with Windows (though, after 3 tries, I have yet to succeed with it). Some proof-of-concept systems have been adapted for Linux, but none exist in the wild.

---

### Post by bodhi.zazen on 2009-02-21
> **john_es said:**
> I was going to encrypt my Ubuntu 8.10 machien using the following guide:

[http://74.125.47.132/search?q=cache:T4va1G_-HIgJ:mazeoflies.com/articles/2008/06/09/ubuntu-hard-drive-encryption-with-external-key+http://mazeoflies.com/articles/2008/06/09/ubuntu-hard-drive-encryption-with-external-key&hl=en&ct=clnk&cd=1&gl=us](http://74.125.47.132/search?q=cache:T4va1G_-HIgJ:mazeoflies.com/articles/2008/06/09/ubuntu-hard-drive-encryption-with-external-key+http://mazeoflies.com/articles/2008/06/09/ubuntu-hard-drive-encryption-with-external-key&hl=en&ct=clnk&cd=1&gl=us)

1.) Is this the best way to go for full disk encryption? Reason I ask is that there does not seem to be a definitive guide as to how to do this.

Personally I do not use keys, otherwise yes.

This how-to is easier to follow :

[http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml)

> 2.) Is there a way to encrypt the entire disk without wiping the entire drive first like this guide shows?Well, that is the definition of full encryptino, no ?. You can install Ubuntu into a partition. The alternate installer will then use LVM and LUKS to then make / and swap.

You can then use other partitions for what you will, including other OS. 


> 3.) Is there a way to setup the machine so that there is a dummy password that allows someone to login but not access the encrypted machine?

Thanks....
JohnSee above. Ubuntu also offers the option of an encrypted home, which may be what you want. An encrypted home is automagically decrypted when you log in, otherwise yoru personal information is encrypted. This may be sufficinet for what you want.

---

### Post by Warmy on 2009-03-02
> **bodhi.zazen said:**
> 
[http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml)


Any suggestions on how to do RAID-5 with encryption?  I did the alternate CD install, then went through the manual drive setup to get the raid arrays setup.  I'm using 4 disks in RAID-5.

After playing with ubuntu, playing with all kinds of settings, software, etc, i'm ready for format and do it again - however I'd like to encrypt the entire system.

I know I need to create a couple MD devices.  Here's what I have

/dev/md0 RAID 1 - about 50 MB for boot since grub can't handle RAID5.

/dev/md1 RAID 5 - for /

/dev/md2 RAID 10 for swap


Should I just run the alternative CD installer again and just use md0 for the drive device for LVM?

-Mitch

---

### Post by bodhi.zazen on 2009-03-02
Yes, you will need to use the alternate CD. I do not think you can put /boot on the raid, not sure about that.

Set up the raid and define the root partition. The alternate CD should then offer you the option to encrypt it.

---

### Post by ushills on 2009-03-03
It was mentioned above that encrypted home may be a good solution.

What is the best method for encrypting eaxh users home folder so that it is only unlocked when they log-in.  

Is at also possible to have all the home folders also owned and opened by some admin user so that a offsite backup can take place.  this is necessary in my case as an encrypted backup is made to Amazon's S3 servers nightly and i would need the folders would need to unlocked for this.

---

### Post by Kobalt on 2009-03-04
> **ushills said:**
> What is the best method for encrypting eaxh users home folder so that it is only unlocked when they log-in.

I have described a way to do this here : [http://www.nschirrer.com/encrypted-home-directory/](http://www.nschirrer.com/encrypted-home-directory/)
I think it's quite simple and efficient.  

> Is at also possible to have all the home folders also owned and opened by some admin user so that a offsite backup can take place.  this is necessary in my case as an encrypted backup is made to Amazon's S3 servers nightly and i would need the folders would need to unlocked for this.

I doubt, but I'm no expert to assure you it's impossible. 
The method I describe, using eCryptfs, uses a per user encryption : that makes data stored inside the encrypted Home folder impossible to read to any other user (including root).

But I guess you could backup encrypted data. It just won't be readable straight from the backup directory...

---

### Post by ushills on 2009-03-04
> **Kobalt said:**
> But I guess you could backup encrypted data. It just won't be readable straight from the backup directory...

Does this method encrypt each file or the entire directory as a single file.

I would be quite happy to have lots of encrypted files backed up to Amazon, one entire changing file would be too much bandwidth.

---

### Post by Kobalt on 2009-03-04
It encrypts files and filenames individualy.

---

### Post by HermanAB on 2009-03-05
LUKS allows you to have multiple passwords for a partition.

Note that full disk encryption is a bit of a misnomer, since you always need to leave a plain text partition to boot from.  This partition can be small (/boot only) or large (/).  

For most people, encrypting /home and providing a different password for each user is good enough.  If your machine is a laptop and you use suspend/hibernate, then you also need to encrypt /swap or place a swap file in /home.  If you run a database or some such, ensure that the data is stored in /home as well.  Even the government use this method.

An alternative, is to buy a self encrypting hard disk - available from Seagate and others.

Cheers,

Herman

---

