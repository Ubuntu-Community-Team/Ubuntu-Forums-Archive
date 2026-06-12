---
title: "Root email being rejected by Postfix because hostname/ip is wrong"
date: 2018-09-12
forum: Server Platforms
---

### Post by webmuppet57 on 2018-09-12
I have Serverpilot install and when the system generates email for root from system tasks like CRON the emails can't be delivered. In the syslog & mail.log the mailserver refused connection but when I look the connection is to "hostname (ip address)" and the hostname is correct for the this server but the IP address is wrong. The hostname is what the VPS provider has given the server and for some reason that hostname resolves to the wrong IP address when I do an NSLookup both locally and from elsewhere on the internet. The host / ip is in the hosts file and is correct in there but for some reason Postfix doesn't seem to get the right IP for the local server. I can send email fine by telnetting into 127.0.0.1 and PHP can send emails fine too.

Where can I change this so that root tries to send through the right IP address? Being the root mail I don't want to mess around too much.

---

### Post by TheFu on 2018-09-12
Why not just use the correct IP and don't trust DNS?
You can setup a alias for root to be root@123.123.123.123, 
Put it in /etc/aliases, then run sudo newaliases to update the DB for the MTA.  I assume you have an MTA running. If not, I cannot help. Sorry.

It is always best to look at the log files, then search for that exact error with google and the release you are running for answers.  Remove the things that are specific to your install in the search-term.

---

### Post by webmuppet57 on 2018-09-17
This turned out to be a doh moment. The hostname & hosts were wrong and I fixed them but I didn't realise the entries in syslog were for emails pre the change that were deferred and kept being retried. Once I purged the queue all was fine again. Oops!

---

