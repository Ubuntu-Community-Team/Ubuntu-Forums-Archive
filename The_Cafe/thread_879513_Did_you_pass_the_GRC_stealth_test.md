---
title: "Did you pass the GRC stealth test?"
date: 2008-08-04
forum: The Cafe
---

### Post by MONODA on 2008-08-04
I did :D [http://www.grc.com/intro.htm](http://www.grc.com/intro.htm) 
go to it and mouse over on services and click SheildsUp! then click proceed then click all service ports.

---

### Post by kostkon on 2008-08-04
I got this:

> Your system has achieved a perfect "TruStealth" rating. Not a single packet — solicited or otherwise — was received from your system as a result of our security probing tests. Your system ignored and refused to reply to repeated Pings (ICMP Echo Requests). From the standpoint of the passing probes of any hacker, this machine does not exist on the Internet. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system wisely remained silent in every way. Very nice.

---

### Post by kevin11951 on 2008-08-04
> **kostkon said:**
> I got this:

so you have a router?

---

### Post by Mazza558 on 2008-08-04
I'm on my Windows PC right now, and it looks like my router's doing all the hard work:

All service ports:
> Your system has achieved a perfect "TruStealth" rating. Not a single packet &#8212; solicited or otherwise &#8212; was received from your system as a result of our security probing tests. Your system ignored and refused to reply to repeated Pings (ICMP Echo Requests). From the standpoint of the passing probes of any hacker, this machine does not exist on the Internet. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system wisely remained silent in every way. Very nice.

File Sharing:

> 	Your Internet port 139 does not appear to exist!
One or more ports on this system are operating in FULL STEALTH MODE! Standard Internet behavior requires port connection attempts to be answered with a success or refusal response. Therefore, only an attempt to connect to a nonexistent computer results in no response of either kind. But YOUR computer has DELIBERATELY CHOSEN NOT TO RESPOND (that's very cool!) which represents advanced computer and port stealthing capabilities. A machine configured in this fashion is well hardened to Internet NetBIOS attack and intrusion.

> Unable to connect with NetBIOS to your computer.
All attempts to get any information from your computer have FAILED. (This is very uncommon for a Windows networking-based PC.) Relative to vulnerabilities from Windows networking, this computer appears to be VERY SECURE since it is NOT exposing ANY of its internal NetBIOS networking protocol over the Internet.

---

### Post by Newuser1111 on 2008-08-04
Yes.

---

### Post by Ozor Mox on 2008-08-04
Every box was green and it said this:

> Your system has achieved a perfect "TruStealth" rating. Not a single packet — solicited or otherwise — was received from your system as a result of our security probing tests. Your system ignored and refused to reply to repeated Pings (ICMP Echo Requests). From the standpoint of the passing probes of any hacker, this machine does not exist on the Internet. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system wisely remained silent in every way. Very nice.

I guess that's a good thing. Which do I give credit for this, Ubuntu or my router? Or both?

---

### Post by koenn on 2008-08-04
> **Ozor Mox said:**
> 
I guess that's a good thing. Which do I give credit for this, Ubuntu or my router? Or both?

Your router, most likely. If it does network address translation (NAT - most routers for home use do this by default), all ShieldsUp can see is the public address of your router, so it's your router being tested, and it will have no open ports unless you enabled port-forwarding or the vendor was stupid enough to make the management tools accessible on the public network interface.

---

### Post by barbedsaber on 2008-08-04
is it possible that being attached to the same modem as a windows computer, would give me bad results.

---

### Post by Zero Prime on 2008-08-04
> Your Internet port 139 does not appear to exist!
One or more ports on this system are operating in FULL STEALTH MODE! Standard Internet behavior requires port connection attempts to be answered with a success or refusal response. Therefore, only an attempt to connect to a nonexistent computer results in no response of either kind. But YOUR computer has DELIBERATELY CHOSEN NOT TO RESPOND (that's very cool!) which represents advanced computer and port stealthing capabilities. A machine configured in this fashion is well hardened to Internet NetBIOS attack and intrusion.
	Unable to connect with NetBIOS to your computer.
All attempts to get any information from your computer have FAILED. (This is very uncommon for a Windows networking-based PC.) Relative to vulnerabilities from Windows networking, this computer appears to be VERY SECURE since it is NOT exposing ANY of its internal NetBIOS networking protocol over the Internet.

> Your system has achieved a perfect "TruStealth" rating. Not a single packet — solicited or otherwise — was received from your system as a result of our security probing tests. Your system ignored and refused to reply to repeated Pings (ICMP Echo Requests). From the standpoint of the passing probes of any hacker, this machine does not exist on the Internet. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system wisely remained silent in every way. Very nice.

> Your system has achieved a perfect "TruStealth" rating. Not a single packet — solicited or otherwise — was received from your system as a result of our security probing tests. Your system ignored and refused to reply to repeated Pings (ICMP Echo Requests). From the standpoint of the passing probes of any hacker, this machine does not exist on the Internet. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system wisely remained silent in every way. Very nice.

Yes

---

### Post by public_void on 2008-08-04
Perfect stealth, although I'm behind two routers, so I'm not sure how that effects this test. My guess is only the first router is being tested.

---

### Post by amar on 2008-08-04
Done it in the past (though at the moment I am at uni so it gives different results)

At home I have 2 closed ports the rest are stealth. the two open ports are HTTP (80) because I use my desktop as a web server for small trial work and a random one in the high numbers which I use for ssh logins (requiring a ssh key)

so though not completely stealth, close enough for my

---

### Post by cardinals_fan on 2008-08-04
All my ports are closed, but it pinged me ;)

---

### Post by Vorian Grey on 2008-08-04
I am completely Stealthed.

---

### Post by Icehuck on 2008-08-04
I got this 

> Your system has achieved a perfect "TruStealth" rating. Not a single packet — solicited or otherwise — was received from your system as a result of our security probing tests. Your system ignored and refused to reply to repeated Pings (ICMP Echo Requests). From the standpoint of the passing probes of any hacker, this machine does not exist on the Internet. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system wisely remained silent in every way. Very nice.

while running WinXP with no firewall and a direct connection to the internet. My Windows Updates are no where near up to date either. Take this as you will.

---

### Post by fatality_uk on 2008-08-04
I failed. I am currently typing from a Windows Vista machine! It's service packed, and configured for best protection.

*I wish there was a shrugging shoulder smiley*

---

### Post by -grubby on 2008-08-04
The rest passed, pinging failed

[quote=shieldsup]
Ping Reply: RECEIVED (FAILED) &#8212; Your system REPLIED to our Ping (ICMP Echo) requests, making it visible on the Internet. Most personal firewalls can be configured to block, drop, and ignore such ping requests in order to better hide systems from hackers. This is highly recommended since "Ping" is among the oldest and most common methods used to locate systems prior to further exploitation.
[/quote]

---

### Post by ~LoKe on 2008-08-04
> Your system has achieved a perfect "TruStealth" rating. Not a single packet — solicited or otherwise — was received from your system as a result of our security probing tests. Your system ignored and refused to reply to repeated Pings (ICMP Echo Requests). From the standpoint of the passing probes of any hacker, this machine does not exist on the Internet. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system wisely remained silent in every way. Very nice.
Running Vista without updates since I bought it and Windows Firewall/Antivirus/etc turned off.

Thanks, router?

---

### Post by klange on 2008-08-04
Of course not. I run a server. Why would I want to appear nonexistent?

---

### Post by Polygon on 2008-08-04
i am behind a router, but i ran this test on vista but the only test that responded (but showed up as closed) was port 113, idnet authentication service

but  my dad might of fiddled with that one cause he does remote work on his computer a lot from his office

---

### Post by Old_Grey_Wolf on 2008-08-04
> **Polygon said:**
> i am behind a router, but i ran this test on vista but the only test that responded (but showed up as closed) was port 113, idnet authentication service

but  my dad might of fiddled with that one cause he does remote work on his computer a lot from his office

Some routers still have port 113 enabled by default. I had to manually override it in one of my previous routers. Heres some information on port 113: [https://www.grc.com/port_113.htm](https://www.grc.com/port_113.htm)

---

### Post by Old_Grey_Wolf on 2008-08-04
> **Icehuck said:**
> I got this...
while running WinXP with no firewall and a direct connection to the internet. My Windows Updates are no where near up to date either. Take this as you will.

Don't turn on file or printer sharing. If you do, you will fail. You are obviously not running a mail server or any other kind of server.

---

### Post by BLTicklemonster on 2008-08-04
Gibson Research is a great site. I went by there not too long ago and tested mine and came way stealthier than a fart in a nunnery.

... in a high wind.

:O)

---

### Post by Paqman on 2008-08-08
That's a handy test. I didn't realise my router was responding to pings.

---

### Post by keiichidono on 2008-08-08
I got: "Your system has achieved a perfect "TruStealth" rating. Not a single packet — solicited or otherwise — was received from your system as a result of our security probing tests. Your system ignored and refused to reply to repeated Pings (ICMP Echo Requests). From the standpoint of the passing probes of any hacker, this machine does not exist on the Internet. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system wisely remained silent in every way. Very nice."

I'm using a router but it doesn't have anything or much to do with it because I always failed the ping test in Windows with a good firewall but in Ubuntu without me touching anything related to the firewall I am perfectly secure. One more reason I love Linux.

---

### Post by infoseeker on 2008-08-09
> Solicited TCP Packets: RECEIVED (FAILED)

> Unsolicited Packets: PASSED

> Ping Reply: RECEIVED (FAILED)


All closed except 80 and 21 ;)
No firewall running...nothing sinister to hide tho :)

