---
title: "Help with samba sharing linux to windows"
date: 2008-11-25
forum: Server Platforms
---

### Post by seshomaru samma on 2008-11-25
Hi, 
this should be really simple but...
I need to share a folder on linux with windows clients , i want to have free access for anyone and allow anybody to do whatever they want with the files in there , the folder is \media\fatfiles. Here are the permissions:
```
drwxrwxrwx 13 root root 16384 2008-11-25 15:26 fatfiles
```
(does it mater that the owner is root?)
I have samba installed. I have changed the workgroup to our workgroup but havn't touched the samba.conf, except adding:
```
comment = Public Folders
path = /media/fatfiles
public = yes
writable = no
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup
```
do i need to do anything else?
when i go to "my network places" or whatever you call that on windows, i can't see the linux share.

---

### Post by renzokuken on 2008-11-25
did you restart samba after you made the changes?

```
sudo /etc/init.d/samba restart
```

if you know the name of the linux computer you should be able to go (on your windows box) Start > Run and type \\nameofcomputer\ and hit enter.

should bring up a window with available shared folders.

if not try using the ip address of the linux computer instead

---

### Post by Silver Bullet on 2008-11-25
I don't see where you named your share. 

```

[SHARENAME]
comment = Public Folders
path = /media/fatfiles
public = yes
writable = no
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup
```

Replace SHARENAME with the name you want the share to be (leave the brackets) and then restart samba as previously mentioned.

---

### Post by seshomaru samma on 2008-11-25
Thank you
I restarted and named the share and now can see it from Windows
(though the computer appears as "server (Samba, Ubuntu) server" , I named it 'server' , I don't know why Windows would see it that way)
But I now I only get read rights, but cannot write. What did I do wrong?
If this is relevant - the share /media/fatfiles is a FAT32 partition owned by root, permissions in my original post

---

### Post by Silver Bullet on 2008-11-25
Change the line under your share in smb.conf
```
writeable = no
```

to

```
writeable = yes
```

then restart samba again

---

### Post by seshomaru samma on 2008-11-25
of course!

i feel so stupid:shock:



thanks!

---

