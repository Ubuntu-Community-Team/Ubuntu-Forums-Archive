---
title: "Postfix How to prevent mail to root@localhost from external networks?"
date: 2014-10-28
forum: Server Platforms
---

### Post by -=pug=- on 2014-10-28
I've started to get some mails recently to root@localhost from external IPs trying to exploit bash. My bash is patched so I should be safe enough, but I'm not comfortable with the idea of anyone being able to send mail to the domain root@localhost from anywhere in the world.

I still need localhost for local delivery so don't want to remove it completely, ideally I'd just like to block mail to localhost and localhost.hostname from everywhere other than local delivery.

Is this possible? I've been looking online for a few hours now and I haven't been able to find a method to do this with postfix.

Running Ubuntu server 12.04 with postfix 2.11.0-1

---

### Post by TheFu on 2014-10-28
Allow from "mynetworks", not anywhere else.  Why is port 25 even available on the internet at all? 
[http://www.postfix.org/STANDARD_CONFIGURATION_README.html](http://www.postfix.org/STANDARD_CONFIGURATION_README.html) has examples. There's a local network only example.

---

### Post by -=pug=- on 2014-10-28
Thanks for replying, but the postfix instance is the MTA for my domain so it needs to be available on the Internet otherwise I don't get any mail :)

My problem is that I also need to be able to get system mails delivered to localhost on the same server, but I can't find a config to both permit mail to my domain and block mail to @localhost for everything other than local delivery

---

### Post by -=pug=- on 2014-10-29
In case anyone else comes across this thread I found a solution for this.

For postfix releases 2.10 or higher add the following to main.cf

> smtpd_relay_restrictions = permit_mynetworks, check_recipient_access hash:/etc/postfix/block_localhost, defer_unauth_destination

For postfix releases before 2.10 add the following to main.cf

> smtpd_recipient_restrictions = permit_mynetworks, check_recipient_access hash:/etc/postfix/block_localhost reject_unauth_destination

Then edit /etc/postfix/block_localhost and add the following

> root@localhost REJECT

postmap the block_localhost file and reload postfix for the new config to take effect.

The smtpd_relay_restrictions and smtpd_recipient_restrictions parameters are followed sequentially. So if there is a match in permit_mynetworks that will be used which will allow local system delivery, but if no match is found it moves onto check_recipient_access where it will reject mail to root@localhost.

Obviously if there are any existing entries already in either smtpd_relay_restrictions or smtpd_recipient_restrictions they will need to be included to maintain other existing config.

---

