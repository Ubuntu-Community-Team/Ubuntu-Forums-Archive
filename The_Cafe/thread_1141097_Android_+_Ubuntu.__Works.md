---
title: "Android + Ubuntu.  Works?"
date: 2009-04-28
forum: The Cafe
---

### Post by Kosimo on 2009-04-28
How compatible is an Android based phone with Ubuntu? In terms of, managing it, update the software, install apps, etc etc.

I guess that when you buy an android phone it comes (probably) with a CD which has a bunch of software to install in a Windows or MAC environment.   How about Ubuntu? Do we have the same support?


If there is any Android owner around here, please give us your impression!

Thanks

---

### Post by aktiwers on 2009-04-28
I have one and it works fine with my Ubuntu PC. The apps and updates for android are done on the phone, using wireless. The connection to the computer recharges the phone fine, and you can move your photos to the computer. 
You can drag music from the computer to the phone as well.

Actually Ubuntu mounts it as a phone, and then you can drop files to or from it, as android detects what is music and what is pics..

---

### Post by Kosimo on 2009-04-28
> **aktiwers said:**
> I have one and it works fine with my Ubuntu PC. The apps and updates for android are done on the phone, using wireless. The connection to the computer recharges the phone fine, and you can move your photos to the computer. 
You can drag music from the computer to the phone as well.

Actually Ubuntu mounts it as a phone, and then you can drop files to or from it, as android detects what is music and what is pics..

Cool, that is good to know.
Have you ever tried to use your Android Phone as a HSDPA Modem to connect to internet using Network Manager?

---

### Post by aktiwers on 2009-04-28
> **Kosimo said:**
> Cool, that is good to know.
Have you ever tried to use your Android Phone as a HSDPA Modem to connect to internet using Network Manager?

Nope..  But sounds interesting. Maybe I should try it out.

HTC G1 Android seams to be the best phone I have ever had, to work with Ubuntu.

---

### Post by Kosimo on 2009-04-28
> **aktiwers said:**
> Nope..  But sounds interesting. Maybe I should try it out.

HTC G1 Android seams to be the best phone I have ever had, to work with Ubuntu.

Cool, I'm considering to buy it as well. Would be good to know anyway if you could connect it. In fact should be really easy to do it with Network manager

---

### Post by steev182 on 2009-05-08
How does Android play with xvid/divx? One of the reasons I would like to move to Android from iPhone is that I don't want the workflow of converting from xvid to mp4.

---

### Post by azanutta on 2009-05-17
has anyone an idea of this sync problem with android?!?
[http://ubuntuforums.org/showpost.php?p=7296106&postcount=5](http://ubuntuforums.org/showpost.php?p=7296106&postcount=5)

and i'd also like to know how to convert my videos in order to see them in the device! =) tnx

---

### Post by aktiwers on 2009-05-17
> **azanutta said:**
> has anyone an idea of this sync problem with android?!?
[http://ubuntuforums.org/showpost.php?p=7296106&postcount=5](http://ubuntuforums.org/showpost.php?p=7296106&postcount=5)

and i'd also like to know how to convert my videos in order to see them in the device! =) tnx

I have the G1 and I just drag the music files to the root of the G1, then it index it all automatically in the G1 music player.

---

### Post by ELD on 2009-05-17
I have the G1 best phone i ever had and i'm not just saying that, it rocks!

---

### Post by azanutta on 2009-05-17
> **aktiwers said:**
> I have the G1 and I just drag the music files to the root of the G1, then it index it all automatically in the G1 music player.

i know it's a possible way to sync your music, just simply copy and paste in nautilus BUT:
[LIST]
[*]i'd like to have the folder automatically organized by author and album in the way that banshee does
[*]i'd like to simply edit the tags of my music on the fly and then eventually sync ... (artwork too)
[*]the playlist thing.... it'll be wonderful if the program will handle also the playlists and syncs them too
[/LIST]

anyway... i can't figure out jet if the rhythmox and amarok that not sync the G2 it's an issue of my PC or DEVICE, or a bug in the software (ubuntu, MTP plugin, music player)... if anyone could try this too...... tnx

---

### Post by helliewm on 2009-05-17
I can't seem to get my G1 to mount a phone. Any ideas?

> Actually Ubuntu mounts it as a phone, and then you can drop files to or from it, as android detects what is music and what is pics..

Helen

---

### Post by aktiwers on 2009-05-17
> **helliewm said:**
> I can't seem to get my G1 to mount a phone. Any ideas?



Helen

When you connect it, you need to pick "mount device" on the Android Phone.
Then it will popup in Ubuntu

And sorry Azunatta, I have no idea :(

---

### Post by KhaaL on 2009-08-11
I just got myself a samsung galxy, but it dosent automount nor show up in nautilus when connected through the USB.  running dmesg | tail gives:
> 
[18013.348743] scsi10 : SCSI emulation for USB Mass Storage devices
[18013.357130] usb-storage: device found at 10
[18013.357137] usb-storage: waiting for device to settle before scanning
[18018.357758] usb-storage: device scan complete
[18018.360711] scsi 10:0:0:0: Direct-Access     Samsung  SAMSUNG Android  Mass PQ: 0 ANSI: 2
[18018.362693] scsi 10:0:0:1: Direct-Access     Samsung  SAMSUNG Android  Mass PQ: 0 ANSI: 2
[18018.364530] sd 10:0:0:0: Attached scsi generic sg8 type 0
[18018.365779] sd 10:0:0:1: Attached scsi generic sg9 type 0
[18018.386935] sd 10:0:0:0: [sdh] Attached SCSI removable disk
[18018.395932] sd 10:0:0:1: [sdi] Attached SCSI removable disk


Even trying with sudo mount /dev/sdi ~/ returns a *mount: /dev/sdi: unknown device* error... Anyone with ideas?

---

### Post by aktiwers on 2009-08-12
Did you click "mount" on the phone (in android) after you connected it?

---

### Post by KhaaL on 2009-08-12
> **aktiwers said:**
> Did you click "mount" on the phone (in android) after you connected it?

 Sometimes i wonder why I go through the hard way when the solution is right under my nose. I am now officially a nublet. Thanks :-]

---

### Post by saunders on 2009-08-21
> **KhaaL said:**
> I just got myself a samsung galxy... 

Completely off topic, but what's the phone like? Call quality, speed, responsiveness? It's either this one or the HTC Hero for me...

---

### Post by KhaaL on 2009-08-21
** OT warning for the sensitive **

Samsung galaxy is one of the best buys i've ever made. the software shortcomings is mostly fixed by free software on the market (except for video recording resolution which is last century quality). The two "meh"s of the phone is the anti-standard USB connector and the lack of radio. the big, big drawback however is the battery life, which is drained like a !@# even with 3g / wifi / gps turned off. The only thing i use the phone intensively for is mp3 playing.

EDIT: and bluetooth turned off too. the battery is 1500mA

---

### Post by castrojo on 2009-08-21
> **azanutta said:**
> 
[*]i'd like to have the folder automatically organized by author and album in the way that banshee does
[*]i'd like to simply edit the tags of my music on the fly and then eventually sync ... (artwork too)
[*]the playlist thing.... it'll be wonderful if the program will handle also the playlists and syncs them too
[/LIST]

I use my G1 with Banshee, here's how I manage it. I create a smart playlist and limit it to 15gb (I have a 16gb card)  and then sort it by Score. (Score is available in the 1.5.x series of Banshee, basically it's like an autorating, this ensures only the songs I like make it onto the G1 since I have over 16gb of music).

Then when I want to sync I just plug it in and then drag the list onto the G1. The artwork and all that stuff syncs fine.

As far as playlists this is a real bummer. I asked Aaron Bockover how hard this would be to implement in Banshee and initially said it would be easy but after looking at it it was much harder than he thought it was. I /think/ you can just drop .m3u files on the card though ...

---

### Post by shellmich on 2009-08-30
> **aktiwers said:**
> Did you click "mount" on the phone (in android) after you connected it?

Where can I click "mount" on the Samsung Galaxy after I connect the usb cable to the Ubuntu 9.04 PC?

My Samsung Galaxy only recognized the USB connection to the PC by showing the icon for "Mit PC verbunden" i.e. "connected with PC" but nothing else happens.

---

### Post by KhaaL on 2009-08-30
on the grey bar at the top, drag it down and click on the "USB connected" line. there you can choose to mount it and from there you can transfer files freely :)

> **shellmich said:**
> Where can I click "mount" on the Samsung Galaxy after I connect the usb cable to the Ubuntu 9.04 PC?

My Samsung Galaxy only recognized the USB connection to the PC by showing the icon for "Mit PC verbunden" i.e. "connected with PC" but nothing else happens.

---

### Post by Pat Benson on 2009-09-13
I've had the HTC hero for about 3 weeks now and I really enjoy it and the features especially the calendar though I'd like to have a better week overview, it's really easy to sync with google calendar, and makes it easy for me to organise work, studies and leisure (and my recent addiction to Bonsai Blast :P )

However one thing that is abit frustrating is that it lagg slightly and from what I've heard the new ROM should make it much more snappy. The sad thing is tho that in my choice trying to avoid M$ I still find myself in their claws when it comes to upgrade the ROM(I didn't choose Android, I rejected any other propriety OS on my phone)

[From HTC support/install instructions:]("http://www.htc.com/se/SupportDownload.aspx?p_id=283&cat=2&dl_id=671")
> **2. Software Requirements - Supported Operating Systems (PC)**
Windows XP Home Edition Service Pack 2
Windows XP Professional Edition Service Pack 2
Windows XP Media Center Edition Service Pack 2
Microsoft Windows Vista Ultimate Edition
Microsoft Windows Vista Enterprise Edition
Microsoft Windows Vista Business Edition
Microsoft Windows Vista Home Premium Edition
Microsoft Windows Vista Home Basic Edition



