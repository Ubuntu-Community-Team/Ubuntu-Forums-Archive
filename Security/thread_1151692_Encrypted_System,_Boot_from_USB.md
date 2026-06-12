---
title: "Encrypted System, Boot from USB"
date: 2009-05-07
forum: Security
---

### Post by levino on 2009-05-07
Hi there, I hope there is no other thread discussing this. At least I did not find it, so if there is any please pardon me and refer to it.

My idea is the following. I want to set up an Ubuntu Distr. on a Desktop PC (will run as a server). The Main drive should be entirely encrypted. To decrypt it I want to use a bootable media, such as a SD-Card or an USB-Stick. As you see I do not just want to store the keyfiles on the stick, but the /boot/ partition as well. Anybody who gets his hands on my harddisk in the PC won't be able to read a single byte. As the set up will be for a server I can't enter any password so auth will have to be done over keyfiles stored on the same sd-card. The system should after boot work entirely on the Harddrive in the PC, even if the USB-Stick is taken away.

So here are my questions: Is it possible to hide the existence of any data on the main drive, like with TC for non-system partitions? How can I do this the most comfortable and dummyproof way ;)? How big will the SD-Card have to be?

The PC is fast enough, has enough RAM and can boot from whatever I like him to boot.

Thx for your time and help, Levino

---

### Post by MarnickV on 2009-05-13
Bumping this because this seems really interesting (putting /boot and keyfiles on a pendrive).

---

### Post by MysticalRiotCandy on 2009-05-14
That would work pretty well, but what would happen if the attacker used a cold boot to dump the contents of the RAM?  Then he'll have all your keys.

It's an interesting concept, though.  I just thought that that vulnerability still needs to be explored.

---

### Post by HermanAB on 2009-05-14
Hmm, you cannot encrypt every last byte, since the system has to boot from something that is readable.  

Furthermore, encrypting the root partition is useless since Linux is Free and anybody can download it from mirrors.kernel.org, it is not secret.  Encrypting the Linux and GNU binaries just serve to make your system slow.  You only need to encrypt your data, typically /home and /swap.

You can use the gnome-luks-format wizard to create encrypted disks.  It works very well and is part of the luks-tools package.

---

### Post by MysticalRiotCandy on 2009-05-15
> **HermanAB said:**
> Hmm, you cannot encrypt every last byte, since the system has to boot from something that is readable.  

Furthermore, encrypting the root partition is useless since Linux is Free and anybody can download it from mirrors.kernel.org, it is not secret.  Encrypting the Linux and GNU binaries just serve to make your system slow.  You only need to encrypt your data, typically /home and /swap.

You can use the gnome-luks-format wizard to create encrypted disks.  It works very well and is part of the luks-tools package.
I think that's why he wanted to put a boot loader inside of a flash drive fob that would be able to decrypt the filesystem after the correct password is inputted.

But then the key would have to remain in memory (the password, not the USB drive), and like I said, the cold boot attack can snatch it out by RAM dumping.

---

### Post by levino on 2009-05-15
> **MysticalRiotCandy said:**
> I think that's why he wanted to put a boot loader inside of a flash drive fob that would be able to decrypt the filesystem after the correct password is inputted.

But then the key would have to remain in memory (the password, not the USB drive), and like I said, the cold boot attack can snatch it out by RAM dumping.

This argument holds for any encryption, doesn't it? As a matter of fact I prefer to have keyfiles stored on the same flash-drive. I know its less save but as the set up should be a server there won't be any keyboard attached. I would just plug in the flash-drive, switch on the server, wait for 30 seconds and pull of the flashdrive again.

---

### Post by HermanAB on 2009-05-15
Now think what is going to happen when the server gets power glitch while you are on the other side of the globe.

---

### Post by levino on 2009-05-15
Thanks for this remark. Actually I do not want to discuss the set up but the realization.

---

### Post by Netpoliglota on 2009-11-18
I'm also interested in how to install the boot partition in a usb flashdrive, to boot from it and unlock a root partition encrypted with  luks, using keyfiles, as it is explained here for Gentoo (without the keyfiles):
[http://en.gentoo-wiki.com/wiki/Booting_encrypted_system_from_USB_stick](http://en.gentoo-wiki.com/wiki/Booting_encrypted_system_from_USB_stick)
It would be nice to have an explanation that could use the encryption procedure already existent in the alternate-cd and then create the boot partition from it.
Actually, having one boot partition in the hd but using it only for rescue purposes (having hashed it first to be able to verify if it hasn't been tampered using a liveCD). Useful if the pendrive gets lost.

---

### Post by fargle on 2009-11-18
> **HermanAB said:**
> Furthermore, encrypting the root partition is useless since Linux is Free and anybody can download it from mirrors.kernel.org, it is not secret.  Encrypting the Linux and GNU binaries just serve to make your system slow.  You only need to encrypt your data, typically /home and /swap.


I understand we're talking about the execution of this specific scenario, but I did just want to interject - I would be careful with thinking like yours, depending on the level of protection you want.  If you encrypt only your home directory, that leaves the shadow password file unencrypted and easily retrievable.  Brute forcing your password, which is being used to encrypt those files, is quite a bit easier than cracking the encryption I think, especially with rainbow tables and such.

Personally, I encrypt the system drive with a boot password, then mount my home partition with my login password, which is different.

---

### Post by kevdog on 2009-11-19
I got a few good responses when I asked a similar question a few months ago, but I've never really pursued this option since -- time and laziness.

---

### Post by shaggy999 on 2009-11-20
This will lead you in the right direction:

[https://mknowles.com.au/wordpress/index.php/2009/10/01/ubuntu-karmic-koala-full-disk-encryption-with-usb-key-authentication](https://mknowles.com.au/wordpress/index.php/2009/10/01/ubuntu-karmic-koala-full-disk-encryption-with-usb-key-authentication)

---

