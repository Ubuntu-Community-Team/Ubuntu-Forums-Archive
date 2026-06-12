---
title: "Breezy Badger quits responding after 24 hours"
date: 2006-02-16
forum: Server Platforms
---

### Post by spidermiet on 2006-02-16
My Breezy Badger install dies out every 24 hours or so, i'm running MySQL, PHP 5, and ubbthreads, not sure if that matters, I'm somewhat new to running Ubuntu, and if nay of you folks could direct me as to where to find the logs or what to look for to get this resolved.

---

### Post by Glut on 2006-02-16
Hi,
When you say it stops responding, is it a kernel panic (screen fills with junk, words 'kernel panic' at the bottm) or is it a specific service that stops responding? (such as apache)

Logs can be found in /var/log/
I suggest looking at syslog and kern.log

---

### Post by spidermiet on 2006-02-19
Thanks for the response Glut, I will check the logs,the system does not throw a panic screen that i could tell, then again i do not sit in front of it all day - it just does not give any output back to the screen does not respond to the keyboard, not can i telnet or puTTY into it...

---

### Post by inkpassion on 2006-02-19
[QUOTE=spidermiet]My Breezy Badger install dies out every 24 hours or so, i'm running MySQL, PHP 5, and ubbthreads, not sure if that matters, I'm somewhat new to running Ubuntu, and if nay of you folks could direct me as to where to find the logs or what to look for to get this resolved.[/QUOTE]

You by chance wouldent be running an IBM Box? I had lots of issues with my netvista just locking up for no reason. I did the [following]("http://ubuntuforums.org/showpost.php?p=598297&postcount=21") and its been a dream machine ever since ;)

---

### Post by spidermiet on 2006-02-21
It's a box we slapped together here at work from pieces, i will check the setting out thought, Thank you

---

