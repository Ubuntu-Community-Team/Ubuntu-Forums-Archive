---
title: "Launched an iPhone app and server crushed today, need help with Apache"
date: 2008-07-12
forum: Server Platforms
---

### Post by jf1991999 on 2008-07-12
We are a bunch of mobile app programmers and have minimal experience in hosting high availability servers.  We just launched a baseball app on iPhone that lets you follow any of the games.  It is pretty cool but we were not expecting the traffic we are getting.

We have the latest install of the desktop Hardy Heron on a 2x dual core opteron 275, 4Gb, 80Gb IBM server.  It is doing nothing much more than running apache2.2.3.  The server is installed in a San Jose colo with a 1Gb fiber pipe so bandwidth should not be an issue.

Everything crashed badly today around 7pm EST and our 3 backup servers went down as well.  We tinkered with the Apache2 conf file increasing the Max Clients to 400 and threads per child to 25.  After a restart everything was good for about 1 hour then the machine itself crashed.  Again all the backups that took the load also failed.

Editting the apache2.conf, I have increased the Server Limit to 40, min maxspare threads to 256/512 threads per child to 64 and Max Clients to 2560.  It is running ok now but it is getting late in the night so the load is probably off a bit. 

Can anyone advise me on what we can do better here or where I can go for more help?  The documentation wasn't very helpful.  I am guessing that we had a lot of iPhone users hammer us badly and it will likely repeat tomorrow.

The server cpu avg is only around 5% and 75% memory free so looking at the machine you wouldn't think there would be a problem.

Thanks in advance.  The app name if anyone is interested is LiveSportz.

---

### Post by promodus on 2008-07-12
Interesting, and unfortunate to hear.

I'm not an expert but how I'd approach the situation would be to have:

Load balancing servers, possibly even apache reverse proxy? Where if your site was hammered, you'd only hand over the amount of load the servers can handle. More load add more servers.

