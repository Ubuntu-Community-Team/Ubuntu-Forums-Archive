---
title: "Laptop recommendations for Ubuntu?"
date: 2004-12-16
forum: The Cafe
---

### Post by AlexV on 2004-12-16
I'm planning on buying a laptop to take to College next year. I've been looking at a few different brands, but right now I'm leaning toward an IBM ThinkPad G40. IBM claims that it is compatible with Red Hat 9 and Suse 9.1, so I assume that I won't have to many problems installing Ubuntu.

But before I make a decision: What laptop(s) do you recommend for Ubuntu?

---

### Post by Jspired on 2004-12-16
I've installed on two different Toshiba laptops with great success.

---

### Post by Dan on 2004-12-17
Why not go for a T22, cheap as chips and will do everything you want to do.

---

### Post by skipsjh on 2004-12-18
What kind of things are you looking to do with this laptop?

Are you going to dual-boot for gaming, just us it for notetaking and wordprocessing, or is it more a general purpose machine because you won't have a desktop?

Gaming: R40 or similar with 15" screen and nice videocard

Notetaking, etc: Thinkpad T42 or X-series

General Use: T42

I'm using all Thinkpads as an example because it's your best bet to get ACPI or APM working for the suspend function and full power management.  IBM tests their machines with Linux, and actually does quite a bit of Linux development for their products.  It's probably one of the only big computer companies out there that will field a support call about Linux on your laptop.

Personally, I have an Inspiron 600m that I got before I started using Linux.  Because Dell has a broken ACPI/APM bios, it doesn't have full power management.  Everything else works fine though.

~Scott

---

### Post by Dan on 2004-12-18
I used a 600X for 3 Years until it finally packed up, I still use a T22. Why pay good bucks for a mega fast cpu and big HD when you don't need it? Nearly all IBM machines work well under any distro and if you only want a study machine you won't get a better deal than a second hand lappy, You're not going to run M$ bloatware on it.

---

### Post by skipsjh on 2004-12-19
[QUOTE=Dan]I used a 600X for 3 Years until it finally packed up, I still use a T22. Why pay good bucks for a mega fast cpu and big HD when you don't need it? Nearly all IBM machines work well under any distro and if you only want a study machine you won't get a better deal than a second hand lappy, You're not going to run M$ bloatware on it.[/QUOTE]

He still hasn't said what he's using the computer for.  I agree that for a study computer, then a T22 or T30 will be perfect.  What if he's into gaming or something else that is more intensive than a P3m or P4m with a crappy video card can handle?

~Scott

---

### Post by varunus on 2004-12-20
I've successfully installed Slackware, Debian, and Ubuntu on a Toshiba Satellite A45-S150.   It was pretty good for the price ($1100 for 2.4GHz P4-m, 60 GB HD, 512 MB RAM, 32 MB Intel Video Card (not shared VRAM), a CD-RW/DVDROM drive, and wi-fi).  I've gotten everything to work under Ubuntu...most things just worked.

This model, I believe, is no longer available, but there is a model with almost the same specs available for a similar price...I think they upped the HD, the RAM, and the processor.

If you aren't into too much gaming with your laptop, then go for this model.  I've had great success with linux.

---

### Post by wulf on 2004-12-20
I've got it installed on a Packard Bell EasyNote M5262. It's working pretty smoothly although I haven't tested everything (for example, I haven't tried writing a CD with the build in CDRW/DVD drive).

The two things I've not yet been able to sort out are:

1) The built in card reader (I was hoping it would automagically work but no such luck)

