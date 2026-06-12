---
title: "ufw and outgoing traffic"
date: 2008-05-05
forum: Security
---

### Post by ngmachado on 2008-05-05
Hi, 

I'm self-learning server administration so I installed Ubuntu 8.04 LTS in a VPS.

Since I'm very concerned with security I intalled ufw (uncomplicated firewall).

Then I created the following rule:

```
sudo ufw allow proto tcp from xxx.xxx.0.0/16 to any port yy
```

where yy is my changed ssh port and xxx.xxx is the beginning of my ISP IPs address. Fine!

I installed Apache2 and I had to define:

```
sudo ufw allow www
```

in order to visit my websites. Fine!

Finally I installed Postfix... and I'm able to send emails without creating any rule. It seems that ufw is not filtering outgoing traffic, only incoming. Is it normal? Should this be a concern?

---

### Post by Monicker on 2008-05-05
Normall you wouldn't filter outbound traffic on a workstation or server, because its usually trusted.  

Now for a gateway to the internet, for example, I definitely would filter outbound traffic; only allow outbound to 25 from the mail server, to web sites from the proxy server, etc.  Egress filtering is a good thing.

---

