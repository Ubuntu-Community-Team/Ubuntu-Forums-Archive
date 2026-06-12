---
title: "Building HTPC.. Should I build Server for movies too?"
date: 2010-04-04
forum: The Cafe
---

### Post by Kdar on 2010-04-04
I plan to build HTPC, I post about it few month ago.

Initially I was thinking to put inside a large 1TB or 2TB 3.5" HardDrive (inside of my HTPC)... but now I am kind of not sure.

Should I get a small, 2.5" harddrive for Linux and XBMC? (for HTPC)

And then build a server for storing all movies, music..etc (have it in garage somewhere).

But I never built a server before and not sure how it will work. Will I able to stream from that server HD movies to my HTPC?

If I will have a server, my HTPC doesn't really needs a lot of space, right? Just enough for OS files, XBMC and other applications, if any.

---

### Post by Regenweald on 2010-04-04
I had thought of building one and using Opensolaris as a base. OSol has the moovidia media manager and ZFS. Basically, I'd make the server and HTPC in one using moovidia as the front end and with zfs I could stripe a few terabyte drives as one device. Osol also has the added benefit of literal one-click backups and a self healing fs. Very stable filesystem, easy backups, Great front end.

---

### Post by srt4play on 2010-04-04
Yes! There are many advantages to a centralized storage server, the biggest in htpc setups in my opinion is you can have the freedom to expand as much as you want with a huge case lots of hard drives, etc. All that noise and heat is kept out of the way and htpc clients can be kept small and quiet as they should be.

---

### Post by Cam42 on 2010-04-04
If you've got the cash, go for it. Definitely worth it.

---

### Post by northwestuntu on 2010-04-04
get a few 1.5tb best bang for your buck and use xbmc.  i wouldn't worry about using a server just make sure you get a case with some room inside and lots of sata ports.  it's all about the case and video card when it comes to noise.  my case is really quiet and my video card nvidia gt210 is fanless so no noise there and make sure you get low powered hard drives.  5800rpm.

---

### Post by Kdar on 2010-04-04
What do you think I would need for this? What kind of parts (other than HadDrive :p )... what kind of speed for CPU.. etc

So XBMC can automatically connect to that server (assuming its on) and browse through all the files on there (movies)?

I also like the idea of center server since I can also use it from my desktop, if I will want to watch movies from there.

---

### Post by cariboo on 2010-04-04
I'm currently using XBMC for my media center, and a seperate server for storing media files. I'm currently using 750Gib of 2Tib, so I still have lots of room for expansion. 

My media center pc has a 160Gib HD, but all that's on it is the os. One of these days I'll install a much smaller drive.

---

### Post by Kdar on 2010-04-04
> **cariboo907 said:**
> I'm currently using XBMC for my media center, and a seperate server for storing media files. I'm currently using 750Gib of 2Tib, so I still have lots of room for expansion. 

My media center pc has a 160Gib HD, but all that's on it is the os. One of these days I'll install a much smaller drive.

Could you post the specs for your Server? I am thinking to do something like you too.

If I remember correctly you use Atom for your HTPC, right?

Your XBMC can automatically connect to that server and you can browse all movies and what not on there?

---

### Post by northwestuntu on 2010-04-04
i would go with a low powered cpu 45 nm.  make sure you get a nvidia card.  then you can use vdpau.  2 gigs of ram is enough xbmc runs better with the 32bit version.  xbmc does a great job of connecting to servers.  guess it's the way your gonna have it setup in your place, but i don't see a need for a server myself.

---

### Post by Cam42 on 2010-04-04
I'd go with an Atom for the HTPC, something nicer for the server. Maybe a Solid State drive in the HTPC, for quiet and quick boots?

---

### Post by cariboo on 2010-04-04
> **Kdar said:**
> Could you post the specs for your Server? I am thinking to do something like you too.

If I remember correctly you use Atom for your HTPC, right?

Your XBMC can automatically connect to that server and you can browse all movies and what not on there?

I use nfs to mount the movie directory from my server, it is setup in fstab, so it mounts on boot.

