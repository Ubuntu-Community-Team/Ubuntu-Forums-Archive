---
title: "Considering a Home Server, looking for advice"
date: 2011-01-27
forum: Server Platforms
---

### Post by deamon_knight on 2011-01-27
I'm looking to build a home server and I need some advice, my network knowledge is basic so I want to make sure what I think I want is possible/makes sense. I'm re-purposing and old gaming system so it will have some spare horsepower.

I'd like to setup a server that hosts my files on a RAID 5 array for redundancy, and I'm also considering a separate RAID 1 Array for the OS. I'd also like to run a torrent client and other downloading services on the server, although I want to manage this from a Win7 client (the New gaming system), and setup cron jobs so these run at night when I don't otherwise need the bandwidth. Eventually I will also want to configure this sever as a backend for MythBuntu or XBMC, so I'll add some TV capture cards, and I'll want to use the severs processing power to transcode/compress videos I want to save. I'll need to be able to manage this from a Linux or Win7 system, and my CLI knowledge isn't great, so I may need to log into a desktop remotely even though I think I'll run the unit headless once it is setup.

Currently I have a windows XP system and another system running Ubuntu. When watch a video shared from the Ubuntu system to the Windows one the access times seem slow, specifically: If I want to jump from one section of a show to another, there is a pronounced wait. One the same file locally there is not noticeable delay. I know that accessing a network resource will always be slower than a local one, but I'm hoping there is some way to get it better that what I am currently seeing. 

Access times is the first hurdle I'd like to solve before going this route, any have any suggestions? My current network is Megabit not Gigabit, and while I plan to move to Gigabit eventually its not an option now. Would using two megabit NICs bonded improve the transfers I'm seeing?

I also don't know if its easy to manage such a beast, checking for raid failures & such. Googling has giving me alot of Info but I'm having trouble verifing this info is recent and correct as of 10.04 (I plan to use a LTS for this project)

Thanks for sticking through that long post!

---

### Post by tgalati4 on 2011-01-27
Recent SATA speed improvements makes RAID for home or gaming use less of an improvement.  Network speeds depend on the quality of your wiring, quality of your switches, and quality of your NICs.  Using samba for file transfer or shared network access for game databases will result in 10 to 20 MB/sec, regardless of how your configure it, so RAID doesn't help there either.  If you are setting up a single-player flight simulator with lots of bitmaps, then possibly you will benefit from RAID striping.  Redundancy won't improve if you use crappy drives to build your RAID.  You would need enterprise-class drives to have a chance at improving reliability over consumer drives in a RAID configuration.  Your RAID controller and power supply also need to be just as reliable.

I can't help with streaming media performance.  If you are trying to stream high-def, then realize that bandwidth is high and the multiprocessing nature of linux will mean interrupts.  If you need better performance, then perhaps a real-time kernel with a slim mythtv client setup.  You need to experiment with your hardware to see what works.

---

### Post by Bucky Ball on 2011-01-27
Use 10.04 LTS Server Edition. LTS releases recommended for production machines, ie servers. Five years support (til April 2015). NOT 10.10. Not sure why those responsible create server editions of anything but the Long Term Support releases. :confused:

---

### Post by HermanAB on 2011-01-28
Howdy,

There are two ways to improve your network speed under Windows:
1. Install Gigabit ethernet
2. Install Windows Services for UNIX and use NFS instead of the default CIFS.

Either of those should double your network throughput.

---

### Post by deamon_knight on 2011-02-12
I'm looking at setting this up a primarily a file server and running downloads and bittorrent, so I'm looking at using RAID for redundancy rather than performance. I'm also a little confused about "streaming" media. If I map a network file system and play a media file from that file system is that streaming? or is there some additional service that needs installed on client and server, uPNP or something else?

---

### Post by jbrown96 on 2011-02-12
> **deamon_knight said:**
> I'm looking at setting this up a primarily a file server and running downloads and bittorrent, so I'm looking at using RAID for redundancy rather than performance. I'm also a little confused about "streaming" media. If I map a network file system and play a media file from that file system is that streaming? or is there some additional service that needs installed on client and server, uPNP or something else?

