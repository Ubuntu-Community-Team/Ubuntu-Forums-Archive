---
title: "How to lock drives??"
date: 2009-04-20
forum: Security
---

### Post by chinmaya_n on 2009-04-20
I would like to lock one of my drives with password.... and that drive should not be used by other users on my system....

How can i do this ??

---

### Post by smileypaul on 2009-04-20
Probably lookin at drive encryption.

TrueCrypt comes to mind, although theres many different ways to do this.

You could also just change the permissions on the drive.. 700? (-rwx------)

that would effectively only allow you to access teh file, no one else.

although anyone with sudo access could easily change those permissions :)

---

### Post by chinmaya_n on 2009-04-20
How can we change permissions on the drive ??
On what file we have to implement the permissions(.. 700)?
Can you be more clear!!

---

### Post by smileypaul on 2009-04-20
Does the drive you are trying to "protect" contain system files? or is it just a drive you use for storing media etc?

---

### Post by chinmaya_n on 2009-04-21
Yes it is just a drive that contain some media !!
It dont contain any system file...!!

---

### Post by smileypaul on 2009-04-21
Then a simple permissions change should work

Before mounting the drive;

chown username /mountpoint
chgrp username /mountpoint
chmod 700 /mountpoint

Then depending on the filesystem, simply mount the drive with your uid and guid and change the permissions of the files;

cd /mountpoint
sudo chown -R username ./
sudo chgrp -R usergroup ./
sudo chmod -R 700 ./

*Note that username = your username and usergroup = your group.

Hopefully you understand that anyone in the same group as you will have access to these files as well. But if you're the only person in your group, then only you'll be able to read/write/execute these files.

Also note that, anyone with root or sudo access will be able to access these files. 

If you really want to hide your files, I suggest encrypting the volume. Look at TrueCrypt or encryptfs.

Hopefully the drive is formatted as something along the lines of ext2/3/4 etc.. if this is NTFS or FAT32.. this definitely wont work.

---

### Post by bodhi.zazen on 2009-04-21
If you wish to do this with permissions, see :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

It most certainly WILL work with NTFS and FAT (use dmask and fmask).

---

