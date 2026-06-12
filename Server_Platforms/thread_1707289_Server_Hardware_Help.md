---
title: "Server Hardware Help?"
date: 2011-03-15
forum: Server Platforms
---

### Post by Nate204 on 2011-03-15
Hey guys,

I just wanted to quickly ask if anyone could give me a few suggestions on possibly upgrading my hardware?

I know this isn't strictly Ubuntu related, although I want to run Ubuntu 64 on it~ I thought I would ask you as the community.

Here is the Mother Board in google:
[se7501wv2s intel]("http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=CPU+width+32#hl=en&sa=X&ei=1TN_TaCTO6SD0QGkq8WDCQ&sqi=2&ved=0CBgQvwUoAQ&q=se7501wv2s+intel+compatible+processors&spell=1&bav=on.2,or.r_gc.r_pw.&fp=98286c98e5a0f890")

I run a small game server, with four SCSI 15,000 HDD on it. It's set to RAID 0 atm... I'm not much happy with that.

Anyway, I was thinking about replacing the processors on it to something that would replace the 32 bit restriction it's current Xeons have. I've already looked it up and found out that yes, they are only able to run 32 bit. They where one of the first Xeons out if I'm not mistaken. 

I have someone willing to donate, but wants me to "Think Big" as he puts it. This was the only way (I could figure) to speed up our server, and work around our current bottle necks.

We also run 5GB DDR EEC RAM, but like I said before, we can only use about 1.5GB dedicated to one process at a time. 

I'm new to Xeons, so any suggestions would be awesome!
Thanks guys for the input!

 - Nate

-----
Edit: The MoBo manual shows it was built in 1998-2002 I believe. I'm open to all suggestions, but "buy a whole new unit" might not be as helpful =) Although It will always be noted and appreciated!

---

### Post by rubylaser on 2011-03-15
Here are a few questions for you.  What's your budget?  How many users will be accessing the server at the same time?  Does form factor matter (rackmount, Full ATX, minitx, etc)? Do you want to run 64bit Ubuntu solely to access more RAM, or is there another reason? Do you really need ECC memory?  If not, you could go with a regular i5/i7 and save a ton of money for comparable performance. Finally, RAID0 as you can imagine, is as bad as it comes if you want reliability.

---

### Post by Nate204 on 2011-03-15
> **rubylaser said:**
> Here are a few questions for you.  What's your budget?  How many users will be accessing the server at the same time?  Does form factor matter (rackmount, Full ATX, minitx, etc)? Do you want to run 64bit Ubuntu solely to access more RAM, or is there another reason? Do you really need ECC memory?  If not, you could go with a regular i5/i7 and save a ton of money for comparable performance. Finally, RAID0 as you can imagine, is as bad as it comes if you want reliability.

1. Unknown Budget ATM. I'm trying to get Ideas for those who donate.

2. 10-20 users at the same time.

3. Here are some Images of the case, I'm not sure what form factor it falls under. (See Below) 

[IMG]http://online-self.com/blog/wp-content/uploads/2011/02/IMAG0352-1024x768.jpg[/IMG]

[IMG]http://online-self.com/blog/wp-content/uploads/2011/02/IMAG0350-1024x768.jpg[/IMG]

4. I wanted to run Ubuntu 10.4 64 bit just to access the extra RAM. ATM we can only dedicate 1.5gb to our game server. It will get to that point, and stop. The rest of my RAM just sits and does nothing. It was a bigger reason for wanting 64bit. 

5. I have ECC because it's what the boards manual said It required. You can check it out here: [http://www.andovercg.com/datasheets/intel-SE7501WV2-motherboard-specs.pdf](http://www.andovercg.com/datasheets/intel-SE7501WV2-motherboard-specs.pdf)
I would like to do something like that, but I'm not positive If I could. That sounds like buying a whole new Rig.

6. I know. Raid 0 is a fail rail for me. If I update the processors, I'll look into switching this. What Raid would you recommended? 

Thanks again for your input!
I appreciate anyones feedback!

 - Nate

---

### Post by Nate204 on 2011-03-15
Bump?

---

### Post by rubylaser on 2011-03-15
That's a rackmount case. That hardware is so old, that if you want to upgrade, you're really going to want to upgrade :)  If you don't need a rackmount server, you should be able build a quad core (AMD because of your budget) in an ATX case with a new motherboard, 8GB of RAM, PSU, and case for around $450.  You'll still need to add hard drives, and a GPU.  Without knowing your budget, this is kind of a wasted exercise.

I personally would wait until the fixed motherboards are released for the Sandy Bridge Intel's and get one of those.

---

### Post by tgalati4 on 2011-03-15
Bumps should be reserved for 24 hours or more.  

Xeon's (32-bit or 64-bit) are workhorses.  I doubt that you are really stressing them.  The PAE kernel in the Ubuntu server editions will automatically detect RAM beyond 4 GB.

If you really want to upgrade, you can find plenty of Dell PowerEdge and HP Proliant rack servers that companies discard when the warranty expires.  These machines can be found for $300 to $500 and are typically 5 to 7 years old.

It's not clear what your performance bottlenecks are, so it's hard to make any recommendations.

---

### Post by Nate204 on 2011-03-15
> **tgalati4 said:**
> Bumps should be reserved for 24 hours or more.  

Xeon's (32-bit or 64-bit) are workhorses.  I doubt that you are really stressing them.  The PAE kernel in the Ubuntu server editions will automatically detect RAM beyond 4 GB.

