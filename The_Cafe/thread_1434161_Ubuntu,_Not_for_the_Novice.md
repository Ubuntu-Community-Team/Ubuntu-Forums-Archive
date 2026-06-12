---
title: "Ubuntu, Not for the Novice?"
date: 2010-03-19
forum: The Cafe
---

### Post by Hman242 on 2010-03-19
I recently realized something lately. I'm getting a new computer in around three weeks. My mom is wanting a new computer because her old desktop isn't near a place to hook it up to the internet. I'm going to give her my current laptop after I get my new one, and that's when I realized it.

As most of you know, Karmic has audio problems. There's no way in Satan's living room that she will be able to run a simple command in the Terminal to fix it. I currently have openSUSE on a partition and I've decided to reinstall it and take up the entire HDD before I give it to her. That's when I realized Ubuntu isn't the most user friendly of the Linux family. It's strange that people complain about Ubuntu being too user friendly, yet this problem has emerged and is keeping someone from using it. It's just a something I thought I would share with you guys. I'm still going to put Ubuntu on my new laptop and I still plan to use it in the future.

---

### Post by mickie.kext on 2010-03-19
OpenSuSE is not bad. You can also try with Mandriva. Or you could install Ubuntu, fix that audio isusse yourself and give her to use.

Use what works best. As long it's Linux:D.

---

### Post by Hman242 on 2010-03-19
I haven't had any problems with it really. Maybe a tad bit slower than Ubuntu, but my mom won't be doing anything serious. Printing, viewing/storing photos, and browsing the web aren't going to overheat my computer.
EDIT: What do you mean fix it? I haven't found any good resolutions except for removing it.

---

### Post by Hman242 on 2010-03-19
Oh don't worry, I'll be putting Gnome on it ;)

---

### Post by mickie.kext on 2010-03-19
> **omgpp said:**
> have u ever tried opensuse kde?

I used SuSE Professional, then later OpenSuSE when Novell bought it. Why do you ask?

---

### Post by warrenc285 on 2010-03-19
> **omgpp said:**
> because opensuse kde 11.2 is the worst distro i have ever used. suse gnome is ok but the kde version is just fudged.

I've been using it for a few weeks and haven't run into any problems.:-|

---

### Post by Khakilang on 2010-03-20
I been using Ubuntu for almost a year now and everything works fine. Maybe you should check out the sound driver or something.

---

### Post by NightwishFan on 2010-03-20
OpenSUSE is great except it always wants to install far too many packages by default. I used to use it full time back when 10.3 was out. It had an EPIC kde desktop then. I still miss it. Since KDE4 came out I switched to Gnome. I am trying to become much more active in Ubuntu so I am now using it full time except for my lower end machines on Debian. I like all three distros though.

As for Mandriva, I have tried it. It is very slick looking and full featured. It seemed a bit Windows-y so I gave up on it.

---

### Post by r4z0r_bl4d3 on 2010-03-20
just a shot in the dark but 9.10 killed audio on my toshiba laptop.

in past versions, 8.10 and prior, I had the same problem with audio (it worked out of the box in 9.04 for some reason.) From what I understand, Ubuntu confuses the sound card with the modem because they are on the same IRQ.  I have solved this problem on my particular laptop (A135-S2386) several times.  I always forget what I did and had to re Google it.

> go to the terminal and:
sudo gedit /etc/modprobe.d/alsa-base.conf

then put this at the bottom:

options snd-hda-intel probe_mask=8 model=3stack

after that kill pulseaudio with this:

killall pulseaudio

after that restart pulse audio:

sudo alsa force-reload

and finally do aplay -l should have something like this:

adamtheo@laptop-satellite:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
Subdevices: 1/1
Subdevice #0: subdevice #0

I know for sure it involves adding a single line in alsa-base.conf.
This has worked for me every time I have an audio problem on a few different laptops.  Hope this is helpful.

---

### Post by cariboo on 2010-03-20
You have to remember that your Mom is like 90% of the computer users out there, she won't be able to fix a problem when it comes up, whether the laptop is running Windows or a Linux variant. I would suggest you don't try and force Ubuntu/OpenSUSE/Fedora on her. Take some time and let her try things out and then decide what to put on it. Don't be surprised if she goes for Windows, and if you aren't around all the time, make sure it's a legal copy.

