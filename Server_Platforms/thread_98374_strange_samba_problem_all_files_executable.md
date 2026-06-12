---
title: "strange samba problem: all files executable"
date: 2005-12-03
forum: Server Platforms
---

### Post by d.h. on 2005-12-03
Hello everybody,

I have replaced my old debian fileserver with a new one and installed ubuntu on it. Samba is already installed and I can access the files from my (ubuntu) client, but there is a big problem: On the client side, every file is executable. I mounted the samba share in /etc/fstab. Here is an example:

dh@server:~/test$ ls -al
total 8
drwxr-xr-x   2 dh users 4096 2005-12-03 11:08 .
drwxr-xr-x  31 dh users 4096 2005-12-03 11:08 ..

dh@client:~/server/test$ ls -al
total 8
drwxr-xr-x  1 dh users 4096 2005-12-03 11:08 .
drwxr-xr-x  1 dh users 4096 2005-12-03 10:54 ..

dh@server:~/test$ echo test > testfile
dh@server:~/test$ ls -al
total 12
drwxr-xr-x   2 dh users 4096 2005-12-03 11:11 .
drwxr-xr-x  31 dh users 4096 2005-12-03 11:10 ..
-rw-r--r--   1 dh users    5 2005-12-03 11:11 testfile

dh@client:~/server/test$ ls -al
total 9
drwxr-xr-x  1 dh users 4096 2005-12-03 11:11 .
drwxr-xr-x  1 dh users 4096 2005-12-03 10:54 ..
-rwxr-xr-x  1 dh users    5 2005-12-03 11:11 testfile


Here you can see pretty good what's happening.
Please notice that I didn't create the file on the client via samba but directly on the server.

How can I change this strange behaviour?

Any healp would be greatly appreciated.
Thanks in advance, dh

---

### Post by LordHunter317 on 2005-12-03
Post the fstab entry.

---

### Post by veehell on 2005-12-03
Hi dude, 
you can specify behavior of the incoming files by "umask" or "acces control files" (by unix side or samba side). 
focus on those:
[B]directory mask
create mask[/B]
* have same syntax as "chmod" "chown" so 700 / 750 / 
those one specified how the files will behave on system(/etc/smb.conf)
SWAT tool (or WEB) have big DOCs...with simply explanation what each line means.

Also some dudes, which have to act as clients (depends on smb.conf settings) run special scripts by crontab which reset the attributes on just uploaded files. (it is only workaround i know ;)

PS: be sure, that you don't cross unix vs samba attibutes because unix will always win...

---

### Post by d.h. on 2005-12-03
[QUOTE=LordHunter317]Post the fstab entry.[/QUOTE]

//192.168.1.1/dh        /home/dh/server        smbfs   user,auto,rw,username=dh,password=secret,uid=dh,gid=users      0 0

Anything wrong with that?

[QUOTE=veehell] 
you can specify behavior of the incoming files by "umask" or "acces control files" (by unix side or samba side). 
focus on those:
[B]directory mask
create mask[/B]
* have same syntax as "chmod" "chown" so 700 / 750 / 
[/QUOTE]

I think you didn't fully understand the problem. With "directory mask" and "create mask" you can specify the rights of a file which is created on the client side (and this works just fine).  But I am not creating the file on the client side. Look at my example. All files within this samba share are marked as executable on the client, but they aren't on the server. This is really strange.


Thanks for your help,
dh

---

### Post by d.h. on 2005-12-05
Nobody in here who can help me out?
Please guys, I could use a little hint. Anyone? :???:

---

