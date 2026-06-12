---
title: "Dedicated MySQL and Apache boxen?"
date: 2008-05-22
forum: Server Platforms
---

### Post by girasquid on 2008-05-22
Hello, all.

I currently have a Ubuntu 7 Server install with the LAMP option, named Max. I'm in the process of building another box, which will be named George.

I'd like to turn George into a dedicated MySQL box, and Max into a dedicated Apache box - once George is available to take over the MySQL part of the equation. Both of these boxes will be located within a co-location facility right next to each other - what will I need to do in order to make sure that George only allows connection to mysql from Max? Will putting something like this inside of my hosts.allow file work?
```

mysqld: Max

```
The hosts.deny file looks like this:
```

ALL:ALL

```
As long as the name "Max" resolves to the proper IP address, is this all I need to do, or are there more hoops to jump through?

Thanks,
Girasquid

---

### Post by kidders on 2008-05-24
Hi there,

If the boxes are going to live right next to each other, I would suggest directly connecting them, and locking mysql down to the dedicated network interface. That'll also give you an opportunity to install as high-speed a pair of network cards as you can, to avoid creating too much of a bottleneck between your web & database servers.

The other issue a dedicated network interface solves for you is privacy. Of course, depending on what'll be passing between your servers (authentication information, users' personal details, etc.), this may or may not be terribly important.

On the other hand, if your using shared network infrastructure to communicate with your database server, the connection will most likely need to be encrypted. One way to take care of this, and solve your security problem at the same time, is to tunnel the connection over SSH, and lock your database server down to "localhost" (ie disallow *all* remote access to MySQL). This approach would worsen the network-level bottleneck between your servers though.

One other thing to think about is the reliability angle. Now that you're essentially doubling the failure probability of the service you're providing, it's worth considering the additional impact something like a switch failure at the CoLo centre is likely to have. It would be nice to know that even if your users were to loose access to your service for a few minutes, your web server's database connection wouldn't get interrupted mid-operation.

Anyhow, I hope that helps.

---

### Post by girasquid on 2008-05-26
Thanks for all the help kidders!

What would I need to directly connect the boxes? Is it just a matter of another network card, or something else?

Thanks for clearing this up for me.

---

### Post by girasquid on 2008-05-26
Thanks for all the help kidders!

What would I need to directly connect the boxes? Is it just a matter of another network card, or something else?

Thanks for clearing this up for me.

---

### Post by windependence on 2008-05-26
What you are doing is very good practice to separate the web and SQL servers. Great for performance!

Might I suggest if you have two boxes that you run virtual machines, two each server, and one vm can be your SQL server and one vm your web server. Do this on both boxes and then cluster them so that if one box fails, you don't have the problem kidders brought up. This way essentially you have a complete backup box and you can run off either one or even both with load balancing.

-Tim

---

### Post by rslrdx on 2008-05-26
I have a setup like that... here is what i followed to get access to mysql from the other server.

[http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html](http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html)

---

### Post by kidders on 2008-05-26
> **girasquid said:**
> What would I need to directly connect the boxes?Anything will do, so long as it's wide enough to accommodate your traffic. A pair of ethernet cards, a firewire cable ... whatever suits.

---

### Post by windependence on 2008-05-26
You can replicate the SQL servers so that they are always in sync also. that way your data is always current on both machines.

-Tim

---

### Post by girasquid on 2008-05-27
Windependence: that sounds like a really neat idea!

How would I make sure that the virtual Apache boxes and MySQL boxes were in sync, though? Running the two virtual machines in a load-balanced situation sounds like a pretty good idea to me, I just can't figure out how to keep them both synchronized.

Also, what would I use to set up and run the two virtual machines? This is an install of Ubuntu Server.

---

