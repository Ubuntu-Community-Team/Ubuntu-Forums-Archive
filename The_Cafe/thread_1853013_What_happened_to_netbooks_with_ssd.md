---
title: "What happened to netbooks with ssd?"
date: 2011-10-01
forum: The Cafe
---

### Post by drawkcab on 2011-10-01
I love my Asus 900a (n270 + 16gb ssd).  I'll admit that I bought it as a toy but I've come to rely on it quite heavily for work and travel.  The 16gb ssd is durable and gives me enough room to install a full linux distro and port a few larger files around.  Unfortunately I abuse the heck out of it and it's getting a bit long in tooth, needing to be replaced.

As I look around for a replacement, all I can find are more expensive netbooks that offer hdd of 160gb or more.  I'd personally rather have the speed and durability of the ssd than 150 gb of space that I'll never use.

_Why isn't anyone offering netbooks with smallish ssds anymore?_  Am I just missing them?  Is it that the ssds are not large enough to house win7?  Is it that marketers want to post a larger number in the spec sheet?  Have tablets effectively replaced this sort of netbook?

All I've been able to find is the occasional refurb on mwave.com.  _Any ideas where I might find a suitable replacement to my 900a?_

---

### Post by forrestcupp on 2011-10-01
> **drawkcab said:**
> Is it that the ssds are not large enough to house win7?  Is it that marketers want to post a larger number in the spec sheet?

I think it's the 2nd thing rather than the first. I have a nettop with a 30GB ssd, and it has plenty of room for Win7 with extra space.

---

### Post by jackyboy633 on 2011-10-01
IMO, I think it is due to the fact that manufacturers want to position netbooks as mini-laptops, not internet devices.

---

### Post by Daveski on 2011-10-01
Just not fashionable I think - which I agree is a real shame. I love my eeepc with a yummy 20Gb on the Linux version (although I installed Ubuntu) it is perfect to chuck in a bag when going somewhere. These were hot devices, now everyone is in tablet mode <sigh>

---

### Post by Copper Bezel on 2011-10-01
Yeah, I'd think that with tablets being limited to the same storage spaces, they'd be more common, but it does seem likely that that the bigger number still sells better. I wouldn't want to use a netbook with a magnetic drive - I've installed an SSD in one for a friend (which was a massive improvement) and got my own Eee with 32 gigs of flash memory. It's plenty of space for my purposes (and an external makes up the difference when I need it.)

To be fair, the Macbook Air 11" is a current netbook with integrated flash memory. = )

---

### Post by el_koraco on 2011-10-01
Buy a netbook, install a 30 GB SSD, use the HDD as an external (the cases are like 20 dollars). That way you can be sure to get yourself a good SSD, not the one the OEM put in there. Hell, I'm not able to fill up 10 percent of my 250 HDD. Might as well sprig up for an SSD instead of buying a new machine, now that I got the graphics sorted out.

---

### Post by viperdvman on 2011-10-01
I too would love to replace the 250GB HDD in my 10" EeePC (mine's an AMD V-series) with maybe an 80GB SSD, enough to run Windows and Ubuntu in dual-boot and add a few things on top of that.

SSD's are so much more rugged, so much faster, and so much more energy efficient (eats less battery). It's sad I can never find netbooks equipped with them anymore.

---

### Post by Copper Bezel on 2011-10-01
Good point. If you don't have an external, you'll need one anyway. The only OEM flash memory I've used is what came with my Eee, but that's an Asus-branded integrated flash chip, not a standard-slot SSD. If OEMS choose SSDs for netbooks by the same set of standards they apply to HDDs for netbooks (read: none at all) installing your own would be quite sensible.

---

### Post by frenchrh on 2011-10-02
Check out the ASUS X101.  Its a $199 netbook that comes with 1 Mb RAM, 8 Gb SSD and Meego. and weighs < 2 lbs.  

     I'm setting up a bunch of these with 2Gb RAM, and Kubuntu.  Works quite well in my initial tests.  

     Just trying to choose my final partioning plan,before installing on 9 of these X101

