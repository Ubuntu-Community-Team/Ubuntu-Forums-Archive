---
title: "my first web server"
date: 2006-07-25
forum: Server Platforms
---

### Post by joshchernoff on 2006-07-25
I'm starting with a small simple web server to first learn how to manage hosting my own sites. 

I'v been using this as a guide to setting up a server.
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

I havent got threw it fully, I got errors with ssl keys? any how
I got a grasp of how it mostly works but the dns stuff I'm still in the dark about.

One. how do you have one box with two dns names servers with Two diffrent static IP's? (do I need two nic's?)

Two. can I still use one of the two IP's for my websites

Three. Do I have to make a diffrent local IP for every site?
Exsample, [www.siteone.com](www.siteone.com) = 192.168.0.101, sitetwo.com = 192.168.0.102, sitethree.com = 192.168.0.103. also would I need to add them to my routers static dhcp?

how do I find out the max my server will handle.
I have a 896kbs upstream line with one static IP right

This is my server,
cpu: amd sempron 64bit 3000+
ram: 1gig ddr2 pc5600 (will be maxing out at 4gigs)
motherboard: msi k9n neo
harddrive: samsung 160 gig sata2 (300)
router: dlink dl-524 802.11.g wifi router 
(wifi turned off used for static dhcp for workstation and server)
video: ati radeon x3000 128mb pcix16 card (not bad for $5)
OS: Ubuntu 6.06 LTS (Dapper Drake)AMD 64 bit
Only looking to have a basic hosting server php, mysql and so on.
I realy dont need ssl as far as I know. no creadit cards on my sites.

Now I know I need a bigger upstream if I want more running on my server but I dont know how to say when I should stop. and start looking? one of my sites I host at godaddy uses only about 3gigs a month on avarage.

Any how I know I should get a GUI but I dont want one I want to learn it the hard way.

---

### Post by lamego on 2006-07-25
> One. how do you have one box with two dns names servers with Two different static IP's? (do I need two nic's?)
The dns allows to setup multiple names pointing to a single IP adrees, you don't need multiple nics for this.
This is done by creating a CNAME or an A record on the DNS pointing to an existing host/IP .

> Three. Do I have to make a different local IP for every site?
Exsample, [www.siteone.com](www.siteone.com) = 192.168.0.101, sitetwo.com = 192.168.0.102, sitethree.com = 192.168.0.103. also would I need to add them to my routers static dhcp?

No, Apache supports virtual hosts, it means you can setup different websites just based on the requested name (even if they point to the same IP address).

```
how do I find out the max my server will handle.
I have a 896kbs upstream line with one static IP right

```
You can only estimate this if you know what will be the network bandwidth used by your sites, it depends a lots on the number of visits and files served.

---

### Post by joshchernoff on 2006-07-25
ok so I got every thing up, but I need to point the domain from godady that I got to it. how to I set up the dns on my dox to have two dns nameservers with two diffrent IP's? I see something out there shows how to point to your own name servers but it did not show to to set up two serves on one box.

---

