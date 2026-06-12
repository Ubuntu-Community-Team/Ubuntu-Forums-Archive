---
title: "Samba share accessible by anyone"
date: 2013-08-19
forum: Server Platforms
---

### Post by Masteroc on 2013-08-19
Hey guys, just a quick question. I've set up my small server as a Samba share for a few computers/users. I want to have a folder available that is accessible by anyone on any type of device. So I want people to be able to go into their My Computer, click on my server and write and read from the share with no logging in and no passwords, a completely open share. 

This is my share from smb.conf (I have also enabled security = share)

[share]
    comment = Server
    path = /home/user/share
    public = yes 
    browsable = yes
    guest ok = yes
    read only = no
    writable = yes
    create mask = 0777
    directory mask = 0777
    force user = nobody
    force group = nogroup


I can easily read from this directory on a Windows machine, but when I go to create a folder it tells me that I need permission.

Thanks

---

### Post by nerdtron on 2013-08-19
A better way to do this is to create an account that can read and write to the samba share. Then give that username and password credentials to everyone who wishes to access the samba share.
Do you have a GUI? [http://www.howtogeek.com/74459/how-to-create-samba-windows-shares-in-linux-the-easy-way/](http://www.howtogeek.com/74459/how-to-create-samba-windows-shares-in-linux-the-easy-way/)
Another guide [http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-file-sharing-with-samba/](http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-file-sharing-with-samba/)

---

### Post by bab1 on 2013-08-19
> **Masteroc said:**
> Hey guys, just a quick question. I've set up my small server as a Samba share for a few computers/users. I want to have a folder available that is accessible by anyone on any type of device. So I want people to be able to go into their My Computer, click on my server and write and read from the share with no logging in and no passwords, a completely open share. 

This is my share from smb.conf (I have also enabled security = share)

[share]
    comment = Server
    path = /home/user/share
    public = yes 
    browsable = yes
    guest ok = yes
    read only = no
    writable = yes
    create mask = 0777
    directory mask = 0777
    force user = nobody
    force group = nogroup


I can easily read from this directory on a Windows machine, but when I go to create a folder it tells me that I need permission.

Thanks

What are the Linux file system permissions on the folder you have shared?  Where is it located?

This is the proper way of providing anonymous user access to an open share, but you have to setup the underlaying file and directory permissions too.

---

### Post by Masteroc on 2013-08-19
What permissions does it need? I ask since this was just a test to get samba up and running before I add the storage partition in /mnt. Right now it's just a folder in a user home directory (which NFS had no problem with). I'm pretty new to cli server setup to answer the first question about whether I had a GUI to work with. I believe the permissions were set for root and the user to rw. I assumed that setting up samba would overrule those permissions.

Thanks

---

### Post by Morbius1 on 2013-08-19
Change this:
> [share]
    comment = Server
    path = /home/user/share
    public = yes 
    browsable = yes
    guest ok = yes
    read only = no
    writable = yes
    create mask = 0777
    directory mask = 0777
    force user = nobody
    force group = nogroup
To this:
> [share]
    comment = Server
    path = /home/[COLOR=#0000cd]**user**[/COLOR]/share
    public = yes 
    browsable = yes
    guest ok = yes
    read only = no
    writable = yes
    force user = [COLOR=#0000cd]**user**[/COLOR]
Restart samba:
```
 sudo service smbd restart
```
/home/user/share has permissions of 755 or maybe 775 so a guest user has only read access. You can have an infinite number of choices to fix this:

One way is to change permissions to 777 the other is to make all your remote users appear to be the user who owns the folder being shared - that's what "force user = user" does.

---

### Post by Masteroc on 2013-08-19
> **Morbius1 said:**
> Change this:

To this:

Restart samba:
```
 sudo service smbd restart
```
/home/user/share has permissions of 755 or maybe 775 so a guest user has only read access. You can have an infinite number of choices to fix this:

One way is to change permissions to 777 the other is to make all your remote users appear to be the user who owns the folder being shared - that's what "force user = user" does.

Thanks! For some reason the first method didn't work for me (changing force user = user) but then I changed the directory permissions to 777 and it worked!

Thanks again

---

### Post by Morbius1 on 2013-08-19
Well I had assumed the owner of /home/user/share was literally the user named "user".

As in "force user = morbius" for /home/morbius/share.

[COLOR=#0000cd]**EDIT**[/COLOR]: Another way to do this is to make the owner of the shared folder nobody then you can keep the original permissions intact or even tighten them:
```
sudo chown nobody:nogroup /home/user/share
```
It all depends on how whoever "user" is in /home/user/share wants to interact with the shared folder.

---

