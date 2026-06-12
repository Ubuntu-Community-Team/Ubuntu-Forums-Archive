---
title: "Post-installation encryption"
date: 2017-10-27
forum: Security
---

### Post by tziulm on 2017-10-27
I've been trying to migrate my Ubuntu home partition to an encrypted one, but I get errors every time. I followed both [this guide]("https://help.ubuntu.com/community/PostInstallationEncryption") and [this one]("https://www.howtogeek.com/116032/how-to-encrypt-your-home-folder-after-installing-ubuntu/"), but nothing worked. Following the first one, after opening the root shell in recovery mode, I get an error that says that the folder is read-only, and following the second method it tells me that the folder is already encrypted, but if I run the command ```
ls -A /home
``` I don't get any ```
.ecryptfs
``` folder, just the usernames for my accounts. Also, after running the ```
sudo ecryptfs-setup-swap
``` command for the first time (following the second guide) I got this error message:


```
WARNING:
An encrypted swap is required to help ensure that encrypted files are not leaked to disk in an unencrypted format.

HOWEVER, THE SWAP ENCRYPTION CONFIGURATION PRODUCED BY THIS PROGRAM WILL BREAK HIBERNATE/RESUME ON THIS SYSTEM!

NOTE: Your suspend/resume capabilities will not be affected.

Do you want to proceed with encrypting your swap? [y/N]: y

INFO: Setting up swap: [/dev/sda5]
WARNING: Commented out your unencrypted swap from /etc/fstab
swapon: stat of /dev/mapper/cryptswap1 failed: File o directory non esistente
```

"File o directory non esistente" means "File or directory does not exist". Trying to run the same command again I got this:

```
sudo ecryptfs-setup-swap
INFO: You do not currently have any swap space defined.

You can create a swap file by doing:
 $ sudo dd if=/dev/zero of=/swapfile count=48748384
 $ sudo mkswap /swapfile
 $ sudo swapon /swapfile

And then re-run /usr/bin/ecryptfs-setup-swap
```

I don't get what's happening. Could someone help me, please?


I have a double boot machine (Ubuntu 16.04 and Windows 8.1) and I need to be able to use both OS.

---

### Post by TheFu on 2017-10-27
First, make a backup of any data you don't want to loose.  You'll need that and after you encrypt stuff, you'll need those backups more often.  For encrypted data the only method of data recovery if anything bad happens is to restore from backups.

There are 2 types of generally used encryption on Ubuntu.
a) HOME - which uses the users password to decrypt just their HOME - encryptfs
b) Full Disk Encryption - which uses a completely separate key to unlock an entire partition/LV - LUKS/dm-crypt does that.

I cannot see why "a" would require an encrypted swap.  Actually, if you are doing it manually, "b" wouldn't require an encrypted swap either, though it would be foolish NOT to encrypt the swap in that situation too.

To be able to help, it really is necessary that you post **all** commands, exactly as you entered them. Saying you followed some guide doesn't mean that mistakes weren't made.  Also, we need to know which version of Ubuntu you are running.  /etc/lsb-release has that info.  Things change over time and internet guides aren't usually updated.  That is what likely happened with the how-to geek guide from 2012 - it is completely out of date.  The history of the ubuntu guide is also from 2012.  Paddy is still around here, so he might see this and chime in.  I know he's been working on a FDE post-install how-to.

Myself, I use FDE. For my needs, HOME directory encryption has multiple drawbacks and broke my backups.  That is unacceptable to me.  Backups are MORE important than staying patched, IMHO.

Another option is to setup a new partition/LV and use dm-crypt/LUKS for it, then manually mount that under your HOME as needed.  That way you can have more control over what is and isn't encrypted. Also, when the encrypted data is accessible, unlike the other 2 methods.  This technique does have some drawbacks too, however.

---

