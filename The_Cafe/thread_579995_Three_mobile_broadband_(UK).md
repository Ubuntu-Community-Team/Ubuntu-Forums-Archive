---
title: "Three mobile broadband (UK)"
date: 2007-10-18
forum: The Cafe
---

### Post by smotsie on 2007-10-18
Hi, Happy Ubuntu newbie here wondering if anyone has any knowledge of the "Three"(Oooh I hate that name - Googling it gets WAY too many false hits!) UK mobile operator's broadband package working with Ubuntu? It's from as little as £10 a month but it requires the use of a "Three" USB "modem". I haav no info on who really makes it, and they won't lend me one to try (I did ask!)

So, if anyone has any info on this it would be great - alternatively iIf anyone wants to risk £50 + £10 a month for 24 months, their site is at [http://threestore.three.co.uk/mixnmatchphone.aspx?phonecode=3GUSBMODDS](http://threestore.three.co.uk/mixnmatchphone.aspx?phonecode=3GUSBMODDS) 
but please let me know how you get on! ;)

Cheers

Smotsie

---

### Post by mog538 on 2007-10-19
Smotsie,

Apparently the modems for Three, Vodafone and T-Mobile's mobile broadband services are all the same, just stamped with the respective company's logo. (Don't know if the express card's are the same though).

