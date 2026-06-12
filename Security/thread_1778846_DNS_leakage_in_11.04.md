---
title: "DNS leakage in 11.04"
date: 2011-06-09
forum: Security
---

### Post by desire.linux on 2011-06-09
One thing that's really starting to annoy me with 11.04 is the random DNS requests it spits out to the internet DNS servers. I can boot up that computer for weeks without this happening, but some random days it spits out a DNS request during login to my admin user account. I'm talking about a clean fresh install.

I have disabled avahi-daemon from staring up and disabled ntpdate as a part of finding out what's up.

According to my router's logs, it never communicates with any servers, just sends a DNS request. It only logs a LAN to LAN packet on port 53, but never any LAN to WAN packets.

What's up with this? Help is appreciated, thanks!

---

### Post by desire.linux on 2011-06-09
It seems to be related to geoip.ubuntu.com. When I restart network-manager, it does a DNS query on that address.

Why is that?

---

### Post by judderwocky on 2011-06-11
not quite sure, i've noticed the computer contacting the ubuntu one server sometimes...

you could use privoxy to lock it down... 

you could use an ip tables script to drop all outbound packets associated with your user.. and then just route all your 'intentional' traffic through the privoxy internal port .... i think its  127.0.0.8118 maybe...

---

### Post by desire.linux on 2011-06-13
The reason for leaving Microsoft Windows was to protect my privacy. Windows sends unknown packets from my computer to all over the internet. Ubuntu seems to be not much better. It seems to be the exact same and potential spy OS as Windows that randomly sends packets from my computer **without** my consent and even when all internet applications are disabled: Ubuntu One, auto update, avaihi, ntpdate, everything is disabled, still it sends random DNS requests and even contacts the outside world a few times when it feels like. What information is sent? It's impossible to know for sure, and it seems like the rest of the community doesn't care much either. Maybe because most of you came from Windows? I don't know but I feel so many similarities between Ubuntu and Windows, especially when you'll need to firewall your Ubuntu box to keep it from sending out random and inconsistent TCP packets. That doesn't actually solve anything, it's just like if you see a warning light in your car, and you cut off the wires to the warning led, and then everything is just fine. But it isn't. But thanks for trying to help anyway.

---

### Post by redmk2 on 2011-06-13
> **desire.linux said:**
> The reason for leaving Microsoft Windows was to protect my privacy. Windows sends unknown packets from my computer to all over the internet. Ubuntu seems to be not much better. It seems to be the exact same and potential spy OS as Windows that randomly sends packets from my computer **without** my consent and even when all internet applications are disabled: Ubuntu One, auto update, avaihi, ntpdate, everything is disabled, still it sends random DNS requests and even contacts the outside world a few times when it feels like.
You answered your own question a few posts back.  What you are seeing is a *request* to GeoIP for updates to the GeoIP database on your machine using the DNS port #53.  It is not DNS though.  It uses this port because it is always known to be open.  Not very well behaved in my opinion, but there is no technical reason why this can't be done.  GeoIP  is a mapping of IP to location (by continent I believe).> 
What information is sent? It's impossible to know for sure,
It is a request for information.  You can always fire up Wireshark and look at what information is in the packets.> 
 and it seems like the rest of the community doesn't care much either.
