---
title: "OSSEC-HIDS fails to startup"
date: 2009-07-26
forum: Security
---

### Post by HD Chang on 2009-07-26
I know this was addressed in the ossec thread but its quite old and I'm running jaunty w/ossec 2.1.

I tried adding the script that comes with it to rc.d and everythign was fine but upon booting ubuntu hangs right before the login screen loads and then i ps aux | grep ossec and none of the services are running.

It starts fine when i run /etc/init.d/ossec start.  So i removed the script from rc.d and copied the script used in the ossec forum, pretty basic one, and updated my rc.d...  still no go, same result as the default.

I was wondering has anyone else had this problem?  Anybody fixed this issue?
Also, if someone could point me to what log the failed ossec daemon info would be in i would appreciate it.  Ive dug all through var/log and cant find it.

thanks

---

### Post by The Cog on 2009-07-27
The logs go in /var/ossec/logs/ossec.log I think.

Why are you removing the script from /etc/init.d which is its normal place? Althoug my ossec is on Intrepid rather than Jaunty, I have no porblem with ossec starting up. I believe it gets started normally by /etc/rc2.d/S20ossec.

---

### Post by HD Chang on 2009-07-27
I didnt remove the script from /etc/init.d, i only removed it from rc.d:
"sudo update rc.d ossec remove" or something like that because it was hanging up my computer during boot.

I left the original alone.  I found that log and I am about to re-add it to my rc.d.  Gonna see if there is a way to increase verbose first.

---

### Post by ajft on 2009-08-19
> **HD Chang said:**
> I didnt remove the script from /etc/init.d, i only removed it from rc.d:
"sudo update rc.d ossec remove" or something like that because it was hanging up my computer during boot.

I left the original alone.  I found that log and I am about to re-add it to my rc.d.  Gonna see if there is a way to increase verbose first.

Problem seems to be that the OSSEC init script runs before networking (or possibly mail services) are running and available.  On my ubuntu system ossec won't load on reboot, I get the errors in /var/oss/logs/

2009/08/20 09:01:17 ossec-config(1501): ERROR: Invalid SMTP Server: smtp.blahblah.au
2009/08/20 09:01:17 ossec-config(1202): ERROR: Configuration error at '/var/ossec/etc/ossec.conf'. Exiting.
2009/08/20 09:01:17 ossec-maild(1202): ERROR: Configuration error at '/var/ossec/etc/ossec.conf'. Exiting.

Manually running the init script after DNS/networking is available works.

I've moved /etc/rc2.d/20ossec to /etc/rc2.d/80ossec to run it later in the sequence, but haven't performed a test reboot yet.

---

