---
title: "How do I find all IP ranges owned by Comcast?"
date: 2007-08-21
forum: The Cafe
---

### Post by izanbardprince on 2007-08-21
I want to set up a ban for bittorrent traffic to Comcast subscribers, this Comcast deal has effectively turned them all into leechers, and the situation has to be dealt with.

As long as they are able to receive packets, they won't see a problem, we need to hit them right between the eyes with a wake up call and get them to move to another ISP.

Edit: Attached the file to block all IP ranges owned by Comcast, in P2P format, with a copy of Peerguardian.

---

### Post by Kingsley on 2007-08-21
That's an a--hole thing do. Comcast happens to be the best cable internet provider for my location.

---

### Post by Polygon on 2007-08-21
This could work both ways... since comcast users are still able to seed to each other...

but again, its not our fault! i personally seed everything i can to a 2.0 ration but its not my fault that comcast banned us from seeding, i cannot get any other isp and i would see if i was able too.

---

### Post by misfitpierce on 2007-08-21
I can still seed to ppl encrypted and do so. I changed default port which may be a good idea... Mine is at 5188-5189 for torrents. :)

---

### Post by Atreus12 on 2007-08-21
Well, whois didn't give me much useful information

```

user@box:~$ whois comcast.net

Whois Server Version 2.0

Domain names in the .com and .net domains can now be registered
with many different competing registrars. Go to http://www.internic.net
for detailed information.

   Domain Name: COMCAST.NET
   Registrar: NETWORK SOLUTIONS, LLC.
   Whois Server: whois.networksolutions.com
   Referral URL: http://www.networksolutions.com
   Name Server: ADNS.CMC.COMCAST.NET
   Name Server: DNS01.JDC01.PA.COMCAST.NET
   Name Server: DNS02.JDC01.PA.COMCAST.NET
   Status: clientTransferProhibited
   Updated Date: 05-oct-2006
   Creation Date: 25-sep-1997
   Expiration Date: 24-sep-2008

>>> Last update of whois database: Tue, 21 Aug 2007 21:27:38 UTC <<<

Get a FREE domain name registration, transfer, or renewal with any annual hosting package
- or just $8.95 with monthly packages.

http://www.networksolutions.com

Visit AboutUs.org for more information about COMCAST.NET
<a href="http://www.aboutus.org/COMCAST.NET">AboutUs: COMCAST.NET </a>


Registrant:
Comcast Corporation
   1500 Market Street
   Philadelphia, PA 19102
   US

   Domain Name: COMCAST.NET

   Administrative Contact:
      Administrator, Domain Registration ContactMiddleName              domregadmin@COMCAST.net
      Comcast Corporation
      1500 Market, West Tower
      Philadelphia, PA 19102
      US
      215-320-8774 fax: 215-564-0132

   Technical Contact:
      Technical Contact, Domain Reg ContactMiddleName           domregtech@comcastonline.com
      Comcast Corporation
      1500 Market St.
      9Fl West
      Philadelphia, PA 19102
      US
      215-320-8774 fax: 215-564-0132

   Record expires on 24-Sep-2008.
   Record created on 25-Sep-1997.
   Database last updated on 21-Aug-2007 17:28:21 EDT.

   Domain servers in listed order:

   ADNS.CMC.COMCAST.NET         68.87.66.172
   DNS01.JDC01.PA.COMCAST.NET   68.87.96.3
   DNS02.JDC01.PA.COMCAST.NET   68.87.96.4


```

So after digging a bit further, comcast owns a bunch of small ranges of ip addresses. Sneaky sneaky.

