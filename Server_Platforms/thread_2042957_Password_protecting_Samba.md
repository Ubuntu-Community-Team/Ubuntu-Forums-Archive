---
title: "Password protecting Samba"
date: 2012-08-15
forum: Server Platforms
---

### Post by kwinsw on 2012-08-15
Hi,

I’m having some trouble. I want to create some password protected Samba shares, but it’s not working.

I’m using Ubuntu Server 12.04 and have been following the guide here:

[https://help.ubuntu.com/12.04/serverguide/samba-fileprint-security.html](https://help.ubuntu.com/12.04/serverguide/samba-fileprint-security.html)

This is what I’ve done so far:

1. Install samba server using sudo apt-get install samba.
2. In smb.conf I’ve specified security = user. 
3. I then added the following section to smb.conf

[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = no
    read only = no
    create mask = 0755

4. Next I created /srv/samba/share and set its permissions using sudo chown nobody.nogroup. 
5. I then installed libpam-smbpass
6. I add one of my system users as a Samba user and enable the account with:

	sudo smbpasswd -L -a username
        sudo smbpasswd -L -e username

7. Finally, I restart nmbd and smbd. 

I know I must be missing something, as when I try to connect to the share from a Windows 7 client I get the error message:

\\servername\share is not accessible. You might not have permission to use this resource...

Can anyone tell me where I’m going wrong or point me in the direction of a good step- by-step guide?

Any and all help, hints or tips would be much appreciated.

Cheers

kwinsw

---

### Post by cariboo on 2012-08-17
Seeing as this is a server related problem, you may can an answer here, rather than in ABT.

---

### Post by volkswagner on 2012-08-18
It appears that guide is missing important info like adding samba user.

Did you add yourself to the samba user list with 
```
smbpasswd
```

Here is a link that may help
[http://ubuntuforums.org/showthread.php?t=837509](http://ubuntuforums.org/showthread.php?t=837509)

---

### Post by Morbius1 on 2012-08-18
Just some random thoughts:

[1] There's 2 sets of permissions at play here. The Samba permissions ( guest ok, read only ) and Linux file permissions, They must be in sync. So what are the permissions of the shared folder and do they allow "username" to have access:
```
ls -dl /srv/samba/share

```[2] Speaking of permissions:
> Next I created /srv/samba/share and set its permissions using sudo chown nobody.nogroup. 
The remote user is not coming across as "nobody" because you specfied "guest ok = no". Everyone will be somebody so you need to find out what the permissions are for "other" - See item [1].

[3] I honestly believe that libpam-smbpass was created to insure that people will go insane. It has only one function in life: Every time you reboot it automatically sets the samba password for a given user to his local login password on the server.

Why in the world would you ever want that to happen? If this was a Server with a big "S" that's sitting on raised floor somewhere behind locked doors then fine. But if this server is in your home then everyone now has local access to the physical server itself. Insane.

Anywho, You can set the samba password as you have in your post but if the samba password is different from that users login password libpam-smbpass will override it at the next reboot.

---

