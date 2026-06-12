---
title: "Looking for feedback: new NAS HDDs or Recertified?"
date: 2024-09-17
forum: Server Platforms
---

### Post by madscientist032 on 2024-09-17
Hello all - I am in the process of upgrading my local storage server and I need to purchase bigger NAS-grade HDDs. We're talking multiple 6-12 TB drives. (Specifically, 2x 6TB, 2x 10TB, and 2x 12 TB.)

I'm looking to see if anyone 's had good luck with recertified NAS drives ? or do y 'all buy brand new ? Ebay , Newegg ,& Amazon have the option to purchase a "renewed" or "re-certified" HDD and I'm on a tight budget & prices look pretty appealing, but I'm curious what the catch is (other than that it's basically a used drive vs factory new) so curious if anyone's gone down this path before, any lessons learned, recommendations, etc? Recognizing this is a "YMMV" situation, but still wanted to reach out and get some feedback.

My storage server currently has 1x 10tb Seagate Ironwolf Pro from 2020 & a buncha "barracuda greens" that were shucked from external drives literally last decade, so the goal here is to xsfer the data onto new (or more recent) hardware that has a good proven track record & reliability.

Thanks in advance!

---

### Post by TheFu on 2024-09-17
I stopped buying "NAS" drives when they dropped the warranty period to just 3 yrs.  I want 5+ yr warranties on my storage devices. Failed disks are such a hassle that the extra money for better warranty AND the longer lifespan for those storage devices (typically 10-13+ yrs) is worth it to me.  Drives with 5 yr warranties are the manufacturer's way of saying "we think this drive should last 10+ yrs".

So, no, I don't buy NAS drives - even new.

I have been buying "Gold" drives which are Data Center specific devices used/refurbished.  When they arrived, I immediately ran a LONG SMART test and looked for issues. Of the 4 drives in my last purchase, 2 had some questionable SMART data, so I asked for and received replacements. The replacements had fine SMART data.  NONE of those refurbished HDDs has failed. They came with a 5 yr warranty from the reseller from my purchase date.  They have 74000+ hours of power-on time now.  That's about 8.5 yrs.  Oh, and I paid $45/each for a 4TB size.  It was a deal then and that price would be a deal now.

I've also been buying new WD-Black HDDs recently for transactional storage.  They also have 5 yr warranties.  

I won't buy anything from Seagate ever again.  They've fooled me twice already with poor designs and the only way I can ensure they know of my dissatisfaction is never to give them any money again.  The Ironwolf drives may be fantastic.  I'll never know and will never care.  They screwed me too many times already, so I don't trust them (the comany management).  I suppose we all have companies that we feel didn't address our problems sufficiently.  I know a few other things about the company because they were a client of a company I worked for in the late 1990s. I saw where they didn't do some things that they should have like our world-class clients all did.  Anyway, management is all different, so perhaps all is fine there now.

BTW, my largest HDDs are 8TB and I split them into 4TB data stores because 4TB was the size I standardize on for all my data and backups long ago.  I don't regret this choice.  It means I'll only buy 4, 8, 12, 16, 20TB HDDs.  That's more about maintenance stuff than anything else.

---

### Post by madscientist032 on 2024-09-18
I completely agree on the warranty call-out. I've used the same logic when purchasing a new PSUs, so it makes perfect sense to do the same for new/replacement disk drives. 

When I got my IronWolf from Microcenter in 2020 it had a 5 year warranty and it's been rock-solid ever since, no issues at all. SMART test has been clean since day one and I'm very happy with it. 

I'll take a look later today and see if I can find any WD Gold drives that meet my criteria. Would you have any recommendations on etailers or do you just buy straight from Amazon/Ebay/Newegg/WD ?

One thing I'm concerned about is noise level. Tthe system they'd be going into is a Fractal Design Define R5 located in my living room. Not only do I lack the space to rack-mount (or a basement/closest) for the server, I'm also I'm picky on how much noise the server generates. The case does a good job blocking out the majority of the drive noise, so I assume it would be OK with WD Golds but I'm not 100% sure & I won't know until I get my hands on a pair. Any thoughts there?

---

### Post by TheFu on 2024-09-18
Gold's and those types of DC drives can be loud.  While I said "Gold", I'm actually using some Hitachi DC drives.  Those may or may not be re-branded as WD-Gold since WD bought the Hitachi HDD manufacturing. The Hitachi models involved had a longer designed MTBF rate and the WD equivalents.  Noise isn't the primary design consideration for DC storage.  I have them spinning in small 4-drive enclosures with quiet Noctua fans pulling air for cooling over the HDDs.  The drives don't seem loud when I'm working during the day.  They are about 1m from my head now.  I hear the PSU fan more. Noctua makes nice, quiet, fans, in my experience. Great for keeping HDDs cool.
Can you guess which are cooled by a big, quiet, Noctua fan?
```
$ sudo hddtemp /dev/sd[a-h]
/dev/sda: HGST HUS726T4TALA6L4: 39°C
/dev/sdb: HGST HMS5C4040ALE640: 38°C
/dev/sdc: WDC WD40EFRX-68WT0N0:  drive supported, but it doesn't have a temperature sensor.
/dev/sdd: ST3320620AS:  drive supported, but it doesn't have a temperature sensor.
/dev/sde: HGST HMS5C4040ALE640: 39°C
/dev/sdh: WDC WD8002FZWX-00BKUA0: [COLOR="#FF0000"]42°C[/COLOR]
```
Only 4 slots for that fan in the system.  42°C  isn't exactly HOT. I don't worry until over 50°C.  A few drives are eSATA connected too. I removed the crappy USB 8TB drives that I use for backups. At the time, they were a good buy and I didn't have room internally or in an array.  As I swap out smaller HDDs for 4x larger ones, slots are becoming freed.  That seagate is from BEFORE the corporate issues.  I have 7 others here of that same model and only 1 has failed. The others are around to be used for scratch HDDs.

