---
title: "Input on building a server"
date: 2009-11-01
forum: Server Platforms
---

### Post by p2ranger on 2009-11-01
I am wanting to build a little server for my home. It's main use will be a file and print server. I've decided to make this a little hobby type project. What I've come up with, I'm not sure will work and would like some input on. I want to use Ubuntu 9.10 server (Linux) as my OS. I want to use two drives inside in a RAID array to prevent data loss. I've read that Linux will handle raid as the system I'm looking at doesn't do hardware RAID

I found this little barebones system on Newegg:
Foxconn R10-S4
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856119012](http://www.newegg.com/Product/Product.aspx?Item=N82E16856119012)

It comes with 1X 3.5 internal bay, 1X 3.5 external bay, 1X 5.25 external bay, 2x SATA connectors, 1X PCI slot, integrated sound, video, NIC.  One reviewer spoke of the 3.5 external bay as "an undersized external 3.5" bay for installing a usb card reader". Not sure if this bay will accommodate other things or not.

I'm still new to Linux and am still trying to wrap my head around how the file system works (and have never attempted anything with RAID before). I was thinking about adding a third hard drive to use for booting and keeping the system on while keeping the two other drives for just keeping the data I want on the network. The idea being that if I need to move this data to another system, I hope that means that I could just pull these drives out and put them in something else.

I guess one question to ask, is it necessary to keep a third drive separate just to have the Linux system on and separte from my data I want that will be on a RAID. If so, will I be able to add a third drive to this. Whether that be buying a PCI card with either an SATA or IDE interface on it to run the third drive which would have the system on it, or rigging some kind of a memory card reader device inside with say an SD card on it and the system on that. Will this system only boot on the two included SATA connectors it comes with? I've read where people have been able to put two drives in and install Linux from a thumb drive, so that tells me you can boot off the USB port anyway.

I'm hesitant to install my OS to a thumbdrive as I don't want it getting knocked off accidentally and more so, I believe there isn't much life expectancy with that much read/write on a thumbdrive.

I want this to be able to sit in a room and never need to be touched again for weeks on end.

Has anyone else had experience with this Foxconn box and if so what is your setup and how has it behaved?

Am I over analyzing all of this?

Thanks for your help

Jason

---

### Post by shaggy999 on 2009-11-01
I wouldn't say you're over-analyzing this. I spend a lot of time and thoroughly check things out whenever I invest in something.

I haven't used that barebones kit, but I have used Foxconn motherboards and they are alright. They are not my first choice if I'm building a high-performance rig, but for budget builds I consider them worthy contenders.

I am also in the market right now for a mini server build and I'm looking at doing something very similar to what you're doing. In fact, I am looking at building an atom 330-based system using this board right here:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813182205](http://www.newegg.com/Product/Product.aspx?Item=N82E16813182205)

It's a flexatx board, which is like the server equivalent of mini itx (It uses a subset of the microatx standard so any microatx-compatable case and it's only slightly larger than mini-itx.

First-off (I'm typing with a surgical wrap on my hand so my typing is funny, sorry if I mispell anything) it's not strictly necessary to to put the OS on a seperate drive, but I think there's some good reasons to do so. First off you need to decide if you're doing hardware or software-based raid. I'm assuming software because there's no mention of it on the newegg site and I would be suprised to find raid support in a cheap box like that. What you would do I guess would be to create two identical-sized partitions on each of the drives and use software raid to raid the partitions, not the physical drives.

Personally, I would put the OS on a third drive and I plan to do exactly that with my system. Secondly, that board has exactly one PCI slot and that's the basic, old, currently being phased out PCI. It's SLOW. You're going to hit a bottleneck if you stick a sata expansion board in there and place any decent sata drive on it.

Here's the sad part: There is not a single Mini-ITX board w/ a PCI-Express slot. Not one. How stupid is that? That's how I came across that flex-atx board and from the specs I *really* like it. It's got atom 330, *TWO* PCI-Express slots, also a plain PCI slot, *FOUR* SATA ports and it supports hardware-based RAID-0/1/10/5. *TWO* GIG-E nics, and a PATA port. This board is built to handle old technology (IDE devices, PCI cards) while also supporting future devices (PCI-Express cards and up to 4 SATA drives).

There's only two marks against it: 1) It's pricey and 2) no sound ports. So if you want to do a music server, this isn't it. But for most server functions I think this is fine.

Personally, what I'm gonna do is put two big drives on two sata ports and software raid them, then use a usb key for the os. A PCI-Express wireless N card will be going into one of the PCI-Express slots and there is more room to upgrade later as necessary.

Oh yeah, that reminds me. You can get some teeny tiny usb sticks that don't stick out very far at all and unless you're doing a newsgroup or mail server you're really not going to be writing a lot of files to the usb stick.

You are looking at a higher price point with the board I mentioned (board + case is probably about $200 vs $120 for the barebones kit) but I think it's worth it.

If I were using the barebones you mentioned I would put the OS on fingernail sized thumbdrive that I would plug into the back of the system and do software raid on the two internal drives.

Good luck on your build.

---

### Post by shaggy999 on 2009-11-01
I forgot to add, if you are concerned over energy efficiency you might want to wait a bit as intel is just now rolling out mini-itx atom-based boards using the MOBILE 945 chipset which actually makes a HUGE difference in the power draw on atom-based boards (as much as 20 watts). Hopefully other vendors will follow suit.

---

### Post by Lars Noodén on 2009-11-02
You could get a solid-state drive (SSD) and use that.  They're not that big, and though ubuntu is big, it will still fit even on a small one.  These do the job and do fit in the pci slot.  

Booting off of USB is also doable.  If you're worried about the thumbdrive getting knocked off, you can put it inside the case (and fasten it with non-conducting tie-wraps, not wire or adhesive tape)  There are usually extra USB connections on the motherboard itself and it is just a matter of plugging a cable.  

You can see a *round*, grey extra USB cable here marked by the yellow arrow in a system that happens to boot off of Compact flash:
[http://www-personal.umich.edu/~lars/images/usb-cable.png](http://www-personal.umich.edu/~lars/images/usb-cable.png)

In that picture, the extra USB connection goes to the outside, but it could just as easily have stayed inside the box.

You can see a P4 junker that boots off of a thumb drive (thumb drive not visible) with the regular drives set up to use as raid 10 for data:
[http://www-personal.umich.edu/~lars/images/raid-10.png](http://www-personal.umich.edu/~lars/images/raid-10.png)

So it can be done.  

There are also starting to be more arm-based systems around, so those are another (IMHO better) low-power option.

---

### Post by NickJones on 2009-11-02
I recently got a system for that exact same purpous. I purchased a $30 laptop with a broken screen, I took off the screen, installed Ubuntu, set up VNC then shoved it under the table next to the router, I VNC-ed into it, set up Samba, and hooked up a external 1TB drive, the whole setup cost me under $100, and now I have a file server that I automatically back up to every night. It works like a charm.
Nick

---

### Post by snowpine on 2009-11-02
Hi P2ranger, I purchased a Foxconn R10-S4 about 2 weeks ago for use as an extra web-surfing machine. It is a decent product for the price, but I have 2 words of advice for you:

1. 2 drives is the max; they really should not be advertising this as having a 3rd drive bay.
2. 9.10 server might run ok, but 9.10 desktop is not compatible with the graphics card. If you want to run a GUI instead of a server, stick with 9.04 (as I have done).

If having lots of hard drives is your #1 priority, you can get an old tower computer for under $100 that will have all the drive bays you need.

Good luck!

---

### Post by p2ranger on 2009-11-03
Thanks for all of your input. I really appreciate having someone else to bounce my ideas off of. I'm going to use a USB key to hold the OS on and find a way to make sure that stays inside somehow. I'm assuming you can use two USB drives at once when I'm installing. One empty one to install on to and another one to install from?

Now I'm looking into the hard drives. Been reading a lot about them and still not sure. It will be two identical SATA drives using RAID1 controlled by Linux. 

Can't really settle on a size/brand/model. I'm looking at 500GB to 1TB. Trying to figure out the $/MB ratios, but can't quite nail down the model and maker I want. There will be two identical drives. I know the WD greens are more power efficient, run cooler, etc. I'm guessing since they are cooler they will have more longevity (maybe?). This will be good as the box will be small and will be turned on all the time. I've read that there might be issues with WD greens being used in RAID0, but does it matter with RAID1? The WD Blacks have a 5 yr warranty as opposed to 3 yr on the greens. Are they made better or have more longevity? The Blacks run hotter, and I don't know that I need that high end of  drive for what I'm using it for. WD has left a bad taste in my mouth with a couple of previous hard drives that died on me. One was an internal drive after a couple of years and the other was one of those crappy My Book external drives, didn't last two years. So I'm thinking about checking out Seagate, but not sure if they are any more reliable.

System use: Storing files, trying to go paperless for the home (bills, bank statements, my work certs, documents, etc.) Keeping all of mine and my wife's music and photos all in one central place. Performance is not going to be a priority. Reliability and longevity are my concern. I'm hoping this will last for several years.

Thanks

Jason

---

### Post by Lars Noodén on 2009-11-05
> **p2ranger said:**
> 
System use: Storing files, trying to go paperless for the home (bills, bank statements, my work certs, documents, etc.) Keeping all of mine and my wife's music and photos all in one central place. Performance is not going to be a priority. Reliability and longevity are my concern. I'm hoping this will last for several years.


RAID1 will help protect you from the failure of a single drive.  
Same for net-based backups that don't utilize removable media.  
  [http://news.bbc.co.uk/2/hi/technology/8049780.stm](http://news.bbc.co.uk/2/hi/technology/8049780.stm)

You'll want two or three removable devices to use for off-site storage of the back ups.  A reason for more than one is that during the time the backup is being updated, or plugged in, it is active and not a back up.  
Encryption is a good idea:
 [http://www.internetnews.com/storage/article.php/3486036](http://www.internetnews.com/storage/article.php/3486036)

Lesson: learn from the mistakes of others.

If privacy or longevity is concerned, then an 'air gap' can be a good idea.  

If its going to be running more or less continuously, then also look at what can save electricity, especially during peak hours.  Stuff like audio and video chipsets use power even though they are not needed on a server.  Unfortunately the trend is to jam more on a board 'just-in-case', so (to pick a random example, it's not an endorsement or a slam) the 7260 uses more power than the 7200:
[http://www.embeddedarm.com/products/arm-sbc.php](http://www.embeddedarm.com/products/arm-sbc.php)

Here are some x86 comparisons:
[http://www.tomshardware.com/reviews/amd-power-cpu,1925.html](http://www.tomshardware.com/reviews/amd-power-cpu,1925.html)


If you have spare computer with a serial connection and you can get a serial cable, then you can practice installing over serial line.  If you're comfortable managing the installation that way and managing the maintenance either over ssh or over serial, then you can eliminate video and other unnecessary power hogs.

---

### Post by p2ranger on 2009-11-05
Good points, thanks!

Jason

---

### Post by Pelsia on 2009-11-06
Since the server can easily be run from just a command line (not a terminal screen), the graphics card is pretty much irrelevant for the console itself.  If you want to use a gui I'd recommend using the remote desktop to logon to the server to save on resources.  

Storage is probably going to become your biggest problem in the long run, even if you put a TB drive in there now its eventually going to fill up.  1 TB+ drives tend to build up heat, so you should be really mindful of cooling as several friends of mine that dumped all their data onto them have ended up loosing all their data when the heads crashed. 

If the pci slot is either a 64 bit or PCI-X slot you have some further options as far as storage goes down the road.  You can get a *real* RAID card for $70-$100 (and it just goes up from there) that has its own memory and cpu onboard; a real *hardware* RAID card is the only reliable way to do a RAID setup.  Most cards in that range will be 4 to 8 channels, plenty to do a good RAID-5 setup.  Personally I wouldn't use anything larger than a 500gb disk in an array for reliability and heat reasons, plus some part of the computer (usually the bios, but can be the kernel depending on the OS) starts to have problems when you try to hookup an array over 2.4 TB.

If you can fit the card in, its not too hard to build your own SAN, depending on who much you want to expend it can get a little pricey.  Either find a case that can mount 6+ drives, or be able to hold a backplane that can accomodate 5 disks (this may require modifying the case).  Put a power supply into the case and bridge the atx connector so it will run on its own.  Then just get some long SATA cables to go from the case to the server and you've got potentially 5 TB worth of fault tolerant extra space.  This is *a lot cheaper* than trying to find even a blank chasis that has the disk trays (built in backplane).

---

