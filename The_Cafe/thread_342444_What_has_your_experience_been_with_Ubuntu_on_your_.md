---
title: "What has your experience been with Ubuntu on your laptop(s)?"
date: 2007-01-20
forum: The Cafe
---

### Post by PatrickMay16 on 2007-01-20
Hello everyone. Let's share our experiences with Ubuntu on laptops.

For me, my laptop is an old IBM thinkpad T22 which I bought on ebay in October 2006. I estimate that it dates to around 2001. I installed Ubuntu Dapper on it.

First off there was a severe problem with the video; the laptop would crash when X started. After some forum searching, I found that adding some lines to Xorg.conf would fix this problem. After that, it worked pretty much perfectly. Also, I bought a PCMCIA wireless card off ebay; a Safecom SWLCT-54125, which uses the Texas Instruments ACX111 chipset. It worked right out of the box with ubuntu; I just put it in, booted the laptop, configured it using GNOME's network config tool, and then I could use the wireless network. 
This laptop has a 900MHZ Pentium III and 256MB RAM, and the performance of ubuntu (GNOME desktop) on it is good. Even so, I did disable unused services and trim things down a bit to speed things up. Heh! I don't think this would be the case with windows vista. 
So Ubuntu on my laptop, apart from a video problem at the beginning, has worked very well.

How about everyone else?

---

### Post by po0f on 2007-01-20
PatrickMay16,

I've a T22 as well.  Ubuntu works perfectly on it (as perfect as a 900Mhz P3 can make it).  :)

No wireless, but I don't think that'll be an issue when it does come up.

---

### Post by Kateikyoushi on 2007-01-20
I have a Vaio X505 everything works fine even wireless but I won't put ubuntu on laptops because of the lack and quality of wireless tools.

---

### Post by EdThaSlayer on 2007-01-20
I have a CyberPowerSystem laptop(some gaming company) and when I installed Dapper Drake on it everything worked perfectly! The wireless "somehow" worked while so many other people on the forums were complaining about bad wireless on the laptops while mine worked out of the box!This whole experience with the laptop was great for me. Hopefully this(working out of the box) will stay the same when I try to upgrade to Feisty Fawn when it comes out.

---

### Post by Kateikyoushi on 2007-01-20
What happens if you leave home or school and try to look around for a hotspot ?

---

