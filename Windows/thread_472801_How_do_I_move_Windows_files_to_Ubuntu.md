---
title: "How do I move Windows files to Ubuntu?"
date: 2007-06-13
forum: Windows
---

### Post by mickeyu422 on 2007-06-13
I have video and audio files saved to a folder in Windows XP. I have both drives hooked up to my computer with the XP one as my slave drive. Because I don't have a lot of free space left on my Ubuntu drive I was wondering if there was some way that I could make ubuntu recognize my XP hard drive in the slave slot? That way I could just play the files from that hard drive in VLC without having to save them to my filled hard drive. Thanks for the help.

---

### Post by sriram on 2007-06-13
u will have to  mount those partitions at the boot to access them..
if the partition is fat32 then it could be mounted with read/write,unlike ntfs which is only read only for newbies..
although ntfs-3g culd be used to write into ntfs..
check the partition no and select mount point as desired.
first cd /media
sudo mkdir desired "mount point name"
make as many directories needed for the no of partitions.
sudo gedit /etc/fstab
add this line to the file and save it.
ex:/dev/hda1(partition no)   /media/Windows(mount point)   vfat    iocharset=utf8,umask=000  0    0
exclude the words in bracket..
then finally sudo mount -a

---

### Post by NJC on 2007-06-13
Mickey;

There's lots of info here too:

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=mount](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=mount)

---

