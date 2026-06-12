---
title: "Ununtu linux server  -RAID5  -data:  SetUp"
date: 2011-01-17
forum: Server Platforms
---

### Post by Glycergic on 2011-01-17
Hi

This is my first post here I think, and directly with a lot of questions actually :p  I'm in the (early) process of setting up my own ubuntu server.

I'd like to make it a back-up and data streaming (over the wifi) -server. Is there a special ubuntu server edition to get or something?

At the moment I have a desktop computer with about 3-4TB of data. I'd like to get about 1TB in a decent back-up system (I was thinking RAID5), by which I could also stream over the wifi at home.
// --> how could you easily receive music, without a laptop or such?

I was thinking of perhaps putting together a simple desktop, packed with some harddisks. Or could I run it on my current desktop (= putting my 2-3TB somewhere else)?


Do you have a similar project? Practical information? Would be great!

---

### Post by Glycergic on 2011-01-21
No one with information?

I downloaded the ubuntu server edition. In the meanwhile I'm buying an old pentium 4 computer in which I will build in some hard disks.

I'll see from there...

---

### Post by Boondoklife on 2011-01-21
It might just be how you phrased your question, I really am not sure exactly what you are asking.

You mentioned backups and media streaming, but not what OS or devices you will be using. If you are streaming music and the client support DAAP then you could try tangerine media sharing. If you are looking to just share your files then you should look into smb,ftp, or nfs (again depending on the devices and oses your planning to use)

As for backups, if you are looking to make and restore system images then you should look into tftp and clonezilla. If you are looking to just store your files some where secure, then look into smb,ftp, or nfs (again depending on the devices and oses your planning to use).

As for the RAID 5, that is a good choice! I would go with 5 disks to start with (4 Live and 1 Spare). This setup allows for two drives to fail with out you loosing data. It has speed benefits similar to RAID 0 and great redundancy. 

Try to give your questions a little more direction and I'm sure you'll get some good answers.

---

### Post by Glycergic on 2011-01-21
Oh okay, I knew there was something.

I just want my music collection secure together with my movie collection and to stream them.

For the devices, what is it dependent of, which protocol to use? IDE/SATA? Hardware (mobo?)?

I'll be using ubuntu server edition, expecting it to have enough options.


For the disk size, perhaps I would take 500GB disks? With 2TB I'll have more than enough.


Then, I have one more, maybe weird question. I would be putting the server upstairs, but I would like to be able to get to the music and play them with a little soundsystem (mini-jack connection) downstairs. Since I'm living together with some other guys, and they tend to break stuff from time to time, I wouldn't really want to put something expensive there. Is there like an easy receiver kind of solution to this?

---

### Post by Boondoklife on 2011-01-21
By devices I meant the ones that will be playing the videos/music. In your situation I would suggest getting something like the wester digital live. You can hook it to a tv and stream your data via smb shares. You could also get a Wii and hack it to play WiiMC, which will do the same, in the Wii's case it is wifi ready so you would not need to run wires.

If you are only looking to stream music then try a rocku sound bridge.

As far as drive sizes, that is up to you. I seen a deal on another site that had 1.5TB wester digital greens for $79 each. Put in a RAID 5 would yield 4.5TB of storage with 1 Spare.

---

### Post by Vegan on 2011-01-21
I would suggest a pair of 2 TB low power disks as discrete non-RAID drives. Then use the smaller disks with a dock to backup the internal disks.

---

### Post by Boondoklife on 2011-01-21
If you are going with a mirror mode, then you may just wanna look into a good NAS like the Wester Digital Mybook. They run linux and rock, check out some hacks [[here]("http://mybookworld.wikidot.com")].

I upgraded mine from a dual 750GB discs to dual 1.5TB, Wester digital green drives. Works great as long as you don't need transcoding.

---

### Post by tgalati4 on 2011-01-21
[http://freenas.org](http://freenas.org)

---

### Post by Glycergic on 2011-01-23
Ok, I'll try to respond in a logical order.

@ Boondok: 
- Is WD like, very good? Or do you just have some shares of the company ;)  But I guess the green means they use less power? That would definitely be a factor I'd like to take in account.

- Wii and Roku don't seem fitting

- The drive sizes you suggest are perhaps a bit too big.

==> Tonight, someone I know is going to bring over his Pentium 4 (hyperthreading), with sata, 350 Watt  computer over. I'm going to let the drive size depend on how many connections there are. 

@ Vegan:
- Why would I use this setup? What advantages does it have? I'm guessing this is the mirror mode Boondok is talking in his post?

@ Boondok:
- I don't really want a network drive or NAS, I want a system I can manage and change. 

