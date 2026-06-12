---
title: "Switch permanantly to Ubuntu?"
date: 2009-08-06
forum: The Cafe
---

### Post by krindik on 2009-08-06
Hi friends,
I'd really appreciate if u would give me some advice on this.
My main question is whether I should switch to Ubuntu or stay with Windows.

I'm new to ubuntu but have mixed experience with linux and windows.
I used to be a c++ developer on linux but used xp at work and now at studies. Now I don't usually develop and mostly use below

1. MATLAB - (have linux version)
2. Latex
3. Edit vector graphics
4. Wireless net
5. Skype - video/speakers/mic 
6. Word

I was wondering whether my choice should be Vista or Ubuntu. If all those above stuff works well with ubuntu without having to find audio drivers etc. I would really like switch as I'm really happy that Ubuntu uses only <200MB whereas Vista uses 1GB+ normally and I dont have to purchase a virus guard !.

The main points I would look to have are:
1. Above software should work
2. Doesn't stuck
3. 99% stuff would work out of the box

I only want a hazzle free, easy (and cheap) to use, non-sluggish desktop to continue with my work. And I'm really bored with compiling software and installing drivers in RH[7-9], FC[1-3] days. 


Btw, I have a 1545 Dell inspiron with ATI video/Intel sound recently purchased for 1200AUD.

Since the 1545 doesn't have seperate keys to mute/wifi etc. will all those work with Ubuntu?  
 
I'm sure you'll give me good advice for this long long letter !!

Thanks
krindik

---

### Post by hyperAura on 2009-08-06
well as i see it u can go ubuntu.. as far as i know above programs work in ubuntu, the only one i dont know is skype which i havent used.. as for the setup u just take a day off and fix everything to suit your needs and u r ready to go.. in ubuntu if a program gets stuck, the whole working environment does not get stuck so no problem getting stuck..

---

### Post by ddrichardson on 2009-08-06
The 1545 with ATI has some issues with graphics driver but I understand its related to performance with games.

The 1545 seems a wide ranging specification, I've the bottom of the range Intel graphics version and everything worked OOB although I had to tweak pulseaudio for louder audio.

Your application list is fine, Word runs in wine although Openoffice supports the same file formats too with the bonus of producing PDF.  I never cared for Matlab (Maple for me) but as you say its a Linux version.  There are several good LaTeX editors, I use [lyx]("http://www.lyx.org/").  Skype runs fine in Ubuntu and is available in the repositories.  Vector graphics I know nothing about.

---

### Post by the8thstar on 2009-08-06
Perhaps you should dual boot; this way you would have the shared benefits of both operating systems.

---

### Post by krindik on 2009-08-06
Thanks. In fact, I have a dual boot system. But don't really want to switch each time. Like to stay with one all the time !

Speakers are working fine but sound recording is poor. Skype is very important to me :)

I tried Lyx on windows but didn't really like it. It gives some strange error/warnings some times. I thought of using Texmaker/Kile but Texmaker has F1, F2 keys and 1545 doesnt have those keys. (Have to press Fn key and wifi. You make a mistake wifi goes..) And Kile doesnt have a windows version. Then again I'd like to stay with one...

Anyway is ntfs write working with no problems? 'Cause if I dual boot I have to share data with Vista.

I use Illustrator in Vista but was thinking of getting used to one thats available both in Linux and Vista. 

Most of all the big plus with ubuntu seems to be that it is really fast and doesnt get slow with time(does it?)

Thanks

---

### Post by barnex on 2009-08-06
Go for it! If you occasionally still need windows for whatever reason, I recommend virtualbox. It's way easier than dual boot, free and fast!

---

### Post by krindik on 2009-08-06
Ok.. :)
Is it because u r a ubuntu fanatic or ubuntu is actually a real desktop? Do u actually work with ubuntu without any trouble... 
I'd definitely like to try it but i'm just worried getting into trouble... anyway will try if sounds and mic works 

