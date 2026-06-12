---
title: "monitoring and logging crack attempts"
date: 2013-04-27
forum: Security
---

### Post by PshhPshh on 2013-04-27
Guys, how can I manage all those annoying attacks to my system ? Let's say, some evil unit uses nmap to scan me (Fyodor strikes back, hell yeah), what do I do to detect that ?

Also, I'm a little bit confused, that people of these forum advise the default set up for ufw (deny all incoming, allow all outgoing). Is there a way to log, which process was responsible for outgoing traffic (a possible private valuable information) ?

Also, I'm looking forward to test my machine with some simple attacks, but unfortunately, I have no second machine for making those attacks. May be, there is some cloud, where it wouldn't be that hard to install and run software like nmap and so on ? I'm afraid, it can be forbidden as considered to be too close to criminal. But how can I test my security else ?

---

### Post by TheFu on 2013-04-27
There is no simple answer to your questions.  Start by reading up on IDS/IPS systems. Google is your friend.

Basic Linux security is simple to understand.
* deploy a hardware firewall on the network connection
* run a software firewall on every computer
* block all inbound connections
* block all outbound connections that aren't clearly desired - log all others
* If you allow any inbound connections, watch for failed attempts, consider automatically blocking those IPs/subnets for some period - Look at DenyHosts or Fail2ban
* Do not run services that you don't need.
* Use simpler services over kitchen-sink services
* Avoid complexity-adding administrative tools - things like webmin or mysqladmin often overly simplify the real settings and if penetrated, allow attackers complete control over the system(s) involved.
* NEVER run a plain-FTP server (most of the time sftp would be a better choice).

Monitoring logs on servers is part of being an administrator.  Most administrators use software to filter out the unimportant log messages, but to be alerted about the very critical messages.  Look for monitoring systems, alarming systems and log watching solutions.  Things like NMS, Cacti, logwatch, monit will get you started. There are lots of other, better choices, but that depends on your specific network and risk level.

You can run a virtual machine and run attacks from it, if your hardware is sufficient. Also, running attacks from a remote VM is a good idea too.  Amazon will provide a free "tiny" Linux VM for a year that you can launch attacks from.  If you share this with security friends, then you can switch to a new "free" install every year using a different person. Clearly, amazon will see all your network probes, so do not expect to be anonymous doing this.

Those advised firewall defaults are fine for a house connection, but terrible for a corporate setting.  In a corporation, knowing about all the outbound traffic is critical for security.  Few Linux firewall solutions are used by my friends in the professional IT Security business.  Seems that Linux kernels have failure modes most networking pros consider undesirable.  pfSense is the routing/firewall platform they suggested to me for a small office from 1 to 500 people.   You can run pfSense inside a VM too.  blocking outbound traffic, except from an approved internal proxy IP is a good step. Blocking DNS from internal machines is another step - but doing this is hard if you only have 1 PC.

I consider network security more important than computer security.  Network equipment can provide better protection from more attacks than any PC directly attached to the internet can, IMHO.  A dedicated device is important when it comes to network security.

Clearly, there are many different opinions about security. People that have never been hacked probably have a less paranoid take on security.  Systems that I managed have been hacked 3 times, but none in the last decade.  I'm paranoid, with good reason. "THEY" aren't out to get me. "THEY" are out to get everyone and have computers doing the automation.

Sorry - I was on a roll.  Hopefully I provided some leads for more research.  Google "how to secure linux" as a good way to get started. Also know that all of those articles are missing key aspects of a secure system. Hopefully, when all of them are combined, you'll have a more secure setup, overall.   

Good luck.

---

### Post by PshhPshh on 2013-04-27
A starting point appeared to be a little larger than expected... wow... 
Thanks, TheFu, I will return, I hope so.

---

### Post by CharlesA on 2013-04-27
> **TheFu said:**
> 
* If you allow any inbound connections, watch for failed attempts, consider automatically blocking those IPs/subnets for some period - Look at DenyHosts or Fail2ban


Agreed. I've been using iptables to do logging of attacks on ssh and logging them. Then having logwatch send me a report.

> * Use simpler services over kitchen-sink services

I've seen this when I was trying to set up my mail server. I originally used iRedMail, but it includes a ton of stuff that I wasn't using and it ran pretty heavy on my (small) VPS. I've set it up manually now and it runs a whole lot lighter now. Besides, less services = good.

