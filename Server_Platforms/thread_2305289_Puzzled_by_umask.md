---
title: "Puzzled by umask"
date: 2015-12-04
forum: Server Platforms
---

### Post by Chris_Shelton on 2015-12-04
Hi,

I am setting up a samba file server and I am almost there, apart from permissions on newly created files. I believe this is due to the umask?

Example


My username is chriss, I am part of the default chriss group and also a staff group. Everytime I create a file, I would like others to be able to read/write to it too.

My guess is that I need a umask of 002, but setting it to that in the ~/.bashrc has not taken effect. I also ran the command umask 002 which didn't work either.

 Newly created files have the following permissions:

-rwxr--r-- 1 chriss chriss 75 Dec  4 15:18 hello.txt

I would like something like:  -rwxrwx--- 1 chriss staff 75 Dec  4 15:18 hello.txt    

Any help would be appreciated, thanks.

---

### Post by darkod on 2015-12-04
First, if you want the whole share to be owned by group staff you should include something like:
```
force group = staff
```

to the share definition. In such case it should create all files with group owner staff.

You can control the umask per share too, in its definition. So it should be something like:
```
umask = 002
```

Otherwise just sorting out the group will not help you the whole group to have RW to the files, because they are created as -rwxr--r-- which means the group also has only R.

For these and many more parameters of samba (smb.conf) you can use:
```
man smb.conf
```

That has loads of info and possible parameters, even too many. :) And google can usually help for a more direct info if finding something specific on the man page is difficult.

---

### Post by Chris_Shelton on 2015-12-04
> **darkod said:**
> First, if you want the whole share to be owned by group staff you should include something like:
```
force group = staff
```

to the share definition. In such case it should create all files with group owner staff.

You can control the umask per share too, in its definition. So it should be something like:
```
umask = 002
```

Otherwise just sorting out the group will not help you the whole group to have RW to the files, because they are created as -rwxr--r-- which means the group also has only R.

For these and many more parameters of samba (smb.conf) you can use:
```
man smb.conf
```

That has loads of info and possible parameters, even too many. :) And google can usually help for a more direct info if finding something specific on the man page is difficult.

Thanks for your reply.

The force group command worked great, but the umask = 002 was unsuccessful. When I put the umask line in the definition, it does not colour it in green like the others. Is this a valid command to put in a share definition?

---

### Post by darkod on 2015-12-04
Don't look at the green, look at the permissions. As far as I know, the green mark means -rwxrwxrwx. In other words, RW not only for the user owner and group, but also for the rest of the world (others). According to your post I assumed you want W only for chriss and staff group, not for other users not belonging to staff. If you give W to all, everyone will be able to write new files and modify existing ones.

If you want -rwxrwxrwx the umask would be something like 000.

PS. And for a start you might need to modify permissions on folders and subfolders because up until know files were being created with different umask. So you will have to modify existing files permissions according to your needs.

---

### Post by Chris_Shelton on 2015-12-04
> **darkod said:**
> Don't look at the green, look at the permissions. As far as I know, the green mark means -rwxrwxrwx. In other words, RW not only for the user owner and group, but also for the rest of the world (others). According to your post I assumed you want W only for chriss and staff group, not for other users not belonging to staff. If you give W to all, everyone will be able to write new files and modify existing ones.

If you want -rwxrwxrwx the umask would be something like 000.

Yes I do want rw for owner and staff group, but that command didn't work. Should the command not be create mask = 002?

---

### Post by darkod on 2015-12-04
It might be, I don't know them all from the top of my head. That's why I said better to consult the man page too, to confirm. Sorry if I confused you...

---

### Post by Chris_Shelton on 2015-12-04
> **darkod said:**
> It might be, I don't know them all from the top of my head. That's why I said better to consult the man page too, to confirm. Sorry if I confused you...

No problem, so yes I think it's create mask.

But that seems to create new files with no permissions to anyone. This is so confusing.

---

### Post by darkod on 2015-12-04
The umask of 002 means chmod 775 for folders or 644 for files. The way to calculate is "777 minus the umask". So, umask of 002 means 775. Sorry, I don't know the exact terminology. :)

So, a mask of 002 means 0 for user/owner, 0 for group, and 2 for "anyone". Or in reverse, 775 for folders and 644 for files. So that mask will give you R for "anyone", as we discussed. No W. But that seems to be along the lines of what you want, right?

---

