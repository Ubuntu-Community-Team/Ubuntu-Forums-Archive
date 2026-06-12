---
title: "Vsftpd and user specific settings"
date: 2010-01-24
forum: Server Platforms
---

### Post by matchett808 on 2010-01-24
I just set up my own server and basically my folder is on say /media/disk1/ and my girlfriends is on /media/patato/ is there a way i can set it so that if i log in it goes to my folder and if she does it goes to hers....

I've currently got it set up as /media/ that it goes to but i cant get it to change it for each user (we can also browse each others drive and we dont want that, we want to be tied into /media/ourdirectory and all of its subdirectories) problem is that it is running on a computer that use to be functional (same install because I cant find my disk drive) so it cant use home folders....(would this work through some sort of simlink?)

I have been through all the vsftpd stuff that i can find (but cant find the soloution)...

I'm a lil stuck lol.......

---

### Post by chuina on 2010-01-25
This might solve your problem.

1.enable chroot to restrict all user in their home directory.
```
sudo gedit /etc/vsftpd.conf
```

2.Delete the #(hash) before the line #chroot_local_user=YES
So, it is now ```
chroot_local_user=YES
```

3.Restart ftp server
```
sudo service vsftpd restart
```


Go to
System->Administration->Users and Groups

Click on the keys icon and give password for sudo privilige.

Now create an user e.g. romeo (under account tab) with the home (under advanced tab) e.g. /media/disk3.

Create another user e.g. juliet with another home directory, e.g. /media/apple

Try ftp login and view others directory.
Should be failed.

---

