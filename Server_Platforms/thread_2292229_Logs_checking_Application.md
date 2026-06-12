---
title: "Logs checking Application"
date: 2015-08-26
forum: Server Platforms
---

### Post by KaCanuHa on 2015-08-26
Hi guys,

I'm looking for some simple solution. We have currently some Linux virtual servers - most of them Ubuntu. From time to time we want to check if everything in logs is ok. The servers so far are running without any problems, they've been updated with security updates and so on. Of course they are server version and we are not so good without GUI :( so I was thinking to install Ubuntu Desktop and maybe install there some application and use to connect to the Ubuntu servers and check if there is something critical or important. I'm not looking to a solution which will constantly connect and collect the logs. For our needs it will be ok if there is a web interface where to logon and after this select the server pickup time interval - for example last 2 weeks or last 30 days, make a filtering of critical and important things and have an export. Do you know about something useful?  Thanks in advance

---

### Post by howefield on 2015-08-26
Thread moved to the "*Server Platforms*" forum for better support.

---

### Post by KaCanuHa on 2015-08-26
Thanks

---

### Post by Habitual on 2015-08-27
Kibana4 server using an "ELK 'stack'"
[http://knowm.org/how-to-set-up-the-elk-stack-elasticsearch-logstash-and-kibana/](http://knowm.org/how-to-set-up-the-elk-stack-elasticsearch-logstash-and-kibana/)

logstash-forwarder on any client machines. 
Send logs to Kibana.
Browse forwarded logs from all clients in Kibana.

Cool stuff Maynard.

---

### Post by TheFu on 2015-08-28
logwatch.

---

### Post by tgalati4 on 2015-08-28
A simple script which searches keywords using *grep* that runs as a cronjob, then email the results or simply store them on a shared directory so they are easy to find.

Spend some time with *gnome-system-log* or *mate-system-log*.  It is a GUI log file viewer that is installed on most desktop systems.

---

### Post by SeijiSensei on 2015-08-28
+1 for logwatch

It will send daily summaries by email.

---

### Post by QIII on 2015-08-28
Definitely logwatch.

---

### Post by slickymaster on 2015-08-28
+1 for logwatch

---

### Post by Habitual on 2015-08-28
He did specify "simple" and ELK is not.
Sorry about that.

---

### Post by KaCanuHa on 2015-08-31
thanks for your answer folks, I've remember that I've seen some of the recommendations but I think that they are a little bit complicated for my level of knowledge. I was thinking more like an "app" which to be used from time to time not for sending daily reports. We are already using check_mk for monitoring some services and "applications" inside the servers but we limit it because if we check everything this will bring a lot of burden on us. I will give a shot to logwatch to see how it "fits" for us. Thank you again for your time.

---

### Post by TheFu on 2015-08-31
Monitoring logs for a server daily is part of the cost of doing business in having a server. 
Not monitoring the logs daily is asking for trouble.

This is a well-worn best practice and logwatch is by-far the easiest answer.

---

### Post by KaCanuHa on 2015-08-31
thank you for your answer I agree with you but our external guy made the things like - install, configure and forget about problems :) About linux servers I totally agree with him and if they are not Internet-facing makes things a bit easier. All we need to take care is installing security updates from time to time. In my previous job we had a linux server working as a router, web server, file server and it was working like this for 5 years with only 3 reboots because of the power outage :) If something is working don't mess with it.

---

### Post by TheFu on 2015-08-31
Little issues, seen early are usually easier to address.

If an application RTO/RPO allow outages - fine.  That is completely up to the client.  When something fails, getting paid more to fix it than if the issue was caught and corrected at the first opportunity.  That's fine too.

I wish you luck.

---

### Post by Habitual on 2015-09-01
I found [this]("https://mathias-kettner.de/check_mk.html") interesting. A nagios fork/spin-off?
and this Check_MK has a "Logfile Pattern Analyzer" built right in.
Now I'm confused. Does the OP have this option in his Check_MK dashboard?

---

