---
title: "buggy installer, ubuntustudio 9.l0 is a pain, and slighty broken!"
date: 2010-01-12
forum: Ubuntu Studio
---

### Post by triplesquarednine on 2010-01-12
hey there everyone,

i am a long time Ubuntu user. i mostly use ubuntu for multimedia. mainly to host VST's
that i control with actual hardware - IE: an MPC and sampler...

recently i needed to replace my harddrive and do a fresh install...
so i picked up a copy of UbuntuStudio 9.10. i knew the Rt-kernel was back and running very well,
and that it would be a decent install. i was right about the Rt-kernel, while i was completely wrong
about it being a decent install...

...since installing ubuntustudio i can no longer use ubuntu for audio.... :(

1st.  why the hell is ttf-mscorefonts-installer stuck in as a dependency - the installer cannot resolve
the DNS server and causes a "timeout". in turn  - the install FAILS and then after this you cannot install grub....the stupid thing is, there is actually a script out there to fix this problem and resolve the server, and yet no one has bothered to fix this in the installer....

2nd. you can get around this by not installing anything but the base system, however if i do this
jackd doesn't work properly(seems to have some permissions issues, and the system isn't installed the proper way...as i have had ubuntu 9.10 running my apps/VST's perfect in the past, even with on my new harddrive 2 weeks ago, the exact same DVD....when i install it normally, and allow the grub not to install, the permissions on things like jack are fine, but then you have to have grub already installed (IE: having another linux partition or grub on USB to be able to boot!). this is a very stupid design flaw...
for me this is a problem, as all of my partitions are max-ed out. as i run OSX, Linux, and BSD.. 
so i use a USB, and change bios!  

3rd. from hardy to karmic there is no standardisation anywhere. everytime you have to upgrade or reinstall, things work and operate differently. this is also true on any install EVEN when using the exact same install dvd.... RESULTS ALWAYS VARY!!! this is a problem, a big problem!  i was planning on using Ubuntu in my live setup as 2weeks ago it was working flawlessly: 

Zero Xruns, running mutliple instances of Native instruments Massive/FM8 (thru wine/wineasio).
synced to my hardware seemlessly...

Now, i can't do a single thing...this is after 10 seperate installs, even trying other OS's : 64 studio, suse 11 and fedora...and it seems to me, if it is even possilbe, i think ubuntustudio has damaged my soundcard..
which if true, i likely will stop using ubuntu all together....

i am going to try one last install, and if i cannot get ubuntustudio to work, or even just plain 9.10, sadly i will have to install windows XP - which i hate, and ditch ubuntu all together. it's pretty sad that winXP is super OLD but is obviously is far more reliable than ubuntustudio will probably ever be (if we can't even have an installer that works properly!)

so anyone looking to use ubuntustudio 9.10, WATCHOUT!  

you might be better off, not bothering until some basic issues are fixed!

---

### Post by AutoStatic on 2010-01-13
Install just the base system, then the RT kernel, set the permissions right manually ([https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support](https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time%20Support)) and you're good to go.

---

### Post by minister_pete on 2010-01-13
I have Ubuntu Karmic Koala 9.10 and I too cannot get WINE to install. Followed the instructions on the WINE HQ site for 9.10 and the best I got was a message saying to fix the broken package. I had installed it with no problem before and now it doesn't install. Doesn't matter if I try to use the terminal and insert: [I]sudo add-apt-repository ppa:ubuntu-wine/ppa  or if I click on the link that says Click here. The program still refuses to install and is not found in the Ubuntu Software Center. This is what comes up in Terminal when the above was inserted....
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 883E8688397576B6C509DF495A9A06AEF9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: key F9CB8DB0: "Launchpad PPA for Ubuntu Wine Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

Any ideas how I can get WINE installed again? Thanks.
[/I]

---

### Post by triplesquarednine on 2010-01-13
ya, i had already done it that way b4. like i said 10 installs later and it was still messed up...
and now i am not going to bother...

