---
title: "Ubuntu 7,10 - worst experience yet"
date: 2007-10-20
forum: Testimonials &amp; Experiences
---

### Post by Sockerdrickan on 2007-10-20
Hi I have to date used
6.06
6.10
7.04
7.10

This is how I would rate them from best to worst

7.04
6.06
6.10
7.10

It's interesting to see that the .10 versions "suck more"

My problem is I'm getting 640x480 mode only, with proprietary nVidia drivers 100.14.19

I installed them on my own first, after every reboot I got welcomed by the so called bullet-proof X layer, it told me a lot of stuff which was irrelevant and I could choose 640x480 or 800x600. Both of these modes where out of sync on my screen.(Congrats bullet proof X team)

Then I installed the driver on my own and it worked. But I'm only getting 640x480.

Time for fallback to 7.04 if no how to's are available!

---

### Post by samuelrash on 2007-10-20
:confused:Tried an update from to 7.10 last night. System crashed in first minute of install. Any way of recovering? Newbie. Thanks

---

### Post by nlindberg877 on 2007-10-20
I'd have to agree... I'm new to Ubuntu, but I have used 6.10 and 7.04 as well as 7.10, which I just installed on both my Laptop and Desktop... I'm having driver issues, codec issues, and for some reason, I need to run my processor only on a single core, rather than dual core, or else 7.10 wont even load. I'm thinking about falling back to 7.04 for the time being.

---

### Post by TheodoreWard on 2007-10-20
I have also been having a lot more problems than usual. One of the main issues though was: I keep my home folder on a separate partition and apparently some of my previous settings were incompatible with the newly installed root.

If your home is on its own partition, and you didn't reformat it, start the terminal do this:

cd ~
mkdir tempsettings
mv .* tempsettings
sudo reboot

All of your previous application settings will be gone and hopefully some of your issues will be fixed. You can then restore some of your settings if needed such as:
mv ~/tempsettings/.evolution  ~ to restore your email settings.

To see what you backed up type: ls -al ~/tempsettings/

---

### Post by antoniuk on 2007-10-20
Don't blame Ubuntu totally. Overall they have made many improvements.

The big problem is that xorg is an application still living in the past and is very crappy in a desktop replacement environment.

They need to scrap this antiquated way of thinking and make a modern video and input control program. They need to separate the keyboard and mouse into their own control and make the video more automated and work with video vendors or allow said vendors to do their thing and stop being so demanding that every thing be opensource

All my problems with Ubuntu can be traced back to Xorg

I know I could go back to windows but I love Linux, I just do not see why it can not catch up to the other two big OSes in the video department.

---

### Post by TheodoreWard on 2007-10-20
> **Tux0r said:**
> Hi I have to date used

My problem is I'm getting 640x480 mode only, with proprietary nVidia drivers 100.14.19

I installed them on my own first, after every reboot I got welcomed by the so called bullet-proof X layer, it told me a lot of stuff which was irrelevant and I could choose 640x480 or 800x600. Both of these modes where out of sync on my screen.(Congrats bullet proof X team)

Then I installed the driver on my own and it worked. But I'm only getting 640x480.

Time for fallback to 7.04 if no how to's are available!

I was having these issues with the ATI fglrx driver. There are two possible solutions:
If you look in /etc/X11 you will see backup xorg.conf files (xorg.conf.1, .2 etc...) you can copy one of these that actually worked over the xorg.conf file and reboot.
What I did was go to restricted driver manager, turn off the restricted video driver, wait for it to uninstall, then turn it back on and let it reconfigure everything again.

---

### Post by mithbuntu on 2007-10-20
> **antoniuk said:**
> 

All my problems with Ubuntu can be traced back to Xorg.

I couldn't agree with more.  7.10 is killing me on the inside.

Is it possible to revert to 7.04 without messing anything up? :(

---

### Post by mithbuntu on 2007-10-20
> **TheodoreWard said:**
> I was having these issues with the ATI fglrx driver. There are two possible solutions:
If you look in /etc/X11 you will see backup xorg.conf files (xorg.conf.1, .2 etc...) you can copy one of these that actually worked over the xorg.conf file and reboot.
What I did was go to restricted driver manager, turn off the restricted video driver, wait for it to uninstall, then turn it back on and let it reconfigure everything again.

I've done this about 30 times, but still to no avail.   ANytime I run fglrxinfo to even check if it has worked my computer crashes.

---

### Post by 127.0.0.1 on 2007-10-20
> **mithbuntu said:**
> I couldn't agree with more.  7.10 is killing me on the inside.

Is it possible to revert to 7.04 without messing anything up? :(

back up data, do a clean install. I am about ready to do that my self. 

as far as drivers and hardware support gose, i am fine no problems with hardware. however i am having codec, plug-in, and software support trouble. I cant find much of the software that i used in fesity for gibbion. might revert back to festiy :( but non the less, i will give 7.10 a chance.

---

### Post by Jermski on 2007-10-20
> **Tux0r said:**
> ...

My problem is I'm getting 640x480 mode only, with proprietary nVidia drivers 100.14.19

I installed them on my own first, after every reboot I got welcomed by the so called bullet-proof X layer, it told me a lot of stuff which was irrelevant and I could choose 640x480 or 800x600. Both of these modes where out of sync on my screen.(Congrats bullet proof X team)

Then I installed the driver on my own and it worked. But I'm only getting 640x480.

Time for fallback to 7.04 if no how to's are available!

You'll probably need to alter your X config file to allow other resolutions.

---

### Post by AnthoMacP on 2007-10-20
I actually had similar problems but unlike the OP i've been using ubuntu since 5.04.  I do tend to agree that the *.10 releases seem to be less than perfect, 6.10 for me was unusable because it didn't recognize my external harddrive firmware for both my externals. 
In relation to your problem however I also had a similar problem in terms of 640x480 mode except in bulletproof-x where it allowed me to up my res to 1024x768. What did the trick for me was playing with different drivers, there are three in synaptic i'm aware of, new old and legacy, mine happens to work with new but not old or legacy so you might want to try that, also there's a few different methods of changing screen resolutions and monitor settings. In the Screens and Graphics tab try and change the monitor you're using. Mine wasnt detected and was giving me a very low res options as a result but when i set it to a generic 1400x1050 LCD display (not the manufacturer ironically, that didn't work) it fixed my resolution problems after i got the driver to work.
Lets hope april's LTS release is better than this one, It was quite a headache to setup.

---

### Post by jviscosi on 2007-10-20
> **Tux0r said:**
> My problem is I'm getting 640x480 mode only, with proprietary nVidia drivers 100.14.19

I got this too.  After I installed the latest nVidia drivers with envy (the version from the website, not from the repos) and added a 1680x1050 mode to xorg.conf, I used gnome-control-center to change my monitor from "generic" to "widescreen 1680x1050" and was then able to pick the resolution I wanted.

---

### Post by Sockerdrickan on 2007-10-20
Gonna install 7.04 now :)

---

### Post by Mateo on 2007-10-20
I agree.  I used 7.04 Feisty before it was released and decided I'd never use a pre-release again.  But even then, I had fewer problem with Feisty pre-release than with Gutsy "final".

I know most of these problem will eventually get worked out, but some of them are unexceptable to ever happen in a final release.

---

### Post by Sockerdrickan on 2007-10-20
The 8.04 LTS will be really stable if you ask me. Maybe like 7.10 with new gnome, Firefox 3.0 and new kernel. Not any real new stuff maybe.

---

### Post by FredB on 2007-10-20
> **Tux0r said:**
> The 8.04 LTS will be really stable if you ask me. Maybe like 7.10 with new gnome, Firefox 3.0 and new kernel. Not any real new stuff maybe.

I just wonder how you can find that gutsy is - sorry - a crappy version ? Did you upgrade a really tweaked feisty ?

Here is my hardware, not really old, not really new too. And **NO PROBLEMS** at all with Gutsy AMD64 version (installed since beta).

- AMD Sempron 3100+ (K8 Core - 64 bits)
- 1.5 Gb DDR 400
- GeForce FX 5200 + Nvidia drivers (last version 100.14.19 or something like that)
- DVD / CD burner
- HDD 160 Gb
- Printer HP Deskjet 3840 USB
- Motherboard GigaByte VIA K8VM800M
- Epson Perfection 1250 Scanner
- Flat screen Packard bell 17 inch.

I simply use the tool proposed for my graphic card, and all works smoothly.

Please explain why you're running into such problems !

---

### Post by FredB on 2007-10-20
> **Tux0r said:**
> The 8.04 LTS will be really stable if you ask me. Maybe like 7.10 with new gnome, Firefox 3.0 and new kernel. Not any real new stuff maybe.

Gnome ? 2.22.0 or 2.22.1.

Firefox 3 ? Let's Gran Paradiso alpha9 be released before.

For your info : Every single version since dapper was stable on my computers...

---

### Post by dietrying on 2007-10-20
l like ubuntu but i can understand why some people are disappointed about gutsy gibbon. I think there are much good new ideas and features in this release but some of these features seem to be not ready for me....

if i look through the forum posts, i see much treads about problems with configuring the x-server.
Tested Gutsy on only 4 machines i can't appraise about the screen configuration tool in generally, but it behaved very strange on that 4 computers. on 3 Computers i had problems with resulution configuration- for example i was able to select the correct screen (1280x1024) but then only was able to have resolutions to 1024x768..?!? or i wanted to switch to nv driver and the program didn't save it.....for this 4 Computers this "tool" only brought difficulties. I was only able to solve this by reconfiguring the xserver manually.

another strange behavior is the abscence of TTY terminals if i'm using the NVIDIA driver...and i'm not the only one with these problems. I don't want to blame ubuntu because in the end they HAVE done a good job! I only think that new technical improvements and graphical frontends should only be used if they work really really good! Else a configuration of graphic-modes by console is much less stressful......

---

### Post by stinkypudding on 2007-10-21
One huge problem is the new nvidia driver has a major issue with widescreen resolutions.  This is all over the boards.  I can't get 720p resolution on my HDTV.   Tried envy, rolling back to the previous driver, the GUI, countless updates to my xorg config.  Nothing seems to work.   It's frustrating, under feisty I had mythtv running in 720p resolution.   I can't believe Gutsy is this messed up.

---

### Post by Cyberbian on 2007-10-21
Just in case you guys haven't seen this. Here is the solution to the small video mode issue.

[http://psubuntu.com/forum/viewtopic.php?t=13]("http://psubuntu.com/forum/viewtopic.php?t=13")

---

### Post by stinkypudding on 2007-10-21
I just wonder how you can find that gutsy is - sorry - a crappy version ? Did you upgrade a really tweaked feisty ?

Here is my hardware, not really old, not really new too. And NO PROBLEMS at all with Gutsy AMD64 version (installed since beta).

- AMD Sempron 3100+ (K8 Core - 64 bits)
- 1.5 Gb DDR 400
- GeForce FX 5200 + Nvidia drivers (last version 100.14.19 or something like that)
- DVD / CD burner
- HDD 160 Gb
- Printer HP Deskjet 3840 USB
- Motherboard GigaByte VIA K8VM800M
- Epson Perfection 1250 Scanner
- Flat screen Packard bell 17 inch.

I simply use the tool proposed for my graphic card, and all works smoothly.

Please explain why you're running into such problems !

You're not trying to configure a 1280x720 resolution for your monitor.   I can do that in feisty, haven't been able to yet in Gutsy.   I hope someone posts a fix to this problem soon.

---

### Post by WallRunner on 2007-10-21
[COLOR=DarkGreen][B]Well, I'm having problems too, but much worse, my monitor (Sampo Alphascan 712), will not come on when using the gnome interface, (my laptops backlight is out so I have to have a external monitor), I can use the TTY consoles just fine, and everything works up until I get to the login screen, I have tried installing drivers, used "sudo dpkg-reconfigure xserver-xorg", but nothing has helped.

Does anyone know how to fix this I can barely use the laptop screen, but I can use it if I need to.

From,
Chris.
[/B][/COLOR]

---

### Post by Sockerdrickan on 2007-10-21
Step one: Install Ubuntu 7.04

---

### Post by Rob500 on 2007-10-21
Setting up desktop effects in Kubuntu 7.10 was an absolute nightmare compared with 7.04.

Apart from that, everything is good, I like the new tickless kernel, it really helps with laptop battery life and Dolphin is a lot better than Konqueror for file management.

Oddly, Gutsy works a lot better after upgrading from Feisty than it did when I did a clean install of Gutsy :confused:

---

### Post by wolfen69 on 2007-10-21
i too, am having similar problems with the new nvidia drivers and codecs. luckily i have 5 hard drives so i can run gutsy and feisty. but im only going to boot into gutsy to see if there are any updates that will fix things. i think this release will scare more people away from ubuntu/linux than convert.

Bad Gutsy.

---

### Post by AnthoMacP on 2007-10-21
> **Tux0r said:**
> Step one: Install Ubuntu 7.04

I did the same thing today but changed the repo's to gutsy so i'm running a sort of hybrid between the two now, it's a little strange actually, my wireless works like it did in fiesty and my screen problems are non-existent but i've got updated apps, old kernel though but i'm more than fine with that till the LTS. I just find that this distro wasn't tested enough on enough computers to be honest because the screen/graphics detector doesn't work properly for a lot of people. I still love ubuntu and give it a lot of credit considering not every machine is built specifically for the distro and it can run on everything with some tweaking but I felt with this distro the increased automation made things harder to fix when the automation failed. I think with time and improvements things will be fine but I find with change there's always this sort of thing. The ideas are amazing, the implementation is just not 100% yet.

---

### Post by InsertNameHere on 2007-10-21
After seeing all that I think im one of the lucky ones......

I only had a minor sound problem that I fixed.... from advice on the forums..

---

### Post by euthyfro on 2007-10-21
for me it's that when i change the x config it just reverts back to the craptacular 800x600 thing if i try to use nvidia drivers.

---

### Post by Sockerdrickan on 2007-10-22
That's probably what I have yes.

---

### Post by RebounD11 on 2007-10-22
> It's interesting to see that the .10 versions "suck more"

I think it's probably cause they're developed in the summer and vacationing isn't all that productive :D

PS: I don't mean to offend the developers - they're doing a great job, they're only human.

---

### Post by Shin_Gouki2501 on 2007-10-22
This is kind of interesting, is there a statsistic which shows what ubuntu version made user most trouble?
Is there an offical resource or anything like that?

---

### Post by AZzKikR on 2007-10-22
I've been using Ubuntu since Breezy. I upgraded to Gutsy too and it doesn't work too pretty. I've backed up my data and I'll be doing a full re-install tonight. I've done that everytime (upgraded first, then reinstall) and it has worked for me.

And mind you, the developers do a great job. They develop an OS which is free of use, and which actually works. So I can't result to complaining actually. I am very happy with this distro! And well, if Gutsy doesn't work for me, I will use Feisty. No problem.

---

### Post by El Zoido on 2007-10-22
I'm using Gutsy for a couple of days now and of yet I quite like it.
I did have some Problems with the Nvidia drivers, but I could fix it rather fast on my own. Seems more a problem of Nvidia than a problem of Gutsy to me. Anyway the new version is out for less than a week now, so no wonder there are some bugs.
Ok, on other thing: DVD playback in Totem isn't working as it should.
Seems the codecs indeed aren't really perfect yet.
Well, I got VLC for that...

---

### Post by stinkypudding on 2007-10-22
I reinstalled Feisty, and got back my 1280x720p resolution.   Anyone who's interested, this is the relevant part of my xorg config:

Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 150.0
    VertRefresh     28.0 - 150.0
    Option         "DPMS"
    Modeline 	   "1280x720"  74.48  1280 1336 1472 1664  720 721 724 746  -HSync +Vsync

EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600"
    Option	   "ConnectedMonitor" "TV"
    Option	   "UseEDID"	"False"	
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
       SubSection     "Display"
        Depth       24
        Modes      "1280x720" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    Option 	   "TVStandard" "HD720p"
    Option	   "ConnectedMonitor" "TV"
    Option	   "TVOutFormat"	"COMPOSITE"	
    EndSubSection
EndSection

Section "Extensions"
	Option	"Component"	"Enable"
	Option	"Composite"	"Enable"
EndSection


I'm using a 27inch Go Video HDTV, with 6600GT and nvidia-glx drivers.

---

### Post by Sockerdrickan on 2007-10-22
> **RebounD11 said:**
> I think it's probably cause they're developed in the summer and vacationing isn't all that productive :D

PS: I don't mean to offend the developers - they're doing a great job, they're only human.
That's a great theory!

---

### Post by Peter6218 on 2007-10-22
> **samuelrash said:**
> :confused:Tried an update from to 7.10 last night. System crashed in first minute of install. Any way of recovering? Newbie. Thanks

Downloaded and burned CD last night, Tried to install this morning. Forget it !!

Plus it wipes out all your stuff you had with Feisty. That's nuts for just an upgrade.

Back to Feisty !!

---

### Post by kazuya on 2007-10-22
> **Tux0r said:**
> Hi I have to date used
6.06
6.10
7.04
7.10

This is how I would rate them from best to worst

7.04
6.06
6.10
7.10

It's interesting to see that the .10 versions "suck more"

My problem is I'm getting 640x480 mode only, with proprietary nVidia drivers 100.14.19

I installed them on my own first, after every reboot I got welcomed by the so called bullet-proof X layer, it told me a lot of stuff which was irrelevant and I could choose 640x480 or 800x600. Both of these modes where out of sync on my screen.(Congrats bullet proof X team)

Then I installed the driver on my own and it worked. But I'm only getting 640x480.

Time for fallback to 7.04 if no how to's are available!


I feel your pain. I hard similar issue, but my resolution which is not a good one was to install kubuntu-desktop>
Login to kde desktop>
Go to Kde Menu> Settings> Display> Change from the 1024X768 or 800X640 to the appropriate one. There are a lot of good on this release than meets the eye.

Do not give up. I agree that they should have looked at that more carefully.

From gnome> I tried to use Screen Graphics> Select the right reolution and click Apply and Keep settings. - sadly, this does not permanently solve the issue as upon boot-up again. You get the same previous resolution.

---

### Post by Sockerdrickan on 2007-10-22
Yes and that's what I don't get...
Why didn't they fix this? Some people reboot all the time, some reboot every third year...

---

### Post by jviscosi on 2007-10-24
> **Tux0r said:**
> It's interesting to see that the .10 versions "suck more"

I wonder if this is related to the "odd-numbered Star Trek movies suck" theorem.  If we could figure that out, we might unlock the secrets of the universe.

---

### Post by cb474 on 2007-10-24
I also feel like Gutsy has been a step backwards for me from Feisty. I don't see any real improvements in my day to day use and am experiencing a number of problems, including the return of a bug I had in Edgy.

1) I see no improvement in battery life, over Feisty. And some problems (sometimes it gets stuck at a very high discharge rate).
2) Sticky Notes do not disappear when clicking on the desktop. (New bug, not in Feisty).
3) With panel on right side of screen all window buttons only show two dots, "..", unless the panel is at least 30 pixels wide. (New bug, not in Feisty--maybe be Gnome 2.20 related, since I saw this in OpenSuse 10.3 as well.)
4) Font rendering in Firefox terrible, appears not to be antialiased. I switched to Swiftweasel (and tried Firefox, not from Ubuntu repos), but fonts not as good there either as in Ubufox on Feisty.
5) Font rendering gone wacko in OpenOffice. Installed OOo from OOo repos, better, but not as good as Feisty.
6) When running on battery, high pitched noise occurs, unless remove module for USB 1 (rmmod uhci_hcd), which also negatively impacts battery life. This is the return of a bug I had in Edgy, but not Feisty.
7) I have two FAT32 partitions that I'm sharing with XP, on two separate hard drives. When I go to access either of those partitions in Nautilus, the first time after startup, Nautilus takes a long time (10 seconds, I timed it) to show the contents of the partition. This is very annoying. This problem did not exist in Feisty, which only took 1 or 2 seconds to read the file tree on those partitions the first time after startup.

