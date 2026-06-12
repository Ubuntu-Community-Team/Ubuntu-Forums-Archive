---
title: "WPA vs WEP"
date: 2005-12-12
forum: Server Platforms
---

### Post by M3ta7h3ad on 2005-12-12
Seeing a post in the Ubuntu support thread sparked this up :)

_The Question:_
> **In *YOUR* opinion what is the most secure system**

So yeah, in your experience (no theory involved here... just practical experience) which do you find best for wireless security.

_My Opinion:_

After trying to crack my home network using WEP with a 128 bit cypher, it took  4 days (actually about 4 and 3/4 days) of packet collection (I had a large ftp transfer going generating traffic along with a few websites that were "auto refresh" things intended at dDosing scam sites generating the network packets needed) before I successfully broke the encryption and got the correct key to join the network.

My mate next door (well 2 doors up.. I get 60% signal from his network :)) helped me generate the heavy amount of network traffic for those 4 days also.

He then setup a WPA-PSK network (my router only supports WEP), for testing. I set my windows XP laptop up collecting packets and came back to it a few hours later. It had crashed. Disaster it had collected about 3 and a half hours worth of packets (I believe it was a few 100,000 packets [edit: Looking at the screenshot it was just over 300,000 packets]) and that was it.

It was late at night and I couldnt be arsed leaving the laptop running overnight so I just tried running wepcrack on what I had. Within 6mins it had found 2 keys (according to my screenshot).

The following screenshot is about half way through the process.

[img]http://m3ta7h3ad.f2o.org/php/upload/wepcrackwindows.jpg[/img]

At the end it had found about 6 keys for 3 and a half hours worth of packet collecting. It turned out my friend had set the key rotation to 30mins or so IIRC (it was a while ago).

While I didnt have the ability to connect to the network (the key changing prevents that to a certain extent.. and the keys I had found had expired prior to having the chance to logon and do a net send message saying "ha! I win" :D I was able to decrypt the packets captured, which included unencrypted IRC messages including my mates IRC password, his girlfriends email credentials, and various other bits of personal information.

So.... in my experience while WEP once cracked allows complete unhindered access to a network until the key is changed. WPA seems worryingly weak in comparison requiring 3 hours worth of packet collection and several keys broken, resulting in the compromise of personal data transmitted over a network.

I am aware now that WEP is weaker now from being able to "force" packets to be generated (I've watched a video capture of someone cracking 128bit wep in 10 minutes), but if this is default security on WPA I am rather worried.

What do you think?

---

### Post by cactus on 2005-12-12
psk (pre shared keys) is the weaker WPA implementation. 
If your test partner was setting a very weak initial passphrase, that can effect it as well..

But generally, I dont rely on the encryption overly much. Yeah, I setup WPA to keep the casual passerby out.. But I require a VPN tunnel, or a tunneled/encrypted web proxy. Depends on the setup I am going for.

Like I said though. I use WPA, and most of my traffic is either encrypted.. or I don't really care about it (it is either encrypted from my box to the destination--stunnel or ssh-tunnel/ssh, or it goes over the internet in the clear anyway). I mean.. there could easily be someone sitting on an upstream node from me dumping each and every packet I send. ;)

---

### Post by [Rui] on 2005-12-12
WPA, WEP... both innefective. Better try to setup a VPN, altough that's not exactly trivial.

---

### Post by LordHunter317 on 2005-12-12
[QUOTE=cactus]psk (pre shared keys) is the weaker WPA implementation.[/quote]WPA-PSK/RC4 is no better.  WPA-PSK/AES can just fine, if your keys can't be found by a dictionary attack on the passphrase.

Only, getting gear where that's possible is difficult.

In practice, not bothering with 802.11 link-layer security at all and using a VPN or other encrypted mechanism where necessary is the best course of action.  This is no different from any physical LAN, really.

---

### Post by bionnaki on 2005-12-13
[QUOTE='[Rui]']WPA, WEP... both innefective. Better try to setup a VPN, altough that's not exactly trivial.[/QUOTE]

how do you do this?

---

### Post by atoponce on 2005-12-13
I use WPA-Radius at home, although it is probably overkill.  WEP would work just fine for me as I use directional atennas keeping 80% of the signial within 2 feet of the outer brick of the house.  Get to the sidewalk only 10 feet away, and the signal constantly drops.  VPN would be nice, but it just isn't necessary.

Of course, I am Mr. Paranoid, so I have MAC address filtering as well, and only allow certain static IPs on the network.  If that isn't enough, the IP tables are "different" and I don't broadcast the SSID.

There are plenty of security measures you can take to ensure that your wireless connection is secure.  Common sense would also say not to leave valuable data on the network.

---

### Post by M3ta7h3ad on 2005-12-13
I would also believe VPN is the way to go for home networks.

I know about the "other" tactics of hidden SSID, use of directional antennas, mac filtering, and dhcp scoping/non-standard ip address.

Just what surprised me the most after this test is that WPA was being touted as "the daddy" of encryption schemes for link layer security (to coin the above phrase used by lordhunter :)), and home users were in effect being told that it would protect their data from any nasty folk.

When in truth, 3 hours requiring no trickery to generate traffic, and I cracked several keys, if I was a little faster on my toes I would have been able to simply login and join his network (providing he doesnt have any other anti-intrusion methods on). Seems a wee bit like false security to me.

---

### Post by Chris Tucker on 2005-12-13
hmmm /me thinks /me needs to change his wep key more often

i think my network is like an all you can eat buffet! with signs and all!
i live in a tiny town, right now one of VERY few with a laptop, and the only one with a wireless network. i like my signal to reach as far as possible, for convienience, doing some netstumbling myself i get pretty good range, soon to be even better :) working on an antenna mod
anyone driving by at the speed limit sees my network for at least 15sec... yea.. ive been using the same key since i got the router.. time to change that key...

