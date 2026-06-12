---
title: "Ubuntu Server no outgoing connections"
date: 2009-05-07
forum: Server Platforms
---

### Post by DevilChild on 2009-05-07
Hi, just wondering if anybody has any idea about this freaky problem I've started having?

Im running Ubuntu Server Edition 8.04.1, using Apache2 webserver with PHP5, MySQL and Webmin.  The server sits in the corner working quietly on its own, and no settings or configurations have been changed for months.

For some reason now though, none of my PHP scripts can perform requests to outside sources.  I mean functions such as file_get_contents fail completely (unless they are to it's own address), and also various get and post request scripts.

I'm reasonably new to linux, so I'm not sure what the problem could be here.  I've checked through the settings in /etc/network/interfaces, and tried rebooting the server, but it didn't help.

The server does work fine on the internet it seems, because others can view the website, and because local network file sharing with my Windows PC works fine.  But anything that requires it to connect to an outside source fails. 

I have tried to use "ping 192.168.0.12" (my router's IP) and that works fine, but it completely fails at "ping google.com".  Also wget doesn't work for downloading files outside of the network.

I can't see any problems with my router settings, network settings or hardware, so any input here would be helpful. I really need this to work for my website.

Sorry for the long post, just wanted to make sure I got everything covered.  Thanks! :)

*edit* The server was working fine till roughly a week ago, and as far as I know nothing has been changed *edit*

---

### Post by antikristian on 2009-05-07
Two things are most likely the culprit here:

**Your dns setting are wrong:** 
Try to ping 74.125.77.103 (google IP, Could be any IP outside your network really.) If this is the case, it will be able to ping this IP

**The computer has the wrong gateway, or there is something wrong with your routes**
If pinging the google IP didn't work, we could look into this.

---

### Post by DevilChild on 2009-05-07
Thanks for the reply

I tried pinging 74.125.77.103, and that works!

So if the network in general is working, maybe its just an apache or php issue?

---

### Post by DevilChild on 2009-05-07
Ok!  I've figured it out.

I was looking through all the different networking files I could find, and eventually found /etc/resolv.conf.  Somehow the "gateway" entry in there had changed to something other than my router.

I changed it back, rebooted, and now everything works as it should :D.

Thanks for the reply antikristian, it was that that got me thinking it was a domain resolving issue.

---

### Post by antikristian on 2009-05-09
Jepp, resolv.conf handles nameservers. So it needs an entry for a nameserver. Most home NAT routers forward dns requests if you set it as the nameserver.

---

