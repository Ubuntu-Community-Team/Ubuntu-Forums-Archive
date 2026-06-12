---
title: "Thinking about switching from SSD to HDD"
date: 2013-08-23
forum: The Cafe
---

### Post by Welly Wu on 2013-08-23
I've been thinking about this for quite some time and I wanted to get some opinions before I made a purchase and cemented my decision. I have a System76 Lemur Ultra Thin (lemu4) with a Crucial m4 SATA-3 128 GB SSD and it just isn't enough disk capacity for my needs. I want to be able to take my music library which is about 220 GB of MP3 songs and high resolution FLAC loss less audio files with me on the go without having to carry an external hard disk drive. I've been thinking about saving my Crucial m4 as a backup drive and buying a Samsung SpinPoint 1 TB SATA-2 5400 RPM hard disk drive and re-installing everything starting with Ubuntu 12.04.3 LTS 64 bit and all of my favorite software applications. I thought that 128 GB SSD would be enough, but it turns out that I'm missing a lot of software applications because I can't get everything to fit on one disk and I'm longing for a high capacity hard disk drive whereby I can install all of my favorite software applications with plenty of disk space for media files. I did this previously with a Toshiba 1 TB 5400 RPM SATA-2 hard disk drive, but I had to take it out and give it to my father because he needed it to store his media files. I know that there is a tremendous difference in speed and performance, but at this point I can take the performance hit in order to gain a huge advantage in available disk space.

I could justify the purchase of a 960 GB or 1 TB SSD, but it will take quite some time for me to save up enough money to buy one. I'd rather put those hundreds of dollars in my bank account toward the purchase of a newer System76 notebook PC in the future. I haven't ruled out this option, but it's a distant one for me right now.

I'm not entirely sold on SSDs. Sure, they're fast as hell, but having to carry around an external 2 TB hard disk drive is a pain in the butt. I want everything to be stored locally on my System76 PC.

Do you think I ought to do it or should I not do it?

---

### Post by zero2xiii on 2013-08-24
Hay,

I would say unless you ACTUALLY NEED the performance of the SSD, dump it. Get yourself a decent size drive and get on with life.

The only people who really NEED SSD drives are maybe: Professional video editor; HUGE multi track audio editor, recorder, mixers; Maybe (although I doubt it highly) hard core gamers; people with huge ego's that want to say "oh look how fast my system boots"...

You need space, get a HDD. You need speed, stick with the SSD.

My opinion.
Cheers

---

### Post by stephane3 on 2013-08-24
If you have one optic bay you can buy a bay to put a 2nd HDD on laptops, not sure if System76 sell that but its worth a search :)

---

### Post by rrnbtter on 2013-08-24
Greetings,
Welly Wu, If you can afford it I would suggest you buy it today, either way you decide. I was involved with the computer rush from MSDOS all the way to WinXP and it didn't make since to me to chase hardware. You will always be doing without today waiting for tomorrow. When tomorrow's hardware arrives, what you have been waiting for will be obsolete. It seems to me that even though the PC market has slowed, the changes are more drastic. Who knows what tomorrows needs will be! Buy it!

---

### Post by Paqman on 2013-08-24
If what you need is tons of storage, get a crusty old magnetic drive for now and upgrade to a big SSD when the price has come a bit. Personally I love SSDs and don't find myself too limited by them, but my needs obviously differ from yours.

How much storage do you actually need though? Does your laptop have an SD slot? You can get SD cards up to 128GB now, and if it's just data you're reading (eg: music) an SD will be plenty quick enough.

---

### Post by Welly Wu on 2013-08-24
I got my original Toshiba SATA-2 1 TB 5400 RPM hard disk drive from my father today. I haven't re-installed everything yet because I'm tired from helping him to move out to an apartment with my family and friend's help. I'm thinking this over tomorrow to evaluate my storage needs.

128 GB SDXC cards are a no go with System76 laptops and Ubuntu 12.04.3 LTS 64 bit. I tried it and never got it to work right.

---

### Post by Welly Wu on 2013-08-25
Anyone here have the new Crucial m500 SATA-3 960 GB Solid State Disk or Samsung EVO SATA-3 1 TB Solid State Disk? I am thinking about getting either one of these high capacity SSDs this holiday season or sooner.

---

### Post by mJayk on 2013-08-25
External HDD an option at all?

---

### Post by Welly Wu on 2013-08-25
I have two external hard disk drives:

1. Seagate FreeAgent Desk GoFlex 3.00 terabyte Super Speed USB 3.0
2. Western Digital My Passport Portable 2.00 terabyte Super Speed USB 3.0

