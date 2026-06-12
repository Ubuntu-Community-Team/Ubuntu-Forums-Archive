---
title: "First Koolu Experience"
date: 2007-09-18
forum: Testimonials &amp; Experiences
---

### Post by Hal58 on 2007-09-18
My Koolu net appliance arrived this past Friday and was immediately hooked to a 1280x1024 LCD, USB keyboard, USB mouse and Ethernet router.  On boot, Ubuntu 7.04 (Feisty Fawn) came right up in 1024x768 mode, entered the final stage of setup.  Unfortunately, I couldn't be me (account name "hal" was prohibited, but I received notice today that the installer has now been fixed).  This little box gets a bit warm with heavy use, but at 10 watts consumption and an 80 GB laptop drive, that's expected in such a small package.

Video:  The box apparently didn't read the display EDID data from the Princeton VL-1916 display and assumed different Horizontal and Vertical sync.  I edited /etc/X11/xorg.conf to enter the correct values, added 1280x1024 to the screens and added the Keyboard option "ctrl:swapcaps" to put the control key where it belongs.  When X was restarted, 1280x1024 came right up, although loading the background was noticeably slower than more powerful systems.  Moving windows and bringing Gnome up results in noticeable refresh lag, and the CPU stays maxed at 100% for quite a while.

Net: Configuration with the Net tool to set for DHCP from my router was simple, and the system keeps up with my 3 Mb/s DSL connection just fine.  The update tool found only five packages to download, and a constant 354 MB/s download rate was maintained.

Audio: Worked out of the box, and sounds good.  Detailed analysis with headphones and Audacity remains to be done.

Data Movement: Plugging an external 250 GB USB2 drive in (formatted for jfs) and loading about 70 GB of flac files onto the internal drive went without a hitch and maintained a steady 30 MB/s rate (+/- 1) until I began doing other things.  Opening Firefox and then moving windows around caused momentary decreases in transfer rates, but it never was starved.  Backing up the OS to a Sony 4GB Flash drive also was fast until it needed to erase and reallocate space, then it slowed WAAAYYY down.

Other: I am a little disappointed that there is no CPU temperature readout, but lm_sensors appears to be out.  Still need to try hddtemp to see if it will report something.  In the meantime, a little touch every once in a while serves to monitor how the little box is doing.

mounting on the rear of an LCD display is easy with two thin strips of metal and two screws to match the threaded inserts that seem to be in the rear of many LCD displays for wall mount adapters.  This can also serve to get a little free airflow around the box to help cool it.

The bios is a very minimal Award bios that lacks many settings.  You cannot set NumLock to "off", and it defaults to "on"; You cannot apparently turn PXE boot "off" and it trys to boot that way greatly extending boot time; and there is no option in the Power screen to automatically boot up when power is applied.  The consequence of this last one is that you ALWAYS must press the power button to turn the Koolu on.

All in all, I am very pleased and can't wait for the Gutsy version of Fluxbox to come out and try that lightweight flavor.  While I like Gnome and KDE are too heavy for the little 500 MHz Geode processor, and XFCE has too much eyecandy for me.  IceWM will probably be the final choice if Fluxbox is delayed.

Now for a Compact Flash version of the Koolu as a server.......

---

### Post by ernia on 2007-09-20
I got a Koolu thin client yesterday and i'm using it with Debian.
You can disable pxe boot by pressing shift+f10 during the boot and changing settings in realtek bios, which starts after Award bios.
This page [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) reports geode cs5536 as supported with scx200_acb module since kernel 2.6.17.
We just need to know how to let him works :confused::confused:

---

### Post by mysticmatrix on 2007-09-21
About video stuff...
Have you tried proprietary AMD drivers for video found on Koolu's Wiki?

---

### Post by armandh on 2007-09-21
neet: like a totally tricked out nslu2

---

### Post by Hal58 on 2007-09-21
ernia: Thanks for the pointer to disable PXE boot.  That was totally non-intuitive.  On the sensors issue, I had loaded the appropriate module, plus all others that might be needed, and it seems to be broken in Feisty.  Hopefully Gutsy will have it fixed.

Just finished apt-get'ing hddtemp, and when configured with defaults, works just fine.  If you then install (or restart if already installed) gkrellm, you can configure Sensors -> Temperatures to display hda temp on the screen.  The max/min can be determined by installing smartmontools and displaying all parameters.

mysticmatrix: I have not installed the driver yet, but will probably try it out shortly.  I moved my koolu to the rear of a 15" 1024x768 LCD on a small bracket made from scrap aluminum sheet spaced about 1 cm from the display rear to give some room for convection cooling.

correction to my original post, the network d/l rate was in kB/s, not MB/s.  What's a few orders of magnitude anyway :/

---