So my question is, have anyone had any "luck" upgrading their HTC/Android phone without windoze or without rooting/hacking it?
I've tried using HTC sync +wine without any success (reports say that HTC works less then good even with windows), I'm using Kubuntu 8.10 and haven't yet found any thread here, KFN, xda-dev, or from HTC support without any luck.
Best option so far have been to use VMware and upgrade from there, but seems as a long procedure (and I'll need a copy of windows anyway) for a 10 min upgrade on the phone. :(

---

### Post by Lizzy on 2009-09-17
I had my HTC Hero for 1 month now, and i'm realy happy with it.
As for upgrading the ROM, i had to "kidnap" my roomy's Vista Laptop as all other ways of doing this (wine/VMware) didn't work. It didn't take more than 5 minutes to do that, but downloading HTC sync and the ROM file seemed to take ages. In reward my phone realy is MUCH,MUCH snappier..... A real improve :) :popcorn:

---

### Post by Mateo on 2009-09-17
I think you're coming at it from the wrong angle.  This is 2009.  Smart phones *ARE COMPUTERS*.  You don't "manage" them with another computer.  The only time you need to attach your android phone to a computer is to transfer file (which you can, just like a flash drive).

---

### Post by Kosimo on 2009-09-19
> **Mateo said:**
> I think you're coming at it from the wrong angle.  This is 2009.  Smart phones *ARE COMPUTERS*.  You don't "manage" them with another computer.  The only time you need to attach your android phone to a computer is to transfer file (which you can, just like a flash drive).

That's the best point I've read in this thread so far

---

### Post by steev182 on 2009-09-19
The HTC Magic can update over the air, so there is no need for Windows with these phones. The only time you'll need any part of the phone plugged into a computer is to charge it or to get media onto it.

---

### Post by KhaaL on 2009-09-21
> **steev182 said:**
> The HTC Magic can update over the air, so there is no need for Windows with these phones. The only time you'll need any part of the phone plugged into a computer is to charge it or to get media onto it.

I envy you. my samsung galaxy requires samsung pc studio wich is windows only in order to update firmware. 

sucks!

---

### Post by jackhynes on 2009-09-26
> **Mateo said:**
> I think you're coming at it from the wrong angle.  This is 2009.  Smart phones *ARE COMPUTERS*.  You don't "manage" them with another computer.  The only time you need to attach your android phone to a computer is to transfer file (which you can, just like a flash drive).

> **steev182 said:**
> The HTC Magic can update over the air, so there is no need for Windows with these phones. The only time you'll need any part of the phone plugged into a computer is to charge it or to get media onto it.

I believe you do *need* to use a Windows program to update the ROM, at least with a Hero you do. As far as I know I haven't seen a solution to the Windows requirement. As for the update over the air, that's for firmware updates not ROM updates.

---

### Post by JCFranklin on 2010-03-20
> **aktiwers said:**
> Nope..  But sounds interesting. Maybe I should try it out.

HTC G1 Android seams to be the best phone I have ever had, to work with Ubuntu.

If you are on AT&T - DON'T use it as a modem, AT&T will change the contract and charge you ridiculously.  Read the fine print on your carrier agreement. 

I love my Backflip.

---

### Post by Amit Howard on 2010-04-09
Can anyone tell me how to sync my phone contacts to my computer? or vice versa?
And also how to transfer calendar entries and notes back and forth?

Right now I'm stuck in India and have no access to Wi-Fi on my phone to back it up online (if there is a way to do that too).

I have Ubuntu Karmic Koala on my computer. The phones (Samsung I7500 Galaxy) connects well with the computer. No problem transferring files back and forth. Also recognised as GSM Mobile Broadband Internet in the Available Networks etc.

I tried to install the official Pc Suite with wine but it didn't work. I tried to connect it with Windows XP on another computer but it shows the I7500 (Galaxy) as an unsupported device in the Suite. The drivers are installed properly (including the adb drivers) but no connection of the phone with the pc suite.

What can I do???
PLEASE HELP 
Amit
(DESPERATE NEWBIE)

---

### Post by aysiu on 2010-04-09
> **Amit Howard said:**
> Can anyone tell me how to sync my phone contacts to my computer? or vice versa?
And also how to transfer calendar entries and notes back and forth?

Right now I'm stuck in India and have no access to Wi-Fi on my phone to back it up online (if there is a way to do that too). No wireless *and* no data plan? 

If you have a data plan, you should be able to sync automatically to your Google account. If you don't have a data plan *or* wireless, I don't know why you got a smartphone.

---

### Post by Amit Howard on 2010-04-10
Well... I said I'm STUCK In India (atleast for another month) Usually the rest of the places where I travel I DO have access to internet. THAT'S why I got a smartphone.

---

### Post by typos1 on 2010-05-06
> **aysiu said:**
> No wireless *and* no data plan? 

If you have a data plan, you should be able to sync automatically to your Google account. If you don't have a data plan *or* wireless, I don't know why you got a smartphone.

I ve had smartphones for the last 6 years and rarely use wireless or data, you can go online with most non smartphones nowadays, so thats a ridiculous thing to say, there a lots reasons to have a smartphone- organiser, apps, music, videos, office, file editing, gaming, voice recording, video, ereader etc etc etc

I ve just moved to Android after 6 years of Window Mobile and Android isnt as good as I thought it would be-you cant sync properly-Why would I want to use Google's online servers just to sync to my ubuntu pc? Thats mad. 

With Windows Mobile you need Windows to reflash the ROM, plus you can do other stuff, there are apps that let you access pc from phone and phone from pc (wired or bluetooth or internet). 

Plus as an Android device is a small pc its quite reasonable to want your small pc and your large pc to talk to each other, but you cant. 

It seems that while Ubuntu/Linux is better than Windows for pcs, Windows is better than Linux for mobile device, bizarre and ironic.

---

### Post by Kosimo on 2010-05-07
> **typos1 said:**
> I ve had smartphones for the last 6 years and rarely use wireless or data, you can go online with most non smartphones nowadays, so thats a ridiculous thing to say, there a lots reasons to have a smartphone- organiser, apps, music, videos, office, file editing, gaming, voice recording, video, ereader etc etc etc

I ve just moved to Android after 6 years of Window Mobile and Android isnt as good as I thought it would be-you cant sync properly-Why would I want to use Google's online servers just to sync to my ubuntu pc? Thats mad. 

With Windows Mobile you need Windows to reflash the ROM, plus you can do other stuff, there are apps that let you access pc from phone and phone from pc (wired or bluetooth or internet). 

Plus as an Android device is a small pc its quite reasonable to want your small pc and your large pc to talk to each other, but you cant. 

It seems that while Ubuntu/Linux is better than Windows for pcs, Wundos is better than Linux for mobile device, bizarre and ironic.


I agree 100%.

There is no way that you buy a linux phone and you can sync everything with Windows but not with Ubuntu.

---

### Post by amitabhishek on 2010-05-07
> **Amit Howard said:**
> Well... I said I'm STUCK In India (atleast for another month) Usually the rest of the places where I travel I DO have access to internet. THAT'S why I got a smartphone.

WTH? :confused: 

Internet in India is available in very much the same way as rest of the world-by paying! There has to be at least 20 ISPs here.

---

### Post by sanket_s on 2010-05-21
I got the Samsung Spica, works great as stand alone PDA, no need to connect to PC at all. Would have liked a sync system to back up contacts etc all data for contacts go to your Google account and hence its manageable from there. 

The device is designed to be on a always-on some form of network and needs that, so if you switch off wifi it starts GPRS/EDGE by default. I'm from India and EDGE is pretty much available in every corner of the country with affordable data plans (affordable for one buying INR 15k smartphones).

I found some articles for syncing music properly using Banshee as you would do with a iPod. Nothing to do with the android phone as such, just tinkering the microSD card to look like a music player. Still would like it to sync with more players Amarok, Rhythmbox etc.

---

### Post by Paqman on 2010-05-21
> **typos1 said:**
> 
I ve just moved to Android after 6 years of Window Mobile and Android isnt as good as I thought it would be-you cant sync properly-Why would I want to use Google's online servers just to sync to my ubuntu pc? Thats mad. 


If you don't want to use your Google account on a phone, don't use Android. It's (perhaps unsurprisingly) designed to be centered around your Google account. Personally I think that's incredibly convenient, but then i've been using Google's stuff on all my computers for yonks, so it suits me down to the ground.

---

### Post by typos1 on 2010-05-21
I ve been using Google's search engine for years. I use it out of choice.

I dont want to be forced to use one of its other services unnecessarily (like to sync to my pc or to,look at the calender on my phone) just so they can try and generate advertising income form anything I click on.

I hadnt realised Android was set up to benefit Google's coffers rather than the user.

I want Linux on my mobile device, I dont want an income generation excercise for Google.

---

### Post by aysiu on 2010-05-21
> **typos1 said:**
> I ve been using Google's search engine for years. I use it out of choice.

I dont want to be forced to use one of its other services unnecessarily (like to sync to my pc or to,look at the calender on my phone) just so they can try and generate advertising income form anything I click on.

I hadnt realised Android was set up to benefit Google's coffers rather than the user.

I want Linux on my mobile device, I dont want an income generation excercise for Google.
What you're saying doesn't make sense. Google makes advertising money off searches, not off calendaring.

And it's not for them rather than the user... it's for them *and* the user, providing the user finds Google's services useful (which many, but not all, do).

If you don't find Google useful, you won't find Android useful either. Many others do, however.

---

### Post by Timmer1240 on 2010-05-21
I was telling my buddy about the new android phone the next day he came over He had one they look awesome he had an Lg chocolate his wifes got that now Hes on the Android now!Hes a phone junkie everytime a new one comes out he has to have it!Its funny hes had a lot of different phones in the last two years!Me I got an old samsung the screen is shot all I can do is make and receive phone calls works for me!

---

### Post by typos1 on 2010-05-26
> **aysiu said:**
> What you're saying doesn't make sense. Google makes advertising money off searches, not off calendaring.

And it's not for them rather than the user... it's for them *and* the user, providing the user finds Google's services useful (which many, but not all, do).

If you don't find Google useful, you won't find Android useful either. Many others do, however.


What I am saying makes perfect sense-I dont want to have to go online just to look at the calender on my phone, I dont want to go online just to "sync" my phone with my pc. There is no need to go online to check my calender, there is no need to have to go online to sync to my pc, all other operating sytems allow these things without going online, what other reason would Google force someone to go online unessecarily? 

What next? Having to go online to answer a call?!

And what if theres no signal? Then I cant check my calender or sync to my pc-its ridiculous.

As I ve said I find Google's search services very useful, but thats irrelevant. And to suggest that if I dont find Google useful that I wouldnt find Android useful is similarly ridiculous. Android is an OS and if I need an OS so if I need an OS for my mobile device then I should "find it useful".

Android forces the user to use Google services, even if when you dont need to, theyre acting very similar to Microsoft. I ll wait til I can put Ubuntu on my mobile device.

---

### Post by aysiu on 2010-05-26
> **typos1 said:**
> 
Android forces the user to use Google services, even if when you dont need to, theyre acting very similar to Microsoft. I ll wait til I can put Ubuntu on my mobile device. That's like saying cars force people to drive. Cars don't force people to drive. People buy cars because they want to drive. Likewise, people buy Android phones to use Google services. If you don't like Google services, you don't buy an Android phone.

My Google calendar works just fine when I don't have a signal. It doesn't go online to check my calendar. It downloads a local copy of my calendar and periodically syncs it to Google's servers, in case I make a change to my Google calendar on another device.

---

### Post by typos1 on 2010-05-26
No, no, no, people buy Android phones because they want a smartphone (ie a camera, a pda, a media player, a phone, a storage device, a browser, a gps device etc, etc) not cos they want to use Google's services. I ve had smartphones for years and I ve never brought one to use Google's services. I may have used Google's services on it sometimes, but I never brought a phone specifically to use Google. I very much doubt anyone ever has. Been a member of many online smartphone forums and no one has ever said they want a smartphone just for Google.

If you want a car analogy then it would be like buying a car and being forced to drive somewhere ONLY via a particular route, even when there are other more convenient routes.

Any other phone operating system allows you to simply check your diary, which is on the phone. If you want you can sync it via cable, or via the internet. 

Android-you have to use the internet and register with Google first. 

And what if you want to put a date in your calender? You have to go online to do it so then the device can go online to update it!! Why cant you just put the date on the calender on your phone!!?? Madness.

Firstly if there is no service then you cant check an up to date copy of your diary.

Secondly, why cant I have the same 3 choices as WinMo, Symbian, RIM or the iphone?

I use Ubuntu cos its open source and not tied to any one company. Android is tied to Google, I am a member of loads of smartphone forums and I ve heard a lot about Android, most good and I was so looking forward to getting it, but its the biggest disappointment ever. Never thought I d rate a Microsoft product over a Linux based one, but for mob devices I do, despite WinMo's faults.

There is so much you cannot do with Android that you can do with WinMo.

You HAVE to put all your contacts on the phone, you cant read them from the SIM, unlike every other phone I ever had (including non smartphones)

Their is no task manager.

You cant sync properly abnd access the filesystem

You cannot PIN lock the device.

There is no phone keypad for one handed use.

It takes ages to boot, just as long as WinMo.

Not enough space to list all the settings you simply cant tweak, but that you can with WinMo (with WinMo you can tweak almost anything, like you can a pc)

---

### Post by aysiu on 2010-05-26
> **typos1 said:**
> No, no, no, people buy Android phones because they want a smartphone (ie a camera, a pda, a media player, a phone, a storage device, a browser, a gps device etc, etc) not cos they want to use Google's services. I beg to differ. If they didn't want Google services, they wouldn't get a Google-branded phone. There are plenty of other smartphones out there. They could get a Palm Pixi, an iPhone, a Blackberry, etc. > I ve had smartphones for years and I ve never brought one to use Google's services. Exactly my point. So if you were to get an Android smartphone, as opposed to all the other ones you've used over the years, you would be getting it for the Google services, because they are an integral part of the phone. > I may have used Google's services on it sometimes, but I never brought a phone specifically to use Google. I very much doubt anyone ever has. Been a member of many online smartphone forums and no one has ever said they want a smartphone just for Google. I didn't say "just for Google and nothing else." But to imagine that you would get a Google phone and not use Google services is just not living in reality.

> If you want a car analogy then it would be like buying a car and being forced to drive somewhere ONLY via a particular route, even when there are other more convenient routes. No, it wouldn't. That analogy just doesn't hold up, because you get a phone for what it can do, not how it does it. I can call any number any other smartphone can call. I can search for anything any other smartphone can search for. I'm not limited in any way except that I use Google services to do it.

> Any other phone operating system allows you to simply check your diary, which is on the phone. If you want you can sync it via cable, or via the internet. You can also check your diary on your Google phone. What's to stop you from doing that? I don't think you understand that Android phones store everything locally and then just sync to Google servers. Things do not live solely on Google servers. Most everything personal is on your SD card, so if you want to copy that to your computer, you just hook up the USB and copy it.

> And what if you want to put a date in your calender? You have to go online to do it so then the device can go online to update it!! Why cant you just put the date on the calender on your phone!!?? Madness. No, you put the date on your calendar, and it goes on. When you finally do get online, it'll automatically sync to the online calendar.

> Firstly if there is no service then you cant check an up to date copy of your diary. How would you check it on another phone? If you can't go online, there are only two options--copy it to your SD card, which you can do on an Android phone, or wait until your get a signal and sync it online, which you can also do on an Android phone.

> Secondly, why cant I have the same 3 choices as WinMo, Symbian, RIM or the iphone? What three choices are you talking about?

> 
You HAVE to put all your contacts on the phone, you cant read them from the SIM, unlike every other phone I ever had (including non smartphones) [http://www.lazybit.com/index.php/2010/02/03/google-contacts-sim-card-sync-tool?blog=2](http://www.lazybit.com/index.php/2010/02/03/google-contacts-sim-card-sync-tool?blog=2)

> Their is no task manager. There doesn't need to be one, but you can install one from the Android market. There are actually plenty.

> You cant sync properly abnd access the filesystem Sure you can. You just mount it as removable storage.

> You cannot PIN lock the device. Sure you can.

> There is no phone keypad for one handed use. Yes there is.

> Not enough space to list all the settings you simply cant tweak, but that you can with WinMo (with WinMo you can tweak almost anything, like you can a pc) Not enough space to list FUD. You clearly haven't used an Android phone for more than a few minutes. I own an Android phone and have for almost a year. I assure you you don't know what you're talking about.

There is one thing I will agree with you on, though: if you don't like Google services, your needs will probably not be *best* met with an Android phone; just as if you use Linux as your primary or only OS, your needs will probably not be *best* met with an iPhone or iPod Touch, despite recent advances with libimobiledevice.

Look, if you don't like Google services, I'm not going to try to convince you to use an Android phone. My point is quite the opposite: people who buy Android phones should (and they usually do) realize that you get the most of the phone by using Google services, since it is a Google phone. I'm sure there are ways to manage an iPhone with iTunes, but that's not how you're going to get the most out of an Apple mobile device.

You can also probably use Linux with a Broadcom wireless card (I know I do), a Lexmark printer, and Adobe CS in Wine, but if that's what you have, your needs will be better served with Windows.

Please stop trying to pretend that people who want nothing to do with Google are buying Android phones and then being surprised that those phones actually use Google services.

---

### Post by Spike-X on 2010-05-26
> **typos1 said:**
> What I am saying makes perfect sense-I dont want to have to go online just to look at the calender on my phone, I dont want to go online just to "sync" my phone with my pc. There is no need to go online to check my calender, there is no need to have to go online to sync to my pc, all other operating sytems allow these things without going online, what other reason would Google force someone to go online unessecarily? 

What on earth are you talking about? You don't have to go online to look at your calendar. You have the *choice* of syncing the phone's calendar to your Google calendar (if you have one; I don't, and the calendar on my Android phone works just fine).

---

### Post by Spike-X on 2010-05-26
> **typos1 said:**
> 
And what if you want to put a date in your calender? You have to go online to do it so then the device can go online to update it!! Why cant you just put the date on the calender on your phone!!?? Madness.

This is simply incorrect. See my post above.

---

### Post by karatedog on 2010-06-01
I'm bit of a personal data control freak, so in my point of view:

> **aysiu said:**
> If you don't like Google services, you don't buy an Android phone.
This message didn't come through the ads as far as I remember, and I don't think it is Google that drives the mobile operators, but the other way around. Nexus One is the clear example. Is there an "only 2 Nexus One per person" buying limit? No. People buy nice-looking, smart devices, not "Google service compatible devices".

I like to store my personal data on my personal devices only, let's say I'm oldschool. But on the other hand there is no benefit at all for me to store my personal data at Google, so why should I? (calendar entries being a personal data for me)

I had my own e-mail before Google, and I tend to use Outlook/KOrganizer for calendar (or used to, as of now I try to live on Ubuntu) because I work at 5 projects in 3 different companies. But Microsoft Windows and its Office friends still dominate the corporate market, so Outlook is an unavoidable source of calendar entries, even for Google. In my case to have all of my calendars entries in the phone the work-flow should be:
1. Windows -> local sync from Exchange
2. Google sync (online) from the phone 
3. Ubuntu -> local sync from Google Calendar (say, with KOrganizer), and local entries up to Google Calendar.
That's bad. I want my (own) smartphone be the central data collector, and not Google and this could be easy. I plug the phone into Windows, then sync, then go home and put it into Ubuntu, then sync. No online thingie included. Same as bringing data home: Pendrive in, copy, pendrive out, bring home. Ofcourse I can upload that X gigabyte to Dropbox, and download it at home, but that's crazy.
The only problem is that non-Windows, non-online sync is missing.

If what you say is true, then smartphones should't work as an extension of a personal computer (be it Win, OS X or some Linux), only work as standalone devices.
What if Google comes out with an operating system? Will they say that I should still sync online and cannot do a proper local sync? Probably no. (or maybe yes, but that would be a big "you should do it our way" message).
So I would be really happy if I see an open, well documented interface to Android's internal calendar (and not just the well polished Google Calendar APIs), on which developers of client side PIM softwares can build their own sync utility (KOrganizer, Sunbird, etc.). Now I have two options: sync everything online (just because I'm on Ubuntu), or use Windows.

---

### Post by keithrennie on 2010-06-19
> **azanutta said:**
> has anyone an idea of this sync problem with android?!?
[http://ubuntuforums.org/showpost.php?p=7296106&postcount=5](http://ubuntuforums.org/showpost.php?p=7296106&postcount=5)

and i'd also like to know how to convert my videos in order to see them in the device! =) tnx

zamzar is a great video conversion service, and has free and paid options.
Check it out. 

Conversion programs with nice GUI didnt work for me. I spent days testing them. Until I found and installed ffmpeg (install it from the software center).

You can run it in a terminal with this command line in Gentoo that works every time for me. Expect it to take a long time. I'm sure there's a more elegant user friendly solution but I just didnt find it yet. Make sure you have all the codecs installed, get Medibuntu as a repository if necessary.  Also be aware it is NOT fast, but you can watch its progress in the terminal.
In the terminal, make sure your input file is visible in the directory you are using, then enter the following command:

ffmpeg -i [source_filename] -vcodec mpeg4 -sameq -acodec libfaac -r 25 -ac 1 -ar 16000 -ab 32000 [outputfilename]

Note that the -r25 parameter must be stated, although the ffmpeg manual states that it is default.

---

### Post by Paqman on 2010-06-19
> **karatedog said:**
> 
What if Google comes out with an operating system? Will they say that I should still sync online and cannot do a proper local sync? Probably no. (or maybe yes, but that would be a big "you should do it our way" message).

Definitely yes. Google's Chrome OS is an operating system for netbooks, and comes out later this year (probably).

It uses only web services. No local apps or devices. Even printing is done through the web.

---

### Post by karatedog on 2010-09-02
> **Paqman said:**
> Definitely yes. Google's Chrome OS is an operating system for netbooks, and comes out later this year (probably).

It uses only web services. No local apps or devices. Even printing is done through the web.

Ops, I forgot to subscribe to this thread :D

if Chrome OS won't allow local data management (which would be very strange as the OS has Linux roots) it will be an ultimate fail. Just go and see why even Apple fanbois began to jailbreak their phones. They liked the phone very much but hated its limit. And not a 'certain' limit, but the concept of 'limits' itself.

---

### Post by Mr. Picklesworth on 2010-09-02
> **Kosimo said:**
> How compatible is an Android based phone with Ubuntu? In terms of, managing it, update the software, install apps, etc etc.

I guess that when you buy an android phone it comes (probably) with a CD which has a bunch of software to install in a Windows or MAC environment.   How about Ubuntu? Do we have the same support?


If there is any Android owner around here, please give us your impression!

Thanks

Unlike i(phone)OS, Android is self-supporting. To put stuff on your phone you dump it in an external SD card from your computer, or you can just download it on the phone in the first place. When you plug the phone in via a USB cable, it can helpfully present that device to your big computer. Ubuntu does know what it is, but that's really just icing.

You can really put media files wherever you want on that SD card; it uses a rather nice system to index all of them seamlessly. (Only &#8220;rather nice&#8221; because it's a major pain if you have two things that happen to involve audio files but have nothing to do with each other).
You really don't need to think about filesystems at all unless you're doing something fancy.

Meanwhile, the development tools use Eclipse and have detailed instructions for Linux.

That is not to say there aren't some awesome things to integrate your big computer and your Android device. I'm in love with this one:
[https://chrome.google.com/extensions/detail/oadboiipflhobonjjffjbfekfjcgkhco](https://chrome.google.com/extensions/detail/oadboiipflhobonjjffjbfekfjcgkhco)
For just about everything, stock Android syncs your data with online services like Google Calendar and Google Contacts, so if you use that on your computer the two will fit together snugly.

---

### Post by whiskeylover on 2010-09-02
> **typos1 said:**
> No, no, no, people buy Android phones because they want a smartphone (ie a camera, a pda, a media player, a phone, a storage device, a browser, a gps device etc, etc) not cos they want to use Google's services. I ve had smartphones for years and I ve never brought one to use Google's services. I may have used Google's services on it sometimes, but I never brought a phone specifically to use Google. I very much doubt anyone ever has. Been a member of many online smartphone forums and no one has ever said they want a smartphone just for Google.

If you want a car analogy then it would be like buying a car and being forced to drive somewhere ONLY via a particular route, even when there are other more convenient routes.

Any other phone operating system allows you to simply check your diary, which is on the phone. If you want you can sync it via cable, or via the internet. 

Android-you have to use the internet and register with Google first. 

And what if you want to put a date in your calender? You have to go online to do it so then the device can go online to update it!! Why cant you just put the date on the calender on your phone!!?? Madness.

Firstly if there is no service then you cant check an up to date copy of your diary.

Secondly, why cant I have the same 3 choices as WinMo, Symbian, RIM or the iphone?

I use Ubuntu cos its open source and not tied to any one company. Android is tied to Google, I am a member of loads of smartphone forums and I ve heard a lot about Android, most good and I was so looking forward to getting it, but its the biggest disappointment ever. Never thought I d rate a Microsoft product over a Linux based one, but for mob devices I do, despite WinMo's faults.

There is so much you cannot do with Android that you can do with WinMo.

You HAVE to put all your contacts on the phone, you cant read them from the SIM, unlike every other phone I ever had (including non smartphones)

Their is no task manager.

You cant sync properly abnd access the filesystem

You cannot PIN lock the device.

There is no phone keypad for one handed use.

It takes ages to boot, just as long as WinMo.

Not enough space to list all the settings you simply cant tweak, but that you can with WinMo (with WinMo you can tweak almost anything, like you can a pc)

This can't be farther from the truth. You can sync your phone with your google account. The keyword here is "sync". It means, you can pull information from the internet into your phone and vice versa. It does NOT mean you have to have an active internet connection, or even a Google account to use your phone.

---

### Post by AlphaMack on 2010-09-02
> **typos1 said:**
> 
You HAVE to put all your contacts on the phone, you cant read them from the SIM, unlike every other phone I ever had (including non smartphones)


I don't seem to have a problem importing VCFs from my SD card.  So you need an extra step to export...to VCF.

> 
Their is no task manager.


Don't need one.

> 
You cant sync properly abnd access the filesystem


Access the filesystem?  ASTRO File Manager can do that.  Root and you have full access.

"Sync properly?"  Subjective.

> 
You cannot PIN lock the device.


On Froyo you can.

> 
There is no phone keypad for one handed use.


If you buy a Droid (Milestone) or Droid 2 you can.

> 
It takes ages to boot, just as long as WinMo.


Subjective.

> 
Not enough space to list all the settings you simply cant tweak, but that you can with WinMo (with WinMo you can tweak almost anything, like you can a pc)

If you try a custom ROM I'm sure you will change your tune about that.  Even with stock you can swap out the default launcher with one of your choice (e.g. ADW or LauncherPro...each with their own custom settings).  Don't like the default mail client?  Get another one (e.g. K-9 Mail).  Don't like the default browser?  You have choices there too (e.g. Opera, Dolphin).

I run Cyanogenmod 6 with P3Droid's 1.0 GHz low-voltage kernel on my Droid and it screams.  Rooted by choice.

Don't even need Google if you don't want it...

Please, try to actually use Android before posting FUD on here about it.

---

### Post by Mr. Picklesworth on 2010-09-02
> **AlphaMack said:**
> Access the filesystem?  ASTRO File Manager can do that.  Root and you have full access.

And if you're like me and you want a tastefully designed file manager that does its job, and only its job, well, [Ghost Commander]("http://www.appbrain.com/app/com.ghostsq.commander") is excellent :)
(It looks especially beautiful, in my opinion, on an OLED screen with the file icons turned off).

typos1, how long a smartphone OS takes to boot is completely irrelevant because it should never need to be (and in practice almost never is) rebooted. The hardware these things run on scales beautifully like that.
If you experience the boot screen on a regular basis, you're using it wrong.

As for task managers, same deal. If you use one regularly, you're doing it wrong. If you actually legitimately need to use it regularly, you have installed some horrific software on your phone; you should promptly remove it and give it the lowest rating you can on the Android Market.
Programs close on their own, and in the event they don't the system will kill them in short order. It just has some unique ways of handling and displaying them. (Remember, this uses a managed runtime so it's quite different from what we're used to).

If you have one of those things installed that actively kills background processes, you're just going to break stuff and waste battery life as those background processes desperately fight for life and restart themselves from scratch.

---

### Post by karatedog on 2010-09-03
> **whiskeylover said:**
> This can't be farther from the truth. You can sync your phone with your google account. The keyword here is "sync". It means, you can pull information from the internet into your phone and vice versa. It does NOT mean you have to have an active internet connection, or even a Google account to use your phone.

Google doesn't ease the pain converting to be an all life Googler. Before HTC Hero I had a Nokia, which perfectly synced to Outlook and its own desktop app. Then I bought the HTC Hero, its sync worked so-so on XP. 
However all of my contacts were synced by HTC Sync to the phone as the sync software decided it, therefore none of my contacts are Google contacts, and it is not possible to change a contact's type in the phone after it is created (huhh?). 
Therefore I cannot sync any of my contact to Google, unless I manually re-add them to the contact list (maybe a 3rd party app? Look like everything has to be solved by 3rd party apps...).
I just wonder if there is anyone at Google who thought about user experience coming from non-Android world, and - being a nice company - going back to the non-Android world. The user owns the data, this is clear when you have a WinMo, a Nokia or an iPhone. When using Android, having your data at your own computer seems discouraged.

---

### Post by whiskeylover on 2010-09-03
> **karatedog said:**
> Google doesn't ease the pain converting to be an all life Googler. Before HTC Hero I had a Nokia, which perfectly synced to Outlook and its own desktop app. Then I bought the HTC Hero, its sync worked so-so on XP. 
However all of my contacts were synced by HTC Sync to the phone as the sync software decided it, therefore none of my contacts are Google contacts, and it is not possible to change a contact's type in the phone after it is created (huhh?). 
Therefore I cannot sync any of my contact to Google, unless I manually re-add them to the contact list (maybe a 3rd party app? Look like everything has to be solved by 3rd party apps...).
I just wonder if there is anyone at Google who thought about user experience coming from non-Android world, and - being a nice company - going back to the non-Android world. The user owns the data, this is clear when you have a WinMo, a Nokia or an iPhone. When using Android, having your data at your own computer seems discouraged.


If you're talking about merging two or more contacts into a single contact (in your case, a google contact) then no, you need a third party app to do so. But what you can do currently with the stock Contact App is link multiple contacts from different sources (like Facebook, Twitter, Exchange etc) together; which is the right way to do it in the first place.

Also, merging contacts is not possible using the stock apps in WinMo either. You have to use third party apps for that too. 

And your contacts/calendar entries on your device stay on your device. They don't automatically sync to Google's servers (unless they're google contacts/calendar entries). I don't understand how you think this is wrong.

---

### Post by karatedog on 2010-09-03
> **whiskeylover said:**
> If you're talking about merging two or more contacts into a single contact (in your case, a google contact) then no, you need a third party app to do so. But what you can do currently with the stock Contact App is link multiple contacts from different sources (like Facebook, Twitter, Exchange etc) together; which is the right way to do it in the first place.
Linking contacts - in my oppinion - is a hack, offered for lazy people who stored different phone numbers for the same contact in different entries, or for people who kept contacts on SIM. It is also useless because I see 100 contacts on the phone in People list, which turns out to be 500 contacts when I sync them (nowhere are shown that a contact is linked to any amount of other contacts, you have to edit contacts one-by-one to check this)

> Also, merging contacts is not possible using the stock apps in WinMo either. You have to use third party apps for that too.
That is true however if you used WinMo (and Outlook), it is very, very easy to edit your contacts on a PC, and sync back the results. when I had a WinMo device, I had a 3rd party app that made a backup of everything to the SD card, and also offered a desktop app for editing that backup file and even editing contacts in the phone (it was free, can't remember the name) that way I could ditch Outlook entirely.

> And your contacts/calendar entries on your device stay on your device. They don't automatically sync to Google's servers (unless they're google contacts/calendar entries). I don't understand how you think this is wrong.
They don't, however if I want a full backup of my data (I mean everything from SMS, MMS to contacts and calendar), either I use the online way, which I can't really use as all of my contacts are not Google type contacts, or I use the offline way which is currently a huge failure (ok, HTC Sync v3.0 is trying, and I remember when Nokia's PC Suite was a complete failure, but in 3-5 years it was polished to a fairly usable state. So I give 1 or 2 years to HTC Sync to mature, if there is a 3rd way to back up data to the SD card, I would welcome it).

What I say is that Google devices are not ready for converting users (coming from WinMo or Nokia), to a click-click-click-finish style of syncing, backup, added that those users might not like online syncing just for the sake of online syncing (without any other benefit). When I use Dropbox I use it because I want to access my data from different devices. If I used Dropbox only on one device, would people call me stupid?

---

### Post by 3rdalbum on 2010-09-03
Nobody has really answered the earlier poster's "audio/video sync issues" post.

I was having the problem on my Desire, until HTC pushed out the update to Android 2.2. Now it all works fine. It's a known problem but for most people the update fixes it.

---

### Post by typos1 on 2010-09-03
Whiskeylover if you dont have or dont want a Google account you cant do anything, you cant even check your calender cos it has to go online to do it! Thats madnes, I want my data on my phone, dont mind having the choice of phone or cloud based, but dont wanna be forced to be cloud based and if theres no signal you cant use it! I m fully aware what sync means and other smartphones can sync via the internet or cable. Quite how you can say you dont need an active internet connection to sync, when you can ONLY sync using the internet is beyond me. And sync does not mean you can pull info from the internet it means you can syncronise 2 devices or the info on them, how you actually do it is not in the definition of the word. 

Mr Picklesworth-You cant access the file system with Android only the SD card and you cant adjust many setting in Android either, no where near as many as Windows Mobile, other phone OSs or any normal pc/laptop with any OS.

To exchange data between your computer and Android you HAVE to use GPRS/3G you cant just plug it in, this is very very stupid-what happens if theres no signal or you dont have a data plan? You either can do it or it ll cost you everytime!

I will turn off/reboot my smartphone as much as I like-it has an off button and iots there to be used! I dont generally turn it off anyway, but I will do as much as I like and because the button exists I am not "using it wrong"

As for task managers-I am not using my phone wrong-I ve had Windows Mob phones for 7 years and sometimes progs run in the back ground and I want to shut em down-I have very few app,s call it a WinMo design fault, but even with ubuntu sometimes I need to go into system monitor and kill processes/apps. You dont have much control with Android. If youre new to smartphone and Android is all you ve experienced it may seem great compared to a non smartphone, but I prefer WM currently-its far far from perfect but you get more control.

Google brought a project that was developing Linux for mobile phones and then turned it into an iphone copy/rival, making it operate similarly (and not like a normal computer or smartphone). Its a moneymaking/fashion thing-bit like touch screens-great for a laptop or pc, but gimicky rubbish for a phone or smartphone, very clever but is less intuitive and slower than a numeric keypad for entering data, but like sheep everyone has one cos everyone else has one. They saved a pile of cash cos Linux is open source and they didnt have too develop their own code. 

I want to do what I want with my smartphone, just like with my pc. Someone said Google was a "nice" company-there were once, but not anymore, like Apple theyve turned into a "nasty" arrogant, greedy company, just like Microsoft and Apple.

I kept my Android phone for 3 days and sold it (any longer and I would have thrown it at the wall!). Sticking with Winmo6.1 for the moment, til I can get proper Linux

Totally agree with most of Karatedog's posts.

What I waiting for is ubuntu smartphone edition.

---

### Post by karatedog on 2010-09-03
Although I'm ranting against online syncing, what you wrote is not entirely true.
> **typos1 said:**
> Whiskeylover if you dont have or dont want a Google account you cant do anything, you cant even check your calender cos it has to go online to do it!
If it is an online calender then of course you have to go online to check it. Outlook synced calendars don't need the phone to be online

> Mr Picklesworth-You cant access the file system with Android only the SD card and you cant adjust many setting in Android either, no where near as many as Windows Mobile, other phone OSs or any normal pc/laptop with any OS. 
You can access it, but not from the outside. Use some phone installed file manager.

>  To exchange data between your computer and Android you HAVE to use GPRS/3G you cant just plug it in, this is very very stupid-what happens if theres no signal or you dont have a data plan? You either can do it or it ll cost you everytime!  
Nope, that is not true. I don't know what you tried, but you get an USB cable along with your phone. Put it in, and set the phone to USB connection. That's when the internal memory is unavailable, but the SD card is available.
Well putting something into internal memory is a tedious task, first putting in on SD, then internally moving it.

> As for task managers-I am not using my phone wrong-I ve had Windows Mob phones for 7 years and sometimes progs run in the back ground and I want to shut em down-I have very few app,s call it a WinMo design fault, but even with ubuntu sometimes I need to go into system monitor and kill processes/apps. You dont have much control with Android. If youre new to smartphone and Android is all you ve experienced it may seem great compared to a non smartphone, but I prefer WM currently-its far far from perfect but you get more control.
Don't extrapolate from a 7 year old experience. When I used Android 1.5 (HTC Hero), a Task manager was badly needed. However after upgrading to Android 2.1, not more than 5-7 tasks are running when I start the Task manager. Something evolved. (not everything, Android still don't naturally supports other language than English, for accented chars. That push-to-reveal-then-select technique is way too complicated, and in Europe only English people don't have some gibberish characters in their language, every other nation has.)

> What I waiting for is ubuntu smartphone edition.
Me as well :p but I suspect that Ubuntu is a bit heavyweight in this area. We should take a look at Bada and WinMo7 first.

---

### Post by wewantutopia on 2010-09-03
Can an Android device be added to my Samba network so it is moutable from my computers and the computers moutable on it?

---

### Post by whiskeylover on 2010-09-03
> **typos1 said:**
> Whiskeylover if you dont have or dont want a Google account you cant do anything, you cant even check your calender cos it has to go online to do it! Thats madnes, I want my data on my phone, dont mind having the choice of phone or cloud based, but dont wanna be forced to be cloud based and if theres no signal you cant use it! I m fully aware what sync means and other smartphones can sync via the internet or cable. Quite how you can say you dont need an active internet connection to sync, when you can ONLY sync using the internet is beyond me. And sync does not mean you can pull info from the internet it means you can syncronise 2 devices or the info on them, how you actually do it is not in the definition of the word. 


As I said previously, you have no clue what you're talking about. You  have an option to sync your data to online services, and you ALSO have  an option to have the data on your phone only. I know what sync is, as  you cleverly tried to explain it to me. You also do NOT realize that  once you sync two devices, you don't need to have a network connection  between them. They can operate independently. That's exactly what  Android does (very similar to how WinMo does.) Android syncs your google  calendar (ONLY if you chose so) and then you can just work off your  device. Or, you can have a device only calendar without a Google  account. Just like how WinMo syncs its calendar with Outlook. Infact,  you can have a fully functioning Android device without even having a  Google account. Please use an Android device before trying to spread  FUD. 



> **typos1 said:**
>  Mr Picklesworth-You cant access the file system with Android only the SD card and you cant adjust many setting in Android either, no where near as many as Windows Mobile, other phone OSs or any normal pc/laptop with any OS.

If you've ever used Android you'd know that you can tweak EVERYTHING in the Android system if you root it. WinMo systems are rooted by default, but come WinMo7, that is going to change. They're going to be equally difficult to root. So you lose the advantage there.



> **typos1 said:**
> To exchange data between your computer and Android you HAVE to use GPRS/3G you cant just plug it in, this is very very stupid-what happens if theres no signal or you dont have a data plan? You either can do it or it ll cost you everytime!

OMG! You can use Wifi!!! : O



> **typos1 said:**
>  I will turn off/reboot my smartphone as much as I like-it has an off button and iots there to be used! I dont generally turn it off anyway, but I will do as much as I like and because the button exists I am not "using it wrong"

As for task managers-I am not using my phone wrong-I ve had Windows Mob phones for 7 years and sometimes progs run in the back ground and I want to shut em down-I have very few app,s call it a WinMo design fault, but even with ubuntu sometimes I need to go into system monitor and kill processes/apps. You dont have much control with Android. If youre new to smartphone and Android is all you ve experienced it may seem great compared to a non smartphone, but I prefer WM currently-its far far from perfect but you get more control.

Just because Android currently does not come with a Task Manager does not mean that there isn't any. You can download plenty of free task managers from the market. And the beauty of Android is that you don't have to be restricted to the default stock task manager.


> **typos1 said:**
>  They saved a pile of cash cos Linux is open source and they didnt have too develop their own code. 
So what is wrong with that? You'd rather they used a proprietary system? Go brown nose Steve Jobs then.


> **typos1 said:**
>  I want to do what I want with my smartphone, just like with my pc. Someone said Google was a "nice" company-there were once, but not anymore, like Apple theyve turned into a "nasty" arrogant, greedy company, just like Microsoft and Apple.

I kept my Android phone for 3 days and sold it (any longer and I would have thrown it at the wall!). Sticking with Winmo6.1 for the moment, til I can get proper Linux

Totally agree with most of Karatedog's posts.

What I waiting for is ubuntu smartphone edition.

I've used WinMo for many years. I recently moved to Android and will never look back. And as I said earlier, come WinMo7, you'd be left with your hands down your pants when they won't let you tweak anything like they did till 6.1.

---

### Post by Calash on 2010-09-03
Some of what is being argued varies a bit depending on the device.  However you do not "need" a Google account to use Android.  If you did devices like the Nook would require you to have one as well.

On the phones having a Google account is encouraged and even pushed to a point.  However contacts and calender information is stored local.  If you skip over adding the account when you first get or reset the device you can use most features without the account.

File system access is an interesting argument.  On Windows Mobile 6.x series it comes with a file manager and lets you do all sorts of good or evil stuff.  Neither iOs or Android have this "Out of Box" support.  Oddly Windows 7 will also be dropping it natively.  I tend to think it is for the better as the average users they are trying to attract with these devices would cause more harm by poking around in the OS structure.

On task managers, Android does have a basic one built-in.  Actually there are a couple.  Holding the Home key opens up recent applications and lets you access the ones that are still running.  In Settings you can browse active services and turn them off.  Mind you this is not the level of control you get with a 3rd party one, but Windows Mobile does not have that by default in any version.  There is also the argument that task killers cause much more harm to the OS on Android.  Personally I have never used one and have yet to run into stuck processes or memory leaks.

Data exchange has been covered but to recap you can use 3G, Wi-Fi, or USB.  USB limits you to the safe parts of the OS, IE the SD card.  If you are more technical you can use the Android Developer Bridge (ADB) to manage data on your device.  To be fair I have not yet found a way to manage contacts and calender via USB.  I think the reason is that the demand for it is so small that no developers have tried to make an app yet.

Boot time is relative and has to do with the amount of media you have on your SD card.  There is an app that will disable the boot media scan and get you a faster bootup.  Personally my phone boots in the same time as my Touch Pro did.

---

### Post by AlphaMack on 2010-09-04
> **typos1 said:**
> Whiskeylover if you dont have or dont want a Google account you cant do anything

Pure bovine excrement.  AOSP ROMs like Cyanogenmod are proof positive that you don't need the "Google experience."  And what about the new Samsung phone coming out...with Bing instead of Google?

The fact that you conveniently gloss over my previous post pointing out that you don't need Google if you don't want them means that you're either seriously misinformed or here to troll.

> 
You cant access the file system with Android only the SD card


Again, download ASTRO or any other file manager of your choosing and go look around.  Unless you root, you have read-only access outside of /sdcard.

> 
and you cant adjust many setting in Android either, no where near as many as Windows Mobile, other phone OSs or any normal pc/laptop with any OS.


FUD.  Clearly you have not used another launcher nor have bothered to research into custom ROMs.

> 
To exchange data between your computer and Android you HAVE to use GPRS/3G you cant just plug it in, this is very very stupid-what happens if theres no signal or you dont have a data plan? You either can do it or it ll cost you everytime!


Uhm...Wi-Fi?

> 
I will turn off/reboot my smartphone as much as I like-it has an off button and iots there to be used! I dont generally turn it off anyway, but I will do as much as I like and because the button exists I am not "using it wrong"


Hate to break it to you...but you're using it wrong.

> 
As for task managers-I am not using my phone wrong-I ve had Windows Mob phones for 7 years and sometimes progs run in the back ground and I want to shut em down-I have very few app,s call it a WinMo design fault, but even with ubuntu sometimes I need to go into system monitor and kill processes/apps.


[http://androidforums.com/android-lounge/139105-why-you-dont-need-task-manager-android.html](http://androidforums.com/android-lounge/139105-why-you-dont-need-task-manager-android.html)

> 
You dont have much control with Android.


So, you're basically living in a walled garden dictated by a single company who decides what apps you can run on your phone?  Got it.

> 
If youre new to smartphone and Android is all you ve experienced it may seem great compared to a non smartphone, but I prefer WM currently-its far far from perfect but you get more control.

Oh, so this all about preference?  It would be nice if you actually *used* Android.  Judging from your posts, however, you clearly haven't.

> 
Google brought a project that was developing Linux for mobile phones and then turned it into an iphone copy/rival, making it operate similarly (and not like a normal computer or smartphone).


Please, do tell.

> 
Its a moneymaking/fashion thing-bit like touch screens-great for a laptop or pc, but gimicky rubbish for a phone or smartphone, very clever but is less intuitive and slower than a numeric keypad for entering data

You do know that you can get an Android device with physical keypads, right?

> 
but like sheep everyone has one cos everyone else has one.

Baaaa.

> 
I want to do what I want with my smartphone, just like with my pc. Someone said Google was a "nice" company-there were once, but not anymore, like Apple theyve turned into a "nasty" arrogant, greedy company, just like Microsoft and Apple.

Because you don't know how to use an Android phone properly?

> 
I kept my Android phone for 3 days and sold it


And there you have it.  You've already made up your mind about Android, Google, and Android users based on three days of trying to make Android work like WinMo.

Where have I heard this before?  Oh yeah, "After 2 days Linux SUX I'm going back to Windows!!11"

:popcorn:

---

### Post by ruffieux on 2010-09-14
> **KhaaL said:**
> on the grey bar at the top, drag it down and click on the "USB connected" line. there you can choose to mount it and from there you can transfer files freely :)

Hi,
I recently bought a Samsung Galaxy phone and tried to connect it (mount) to my Ubuntu 10.04 box. 
I see this grey bar saying "USB connected". However, when "click" on it nothing happen's. 
I can see the device with lsusb and I see it in dmesg.
How does the Samsung Kies USB communication program play's into this?

Any experience with this?

Thanks a lot for your feedback.

Heinz

---

### Post by whiskeylover on 2010-09-14
> **ruffieux said:**
> Hi,
I recently bought a Samsung Galaxy phone and tried to connect it (mount) to my Ubuntu 10.04 box. 
I see this grey bar saying "USB connected". However, when "click" on it nothing happen's. 
I can see the device with lsusb and I see it in dmesg.
How does the Samsung Kies USB communication program play's into this?

Any experience with this?

Thanks a lot for your feedback.

Heinz

In the settings under Applications, change the USB Settings to "Ask on connection". Then when you connect the USB cable, select  "Mass Storage", and not "Samsung Keis". 

Samsung Kies is used for working with their Keis desktop application.

Then go to the Android bar on top, and click on "USB connected", then Mount.

---

### Post by aysiu on 2010-09-14
> **ruffieux said:**
> Hi,
I recently bought a Samsung Galaxy phone and tried to connect it (mount) to my Ubuntu 10.04 box. 
I see this grey bar saying "USB connected". However, when "click" on it nothing happen's. 
I can see the device with lsusb and I see it in dmesg.
How does the Samsung Kies USB communication program play's into this?

Any experience with this?

Thanks a lot for your feedback.

Heinz
You don't click on it. You drag it down with your finger.

Put your finger on the bar. Hold it down. While pressing, move your finger in the downward direction. Then click on it.

---

### Post by typos1 on 2010-09-14
> **whiskeylover said:**
> As I said previously, you have no clue what you're talking about. You have an option to sync your data to online services, and you ALSO have an option to have the data on your phone only. I know what sync is, as you cleverly tried to explain it to me. You also do NOT realize that once you sync two devices, you don't need to have a network connection between them. They can operate independently. That's exactly what Android does (very similar to how WinMo does.) Android syncs your google calendar (ONLY if you chose so) and then you can just work off your device. Or, you can have a device only calendar without a Google account. Just like how WinMo syncs its calendar with Outlook. Infact, you can have a fully functioning Android device without even having a Google account. Please use an Android device before trying to spread FUD.


Right-I had an Andoid device for 4 days and I hated it-if you d had read my posts correctly you would have assertained that, so I m not "trying to spread FUD". With Winmo I dont actually "sync" anything I uncheck most boxes-but "sync" is also the expression they use to connect the device to you pc so you can access one from the other and move stuff across. Couldnt do that on Android (and CANT access the file system either) the only thing you can do is sync (ie copy) data using the internet, cant understand why you cant simply plug it into your pc like you can winmo and sync or exchange data and access the filesystem. I dont have, want or need wifi, but again you miss the point-you cannot plug Android into your pc, only access the sd card-want to exchange data?Yyou re forced to use internet=ridiculous if you are sat next to your pc and you want to exchange data-youre sending this data 1000s of miles when your pc is sat next to you!. And if "Infact, you can have a fully functioning Android device without even having a Google account." then how come whatever I did I could not access my calender without getting a Google login prompt? "Please use an Android device before trying to spread FUD." Please read other member's posts properly before going off on one and getting rude and abusive.


> **whiskeylover said:**
> If you've ever used Android you'd know that you can tweak EVERYTHING in the Android system if you root it. WinMo systems are rooted by default, but come WinMo7, that is going to change. They're going to be equally difficult to root. So you lose the advantage there.

As I said I HAVE used Android-I couldnt tweak anything and got no prompts for a password to login as root. This might explain why I got so frustrated with it, but without any prompts I did not know I could login as root and change things. 


> **whiskeylover said:**
> OMG! You can use Wifi!!! : O

OMG he hasnt bohtered reading my post again!-I dont have wifi at homke, I dont need it, I dont want it (its very slow compared to a wired connection) and why should I have it if the pc is sat next to me? I just want to plug it in. Point missed again-I dont want to be forced to use the internet when it is not necessary! It isnt necessary when I m at home and I want to excahnge files between pc and phone-its like using a sledgehammer to crack a nut.




> **whiskeylover said:**
> Just because Android currently does not come with a Task Manager does not mean that there isn't any. You can download plenty of free task managers from the market. And the beauty of Android is that you don't have to be restricted to the default stock task manager.

Fair point, Winmo didnt come with one at one point and I added one. Cant understand your " And the beauty of Android is that you don't have to be restricted to the default stock task manager." comment as "the beauty of" any mobile phone operating system "is that you don't have to be restricted to the default stock task manager"-this applies to Winmo as well (OMG has actually USED Winmo?! : O) and pretty much any app you want-there are 100s of 1000s of apps for ALL mobile phone operating systems (OMG where has he been for the last 10 years?!)



> **whiskeylover said:**
> So what is wrong with that? You'd rather they used a proprietary system? Go brown nose Steve Jobs then.

They have used and modded a "proprietary system"-its called Linux and they modded it to produce an iphone like, iphone rival on the cheap.




> **whiskeylover said:**
> I've used WinMo for many years. I recently moved to Android and will never look back. And as I said earlier, come WinMo7, you'd be left with your hands down your pants when they won't let you tweak anything like they did till 6.1.


Again if you d read my posts you d realise that I decided to keep my current Winmo phone and I sold my Android one, therefore what they do to winmo 7 is irellevant. As I ve said I ve used Winmo for 7 years and I prefer it to Android-we ARE allowed different opinions you know! It may well be that I would have a different impression of Android had I rooted it and I m perfectly prepared to have another look at it at some point. I d be much more inclined to do so without aggressive posts though.

It might be a good idea if you read people's posts properly before posting and if you pleasantly suggested that I might have got the wrong impression cos I didnt root it, rather than post rude, obnoxious, abusive comments that make you look a bit childish. That way we can have an adult discussion!


> **Calash said:**
> Some of what is being argued varies a bit  depending on the device.  However you do not "need" a Google account to  use Android.  If you did devices like the Nook would require you to have  one as well.

On the phones having a Google account is encouraged and even pushed to a  point.  However contacts and calender information is stored local.  If  you skip over adding the account when you first get or reset the device  you can use most features without the account.

File system access is an interesting argument.  On Windows Mobile 6.x  series it comes with a file manager and lets you do all sorts of good or  evil stuff.  Neither iOs or Android have this "Out of Box" support.   Oddly Windows 7 will also be dropping it natively.  I tend to think it  is for the better as the average users they are trying to attract with  these devices would cause more harm by poking around in the OS  structure.

On task managers, Android does have a basic one built-in.  Actually  there are a couple.  Holding the Home key opens up recent applications  and lets you access the ones that are still running.  In Settings you  can browse active services and turn them off.  Mind you this is not the  level of control you get with a 3rd party one, but Windows Mobile does  not have that by default in any version.  There is also the argument  that task killers cause much more harm to the OS on Android.  Personally  I have never used one and have yet to run into stuck processes or  memory leaks.

Data exchange has been covered but to recap you can use 3G, Wi-Fi, or  USB.  USB limits you to the safe parts of the OS, IE the SD card.  If  you are more technical you can use the Android Developer Bridge (ADB) to  manage data on your device.  To be fair I have not yet found a way to  manage contacts and calender via USB.  I think the reason is that the  demand for it is so small that no developers have tried to make an app  yet.

Boot time is relative and has to do with the amount of media you have on  your SD card.  There is an app that will disable the boot media scan  and get you a faster bootup.  Personally my phone boots in the same time  as my Touch Pro did.

I could not find any way of getting into calender without giving my login details for Google. Maybe I missed something but I tried loads.

I just couldnt understand why out of the box I couldnt plug it into the pc and I still can see why it cant do it, or the "not much demand" arguement. I mean  Winmo data exchanges with the pc with no restriction it seems logical to me that any small computer (thats what an Andoird/Winmo device is) attached to a another computer via usb would be able to exchange ANY data-it looks like certain types of data exchange have been engineered out ie they specifically DIDNT allow it to do it which is weird, why restrict some things?? And surely it would have taken more time to stop it syncing certain data as opposed to syncing everything.

The SonyEricsson Experia X10 I tried was awful and maybe certain things are device specific. The touch screen was capacitive and I was expecting an improvement over my old resistive Omnia but it was just as bad response wise so that coupled with not being able to do even the most basic thing with the OS was very frustrating, hence selling it. Ideally I d have a device with a phone keypad and no touchscreen-its useless gimick for a phone (great for other stuff-tablets, laptops, pcs, screens in cars etc) but rubbish for small device-it takes longer to move your fungers over the screen than it does to move your thumb on a keypad and qwerty this small is just plain silly it stops it being a one handed device, its much more practical for small devices to be one handed.

I d be interested to experience a rooted Android device, but I d still prefer Ubuntu developed for mobile devices, without any huge great multinational company behind things, so I could simply install it on any mobile device like I can Ubuntu on my pc.

Thanks though Calash for having a more mature and friendly attitude in your posts than some others on here!

> **AlphaMack said:**
> Pure bovine excrement. AOSP ROMs like Cyanogenmod are proof positive that you don't need the "Google experience." And what about the new Samsung phone coming out...with Bing instead of Google?

The fact that you conveniently gloss over my previous post pointing out that you don't need Google if you don't want them means that you're either seriously misinformed or here to troll.

Right so you have to install a cooked ROM to get Andoid without the "Google Experience", that kinda proves my point-others agree so someone developed a ROM to get round it! The phone with Bing is a new development, not even out yet. If you read my previous post you d have seen that I got rid after 3 or 4 days cos I hated it so much. What I had taken for granted for years from Winmo wasnt available and whatever I did I couldnt get into my calender just to check the date without having a Google login prompt. Your earlier post was months after I sold it, if youd read my earlier posts you d have got that. No "trollin" just expressin my opinions.

> **AlphaMack said:**
> Again, download ASTRO or any other file manager of your choosing and go look around. Unless you root, you have read-only access outside of /sdcard.

Ok, but why cant I do it out of the box? Why go to the trouble of developing it so you CANT?! Its stupid.



> **AlphaMack said:**
> FUD. Clearly you have not used another launcher nor have bothered to research into custom ROMs.

Quite right-did you read my earlier posts?! If it doesnt impress I m hardly likely think "I really hate most things about it, but I ll just see if I can mess about with it and stick on a custom ROM, maybe it ll turn into an amazing system if I do. And its hardly an "amazing OS" if you HAVE to flash it with cooked ROMs to make it so. 



> **AlphaMack said:**
> Uhm...Wi-Fi?

Um, read my earlier post? I dont have wifi and dont need it, but even if I did why would I want to use the internet to get a picture off my pc when its just sat there and I could jsut plug it in and get it from it lke that???? Its far quicker and easier. Wifi to do it is good if I m not at home, but sending the picture down 1,000s of miles of wires when the machine I want to put it on is a metre away is really very silly.



> **AlphaMack said:**
> Hate to break it to you...but you're using it wrong.


Cool, so I ve been using the on/off button to turn my pdas on and off for the last 7 years (on the rare occassions I do turn it off) and thats wrong? Of course, silly me-I should be using the cameraa button to do that, or maybe the dial button, or they back button? Hmm



> **AlphaMack said:**
> So, you're basically living in a walled garden dictated by a single company who decides what apps you can run on your phone? Got it.

I say that you dont have much control with Android and you say the above, I never mentioned apps and was clearly talking about things like not being able to access the filesytem and other stuff covered above, quite how you can think that I m "living in a walled garden dictated by a single company who decides what apps you can run on your phone" cos I dont like not being able to access the filesystem I dont know.


> **AlphaMack said:**
> Oh, so this all about preference? It would be nice if you actually used Android. Judging from your posts, however, you clearly haven't.

Again I m left wondering if you even bothered to read my posts at all. I ve said countless times I HAVE used Android. 



> **AlphaMack said:**
> You do know that you can get an Android device with physical keypads, right?

Yep, but there are very few and most of them are qwerty keypads (not phone keypads like the old Winmo smartphone edition) and a lot of them are low spec versions. Although if you had actually read my posts you would see that all this happened months ago and things might have improved since



> **AlphaMack said:**
> Because you don't know how to use an Android phone properly?

No, because it is getting increasingly "nasty" arrogant, greedy company, just like Microsoft and Apple. And I didnt like Android when I used it-sorry but theres no law saying you HAVE to like Android.



> **AlphaMack said:**
> And there you have it. You've already made up your mind about Android, Google, and Android users based on three days of trying to make Android work like WinMo.

Where have I heard this before? Oh yeah, "After 2 days Linux SUX I'm going back to Windows!!11"

Ok, you may have a point there-I could have tried it for longer, but I really didnt get on with it. And even if it can do some of the things I thought it couldnt it would appear you have to seriously mod it, like reflash it with a cooked ROM for instance or stick on a different launcher (ok that last one isnt a serious mod but you get my point). Why doesnt it have a decent launcher out of the box? You have to tweak Winmo a fair bit, but at least it runs ok out of the box. Moving to Ubuntu from Windows was easy and pretty smooth, no real probs, moving to Android from Winmo was hell. Sorry if thats different from your experience but we re not all the same. 

Think I ve mis judged Android and I should give it another go? Great, politely show me the error of my ways, nicely suggest I ve missed something, kindly point out with a different ROM its a dream and I ll love it as much as Ubuntu. Fair enough. Start being rude, aggressive, sarcastic and abusive as you and Whiskeylover have and you may as well just not bother posting-its hardkly in the spirit of "humanity towards others" is it?-go tweak your phone or something instead!

---

### Post by SomeGuyDude on 2010-09-14
I'll say this.

I can't read the internal storage on my rooted Inc under Arch, but that's not a huge deal.

---

### Post by ruffieux on 2010-09-14
> **aysiu said:**
> You don't click on it. You drag it down with your finger.

Put your finger on the bar. Hold it down. While pressing, move your finger in the downward direction. Then click on it.

Thanks aysiu for your hint, I was not aware of it. 
However....even when I hold it down (it changes the color) and then try to slide it downwards, nothing happens....
Am i stupid or is there something else wrong? I did not install any SW on the linux box. Do I need to install anything?

Thanks

Heinz

---

### Post by AllRadioisDead on 2010-09-14
> **SomeGuyDude said:**
> I'll say this.

I can't read the internal storage on my rooted Inc under Arch, but that's not a huge deal.
You're not supposed to be able to access the internal storage of the phone.
If for whatever reason you need that access, root and download rootexplorer.

---

### Post by ruffieux on 2010-09-14
> **aysiu said:**
> You don't click on it. You drag it down with your finger.

Put your finger on the bar. Hold it down. While pressing, move your finger in the downward direction. Then click on it.

Got it!

However this only works if you set your phone into "USB debugging" mode under Settings>Applications>Development

Found it in this threat:
[http://ubuntuforums.org/showthread.php?t=1557917&highlight=android+mount](http://ubuntuforums.org/showthread.php?t=1557917&highlight=android+mount)

---

### Post by 3rdalbum on 2010-09-14
> **AllRadioisDead said:**
> You're not supposed to be able to access the internal storage of the phone.
If for whatever reason you need that access, root and download rootexplorer.

If you just want to read, then install Astro on the phone, no root required.

---

### Post by aysiu on 2010-09-14
> **ruffieux said:**
> Got it!

However this only works if you set your phone into "USB debugging" mode under Settings>Applications>Development

Found it in this threat:
[http://ubuntuforums.org/showthread.php?t=1557917&highlight=android+mount](http://ubuntuforums.org/showthread.php?t=1557917&highlight=android+mount)
It should work even with USB debugging turned off. See attached screenshots.

But whatever works, of course.

---

### Post by Vege 4wd on 2010-12-14
Hi I have an android phone on the way.:D

After reading quite a few threads I am not sure what to expect. Anyway some talk of rooting the phone. How do you do that. 

I will reserve comments on android until after I have used it for a while. 

Thanks all.

---

### Post by aftertaf on 2010-12-22
From what I can tell, the version of Android makes each experience differ too.

The phone companies are partially to blame, because with Froyo (2.2) you have things much easier : stability, performance, removed the need for task managers, but they still ship with 2.1 or maybe some even with 1.5.

Its like starting out today, 22nd December 2010 with a new laptop and having ubuntu 6.06 or 7.10 on it....

From a synching point of view : you dont have the type of things we are used to having with proprietary software : direct management and sync of calendar,contacts, photos, etc etc etc...

You can mount the sd card as a usb external with ubuntu and copy/paste etc that way.

For now the simplest way for PIM data sync is via the online services (google account is the most obvious for me, as i'm already on gmail.)
But maybe sometime soon there will be developers that will work on a sync tool that is fully-compatible and respectful of the way android phones store their data.

But before anyone 'judges' how android works, make sure you're trying 2.2.... some reports are 5-20 times better in performance (benchmarking tools) and in autonomy.

but i've only had my 2.2 HTC Desire HD since friday.... so... :D

---

### Post by LowSky on 2010-12-22
I used an app called Unrevoked to root my HTC Droid Incredible. It was very simple to do even on Ubuntu, I just had to run the program using sudo. I got the phone when it came out so about 9 months or so now. Some phones can be rooted with ease and allow custom or newer versions of Android to be installed, while others are completely locked down as per the manufacturer, not Google.

I have tried a few custom ROMs and found that stock HTC Sense UI to be my favorite with Cyangenmod 6.1 coming in second place.

As for data syncing Google does work very well. Their calendar and mail programs work well with Ubuntu's Evolution and instructions for setting it up are easy to find, so if you want a the notifications on your PC it works very well. No need to USB link the phone just to set calendars up.

Android 2.2 is better than previous versions in speed for most of the newer models.  Battery life also improved pretty good too. Otherwise all other aspects remain good. Remember that most other parts of the phone may be related to other applications, and with updates can change their performances. For instance Google updated their program Voice (separate phone service) a while back basically crippled it, and we waited over a month for a fix.

---

### Post by Vege 4wd on 2010-12-22
I have been using my android for a while now and find it great. 
Google sync is easy use.

I would like to have control over the programs though.

Lowsky, have you found any advantages after rooting the phone?

---

### Post by aaron76 on 2011-04-20
> **aktiwers said:**
> I have one and it works fine with my Ubuntu PC. The apps and updates for android are done on the phone, using wireless. The connection to the computer recharges the phone fine, and you can move your photos to the computer. 
You can drag music from the computer to the phone as well.

Actually Ubuntu mounts it as a phone, and then you can drop files to or from it, as android detects what is music and what is pics..

Excuse my ignorance, but does this mean I don't need to install Kies (as it's Windows anway)? Also, do you use a wireless hotspot or a wireless router at home?

---

### Post by Mike BFD on 2011-05-31
> **karatedog said:**
> ...Just go and see why even Apple fanbois began to jailbreak their phones. They liked the phone very much but hated its limit. And not a 'certain' limit, but the concept of 'limits' itself.
A little off-topic here: I've just returned from a short trip to StPeterburg, Russia. What I should say, the Russians (unlike inhabitants of Europe and Americas) are almost "unreachable" by all those "copyright protectors"...
So "jailbreaking" of iPhones there is made not by "some undercover individuals" but by pretty large companies with offices in downtown and broad advertising campaigns)))

Pretty funny to see. Another thing to be noticed, they (as they say) "nearly completely rewrote" the original Apple OS - it looks the same but has literally NO "limits". Many Finns have already brought their iPhones there (it's only 400km drive from Helsinki finally) and are happy with the results...

Wander what those guys can make with Android))))))) Maybe I should ask))))

---

