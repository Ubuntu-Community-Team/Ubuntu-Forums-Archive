---
title: "The joys of ISPs throttling legal (Ubuntu) Bittorrent"
date: 2008-04-24
forum: The Cafe
---

### Post by Mazza558 on 2008-04-24
I thought I'd start my download of 8.04, and... yeah... I think you should look at the attachment.

I'm going to have to use the http method instead... :(

---

### Post by blithen on 2008-04-24
Wow! I'm sorry man. mine was downloaded within a half hour. D:

---

### Post by Andrewie on 2008-04-24
20 days isn't that long...

---

### Post by TBOL3 on 2008-04-24
I actually spent a week downloading the Mancand FAQ at a wapping average of about 10 KB, can you say sloowwwwww.......

---

### Post by zekopeko on 2008-04-24
hmmm... try deluge (if that isn't it in the pic). it might avoid bt throttling.

---

### Post by Bölvaður on 2008-04-24
I know there is a way behind this, but I've never managed to do it :(

---

### Post by Washer on 2008-04-24
you've tried azureus encryption & all? I have comcast & either they're not throttling me, or i've got mad skills.

---

### Post by klange on 2008-04-24
My deepest of sympathies, Mazza.

---

### Post by p_quarles on 2008-04-24
I downloaded the torrent on Comcast myself (for no reason other than to seed, actually) and got between 750 and 1,200 Kb/s. I believe that the public reaction to their throttling -- along with the current FCC investigation into the practice -- has made them curb their traffic shaping considerably. 

For those on ISPs that continue to do that: my condolences.

---

### Post by abuakel on 2008-04-24
That's ridiculous! 
Back during my XP days, I used bit torrent to download a friend's video and it clocked at a speedy 2 kb/s.. took three days! It was probably because I was in another country 'stealing' someone's internet and the connection was atrocious...but the frustration was unbelievable, multiple times I had the urge of throwing my computer across the room! ](*,) 

yes.. http is much faster \\:D/

---

