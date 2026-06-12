---
title: "My first server"
date: 2011-05-22
forum: Server Platforms
---

### Post by heslop on 2011-05-22
Hello, I'm an Ubuntu and networking noob, so please bear with me.

I am trying to build a file server with RAID 5 over a couple of 1TB HDDs, to serve about 10 client machines using Ubuntu Server. 

I already own a 22-port switch: HP ProCurve v1810G-24 Switch (J9450A), which I am assuming will do the job. And for the actual server I am thinking of buying: HP ProLiant DL120 1U.

Will this hardware suffice, or am I missing something important to get the whole thing running? Any other comments or suggestions are welcome. :)

---

### Post by CharlesA on 2011-05-22
That would work fine.

---

### Post by heslop on 2011-05-22
> **CharlesA said:**
> That would work fine.

Cheers CharlesA ! 

Should I get something like "[Adaptec SCSI RAID Controller (PCI-X)2120s Raid 5 u320]("http://www.box.co.uk/Adaptec_SCSI_RAID_Controller_(PCI-X)2120_67126.html")" for raid5. Will that make a difference ? 

Many thanks.

---

### Post by CharlesA on 2011-05-22
It's up to you, really. I'm running a cheap RAID 5 card on my server and it runs at decent speeds. I've heard that software RAID is a tad slower, but it's a trade off for how much you want to pay.

---

### Post by heslop on 2011-05-22
> **CharlesA said:**
> It's up to you, really. I'm running a cheap RAID 5 card on my server and it runs at decent speeds. I've heard that software RAID is a tad slower, but it's a trade off for how much you want to pay.

Cheers. I've got a £1,000 budget and I think that server plus card plus extra 5TB HDDs seems to be the best solution that I can find for a file server.

---

### Post by CharlesA on 2011-05-22
Nice budget. When I built my file server, I ended up getting one of [these]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816115053&cm_re=rocketraid-_-16-115-053-_-Product") cards, and 3 of [these]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822145298&cm_re=hitachi_2tb-_-22-145-298-_-Product") drives.

Set me back a bit money-wise, but so far they have been rock solid.

EDIT: When I got the drives 2 years ago, they were around $200 each.

---

### Post by heslop on 2011-05-23
Another question for you :)  If I use a quad port ethernet card in the server can I get faster transfer of data from  the switch to the server ? I think the term is "link aggregation"  The switch is a HP V1810-24G Port Gigabit Switch. 

I'm not sure if I can though.

:)

---

### Post by spynappels on 2011-05-23
You'll have to check out Jumbo Frame support in that switch, I'm not sure off the top of my head whether it does.

Are you using 5 x 1TB disks? In what configuration? If the budget (and case) stretches, consider adding a hot spare disk so if there is a failure, the rebuild starts immediately on the spare disk. This might lower the risk of a second disk going belly up before the array is properly rebuilt. 5 x 1TB disks in RAID5 + Spare still gives 3TB storage, but I don't know how much you actually need.

---

### Post by CharlesA on 2011-05-23
> **spynappels said:**
> You'll have to check out Jumbo Frame support in that switch, I'm not sure off the top of my head whether it does.

Are you using 5 x 1TB disks? In what configuration? If the budget (and case) stretches, consider adding a hot spare disk so if there is a failure, the rebuild starts immediately on the spare disk. This might lower the risk of a second disk going belly up before the array is properly rebuilt. 5 x 1TB disks in RAID5 + Spare still gives 3TB storage, but I don't know how much you actually need.
+1.

I've got 2 spares that I can swap out anyway, so I don't see it as a huge deal (but it could be, I suppose).

---

### Post by spynappels on 2011-05-23
> **CharlesA said:**
> +1.

I've got 2 spares that I can swap out anyway, so I don't see it as a huge deal (but it could be, I suppose).

The way it was explained to me was that if a disk went down and it restarted rebuilding on a spare disk straight away, with RAID5 you were only vulnerable to data loss while the array was rebuilding, which could take quite a long time for a large drive. The failed disk could then be swapped out as soon as possible, but if there was a delay, the rebuilding would be ongoing or completed anyway.

Most of our systems sit unattended, scattered across the country, so for us it made sense to add a hot spare to all our arrays, so that if we could not get onsite immediately to swap out the faulty disk, we were still minimising the danger window where data loss was more likely.

I suppose it all depends on the ease of access and value of the data.

---

### Post by rubylaser on 2011-05-23
> **heslop said:**
> Another question for you :)  If I use a quad port ethernet card in the server can I get faster transfer of data from  the switch to the server ? I think the term is "link aggregation"  The switch is a HP V1810-24G Port Gigabit Switch. 

I'm not sure if I can though.

:)

You're looking to do LACP on your HP Switch (IEEE 802.3ad).  You're HP switch supports that protocol, so you could set that up with ifenslave (this is the package you'll need, and you'll need mode 4). Jumbo frames are also a good idea, as long as all of your devices support them.

In production at a minimum, you'd want RAID5 + a spare.  I personally use RAID10 at work, and at home use RAID6, because I don't need maximum write performance (I can still saturate a gigabit uplink with mdadm though).

---

### Post by CharlesA on 2011-05-23
> **spynappels said:**
> The way it was explained to me was that if a disk went down and it restarted rebuilding on a spare disk straight away, with RAID5 you were only vulnerable to data loss while the array was rebuilding, which could take quite a long time for a large drive. The failed disk could then be swapped out as soon as possible, but if there was a delay, the rebuilding would be ongoing or completed anyway.

Most of our systems sit unattended, scattered across the country, so for us it made sense to add a hot spare to all our arrays, so that if we could not get onsite immediately to swap out the faulty disk, we were still minimising the danger window where data loss was more likely.

I suppose it all depends on the ease of access and value of the data.

Yep, that's true. I only have mine set up that way since the server in question is at home and I've got daily backups that I can restore if a disk goes out and I lose the array when it's rebuilding.

In your case, it makes sense to have a hot spare. :)

---