I haven't used my Toshiba 1 TB 5400 SATA-2 laptop hard drive yet. I had to help a friend to do a system recovery for his HP desktop PC running Microsoft Windows 7 Home Premium Service Pack 1 64 bit. I may get to this project next week.

I already have my media library and confidential files stored on my external Seagate hard disk drive. I have a backup copy of my media library on my Western Digital portable hard disk drive. I think I'm good for now. I might wind up forgoing the Toshiba 1 TB hard disk drive and I may get a Crucial m500 960 GB SATA-3 Solid State Disk. I don't want to re-install Ubuntu from scratch along with all of my favorite software applications twice by the end of this year.

---

### Post by ssam on 2013-08-25
Can you fit a HD and SSD in there (you can on some laptops like x series thinkpad)?

Have you looked at the hybrid drives, they have large HD and a small amount of NAND to act as a cache.

Also be sure to check drive hight when buying a 2.5" drive for a laptop (usally 7mm or 9mm). Most of the 1TB drives are taller and will not fit in small laptops.

---

### Post by AllenGG on 2013-08-25
Hola to Welly and others,  RE SD XC cards DO work very well in Ubuntu. You need to make a very small addition from the repository.  ( Fuse )

refer to : Want to use the exfat system on a new SDXC  memory card, 
This works, came from here:  
[http://superuser.com/questions/436368/how-to-open-exfat-ssd-in-ubuntu-12-04](http://superuser.com/questions/436368/how-to-open-exfat-ssd-in-ubuntu-12-04) 

[TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: answercell"]     exFAT is a proprietary file system  developed by Microsoft, and implementing it requires accepting a very  restrictive license from Microsoft. However, there is a FUSE [implementation]("http://code.google.com/p/exfat/") of exFAT for linux.
  Since you are on a Ubuntu system, you can install the above-mentioned exFAT implementation from their [PPA]("https://launchpad.net/%7Erelan/+archive/exfat").
  
[LIST=1]
[*]Add the PPA to your sources list by running
  sudo add-apt-repository ppa:relan/exfat
  in your favourite terminal emulator 
[*]Install the fuse-exfat and the exfat-utils packages:
  sudo apt-get update && sudo apt-get install fuse-exfat exfat-utils 
[/LIST]
  Now you should be able to use the SSD
 
     [TABLE="class: fw"]
[TR]
[TD="class: vt"][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
  Note to Welly, I use a 64Gig sc XC card, super fast, very tiny, and sturdy.  Check Amazon, Tiger Direct, Newegg etc.[IMG]http://ubuntuforums.org/images/icons/icon6.png[/IMG]

---

### Post by Welly Wu on 2013-08-25
I already know about that. I'm talking about 128.00 GB SDXC cards. System76 does not support them for their current generation Lemur Ultra Thin (lemu4) notebook PCs. I already created a support ticket and did extensive troubleshooting with them on this issue. I added the relan exfat PPA and it did not work with 128.00 GB SDXC cards.

Besides, I want to format it to /ext4 and encrypt it using LUKS. System76 says that this configuration is not supported in Ubuntu for 128.00 GB SDXC cards.

64 GB SDXC cards do work, but it's too small for me. They're affordable though.

I already have a Kingston DataTraveler HyperX 128.00 GB Super Speed USB 3 thumb drive. It's formatted to /ext4 and encrypted using LUKS.

Ditto for the WD and Seagate hard disk drives.

I try to encrypt almost everything that I have in terms of digital files.

---

### Post by Welly Wu on 2013-08-25
I tried it. The hdd is really really slow as molasses. I re-installed Ubuntu 12.04.3 LTS 64 bit and it's as slow as Windows 7. I thought Ubuntu was supposed to be faster than a PC and prettier than a Mac? I guess it's truth in advertising at it again. I'll keep the hdd as a backup disk drive in case my Crucial m4 SSD dies, but I strongly prefer not to use the hdd.

---

### Post by ikt on 2013-08-26
> **Welly Wu said:**
> I want to be able to take my music library which is about 220 GB of MP3 songs and high resolution FLAC loss less audio files with me on the go without having to carry an external hard disk drive.

Any reason why not spotify/google music etc? That sounds like it'd eliminate a huge space taker.

---

### Post by Welly Wu on 2013-08-26
I already subscribe to Netflix, Hulu Plus, and Spotify Premium. You see, I'm a media buff. I value the arts and entertainment as I'm willing to pay for my premium content. I also have more than 2,750 electronic books for my Amazon Kindle 3G + Wi-Fi e-book reader and I have hundreds of digital magazines in Adobe .PDF format and through Zinio.

My goodness, I have 6.5 terabytes of storage capacity in SATA-2, SATA-3, and Super Speed USB 3. I just have the desire to collect digital media content. Don't try to attack me. I used to be a Systems Administrator, security analyst, and penetration tester for the US Department of Defense specifically the National Security Agency. I've hardened my Ubuntu 12.04.3 LTS 64 bit installation to the maximum capability possible. I monitor my own network traffic constantly and I know how to take offensive and defensive countermeasures. I can call my friends from my former employer for help and assistance.

Besides, I doubt that you'd like my musical and movie preferences and I doubt you read as many books or magazines as I do. I have rather esoteric interests given my former profession.

I prefer to stream content as much as possible as I have Verizon FiOS Quantum fiber optic Internet access, but I do rely on my huge private media library from time to time.

I tried the Toshiba 1 TB HDD and it's dog slow. I don't like it, but I can't say that I'm surprised. SSDs spoiled me rich. The speed and performance are wonderful and I'm likely to buy a high capacity SSD by the end of this year. I'm retired and disabled now, but I have significant assets and I still have significant income sources coming in each week.

I'm thinking that the Crucial m500 960 GB SATA-3 solid state disk is my top choice right now. I'm also looking at the Samsung EVO 1 TB SATA-3 solid state disk. If I get approved for credit this week, then I might place my online order and use 12 months of financing to pay for it by the end of September 2013.

I would rather not have to install Ubuntu 12.04.3 LTS 64 bit more than twice in less than 6 weeks. I just installed it this past Friday from scratch. I hate re-installing operating systems and my favorite software applications from scratch even though I document all of my work carefully so that I can pinpoint technical issues and resolve them precisely. It's not fun to re-install everything from scratch as it's a lot of significant work. I don't trust imaging software to do it as a full re-installation usually produces the best quality results. My needs do change with each installation so I have to re-evaluate my software decisions.

Then again, I may decide to get a newer System76 Galago UltraPro with a Crucial m500 mSATA SATA-3 240 GB SSD and a second Crucial m500 960 GB SATA-3 SSD. It would be expensive, but I could afford it early next year in February 2014.

It's 4:48 AM EST so I just woke up and I'm contemplating ideas.

Another option is a solid state hybrid disk. Seagate sells their Laptop Thin 2.5" 9.5 mm 1 TB SATA-3 with 8 GB MLC NAND FLASH 5400 RPM hard disk drive for under $130.00 USD. I haven't tried it yet, but I understand that it's almost as fast as a real SSD in terms of boot, reboot, and shutdown performance. Otherwise, it performs like a standard 5400 RPM hard disk drive for regular usage. It has adaptive learning algorithms so it gets faster and faster after 1 week of time using it. I often do repetitive tasks in Ubuntu 12.04.3 LTS 64 bit so a SSHD would speed up my System76 Lemur Ultra Thin (lemu4) significantly without costing a large sum of money compared to a 960 GB or 1 TB SSD. I've seen reviews of these SSHDs and they're quite promising.

We shall see what I do. I may revert to the Toshiba HDD later this week to re-evaluate my options. If I can compromise on speed and performance in return for huge storage capacity, then I may wind up doing that.

---

### Post by Isaacmarritt on 2013-08-26
why dont you just get a hybrid drive so you can have both. Thats what I got in mine and it boots uber fast and has 750 gb of storage

---

### Post by Welly Wu on 2013-08-26
I'll give it more consideration this weekend. I'll have the extra money available next Monday and I can purchase a new Seagate Laptop Thin 2.5" 9.5 mm 1.00 terabyte SATA-3 5,400 RPM with 8 GB MLC NAND FLASH solid state hybrid disk from NewEgg.com for $100.00 USD plus New Jersey taxes and shipping fees. I need to evaluate my storage needs this week as I plan to download and install more software applications and perhaps some Steam for Linux PC games as well. We shall see.

---

### Post by Welly Wu on 2013-08-29
Well well. I just got approved for an Amazon Store Card and my credit limit makes it very easy for me to afford the Seagate Laptop Thin 1 TB SSHD. I'll wait until next Monday to see if I really need it or not though. I'll have the money at that time. I'm getting my disability direct deposit every 3rd of the month so I can shop for a high capacity SSD in late September 2013.

I want to be able to download and install all of my Humble Indie Bundle and Steam for Linux PC games. This is why I need a high capacity disk.

I'm not entirely sold on the high prices for SSDs. I think that SSDs are a bit over rated and hyped because they offer such low capacities for more affordable models. A SSHD might be the only compromise that I can afford to make right now. My understanding is that it would take about one week for the intelligent algorithm to cache my frequently used files in the 8 GB MLC NAND FLASH for it to make a noticeable difference in terms of performance.

128 GB is sufficient for my needs, but I have to do without installing a lot of favorite software applications and especially PC games. If I want to be able to keep purchasing and installing more PC games, then I'm going to need a 1 TB disk whether it be a SSHD or SSD.

I'll have to think this over because I want to make this the last time I re-install Ubuntu on any PC from scratch. I worked hard to get my existing installation just the way that I want it to function and every time I re-install an OS and software applications from scratch, something changes and it's not identical to my previous installation. It becomes a chore to figure out what's still missing even though I have excellent documentation and step-by-step procedures for all of my favorite software applications. It takes me about 5 - 7 days to re-install everything from scratch to resemble something similar to what I had before.

---

### Post by Welly Wu on 2013-08-29
By the way, can I get more reviews for SSHDs from actual users here in Ubuntu Forums?

I know that SSHDs speed up boot, reboot, and shut down times after 4 cycles, but do they improve the performance of loading frequently used software applications as well? I'm thinking that 8 GB of MLC or SLC NAND FLASH isn't enough for everything to be cached at once.

Should I stick with my Crucial m4 SATA-3 128 GB SSD or should I get the Seagate Laptop Thin SATA-3 1 TB 5,400 RPM SSHD? Is it going to be a major downgrade in terms of performance in order to gain a huge upgrade in storage capacity? Is it that dramatic?

---

### Post by DarkAmbient on 2013-08-30
You should do it, is my opinion. I'd switch at once If I could, I tried when I bought my laptop my new laptop a month ago. But It had no "service-hatch" for replacing the storage-device, cracking the shell open to do that would void the guarantee. So I sticked with my hdd. Harddrives really is the bottleneck on most laptops, sadly enough.

---

### Post by Welly Wu on 2013-08-30
I installed Leisure Suit Larry and Team Fortress 2 from Steam for Ubuntu Linux and I'm left with exactly 56.80 gigabytes of available disk space on my Crucial m4 SATA-3 128.00 gigabyte solid state disk right now.

It's not a lot of available disk space.

I plan to purchase the Valve Corporation Source Complete Game Pack and Penumbra PC games. I don't plan to download and install everything, but I wish that I could do that.

Here's the thing. I decided not to transfer my huge media library to my internal disk drive on my System76 PC. It's just redundant. I have an enormous amount of high speed Super Speed USB 3 SATA-3 external hard disk drives totaling in excess of 5 terabytes. That's where I store my massive media library.

I got Spotify Premium, Netflix, and Hulu Plus subscriptions. The software is already installed in Ubuntu 12.04.3 LTS 64 bit.

I got Verizon FiOS Quantum 75 MB/s download and 35 MB/s upload Internet access and Private Internet Access VPN.

I'm thinking about doing this after all. I just can't decide to get the Seagate Laptop Thin 1 TB SATA-3 SSHD or a Crucial m500 960 GB SSD. I could afford to get both if I wanted to get both, but I'm still debating whether to get the Crucial m500 960 GB SSD. It's actually quite affordable for me. I would just have to wait until October 1st, 2013 or a few days earlier to get it using my Amazon Store Card.

The good thing is that I can swap it out if I get a new System76 notebook PC in August 2014. I can swap in my existing Crucial m4 128 GB SSD back into my older System76 Lemur Ultra Thin (lemu4) so I'd have two notebook PCs with SSDs. Everything is 64 bit now in terms of PC CPUs.

I know myself well enough to say quite accurately that I'll be purchasing Ubunt PC games on a weekly basis. I've got the money for all of this. I just need a high capacity terabyte class internal disk. I already have an older Toshiba SATA-2 1 TB 5,400 RPM hard disk drive stored in my Sentry Safe in my bedroom as an emergency backup disk in case of total failure. I also have 4 GB of PC3-10600 1,600 MHz SODIMM RAM in case of failure. I got a second Lithium Ion battery as backup too.

I'll have to think this through more carefully. What I'm dreading is to re-install Ubuntu from scratch all over again in less than one month. It's a pain to do this again. I never can seem to get an identical installation no matter how well I documented everything in my LibreOffice Writer documents.

---

### Post by Welly Wu on 2013-08-31
I keep reading reviews that the sequential data transfer rate for SSHDs is slightly worse than conventional 5,400 RPM HDDs. It's also much slower than 7,200 RPM HDDs. I do a lot of very large copying of large files in excess of tens of gigabytes so this is a major concern for me. I'll have to keep reading reviews to figure out if I should get a SSHD or not.

---

