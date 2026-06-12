---
title: "Question about clustering, suggestions wanted!"
date: 2008-04-28
forum: Server Platforms
---

### Post by squirrley5 on 2008-04-28
Hi all,
I've looked around and haven't seen this kind of question asked anywhere, unfortunately. Let me preface this all by saying that I'm relatively new to linux/debian; I have been using it off and on (mostly off) since 1999, but infrequently enough that I often forget commands. I have done some installations from source, but much prefer apt-get install. :)

Now, on to the question. I recently inherited the server administration and network engineering for a company when their previous guru left. I've worked a lot with LAMP before, but never email. I'm quite out of my element. All I know for sure is that if things remain the way they are, they'll go down in a hurry, and I'll be blamed. Let me back up a tad.

I work with a moderately-sized Wireless ISP in Illinois and Indiana, a couple hours south of Chicago. We have about 1000 customers. There are two networks: the Indiana network operating on 3xT1 connections, and the Illinois networking operating on a 10Mbps partial fiber link bounced to our first tower wirelessly by our ISP. Currently, our single email server is sitting next to the T1 router over in Indiana, not benefiting from all the bandwidth we have here in IL. Of course, I keep getting told that in "a few weeks" the field technician will connect the two networks, and we'll be able to use our internal backhaul (which runs fairly consistenly about 8Mbps - 10Mbps from any location to any other) for all inter-server communication.

Since taking over, I've been able to consolidate and better organize things so that I have 4 "spare" servers sitting here next to my left leg. I also have a server currently running Freeradius and MySQL for auth down at the IL "first hop", and two servers over in the main Indiana POP: one running qmail, vqAdmin, and also our websites. The other is our in-house nameserver and will temporarily cache emails should the main email server go down, if I understand correctly. So altogether, I have 7 servers to work with, the most powerful of which are 2 dual-core Dell PowerEdge servers in the 1.8Ghz range with 1GB RAM and 500GB HDD, and the less powerful likely being somewhere around 1Ghz single-core w/ 512MB of RAM and 40GB Hard Drives. By the way, there's no backup system in place. All we have is a copy of the MySQL authentication / customer database that I made about a month ago and have stored in .sql format on my laptop.

My current train of thought is that I'd like to set up a cluster with 2 controllers (one main, one using heartbeat to become live if necessary), 2 for NFS to host the data (probably one in IN and one in IL, and again one main and one backup with heartbeat), and 3 for actual LAMP, DNS, and Email service (using mounted NFS shares). My reasoning is that this would probably provide the best overall redundancy and speed. Remember, this is an ISP, so if something goes down, there needs to be a backup that takes over **immediately**.

Now, first, I'd like opinions on this setup. If you were in charge of this mess, and had two company websites as well as about 10 customers' websites, in addition to needing to have MySQL database for authentication, plus having FreeRadius, DNS, and email... and had those particular computers to work with... how would you set it up?

Second, since the current email server has been choking and seems to be giving its death rattle, my supervisors have made it a priority to "get a new email program". If I need to stick with qmail, that's fine. But I do want to move away from RedHat / Fedora, and use Ubuntu exclusively. If I switch from qmail to letting ubuntu set it up for me from the server setup cd, how can I migrate all my settings and emails from the old server to the new one(s) without more than a few hours' downtime (to be done late one night when nobody's likely to be awake)? Of course, I would make a complete backup of the drive before I started just in case the whole thing chokes.


Thanks for any and all help,
Sam

---

### Post by theDaveTheRave on 2009-04-06
Sam

I notice that you have had no responses from this thread.

However I also get the impression you are probably savy enough to have organised a system setup by this time.

so I am hoping that you may be able to assist me with my queries.

Currently this is only small scale, but I hope to get something in place that will be able to "expand" relatively easily.

I going to start another thread with my questions, I will do this shorly, but for now very briefly here is my current desire for my completed setup.

3 servers running;
2 on my laptop, (one to "test and break"), the other (once i get things right) to have "stable".

This second "stable" version should then auto back up to both the "testing" version (on the laptop) and the 3rd instance on the "Desktop".

I would like to be able to gain access to the data on any of the 3 servers directly at any point in time (and at the same time).


Thanks for your time

David

---