Here's another system:
```
$ sudo hddtemp /dev/sd[a-h]
/dev/sda: WDC WD8002FZWX-00BKUA0: 37°C
/dev/sdb: WDC WD20EFRX-68AX9N0: 34°C
/dev/sdc: WDC WD8002FZWX-00BKUA0: 37°C
/dev/sdd: WDC WD20EFRX-68AX9N0: 35°C
```
Nice, cool, drives.  The EFRs are WD-Reds and pretty old now.

Most of the use/noise happens overnight for backups (rdiff-backup) and delayed mirrors (rsync).

I'm an opportunity buyer.  I watch a few "deal" websites for sales, then buy a few HDDs at a time, assuming they aren't Seagate and are from a reputable seller/middleman.  I seldom remember the actual name of the seller, but they aren't "Joe Guy" - it is a real company that has something about HDDs in their name. I've seen them before, but can't think of it today. Sorry.

I don't have a computer with storage in my living room, just a fanless Raspberry pi that hooks into a Jellyfin server on the other side of the house. Last thing I want is noise to take away from any movie experience. Since we only watch projectors or tablets now (no TVs), as long as the Pi is quieter than the projector fan, we're good.  I've had some jet-engine loud cheap projectors, but we're rocking some Epsons now. Nice a quiet compared to all the others.

Also, beware that HGST drives have hugely varying quality across their lines. Some models are much worse with failures than even the terrible Seagate's that I think the FTC should have mandated for recall.  We are unlikely to have sufficient numbers of HDDs for statistical use. Lots of companies don't, but [https://www.backblaze.com/cloud-storage/resources/hard-drive-test-data](https://www.backblaze.com/cloud-storage/resources/hard-drive-test-data) does and publishes it - even if it is flawed - it is better than nothing.  Just remember that in their business model, drive slots and having the highest density of storage is very important, not total lifespan.   [https://www.backblaze.com/blog/backblaze-drive-stats-for-q2-2024/](https://www.backblaze.com/blog/backblaze-drive-stats-for-q2-2024/) is the most recent data they've interpreted.   Seagate has some models with the best and worst failure rates this quarter.

---

### Post by madscientist032 on 2024-09-20
Thanks for the clarification about WD Gold + Hitachi. Back when I used to work as a contractor for IBM between '09-'13, Hitachi was one of the OEM providers for their Thinkpad HDDs. I rarely remember any issue with those drives, whereas the Toshibas (the other OEM for IBM at that time) were more likely to have issues IIRC. I know Seagates would have issues too, but that was limited to the 7mm models vs the thicker 9mms. Not to mention it wasn't super common for a Seagate HDD to be in a system I'd be servicing. I think it was probably 15% of the time I'd get a laptop w/ a seagate inside...

Anyways - I'm getting off topic! All my drives in my server are cooled by 2x 140mm Noctua fans. Noctua's been a staple in all my builds since 2012. They do an amazing job at maintaining a good temperature (29-33c) with basically zero noise. Also, the Define R5 has built-in sound-deadening material which provides a second layer of defense, to help keep things quiet. I don't hear the server over my TV & stereo while I'm watching my media :) 

I know the drives can tolerate much higher temps but I'm always trying to keep my hardware running cool and as quiet as possible, for both longevity and piece of mind. For example - the 2tb scratch pool I have now is comprised of from 2x 1TB drives that I have had for at least a decade (they came from my previous gaming rigs). I don't like any of my equipment running hot if I can help it. 

BTW I tried to run hddtemp but it seems that was pulled out of 22.04 server. It's not a huge issue as I can pull temperature data from smartctl, but kind of a bummer because it looks like hddtemp can pull ALL drives in one command whereas smartctl you need to provide the drive individually (it doesn't allow 'smartctl -a /dev/sd[a-g]' for example). I did a quick search online and it does seem possible to get hddtemp working in 22.04 but for me the juice isn't worth the squeeze, so to speak.  

I don't know if this post will get more response from other users, but at the same time I'm simply happy that I'm not crazy for thinking it's worth picking up a couple refurbished/recertified data center drives. 

