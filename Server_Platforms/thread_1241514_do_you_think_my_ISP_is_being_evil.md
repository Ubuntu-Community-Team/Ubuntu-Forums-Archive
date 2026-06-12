---
title: "do you think my ISP is being evil?"
date: 2009-08-16
forum: Server Platforms
---

### Post by hellarough on 2009-08-16
I have been running my server for about 7 months and I mostly have used it as a remote torrent box, personal FTP, and general file host. There are two domains from dynDNS pointing to my IP that are updated by my router. The problem is they are no longer accessible outside of my home network (they used to be about a week ago but now all i get is "Failed to connect"). I haven't changed much on the server at all but I think the last thing I tried to do was install iptables (and the server responded by telling me that it was already installed) after that I set up a crontab for updating, restarting, and cycling my log files. Since no port forwarding settings have changed on the router I am guessing that my ISP has gotten wise to my sites and done something to block outside access. Is that even possible? Wouldnt i just get a nasty letter telling me to stop hosting from a dynamic ip?

Other details i can think of:
since i decided to use dynDNS i have seen regular port scans on my router's log, a number of failed get requests or login attempts in my sites error log, and a few sucessful get requests in the access log. So i guess it could also be a security breach....but if it was a security breach why would this supposed attacker prevent http access?

---

### Post by nerr on 2009-08-16
Oddly enough, I'm suddenly experiencing the exact same problem.  Every port I try is blocked.  Even port 80!  What in the hell...?  Do you have Comcast?

---

### Post by ian dobson on 2009-08-16
hi,

So your using a normal home (ADSL/Cable) connection for a small web server. Check the contract/usage rules from your ISP.

You could try using telnet into port 80 from inside/outside your network to check if the problem is with your ISP blocking well known ports (80,25,22,21,110).

Regards
Ian Dobson

---

### Post by hockey97 on 2009-08-16
Most, ISP require you to buy their business line package instead of residential lines. The commercial line is more money and is a different line that was designed to service commercial services. Most ISP's won't allow you to run a server on residential lines 2 reason on why. One is that you could be a spammer/hacker causing trouble on the internet. The other reason is that you are doing something that their line isn't designed to handle what your doing. They design residential lines to be used with with low scale needs. No homes need to host servers of their own. They would only use it for the downloads from the internet and not uploads as much. So your server will have a low upload bandwidth and if you over exceed the residential line on the upload side of things you can crash their network. This is why most ISP's won't allow you to host a server on their residential lines but commercial lines they will allow you. They blocked those ports because they must of found some heavy loads on the network from uploading side of things on those port indicating people are using servers on their lines which aren't allowed too.

So look at your ISP'S terms and services agreement if they have a policy against servers then you can't use a server and they blocked you for good reasons. 

If you are on a residential line and they have restrictions on servers you can easily ask for a commercial/business line and that policy will go away but you will pay more then what you paid for residential internet. 
I think it's worth the money because you will also have prioity on internet issues. They will fix the commercial internet lines if a bad storm knocks them down compared to residential because business lines have a higher priority. 

To answer one of your questions. Yes the ISP can block your server from being seen from the internet. Their computers/servers/hubs/switches/ routes internet traffic to your computer/server. They can easily block ports that are susiously running servers or shows enough evidence you are using a server on their networks that is not authorized or against ISP's policy. 

From what I collected from your post. It seems you have an ISP that has a no server policy. They have logs of your activity and determined you are using a server of some sort so they blocked common server ports to prevent you from getting any traffic from the internet to your server. Like I said 2 reason, one is that you could be a hacker/spammer/security risk. Or could cause possible network crashes which will cost the ISP company some money to fix the problem.IN business time is money so the time down the cost will rise for the ISP. So they simply block the ports on your connection. From my understanding they can allow/or disable a port on individual connections. So when they block a port it work block everyone port. Just the individual ones.

Hope this helps.

---

### Post by hellarough on 2009-08-16
> **nerr said:**
> Oddly enough, I'm suddenly experiencing the exact same problem.  Every port I try is blocked.  Even port 80!  What in the hell...?  Do you have Comcast?

no...I have charter. I wish I had comcast still, it was much better than this crap int terms of service as for the billing dept. I think they were a bunch of incompetent fools.

As for the excessive uploads, all my torrents are auto-capped for upload speeds to avoid that and other than that I'd access from an outide IP about once a week just to manage the torrent queue. Thats lame that they shut me down like that since it was really only for personal use and shouldnt have been causing excessive uploads.

well, thanks for the replies. I am happy that it was not a security breach but I wanted to get some other opinions since I wasnt' sure if there was anything else that could cause that.

---

### Post by windependence on 2009-08-17
Trust me, you don't want Comcrap.

Go to canyouseeme.org and check your ports and you can find out if they are blocked.

-Tim

---

### Post by scroo.loose on 2009-08-17
I am having the same issues with comcast. They are rotten bastards. Can anyone suggest a better ISP? I was thinking with going with something satellite. But am open to anything more cost effective. (Not trying to hi-jack thread, just trying to work thru the same issue)

---

### Post by steveneddy on 2009-08-17
running a torrent server from your house on a residential line?

No way will they notice...#-o

---

### Post by jamesrfla on 2009-08-17
> **hellarough said:**
> no...I have charter. I wish I had comcast still, it was much better than this crap int terms of service as for the billing dept. I think they were a bunch of incompetent fools.

You don't want to go back to Comcast trust me. I never had it but my boss has it and it is a piece of junk. It never works and they like to shutdown home servers a lot. I have Embarq and I am able to host all my server services without any problems at all. It seems to be up every time I need it. I think I had it go out once but it wasn't Embarq's fault. Some people can't seem to read the line where the phone is and yet still dig there.

---

### Post by jamesrfla on 2009-08-17
> **scroo.loose said:**
> I am having the same issues with comcast. They are rotten bastards. Can anyone suggest a better ISP? I was thinking with going with something satellite. But am open to anything more cost effective. (Not trying to hi-jack thread, just trying to work thru the same issue)

Use Embarq if you have it in your area. If not try to find DSL providers in your area.

---

### Post by windependence on 2009-08-17
[www.speakeasy.net](www.speakeasy.net)

They are server and Linux friendly.

-Tim

---

### Post by Thirtysixway on 2009-08-17
Woah.  I thought it was just latency issues from my school, seems others with Comcast are having problems as well.  I don't pay the cable/internet bill so it's not my choice which ISP I have so I can't switch.

Is it all ports or just 80?

edit: even a random port like 7411 is blocked from external access.  How am I going to remotely access all my files? I was using my home server to develop and then accessing it elsewhere to work on it.  Great, thanks comcast.  First you force me to digital cable, then hijack my misspelled URLs, and now block my server.

---

### Post by R.Bucky on 2009-08-19
I used to run my web and other servers from my residential line. I now pay $10/mo. extra for a true static ip, business class services, and unlimited bandwidth with Comcast. Not bad...

---

### Post by Whiffle on 2009-08-19
I've had earthlink +time warner for about 2 1/2 years here, never had a problem.  I've been running a server off and on as well, but I don't do much with torrents.

---

