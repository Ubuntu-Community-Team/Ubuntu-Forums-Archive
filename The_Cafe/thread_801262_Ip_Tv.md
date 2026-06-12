---
title: "Ip Tv"
date: 2008-05-20
forum: The Cafe
---

### Post by Black Mage on 2008-05-20
Hey,

Is there anything good in Ubuntu for IPTV?

My job is trying to implement it and they gave me some TV Tuner cards and a computer to try it on. I know solutions exist such as MythTV, but what are good other solutions for IPTV? And are there any that can do HDTV?

---

### Post by jmore9 on 2008-05-20
Type in the search box the following :

pinnacle 800i

this will give you some idea of what you are looking for.  different card but you can see what is involved.

Hope this helps

---

### Post by uraldinho on 2008-05-20
You mean something like IPTV server? Receive the signal, decode, and transmit over TCP/IP or UDP? 

Well, I imagine you need to implement a TCP/IP or UDP server and either 1) multicast for live tv, or 2) torrent like transmission on demand (joost, sopcast, BBC iPlayer are a few applications that come to my mind. they are closed source, but will give you an idea). Your transmitted data would be your encoding of the decoded signal. 

If you know the transmission protocol, and the codecs you are using, the implementation shouldn't be too complicated.

---

### Post by Xanderfoxx on 2008-05-20
Here's a forum I found. It may help.

[http://ubuntuforums.org/showthread.php?t=698878](http://ubuntuforums.org/showthread.php?t=698878)

---

### Post by Xanderfoxx on 2008-05-20
When I asked, I was recommended VLC Player as both server and client.

Here: 

[http://www.videolan.org/vlc/streaming.html](http://www.videolan.org/vlc/streaming.html)

---

### Post by Black Mage on 2008-05-20
> **uraldinho said:**
> You mean something like IPTV server? Receive the signal, decode, and transmit over TCP/IP or UDP? 

Well, I imagine you need to implement a TCP/IP or UDP server and either 1) multicast for live tv, or 2) torrent like transmission on demand (joost, sopcast, BBC iPlayer are a few applications that come to my mind. they are closed source, but will give you an idea). Your transmitted data would be your encoding of the decoded signal. 

If you know the transmission protocol, and the codecs you are using, the implementation shouldn't be too complicated.

Yes, that is exactly what I'm look for, an IPTV server, but with open source. Can MythTV act a server and stream TV to other computers with MythTV?

> 
When I asked, I was recommended VLC Player as both server and client.

Here:

[http://www.videolan.org/vlc/streaming.html](http://www.videolan.org/vlc/streaming.html)


That was seems very interesting too.

---

### Post by uraldinho on 2008-05-20
> **Black Mage said:**
> Yes, that is exactly what I'm look for, an IPTV server, but with open source. Can MythTV act a server and stream TV to other computers with MythTV?


The simple answer is, I do not know.... 

VLC does exactly what you are looking for, but obviously it is not open source. The graph in this page is your architecture basically: [http://www.videolan.org/vlc/streaming.html](http://www.videolan.org/vlc/streaming.html) 

Look at the existing video streaming open source projects. They should have most of the things you need.

---

### Post by Black Mage on 2008-05-20
> **uraldinho said:**
> The simple answer is, I do not know.... 

VLC does exactly what you are looking for, but obviously it is not open source. The graph in this page is your architecture basically: [http://www.videolan.org/vlc/streaming.html](http://www.videolan.org/vlc/streaming.html) 

Look at the existing video streaming open source projects. They should have most of the things you need.

I definitely like how VLC looks, and how easy it seems. What worries me though is it doesn't seem to have much documentation on the web, so I'm not sure how much it is used.

The more the merrier, so when I have problems, hopefully I'm not the first one and have others to look too.

---

### Post by uraldinho on 2008-05-20
The thing is, you don't need VLC documentation, you need IPTV documentation. IPTV documentation should tell you the client-server model, and the codec algorithms to use. 

your architecture will have two main parts. 1) client-server communication model, 2) sending and receiving frames to and from codecs. IPTV specs should give you the protocol details for both of these. Basically, you need to know 1) how to connect two remote applications, 2) how the two applications exchange information. 

I haven't done any real-time stuff, but I assume the client-server communication model is based on multicast or UDP, there might be some addressing information (eg, "SAP/SDP announcements" in the VLC diagrams that announce to the client the ways of communicating with the server) in the protocols too. Send and receive would be about data frames, ie, how data frames are read from the encoder at the server end and how the transmitted frame is written into the decoder at the client end. 

In the IPTV specs, there might be some very lengthy info about the codecs, but I would only read the sections about frames and timing, so that you know what data to send and when. 

Disclaimer: don't take my word for it. Do your own research. I don't know much about IPTV, my comments are nothing more than a guess.

---

