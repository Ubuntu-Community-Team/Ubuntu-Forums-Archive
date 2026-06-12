---
title: "user able to delete root files"
date: 2006-05-18
forum: Server Platforms
---

### Post by ashrack on 2006-05-18
a user with the following priviligies:
```
dijaki@zavod:~$ id
uid=1001(dijaki) gid=100(users) skupine=24(cdrom),25(floppy),29(audio),46(plugdev),100(users)

```
is able to remove from NAUTILUS or from TERMINAL the following file:
```
dijaki@zavod:~$ ls -la .xsession
-rwxr-xr-x 1 root root 43 2006-05-18 20:55 .xsession

```
correct me if Im wrong but isnt this file writable only by user ROOT?

ps. I tried doing as root```
chmod -w .xsession
```
and the user DIJAKI was still able to remove it. 
ps2. I even tried restarting linux but its still the same. 
DOESNT THAT GO AGAINST EVERY LINUX POLICY??

using latest DAPPER with all of updates

---

### Post by bluevoodoo1 on 2006-05-18
That's strange. My .xsession file reads...

-rwxr-x--x 1 brian brian 320 May 12 00:31 .xsession

...since I created it, I can write/read/execute it.

---

### Post by ashrack on 2006-05-18
[QUOTE=bluevoodoo1]That's strange. My .xsession file reads...

-rwxr-x--x 1 brian brian 320 May 12 00:31 .xsession

...since I created it, I can write/read/execute it.[/QUOTE]
I purposely chowned it to ROOT so the user using this account wouldnt be able to change it, cos I have some logout scripts in there...

But the user is still able to delete it or change it....

---

### Post by bluevoodoo1 on 2006-05-18
Ok, I see what you mean now.

---

### Post by ashrack on 2006-05-19
[QUOTE=bluevoodoo1]Ok, I see what you mean now.[/QUOTE]
But does anyone know the reason?? This really is a security risk 4M

I've opened a bug report:
[https://launchpad.net/distros/ubuntu/+bug/45541](https://launchpad.net/distros/ubuntu/+bug/45541)

---

### Post by nocturn on 2006-05-19
[QUOTE=ashrack]a user with the following priviligies:
```
dijaki@zavod:~$ id
uid=1001(dijaki) gid=100(users) skupine=24(cdrom),25(floppy),29(audio),46(plugdev),100(users)

```
is able to remove from NAUTILUS or from TERMINAL the following file:
```
dijaki@zavod:~$ ls -la .xsession
-rwxr-xr-x 1 root root 43 2006-05-18 20:55 .xsession

```
correct me if Im wrong but isnt this file writable only by user ROOT?

ps. I tried doing as root```
chmod -w .xsession
```
and the user DIJAKI was still able to remove it. 
ps2. I even tried restarting linux but its still the same. 
DOESNT THAT GO AGAINST EVERY LINUX POLICY??

using latest DAPPER with all of updates[/QUOTE]


This file should be owned by your user ID. 
But even after chowning it, you do have the right to delete it since you are owner of the above directory.  This isn't new nor is it a security leak.

---

### Post by nocturn on 2006-05-19
A little additional information.

If you own a directory, you are able to delete *every* file in it.  This makes sense as any user that can write to it could dump stuff in your directory and you would not be able to clean it out. 

If you make the file root:root 660 (so you have not read access), you will not be able to read or modify the document, just remove it.

If you have read, but not write, you can modify the document and the permissions will be reset to your ID.  This makes sense as the changing can be broken up into read (which you have), delete (which you have) and create a new file (which you also have).

---

### Post by ashrack on 2006-05-19
noctrun
So how could a protect  that file in the users dir so only root would have write/read access to it??

---

### Post by Azrael on 2006-05-20
[quote=ashrack]noctrun
So how could a protect  that file in the users dir so only root would have write/read access to it??[/quote]
By chown'ing the directory and its parent director(y|ies) to root. Otherwise you need to move the file somewhere else.

---

### Post by ashrack on 2006-05-20
[QUOTE=Azrael]By chown'ing the directory and its parent director(y|ies) to root. Otherwise you need to move the file somewhere else.[/QUOTE]
If I CHOWN the directory to ROOT than only root has write access to it. But not the user. And moving the file is out of the question because GNOME access that file on LOGOUT!!! 

Anyother ways

---

### Post by Azrael on 2006-05-21
So what's wrong with a user having control over his own .xsession file?

---

### Post by ashrack on 2006-05-22
[QUOTE=Azrael]So what's wrong with a user having control over his own .xsession file?[/QUOTE]
because in .xsession file theres a script file called which I wrote that at a user log out it recopies his home dir with the one I've set up. So no permanent changes could be made to user's home dir. This is required for the internet kiosk that this machine will be.

---

### Post by nocturn on 2006-05-22
[QUOTE=ashrack]because in .xsession file theres a script file called which I wrote that at a user log out it recopies his home dir with the one I've set up. So no permanent changes could be made to user's home dir. This is required for the internet kiosk that this machine will be.[/QUOTE]

You can make the home directory owned by root, but the group of the user.
Then make .xsession root owned, but readable by the user (rwxr-x---).

You can also make the directory sticky.

---

### Post by ashrack on 2006-05-22
[QUOTE=nocturn]You can make the home directory owned by root, but the group of the user.
Then make .xsession root owned, but readable by the user (rwxr-x---).

You can also make the directory sticky.[/QUOTE]
I used this info which I got from gnome forums:
```
chattr +i .xsession
```
and it works great

---

### Post by nocturn on 2006-05-22
[QUOTE=ashrack]I used this info which I got from gnome forums:
```
chattr +i .xsession
```
and it works great[/QUOTE]

That should work too, it makes the file immutable.   I think this options is not supported on Reiserfs, but ext3 should be fine.

---

### Post by ashrack on 2006-05-22
[QUOTE=nocturn]That should work too, it makes the file immutable.   I think this options is not supported on Reiserfs, but ext3 should be fine.[/QUOTE].U are correct. 4 Reiserfs support U must install some patch into the kernel. Thank god I chose EXT3 for this machine since I use reiserfs on my 2 home machines

---

