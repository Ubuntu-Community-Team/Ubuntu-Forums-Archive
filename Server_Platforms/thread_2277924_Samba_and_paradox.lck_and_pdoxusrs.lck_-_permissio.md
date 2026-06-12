---
title: "Samba and paradox.lck and pdoxusrs.lck - permissions"
date: 2015-05-12
forum: Server Platforms
---

### Post by rhandy2 on 2015-05-12
Hello

I have one shared folder on Ubuntu server with paradox.db files.

But my problem is when one user open database from one windows client, they create 2 files PARADOX.LCK AND PDOXUSRS.LCK with permissions 744 for the first user. when other user try to open database, they can´t because don´t have permissions to re-write files. Folders Have permissions 770 , but I can´t fix permissions on that 2 files, because when client logout from db manager software, software delete .LCK files. The only thing I can do is have same samba user for all client machines. 
But I realy don´t like :-(

---

### Post by rhandy2 on 2015-05-13
Any suggestion?

---

### Post by volkswagner on 2015-05-13
Are you sure your pdoxusers.net location is correct for all clients?
[https://support.novell.com/docs/Tids/InfoDocument/1203264.html](https://support.novell.com/docs/Tids/InfoDocument/1203264.html)


I don't see why you can't setup group permission and force creation of file as 764. Make samba share force group and make sure
all users are added to the group so they can write to the file.

Things you want to research, force group, group sticky bit [http://unix.stackexchange.com/questions/164884/how-to-set-default-group-for-files-created-in-samba-share](http://unix.stackexchange.com/questions/164884/how-to-set-default-group-for-files-created-in-samba-share)

Also if you are running ACL's you can setup inheritance, which may help. I have found this article very helpful with samba permissions
     [http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm)

When first user runs db what are full permissions? Have first user exit then second user connect, what are permissions now?
Please post output of command below for both scenarios above.

```
ls -al /path/to/pdoxdbDir
```

---

### Post by rhandy2 on 2015-05-14
Is strange!

Is do-it before # ls-al /pathtoParadoxdir

Folder Have 770, but paradox create [COLOR=#000000]2 files PARADOX.LCK AND PDOXUSRS.LCK with permissions 744 for the first user[/COLOR]

---

### Post by volkswagner on 2015-05-14
Can you post the previously requested info?
Also post your smb.conf.

---

### Post by SeijiSensei on 2015-05-14
If you don't care about auditing the users at the OS level, you can use "force user" and "force group" to make all files in the share owned by the same Linux user.  For something like Paradox, this might be the easiest solution, if the application manages authentication and auditing itself.  I used the force user/group commands for a shared accounting application, since it handled all the user authentication.

---

### Post by rhandy2 on 2015-05-16
How I can force user and group?

---

### Post by SeijiSensei on 2015-05-16
[https://www.samba.org/~ab/output/htmldocs/manpages-3/smb.conf.5.html#FORCEUSER](https://www.samba.org/~ab/output/htmldocs/manpages-3/smb.conf.5.html#FORCEUSER)

[https://www.samba.org/~ab/output/htmldocs/manpages-3/smb.conf.5.html#FORCEGROUP](https://www.samba.org/~ab/output/htmldocs/manpages-3/smb.conf.5.html#FORCEGROUP)

Basically

1) Create a Linux user who will own the share and all the files therein.
```
sudo adduser bossman
```

2) Create the shared directory and assign ownership to the user.
```

sudo mkdir /srv/shared
sudo chown bossman:bossman /srv/shared
sudo chmod 0770 /srv/shared

```

3) Add "force user/force group" to smb.conf:
```

[sharename]
path = /srv/shared
force user = bossman
force group = bossman
[other stuff]

```

4) Restart Samba.

---

