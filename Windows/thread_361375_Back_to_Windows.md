---
title: "Back to Windows"
date: 2007-02-14
forum: Windows
---

### Post by atact88 on 2007-02-14
Ubuntu has been great for the most part, but I don't know what kind of code they're writing with regard to mounting fat32 volumes. My hard drive is split up into a 1 NTFS partition, 1 ext3 partition, a swap, and a large FAT32 partition to store data in.

My first install, Ubuntu saw the FAT32 partition and NTFS partition and nicely listed them in my Computer browser. Next install, it didn't. I've been mounting them manually now:

sudo mount /dev/sda5 ~/Desktop/win

Then I get read-only permission. So I give myself write permission

sudo chmod 777 ~/Desktop/win
or
sudo chmod 777 ~/Desktop/win/*

As recently as last night I was able to overwrite and save files to the mounted partition without needing to resort to terminal and sudo commands (this is in Dapper, permissions have never worked for me in Edgy). Today, lo and behold, permissions won't change no matter how many commands I throw at it. It doesn't work for folders or files. 

Windows works with everything no problem. Oh well.

---

### Post by linuxfanatic1024 on 2007-02-14
Try:

```
sudo mount -o umask=0,rw /dev/sda5 ~/Desktop/win
```

That should force it to be read/write.

---

### Post by Swab on 2007-02-14
> **atact88 said:**
> 

Windows works with everything no problem. Oh well.

Doesn't work too well with ext3 does it?  At least, not without third party apps.

---

### Post by atact88 on 2007-02-14
> **linuxfanatic1024 said:**
> Try:

```
sudo mount -o umask=0,rw /dev/sda5 ~/Desktop/win
```

That should force it to be read/write.

it worked, thank you very much!

---

