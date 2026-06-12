---
title: "Master Repository For Multiple Synced Nodes"
date: 2011-05-08
forum: Server Platforms
---

### Post by speedrcj on 2011-05-08
I am currently looking for a solution involving keeping data synced across multiple nodes.  It's for a planetarium and the problem is thus:

We have two display systems each with 1 master control and 6 nodes that are rendering data in real time.  Therefore we've got 12 render nodes, and 2 master computers that need to have the same information on them at all times.  The data can be edited on either of the master nodes, or in offline production systems.  


These are all windows machines, and I currently use Ubuntu server to rsync a portion of the data every 5 min since there's a good amount, and I use svn for part of it that gets modified often.  I don't want people to be able to overwrite someone elses work, and I want to be able to push updates out when data is updated.  Anyone got a good idea for this one?  

Thanks for your time!

---

