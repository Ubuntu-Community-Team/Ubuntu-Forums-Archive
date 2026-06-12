---
title: "Acer Aspire Easystore H340 Home Server"
date: 2009-06-21
forum: Server Platforms
---

### Post by rhdinah on 2009-06-21
Does anyone know if Ubuntu server runs on this box? Thanks! :D

---

### Post by basementgeek on 2009-06-23
I would like to know as well!  Being that it's headless, (no vga) I'm not sure how you would even go about installing it (NAS noob)...some sort of network drive install?

Apparently there is a 26 pin header on the mobo that would allow vga and keyboard, but you need a custom cable to make it happen.

---

### Post by cariboo on 2009-06-23
THe unit is based on an Intel Atom motherboard, so you can install Ubuntu on it. Have a look at this [page]("https://help.ubuntu.com/community/Installation") for installation options.

---

### Post by rhdinah on 2009-06-27
> **cariboo907 said:**
> THe unit is based on an Intel Atom motherboard, so you can install Ubuntu on it. Have a look at this [page]("https://help.ubuntu.com/community/Installation") for installation options.

Thanks! But being a headless system it makes it a bit rough to see what you're doing, let alone make changes or selections. There is a cable someone has constructed at a healthy price for the HP Mediasmart Server that will enable that. But I think pulling the HD out of the unit, snapping it into a tower, setting up linux and then re-installing might work. From there, knowing the IP Address, one should be able to rlogin. Just passing thoughts by ...

---

### Post by nerr on 2009-07-10
Hey everybody, I actually just ordered this box as well and came to ask the same thing... but after doing some reading, it would appear rhdinah's method should work just fine.

I plan on removing the 1TB HDD it comes with, installing the second 1TB HDD I'm getting for free with mine in my rig, installing Ubuntu Server, updates, and SSH on it, then putting it back in the easyStore and seeing if I can boot Ubuntu and such with it.  I'm very excited to give this a shot, but will definitely hold onto that WHS disk until everything is up and running... just in case!

I'll post a reply to let you all know how it goes when mine arrives next Wednesday or Thursday.

---

### Post by druhboruch on 2009-07-11
I installed Ubuntu server on it and I have to tell you that I am very impressed.  It is very quiet and runs very cool with stock disk.  It may get warmer when I install additional disks.

The only thing that doesn't work is some LED's.  The "i" light is flashing blue all the time and the LED's next to disks don't lite at all.

All LED's work OK when booted with WHS.

There is also build in flash memory in this little machine.  It contains some drivers for WHS and can be formated as well.

Overall great piece of hardware.  I am glad I bought it.

---

### Post by nerr on 2009-07-11
druhboruch, any specific advice or method as to how you installed and got Ubuntu Server running on your box?  Did you use the same method I was thinking about trying, or is there a more specific one?  I'd really like to get this right the first time around, so your advice is greatly appreciated.

And the LEDs don't work eh?  That's a bummer!  Not a huge deal for me since I won't even be in the same house as this machine for most of the year, but it'd be cool if you could still use them. :)

---

### Post by druhboruch on 2009-07-11
This is how I setup ubuntu server on H340:

I plugged disk to another PC and installed Ubuntu Server command line system and SSH server.

During the setup I selected manual network configuration with static IP address.

After setup was completed I rebooted the system.

Enabled root account.

Loged in as root and modified /etc/udev/rules.d/70-persistent-net.rules.
Removed the line:
```
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:00:00:00:00", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0" 
```

Then I powered down the pc and moved disk back to H340.

It took less than 20 minutes.

Then I installed xorg, gnome-core, ubuntu-artwork and freenx-server.

Everything works as a charm.

---

### Post by tstack77 on 2009-07-11
This might be a stretch, but would it be possible to somehow check the bios to see if it can boot from a flash drive?

I would love to use all 4 drives in a raid 5 array.

---

### Post by druhboruch on 2009-07-11
> **tstack77 said:**
> This might be a stretch, but would it be possible to somehow check the bios to see if it can boot from a flash drive?

I would love to use all 4 drives in a raid 5 array.

It is very easy to find out.  I would just run installation to flash on another PC and I would try to boot from H340.

It may just work...

---

### Post by tstack77 on 2009-07-11
My thoughts exactly, but I should've worded my question better...

*Before I buy one,* would anyone know if it's possible to somehow check the bios to see if it can boot from a flash drive?

;)

---

### Post by rhdinah on 2009-07-12
> **tstack77 said:**
> My thoughts exactly, but I should've worded my question better...

*Before I buy one,* would anyone know if it's possible to somehow check the bios to see if it can boot from a flash drive?

;)

That's what the special cable developed for the HP LX195 box is for.

---

### Post by tstack77 on 2009-07-12
Why does microsoft have to make everything so damn backwards??? Seriously, what does NOT having a simple vga port do to boost sales of a dedicated server???

