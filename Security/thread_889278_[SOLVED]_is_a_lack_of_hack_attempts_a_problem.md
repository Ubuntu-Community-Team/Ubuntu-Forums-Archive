---
title: "[SOLVED] is a lack of hack attempts a problem"
date: 2008-08-13
forum: Security
---

### Post by tamoneya on 2008-08-13
I was just reading this thread: [http://ubuntuforums.org/showthread.php?t=888199](http://ubuntuforums.org/showthread.php?t=888199) and i ran the command listed in post #4 ```
sudo grep sshd /var/log/auth.log | less
```

All i found in there were all of my logins all of the originating from my internal IP address and the IP address of my office (I log in from work fairly often via ssh) so they are definitely not hack attempts.  This however appears out of the ordinary according to the above thread as it appears I should see some dictionary attacks or something every couple of days.  I checked the entire month and didnt find anything out of the ordinary.  

This seems suspicious to me so I was wondering what you guys think about it.  Am I just really lucky to never get targeted or do I have some sort of security hole.

---

### Post by Dr Small on 2008-08-14
You just haven't been hit by the botnets. Don't worry.

---

### Post by CameO73 on 2008-08-14
Give me your IP and I'll fix that for you! ;)

---

### Post by tamoneya on 2008-08-14
> **Dr Small said:**
> You just haven't been hit by the botnets. Don't worry.

So your saying im just lucky or is there a reason why my IP is special and doesnt get targeted.

---

### Post by todb on 2008-08-14
> 
Am I just really lucky to never get targeted or do I have some sort of security hole.

:)

You could look at the touch times on your old logs to see if they've been modified. Of course, if an attacker is being so careful as to excise his own (and others') login attempts, he'll probably just re-touch the files to their original write times.

If you're worried that your logs are being tampered with, store them offline routinely, echo them out to another machine using snmp and then store /those/ logs offline, etc.

But yeah, paranoia will only get you so far.

Here's a quick experiment to see if your logging is working; try a bunch of failed ssh logins to the suspect machine. If you don't see them in the logs, then you have a problem (either with writing or reading your logs)

In fact, with the command given here, /that/ command should match the grep, since the act of sudo'ing will (by default) be logged in auth.log.

---

### Post by tamoneya on 2008-08-14
> **todb said:**
> :)

You could look at the touch times on your old logs to see if they've been modified. Of course, if an attacker is being so careful as to excise his own (and others') login attempts, he'll probably just re-touch the files to their original write times.

If you're worried that your logs are being tampered with, store them offline routinely, echo them out to another machine using snmp and then store /those/ logs offline, etc.

But yeah, paranoia will only get you so far.

Here's a quick experiment to see if your logging is working; try a bunch of failed ssh logins to the suspect machine. If you don't see them in the logs, then you have a problem (either with writing or reading your logs)

In fact, with the command given here, /that/ command should match the grep, since the act of sudo'ing will (by default) be logged in auth.log.

Okay that looks good.  I tried remoting in as root and it was caught in my logs. Thanks

---

### Post by Titan8990 on 2008-08-14
There shouldn't be any need to log in as root on a debian based os.

---

