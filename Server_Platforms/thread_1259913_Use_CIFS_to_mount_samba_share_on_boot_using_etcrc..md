---
title: "Use CIFS to mount samba share on boot using /etc/rc.local"
date: 2009-09-06
forum: Server Platforms
---

### Post by rioguia on 2009-09-06
I have a samba server (CENTOS 5.3). The server has a share called "export_name." For the purpose of this question, the share has no password.

I want to mount "export_name" automatically when I boot on a client (UBUNTU 9.4). The mountpoint is called "/home/my_local_user_name/export_name."

I have added this single line to the /etc/rc.local file on the UBUNTU client, saved it, and set the executable bit (chmod + /etc/rc.local). The line is as follows:

mount -o username=user //192.xxx.xxx.xxx/export_name /home/my_local_user_name/export_name

This rc.local file does not work on boot but works only when I open a terminal and type:
sudo sh /etc/rc.local

---

### Post by Iowan on 2009-09-08
Have you seen [this]("http://ubuntuforums.org/showthread.php?t=288534") one?

---

### Post by rioguia on 2009-09-15
Thanks Iowan for your post and to all who read my question.  The Firestarter piece was a great article.  In the end, it appears that I mis-configured the Samba server's SE Linux setting.  The server's logs in /var/log/samba showed that the client did not have permissions.  I had to read the logs in /var/log/secure to discover the SE Linux problem.  Given that variable, it's hard to say what (if anything) was wrong with the samba client's configuration.

---

