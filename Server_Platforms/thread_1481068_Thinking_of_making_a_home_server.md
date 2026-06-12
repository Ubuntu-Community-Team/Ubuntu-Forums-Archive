---
title: "Thinking of making a home server"
date: 2010-05-12
forum: Server Platforms
---

### Post by d1brian on 2010-05-12
As the title says i'm thinking of making a home server that's going to be used for the following services:
 
1. Routing (w/ NAT), firewall (i would probably do this using iptables)
2. Web server (most likely with max. 2-3 virtual hosts) using both https(default) and http.
3. FTP Server (for accesing the web pages source files in case i need to and i'm not home)
4. File server for the LAN (for small things)
5. Mail server that would gather the emails from other email accounts (eg: gmail) and filter the spam (i going to install SquirrelMail for web access)
6. Maybe a VPN (and wake on lan in case i need something from my desktop) - it's kind of a pending service right now, but for learning purposes i maybe would install it.
7. I'm also thinking of running a DNS (as a backup in case the providers DNS servers (partially) go down - and it has happend)
8. SSH Server
9. MySQL server
10. DHCP Server
 
I'm not sure if point 5 is entirely possible (i mean the gathering part).
 
The ideea is that i want something that requires very few resources (hence less power and lower hardware costs - not a very big budget).
 
So as the OS i was thinking of using Ubuntu Server (i don't mind using CLI - plus it's got the advantage that it's faster to SSH than to use remote desktop and using a GUI would be more resource intensive) with Webmin. 
 
As an alternative dristo i was thinking of Smoothwall but then i think i would have to drop some services (not a very big problem but would be nice to have them) - haven't got a chance to test it yet and see what i can and can't do with it.
 
The question is: What hardware configuration (i'm thinking of a 1.8Ghz CPU (max), 512 RAM and >20GB HDD) and which distro/OS would be more appropriate for what i'm thinking to do?
 
Also i'd like to mention that i'm sort of new to Ubuntu (i've been using it for about 2-3 months) but than again i'm looking at this as an oportunity of learning new things.
 
Thanks in advance.

---

### Post by dudumomo on 2010-05-12
Hi d1brian,
Glad to see you want to self host yourself.

To do all these: SSH, SFTP (Better than FTP), SAMBA, MAIL (Don't know how to do what you want), LAMP, BIND, etc... a 1.8GHZ single core (I guess) will be enough. I've used a Duron 900Mhz to host a website and a couple of others small services.

But, I'm don't think 512mb will be enough (Especially if you want to use VPN). 1GB will be more than enough. So if you can add 512mb or even 256mb, it would be much better.

Obviously, in some case you can do all that with less than 512mb (By using lighter softs, lighter OS than Ubuntu Server, etc...) but the simpliest would be to add a bit more RAM.

About the OS, well...not very objective...but Ubuntu server is a good distrib, very easy to use.
I've start by Gentoo (As my main computer are using Gentoo and not Ubuntu), but it was quite difficult to do everything I wanted (As I was a real noob). The advantage of Gentoo was a smaller usage of RAM, but quite taugh for me to manage the distrib as a server.
Debian will do great as well, even lighter than Ubuntu I bet, but again a bit more difficult.

Or you can have a try with specialized distributions as SME Server by example.

But in my case, I've finally chosen Ubuntu Server.

---

### Post by rmccarri on 2010-05-12
I would second dudumomo's comments.  I think that 1 gb would be worth a $25 order from NewEgg.

My setup at home is similar to what you want to build (I'm serving a few web sites with LAMP and virtual hosting, an SSH server, WakeonLan for other computers, a VPN server, automated backups, Tivo home media server and such).  My system actually has the GUI installed since it is our home desktop as well and it runs without hiccups with an old AMD single core Athlon processor (I believe it's exactly 1.8 GHz) and 2 GB of ram.  The only time that the extra GB of ram is really necessary is when I'm using Matlab or some other resource intensive program through the GUI.  Typical system loads when it's running just as a server are in the 0.2 range or so.

Good luck and have fun!

---

### Post by rmccarri on 2010-05-12
Check that, I just SSHed into the server to check the system load and after initializing a VPN connection to test it, I got this:

```
11:03:51 up 2 days, 18:44,  1 user,  load average: 0.06, 0.03, 0.01
```

The 0.2 number in my previous post was too high.

---

### Post by NullHead on 2010-05-12
Honestly, I'd just go for something like [this](http://www.newegg.com/Product/Product.aspx?Item=N82E16813500027) or snag somebody's old gamer computer off ebay. Typically speaking, the more CPU cores the better. This one at least has two cores, you can expand to 4gb of ddr800, there is three SATA connectors and it only uses 90 watts of electricity!

---

### Post by CharlesA on 2010-05-12
> **NullHead said:**
> Honestly, I'd just go for something like [this](http://www.newegg.com/Product/Product.aspx?Item=N82E16813500027) or snag somebody's old gamer computer off ebay. Typically speaking, the more CPU cores the better. This one at least has two cores, you can expand to 4gb of ddr800, there is three SATA connectors and it only uses 90 watts of electricity!

That would work perfectly for this kind of set up.

---

### Post by Boondoklife on 2010-05-12
> **d1brian said:**
> As the title says i'm thinking of making a home server that's going to be used for the following services:
 
1. Routing (w/ NAT), firewall (i would probably do this using iptables)
2. Web server (most likely with max. 2-3 virtual hosts) using both https(default) and http.
3. FTP Server (for accesing the web pages source files in case i need to and i'm not home)
4. File server for the LAN (for small things)
5. Mail server that would gather the emails from other email accounts (eg: gmail) and filter the spam (i going to install SquirrelMail for web access)
6. Maybe a VPN (and wake on lan in case i need something from my desktop) - it's kind of a pending service right now, but for learning purposes i maybe would install it.
7. I'm also thinking of running a DNS (as a backup in case the providers DNS servers (partially) go down - and it has happend)
8. SSH Server
9. MySQL server
10. DHCP Server
 
I'm not sure if point 5 is entirely possible (i mean the gathering part).
 
The ideea is that i want something that requires very few resources (hence less power and lower hardware costs - not a very big budget).
 
So as the OS i was thinking of using Ubuntu Server (i don't mind using CLI - plus it's got the advantage that it's faster to SSH than to use remote desktop and using a GUI would be more resource intensive) with Webmin. 
 
As an alternative dristo i was thinking of Smoothwall but then i think i would have to drop some services (not a very big problem but would be nice to have them) - haven't got a chance to test it yet and see what i can and can't do with it.
 
The question is: What hardware configuration (i'm thinking of a 1.8Ghz CPU (max), 512 RAM and >20GB HDD) and which distro/OS would be more appropriate for what i'm thinking to do?
 
Also i'd like to mention that i'm sort of new to Ubuntu (i've been using it for about 2-3 months) but than again i'm looking at this as an oportunity of learning new things.
 
Thanks in advance.


Well first off I would like to tip my cup to your adventurous endeavor, BUT I personally would not go about having all of these eggs in one basket.

For the firewall/routing, why not just get a cheap dd-wrt compatible router? This would take care of the need for your server to be the main network pipe/filter. I have one myself and I have yet to run into a firewall issue I could not resolve. Also it will allow you to edit firewall rules via iptables if you wish. It also serves as my DNS/Filter.

Secondly, how much speed do you need for your fileserver? I ask because western digital makes a nifty little NAS myBook World edition that may suit your needs. While it is not the fastest thing on the planet (1.5MB/s is normal here but I use 802.11g). You can use an optiware server to get other precompiled software that you can run on it including a torrent client. 

Lastly I would also just go with a VPN device to facilitate that or use the DD-WRT router to do it.

As for the rest, you will prolly spend most of your time with the mail server stuff and web, and may verywell foobar things a few times. however by using seperate appliances, you can minimize the impact to others that will be using your server (unless you will be the only person using it).

---

### Post by d1brian on 2010-05-12
> **NullHead said:**
> Honestly, I'd just go for something like [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813500027") or snag somebody's old gamer computer off ebay. Typically speaking, the more CPU cores the better. This one at least has two cores, you can expand to 4gb of ddr800, there is three SATA connectors and it only uses 90 watts of electricity!

unfortunately that setup from newegg isn't really an option because is like 3x my budget :( (and i don't know if the ship in Europe)

> **Boondoklife said:**
> Well first off I would like to tip my cup to your adventurous endeavor, BUT I personally would not go about having all of these eggs in one basket.

I wouldn't either but considering it's mostly for personal use i don't want to invest that much in equipment and keep the overall costs as low as possible.

I don't really need a very fast file server (maybe i won't need it at all) because i would mostly store small files on it.

---

### Post by CharlesA on 2010-05-12
It would still be better to use a different device as the router/firewall.

If that box is compromised, you are owned.

---

### Post by Boondoklife on 2010-05-12
Well really I think your costs are minimal with my setup, you can get the router for prolly 20, got min for 15 on ebay. The mybook is the older bluering edition so prolly 80-100 there (That is with 2 750GB drives). As a side note I use the mybook in RAID 1 to make sure I have a backup.

Powerwise it is minimal as the mybook is 30watts and the router cant be more than 20watts.

---

### Post by windependence on 2010-05-12
> **NullHead said:**
> Honestly, I'd just go for something like [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813500027") or snag somebody's old gamer computer off ebay. Typically speaking, the more CPU cores the better. This one at least has two cores, you can expand to 4gb of ddr800, there is three SATA connectors and it only uses 90 watts of electricity!
Sorry, but this is just not true. First off, unless your apps can use multiple cores, extra cores are useless and just sit there consuming power. More than half the apps out there do not use more than a single core. He would be much better spending his money on extra RAM rather than more cores. 

I agree that he should think seriously about using a separate box for the firewall/router setup because your server can easily be overwhelmed just by sending a DDOS attack. Blocking those packets will consume CPU and memory until the server comes to it's knees even though the server is doing it's job correctly. Take a look at PFsense [www.pfsense.org](www.pfsense.org).

-Tim

---

### Post by CharlesA on 2010-05-12
Having dual or quad cores allow the OS to do load balanacing between the cores. Apps don't have to use more then one core for you to benefit from the performance of a multicore CPU.

---

### Post by windependence on 2010-05-12
Not only do the apps have to be written to take advantage of multiple cores, but the OS has to support SMP as well. We can go even further on this by saying that some implementations of SMP are not the greatest either. I am not real familiar with Ubuntu's implementation of SMP, but I can tell you that you're going to find that generally, only production server type apps will benefit from multiple cores. For example, it probably won't do you much good to have 8 cores on your torrent server, but if you are running a LAMP based web server, the applications most definitely will take advantage of SMP. There is no automatic "load balancing" just because the machine has multiple CPUs.

-Tim

---

### Post by CharlesA on 2010-05-12
I must be missing something since the kernel I use says this:

```
 2.6.32-22-server #33-Ubuntu SMP
```

Then again, I use my box to run VMs. *shrug*

---

### Post by windependence on 2010-05-12
> **CharlesA said:**
> I must be missing something since the kernel I use says this:

```
 2.6.32-22-server #33-Ubuntu SMP
```Then again, I use my box to run VMs. *shrug*
Correct - on your box. Most virtualization software will balance the load between CPU cores and actually will use them all as one big CPU pool. One of the great advantages of virtualization. :-)

-Tim

---

### Post by NullHead on 2010-05-12
> **windependence said:**
> Sorry, but this is just not true. First off, unless your apps can use multiple cores, extra cores are useless and just sit there consuming power. More than half the apps out there do not use more than a single core. He would be much better spending his money on extra RAM rather than more cores. 

I agree that he should think seriously about using a separate box for the firewall/router setup because your server can easily be overwhelmed just by sending a DDOS attack. Blocking those packets will consume CPU and memory until the server comes to it's knees even though the server is doing it's job correctly. Take a look at PFsense [www.pfsense.org](www.pfsense.org).

-Tim

Having a dual core at least allows the OS to have some CPU power when an app is using the other. That's really all I meant. Plus it's simply impossible to buy a modern CPU that has a single core. 

My point wasn't really on the "is a dual core /really/ better than single core?", but more on that it's power efficient, small and has some extra juice if needed.

Anyways, an argument best had in another thread.

---

### Post by d1brian on 2010-05-12
but isn't a router kind of pointless if someone decides to make a DDOS attack, i mean i still have to forward ports on the router, wouldn't that be the same as not having the router?

---

### Post by Boondoklife on 2010-05-13
> **d1brian said:**
> but isn't a router kind of pointless if someone decides to make a DDOS attack, i mean i still have to forward ports on the router, wouldn't that be the same as not having the router?

Well I really doubt hardware will be a real issue in your case unless you have a huge pipe coming to your house. In my opinion a ddos is gonna get you either way.

The real benefit to having a separate device for the firewall/routing is just that it is segregated from all the other services. If you pooch your file server or what ever other service, then you may very well pooch your main line to the internet (this to me would be unacceptable).

---

### Post by NullHead on 2010-05-13
> **Boondoklife said:**
> Well I really doubt hardware will be a real issue in your case unless you have a huge pipe coming to your house. In my opinion a ddos is gonna get you either way.

The real benefit to having a separate device for the firewall/routing is just that it is segregated from all the other services. If you pooch your file server or what ever other service, then you may very well pooch your main line to the internet (this to me would be unacceptable).

I have to say, I agree with this. Having a dedicated box to firewall your internet sounds like a good idea; considering I'd probably end up bringing the machine down quite often.

---

### Post by CharlesA on 2010-05-13
> **NullHead said:**
> I have to say, I agree with this. Having a dedicated box to firewall your internet sounds like a good idea; considering I'd probably end up bringing the machine down quite often.

I've used a regular linux box as a gateway before, but that was it's only job.

If you are to the point of getting hit with DDoS attacks, you really need to rethink the idea of having all your eggs in one basket, so to speak.

Dedicated routing appliance work be better off overall. Like I said before, if your box is compromised and it runs all your services, you are pretty much owned.

If the box is the gateway and hosts all of your services, and gets DoS'd or DDoS'd that machine will be out of commission until you reboot it. What would be preventing that sort of thing from happening again? Firewall rules won't.

---

### Post by d1brian on 2010-05-13
I thought it through and I'll use a dedicated appliance for routing.

As software I was thinking to use:

Web - apache
FTP - ftpd-ssl
Mail - postfix
VPN - pptpd
SSH - openssh
DHCP - dhcp3
DNS - bind9

Should I be using different software?

---

### Post by CharlesA on 2010-05-13
Looks good.

---

### Post by CharlesA on 2010-05-13
EDIT: Double post for some reason.

---

