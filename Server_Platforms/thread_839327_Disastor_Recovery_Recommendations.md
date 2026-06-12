---
title: "Disastor Recovery Recommendations"
date: 2008-06-24
forum: Server Platforms
---

### Post by tcpip4lyfe on 2008-06-24
Our IT department was affected by the recent floods in the US and we ended up having to relocate all of our servers and 100 people to a temporary facility.  We didn't have a disaster recovery plan but in the process of removing and moving 20 servers, we didn't lose any data, though we had considerable downtime in the process of moving and transferring over to backup servers. It was a nightmare and was extremely disorganized.  Now the executives are finally concerned about disaster recovery and have decided to throw some money at us for redundant servers and off site hot spares and what not.  I was just curious about other admin's disaster recovery plans.  Do you pay for off site real time replicated servers in a data center? Or do you keep it in house meaning you'd need generator's, UPS's, redundant ISP's on different networks?  I'm leaning for the latter obviously because I want control and instant access to our own equipment.   


Also we don't even have a tap drive (We just Rsync and tar to redundant backup servers) so I was wondering if anyone could recommend a good one for ubuntu.

---

### Post by NetworkGuy on 2008-06-24
My company has a combination of both.

We have a company owned off-site location about 2 hours from the primary location (different power grid).  Within this location is a small datacenter with enough real-time replicated servers to get us back up and running within 30-45 minutes of a failure in the primary location.  This site is continuously growing and more services are being installed all the time.  Different data circuits (same provider), different ISP's.

You will see that setting up rsync properly should do what you need since only the changes are sent to the backup servers.  It helps keep the costs down with the circuit between the datacenters.  I believe looking at your OP that you plan on setting up a second datacenter and not just adding redundancy to the same building.

We also test the backup location once a month (mostly off-hours) and twice a year (for a complete week).  What good is a backup center if you don't know if it will work when you really need it?

---

### Post by tcpip4lyfe on 2008-06-24
Thanks for the reply.  That's basically what we want to do but of course cost is the primary obstacle. I think securing a couple racks in a redundant data center a couple hundred miles away is probably our best bet since we don't even own our on building (we lease) though it's not really what we want to do. Sounds like your company is well established, we're only a couple years old.  What did you guys start out with: Building in house redundancy (redundant server's on redundant power) or off site replication?

---

### Post by NetworkGuy on 2008-06-24
Actually, almost before I started here, we were using an off-site company where we would perform restores of our backups.   Took at least 1-2 days to come back up, also cost an arm and a leg.

I believe having something is better than nothing.

---

### Post by dca on 2008-06-24
I would assume a lot depends on how successful the company is to whether they would host their own in-house disaster recovery or out-source it to a firm specifically designed for that kind of thing...  The funny thing would be if you were able to contract a company to perform this service and their disaster recovery was as non-existent as yours...  I guess due diligence is necessary :-) ...  
 
Some larger enterprises break it down between mission critical servers running Unix, utility servers running this, application servers running that and start from there.  Mission critical servers can be out-sourced to a company specializing in disaster recovery and the lower level servers (some view Email of any type lower level than say a primary billing system or POS) you can set-up in one of the admin(s) garage...

---

