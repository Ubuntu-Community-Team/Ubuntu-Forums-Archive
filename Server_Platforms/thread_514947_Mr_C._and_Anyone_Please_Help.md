---
title: "Mr C. and Anyone Please Help"
date: 2007-08-01
forum: Server Platforms
---

### Post by moxon on 2007-08-01
Hello Mr. C,

I was reading a post where you helped out a person with a Windows sharing issue with Ubuntu. I was wondering if you could maybe give me some advice. I am fairly new to Ubuntu. But I have read many posts over the last few days and don't seem to I have luck getting the sharing thing going. I hava a USB Drive connected to ubuntu and that is really what i need to share. I have installed WEBMIN, and followed everything you said your help to the other fella. FYI, I have reformatted the USB drive to FAT32, I read that somewhere.


In webmin it says my external drive has read/write permissions. I checked the users and the passwords. They seem fine. I have disabled passwords. Here are the results I get.

Mac - After I put in the password it gives me the error that the alias has been deleted, and it asks if I want to repair or delete it. Nothing works

Windows - just keeps bringing up the password box.


Oh, I have also tried just sharing a folder in the filesystem root directory. I get the same results from both Mac and Win as trying to access the USB drive.

I am able to talk to the Windows network from Ubuntu, just not to Ubuntu from Windows or Mac.

Please Help,

---

### Post by Mr. C. on 2007-08-01
Sorry, I've been a little busy today.

I don't use webmin, and haven't looked at it in years. Regardles, there isn't enough information in your post for us to know how things are configured, or what the state of your system is.

Let's step back. It sounds like you are simply trying to share a file system with various systems (Mac and PC). If this is correct, then you will need to use Samba.

What is the contents of your smb.conf file ?
Is Samba actually running ?

Here are some commands to help us begin the diagnosis:

```
cat /etc/samba/smb.conf
ps -ef | grep smb
```

Look for errors or any other helpful messages in your /var/log/samba/* logs.  Post any of those.

MrC

---

