---
title: "Running TCPDump in the background? or as a service?"
date: 2010-04-01
forum: Security
---

### Post by EJeanmaire on 2010-04-01
I was wondering how one could set up tcpdump to run in the background, dumping all output to a file until I terminate the process.

Here is the dilema... I SSH into the box that will be listening (using tcpdump)...

ssh> sudo tcpdump -i eth0 > dump_file
yadda yadda...

then if I exit my ssh session, tcpdump closes.

If I do a...
ssh> sudo tcpdump -i eth0 > dump_file &
[1] 12938
yadda yadda...

and same deal, once I leave ssh it is gone.  

Any suggestions?

---

### Post by Soul-Sing on 2010-04-01
A program running as root and as a service in the background?
Before even considering this i should apparmor tcpdump.

---

### Post by EJeanmaire on 2010-04-01
> **leoquant said:**
> A program running as root and as a service in the background?
Before even considering this i should apparmor tcpdump.

Yeah sounds nice and risky, does it not ;)

The plan is only to run it for 2 hours or so for a networking test; but I need it to run without me directly logged in.

---

### Post by Soul-Sing on 2010-04-01
ps it would generate very much noise, so gzip the content:
```
.....bla/bla tcpdump.txt gzip tcpdump.txt
```

---

### Post by Soul-Sing on 2010-04-01
ps it would generate very much noise, so gzip the content:
```
.....bla/bla tcpdump.txt gzip tcpdump.txt
```

so: ```
tcpdump -n -i eth0 > tcpdump.txt gzip tcpdump.txt
```

---

### Post by cariboo on 2010-04-01
Try using screen, that way the process will keep running even if you exit the session. I don't use it often enough to remember commands, so check man screen.

---

### Post by The Cog on 2010-04-01
Aside from running tcpdump in screen, another way to do it is to run:
> nohup tcpdump -n -i eth0 > tcpdump.txt &
but then you'll need to use kill or pkill to stop it.

---

### Post by Kinstonian on 2010-04-01
You might want to check out [Daemonlogger](http://www.snort.org/users/roesch/Site/Daemonlogger/Daemonlogger.html).  A cool thing about it is that it has the ability to start logging to another file after a certain time or file size.

---

