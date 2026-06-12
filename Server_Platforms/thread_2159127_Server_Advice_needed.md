---
title: "Server Advice needed"
date: 2013-07-01
forum: Server Platforms
---

### Post by milkboy007 on 2013-07-01
Hi,

One of my close friend had ask me to consult him about the posibility of building a server for a school he help to manage.
This school is a hybrid-funded (Gov funds + Private Donations) institution for lower income families, in a developing country.
Hence, [COLOR=#ff0000]their fund[/COLOR] for this project [COLOR=#ff0000]is[/COLOR] [COLOR=#ff0000]limited at best[/COLOR], and most-likely they will have to repurpose old PC (their best is a few core-duo chips) to build a server for the student and staff, using it possibly for all school needs (if possible). The school has exhausted the local IT company in which none want to volunteer/support (either pay for IT support or pay for hardware+power bills).

Their staff/teacher is less than a 100, and student less than a 1000 AFAIK, IT staff consist of teacher and student volunteers (both with very little it training and background, virtually no linux knowledge). their school system is a mess, running XP, all with viruses, using more power than people use.
I'm being brought in as an "volunteer" IT consultant, to give them informed choice for procurment in IT software and hardware, possibly might be brought in as an "volunter" IT support and manage the project. however, my real job is not in IT  (I'm work in the hospital If u wanna know),and i only have experience in building, running, and maintaining my on private server(single node). here in lies the problem i dont have technical expirence in "medium enterprise" server cluster, but i know the "know how" to built one.

I'm gonna advice him in using a assortment of Xubuntu machine + webserver with Open source app for all his need 
staff and student terminal will run on Xubuntu + Office and web browser
all other critical system will be on the server, running Mysql, Nginx, PHP, Pearl and ruby, nodeJS (ssh+ftp for remote control) on top of Ubuntu server
[OpenERP]("http://en.wikipedia.org/wiki/OpenERP")(accounting, Resource management,etc....), [KOHA]("http://en.wikipedia.org/wiki/Koha_%28software%29")(library system), [Moodle]("http://Moodle")(E-learning for teacher-student), [RACHEL]("http://www.worldpossible.org/rachel/")(digital library and self learning), and Maybe Wordpress/Joomla(CMS for the school).
[SIZE=3][B]
Question[/B][/SIZE]
for this i require info for the hardware requirements and google didn't help much

[LIST=1]
[*]for roughly 10 admin staff (acessing OpenERP), 1000 student and teacher (accessing moodle, KOHA, and RACHEL), with related parties(parents/teacher/staff) accesing Wordpress on the same server, what is best number of nodes of core2duo pc i need? 
[*]What setup is the best  in your opinion? 
[*] LVS running one app/virtual server, or one server for all app? 
[*]hdd RAID10 or others? 
[*]running High-availability or load balanced cluster? 
[*]any link and/or tutorial sites(for cluster webserver) you can give me? 
[/LIST]


Web/cloud sever provider is not a viable choice at the moment due to expensive and slow internet connection, with a bandwith cap.
maybe just for School website i can use free webhosting. other important system are to be access locally most of the time.
i also have other solution beside this one, a very simple solution (seperate system for all, 1 server for admin, 1 server for library 1 webhosted WP for news and announcement, etc...) but the point is, i need all the information before i can give him all the options possible.

also it would be helpful if you guys know the right place/website for cluster server? like i said IT is a hobby not my real job.

All opinion are welcomed and appreciated
thxs :KS

---

