---
title: "bricked Ubuntu server 20.04 &quot;sudo chmod o= /&quot;?"
date: 2021-04-24
forum: Server Platforms
---

### Post by hinerron on 2021-04-24
Ok, I think I bricked my home Ubuntu 20.04 server while I was playing with modifying permissions by entering "sudo chmod o= /".  I thought to myself, hey if I just type "/" for the directory I want to change permissions to, it should just change it for every directory!  Sounded like a good time saver.  even though it looks to me like I was only modifying the permissions for Others, I somehow completely got locked out.  I can't log in as a super user at all, let alone make any sudo changes.  From a little research it seems like it's time to re-install my Linux OS as a last resort.

Two questions:  First, are there any alternatives?  Second, what did this actually do, if anyone happens to know?  A quick Googling made it seem like a not very common problem.

---

### Post by CharlesA on 2021-04-25
This is going to be a mess to fix and you will probably better off just backing up your data and then reinstalling the OS.

However, if you want to try to fix it and are fine with potentially running into issues with some files later, you can read the links below:
[https://askubuntu.com/questions/958141/fix-permissions-of-server-after-accidental-chmod](https://askubuntu.com/questions/958141/fix-permissions-of-server-after-accidental-chmod)
[https://superuser.com/questions/1252600/fix-permissions-of-server-after-accidental-chmod-debian](https://superuser.com/questions/1252600/fix-permissions-of-server-after-accidental-chmod-debian)
[https://stackoverflow.com/questions/37157020/how-to-fix-permissions-after-chmod-r-777](https://stackoverflow.com/questions/37157020/how-to-fix-permissions-after-chmod-r-777)

There are some files that need to have special permissions, which as ping, so you will need to keep that in mind.

---

### Post by TheFu on 2021-04-25
Well, the good news is that command only touched the contents of 1 directory. 
The bad news is that was the root directory.

The good news is that you learned something. Don't run commands, especially with sudo, that you don't completely understand.
The chmod command removed all permissions for "other".  Most userids in the root directory are "other", since those files and directories are typically setup with root:root owner and group.  

I'd guess you could boot into a try ubuntu flash drive, mount the root directory storage to /mnt/root and run 
**sudo chmod o+rx /mnt/root/**
In theory, that should fix it enough, if not exactly.
On my systems, looks like only the 
```
drwx------   2 root root      16384 May  2  2020 lost+found/
```
needs different permissions.

I think you got lucky.  Why?
[LIST]
[*]You could have included the -R option - chmod -R . That would have been infinitely worse. Restore from backups or fresh install would have been the only options.
[*]You've learned that versioned backups are critical.
[*]You've learned that owner, group, permissions, ACLs, and xattrs are 50% of what a backup needs. The data is only half of what you need in the backups.
[/LIST]

Just be glad you didn't do this before a deadline.

---

