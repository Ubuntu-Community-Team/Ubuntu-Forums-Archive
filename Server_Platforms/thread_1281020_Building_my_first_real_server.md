---
title: "Building my first real server"
date: 2009-10-02
forum: Server Platforms
---

### Post by ConXtionS on 2009-10-02
Hello All,
 
The short version is
 
I want to build a server for use at my campground.  We have crappy tv so I plan on using mythbuntu backend to grab some tv, then I want to store the tv on a server, and be able to watch it at the camp ground.
 
I would also like for the server to be able to host a few web pages, maybe a teamspeak server (incase I manage to get high speed net TO the camp ground) and to have it all fed from a walled garden so I can control where lil johhny is going to.
 
I have an old sempron 2800 mb ready for the job.
 
I also have a 200 and 300 gig hard drive to host the files
 
Please remember I am a total linux noob, but I did just win a bet as I have mythbuntu running around just llike windows media center in less than a week.   So I am TRAINABLE....
 
What do you all think I need to start my lil project???
 
thanks in advance
 
Jim

---

### Post by badger_fruit on 2009-10-03
Jim
This sounds like fun!
Apache for the Webserver, dead easy to get up and running, PHP and MySQL.
Also known as a "LAMP" setup, lots of docs out there on the interwebz to help you get going!

Myth backend will do the job capturing/recording the TV, you just configure the clients to point to it.

Oh, you'll need to set the Myth server with a static IP address so you can always find it on the network and erm, that's about it.

Can't comment on Teamspeak though, sorry.

What do you mean by "to have it all fed from a walled garden so I can control where lil johhny is going to"?

If you mean controlling internet access, Squid's the baby to do this although be nice to it as it's got many arms and a vicious mouth.  I have little experience with Squid but again, there are plenty of docs which will get you going.

Have a lot of fun !

---

### Post by ConXtionS on 2009-10-04
> **badger_fruit said:**
> Jim
This sounds like fun!
Can't comment on Teamspeak though, sorry.
 
What do you mean by "to have it all fed from a walled garden so I can control where lil johhny is going to"?
 
If you mean controlling internet access, Squid's the baby to do this although be nice to it as it's got many arms and a vicious mouth. I have little experience with Squid but again, there are plenty of docs which will get you going.
 
Have a lot of fun !
 
Yes... I mean controlling little johnny on the net.  I "BELIEVE" I will be successful in getting a wireless ISP to get a signal to the campground.  However much of our state is still pretty backward where the net is concerned so the amount of bandwidth will be small 256 or 512Kb maybe.  Also the total amount of gigs allowed will be small as well.   So, the last thing the camp ground owners would need would be for "lil johnny" to down load a swarm of porn or something and ruin it for the rest of us.
 
As for the fun, so far ubuntu has been a BLAST!
 
The guys here on the forums are both INTELLIGENT and funny and seem more than willing to help a guy out just to be nice.
 
If I do manange to pull this all together it is my hope to some how fit it all on one cd, so that other people dont have to start at the beginning like I am doing.   Hopefully I will be smarter by then tho.
 
thanks for the help
 
I am downloading the ubuntu server software now and will be setting up a nice new lamp next week.
 
Be well sir
 
Jim

---

