---
title: "read/write access to MP3 files in /usr/Music"
date: 2011-05-02
forum: Security
---

### Post by Flywaver on 2011-05-02
I had to reinstall Ubuntu (Natty) on a brand new computer and while installing I setup the datas partition to be mounted in /usr but now I can't have access to files I put in there even if I setup the group/user permission! I can accezz /usr/Music but all files are locked! :(

Is there a way to unlock this?

---

### Post by bodhi.zazen on 2011-05-02
Yes you can.

/usr/Music is a non-traditional mount point , but that does not matter.

To set permissions it depends on the file system. FAT / NTFS permissions are set in fstab , linux permissions are changed with chown and chmod.

sudo chown user.group /usr/Music -R
sudo chmod 755 /usr/Music
sudo chmod 644 /usr/Music/*

See also:

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by Flywaver on 2011-05-03
ok I tried several tutorials but my partition is EXT4 and for some reason I managed to setup the partition in /Media/Music but inside the /Music folder it would say there is a 16kb file and would not tell me the size which should be 430Gb!

---

### Post by Flywaver on 2011-05-03
Solved it!! :)

Created the /Datas dir in /media, then went into fstab, added the drive: 
```
UUID=b4692307-58a6-41e9-85ca-755461590a75  /media/Datas  ext4  defaults 0 2
```

Then I mounted the drive and it works fine! :D

---

### Post by rookcifer on 2011-05-03
Why are you using /usr/Music instead of /home/Music?  Are you coming from BSD?

---

### Post by Flywaver on 2011-05-04
> **rookcifer said:**
> Why are you using /usr/Music instead of /home/Music?  Are you coming from BSD?

Because when I installed Ubuntu it never offered me to set the partition in /Media ! ;)

Anyways all is fine now, I managed to mount the partition in /Media! :)

---

