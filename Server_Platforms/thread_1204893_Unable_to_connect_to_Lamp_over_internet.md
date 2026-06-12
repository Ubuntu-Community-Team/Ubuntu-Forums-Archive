---
title: "Unable to connect to Lamp over internet"
date: 2009-07-05
forum: Server Platforms
---

### Post by jclb111181 on 2009-07-05
Hi.  I searched for something similar but nothing seemed to be quite the same.  I set up a Lamp about a year ago.  Never had a lot of traffic, just family looking at pictures.  About a week ago, it quit working.  I can only access through localhost and not from any other computers.  I use no-ip.com to forward traffic to my ip.  I checked to see if my isp was blocking port 80. They are not.  I don't know what could have changed unless there was some update to apache or something else in the last week.  Please help.  Thanks.

---

### Post by Kareeser on 2009-07-05
Your post is a bit vague - it could be any number of problems.

We need you to narrow down the problem through a series of trial and error, with process of elimination.

1. Are you trying to access your website through the no-ip.com address? What happens if you try connecting using the public dynamic IP of the server? If the latter works, then the problem lies with no-ip.com.

2. Did your router reset its port forwarding rules and block public access of port 80?

---

### Post by jclb111181 on 2009-07-06
I am sorry that the post is a bit vague, but I did not have any idea where to start.  

Trying both the no-ip address as well as my computers ip address yields the same results: The server at (ip address) is taking too long to respond.  

Also I have checked the router settings and port 80 is still enabled for http.  

I am at a loss.  It seriously was fine for about a year and then one day, nothing.  Thanks for any help you could provide.

---

### Post by ndxtg on 2009-07-06
> **jclb111181 said:**
> I am sorry that the post is a bit vague, but I did not have any idea where to start.  

Trying both the no-ip address as well as my computers ip address yields the same results: The server at (ip address) is taking too long to respond.  

Also I have checked the router settings and port 80 is still enabled for http.  

I am at a loss.  It seriously was fine for about a year and then one day, nothing.  Thanks for any help you could provide.

same problem from here [http://ubuntuforums.org/showthread.php?t=1205024](http://ubuntuforums.org/showthread.php?t=1205024)

set up your router (Virtual Server part) to point to the right local IP address
and remember to set your local IP static  :KS

---

