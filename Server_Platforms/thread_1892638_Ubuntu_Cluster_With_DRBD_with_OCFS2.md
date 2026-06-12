---
title: "Ubuntu Cluster With DRBD with OCFS2"
date: 2011-12-08
forum: Server Platforms
---

### Post by steveWag on 2011-12-08
Hello All,

I'm trying to implement a physical (I have the two servers on hand) cluster that is:[INDENT]2 Node
Load Balancing
High Availability
Primary Purposes: Webserver, MySQL server
Secondary Purpose: E-mail server, ftp server
[/INDENT]I've managed to set up basically everything the way I want it to work with Pacemaker/Coronosync, however I'm having a terrible time trying to create a shared disk using OCFS2 and DRBD and making the shared disk dual primary.

I've been trying to use Natty as my Ubuntu version but when that failed, I tried Maverick, and quickly tried Lucid as well.

I've tried the following walk throughs:
[http://wiki.insanityradio.com/wiki/Rivendell_HA](http://wiki.insanityradio.com/wiki/Rivendell_HA)
[https://wiki.ubuntu.com/ClusterStack/LucidTesting#Pacemaker.2C_drbd8_and_OCFS2_or_GFS2](https://wiki.ubuntu.com/ClusterStack/LucidTesting#Pacemaker.2C_drbd8_and_OCFS2_or_GFS2)

As well as combining together numerous other resources like:
[http://www.drbd.org/users-guide-emb/ch-ocfs2.html](http://www.drbd.org/users-guide-emb/ch-ocfs2.html)
[http://www.clusterlabs.org/wiki/Dual_Primary_DRBD_%2B_OCFS2](http://www.clusterlabs.org/wiki/Dual_Primary_DRBD_%2B_OCFS2)


So my question is...
Has anyone actually implemented any of these? Or has anyone tried something else?
Is there any incite that someone can give?

I know there are open projects that are in development for this type of thing, but with these walk throughs and the my lack of ability to find something that says I can't do what I want to do, I assume it is possible. Any help would be appreciated.

Thanks for the help,
Steven

---