### Post by Erik Trybom on 2007-01-20
I have a Fujitsu-Siemens Lifebook from 2002. I think pretty much everything works, and it has gotten better and better with each new kernel version (I'm thinking particularly of hibernation and suspending).

On a side-note this computer actually was configured with dual boot Redhat/Windows 2000 when I got it. I rented it from my university and Linux was installed by default.

---

### Post by PatrickMay16 on 2007-01-20
> **Kateikyoushi said:**
> What happens if you leave home or school and try to look around for a hotspot ?

I do not know, because I have not tried that. Have you?

---

### Post by happy-and-lost on 2007-01-20
It's almost perfect on Ubuntu (Dell I6000), especially as wifi worked out of the box. Debian etch is better, though. Hibernate/suspend worked out of the box.

---

### Post by teaker1s on 2007-01-20
hp dv6000 series dv6116eu with ndiswrapper and [COLOR="Red"]network-manager-gnome[/COLOR] switching networks is easy with the utility:guitar:

---

### Post by zanglang on 2007-01-20
It's been pretty awesome for my old 1Ghz Compaq laptop so far. It needed a fair bit of tweaking to get things working the way i'd like it to, such as direct rendering on my graphic card, fixing hibernate, broken ACPI, looking for effortless ways to work with my DWL-650+ (had to settle down with ndiswrapper and network-manager)... I still don't have the best of power management, and it dies once in a blue moon, but i'm content. :D

---

### Post by teaker1s on 2007-01-20
im experiencing very rare lock ups and occasional boot/shutdown issues i've yet to resolve. also with the 6150go nvidia open GL driver it doesn't like ndiswrapper and wireless becomes unstable

---

### Post by cstrippie on 2007-01-20
When I first loaded Edgy it was on a Dell 9100 laptop, 3.2ghz p4 broadcom wireless, ATI 9700 video.  The wireless was so completely hopeless that I bought a PCMCIA card with linux support.  After that, things worked reasonably well with the exception of suspend: would go into suspend but would not come out.  Subwoofer never worked.

The new Dell is an e1705, c2d @ 2ghz, ATI x1400, Intel wireless.  With the exception of the subwoofer, *everything* on this book works in Edgy.  It's so flawless it's boring...so I moved to feisty.

Feisty herd 2 on this book is a different story - very little works, but I expect that to change as we go along.

Attempt to load Edgy on a Fujitsu test box (Pentium M, ATI 9000, likely broadcom wifi), resulted in a no-boot scenario on two different CD's. 

So, two for three.

---

### Post by Solicitous on 2007-01-20
WOW! My first post on the Ubuntu forums ever *head spin*

Well I'm a Gentoo user, but with the recent purchase of my new lappy, a Toshiba M110, I thought I would give Ubuntu a try.  To be honest I'm actually very impressed by it all.  The hardware in general worked right from the start of the install.  

Only issues I suffer from are any keyboard functions that require the Fn key (apparently because of the PheonixBios, oh well) don't work, so no adjusting screen brightness or anything.
And coming out of hibernate/suspend the sound card doesn't make any noise.

Other than that I'm a happy camper.

---

### Post by mips on 2007-01-20
> **PatrickMay16 said:**
> 
This laptop has a 900MHZ Pentium III and 256MB RAM, and the performance of ubuntu (GNOME desktop) on it is good. Even so, I did disable unused services and trim things down a bit to speed things up. 

Why don't you try something like Fluxbox or Enlightenment over gnome, it would be much faster.

---

### Post by Kateikyoushi on 2007-01-20
> **PatrickMay16 said:**
> I do not know, because I have not tried that. Have you?

I asked EdTheSlayer, actually for me it was too much pain to set it up for such a short time so I just borrowed my girlfriends ntoebook, shame on me. I think linux needs better wireless support more than the fancy windows and redesigned control panel of feisty.

---

### Post by floke on 2007-01-20
I have a crappy Toshiba Equium L20-197, which works perfectly, wireless and all (although its an ATI radeon stoneage 'graphics' (allegedly) card, so unfortunately no compiz or beryl:( )

Also have a Tecra A8 for work, which also works perfectly (it has an intel graphics card so compiz and beryl work like a dream \\:D/ ). Only issue is the sound, though. It works with the headphones on but nothing without - have tried all the howtos etc. and have filed a bug report (though people with far more knowledge that I will ever have on such matters reckon its a jack sense bug, so I'll have to wait and see) - Feisty, Edgy, Gentoo, Fedora, Knoppix and DreamLinux are all silent!

Still, a silent Linux world is better than the noise you get through those Windows!

---

### Post by Choad on 2007-01-20
got a zepto znote 6214 and everything works great except acpi. which is a big problem :(

---

### Post by matthew on 2007-01-20
My main computer is a laptop with Edgy installed on it and I've had a great experience. Click the "my hardware" link in my sig for specific details.

---

### Post by slimdog360 on 2007-01-20
the only problem is that it seems to run a little hotter then under windows. Other then that everything works. Ive got an IBM R50e Thinkpad.

---

### Post by frrobert on 2007-01-20
Running a Toshiba A70.  Would not recommend it as a laptop has had 3 motherboards (that another story).  But had no issues running Drapper Drake could not get the wireless to work under Edgy.

---

### Post by RandomJoe on 2007-01-20
I've run Linux on so many laptops over the years...!  Ubuntu I've put on a whole stack of Dell Latitudes.  C640, C810, C840(x2), D610 and just last night a C400.  All of them have worked OOTB except for wireless and modems.

I did have a few video "glitches" - mostly, a couple of these the boot-up splash screens looks *hideous*, but as soon as it switches to X everything's fine.  I usually disable the splash, so no biggie to me...  And my D610 wouldn't use native resolution until I got the 915resolution script going.  Still perfectly usable, though, just at a lower res.

Wireless has been interesting.  I have a D-Link 54Mb PCMCIA card that - surprising the heck outta me - worked perfectly from first boot.  Guess I got lucky with the chipset.  I have a couple of older 11Mb cards that work with native drivers, but they will only associate once, not sure if it's the drivers or perhaps just the old cards.  If I want to change which AP I'm connected to, I have to unload and reload the driver first!  They've _always_ done this, and back on Slack I just wrote a little script to do that.  Haven't bothered with figuring that out in Ubuntu though - I have newer cards so not much need for them.  The 54Mb miniPCI card is a Broadcom, so I have to use ndiswrapper, but once I set that up it's perfect.  When I boot up, it just connects to the appropriate AP.  But I have all of the APs I use preconfigured - home, work, so forth.  I've never tried searching for an available one.  (The one time I thought I would - at a hotel - they only had wired connections in the rooms.)

The modems will supposedly work, but as I haven't used a modem in years I've not bothered.  The things are winmodems, and they never worked well in Windows either so I'm not overly optimistic...

---

### Post by Obor on 2007-01-20
I have Ubuntu running on a Dell Smartstep 250N (Pentium4, 2.4GHz, 512RAM, desktop replacement laptop), that I bought back in 2001, without any problems. Can't get beryl/compiz working with my old ATI card though. It did work with Sabayon Live cd...

Also have Ubuntu running on my second laptop, Dell CPx, P3, 500MHz, 256RAM and ATI grafix. Ubuntu is one of the few distros that work out of the box on this pc. DVD playback is not as smooth as it was with Win2000. Suse, PC linux, freespire... all gave me screen problems (white stripe across).

Basically, no major problems and painless install on both laptops.

---

### Post by machoo02 on 2007-01-20
I have Kubuntu Edgy running on my Thinkpad R52 (Pentium-M 1.86 GHz, 1.5 Gb RAM, ATI X300, Intel 2915 mini-PCI wireless) and I have not had any major problems.  Probably the biggest issue thus far is having a reduced battery life: ~3 hours in WinXP vs. ~2 hours in Kubuntu.  Other than that...everything has worked like a charm OOTB.

---

### Post by Zuuswa on 2007-01-20
I have a compaq presario R4000, and after some xorg and driver tweaks, I was able to get full 3d acceleration and beryl/xgl running.  Although, I cant run counterstrike in xgl.  Overall, a great experience alltogether.

---

### Post by K.Mandla on 2007-01-20
Dell Inspiron 8000, 1Ghz PIII, 512Mb, 64Mb Geforce4 440 Go, 2x60Gb Toshiba HDDs, 8x dual layer DVD+-RW, Linksys WPC11 wireless.

Dell Inspiron 8100s of similar specs work equally well.

Dell Latitude CPx J750GT, 750Mhz PIII, 8Mb Rage Mobility M1, 512Mb, 20Gb Samsung HDD, 8x dual layer DVD+-RW, Linksys WPC11 wireless, custom paint job :biggrin:

I get an irritating mouse stutter with the CPx, but it happens regardless of distro, so I think it's a hardware issue. :(

I've also worked with dv6000 (?) machines from HP, which had trouble with the dreaded XPress 200M video card, but otherwise worked fine.

---

### Post by shanepardue on 2007-01-20
Mine worked perfectly out of the box..

HP Compaq nx6310 with integrated intel wireless and video. Beautiful AIGLX/Beryl graphics and perfect WPA2 wireless with networkmanager. Couldn't be happier with Edgy's performance.

---

### Post by raublekick on 2007-01-20
Dell Inspiron 9300

Everything works except Suspend / Hibernate, but I don't use them much anyways and I am too lazy to figure out why.

---

### Post by Rinzwind on 2007-01-20
> **raublekick said:**
> Dell Inspiron 9300

Everything works except Suspend / Hibernate, but I don't use them much anyways and I am too lazy to figure out why.

I have a Dell Inspiron 9300 too.
Everything works. Suspend/Hibernate worked out of the box too (If I recall correctly).
(Edgy)

---

### Post by ushaba on 2007-01-20
i've actually been pretty lucky with the Thinkpad T40 I have. I've probably installed ubuntu about a half dozen times over the course of my early flirtations with the distro, and i've learned that the following need to be done every time: save xorg.conf file to hard drive, save pppoe configuration file for weird hong kong service, and pray that the wireless card is recognized at startup. the xorg.conf is ok, as i've managed to eke out about 2500 fps on an old ATI mobility 7500, but the wireless is really a crap shoot. this is in fact the only reason i upgraded from dapper to edgy, because suddenly i would have no wireless card detected at startup and my ignorance was not solved by lack of an internet connection. i've gotten my few games working under wine, so the only reason i currently keep windows installed is to make sure that i have internet access in the event of a crisis. haha. i think it's pretty much the distro i've tried on the laptop, though i will admit that mandriva had pretty good wireless tools, all the drakes or whatever, but their ugly stoned penguins convinced me never to use their distro again.

---

### Post by beercz on 2007-01-20
I bought a new [HP Compaq nx7400]("http://h10010.www1.hp.com/wwpc/us/en/sm/WF06b/321957-64295-89315-321838-f33-1847094-1847095-3287111.html?jumpid=oc_R1002_USENC-001_HP%20Compaq%20nx7400%20Notebook%20PC&lang=en&cc=us") laptop in November 2006, installed Dapper on it and have since upgraded to Edgy.

No problems apart from power management not working correctly.  I updated the BIOS (downloaded from the HP website), and it has improved, including the correct battery usage reporting, although I do get occasional problems if I suspend my laptop with occasional lock ups when I resume, and I have to restart my networking when I resume.

Power management still needs to be improved though, as my battery only lasts about 2 hours.  With Windows installed I can over 3 hours (according to the laptop's documentation apparently - I don't have windows installed, just edgy).

Everything else worked out of the box for me.

---

### Post by mcduck on 2007-01-20
I have Asus A6Ja, and everything has worked perfectly out-of-the-box with Edgy. Only things I'm not sure are modem (I can't even remember when I used modem connection last time..) and webcam which I have absolutely no use for. If I get really bored some day I might check if the webcam works or not..

Only thing I had to do manually was installing fglrx drivers for this laptops mobility Radeon X1600, but even without that I had a working desktop.

---

### Post by LookTJ on 2007-01-20
Everything works out of the box except ATI card, which I don't care about installing.

---

### Post by ButteBlues on 2007-01-20
Mine's a Compaq Presario 1525US, Penitum 4, 512 MB RAM.

In most kernels, my function keys don't work.

My usb wireless adapter requires me to disable the bundled driver (which doesn't work), install a cvs third-party driver, and then manually configure /etc/network/interfaces to have wireless internet (included software still doesn't let me add wireless).

Upon default, it always gets my display wrong, so I have to edit xorg every time, else I have about 3 inches of unused screen between the right side and the bottom.

My ATI card only likes one resolution - the native maximum.

Everything else works fine.

---

### Post by PatrickMay16 on 2007-01-20
> **ButteBlues said:**
> My usb wireless adapter requires me to disable the bundled driver (which doesn't work), install a cvs third-party driver, and then manually configure /etc/network/interfaces to have wireless internet (included software still doesn't let me add wireless).

This sounds very similar to the experience I've had with a USB wlan adapt0r that I bought the other day. What chipset does yours use? What make, company, model number is it?

---

### Post by ButteBlues on 2007-01-20
> **PatrickMay16 said:**
> This sounds very similar to the experience I've had with a USB wlan adapt0r that I bought the other day. What chipset does yours use? What make, company, model number is it?
RT73 (using the seamonkey or whatever third-party GPL drivers).

Linksys Wireless G WUSB54GC

---

### Post by DarkOx on 2007-01-20
Ubuntu gets mad props for hardware support, at least so far as my Dell 600m laptop is concerned. Hibernate and suspend both work perfectly - along with apt, these are the features that make Ubuntu my favourite Linux OS at the moment.

The only thing that didn't work was my volume/mute keys (well, they do work, in the sense that they control my laptop's main speakers, which suck. The decent speakers which plug into my headphone jack weren't controlled by them at all) and wireless internet. 

Fortunately, thanks to keytouch and ndiswrapper, I managed to get both of those working. I've heard that the volume key thing will be solved out-of-the-box in Gnome 2.18, and that Feisty will come with network manager by default. If that's true, my laptop will be pretty much supported out of the box by Ubuntu.

---

### Post by Insomniac20k on 2007-01-20
I have never had a linux installation go so easily or smoothly. It took maybe 10 minutes AND everything including my wireless card worked. This has never happened on my laptop. A few minutes with Automatix2 and I had a fully functional system. 

Although every linux distro I've tried has supported more of my hardware than Windoze.

---

### Post by AndyCooll on 2007-01-20
Got a couple of old Toshiba Satellites and an aging Toshiba Satellite Pro. They don't come with wireless cards so bought some Belkin PCMCIA cards. Ubuntu Edgy recognises a couple of these out of the box, the third has a different chipset and I have to configure it. 

The install process can be trying time,. often failing. Patience and persistence are required. 

However that patience is rewarded, cos once installed they run fine, function keys work etc. I only use them at home, however all the functions I need work.

:cool:

---

### Post by Dainn on 2007-01-20
I have a Dell Inspiron 1150 with a D-Link WNA 1330.  I'm running Dapper.  Other than hibernate/suspend not working right, everything worked out of the box... at least I haven't noticed anything not working.

---

### Post by WorkingOnWise on 2007-01-20
In two words, freakin awsome! I have a Compaq Presario M2000 with an ATI Radeon Xpress 200M GPU, 512 ram, and a broadcom 4318 wifi card. Ubuntu Christian Edition 6.1 (identical to Ubuntu 6.1 as far as hardware goes) worked so well out of the box that I didn't even bother with a dual-boot with WinXP Home. Replaced my drive with a new 80Gig drive, installed Ubuntu CE 6.1, setup the wifi (took 30 minutes), and started all the open source goodies I could handle! Like a kid in a data candy store!
In fact, my video worked Better with the config that Ubuntu had that with the config and drivers that I got from ATI! I have to work harder to get video up using the vendor supplied drivers that with the OS supplied drivers! I can't remember the last time I had that problem in windows!
Ubuntu, as well as linux and open source in general have work to do still, but I would not hesitate to throw this at anyone now. It is time for linux people.
Oh, my power management works fine too....suspend, hibernate, shutdown and restart!

Very Nice.

Keith

---

### Post by eriqk on 2007-01-20
I have a Toshiba Tecra 8000 which must be close to 10 years old now.
So far, I've installed Breezy, Dapper and now Edgy, but always a customized install (except for the first Edgy installation because I clicked the wrong option).
Most of the hardware works OOB, except the (somewhat exotic) graphics card. On Breezy I got no X until I dpkg-reconfigured (had to fill in horizontal and vertical sync, even), on Edgy it picked a resolution of 640x480. In each case it went for 24 bits graphics which is simply too much for this poor old fogey of a notebook.
No onboard WiFi, but I have a Sweex PCMCIA card whith an Atheros chipset which Just Works.
On Breezy I thought I had no sound, until I decided to, like, turn the volume wheel.
I've never figured out if Suspend/hybernate work. I just turn the thing off.
The Fn key doesn't work- there should be a fix for this somewhere out there, but I'm too lazy to figure it out.
Great little all-round machine. Cost me 60 euro's, too. Can't beat that.
I'm thinking about getting the G3 PoBo from  my old job and Linuxify it just for fun.

Groet, Erik

---

### Post by LookTJ on 2007-01-20
> **DarkOx said:**
> in the sense that they control my laptop's main speakers, which suck. The decent speakers which plug into my headphone jack weren't controlled by them at all). 

Fortunately, thanks to keytouch and ndiswrapper, I managed to get both of those working. I've heard that the volume key thing will be solved out-of-the-box in Gnome 2.18, and that Feisty will come with network manager by default. If that's true, my laptop will be pretty much supported out of the box by Ubuntu.
That's funny because I too have Dell INSPIRON 600m. Wireless network is fine. but I want the volume thing to control the system(including headphones).

---

### Post by The Noble on 2007-01-20
All four of my laptops work great with Ubuntu, although some minor problems occur. My Dell inpiron 5150 has a broadcom card, but it works without any problems after tinkering. My old dell from long ago, which is a pentium 133 Mhz, still runs, but only with breezy and before because of the kernel (dsl and puppy have major graphic problems...). Otherwise, I have always been a happy camper.

---

### Post by DarkOx on 2007-01-20
> That's funny because I too have Dell INSPIRON 600m. Wireless network is fine. but I want the volume thing to control the system(including headphones).

Here's how I got it working:
1. Install keytouch and keytouch-editor (both are in the repositories, but you might need to install the beta keytouch-editor from [here]("http://sourceforge.net/project/showfiles.php?group_id=111201"))
2. Launch keytouch-editor, and make a file for your Dell 600m. I selected the default keyboard setting. After that, go to New to add a key, and it will ask for you to press one of your volume keys. You then have to associate a program that will change your volume to each key. I used "aumix -w -3" for volume down and "aumix -w +3" for volume up (I had to download auxmix first. It's in the repositories). Save.
3. I think that you could use amixer to do the same thing, which is installed in Ubuntu by default. I never got the syntax of that right, however and don't feel like experimenting with it right now.
4. Open up keytouch, and tell it to import the file you made in keytouch-editor. Select that file, and apply it (it's defaults should be fine). Test your buttons. As it currently stands, volume increase/decreases on mine, but the on screen volume bar doesn't appear, which is good enough for now.

Hope that helps.

---

### Post by rayclev on 2007-01-20
Hi,
I have an hp pavilion ze5375us laptop and was forced by circumstances to try Ubuntu 6.10. It worked perfectly for what I want my computer to do. I dual boot with Windows XP. My Belkin G Adapter worked upon booting up with no tweeking at all.
Cheers. rayclev

---

### Post by queen_yoshi on 2007-01-21
Well I am using my Dell Inspiron 700m with Ubuntu, firstly installed Warty and had a few problems especially in the good old days where you had to search and install 815resolution and create scripts etc to get it to boot into 1280x800 lol

Now I run Dapper and I must say that apart from a few dramas with suspend (doesnt want to come back to me sometimes!) the only thing that doesnt work from a fresh install is the wifi light, but someone here has already worked out how to get that running too! (I love these forums for that! Someone else has already solved it for you! =D> ) 
I connected to the net straight away (admitedly it connected to one of the neighbours un secured networks first lol), all I had to do was use Synaptic to get my resolution running at 1280x800 (so much easier now that 915resolution is now in the repositories!)

And thats been it! Otherwise perfect for me. I just tinker with everything else now and see what happens lol :biggrin:

---

### Post by LarryGB on 2007-01-21
Been quite happy right from the Dapper LiveCD to the install. Little hiccup on the dual boot process, but seems to have cured it self, with a little help. I've been documenting the hurdles here : [http://www.laerbe.com/Ubuntu%20Experiences.html](http://www.laerbe.com/Ubuntu%20Experiences.html) but for the most part all the hardware and external connections are perfect.

---

### Post by jimrz on 2007-01-21
have 2 ThinkPads, a T42 + my old 600x, both work pretty much ootb (well since dapper anyway, had to do a bit of tinkering to get the 600x setup under breezy) with minimal tinkering to get them pretty much "just right".

---

### Post by x_helium on 2007-01-21
Xubuntu (dig the mouse!!) on a IBM T41.  Everything works great except I can't connect my wifi.  Haven't researched it much since I've been using it for a couple of days.  Xubuntu is far superior to other distros available, imho.  Limited apps installed and picking and installing new apps is easy.

There is that hibernation issue with Debian Sarge that doesn't seem to carry over to Ubuntu....why is that?

---

### Post by euler_fan on 2007-01-22
I have two machines:

1) a Compaq v5000, which except for wireless works ootb (ndiswrapper fixes the wireless, and that is great!) I have tried Xubuntu and Ubuntu, and can't see a difference on my machine except for some things I like better in one or the other. I did just have my 64-bit OS really act up (I am now tri-booting XP, 32-bit Edgy, and 64-bit Edgy). It won't see the swap (rather spontaeously) and the panels won't display any more on boot. Haven't really tried to fix it, but also probably won't get around to it for a while.
2) A Dell Inspiron 1150. It dual boots XP and 32-bit Dapper. The only issue thus far has been (as usual) wireless. Have yet to fix it, but it also sits on my desk in my dorm as a back-up machine. ;) I suspect once I find the right how-to there will be no problems.

Off-topic, I just want to say thanks to all the people who volenteer to do tech support on the forums. They have been a great help to me and I just want to say thanks.

Back to laptops, overall everything else has worked great and if anything I will probably be able to use them both well past their usual service life just because I can keep moving to lighter and lighter windowing systems. (I think I might end up moving the dell to fluxubuntu from Xubuntu in 9-15 months or so when I get tired of being way behind my other machine in terms of updated apps).

---

### Post by Onyros on 2007-01-22
I have three laptops:

1--> Toshiba Satellite M70-320 (Pentium M 760 2.0GHz, 1GB RAM DDR2, 100GB HDD, ATi MR X700, etc). Everything working perfectly with Edgy. Obviously, after the first install I had to switch my xorg.conf to use VESA, and then installed ATi's proprietary drivers. I installed XGL+Beryl for curiosity and it worked perfectly. No wireless problems, as this laptop is a Centrino (therefore with Intel's wifi which works out of the box).

