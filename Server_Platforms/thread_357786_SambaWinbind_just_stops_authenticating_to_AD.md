---
title: "Samba/Winbind just stops authenticating to AD"
date: 2007-02-10
forum: Server Platforms
---

### Post by GrammatonCleric on 2007-02-10
I have a Dell 2950 server with Ubuntu 6.06 server installed on it.  Everything is running fine with the exception of Samba/Winbind interacting with a Windows Active Directory in the mixed mode.  The server in question has been joined to the AD and works...for a time.  Eventually, not sure why, the server just stops authenticating against the AD.  If I restart the server's winbind service AD authentication returns.   I can't seem to find anything in the logs that points to the issue .  Any ideas as to what is causing the server to stop authenticating would be most welcome! 


-GC

---

### Post by elst on 2007-02-10
Read up a bit on the Kerberos client utilities (kinit etc.), and the next time that it stops working try some diagnostics with those. It may also be worth checking:

a) Process activity (with top).
b) The Windows server (Event Viewer etc.)

Since this is tricky to troubleshoot, try asking on IRC and you may be able to find someone that can work through the issue with you.

---

### Post by tstrowd on 2007-02-11
So you have Ubuntu clients authenicating to active directory? If so how did you do that in the first place. I have been trying to do that for a while but never got any answers.

---

### Post by localzuk on 2007-02-11
It is in the wiki - Search for ActiveDirectory on wiki.ubuntu.com

---

### Post by GrammatonCleric on 2007-02-12
> **tstrowd said:**
> So you have Ubuntu clients authenicating to active directory? If so how did you do that in the first place. I have been trying to do that for a while but never got any answers.

I actually followed the following post....

[http://www.ubuntuforums.org/archive/index.php/t-91510.html](http://www.ubuntuforums.org/archive/index.php/t-91510.html)

...and tweaking it for my AD.  Also for each share in your smb.conf the way you add the user groups is as follows....

```
[FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]
[public][/FONT][/SIZE][/FONT]
  [FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]    comment = Public Share[/FONT][/SIZE][/FONT]
  [FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]    path = /home/DOMAIN/Public[/FONT][/SIZE][/FONT]
  [FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]    valid users = @"DOMAIN+Domain Admins", @"DOMAIN+U_GROUP_FOO"[/FONT][/SIZE][/FONT]
  [FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]    admin users = [/FONT][/SIZE][/FONT][FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]@"DOMAIN+Domain Admins", @"DOMAIN+U_GROUP_FOO"[/FONT][/SIZE][/FONT]
[FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]        create mask = 0700[/FONT][/SIZE][/FONT]
     [FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]inherit acls = yes[/FONT][/SIZE][/FONT]
   [FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]    inherit permissions = yes[/FONT][/SIZE][/FONT]
[FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]         create mask = 0700[/FONT][/SIZE][/FONT]
  [FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]    directory mask = 0700[/FONT][/SIZE][/FONT]
  [FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]    writeable = yes
[/FONT][/SIZE][/FONT]
```[FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]

or another way to specify the user groups per share is....
[/FONT][/SIZE][/FONT][FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]
[/FONT][/SIZE][/FONT][FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]
[/FONT][/SIZE][/FONT]```

[FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot][public][/FONT][/SIZE][/FONT]
  [FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]    comment = Public Share[/FONT][/SIZE][/FONT]
  [FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]    path = [/FONT][/SIZE][/FONT][FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]/home/DOMAIN/Public[/FONT][/SIZE][/FONT]
  [FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]    admin users = @"Domain Admins"[/FONT][/SIZE][/FONT]
  [FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]    valid users = @"Domain Users"[/FONT][/SIZE][/FONT]
  [FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]    create mask = 0700[/FONT][/SIZE][/FONT]
  [FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]    directory mask = 0700[/FONT][/SIZE][/FONT]
  [FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]    inherit acls = yes[/FONT][/SIZE][/FONT]
  [FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]    inherit permissions = yes[/FONT][/SIZE][/FONT]
  [FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]    writable = yes[/FONT][/SIZE][/FONT]

```[FONT=Bitstream Vera Sans][SIZE=2][FONT=&quot]
[/FONT][/SIZE][/FONT]
-GC

---

