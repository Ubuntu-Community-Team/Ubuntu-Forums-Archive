---
title: "Any experience with the new SPARC ubuntu?"
date: 2006-06-17
forum: Server Platforms
---

### Post by tribaal on 2006-06-17
Hi all!

My company asked me to investigate a little on possible performance increase / power savings, if we decided to switch some of our webservers to sun FIRE servers (T1000 or T2000 most probably).

Has anybody tried to install Ubuntu / LAMP server (with php) on such a server? Are the benchmarks satisfying?
I'm especially interested in the load performance.

I'll get back to you guys when (if) we make the switch!

- trib'

---

### Post by Ubuntu Warrior on 2006-08-25
We are also seriously looking at the Sun T1000/T2000 "enviro" servers - who can pass up the chance to help save the planet by burning up less energy! Way to go, Sun!

The only catch is that, as tribaal looks to be doing, we want to stick to running Ubuntu Linux on the boxes as ALL our Linux servers are of the Ubuntu flavour to date.

Also extremely interested in finding out how Ubuntu runs on top of the Sun boxes.

---

### Post by Woei on 2006-08-26
> **tribaal said:**
> 
My company asked me to investigate a little on possible performance increase / power savings, if we decided to switch some of our webservers to sun FIRE servers (T1000 or T2000 most probably).

Has anybody tried to install Ubuntu / LAMP server (with php) on such a server? Are the benchmarks satisfying?
I'm especially interested in the load performance.

I'll get back to you guys when (if) we make the switch!

Well, perhaps the most famous article on the net about the TX000 series is by one of the operator's of the [Heanet network.](http://www.stdlib.net/~colmmacc/category/niagara/page/2/) Another great review, unfortunately only in Dutch can be found [here](http://tweakers.net/reviews/633/5). 

The point to take away on both of these reviews is this: it's more expensive than dual core x86-64 machines, usually performs a bit to a lot worse in anything but insanely multithreaded situations (a massive fileserver, or an http server serving mostly static content). Running it as a database server doesn't give you much benefit either if your queries are anything but trivially simple. The only case where the Niagara shines is in multithreaded operations with very light CPU requirements (it only has one FPU!). That Dutch article for example is from one of the biggest hardware sites in the Netherlands, and for their load (which is higher than most business will ever see), a dual x86-64 is a much better choice. Only go for the more expensive TX000 if, after profiling your applications, you can demonstrate your workload is limited by the number of processes that can run simultaniously, and not raw CPU power or available memory. And even then, you'll have to tweak Apache and MySQL servers a lot and try different builds to get optimum performance. All things you needn't do on a more mainstream x86 machine, where it's practically boot and go.

Also, please bare in mind that the TX000 is a completely different architecture. Closed source x86 programs will *not* work on the SPARC. Virtualisation packages like Xen still have no support for SPARC, and VMWare is out of the question too. Solaris 10 has a nice new feature called 'zones', which are a form of containers instead of a full virtualisation solution, but that's Solaris, not Ubuntu.

The TX000 may seem like a nice product, but from what I've read about it, it's more of a niche product for specific needs than something any business can purchase and immediately expect great results from. I haven't played with a TX000 yet myself though, so take my opinions about it for what it's worth.

---

### Post by apaton on 2006-08-27
I haven't run Ubuntu yet on a SPARC server but I do have a T2000. *"Conflict of interest - I work for a Sun reseller". *

I want to agree with Woei's comments about the T2000 and add the following. The T1000/2000 is great at running Apache, SQUID, DNS & DHCP infrastructure applications but running a database, (Postgres/MYSQL/ORACLE/DB2) is not its strong point.

I've recommended to customers to use a two tier approach, provided a database backend on Opteron/Xeon/Ultra SPARC server and deliver WEB front end on T1000/T2000. This is usually good practice for scalable system design.

FYI: Solaris 10 with T2000 zones, You can easy run "Apache, SQUID, DNS & DHCP" on a single server in separate zones using Solaris 10 to allocated resources appropriately.

apaton

---