2--> IBM Thinkpad T23 (Pentium III-M 1.0GHz 512Kb L2 cache, 512MB RAM PC133, 20GB HDD, ATi graphics with 16MB of dedicated memory). Even though I do have the new machine, I love this oldie goldie. I use my own brand of Fluxbox + Ubuntu with it and it works flawlessly. I have a wireless adapter for it, as it's my most mobile lappy, I take it everywhere. Too bad the battery is waning in terms of capacity, but at least buying a new one won't be too expensive.

I actually have another one of these that I'm working on, it doesn't boot up, I hope it's not the motherboard, otherwise I'll have to sell it for parts.

3--> Compaq Presario 1714 (monitorless - Pentium III-M 1.0GHz, 512MB RAM PC 133, 20GB HDD, ATi MR 8MB). I once was very much into Mini-ITX systems, but I found this gem on a Portuguese auction site for a good price. It's now my media center, with that brand of Fluxbox + Ubuntu I personalized from a server install. It's working beautifully connected to my TV. Me and my wife use to for everything from leisure browsing the internet, to replying to emails (we have a special account configured just for the living room PC), to play a few MAME games. I might install MythTV on it later on, but now we really don't need that.

All in all, it's been a very good experience with laptops. Now, I'm just drooling over the new System 76 lappy's. Too bad they don't have reps here in Europe, otherwise my Toshiba would have been sold by now :P

---

### Post by Grey on 2007-01-22
Here's the laptops that I have personally installed Ubuntu on, and my results.

**1) Maria (My laptop)**

Toshiba Satellite M50-YK4.  Pentium M 1.73GHz, 1GB DDR, i915.

EVERYTHING works perfectly on this laptop, as of Edgy.  The SD card reader, the wireless, the video, suspend, hibernate, the works.  Windows would not be present on this laptop, except for the necessity of having it for work.  (I am a programmer who is forced to use dev tools written for windows).

**2) Bishop (My girlfriend's tablet)**

Gateway CX2620.  Pentium M 1.73GHz, 1GB DDR, X700.

Works nearly perfectly on this laptop, as of Edgy.  The tablet functionality works with a few very minor issues, although it required a couple hours of my time to get working.  SD card reader works, with a bit of fiddling.  Video works perfectly with both fglrx and open source drivers.  suspend and hibernate also function.  Ubuntu is the primary OS on this laptop.  It's never booted into Windows, although it's present.

**3) Tony (My girlfriend's daughter's laptop)**

IBM Thinkpad 600.  Pentium 2 433MHz.  128MB SDR, SVGA.

Works, with some minor issues.  Too slow to run Gnome, runs XFCE fine.  All peripherals seem to work, although sound was a real bitch to get working (took me two days).  When the computer suspends and tuxpaint is running, X has a tendency to crash.  I haven't gotten around to disabling suspend yet.  Ubuntu is the sole OS on this computer, as the girl who owns it is only 6, and just uses it for edutainment, such as gcompris.

---

### Post by hizaguchi on 2007-01-22
I've been using Kubuntu on my Acer Aspire 5102wlmi since August.  Nearly everything works in Edgy, but suspend to ram can be glitchy sometimes.  Other than that and, of course, the built-in camera and card reader, it works perfectly with the only catch being that you need to install fglrx if you want video hardware acceleration.

The hardware itself is a different story though.  The ATI Xpress 1100 video card has horribly broken OpenGL support.  Even with the latest driver in Windows you can't get more than 6fps on even old OpenGL games, like Savage.  Even Quake 2 slows down beyond being playable alot of the time.  That's minor though compared to the motherboard problems I'm having.  A few months ago, I started getting random freezes and crashes, which progressed to the computer sometimes failing to boot up.  Before long I was getting error messages about hard drive failure, even if I swapped in a different (known to be working) drive.  It got to the point that I couldn't use the computer for more than 5 minutes without an error, so I sent it (I had to pay for shipping) to Acer for repair.  They replaced a stick of ram and sent it back, and as soon as I turned it on "hard drive failure" popped up on the screen.  Back to Acer again.  I've not seen my laptop for more than a day in nearly 2 months, but I recently got an email saying it's on the way home.  I'm praying they actually fixed it this time, but I'm getting the impression that they'll just give me the run around until my warranty expires. :frown:

---

### Post by palmerthegeek on 2007-01-22
Good day,
I am a dual boot-er (still) due to XP and work stuff.  However, Ubuntu has been apart of my life since Breezy!  Current setup is Dell Lat D610, with the ever popular ATI graphic card!  Seriously I spend more time in Edgy then XP however, some apps I just can't get around....

Thanks.

---

### Post by sanone on 2007-01-22
I'm using my Toshiba Protege M200, a tablet notebook, as my default study/work pc. It works out of the box almost perfectly. \\:D/

Everything gets recognized automatically with the exception of the SD card reader since no drivers for Linux exist. I also had to install wacom-tools in order to get the pen working. This isn't hard but it would be nice if this could be checked at install. The same goes for the wireless network manager.

On the eye-candy part; I can run beryl quite good on this notebook, only 32 Mb of video ram, if I select to copy the rendering path. Also the rotation option, of the official nvidia driver, works if I use the script from [otto]("http://i-otto.blogspot.com/2006/09/toshiba-portg-m200-with-ubuntu.html").

The only thing that keeps bugging me is that I have to reconfigure my network settings every now and then at boot time. For some unknown reason the wireless device is disabled and the wired is enabled. 

Other then that I love it.. and I love to see people turn their heads as they see this notebook and if they look a bit better the slick OS I'm running!

San!

---

### Post by PartisanEntity on 2007-01-22
My Asus A6K is my main machine, and I am using it with Dapper. It is the only OS installed. I haven't had any trouble, just about everything works, SD card reader, wifi, touchpad, nvidia graphics card, sound, hibernation etc

Software wise everything works, a very stable system and it has not crashed on me once yet.

My specs are in my signature :) :

---

### Post by MethodOne on 2007-01-22
Compal DL70 dual-booting Kubuntu Edgy and XP Pro:

Everything works out of the box except the Winmodem, 3D acceleration (Mobility Radeon X600), and the volume hotkeys.  To get the modem to work, I just entered "apt-get install sl-modem-daemon" in the terminal and used GNOME PPP to dial.  I no longer have a use for that since I got DSL service from my phone company.  I got 3D acceleration working by installing the fglrx drivers.  The only problem after installing the drivers is that I had to edit my KDM configuration file to get my system to stop crashing at shutdown.  I did got Beryl to work with Xgl, but not with AIGLX (ATI's fault).  UT2004 works with default settings, but there was choppy sound when I ran it in KDE.  I didn't have this problem with IceWM.  With the volume hotkeys, I couldn't get them to work at all with any distribution.  I had to keep Windows because of the protected audio files my sister bought from the iTunes Store and a Windows-only vmplayer frontend called [moka5]("http://www.moka5.com").

---

### Post by Incense on 2007-01-22
I have a Compaq Presario V4000 series that has worked great with edgy and dapper. Everything (even the wifi) was detected and worked out of the box. Good times!

---

### Post by mostwanted on 2007-01-22
> **PartisanEntity said:**
> My Asus A6K is my main machine, and I am using it with Dapper. It is the only OS installed. I haven't had any trouble, just about everything works, SD card reader, wifi, touchpad, nvidia graphics card, sound, hibernation etc

Software wise everything works, a very stable system and it has not crashed on me once yet.

My specs are in my signature :) :

I have an ASUS V6J and the experience is the same, although to get the highest screen resolutions I was required to install the Nvidia drivers.

My problem is with accessing my school wifi network which uses PEAP certificate authentication (not properly supported by Linux yet). I'm banished to my home thereby negating most benefits of portability (I chose this laptop because it's very portable).

---

### Post by Patrick-Ruff on 2007-01-22
my experience sucked.  1.6GHz Pentium M, Mobility Radeon X300, the rest doesn't matter.

everything works well except that ATI card, and I also get 2 hours less battery life . . . it doesn't look like the proprietary drivers will support aiglx for a long time, so untill then I'm basically screwed.

---

### Post by Erunno on 2007-01-22
The only thing that is really bothersome on my Toshiba Satellite is that the CPU seems to be more often in need of cooling, the fan constantly switches on and off which is bothersome if you are trying to do some work. If I don't find out what's causing it in the next couple of days I'll put Windows back on it. Other than that Edgy used to crash pretty often right after release but seems to be stable right now. Hibernate/Suspend works out of the box with the nv drivers but won't work with nvidia drivers even after I make the proposed changes to various config files as outlined in the wiki (that's a minor point as I don't need the acceleration). WLAN usb stick wasn't detected as it is pretty new but ndiswrapper solved this problem in mere minutes.

---

### Post by Narzuhl on 2007-01-22
So i have run Ubuntu on 2 laptops.

1. a Toshiba Portege 3490CT. This ran great and once i setup the linksys wireless it was even better. Everything was picked up except the winmodem. (i believe i was using hoary at the time) that was an easy configure. ubuntu even booted of the PCMCIA cd rom. i got about 2.5 hours of battery life. Same as my Windows install.

2. is a Compaq Evo n610c this is working great. I am currently dual booting with Suse (suse is going away) I have tried Kubuntu (Edgy) and Ubuntu (Dapper) on this laptop.
again in Edgy i had to setup the wireless card, in Dapper it was auto detected (some Netgear model) 
I find this unit runs a little hotter in Ubuntu and Suse than it did in windows, but i thing this is just a configuration issue.

I did run Ubuntu Dapper on a IBM T60, but pulled it off as there was no support (that i could find anyways) for my Verizon WWAN card. 

So all in all i am very happy running Ubuntu on my laptop. Battery life in the n610c is about 3+ hours....this is the same i was receiving in Windows XP. 
Never did check the battery on the T60, but i bet it is close to the Windows install.

---

