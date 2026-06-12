---
title: "Is TOR the best way to change your (static) IP address? If so, how?"
date: 2012-01-17
forum: Security
---

### Post by rocksockdoc on 2012-01-17
How can I temporarily change my static IP address while using Firefox?

Googling, I found "TOR"; but there is conflicting installation information for TOR on Ubuntu.

If TOR is the best answer, then what's the best way to install TOR?

DETAILS:
1. Googling for how to change a static IP address in Firefox I find "The Onion Router" project.
2. Searching for "TOR" & "Onion" in the Ubuntu Software Center finds "Vidalia" & "TorK", both of which I installed.
3. Googling for how to use them, I find the TOR site which advises against it.
- [The TOR FAQ]("https://www.torproject.org/docs/faq.html.en#CompatibleApplications")

The TOR site suggests using the "[TOR Browser Bundle]("https://www.torproject.org/projects/torbrowser.html.en")" with Firefox, and not Vidalia/TorK, and certainly not the TOR button application for Mozilla; so I'm confused.

Worse yet, the Linux instructions for installing the TOR Browser Bundle are complex (see screenshot below) for a newbie who is used to installing things from the Ubuntu Software Center.

May I ask from those who use TOR with Firefox to change your IP address ... 
Q: What is the best way to enable Firefox to use TOR for temporary IP address changes?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=211026&stc=1&d=1326829076[/IMG]

---

### Post by hackertarget on 2012-01-17
Tor has very specific use cases in that provides an anonymous communication medium. It makes it difficult for your communication to be tracked back to you.

The best way to change your static IP is to pay for a VPN service, or to pay for a small VPS and install openvpn. This allows you to have all your traffic come from a totally removed and remote IP address location (including another country). Traffic between you and the VPN endpoint is all encrypted.

Using a VPN or VPS you will get good speed for normal use cases.


It really depends on why you want to change your IP...

---

### Post by rocksockdoc on 2012-01-20
> **hackertarget said:**
> It really depends on why you want to change your IP

Thanks for that nice summary as I'm new to changing my IP address:

[LIST]
[*]TOR ==> anonymous communication
[*]VPN service or VPS/openvpn ==> remote IP + encryption
[/LIST]
I don't need to be anonymous; nor do I need encryption: I just need a different IP address.

In the past, with DSL, changing the IP address was as simple as disconnecting the home broadband router and waiting long enough for the DSL provider to issue a new IP address. That works well with large providers who have many IP addresses.

However, now I'm on a small WISP provider who assigns me the same IP address as he does hundreds of his other clients. We all have the same IP address ... so ... we all suffer/benefit equally from all that entails.