I also had the experience that a clean install (reformatting / and /home partitions) did not work as well as an upgrade from Feisty. I tried the clean install first and was getting weird video problems and crashes right away, before I hardly tweaked anything (as well as after I properly set up everything for my computer). Then I went back to Feisty (from a partition image), did the upgrade, and it's been much more stable. Weird.

Anyhoo. I'm seriously thinking about going back to Feisty. I feel like the Ubuntu developers might do well by adopting more of an "if it ain't broke, don't fix it" policy. I know they work hard and I appreciate that, but sometimes I think things are tweaked to create a new and improved look, that ends up causing problems or just annoying people who liked how things were. I'm interested in improvements to the underlying system and new usability features, but the things that just work fine and look fine already I wish were left more alone.

I also find that with every upgrade there are new bugs introduced (like the Sticky Notes bug) they don't get fixed until the next upgrade. In bug reports, people say it's not important enough to get worked on inbetween upgrades. But then with the next upgrade there's some new set of bugs. So in the long run there are always little things that aren't right. I think it would be worthwhile, instead of putting so much of the development energy into making sure Ubuntu has as much of the latest and greatest possible, to fix the little annoying bugs quickly. I think they create as much of people's impressions of Ubuntu as anything.

---

### Post by Shin_Gouki2501 on 2007-10-25
I ask again?!
Is there any offical Statement or such which shows WHAT ubuntu version did ship with what problems.
And Which ubuntu Version was the one with "least" Problems?

---

### Post by AnthoMacP on 2007-10-25
> **Shin_Gouki2501 said:**
> I ask again?!
Is there any offical Statement or such which shows WHAT ubuntu version did ship with what problems.
And Which ubuntu Version was the one with "least" Problems?

No that data would be pretty hard to generate. launchpad will give you a rough idea of that information but a lot of problems are fairly hardware specific so it's not a general "this doesn't work, period" kind of thing, I usually just judge based on amount of "General Help" topics relating to various broad issues, like right now you see a lot of people asking for graphics hardware help so you know that Gutsy must have some graphics/display issues.

---

### Post by desertboy on 2007-10-25
What can I say I've been using Gutsy since Tribe 2 and I had problems with switch user (Related to compiz) but since about 1 month before the final everything has worked fine including widescreen modes on my monitor.

Using whatever the latest drivers in the restricted manager are, I have a 8800GTS.

---

### Post by ben.15 on 2007-10-25
i recently tried 7.10 worked first boot after update and install
now it doesn't work at all
comes up with text based boot

---

### Post by regeya on 2007-10-25
Oddly enough, I had just the opposite experience this time.  The last couple of upgrades went badly--Feisty went so bad the first time, I switched to Debian Etch for several months--then this past week I upgraded a "problem child" kubuntu feisty system (so called by me, because I've used 3rd-party repos, done some self-backporting, etc.) and mostly everything works.

The only thing really kicking me in the butt other than Compiz (beta-quality software, folks, remember that) is a problem with apt-zip where when I drag my flash drive to work and run fetch-script-wget-leto I get about 98% of packages with a bad md5sum.  Machine at work is an OS X Tiger box so that may be the problem.

Otherwise, things seem to be going quite smoothly.  :)  I'm sorry to hear so many other people are getting kicked in the butt by Gutsy--this is the tune I was singing when Feisty first came out.  :(

---

### Post by Shin_Gouki2501 on 2007-10-26
man its does sounds still FAR too much like jepoardy for me,
if ur luky it works good but if not...
i dislike that somehow.
Ubuntu needs certain quality standards imo.

But i guess Launchpad is a very good place to start with!
Use soem analytics and statistics there combined with the forums should produce some "useable" output.

This is all because i think that the generall situation with linux NOW is not satisfying. Of course there has to be driver support yes. But IMO there should more "stable" developpment, even is this would mean a slow down... hmm maybe i should switch to debian lol

---

### Post by khurrum1990 on 2007-10-26
Ubuntu 7.10 isn't bad at all. When Ubuntu 7.04 came out, I could never get it to work properly on my computer so I tried OpenSuse 10.2 at the time which worked perfectly. Now after 7.10's release everything works great. It just varies from different computers to different computers.

---

### Post by zgoda on 2007-10-27
I tried all releases since 5.04 an all I can say only 6.06 was behaving worse than 7.10 on my laptop. The faults that make me really sick:
 * The CPU never idles, fan is running all the time, battery is exhausted in less than a hour (~3 hours in 7.04). Recharging battery from 0 to full capacity takes ~6 hours (less than 3 hours in 7.04).
 * Closing the laptop lid should result in turning off the LCD. When the lid is opened, mouse cursor jumps from place to place even without any movement of mouse. Nothing helps, I have to reboot to be able to use mouse at all.
 * The new and "improved" font rendering in GNOME (not in Firefox!) makes some fonts look blurry. This has killing effect on my eyes. I see nobody really complaints so I do not expect it will be fixed. Unfortunately, one of the fonts that are diplayed blurry is my preferred Tahoma.

I'm not that distant from going back to 7.04.

---

### Post by cb474 on 2007-10-27
I've gone back to Feisty. Too many annoying little problems in Gutsy (which I outline in a post above). I spent a week trying to solve them. Nothing was really wrong with Feisty for me. And Gutsy is definitely not new and improved for me. I think the issues with font changes in Firefox and OpenOffice, though these were far from my only problems with Gutsy, should be taken more seriously. At the end of the day, most of my time using my laptop is spent looking at text, so how it looks and whether it makes my eyes bug out matters.

---

### Post by gmc on 2007-10-28
As a linux user since '98 (Redhat 5.0) and having used every  version of Ubuntu since 4.10, I really have to say the fresh install of 7.10 has really left me **[COLOR=PaleTurquoise]cold[/COLOR]**.

The number of problems with this release really makes me believe that 7.10 was too rushed and should have been delayed a few extra weeks to ferment before being unleashed to the world.

I'm now considering several options:

1. Rollback to Feisty
2. Move back to Debian
3. Try another distro (and at this point of my frustration, even RPM based is in the running)
4. Go back to Windows (and shoot myself)

I'll look at Hardy when it's released, but I'm done with Gutsy.


Gord

---