instead i stayed up all night and have installed Fedora 12.   it is flawlessly configured, and ready to go.
it also out performs my prior ubuntustudio setup. i am getting lower latency and zero xruns, and planetccrma
had the latest jack 1.9.4, as well as pretty much everything i use updated right to where i like all my libraries/apps to be..
normally in ubuntu i would have to go to ppa and find newer libraries in order to get things perfect...
Fedora took little to almost no effert, i didn't even have to edit /etc/security/limits.conf or anything like that!!
i decided to take Paul Davis' advice i once read on Ardour.org - that fedora was the best for audio in linux...

i still will use ubuntu for some stuff, but as far as i am concerned fedora is a 
better platform for reliable audio production.... which is my concern as i need to use it on stage,
and ubuntu thus far has been to unpredictable to be used in production, maybe in a couple years...

thanks though!

---

### Post by triplesquarednine on 2010-01-13
you should try:

open a terminal and type: "sudo apt-get remove wine" (to make sure it's not present!)(without the quote's!!)

and if you have the ttf-mscorefonts-installer problem

open a terminal and type: "sudo apt-get remove ttf-mscorefonts-installer"  (no quotes)

and then, to re-install wine

Open a terminal and type: "sudo apt-get install wine" (no quotes)

if that doesn't work download a .DEB package from either the PPA you are using, of direclty from [www.winehq.com](www.winehq.com)

post again if this doesn't fix your problem...cheerz

---

### Post by AutoStatic on 2010-01-13
I use Fedora 12 at work, 9 to 5, 5 days a week. Good luck with it, I wouldn't use it for audio production, once a week a truckload of updates and then keeping your fingers crossed that it will still boot up, nvidia kernel modules that are lagging behind kernel updates, PlanetCCRMA that is afaik basically one sole person. I wouldn't rely on it that much. Not that I don't like it, I like it a lot, but it is simply a bit too bleeding edge for me.

---

### Post by triplesquarednine on 2010-01-14
> **AutoStatic said:**
> I use Fedora 12 at work, 9 to 5, 5 days a week. Good luck with it, I wouldn't use it for audio production, once a week a truckload of updates and then keeping your fingers crossed that it will still boot up, nvidia kernel modules that are lagging behind kernel updates, PlanetCCRMA that is afaik basically one sole person. I wouldn't rely on it that much. Not that I don't like it, I like it a lot, but it is simply a bit too bleeding edge for me.


i do agree that is quite bleeding edge, but here are some observations in my 48hours of using
fedora 12 for audio: (and why i am sticking with it!)

1st. the quality of packages is much higher than that of ubuntu, regardless of whether there is less people
making these packages...in fact, if there is only one person @ planet ccrma, i feel sorry for ubuntustudio.
as one person in fedora is making way better setups and installs! 

2nd. several VST's that wouldn't work properly in ubuntu, work OUT OF THE BOX in fedora!
this includes things like N.I Absynth, Battery3 and other parts of Native instruments Kore. before the only reliable plugins from N.I where Massive, and FM8. Battery 3 worked but was only good for sampling as
it would cause Xruns, this isn't the case in fedora, it just works! (and works well)

3rd. i am not using Nvidia on this machine, and as it is for audio production i do not require hi-end graphics, opneGL or any of that crap. it is for music... i am running a lite version of Compiz and it is quite stable...and an old ATI card. (x1300 mobility)

4th. as far as updates, once this machine is working exactly the way i want it to, as in it must be able to run several VST's, LV2, and 1 or 2 other apps glitch free! i won't be updating(totally disable) it or using it to connect to the internet - in fact, i will disable EVERYTHING that isn't essential to what i am using it for. i have MacOSX, and freeBSD on this machine for everything else. my fedora install is only for audio, and nothing else...now i use ubuntu on a USBstick mainly for if and when problems arise, and just for fun.

5th. already i have it setup similar to ubuntustudio, similar optimization and fedora would definetly out-benchmark ubuntustudio. it feels faster, uses less memory and i can run more apps at once without problems...it also is using less CPU, when i am running the same apps as in ubuntu.

i also feel like the RT-kernel is a bit better.

***fedora 12 is one partition on my box, it is small, and will be used only for live-purposes, where i do not 
want the OS to get in the way of the plugins i am running, and linux being modular in nature allows me to do some interesting setups: live-looping with VST's and my AKAI MPC controlling plugins... it will pretty much be running headless...
so i think it will work fine...

