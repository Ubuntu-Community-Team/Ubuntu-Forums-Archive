---
title: "Need help with Samba auditing"
date: 2008-10-08
forum: Server Platforms
---

### Post by 47_MasoN_47 on 2008-10-08
Alright, we've recently got some very confidential jobs and the files for them are being stored on our file server (Ubuntu Server 8.04.1 x32) via Samba.  I have spent the last 2 hours Googling for how to setup auditing and I found a tool called smbd_audit.  It doesn't really seem to work though, it only logs when someone connects and disconnects, which I don't really care about.

I need to be able to see who opens certain files, and preferably if they made any changes or printed it out.

I also tried the full_audit.so function, but I don't think it's doing anything either.

Has anyone set something like this up before?  I really need some help and need it really fast if possible!

Thanks!

---

### Post by cariboo on 2008-10-08
I think I've found a partial solution to your problem. You need to use vfs stackable modules, extd_audit in particular. This doesn't log who did what to a file on your samba share, but it does show  the following:

```
Log Level Log Details - File and Directory Operations
0                 Make Directory, Remove Directory, Unlink
1                 Open Directory, Rename File, Change Permissions/ACLs
2                 Open & Close File
10                Maximum Debug Level
```

The output from extd_audit is in /var/log/syslog

to enable extd_audit edit /etc/samba/smb.conf change:

```
syslog = 0
to
syslog = 10
```

and add

```
vfs object = extd_audit
```

to the line just below syslog

I tried it on a music directory called incoming and then ran:

```
cat /var/log/syslog | grep incoming
```

This echoed back all the lines in /var/log/syslog that had the word incoming it them. I found the information in:

[www.samba.org/samba/docs/Samba-HOWTO-Collection.pdf](www.samba.org/samba/docs/Samba-HOWTO-Collection.pdf) 

I use the above plus:

[www.samba.org/samba/docs/Samba3-ByExample.pdf](www.samba.org/samba/docs/Samba3-ByExample.pdf)

To help me with most samba problems

I found the info on vfs extd_audit on page 620 of the Samba Howto manual.

Jim

---

