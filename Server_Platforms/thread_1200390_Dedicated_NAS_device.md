---
title: "Dedicated NAS device"
date: 2009-06-30
forum: Server Platforms
---

### Post by BDNiner on 2009-06-30
I am looking into buying a NAS device like the Buffalo Linkstation or WD My book World Edition. I wanted to know if anyone has any experience with these devices. 

I have looked into putting together a small file server. The main reason why I don't want to build a home server is space and noise. I don't think that I can sleep with the humming of a PC all night. 

This may be the more expensive option too. I know the device and gigabit switch and the cables would cost more than using an old computer with a RAID card and a couple hard disks.

So any thoughts or comments?

---

### Post by dtoronto on 2009-06-30
I'm not sure about the devices that you're thinking about, but you may want to look at FreeNAS which runs on a FreeBSD version of UNIX if you're under a budget.

---

### Post by TwiceOver on 2009-06-30
Intel Atom based passively cooled board/proc combo, and a bunch of drives.  Much better solution than a device that only serves files.

---

### Post by Henrike Corinna on 2009-06-30
**[SIZE=2]Can anyone recommend software that will act as a network attached storage device?[/SIZE]**

---

### Post by BDNiner on 2009-06-30
> **dtoronto said:**
> I'm not sure about the devices that you're thinking about, but you may want to look at FreeNAS which runs on a FreeBSD version of UNIX if you're under a budget.

I have looked into FreeNAS but I don't want to have another PC running constantly. And even if i used the shuttle form factor it would still be too big. I was looking for advice on NAS devices like Western Digital's My Book World Edition, or something along those lines. It is basically a pre built hard disk with a NIC and a long power processor.

---

### Post by BDNiner on 2009-06-30
> **TwiceOver said:**
> Intel Atom based passively cooled board/proc combo, and a bunch of drives.  Much better solution than a device that only serves files.

That would still be a lot bigger than I was hoping. I am going to research passive cooling. It will deal with the noise aspect, so I may just have to sacrifice size.

---

### Post by BDNiner on 2009-06-30
> **Henrike Corinna said:**
> **[SIZE=2]Can anyone recommend software that will act as a network attached storage device?[/SIZE]**

I don't understand what you are asking. Any OS with the correct software can provide the services of a NAS device. What services are you looking to have? FTP, backups, media sharing?

---

### Post by windependence on 2009-06-30
> **BDNiner said:**
> That would still be a lot bigger than I was hoping. I am going to research passive cooling. It will deal with the noise aspect, so I may just have to sacrifice size.