### Post by Xanderfoxx on 2008-05-20
According to this page:

    [http://www.masternewmedia.org/2005/06/04/iptv_vs_internet_television_key.htm](http://www.masternewmedia.org/2005/06/04/iptv_vs_internet_television_key.htm)

> 

**What is Internet Television** So, what is then the alternative open internet of video that Jeremy Allaire of Brightcove [evangelizes about]("http://breeze.brightcove.com/p47258018/")?

[LIST]
[*]Internet Television, is quite different in terms of the model for the consumer, the publisher and for the infrastructure used itself.
[*]In the Internet of Video, as Jeremy Allaire calls it, or Internet Television approach, the **model is open to any rights holder**, as it is based on the same publishing model that exists on the Web: **anyone can create an endpoint and publish that on a global basis.**
[*]Internet Television is **open to any rights holder** no matter whether this is an individual creating a video for a very small audience or a traditional publisher that offers linear cable channels.
[*]The Internet Television approach **the publisher has a direct communication channel to the consumer**.The content publisher is able to directly reach the consumers on the multiple devices independent of any specific carrier or operator. Internet Television is in fact an approach that also attempts to be as **device independent** as possible. Thanks to open standards and formats which have helped create this opportunity, Internet Television wants to be just as the web is today. Accessible from any type of computer and connection around the world..... and not physically tied to the user living room or set-top box.
[*]Internet Television will be **deeply integrated into the existing Internet user experience** and into the mechanisms that users use to access services, discover resources and share experiences in the Internet world, in the near future will merge with the world of video and television services seamlessly.
[*]Internet Television is **an outgrowth, not an overhaul**. Internet Television is able to ride on existing lowest common denominator infrastructure including broadband, ADSL, wi-fi, cable, satellite doesn't require new infrastructure to work or provide value to users.
[*] Internet Television uses a** global reach business model**, where video and television services that are offered in one geography can be accessed from any other global geography (as long as content distribution rights are in place).
[*]Internet Television **promises access to many new products and much broader range of programming** that we have been accustomed to retail video world and dramatically more control, as to when and where and how users can access that video/tv programming."
[/LIST]
 "*An open platform gives content providers control over the brand and customer relationship,*" says Jeremy Allaire of [BrightCove]("http://www.brightcove.com/"). 
 This, he feels, will create **an explosion of niche content that people can access directly over open, IP-based systems**. "*Nearly every small niche can be economically supportable.*"
 And also:
  "*Beyond looking at Internet Television as an ideal platform for marketing and distribution, it is interesting to think about how the Internet facilitates a distributed and collaborative environment for media production. *
 ***It won't surprise me to see** new "media collectives" modeled after open source projects that form together to put forth a particular view point - be it for entertainment or informational programs. *
 *Is this a missing piece to create a platform for citizen's media? *"



---

### Post by Xanderfoxx on 2008-05-20
According to Wikipedia:

    [http://en.wikipedia.org/wiki/Internet_Television](http://en.wikipedia.org/wiki/Internet_Television)

> **Internet television** (or **Internet TV**) is [television]("http://en.wikipedia.org/wiki/Television") distributed via the [Internet]("http://en.wikipedia.org/wiki/Internet"). Internet television allows viewers to choose the show they want to watch from a library of shows. The primary models for Internet television are streaming Internet TV or selectable video on an Internet location, typically a website. It differs from [IPTV]("http://en.wikipedia.org/wiki/IPTV") in that IPTV offerings are typically offered on discrete service provider networks.
 Internet TV is a quick-to-market and relatively low investment service. Internet TV rides on existing infrastructure including broadband, ADSL, Wi-Fi, cable and satellite which makes it a valuable tool for a wide variety of service providers and content owners looking for new revenue streams.


According to this page:

    [http://www.masternewmedia.org/2005/06/04/iptv_vs_internet_television_key.htm](http://www.masternewmedia.org/2005/06/04/iptv_vs_internet_television_key.htm)

> 

**What is Internet Television** So, what is then the alternative open internet of video that Jeremy Allaire of Brightcove [evangelizes about]("http://breeze.brightcove.com/p47258018/")?

[LIST]
[*]Internet Television, is quite different in terms of the model for the consumer, the publisher and for the infrastructure used itself.
[*]In the Internet of Video, as Jeremy Allaire calls it, or Internet Television approach, the **model is open to any rights holder**, as it is based on the same publishing model that exists on the Web: **anyone can create an endpoint and publish that on a global basis.**
[*]Internet Television is **open to any rights holder** no matter whether this is an individual creating a video for a very small audience or a traditional publisher that offers linear cable channels.
[*]The Internet Television approach **the publisher has a direct communication channel to the consumer**.The content publisher is able to directly reach the consumers on the multiple devices independent of any specific carrier or operator. Internet Television is in fact an approach that also attempts to be as **device independent** as possible. Thanks to open standards and formats which have helped create this opportunity, Internet Television wants to be just as the web is today. Accessible from any type of computer and connection around the world..... and not physically tied to the user living room or set-top box.
[*]Internet Television will be **deeply integrated into the existing Internet user experience** and into the mechanisms that users use to access services, discover resources and share experiences in the Internet world, in the near future will merge with the world of video and television services seamlessly.
[*]Internet Television is **an outgrowth, not an overhaul**. Internet Television is able to ride on existing lowest common denominator infrastructure including broadband, ADSL, wi-fi, cable, satellite doesn't require new infrastructure to work or provide value to users.
[*] Internet Television uses a** global reach business model**, where video and television services that are offered in one geography can be accessed from any other global geography (as long as content distribution rights are in place).
[*]Internet Television **promises access to many new products and much broader range of programming** that we have been accustomed to retail video world and dramatically more control, as to when and where and how users can access that video/tv programming."
[/LIST]
 "*An open platform gives content providers control over the brand and customer relationship,*" says Jeremy Allaire of [BrightCove]("http://www.brightcove.com/"). 
 This, he feels, will create **an explosion of niche content that people can access directly over open, IP-based systems**. "*Nearly every small niche can be economically supportable.*"
 And also:
  "*Beyond looking at Internet Television as an ideal platform for marketing and distribution, it is interesting to think about how the Internet facilitates a distributed and collaborative environment for media production. *
 ***It won't surprise me to see** new "media collectives" modeled after open source projects that form together to put forth a particular view point - be it for entertainment or informational programs. *
 *Is this a missing piece to create a platform for citizen's media? *"



---

### Post by uraldinho on 2008-05-20
> **Xanderfoxx said:**
> According to Wikipedia:

    [http://en.wikipedia.org/wiki/Internet_Television](http://en.wikipedia.org/wiki/Internet_Television)



According to this page:

    [http://www.masternewmedia.org/2005/06/04/iptv_vs_internet_television_key.htm](http://www.masternewmedia.org/2005/06/04/iptv_vs_internet_television_key.htm)

that's the "business model" of IPTV. technology wise, IPTV is similar to VoIP. 

Which gives me another idea. If VoIP and IPTV are similar (im saying IF, i don't know), a VoIP server could be modified to use video codecs rather than audio codecs to turn it into an IPTV server. It's worth looking at.

---

### Post by Black Mage on 2008-05-21
> **Xanderfoxx said:**
> According to Wikipedia:

    [http://en.wikipedia.org/wiki/Internet_Television](http://en.wikipedia.org/wiki/Internet_Television)


All the methods would work except one, wireless. Yesterday we had a huge discussion about broadcasting TV over a wireless network and it just won't work. If there is a 802.11/b on the network, that means an access point will be operating at a theorotical max of 11 Mbps, but an actually 7 Mbps. IPTV for regular channels takes 2-4 Mbps, so really, only 2-4 users would be able to use an access point proficiently.

And say that we block out 802.11/b and allow only 802.11/a/g, that a theoritical max of 52 Mbps but an actual of only around 32 Mbps. That means a max of 16 users would be able to use that one wireless point proficienltly, which is ok. But users do other things such as AIM, web browsing,downloading, etc, so 16 would be pushing that number should be divided in half.

So the best option would be using 802.11/n, but to upgrade all the access points to that standard would cost about 5 million dollars and it isn't an offical IEEE standard yet.

So basically, using IPTV over wireless is possible but very impratical.

Anyway, I'm still trying to get MythTV and VLS to work.

---

### Post by uraldinho on 2008-05-22
what about multicast? multicast transmits the same packet to multiple destinations in the wireless hotspot. that way you could use 802.11 for IPTV?

Quote from [http://en.wikipedia.org/wiki/Multicast](http://en.wikipedia.org/wiki/Multicast) : 

"IP Multicast is a technique for one to many communication over an IP infrastructure. It scales to a larger receiver population by not requiring prior knowledge of who or how many receivers there are. Multicast utilizes network infrastructure efficiently by requiring the source to send a packet only once, even if it needs to be delivered to a large number of receivers. The nodes in the network take care of replicating the packet to reach multiple receivers only where necessary."

If you think about it, all data link (MAC layer) technologies have some sort of multiple access, and share the available bandwidth. An 100mb Ethernet would also run out of bandwidth very quickly if you start using it for TV. I wouldn't rule out 802.11 only because it supports data rates of 54mbps. 54 mbps is not a small number. 

just to complicate matters for you :) one of the newer 802.11 protocols (i think e) has a traffic shaping based QoS algorithm. You could use it to allocate bandwidth on demand... but that would be over complicating the project, besides, I don't think there is any hardware/software available for QoS yet.

---

