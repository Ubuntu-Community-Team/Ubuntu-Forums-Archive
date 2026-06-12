---
title: "ubuntu 18.04 nfs server umask ignored by client"
date: 2020-04-16
forum: Server Platforms
---

### Post by skyscreaper on 2020-04-16
Hi All!!

I've the following setup:
1 ubuntu 18.04 client
1 ubuntu 18.04 server

on the server here is the export
```
/myshare      *(rw,sync,all_squash,anonuid=1001,anongid=1001,no_subtree_check)
```

the user 1001 equals to the user test in my etc/passwd and etc/group
```
test::1001:1001::/home/test:/bin/sh
test::1001:

```
on the server i changed too the umask settings in /etc/pam.d/common-session to the following:
```
session    optional    pam_umask.so    umask=077
```

on the server everything seems working good indeed if from every user on the server i type umask this is the result
0077 
this is ok.

now on the client i mount my nfs share with the following:
```
sudo mount -t nfs -o "rw,vers=3" server:/myshare /mnt/myshare
```

here is the problem
whatever file i create under the /mnt/share folder is created like the following
```
-rw-rw-r-- 1 1001 1001    0 Apr 16 09:56 file
drwxrwxr-x 2 1001 1001 4096 Apr 16 10:08 test
```



the anonuid and anongid are respected... but the permissions are wrong... indeed the umask for the client user is 0022.

i was expecting to see something like

```
-rw------- 1 1001 1001    0 Apr 16 09:56 file
drwxr----- 2 1001 1001 4096 Apr 16 10:08 test
```


what am i doing wrong here? how do i enforce the permissions to be umask 0077?

i did another test : sudo systemctl edit nfs-server.service.
I added the following override:
```
[Service]
UMask=0077
```

Still not working... the files always get created with permissions coming from client user umask. (0022)

---

### Post by TheFu on 2020-04-16
Change the umask on the client.  Let me test it.  Yep. That works as expected.  NFS isn't like Samba.  The server isn't all-powerful, overruling the client settings.  
Proof:
```
# On the Server
tf@istar:/tmp$ cd /D/M
tf@istar:/D/M$ cd Foo
tf@istar:/D/M/Foo$ ll
total 68
drwxrwsr-x    2 tf tf    4096 Apr 16 07:50 ./
drwxrwsr-x 1309 tf plex 61440 Apr 16 07:51 ../
tf@istar:/D/M/Foo$ umask
**0077**
tf@istar:/D/M/Foo$ touch server
tf@istar:/D/M/Foo$ ll
total 68
drwxrwsr-x    2 tf tf    4096 Apr 16 07:51 ./
drwxrwsr-x 1309 tf plex 61440 Apr 16 07:51 ../
-rw-------    1 tf tf       0 Apr 16 07:51 server
# On the Client
tf@posc:/home/tf$ cd /D/M/Foo
tf@posc:/D/M/Foo$ ll
total 68
drwxrwsr-x    2 tf tf       4096 Apr 16 07:51 ./
drwxrwsr-x 1309 tf lightdm 61440 Apr 16 07:51 ../
-rw-------    1 tf tf          0 Apr 16 07:51 server
tf@posc:/D/M/Foo$ umask
**0002**
tf@posc:/D/M/Foo$ touch client
tf@posc:/D/M/Foo$ ll
total 68
drwxrwsr-x    2 tf tf       4096 Apr 16 07:51 ./
drwxrwsr-x 1309 tf lightdm 61440 Apr 16 07:51 ../
-rw-rw-r--    1 tf tf          0 Apr 16 07:51 client
-rw-------    1 tf tf          0 Apr 16 07:51 server
tf@posc:/D/M/Foo$ **umask 077**
tf@posc:/D/M/Foo$ touch client2
tf@posc:/D/M/Foo$ ll
total 68
drwxrwsr-x    2 tf tf       4096 Apr 16 07:54 ./
drwxrwsr-x 1309 tf lightdm 61440 Apr 16 07:51 ../
-rw-rw-r--    1 tf tf          0 Apr 16 07:51 client
-rw-------    1 tf tf          0 Apr 16 07:54 client2
-rw-------    1 tf tf          0 Apr 16 07:51 server
```
Note how the gid doesn't match between the client and server?  Unimportant.

in short, working as designed, to the best of my knowledge.  Did i miss something?  

You could use the setgid bit, perhaps, to force fewer group perms.  Usually that is used to force group write access. Hummmm.  Nope, that doesn't work assuming the directory owner is the file owner for any newly made files.

---

### Post by slickymaster on 2020-04-16
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2020-04-16
Changed the directory to drwx-----T and tried again.  That doesn't work either.  Looks like making the userid on the client have 077 umask is the only solution that doesn't involve running a script every 10 minutes.

Not sure it was clear above, but the permissions on the directory there the files are created are VERY important. Newly create objects can be influenced by the parent object's setup, at least for group membership.  in the default ubuntu world, every userid also gets a dedicated groupid just for that user, so 077 and 007 umask is effectively the same.  in my example above, the parent dir has the setgid bit set, so when i made the directory on the server-side, the group was forced to be "plex".  My uid is a member of the plex group ,but only on the server.  On the client side, that gid is for lightdm, which my userid is NOT a member, so the g+s permission couldn't force the plex group from the client side.

Clear as mud?  Basically, Unix permissisons are honored by the clients and servers equally w/ NFS.

---

### Post by skyscreaper on 2020-04-16
I see so what if a user on the client side does something like this?

umask 0777

than i create a file/dir inside the share 
mkdir testfolder

the result is :
d--------- 2 1001 1001 4096 Apr 16 14:27 test

On the server side if i try to access the directory i get permission denied...

i understand that this is by design... but on the server I'll have to fix the permissions i guess...

what about this:

> [COLOR=#000000]i did another test : sudo systemctl edit nfs-server.service.[/COLOR]
[COLOR=#000000]I added the following override:[/COLOR]
[COLOR=#000000][Service] [/COLOR]
[COLOR=#000000][FONT=&amp]UMask=0077
[/FONT][/COLOR]
neither this is working.

---

### Post by TheFu on 2020-04-16
Stupid users have always existed.   if they break the permissions of the files they own, too bad.  Only the owner can change permissions.  The Unix Philosophy demands that users have this control.

Most users have never heard of umask, so as long as the default is reasonable for system usually in /etc/profile, then the problem above is highly unlikely.  Certainly, the user will learn a lesson.  if they are the system admin, then they will learn a more important lesson.

---

