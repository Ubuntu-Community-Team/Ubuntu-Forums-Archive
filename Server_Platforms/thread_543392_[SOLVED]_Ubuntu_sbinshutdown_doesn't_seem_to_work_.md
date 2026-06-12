---
title: "[SOLVED] Ubuntu /sbin/shutdown doesn't seem to work with /etc/shutdown.allow"
date: 2007-09-05
forum: Server Platforms
---

### Post by PryGuy on 2007-09-05
Good day everyone! 
One of my clients asked me the other day for a thing: he wants me to make a script that would allow the ordinary users to shutdown the system pressing some combination of keys. I think I have to write a script for that. The problem is that only admins can shutdown system and it is not acceptable for us. I've RTFMed a bit and found out that one can write an /etc/shutdown.allow script with the list of users that can shutdown system and run /sbin/shutdown with -a. It's all good but it doesn't seem to work for me for some reason. Yet, I couldn't find a reference to the -a key in the Feisty 'man shutdown'. Is the shutdown.allow thing supported in Ubuntu?

---

### Post by conjur3r on 2007-09-05
Try looking into the /etc/sudoers file.  You can then define a specific user, set of users, or a group access to specific commands (eg shutdown).  Have a look at its very extensive manual page for alot more information.

For example, to allow the group "myGroup" to shutdown the computer using sudo, add:

%myGroup ALL = /sbin/shutdown

---

### Post by conjur3r on 2007-09-05
Also, I believe you want:

# shutdown -h now

to halt the machine after it has shutdown.

---

### Post by joewilliams on 2007-09-05
I always do
```

shutdown now -hP

```
from  "man shutdown"
```
-h     Requests that the system be either halted or powered  off  after
              it has been brought down, with the choice as to which left up to
              the system.

-P     Requests  that  the  system  be  powered  off  after it has been
              brought down.
```

..got an older motherboard that seems to like this best

-Joe

---

### Post by PryGuy on 2007-09-06
> **conjur3r said:**
> Try looking into the /etc/sudoers file.  You can then define a specific user, set of users, or a group access to specific commands (eg shutdown).  Have a look at its very extensive manual page for alot more information.

For example, to allow the group "myGroup" to shutdown the computer using sudo, add:

%myGroup ALL = /sbin/shutdownbut they can shutdown it now  with sudo. The question is how to allow them do it *without* sudo.

---

### Post by conjur3r on 2007-09-06
Isn't that good enough?  If they have a default sudo access, then that's all they need.  They can assume root privileges to do whatever they need.  A warning bell has gone off here.  On production machines, you have sudo hardended down.

I would definitely question the validity of allowing ordinary users access to completely turn off a server in the first place!  Servers are supposed to be up and running 99.999% of the time.

---

### Post by PryGuy on 2007-09-07
> **conjur3r said:**
> Isn't that good enough?  If they have a default sudo access, then that's all they need.  They can assume root privileges to do whatever they need.  A warning bell has gone off here.  On production machines, you have sudo hardended down.The thing is that if the user gets access to sudo he gets access to *the whole *sustem and can crush it.

> **conjur3r said:**
> I would definitely question the validity of allowing ordinary users access to completely turn off a server in the first place!  Servers are supposed to be up and running 99.999% of the time.This is our customer and that explains it! This server will have a crypted drive... well, it's a long story...

---

### Post by [h2o] on 2007-09-07
> **PryGuy said:**
> The thing is that if the user gets access to sudo he gets access to *the whole *sustem and can crush it.
I am quite sure that you can (as already written in this thread) have sudo give different privileges to different users/groups.
Just because they are allowed to use "sudo" does not mean they are allowed to do "sudo rm -rf /". You can limit them to only "sudo shutdown -h now"

---

### Post by asmoore82 on 2007-09-07
add set-uid to the permissions of the file /sbin/reboot like this ...
```
~$ sudo chmod u+s /sbin/reboot
```

then, any user can run the '/sbin/halt' command to halt the system (/sbin/halt is a shortcut to '/sbin/reboot')
(('/sbin/reboot' is a smart multi-call binary that changes its actions depending on which shortcut called it))

set-uid is in general a bad practice, but is generally accepted for halt/reboot of UNIX systems.

---

### Post by PryGuy on 2007-09-07
You are** the man!** =D>Beer on me, buddy!!! Thanks to those who answered also! :)

---