### Post by rev_b on 2007-01-22
I have Ubuntu on a HP pavilion dv1140 and everything works after instalation from the live cd. Widescreen, VGA out, suspend, touchpad, bluetooth (it's not enabled in windows by default, you have to use some obscure setting in HP rescue disks!), 3d aceleration (OS Intel drivers). Just had to enable the wireless network in system -> administration -> networking, because it defaults the network to the integrated 10/100 wired.

A very pleasant experience, IMO. MUCH more simple than installing windows on it, as after a default XP installation (not using HP "rescue" disks) you need 3dr party drivers for almost everything!

---

### Post by mustang on 2007-01-22
Running the first generation (core duo) macbook. 

Experience has been...not too great. No power management so it gets warm really quickly which in turn yields a 70% battery life compared to what I get in osx.

Suspend still doesn't shut down everything (fans remain on). And this is all with the newest kernel. I'm anxiously awaiting the Feisty release.

On the up side, it gives me an opportunity to explore OSX which so far, has been pretty positive. I intend to write a ubuntu versus OSX comparison sometime in the future.

---

### Post by bvanaerde on 2007-01-25
I've got an Acer Travelmate 4001WLMi.
Everything works great except for the battery life, which is 2 hours instead of 3.5 (on Windows XP).
Hibernate doesn't work all the time, but I can live with that.

I would be really happy if the battery problem would be solved.
edit: I just followed [this thread]("http://www.ubuntuforums.org/showthread.php?t=339089") to improve my battery life. Hope it will help...

---

### Post by anaconda on 2007-01-25
I have installed ubuntu to an old siemens laptop, hp dv2007ea, and couple of acer laptops

the siemens is so old that I didnt expect ubuntu to work at all, but it works fine execpt for the soundcard, which doesnt work, but I havent even tried.

the hp laptop was the hardest to get working properly. everything had to be manually configured. nvidia drivers, display resolution, webcam, souncard etc. the microphone is the only thing that still wont work. after doing all that work i am happy with my hp, but wish I would have bought an acer instead.

the 2 acer laptops (not mine) were the easiest. everything worked "out of the box" even with their integrated ATI- display cards! Drivers to which were installed automatilally with 3D-acceleration and direct rendering working out of the box..Amazing!  (didn't ever try the memorycard reader, so cant tell if it works or not.)

---

### Post by sloggerkhan on 2007-01-25
I've got an Acer Ferrari 4000 series (it was on sale when I needed a computer).
My first few installs were rough, but it actually runs Ubuntu very well.

Currently 3-D works, though every install I have to fix the xorg.conf file because even if I can use ATI drivers fine, it never detects the LCD panel correctly.

The wireless works perfectly (even though it's a "dreaded" broadcom 4318 airforce 1). I just used ndiswrapper and the driver from acer's website.

My card reader works fine for SD cards, though I have use a command to activate it. (forget what, I should make a script on login.)

Have no idea if the infrared works, I think bluetooth works, but haven't tried it cause I don't use the acer mouse.


All in all, I like the acer, but think think that it's 3-D performance is worse than it should be (off an ATI x700) with the fglrx or ati drivers.

But at least everything works. (Sleep, suspend, etc.)

---

### Post by stuh84 on 2007-01-25
All works pretty well for me.

I'm on an HP DV5120EU, 1.8 Gig Turion 64, 1 gig ram, 80GB HD, ATI X200 Radeon Xpress.

The wireless was the biggest pain to get working, couldn't do it for the life of me in 6.06. 6.10 I did it get it working using the BCM43XX Firmware cutter (yes, 4318 Airforce 1). Glad I didn't have to go down the NDISWrapper route, I don't like it. Using Network-Manager-Gnome as well so any networks can be found (although I've only ever needed to connect to two while using Ubuntu, both in my house). Never been near any hotspots so no idea how it would take them.

Video works fine (although cannot get Beryl or Compiz to work at all, tried many different times many different ways, all to no avail), mousepad was a bit erratic at first but it seems to have settled down, sound works perfectly, screen works perfectly in native resolution (1280 x 800). Getting running with a second screen can be a bit troublesome, and even when I do, the stretched wallpaper thing is just annoying.

I can't think of anything that really holds it back from being perfectly functional, everything useful is done.

I will have to see how it takes recording with once my audio interface arrives. Will see if its Linux compatible (no, I didn't buy one for being Linux compatible, because frankly I don't care if it is, ProTools isn't on Linux so it bothers me little if it doesn't work with it), and if so, will start using Ardour a bit I guess.

---

### Post by mike_m on 2007-01-28
I have a old Dell cpx, 650 mz, 512 ram, 5gig, HD, SMC wifi card -
Ubuntu works out of the box even the wifi, in fact Ubuntu is the only linux that works my wifi out of the box & I can never figure out how to set it up.

Anyways of all the linux's I've tried Ubuntu is the most complete & easy to use.

Tips: I had to set the swap size to 1gig at install for a smoother running system & install Gkrellm-i8kfan to run my dell fan

Now if I can get my Lexmark printer to work I'll be all set :)   

Mike

---

### Post by liamk on 2007-01-28
ibm t23 and only one problem - savage and video :/

[http://www.ubuntuforums.org/showthread.php?t=228393&highlight=savage](http://www.ubuntuforums.org/showthread.php?t=228393&highlight=savage)

[http://www.ubuntuforums.org/showthread.php?t=332234&highlight=savage](http://www.ubuntuforums.org/showthread.php?t=332234&highlight=savage)

---

### Post by FuturePilot on 2007-01-28
I've got Dapper running on my laptop. It works great. Really don't have any huge problems. The only thing that I have a problem with is my sound card. Audacity won't let me record or play anything.  But it's just Audacity as I can still play everything fine in any media player. I even got Beryl running great. Only a very slight lag to it. My laptop is a Dell Inspiron 8200 Nvidia GeForce 2 Go, Pentium 4M, 768 MB RAM

---

### Post by GaryAndersonMissed on 2007-01-28
You can see the specs of my ubuntu box in my sig....

Pain with the wireless card....
A little bit of pain with beryl...

Other than that life is peachy.

---

### Post by bcdeck on 2007-01-30
I have a Compaq Presario 1200s, 1 gig processor. It runs Dapper happily -- only thing I ever had to do was install codecs and such. Wireless via a D-Link PCMCIA card works on my home network (router is a Linksys) and at Wi-fi spots. 

I actually had a harder time converting my desktop (with its ATI video card) to Ubuntu. But it's running fine a well.

---

### Post by Artemis3 on 2007-01-30
I have found trouble with two HP laptops with their "whatever" hidden and recovery partitions. Gparted won't resize the large ntfs partition and spits out some silly error.

---

### Post by Bezmotivnik on 2007-01-30
I'm using a VIA-chipset ECS and Ubuntu doesn't work well enough on it for a permanent installation.

Wireless can be made to work in stupid mode, but the wireless support is still so primitive that there is no connection-quality monitor that I can find, nor can I get encryption/security to work at the level I want.

The Unichrome Pro video works, but only for routine tasks.  There are known issues in 3D that make it a non-starter for serious 3D and the squandering of driver development resources through forking (the plague of Linux) means that they will probably never get worked out before obsolescence.

I can't make my touchpad work for tap-tap/leftclick.

These are the problems I've uncovered so far, but the big one and the deal-killer is that Ubuntu 6.06 and 6.10 definitely, positively screw with the cooling fan operation in my notebook, and that scares me.  Fanboys will try to shout you down if you say that crummy drivers can cause hardware damage, but they *do* and system cooling is not trivial.  I'm not going to risk it with a notebook, which is difficult to work on and expensive to replace.

---

### Post by indigoshift on 2007-01-30
I'm running on an old (3+ years?  It was given to me by my old boss in college, and I don't know how long he had it before he gave it to me) Compaq Evo N600c with an equally-old Linksys wireless (PCMCIA) card.

Everything worked as soon as I installed Ubuntu.  This old girl (typing on it as we speak) may not be my main machine in two years' time, but for now it's working splendidly.

---

### Post by dbqp on 2007-01-31
I am running Ubuntu 6.06 on my IBM T30 (P4-M 1.86GHz and 512MB).  Installed great and usability is awesome.  Installed Automatix and got all the goodies...I even run VM Ware Server to run XP SP2 and have been really satisfied with the responsiveness.

The only trouble I had was getting a Motorola Wireless add-on card to work, as this notebook does not have wireless built-in.  Ended up using ndis wrapper, but always reactivates on reboot and has TERRIFIC range. I have totally disconnected my network cable and soley run wireless.

One negative: Battery life is shorter than using XP, but I can deal with this - no complaints!
I'll try the [thread mentioned earlier]("http://www.ubuntuforums.org/showthread.php?t=339089") regarding battery life.

---

### Post by gholen on 2007-02-02
My laptop works just fine under Dapper, but not under edgy.
But, lastly, I've been considering to go back to Windows to get my WiFi to work again.
Dapper and edgy are nice, bot i can't use wireless network, and if i for once have it connected, the system hang bigtime if I trie to give a WPA or a WEP key.

That does bullshit me, and Im not happy about it.
So, well, Windows seems to be the only solution. That sucks, but in my case, I really dont have a choise.

Oh, and the specs for the laptop is:
Dell Inspiron 1300
1,4 ghz Intel Celeron
256 Mb RAM
40 Gb harddrive
Broadcom AirForce One WiFi
Intel chipset
CD-RW/DVD

---

### Post by boredandblogging.com on 2007-02-02
Got a Dell Inspiron 6000 in December 2005. Installed Breezy on it back then and upgraded as usual. Never given me any problems with wireless.

---

### Post by wthanna on 2007-02-02
I have Ubuntu Dapper Drake ( 6.06 ) running on a Dell Inspiron 8100 1.2Ghz with 256MB RAM.  Let me tell you what this "old" "underpowered" ... at least by current "Windoze" standards, little beauty is doing for me.  I am running a web server hosting a fairly low traffic website (Apache) for my company... I run a Hula mail server, on which I host my company's email.. An FTP server... NX Server for remote access via FreeNX.. Samba for easy file sharing with our Windows machines..    I have been running Ubuntu since Warty (4.10?) and absolutely love it!  I'm sure this little machine is doing much more for us.. and will probably edit this post later when I have time to think about it a bit..  even while running all of these services in the background, it is still occasionally used for openoffice.org documents, email, browsing the web and other tasks..

---

### Post by TomFumb on 2007-02-03
I have a thinkpad x22 and I love having xubuntu on it. I had a little trouble with wireless at first, and I had to 'modify' a pair of wifi aerials that I bought for the intelbg2200 pci. 

My x22 has a 700mhz p3 and 256 mb memory, and with xubuntu it starts up faster than my 2.7ghz 512 mb laptop running xp. I think there's a lesson here...

---

### Post by Pikestaff on 2007-02-03
I have a Lenovo 3000 C100 that I bought maybe six months ago (so it's pretty new) and Kubuntu works perfectly fine on it... I've had no major problems thus far.  I had a few internet problems early on but I got that working with a little help from Google. ;)

---

### Post by slimdog360 on 2007-02-03
Ive got a tinkpad R50e (1.7GHz celeron, 768MB RAM) with ubuntu on it and it runs almost perfectly. It seems to run a little hotter then windows with the fan going on sooner when ubuntu is installed. Its the same with other distros such as mepis, xubutu, dreamlinux and so on.

---

### Post by Derspankster on 2007-02-04
I have an Acer 5003. Installation was flawless, wireless is not. I have a Broadcom 4318 card that I cannot make work. I've read just about every tutorial in these forums but still it does not work. Ubuntu with this laptop is essentially useless to me until I can get wireless to work. Any help would be appreciated.

---

### Post by Strider42 on 2007-02-04
I'm running a Dell Inspiron 8600.  Everything seems to work fine right out of the box with the exception of wireless (Broadcomm 4306).  I have tried tirelessly for weeks to get it running, but no luck.  I followed the excellent ndiswrapper thread here [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29") and got really close.  I gave up in the end because the bump on my head was getting larger and larger from hitting it against a wall.  I had an old Belkin PCMCIA card that I found hiding in a box of bits, popped that in, and away we went.  Wireless - the holy grail had been found.

I'm now just playing around with the OS, crashing it, reloading it when it all goes tits up, and learning lots in the proccess.  This is a second machine, so I guess I'm lucky to be able to do this.  Getting Beryl to work is the next task.

I do have a 30Gb M$ partition still, but as soon as I'm confident that I can do everything I need while on the road with the laptop, M$ will be deleted :)

---

### Post by rofarmer on 2007-02-05
I have a ThinkPad A20m with a port replicator, and experience with Ubuntu 6.10 has not been that good.  The machine previously had W2K, and the hard drive had problems and was replaced with a new one.  I installed Ubuntu from a CD to that fresh drive.  But now it will not connect to the internet at all.  I have posted some Forum questions, but have not had a response.   First difficulty was that many of the panels that open during the initial installation are too tall for my screen, and the buttons are almost entirely off the bottom, making it really hard to find"Continue".  Second problem was finding out where to type the SUDO commands.  "Terminal" is not at all intuitive.  So....I continue to try to find a way to connect, but if I can't, then I will have to "upgrade" back to Windows.

UPDATE !!!   Further experience gets only worse.  My internet connection has stopped working (I had a lot of trouble getting this to work initially, but with some help from the Forum people, it finally started to work).  My diskette drive is quite confused about what files are on what diskette, and usually reports the files on disk A (which is empty) as being those files which are actually on diskette B - no longer in the machine.  It seems unaware that the diskette has been removed and a new/different one inserted.  I never got around to testing all the function keys, and those specific to the ThinkPad.  Quick looks indicate a lot of them don;t work as designed.  I am completely unable to get SETI installed and connecting/working.  I regret to say I consider Ubuntu NOT ready for prime time.  Maybe on a desktop it would be easier to get working.   I will regrettably downgrade to Windows.  Thanks to all those who tried to help me.

---

### Post by pierskarsenbarg on 2007-02-05
I bought a Mesh laptop ([http://www.meshcomputers.com](http://www.meshcomputers.com)) just before Xmas ad put Ubuntu on it yesterday. Admittedly that hasn't given me a lot of time to play around with it. Although my wireless card was detected and could "see" all the wireless networks around me, I couldn't connect to my usual one straight away, but I think this was due to the way the network was set up, rather than the system. 

Other than that, it's all running very nicely on my dual core system with 1Gb ram. 

And for me next trick I will be trying to run WoW on it. I found some posts on the forums here to help me do that, so we shall see... That was pretty much the only thing keeping me from moving over to Linux anyway.

---

### Post by mattotoole on 2007-03-01
I'm running 5.10 (Breezy) on a T20.  It works great except I can't get the mic or sound recording to work, and it doesn't shut down completely all the time (I just power off manually, with no problems).

I've tried upgrading to Dapper and Edgy, but neither of them work.  I can get them to boot with the video in safe mode, but I can't get the wireless to work.

I really like my T20, and I hear the later T23s work perfectly with Dapper, so I might try one of those.

Despite these nitpicks I really like Ubuntu.  I feel much more productive with it than with anything I 've used in the past (Windows, other Linuxes).

---

### Post by tigerpants on 2007-03-01
Cheap as chips E-systems laptop entirely Intel based. Everything works perfectly, including the wifi, right out of the box. Hurrah for Intel.

---

### Post by Bear on 2007-03-02
I have a Sony Vaio that's around five years old and have had no trouble with Ubuntu 6.10. (no wireless) Runs great, no problems, love it.. :)

---

### Post by xyz on 2007-03-02
I have a 
>  description: Notebook
    product: Satellite A40
    vendor: TOSHIBA
    version: PSA40E-0DEWN-S4
    serial: 54039386H
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    512 RAM - 2.7 Ghz - 80 G HD

bought in August 2004 - no real problem but I have no printer, no wireless and I don't game.
Basically it's been good to me except that my HD died 22 months after I bought it. The "best" thing about it is that I bought it without checking for Linux compatibility. It was on sale: it was simply the cheapest!

---

### Post by ctt1wbw on 2007-03-02
Well, Back In The Day, I put Warty Warthog on my Dell Inspiron 8600.  Everything worked Out Of The Box.  Wifi worked, and it took all of about 3.456 seconds to get the nVidia drivers to work.

Now I still  have that same laptop, except that the wife uses XP on it.

I have a new HP dv8000.  I put Edgy on it and everything except the wifi Broadcom works.  I have ethernet ports all over the house, so I ain't worried.  Took some trying to get the ATI drivers and beryl to work, now that works too.

And I just bought a spare laptop, a Thinkpad T30.  I'm planning on using that one for school and making it a dedicated Fedora Core 6 system.

---

### Post by Sunflower1970 on 2007-03-02
I have a Thinkpad R40 P4-M 2.0 Ghz, 1 gig RAM 20 gig HD 14.1" screen. I had some issues at first with trying to install *any* version of Ubuntu 6.10...I'm guessing it didn't have enough RAM at first before I upgraded to the 1 gig. I also had some trouble with a PCIMA wireless card I bought (It's supposed to have an internal wireless card, but since it's a used laptop, it didn't), and for whatever reason, it still doesn't like a wired ethernet connection, but the wireless now works great (It's a Dlink WNA-2330), and I really don't care about the wired connection anyway. (well, now at least :P)

What's funny, is the problems I ended up having were kind of a surprise (wired, wireless, and trying to install Edgy and even Feisty). I was expecting tons of problems with the ATI Mobility 7500 graphics card in it, but it ended up being recognized and configured for 3-D right away.  :shock: I even was brave enough to try Beryl on it. And that works (almost) perfectly too. (I'm still not brave enough to try Beryl on my Dell desktop tho)

All in all my laptop experience is mixed. I'm thrilled it's working so well, but for about a week I was beginning to wonder if I should have even tried putting Ubuntu on a laptop.

---

### Post by qamelian on 2007-03-02
Overall my laptop experience with Ubuntu is good. I use a Compaq Presario R3000T and everything thing works on it except the 5-in-1 SD card reader, which I have no use for, so I don't even miss it. Wireless generally work well on it after installing the bcm-43xx firmaware and I get very good performance in Beryl using the open-source ATI/Radeon drivers. Ubuntu has been on this latop since Warty and was the first distro to actually work out of the box with the onboard sound card.

On the downside, while sound worked perfectly on Breezy, I wasn't so lucky with Dapper or Edgy. Both experienced frequent problems when ever I tried to play sound or video that included sound. Also I had to do a killall on esd to get the beast to boot to a desktop. These issues seem to be resolved on Feisty though as everything is working perfectly except the card reader which I haven't bothered to test.

---

### Post by wataboutbob on 2007-03-07
My laptop is a Dell XPS M1710. 

Everything worked out of the box except for subwoofer and WiFi WPA passkey which was fixed. Beryl worked without issues. 

So impressed with 6.10 Edgy that I use this all the time and login to Win XP only to game.

---

### Post by Ubunted on 2007-03-07
Two Thinkpads, A22m and X30. Both worked better out-of-the-box with Ubuntu than with Windows. Only outstanding issue I had was that Edgy saw the X30's wireless as an Ethernet adapter, but Dapper was fine.

Both are long gone and I'm considering an R40.

---

### Post by wersdaluv on 2007-03-07
I have a BenQ Joybook R31E. None of my USB peripherals work in Edgy and Feisty Herds. 

If I use Boot arguments, they work, but my wireless don't.

---

### Post by Black Dog on 2007-03-07
I have a Dell Inspiron 5000e. Dapper works just fine. Edgy did not - crazy battery life, and no help on the forums other to confirm that this was the case. So I went back to Dapper. Really concerned about Feisty working on this machine - who really needs wobbly windows? So I'll be staying with Dapper for a long time, which is a shame 'cos I really really want the latest f-spot.

Cheers,
David

---

### Post by PatrickMay16 on 2007-03-07
> **xyz said:**
> I have a 

bought in August 2004 - no real problem but I have no printer, no wireless and I don't game.
Basically it's been good to me except that my HD died 22 months after I bought it. The "best" thing about it is that I bought it without checking for Linux compatibility. It was on sale: it was simply the cheapest!

How much did it cost?

---

### Post by chili555 on 2007-03-19
I have two IBM T23's. My first I dropped and pieces broke all over it. I thought I was doomed. It started and runs perfectly. I downloaded the maintenance manual from IBM and took it pretty far apart and super-glued stuff back together and put it back together and it still works!

When I saw how cheap they were getting on Ebay, I bought another, for spares, I told myself. Well, it sits on a table upstairs and I run Edgy on it, too.

Both work perfectly with Ubuntu, although I have never experimented with suspend/sleep/hibernate/cryo-freeze/etc. I just use it plugged in on my lap and turn it off when I'm done. 

I have a T60 on order and will have Edgy or Feisty on it by the end of the day it's received. What sane man needs three laptops? Is there a twelve-step program?

---

### Post by Hortinstein on 2007-03-19
I got the laptop in my sig, and after a little wifi hardware tinkering, it works great.  I would never reinstall vista on this computer...ever

I really have enjoyed my ubuntu exp so far

---

### Post by DrOlaf on 2007-03-19
I have an Acer Aspire 5002WLMi, currently triple-booting 32-bit Edgy with Gnome, 64-bit Edgy with Kubuntu, and (very rarely) the Windows XP home that it came with. With two exceptions, I'm very happy with it. Everything worked OOTB or with minimal finagling (such as manually editing xorg.conf to get the 1280x800 resolution working). Suspend works great, but hibernate isn't so good - but I never use that anyway.

The first problem was WiFi. The machine came with a BCM4318 card, and I managed to get ndiswrapper working sort-of-OK with it, but in the end it was easier to spend 20 bucks at newegg to get a different mini-PCI wireless card that works with FOSS drivers. 

The second problem isn't really a problem, just an annoyance due to my insufficient research before I made my purchase. The onboard graphics is an el-crappo SIS chip that is OK with regular gnome or KDE, but means there's no Beryl for me on the notebook. 

Other than that, it works great. I have to download and compile a lot of work-related programs that aren't in the repos, and I haven't had major problems with that yet. My goal is to provide myself with a <$1,000 portable bioinfomatics workstation, and I'm about 80% there, I reckon.

---

### Post by ali4949 on 2007-03-19
Using Dapper on IBM Thinkpad T30 with 768MB of ram. First time out of the box wi-fi worked on my US robotics wireless card.. tried ndis wrapper for the netgear 54G card but found out that it uses the marvell chipset  which just doesnt want to work. sound works great. Pretty much just waiting for fiesty fawn official release to upgrade to the new features.

---

### Post by diskotek on 2007-03-19
i'm on HP Compaq nx6110: i run kubuntu 6.06/ubuntu 6.06 and xubuntu 6.06-6.10 on it. they all worked perfectly. i stuck to xubuntu 6.10 now... i never faced with a problem and i'm a quite newbie :)

---

### Post by konungursvia on 2007-03-19
Dapper on a Dell Inspiron 8200, it works great, except no DVD disks will mount, no encrypted wireless connection that works, and some huge mpegs in ts format say "too many frames per buffer". Other than that, in a million ways, I love it!

---

### Post by hardyn on 2007-03-19
Edgy on an Asus Z71Vp... most things worked out of the box... no card reader, no modem... things i don't think should be in notebooks anyway... but that is a talk for another day.

I think it works so well becuase everthing in here is pretty common, intel wireless and nvidia video, which is using the nvidia binary drivers. AND all the "dashboard" buttons work!

the power management under ubuntu i find to be 'fair' at best... its something that really needs some work,  like enabling wifi power management.  power management is something that i would like the nvidia people to do to.

all and all... works really well.

---

### Post by lintroduccion on 2007-03-19
I'm using a Dell Inspiron 6400.

It works almost perfectly. The forum has an excellent howto about setting things up in this model, as Fan Control and ATI card needed extra attention after install. Wi-fi worked out of the box, and except some minor issues with Fn keys and WPA annoyance I'm quite satisfied with it.

---

### Post by jnev on 2007-03-19
I have a compal hel80 (intel t7200, 7600go, 1gb ram, wifi/bluetooth, etc) running feisty. everything works perfectly except for the built-in webcam, bluetooth, and suspend/hibernate. while the suspend/hibernate I'd like to get working, it really doesn't bother me too much...

---

### Post by Kevanx on 2007-03-20
I've been delighted with my first week with Edgy, after doing a dual boot install after years of agony with XP (and worse - M.E.)

Running a Toshiba Satellite 1800 series. It's in rough shape, but bumped the HD (after a crash) up to 40Gb from a measly 14, and the ram up to 384 Mb from 128Mb. She's far from mighty, but it's running super smoothly, everything adapted easy-peasy.

Running it off the LiveCD led to really slow startup times, and an apparent issue with my ALi cyberblade card (confirmed on the forums), but I sucked it up and installed, the problems disappeared. Had a fun time exploring xorg.conf trying to get the forward/back buttons working on my PS/2 logitech mouse, but apart from that, everything has been SWEET. I love the OS. Just wish my crappy graphics card could run beryl, but I've never been too much of a sucker for eyecandy.

I have to admit though - Amarok is damn good, but I really miss Winamp.

Anyway, this forum alone has been worth the switch. I'm just glad that my IRC days way back when prepped me for basic linux commands so I don't feel like an utter toolbox of a newb.
Cheers all!

---

### Post by eXcentra on 2007-03-20
VERY good. 
I've been using Ubuntu on my Samsung Sens P28 since 5.04. Runs perfectly; wireless, Beryl and all. :)

---

### Post by nebhead on 2007-03-21
on an acer travelmate 2420 all i needed was a simple wireless driver and more RAM and everything run perfectly. didn't even have to sort the graphics card for beryl,  all worked out of the box.  The little buttons all above the keyboard launched what they were supposed to, as well, quite pleased with it :D

---

### Post by ppatalano on 2007-03-21
I'm on a ThinkPad T60p and I've never been happier, the only troubles I've had were the FireGL 5200 I have in here and the wireless card iwp 3945abg (getting that to work was slightly annoying).

---

### Post by got_nix on 2007-03-24
I gotta be honest as of lately its been a nightmare.. nothing wants to work. :( . Ati x1300  video card.. for the love of God it will not install properly following many different guides the resolution comes out correct but when i do fglrxinfo i'm still getting vesa info. glrxgears runs very slow and slouchy. beryl i cant even think about it

really ironic when i had a lame inspiron 6000 with intel gma card i was able to succesfully configure everything on my own compiz and the works. now i got a way better laptop and nothing works.

---

### Post by gree on 2007-03-28
Ubuntu was troublesome on my last laptop (amilo a7600), because I had to patch the kernel with DSDT to enable direct rendering and the usb ports. But I have bought a new laptop (broke the old while disassembling it), an Amilo V3205, and this one works pretty good with Feisty. (the mic doesn't work with earlier versions). But whichever linux distro I've tested, suspend freezes the touchpad, and I'll have to use a usb-mouse if i want to use suspend.

Thus far, the suspend issue is the only thing keeping a small windows partition on my laptop, for when I'm moving around with it.

---

### Post by Hallvor on 2007-03-28
The wireless (Atheros AR5005G) on an Acer Travelmate 2310 worked fine for a few days, then broke. This happened both on Dapper and Edgy. I have searched the forums and tried just about everything out there to fix it; so if I can`t solve it, I`ll install Windows and wait for better drivers.

(Dapper works flawlessly on my desktop, though.)

---

### Post by ndefontenay on 2007-03-28
I tried to convert a friend who, after buying an asus laptop for work, had an old dell left aside.

I proposed to convert her and she was really willing to try. 
But it wouldn't install at all.
It took ages to boot.
The first time, I didn't had the install permanently icon on the desktop.
2nd time, when I pressed it, it took ages to open a window.
Finally I stopped it and had a bitter taste of failure.
I tried to convince her to use her empty D partition to dual boot her new laptop because it would be O so cool to get to your customer and have such cool interface, different from windows but she wouldn't let me because quote "I'm scared to break it"

Jesus! 

Sometimes advocacy is not fun at all.

---

### Post by teaker1s on 2007-03-28
I'd advocate you offer to install and return within one week, that way you can iron out install issues and setup and test. thats what my grandparents ubuntu box got. I never hear about it as my gran reckons It just works:), unless they ask how to change something

---

### Post by jariku on 2007-03-28
I'm using Ubuntu Feisty on my Acer Aspire 3610 laptop and so far the only problems I have currently is that I have some dead buttons on my Finnish keyboard (the euro and dollar signs next to the arrow keys and two of the "special" keys the computer has above the keyboard.

I don't think I'm going to do anything to the currency keys that aren't working, they're mostly in the way anyway.

With Kubuntu Feisty I had a problem with my NTFS USB-HD not mounting automatically, but that got sorted out automagically when I switched from KDE to Gnome.

---

### Post by Aetherius on 2007-03-28
NO problems at all :D

Feisty on my new Thinkpad R60e, and everything (plus some) works out of the box!

---

### Post by Cippa Lippa on 2007-03-28
Hei

I have a ECS G732 and kubuntu feisty worked almost out of the box. I have some problems with an external firewire drive not mounting automatically but for the rest everything is fine... I would hope though that grub installation would be a bit more user-friendly. When I did it the first time I was wondering what hd0,0 stood for. The result is that I installed grub on my windows drive and I screwed it for good.

Cheers

Cippa

---

### Post by Ozor Mox on 2007-03-28
On my Dell Latitude D600 Ubuntu installed and ran absolutely fine. The only thing that didn't work and took me a while to figure out was my Broadcom BCM4309 built-in wireless card, but thanks to the excellent documentation and community help I got it sorted. Everything else has been very quick to get working so far. I've not missed Windows even a little bit.

---

### Post by bigjack on 2007-03-29
Ubuntu 6.10 Edgy Eft installed and worked perfectly on IBM Thinkpad T40--found the wireless card and connected to my home wireless network with no problem.

But in trying to upgrade to Feisty Fawn 7.04 Beta it went smoothly until the stage for checking for outdated software--total freeze.  I had to turn off the computer, then reboot.  All looked OK but could not get the wireless to see our home network.

Decided to install Feisty Fawn 7.04 Beta from CD.  When it got to the stage for setting up the network, it could not see our network.  Note that Edgy 6.10 Edgy Eft sees network and sets up wireless with no problem.

Going to keep using Edgy Eft 6.1 until problem with Feisty Fawn and wireless is corrected.

---

### Post by stchman on 2007-03-30
> **PatrickMay16 said:**
> Hello everyone. Let's share our experiences with Ubuntu on laptops.

For me, my laptop is an old IBM thinkpad T22 which I bought on ebay in October 2006. I estimate that it dates to around 2001. I installed Ubuntu Dapper on it.

First off there was a severe problem with the video; the laptop would crash when X started. After some forum searching, I found that adding some lines to Xorg.conf would fix this problem. After that, it worked pretty much perfectly. Also, I bought a PCMCIA wireless card off ebay; a Safecom SWLCT-54125, which uses the Texas Instruments ACX111 chipset. It worked right out of the box with ubuntu; I just put it in, booted the laptop, configured it using GNOME's network config tool, and then I could use the wireless network. 
This laptop has a 900MHZ Pentium III and 256MB RAM, and the performance of ubuntu (GNOME desktop) on it is good. Even so, I did disable unused services and trim things down a bit to speed things up. Heh! I don't think this would be the case with windows vista. 
So Ubuntu on my laptop, apart from a video problem at the beginning, has worked very well.

How about everyone else?

My Toshiba laptop works very well with Ubuntu.  I have been able to get all devices working.

1.  Installed latest ATI video drivers
2.  Installed latest madwifi drivers for my built in Atheros wireless
3.  All motherboard and chipset drivers work.
4.  Power management works
5.  Very stable
6.  Works with my flash drives, digital cameras, zip drives.  Have not tried Bluetooth.
7.  I don't know if it works with the crappy winmodem, but I have not used dialup in years.

All in all I would recommend Ubuntu for a laptop.

---

### Post by RaZer0r on 2007-03-30
same here, no problems at all, not during instalation not after.
intel core duo T2300@ 1.6Ghz
intel 950 graphics card
wireless didn't work in edgy or dapper, but with the feisty beta it worked out of the box :)
bluetooth is somehow a pain in the ***, still looking for a way to get that working.
hibernate works, but something wierd is going on, as it wakes up im not able to use the letters u i and o for some reason, unfortunately my pass includes some of those letters :confused: 

and i had to apply the 915resolution patch to get my native resolution (1280x800) to work
i have an acer aspire 5612WLMi

---

### Post by Onyros on 2007-03-30
Anyone installed Ubuntu on a Sony C2Z/B yet? I've pre-ordered one recently, and don't expect many headaches, but one never knows...

---

### Post by shugasmax on 2007-03-31
> **K.Mandla said:**
> Dell Inspiron 8000, 1Ghz PIII, 512Mb, 64Mb Geforce4 440 Go, 2x60Gb Toshiba HDDs, 8x dual layer DVD+-RW, Linksys WPC11 wireless.

Dell Inspiron 8100s of similar specs work equally well.


I get an irritating mouse stutter with the CPx, but it happens regardless of distro, so I think it's a hardware issue. :(
.

do you get the mouse stutter on the Inspiron as well?  I'm running mint on a lattitude c600 (it's run dapper and edgy before as well) and have a mouse issue.  If I remember correctly there is a simple fix.  I believe its something to do with switching from ACPI to APM for power management.  Sorry I can't recall the exact thread but I did fix it at one point.

-Max

---

### Post by shugasmax on 2007-03-31
Woops.  Once again a case is made for searching the forums thoroughly before posting.  Sounds like you [figured it out]("http://ubuntuforums.org/showthread.php?t=180656&highlight=mouse+acpi+stutter").  So did this ultimately work for you?

---

### Post by SDF-1 on 2007-04-02
I am running a ASUS F3Jp 2006 Model.

Specifications:

 - Intel Centrino Core 2 Duo Inside 1.66Ghz
 - ATI Mobility Radeon X1700 512MB*
 - 80GB ATA HD
 - 2GB RAM

I know this laptop may be completely psycho to run a Ubuntu but it is absolute flawless performance, thats what I love about Ubuntu unlike Windows with their poor coding which causes crashes, etc. The biggest problem for me is that its hard to install my graphics card. I still haven't had the chance to install Beryl and XGL, very eager to see how the performance goes thats if I can get my graphics card installed. :(  Does anyone have any ideas of how I can install my graphics card?

Go GNOME! :)

---

### Post by kombinator on 2007-04-07
Toshiba P100 PSPA3C-SD300 here (Core Duo 1.83ghz, 1 gig ram, Geforce Go 7300, 100gb hd, 17" widescreen, Intel Conexant paininthearse audio, Intel Pro Wireless 3945ABG).  I'm dual booting Kubuntu with the OEM Windows XP that was preinstalled (hey, as much as I hate it, I paid for it right?). 

In Edgy it was a royal pain to get wireless working (took hours of tweaking and changing and downloading over a wired connection...and when it finally did work it showed up as an Unknown device so I couldn't edit any settings without it crashing.  It eventually stopped working altogether and I couldn't connect anywhere), and I had to use the JR100E custom DSDT to get sound and acpi working at the same time.

I reformatted and clean installed Feisty and found that everything but sound worked out of the box.  Wireless was brilliant, it detected correctly and I could switch to monitor mode should I so desire (although upon switching it back to managed it won't connect anywhere until I reboot), and with a quick run of the initrd-add-dsdt script from [http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml) sound was running and everything was bank, no annoying kernel recompile required.  Very painless.  

Kubuntu loads and runs like an absolute dream come true--blazingly fast.  UT2004 would take 4 minutes to load on Windows regardless of how many or how few bots I'm loading or how large or small the map was, and it takes about 12 seconds in Feisty with 30 bots and ONS-Severance, the largest map in the game(as my friend said, the Windows load time includes 12 seconds for the game, and 3 minutes 48 seconds for Windows to take a crap :D).

So...although YMMV, it can indeed require a fair bit of tweaking on this model (thanks for your support, Toshiba :roll:), but I'm so fed up with Windows inducing migraines that I couldn't care less, not to mention my laptop runs at three times the speed it did under Windows.  It's worth every minute of it to me, as at least I know what's going into my computer and can fix the damn problems at my leisure without waiting for a patch from Microsoft!

---

### Post by RAV TUX on 2007-04-07
Installed on a Fujitsu T4215 convertible, everything worked like a dream without event, except some tweaking needed on the wacom....

Fujitsu really is a superior choice if you want a laptop or convertible where things will just work with Linux.

---

### Post by Compucore on 2007-04-07
I have installed ubuntu dapper drake on two IBM thinkpads over here. The thinkpad R32 and a older on I forgot the specific model number right now. BOth work great overall on both. One being a celery 550 and this one the h32 being a PIV 1.6ghs with 256 megs of ram. So far no complaints whatt so ever with the well known exception of the soft modem on both that were not compatable with dapper drake. Which is normal I find since they didn't make it like a true modem to begin with for them. WIsh they were working though. It would be nice to use it as well. I had even checked the settings under administration networking to bring it live. But ni avail to get them working. THe wireless and regular networking is perfect though for it. And the other as well. Can't live without using my ubuntu.

Compucore

---

### Post by waynetar on 2007-04-17
I have a Dell Cpi J and want to install ubuntu on it, I tried booting version 6.06, it almost loads then the screen goes black and stay's that way.  Uggh, Can anybody Help Me?

---

### Post by Skarjoko on 2007-04-17
Running Edgy on a Dell D400, and everything was up and running fine when I installed it. The only problem I have is that I can't seem to get any music programs to record my guitar (which I've plugged into the mic slot with an adapter).

---

### Post by Erunno on 2007-04-18
I've installed Feisty on my laptop today and activating the restricted nvidia drivers with the restricted manager still cripples hibernate. Once I hit hibernate the screen goes black and stays that way and I'm forced to power down the laptop manually (and losing all session data along the way). I had really hoped that they would take it into account when creating the restricted manager. Meh :-/

---

### Post by pirothezero on 2007-04-18
Ubuntu 6.10 soon to be 7.04 on IBM Thinkpad T42. After following one guide about the WPA I got network manager plus 2100 wireless to work which was the only problem. Haven't had any problems since. 

I've been blessed to be able to have such a great system with such a great os :)

---

### Post by PatrickMay16 on 2007-04-18
I recently bought an Asus Z35F laptop, and it works great with Ubuntu. I bought it from Shafetech, but unfortunately they closed their business earlier this month.

---

### Post by fallscrape on 2007-04-18
I have several laptops, two however I've installed ubuntu on.

One was an IPC cr*ptop with a cracked lid.  About 128MB ram (32mb shared) with 9.2gb HD 900mhz processor - massively noisy.  Runs fine if not a little slow straight from the box.

Second laptop was a MV laptop - 1.6gh P4M with 1ghz RAM and 20gb HD. It is a little bit odd because it boots off linux already - from factory - using a special version of powerDVD for linux when you press the 'P' button.  Works seperately to the main OS.  That also installed fine and picked up the wireless card, bluetooth etc (at least on v6.10).  Upgraded to 7.04beta with no probs.  Will probably start from scratch as it has nothing worth keeping on it at present.

---

### Post by dthomasdigital on 2007-04-18
I run fiesty on a Dell c840 and it runs like a champ.

---

### Post by tmortn on 2007-04-27
Dell Latitude D820 here.

Wireless worked fine with a PMCIA card to start with. Got the internal Broadcom card working later with ndiswrapper. Still having problems with WEP though.

Picked up my WUXGA resolution with no configuration file mucking which was the first time I have not had to mess with that stuff when trying out Linux in the past.

Sound works out of the box... another first in my linux experience (Other than later versions of Knoppix)

Beryl is iffy but its beta, typically have it off. It does work... just doesn't seem to play nice with suspend/resume. Have not had a black screen resume with it disabled yet. Really like what I have seen of it... but its got a ways to go. 

Suspend/Hibernate is a bit funky. Works fine sometimes, other times random things don't start back up... networking, sound etc... Have only gotten the dreaded lappy black screen of linux resume death a couple of times so far (dozens of suspend/resume cycles). And it hasn't blacked screened on me at all without Beryl active.

Buttons all work... sound +/- on/off, auto light sensor, dim brighten LCD. WiFi detecor does not work however. 

Internal mic does not work which is a bummer. Means Skype is awkward. Bluetooth headset linking is non-obvious and I think requires an ALSA rebuild. Have not found anyone on the forums that has had much success with Dell internal mics

Don't have an express card so no idea if that works... the smart card reader is showing up and not causing any problems but also don't have one of those to test . Have not had to use the modem either. 

Don't have the fingerprint scanner so no idea on it.

CD read and write, DVD read and write all worked out of the box which was nice. Last time I managed to burn in Linux I felt like I had faced a buggblatter beast while wigging out on pan galactic gargle blasters... was not a fun experience and it was never very user friendly. 

Have not really tested battery Life yet... spend most of my time plugged in if at all possible. The 9 Cell primaries I use give me better than 3 hours.... better than 4 with light use. If I can get around 3 I will be happy as battery power normally just has to get me through a meeting before getting plugged back in.

All in all... if you get the Intel wireless card this would make an excellent linux system by default. Still not exactly a newbie experience in my book. But its getting closer.

---

### Post by ShaneR on 2007-04-30
I just put Feisty on my Dell i6400 today.  

Thanks to a script that a user has posted in the forums (forget the users name), everything is running great-- wireless, beryl on an ATi x1400, etc etc all is fine.  Without that script, I would have not installed Ubuntu and looked elsewhere for a Linux "fix".

in fact, this is my main complaint about Linux: wheather it be on a desktop or  laptop, installation and configuration is far from user and newbie friendly.  Yes, on some systems everything is smooth, but more often than not (in my experience), it's a headache.   i've owned various systems over the years and have tried many distros, I've never had a smooth experience with any of them.  

That said, once it is running, ain't nothin to complain about :)

---

### Post by freshman on 2007-05-01
Have 7.04 running on Thinkpad 600E (upgraded to 448 Mb RAM and 40 Gb HDD).
Works smooth and fast. 
Still can't get sound working. Also WLAN does not work after waiking up from suspend

---

### Post by kdragon on 2007-05-01
my toshiba M100 running Ubuntu 7.04 

although my wireless card is intel,it cant connect to access point,just 1 time 3 weeks ago,now i have to use windows to surf web.

In general,ubuntu work well, no virus,smooth,stable

but it cant suit my general task: internet

---

### Post by Guranic on 2007-05-07
Asus A6K laptop running FeistyFawn
3000+ Sempron Mobile
512 mb ram
nVidia geForce go 6800

Generally my laptop is running pretty ok, after installation I got wireless network working with fwcutter from repos and now only piece of hardware without support is integrated webcam. Wireless is still bit buggy, but everything else is really stable and running fast. Gnome and Compiz are running smooth&fast and they look amazing! Vista users are so envious.. Keep up the good work Ubuntu teams!!

---

### Post by Kunstar on 2007-05-07
I have a Novatech (UK) laptop, its fairly generic, you can get one quite cheap with or without an operating system preloaded. It has 1.4GHz Celeron, 512MB of RAM, 60GB Hard Drive, Intel Graphics. 

I first installed Edgy and it ran with no problems. I upgraded to Fiesty and have also had no problems. The resolution was stuck at 1028x768 but that got quickly sorted out when i installed the 915resolution drivers from the repositories. I've had no slow downs or issues with Linux which is a relief because I'm a total newbie. Not bad for a laptop that cost less than £500.

---

### Post by timpino on 2007-05-07
I have an Inspiron 8200. P4M 1.7GHz 512MB RAM and a 64MB Geforce 440Go, Feistys nvidia drivers install does not work, closing the lid kills the laptop, standby kills the laptop, hibernate kills the laptop, klicking menus take ~2 seconds to render, Feisty couldn't find any Operating systems to load documents from while XP was installed to begin with. This is a laptop atleast 5 years old and I can't close the lid, very VERY BAD!

---

### Post by PhatStreet on 2007-05-07
> **timpino said:**
> 64MB Geforce 440Go, klicking menus take ~2 seconds to render, Isn't that an integrated card? In my experience their performance will be utter rubbish unless you install a driver for them. Just a guess.

---

### Post by Cruithne on 2007-05-07
I'm about three hours into it so far. It's a lot easier than I expected. I have a few teething problems such as no headphones and no WiFI, but I'll get round that soon enough.
Man, why didn't I do this sooner?
:confused:

---

### Post by timpino on 2007-05-07
> **PhatStreet said:**
> Isn't that an integrated card? In my experience their performance will be utter rubbish unless you install a driver for them. Just a guess.

It's not an integrated card, and Feisty won't install the nvidia driver for it. Btw I have the same utter rubish performance on my desktop with a 6600GT so I don't think it's the adapters fault...

I could live with poor performance but not being able to close the lid is a stopper for me.

---

### Post by kretara on 2007-05-09
I have an IBM ThinkPad x24 (1.13Ghz, 640MB, 80GB with Orinoco wireless card).
Everything worked under 6.10.  Totally stable and a pleasure to use.

I upgraded to 7 and have run into some issues (none too serious).   
1.  closing the LCD no longer suspends the computer
2.  none of the function keys work
3.  the wifi card no longer auto connects to my network on startup/wake from suspend or hibernate.  I have to manually reconnect which ALWAYS fails the first time.  But will usually connect the second time.

I'm not certain that I will stay with 7.  It just does not seem as ready for prime time as 6.10.
Regardless, I feel that if I did a clean install that some of the issues above would disappear.

---

### Post by Bagster on 2007-05-09
I just bought a dell 640m. Feisty almost passed the "just Works(TM)" test.
It installed fine, everything worked, including all the function keys, the media launch keys, wifi, sleep and hibernate straight out of the box. The only point it failed on was the screen resolution. By default the resolution was wrong and i needed to install the 915 resolution hack.  So 9/10 there. It was a shame about the resolution though. 

I still haven't tested the bluetooth yet, but I live in hope :P

---

### Post by digitalramble on 2007-05-11
I've got a three or four year old laptop from Gateway, the 200X series which seems to have been long since discontinued?  Dunno...but it's a lovely lightweight thing.  I've been using Ubuntu on it since Hoary Hedgehog.  It's worked like a charm, the only issues have been wireless (minor, mostly since I've no problems with using iwconfig to beat it into submission, but the network-manager module works very well now) and hibernate.

---

### Post by steevols on 2007-05-24
I installed Ubuntu on a Toshiba 2435 Sat. that I bought on eBay about 4 months ago. Everything went fine except for one issue: the graphics card does not work properly (NVidia GeForce4 420 Go). I had to tinker with EDID settings and swap around between drivers to get it working properly. I'm still not sure how I got everything working, but it is...

---

### Post by joshuag86 on 2007-06-01
installed feisty on a Toshiba Satelite p100. i had some early problems with "slight overheating" of the video card (around 146 degrees cecius), and no sound. Patched the dsdt using the guide supplied on ubuntu forums and now everything is sweet. wireless worked out of the box, as did the   5 in 1 card reader but the fingerprint reader does not work and havent figured that one out. yet.
all in all works well with a few minor adjustments.

---

### Post by MOS95B on 2007-06-01
IBM/Lenovo Thinkpad R51 - Flawless so far.   Beryl didn't work, but that's not Ubuntu's fault, it's ATI's.   Wireless, sound, everything was detected and worked on this release and the last one I tried.

---

### Post by cypresstwist on 2007-06-01
Dell Latitude D850. Everything works perfectly, from wireless to the internal modem.

---

### Post by shearn89 on 2007-06-01
I got passed a ridiculously old laptop from my sister, who got it from our mum beforehand. It use to (barely) run WindozeME, so i stripped that off and put Ubuntu (5.04? i think) on it, and apart from a little tinkering to get it to boot [ACPI module probs], it works fine. It was REALLY old - 640Mhz, 64Mb RAM, 10GB hd. I put some more RAM in it, so its now 512, but the processor's the same, and ubuntu runs perfectly! Unless i'm running loads of programs all at the same time, its fine. And given that my school uses a citrix network for users to connect to and use, its perfectly adequate for the job....
Hopefully i'll get a new laptop soon, so i can put ubuntu on that and have it run ridiculously fast!

---

### Post by matheuu on 2007-06-04
I have a Toshiba A200 Satellite Laptop. The sound doesnt work.... at all..well I have a speaker icon and it detects my card...but no sound... It is amazing how much you miss your sound. Thinking of getting rid of feisty....

---

### Post by laxmanb on 2007-06-04
Ubuntu doesn't support my ATi Mobility Radeon GPU. So I can't start/install it...

so back to Vista Home Premium...

---

### Post by misfitpierce on 2007-06-04
Ive got a 2yr old compaq... Little less than 2 years actually and broadcom wireless. Overall once I got firmware for wireless card its been greater than great :)

---

### Post by ButteBlues on 2007-06-04
> **laxmanb said:**
> Ubuntu doesn't support my ATi Mobility Radeon GPU. So I can't start/install it...

so back to Vista Home Premium...
Change the display driver to vesa, the safe fallback for non-supported cards. ;)

---

### Post by misfitpierce on 2007-06-04
> **laxmanb said:**
> Ubuntu doesn't support my ATi Mobility Radeon GPU. So I can't start/install it...

so back to Vista Home Premium...

Back to DRM and no privacy... ;)

---

### Post by init1 on 2007-06-04
I have had very few problems with ubuntu on my laptop. I couldn't get edgy to recognize my wireless card, though. I think it might be better in feisty.

---

### Post by bishop9226 on 2007-06-04
took me 2 tries to get wifi on e1505, now it works perfectly.  everything else worked right away, beryl, flash player, etc...

seems the x86 is better than the amd version

---

### Post by darksider415 on 2007-06-23
My experience with my Toshiba Satellite A105-S4002 has been perfect, except for my brightness controls not working before I installed a BIOS update during my experiment with Vista. (Lasted two hours before I got irritated and went back to my previous Kubuntu-only setup)  Apparently the lack of brightness control in Kubuntu was due to the Phoenix BIOS, but it works now.. 

However, my wireless worked perfectly, as did my graphics card. (Intel PRO/Wireless 3945 wireless and Intel 950 graphics) No major issues, nothing doesn't work except the TI media card reader, but I don't use it anyway. I haven't tested the ExpressCard slot, but the PC Card does work perfectly.

---

### Post by karachuonyo on 2007-07-28
> **PatrickMay16 said:**
> Hello everyone. Let's share our experiences with Ubuntu on laptops.

For me, my laptop is an old IBM thinkpad T22 which I bought on ebay in October 2006. I estimate that it dates to around 2001. I installed Ubuntu Dapper on it.

First off there was a severe problem with the video; the laptop would crash when X started. After some forum searching, I found that adding some lines to Xorg.conf would fix this problem. After that, it worked pretty much perfectly. Also, I bought a PCMCIA wireless card off ebay; a Safecom SWLCT-54125, which uses the Texas Instruments ACX111 chipset. It worked right out of the box with ubuntu; I just put it in, booted the laptop, configured it using GNOME's network config tool, and then I could use the wireless network. 
This laptop has a 900MHZ Pentium III and 256MB RAM, and the performance of ubuntu (GNOME desktop) on it is good. Even so, I did disable unused services and trim things down a bit to speed things up. Heh! I don't think this would be the case with windows vista. 
So Ubuntu on my laptop, apart from a video problem at the beginning, has worked very well.

How about everyone else?
 
I also have an old laptop, acer aspire bought new in 2002. Has feisy on it and works a treat. I also have a safecom pcmcia card (texas instruments acx 111 chipset) and wireless works in WEP security but not WPA. Somehow knetworkmanager or WICD cannot connect but installed WLAN which connects even better then when using windows.
All in all with feisty everything has worked out of box even the keyboard multimedia buttons. Feisy :guitar:

---

### Post by Gargamella on 2007-07-28
I use ubuntu on laptop since dapper and there have been great improvements on hardware since that release.
So very good

---

### Post by Gnomester on 2007-07-28
I have Feisty on my Toshiba Satellite L30 and have put up with the USB ports failing to work after a short amount of time of usage every day since May.:confused:

I like Ubuntu but the USB problem is too much to put up with so I'll be moving back to SuSE very soon.

---

### Post by samb0057 on 2007-07-28
My brother has a Dell Inspiron, 1100 I think, ran the live CD with no problems. You guys should post this stuff on ubuntuhcl.org

---

### Post by bonzodog on 2007-07-28
I just bought an Acer Travelmate 4200 WLMi, with all intel chipsets, and **everything** Just Works.

It only had to install the one driver for the intel 9345 wireless card, but it now works better than with Windows.

I would definitely say that Acer laptops are to be considered for Just Works Linux Laptops, but avoid the ATi ones.

---

### Post by Luinar on 2007-07-28
My main computer at the moment is an Acer Aspire 1362WLMi. Installed Ubuntu a few days back and it is currently up and running more or less perfectly on it; needed to enable the restriced drivers and then fiddle about with the nVidia settings tool to get the the graphics card (GeForce FX Go 5200, 64MB) working at the correct resolution, and needed ndiswrapper to get the wireless card working, but that wasn't too much bother (incidentially it hasn't lost connection once, under Windows this was incredibly flaky). Pretty much the only thing that doesn't work currently is suspend/hibernate, although I haven't gotten around to having a proper look at this yet. Either way, I can live without this if needs be.

Installation was a bit tricky though. The installer on the live disc kept freezing, and the laptop would keep overheating when installing from the alternate installer. Installing the command line system, and then getting the ubuntu-desktop from apt got it up and running fine, though. :-)

