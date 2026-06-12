---
title: "How to create separate list of samba users."
date: 2011-08-19
forum: Server Platforms
---

### Post by honey_bee on 2011-08-19
hi,
I want to use samba in ubuntu.For samba users i make a user in my linux box like


# useradd smith
# useradd jone

These users can also login into my ubuntu system if they want.** For samba I want to know that, is there any way to create separate  valid list of samba users so that they may access files from windows xp.**

Thanks in advance,
honey

---

### Post by hawk2010 on 2011-08-19
All you need to do is 
in your /etc/ssh/sshd_config put the following

AllowUsers user1,user2 (these users will be logging into your linux both via ssh) by this we prevent other samba users logging into your box.

You can further group unix users so you can further control

---

### Post by luvshines on 2011-08-19
If I understand your question correctly, do you want to stop some samba users from ssh while allowing others to ssh ?
I think you should be able to control this by changing the login shell for those users to '/usr/sbin/nologin'.

Please note that adding 'AllowUsers' parameter in sshd_config file will limit ssh to only those users listed against it. That is you won't be able to ssh with any user other than those listed against 'AllowUsers'

---

### Post by Morbius1 on 2011-08-19
Maybe it's just me but I read through the entire original post several times ( it's short ) and I did not see any reference to ssh at all.

The post is somewhat confusing however so I'm going to interpret it this way:

* I've got users smith and jones who can login to my local box and have home directories.

* Can I have users bob and ted that don't have home directories or local login capabilities but can access my shares from WinXP?

Yes you can.

Create a user named bob that has no home directory or local login capability:
```
sudo useradd -s /bin/true bob
```Then add him to the samba database:
```
sudo smbpasswd -a bob
```

---

### Post by honey_bee on 2011-08-23
Thanks "Morbius1" for your kind reply. Well if I summaries all this then it is.

"Create a user named bob that has no home directory or local login capability:

[PHP]sudo useradd -s /bin/true bob[/PHP]

Then add him to the samba database:

[PHP]sudo smbpasswd -a bob"[/PHP]

***Well my question is is there anyway to create users specifically for Samba and we add that users in a separate file in samba.If there is no way then your answer is the best solution .***

thanks
honey.

---

### Post by bab1 on 2011-08-23
> **honey_bee said:**
> Thanks "Morbius1" for your kind reply. Well if I summaries all this then it is.

"Create a user named bob that has no home directory or local login capability:

[PHP]sudo useradd -s /bin/true bob[/PHP]

Then add him to the samba database:

[PHP]sudo smbpasswd -a bob"[/PHP]

***Well my question is is there anyway to create users specifically for Samba and we add that users in a separate file in samba.If there is no way then your answer is the best solution .***


You have to be a local (Linux) user first```
sudo useradd -s /bin/true bob
```

Then you can create a separate Samba user (and password) in the smbpasswd file```
sudo smbpasswd -a bob"  
```

If you don't create the Samba user then Samba will consider you a guest.  It will then map you to whatever you have configured as guest.  The default guest user is the user nobody.

I think Morbius1 answered the question.  What other *separate *list where you thinking of?  You can see this separate list of Samba users with the command *pdbedit * like this```
sudo pdbedit -L
```

from the pdbedit man pages```
pdbedit - manage the SAM database (Database of Samba Users)
```

---

### Post by honey_bee on 2011-08-23
thanks a lot for help :popcorn:

---

### Post by Sanados on 2011-08-23
actually you can sync samba with your passwd to keep those files in sync and password changes apply to samba users aswell.

To maintain the samba accesslist i would bind the share to a user group ( smb.conf: users = @sambausers) and then add the samba users to that specific group

And the shell for all users should be nologin or false on router anyway. (which user really needs ssh???)
But then again you have to remember that the user who needs ftp also needs a valid shell.
So if you set all shells to /bin/false remember to add /bin/false to /etc/shells that the ftp server recognizes /bin/false as shell and allows the user to login into ftp.

---

### Post by honey_bee on 2011-08-25
thanks "Sanados" for the reply. Well can you elaborate your statement ?

---

