---
title: "SuperUser Rights"
date: 2010-02-04
forum: Security
---

### Post by aleyali on 2010-02-04
[COLOR=black][FONT=Arial][FONT=Verdana]Hi,[/FONT][/FONT][/COLOR]
[COLOR=black][FONT=Arial][FONT=Verdana] [/FONT][/FONT][/COLOR]
[COLOR=black][FONT=Arial][FONT=Verdana]I am new in Linux (Ubuntu 9.10) world; and I plan migrate my network from Microsoft to Linux (Ubuntu); kindly help me in my some queries.
[/FONT][/FONT][/COLOR]
[LIST]
[*][FONT=Arial][FONT=Verdana]How to assign super user OR administrative rights to specific local user, domain administrator and any domain’s group, my domain controller in windows server (Active Directory).
[/FONT][/FONT]
[*][FONT=Arial][FONT=Verdana]I got error when I run my ASP.NET application in Wine environment with MSSQL, my MSSQL on the different Windows server.
[/FONT][/FONT]
[*][FONT=Arial][FONT=Verdana]Previous practice of my user is lock his screen by pressing Ctrl+Alt+Delete; there is any option available of change screen lock keys from Ctrl+Alt+L. to as windows.[/FONT][/FONT]
[/LIST][FONT=Verdana][FONT=Arial]Kindly help me with step-by-step guidance in these queries.[/FONT][/FONT]

---

### Post by niklinux03 on 2010-02-04
Hi,

here is an answer to your question how to assign super user
priviliges to local users.

Look at file /etc/group.
There you should find an entry like
 
admin:x:SOME NUMBER:USERNAME_1

Just add the user name of those local users that
you want to assign super user privileges. 

admin:x:SOMENUMBER:USERNAME_1,USERNAME_2

Don't forget the comma, that is important.
If you are new to linux make sure to backup the
/etc/group file before edditing.

Best

---

### Post by FuturePilot on 2010-02-04
> **niklinux03 said:**
> Hi,

here is an answer to your question how to assign super user
priviliges to local users.

Look at file /etc/group.
There you should find an entry like
 
admin:x:SOME NUMBER:USERNAME_1

Just add the user name of those local users that
you want to assign super user privileges. 

admin:x:SOMENUMBER:USERNAME_1,USERNAME_2

Don't forget the comma, that is important.
If you are new to linux make sure to backup the
/etc/group file before edditing.

Best

Best to use the tools provided than to try and edit it yourself where mistakes can be made.

```
sudo usermod -a -G admin username
```

will give username sudo privileges.

---

### Post by doas777 on 2010-02-04
in terms of superuser, read this first:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

admin works differantly in ubuntu than on most systems, in that you are never an admin persistently, but you have the ability to become admin on a command by command basis. 

you can remap your keys in System -> Prefrences -> Keyboard shortcuts

---