I just had to rebuild my server as the motherboard that came from the garbage dump finally died :(. the new specs are:

[list]
[*] MSI [G31M3-F V2]("http://us.msi.com/index.php?func=proddesc&maincat_no=1&cat2_no=170&prod_no=1573#")
[*] Intel [E5400]("http://ark.intel.com/Product.aspx?id=40478")
[*] 2X Kingston 1Gb PC5400 ram
[*] 1 WD 320Gb PATA Hard Drive
[*] 1 Maxtor 120Gb PATA Hard Drive
[*] 2X Seagate 400Gb SATA Hard Drives
[*] 1 Seagate 750Gb SATA Hard Drive
[*] Coolermaster eXtreme Power Plus 500W power supply.
[*] junk case, that has enough room for everything.
[/list]

My media center pc is atom powered, and runs [XBMC Live]("http://wiki.xbmc.org/?title=XBMC_Live") really well. I use a Logitech wireless keyboard and mouse to control it.

---

### Post by Kdar on 2010-04-04
> **Cam42 said:**
> I'd go with an Atom for the HTPC, something nicer for the server. Maybe a Solid State drive in the HTPC, for quiet and quick boots?

Yes. Thats what I think to do.

Initially I was thinking to use Atom+Ion build, but I was thinking to use a big capacity hard-drive. 

But recently I was thinking to make that HTPC really compact, use small hard-drive, possibly SSD, like you said. Hide it somewhere behind TV, maybe attach it to the wall. And to use Server with it in garage.

I was also thinking to wire my house with Cat5, so maybe I can do it all as one project. Make Ethernet plugs in my computer office, in tv room and move all routers with server to garage.

---

### Post by Cam42 on 2010-04-04
Cat5 wiring would be a great idea as well.

---

### Post by Kdar on 2010-04-04
> **cariboo907 said:**
> I use nfs to mount the movie directory from my server, it is setup in fstab, so it mounts on boot.

I just had to rebuild my server as the motherboard that came from the garbage dump finally died :(. the new specs are:

[list]
[*] MSI [G31M3-F V2]("http://us.msi.com/index.php?func=proddesc&maincat_no=1&cat2_no=170&prod_no=1573#")
[*] Intel [E5400]("http://ark.intel.com/Product.aspx?id=40478")
[*] 2X Kingston 1Gb PC5400 ram
[*] 1 WD 320Gb PATA Hard Drive
[*] 1 Maxtor 120Gb PATA Hard Drive
[*] 2X Seagate 400Gb SATA Hard Drives
[*] 1 Seagate 750Gb SATA Hard Drive
[*] Coolermaster eXtreme Power Plus 500W power supply.
[*] junk case, that has enough room for everything.
[/list]

My media center pc is atom powered, and runs [XBMC Live]("http://wiki.xbmc.org/?title=XBMC_Live") really well. I use a Logitech wireless keyboard and mouse to control it.

Would NAS drive work?

---

### Post by CharlesA on 2010-04-04
> **Kdar said:**
> Would NAS drive work?

Should work. I didn't go that route since I wanted my server to do other things beside serve files: DHCP, Virtualization, etc.

---

### Post by JohnnyC35 on 2010-04-04
[LEFT][SIZE=2]I plan on making a file server myself. atm I have 3 Tb drives in my media-centre, an 2 500's and a 1Tb in external storage. I priced my server up fairly cheap, just need $$:[/SIZE][/LEFT]
            [LEFT][SIZE=2]
[/SIZE]
[SIZE=2]6 Port SATA PCI card (2 external, 4 internal) x3 (40$ a piece)[/SIZE][/LEFT]
    [LEFT][[SIZE=2]http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=5265863&CatId=1455[/SIZE]]("http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=5265863&CatId=1455")[/LEFT]
        [LEFT][SIZE=2]
[/SIZE]
[SIZE=2]Ultra M923 ATX Black Full Tower Case (30 lbs of 20 drive bay sexyness) (140$ (on sale))[/SIZE][/LEFT]
    [LEFT][[SIZE=2]http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=3319620&CatId=1510[/SIZE]]("http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=3319620&CatId=1510")[/LEFT]
        [LEFT][SIZE=2]
[/SIZE]
[SIZE=2]XFX nForce 750a(70$)[/SIZE][/LEFT]
    [LEFT][[SIZE=2]http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=4680349&CatId=3701[/SIZE]]("http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=4680349&CatId=3701")[/LEFT]
        [LEFT][SIZE=2]
[/SIZE]
[SIZE=2]AMD Athlon II X2 2452.9Ghz (70$)[/SIZE][/LEFT]
        [LEFT][[SIZE=2]http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=4924304&sku=A79-0245[/SIZE]]("http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=4924304&sku=A79-0245")[/LEFT]
        [LEFT][SIZE=2]
[/SIZE]
[SIZE=2]Crucial 1024MB 667Mhz (33$)[/SIZE][/LEFT]
        [LEFT][[SIZE=2]http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=1558820&CatId=1654[/SIZE]]("http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=1558820&CatId=1654")


[SIZE=2]Not including the PCI card(s) it wuld be 400$ w/ tax+ship.
[/SIZE][/LEFT]

---

### Post by Kdar on 2010-04-05
> **cariboo907 said:**
> I use nfs to mount the movie directory from my server, it is setup in fstab, so it mounts on boot.

I just had to rebuild my server as the motherboard that came from the garbage dump finally died :(. the new specs are:

[list]
[*] MSI [G31M3-F V2]("http://us.msi.com/index.php?func=proddesc&maincat_no=1&cat2_no=170&prod_no=1573#")
[*] Intel [E5400]("http://ark.intel.com/Product.aspx?id=40478")
[*] 2X Kingston 1Gb PC5400 ram
[*] 1 WD 320Gb PATA Hard Drive
[*] 1 Maxtor 120Gb PATA Hard Drive
[*] 2X Seagate 400Gb SATA Hard Drives
[*] 1 Seagate 750Gb SATA Hard Drive
[*] Coolermaster eXtreme Power Plus 500W power supply.
[*] junk case, that has enough room for everything.
[/list]

My media center pc is atom powered, and runs [XBMC Live]("http://wiki.xbmc.org/?title=XBMC_Live") really well. I use a Logitech wireless keyboard and mouse to control it.

What did you use on server? I mean what kind of OS?

---

### Post by cariboo on 2010-04-05
Seeing as I installed a new motherboard, I upgraded from Jaunty to Karmic server version.

---

### Post by handy on 2010-04-05
> **Kdar said:**
> ...
But recently I was thinking to make that HTPC really compact, use small hard-drive, possibly SSD, like you said. Hide it somewhere behind TV, maybe attach it to the wall. And to use Server with it in garage. 

You could use a flash card to run your system on, quiet & less power consumption.

> **Kdar said:**
> 
I was also thinking to wire my house with Cat5, so maybe I can do it all as one project. Make Ethernet plugs in my computer office, in tv room and move all routers with server to garage.

If you use Cat5e it will cost you very little more for the cable, & you will be able to use gigabit speed LAN on it if you choose to at a later date.

---

### Post by Paqman on 2010-04-05
If you don't want to build your own file server/NAS there's some good ones on the market now. I've got one of the QNAP RAID-1 NAS boxes (TS-209). It runs Linux on an ARM chip with full Telnet/SSH access. I normally build my own systems, but I got this because it's smaller, simpler and uses much less power than an x86 machine.

If you're going to move all the storage away from the HTPC then you won't need a big hard drive in it. It's a good opportunity to use a small fast SSD instead of a magnetic hard drive. For an HTPC having it boot up fast is nice. I like an HTPC to be like an appliance, not a PC.

---

### Post by handy on 2010-04-05
That's true, I use a Netgear ReadyNAS Duo, it runs a cut down version of Debian, has gigabit NIC built in, & uses bugger all power & is quiet. Runs on a Sun processor, 256MB SODIMM, upgradeable to 1GB.

---

### Post by solitaire on 2010-04-05
if you go for the Atom ION board then it might be an idea to use it's "mini-pci" slot for a 16Gb ssd rather than a wireless controller. (Personally I think Media centers work better with wired connections to their servers / router ) :)

That means you don't need a separate ssd or hard drive so the unit is smaller and you can get away with a smaller PSU in the case.

---

### Post by Kdar on 2010-04-05
> **solitaire said:**
> if you go for the Atom ION board then it might be an idea to use it's "mini-pci" slot for a 16Gb ssd rather than a wireless controller. (Personally I think Media centers work better with wired connections to their servers / router ) :)

That means you don't need a separate ssd or hard drive so the unit is smaller and you can get away with a smaller PSU in the case.

Thats good idea. Especially that I will do wired connection in my house, at least for my Office-room and Tv-room, I would never use it.

---------------------------------
What about TV-tuner? Where should I install it into HTPC or into Server?

Or people put TV-tuners into servers just for recordings?
(I am not really familiar with this, just read it somewhere few days ago).

---

