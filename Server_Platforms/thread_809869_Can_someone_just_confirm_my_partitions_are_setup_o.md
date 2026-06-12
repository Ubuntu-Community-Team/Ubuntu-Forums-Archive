---
title: "Can someone just confirm my partitions are setup ok"
date: 2008-05-27
forum: Server Platforms
---

### Post by garethsimpsonuk on 2008-05-27
Evening all (if ur in england) I reinstalled my server to day after first doing a 'trial run' (installing / uninstalling, trying different setups) as I'm new to Linux.

I have chosen to stop using the guided installation as I didn't like the idea of 256mb scratch space and have read of better setups.
Here is what I've done:

sda - /
sdc1 - /swap
sdc2 - /home

I have 256mb of RAM but I will be upgrading to either 512mb or maybe to 1gb as it's only cheap.
Was I right in selecting logical and then swap? I also chose none bootable for swap / home and bootable for sda (root). Is this correct?

I did just come across an article stating that for servers you should have your swap half the size of your RAM? Is this correct?
Why don't we set our swap to like 4GB if we have the space? Is it because the data gets fragmented on a large partition? In windows it's a good idea to use a dedicated disk (I use a USB memory stick) for your paging file. Does this apply to Linux / UNIX aswell?
I just wanted people to check my setup and make sure it's ok.
I have installed root on a 4.3GB IDE drive which I think is quite old and may be a slower RPM than some of my other ones, is this a bad idea for my root? Will it affect performance?

Thanks for your time guys I just wanted to make sure I haven't made any mistakes.

Gareth

---

### Post by NateMan on 2008-05-27
yes swap space is almost identical for all of those concerns to a paging file. There is no disadvantage to using more swap space, if you have a fast drive for it, it can dramatically increase performance. I have my server swap file on a hardware raid array and it seems to go quite quickly. If the small drive is much slower in rpms it would probably be a good idea to use one of the other drives, esp since data density would increase performance as well. If you have a 40gig single platter drive that would probably give you the best performance. On my server with 5gigs of ram I gave it a full 8gigs for swap space, just in case I want to run virtual machines (which it would probably do quite well at, since the swap drive is quite fast as well.) Your swap space is setup correctly as is your root, however due to the drive being slower, it might be best to use your fastest drive for that purpose. Hopefully that will help. The flash drive idea you used in windows seems like a good one, except that they only have so many writes in their lifespan and swap space will do quite a bit of writing.

---

### Post by garethsimpsonuk on 2008-05-27
Yea I setup mr / (root) on the old drive and my swap is on the 40GB so now it's confirmed I'm confident in the setup (it was your advice that guided me to this setup so thanks)
Thanks for a your post I think we got off to a bad start on the last post and again you've posted to help me so I apprecaite that, cheers

Gareth

(what controls the data density is that sector size?)

---

### Post by garethsimpsonuk on 2008-05-27
Yea I setup my / (root) on the old drive and my swap + home is on the 40GB so now it's confirmed I'm confident in the setup (it was your advice that guided me to this setup so thanks)
Thanks for a your post I think we got off to a bad start on the last post and again you've posted to help me so I appreciate that, cheers

Gareth

(what controls the data density is that sector size?)

---

### Post by NateMan on 2008-05-27
I am not sure, but as far as I can tell, yes sector size is directly related to data density. I have several 40gig drives, but one is a single platter and runs circles around the others because the read/write heads just don't have to physically move as much.

---

### Post by NateMan on 2008-05-27
Also moving the root file system off of the 4 gig drive would make a big difference in performance as well. I should have thought of the data density issue in your first post.

---

### Post by NateMan on 2008-05-27
P.S.- I'm always glad to help. I've learned quite a bit in my years and its not the linux way to keep it secret.

---

