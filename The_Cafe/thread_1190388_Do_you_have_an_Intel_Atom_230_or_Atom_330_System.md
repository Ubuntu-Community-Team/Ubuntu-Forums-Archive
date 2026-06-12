---
title: "Do you have an Intel Atom 230 or Atom 330 System?"
date: 2009-06-17
forum: The Cafe
---

### Post by learningcurb on 2009-06-17
Hi, I've been thinking about getting one of these ultra cheap Intel Atom systems as a web browsing / email terminal.  If it can play youtube videos that's great, but if it can't and it's a few bucks cheaper that's also fine (it would be one less distraction :)).

I'm also considering getting another unit that is capable of displaying Youtube videos or DVD content on a small 20" TV.  I'm aware that there's the Nvidia Ion platform, but they seem a bit expensive ($300 or more) I'm shooting for a sub-$200-$150 platform if possible. 

I was wondering if anyone has tried these units or similiar ones with Ubuntu, and what the experience is like.  

[Foxconn Atom 230]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856119011")
[Foxconn Atom 330 (dual core)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856119012")
[MSI Atom 330]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856167037")
[Intel BOXD945GCLF Intel Atom processor 230]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813121342") only $65, which is pretty amazing.

oops, the second "Intel Atom 230 with Nvidia Ion chipset" choice is supposed to be Intel Atom 330. :\

---

### Post by gn2 on 2009-06-17
Don't have one, but am currently considering purchase of the Atom + Nvidia Ion [Acer Revo]("http://www.play.com/PC/PCs/4-/9606798/Acer-Aspire-Revo-Intel-Atom-N230-1-6GHz-1GB-8GB-SSD-Linux-Desktop-PC/Product.html") (Hornet in the US)

---

### Post by Collin White on 2009-06-17
I have a System76 Meerkat that I'm quite happy with.

---

### Post by Sublime Porte on 2009-06-17
I don't have one of those desktop systems, but I do have an Eee1000H which has the same CPU and chipset I think. Of course it runs Youtube videos fine (as pretty much any x86 pc you buy today would). Atom systems are perfect for internet-based computing.

---

### Post by cariboo on 2009-06-17
I have mine w/945 chipset connected to a 32" HDTV LCD, it plays avi's full screen quite nicely, I would suggest using the video drivers from [this ppa]("https://launchpad.net/~intel-gfx-testing/+archive/ppa").

---

### Post by learningcurb on 2009-06-17
> **cariboo907 said:**
> I have mine w/945 chipset connected to a 32" HDTV LCD, it plays avi's full screen quite nicely, I would suggest using the video drivers from [this ppa]("https://launchpad.net/~intel-gfx-testing/+archive/ppa").

Neat, how high a resolution can you push the AVI files before playback becomes impaired?  And what resolution does your HDTV display? Also did for your 945, did you get the BOXD945GCLF2 or the BOXD945GCLF2D?

Also, I'm trying to figure out the difference between the two. Perhaps one of them has S Video out and the other does not?  Newegg's data entry on the specs is somewhat spotty and [http://www.intel.com/support/motherboards/desktop/d945gclf2/sb/CS-029521.htm](http://www.intel.com/support/motherboards/desktop/d945gclf2/sb/CS-029521.htm) and [http://www.intel.com/support/motherboards/desktop/d945gclf2/sb/CS-029525.htm](http://www.intel.com/support/motherboards/desktop/d945gclf2/sb/CS-029525.htm) do not seem to provide much information either.

Another interesting choice is are the JetWay motherboards at Newegg.  They have a line of mobos that use VIA processors instead of the Intel Atoms.  They're only slightly cheaper but some of them support up the 4GB of RAM or dual gigabit ethernet, which might make them an interesting choice for NAS box.  VIA chipsets may also be more energy efficient than the Intel 945 for some sort of server that you will leave running 24/7.  I have a hunch the Intel 945 is probably the more widely supported choice for desktop or HTPC use however.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813121359](http://www.newegg.com/Product/Product.aspx?Item=N82E16813121359) Intel BOXD945GCLFD 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813121383](http://www.newegg.com/Product/Product.aspx?Item=N82E16813121383) Intel BOXD945GCLF 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813153144](http://www.newegg.com/Product/Product.aspx?Item=N82E16813153144) JetWay JATOM-GM1-330-LF Intel Atom 330

---

### Post by kerry_s on 2009-06-18
i have the foxconn with the atom 330 on the way. :D

---

### Post by SLEEPER_V on 2009-06-18
my dell mini 9 shows up as a dual core 270

---

### Post by learningcurb on 2009-06-18
> **kerry_s said:**
> i have the foxconn with the atom 330 on the way. :D

neat, any idea what motherboard is inside?

---

### Post by kerry_s on 2009-06-18
> **learningcurb said:**
> neat, any idea what motherboard is inside?

i have no idea, the specs are here: [http://www.newegg.com/Product/Product.aspx?Item=N82E16856119012](http://www.newegg.com/Product/Product.aspx?Item=N82E16856119012)

i chose that 1 cause you can use any os on it, it's x86 & 64bit. linux & win compatible, i hear it can do mac "hackintosh", but i doubt i'll ever try that, rather have good ol debian. :D

---

### Post by 3rdalbum on 2009-06-18
I have an Atom-based home-built home server and an Atom-based netbook - the server reports as an Atom 230, and I think the netbook uses the same.

The netbook regularly plays h.264 videos at 640x480 which is my TV's resolution. Curiously enough, the netbook is very sluggish for web browsing but the server seems much faster. Ion is overkill for playing Youtube or DVD quality video on a 20 inch screen - Intel graphics can handle this, even with the problems introduced by Ubuntu 9.04. However, if you will be playing HD content, Ion is a necessity due to its support for VDPAU.

---

### Post by ssam on 2009-06-18
i was looking at them for a low power machine (to replace my ageing via epia MII6000). one thing i found interesting is that the only the power consumption of the CPU gets quoted by intel, but actually the northbridge chip is far more power hungry.

if you look at a photo of a atom 230/330 board (eg [http://www.intel.com/Products/Desktop/Motherboards/D945GCLF/D945GCLF-overview.htm](http://www.intel.com/Products/Desktop/Motherboards/D945GCLF/D945GCLF-overview.htm) ) you will see 2 main heat sinks, the little one is the CPU, the big one with the fan is the northbridge (you can verify this in the manual).

if you want low power, you need to get a via board, or wait for the next batch of atoms.

the is a table of mini-itx boards and power consumption at [http://mini-itx.com/store/?c=2](http://mini-itx.com/store/?c=2)

---

### Post by cariboo on 2009-06-19
> **learningcurb said:**
> Neat, how high a resolution can you push the AVI files before playback becomes impaired?  And what resolution does your HDTV display? Also did for your 945, did you get the BOXD945GCLF2 or the BOXD945GCLF2D?

Also, I'm trying to figure out the difference between the two. Perhaps one of them has S Video out and the other does not?  Newegg's data entry on the specs is somewhat spotty and [http://www.intel.com/support/motherboards/desktop/d945gclf2/sb/CS-029521.htm](http://www.intel.com/support/motherboards/desktop/d945gclf2/sb/CS-029521.htm) and [http://www.intel.com/support/motherboards/desktop/d945gclf2/sb/CS-029525.htm](http://www.intel.com/support/motherboards/desktop/d945gclf2/sb/CS-029525.htm) do not seem to provide much information either.

Another interesting choice is are the JetWay motherboards at Newegg.  They have a line of mobos that use VIA processors instead of the Intel Atoms.  They're only slightly cheaper but some of them support up the 4GB of RAM or dual gigabit ethernet, which might make them an interesting choice for NAS box.  VIA chipsets may also be more energy efficient than the Intel 945 for some sort of server that you will leave running 24/7.  I have a hunch the Intel 945 is probably the more widely supported choice for desktop or HTPC use however.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813121359](http://www.newegg.com/Product/Product.aspx?Item=N82E16813121359) Intel BOXD945GCLFD 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813121383](http://www.newegg.com/Product/Product.aspx?Item=N82E16813121383) Intel BOXD945GCLF 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813153144](http://www.newegg.com/Product/Product.aspx?Item=N82E16813153144) JetWay JATOM-GM1-330-LF Intel Atom 330

I have a D945GCLF with 1GB ram, 160GB SATA hard drive and Samsung slim DVD R/w in a InWin BM639 case. I use a D-Link WUA-1340 usb wirelss device to connect to the network. The HDTV is a Samsung LN-T3242H, I use the VGA input so the resolution is 1360X768, Watching recorded HDTV that I get from my brother-in-law the quality is not as good as the ouput I get from my Bell Expressvu HD DVR.

The tv does 720p, but I normally watch it @ 1080i. DVD from component output is just horrible, DVD playback on the pc is much better subjectively. I plan on getting a blu-ray dvd player later on this year as I just can't watch dvd using the current dvd player.

The audio is run through a Techics reciever that I sold used to a friend 10 years ago, he gave it back just before he moved out of town last year. It is due to be replaced later on this year too. The speakers are Paisley Bookshelf, that I've had since the early 80's. If I could ever find a bookshelf speaker that sounds as good I would replace them.

---

### Post by learningcurb on 2009-06-19
Ah cool, thanks for the tips.  I glad to know the Atom can playback at 1360X768 nicely in case I want to upgrade my TV in the future.

> **cariboo907 said:**
> 
The tv does 720p, but I normally watch it @ 1080i. DVD from component output is just horrible, DVD playback on the pc is much better subjectively. I plan on getting a blu-ray dvd player later on this year as I just can't watch dvd using the current dvd player.


How did you get the S-video output working? I read somewhere on the forums (I can't seem to find the page) that people were having trouble with the S-video output on that particular board. It's only a $5 premium for the board that has the S-video out though, so it might be worth it just to try it out.

Also, I just read [http://www.tomshardware.com/reviews/Atom-Athlon-Efficient,1997-14.html](http://www.tomshardware.com/reviews/Atom-Athlon-Efficient,1997-14.html) which points towards a microATX Athlon 64 2000+ as a possible contender with the Atom 330 since it runs cooler, uses slightly less power and outperforms it.  However it does require the larger microATX form factor compared to miniITX.

---

### Post by cariboo on 2009-06-19
I don't use [S-video]("http://en.wikipedia.org/wiki/S-video") , as it is only slightly better than [composite video]("http://en.wikipedia.org/wiki/Composite_video"). I was talking about [component video]("http://en.wikipedia.org/wiki/Component_video") which makes dvd's virtually unwatchable on an HD LCD TV. I connect to the tv using the builtin vga connector.

---

### Post by kerry_s on 2009-06-23
woohoo! i just got my foxconn r10-s4 today.
i just got it put together about 5 minutes ago, i stuck in a 250gb sata hd(pulled from my external enclosure) & i only had 512mb ram(i had 4 of these laying around) so i used that, i'll get a 2 gig stick later when it's on sale. i don't have a sata cd, so i'll have to get that later to.
i'm now installing debian from a usb thumb drive(i only have my 64mb stick, the rest are out on loan), cause i'm just dying to get this thing up an running. i just can't wait to see what it can do & how the dual core atom 330 works.

this is my first ever new computer, all the computers i ever had were past on to me. feels good. :D

---

### Post by boon4376 on 2009-07-13
I just ordered the Atom 230 foxconn barebones from newegg.. I'm building an intranet webserver for a client, and It just needs to be a REALLY cheap, preferably low power system for a PHP based electronic records management program.

The cheapest system i could find was this, I got the barebones for $95 with free shipping so it was a great deal, the cheapest AMD (equivalent components) system i could put together was $130 + shipping costs.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856119011](http://www.newegg.com/Product/Product.aspx?Item=N82E16856119011)
Im still amazed, $95 was a steal for mobo, case, processor, power supply, + 2 SATA cables

And im putting it together today, Im worried that it will be underpowered, although all it is really doing is loading 60kb tiff files and performing the occasional image rotate with imagemagick so I think it should be fine, but im still nervous as I wont have time to return it or get a more powerful system before we install it into our clients network. (i'd have to give them my home media center PC i think LOL)

I wish I could find a benchmark that compared it to say an AMD Athlon 64 3200+ (my ubuntu developement computer), but the only benchmarks I find compare it against other NEW lower power processors. I really like to see how these things perform against older mainstream processors.

---

### Post by kerry_s on 2009-07-13
i think you should have paid a little more & got the duel core:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856119012](http://www.newegg.com/Product/Product.aspx?Item=N82E16856119012)

which is the 1 i got, runs perfectly, love this thing. does multi-tasking without a hickup.

---

### Post by khelben1979 on 2009-07-13
I have never seen an atom processor in any system and from what I have read about them, I prefer not to either (not yet any way).

---

### Post by cariboo on 2009-07-13
I updated the bios last week and connected the fans to the right connectors, and now the system is quieter than my satellite receiver/dvr.

---

### Post by CheresZabor on 2009-07-16
I've been running the Intel BOXD945GCLF2 for the past two months with 2GB of ram as a SMB server. 

Installed Ubuntu Server w/ Webmin and i can say it works very well

---

### Post by Gruic on 2010-06-24
Greetings!  I have the Foxconn super-mini Atom 330 w/ nvidia ION system that I had bought to use as an xbmc htpc system.  I installed the xbmc live system, which is based on ubuntu 9.10 and I am sad to say that ubuntu has knowledge of the wireless card or the sound card.  The sound card is an Nvidia MCP7A rev b1 chipset, but the pci-id is not in the kernel's database yet so alsa doesn't know how to initialize it.  I will say though that playback of H.264 / MKV is excellent.  I complete dig XBMC and will do whatever it takes to make it run on this hardware.  Going to try 10.04 next to see if there are updated drivers.  If not, it looks like I'm going to grab the latest linux kernel to see if drivers exist there.  It's going to suck making a custom kernel because then I have to recompile the nvidia video drivers as well.  If anyone else has gotten this working, please let me know.  

 Gruic

   Gruic @ duskwood D0T 0rG

---

### Post by kamaboko on 2010-06-24
You didn't mention the N270.  That's in my Asus 1000HA.  Love it.

---

