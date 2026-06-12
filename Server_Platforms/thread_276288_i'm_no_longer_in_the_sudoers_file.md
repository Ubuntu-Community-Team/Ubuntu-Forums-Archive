---
title: "i'm no longer in the sudoers file"
date: 2006-10-12
forum: Server Platforms
---

### Post by Curtis_B on 2006-10-12
I recently setup a intranet server, I am somewhat new to the command line environment but I feel pretty confident in my actions. 

Anyway, I've had my ftp / www / php / mysql all running without any major incident for a few weeks straight at this point. Today I clicked my kvm switch over to the server and wanted to run some sudo commands, now it's telling me that my user is not in the sudoers file. I don't understand how it could have lost me, I've run plenty of sudo commands up to this point, all under the same user. 

On the router level / firewall no ports are forwarded to the server, I didn't want it exposed to the net at all. 

Any ideas?

Thanks

Curt

---

### Post by aysiu on 2006-10-12
I don't know how it got lost either, but if you can afford a quick reboot, this might help:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

