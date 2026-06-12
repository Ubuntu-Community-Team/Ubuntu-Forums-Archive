---
title: "Load Balancing"
date: 2013-02-07
forum: Server Platforms
---

### Post by sandshakimi on 2013-02-07
I'm seeking a step-by-step guide to installing load balancing on our Ubuntu Server ver. 12

This is for hosting future public facing Drupal websites.

I envision (2) front end Web Servers, and (1) database server (serving both web servers).

If Web Server "A" gets compromised, I want Web Server "B" to kick in, or vice-versa.

I don't have a lot of Linux experience, so I'm looking for something easy to configure and setup.

(The web server has Ubuntu Server, Apache2, PHP)

---

### Post by tgalati4 on 2013-02-07
Are these 3 physically separate machines?  Or are you thinking of one bare-metal server with 3 virtual machines?  I'm not sure it is possible to run 2 separate instances of Drupal with one (mysql?) database.  I can conceive of "snapshotting" Server A to Server B every so often (once a Day, once every 4 hours) then using an iptable rule to route traffic from ServerA to ServerB when ServerA goes down or needs maintanence.

You would need to provide a lot more detail:

What version of Drupal?
What database?
What is the physical hardware?

How much downtime can you afford during the switchover?

I would set up a physical server and a cloud-based server and set up provisions for snapshotting and/or live migration.  That way you have off-site redundancy.  Does the expected load on this site really demand 2 servers for load balancing?

---

### Post by Cheesemill on 2013-02-07
What you are describing sounds like HA (high availability) rather than load balancing.

With HA you have the situation described where if your main server goes down the backup server immediately takes over. With load balancing both servers are live at the same time and requests are shared between them.

Both of these are very involved subjects, way beyond the scope of a few paragraphs on a forum. For an intro to the basics Linode have some good how-to's on their site...

[http://library.linode.com/linux-ha](http://library.linode.com/linux-ha)

---

### Post by Habitual on 2013-02-08
> **sandshakimi said:**
> 
If Web Server "A" gets compromised, I want Web Server "B" to kick in, or vice-versa.How would A know B was "hacked"?

HA or Load Balancing anything can not answer that Q.

---