---

### Post by billgoldberg on 2008-08-09
I failed because the computer pinged back.

---

### Post by Dremora on 2008-08-09
I don't know, I don't go to his website.

This is the guy that got pwned by a 12 year old script kiddie and then realized he had made an entire website devoted to the ordeal, before quietly deleting all of those pages.

---

### Post by k3lt01 on 2008-08-09
My ports were Closed with about 5-10% Stealthed. I just posted about it in a new thread. I did it on a wireless Laptop running Hardy and want to find out how to fully stealth my machines. I could stealth XP but Linux is an entire new ball game so I want to learn how to do it.

---

### Post by drawhole on 2008-08-09
acually i hve a routor and it was close for the first bit like first 4 or so lines then it went green for the rest. said i failed ... but i know other wise i've done a lot of tests vs my system. Nmap - being one of them

---

### Post by Paqman on 2008-08-10
> **billgoldberg said:**
> I failed because the computer pinged back.

Have a rummage around your router's settings, you can probably tell it not to respond to pings.

---

### Post by Closed_Port on 2008-08-10
> **Dremora said:**
> I don't know, I don't go to his website.

This is the guy that got pwned by a 12 year old script kiddie and then realized he had made an entire website devoted to the ordeal, before quietly deleting all of those pages.
Oh noes, don't tell me you think Steve Gibson isn't trustworthy:
[http://en.wikipedia.org/wiki/Steve_Gibson_(computer_programmer)#Controversy](http://en.wikipedia.org/wiki/Steve_Gibson_(computer_programmer)#Controversy)

And Stealth must be more secure, especially if you have achieved perfect "TrueStealth" rating. Now if this doesn't sound good.

The problem is of course, that your computer isn't stealthed, that Truestealth is stupid marketing bubble and that in the process of achieving a perfect "TrueStealth" rating, you are breaking the internet.
Well done!
[http://hansenonline.net/Networking/stealth.html](http://hansenonline.net/Networking/stealth.html)

---

### Post by sujoy on 2008-08-11
well i finally managed to get trustealth with a fresh iptables [setup]("http://binarycodes.blogspot.com/2008/08/i-saw-thread-in-ubuntuforums.html") (my first ever)!
now the above link has got me thinking. it seems right. perhaps i ought to change the target from DROP to REJECT with appropriate --reject-with message.

---

