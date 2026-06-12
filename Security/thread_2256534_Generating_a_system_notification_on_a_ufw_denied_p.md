---
title: "Generating a system notification on a ufw denied packet"
date: 2014-12-13
forum: Security
---

### Post by actionmystique on 2014-12-13
Environment: Ubuntu 14.10
--------------------

Hello everyone,

If we configure ufw to deny all incoming packets not matching any allowing rule, how is it possible to have a system notification (other than just a line in the log) when a packet is denied?

Regards.
JC

---

### Post by bashiergui on 2014-12-14
If you want ufw to notify you of every blocked packet then there are a lot of possibilities. If you asked that would indicate that you can't write your own script.  So you can search for other people's scripts that you could use or adapt. Here's one: [http://petrusgomes.wordpress.com/2010/09/25/one-more-step-ufw-notify/](http://petrusgomes.wordpress.com/2010/09/25/one-more-step-ufw-notify/)


Someone on this forum wrote a script to notify:
[http://ubuntuforums.org/showthread.php?t=1716171](http://ubuntuforums.org/showthread.php?t=1716171)


You could also set ufw to email you but that would require you to run an email server.


Look at your ufw logs to determine how many notifications you would get per minute/hour before you go to the trouble of setting up alerts. If the firewall faces the internet then you'll probably find it would be much easier to just review the ufw logs regularly.

Depending on what you plan to do with the notifications you might also consider something like fail2ban that would automatically ban misbehaving IPs instead of just telling you about them.

---

### Post by actionmystique on 2014-12-15
Thanks for your answer. Writing scripts takes time, I thought there would be an app for that important feature. fail2ban might do the trick.

But you're right: if we cannot narrow down the extent of the notifications sources, such as what range of IP addresses/Protocols/Ports numbers IN/OUT do or do not trigger notifications, we would be overwhelmed with them.

---