### Post by bd@cb8be8510 on 2007-10-28
I _was_ a happy Feisty Ubuntu-user until :cry: I installed Gusty. First of all my wireless-network was down. After reading all the good advices (on another computer, of course) I finally was able to get my wireless network working again
(I needed to download, compile and install a new driver from serialmonkey - How pretty easy is Ubuntu, isn't it?). Solving this problem took me almost a week. A lot of problems regarding the RT2500-drivers were reported during the evaluation of the release-candidate. So why was this kind of crap released after all?

 Secondly.  When I start a spellingscheck, open office crashes.I can't even configure Open Office. You can open the dialog, but as soon as you select a submenu, the system hangs. Nice. I got a pretty workable system with Feisty, now in stead of doing my real job on my computer, I'm browsing the forums to find a solution for open office. 7.10 is my worst experience. 

I'll switch back to Xp. I want to work with my computer, not browsing the forums to find solutions for problems I never had with Feisty. Sorry Ubuntu-people, you made a nice looking car with a very powerful engine, but you forgot to mount proper wheels on this car:(

---

### Post by conehead77 on 2007-10-28
> **bd@cb8be8510 said:**
> 
I'll switch back to Xp. I want to work with my computer, not browsing the forums to find solutions for problems I never had with Feisty. Sorry Ubuntu-people, you made a nice looking car with a very powerful engine, but you forgot to mount proper wheels on this car:(

But why do you switch back to Windows instead od Feisty if it worked for you?
I hear many people saying this, but i really dont understand it.

---

### Post by AnthoMacP on 2007-10-29
> **conehead77 said:**
> But why do you switch back to Windows instead od Feisty if it worked for you?
I hear many people saying this, but i really dont understand it.

I think it has something to do with the fact that Feisty was an on going process to get working just the way they liked, then after gutsy it just gets too frustrating to have to re-do everything in Feisty after the gutsy failure. I know that's how I felt atleast when my gutsy experience was less than stellar. I was really annoyed at the prospect of having to tweak everything all over again.

---

### Post by karellen on 2007-10-30
there's one thing that I particulary don't get: why risking updating to the "latest-and-greatest" (gutsy) when you already have a working and stable system? why? what's the point? too much spare time?...I only update when I have nothing to lose (aka a spare ext3 partition) and I'm curious to see what's all the fuss about...

---

### Post by AnthoMacP on 2007-10-30
> **karellen said:**
> there's one thing that I particularly don't get: why risking updating to the "latest-and-greatest" (gutsy) when you already have a working and stable system? why? what's the point? too much spare time?...I only update when I have nothing to lose (aka a spare ext3 partition) and I'm curious to see what's all the fuss about...
Haha shiny and new. Seriously, you get all the new bells and whistles for your whole operating system. For me it was also part functionality since I was hoping to get dual monitors working w/o having to switch xorg.conf over then reboot every time i want to turn it on but I mean it was as much that as the prospect of having all updated apps, other new things, new kernel. I think that people tend to assume that "new" inherently means "new and improved" unless otherwise indicated.

---

### Post by gregh on 2007-10-30
My experience has easily been the *best* Ubuntu so far.

My (fresh) install went without a hitch and all hardware (and I mean all) worked immediatly after restart.

I have a HP laptop (DV5129), core-duo, Nvidia, 1G, 80G , 15.4" and wireless is the Intel 3945.

I feel for people who have issues, all OS's have problems (go search a leopard or vista forum if you dont believe me) at least you did not have to pay big $$ to find out you have a problem :-)

I would not be too put off, the next release is a LTS so I would ecpect it to be more stable than some  people are reporting with Gutsy.

-Greg

---

### Post by gmc on 2007-10-31
> **karellen said:**
> there's one thing that I particulary don't get: why risking updating to the "latest-and-greatest" (gutsy) when you already have a working and stable system? why? what's the point? too much spare time?...I only update when I have nothing to lose (aka a spare ext3 partition) and I'm curious to see what's all the fuss about...

Four words: "improved support for hardware".

If the next version of an OS has better support for your hardware then it makes sense to upgrade, no? Check the forums, lots of people upgraded to get better wireless, sound card, dual screen support.

Just because Feisty supports your hardware and you're happy, doesn't mean that it be so for everyone else.

Yes, there are lots of people who upgrade because it's new and it's shiny, but don't assume that everyone falls into that category.

Gord

P.S. Sorry if this sounds judgemental, it's mostly because I'm so frustrated at the situation.

---

### Post by karellen on 2007-10-31
after years of experience with linux I would say the safest way of enjoying a  new release is a fresh install. the updating (almost) always has some sort of hiccups

---

### Post by gmc on 2007-10-31
> **karellen said:**
> after years of experience with linux I would say the safest way of enjoying a  new release is a fresh install. the updating (almost) always has some sort of hiccups

Oh I agree and in my case that's exactly what I do time and time again. I'll play with the RC versions (usually  starting around RC3 or RC4) and then do a fresh install when the gold version arrives. However this problem (for me) appeared only with the Gold version, RC5 was fine.

In my 9 years with Linux (started with Redhat 5.0) I've learned a thing or two about installing/configuring and fixing linux systems, not that I know everything but when a problem pops up, I have a pretty good idea as to where to start looking. However in all that time I've never seen anything like this, there's no rythme or reason to it.

Todate, FC7 doesn't have the problem, though the repos for FC really really suck, so that's not really a viable option. I believe there might be a problem with CD burning as I have yet to be able to burn a working Debian disk (though it could be the cheap disks that I picked up, I'll know more about that tomorrow)

Gord

---

### Post by revan99 on 2007-10-31
Hello,

It's the first time I use Ubuntu and almost my hardware works. even the media card reader of my notebook works. What doesn't work, or more precisely, stopped working was the CD/DVD drive.

After 2 days of use the CD/DVD drive died. Can't mount any media, and since I replaced windows for Ubuntu, I'm now stucked with a OS which I can't re-install, because the drive isn't detected even on boot.

Can't be worst than this!!! I search on the forum and I found out that many people have CD/DVD drive issues, which no one is able to give a good solution.

Need to get backup data from DVDs to do some works, and every time I need to recover data I have to go to another computer, insert the DVD, copy it to my usb drive.

Can anyone help me, please?!!!! :cry:

---

### Post by gmc on 2007-10-31
> **revan99 said:**
> Hello,

It's the first time I use Ubuntu and almost my hardware works. even the media card reader of my notebook works. What doesn't work, or more precisely, stopped working was the CD/DVD drive.

After 2 days of use the CD/DVD drive died. Can't mount any media, and since I replaced windows for Ubuntu, I'm now stucked with a OS which I can't re-install, because the drive isn't detected even on boot.

Can't be worst than this!!! I search on the forum and I found out that many people have CD/DVD drive issues, which no one is able to give a good solution.

Need to get backup data from DVDs to do some works, and every time I need to recover data I have to go to another computer, insert the DVD, copy it to my usb drive.

Can anyone help me, please?!!!! :cry:

Will the drive play a music CD or is it just data CD/DVD's that are the problem?

Gord

---

### Post by revan99 on 2007-10-31
Any media disc. audio cd, data cd, movie dvd, data dvd...none of them work.

I tried changing the iso9660,udf FStype on fstab, as suggested on most of the posts about this issue, but nothing worked.

After posting my message I managed to borrow an external usb dvd drive, and I went home to try it out and it works perfectly.

The lshw command shows the internal and the external drive...so i think it's not a hardware problem...besides the drive used to work on XP.

Any ideas?

---

### Post by gmc on 2007-10-31
> **revan99 said:**
> Any media disc. audio cd, data cd, movie dvd, data dvd...none of them work.

I tried changing the iso9660,udf FStype on fstab, as suggested on most of the posts about this issue, but nothing worked.

After posting my message I managed to borrow an external usb dvd drive, and I went home to try it out and it works perfectly.

The lshw command shows the internal and the external drive...so i think it's not a hardware problem...besides the drive used to work on XP.

Any ideas?

Ok, can you post the output of lsmod, lspci -vvv and dmesg (preferably right after a complete reboot) and post them here?

Also, I assume the drive mechanically sounds the same now as it did when it was working, when you instert/remove a disc?

Gord

---

### Post by madscientist on 2007-10-31
> **revan99 said:**
> After 2 days of use the CD/DVD drive died. Can't mount any media, and since I replaced windows for Ubuntu, I'm now stucked with a OS which I can't re-install, because the drive isn't detected even on boot.If the drive can't even be detected on boot (I assume by this you mean from the BIOS, so the system won't boot off of the drive) then it sounds to me like your drive is broken (bad hardware).  Certainly if the BIOS can't detect it it's not surprising Linux can't either.  I don't see how this could be considered Ubuntu's fault, except an unfortunate coincidence of timing.

Note that just because you can see the drive with lshw does NOT mean there are no hardware issues with the drive.

Now, if you tried to boot Windows from the borrowed drive and that could use the internal drive properly but Ubuntu couldn't, then I'd say you have a software problem.  However, I don't think it will be that simple because Windows doesn't have any sort of "live CD" that I know of.  Or, if you took the drive out of your system and put it into another system (running Windows or whatever) and it worked there, then I'd say it's a software problem.

But from what you've said here it sounds like a hardware problem to me.

---

### Post by revan99 on 2007-10-31
> **gmc said:**
> Ok, can you post the output of lsmod, lspci -vvv and dmesg (preferably right after a complete reboot) and post them here?

Also, I assume the drive mechanically sounds the same now as it did when it was working, when you instert/remove a disc?

Gord

The drive's noises aren't the same. It's seems like it tries to read disc, then it stops, and it repeats the process again 4/5 times. Then it simply stops and stays unmounted.

The malfunctioning drive is the PIONEER DVD-RW DVR-K12RA(/dev/hdc). The other is a borrowed one(usb external drive).

I'm sending the fstab file also.

```
-----------------------------FSTAB-------------------------------------------

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=1cd2216a-9272-4492-b216-99c38fd33e12 /               reiserfs notail          0       1
# /dev/hda5
UUID=CE48762348760A8B /media/hda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda3
UUID=4f1c98e6-7719-4897-ad7e-90e75fc91f6c none            swap    sw              0       0

/dev/hdc  	/media/cdrom0   auto	user,noauto	0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec	0       0
```

```
-----------------------------DMESG-------------------------------------------

[0.000000] Linux version 2.6.22-14-generic (buildd@crested) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 21:45:15 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] Command line: root=UUID=1cd2216a-9272-4492-b216-99c38fd33e12 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fef0000 (usable)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003fefb000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fefb000 - 000000003ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261872) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F68C0 checksum 0
[    0.000000] ACPI: RSDP 000F68C0, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 3FEF5D48, 0030 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 3FEFAE56, 0084 (r2 AMDK8  PTLTW     6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT 3FEF5D78, 50DE (r1  VIA   PTL_ACPI  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 3FEFBFC0, 0040
[    0.000000] ACPI: SSDT 3FEFAEDA, 00D6 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: APIC 3FEFAFB0, 0050 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000003fef0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261872) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000003fef0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   261872
[    0.000000] On node 0 totalpages: 261775
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1124 pages reserved
[    0.000000]   DMA zone: 2819 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3524 pages used for memmap
[    0.000000]   DMA32 zone: 254252 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d8000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d8000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bffe0000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 257071
[    0.000000] Kernel command line: root=UUID=1cd2216a-9272-4492-b216-99c38fd33e12 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   87.379497] time.c: Detected 797.736 MHz processor.
[   87.380625] Console: colour VGA+ 80x25
[   87.380658] Checking aperture...
[   87.380665] CPU 0: aperture @ e0000000 size 256 MB
[   87.403085] Memory: 1020952k/1047488k available (2274k kernel code, 26148k reserved, 1181k data, 296k init)
[   87.403187] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   87.481452] Calibrating delay using timer specific routine.. 1597.33 BogoMIPS (lpj=3194673)
[   87.481522] Security Framework v1.0.0 initialized
[   87.481539] SELinux:  Disabled at boot.
[   87.481773] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   87.483193] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   87.483883] Mount-cache hash table entries: 256
[   87.484149] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   87.484155] CPU: L2 Cache: 1024K (64 bytes/line)
[   87.484162] CPU 0/0 -> Node 0
[   87.484192] SMP alternatives: switching to UP code
[   87.484453] Freeing SMP alternatives: 24k freed
[   87.485794] Early unpacking initramfs... done
[   88.226678] ACPI: Core revision 20070126
[   88.226794] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   88.280938] Using local APIC timer interrupts.
[   88.406238] result 12464629
[   88.406242] Detected 12.464 MHz APIC timer.
[   88.409109] Brought up 1 CPUs
[   88.409618] NET: Registered protocol family 16
[   88.409769] ACPI: bus type pci registered
[   88.409781] PCI: Using configuration type 1
[   88.411225] ACPI: EC: Look up EC in DSDT
[   88.412504] ACPI: EC: GPE=0x0b, ports=0x66, 0x62
[   88.415485] ACPI: Interpreter enabled
[   88.415492] ACPI: (supports S0 S3 S4 S5)
[   88.415521] ACPI: Using IOAPIC for interrupt routing
[   88.964394] ACPI: EC: GPE=0x0b, ports=0x66, 0x62
[   88.964478] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   88.964494] PCI: Probing PCI hardware (bus 00)
[   88.965103] PCI quirk: region 4000-407f claimed by vt8235 PM
[   88.965111] PCI quirk: region 8100-810f claimed by vt8235 SMB
[   88.965642] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   88.986878] ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *9, disabled.
[   88.987045] ACPI: PCI Interrupt Link [ALKB] (IRQs 16 17 18 19 20 21 22 23) *10, disabled.
[   88.987208] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *11, disabled.
[   88.987365] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *10, disabled.
[   88.987576] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 12 14 15)
[   88.987786] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 12 14 15)
[   88.987996] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *11 12 14 15)
[   88.988211] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   88.988399] Linux Plug and Play Support v0.97 (c) Adam Belay
[   88.988418] pnp: PnP ACPI init
[   88.988440] ACPI: bus type pnp registered
[   89.011686] pnp: PnP ACPI: found 14 devices
[   89.011691] ACPI: ACPI bus type pnp unregistered
[   89.011792] PCI: Using ACPI for IRQ routing
[   89.011798] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   89.011813] PCI: Cannot allocate resource region 0 of device 0000:00:00.0
[   89.011960] NET: Registered protocol family 8
[   89.011965] NET: Registered protocol family 20
[   89.012069] agpgart: Detected AGP bridge 0
[   89.029285] agpgart: AGP aperture is 256M @ 0xe0000000
[   89.029436] pnp: 00:05: iomem range 0xe0000-0xfffff could not be reserved
[   89.029446] pnp: 00:05: iomem range 0xfff00000-0xffffffff could not be reserved
[   89.029454] pnp: 00:05: iomem range 0xffee0000-0xffefffff has been reserved
[   89.029468] pnp: 00:06: ioport range 0x600-0x60f has been reserved
[   89.029475] pnp: 00:06: ioport range 0x1c0-0x1cf has been reserved
[   89.029482] pnp: 00:06: ioport range 0x4d0-0x4d1 has been reserved
[   89.029490] pnp: 00:06: ioport range 0xfe10-0xfe11 has been reserved
[   89.029498] pnp: 00:06: iomem range 0xfec00000-0xfec00fff has been reserved
[   89.029506] pnp: 00:06: iomem range 0xfee00000-0xfee00fff could not be reserved
[   89.030123] PCI: Bridge: 0000:00:01.0
[   89.030129]   IO window: 2000-2fff
[   89.030137]   MEM window: d0100000-d01fffff
[   89.030144]   PREFETCH window: d8000000-dfffffff
[   89.030151] PCI: Bus 2, cardbus bridge: 0000:00:0b.0
[   89.030157]   IO window: 00001c00-00001cff
[   89.030163]   IO window: 00003000-000030ff
[   89.030171]   PREFETCH window: 50000000-53ffffff
[   89.030178]   MEM window: 54000000-57ffffff
[   89.030184] PCI: Bus 6, cardbus bridge: 0000:00:0b.1
[   89.030189]   IO window: 00003400-000034ff
[   89.030195]   IO window: 00003800-000038ff
[   89.030203]   PREFETCH window: 58000000-5bffffff
[   89.030210]   MEM window: 5c000000-5fffffff
[   89.030233] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   89.030257] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 17
[   89.030267] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   89.030282] PCI: Enabling device 0000:00:0b.1 (0000 -> 0003)
[   89.030289] ACPI: PCI Interrupt 0000:00:0b.1[B] -> GSI 18 (level, low) -> IRQ 18
[   89.030300] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   89.030407] NET: Registered protocol family 2
[   89.032753] Time: tsc clocksource has been installed.
[   89.068810] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   89.069442] TCP established hash table entries: 131072 (order: 9, 3145728 bytes)
[   89.073420] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   89.074766] TCP: Hash tables configured (established 131072 bind 65536)
[   89.074773] TCP reno registered
[   89.084956] checking if image is initramfs... it is
[   90.527350] Freeing initrd memory: 7194k freed
[   90.536854] audit: initializing netlink socket (disabled)
[   90.536878] audit(1193853764.032:1): initialized
[   90.545750] VFS: Disk quotas dquot_6.5.1
[   90.545977] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   90.546303] io scheduler noop registered
[   90.546308] io scheduler anticipatory registered
[   90.546313] io scheduler deadline registered
[   90.546739] io scheduler cfq registered (default)
[   90.546753] PCI: VIA PCI bridge detected. Disabling DAC.
[   90.548019] Boot video device is 0000:01:00.0
[   90.622646] Real Time Clock Driver v1.12ac
[   90.622798] Linux agpgart interface v0.102 (c) Dave Jones
[   90.622805] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   90.623156] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   90.625406] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   90.625740] input: Macintosh mouse button emulation as /class/input/input0
[   90.625888] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   90.628119] i8042.c: Detected active multiplexing controller, rev 1.1.
[   90.629328] serio: i8042 KBD port at 0x60,0x64 irq 1
[   90.629337] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   90.629343] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   90.629350] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   90.629357] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   90.629916] mice: PS/2 mouse device common for all mice
[   90.630165] TCP cubic registered
[   90.630422] NET: Registered protocol family 1
[   90.630882] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   90.630898] Freeing unused kernel memory: 296k freed
[   90.714425] input: AT Translated Set 2 keyboard as /class/input/input1
[   92.174611] AppArmor: AppArmor initialized<5>audit(1193853765.668:2):  type=1505 info="AppArmor initialized" pid=1211
[   92.273485] fuse init (API version 7.8)
[   92.282728] Failure registering capabilities with primary security module.
[   92.399822] ACPI: Thermal Zone [THRS] (63 C)
[   92.491326] ACPI: Thermal Zone [THRC] (82 C)
[   93.645246] ACPI: PCI Interrupt 0000:00:0b.2[C] -> GSI 19 (level, low) -> IRQ 19
[   93.737858] usbcore: registered new interface driver usbfs
[   93.737918] usbcore: registered new interface driver hub
[   93.737966] usbcore: registered new device driver usb
[   93.739624] USB Universal Host Controller Interface driver v3.0
[   93.794845] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[d0002000-d00027ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   93.813871] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 21
[   93.814298] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   93.814544] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
[   93.814632] ehci_hcd 0000:00:10.3: irq 21, io mem 0xd0002800
[   93.814643] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   93.814934] usb usb1: configuration #1 chosen from 1 choice
[   93.815001] hub 1-0:1.0: USB hub found
[   93.815014] hub 1-0:1.0: 6 ports detected
[   93.922702] tg3.c:v3.77 (May 31, 2007)
[   93.922741] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 20 (level, low) -> IRQ 20
[   94.006729] eth0: Tigon3 [partno(BCM95705A50) rev 3003 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:0a:e4:4d:1b:16
[   94.006747] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[1]
[   94.006755] eth0: dma_rwctrl[763f0000] dma_mask[32-bit]
[   94.051433] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
[   94.051457] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   94.051536] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[   94.051571] uhci_hcd 0000:00:10.0: irq 21, io base 0x00001020
[   94.051876] usb usb2: configuration #1 chosen from 1 choice
[   94.051943] hub 2-0:1.0: USB hub found
[   94.051956] hub 2-0:1.0: 2 ports detected
[   94.082110] SCSI subsystem initialized
[   94.093709] libata version 2.21 loaded.
[   94.158418] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 21
[   94.158439] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   94.158498] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[   94.158531] uhci_hcd 0000:00:10.1: irq 21, io base 0x00001040
[   94.158816] usb usb3: configuration #1 chosen from 1 choice
[   94.158885] hub 3-0:1.0: USB hub found
[   94.158898] hub 3-0:1.0: 2 ports detected
[   94.222149] usb 1-3: new high speed USB device using ehci_hcd and address 2
[   94.266352] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 21
[   94.266373] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   94.266436] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[   94.266469] uhci_hcd 0000:00:10.2: irq 21, io base 0x00001060
[   94.266763] usb usb4: configuration #1 chosen from 1 choice
[   94.266832] hub 4-0:1.0: USB hub found
[   94.266846] hub 4-0:1.0: 2 ports detected
[   94.291020] Floppy drive(s): fd0 is 1.44M
[   94.320633] FDC 0 is a National Semiconductor PC87306
[   94.363586] usb 1-3: configuration #1 chosen from 1 choice
[   94.388491] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   94.388502] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   94.389582] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[   94.389710] ACPI: Unable to derive IRQ for device 0000:00:11.1
[   94.389716] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[   94.389731] VP_IDE: chipset revision 6
[   94.389736] VP_IDE: not 100% native mode: will probe irqs later
[   94.389755] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[   94.389770]     ide0: BM-DMA at 0x1000-0x1007, BIOS settings: hda:DMA, hdb:pio
[   94.389791]     ide1: BM-DMA at 0x1008-0x100f, BIOS settings: hdc:DMA, hdd:pio
[   94.389804] Probing IDE interface ide0...
[   94.813933] hda: IC25N060ATMR04-0, ATA DISK drive
[   95.077853] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000ae4040210284f]
[   95.433530] usb 4-2: new low speed USB device using uhci_hcd and address 2
[   95.485984] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   95.509403] Probing IDE interface ide1...
[   95.609854] usb 4-2: configuration #1 chosen from 1 choice
[   95.614360] usbcore: registered new interface driver libusual
[   95.635829] usbcore: registered new interface driver hiddev
[   95.645470] Initializing USB Mass Storage driver...
[   95.647149] scsi0 : SCSI emulation for USB Mass Storage devices
[   95.647653] usb-storage: device found at 2
[   95.647659] usb-storage: waiting for device to settle before scanning
[   95.664952] input: KYE USB MOUSE as /class/input/input2
[   95.665003] input: USB HID v1.10 Mouse [KYE USB MOUSE] on usb-0000:00:10.2-2
[   95.665043] usbcore: registered new interface driver usb-storage
[   95.665051] USB Mass Storage support registered.
[   95.665227] usbcore: registered new interface driver usbhid
[   95.665235] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   96.397141] hdc: PIONEER DVD-RW DVR-K12RA, ATAPI CD/DVD-ROM drive
[   97.124863] ide1 at 0x170-0x177,0x376 on irq 15
[   97.139288] hda: max request size: 512KiB
[   97.154384] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
[   97.155458] hda: cache flushes supported
[   97.155538]  hda: hda1 hda2 < hda5 > hda3
[   97.652145] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(33)
[   97.652164] Uniform CD-ROM driver Revision: 3.20
[   97.726949] Attempting manual resume
[   97.726957] swsusp: Resume From Partition 3:3
[   97.726961] PM: Checking swsusp image.
[   97.746588] PM: Resume from disk failed.
[   97.780835] ReiserFS: hda1: found reiserfs format "3.6" with standard journal
[   97.780855] ReiserFS: hda1: using ordered data mode
[   97.787484] ReiserFS: hda1: journal params: device hda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   97.789534] ReiserFS: hda1: checking transaction log (hda1)
[   97.849097] ReiserFS: hda1: Using r5 hash to sort names
[  100.647150] usb-storage: device scan complete
[  100.649513] scsi 0:0:0:0: CD-ROM            ATAPI    DVD+RW 4X4X12    B1FY PQ: 0 ANSI: 0
[  107.744163] PM: Writing back config space on device 0000:00:0c.0 at offset b (was 3ed173b, writing 461025)
[  107.744185] PM: Writing back config space on device 0000:00:0c.0 at offset 3 (was 0, writing 4010)
[  107.744196] PM: Writing back config space on device 0000:00:0c.0 at offset 2 (was 2000000, writing 2000003)
[  107.744207] PM: Writing back config space on device 0000:00:0c.0 at offset 1 (was 2b00000, writing 2b00006)
[  107.744218] PM: Writing back config space on device 0000:00:0c.0 at offset 0 (was 3ed173b, writing 169c14e4)
[  109.356492] NET: Registered protocol family 17
[  109.626320] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  109.626330] tg3: eth0: Flow control is on for TX and on for RX.
[  110.466779] ieee80211_crypt: registered algorithm 'NULL'
[  110.521526] Yenta: CardBus bridge found at 0000:00:0b.0 [1025:0046]
[  110.529513] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  110.529522] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  110.548268] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  110.613340] bcm43xx driver
[  110.654584] Yenta: ISA IRQ mask 0x00b8, PCI irq 17
[  110.654593] Socket status: 30000006
[  110.654919] Yenta: CardBus bridge found at 0000:00:0b.1 [1025:0046]
[  110.782513] Yenta: ISA IRQ mask 0x00b8, PCI irq 18
[  110.782523] Socket status: 30000006
[  110.785686] PCI: Enabling device 0000:00:0a.0 (0000 -> 0002)
[  110.785699] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 21 (level, low) -> IRQ 21
[  110.791096] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  111.856370] irda_init()
[  111.856411] NET: Registered protocol family 23
[  112.086724] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 22
[  112.093190] PCI: Setting latency timer of device 0000:00:11.6 to 64
[  112.826978] input: PC Speaker as /class/input/input3
[  113.019782] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9248b1, caps: 0x904713/0x4000
[  113.060986] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[  113.063799] parport_pc 00:0a: reported by Plug and Play ACPI
[  113.063889] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  113.235599] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[  113.235642] nsc-ircc, chip->init
[  113.235656] nsc-ircc, Found chip at base=0x02e
[  113.235687] nsc-ircc, driver loaded (Dag Brattli)
[  113.235699] nsc_ircc_open(), can't get iobase of 0x2f8
[  113.235733] nsc-ircc, Found chip at base=0x02e
[  113.235763] nsc-ircc, driver loaded (Dag Brattli)
[  113.235769] nsc_ircc_open(), can't get iobase of 0x2f8
[  113.236054] pnp: Device 00:0b disabled.
[  113.435016] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[  113.435196] sr 0:0:0:0: Attached scsi CD-ROM sr0
[  113.509067] wbsd: Winbond W83L51xD SD/MMC card interface driver
[  113.509075] wbsd: Copyright(c) Pierre Ossman
[  113.514357] mmc0: W83L51xD id 7112 at 0x820 irq 10 FIFO PnP
[  113.549129] sr 0:0:0:0: Attached scsi generic sg0 type 5
[  113.786644] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
[  113.786795] PCI: Setting latency timer of device 0000:00:11.5 to 64
[  114.762966] lp0: using parport0 (interrupt-driven).
[  114.913064] Adding 2008116k swap on /dev/hda3.  Priority:-1 extents:1 across:2008116k
[  124.456994] NET: Registered protocol family 10
[  124.457317] lo: Disabled Privacy Extensions
[  126.222992] ACPI: Battery Slot [BAT0] (battery present)
[  126.508900] ACPI: AC Adapter [AC] (on-line)
[  126.531146] No dock devices found.
[  126.661487] input: Power Button (FF) as /class/input/input5
[  126.669800] ACPI: Power Button (FF) [PWRF]
[  126.731520] input: Lid Switch as /class/input/input6
[  126.739733] ACPI: Lid Switch [LID]
[  126.781839] input: Sleep Button (CM) as /class/input/input7
[  126.782362] ACPI: Sleep Button (CM) [SLPB]
[  126.934564] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[  127.234935] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (version 2.00.00)
[  127.235009] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x2
[  127.235017] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x6
[  127.235023] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x12
[  127.237454] Marking TSC unstable due to cpufreq changes
[  127.239680] Time: acpi_pm clocksource has been installed.
[  129.719676] ppdev: user-space parallel port driver
[  130.031100] audit(1193853802.896:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4965 profile="/usr/sbin/cupsd"
[  130.311803] ttyS1: LSR safety check engaged!
[  130.483817] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  131.344185] Failure registering capabilities with primary security module.
[  131.850128] Bluetooth: Core ver 2.11
[  131.850398] NET: Registered protocol family 31
[  131.850404] Bluetooth: HCI device and connection manager initialized
[  131.850414] Bluetooth: HCI socket layer initialized
[  131.920545] Bluetooth: L2CAP ver 2.8
[  131.920558] Bluetooth: L2CAP socket layer initialized
[  131.997156] Bluetooth: RFCOMM socket layer initialized
[  131.997375] Bluetooth: RFCOMM TTY layer initialized
[  131.997382] Bluetooth: RFCOMM ver 1.8
[  134.258181] [drm] Initialized drm 1.1.0 20060810
[  134.286648] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  134.290463] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[  136.055723] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  136.303415] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[  136.303647] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[  136.303912] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[  137.072248] vmmon: module license 'unspecified' taints kernel.
[  137.077581] /dev/vmmon[5356]: VMCI: Driver initialized.
[  137.081637] /dev/vmmon[5356]: Module vmmon: registered with major=10 minor=165
[  137.082269] /dev/vmmon[5356]: Initial HV check: anyNotCapable=1 anyUnlocked=0 anyEnabled=0 anyDisabled=0
[  137.082279] /dev/vmmon[5356]: Module vmmon: initialized
[  137.582809] [drm] Setting GART location based on new memory map
[  137.582826] [drm] Loading R300 Microcode
[  137.582897] [drm] writeback test succeeded in 1 usecs
[  137.748824] /dev/vmnet: open called by PID 5400 (vmnet-bridge)
[  137.749378] /dev/vmnet: hub 0 does not exist, allocating memory.
[  137.749855] /dev/vmnet: port on hub 0 successfully opened
[  137.750303] bridge-eth0: enabling the bridge
[  137.750718] bridge-eth0: up
[  137.751077] bridge-eth0: already up
[  137.751085] bridge-eth0: attached
[  138.640451] /dev/vmnet: open called by PID 5416 (vmnet-dhcpd)
[  138.640952] /dev/vmnet: hub 1 does not exist, allocating memory.
[  138.641429] /dev/vmnet: port on hub 1 successfully opened
[  138.829665] /dev/vmnet: open called by PID 5429 (vmnet-dhcpd)
[  138.830162] /dev/vmnet: hub 8 does not exist, allocating memory.
[  138.830647] /dev/vmnet: port on hub 8 successfully opened
[  138.919229] /dev/vmnet: open called by PID 5434 (vmnet-natd)
[  138.919802] /dev/vmnet: port on hub 8 successfully opened
[  139.309535] eth0: no IPv6 routers present
[  148.107562] /dev/vmnet: open called by PID 5526 (vmnet-netifup)
[  148.108228] /dev/vmnet: port on hub 1 successfully opened
[  148.646417] /dev/vmnet: open called by PID 5537 (vmnet-netifup)
[  148.646617] /dev/vmnet: port on hub 8 successfully opened
[  157.710872] UDF-fs: Partition marked readonly; forcing readonly mount
[  157.824197] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'MP3_DVD1', timestamp 2005/04/25 23:52 (1000)
[  158.719794] vmnet1: no IPv6 routers present
[  159.187560] vmnet8: no IPv6 routers present
[  159.339653] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  193.762786] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  225.454188] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  250.273759] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  275.093189] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  407.028620] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  615.988795] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.028862] hdc: tray open
[  616.029360] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.029370] end_request: I/O error, dev hdc, sector 8388352
[  616.029380] Buffer I/O error on device hdc, logical block 2097088
[  616.029389] Buffer I/O error on device hdc, logical block 2097089
[  616.040371] hdc: tray open
[  616.040832] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.040841] end_request: I/O error, dev hdc, sector 8388352
[  616.040848] Buffer I/O error on device hdc, logical block 2097088
[  616.040856] Buffer I/O error on device hdc, logical block 2097089
[  616.052377] hdc: tray open
[  616.052838] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.052847] end_request: I/O error, dev hdc, sector 8388584
[  616.052856] Buffer I/O error on device hdc, logical block 2097146
[  616.052864] Buffer I/O error on device hdc, logical block 2097147
[  616.064382] hdc: tray open
[  616.064844] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.064852] end_request: I/O error, dev hdc, sector 8388584
[  616.064859] Buffer I/O error on device hdc, logical block 2097146
[  616.064867] Buffer I/O error on device hdc, logical block 2097147
[  616.076389] hdc: tray open
[  616.076855] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.076862] end_request: I/O error, dev hdc, sector 0
[  616.076868] Buffer I/O error on device hdc, logical block 0
[  616.076875] Buffer I/O error on device hdc, logical block 1
[  616.082760] hdc: tray open
[  616.083136] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.083143] end_request: I/O error, dev hdc, sector 0
[  616.094396] hdc: tray open
[  616.094857] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.094864] end_request: I/O error, dev hdc, sector 0
[  616.106401] hdc: tray open
[  616.106863] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.106871] end_request: I/O error, dev hdc, sector 8388600
[  616.112404] hdc: tray open
[  616.112866] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.112874] end_request: I/O error, dev hdc, sector 8388600
[  616.118408] hdc: tray open
[  616.118870] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.118878] end_request: I/O error, dev hdc, sector 8388600
[  616.124411] hdc: tray open
[  616.124875] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.124883] end_request: I/O error, dev hdc, sector 8388600
[  616.130413] hdc: tray open
[  616.130874] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.130882] end_request: I/O error, dev hdc, sector 8388600
[  616.136423] hdc: tray open
[  616.136882] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.136893] end_request: I/O error, dev hdc, sector 8388600
[  616.142422] hdc: tray open
[  616.142881] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.142889] end_request: I/O error, dev hdc, sector 8388536
[  616.148428] hdc: tray open
[  616.148886] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.148896] end_request: I/O error, dev hdc, sector 8388540
[  616.154427] hdc: tray open
[  616.154888] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.154897] end_request: I/O error, dev hdc, sector 8388592
[  616.160454] hdc: tray open
[  616.160913] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.160922] end_request: I/O error, dev hdc, sector 8388596
[  616.166431] hdc: tray open
[  616.166892] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.166900] end_request: I/O error, dev hdc, sector 8388600
[  616.172434] hdc: tray open
[  616.172893] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.172901] end_request: I/O error, dev hdc, sector 8388600
[  616.178437] hdc: tray open
[  616.178898] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.178905] end_request: I/O error, dev hdc, sector 0
[  616.184439] hdc: tray open
[  616.184904] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.184912] end_request: I/O error, dev hdc, sector 4
[  616.190441] hdc: tray open
[  616.190902] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.190909] end_request: I/O error, dev hdc, sector 0
[  616.196444] hdc: tray open
[  616.196906] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.196914] end_request: I/O error, dev hdc, sector 4
[  616.202448] hdc: tray open
[  616.202908] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.202916] end_request: I/O error, dev hdc, sector 0
[  616.208451] hdc: tray open
[  616.208914] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.208921] end_request: I/O error, dev hdc, sector 4
[  616.214453] hdc: tray open
[  616.214913] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.214921] end_request: I/O error, dev hdc, sector 0
[  616.220455] hdc: tray open
[  616.220917] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.220924] end_request: I/O error, dev hdc, sector 4
[  616.226459] hdc: tray open
[  616.226919] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.226926] end_request: I/O error, dev hdc, sector 0
[  616.232461] hdc: tray open
[  616.232922] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.232929] end_request: I/O error, dev hdc, sector 4
[  616.238467] hdc: tray open
[  616.238932] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.238939] end_request: I/O error, dev hdc, sector 0
[  616.244473] hdc: tray open
[  616.244931] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.244939] end_request: I/O error, dev hdc, sector 4
[  616.252694] hdc: tray open
[  616.253093] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.253105] end_request: I/O error, dev hdc, sector 0
[  616.258473] hdc: tray open
[  616.258934] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.258942] end_request: I/O error, dev hdc, sector 4
[  616.264476] hdc: tray open
[  616.264940] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.264947] end_request: I/O error, dev hdc, sector 0
[  616.270479] hdc: tray open
[  616.270940] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.270947] end_request: I/O error, dev hdc, sector 4
[  616.276482] hdc: tray open
[  616.276944] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.276951] end_request: I/O error, dev hdc, sector 0
[  616.282485] hdc: tray open
[  616.282946] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.282954] end_request: I/O error, dev hdc, sector 4
[  616.288488] hdc: tray open
[  616.288949] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.288956] end_request: I/O error, dev hdc, sector 0
[  616.294492] hdc: tray open
[  616.294952] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.294960] end_request: I/O error, dev hdc, sector 4
[  616.300493] hdc: tray open
[  616.300955] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.300962] end_request: I/O error, dev hdc, sector 0
[  616.306496] hdc: tray open
[  616.306960] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.306967] end_request: I/O error, dev hdc, sector 4
[  616.312498] hdc: tray open
[  616.312960] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.312967] end_request: I/O error, dev hdc, sector 0
[  616.318525] hdc: tray open
[  616.318987] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.318995] end_request: I/O error, dev hdc, sector 4
[  616.324505] hdc: tray open
[  616.324965] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.324972] end_request: I/O error, dev hdc, sector 0
[  616.330508] hdc: tray open
[  616.330969] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.330977] end_request: I/O error, dev hdc, sector 4
[  616.336511] hdc: tray open
[  616.336974] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.336981] end_request: I/O error, dev hdc, sector 0
[  616.342514] hdc: tray open
[  616.342973] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.342981] end_request: I/O error, dev hdc, sector 4
[  616.348516] hdc: tray open
[  616.348976] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.348984] end_request: I/O error, dev hdc, sector 0
[  616.354519] hdc: tray open
[  616.354980] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.354987] end_request: I/O error, dev hdc, sector 4
[  616.360522] hdc: tray open
[  616.360983] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.360991] end_request: I/O error, dev hdc, sector 0
[  616.366524] hdc: tray open
[  616.366987] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.366994] end_request: I/O error, dev hdc, sector 4
[  616.372527] hdc: tray open
[  616.372989] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.372996] end_request: I/O error, dev hdc, sector 0
[  616.378531] hdc: tray open
[  616.378991] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.378999] end_request: I/O error, dev hdc, sector 4
[  616.384532] hdc: tray open
[  616.384995] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.385003] end_request: I/O error, dev hdc, sector 0
[  616.390535] hdc: tray open
[  616.390996] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.391003] end_request: I/O error, dev hdc, sector 4
[  616.396543] hdc: tray open
[  616.397005] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.397012] end_request: I/O error, dev hdc, sector 0
[  616.402542] hdc: tray open
[  616.403002] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.403009] end_request: I/O error, dev hdc, sector 4
[  616.408546] hdc: tray open
[  616.409007] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.409014] end_request: I/O error, dev hdc, sector 0
[  616.414550] hdc: tray open
[  616.415010] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.415017] end_request: I/O error, dev hdc, sector 4
[  616.420555] hdc: tray open
[  616.421012] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.421022] end_request: I/O error, dev hdc, sector 0
[  616.426552] hdc: tray open
[  616.427016] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.427024] end_request: I/O error, dev hdc, sector 4
[  616.432555] hdc: tray open
[  616.433017] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.433024] end_request: I/O error, dev hdc, sector 0
[  616.438560] hdc: tray open
[  616.439024] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.439031] end_request: I/O error, dev hdc, sector 4
[  616.444561] hdc: tray open
[  616.445022] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.445029] end_request: I/O error, dev hdc, sector 0
[  616.450565] hdc: tray open
[  616.451027] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.451035] end_request: I/O error, dev hdc, sector 4
[  616.456567] hdc: tray open
[  616.457028] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.457036] end_request: I/O error, dev hdc, sector 0
[  616.462573] hdc: tray open
[  616.463032] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.463039] end_request: I/O error, dev hdc, sector 4
[  616.468577] hdc: tray open
[  616.469037] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.469046] end_request: I/O error, dev hdc, sector 0
[  616.474577] hdc: tray open
[  616.475036] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.475044] end_request: I/O error, dev hdc, sector 4
[  616.532059] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.602840] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.632654] hdc: tray open
[  616.633112] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.633123] end_request: I/O error, dev hdc, sector 8388352
[  616.638654] hdc: tray open
[  616.639115] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.639124] end_request: I/O error, dev hdc, sector 8388356
[  616.644656] hdc: tray open
[  616.645118] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.645126] end_request: I/O error, dev hdc, sector 8388352
[  616.650658] hdc: tray open
[  616.651119] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.651127] end_request: I/O error, dev hdc, sector 8388356
[  616.656662] hdc: tray open
[  616.657123] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.657130] end_request: I/O error, dev hdc, sector 8388584
[  616.662665] hdc: tray open
[  616.663126] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.663134] end_request: I/O error, dev hdc, sector 8388588
[  616.668667] hdc: tray open
[  616.669129] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.669137] end_request: I/O error, dev hdc, sector 8388584
[  616.674672] hdc: tray open
[  616.675132] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.675140] end_request: I/O error, dev hdc, sector 8388588
[  616.680673] hdc: tray open
[  616.681134] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.681142] end_request: I/O error, dev hdc, sector 0
[  616.686675] hdc: tray open
[  616.687139] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.687146] end_request: I/O error, dev hdc, sector 4
[  616.692679] hdc: tray open
[  616.693139] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.693146] end_request: I/O error, dev hdc, sector 0
[  616.698681] hdc: tray open
[  616.699143] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.699150] end_request: I/O error, dev hdc, sector 4
[  616.704684] hdc: tray open
[  616.705148] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.705155] end_request: I/O error, dev hdc, sector 0
[  616.710686] hdc: tray open
[  616.711147] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.711155] end_request: I/O error, dev hdc, sector 4
[  616.716690] hdc: tray open
[  616.717151] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.717159] end_request: I/O error, dev hdc, sector 8388600
[  616.722692] hdc: tray open
[  616.723153] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.723161] end_request: I/O error, dev hdc, sector 8388600
[  616.728699] hdc: tray open
[  616.729162] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.729170] end_request: I/O error, dev hdc, sector 8388600
[  616.734698] hdc: tray open
[  616.735159] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.735167] end_request: I/O error, dev hdc, sector 8388600
[  616.740701] hdc: tray open
[  616.741162] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.741171] end_request: I/O error, dev hdc, sector 8388600
[  616.746708] hdc: tray open
[  616.747168] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.747177] end_request: I/O error, dev hdc, sector 8388600
[  616.756276] hdc: tray open
[  616.756796] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.756807] end_request: I/O error, dev hdc, sector 8388536
[  616.761714] hdc: tray open
[  616.762175] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.762183] end_request: I/O error, dev hdc, sector 8388540
[  616.767715] hdc: tray open
[  616.768175] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.768183] end_request: I/O error, dev hdc, sector 8388592
[  616.773716] hdc: tray open
[  616.774181] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.774189] end_request: I/O error, dev hdc, sector 8388596
[  616.779719] hdc: tray open
[  616.780180] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.780188] end_request: I/O error, dev hdc, sector 8388600
[  616.785723] hdc: tray open
[  616.786184] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.786192] end_request: I/O error, dev hdc, sector 8388600
[  616.791726] hdc: tray open
[  616.792186] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.792193] end_request: I/O error, dev hdc, sector 0
[  616.797728] hdc: tray open
[  616.798189] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.798197] end_request: I/O error, dev hdc, sector 4
[  616.803731] hdc: tray open
[  616.804191] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.804199] end_request: I/O error, dev hdc, sector 0
[  616.809734] hdc: tray open
[  616.810194] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.810201] end_request: I/O error, dev hdc, sector 4
[  616.815736] hdc: tray open
[  616.816198] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.816206] end_request: I/O error, dev hdc, sector 0
[  616.821739] hdc: tray open
[  616.822200] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.822208] end_request: I/O error, dev hdc, sector 4
[  616.827742] hdc: tray open
[  616.828204] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.828211] end_request: I/O error, dev hdc, sector 0
[  616.833745] hdc: tray open
[  616.834207] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.834214] end_request: I/O error, dev hdc, sector 4
[  616.839750] hdc: tray open
[  616.840209] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.840216] end_request: I/O error, dev hdc, sector 0
[  616.845751] hdc: tray open
[  616.846213] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.846220] end_request: I/O error, dev hdc, sector 4
[  616.851753] hdc: tray open
[  616.852214] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.852221] end_request: I/O error, dev hdc, sector 0
[  616.857756] hdc: tray open
[  616.858218] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.858225] end_request: I/O error, dev hdc, sector 4
[  616.863759] hdc: tray open
[  616.864220] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.864227] end_request: I/O error, dev hdc, sector 0
[  616.869763] hdc: tray open
[  616.870223] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.870231] end_request: I/O error, dev hdc, sector 4
[  616.875764] hdc: tray open
[  616.876228] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.876235] end_request: I/O error, dev hdc, sector 0
[  616.881767] hdc: tray open
[  616.882228] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.882235] end_request: I/O error, dev hdc, sector 4
[  616.887771] hdc: tray open
[  616.888232] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.888239] end_request: I/O error, dev hdc, sector 0
[  616.893774] hdc: tray open
[  616.894234] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.894242] end_request: I/O error, dev hdc, sector 4
[  616.899776] hdc: tray open
[  616.900238] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.900246] end_request: I/O error, dev hdc, sector 0
[  616.905781] hdc: tray open
[  616.906239] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.906247] end_request: I/O error, dev hdc, sector 4
[  616.911783] hdc: tray open
[  616.912243] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.912250] end_request: I/O error, dev hdc, sector 0
[  616.917785] hdc: tray open
[  616.918246] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.918254] end_request: I/O error, dev hdc, sector 4
[  616.923788] hdc: tray open
[  616.924249] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.924256] end_request: I/O error, dev hdc, sector 0
[  616.929791] hdc: tray open
[  616.930253] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.930260] end_request: I/O error, dev hdc, sector 4
[  616.935801] hdc: tray open
[  616.936256] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.936266] end_request: I/O error, dev hdc, sector 0
[  616.941801] hdc: tray open
[  616.942258] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.942267] end_request: I/O error, dev hdc, sector 4
[  616.947799] hdc: tray open
[  616.948264] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.948271] end_request: I/O error, dev hdc, sector 0
[  616.953801] hdc: tray open
[  616.954263] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.954271] end_request: I/O error, dev hdc, sector 4
[  616.959809] hdc: tray open
[  616.960270] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.960277] end_request: I/O error, dev hdc, sector 0
[  616.965808] hdc: tray open
[  616.966269] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.966277] end_request: I/O error, dev hdc, sector 4
[  616.971814] hdc: tray open
[  616.972273] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.972280] end_request: I/O error, dev hdc, sector 0
[  616.977813] hdc: tray open
[  616.978274] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.978281] end_request: I/O error, dev hdc, sector 4
[  616.983815] hdc: tray open
[  616.984280] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.984287] end_request: I/O error, dev hdc, sector 0
[  616.989819] hdc: tray open
[  616.990280] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.990287] end_request: I/O error, dev hdc, sector 4
[  616.995825] hdc: tray open
[  616.996279] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.996286] end_request: I/O error, dev hdc, sector 0
[  617.001827] hdc: tray open
[  617.002281] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  617.002290] end_request: I/O error, dev hdc, sector 4
[  617.007440] hdc: tray open
[  617.007954] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  617.007964] end_request: I/O error, dev hdc, sector 0
[  617.012829] hdc: tray open
[  617.013290] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  617.013297] end_request: I/O error, dev hdc, sector 4
[  617.018833] hdc: tray open
[  617.019289] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  617.019296] end_request: I/O error, dev hdc, sector 0
[  617.024838] hdc: tray open
[  617.025294] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  617.025301] end_request: I/O error, dev hdc, sector 4
[  617.030839] hdc: tray open
[  617.031294] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  617.031303] end_request: I/O error, dev hdc, sector 0
[  617.036844] hdc: tray open
[  617.037298] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  617.037306] end_request: I/O error, dev hdc, sector 4
[  617.042843] hdc: tray open
[  617.043299] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  617.043306] end_request: I/O error, dev hdc, sector 0
[  617.048846] hdc: tray open
[  617.049306] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  617.049313] end_request: I/O error, dev hdc, sector 4
[  617.054849] hdc: tray open
[  617.055304] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  617.055311] end_request: I/O error, dev hdc, sector 0
[  617.060852] hdc: tray open
[  617.061308] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  617.061316] end_request: I/O error, dev hdc, sector 4
[  617.066854] hdc: tray open
[  617.067310] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  617.067317] end_request: I/O error, dev hdc, sector 0
[  617.072857] hdc: tray open
[  617.073312] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  617.073319] end_request: I/O error, dev hdc, sector 4
[  617.078860] hdc: tray open
[  617.079316] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  617.079324] end_request: I/O error, dev hdc, sector 0
[  617.084863] hdc: tray open
[  617.085321] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  617.085328] end_request: I/O error, dev hdc, sector 4
[  617.133081] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
```

```
--------------------------------LSMOD-----------------------------------------
Module                  Size  Used by
udf                    90024  1 
vmnet                  51008  13 
vmblock                19144  3 
vmmon                 999404  0 
binfmt_misc            14860  1 
radeon                129824  2 
drm                   106408  3 radeon
rfcomm                 47656  2 
l2cap                  28672  11 rfcomm
bluetooth              63876  4 rfcomm,l2cap
ppdev                  11272  0 
powernow_k8            16608  0 
cpufreq_powersave       3072  0 
cpufreq_stats           8160  0 
cpufreq_userspace       6048  0 
cpufreq_ondemand       10896  1 
cpufreq_conservative     9608  0 
freq_table              6464  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
video                  21140  0 
container               6400  0 
sbs                    21520  0 
button                 10400  0 
dock                   12264  0 
ac                      7304  0 
battery                12424  0 
ipv6                  317192  8 
sbp2                   27144  0 
lp                     15048  0 
joydev                 13440  0 
pcmcia                 46232  0 
snd_via82xx            33192  2 
gameport               18704  1 snd_via82xx
sg                     41384  0 
wbsd                   20752  0 
mmc_core               33416  1 wbsd
snd_mpu401_uart        11008  1 snd_via82xx
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
sr_mod                 19876  1 
snd_seq_midi           11008  0 
snd_rawmidi            29824  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
parport_pc             41896  1 
parport                44172  3 ppdev,lp,parport_pc
pcspkr                  4608  0 
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
k8temp                  7680  0 
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                45596  0 
serio_raw               9092  0 
i2c_viapro             11544  0 
i2c_core               30208  1 i2c_viapro
snd_via82xx_modem      18444  0 
snd_ac97_codec        122200  2 snd_via82xx,snd_via82xx_modem
ac97_bus                4096  1 snd_ac97_codec
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                94344  5 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_timer              27272  2 snd_seq,snd_pcm
via_ircc               29632  0 
irda                  221804  1 via_ircc
snd                    69288  15 snd_via82xx,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         12560  3 snd_via82xx,snd_via82xx_modem,snd_pcm
soundcore              10272  1 snd
crc_ccitt               3456  1 irda
shpchp                 38300  0 
bcm43xx               140392  0 
ieee80211softmac       34944  1 bcm43xx
pci_hotplug            36612  1 shpchp
ieee80211              38344  2 bcm43xx,ieee80211softmac
yenta_socket           30220  2 
rsrc_nonstatic         14208  1 yenta_socket
pcmcia_core            46628  3 pcmcia,yenta_socket,rsrc_nonstatic
ieee80211_crypt         8192  1 ieee80211
af_packet              28172  2 
evdev                  13056  5 
reiserfs              255616  1 
ide_cd                 35488  0 
cdrom                  41768  2 sr_mod,ide_cd
ide_disk               20352  4 
usb_storage            81728  1 
usbhid                 32576  0 
hid                    33408  1 usbhid
libusual               22824  1 usb_storage
via82cxxx              11268  0 [permanent]
ide_core              141200  4 ide_cd,ide_disk,usb_storage,via82cxxx
floppy                 69608  0 
ata_generic             9988  0 
libata                138928  1 ata_generic
scsi_mod              172856  5 sbp2,sg,sr_mod,usb_storage,libata
ehci_hcd               40076  0 
uhci_hcd               29600  0 
usbcore               161584  6 usb_storage,usbhid,libusual,ehci_hcd,uhci_hcd
tg3                   118788  0 
ohci1394               38984  0 
ieee1394              109528  2 sbp2,ohci1394
thermal                16528  0 
processor              36232  2 powernow_k8,thermal
fan                     6920  0 
fuse                   52528  3 
apparmor               47008  0 
commoncap               9472  1 apparmor

```

```
---------------------------LSPCI-----------------------------------------------

00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
	Subsystem: Acer Incorporated [ALI] Unknown device 0046
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0
	Region 0: Memory at <ignored> (32-bit, prefetchable)
	Capabilities: [80] AGP version 3.5
		Status: RQ=32 Iso- ArqSz=0 Cal=2 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
		Command: RQ=1 ArqSz=0 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x8
	Capabilities: [c0] HyperTransport: Slave or Primary Interface
		!!! Possibly incomplete decoding
		Command: BaseUnitID=0 UnitCnt=3 MastHost- DefDir-
		Link Control 0: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0
		Link Config 0: MLWI=16bit MLWO=16bit LWI=16bit LWO=16bit
		Link Control 1: CFlE- CST- CFE- <LkFail+ Init- EOC+ TXO+ <CRCErr=0
		Link Config 1: MLWI=8bit MLWO=8bit LWI=8bit LWO=8bit
		Revision ID: 1.02
	Capabilities: [68] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] HyperTransport: Interrupt Discovery and Configuration

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d0100000-d01fffff
	Prefetchable memory behind bridge: d8000000-dfffffff
	Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:0a.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
	Subsystem: Wistron NeWeb Corp. TravelMate 290E WLAN Mini-PCI Card
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at d0000000 (32-bit, non-prefetchable) [size=8K]

00:0b.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev aa)
	Subsystem: Acer Incorporated [ALI] Unknown device 0046
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 168
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at 60010000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: 50000000-53fff000 (prefetchable)
	Memory window 1: 54000000-57fff000
	I/O window 0: 00001c00-00001cff
	I/O window 1: 00003000-000030ff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001

00:0b.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev aa)
	Subsystem: Acer Incorporated [ALI] Unknown device 0046
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 168
	Interrupt: pin B routed to IRQ 18
	Region 0: Memory at 60011000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=06, subordinate=09, sec-latency=176
	Memory window 0: 58000000-5bfff000 (prefetchable)
	Memory window 1: 5c000000-5ffff000
	I/O window 0: 00003400-000034ff
	I/O window 1: 00003800-000038ff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001

00:0b.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 02) (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 0046
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (500ns min, 1000ns max)
	Interrupt: pin C routed to IRQ 19
	Region 0: Memory at d0002000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=2 PME+

00:0c.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
	Subsystem: Acer Incorporated [ALI] Unknown device 0046
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (16000ns min), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at d0010000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at 60000000 [disabled] [size=64K]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [50] Vital Product Data
	Capabilities: [58] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable-
		Address: ff6bf27bffedff7c  Data: fffd

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 0046
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 21
	Region 4: I/O ports at 1020 [size=32]
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 0046
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 21
	Region 4: I/O ports at 1040 [size=32]
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 0046
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin C routed to IRQ 21
	Region 4: I/O ports at 1060 [size=32]
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME+

00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 0046
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin D routed to IRQ 21
	Region 0: Memory at d0002800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
	Subsystem: Acer Incorporated [ALI] Unknown device 0046
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
	Subsystem: Acer Incorporated [ALI] Unknown device 0046
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Interrupt: pin A routed to IRQ 0
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	Region 4: I/O ports at 1000 [size=16]
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
	Subsystem: Acer Incorporated [ALI] Unknown device 0046
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin C routed to IRQ 22
	Region 0: I/O ports at 1400 [size=256]
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
	Subsystem: Acer Incorporated [ALI] Unknown device 0046
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin C routed to IRQ 22
	Region 0: I/O ports at 1800 [size=256]
	Capabilities: [d0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Capabilities: [80] HyperTransport: Host or Secondary Interface
		!!! Possibly incomplete decoding
		Command: WarmRst+ DblEnd-
		Link Control: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0
		Link Config: MLWI=16bit MLWO=16bit LWI=16bit LWO=16bit
		Revision ID: 1.02

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] (prog-if 00 [VGA])
	Subsystem: Acer Incorporated [ALI] Unknown device 0046
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B+
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 66 (2000ns min), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at d8000000 (32-bit, prefetchable) [size=128M]
	Region 1: I/O ports at 2000 [size=256]
	Region 2: Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at d0120000 [disabled] [size=128K]
	Capabilities: [58] AGP version 3.0
		Status: RQ=256 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
		Command: RQ=32 ArqSz=0 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x8
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-


```

Best regards,

revan99

---

### Post by skits on 2007-10-31
My Experience with upgrading to Ubuntu 7.1 &#8211; not good!
I have been using Ubuntu Dapper for about a year and have used other distributions of Linux for about ten years. So I'm not a total neophyte. And the reviews on Gutsy were very good.
I downloaded the Ubuntu 7.10 i386 desktop iso &#8211; took three tries to get one that passed the MD5 check. 
I burned cd's, five, before I decided it might be the brand of cd that was causing the Check Disk Integrity failures. A different brand worked first burn. 
The live cd functioned well &#8211; I had 1280x1024 resolution, windows opened and closed, Internet was browsed, games played, Office used &#8211; in short it looked good. Time to try the Install function.
I have a Gateway AMD 3800 with 1GB ram and a 200GB hd, nVidia GeForce 6100 onboard video, onboard NIC etc. . I had the drive partitioned into several virtual drives &#8211; this saved my valuable files as /home is on one &#8220;drive&#8221;.
Install went well; have to be careful setting up the partitions/drives to make sure it doesn't reformat the wrong drive and destroy valuable data. Time to re-boot.
Hmm, resolution is 800x600. Strange. Check xorg.conf &#8211; all resolutions are there but not displayed on  System>Preference>Screen resolution, only 640x480 and 800x600. Do some browsing on the Internet, lots of hits on Google for Ubuntu 7.1 display issues. That should have been a warning!
Download and install the nVidia proprietary driver and reboot. Windows open, but have no title bars, windows are ghosts and don't update, windows cannot be moved around, there are no icons on the top tool bar. Went through this whole process several times. I found that I could get the empty windows (e.g. Synaptic Package Manager) to update by either going to a terminal session via Ctrl-Alt-F4 and then back via Ctrl-Alt-F7, or by minimizing the window (when it had &#8220;decorations&#8221;) and then restoring it. Either is a tedious way to scroll through choices.
More browsing on the internet. Found several hints. Tried adding Options to Xorg.conf in the Screen section to &#8220;AddARGBLXvisuals&#8221; &#8220;True&#8221; and &#8220;DisableGLXRootClipping&#8221;&#8221;True&#8221;. No better.
Tried setting indirect=yes in /usr/bin/compiz. Nope
Tried apt-get install advanced-desktop-effects-settings and turning on various combinations of the effects. Nope. Still variations on the non-updating, ghosting etc of the applications windows.
Tried removing/disabling the nVidia driver. Nope.
Could not find how to remove compiz. 
Any time I had Compiz AND the nVidia driver enabled, I had the weird problems. Without the nVidia driver I had low resolutions. but most things worked.
I tried the Alternate install &#8211; no better.
After two days of frustration, I downloaded Dapper, 6.06.1. I re-installed it and, apart from having to re-install all the otional programs like gcj, gcc, g77, f95, Eclipse etc etc etc, all is well now.
So, my advice if you have an nVidia card (or, if you have an ATI card, according to some of the 'issues' I googled) DO NOT UPGRADE to 7.10, unless you are prepared for a lot of work. Of course, your mileage may vary. 
And, BACK UP your important files first!

---

### Post by gmc on 2007-11-01
Hi Revan99,

I've looked over the information you posted and I'm afraid it doesn't look good for the drive.

> **revan99 said:**
> 
[   96.397141] hdc: PIONEER DVD-RW DVR-K12RA, ATAPI CD/DVD-ROM drive
[   97.652145] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(33)
[   97.652164] Uniform CD-ROM driver Revision: 3.20


The BIOS and Linux agree on what brand/model of drive it is. 

> **revan99 said:**
> 
[  100.649513] scsi 0:0:0:0: CD-ROM            ATAPI    DVD+RW 4X4X12    B1FY PQ: 0 ANSI: 0


Linux loads the appropriate driver for the drive.

> **revan99 said:**
> 
[  615.988795] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.028862] hdc: tray open
[  616.029360] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[  616.029370] end_request: I/O error, dev hdc, sector 8388352
[  616.029380] Buffer I/O error on device hdc, logical block 2097088
[  616.029389] Buffer I/O error on device hdc, logical block 2097089
[  616.040371] hdc: tray open


