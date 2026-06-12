---
title: "Format server 11.04 HDD"
date: 2013-09-08
forum: Server Platforms
---

### Post by Denlyn on 2013-09-08
No longer needing Ubuntu server 11.04 as I have now downgraded to a more simplified business, how do I format the HDD so as I can use it for a backup drive.

I have downloaded Ubuntu 13.04 and ran it as a live distro on my old server and then started Gparted.

The partition where the server is installed has a lock symbol on it and I can't seem to find a way to either format or delete the volume. When I tried to install Ubuntu 13.04, it wanted to install next to it or upgrade the operating system. As I can't find a way to do this task, I tried to format it through Windows 7 but there is no options to delete the volume. Right clicking on the partition, Windows 7 only shows a help link.

As stated, I no longer need Ubuntu server and it done the job to perfection without any hiccups. But I do want my hard drive back for my own use.

I hope someone can give me step by step instructions as this has me baffled. 

Cheers.

---

### Post by M!K3_$ on 2013-09-08
If you are using Windows you can follow this guide to use the Disk Management interface.
[http://windows.microsoft.com/en-ca/windows/create-format-hard-disk-partition#create-format-hard-disk-partition=windows-7](http://windows.microsoft.com/en-ca/windows/create-format-hard-disk-partition#create-format-hard-disk-partition=windows-7)

If you are using Ubuntu, I suggest booting a live disk and then running gparted. You should be able to find this from the applications menu in Ubuntu. It is pretty straight forward, but here is the user guide:
[http://gparted.sourceforge.net/display-doc.php?name=help-manual](http://gparted.sourceforge.net/display-doc.php?name=help-manual)

Using either of these tools you can delete the existing partitions and create new partitions on the drive which you can then use for whatever you like.
Good Luck!


* Mods: I would suggest this thread be moved as it is not a server specific question.*

---

### Post by Denlyn on 2013-09-08
Thank you M!K3_$

I already knew about the procedures of using the Windows guide and Gparted it simply wouldn't let me do anything. I cannot explain it but I rebooted the system with the distro in it the next day and I had full access to do what I needed done. Thanks for the help anyway.

Cheers

---

### Post by M!K3_$ on 2013-09-08
Hello,

Perhaps the partition was mounted while you attempted your maintenance. Either way, I'm glad to see you got it working!
Please remember to mark this thread as solved.

---

