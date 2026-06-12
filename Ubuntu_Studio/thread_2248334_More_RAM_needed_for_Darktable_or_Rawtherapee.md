---
title: "More RAM needed for Darktable or Rawtherapee?"
date: 2014-10-14
forum: Ubuntu Studio
---

### Post by bulevardi on 2014-10-14
Hi,

[SIZE=1](don't know if I had to put this into the Hardware section or the Ubuntu Studio section)
[/SIZE]
I'm new to Linux, (using Ubuntu Studio) and want to proces raw files for photography.
I just did some tryouts in RawTherapee, DarkTable, ... 
But when doing some changes, like contrast etc.. by pulling the faders in the menu, the photo gets updated with a slight delay on my screen. Mostly around a second. Quite annoying.

I suppose this problem does not exist on new computers, and will only affect older ones, like mine. Or does this problem occur on new computers aswel?

[B]Could I solve this problem by (for example) just upgrading my RAM?
I can upgrade to 8GB ram if needed.
Or should it be upgraded by a better graphics card?[/B]

Mine is 7 years old now, with the following specs:
Motherboard: MSI Neo P35 F
Processor: Intel Core 2 duo 2.13 Ghz, E6420, fsb1066 4mb lga775
RAM:  Kingston Memory 2x 1gb 667mhz DDR2, pc2-5300 non ecc 240 pin
Graphics card: XFX 8GF-8600 GTS, 675M 256 MB DDR3

Thanks for the advice!

I know that photo processing software can get slow, on my other pc with 6gig ram, it can get slow aswel, but probably that's because of the Windoze environment ;)

---

### Post by redbull00 on 2014-10-14
My bet is that 2GB RAM is definitely insufficient for that, not to mention more advanced filters that require more memory. In general for comfortable work with large images, I'd recommend at least 8GB RAM. Anyway it would be best if you bought new hardware because DDR2 is more expensive than DDR3 at least where I live. It is because it got old and fewer chips are being produced. It is also considerably slower which is also not without meaning and often becomes a bottleneck of the whole system. If you buy DDR2 and then decide to buy a new PC, the DDR2 won't fit to it.

---

### Post by bulevardi on 2014-10-14
I suppose DDR3 RAM won't fit on a DDR2 motherboard?
Although, the graphics card seems to be DDR3... hmm.
I'm not that technical. Not going to buy new motherboard, will cost a lot more too.

Then it still depends where I'd buy it. When I buy this in a local shop, it costs me 4 times as much as on Ebay from China. 
Although that last one seems warranty-wise not a good idea...

---

### Post by naradezza on 2014-10-14
more big of ram, so you will get mre space to application use, you need upgrade your ram and more great you upgrade your motherboard too

---

### Post by redbull00 on 2014-10-14
Your graphics card has built in RAM which has nothing to do with ram for your motherboard. DDR2 is not compatibile with DDR3 and vice versa. If you buy DDR2 now and then decide to buy a new computer, the DDR2 you bought will be useless because now DDR3 is being used and both use different sockets. There are no adapters nor anything like that. You simply need more RAM, but for me upgrading DDR2 doesn't make sense for the already mentioned reasons.

---

### Post by bulevardi on 2014-10-15
I understand that a new computer would be better... but aswel 5 to 10 times more expensive as putting some new RAM in my old one.
I'm not really into this "consumer society" where we always immediately buy something new instead of repairing/upgrading something old.

And another huuuuge problem; since I had this Marriage bug few years ago, the system installed Wife 1.0, which forces me to justify all the expenses I make. The Wife 1.0 firewall does not seem to give error messages when justifying smaller amounts of money ;)

---

### Post by Michael_McKenney on 2014-10-15
My Windows 7 x64 workstation has Adobe Photoshop CS 6.  It has 16GB of RAM.  I could use 32GB for the newer camera RAW formats.  RAM keeps files in memory instead of paging.  RAM on newer boards is not expensive $20-$40 a GB.   The problem is 16-32 GB can cost a lot of money.  I tell people to find a board that supports 16-32GB of RAM with 4 slots minimal.  Add RAM in 4 or 8 GB sticks at a time.  So you don't replace RAM.  I would not invest in ram for older boards.   Spend the money and upgrade to new boards, CPUs, and RAM.  It is a better investment.

