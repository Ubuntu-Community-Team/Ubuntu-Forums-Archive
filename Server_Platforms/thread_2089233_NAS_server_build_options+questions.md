---
title: "NAS server build options+questions"
date: 2012-11-28
forum: Server Platforms
---

### Post by jgalloway on 2012-11-28
Hi all, sorry if there is a more appropriate form for these questions
Bolded are the short form questions, rest is just info on why/how is being done

What our situation is:

I work in a semi-poor school district. Recently there have been a lot of vandalism and theft of the school property.

Actually this was not sporadic, this was every weekend and the odd weekday this was happening. I think the police called it a hate-crime. Anyway totaled sum of damages and loss is significant, enough so that now the board and superintendent is  aiming for a POE security system. They are looking at getting around 15-20 cams. They are hoping for more but the price could inhibit the number of cams.

We are only in the preliminary stages of this project but higher wants this going ASAP.  A rough guess of 1TB per cam for a month of storage was what the sales rep said to expect around. He hasn't given us any tech specs on what exactly we need. So we are looking at 20TB of usable storage.

I know for a fact I can get 16TB of raw data and do this for under $1500, and the reason I know is because I already built a working NAS using Ubuntu servers software RAID connecting via eSATA to 2 RAID enclosures. So practically a 1+0RAID array.

So here is our task:
I am thinking I can setup 16TB of raw data, but if a HD fails, then its all over. I want to RAID it, preferably using mirror. Security cams are too delicate of a topic... I don't think I would live very long if a HD fails and we loose video files. 

So I am looking for 40TB of raw data.

