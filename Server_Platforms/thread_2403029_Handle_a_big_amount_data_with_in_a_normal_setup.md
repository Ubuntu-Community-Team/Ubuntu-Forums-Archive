---
title: "Handle a big amount data with in a normal setup"
date: 2018-10-06
forum: Server Platforms
---

### Post by sed_faster on 2018-10-06
Hello,

I am studying a way to create a server where I can put many disks (I am thinking starting with 6 drives sata). After I search on internet I found this project:

1-https://www.backblaze.com/blog/wp-content/uploads/2015/11/Storage-Pod-5.0-Build-Book-V4.pdf
2-https://cdn.shopify.com/s/files/1/0848/1004/files/BPEVE252443_REV_A_STARTUP_GUIDE_6.0.pdf?5737656823305951323
3-https://www.backuppods.com/?variant=20041428743
4-https://www.backblaze.com/

My idea is "Bought the BackPlane and Sata Card" and connect the disk in normally motherboard with a SO Ubuntu Server (or debian, after I study this distribution). What do you think about this idea? Anyone have a good experience with this hardware? Do you suggestion another equipment or projects?
The goal of my project is "handle a big amount data through a normal motherboard and disks". I don't need many velocity, 2GHz and 2 Ram are more than enough to me.

Thanks

---

### Post by sed_faster on 2018-12-31
Hello,

After all these months I still need build this solution. Today I asked backblaze relative where can I buy their solution. Anyone have experience with this? Where can I buy the red case and all system?
Thanks

---

### Post by Tadaen_Sylvermane on 2018-12-31
How much data are you storing? A backup pod is just a fancy name for a nas as far as I'm concerned. Can do it with any hardware and case. Doesn't have to be specifically that one. Example. My current media collection is all sitting on a single 2 terrabyte drive. 631 movies + 1200 episodes of tv shows + 1600 mp3 files for music. I still have 34% of my space available according to Kodi. All backed up with snapraid to another drive. This is housed in an mITX case. AMD quad core Kabini at 2.2? ghz with 8 gigs of ram. 120gb ssd for OS and other. Total spent, about 400 bucks. Also serves as my living room media center.

Requirements for a nas are simple. Case with enough space for as many drives as you realistically need + mobo that can handle all the sata connections you will need / or PCIx slots to house SATA cards. Doesn't need to be high powered or fancy. Even cheap consumer hardware will work just fine as long as it isn't under tremendous load. You don't need anything special or custom. The only thing you may need special is RAM amount. And that is only if you use ZFS as your filesystem with deduplication enabled. Think it's 5gigs per terrabyte but I'm not sure about that. I know there is some debate on that number.

---