---

### Post by kurja on 2014-10-15
I've been using Darktable for a few years now, on old and old-er computers. Yes, it wants a lot of memory, and yes, it wants a lot of processing power. Afair, for very basic work, 2gb should be enough; if you handle large amounts of images, have very high resolution images and/or use a ton of plugins you might want more - but you can just use system monitor to see if you're running out of ram or not? (I just tried it, and after opening a raw photo with half a dozen plugins applied to it, Darktable is using about 900 megabytes. Add system processes and maybe some other app, and you probably won't have much if any left over of your 2 gigs.)

What I've experienced to be a huge boost to Darktable is enabling OpenCL. Sadly, to be really efficient it needs a video card that has plenty of ram of it's own, 256 that you have  really isn't enough. But if you can get a nice cheap gpu - think second hand gaming cards from a few years back - that has one gig or more of memory on it, it could really boost performance, for a lowish cost. Not that just adding ram couldn't sweeten things too.

---

### Post by bulevardi on 2014-10-15
> **kurja said:**
> I've been using Darktable for a few years now, on old and old-er computers. Yes, it wants a lot of memory, and yes, it wants a lot of processing power. Afair, for very basic work, 2gb should be enough; if you handle large amounts of images, have very high resolution images and/or use a ton of plugins you might want more - but you can just use system monitor to see if you're running out of ram or not? (I just tried it, and after opening a raw photo with half a dozen plugins applied to it, Darktable is using about 900 megabytes. Add system processes and maybe some other app, and you probably won't have much if any left over of your 2 gigs.)


Very interesting to montitor this. 
Just tried with gnome system monitor.

With only the terminal and the system monitor opened, I had the following results:
CPU: between 5-10%
Memory: 344Mb, 17%

When opening Darktable and changing some faders in the menu:
CPU: went up to 70, 80 sometimes to 100%
Memory: 944Mb, 46%

When exporting one photo to save as jpg (max resolution):
CPU: went up to 100% too.
Memory: went up to 1,6 Gb, 83%

---

### Post by bulevardi on 2014-10-15
> **kurja said:**
> 
What I've experienced to be a huge boost to Darktable is enabling OpenCL. Sadly, to be really efficient it needs a video card that has plenty of ram of it's own, 256 that you have  really isn't enough. But if you can get a nice cheap gpu - think second hand gaming cards from a few years back - that has one gig or more of memory on it, it could really boost performance, for a lowish cost. Not that just adding ram couldn't sweeten things too.

Hmm, but maybe it won't increase the speed, according to this article:
[http://www.tomshardware.com/reviews/graphics-card-myths,3694-5.html](http://www.tomshardware.com/reviews/graphics-card-myths,3694-5.html)
> [h=3]Video memory enables resolution and quality settings, does not improve speed[/h]  Graphics memory is often used by card vendors as a marketing tool.  Because gamers have been conditioned to believe that more is better,  it's common to see entry-level boards with far more RAM than they need.  But enthusiasts know that, as with every subsystem in their PCs, balance  is most important.



---

### Post by kurja on 2014-10-15
What you quoted there is true for most applications - but not in this case. Just like processing photos on your CPU you need RAM; to process them on the GPU you need memory on it. Modern GPU's have a lot of (a ***lot*** of) processing power, just look at 3d graphics in modern games - they're absolutely incredible. Actual supercomputers have been built out of those things. Usually in normal use not so much memory is required, unless using extremely high resolutions, for an example to drive a work space across multiple monitors. But, GPU's have other uses too: for maximum performance in rendering graphics, they are capable of running parallel processes (hundreds of them) and this makes them very powerful indeed for certain computational tasks, and, that is where we get lucky with Darktable and it's OpenCL support =)

I have twice the CPU cores and at a higher frequency than your core2duo intel, and the gaming gpu that I bought from a gamer friend of mine runs Darktable plugins faster than my CPU.

---

### Post by jejeman on 2014-10-16
Using Rawtherapee for more some time now. Only placing faster CPU (i5) speeded up things, but still is slow. I have 4GB of RAM, and RT tends to use it all (together with OS). 4GB is minimum.

---

### Post by bulevardi on 2014-10-16
I have another pc here, 2 year old with windows on it,..  running a raw converter there pushes the CPU to 98% too. (Intel i3, 6 gb ram ddr3). Just checked and saving a photo uses 3,5 gb ram.  So anyway, ram needs higher.
Maybe a new graphics card with memory too... but a new pc won't be an option :)

---

### Post by kurja on 2014-10-16
where are you located? I might have some extra ddr2 lying around that I could give away.

---

### Post by bulevardi on 2014-10-17
Live in Belgium, around Brussels. 
Just realized that I changed the graphics card of that computer few years ago, because the old one didn't work anymore. I then didn't think about the things I would do now and bought the cheapest I could get for around &#8364; 20, it has 512 Mb ram on it instead of the 256 I mentioned. Whooa! What an upgrade ;)

---

### Post by kurja on 2014-10-17
:) 512 is enough to give opencl a try: it's likely to quickly run out and might not get enabled without a tweak or two, but I've done it in the past. In Darktable click the 'cogwheel' symbol, core options, check enable opencl. Then restart darktable with ```
darktable -d opencl -d perf
``` and look for this line: **[opencl_init] FINALLY: opencl is AVAILABLE on this system. **If that's not to be found, line **[opencl_init] opencl_memory_requirement: <amount> **is of interest. That value can be modified in /home/<user>/.config/darktable/darktablerc file. See this page for reference: [http://www.darktable.org/2012/03/darktable-and-opencl/](http://www.darktable.org/2012/03/darktable-and-opencl/)

I'm saying, it's not likely to work so great with just 512 video ram, but should work sufficiently to give you an idea of what it can do.

---

### Post by kurja on 2014-10-17
> **bulevardi said:**
> Live in Belgium, around Brussels. 
Just realized that I changed the graphics card of that computer few years ago, because the old one didn't work anymore. I then didn't think about the things I would do now and bought the cheapest I could get for around € 20, it has 512 Mb ram on it instead of the 256 I mentioned. Whooa! What an upgrade ;)

