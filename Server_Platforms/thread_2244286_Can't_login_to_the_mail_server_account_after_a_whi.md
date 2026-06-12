---
title: "Can't login to the mail server account after a while"
date: 2014-09-15
forum: Server Platforms
---

### Post by bsrcube on 2014-09-15
Hi all,

I have a mail server system setup with "postfix + dovecot + squirrelmail" on Ubuntu 12.04 LTS. 

The mail server seems to run fine for a couple of hours after its started. Beyond that, I find that none of the users can log in to their accounts. Upon entering the user name and passwords I get the following error (from squirrel mail),

[TABLE="width: 70%"]
[TR]
[TD][TABLE="width: 100%, align: center"]
[TR]
[TD="bgcolor: #dcdcdc, align: center"][COLOR=#cc0000]**ERROR**[/COLOR][/TD]
[/TR]
[TR]
[TD="align: center"]You must be logged in to access this page.[/TD]
[/TR]
[TR]
[TD="bgcolor: #dcdcdc, align: center"][COLOR=#cc0000]**[Go to the login page]("http://mile.ee.iisc.ernet.in/squirrelmail/src/login.php")**[/COLOR][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

If I check the service status for postfix and dovecot,
```

mile@mile$ service postfix status
-su: /sur/sbin/service: input/output error

```

At times the squirrelmail throws the error,
[FONT=arial]Preference file, /var/lib/squirrelmail/data/[/FONT][FONT=arial]user1.pref.tmp, could not be opened.[/FONT]

Also, If I try to use a terminal and login as a superuser,
```
mile@mile$ sudo su -
[sudo]: password for mile:
mile@mile$ sudo: Unable to open /var/lib/sudo/mile/0: Read-only file system

```

I am not sure if the above errors are related or what seems to be the problem. I am increasingly getting a feeling that the installation of the packages or rather the configuration of the packages is not done properly or mucked up somehow. 

After a restart, it seems to work ok for a while only to throw one of the errors again.

Can this be fixed? Has anyone encountered issues like this before?

---

### Post by SeijiSensei on 2014-09-15
```
sudo: Unable to open /var/lib/sudo/mile/0: Read-only file system
```

If the filesystem randomly becomes marked "read-only" some time after rebooting, it's very likely the disk where /var/lib is stored has some physical problems.  You might want to run the tests in the **[smartmontools]("https://help.ubuntu.com/community/Smartmontools")** package.

---

### Post by bsrcube on 2014-10-27
Thanks a ton SeijiSensei.

It was a hardware issue. The HDD was corrupt. Having replaced the HDD, the system is all fine :).

Good Day!

---

