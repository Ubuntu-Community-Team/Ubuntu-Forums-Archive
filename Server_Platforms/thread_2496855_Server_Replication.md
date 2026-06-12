---
title: "Server Replication"
date: 2024-04-15
forum: Server Platforms
---

### Post by didier1981 on 2024-04-15
Hello everyone,

first time on this forum.

we have installed Ubuntu 22.04 on our 2 server and we are looking for a replication solution ( we used Carbonite before but it is no longer supported) in order to maintain an active replica of the main server.

any suggestion on a solution that would replace Carbonite?

thank you for you help

---

### Post by MAFoElffen on 2024-04-15
When you say "replication", please explain your context further.

When I think "replication", I think databases and data, here you sync data between multiple locations, whether local or remote. When I hear server replcation my head goes to Server Failover Clusters.

But "Carbonite" is a backup solution. It doesn't fall into my understanding of replication. You say they are no longer supported? I thought that Carbonite Safe Server Backup v6.8s last update was May 22. Hmmmm. 

Here is a "Top 5 Server Backup Solutions" for 2024, which Carbonite came in 3rd: [https://www.cloudwards.net/best-server-backup-solutions/](https://www.cloudwards.net/best-server-backup-solutions/)

---

### Post by TheFu on 2024-04-15
Replication has many different meanings and many different solutions depending on the goal.  
Is this an active-active, active-failover, or active-standby situation?
What sorts of things need to be replicated?  text files? Documents? DBMSs?  
If a DBMS, are you using block replication/mirroring like ClusterFS or DBRD or would using the build-in replication be a better answer like Postgres supports?  Or would replaying DB logs work for slightly delayed replication?

What are the main goals?  How much downtime for the service are allowed?  Are you seeking true HA or just a quick recovery?

BTW, the type of application can make each of these things easier or harder.  If the clients to the server(s) are using CORBA, things are harder than if they are simple VIP with a floating IP between the servers.  If there are multiple front-end webservers, then the users may not need to know about any back-end server issues at all?

Are these servers in VMs?  VM failover tends to be easier than physical failover.

Anyway, there are lots of details that haven't been provided.

I've never used Carbonite. Don't know what it is good for. Some companies like to pay for things that don't need to be paid for. That's fine too.

---

### Post by stephan4 on 2024-08-27
What use-case???

Replication has many use-cases like Databases, file systems and simple file transfers.

---

### Post by TheFu on 2024-08-27
> **stephan4 said:**
> What use-case???

Replication has many use-cases like Databases, file systems and simple file transfers.

Dude, you've been necroposting all day.  If a thread is over about 3  weeks only, the OP is likely gone and no longer watching.
OTOH, thanks for pointing out a few threads I need to unsubscribe from to avoid necroposts.

---

### Post by stephan4 on 2024-08-29
Indeed, I have not seen that. Just used the "unanswered" filter.

Please don't attack me for reacting to an open question.

Dead posts should be "closed" ... and it's such a shame if people don't come back to their "questions".

---

