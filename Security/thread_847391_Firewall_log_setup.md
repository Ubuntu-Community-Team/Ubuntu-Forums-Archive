---
title: "Firewall log setup"
date: 2008-07-02
forum: Security
---

### Post by craigjw on 2008-07-02
Hi all,

I'm new to Linux but not to Firewalls - I have Ubuntu Server installed and Iptables configured using FWBuilder. Now, my major issue, what can I use to view the logs in a easy-to-use manner? I'd like to use a Windows (preferably) or a Linux system to run a log viewing program.

Any thoughts or instructions on how to go about this?

Thanks
Craig

---

### Post by prshah on 2008-07-02
> **craigjw said:**
> 

 what can I use to view the logs in a easy-to-use manner? 


All logs are stored in the "/var/log" directory (folder). You can use the linux command "vi" to view them, or if you prefer Windows, you can share the "/var/log" directory, then connect from a Windows box and view the logs.

---

