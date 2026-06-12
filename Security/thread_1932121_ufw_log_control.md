---
title: "ufw log control"
date: 2012-02-26
forum: Security
---

### Post by spezticle on 2012-02-26
so i'm using UFW and i have logging enabled, but i want to control the logging setup.

i know i can grep or less or use other methods to display and filter through a log but if there is another way, i'd rather do that.

essentially, i want to have any connection on port 'x' unlogged.
or any source ip matching 'y' unlogged.

things of this nature.
where might i edit a configuration for this sort of editing, or would i be better off just using a fuller featureset firewall such as shorewall for example?

Thanks in advance,

---

### Post by kevdog on 2012-02-27
I'm no expert in ufw since I never used this, however I know this could be done using iptables directly -- meaning the packet would be simply be dropped without logging it.

---

### Post by SparTacux on 2012-02-28
There's a special UFW configuration file called 20-ufw.conf that can be found in /etc/rsyslog.d/ that you can edit for finer control of UFW audit data.  Check out my creating a web browser logger link on how to configure it

---

