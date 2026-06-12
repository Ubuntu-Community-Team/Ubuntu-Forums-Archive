---
title: "Vbox wont run 98"
date: 2010-02-22
forum: Virtualisation
---

### Post by degarb on 2010-02-22
I ran install for xp, 2000 and 98 as guest.   Windows 98 took about 12 hours to install.  And once it runs, it takes 20 seconds for some clicks to be sent to guest.   XP and 2000 installed in normal time.   But there are two reasons for me to not use them.  

I also have a legal copy of windows me, but probably the install would be same as 98.   Any alternative vm or way of making 98 run quicker?  

Also, out of curiosity, could you get grub to mount an external usb drive and I just install 98 on the external drive as a dual boot?


-----------------
offtopic:
I really would like a slipstream or light xp or 2000 with all crap taken out, to run on smaller machine.   I would even pay for light windows 7 to run on 2003 specs.  But not at ms prices.

---

### Post by LowSky on 2010-02-22
Why do you want to run a 12 year old operating system?
Forget security, just trying to find the right drivers is going to be insane.

---

### Post by degarb on 2010-02-22
Well, 98 is legal.  Xp to win 7 licensing is too expensive for the modern 5 + computer house.  They consider you a renter not an owner of your Operating system.  (Being a renter/serf is never good).  Also, someone like me spent all of free time for at least 3 years to find perfect windows software, rejecting most due to bugs, missing features, bloat, overly steep learning curve, or awkward design.   

And there is major critical missing applications in linux--as nice as ubuntu is, as simple as it is to find most common apps (internet, office and multimedia).  Take voice dictation: this is every bit as important as owning a keyboard.  160 words a minute verses my 40 word typing.   (I could go on with other missing software, but would forget a bunch and get mired down with debate over specifics.)   Then, there is giftware (for kids).   Take my daughter,  we cannot get her to play a single downloaded (educational) game (like typing).  But put a cd in her stocking, and she will play and learn (just her age and mindset).  Half of these programs won't run on wine.   The wine forum here seem pretty dead, too. 

----

(I have use three my self: one laptop dedicated to living room for everyone, on in office, and one portable.  And one per kid.)  That is alot of OS's to buy.

---

### Post by lykwydchykyn on 2010-02-22
I sympathize with your plight.

Unfortunately, last time I checked, VBox doesn't support Windows 98 very well.  They don't have a windows 98 graphics driver, and the guest tools don't really work.

You might have better luck running qemu; I've run windows 98 in it before, though it's been a while since I tried.  qemu is in the repositories, and I think there's a GUI or two available for it as well.  Just search in synaptic for qemu.

Chances are a lot of modern software won't run in 98, though. Unfortunately, for law-abiding citizens who want to run Windows software, the only fool-proof option is to shell out the money for Windows.  I ran into this problem recently when one of my kids got "lego starwars" for Christmas and it wouldn't run on his Windows 2000 dual-boot.  Fortunately we had another computer that had come with Vista.

This would be part of the reason a lot of us want to see better third-party support for Linux.  Until that happens, you just have to decide if having Windows applications available to you is worth the cost of a Windows license or two.

---

### Post by eriktheblu on 2010-02-22
98 doesn't appear to be well supported. Listed requirements are "Requires VT-x or AMD-V hardware virtualization support." Check your hardware for comparability.

2K pro is what I use virtualized, I got it 5 or so years ago through Amazon for under $100 US. It isn't free, but can be found cheaper than XP, Vista, or 7.

I take that back, you could probably find copies of Vista in a dumpster behind your local software store :D.

---

### Post by degarb on 2010-02-22
do you mean gxemu

---

### Post by bodhi.zazen on 2010-02-22
> **lykwydchykyn said:**
> Unfortunately, last time I checked, VBox doesn't support Windows 98 very well.

I have not tried Windows 98, and although I have seen some people claim it works, I have seen problems with it.

Last time I searched, the VBox developers were interested in supporting more modern versions of Windows.

If you do not like Microsoft, do not use their products. What is it Linux will not do for you the Windows 98 will ?

---

### Post by lykwydchykyn on 2010-02-23
> **degarb said:**
> do you mean gxemu

No, qemu.  The package name to install it is qemu-kvm.  It's a command-line based virtualization system, but there are graphical front-ends available - qemulator and qemuctl.  Couldn't tell you which front-end it better, but they both just run qemu.

---

### Post by Mark Phelps on 2010-02-23
> **degarb said:**
> ... Windows 98 took about 12 hours to install.  And once it runs, it takes 20 seconds for some clicks to be sent to guest. 

Maybe I missed it, but how fast is your processor and how much system memory do you have?  

If this is a Win98-era machine, typically with a 233MHz processor and 128MB of memory, then trying to run ANY VM product on such an underpowered machine is going to be painfully slow.

---

### Post by degarb on 2010-02-23
1 ghz cpu and 512 ram.  6 gig internal and 1.5 external (for today)

The gui I am using is qtemu, now.  No luck with compressed btrfs.  emu kept crashing.  I reformatted ext4 and am now trying to install 98.   The drive through put still seems very slow; just copying all files for setup to drive is taking 188 minutes.  I tried installing 2000 on a compressed btrfs, but unpacking files was looking like it would take 40 hours, so I aborted.  At least in vbox, 2000 installed like a snap in vbox, just didn't have enough room to finalize throwing all the extras on the machine. 

The drive throughput wasn't a problem with vbox.  But, vbox  came to crawl once it started configuring and registering windows 98 components.

---

### Post by lykwydchykyn on 2010-02-23
Is this a netbook with a SSD?

---

