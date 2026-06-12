---
title: "My root conrtab won't run @reboot"
date: 2015-10-24
forum: Server Platforms
---

### Post by moebob24 on 2015-10-24
I'm setting up my iptables reload command for loading on reboot. I can't seem to get the root crontab to run my command on reboot.

Heres my set up:
I've used ***iptables-save > firewall_rules.v4*** to get a file containing rules to absorb with ***iptables-restore < firewall_rules.v4*** on boot.

I've ***sudo su***'ed into to root user and saved the rule file in ***/root***. I've added the following line to my _root_ crontab with ***crontab -e***.

[HTML]@reboot iptables-restore < ~/firewall_rules.v4[/HTML]

Upon reboot I run the standard ***sudo iptables -L -v*** and find and empty rule table.

Why so?!

---

### Post by SeijiSensei on 2015-10-25
if you want to load the rules at startup, place the command in /etc/rc.local.

You might also need the complete path, /sbin/iptables-restore.  It's possible /sbin is not in the default search path that cron has available to it.  In general, I always use complete paths in crontabs.

---

### Post by steeldriver on 2015-10-25
Where did you actually save the rules to? using ~/ in EITHER a root crontab OR rc.local file seems like a bad idea to me, if anything it will expand to root's home (perhaps you are expecting it to expand to your home?). I'd recommend using an explicit absolute path to the file regardless.

---

### Post by moebob24 on 2015-10-25
> **SeijiSensei said:**
> if you want to load the rules at startup, place the command in /etc/rc.local.

You might also need the complete path, /sbin/iptables-restore.  It's possible /sbin is not in the default search path that cron has available to it.  In general, I always use complete paths in crontabs.

Using rc.local worked.

I used an absolute path to the location is /root where I copied my rule list.

***iptables-restore < /root/firewall_rules.v4***

---

### Post by moebob24 on 2015-10-25
EDIT: Double post due to my crappy internet :(

---

### Post by moebob24 on 2015-10-25
> **steeldriver said:**
> Where did you actually save the rules to? using ~/ in EITHER a root crontab OR rc.local file seems like a bad idea to me, if anything it will expand to root's home (perhaps you are expecting it to expand to your home?). I'd recommend using an explicit absolute path to the file regardless.

I was originally running the ***~/*** in the root conrtab so I would expect it to expand to ***/root***. 

However, I'm running this in ***rc.local*** now with a full path to ***/root***

---

