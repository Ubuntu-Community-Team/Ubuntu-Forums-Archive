---
title: "Alerts when Apache LOGS contain certain data"
date: 2010-07-10
forum: Security
---

### Post by mistypotato on 2010-07-10
Does anyone know of any software that can monitor the Apache logs for certain phrases or keywords then send an alert when found?

For example I know an attempt to hack has been made when I see log entries like this....

/admin/
/admin/phpadmin/
/phpadmin/

But by the time I see it, the attempt has long since failed or succeeded.

What I need is a way for my server to alert me WHILE someone is entering these phrases.

I realize there may be a "hit" to performance but my server is not that busy anyway (except for hackers).

Thx

---

### Post by spynappels on 2010-07-10
I'm sure someone has already written a script to do this, but I'd imagine this would be a good way to learn shell scripting.

You'd need to grep the logs for the phrases in question on a continuous basis (maybe using tail -f?), and when these phrases are found it could mail an alert, which could include data from the log itself.

---

### Post by Rubi1200 on 2010-07-10
This might prove helpful for checking your logs:

[http://beginlinux.com/sec_train_m/sec_secure/777-logschecks](http://beginlinux.com/sec_train_m/sec_secure/777-logschecks)

It uses the egrep command.

As spynappels pointed out, either find a script that has already been written or have a go at it yourself.

This might also interest you (from bodhi.zazen's security sticky):

[http://www.debianhelp.co.uk/logwatch1.htm](http://www.debianhelp.co.uk/logwatch1.htm)

---

### Post by anomie on 2010-07-12
[QUOTE=mistypotato]For example I know an attempt to hack has been made when I see log entries like this....

/admin/
/admin/phpadmin/
/phpadmin/[/QUOTE]

If you're getting a lot of attacks directly against phpMyAdmin, you might consider putting another layer of security in place. 

Keeping the /phpmyadmin/ (or whatever) directory behind HTTP digest authentication will 1) put an end to scripted attacks that are searching for low hanging fruit; 2) frustrate / slow down even dedicated attackers. 

That, *plus* regular (e.g. cookie) authentication on phpMyAdmin is a strategy I've employed on various 'net-facing hosts.

---