This is an increasingly socially connected world.  People want to know things... :-(> 
Maybe because most of you came from Windows? I don't know but I feel so many similarities between Ubuntu and Windows, especially when you'll need to firewall your Ubuntu box to keep it from sending out random and inconsistent TCP packets. 
I think rather that just ranting you should learn how the OS works and modify it to your liking  I have no GeoIP packets eminating from my 10.04 DE hosts.> 
That doesn't actually solve anything, it's just like if you see a warning light in your car, and you cut off the wires to the warning led, and then everything is just fine. But it isn't. But thanks for trying to help anyway.
You can always disable Network-Manager (the actual requester of the GeoIP information) or switch to WICD if you are using wireless. 

All of my wired hosts are manually configured at the lowest level.  No GeoIP data at all on these hosts.  The doc's are there describing it, but no downloaded information.

---

### Post by desire.linux on 2011-06-13
> **redmk2 said:**
> You answered your own question a few posts back.

No, you did:

> *You can always disable Network-Manager (the actual requester of the  GeoIP information) or switch to WICD if you are using wireless.*BTW, it's not only DNS requests that are sent. Also ordinary requests on port 80. So far it's only to an IP owned by **Canonical ltd Admin**, but please note that automatic updates are disabled.

You write that I must learn how the OS works and configure it to my needs, that is what I want to do, but I can't because the thing that happens and concerns me isn't consistent so I can't track the problem down. Ubuntu decides, a few times now and then, to send information to Canonical during startup. I can run wireshark for two weeks all day long while rebooting 1000 times a day, and it doesn't happen again. Until one random day much later, when I'm too tired to run wireshark and when I'm not checking, it happens again.

The inconsistence is what scares me. Normally it should have been a consistent startup script or a cron job that runs regularly and predictably for a specific reason, but it isn't. For all I know it could be FBI or NSA cooperating with Canonical "in the war against terror" or something to gather private data about us and our usage. No conspiracy lunacy intended, this inconsistency it's just a general great great idea to make it difficult for the users of Ubuntu to actually do what you ask me to do, learn how the OS work and tune it to my needs. Even the logs doesn't tell me anything and that's even greater... less control and less supervision for the end user.

I don't mean to hurt Canonical's feelings intentionally, I do love Ubuntu, except for the bad Microsoft vibes I get regarding lack of control, supervision and possibly privacy. 10.04 seems to behave well, but what comes after doesn't.

---

### Post by capscrew on 2011-06-13
My mistake -- wrong post.

But I can't resist commenting...

> For all I know it could be FBI or NSA cooperating with Canonical "in the war against terror" or something to gather private data about us and our usage.   I wouldn't worry about that.  Say what  you want about Canonical but hiding info or being secretive in any way is not in their interests.  It is FOSS from kernel to applications and as such is available as source code.  I'm sure if there was something nefarious we would all know it.

---

### Post by redmk2 on 2011-06-14
> **desire.linux said:**
> No, you did:

BTW, it's not only DNS requests that are sent. Also ordinary requests on port 80. So far it's only to an IP owned by **Canonical ltd Admin**, but please note that automatic updates are disabled.
I'm always up for something interesting.   This is part of Ubuntu's implementation of geo-location of IP addresses.  It appears that Canonical is running the server with the GeoIP database.  Querying [**_[COLOR="DarkSlateGray"]their database[/COLOR]_**]("http://geoip.ubuntu.com/lookup") will return an XML response in my web browser.  i can see this in wireshark too.> 

You write that I must learn how the OS works and configure it to my needs, that is what I want to do, but I can't because the thing that happens and concerns me isn't consistent so I can't track the problem down. Ubuntu decides, a few times now and then, to send information to Canonical during startup. I can run wireshark for two weeks all day long while rebooting 1000 times a day, and it doesn't happen again. Until one random day much later, when I'm too tired to run wireshark and when I'm not checking, it happens again.

The inconsistence is what scares me. Normally it should have been a consistent startup script or a cron job that runs regularly and predictably for a specific reason, but it isn't. For all I know it could be FBI or NSA cooperating with Canonical "in the war against terror" or something to gather private data about us and our usage. No conspiracy lunacy intended, this inconsistency it's just a general great great idea to make it difficult for the users of Ubuntu to actually do what you ask me to do, learn how the OS work and tune it to my needs. Even the logs doesn't tell me anything and that's even greater... less control and less supervision for the end user.
The GeoIP database is nearly ubiquitous.  See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.maxmind.com/app/geoip_resources") for for a list of the possibilities.  It can be triggered by multiple applications.  Maybe this is the apparent randomness.> 

I don't mean to hurt Canonical's feelings intentionally, I do love Ubuntu, except for the bad Microsoft vibes I get regarding lack of control, supervision and possibly privacy. 10.04 seems to behave well, but what comes after doesn't.
i believe you are correct.  Once again you can always experiment with removing the offending packages.  Welcome to the cutting edge.  :-)

---

### Post by desire.linux on 2011-06-14
> **capscrew said:**
> My mistake -- wrong post.

But I can't resist commenting...

  I wouldn't worry about that.  Say what  you want about Canonical but hiding info or being secretive in any way is not in their interests.  It is FOSS from kernel to applications and as such is available as source code.  I'm sure if there was something nefarious we would all know it.

No one knows for sure what lays in anyone's interest, but you're probably right. I have no real proofs of Canonical being malicious other than their hunger for random TCP packets from their users.

Open source software is definitely a false sense of security. How many people are actually traveling trough every line of code in e.g. Ubuntu? Person A says "Hey, I'm pretty secure, because even though I don't read any code of my open source software, person B does all that for me, and that's so nice!". The problem is that person B says the same about A. Hopefully there's a C involved here ... who is a hardcore Ubuntu geek with the same amount of paranoia as myself.

---

### Post by desire.linux on 2011-06-14
> **redmk2 said:**
> I'm always up for something interesting.   This is part of Ubuntu's implementation of geo-location of IP addresses.  It appears that Canonical is running the server with the GeoIP database.  Querying [**_[COLOR=DarkSlateGray]their database[/COLOR]_**]("http://geoip.ubuntu.com/lookup") will return an XML response in my web browser.  i can see this in wireshark too.The GeoIP database is nearly ubiquitous.  See [**_[COLOR=DarkSlateGray]here[/COLOR]_**]("http://www.maxmind.com/app/geoip_resources") for for a list of the possibilities.  **It can be triggered by multiple applications.  Maybe this is the apparent randomness.**

Except for the fact that the same applications are ran at each boot, unless there's some randomness there too that I don't know about. And I've tried to run all the cron jobs too (daily, weekly, monthly), but they didn't trigger this at all.

>  i believe you are correct.  Once again you can always experiment with removing the offending packages.  Welcome to the cutting edge.  :-)

The nice thing about openSUSE is that you can select what packages you want during install, so you can more or less build your own distro during install. I'm not sure if Ubuntu supports the same.

Thanks anyway for baring with me here ;) and trying to help out. :)

---

### Post by cariboo on 2011-06-15
In my experience, geo-ip location doesn't work that well anyhow, it shows my location as being at the end of the third fairway of one of the local golf courses, that is about 10km away by road.

---

### Post by desire.linux on 2011-06-15
> **cariboo907 said:**
> In my experience, geo-ip location doesn't work that well anyhow, it shows my location as being at the end of the third fairway of one of the local golf courses, that is about 10km away by road.

What's the purpose of this application BTW?

Is it possible to deactivate it completely?

---