argh...anyway

I think an easy test would be for one of you out there with this box to try and boot an unRaid flash drive (get it [HERE]("http://www.lime-technology.com/joomla/index.php")).

This is a simple os based on slackware that is meant to be installed on a headless server from a flash drive.

Anyone care to play guinea pig :lolflag:

---

### Post by druhboruch on 2009-07-12
> **tstack77 said:**
> 
I think an easy test would be for one of you out there with this box to try and boot an unRaid flash drive (get it [HERE]("http://www.lime-technology.com/joomla/index.php")).

This is a simple os based on slackware that is meant to be installed on a headless server from a flash drive.

Anyone care to play guinea pig :lolflag:

The server has build in 250M flash drive.
If you prepare an iso for me I will try to boot my server and post the results.

Cheers

---

### Post by tstack77 on 2009-07-12
That would be awesome, I really appreciate it!

Above I gave a link for unRaid, it's the most simple test that I can think of if you have a spare flash drive laying around. Complete instructions for preparing the drive are [HERE]("http://www.lime-technology.com/joomla/unraid-os")

I can't imagine this taking more than 5 minutes to test :p

Thanks again!

---

### Post by druhboruch on 2009-07-13
> **tstack77 said:**
> That would be awesome, I really appreciate it!

Above I gave a link for unRaid, it's the most simple test that I can think of if you have a spare flash drive laying around. Complete instructions for preparing the drive are [HERE]("http://www.lime-technology.com/joomla/unraid-os")

I can't imagine this taking more than 5 minutes to test :p

Thanks again!

tstack77,
I have great news for you.
unRaid booted succesfully from the front port of H340.

:popcorn:

---

### Post by nerr on 2009-07-13
Hm, sorry to steer the thread in a slightly different direction, but does anybody here know if it'd be possible to create a software RAID 1 array during setup on another machine, and then migrate the array to this server machine while still retaining data integrity?  I'm curious because mine is coming with two identical 1TB Western Digital Green drives, and a RAID 1 array would be a beautiful thing to keep my OS and data alive.

---

### Post by tstack77 on 2009-07-14
> **druhboruch said:**
> tstack77,
I have great news for you.
unRaid booted succesfully from the front port of H340.

:popcorn:

:guitar:

Simply awesome.

Big THANKS!

---

### Post by windependence on 2009-07-14
I have a question for you guys. If you could get a box like this for $100 less and have a VGA port, front USB and sound ports with a 1 TB HD, without the nasty Windoze stuff how many of you would buy it?

-Tim

---

### Post by druhboruch on 2009-07-14
> **windependence said:**
> I have a question for you guys. If you could get a box like this for $100 less and have a VGA port, front USB and sound ports with a 1 TB HD, without the nasty Windoze stuff how many of you would buy it?

-Tim

Are you suggesting that I should get the refund from Acer for WHS?

---

### Post by windependence on 2009-07-14
No, but I build boxes for my customers based on the Intel Atom board. Fully functional and Linux compatible for $299US. the form factor is very small. Essentially, this is the same thing. We get some of the parts direct from China.

I was just wondering how big this market might be. These machines only draw 32 watts of power.

-Tim

---

### Post by tstack77 on 2009-07-14
I'd definitely check it out. Got it on your website?

---

### Post by windependence on 2009-07-15
I wish my site was up right now. You know the old addage, the mechanic has the worst car? Well I am a consultant and I haven't had time to fix a problem I had when moving to a new machine. I hope to have it up very soon, thanks.

-Tim

---

