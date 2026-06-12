---
title: "Load balancing?"
date: 2009-02-14
forum: Server Platforms
---

### Post by linuxisevolution on 2009-02-14
I would like to setup a load balancing network for Apache. I have three systems for this project. Do I need all three? Could I just have the two apache machines load balance them selves, or should I have the third weakest machine with three NIC cards routing to the two others and having it be the balancer? for instance:


Internet >> Load balancer >>


                          Apache machine 1
                          Apache machine 2

or 

Internet >> Apache Machine 1
            Apache Machine 2


Which is right? I'm trying to follow this howto 

[http://www.howtoforge.com/high_availability_loadbalanced_apache_cluster](http://www.howtoforge.com/high_availability_loadbalanced_apache_cluster)

---

### Post by HermanAB on 2009-02-14
Howdy,

Use rsync to keep the machines the same, so that you only ever need to update one of them.  Then use Round Robin DNS to share the load between them.

Cheers,

Herman

---

### Post by linuxisevolution on 2009-02-14
> **HermanAB said:**
> Howdy,

Use rsync to keep the machines the same, so that you only ever need to update one of them.  Then use Round Robin DNS to share the load between them.

Cheers,

Herman

Thanks, but my question was how should I have them networked?

---

### Post by HermanAB on 2009-02-14
Simply plug them all into the same switch and give them all individual IP addresses.  So there is no 'load balancer' device per se.  Simply let the DNS resolve the machines in a round robin.  Many big web sites work this way - nice and simple.

Google for 'round robin dns'.

Cheers,

Herman

---

### Post by linuxisevolution on 2009-02-14
> **HermanAB said:**
> Simply plug them all into the same switch and give them all individual IP addresses.  So there is no 'load balancer' device per se.  Simply let the DNS resolve the machines in a round robin.  Many big web sites work this way - nice and simple.

Google for 'round robin dns'.

Cheers,

Herman

Thanks! I'll be using BalanceNG because it is simple and free if you just have two "targets." The only problem is, only one of my servers has a working hard drive and networking card.Do you know were I can find two very cheep ethernet cards and two used or new hard drives? The balancer server just needs a low-end 500mb-ish hard drive or similar...The other server I would like to have a 6gb or higher hd for it. Is anyone giving any away? Thanks for any help :)


EDIT: The sites that I will be serving get around 200+ hits a day. I bit much for my fifteen year old hardware, that's why I like this setup. The sites are currently on Yahoo Business accounts, but why do that when I can do it myself for free? And I can use cgi and PHP ;)

---

### Post by cariboo on 2009-02-14
If you don't want to spend a lot of money on hardware, try your local thrift store, and if your local dump has a share shed try there, also ask friends if they have any old  computers lying around that they want to get rid of, it is amazing what people throw away. Otherwise Ebay is a good place for used hardware, just make sure you set yourself a buget first.

Actually if you have to depend on your servers new hardware would be better, Locally I can get new network cards for $15.00CDN and 80Gb hard drive retail for less than $70.00

Jim

---

### Post by HermanAB on 2009-02-14
If you are cash strapped, why use BalanceNG?  Round robin balancing is built into BIND.  You don't need anything special, you don't need any hardware, just configure BIND to resolve your domain in a round robin.  I guess it sounds 'too easy', but it is.

Cheers,

Herman

---

### Post by linuxisevolution on 2009-02-14
> **HermanAB said:**
> If you are cash strapped, why use BalanceNG?  Round robin balancing is built into BIND.  You don't need anything special, you don't need any hardware, just configure BIND to resolve your domain in a round robin.  I guess it sounds 'too easy', but it is.

Cheers,

Herman

Because I understand BalanceNG and I can use the free version, and it works. I still need a networking card and hard drive to use bind anyway, don't I? :P

---

### Post by linuxisevolution on 2009-02-14
> **cariboo907 said:**
> If you don't want to spend a lot of money on hardware, try your local thrift store, and if your local dump has a share shed try there, also ask friends if they have any old  computers lying around that they want to get rid of, it is amazing what people throw away. Otherwise Ebay is a good place for used hardware, just make sure you set yourself a buget first.

Actually if you have to depend on your servers new hardware would be better, Locally I can get new network cards for $15.00CDN and 80Gb hard drive retail for less than $70.00

Jim

Is this a good networking switch for the price? :

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833180057](http://www.newegg.com/Product/Product.aspx?Item=N82E16833180057)


And is this a good ethernet card?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833180025](http://www.newegg.com/Product/Product.aspx?Item=N82E16833180025)


I could get a hard drive for $30USD but I don't have it :( . Anybody?

---

### Post by HermanAB on 2009-02-14
Anyhoo, with only 200 hits a day, you only need one machine (an Eee PC 701 can handle it).  So you don't need a load balancer at all, whether software or hardware.  Just get your one machine to work properly.

Cheers,

Herman

---

### Post by linuxisevolution on 2009-02-14
> **HermanAB said:**
> Anyhoo, with only 200 hits a day, you only need one machine (an Eee PC 701 can handle it).  So you don't need a load balancer at all, whether software or hardware.  Just get your one machine to work properly.

Cheers,

Herman

Well 200 hits per website, and total it's be about 500 hits a day. My current server is 550mhz and is already getting 50 hits  a day plus 3gb+ downloads. A load balancer is required ;)

---

### Post by Advice Pro on 2009-03-21
What did you mean by two targets:

I'll be using BalanceNG because it is simple and free if you just have two "targets."


Is it two computers, if so then can't I use more than two?

Can I run just any software?  You can answer at: 

[What software can be ran on a load-balancing cluster of Ubuntu Server Edition]("http://ubuntuforums.org/showthread.php?p=6917845#post6917845")

---

