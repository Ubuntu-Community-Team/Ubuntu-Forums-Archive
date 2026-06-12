---
title: "Ubuntu File Server for Windows Network"
date: 2006-08-07
forum: Server Platforms
---

### Post by egraham on 2006-08-07
I am fairly new to Linux.  I am trying to add a Ubuntu Server to my Windows network as a file server.  I have been able to join the server to AD.  I would like for my Windows users to access the shares on the Ubuntu server without having to input another username and password.  I have searched these forums and Googled it and haven't been able to find a solution for me.

Any help would be appreciated!

Eric

---

### Post by pertu on 2006-08-07
Eric,

Try to add the same user that you use on windows into your samba database.

1) Add a linux user:
useradd "username" -m -G users

2) Add the linux user to the SAMBA password database:
smbpasswd -a "username"



*Use the same password for windows and SAMBA.

---

### Post by egraham on 2006-08-07
We are talking around 65 users In a corporate environment.

---

### Post by Glut on 2006-08-07
Your nsswitch service will need winbind to access windows users. Apt-get install winbind and edit /etc/nsswitch.conf such that passwd, group & shadow look at winbind in addition to files.

---

### Post by egraham on 2006-08-09
I have my Ubuntu box on the Domain I can see it in My Network Places, if I am logged into one of my Windows machine as Admin I can open up the Ubuntu box, but need to input another username and password when I try to access a shared folder, if I am in as any other user I have to input a username and password when tying to access the Ubuntu box from My Network Places.  On the Ubuntu box I can do wbinfo -u and -g and get the list of AD users and groups from my 2003 AD Server.

What am I missing to give all users access to a share onthe Ubuntu box without having to input another username and password?

Since I last posted this I can now access a shared folder on my Ubuntu from a Windows box when logged in as Administrator but still no other users.

---

### Post by AndyW on 2006-08-10
I just did this the other day
either read only [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DNo.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DNo.29)
or read and write
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29)
;)

---

### Post by Glut on 2006-08-10
Does admin have a local account on the linux box?
What are the logs saying in /var/log/samba/log.ipaddress.or.name

---

### Post by datakid on 2006-08-10
> **pertu said:**
> Eric,

Try to add the same user that you use on windows into your samba database.

1) Add a linux user:
useradd "username" -m -G users

2) Add the linux user to the SAMBA password database:
smbpasswd -a "username"

*Use the same password for windows and SAMBA.

Maybe you could write a quick batch script to do this, and iterate over the names/passwds?
ie, put them all in a txt file, comma seperated, and then loop over that - I don't know how to do that myself, but that's where I'd start.

Unless of course, you are going to let everyone view the shares anyway and are behind a firewall - in that case surely guest = ok in the smb.conf would suffice?

---

### Post by egraham on 2006-08-10
> **Glut said:**
> Does admin have a local account on the linux box?
What are the logs saying in /var/log/samba/log.ipaddress.or.name

Here is what the log says:
[2006/08/09 15:33:49, 1] smbd/sesssetup.c:reply_spnego_kerberos(197)
  Failed to verify incoming ticket!

---

### Post by egraham on 2006-08-10
It appears as though I have it working the way I want it.  Thank you all for your help.

I have one additional question, how would I give access to one folder to 2 seperate users?

---

### Post by Glut on 2006-08-10
Can I ask what the issue was?

In the share definition:
valid users = fred,jane

---

### Post by egraham on 2006-08-11
What I ended up doing was what pertu is suggesting and adding my users, which will take some time but has been the only way I can get it to work.  I also had to go in and uncomment some enties under the Share Directories section in the smb.conf file.
```

[homes]
   comment = Home Directories
   browseable = no

   valid users = %S

   writable = yes

```
This gives only my users I create access to their folder that is created when I add them to the Ubuntu box.

As for your answer to my last question it would look something like this?
```
[allusers]
    comment = All Users
    path = /home/shares/allusers
    valid users = bjones,msmith
    create mask = 0660
    directory mask = 0771

```

Again thanks to all who gave input!:KS

---

### Post by Glut on 2006-08-13
Yep

---

