---
title: "User Authentication, Email Hosting...Is it available in Ubuntu Server?"
date: 2012-04-10
forum: Server Platforms
---

### Post by terrykiwi83 on 2012-04-10
[FONT=Georgia][SIZE=2]I have just acquired myself a half decent spare desktop PC that I intend to set up as a server[/SIZE][/FONT], [FONT=Georgia][SIZE=2]I have heaps of experience with Squid but limited experience with using Ubuntu as a server for anything else.

What I would want from a Ubuntu Server (If its possible?)
[/SIZE][/FONT]
[LIST]
[*][FONT=Georgia][SIZE=2]**User Authentication**, similar to that of a Windows Active Directory setup. I have 5 desktops (All Ubuntu) throughout my house and would like them all to authenticate each user with the server, then load that users desktop..etc.[/SIZE][/FONT]
[*][FONT=Georgia][SIZE=2]**Email Hosting** (Microsoft Exchange Server type of setup). I would also need a program to run on the server that will manage our email accounts. We all use Evolution and would like to have public/private email folders setup etc.[/SIZE][/FONT]
[*][FONT=Georgia][SIZE=2]**Squid Caching Server** - I am able to set this up myself[/SIZE][/FONT]
[*][FONT=Georgia][SIZE=2]**Folder sharing across** the network (Everybody will store there stuff on this server, possibly everyones Documents folder is linked to the server?) [/SIZE][/FONT]
[/LIST]
[FONT=Georgia][SIZE=2]So is the above all possible on a Ubuntu server? do you have any suggestions for software, and maybe tutorials to follow, and finally what version server? 10.04LTS or wait for 12.04 LTS? 
[/SIZE][/FONT]


[FONT=Georgia][SIZE=2]Or should I go with CentOS or Debian?[/SIZE][/FONT]


[FONT=Georgia][SIZE=2]Decisions, Decisions, Decisions :\
[/SIZE][/FONT]

---

### Post by roelforg on 2012-04-11
Linux has the "everything is an app" credo.
And i'm thinking (research each one to see if it might work):
 * LDAP / Samba (samba does more then shares)
 * [https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)
 * Samba for the shares for win and have nfs share the same ones for linux.
 
Done it on 11.10

---