---

### Post by bionnaki on 2005-12-13
[QUOTE=atoponce]I use WPA-Radius at home, although it is probably overkill.  WEP would work just fine for me as I use directional atennas keeping 80% of the signial within 2 feet of the outer brick of the house.  Get to the sidewalk only 10 feet away, and the signal constantly drops.  VPN would be nice, but it just isn't necessary.[/quote]

how do you set up directional atennas?

> Of course, I am Mr. Paranoid, so I have MAC address filtering as well, and only allow certain static IPs on the network.  If that isn't enough, the IP tables are "different" and I don't broadcast the SSID.

I have mac filtering as well and disable ssid broadcast. Not sure how to only allow my static IP on my wireless network using my router (linksys wrt54g)...any ideas?

---

### Post by atoponce on 2005-12-13
You can purchase direction atennas at most any electronics store.  Although they are labeled "directional", the nature of radio waves is omnidirectional.  However, they work pretty well for the most part.

What firmware are you using for your router?  The default?  Can't do it.  Get an updated firmware from Sveasoft, and it's possible.

---

### Post by bionnaki on 2005-12-13
I'll check out the directional antennas. thanks

right now, im running the latest firmware from linksys. I've used hyperwrt firmware and remember the broadcast strength option, but I had trouble maintaining a continuous connection - it would drop all the time even though I made no changes and the configuration from the linksys firmware that I had made (and had worked) was supposed copied over to hyperwrt. So I switched back to the linksys firmware.

---

### Post by anaoum on 2005-12-19
Hello,

I have set up both MAC Filtering and WEP encryption on my wireless network. 

Does WEP slow down data transfer rates? 

Is WPA faster that WEP? 

Is encryption even neccassary if i have MAC Filtering?

Thanks,

---

### Post by LordHunter317 on 2005-12-21
> **atoponce]WEP would work just fine for me as I use directional atennas keeping 80% of the signial within 2 feet of the outer brick of the house.[/quote] Radio waves don't work like that though.  If I get a good enough antenna, I can hear you from the street.  It would be difficult, but not impossible.

Directionality is only any sort of a security meausre on very long hauls, and then only if the signal is very narrow.  And it's certainly not something to be relied on at that bandwidth said:**
> Of course, I am Mr. Paranoid, so I have MAC address filtering as well,Doesn't add any security. I crack the encryption and I have a MAC.

> and only allow certain static IPs on the network.  If that isn't enough, the IP tables are "different"I'm not sure what you mean.

>  and I don't broadcast the SSID.Doesn't add any security.  I can still see your SSID.

> There are plenty of security measures you can take to ensure that your wireless connection is secure.Yes, use application-level encryption where it is needed, *just like on a wired network*.

Beyond that, if you don't want people leeching internet, then use whatever best level of encryption your router/gear supports and understand it's only a deterrent.

If you really, really must go beyond that, then you have to plunk down for 802.1x and the required software to support it.

[quote=Chris Tucker]hmmm /me thinks /me needs to change his wep key more often[/quote]There's no point.  I can crack any WEP key in the span of a few minutes.  You have'll better security watching your router's "connected" page and taking a baseball bat to anyone who isn't supposed to be on[1].

[quote=anaoum]Does WEP slow down data transfer rates?[/quote]Depends on the device but generally, yes.

> Is WPA faster that WEP?Depends.  Most cards still use the host CPU to do RC4.  Most that does AES have an accelerator because otherwise you'd get no bandwidth.

> Is encryption even neccassary if i have MAC Filtering?Yes.  MAC filtering offers zero protection.  It's not even worth bothering with.

---

### Post by Danielle on 2005-12-22
NOTE the link below is an MP3. you can tell your media player to play the MP3 instead of downloading it.
[MAC address filtering, WEP encryption, and SSID hiding](http://aolradio.podcast.aol.com/sn/SN-011.mp3)

there are some more episodes about wireless below.
[http://www.grc.com/securitynow.htm](http://www.grc.com/securitynow.htm)

---

### Post by Chris Tucker on 2006-01-19
[QUOTE=LordHunter317]
There's no point.  I can crack any WEP key in the span of a few minutes.  You have'll better security watching your router's "connected" page and taking a baseball bat to anyone who isn't supposed to be on[1].
[/QUOTE]
_you_ dont live here, if you did id be worried for my bandwidth :P
the only thing i worry about is occasionally i'll see a van or car going through this town slow down when they hit the first edge of my reception area and speed back up about where my connection drops off.. might just be a quincidence but probably wardrivers. theres only 3-4 people in this town that have laptops, and im the only one with wifi right now. and the laptop owners here dont know where to begin with wifi cracking.. i know them personally..
reason i need to change my key is becasue this is a popular commute route.. so someone with a laptop that drives through here frequently could catch enough data to get a key. im not even very worried about bandwidth theft... been thinking about turning OFF encryption. but just worrying about that one person thats like me.. and looks for wifis when theyre stuck in a foreign town for a while, to bittorrent off of or update their systems.

---

