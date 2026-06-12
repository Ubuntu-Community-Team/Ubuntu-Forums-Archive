---
title: "Help with 2 NICS"
date: 2012-02-21
forum: Server Platforms
---

### Post by KenM1575 on 2012-02-21
I setup up a hypervisor with a VM of Ubuntu. It has apache and PHP installed. Everything is working and communicating from the inside fine. I set one nic to internal eth0 (172.xxx.xxx.xxx) and the other to outside eth1 (75.xxx.xxx.xxx). I can also get to the web server on 75.xxx.xxx.xxx from the outside.. Now the problem…
I set up a drupal website and part of drupal has it sending emails from with in the site. Problem is it gets confused which nic to use for its default route. How can I configure Ubuntu to handle the two nics and their default routes.
Thanks
Ken

---

### Post by spynappels on 2012-02-21
> **KenM1575 said:**
> I setup up a hypervisor with a VM of Ubuntu. It has apache and PHP installed. Everything is working and communicating from the inside fine. I set one nic to internal eth0 (172.xxx.xxx.xxx) and the other to outside eth1 (75.xxx.xxx.xxx). I can also get to the web server on 75.xxx.xxx.xxx from the outside.. Now the problem…
I set up a drupal website and part of drupal has it sending emails from with in the site. Problem is it gets confused which nic to use for its default route. How can I configure Ubuntu to handle the two nics and their default routes.
Thanks
Ken

There will only ever be one default route, if you have set up a default route for each NIC, that may cause you issues. Is your mail server in the LAN or are you using an external Mail server?

---

### Post by hawkmage on 2012-02-21
As spynappels said you should only have one default route.  This is a very common issue when you dual/multi homed system.  

I try to avoid multi homing a system if I can, If i do have to have interfaces in multiple subnets I try to make them so all but one so that the interface only has to communicate on its own segment/subnet.  If not you have to get into setting routes to get traffic to go the way you need it to.  

In your case your default route most likely should be to your router on the internet side on eth1 and add a manual rout in the interfaces configuration so that you route all 172.* traffic to your interanl router on the eth0 side of things.  If there are any other internal subnets you will have to add routes for them as well.

---

### Post by KenM1575 on 2012-02-21
> **spynappels said:**
> There will only ever be one default route, if you have set up a default route for each NIC, that may cause you issues. Is your mail server in the LAN or are you using an external Mail server?
 No I'm using gmail.
KenM

---

### Post by spynappels on 2012-02-22
Ok, in that case, are you using the server as a router as well, or only as an internet facing server with a LAN connection as well?

I guess you'd probably want to put the default route on the net facing connection and use the gateway your ISP gave you for your 75.x.x.x IP address.

I would recommend a careful look at your firewall rules as well though if this box is directly Internet facing, and lock down the input side of that interface to only allow incoming connections to port 80 (and 443 if you're using https). All other services should probably be bound to the LAN facing interface as well to help with security.

---

