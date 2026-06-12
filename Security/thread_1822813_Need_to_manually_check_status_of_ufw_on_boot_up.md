---
title: "Need to manually check status of ufw on boot up?"
date: 2011-08-11
forum: Security
---

### Post by jsvidyad on 2011-08-11
Hello,

  I have a question regarding ufw. 
  
Before using ufw, I was using firestarter to set up the firewall rules. While using it, I was told that it is just an interface to set up the iptables rules and that the firewall would be running automatically at boot without any manual intervention. But, once I just checked my firewall and found that there were no iptables rules set and I wasn't protected by a firewall. After that, I would always log into the administrative account first, run firestarter, make sure that it was active(there is an icon which shows that) and also check the iptables rules. 

I decided to move from firestarter to ufw since firestarter does not set up filter rules for ipv6.

Now, when we first enable ufw, we get a message saying that the firewall was enabled and would be automatically enabled at boot time. How dependable is this piece of information? As of right now, I always first log into the administrative account, run the command "sudo ufw status verbose" and make sure that the firewall is actually active. It has been active every time I checked(for a desktop). Now, is it necessary to do this? How about cases where network connections are set up only when you log into an user account(such as when you connect to a wireless network using a laptop)? In that case, will ufw automatically adapt the rules to that new network connection or is any manual intervention or status checking required?

Thanks in advance for your help.

---

### Post by bodhi.zazen on 2011-08-11
Firestarter and ufw conflict with eachother, so, you need to purge(not remove) firestarter.

when you apt-get remove firestarter, all the config files are left in place

when you apt-get purge firestarter, the config files are removed as well.

What and how do you want to check your firewall ?

You can run 

```
sudo iptables -L -v -n
```

[http://manpages.ubuntu.com/manpages/lucid/man8/apt-get.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/apt-get.8.html)

[quote] purge
           purge is identical to remove except that packages are removed and purged (any configuration files are deleted too).[quote]

---

