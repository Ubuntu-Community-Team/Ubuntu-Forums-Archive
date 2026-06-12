---
title: "anyone running low power/noise servers?"
date: 2010-01-09
forum: Server Platforms
---

### Post by jobsonandrew on 2010-01-09
Hi,
I've got a low power low noise server at home which is doing great but I want something with a much higher capacity hd.. maybe 1.5 or 2 TB

CPU and memory wouldnt need to be too beefy, all it would be doing is seeving efilea and web pages as well as running teamspeak and other ubuntu server stuff

Anyone got a machine like this? I'd be interested in what hardware you have etc..

PS I have a nas drive but if I could use only ubuntu server I would

---

### Post by cascade9 on 2010-01-09
I dont run one myself, but I have built one for a friend- 

AMD Athlon II X2 235e (45 watt)
Gigabyte GA-MA770T UD3 
Asus EN8400GS silent 512M
2x2GB DDR3
1.5TB WD 'greeen power' Hdd. 
SeaSonic M12II 500 watt

+ Other stuff, but that was unimportant 

BTW, if your happy with your current quiet server, but its old (therefore no SATA ports) or you have used all the SATA ports, you could just add a PCI or PCI-E SATA card and a 1.5 or 2TB WD green power drive.

---

### Post by jobsonandrew on 2010-01-09
hi, thanks for the spec... the only problem ive got with my current box is that its just too small! cant actually get a 3.5" hard drive in the case..

im willing to get a bigger box if it means i can use a full size hard drive.. do you know if the WD "green power" drives are particularly quiet? im trying to go completely fanless

thanks again :)

---

### Post by smc18 on 2010-01-09
[http://www.newegg.com/Product/Product.aspx?Item=N82E16816110024&cm_re=asus_rs100-_-16-110-024-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16816110024&cm_re=asus_rs100-_-16-110-024-_-Product)

It's $350 on Newegg for the Asus RS100-X5/PI2. ($210 for an Open-Box deal) The barebone setup includes the 1U case, Motherboard, two small case fans, heatsink and Power supply.  The motherboard has a PCI and a PCIe slot, 2 SATA2 ports, 1 IDE header, two integrated NICS, integrated graphics, and I believe the Intel ICH7 Chipset.

All you need is a Socket 775 CPU, DDR2 memory and a slimline dvd drive.  (An External USB DVD Drive will work fine though)

I have mine with a Intel Core 2 Duo E7500 (2.93GHz, 3MB L2 Cache) and 4GB of memory.  The tech specs says it can only use 2GB but my 4GB sticks work but I only get 3.5GB out of it.

I'm currently using it for running XenServer to host some VMs and I can't complain.  The bright blue LED on the front case is more of an issue than any noise.  The server sounds just like a quiet tower PC.  Nothing like a real enterprise rackmount server that sound's like turbine fans when they POST or are at idle.

My complaint's are the super bright blue LED on the front(Hardly a real issue though), and the HDD setup.  There is room for two 3.5" HDD's and the Slimline DVD sits overtop of one HDD; this caused issues because I had to buy two different size laptop DVD connector to IDE adapters in order for it to fit properly.  (Not to mention I also had to make an extension cable for the Berg-style power connector for the IDE adapter because the adapter that finially fit, the Berg-style power connector did not reach.)

---

### Post by cascade9 on 2010-01-10
@ smc18- How I hate the 'OMG! sooo bright' LEDs in some cases. I have a neat, and cheap solution though- black marker pen. Just colour the LED black, it wont make it stop showing any light at all, but it will sure dim the cursed thing. (I did that with my current case, it was like a blue lazer in the dark LOL). 

That is actually a next little rackmount. If jobsonandrew already has a rack then its would be wortha  look, but if not, I wouldnt bother. Its just an Intel 945GC chipset in a rackmount case, you could get a 945GC chipset motherboard  and a really nice case and power supply for quite a bit less than that. 

> **jobsonandrew said:**
> hi, thanks for the spec... the only problem ive got with my current box is that its just too small! cant actually get a 3.5" hard drive in the case..

im willing to get a bigger box if it means i can use a full size hard drive.. do you know if the WD "green power" drives are particularly quiet? im trying to go completely fanless

thanks again :)