### Post by dustinharriman on 2007-12-01
I also have a Koolu, and I'm running Ubuntu Gutsy Gibbon.  I was able to get better video performance when I enabled framebuffer support in x.org.  I have given some high-level instructions on my blog on how to do this:

[http://ca.blog.360.yahoo.com/blog-RkGSoVA1brWtXrVH9Gr5CzgVujwwGg--?cq=1](http://ca.blog.360.yahoo.com/blog-RkGSoVA1brWtXrVH9Gr5CzgVujwwGg--?cq=1)

These instructions may not be easy enough for a newbie, but if you have a few years experience with linux, and know how to hand-compile a kernel yourself, you should be OK.

BTW: if you want to run Ubuntu completely solid state on a Koolu (ie. run Ubuntu from a USB flash drive), then check this out:

[http://ca.blog.360.yahoo.com/blog-RkGSoVA1brWtXrVH9Gr5CzgVujwwGg--?cq=1&p=65](http://ca.blog.360.yahoo.com/blog-RkGSoVA1brWtXrVH9Gr5CzgVujwwGg--?cq=1&p=65)

---

### Post by dustinharriman on 2007-12-01
Actually, I have posted several times on my blog about my experiences with the running Ubuntu on a Koolu (over the last several months), which you might also find useful, you can see all those Koolu-related blog posts here:

[http://ca.blog.360.yahoo.com/blog-RkGSoVA1brWtXrVH9Gr5CzgVujwwGg--?cq=1&tag=koolu](http://ca.blog.360.yahoo.com/blog-RkGSoVA1brWtXrVH9Gr5CzgVujwwGg--?cq=1&tag=koolu)

---

### Post by bence8810 on 2007-12-12
Hi All,

I am in a hunt for a device like this, but I am unsure if Koolu will be my best candidate. If you dont mind, I would like to ask a few questions.

Am I able to get rid of Ubuntu, and install a base Debian without X on it? I would use it only for Exim, apache and proftpd.

I would like to make it as minimal as possible, and it would be a server rather than a workstation, with no monitor, etc.

Another question is would I be able to use the Thin client for this, booting from a Compact flash or a pendrive?

Thanks

Ben

---

### Post by simonn on 2007-12-20
> **bence8810 said:**
> 
Am I able to get rid of Ubuntu, and install a base Debian without X on it? I would use it only for Exim, apache and proftpd.


I got rid of the pre-installed Feisty and installed Gutsy server (i.e. no X) from a 1Gb USB stick. So, yes you can get rid of it.

See my post on the slim devices forum: [http://forums.slimdevices.com/showpost.php?p=246338&postcount=27](http://forums.slimdevices.com/showpost.php?p=246338&postcount=27)

> 
Another question is would I be able to use the Thin client for this, booting from a Compact flash or a pendrive?


A USB pendrive is definitely possible as it is how I installed Gutsy and compact flash should be possible. Remember that lots of disk writes kills flash RAM quickly. If you are worried about noise, the net appliance is for all intents and purposes silent with the 80gb drive.

---

### Post by bence8810 on 2007-12-20
Hi

I do have an 80GB HDD at home which I can use if worst come to worst, as buying the thin client for 100USD less brings me less custom taxes to pay for. Lower value, lower tax. 

Can I add the drive myself to the Thin client, eventually making it to a Net Appliance? The specs and info on koolu.com is not very fullfilling.

Are you satisfied with your unit in all aspects?

Thanks

Ben

---

### Post by simonn on 2007-12-20
> **bence8810 said:**
> 
I do have an 80GB HDD at home which I can use if worst come to worst, as buying the thin client for 100USD less brings me less custom taxes to pay for. Lower value, lower tax. Can I add the drive myself to the Thin client, eventually making it to a Net Appliance?


I think the Koolu FAQ says you can. 

> 
The specs and info on koolu.com is not very fullfilling. 


True, but I am 99.9999% certain that the net appliance is just a thin client with the added drive. By default it tries to net boot anyway.

> 
Are you satisfied with your unit in all aspects?


Yes. No problems whatsoever and it has been running 24/7 since I have had it (~4 weeks).

---

### Post by bence8810 on 2007-12-20
Hi

Thanks, I will look into it then further, as it may very well be what I am looking for.
Can you elaborate a little more on the CF and other flash based devices lifetime? It has a maximum amount of write sessions?

If I dont put a SWAP partition on it, then I guess the write to the disk will be minimal, and 512MB of RAM should be enough for a couple of services with no X.

Thanks

Ben

---

### Post by jcwhui on 2008-01-18
Hi, pardon me if I am not in the right forum. If not, let me know.

I am curious about using koolu (512MB, 80GB) as a front end. E.g does it play a DVD from a USB DVD-ROM smoothly?

Or how about playing video files from another network file server? Or like playing mounted DVD .iso files?

To play DVD/Video files, is it better to install WinXP on koolu, or Ubuntu?  I guess ubuntu, right?  But has anyone tried WinXP?

Anyone has experience or recommendation? Thanks!

---

### Post by simonn on 2008-01-20
I haven't tried playing movies on it as I am using it as a headless server.

I think the CPU would struggle, but if you get the proper video drivers then you may be ok(?):

See: 

[http://ca.blog.360.yahoo.com/blog-RkGSoVA1brWtXrVH9Gr5CzgVujwwGg--?cq=1&tag=koolu](http://ca.blog.360.yahoo.com/blog-RkGSoVA1brWtXrVH9Gr5CzgVujwwGg--?cq=1&tag=koolu)

---

### Post by jcwhui on 2008-01-21
Thanks!  I found this: [http://www.math.ucla.edu/~jimc/koolu/](http://www.math.ucla.edu/~jimc/koolu/)  He reported that WinXP can be installed but there is no audio driver.  So, I can't use it for media player then if I use XP (either way XP is such a monster).

Oh btw, anyone know if the USB ports of koolu has enough voltage to support a laptop DVD-ROM, i.e. an external DVD-ROM without external powe?.  So far, all google search shows that people use external powered DVD drives only.

---

### Post by barrybingham on 2008-03-19
I've been running the net appliance for a few weeks now. I think that Koolu must have taken note of dustinharriman's comments about HDD noise, as my unit appears completely silent: only the telltale orange light lets you know that the hard drive is doing anything.

I musy admit that I'm very impressed and I've found no need at all to use my tower system since the koolu arrived. Of course I spent a lot of time tweaking it (although I've stuck with Feisty) and with the AMD driver and IceWM+Rox instead of Gnome it's completely acceptable as a workaday system for just about everything other than 3D gaming (although mid-90s stuff via DOSBOX or Wine provides some nostalgic entertainment when not working)

I am wondering if and when Koolu will recommend a safe Gutsy upgrade. Not that I really feel any great need to upgrade now, but longer term I doubtless will, if only from a security point of view. From playing with livecds I think the X issues are general to all newer distros, as Fedora 8 (like Gutsy) produces a black screen with no apparent access to console. 

Still it's a great piece of kit. I can no longer tolerate the background noise of PCs now I've discovered silent computing!!

---

### Post by dennus on 2008-06-16
Hi guys!   I'm currently deciding on leaving my XP based home PC for a green-pc like the Koolu or ZONBU. I can't decide really. Most of my computer-time is spent on browsing the web. Occassionally I burn a DVD. So, do you think it is wise to switch to a thin-client like the ones mentioned?

---

### Post by hyper_ch on 2008-06-17
Hmmm, I have to check what Koolu exactely is :)

---

### Post by barrybingham on 2008-06-17
> **dennus said:**
> Hi guys!   I'm currently deciding on leaving my XP based home PC for a green-pc like the Koolu or ZONBU. I can't decide really. Most of my computer-time is spent on browsing the web. Occassionally I burn a DVD. So, do you think it is wise to switch to a thin-client like the ones mentioned?

Well, I use the Koolu for everything. I run an external usb burner for DVDs, OpenOffice for all the MSOffice stuff my employer uses, and a combination of DosBox, Dosemu, Crossover, vanilla Wine and VirtualBox enables me to even play some older games. No3D acceleration, of course! The only flies in the ointment are the upgrade query I referred to in my post on this thread and the jerky video on the flash videos now used by the BBC and others: for updating, I think that the next point release of Hardy may install on the Koolu without problems. That said Feisty does everything I want, with a little tweaking. I even run XP through VirtualBox (just for the hell of it and to play some AoEmpires & SimCity 3000 without glitches).  So the answer is that the Koolu will do almost everything except modern gaming, but you will need to spend some time tweaking it to get decent performance (ditching Gnome in favour of Icewm, installing AMD video driver, changing video memory in BIOS)

---

### Post by alexeix on 2008-07-20
I'm thinking of buying a Koolu to use as a client for MythTV - would I be better off with the Net Appliance or the Thin Client?

Also, how does it handle connection to an HD TV?

Any experiences that people would like to share in this area?

Thanks.

---

### Post by Beowulf878 on 2008-12-11
I have had my Koolu for about 6 months now. I use it on a 22 inch screen at 1650 x 1050 resolution, as long as at least 32mb is assigned to the graphics there is no problem (I usually have it at 128mb though).

I have tried lots of different distributions on it, and lots of OSs, so far all that easily works for me is Ubuntu (I have 8.04 on mine). For most of the others you have to compile the graphics driver.

It is surprisingly usable with the default ubuntu installation, with Xfce its quite snappy and with fluxbox its very comfortable. The only thing I would say is this - firefox 3 is noticeably slower than practically any other browser, and webpages such as facebook seem to need more cpu time than everything else put together - its really very slow since its been updated. BBC iplayer also isn't brilliant for me - the low-quality programmes are watchable though. Galeon is currently my browser of choice.

In terms of the USB, basically anything bigger than a usb-flashdrive / receiver for a wireless keyboard or mouse requires an external powersource: since wifi isn't built in, this may mean you need one all the time.

The audio is ok, but even with external speakers the quality isn't really good enough for music on my model.

In terms of sound it is actually very very close to silent. Even in the countryside at my parents (since its so small, it goes with me) you can't tell if its on or not as long as you tune the hard-drive. When it came, I had been prepared to replace the HD with an actually silent one, however at the time this was the best on the market for silence. When it powers down, however, it clunks: I disabled mine using hdparm and since then its been very quiet. Also of note is that even in the summer, it didn't get above 48 degrees Celsius (there is a sensor on the HD) when I had disabled powering down, and now its winter here in England it is usually about 25-30. As long as you don't bury the unit it only  feels warm to the touch.


All in all I was surprised how much it could actually do - I bought it just for a 24/7 IRC box and had intended to use it without x, but in the end I found myself using it as a complete pc. Most powerpoints and word documents open well in it, although if you have a 100mb+ .ppt (and I do) it did open it, but only after swapping everything in the RAM - this took a while.  

Hope this is of some use to prospective buyers! Personally I cannot wait until there is a low-power gpu to go with the intel atom, I will build myself a 2nd silent pc hopefully no bigger than the koolu. I suppose it has really changed my ideas about what a pc should be - all of mine will be silent from now on. ;)

---

### Post by dennus on 2008-12-12
I went to Koolu's website. Looks as if they no longer sell the Koolu PC.

---

### Post by barrybingham on 2008-12-12
> **dennus said:**
> I went to Koolu's website. Looks as if they no longer sell the Koolu PC.

That's right. It was quietly dropped some time back and the company seems totally focused on OpenMoko and GoogleApps...  But they never actually made the thing: rather they seem to have optimsed and installed Ubuntu on a Taiwanese mini-PC, the FIC ION A603 "thin client".

If you are really keen, it looks like this is still on sale in some markets:
[http://www.fic.com.tw/product/minipc.aspx](http://www.fic.com.tw/product/minipc.aspx)

No OS, but you just need to stick Intrepid on it and you'll find that everything works "out of the box". Unlike the original Feisty install from Koolu, which needed lots of tweaking to make it truly usable as a general purpose PC. The last of the Koolu boxes were visually identical to the one shown on the FIC website, apart from the fact that they had "Koolu" stickers on the front......

---

### Post by dennus on 2008-12-12
I went to the website. Have a little trouble finding a local supplier. Do you know of any other alternatives to the Koolu PC?

---

### Post by barrybingham on 2008-12-13
> **dennus said:**
> I went to the website. Have a little trouble finding a local supplier. Do you know of any other alternatives to the Koolu PC?

Well, there's the (somewhat pricy) Linutop, from France. Flash only, intended originally for kiosks, there's now a Linutop 2 which I think could be used as a general purpose PC. The website was down just but it's:

[www.linutop.com](www.linutop.com)

It's sad really, but this sort of thing seems not to have caught on enough to be viable for the companies. Everybody is into netbooks and laptops now. This time last year, Linutop was slogging it out with the Koolu and the Zonbu. Now its the only one left (Zonbu - in the US - has stopped selling hardware and now just seems to do software)

Of course there may be other silent mini-PCs out there like the FIC, but without the visibility of Koolu, Zonbu or Linutop (which were really about showing what could be done with particular software on a very small power footprint). And if so probably cheaper...  a search on ebay reveals several cheap and interesting silent, fanless and barebones boxes. Of course as ever there's no sense as to quality or even manufacturer so it would be a case of "buyer beware". The Koolu, Zonbu and Linutop all attracted enough attention to be tested and reviewed.

I wouldn't swap my FIC/Koolu for anything now. Like Beowulf878 I find silent computing something I cannot face losing...

---

### Post by Beowulf878 on 2008-12-17
fit-pc is an option - very similar spec. [same cpu, ram etc]

For myself, I am going to wait until there is a low-powered (i.e. 10W or less) atom-based system, or an improved VIA ULP chipset ( I think they have a 600mhz board similar to the koolu's). What I would say is be careful of the resolutions of these - a lot of them only do 1280x1024 - this is why I chose an AMD-Geode based system. I really do feel that for web 2.0 at least 1 ghz is needed, maybe more now - although I am not convinced its better than websites from 5 years ago: not my choice though...

---

### Post by armandh on 2008-12-17
dell mini9 is limited by the svesa out 
perhaps the next gen will be hdmi

---

