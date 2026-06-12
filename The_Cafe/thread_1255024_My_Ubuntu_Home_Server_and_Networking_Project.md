---
title: "My Ubuntu Home Server and Networking Project"
date: 2009-09-01
forum: The Cafe
---

### Post by flatland2d on 2009-09-01
I wrote this in my personal blog, but also wanted to share it with the Ubuntu community.

I take a lot of pictures and video. My current disk usage for video is 78GB and pictures is 160GB. That amounts to 34,000+ pictures, although many are duplicates shot in RAW+jpeg formats. Each full memory card from my camera dumps another 2GB onto the hard drive, which was beginning to run out of space. I had been shuffling files around between the two 320GB hard drives in my desktop in order to avoid the "low disk space" warnings and burning DVDs of the files I don’t access often. More importantly, these hard drives contain the only copies of these pictures and videos, which document the last six years of my life and countless memories. A destructive Windows virus (unfortuntely, the OS of choice for the desktop) or hard drive failure could potentially erase all of my media. I decided to add more storage space and proactively safeguard my pictures and videos. The best solution was decided to be building a home server with redundant hard drives.

After much research, I ended up building the following:

[LIST]
[*]      AMD Sempron 140 Sargas 2.7GHz Socket AM3 processor
[*]      ASRock M3A780GXH/128M motherboard
[*]      Crucial 2GB DDR3 RAM
[*]      Two 1TB Western Digital Caviar Green SATA-II hard drives for storage
[*]      100GB Western Digital IDE hard drive for operating system (pulled from my parts box of computer stuff)
[*]      Case, fans, cables, and other accessories
[/LIST]

The server went together fairly quickly and I fortunately didn’t forget to order any critical pieces. The processor chosen is a low power model than only uses 45 watts. The Green series hard drives are also low energy devices. The complete up-and-running server uses 82 Watts in idle condition (105 Watts at 100% load). This has an operating cost of $1.47 per week in electricity. Most amazing is that the heatsink on the processor is cool to the touch, without the slightest hint of warmth. The exhaust air leaving the case is also room temperature. The motherboard has six SATA-II ports, allowing me to connect an additional four hard drives someday.

[IMG]http://www.morlinos.com/pictures/homeserver/DSC04236.jpg[/IMG]

[IMG]http://www.morlinos.com/pictures/homeserver/DSC04241.jpg[/IMG]

So maybe the blue LEDs are not totally required for a server I hardly ever look at, but who says you can't have a little flair.  The LEDs draw practically nothing, so it doesn't add to the electric bill.

I installed Ubuntu 9.04 desktop edition.  Before everyone criticizes the desktop version, let me just say this was my personal choice.  I like being able to remote desktop in to work on it.  I'm learning a heck of a lot about servers in general by doing this project and wanted the GUI to help me adjust.  Plus, my wife needs occasional access and there's no way she's learning ssh and shell commands.

**Backup Policy**

Only one of the terabyte hard drives is shared with Windows. The second terabyte drive is rsync'ed to the first every night. A RAID array was considered, but some vulnerabilities led me to choosing rsync instead.  I might change this to run less frequently.

I might use another hard drive to to make yet another backup. As mentioned, many of my pictures are duplicates. The RAW files average about 10MB and the jpeg files average about 2.5MB. I like keeping the RAW files because it contains the image information straight off the camera’s sensor without lossy compression, like jpeg does. However, in a something-better-than-nothing situation, I could just rsync the jpeg files, only needing one fourth the storage size. This drive would then be disconnected from the server and stored in a fireproof safe at the other end of the house, which would protect against lightning strikes (should the surge protector on the server fail to operate fast enough), fire, and theft of the server. Rsync-ing would only be done every month or two since it would have to be done manually. Might be a little excessive, but I really don’t want to lose my pictures.
[B]
Networking[/B]

In order to get my desktop, server, PS3, and DVR connected to the network (Dish wants to charge $5 a month for NOT having your DVR connected to the internet!), I needed to run Cat-5e ethernet cable from the jacks, through the walls and attic, and back to my central networking station, the office closet. Only existing jacks were chosen to have ethernet added because this greatly simplified the installation. Our home builder graciously installed two coax and one phone line in every wall plate, so one coax cable was disconnected and used as a pull string to feed cable up through the walls and into the attic. Once done, the coax was pulled back down and reconnected. A while back I ran our surround sound through the walls and attic and did not have existing cables to pull on which was a real pain.

A standard six port wall plate was chosen that is capable of accepting various inserts for coax and ethernet jacks, and blank inserts covered up unused holes. Four runs of Cat-5e was made to the entertainment center for the PS3 and DVR, leaving two spares for future devices. Two runs were made to the desktop, leaving one spare for connecting a laptop to the wired network (faster than wireless) or a future network capable printer. One run was made to my hobby table, also for laptop use.

[IMG]http://www.morlinos.com/pictures/homeserver/DSC04256.jpg[/IMG]
This is the wallplate for the entertainment center.

All the Cat-5e cables terminate in the closet where I also used wall plates as a kind of patch panel. One port was used for coax which I had to swap with our previous internet enabled outlet in the outside cable service box. I only have a four port router, so I can only have four devices on the network at a time. Including a switch into the network someday would allow use of the other jacks.  For now, four is enough.

[IMG]http://www.morlinos.com/pictures/homeserver/DSC04252.jpg[/IMG]
The patch panel.

**Optimizing the Wireless Network**

A wireless survery was conducted in order to find the optimal orientation for the wireless router. Since it doesn’t use external antennas, it’s not obvious how obtain optimal coverage in my house. The survey was conducted by running kismet on my laptop from the back of the living room, which is our most frequently used wireless area. The router was orientated on each 3D plane and signal strength was measured. I found that any upright orientation provided noticeably better received power than when it was lying flat, which is probably how most people end up using it.

[IMG]http://www.morlinos.com/pictures/homeserver/DSC04251.jpg[/IMG]
This particular orientation was chosen because it allows the wires to flow cleanly.

**PS3 Media Server**

The server also functions as a media server for the PS3. I don’t know how accurate this is, but the media server software (ps3mediaserver) reported a peak transfer rate of 190Mbps, which is pretty darn fast.  It's only a 100Mbit LAN, so I don't know...

[IMG]http://www.morlinos.com/pictures/homeserver/DSC04228.jpg[/IMG]
The complete setup.

In the near future I might be adding Skype to this server to run the phone jacks in my house (currently not in use - we are a cell phone only family).  I've been looking into ZoneMinder and might use this server as a DVR for the security cameras.  And X10 home automation will probably play into all this someday, too.  I'm loving all the possibilities.  When first thinking about adding more storage, I was considering just using NAS, and I'm so glad I decided to build the complete setup instead.  Overall cost for the project was $400 for the server and $100 for networking supplies (cable, jacks, wall plates).  The server is probably way overkill for what it does, but I'm hoping it will keep up with all the future projects I throw at it.  It currently transcodes videos in real time to the PS3 with ease.

I hope you've enjoyed reading this and maybe given some good ideas to people thinking about building a home server.

---