You'll probably want to run some sort of DLNA (UPnP) media server. I use Mediatomb (packages available) with great success. Some people also like PS3MediaServer (works with way more than the PS3) if they need to transcode in real time. 


RAID is fairly easy, but you need to be kind of careful with the drives. I have a 4x1TB RAID6 array that is a pain. Two of the drives are "green" (one is a Samsung and the other is a WD). They spin-down more aggressively, and report too slowly to the OS sometimes. Linux will mark them "failed" or "remove." There's nothing wrong with them, but you have to rebuild the array about once a month (my array takes ~10 hours to rebuild). I don't have any problems with the regular (non-green) Hitachi drives.
If you do plan to use green drives, I'd go with RAID6 so one of these "fake" failures doesn't kill your array if it dies during a rebuild. 

Managing RAID is fairly easy. You just need to remember to check it in some fashion. By default, if there is a failure, the system will send you an email. I use Fedora, which has a real root account, so the email is sent to root@localhost, and I can check it with ```
mail
```. Ubuntu probably sends mail to the first user. You could also set it up to send the system mail to any mail account (mine also goes to my Gmail). That should help you be proactive about any failures, but if you want to manually check you can use:
```
mdadm -D /dev/mdX
``` where X is the number of your RAID array (probably 0 but mine is 127). 

RAID is fairly easy as long as you understand what it does, and that it's not a backup.

---

### Post by cbanakis on 2011-02-12
As far as hardware goes, I have spent years researching the most affordable, reliable, and insanely large storage solution for my home.

Unfortunately I still have windows in the mix, but that is because there is no linux based media center that compares to windows media center.  (not including glitches and stability)

First of all, gigabit is a MUST.
You can save alot of money by running cat 5e instead of cat 6 wire.  (works fine for me)

Here is a list of all my hardware.
I'll try to include prices and links.