What make and model is your current video card? I'll look around next monday what ddr2 memory sticks I still have around.

---

### Post by bulevardi on 2014-10-19
Will have to check the type of that card, but the brand is Gigabyte.

I'll try the opencl workaround too when I'm home. I'll let you know the results.
(there will be something similar for RawTherapee I suppose?)

Will have a try with another graphics card too from this other 2 years old computer I have (a geforce 510 card, goes probably to 1 gb):
[http://www.geforce.com/hardware/desktop-gpus/geforce-510-oem/specifications](http://www.geforce.com/hardware/desktop-gpus/geforce-510-oem/specifications)
But this is a small format computer, so I don't know if it would fit in a normal bigger desktop case. Will try this as soon as I have time for it.

As far as I read on internet, just upgrade RAM won't change so much, it probably lies on my graphics card, or more likely my processor, but replacing that last one is not my cup of tea.

---

### Post by kurja on 2014-10-19
Adding ram speeds up your computer only if it's currently running out of memory, adding a faster video card only speeds up your computer if you're running software that can use the additional gpu power, and likewise a faster cpu only helps if your current one is already running at 100% load... And it seems all three are true in your case. Certainly, upgrading the whole box would give best results for raw photo editing but I'm promoting the gpu/opencl route here because afair it would give the most bang for the fewest bucks, so to speak.

I've never used raw therapee, a quick googling suggests that opencl support is at least in the works if not already supported, but I don't know.

---

### Post by bulevardi on 2014-10-19
The opencl solution didn't work out. Couldn't check/uncheck the box in Darktable. When running the command in my terminal I got this line:
[opencl_init] FINALLY: opencl is **NOT** AVAILABLE on this system
I changed the memory in that configfile to the amount of memory I have on my graphics card (512), did not change the performance speed.

Anyway, in the mean time looking for maybe upgrading the CPU, does not seem to be quite difficult, but I'm new to this. So doing some research on all stuff like RAM, Graphics Card, and now CPU.
Need to have the right socket that fits the motherboard (775). Ghz, Mhz and Mb cache needs to be as high as possible I suppose.
Just need to make sure the voltage and power is right. But what about heat/cooling? No problem? 
I'm not quite sure wether I need to get a dual core (as I have right now) or a quad

I'm sure I can still upgrade this pc to a good speed at an affordable price instead of buying a brand new one.

The CPU I currently have is :
Core 2 Duo E6420     2.13 GHz     4 MB     1066 MT/s     0.85–1.5 V     65 W   

A nice upgrade would be (for only 50 $ new) : 
Core 2 Duo E8600     3.33 GHz     6 MB     1333 MT/s     0.85–1.3625 V     65 W     LGA 775

But this seems even better (90 $ used) , ... it's only 95 watt instead of 65 is probably a problem for power supply:

Core 2 Quad Q9650   3 GHz       2 × 6 MB     1333 MT/s     0.85–1.3625 V  95 W

Have to check what kind of power supply is installed. ...

---

### Post by jejeman on 2014-10-19
Go for C2Q if MB supports it.

---

### Post by kurja on 2014-10-19
+1, quad cpu would be much better.

You're not seeing a performance boost from opencl if it's not available, obviously. Maybe your GPU doesn't support it, you didn't say which gpu it is, but anyway you shouldn't try to allocate **all** of your video ram for opencl use - it will need some to continue drawing things on your screen ;)

---

### Post by bulevardi on 2014-10-20
> **kurja said:**
> Maybe your GPU doesn't support it, you didn't say which gpu it is, but anyway you shouldn't try to allocate **all** of your video ram for opencl use - it will need some to continue drawing things on your screen ;)

It's Gigabyte GeForce 210,  512mb on board DDR3, turbo cache to 1gb.
Should support Opencl, as far as I googled.

For the processor, the quad seems ok, takes more Watt than the previous one... but my power supply (antec 430) seems to produce max 430 watt... should be fine I guess... 
Would I take the risk for a second hand cpu like from amazon or ebay, or would a new boxed version be the better idea?

---

### Post by kurja on 2014-10-20
> **bulevardi said:**
> It's Gigabyte GeForce 210,  512mb on board DDR3, turbo cache to 1gb.
Should support Opencl, as far as I googled.

For the processor, the quad seems ok, takes more Watt than the previous one... but my power supply (antec 430) seems to produce max 430 watt... should be fine I guess... 
Would I take the risk for a second hand cpu like from amazon or ebay, or would a new boxed version be the better idea?

Maybe try editing darktablerc line **opencl_memory_requirement<amount> **to 500 and **opencl_memory_headroom<amount>**to 256. First is the minimum detected amount of memory for registering the device as an opencl unit, second is the amount of memory left untouched so it can continue operating normally (updating your screen). Default memory_requirement is I think 768. You can try pulling the second number further down if opencl won't come available, or increase if your machine crashes ;)

Can't really advice on new versus second hand, my own machine is almost entirely built of scrap parts... :) to each his own, new is new and has a warranty but used is cheaper, your call really. What I'd maybe pay attention is the cooler, having a higher wattage cpu means more heat and more fan noise, if your old one is good, or does the 2nd hand one come with one, or is one included with the new cpu...

---

### Post by bulevardi on 2014-10-21
Just tried with the other graphics card, the Geforce GT510. 
Same problem in Darktable: opencl is not activated.

Seems that other people seem to have this issue too:
[http://darktable.org/redmine/issues/9844](http://darktable.org/redmine/issues/9844)
[http://darktable.org/redmine/issues/10055](http://darktable.org/redmine/issues/10055)

When using RawTherapee now, even with a graphics card that is 2 times better, it takes the same amount of usage of cpu/memory when testing in system monitor.
Exporting a file as jpg goes up to 100% cpu usages and 1,6 out of 2 gb ram.

I'm wondering, when adding a new graphics card, do you need to change this in your BIOS or update this somewhere, so he'll recognise the opencl or something?

---

### Post by kurja on 2014-10-21
> **bulevardi said:**
> Just tried with the other graphics card, the Geforce GT510. 
Same problem in Darktable: opencl is not activated.

Seems that other people seem to have this issue too:
[http://darktable.org/redmine/issues/9844](http://darktable.org/redmine/issues/9844)
[http://darktable.org/redmine/issues/10055](http://darktable.org/redmine/issues/10055)

Bummer :( I can't really help you any further on that if it's actually not recognized as an opencl device.
> **bulevardi said:**
> 
When using RawTherapee now, even with a graphics card that is 2 times better, it takes the same amount of usage of cpu/memory when testing in system monitor.
Exporting a file as jpg goes up to 100% cpu usages and 1,6 out of 2 gb ram.

I'm wondering, when adding a new graphics card, do you need to change this in your BIOS or update this somewhere, so he'll recognise the opencl or something?
No, if you're getting anything on the screen after booting up with a new card you do not need to change anything in bios. There may be some settings in there concerning video cards but they're likely to autodetect unless you've manually changed them before.

I've never used rawtherapee but it's likely that just as Darktable, it has a setting to enable opencl. Or, like Darktable, it's not recognizing your gpu as an opencl device - or if rawtherapee actually uses opencl at all. If it doesn't, a faster video card will do absolutely nothing for your photo editing.

---

### Post by bulevardi on 2014-10-21
> **kurja said:**
> 
I've never used rawtherapee 

It's ok, I can live with that ;)
The faders seem more easy to handle for me in Rawtherapee, and the geometric options for perspective corrections seem more handy in my workflow.
Apart from that, both are kind of the same software to me.

> **kurja said:**
> If it doesn't, a faster video card will do absolutely nothing  for your photo editing.
I see. The faster video card didn't seem to make much difference on first sight... 
But on the other hand, would a better processor give much more better results on graphics?

I could give it a try ... maybe together with boosting up the RAM from 2gig to 8gig.

---

### Post by kurja on 2014-10-21
Yes, faster cpu would help. More ram would help as well.

---

### Post by jejeman on 2014-10-21
I don't think Rawtherappe uses GPU for computing, never saw that option. I have decent GPU and would benefit greatly if it could.
For RT just CPU and RAM. As I said, even with i5 it is slow, and i5 is much faster than C2Q.
I also find RT more pleasant for work than DT, although DT has some nice features.

---

### Post by kurja on 2014-10-22
> **jejeman said:**
> As I said, even with i5 it is slow, and i5 is much faster than C2Q.

Depends on the exact model, some of the cheapest i5's actually rank worse in benchmark tests than the best core2quad models.

---

### Post by bulevardi on 2014-10-23
Did some ebay shopping, came around  &#8364; 186 for 8gig ram + core2quad cpu (shipping included) from somewhere in china.
Will be here in a few weeks. I'll let you know if it works out or not!
Note of the cpu seller: "New: other:  performance as new condition"    (which means used... but I give it a try) It it's not working, I haven 't lost lost a fortune.
Will buy some thermal paste in the local shop next week.

---

### Post by bulevardi on 2014-11-07
My new RAM just arrived ! 
8 gig installed instead of 2 right now. The system recognizes it well, even though it's not from a specific brand. 
"white label". It's the same as the replaced Kingston memory that is made in China aswel, probably all made in the same factory IMHO. Looks totally the same, only the brand name on the sticker is different.

Anyway, the problem isn't resolved. Some things seem to work faster, but changing faders in DT or RT still make my screen flicker with a delay. 
Doing that, the System Monitor displays the CPU going up to 93%.


So, waiting for the quad core CPU to arrive, hopefully next week. 
I'll let you know how that works out as soon as I got it installed!

---

### Post by jejeman on 2014-11-07
As I said, just CPU... but will see.
Anyway, I tried RT on 2GB system - it's no use...

---

### Post by bulevardi on 2014-11-13
I just installed the new CPU, and since then, I cannot boot anymore. 
I  only get the startup screen with message: "press tab for post, press  del for bios". But whatever I press, nothing happens. The system shuts  down after a minute or so.
There even is no beep.

What should I do now? 
Should I update BIOS? The pc is like 7-8 years old so I suppose it needs an update for newer CPU's.
And how should I do that if I cannot start.

Or  should I try again with the old CPU first to check if nothing is wrong  with the motherboard, to verify it's not the CPU or something that fried  the motherboard while installing the new cpu?
Hmm
I probably messed up, my own fault, but ... Not giving up anyway ;)

---

### Post by jejeman on 2014-11-16
Mybe the CPU is bad.
Test it elsewere.

If there is, you can try to update BIOS.

---

### Post by bulevardi on 2014-11-17
> **jejeman said:**
> Mybe the CPU is bad.
Test it elsewere.

If there is, you can try to update BIOS.
Hmm, haven't got another pc where that CPU fits into. Cannot test this way.
 
Anyway... I've just put in my old CPU again, everything still works fine.
Maybe I'll upgrade the BIOS as soon as I know how. (it's quite delicate)
After that, I'll try with the new CPU again.
Hopefully it'll work out.

---

### Post by bulevardi on 2014-11-19
Alright, the story continuous.
Yesterdaynight, I flashed the bios. (I put FreeDOS on a USB stick, and the Flash Utilities from the Mobo Manufacturer).

Got this picture after flashing:
[[IMG]https://farm6.staticflickr.com/5612/15823581711_4aa62ba3ab_o.jpg[/IMG]]("https://flic.kr/p/q7gZyk")

But after rebooting, went into BIOS, set Optimized Defaults, then the system rebooted automatically...
And then... the screen stayed black, no beep, no cursor, no keyboard numlock light. Couldn't get into BIOS anymore,... 

This morning pulled out the CR 2032 battery out of the Mobo for a while. 
At some point, Ubuntu started...could get acces to my hard drive files, ... but when rebooting the pc, the problem continued;  
I now can get into BIOS again, or I get a menu screen titled "GRUB Version 2...." with a possibility to select:
- Ubuntu (low latency)
- Ubuntu
- Memory test...
- Other Memory test
- ...
Each option I select: the screen just goes black with a flickering cursor.
Can't go further than that.

Anyone an idea what I should do now? Change some settings in BIOS? How to avoid GRUB pops up instead of booting ubuntu right away?
Reïnstall Ubuntu via a Live CD I have? 
When I ever get Ubuntu started, should I set some settings right somewhere?

Actually, should I start a topic in the Hardware section? Because at the moment, this has not much to do anymore with the beginning of the topic.

---

### Post by bulevardi on 2014-11-20
He mostly won't boot anymore after changing stuff in the BIOS setup, like the boot sequence,...  then I put the battery in/out again to make it work again.
Today I could get further and got Linux started somehow. 
Read about GRUB Customizer, and try to fix it with this program. Didn't work.
 Now pc boots with specific screen with texts like:
 "gave up waiting boot device", "missing modules", "ALERT", "dropping to a shell".
 "BusyBox v1.21.1" and then a commandline kind of program kicks off with <initramfs>.
 
Now I read somewhere I could fix this by "chrooting from a live cd", like this:
 [http://www.webupd8.org/2014/01/how-to-fix-non-bootable-ubuntu-system.html](http://www.webupd8.org/2014/01/how-to-fix-non-bootable-ubuntu-system.html)
 
Or here, this "bug" is mentioned too, but not with lots of unclear solutions for it:
 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360378](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360378)
 
Don't know yet what I'm going to try first.
 Does not matter for me if I have to reïnstall Ubuntu again and copy my harddrive files back from my backup harddrive.

---

### Post by bulevardi on 2014-12-02
Okay, the pc does not boot well anymore, something with the bootloader... but I'm dealing with that in another thread.

Anyway, when I finally get booted, I tried Darktable and RawTherapee on an image.

Darktable is still quite slow, slightly better... . But RawTherapee is a bit better too.
I can now see on the monitor that he has 4 processors (quad), and when changing the faders, they all go to 75%.
When saving an image, they all go up to 100%

A screenshot below as proof:

[ATTACH=CONFIG]258322[/ATTACH]

Just wanted to inform you guys about the progress I'm making  :)

---

### Post by uwe-bungto on 2014-12-02
> **bulevardi said:**
> Okay, the pc does not boot well anymore, something with the bootloader... but I'm dealing with that in another thread.

Anyway, when I finally get booted, I tried Darktable and RawTherapee on an image.

Darktable is still quite slow, slightly better... . But RawTherapee is a bit better too.
I can now see on the monitor that he has 4 processors (quad), and when changing the faders, they all go to 75%.
When saving an image, they all go up to 100%


Just wanted to inform you guys about the progress I'm making  :)

Darktable also makes use of OpenCL for processing. go into global preferences -> core options and check activate OpenCL support. This will make use of the GPU in your video card it is way more bang for the buck than upgrading the CPU

---

### Post by bulevardi on 2014-12-03
> **uwe-bungto said:**
> Darktable also makes use of OpenCL for processing. go into global preferences -> core options and check activate OpenCL support. This will make use of the GPU in your video card it is way more bang for the buck than upgrading the CPU

I know.
But the checkbox for OpenCl is greyed out and when mousing over it, it says "no opencl support available on this system".

Will try to install OpenCL with this workaround:
[http://wiki.tiker.net/OpenCLHowTo#Installing_the_Intel_CPU_ICD](http://wiki.tiker.net/OpenCLHowTo#Installing_the_Intel_CPU_ICD)

Will let you know if it works out!

---

### Post by bulevardi on 2014-12-03
GRRR, when doing this approach:
> TGT_DIR="/opt/intel-opencl-icd-VERSION.MINOR/lib"
mkdir -p "$TGT_DIR"
rpm2cpio intel_sdk_for_ocl_applications_*/opencl-*-intel-cpu-*.x86_64.rpm | cpio -idmv
cp ./opt/intel/opencl-*/lib64/* "$TGT_DIR"
echo "$TGT_DIR/libintelocl.so" > /etc/OpenCL/vendors/intel.icd
I get this message: 

"bash: /etc/OpenCL/vendors/intel.icd: file or folder does not exist"

---

### Post by uwe-bungto on 2014-12-03
> **bulevardi said:**
> I know.
But the checkbox for OpenCl is greyed out and when mousing over it, it says "no opencl support available on this system".

Will try to install OpenCL with this workaround:
[http://wiki.tiker.net/OpenCLHowTo#Installing_the_Intel_CPU_ICD](http://wiki.tiker.net/OpenCLHowTo#Installing_the_Intel_CPU_ICD)

Will let you know if it works out!

> **bulevardi said:**
> GRRR, when doing this approach:

I get this message: 

"bash: /etc/OpenCL/vendors/intel.icd: file or folder does not exist"

This is one of the undisclosed features of nVidia, it is not finding libOpenCL
Try this Thread [http://sourceforge.net/p/darktable/mailman/darktable-users/thread/201408031057.04064.christian.kanzian@gmx.at/](http://sourceforge.net/p/darktable/mailman/darktable-users/thread/201408031057.04064.christian.kanzian@gmx.at/)
[URL="http://sourceforge.net/p/darktable/mailman/darktable-users/thread/201408031057.04064.christian.kanzian@gmx.at/"]
[/URL]**   [COLOR=#000000][FONT=tahoma]Nvidia CUDA toolkit is a problem I had to remove the tool kit[/FONT][/COLOR]**
try
[COLOR=#000000][FONT=courier new]sudo find / -iname libopencl*

[/FONT][/COLOR]cat /etc/OpenCL/vendors/nvidia.icd

---

