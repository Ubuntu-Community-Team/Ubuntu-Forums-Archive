---
title: "Postfix program / Bind"
date: 2009-10-01
forum: Server Platforms
---

### Post by apolloeye on 2009-10-01
Hi, I hope you guys can help. I get hundreds of emails a day sent to the system email address with the following body:

```
This is the Postfix program at host ubuntu.servername.info.

I'm sorry to have to inform you that your message could not be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to <postmaster>

If you do so, please include this problem report. You can delete your own text from the attached returned message.
```

I believe I am getting spamed because of open SFP (so I have been told.) I have tried to change my "named.conf.local" file to include the zones file but I toke town every site on the server due to a DNS problem. My "named.conf.local" file looks like this:

```
// __NS1__ "ns1.servername.info" DO NOT DELETE - REQUIRED BY MATRIX CONTROL SOFTWARE
// __NS2__ "ns2.servername.info" DO NOT DELETE - REQUIRED BY MATRIX CONTROL SOFTWARE
// __ADMIN_EMAIL__ "serveradmin@servername.info" DO NOT DELETE - REQUIRED BY MATRIX CONTROL SOFTWARE
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

	
zone "servername.info" in {
        type master;
        file "db.servername.info";
    };
	
zone "website1.com" in {
        type master;
        file "db.website1.com";
    };
	
zone "website2.co.uk" in {
        type master;
        file "db.website2.co.uk";
    };

```

The websites repeat on for ages but you should get the idea. The server is a Ubuntu server says:

```
Linux ubuntu.servername.info 2.6.15-26-686 #1 SMP PREEMPT Fri Sep 8 20:16:40 UTC 2006 i686 GNU/Linux
```

Any help would be greatly received, getting very fed up of all these bounce backs.

---

