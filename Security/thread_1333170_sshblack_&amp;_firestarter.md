---
title: "sshblack &amp; firestarter"
date: 2009-11-21
forum: Security
---

### Post by BarryDocks on 2009-11-21
Hi all,
Hope someone might help me:

I would like to configure my server as a gateway and dhcp server so I though I would use Firestarter as is seems straight forward to set up and ticks most boxes.

I am concerned about ssh security and like the idea of blocking IPs after a certain number of failed log-in attempts.  I was thinking of using something like sshblack to administer this for me.

Is it possible (or necessary) to install both ssblack and firestater?

Thanks

PS I intend to use RSA keys rather than password authentication for the ssh server

---

### Post by Yoann Juet on 2009-11-21
> **BarryDocks said:**
> Is it possible (or necessary) to install both ssblack and firestater?

Certainly ; all what you need is a firewall - firestarter or just a little bash script with iptables rules - and another tool to automatically ban ssh brute force/dictionary based attacks - sshblack, fail2ban... -. Another option would be to restrict, through iptables rules, source IPs allowed to ssh in to your server.

---

