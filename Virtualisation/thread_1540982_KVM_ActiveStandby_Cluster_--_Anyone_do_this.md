---
title: "KVM Active/Standby Cluster -- Anyone do this?"
date: 2010-07-28
forum: Virtualisation
---

### Post by bxcrx on 2010-07-28
I'm looking around all over the internet for information on a very vanilla HA solution using ubuntu 10.04 Server and thus far I've read about heartbeat/pacemaker being a solution for what I'm looking to accomplish. 

Nothing seems too concrete out there though. 

E.G.

I have two servers 

vmserver01
vmserver02 

They are both using shared storage via ISCSI

I can migrate the VM's hosted on vmserver01 to vmserver02 and vice versa with no problems.

I'm looking for clustering software that would detect failure if vmserver01 goes down, and then fail over the VM's to vmserver02.

Thanks

---

### Post by TheFu on 2010-07-28
There are many ways to accomplish this without concern for virtualization. You aren't gonna find "vMotion" with KVM at this point.  The best type of clustering will be highly dependent on the specific applications running on the systems, whether any parts can be active/active or if there is a DBMS involved that may need specialized storage configs for cluster support.  I believe KVM has a way to migrate a running server to another server, but I understand that is more for migration, not for fail-over.

Honestly, I'd start with [FONT=Arial, Helvetica, sans-serif][SIZE=2][COLOR=#008000]www.howtoforge.com.[/COLOR][/SIZE][/FONT]

---

