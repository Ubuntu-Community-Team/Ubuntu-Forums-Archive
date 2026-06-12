---
title: "Ubuntu firewall not blocking attacks to postfix"
date: 2015-05-25
forum: Security
---

### Post by rhandy2 on 2015-05-25
Hello

I have same guy trying to login on postfix.
> 
May 25 09:50:18 example.com postfix/smtpd[5751]: connect from 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]
May 25 09:50:21 example.com postfix/smtpd[5751]: warning: 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]: SASL LOGIN authentication failed: authentication failure
May 25 09:50:21 example.com postfix/smtpd[5751]: lost connection after AUTH from 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]
May 25 09:50:21 example.com postfix/smtpd[5751]: disconnect from 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]
May 25 09:53:33 example.com postfix/smtpd[5850]: connect from 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]
May 25 09:53:35 example.com postfix/smtpd[5850]: warning: 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]: SASL LOGIN authentication failed: authentication failure
May 25 09:53:35 example.com postfix/smtpd[5850]: lost connection after AUTH from 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]
May 25 09:53:35 example.com postfix/smtpd[5850]: disconnect from 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]
May 25 09:56:48 example.com postfix/smtpd[6053]: connect from 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]
May 25 09:56:50 example.com postfix/smtpd[6053]: warning: 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]: SASL LOGIN authentication failed: authentication failure
May 25 09:56:50 example.com postfix/smtpd[6053]: lost connection after AUTH from 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]
May 25 09:56:50 example.com postfix/smtpd[6053]: disconnect from 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]
May 25 10:00:03 example.com postfix/smtpd[6177]: connect from 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]
May 25 10:00:05 example.com postfix/smtpd[6177]: warning: 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]: SASL LOGIN authentication failed: authentication failure
May 25 10:00:05 example.com postfix/smtpd[6177]: lost connection after AUTH from 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]
May 25 10:00:05 example.com postfix/smtpd[6177]: disconnect from 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]
May 25 10:00:18 example.com postfix/anvil[5753]: statistics: max connection rate 1/60s for (smtp:195.154.117.65) at May 25 09:50:18
May 25 10:00:18 example.com postfix/anvil[5753]: statistics: max connection count 1 for (smtp:195.154.117.65) at May 25 09:50:18
May 25 10:00:18 example.com postfix/anvil[5753]: statistics: max cache size 1 at May 25 09:50:18
May 25 10:19:33 example.com postfix/smtpd[2410]: connect from 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]
May 25 10:19:35 example.com postfix/smtpd[2410]: warning: 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]: SASL LOGIN authentication failed: authentication failure
May 25 10:19:35 example.com postfix/smtpd[2410]: lost connection after AUTH from 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]
May 25 10:19:35 example.com postfix/smtpd[2410]: disconnect from 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]
May 25 10:22:47 example.com postfix/smtpd[2456]: connect from 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]
May 25 10:22:50 example.com postfix/smtpd[2456]: warning: 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]: SASL LOGIN authentication failed: authentication failure
May 25 10:22:50 example.com postfix/smtpd[2456]: lost connection after AUTH from 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]
May 25 10:22:50 example.com postfix/smtpd[2456]: disconnect from 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]
May 25 10:26:01 example.com postfix/smtpd[2620]: connect from 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]
May 25 10:26:03 example.com postfix/smtpd[2620]: warning: 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]: SASL LOGIN authentication failed: authentication failure
May 25 10:26:03 example.com postfix/smtpd[2620]: lost connection after AUTH from 195-154-117-65.rev.poneytelecom.eu[195.154.117.65]




I use fail2ban and it create ban rule  in iptables

> -A fail2ban-sasl -s 195.154.117.65/32 -j REJECT --reject-with icmp-port-unreachable



I add in ufw

> sudo ufw deny from 195.154.117.65/32

but it still can try logins.

help please

---

### Post by rhandy2 on 2015-05-25
I found an solution

Look at : [http://ubuntuforums.org/showthread.php?t=1711478](http://ubuntuforums.org/showthread.php?t=1711478)

I create one "top" iptable rule 

But I advice for others as been searching about this

Creating one Deny rule on ufw, does´t work before allow Rules.

I also suggest create one rule on fail2ban for Persistent attackers.

Read this!!! [http://www.syntaxtechnology.com/2009/08/prevent-bruteforce-attacks-with-fail2ban/](http://www.syntaxtechnology.com/2009/08/prevent-bruteforce-attacks-with-fail2ban/)

Very good!!!! :-)

---