@ Tgalati4:
- Thanks for the link, this seems like what I'll be needing!


So, the plan is, to buy this Pentium 4 tonight, put in some disks, and then install freenas on it. Do you guys think this is a good idea?

I saw these: 

[Seagate 500 GB]("http://www.pixmania.be/be/nl/2731285/art/seagate/barracuda-harddisk-7200-1.html")

One costs only 36,90 euro.

But perhaps I'll be going for 1TB per HD, just to be future proof :-)  The question would be, Seagate or Western Digital (or...)?

Anyway, thanks for your answers! Let's get this project going :D



PS: It would be to stream video and audio to mac and windows.

---

### Post by Boondoklife on 2011-01-23
> - Is WD like, very good? Or do you just have some shares of the company :wink:  But I guess the green means they use less power? That would definitely be a factor I'd like to take in account.
 
Well when you deal with hardware you tend to recommend what works for you, in this case I have had great luck with Western Digital drives. I do not own stock with them or stick with the exclusively though. The Green drives do use less and there is a special version for media centres. It is a 5400rpm drive but runs very cool and quiet.

>   - Wii and Roku don't seem fitting
Well you never said what will be playing the files, I personally find having a rig (unless it is well disguised) in your media centre can look tacky. I mentioned these two devices as they are cheap media player capable devices that hook to almost any TV/Radio.
 
>   - The drive sizes you suggest are perhaps a bit too big.
Not if you are seriously considering having video. I have a 750GB NAS that is completely full with media, I also have over 200DVD's worth of old archived videos that I had to burn off to discs.

If you are going with RAID1 and use two 500GB files, then you will only have 500GB of storage. If you use the RAID5 as I mentioned you will have 1.5TB and could loose two drives without loosing data (using 5 500GB drives).

If you are on a budget, this is why I suggested the larger drives. You can put two 1.5TB drives in RAID1 and have access to 1.5TB of space and still be able to loose one drive.

>  - I don't really want a network drive or NAS, I want a system I can manage and change. 
Kind of a funny statement, NAS is just an idea and you are in fact building a NAS. :p I am curious as to what you mean by a system you can manage. 

The MyBook World devices run a modified version of linux that you can hack to your hearts delight. I for example have it running a small webserver, transmission (torrent daemon), tftp, ftp, ssh, and a few scripts I put together to keep my media in logical folders and what not.

---

### Post by doogy2004 on 2011-01-23
> **Glycergic said:**
> I'd like to get about 1TB in a decent back-up system (I was thinking RAID5

It looks like you are thinking that RAID (any level) is a way to back up your data.  RAID is for speed and availability.  RAID is not a replacement for backing up your data.

---

### Post by Glycergic on 2011-01-26
@ Boondok, no pun intended btw, was just a joke :-)

Isn't 5400rpm gonna slow things down btw?

Those WD Mybook world hacks sound quite cool btw. I'd be happy to be able to integrate all those things on my nas/server.

And for the media that will be playing it, it'll be windows-driven and macintosh computers (that is what you meant, no?).

And I meant that I don't want a prefab NAS, but something I put together myself. Also, I just want to get to know the possibilities of linux as a server OS. I'd like to learn more about it.

Isn't RAID a protocol, as in how you back up? I just want to be REALLY safe, that's all :-)


So, I bought this Pentium 4 from a guy I know for 35 euro. Has 4 sata connections. I had a harddisk laying around, so I'm gonna test freeNAS with that, and I'll see what turns out. Having a bit of a hassle with putting it on a usb stick, apparently it wants dmg, not iso... (on a mac). Hopefully the mobo can boot usb drives...

If i figure out what exactly I want to use, I'll go on to the next part, buying me some hard disks :-)   And I am on a budget, but still convinced that this way, it'll cost me less than buying prefab. 

Thanks for the info!!!

---

### Post by Boondoklife on 2011-01-26
Well the 5400 will slow down the transfer rate in comparison to the higher rpm drives, but again there is a trade off for everything. If you go with the slower drives, they run cooler, quieter, and draw less power. This is a must for me as I don't want any heating issues on a box that only gets looked at when there is an issue. The transfers over the network prolly will not see a dent as the drives are on a 3.0Gb/s Sata  controller.

RAID is just a way to utilise many disks as one volume. It does offer redundancy, not to be confused with backups. Redundancy ensures that you can loose one or more hard disks without loosing data (dependant on the RAID level and number of disks used). A backup to an off-site server, preferably in another region of the world, is needed to make sure you still can get your data back should your box's flux capacitor go haywire and sends it back to 1955 with no hope of returning. 

If you are going with only 4 disks then I would stick with RAID5 as it will give you the most bang for your buck (3Live, 1Spare).

---

