---
title: "How to encrypt whole file system?"
date: 2009-06-02
forum: Security
---

### Post by uupreti on 2009-06-02
I installed fresh copy of Ubuntu using manual partition. I did well and now I am wondering if there is any way to encrypt my whole file system with some sort of encryption algorithm. I have heard about **truecrypt** but never used it. Do you guys have something to say about it or any other better option for me?


After encrypting my file system, can anyone login using single user mode and change my user or root password??

---

### Post by rookcifer on 2009-06-02
Now that you have Ubuntu installed, you can't encrypt the whole file system.  You will have to reinstall.  But this time you must use the alternate install CD.  Once you have that, then follow the instructions [here.]("http://oei.yungchin.nl/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/")

And no, if the filesystem is encrypted no one can boot the system without the encryption key password.  If the system is already running, it will work as it would without encryption as far as other security measures are concerned.

---

### Post by uupreti on 2009-06-02
Ok but I'm just wondering if normal ubuntu desktop CD will work or I have to get Alternate install CD?

---

### Post by rookcifer on 2009-06-03
> **uupreti said:**
> Ok but I'm just wondering if normal ubuntu desktop CD will work or I have to get Alternate install CD?

You need the alternate CD (that is unless you use use some other livecd and set-up encryption from the command line).  But the easiest way is just to use the alternate CD.

---

### Post by uupreti on 2009-06-03
OH ok I got it now that Alternate CD is used when your graphics card does not support for installation. I read through the guide from your link. And it seems it's encryption technique provided by Ubuntu itself (Which is LVM encryption --I forgot the exact word). 

Now my next question is, I am hearing here and there about **truecrypt**. What is this all about? Is this about encrypting filesystem or specific data folder. Can we do after fresh installtion of Ubuntu?

I also looked at their website but I thought it would be easy if I get some basic preview from user who already went through it. 

Thanks.

---

### Post by unutbu on 2009-06-03
Truecrypt provides a way to encrypt either individual directories or a partition.
I believe one attraction of Truecrypt is that it is compatible with both Windows and Linux. One detraction however is its license:

[http://fedoraproject.org/wiki/ForbiddenItems#TrueCrypt](http://fedoraproject.org/wiki/ForbiddenItems#TrueCrypt)
> 
The TrueCrypt software is under an extremely poor license, which is not only non-free, but actively dangerous to end users who agree to it, opening them to possible legal action even if they abide by all of the licensing terms. Fedora made extensive efforts to try to work with the TrueCrypt upstream to fix these mistakes in their license, but was unsuccessful.

Fedora Suggests: Avoid this software entirely. 

Here are a few open-source alternatives:
[list]
[*] You can do LUKS "whole-disk" encryption using the alternate CD
[*] Use eCryptfs to encrypt a filesystem (i.e. a directory).
Dustin Kirkland, an Ubuntu developer is actively working on integrating the ability to use eCryptfs with the default Ubuntu installation. It is very easy to setup and use, even from the command-line. (See [http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)) This page explains some weaknesses in using an encrypted filesystem compared to whole-disk encryption: 
[list]
[*] [http://ecryptfs.sourceforge.net/ecryptfs-faq.html#deployment](http://ecryptfs.sourceforge.net/ecryptfs-faq.html#deployment)
[*] [http://ecryptfs.sourceforge.net/ecryptfs-faq.html#compare](http://ecryptfs.sourceforge.net/ecryptfs-faq.html#compare)
[/list]
[*] Use EncFS to encrypt a filesystem (i.e. a directory) (See [http://www.movingtofreedom.org/2007/02/21/howto-encfs-encrypted-file-system-in-ubuntu-and-fedora-gnu-linux/](http://www.movingtofreedom.org/2007/02/21/howto-encfs-encrypted-file-system-in-ubuntu-and-fedora-gnu-linux/) and [http://ubuntuforums.org/showthread.php?t=148600](http://ubuntuforums.org/showthread.php?t=148600))
[/list]

---

### Post by 3startuna on 2009-06-03
this mght be a stupid question but doesnt this happen automatically anyway?

The entire file system is owned by the "root" user

---

### Post by HermanAB on 2009-06-03
Easy:
Install luks-tools and run the gnome-luks-format wizard.

---

### Post by bodhi.zazen on 2009-06-03
> **3startuna said:**
> this mght be a stupid question but doesnt this happen automatically anyway?

The entire file system is owned by the "root" user

That is not the same as encryption.

With a non-encrypted installation one has easy and full access to all the data on the system with a live CD.

Be encrypting the installation they can not access the data or make changes to the system (other then re-installing or other destructive actions).

---

### Post by rookcifer on 2009-06-03
Hopefully one of these days Ubuntu will do what Fedora has been doing for a couple of years now -- offer to encrypt the partitions during install.  With Fedora it's as simple as clicking "encrypt" on each partition, and Fedora sets them up automatically in a LUKS LVM configuration.

---

### Post by bodhi.zazen on 2009-06-03
> **rookcifer said:**
> Hopefully one of these days Ubuntu will do what Fedora has been doing for a couple of years now -- offer to encrypt the partitions during install.  With Fedora it's as simple as clicking "encrypt" on each partition, and Fedora sets them up automatically in a LUKS LVM configuration.

Indeed Ubuntu offers several options for encryption.

---

### Post by walterav on 2009-06-04
I have a question.

Can I read a encrypted system partition, If I have the password, but not a working computer anymore?

So what I mean is, you installed ubuntu on "computer X", you did the alternate encryted installation. Maybe because of some error, ubuntu doesn't boot anymore..."maybe..." or computer X is dead.
Than you just swap the whole harddisk to "computer Y".

What than?
Howdo do I mount the encrypted volume, so I can access my data in a other machine or during a live-cd session?

---

### Post by unutbu on 2009-06-04
walterav, if computer X dies, but the hard drive is okay, then you could install the hard drive in computer Y, and set the BIOS to boot the hard drive. It should work without any changes.

Below are instructions on how to manually mount a LUKS-encrypted partition using the alternate or LiveCD:

If you have a LUKS-encrypted partition (what you would get from using the alternate Ubuntu installation CD), then:

[list]
[*] Boot the alternate CD
[*] Get to a terminal prompt and type
```
sudo modprobe dm-crypt  # maybe not necessary.
sudo cryptsetup luksOpen /dev/sdXY sdXY_crypt
```
[/list]

Change "sdXY" to the correct device name of the LUKS-encrypted partition.
The last command will decrypt /dev/sdXY and put the decrypted partition at 
/dev/mapper/sdXY_crypt.

You can then treat /dev/mapper/sdXY_crypt as you would a normal device.

For example, if you have an ext3 filesystem inside the sdXY, then you could mount it with
the command
```

sudo mount /dev/mapper/sdXY_crypt /mnt
```

Or, if you have an LVM inside sdXY, then you could access the LVM logical volumes with
```

sudo vgscan --mknodes
sudo vgchange -ay       # makes the logical volumes known to the kernel
```

The kernel will create block devices in /dev/mapper -- one block device for each logical volume. If the volume group is called "vol_group" and the logical volume is called "logical_vol", then the block device would be located at /dev/mapper/vol_group-logical_vol.

You can then mount the logical volume like this:
```

sudo mount /dev/mapper/vol_group-logical_vol /mnt
```

If you have a LiveCD instead of an alternate CD, then you would need a network connection so you could install the lvm2 and cryptsetup packages before running the above commands:

```
sudo apt-get install lvm2       # if you have an LVM inside the LUKS-encrypted partition
sudo apt-get install cryptsetup # to decrypt LUKS
```

See [http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html](http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html)

---

### Post by walterav on 2009-06-05
Thanks a lot for this complete answer, 
I'll try it right now with my livecd in a virtual machine.

I also have two other questions:

Is 'hibernate' instead of 'suspend to ram' safe for sleep 'encryption etc'?

Or can I use suspend to ram, and decrypt the ram before it sleeps, so therefor it is not possible to gain access to the key... "or is it possible to load a program after shutdown that fills the ram memory with 0 or 1 before it shutdown" So no possibility of sniffing the key from the ram after the machine turned off?

I might be paranoid but just want to know the limits...

---

### Post by walterav on 2009-06-05
Did use the livecd "mint 7 gloria"

I was able to:
apt-get install lvm2 cryptsetup
able to mount the encrypted partition
able to read and write
Therefor your guide works perfect!

I was not able to:
mount the homedir, because that one was also encrypted during install...
So when entering /home/user/ all seems empty instead for a ACCESS-Your-private-data.desktop file.
I followed the directions on this page:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)
It mounts something but what I read in there looks all scrambled...

any thoughts?

---

### Post by unutbu on 2009-06-05
walterav, thanks for so many wonderful questions. I don't know the answer to all of them, so hopefully someone with more knowledge will step in. 

According to [http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/), the encrypted home directory is located at /var/lib/Ecryptfs/user_name/

and so the command to mount the encrypted filesystem should be

```
sudo mount -t ecryptfs -o key=passphrase,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_passthrough=no,ecryptfs_enable_filename_crypto=yes /var/lib/Ecryptfs/user_name/ /home/user_name/
```

assuming you used the default options when setting up the ecryptfs.

Otherwise, try
```

sudo mount -t ecryptfs /var/lib/Ecryptfs/user_name/ /home/user_name/
```

(you'll just have to answer a few more questions.)

I don't know what the "state-of-the-art" is regarding hibernate,suspend and encryption. As far as I know, you give up the ability to hibernate and suspend if you use LUKS.
Some clever person might certainly have found a way to make it work; I just don't know about it.

I suppose there should be some way to write 0's to RAM, but I don't know how to do that either! I believe if you can keep the hackers with cans of freezing agent away from your machine for about 2 minutes after powering off, then you should be okay. (See [http://citp.princeton.edu/memory/](http://citp.princeton.edu/memory/)).

---

### Post by walterav on 2009-06-06
> **unutbu said:**
> 

I suppose there should be some way to write 0's to RAM, but I don't know how to do that either! I believe if you can keep the hackers with cans of freezing agent away from your machine for about 2 minutes after powering off, then you should be okay. (See [http://citp.princeton.edu/memory/](http://citp.princeton.edu/memory/)).

Yes, that movie made me go paranoia :p, but it just might be a simple idea to built a program that fills the ram with other stuff so the key might not be found... Maybe we'll have a physical protection mechanism for our laptops in the near future, like chemical attack for everyone going near the laptop when its turning off... besides software firewall ids virusscanner... well I'll keep dreaming :p

I'll do a re-install of ubuntu, this time looking for the options of encryptfs for the homedir "I didn't remember anymore what I did there" twofish, aes or something else.

I'll post the new findings.

---

### Post by unutbu on 2009-06-06
walterav, I'm not sure if this is very practical, but the secure-delete package can wipe swap and RAM:
```
apt-cache show secure-delete
```
> Description: tools to wipe files, free disk space, swap and memory
 Even if you overwrite a file 10+ times, it can still be recovered. This
 package contains tools to securely wipe data from files, free disk space,
 swap and memory.

PS. I am not so sure about the claim that files can be overwritten 10+ times and still be recovered. See [http://ubuntuforums.org/showpost.php?p=7375048&postcount=41](http://ubuntuforums.org/showpost.php?p=7375048&postcount=41)

---

### Post by bodhi.zazen on 2009-06-06
> **unutbu said:**
> PS. I am not so sure about the claim that files can be overwritten 10+ times and still be recovered. See [http://ubuntuforums.org/showpost.php?p=7375048&postcount=41](http://ubuntuforums.org/showpost.php?p=7375048&postcount=41)

That has been bebunked , one write seems sufficient.

[http://ubuntuforums.org/showpost.php?p=7405704&postcount=3](http://ubuntuforums.org/showpost.php?p=7405704&postcount=3)

---

### Post by unutbu on 2009-06-06
bodhi.zazen, thanks for the information/corroboration.

---

### Post by walterav on 2009-06-06
I tried the options to decrypt the encrypted homedir, but I can't get it to work.

I'm already satisfied with the "whole encrypted fs", I'll just remember not to "extra" encrypt the homedir before I'll have a solution.

thanks for the input sofar!

---

### Post by brallan on 2009-06-26
> **walterav said:**
> I tried the options to decrypt the encrypted homedir, but I can't get it to work.

I'm already satisfied with the "whole encrypted fs", I'll just remember not to "extra" encrypt the homedir before I'll have a solution.

strikes me as an invitation for problems to ask to encrypt the home directory once the whole filesystem is encrypted. It's easy to think, gee, of course the home directory should be encrypted, why just encrypt the rest of the disk?! and answer YES. I fell in the trap the first time, too.

---

### Post by walterav on 2010-05-18
> **brallan said:**
> strikes me as an invitation for problems to ask to encrypt the home directory once the whole filesystem is encrypted. It's easy to think, gee, of course the home directory should be encrypted, why just encrypt the rest of the disk?! and answer YES. I fell in the trap the first time, too.

:popcorn:

HOWTO:
Decrypt the /home directory from a liveCD:
[http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/](http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/)

---

