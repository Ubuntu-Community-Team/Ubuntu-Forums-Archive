---
title: "Viewing LUKS (on FDE) Password at Startup"
date: 2017-09-23
forum: Security
---

### Post by Franz_Ziereis on 2017-09-23
I have several fully encrypted Ubuntu installations.  A couple have their /boot on removable thumb drives.  It seems that everyday that I boot any given one of these machines I have to enter a very long and complex (though well known by me now) passphrases two and three time regardless of how careful I seem to enter them.  I changed the keyboard on one of the machines and still have the same problem.  I'd like to see what the mistakes are that I'm actually making, A key or two on the keyboard with a tendency to double a letter, my finger not pressing the shift key hard enough for a capital letter or sybmol or whatever the case may be.  Is there some way that I can make the password viewable as I type it? I haven't noticed anything obvious to allow that. Some encryption programs like, ScramDisk, Drivecrypt, E4M, Truecrypt and Veracrypt have long had that as an option. Thanks. vielen Dank!

---

### Post by TheFu on 2017-09-24
I don't know of any method, short of modifying the code yourself, to have it display what you type.  

Another option is to switch from a passphrase method to a keyfile-based method.  THAT is supported.  
[https://wiki.archlinux.org/index.php/Dm-crypt/Device_encryption#Keyfiles](https://wiki.archlinux.org/index.php/Dm-crypt/Device_encryption#Keyfiles)  I've not used this for a boot/OS disk, but I have for other encrypted partitions.

For booting, I use a Yubikey + a shorter (15 character) passphrase to unlock my encrypted partitions.  I also have another passphrase slot for the encryption that requires entering a 70+ character passphrase as a backup, should that yubikey be lost/stolen.  The 70+ character passphrase is kept by my lawyer - I do not have a copy.

Anyway - the yubikey + shorter passphrase together are fairly long and much more secure than a passphrase alone. The passphrase is short enough that I don't have issues entering it.  The yubikey static output really is just a pre-programmed standard passphrase too ... but it gets typed perfectly every time.

Just because another program offers a "feature", doesn't mean that feature is a good idea.

---

### Post by Franz_Ziereis on 2017-09-24
Thanks for the response.  That sounds like quite a nice setup you've got there but a bit advanced for me at this stage.  Can you set the pp on the YubiKey  yourself or does it come preset?  I remember years ago a guy that was working on, if I remember correctly, a PGP type of thing on /boot.  I followed him for awhile and had it working in a VM but at some point he gave up the project and it seems like it would break with every Ubuntu update.  I need to install Virtual Box again and go through that link you sent me and see if I can get a key as well as an additional slot working, like yours.

As long as I have your ears, why is it that Ubuntu is set up for a SWAP partition instead of a paging file?  After I set up my encrypted systems - usually just all of / encrypted but with /boot on a  thumb drive - I sometimes end up making a paging file.  I assume this is safe, as it (the paging file) would be encrypted like any other file I create on my encrypted root partition?

I've got a 2008 edition of _Linux Bible_ is there any other - or better book - that you would recommend to really get into the Linux/Ubuntu entrails and learning the terminal?

---

### Post by TheFu on 2017-09-24
* Yes.
* I don't know.
* I don't know.
* I use manpages.

---