They are completely silent, but they are much more quiet than all the 7200 RPM drivers I've ever used. In my current boxen I've used a WD IDE 7200, seagate SATA 7200, seagate IDE 7200 and the WD GP drive is almost impossible to hear over my CPU/PSU fan, while everythign else I could hear the typical 'ticking and knocking' over the fans much more easily. Probably more quiet than any of the old 5400s. I would say they are for sure, but its been a while since I've used an IDE 5400. 

Very low power consumption compared to other drives will help in the quest for silent. Check power use figures here (and also general performance figures)- 

[http://www.xbitlabs.com/articles/storage/display/1tb-14hdd-roundup_21.html#sect0](http://www.xbitlabs.com/articles/storage/display/1tb-14hdd-roundup_21.html#sect0)

BTW- if your are4 trying to get as quiet a possible, the case is pretty important. I'm running a Antec Solo, which has the option to 'suspend' the HDDs (not using that, its too hot here and the rubber suspension cords stretched a little..and I move my case around a bit and suspension isnt the best for that). The 'standard' attachment  method is bolting onto removable plates- but where you screw the drives to the plates there are little silicon grommets/shock absorbers. Takes the edge of the 7200s compared to my last case, that used the standard 'hard bolted into a rack that is attached to the case with no shock absorption.' (never tried the WD GP drive in a 'standard' case so I have no idea how that drive compares) 

The neat hdd mounting and factory noise absorption in the case make it, or something like it, worth looking at IMO. 

Review on that case here (page 6 has the hdd mounting methods)- 

[http://www.bjorn3d.com/read.php?cID=937&pageID=2392](http://www.bjorn3d.com/read.php?cID=937&pageID=2392)

---

### Post by munky99999 on 2010-01-10
Mini-Itx + ssd(no hd spooling and clicking sounds)

[http://ncix.com/products/index.php?sku=39870&vpn=BOXDG41MJ&manufacture=Intel](http://ncix.com/products/index.php?sku=39870&vpn=BOXDG41MJ&manufacture=Intel)

8 gigs ram
gigabit lan.
3 sata slots

Get an appropriate cpu with extremely quiet heatsink. Dont go fanless as those typically, from the reviews i read, give off an annoying highpitched sound.

If you get the right chip and fan. You could almost have a sound-free machine.

---

### Post by cascade9 on 2010-01-10
Mini-ITX Intel core 2 duo wont be any quieter than a full size ATX intel core 2 duo. Actually, if your thinking about fanless, full size ATX is a better choice (mini ITX cases will heat up faster, less air in the case to absorb the heat). 

Yeah, I've heard that 'highpitched whine' on a fanless machine I built once, just as a joke from free parts I was given (nforce 2 motherboard, underclocked/undervoltaged athlon, 1GB DDR1, 9600XT). IIRC, it came from the video card, but no doubt other computer parts can make that horrid noise. 

Its easier try to make the case absorb the noise than most people would guess, but that is a lot more effort than most people would go to. 

SSDs arent a bad idea for noiseless, but the OP wants 1.5-2TB, and 1TB SSDs are just a little pricey at the moment- 

[http://www.newegg.com/product/product.aspx?Item=N82E16820227502](http://www.newegg.com/product/product.aspx?Item=N82E16820227502)

1TB- $3900.

---

### Post by munky99999 on 2010-01-10
> **cascade9 said:**
> 
SSDs arent a bad idea for noiseless, but the OP wants 1.5-2TB, and 1TB SSDs are just a little pricey at the moment- 

[http://www.newegg.com/product/product.aspx?Item=N82E16820227502](http://www.newegg.com/product/product.aspx?Item=N82E16820227502)

1TB- $3900.
Totally spaced on that. SSD -> 3 sata totally didnt connect in my head.

I guess the alternative is to have the ssd for the base system stuff. Then have regular drives for the space needs. That way those mechanical ones can spin down.

> Mini-ITX Intel core 2 duo wont be any quieter than a full size ATX intel core 2 duo. Actually, if your thinking about fanless, full size ATX is a better choice (mini ITX cases will heat up faster, less air in the case to absorb the heat).
Well ya. pretty much. Except you miss the case part. I was thinking more of a brownbox sort of case :) Mini-itx is so rare that the cases are ridculously priced. Especially ones which could house the 3 drives etc. If aesthetics matter... i dunno if it matters for the heat. obviously yes the larger case will be better; but will it matter?

[IMG]http://img259.imageshack.us/img259/5656/1249132482331.jpg[/IMG]

---

### Post by CharlesA on 2010-01-10
Mine's not exactly a low-power server (or low noise), but if I upgrade to a new one I'm going to go with something like this here: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813500028&cm_re=itx_ion-_-13-500-028-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16813500028&cm_re=itx_ion-_-13-500-028-_-Product)

Altho, that sounds like the perfect board for a nice small HTPC.

---

### Post by The Real Dave on 2010-01-10
Not designed to be low power or noise, but is pretty close. Its just a typical PC case, fairly thick though, which deadens noise. It now has a 500Gb Seatgate 7200.12, which is a good bit noiser and hotter than the 320Gb Samsung Spinpoint F1s that it used have. Samsung in my experience are generally very quiet and cool, their newer drives are very good. 

My problem though is the 6Gb Quantum Fireball HDD that Ubuntu is installed on, the thing is damn loud :( The sever has a 1.7Ghz Pentium IV, with the CPU fan running at full speed, and yet, that's extremely quiet. I figure its the case.

I'm going to try to lag the inside of the case, and maybe that 6Gb HDD to try and kill the noise somewhat. Pics and Specs are [here]("http://linuxexpresso.wordpress.com/hardware/") and [here]("http://linuxexpresso.wordpress.com/2009/12/29/christmas/")

---

### Post by volkswagner on 2010-01-10
I have been happy with my [Intel Atom 330]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813121383") (dual core) based system.  With two sata and one pata, you can have 2-SATA HD's and one PATA or USB optical disk.  Or add a pci-sata card.  

The Ion based system mentioned above is better suited for GUI like HTPC but it is single core (Atom 230) making my vote for the Atom 330 better suited for server application.


Here is a [passive cooled variant]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813186184").

If you do go with fan cooled Atom, the fan is actually for the chipset, and heed the advice for a quiter fan and you'll be very happy.

Yes they are mini-itx, but as mentioned you can install in a compatible mATX, or ATX case for breathing room and hard disk bays.

---

### Post by vk7krj on 2010-01-12
Andrew, I run a fanless via epia mini-itx board (ln10000a) with 1gig of ram, 4, 1tb WD green drives for nas and a 320g for ubuntu 9.04 and my web pages. This is in a 2u rack box, no fans, virtually silent and no heat problems. It runs from 12 volts using a Pico power supply and takes around 30 watts, with some peaks at 35 watts or so on disk access (it's my media server). The 1tb drives are set to spin down after 15 minutes inactivity which helps with the power and noise- now the kids have left the media server spends most of it's time doing very little. But hey, it was fun building it and getting it going.  [quote=jobsonandrew;8635839]Hi,
I've got a low power low noise server at home which is doing great but I want something with a much higher capacity hd.. maybe 1.5 or 2 TB

---

### Post by BkkBonanza on 2010-01-12
@munky99999
Nice rack of mainboards! Google style.

I think these Atom based low-power boards are good for this type of application. I'm surprised that they don't use less power though. I think it's the chipset that is the problem because the CPU appears to be very low-power. I don't know if they've improved that yet but in the early Intel based atom boards they used older chipsets that were not low-power at all. 

I think of low power meaning 5-10 W, like my router. The early Atom boards were still 25-30 W. But those Intel Atom boards were quite cheap.

This looks like a nice board for a home server/firewall/router applications,
Atom 330 w/2 GBit LAN, 6 USB, and miniPCIe for wifi if desired,

[http://www.logicsupply.com/products/ms_9832](http://www.logicsupply.com/products/ms_9832)

---

### Post by Vegan on 2010-01-12
> **jobsonandrew said:**
> Hi,
I've got a low power low noise server at home which is doing great but I want something with a much higher capacity hd.. maybe 1.5 or 2 TB

CPU and memory wouldnt need to be too beefy, all it would be doing is seeving efilea and web pages as well as running teamspeak and other ubuntu server stuff

Anyone got a machine like this? I'd be interested in what hardware you have etc..

PS I have a nas drive but if I could use only ubuntu server I would

I use an old Pentium IV which has APCI throttling and if the 500 GB disk seems small, the USB ports can allow for 128 more disks.

---

### Post by cascade9 on 2010-01-12
munky99999- lovely pile computer you have there. What brand are those gold PSUs? You seem to like them a lot. ;) 

> **BkkBonaza said:**
> @munky99999
Nice rack of mainboards! Google style.

I think these Atom based low-power boards are good for this type of application. I'm surprised that they don't use less power though. I think it's the chipset that is the problem because the CPU appears to be very low-power. I don't know if they've improved that yet but in the early Intel based atom boards they used older chipsets that were not low-power at all. 

I think of low power meaning 5-10 W, like my router. The early Atom boards were still 25-30 W. But those Intel Atom boards were quite cheap.

It was the chipset. The 945GC used 22watts by itself! LOL

---

### Post by Queue29 on 2010-01-12
Another Atom 330N server here, using this barebones kit: 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16856167037](http://www.newegg.com/Product/Product.aspx?Item=N82E16856167037)

2 GB of RAM, Gigabit lan, and room for 2 SATA HDDs, so up to 4 Terabytes of storage I guess. There's also a CompactFlash card reader built in (internally) to the motherboard, which is perfect for keeping backups of config files.

The fan only kicks on under load, so it produces almost no heat and very little noise. 

For a headless personal web/utility server I couldn't think of anything better.

---

### Post by BkkBonanza on 2010-01-12
I've been reading around more on this today. It seems the mobile Core2Duo combos available are using about the same power as the Atoms - so I'm wondering what the gain is now. A Core2Duo mobile has got to perform better and it's so familiar for running Linux.

eg. on eBay Abit IL90MV mainboard $45 + Core2Duo T5250 1.5GHz $30 = $75. 
That's half the price of many of the Atom boards. Still add RAM either way.

I came across this interesting OLD post which talks about power usage with PicoPSU power module and 12V laptop style power brick. Idle power approx. 22W, same as my notebook roughly.
Though I don't know why they don't just make the mainboard take 12V power. 

[http://www.silentpcreview.com/forums/viewtopic.php?t=35472&highlight=core+solo](http://www.silentpcreview.com/forums/viewtopic.php?t=35472&highlight=core+solo)

Edit: CeleronM 1.6 GHz for $2.99 on eBay, uses same mainboard. ha!

---

### Post by jobsonandrew on 2010-01-12
Wow thanks for the replies and suggestions! :)

In the end I ordered:
Jetway J7F4K
--1.2GHz Via C7
--1GB RAM
--Fanless and uses around 7W power supposedly
Jetway JC113 Case
--27x30x6cm (ish.. very small and smart)
1x 2TB WD Green Power SATA
--yes... thats 2 thousand gig :P

so really the only sound it should make (fingers crossed) is the sound of a very quiet hard drive (25-29DBa)

The intention is to install Ubuntu Server 9.10 on it and then move to 10.04 LTS when that comes out

Peace!

---

### Post by BkkBonanza on 2010-01-12
That looks like a nice clean setup. Hope it works well for you. I like the dual GBit LAN. Only thing I wish they put more often on these small boards is the miniPCIe - it makes it easy to add wifi with a card that can do host (master) mode. Usually it's hard to find a USB dongle that does that.

---

### Post by Queue29 on 2010-01-12
Looks good. The Via seems to be 32 bit only, so remember to download 32 bit version of server (it defaults to 64 bit version).

---

### Post by barnex on 2010-01-13
Not really low-power, but quite low noise:

the most quiet parts:

case: Cooler Master HAF 932 
PSU: Cooler Master Silent Pro M700 700 Watt
HD: Western Digital 1TB SATA II 7200RPM 32MB Caviar **Green** (very silent and low power)

too bad this one is noisier than all the rest together:
GPU: MSI nVidia N295GTX 1792MB DDR3
(the GPU is used for CUDA simulations, i case you wondered why I'd put that in a server)

---

### Post by jobsonandrew on 2010-01-16
Hi all,
I got my server set up and its great :D

The drive is extremely quiet, have to put your ear to the case to really hear it.. even when its working its mega quiet

I'd recommend the WD Green Power drives to anyone, they seem brilliant

didnt bother connecting the 2 fans that thte case has, and it still seems to run cool

thanks again

---

### Post by cascade9 on 2010-01-16
If it was me, I would hook up at least 1 of the fans, if only to see how noisy it it (some fans are very quite, some of themare like a helicopter taking off). But I worry about overheating, which a lot of people dont.  

Congrats on your new machine ;) . Good luck and enjoy.

---

### Post by BkkBonanza on 2010-01-16
Have you taken any power use measurements? I'm curious what it draws when idle.

This thread got me researching and deciding to make myself a mini-itx server. I'm on a different path though. I'm going with the Gigabyte GA-6KIEH-RH board and a C2D T5450 CPU. I have the case and ordered the CPU, but haven't taken the leap on the board yet. The case is small and sweet. It only cost me $32 and it has 120W power built in with laptop style adapter. Very small footprint with lots of holes for air flow.

That board has all mini-PCIe, mini-PCI and PCI. The PCI is close to useless in such a small case but the mini-PCIe allows me to plug in my Atheros 9281 and set it up as a wifi access point too. Big deciding point was mini-PCIe on board with Dual Intel LAN. A lot of the boards have Realtek, which I don't like. Anyway, I've heard that Gigabyte makes good solid boards.

---

### Post by jobsonandrew on 2010-01-16
I havent taken any measurements for power usage, but jusdging by reviews of each component, I'd guess it draws around 20-25W?

if you want low power consumption you have to sacrifice on performance, but that means you also get less heat.. and luckily Ubuntu server is actually really light-weight.

I have Torrentflux-b4rt running but I've gone the extra few steps to get it working under lighttpd instead of Apache2 (huge and unecessary) and its using SQLite rather than mySQL (also huge and unecessary).

Also have teamspeak, postfix and samba working, and at the moment its only using 64MB RAM!!! and when bit-tornado stops running that memory usage will have a third cut off it.. marvelous!

oh by the way.. i had a bit of a panic.. i rebooted it via SSH and it refused to boot without a keyboard connected (!!!).. luckily there is a setting to ignore that in the BIOS, but I had to dig for it.. just a heads up in case you see the same thing

cheers

---

### Post by steven.jones on 2010-01-16
> **jobsonandrew said:**
> Hi,
I've got a low power low noise server at home which is doing great but I want something with a much higher capacity hd.. maybe 1.5 or 2 TB

CPU and memory wouldnt need to be too beefy, all it would be doing is seeving efilea and web pages as well as running teamspeak and other ubuntu server stuff

Anyone got a machine like this? I'd be interested in what hardware you have etc..

PS I have a nas drive but if I could use only ubuntu server I would

========

I am just going through this now.....its a balancing act...energy v performance v cost.

NAS boxes are really slow and over-priced...if you need more than 2 disks worth of capacity.

If its a "server".....just one drive?  Really need a Raid 1 pair IMHO.....trust me if its not just your data....my wife would kill me if I lost email or files!

;]

I am just re-building my house server, I used to run 9 x 10,000rpm scsi disks...at 18watts each, costly and noisey....

Now I will have 8 x pata disks at 8watts each but double the capacity (1tb), one half will do the samba/email/web and the other "half" (600gb) will be an iscsi mount for a small esxi box (hence the disk count).

After speed testing I find that the R5(4+1) 5400rpm 320gb pata's are little slower than the 10,000rpm R5(3+1) 146gb scsi's....but have twice the capacity, at least half the energy use and a lot quieter....

The 1.5tb disks ie the WD green ones are 6watts each, really good in terms of energy per gb and performance....I'd go with a pair, they are my next purchase I suspect...

iscsi, needs little cpu or ram, its all disk i/o, samba is different that will use CPU if you have a GB network and transfer large files you will notice...

I have a dual core 1.6ghz celeron and 4gb of ram, motherboard is an Asus P5K which is set to energy saving mode....the advantage of this board is the chassis fans are controlled by the m/board.

I also have a temp controller board this monitors 4 temp points and can control 4 fan speeds....all to minimalise energy cost.


regards

---

### Post by lisati on 2010-01-16
Hmmmm.... I must give a bit of thought to upgrades for the machine I'm currently using as a server. It's not too noisy - my old desktop (useful as a backup machine for my web site) is definitely old, tired and noisy!

---

### Post by steven.jones on 2010-01-16
Another good posibility is an atom based notebook like the asus Eee or the Aspire unit....add on usb disks...

---

### Post by BkkBonanza on 2010-01-17
> **steven.jones said:**
> Another good posibility is an atom based notebook like the asus Eee or the Aspire unit....add on usb disks...

While that may work as a temporary measure it lacks one critical thing for me: a second LAN port. I suppose you could add a USB-LAN converter but that's a little wonky. One of my main goals is to replace my Linksys router with a higher performance solution. I use the router to firewall me against other users in my building and I often use it to transfer files from outside to me. With the Linksys that tops out around 3.5 MB/s. So my most immediate goal is a gateway that can handle gigabit speeds and isn't tied down by the gateway cpu. The Linksys routers also get hamstrung by too many connections for P2P apps which I also find limiting.

I'm not too excited about building a fancy NAS box. I'll likely just hang a couple USB drives off it anyway and it will do me. This GA motherboard has a SATA RAID controller and 5 ports so if I wanted I could move it into a nice hot-swap RAID enclosure, but that's not the plan right now.

For anyone interested in this I made this handy CPU chart to help me decide which way to go. It doesn't cover the C7 but I know it's in the same ballpark as the Atoms. It's still very incomplete but I was trying to link power use with CPU performance. 
```

CPU			Skt	GHz	Score	TDP	Idle 	Load
AMD Geode NX1750	-	1.4	282	14W		
Atom N270		-	1.6	304	2.5W		
Atom 230		-	1.6	313	4W	14W/39W	19W/41W
Pentium M 1400		478	1.4	318	10W		
P4 2.4			478	2.4	322	60W		
Celeron 220		479	1.2	341	19W		
Celeron M 420		M	1.6	404	27W	24W	29W
P4 2.8			478	2.8	415	68W	83W	128W
Celeron M 530		P	1.7	435	27W		
P4 3.0			478	3.0	483	70W		
Celeron M 550		P	2.0	538	31W		
Atom 330		-	1.6	623	8W	25W/41W	28W/44W
Atom D510		-	1.6	660	13W	21W	26W
Core Duo T2300		478,v	1.6	760	31W		
Core 2 Duo T5200	M	1.6	826	34W		
Core Duo T2350		M	1.9	844	31W		
Core 2 Duo T5300	M	1.7	876	34W		
Core Solo T1400		478	1.8	898	27W	20W	26W
Core Duo T2600		478,v	2.2	902	31W	22W	37W
Core 2 Duo T5500	M,v	1.7	910	35W		
Core Duo T2500		478,v	2.0	912	31W		
Core Duo T2450		478	2.0	916	31W		
Core 2 Duo T5450	P	1.6	930	35W		
Core 2 Duo T7100	P,v	1.8	944	35W		
Core 2 Duo T5600	M,v	1.8	997	34W		
Core 2 Duo T7250	P,v	2.0	1086	35W		
Core 2 Duo T5750	P	2.0	1098	35W		
Core 2 Duo T7300	P,v	2.0	1103	35W		
Core 2 Duo T5800	478	2.0	1113	35W		
Core 2 Duo T7200	M,v	2.0	1130	34W		
Core 2 Duo E7300	775	2.7	1791	65W		
Core i5 750		1156,v	2.7	4206	95W		

```
I just compiled this from other sources on the web. If you want a openoffice worksheet of this just let me know.
Or if you have idle/load figures to add I'd be interested.

Notes: socket 478, 479, M and P are all very similar. P being the latest variant.
The Atom has two power values, one for the old chipset and one for the EEEBox and Ions that use a low power chipset. The desktop cpus at the end are just for comparison. The "v" indicator means has cpu virtualization support. The TDP is from spec sheets, whereas the idle/load values are always from real world tests on a board. These were usually taken from reviews at anandtech, toms hardware or reported on forums by users.

---

