---
title: "Setting up a web server"
date: 2012-09-03
forum: Server Platforms
---

### Post by steaksauce on 2012-09-03
Hi! While I'm not new to Ubuntu, I'm new to servers and I'm running into a couple of potential issues. I'm wanting to set up a web server (that can be accessed externally) and I don't have a static ip from my ISP. I've looked into this and the solution seems to be a DynDNS service.
 
However, I do not want to pay for this service and was wondering if there was a way to set up a DynDNS web server using Ubuntu Server or if there's a way to run a script that checks my external IP every few minutes or so and if it's changed, automatically update it in my DNS settings.
 
Any help would be appreciated!
 
Thanks!

---

### Post by Lars Noodén on 2012-09-03
There are a number of other dynamic DNS services besides DynDNS.  DynDNS relatively recently stopped allowing new subscriptions to its free service.  

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

### Post by bobmct on 2012-09-03
First, it depends on what you're planning on using the server for?  Will it be for open public access?  Or would it be for private, family and friends?

I have found that many/most ISP's, although employing DHCP to assign customer their IP address, the have seemed to assign the same IP based on the setup MAC address time and time again.  In fact, I know several home servers that have had the same IP for several years, even though they are assigned dynamically.

It might be worth a shot to use what you have been assigned and worry about the dynamic if/when needed.

Good luck. ;)

---

### Post by DJ_Max on 2012-09-03
With the low costs of legit web hosting, you'd probably better off going with a web host than trying to do it out of your home. Much faster networks, redundant power, better hardware, etc..

---

### Post by steaksauce on 2012-09-04
Thanks for the speedy replies!
 
First off, it will be public, but mostly for project and experience purposes.
 
If traffic starts to increase and eat up my bandwith (which I do not plan to employ the site in this way), I will host it externally.
 
Lastly, it seems like I will still have to pay to use a DNS service like No-IP, unless I can set up my own. Is that a possibility?

---

### Post by DJ_Max on 2012-09-04
> **steaksauce said:**
> Thanks for the speedy replies!
 
First off, it will be public, but mostly for project and experience purposes.
 
If traffic starts to increase and eat up my bandwith (which I do not plan to employ the site in this way), I will host it externally.
 
Lastly, it seems like I will still have to pay to use a DNS service like No-IP, unless I can set up my own. Is that a possibility?

Options:
A.) Typical Dynamic IP with your ISP, will need something like no-ip.
B.) Static IP with your ISP you can use your domain register DNS service and have an A record point to your IP.

---

### Post by steaksauce on 2012-09-04
> **DJ_Max said:**
> Options:
A.) Typical Dynamic IP with your ISP, will need something like no-ip.
B.) Static IP with your ISP you can use your domain register DNS service and have an A record point to your IP.

Thanks!

---

### Post by Habitual on 2012-09-05
> **DJ_Max said:**
> Options:
A.) Typical Dynamic IP with your ISP, will need something like no-ip.
B.) Static IP with your ISP you can use your domain register DNS service and have an A record point to your IP.

Damn Straight and to the Point!

---

### Post by DJ_Max on 2012-09-05
> **steaksauce said:**
> Thanks!
No Problem, servers are my specialty
> **Habitual said:**
> Damn Straight and to the Point!
I try, I sometimes ramble if i try to explain things in detail and it ends up confusing people.

---

