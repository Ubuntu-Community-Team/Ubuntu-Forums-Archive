---
title: "How do I AutoMount a crypted Partition at login?"
date: 2008-10-08
forum: Security
---

### Post by ewanchic on 2008-10-08
I have a LVM2 system on my Ubuntu 8.04. I'm adding a new logical partition, which I've encrypted and mounted properly. What I'd like to do is when I log into my environment, Ubuntu can auto prompt me to mount the partition to my desired location, and prompt me for the password (pass phrase). And, of course when I log out, it will umount the drive for me.

This is different than using /etc/fstab because I don't want it halting and prompting me during boot, only when I log-in.

I've been doing some goggling and I've tried the information listed on this site [http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu](http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu), trying to make some minor modification, but it doesn't work.

Any other options or Ideas I could try? Thanks (^_^)

---

### Post by Titan8990 on 2008-10-08
I have an *untested* idea. Make a small script that mounts the HDD. Add it to your sessions list. Log in.

I have a feeling you will not get the password prompt and it will fail but it is worth a shot.

---

### Post by mosburn on 2008-10-08
If you are going to unlock that partition at login, doesn't it kinda defeat the point of encrypting it? I forsee the situation of locking the screen and leaving the encrypted partition mounted. In this case, any other user can access the data on the drive (as long as they have access).

You would be better having a script that runs on a flash drive (or some other removable media) and have something like the following in your .bashrc file. 

```

if [ -e /media/usb/.unlock_me/unlock.sh ] then
    sh /media/usb/.unlock_me/unlock.sh
fi

```
Where .unlock_me is your unlocking script. 

This way, you can selectively choose if you want that partition unlocked and a usb key is pretty easy to dispose of if needed. Of course then all your data is gone but hey, its secure. 

In the .unlock_me directory you can have your private key and do the unlocking tranparently. I know there are ways that you can play with the automounting system to automount the dirve and unmount it depending on how if the ksy is installed or not.

---

