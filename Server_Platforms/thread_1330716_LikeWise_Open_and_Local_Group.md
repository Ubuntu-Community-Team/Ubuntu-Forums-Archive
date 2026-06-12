---
title: "LikeWise Open and Local Group"
date: 2009-11-18
forum: Server Platforms
---

### Post by Zeon100 on 2009-11-18
Hi,
I am trying to achieve a setup where remote users can upload files via sftp to our Ubuntu server. We can then pull these off via Samba file server to our local windows server via SMB. They remote users need to login with their active directory username/passwords.

So I have installed the following:

[LIST]
[*]Like Wise Open 5
[*]OpenSSH with Chroot and sftponly (as described in this thread):
[http://ubuntuforums.org/showthread.php?t=1057657&highlight=ssh+home+directory](http://ubuntuforums.org/showthread.php?t=1057657&highlight=ssh+home+directory)
[*]Samba
[/LIST]
Like Wise open 5 install went fine and so did the install and setup of openssh. However in the guide for openssh, there is a step where the user you want to limit chroot with needs to be added to a group. How can this be done with likewise open?

---

### Post by Zeon100 on 2010-01-10
It seems that if you manually add the user to the sftponly group in /etc/groups then it will works even though it may not show up when you list the groups of a particular user.

e.g.

```

#sudo vi /etc/groups

```then edit the sftponly group and add your users e.g.

```

sftponly:x:1234:user1,user2

```

---