---

### Post by Depressed Man on 2007-07-28
I have a Sony VAIO laptop. And I had mostly a positive experience with my laptop. It worked (installed without any problems), it detected even my memory card reader (though oddly it can't read anything my Canon A620 takes a picture or records without hooking up my camera). But it does read memory cards writen from a Sony camera >.>

And it didn't detect my built in camera (though I got it working after searching a bit). But it did detect my built in microphone! 

And after a while I got suspend working with help fully. :)

---

### Post by Redrazor39 on 2008-01-21
I just need my built-in webcam and microphone and my built-in fingerprint scanner to work on my Vaio VGN-SZ430N.


I wish a dev would hurry up and add this...

---

### Post by init1 on 2008-01-21
> **init1 said:**
> I have had very few problems with ubuntu on my laptop. I couldn't get edgy to recognize my wireless card, though. I think it might be better in feisty.
Wireless doesn't work in Feisty, nor in Gutsy. I don't really worry about it though since 99% of the time I have an ethernet connection.

---

### Post by Mose250 on 2008-01-22
I have a couple-of-year-old Compaq Presario V2000, and Gutsy is the first Linux release that has pretty much become my everyday desktop.  Full Compiz effects, even despite the computer's age, and slick install.  I love easy shortcuts for shutting down my computer at night / turning the monitor off, as I like to listen to podcasts as I go to sleep (it's like a sleep timer).  Wireless has been better since I installed wicd, but I think sometimes that the signal strength isn't as good as it is in XP.  I'm dual-booting, and the NTFS support has been flawless.  Amarok handles my iPod and music needs quite well (with a little tweaking), and I love Tomboy, etc.  I got slingplayer up and running under wine, and there's been no looking back.  

