---
title: "Home server with single IP"
date: 2012-09-07
forum: Server Platforms
---

### Post by Ortix on 2012-09-07
I have been searching about this topic for over a week now and I can't seem to find any solid answers. They are all very vague.

So my question is this. I want to run a webserver with a single static IP. How do I configure my DNS settings in order for this to work? Is it even possible at all and if not what are some alternatives? I am running openpanel and I want to run multiple sites on it.

On my rented servers I always had two IP's and i'd just create two A records with ns1 and ns2 as value for the master domain and then just point the two IP's in godaddy to the nameservers.

How would i go about doing this on my home server?

Thanks!

---

### Post by kennethconn on 2012-09-07
[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)
 
This is typically required for home server set up, don't forget to port forward on your router. Obviously, make sure it's working properly from LAN side before trying to access it externally.
 
Sorry, just noticed static in your post - my mistake.

---

### Post by lisati on 2012-09-07
I'm assuming that you have a domain name organized with a provider somewhere, e.g. no-ip or dyndns. Here's a somewhat shortened version of what I think needs to happen.

You should have access to a control panel which lets you direct your domain name to a particular public IP address. 

With no-ip.com, you can click on ["Manage my hosts"]("https://www.no-ip.com/members/dns/") then on "modify" for the particular domain name. Dyndns has theirs [here]("https://account.dyn.com/dns/dyndns/"). Other providers have different arrangements for what you can do and where. Unless you're feeling brave, I'd suggest leaving any nameserver setup alone for now, and just concentrate on the main domain names that you manage.

On your router, you'll need to organise port forwarding (or similar) so that incoming requests to view your website(s) can be directed to the correct machine on your network.

I have no experience with openpanel, but would suggest looking at its "virtual host" options. Looking at the screenshots on their website, I think that the "doamin" tab might be one place to start. I usually manually edit apache's "sites-available" files through the command line.

Hope this helps get you started.

---

### Post by SeijiSensei on 2012-09-07
Quick answer is to point all the various sites to the same IP address and use [name-based virtual hosting]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html") in Apache to sort them out.

---

### Post by Ortix on 2012-09-08
Ok so people are recommending several things here so let me try to be a bit more clear. The server has to function as a full fledged web server with email and everything. I want to use nameservers so i can get done with that so i don't have to come back later to ask the same question. My domains are registered at godaddy.com and I want to use one of the domains there as the nameserver (and it should also function as a regular website).

Is it simply not possible to set up 2 nameservers with a single ip? I'll take a look at no-ip, it looks promissing.

BTW, the server is accessible from the outside. It's up and running and everything, i just need the domains to work.

---

### Post by darkod on 2012-09-08
First of all, it would be much simpler if you have a static IP from your ISP. You never mentioned whether you do. Even if you don't have to, maybe you can buy the service for small montly fee.

If your public IP is dynamic, you will have to use a service like the mentioned no-ip or dyndns.

On the other side, you bought domains with godaddy, right? By default, they use godaddy nameservers. Leave it as it is. The requirement for dns servers is to have at least two of them anyway, so if you want to run your own nameservers you need to have two of them with two public IPs.
So, use the godaddy panel and simply point the A record of your domain(s) to your home public IP (or to the no-ip or dyndns host if you need to use them).

That's it.

The third topic is how you will have your apache set up and organized so that it displays your domains but you seem to have that handled.

---

### Post by Ortix on 2012-09-08
Yes I do have a static IP. I mention it in my second paragraph, second sentence ;) And I will take a look at those records over at godaddy! :D

EDIT:

I also realized that my parents also have a static ip address and we have a NAS here which is on all the time (running on busybox). Would this come in handy or is it just too much work? 

I'm just asking while I wait for godaddy to process my requests

---