On the benefit side, it provides us a measure of anonymity (we're one of of hundreds with the same IP address); but more to my problem - we suffer from the actions of any one of our 'neighbors'.

In my case, the IP address is banned from a website that I wish to use. I have only two choices (that I can think of):

[LIST=1]
[*]Connect to that website from somewhere else (which is my current workaround)
[*]Change my IP address (which is the current question)
[/LIST]
For what I'm doing, (i.e., simply posting to a very common web site), I don't need encryption nor anonymity ... I just need an IP address that isn't already banned through no fault of my own.

While walking over to my friend's house to post works just fine (he has a different IP address obviously), I was trying to figure out how to post with a local IP address.

I suspect a geolocated foreign address might also be banned (since it's a local web site); but I definitely do need to look up these two services you suggested, even though they seem like overkill for what I want (which is simply to change the IP address to something that isn't banned already).

Since I generally learn using free sites (the knowledge gained then allows me to better choose for-pay sites that serve my needs) ... and since I only need about 100KB of texting capability per week for this one site (text messages only), I will first explore the free VPN/VPS servers if they exist.

Googling with the Ubuntu keyword, I still find most work only on PCs, but I 'think' these work also on Ubuntu Linux based on an initial search:

[LIST]
[*]Proxy serving
[LIST]
[*][PHP My Proxy]("http://www.phpmyproxy.com")
[*][Hide My Ars]("http://www.hidemyass.com")
[*][Free Proxy Server]("http://freeproxyserver.net")
[/LIST]
 
[*]Reputed free VPN services on Ubuntu
[LIST]
[*][Its Hidden]("http://itshidden.com/")
[*][Your Freedom]("http://www.your-freedom.net/")
[*][Cisco VPN Client]("http://compnetworking.about.com/od/vpn/p/ciscovpnclient.htm")
[*][Tinc VPN Daemon]("http://www.tinc-vpn.org/")
[*][FreeS/WAN]("http://www.freeswan.org/")
[*][Hide IP VPN]("http://www.hideipvpn.com/")
[*][Tutorial for Ubuntu]("http://www.paulstechtalk.com/how-to-get-a-free-vpn-for-ubuntukubuntu/")
[/LIST]
 
[*]Reputed free VPS/openvpn services
[LIST]
[*][FreeVPS 1.5-8]("http://linux.softpedia.com/get/System/Operating-Systems/Kernels/FreeVPS-5134.shtml")
[*][ChunckHost]("http://chunkhost.com/r/houseoflinux")
[/LIST]
 
[/LIST]
I'll pick one of each to test out on the desired web site. 
Thanks for all the advice!

---

### Post by haqking on 2012-01-20
TOR does not change your IP from your ISP.

At best it anonymises it to sites you visit, and it is not completely anonymous.

To install TOR see here [http://dangertux.wordpress.com/tutorials/tor-polipo-5-minute-install-guide-ubuntu-11-0411-10/](http://dangertux.wordpress.com/tutorials/tor-polipo-5-minute-install-guide-ubuntu-11-0411-10/)

Takes 5 mins and its installed and running.

Or use the browser bundle if you prefer but it does not change your STATIC IP, Static means it doesnt change ;-)

---

### Post by rocksockdoc on 2012-01-20
> **haqking said:**
> At best it anonymises it to sites you visit, and it is not completely anonymous.

It's my fault for not being clear.

I don't need anonymity. I'm simply trying to post a free ad to Craigslist so they already know who I am based on my email address & telephone verification number. And, I don't need encryption either (the ad is posted in the clear).

And, I can post using my same computer, my same email, and my same ad, when I go to a friend's house (but not if I go to Starbucks ... go figure). It works from some local libraries - but not others (again, go figure).

I can even post fine from my home if I connect to a neighbor's (unprotected) WiFi SSID (I guess I should tell them not to do that); but that's not ethical to connect to someone else's WiFi plus I don't wish to break the law just to post an ad to Craigslist that I can live without.

After a month of this (I recently switched WISP providers), I've concluded **the ONLY thing different in all these tests is the IP address. **

Since Craigslist is well known for ghosting, I strongly assume the 'static' IP address that I share with hundreds of others is on the ghosted list. There is nothing I can do about that (Craigslist doesn't seem to answer any queries except to autoreply with a help file which doesn't even mention ghosting).

> **haqking said:**
> TOR does not change your IP from your ISP.

I realize that. I apologize for not being explicit about my needs. 

I'm looking for something that will change my IP address once a week (or so) so that I can post an ad that posts just fine from a different IP address. 

For that, I think all three ideas are overkill - but I will use them if that's the recommended solution:

[LIST]
[*]TOR (intent is mostly anonymity)
[*]VPN (intent is mostly encryption)
[*]VPS (I'm not sure why VPS even exists)
[/LIST]
My basic question is what's the simplest way to simply change what IP address I 'appear' to be coming from to a web server such as Craigslist?

---

### Post by haqking on 2012-01-20
> **rocksockdoc said:**
> It's my fault for not being clear.

I don't need anonymity. I'm simply trying to post a free ad to Craigslist so they already know who I am based on my email address. And, I don't need encryption either (the ad is posted in the clear).

And, I can post using my same computer, my same email, and my same ad, when I go to a friend's house (but not if I go to Starbucks ... go figure).

So, the ONLY thing different in these is the IP address. Since Craigslist is well known for ghosting, I strongly assume the 'static' IP address that I share with hundreds of others is on the ghosted list. There is nothing I can do about that (Craigslist doesn't seem to answer any queries except to autoreply with a help file which doesn't even mention ghosting).



I realize that. I apologize for not being explicit about my needs. 

I'm looking for something that will change my IP address once a week (or so) so that I can post an ad that posts just fine from a different IP address. 

For that, I think all three ideas are overkill - but I will use them if that's the recommended solution:

[LIST]
[*]TOR (intent is mostly anonymity)
[*]VPN (intent is mostly encryption)
[*]VPS (I'm not sure why VPS even exists)
[/LIST]
My basic question is what's the simplest way to simply change what IP address I 'appear' to be coming from to a web server such as Craigslist?


well if thats all then just use an online proxy such as

[www.hidemyass.com](www.hidemyass.com)
[http://anonymouse.org/anonwww.html](http://anonymouse.org/anonwww.html)
[http://proxify.com](http://proxify.com)

and thousands of others.

just visit craigslist from one of those or similar and see if that works for you.

However anything illegal is obviously not supported here

Cheers

---

### Post by rocksockdoc on 2012-01-20
> **haqking said:**
> well if thats all then just use an online proxy such as
[www.hidemyass.com]("http://www.hidemyass.com")
[http://anonymouse.org/anonwww.html](http://anonymouse.org/anonwww.html)
[http://proxify.com](http://proxify.com)

Thanks for the suggestion. 

While I agree a proxy server 'is' the right answer, I'll have to test each and every one to see if it's likely to work. I'm sure 'one' will work but most will already be on the ghosting list for sure.

I think I can do a first sort by using 'whatismyipaddress' as the target URL:

[LIST]
[*][www.hidemyass.com]("http://www.hidemyass.com/")
[LIST]
[*]IP Information:  67.159.5.242
[*]ISP:FDCservers.net
[*]Services:[ Suspected Network Sharing Device]("http://6.hidemyass.com/ip-1/encoded/Oi8vd2hhdGlzbXlpcGFkZHJlc3MuY29tL2lwLXNlcnZpY2Vz")
[/LIST]
 
[*][http://anonymouse.org/anonwww.html](http://anonymouse.org/anonwww.html)
[LIST]
[*]IP Information:  193.200.150.82
[*]ISP:Anonymous S.A.
[*]Connection:[Broadband]("http://anonymouse.org/cgi-bin/anon-www.cgi/http://whatismyipaddress.com/broadband")
[/LIST]
 
[*][http://proxify.com]("http://proxify.com/")
[LIST]
[*]IP Information:  231.224.137.157
[*]ISP:SingleHop
[*]Connection: blank
[/LIST]
 
[/LIST]
Notice the first one above is listed (by [http://whatismyipaddress/](http://whatismyipaddress/)) as a 'suspected network sharing device'. This is most likely a red flag to Craigslist ... so I'd cull it out in the first pass. 

Then I'll try to find one that works & let you know.

Thanks.
  > **haqking said:**
> and thousands of others.

Unfortunately, it may be that ALL the free ones are blacklisted already ... but I won't know that until/unless I try each and every one of them. Sigh. (I wish there were a simpler way to change your IP address temporarily.)

---

### Post by CharlesA on 2012-01-20
Easy - talk to you ISP, if you want your external IP changed. Unless you are paying extra for a static IP, you will have a dynamic one.

Even if it's a Small ISP, they shouldn't assign everyone the same IP address.

---

### Post by rocksockdoc on 2012-01-20
> **CharlesA said:**
> Unless you are paying extra for a static IP, you will have a dynamic one...they shouldn't assign everyone the same IP address.

That's not my experience.

Out here, all the WISP providers (well, both of them) hand you an IP address that you share with fifty to two hundred other users. 

So, while you're not paying for a static IP address, it's what you get.

---

### Post by CharlesA on 2012-01-20
> **rocksockdoc said:**
> That's not my experience.

Out here, all the WISP providers (well, both of them) hand you an IP address that you share with fifty to two hundred other users. 

So, while you're not paying for a static IP address, it's what you get.
Have you talked to your ISP yet? Unless they are using some form of NAT to get everyone on the same external IP, which each client having a private IP, you should have your own IP.

What is the first octet of the IP that your router gets assigned? Is ti 192.x.x.x, 172.16.x.x to 172.31.x.x or 10.x.x.x ?

---

### Post by rocksockdoc on 2012-01-21
> **CharlesA said:**
> What is the first octet of the IP that your router gets assigned?

I own my own rooftop radio & antenna & home router so I have all the numbers:

[LIST]
[*]Rooftop antenna 19dBi planar
[*]Rooftop radio 600mW (28dBm)
[LIST]
[*]IP address 10.0.25.7 in bridge mode
[*]Gateway IP 10.0.25.1
[*]Primary DNS IP 192.168.300.1
[/LIST]
 
[*]Home broadband router, 30mW Linksys WRT54G (15dBm)
[LIST]
[*]IP address 10.0.25.8
[*]DHCP server 192.168.1.1
[/LIST]
 
[/LIST]
 > **CharlesA said:**
> Unless they are using some form of NAT to get everyone on the same external IP, which each client having a private IP, you should have your own IP.

I've spoken to both WISP providers in my area. Both use extensive NAT (we're double, triple, and quadruple nat'ed apparently). 

If you can make sense of the traceroute below, I'd appreciate it because I don't understand why there are so many private IP addresses in the path:
```

$ traceroute www.google.com
traceroute to www.google.com (74.125.127.106), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  3.890 ms  12.460 ms  13.063 ms
 2  10.0.25.1 (10.0.25.1)  18.009 ms  18.428 ms  18.851 ms
 3  192.168.85.1 (192.168.85.1)  19.864 ms  20.329 ms  20.748 ms
 4  10.0.80.1 (10.0.80.1)  21.209 ms  22.176 ms  22.656 ms
 5  192.168.251.1 (192.168.251.1)  26.344 ms  28.688 ms  29.429 ms
 6  192.168.244.1 (192.168.244.1)  30.252 ms  8.396 ms  18.845 ms
 7  192.168.242.1 (192.168.242.1)  19.578 ms  20.369 ms  22.491 ms
 8  192.168.241.1 (192.168.241.1)  22.936 ms  23.854 ms  24.269 ms
 9  192.168.300.4 (192.168.200.4)  25.117 ms  25.559 ms  26.376 ms
10  10.4.2.1 (10.4.2.1)  27.143 ms  27.984 ms  28.745 ms
11  10.4.1.1 (10.4.1.1)  29.655 ms  30.527 ms  30.884 ms
12  64.62.134.233 (64.62.134.233)  28.456 ms  14.824 ms  22.515 ms
13  10gigabitethernet1-1.core1.sjc2.he.net (72.52.92.74)  23.261 ms  30.053 ms  30.856 ms
14  72.14.219.161 (72.14.219.161)  23.977 ms  25.966 ms  26.765 ms
15  216.239.49.168 (216.239.49.168)  27.637 ms 216.239.49.170 (216.239.49.170)  29.299 ms 216.239.49.168 (216.239.49.168)  31.090 ms
16  209.85.250.60 (209.85.250.60)  35.110 ms 209.85.250.63 (209.85.250.63)  35.600 ms 209.85.250.66 (209.85.250.66)  38.020 ms
17  * 216.239.47.186 (216.239.47.186)  52.708 ms *
18  72.14.233.200 (72.14.233.200)  48.447 ms * 72.14.233.140 (72.14.233.140)  37.338 ms
19  64.233.174.99 (64.233.174.99)  41.306 ms  44.849 ms 64.233.174.127 (64.233.174.127)  40.310 ms
20  * * *
21  pz-in-f106.1e100.net (74.125.127.106)  45.593 ms  46.480 ms  47.826 ms

```

Can you help me make sense of this output?

---

### Post by CharlesA on 2012-01-21
Wow, that is a mess. You don't leave their network until hop 12. Everything before that is all private IP addresses.

Using a proxy is probably going to be the only way you are going to be able to get a different external IP unless you switch providers.

---

### Post by rocksockdoc on 2012-01-21
> **CharlesA said:**
> You don't leave their network until hop 12.

Thanks for taking a look for me. I wasn't sure how common this is.

Is this the experience of a dozen internal NATs typical with WISPs?

Or is this unusual?

* Note: There is no cable and DSL is too far from the phone company.*

> **CharlesA said:**
> Using a proxy is probably going to be the only way you are going to be able to get a different external IP unless you switch providers.

I was hoping there was a 'better' answer than that, if only because I suspect most proxies are blacklisted already (but there's only one way to find out).

I do thank you for your help ... I guess it's a difficult problem. 

Luckily nobody is gonna die if they can't post to Craigslist (however, it 'feels' like there should be an amendment in the constitution about this entitlement being taken away).
:)

---

