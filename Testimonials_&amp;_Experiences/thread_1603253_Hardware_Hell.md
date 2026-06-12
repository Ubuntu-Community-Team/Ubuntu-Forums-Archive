---
title: "Hardware Hell"
date: 2010-10-22
forum: Testimonials &amp; Experiences
---

### Post by pihbar on 2010-10-22
I had everything working on my Lenovo U350 on 10.04. I figured I should upgrade to 10.10 because, well, things could only get better. Right? No. 10.10 completely broke everything. The graphics wouldn't work at first, and after I fixed them (with a simple but frustrating to find fix) they were jerky (there was a fix for that too), the internal mic died, the brightness keys became decoration, etc. I had to waste hours to reinstall 10.04 and fix some 10.04 errors.

I was telling my friend about the experience, who uses a Mac by the way, and he said, "Don't they check for hardware compatibility and **hardware-specific fixes** for these things when you upgrade?"

They do not. But why not? Much more important than having an extra monochrome indicator applet icon is to have a computer run Ubuntu in the first place. A user will never see the indicator applet, or even system tray for that matter, if he or she cannot get X to start without knowing a lot about Linux already. Even people who are familiar with Linux will have some difficulty hunting down information necessary to fix their system.

Two obvious and easy alternate **solutions** to this problem present themselves. 

[LIST=1]
[*]Create a collection of *relatively* simple **post-install scripts** that fix common issues based on detected hardware. For example, if the script matches the output of lspci with the Lenovo U350 sound card, then execute
[FONT="Courier New"]
sudo apt-add-repository ppa:ubuntu-audio-dev/ppa && sudo apt-get update && sudo apt-get install linux-alsa-driver-modules-$(uname -r)
[/FONT]
in order to prevent sound coming out from the speakers when headphones are plugged in (what an annoying bug).