---

### Post by Kenny_Strawn on 2010-03-20
> **Hman242 said:**
> I recently realized something lately. I'm getting a new computer in around three weeks. My mom is wanting a new computer because her old desktop isn't near a place to hook it up to the internet. I'm going to give her my current laptop after I get my new one, and that's when I realized it.

As most of you know, **Karmic** has audio problems. There's no way in Satan's living room that she will be able to run a simple command in the Terminal to fix it. I currently have openSUSE on a partition and I've decided to reinstall it and take up the entire HDD before I give it to her. That's when I realized Ubuntu isn't the most user friendly of the Linux family. It's strange that people complain about Ubuntu being too user friendly, yet this problem has emerged and is keeping someone from using it. It's just a something I thought I would share with you guys. I'm still going to put Ubuntu on my new laptop and I still plan to use it in the future.

Karmic? Excuse me?

Lucid will be released in six months. Wait until then, and then upgrade to the LTS, which will be very innovative and easy to use. It is much more user friendly than Karmic.

It does have [updates that break it]('http://ubuntuforums.org/showthread.php?t=1434160'), however, at least in Beta 1, out now. Beta 2 and the RC will be released next month, and will certainly be more stable. And the final release will be a week after the RC.

Here is what the Beta 1 looks like:

[ATTACH]150713[/ATTACH]

[ATTACH]150714[/ATTACH]

---

### Post by Dayofswords on 2010-03-20
> **cariboo907 said:**
> You have to remember that your Mom is like 90% of the computer users out there, she won't be able to fix a problem when it comes up, whether the laptop is running Windows or a Linux variant. I would suggest you don't try and force Ubuntu/OpenSUSE/Fedora on her. Take some time and let her try things out and then decide what to put on it. Don't be surprised if she goes for Windows, and if you aren't around all the time, make sure it's a legal copy.

i dont think the same 90% would even know how to get an illegal copy

---

### Post by jayze on 2010-03-20
Old lady learner here!......the netbook remix is very simple to use...(I personally found it simpler than Windows)....set it up for her and just tell her to use it. (as in opposed to tinkering with it)...surely you can fix it for her if theres a real problem......what a thought....condemning your own mother to Windows ..(would you be able to live with yourself? lol)

---

### Post by Hman242 on 2010-03-20
> **Kenny_Strawn said:**
> Karmic? Excuse me?

Lucid will be released in six months. Wait until then, and then upgrade  to the LTS, which will be very innovative and easy to use. It is much  more user friendly than Karmic.

It does have [updates that break it]("http://ubuntuforums.org/showthread.php?t=1434160"), however, at least in Beta 1,  out now. Beta 2 and the RC will be released next month, and will  certainly be more stable. And the final release will be a week after the  RC.

Here is what the Beta 1 looks like:

[ATTACH]150713[/ATTACH]

[ATTACH]150714[/ATTACH]
I know what Lucid looks like. I'm currently typing this up on the beta.  It's actually running without any problems so far, only one minor crash  of something that I can't remember. I said to report it and it said it  had already been.

> **cariboo907 said:**
> You have to remember that your Mom is like 90% of the computer users out there, she won't be able to fix a problem when it comes up, whether the laptop is running Windows or a Linux variant. I would suggest you don't try and force Ubuntu/OpenSUSE/Fedora on her. Take some time and let her try things out and then decide what to put on it. Don't be surprised if she goes for Windows, and if you aren't around all the time, make sure it's a legal copy.

I merely suggested the idea, and she thought it was a very good idea. She doesn't need that good of a computer, just one that is reliable and runs. I would benefit more from having a new computer than she would. I'm not sure if I should get her to use Ubuntu 10. When I get the new computer, I assume she is going to want mine the very same day.  I want her to be able to keep all her stuff and whatnot that she will have acquired since she has started using it, so that means she probably isn't going to want to change her OS since it doesn't matter that much.

---

### Post by Kenny_Strawn on 2010-03-20
> **Hman242 said:**
> I know what Lucid looks like. I'm currently typing this up on the beta.  It's actually running without any problems so far, only one minor crash  of something that I can't remember. I said to report it and it said it  had already been.

