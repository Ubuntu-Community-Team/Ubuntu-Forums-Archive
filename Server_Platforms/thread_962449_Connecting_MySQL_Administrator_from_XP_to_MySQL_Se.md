---
title: "Connecting MySQL Administrator from XP to MySQL Server on Hardy"
date: 2008-10-29
forum: Server Platforms
---

### Post by townclown on 2008-10-29
Hi,
I have MySQL 5.0.51 running on my Hardy Server, i want to connect mysql administrator to it from my windows XP dev machine.
I can't get past this message: MySQL Error Number 1130: Host '192.168.0.34' is not allowed to connect to this MySQL Server.

How can i enable it to accept connections so that i can admin using the gui. I am a linux noob so not too keen on command prompt commands just yet.

And security is not an issue it is a closed network for testing.

Many thanks,
Dazz

---

### Post by koenn on 2008-10-29
MySQL listens on localhost only, by default. It's a security thing.

look here:
[http://ph.ubuntuforums.com/showthread.php?t=960675](http://ph.ubuntuforums.com/showthread.php?t=960675)

---

### Post by townclown on 2008-10-29
Thank you

---

### Post by townclown on 2008-10-29
Just did it and it works 1st time, thanks a million mate!

---

### Post by koenn on 2008-10-29
no problem.

---

