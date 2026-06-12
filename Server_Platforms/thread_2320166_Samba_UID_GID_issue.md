---
title: "Samba UID /GID issue"
date: 2016-04-11
forum: Server Platforms
---

### Post by Daniel_Hope on 2016-04-11
Hello All 

First time poster so sorry if i post in the wrong place / its a repeat (I did check couldn't seem to find the answer).

I have two virtual machines using samba 4.1.6 (Come on apt repository). One is setup as a DC and the other is a domain joined file server. Now for typical day to day use this works fine, domain clients can log on and access the file server drives (Mapped through GPO). 

But I have a strange issue where the clients access to the file server will periodically drop out (seemingly random times) and come back again 5 minutes later. I have logging on per machine (Only level 1) and i can see an interesting when looking at the machine log file that says.
[I]
[2016/03/25 12:33:55.602091,  1] ../source3/smbd/sec_ctx.c:85(become_gid)
  WARNING: using gid -1 is a security risk[/I]

I tried googling it and couldn't find any results.

Anybody got any ideas? 

Thanks

---

### Post by slickymaster on 2016-04-11
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by SeijiSensei on 2016-04-11
Show us the contents of smb.conf inside of [noparse]```

```[/noparse] tags.

---

### Post by Daniel_Hope on 2016-04-11
Sure here is the conf file file, not all of the shares but the one in question

```
[global]

       netbios name = fileserver0
       security = ADS
       workgroup = MYREALM
       realm = MYREALM.NET

       log file = /var/log/samba/%m.log
       log level = 1

       socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536

       dedicated keytab file = /etc/krb5.keytab
       kerberos method = secrets and keytab
       winbind refresh tickets = yes

       winbind trusted domains only = no
       winbind use default domain = yes
       winbind enum users  = yes
       winbind enum groups = yes


       vfs objects = acl_xattr
       map acl inherit = yes
       store dos attributes = yes


[Profiles$]
        path = /data/Profiles$
        read only = no
        browseable = yes

[TFS]
        path = /datastore/design
        available = yes
        valid users = "+MYREALM.net\Domain Users"
        read only = no
        browseable = yes
        public = no
        writable = yes
        create mask = 0777
        directory mask = 0777


 
```

---

### Post by SeijiSensei on 2016-04-11
Boy that is an arcane error!  My version of smbd runs as root:root, so uid=gid=0.  I don't know how gid could get decremented to -1.

I think you need to post this on the Samba Bugzilla forum.  I looked, and though I saw [some things that might be related]("https://bugzilla.samba.org/buglist.cgi?bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bug_status=NEEDINFO&field0-0-0=product&field0-0-1=component&field0-0-2=alias&field0-0-3=short_desc&field0-0-4=status_whiteboard&field0-0-5=content&field1-0-0=alias&field1-1-0=short_desc&field1-2-0=status_whiteboard&field1-3-0=content&order=changeddate%20DESC%2Cbug_status%2Cpriority%2Cassigned_to%2Cbug_id&query_based_on=&query_format=advanced&type0-0-0=substring&type0-0-1=substring&type0-0-2=substring&type0-0-3=substring&type0-0-4=substring&type0-0-5=matches&type1-0-0=notsubstring&type1-1-0=notsubstring&type1-2-0=notsubstring&type1-3-0=notmatches&value0-0-0=gid&value0-0-1=gid&value0-0-2=gid&value0-0-3=gid&value0-0-4=gid&value0-0-5=%22gid%22&value1-0-0=1&value1-1-0=1&value1-2-0=1&value1-3-0=%221%22"), no one reported your "gid(-1)" error there.  This could be a real bug that only the Samba developers can fix.

Have you tried increasing the server's verbosity by adding a "log level" directive?  See "[man smb.conf]("https://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html")" for details.

---

### Post by Daniel_Hope on 2016-04-12
Thanks for the reply!

This is a strange one 

I have submit this bug in the suggested forum

The link to the bug report for any future reference is [https://bugzilla.samba.org/show_bug.cgi?id=11828](https://bugzilla.samba.org/show_bug.cgi?id=11828)

Thanks Again
Dan

---