### Post by raydeen on 2010-02-23
I've seen something similar. I actually got a Win 3.1 guest running and the performance is very laggy. I'd go for a Win2000 guest if you can as it should run much better and will have better support.

---

### Post by bodhi.zazen on 2010-02-23
Moved to the virtualization formus.

---

### Post by degarb on 2010-02-23
I am trying qtemu front end.  Do other front ends use different qemu?  I just am not having luck with 98 installing.  It took near 200 minutes unpack the files, and seems to lock up after that point.  


On an aside, would it not be easier for the guest os to just send print jobs to the host, use the sound on the host, use as much as possible on the host machine.  Thus, someone like me wouldn't have to worry if some periferal had a windows 98 driver.  Longer life cycle of an aging os.

---

### Post by egalvan on 2010-02-23
> **degarb said:**
> -----------------
offtopic:
I really would like a slipstream or light xp or 2000 with all crap taken out, to run on smaller machine.
I would even pay for light windows 7 to run on 2003 specs.  But not at ms prices.


This takes $
[http://www.litepc.com/](http://www.litepc.com/)


This takes Time
*Slimming Down Windows XP: The Complete Guide*

[http://www.graphixanstuff.com/Forum/index.php?showforum=68](http://www.graphixanstuff.com/Forum/index.php?showforum=68)

---

### Post by pirateghost on 2010-02-23
> **egalvan said:**
> This takes $
[http://www.litepc.com/](http://www.litepc.com/)


This takes Time
*Slimming Down Windows XP: The Complete Guide*

[http://www.graphixanstuff.com/Forum/index.php?showforum=68](http://www.graphixanstuff.com/Forum/index.php?showforum=68)

or do your own slipstream cd
[http://www.nliteos.com/](http://www.nliteos.com/)

---

### Post by Shazaam on 2010-02-23
From a dusty old memory  :)...
Try changing the Win98 machine type to fix acpi problems. I think it is under Device Manager. Win98 may have it listed as "Standard PC".
Try searching the VBox AND VMWare forums for a Win98 acpi fix. It's been a while but you might be able to find something.

---

### Post by degarb on 2010-02-23
> **Shazaam said:**
> From a dusty old memory  :)...
Try changing the Win98 machine type to fix acpi problems. I think it is under Device Manager. Win98 may have it listed as "Standard PC".
Try searching the VBox AND VMWare forums for a Win98 acpi fix. It's been a while but you might be able to find something.

I am trying to search this. I am vaguely getting:  acpi something to do with hal.  Is hal not included in Lucid lynx, ergo vm ware wont run on next version of Ubuntu?

---

### Post by lykwydchykyn on 2010-02-23
> **degarb said:**
> I am trying to search this. I am vaguely getting:  acpi something to do with hal.  Is hal not included in Lucid lynx, ergo vm ware wont run on next version of Ubuntu?

VMware will run on the next version of Ubuntu, you can be sure of this.  HAL stands for "hardware abstraction layer", and both Linux and Windows have one.  

The current HAL on Linux is being replaced in the next Ubuntu by other services.  Its functionality isn't going away.

In any case, the issue here is acpi on Windows 98, not acpi for Linux.

---

### Post by degarb on 2010-02-23
I went down the road and bought a 10 dollar ten gig drive for the external usb case.  Ubuntu says it has many bad sectors.  Is Ubuntu going to write around these okay?  Or should I rush it back to get a refund and any accrued damages?  :P

I went ahead and installed windows 2000 on it.  All went okay.  No msconfig for some reason.

Also, I still don't think the video driver is ideal.  Only 16 colors and 600 by 800 resolution.  Do I get that funky driver for windows 98.

---

### Post by degarb on 2010-02-23
I did get 98 installed on qemu but I think less successful than vbox.  Video driver likely issue there.

---

### Post by lykwydchykyn on 2010-02-23
> **degarb said:**
> I went down the road and bought a 10 dollar ten gig drive for the external usb case.  Ubuntu says it has many bad sectors.  Is Ubuntu going to write around these okay?  Or should I rush it back to get a refund and any accrued damages?  :P

I wouldn't plan on it working very well if it's full of bad sectors.  
> 
I went ahead and installed windows 2000 on it.  All went okay.  No msconfig for some reason.

Also, I still don't think the video driver is ideal.  Only 16 colors and 600 by 800 resolution.  Do I get that funky driver for windows 98.

Did you install the "guest additions" in VBox?  Or are you using qemu?

---

### Post by degarb on 2010-02-24
The 98 qemu install was resulted in an unusable video driver and disk access seemed very slow.  

So, on this 10 gig (many bad sector) HD, I installed windows 2000 as guest.  I went very well and seems to run okay,  but the video driver has only 16 colors and reduced resolution.  I need to figure out what driver to download and any direct x or other plugins to allow kids games.

---

### Post by degarb on 2010-02-24
I haven't got as far as looking at guest additions.  Will check it out.

---

### Post by lykwydchykyn on 2010-02-24
> **degarb said:**
> I haven't got as far as looking at guest additions.  Will check it out.

That installs all the video/audio/whatever drivers.  It's pretty painless.

---

### Post by degarb on 2010-02-24
I figured nothing to loose  So I installed xp sp3 too.  Note this is on my pentium 3 (reading 600 ghz in xp) with 512 meg ram.  Interestingly, after I adjusted for best performance and turned off unneeded services and startup items.  It runs more smoothly than windows 2000, which ran more smoothly than 98 (a disaster).  Plus, it has more bells and whistles. 

2000 takes 1.7 gig of vdi and xp is about 3 gig.  Out of box.  I don't know how long I can run this version of xp before I can no longer, so I should get 2000 up to snuff though.

---

