---
title: "Linux for the girlfriend and mom"
date: 2007-03-13
forum: The Cafe
---

### Post by hotspoons on 2007-03-13
So I'll start this with my geek credentials...I'm 27, been a computer user since the age of 4 (I learned to read by copying programs in Basic from a book to the trusty Timex Sinclaire 4K computer in 1983 and saving them to a cassette deck), and have been a linux user since 1999, but it hasn't been my main OS until 2004. My entire career has been in IT, mostly in programming and network administration.

Anyhow, I'll start this thing with the mom. It is actually because of my dad...he has always been a fan of using a computer, but not of learning anything above and beyond using MS Word and Internet Explorer, and has depended on me as his private IT department; times were hard for him while I was away at college, but RDP and port forwarding helped a lot of the time. However, he enjoys using his home office (he is semi-retired) computer as his fun-for-everything computer, as well as his data center, and has suffered massive catastrophe at the hands of viruses, malware, and hard-drive failures on multiple occasions. The last time he had a major catastrophe in 2004, I demanded that he use something more immune to malicious software, having a basic level of data redundancy, and separate from his main (then and now) Windows XP Professional workstation. I found a hell of a deal...$237 for a Dell Poweredge SC420 server (2.5 GHz celeron, 512 MB ram, 80 gig drive, no sound, integrated Intel video), and it came with no OS, so I used what I knew from years before...Redhat...more specifically Fedora Core (1 or 2...never used it since). I also had a Silicon Image PATA soft-raid controller laying around as well with a pair of identical 160 GB drives, though I never figured out how to set up a soft raid in FC.  Shortly after installing it, attempting to add a few packages to make the PC have more functionality than just a SMB file server, I broke the package pool. I reloaded it, and the same thing happened. I became so frustrated that I tried 5 or 6 different distros, and finally cam upon something called Ubuntu...5.04 RC3 to be exact, with the KDE desktop installed. But it worked, and worked wonderfully, and remained my dad's file server (the main share was mapped directly to 'My Documents' on his PC) for close to two years with no modifications above an occasional update, and with very little digging, after loading it, I was able to configure DMRaid to set up a mirrored soft RAID where which my father's precious 'My Documents' resided.

Anyhow, my mother started using my father's computer more (they would fight for usage of the Windows XP box), and KDE was not to my mother's neophyitical liking. On top of that, a net bot guessed the password of an account I set up on the computer and had forgotten about (I think I set the username and password to be the same and never bothered changing it for my mom after I initially set up the PC), and with port 22 and port 80 forwarded to the computer, it was compromised and used as a spam server for a day or two. Whoops. But the computer had never been usable for much else besides a server anyhow. And my mother wanted her own PC. By now it was December 2006, and Edgy had been around for a bit, so I decided to apt-get dist-upgrade to dapper, then edgy. And magically it worked. It just worked. With a wounded and beaten computer, everything worked. And I set up Gnome, which had improved orders of magnitude since I had last used it, and my mother instantly took a liking to it. And Wine allowed me to install Southwest Ding!, which I deemed not possible before.

