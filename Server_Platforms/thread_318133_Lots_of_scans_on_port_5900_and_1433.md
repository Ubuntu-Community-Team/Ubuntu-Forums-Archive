---
title: "Lots of scans on port 5900 and 1433"
date: 2006-12-13
forum: Server Platforms
---

### Post by PetePete on 2006-12-13
was looking at my firewalls log and seems that every other entry is a probe to port 5900(VNC) or 1433 (MS-SQL) 

is there a worm which scans subnets for vulnerable hosts?

anyone know why theres so much activity on these 2 ports?

cheers

---

### Post by dbott67 on 2006-12-13
If you look at the following site, you can see the trend of source & target computers, as well as what ports are being scanned.

[http://isc.incidents.org/trends.php](http://isc.incidents.org/trends.php)
> Details

These tables strive to show trends in portscanning activity. Three basic tables are shown. **The first table (Sources), shows the change in the number of distinct source IPs scanning for a given port. The second table (Targets), shows the number of distinct IPs targeted by these sources**. The last table (Reports) uses the total number of log entries submitted.

You'll notice that there are 3912 sources scanning almost 30,000 computers daily... button up your firewall, turn off unneeded services and use SPF 45.

-Dave

---

### Post by ciscosurfer on 2006-12-13
> **PetePete said:**
> was looking at my firewalls log and seems that every other entry is a probe to port 5900(VNC) or 1433 (MS-SQL) 

is there a worm which scans subnets for vulnerable hosts?

anyone know why theres so much activity on these 2 ports?

cheersI take it you're not running a VNS-server or using MS-SQL?

---

### Post by ciscosurfer on 2006-12-13
> **dbott67 said:**
> If you look at the following site, you can see the trend of source & target computers, as well as what ports are being scanned.

[http://isc.incidents.org/trends.php](http://isc.incidents.org/trends.php)


You'll notice that there are 3912 sources scanning almost 30,000 computers daily... button up your firewall, turn off unneeded services and use SPF 45.

-DaveNice post / good link, dbott67!

---

### Post by PetePete on 2006-12-13
> **ciscosurfer said:**
> I take it you're not running a VNS-server or using MS-SQL?

no i'm not. just the basic desktop setup!

thanks to dbott for that website.

---

