---
title: "Users at Login"
date: 2013-07-16
forum: Ubuntu Development Version
---

### Post by PJs Ronin on 2013-07-16
My production system is 13.04 on sda5 running Unity.   From this I do a DD into sda6 as a baseline then do an apt-get dist-upgrade to build to 13.10 specs.   I can then test to my hearts content in sda6 as Saucy moves to release.   The only user accounts on the production partition (sda5) are myself and PostgreSQL.   Under 13.04, only my user name appears in the login screen and under the "log out etc" icon on the top panel.   When I want to logout or restart the computer, Ubuntu just does it without asking for passwords.   I'm happy.

After upgrading my sda6 partition to Saucy (and booting into that partition), I now have PostgreSQL listed as a user at login:[INDENT][ATTACH=CONFIG]244807[/ATTACH] [/INDENT]

and also at the 'logout/restart' icon on the top panel:[INDENT][ATTACH=CONFIG]244808[/ATTACH] 

[/INDENT]
 
which also now demands that I provide a password confirmation of action.   Not so happy.

If I check the details under "User and Groups" on both 13.04 and 13.10, the details are exactly the same... as I would expect.    I'm running LightDM on both partitions.

Damned if I can find a reason for the difference with the exception that 13.10 has introduced something new with regards to users.   I don't believe there are any options for excluding a particular user from the login screen... it's an all or nothing switch.

Anyone have any ideas how I can exclude PostgreSQL from the login screen.

---

### Post by jbicha on 2013-07-16
Please file a bug.

```
ubuntu-bug accountsservice
```

If you can include any lines in /etc/passwd that mention postgres that would help too. Thanks!

---

### Post by PJs Ronin on 2013-07-17
Ruh Roh... filing a bug... ok, time for an old dog to learn a new trick.   I will be looking for a treat if I get this right.

---

### Post by PJs Ronin on 2013-07-17
Woot woot... [lpbug]1202054[/lpbug]

I can haz belly rub?

Edit: Is good to learn something new.

---

### Post by mc4man on 2013-07-17
In this forum you can now use [lp[COLOR="#FF0000"]d[/COLOR]bug]bug number only[/lpbug] (remove the red d, only used  so bb code would display
yours - 1202054

[lpbug] 1202054[/lpbug]Users at Login

---