### Post by sed_faster on 2018-12-31
I agree with you. Maybe I am dreaming some high. I found this video/company: [https://www.youtube.com/watch?v=A0wV4k58RIs](https://www.youtube.com/watch?v=A0wV4k58RIs)
At the moment I have not knowledge needed to handle this system but I will study :D
But right now I need know cheap case where I can put more a less eight hard drives. All cases I found only I can assembled four hard drives and the system it is very poor.

Thanks

**[UPDATE1]**
What PCI card do you suggest to connect more hard drives sata into to my board!? I asked this because the pci card should be compatible with linux and good (I bought some this pci card from ebay and this is very bad).
The version and model of the motherboard it is important to define the model PCI Card?

Thanks

---

### Post by volkswagner on 2019-01-01
Perhaps starting off with a budget, current storage needs (how many terabytes) and future growth would be helpful.

Have you seen these [http://www.45drives.com/products/storage/]("http://www.45drives.com/products/storage/") ?

---

### Post by Tadaen_Sylvermane on 2019-01-01
> [COLOR=#000000]What PCI card do you suggest to connect more hard drives sata into to my board!?[/COLOR][COLOR=#000000]

When I was researching upgrading my own server I was directed toward the LSI 9211 I think. Flash to IT mode and you can manage the drives independently. Each card can handle 8 sata drives if I recall correctly. I ultimately abandoned that as I didn't need as much storage as I thought I would. Hence why you need to establish a target storage size, then assemble parts to make it work. Can't do it backwards. 6, 8 drives is meaningless if you only need to store a few hundred gigabytes of data. Then you will just end up with a ton of dead space, wasted money that you may never use. Every person's idea of "Large storage" is different. Again in my own example, I feel I have a respectable media library and it all fits comfortably on a single 2 terrabyte drive with another one as a backup. Every scenario is unique.[/COLOR]

---

### Post by sed_faster on 2019-01-01
> **volkswagner said:**
> Perhaps starting off with a budget, current storage needs (how many terabytes) and future growth would be helpful.

Have you seen these [http://www.45drives.com/products/storage/](http://www.45drives.com/products/storage/) ?

The budget will depend of the solution which I choose to start build my owner server system. But in first impress the budget level is in "in the least possible" :)

I intend build a system where I can put something like 12TB distributed by twenty-four hard drives each 1TB (this is will be a system where I will use 12TB mirrored with 12TB). If the motherboard would have four connection sata I only need five pci card where each must have four connection sata. Ok, I don't know if this is possible or if exist motherboard where I can find four connection pci to connect so many hard drives. I am do this from scratch.

On this link: [http://www.45drives.com/products/storage/](http://www.45drives.com/products/storage/) I only can buy all solution. I only need the case (note: I haven't yet build the system).

> **Tadaen_Sylvermane said:**
> [COLOR=#000000]

When I was researching upgrading my own server I was directed toward the  LSI 9211 I think. Flash to IT mode and you can manage the drives  independently. Each card can handle 8 sata drives if I recall correctly.  I ultimately abandoned that as I didn't need as much storage as I  thought I would. Hence why you need to establish a target storage size,  then assemble parts to make it work. Can't do it backwards. 6, 8 drives  is meaningless if you only need to store a few hundred gigabytes of  data. Then you will just end up with a ton of dead space, wasted money  that you may never use. Every person's idea of "Large storage" is  different. Again in my own example, I feel I have a respectable media  library and it all fits comfortably on a single 2 terrabyte drive with  another one as a backup. Every scenario is unique.[/COLOR]

You talking about this, right ([https://www.starline.de/fileadmin/images/produkte/lsi/LSISAS92118i__ENG_.pdf)?](https://www.starline.de/fileadmin/images/produkte/lsi/LSISAS92118i__ENG_.pdf)?)

I am thinking build my own case. Maybe this is more simple because all case system I found are designed to connect in system rack in big environment servers. My environment it is domestic/small business. I don't know, right know I have not made any final decisions yet.

Thanks

---

### Post by volkswagner on 2019-01-02
I'm not sure why you'd want to use 24 drives for only 12 TB of space.
I can only assume you are getting the drives for free???
That seems to be a huge waste in electricity (assuming 3.5" hard drives).

For ~$800 you can get 16TB of storage in a RAID 10 array
with four of [these drives]("https://www.newegg.com/Product/Product.aspx?Item=22-183-793&utm_medium=Email&utm_source=GD010219&cm_mmc=EMC-GD010219-_-landing-_-Item-_-22-183-793").

---

### Post by sed_faster on 2019-01-02
> **volkswagner said:**
> I'm not sure why you'd want to use 24 drives for only 12 TB of space.
I can only assume you are getting the drives for free???
That seems to be a huge waste in electricity (assuming 3.5" hard drives).

For ~$800 you can get 16TB of storage in a RAID 10 array
with four of [these drives]("https://www.newegg.com/Product/Product.aspx?Item=22-183-793&utm_medium=Email&utm_source=GD010219&cm_mmc=EMC-GD010219-_-landing-_-Item-_-22-183-793").

I am newbie guy in this subject/world. I didn't think this way. I need many space and I will reconfigure the number of the hard drives through your advice. But I still need the system/structure/environment where I can add hard drives along the time because I don't know when and what space I will need space. The limit will be the structure of the motherboard, I think.

---

### Post by sed_faster on 2019-01-04
I am thinking build some like this: [https://www.youtube.com/watch?v=EDnAf2w2v-Y](https://www.youtube.com/watch?v=EDnAf2w2v-Y)

---