I have not signed up yet as waiting to see if O2 are going to rethink the price for their imminent service as I have had shocking experiences on Three in the past but as I still have a windows partition on my laptop that deal may be too good to pass up (even if their use of the word "unlimited" riles me somewhat!

If/when I do sign up I would be interested to hear others experiences of trying to get this working with Linux as I am no expert but will certainly give it a go.

---

### Post by CbrPad on 2007-10-19
I've been using the Irish version for the past few months.  Its ok but nowhere near as good as dsl.

The modem here is a Huawei E220 which I believe is also used by Vodafone and .. er, someone else.

I installed it using the following guide, its a piece of cake...

[http://www.linux.ie/articles/tutorials/threeirelandUSBmodem.php](http://www.linux.ie/articles/tutorials/threeirelandUSBmodem.php)

I also found there is Vodafone linux s/w under development.  I just ran it  under Ubuntu to see if it would crash, which it didn't, but I never tried actually tried configuring it for 3, I simply use the pon/poff script from above.

Also, take note that 3 have been taking a fierce slating in Ireland.  Check out the massive thread of problems here...

[http://www.boards.ie/vbulletin/showthread.php?t=2055115306](http://www.boards.ie/vbulletin/showthread.php?t=2055115306)

Ooops, just reread and remembered that you've had bad experiences with them already.   Go Vodafone methinks ;-)

Best of luck.

---

### Post by smotsie on 2007-10-21
Thanks for those replies, guys - I hadn't thought about Three's very poor reputation. We have a Vodafone modem and account at work which I should be able to borrow for a night to test. If as you say the modems are the same then it will prove a useful test. I think I shall wait for 02 to set their price as I have used them for mobile services for several years with no problems.

I also think I will attempt to dig deeper with the tech guys at whichever provider I go with to determine for sure what model the USB modem is. Meanwhile if anyone has experience of using Three's or any other Mobile BB service it would be great to hear - I for one am convinced that it is going to make as big a difference to the way we all use the Internet as ADSL and wifi have.

Cheers
Smotsie

---

### Post by Swab on 2007-10-23
I contacted three regarding their service and the modem they supply, this is what they said...

> The model number of our USB modem is E220.  I understand you wish to use this modem with Linux however I’m afraid that our modem doesn’t support Linux.  It only supports Windows 2000, Windows XP (Home and Professional), Windows Vista or OSX.  This is the only modem we have as of now, so you'll not be able to use an alternative modem.  We might support Linux in future however, can’t commit anything as of now.  We'll take this as a feedback and try working on this option.

I am presuming this means the modem is a Huawei E220.  There is a thread in these forums relating to this modem: [http://ubuntuforums.org/showthread.php?t=262867](http://ubuntuforums.org/showthread.php?t=262867)

Seems like it is possible :)

---

### Post by CbrPad on 2007-10-23
Yup, the 220 is what I have from them.   I replaced my EsatBT dsl connection with it, simply coz I didn't want to be paying line rental when I never use a landline to make calls.

My experience with it has been mixed.  I had it up and running within five minutes using that link I posted so getting it running under Ubuntu is easy.  However, the service is another matter entirely.

3 claim a max speed of 3.6mbps (about 450KB a second I think) which is complete rubbish.  The most I've ever gotten is 150KB, and it averages something like 50.  
It appears to suffer massively from contention with mobile users, not to mention 3 not having a clue how to run a network, eg, there seems to be only one ip address for the entire network (see the boards.ie thread I also linked to).    Access also seems to really slow down after 7pm and at the weekends, ftp is very iffy, latency is huge so online gaming is a no-no, etc etc.

However, if like me you only want it to surf, check emails, and download the occasional torrent then it's fine.  For 20 euros a month it's cheaper than I was paying just for line rental, let alone BB access.  Plus it's got the nifty advantage that it's mobile, which is fantastic.

But beware that the service you get seems to be very much dependent on your location, some people are getting performance worse than dialup !!   Take the 2 week trial to see how you get on.

{Edit}  Sorry I think I originally forgot the link for the Vodafone s/w, so here it is, I see there's a Gutsy deb available already, sweet...

[https://forge.vodafonebetavine.net/frs/?group_id=12](https://forge.vodafonebetavine.net/frs/?group_id=12)

---

### Post by Swab on 2007-10-25
OK, so I ordered the 1GB allowance / £10 per month option.  Will not be used as my primary connection just for when out and about :)  Will let you all know WHEN I get it working!

---

### Post by Swab on 2007-10-26
Got my modem today, basically works out of the box in Gutsy!

Hardware is recognised, just have to use wvdial to configure the connection much like any other modem.  Presumably gnome-ppp or kppp would work also.

Speed seems pretty good, although latency is an issue.  Seems like the modem goes idle after a few seconds of inactivity and then takes another few seconds to come back when you load a page.

All in all I am pretty pleased, no more £5 an hour coffee shop internet fees for me!

---

### Post by speedwell68 on 2007-10-26
Just pray you never have to phone a Three Technical Support call centre.:KS

---

### Post by fabianfox on 2007-11-05
I live in Derry City, Northern Ireland - supposed Three Hot Area! I got the Three Mobile Broadband about 3 weeks ago. I am using Mac os x. Firstly, quite difficult to install for basic users - few detours to network preferences before it will work.

As for speed, its seriously bad. Download speeds range from 4k per sec to a max of 90k on the very odd occasion. It averages about 30k. As for browsing (and I have tried on Firefox, Safari and Netscape) times can vary but it could take up to 30 seconds to open up google and as for You Tube, just don't bother for it stops and starts movies way too often.

I also have had problems connecting occasionally. I have had to take out the sim and place in a phone to re-igniteit,i and then replace in modem just to get it started again.

Contacting customer support is another waste of time. Foreign staff who just don't understand what your saying, although they are very friendly and polite.

In conclusion, if I had the chance to do it all again I just wouldn't bother. Give it a bit of time to another service provider has a better mobile broadband option.

---

### Post by paul cooke on 2009-05-04
> **Swab said:**
> Got my modem today, basically works out of the box in Gutsy!

Hardware is recognised, just have to use wvdial to configure the connection much like any other modem.  Presumably gnome-ppp or kppp would work also.

Speed seems pretty good, although latency is an issue.  Seems like the modem goes idle after a few seconds of inactivity and then takes another few seconds to come back when you load a page.

All in all I am pretty pleased, no more £5 an hour coffee shop internet fees for me!

ah, good news for me... this dial up USB modem thing is the sticking point for my daughter dumping Vista...

we lost our collective rag at Vista the other day as there was a document stuck in the print queue and nothing we did would get it out of it... and it wouldn't let us even delete the printer so we could re-install it. Currently. we're printing using a Linux live disc.

---

### Post by mips on 2009-05-04
> **Swab said:**
> I contacted three regarding their service and the modem they supply, this is what they said...


They really don't have a clue or they mean they don't offer support for linux related problems.

---

### Post by Sublime Porte on 2009-05-04
With intrepid and now jaunty, all you do is plug your modem in, and it'll ask you your provider, then you're away. No configuration, no fiddling, no nothing, it's really so simple.

I've tested installing 3's software on both Windows and Mac OSX, and the latter is a complete nightmare. So much fiddling and mucking around. Ubuntu is really a breeze when it comes to using wireless broadband.

---

### Post by Plumtreed on 2009-05-04
I used 3 USB modem from Oct '08 to Mar '09 during a recent visit to the UK. It will work on current versions of Ubuntu but with 8.04LTS you may need to upgrade to NetworkManager .7?? (current version of NetworkManager)

You will have to configure it by entering the phone# *99#, Password and name can be left blank and the APN is '3internet'

When I was there it wouldn't work well except in large urban areas and could get easily overworked during peak hours. It was the only network providing 'pay-as-you-go' but I think BT's idea is better in that users can also get included access to their WIFI sights, such as hotels, pubs etc. These, in my short experience, were more reliable and effective.

Basically, connecting in Ubuntu or Puppy linux is easy! Once installed it will connect automatically.

---

### Post by Johnsie on 2009-05-04
With Ubuntu it depends which dongle you use. To be honest it's alot easier to install on Windows because ALL the dongles come with Windows drivers/software.

---