I build these all the time for my clients:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16811154091](http://www.newegg.com/Product/Product.aspx?Item=N82E16811154091)

Totally silent with the Atom 230 or 330 board. Run two 1TB drives and FreeNAS. You can even run the FreeNAS system on an SD card plugged into the IDE slot on the board, then you don't waste any space. These systems only take about 32 watts of power. FreeBSD is an awesome OS and extremely tiny, powerful, and rock solid.

If you want a smaller case yet, Apex makes a case with an external power supply.

-Tim

---

### Post by BDNiner on 2009-06-30
> **windependence said:**
> I build these all the time for my clients:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16811154091](http://www.newegg.com/Product/Product.aspx?Item=N82E16811154091)

Totally silent with the Atom 230 or 330 board. Run two 1TB drives and FreeNAS. You can even run the FreeNAS system on an SD card plugged into the IDE slot on the board, then you don't waste any space. These systems only take about 32 watts of power. FreeBSD is an awesome OS and extremely tiny, powerful, and rock solid.

If you want a smaller case yet, Apex makes a case with an external power supply.

-Tim

How is the noise from the fan on the power supply. In a business I guess the humming is drowned out. Does the device get hot? I will also look at the external power supply case. That seems better, since there should be no noise coming from it at all. FreeBSD seems to get a lot of recommendations.

---

### Post by windependence on 2009-06-30
Because FreeBSD IS Unix. It has been around for decades. 

There is NO noise from the unit. There is no fan on the CPU, only in the chipset and it's tiny. You absolutely cannot hear it. There is no humming whatsoever. I have these in my house. At 32 watts it does NOT get hot at all, barely warm.

-Tim

---

### Post by memilanuk on 2009-06-30
Tim,

I don't suppose you could supply a sample parts list of what all you might stuff in one of said little mini-ITX cases for an average build?  Known good combinations and all that ;)

Thanks,

Monte

---

### Post by DownTown22 on 2009-06-30
To answer your question, I have a D-Link DNS-323 setup in my house to store all my files, etc.  I also have the UPnP AV server and iTunes servers activated which is nice for sharing music and videos with various computers in the house.  I also use the built-in FTP server to access files when I'm away from the house.  I've had it for about a year with no problems whatsoever.

The only thing with this NAS device is that you have to buy the drives separately - I see this as a bonus because it allows me upgrade my drives to larger ones (which I just did....500GB drives to 1TB drives).

Almost forgot, it also acts as a print server as well, so any computer can print to it!

---

### Post by kustomjs on 2009-06-30
I would use FreeNAS and get a computer that have SATA ports on it and add up to 6tb or what ever size of storage you want.

---

### Post by michaelzap on 2009-07-01
I have a Buffalo LinkStation and an HP MediaVault, and I highly recommend using a NAS instead of building a server. They make very little noise, use almost no electricity, and are simple and reliable.

The Buffalo is my favorite (had it for years now). I'd definitely get another Buffalo NAS before trying another brand. The HP isn't bad, but it just seems a little bit clunkier.

The only negative that I don't like about using a NAS instead of a home server is that it's very difficult to encrypt your data if multiple people will be mounting the volume at the same time, so consider that and perhaps one of the new Buffalos does encryption now.

---

### Post by BDNiner on 2009-07-02
Thank you for your responses Downtown22 and michaelzap. I have been looking a products from Buffalo, Dlink and the WD my book. I am leaning towards the Buffalo link station. I would also like to hear the sample parts list for your mini-ITX computers. having an actual PC allows me to perform maintennance than rely on the manufacturer. which is what I would prefer todo. But the other devices if they work with little head ache are great because of the small footprint and low noise. 

Are you able to run the Buffalo linkstation and DLINK device constantly?

---

### Post by michaelzap on 2009-07-02
> **BDNiner said:**
> Are you able to run the Buffalo linkstation and DLINK device constantly?

I practically never turn off my Linkstation. It spins down after prolonged inactivity, so it sleeps when I do. Custom firmware is available for the Linkstation if you want to do more interesting things with it:
[http://buffalo.nas-central.org/index.php?title=FAQ](http://buffalo.nas-central.org/index.php?title=FAQ)

---

### Post by BDNiner on 2009-07-02
> **michaelzap said:**
> I practically never turn off my Linkstation. It spins down after prolonged inactivity, so it sleeps when I do. Custom firmware is available for the Linkstation if you want to do more interesting things with it:
[http://buffalo.nas-central.org/index.php?title=FAQ](http://buffalo.nas-central.org/index.php?title=FAQ)

Thanks for the link. It looks like I can do a lot more with this device if I decide to hack it. It makes me want to buy 2 of them. How are the transfer speeds? I am looking at 1 computer accessing it using a hard line and the other devices connecting wirelessly.

---

### Post by michaelzap on 2009-07-02
> **BDNiner said:**
> Thanks for the link. It looks like I can do a lot more with this device if I decide to hack it. It makes me want to buy 2 of them. How are the transfer speeds? I am looking at 1 computer accessing it using a hard line and the other devices connecting wirelessly.

I've never had any reason to test the transfer speed, but I routinely compress video to it and open and work on large files directly from it without any hiccups.

Wireless is slower than cable, of course. There are pretty much always two of us connected and using files at any given time, and we play our mp3 library from it also. It just works.

---

### Post by BDNiner on 2009-07-02
> **michaelzap said:**
> I've never had any reason to test the transfer speed, but I routinely compress video to it and open and work on large files directly from it without any hiccups.

Wireless is slower than cable, of course. There are pretty much always two of us connected and using files at any given time, and we play our mp3 library from it also. It just works.

The only reason I asked about transfer speeds is because I am planing on moving about 100GBs as soon as I get the device and I wanted to know the performance of the machine. Nice to see that you share the music. Do you buy chance use an ipod/iphone and can it load files on the device over the network?

---

### Post by michaelzap on 2009-07-02
> **BDNiner said:**
> The only reason I asked about transfer speeds is because I am planing on moving about 100GBs as soon as I get the device and I wanted to know the performance of the machine. Nice to see that you share the music. Do you buy chance use an ipod/iphone and can it load files on the device over the network?

Start the transfer before going to bed, and when you get up it'll be done.

I don't own an iPod or iPhone, but I assume that it wouldn't have any problems with a NAS. I just mount mine using fstab, so as far as the iPod would know this is a local directory. I can also play my mp3s and video files wirelessly using a D-Link media doohickie that I ave hooked up to my teevee upstairs (although that's using the built-in media server on my HP MediaVault; my Linkstation is 1st-generation and they didn't have media servers back then).

---

### Post by windependence on 2009-07-02
> **memilanuk said:**
> Tim,

I don't suppose you could supply a sample parts list of what all you might stuff in one of said little mini-ITX cases for an average build?  Known good combinations and all that ;)

Thanks,

Monte

Sure, I am out at a client right now, but when I get home I'll put it together for ya.

-Tim

---

### Post by DownTown22 on 2009-07-02
> **BDNiner said:**
> Thank you for your responses Downtown22 and michaelzap. I have been looking a products from Buffalo, Dlink and the WD my book. I am leaning towards the Buffalo link station. I would also like to hear the sample parts list for your mini-ITX computers. having an actual PC allows me to perform maintennance than rely on the manufacturer. which is what I would prefer todo. But the other devices if they work with little head ache are great because of the small footprint and low noise. 

Are you able to run the Buffalo linkstation and DLINK device constantly?

My DNS-323 runs constantly.  You can set it so the drives spin down after so many minutes/hours without activity.
I've never bothered to do any hacking on mine as it does exactly what I need it to already!

---

### Post by BDNiner on 2009-07-02
> **michaelzap said:**
> Start the transfer before going to bed, and when you get up it'll be done.

I don't own an iPod or iPhone, but I assume that it wouldn't have any problems with a NAS. I just mount mine using fstab, so as far as the iPod would know this is a local directory. I can also play my mp3s and video files wirelessly using a D-Link media doohickie that I ave hooked up to my teevee upstairs (although that's using the built-in media server on my HP MediaVault; my Linkstation is 1st-generation and they didn't have media servers back then).

That is cool. I was planning on using ushare and my xbox360 to play media files on the main tv. I can already do this with my current setup. There is a delay in playing media though. About 1 second. My tv actually has a network jack on the back and there is a wireless dongle that Samsung makes for the tv. I haven't tried plugging in one of my other wireless dongles into the tv to see if it works. The O/S for the tv is some variation of Linux so I don't see why it would not work.

Loading files onto my iphone and ipod over the network is something I will have to try. If anything I will have to keep 2 copies of my music library, but that is not a big deal. I just want to have the backup.

So you media vault runs windows server? or did you install linux on that machine?

---

### Post by michaelzap on 2009-07-03
> **BDNiner said:**
> So you media vault runs windows server? or did you install linux on that machine?

Not Windows. The HP runs Linux and has a media server built-in. More info here:
[http://www.k0lee.com/hpmediavault/#dlna](http://www.k0lee.com/hpmediavault/#dlna)

I expect that newer Linkstations also have this feature, but I haven't investigated.

---

### Post by DownTown22 on 2009-07-03
This is the first I've heard about the HP Media Vault and I must say they're looking pretty nice!

---

### Post by michaelzap on 2009-07-03
> **DownTown22 said:**
> This is the first I've heard about the HP Media Vault and I must say they're looking pretty nice!

They're not bad, but I still prefer the Buffalo. I'm not really sure why, so maybe it's just a personal whim. Maybe it's because when I first bought my HP the drive died on me within a couple weeks (and when I called to have it replaced they told me that the warranty had expired in July, even though I bought it in September; they eventually did replace the drive at no cost, so I suppose I shouldn't hold that against them). The HP is a much bigger unit (and I've added a 2nd drive, which is super easy). I guess I've always felt that every Buffalo device I've ever had has been top-notch, whereas HPs are hit-or-miss.

---

### Post by BDNiner on 2009-07-20
I decided to go with the Buffalo 1TB drive. I went with BUFFALO LS-XH1.0TL 1TB LinkStation Pro Network Attached Storage. link is here, [http://www.newegg.com/Product/Product.aspx?Item=N82E16822165154](http://www.newegg.com/Product/Product.aspx?Item=N82E16822165154)

---

### Post by tilapia on 2009-08-08
The other really neat thing about the HP Media Vault machines is that they can be hacked to run Debian! This gives much better support for larger disks, as well as better security updates and more software than the version of Linux which is pre-installed, albeit without the web GUI. Though you could install Ebox or Webmin or something if you really needed it. 

I set up mine using this guide: [http://techpad.co.uk/content.php?sid=63](http://techpad.co.uk/content.php?sid=63)

---

