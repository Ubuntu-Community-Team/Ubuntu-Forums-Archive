---
title: "Ubuntu server 11.04 + NO-IP + SSH"
date: 2011-07-05
forum: Server Platforms
---

### Post by ward86 on 2011-07-05
Hello all,
 
First i would like to say that ubuntu is not new for me ... So i know pretty mutch what i'm doing. I don't want to do profit from the free community or somthing. 
 
My situation :
 
I Have a Ubuntu server 11.04 with 1 NIC and static ip : 192.168.1.3
 
What have i done :
 
apt-get install ssh-server > OK
set ssh-config file to port 7100 > OK , port check OK
check that service is running > OK
do SSH session from internal > OK , working over port 7100 with putty and from other linux machine :popcorn:
I have installed : 
 
apt-get install no-ip + host setup + login etc... > OK
check ip : cron [http://www.whatismyip.org](http://www.whatismyip.org) > OK
check status no-ip > working
ping to "host" from no-ip > OK , ping ok
 
MY GOAL :
 
ssh from work to home over port 7100( i'm 1000% sure its a open port )
At the moment i'm trying from home to get this working.
 
so i do in putty : external ip( i see on ubuntu server ) + port 7100 > connection refused ...
 
I have forwarded following ports in my DD-wrt router :
 
port 7100-7101 TCP/UDP( i know i only need TCP) ip : external + static internal 
 
I think when i try to connect from external that i end at my router ... that i try to connect there to the external ip??? 
 
is it possible that i connect to my no-ip host? I don't care if i have to connect to my external IP , since its not changing anymore...
 
If you need more info from me , i'm happy to send

---

### Post by Lars Noodén on 2011-07-05
> **ward86 said:**
> ...
 
I have forwarded following ports in my DD-wrt router :
 
port 7100-7101 TCP/UDP( i know i only need TCP) ip : external + static internal ...

Are you sure?  Try an [external port scanner](http://www.canyouseeme.org/) and point it at port 7100.

---

### Post by ward86 on 2011-07-05
Lars,
 
Thank you for your reply :
 
[COLOR=#ff0000]Error:[/COLOR] I could **not** see your service on **178.119.233.187** on port (**7100**)
Reason:[SIZE=2] Connection refused[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]I have added the screenshot from my dd-wrt router[/SIZE]
[SIZE=2][/SIZE] 
[[IMG]http://img402.imageshack.us/img402/6767/routerp.png[/IMG]](http://imageshack.us/photo/my-images/402/routerp.png/)
Uploaded with [ImageShack.us](http://imageshack.us)
 
what am i doing wrong? I tought this what correct?

---

### Post by arrrghhh on 2011-07-05
> **ward86 said:**
> Lars,
 
Thank you for your reply :
 
[COLOR=#ff0000]Error:[/COLOR] I could **not** see your service on **178.119.233.187** on port (**7100**)
Reason:[SIZE=2] Connection refused[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]I have added the screenshot from my dd-wrt router[/SIZE]
[SIZE=2][/SIZE] 
[[IMG]http://img402.imageshack.us/img402/6767/routerp.png[/IMG]](http://imageshack.us/photo/my-images/402/routerp.png/)
Uploaded with [ImageShack.us](http://imageshack.us)
 
what am i doing wrong? I tought this what correct?

Perhaps the SSH2 entry is making it mess up?

You should only have one entry in dd-wrt, and the IP it's asking for is the local IP on your LAN.

---

### Post by ward86 on 2011-07-05
> **ward86 said:**
> Lars,
 
Thank you for your reply :
 
[COLOR=#ff0000]Error:[/COLOR] I could **not** see your service on **178.119.233.187** on port (**7100**)
Reason:[SIZE=2] Connection refused[/SIZE]

[SIZE=2]I have added the screenshot from my dd-wrt router[/SIZE]

[[IMG]http://img402.imageshack.us/img402/6767/routerp.png[/IMG]]("http://imageshack.us/photo/my-images/402/routerp.png/")
Uploaded with [ImageShack.us]("http://imageshack.us")
 
what am i doing wrong? I tought this what correct?
 
UPDATE :
 
[COLOR=#008000]Success:[/COLOR] I can see your service on **178.117.144.98** on port (**7100**)
Your ISP is not blocking port 7100

---

### Post by ward86 on 2011-07-05
> **arrrghhh said:**
> Perhaps the SSH2 entry is making it mess up?
 
You should only have one entry in dd-wrt, and the IP it's asking for is the local IP on your LAN.
 
check my update below and screenshot in my reply to you :
 
[[IMG]http://img827.imageshack.us/img827/5877/router2t.png[/IMG]](http://imageshack.us/photo/my-images/827/router2t.png/)
Uploaded with [ImageShack.us](http://imageshack.us)
 
I will test tomorrow.
 
Now i want to set a computer(windows xp ) that my traffic will go over SSH trough the network over my network to the internet ... I presume that i have to use a proxy again? Or setup a proxy in my browser for the windows xp?

---

### Post by arrrghhh on 2011-07-05
> **ward86 said:**
> UPDATE :
 
[COLOR=#008000]Success:[/COLOR] I can see your service on **178.117.144.98** on port (**7100**)
Your ISP is not blocking port 7100

So are you good?

If it's fixed, go ahead and use the "Thread Tools" drop-down to mark this thread [SOLVED].

Either way, if it is working I would remove the entry on the port forward page that has your WAN IP.  That's not necessary, at all.  The whole point of that port forward page is to forward ports from your LAN to the outside internet.

> **ward86 said:**
> check my update below and screenshot in my reply to you :
 
[[IMG]http://img827.imageshack.us/img827/5877/router2t.png[/IMG]](http://imageshack.us/photo/my-images/827/router2t.png/)
Uploaded with [ImageShack.us](http://imageshack.us)
 
I will test tomorrow.
 
Now i want to set a computer(windows xp ) that my traffic will go over SSH trough the network over my network to the internet ... I presume that i have to use a proxy again? Or setup a proxy in my browser for the windows xp?

Edit - just saw this post.

Looks good.  As for your other question, I do this and yes you would need a proxy.  I use a SOCKS proxy thru putty on the XP machine to connect back to my server @ home.

---

### Post by ward86 on 2011-07-05
> **arrrghhh said:**
> So are you good?
 
If it's fixed, go ahead and use the "Thread Tools" drop-down to mark this thread [SOLVED].
 
Either way, if it is working I would remove the entry on the port forward page that has your WAN IP. That's not necessary, at all. The whole point of that port forward page is to forward ports from your LAN to the outside internet.
 
I will test this tomorrow @ other pc ... I can putty myself in trought the external IP .. I don't know if its like FTP that when you connect trought external IP that you connect over LAN IP when you are in the same subnet.
 
And also i have added a second "small question"...
 
I have been reading that you can tunnel your traffic with SSH and set it up in firefox so surf over the internet trough the SSH tunnel... Yet i don't know how to do this. :confused:

---

### Post by ward86 on 2011-07-05
> **arrrghhh said:**
> So are you good?
 
If it's fixed, go ahead and use the "Thread Tools" drop-down to mark this thread [SOLVED].
 
Either way, if it is working I would remove the entry on the port forward page that has your WAN IP. That's not necessary, at all. The whole point of that port forward page is to forward ports from your LAN to the outside internet.
 
 
 
Edit - just saw this post.
 
Looks good. As for your other question, I do this and yes you would need a proxy. I use a SOCKS proxy thru putty on the XP machine to connect back to my server @ home.
 
Can this be it? : [http://vectrosecurity.com/content/view/67/26/](http://vectrosecurity.com/content/view/67/26/)
 
IF i understand correctly, i have connect to Putty... log myself in and setup firefox ( IE compatible?) to use local proxy?
 
We both type fast :D can you please explain with a screenshot or guide? I'm a pretty exp. guy in IT , because i studied for it and work in it -_- But , SOCKS proxy is unknown for me ...

---

### Post by arrrghhh on 2011-07-05
> **ward86 said:**
> Can this be it? : [http://vectrosecurity.com/content/view/67/26/](http://vectrosecurity.com/content/view/67/26/)
 
IF i understand correctly, i have connect to Putty... log myself in and setup firefox ( IE compatible?) to use local proxy?
 
We both type fast :D can you please explain with a screenshot or guide? I'm a pretty exp. guy in IT , because i studied for it and work in it -_- But , SOCKS proxy is unknown for me ...

Heh, we type too fast it seems :p.

I took a brief look at that guide, and that's exactly what I do.  Basically in putty under the tunnels section I forward a port, and then in FireFox I set it up to use the proxy pointed back to the localhost of the XP machine.  Works very well, PM me if you want some help on it.  Kinda outside of the scope of the Ubuntu forums ;).

---

