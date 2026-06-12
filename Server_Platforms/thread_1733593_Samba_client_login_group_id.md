---
title: "Samba client login group id"
date: 2011-04-19
forum: Server Platforms
---

### Post by BCven86 on 2011-04-19
Hi,

I set up a Samba server with several folder shares that is to be accessed by both Windows and Linux users. For the most part everything works great, however I am concerned about the permissions. I want to share several mounted external drives (/media/[disk1], /media/[disk2], etc.) that are set up to mount with permissions 770 through fstab with uid=nobody and gid=group1. 

Clients access the shares with username/smbpasswd, where the "username" is a username that has been created on the linux server. On the linux server, each of the relevant usernames has been appropriately placed in "group1". I share the drives using smb.conf:

```

[disk1]
   read only = no
   browseable = yes
   path = [share folder]
   guest ok = no
   create mask = 0777

```When I mount the share remotely from a client linux system I have rwx =  0 permission, i.e. I cannot read/write/execute the files, despite the fact that the username I log in with is part of "group1" on the server. If, instead, I mount the drives on the server with 777 permissions I *am* able to access the files. My interpretation is that when I log in remotely I am given "others" permissions rather than "group" permissions as I would like. 

My question is, how can I make it so the user groups associated with the username with which the client accesses the share are the same user groups associated with the username on the linux server. I tried adding 
```

force group = group1

```to the smb.conf configuration but that neither worked nor is what I want to do in the end.

I appreciate any help,
Bob

---

### Post by BCven86 on 2011-05-16
Anyone?

---

