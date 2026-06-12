---
title: "Could a cluster of old desktops with a 6M DSL connection make a good MMO server?"
date: 2010-09-18
forum: The Cafe
---

### Post by Dustin2128 on 2010-09-18
I'm working on a FOSS mmo with some friends of mine, with me and 2 others working on the technical aspects (everything that the player won't see). So far its going well, but I just ran into one obvious problem: the server. I don't know what kind of specs you need for a good game server, can't afford a commercial one, and I don't know if my home connection, which faster than my friends' (they all have satellite or low-end DSL) is good enough anyway! The cluster was something I was planning to do when I get some spare time anyway. 4 desktops: 2 ancient P3s and 2 P4s, with a combined 3GB RAM and 500GB of disk space, most likely running dragonfly BSD, all being controlled by my P4 desktop. My goal is to be able to support about 100 people playing simultaneously on a decent sized game map with graphic detail comparable to regnum online. Is this practical without upgrading to a better ISP? And do I have to use my cluster as a server or can I just use a single desktop?

---

### Post by never say never on 2010-09-18
There are a lot of variables unanswered in your question really, so I am making some assumptions here  but there are a lot of things you need to consider.

1. Internet Connection.  
I seriously doubt that a DSL connection will be satisfactory to run a server from.  There are several reasons for this 
     A. Probably violates your TOS (Terms of Service) to run a server.
     B. Up speed is probably more like 256k, 384k, or if lucky 512k.
     C. You should really have a static IP if you are going to have a server
         net.  Anything else just won't have the reliability needed.
     D. You will want to be with a tier 1 or 2 provider to reduce latency.
     E. best practice would be to have at least 2 connections on different 
         provider networks for reliability.

2. Server
You will probably want to invest in a server, even if it is a home built one to start.  For $500 - 700 you can build a fairly decent system that can handle database, number crunching and streaming.  Get LOTS of RAM.
     A. This will largely depend on what kind of number crunching you 
         will have to do.
     B. A cluster of 4 sub par systems will probably not be up to the task 
         of running your database, crunching numbers and streaming data.
     C. Power consumption will eat you alive in costs related to powering 
         and cooling the equipment.
     D. Sub par drives will reduce the ability to handle the database efficiently.
     E. Number crunching will likely be painfully slow on a  P3.



For a more helpful response, we will need a lot more information.  Such as what is your average outgoing bandwidth (You can goto DSL reports and run some tests to get speed averages as well as latency). 

Tell us more about the amount and types of data you plan to be pushing to players.  I am guessing you will need 20 - 30 k per connection (maybe more depending on how tight you code is).  You should plan on not going above about 75% of you outgoing bandwidth so if you have 512k up that would mean you should stay below about 384k (or about 10 user if it is a 30 k connection.).  The size of the packets, and protocol will play a part here too, UDP or TCP?  Encrypted?  

Check out your area for a Colo (Co-Location facility) that will have cheaper bandwidth and you won't worry about speed, cooling, power outages . . .  Make sure you get one with multiple Tier 1 or Tier 2 providers (as I stated above this helps to keep latency low for more people).

Good luck, let us know some more details and we can try to nail down more specific numbers.

---

### Post by Dustin2128 on 2010-09-18
thank you very much for the detail of your post, though I suddenly feel I may be a bit in over my head... as far as what I can answer, if I need 20-30k per connection, my service definitely won't cut it. As for a co-location facility, I'll probably have to drive about 50 miles out of my way to find one, and what kind of prices are we talking about? I'm thinking about how to pay for upkeep while keeping the community development part and I'm not coming up with much. As far as building a server goes, how much RAM would be enough?  8GB? 12?

---

### Post by never say never on 2010-09-19
I am using 20 - 30 k as a guess.  Since I haven't seen your code, I just looked at the average for most MMO's.  Depending on what you install with the game  You might be able to trim that down a bit, but if you have to send maps, NPC figures and Player stuff it could go higher too.  You will need to look into how much bandwidth you are using with your code.

The amount of RAM (and disk storage) needed will depend on the size of your database . . .  Again without know anything about your back-end code, there isn't any way to say what you need.

As for the Colo, you should only need to go their once to install and set up your server, after that you should be able to remote in to do updates and maintenance.  The cost will vary greatly depending on where you are located, the number of rack space required for your server, the power used by the server, and finally the bandwidth used by your system. Probably a minimum of $200/Month.  

You could look into a dedicated server or a cloud service (Think Amazon EC2 Cloud here).  That will come with almost no up front costs and lower monthly costs that are based on how long the server is 'on' and how much bandwidth is used.  Generally speaking this would be a short term solution until you could afford a dedicated server or to Colo a server of your own.  This may be the best place to start because during building and testing you can turn it on and off and only pay for what you use.  Also if you need more you just say give me more and pay the rate.  Depending on server size needed and bandwidth could be $60 - $500+/mo for 24/7.

Really the fist things you need to nail down are, what kind of compute power your server will require per user, and what kind of bandwidth per user, then you can figure out what you need.  You are the only one who can answer that, because you are the one writing and testing the code.

---

### Post by Dustin2128 on 2010-09-19
thanks again for the detailed reply. The coding's barley even begun honestly, there wouldn't be much to show you. Unfortunately, those kinds of prices are pretty well outside my range. I'm just kind of thinking outside the box here as far as ways to get around having to own a dedicated server, but would it be possible to have the game data-load process work as some sort of peer to peer system like bit torrent? It would grab user data such as level and location from the archive run by me, seeing as that wouldn't necessarily take that much up-speed or bandwidth, but it would grab the maps, models, and other such data from other user's clients. The main disadvantages I can come up with are that it by default requires a moderate sized userbase to start with, and seeing as its FOSS, the people might modify the data stored on their node, thus modifying it for the whole game. No need to take the above seriously ;), I'm just brainstorming.

---

### Post by samb0057 on 2010-09-19
I know colocation with FDC Servers gives you quite a bit of bandwidth for the price you pay.

---

### Post by juancarlospaco on 2010-09-19
You use TCP or UDP?

---

