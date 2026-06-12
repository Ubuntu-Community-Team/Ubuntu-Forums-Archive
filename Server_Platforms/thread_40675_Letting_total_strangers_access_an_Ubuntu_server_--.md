---
title: "Letting total strangers access an Ubuntu server -- how (un)secure?"
date: 2005-06-09
forum: Server Platforms
---

### Post by hantms on 2005-06-09
Suppose I have an Ubuntu server with a screen & keybaord that any passer-by can access.  Imagine the same server has sensitive files on it, owned by actual users of the system.

Is it safe to allow a guest access then?  How to set it up to the guest can't read those files?  The guest will not have physical access to the server, just keyboard, mouse, screen.

Han.

---

### Post by hantms on 2005-06-09
[QUOTE=hantms]Suppose I have an Ubuntu server with a screen & keybaord that any passer-by can access.  Imagine the same server has sensitive files on it, owned by actual users of the system.

Is it safe to allow a guest access then?  How to set it up to the guest can't read those files?  The guest will not have physical access to the server, just keyboard, mouse, screen.

Han.[/QUOTE]
 
Note that the user files will get on to the server through Samba. 

I was thinking:

I gave all users the group 'general' so I can set it up so they can see (read) each others files.  Like 640 file access rights on anything they create.  (what UMASK is that by the way and where do I set that?)

Then a user 'guest' (is this a predefined account like in Windows?) would be not part of that group, so could not see those files.

Will this work?  Will this be secure?  

Initially I was thinking a diskless workstation, but setting that up is just too complicated to even consider..   If I even slightly value my time then just buying another box would be way cheaper. And from a security point of view, there's not much difference between X-terminal login and actual server login, correct?

Han.

---

### Post by LordHunter317 on 2005-06-10
> **hantms]Suppose I have an Ubuntu server with a screen & keybaord that any passer-by can access.  Imagine the same server has sensitive files on it, owned by actual users of the system.[/quote]This is an inherently bad idea, generally.

> Is it safe to allow a guest access then?If you do a lot of work to secure it, yes.  

> How to set it up to the guest can't read those files? Very cautious file system permissions on everything.  You may have to secure more than just the data, depending on what the system is running.

> The guest will not have physical access to the server, just keyboard, mouse, screen.That's umm, physical access.  Perhaps not complete, but close enough.

> I gave all users the group 'general' so I can set it up so they can see (read) each others files. Like 640 file access rights on anything they create. (what UMASK is that by the way and where do I set that?)There's a group already for this, and it's called 'users'.  For Samba, you set creation permissions in smb.conf.  For shell accounts, you set the umask in /etc/login.defs and in /etc/profile.

Samba doesn't use a umask in its configuration said:**
> 
path=/home/example
browseable = yes
guest ok = no
create mask = 640
directory mask = 2770
force group = users
```

> Then a user 'guest' (is this a predefined account like in Windows?) would be not part of that group, so could not see those files.The default guest account on UNIX is called 'nobody'.

[quote]And from a security point of view, there's not much difference between X-terminal login and actual server login, correct?An X-terminal login is an actual server login.

Not to be mean, but I'm not sure you should really proceede with this, not at least without doing some serious reading on how to proper secure the software you will be using first.

---

### Post by az on 2005-06-10
You would need some sort of kiosk mode software.

---

### Post by desdinova on 2005-06-10
inherently insecure = from the keyboard - reboot, select recovery mode and read every file on the system... so for a start, you'd need a way of disabling reboot and secruing grub for a start....

oops not your comment azz, the original -

---

### Post by LordHunter317 on 2005-06-10
Both of which are trival to do.

---

### Post by tread on 2005-06-10
You can lock booting into single mode with a password if you use lilo (I think, but you will have to check)

Basically, in the default installation, a reboot into single mode will give anyone root access.

---

### Post by LordHunter317 on 2005-06-10
[QUOTE=tread]Basically, in the default installation, a reboot into single mode will give anyone root access.[/QUOTE]That's a change from Debian then, where you need the root password to get in single or emergency modes.

And GRUB supports locking.

---

### Post by hantms on 2005-06-10
Thanks, VERY useful comments and suggestions there!!!

And you're right, should not run anything important on a box that has random people mess with.

Then again.... When I was in university, everyone and his dog had access to terminals that logged in on a HP UX system.  Apparently they managed to make that 'student-proof' and that's a challenge!! :)   Like people would actually go to the root folder and do a 'rm -r' just to see what would happen and which files had their permissions set to world writable.  (Mostly wiped out their own home folder  :???: )  Then trying 'shutdown' wouldn't work without root permissions.. 

Like someone said before, an X-terminal login IS a server login.. (Later on they actually had X-terminals at uni, not just text based terminals).  They managed to get that secure.

So.. Is Ubuntu radically more unsecure than HP Unix that you can't give people a login?  In the example scenario I said 'random passers by' but for sure things would need to be secure to prevent staff from messing things up as well, right?

And............. On another interesting note: Giving random passers by a login would actually FORCE you to get serious about security.  If you just run a server and think it's 'safe' just because it's sitting under a desk somewhere then the first staffer with a grudge will bring the company down..   

Like you already came up with a suggestion to prevent shutdowns and secure the boot thingy..  I bet that's totally essential for any office server that's not in a locked room (or even when it is in a locked room..) 

Cheers,
Han.

---

### Post by LordHunter317 on 2005-06-10
[QUOTE=hantms]\Then again.... When I was in university, everyone and his dog had access to terminals that logged in on a HP UX system.[/quote]And that's probably all that box did.  So in the event of a compromise, only student's files were at risk.

> So.. Is Ubuntu radically more unsecure than HP Unix that you can't give people a login?No, but two things:[list][*]I'd use a box that has untrusted shell acounts for anything else.  Literally.  And I truly mean that.[*]Ubuntu doesn't necessarily come out of the box in an optimial configuration for multiple shells.  Resource limits aren't set properly, for one thing.  The default umask is probably too permissive (unless it's no longer 0022).  There are other issues.[/list]


> Giving random passers by a login would actually FORCE you to get serious about security.But it doesn't, really.  The security needed on a shell server is totally different from that of a web application server.

---