It's good to hear first-hand that there are people that have good luck with refurbished drives. I'll keep an eye out for any deals and probably snag a couple refurbs just to see how they perform & sound, but based off your experience it's probably a good decision as long as the seller is reputable and the warranty's not stupid short! Thanks again for the feedback & sharing your experience.

---

### Post by TheFu on 2024-09-20
Well, I did buy 4 and returned 2 for replacement because the SMART data wasn't good after a long test, so be prepared to return any that don't look good at the start. 

And just for the lurkers, I didn't replace the Noctua fans until they were making noise.  That was about 3 yrs for one system.  The other system, I'd bought a drive cage that I decided not to use. That drive cage didn't come with any fan, so I'd bought another Noctua for it ... then was able to find a hot-swap drive cage just like the one in my other systems which has been working well (uses 3x5.25 slots, but will hold 4x3.5in HDDs).  Having front-panel hot-swap is a great convenience, even if you don't really use it.  Knowing that you CAN (obviously, umount the file systems on the disk to be pulled first!).

I'll go away now. Hopefully others will share their info too.

---

### Post by madscientist032 on 2024-09-25
I am returning to this thread to provide an update as I have some developments I want to share with the community. 

**I've found a number of e-tailers that sell Refurbished hard drives - both consumer-grade & enterprise-grade - and I've already purchased a number of drives for a fraction of what I'd be paying brand-new. **

In my original post, I was looking for drives ranging in capacity from 6TB to 12TB. Since then, I've gone & performed some *significant* cleanup. I no longer require 12TB disks... now I need a 6TB platter, which is far more preferable!  :) 

Additionally, I forgot to mention I have a "scratch" disk powered by an aging 10 year old Seagate Barracuda.  

So... I went around the net and looked for reputable companies/retailers/eTailers based off the feedback I recieved here + my own experience as a former IBM contractor servicing ThinkPad systems (where it was common practice to re-use drives  after putting them through a Drive Fitness Test & ensuring a clean bill of health.)

Addressing the scratch disk pool first made the most sense, as it has the lowest amount of risk + cost overall for my system, and it would serve as a starting point of confidence-building for each etailer. 

**For my scratch drive pool,** I went with 2x Toshiba 2TB 7200 RPM Consumer-grade HDDs from [serverpartdeals.com]("https://serverpartdeals.com/") (they have an Ebay storefront, which is where I ordered mine) Within 2 days of purchase, I had the drives delivered and they were packaged as if they came from the OEM! Meaning, they were properly shipped in a box with anti-static wrapping + HDD drive air pocket padding. Very nice overall and I was quite pleased. 

How consumer-grade are we talking? ([Toshiba's data sheet has them literally branded as "Generic Storage Device" ]("https://toshiba.semicon-storage.com/content/dam/toshiba-ss-v3/master/en/storage/product/internal-specialty/cHDD_MD04ACAxxx_product-overview.pdf")). They are model number [FONT=courier new]MD04ACA200NR[/FONT], for anyone interested. 

That said, initial SMART & badblocks testing shows no issues, no bad sectors, and I'm quite pleased with performance. Moving from a single disk to a RAID0 setup is amazing on its own. Knowing I have a healthy drive that's not at death's door is another positive (The 10-year-old Seagate Barracuda is on its last legs.)

So that closes out the Scratch Drive effort. Pretty painless and I'm happy overall. 

**Next up - the archive pool: **The other drives I purchased - which have not yet arrived - came from [GoHardDrive.com]("https://www.goharddrive.com/"). Just like ServerPartDeals, they too have an eBay storefront. 

I purchased 2x 8TB WD HGST DC drives with the intent purposes of setting up a 6TB RAID1 array.  The specific model number is [HGST Ultrastar HUH728080ALE604]("https://documents.westerndigital.com/content/dam/doc-library/en_us/assets/public/western-digital/product/data-center-drives/ultrastar-sas-series/data-sheet-ultrastar-he8.pdf") 

 The eBay store front gave them a 5-year warranty and were much cheaper than a similar model from ServerPartDeals. 

Provided all is well & that they survive SMART and badblocks testing, they will be  replacing the 1x 10TB Seagate Ironwolf Pro NAS drive I currently have that's  backing up my entire home, which has been in service since March 2020. I'll likely end up using THAT drive to back up the ENTIRE NAS. So that's exciting!

BTW for those curious, I went with 2x 8TB over 2x 6TB because it was cheaper and easier to find and purchase 8TB drives over 6TB... and I can very easily partition out 6TB to start & then add space later if the need arises. 

Once I those drives arrive & and tested & vetted, I'll likely update this post accordingly. 

For now, I simply wanted to provide an update in meantime. Thanks for reading!

---

### Post by sgt-mike on 2024-09-29
> **madscientist032 said:**
> ......**Next up - the archive pool: **The other drives I purchased - which have not yet arrived - came from [GoHardDrive.com]("https://www.goharddrive.com/"). Just like ServerPartDeals, they too have an eBay storefront..................

Just went to their website one drive that peaked my interest was the MDD 4TB SAS. Never had any dealing with that product. Now you got me interested.
Dang you LMAO....  Nice post thanks for the update.

---

