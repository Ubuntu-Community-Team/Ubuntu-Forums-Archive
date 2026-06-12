---
title: "Apache randomly displays 404 page"
date: 2009-03-23
forum: Server Platforms
---

### Post by tini on 2009-03-23
Hi there

I have a strange behaviour with apache2 on Ubuntu.

I noticed today that the webserver randomly displays the 404 page.
By randomly I mean, that I cannot observer a behaviour pattern, i.e. restarting apache2 does not solve the problem.
But sometimes, the webserver display the installed Wordpress application without any problem.

Does anybody have an idea, why this is happening or where I should look for further info?

Thx in advance

Martin

---

### Post by Bachstelze on 2009-03-23
> **tini said:**
> 
Does anybody have an idea, why this is happening or where I should look for further info?

The Apache error log: /var/log/apache2/error.log

---

### Post by tini on 2009-03-23
Yeah, that was the first place I looked into.

I didn't see anything unusual. So, I raised the LogLevel from "warn" to "notice", maybe I'll se more.

---

### Post by tini on 2009-03-23
Well, I don't think this problem is related to Apache, because sometimes I can ssh/scp to the server and sometimes I cannot.

Very strange. Any idea?

---

### Post by wineman on 2009-03-23
check if your version of apache2 is stable or development, that can affect it quite hectically.
the issues that apache2 is showing is common in the development versions, so check if the version you have (along with it's plugins) is stable. rather downgrade apache2 to stable than have a non-functional web server.

also, it sounds like you are running a beta / alpha version of ubuntu. Rather stick to 8.04, it's 99 % complete, plus the server-side software is almost all stable, even if the repositories are a bit out of date. The issues you're experiencing are similar to the issues that i went through on my home server, and i was using a devel. version of ubuntu.

otherwise, uninstall apache2 and build it from source. that is a bit extreme but it's the ultimate way to fix issues. also check up on your squid/apache2 config, and on your version of apache2.

Good luck mate:D

---

### Post by tini on 2009-03-23
Thanks for your hints.

I'm running "Ubuntu 8.10 Server Edition", Kernel is 2.6.27-11-server with Apache 2.2.9.

Isn't this software considered to be stable?

---

### Post by wineman on 2009-03-24
ya im running 8.10 as well, except that it also gives me issues...
maybe we should report this as a bug. Honestly im stumped - i thought it had something to do with unstable software. the only thing it MIGHT be is a squid / browser issue, but hten we go back to the LAN cards. try "apt-get upgrade"ing your system, see if that helps.

i would have canned the idea if it gave me this much trouble. 
But good luck mate:D

---

