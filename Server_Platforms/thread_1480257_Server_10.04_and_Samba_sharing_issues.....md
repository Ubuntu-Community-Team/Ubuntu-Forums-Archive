---
title: "Server 10.04 and Samba sharing issues...."
date: 2010-05-11
forum: Server Platforms
---

### Post by jahservant on 2010-05-11
I'm quite familiar with Ubuntu, but still new to Samba.  I'm using Ubuntu 10.04, and I'm trying to create a share "myshare" that will give read-only permissions to one group but will allow write access to another group.

Here's the catch: Samba is connecting to a Microsoft Server's Active Directory, and the permissions need to be set by  the M$'s groups.

In other words, I want the group "MYCOMP\\Domain Users" to have read-only access to "myshare", but I need "MYCOMP\\Domain Admins" to have write access as well.

I've seen a lot out there, such as adding this to my smb.conf:
[INDENT][myshare]
path = /mnt/myshare
valid users = @"MYCOMP\\Domain Users"
read only = yes
write list = @"MYCOMP\\Domain Admins"[/INDENT]

But alas, nothing works. Either both groups have write access or both groups have read-only access.

Has anyone been able to get something like this to work?

(P.S. I know this is a Samba question on an Ubuntu forum; I just figured that, since I can't get my answer elsewhere, the wealth of expertise in the Ubuntu community could give me a hand....)

---

### Post by BobVila on 2010-05-11
> **jahservant said:**
> I'm quite familiar with Ubuntu, but still new to Samba.  I'm using Ubuntu 10.04, and I'm trying to create a share "myshare" that will give read-only permissions to one group but will allow write access to another group.

Here's the catch: Samba is connecting to a Microsoft Server's Active Directory, and the permissions need to be set by  the M$'s groups.

In other words, I want the group "MYCOMP\\Domain Users" to have read-only access to "myshare", but I need "MYCOMP\\Domain Admins" to have write access as well.

I've seen a lot out there, such as adding this to my smb.conf:[INDENT][myshare]
path = /mnt/myshare
valid users = @"MYCOMP\\Domain Users"
read only = yes
write list = @"MYCOMP\\Domain Admins"[/INDENT]But alas, nothing works. Either both groups have write access or both groups have read-only access.

Has anyone been able to get something like this to work?

(P.S. I know this is a Samba question on an Ubuntu forum; I just figured that, since I can't get my answer elsewhere, the wealth of expertise in the Ubuntu community could give me a hand....)

Forgive the silly question, but have you set up AD Authentication on the box?

---

### Post by jahservant on 2010-05-12
Yes, I've set up AD Authentication on the box, and it seems to be working.

"wbinfo -u" gives me all of the users on the domain and "wbinfo -g" gives me all the groups.

And, adding
[INDENT]valid users = @"MYCOMP\\Domain Users"[/INDENT]
to smb.conf gives access to all of the domain users using their domain, username, and password authenticatin.

So yeah, AD Authentication is set up and working great ^_^

---

### Post by Boondoklife on 2010-05-12
> **jahservant said:**
> I'm quite familiar with Ubuntu, but still new to Samba.  I'm using Ubuntu 10.04, and I'm trying to create a share "myshare" that will give read-only permissions to one group but will allow write access to another group.

Here's the catch: Samba is connecting to a Microsoft Server's Active Directory, and the permissions need to be set by  the M$'s groups.

In other words, I want the group "MYCOMP\\Domain Users" to have read-only access to "myshare", but I need "MYCOMP\\Domain Admins" to have write access as well.

I've seen a lot out there, such as adding this to my smb.conf:[INDENT][myshare]
path = /mnt/myshare
valid users = @"MYCOMP\\Domain Users"
read only = yes
write list = @"MYCOMP\\Domain Admins"[/INDENT]But alas, nothing works. Either both groups have write access or both groups have read-only access.

Has anyone been able to get something like this to work?

(P.S. I know this is a Samba question on an Ubuntu forum; I just figured that, since I can't get my answer elsewhere, the wealth of expertise in the Ubuntu community could give me a hand....)

this comes out of my samba conf on a small box here.

```
valid users=@domainadmins @domainusers
write list=@domainadmins
read list=@domainusers
```of course this depends on the groups existing.

---

### Post by jahservant on 2010-05-12
Boondoklife: I tried what you gave me:
[indent][myshare]
path = /mnt/myshare
valid users = @"MYCOMP\\Domain Users", @"MYCOMP\\Domain Admins"
write list = @"MYCOMP\\Domain Admins"
read list = @"MYCOMP\\Domain Users"[/indent]

But the "Domain Admins" users don't have write access.  Everyone can read fine, but the Admins can't edit files or create new ones....

Am I missing something?  I've double and triple checked everything but it doesn't seem to be working....

---

### Post by Boondoklife on 2010-05-12
```
[Music]
comment = Music
path=/shares/internal/media/Music
guest ok=no
force group = domainadmins
force user = %U
create mode = 0666
directory mode = 0777
valid users=@domainadmins @domainusers
write list=@domainadmins
read list=@domainusers
```

This is exactly what I have in mine, NOTE there is not a comma in any of them.

---

### Post by jahservant on 2010-05-13
Hmm. Still no luck.  Administrators can't edit files or create new ones.

I found a bunch of these in /var/log/samba/log.nmbd, which seems to be occuring everytime an admin tries to create or edit a file:
```

[2010/05/13 09:35:59,  0] nmbd/nmbd_serverlistdb.c:354(write_browse_list)
  write_browse_list: Fatal error - cannot find my workgroup MYCOMP

```

I checked with the kinit and wbinfo commands and everything seems to be working fine -- I don't understand what "cannot find my workgroup" means.

Thanks for all the help!

---

### Post by Boondoklife on 2010-05-13
> **jahservant said:**
> Hmm. Still no luck.  Administrators can't edit files or create new ones.

I found a bunch of these in /var/log/samba/log.nmbd, which seems to be occuring everytime an admin tries to create or edit a file:
```

[2010/05/13 09:35:59,  0] nmbd/nmbd_serverlistdb.c:354(write_browse_list)
  write_browse_list: Fatal error - cannot find my workgroup MYCOMP

```I checked with the kinit and wbinfo commands and everything seems to be working fine -- I don't understand what "cannot find my workgroup" means.

Thanks for all the help!

Sounds like it is having an issue finding your groups, did you map them correctly to the samba server? I have not used samba in a Domain member so not sure it this is a limitation.

---

### Post by jahservant on 2010-05-13
I created a new group on the M$ Windows server and tried that instead of "Domain Admins", and it worked!  I then deleted the new group I created and tried "Domain Admins" again, and it started working.

I don't know what the heck was going on with that, but it's working now and I'm satisfied enough with that.

Thanks a lot Boondoklife!

---

