---
title: "Linux internet cafe software?"
date: 2007-01-29
forum: The Cafe
---

### Post by doobit on 2007-01-29
Has anyone here tried any Linux Internet cafe management software that they could recommend? It could be free or for purchase. I don't mind paying for it if it's very good.

---

### Post by xmastree on 2007-01-29
When I used to run [CG Internet](http://www.cginternet.net) I experimented with [cafesuite]("http://cafesuite.net"). It ran under wine, but couldn't lock the remote computers. It was ok for calculating time/charging rates, but that was all.
The authors were forever saying they were working on a linux version though...

---

### Post by doobit on 2007-01-29
> **xmastree said:**
> When I used to run [CG Internet](http://www.cginternet.net) I experimented with [cafesuite]("http://cafesuite.net"). It ran under wine, but couldn't lock the remote computers. It was ok for calculating time/charging rates, but that was all.
The authors were forever saying they were working on a linux version though...

I checked them out. It says "paused" at 5% on the Linux development. If I get some time I'll download and try out some of the trial ones, but I'm hoping someone here has already tried some and can give me recommendations.
Thanks!

---

### Post by doobit on 2007-01-29
So far the only actual Linux package I've found is Zybacafe. Has anyone used that one?

---

### Post by sabitha on 2007-02-17
> **doobit said:**
> So far the only actual Linux package I've found is Zybacafe. Has anyone used that one?

Introduction: 

ZybaCafe is a powerful and complex application with several parts. Thus a bit of careful planning is required before starting the installation.

This short guide will help you download and install the various components and set up your internet cafe.

The free/open-source ZybaCafe comprises everything needed to run a Linux based internet cafe with it. Additionally clients for offering a wifi-hotspot or windows-client machines as well as multiple plugins for interacting with other programs are available from getopenlab.com  and the list is always growing.

anyone can help with zybacafe instalalation or HOWTO please...............

---

### Post by nicoladimaria on 2007-04-02
bump
any news ?

EDIT:
now zybacafe is called
OutKafe
[http://outkastsolutions.co.za/outkast/index.php?option=com_frontpage&Itemid=1](http://outkastsolutions.co.za/outkast/index.php?option=com_frontpage&Itemid=1)

---

### Post by peterroots on 2007-08-08
Has anyone actualy got OutKafe to work?
I am using kubuntu and failing at every step!
Installing Outkafe was a minor challenge as it was missing some dependencies but my big problem was getting Postgresql to work!
first off it seemed to work but would not talk to the clients and after messing it up I tried removal and reinstallation - this totally messed up everything and after many retries I reinstalled Kubuntu from the start.
postgresql now talked to the server and phppgadmin but not the clients - first problem was not installing postgressql common on the clients so they did not know about connecting to the server.
then edited /etc/gpstgresql-common/user_clusters to tell it about the server and database for outkafe
nothing doing
i edited pg_hba.conf tying various settings ending up with 
host   outkafe    outkafe    192.168.0.0/24 trust
but it still would not talk to the clients
edited /etc/postgresql/8.2/main/postgreql.conf
seemed to be only listening to localhost so uncommented the relevant line and added 192.168.0.0/24 with a comma after 'localhost'
now outkafe server or phppgadmin could not connect to database!
tried '192.168.0.0/24' instead of 192.168.0.0/24
Still nothing
gave up on nice careful security altogether and replace my list with '*' - now everything and anyone can talk to the database
GREAT I though the client talks to the server, I can sell tickets, log in and out as a customer or staff member, kick customers off adn see how much time they have left
WOW
Oh Oh - the time does not seem to count down on the client (it does seem to on the server if you press the refresh button
The client is popping up messages occasionally OKln unable to start new thread - clicking ok does nothing, cancel shuts the client software down and leaves the customer logged in
Anyone got any ideas?:confused:

---

### Post by peterroots on 2007-08-08
So Progress of sorts
I went to lunch and the timer is now working!
Unfortunately on leaving a client running logged in back came the OKln error about not being able to create a new thread when I tried to log out.  The server recognizes that the customer has logged off but the client will not return to the login screen or display the correct time on the timer.  The client computer is still usable and appears logged in by the customer.
Still:confused:
but more:) than I was

---

### Post by peterroots on 2007-12-05
Things are now working rather well thanks to a few tweeks by the OutKast folks (thanks VJ) and their idea of using devilspie to keep the cafe client windows on top on the stack of open windows

---

