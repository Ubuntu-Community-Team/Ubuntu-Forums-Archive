---
title: "BT Speedtest Terminology?  IP Profile?"
date: 2007-12-04
forum: The Cafe
---

### Post by MonkeyBoy on 2007-12-04
I have been doing the speedtester.bt.com test for Pipex, my isp, because I have been having problems with my speed.  I keep getting results like:

> Test1 comprises of Best Effort Test:  -provides background information.

    IP profile for your line is - 135 kbps

    DSL connection rate: 448 kbps(UP-STREAM)  6976 kbps(DOWN-STREAM)

    Actual IP throughput achieved during the test was - 112 kbps

Can anyone explain what these terms actually mean?  I just spoke to Pipex tech support and they were a bit condescending but I got the impression they didn't know what these numbers mean either.

I am particularly interested in what an IP Profile is as I suspect this has some deep relevance in my problems.

Apologies if this would be best posted elsewhere.

---

### Post by Lostincyberspace on 2007-12-04
Could you put up a link to it so I can check the above mention address doesn't work. But I think that is the speed you should get.

I think it is made up though for them because a real Ip profile is like your Ip address.

---

### Post by mips on 2007-12-04
>      IP profile for your line is - 135 kbps

    DSL connection rate: 448 kbps(UP-STREAM)  6976 kbps(DOWN-STREAM)

    Actual IP throughput achieved during the test was - 112 kbps

Basically says:

Actual **physical** line speed is 448kb/s up, 6976kb/s (6Mb/s) down.

The actual speed you are getting is 112kb/s which is way below what it should be.

---

### Post by MonkeyBoy on 2007-12-04
Sorry I put the wrong url there.  It should be [this]("http://speedtester.bt.com/").  The IP profile is the mystery part really.  I get the impression from googling it that it is some sort of choke on my speed but I'm not sure.

---

### Post by gn2 on 2007-12-04
Quote:
Test1 comprises of Best Effort Test: -provides background information.

IP profile for your line is - 135 kbps

DSL connection rate: 448 kbps(UP-STREAM) 6976 kbps(DOWN-STREAM)

Actual IP throughput achieved during the test was - 112 kbps 

OK here goes:

IP profile: this is the speed at which the exchange will attempt to communicate with your router.

DSL Connection rate: This is the fastest speed attainable on your line.

Actual throughput rate: self explanatory.

You have a simply dreadful speed result there.

Lots of useful UK ADSL info at [www.kitz.co.uk](www.kitz.co.uk)

---

### Post by MonkeyBoy on 2007-12-04
Cheers!  That is excellent gn2.  That link explains it all.  I suspected it was something like that but couldn't get confirmation.

It sounds like Pipex need to get BT to reset my profile so I can build it up to a reasonable speed again.  I don't know why it went that low though.  I use to get 5000-6000 until last week.

---

### Post by gn2 on 2007-12-04
> **MonkeyBoy said:**
> 
It sounds like Pipex need to get BT to reset my profile so I can build it up to a reasonable speed again.  I don't know why it went that low though.  I use to get 5000-6000 until last week.
.
Could have been any number of things.
Has there been any alteration to your phone wiring or extension cables?
I had an upgrade to Sky+ yesterday and the engineer left the Sky+ phone line unfiltered.
I was not amused when I came home from work and the internet speed had dropped to 1meg :(
Had a look behind the sofa and found the adsl filter lying on the carpet.
Plugged back in and normal service resumed :)

You need to continue doing more speed tests through the BT Speedtester and keep a file of the URL's of the results then e-mail Pipex support with them and get them to extract the digit regarding the profile.

You may also have fallen foul of the FUP/AUP if you've been downloading heavily?
Some ISP's will dramatically throttle you for downloading what they deem as too much.

---

