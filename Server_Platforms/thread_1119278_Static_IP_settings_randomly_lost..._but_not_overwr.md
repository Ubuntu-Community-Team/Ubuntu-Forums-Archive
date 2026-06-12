---
title: "Static IP settings randomly lost... but not overwritten"
date: 2009-04-07
forum: Server Platforms
---

### Post by The_Dudester on 2009-04-07
Yo! I wasn't sure whether to post this in the server forum or the networking forum. If it needs to be moved, just let me know.

Anyway, I have an old Dell desktop running Ubuntu Server 8.10, which is hooked via ethernet up to a router (WRT54G v4). I configured it with a static IP and forwarded port 80 so I could host a tiny website for a few friends. Everything was working golden, until...

One day, I tried to access the website. Connection failed. So I attempt to log in with SSH with the assigned static ip, and... nothing. I check out the router's DHCP client table and lo, there's the server, sitting placidly with an assigned DHCP address. I log in with SSH, and look in /etc/network/interfaces, and it still has my static IP settings. Weird. Then I do an /etc/init.d/networking restart, and everything was fine. I thought perhaps it was an isolated incident.

But no, I have found my hope ill-founded. At completely random times, the server has suddenly reverted to DHCP, and I have to do a networking restart to fix it. It hasn't done any restarts. And this week, I'm leaving, so I won't be able to access any other machine except the one that has been forwarded ports, so... if it does this, I'm screwed. My router also does not do static IP "leases". If it comes to it, I guess I could put DD-WRT on it, but that's the last option.


Any ideas from the swarm of knowledgeable users?

---

### Post by cariboo on 2009-04-08
My solution to the problem isn't very elegant, I just uninstalled dhcp3-client, and haven't had a problem since then.

```
sudo apt-get purge dhcp3-client
```

Jim

---

### Post by The_Dudester on 2009-04-08
Thanks for the tip! I just tried it, and I'm hoping that'll fix it.

Thanks again!

---

