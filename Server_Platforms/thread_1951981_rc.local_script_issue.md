---
title: "rc.local script issue"
date: 2012-04-03
forum: Server Platforms
---

### Post by pma083 on 2012-04-03
Hi everyone!

I've created a script to load into the rc.local to change the root password, ip configuration and the hostname. 
This script works perfect in Debian but when I moved to Ubuntu the script start being executed but something is executed in the background and doesn't work as expected. 
So is there any posibility to run my script with no other thing running? I added a line intto the rc.local invoking the script.

Thanks in advance!

---

### Post by Doug S on 2012-04-03
This isn't a great suggestion, but would it be good enough to put a mindless sleep at the start of your script?
 
There was a posting awhile back about how to specificly check if something else was done or similar, but I cann't find it now.

---

### Post by pma083 on 2012-04-03
> **Doug S said:**
> This isn't a great suggestion, but would it be good enough to put a mindless sleep at the start of your script?
 
There was a posting awhile back about how to specificly check if something else was done or similar, but I cann't find it now.

I'll search for that, maybe could help me. :)

---

### Post by pma083 on 2012-04-03
This is how it looks.
[http://imageshack.us/photo/my-images/29/ubuntuissue.png/](http://imageshack.us/photo/my-images/29/ubuntuissue.png/)

---

### Post by pma083 on 2012-04-04
> **Doug S said:**
> This isn't a great suggestion, but would it be good enough to put a mindless sleep at the start of your script?
 
There was a posting awhile back about how to specificly check if something else was done or similar, but I cann't find it now.

Hi, I've tried with the sleep, but didn't worked, it like things in background breaks my script.
I'll keep searching.

Thanks again.

---

