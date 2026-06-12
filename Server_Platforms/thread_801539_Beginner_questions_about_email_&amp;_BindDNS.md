---
title: "Beginner questions about email &amp; BindDNS"
date: 2008-05-20
forum: Server Platforms
---

### Post by Mech13 on 2008-05-20
I have a decent amount of knowledge about computers, but when it comes to servers and command line interfaces I&#8217;m not all that good but i'm starting to get the hang of it.

_So far this is my set up:_
I have a good desktop computer that I am running Ubuntu 8.04 with a 15Mbit up and downstream connection using a static IP address with no blocked ports. So far I have configured Ubuntu to its own static IP address inside of my home network, did the Port Forwarding on my router to the server (ports 80, 25, 110, 20-21, 10000) and have signed up for a web page using GoDaddy.com. I&#8217;m currently using GoDaddy's Total DNS service and entered my IP address under the ARecord to get it forward to my home server. I also do most of the management of the server from Webmin.


_My questions are:_
I have my webpage configured to allow users to set up usernames to access the forums. But, I can't get the confirmation e-mails to be sent out; I&#8217;m assuming that this is because I don't have the email properly configured on my server (the webpage code has worked before, just on a different server). I was hoping someone could tell me how to configure Sendmail, PHP or SMTP as I can use anyone of them for the autogen confirmation e-mail. Sendmail is currently installed, and it's the one that i'm trying to use.

I was thinking about using the BindDNS setup instead of using GoDaddys Total DNS service. Is that a good way for me to go?

Also, I get 2 errors when I boot up my server. The first is "Starting DHCP server dhcpd3" [[COLOR="Red"]fail[/COLOR]]
and
"apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for Servername"
What should i do to resolve these errors?

---

### Post by Mech13 on 2008-05-21
Update:
I have done some googleing and searching through the forums and found the BIND DNS post by tomtom_in_eire: [Bind DNS]("http://ubuntuforums.org/showthread.php?t=236093")


But i'm not sure how to bridge what he said to do with a godaddy.com account.
After more googling i was able to find a post that explains how to configure bindDNS with godaddy, but it's for openSuSE. [ Configure Bind in openSuSE]("http://torqzone.com/index.php/2007/12/22/configure-bind-to-work-with-godaddy/")

I'm really stuck on this problum, could someone please help me out?

---

### Post by Mech13 on 2008-05-21
_Sendmail Update_
After a long night of strugelling with sendmail, these are the error messages i'm still getting after i set it up.

```
WARNING: Local host name (server) is not qualified; see cf/README: WHO AM I? 
/etc/,ao;/aliases: 2 aliases, longest 8 bytes, 26 bytes total
```

and

```
Warning: These messages were issued while creating sendmail.cf make sure they are benign before starting sendmail!

Errors is generating sendmail.cf
***ERROR: FEATURE() should be before MAILER()
***MAILER('local') must appear after FEATURE('always_add_domain')***ERROR: FEATURE() should be before MAILER()
***MAILER('local') must appear after FEATURE('allmasquerade') ***ERROR: FEATURE() should be before MAILER()
```

---

