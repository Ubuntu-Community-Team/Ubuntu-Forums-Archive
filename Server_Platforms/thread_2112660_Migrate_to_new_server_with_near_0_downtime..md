---
title: "Migrate to new server with near 0 downtime."
date: 2013-02-05
forum: Server Platforms
---

### Post by rs2k on 2013-02-05
I'm needing to move a production website to a new server with near 0 downtime. The website is php and mysql based with sessions handled in the mysql database. I assume the best way to do it would be to have the php website on both servers use just the one mysql server on the new server until the DNS is done dancing around? (One remotely and one localhost)

I don't like the idea of having a mysql server open to remote connections, but I don't know of any other way to do it and it will only be open for a few days.

---

### Post by spynappels on 2013-02-05
Are the two servers going to be in the same location, on the same subnet? Or will they both have public IPs?

---

### Post by rs2k on 2013-02-05
Public IPs on two different hosts in two different geographical locations.

---

### Post by spynappels on 2013-02-05
Ouch.

How latency sensitive is the connection to the mysql server going to be?

Will access to the mysql database be required from the old server when the new one is up? I guess it will, but confirmation would be good.

I would suggest as one possibility creating a point-to-point VPN tunnel between the two servers and using this for the mysql queries from the old to the new server. You will need to make mysqld listen on all interfaces rather than just on localhost, but you could then block all inbound connections from eth0 using IPtables so there is still no access to it from outside, other than through the tunnel.

Might have some latency issues though, hence my question...

---

### Post by rs2k on 2013-02-05
If I do the transfer at night when the traffic is low I think I can live with a slow website over no website for some of our customers. DNS changes seems to happen pretty quickly, usually within a few hours.

---

### Post by tgalati4 on 2013-02-05
Be upfront with your customers.  You will need to plan for downtime and if you are up before the end of the scheduled outage, then you will add to your reliability/credibility.  Trying to perform this switchover without a true live migration will result in some downtime and some services that need tweaking.

Planning is key.  It's the difference between changing a tire on the family car in an hour, versus 5 seconds for an Indy race car.  Fill out a matrix:  Known problems, Known consequences; Known problems, Unknown consequences; Unknown problems, Known consequences; Unknown problems, Unknown consequences.  The last one, *Unk-Unk's* are usually what throws you.

---

### Post by spynappels on 2013-02-05
> **tgalati4 said:**
> Be upfront with your customers.  You will need to plan for downtime and if you are up before the end of the scheduled outage, then you will add to your reliability/credibility.  Trying to perform this switchover without a true live migration will result in some downtime and some services that need tweaking.

Planning is key.  It's the difference between changing a tire on the family car in an hour, versus 5 seconds for an Indy race car.  Fill out a matrix:  Known problems, Known consequences; Known problems, Unknown consequences, Uknown problems, Known consequences; Unknown problems, Unknown consequences.  The last one, *Unk-Unk's* are usually what throws you.

Definitely true, Scheduled downtime is better than unscheduled downtime, and DNS propagation is normally pretty fast. Might be the safest option to do a clean migration during a planned Maintenance Window.

---

### Post by LHammonds on 2013-02-05
Can you get the database running @ the new location and then point the old website to the new database location?  This can be near 0 downtime for a 1/2 switch like that since everything would be immediate and under your direct control.  Then you can bring up the new website with it connected to the new database.  Both websites using the same DB at the same time.  Then update the DNS.  At one point, some people in the world will be using the old web server, others the new web server.  Once DNS is fully propagated and no more users connected to old website, you can then shutdown the old web server.

LHammonds

---

### Post by spynappels on 2013-02-05
> **LHammonds said:**
> Can you get the database running @ the new location and then point the old website to the new database location?  This can be near 0 downtime for a 1/2 switch like that since everything would be immediate and under your direct control.  Then you can bring up the new website with it connected to the new database.  Both websites using the same DB at the same time.  Then update the DNS.  At one point, some people in the world will be using the old web server, others the new web server.  Once DNS is fully propagated and no more users connected to old website, you can then shutdown the old web server.

LHammonds

This is essentially what I was suggesting with my point-to-point VPN tunnel suggestion, although getting the downtime over with at the start of the migration is probably a better idea as all the users migrating to the new web server would no longer be subjected to any latency associated with a remote MySQL query.

This could be achieved within a Maintenance Window of less than an hour using mysqldump on the old server and restoring the DB on the new one and making the changes in the sqlconnect code, assuming the tunnel has been set up previously.

---

### Post by SeijiSensei on 2013-02-05
> **rs2k said:**
> I don't like the idea of having a mysql server open to remote connections, but I don't know of any other way to do it and it will only be open for a few days.

That's easily solved with an iptables rule on the MySQL server. From the command prompt you could enter:

```

/sbin/iptables -I INPUT -p tcp ! -s 127.0.0.0/8 --dport 3306 -j REJECT
/sbin/iptables -I INPUT -p tcp -s ip.of.remote.server --dport 3306 -j ACCEPT

```

The rules appear in reverse order here because I'm using the -I switch to insert these records above any others you may already by using.  When those commands are done, the rules will be in the reverse order at the top of the ruleset.  (If you are adding these to an existing ruleset, reverse their order and use the -A switch.  Put them ahead of any default deny rule you may have at the bottom of the INPUT chain.)

The "! -s 127.0.0.0/8" is only needed if there is not a default ACCEPT rule for localhost above where these rules would be entered.

---

### Post by 1clue on 2013-02-05
Are you using some sort of version control software for your php/css/html?

This sort of situation is one of the more compelling examples of why that sort of thing is needed IMO.  Put your entire site/sites into source control, check it out at your new server, get a recent copy of the mysql database up and going, and then test it before the changeover.

In the end, the final transfer can be what everyone else has already said, but to test it out in advance removes quite a bit of doubt and lowers your blood pressure to boot.

---

### Post by rs2k on 2013-02-05
Version control is not a problem. FTP and a few commands will easily get the site running on a new server. I'm just looking for a way to minimize the confusion the DNS change causes. During the change the DNS likes to swap back and forth between IPs. This causes havoc on a website that uses sessions. The sessions are stored in the database so I think using telling the old server to use the new server for MySQL during the DNS change will work best.

---

