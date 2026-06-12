---
title: "disable terminal"
date: 2008-04-10
forum: Security Discussions
---

### Post by BatsotO on 2008-04-10
I'm running internet cafe, and I just tried cclfox for the billing system.
The major flaw of this system is in the client side. The cclcfox run on client desktop which display user's bill and lock the desktop when not log-in is easily bypassed by simply kill it.
Is it possible to disable user from running terminal, or just block process listing? of course other user still have access to run terminal.

---

### Post by Dr Small on 2008-04-10
I would place them in a restricted group (the user's that you don't want to be able to use kill) and chgrp restricted /bin/kill

---

### Post by BatsotO on 2008-04-10
God.. why didn't i think of that. All i can think of is disabling the whole thing. BTW if i remove x from the group other, administrator account wouldn'tl also cannot execute kill?
But this will fix the flaw, thank for the tip .

---

### Post by BatsotO on 2008-04-10
chmod u-x /bin/kill = no luck
chmod 744 /bin/kill = no luck

I can block gnome-terminal, but with virtual console open it's just the same

---

### Post by netlogic on 2008-04-10
> chmod u-x /bin/kill = no luck
chmod 744 /bin/kill = no luck

I can block gnome-terminal, but with virtual console open it's just the same

chmod 700 name.of.the.app
edit your menu to "gksu name.of.the.app"
now, it will prompt you for the password to use it.

---

### Post by BatsotO on 2008-04-11
Already done that, but user user still able to execute kill process. 
The next best thing i can do are blocking access to any terminal applications and disabling virtual consoles.
maybe executing /bin/kill is the same with clicking close button in gui.
Or maybe i need more caffeine and nicotine.

---

### Post by netlogic on 2008-04-11
You weren't cleared about your need.
If you don't want them to run virtual terminals outside the Windows enviornment, modify your inittab.

If you don't want them to use kill function, just don't let them use kill command. Change the permission.  If you don't want them to use the close button on the metacity, you will need to recompile few gnome library. 

/bin/kill is a separate application.

---

### Post by BatsotO on 2008-04-11
The goal is to prevent user from issuing kill command to stop a process, in my case is cclcfox. Changing mode on kill was no luck, I've tried it in two computers, chmod 700 kill but still user can kill process. 
My first approach to this goal is prohibit user to execute gnome-terminal and disable virtual console so they can issue kill command, but Dr small remind me about changing permission kill command that i wasn't able to think of at the first time, but changing permission on /bin/kill has no effect, dunno why.. 

root@bina:/usr/bin# ls -al |grep kill
-rwx------  1 root   root      14536 2007-03-08 04:41 killall
lrwxrwxrwx  1 root   root          5 2007-09-12 03:59 pkill -> pgrep
-rwx------  1 root   root      12592 2007-03-08 04:42 skill
lrwxrwxrwx  1 root   root          5 2007-09-12 03:59 snice -> skill
-rwx------  1 root   root       8556 2006-01-05 12:45 xkill
root@bina:/usr/bin# 
--
root@bina:/bin# ls -al |grep kill
-rwx------  1 root root   12592 2007-03-08 04:42 kill
lrwxrwxrwx  1 root root      16 2007-09-12 03:58 pidof -> ../sbin/killall5
root@bina:/bin#

I dont want to disable close button like the rest of computer users in this world, and feisty no longer have inittab.

---

### Post by myle on 2008-04-11
That sounds weird.
You have to disable top also.

---

### Post by BatsotO on 2008-04-12
I dont have to disable top, my users now cant even access terminal,but many reasonable windows admins here also disable command.exe, so I guess my users wont miss anything. 
But my first thought is disabling ps and top.

---

