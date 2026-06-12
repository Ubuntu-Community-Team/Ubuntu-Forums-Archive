---
title: "PPC webserver with 2 HD's failover load balancing"
date: 2008-11-11
forum: Server Platforms
---

### Post by drkoop81 on 2008-11-11
I have a problem and I am wondering if there is someone with a solution out there. I have dug bit and haven't found exactly what I am looking for so I am posting a thread about it. I orginally posted this in Apple users since it is on PPC but I am re-posting here.

I found this thread that is similar to what I am looking for but this is kinda overkill. plus I only have one server for now.

[http://www.howtoforge.com/the-perfec...04-hardy-heron](http://www.howtoforge.com/the-perfec...04-hardy-heron)

So I have a perfect server ubuntu 8.04 LTS setup with ppc xserve. Dual lan ports two 500gb hardrives, on 1 HD is LAMP, mail. FTP, ISPconfig and all the great stuff running like a champ. I have bout 30 websites with mysql on it already.

All is swell but I want to host some important sites that need to be up with little downtime. So I want to be able to clone the first HD over to the second and if the first HD goes out be able to go seamlessly to the second drive. I also want to have simple load balancing to the second lan port with a second IP and round robin DNS for a little higher traffic. Any thoughts? Links or things I may have missed. Thanks in advance for any help.

---

### Post by drkoop81 on 2008-11-13
bump bump anyone know how to do this? I get the DNS part now. Can I do that backup with software raid? Can i do it with a current bunch of sites operating on it. 

Basically I was thinking of something similar to Carbon copy Cloner. I can set that up and it will backup at 2 am and I can boot to that drive if the main goes down. Shoot I don't know. I am kind of a Linux noob. :)

---

### Post by Philio on 2008-11-13
Well to clone the hard drives you need to setup a RAID array. I'm afraid I've no idea how you would do it on PPC though as never used one.

I think that load balancing a single server with 2 network cards would be pointless, there are too many other single points of failure in 1 server to warrant load balancing 2 network cards which would only give you fail over in the event one of the ethernet cards dies. Also DNS round robin isn't ideal, as if one of the cards did stop working only 50% of the connections would actually reach the box, the other 50% would receive a browser timeout.

For example in a single machine (if you did 'load balance' the network cards) you would have the following other single points of failure:

Motherboard
CPU
RAM
Power supply
Drive controller

---

### Post by drkoop81 on 2008-11-14
I hear ya. So I should set it up like the link above with two servers with four hard drives. I want to do that I just have to migrate some stuff first. I should then have two load balancers then too as that would eliminate the point of failure.

Can I execute the [this]("http://www.howtoforge.com/the-perfect-load-balanced-and-high-availability-web-cluster-with-2-servers-running-xen-on-ubuntu-8.04-hardy-heron") with sites running on it already? Can I do it with the RAID array too? I already have sites on it and isp config setup.  

I just figured I could change the dns if the one lan port went bad. I would need to get more ip's to do this too. 

Cool  Thanks :)

---

### Post by cariboo on 2008-11-14
A raid array will not do what you are looking for. Raid is only good if you have a hard rive failure. If there is data corruption on I drive it will alos be corrupted on the second drive. If you have a raid array, you should also have up to date backups of that array.

If you need an exact duplicate of your first hard drive. Rsync is the program you need, to create an exact duplicate of your main hard drive. Have a look at the script in the last post here:

[http://ubuntuforums.org/archive/index.php/t-355030.html](http://ubuntuforums.org/archive/index.php/t-355030.html)

As for thee automatic fallover if one drive fails or is corrupted, I'm not sure about that, but I'm sure someone else will come along with a suggestion.

Jim

---

