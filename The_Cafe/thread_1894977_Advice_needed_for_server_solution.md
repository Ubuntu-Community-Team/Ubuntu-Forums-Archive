---
title: "Advice needed for server solution"
date: 2011-12-13
forum: The Cafe
---

### Post by fikkaud on 2011-12-13
Hello all,
I'm a happy Ubuntu user, and have been running different LAMP servers for the past 10 yrs on single PC setups.
So I'm not the most skillful sysop, but I've managed so far with tutorials and guides. 
Now the hobbyist in me wants to push it a bit further.
 
I've got my hands on a bundle of really cheap nano PC's with ATOM 230 @1.6GHz. As far as I know they can run 64bits. They only have one Gb NIC. But I guess USB NICs could be used.
 
I'd like to set up a multinode server (2 or 3 nodes)
The main task for this will be hosting a few small websites (1000 pageviews/day) 
Apache or nginx, Perl scripts, MySql, Mailserver, Samba.
 
Understand me right here, my present server is coping fine with the tasks today. The toughest for my current server is to parse a 500MB textfile every night and update the MySql database. Which takes it 1hr to complete.  
I'm only chasing this b'cause I'd like to explore more advanced setups. And I think this minirack will look really cool too :P
 
Since I'm a novice I need advice in which way to go when planning the setup.
Here's a list of keywords currently running through my brain:
Speed, redundancy, Cloud, load balancing, Hadoop, hearbeat, cluster.
 
Any response to my thoughts will be appreciated.
Regards
A

---

### Post by Primefalcon on 2011-12-13
Frankly I'd say stick with Ubuntu, but go for he server LTS releases, and wait until a new version has been out a minimum of 6 months before you upgrade, or better yet wait until hat you have installed is near end of life support before upgrading to the next in line LTS...

When 12.04 hits both desktop and server will be supported for 5 years...

A lot of people will say CentOS, but honestly... with how red hat has been with trying to be non-friendly to respins... and with the upcoming 5 year support on Ubuntu.... well

---

### Post by sandyd on 2011-12-13
> **fikkaud said:**
> Hello all,
I'm a happy Ubuntu user, and have been running different LAMP servers for the past 10 yrs on single PC setups.
So I'm not the most skillful sysop, but I've managed so far with tutorials and guides. 
Now the hobbyist in me wants to push it a bit further.
 
I've got my hands on a bundle of really cheap nano PC's with ATOM 230 @1.6GHz. As far as I know they can run 64bits. They only have one Gb NIC. But I guess USB NICs could be used.
 
I'd like to set up a multinode server (2 or 3 nodes)
The main task for this will be hosting a few small websites (1000 pageviews/day) 
Apache or nginx, Perl scripts, MySql, Mailserver, Samba.
 
Understand me right here, my present server is coping fine with the tasks today. The toughest for my current server is to parse a 500MB textfile every night and update the MySql database. Which takes it 1hr to complete.  
I'm only chasing this b'cause I'd like to explore more advanced setups. And I think this minirack will look really cool too :P
 
Since I'm a novice I need advice in which way to go when planning the setup.
Here's a list of keywords currently running through my brain:
Speed, redundancy, Cloud, load balancing, Hadoop, hearbeat, cluster.
 
Any response to my thoughts will be appreciated.
Regards
A
I would advise either to use UEC. [https://help.ubuntu.com/community/UEC](https://help.ubuntu.com/community/UEC) , or setup a VMWare ESXi cluster with the nodes. I would advise ESXi (if your hardware supports it that is), because its much more scalable, and you can run multiple OSes at once.

I tried out UEC earlier, and it was quite nice, though I don't use it anymore (It isn't that its bad or anything, but I just decided on a different setup using a several super powerful servers and ESXi Nodes).

The only problem I had with testing clusters with normal PC-grade hardware was that the HD becomes sufficiently bogged down with I/O Requests. I would recommend either a SAS / RAID 10 Array / SSDs to prevent that. Besides, SASes are better if you plan on running 24/7, because normal PC-grade HDs were never meant for that.

---

