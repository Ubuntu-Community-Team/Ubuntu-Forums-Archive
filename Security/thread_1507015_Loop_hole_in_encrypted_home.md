---
title: "Loop hole in encrypted home"
date: 2010-06-11
forum: Security
---

### Post by DreamDreams on 2010-06-11
I'm using 10.04 with encrypted home dir. I think the behavior below is wrong:

I can log in as root and change user's password. After that the user can log in using new password, which is normal, but it can also decrypt its home dir using the new password, which is dangerous. Assume I lost my computer. This encrypted home dir will not protect my private data because whoever gets the computer can boot it up with a livecd and chroot to change my user's password and then boot up my system and log in using new password. 

Any idea?

---

### Post by Agent ME on 2010-06-11
That scenario won't work. All of the ~/.Private files are encrypted by a key in ~/.ecryptfs. That key is encrypted by the user's password, so that the key, and then the files can't be decrypted until the user's password is entered.

If a user changes his password (such as with "passwd"), he then has to run "ecryptfs-rewrap-passphrase" next (this might be made automatic already or in a future version) which takes in the old password, uses it to decrypt the key, then it takes in the new password, and reencrypts the key with the new password.

Notice that the old password is required in this process. Nothing can get around that.


If you are root and run "passwd bob", it will prompt you only for the new password; not the old password (because you as root probably don't know it since you aren't bob). Then when you run "ecryptfs-rewrap-passphrase" as root, you won't be able to know what to enter for the old password.

---

### Post by DreamDreams on 2010-06-11
I hope you were right. 

But no. That scenario works because I tried. Maybe you should give it a try yourself. 

My system is a fresh install with encrypted home dir selected during installation.

---

### Post by DreamDreams on 2010-06-12
OK, I tried again. My previous description was not accurate. 

That scenario works only when I try it after the user logs out and before system reboots. If I reboot the system and log in as root and change user's password then log in as the user, I can't mount the user's private dir. 

So the question now is how to really completely log out a user. Does anybody have any idea?

---

