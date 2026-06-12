---
title: "dovecot won't start at all"
date: 2012-04-12
forum: Server Platforms
---

### Post by associates on 2012-04-12
Hi,

I need some help with my dovecot installed on Ubuntu Server 10.04. It was working before but now it's not even starting. Normally, to restart it after a few modifications on its config, one can just execute the following command in the terminal.

```
sudo /etc/init.d/dovecot restart
```

When I run that command, nothing happened. It did not render any errors at all. Then, I double checked it by using the command ps -A | grep dovecot, no result was returned.

I wonder with this kind of sympton, what went wrong and how to get it back on again.

I also run postfix and squirrelmail.

Any help is appreciated. Thank you

---

### Post by raja.genupula on 2012-04-12
```
/etc/init.d/dovecot stop
/etc/init.d/dovecot start
```

try again with this .  

are you getting any error message while doing stopping or starting , let us know .

---

### Post by lisati on 2012-04-12
*Thread moved to **Server Platforms***
If memory serves correctly, dovecot posts error messages in the mail.log file - you might be able to find some information that can aid your troubleshooting efforts there.

---

### Post by associates on 2012-04-12
Thank you guys for your replies.

No, I tried them both before posting and none of it made it respond as if it wasn't installed or something. 

I also checked in the mail.log and found no record whatsoever. very bizarre. The other option I have is remove the whole package of dovecot and re-install but this would usually stuff up my apache which is already working perfectly (well I had the experience before and don't want to go through it again but if there is no other way out, I guess I've just got to do it.

Many thanks

---

### Post by SeijiSensei on 2012-04-12
Does this machine run a firewall?  If so, are TCP connections to port 143 (and port 110 if you must provide POP3) permitted?  I've had the problem of daemons failing to start because the port was blocked by iptables.

---

### Post by associates on 2012-04-13
Thanks for your reply.

I do not recall if I have done anything to the firewall. AFAIK, I tried to leave things as they are by default as I'm still learning my way around the new OS.

Thank you

---

### Post by elico on 2012-04-16
it can be a defected init.d script.
try to edit the /etc/init.d/dovecot 
file to get the sense of it.
if the dovecot service process was executed you should have got some log output.

---

### Post by perspectoff on 2012-04-16
That happened to me from time to time. I had to restart networking and then things worked ok.

sudo /etc/init.d/networking restart

The problem seemed to be with Network Manager, not with dovecot.

Since I dumped Network Manager, I never have the problem any longer.

---

