---
title: "Potentially Compromised OS"
date: 2009-01-30
forum: Security
---

### Post by nealnaidoo on 2009-01-30
Hello, 
I've been running Ubuntu for a few months now, and mainly use it as my media centre.  A few days ago i noticed that while i was watching a video, the network card and the hard disk had allot of activity.  I expected the hard disk activity given i was watching a video file, but i couldn't understand the network card activity.  When i closed all the applications down and monitored the network activity, i was shocked to find that the box had uploaded 2gb of data in 2hrs via my broadband connection.  I run azureus and VLC and not much else on the box, and recently configured the box to accept remote VNC connections so i can navigate from my notebook without needing a kb and mouse plugged in.  I'm concerned that the thing has been in some way compromised.  It uploads data constantly despite no active applications being run.  Anybody got any idea what may be going on, it's got me baffled. 

-n

---

### Post by deadtom on 2009-01-30
Does your VNC server log everything? I'd check that first. VNC is frighteningly easy to break into.

---

### Post by cdenley on 2009-01-30
Are you sure it wasn't azureus? Is there a firewall or router to prevent people from connecting to VNC from the internet?

If you let an attacker in through VNC, then you can no longer trust your OS, and you should do a full re-install with a different password.

---

### Post by nealnaidoo on 2009-01-30
There is a firewall built into the router i use.  I have only opened specific ports.  If i do a rebuild of the OS, what other mechanism could i use for remote access?  Is there any monitoring tools i can use to check if it indeed has been compromised?

---

### Post by Neural oD on 2009-01-30
yes - could be torrents - also check if your system hasn't automatically downloaded updates or something - shouldn't be 2g though - but that depends

---

### Post by jerome1232 on 2009-01-30
Well out of curiosity what does netstat say the traffic is?

```
sudo netstat -tlanp
```

---

