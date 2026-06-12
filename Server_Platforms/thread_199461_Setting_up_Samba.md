---
title: "Setting up Samba"
date: 2006-06-18
forum: Server Platforms
---

### Post by mssever on 2006-06-18
I'm having trouble getting Samba to work properly on Ubuntu 6.06 (I just installed Ubuntu for the first time last night and I've never used Samba before). Here are the symptoms: when I try to browse to my Linux box from WinXP, I get a login box that won't accept my username/password. Also, I can't see the printer attached to the Linux box. I suspect that Samba isn't configured correctly.[LIST=1]
[*]I installed swat; according to the man page, I should be able to point a web browser at localhost:901. No such luck. Swat isn't running. I tried ```
service swat start
``` and got "command not found". I even rebooted to no avail. How to I make swat run? As a corolary, how do you control services in Ubuntu? Neither "service" nor "chkconfig" work.
[*] Is there a better Samba configuration program available?
[*]Or, am I completely barking up the wrong tree?[/LIST]Any help would be much appreciated.

---

### Post by woedend on 2006-06-19
[http://ubuntuforums.org/showthread.php?t=76647](http://ubuntuforums.org/showthread.php?t=76647)

try that thread.
it's fairly simple.  First, you must add the user to your ubuntu box.  lets see you add a user called mrsamba.

then, you must run 
sudo smbpasswd -a mrsamba

it will ask you for the password, make one up here and push enter.  

from the thread, make sure your workgroup names match, and make the other necessary changes.  If you follow that nad still cant get it working, let me know i'll work you through it.

---

### Post by beowulf62381 on 2006-06-19
I found this site helpfull for many things in dapper

it has a helpfull section on samba and samba printing

[http://ubuntuguide.org/wiki/Dapper#Samba_Server]("http://ubuntuguide.org/wiki/Dapper#Samba_Server")

hope it helps

---

### Post by mssever on 2006-06-19
[quote=woedend][http://ubuntuforums.org/showthread.php?t=76647]("http://ubuntuforums.org/showthread.php?t=76647")
try that thread.
it's fairly simple.  First, you must add the user to your ubuntu box.  lets see you add a user called mrsamba.

<snip>[/quote] 
Thanks. It works now. I only wish I knew why the GUI didn't work.

---

### Post by LordHunter317 on 2006-06-19
The service and chkconfig commands are RH specific and don't exist on Ubuntu.  You run the init scripts directly.

---

