---
title: "IP Address Questions"
date: 2007-06-07
forum: Server Platforms
---

### Post by blmartin777 on 2007-06-07
I have kind of a dumb question. I am setting up a static ip with my service provider for my server. Would it be better to get seperate ip's for the server and my home computer? Or would I be fine running 1 ip through my netgear router to the server and my home computer?

Thanks

---

### Post by Frosty Cold Drink on 2007-06-07
> **blmartin777 said:**
> I have kind of a dumb question. I am setting up a static ip with my service provider for my server. Would it be better to get seperate ip's for the server and my home computer? Or would I be fine running 1 ip through my netgear router to the server and my home computer?

Thanks

If you are going to server FTP on the server or use VoIP, you are probably better off with 2 IP addresses.

---

### Post by reckless2k2 on 2007-06-07
depending on your up or down stream, one IP can be fine. i run a web, ftp, mail, and voip server box on 1 ip with no problem. i don't use a static purchase from an ISP either. i use a DDNS.

---

### Post by blmartin777 on 2007-06-07
My buddy has a business as a Graphic Designer and Web Sites. I am going to host his sites that he creates. I figured a static was more reliable plus I need a decent amount of speed?

---

### Post by Frosty Cold Drink on 2007-06-07
> **blmartin777 said:**
> My buddy has a business as a Graphic Designer and Web Sites. I am going to host his sites that he creates. I figured a static was more reliable plus I need a decent amount of speed?

Static vs dynamic IP won't affect speed. DynDNS is pretty quick, and I'd assume the other similar services are as well.

You'll be fine with a single, dynamic IP address, but having two static ones is easier in many respects. You have less NAT traversal issues, no data port for FTP complications, etc...

---

### Post by kilroy423 on 2007-06-07
The static address is just given to your house....why can't you get yourself a good router and then just split one ip for each computer then use forwarding in the router's software to forward the correct ports to the computer you desire to receive them.....the router that I use in the Linksys WRT54g which is quite easy to administrate....I have run ftp, apache, couter strike server, and teamspeak server on one connection with all different computers(eats bandwidth but gets the job done)



dan

---

### Post by blmartin777 on 2007-06-07
But from a business standpoint. Which is the best way to handle this. I want to expand to other services as things get going so I though a static ip for the server would be a more stable setup? Thanks for all your help.

---

### Post by Frosty Cold Drink on 2007-06-07
> **kilroy423]The static address is just given to your house....why can't you get yourself a good router and then just split one ip for each computer then use forwarding in the router's software to forward the correct ports to the computer you desire to receive them.....the router that I use in the Linksys WRT54g which is quite easy to administrate....I have run ftp, apache, couter strike server, and teamspeak server on one connection with all different computers(eats bandwidth but gets the job done)[/QUOTE]

There are lots of reasons why. Yeah this would work, but there are still lots of reasons why.


[QUOTE=blmartin777 said:**
> But from a business standpoint. Which is the best way to handle this. I want to expand to other services as things get going so I though a static ip for the server would be a more stable setup? Thanks for all your help.

From a business standpoint hosting at home is just a bad idea in general. Well, you *could* but you would want a seperate, higher quality link, and other stuff depending on the business.

---

### Post by blmartin777 on 2007-06-07
> **Frosty Cold Drink said:**
> From a business standpoint hosting at home is just a bad idea in general. Well, you *could* but you would want a seperate, higher quality link, and other stuff depending on the business.
What exactly do you mean by a higher quality link, and other stuff. I am looking for all the feedback that I can get before I actually start it. 

Thanks

---

### Post by Frosty Cold Drink on 2007-06-07
> **blmartin777 said:**
> What exactly do you mean by a higher quality link, and other stuff. I am looking for all the feedback that I can get before I actually start it. 

Thanks

Typical resedential connections are
[LIST=1]
[*]Slow to upload (your low upload speed is someone else's max download speed, if they are the only one using the link)
[*]unstable, often dropping for a fraction of a second to a few minutes (most people don't notice)
[*]Not guarenteed to be up, with service calls happening in a couple of days insted of a couple of hours
[*]not allowed to serve data to the general public (check your ToS)
[/LIST]

---

### Post by blmartin777 on 2007-06-07
> **Frosty Cold Drink said:**
> Typical resedential connections are
[LIST=1]
[*]Slow to upload (your low upload speed is someone else's max download speed, if they are the only one using the link)
[*]unstable, often dropping for a fraction of a second to a few minutes (most people don't notice)
[*]Not guarenteed to be up, with service calls happening in a couple of days insted of a couple of hours
[*]not allowed to serve data to the general public (check your ToS)
[/LIST]

What is a fast enough upload speed? I was looking at getting a business line. Lets say I use a residential line can I get in trouble?

---

### Post by Frosty Cold Drink on 2007-06-07
One couldn't really define "fast enough". You will need to guess your max concurent users at any given time, bandwidth required to serve them up in a reasonable amount of time, (a few seconds at most for complete page load), and throw yourself a little stretchign room.

If you use a resedential ACCOUNT, you could poitentialy get your service cut off, and yourself banned from the ISP. If you have a business account, that's far less likley to happen, but you still have to deal with the link quality issues.

---

### Post by blmartin777 on 2007-06-07
At start we are not talking about a lot a concurrent users. I will have at lease 756 upload but maybe 1gb or more depending on price and were I go with it?

---

### Post by blmartin777 on 2007-06-07
Is 756 or 1gb fast enough or should I be looking for faster?

---

### Post by Frosty Cold Drink on 2007-06-08
There is no way to tell without profiling browsing sessions.

---

### Post by blmartin777 on 2007-06-08
Is 756 or 1mb a decent speed at all? If you get a web hosting package form godaddy what are there speeds? Way above what I have?

I have been told that should be a good speed.

---

### Post by Mr. C. on 2007-06-08
Are we there yet?  Are we there yet?

blmartin777, your questions are similar to "Is it cold out?  Should I wear a jacket?"

Only *you* can answer these questions by knowing what your own needs are.  A "decent speed" or "fast enough" for one is completely unacceptable to another.

Figure out specifically what you want to be able to do, and then you can get some better feedback.

MrC

---

### Post by blmartin777 on 2007-06-08
I see your point I am spinning in circles. I am not going to do this on a big scale to start. Just some minor sites with low traffic. Thanks for the replies.

---

