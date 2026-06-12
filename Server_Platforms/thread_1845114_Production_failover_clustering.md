---
title: "Production failover clustering"
date: 2011-09-16
forum: Server Platforms
---

### Post by Servious on 2011-09-16
I need a solution to provide an active fail-over for a single LAMP server. It needs to actively share all the same data with MINIMUM amount of possible loss due to fail. It also needs to have the same hostname and/or IP address so that if the first box fails everything else that interacts with that box can switch to the second box without anyone noticing.

The Boxes:
Dell 850 3.2Ghz Dual Cores with 4GB of memory
2 x 140Gb SSD's software Raid 1 with a swap partition and main partition.

Both boxes are the same.

They're running ubuntu 10.04 LTS

One of the boxes is fully configured and set-up as a production box. It has the IP it needs it has apache2, php, mySQL, and everything else configured to how we'll need it in the production environment.

Box 2 is a blank slate at the moment.

What can I use to replicate box 2 into an exact clone of box one, keep it up to date by the second and in case of box one's failure switch to box 2 seamlessly. 

I've looked at DRBD and that seems to be EXACTLY what I'm looking for but all the guides on setting it up seem to deal with partitions that are not created or populated with data. This box already exists and can't be rebuilt easily.

Does anyone out there in the community have any solutions?

Thank you.

---

### Post by gombadi on 2011-09-16
I think the first thing to do is manage expectations -

> 
It also needs to have the same hostname and/or IP address so that if the first box fails everything else that interacts with that box can switch to the second box without anyone noticing.

and

 keep it up to date by the second and in case of box one's failure switch to box 2 seamlessly.
 

You will find it very difficult to reach this level of failover. Someone will always notice. Take for example the case that someone removes the power cord from server 1 while it is in the middle of processing some php code and waiting for mysql to update the database. To get server 2 to pickup in the middle of that that and carry on so no one notices is very hard.

As far as I know, and what I have done with our production systems, is to use a combination of things, A third floating ip address, drbd to replicate some of the partitions between the servers, MySQL replication to copy the database between the servers and heartbeat to handle the switch over.

I take it you mean that server 1 is already setup and therefore you can't add things like drbd to it. If that is the case and server 2 is blank then I suggest you install server 2 the same as server 1 but with drbd in a standalone mode. With it the same then take some downtime and transfer the active site over to server 2. After this you can rebuild server 1 with drbd and then add it to server 2 as the standby machine. Then setup Mysql replication from server 2 to server 1, configure heartbeat between the systems and you should be all go. You can of course fail over to server 1 as the active machine if you want.

Hope this helps.

---

### Post by Servious on 2011-09-26
I can't seem to think of a good way to get the data i need synced onto a empty partition that can be copied easily with DRBD.

What I might end up doing is just running cron jobs every 10min to sync the home directories and then use mySQL replication.

Set up heartbeat to float an IP between the two servers.

The only thing this leaves me without, that I would still need, is a way to keep config files, updates, and loaded applications in sync between the servers.

It would be quite a hassle to manually update the config files on both server's to match every time i want to make a change  and keeping the exact same updates and revisions of things on both servers.

Any suggestions?

---

