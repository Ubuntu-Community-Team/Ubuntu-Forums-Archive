---
title: "BIND9, DDNS, and Windows."
date: 2006-08-09
forum: Server Platforms
---

### Post by Swab on 2006-08-09
I've setup a BIND9 server which seems to be working.  I can query from the local machine or from my Windows machine.  However I am having a problem with dynamic updating.  

Basically I want to be able to change the IP address on my Windows machine and have it updated in DNS automatically.  Currently DHCP is not involved here, just static IPs.

Not sure where I'm going wrong, or what I have missed out, but dynamic updating is not working.  I have checked the box in the windows dns settings that says "register this connections address in DNS"

Any ideas?

Here is my names.conf.local

```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";


zone "testdomain.local" {
	type master;
	file "/etc/bind/db.testdomain.local";
	allow-update { 192.168.1.0/24; };
};

```

---

### Post by Swab on 2006-08-10
bump...

---

### Post by wldake on 2006-08-26
Do you see anything in the logs about updates being denied from your PC's IP address on your BIND 9 server?

---

### Post by MorfiusX on 2006-08-27
On your Windows machines, try running "ipconfig /registerdns". Also, make sure you have a domain name suffix configure otherwise the machine won't know which zone they are supposed to be registering to.

---

### Post by Swab on 2006-08-27
Thanks for the suggestions, will take a look tomorrow.

---