thanks

---

### Post by ddrichardson on 2009-08-06
> **krindik said:**
> I tried Lyx on windows but didn't really like it. It gives some strange error/warnings some times. I thought of using Texmaker/Kile but Texmaker has F1, F2 keys and 1545 doesnt have those keys. (Have to press Fn key and wifi. You make a mistake wifi goes..) And Kile doesnt have a windows version. Then again I'd like to stay with one...
FYI you can swap the function key behavior in BIOS.

---

### Post by krindik on 2009-08-06
ok.. i'll try on next reboot.. but can u use another key pair to get that behavior..?

Does NTFS write work well? Does it still say "use at ur own risk"?
I really don't want to screw my file system. Only want the super fast flexibility in linux :)

---

### Post by armandh on 2009-08-06
I dual booted my wife's HP/Compaq-v6000 laptop by using the vista utility to reduce the vista partition by 10Gb and when installing Ubuntu selected "use largest unpartitioned space"
everything works including R/RW to ntfs and she has never gone back to vista.

but it is there in case it is needed. 

such as when I coppied her oldest e-mail addresses in to a word doc
then back to Ubuntu and retrived it from the ntsf partition.

may be next year when the AV runs out I will wipe the vista.

---

### Post by RED Lemming on 2009-08-06
I was like you when I first started to switch. I had played around with the Live CD for a while and when windows yet again went silly I decided to put Ubuntu on my hdd....

Too stop me from worrying too much I backed EVERYTHING up then;

I checked my back up.

I then went to install windows, I only used a third of my hdd for it though.

I then installed Ubuntu onto the end of the hdd and set up GRUB (or let it set itself up).

Using the native Ubuntu partition editor I formatted the middle bit of my hdd to fat 32 and had that as a transfer section for common data that would be accessible from both.

Later however I discovered it was possible to tell windows to look to a different location for the contents of my documents, desktop and just about everything else so I shifted all my personal stuff from the NTFS drive to the FAT 32 partition.

Later still I set up VirtualBox and created a Windows virtual machine, that seems to run most things that Ubuntu and WINE have/had trouble with (although that is always improving as more upgrades are released for WINE etc.

I have been using my NTFS partition to randomly store stuff in of late and I can't remember the last time I booted to it tbh. I keep on using the Ubuntu partition editor to shrink it more and more and expand Ubuntu more and more.
The next time I get around to reformatting I'll get rid of it, or maybe dig out an old hdd and put windows on that in a tray just to have as a back up (what a sorry day that'll be...)

---

### Post by krindik on 2009-08-06
nice news all around :)

however, in my case all my partitions are NTFS. Since u all say it is fine I'll say bye to vista for some time.. but have to find a good vector graphics program(I saw Inkscape) and a Latex editor(Kile, Texmaker) and make mic work and sound louder ...
anyway I'll give it a try.. it is just that I don't want to bother too much in managing my computer 'cos I have more important things to do ! But can't let Vista do that for itself. it takes more memory, more cpu for nonsense services and to prettify dialog boxes  and what not but doesn't care a bit about what I want to run ...
Only plus thing is that it takes care of everything for me...

---

### Post by ugm6hr on 2009-08-06
If you already have a dual-boot, you should know how well Ubuntu meets your needs.

Just get used to using Ubuntu, and then remove Vista when you are comfortable.  Vista will stay dormant on about a 25GB partition.

I have had XP on my laptop (unused) for about a year now, and just removed it last week.  It's nice to have a security blanket when you make big changes.

---

### Post by fennec_fox on 2009-08-06
Not to just repeat what other people have said but, I don't see a problem with anything you want to do. Inkscape is quite good. You said you already have matlab so I would stick with that but, there are alternatives like octave, sage and scilab. 

One thing I was going to chime in about though is NTFS. All of my drives are NTFS except for the partition I installed ubuntu on. I'v had it for years and I have never had any problems with it. 

