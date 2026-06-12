---
title: "Breezy: mysql-4.1 and php4-mysql"
date: 2006-06-15
forum: Server Platforms
---

### Post by linuxone on 2006-06-15
Hi,

on my servers I still use the Breezy 5.10 release, currently with mysql-server-4.0 and php4-mysql.
For specific reasons I need to update mysql to 4.1, but I must keep php4-mysql and can't update to php5 nor mysqli yet.

Unfortunately the combination of mysql-server-4.1 and php4-mysql does **not** work in Breezy 5.10. PHP complains about an incompatible client version.

Surprisingly the same combination does work into Dapper Drake 6.06: mysql-server-4.1 and php4-mysql (not mysql**i** !) does exist, can be installed together and does work. All PHP apps are running correctly.

How can I run mysql-server-4.1 and php4-mysql (not mysqli) in Breezy 5.10? I can't find a real solution for this old question, neither here in this forum nor anywhere else.
And no, updating to Dapper Drake currently is no solution for me. Too much problems when testing it, things working in 5.10 doesn't run in 6.06 anymore (except mysql/php) so I was forced to go back to 5.10 to get a working server. But that's another issue.

Thanks,
Thomas

---

### Post by irv on 2006-06-17
[QUOTE=linuxone]Hi,

on my servers I still use the Breezy 5.10 release, currently with mysql-server-4.0 and php4-mysql.
For specific reasons I need to update mysql to 4.1, but I must keep php4-mysql and can't update to php5 nor mysqli yet.

[/QUOTE]
I see no one tried to answer you questions here so let me give you my two cents worth. To me it sound like because of the older version of mysql and php not enough testing was done to make 5.10 or 6.06 run well with older version of these two products. Have you tried to turn in a bug report on this problem with either of these Ubuntu version? It sure would be nice if someone could test this out on a spare PC. I picked up an older PC on ebay and use it to test things out like this. It is kind of a hobby with me. Right now I am doing some testing with Fedora so it is not open at the moment. I recommend if the need is great enough you might consider doing the same or maybe someone reading this might reach out a helping hand?
Well, that's my two cents worth! I know it was probley not much help.

---

### Post by linuxone on 2006-06-18
hi,

thanks for your answer. :)

[QUOTE=irv]I see no one tried to answer you questions here so let me give you my two cents worth. To me it sound like because of the older version of mysql and php not enough testing was done to make 5.10 or 6.06 run well with older version of these two products.[/QUOTE]

this issue has certainly nothing to do with a bug. MySQL 4.1 and of course PHP4  are in use on many thousands (or millions?) of servers just in this minute.

BTW, another PHP related problem into Breezy 5.10 is the still missing php4-mysql**i** package. You must use php5 for mysql5.

The combination of php4-mysql (not mysqli) is possible and does work perfectly, as Dapper Drake 6.10 proves. Unfortunately I can't find the necessary trick to recompile the PHP4 deb packages to get a working php4-mysql package for mysql-server-4.1. :( 

Running production servers with specific applications it may happen updates to a newer software release are **not** possible. But mysql-server-4.1 and php4-mysql would be helpfull for further development, so again: how can I get this combination running into Breezy 5.10?

Thomas

---

### Post by damian_ on 2006-08-07
The same thing happens when using php5-mysql .. PHP just doesn't use the 4.1 library files. It reverts back to 4.0.

Have you attempted to copy your mysql.so file from Dapper to Breezy and see if that works?

The file should be located in /usr/lib/php5/<a-number>/mysql.so .. Don't ask me what the number is for, probably a compile version for the module or something.

If this works, please get back to me (and upload the file if possible?).

Also, another possible solution might be to compile php seperately to the rest of it all, and steal the mysql.so from that compile to use with the package.

Neither of these solutions I have tested, as I only have one Ubuntu machine, and it's a 200mhz POS.. I would rather not sit here and wait for PHP to compile to figure this problem out (it takes approx. 1.5hrs for PHP to compile on it :P)

---

### Post by linuxone on 2006-08-08
Hi,

> **damian_ said:**
> Have you attempted to copy your mysql.so file from Dapper to Breezy and see if that works?

no. I doubt this would work because the shared libraries were different. And a production server is no area for such kind of tests. 

Today I got my new notebook, so I'm again able to do some tests. I'll test if it is possible to upgrade a production server from Breezy to Dapper Drake, if all required software and libraries will run into Dapper.

Thanks for help. :)
Thomas

---

