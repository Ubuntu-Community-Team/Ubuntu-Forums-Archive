---
title: "Whole Disk Encryption - How much is possible using TrueCrypt?"
date: 2008-02-14
forum: Security Discussions
---

### Post by breaking on 2008-02-14
I would like...
[list][*]100% encrypted harddisk
[*]no mbr, initrd, /boot on harddisk
[*]swap also encrypted
[*]booting from usb stick, enter password and use the encrypted harddisk then
[*]two factor authentication (a keyfile on usb stick + a passwort to enter before booting)[/list]

There [are](https://help.ubuntu.com/community/?action=fullsearch&value=encryptedfilesystem&titlesearch=Titles) a lot of howtos inside the wiki. But none of them is talking about TrueCrypt when using full disk encryption.

Is it not possible to have a small unencrypted linux somewhere (usb stick or small partition on harddisk), then load TrueCrypt, then enter password, then start the rest?

---

### Post by HermanAB on 2008-02-14
Encrypting / and /usr is useless since Linux is FOSS anybody can download and read it, it is not secret.  Also, doing so makes the machine slow.

You only need to encrypt /swap, /tmp and /home.

It is usual to encrypt the whole HDD on Windows machines, since no-one knows exactly what Windows does, but such extreme measures are not required on Linux.

Cheers,

Herman

---

### Post by breaking on 2008-02-14
> **HermanAB said:**
> Encrypting / and /usr is useless since Linux is FOSS anybody can download and read it, it is not secret.  Also, doing so makes the machine slow.
Sorry, no offense. But this is your opinion.

Third thread is not to debate who needs it and if it`s pointless or not. It`s possible to fill up books with this discussion. Other people also encrypt hole disk using dm-crypt...

I am just asking how much is possible with TrueCrypt.

---

### Post by hyper_ch on 2008-02-14
just make a truecrypt containter that's as big as the harddisk... then you have it fully encrypted.

---

### Post by AusIV4 on 2008-02-14
I believe you can encrypt everything except /boot, however if supported by your BIOS there's probably away to make your /boot partition a USB device. I don't have any good how-tos for you, because a lot changed with TrueCrypt 5.0, so the older tutorials are now out-dated.

Ignore HermanAB, who clearly has no idea what he's talking about. Encrypting / and /usr has advantages and disadvantages, and is most certainly not useless.

Lastly, I would encourage you to use dm-crypt and LUKS, unless you intend to view the disk on Windows as well. Not only will you find speed improvements, if you ever need to boot your disc from a live CD for recovery purposes, there are lots of distros that include dm-crypt and LUKS in the default install. If you use Truecrypt, you'd have to boot the LiveCD, download truecrypt and install it, then you could mount your partitions.

Obviously, this isn't my decision to make, but when I was looking at encrypting my laptop, I spent a lot of time trying to figure out how to do it with TrueCrypt, but eventually I realized there was a reason all of the tutorials use dm-crypt (and previously cryptoloop).

---

### Post by hyper_ch on 2008-02-14
if you use luks/dm-crypt for encrypting swap and root you can also create a key-file that will then make your other TC-drive auto-transparent upon booting (well, it works with dm-crypt/luks but I think TC should also have that option somehow).

---

### Post by breaking on 2008-02-14
I think you may be right I should look into dm-crypt. Maybe it`s not impossible with TrueCrypt to do like I want but for relative new users it`s to hard to figure out how to.

> **AusIV4 said:**
> Lastly, I would encourage you to use dm-crypt and LUKS, unless you intend to view the disk on Windows as well.
Yes, I want to do this because TrueCrypt has runs well on windows, it has a gui and there is also an ext3 driver for windows.

> **AusIV4 said:**
> Not only will you find speed improvements, if you ever need to boot your disc from a live CD for recovery purposes, there are lots of distros that include dm-crypt and LUKS in the default install.
Of course I also want this option (Access it from live cd.).

---

### Post by OpenSourceFuture on 2008-02-14
From what you are saying you want no sign of data on the computer, so one huge TC partition? Here are your options:

1) Install Ubuntu 7.10 with alternative cd, use whole disk crypt.
Advantages: Relatively Simple, Very secure for most needs
Disadvantages: /boot partition cannot be crypted

2) Find a guide to installing ubuntu/any linux onto a USB drive, install TC on usb linux and crypt whole drive, access through live USB.
Advantages: No /boot
Disadvantages: LiveUSB, Small amount of space for OS, relies on two pieces of hard ware, USB OS unencrypted

3) Make a virtual OS using QEMU, encrypt it, when needed decrypt it and use as your OS for sensative stuff.
Advantages: Easiest to implement, protects main OS from problems on virtual one
Disadvantage: Main OS not encrypted

