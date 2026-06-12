---
title: "postfix problem"
date: 2014-12-11
forum: Server Platforms
---

### Post by katja2 on 2014-12-11
so, i have a problem.. trying to set up postfix/dovecot.. just apt-get installed both.. they run fine. haven't messed with dovecot yet because postfix doesn't work...

installed postfix. set hostname and stuff to my website.com (website.com is an example site for asking this question. not the actual site.) address.. not sure what to do.. most websites with tutorials on the dovecot/postfix website say postfix should work out of the box... just configure it to accept external mail and associate with website.com. configs look ok in webmin... 

one tutorial has you just apt-get install it and then it say: "[COLOR=#333333][FONT=CartoGothicStdBook]Now you will be able to send mail from your server.  Try it with a command like this from your server: [/FONT][/COLOR]echo "test" | mail -s testsubject [email]someemail@hotmailorwherever.com[/email]"

but that doesn't work on my system... normal xubuntu 14.04 distro. i try telnetting into localhost on port 25 which should be postfix and i get 220 website.com ESMTP Postfix (Ubuntu)... looks good.. but then i access it from the internet.. using telnet website.com 25... i get 220 **********************************************

so, something's not right... obviously the ports are forwarded.. not sure. my MX records on my DNS server are MX @ @ with a TTL of 1 hour. the A record of @ is my server's IP address, as it should be. that works perfectly.. but not mail.....

what do?

---

### Post by TheFu on 2014-12-11
Some ISPs block port 25. This is common for residential locations.
Can you telnet to the IP and port 25 from anywhere on the internet?

---

### Post by katja2 on 2014-12-11
> **TheFu said:**
> Some ISPs block port 25. This is common for residential locations.
Can you telnet to the IP and port 25 from anywhere on the internet?

yes. tried doing it from school. it worked. got that reply.

---

### Post by TheFu on 2014-12-22
> **katja2 said:**
> yes. tried doing it from school. it worked. got that reply.

If it worked, is this solved?

---

