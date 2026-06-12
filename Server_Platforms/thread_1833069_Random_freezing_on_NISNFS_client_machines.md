---
title: "Random freezing on NIS/NFS client machines"
date: 2011-08-25
forum: Server Platforms
---

### Post by MikeDanger on 2011-08-25
We administer a small lab of Ubuntu 11.04 machines. Users authenticate via NIS to the fileserver, which then uses NFS to mount their /home directory.

From time to time, seemingly at random, the machines will lock up. After about 15 minutes, they will go back to normal.

Switching the machine to the console with/ Ctrl+Alt+F1 doesn't help either - credentials get entered, but there's still a 15 minute wait before any commands can be entered. Some error messages show up at this point about processes that were running timing out. However, the root user can log in immediately (which makes us think that this is only affecting NIS accounts).

Logging in with the root account, we can ping our NIS server, and it responds normally. We can restart the networking and NIS daemons but neither of these help.

We checked the NIS error log in /var/yp/ypserv.log and it is empty.

We used to be running a different version of Ubuntu on the client machines (10.04 LTS), but not on the server, and we never had this problem with that configuration.

---

### Post by Wayne_V on 2011-08-25
so is the root user not using an NFS home directory?   If so, it sounds more like an NFS issue.  Check the logs on both the server and clients for issues.

---

### Post by SeijiSensei on 2011-08-25
Try isolating the problem by running a cron job as an active ordinary user that pings the server once a minute.  If that person's machine locks up, you can determine if there's a communication problem between the server and its clients and when it occurs. 

Personally I doubt the problem is connectivity, but it doesn't hurt to rule it out.

How hefty is the server, and particularly, the shared storage?  High speed drives (7.2K at a minimum; 15K better)?  RAID?  (RAID often improves read speeds at the expense of the much less common writes.)  Lots of memory to be used as cache?  

Is it possibly a resource contention problem?  Run top on the server; does it show spikes in load average at particular times?  

Maybe you should go back to 10.04 LTS?  It's "LTS" for exactly reasons like this one.  I'm pretty sure 10.04 used NFSv4, but you can try forcing NFSv3 on both ends and see if it helps.  See "nfsvers" in "man nfs".

One other possible option I can think of is that somehow the clients are losing authentication with the server and need to wait to be re-authenticated.  I can't see how this would happen with NIS, but I'm hardly an expert in these matters!

---

### Post by MikeDanger on 2011-09-15
Thanks for your quick and helpful responses. Unfortunately, we have not yet been able to resolve this issue.

> Try isolating the problem by running a cron job as an active ordinary user that pings the server once a minute. If that person's machine locks up, you can determine if there's a communication problem between the server and its clients and when it occurs. 

Personally I doubt the problem is connectivity, but it doesn't hurt to rule it out.
We did not try this. I don't think this was made clear in my first post, but while the freezing issue occurs, it is possible to switch to a new terminal (with ctrl-alt-F1), log in as root, and ping the NIS server. There seems to be no problem with communication. 


> How hefty is the server, and particularly, the shared storage? High speed drives (7.2K at a minimum; 15K better)? RAID? (RAID often improves read speeds at the expense of the much less common writes.) Lots of memory to be used as cache? 

Is it possibly a resource contention problem? Run top on the server; does it show spikes in load average at particular times?
I am also pretty sure that this is not the problem. The freezing seems to occur randomly with no correlation to the number of users logged in and using resources. Also, we used the same client and server machines last year and had no issues with NIS whatsoever.

> Maybe you should go back to 10.04 LTS? It's "LTS" for exactly reasons like this one. I'm pretty sure 10.04 used NFSv4, but you can try forcing NFSv3 on both ends and see if it helps. See "nfsvers" in "man nfs".
We have taken your suggestion and tried both of these things. Neither seemed to change the behavior in any way.

> One other possible option I can think of is that somehow the clients are losing authentication with the server and need to wait to be re-authenticated. I can't see how this would happen with NIS, but I'm hardly an expert in these matters!
Restarting the NIS daemon on the client machine seems to have no effect on the problem, so I am not sure if this is likely.

It should probably be noted that our NIS server is running Karmic without backports installed. We are wary of upgrading and breaking even more things, but is it possible that this has something to do with our problem? Does anyone have any more ideas?

---