### Post by rune0077 on 2008-04-24
Change the incoming port of your torrent-client to some very high number (like 70000 and something). That ought to fix it (at least if it's throttling, though it may also - more likely with such a low speed - be a firewall somewhere blocking you).

---

### Post by Eclipse. on 2008-04-24
uTorrent works perfect with wine and has protocol encryption, you could try that.I'm seeding with it atm.

---

### Post by gsmanners on 2008-04-24
If you have problems with Comcast, this might be of interest:

[http://torrentfreak.com/how-to-bypass-comcast-bittorrent-throttling-071021/](http://torrentfreak.com/how-to-bypass-comcast-bittorrent-throttling-071021/)

---

### Post by SuperSon!c on 2008-04-24
you can thank most of your buddies and, quite frankly, quite a few people on this forum for ISP's doing this.

---

### Post by gsmanners on 2008-04-24
You're welcome. :)

And if Comcast cuts your line altogether maybe you can thank *them* by using a real ISP.

---

### Post by rune0077 on 2008-04-24
> **SuperSon!c said:**
> you can thank most of your buddies and, quite frankly, quite a few people on this forum for ISP's doing this.

Not really, I think. Throttling does not mean stopping your torrent, it means slowing it down. They're not throttling you to stop illegal activity, they do it to decrease bandwidth traffic and prevent it from burdening their infrastructure (much the same way you put speedlimits and traffic lights on city roads).

---

### Post by SuperSon!c on 2008-04-24
don't thank me, i couldn't care less. so far, i'm not affected.

---

### Post by SuperSon!c on 2008-04-24
> **rune0077 said:**
> Not really, I think. Throttling does not mean stopping your torrent, it means slowing it down. They're not throttling you to stop illegal activity, they do it to decrease bandwidth traffic and prevent it from burdening their infrastructure (much the same way you put speedlimits and traffic lights on city roads).

i never said stopping. i know exactly what throttling is.  perhaps comcast's definition is stoppage. comcast is one of the worst providers in the states.

---

### Post by Mazza558 on 2008-04-24
I'm not on Comcast (though it sounds pretty painful). I'm in the UK.

---

### Post by rune0077 on 2008-04-24
> **SuperSon!c said:**
> i never said stopping. i know exactly what throttling is.  perhaps comcast's definition is stoppage. comcast is one of the worst providers in the states.

Oh okay. Really, wouldn't blocking your connection completely be considered kind of an illegal move on their part, in the States? I mean, they can't prevent you from using a service that you are paying them for? My ISP would never be allowed to pull a stunt like that.

---

### Post by Mateo on 2008-04-24
well, the DVD is very slow apparently. everyone i've talked to who is getting the DVD (myself included) is saying their downloads are all below 100k.  mine peaked at 80k.

---

### Post by p_quarles on 2008-04-24
> **rune0077 said:**
> Oh okay. Really, wouldn't blocking your connection completely be considered kind of an illegal move on their part, in the States? I mean, they can't prevent you from using a service that you are paying them for? My ISP would never be allowed to pull a stunt like that.
As I said above, Comcast is currently under investigation by a U.S. regulatory body for their traffic-shaping activities. It's not clearly illegal, but it may be found to be so.

---

### Post by rune0077 on 2008-04-24
> **p_quarles said:**
> As I said above, Comcast is currently under investigation by a U.S. regulatory body for their traffic-shaping activities. It's not clearly illegal, but it may be found to be so.

Let's cross our fingers and hope they get the knife :)

---

### Post by SuperSon!c on 2008-04-24
> **rune0077 said:**
> Change the incoming port of your torrent-client to some very high number (like 70000 and something). That ought to fix it (at least if it's throttling, though it may also - more likely with such a low speed - be a firewall somewhere blocking you).

actually that may not do anything.  traffic shaping has the ability to check packet strings which are 19 bytes for bit torrent and effectively slow (shape) that traffic as it sees fit.

---

### Post by rune0077 on 2008-04-24
> **SuperSon!c said:**
> actually that may not do anything.  traffic shaping has the ability to check packet strings which are 19 bytes for bit torrent and effectively slow (shape) that traffic as it sees fit.

My ISP just throttles the default torrent ports. Anything higher than that, and you're fine. Guess it's different for different ISP's.

---

### Post by SuperSon!c on 2008-04-24
> **rune0077 said:**
> Oh okay. Really, wouldn't blocking your connection completely be considered kind of an illegal move on their part, in the States? I mean, they can't prevent you from using a service that you are paying them for? My ISP would never be allowed to pull a stunt like that.

as Quarles said, they're under investigation.  although i don't agree with an ISP shaping *what* you should be downloading, i'm not against ISP's tiering their packages by bandwidth.

---

### Post by SuperSon!c on 2008-04-24
> **rune0077 said:**
> My ISP just throttles the default torrent ports. Anything higher than that, and you're fine. Guess it's different for different ISP's.

yeah, i'm sure they're all doing their own thing so YMMV.

---

### Post by p_quarles on 2008-04-24
> **SuperSon!c said:**
> as Quarles said, they're under investigation.  although i don't agree with an ISP shaping *what* you should be downloading, i'm not against ISP's tiering their packages by bandwidth.
Yeah, and that's actually the subject of the investigation. Comcast at first said they were throttling torrent traffic during high-traffic times, and in crowded infrastructure. What's coming to light, however, is that it was much more wide-spread than that.

---

### Post by SuperSon!c on 2008-04-24
> **Mazza558 said:**
> I'm not on Comcast (though it sounds pretty painful). I'm in the UK.

that's good news, although you also have [this to deal with]("http://www.telegraph.co.uk/connected/main.jhtml?xml=/connected/2008/04/10/dlweb110.xml").

---

### Post by SuperSon!c on 2008-04-24
> **p_quarles said:**
> Yeah, and that's actually the subject of the investigation. Comcast at first said they were throttling torrent traffic during high-traffic times, and in crowded infrastructure. What's coming to light, however, is that it was much more wide-spread than that.

exactly.  although i can see their reasoning to an extent to use traffic shaping, an ISP would have to be totally up front in detail when you sign a contract with them, imo.  obviously it seems that comcast has earned its bad reputation.

---

### Post by klange on 2008-04-24
The official torrent was running at around 700kb/s for me. I'm currently seeding with a ~50kb/s upload rate.

---

### Post by Joeb454 on 2008-04-24
My downloads were around 60-150 kb/s down :(

I even had encryption enabled, though it definitely helps to have the torrents encrypted :)

---

### Post by LightB on 2008-04-24
Your locations matters a lot. I don't think most people huddled together in large cities understand it, it's just a lot easier to provide cheap, fast access in those places. But if you live in smaller towns, or worse yet, the sticks, the ISPs really take you to town reducing the speeds while increasing the prices. At least that's how it is in the US. I know in other smaller countries even more remote areas get really nice connections for a good price.

---

### Post by bruce89 on 2008-04-24
It took me about 9 hours here with Pipex.

Funny thing is my connection up in Craobh (in the countryside) is twice as fast as here.

---

### Post by Phil Airtime on 2008-04-24
> **bruce89 said:**
> It took me about 9 hours here with Pipex.

Funny thing is my connection up in Craobh (in the countryside) is twice as fast as here.

I have an ADSL Max connection here which fluctuates around the 2Mb mark, while where I stay in the Hebrides we get the full 8Mb. City centres and rural areas seem to have it good because of distance from the exchange, but if you're in the suburbs you're more likely to have a bad connection.

---

### Post by Flying caveman on 2008-04-25
I have comcast and I was able to use the torrent, it was fast but when it finished, I lost my connection when I was trying to seed. 

EDIT: No its not just a coincidence it only quits when i'm trying to use torrents.  And by "throttling" they mean "killing your connection" I'm tired of unpluging/re-plugging my router, otherwise  I would seed for the next week.

---

### Post by Paqman on 2008-04-25
I'm glad Transmission is included in Hardy by default. Encrypted torrents are going to become ever more useful as the ISPs ramp up their traffic shaping. Azureus is great, but it's pretty huge and unwieldy.

---

### Post by wolfen69 on 2008-04-25
> **Mazza558 said:**
> I thought I'd start my download of 8.04, and... yeah... I think you should look at the attachment.

I'm going to have to use the http method instead... :(

you might be able to get around that by using a torrent client that supports encryption, such as deluge or ktorrent. also change the default ports to a high number such as 51378. default is 6xxx, and isp's know this.

---

### Post by SuperSon!c on 2008-04-25
> **Flying caveman said:**
> I have comcast and I was able to use the torrent, it was fast but when it finished, I lost my connection when I was trying to seed. 

EDIT: No its not just a coincidence it only quits when i'm trying to use torrents.  And by "throttling" they mean "killing your connection" I'm tired of unpluging/re-plugging my router, otherwise  I would seed for the next week.

actually, that's a common problem with routers using stock firmware, not a blame on your ISP.

---

### Post by Tom Mann on 2008-04-25
I did the following:

- Downloaded the ISO and torrent file via HTTP
- started the torrent, then closed the transmission
- md5summed the ISO to check it was ok, then copied it over the iso transmission made
- started transmission that confirmed my file was ok, then seeded it

:guitar:

---

### Post by SunnyRabbiera on 2008-04-25
> **p_quarles said:**
> I downloaded the torrent on Comcast myself (for no reason other than to seed, actually) and got between 750 and 1,200 Kb/s. I believe that the public reaction to their throttling -- along with the current FCC investigation into the practice -- has made them curb their traffic shaping considerably. 

For those on ISPs that continue to do that: my condolences.

Yeh, I was able to cut around the throttling thanks to bit tornado by constantly changing the download speed... like a manual car, from dialup speed up to t3...
mess with em :D

---

