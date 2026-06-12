---
title: "Access eCrypt Home Directory Through OS X"
date: 2015-04-19
forum: Security
---

### Post by corbin.loftis on 2015-04-19
Hello,

I have had numerous problems with my Ubuntu installation, and another kernel panic occurred today, and now my system will not boot. I have pulled out the hard drive, and I am able to open the encrypted home folder when plugging it in externally to my MacBook Pro using [sudo ecrypt-recover-private] through Virtualbox (running Ubuntu 14.04 in the virtual environment). I am just trying to back up the files in my ~/home directory to my computer or another external hard drive.

The only problem with this is that even though I am able to access the files on the encrypted drive using Virtualbox, when I try to copy them (even when running nautilus as root), it will copy the first file and then freeze the entire system and require me to reboot the virtual drive and begin again. It happens every time, even when copying less files.

I am able to mount the hard drive on my Mac OS X desktop, but I have no way of accessing the encrypted ~/home folder through Mac OS X. Is there something I can do so that it will not freeze during file copying in Virtualbox, or is there a way I can locate and open the encrypted file directory on Mac OS X, the same way I am able to using ecryptfs through Virtualbox Ubuntu?

Thank you

---

### Post by corbin.loftis on 2015-04-19
Here is the process I used for copying files off of an external hard drive's encrypted home folder:

1. Install Ubuntu through Virtualbox, with Guest Additions and Extension installed.
2. Set up shared folder through settings in Virtualbox before turning it on.
3. Turning on virtual Ubuntu and mapping the shared drive to the /media/ folder.
4. Install ecrypt-utils if not installed already
5. Run 'ecrypt-recover-private' and wait. It will take a WHILE
6. Prompts will come up when the encrypted directory is found, asking if you would like to recover. Type 'y', then 'y' again to type in the password of the directory/encrypted login.
7. Copy some files and paste them into the shared folder as a test. If all goes well, copy larger batches of files. Don't do huge amounts, as it could cause the virtualbox environment to freeze up from an overload of system activity.
8. WAIT

---

### Post by corbin.loftis on 2015-04-21
Alright, it has not been working. It seizes up when copying files. Is there a way to mount the encrypted Ubuntu /home folder using OS X?

---

### Post by corbin.loftis on 2015-06-05
Well, as far as I can tell, there is ABSOLUTELY no way to do this through OS X, because eCryptFS is a Linux-only utility. I ended up installing Ubuntu through bootcamp and booting into it in order to copy all of the files off of the hard drive...

---