I don't really think I have anything else to add outside of learning to read your logs or use a log management/reporting tool like mentioned above.

---

### Post by clearski on 2013-04-27
I knew I needed a better log watch application and I see that you recommend *logwatch*. I found it in the Ubuntu library, but I read that it emails the results every night. Does it require a mail server on my system to send emails? I am afraid so...

---

### Post by CharlesA on 2013-04-27
> **clearski said:**
> I knew I needed a better log watch application and I see that you recommend *logwatch*. I found it in the Ubuntu library, but I read that it emails the results every night. Does it require a mail server on my system to send emails? I am afraid so...

Yes, you need a SMTP server, but you can limit it to localhost or firewall it so it isn't accessible from outside. I've been running one on my home server as a relay thru gmail due to my ISP blocking port 25.

---

### Post by TheFu on 2013-04-27
> **CharlesA said:**
> Yes, you need a SMTP server, but you can limit it to localhost or firewall it so it isn't accessible from outside. I've been running one on my home server as a relay thru gmail due to my ISP blocking port 25.

Sending authenticated email from any Linux system is relatively easy. There are how-to guides. Most of the time, you just need to use your ISP email servers and account, so you don't look or act like a spammer. You don't need to accept any inbound email at all to send.  To retrieve email from another server, use a pop3s or imaps client - these can be a GUI or you can poll using something like **fetchmail**. This way, you have all your email locally and don't need to use a remote server. Of course, with all your email local, now you accept responsibility for failures, corruption, backups and virus checking.  Email is really 2 different services:
* SMTP for sending (or for servers to talk to each other).  Postfix is an example.
* IMAP/POP3 for retrieving or allowing clients to retrieve emails. courier-imap is an example server and almost any GUI email program you've ever used it a client.

BTW, that **Basic Security** link at the bottom of Charles' posts is really great. Much, much better than my answer, even if it is more generic.

---

### Post by clearski on 2013-04-28
> **CharlesA said:**
> Yes, you need a SMTP server, but you can limit it to localhost or firewall it so it isn't accessible from outside. I've been running one on my home server as a relay thru gmail due to my ISP blocking port 25.

I'll definitely go for a local mailserver. I don't know how soon, but I will. Did you run sendmail or other server?

---

### Post by clearski on 2013-04-28
> **TheFu said:**
> Sending authenticated email from any Linux system is relatively easy. There are how-to guides. Most of the time, you just need to use your ISP email servers and account, so you don't look or act like a spammer. 

I would never let my security logs and annoucements go through Gmail's servers (or any other provider's). I don't think that anybody there is wasting time with my logs, but it's just a matter of principle. I could also have my router sending security emails, but I prefer to read the logs until I'll setup a local mailserver for my needs. :)

---

### Post by CharlesA on 2013-04-28
> **clearski said:**
> I'll definitely go for a local mailserver. I don't know how soon, but I will. Did you run sendmail or other server?

Postfix for me.

> **clearski said:**
> I would never let my security logs and annoucements go through Gmail's servers (or any other provider's). I don't think that anybody there is wasting time with my logs, but it's just a matter of principle. I could also have my router sending security emails, but I prefer to read the logs until I'll setup a local mailserver for my needs. :)

I only use gmail cuz I didn't have the VPS setup when I built my home server. It works fine for me and there shouldn't be any real sensitive information in logs anyway. Usernames, sure, but I don't think passwords are logged, unless you mistype something via sudo.

---

### Post by TheFu on 2013-04-28
> **clearski said:**
> I would never let my security logs and annoucements go through Gmail's servers (or any other provider's). I don't think that anybody there is wasting time with my logs, but it's just a matter of principle. I could also have my router sending security emails, but I prefer to read the logs until I'll setup a local mailserver for my needs. :)

100% agreed on the not shipping security info outside my network. This is in the "can do it", not "should do it" realm.  OTOH, the base information is still true.

I think that very few people should actually run sendmail. Most commercial shops shouldn't unless they really need all those capabilities and dangers. I've been running Postfix for commercial uses about 15 yrs.  Easy enough.

---

### Post by clearski on 2013-04-29
To Charles A & TheFu

Alright, I see that you both recommended PostFix, so that will be. :)

Thank you!

---