---

### Post by OpenSourceFuture on 2008-02-14
4) Last option, Manual Install for dual boot with windows & linux:
Install Windows
Install Ubuntu with alternative cd
Manually created crypt ubuntu & swap
Create a third large partition
Encrypt Windows with TC
In ubuntu, or windows, format the third partition with TC, make filesystem fat32
That will be your intermediate so you can access stuff from either.

Good luck.

---

### Post by hyper_ch on 2008-02-15
> **OpenSourceFuture said:**
> Disadvantages: /boot partition cannot be crypted

Why is that a disadvantage?

---

### Post by breaking on 2008-02-15
Virtual OS are to slow on my comp. I am already playing with it for test purposes but for every day use I wouldn´t have fun with it, it`s to limited.

I think the first thing I need to learn now
- use dm-crypt for files
- then installing Ubuntu on USB
- then encrypting disk with normal instructions
- using keyfiles
- and then I try to combine all this.

> **hyper_ch said:**
> Why is that a disadvantage?
It`s not sure if it`s his opinion. He did just write this because I was asking for an fully encrypted disk with /boot an another device.

The advantage of a 100% encrypted disk is that no one can manipulate anything (only deleting and destroying) even with physical access to it. No way to infect /boot with malware as long usb stick or password are still secret.

---

### Post by hyper_ch on 2008-02-15
With the alternate install cd you can fully encrypt an install (except for /boot). So, learning dm-crypt isn't that though. You'll let the installer handle everything. If you know how to install onto usb, then you can just fully encrypt that.

After that you can use either dm_crypt/luks to encrypt further disks or you can use TC to do that. Just keep a key-file (if you chose to use one) on a dm_crypt/luks partition so that it only becomes available after you have made that one transparent.

> **breaking said:**
> It`s not sure if it`s his opinion. He did just write this because I was asking for an fully encrypted disk with /boot an another device.

Well, in /boot you should only have the linux kernels and the grub starting menu. None of this is sensitive I think (except if someone adds a malicious kernel there - if that is possible).

---

### Post by AlexEagar on 2008-02-16
I was under the impression that system encryption was supported in Linux. I just found out that [it is only supported in Windows]("http://www.truecrypt.org/docs/?s=sys-encryption-supported-os"). I recommend that you use the alternate CD to enable system encryption while installing Ubuntu. You can just select to encrypt the whole disk, which requires no extra configuration besides typing your password. Or you can [configure your encrypted partitions manually]("http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html"). Then just use TrueCrypt to encrypt non-system volumes. Just install the deb file that you can download from the TrueCrypt website and then run 'truecrypt' from a terminal window. I'm looking forward to system encryption support in Linux in a future version of TrueCrypt.

---

### Post by eggface on 2008-07-02
Hi, this is not a good enough solution for everyone. Some of us need deniable encryption. How do you get deniable whole disk encryption with Linux? It would be a shame if I had to use windows to be more secure!

By deniable I mean: at least two possible passwords, preferably an infinite amount which decrypt to separate volumes. You cannot tell other volumes exist or at least cannot tell how many with the wrong password.

---

### Post by hyper_ch on 2008-07-02
why do you need deniability anyway?

---

### Post by eggface on 2008-07-02
With all due respect, that's none of your business.

---

### Post by hyper_ch on 2008-07-03
problem with plausible deniability is that if you encountr a group that forces you to reveal the password for the first level, that group can never be sure if there is anything more to it ;) so they will go on forcing you... depending on that group you could replace force with "torture" - if that's what you're afraid of...

Since you can hide systems within systems within systems they just won't believe you and think there is even more to it ;)

---

### Post by Xebec on 2008-07-04
Entire disk deniable encryption? LOL. If you want deniability, then you definitely do not want to encrypt everything. You must have working breathing operating system. Use TrueCrypt to create encrypted volume file with a hidden subvolume somewhere on your filesystem. Inside it you can put anything you want. If you want whole operating system hidden on your PC, just install a virtual machine.

---

### Post by solitaire on 2008-07-08
New version of Truecrypt lets you install 2 encrypted OS's on a drive. One a working OS. The other is a plausible deniability OS (working OS that has no sensitive data on it.) Trrucrypt installs a pre-boot encryption prog which asks you for the password. 1 password boots your real encrypted OS, another password starts up the encrypted "dummy" OS.

I'm thinking of trying this on my laptop Insted of running VirtualBox I'll install XP as my DUMMY OS and use it for all the stuff I need windows for (Steam!!!) :) and my main OS being Linux that holds all my Bit torrents and Email ;) lol!!!

---

