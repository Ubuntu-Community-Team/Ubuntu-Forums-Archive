---
title: "gvfs-http"
date: 2008-11-22
forum: Security
---

### Post by XanTrax on 2008-11-22
So I saw a lot of disk use on my external hdd, so I decided to do some checks for who or what might be running so much information with it.  I did a netstat to see if anyone was connected to it via samba.  To my surprise, this is what I find:

tcp    58208      0 10.27.2.23:43593        64.62.222.199:80        ESTABLISHED 8374/gvfsd-http 


Which that IP goes to shooshtime.com, a heavily overloaded site of spam, popups, and porn.  Why would gvfs-http be sending/receiving information over port 80 if I don't even have a browser open?  There was no browser open at the time of the netstat command execution.

Anyone have any ideas?

---

### Post by lemming465 on 2008-11-25
Does the gvfsd-http have a parent process (ps -flp PID)?  Knowing who started it would be helpful.  Does it come back after a reboot?  My first guess is a previous web browser session ran into some hostile javascript which started things off, but I could be very wrong.

---

### Post by XanTrax on 2008-12-02
> **lemming465 said:**
> Does the gvfsd-http have a parent process (ps -flp PID)?  Knowing who started it would be helpful.  Does it come back after a reboot?  My first guess is a previous web browser session ran into some hostile javascript which started things off, but I could be very wrong.

That sounds like a possibility.  I made sure I did 

killall firefox

to make sure it wasnt anything browser related.  If I see it happen again I will make sure to run the command and find the owner.  Still wondering why a virtual file system daemon was sending/receiving information from that website even with a browser closed.  Maybe you're right though, something outside of the browser got hung up some where.

---

