---
title: "What is wrong with my Samba shares ?"
date: 2011-03-17
forum: Server Platforms
---

### Post by Ghost_Mazal on 2011-03-17
Lo guys , I've been struggling since yesterday to get some shares working on SAMBA , but I just can't get it to work.
After hours going through manuals I still can't find the problem.
All I want is the homes must be shared , as well as a second share folder and the server must prompt the user for his username and password to access the shares. But it just doesn't work.

My security is set to user
Here is the shares in my smb.conf

```
[share]
comment = Ubuntu file server
path = /srv/samba/share
browseable = yes
guest ok = no
read only = no
create mask = 0755

[homes]
comment = Home Directories
browseable = no
read only = no
create mask = 0700
directory mask = 0700
valid users = %s
```

Can someone please help me , I have tried every how-to I could get my hands on , but it simply doesn't work.

Ubuntu Server 10.10 , 32bit

Thanx

---

### Post by TechSupportx86 on 2011-03-17
Edit your /etc/samba/smb.conf file and add this to the bottom:

```

[B][[COLOR=Red]test[/COLOR]]
path = [COLOR=Red]ADD/YOUR/PATH[/COLOR]
available = yes
valid users = [COLOR=Red]USERNAME[/COLOR]
read only = no
browsable = yes
public = yes
writable = yes
[/B]
```([COLOR=Red]Edit in your own path and the main username[/COLOR]) This (along with a chown command) will allow the share to show up on the network, and it WILL ask for the username AND password upon trying to connect (The "remember credentials can be clicked).

Then you must chown the directory with:

```

sudo chown -R [COLOR=Red]username[/COLOR]:[COLOR=Red]username[/COLOR] /srv/samba/share

```Source and good how-to:
[http://www.jonathanmoeller.com/screed/?p=2143](http://www.jonathanmoeller.com/screed/?p=2143)

Let me know how it goes :)

---

### Post by Ghost_Mazal on 2011-03-17
That worked , thanx man ;)

---