### Post by garethsimpsonuk on 2008-05-27
Yea you did mention it. I do notice the difference I think, synaptic seems to lock up when all updates are marked for download at once (it's only a 1.7ghz athlon, I see a lot of prebuilt servers have athlons are these good for a server?)
While we're on the intricasies of hard drives is the beginning of the drive (according to ubuntu installer) the edge of the disc? Is the fastest part of the disk the centre because the head doesn't have to move around so much? when partitioning I was given the option of beginning or end for partitions. I chose the beginning for swap was that right do you know?
Now I know that my root should really be on a faster drive I think I might go back to using the 40GB for root, otherwise it will bug me. Now I know a bit more I think I will use 1 the 40GB for my root + home and and a 1 or 2 GB partition on the other 40GB (on the other ribbon cable) for swap. I will use the rest of the 40GB and the 80GB for other data. When I can overcome my habit of reinstalling I will take the DVD driveout and use that for another 80GB. ( I would like to use a 500GB but it's SATA so I guess I would have to buy a controller?)
Will this new setup be a good one? Let me know if you can and I will start the new installation for over night.
Thanks, here we go again lol

(I'm feeling a bit cocky should I go for seperate partitions for my tmp / local etc.?)

---

### Post by NateMan on 2008-05-27
well a 1.7 gig athlon is a lot of processing power for a server, some might disagree, but I have twin 1gig p3s running my server and I can't even get it to use a fourth of what they have, not even while encoding music for streaming. I've always noticed better performance from the end of my discs so I normally place my swap at the end and / at the beginning. Why don't you try setting up a separate partition for / and /var on your home drive, about half and half for each then use your 80gig for your /home. Then as you add in drives you can setup them to be mounted in /media or /home and then use symbolic links to them. I love using links as it lets mount a drive in one place but access any part of it from your /home (or wherever). Mount your additional 40 and 80gig(when available) in media. 
Now as for the sata, I've been using a cheap sata card shown here: [http://www.newegg.com/Product/Product.aspx?Item=N82E16816132013](http://www.newegg.com/Product/Product.aspx?Item=N82E16816132013)
it works very well and even has the ability to use the esata ports on the back, with the correct jumpers. I got it to use a 300gig sata drive in my server as a /scratch drive, and to allow for myself to plug in esata drives. Works with no problems in linux (unless you read the manual wrong and plug your sata cable into the wrong port, I have an embarrassing post out there.). Then you can mount that drive and create links as well. In fact links can be used instead of partitions for more stuff than people imagine. Gotta love unix.

---

### Post by garethsimpsonuk on 2008-05-27
thats good to know, i'll try my swap at the end this time, it's hard to know what is considered the end and whats the beginning, I don't know but I'd say near the spidle is the beginning. n e idea?
You're a great advocate of symbolic links! I've been reading about them + hard links. I'm sure there a lot more but they seem to be just a linux version of shortcuts. If I save to a symbolic link does it save to the target? I will have to read some more.
Just quickly am I right in setting all partitions to logical and only the root with a bottable flag?
cheers

---

### Post by NateMan on 2008-05-27
I normally make all of my partitions primary, unless they are an array or something of that sort, but you can set only your / partition to be bootable. I would make them all primary. Logical partitions work somewhat differently. And yes they are in a way just the linux version of shortcuts, but they are much more powerful, more like the files actually exist where they are linked instead of in windows where it is something different.
Heres a good explanation: [http://www.wellho.net/mouth/334_Symbolic-links-and-hard-links.html](http://www.wellho.net/mouth/334_Symbolic-links-and-hard-links.html) Basically symbolic links give multiple files one name and hard links give one file multiple names. Both are very useful in linux administration.

---

### Post by garethsimpsonuk on 2008-05-28
cool thanx. yea I actually meant I used primary not logical. I've just got up for work and I was gonna set the installation off but I realise that to keep all critical parttitions off the slow drive I'll have to maybe put something on the 80GB, which is on the same cable as the 40GB. 
While I can do it I might aswell put them on seperate ribbin cables, which means I have to mess around with the jumpers etc. which is probably gonna be a problem as it always is has some dont have diagrams on! So I'll start it all after work and try and have basic operation set up tonight.
Thanx for the link on links, it all helps towards my education. 
I'm thinking of getting off my CIW (Certified Internet Webmasters Course) and maybe starting an A+, then a Linux+. Even though I love the design side, I seem to be messing with Linux over getting on with the web design jobs I have. Or maybe wait until I've finished this course, and do the A+ & Linux+ as it would be a shame to not finish it now. Have you done any of the certs?
Thanx for ur help again.

By the way out of these 2 options what would you say?

/ - sda1 -- 5 / 6 / 7 GB? 
*I had this on the 4GB I have now the option to enlarge it, should I just to be safe? I think will have a lot of apps eventually (will also contain public shares & everyones private directories)*
swap - sdc1 -- 1GB or 2 or 3?  
*will be getting more RAM v.soon, either 512MB or 1GB depending how cheap the old stuff is now.*
/home - sdc2 -- the whole 80GB? It will contain movies / music / large torrent files until I archive them on 500GB USB drive (or maybe I will take the plunge and format the USB in EXT3 (or JFS what you reckon?) and save them straight on there? 
I can then use the 4GB for my work / websites and make that private. 

or...

( the same options / partitions as above apply but just moving them around. )

/ - sda1
/home - sda2
swap - sdc1
/media/business - sdd

Obviously sda & sdc will be on seperate ribbon cables, if you can think of a better setup like this let me know. You don't have to answer if you're busy you've done enough! Cheers

I have 2 40GB drives how do I determine the read / write speed? Is it the RPM? I thought most drives (probably all the IDE ones I have would be 7200RPM) and the more expensive ones are 10,000 or summink. One of the 40GB drives is from like '05 and the other is from '08 shall I use the '08 or will they both be the same speed?

---

### Post by garethsimpsonuk on 2008-05-28
Anyone else up 4 helpin me? It seems Nateman's gone whichever timezone he's in

---

### Post by NateMan on 2008-05-28
The 08 drive will probably be faster. RPMs, data density, and cache determine how fast a harddrive is. RPMs tell you how fast the disks spin to show how quickly they can get to the read/write heads. Data density shows how close the information is together and how far the r/w heads actually have to move. Cache is memory onboard the harddrive that stores some data ahead of time to improve performance, normally 8mb or 16mb now  a days. 

7gigs would be fine for you / partition. Put your / drive on its own ide bus. Then place the other 40 and 80 gig drives on the other cable and use one of them for you home partition. You can put the swap file right on the first harddrive your using for root since it will have its own ribbon cable. That will probably be faster than placing it on a shared cable. For your swap file, I'd recommend 1 or 2 gigs, you'll probably never use it, but why not? you have some space to spare, whats a gig lately?
This would be a good scheme:

First cable--|40gig 08- sda1  /    38gigs
                        sda2  swap 2gigs

             |--80gig   - sdb1  /home
 Same cable--|
             |--40gig   - sdc1  /media/40gig

---

### Post by garethsimpsonuk on 2008-05-28
I could be wrong but I thought the root and swap would be the most accessed drives so having them on separate cables would be better So they're not competing.

home & swap on 1

root and the other drive on 2.

But then again when I access the server I'll be requesting / writing data from home or other drive so I don't know.

The question is whats more important accessing the root for the os or my home directories for the data the OS is manipulating? i really don't know.

Anyway unless there's a reason not to I think I will use your method but put / and swap on separate ribbon cables.

---

### Post by NateMan on 2008-05-28
Well... if there weren't two drives on the seperate ribbon cable then it would be ok. Plus swap doesn't get written to as much as you think, esp since it will be a data storing machine. Having them on the same drive with it being the only drive on an ide cable would be preferable over having swap, media, and more media traveling over the same ribbon. Then you'd have 3 partitions running over one cable, where as if you place swap on your / drive then you will just have two partitions. Does that make sense?

---

### Post by NateMan on 2008-05-28
oh yeah about certs... I had my a+ and cisco network certifications after highschool, but those are old now, and out of date. I'm now a junior working on my bs in CS.

---

### Post by garethsimpsonuk on 2008-05-28
Wow computer science what's it like? Is there a lot of mathematics invloved? I'm in the territorial army (Royal Signals) and my jobs setting up radio comms, eventually will have skills / certs that will help me greatly in obtaining my CCWNA which is why I'm considering switching over to networking as I'm still young enough. The thing is I'm over a year in to my design course and I've grew up building websites so I would be stupid to throw it away. I don't wanna fall into the trap of being a jack of all trades, and should specialise in one area.
How long is the A+? I'm thinking of just buying the books, learning with them and paying for an exam.

N e ways yea I think you're right about the media more important than swap. Especially doing torrrents although the bottleneck will be the net connection (i got 8mbit is this true? although i have a sneaky suspicion that our adsl line can only accept 4.5)
I noticed that the swap usage is pretty low even with gnome, although this wasnt nowhere near a heavy load. What stress tests / diagnostic tools do you recommend?

N e cool ideas that I can use my spare linksys BEFW11s4 switch / w-router for? Maybe an extension of the wireless network for upstairs for better signal? Is this possible? Or to have connected to printer and scanner so they can be connected wirelessly? I doubt this is possible.
Also is it possible to set up a bluetooth network with Ubuntu? so we can access the network with phones & bluetooth headphones ( streaming ), is bluetooth physically faster than wifi?
(I do Google by the way it's just a point of discussion, i'm not just being lazy!)

Thanks again

---

### Post by garethsimpsonuk on 2008-05-28
Ok after just finding out I have a 80 wire cable AND a 40 ( i thought they were one or the other, in my case 80 ) and that the 80 gives better performance.
Also that the master should be on the end for the 80 and in the middle for the 40. I've taken them all out and checked the labels off all drives and have learnt that the rpm varies quite a bit.

This is what I've come up with:

[_40GB_]  ----------------------------------------------------------------[_4GB_]---------------------------1--(80 ribbon)--]PC
 
^ /(7GB), Swap (2GB), /Home (31GB) - - - - - - - - - - - - - - - -- - - - - ^ /Media/Business - - - - - - - - - - - - - - - - -  


[_CD/40GB_]---------------------------------------------------------------[_80GB_]--------------------------2--(40 ribbon)--]PC

^ /Dunno bacula backup maybe? (40GB) - - - - - - - - - - - - - - - - - - - -^ /Media/Torrents (80GB) - - - - - -- - - - - -- - 

80 ribbon = master on the end
40 ribbon = master i the middle

This is so the 2 most critical drives are on their own cable (root / swap & torrents)

I've probably thought well too much into this because I want it to be perfect! I'm not doing another reinstall!

I value your opinion Nateman but the beauty of forums is that you can have different ppls views and approaches so if n e 1 else has followed this this far what do you think?

Cheers

---

### Post by NateMan on 2008-05-28
I know there are bluetoth apps for ubuntu, but no idea about its setup. Yes, using your spare wifi router to add range upstairs is a good idea. Now for using a printer and a scanner on the network, you could hook them up to your server, or get another computer and use it just to be a network print server.

---

### Post by garethsimpsonuk on 2008-05-28
having major issues detecting the drives after moving around I hope I aint fried them wiv static

edit: one of my disks is showing up as a 2.2 gb FAT32 whats going on! I should've just left it

do u know a way of viewing the disks without having to go through the setup CD? I wuld need MD-Dos or summink wouldn't I?

---

### Post by NateMan on 2008-05-28
Can you post any sort of output from your machine? Is there currently an OS installed? Its normally pretty hard to fry harddrives with static now a days. Did you check to make sure the connections are solid? What sort of procedure did you use when you moved them?

---

### Post by garethsimpsonuk on 2008-05-28
Well at first I arranged drives as stated and gently put them in the two drive housings. I had taken the CD drive off it's original cable and on to the other. (which is replacing one of the 40's for the install)

The first time I booted up the Hardy CD and only 2 of my drives were detected instead of all 3. So I restarted.

The second time I tried unplugging all but my no1 master (which is a faster 1 but 1 that wasn't in the box b4 but it was in an pxe booting shop till and it worked)
This time the bios displays bootfailure during startup.

The third time I tried putting back in my orignal 40GB and the 4GB. They showed up but the 4GB was displaying as FAT32 & a smaller size ( I think this was the size of the partition)

I need to keep trying each drive / jumpers to diagnose the specific fault but it takes a while to get to the partitioner in ubuntu install CD.

I'm gonna try a windows disk as it ask for partition info first.

---

### Post by NateMan on 2008-05-28
You could try a live disk and then check and see what devices are attached in your /dev.

---

### Post by garethsimpsonuk on 2008-05-28
right I've used a windows disk and have picked up my 80GB and 40GB on idividual ribbons. I'm gonna try and add the 3rd drive now and see what happens. I hope when I put the ubuntu cd in it sees them to

---

### Post by garethsimpsonuk on 2008-05-28
yea that's a good idea with the live cd. i'll remember that for next time, hopefully I dont need it now, just waiting for the windows install CD to boot

---

### Post by NateMan on 2008-05-28
yeah no point in taking a long time to download. I will admit however that ubuntu's live cd isn't my favorite for that job. There are plenty of other distros specifically designed to help someone recover a lost system. I have what seems to be a windows 98 cd at first boot, but it contains a linux install and numerous harddrive and memory tools which can be booted into memory. Saved me too many times to count.

---

### Post by garethsimpsonuk on 2008-05-28
F#$%&n B"|#$&d Computers I hate them!!
it doesn't pick it up and the size of the 80 changes to 12 when I plug the third in. I've never seen that in before. Who the invented the jumpers on drives? It just makes one extra thing that need ruled out.
I think I should just try n remember and set it up how I had it. Luckily these posts will help me

---

### Post by garethsimpsonuk on 2008-05-28
I've got live cds like russix and Nubuntu, but they've got hundreds of apps on so will take ages to boot.

Yep the drive shows up as 12146MB (its really 80gb) when I plug the third in. This is very strange

---

### Post by NateMan on 2008-05-28
yeah I normally use cli recovery distros, its very rare that I need the full desktop to backup stuff or fix most issues. How many ide (I assume thats what your using) ports do you have? Which ide port (primary or secondary) are your drives plugged into? Also how is your cdrom drive attached to this as well? I know sometimes that cd-roms don't like to be on the same port as hard drives. Just give me a simple text layout of your motherboard and I'll do my best to assist.

---

### Post by garethsimpsonuk on 2008-05-28
Ok thanks. I have two IDe cable plugged into the mother board with 2 plugs on each cable, I'm using all sockets. One with a cd dvd drive and a hard disk and 1 with 2 hard disks. It all worked fine and I had even unplugged the CD drive and used 4 disks before.
One of the cables has 80 wires which has master cd-rom and slave cd-rom written on the cable labelling each plug. The other cable has 40 wires and has nothing written on them and has a blue plug going into the motherboard all the other plugs are black and there is no labels on the 80 wire.
I took the CD drive off the cable with CD-rom written on it and plugged it as slave on the 40 cable (believing the 80 wire would give a faster transfer rate and therefore would be better for the critical hard disks).
Although the CD drive still boots maybe it has to be on the cable labelled cd-rom m / s.
Also it seems to be 1 of the 40gb drives that is causing issues. When I plug it in with another drive on the same cable the capacities are wrong. When I plug it in on it's own it's showing up as 4GB (the 4GB drive isn't connected at all.)
I'm gonna try and connect all up without the suspicious disk.
Thanks for your help once again. 'If it aint broke don't fix it' why didn't I stand by this statement lol

---

### Post by garethsimpsonuk on 2008-05-28
ok i unplugged the dodgy drive, put the cd drive back where it belongs and it seems to be ok. I'm plugging the dodgy drive back in to see if goes wrong again

---

### Post by garethsimpsonuk on 2008-05-28
ok it's true my 40GB Samsung drive is playing pranks on me. It looks like he's retired now (or just wants to run at 11GB). I'll get everything up and running and maybe have a look at the drive on another box.
What a nightmare that was

edit: now i plug the 4GB in and it's showing up in windows installer as: 

-: Partition1 [Dynamic Volume]   2059 MB < 0MB free>

Whats that all about? I press enter on it and windows says it cant install this but you can delete and format. I choose format and it's only like 2096 MB. So this is now looking like it's not the drive and maybe that 1 connector. The plastic on the plug is a lil but cracked maybe it's this?

---

### Post by garethsimpsonuk on 2008-05-28
While messing around with the disks using windows installer. Somehow Server 2003 started to install. It just can't let go can it lol

---

### Post by garethsimpsonuk on 2008-05-28
If anyones following this I'm booting back into the ubuntu install cd now. It looks like I've lost 40GB from my server but that's ok cos I found a fiver today so it's not all bad!

---

### Post by NateMan on 2008-05-28
Yeah bad cables can cause a world of problems. I would get some new cables and re-attempt. I'm sure you know someone who has a few ide cables laying around unused. Shoot, I've a ton of em in a box. 

Oh by the way, CS is a ton of math and programming theory. I like it though, its very entertaining.

---

### Post by NateMan on 2008-05-28
By the way, I always use 80pin cables for harddrives exclusively, it is a superior connection.

---

### Post by garethsimpsonuk on 2008-05-28
so can i plug another IDe cable in? and take the 40 out? until tonight I thought that they were identical but obviously not.
I've just set up my partitions, 

40GB = / (beginning), /home, /swap (beginning) - I only set the root partition as bootable flag is this ok?

80GB = /media/torrents. (beginning) (would this be better with JFS? do u think?)

I've left the other drive out for now. I just wanna get it installed and I will check the drives on another box. Will plugging a 500GB drive in via usb be slower than PCI slots? I guess it would. I think I need to go and get another 500GB (is it worth the hassle and money of getting a pci sata controller?) will the bottleneck be at the disks or the connection to the web? If it's the latter I will just got with SCSI.
Sorry for so many questions again..If others are reading give Nateman a break and help me please!

by the way during the boot of the ubuntu CD i caught a glimpse of an a couple of errors ( on sda I think) should I be worried about this? could this just be a dead sector thats not being used? i dont wanna have an 80GB drive and then for it to retire like the 40 (luckyily it was empty!)

---

### Post by garethsimpsonuk on 2008-05-28
great, server is installed. At login prompt I've got errors. fsck died...exit status 8, file system check failed.... A maintenance shell has now been started. Looks like my issue still stands

edit: and its logged me in as root automatically. is that because of maintenance mode?

---

### Post by NateMan on 2008-05-28
yeah if its working now, you can easily later replace the cables, just don't forget where they go!

the bottleneck should be at the web unless you have 100MB/s upload speed. 

Yes it is incredibly worth it to get a pci sata card. The one I showed you works great for non-raid. 

The usb drive will be much slower than your pci bus drives, although theoretically this should not be true, but in real life testing I've found it is. 

Your partitions look good. No reason to go with jfs, stick with ext3. Maybe a /var partition as well? Useful but not necessary if you manually check your log files and disk space.

Why don't you download some sort of program you can use to check your disks? I know I have a cd (mentioned earlier) that has numerous disk tools on it and allows booting. Maybe later tonight I'll make an iso of it and host it for download. I used to have one up, but it was lost in the great 500gig crash of '07. Without knowing the errors then I can't be sure of their dangers. When you get your server up and running immediately  apt-get install smartmontools and check your drive's health.

---

### Post by garethsimpsonuk on 2008-05-28
I tried to fetch the app you mentioned and I get 'command could not be located because '/usr/bin' is not included in the PATH enviroment variable.

I'm gonna plug all the hard disks in onto another right now and see what happens installing on that

---

### Post by NateMan on 2008-05-28
Sounds good. when you get installed run apt-get update then apt-get upgrade then apt-get install smartmontools. I double checked and that is the proper package.

---

### Post by garethsimpsonuk on 2008-05-28
well the three disks are picked by the bios in the bios boot display with correct sizes. I then tried the dodgy disk and it goes into a boot loop and doesn't detect disk in bios. 
Install is going fine (with the three good disks). If everything is fine what could it be? heres my guess - 

the dodgy disk has actually died 

+ something else has gone wrong as I recieved them error messages once the os was installed. maybe the ide cable is damaged (a bit of plastic on one of the plugs has cracked)

the actual motherboard is kaput , i bl**dy hope not

or someones playing a very bad joke on me ( i'm hoping it's this one )

---

### Post by garethsimpsonuk on 2008-05-28
yep everythings installed fine, no errors. ubuntu ran a file system check and it's all gone smoothly.

That means it's the other tower. I'm gonna swap the IDE cables round and try again.

---

### Post by garethsimpsonuk on 2008-05-28
yep everythings installed fine, no errors. ubuntu ran a file system check and it's all gone smoothly.

That means it's the other tower. I'm gonna swap the IDE cables round and try again.

---

### Post by garethsimpsonuk on 2008-05-28
well i didn't swap the cables round, i just done a fresh install back onto my actual server and I get the same errors, so it's defo not the drives. does anyone else have any ideas? well this thread is way too long and i doubt anyones read this far apart from me and Nateman.
the cables in the other tower are different (the plugs are black, blue and grey (i cant remember the difference but i do know it makes them a different type) does this mean they're not compatible? 
one is a 80 ribbon and ones a 40 again. Right now im installing again but have put both drives on one cable ( the one without the crack in it ) to see if that's the problem.

don't you just love troubleshooting..

---

### Post by NateMan on 2008-05-28
Shouldn't be any difference, there are only two main types of ide cables, ones that are designed for cdrom drives (40pins I believe) and the higher density ones designed for harddrives(80pins). Blue normally goes to the mobo, gray to the slave, and black to the master.

---