The other option to possibly consider is Akamai services.
[http://www.akamai.com/](http://www.akamai.com/) 
These guys handle a lot of major websites out there, including apple & microsoft.

Please share your trials and tribulations. Book marking the thread.

---

### Post by jf1991999 on 2008-07-12
Thanks for your comments.  We do use Akamai today for another oart of our business, but the files beign served up for the iPhone app are changing rapidly so akamai can't help here.

The load balancing and more server approach is definitely the longer term way to go, however I feel that if we tuned Apache and the TCP connections better we would get a lot more performance.

The files we are serving a tiny (2k), the problem seems to be the number of simultaneous connections.  I can't find anywhere that tells me how many people can connect and pull files from apache over a 60 second period if tuned correctly.  The CPU is not being hammered at all.  I read that there is a hard coded max of 20,000 maxclients.  Would it be bad for me to use this setting?  Why is the default only 150?

Could my issue also be with the OS running out of TCP connections?  This could have been the case as we couldn't VNC into the machine after the second crash although it was still alive.  Although it never recovered and we had to have it rebooted.

---

### Post by promodus on 2008-07-12
Some insight on wikipedia:

[https://wikitech.leuksman.com/view/MediaWiki_caching](https://wikitech.leuksman.com/view/MediaWiki_caching)

[https://wikitech.leuksman.com/view/Main_Page](https://wikitech.leuksman.com/view/Main_Page)

[http://meta.wikimedia.org/wiki/Wikimedia_servers](http://meta.wikimedia.org/wiki/Wikimedia_servers)

---

### Post by promodus on 2008-07-12
> **jf1991999 said:**
> We are a bunch of mobile app programmers and have minimal experience in hosting high availability servers.  We just launched a baseball app on iPhone that lets you follow any of the games.  It is pretty cool but we were not expecting the traffic we are getting.

We have the latest install of the desktop Hardy Heron on a 2x dual core opteron 275, 4Gb, 80Gb IBM server.  It is doing nothing much more than running apache2.2.3.  The server is installed in a San Jose colo with a 1Gb fiber pipe so bandwidth should not be an issue.

Everything crashed badly today around 7pm EST and our 3 backup servers went down as well.  We tinkered with the Apache2 conf file increasing the Max Clients to 400 and threads per child to 25.  After a restart everything was good for about 1 hour then the machine itself crashed.  Again all the backups that took the load also failed.

Editting the apache2.conf, I have increased the Server Limit to 40, min maxspare threads to 256/512 threads per child to 64 and Max Clients to 2560.  It is running ok now but it is getting late in the night so the load is probably off a bit. 

Can anyone advise me on what we can do better here or where I can go for more help?  The documentation wasn't very helpful.  I am guessing that we had a lot of iPhone users hammer us badly and it will likely repeat tomorrow.

The server cpu avg is only around 5% and 75% memory free so looking at the machine you wouldn't think there would be a problem.

Thanks in advance.  The app name if anyone is interested is LiveSportz.

I was starting to think about how to break down this problem to tune for performance when It dawned on me, need to understand a little more on the traffic & scripts being run.

What server side scripting are you using? PHP? Something else?
How many of these servers do you have?  is it just the one?
How many hits / sec where you getting when the server was giving out?
What is the typical payload size for each hit? 
Are you sure it was apache that gave out? Anything in your kern.log ?

---

### Post by windependence on 2008-07-12
Like promodus said, load balancing is what you need here. there are a nimber of ways to go about it. commercially you could obtain a netscalar appliance and load balance that way, or you could build some front end boxes using FreeBSD and maybe Vyatta, or CARP.

FWIW, I like to use FreeBSD when running high volume sites. If you look at netcraft.com, you will see most of the sites out there run BSD. There is a reason for that. Stability. I will put on my flame suit now. :)

-Tim

---

### Post by jf1991999 on 2008-07-12
The traffic is very simple.  A selection of about 50 static xml files with sizes from 300 bytes to 2k.  Each user will hit the server every 30 seconds and download 3 files on the first connection and then normally just 1 300 byte file every 30 seconds.  The xml is generated on another machine and the apache server grabs the files from a shared folder.

We only have this one server today however we have several others that we could spread the load to.  My main concern is working out how we get the most out of each individual server.

I am not the most technical person to be checking the kern.log, however it could well be that something else is failing.  The fact that I was unable to VNC into the machine 30 minutes after switching all the load away was strange.  I would have thought the connections would have timed out and the machine would have gotten back to normal.  I needed to call the colo and have it rebooted.

How can I monitor total connections / hits per second?

I have changed the apache settings to have a MaxClient of 6400 with Maxserver 100 and 64 threads per child.  There is no load right now and the first games start at 1:00pm E.  Yankees at Toronto, so likely some iPhone users :)  Hope I don't let them down although I am a red sox fan that hopes the cubbies can do well this year.

---

### Post by promodus on 2008-07-12
Each user will hit the server every 30 seconds to download 3 files...

If you have a thousand people, that server will have some load that's for sure. 

3 * 1000 / 30 = 100 hits a second. 

If you where to do that all day, that would be 8.5 million hits in a day.

Your CPU can handle that apache wise. I'm not sure if you have a database on that server, also. 

Is the server serving static files only?

For hits per second, that should be in your apache logs.

---

### Post by jf1991999 on 2008-07-12
I have found some interesting reading on this topic. [http://www.stdlib.net/~colmmacc/Apachecon-EU2005/scaling-apache-handout.pdf](http://www.stdlib.net/~colmmacc/Apachecon-EU2005/scaling-apache-handout.pdf)

We are serving only static files with no database.  I have changed the settings as outlined in the above document.  It appears that we should be able to handle a substantial number of connections, although I am worried we will run out of memory.

---

### Post by ixus_123 on 2008-07-12
What was the reason the data center staff gave that the server fell over and died?

Was it out of memory?

I'm not an expert in setting up apache but have worked with customers who experience seasonal loads - one is a perfume supplier so valentines and christmas tey usuallly crash a lot, the other organises a major sporting event.

If both cases, either apache would die first due to being out of memory, if you didn't catch this fast, then the whole server would end up kernel panicing with out of memory errors.

Another problem is the amount of swap, once the server starts swapping due to these errors, the website is basically unuseable. It was much better for the server to crash so DC staff could reboot it than swap for 30 minutes.

As a short term solution, you might see if you can have more RAM in there for a month or two till all the excitement dies down.

FWIW: I'm not sure what setup Apple or O2 (UK phone company) have, but I would imagine load balanced clusters. Both of those sites went down as a result of the iPohne release!

As for your bandwidth, I'd guess you have 100mb max as you'll be limited by the switch in your cabinet and / or your firewall unless you're paying big bucks for a GB switch / firewall

---

### Post by windependence on 2008-07-12
I am sure bandwidth is not his problem, the server would not crash because of that and it sounds like he has plenty.

Why are you VNCing into the server? Are you running a GUI? If so, STOP! Turn off the GUI and use ssh or a web client to save those resources, although I don't think that is the cause of your crashes.

You need to take a good look at load balancing even if you don't run a cluster, it's not necessary anyway, but balancing the incoming reequests would distribute the load and save your servers.

-Tim

---

### Post by jf1991999 on 2008-07-12
I have installed Tcptrack and it is showing an average of 300 connections peaking at 400.  They seem to closing within  a second or 2 so this looks like it is working well.

We do have a 1G switch and fiber so bandwidth isn't an issue.

The machine crashed again around 2pm E, the colo guy said the screen was just blank when he put the monitor on with no keyboard response.  The machine is not totally dead as it appears to accept the initial VNC contact but there is no response after that.

It has been back up for about 90 minutes now and the memory used is creeping up slowly and is now 730M.  I only have 2G on this machine which is likely part of my problem.  The number of connections is fairly steady right now.

I am using VNC because I am pretty clueless when it comes to Linux and running servers.  Ubuntu made it easy for me to transition from M$.  The CPU is barely being pushed, averaging around 5%.

Do you think I should get another few Gig put into this machine on Monday?  Or would I be seeing the mem used going way up before a crash?
Thanks for all the help guys!!!

---

### Post by Thirtysixway on 2008-07-13
If it's a server I suggest no GUI.  it uses up a lot of ram that you could be using.  If the screen is blank, it could be the gui crashing.

Perhaps you could try a cacheing mod for apache, this would lighten the load a little bit as far as fetching files.

---

### Post by promodus on 2008-07-13
A video on youtubes growth and some scalability issues they had:
[http://video.google.com/videoplay?docid=-6304964351441328559](http://video.google.com/videoplay?docid=-6304964351441328559)

---

### Post by windependence on 2008-07-14
2 gigs is a bit thin for a server with that load. Thirtysixway is correct, it could very well be the GUI crashing has contributed to the problem. I would try 4 gigs and see how that plays out.

-Tim

---