Some minor issues have been:[LIST][LIST]
[*]Wireless Support
[*]Hibernate / suspend - although the shutdown/bootup process is quick enough that I don't really need it, it would be nice to have.  I haven't tried it in a while, but it was  screwed up on initial install
[*]Printer support - my Lexmark Z730 seems to have no chance of working, (but on the other hand, the detection and install of a networked Dell M5200 was the smoothest printer setup I've seen in any OS)
[*]Tracker doesn't want to index my NTFS partition without trouble
[*]I've had some issues with trying to plug in a monitor and go dual-screen
[/LIST]
[/LIST]

All in all, it's been great!  Looking forward to 8.04 (and amarok 2)

---

### Post by ddrplayer512 on 2008-01-22
Sound does not work at all with my Compaq Presario v3020us laptop. The wi-fi worked out of the box. Sound would work in Fedora, however...

---

### Post by chirulais on 2008-01-22
emmm, just the broadcom wireless thing... ._.:confused:

---

### Post by Bossieman on 2008-03-18
I use the latest alpha of Hardy on my Zepto laptop. The Znote 6224W works like a charm. Sound, Wifi, 3-1 cardreader, Bluetooth, Hibernate a.s.o. works straight out of the box. Only had to use restricted manager to download Nvidia drivers.

---

### Post by derekr44 on 2008-03-20
I never was able to get the nVidia driver working on my laptop properly until I went to Arch and found out the problem.  The Toshiba Satellite series from a few years ago had a problem with the way the max screen resolution was embedded, forcing the resolution to 800x600 on proprietary drivers.  I had to get in there and use a custom EDID and change my xorg.conf file to use the custom changes.

Now it runs great with Arch!

---

### Post by Chipter on 2008-03-20
I have a Toshiba A100 laptop, and i've been running LinuxMint Daryna (exclusively) since last November and it's running fine.
I can't use all the Compiz effects, but I don't really want to run them all anyway.

---

### Post by gasparov on 2008-03-21
7.04 was fine and was fine updating to 7.10 too
7.10 fresh install was a disaster, solved for the most but still can't hibernate

P.S. a laptop installation working doesn't mean "the wireless and nvidia card work"

---

### Post by drascus on 2008-03-21
wow man good show. Makes me happy to know that my lappy hardware will still be extendible in the future. So I always use a laptop I have never had a desktop. I started out with a compaq presario v2000 with an ATI chipset. That thing was pretty incompatible. It took me forever to figure out how to get the dang wireless card to work with ndiswrapper in dapper. Back in the day before restricted drivers managers and such. Then eventually I got tired of tweaking and the fact that I could never get compiz to work fine. I looked at a future of slower and slower speed with it. So I opted for a new laptop. Because of my love of Ubuntu I bought a Zareason who preinstalls. They really lived up to their motto "building linux hardware so you don't have to" Now everything just works fine and I have ran a few live cd's from other distros and they all worked out of box on this as well. So I have found my computer company pretty much sticking with them for all my needs in the future.

---

### Post by ninty9notout on 2008-03-22
> **po0f said:**
> PatrickMay16,

I've a T22 as well.  Ubuntu works perfectly on it (as perfect as a 900Mhz P3 can make it).  :)

No wireless, but I don't think that'll be an issue when it does come up.

I have s sony vaio ar51j. I use xubuntu gutsy on it and wireless works just fine on mine. I do have one problem though.

I have xubuntu installed on my USB pen and i have vista on my laptop. I load xubuntu of my USB pen. However, I have a problem getting into Vista without having the USB pen plugged in. Any suggestions?

Btw, I only have Vista because I have to use Adobe Flash for my coursework otherwise I would have already replaced it with Linux.

---

### Post by kamaboko on 2008-03-22
My experience had been very good until recently.  For some reason my laptop (vostro 1400) would freeze constantly.  This happened with Linux Mint, Debian, of course Ubuntu, and several other distros based on Debian.  There's something in a recent update that my laptop simple does not like.

---

### Post by Lee83 on 2008-11-02
as up to now my experiences have been promising,im using a dell inspiron 6400 which has seen more linux distros than ive had hot dinners,everything from DSL to the last three fedora distros,recently installed ubuntu 8.10 (intrepid maybe memory doesnt recall) but had a load issue after log in screen with it hanging after login sound,currently using hardy and it works a treat,some minor issues but nothing major like icons becoming bunched together after running emulators but i think its a configuration problem as opposed to an OS problem,couldnt imagine ever goin back to windows,purely for the fun of learning a new distro basically :) and as a bonus all add ons (web cams,bluetooth adaptor etc) work straight out of the box...brilliant.

