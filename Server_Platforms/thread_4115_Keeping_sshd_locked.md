---
title: "Keeping sshd locked"
date: 2004-11-12
forum: Server Platforms
---

### Post by mrdud on 2004-11-12
All right first off, I'd like to state that I'm some what paranoid. I use ssh and I have created a simple script that parses the /var/log/auth.log for any information pertaining to sshd. 

I also added the AllowUsers <username> line to my /etc/ssh/sshd_config file (multiple users separated with spaces). Lowered the LoginGraceTime to 30 seconds, and installed Firestarter and use that to block any offending IP addresses. 

Now for the help part. I'm lazy but paranoid. So I know I can always throw it in cron.hourly and have that run but I got control issues too. I want to know whats happening NOW not 50 minutes later. 

Well aside from that my windows back ground has really hindered me on trying to make my little script. I was wondering if anyone knew of a way to add in checks for the date so it will only post the relevant information for that day. Also if anyone else has any other information besides leaving a root terminal open or typing my password a few times a day.

Heres the little bugger any other information/tips will be awsome!

```
# File to parse the logfile and to print out any ssh info
#/bin/bash
cat /var/log/auth.log |grep sshd >> sshd.txt |vi sshd.txt
```

---

### Post by jdong on 2004-11-12
[http://www.astro.uiuc.edu/~r-dass/logcheck/](http://www.astro.uiuc.edu/~r-dass/logcheck/)

Logcheck is a great program for that purpose. It's in Universe. I have it set up on my server to mail me new portions of the log nightly.

---

### Post by FLeiXiuS on 2004-11-12
[QUOTE=jdong][http://www.astro.uiuc.edu/~r-dass/logcheck/](http://www.astro.uiuc.edu/~r-dass/logcheck/)

Logcheck is a great program for that purpose. It's in Universe. I have it set up on my server to mail me new portions of the log nightly.[/QUOTE]


I was always a fan of Afick.
[http://afick.sourceforge.net/](http://afick.sourceforge.net/)

Great system security logger.

---

### Post by mrdud on 2004-11-18
Thanks for the suggestions, just noticed about fifty entries of 

User root not allowed because not listed in AllowUsers

All in my email, thanks very convenient!

---

