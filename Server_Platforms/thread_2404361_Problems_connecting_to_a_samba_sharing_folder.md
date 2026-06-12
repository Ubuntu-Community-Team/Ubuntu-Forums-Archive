---
title: "Problems connecting to a samba sharing folder"
date: 2018-10-23
forum: Server Platforms
---

### Post by dam034 on 2018-10-23
Dear users,

I have a LAN server with samba service.

I have these folders:
```
root@lanserver:/srv/sharings# ls -ahl
total 64K
drwxrwxr-x  8 peter admin 4,0K mar 22  2018 .
drwxr-xr-x 11 root  root  4,0K may  3 21:02 ..
drwxrwxr-x  8 peter admin  36K oct  4 18:09 music
drwxrwx--- 30 jack  admin 4,0K mar 23  2018 private
drwxrwxrwx  4 peter admin 4,0K oct 20 12:22 write
drwxrwxr-x  3 peter admin 4,0K jun 21 20:09 service
drwxrwxr-x 13 peter admin 4,0K sep 10 08:42 temporarily
drwxrwxr-x  4 peter admin 4,0K aug 14 17:22 videos
```

When I try to connect to "music", "write", "service", "temporarily" and "videos" sharings I don't have any problem. When I try to connect to "private" sharing with jack username and password, I get authentication error.

The smb.conf is this:
```
[music]
available = yes
browseable = yes
path = /srv/sharings/music
read only = yes
guest ok = yes
create mask = 0775
directory mask = 0775

[private]
available = yes
browseable = yes
path = /srv/sharings/private
read only = no
public = yes
create mask = 0770
directory mask = 0770

[write]
available = yes
browseable = yes
path = /srv/sharings/write
read only = no
public = yes
create mask = 0777
directory mask = 0777

[service]
available = yes
browseable = yes
path = /srv/sharings/service
read only = no
public = yes
create mask = 0775
directory mask = 0775

[temporarily]
available = yes
browseable = yes
path = /srv/sharings/temporarily
read only = no
public = yes
create mask = 0775
directory mask = 0775

[videos]
available = yes
browseable = yes
path = /srv/sharings/videos
read only = yes
guest ok = yes
create mask = 0775
directory mask = 0775
```

I want this configuration:
[LIST]
[*]"music", "service", "temporarily" and "videos" sharings accessible from anyone without authentication, with read-only permission (and it works)
[*]"write" sharing accessible from anyone without authentication, with read/write permissions (and it works)
[*]"private" sharing accessible only from "jack" user (and his password), with read/write permissions
[/LIST]

I can't do the third part I wrote.

How can I fix this issue?

Thanks

---

### Post by Morbius1 on 2018-10-23
The Linux permissions on "private" look right for access by "jack" ( drwxrwx--- 30 jack  admin 4,0K mar 23  2018 private )

Your share definition looks right for access by jack - but only if you force it because you designated it as a public share:
> [private]
available = yes
browseable = yes
path = /srv/sharings/private
read only = no
public = yes
create mask = 0770
directory mask = 0770