---

### Post by N_Nick on 2008-11-02
> **Kateikyoushi said:**
> I have a Vaio X505 everything works fine even wireless but I won't put ubuntu on laptops because of the lack and quality of wireless tools.

+1

One of the main drawbacks of using ubuntu or linux in general on laptops. I just installed interpid on my MacBook Pro and let me tell you wifi is being a pain in the *** :mad:

---

### Post by borfil on 2008-11-02
I have an old (7yr) Laptop a Compaq Presario700 with an AMD Athlon D 1.3 CPU. She works perfect on all programs exept when I connect my Dlink DWL-G1222 USB wireless Iadpter. I recognize it, it can sniff the network but it will not transmit. Thats right of the box. I been searching for driver for it but all I just found was for the older model DWL-122 I'm going to try them and see, My camara well that is also the same. It recognize it but it will not turn it on. But I use the laptop as a secondary pc and for what I need her she works great. she connects much faster to the net, it runs faster and it is 2000% much more stable than MS XP or Vista. I dont worry to much for the connection because I connect via cable DSL but if I want to take her with me I can connect other than via phone. My other Laptop do not accept linux, to many propetary thing on her and only MS WINDOs. well win some lose some.
:confused::)

---

### Post by OttifantSir on 2008-12-10
I had an OLD laptop once [Amazed at OLD laptop]("http://ubuntuforums.org/showthread.php?t=320419"), and now I'm using a Dell Inspiron 9400. Been loading Linux on it since 7.04

