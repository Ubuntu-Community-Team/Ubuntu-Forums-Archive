---
title: "Secondary DNS not responding"
date: 2009-02-22
forum: Server Platforms
---

### Post by jbarnett on 2009-02-22
I have configured a master and a secondary DNS server. The secondary will update the zone files from the master. The secondary will not answer queries from the network. If I change all of the config files to make the secondary server act like the master it will answer queries. I do have the zone files in different directories. .../zones and .../zones/secondary and those paths are correct for the config being used. I have even tried making the secondary zone file path .../zones with no luck. Is this a permission issue in apparmor or somewhere else? Any help would be greatly appreciated. Thanks...

---

### Post by hictio on 2009-02-22
How do you know the secondary does not reply to queries?
Are you querying it directlly?
Have you enabled logging on the servers (both) to see what it might be happening?

---

### Post by jbarnett on 2009-02-22
When I dig @... from elsewhere on the net I get connection timed out; no server could be reached when it is configured a s a secondary.  When I have configured it as a master in named.conf.local the dig answers. the only difference between the two is the allow-transfer line, I remove it whe I config as master.

zone "xyz.com" {
       type master;
       file "/etc/bind/zones/xyz.com.db";
       allow-transfer ( private IP; };
       };

-or-

zone "xyz.com" {
       type secondary;
       file "/etc/bind/zones/secondary/xyz.com.db";
       masters { private IP; };
       };

Machine with master resolves machine with secondary does not.  If I modify the secondary machine to match the master config it will resolve but obviously not update the zone files.

Zones consist of public address machines are NAT'd at my firewall.

---

### Post by hictio on 2009-02-22
> **jbarnett said:**
> 

~snip~

zone "xyz.com" {
       type secondary;
       file "/etc/bind/zones/secondary/xyz.com.db";
       masters { private IP; };
       };

~snip~



Try changing 'secondary' for 'slave' on the secondary DNS server, and re-init named.

EDIT:

Change the line:

```

type secondary;

```

for:
```

type slave;

```

On the config file of your named.

---

### Post by jbarnett on 2009-02-22
Sorry...typo on my part.  I had it as slave already.

---

### Post by ikonia on 2009-02-22
ok - so lets look at this objectivly here

1.) what's your domain, we are in the outside world, lets see what it's setup to from our point of view.

2.) in your domain configuration (not dns server) what are the master and secondary server set to with the registrar ?

if the slave server is not set with the registrar then when you try to query it, it won't respond as it will say "sorry - I'm not the master, go away" which would explain why you set it to the master, it resolves


post your full named config file for both slave, 


Lets work this through.

Also are you using ACL's ? if so, please explain your ACL's

---

### Post by hictio on 2009-02-22
Ok, try this against your secondary DNS server, when the setup is done the way that its giving you problems.
From another Linux box, type this:

```

dig @ip.address.secondary.DNS www.cnn.com ENTER

```

If your DNS setup prevents from resolving 'www.cnn.com', replace that with a hostname query that you know it has to work.

Post the output.

---