If you really want to upgrade, you can find plenty of Dell PowerEdge and HP Proliant rack servers that companies discard when the warranty expires.  These machines can be found for $300 to $500 and are typically 5 to 7 years old.

It's not clear what your performance bottlenecks are, so it's hard to make any recommendations.

Sorry for such an early bump.

I guess my bottlenecks are my RAM not being fully utilized. Java JDK for my game server only allows for 1.5GB of ram to be allocated to it on 32bit. With 64bit, the sky seems to be the limit. This server is dedicated to running just this one process. I have at least 3GB or RAM just sitting and not being used.  

I wish I could toss out a dollar amount, but If you have suggestions, think about a budget buy. Something low and simple. 

I also appreciate the info on my server being old. I bought it for cheap, and I wanted to get my hands one something other than a dedicated desktop/server.

I have a member of the server asking how much it would cost to update our hardware to increase performance, and this is where I'm stuck. I'm really not sure what to offer him. 

Thanks again guys for your insight. I greatly appreciate it!

---

### Post by tgalati4 on 2011-03-15
So the real problem is the JAVA JDK not allowing greater than 1.5 GB per instance.  Since JAVA is open source (most of it anyway), is it not possible to recompile it to use the PAE kernel?  I don't see why 32-bit vs 64-bit would make a difference since the PAE handles the memory map.

If you can't get around the JAVA limitation, then you would have to upgrade to 64-bit architecture.  Check craigslist.org for poweredge or proliant servers--there are lots of them floating around.

I doubt that your motherboard would support 64-bit Xeons--but you never know--you would have to do some research.

---

### Post by Nate204 on 2011-03-16
> **tgalati4 said:**
> So the real problem is the JAVA JDK not allowing greater than 1.5 GB per instance.  Since JAVA is open source (most of it anyway), is it not possible to recompile it to use the PAE kernel?  I don't see why 32-bit vs 64-bit would make a difference since the PAE handles the memory map.

If you can't get around the JAVA limitation, then you would have to upgrade to 64-bit architecture.  Check craigslist.org for poweredge or proliant servers--there are lots of them floating around.

I doubt that your motherboard would support 64-bit Xeons--but you never know--you would have to do some research.

"Socket 604 interface."

If I'm not mistaken, I believe this is they type I would need.
I found it when looking up my MoBo on google search.

[http://reviews.cnet.com/motherboards/intel-server-board-se7501wv2/4505-3049_7-20723440.html](http://reviews.cnet.com/motherboards/intel-server-board-se7501wv2/4505-3049_7-20723440.html)

Do I simply need to find a Xeon that will support this socket type that is 64bit compatible?

---

### Post by BkkBonanza on 2011-03-16
You would need to co-ordinate info from Intel CPU, chipset and mainboard as any of these could limit the possibility.

I would also look at the cost of using Amazon EC2 for your application. You can test it for almost nothing. Nowadays I much prefer this method as it gets away completely from the headache of managing hardware, upgrades, failures and scaling up when load is high. I know it's way off base for your question but if you don't look at it then you don't really know what you can gain by leaving hardware behind. Some very large sites are hosted on EC2 now and according to their reports they save tons by not dealing with hardware any more.

It is especially good if you have periods of high use and other times with light use as with a bit of configuring you can bring up and down servers to handle load.

---

### Post by Nate204 on 2011-03-16
> **BkkBonanza said:**
> You would need to co-ordinate info from Intel CPU, chipset and mainboard as any of these could limit the possibility.

I would also look at the cost of using Amazon EC2 for your application. You can test it for almost nothing. Nowadays I much prefer this method as it gets away completely from the headache of managing hardware, upgrades, failures and scaling up when load is high. I know it's way off base for your question but if you don't look at it then you don't really know what you can gain by leaving hardware behind. Some very large sites are hosted on EC2 now and according to their reports they save tons by not dealing with hardware any more.

It is especially good if you have periods of high use and other times with light use as with a bit of configuring you can bring up and down servers to handle load.

That's a good Idea. I like it, but I'm very new to it. Looks like I've got some reading to do...

---

### Post by BkkBonanza on 2011-03-16
I think at first it appears harder than it actually is probably due to new ways of doing things. Each application/site is different as to whether it would be beneficial. It does make it easy to split up load onto several servers. You pay for bandwidth, storage and cpu hours used so you'd have to compare to what you pay now for co-locating and connection.

You can move any static content to S3 (or a second server or VPS) and that takes that load off your server (whether your current one or new one). 

Looking into caching dynamic content is also a route that many forget to consider as another way to avoid big upgrades is to improve the efficiency of the current setup. Often a few small improvements to caching (using memcached or similar apps) can make a big difference to site load as can a few improvements to mysql optimizing. Unless you've already done that, you'd be surprised how much improvement can be made.

And finally, my favorite, is looking at whether you can replace Apache with a much lighter and more efficient Nginx web server. I don't use Java so don't know the details of how it works with Nginx but I do know that running a dozen instances of Apache takes tons more resources compared to a single low footprint Nginx one. 

I guess I'm just saying that a hardware upgrade isn't the only way to fix performance problems. One place to start is using **htop** (or dstat) to monitor what processes are consuming resources when the site slows down. Another is to turn on query logging in mysql as that can often show you which terrible queries are wasting cpu time and can often be vastly improved by adding a few appropriate indexes. I've heard of admins reducing 30%+ load off by making a small change like that.

---