*When I say a RAID enclosure I mean this one (or similar)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16816111149](http://www.newegg.com/Product/Product.aspx?Item=N82E16816111149)

*when doing initial calcs, there are 2 or 3 TB hds available. 
[http://www.cdwg.com/shop/products/Seagate-Barracuda-hard-drive-3-TB-SATA-600/2522015.aspx](http://www.cdwg.com/shop/products/Seagate-Barracuda-hard-drive-3-TB-SATA-600/2522015.aspx)



Option 1:
I found Dell PowerEdge T320 Chassis up to 16 HDS... better PowerEdge T620 with Chassis with up to 32 HDs. We can load it up with HDs, but the requirement is that the server needs PERC H310/PERC H710/PERC H710P. **I need to know if in fact the PERC H310/PERC H710/PERC H710P would work with Ubuntu Server, and if Ubuntu server will work on the PowerEdge platform at all.** My guess it will, but I would be in deep :-\" if we bought this and turns out doesn't work...
(and on a side note I need to find if I can install my own HDs because the HDs offered are insanely expensive compared to buying from a store)
(another side note, I have to find how they hook them all up, looks like the PERC cards have a max of 8 ports, unless port multipliers are included)
~5,180

I found this site showing the 'certified Dell hardware' the T620 is not on it. However the Optiplex 745 is not either and I am not having any issues with it yet. 
[http://www.ubuntu.com/certification/server/make/Dell/?csrfmiddlewaretoken=ab68e3e204626be915605a4baa35a190&query=&release=Any&level=Certified](http://www.ubuntu.com/certification/server/make/Dell/?csrfmiddlewaretoken=ab68e3e204626be915605a4baa35a190&query=&release=Any&level=Certified)

Option 2:
Use a single computer (that we already own) and connect 4 RAID enclosures to it, with 3TB hds to get a total of 48TB of raw data, with the OS on the RAIDed HDs
~$2,750 (for hds, enclosures and already available computers)


Option 3:
(this option was born from the thought we were limited to 2TB HDs only, so we would have fell short of our required data. This option is well, unnecessary because of option 2 can fit all HDs on a single computer. But I would like to know if its possible anyway )
So using 2 desktops, I can have 1 desktop with 3 RAID enclosures and desktop 2 with 2 enclosures. Now the question is **can I link the two Ubuntu servers to perform as one virtual NAS server (maybe using the MaaS?) **
~$2,750


I have experience with Ubuntu server RAID, LAMP, FTP, SSH, file server.. but have not dived into the whole virtual machine world extensively yet

I am inclined to go with Option 2, because its using the groundwork that already I already know works, but option 1 is enticing since it would add layers of redundancy (with redundant power supply) not to mention using a new tower computer with a Xeon CPU that is designed for server applications. 

Anyway thanks for the input 
[IMG]http://www.planetsmilies.com/smilies/sign/sign0201.gif[/IMG]

---

### Post by darkod on 2012-11-28
I don't have too much experience with similar setups, and probably others will have better ideas, but... I would seriously look into FreeNAS.

It might take some learning, but it sounds to me like ideal for the job. I am myself investigating it in VBox before I suggest it for a production machine.

The OS itself can run on as little as 2GB, including from usb stick or Compact Flash card, so any similar device of 4GB/8GB would do. The reason to use small devices is that the disk that holds the OS can not be used for data, so if you use a large disk it's wasted.

FreeNAS uses ZFS, that most people praise for data storage and redundancy. It supports CIFS shares (like samba shares, which is probably how you planned to use an ubuntu NAS) and NFS, among others. I assume there will be another machine running some kind of CCTV software and you will need this server only for storage.

There are three basic levels of raid, that FreeNAS calls RAIDZ (one disk redundancy), RAIDZ2 (two disk redundancy) and RAIDZ3 (three disk redundancy).

So, here is an example:
Get the case with 16 hdd bays. Use 15 bays with 2TB disks for one single large RAIDZ3 device. The 16th bay can be with the OS disk (any smaller disk will do), or simply use usb stick or flash card as mentioned.

RAIDZ3 means three disks can fail and the device is still available and data safe. Of course, you should really change a faulty disk as soon as you notice it, so you will rarely even arrive to a situation where three disks are bad. The three disk redundancy (parity) means you lose three disks as usable space, but that still leaves 12 disks x 2TB = 24TB usable data storage. That falls great into your needs, right?

That's what I would do, probably. The freenas website is:
[http://www.freenas.org/](http://www.freenas.org/)

Also you can find many online articles about the benefits of ZFS, or downsides if you manage to find any serious ones.

---

### Post by sandyd on 2012-11-28
> **darkod said:**
> i don't have too much experience with similar setups, and probably others will have better ideas, but... I would seriously look into freenas.

It might take some learning, but it sounds to me like ideal for the job. I am myself investigating it in vbox before i suggest it for a production machine.

The os itself can run on as little as 2gb, including from usb stick or compact flash card, so any similar device of 4gb/8gb would do. The reason to use small devices is that the disk that holds the os can not be used for data, so if you use a large disk it's wasted.

Freenas uses zfs, that most people praise for data storage and redundancy. It supports cifs shares (like samba shares, which is probably how you planned to use an ubuntu nas) and nfs, among others. I assume there will be another machine running some kind of cctv software and you will need this server only for storage.

There are three basic levels of raid, that freenas calls raidz (one disk redundancy), raidz2 (two disk redundancy) and raidz3 (three disk redundancy).

So, here is an example:
Get the case with 16 hdd bays. Use 15 bays with 2tb disks for one single large raidz3 device. The 16th bay can be with the os disk (any smaller disk will do), or simply use usb stick or flash card as mentioned.

Raidz3 means three disks can fail and the device is still available and data safe. Of course, you should really change a faulty disk as soon as you notice it, so you will rarely even arrive to a situation where three disks are bad. The three disk redundancy (parity) means you lose three disks as usable space, but that still leaves 12 disks x 2tb = 24tb usable data storage. That falls great into your needs, right?

That's what i would do, probably. The freenas website is:
[http://www.freenas.org/](http://www.freenas.org/)

also you can find many online articles about the benefits of zfs, or downsides if you manage to find any serious ones.

+1

---

### Post by dannyboy79 on 2012-11-28
Have you checked out unRAID? For more then 3 drives you have to pay for a license but seems very scalable and can be run from a tiny flash drive. The drives don't all need to be the same size but your parity drive needs to be the same size or larger then your largest HDD. Read about it here: [http://lime-technology.com/technology](http://lime-technology.com/technology)

---

### Post by rubylaser on 2012-11-28
SnapRAID + AUFS is similar to UnRAID (without the Web Interface) and is open source and free, but if data integrity is paramount, I'd be doing this with ZFS and RAIDZ3 as mentioned above (I personally would use Openindiana + Napp-it instead of FreeNAS, but that's just personal preference).  

Here's a rough idea of what I would use for parts (not all inclusive, but an idea).

[CPU] [Intel Xeon E3-1230 V2 Ivy Bridge]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819117286")
[MOBO] [SUPERMICRO MBD-X9SCM-F-O]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813182253")
[RAM] [Kingston KVR1333D3E9SK2/8G RAM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820139262") x 2 = 16GB (ZFS loves RAM)
[HD] [TOSHIBA DT01ACA300 3TB]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822149408") x 10 (These are rebadged Hitachi drives and work great with ZFS).
[CASE] [Norco 4020]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811219021") or similar
[HBA][ IBM1015]("http://www.ebay.com/sch/i.html?_trksid=p5197.m570.l1313&_nkw=ibm+m1015&_sacat=0&_from=R40") x 2 Flashed to IT mode. This would support connecting 16 drives without the need for a port multiplier.

Price with hard drives is ~$2,550.  You'd still need (4) SFF-8087 cables, but they can be had for around [$10 each]("http://www.monoprice.com/products/product.asp?c_id=102&cp_id=10254&cs_id=1025406&p_id=8186&seq=1&format=2"). Also, I'd suggest installing the OS on separate ZFS mirror if you go the Openindiana route (never tried this on FreeNAS).

Another thing I'd want to know from the vendor is the Mbps rate from each camera to make sure that a single gigabit connection to the server is enough to keep up.  You may want/need to look at LACPing a few interfaces or using 10GBe.

---

### Post by darkod on 2012-11-29
Yeah, that's another thing I love with FreeNAS. If you need more than a Gb connection, it's very easy to do link aggregation of more interfaces. Including the static aggregarion, and the LACP (dynamic).

Personally I started my testing with freenas because I suck at Unix and OpenIndiana or Solaris Express (which by the way I think is withdrawn now) looked way beyond me. :)

---

### Post by jgalloway on 2012-11-29
> **darkod said:**
> 
I don't have too much experience with similar  setups, and probably others will have better ideas, but... I would  seriously look into FreeNAS.

It might take some learning, but it sounds to me like ideal for the job.  I am myself investigating it in VBox before I suggest it for a  production machine.


I have heard of that and fooled around with it for a while, but  never really for productive use anyway. I'll be willing to go with  whatever works, but I would still would need confirmation that FreeNas  works with the PERC cards.

> **darkod said:**
> 
The OS itself can run on as little as 2GB, including from usb stick or  Compact Flash card, so any similar device of 4GB/8GB would do. The  reason to use small devices is that the disk that holds the OS can not  be used for data, so if you use a large disk it's wasted.

Interesting  limitation, but easily overcome, we have a good supply of HDs and I  think the HD standard to our machine is a 70GB, but that's ok, I even  have some HDs as low as 10GB if I remember right. :smile:

> **darkod said:**
> 
I assume there will be another machine running some kind of CCTV software and you will need this server only for storage.


I assume as well, I have seen of this IP cams streaming  directly to NAS, but I doubt that would be the case. I believe he  mentioned the client software operates on Windows 7, but we wont know  for sure exactly how the system works until we get the software specs I  think.


> **darkod said:**
> 
There are three basic  levels of raid, that FreeNAS calls RAIDZ (one disk redundancy), RAIDZ2  (two disk redundancy) and RAIDZ3 (three disk redundancy).... That falls  great into your needs, right?

I think it would and it has  a little more efficient use of disk space. Though I guess I should say I  don't know if I trust the RAIDZ3 well enough to stake my life on it yet  :wink:  but I think Ill install it on a development machine and go through some  rigorous tests and see how resistant it is to hardware failures. If I  remember right I think FreeNas has the ability to mirror as well, so  maybe we can mirror a RAIDZ3 array.... actually the more I think about  that, the more I like it :smile:


> **darkod said:**
> 
Also you can find many online articles about the benefits of ZFS, or downsides if you manage to find any serious ones.

I  think I did find a downside (not to the ZFS file system) but the  software raid of freeNas (RAIDZ3 RAIDZ2 ext,) that having a large number  of HDs bottlenecks transfer speed. Probably like RAID 4 where the  dedicated parity disk bottlenecks performance from dependency on a  single disks read/write/seek.

Ill have to find reference though, I  have never experienced that myself, especially since the only NAS we  have uses external hardware RAID.


> **rubylaser said:**
> Another thing I'd want to know from the vendor  is the Mbps rate from each camera to make sure that a single gigabit  connection to the server is enough to keep up.  You may want/need to  look at LACPing a few interfaces or using 10GBe.


I have a note they mentioned using a pelco IP camera that is 1.3 Megapixel

Not sure if this is it exactly: but the bandwidth specs should be the same.
http://www.global-download.schneider-electric.com/85257689000007EE/all/901CF7C8D19BAA9D852578D50008CFDF/$File/en_c2981_im10v_sarix_r021312.pdf

H.264  looks like it uses 2.5 Mbps which translates to about 780-730MB a  month, which is close to the 1TB a month originally quoted.

We have gigabit Ethernet all the way through the district, so one Ethernet can handle ~400 cameras streaming theoretically. :rolleyes:  A more logical guess would be ~200-250 accounting for overhead. (And we  need to leave some bandwidth for reading proposes, when videos want to  be accessed)

---

### Post by rubylaser on 2012-11-29
> **jgalloway said:**
> I think it would and it has  a little more efficient use of disk space. Though I guess I should say I  don't know if I trust the RAIDZ3 well enough to stake my life on it yet  :wink:  but I think Ill install it on a development machine and go through some  rigorous tests and see how resistant it is to hardware failures. If I  remember right I think FreeNas has the ability to mirror as well, so  maybe we can mirror a RAIDZ3 array.... actually the more I think about  that, the more I like it :smile:

ZFS is VERY fault tolerant to hardware failures and will not be susceptible to the RAID5/6 write hole either. Mirroring a RAIDZ3 would be ridiculous/unnecessary in my opinion with the number of disks in question.  This will survive 3 simultaneous disk failures with only 10 disks in use. If this data is as critical as you say, a more prudent measure would be to build a second server to backup your original RAID set to.
 
> **jgalloway said:**
> I  think I did find a downside (not to the ZFS file system) but the  software raid of freeNas (RAIDZ3 RAIDZ2 ext,) that having a large number  of HDs bottlenecks transfer speed. Probably like RAID 4 where the  dedicated parity disk bottlenecks performance from dependency on a  single disks read/write/seek.

Ill have to find reference though, I  have never experienced that myself, especially since the only NAS we  have uses external hardware RAID.

What you are talking about is IOPS, and reading from one big vdev.  With the 10 disk array that I mentioned, you'd have no problem getting around 600-700MBps read and write to the array.  This will easily saturate gigabit many times over.  Bottlenecks for your use case will not be an issue.

> **jgalloway said:**
> I have a note they mentioned using a pelco IP camera that is 1.3 Megapixel

Not sure if this is it exactly: but the bandwidth specs should be the same.
http://www.global-download.schneider-electric.com/85257689000007EE/all/901CF7C8D19BAA9D852578D50008CFDF/$File/en_c2981_im10v_sarix_r021312.pdf

H.264  looks like it uses 2.5 Mbps which translates to about 780-730MB a  month, which is close to the 1TB a month originally quoted.

We have gigabit Ethernet all the way through the district, so one Ethernet can handle ~400 cameras streaming theoretically. :rolleyes:  A more logical guess would be ~200-250 accounting for overhead. (And we  need to leave some bandwidth for reading proposes, when videos want to  be accessed)

Those are fairly low bitrate cameras, so gigabit should be fine. I'd still be aggregating some NICs for redundancy and to mitigate a single NIC causes a bottleneck.

---

### Post by darkod on 2012-11-29
When you are investigating the PERC support, there is one more thing I forgot to mention.
The controller has to be able to "show" the disks as plain disk devices. The raid (in this case RAIDZ) is done by freenas and you will not be using any raid from the controller card itself.

I am not sure whether all of these server cards allow the option to show the disks directly without any raid arrays configured.

---

### Post by rubylaser on 2012-11-29
> **darkod said:**
> When you are investigating the PERC support, there is one more thing I forgot to mention.
The controller has to be able to "show" the disks as plain disk devices. The raid (in this case RAIDZ) is done by freenas and you will not be using any raid from the controller card itself.

I am not sure whether all of these server cards allow the option to show the disks directly without any raid arrays configured.

You'd really want to avoid using a PERC card with ZFS.  They are raid controllers, so the best way you could pass them through would be as single disk RAID0s.  Also, it's likely you'd lose one of ZFS's main benefits to self heal checksum errors.

A simple (cheaper) HBA like the IBM m1015's in IT mode work great and pass through the drives seamlessly to the OS.

---

### Post by darkod on 2012-11-29
> **rubylaser said:**
> You'd really want to avoid using a PERC card with ZFS.  They are raid controllers, so the best way you could pass them through would be as single disk RAID0s.  Also, it's likely you'd lose one of ZFS's main benefits to self heal checksum errors.

A simple (cheaper) HBA like the IBM m1015's in IT mode work great and pass through the drives seamlessly to the OS.

Rubylaser, while we are on the subject. I got interested in this IBM M1015 card. Does it offer pass through of disks by default or only flashed because you mentioned flashing it in the previous post?

Is it good for this kind of setup, where you need a card only for pass through and not raid? Would you be able to substitute a raid card with it?

---

### Post by rubylaser on 2012-11-29
> **darkod said:**
> Rubylaser, while we are on the subject. I got interested in this IBM M1015 card. Does it offer pass through of disks by default or only flashed because you mentioned flashing it in the previous post?

Is it good for this kind of setup, where you need a card only for pass through and not raid? Would you be able to substitute a raid card with it?

The default firmware on the card is IR (integrated RAID, and supports RAID0/1).  It's really a LSI 9220-8i card, and [flashing to IT firmware]("http://lime-technology.com/forum/index.php?topic=12767.msg121131#msg121131") is VERY easy (less than 2 minutes) and allows you to pass the disks directly through. Here's another [great series]("http://www.servethehome.com/ibm-serveraid-m1015-75-dollars/") about the features of the card.

It is perfect for anytime you just need an HBA to attach a bunch of disks that are just passed through the OS (ZFS, mdadm, UNRAID, SnapRAID, etc).  I'm not sure what you mean about being able to substitute a RAID card.  Since it's an HBA, you're not locked into this card at all, just think of it as adding 8 SATAIII ports to your motherboard.

Hope that answers your question :)

---

### Post by darkod on 2012-11-29
I meant in a situation if you want to substitute a raid only card in existing server, not when you are building one from scratch.

For example, I have a server with 16 bays but the controller is raid only, doesn't allow pass through. Provided there are two PCIe 8x slots free, you would install two of these cards and I assume you can connect them to the disks (backplate) somehow... Of course, that would depend from server to server...

But in general, it should be doable I guess.

---

### Post by rubylaser on 2012-11-29
> **darkod said:**
> I meant in a situation if you want to substitute a raid only card in existing server, not when you are building one from scratch.

For example, I have a server with 16 bays but the controller is raid only, doesn't allow pass through. Provided there are two PCIe 8x slots free, you would install two of these cards and I assume you can connect them to the disks (backplate) somehow... Of course, that would depend from server to server...

But in general, it should be doable I guess.

Yes, that would work.  You'd just need the correct [8087 cable]("http://www.monoprice.com/products/search.asp?keyword=SFF-8087") to connect to your server's backplane.

---

### Post by jgalloway on 2012-11-30
> **rubylaser said:**
> ZFS is VERY fault tolerant to hardware  failures and will not be susceptible to the RAID5/6 write hole either.  Mirroring a RAIDZ3 would be ridiculous/unnecessary in my opinion with  the number of disks in question.  This will survive 3 simultaneous disk  failures with only 10 disks in use. If this data is as critical as you  say, a more prudent measure would be to build a second server to backup  your original RAID set to.
 
Well I am probably just being my old paranoid self, but I just  wanted the system to work 99.9999999999% of the time, since with my  luck, something will happen where we need video surveillance the  second  it goes down. :sad:

IMHO  we really shouldn't need 1 month of video stream, perhaps 2 weeks would  be best and that would cut down data by half, but well... unless we can  convince otherwise...

> **rubylaser said:**
> 
What you are talking about is IOPS, and reading from one big vdev.  With  the 10 disk array that I mentioned, you'd have no problem getting  around 600-700MBps read and write to the array.  This will easily  saturate gigabit many times over.  Bottlenecks for your use case will  not be an issue.

Ah I figured as much, that it would be only for very very large deployment.


> **rubylaser said:**
> 
Those are fairly low bitrate cameras, so gigabit should be fine. I'd  still be aggregating some NICs for redundancy and to mitigate a single  NIC causes a bottleneck.

Agreed wholeheartedly :smile:

> **rubylaser said:**
> You'd really want to avoid using a PERC card  with ZFS.  They are raid controllers, so the best way you could pass  them through would be as single disk RAID0s.  Also, it's likely you'd  lose one of ZFS's main benefits to self heal checksum errors.

A simple (cheaper) HBA like the IBM m1015's in IT mode work great and pass through the drives seamlessly to the OS.

I found a few references saying the same thing, so PERC is out. I  also found several sources that say the same thing, PERC doesn't work  well because it doesn't support JBOD. 

In the same paragraph mentioned LSI HBAs;
[http://www.lsi.com/products/storagecomponents/Pages/HBAs.aspx](http://www.lsi.com/products/storagecomponents/Pages/HBAs.aspx)

Anyway these LSI cards where recommended at least once... yowsa expensive cards...

Actually looks like any controller larger than 2 port gets expensive.

Well the whole point of using the LSI card is because it is a SATA controller... or it supports non-RAID mode (like JBOD)

So I found this in FreeNas documentation. 
[http://doc.freenas.org/index.php/Hardware_Recommendations](http://doc.freenas.org/index.php/Hardware_Recommendations)

[QUOTE=freenas.org]instead of mixing ZFS RAID with hardware RAID, it is recommended that  you place your hardware RAID controller in JBOD mode and let ZFS handle  the RAID[/QUOTE]

So I think I can take it from this statement, that any any RAID controller card with JBOD would work properly.


Oh and here is another limitation: I cannot go to ebay, or amazon or  walmart... or many other retailers. Actually a pretty big limit on  the retailers I can go through. :sad: Primarily because of the method of payment 'preferred' even though its cheaper.. [IMG]http://www.planetsmilies.com/smilies/mad/mad0228.gif[/IMG]

---

### Post by rubylaser on 2012-11-30
I have a similar situation at work, and it takes an act of Congress to buy from somewhere else.  Or, I just use my personal credit card and then put in for a reimbursement.  

Can you use someone like [CDW]("http://www.cdw.com/shop/products/LSI-MegaRAID-SAS-9240-8i-storage-controller-RAID-SATA-600-SAS-PCI/1982609.aspx") or [Provantage]("http://www.provantage.com/ibm-46m0831~7IBSR23L.htm")?  They both provide invoicing options that can be run through your Accounts Payable department.  

They are both way more expensive than server pulls like you'd get on Ebay, but these are very good HBA's that support disks greater than 2TB and won't be the bottleneck even with SSD's on each port.

---

### Post by jgalloway on 2012-11-30
> **rubylaser said:**
> I have a similar situation at work, and it takes an act of Congress to buy from somewhere else.  Or, I just use my personal credit card and then put in for a reimbursement.  

Can you use someone like [CDW]("http://www.cdw.com/shop/products/LSI-MegaRAID-SAS-9240-8i-storage-controller-RAID-SATA-600-SAS-PCI/1982609.aspx") or [Provantage]("http://www.provantage.com/ibm-46m0831~7IBSR23L.htm")?  They both provide invoicing options that can be run through your Accounts Payable department.  

They are both way more expensive than server pulls like you'd get on Ebay, but these are very good HBA's that support disks greater than 2TB and won't be the bottleneck even with SSD's on each port.

Actually CDW is the company they like ordering from (we use CDW-G because we are a school) I haven't seen provantage before but I am liking the price difference :)

As long as they use POs then I think it should be ok. 

For the price difference between ebay and online sites.. I think it might be worth the headache cutting through the red tape to get those cards reduced price. I have to wonder though, to buy electronics on ebay... makes me wonder if they are working cards or not

---

### Post by rubylaser on 2012-11-30
You are covered by Ebay's buyer protection + every one of those sellers also provides some form of warranty.  As an FYI, I've purchased 10 of these cards at this point from Ebay for various servers (and some additional IBM br10i cards as well), and they've all performed flawlessly.

---

