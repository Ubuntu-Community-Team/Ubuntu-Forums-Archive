---
title: "server stats to sql db"
date: 2013-02-11
forum: Server Platforms
---

### Post by kr651129 on 2013-02-11
I'm working on a project where I will need to take server usage statics from several ubuntu servers and place the results in a SQL database.  Things like network activity, cpu load, cpu fan speed and heat, memory usage, etc.  Does anyone know of anything out there that can do this or will I have to handroll some software?

---

### Post by TheFu on 2013-02-11
There are many, many, many server monitoring tools. Some probably use mysql or better, pg, to store data.  My preferred tool uses rdd files, so I'm positive the file sizes never get any larger.
A few tools for you to research further.
* Monit
* SysUsage
* sar (if you like pain)
* Nagios
* Cacti[]("http://www.networkuptime.com/tools/enterprise/cacti.html")
*** **ZABBIX
* ZenOSS
If you want to put data into an MS-SQL DB, you are on your own.

If you just want access to the data in a centralized location, then **Cacti** or **SysUsage **would be my strong recommendations.

---