*[COLOR=#0000cd]**Side note:**[/COLOR]* That share definition is not doing what you stated: ""private" sharing accessible only from "jack" user (and his password), with read/write permissions". That share is accessible to everyone.
The Linux permissions on that folder will limit actual access only to jack and any user that is a member of the admin group so if you want it to be accessible only to jack then specify that in your share definition:
> [private]
available = yes
browseable = yes
path = /srv/sharings/private
read only = no
[COLOR=#0000cd]**valid users = jack**[/COLOR]
create mask = 0770
directory mask = 0770

The only thing you did not mention is if you added jack to the samba password database:
```
sudo smbpasswd -a jack
```

---

### Post by dam034 on 2018-10-23
Now I have:
[list]
[*]how can I define the share "private" according linux permissions? (valid users = jack + admin group)
[*]if I add jack to samba password db, it gets jack's password from linux users? And updates it if I update linux jack's password?
[*]"private" now isn't accessible only because the linux permission is 770? Then the share definition is same as "write"?
[/list]

Thanks

---

### Post by Morbius1 on 2018-10-23
There are two sets of permissions going on here.

Linux permissions are the ultimate authority of what can be done to a folder. The samba share definition is the network gatekeeper to that folder. You could make the permissions of the folder 777 allowing everyone access but if you set valid users = jack only jack will be able to gain access to the share from the network.
> 
[LIST]
[*]how can I define the share "private" according linux permissions? (valid users = jack + admin group) 
[/LIST]

From a linux perspecive you have already done that. From a Samba perspecive you change valid users = jack to:
```
valid users = jack @admin
```
> 
[LIST]
[*]if I add jack to samba password db, it gets jack's password from linux users? And updates it if I update linux jack's password? 
[/LIST]

Nope. There are two sets of passwords: The Linux login password for that user and the samba password for that user. When you run the smbpasswd command you will be asked for the samba password. You  can make it the same as the login password if you want.

---

### Post by dam034 on 2018-10-23
> **Morbius1 said:**
> From a Samba perspecive you change valid users = jack to:
```
valid users = jack @admin
```
This now works fine.

> **Morbius1 said:**
> Nope. There are two sets of passwords: The Linux login password for that user and the samba password for that user. When you run the smbpasswd command you will be asked for the samba password. You  can make it the same as the login password if you want.
I created a "guest" user on linux with a password and without sudo permissions. If I'm connecting to a sharing folder from windows 10, I can't connect as anonymous, so I enter the "guest" username and password, taken from the linux users, not samba users.
Why guest user works from linux users to samba users and jack not?

Thanks

---

### Post by Morbius1 on 2018-10-23
> If I'm connecting to a sharing folder from windows 10, I can't connect as anonymous
I have no idea why you can't access your public shares without passing credentials. I can with my Win10 machine.
> so I enter the "guest" username and password, taken from the linux users, not samba users.
Great! Sounds like it would accept any name with any password to me.
>  Why guest user works from linux users to samba users and jack not?
Can not answer that question as I cannot reproduce your symptoms.

---

### Post by volkswagner on 2018-10-23
When connecting from a Windows computer, you often can't 
connect to a share truly anonymously. You need to send some
bogus user/password first (that's why you were able to connect 
as the "guest user").  You don't need to create a guest user, just 
have users on the network use windows with a password on their
workstation. If they had a password, Windows would try to authenticate
as that user first (and samba should map it to bad user = guest).

Hopefully I'm correct and your windows user doesn't have a password set.
There are other anomalies created when the Windows user does have a 
user/password set, and username exists in SAMBA DB, but passwords don't match.

---

### Post by dam034 on 2018-10-24
Attention, not to confuse the anonymous user with the guest user, that I created specifically with a password to allow access from win10, otherwise I would have had an error.

Now, on a ubuntu desktop client, if I navigate the explorer and I write smb://server-ip/private entering jack and his password, it works fine.

But if I try to mount in CLI, I get this error:
```
root@ub-gaming:/tmp# mount -t cifs //server-ip/private privfiles -o username=jack,password=hispw,dir_mode=0777,file_mode=0777,iocharset=utf8
mount: wrong fs type, bad option, bad superblock on //server-ip/private,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
```

How can I fix client-side?

Thanks

---

### Post by Morbius1 on 2018-10-24
Looks like you are missing cifs so install it:
```
sudo apt install cifs-utils
```
And you are missing a mount point.
>  mount -t cifs //server-ip/private [COLOR=#0000cd]**/home/your-user-name/privfiles**[/COLOR] -o username=jack,password=hispw,.....

---

### Post by dam034 on 2018-10-29
Now I can mount the sharing.

But I have problems with the permissions, this is the terminal client-side:
```
root@ub-gaming:/tmp# mount -t cifs //server-ip/private privfiles -o username=jack,password=hispw,dir_mode=0777,file_mode=0777,iocharset=utf8
root@ub-gaming:/tmp# ls -ahl
total 72K
drwxrwxrwt  13 root    root     20K oct 29 10:52 .
drwxr-xr-x  23 root    root    4,0K oct  9 18:47 ..
drwxrwxrwt   2 root    root    4,0K oct 29 10:39 .font-unix
drwxrwxrwt   2 root    root    4,0K oct 29 10:40 .ICE-unix
drwxrwxrwx+ 31 1002    1001       0 oct 23 15:28 privfiles
[other folders]
```
I can't navigate the privfiles folder, I don't have the permissions.

How can I fix this issue?

Thanks

---

### Post by Morbius1 on 2018-10-29
I was going to suggest you add **nounix **to your list of options but then I noticed this:
> drwxrwxrwx[COLOR=#ff0000]**+**[/COLOR] 31 1002    1001       0 oct 23 15:28 privfiles
Why are you messing about with ACLs. Just to make this more complicated than it needs to be?

---

### Post by dam034 on 2018-10-29
I can't understand what you wrote.

I don't know what is nounix.

Can you suggest me a easier way to mount a sharing folder?

In ubuntu desktop, surfing the explorer, I can mount the folder fast, without problems.

Thanks

---

