---
title: "Ext3 Encryption Removal"
date: 2010-07-21
forum: Security
---

### Post by Amadameus on 2010-07-21
Recently I bought a 1TB external drive, and promptly formatted it to ext3.

I must admit, I'm only a level 3 or 4 Ubuntu user, so a lot of what I've done was beyond my grasp but I *am* trying to figure things out.

Anyway, I was given the option to encrypt files on the drive. Naturally, I said yes. I was also given the option to make the drive refuse access to anyone but the current user. I said yes again.

Well, now my boot sector is beginning to corrupt and I'm starting to become quite nervous that sometime soon I won't have the "current user" and won't be able to access the files ever again - since this drive is my master backup, that's kind of a big deal.

Short of transferring everything to another location and formatting the 1TB drive again, are there any ways to open up permissions so I can reinstall my OS on a new HD and still access my files?

---

### Post by Rubi1200 on 2010-07-21
What exactly do you mean by > now my boot sector is beginning to corrupt Could you please provide some more information such as a description, error messages and the like.

---

### Post by Amadameus on 2010-07-21
> **Rubi1200 said:**
> Could you please provide some more information such as a description, error messages and the like.

My boot drive is a dodgy 10GB HD that I found and salvaged. (Truckload full of towers/CRT monitors left at the dump, I bought them for the scrap metal and got some decent parts but don't fully trust any of them)

Anyway, the BIOS loads perfectly fine.
The BIOS then tries to load the main OS (Ubuntu 10.04) and waits.
And waits. And waits.
Eventually it gives up on waiting and drops to the *initramfs* shell.
About 5 minutes after dropping to the shell, exiting the shell causes the OS to load properly.

To me, this means impending data corruption and eventual failure of my 10GB HD. If this happens, then I'll lose the only OS with privileges to my 1TB drive!

Exact error messages aren't clear - they're only displayed briefly by the BIOS before it drops to the shell. Although the rig does reliably boot, it requires several minutes of waiting, which I usually use as an opportunity to make a sandwich.

---

### Post by Rubi1200 on 2010-07-21
In my opinion, the smartest thing to do right now is get the data off the 1TB drive.

---

### Post by CharlesA on 2010-07-21
> **Rubi1200 said:**
> In my opinion, the smartest thing to do right now is get the data off the 1TB drive.
+1 to that.

If you can, transfer it to another drive, then reformat the 1TB drive without encryption and transfer it back.

If the OS is having problems loading, you'll be SOL if it doesn't load and the file system is encrypted.

---

### Post by Amadameus on 2010-07-22
> **Rubi1200 said:**
> In my opinion, the smartest thing to do right now is get the data off the 1TB drive.
> **CharlesA said:**
> +1 to that.

If you can, transfer it to another drive, then reformat the 1TB drive without encryption and transfer it back.

Already in the process - but my poor old rig doesn't have USB 2.0 and transferring 800-some gigs of files is going to take some time.

*shrug* Ah well, I was hoping there was an option (someone said that converting ext3 to ext2 might cause it to drop its' security permissions but I couldn't find any data confirming that online) which didn't involve spending 48 hours patiently moving data around.

Thanks very much for the help!

---

