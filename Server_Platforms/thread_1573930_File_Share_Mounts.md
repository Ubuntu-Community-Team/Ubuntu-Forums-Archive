---
title: "File Share Mounts"
date: 2010-09-13
forum: Server Platforms
---

### Post by smittyatthebeach on 2010-09-13
I'm having a some pretty weird problems with some mounted file share in Ubuntu Server 10.04 LTS.


Currently we are mounting several file share stored on a SLES Files Server onto our Ubuntu Web Servers using the CIFs protocol. Occasionally ( no rhyme or reason ) we will find that when you do a directory listing on the mounted share, while you are on the Ubuntu Server, there are no files being listed. Yet if you browse the SLES File Server or any other of the identical Ubuntu Servers (with the same mounts), the files are there ready to go.

Before using SLES for our file server we tried windows, and experience many of the problem you that you see on the forums of CIFs errors on the console screen. I'm beginning to wonder if 1. we can resolve the CIFs problems in Ubuntu 10, or do we need to down grad to Ubuntu 9 or 3.) change to something other than CIFs.

I would greatly appreciate any advice or thoughts on this situation.

---

### Post by Fafler on 2010-09-13
My experience with Linux to Linux filesharing is that NFS is a lot better for things like this.

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

The server part should be pretty similar on SUSE, except for the package installation. But i'll bet you know a lot more than me about that ;)

---

### Post by arrrghhh on 2010-09-13
Yes, NFS is much better for Linux to Linux communication.  The only reason I resort to samba is for Windows clients.

---