---

### Post by AutoStatic on 2010-01-15
> **triplesquarednine said:**
> 1st. the quality of packages is much higher than that of ubuntu, regardless of whether there is less people
making these packages...in fact, if there is only one person @ planet ccrma, i feel sorry for ubuntustudio. as one person in fedora is making way better setups and installs! Haven't thought of it that way, and when I do think about it I have to say you're quite right. The [CCRMA maintainer]("https://ccrma.stanford.edu/~nando/") is doing a good job actually.

> **triplesquarednine said:**
> 2nd. several VST's that wouldn't work properly in ubuntu, work OUT OF THE BOX in fedora!You don't use nVidia, I don't use any VST's or stuff that needs Wine.

> **triplesquarednine said:**
> 4th. as far as updates, once this machine is working exactly the way i want it to, as in it must be able to run several VST's, LV2, and 1 or 2 other apps glitch free! i won't be updating(totally disable) it or using it to connect to the internet - in fact, i will disable EVERYTHING that isn't essential to what i am using it for.I'm with you on that. But Fedora doesn't release so many updates (48 today!) for nothing I think. Maybe it's just a sort of biased point of view, wow, another 48 updates, their stuff has to be buggy! To be honest, I don't check the changelog of every single update.

> **triplesquarednine said:**
> 5th. already i have it setup similar to ubuntustudio, similar optimization and fedora would definetly out-benchmark ubuntustudio. it feels faster, uses less memory and i can run more apps at once without problems...it also is using less CPU, when i am running the same apps as in ubuntu.Maybe I should give F12 a go too, I doubt if the differences are that big.

> **triplesquarednine said:**
> i also feel like the RT-kernel is a bit better.They both use a 2.6.31 kernel, slightly different versions though so you could be right, allthough the current Karmic rt kernel performs pretty ok. Haven't worked with the F12 rt kernel yet.

It's all about choices and having the freedom to choose. I chose Ubuntu for music production, Fedora feels too unfinished and too bleeding edge for me.

---

### Post by triplesquarednine on 2010-01-15
hey autostatic!

i think fedora gets so many updates, not because of just bugs, but because it is the fore-front of linux..
i think you might be really surprised with fedora's capability for multimedia, after a few days now, i am blown away..
thanks for giving me the tips about fedora's updates. so far i have only let it perform security updates. my system is running really really well....i'll kind of explain what i am doing, if you are interested??