2) Connecting up an external monitor (although I also didn't get the particular monitor I had in mind to work under WinXP - a different monitor worked fine in the past)

I also occasionally have to restart X after boot up - instead of loading GDM it presents me with a blank screen, fixable with Ctrl-Alt-Backspace.

Therefore, while it's not been perfect it's worked pretty well.

Wulf

---

### Post by soritong on 2004-12-24
[QUOTE=AlexV]I'm planning on buying a laptop to take to College next year. I've been looking at a few different brands, but right now I'm leaning toward an IBM ThinkPad G40. IBM claims that it is compatible with Red Hat 9 and Suse 9.1, so I assume that I won't have to many problems installing Ubuntu.

But before I make a decision: What laptop(s) do you recommend for Ubuntu?[/QUOTE]
 Surprisingly, for a cheap deal, my Dell Inspiron 1000 runs Ubuntu great, apart from all the other distro's I've have problems with the X server and getting the display to actually display.

---

### Post by Krash1201 on 2004-12-25
running dual booted with windows xp pro on a dell inspiron 8600.  install went great, adapted to the laptop no problem.  the big drawback, it won't recognize my mpci internal wireless card, so i got no internet.  i can't get ndiswrapper to work, so that is the only big problem i have had.  works great with kernel 2.6.8.1-3-686, but be warned, wifi=major headache.

---

### Post by mistic on 2004-12-25
I'm using an Apple iBook G4 for my study-work, Ubuntu runs great on it, the hardware-support is realy phenomenal ( Firewire-HD-worked out of the box and stuff)

I tell you, if you need a laptop that's easy to take along where-ever you go, there's nothing like these nice 12" babies, its so handy, you can almost put it in your backpocket and yet it is more then big enough...

Plus as long as your a student you get a discount from apple on all their stuff (hard- and software...) 

I know its a weird choice, but for me and some friends of mine, the 12" iBook G4 turned out to be the ideal laptop, mostly because of his compactness and easy handling...

grtz
Mistic

---

### Post by ChamPro on 2005-01-24
I just got a Dell Inspiron 8600 myself, and using Warty with the built-in mpci Intel 2200 B/G works fine. The IPW2200 drivers are included in Warty. However, I tried to upgrade the current Hoary and DNS for both wired and wireless went crazy.

So if you stick with stable you're fine.

I was going to get a Apple Powerbook, but the Dell was a present. Can't look a gift horse in the mouth.

---

### Post by ctt1wbw on 2005-01-24
[QUOTE=ChamPro]I just got a Dell Inspiron 8600 myself, and using Warty with the built-in mpci Intel 2200 B/G works fine. The IPW2200 drivers are included in Warty. However, I tried to upgrade the current Hoary and DNS for both wired and wireless went crazy.

So if you stick with stable you're fine.

I was going to get a Apple Powerbook, but the Dell was a present. Can't look a gift horse in the mouth.[/QUOTE]


I, too have an Inspiron 8600.  I was so impressed that Ubuntu installed the Intel Pro Wireless drivers correctly.  I had Mandrake and gave up with trying to get it to work.  I wanted a Powerbook and couldn't get one financed and I needed a new laptop like yesterday.  Dell gave me 1500 bucks in under 5 seconds.  So hello 15.4" Inspiron 8600.  Not a bad machine as long as Windows doesn't boot up.

---

### Post by mendicant on 2005-01-24
I've got it installed on an IBM T42.  Everything seems to work, although I've never tried to get the fingerprint reader working.  It has an ATI card, unfortunately, and their proprietary drivers have poor performance.  If you care about 3D stuff (whether for work or entertainment), you'll probably want to make sure you've got an NVidia card in there.  For non-3D work, it's a very nice little laptop.

---

### Post by ctt1wbw on 2005-01-24
[QUOTE=Krash1201]running dual booted with windows xp pro on a dell inspiron 8600.  install went great, adapted to the laptop no problem.  the big drawback, it won't recognize my mpci internal wireless card, so i got no internet.  i can't get ndiswrapper to work, so that is the only big problem i have had.  works great with kernel 2.6.8.1-3-686, but be warned, wifi=major headache.[/QUOTE]


I have the same laptop and installed the kernel based on the i386 and the wireless is perfect.  What gives with that kernel?

---

### Post by Viro on 2005-01-24
I'm using a Powerbook G4 12". It runs nicely and I like the small form factor. The only things that don't work are wireless, 3D acceleration, sleep/suspend and the internal modem. Everything else like bluetooth, ethernet, sound, etc works straight out of the box. Which is cool.

Now if everything worked, I'll be sorted.

---

### Post by Buffalo Soldier on 2005-01-25
Anyone in Malaysia looking for 2nd hand laptop. Here's a good site:

[http://bidnow.com.my/cart/index.php?cPath=21](http://bidnow.com.my/cart/index.php?cPath=21)

---

### Post by jerome bettis on 2005-01-25
[http://www.laclinux.com/en/Laptop](http://www.laclinux.com/en/Laptop)

i can say with pretty good confidence that my laptop works better than everyone's on this forum.  that's right i said it.

good warranty too.  i spilled water on my keyboard and they fixed it no questions asked, i just had to pay shipping both ways.

i'm so glad i didn't buy a dell, ibm etc and have to deal with headaches getting things setup, only then to still have acpi broken or wireless not working etc etc etc.

---

### Post by Pluk on 2005-01-25
IBM T42 works 99,9% with linux. The ati-driver (fglrx) crashes the laptop if i put it to sleep, but i dont game so i dumped the ati driver.

---

### Post by mirtux on 2005-02-01
Hi,
    you can also have a look at this thread ---> [http://www.ubuntuforums.org/showthread.php?t=13526]("http://www.ubuntuforums.org/showthread.php?t=13526"). Other happy Ubuntu users!
  
  Regards,
  MC

---

### Post by llanitedave on 2005-09-21
I just bought the latest G4 iBook and set it up to dual boot on OS X 10.4 AND Ubuntu linux.

The trackpad doesn't work on linux (new driver for this model, apparently) and Mac's vaunted "Internet Ready" networking can't pick up my internet connection. (Ubuntu on the same machine had no trouble at all.) In addition, Apple has removed Appleworks in favor of the less capable -- and must purchase -- iWork.  I'll be returning it to the store this weekend. 

My question is this:  What is the best model laptop in the $1000 range for running with Linux?  If it's not an Apple, there's no need to dual boot.

I'm leaning towards an HP Pavilion.  Any suggestions?

---

### Post by Hobbsee on 2005-09-21
[QUOTE=llanitedave]I just bought the latest G4 iBook and set it up to dual boot on OS X 10.4 AND Ubuntu linux.

The trackpad doesn't work on linux (new driver for this model, apparently) and Mac's vaunted "Internet Ready" networking can't pick up my internet connection. (Ubuntu on the same machine had no trouble at all.) In addition, Apple has removed Appleworks in favor of the less capable -- and must purchase -- iWork.  I'll be returning it to the store this weekend. 

My question is this:  What is the best model laptop in the $1000 range for running with Linux?  If it's not an Apple, there's no need to dual boot.

I'm leaning towards an HP Pavilion.  Any suggestions?[/QUOTE]
 [http://ubuntuforums.org/showthread.php?t=52814](http://ubuntuforums.org/showthread.php?t=52814) might be something you want to check out for good laptops to put ubuntu on...

Not sure in the under $1000 range, seeing as I dont work in US dollars...

---

### Post by maxxx on 2005-09-26
I've been struggling with a Thinkpad 600E and SuSE (8.1, 8.2) over the past 3 years. It was old when I got it, and now the battery is dead. I never got the soundcard working and the lack of a backlit screen really limited where I could use it.

I'm looking to buy a new laptop, top limit £600. Nothing fancy, I'll only be running apache, mysql, php, perl, etc. and would like a couple of USB ports, a CD-writer (maybe a CD/DVD combo). Can anyone recommend a laptop, website or point me in the right direction?

I want to just be able to put my Ubuntu CD in, get it installed and have everything working.

---

### Post by Zelut on 2005-09-26
Well I've been using an emachines notebook for the past year (6 months with Ubuntu) and everything works.  Wireless networking doesn't work "out-of-the-box", but it is supported.  I do like the machine and it seems to fit your requirements however I will say the customer support with emachines is crap.  

I have installed Ubuntu on a number of notebooks and everything has worked great by default.  There aren't any machines (yet) that I would say NOT to buy.

---

### Post by datamichael on 2006-04-12
If I wanted to purchase a new laptop just to run Ubuntu or kubuntu, what would be the best brand/model?

And when I say "best", I mean best supported, quickest, easiest configuration, wireless and trackpad that are fully supported, etc.

Thanks!
Michael

---

### Post by aysiu on 2006-04-12
[http://www.system76.com](http://www.system76.com)

---

### Post by mips on 2006-04-12
[QUOTE=datamichael]If I wanted to purchase a new laptop just to run Ubuntu or kubuntu, what would be the best brand/model?

And when I say "best", I mean best supported, quickest, easiest configuration, wireless and trackpad that are fully supported, etc.

Thanks!
Michael[/QUOTE]

I would look beyond that and go for and IBM Thinkpad, with a few tweaks everything should work fine and you'll have one of the best laptops out there...

---

### Post by aysiu on 2006-04-12
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptops](https://wiki.ubuntu.com/HardwareSupportMachinesLaptops)

---

### Post by datamichael on 2006-04-12
[QUOTE=aysiu][https://wiki.ubuntu.com/HardwareSupportMachinesLaptops](https://wiki.ubuntu.com/HardwareSupportMachinesLaptops)[/QUOTE]

Thanks! That's what I was looking for. Looks like HPs are the most supported out of the box. That kind of surprises me since my Compaq R3000 isn't.

Anyway, I'll be taking a knoppix CD down to best buy to confirm.

Thanks!

---

### Post by FlakJacket on 2006-04-12
My HP Pavilion ze5300 isn't on that list but it pretty much worked out of the box.  It's a couple of years old though.

Flak

---

### Post by RedGhost on 2006-09-20
Hey, I am looking to purchase a laptop in the $700-$1200 range. I want it to include a 64bit processor, atleast a gig of ram, and decent video. I have scoped out a few that interest me and they are:

-Compaq Presario AMD Turion 64 X2 TL-52 1.6GHz Laptop (V3030)
-Acer Aspire AMD Turion 64 X2 Dual Core TL-50 1.6GHz Media Center Laptop (AS5102WLMi)
-Gateway AMD Turion 64 X2 Dual Core TL-50 T2050 1.6GHz Media Center Laptop (MX3414)

Now I have researched these three a bit and the latter two seem to present a range of problems with Linux and I couldn't really find any info on the former. If you have experience with any of these with Ubuntu, or have a suggestion for a nice compatible laptop within my specifications please let me know.

---

### Post by xyz on 2006-09-20
I can suggest a few links:
_Linux on Laptops_
[http://linux-laptop.net/](http://linux-laptop.net/)
_HardwareSupportMachinesLaptops_
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptops](https://wiki.ubuntu.com/HardwareSupportMachinesLaptops)
_System76 - Ubuntu Pre-Installed Laptops, Desktops, and Servers_
[http://digg.com/linux_unix/System76_Ubuntu_Pre_Installed_Laptops_Desktops_and_Servers](http://digg.com/linux_unix/System76_Ubuntu_Pre_Installed_Laptops_Desktops_and_Servers)

My own experience is with a Toshiba Satellite A 40 bought 2 years ago and I have had no major problems with Ubuntu, Mandriva, Debian.
Note that this laptop came with XP Home pre-installed and the reason I bought it was because it was on sale! Incredible price!

So I didn't buy it *because* of planning on installing GNU/Linux OS. And it works fine for me - fingers crossed!

I realize my following suggestion is rarely possible (except if you're thinking of purchasing second hand) but using the Live CD is a good way to check for compatibility.

Pre-installed Ubuntu laptops are also much cheaper (obviously!) and I'm pretty sure you could repartition the HD to make room for Windows if you need it!

---

### Post by bluefuse on 2006-09-20
IBM with a cisco wireless card, they use all intel, a t40-t42.....zero configuration...wifi works out of the box

---

### Post by RedGhost on 2006-09-20
> **xyz said:**
> 
Pre-installed Ubuntu laptops are also much cheaper (obviously!) and I'm pretty sure you could repartition the HD to make room for Windows if you need it!

Hey, I checked about 30 Linux/notebook sites on the web including System76. None of them even came close to the cheap prices at Futureshop or other local stores. For $899 I am getting more then some of these sites even offer (and their < $1000 packages are quite bad) and without paying for shipping or overhead.

Thanks I checked out those reviews and sites, I made my choice, now I just pray :-({|=

---

### Post by xyz on 2006-09-21
> **RedGhost said:**
> Hey, I checked about 30 Linux/notebook sites on the web including System76. None of them even came close to the cheap prices at Futureshop or other local stores. For $899 I am getting more then some of these sites even offer (and their < $1000 packages are quite bad) and without paying for shipping or overhead.

Thanks I checked out those reviews and sites, I made my choice, now I just pray :-({|=

I'm sure glad you found shoes to fit your needs! I don't think you'll need to pray that much but it would be nice of you to come back here and tell us how it went once you have Ubuntu installed.

I don't know Futureshop! Is it in the States?
Around where I live pre-installed Ubuntu boxes can be found at a cheaper price but it requires some travelling.

Happy Ubuntu on a laptop to you!  :D

---

### Post by floring on 2006-09-23
Hi,

Got myself a nice Compaq V3030CA from Futureshop and installed Ubuntu 64Bit dapper. Works really well. The only issue I had so far is the Broadcom driver (WIFI); It doesn't seem to work with or without ndiswrapper. HAL doesn't see the device properly so even if drivers are properly installed, the device is not seen at all. Otherwise, I am running vmware and WinXPPro both standalone and virtual (vmware) and the box is a real work horse... 

I make the mention that I tried the V3020 and it did not work at all ...stale big time. I think because of the processor TL-50 and cache 256. I tried a duo core T2400 Asus (Intel) on 32 bit and returned it, it did not even come close in Linux to the Compaq V3030CA TL-52 64 bit AMD.

Still digging for WIFI ... but in general I really love this machine. Great value for the $$.

cheers

---

### Post by Duo Maxwell on 2006-09-23
You looked at [http://powernotebooks.com/](http://powernotebooks.com/) ? I've been looking at replacing my aging 600Mhz G3 iBook Snow with the Crown P 15:2 ULTRA maxed out with the 3 year accidental damage  warranty  looks like between $1948.73-2009.00 USD. Comes OSless so there's no M$ tax. The only AMD based tops I see there are some real high end Sagers.

You checked newegg? these are all the Turion X2/Nvidia powered tops they have [http://www.newegg.com/Product/ProductCompare.asp?SrchInDesc=amd&Category=26&N=2030260032&Submit=ENE&Nty=1&Subcategory=32&CompareItemList=N82E16834147275%2CN82E16834149046%2CN82E16834147172%2CN82E16834147198%2CN82E16834147197](http://www.newegg.com/Product/ProductCompare.asp?SrchInDesc=amd&Category=26&N=2030260032&Submit=ENE&Nty=1&Subcategory=32&CompareItemList=N82E16834147275%2CN82E16834149046%2CN82E16834147172%2CN82E16834147198%2CN82E16834147197) Mostly HP/Compaq stuff.

I don't trust ati for anything let alone linux after having to deal with sevral desktops and a few laptops with ati motherboard chipsets and GPUs.

Stick with nvidia or intel's GMA950 or GMA3000 and GMAx3000 based chipsets and you should be alright.

---

### Post by tj03 on 2006-09-24
I have the v3030 as well and have been unable to get the wifi working either..  That and sound, which is kinda a sticking point.  

Have you been able to get sound working??

---

### Post by xyz on 2006-09-24
[Wireless Networking]("http://bengross.com/wireless.html")
by Ben Gross

---

### Post by tj03 on 2006-09-24
Well after wasting two days on the v3030 I returned it to futureshop.. Networking was useless -- couldn't get the wifi or ethernet connection to work, sound wouldn't work at all.  I finnaly gave up after almost hitting it with a hammer.

Ended up building a desktop instead

Athalon 64 4600+ x2
MSI K8NGM2 Motherboard with Nvidia GeForce 6150 + Nforce 430
320gig SATA HDD
2 gig's dual channel ddr400mhz ram
micro case
Hauppauge pvr350
17" LCD

Was able to get the sound and networking going in a matter of minutes, the ironic thing is -- it's the same dam chipset yet neither would work on it..

As a side note I tried to reinstall the original software on the laptop when I returned it -- surprise surprise the windows install is faulty and doesn't work.. I ended up returning it with a formatted HD.

---

### Post by UnknownVariable on 2006-10-02
Well it's pretty easy to say I'm a bit frustrated with getting Ubuntu to work correctly on my laptop. I just happen to have the lucky model of laptop which has a horrible video card and a horrible wireless card, both of which it seems 90% of people who own one **can not** get them working correctly with Ubuntu. I got the video card working for the correct resolution display, but after countless attempts at getting my wireless card running with the only way to revert changes as a reinstall (as far as I can see -- Broadcom Airforce One 54g, do a search on these forums and you'll see the mess) I've decided I should just go out and buy a new laptop. I need a new one for school anyhow.

Do you guys have any recommendations or any suggestions on things to look out for to make sure my hardware is supported by Ubuntu? What seems to be the easiest brand of video card / wireless card to get started?

Thanks. :)

---

### Post by Zyzzyx on 2006-10-02
Check out [System76]("http://www.system76.com"). All Ubuntu systems, and they're active here on the forums too.

---

### Post by handy on 2006-10-02
If I were buying, nVidia GPU would be essential.

---

### Post by boogyman on 2006-10-02
Can't you use ATi GPU's on ubuntu?

---

### Post by handy on 2006-10-02
> **boogyman said:**
> Can't you use ATi GPU's on ubuntu?

Most user's find them troublesome.  

ATI's linux support is way behind nVidia's.

---

### Post by gn2 on 2006-10-02
I would suggest trying other Linux distros before buying a new laptop.......

Potentially massive savings....

Or just get a known working PCMCIA or USB wireless adapter?

---

### Post by UnknownVariable on 2006-10-02
> **gn2 said:**
> I would suggest trying other Linux distros before buying a new laptop.......

Potentially massive savings....

Or just get a known working PCMCIA or USB wireless adapter?

Ubuntu seems to be the "easiest" linux distro out there, and believe me, I'm having a bit more than difficult time getting everything to work on my current box. I need a new laptop as it is anyhow, because I'm going to a national web design competition in June and my partner needs a box to work on. ;) 

Money's not really an issue, I'm one of those nerdy guys that saves his money instead of getting a girlfriend to spend it all on :lol:

I do have a separate external USB wireless card though... I know it needs a few drivers to be installed to work on Windows, so I'd probably have to extract the firmware like in that tutorial... Unless it'll work automatically? Who knows, I'll give it a try later when I'm out of class. :o

---

### Post by lalji on 2006-10-02
I just bought a new laptop and have a dual boot setup with XP and Ubuntu. I'm new to Ubuntu so you might want to factor that in to my recommendation, but I have had pretty good success with getting the basics (wireless, graphics etc) working on my laptop.

It's a Powerpro L8:14, which has an nvidia 7600 and pretty good specs (Core Duo, 1 GB ram, 14" widescreen). Powernotebooks ([www.powernotebooks.com](www.powernotebooks.com)) makes them based on a barebones from Compal. Their service is great and they won't make you buy an MS stuff you don't want. You might like what they have - and it has worked pretty well with ubuntu for me.

---

### Post by UnknownVariable on 2006-10-02
Sounds good, thanks, I'll look into them. :D

---

### Post by petri on 2006-10-02
These two links might help your decision

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptops](https://wiki.ubuntu.com/HardwareSupportMachinesLaptops)

[https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

---

### Post by gn2 on 2006-10-02
> **UnknownVariable said:**
> Ubuntu seems to be the "easiest" linux distro  :o

You obviously haven't tried PCLinuxOS yet...

---

### Post by aysiu on 2006-10-02
... or Mepis...

---

### Post by UnknownVariable on 2006-10-02
Lol, true, I haven't tried either of those distros yet. Then again, there's so many of them and lots of them aren't popular by word-of-mouth yet, so it's hard to get in-the-know about them all. I'll probably take a look at some other distros later, but I'll stick with Ubuntu for now. It's one of the fastest growing binary distros available from what I've seen, and this is some good stuff here. :o

---

### Post by aysiu on 2006-10-02
While I do believe Ubuntu is the "best" distro (for me, that is), I do not think it is technically superior to other distros or that it is the *easiest* for ex-Windows users (who--face it--are most of the new Ubuntu users out there).

I use Ubuntu for its initial simplicity (one app per task), the implementation of *sudo* by default, and the wonderful support community and documentation.

Mepis has several things that'll make the transition easier for ex-Windows users:

1. With a single click, automounting (with correct permissions) of Windows partitions. No editing of the /etc/fstab file necessary

2. Flash, Adobe Reader, Nvidia drivers... a slew of popular proprietary software and codecs.

3. Point-and-click Grub reinstallation

4. New, old, and older kernels at boot time for different hardware scenarios.

5. Lack of choice--x86 only, KDE only. This isn't ideal *eventually*, since Linux is all about choice, but that's great for a first distro, since many new Windows users get overwhelmed by choice.

Of course, I do believe that if Mepis is an excellent first distro, Ubuntu is definitely an excellent second distro. It's been my second distro, and I've stuck with it for 1.5 years already.

---

### Post by gn2 on 2006-10-02
Reasons I like PCLinuxOS:

1: GUI Control Centre sets _everything_ up very easily.

2: Synaptic installs Nvidia driver.

3: Only needed to install libdvdcss2 via Synaptic to get full multimedia  support.

4: Easy configuring of access to Windows partitions via GUI.

5: Draklive installer offers direct install to USB drive option.

6: Grub location selectable at install.

Generally "feels" more up to date than Ubuntu, but that's just my personal opinion, not a statement of technical fact....

---

### Post by UnknownVariable on 2006-10-02
I see. :o

Well, my only response to that is that I'm switching linux *because* of the choices. I'm a web developer, so I know my way around computers (for the most part) but getting into Linux is like learning a new language. It's tough at first, but as you get more and more into it, it's second nature. I don't mind getting dirty with technical stuff once in a while -- afterall, I live for computers, you could say. Sometimes we just go for a challenge due to the sheer fun of it. I'd rather learn my way around Linux with rough times than have a super simple windows-clone where I learn nothing new. :)

---

### Post by aysiu on 2006-10-02
I like PCLinuxOS because DiskDrake is the most reliable disk partitioning tool I've used.

---

### Post by CujoQuarrel on 2006-10-03
Using a dual boot on my Dell Inspirion 6000 with no major problems to date. 

Mostly used for music and web surfing.

---

### Post by yogamatt1970 on 2006-10-11
OK, I'm sitting here using my wife's Dell Inspiron on Windows, watching Symantec Antivirus hog up 80% of the CPU while I'm doing nothing and well, I am totally sick of Windows!
And I'm looking to buy a new laptop.
I know this sort of question has been posted before but I keep getting lost in the various discussions I've found.
Does anyone have a recommendation for the best laptop to use to run Ubuntu? 
Ideally, I'd like something that will just work with minimal fuss.  I've been seriously considering a thinkpad T43 or T60 because I've used thinkpads in the past and I love them.  Also, I have run Linux before on desktop machines (Fedora Core and CentOs) so I'm not a complete Linux newbie.  The problem is, it just seems like there's no perfect laptop for Linux (not just Ubuntu, but Debian, SUSE, Gentoo etc.).  Between all the problems people seem to have with wireless, suspend, the Access IBM button on thinkpads, video cards (ATI's seem horrible and that's what all thinkpads ship with), I'm feeling like maybe I should just buy a macbook pro.
But then I feel like the mbp's are overpriced and I dislike the idea of giving Apple my money.  IMO, they would be just as evil as Microsoft is if they had the chance.
Any help is appreciated.

---

### Post by Buffalo Soldier on 2006-10-11
[http://system76.com/](http://system76.com/)

They even have a support section in here. [http://ubuntuforums.org/forumdisplay.php?f=158](http://ubuntuforums.org/forumdisplay.php?f=158)

---

### Post by hw-tph on 2006-10-11
Get an Apple MacBook or MacBook Pro. Works great, looks good, and you can dual boot OSX and Ubuntu (or - God forbid - triple boot with Windows!).


Håkan

---

### Post by kondor on 2006-10-11
I have not bought one of these, nor do I work for them. But, I found this site last week and they ship with Ubuntu installed and configured.

[http://groovix.com/store/index.php?main_page=index&cPath=2&zenid=f9e65a9cd50125fbd9c0d9ad130ebe0b]("http://groovix.com/store/index.php?main_page=index&cPath=2&zenid=f9e65a9cd50125fbd9c0d9ad130ebe0b")

I run 6.06.1 on a Toshiba Satellite A65

---

### Post by arkangel on 2006-10-11
dell and IBM lenovo usually  work very well  too

---

### Post by ZERO_SHIFT on 2006-10-11
I was planning on buying a macbook, but I found that it is not easy to get ubuntu running smoothly on it. Hence I am going to get a HP dv2000.

I think your best choice would be system 76.

IBM's are also very supportive to ubuntu/linux as well as DELL and HP.

---

### Post by mdwuznik on 2006-10-11
Me and quite a few of my colleagues use AsusW5A or Asus Vseries. Works great with ubuntu, with the only piece missing being the integrated webcam.

Cheers
Michal

---

### Post by yogamatt1970 on 2006-10-11
Thanks for info everybody.  Although I trust the quality of Lenovo/IBM, I don't feel like dealing with the video driver problems.  I hadn't heard of system76 before, I'm seriously considering buying a serval.  To be honest though, it almost sounds to good to be true.  I googled around and it seems like they have a decent enough reputation (although no one can tell how long they're going to last).  I do not mind paying their prices if they can support the hardware to run Linux.  I'd much rather support them than Apple or Lenovo (btw, Lenovo's pre-installed SUSE notebooks start at over 3K!).

Since I do need to do some remote work on Windows boxes, I'm going to give rdesktop a try when I get Linux running on my laptop.  If that doesn't work, I'll just host Windows with VMWare or make my Linux laptop dual bootable. 

Anyone here have any experience with system76?  How about rdesktop?

---

### Post by Bagnaj97 on 2006-10-11
I bought a Lenovo 3000 C100 the other day and everything's been supported out of the box apart from the broadcom wireless (which works fine with ndiswrapper) and the built in card reader. If you get a centrino laptop everything should work because intel hardware is generally well supported.

---

### Post by John.Michael.Kane on 2006-10-11
Acer and Averatec have worked for me with 5.04-dapper.

IBM/Dell/System76/Fujitsu/Asus/Hp/Compaq.

---

### Post by hw-tph on 2006-10-11
> **Bagnaj97 said:**
> (...)apart from the broadcom wireless (which works fine with ndiswrapper)

It works flawlessly with the bcm43xx driver that comes with Dapper. You just have to set it up (put the firmware in place). 

[ndiswrapper is evil](http://acx100.sourceforge.net/ndis_cludge.html) and doesn't do any good at all.


Håkan

---

### Post by ZERO_SHIFT on 2006-10-11
"Canonical worked with HP to ensure that Ubuntu could be installed in the factory on thier laptops for sale in Europe as an option for thier customers."  -The Official Ubuntu Book

Also I would like to mention that HP depends heavly on Linux on thier mighty powerful servers.

---

### Post by ZERO_SHIFT on 2006-10-11
I just had this chat with a HP representative that might intrest you:
> Chat InformationYou are connected with HP's Pre-Sales Consulting Chat Service. My name is John. How may I help you with your sales questions today?
John: Hello and welcome. To make sure I get you to the best Sales Consultant for your solution, please tell me about how we can help you today?
you: hello
John: Hello.
John: How are you doing today?
you: fine thak you
you: *thank you
you: I would like to look for a laptop
you: for university
John: Great!
John: I appreciate your interest in HP.
you: I was thinking of HP dv2000t
you: but there is one tiny problem
you: I would like to be preinstalled with ubuntu liunx, and would like to know to what extent is it supportive to ubuntu?
you: hello??
John: Yes I am here.
John: We have a dedicated department handling queries related to these products, let me transfer you to them, please hold on for a moment.
Chat InformationPlease wait while I transfer the chat to Kevin.
Chat InformationYou are not currently connected to a chat representative.
Chat InformationYou are connected with HP's Pre-Sales Consulting Chat Service. My name is John. How may I help you with your sales questions today?
John: Hello.
John: I'm sorry our expertise team is busy assisting other customers.
John: Let me check on the information for you.
you: okay
John: One moment please...
you: I am waiting
John: I checked that for you.
you: yes
you: and..
John: I see that the dv2000t does not come pre installed with Linux.
John: However we do have business models that are certified to use...
John: Linux.
you: which ones are they?
John: I am getting that link for you.
you: okay
John: The models that are certified to use Linux are nw9440 , nx9420 , nw8440 , nc8430 , nx7400 , nc6400 , nx6325 , nc6320 , nx6310 , nc6220 and nc6230.
you: Thank you for your help
John: You're always welcome.
[[img]http://www.userbars.com/galerie/images/files/3/6/hp0np.png[/img]](http://www.userbars.com/)
[[img]http://www.userbars.com/galerie/images/files/3/13/ubuntu.jpg[/img]](http://www.userbars.com/)

---

### Post by Bagnaj97 on 2006-10-12
> **hw-tph said:**
> It works flawlessly with the bcm43xx driver that comes with Dapper. You just have to set it up (put the firmware in place). 

[ndiswrapper is evil](http://acx100.sourceforge.net/ndis_cludge.html) and doesn't do any good at all.


Håkan

I tried using the bcm43xx driver with no luck at all. I'm using it on my desktop with a bcm4306 chip, but it's listed as unstable for bcm4319 on the project's homepage and I had no luck getting it to work.

---

### Post by farmerbee on 2006-10-12
my asus w7k24j-sl is working well with ubuntu(just some difficulties in configure the buletooth mouse device)..

---

### Post by lH)4~mK0e on 2006-10-12
I have a Dell Inspiron 6000 and Ubuntu pretty much works with all devices right out of the box (so to speak).  I did opt to use the fglrx driver for my ati radeon x300 pcie 16x but that is kind of a given.  Other than having to rebuild that module with each kernel patch, I am satisfied with it.  The downside, this laptop is out of production.  I would say that any of the Dell's using i810 based architechture for the pci would work well.

---

### Post by rem on 2007-03-04
Hi all,

I would like to get myself a laptop and I was curious to know, from your experience, what would be the best laptop to use with Ubuntu, also concerning autonomy?

Thanks a lot!

---

### Post by Onyros on 2007-03-04
Talking only from my experience, after having tested Ubuntu on

- Fujitsu Siemens Amilo 7830
- Acer Ferrari 3000
- Toshiba M70-320
- IBM Thinkpad T23

The Thinkpad is, by far, not only the oldest, but also the most compatible. Taking into account the Thinkpads' history of compatibility with Ubuntu, I'd say those must be one of the safest bets. Meaning, betting on a new Lenovo Thinkpad, I'm not recommending the T23 anymore, even though it is still a fine machine. Curiously, in terms of autonomy, the Thinkpad with its old battery also beat the others mentioned (none of them known for being good laptops in terms of autonomy).

---

### Post by Redeyes_Gambit on 2007-03-04
My Acer travel mate 2423WXCI works out of the box with Edgy and Dapper. Breezy needed kernel headers but that's it.

---

### Post by Ubunted on 2007-03-04
I have had two Thinkpads (A22m and X30) and am considering a third (R40). Both worked extremely well and only got better with each release. Only big problems I had were a wireless issue with Edgy on the X30 and the ATi graphics on the A22m.

As long as you get one with Intel video (3D out of the box) you'll have no problems.

---

### Post by Kobalt on 2007-03-04
My HP dv6120eu has given me full satisfaction... 
I wouldn't recommend a particular brand or model, but I can strongly advise you to buy a laptop with nVidia graphics, maybe get some hints for the wireless as well to see what's the easiest to install (my broadcom 4311 was fine with  ndiswrapper)...

---

### Post by rem on 2007-03-04
Thanks a lot guys.. great to know there are so much options. Speaking of... I need to have some opinions from you guys before I go out there and purchase one.

Here's an offer I have for a DELL notebook:

> 
DELL D800 Intel Centrino   1600Mhz , 512 Mb RAM, 40Gb HDD, DVD, 15.4 inch UltraSharp WSXGA ,WiFi (802.11a/b/g) Bluetooth, USB 2.0, PCMCIA, Modem Touchpad Mouse , Wireless, Video 128 Mb X600


and the price for this one is about $US 680. I did a bit of researching on the www and found out that's working OK with Linux as well and the autonomy is pretty good. Instead, a friend of mine told me about these ones that there are some troubles with the batteries :confused:

---

### Post by banjobacon on 2007-03-04
I have a Dell 700m. The only problems I've had with it are:

1. The SD card reader doesn't work. Maybe it'll work in Fiesty, but I haven't looked into it. I don't really need it, as I can just plug in my camera.

2. The wrong resolution is applied on install. The solution to this is pretty simple, though.

The laptop was inexpensive, though, so no complaints.

---

### Post by rem on 2007-03-04
Sounds great... and yes, the price is pretty good...
I wouldn't worry about the resolution and the SD card reader either. What about autonomy?

---

### Post by RAV TUX on 2007-03-04
> **rem said:**
> Hi all,

I would like to get myself a laptop and I was curious to know, from your experience, what would be the best laptop to use with Ubuntu, also concerning autonomy?

Thanks a lot!

[Fujitsu Lifebook T4215]("http://store.shopfujitsu.com/fpc/Ecommerce/buildseriesbean.do?series=T4215")


(you can go here to [compare]("http://store.shopfujitsu.com/fpc/Ecommerce/xbproductcompare.do") different Fujitsu Notebooks)

---

### Post by seijuro on 2007-03-04
I have a Dell Inspiron 8200 with a nvidia card been running Ubuntu for 2 years w/o any problems only minor complaint is the payola drivers needed for the winmodem but if you don't need dialup then its not at issue at all.

---

### Post by lonce on 2007-03-04
My satellite I just bought works flawlessly.  Everything worked out of the box.  I was so happy I almost cried.

---

### Post by mtn on 2007-03-04
I have had really good experience with a new [Toshiba Satellite Pro A120 (Part Number: PSAC1E-04V00VEN)]("http://uk.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/seriesHomepage.do?service=UK&SERIES_ID=118119"), everything worked with Edgy – Beryl  3D desktop even worked with no configuration once the repositories were added, and Beryl installed - with the exception of the built in wireless card (so I use a[ Belkin pcmcia card]("http://www.linuxemporium.co.uk/products/wireless/#pid81765")) and the built in modem (which I have not tested).

I wouldn't buy from Dell after their [Ideastorm]("http://www.ubuntuforums.org/showpost.php?p=2235998&postcount=215") fiasco.

Not sure about Toshiba's ethical credentials, I seem to remember they are into Nuclear and other stuff.

Hope this helps

---

### Post by Anthem on 2007-03-04
Anything Centrino.  Native wireless and graphics drivers are to die for.

My wife bought a Toshiba A135, and everything worked out of the box.  Good price too.

---

### Post by Enigmus on 2007-03-05
I dunno if it's the best, but I use an old IBM Thinkpad R30, and it works pretty well, all things considered. I've been able to dual boot Kubuntu Edgy and Ubuntu Dapper off it, and it worked fantastically.

---

### Post by rem on 2007-03-05
Thanks guys for sharing your opinions...
I found this after all, within a local store at a very good price:

[http://www.fujitsu-siemens.com/products/mobile/notebooks/lifebook_c.html]("http://www.fujitsu-siemens.com/products/mobile/notebooks/lifebook_c.html")

What do you think, it's a go or it's a no? :D

---

### Post by wersdaluv on 2007-03-05
You might want to try [System76 Linux Laptops with Ubuntu pre-installed]("http://system76.com/") or [Dell's Open Source Notebooks]("http://www.dell.com/content/products/features.aspx/nseries_nb?c=us&cs=04&l=en&s=bsd").

I never had a chance to try them but they sure seem to be good for Ubuntu. 

:guitar:

---

### Post by graywizard on 2007-03-05
I just bought a shop rcubed laptop and love it - asus based too - loaded with ubuntu
[http://www.shoprcubed.com/](http://www.shoprcubed.com/)

 use it 100% wireless in my home and office.

---

### Post by claudex on 2007-03-05
I've got a Toshiba Satellite A110-178, all goes well, without the card reader which is a ENE and there are no drivers and the multifunction keys which seems to work with Feisty

---

### Post by rem on 2007-03-05
thanks a lot guys for all the posts.. i just bought the fujitsu-siemens machine... and installing edgy on it. so far so good... it seems to be just fine, hardware recognized, etc... we'll see along the way. thanks once again, i really appreciate it!

best!

---

### Post by graywizard on 2007-03-05
Great! Good Luck!

---

### Post by rem on 2007-03-05
thanks... i was thinking... since all of you guys posted here so many laptop solutions and almost none alike, than this should be another Ubuntu success story, isn't it? :) I'm still keeping my fingers crossed, hope mine will rule as well :)

---

### Post by Bartender on 2007-03-05
rem -
Thanks for posting your request, and thanks to everyone for input.  It's hard to find good feedback on modern laptops, so I always take notes when spying a thread like this one.
Thanks again!

---

### Post by rem on 2007-03-05
> **Bartender said:**
> rem -
Thanks for posting your request, and thanks to everyone for input.  It's hard to find good feedback on modern laptops, so I always take notes when spying a thread like this one.
Thanks again!

Problems here! Fujitsu-Siemens Lifebook  C Series, P4 Mobile.
Indeed the live CD went fine, the installation as well, but no booting afterwards. I posted this [http://ubuntuforums.org/showthread.php?p=2250812#post2250812](http://ubuntuforums.org/showthread.php?p=2250812#post2250812) and still waiting for a solution. Meanwhile I will try fix Grub if that's about it... :(

---

### Post by euler_fan on 2007-03-05
I have an Compaq v5000 (AMD64) and the only issue with dapper or edgy has been with the wireless, which works great with ndiswrapper. A small warning--at this time wireless is only supported using the 32-bit version, but its not a problem.

---

### Post by thomasaaron on 2007-03-05
I'm happy with my ACER Aspire 3000.

At first, the wireless was a little tough to get working, but that's all be sorted out now.
Other than that, it's been smooth sailing.

---

### Post by charles.g.moore on 2007-03-05
I am very satisfied with my HP dv6000t
Everything works (not out of the box of course)

---

### Post by rem on 2007-03-05
> **rem said:**
> Problems here! Fujitsu-Siemens Lifebook  C Series, P4 Mobile.
Indeed the live CD went fine, the installation as well, but no booting afterwards. I posted this [http://ubuntuforums.org/showthread.php?p=2250812#post2250812](http://ubuntuforums.org/showthread.php?p=2250812#post2250812) and still waiting for a solution. Meanwhile I will try fix Grub if that's about it... :(

I managed to fix it! Here's how: [http://ubuntuforums.org/showthread.php?p=2251202#post2251202](http://ubuntuforums.org/showthread.php?p=2251202#post2251202)
Everything is working ok now!

---

### Post by thomas.hoyland on 2007-03-26
ok guys,
i bought a laptop and ended up sending it back as it was a complete disappointment!
but
i need you to advise me...
what is the best laptop for ubuntu in terms of compatibility and stuff?
e.g. dell, ibm, acer, asus and what models?
what wifi chipset should i go for? etc etc?

regards,
tom

---

### Post by siucdude on 2007-03-26
Here is the best in my opinion.

[http://www.system76.com/](http://www.system76.com/)

Thanks
TJ

---

### Post by thomas.hoyland on 2007-03-26
yeh, i know about system76 and they dont sell in the uk...grrrrr

---

### Post by p252 on 2007-03-26
Well, I can only speak from personal experience. I am running Ubuntu on a cheap Dell Laptop (Inspirion B13/1300) which sports 1 gig of ram, Intel Celeron M processor, Intel 915 Express Graphics. It may not be as fancy as some but it has been awesome with Ubuntu. Most everything was picked up "out-of-box." The only thing I had to tweak was the screen resolution (install 915resolution) and the wifi. The laptop is using Dell TrueMobile 1370 (which is just a Broadcom 4318) and despite the horror stories I have read, I found getting the wireless to work easy (maybe because I searched the forums for hours before attempting). I don't think Dell makes the 1300 series anymore (though you may get it for an awesome price in the Dell outlet), but they do have a new Inspirion 1505 model. I'd stick with decent specs but not too fancy personally; definitely get one with an Intel graphics card being I have found them more user friendly.  I have also had the same success on and older HP Pavilion ZE4430US laptop I have sitting at home. 

As I said, this is just my personal experience; hope it helps.

p252

---

### Post by fuligin on 2007-03-26
Since you live in the UK. Perhaps you should try this online store:
[http://www.linuxemporium.co.uk/products/laptops/](http://www.linuxemporium.co.uk/products/laptops/)

From what I can recall they are the ones that distribute the powered by ubuntu stickers in the U.K. 

They are in Birmingham if you anywhere near the Midlands, they also look like they deal with IBM's I have seen some that do sell other brands. 
Personally i use a Thinkpad and am happy with it, but I havent personaly tried this store and dont even know if their prices are really good or not, but it should generally give u a bench mark of what you are looking for. 
Hope this helps.

---

### Post by p252 on 2007-03-26
Very nice Fuligin. I remember seeing Linux Emporium in a magazine. Completetly forgot about them though. . .

---

### Post by s0cket on 2007-03-26
I like Dell.  They stick with Intel chipsets and pretty decent hardware.  Ubuntu even supports my multimedia card reader out of box.  That impressed me greatly (both for Ubuntu and Dell).

---

### Post by dr_d12 on 2007-03-26
I'm using a thinkpad X40 and I haven't had any problems - I think all of my hardware was recognised and usable after a fresh install of feisty.
-D

---

### Post by thomas.hoyland on 2007-03-26
hey,
thanks for the huge response.
the laptop i bought was wierd
it was a core 2 duo with a really good spec and 12.1" screen (as im all about portability)
however, the cpu fan was blowing like a hurricane all the time
i scaled down the cpu in ubuntu but it made no difference at all and so the fan kept on blowing (killing batt life)
the wifi wudnt work either, it was an intel abg and i found the drivers but still no luck
saying that, the screen was gorgeous, but the rest was a let down.

i really like the look of thinkpads but im a bit scared ill get a laptop and it will have a fan blowing like a hurricane (quiet is also important to me)

any thoughts or experiences on loud fans on laptops, who are the worst? best?

regards,
tom

---

### Post by p252 on 2007-03-26
My Dell Inspirion 1300 is really quite. It does not run like  'hurricane' but it does run off and on every few minutes or so. My temp is kept between 48c to 55c.

---

### Post by thomas.hoyland on 2007-03-26
do you think that all small notebooks e.g. 12.1" screens etc have fan issues? maybe is because of the small size and all the stuff crammed in their?

any thoughts anyone?

---

### Post by dr_d12 on 2007-03-28
The thinkpad X40 has a 12" screen and under ubuntu the fan is off for the first 20 min while the laptop warms up, then it turns on to about 4000rpm and stays on until I shutdown. I'm pretty picky about noise and it's not loud enough to bother me.
If you really hate fan noise, my girlfriend's laptop is a fujitsu P7120. It has no fans. But she won't let me install linux on it.
-Dave

---

### Post by queen_yoshi on 2007-03-28
I have been running a few different flavours of linux and a few versions of Ubuntu (from Warty) on my Dell Inspiron 700m notebook. Everything bar the resolution works out of the box for me, and to fix the resolution these days is sooooo much easier with 915resolution available in the repos. Running CPU Freq I havent noticed any heat issues, then again I dont sit with my notebook resting on my lap or bed without it sat on a firm surface like a large book! As for fan noise there is little or no noise, and apart from the rev the fan makes at a restart there is not much going on, and I have never had an over temp problem!!

I too am looking to get a new notebook and the Dell 640m is currently a front runner, portable(14.1" widescreen - form factor isnt that much larger than the 700m) and after originally planning on getting an XPS M1210, I decided I dont need to spend money to get something with uber graphics as the Intel Intergrated works just fine for me at the moment :D

---

### Post by robenroute on 2007-03-29
You might want to give [www.zepto.com](www.zepto.com) (and select UK) an oggle. They build laptops with nothing but bog-standard components. These laptops have also been tested and reviewed with excellent outcome.

Happy hunting!

---

### Post by vadimolen on 2007-03-29
> **thomas.hoyland said:**
> hey,
the laptop i bought was wierd
it was a core 2 duo with a really good spec and 12.1" screen (as im all about portability)


I was in the same place as you a few months ago (and portability and battery life are the most important things for me).  I wound up getting a used Dell D410 on craigslist because I didn't need any serious specs.  I've never once been longing for more power in the last few months (it has a Pentium M proc and 1GB RAM).  You can get a new Dell D420 which is very similar only with  a widescreen display (and not old hardware:) ).

Absolutely everything worked 100% out of the box in Edgy except for wireless.  It had the cheap Broadcomm card and I messed around with ndiswrapper for a while before spending $30 on ebay for an intel ipw2100 card.

So, in summary: Dell D410, works wonderfully out of the box in edgy and feisty, but not if it comes with the broadcomm wireless.  You'll probably be equally happy with a D420 now.

---

### Post by gus sett on 2007-03-29
you can keep HP/Compaq on your candidate list if you haven't closed
a new deal just yet. a core 2 duo would probably run warmer than the
Celeron M in my unit, but the fan is quiet.  I found that doubling+ battery
capacity by getting a 12-cell pack and keeping the original 6 pack
as a spare to be well worth it :arrow:
:?: By the way, what do you make of the premium many vendors
want to charge for screens smaller than 13.3 inches or larger than
15.4
> **thomas.hoyland said:**
> hey,
thanks for the huge response.
the laptop i bought was wierd
it was a core 2 duo with a really good spec and 12.1" screen (as im all about portability)
however, the cpu fan was blowing like a hurricane all the time
i scaled down the cpu in ubuntu but it made no difference at all and so the fan kept on blowing (killing batt life)
the wifi wudnt work either, it was an intel abg and i found the drivers but still no luck
saying that, the screen was gorgeous, but the rest was a let down.

i really like the look of thinkpads but im a bit scared ill get a laptop and it will have a fan blowing like a hurricane (quiet is also important to me)

any thoughts or experiences on loud fans on laptops, who are the worst? best?

regards,
tom

---

### Post by zachalekos on 2007-04-13
Compaq Presario R3116EA works great with Edgy and works with Feisty live cd. It plays most games on windows as well.

---

### Post by Bossieman on 2008-03-18
All the current Zepto modells works perfectly with Hardy Heron

6224W
6324W
6625WD
3214W
3414W
3415W
3215W
6025WD

Even the webcams works
In 7.10 uou had to compile ALSA but now with 8.04 everything works perfect. :guitar:

---

### Post by Twitch6000 on 2008-03-18
I am going to be the lets say odd ball here and say get a acer aspire 9410.
Then if you need more ram you will be able to pay for it.For a OS btw if you Wan't just Linux you can buy them with No OS now I think.

Only thing that hasn't worked for me is the webcam that comes with it but,I think there is a workaround,I am still looking :).

---

### Post by barzam on 2008-05-15
Using an Inspiron 1520, everything works like a charm. Very smooth install, only the graphic card needed an update (quickly done though). 

The computer is quiet enough, but I'm starting to find it a bit big for my needs. I got it to be able to play games as well (and it does that well), only I play less than I intended.

I'd got for a small portable Dell if I was you. I know they have a pretty bad reputation but I haven't been disappointed with them yet.

---

### Post by xt0rt on 2008-05-15
I'm running Hardy on an HP Pavilion dv9500t (Core2 Duo 2.4GHz, 4GB RAM, GeForce 8600M GS, 2 120GB HDDs). When I purchased this laptop I did not originally plan on using Linux, but after two failed Vista installations and a refusal of XP to easily install over Vista (yes, I know there are several ways around this) I decided to make the switch.

Nearly everything is working out of the box (WiFi & Bluetooth included), with the exception of the webcam and fingerprint scanner. I know there is a workaround for the webcam, and well, fingerprint scanners are useless when drives are not encrypted.

This is a rather high-end laptop, and would probably be overkill for the average user. Still, if you are considering forking out some cash, not a bad buy.

---

### Post by bigbrovar on 2008-05-15
i once used a gateway its was the first lappi i used with linux... very fast and everything worked out of the box .. i cant quite remember the name now but i will find out ..
edited  gateway Mt6821 160gb 2 gb ram core2 duo 1.6 intel GMA 945 worked 100% with ubuntu .. everything worked

---

### Post by Ichido on 2008-05-17
Dell inspiron 1525n!
Came with Ubuntu 7.10 installed and everything, including wifi, worked great.
I added,dual boot, Heron 8.04 and everything stills works.
2GB RAM, Intel® Core™ 2 Duo T5450 (1.66GHz/667Mhz FSB/2MB cache), 120GB hard drive, 802.11g, Wide Screen, 2 hour battery gives 1.5 hours.
NOTE: 24/7 Phone Support is for M$ Windows only!
All Tech Questions are diverted to "Call Ubuntu Support" even if your question has nothing to do with the O.S.

Link:
[http://www.dell.com/content/products/productdetails.aspx/inspnnb_1525?c=us&l=en&s=dhs&cs=19&~oid=us~en~29~linux_3~~](http://www.dell.com/content/products/productdetails.aspx/inspnnb_1525?c=us&l=en&s=dhs&cs=19&~oid=us~en~29~linux_3~~)

---