Just [don't 'sudo apt-get upgrade' or use Update Manager until all bugs in the repos get ironed out]('http://ubuntuforums.org/showthread.php?t=1434160').

---

### Post by 3rdalbum on 2010-03-20
> **Kenny_Strawn said:**
> Lucid will be released in six months.

Lucid will be released in five weeks, not six months.

Also I actually haven't seen these "problems with audio" that are so widespread. Flash Plugin won't use my USB headset when I have it selected in Pulseaudio; but I imagine your gramma won't hit this problem (which I believe would happen on any distro anyway).

---

### Post by the yawner on 2010-03-20
Your Karmic was problematic, mine hardly. Your mileage will always vary, but Ubuntu at least tries this hand-holding approach. :)

---

### Post by jayze on 2010-03-20
Hmmm something just caught my eye!....maybe I shouldn't say this but here goes...when I was shopping round for a Windows install disc (and getting gobsmacked by the prices)..I was offered loads of choice from absolutely everywhere..but they all came with a "but you can't update it" or "don't go on the net with it" warning...otherwise if I wanted to avoid being thrown in microsofts dungeons the choices were three...Windows direct..Argos...or Currys.........              Maybe its a reflection on the company I keep (lol my own usually)...        And I just ran it through in my mind and Yes...everyone I know barr maybe two or three are running Ubuntu...a few Mac...and the rest illegal Windows.        This has confirmed now that Yes I Am Off a Different Planet...which I have suspected very often since embarking on this great techno adventure.

---

### Post by Shpongle on 2010-03-20
> **r4z0r_bl4d3 said:**
> just a shot in the dark but 9.10 killed audio on my toshiba laptop.

in past versions, 8.10 and prior, I had the same problem with audio (it worked out of the box in 9.04 for some reason.) From what I understand, Ubuntu confuses the sound card with the modem because they are on the same IRQ.  I have solved this problem on my particular laptop (A135-S2386) several times.  I always forget what I did and had to re Google it.



I know for sure it involves adding a single line in alsa-base.conf.
This has worked for me every time I have an audio problem on a few different laptops.  Hope this is helpful.

change the model to lenovo to fix it , thats usually done it for me before on my toshiba. it works outta the box for me now

---

### Post by leandromartinez98 on 2010-03-20
> **Hman242 said:**
> 
As most of you know, Karmic has audio problems.

Does OpenSuse doesn't have the same problems? (I'm really asking)

---

### Post by xpod on 2010-03-20
> Re: Ubuntu, Not for the Novice?

Not something i myself could ever agree with but i will say that anyone trying out the whole discover, burn, try, install and use Ubuntu/Linux experience needs to be just a little more Gung Ho than the average novice usually is. Most long time computer users i know are still too terrified to even navigate through a menu, let alone install a new OS. 
Having it pre-installed & configured by Dell, System76 or even the geeky guy next door is another matter entirely of course.

No different to Windows in that regard.

---

### Post by XubuRoxMySox on 2010-03-20
*Any* Linux distro that throws in experimental, risky, troublesome Beta software by default (PulseAudio, Grub2, etc) is not for novices. When it works, it's cool. But when it doesn't, PulseAudio for example has been troublesome even for experienced Linux users. Handing newbies Beta software and expecting them to be just fine with it is just unforgivable. It is one of Ubuntu's most prominent of sins against newbies - but Ubuntu is certainly not the only such offender that makes unwitting lab rats out of Linux novices.

-Robin

---

### Post by JDShu on 2010-03-20
> **xpod said:**
> 
Having it pre-installed & configured by Dell, System76 or even the geeky guy next door is another matter entirely of course.

+1

