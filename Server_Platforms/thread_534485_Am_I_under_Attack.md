---
title: "Am I under Attack?"
date: 2007-08-25
forum: Server Platforms
---

### Post by Ken Dodd on 2007-08-25
Ok first off I'm new to ubuntu and Linux, I've had it installed for about 2weeks now and am loving it.

I decided last week to install a firewall, having not bothered for a while due to hearing how safe ubuntu and Linux in general is compared to windows.

As I am used to windows and I am not really used to the terminal in ubuntu, I decided I wanted a firewall that would be similar to norton and easy to use.

After looking at recommendations on this forum I eventually installed firestarter.

Now after a couple minutes of me setting it up and first activating it, I can honestly say its tray icon never changes from red, and constantly reports hits.

I am getting worried because when I look at my events log it reports constantly what look like attack attempts mainly on ports 135 and 39419.

When I say constant alerts I mean it I get like 10-20 reds a minute.

I have been to shields up to test my firewall and I pass every test, but I am still concerned at the sheer amount of alerts an hope that someone at this forum can help shed some light on these port numbers and whether or not I can settle my mind, as at the moment my ubuntu experience is being ruined.

Link to screenshot of firestarter event log:  [http://img165.imageshack.us/img165/1786/firewallscreenshotht2.png]("http://img165.imageshack.us/img165/1786/firewallscreenshotht2.png")

---

### Post by rickyjones on 2007-08-25
Looks like your firewall is working. My guess would be that those are bot-computers that are just automatically launching attacks.

Another way to protect yourself would be to get a hardware firewall if you have a high speed connection.

-Richard

---

### Post by Nepherte on 2007-08-25
Just for the record: you did not install a firewall but a gui for an already installed firewall called iptables.

---

### Post by koenn on 2007-08-25
apparently port 135 is used by Microsoft Remote Procedure Calls ( [http://www.linklogger.com/TCP135.htm](http://www.linklogger.com/TCP135.htm) ) so it is indeed likely that your seeing an automated attack or a script kiddie trying to exploit ms RPC on random IP adresses. 
So, no worries, and your firewall seems to be working.

---

### Post by GigaVolt on 2007-08-25
View this HowTo:
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

P.S. don't worry port 135 is loc-srv

---

### Post by Ken Dodd on 2007-08-25
Yo thx everyone for the reply's, I suppose the main reason I am worrying is because  they all seem to be directed an the same ports 135 and 39419.

I have this computer currently set up on a dual boot with windows xp as I still need certain software, mainly adobe software that I use, as I am a graphic designer and need this software for work etc.

koenn, I followed the link and agree with your explanation of it being an automated attack.

Now my only worry is this:

What are the chances of these automated attacks exploiting my pc when booting into and using xp? (I have norton, which also passed all port tests on shields up btw).

Also does anyone know what port 39419 is for? as this particular port takes up 90% of the reported blocked connections in firestarters event log.
Firestarter also lists blocked connections were there is no port listed only the source and protocol are shown

Again thx everybody for your advice. :)

---

### Post by koenn on 2007-08-25
can't find any info on port 39419 but given that it's a high, not well-known port, it may be the default port some or other trojan listens  on, and your 'attacker' is just looking around to find a host where this trojan is installed. 

If your XP shows port 135 closed/stealth on "Shields Up", that means there is no service listening there, so an attack via that port wont work either.

not all network protocols use tcp/udp ports. ICMP (a.o. for echo requests or "pings") and GRE (MS vpn) are typical examples.

---

### Post by Ken Dodd on 2007-08-27
Koenn thx again for the reply.

Just turned my comp on today and now it seems like 90% of the hits are all at port 56859 instead, and the rest are port 39419.

I understand I shouldn't worry because the firewall is obviously doing its job, but I would just like to know whether there is a likelyhood that I in particular am being targeted or whether I shouldn't worry and they are like you said 'automated attacks'.

As if it is my computer that is being targeted they seem fairly determined to get through.

btw, since 2day my cpu keeps peaking at 100% and rarley dropping below 80, I'm getting really anoyed as I thought linux was secure, but these constant hits are driving me mad.

---

### Post by koenn on 2007-08-27
Well, it could be some sort of denial of service against whatever service is supposed to be listening on 56859 , but if you don't have anything running there, it's hard to maintain you're the actual target. 

Did you piss off anyone who could be doing this ? Have you been boasting about your firewall, enough to challenge people to have a go at it ? Did you blog about the treasure map hidden in your home directory ? What other reason can there be that you're specifically targetted ? 

80-100% cpu usage is a lot. I have iptables running on a seperate machine that routes and firewalls. It's a 133 Mhz Pentium II, and it hardly ever goes below_ 80% idle_.

you could run netstat (with intervals) to check what connections you have going on, to make sure nothing extraordinary is going on. Other than that, I don't really know what to do next.

---

### Post by Seisen on 2007-08-27
Port numbers that high are usually related to P2P programs have you ever had torrent software that ran off of th same IP address as your server?

---

### Post by Ken Dodd on 2007-10-06
> Port numbers that high are usually related to P2P programs have you ever had torrent software that ran off of the same IP address as your server?

You were right, that port number 56859 is related to P2P, as I have just checked azureus in xp and that is the port that I have set Azureus to use.

However I don't know what you mean about 'same ip address as your server', I just using an home pc with my modem on cable broadband.

Now does anyone know why firestarter is alerting me of hits on port 56859 when I only use this port for azureus P2P software under windows?

Should I be worried about hits on this port when running in windows?

Some things I don&#8217;t understand is why when running ubuntu firestarter is alerting me of hits on a port that is only used under windows for azures.  Why would this port be getting hits when running in linux, If I don&#8217;t have azureus on ubuntu and the port is closed why Is firestarters LOG filled to the brim with alerts on this port and its status always flashing red on the taskbar?

Its disconcerting and putting me off using ubuntu even though I love the OS.

---

### Post by Soarer on 2007-10-06
It should put you off XP rather. The 'attackers' don't know what OS you are currently using, and only Ubuntu lets you know there *may* be a problem. The exact same thing was happening on XP, but you never knew.

I guess at least some of them are P2P asking for a connection to Azureus. They don't know whether Azureus is running or not, or what OS you are currently using.

All that is being reported is attempted connections. These are being blocked by the firewall so where is the problem? Most likely they are due to programs you have run on XP in the past.

---

### Post by eentonig on 2007-10-06
What is your problem? You're FW is just doing what you asked him to do. Meaning, block connection attempts.

The attempts to those high ports are probably because you used them in somo p2p program, and someone still thinks they are available

---

### Post by Ardoramor on 2008-01-22
My topic relates to this one so hopefully someone can help me here. I have recently set up a server at home (Ubuntu gutsy). I've installed some basic services (web, ssh, mysql) and also installed firestarter. I've left the server overnight and on the next day decided to check the activity. There wasn't much but a couple activity but some things surprised me such as Microsoft-ds service that was blocked, Samba, and couple FTPs (these were in red) other entries were unknown services and were also blocked. Today, however, I was even more surprised to see per second service requests from several sources. To me (although I'm really new) it seems like someone was trying to mount an attack. Many sources were going for 23636, 50276, and 50xxx (356, 333, 276). Also, looking at my logs, syslog, messages, and kern.log were going off very fast and i could see the list growing in front of my eyes. I know that my firewall is doing its job but should i act somehow other than just watch it? I've resecured my password (there is no root but just my account and i though harder password is safer). So my question is whether there is anything I can and should do in this case? What are your suggestions (as far as I know, I haven't pissed off any hacker XD)

---

### Post by MJN on 2008-01-22
There is little you can do but keep the hatches bolted down and weather the storm.
 
Any 'effective' action (such as notifying upstream providers, source address owners etc) is immediately offset by the fact that if it's one source today it'll be another tomorrow, then the next and so on.
 
Your firewall is doing it's job - and unless your connection becomes unusable then it is probably safe to assume you are not under a DOS attack and that you're just today's random 'target' for some compromised machines.
 
Mathew

---