I had to use ndiswrapper then, because of a Broadcom wireless chip, but it got done in about five minutes (less time than it took to install the drivers in Windows, reboot, figure out the settings and actually connect). Since 7.10, I can use Jockey (or Restricted Drivers Manager)

Including 7.10, I also had to install 915resolution to get 1440x900. 

The Ricoh card reader didn't work at all before sometime after the release of 7.10, but is problem-free now.

Only other thing to do was to tick off LFE (subwoofer) in volume control and unmute it (all prior and subsequent versions, including 8.10).

The real problem now is PEBCAK. I try to do too much at once without always understanding what it is I am doing, slavically following instructions online because it MIGHT work. Had to do quite a few reinstalls because of this, because I don't always remember what I did, and when I do, the steps I take to backtrack it doesn't always work. The latest occurence of PEBCAK: I managed to disable my LFE completely with no idea on how to get it back.

All in all, I'd say Ubuntu has been fairly painless on this one, and probably even better than painless on the OLD one (which I got for free and sold online for about $40 installed with Edgy Eft. On the second page of that thread is the specs, which I listed online, told what it could and COULDN'T do quite clearly, and still got a nice buck in return)

I love Ubuntu. I just wish more of my friends would see the benefit of it, and some of the other aspects of FLOSS. Like, no DRM. My friends actually endorse and argue for it. Really, really sad.

---

### Post by Changturkey on 2008-12-10
Hopefully Jaunty makes power management really good.

---

### Post by magmon on 2008-12-10
It works perfectly. I did once get very pissed that a file wasnt opening properly, and over reacted by reinstalling vista and setting up a dual boot. It turned out to be the file, not my ubuntu.

---

### Post by zmjjmz on 2008-12-10
My MacBook had a few minor issues, but besides that all of my laptops have worked beautifully with Linux.

---

### Post by mmoses on 2008-12-10
Started with Gutsy dual booting, now on Intrepid, Sony Vaio VGN-FJ270 w/ 320GB SATA HDD and 2GB RAM.  Generally happy, no serious issues.  I have not been able to get the brightness/volume function keys to work but haven't hit that issue very hard.  HDD runs hot while I try to find a good balance between constant load cycling vice constantly on.  Battery life under Ubuntu is abysmal, but I am almost always on AC so it's another low priority for me.

Finally completely Windows free!

---

### Post by Grant A. on 2008-12-10
I have an old Toshiba Satellite with 526MB RAM, an Intel chipset, and a centrino processor. I haven't had any problems whatsoever, even with wireless.

---

### Post by magreenberg on 2009-07-08
I installed Ubuntu 8.10 on my old Thinkpad A20M.  It was manufactured in Sept, 2000 and came with Windows 2000 pre-installed.  It has a Pentium III 700Mhz processor and 512 MB of RAM.
 
Most of the time it works fine.  If for some reason it doesn't shut down normally I have to start in recovery mode to get it back.  
 
The touchpad and trackpoint devices don't work.  I can't find specfic drivers but I did find a couple of articles today on thinkwiki.org that I will read on configuring them.  The Logictec Mouse works fine.
 
It doesn't have a on-board NIC so I had to use an older Linksys wireless PC card that I had, model WPC11, 802.11a.  Linksys doesn't provide Linux drivers for their newer faster cards, 802.11g.
 
Please let me know if anyone has any thoughts on these issues.
 
Thanks!

---

### Post by wcutrombonekid on 2009-07-08
I have a Gateway E-475m and so far things have been pretty flawless.  The biggest problem I had with the laptop itself is that it only had an 80 GB hdd so i switched it out with a newer 320 GB one and moved windows over to it and have a 27 GB-ish partition that Ubuntu is on.  So far things have been spectacular.  I started with 9.04 and ext4 and so far have had no problems.  The biggest thing with ubuntu is that i have one of the blacklisted graphics cards, so i can't really play any games.  But as far as daily usage goes i love it.

---

### Post by sraghav on 2009-10-01
I put Jaunty on a new Compaq CQ40 a few months ago. The HP helpline in India assured me I needed to buy Windows (unless I bought some other costlier model) but luckily I ignored their advice. :) It has generally been a fairly smooth ride. I needed to enable the proprietary driver for wireless, which then has worked fine. It needed some effort to get sound working, but these forums helped take care of that. Both suspend and hibernate work fine too. 

The only thing I have not yet sorted out is power management. The laptop runs at full power all through - the default menus in System > Preferences > Power Management seem rather basic - I was wondering if anyone knows a way to get more advanced power management working (Like my Lenovo T400 office laptop on WinXP), so that I can extend battery life beyond the 2 hrs or so that I currently get. :confused:

Would appreciate any inputs on this. Thanks.

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-01
My laptop runs on full power too
I installed cpufrequtils, but I haven't measured if that helped

---

### Post by random turnip on 2009-10-01
Lack of wireless drivers made it unpleasant...

...until 9.04.  Now i love it.

---

### Post by Crunchy the Headcrab on 2009-10-01
Time to install < 30 minutes.  Wireless works ootb.  Audio minus my headphone jack works ootb.  Time to config my headphone jack < 1 minute.  Appearance, better than vista/7 now that I have a sweet theme.  Uses less ram, cpu, better battery life (yup, I didn't believe it either).

So basically the only thing that Windows has that I miss is a few commercial apps (games).

All in all I run Linux/Ubuntu on my lappy full time.

---

### Post by Rob Maddison on 2009-10-03
Toshiba Satellite L300 29w which is running Jaunty pretty much as good as Vista straight out of the box.

The only issue I have is a recurring issue with screen resolution at start up - it reverts to 4:3 on most start ups, sometimes retaining the 16:10 that works best. Trying to sort it out without shouting for help too many times!

---

