---
title: "exim4"
date: 2008-11-26
forum: Server Platforms
---

### Post by Joel Duckworth on 2008-11-26
Hi,

We're running Ubuntu Server Gutsy and have exim4 installed and configured for sending emails from our internal machines. We're running into some issues with the time it takes to accept a message via SMTP. When we run the same delivery against our Exchange server the message is accepted in a fraction of a second however it takes about 5 seconds for the same process to occur with Exim. There are no DNS issues in the logs, the log entry just shows:

2008-11-27 13:49:28 1L5Wwa-0005K5-Fq <= [email]mailtest@obfuscated.com.au[/email] H=pc-051.obfuscated.local (pc-051) [10.14.11.38] P=esmtp S=581 id=8856448.0.1227754168310.JavaMail.jduckworth@pc-051
2008-11-27 13:49:28 1L5Wwa-0005K5-Fq => [email]joel.duckworth@obfuscated.com.au[/email] R=dnslookup T=remote_smtp H=mail.obfuscated.com.au [218.185.72.86]
2008-11-27 13:49:28 1L5Wwa-0005K5-Fq Completed

The message is coming from a java application using javamail.

I've done a little reading and found it may be a setting in Exim to have background delivery of messages so the connection does not wait for delivery to occur before closing. 

Is anyone able to point me in the right direction? Thanks.

---

### Post by Philio on 2008-11-26
I know it doesn't look like it from your logs, but are you sure it's not the DNS lookup that's causing the delay?
I've had a similar issue in the past and installing a caching name server solved the problem.

---

### Post by Joel Duckworth on 2008-11-26
Hi Philio, Thanks for the reply, I'm just doing some more testing on it at the moment I'm watching DNS traffic and log while I make the connection. There appears to be large delay at the start where no log and no DNS traffic (sudo tcpdump -i eth0 "port 53") occurs, then there is a flurry of DNS resoltion and the messages goes through in the log. What caching nameserver are you using out of curiosity? And any other ideas?

---

### Post by Joel Duckworth on 2008-11-26
I've found the problem if anyone else is having slow smtp connections it's probably because your hosts are not responding to rfc1413 requests and the default delay to wait for these is 5 seconds. I'd never heard of rfc1413 but you can read about it here: [http://www.nabble.com/Delay-when-connecting-to-send-mail-td15266057.html](http://www.nabble.com/Delay-when-connecting-to-send-mail-td15266057.html) 

Simple soltion, update your exim config to have 

rfc1413_query_timeout = 0s 

...which for me was done by updating /etc/exim4/exim4.conf.template and reloading. It may be different if you are using the split config file system then the config will be under /etc/exim4/conf.d somewhere.

---