Another example is the installation of Broadcom wireless drivers. Some BCM43xx chipsets do not work well with open source drivers. In my case, they do not work at all. I had to wade through that horrible Ubuntu "developer wiki" (read the heading page, the wiki isn't meant for finding help: [https://wiki.ubuntu.com/]("https://wiki.ubuntu.com/")) to figure out that I had to install three packages *already on the CD*. This wasted me hours, because there were many possible configurations and I wasn't sure which one to use so I had to try several (with steps including downloading data on another computer and transferring to this one because I had no Internet access). What should have happened is that Ubuntu should have figured out which driver I need (this is well documented, see [http://forums.fedoraforum.org/showthread.php?t=239922]("http://forums.fedoraforum.org/showthread.php?t=239922"), which has a freaking flow-chard of what to use), and then told me:

*"We need to use non-free drivers, or else you won't have Internet. Clicking this button will install three packages on the CD for you, because you shouldn't dig through random files and documentation to figure out which. If this doesn't work, you'll be offered to revert to your previous configuration."*

Finally, a lot of these common bugs (that you can expect simply by doing lspci and uname -r to match hardware and kernel) are fixable by adding just one option to one text file in /etc/something.conf. So a fix of the form

[FONT="Courier New"]cat option snd-hda-intel model="ideapad" >> /etc/alsa.conf[/FONT]

(or whatever) can save the user a lot of time, nerves and (from a business perspective, most importantly) can make the user NOT switch away from Ubuntu.
[*] If these scripts are too much, then at least **start a well organized hardware wiki** that the users are informed about with a popup on the install disc 

*"Would you like to check hardware a compatibility to fix common issues?"*
[/LIST] 

My point is, every time a user meets annoying bugs like sound not working or microphone not working or other hardware bugs, he or she will quit Linux and never come back. Linux desktop *needs* a bigger userbase to become better, more stable, and to start seeing more software ported to Linux. God forbid games, or something.

These bugs are often discovered in bug reports and fixed very quickly. If the developers, and bug-squashers had a *standardized* place to go to in order to implement a fix or document how to fix the bug for everybody with this bug, Ubuntu would benefit greatly. 

All it takes is for a skilled programmer to create a script template that compares (as I said) the output of lspci and uname -r and then executes some code (with notification popups) based on this output AND for others (maybe only bug-fixers as a start) to know about this easily-accessible website and start adding information.

For this purpose, I am starting an Ubuntu Branstorm thread to help me get this started (with help of said skilled programmers :)), If you feel like you can **help out**, please do so! I have limited time, but would be willing to do a little bit on this!

Related **Ubuntu Brainstorm** threads:
[LIST]
[*] [http://brainstorm.ubuntu.com/idea/26221/](http://brainstorm.ubuntu.com/idea/26221/) - Idea directly related to this post.
[*] [http://brainstorm.ubuntu.com/idea/26084/](http://brainstorm.ubuntu.com/idea/26084/) - Ubuntu community sites need more exposure
[/LIST]

---

### Post by ventrical on 2010-10-22
Sorry to hear that you had a bad experience with Ubuntu 10.10.

 I have a sony VAIO PCG V50...) laptop  and I had Ubuntu 10.4 and then upgraded  from BETA CD. It completely destroyed the previous GRUB which had WinXP and Ubuntu 10.4, but, I  have the recovery disk - so I don't care- that I lost the Windows Install. However... the Meerkat Install has become more stable over time and after many updates. The only real work I had to do was to set-up the DVD playback correctly - and that is working very fine last time I checked.. but I hear you and your concerns because it  makes it seems that the version updater process is unreliable and that a very well tempered and well kept install of 10.4 can be wiped out and broken by a 10.10 Meerkat upgrade.

---

### Post by 3Miro on 2010-10-22
Comparing upgrades in Ubuntu and Mac is totally unfair. Apple provides only a handful computer models, so the developers have full access to absolutely all the configurations that the users will have. People use Ubuntu on every hardware configuration under the sun.

```
sudo apt-add-repository ppa:ubuntu-audio-dev/ppa
```
This is a development repository, you can access it, but it is supposed to be unstable. This is the one that people are using to test stuff, basically it is only a matter of time before an upgrade from that repo breaks your sound. This cannot be used as an official fix (a temporary hack at best).

I have a Broadcom wireless that doesn't like the open source driver. However, I have never had trouble with the drivers if I get them straight from the Hardware Center. Get a wired connection and use the HW center, once the packages are installed, you can disconnect the wire. Also, the bad and complicated driver is Broadcom's fault, not Ubuntu.

There is a common place to report/resolve bugs, thought it may be a bit obscured:
```
https://bugs.launchpad.net/ubuntu/maverick
```

The issue with hardware specific post-install scripts is that the Ubuntu developers don't have access to that much of the hardware available. Check System76 for a contrast, they work out all the bugs on their laptops and they tell you when it is OK to upgrade. 

About all the sound issues that you have, are those apparent, if you boot from a liveCD. I am wondering how much upgrade vs. clean install has to do with those issues.

---

### Post by pihbar on 2010-10-22
> **3Miro said:**
> Comparing upgrades in Ubuntu and Mac is totally unfair. Apple provides only a handful computer models, so the developers have full access to absolutely all the configurations that the users will have. People use Ubuntu on every hardware configuration under the sun.

```
sudo apt-add-repository ppa:ubuntu-audio-dev/ppa
```
This is a development repository, you can access it, but it is supposed to be unstable. This is the one that people are using to test stuff, basically it is only a matter of time before an upgrade from that repo breaks your sound. This cannot be used as an official fix (a temporary hack at best).

I have a Broadcom wireless that doesn't like the open source driver. However, I have never had trouble with the drivers if I get them straight from the Hardware Center. Get a wired connection and use the HW center, once the packages are installed, you can disconnect the wire. Also, the bad and complicated driver is Broadcom's fault, not Ubuntu.

There is a common place to report/resolve bugs, thought it may be a bit obscured:
```
https://bugs.launchpad.net/ubuntu/maverick
```

The issue with hardware specific post-install scripts is that the Ubuntu developers don't have access to that much of the hardware available. Check System76 for a contrast, they work out all the bugs on their laptops and they tell you when it is OK to upgrade. 

About all the sound issues that you have, are those apparent, if you boot from a liveCD. I am wondering how much upgrade vs. clean install has to do with those issues.

Well, I wasn't comparing them but merely showing what a user of a stable system comes to expect. A user doesn't judge what to use based on what's "fair," but what is better. Fairness has nothing to do with quality, I'm afraid. But yes, Macs have it easy and that is out of the scope of this discussion -- if you want to compare look at Windows.

Both my ethernet and wireless are using broadcom drivers, so that was not an option. Besides, if drivers are on the CD, it *is* Ubuntu's fault for not informing the user about them. I don't *have* to go to the software center and guess what I need. Installing the drivers isn't complicated if you know where to look. My idea merely suggests that you should be pointed in the right direction (and have the work done for you up to a click).

As for you unstable sound comment, well, it's been months and more than one release of Ubuntu since the fix has been in the developer repo, and it hasn't come to the main ones. Besides, what does it mean that the drivers in the repo aren't stable if they work and the "stable" ones do not?

I have reported many bugs, some got resolved, but that is a labor intensive effort. The point of these scripts is that the developers don't NEED access to the hardware! The point is that once a bug gets resolved in said bug reports, THEN just make a script for fixing it or list how to fix it in a **centralized** location that one can immediately turn to, like a real and well organized wiki.

The issues persist on both fresh install and upgrade, I've done both.

---

### Post by cariboo on 2010-10-22
There seems to be a bug in the installer, where it doesn't drop back to the open source video drivers, when there is a restricted driver already installed. This causes a problem, because the old restricted driver will not work with the latest version of Xorg, so you can at least blame that on the install process.

---

### Post by 3Miro on 2010-10-23
> **pihbar said:**
> 
... I don't *have* to go to the software center and guess what I need...

You don't. You go to the "Hardware Center", also known as jockey (if you call it for the terminal) or System -> Admin -> Hardware Drivers. You don't have to guess anything in that one, it does the work for you, all that you need is a working internet connection to pull the right deriver.

(If Ubuntu doesn't include a driver on the CD it is usually a legal issue.)

---

### Post by rjbl on 2010-10-24
What's all this crap about GNU/Linux being picky with hardware. OK, so in the early days of RH5.5 it helped the installation along a lot if you had a note of yer graphic card type but, lets be honest, since those days you've very, very rarely found an install that fails to detect the hardware more or less correctly, first time.

rjbl

---

### Post by pihbar on 2010-10-24
> **3Miro said:**
> You don't. You go to the "Hardware Center", also known as jockey (if you call it for the terminal) or System -> Admin -> Hardware Drivers. You don't have to guess anything in that one, it does the work for you, all that you need is a working internet connection to pull the right deriver.

(If Ubuntu doesn't include a driver on the CD it is usually a legal issue.)

That's the problem: I don't have any means of accessing the internet. All my cards are problematic. Also, I don't need access to the internet: I can use the propriatery drivers that I need to install from the cd (bud didn't know were there). A user shouldn't have to know about jockey and the install disc directory structure. THe point is: it doesn't work the way things are. Why do you defend ubuntu as if it's a holy relic. Let's just focus on making it better.

---

### Post by ventrical on 2010-10-24
> **pihbar said:**
> That's the problem: I don't have any means of accessing the internet. All my cards are problematic. Also, I don't need access to the internet: I can use the propriatery drivers that I need to install from the cd (bud didn't know were there). A user shouldn't have to know about jockey and the install disc directory structure. THe point is: it doesn't work the way things are. Why do you defend ubuntu as if it's a holy relic. Let's just focus on making it better.

 Mabey I should start a new thread on this . All I have to say is that I happened to download a real bogus beta version and RC version of Ubuntu 10.10. I was in a real hurry to burn some CDs and really didn't care to validate my source.  During the install on one PC I was actually hacked with a 'man-in the-middle' attack.

  As I watched the indicator bar on the installer move along 'copying files' it came near the end on the install and suddenly the text changed to  "Ok .. I'm ready when you are' !!!!!!!!! So you could imagine my surpirse. well.. not really because I have been hacked many times before.

  My point is (and I think caribou pointed out about a bug with the installer) , yes .. thats true .. but it is important that we have a good , solid and verifyable .ISO file to start with. If not ,  then my declarations really don't hold water. But you do make some good points and Ubuntu should be held to a higher bar of excellence.

---

### Post by cariboo on 2010-10-24
> As I watched the indicator bar on the installer move along 'copying files' it came near the end on the install and suddenly the text changed to "Ok .. I'm ready when you are' !!!!!!!!! So you could imagine my surpirse. well.. not really because I have been hacked many times before.

I actually saw that message doing a Mythbuntu install the other day. The iso was downloaded from [http://releases.ubuntu.com/]("http://releases.ubuntu.com/"). So the message is valid, it's probably just a dev having some fun.

---

### Post by 3Miro on 2010-10-24
Right after install, on the first boot, jockey should have popped up to tell you about Hardware Drivers (if they were indeed on the install CD, some of them have to be downloaded separately ... legal issues). If it did not, then this is where the problem is, not with the developers not thinking about simple solutions.

I am all about making Ubuntu better, however, there are things that are reasonable and things that are not. If we have a real bug, then it should be fixed and you have the right to be dissatisfied. Otherwise, we are just dealing with a bunch of hardware manufacturers that refuse to make good FOSS drivers and I think it is unreasonable to complain, when Ubuntu fails to jump through all of their hoops. I don't think we can make Ubuntu better by making more "flexible" to the demands of hardware manufacturers, we should instead use out money against those manufactures and research hardware as much as we can before we buy, then the manufacturers will make good drivers for all hardware.

Yesterday I installed 10.10 on my sister's laptop, audio, video, wireless, suspend, hibernate, external monitor all worked out of the box. This was simply because all of her hardware was Intel and they had good FOSS drivers. All hardware should be like that.

---

### Post by mastablasta on 2010-10-25
another thing is to use a live CD (or USB) first before upgrading, just to see if everythign works as planned. even if unreliable it is still quite good indicator of what is to come in true instal.
 
as for the uncomaptible hardware it really is an issue of hardware manufacturers. but let's be hones here. Linux with it's new kernel versions and x.org version every couple of weeks or every few months doesn't really make it easy for them does it? I mean windows has only one kernel that later gets patched the other ways. so hardware manufacturers know they can focus on improving their drivers there instead of keep having to develop new ones because someone decided a new feature should be added to X.
 
another way would be to release every data about drivers and cards out to community but then again why should they?! so that someone can use their ideas and patents?

---

### Post by 3Miro on 2010-10-25
> **mastablasta said:**
> 
another way would be to release every data about drivers and cards out to community but then again why should they?! so that someone can use their ideas and patents?

Who is that someone? That someone is me, the person who already payed them money for the hardware. Now I am only allowed to use it this or that way, the way they feel I should. Why does Ford and Toyota let me look under the hood of my car, I can take the whole engine apart if I wanted to, why are they not worried about their patents? If I do the same with windows OS or some Linux drivers, then I can go to jail. What sense does that make?

Besides, it isn't that hard to deal with the kernel and Xorg. Older NVIDIA drivers work with both old and new versions of the kernel, you have one standard interface on the kernel side, one interface on NVIDIA binary code and you compile/recompile the connection. It is slow and clumsy, but it works. There is nothing that prevents other manufacturers from doing the same.

You also have a list of companies like Intel and AMD that provide FOSS drivers for their products, are they losing money? The problem with manufacturers is that they either don't think they can make money out of Linux or some technologically illiterate CEO believes that they have to protect their "corporate secrets". There is no reason to not make all drivers FOSS (other software like games and photoshop is a different story).

This getting out of topic. I am leaving this thread and the mods will probably close it.

---

### Post by ventrical on 2010-10-25
> **cariboo907 said:**
> I actually saw that message doing a Mythbuntu install the other day. The iso was downloaded from [http://releases.ubuntu.com/](http://releases.ubuntu.com/). So the message is valid, it's probably just a dev having some fun.

Fair enough :) but it doesn't explain the lock-up afterwards.

  But back to topic here .. I have had the same (if not worse) experience with obsoleted Win98 back about 4 years ago when AV devs were still writing security for that OS. It was near impossible to get some of the printer/scanner and CR-RW drivers  while running Win98 and even XP also .. with legacy roll-backs.  So hardware hell drivers are inherent on most operating systems.

Thankfully for the most part, more often than not , all the hardware is detected and then it is smooth running from there. I would think to stay the course as Ubuntu continues to update and develop because the writing is on the wall that a System Restore type GUI has most likely been in the works and hardware driver rollback also.

  I like what Miro said about owning his own car and not violating copyright laws. Thats true. A guy can buy a new car, take it completely apart, take a million photos of each part and post them on the internet all for free and with no threat of copyright infringment.  Like .. hello !!! and if a guy makes an image of his original  Win ISO to give to a buddy  for a recovery because he had a factory install with an OEM , they call him a bum and a pirate.

  So that brings back the point of why we can count our blessings in having Ubuntu (and other) as free Open Source programs. It's a good back-up without  having stressed out worry about offending somebodies copyright (that they probably hijacked in the firstplace) from some old BASIC script of a Space Invaders game :)


 regards..

---

### Post by armandh on 2010-10-26
and to add to your grief you have migrated from a LTS ver.
so you get to do it all over again sooner

my wife's lap-top is running 8.04
and I am not changing a thing until I absolutely have to.

---

### Post by 3rdalbum on 2010-10-26
Tell your Mac friend about the bugs in OS X that would never make it into Ubuntu, such as "switch to the Guest account and your home directory gets deleted" or "cutting and pasting in Finder actually deletes the file before it gets pasted".

---

### Post by ventrical on 2010-10-26
> **armandh said:**
> and to add to your grief you have migrated from a LTS ver.
so you get to do it all over again sooner

my wife's lap-top is running 8.04
and I am not changing a thing until I absolutely have to.

  I still have my 8.04 Heron distro and I still use it. However , I did a migration from 10.04 to 10.10 on a Sony Vaio and , at first it was real hell to get it up running  but that was because it was BETA. During the install process of 10.10 it proceeded to destroy the SONY OEM Windows XP Pro install but I usually know what I'm getting into when i am BETA testing. Then, I proceeded to download the RC through the online updater and that went a lot better. So it took some time to get it working 'somewhat'. (I'm not expecting seamless installs everytime but they are real nice when they happen.)  But I catch your drift.

  But I would like to put up an experience that happened last night. I put back in the original HDD with Win XP on it on an ACER Aspire 3860 with a certain anti-virus program (AVG 2011) that had just recently updated and it completely ruined the fluency of how Adobe Flash worked in Internet Explorer. Then I stuck my Ubuntu pen drive  in , booted and  got  my audio back.

  And speaking about hardware ... I could never find a program for Windows that would allow me to use the voice recorder (just a 10 second sample) - but Ubuntu comes with this built in recorder and I can do voice memos in MP2, .wav and .ogg  a half hour long if I want.

  I guess in some cases , because of competitivness of the devlopers and the diverse hardwarexia and plethora of enthnically intergrated motherboards, all chips claiming their own ports, it  is certainly understood that a lot of idchips get dissed on the way up , but I have noticed that with patience there is a trend that a lot of the driver issues get resolved, maby not right away but over time they get ironed out.

 Then again , why ruin a good install in the first place.?

---

### Post by mastablasta on 2010-10-28
> **3Miro said:**
> Who is that someone? That someone is me, the person who already payed them money for the hardware. Now I am only allowed to use it this or that way, the way they feel I should. Why does Ford and Toyota let me look under the hood of my car, I can take the whole engine apart if I wanted to, why are they not worried about their patents? If I do the same with windows OS or some Linux drivers, then I can go to jail. What sense does that make?

Don't know, but my guess is that nvidia will want to have a look at ATI and vice versa. or better yet maybe SiS would liek to have a look into latest nvidia?! this way by the time anyone would reverse engineer something you could already have a new model out there. i mean why else woul dthey make this software proprietary.

yes you can look into the hood of the car but you still can't steal the patent. also you may find out how the engine is made, but not of what is it made.

ever wandered why you can't access easilly firmware from your washing maschine contorl unit or TV or oven? why is that not opensource? i guess if it was you would get access to solutions. access to the selling advantage the firm made with it's own R&D. 

> 
Besides, it isn't that hard to deal with the kernel and Xorg. Older NVIDIA drivers work with both old and new versions of the kernel, you have one standard interface on the kernel side, one interface on NVIDIA binary code and you compile/recompile the connection. It is slow and clumsy, but it works. There is nothing that prevents other manufacturers from doing the same.


yes, but different distros use different kernel versions don't they?
Ati drivers work with new kernel, but not with new x.org. if it is so easy and if cards are so old it really is strange why not release the code out...


> 
some technologically illiterate CEO believes that they have to protect their "corporate secrets". 

ha, ha, ha... you know what? you are probably 100% right.

---

### Post by ventrical on 2010-10-28
Well then we have a 'virtual hardware hell'! :) I mean  to say that the information that comes out of my radio device (stereo reciever) belongs to _ME_ after it leaves the surface of the speaker diaphram. Why else then would their be two cassette tapes built in if it  were not for copying on to those two cassette bays - or CD  for that matter when concerning a PC.?

Personally I think (IMO) that a lot of larger corporations definitly practice strong-arming their customers and putting the muscle on  competitors and motherboard makers and software devs.

  So , my point is , the way it all comes across to me, is that proprietary software devs virtually 'OWN' the music in the space between my speaker and the time it takes to reach my ear. So  they also own the virtual hardware hell also.

  However  most PC users are becoming more and more savvy about OpenSource and devs are becoming more savvy  on how to write drivers for older  video cards. They see the interest where a commercial dev may not care. So it's  a real pain. But those guys loose out because people are learning to make their older systems last longer and why get a new video card when you can make the old one jump through hoops?

  One  user was upset that Outlook Express did not come bundled with Windows 7. I proposed that MS right up a legacy "classic" version of Outlook Express for Windows rather that the Windows Live ( keeping respect in mind for more senior users) and they want no part of it. It's full speed ahead for them and  just keep obsoleting software that people take years to learn.

---

### Post by ubunterooster on 2010-10-28
> **cariboo907 said:**
> I actually saw that message doing a Mythbuntu install the other day. The iso was downloaded from [http://releases.ubuntu.com/]("http://releases.ubuntu.com/"). So the message is valid, it's probably just a dev having some fun.
Same here.

---

### Post by Omnomnom on 2010-10-29
> **cariboo907 said:**
> I actually saw that message doing a Mythbuntu install the other day. The iso was downloaded from [http://releases.ubuntu.com/](http://releases.ubuntu.com/). So the message is valid, it's probably just a dev having some fun.
Aww, I just got a boring old "Restart computer to boot into Ubuntu" message.

---

