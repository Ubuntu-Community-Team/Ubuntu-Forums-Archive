---
title: "Munin: no info from other machines"
date: 2010-12-17
forum: Server Platforms
---

### Post by jmehdi on 2010-12-17
I have installed munin on a server and it works locally, I have stats and graphs for the server itself. I have installed munin-node on another machine but no infos are retrieved...

telnet seems works:
$ telnet 192.168.1.1 4949
[...]
# munin node at xeonserver


munin-node.conf on the remote machine (xeonserver):
allow ^192\.168\.1\.29$
host 192.168.1.1
port 4949


munin.conf on the server:
[xeonserver@
    address 192.168.1.1
    use_node_name yes


Any idea what is wrong?

---

### Post by tr333 on 2010-12-17
Have you checked the munin logs in /var/log/munin?
Is there a firewall on the munin-host server blocking any relevant ports for traffic coming in from the remote munin nodes?

I'm new to using munin so it's my only guess on what might be wrong.

---

### Post by jmehdi on 2010-12-18
> **tr333 said:**
> Have you checked the munin logs in /var/log/munin?
Is there a firewall on the munin-host server blocking any relevant ports for traffic coming in from the remote munin nodes?

I'm new to using munin so it's my only guess on what might be wrong.
Found the problem, munin-graph.log told me there was a problem writing to /var/cache/munin/www/xeonserver, so I created this folder, set it to 755 and owner=munin; it works now :D

---

