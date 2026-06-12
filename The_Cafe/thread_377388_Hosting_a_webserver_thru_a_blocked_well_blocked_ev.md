---
title: "Hosting a webserver thru a blocked well blocked every thing"
date: 2007-03-06
forum: The Cafe
---

### Post by Foudre on 2007-03-06
Lol, i know this is a sort of the wall idea to post this here but hey who else would know, its not a linux related thing since i'm sort of being forced to use windows on the server, the server itself isn't a problem, its getting people outside the network to connect. Now i'm confused i'm on a campus internet, they block things like bittorrent based on activity, ok i guess thats semi their right. But nothing peer to peer works annoying but what ever. Now my radio server works fine, i've even had a dude in germany connect and it was fine. The radio server also has a mini http server on it too. My web server by being forced to use since vista and apache don't quite agree, is myserver. It won't connect, even after routing traffic away from port 80 to 8000. People on the shcool wired network can connect just fine, but people outside can't even with a port redirect, i'm using no-ip to make the address change the port by default when some one uses the address. 

Any one know a way past this? Its not port specific, but a simalair type of traffic is already working. And i checked my agreement to use their net, and it says nothing about hosting a server, so they can't do anything to me about it / they shouldn't have the right to block it.

---

### Post by kidders on 2007-03-06
Hi there,

> **Foudre said:**
> Now my radio server works fine, i've even had a dude in germany connect and it was fine. The radio server also has a mini http server on it too. ... It won't connect, even after routing traffic away from port 80 to 8000.In order for your radio server to work, your network admins presumably redirected incoming traffic on the network's public IP to your internal IP. Won't they do the same for your HTTP server?

> **Foudre said:**
> And i checked my agreement to use their net, and it says nothing about hosting a server, so they can't do anything to me about it / they shouldn't have the right to block it.Naturally, the owners of a network can do anything they want with their own property ... unfortunately, since running an externally accessible HTTP server on a LAN normally requires administrative configuration, there's not a lot you can do if they decide not to let you.

---

### Post by Foudre on 2007-03-07
the funny thing is, both my foreign and local ip are the same. I don' t know, the whole thing confuses me why one will work but not the other, maybe if i reduce the number of accepted users it' won't get blocked, my radio is only set pretty low, my web server is set unlimited, I doubt that'll  work though.

---

### Post by Ocxic on 2007-03-07
they'll nevber allow you to run a web server if they redirtect port 80 on there ser4ver to your computer that would mean that the eintire school lan would connect to you, and they would loose there net connection, and unless I'm completly wrong about that, they still wouldn't like you eating upo ther bandwidth with a server, even a small one

---

### Post by Foudre on 2007-03-07
well i'm not touching port 80, the port 80 redirect thing is a  dns deal, the address [http://foudrenet.no-ip.biz](http://foudrenet.no-ip.biz) would other wise require [http://foudrenet.no-ip:8033/index.html](http://foudrenet.no-ip:8033/index.html)

i can half way understad their part at the same time, its not against their it policy, I don't expect more then 2 visitors a week really, half of which would be me, convienient to store files that way. 
I'm just confused that one would work and not the other (the radio server with a http server, it won't let you edit it since its intiated on the server startup and stored in tempfiles, and activly changes it in the exe to update it so if you change it just gets changed back) (and the actuall web server). Maybe they just like port 8032 for letting stuff thru?

---

### Post by kidders on 2007-03-07
> **Foudre said:**
> the funny thing is, both my foreign and local ip are the same.Yep. Large educational establishments typically reserve large numbers of public IPs for use on their networks. The whole of 129.130.0.0/16 belongs to Kansas State University, so there is no reason why their internal DHCP servers can't hand out these addresses instead of private ones.

> **Ocxic said:**
> they'll nevber allow you to run a web server if they redirtect port 80 on there ser4ver to your computer that would mean that the eintire school lan would connect to youIn this case, that wouldn't happen. Having said that, packets destined for your IP still won't necessarily get through though, since routers they pass through on the way to you (eg 129.130.252.9, 129.130.252.26) may drop them.

> **Foudre said:**
> I'm just confused that one would work and not the otherMe too. Since you appear to be able to run externally accessible servers, you must have some sort of configuration problem.

---

### Post by Foudre on 2007-03-07
hmm, not sure if i did, but did i ever say i was going to kstate? if that was just an example it was a pretty random match then, cause i do go there, I think i have said it on another thread. Hmm, ok i can believe i made a configuration error (its me after all), but then if that were the case why can people in the dorm, maybe all over campus (only tested it in dorm) be able to connect. Well nvm i sort of get that, but what would i have configured wrong to make it so only those at kstate can access it? I know apache may have been easier to do this with, but vista won't use apache quite yet, I'm using something called myserver, it was just some quick free thing i found seamed to be high enough quality and it works on vista.

so if its a config error any suggestions as to what to change?

---

### Post by kidders on 2007-03-07
> **Foudre said:**
> hmm, not sure if i did, but did i ever say i was going to kstate? if that was just an example it was a pretty random match then, cause i do go thereHehe sorry... I looked up the IP you posted. I wanted to take a peek at how your network handles incoming data ... just in case there was something obvious causing your problem.

> **Foudre said:**
> any suggestions as to what to change?I'm not sure. First, we need to figure out exactly what the problem is. The easiest option would be to ask your network admins.

---

### Post by Foudre on 2007-03-07
kstate IT department isn't exactly freindly, or smart. They won't help me, they can basicly install windows, and read off a piece of paper and tell you to do something 8 times in a row  that isnt' working.  I'm afraid if i address them they'll just drop me from the network, the way they are. The allowed list of operating system is as follows, Windows Xp with service pack 2, Mac OS X, end of list, we got a email saying that we can have vista on their network yet, total bs their preface to the IT policies says we have the right to choose our medium.

---