20x [http://www.newegg.com/Product/Product.aspx?Item=N82E16822148337](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148337) $70 each
(You can get whatever drives, but STAY AWAY from WD drives unless they are enterprise drives)

4x [http://www.newegg.com/Product/Product.aspx?Item=N82E16816132015&cm_re=port_multiplier_esata-_-16-132-015-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16816132015&cm_re=port_multiplier_esata-_-16-132-015-_-Product) $200 each

1x [http://www.newegg.com/Product/Product.aspx?Item=N82E16816115036&cm_re=port_multiplier_esata-_-16-115-036-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16816115036&cm_re=port_multiplier_esata-_-16-115-036-_-Product) $185

1x [http://www.newegg.com/Product/Product.aspx?Item=N82E16811133093](http://www.newegg.com/Product/Product.aspx?Item=N82E16811133093) $65
(I drilled a 4" hole on top and mounted a 120mm fan instead of installing a cdrom)

1x [http://www.newegg.com/Product/Product.aspx?Item=N82E16813500042](http://www.newegg.com/Product/Product.aspx?Item=N82E16813500042) $90

1x [http://www.newegg.com/Product/Product.aspx?Item=N82E16819116367](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116367) $70

1x [http://www.newegg.com/Product/Product.aspx?Item=N82E16820220396](http://www.newegg.com/Product/Product.aspx?Item=N82E16820220396) $60

1x [http://www.newegg.com/Product/Product.aspx?Item=N82E16820233122](http://www.newegg.com/Product/Product.aspx?Item=N82E16820233122) $79

Total Price Tag
$2748.70

Total Capacity at RAID5
26TB

Pretty pricey, but not really.
Its pretty much the cost of any near top of the line computer.

This angers me though, because I built it a couple years ago, and it was around $5,000.00 at that time :(

Heres a fancy picture of my fancy server :)

[http://i340.photobucket.com/albums/o344/cbanakis/photo.jpg](http://i340.photobucket.com/albums/o344/cbanakis/photo.jpg)

You can mix and match hard drives and enclosures.
But any setup using esata port multipliers will save you thousands.

Be advised, the rocket raid controller will not support more than 16 drives in a single array with the proved drivers.

I have custom drivers for both windows and linux that allow full 20drive use, so if anyone needs them let me know.
You can also get them direct from highpoint as I did, but it was a hassle dealing with them.

PM me if you need any info from me.

I'll be glad to share my experiences.

---

### Post by ashikaga on 2011-02-12
> **deamon_knight said:**
> 
I'd like to setup a server that hosts my files on a RAID 5 array for redundancy, and I'm also considering a separate RAID 1 Array for the OS.
If you are using Linux software RAID (mdadm), you may want to stay away from WD Green drives, as I've recently learned [the hard way.]("http://ubuntuforums.org/showthread.php?t=1681924")

---

### Post by cbanakis on 2011-02-12
> **ashikaga said:**
> If you are using Linux software RAID (mdadm), you may want to stay away from WD Green drives, as I've recently learned [the hard way.]("http://ubuntuforums.org/showthread.php?t=1681924")

YES, STAY THE HECK AWAY FROM WD

My buddy has a similar setup to mine, but went with WD

EPIC FAILURE

6 months in, 13 of his 20 green drives failed.

He has enterprise drives now, and all seems well.  But bare in mind that WD enterprise drives cost much more than seagate barracudas, and they aren't a whole lot more reliable.

Ive been messing with computers for about 18 years, and I've only seen 5 seagate drives fail.

That doesn't mean they wont break though.

Note the static back on the shelf in the picture of my server.
It contains a spare drive, just in case.

---

### Post by RockinRob2258 on 2011-02-12
What are these green disks you guys keep talking about?
Hoping to eventually build a home server but not enough cash saved up at this point :P

---

### Post by cbanakis on 2011-02-12
If its made by Western Digital, and it doesn't say "Enterprise" on it, it is either a green drive, or might as well be.

The Green Drive is a WD drive.

They did a real crappy job throwing it together.
(Very slow and unreliable)

Coincidently, this slow crappy drive uses less power than most decent drives, so Western Digital decided to call them Green.  Like "Green" for the earth.

A green drive is sorta like taking a hybrid car to the race track.
You WILL lose, every time.

---

### Post by jbrown96 on 2011-02-12
> **cbanakis said:**
> If its made by Western Digital, and it doesn't say "Enterprise" on it, it is either a green drive, or might as well be.

The Green Drive is a WD drive.

They did a real crappy job throwing it together.
(Very slow and unreliable)

Coincidently, this slow crappy drive uses less power than most decent drives, so Western Digital decided to call them Green.  Like "Green" for the earth.

A green drive is sorta like taking a hybrid car to the race track.
You WILL lose, every time.

Any of the "power-saving" drives will do this, but the WDs are very bad. 

The thing is that the drives don't actually fail. The RAID hardware/software thinks they do and marks them failed. You can just re-add them to the array, but they will fail again in a certain amount of time. Most people RMA them, but that's worthless because there's nothing wrong with it; they just aren't suited to RAID applications. 
Just buy 7200rpm drives and you won't have to worry at all.

---

### Post by Bucky Ball on 2011-02-13
I'm not running RAID but have been using WD Green drives for ages. Never a problem.

---

### Post by cbanakis on 2011-02-13
IDK, my experience has caused me to be a hater when it comes to Western Digital.

I've even had 4 velociraptors fail on me, and they are supposed to be the cream of the crop.

Seagate 4 life

---

### Post by ashikaga on 2011-02-13
> **Bucky Ball said:**
> I'm not running RAID but have been using WD Green drives for ages. Never a problem.
To be clear - the issue here is not WD Green drives per se, it's that they are a bad choice for RAID. I only wish I'd realised this before I bought three of them! Fortunately it seems you can work around the issues.

re. Seagate vs WD, it seems to me that you can find plenty of anecdotal evidence on either side of the debate, depending on which brand of fanboy/girl you consult. :) I've personally oscillated back and forth several times over the years.

---

### Post by cbanakis on 2011-02-13
I guess I could agree with that.

My whole thing is that the Barracuda's and the Green drives are comparable in price, but as far as RAID goes NOT in performance.

The Barracuda's are good enough to run in RAID, and the Green drives are not.

Really, the only choices for building a RAID server are Seagate Barracuda's, Western Digital Black Drives, or Seagate Constellations.

The Most affordable being the Barracuda's as far as $ per Gigabyte goes.

But we are all in agreement to STAY AWAY from WD Green drives for whatever reason.

I do base my opinions on experience though, not being a "fan boy"

And I have gone through hundreds of hard drives over the years.

---

### Post by cbanakis on 2011-02-13
[deamon_knight]("http://ubuntuforums.org/member.php?u=408100"),

To answer more of your concerns.

It has been my experience that windows and linux to not get along so well when it comes to networking.  (stable and reliable, yes, but not very fast)

I'm sure its possible to get it working right if you have the time/energy/knowledge...

Transfer speeds seem to be greatly diminished when going from one to the other, despite your network hardware.

I am forced to use Windows7 Media Center in my living room and bed room because I want full TV capture capabilities (Cable TV) AND the ability to access and play all my archived movies/tv shows from my file server.

I have spent an insane amount of time trying to find a linux based alternative to windows media center, and cannot find a single one that has all the functions I want/need.

I originally had Ubuntu running on my server, and saw 100mb+ transfer speeds to and from my Ubuntu desktop and laptop, but the windows machines were only seeing 10-30mb

Since the media centers are my main concern, I ended up running windows server 2008 on my server, and it works like a charm.

Except, now when I transfer to and from my desktop I have the slow 30mb speeds, but that is acceptable because desktop access is not my priority.

As far as I know, there is no practical way to bond 2 100mb lans.
But even if you could, it would still only be 200mb.  (still kinda slow)

Even wireless N is more than double the speed of 10/100 now, so I would start by moving up to gigabit.

FYI, I only brought up wireless N as a speed example.
DO NOT USE WIRELESS N, LOL

Wireless is great for many things, like a laptop or a smart phone.

For on-line gaming, and HTPC's pulling data from a file server, you gotta get the wire.

I'm not sure what kind of video you plan on accessing over your network, but it was my experience that HD content barley worked at all till after the gigabit upgrade.

---

### Post by garfonzo on 2011-02-13
I might as well chime in since I run a system much to what you're looking for. I have a Ubuntu server in my garage with 3 hard drives totaling 1.1TB. This is just a big fat file server. I have multiple Windows computers in my home (no Ubuntu desktops). 

I have a specific computer dedicated to watching movies and is connected to my HD Projector. This computer is just a Dell optiplex something or other, small, and quite. Fantastic for watching movies on. 

My main desktop runs Windows media center for recording TV. When a show is recorded, I have "MCE Media Buddy" automatically convert the recorded TV to an AVI, send it to the server, and delete the original. That way my shows are all waiting to be watched from any computer in the house. 

Since the computer connected to the projector is windows, I could use XBMC or something, but I prefer to just open up Windows Explorer, navigate to my movie/TV show of choice, and watch it via VLC. This is just faster without any frills and eye candy. Don't get me wrong, the eye candy is beautiful (and I tried XBMC) but I figure I'm there to watch a movie, not the eye candy. I'll admit that when I have friends over to watch a movie, I'll bust out XBMC to get the "OOooos" and "AAaaahhs". Fun!

What ties all the computers together is a Gigabit wired system I installed myself with CAT 5e cables. I can stream 1080p movies from my Ubuntu server to my movie computer without a glitch. I can jump forward in the movie, back, without hesitation. I use Samba on the Ubuntu box to "talk" to all the Windows computers. The transfer speeds from a Windows machine to the Ubuntu box aren't superb, ranging from 20-30MB/s (megabytes, not megabits). 

Samba was a bit of a hassle to set up, but now that it is up, I don't need to touch it. As far as redundancy, every hard drive attached to my server has an "twin" which I copy all the data to once a week using rsync. This is automated through a cron job.

Anyway, that's my setup in a nutshell.

---

### Post by deamon_knight on 2011-02-14
Thanks guys, this is a lot of great info. cbanakis, wow, just wow. Thats WAY more than I'm aiming for, but thats also pretty cool. I'm Planning to ultimately have a network setup like this. 1 Gaming/Performance desktop running Win7. 1 File server, bittorrent etc. server, and 1 media center system. The gaming system needs to be Win7, but I'd like to have the Server as Linux based as the media center as Linux based (although my current Media Center is win XP) I'm currently replacing my Gaming system with a new one and a the old gaming system is available to be turned into a file server for this purpose.

I'd like to have a linux based media center (perhaps front end is a better description) and have most of the downloading, media storage and TV capture occurring on the file server and the media just being accessible/manageable from the media center. Now this puts a lot of demands on the file server. However, I'm not planning on upgrading the Media center system just yet, so I'm focusing on the file server.

As the file server goes, I plan to use software RAID to keep costs down, and I thought you could alter the timeout failure settings to allow for this. The "feature" in wester digital driver is called TLER, see [here]("http://www.google.com/url?sa=t&source=web&cd=1&sqi=2&ved=0CBYQFjAA&url=http%3A%2F%2Fwww.wdc.com%2Fwdproducts%2Flibrary%2Fother%2F2579-001098.pdf&rct=j&q=wester%20digital%20tler%20raid%20management&ei=QuZZTcjFLYL7lwfc5aX2DA&usg=AFQjCNFp1k98K6Uv_hnxCLV203VxkMt5RQ&cad=rja") . 

I'm not sure what analogous setting on seagate or hitachi drives are. I wasn't planning on using green WD drives, although their lower power consumption seems like it might make sense when you have several drives. It also appears that WesterDigital, and maybe others, disabled the ability to alter the timeouts on their consumer level drives to push sales of their enterprise disks.

If I just want a 4 disk RAID 5 array, or a two disk RAID 1 array, is this easy to setup using mdadm? Is there a walkthrough somewhere for trying to select the best settings, block size, etc. ?

---

### Post by cbanakis on 2011-02-15
**TLER**

OK, Western Digital drives are not locked, but they stopped distributing the TLER software, and deny ever having it. 
Even though myself, and a few friends personally received the software directly from Western Digital in the past.

They also void your warranty if you RMA a modified drive.  (Losers)

You can still get the TLER software if you hunt around online, and if  your completely hellbent on Western Digital, I guess I could send it to you.  (I'm sure I got in somewhere on this server, LOL)

Not sure about Hitachi, but Seagate Barracuda's just work, no tweaking necessary.

Of course Enterprise drives by any manufacturer are the ideal way to go for RAID. (But at what cost?)

**Hard Drives**

Seriously though, Western Digital Vs Seagate...

Western Digital loses in every application (excluding the VelociRaptor)

Ive also had more than too many VelociRaptors fail on me, but its worth dealing with for a 10k RPM SATA drive.  (I Guess)

I'm not speaking as a Seagate fanboy.

As you can probably tell, I know a thing or two about hard drives.

I have probably gone through about 100 drives in the last 10 years.

Maxtor and Quantum were the absolute worst, next is Western Digital.

The best is probably somewhere between Hitachi, and Seagate overall.
But I don't have much experience with Hitachi, cause they have a very limited selection on drives, so Ive only had a few.  

Also, Never owned a Samsung...

**RAID**

Not sure about command lines to create a RAID array, but in ubuntu you can easily setup a software raid in disk utility.

Just File/Create/RAID Array

The choose RAID5, and select the disks you want to use.

---

