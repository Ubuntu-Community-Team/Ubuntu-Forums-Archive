---
title: "[SOLVED] autofs possible permisions problem... help please"
date: 2015-01-04
forum: Server Platforms
---

### Post by jakub16 on 2015-01-04
Greetings everyone,

I am trying to make a OpenLDAP, autofs, nfs solution. It is giving me kinda hard times. Mounting is functional, i can mount using mount -t nfs my exports, fstab working too. Now with autofs I cannot go to my shared directory, it says

"This location could not be displayed"
"server -name of my folder" could not be found. Perhaps it has recently been deleted.

I can see ther folder "server" in "/mnt/nfs" directory but its contents are unreadable.

auto.master
```
#+auto.master
/mnt/nfs    /etc/auto.network uid=1000,gid=1000 --timeout=6000 --ghost
```

auto.network
```
server -fstype=nfs,rw,soft,tcp,nolock,gid=1000,uid=1000 *myserverip*/media/server
```

From what I have read, there could be problem with permisions? I tried to change those via chown, chmod but it didnt help me... I am not sure what could be done to get it working at this point. Everytime I restart autofs service, owner of "server" switches to root... -.-

---

### Post by Toz on 2015-01-04
From your auto.network file, there appears to be a typo:
> ... myserverip/media/server
...should read:
```
... myserverip:/media/server
```
...note the colon.

To troubleshoot the autofs service, first stop it:
```
sudo service autofs stop
```
...and run the automounter manually:
```
sudo automount -v -f
```
...and look for any error messages.

---

### Post by TheFu on 2015-01-04
I've never specified userids or groupids in the autofs config files. That sorta defeats the purpose for using NFS, right?

auto.master:
> /export/home       /etc/auto.homes
then auto.homes
> /export/home -fstype=nfs,soft,intr,rw,async,vers=3        server:/export/home

There are lots-o-options and I'm being lazy using NFSv3.  There is a way to specifically mount each userid's home, if you need that, but I don't do it that way. They also show where the storage is mounted with a bind-mount.  I've never used that either. Seems like it could be useful in certain situations. I dunno.

---

### Post by jakub16 on 2015-01-06
oh guys, I love you... for real. I am not sure what made the difference though, I have tried with "server:/path" before, and it didnt work out. Same with userids and groupids, maybe specifying nfs version with vers=3 did the trick, but now its working like a charm. Thank you so much. I may be ask for help later when Ill be battling with OpenLDAP, but for now, thank you so much.

---

### Post by TheFu on 2015-01-06
Please mark the thread as solved.

---

