---
title: "Ubuntu Server does not reboot or shutdown, no command I have found will work"
date: 2013-09-21
forum: Server Platforms
---

### Post by rmksd on 2013-09-21
I don't know what else to do.. 
I've tried reboot, shutdown, halt, init 5, init 6, and all with different options and nothing has worked.

It just goes to a new line and just pretends I didn't type anything. 
Reboot though, will make the system freeze.

I tried looking at top for any out of control processes and nothing.

---

### Post by Bashing-om on 2013-09-21
rmksd; Hi !

What results from terminal command:
```

sudo shutdown -h now

```

[INDENT][INDENT]should work, else ?

[/INDENT][/INDENT]

---

### Post by rmksd on 2013-09-21
```
ken@kserv:/var/log$ sudo shutdown -h now

Broadcast message from ken@kserv
        (/dev/pts/0) at 20:03 ...

The system is going down for halt NOW!
```

and then new line and acts as though nothing was actually entered.. I'm not sure what log I should be looking in. I've looked in a few. Maybe I don't know what to look for.

---

### Post by Bashing-om on 2013-09-22
rmksd; Humm ..
Sorta makes one wonder what file  is not being updated:
How 'bout looking here for starters ?
[http://manpages.ubuntu.com/manpages/raring/man3/login.3.html](http://manpages.ubuntu.com/manpages/raring/man3/login.3.html)

And to view the log files:
```

last -f /var/log/utmp
last -f /var/log/wtmp
last -f /var/log/wtmp.1

```

[INDENT][INDENT]could be another learning experience
[/INDENT][/INDENT]

---

### Post by rmksd on 2013-09-22
```

ken@kserv:~$ last -f /var/log/wtmp 
ken      pts/2        kion.local       Sat Sep 21 21:46   still logged in   
reboot   system boot  3.8.0-30-generic Sat Sep 21 20:47 - 20:47  (00:00)    
ken      pts/0        kenseven.local   Sat Sep 21 20:38 - crash  (00:08)    
ken      pts/0        kenseven.local   Sat Sep 21 20:36 - 20:38  (00:02)    
reboot   system boot  3.8.0-30-generic Sat Sep 21 20:33 - 20:33  (00:00)    
ken      pts/0        kenseven.local   Sat Sep 21 20:26 - crash  (00:07)    
ken      pts/0        kenseven.local   Sat Sep 21 20:21 - 20:25  (00:04)    
reboot   system boot  3.8.0-30-generic Sat Sep 21 19:52 - 19:52  (00:00)    
ken      pts/0        kenseven.local   Sat Sep 21 19:43 - crash  (00:09)    
reboot   system boot  3.8.0-30-generic Sat Sep 21 19:19 - 19:19  (00:00)    
ken      pts/0        kenseven.local   Sat Sep 21 19:19 - crash  (00:00)    
reboot   system boot  3.8.0-30-generic Sat Sep 21 18:34 - 18:34  (00:00)    
ken      pts/0        kenseven.local   Sat Sep 21 18:26 - crash  (00:08)    
reboot   system boot  3.8.0-30-generic Wed Sep 18 00:12 - 00:12  (00:00)    
ken      pts/0        kenseven.local   Tue Sep 17 23:16 - crash  (00:56)    
ken      tty1                          Tue Sep 17 22:22 - down   (00:09)    
reboot   system boot  3.8.0-30-generic Tue Sep 17 22:22 - 22:32  (00:09)    
ken      tty1                          Tue Sep 17 22:12 - down   (00:09)    
reboot   system boot  3.8.0-30-generic Tue Sep 17 22:12 - 22:21  (00:09)    
ken      tty1                          Tue Sep 17 21:59 - down   (00:04)    
reboot   system boot  3.8.0-30-generic Tue Sep 17 21:59 - 22:04  (00:04)    
reboot   system boot  3.8.0-30-generic Tue Sep 17 21:55 - 21:55  (00:00)    
ken      pts/2        kenseven.local   Tue Sep 17 21:52 - crash  (00:02)    
reboot   system boot  3.8.0-30-generic Tue Sep 17 21:48 - 21:48  (00:00)    
ken      pts/0        kenseven.local   Tue Sep 17 21:46 - crash  (00:02)    
ken      tty1                          Tue Sep 17 21:33 - down   (00:10)    
reboot   system boot  3.8.0-30-generic Tue Sep 17 21:33 - 21:44  (00:11)    
reboot   system boot  3.8.0-30-generic Tue Sep 17 21:28 - 21:28  (00:00)    
reboot   system boot  3.8.0-30-generic Tue Sep 17 21:26 - 21:26  (00:00)    
ken      pts/0        kenseven.local   Tue Sep 17 21:24 - crash  (00:01)    
ken      tty1                          Tue Sep 17 21:16 - down   (00:05)    
reboot   system boot  3.8.0-30-generic Tue Sep 17 21:15 - 21:21  (00:05)    
reboot   system boot  3.8.0-30-generic Tue Sep 17 20:37 - 20:37  (00:00)    
ken      pts/0        kenseven.local   Tue Sep 17 20:37 - crash  (00:00)    
reboot   system boot  3.8.0-30-generic Tue Sep 17 20:20 - 20:20  (00:00)    
ken      pts/3        kenseven.local   Tue Sep 17 20:08 - crash  (00:11)    
ken      pts/1        192.168.0.101    Tue Sep 17 12:22 - 13:04  (00:42)    
ken      tty1                          Mon Sep 16 21:21 - down   (14:54)    
reboot   system boot  3.8.0-30-generic Mon Sep 16 21:21 - 12:15  (14:54)    
```

I haven't the faintest idea what to do next. I keep running into problems with this server. -_-
Might as well move me over to absolute beginner, because that's about right, right now.

---

### Post by Bashing-om on 2013-09-22
rmksd; Well ..
That does not tell us much that was not already known ..
I ran across this:
I will be pleasantly surprised if this does resolve the issue;
[http://www.necopost.com/2011/05/ubuntu-wont-shutdown-logout-or-restart.html](http://www.necopost.com/2011/05/ubuntu-wont-shutdown-logout-or-restart.html)
But, it is worth a try, no more trouble than it is.

[INDENT][INDENT]hey it is a possibility
[/INDENT][/INDENT]

---

### Post by rmksd on 2013-09-22
Unfortunately, that didn't work. I might just have to hose this and reinstall the OS

---

### Post by Bashing-om on 2013-09-22
rmksd; Well.

That is a great thing about 'buntu .. when one keeps backups, (re-)install is a sure fix !
Generally looked on as a means of last resort; However, we learn little in doing so ...
 
The process is intriguing and I am more than happy to work with you to find the solution. As you have seen, there could be many causes and may take some time to find that cause.

[INDENT][INDENT]what we have here is a 'process' failure to communicate
[/INDENT][/INDENT]

---

### Post by rmksd on 2013-09-22
I did a fresh install and it still didn't reboot or shutdown. I'm chalking it up to 13.04. I'm going down to 12.04 and will give it another whirl.

---

### Post by Bashing-om on 2013-09-22
rmksd; Hi ! --WoW !

This should prove interesting ..I have been active trying to come up with a trouble shooting procedure.
Look'n and think'n; this is generally a process not completing and many times that process is related to wireless issues.
Will await results from the 12.04.? kernel.

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by rmksd on 2013-09-22
HA! It always ends up being the simplest solution. I only needed to add "nomodeset" to my grub boot options.. apparently it was being held up by the onboard graphics >.<

---

### Post by Bashing-om on 2013-09-22
rmksd; Outstanding !

2nd leading cause from what I have ran across .. but I, in all honesty, was not prepared for it to be the solution in this case !

Please mark this thread as "solved" aids others seeking a solution and helps keep the forum tidy.

[INDENT][INDENT]who wuudah thunk it
[/INDENT][/INDENT]

---

### Post by rmksd on 2013-09-23
Thanks for your assistance along the way! Marked as solved. :)

---

