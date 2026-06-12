---
title: "Problems with charsets/encoding in samba between hardy and intrepid"
date: 2009-10-04
forum: Server Platforms
---

### Post by hkais on 2009-10-04
Hello all,

I use hardy as a samba server (samba 3.0.28a). I am running hardy with en_US.UTF-8 locale. My users are german natives. Their operating systems are Windows and Linux. Windows clients can work fine with german umlauts. But the Linux users report problems with the german umlauts.

I am running samba server with
dos charset = 850
unix charset = utf8

This is working fine with Windows. Windows sees umlauts also the umlauts are display properly on the hardy samba server.

Linux-clients report problems with german umlauts.
I have here a Ubuntu intrepid client. The client has a en_US.UTF-8 locale set.
The mount is done by fstab 
```
//hardy/share /mnt/hardy/share cifs username=user,uid=user,gid=user,iocharset=utf8,noauto
```
I tried all permutations with iocharset=utf8 and mapchars. Every create of files/dirs with german umlauts on intrepid creats unreadable characters on hardy-samba-server. The chars are also unreadable for windows.
Pretty odd is the fact, that smbclient on intrepid is displaying the umlauts properly and can also create umlaut files and folders properly.

Can anyone help me?

---

