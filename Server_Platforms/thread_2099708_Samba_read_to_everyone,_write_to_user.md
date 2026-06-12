---
title: "Samba: read to everyone, write to user"
date: 2012-12-30
forum: Server Platforms
---

### Post by boone58 on 2012-12-30
I' hoping this is possible. I have a share with music. I'm trying to make it write by me only but readable to everyone. I don't want everyone on my network to be able to delete files, which is what will happen if it's read/write to everyone. I've tried

```
force user = boone
browseable = yes
guest = ok
guest only = no
valid users = boone, @users
```which still leaves me with read only to everyone.
Ive tried several different ways and end up with read/write to all known users or read/write to everyone. 

I have the ubuntu samba server guide open in a pdf and several other samba guides open in tabs, but none show me how to do what I want. I know there must be a way to do this.

Note, this is on a headless 12.04 LTS server which I've been using as a web server for quite a while, but I'd really like to get samba configured correctly so I can get rid of my M$ server.

---

### Post by ranger12 on 2012-12-30
Hi, I am guessing since you are using the Server guide and judging from your post that you have already tried create mask = and directory mask = on the share? How about create mask = 755 and  directory mask = 755?

---

### Post by boone58 on 2012-12-30
Thanks for the reply, and yes I did that. I'm thinking it's something simple that I'm overlooking. Perhaps it's just the order in smb.config

---

### Post by Morbius1 on 2012-12-30
Not sure if I understand the requirement but as I read it you want a read only share to everyone but writeable to only one user - boone. If that is correct:

Change this:
> force user = boone
browseable = yes
guest = ok
guest only = no
valid users = boone, @usersTo this:
> 
browseable = yes
guest = ok
valid users = boone, @users
read only = yes
write list = booneThen restart samba.

That may look contradictory to have one user that can write to a read only share but "write list" overrides "read only". So only "boone" and members of the "users" group will gain access but only "boone" will be able to write ( and delete ) to ( from ) it.

---

### Post by boone58 on 2012-12-30
Thank you very much. That wasn't exactly what I wanted, but it was a step in the right direction and now I have a read only guest share writable only by me. This is what I ended up with.

```
[music]
    comment = All Music
        guest ok = yes
    read only = yes
    browsable = yes
        write list = boone
        create mask = 755
        directory mask = 755
    path = /srv/smb/public
```

---

### Post by kevinthecomputerguy on 2012-12-30
The problem i see here is with a diskspace quota, and then eventually multiple writers.

I would make a read-only group, a writeable group, and then set a quota on the mount point.

You could use "force user" for write, and then public yes and no acct needed for read. No acct needed for read means changing share server role

---

