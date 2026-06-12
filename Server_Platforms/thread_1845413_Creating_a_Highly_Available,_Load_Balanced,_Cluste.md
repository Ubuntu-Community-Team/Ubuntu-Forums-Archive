---
title: "Creating a Highly Available, Load Balanced, Clustered LAMP Setup"
date: 2011-09-17
forum: Server Platforms
---

### Post by tts5 on 2011-09-17
I'm attempting a fairly complicated Linux setup and am wondering if everything looks right. Why not ask the community?

  Here's my proposed layout:

> 
      Server A - Web Server (Primary)
Server B - Web Server (Secondary)
Server C - Database Server (Master)
Server D - Database Server (Slave)
Server E - Load BalancerMultiple web sites are hosted on Server A using name-based Virtual  Hosts in each users' /home/user/public_html directory (e.g.  /home/aaa/public_html, /home/bbb/public_html, etc.). The  directories/files are owned by user:web (a group only for sysadmins) and  permissions of the directories and files are 755 and 664, respectively.  Additionally, the commands "chmod g+s" and "umask 022" are applied to  ensure consistent permissions on subsequent files. Users can SSH to  their /home/user/public_html directory and modify files as needed.

  To implement Load Balancer technology (Servers E/F), a secondary IP  address must be provisioned that is shared between Server A/B. In  addition, Server A's /home directory must always be in sync with Server  B's /home directory. This will be accomplished via rsync over SSH with a  Cron job (using key, not password-based authentication) and the  --delete option (to remove old files on Server B).

Assuming that files on Servers A/B are always kept in sync,  applications that utilize a database will connect to Servers C/D  (master/slave), respectively. To remove the fin
al single point of  failure (SPOF), another Load Balancer should be implemented as outlined  above.

  What are your thoughts? Am I missing anything? Thanks in advance for any help/advice.

---

### Post by zackwasa on 2011-09-17
You can use drbd to sync the partitions between the hosts and heartbeat to do the automatic IP switching, partitions mounting and service starting.

---

### Post by SeijiSensei on 2011-09-17
The most recent [version]("http://www.postgresql.org/about/news.1349") of PostgreSQL, 9.1, has a variety of advanced [replication]("http://www.postgresql.org/docs/9.1/static/warm-standby.html#SYNCHRONOUS-REPLICATION") options that might be helpful here.  That assumes you and your clients aren't attached at the hip to MySQL.

---

