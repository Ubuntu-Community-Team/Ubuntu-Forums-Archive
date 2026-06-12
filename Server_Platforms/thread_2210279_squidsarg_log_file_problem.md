---
title: "squid/sarg log file problem"
date: 2014-03-10
forum: Server Platforms
---

### Post by viperce on 2014-03-10
Hi,

Im having a slight issue with squid/sarg, I think my issue is more on the squid side....

I have noticed lately that squid isnt creating a new log file everything is being dumped into the access.log all the cache is also being stored in the cache.log and as a result 
when sarg creates its daily logs, the log file starts from 

[TABLE]
[TR]
[TD="class: data2"][2014Feb24-2014Mar10]("https://192.168.254.180:10000/sarg/view.cgi/2014Feb24-2014Mar10/index.html")[/TD]
[TD="class: data2"]Mon Mar 10 08:06:53 2014[/TD]
[TD="class: data"]49[/TD]
[TD="class: data"]14.40G[/TD]
[TD="class: data"]294.00M[/TD]
[/TR]
 [TR]
[TD="class: data2"][2014Feb24-2014Mar08]("https://192.168.254.180:10000/sarg/view.cgi/2014Feb24-2014Mar08/index.html")[/TD]
[TD="class: data2"]Sat Mar  8 06:31:53 2014[/TD]
[TD="class: data"]49[/TD]
[TD="class: data"]13.91G[/TD]
[TD="class: data"]284.02M[/TD]
[/TR]
 [TR]
[TD="class: data2"][2014Feb24-2014Feb27]("https://192.168.254.180:10000/sarg/view.cgi/2014Feb24-2014Feb27/index.html")[/TD]
[TD="class: data2"]Thu Feb 27 14:35:03 2014[/TD]
[TD="class: data"]41[/TD]
[TD="class: data"]7.09G[/TD]
[TD="class: data"]173.07M[/TD]
[/TR]
 [TR]
[TD="class: data2"][2014Feb24-2014Feb26]("https://192.168.254.180:10000/sarg/view.cgi/2014Feb24-2014Feb26/index.html")[/TD]
[TD="class: data2"]Wed Feb 26 15:35:53 2014[/TD]
[TD="class: data"]38[/TD]
[TD="class: data"]2.46G[/TD]
[TD="class: data"]64.82M[/TD]
[/TR]
 [TR]
[TD="class: data2"][2014Feb14-2014Feb17]("https://192.168.254.180:10000/sarg/view.cgi/2014Feb14-2014Feb17/index.html")[/TD]
[TD="class: data2"]Mon Feb 17 08:09:36 2014[/TD]
[TD="class: data"]31[/TD]
[TD="class: data"]800.30M[/TD]
[TD="class: data"]25.81M[/TD]
[/TR]
 [TR]
[TD="class: data2"][2014Jan25-2014Feb14]("https://192.168.254.180:10000/sarg/view.cgi/2014Jan25-2014Feb14/index.html")[/TD]
[TD="class: data2"]Fri Feb 14 16:24:52 2014[/TD]
[TD="class: data"]59[/TD]
[TD="class: data"]22.67G[/TD]
[TD="class: data"]384.32M
[/TD]
[/TR]
[/TABLE]


does anyone know how i could possibly resolve this?


thanks in advance.

---

### Post by SeijiSensei on 2014-03-10
I've not understood this question when you posted it in the past.  Are you saying you want to have SARG generate a daily report?  Probably the simplest solution is to rotate the access logs daily using logrotate.

Create a file called "squid" in /etc/logrotate.d/ with the following content:
```

/var/log/squid/access.log
{
        rotate 15
        daily
        missingok
        notifempty
        postrotate
            /usr/sbin/squid -k rotate 2>/dev/null
        endscript
}

```
This generates a new squid log every day and preserves the prior fifteen days of logs in /var/log/squid.

---

### Post by viperce on 2014-03-11
Thanks dude Ill give this a try

 my squid is not currently generating a new squid log file so all the data is being stored in 1 file and it seems like when i do my Report using sarg, it generates a report with all the information in 1 report

2014Feb24-2014Mar10     Mon Mar 10 08:06:53 2014     49     14.40G     294.00M

will let you know what happens.

---

### Post by SeijiSensei on 2014-03-11
Oh, one other thing.  You'll need to tell SARG to analyze /var/log/squid/access.log.1, since that will be yesterday's data after rotation.

---

