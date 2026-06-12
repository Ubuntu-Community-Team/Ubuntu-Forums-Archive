---
title: "ntpd and security risk"
date: 2008-09-02
forum: Security
---

### Post by sulekha on 2008-09-02
Hi,

I have read in a book that unless you have very specific needs(and your own GPS or atomic clock) running ntpd on your machine can be both a waste of resource and security risk. for that reason some sysadmins prefer ntpdate(often in a daily cronjob) to set their system time via NTP

how valid is this claim ?

---

### Post by cdenley on 2008-09-02
> **sulekha said:**
> Hi,

I have read in a book that unless you have very specific needs(and your own GPS or atomic clock) running ntpd on your machine can be both a waste of resource and security risk. for that reason some sysadmins prefer ntpdate(often in a daily cronjob) to set their system time via NTP

how valid is this claim ?

Running any server creates potential for a security risk. I think ntpdate functions as a client which would make it safer. I believe ntpd would listen for network connections, which gives hackers something to attack.

---

### Post by simvin76 on 2008-09-24
Just as cdenley sais, there is always a risk with having a computer connected to the internet.

The difference between ntp-client and ntpd is that ntp-client is run once and then resets the clock to the correct time. ntpd (ntp daemon) runs all the time and speeds up or slows down the computers clock to adjust it to the correct time.

It is not advisable to adjust the clock in to large steps because that can mess up your system. If your clock is moved backwards for exampel dovecot (imap client) kills itself ([http://wiki.dovecot.org/TimeMovedBackwards](http://wiki.dovecot.org/TimeMovedBackwards)).

In '/etc/ntp.conf' you can specify which computers are allowed to use you computer as a timeserver and which computers are allowed to  change the time on your computer.
But if you are running a firewall (shorewall or ufw for example) you should be safe anyway.

---

