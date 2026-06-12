---
title: "Is this first time user exp normal???"
date: 2020-05-03
forum: Ubuntu, Linux and OS Chat
---

### Post by spdkils on 2020-05-03
I've been Linux curious for years. I installed 14.0 16, 18, 20, version of Ubuntu. Ran some minecraft servers, some ssh, some GNS 3, various other things, even a proxy service or two.

I thought hey it's 2020, lets try it on my desktop instead of just VMs. So I installed it on a thumb drive, using simple MBR boot, after a week, installed it on my oldish 2015 laptop.

What I learned after 7 days of non-stop tinkering.

Video Issues
Web and GPU Support
[LIST]
[*]Can't play netflix
[*]Youtube videos seem to CPU render (chrome://gpu, and firefox about://support)
[*]Applications that use your GPU say, roll20.net for rendering LOS and shadows are terribad slow, or only use built in graphics.
[*]Can't select NVIDA driver for web with right click after installing proprietary driver.
[/LIST]

Gaming
[LIST]
[*]Screen tearing, or folding when moving vertical on game that have Linux builds.
[*]Terrible user experience trying to install Vulkan, or even finding info on what supports what.
[/LIST]

Drivers (Things get strange)
[LIST]
[*]Monitors swap positions before and after login. (Yes copy more manual XML files to seemingly archaic places on your computer)
[*]If you're booting use UEFI you have to now deal with a boot menu to try and add keys, or hashes, and what file should I pick? Why did I have to type passwords? What is going on with boot now that I changed a video driver? (I know basically, but the process is cray cray)
[*]The boot splash screens change resolution, and look like garbage, but they were pretty before, why does it go so wonky? I'm sure there is a file in 10 strange places, to maybe fix it.
[/LIST]
Sound
[LIST]
[*]Change the default playback device is not "sticky" by default. You have to use commands, and edit config files to make it persistent.
[/LIST]

Installation of Software
[LIST]
[*]What a nightmare this is. From drivers, to just simple things like a web browser, everything has 4 layers of complexity.
[*]Sure I can install firefox from the installed application library, but it's already installed I guess with apt-get
[*]But wait, neither version lets me click links out of VSCode without a crash, so I should install something else?
[*]Oh and what about this GD-launcher for minecraft, oh it doesn't work on snap package, but there is the applite thing that just does?
[*]Oh I have java installed, but I have to run this other command to figure out what version this symlink is pointed at?
[*]I have a path, but a different path is bash, for different things.
[/LIST]

I got more obscure as the list went on but, you can't even use the web out of the box. BASIC things like being able to play video without 40% CPU overhead, BASIC things like netflix and chill... BASIC things like selecting the default audio device. BASIC updating a video driver without going into UEFI crazy land and boot going to hell.

Bad ass terminal.... great for scripting, and coding.... Great where Windows Sucks, Sucks where Windows is great.

---

### Post by Autodave on 2020-05-03
So far, I have installed 20.04 on 6 different machines: 4 desktops and 2 laptops/  Not a single problem with any of them. No working in the terminal to get things working.  Install, reboot, everything works.

You certainly are having WAY more issues than the average person.  The 2 GPUs in your laptop WILL cause problems.  There are fixes for that problem, but they are above my pay scale.

I believe that once the 2 GPUs are sorted out, most of the rest of your problems will be gone, also.

You need to remember that when you were running Linux in a VM, Window drivers were installed and working.  Now, a little tweaking or installing a driver or two will be needed.  This is normally NOT the case though.

---

### Post by jimjeater on 2020-05-03
Hi,

Are you able to provide info on your graphics cards, hardware model/version, drivers etc.

Jim

---

### Post by jimjeater on 2020-05-03
Also, thinking about it, when I've run it from a USB without installing it doesn't use the 3rd party drivers, this can make websites not function correctly.  Has this  definitely been installed onto the hard disk and was the 3rd party option ticked on the installer?

---

### Post by wildmanne39 on 2020-05-03
*Thread moved to **Ubuntu, Linux and OS Chat since this is not a support request**.*

If you would like support for these issues please start a thread in the appropriate sub-forum and have only one issue per thread, please state the specs of your computer, what you have tried and installed from possible third party sources, remember linux is not windows there is a learning curve and sometimes it requires a little effort to get things to work properly since drivers or not written by the vendors of computer hardware to run on linux like it is on windows but we are here to help if you need it you just need to ask and supply the info needed to help you.

---

### Post by crip720 on 2020-05-03
Would say not regular experience.  Have used different laptops over the years and most of them just had to burn ISO and install and everything good.  One old P4 still using, did have trouble between 12.04 and 16.04.  The versions in between did not like the graphics for some reason, running 18.04 now.  Your problems are probably something to do with your hardware and Ubuntu not liking each right away.  As others have said your computer specs will go a long way to getting good advice.

---

### Post by jared-plus on 2020-05-03
Not really. Though most problems I had with Linux and the BSDs came mostly from the Nvidia drivers. In my case, a simple kernel upgrade fixed the issue. If I may ask have you enabled Nvidia's proprietary drivers from the additional driver program and have you picked to install third party applications from the installer?

---

### Post by Hwæt on 2020-05-03
IIRC actual Google Chrome and Firefox are capable of playing Netflix. I'm not sure about Chromium. What browser were you using?

---

### Post by mastablasta on 2020-05-04
well this is my experience - 

i have 3 PCs. one is a laptop from 2012 (dual booting Linux with win7), the other two desktops i assembled myself. one in 2004 (my main PC - winXP) and the other younger one in 2011 (linux since major renovation in 2011).

Laptop got linux in the same month or next month that i bought it. it worked more or less flawlessly. I was worried about AMD not supporting the GPU anymore, but opensource driver works well now. windows needs a lot longer to boot and despite being Win7 Starter it takes up more ram than Kubuntu and uses disk excesively on start.

last year i decided to install Kubuntu on 16 year old WindowsXP machine. this was my main PC, i already reserved half of the drive. I got scared about MBR being too small. so i got an extra hard disk. install was smooth. i had issues as it didn't boot to monitor but to TV (same was on WinXP with this nvidia 730 GPU) and the DPI was too small. anyway i solved it in system settings. and then i started with basic stuff install, then some PoL games and finally Steam and games from Steam at the request from the kids. pritner and all that worked just as it should. no issues since OS install until this year when i struggled a bit to get the correct sound input&output. finally i understood the settings and managed to make it switch to handphones when they are plugged in. this was the only thing that windows did better.

Linux boots faster (45 secs compared to 10 mins on winXP), is faster, uses less ram and utilises all 4GB of RAM (widnows was with 32bit PAE kernel and had some limits, though it did use the whole RAM. Minecraft works better and faster, most of the old games work, i have all applications i need and use. the only one i miss a bit is MS Office. i can play games that need windows 7 or 8 or even 10. not sure i can even install those OS on my PC.

the other younger PC started to have more and more issues. final straw was when i started turning itself off. i decided to use the PSU and hard disks and get a new PC. the kid payed for it, i paid for a new monitor. we got a ryzen 7 2xxx series and GTX1650. anyway the only issue i had was that monitor was not recognised at first. not sure what happened, but i switched the HDMI cable and then switched it back and it all worked. everything works as it should. we have a bunch of windows games on it - though mostly older since i don't have money for new ones (COD2, COD4:MW, CODMW2, Quake2, Halo...) and we added a couple more from Steam. i also managed to get some native engines going (OpenMW, Quake4 and Doom3...). 

my point is there are no issues so far. it acts like any other OS would.

---

### Post by spdkils on 2020-05-04
@ Hwaet after a while of looking the netflix is Chromium! I did figure that out....
It doesn't ship with the DRM installed.

It doesn't explain my other GPU problems with firefox. :(

I only started messing with video drivers because it wasn't "acting" normal when using web apps that I use commonly when booted into windows.

---

### Post by spdkils on 2020-05-04
Generally, I'm fairly happy with Linux. I like several key things about it....

But when you pay for a 1080TI you want it to work. You want to be able to play game titles that are native to linux (Factorio for example) and actually not have screen tearing etc.
So what do you do when you have problems like that??? You update the drivers!
What happens when you update drivers on Ubuntu?

Well you run into UEFI areas...
Your login screen changes left/right multi-monitor swaps.
You lose the 'hi-res' splash screens.

Why else do you upgrade drivers? Using web_gl and other GPU web site applications. (Like dynamic lighting in Roll20)

This was a pretty painful process to try and sort it out, and I still haven't figured out some of them, because the complexity and confusion with SOOOOOo many options. There are crazy amounts of browser things you can install. They have supposed GPU  working for video decoding, or this or that. With Windows.. I install Firefox, and latest drivers directly from NVIDIA and I'm done... Nothing else needed... No custom compiles, no alternative patches, nothing to fiddle with. It just works. It doesn't matter if I'm on windows 10 build 1500 or 1800 or 1909. It just works.

---

### Post by poorguy on 2020-05-04
[SIZE=3]***@spdkils ***[/SIZE] 

[SIZE=3]***A good read.***[/SIZE]

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)[SIZE=3][/SIZE]

---

### Post by TheFu on 2020-05-04
If your goal is gaming, go back to windows. That is the platform that all the hw and game software vendors target.  Linux will never be the primary platform.  Linux has a completely different philosophy than other OSes, which can be frustrating for people who just want things to work easy< without regard for politics or sw licensing.

For example, I don't want any msft code or proprietary DRM code on my systems.  I'd rather not use netflex streaming than be subjected to that.

Your system seems to have Secure Boot enabled.  That's why driver updates require a password.

Expecting Linux to behave like Windows is asking for frustration.  Just a reminder.  HW issues with drivers need to be taken to the vendors.  They make the drivers for all OSes.  Generally, only the drivers automatically installed through the ubuntu driver update should be used.  Going to the vendor's site usually is a bad idea.  Intel gpu drivers are automatically installed and maintained.  Most of my systems use those.  I have one system with an nvidia 1030 card.  There is a program, ubuntu-drivers, that should load the correct proprietary drivers for LTS 18.04.  There is a release note warning about using nvidia proprietary drivers for 20.04.  Check the release notes.  Complain to nvidia.

Wish I had better advice, but you and I are completely different types of users.  The way I use my 20 or so systems seems to be completely different from how you expect them to work.  For example, I don't use browsers for video. Webgl security is terrible, so I've disabled it. [https://threatpost.com/researchers-warn-security-issues-webgl-standard-051111/75222/](https://threatpost.com/researchers-warn-security-issues-webgl-standard-051111/75222/)
We have media playback devices running osmc for that or a roku.  The roku is heavily firewalled to limit tracking as much as possible.  Most of the time, that's good. But not always.  Some searches don't work.  Security often impacts usability and convenience.

---

### Post by wildmanne39 on 2020-05-04
I see you still have not started a thread, one for each of your issues in the proper sub-forum to get help fixing these issues, until you do you are just making it harder on yourself trying things that may make matters worse.

---

### Post by Shibblet on 2020-05-06
> **spdkils said:**
> I've been Linux curious for years. I installed 14.0 16, 18, 20, version of Ubuntu. Ran some minecraft servers, some ssh, some GNS 3, various other things, even a proxy service or two.

I thought hey it's 2020, lets try it on my desktop instead of just VMs. So I installed it on a thumb drive, using simple MBR boot, after a week, installed it on my oldish 2015 laptop.

What I learned after 7 days of non-stop tinkering.


With no offense intended:  This sounds like a Windows user having a difficult transition to a different type of OS.  One of the most difficult things Windows users deal with, is how things are done differently in Ubuntu.  I count myself among  these people, as I still have issues from time to time.

> **spdkils said:**
> Video Issues
Web and GPU Support
[LIST]
[*]Can't play netflix
[*]Youtube videos seem to CPU render (chrome://gpu, and firefox about://support)
[*]Applications that use your GPU say, roll20.net for rendering LOS and shadows are terribad slow, or only use built in graphics.
[*]Can't select NVIDA driver for web with right click after installing proprietary driver.
[/LIST]

[LIST]
[*]Netflix should work in Firefox, no questions asked.
[*]YouTube renders within the browser, and the browsers do not have VHAPI or VDPAU built in.  There are some beta-builds that do, you can check for those.  Or you can grab the YouTube URL and drop it into VLC.
[*]Allow the OS to install the Nvidia driver, and do not try to download it from Nvidia and do it manually.  All of the newest Nvidia drivers for Windows are game-day release updates.  They usually do not apply to Linux because new-games take a while to be put into the Proton Library, and tweaked a bit to work.
[/LIST]

> **spdkils said:**
> Gaming
[LIST]
[*]Screen tearing, or folding when moving vertical on game that have Linux builds.
[*]Terrible user experience trying to install Vulkan, or even finding info on what supports what.
[/LIST]

[LIST]
[*]Tearing sucks... I agree.  If you are using Nvidia you can turn on "ForceFullCompositionPipeline" to remove screen tearing.
[*]If you are a Steam user, Proton will install what is needed for each specific game.  And you don't have to download any additional stuff.
[/LIST]

> **spdkils said:**
> Drivers (Things get strange)
[LIST]
[*]Monitors swap positions before and after login. (Yes copy more manual XML files to seemingly archaic places on your computer)
[*]If you're booting use UEFI you have to now deal with a boot menu to try and add keys, or hashes, and what file should I pick? Why did I have to type passwords? What is going on with boot now that I changed a video driver? (I know basically, but the process is cray cray)
[*]The boot splash screens change resolution, and look like garbage, but they were pretty before, why does it go so wonky? I'm sure there is a file in 10 strange places, to maybe fix it.
[/LIST]

[LIST]
[*]I believe you can assign each monitor in the Nvidia Control Panel
[*]Yup... UEFI was supposed to be a great new form of BIOS, but Microsoft put that secure boot crap in there, and now you have to be able to disable it in order to boot Linux.
[*]Are you running Ubuntu 20.04?  The boot screen is finally awesome.
[/LIST]

> **spdkils said:**
> Sound
[LIST]
[*]Change the default playback device is not "sticky" by default. You have to use commands, and edit config files to make it persistent.
[/LIST]

[LIST]
[*]There are issues with USB Sound Devices.  They can usually be cleared up by unplugging the USB device, and then plugging it in after boot.
[/LIST]

> **spdkils said:**
> Installation of Software
[LIST]
[*]What a nightmare this is. From drivers, to just simple things like a web browser, everything has 4 layers of complexity.
[*]Sure I can install firefox from the installed application library, but it's already installed I guess with apt-get
[*]But wait, neither version lets me click links out of VSCode without a crash, so I should install something else?
[*]Oh and what about this GD-launcher for minecraft, oh it doesn't work on snap package, but there is the applite thing that just does?
[*]Oh I have java installed, but I have to run this other command to figure out what version this symlink is pointed at?
[*]I have a path, but a different path is bash, for different things.
[/LIST]

[LIST]
[*]Depends on how you look at it.  If you're trying to load drivers the way you do in Windows, you're going to have a hard time.  Look for some threads that show how to load these drivers the Ubuntu way, with PPA's and things like that.
[*]Firefox is the default browser for Ubuntu.  You shouldn't have to install anything to run Firefox.  It's there, and keeps updated via the Ubuntu repositories.
[*]And you lost me on the rest of this list...
[/LIST]

> **spdkils said:**
> I got more obscure as the list went on but, you can't even use the web out of the box. BASIC things like being able to play video without 40% CPU overhead, BASIC things like netflix and chill... BASIC things like selecting the default audio device. BASIC updating a video driver without going into UEFI crazy land and boot going to hell.

Bad ass terminal.... great for scripting, and coding.... Great where Windows Sucks, Sucks where Windows is great.

It is no disgrace to say that you prefer Windows.  If it is what you want to use, or more-so, what you prefer, or even need to use.  I still use Adobe InDesign, and it JUST WILL NOT work in Ubuntu.  I have to run it in a Windows VM.  By all means, use Windows, and piddle around with Ubuntu in your spare time.  

I still dual boot my computer myself.  I use Kubuntu most of the time, but sometimes I have something that I would like to use, and it requires Windows.  Usually, it is a game.  To me, it's not worth the effort required to force a game to run under Wine or even make Proton tweaks, just to get the game to run sub-par in Kubuntu.  So, I will just run it in Windows, and reboot to Kubuntu for all of my other stuff. 

But regardless of what problems you have, you are always welcome at the Ubuntu forums for assistance.

---

### Post by Perfect Storm on 2020-05-07
I've used Linux since 1999 (Mandrake back then wohhoo! :) ) and only experienced minor glitches. But again I do my research when I gather pieces for my machine(s) through the time. I did however took a chance when getting a Ryzen when it hit the shelves.
There can be some minor glitches with nvidia cards. Never experienced it myself and I only using nvidia cards in my home. Installing the driver is ridicules easy nowadays. In eOS (and I guess ubuntu have something similar) you go to appcenter and simpel pick the driver you want to use and you can easily switch between the drivers.
Illustration:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=285782&stc=1&d=1588839883[/IMG]

Both HBO and Netflex works on chrome in Linux. I (behold tadadaaa!) ditched my TV and only uses computers for streaming.
For the gaming part, I only buy games that works natively in Linux. Yes I may be missing the hottest titles, but many of them are overrated IMHO, the gems you'll find in indie games nowadays and usually they have a linux client.


regards

---

### Post by mastablasta on 2020-05-07
> **spdkils said:**
> 
This was a pretty painful process to try and sort it out, and I still haven't figured out some of them, because the complexity and confusion with SOOOOOo many options. There are crazy amounts of browser things you can install. They have supposed GPU  working for video decoding, or this or that. With Windows.. I install Firefox, and latest drivers directly from NVIDIA and I'm done... Nothing else needed... No custom compiles, no alternative patches, nothing to fiddle with. It just works. It doesn't matter if I'm on windows 10 build 1500 or 1800 or 1909. It just works.

about drivers - they are provided by nvidia. or any other manufacturer. so whatever they provide and how they provide it is how well things then work with linux. for example AMD provides them as part of kernel since their source is open. similarly intel. so, there should be no issues there.

i think with latest PPA they (nvidia) made it really simple to install, update and use the driver of choice. to me a much bigger annoyance is when their chip falls out of support. in my opinion this would be a good point in time when they would at least open the drivers if not provide the code to or help develop the mostly reverse engineered opensource nouveau driver.

i bought a Samsung laser printer. it came with CD that had linux drivers on it. but it was difficult to install and faulty. however someone corrected it and provided a PPA. now this all made it complicated particularly for new users. is that linux or linux users fault? well it is clear that samsung messed up a bit here.

anyway HP took over support from them. so this driver became part of HPLIP (which is in kernel). so what is the procedure for driver install now? you plug in the printer and start printing. yeah that's pretty much about it. well for scanning i installed Skanlite. works well.

---

### Post by TheFu on 2020-05-07
Since around 2013, I've only bought systems with iGPUs (Intel) and have been pretty happy.  Intel's drivers are 100% automatic at this point. 16 months ago, while building a new box, found myself getting an nvidia GPU.

nVidia supported drivers
[https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its](https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its) has more.
Perhaps Linus' famous "feedback" finally got their attention to stop being difficult. You can google "Linus nvidia" to find that NSFW image.

Since Intel and AMD have been much nicer, perhaps Linux users should support those companies?

---

### Post by jdeca57 on 2020-05-07
Some people have had issues with the 2020 LTS release. Actually, for people using (a previous version of) the OS the upgrade doesn't show yet and if you force it then it tells you that it's still in development. Stepping in early always may cause trouble (I didn't experience it, and haven't had that problem but then it's always a combination of hardware and the applications one uses).
But the issue of starting with Linux, driver problems, learning about the OS, games that won't work is completely different. Yes, you have to learn another OS. Some of us do that hands-on, some need manuals and others simply ask questions in the forum. I remember years ago I bought my first Android phone. Someone calls me and then there is that green button. It took me some seconds to find out how to answer. Every first has its problems. You accept it, learn about the way it works and use it. Or you don't.
Knowledge never comes free.

---

### Post by poorguy on 2020-05-08
> **TheFu said:**
> 
Perhaps Linus' famous "feedback" finally got their attention to stop being difficult. You can google "Linus nvidia" to find that NSFW image.

Since Intel and AMD have been much nicer, perhaps Linux users should support those companies?

Yep I stay away from Nvidia for the exact reason that they can  and sometimes are very problematic even using Windows OSs and the native  Windows graphics driver. 

Here's that Linus' famous "feedback" link.

[https://www.youtube.com/watch?v=iYWzMvlj2RQ](https://www.youtube.com/watch?v=iYWzMvlj2RQ)

---

### Post by Tadaen_Sylvermane on 2020-05-08
I can't speak to any of your specific issues. Years ago before I fully made the switch to Linux I tried several times. I tried various distros, both x86 and x64. Nothing ever worked. It was all kinds of problems and issues and ultimately I gave up on it. Fast forward 7 years and it works on every machine I've tried with very little needing to be done. I can't explain why this is. Maybe the hardware I was using just had a few issues. Maybe I kept getting bad downloads, who knows. Point being there are many possible reasons you are having issues. And while I know some may not agree, it could be simply a piece of hardware that just isn't very well supported, maybe a bad ram stick. Linux is a bit less tolerant of those types of things. Hell even a slightly unstable PSU can hurt you, or overclocking, all kinds of things.

---

### Post by VMC on 2020-05-08
I was so happy when my nvidia pc died and I got a new pc equipped with intel graphics. Never again nvidia. I learned my lesson.

---