### Post by milkboy007 on 2013-07-02
none? seriously? :(
hopefully someone will reply when i check back later

---

### Post by sandyd on 2013-07-02
What I would reccomend is a cloud-style configuration through software such as openstack.

[LIST=1]
[*]It is easy to scale resources
[*]If one server app requires more CPU than a single computer can provide, the cloud will spread it out accross several computers
[*]If one server app requires less CPU than a single computer provides, the unused CPU wont be wasted
[*]If you run out of resources, you can simply add another computer
[*]If a server fails, it will fail over to the other servers, so there is no downtime
[/LIST]
The only qualm I have about this is the need to have a central NAS/SAN unit that does all the storage.

---

### Post by milkboy007 on 2013-07-02
> **milkboy007 said:**
> Hi,
[SIZE=3]**Question**[/SIZE]
for this i require info for the hardware requirements and google didn't help much

[LIST=1]
[*]for roughly 10 admin staff (acessing OpenERP), 1000 student and teacher (accessing moodle, KOHA, and RACHEL), with related parties(parents/teacher/staff) accesing Wordpress on the same server, what is best number of nodes of core2duo pc i need? 
[/LIST]

 


thx for the reply. and thx for the patience, as i mentioned i have very limited knowledge on building multi node server. :smile:
so i have very little knowledge about cloud. ill read about openstack as time permits.

however, the question above is yet to be answered. i just did a quick google search again and i still cant find any
i need to know how many pc i might need, before presenting openstack or any other similar solution as a viable options

anybody who have exp. working or did a similar job, for any person/company/institution/etc.... willing to share their knowledge/setup?
just maybe like along the lines of "I setup 5 nodes of (hardware) for my company with 20 staff and their (apps) & website with no. visitor"
just to give me some idea.

again thx sandyd for the reply

---

### Post by DJ_Max on 2013-07-02
Cloud has become an overused marketing term. A *proper* cloud configuration with openstack would require 6+ physical computers, dual gigabit cards and other hardware. You need separate controller, compute, storage and backup nodes.  Costing several thousands of dollars for the initial setup. Not to mention most people don't know how to maintain a cloud environment. 

I doubt you need to spend money on a cloud configuration. You can pickup one or two servers from eBay, for example, you can purchase a dual Intel L5420 for a couple hundred dollars. Add RAID1, Nginx Round Robin support with decent hard drives and you are good. 

Your numbers don't seem to outrageous, proper database and webserver optimization will go a long way. A single VPS or dedicated server can run what you need fine, I think you are over-complicating things. If you are with a host with decent uptime you won't have issues. If you want high availability, I would suggest you setup several VPS's remotely in different data-centers. Not much good if you have all your hardware goes down locally.

A simple setup, *nod*e could be dedicated or VPS

1 or 2 - node webserver/storage (Nginx, some sort of caching) round robin for two+ nodes
1 - node Database (MariaDB 5.5)
1 - node backup (NFS)

You can also also host everything remotely with a provider with a cloud infrastructure also.

---

### Post by rubylaser on 2013-07-02
Another option for hardware is a [Dell C6100 from Ebay]("http://www.ebay.com/itm/DELL-POWEREDGE-C6100-XS23-TY3-2U-4-x-HOT-PLUG-NODES-8-x-2-26GHz-QC-L5520-96GB-/111099492822?pt=COMP_EN_Servers&hash=item19de0bb9d6").  This is a very stout platform, and is very inexpensive for the hardware your are getting.

---

### Post by milkboy007 on 2013-07-03
soo...... building from a repurpose destop pc was imposible huh..........

the fact that the school doesnt have that much fund available, and it is in a developing country (its in "rural" indonesia, not the USA)
makes acquiring additional (specialized) hardware might prove difficult.

and as far as i know, the school do not buy new, the buy used Destop from a liquidation company, at below (used)market price in bulk every 2-3 years. i can ask that company if they sell used server, but it is highly unlikely that they do.
there may be some small donation , but i dont think its will be enough for a "real" server, by that i mean xeon based PC. it will probably just enough to improve the infrastucture. cables, router, and what not...

I guess it will be difficult to build a centralized server, with the current situation.

VPS or any other web based hosting is finacially imposible, for the school and its student.
but thx anyways DJ_Max. :)
 
(DJ Max like the game "DJ Max"?) loz....

P.S. a centralise server is what i personally want, since my friend has ask me personally to do most of the work, if he cant find a sponsor/volunteer to do it, and i cant really spend too much time building multiple system for the school without interfering with my job. plus is quite a commute to said school.

---

### Post by DJ_Max on 2013-07-03
Than I don't see why you can't run it off a single server with RAID. Drop Nginx/PHPFCGI and MariaDB. Though I would suggest against Wordpress.

---