I you really want it to work for your mom with no hassle for her, get a preinstalled from Systemy 76, ZaReason, or maybe Dell (though I've heard their linux support is sketchy)

---

### Post by Kenny_Strawn on 2010-03-20
> **3rdalbum said:**
> Lucid will be released in five weeks, not six months.

Also I actually haven't seen these "problems with audio" that are so widespread. Flash Plugin won't use my USB headset when I have it selected in Pulseaudio; but I imagine your gramma won't hit this problem (which I believe would happen on any distro anyway).

Sorry, I meant weeks. Sorry for the typo.

---

### Post by madjr on 2010-03-20
> **dixiedancer said:**
> *Any* Linux distro that throws in experimental, risky, troublesome Beta software by default (PulseAudio, Grub2, etc) is not for novices. When it works, it's cool. But when it doesn't, PulseAudio for example has been troublesome even for experienced Linux users. Handing newbies Beta software and expecting them to be just fine with it is just unforgivable. It is one of Ubuntu's most prominent of sins against newbies - but Ubuntu is certainly not the only such offender that makes unwitting lab rats out of Linux novices.

-Robin
+1

i have to agree

ubuntu been breaking my stuff for years

it would be much better if we kept a separate "**experimental and testing** release/branch" like **debian** does

there's no excuse not to

---

### Post by alexfish on 2010-03-20
> **dixiedancer said:**
> *Any* Linux distro that throws in experimental, risky, troublesome Beta software by default (PulseAudio, Grub2, etc) is not for novices. When it works, it's cool. But when it doesn't, PulseAudio for example has been troublesome even for experienced Linux users. Handing newbies Beta software and expecting them to be just fine with it is just unforgivable. It is one of Ubuntu's most prominent of sins against newbies - but Ubuntu is certainly not the only such offender that makes unwitting lab rats out of Linux novices.

-Robin

I love been a lab rat :p  But not a unwitting one :P

Linux is a freedom of Choice :o

---

### Post by J_Stanton on 2010-03-20
> **NightwishFan said:**
> OpenSUSE is great except it always wants to install far too many packages by default.  i noticed that too. i'm not going to try opensuse again for a LONG time. every time i do, i'm disappointed. every distro works good for me EXCEPT opensuse. weird.

---

### Post by RabbitWho on 2010-03-20
What is the newbiest of the newb linux distro? I'd like to give my parents a go and like that I won't always be around to help them. Even with windows every time I see them there are a few things on the computer need to be fixed. 

I thought linux must be for newbies since I'm able to use it but it's certainly not for necessary people who just want the internet to go online, use word processors, read PDFs, save pictures, listen to music. 

> 
			 		 	 	 +1

i have to agree

ubuntu been breaking my stuff for years

it would be much better if we kept a separate "**experimental and  testing** release/branch" like **debian** does

there's no excuse not to 	

In my opinion we are the testers, that's how the company stays in business, it has the most stable product to offer because thousands and thousands and thousands of people test every release. It's an excellent system, we get a free OS out of it and they get more testers than they would if they had a separate testing branch.

---

### Post by MasterNetra on 2010-03-20
> **RabbitWho said:**
> **What is the newbiest of the newb linux distro? I'd like to give my parents a go and like that I won't always be around to help them.** Even with windows every time I see them there are a few things on the computer need to be fixed. 

I thought linux must be for newbies since I'm able to use it but it's certainly not for necessary people who just want the internet to go online, use word processors, read PDFs, save pictures, listen to music. 



In my opinion we are the testers, that's how the company stays in business, it has the most stable product to offer because thousands and thousands and thousands of people test every release. It's an excellent system, we get a free OS out of it and they get more testers than they would if they had a separate testing branch.

I'd say that might be Google Chrome when its officially released. ...whenever that might be...

---

### Post by wojox on 2010-03-20
> **RabbitWho said:**
> What is the newbiest of the newb linux distro? I'd like to give my parents a go and like that I won't always be around to help them. Even with windows every time I see them there are a few things on the computer need to be fixed. 

I thought linux must be for newbies since I'm able to use it but it's certainly not for necessary people who just want the internet to go online, use word processors, read PDFs, save pictures, listen to music. 



In my opinion we are the testers, that's how the company stays in business, it has the most stable product to offer because thousands and thousands and thousands of people test every release. It's an excellent system, we get a free OS out of it and they get more testers than they would if they had a separate testing branch.

Try LinuxMint

---

### Post by Uncle Spellbinder on 2010-03-20
> **wojox said:**
> Try LinuxMint

Which is nothing more than a green Ubuntu Karmic with a few Mint-specific apps. After all, they even use the Karmic repos.

---

### Post by wojox on 2010-03-20
> **Uncle Spellbinder said:**
> Which is nothing more than a green Ubuntu Karmic with a few Mint-specific apps. After all, they even use the Karmic repos.

Agreed but it is pretty newb friendly as far as having everything pre-installed. :D

---