### Post by fikkaud on 2011-12-13
sandyd, thank you for your answer. I immediately looked into ESXi, and was impressed and quite tempted. Although looking at the specs I'm probably falling out on RAM and CPU. I guess I could fit 4GB more RAM, but it seems like a huge overkill.
[SIZE=1][/SIZE] 
[SIZE=1]***[SIZE=1]MINIMUM [/SIZE]HARDWARE** *[/SIZE]
[SIZE=1][/SIZE] 
[FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1][FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1]***ESXi ***[/SIZE][/FONT][/SIZE][/FONT]
[FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1][FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1]*Three ESXi/ESX servers *[/SIZE][/FONT]
[SIZE=1][FONT=Gotham Narrow Light,Gotham Narrow Light]*CPU &#8211; Two processors of 2GHz *[/FONT][/SIZE]
[SIZE=1][FONT=Gotham Narrow Light,Gotham Narrow Light]*Memory &#8211; 6GB *[/FONT][/SIZE]
[SIZE=1][FONT=Gotham Narrow Light,Gotham Narrow Light]*Network &#8211; 2x 1GB network adaptor *[/FONT][/SIZE][/SIZE][/FONT]
[FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1][FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1][/SIZE][/FONT][/SIZE][/FONT] 
[FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1][FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1]***Storage ***[/SIZE][/FONT][/SIZE][/FONT]
[FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1][FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1]*One datastore (100GB) *[/SIZE][/FONT][/SIZE][/FONT]
*[SIZE=1][/SIZE]* 
[FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1][FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1]***Network ***[/SIZE][/FONT][/SIZE][/FONT]
[FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1][FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1]*One VLAN for carrying virtual machine traffic; one VLAN for carrying management traffic *[/SIZE][/FONT][/SIZE][/FONT]
 
 
Is Ubuntu Cloud similar in the way you set up a virtual environment with multiple nodes?
I can give 'em both a try, to get to know the theory behind.

---

### Post by sandyd on 2011-12-13
> **fikkaud said:**
> sandyd, thank you for your answer. I immediately looked into ESXi, and was impressed and quite tempted. Although looking at the specs I'm probably falling out on RAM and CPU. I guess I could fit 4GB more RAM, but it seems like a huge overkill.
 
[SIZE=1]***[SIZE=1]MINIMUM [/SIZE]HARDWARE** *[/SIZE]
 
[FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1][FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1]***ESXi ***[/SIZE][/FONT][/SIZE][/FONT]
[FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1][FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1]*Three ESXi/ESX servers *[/SIZE][/FONT]
[SIZE=1][FONT=Gotham Narrow Light,Gotham Narrow Light]*CPU &#8211; Two processors of 2GHz *[/FONT][/SIZE]
[SIZE=1][FONT=Gotham Narrow Light,Gotham Narrow Light]*Memory &#8211; 6GB *[/FONT][/SIZE]
[SIZE=1][FONT=Gotham Narrow Light,Gotham Narrow Light]*Network &#8211; 2x 1GB network adaptor *[/FONT][/SIZE][/SIZE][/FONT]
 
[FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1][FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1]***Storage ***[/SIZE][/FONT][/SIZE][/FONT]
[FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1][FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1]*One datastore (100GB) *[/SIZE][/FONT][/SIZE][/FONT]
 
[FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1][FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1]***Network ***[/SIZE][/FONT][/SIZE][/FONT]
[FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1][FONT=Gotham Narrow Light,Gotham Narrow Light][SIZE=1]*One VLAN for carrying virtual machine traffic; one VLAN for carrying management traffic *[/SIZE][/FONT][/SIZE][/FONT]
 
 
Is Ubuntu Cloud similar in the way you set up a virtual environment with multiple nodes?
I can give 'em both a try, to get to know the theory behind.
ESXi can run on as little as 2GB RAM/node - The minimum requirements are just for optimal performance. I run a 2GB RAM server (seperate from my normal ones) at worldstream with ESXi. Those specs look more like the ones that you would use to create a HA cloud cluster, not a normal cheaper one.

---

