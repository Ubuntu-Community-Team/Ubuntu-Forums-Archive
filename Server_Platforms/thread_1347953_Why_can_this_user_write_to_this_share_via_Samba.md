---
title: "Why can this user write to this share via Samba?"
date: 2009-12-06
forum: Server Platforms
---

### Post by Roasted on 2009-12-06
I have a user I created who is able to write to a directory and I'm not quite sure why. He can only write to this directory through Samba. Locally on the computer he can't even enter "storage" because he's not a member of the group "samba" and I don't have any permissions allowed for "others." See below:

```
jason@Area51:/media$ ls -l
drwxr-x--- 47 jason samba 4096 2009-12-06 17:55 storage
```

750 permissions - no access by "others"



```
jason@Area51:/media/storage$ ls -l
drwxrws---  2 jason samba  4096 2009-12-06 18:11 myshare
```

myshare is listed as 770 permissions, again no access by "others"

```
jason@Area51:/media/storage$ groups fred
fred
```

As you can see, Fred is -not- a member of Samba.

Fred cannot write to the drive locally.
Fred can write to the drive via Samba.







Hmm - I just fired up Webmin and I see here in the shares section this line.

myshare 	/media/storage/myshare 	Read/write to all known users

So even if the users don't have access to write to the drives locally, they can have access granted to them via Samba? I thought RWX permissions had to be in place before Samba could even allow users to read/write to the corresponding shares.

Can anybody elaborate on this at all?

EDIT - Does it matter that I don't have the valid users tag in the myshare section? See below. I have 3 shares. One that has a valid group, one with valid users, and the myshare one with no valid section. What gives?

```
[Backup Data]
        comment = Backup Data
        writeable = yes
        valid users = jason,user
        path = /media/storage/backup_data
;       browseable = yes

[Public]
        comment = Public
        writeable = yes
        valid users = @samba
        path = /media/storage/public
;       browseable = yes

[myshare]
        comment = myshare
        valid users = fred
        writeable = yes
        path = /media/storage/myshare
;       browseable = yes

```



EDIT - It seems as if it just took some time for the permissions to kick in until this user became restricted accordingly. Does anybody know how much time it takes for permissions to trickle down like this?

Also - One thing I can't understand is this... I re-set up a bogus share like I did above (this is a completely separate scenario). The share had 775 permissions, owned by jason:samba. Fred was the bogus user I used again in this situation, but he was NOT a member of Samba. Even still, Fred could not even view the share - yet there were R-X permissions (5) on it for "other" users. And yes, the smb.conf had him listed as a valid user.

Why is it Fred couldn't access anything at all even with read and execute permissions? Once I added him to Samba, he could access everything fine - but he was also in the group now. When Fred was an "other" where he would take on the "5" permissions from 775 on the share, he couldn't get ANY access.

What gives? Am I going about this wrong? Should I be utilizing Webmin a bit more to act like an Access Control List instead of messing around with Linux's UGO (User/Group/Other) permissions?

Just looking for some insight on these questions I have. Thanks guys.

---

