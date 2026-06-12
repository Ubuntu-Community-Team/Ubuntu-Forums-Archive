---
title: "No longer possible to encrypt /home partition during installation?"
date: 2020-09-19
forum: Security
---

### Post by cackerso on 2020-09-19
I recently read this web article: 

[https://www.linuxuprising.com/2018/04/how-to-encrypt-home-folder-in-ubuntu.html](https://www.linuxuprising.com/2018/04/how-to-encrypt-home-folder-in-ubuntu.html)

Which starts by stating Ubuntu 18.04 and 20.04 no longer include a feature to encrypt a /home partition when installing the system. To me it implied that encrypted /home folders are insecure.

Recently I installed Mint 20 on a dual boot system with Ubuntu 18.04.  Using Mint I could see the contents of my supposedly encrypted /home on the Ubuntu partition. To say the least I was surprised.  I haven't tired yet to see if  a USB thumb drive live boot of Mint 20 will do the same thing.

Is there a way to check it a /home directory is in fact encrypted?

My knowledge of Linux in general is basic to moderate.

---

### Post by TheFu on 2020-09-19
> encrypted /home folders are insecure.
and hard to maintain, backup, support migration, and have poor performance.

If you want to encrypt stuff, there are a number of "ok" ways and one, accepted, excellent, way.
The 'ok' list:
[LIST=1]
[*]encfs
[*]encryptfs
[*]zip and other "archive" containers
[*]LUKS at a file level (create a "volume" file, then use cryptsetup and mkfs to create the container to hold files, and mount that file system); remember, on Unix systems, "everything is a file", so we can use files as devices when desired.
[*]LUKS at the /home/ partition level. 
[/LIST]
There are security issues with each of those.  Performance for LUKS encrypted /home/ would be the best. Setting up automatic prompts at boot to decrypt /home/ and mount it are beyond my skill, but others have done it. It requires modifying the crypttab, fstab, and initramfs. I wouldn't be surprised if grub needed some settings too.

The "ok" list is usually sufficient to prevent a teen from gaining access, but someone dedicated to gaining access from any security business or govt who is patient and has time to trick one of the operators into providing the passphrase will be successful.  

The "excellent" list:
[LIST]
[*]During installation, select whole system encryption. Choose a strong passphrase, over 30 random characters.
[/LIST]
This will result in a HDD setup with LVM and all LVs contained inside an encrypted container. Only the boot areas aren't encrypted.  The "evil maid" attack can still be used, without additional steps.  Adding a hardware device using a challenge/response code for unlocking would help improve security. Booting from a flash drive that isn't left with the system would further increase security.  This assumes the crypto+boot-flash are always with you - always. 

A microSD boot device can be tiny and a Yubikey 5c is small.  I only do the boot flash when traveling. The yubikey is part of my normal decryption-at-boot process.  I have a backup yubikey and a 60+ character, random, passphrase that I doubt I could enter by hand.  dm-crypt/LUKS has 8 slots for different decryption methods. 

But people sometimes think I'm paranoid. ;)

---

### Post by EuclideanCoffee on 2020-09-19
Since 18.04 LTS, full disk encryption has been the preferred method, with ecryptfs (home directory encryption) not available at installation. You have the ability to use ecryptfs after installation if you wish. There're a few tutorials on how to accomplish this with Debian, which is the same for Ubuntu. [https://wiki.debian.org/TransparentEncryptionForHomeFolder](https://wiki.debian.org/TransparentEncryptionForHomeFolder)

To check for ecryptfs (home directory) encryption, use this command in your terminal.

```

ls -A /home

```

or 

```

ls -A /home/username_here

```

You should find a .ecryptfs folder.

If you want further proof, try this command:

```

ecryptfs-verify -h

```

If both are positive, you should feel confident that your home directory is encrypted.

However, LUKS is now the preferred method, which is full disk encryption. This however limits you to one distribution.

---

### Post by MoebusNet on 2020-09-19
@The Fu

> But people somethings think I'm paranoid.

I heard somewhere "You're not paranoid if they're really out to get ya..."

---

### Post by tapucosmo on 2020-09-19
> **EuclideanCoffee said:**
> However, LUKS is now the preferred method, which is full disk encryption. This however limits you to one distribution.

You can use LUKS for multiple operating systems, it just becomes more complex to set up. It requires manually creating the partitions and encrypting them with LUKS before running the OS installer (I haven't personally tried this though).

I have used cryptsetup-reencrypt before to encrypt my root and home partitions on a dual boot system.

---

### Post by EuclideanCoffee on 2020-09-19
> **tapucosmo said:**
> You can use LUKS for multiple operating systems, it just becomes more complex to set up. It requires manually creating the partitions and encrypting them with LUKS before running the OS installer (I haven't personally tried this though).

I have used cryptsetup-reencrypt before to encrypt my root and home partitions on a dual boot system.

This may have changed, but the general advice is that this somehow weakens encryption or makes it useless. I admit I haven't kept up with LUKS development since LUKS2 seems to solve many of these issues.

Someone wrote a wonderful blog post here: [https://www.mikekasberg.com/blog/2020/04/08/dual-boot-ubuntu-and-windows-with-encryption.html](https://www.mikekasberg.com/blog/2020/04/08/dual-boot-ubuntu-and-windows-with-encryption.html)

I'm not 100% on this method however. I wouldn't implement it for a client for example.

---

### Post by cackerso on 2020-09-19
The reply's answered my questoins, thanks for the help

---

### Post by EuclideanCoffee on 2020-09-20
Please remember to mark the thread as [SOLVED]. This helps users searching for solutions later.

---

