---
title: "Samba user problem"
date: 2008-09-07
forum: Server Platforms
---

### Post by Coolbone on 2008-09-07
Hello,

I am pretty new to the whole linux-scene but i managed to build a linux server on an old pc.

The purpose of the server in the first stage is acting as file-server and cups-printer server.

I installed samba en started to edit the config-file. This worked pretty fine and after a few try's my file-server was ready. 

The user had to log in to view his home-dir's. Now this is where te problems began. Once i logged into the server (via xp/vista) with user1 i was able to see the home-dir of user1. If i try to view the home-dir of user2 its not possible without restarting my pc the login again with user2.

Is there an easyer way of switching users?

Pleas forgive any faults made :p

Greetz Coolbone

---

### Post by puppywhacker on 2008-09-07
In the windows explorer you can go to the menu 'tools' and 'map network drive' there you can specify the folder like \\oldpc\user1. At 'finish' it should ask you to 'connect as' so you fill in the user1/pass1

Two access the second home folder you have to right-click the mapped network drive and select 'disconnect' before you can connect to the user2 home directory.

In the Samba conf I believe you need to specify 
security = user

goodluck

---

### Post by Coolbone on 2008-09-07
I tryed that allready but it didnt worked.
edit: i think i found something : [http://help.lockergnome.com/linux/samba-connection-XP-ftopict420098.html](http://help.lockergnome.com/linux/samba-connection-XP-ftopict420098.html)
but in my /etc/samba/ map there is no smbusers.

Also if i put security = user in my smb.config file and i do testparm it isnt there

---

### Post by kamaji792 on 2008-09-19
I don't think the solution you found it what you want.  They were talking about 'switching users'.  i.e. logging out as one user and then logging back in as another user.

If you are still looking for a solution I have a question.  Why do you want to look at the files in the directory of the other user?

You could create a separate share that either user could access.  To do that  try adding the following to the bottom of the /etc/samba/smb.conf file:
```
[ShareNaem]
        comment = Network Attched Storate
        path = /path/to/share
        valid users = user1, user2
        read only = No
        create mask = 0770
        directory mask = 0770

```

All the best

---

