---
title: "Inconsistent uids and gids using Winbind and Windows 2008 ADS"
date: 2010-04-25
forum: Server Platforms
---

### Post by discore on 2010-04-25
I have almost got all authentication centralized in 1 place for my office's little LAN but the Linux boxes are having one little issue: userids and groupids for every user are set seemingly at random by Winbind.

For example, this is me on server1:

me@server1:~$ id
uid=10004(me) gid=10007(domain users) groups=10000(front office users),10001(unix admins),10006(BUILTIN\users),10007(domain users)

And on server2:

me@server2:~$ id
uid=10002(me) gid=10007(domain users) groups=10000(front office users),10001(unix admins),10003(BUILTIN\users),10007(domain users)

My uid is different and one harmless gid is different. In this specific case there are no significant gid problems, but there are for other users and other groups.

Between the two machines the uids/gids seem pretty random, but at least they are consistently random. I will always be uid 10004 on server1 and I will always be uid 10002 on server2. I'd like to be the same on both, everywhere, for everyone.

Some Googling around seems to point at these 2 smb.conf lines being key players in obtaining consistency:

```
        allow trusted domains = no 
        idmap backend = idmap_rid:<AD short name>=10000-50000
```

I did this and deleted the winbindd_idmap.tdb cache file as suggested by a random person on the internet and all I got were a bunch of new, random uid/gids and a little file permissions mess in the works. If those lines are the key, I am missing something.

So, any ideas? Anyone got Linux boxes using Samba/Winbind to authenticate against an ADS machine with consistent uid/gids?

Here are some relevant configs:

/etc/nsswitch.conf:
```
passwd:         files winbind
group:          files winbind
shadow:         files winbind
```

(parts of) /etc/samba/smb.conf:
```
[global]
   workgroup = WORKGROUP
   realm = REALM

   server string = %h server
   dns proxy = no

   security = ads

   encrypt passwords = true

   passdb backend = tdbsam

   obey pam restrictions = yes

   unix password sync = yes

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

   pam password change = yes

   idmap uid = 10000-20000
   idmap gid = 10000-20000
   template shell = /bin/bash
   template homedir = /home/%D/%U
   winbind use default domain = yes
   # tried with no luck!
   #allow trusted domains = no 
   #idmap backend = idmap_rid:WORKGROUP=10000-20000
```

I can give you any output from "net" or "wbinfo" if needed. In fact, wbinfo looks sort of promising in general for at least manually mapping things.

Help!

---

### Post by discore on 2010-04-27
Nothing? One and only bump from me.

I can't be the only guy authenticating Linux boxes against ADS. Ask around!

---

### Post by Bakyt Niyazov on 2012-04-09
I am having exactly the same problem now in 2012. Were you able to resolve this?

---

### Post by Elfy on 2012-04-09
I'd start a new thread. 

The OP's not been back since they posted this.

Closed old thread.

---

