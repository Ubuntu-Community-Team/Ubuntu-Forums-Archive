---
title: "Ubuntu Server HP ProLiant DL380 G5"
date: 2010-04-13
forum: Server Platforms
---

### Post by alambre on 2010-04-13
Does anybody here tried installing Ubuntu Server 9.10 on HP Servers, need info about drivers and config. tanx

---

### Post by jaimerosario on 2010-04-18
I've installed on some servers and all works out-of-the box. I'm using 64-bit version without GUI (all is executed from the CLI).

---

### Post by spynappels on 2010-04-19
All flavours of Ubuntu Server regularly install without problems on both Proliant ML 110 and ML115 for me. I don't use RAID so I'm not sure how it copes with that.

The only thing I've noticed is that on the ML110 (Intel) the HDD partitioner seems to hang for a while during the install, but if it is left alone it eventually completes correctly.

---

### Post by iclebyte on 2010-04-20
I've just built 2 of these servers on ubuntu 9.10 and they work perfectly out the box.

---

### Post by alambre on 2010-04-30
if you were me, which should i choose? 9.10 or the 10.4 LTS which is currently released, tanx

---

### Post by alambre on 2010-04-30
anyways, thanx for all your reply

---

### Post by spynappels on 2010-04-30
Being a cautious sort of person who has been bitten by bugs after upgrading too early, I would suggest that the answer depends on whether you need rock solid stability or cutting edge features.

Cutting edge --> use the 10.04 LTS

Stability --> Use an older LTS release such as 8.04, or you can use standard 9.10 if long term support is not so crucial.

I tend to go with stability, so I'll not be using 10.04 LTS for another 6-8 months when the bugs have been workied out.

---

### Post by ghost_ryder35 on 2010-04-30
> **alambre said:**
> Does anybody here tried installing Ubuntu Server 9.10 on HP Servers, need info about drivers and config. tanx

Worked out of the box for me.
Also if you need the PSP or firmware updates etc here is a link to HP's driver download page.  [http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?prodNameId=3288134&lang=en&cc=us&prodTypeId=15351&prodSeriesId=1121516&taskId=135](http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?prodNameId=3288134&lang=en&cc=us&prodTypeId=15351&prodSeriesId=1121516&taskId=135)  They  offer downloads for 9.04 and 9.10 both x86 and x86_64

---

### Post by alambre on 2010-05-02
just finished installing 10.4, so far so good, will update for some problems later, btw, installed like a charm

---

### Post by slick666 on 2010-07-07
Does the idea of "installing" include getting some of HP's monitoring software working?

I've found that HP has Redhat and Suse packages but no .deb packages.

---

### Post by jmer1975 on 2012-03-02
just want to ask, do i have to use the two embedded network interface at the same time while installing the Ubuntu server 10.04? it cannot configure the network device if I'm only using one network cable.

---

### Post by seannon on 2012-03-04
No, you should be able to install with the one, it will likely be easier to use the 0 port, instead of the 1 port, (or if they are marked 1 and 2, use 1, not 2) there may also be a third port (with a wrench/spanner icon) that you will NOT want to use (unless it is also the 0 port of 0/1, or 1 of 1/2)as it is the management port..I have a DL380 G3, and 2 DL380 G4's and they both installed easily, the only trouble you may have is in setting up the hardware RAID arrays, the setup for those is easiest under windows apparently, so it may be a good idea to install windows, then do the major hardware configuring to get the RAID the way you want/need it, then blow the windows partition away and install Ubuntu... as a side note... through my trials and tribulations, of trying to get a nice VT enabled server, the G5 appears to be the first of this series that has the option in the BIOS to enable virtualization (VT support)... 

Good Luck!!!

Seannon

---

