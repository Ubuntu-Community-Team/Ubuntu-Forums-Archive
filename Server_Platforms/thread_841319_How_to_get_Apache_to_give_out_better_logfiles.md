---
title: "How to get Apache to give out better logfiles?"
date: 2008-06-26
forum: Server Platforms
---

### Post by stfu on 2008-06-26
I'm trying to set up awstats on my small apache box but cannot get referrers / OS out of the apache log files (level 2). I'd like to see them, so how do I change the loglevel to more accurate?

---

### Post by MJN on 2008-06-26
You typically need to do two things - advise Apache of the format of the logs (and by implication what to log) and then tell it to log in this format.
 
The standard format for the information you require is the 'Combined Log Format'. To use this put the following in either /etc/apache2/apache2.conf or within the relevant virtual host(s) as required:
 
```
[FONT=Courier New]LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-agent}i\"" combined[/FONT]
[FONT=Courier New]CustomLog /var/log/apache2/access_log combined [/FONT]
``` (I thought this was the default configuration anyway, perhaps the format is defined but only 'common' logging is selected)
 
Mathew

---

### Post by stfu on 2008-06-26
> **MJN said:**
> You typically need to do two things - advise Apache of the format of the logs (and by implication what to log) and then tell it to log in this format.
 
The standard format for the information you require is the 'Combined Log Format'. To use this put the following in either /etc/apache2/apache2.conf or within the relevant virtual host(s) as required:
 
```
[FONT=Courier New]LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-agent}i\"" combined[/FONT]
[FONT=Courier New]CustomLog /var/log/apache2/access_log combined [/FONT]
``` (I thought this was the default configuration anyway, perhaps the format is defined but only 'common' logging is selected)
 
Mathew

Yeah, it's something like that. I see the variables in apache conf and it should be ok. I have to see if the format is defined wrong. Thanks for the answer.

---

