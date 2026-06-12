---
title: "Ecryptfs questions"
date: 2009-05-29
forum: Security
---

### Post by timzak on 2009-05-29
Hi,

I'm using ecryptfs for an encrypted private directory in my home folder.  I had some questions regarding ecryptfs, as I am new to using encryption:
1) I use sbackup to automate backups of my system.  What happens to the items in my private directory that are backed up?  Are they in an unencrypted state in the backup directory?
2) In what situation would I ever need the randomly generated passphrase?  Could someone give an actual scenario?

Thanks,
Tim

---

### Post by Agent ME on 2009-05-31
1. Make sure sbackup DOES NOT backup the ~/Private directory. It should backup only the ~/.Private directory, which holds the encrypted files.
There's a chance it already behaves this way if it only follows one file-system. Try running it (while you're logged on) and see how it works. From reading the description of it, you should be able to tune its settings.

2. If your ~/.ecryptfs directory was lost, you would need it. All the files in ecryptfs are encrypted by a random key in that directory and your passphrase hashed together. Lose one of those two and the files might as well be random data. (I believe the mount phrase ecryptfs gives you when you set it up is the result of both parts pre-hashed together.)

---

### Post by kaefert66014235 on 2009-06-01
Hi there!

It seems that I used Ecryptfs to encrypt my home directory on my Ubuntu 9.04 server.

Just now I replaced one harddisc of the system, and booted it up again, and I can't read my home directory anymore. I didn't know I was using Ecryptfs, and therefore I don't know my passphrase. This is not the first time I rebooted since the installation, and until now the system could mount my homedirectory without any problems. Why the **** did this happen now?

Is this some sort of check if the system configuration changed? Will I get access to my home directory, if I restore the hardware configuration of the server back to how it was?

Or what else could I do for beeing able to access my home directory again?

Thanks for your help.


EDIT:
I readded the disk I removed, and now the automatic mounting of my homedirectory works alright again. Can somebody tell me, how I could proceed so that I am able to remove that disc, but still access my home directory?

Is there a way to access the passphrase used by ubuntu to automatically mount the homedirectory? or if the homedirectory is already mounted, a way to change the passphrase?
Or should I just copy the contents of my homedirectory to some other directory, and afterwards restore it from that backup?


EDIT:
I did as I discribed above. just copied the contents. But after trying to resetup the encryption, only the "Private" folder of my homedirectory is encrypted.

---

