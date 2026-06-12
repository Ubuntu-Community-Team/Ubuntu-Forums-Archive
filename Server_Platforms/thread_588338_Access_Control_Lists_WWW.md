---
title: "Access Control Lists WWW"
date: 2007-10-23
forum: Server Platforms
---

### Post by knichel on 2007-10-23
I am not sure if this is the correct section to post this, but....
I manage a small network (my classroom) and I used to use a wireless router.  With the router I could set acl's to block internet during a certain time of day to keep the students on task.
Now I use a ubuntu machine with iptables to control access to the internet.  Is there a simple way to turn "off" the internet for the students during certain times of day without having to change  the iptables settings?
Currently I use dansguardian and squid for all outgoing traffic.  If I stop dansguardian then the students cannot get "out", but can still access the webserver in the class.

Thanks in advance for any suggestions you have.
Mike

---

### Post by Dr Small on 2007-10-23
Is this ubuntu machine a server ?
If not, I would get firestarter, and lock the firewall. It stops all incoming and outgoing traffic.

Dr Small

---

### Post by knichel on 2007-10-24
Yes, it is a ubuntu (kubuntu) machine.  I am using webmin to manage my firewall.  I wanted a solution where I can easily turn off the students' access to the web.  

For now, I simply stop dansguardian and that does it.  The students can still get to the in-class resources, but not to the web.

---