To the girlfriend...the girlfriend had not had a home computer in years. Her last computer, ca. 1998, was in her mother's basement, hundreds of miles away, with a hot hot load of Windows 98, first edition residing on it. I have a pile in a room, floor to ceiling, several feet wide, of old computers and computer junk. I was able to throw together a computer consisting of an Athlon XP 1700, Riva TNT video, 256 MB DDR Ram, a several year-old 120 GB hard drive, and a spraypainted black case with ultra-violet LED's I put in myself years before. I figured all of the parts in it were worth maybe 150 dollars (that's about two nice bouquets of flowers delivered). But instead of installing a volume-licensed copy of Windows XP (pre-service pack one) I obtained from college years before (for $5), I deduced that though she knew enough about a computer to at least give something new a try. She's not that technologically apt, so when I tried to explain to her that her PC (loaded with Edgy) was more like Mac and less like Windows because it was Unix based, she thought it was a Mac. Go figure. She just wanted to load her iPod with music she ripped from her own CD's, download pictures from her camera, occasionally use office software, and browse the web. And in a long afternoon, during which if I was loading a windows PC, I would still have been in the process of 'downloading and verifying service pack 2', I had completely loaded her PC to most of the state it is in today, able to play any media file she throws at it, manage her iPod, and do anything else she could ask. She still doesn't know how to use picassa, and has never opened a shell before, but she's on it for a couple of hours a day, so something must be right. I got bored with her PC after a month because it seemed kind of slow, so I spent a whopping $97 on an Athlon 64 3400 and GeForce 7300LE from New Egg (I had an Athlon 64 939 pin motherboard laying around with another 256 MB stick of DDR ram), and after installing Beryl and the Nvidia driver, and running a long  audio and VGA extension cable to her 32" LCD HDTV across the room, she also had the HTPC capability (which is yet to be used...she enjoys playing mario 3 in Mednafen, but only at her computer chair), as well as graphical capabilities that made her mother's Windows Vista Home Premium PC w/ Aero look dated by a couple of years (yes, she knows how to use the cube, but she doesn't really use it much...she is mesmerized by the exploding windows effect though). She hasn't complained that she wants Windows in a long time, which means with a properly configured system (albeit with some proprietary and not-legit-in-the-us software), a new, unexperienced linux user became comfortable, and sometimes pleased (it was a very very easy process for her to rip her CD's to her iPod using sound-juicer and rhythmbox). And it is hooked up, ready to send HDTV to any client in her house via Firewire from her Motorola QIP6200 box and MythTV, though she doesn't need it per se.

Oh, and on my mothers 2.5 year-old super-cheap Dell SC420 server, I modified the PCI-express 8X slot with a blow-torch, a box cutter, and a screw-driver (I **** you not) to take a PCI-express 16x card, and got her the same GeForce 7300LE card I bought for my girlfriend, installed it with no issues, and for $40, that PC runs bleeding edge graphics (Beryl) as well. And my mother is mesmerized by the wiggly windows and the zoom.

So that's my story of a mom and a girlfriend, forced into linux by their brutish son/boyfriend.

---

### Post by GreenHawkIA on 2007-03-13
Nicely done!

---

### Post by godd4242 on 2007-03-13
Well played.
However, I hate you for getting Beryl to work.
It doesn't like me ;_;

---

### Post by nalmeth on 2007-03-13
I'm impressed,
> Well played.

---

### Post by kevinf311 on 2007-03-13
That's an awesome story.

It's amazing how well jerry-rigging things works. Just tonight I fixed our... couch (I'll attach a picture to save the 1000 words) with speaker wire, aluminium foil, and electrical tape. Some people were moving it outside and the battery fell out, taking all of the power connections with it. The pin for the negative wire broke and the stripped speaker wire + aluminium foil is doing well for a stop-gap fix.

The computer I built for my Grandparents runs XP Pro because at the time it was what I was most proficient with. My grandmother can do e-mail, web search, and word processing pretty well. When that XP install bites the dust, I plan on switching it out for Linux. Probably a KDE distro so I can dress it up like XP easier. 

I'll be moving back to my parents house for a bit this summer and I hope to entice my mother to use Ubuntu. She is anti-computer. This also means that she is completely untouched by the mainstream conditioning ;)

---

### Post by hotspoons on 2007-03-13
> **GreenHawkIA said:**
> Nicely done!

Thank you, I do my best!

> **godd4242 said:**
> Well played.
However, I hate you for getting Beryl to work.
It doesn't like me ;_;

The price of entry for flawless performance and stability on modern platforms is a GeForce 7300LE graphics card ($37 last I checked on newegg). If you want in it 42 inches of 1920x1080 LCD panel glory, my 7950GT card does marvelously (plus the 2.13GHz core2 duo and supporting hardware, stuffed in a sweet looking toaster-sized box). The last ATI card I tried on Linux was a 9600 pro, and it wouldn't accelerate XvMC (on an otherwise underpowered MythTV HDTV box), so I deemed it with a less-than-enthusiastic driver developer (private, ATI/AMD) and I never looked back, and replaced the superior 9600 pro with a 5200 something rather that cost $33, and made deinterlaced 1920x1080 HDTV more than watchable on my dad's Athlon XP 2700 MythBox...

Get a 5xxx series GeForce card or better , and merely following any of many Beryl/Compiz how-to's out there (usually adding argb visuals to xorg), installing and running beryl-manager will bring you much joy. And perhaps the joy of your girlfriend or mother who is stuck with you as their builder-of-PC's.

---

### Post by graabein on 2007-03-13
Nice story. Thanks for sharing! 

I have already converted my mom to Ubuntu but my father still use Windows XP. He is too occupied with an assortment of work-related Windows-only software while mom mainly need card games, some music and an internet browser to pay the bills.

I'm afraid the girlfriend is dependent on Picasa and Photoshop and maybe MSN Messenger and webcam support so I won't try anything there yet. I just remind her to backup her photo collection.

I sure hope Google will continue Picasa development (native GTK version perhaps?) and that Wengo Phone or something comes through for instant messaging with voip and webcams...

---

### Post by hotspoons on 2007-03-13
> **graabein said:**
> Nice story. Thanks for sharing! 

I have already converted my mom to Ubuntu but my father still use Windows XP. He is too occupied with an assortment of work-related Windows-only software while mom mainly need card games, some music and an internet browser to pay the bills.

I'm afraid the girlfriend is dependent on Picasa and Photoshop and maybe MSN Messenger and webcam support so I won't try anything there yet. I just remind her to backup her photo collection.

I sure hope Google will continue Picasa development (native GTK version perhaps?) and that Wengo Phone or something comes through for instant messaging with voip and webcams...

I know for a fact Photoshop 7 and Picassa work flawlessly with Wine. As far as IM software is concerned...don't use it, so I wouldn't know. Everyone these days has gmail chat anyhow.

---

### Post by lwr on 2007-03-13
My parents have been using Ubuntu for several months now, and they're both virtually computer illiterate. Of course they didn't have much choice in the matter. I think all they do is use Firefox and Thunderbird, so in a way it's even easier than Windows because they don't have to look after anti-virus and firewall software. They even manage to switch between Windows at work and Ubuntu at home, and considering how good they are with conmputers, it must mean Ubuntu's very easy to use.

---

### Post by cowlip on 2007-03-13
Re: MSN Messenger and webcams---use AMSN or Kopete for that, they both support cams.  GAIM should get webcam support sometime this year....maybe.

List of supported webcams with spca5xx or gspca: [a ton, even my cheap *** creative cam is]

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

---

