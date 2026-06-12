---
title: "System76 Serval Professional SERP5 Review + Vista Dual Boot + WinXP VMWare Guest"
date: 2009-08-27
forum: System76 Support
---

### Post by jpongin on 2009-08-27
All remarks and comments are high level with links to low level details.  After Googling and Binging, I couldn't find one comprehensive place that explained the steps needed to setup my configuration.  So, here's my attempt at making someone else's life easier.

System76 Review:
- Great support staff.  They write, maintain, and distribute their own drivers.  This was a major selling point for me.  I'm far too busy to try to hack up a driver myself.
- Competitive pricing.
- Very high end laptops are available.
- Good online support knowledge database: [http://knowledge76.com/index.php/Main_Page](http://knowledge76.com/index.php/Main_Page)
- I live in Los Angeles, and my laptop arrived within 5 business days of the order.  It only takes 1 day to ship to LA since the warehouse is here.
- Laptop arrived in perfect condition with all the correct configuration specs.

============================================
Seval Professional (SERP5) Review:

Other Reviews:
[http://www.youtube.com/watch?v=nWBqgtJBOAA](http://www.youtube.com/watch?v=nWBqgtJBOAA)
[http://www.phoronix.com/scan.php?page=article&item=system76_serval_pro&num=1](http://www.phoronix.com/scan.php?page=article&item=system76_serval_pro&num=1)

Here's the product details straight from the order confirmation email:
------------------------------------------------------
1 x Serval Professional (SER-P5) = $1,862.00
    Display Resolution 15.4" WUXGA Matte Finish LCD (1920 x 1200)
    Graphics nVidia GeForce GTX 260M with 1GB DDR3
    Hard Drive 500 GB 5400 RPM SATA II
    Hardware Warranty 1 Yr. Ltd. Warranty and 1 Yr. Technical Support
    Memory 4 GB - DDR3 1066 MHZ - 2 DIMMs
    Operating System Ubuntu 9.04 (Jaunty Jackalope) 64 Bit Linux
    Optical Drive CD-RW / DVD-RW
    Processor Core 2 Quad Q9000 2.00 GHz 1066 MHz FSB 6 MB L2 (45 Watt)
    Wireless Intel Wi-Fi Link 5300 - 802.11A/B/G/N Up to 450 Mbps
    Bluetooth
------------------------------------------------------
United Parcel Service (1 x 15lbs) (Ground): $14.94
Discount Coupons:forums-laptop: -$25.00
Sub-Total: $1,862.00
CA TAX 8.25%: $153.62
Total: $2,005.56

I have a quadcore dell desktop as my workstation where I do all sorts of development and systems management, and I needed something mobile with the same computing power.  It came down to the Serval Professional (15.4") and the Bonobo (17").  I chose the Serval because, well, I ultimately wanted mobility.  The Bonobo offered more powerful CPU options, but the Core 2 Quad Q9000 2.00 GHz turned out to work very well.

Hardware: 
- Casing: Very well built with brushed aluminum casing.  The front System76 logo lets everyone know that you just don't check email with your laptop - very very cool.
- 15.4" WUXGA Matte Finish LCD (1920 x 1200): Very bright, no dead pixels, matted finish reduces the glare very nicely, excellent colors - as good as any Macbook Pro for sure.  I've watched several 1080p movies on it without any ghosting or hangups.
- Hard Drive 500 GB 5400 RPM SATA II: It was pretty fast for me.  I partitioned it 250GB/250GB for the Vista Ultimate dual boot option give or take some GBs for swap partitions.
- Graphics nVidia GeForce GTX 260M with 1GB DDR3: I haven't installed any games on it yet, but I'm a Battlefield 2 enthusiast, and so I'll be testing out this baby with that game.  I'm sure it'll run nicely.  Again, this card handled the 1080p movies very nicely.
- Intel HD Sound: This is a 2.1 soundcard.  It's pretty good for 2.1.  Windows drivers are very good for it.  More about this later.
- Wireless Intel Wi-Fi Link 5300 - Was able to stream 1080p movies at 18-30MBps without any lag.  Installed wireless drivers allowed me to easily switch between WiFi and landline connections effortlessly.
- Core 2 Quad Q9000 2.00 GHz, 4 GB - DDR3 1066 MHZ: I've run this with 3-4 IDEs, VMWare WinXp, and 20-30 terminals, coding, building, compiling, ssh'ing all at the same time without effort.
- Card reader: This wasn't able to read my SD card, so it didn't work.  I haven't tried it with the 6 other different flash card it supported though.
- Webcam: works nicely, just as good as the $80-$90 logitech webcams.  Software is good too.
- Touchpad: Smooth, but not as responsive as Windows Vista's drivers.
- Bluetooth: Haven't tried this yet.
- HDMI: Haven't tried this yet.
- DVI: Haven't tried the dual monitor split yet.
- eSATA: Haven't tried it yet.
- BioScan (finger) is not supported.
- Battery life: With this configuraiton, I estimated that it would completely discharge in a little over an hour on a full charge.  So plug in if you can.

============================================
Software:
When you first get turn on the laptop, be sure to install the System76 drivers by going to System => System76 Drivers => Install
Ubuntu Jaunty is pretty good and stable.  Everything works as it should.  I usually setup my own keystroke shortcuts for the Nautilus browser and popping a terminal.  I've also added Synergy and VMWare Player.

Another reason I wanted this laptop was so that I can stream HD 1080p videos from my main home file server to my entertainment center.  I installed Windows Vista Ultimate on another partition for this purpose.

- Ubuntu's Suspend and Hibernate features work as they should.  I have yet to test the battery life on full suspend and hibernate.  Any insite into these figures is much appreciated.  Restoring from suspend (memory) was nearly 100 times faster than restoring from hibernate (disc).  I restored nearly 20 running applications without any issues.

============================================
Adding Windows Vista To Ubuntu on the same drive:

References:
[http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine](http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine)
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

The two references above were the best I could find, yet they still didn't work for me line by line.  I had to make some adjustments on my own, and this is what I'll outline here.

Presteps:
1. Go here to grab all the appropriate drivers: [http://knowledge76.com/index.php/Serp5](http://knowledge76.com/index.php/Serp5)
2. Restart your System76 laptop, Hit F2 to enter BIOS, choose to boot with Optical Drive before your Harddrive. 

The Easy Way: Install Vista first, then install Ubuntu - You will lose all your current Ubuntu data.
1. Boot with Windows Vista CD => Delete all partitions => Complete Vista installation
2. After installing Vista, boot with Ubuntu Live CD => Resize partition => Install Jaunty
3. Restore the System76 drivers - [http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

The Hard Way: [http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
Page 3 comments: 
- You might get an warning/error dialogue about parition tables, just hit okay and ignore it.
- GParted's Partition Editor did now allow me to resize ANY of my paritions.  Ubuntu's partition was an ext logical partition at 490GBs.  This was the one I needed to resize.
- I had to actually initiate an Ubuntu Install, and only then did it allow me to resize my partition.  I chose to resize my partition to half it's original size (250GB).  Choose to install Ubuntu side-by-side with your current Ubuntu OS.
- After that, the Ubuntu Installation Wizard gives you the option to quit the installation.  Quit the installation.
- It will restart.  At this point, you can insert your Windows Vista Boot CD and boot into the Windows install.

Page 4 comments:
- Vista will not allow you to install on the new unallocated partition, even if you format it to NTFS.
- After formatting, you must "activate" the partition.  Follow the steps outlined to do so.

Page 5 comments:
- I didn't choose this option because I didn't want Windows to be aware of the GRUB boot loader.

Page 6 comments:
- Now, not everyone's partition is the same, so it's important that you know which partition your Windows Vista OS is actually on
- When you come to the part where you are editing /boot/grub/menu.lst, the example says to enter this at the end of the file:

title Windows Vista
root (hd0,1)
makeactive
chainloader +1

This is only true if you have Vista's partition on /dev/sda2.  For me, I had Vista installed on /dev/sda3, so mine looked like this:

title Windows Vista
root (hd0,2)
makeactive
chainloader +1
  
When you boot into Windows Vista, and you recieve an ERROR 12 message, please review again which partition your Windows is installed on.

============================================
Adding Windows XP VMWare guest to your Ubuntu host - This allowed me to easily bounce back and forth between my office products and dev / sys management work.

References:
[https://help.ubuntu.com/community/VMware/Player](https://help.ubuntu.com/community/VMware/Player)
[http://www.easyvmx.com/new-easyvmx.shtml](http://www.easyvmx.com/new-easyvmx.shtml)

High level steps:
1. Install VMWare player as outlined in the reference above.
2. Create a Windows XP vmware image from [www.easyvmx.com](www.easyvmx.com)
3. Insert Windows XP install disc, Launch VMWare Player, and choose to "play" the Window XP vmware image created in step 2.

Comments on creating the EasyVMX Windows XP Pro image:
- I chose Windows XP vs. Vista because XP doesn't eat up as much of my memory as much as Vista does.
- Here were my selections.  
* Choose EasyVMX v2.0
* 1 CPU
* 768MB of RAM
* Ethernet0, NAT, vlance
* Hard Drives, 25GB
* everything else was left at default

After the Windows XP installation, if you don't have connection, go to Control Panels => Network Places => Right click properties => Right click Local Area Connetion => Repair connection.

You will need to perform this operation everytime you move from one LAN to another to restore your VMWare internet connection.

I also found that Shared Folders does not work.  So instead I just use a thumbdrive to transfer files between the guest and host.

============================================
Windows Vista review on the Serval Professional
- The sound is MUCH better on Vista.  The driver and software provide you with much more options for filtering and effects
- The touchpad is also much more responsive.  You can swipe your finger across much faster with Vista.
- Sites with heavy Flash content also perform much better under Vista
- Games like Battlefield 2 of course will run on Vista
- I havne't tried the Bioscan yet, besides, I'm way to used to the user/password paradigm to put effort into testing it.
- I haven't tried the card reader for Vista yet either.  I think I'm just going to get those USB/SD card adapters instead.
- In general, 1080p movies and media play very nicely in Vista.

============================================
Possible Upgrades
- 5.1 card from Creative Labs.
- 8GB memory when the price goes down.  Right now it's $795 for a 2x4GB 8GB DDR3 1066 MHZ kit!

---

### Post by Eldera on 2009-08-27
jpongin: Congratulations on a magnificent write up. I am sure this will be helpful to a lot of people, especially me. Every time I learn something new, I want to change my partitioning around.

One comment 

[quote=jpongin]- GParted's Partition Editor did now allow me to resize ANY of my paritions. Ubuntu's partition was an ext logical partition at 490GBs. This was the one I needed to resize.
- I had to actually initiate an Ubuntu Install, and only then did it allow me to resize my partition. I chose to resize my partition to half it's original size (250GB).[/quote]

At this point one could check to see if any swap partitions were active. Gparted does not work when they are. There will be a key by the name of the partition. (Locking Gparted out) Click the problem partition, click "partition" in menu > swapoff. When this is done, Gparted becomes active.
If a swap and its extended partition are locked, unlock swap first and then the extended partition.

Of course, your problem might have been something quite different, Computers can do strange things. 

Have a great day:)

---

### Post by thomasaaron on 2009-08-27
Yes, great write-up. Thank you.

Eldera's right on the money. Use gparted from a live cd and set the swap partition to 'swapoff.'

Also, your card reader definitely should work. Try a different card. We've been seeing a lot of problems lately with certain camera card formats.

---

### Post by registering on 2009-08-27
Yes, awesome write-up, thanks! I was planning on a Pangolin but now I'm leaning more towards the Serval.

Can you let us know how the battery holds-up? One hour seems like a very short lifetime for an 8-cell battery (even for a quad-core pulling 45 watts). My Dell D630 gets about 3.5-4 hours on Ubuntu w/a 9-cell battery playing videos.

Do you need to squint at that resolution? I'm debating about whether to get the matte display. If money were no object I would, but I don't know if I'd end-up lowering the resolution to make things more readable. I couldn't find any resolutions that high on a screen that size at Best Buy to compare with. :(

---

### Post by thomasaaron on 2009-08-27
> (even for a quad-core pulling 45 watts)

The graphics card is very power hungry.

---

### Post by registering on 2009-08-27
Aaahhh, good point I missed that. :)

---

### Post by jpongin on 2009-08-27
> **Eldera said:**
> jpongin: Congratulations on a magnificent write up. I am sure this will be helpful to a lot of people, especially me. Every time I learn something new, I want to change my partitioning around.

One comment 



At this point one could check to see if any swap partitions were active. Gparted does not work when they are. There will be a key by the name of the partition. (Locking Gparted out) Click the problem partition, click "partition" in menu > swapoff. When this is done, Gparted becomes active.
If a swap and its extended partition are locked, unlock swap first and then the extended partition.

Of course, your problem might have been something quite different, Computers can do strange things. 

Have a great day:)

Not at all, I believe you are correct.  My Swaps were active, and everything was locked down.  Thanks for replying, now someone knows exactly what to do.

---

### Post by jpongin on 2009-08-27
> **registering said:**
> Yes, awesome write-up, thanks! I was planning on a Pangolin but now I'm leaning more towards the Serval.

Can you let us know how the battery holds-up? One hour seems like a very short lifetime for an 8-cell battery (even for a quad-core pulling 45 watts). My Dell D630 gets about 3.5-4 hours on Ubuntu w/a 9-cell battery playing videos.

Do you need to squint at that resolution? I'm debating about whether to get the matte display. If money were no object I would, but I don't know if I'd end-up lowering the resolution to make things more readable. I couldn't find any resolutions that high on a screen that size at Best Buy to compare with. :(

I have some figures on a fresh fully-charged, fairly new battery.

Assumptions:
When I test a battery's consumption, I test it while I'm using the laptop to perform my daily tasks.  I don't just turn it on and not run anything.  Tasks can of course differ for different people.  

On Battery Consumption With Laptop Usage:
A situation for me where I can see myself not plugging in is when I'll be using the laptop to mainly do work related things at a coffee shop or a bookstore.  In which case, I'll have at least 5-10 terminals, 2-3 IDEs, VMWare w/ WinXP, 5-10 browser tabs, and streaming Shoutcast.  At this rate, I did notice that I'd be out of power after about 1.5 hours.

On Battery Consumption With Suspend:
I pretty much suspended my configuration above overnight on a full charge.  Roughly 9 hours later, I powered on the laptop at my office, and the battery power indicated 89% power left.  So, 9 hours of suspend on a full charge will consume about 11% of battery power.  VERY NICE!  Everything came back up in a snap without hiccups.  Of course, as the battery loses its charge over time, the consumption will increase, in which case, it's time to replace it.

On the resolution:
I specifically chose the 1900x1200 for three reasons:
1) My work demands a lot of realestate, at least for high productivity it does.
2) 1080p movies on the laptop.
3) 1080p games on the laptop.

I don't need to squint, but I'm the type of person who likes to work on small details, so my near-sighted vision maybe different than others.  I believe some Macbook Pros come in that resolution for 15.4" screens.  At BestBuy, I also noticed some 16" Sony Vaio laptops with 1900x1200 resolution.  This is what I used to see what it would look like on a 15.4" screen.  It's pretty accurate.

---

### Post by registering on 2009-08-27
Cool, thanks jpongin. I appreciate the feedback. Is there any difference in difficulty when viewing the 1680x1050 versus 1920x1200 resolution on that screen size?

Oh, I see we both edited. :) Thanks for the great feedback, off to Apple store to compare (yes, my eyesight isn't great).

---

### Post by jpongin on 2009-08-29
So I'm trying the HDMI out, but I'm not getting any sound output via HDMI to my HDTV.  Is this the expected behavior?  I was under the assumption that the sound signals would be fed through the HDMI output along with the video.

---

### Post by gpstar on 2009-08-29
[http://ubuntuforums.org/showpost.php?p=7782584&postcount=22](http://ubuntuforums.org/showpost.php?p=7782584&postcount=22)


> **jpongin said:**
> So I'm trying the HDMI out, but I'm not getting any sound output via HDMI to my HDTV.  Is this the expected behavior?  I was under the assumption that the sound signals would be fed through the HDMI output along with the video.

---

### Post by jpongin on 2009-08-30
Got HDMI audio out working!... er. on Vista.  I just needed to switch the default audio device to Realtec Digital Out.

I've set to try it on Ubuntu.

---

