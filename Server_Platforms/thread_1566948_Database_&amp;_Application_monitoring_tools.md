---
title: "Database &amp; Application monitoring tools"
date: 2010-09-03
forum: Server Platforms
---

### Post by Thyagaraj on 2010-09-03
Could any one suggest me the tools for database and application monitoring.
Thank you!

---

### Post by R.Bucky on 2010-09-05
Munin, Splunk, htop, Apache2 mod_status. Otherwise, be more specific with your question. What applications and what type of monitoring tools. Do you just want db stats, or network throughput...?

---

### Post by Thyagaraj on 2010-09-05
I''m looking for the tool that monitors all the applications running(tomcat apache mysql ....) and I'm even asked to find out database monitoring tool(I'm not sure about this but need it urgently).
The following tools I tried.

munin- couldn't configure it to monitor tomcat 
monit- supports only graphical format
zabbix- presently using this tool but doesn't provide more information about monitoring application and don't know how about database monitoring and email notification is failed to notify
nagios- tried this but don't know how to use this
zenoss- tried but not monitoring any of the resources

I'm looking for the tools that monitors hosts, hardware, services, application, database along with email notification.
If you could suggest me the tool to monitor all the application or the databases, it's also better. But somehow need help...

Thank you!

---

### Post by inphektion on 2010-09-05
nagios probably your best bet.  follow the 15 min quickstart.  
start small i know it can be overwhelming.  have an initial config where nagios is just monitoring the ping to server.  then add plugins and features incrementally.

---

### Post by Thyagaraj on 2010-09-06
Thank you I'll try that.

I used Splunk but I'm not sure if it is a database monitoring tool or application monitoring tool.
Actually I'm confused, what is application and what is database?.

---