basically, i am turning my laptop into a "dedicated multi-timbral software synthesizer-sound module". what this means is that i can hook it up to a hardware sequencer(my AKAI MPC) and have multiple synths or samplers and or FX be controlled and running at the same time. the closest comparison you can find in retail is known as the receptor/receptor2 made by muse reseach. you should check out there website and watch a video or two - they are doing some amazing things with linux in the pro-audio world. here is the link:  [http://www.museresearch.com](http://www.museresearch.com)

now where as their sound module is(from what i gather) meant to only run one synth at a time, i intend to be able to run several. one or two being sequenced, and one for "live play"...why do i want to do this, you may ask???

i can't afford thier hardware, but i want to be able to use the same sound live as the ones i use in recordings...
luckily for me, wine can run my Native Instruments pretty well, even multiple instances. now these plugins are VST's however, i do not run them as VST's. i use the .EXE - standalone apps with wineasio, which is more reliable than FST or DSSI-VST. 

one might ask why not just use my Mac to do this, the answer is quite simple. linux provides the lowest latencies available in any OS, followed by the fact that linux handles memory far better than mac or PC, and lastly i can remove everything not needed for making music - great optimization! i can safely achieve latencies as low as 5msec! if i ran only one synth as low as 2msec and that is with my crappy intelHDA! imagine what a newer computer with a better sound card could do.....?

anyway, a little more about my setup....obviously, i switched i am using Fedora 12... and the rt-PAE 32-bit kernel. this is running on a Dell inspiron 6400 - Core Duo 1.6ghz, 1 gig, 320gig harddisk... instead of using Gnome/KDE/XFCE i have opted to use Fluxbox as my window manager, this gives me a 10% reduction in CPU usage, on average and 50mb reduced in memory usage....fluxbox also doesn't support Compiz - which in my experiences can interfere with using linux for pro-audio. fluxbox is extremely lite, easy to configure and fast as hell. i don't loose my normal desktop either, as i can pick between a gnome-session for standard desktop usage or fluxbox for audio.

thus far i have been able to run 5-7 N.I. instruments without problems, with one or two small exceptions(there are certain FX plugins that i need to avoid, one is called a "fractalizer" and causes crashes, not surprisingly!). so the name of the game is to root out all buggy patches and stick with what works really well...

also, with fluxbox i have a file called "startup" where i can execute things on startup, so the idea is once i have figured out the perfect setup: ie: what synths i will use and how they are configured, i can setup it up to call up Qjackctl, a mixer and all of my plugins - with whatever routing i want already setup in jack!  you can think of this sort of like what Lash is supposed to do, but instead i am using the OS to do this, as Lash is often unpredictable. so basically, the OS becomes a vessel for more synths and that is it's only purpose...

i will be putting some videos up on youtube, sometime after the weekend. (i need to buy a few patchchords and midi cables before i can do full testing and use it.) so far, i have done software testing - using Muse to control all of my synths, doing things like trying to make linux crash from CPU/mem over-usage. but i am not interested in using software sequencers as i am a tactile preson and own real gear. my mpc, an SP-555 sampler, keyboard, etc.

anyway, i will post a link to my youtube when i got something to post, k?

later!

TS9

---

### Post by AutoStatic on 2010-01-16
> **triplesquarednine said:**
> i think fedora gets so many updates, not because of just bugs, but because it is the fore-front of linux..True, true. And they fix bugs way faster: [https://bugzilla.redhat.com/show_bug.cgi?id=554292](https://bugzilla.redhat.com/show_bug.cgi?id=554292)
The Ubuntu way: [https://bugs.launchpad.net/ubuntu/+source/recordmydesktop/+bug/448027](https://bugs.launchpad.net/ubuntu/+source/recordmydesktop/+bug/448027)

> **triplesquarednine said:**
> basically, i am turning my laptop into a "dedicated multi-timbral software synthesizer-sound module". what this means is that i can hook it up to a hardware sequencer(my AKAI MPC) and have multiple synths or samplers and or FX be controlled and running at the same time. the closest comparison you can find in retail is known as the receptor/receptor2 made by muse reseach. you should check out there website and watch a video or two - they are doing some amazing things with linux in the pro-audio world. here is the link:  [http://www.museresearch.com](http://www.museresearch.com)Checked it out. The first thing that pops up in my mind when I see products like that is: do these guys contribute anything to the Linux community? Might sound a bit sarcastic, but it's also that I'm totally not interested in products like the Receptor. I didn't even know of its existence. But I can imagine it's quite fun to build something like that yourself.

> **triplesquarednine said:**
> one might ask why not just use my Mac to do this, the answer is quite simple. linux provides the lowest latencies available in any OS, followed by the fact that linux handles memory far better than mac or PC, and lastly i can remove everything not needed for making music - great optimization! i can safely achieve latencies as low as 5msec! if i ran only one synth as low as 2msec and that is with my crappy intelHDA! imagine what a newer computer with a better sound card could do.....?Mac is based on BSD and is a close relative to Linux. I really, really doubt if a Linux desktop outperforms a Mac that has hardware and software that match perfectly. I like to point out though that I personally dislike Apple.

> **triplesquarednine said:**
> anyway, a little more about my setup....obviously, i switched i am using Fedora 12... and the rt-PAE 32-bit kernel. this is running on a Dell inspiron 6400 - Core Duo 1.6ghz, 1 gig, 320gig harddisk... Why do you use the PAE kernel? Are you planning to extend your RAM?

> **triplesquarednine said:**
> also, with fluxbox i have a file called "startup" where i can execute things on startup, so the idea is once i have figured out the perfect setup: ie: what synths i will use and how they are configured, i can setup it up to call up Qjackctl, a mixer and all of my plugins - with whatever routing i want already setup in jack!  you can think of this sort of like what Lash is supposed to do, but instead i am using the OS to do this, as Lash is often unpredictable. so basically, the OS becomes a vessel for more synths and that is it's only purpose... You should check out [http://digitaldub.wordpress.com/2009/12/16/linux-audio-session-scripting/](http://digitaldub.wordpress.com/2009/12/16/linux-audio-session-scripting/)

> **triplesquarednine said:**
> anyway, i will post a link to my youtube when i got something to post, k?Cool! Maybe you could post them on the Fedora Forum too. I don't hang around there often myself anymore though.

---

### Post by triplesquarednine on 2010-01-18
> 
  The first thing that pops up in my mind when I see products like that is: do these guys contribute anything to the Linux community? Might sound a bit sarcastic, but it's also that I'm totally not interested in products like the Receptor. I didn't even know of its existence. But I can imagine it's quite fun to build something like that yourself.


i think the main people who are interested in products like peceptor, are people who have a need for it.
this is the case for me, as having a consistent sound is important, and being able to better allocate resources when in recording-sessins is quite valuable...now that being said, i do agree with you that this company really doesn't share anything with the linux community, which is annoying! but i can still appreciate the design and i understand the value, and why it is a good solution in the pro-audio world!

> 
Mac is based on BSD and is a close relative to Linux. I really, really doubt if a Linux desktop outperforms a Mac that has hardware and software that match perfectly. I like to point out though that I personally dislike Apple.


yes, i use freeBSD8 on a machine, and although they are related X is quite different in a lot of ways.

thus far, atleast at my end, linux IS  outpreforming OSX.  my latencies are much higher in OSX, and using them in a "live atmosphere" i run out of resources quickly too... you got to remember i am running a slower machine with a gig of ram....OSX takes up 5-10% of cpu to run, and 15-20% of memory.
under linux there are almost zero services running, alsa and jack, my lite gui, fluxbox. and on startup i am using 1% of CPU, and 94% or RAM.  i have extremely low-latencies, lower than i can acheive with this same hardware under OSX.  

i will be testing it on my macbook pro next!  but i can pretty much guarantee it will be the same
out come as this old machine, because so much of the OS has been stripped away and because you can get really low-latencies in the linux platform.  you can feel the difference when there are many 
plugins being controlled thru midi and when you are playing really large-complex multi-patches on top.
linux just moves along...i might add as well that all of external hardware is being routed thru the
input of my computer and being mixed before output to the speakers, and i have no xruns, unless
i use a bad plugin!

> 
 You should check out [http://digitaldub.wordpress.com/2009/12/16/linux-audio-session-scripting/](http://digitaldub.wordpress.com/2009/12/16/linux-audio-session-scripting/)

Cool! Maybe you could post them on the Fedora Forum too. I don't hang around there often myself anymore though.

i'll check them out! thanx

---

### Post by AutoStatic on 2010-02-02
> **triplesquarednine said:**
> i do agree with you that this company really doesn't share anything with the linux community, which is annoying!They do contribute to the Linux community so I take my words back: [http://www.google.com/search?q=Michael+Ost+site%3Alists.linuxaudio.org](http://www.google.com/search?q=Michael+Ost+site%3Alists.linuxaudio.org)

---

### Post by 5010 on 2010-02-09
I'm trying to figure out how to test drive ubuntu studio 9.10 from a usb drive.  I downloaded the dvd ubuntustudio-9.10-alternate-i386.iso and used "USB Startup Disk Creator" to put it on a flash drive.  Then I booted to the USB and the only option I could see was to install and then it wanted to format my main HDD.  Then I tried booting from local drive instead and it froze, so I reset the CPU, lost the ability to start X, it said to check my syslog.  I don't know where that is.  I tried the option to auto fix the X and it said it was read only, then I powered off the system and ran an errand and came back and it started up ok this time (not 9.10 but back to my 9.04 studio on the HDD).  Scary stuff.

So now I'm really paranoid.  How can I get 9.10 Ubuntu Studio to install on the USB without doing anything to the HDD?  I really want to check out the newer lmms version.

---

### Post by AutoStatic on 2010-02-09
Hello 5010, are you using Jaunty? Tobydox, LMMS' main dev, has his own PPA. You could try 0.4.6 from there: [https://launchpad.net/~tobydox/+archive/lmms](https://launchpad.net/~tobydox/+archive/lmms)

---

### Post by 5010 on 2010-02-09
Yep Autostatic.
 
I don't know what a "PPA" is or how involved it is to install it.  I checked out your link and it says "This PPA can be added to your system manually by copying the lines below and adding them to your system's software sources."
 
So then I found info here: [https://help.launchpad.net/Packaging/PPA/InstallingSoftware](https://help.launchpad.net/Packaging/PPA/InstallingSoftware)
 
So I think the easiest way to test it would be to just install regular Jaunty on the USB and boot from that.  Then install launchpad.  Then set it up to get lmms 0.4.6.  Install that.  Then try opening my projects on the HDD.
 
Am I missing anything?  I'm not at my linux box now but want to try it tonight.  This is a learning experience.
 
Maybe if I learn enough I can someday help the ubuntu studio team add the ability to test drive it before installing.

---

### Post by AutoStatic on 2010-02-09
Are you using Jaunty? Is it installed on your computer? Then you can add the PPA, install LMMS (it will automatically install 0.4.6 if tobydox's PPA has been added correctly) and test it. And if it doesn't work for you you can easily uninstall it in Synaptic again. Or is there a specific reason why you want to boot from USB to test LMMS?

---

### Post by 5010 on 2010-02-09
Yep, I've been doing the project with lmms for Jaunty's Ubuntu Studio. Also 3 other family members share the machine although they don't make music on it.
 
How do I know I can uninstall and get things back to the way they were if the new lmms doesn't work out ok for this machine? What if the new version pulls in dependancies that cause problems for the old version? I'm not confident. I have a lot of work done and until we release the songs I don't want to jeapordize the ability to adjust and re-render them as needed.
 
But there are other reasons I want to learn how to test drive things on the USB. Jaunty's maintenance will eventually run out, so before I risk hitting the "update now" button I want to clone my system and try it on another drive 1st. If that causes problems, then I'd want to try out a fresh install on another drive before risking this drive.
 
But also it would be cool to be able to boot my stuff on other artists' computers when we meet for collaboration.
 
When I hear stories about people updating something and messing up their systems, it makes me nervous. Stuff like "be sure you back up everything before you adjust your partition". OK I have a backup of everything, which created a DvD full of read-only files. How do I restore from that? I don't know.
 
I wish my machine had an "undo 1 day" button on the front panel. ;)

---

### Post by 5010 on 2010-02-10
The usb startup disk didn't work out.  I selected to try ubuntu and it eventually got stuck.  Couldn't put /dev/loop on /cow whatever that means.  Oh well.

---

### Post by cub on 2010-02-20
I'm not sure if I should start my own new thread or continue in this one.

I want to install Ubuntu Studio on an old laptop which is good enough to do the small work I do. Since the laptop only have a cd-drive and not DVD, I downloaded ubuntustudio-9.10-alternate-i386.iso and put it on an USB-stick with UNetbootin.

The installation starts up fine, I choose keyboard and country but the the next phase arrives: Detect and mount CD-ROM.
"Your installation CD-ROM couldn't be mounted. This probably means that the CD-ROM was not in the drive. If so you can insert it and try again.
Try again to mount the CD-ROM? Yes/No"
Of course there's no CD in the drive. The installation would only fit on a DVD to begin with and second I have it on an USB-stick. Why is it trying to find the non-existing CD-ROM installation?
Sadly there don't seem to be a way around this since if I press YES it tries to mount the cd and fails, if I press NO the installation fails since the following steps continue too look for the installation CD.

Any suggestions? (Except buying a new laptop)

The laptop has had several Ubuntu versions installed, but in the days when it came on a CD. One thought I had was if it would be possible to boot the laptop with the old Ubuntu 8 that's installed and run the Ubuntu installation from there? But surely I would end up with the "mount CD-ROM" issue again, wouldn't I?

Edit update:
Ok, after some coffee I tried the workaround written on [https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu) .
I installed Ubuntu 9.10 from a CD and the did the manual full upgrade to Ubuntu Studio. It seems to have worked. I'm happy. Though I still wonder why a USB-stick installation wouldn't work.

---

