---
title: "Weird behavior of smtp..."
date: 2010-03-29
forum: Server Platforms
---

### Post by d.vanheeckeren on 2010-03-29
It seems for some reason that my smtp works fine for a while, then 'temporarily rejects authentication for this account'.  I have to open up a tty and do the following each time, at least once per day:



```
login as: daniel
daniel@atheists's password:
Linux atheists 2.6.31-14-generic-pae #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 i686

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

  System information as of Mon Mar 29 16:37:41 CDT 2010

  System load:  0.08               Swap usage:  0%     Users logged in: 0
  Usage of /:   47.8% of 36.05GB   Temperature: 49 C
  Memory usage: 25%                Processes:   100

  Graph this data and manage this system at https://landscape.canonical.com/

You have mail.
Last login: Mon Mar 29 10:32:44 2010 from 192.168.1.101
daniel@atheists:~$ sudo su root
[sudo] password for daniel:
root@atheists:/home/daniel# /etc/init.d/postfix restart
 * Stopping Postfix Mail Transport Agent postfix                               [ OK ]
 * Starting Postfix Mail Transport Agent postfix                                [ OK ]
root@atheists:/home/daniel# /etc/init.d/dovecot restart
 * Restarting IMAP/POP3 mail server dovecot                                  [ OK ]
root@atheists:/home/daniel#
```Any ideas on why it would work for a while and then suddenly fail?  Where would I start looking for something like that?  I could understand if it was a configuration problem, then it wouldn't work right all the time...but half a day, then quit??  I can't figure this one out.

---

### Post by d.vanheeckeren on 2010-03-30
Update:  I don't have to restart Postfix, only dovecot, so at least it narrows it down for me.  If anyone can help, it would be welcomed.

---

### Post by KB1JWQ on 2010-04-01
What do the mail logs say?

---

