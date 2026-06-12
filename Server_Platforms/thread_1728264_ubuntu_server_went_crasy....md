---
title: "ubuntu server went crasy..."
date: 2011-04-13
forum: Server Platforms
---

### Post by alis5 on 2011-04-13
Hello,

I'm pretty new to ubuntu and have set up a ubuntu server that I control through putty.

I'm running mail (zarafa) and samba, a small private homepage for sharing pictures among family. It has worked pretty nice until now.

Suddenly my other computers in the network can't find the server.
I'm using samba to share some maps along 4 computer.

First I got some strange error yesterday when I ran sudo on commands (through putty). I added some line that I don't remeber what it said.  But the sudo/command worked anyway.
When I then today tried to login (through putty) I couldn't get a connection!
I finally gave up and did a "hard reboot" (power on/off). 
After that putty started to work, but now I cant find my shared folders any more.
I can't even find my server when I browse in "microsoft widows network". All other computers are there.

I can ping my server, and zarafa is working and also my webpage.
But if I connect through winSCP I can't get in to one of my to 2 folders that I share through samba. I need top login as sudo su to get in there. 

In my smb.conf it all looks as it should. Right workgroup and everything.

In a log for samba (log.smbd) it complained about cups 
"printing/print_cups.c:103(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused"
After some reading I tried to reinstall cups, but that didn't do the trick either.

When this (the first putty failure) was happening I was "playing under /var/www/ and also changed owership for /var -R to 777 (by mistake), but I have now changed /var/www to 755, (the rest I don't know).

Thank for help, I don't know where to start !?!
How to get my computer visable in windows again, and how to get my folders back up?!?

_**Solved!**_
The fault was that /var/lib/samba and /var/cache/samba/ had the permissions 777, but they needed 755. (found this error by typing testparm -h).

---

### Post by ruffEdgz on 2011-04-13
> **alis5 said:**
> 
_**Solved!**_
The fault was that /var/lib/samba and /var/cache/samba/ had the permissions 777, but they needed 755. (found this error by typing testparm -h).

Glad to hear that you solved the problem. If you can mark this topic as resolved, that would be helpful.

---

