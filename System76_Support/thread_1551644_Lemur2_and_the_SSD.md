---
title: "Lemur2 and the SSD"
date: 2010-08-12
forum: System76 Support
---

### Post by stillnotcool on 2010-08-12
First, I'd like to express my excitement at the wonderful new Lemur model from System76.  I've been looking for a notebook of this type for quite some time [[for instance]("http://ubuntuforums.org/showthread.php?t=1475760&highlight=semioticrobotic")], and am seriously considering purchasing one in the near future.

I do have one question/concern, and I'm hoping a System 76 representative can clear it up for me.  It concerns the SSD options available on the new Lemur.

I'd certainly like to order a Lemur with an Intel 40GB SSD, but I have reservations about this hard disk option.  And I doubt I'm alone.  Quite frankly, the Internet is full of anecdotal, incomplete, and contradictory information regarding the lifespan of SSD drives, particularly under Linux.  You've read it all, I'm sure: SSDs wear more quickly than "traditional" HDDs; newer SSDs automatically enact wear leveling to extend their lives; SSDs run best with TRIM support, which isn't available in Lucid's version of the Linux kernel; SSDs require maintenance programs that only run under Windows; new Intel SSDs can expect to last only five years; 40GB Intel SSDs don't last as long as 80GB SSDs might; SSDs must be properly (and manually) aligned under Linux; SSDs will perform better under Maverick.  The list goes on.

I planned to call System76 directly so I could speak with a sales representative about the company's SSD testing procedures, but I thought starting a thread might be a better option -- if only because others can also hear from System76 on these issues (or perhaps experienced users can offer additional information?).

What kind of testing has System76 done on Lemurs with SSD options?  What kind of research has System76 performed in order to support SSD drives under Ubuntu?  Are these storage options "safe" on machines running Ubuntu?  Does System76's custom driver ameliorate common problems with SSDs on Linux -- or are these problems nonexistent?

Thanks to anyone who can help an excited but cautious user.

---

### Post by tomart on 2010-08-12
I would also be curious to know the exact battery life in the SSD vs HD versions.

---

### Post by msrinath80 on 2010-08-12
> **tomart said:**
> I would also be curious to know the exact battery life in the SSD vs HD versions.

Me too. Can anyone with an SSD in their lemur comment on this? I have a 640GB HDD in my Lemur. I can easily get around 2 hours and 45 mins worth of battery for moderate usage. Also, I'd appreciate if someone can comment on how hot the SSD gets? Thanks!

---

### Post by murchball on 2010-08-13
In a previous thread, System76 said the difference was about 15 minutes on the original Lemur

---

### Post by thomasaaron on 2010-08-13
> What kind of testing has System76 done on Lemurs with SSD options? What kind of research has System76 performed in order to support SSD drives under Ubuntu?

I really don't have all the technical details of how they test this in R&D, but we've never had a problem with SSDs in any of our machines.

> Are these storage options "safe" on machines running Ubuntu?

Same answer as above.

> Does System76's custom driver ameliorate common problems with SSDs on Linux -- or are these problems nonexistent?

The System76 Driver does nothing pertaining to SSD's.

> I would also be curious to know the exact battery life in the SSD vs HD versions.

We do not do a direct comparison. We only give an average battery life, which, on the Lemur, is about 3 hours. The 15-minute difference was only a guesstimate based on the fact that the SSD has no moving parts.

---

### Post by stillnotcool on 2010-08-13
Thanks for your reply, TA.  Anyone else have reports, reviews, or advice on ordering a machine with an SSD option?  Will Ubuntu's default ext4 filesystem be the best option for formatting such a drive?

---

### Post by tonyyarusso on 2010-08-20
You'll be perfectly safe.  The show-stopper types of issues reported with SSDs applied to early ones on the market, and have since been fixed by any manufacturer worth their salt.  There may be tweaks you can do to get more speed/life/whatever out of it, but they aren't a requirement and quite likely wouldn't be worth your time anyway.  System76's SSD choice are Intel models, which are among the top tier of the market for quality.

As far as getting better performance with Maverick, it is entirely possible that will be true, especially since Maverick will likely support btrfs in the installer.  ext4 is a perfectly reasonable choice for now though.

---

### Post by PabloH on 2010-08-22
Don't worry about quality SSD's. The bad ones were cheapy units. The bad stories concern these units primarily. 

The Intel's are quality units based on their SSD's used in servers with very high uptime requirements. The technology is hardly new, even then. Hard cards have been around since the 90's. Similar flash buffering write devices have been used by IBM mainframe's.

The SSD's will last longer in most usage scenarios, as the Intel units have a higher MTBF than a traditional hard drive. The 160GB one that I have was tested for 20 GB writes per day and is expected to last 5 years at that rate before the flash fails. If you are putting the drive in a shock prone environment (laptop)-- the SSD's will certainly last longer than the spinning platters would.

The details can be found here:

[http://download.intel.com/design/flash/nand/mainstream/mainstream-sata-ssd-datasheet.pdf](http://download.intel.com/design/flash/nand/mainstream/mainstream-sata-ssd-datasheet.pdf)

---

### Post by stillnotcool on 2010-08-22
> **PabloH said:**
> Don't worry about quality SSD's. The bad ones were cheapy units. The bad stories concern these units primarily. 

Thanks, PabloH, for assuaging my fears.  I hope to order my Lemur in the next few weeks.

---

### Post by msrinath80 on 2010-08-25
Just an FYI. Back in June 2008, Tom's hardware showed that SSDs don't do much in terms of prolonging battery life[1]. I'm curious if anyone with an SSD on their lemur can post their battery runtime when idle. If you could do that, I can post my idle battery runtime for a traditional WD 5400RPM drive and then we could compare the results.

References:
[1] [http://www.tomshardware.com/reviews/ssd-hdd-battery,1955-15.html](http://www.tomshardware.com/reviews/ssd-hdd-battery,1955-15.html)

---

