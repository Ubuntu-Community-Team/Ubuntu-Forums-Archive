---
title: "Should I separate Mysql into its own VM?"
date: 2023-02-08
forum: Server Platforms
---

### Post by Heeter on 2023-02-08
Hi all,

I have 2 KVM guests (1 Mail server, 1 Webserver) that each run their own Mysql instance within them. Wondering if it's worthwhile security wise if I was to create a standalone guest and run just the Mysql in that, and redirect other 2 servers to that one

Regards

---

### Post by TheFu on 2023-02-08
Having network-access to a MariaDB server would be a slight loss of security vs localhost only connections.
Generally, the choice would come down to the required software stack and performance, since different DB client systems may require a specific version of a DBMS.

Also, perhaps putting the DBMS directly on hardware would make more sense if you are worried about performance. That would remove the overhead that all VMs bring especially for storage access the way that most people do it.

If you have different people managing the DBMS but never touching other parts of the software stack, it might make sense too.  Don't let a DBA on any systems they don't need to be maintaining.  If you have a DBA, then it could be good for security to keep them away from other parts of the applications.

Of course, there are different opinions.

---

### Post by LHammonds on 2023-02-09
Because I have so many VMs, I opted to use a dedicated MariaDB instance for several reasons:  (*oh and MySQL development stagnated too long for me to use it*)

1. Consumption of less resources with only one DB instance as opposed to one for every app.
2. Easier to maintain backups for all databases (fewer backup/restore scripts to maintain)
3. All my VMs are hosted at the same site so communications between app<-->db never hit an external network switch
4. Remote access to the DB is kept tight...such as user123 only has specific access to the database but only from static IP 10.10.10.10 for example.
5. Firewall rules can also be configured to only allow access to the DB port from specific IPs or subnets. (e.g. only the server subnet can access but completely dark to wifi and PC networks for example)

On the flip side, that also means I cannot use the oversimplified method of "**apt install webservice**" which typically installs the DB+Web systems.  That means you have to manually install / upgrade the web apps.   This is not a bad thing in my eyes since it forces me to be very familiar with the system and how it functions rather than a black box of "it just works" which might mean its also not very secure.

Security has to be part of the whole design.  Hardware firewall, network design, hardware design/selection/implementation, proxy usage, OS design/selection/implementation, app config, etc.

LHammonds

---

### Post by Heeter on 2023-02-21
Sorry for the late post, Thank you guys for your input

Regards

---

### Post by Skaperen on 2023-02-21
sorry for the late post.

is this something containers could be used for?

or if you need the most extremely secure boundaries, how about physically separate hardware?

have you considered what certain 3-letter government agencies are doing?

---

### Post by TheFu on 2023-02-21
> **Skaperen said:**
> 
is this something containers could be used for?

Sure. Lots of places do.

> **Skaperen said:**
> or if you need the most extremely secure boundaries, how about physically separate hardware?

If you need high security, use air-gapped systems.

> **Skaperen said:**
> 
have you considered what certain 3-letter government agencies are doing?
I worked for a 4-letter agency and a 3 letter world-wide networking company ... with a number of 3-letter agencies as clients. When we wanted security, it was through air-gapped networks where we'd change protocols between different subnets (routed and non-routed) and through strong physical security to gain access to the networks, servers and workstations.  Any outside traffic allowed in was 1-way through specific links that were difficult for any non-govt to even access, since they weren't terrestrial. 
In the 3-letter company, I didn't have access to the equipment required by the 3-letter agencies. There were some floors in the building where nobody ever stopped and nobody ever discussed why that was.  They could have been specialized labs, but I did have access to a few of those where we tested all sorts of equipment.  Almost every week we were trained for 2-4 hrs in different products for almost anything related to computing systems and security.  I still remember some of the Bluecoat training 20 yrs ago and it scared me back then.  I can only imagine what is possible today, but if I can think of it, I bet someone is doing it and selling a product. Wikileaks has some bluecoat documentation - deployment guides, if you are that interested.  The company has been sold a few times and I don't know the current owner of the company. 

Don't trust https as "security", just sayin. It is part of a house of cards that can easily be attacked in ways that you are unlikely to recognize and your https client is unlikely to complain.

You are unlikely to prevent their access if they truly want it.  You can probably block 99% of the world's govts from access, with a multi-layered security architecture.  Containers or VM would be the least of my concerns in the security stack, though I wouldn't use Docker as setup by defaults. If you use any RF (wifi/bluetooth/cellular data), you've already lost the security fight.  Same if using passwords.

---

