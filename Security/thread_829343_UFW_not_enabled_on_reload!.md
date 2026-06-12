---
title: "UFW not enabled on reload!"
date: 2008-06-14
forum: Security
---

### Post by RedMartin on 2008-06-14
Despite following the following method to start UFW I find that after rebooting that the firewall is not loaded.

sudo ufw default deny
sudo ufw enable 

What am I doing wrong?

Also, Shields Up! tells me that port 1864 is open. What is this and is it anything to worry about?

---

### Post by Pjotr123 on 2008-06-15
> **RedMartin said:**
> Despite following the following method to start UFW I find that after rebooting that the firewall is not loaded.

sudo ufw default deny
sudo ufw enable 

What am I doing wrong?

Also, Shields Up! tells me that port 1864 is open. What is this and is it anything to worry about?

The first command is unnecessary and maybe the cause of this problem. "sudo ufw enable" is enough.

The open port: possibly your router has an open port in the firmware. The ping port for example. Close it in the configuration of the router.

Open ports are not a problem as long as there are no listening services behind the port. An attacker can't do anything unless there is a listening service:
[http://ubuntutip.googlepages.com/security](http://ubuntutip.googlepages.com/security)

Greeting, Pjotr.

---

### Post by RedMartin on 2008-06-15
Thanks for the reply.

I initially did use just the sudo ufw enable command which didn't make the firewall persistent. Some further reading suggested that setting it to default deny before enabling was the best (safest?) was to start it up.

Is there an easy way to find out if anything is listening behind that port? I'm getting very confused by all the stuff I'm reading.

---

### Post by Pjotr123 on 2008-06-15
> **RedMartin said:**
> Thanks for the reply.

I initially did use just the sudo ufw enable command which didn't make the firewall persistent. Some further reading suggested that setting it to default deny before enabling was the best (safest?) was to start it up.

Is there an easy way to find out if anything is listening behind that port? I'm getting very confused by all the stuff I'm reading.

You have to distinguish between the firewall status of your computer on the one hand, and the firewall status of your router on the other hand. 

If you computer is completely firewalled and your router isn't, Shields Up will still tell you that there are holes. Because the router is the first thing that Shields Up detects.

In the configuration of your router, you can enable it&#347; own firewall and also close the ping port, which is default opened on any router. The firewall status of Ubuntu, you can check by the command "sudo ufw status".

Greeting, Pjotr.

---

