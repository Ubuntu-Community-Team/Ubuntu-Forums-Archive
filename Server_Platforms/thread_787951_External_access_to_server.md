---
title: "External access to server?"
date: 2008-05-09
forum: Server Platforms
---

### Post by swisstone on 2008-05-09
I have installed a Ubuntu Lamp server using 6.06 LTS and installed vTiger. I can happily access the vTiger site from LAN and external addresses without any trouble. 

I have in the last week reinstalled the system to use ubuntu server Lamp 8.04 - I have installed vTiger and configured the apache in the same way. 

Problem is I cannot access the vTiger site from external addresses!?! It is working from anywhere on my lan (192.168.*.*) but not across the internet!

I have checked the Port redirection and settings many times. I have used the same fixed IP as before and cannot understand why it is not working? 

Can anyone advise what is causing this behaviour? I have checked the apache and http config files they appear ok. I am also able to re-connect the old server and it still works when I change the port redirect in the router. Are there any other firewall or blocking systems/reasons in the 8.04 distribution?

Any advice greatly accepted!

Many thanks,
Tony

---

### Post by cdenley on 2008-05-09
> 
Are there any other firewall or blocking systems/reasons in the 8.04 distribution?


Not on a default install.
```

sudo iptables -L INPUT

```

No rules should be listed, and it should default to ACCEPT
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

```

---

### Post by swisstone on 2008-05-09
Thank you for the reply.

root@wilcrm:~# iptables -L INPUT

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

root@wilcrm:~#

I don't think this is blocking it?

---

