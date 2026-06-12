---
title: "SAMBA ignores groups in 'valid users' line.  Help!"
date: 2009-01-23
forum: Server Platforms
---

### Post by xerxesv5 on 2009-01-23
Hi

Hope someone has seen this before: Fresh install of 8.04.1 (although I have never gotten this to work, even on earlier releases), I do a very basic setup in smb.conf

If I use this in a share directive:

```
valid users = user1,user2,user3
```

...it works fine, however if I try...

```
valid users = +somegroup
```

(or @somegroup)

...it refuses to allow access. The UNIX users and groups are there, they belong to the appropriate groups, I've added the users with smbpasswd. 

Am I missing something obvious? Help!

-xv5

---

### Post by capscrew on 2009-01-23
Are these AD groups? 
 See: [**http://lists.samba.org/archive/samba/2007-April/131458.html**]("770http://lists.samba.org/archive/samba/2007-April/131458.html")

---

### Post by xerxesv5 on 2009-01-23
Nope, no AD/domains/ldap at all. Just vanilla SAMBA with local UNIX users and groups.

---

### Post by capscrew on 2009-01-23
xerxesv5,

Interesting.  Here is the entry for one of my shares:
```
valid users = +smbusers
force group = smbusers
```

I added the individual users to the group "smbusers" so that all users could manipulate the files.  In my case all the users in the work group are smbusers.  

I used the "force group" command so that all files and directories have the group.

---

### Post by xerxesv5 on 2009-01-23
Hrm, okay I'll give that a go in a second... however as I understand it, '[force group]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#FORCEUSER")' forces a particular group for permissions transactions on files and dirs within a share, no matter what the group of the authenticated user really is. My problem is that users aren't even able to authenticate onto the share in the first place - they just get kicked out unless their username is explicitly placed in the valid users line (or valid users is blank).

---

### Post by capscrew on 2009-01-23
See this explanation: 
[http://www.linuxtopia.org/online_books/network_administration_guides/using_samba_book/ch06_01_00.html]("http://www.linuxtopia.org/online_books/network_administration_guides/using_samba_book/ch06_01_00.html")

I have not tried this way (@account).

Edit:  I'm aware of the use of "force user".  I included it (with an explanation) in the interest of completeness.

---

### Post by xerxesv5 on 2009-01-23
Thanks, but that doesn't seem to work either...

From [http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#INVALIDUSERS]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#INVALIDUSERS") (valid users line is interpreted the same way)

> A name starting with a '@' is interpreted as an NIS netgroup first (if your system supports NIS), and then as a UNIX group if the name was not found in the NIS netgroup database.

A name starting with '+' is interpreted only by looking in the UNIX group database via the NSS getgrnam() interface. A name starting with '&' is interpreted only by looking in the NIS netgroup database (this requires NIS to be working on your system). The characters '+' and '&' may be used at the start of the name in either order so the value +&group means check the UNIX group database, followed by the NIS netgroup database, and the value &+group means check the NIS netgroup database, followed by the UNIX group database (the same as the '@' prefix).

---

### Post by xerxesv5 on 2009-01-23
I'm going to rebuild this from scratch using Debian testing in a VM and see if I have the same breakage.

I have a hack with a python script that finds all the users belonging to a group and fills them in manually, but that's a long way away from @groupname. Oh if only it could be easy like they said on the cover :)

Btw, thanks for the help capscrew, if you (or anyone else) find anything that looks like it could resolve this in the meantime, I'd really appreciate it...

---

### Post by capscrew on 2009-01-23
I have just setup a new test share and accessed it with a group that only has 2 users in it (valid users = testusers). The client is an XP SP2.  I used local logins on the Windows host with the same names as the in the Linux (Samba) host (also added to smbpasswd).  In other words all of the logins match.

The samba +testusers works.  I feel there must be something in your smb.conf that is different than mine.  Will you post the whole smb.conf file for me to look at.

Are you using Webmin or do you config Samba directly on the smb.conf file?

Are the Samba client hosts XP or Vista.  Do you have Samba clients that are Linux?  I successfully use Linux clients to access Samba shares (via Gnome and CLI).

---

