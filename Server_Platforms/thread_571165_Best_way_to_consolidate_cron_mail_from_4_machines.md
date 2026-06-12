---
title: "Best way to consolidate cron mail from 4 machines?"
date: 2007-10-09
forum: Server Platforms
---

### Post by andb on 2007-10-09
Does someone have a clever solution to consolidate email from cron from multiple machines, without setting up a mail server on each and every one of them? 

In my home I have: 
1. main server 
2. application server running in VM 
3. testing server in VM
4. Freevo based mediacenter

All of these generate mails from cron jobs. Id like to consolidate all of these. Ideally I would like to receive all of the mail to a gmail account, but I may settle for a local solution if it proves easier.

Anyone found a creative way to deal with this? :eek:

---

### Post by HermanAB on 2007-10-09
Cron is configured by the file /etc/crontab.  In there is a MAILTO=whoever@wherever.tld parameter.  

Set that parameter to the same email address on all machines. You do need a MTA to send the mail, but this MTA can be a simple one, like nullmailer [http://untroubled.org/nullmailer/](http://untroubled.org/nullmailer/)

Hope that helps!

Herman

---

### Post by conjur3r on 2007-10-09
You can make use of a centralised syslog server.  Eg, specify one of those servers to be that centralised server, then configure all other servers to send their logs to that central server.  This requires a little bit more effort but is extremely handy.

---

