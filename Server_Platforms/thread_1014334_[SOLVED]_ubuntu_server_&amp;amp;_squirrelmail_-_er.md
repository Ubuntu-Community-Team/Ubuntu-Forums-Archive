---
title: "[SOLVED] ubuntu server &amp;amp; squirrelmail - error 'Could not move/copy file. File not att"
date: 2008-12-17
forum: Server Platforms
---

### Post by nicolasdiogo on 2008-12-17
hi folks,

i have installed squirrelmail and apache2 as per instructions found here.

[https://help.ubuntu.com/community/Squirrelmail](https://help.ubuntu.com/community/Squirrelmail)

everything works fine, besides sending messages with attachments.
at the point, when i choose a document and try to attach it to the message i get the message:

'Could not move/copy file. File not attached '

i have already changed the permissions of the folder to 730 and 777.  and also changed the folder to /tmp.

but nothing has solved the problem.

does anyone have any idea how this problem could be solved?

thanks a lot,


Nicolas

---

### Post by albinootje on 2008-12-17
> **nicolasdiogo said:**
> hi folks,

i have installed squirrelmail and apache2 as per instructions found here.

[https://help.ubuntu.com/community/Squirrelmail](https://help.ubuntu.com/community/Squirrelmail)

everything works fine, besides sending messages with attachments.
at the point, when i choose a document and try to attach it to the message i get the message:

'Could not move/copy file. File not attached '


Here are the relevant permissions on a mailserver which i maintain :

# ls -la /var/spool/squirrelmail/
total 16
drwxr-xr-x 4 root     root     4096 May 14  2008 .
drwxr-xr-x 8 root     root     4096 Oct 28 05:11 ..
drwx-wx--- 2 root     www-data 4096 Dec 17 23:28 attach
drwxr-x--- 2 www-data www-data 4096 Jun 25  2007 pref

---

### Post by nicolasdiogo on 2008-12-21
thanks albinootje,

i have the exact same permissions on my folders, see below:
/var/spool/squirrelmail# ls -la
total 12
drwx-wx--- 3 root root     4096 2008-12-11 22:47 .
drwxr-xr-x 4 root root     4096 2008-12-11 22:47 ..
drwx-wx--- 2 root www-data 4096 2008-12-16 06:55 attach

so i will be looking at the PHP configuration to see if there is something that i should amend.

any idea of what i might need to look next?


thanks a lot,

Nicolas

---

### Post by MJN on 2008-12-21
> **nicolasdiogo said:**
> /var/spool/squirrelmail# ls -la
total 12
drwx-wx--- 3 root root     4096 2008-12-11 22:47 .
drwxr-xr-x 4 root root     4096 2008-12-11 22:47 ..
drwx-wx--- 2 root www-data 4096 2008-12-16 06:55 attachI would've thought Squirrelmail (or rather Apache) requires read access to the attachment directory.

Fix this with **sudo chmod g+r /var/spool/squirrelmail/attach** or, better still, make /var/spool/squirrelmail owner:group www-data:www-data with **sudo chown www-data:www-data: /var/spool/squirrelmail/attach**.

Repeat for /var/spool/squirrelmail/prefs if not already done so.

That said, if Albinootje's is working...

Mathew

P.S. What are your $data_dir and $attachment_dir set to in <squirrelmail root>/config/config.php?
P.P.S. What are the permissions of /var/spool/squirrelmail ?

---

### Post by nicolasdiogo on 2008-12-22
hi MJN,

i have used the same directories as those given by the web documentation:
[https://help.ubuntu.com/community/Squirrelmail](https://help.ubuntu.com/community/Squirrelmail)


so i am using:
Data Directory = /var/lib/squirrelmail/data/ 
Attachment Directory = /var/spool/squirrelmail/attach/

but i should follow your advice when i get home later.

thanks,

Nicolas

---

### Post by nicolasdiogo on 2008-12-23
MJN,

i have tried your suggestions and i did not work.
when i can back later i will purge squirrelmail and restart all over again.

thanks

---

### Post by MJN on 2008-12-23
What about the P.S. questions?

Mathew

---

### Post by spiderbatdad on 2008-12-24
```
sudo chmod 733 /var/spool/squirrel/attach/
```

also I think it should be owned by www-data, but it is the final permission set that is stopping it from working.

```
 sudo chown www-data:www-data /var/spool/squirrelmail/attach/ 
```

---

### Post by nicolasdiogo on 2008-12-28
thanks guys,

i have changed my permissions from:

# ls -la /var/spool/squirrelmail/
total 16
drwxr-xr-x 4 root root 4096 May 14 2008 .
drwxr-xr-x 8 root root 4096 Oct 28 05:11 ..
drwx-wx--- 2 root www-data 4096 Dec 17 23:28 attach
drwxr-x--- 2 www-data www-data 4096 Jun 25 2007 pref

to:

# ls -la /var/spool/squirrelmail/
total 16
drwxr-xr-x 4 www-data www-data 4096 May 14 2008 .
drwxr-xr-x 8 www-data www-data 4096 Oct 28 05:11 ..
drwx-wx--- 2 www-data www-data 4096 Dec 17 23:28 attach
drwxr-x--- 2 www-data www-data 4096 Jun 25 2007 pref

and i believe it has been solved.

many thanks for the suggestions.


Nicolas

---

