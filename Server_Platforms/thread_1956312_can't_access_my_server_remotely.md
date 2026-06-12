---
title: "can't access my server remotely"
date: 2012-04-10
forum: Server Platforms
---

### Post by stunet on 2012-04-10
I installed a virtual server on my computer to add a QA environment, but the issue is I can't access it no matter what I do.

I opened the needed ports and i got incoming set to allow, but nothing works.

any ideas, I'm new to the server version of ubuntu

thanks

---

### Post by arrrghhh on 2012-04-10
Are you accessing it locally or over a WAN?  SSH, Apache, what are you trying to access?

---

### Post by stunet on 2012-04-10
all the above actually

i did a check my IP is 10.0.2.15, which if i enter it remotely just does an endless spin.

---

### Post by stunet on 2012-04-10
its a virtualbox issue, I must have a setting not set correctly.

---

### Post by papibe on 2012-04-10
Hi stunet.

Sometimes it's easier to access a server on a VM if it is on the same network as you are. To do that, change the setting for the VM from NAT to 'Bridge Adapter'.

Just a thought.
Regards.

---

### Post by hawkmage on 2012-04-10
If you are using NAT and have set up port forwarding is the host port being forwarded less than 1025?  On a linux based system I have had issues forwading ports under 1025 since it takes root access to bind to a port below 1025.

---

