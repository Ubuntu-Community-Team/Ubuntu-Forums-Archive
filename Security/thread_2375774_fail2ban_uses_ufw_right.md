---
title: "fail2ban uses ufw right?"
date: 2017-10-27
forum: Security
---

### Post by calby on 2017-10-27
Hi,
I'm wondering if fail2ban are using ufw to block/ban IP's?
If so, how can I see in the ufw if a IP is banned?

I did unban a ip troug the command: sudo fail2ban-client set nginx-dos unbanip 192.168.234.1 
But I'm not sure if it worked or not?

And yeah, it did ban my gateway, that's not good I know that, but I don't really know why my gateway did spam my nginx server, but my quastion is - how can I see if the IP are still banned in the UFW?

---

### Post by Doug S on 2017-10-27
fail2ban uses iptables, which ufw uses also. You can observe your current iptables rule set, along with packet and byte counts, with this command:
```
sudo iptables -v -x -n -L
```

---

