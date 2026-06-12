---
title: "Seagate 7200.11 series looks like one to stay away from."
date: 2009-01-18
forum: The Cafe
---

### Post by handy on 2009-01-18
I've been doing a bit of research on drives & found this thread on the overclockers forum; it really looks like this particular series of Seagate drives have a firmware issue:

*_[http://forums.overclockers.co.uk/showthread.php?t=17937547](http://forums.overclockers.co.uk/showthread.php?t=17937547)_*
[B]
*[Edit:][/B] Just found this one too:*

*_[http://www.msfn.org/board/index.php?showtopic=128514&st=0&p=826277&#entry826277](http://www.msfn.org/board/index.php?showtopic=128514&st=0&p=826277&#entry826277)_*

***[Edit:]** & another:*

*_[http://www.engadget.com/2009/01/16/seagate-barracuda-7200-11-drives-said-to-be-failing-at-an-alarmi/](http://www.engadget.com/2009/01/16/seagate-barracuda-7200-11-drives-said-to-be-failing-at-an-alarmi/)_*

***[Edit:]** Seagate acknowledge the problem (at last):*

*_[http://techreport.com/discussions.x/16246](http://techreport.com/discussions.x/16246)_*

*_[http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207931](http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207931)_*

---

### Post by mips on 2009-01-19
Yeah, I read that a few days ago. Might want to wait for the bugs to get sorted or possibly look at WD.

---

### Post by handy on 2009-01-19
I'm pretty keen on the WD green drives, they are quiet & cool, & the way I see it the network speed will be my limiting factor, not the speed of my drives.  I should be able to run 5400 rpm drives in my FreeNAS box, using less power & making even less noise if I buy a quiet drive.

---

### Post by mips on 2009-01-19
Network speed is going to dictate your speed so work according to that unless you ever intend to use the drives for something else.

I had a look at a local online site selling VIA stuff just out of interest and I came to the conclusion that the pricing is just crazy!!! For just a mini-itx board & cpu combo they want about 75% of what I paid for my beast of a desktop which included way more. Will probably be more economical trying to buy something like a Everex gPC which uses the same tech basically if one can be found locally.

---

### Post by handy on 2009-01-19
The intel Atom MiniITX boards are much cheaper than the VIA MiniITX.

They apparently outperform them as well.  If I buy a new board I expect it will be probably be one of these:

*_[http://www.mini-itx.com/reviews/atoms/default.asp?page=6](http://www.mini-itx.com/reviews/atoms/default.asp?page=6)_*

It has more CPU power than I need (& being dual core is nice) which may be useful for soft RAID & who knows what else in the future.

I can buy that board online for $143- Oz, plus freight.

I will buy drives & an adapter so I can run them in my test box, & wait for the inevitable PII/PIII that arrives at the tip to hopefully save me having to spend too much money, as I'd rather save up for a one of those fancy new intel quad-core CPU's & the bits & pieces I need to put one of those things together. :-)  It won't be being used as a NAS box though, that's for sure.

---

### Post by mips on 2009-01-19
That board looks nice and should be easily sourced seeing it is Intel. Would be nice if it had 4x SATA and 2x GBEth connectors. all you need is a Flash-to-IDE adapter for the OS and you are good to go.

---

### Post by adamlau on 2009-01-19
WD green? No way, VelociRaptors all the way :guitar: ...

---

### Post by mips on 2009-01-19
> **adamlau said:**
> WD green? No way, VelociRaptors all the way :guitar: ...

And you are going to benefit how in terms of performance seeing all the data traverses a 100Mb/s LAN from the NAS box?

---

### Post by blastus on 2009-01-19
I started hearing about the firmware issue a few months ago. Buying a Seagate drive these days seems like a crap shoot. I bought four of them last year before summer and fortunately haven't had any issues.

I would not buy another Seagate drive until the reports of bad firmware stop surfacing and Seagate (and everyone on the Internet) identifies a firmware revision # and manufacture date for drives where this issue is resolved. Even then I would still wait 3-4 months just to be sure it's really resolved.

---

### Post by igknighted on 2009-01-19
This is too bad.  As far as construction quality, I consider seagate second to none.  I've never been a WD fan... how are those japanese HD's?

---

### Post by mister_doctor on 2009-01-19
I nearly crapped myself when I read this last week. I bought one of the 1TB drives back in May 2008 before I even knew about any issues with the Seagate 7200.11 drives.

Sure enough AFTER reading the article I start noticing flakiness.

First offense: Girlfriend was watching a TV show on her laptop stored on said drive, connected through a network share. Halfway through it just stops. I got investigate and my system is hung. After a reboot there's not even so much as a log entry...

Second offense: I'm watching a TV show on the box housing said drive. The video stops. The system is hung.

I follow some links to a Seagate knowledgebase entry that contains a "serial number validator". I punch mine in and it claims to be "unaffected". 

Bull. Crap.

I'm seriously considering getting another not-seagate drive... this 1TB unit is already more then half-full. It would take months to re-download all of my beautiful stuff...

---

### Post by mips on 2009-01-19
> **mister_doctor said:**
> I nearly crapped myself when I read this last week. I bought one of the 1TB drives back in [COLOR=Red]**May 2008**[/COLOR] before I even knew about any issues with the Seagate 7200.11 drives.

I follow some links to a Seagate knowledgebase entry that contains a "serial number validator". I punch mine in and it claims to be "unaffected". 

Bull. Crap.

I'm seriously considering getting another not-seagate drive... this 1TB unit is already more then half-full. It would take months to re-download all of my beautiful stuff...

1. Your drive is still under warranty.

2. I would complain and explain to Seagate your simptoms are identical to the affected drives.

3. They are paying for data recovery on these drives.

Make yourself heard!

---

### Post by handy on 2009-01-19
> **adamlau said:**
> WD green? No way, VelociRaptors all the way :guitar: ...

I have a pair of WD360 Raptors, they are the noisiest drive I have ever owned, use extra electricity & offer no benefit whatsoever in a NAS box, as the throughput of your network is the bottleneck, even if I move up to a Gigabit, the network will still very much be the bottleneck when it comes to moving data around the LAN.

---

### Post by handy on 2009-01-19
> **mips said:**
> That board looks nice and should be easily sourced seeing it is Intel. Would be nice if it had 4x SATA and 2x GBEth connectors. all you need is a Flash-to-IDE adapter for the OS and you are good to go.

Some of the other manufacturers will build with 4x SATA & 2x Gb ethernet I'm sure.  They usually always build better quality boards than intel as well.

---

### Post by handy on 2009-01-19
> **blastus said:**
> I started hearing about the firmware issue a few months ago. Buying a Seagate drive these days seems like a crap shoot. I bought four of them last year before summer and fortunately haven't had any issues.

I would not buy another Seagate drive until the reports of bad firmware stop surfacing and Seagate (and everyone on the Internet) identifies a firmware revision # and manufacture date for drives where this issue is resolved. Even then I would still wait 3-4 months just to be sure it's really resolved.

The firmware has been identified it is in one of the links I posted in the OP.

---

### Post by handy on 2009-01-19
> **igknighted said:**
> This is too bad.  As far as construction quality, I consider seagate second to none.  I've never been a WD fan... how are those japanese HD's?

Well I've always considered WD to be a consistent top drive manufacturer, some years ago Seagate had a bad run, as have Maxtor, IBM - the Deathstar lol, & Quantum, there was also the drive who's name I've forgotten that was made in India, they were cheap & noisy & very unreliable (from my experience).

I don't recall WD having such a bad run, but I have not been in the game for a few years now.

I have personally lost Quantum, Seagate, Maxtor & IBM drives & the Indian cheepy. The only WD I lost was a WD360 Raptor, which was DOA, my supplier was really surprised as it was a first for him, & he only supplied dealers so he moved a lot of stock.

Those Japanese HDD's - Hitachi, are great drives, they bought the IBM drive business, & apart from the IBM Deathstar, (I had one of those that died out of warranty & too soon), the IBM - Hitachi drives are excellent quality in my opinion.  I've had Toshiba 2.5" drives die on me but thus far no Hitachi 2.5" drives.

Though the bottom line is they will all die. :-)  It is the workload longevity ratio that we value.

Seagate will sort out the bad firmware problem with their current troubled drives, & people won't loose data when they go that route.

We all make mistakes.

---

### Post by blastus on 2009-01-19
> **handy said:**
> I don't recall WD having such a bad run, but I have not been in the game for a few years now.

WD drives had problems with bearings as they aged (even those from just a few years old.) As the bearings wore they would emit a high-pitched whining noise. I read on silentpcreview.com that they have since fixed the issue. At one time silentpcreview.com removed WD from their recommended drives because of this. 

Every single WD drive I have ever owned ended up having this problem. It is practically unbearable. I still have a 120 GB WD drive from a few years ago that I can literally hear from 25 feet away. It's that loud and because it is so high-pitched it is headache inducing.

---

### Post by mips on 2009-01-20
> **handy said:**
> 
I have personally lost Quantum, Seagate, Maxtor & IBM drives & the Indian cheepy.

I've had Toshiba 2.5" drives die on me but thus far no Hitachi 2.5" drives.


I swear by Seagate & WD but I have lost one of each in the past. Maxtor I will not touch with a ten foot pole, working in the industry I saw them drop like flies in new pc's.

Hitachi Travelstar 2.5" drives are the dogs you know what. I'm not the only one that thinks so, two large data recovery companies also recommended me these drives and they were not trying to sell me anything.

---

### Post by pt123 on 2009-01-20
Wasn't seagate planning on releasing drives with a feature that is only functional with Windows & Macs?

---

### Post by handy on 2009-01-20
> **blastus said:**
> WD drives had problems with bearings as they aged (even those from just a few years old.) As the bearings wore they would emit a high-pitched whining noise. I read on silentpcreview.com that they have since fixed the issue. At one time silentpcreview.com removed WD from their recommended drives because of this. 

Every single WD drive I have ever owned ended up having this problem. It is practically unbearable. I still have a 120 GB WD drive from a few years ago that I can literally hear from 25 feet away. It's that loud and because it is so high-pitched it is headache inducing.

None of my WD's have that problem, except that my Raptors were the first version which were noisy from new, they apparently fixed that with the next series of Raptors they made.

---

### Post by zekopeko on 2009-01-20
i'm trying to see if one of my drives is affected with the firmware bug.
could somebody who has a ST3640323AS with firmware version SD13 confirm if it's affected?
the drive is on the list but since the main problem is the firmware not the hardware a don't know if my disk is affected.

we could also compile a list WITH the affected firmware versions for a more detailed list then those offered on the seagate website.

---

### Post by dmizer on 2009-01-21
> **zekopeko said:**
> i'm trying to see if one of my drives is affected with the firmware bug.
could somebody who has a ST3640323AS with firmware version SD13 confirm if it's affected?
the drive is on the list but since the main problem is the firmware not the hardware a don't know if my disk is affected.

we could also compile a list WITH the affected firmware versions for a more detailed list then those offered on the seagate website.

zekopeko, I merged your thread with this one as they seem to be discussing the same issue. Lots of information in the first post of this thread.

---

### Post by mips on 2009-01-22
[COLOR=Red]**Warning!!! Click on the link for your drive and read the instructions very carefully, if you don't you can brick your drive!!!**[/COLOR]

**Barracuda 7200.11**
      [ST31000340AS]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207951")  SD15, SD16, SD17, SD18, SD19 Affected.
      [ST3750330AS]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207951")    SD15, SD16, SD17, SD18, SD19 Affected.
[ST3750630AS]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207951")    SD15, SD16, SD17, SD18, SD19 Affected.
[ST3640330AS]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207951")    SD15, SD16, SD17, SD18, SD19 Affected.
[ST3640530AS]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207951") SD15, SD16, SD17, SD18, SD19 Affected. 
[ST3500320AS]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207951")    SD15, SD16, SD17, SD18, SD19 Affected.
[ST3500620AS]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207951")    SD15, SD16, SD17, SD18, SD19 Affected.
[ST3500820AS]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207951")    SD15, SD16, SD17, SD18, SD19 Affected.
[ST31500341AS]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207957")   All [COLOR=Red]NON[/COLOR] CC or LC versions. Do [COLOR=Red]NOT[/COLOR] flash CC or LC Drives!!!
[ST31000333AS]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207957")   All [COLOR=Red]NON[/COLOR] CC or LC versions. Do [COLOR=Red]NOT[/COLOR] flash CC or LC Drives!!!
[ST3640323AS]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207957")     All [COLOR=Red]NON[/COLOR] CC or LC versions. Do [COLOR=Red]NOT[/COLOR] flash CC or LC Drives!!!
[ST3640623AS]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207957")     All [COLOR=Red]NON[/COLOR] CC or LC versions. Do [COLOR=Red]NOT[/COLOR] flash CC or LC Drives!!!
[ST3320613AS]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207957")     All [COLOR=Red]NON[/COLOR] CC or LC versions. Do [COLOR=Red]NOT[/COLOR] flash CC or LC Drives!!!
[ST3320813AS]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207957")     All [COLOR=Red]NON[/COLOR] CC or LC versions. Do [COLOR=Red]NOT[/COLOR] flash CC or LC Drives!!!
[ST3160813AS]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207957")     All [COLOR=Red]NON[/COLOR] CC or LC versions. Do [COLOR=Red]NOT[/COLOR] flash CC or LC Drives!!!
         **Barracuda ES.2 SATA**
        [ST31000340NS]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207963")   All firmware versions [COLOR=Red]earlier[/COLOR] than SN06.
      [ST3750330NS]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207963")     All firmware versions [COLOR=Red]earlier[/COLOR] than SN06.
      [ST3500320NS]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207963")     All firmware versions [COLOR=Red]earlier[/COLOR] than SN06.
      [ST3250310NS]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207963")     All firmware versions [COLOR=Red]earlier[/COLOR] than SN06.
     **DiamondMax 22**
      [STM31000340AS]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207969")  MX15 (or higher) 
      [STM3750330AS]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207969")    MX15 (or higher) 
      [STM3500320AS]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207969")    MX15 (or higher) 
      [STM31000334AS]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207975")  All versions
      [STM3320614AS]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207975")    All versions
      [STM3160813AS    All versions  ]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207975")

---

### Post by mips on 2009-01-22
I have an affected 500GB drive, grrr. I'm not flashing it either as there are many reports of the firmware fix Seagate put out bricked peoples drives.

---

### Post by mips on 2009-01-22
> **zekopeko said:**
> i'm trying to see if one of my drives is affected with the firmware bug.
could somebody who has a ST3640323AS with firmware version SD13 confirm if it's affected?
the drive is on the list but since the main problem is the firmware not the hardware a don't know if my disk is affected.

we could also compile a list WITH the affected firmware versions for a more detailed list then those offered on the seagate website.

If your drive firmware version does not start with CC or LC like in your case then I would say you are affected.

The list provided by Seagate is complete, how much more detail do you want?

---

### Post by zekopeko on 2009-01-22
> **mips said:**
> If your drive firmware version does not start with CC or LC like in your case then I would say you are affected.

The list provided by Seagate is complete, how much more detail do you want?

it doesn't say if my firmware version was affected. the rep said that my drive isn't affected but looks like that might not be the case any more. i want a nice page saying: this disk model with this firmware is affected. use this update tool to flash your firmware.

it does not say that on the page with the info about my disk. the firmware version are still "In validation". so i tried turning to the community to see if anybody experienced problems with this model.

that's how much more detail i want.

---

### Post by mips on 2009-01-22
> **zekopeko said:**
> it doesn't say if my firmware version was affected. the rep said that my drive isn't affected but looks like that might not be the case any more. i want a nice page saying: this disk model with this firmware is affected. use this update tool to flash your firmware.

It does say it by exclusion.

> *** Note:** If your drive has **CC** or **LC**  firmware, your drive is not affected and no further action is required.  Attempting to flash the firmware of a drive with **CC** or** LC** firmware will result in rendering your drive inoperable. Does your drives firmware version# start with CC or LC? No, you are affected.


> **zekopeko said:**
> 
it does not say that on the page with the info about my disk. the firmware version are still "In validation". so i tried turning to the community to see if anybody experienced problems with this model.

that's how much more detail i want.

"In validation" means they are testing the new firmware before releasing it to the public.
"Recommended Firmware Update Status" means just that, the new version of firmware they recommend you use and does not list old affected versions.

> The firmware update for drives indicated as "In Validation" means the update is currently in testing and should be available soon.All the detail you want is there in plain sight.

---

### Post by mips on 2009-03-15
If your drive is already bricked then you could try this guide to get it alive again,
[http://www.msfn.org/board/index.php?showtopic=128807](http://www.msfn.org/board/index.php?showtopic=128807)





.

---

