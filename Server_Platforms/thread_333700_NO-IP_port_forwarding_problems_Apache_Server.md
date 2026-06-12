---
title: "NO-IP port forwarding problems Apache Server"
date: 2007-01-07
forum: Server Platforms
---

### Post by nucrebain on 2007-01-07
Ok, here is a good one.

I have Ubuntu 6.10 distro. with apache2 running as a web server. I can view the web page by typing in [http://localhost](http://localhost) or by typing in the IP address of the server: 192.168.1.4. So, apache works ok!
I am also running NO-IP on my system

I set up port forwarding on my netgear router to 192.168.1.4:80.
I also set port forwarding on my actiontech DSL modem to 192.168.1.4:80.

Every time I follow the url, pkartworks.servehttp.com, I get my modem log in screen. I thought the problem was that I was inside the network so I asked my friend to acces the URL from his computer on a different ISP.. The site was not found.

Whats going on? My no IP account updates to my newest IP address. What do I do about port forwarding with a modem and a router? Do I need to forward to the router then to the server? I have tried both.. :(   What do I do?

---

### Post by Spano on 2007-01-07
I think the problem is in your port forwarding. 

In your modem forward port 80 to your Local Area Network address.

In your router forward port 80 to the machine address of your server.

I'm assuming your connection is wall to modem, modem to router, router to x number of machines on LAN including the server.
Also: could you plug your server directly into the modem and bypass the router.  Then you could forward port 80 directly to the sever IP.

---

### Post by nucrebain on 2007-01-08
Yes my sutup goes: wall --> Modem --> router --> server.
I was thinking about just running the server as the router, that would be a lot more simplified.

I was woundering though what my local area network IP is. I know my router's IP is 192.168.1.1, but on my modem It talks about my network being 192.168.0.1. I always thought my network was 192.168.1.1. Am I wrong? Am I explaining everything right?

I'll try what you told me to do: modem forward to LAN then forward to server. See if this link works for you: [http://pkartworks.servehttp.com]("http://pkartworks.servehttp.com")

thanks!

---

### Post by Spano on 2007-01-08
Unfortunately I'm not seeing you at [http://pkartworks.servehttp.com](http://pkartworks.servehttp.com).

In trying to advise you I'm flying blind because my home network is
different than yours. I have a Zoom 5x DSL modem that acts as a router as well. 

 To communicate with my modem/router I browse to 10.0.0.2, which is my gateway IP (what I was calling my LAN address in preceding post).

To forward port 80, I set the server box IP static to 10.0.0.17, which is outside the range of the Zoom's defined starting and ending IP range of 10.0.0.3 - 10.0.0.15.

I use NO-IP, as you are, to get around the dynamically assigned IP address my ISP provides.  The No-Ip client is available as a package in Synaptic.
You won't be able to browse  [http://pkartworks.servehttp.com](http://pkartworks.servehttp.com) from within your LAN (as you discovered), but you can verify your setup from outside your LAN
by going to [http://www.canyouseeme.org/](http://www.canyouseeme.org/)

Re-read your modem and router manuals to confirm that your forwarding ports correctly.  

You might want to post your modem and router model #s for others reading this thread. Could be helpful in diagnosing the problem.

Hopefully some others will chime in here with advice.

---

### Post by nucrebain on 2007-01-08
My Modem is an Actiontech GT701-WG. My ISP is Quest. 
My router is a Netgear WRG614 v5.

-Thanks!

---

### Post by aragorn2909 on 2007-01-08
> **nucrebain said:**
> 
I set up port forwarding on my netgear router to 192.168.1.4:80.
I also set port forwarding on my actiontech DSL modem to 192.168.1.4:80.


I just reread your first post.  Going from wall->modem->router->lan  
Why are you forwarding ports twice?  Clear the forwarding rules from your modem and allow the router to handle it.  

A.B.

---

### Post by nucrebain on 2007-01-09
> **aragorn2909 said:**
>  
Why are you forwarding ports twice?  Clear the forwarding rules from your modem and allow the router to handle it.  

A.B.

I removed the port forward on my modem. But it still doesn't work. My firewall is dissable on my modem. Do I also dissable Nat on the modem as well? How do I dissable portforwarding on my modem and let my router handle everything? This is the main things I am confused about in this whole ordeal... ](*,)

---

### Post by nucrebain on 2007-01-09
Oh yeah, I did visit [http://www.canyouseeme.org]("http://www.canyouseeme.org"). It got my IP adress correct but when I enter port 80 in the box and click submit I get this error:

"Error: I could not see your service on 70.56.30.104 on port (80)
Reason: Connection timed out"

I think I got another error like this but it said somthing like cannot acces server or somthing like that. I'm kinda vuge about what it said..

---

### Post by nucrebain on 2007-01-09
This is another one from [http://canyouseeme.org]("http://canyouseeme.org"), "Error: I could not see your service on 70.56.30.104 on port (80)
Reason: Connection refused"

yeah, I dont know what to do.. someone please help...

---

### Post by nucrebain on 2007-01-09
This might Help, Here are some screenshots of my kit and their setup:

My actiontech modem:
[IMG]http://img479.imageshack.us/img479/8103/actiontech1cg9.jpg[/IMG]
[IMG]http://img479.imageshack.us/img479/5517/actiontech2yj6.jpg[/IMG]
[IMG]http://img205.imageshack.us/img205/3357/actiontech3by9.jpg[/IMG]

My netgear router:
[IMG]http://img205.imageshack.us/img205/7792/netgearportforwardcopypg6.jpg[/IMG]
As you can see I  have tried many ports with no success....
See no IP forward on my actiontech modem.
I have port 80 and 8080 pointing to my server 192.168.1.4. I was trying to work around my ISP if they were blocking. I called them and they said that they did not block 80.

What am I doing wrong?

thank you in advance for your assistance!

---

### Post by aragorn2909 on 2007-01-09
I'm curious.  On your modem, is your firewall active?  Do you have the firewall active on your router?  Do you run a software firewall on the computers on your lan?   

A.B.

---

### Post by Modernity on 2007-01-09
** Quick overview **
If you are trying to host your server in your house, you must bridge your DSL modem to your router. By doing this you will be using the router as your modem ( i.e. to pull an addresss). You will have to configure your router with the appropiate username and password, for this to work. Call your ISP provider to do this! Once you have your Modem bridged to your Router then use Port forwarding on your router. I have never used NO-IP, so I can't help you with that, but after doing all this make sure you up-date your DNS address with the company that is porting your URL.

---

### Post by nucrebain on 2007-01-09
> **aragorn2909 said:**
> I'm curious.  On your modem, is your firewall active?  Do you have the firewall active on your router?  Do you run a software firewall on the computers on your lan?   

A.B.

Fire walls:
My router is firewalled, nat and spi.

My modem firewall is off but nat is still on (should I turn this off?).

My windows PCS are using Zone alarm.

My ubuntu box has no firewall and firestarter is disabled or not started.

---

### Post by nucrebain on 2007-01-09
> **Modernity said:**
> ** Quick overview **
If you are trying to host your server in your house, you must bridge your DSL modem to your router. By doing this you will be using the router as your modem ( i.e. to pull an addresss). You will have to configure your router with the appropiate username and password, for this to work. Call your ISP provider to do this! Once you have your Modem bridged to your Router then use Port forwarding on your router. I have never used NO-IP, so I can't help you with that, but after doing all this make sure you up-date your DNS address with the company that is porting your URL.

Im going to try this to see if it will work. My router has an option to enter a login username and password for internet usage. Ill tell you how it goes

---

### Post by nucrebain on 2007-01-10
Ok, every time I change any setting to do with nat on my modem I loose access to the internet. Then I have to reistall the firmware to reset it. Then everything works again.

Perhaps I should contact my isp (qwest).

---

### Post by Modernity on 2007-01-10
> **Modernity said:**
> ** Quick overview **
If you are trying to host your server in your house, you must bridge your DSL modem to your router. By doing this you will be using the router as your modem ( i.e. to pull an addresss). You will have to configure your router with the appropiate username and password, for this to work. Call your ISP provider to do this! Once you have your Modem bridged to your Router then use Port forwarding on your router. I have never used NO-IP, so I can't help you with that, but after doing all this make sure you up-date your DNS address with the company that is porting your URL.

That's why I said call your ISP, because if I am not mistaken, they have to make a change on their end too (depending on who your ISP is).

---

### Post by drkknight on 2007-01-12
I would really love to hear what Qwest had to say about this or if you got it working on your own. I too have Qwest and the same modem and have been fighting with this for some time now. Every time I try to get help from Qwest, they say they don't support what I'm doing and I'm on my own. Oh, and don't tell them you use Linux because that usually ends up with them terminating the conversation :)

---

### Post by ishift on 2007-01-13
curious as to how this turns out as i'm also having port-forwarding issues...

*bump*

---

### Post by chrisfay on 2007-01-14
Have you tried it without the router? I would eliminate as many variables as possible and work my way up the chain. If it works without the router, then move forwards. If not, you have an issue in your modem. The less you have to guess with the better.

Secondly, if you're using your nat and routing functions within the modem, you will need to change your router from 'Gateway' mode to the non-gateway setting since your modem is actually functioning as your DG. There should be a simple option for this in your admin pannel.

---

### Post by PurposeOfReason on 2008-03-21
Sorry to bring back this thread but I have the exact same problem and the exact same hardware and was wondering if this got done and how.

---

