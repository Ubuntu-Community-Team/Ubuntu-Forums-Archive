---
title: "Apache Virtual Server Configuration with internal router"
date: 2008-11-20
forum: Server Platforms
---

### Post by notlistening on 2008-11-20
Hi Guys,


I have two problems at the moment with the way that my web server/network is configured.

Currently i have a Wifi router that is configured to display it configuration page through its internal web server on port 80. This is great until I try to view my website in my network and I get the login page for my router. This happens when i use the external public ip address. 

Hold on you say use the internal address I can do that but have two websites on the same machine and can only access the one website when i am using the internal IP address the other website is the second. How can i configure apache / my network to allow me to see both website when connecting inside my network?

One solution i have found to work is using an external proxy server to route my traffic out and then back into my network again but i can not find a reliable one, if anyone knows of any I would appreciate that as it is a easy solution. 
----
Secondly I have two address configured in apache as virtyal hosts the first is [http://mywebsite.com](http://mywebsite.com) which works as [http://www.mywebsite.com](http://www.mywebsite.com) and a second [http://website2.info](http://website2.info) when i use the www. infront it directs me to the correct website but if i miss the www off the front of website 2 so like [http://website2.info](http://website2.info) it direct me to [http://mywebsite.com](http://mywebsite.com) I am sure it is a configuration on apache but not sure how to modify it.

Thanks in advance 

Tom

---

### Post by MJN on 2008-11-20
The logical solution to me would be to see if your router can listen on a port other than 80 - can it?
 
For your second query you need to ensure that Apache knows all the variations of names that each virtual host is to respond to. You presumably already have a ServerName directive for each site (set to www.<domain>) and so you now need to add a ServerAlias directive set to just <domain>.
 
Mathew

---

### Post by notlistening on 2008-11-20
Thanks Mathew,

I will try the new server directive. The router can not be set to another port. Nice 1 Netgear. 

Tom

---

### Post by threetimes on 2008-11-20
If you can't run your server on port 80, run it on port 81 for ([www.)mywebsite.com](www.)mywebsite.com) and 82 for ([www.)website2.info](www.)website2.info) and use a proxy outside of your network (I can do this, PM me) to forward the traffic to your server.

---

### Post by notlistening on 2008-11-20
Ah a solution in an update, how novel. 

In trying out an update to my router i have managed to fix the problem. Moving up from version 2.xx to version 3.xx of the firmware the router now knows i am not trying to access the administration page and passes the request onto the web server and now i can see both pages when requesting them.

For completeness the router is the Netgear DG834G v2. 

Thank you for the offer to use your proxy that was very nice.

This problem is now solved.

---

