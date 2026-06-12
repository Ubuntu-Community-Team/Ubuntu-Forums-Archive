---
title: "Pre-boot authentication"
date: 2012-04-13
forum: Security
---

### Post by Stonecold1995 on 2012-04-13
I'm currently running Kubuntu 11.10, and like to set up pre-boot authentication for my system using on-the-fly encryption.  I've looked at one thread from a few years ago, and it told me to re-install my OS with an alternate installation CD.  I can't do that though, and I need everything as it is (i.e. no uninstalling and reinstalling, etc).  Is there a way I can do this with free (preferably open source) software?  I'm thinking of something like what TrueCrypt does with Windows where you just set it to encrypt and then reboot (if I've even got that right).  I don't think I need the boot partition encrypted (it doesn't contain anything specific to my computer, right?), and the only other partitions I have are my main partition and swap (both of which I want encrypted with 256-bit Serpent-Twofish-AES or AES-Twofish-Serpent, which ever one is more powerful.  This is assuming my CPU is powerful enough to encrypt/decrypt this on-the-fly, which I really hope it is).

So basically, can anyone recommend free software that can do this for me?  I need something that's relatively easy to use but still secure (I'm kind of a Linux noob, but I'm not *completely* ignorant!).  Like something where I specify my encryption method, salt, and encryption key and it reboots for me and encrypts the drive.

I'm sorry if a there's already a thread like this posted elsewhere that I didn't notice, but I couldn't find any that answered this question.

Also, do any of these programs also encrypt data in the RAM?  If the swap can be encrypted, then I assume the RAM can also.  I know it can't *all* be encrypted, but just something to prevent things like cold-boot attacks (yes, I am kind of paranoid).  This isn't necessary, but I'm just curious to see if it's possible.

---