I've seen errors like these from an external drive, where the door was obviously closed but the drive itself insisted that it wasn't.

Unfortunately, imho the drive is dead. As I see it, you have a couple of options.

1. Send it in for repair (if it's under warrenty)
2. Purchase an external usb enclosure and a drive (cheap) or a brandname pre-built external drive.
3. If it's an older laptop, use this as an excuse to get a new one (christmas is comming).

Gord

---

### Post by kvonb on 2007-11-01
-

---

### Post by jlipoth on 2007-11-02
I also find upgrading to 7.10 from 7.04 better that a straight install of 7.10, but it's still seems kinda buggy.  7.04 has been the smoothest in my experience.  I think it's been frustrating for those of us who love using ubuntu  and have had major problems all of a sudden with the dawn of 7.10.  At least we only have to wait 6 months for another go at it (poor vista users - I really pity them).

---

### Post by andrebrait on 2007-11-02
7.10 is full of crap!

I found a lot of configurations in my xorg.conf file I never saw before.

I used theses Linuxes:
Kurumin 2.0~6.0 or something like that
Ubuntu 5.10, 6.06, 6.10, 7.04 and 7.10
Slackware 10.2 and 11.0
SUSe 6.(i don't rememeber)
Conectiva Linux (e RedHat based distro)
Mandriva 2007

And some other distros.

All f them worked... well, for me

I'm having problem I never had with 7.04
I passed all the day yesterday trying to make fglrx driver work in gutsy, in 7.04 just a few minutes!

I'll uninstall AppArmor... honestly... for what do I need it?
Additional security layer? Woul be good, but please, include it when it is STABLE and FUNCTIONAL.

---

### Post by Hallvor on 2007-11-02
Made a backup of my system before installing Xubuntu 7.04. Immediately god a lot of trouble with the wireless connection. (I have a Ralink rt2500.) Internet became unstable and slow, and then just died. Had to reboot to make it work again, before it became unstable and slow, and then just died - again. Reinstalled my saved disk image, and had my old system back in ten minutes... Guess I`ll wait for Hardy.

---

### Post by revan99 on 2007-11-02
> **gmc said:**
> Hi Revan99,

I've looked over the information you posted and I'm afraid it doesn't look good for the drive.



The BIOS and Linux agree on what brand/model of drive it is. 



Linux loads the appropriate driver for the drive.



I've seen errors like these from an external drive, where the door was obviously closed but the drive itself insisted that it wasn't.

Unfortunately, imho the drive is dead. As I see it, you have a couple of options.

1. Send it in for repair (if it's under warrenty)
2. Purchase an external usb enclosure and a drive (cheap) or a brandname pre-built external drive.
3. If it's an older laptop, use this as an excuse to get a new one (christmas is comming).

Gord

Hi Gord,

Thanks for looking into my problem. Unfortunately this is not a software problem...would be more cheaper to get it working. I think second option would be nice.

Thanks again,

Revan99

---

### Post by The Pinny Parlour on 2007-11-02
I have to say, there are many things I like about 7.10, but I have 1 major issue that is bugging me.  Top Panel is really badly justified to the right and no amount of resets/restarts seems to fix it.  It all started when I tried to remove the tick from 'Expand' in the top panel properties.  A restart rendered the top panel to the bottom, and ever since then I can't get it non-expanded and centered.  It's the biggest visual annoyance so far (that doesn't involve X).  I wish I knew how to fix it.

---

### Post by Johnsie on 2007-11-02
It's early days yet... The stable release has only been out a few weeks. I dont know of any desktop operating system that is quirk free so soon after a release. 

Windows Vista: Nealry a year down the line there are alot of problems
Leopard: Already having major security problems just after stable release.

It's always sensibile to wait a while after an operating system is released because the first stable version normally has teething problems.

---

### Post by AnthoMacP on 2007-11-02
> **Johnsie said:**
> I
It's always sensibile to wait a while after an operating system is released because the first stable version normally has teething problems.

That's true but it's not quite the way Ubuntu is supposed to work. Since it's only incremental builds of basically the same OS with new implementations you would assume that things would only get better, not worse. Also, because of the short release cycle, a 6 month wait for the OS to be in good shape is pointless since a new one will be released. This isn't a brand new GUI and totally new code from the ground up like say between XP and Vista but more just building off waht already exists. Things that worked before *should* still be working

---

### Post by Atlanta on 2007-11-02
Trying to install ubuntu right now, experiencing some major difficulties. It seems to be one problem after another... 

I'm not losing hope just yet, once I get this installed and everything is running smooth, I'll be good.... I'm hoping this OS will be relatively low maintenance.

----------------------------

Ubuntu is now up and running! Switched out the hard drive with another one, and from there, the install went smooth.

---

### Post by Gaunt on 2007-11-04
Yeah i second the graphics problem and also would like to add that a classic program like Amarok seems more prone to crash in Gutsy. The graphicsproblems are the most annoying part and since many people seem to have them I find it wierd that there has been no official comment from the Ubuntu team.

---

### Post by zippy028 on 2007-11-04
I have used each Ubuntu release since 6.06 and overall I would say breezy was the best for my system at the time. I switched to 6.10 after I built a new system and it was horrible, as was 7.04. I installed Gutsy about two weeks ago and had the lock-ups/freezes which in my case seemed to be related to the latest Nvidia driver and possibly my hardware but I seemed to have fixed that problem and I am pleased with Gutsy now and have begun to look into more customizations. I have never become a full time Linux user nor have I ever really made it beyond advanced newbie mostly because everyone else (kids, wife)reboots to XP the second they get on the computer because of games or windows specific apps or just the fear of change is what I suspect. One thing I have noticed since my first Linux experience (mandrake 7.1) is that their is always a new release which almost always comes with new bugs. If you are really looking for stability try Debian although, you may be using software that is three years old in the stable release. I will always upgrade and take my chances just because that is my nature and if it doesn't work out I re-install what did and go through the steps of making it how I had/want it. YMMV but it is important to remember  the developers do the best they can to support a countless number of unique hardware arrangements and peripherals and sometimes things fall short. Many times those shortcomings are the result of proprietary software and have little to do with the distro in question.:guitar:

---

### Post by ie_gwang on 2007-11-05
before im upgrade to 7.10, im using ubuntu 7.04 everything is ok. when im upgrade ubuntu 7.10 cant play any movie, sound is no problem....
what wrong with 7.10?
any one can help me....
thx before

---

### Post by DavidTangye on 2007-11-05
> I had the drive partitioned into several virtual drives – this saved my valuable files as /home is on one “drive”.Quite a few people do this, and it seems to me that this might be the cause of all sorts of problems after an upgrade. Under your home there are several .hidden directories containing all sorts of setup /configuration stuff for your account for the window manager, desktop, and applications.
When upgrading I always set up new, clean homes, and simply link back in those non-hidden subdirectories from the old setup that contain my files. These subdirectories are typically on another partition.  I also copy a few other items, such as the Firefox bookmark file, from .mozilla/firefox/.../bookmarks.html into the new subdirectory. I am sure that this approach has saved me from many of the problems that I see people having every six months when there is a new upgrade.

---

### Post by eugo on 2007-11-05
On the matter of worst experience, I think it boils down to the amount of computer knowledge the user has. For example, some things are easily done if you only have the experience. A new user would have to search and look and fall to get the same amount of experience.

I tried Ubuntu 7.04 and just installed 7.10 on a family PC (amd64.) Actually it was a resort because I had just formated and reinstalled WinXP when on reboot it gave me a hasty 'Disk read error'. I tried a number of things (chkdsk, fsck, fat32, fixmbr) with no luck, and decided to try Gutsy. The fresh install went fine, and family members find it easy to use. There are, as always, problems. My orinoco USB wireless card doesn't work, which then defeats the whole purpose of the fix. There is a workaround ($100 for a new card) but these kinds of problems are not Ubuntu's fault.

The biggest pitfall for Linux are consumer market device drivers. Many manufacturers do not release their source code because of Microsoft related marked deals (and other reasons) and therefore it is up to the Linux community to come up with a engineered driver.

I agree that there needs to be a central body for the Linux device driver development and sites like [www.linuxdriverproject.org]("http://www.linuxdriverproject.org") are getting it done, but it will take time. I also agree there needs to be a re-haul of the windows management.

---

### Post by meg23 on 2007-11-05
7.04 was really a milestone for Ubuntu and the Linux community. I don't know why its not getting 5 year support. Thats really disappointing. I upgraded to 7.10 and ended up having to fresh install Fiesty again. Gutsy is just no all there yet. Unfortunately, there is no way to revert back previous release. That would, however, would be a nice addition to Hardy Heron.

---

### Post by wPwLUi3N on 2007-11-05
working perfectly for me.........

Also always backup your data before you make any change in OS.

---

### Post by AnthoMacP on 2007-11-05
> **eugo said:**
> On the matter of worst experience, I think it boils down to the amount of computer knowledge the user has.

I don't wholly agree with that statement, In 5.04 when I first started using the OS I was stuck in the command line for a few days trying to install a proper version of my nvidia driver to get the whole thing working again, that was actually easier than Gutsy even though I needed a hell of alot more knowledge to remove the old conflicting driver and install a newer one in the command line. Same goes for my wireless drivers in earlier versions of Ubuntu having to use ndiscwrapper to get them running and spending a good 45 mins making sure I did everything right when now the drivers come preinstalled (although in Gutsy I needed to tweak them). I still rank those older builds above Gutsy because for me atleast, worst experience has more to do with the amount of work to get things functioning properly and how many things come broken to begin with. I had to fix atleast 10 things that weren't working quite right in Gutsy and was still getting freezes with the new nvidia driver (the old one would revert my screen back to 800x600) even after everything else was fixed. Had nothing to do with my knowledge, it was just a pain in the ***.

---

### Post by froy02 on 2007-11-05
All you have to do change your monitor to the right type and you'll get all the resolution and refresh rate supported by your monitor.

Right now your monitor is probably set to generic.

---

### Post by por100pre1 on 2007-11-05
I just made some small adjustments, like selecting my video card manually, no big deal. Ubuntu 7.10 is a big step in the right direction, it has been a bumpy ride for some users, but it is truly a move in right direction. I'm sure Ubuntu 8.04 will be even better. :)

---

### Post by Sockerdrickan on 2007-11-05
7.10 was fail for me so 8.04 has to be a LOT better.

---

### Post by Arthur Archnix on 2007-11-05
Points 1 and 3 from the absolute beginner forum sticky bear repeating:

> 1) Wait a month before installing the latest version of X,Y,Z distro after its release. That would give the devs some time to iron out some critical bugs that might appear after the release.

...

3) Go for Clean install instead of upgrade.
No matter which OS or distro, an upgrade may be a hazardous process, especially if you have non-official libs/apps installed or if you have heavy modified your OS.
If you kept to the official sources there should be no problem upgrading.

Another point they make is to have separate partitions. My personal favorite setup is something like this:
```
/dev/sda1   Windows (if present) ~ 5 to 30 GB
/dev/sda2   Linux 1 ~ 5 - 10 GB
/dev/sda3   Linux 2 ~ 5 - 10 GB
/dev/sda4   Linux Swap Partition ~ 1.5x RAM
/dev/sda5   Data ~ remainder
```

If you had 7.04 installed on your machine it would be, say, Linux 1. When 7.10 is released you install it as Linux 2. That way you can easily boot back into your stable and tweaked setup.

Rather than put /home on its own partition, just add a simlink where needed to your data partition in your home folder.

---

### Post by arkara on 2007-11-05
ubuntu 7.10 worked quite well for me.. the only problem i have is that my sound is not working.. this is easily  resolved by booting with acpi=off but i own a laptop and this takes away a lot of is functionality.
the thing is that this problem also was on ubuntu 7.04 so in the end ubuntu is a big disappointment for me....:(

---

### Post by AnthoMacP on 2007-11-05
> **froy02 said:**
> All you have to do change your monitor to the right type and you'll get all the resolution and refresh rate supported by your monitor.

Right now your monitor is probably set to generic.
Tried that, trust me i went through everything, the old driver was really a no go in terms of monitor support. Doesn't bother me thought 7.04 is working great for me

---

### Post by kvonb on 2007-11-06
-

---

### Post by FooAtari on 2007-11-06
I'm having lots of video problems with 7.10.  Im running Kubuntu.  Im not a huge fan of Gnome, but are both Ubuntu and Kubuntu likely to suffer from the same problems? Or can something like a video issue be environment specific?

---

### Post by raafaell on 2007-11-07
> **Tux0r said:**
> Hi I have to date used
6.06
6.10
7.04
7.10

This is how I would rate them from best to worst

7.04
6.06
6.10
7.10

It's interesting to see that the .10 versions "suck more"

My problem is I'm getting 640x480 mode only, with proprietary nVidia drivers 100.14.19

I installed them on my own first, after every reboot I got welcomed by the so called bullet-proof X layer, it told me a lot of stuff which was irrelevant and I could choose 640x480 or 800x600. Both of these modes where out of sync on my screen.(Congrats bullet proof X team)

Then I installed the driver on my own and it worked. But I'm only getting 640x480.

Time for fallback to 7.04 if no how to's are available!

maybe for you 7.10 is the worst, but not for me, i have had a lot of issues with 7.04, my system would crash each 3 minutes if using desktop effects, now i'm using Ubuntu 7.10 (Gutsy) on my amd64, and also I've installed gutsy on Acer notebook, with a ATI radeon 1100, and everything went ok, now i'm up to enjoy my desktop, without any problems.. Cheers. :popcorn:

---

### Post by cwill747 on 2007-11-07
Just updated to 7.10.

Problems galore

My display freezes up about once an hour. Still can move the mouse, but can't click. This didn't happen in 7.04.

Might fall back because i can't seem to fix this nor find a fix.

---

### Post by asphixmx on 2007-11-08
Well, well... I am not agree to score a whole version (7.10) the worst version just because you only can display 640x800 or having problems with your nVidia... the system is much more than that.

---

### Post by XopherH on 2007-11-10
I am finally 99% converted to Ubuntu 7.10 and its the best one yet.

no issues what-so-ever compared to the previous releases.  In fact this is the only one I've been able to re-create the same experience as I would have normally on win2kpro minus all the file manipulation, which is only a matter of finding the appropriate linux software or simply using my GRUB bootloader for a quick shared access drive conversion.

Intel D915PBL
P4 3.0ghz
1 GB RAM.
Nvidia GeForce 4

and it even reads from the SATA DVDR that "wouldn't communicate" in win2kpro.

---

### Post by mells on 2007-11-10
Wow my experience has been the other way around.

6.10 - Brilliant. Everything worked out the box, but system developed a hard crash problem after 12 months I think due to a software update. Gave up and waited for 7.04.

Used Linux Mint (Cassandra)

7.04 - Buggy, to many issues with ATI graphics and wireless so went to Mint.

7.10 - So far - Brilliant. Everything worked out the box. Little tweaking with the boot screen bug and slow interweb, but now its running better than 6.10.

---

### Post by cambirder on 2007-11-10
I'm seeing a similar low res problem, The odd thing is if I reboot I get full resolution back again.

---

### Post by coldstatue on 2007-11-13
> **Arthur Archnix said:**
> 


Rather than put /home on its own partition, just add a simlink where needed to your data partition in your home folder.

Can someone point me to a thread/tutorial? I can't find anything on this - in this situation. I already have a /home part, so this seems like an easy solution for a clean install - just turn /home to a data part, w/ home in / part. Insert simlink (that last bit is the part that confuses me.) Do i have to link to each file, or folder, or what? At what point do i do it, etc.? ...Lost on the logistics. 

I have a separate /boot part as well, so clean install is the only option I assume. I'm waiting for Hardy, but want to start researching now.

Thanks

---

### Post by potentia on 2007-11-13
> **eugo said:**
> On the matter of worst experience, I think it boils down to the amount of computer knowledge the user has.

That would explain the insignificant Linux market share. I would recommend that Linux just works, soon.

I am not a novice, my update was a disaster and the (time wasting reinstall) wasn't easy either.

Ubuntu has a problem. Users don't.

---

### Post by rundee_f on 2007-11-14
Lets not forget to appreciate for those who had develop Ubuntu in each release.. everyone has their own preferences... :) (so wise)

---

### Post by MNICY on 2007-11-14
I knew there would be problems updating.
What did i do?
Downloaded the new .iso, burned it to a CD and did a Clean install. (back up my data onto a storage partition).
Settings were easy to bring back, (also, i have fun setting up my desktop), and all in all i feel i saved myself alot of trouble.
Gutsy is amazing.

---

### Post by hutxubix on 2007-11-14
Hi!!

I have done two installations of Ubuntu 7.10:

First, an upgrade from 7.04 32 bits: lots of problems

Second, a clean install for 64 bits: It's just GREAT, AMAZING

THANKS TO ALL THE DEVELOPERS.

---

### Post by ~&#730;JaZ&#730;~ on 2007-11-14
> **Tux0r said:**
> Hi I have to date used
6.06
6.10
7.04
7.10

This is how I would rate them from best to worst

7.04
6.06
6.10
7.10

It's interesting to see that the .10 versions "suck more"

My problem is I'm getting 640x480 mode only, with proprietary nVidia drivers 100.14.19

I installed them on my own first, after every reboot I got welcomed by the so called bullet-proof X layer, it told me a lot of stuff which was irrelevant and I could choose 640x480 or 800x600. Both of these modes where out of sync on my screen.(Congrats bullet proof X team)

Then I installed the driver on my own and it worked. But I'm only getting 640x480.

Time for fallback to 7.04 if no how to's are available!


I had the same problems...for a long time...spend a lot of time in front of my machine...:(...at firs when i put my geforce graphic card in the gdm didnt wanna start at all...all i could do was mess around in the terminal, so i tried removing the original nv drivers and installing glx-new, that got novere....so i had to reconfigure the xorg....(strangely it was empty...from the beginig after i upgradet to gutsy), but i maneged to start x only at 640x480...then i maneged to install envy....that helped me a lot...i had to reinstall all drivers and start them manualy...but envy automaticaly reconfigured my xorg file..so mostly i have to thank alberto milone,,,so i gues most of the problems are in the xorg file...:> try reconfiguring it...if its not empty like in my case...still not sure how i maneged to lode it anyway...good luck with it

---

### Post by wjston on 2007-11-16
I did a clean install of Gutsy a few days after it's release. I had problems configuring my screen resolution past 800 x600. I followed a few guides and, after some frustrating moments, I was able to get my resolution up to 1024 x 768. I then installed some necessary codecs to view dvds; however, I was unable to load a dvd I just purchased. After some googling, I finally was able to view my dvd. I decided I would try and back it up but I gave up after numerous attempts using K9copy. This program worked great in Feisty, so I decided to reinstall. I went through the the complete process only to find out K9copy dvd's would not play in my home dvd player anymore (they worked great in the computer). I tried everything that forum viewers suggested to no avail. I also created a separate /home drive, but I never realized I should have moved my temp directory. I will be trying that next time. Having said all that, I have downloaded and installed Ultimate Ubuntu and after messing around with the 800 x 600 res problem again (use the Envy application under Application>System Tools>Envy), I configured my system to 1024 x 768 and downloaded/installed K9copy and backed up my dvd that I successfully played in my standalone dvd player.

My suggestion to anyone having problems with Gutsy is to try Ultimate Ubuntu, which I am thankful I found, and to continue adding information to this forum as this is what will propel Ubuntu to improve. I have cursed, I have struggled, and I have reinstalled; however, I have not sat behind a computer and programmed for endless hours so that lucky individuals like myself could be rewarded with free software. I agree Gutsy caused me some headaches, but I will wait and hope the next release will have fewer issues. However, I will continue to  run Ubuntu on my system in one form or another. I have only been introduced to computers since 2000 and, I agree that Microsoft has an edge, but I have been a supporter of the underdog all my 50 some years. I can honestly say that I presently use Ubuntu (in some form) to complete my everyday computer/entertainment tasks and I am thankfull that so many individuals contribute to this project....CUDOS.

---

### Post by wjston on 2007-11-16
I did a clean install of Gutsy a few days after it's release. I had problems configuring my screen resolution past 800 x600. I followed a few guides and, after some frustrating moments, I was able to get my resolution up to 1024 x 768. I then installed some necessary codecs to view dvds; however, I was unable to load a dvd I just purchased. After some googling, I finally was able to view my dvd. I decided I would try and back it up but I gave up after numerous attempts using K9copy. This program worked great in Feisty, so I decided to reinstall. I went through the the complete process only to find out K9copy dvd's would not play in my home dvd player anymore (they worked great in the computer). I tried everything that forum viewers suggested to no avail. I also created a separate /home drive, but I never realized I should have moved my temp directory. I will be trying that next time. Having said all that, I have downloaded and installed Ultimate Ubuntu and after messing around with the 800 x 600 res problem again (use the Envy application under Application>System Tools>Envy), I configured my system to 1024 x 768 and downloaded/installed K9copy and backed up my dvd that I successfully played in my standalone dvd player.

My suggestion to anyone having problems with Gutsy is to try Ultimate Ubuntu, which I am thankful I found, and to continue adding information to this forum as this is what will propel Ubuntu to improve. I have cursed, I have struggled, and I have reinstalled; however, I have not sat behind a computer and programmed for endless hours so that lucky individuals like myself could be rewarded with free software. I agree Gutsy caused me some headaches, but I will wait and hope the next release will have fewer issues. However, I will continue to  run Ubuntu on my system in one form or another because I have only been introduced to computers since 2000 and I agree that Microsoft has an edge but I have been a supporter of the underdog all my 50 some years. I can honestly say that I presently use Ubuntu (in some form) to complete my everyday computer/entertainment tasks and I am thank full that so many individuals contribute to this project....CUDOS.

---

### Post by ekravche on 2007-11-18
> **Tux0r said:**
> Hi I have to date used
6.06
6.10
7.04
7.10

This is how I would rate them from best to worst

7.04
6.06
6.10
7.10

It's interesting to see that the .10 versions "suck more"

My problem is I'm getting 640x480 mode only, with proprietary nVidia drivers 100.14.19

I installed them on my own first, after every reboot I got welcomed by the so called bullet-proof X layer, it told me a lot of stuff which was irrelevant and I could choose 640x480 or 800x600. Both of these modes where out of sync on my screen.(Congrats bullet proof X team)

Then I installed the driver on my own and it worked. But I'm only getting 640x480.

Time for fallback to 7.04 if no how to's are available!

Yep, 7.10 is a very unstable release...

The best one was 7.04.

I think I would rate them as
7.04
6.10
6.06
7.10
5.10
5.04

---

### Post by MNICY on 2007-11-18
I dont get how people are having problems with 7.10.
I had way more problems with Feisty then i do with Gutsy. :guitar:

---

### Post by scemmine on 2007-11-18
I agree with you, gutsy hasn't gone so far as they would have expected... I'm happy with feisty, that "has found her legs". But i still love dapper...

---

### Post by CalonDdraig on 2007-11-19
I'm afraid my own upgrade experience was less than perfect. 

After downloading all the updated packages, my system froze halfway through the upgrade process, the result being that I'm effectively running 7.04 with different artwork and less functionality. I say this because the main thing that doesnt seem to be working for me is anything which uses the USB Mass Storage convention. I get errors that look like: 

"Unable to Mount Volume" And more messages about wrong file system type or bad superblocks. 


Because of this I cant copy my files to an external hard drive and I'm wondering how I can roll back to Ubuntu 7.04 if possible because this is a nightmare... it feels very jerky and unstable even though most things work, they dont work as well as in 7.04. 

Btw, I've been a ubuntu user since 4.10:)

---

### Post by moe_syzlak on 2007-11-20
I am a Linux veteran of like 5 years strong. [-(

Gutsy has too many bugs: network, programs loading too slow, azureus crashing all the time, the same standard ubuntu theme(not really a bug but irritating). These annoying bugs have really set back Ubuntu against it's competitors, such as Mac OS, Windoze, and other Linux distros.

Someone needs to yell at Mark.:twisted:

---

### Post by emmamarie on 2007-11-20
I'm afraid that I'll have to agree with the titles sentiment.

I installed Gutsy, and it was nice, it ran smoothly and detected all of my hardware just as it should. However it went into a complete system freeze once a day for the three days that I put up with that till I reloaded feisty.

What would happen was that the screen would start scattering pixels downward (matrix style :D ) till the whole screen was filled with junk, at the same time me computer would start grinding and the mouse etc would freeze. Then when I tried to reboot (hard reboot) it would crash half a dozen times each time with a kernel panic caused by an unrecognised boot option.

I'm not a total bunny, but I simply couldn't work out what was causing it, I assumed at first that it was either evolution, xmms, or firefox, however the last time it crashed I was using only nautilus to move files about, so I'm thinking that it's probably x doing something weird looking for screen rates and resolutions, though why that would happen during a session is beyond me.

I've gone back to feisty as I need a stable system more than I need any updated software, unfortunately however it's just done the same thing in this OS (after a system update), which worries me considerably. I was getting uptimes in the weeks range previously in feisty, I don't get why the whole distro has suddenly become unstable on my PC (and no, I haven't changed hardware).

---

### Post by AnthoMacP on 2007-11-20
> **emmamarie said:**
> 
I've gone back to feisty as I need a stable system more than I need any updated software, unfortunately however it's just done the same thing in this OS (after a system update), which worries me considerably. I was getting uptimes in the weeks range previously in feisty, I don't get why the whole distro has suddenly become unstable on my PC (and no, I haven't changed hardware).

My computer happens to hate the newest version of nautilus and freezes due to that, freeze the nautilus packages in feisty and update everything else that might help, i had similar problems after updating feisty and had to do a reinstall. I, like you, also thought it was firefox or in my case rhythmbox. Hopefully with a complete refresh of all apps by the LTS release we'll be able to update :)

---

### Post by tahitiwibble on 2007-11-21
I'm new to Ubuntu and was absolutely stoked with 7.04. Since 7.10 I have a useless computer due to screen resolution issues that I can't fix.

---

### Post by whiskyprajer on 2007-11-21
I'll be re-installing Feisty in a few minutes; here are my difficulties with Gutsy:

FONTS - as detailed here: [http://ubuntuforums.org/showthread.php?t=581331&page=4](http://ubuntuforums.org/showthread.php?t=581331&page=4)

FILE TRANSFERS RESULTING IN FREEZE/SHUT DOWN - particularly when I'm transferring mp3s to my SansaDisk.

SCRIPTS - this one is the straw that broke the camel's back: Ooo Writer opens up and looks like this (see .png below).

My computer is a Dell Dimension 3100, Intel Pentium 4, Intel Graphics Media Accelerator 900. While Ubuntu remains my primary OS, I've partitioned the harddrive to allow for a little Windows gameplay, but that's all. I'm surprised there have been as many bugs as all this, but I'm not particularly bitter about it. I'll be happy to be back on Feisty, though.

---

### Post by whiskyprajer on 2007-11-21
I should add:

I originally upgraded to Gutsy, then did a fresh install (much better, but still problematic).

---

### Post by buntunub on 2007-11-21
Agree! 

Feisty = Brilliant release. 

Gutsy = WTH were they thinking????!!!

Its funny because ive seen alot of Gutsy supporters clamoring about "Every release has issues and the one before it is always the best release ever!" kind of stuff, but come on! Even taking that into account, all they really did with Gutsy was introduce more blatant bugs into the already over crowded, and underutilized Bugzilla. Its more like Gutsy was a stress test for the volunteer Bug Squad team than anything else lol!

Mark. Dude!.. Stability first, everything else after that has been thoroughly established via multi-platform beta testing and ALL bugs have been squished. Then release. Ok? Does anyone actually care about 6 month release cycles?? Not if those releases are junk they dont!

---

### Post by madscientist on 2007-11-21
I know this is a problems thread, but just to say: I've been using Gutsy since it was released (actually on one system I installed it the week before the release) and while I've had a few glitches here and there, overall it's worked very well for me.  One system I upgraded, the other I installed from scratch (because I wanted to redo the partitioning on that box anyway).  My fonts all look great; in fact I was really surprised at how much BETTER the fonts in Gutsy looked than the ones in Feisty.  On the upgrade box I did have a problem where the system wouldn't boot with the new kernel due to LVM issues (there's a bug about this) but that appears to have been fixed in the final release, and was easy to fix once I found the bug report.

My only problems have been video related, but none have taken much effort to fix; just a little dedicated searching.  First, in order to get my home video card (nVidia FX5500) to do video effects I had to add an option to xorg.conf.  Second, on my work system I couldn't get decent resolution on my LCD display because my monitor wasn't recognized: I had to go to the screen selection GUI and choose "Generic LCD", then it worked fine.  My suspicion is that a LOT of the problems with resolution people are having on this thread can be solved by choosing the right monitor type (or a generic one): most people probably are futzing with their video card config without realizing they should be looking to make sure the configured monitor is appropriate; most older monitors can't be queried.

The last problem I had last weekend and is apropos to your sig, buntunub: my CRT at home was dying so I bought a new widescreen LCD and when I plugged it in (via DVI) I could only get 1440x900, rather than the full 1680x1050 resolution.  After some unsuccessful searching I asked on the nvnews site and someone quickly told me to remove all the Mode lines that the "Screens and Graphics" app had added to xorg.conf when I configured the new monitor.  I took all that stuff out, restarted X, and voila!  Perfect!  So I do agree that that application needs some love--although I'm sympathetic because this has ALWAYS been one of the most difficult areas to configure.

Other than these glitches I'm loving Gutsy--and I DO care about the 6 month cycle because I am forced to use Evolution due to my company standardizing on Exchange for mail/calendaring (boo!), and I need every new version of Gnome/Evolution as soon as possible: previous versions are too buggy.

---

### Post by moe_syzlak on 2007-11-22
hey if anyone want to talk about ubuntu can IM me at tmantist on yahoo messenger

---

### Post by blop on 2007-11-22
Im glad to come across this post...i thought i was being silly!! 

 I have had numerous issues with Gutsy mainly around really weird network behaviour....loads and loads and loads of probs with samba....many hair pulling moments i can tell you. I thought i was doing something wrong......there is loads of nice bits in Gutsy but underneath it feels a bit wobbly. 

But luckily i imaged my working Feisty before i 'upgraded'....so i reinstalled and im back in love with Linux....it got to the point that i was screaming "this is almost as bad as XP!!". I was seriously considering going back...

Gutsy is just not ready....maybe in a few months...maybe in the next version...ill be back to it.

But i have learnt something....its not the bells and whistles its the functionality thats important!

---

### Post by MarkLori on 2007-11-22
I had problems with this which turned out to be bad monitor settings.  I had to put refresh rates in the xorg.conf file to even get a reasonable display.  Then go to the graphics settings from the main settins menu and manually select my monitor.  I now have any resolution I need, but the apps don't come up in a "window"  I have no borders to resize or even an x to hit to close an app.

---

### Post by MeanStreak on 2007-11-22
> **Tux0r said:**
> 
It's interesting to see that the .10 versions "suck more"


Thought this might be relevant, re: Ubuntu versions ([https://help.ubuntu.com/7.10/about-ubuntu/C/version-numbers.html]("https://help.ubuntu.com/7.10/about-ubuntu/C/version-numbers.html"))

"The **Ubuntu version numbering scheme is based on the date we release a version of the distribution.** The version number comes from the year and month of the release rather than reflecting the actual version of the software."

---

### Post by misfitpierce on 2007-11-22
I think gutsy is great. I think feisty was a bit more stable upon release and gutsy was not completely there. I however have not had freezing problems or anything but did have problem with bootsplash on restart. Fixed that and everything is fine now.

---

### Post by cluepon on 2007-11-23
*Sorry for the length of reply, I have said some of these things before, in other threads, but I think these things are worth considering and thinking about...*

I wouldnt call gusty a **complete** failure. But, to be sure, I think the wide extremes in reporting (it was great...it was horrible) are something everyone needs to look at. Gusty is not a failure...But, there are issues. I am an experienced computer user. Ive touched , used, tweaked and administrated many an OS over my 25 year career.

Updating for me, to 7.10 was a mini nightmare. I have spoken to a few people (including developers) who have stated, quite frankly: dist-upgrade is horrible, and needs alot of work. I was able to figure out a path to get things fixed on my own. But, as I upgraded, I kept thinking...knee deep in forums and command lines, every 10 minutes that passes while I do this, could be a frustrated user who goes to a M$ license. 

And that's the nasty little bug in alot of ears. Certainly mine, because I want ubuntu to succeed. Ubuntu is the best linux-desktop solution there is right now. It could be better, How it could be better, I will get to, but how about we look at some of the issues.

Let's cover some of the things said here: 

1) **The classic "user arguments". Such as Computer experience someone has, Linux isint for everyone,** etc. This dead horse is pulp. Stop whacking it. It needs to be buried. It's completely irrelevant with bug #1 is "Microsoft has majority market share" and the rabid pursuit of OEM deals for Ubuntu seats. 

Simply put: this is an excuse. plain and simple. Every time you say that, you're saying Ubuntu does not have the gust in its sails to compete on the end user desktop level. To compete with the crap M$ pushes down the throats of many. ***For those of you who will undoubtedly nitpick the last sentence, note***: I said ***compete*,** not ***replace*.** To be sure, Ubuntu is not windows, nor should it be. It IS different, but, to ignore that Windows is a successful OS, and that "all art is borrowed" is both ignorant, *and* foolish. 

Windows, for all it's faults, is a successful exercise in Operating Systems. Success in something does not always mean you have the best, typically (and especially in M$'s case) its the easiest way to get from point A to B. Microsoft has successfully sold an operating system people **KNOW** is flawed for alot of years now. That is Ubuntu's greatest advantage: people are at the point they want better, they want new. They want it to work. 

Ubuntu was designed to be user friendly, if tweaked systems cause upgrade problems, then developers should look at why these tweaks are made. Try to cover them. Try to tighten things up. Tweaks exist for a reason: to solve a percieved or real problem. This forum is littered with tweaks, and I would say a fair half to majority of them could result in having to re-install. 

Re-installing to solve problems is often a Microsoft/Vendor way of doing things. Ubuntu needs to try and move away from that methodology. Because, as we all know...re-installing an OS sucks. It sucks bad. 

Users take the path of least resistance. This is almost always the case. And, I think the Ubuntu folks are learning this, as evidenced by their working with the Automatix team in a more open and friendly fashion. To wit: automatix plugged a hole in the user experience. It was something that users turned to when they couldnt follow the flow of ubuntu to easily install things that brought Ubuntu up to a workable level with things (read: features and usability) people are used to having in windows. 

2) **Drivers: yes, the state of drivers is a mess in some places, but not in others.** In my (purely anecdotal) experience, for every bad driver ive encountered in the last 2-3 years, ive seen 10 that go above and beyond. 

A good example of this, is the v4l stuff. I bought a brand new revision card (pinnacle PCTV HD 800i), and out of the box, Ubuntu and v4l was able to use the card, without recognizing it. The use is ugly, but it is usable. Sure, there's no specific card description. Sure, I cant use all the features...yet. But it says alot about a driver when it can broadly use stuff like that. Thats a good thing.

Someone here said, "I suggest Ubuntu just "works"..and soon". I couldnt have said it better myself. Dist upgrading should NOT be a chore. People should not be afraid of the upgrade process. If there is a fear there, then it needs to be addressed. Just like other big issues need to be addressed. 

Maybe implement some kind of rollback function. So if something goes awry, you can restore the former state. While this does not solve all of the issues, it would give people an out. A way to undo, and get back to their former workability. 

I also think, some of these issues come down to an inferior testing process. No testing can ever be all inclusive. Ever. Because no one particular team of developers, not even Microsoft, can replicate what each and every user may or may not have. They might come close, but never ever close enough. The variables in a user base, were you to actually be able to calculate them, would give us all nightmares, and reduce us to crying fits while sucking our thumbs. 

But, what shocks me about Ubuntu, is that sometimes I see flagrant stuff (like, in my case, the dist-upgrade hanging...its a known bug, that nobody has really addressed) that probably could have been caught in testing. 

Perhaps Ubuntu should switch to releasing yearly, and tighten up the testing protocol. 1 release a year, with maybe 1 or 2 "service pack" type releases. 

I am looking forward to 8.04. And, I am even reasonably happy with 7.10. But, what I really want is stability. I upgraded to 7.10, just a week ago. I never upgrade right out of the gate, I tend to wait to see what shakes out first. I do, however, when I have time try to run live disks, or test in virtual environments.

Better testing, more focus on filling the holes in the user experience and usability, and more focus on tightening things up. I like new features as much as the next guy, but as Mister Scott said: the more you over think the plumbing, the easier it is to stop up the drain. 

I love new features, but I would gladly wait on them, if it meant a tighter, better tested package with more bugs killed. 

I think it's a mistake to try to do too much at once, and I get the feeling that some of that is what's going on in ubuntu development these days. This race will not go to the swiftest, per se...but the one who has more of their ducks in a row. It's a difficult balancing act. But, I think the community has the gumption to do it. =)

Just my $10.02

---

### Post by thorwood on 2007-11-23
I had big problems with Drake but feisty fixed that...ah Feisty was great. I did an upgrade install  but that went awry, fresh install definitely better, but nautilus still crashes!

---

### Post by madscientist on 2007-11-23
> **MarkLori said:**
> I had problems with this which turned out to be bad monitor settings.  I had to put refresh rates in the xorg.conf file to even get a reasonable display.  Then go to the graphics settings from the main settins menu and manually select my monitor.  I now have any resolution I need, but the apps don't come up in a "window"  I have no borders to resize or even an x to hit to close an app.Having no window borders doesn't have anything to do with your monitor or video card settings: it means your window manager is not working.

I had this same problem, when I tried to use compiz (Desktop Effects) with my nVidia card.  Have you tried disabling them (use System -> Preferences -> Appearance)?  If you do have window decorations after you disable desktop effects but not with them then you may well have the same problem.

If you have an nVidia card, then first you'll need to use the restricted drivers version of the nVidia driver; the free one did not work for me at all with desktop effects (compiz).

Then, I had to edit the /etc/X11/xorg.conf file with a text editor (you'll have to do this with sudo; try opening a terminal from Applications -> Accessories -> Terminal then running something like "sudo gnome-text-editor /etc/X11/xorg.conf").  Then find the section "Screen" and add the line:
```
 Option          "AddARGBGLXVisuals"     "True"
``` then log out and back in (you should see the nVidia announce screen; if not log out again and back in) and see if that helps.  If you don't have an nVidia card or you have this problem even without desktop effects enabled then there's a different issue.

---

### Post by madscientist on 2007-11-23
> **cluepon said:**
> Updating for me, to 7.10 was a mini nightmare. I have spoken to a few people (including developers) who have stated, quite frankly: dist-upgrade is horrible, and needs alot of work.
[...]
Users take the path of least resistance. This is almost always the case. And, I think the Ubuntu folks are learning this, as evidenced by their working with the Automatix team in a more open and friendly fashion. To wit: automatix plugged a hole in the user experience. It was something that users turned to when they couldnt follow the flow of ubuntu to easily install things that brought Ubuntu up to a workable level with things (read: features and usability) people are used to having in windows. 
[...]
But, what shocks me about Ubuntu, is that sometimes I see flagrant stuff (like, in my case, the dist-upgrade hanging...its a known bug, that nobody has really addressed) that probably could have been caught in testing. 

I agree with most of what you say.  In particular, it always cheeses me off as well when people say "well Linux is not for everyone".  What a crock!  Listen, I've been programming on UNIX since 1985 (!!) and Linux since 1993.  I've been using open source since before Linus ever wrote the first line of the kernel, back when it was actually *hard* to build from source code.  And the state of Linux today WRT usability is nothing short of astounding--it's far more usable and user-friendly than older versions of Windows, and I don't remember anyone saying that Windows was only for experts, back in the 1990's!

But anyway, to your points above:

First, when you say "dist-upgrade" I hope you don't mean running "apt-get dist-upgrade" or even "aptitude dist-upgrade".  These are NOT supported ways of upgrading Ubuntu!  That method is KNOWN NOT TO WORK.  It has never been advocated as an upgrade method for Ubuntu and none of the official upgrade methods recommend it.  Rather, you MUST use the update manager to upgrade to your new release.  Dist-upgrade is a *Debian* feature and although Ubuntu is based on Debian, it is not Debian.  Frankly, people using dist-upgrade who then complain that it didn't work don't get any sympathy from me, with one exception as below.

Second, you mention dist-upgrade "hanging".  I do know that there is or was a bug where the update manager didn't work properly to upgrade to new releases, but this bug happened ONLY on Kubuntu; it never happened on Ubuntu.  You talk about Ubuntu, but if you're really using Kubuntu then this might have impacted you; in this case using dist-upgrade is understandable.  I don't use Kubuntu so I haven't followed this but I think it was tracked down to some kind of issue with Qt or something.  In this case I don't think your disappointment is quite justified.  Kubuntu is not Ubuntu, and the team that puts it together is a different team.  It's provided by the Canonical folks but I don't think it has quite the same status.  So, blaming the Ubuntu folks for not finding a bug that appeared only in Kubuntu doesn't seem fair.  Of course, if you're using Ubuntu and saw a hang in the update manager there then I'm completely off-base... never mind!

Lastly, Automatix: the problem everyone had with Automatix is not with its goal, it's with its methods.  Automatix was just a hack.  It COULD have been done well, in such a way that it was a real benefit.  But in reality it actually BROKE many/most of the systems it was installed on.  Of course, users generally wouldn't realize their system was broken until they tried to upgrade it... then they'd blame Ubuntu rather than Automatix.  I agree it would have been better if Ubuntu had included the current features for installing extra software and Automatix had not been necessary, but this is a difficult and complex problem and I'm not surprised it took a while to get a solution everyone could live with.

Cheers!

---

### Post by madscientist on 2007-11-23
One thing I wanted to say: I do hope that everyone who is having problems is REPORTING these problems!  When you find a bug you should search the bug database and see if someone else already reported it; if so, add a "me too" with some relevant info and subscribe to the bug so you get notified of changes to it.  This helps the developers know which bugs are more common and how many people they impact.  If you don't see the bug, report it!  Again, provide as much detail as possible but even if you don't know what detail to provide, report the bug (someone may well get back to you with specific requests for info--if so, reply and provide that info!)

The reality is that a system like Ubuntu is incredibly complex and the environments systems live in vary so widely that it's impossible for all combinations to be tested by the developers.  Obviously the tests they've run have not exposed the bugs you're seeing, or they likely would be fixed already.  The only way that Hardy will be better than Gutsy is if everyone who has problems with Gutsy REPORTS the problems and, ideally, helps with the problem resolution.  If you don't report it then don't be surprised if it doesn't get fixed.  In Open Source, the squeaky wheel truly does get the grease.

Cheers!

---

### Post by cluepon on 2007-11-23
> **madscientist said:**
> Kubuntu is not Ubuntu, and the team that puts it together is a different team.  It's provided by the Canonical folks but I don't think it has quite the same status.  So, blaming the Ubuntu folks for not finding a bug that appeared only in Kubuntu doesn't seem fair. 

I should have been more clear, and yeah, I do use KDE. My install is simply ubuntu with kde-desktop installed from the metapackage. 

Gnome is too limiting for me. =)

Kubuntu has official status. Period. It's not a red headed stepchild. The status of it is simple, and answered by the FAQ: 

[B]Is this a fork of Ubuntu?

No, it is an official part of Ubuntu. All our packages are in the same archives.[/B]

It should be noted also that if you look at the blueprints/milestones for Hardy, one of the goals is getting Kubuntu caught up. ([https://blueprints.launchpad.net/ubuntu/hardy](https://blueprints.launchpad.net/ubuntu/hardy))

This is not a blame ubuntu or blame kubuntu situation. It's the same folks, in different specializations. To me, as I see it, thats like trying to say you cant blame the folks in charge of the shape and direction of the distro for what their own team on X.org does in relation to the distro. For what it's worth, kubuntu is ubuntu with KDE instead of gnome. Of course it's different, but the underlying OS is the same. Same with Xubuntu,

For what it's worth, I was using the upgrader via adept. And, what's more, the hang occured while the backend, and not the front end was working.

There are other little issues, like module-assistant totally depending on apt, when I am fairly convinced aptitude would be better, etc...the bottom line is, environments aside, alot of these things are rooted in the back, and not the front. 

> **madscientist said:**
> Lastly, Automatix: the problem everyone had with Automatix is not with its goal, it's with its methods.  Automatix was just a hack.

Oh, I agree their methodology wasnt great. But I try not to use weasel words when I discuss this. 

After all, alot of "hacks" are the result of people trying to kludge together solutions to solve problems. And history is replete with examples of "hacks" becoming quality products and usable things. 

And many would point to Linux as the chief example of how a hack can grow legs and become something. =)

> **madscientist said:**
> It COULD have been done well, in such a way that it was a real benefit.  But in reality it actually BROKE many/most of the systems it was installed on.  Of course, users generally wouldn't realize their system was broken until they tried to upgrade it... then they'd blame Ubuntu rather than Automatix.  I agree it would have been better if Ubuntu had included the current features for installing extra software and Automatix had not been necessary, but this is a difficult and complex problem and I'm not surprised it took a while to get a solution everyone could live with.

Again, I try not to get into pointing a finger at people. I think the Automatix debacle had villans on both sides of the argument. The bottom line is, out of it grew the idea that working towards a common goal was better than working against each other. Which is another thing that the blueprint shows: work together with team automatix. ([https://blueprints.launchpad.net/ubuntu/+spec/automatix-ubuntu-team-collaboration](https://blueprints.launchpad.net/ubuntu/+spec/automatix-ubuntu-team-collaboration))

Because, at the end of the day, saner and cooler heads prevailed. I think it's a bit disingenuous to lay all the blame at the feet of the AX devs. There are always three sides to a story: Your side, their side and what it actually is. Of course even then, it's all subject to perspective. =)

I say that, having installed systems with Automatix, and without. I also say that, having seen bad behavior on the part of the AX Team, and seeing alot of weaselly talk here on these forums about AX. Neither of those are conducive to getting the job done and solving the underlying issues. Again, I am glad to see cooler heads prevail.

In any event, the main idea of my argument is: we have a usable system, that's a pretty good thing. Lets take some time out, worry less about eye candy, and tighten up the bike before we add more spinners and chrome.

---

### Post by madscientist on 2007-11-23
> **cluepon said:**
> For what it's worth, I was using the upgrader via adept. And, what's more, the hang occured while the backend, and not the front end was working.I don't know much about Adept; does it have an Ubuntu-specific release upgrade facility?  In Synaptic, for example, there is no such thing; the only supported, correct way to upgrade to a new release in Ubuntu is to start the update-manager in such a way that it shows you "New release available, do you want to install?" (typically by adding the -c and -d options) and click the button to install.  No other upgrade method is supported.  This is because the update-manager performs extra operations during that processing that normal dist-upgrade, even if run from Synaptic, does not do.

If the Adept folks have introduced an interface to that same process update-manager uses it should work (and is a bug otherwise). If not, it's not supported.

> **cluepon said:**
> Oh, I agree their methodology wasnt great. But I try not to use weasel words when I discuss this.Well, in my first draft I said Automatix was badly written.  Is that better? :)

> **cluepon said:**
> Again, I try not to get into pointing a finger at people. I think the Automatix debacle had villans on both sides of the argument..I'm not talking about the politics of Automatix.  I'm talking about the implementation.  I agree you can argue about who was or wasn't to blame about the state of the relationship between Auotmatix and Ubuntu, but you can't argue with the fact that Automatix did not follow basic packaging and installation principles, and that it caused peoples' systems to break as a result.

> **cluepon said:**
> In any event, the main idea of my argument is: we have a usable system, that's a pretty good thing. Lets take some time out, worry less about eye candy, and tighten up the bike before we add more spinners and chrome.IMO that's the job of the LTS releases.  Interim releases like Gutsy are for adding spinners and chrome: most of the time you simply CAN'T find all the places that need tightening before you get the bike out there to be used by lots of different people in lots of different situations.  Obviously you'd prefer it if the wheels didn't come off as well but you've got to take chances and if you are releasing every six months, you don't always have time to completely validate all those chances before they go out the door.  Luckily, Hardy is targeted to be an LTS release so I'm sure you'll see a lot more nut and bolt tightening and a lot less new chrome in that release.

But as I said earlier, if you (the generic "you", not "you, cluepon") want to be sure the bolts that are causing your particular rattle are tightened, you need to report the rattles rather than silently suffer them (or silently return the bike).

Cheers!

---

### Post by conehead77 on 2007-11-23
> **madscientist said:**
> 
First, when you say "dist-upgrade" I hope you don't mean running "apt-get dist-upgrade" or even "aptitude dist-upgrade".  These are NOT supported ways of upgrading Ubuntu!  That method is KNOWN NOT TO WORK.  It has never been advocated as an upgrade method for Ubuntu and none of the official upgrade methods recommend it.  Rather, you MUST use the update manager to upgrade to your new release.  Dist-upgrade is a *Debian* feature and although Ubuntu is based on Debian, it is not Debian.  Frankly, people using dist-upgrade who then complain that it didn't work don't get any sympathy from me, with one exception as below.
Cheers!
Didnt know that and i have seen lots of people recommending dist-upgrade, thanks for pointing this out.

---

### Post by john_spiral on 2007-11-23
I've had the following problems with a fresh 7.1 GNOME install over the last 2 weeks.

(1) Resolution changing between boots.
(2) After changing my resolution I'm unable to shut the machine down as the power button doesn't react to my clicks. ALT + F1 to reboot.
(3) Switching users eventually looses a session.
(4) Unable to use a keyboard to navigate in the Open Office Writer Save screen.
(5) The volume control in Rhythm box remains on screen even though app is a few screens back.
(6)Firefox crashes

there have been more....

7.04 seemed more stable.

Looks like there should be more user testing before releases?

---

### Post by madscientist on 2007-11-24
> **conehead77 said:**
> Didnt know that and i have seen lots of people recommending dist-upgrade, thanks for pointing this out.I know, I've seen this everywhere as well.  And right beside it you typically see a list of bitter complaints about how using dist-upgrade "broke the system" and how Ubuntu sucks because they can't get upgrades right.  Some people have legitimate problems with upgrades, no doubt, but if you're not using a supported upgrade method then you're not one of them.  All you have to do is read the release notes:

[https://wiki.ubuntu.com/GutsyGibbon/ReleaseNotes](https://wiki.ubuntu.com/GutsyGibbon/ReleaseNotes)

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

These are simple, easy-to-read documents not long-winded books.  Before doing something as major as upgrading your operating system it seems like spending 10 minutes reading the release notes would be a good idea :cool:

---

### Post by madscientist on 2007-11-24
> **john_spiral said:**
> I've had the following problems with a fresh 7.1 GNOME install over the last 2 weeks.

(1) Resolution changing between boots.
(2) After changing my resolution I'm unable to shut the machine down as the power button doesn't react to my clicks. ALT + F1 to reboot.
(3) Switching users eventually looses a session.
(4) Unable to use a keyboard to navigate in the Open Office Writer Save screen.
(5) The volume control in Rhythm box remains on screen even though app is a few screens back.
(6)Firefox crashes

The only one of these I've seen, I think, is #3; what does "looses[sic] a session" mean exactly?  I have seen a situation where when you change to another user you get a completely white screen.  However, this is a video artifact: the session is not lost.  In fact if you type your password at that white screen and hit enter, just as if the password dialog was visible, you'll get your session back just as it was, with no ill-effects.

I've also seen something where the user switch seems to get confused and switch to the wrong virtual terminal; then you get a blank screen with just a blinking cursor at the upper left.  In this case, you can use C-A-Fn where n is 7, 8, 9, 10, etc. to find the right virtual terminal for that user.  This happens much less often.

These are annoying, to be sure, but not serious.  Cheers!

---

### Post by john_spiral on 2007-11-24
> **madscientist said:**
> The only one of these I've seen, I think, is #3; what does "looses[sic] a session" mean exactly? ....

I choose **Switch User** when logged in as ubuntu1, login as say ubuntu2

logout as ubuntu2

and then attempt to login as ubuntu1 and it gives me a clean session, surely it should re-connect me to my initial session?

---

### Post by CalonDdraig on 2007-11-24
There wouldn't happen to be a *Distribution Downgrade* tool out there would there?

No seriously, for some reason I cant find my 7.4 installation disc. Is 7.4 still available for download?

~CalonDdraig

---

### Post by AnthoMacP on 2007-11-24
> **CalonDdraig said:**
> 
No seriously, for some reason I cant find my 7.4 installation disc. Is 7.4 still available for download?

~CalonDdraig

[http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/) google is your friend :lol:

---

### Post by samuraiCat on 2007-11-26
> **madscientist said:**
> I know, I've seen this everywhere as well.  And right beside it you typically see a list of bitter complaints about how using dist-upgrade "broke the system" and how Ubuntu sucks because they can't get upgrades right.  Some people have legitimate problems with upgrades, no doubt, but if you're not using a supported upgrade method then you're not one of them.  All you have to do is read the release notes:

[https://wiki.ubuntu.com/GutsyGibbon/ReleaseNotes](https://wiki.ubuntu.com/GutsyGibbon/ReleaseNotes)

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

These are simple, easy-to-read documents not long-winded books.  Before doing something as major as upgrading your operating system it seems like spending 10 minutes reading the release notes would be a good idea :cool:

Okay, but to be fair, what exactly does one expect people to do when they see a button saying an upgrade is available? It doesn't say, "Ubuntu 7.10 Available -- Click here to read up on it first, slackass!"

---

### Post by madscientist on 2007-11-27
> **samuraiCat said:**
> Okay, but to be fair, what exactly does one expect people to do when they see a button saying an upgrade is available? It doesn't say, "Ubuntu 7.10 Available -- Click here to read up on it first, slackass!"They should press the button.  That's the approved way to upgrade your system.  I agree it would be really nice if the upgrade tool contained a hyperlink you could press to jump to the release notes: that's something you should add as an enhancement/usability request in Launchpad for the update-manager tool.

What I'm talking about is all the folks coming from Debian and various other Debian-based systems, or else getting advice from other people coming from such systems, who "know" that the right way to upgrade to a new version is to run "apt-get dist-upgrade" (or "aptitude dist-upgrade").  Those are NOT the right way to upgrade Ubuntu.  Even more irksome than those folks doing it to their own systems is how often they post to these forums, mailing lists, etc. telling other people that they should also use this unsupported method.

---

### Post by MNICY on 2007-11-27
I hate upgrades. They seem to always screw up.
I just did a clean install. Worked much better :) :guitar:

---

