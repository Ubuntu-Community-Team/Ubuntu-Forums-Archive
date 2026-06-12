---
title: "Server failover strategy"
date: 2012-07-08
forum: Server Platforms
---

### Post by cbianchi on 2012-07-08
Dear list,

I wonder if I can get some strategic advice from your experience.

We host the websites (PHP/MySQL) of some of our customers on one Ubuntu server, co-located. The server is backed up and has a RAID 1 redundancy - but if anything goes wrong, there is no real-time backup solution to get the websites up and running in a matter of minutes.

My idea to enhance this would be to have two servers in place, in different co-location facilities, which are synced in real time. One of them may be always in use (master) and the second only used when/should the first one fail (network, hardware, etc). Whan need synchronising (for each user account/website) is:

- The MySQL databases
- The media assets (images and video)
- The codebase

Ideally you also want to keep the OS and applications in sync.

Is this a good idea and solution? If it is, my next question would be how do you go about implementing it.

1. Is the CLOUD/MAAS/JUJU infrastructure something that can be used?
2. Or more something like GlusterFS + MySQL replication?
3. Or a simple series of rsync cron jobs between the two machines?

I struggle (as you can see!) with the idea of a private cloud - as I am not sure it is what I am looking for. Which is a fairly basic failover solution!

I hope you can point me in the right (and possibly detailed) direction.

With infinite gratitude,
Cristiano/Keepthinking

---

### Post by spynappels on 2012-07-08
It may be useful to know if the sites you host are relatively normal dynamic sites or rapidly changing ones using some form of CMS (Drupal, Wordpress etc)?

As I see it, there are 2 separate systems required here:
[LIST=1]
[*]Loadbalancer to steer traffic one way or another
[*]A Sync method
[/LIST]
For the loadbalancer system, some DNS providers provide a form of this, but the most reliable method is a third server acting as a loadbalancer, healthchecking both content servers and using the Active one until it senses a failure, after which it sends traffic to the other content server, previously the standby server. Do a Google for Apache High Avaliability and Loadbalancing, there are many good how-tos on this subject.

For keeping the content in sync you can use a cronjob which uses rsync to copy content to the standby server at regular intervals. The difficulty will be with the MySQL database data. You will probably need to dump the database immediately before the rsync copy, and restore the dumped DB on the standby server straight after.

---

### Post by Cheesemill on 2012-07-08
Check out the Linode library, it's a great place to start:[]("https://library.linode.com/linux-ha")
[https://library.linode.com/linux-ha/ip-failover-heartbeat-pacemaker-drbd-mysql-ubuntu-10.04](https://library.linode.com/linux-ha/ip-failover-heartbeat-pacemaker-drbd-mysql-ubuntu-10.04)

---

### Post by Cheesehead on 2012-07-08
My failover server uses a fairly simple script:
It uses a heartbeat monitor to test that the primary system is working.
Upon heartbeat failure:
 - It sends an alarm to a human.
 - It sends a command to the router to change the server's IP traffic forwarding to the failover.  Online connections are severed by this process, and must be restarted, but that's okay for my connections.
 - It changes runlevels, reconfiguring itself as the active server, no longer backing up from the primary, and taking over forwarded IP traffic.

There may be simpler systems, but mine works great for what I need - failover and alert.

---

### Post by cbianchi on 2012-07-08
Dear all, thank you for the replies so far. My thoughts:

@spynappels
The sites change all the time, they are CMS driven. Your strategy, which is fairly low-tech and manually driven, is a good one and you may use MySQL replication for mysql. The issue is by adding a load balancer you add another component, which may also fail - hence you possibly need two of them, monitoring one another.

@Cheesemill
I did look at Linode, but I prefer GlusterFS, which is a similar concept - or so it seems to me. But it does not solve database replication, or does it? What I did like about GlusterFS is the fact that it lets you use a folder (with you may configure to be /home) among as many nodes as you like. I guess Linode can do the same.

@Cheesehead
That's fine for monitoring the system and do the switch. But how do you keep the two servers in sync with one another?

Again, thank you for the time taken to reply. I am puzzled at what is the Ubuntu Private Cloud for...? Not for something like this?

Best, Cristiano

---

### Post by Cheesemill on 2012-07-08
The Linode guide that I linked to earlier uses DRBL to sync the filesystems across the machines. One of the locations that it replicates is /var/lib/mysql which effectively syncs the MySQL database.

You don't need to be using Linode to host your VPS machines, it's just a great source of information.

---

### Post by SeijiSensei on 2012-07-08
You might want to browse the "[high availability](http://www.linux-ha.org/wiki/Main_Page)" options in Linux as well.  I suspect Cheesehead's "heartbeat" monitor is part of the HA suite of applications.

---

