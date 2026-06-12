---
title: "Is it necessary that firewall should be active  in my desktop"
date: 2011-06-15
forum: Security
---

### Post by starbala2008 on 2011-06-15
Hi,
I am using ubuntu 11.04 in my home desktop. Is it necessary that  firewall should be active inorder to avoid hack? I heard that we will  not be given static ip address, only paid one will get static ip address  that can be used for web server implementation. If my system doesnt have  static address then can others access my system?

---

### Post by ratcheer on 2011-06-15
I would use one unless my router was running a good firewall. For the desktop, look at ufw and/or gufw. These are front ends that make iptables easier to manage.

Tim

---

### Post by sffvba[e0rt on 2011-06-15
It won't hurt to have it activated... Ubuntu Firewall is already installed...

In terminal type: sudo ufw enable

Enter password and it is on.  Simple and easy.


404

---

### Post by uRock on 2011-06-15
> **not found said:**
> It won't hurt to have it activated... Ubuntu Firewall is already installed...

In terminal type: **sudo ufw enable**

Enter password and it is on.  Simple and easy.


404

+1 If your are using I wireless connection, then I feel having the firewall turned on is a must.

---

### Post by BkkBonanza on 2011-06-15
Just adding to above advice - your IP being static or dynamic has no bearing on whether someone can see you. A simple IP scan will show you exist even if dynamic. And an arp spoof attack can take over your gateway traffic regardless of how your IP was assigned, and regardless of having a firewall or not. 

The only case where I think you probably wouldn't need the firewall is when you are behind a good router on your own private network fully under your control. In theory Ubuntu won't have any open ports (except maybe CUPS for printing support) making a firewall redundant - in practice it's always better to have the extra protection. And if you're sharing a network with any unknowns then it's even more advisable to have it up, wifi being the obvious extreme case.

---

### Post by Dngrsone on 2011-06-16
I have a firewall appliance between my laptops and the internet.  My logs are filled daily with attempts from Chinese IPs looking for easy pickings.

In other words, you're well-served having a firewall between you and the world-wide-web.

---

### Post by spynappels on 2011-06-17
> **Dngrsone said:**
> I have a firewall appliance between my laptops and the internet.  My logs are filled daily with attempts from Chinese IPs looking for easy pickings.

In other words, you're well-served having a firewall between you and the world-wide-web.

Very true, but a home router often has this as a basic feature.

To the OP: If you have a router of any kind between you and the internet, check whether it has firewall functionality. Still no harm in enabling UFW, but it will normally not do anything.
If you don't, then use UFW/GUFW.

---

### Post by jmore9 on 2011-06-17
I have 3 machines runnig 10.10 and i use firestarter as my GUI for the firewall.  Really simple to use has a wizard once configured no need to look at it ahain.

When i first started using firestarter a long time ago i used to look at all the blocked connect attempts !  It was driving me batty.  I rarely look now, only if problem with connection.

Hope this helps a little.

---

### Post by BkkBonanza on 2011-06-17
Firestarter is no longer supported/updated. UFW is the recommened replacement.

---

### Post by starbala2008 on 2011-06-17
Hi,
Thanks to all who responded for my query. I have enabled firewall using ufw. For your info. it is wired connection between my modem and desktop, no router, disabled wifi in modem as i dont need it. 

I have one more question. How can anyone access my system (say, cracker)? What are the details a cracker needs to know to access data from my system?

---

### Post by uRock on 2011-06-17
> **starbala2008 said:**
> Hi,
Thanks to all who responded for my query. I have enabled firewall using ufw. For your info. it is wired connection between my modem and desktop, no router, disabled wifi in modem as i dont need it. 

I have one more question. How can anyone access my system (say, cracker)? What are the details a cracker needs to know to access data from my system?

With the firewall enabled Ubuntu will not respond to port scans, so anyone trying to connect will quickly move on to the next address on their list.

---

### Post by spynappels on 2011-06-17
> **starbala2008 said:**
> Hi,
Thanks to all who responded for my query. I have enabled firewall using ufw. For your info. it is wired connection between my modem and desktop, no router, disabled wifi in modem as i dont need it. 


If your modem has wireless built in, it is more than likely also a router. If it is an ADSL modem with 4 RJ45 ports on the back, it is a router. Nonetheless, having UFW enabled will not do any harm.

---

### Post by Thewhistlingwind on 2011-06-18
> **starbala2008 said:**
> 
I have one more question. How can anyone access my system (say, cracker)? What are the details a cracker needs to know to access data from my system?

Ideally, they would need your IP/Some other way to contact you.

Where it goes from there, well, that's not a static thing.

So basically, they need to know where to hit. From that point on everything depends on your setup.

If you have UFW enabled 99/100 times I'd say your good.

However, just because your secure in the technical sense, doesn't mean that can't be easily negated by installing something malicious/custom made attachment trojans.

---

