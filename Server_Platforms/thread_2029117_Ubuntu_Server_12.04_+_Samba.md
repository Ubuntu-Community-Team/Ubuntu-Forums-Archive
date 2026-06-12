---
title: "Ubuntu Server 12.04 + Samba"
date: 2012-07-19
forum: Server Platforms
---

### Post by wambo on 2012-07-19
Hello!

I have trawled the internet and found multiple threads etc all relating to samba but none which specify exactly what I was after. I'm sure they're out there but I couldn't find them!

I want to be able to configure a samba share so multiple users have access. So far at home I can only allow 1 user access to all the share. This isn't ideal. I'm quite new to Ubuntu so please be sympathetic.

So i want:
User 1 + User 2 to have access to Share1.

User1 has Read/Modify access - User2 has read only.

How do I configure Ubuntu and Samba.

I have added the users in samba. Added them in ubuntu also. Tried to add the unix users to a group and have the owners of the folder as 'me:sharegroup'. This also hasn't worked. I'm either half right and just have a few steps missing or I'm going in the completely wrong direction!!

Help is more than welcome! Thank you!

---

### Post by CharlesA on 2012-07-19
[http://charlesa.net/tutorials/debian/debiansamba.php](http://charlesa.net/tutorials/debian/debiansamba.php)

```
[Charles]
        path = /media/data/charles
        write list = charles
        read list = joe
```

EDIT: Is this supposed to be marked as solved?

---

### Post by wambo on 2012-07-19
> **CharlesA said:**
> [http://charlesa.net/tutorials/debian/debiansamba.php](http://charlesa.net/tutorials/debian/debiansamba.php)

```
[Charles]
        path = /media/data/charles
        write list = charles
        read list = joe
```EDIT: Is this supposed to be marked as solved?

Thanks Charles. I now seem to be stuck where is I am user1 i create a txt file. Then user2 can open it but is unable to make changes to it.

Both users are in the multishare group.
My smb.conf is configured with write list = @multishare

So why can't the user who created it make changes.

Thanks

---

### Post by CharlesA on 2012-07-19
user1 has read/write access, user2 has read only access.

Isn't that what you wanted?

---

### Post by wambo on 2012-07-19
Sorry, Ok lets say user3 starts at the company and now they need write access.

User1 creates a file which user3 can open but cannot modify. Even though they are both in the write list.

Thanks for you time.

---

### Post by CharlesA on 2012-07-19
That has to do with linux permissions. You probably have to force permissions like this:

```
        create mask = 660
        directory mask = 770
```

Add those to the share definition and it should let whoever is in the write group, actually write to the files.

---

### Post by wambo on 2012-07-19
Yea hmm. This is my config for the share.

[multishare]
comment = Multi Share Test Folders
guest ok = no
writable = yes
valid users = @multishare
write list = @multishare_write
read list = @multishare_read
path = /media/multishare
force create mode = 660
force directory mode = 770

---

### Post by wambo on 2012-07-19
What I'm finding is if I go to the security details in windows it only shows my username. It doesn't show the group.

Thats why only the user who creates can see modify the file.

---

### Post by CharlesA on 2012-07-19
Check the permissions of /media/multishare

---

### Post by wambo on 2012-07-20
I used the command sudo chmod g+s

This is now making the created files inherit the top level folders owner group.

---