Go to [Ip Index](http://ipindex.homelinux.net/) and on the left side search for 'comcast'

There's a lot of ranges.

-Andrew

---

### Post by sumguy231 on 2007-08-21
> we need to hit them right between the eyes with a wake up call and get them to move to another ISP.
Comcast has a monopoly over cable broadband here. Blocking Comcast users because the only cable ISP in their area happens to be run by jerks is a jerk move itself. I don't like this any more than you do.

---

### Post by juxtaposed on 2007-08-21
The "no seeding" thing is rolling, as in not everyone with comast can't seed at once. Some can at different times.

It will be for everyone all the time soon though.

---

### Post by tbroderick on 2007-08-21
As a Comcast user, my seeding has been unaffected. Comcast is the only broadband provider in my town. DSL is not available. I see no problem if Comcast or any ISP decides to throttle bittorrent activity during times of heavy internet traffic as long as they inform the customers that they are doing it.

---

### Post by izanbardprince on 2007-08-21
Attached a copy of Peerguardian with Comcast.p2p, it will block all IP ranges owned by Comcast.

I'm also making this into a torrent, plan on posting it to The Pirate Bay and Torrent Reactor.

---

### Post by init1 on 2007-08-21
> **Kingsley said:**
> That's an a--hole thing do. Comcast happens to be the best cable internet provider for my location.
And preventing people from seeding isn't?

---

### Post by BoyOfDestiny on 2007-08-21
Why not recommend this to comcast users, instead of outright blocking them?

[http://www.whalesalad.com/2006/08/27/tunneling-bittorrent-over-ssh/](http://www.whalesalad.com/2006/08/27/tunneling-bittorrent-over-ssh/)

:)

Also, just curious, to comcast users... Does their "block" work on things like bittornado, which uses random ports (10000-60000)?

---

### Post by Depressed Man on 2007-08-21
I think it has to do with the way Comcast attacks bittorenting (something about sending RST packets)

---

### Post by tbroderick on 2007-08-21
> **izanbardprince said:**
> Attached a copy of Peerguardian with Comcast.p2p, it will block all IP ranges owned by Comcast.

I'm also making this into a torrent, plan on posting it to The Pirate Bay and Torrent Reactor.

Can I block your IP?

---

### Post by Dimitriid on 2007-08-21
Comcast users I feel your pain, for years my city only had dial up ( and its a pretty big city, 5 million ) then a cable company gave you only like 500mb per month and charged 10 cents per megabyte after. 

After that ISDN was offered but they ISDN company was the same as the phone company so they where interested in getting you to make more phone calls ( you only get 100 free local calls per month after that is charged ) so they always booted me off after 8 hours. 

Nowadays there finally is so so connections but I am still fairly limited on my experience, when they say ADSL they really mean it: 1mb down and 128kb up :mad: 

I even remember when the entire dal.net irc network just decided to ban my entire country, but then and now I've always been hunting for solutions. So do not give up, give the ssh tunneling thing a try, check satellite services, etc.

---

### Post by tgm4883 on 2007-08-21
> **izanbardprince said:**
> I want to set up a ban for bittorrent traffic to Comcast subscribers, this Comcast deal has effectively turned them all into leechers, and the situation has to be dealt with.

As long as they are able to receive packets, they won't see a problem, we need to hit them right between the eyes with a wake up call and get them to move to another ISP.

Edit: Attached the file to block all IP ranges owned by Comcast, in P2P format, with a copy of Peerguardian.

Sweet, thanks for being a dick

---

### Post by Polygon on 2007-08-22
> **izanbardprince said:**
> I want to set up a ban for bittorrent traffic to Comcast subscribers, this Comcast deal has effectively turned them all into leechers, and the situation has to be dealt with.

As long as they are able to receive packets, they won't see a problem, we need to hit them right between the eyes with a wake up call and get them to move to another ISP.

Edit: Attached the file to block all IP ranges owned by Comcast, in P2P format, with a copy of Peerguardian.

thanks, jerk. That will show us comcast users, one person using a peerguardian block list of all comcast ips. Whee.

---

### Post by izanbardprince on 2007-08-22
> **Polygon said:**
> thanks, jerk. That will show us comcast users, one person using a peerguardian block list of all comcast ips. Whee.

I could give a crap, I made that list because, I personally don't want them draining my bandwidth and giving nothing back in return.

---

### Post by Polygon on 2007-08-22
> **izanbardprince said:**
> I could give a crap, I made that list because, I personally don't want them draining my bandwidth and giving nothing back in return.

what about all the other people who are perfectly capable of giving back but dont anyway? make a block list for them?

and besides, when we are downloading our upload is fine, its only after we are done that we cant upload. (very well)

---

### Post by hanzomon4 on 2007-08-22
This will only stick it to the consumer not the man.. Try looking for a way to help Comcast users circumvent this BT seeding "block".

---

### Post by izanbardprince on 2007-08-22
> **Polygon said:**
> what about all the other people who are perfectly capable of giving back but dont anyway? make a block list for them?

and besides, when we are downloading our upload is fine, its only after we are done that we cant upload. (very well)

There has to be something you can do, this isn't 1998, DSL is practically everywhere, fiber optics is gaining popularity, broadband over power lines is being tested in several cities, and even if you're out in the stix, there's still satellite.

Also, there are many ISP's still supporting ISDN.

I too once had Comcast, the service was terrible, sometimes the internet service would go out, with no explanation, over several city blocks, and Comcast wouldn't fix it for hours, if not a day or two, it was about twice as expensive as my DSL line, and about half the speed.

---

### Post by tbroderick on 2007-08-22
> **izanbardprince said:**
> There has to be something you can do, this isn't 1998, DSL is practically everywhere, fiber optics is gaining popularity, broadband over power lines is being tested in several cities, and even if you're out in the stix, there's still satellite.

Or do [this]("http://thaking.net/pages/comcast-fix/").

---

### Post by rivalarrival on 2007-08-23
I'm thinking more from the viewpoint of webmasters...  It shouldn't be hard to target Comcast traffic to your website/blog/etc with a message of what's going on and links where Comcast customers can complain.

The more dedicated among you could provide links to competing ISP's in the user's region.

It can't be hard - if I believed the ads I see, my town's population is 80% 18-26 year old hot, semi naked chicks looking for me.  (Wish one of them wold find me already...)

---

### Post by Transient77 on 2007-10-26
> **izanbardprince said:**
> I want to set up a ban for bittorrent traffic to Comcast subscribers, this Comcast deal has effectively turned them all into leechers, and the situation has to be dealt with.

As long as they are able to receive packets, they won't see a problem, we need to hit them right between the eyes with a wake up call and get them to move to another ISP.

Edit: Attached the file to block all IP ranges owned by Comcast, in P2P format, with a copy of Peerguardian.

Thanks!! You didn't get them all, but I can probably manually find the rest.

BTW, if anyone is interested, I used this blocklist converter to convert this into eDonkey format for use with uTorrent:
[http://www.bluetack.co.uk/convert.html](http://www.bluetack.co.uk/convert.html)

For all the Comcast users, sorry you have to get caught up in the crossfire. But I agree with the original poster. 

I'm passing this along to several of my friends, so there's going to be at least 20 people using it. Hopefully it catches on.

---

### Post by LowSky on 2007-10-26
I'm sorry to all those people who are affected for doing absolutly nothing wrong, but comcast has the right to limit what you do over their network. If you don't like it switch to another provider.

---

### Post by Sunflower1970 on 2007-10-26
Comcast may have stopped their throttling of  bittorrent traffic, according to one user:
[http://consumerist.com/consumer/comcast/comcast-ceases-throttling-traffic-after-negative-ap-story-314759.php](http://consumerist.com/consumer/comcast/comcast-ceases-throttling-traffic-after-negative-ap-story-314759.php). 

Amusingly, this has made it all the way to Congress... [http://valleywag.com/tech/politics/congressman-tells-comcast-to-play-nice-and-share-315109.php](http://valleywag.com/tech/politics/congressman-tells-comcast-to-play-nice-and-share-315109.php)

Comcast isn't the only broadband provider who does something like this. So does Time Warner...Not bittorrent traffic that I know of, since I don't use it...if one downloads a large item...such as a ton of different ISO's for different distros, which I have, they'll reset my modem to try and stop the download.  Interestingly enough, the resetting of my modem used to happen every few hours when using Windows, whether I was downloading something or not...when I switched to Ubuntu, the restting happens only every few days, or sometimes I can go weeks before it happens....but it sure is annoying when one is trying to win an auction on Ebay and in the last minute or so of the auction all of a sudden the modem goes out for a reset....AAUUGHH!

---

### Post by agurk on 2007-10-26
Blocking Comcast *is* the apropriate response to such behaviour and it has worked in the past, for example when thepiratebay.org blocked the Perspektiv network. If you have no other ISP in your area but Comcast, just hang in there until Comcast caves in. And they will.

---

### Post by jc87 on 2007-10-26
Why don´t you change to other p2p tools that benefit thoose who share?

I know it sucks, but all around the world there are crappy ISP´s that make users leechers against their will, for instance i´m Portuguese and my ISP package (netvisao) is the following:

Download speed -  2mbps

Upload speed - 128kbps

Traffic limit - 13 gigabytes 

Happy hour - From 01:00 am to 09:00 (no traffic is counted during this period)

I pay for it about 25 euros month, and extra 1,75 euros for each extra 100 megabytes

I would seed more if i could, but except for P2P i´m currently happy with my ISP (good gaming pings and network stability, wasn´t always like that in the past but improved a lot)

If they increase upload speed in the next upgrade i will seed more, otherwise i will only share the litle i can in the moment ( in Portugal ISP´s suck a lot)

---

### Post by cyberdyne2 on 2008-11-13
> **izanbardprince said:**
> I want to set up a ban for bittorrent traffic to Comcast subscribers, this Comcast deal has effectively turned them all into leechers, and the situation has to be dealt with.

As long as they are able to receive packets, they won't see a problem, we need to hit them right between the eyes with a wake up call and get them to move to another ISP.

Edit: Attached the file to block all IP ranges owned by Comcast, in P2P format, with a copy of Peerguardian.

[http://postmaster.comcast.net/dynamic-IP-ranges.aspx](http://postmaster.comcast.net/dynamic-IP-ranges.aspx)

---

### Post by tgm4883 on 2008-11-13
> **cyberdyne2 said:**
> [http://postmaster.comcast.net/dynamic-IP-ranges.aspx](http://postmaster.comcast.net/dynamic-IP-ranges.aspx)

Note only did you reply to a thread that is over a year old, but this thread already has the list posted in the first thread (it's an attachment).  Thanks you for posting, but in the future please look at what you are posting to.

---

