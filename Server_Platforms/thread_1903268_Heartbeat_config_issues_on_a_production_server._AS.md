---
title: "Heartbeat config issues on a production server. ASAP help appreciated!"
date: 2012-01-02
forum: Server Platforms
---

### Post by tethlah on 2012-01-02
So I currently have 2 identical servers running a lamp stack with DRBD on them.  I have everything set up with DRBD to accept node1 and node2 properly.  Right now I have (internally) 10.10.1.51 working fine over http when I hit it, I then do this:

On node1 (10.10.1.51):
-Stop apache2 services
-Umount drbd0 from the data mount point (where the lamp stack resides)
-Switch drbd to secondary.
-Check [http://10.10.1.51](http://10.10.1.51) and the site is down.

On node2 (10.10.1.52):
-Switch drbd to primary.
-Mount drbd0 to data mount point (where lamp stack is)
-Start apache2 services
-Check [http://10.10.1.52](http://10.10.1.52) and the site is up with the changes I made on node1.

I go through this process the opposite direction making a change on node2 and everything replicates fine to node1 when I check the website.

Now I have heartbeat installed and am trying to get things working on the new virtual IP 10.10.1.50.  When I run heartbeat I can see 10.10.1.50 and 51 when I have node1 primary.  I pull the power on node1 and node2 does not take over.  If I manually switch node2 to primary and keep heartbeat running on node2 with node1 powered off I can hit 10.10.1.52 but 50 doesn't work...I'm banging my head against the wall here.  Here are my configs, see anything wrong?

Ubuntu version: 10.04.3 LTS
I just installed both drbd and heartbeat, so it should be all updated.

/etc/ha.d/authkeys:
```
auth3
3 md5 mypassword
```

/etc/ha.d/ha.cf:
```
logfacility     local0
keepalive 2
deadtime 20
warntime 10
initdead 120
bcast bond0    #external network (internet)
bcast bond1    #internal network (directly between nodes)
node ein       #name of node1
node ed        #name of node2
```

/etc/ha.d/haresources
```
ein IPaddr::10.10.1.50/24/bond0 drbddisk::lamp Filesystem::/dev/drbd0::/srv/data::etc4 mysql apache2
```

Anyone know what I'm doing wrong here?  It all works when I switch manually, (except heartbeat doesn't broadcast the vip when on node2), but when I shut down node1 it all falls apart.  I thought I set this up correctly according to every resource I can find, any suggestions?  I know I'm on here asking for help, but this is a production environment and I need to find a solution (we currently have no automated redundancy) asap if possible.

Thanks guys.

---

### Post by tethlah on 2012-01-02
If there is any other configs you need to see, feel free to ask, only other thing I can think of is the drbd.conf, but I've established that is working manually.

On a side note, I copied this exact server set-up on two machines at home and removed DRBD and Heartbeat.  I downloaded LCMC and used it to load DRBD, Heartbeat, and Pacemaker on my clones, went through it's install and I'm still having the same problem.  Everything works until it's Heartbeat's turn to do it's job.  I'm positive that there is something wrong with my haresources file but I just can't peg it.

---

### Post by tethlah on 2012-01-03
Is there anyone on these forums familiar with heartbeat?  I've combed every resource I can find and I'm missing what wrong with my config.  I'm still looking, but I'm really hoping someone here is familiar with what I'm doing or at least familiar with Heartbeat to point out something I'm missing.  At this point I'm loosing money.  Any help would be appreciated.

---

### Post by tethlah on 2012-01-05
Is there no one that knows anything about Heartbeat on these forums?  I've lost 4 clients now and still can't find an answer anywhere....

---

