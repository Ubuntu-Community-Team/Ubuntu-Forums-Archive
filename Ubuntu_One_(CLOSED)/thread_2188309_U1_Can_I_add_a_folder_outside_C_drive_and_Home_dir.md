---
title: "U1: Can I add a folder outside C: drive and Home directory?"
date: 2013-11-16
forum: Ubuntu One (CLOSED)
---

### Post by Deorc on 2013-11-16
Can I add a folder outside **C: drive** and **Home directory** in Windows and Ubuntu respectively in any way? If yes, them tell how to do that clearly step by step please as I am new in Linux. As I have both windows and Ubuntu, I want to share a common folder outside c: Drive and home directory in Windows and Ubuntu.

---

### Post by The Cog on 2013-11-16
The normal way to do this would be to create a new partition that can be shared by both OSs. This would probably then become the D: drive in Windows, and could be mounted wherever you want (e.g. perhaps /d) in Linux. As you are more familiar with windows, it is probably better if you use windows to do this - format it to NTFS.

In Linux, you will need to create a folder where the drive's contents will appear, perhaps with this command:
```
sudo mkdir /d
```
and you will need to edit the file /etc/fstab to get linux to "mount" the partition so that users can see its contents, by adding a line something like this:
/dev/sda3    /d    ntfs   umask=0    0  0
but we would need to know the disk layout before we can confirm the device name - I just put /dev/sda3 as an example.

---

### Post by Deorc on 2013-11-16
My common partition is shared between win7 and Ubuntu as it is formatted in NTFS already. It's a D drive in windows and sda3 in Ubuntu.

I can not even add a file outside C: drive when I use ubuntu client for Window. If I can add a file windows, then I will try ubuntu to mount using /etc/fstab. But first tell me how to add a folder using windows ubuntu one client outside C: drive please.

here is the screen shot that the Ubuntu one client on Windows does not allow adding any file from ouside C: drive also as like in Ubuntu (where outside home directory is not allowed by default).


[IMG]http://www.fotoshack.us/fotos/712671.jpg[/IMG][IMG]http://www.fotoshack.us/fotos/279042.jpg[/IMG]


So how to add in windows?

---

### Post by The Cog on 2013-11-17
Now I am confused. What has Ubuntu One got to do with it? I thought we were talking about local hard disk with a shared partition - you even say sda3. 

Ubuntu One is a cloud storage system - remote servers, and I don't know much about it as I have never used it.

---

### Post by Irihapeti on 2013-11-17
The answer to the OP's question is "no". You can only sync folders that are within the home directory. I believe the same applies to Windows, though I've not used U1 on Windows very much.

---