The only things that are kind of issues for me are if an external ntfs hd gets removed from windows without unmounting or safety removing, my ubuntu doesn't want to mount it until it's been safely removed from a windows system. Not really an issue though and may not affect all users. Just remember to safely remove.

Also, if you dual boot and you want to access everything on an ext partition from windows you'll have to install this on windows. [http://www.fs-driver.org/](http://www.fs-driver.org/)

I don't think that reads ext4 yet though.

---

### Post by Sef on 2009-08-06
Moved to Community Cafe.

---

### Post by MasterNetra on 2009-08-06
Looks like you can make the jump to Ubuntu. As for skype, its in Medibuntu's repo. Vector editing there is inkscape, if you don't need to use pan-tones (which really are meant for print jobs), then go for that. And by wireless net, you mean connecting wirelessly? If so it does that well enough. ^.^ At least it has for me. With all you need working on Ubuntu/Linux why bother with windows? ^.^...Of course you can always VM XP for testing material on or to break it for the fun of it. ^.^

---

### Post by HappyFeet on 2009-08-06
If you need to ask, then you should probably stay with windows. The desire to use and appreciate linux comes from within. It is a personal choice that does not need other people's reassurance. 

It's like going to world class auto dealer. If you need to ask the price of the car, you probably can't afford it.

---

### Post by cptrohn on 2009-08-06
> **the8thstar said:**
> Perhaps you should dual boot; this way you would have the shared benefits of both operating systems.

I have returned to a dual-boot on my laptop just because of work issues for the most part... And for One thing really.. Netflix watch it now.. (OK 2 things) and my Hauppage 950Q runs much better in Windows... (sorry it just does)

So I am curently dual booting Vista (I have stripped it down quite a bit though to only what I absolutly HAVE to have)  and Kubuntu 9.04 on the laptop and just straight Ubuntu on the desktop I built..


And just for the record SKYPE is just much better on Windows, many, many more features to choose from AND the USB phones are totally compatible with the Windows version.... and I use the phone for business quite a bit... So those are my only MUST-Haves for the windows world..(ok so THREE things)

---

### Post by HappyFeet on 2009-08-06
> **cptrohn said:**
> I have returned to a dual-boot on my laptop just because of work issues for the most part... And for One thing really.. Netflix watch it now.. (OK 2 things) and my Hauppage 950Q runs much better in Windows... (sorry it just does)

So I am curently dual booting Vista (I have stripped it down quite a bit though to only what I absolutly HAVE to have)  and Kubuntu 9.04 on the laptop and just straight Ubuntu on the desktop I built..


And just for the record SKYPE is just much better on Windows, many, many more features to choose from AND the USB phones are totally compatible with the Windows version.... and I use the phone for business quite a bit... So those are my only MUST-Haves for the windows world..(ok so THREE things)

If you hand picked the hardware based on which OS you are going to use, instead of the other way around, you would not have these issues.

---

### Post by magmon on 2009-08-06
Id say dual boot if you can't find software for everything you need to do. Id highly recommend ubuntu otherwise.

---

### Post by cptrohn on 2009-08-06
> **HappyFeet said:**
> If you hand picked the hardware based on which OS you are going to use, instead of the other way around, you would not have these issues.

OK... can you tell me which hardware would help to run Netflix Watch it now on my laptop... and direct me to a USB phone that runs fully featured on Linux....


I'll patiently wait for you to tell me it can't be done at this time.

---

### Post by krindik on 2009-08-06
> **HappyFeet said:**
> If you need to ask, then you should probably stay with windows. The desire to use and appreciate linux comes from within. It is a personal choice that does not need other people's reassurance. 

It's like going to world class auto dealer. If you need to ask the price of the car, you probably can't afford it.

Thanks. Actually I wanted to know whether this "world class car" is  really world class from your experience :)

---