### Post by cakalapati on 2009-07-16
I have some BIOS screenshots that I took posted here:
[http://www.mediasmartserver.net/forums/viewtopic.php?f=23&t=4812](http://www.mediasmartserver.net/forums/viewtopic.php?f=23&t=4812)

I installed Ubuntu 9.04 Server on the Acer easyStore and ran a bunch of Linux commands:
[http://www.mediasmartserver.net/forums/viewtopic.php?f=23&t=4813](http://www.mediasmartserver.net/forums/viewtopic.php?f=23&t=4813)

I saw the same LED problem described in a previous post.  The LEDs are controlled by a custom driver and will probably have to be reverse engineered for it to work in Linux, as I did once before (with the MediaSmart Server) here:
[http://www.mediasmartserver.net/forums/viewtopic.php?f=2&t=2335](http://www.mediasmartserver.net/forums/viewtopic.php?f=2&t=2335)

---

### Post by druhboruch on 2009-07-16
cakalapati,

Thank you  for all the info and for confirming what I suspected about LEDs.

---

### Post by nerr on 2009-07-16
Hey again everybody, mine just came today and I'm having absolutely no luck getting Ubuntu Server running on it.  My networking won't initialize at all under Ubuntu Server, and I have absolutely no idea why.  Could it be that I opted for DHCP versus a static IP?  Does it matter that much?

---

### Post by druhboruch on 2009-07-16
Have you removed udev rule before first boot?

---

### Post by nerr on 2009-07-16
Ahaha, that was the problem.  I should have just done that in the first place.  Thanks for your original instructions, heh!

This thing really is a beast.  I'm running a massive rsync job right now and working on compiling rtorrent and libtorrent, and it's still just chugging along.  CPU load is at 3.29, but it's making no indications of stopping.  Man I love this box right now.

I think I'm going to run RAID 1 with two 1TB WD disks (one that had WHS, the other that came free with it), but I've run into a slight hitch.  One disk has 8MB of cache, the other has 32MB.  That's quite a difference.  From what I've read it doesn't matter too much unless you want to do Linux mdadm RAID 0, but since I want an mdadm RAID 1 array, I should be okay, right?

I HIGHLY recommend this box for anybody looking for a nice little file server.  It truly is a marvel.

---

### Post by tstack77 on 2009-07-16
> **nerr said:**
> One disk has 8MB of cache, the other has 32MB.

So the 1TB drive that came with the box is an older wd 5400 green drive? I was under the assumption that it was one of the newer 7200 caviar green drives :(

---

### Post by windependence on 2009-07-17
The 5400 drives ARE the new drives. Contrary to popular belief, spindle speed means nothing for data access unless you are accessing sequential data. Almost NO data is accessed that way. With random access to data, things like seek time are way more important and the correct interleave. The drive manufacturers have known this for quite some time, but green is "PC" now so they finally have to actually do it. The new drives data access times are just as good as the 7200 RPM drives. Check out the new technology on the WD site.

-Tim

---

### Post by TaleSlinger on 2009-08-01
Thanks for the installation instructions (post #8).  I've attempted to follow the instructions, but I've missed something. 

I'm attempting to boot from a USB (via xubuntu).

Here's what I've done:
- Installed xubuntu to USB via live CD
- set the ip address to be static
- installed xvnc, SSH, FreeNx 
- changed /etc/udev/rules.d/70-persistent-net.rules as directed (I didn't understand what that does for me however).
- double-checked the network cable to be srue that it works

When I plug the usb into my laptop, it works just as I'd expect.

when I plugged it into the Acer H340, usb connectors (front, back) to attempt to boot it.
I don't get anyting I can work with, and I can't ping the server.  

do I need to go into the bios to allow it to boot to hd?

Thanks in advance.

---

### Post by druhboruch on 2009-08-02
First see if you can ping and ssh your laptp after you boot it from USB stic.

If you can, then just make sure that everything inside 70-persistent-net.rules file is commented out and THEN boot H340 again.

The udev rule maps MAC address of your network card to the network interface eth0 as defined in /etc/network/interfaces.

Please, describe what is happening when you boot H430 from USB.
The "i" shuld be blinking blue and you should be able to ping your server.

---

### Post by TaleSlinger on 2009-08-03
> **druhboruch said:**
> First see if you can ping and ssh your laptp after you boot it from USB stic.

If you can, then just make sure that everything inside 70-persistent-net.rules file is commented out and THEN boot H340 again.

The udev rule maps MAC address of your network card to the network interface eth0 as defined in /etc/network/interfaces.

Please, describe what is happening when you boot H430 from USB.
The "i" shuld be blinking blue and you should be able to ping your server.

Thanks.  This was helpful.  

Here's what I've done so far, and what I've done and learned so far (speaking as a marginally competent guy who doesn't know *nix that well):

My goal is to install Linux on a memory stick/USB, then put four 1.5 TB drives in the Acer H340, running RAID 5, for a 4.5 TB system with some redundancy, costing $750, total. ($100x4x1.5 TB, $350 for the Acer 340 from NewEgg).

Other things I didn't mention above:
- I added a separate fixed, wired IP address for the installation (might not have been a good idea -- I should probably have modified the default wired connection, but I later tried that with results I don't understand).
- on the PC, I checked the IP address with ifconfig, and verified that it is as I set it:  192.168.1.128
- I verified that SSH and VNC were working by actually sshing and VNCing (separately) into the USBed desktop.

When I plugged the memory key in, it booted, but didn't connect to the network properly.  You can tell that you are connecting to the network, because the "network led blinks properly (lots of flashing).

Once I modified the udev commenting out ALL the lines there, and plugged the usb back in, it booted and the connectivity light blinked.  

However, the IP address of the H340 was not as set, but 192.168.1.143.  I'm not sure why this happened, once I checked the router and determined the address, I was able to SSH in to the embedded system, and remote emacs back to my remote computer.

(However, since I didn't set up my keys properly, it seems like I could only do this once each.  I don't know what my problem here is).

I was not able to do VNC to the Acer H340 however, even though I had the proper addres (Any suggestions here would be appreciated).

So, at the moment, I have successuflly booted the system from USB, and SSHed to it.  It doesn't have the same fixed IP that I set it to however (possibly becuase I need to do something better in udev than commenting out everything, or perhaps there's something i can do with my router -- DD-WRT)

Why can't I use VNC to remote desktop to the H340, but I can VNC to the dekstop?


If you have a recommended tutorial for setting up SSH, sending the entire desktop back as an XWindows session (should be able to do that, right?) and/or software RAID, I''d appreciate it.  Of couse, I can use Google as well as the next guy if you don't have any outstanding recommendations.

Thanks again for your help.  I couldn't have gotten this far without support, and I would have ended up using Windows otherwise.  (I would have trid to get a few bucks back from NewEgg for the Windows Embedded License, but I bought it on "No refunds--echanges only" terms.

Best regards,

TaleSlinger

---

### Post by nerr on 2009-08-03
I apologize for adding my own little sub-thread on here, but I've been experimenting with my box a lot lately, and after opening it up, it appears there's really no way to add additional cooling for the box other than replacing the stock, 120mm 4-pin fan on the side with a different fan.  Has anybody managed to find a way to get additional cooling on the system, particularly for the hard drives?

Running with four drives in the system, my temperatures were as follows:
Western Digital 1TB Green (1): 43 C
Western Digital 1TB Green (2): 42 C
Western Digital 640GB Black: 50 C
Seagate 1.5TB 7200.11 Barracuda: 49 C

Obviously the "Green" drives help to keep temperatures down, but I just read a little while ago that every degree you're able to drop off a disk's temperature could mean another 10% bonus to its lifetime.  For a system that runs 24/7, even with backups, it'd be nice to have some very reliable and cool drives.  It doesn't appear that there's any way to tack any more cooling fans on to the power supply, so I was curious if any creative minds have come up with a solution yet.  I'm almost tempted to buy a high power fan to replace the stock 120mm 4-pin mounted on the right side of the chassis!

Edit: And has anybody found a way to make use of the dme1737 sensor supposedly located on this machine?  My installation isn't able to use it when I run "sensors" even after detecting it and adding it to my /etc/modules file.  Being able to control that system fan could be a great asset if it's at all possible.

---

### Post by Sockpuppet on 2009-08-06
Hi,

installing Ubuntu on my H340 worked fine here, as well. My solution is a bit different:

I took out the Easystore's OS harddisk, attached it to my desktop with a USB-SATA adapter (like [this one]("http://www.compusb.com/miusb20tosaa.html")) and installed the OS via the desktop PC, using kvm:

```
# /dev/sdg is the drive, attached to desktop PC with USB-SATA adapter
# - device name may vary on your PC

# first, install
kvm -cpu n270 -m 756 -hda /dev/sdg -cdrom ubuntu-9.04-server-i386.iso -boot d

# then, after installation is done, start again and install openssh-server
kvm -cpu n270 -m 756 -hda /dev/sdg
```

No problem installing Ubuntu that way. The H340 comes with a 256 MB flash disk. I couldn't use it for my installation, my Ubuntu server installation is about 700 MB.

---

### Post by Sockpuppet on 2009-08-06
On the net, someone else described how he used a [special vga adapter]("http://www.mediasmartserver.net/forums/viewtopic.php?f=6&t=3980") to [install Ubuntu]("http://www.mediasmartserver.net/forums/viewtopic.php?f=23&t=4813") on this box.

So now we have several options on how to install Linux on the H340.

---

### Post by Sockpuppet on 2009-08-06
Oh, that other guy also posted in this thread. Hi there, fellow! :-)

Die anyone make progress with the LEDs?

It's curious that the system loads the led_class kernel module, yet /sys/class/leds is empty. Any idea what triggers loading the module?

Thanks!

---

### Post by windependence on 2009-08-06
With drives having a MTBF of 1,000,000 hours, there is no need for extra cooling since the MTBF is 114 YEARS! Modern drives last a long, long time. Also, for all the futzing around you have to do with this thing, the small form factor boxes like I am building for customers is much more flexible. Here is a pic:

Dimensions are:

8.7"x 5.1"x 11.8" 
220mm x 129mm x 300mm
(W) x (H) x (D)
*Measurement of depth is without front bezel.

-Tim

---

### Post by Sockpuppet on 2009-08-07
Hi Tim,

I bought the Acer H340 specifically because of its four drive bays. Your box is nice, but it's not made for a RAID setup.

Regards,

sp

---

### Post by windependence on 2009-08-08
How big is that thing?

-Tim

---

### Post by Sockpuppet on 2009-08-08
7.9" (200mm) W x 7.1" (180mm) D x 8.3" (212mm) H (according to a quick googling).

This cube is 1/4th of the dimensions of my current home-built fileserver (midi tower case). So I'm very happy.

---

### Post by Rural on 2009-08-09
Chalk me up as one of the folk running Ubuntu on the Acer Aspire Easystore H340. I used the same method as druhboruch outlined. Worked like a charm in about 20 minutes.

I've got a total of 3 1TB WD Green drives and am about to set them up as a RAID 5 array, but have had trouble understanding what one can get away with under RAID and LVM. I'm familiar with LVM but this will be my first software RAID box.

Ideally, I'd like a single RAID 5 array with everything on it under LVM. Unfortunately, it looks like one needs /boot, as a minimum, outside of LVM and RAID. I'm getting the impression that root should also be outside of RAID, but maybe I'm misinterpreting something.

What I've got now is a single disk with /boot as a native partition (ie. outside of LVM), everything else (swap, /, and /usr) is under LVM. This is on 10GB. What I'd like to do is set up the same 10GB on each disk. That way I'm guaranteed to have a bootable and useable OS with all the basics as long as one drive remains. 
The remainder of each drive will be used for a RAID 5 array and will house /home, /tmp, /var, and some of the other stuff I generally setup. (Maybe I should put swap on the RAID 5 array as well.)

I'm curious what others have done and if anyone has any suggestions for my plan as outlined above.

---

### Post by Rural on 2009-08-10
I setup the RAID 5 array last night and did some benchmarking when my work got boring today. I'm seeing about 164MB/s reads (using dd to write a 4GB file full of random data to /dev/null). Combination read/writes (writing one 4GB file to another) are more like 35 MB/s. This is with no optimization of anything. Just standard LVM2 running over standard Linux software RAID 5.

But what most impresses me about this box is how quiet it is. Just a soft hum from three feet away. It is by far the quietest machine I've worked with, yet it is a file-server.

Still getting each of the drives setup to be bootable. And I'll need to figure out a boot disk that runs sshd.

The headlessness does add some complication, but it's not insurmountable.

---

### Post by rjs82vette on 2009-08-16
I have two of these boxes, one running WHS and one running ubuntu server.

---

### Post by nerr on 2009-08-16
These little guys are great.  Mine runs everything wonderfully, and serves as an excellent home server.  The hotswap hard drive bays are practically necessary for a box like this, and will be a must for any future home server boxes I look into buying or building.

On mine, I run:
HTTP, HTTPS: Apache2 + PHP
SSH: OpenSSH Server
BitTorrent: rTorrent
SMB/CIFS: Samba
rsync
IPP: CUPS

I've also created scripts that back up all data from /srv (my main storage location) to a secondary hard drive once a day using rsync, and a script that uses nmblookup in Samba to find Windows machines on the network and pulls data down from them using rsync to backup and store.  It's a great little box!

---

### Post by windependence on 2009-08-17
What are you using as an rsync client on the Windows boxes?

-Tim

---

### Post by nerr on 2009-08-17
There's a program called DeltaCopy that installs a few Cygwin files and gives you rsync, ssh, and chmod executables along with it.  I don't even use the client, I just make up batch scripts and use them that way to sync my files.

For example:
```
@echo OFF
set client=/cygdrive/f/music/
set server=nerr@mydomain.com:/srv/media/Music/
C:
cd \DeltaCopy\
:menu
echo rsync batch script - Music
echo ----------------------------------------------
echo 1) Backup    2) Restore    3) Exit
set /p choice="Please select an action: "

if %choice%==1 goto:backup
if %choice%==2 goto:restore
if %choice%==3 goto:eof

:backup
rsync -avz --progress --inplace --del --chmod=a+rwx --exclude desktop.ini --exclude thumbs.db --rsh='ssh -i id_rsa' %client% %server%
Pause
goto:eof

:restore
rsync -avz --progress --inplace --del --chmod=a+rwx --exclude desktop.ini --exclude thumbs.db --rsh='ssh -i id_rsa' %server% %client%
Pause
goto:eof
```

That works well enough for when I'm syncing outside of my home network, but if I'm on the local network, I just have the server mount a shared folder as CIFS and push/pull data to or from it that way, using rsync.

---

### Post by windependence on 2009-08-18
Yep, I'm familiar with DeltaCopy. Thought that might be what you were using. How is the stability?

-Tim

---

### Post by nerr on 2009-08-18
Actually it's not bad at all.  I originally had to run a 75' ethernet cable to plug into my router for my desktop successfully sync a LOT of data with it (we're talking 600GB or so), but otherwise it's been completely reliable even on wireless on both my desktop and laptop.

---

### Post by panicprone on 2009-08-21
Hey guys,

I'm just about to buy one of those boxes.

Of course I want to get rid of WHS.

One question: Did someone of you set up wake on lan on ubuntu with the aspire h340?


- Jo

---

### Post by dabombnl on 2009-12-07
Rather than buying one of the cables to connect to VGA (for $60 at the cheapest). Would a USB graphics adapter work for BIOS access instead? They are cheaper, work externally, and work for other computers.

---

### Post by egosumliber on 2010-01-12
This may be a stupid question, but should I use the 64 or 32 bit installer?  I know the Atom processor can handle 64-bit, but somewhere else online I saw to use the I386 (32-bit) installer... Also a little confusing, the file name of the 64-bit installer has "amd64".

Thanks!

---

### Post by CannedCorn on 2010-02-09
Sooo.... is it possible to load ubuntu through a USB drive? Can someone please describe this process?

---

### Post by prodigy7 on 2010-02-21
Hi there!

I want made the leds working under linux like cakalapati has it done. Therefor i would need the hardware address (see [http://www.mediasmartserver.net/forums/viewtopic.php?f=2&t=2335](http://www.mediasmartserver.net/forums/viewtopic.php?f=2&t=2335)) or someone in germany who can borrowing his gen2 cable with serial for some days.
I think, when I've the "important" information, I could made an led driver.

prodigy7

---

### Post by dadepfan on 2010-05-01
Hi everyone - just joined the forum.

I know it has been several months since the last post on this thread, but after reading the whole thread, I wanted to ask some questions.

First, I have had the Acer Aspire with Windows Home Server for a few months, and have been having a several-times a day problem where the shared folders suddenly become not accessible from my Windows 7, 64-bit clients.  This impacts Windows Explorer and any other application trying to access a file on the server, but nothing else on the client.  There is no way to fix this other than rebooting the client, and doing so causes Windows to hang on the "logging off" screen forever.  The power button becomes the only option.

So after MANY hours researching and trying to solve this problem, I am now considering replacing the operating system with Ubuntu Server.

Several years ago, I experimented with running SuSe Linux, but ended up going back to Windows.  Reading this thread, my first comment is that I do not know what the flash drive that comes with the box is.  I do not believe I received one with mine (unless it is on the inside or something).

I have a 750 GB Maxtor OneTouch USB external drive that I just formatted.  Is it possible to install Ubunto Server on the OneTouch (attached to my laptop), and then use it to somehow install it on the Aspire?  I can configure the laptop to boot from the OneTouch (I think), but how do I use that to install on the Aspire?

I know there are some instructions on this thread, but I am not sure how the lack of keyboard and monitor is overcome.  Could someone post some step-by-step instructions for the less Linux-orientated among us?

Thanks,
Dave

---

### Post by bakinsoda on 2010-05-05
Any luck on getting the LED lights to work?  Updates?

---

### Post by hakonlo on 2010-06-11
A driver for the LEDs has been developed:

[http://www.mediasmartserver.net/forums/viewtopic.php?f=23&t=7720](http://www.mediasmartserver.net/forums/viewtopic.php?f=23&t=7720)

---

### Post by bryanhiggins on 2010-11-29
For the record, it isn't necessary to change any BIOS settings to boot from USB. Just pull out the primary HD, wait for the system to boot, then re-insert it.

I used another PC to configure a live USB so that SSH server is enable on boot. I then used that environment to partition my drives and setup a new installation using debootstrap.

See my blog post for full details.

[http://bryanhiggins.net/2010/11/29/installing-ubuntu-on-acer-easystore-h340/](http://bryanhiggins.net/2010/11/29/installing-ubuntu-on-acer-easystore-h340/)

---

### Post by merelin on 2011-01-19
Guys,

I've posted a deb file for mediasmartserverd here:

[http://www.mediasmartserver.net/forums/viewtopic.php?p=78292#p78292](http://www.mediasmartserver.net/forums/viewtopic.php?p=78292#p78292)

---

### Post by merelin on 2011-01-19
Guys,

I've posted a deb file for mediasmartserverd here:

[http://www.mediasmartserver.net/forums/viewtopic.php?p=78292#p78292](http://www.mediasmartserver.net/forums/viewtopic.php?p=78292#p78292)

Sorry guys, this duplicate is due to a connectivity issue. Can't be deleted.

---

### Post by merelin on 2011-01-19
Guys,

I've posted a deb file for mediasmartserverd here:

[http://www.mediasmartserver.net/forums/viewtopic.php?p=78292#p78292](http://www.mediasmartserver.net/forums/viewtopic.php?p=78292#p78292)

Sorry guys, this duplicate is due to a connectivity issue. Can't be deleted.

---

### Post by FromTheUnderground on 2011-02-02
I am running into a problem that I can't find a solution to.  I am installing Ubuntu server 10.10 onto a USB hard drive to run my Acer server.   I am installing the OS through a PC laptop onto the USB drive and I am able to SSH into it.  When I plug the USB drive into the server and boot it up, I can ping the server but can not SSH into it.  I ran a port scan and found that when plugged into the Acer, port 22 is turned off; when plugged into my laptop, port 22 is open.  Any idea as to why this is happening.

BTW, I have commented out the items in the 70-persistant-net.rules file.

---

### Post by merelin on 2011-02-03
> **FromTheUnderground said:**
> I am running into a problem that I can't find a solution to.  I am installing Ubuntu server 10.10 onto a USB hard drive to run my Acer server.   I am installing the OS through a PC laptop onto the USB drive and I am able to SSH into it.  When I plug the USB drive into the server and boot it up, I can ping the server but can not SSH into it.  I ran a port scan and found that when plugged into the Acer, port 22 is turned off; when plugged into my laptop, port 22 is open.  Any idea as to why this is happening.

BTW, I have commented out the items in the 70-persistant-net.rules file.

Are you sure you are booting from the USB drive?
Did you try to remove all the HDDs from bays and boot from the USB drive?

---

### Post by FromTheUnderground on 2011-02-03
> **merelin said:**
> Are you sure you are booting from the USB drive?
Did you try to remove all the HDDs from bays and boot from the USB drive?

All of the hard drives had been formatted earlier but I removed them anyway.  Booted up the machine with only the USB drive and port 22 is still turned off.  

Is there a config file or something that I can use to check to make sure all the correct services / daemons are running.  Is it possible that since the MAC address is different, it's causing SSH to stop working?

---

### Post by merelin on 2011-02-03
> **FromTheUnderground said:**
> All of the hard drives had been formatted earlier but I removed them anyway.  Booted up the machine with only the USB drive and port 22 is still turned off.  

Is there a config file or something that I can use to check to make sure all the correct services / daemons are running.  Is it possible that since the MAC address is different, it's causing SSH to stop working?

Are there any other ports open apart from 22?
Make sure OS is booted on another PC or under say kvm.
Try to re-install openssh-server.

---

### Post by FromTheUnderground on 2011-02-04
> **merelin said:**
> Are there any other ports open apart from 22?
Make sure OS is booted on another PC or under say kvm.
Try to re-install openssh-server.

When I boot the USB drive off the laptop, only port 22 is open.  When I boot the USB drive off the Acer, I get a weird number of ports; 135, 139, 8912, 49162, 49163.

I think I am going build one of the video cables for the server and use an external CD drive to install the OS.

---

### Post by FromTheUnderground on 2011-02-04
Disregard my last post. It looks like there is an embedded OS on the server that the system is booting to instead of the USB device.  I am not working on removing that embedded OS or find a way to get into the BIOS to set it to boot only from USB.  Thanks for all of your help with this.

---

### Post by ReginaldPerrin3 on 2011-03-06
I must confess to being a bit of a noob when it comes to servers and things. I have an H340 Home Server, and I really want to eliminate any Windows on it.
Having read what people have written here, I installed Ubuntu Server 10.10 on an empty drive via an existing machine. Then I removed the supplied 1 TB drive with Windows Server on it from the H340, inserted the new Ubuntu server drive.
Now I can power up the machine, the lights come on, the network light flickers with activity, and...
Well, I am at a bit of a loss at what to "do" now.

The H340 is connected to a router, just like my existing machine, so it gets an IP address from the DHCP server in the router.
How do I actually connect to the H340? I really don't know. Do I go "Places->Network"? or "Places->Connect to Server"? Or do I do a remote desktop connection?
When it is powered up, how does it start without a user doing a login?
There is no keyboard, screen, etc. Only the network cable.

I would appreciate some help here.
I hope I don't come across as silly and useless, I have simply never had to deal with a Server before, so I need some hand holding for a while. I have Ubuntu desktop and Windows 7 dual boot.

Thanks

---

### Post by merelin on 2011-03-07
> **ReginaldPerrin3 said:**
> I must confess to being a bit of a noob when it comes to servers and things. I have an H340 Home Server, and I really want to eliminate any Windows on it.
Having read what people have written here, I installed Ubuntu Server 10.10 on an empty drive via an existing machine. Then I removed the supplied 1 TB drive with Windows Server on it from the H340, inserted the new Ubuntu server drive.
Now I can power up the machine, the lights come on, the network light flickers with activity, and...
Well, I am at a bit of a loss at what to "do" now.

The H340 is connected to a router, just like my existing machine, so it gets an IP address from the DHCP server in the router.
How do I actually connect to the H340? I really don't know. Do I go "Places->Network"? or "Places->Connect to Server"? Or do I do a remote desktop connection?
When it is powered up, how does it start without a user doing a login?
There is no keyboard, screen, etc. Only the network cable.

I would appreciate some help here.
I hope I don't come across as silly and useless, I have simply never had to deal with a Server before, so I need some hand holding for a while. I have Ubuntu desktop and Windows 7 dual boot.

Thanks

ReginaldPerrin3,

On Ubuntu Server you would generally want to install openssh-server to be able to login to your server via terminal. You would want to install either samba server or NFS server to be able to share your files over the network. Further on you would probably want to install media server software on the box.

---

### Post by excogitation on 2011-03-17
> **merelin said:**
> Guys,

I've posted a deb file for mediasmartserverd here:

[http://www.mediasmartserver.net/forums/viewtopic.php?p=78292#p78292](http://www.mediasmartserver.net/forums/viewtopic.php?p=78292#p78292)

Sorry guys, this duplicate is due to a connectivity issue. Can't be deleted.

hey, did you also by any chance build an amd64 version for it, or can you tell me how to package it for 64 bit?

---

### Post by merelin on 2011-03-18
> **excogitation said:**
> hey, did you also by any chance build an amd64 version for it, or can you tell me how to package it for 64 bit?

excogitation,

Both versions are there:

[http://www.mediasmartserver.net/forums/viewtopic.php?f=23&t=7720&start=45](http://www.mediasmartserver.net/forums/viewtopic.php?f=23&t=7720&start=45)

---

### Post by excogitation on 2011-03-18
> **merelin said:**
> excogitation,

Both versions are there:

[http://www.mediasmartserver.net/forums/viewtopic.php?f=23&t=7720&start=45](http://www.mediasmartserver.net/forums/viewtopic.php?f=23&t=7720&start=45)

Thanks.
Do you have a script at hand to control the led's according to events like failure, smart status and the like?

Another question you might have an answer for - does the H340 boot from pcie? I'm at the moment running a 10.10 from USB with [log to ram]("http://www.tremende.com/ramlog/") and want to put in a pcie -> cf adapter card provided the box boots from pcie.

---

### Post by dsmturbo on 2011-05-04
Can I run the desktop version on Easystore, or do I need to run the server version?

---

### Post by nerr on 2011-05-06
dsmturbo, I suppose I don't see why you wouldn't be able to run the desktop version, but keep in mind that you'll need a video adapter if you actually wanted to use this as a "desktop" machine.  If you are simply worried about the terminal interface, I suggest just giving it a shot anyway; once you learn, you'll never want to go back.

Because I haven't posted in this thread for a while, pictures to come of my server with its setup.  I've been running Ubuntu Server for nearly two years now, and can't live without it now.  This server is easily one of the best investments that I've ever made.

EDIT: Also, has anybody figured out a way to get the one-touch backup working?  I'd love to be able to plug in a drive, and then script the device to perform a backup at the touch of a button.

---

### Post by chris.delacy on 2011-07-15
Hello all.... I am chris a relative noobie to linux server stuff, well servers in general but I ended up the proud owner of an Acer H340 unfortunatly I don't like windows much and had several problems with it including after updates being kocled out of it.... so I decided if I have a server it must be Ubuntu. I followed the instructions to change it to a ubuntu server but struggled with one piece which is how exactly do you remove the line ?
 when I have attempted to do this by the CNTRL "O" it seemed to work then CNTRL "Z" but no changes seem to be written 
When I restart and look the line is still there

Could anybody give me a nudge in the right direction

---

### Post by chris.delacy on 2011-07-15
i have followed you right upto getting rid of the line i'm a bit of a noobie at playing with code like this 
could you PLEASE give me few clues

---

### Post by one9one on 2011-08-30
> **chris.delacy said:**
> Hello all.... I am chris a relative noobie to linux server stuff, well servers in general but I ended up the proud owner of an Acer H340 unfortunatly I don't like windows much and had several problems with it including after updates being kocled out of it.... so I decided if I have a server it must be Ubuntu. I followed the instructions to change it to a ubuntu server but struggled with one piece which is how exactly do you remove the line ?
 when I have attempted to do this by the CNTRL "O" it seemed to work then CNTRL "Z" but no changes seem to be written 
When I restart and look the line is still there

Could anybody give me a nudge in the right direction


Are you using "sudo nano filename", then entering your password?

---

### Post by one9one on 2011-08-30
Using the 70 persistent fix and a static IP address , I was able to load Ubuntu Server 10.04 "64" bit (with only SSH included), replacing WHS.  The drive was created using a PC and CD, and then moved.

I tried 11.04 32 bit Server with a bunch of packages, and that didn't work.  Ping didn't return anything.  Maybe someone wants to try it.  I should have tried it with SSH only.

As I have read somewhere, you want to load Windows Home Server at least once, to configure the network hardware.

---

### Post by drewski803 on 2012-02-19
I am looking to sell this model with a fresh Ubuntu installation. Its a great box, but we need more speed for our industrial uses. Asking $400 w/shipping. PM me.

---

