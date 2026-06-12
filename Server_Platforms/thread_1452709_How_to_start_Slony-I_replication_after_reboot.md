---
title: "How to start Slony-I replication after reboot"
date: 2010-04-12
forum: Server Platforms
---

### Post by radiognome on 2010-04-12
I have slony-I replication between two Ubuntu servers working fine. I made it with slon_tools.conf and the altperl scripts supplied with the slony1-bin package.

After a reboot, the replication does not start, and I manually have to do a
sudo su postgres -c "slon_start [node#]" on the machines.

When I check /etc/init.d/slony1 I see some commands promising to bring up the node, but I haven't figured out what I have to do to make it work.

I did put the cluster_name and conn_info in slon.conf.
Both slon.conf and slon_tools.conf are in /etc/slony1

Any help would be appreciated. I could of course put my command in the init.d script, but I would like to have a more generic solution.

Thanks, Martin

---

### Post by radiognome on 2010-04-13
I'll answer it myself....

Edit the file /etc/default/slony1

Insert the node-number of the server between the double-quotes.

Only problem still....
slony-watchdog is not being started by /etc/init.d/slony1

---

### Post by radiognome on 2010-04-13
The node-number in the previous post, refers to the node-number given in slon_tools.conf. That is the place to configure everything for your replication.

Adding slon-watchdog on startup:

Alter the file /etc/init.d/slony1

Change the line
                is_running $x || su -c "slon_start --nowatchdog $x >/dev/null" - postgres
to
                is_running $x || su -c "slon_start $x >/dev/null" - postgres

Now the slony-watchdog will also start on server-reboot.

---

### Post by dasun_heenatigala on 2010-04-22
Thanks for answering your own questions :)
It helped me out a lot.

---