Any suggestions? 
        1. With only 8 Gb SSD, should I use 2Gb of it for a Swap partition??  Is it necesary, or a waste of space?

        2. Put user files on a 16 Gb microSD card (but don't put the home partition there. just link to it from home/documents

---

### Post by Copper Bezel on 2011-10-02
Eight? As in half of sixteen, which is half of thirty-two? I can't count that low in gigabytes of storage. Yes, put the whole of /home on the SD card. 

Assuming the user is content with hibernate being disabled, then you can reduce swap to 1 gig, but my basic Ubuntu install with some necessities added takes 3.8 gigs out of a 4.5 gig partition. That leaves 2.5 for user data, which is scarcely worth dealing with. Just do 6+2 and leave the options open.

But using the SD card interface for all data is going to lose a lot of the snappiness that the SSD gains in application access. (Which is not to say that your idea is a bad one, but it does make the X101 a little less than ideal for the OP's purposes.)

---

### Post by wewantutopia on 2011-10-02
2GB RAM on a netbook...  don't bother with any swap.  My EeePC with 2GB RAM hasn't had swap ever and I haven't had a problem.  I've even ran a virtual box machine with 1GB allocated with no issues.

---

### Post by michaelcarey95 on 2011-10-02
> **frenchrh said:**
> Check out the ASUS X101.  Its a $199 netbook that comes with 1 Mb RAM, 8 Gb SSD and Meego. and weighs < 2 lbs.  

     I'm setting up a bunch of these with 2Gb RAM, and Kubuntu.  Works quite well in my initial tests.  

     Just trying to choose my final partioning plan,before installing on 9 of these X101

Any suggestions? 
        1. With only 8 Gb SSD, should I use 2Gb of it for a Swap partition??  Is it necesary, or a waste of space?

        2. Put user files on a 16 Gb microSD card (but don't put the home partition there. just link to it from home/documents


You could get by one 1GB Swap, but if the user wants to use hibernate or anything, go with 2GB.  Then set /home to the 16GB SD card, to be plugged in always.  The rest of the 8GB SSD should be used to OS and programs.

---

### Post by viperdvman on 2011-10-02
Now you're making me want to grab me one of those cheaper netbooks with the small 8GB SSD's, just for running Ubuntu on :P 

It sucks that they're hard to come by nowadays, but still. Slip in a 32GB SD card in it, and I have a nice cheap Ubuntu-only netbook for doing minor stuff.

---

### Post by drawkcab on 2011-10-02
> **frenchrh said:**
> Check out the ASUS X101.  Its a $199 netbook that comes with 1 Mb RAM, 8 Gb SSD and Meego. and weighs < 2 lbs.

Yeah, that's pretty nice actually.  It's either that or get one of those 11.6" lenovo thinkpads (x120e) which have dropped to $300 finally.

---

### Post by michaelcarey95 on 2011-10-02
I really love my Dell Inspiron M5030 laptop.  Having said that, I would like to trash it soon.  For one, it doesn't run Ubuntu at all.  I'm stuck with Windows 7.  :(  Eventually, I'd like to get a desktop for Ubuntu only, and a netbook or something similar for taking with me everywhere.  I wouldn't be doing anything too heavy on it.  Mostly just typing notes/essays in school, giving slide show presentations, watching videos, and browsing the web.  Maybe some html coding in emacs.  But I would want the desktop to do all of the heavy things, and perhaps run as a server?  I don't know, but I don't do much heavy things anyway right now.

Perhaps two netbooks?  One of them as a home server for mail and a website?  The second one for everything else. Just have a monitor, keyboard, mouse for at home?  Hmmmmm.  Either way, I need to save money.  I have $0.00 right now.  :lolflag:

---

### Post by el_koraco on 2011-10-02
> **michaelcarey95 said:**
> IPerhaps two netbooks?  One of them as a home server for mail and a website?  The second one for everything else. Just have a monitor, keyboard, mouse for at home? 

If you need it only for netbook type stuff, but want a bigger monitor and it's gonna be stationary, get a nettop. They go for like 300 dollars.

---

### Post by wolfen69 on 2011-10-02
Just buy the netbook that tickles your fancy, and pop in an SSD. Done, end of story.

---

### Post by forrestcupp on 2011-10-02
> **el_koraco said:**
> If you need it only for netbook type stuff, but want a bigger monitor and it's gonna be stationary, get a nettop. They go for like 300 dollars.

I have a nettop, and mine totally sucks. I wish I never would have bought it. It's a great concept, but the hardware stinks. I can't even watch hulu in full screen without it being like 5 frames per second. Also, it didn't take long for all of my USB slots to become corrupted and not work properly.

I have a Zotac Zbox hd-id11. Maybe the new ones are better, but I won't ever be buying another one.

---

### Post by LowSky on 2011-10-02
> **forrestcupp said:**
> I have a nettop, and mine totally sucks. I wish I never would have bought it. It's a great concept, but the hardware stinks. I can't even watch hulu in full screen without it being like 5 frames per second. Also, it didn't take long for all of my USB slots to become corrupted and not work properly.

I have a Zotac Zbox hd-id11. Maybe the new ones are better, but I won't ever be buying another one.

USB slots don't get corrupted unless you have a operating system issue, like malware. Running flash on the older models was always a problem, especially high definition, but the newer models built on nvidia or AMd graphics work much better, especially with Windows.

I actually love my Lenovo S10 (first gen). It's a bit too small but its great for traveling, and lets me works on things my smart phone and tablet still struggle to do. It is funny my phone and tablet can play HD video and my netbook really can't.

I hate to say netbooks were a fad. A place holder until tablets stole the show. Now it seems PC manufacturers are building 15.6" computers for cheaper than 10" netbooks. Most of them run a bit faster too. I think my next purchase will be one of these machines. I have come to the conclusion that my laptop needs a screen bigger than 10", while oddly I need a tablet smaller than 10".

---

### Post by drawkcab on 2011-10-03
> **forrestcupp said:**
> I have a nettop, and mine totally sucks. I wish I never would have bought it. It's a great concept, but the hardware stinks. I can't even watch hulu in full screen without it being like 5 frames per second. Also, it didn't take long for all of my USB slots to become corrupted and not work properly.

I have a Zotac Zbox hd-id11. Maybe the new ones are better, but I won't ever be buying another one.

I have an acer revo with the dual core atom ion and it's ok.  Flash works pretty well actually although I am limited to 720p which is fine.  It's also nice that it's small and very quiet.

The real stinker is the sound though because I'm stuck with analog stereo.  At some point I'm going to have to upgrade to a surround sound system with an htpc that offers better sound.

---

### Post by drawkcab on 2011-10-03
> **LowSky said:**
> I actually love my Lenovo S10 (first gen). It's a bit too small but its great for traveling, and lets me works on things my smart phone and tablet still struggle to do. 

I love my netbook because I can carry it around at all times and complete tasks during the day as they come up.  I need a keyboard so phone/tablet won't work.

> **LowSky said:**
> It is funny my phone and tablet can play HD video and my netbook really can't.

I hate to say netbooks were a fad. A place holder until tablets stole the show. Now it seems PC manufacturers are building 15.6" computers for cheaper than 10" netbooks. Most of them run a bit faster too. I think my next purchase will be one of these machines. I have come to the conclusion that my laptop needs a screen bigger than 10", while oddly I need a tablet smaller than 10".

I could really care less about playing hd video on my netbook.  I really don't have room for the files and I really don't think hd video looks all that great on a 9" screen anyway.  I only use it for vids when I travel and standard def is fine.

I'd like to abandon my netbook and 15" laptop for something in the 11"-13" range and then buy a desktop.  The portability of the netbook is nice but that 9" keyboard is driving me nuts.

I really have no use for a tablet except for reading .pdfs.

---

### Post by forrestcupp on 2011-10-03
> **LowSky said:**
> USB slots don't get corrupted unless you have a operating system issue, like malware. Running flash on the older models was always a problem, especially high definition, but the newer models built on nvidia or AMd graphics work much better, especially with Windows.

You know we were talking about nettops and not netbooks, right?

The one I have does have an nvidia ion2 chipset. These nettops have different problems than netbooks have. You hook them up to your hdtv with an hdmi cord. The problem is the limitation of PCI lanes. If you're using wifi or ethernet and also trying to output HD video to a large TV, it really leaches the limited PCI lane bandwidth, and it starts to choke. So Hulu videos work just fine until you try to make them fullscreen. Other video sites make better use of the GPU. Like HD video on YouTube in fullscreen works much better than Hulu on a nettop.

And as for what you said about USB slots, that's not my experience in this case. I'm basically using this only for watching my ripped DVDs from an external HD, and also some YouTube. I had Win7 installed as the OS, and I didn't install any software or do anything at all that would introduce malware. Over a small amount of time, the USB port stopped reading my video files from the external properly, causing a lot of video junk and skipping. When I switched USB ports, it worked fine for a little while, then it started doing the same thing. So I wiped my SSD and installed Ubuntu, which is 100% immune to viruses. :) Well, guess what? I'm having the same problem. Thinking it might be my files or the external hard drive, I tried playing them from my capable laptop, through the hdmi, and it worked just fine.

---

### Post by forrestcupp on 2011-10-04
Just an update on what I said about my Zotac zbox nettop. Yesterday, I did a clean install of Win7 and installed all of the updated drivers. Hulu now works perfectly in full screen. I'm still having the USB trouble, but since I trashed it for its full screen Hulu, I thought I'd better make that right.

---

### Post by a2j on 2011-10-04
after swapping hdd with ssd in my eeepc, cpu is the bottleneck...

---

### Post by krapp on 2011-10-04
Eee PC 1015-PEM here with 250 GB disk drive. Love it to bits. Not having SSD is not an issue at all. It's presently a waste of money as far as I am concerned.

---

