---
title: "Setting up server to be accessed by others"
date: 2010-05-25
forum: Server Platforms
---

### Post by rhyz on 2010-05-25
Hello

First off sorry if in incorrect forum.

I am totally new to this whole server thing but as far as i can tell i have installed everything correctly.

I have installed: apache2 mysql and php5

When i open "http://localhost/testphp.php" i get my file :) and works great.

But trying to access through another computer doesn't work i have tried

rhys-laptop (computer name)
MY IP (which i got off whatsmyip.org)

so i think its something to do with setting up the server to the right ip but haven't got a clue what IP to use and how to change it

or if it could be something else?

Thanks Rhys

---

### Post by cdenley on 2010-05-25
Are you on a LAN? If so, does your server need to be accessed from inside your LAN or from outside your LAN?

---

### Post by rhyz on 2010-05-25
Ok thankyou for reply i have sorted it,

The IP from the site was the wrong it began in 80.
Using ifconfig i got the right one beginning in 192.168

please correct me if i have set it up wrong. but i can now access it from all computers from our network

Can outsiders connect to it?

---

### Post by cdenley on 2010-05-25
> **rhyz said:**
> Can outsiders connect to it?

No. Your IP address starting with "192.168" is the server's IP address on your LAN. It cannot be accessed from outside your network. whatsmyip.org told your what your router's WAN IP address is. That is your only IP address which can be accessed over the internet. You have to configure your router to forward any traffic it receives on port 80 to your server's LAN IP. Some ISP's will change your WAN IP frequently.

---

### Post by rhyz on 2010-05-25
Thankyou for the info i wanted to know more for security reasons.

So how would i set it up so the outsiders could access it (i would do this once site is ready)

Can they access it by a www?

---

### Post by cdenley on 2010-05-25
> **rhyz said:**
> So how would i set it up so the outsiders could access it (i would do this once site is ready)
> **cdenley said:**
> You have to configure your router to forward any traffic it receives on port 80 to your server's LAN IP.
This is called "port forwarding".
> **rhyz said:**
> 
Can they access it by a www?
You mean by a [domain name]("http://en.wikipedia.org/wiki/Domain_name")? Sure, as long as that domain name resolves to your IP address.

---

### Post by SoFl W on 2010-05-25
> **cdenley said:**
> 
You mean by a [domain name]("http://en.wikipedia.org/wiki/Domain_name")? Sure, as long as that domain name resolves to your IP address.

If he has a static IP (or updates the DNS when the IP changes) AND if the ISP allows traffic on port 80, and then the router has to allow data to pass through and goto the correct machine.

---

### Post by NeddyDownUnder on 2010-05-25
I'm assuming your ISP provides you with a dynamic IP address...

Have a look at this to get you started:
[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/DynamicDNS[/COLOR]]("https://help.ubuntu.com/community/DynamicDNS")

If by some chance your ISP gives you a static IP then things are simpler and you basically just need to setup port forwarding correctly on your router...

---

### Post by expatCM on 2010-05-26
You may want to download the server setup guide from [this]("http://woodel.com/") site.  It covers a lot of ground and from reading this thread I think you may find quite a number of areas to help you ......

---

### Post by rhyz on 2010-05-26
Thanks for the help that info was very useful and i will have a look at setting it up once im happy with everything :)

Rhys

---

