---
title: "Samba Active Directory Shares?"
date: 2009-09-16
forum: Server Platforms
---

### Post by geek-n-out on 2009-09-16
Hey everyone,

First things first UBUNTU SERVER ROCKS!!!! :guitar:

I currently am implementing an ubuntu 9.04 server box for file sharing in a windows network.  I have read lots and lots of articles and samba docs and posts and AHHHHHHHHHHHHHHHHHHHHH.... ok you get the point.

Here's my issue...

I installed Ubuntu 9.04 server edition...
Used likewise open to attach it to the domain (bad *** by the way!!! love it!!)
install samba
set up the share:
```


[share]
path = /var/samba/share
browseable = yes
public = no
write list = @"Domain Group" user
read list = @"Domain Read Group"
admin users = @"Domain Admins"


```

Then I used :

```


setfacl -m u:username:rwx /var/samba/share/IT
setfacl -m g:group:rwx /var/samba/share/IT


```

this works beautifully...

The problem is if I remove the write list line from the samba share the username/group that I set to be able to rwx can't write to the directory. My question is how do you set up the share similar to windows, user can read to their directory, but write in their directory?  I can do this in windows, but I can't seem to figure it out in linux.  I for obvious reason's don't want production users having really any rights to HR, Accounting, etc.  I need to be able to tighten security without creating 10 shares.

---

### Post by geek-n-out on 2009-09-16
Figured it out on my own here is the solution if anyone else needs to know:

In smb.conf:

the share should be as follows:

```


[share]
comment = share comments
path = /path/to/filetoshare
browseable = yes
public = no
writable = yes
admin users = @"Domain Admins"


```

The above code makes the directory writable... I misunderstood this to mean to everyone, it's just so anyone can write to it, but they have to have rights too.

Here is how you give them rights to write to the files below the main share:

```


setfacl -m u:username:rwx /path/to/filetoshare

or

setfacl -m g:groupname:rwx /path/to/filetoshare


```

you might have to install acl...

```


sudo apt-get install --yes acl


```

if you have to install acl don't forget to add it as an option to the drive that houses the share and either reboot or remount that share.

Ok well thats it so I guess this can be marked as solved.  LOL

Thank you me. :P

---

