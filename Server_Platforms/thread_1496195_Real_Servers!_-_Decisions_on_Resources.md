---
title: "Real Servers! - Decisions on Resources"
date: 2010-05-29
forum: Server Platforms
---

### Post by Xiuh on 2010-05-29
I got my hands on a couple old servers. An HP tc2021 and a Proliant ML110. Sure they're ancient, but I thought they would make a couple of great Ubuntu Servers for a new "start up" business I'm trying out.

Now I've got to decide the best scenario to distribute the load between the two servers and figured I'd present the question on the forum. I'm going to make an internal domain and will probably be running the following: Kerberos, Samba, Apache, Postfix, mysql, bind, dhcp, SVN, GCC, and Nagios. So in summary, I'll have the following roles; domain controller, web server, file server, and network monitoring services. Anyone have some input on how they would handle splitting these services up between two servers? (I use to run all the above on a P3 test box with 512 memory, what a great upgrade this will be!)

---

### Post by craigp84 on 2010-05-29
For small startups, the key is normally a no cost solution. When they're starting they really don't want to be paying for anything at all - that money's better invested in critical business functions; often advertising. IT Operations comes wayyyy down the list and only really matters once there are a few customers.

So for that reason i normally source 2 or 3 identical boxes, 2nd hand. Thanks to WEEE regulations governing disposal, there is always 2nd hand kit available for free.

Other than verifying the hardware all works, the spare(s) are destined to spend life mostly switched off. Once the primary box is configured at a basic functional system level (inc. security, backup & restore, auditing & logging, monitoring, documented), that configuration needs replicating to a spare box.

Documentation for small businesses normally means putting an A4 refill pad next to the server and writing "logbook" on it. Anyone wants to make a change, they write the date, the time, what they're doing and *why*. Application / services get installed and configured 1 by 1 now.

The number 1 service on the server is the backup and restore functionality. It's the first thing to be installed / setup and it's verified still working on a schedule (daily's often a good rate).

So then you're left with 2 or 3 boxes:

- 1 plugged in (cheaper leccy bills!)
- 1 ready to go (nb: it's used to test restoring your main box's backups every week, make sure the backups are good). The 1 ready to go very quickly IN THE CASE OF CATASTROPHIC FAILURE -- just needs plugged in, the latest backup restored onto it and it's ready.
- 1 (possibly) ready to use as spares

In most cases, you're just going to scavange parts out of box 2 (or 3) and get production back up and running. You can wait for a new part to be delivered for the box that's switched off currently.

I'm only scratching the surface (the not so obvious stuff is why i charge a fee :-) ) but this is enough to get you going with one approach. There are many approaches, go with what makes sense for your particular business. An obvious change is i said IT Ops is a low priority -- that aint true if your business is a web design company!

---

