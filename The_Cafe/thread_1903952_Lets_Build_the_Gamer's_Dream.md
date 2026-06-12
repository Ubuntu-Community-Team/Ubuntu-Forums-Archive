---
title: "Lets Build the Gamer's Dream"
date: 2012-01-03
forum: The Cafe
---

### Post by thig1002 on 2012-01-03
So here I am, sitting at work, and an idea that is way too proposterous popped in my head. Why not build the ultimate emulation box? Something - that with enough money put into it - could replace every game system I own? Why? "**Proof of Concept**."

Here are the key ideas:

[LIST]
[*]Must be based on open source emulators, as well as open source OS.
[*]Assume that the machine running this has the hardware to run each and every emulator.
[LIST]
[*]What do you think the recommended system requirements would be?
[/LIST]
[*]Has a stripped down Ubuntu/Other linux OS interface, built custom for the box
[LIST]
[*]I'm picturing maybe a GRUB style menu to choose what game system to emulate.
[*]Or maybe you can choose from a list of installed games and the system automatically chooses the right emulator.
[/LIST]
[*]The ability to pop in an original disc for whichever game system is most likely out of the question, though would be a nice feature.
[*]Most importantly, it must have a saveable auto configuration to find the best possible playable settings **Per specific game.**
[*]Built in controller drivers for Xbox 360 controllers, Original Xbox controllers (Obviously those have to be modded), and PS3 controllers (Bluetooth and usb)
[/LIST]A few questions I have: What emulator would you recommend for each game system, dating back to the SNES? Anyone have suggestions or theories on how to make this a plausible concept? 

Oh, and if you've already done this (or something like this), please post some screenshots.

---

### Post by thomasw_lrd on 2012-01-03
You're not going to find emulators for the PS3 or the 360 or even the orininal XBOX.  The best you can do is Playstation 2.  The specs aren't really that bad.  I think PCSX2 runs on pretty minimal hardware (at least considering what you can build a machine for).  It has built in drivers for the controllers, and a usb device to run them is about $4.37 on Amazon.com.  It works pretty well.  The controllers also work great for the ps1 emulator, and the snes, and nes emulators I've tried.

---

### Post by thig1002 on 2012-01-03
I was aware that emulators for the ps3 and xbox360 weren't out yet. The Original xbox does infact have an emulator, but it can only run one game at the moment (Halo: Combat Evolved) and it requires some pretty heavy system resources.
 
I beleive emulators for modern systems can be built, maybe not for the practical computer, but as I mentioned before: This is "Proof of Concept". I am willing to build a machine to handle it, but to be honest I couldn't donate two cents in the knowledge of designing an emulator.
 
Really, I'm more interested in the design of a Custom Ubuntu/Linux app to run this. Not like an installed application, but more so like an OS in itself.
 
I've been thinking on how Citrix XenApp works, and I think that would be a goood base for how I want this to work. I know there is an Ubuntu version of XenApp, but I have yet to research it.
 
In essence the client would only need two things: A blazing fast ethernet connection, and a good graphics card. The server would handle everything else... Assuming that model is even plausable.

---

### Post by vehemoth on 2012-01-03
what you mean something like this [http://puppylinuxnews.org/puplets/puppy-linux-arcade/?category=puplets/puppy-linux-arcade/](http://puppylinuxnews.org/puplets/puppy-linux-arcade/?category=puplets/puppy-linux-arcade/)

---

### Post by JDShu on 2012-01-03
If you want to build something, do some research and then try to build it. Posting a random wish on a forum is not going to make something materialize according to your specifications - you have to do it yourself and expect nobody to help you until you have something viable and usable.

---

### Post by |{urse on 2012-01-03
Whatever the question is, yes it can be done. Whether it's legal, worth the effort, the money and time it will take.. I'd have to say no. 

Btw if you are on a quest for an "almost working" xbox emu,try cxbx. That's really all I can tell you. Keep looking though :) Share if you find or make something cool :)

---

### Post by mips on 2012-01-04
> **|{urse said:**
> Whatever the question is, yes it can be done. Whether it's legal, worth the effort, the money and time it will take.. I'd have to say no. 


Any current desktop spec pc (with nvidia gpu) will be able to do the job and at the same time act as a media centre.

I would look at OpenELEC as a base (it rocks!) and already has some emulator plugins but you should be able to add more.

[http://www.openelec.tv/get-openelec](http://www.openelec.tv/get-openelec)
[http://mybroadband.co.za/vb/showthread.php/376752-A-Complete-Guide-to-creating-the-Ultimate-TV-Experience](http://mybroadband.co.za/vb/showthread.php/376752-A-Complete-Guide-to-creating-the-Ultimate-TV-Experience)

So you end up with one box in your lounge that does everything from games, music, movies to photos etc.

---

### Post by BrokenKingpin on 2012-01-04
An emulator box is a decent idea, with things already setup ready to go (specially with the gamepad drivers).

If you use only open source emulators you should be fine from the legal standpoint, it is only the users who have issues as they have to use legally purchased roms. Since all the emulators will be for older systems the games for them may not be available legally from the developers. Sure, you can get pretty much any game you want from torrents or whatever, but that is not legal, and it is hard to advertise a product where you can't get the software for it legally lol.

As others have stated emulates for this gen of systems do not exist, and will not for some time to come. Even the last gen systems don't have great emulators.

What I would really like to see in the short term is a package that can easily be installed from the repo to get the drivers for most gamepads. Getting the analog sticks working on an Xbox 360 controller never really worked for me the last time I tried.

---

### Post by |{urse on 2012-01-04
> **mips said:**
> Any current desktop spec pc (with nvidia gpu) will be able to do the job and at the same time act as a media centre.

I would look at OpenELEC as a base (it rocks!) and already has some emulator plugins but you should be able to add more.

[http://www.openelec.tv/get-openelec](http://www.openelec.tv/get-openelec)
[http://mybroadband.co.za/vb/showthread.php/376752-A-Complete-Guide-to-creating-the-Ultimate-TV-Experience](http://mybroadband.co.za/vb/showthread.php/376752-A-Complete-Guide-to-creating-the-Ultimate-TV-Experience)

So you end up with one box in your lounge that does everything from games, music, movies to photos etc.

The xbox 360 runs a tri-core 3.2ghz cpu. And there aren't any emulators out there for it or any of the current consoles OP mentioned.

---

### Post by mips on 2012-01-04
> **|{urse said:**
> The xbox 360 runs a tri-core 3.2ghz cpu. And there aren't any emulators out there for it or any of the current consoles OP mentioned.

Where did I say it could? Seriously, point it out to me please.

---

### Post by thig1002 on 2012-01-04
> **JDShu said:**
> If you want to build something, do some research and then try to build it. Posting a random wish on a forum is not going to make something materialize according to your specifications - you have to do it yourself and expect nobody to help you until you have something viable and usable.


I don't recall saying I expected something to materialize. Nor did I realize I said I wanted "help" or anyone to build it for me. Also, I posted this in The Community Cafe for a reason. Because I think it is a good idea that could generate a discussion. I fully intend to attempt this "wish" after I do a little research, which by the was is what posting in this forum was for: Getting some feedback from fellow users who may have something intelligent to say.


**Stop being a troll.**

---

### Post by Basher101 on 2012-01-05
okay i got what you are trying to do..but i have to agree with |{urse, is it really worth the resources? no matter how i look at it you will just spend a ton of money and time just to proove something...not very efficient if you ask me. But that is my opinion, if you want it done you should get it done :popcorn:

---

### Post by mamamia88 on 2012-01-05
Get a wii and install homebrew channel on it.   Any emulator you can want tons of controller options and since it is antiquated technology can be had for dirt cheap.    It only takes about 5 minutes too

---

### Post by thig1002 on 2012-01-05
> **vehemoth said:**
> what you mean something like this [http://puppylinuxnews.org/puplets/puppy-linux-arcade/?category=puplets/puppy-linux-arcade/](http://puppylinuxnews.org/puplets/puppy-linux-arcade/?category=puplets/puppy-linux-arcade/)

Yes... Something very similar. Strange, I didn't come across this before. But I want to take it to the next level. ;)

> Whatever the question is, yes it can be done. Whether it's legal, worth  the effort, the money and time it will take.. I'd have to say no.You're probably right, it's not worth the effort. But that won't stop me, ha. And yes, it is legal. Assuming you own the games you play.


> The xbox 360 runs a tri-core 3.2ghz cpu. And there aren't any emulators  out there for it or any of the current consoles OP mentioned.tri-core isn't that impressive anymore ;) A Core i7 second gen (which is a quad-core) should be more than enough processor to run this mythological emulator.

---

### Post by thig1002 on 2012-01-05
> **mamamia88 said:**
> Get a wii and install homebrew channel on it.   Any emulator you can want tons of controller options and since it is antiquated technology can be had for dirt cheap.    It only takes about 5 minutes too


I already did that, and I very much enjoy my Homebrewed wii. :)

---

### Post by Basher101 on 2012-01-05
the ps3 and 360 are the only ones i was not able to emulate, due to none existant emulators. I have successfully emulated the Wii with 60 FPS on even BETTER graphic settings than the original (anti aliasing on max, 1080p resolution etc., the wii itself can only handle 480p) (btw i use ripped isos from the games my little brother owns). I also emulate only games i own.

still a Universal ALL-IN-ONE emulator sounds very interesting, yet it is against everything the companies are trying to make. Why would they go through the trouble to make systems that play specific formats if in the end it lands on the PC anyway?

they should just create games which run on the PC like on consoles - especially some multiplayer games....PC hardware outpowers those of consoles by far so it is only a software matter.


edit: > **thig1002 said:**
> I already did that, and I very much enjoy my Homebrewed wii. :)
 i got that too, my PSP has also homebrew. So many great apps, espacially eyecandy...still do not know why sony is so closed on that matter. I should be able to custimize a product i own to the way i like..

---

### Post by mamamia88 on 2012-01-05
> **thig1002 said:**
> I already did that, and I very much enjoy my Homebrewed wii. :)
seems like you want a system that can do absolutely everything.  would be awesome if it existed but unfortunately it doesn't.  you could build a kickass gaming rig with emulators and hook up your consoles to the same tv so that you have all your stuff in one place.

---

### Post by thig1002 on 2012-01-05
Basher101, shoot me an email. I'd like to know your thoughts on building a custom emulator.

---

### Post by mamamia88 on 2012-01-05
> **Basher101 said:**
> the ps3 and 360 are the only ones i was not able to emulate, due to none existant emulators. I have successfully emulated the Wii with 60 FPS on even BETTER graphic settings than the original (anti aliasing on max, 1080p resolution etc., the wii itself can only handle 480p) (btw i use ripped isos from the games my little brother owns). I also emulate only games i own.

still a Universal ALL-IN-ONE emulator sounds very interesting, yet it is against everything the companies are trying to make. Why would they go through the trouble to make systems that play specific formats if in the end it lands on the PC anyway?

they should just create games which run on the PC like on consoles - especially some multiplayer games....PC hardware outpowers those of consoles by far so it is only a software matter.


edit: 
 i got that too, my PSP has also homebrew. So many great apps, espacially eyecandy...still do not know why sony is so closed on that matter. I should be able to custimize a product i own to the way i like..
cause the reason most people homebrew it is to play games they didn't buy.     If I could find my psp I would totally do that.  Would be nice to have something to play all the old console games on with a physical controls.    And since it's a smaller screen than my tv i wouldn't be too distubed by how bad the graphics where.

---

### Post by thig1002 on 2012-01-05
Who doesn't want a kickass gaming rig? But you did just give me another idea: Multiple monitor support. I don't think my Wii has multi monitor support :P (Not that I can think of any games off the top of my head that would need/look good with).

---

### Post by Basher101 on 2012-01-05
> **thig1002 said:**
> Basher101, shoot me an email. I'd like to know your thoughts on building a custom emulator.

i might use emulators alot (espacially VisualBoy Advance, PS2 emulator, dolphin wii and gamecube emulator (all my stuff is in another country left behind catching dust...i still own it tho so its legal for me getting the games elsewhere..) and N64 emulator (both on PC and PSP^^))

the only thing is i have knowledge on hardware (otherwise the custom built computer which i am writing from would not work lol) and pretty much none on software development of any kind...in that regard i am a noob.

---

### Post by thig1002 on 2012-01-05
Same here. I can build it. But I'm still learning software development. I have a very strong grasp on a few programming languages, but I wouldn't know where to beginning in writing an emulator.

---

### Post by Basher101 on 2012-01-05
> **thig1002 said:**
> Same here. I can build it. But I'm still learning software development. I have a very strong grasp on a few programming languages, but I wouldn't know where to beginning in writing an emulator.

hell if i knew where to start to write an emulator :-D

---

### Post by mamamia88 on 2012-01-05
Hey I just thought of something that might not be practical but doable.    Build a gaming pc with all your emulators and then combine all your consoles into a single case.    They are just like computers internally but with fancy cases.    You could maybe even build some kind of imput switch to it so that all could be connected to same input on monitor.  That would be huge though and probably get super hot.

---

### Post by Basher101 on 2012-01-05
> **mamamia88 said:**
> Hey I just thought of something that might not be practical but doable.    Build a gaming pc with all your emulators and then combine all your consoles into a single case.    They are just like computers internally but with fancy cases.    You could maybe even build some kind of imput switch to it so that all could be connected to same input on monitor.  That would be huge though and probably get super hot.

[sacrasm]sure lets do the same for cars...buy a lamborghini for high speeds, a Mustang for the horsepower and a Smart to be efficient, glue them all together and use all their features :D[/sarcasm]

that would be the easiest way to make a "machine" cable of running everything you throw at it, but i am sure the OP is not looking for this solution..the idea is not bad itself, simply not what the OP wants to proove.

---

### Post by mamamia88 on 2012-01-05
> **Basher101 said:**
> [sacrasm]sure lets do the same for cars...buy a lamborghini for high speeds, a Mustang for the horsepower and a Smart to be efficient, glue them all together and use all their features :D[/sarcasm]

that would be the easiest way to make a "machine" cable of running everything you throw at it, but i am sure the OP is not looking for this solution..the idea is not bad itself, simply not what the OP wants to proove.

True I would much rather have a pc hooked up to a monitor and have my consoles hooked up to the same monitor but neatly stacked up on some kind of shelf then waste time on a case mod.     It is doable but just not practical.  They already have something similar [http://www.ign.com/articles/2010/09/07/finally-a-gaming-pc-with-a-built-in-xbox-360](http://www.ign.com/articles/2010/09/07/finally-a-gaming-pc-with-a-built-in-xbox-360) but it's probably more hassle than it's worth.

---

### Post by Basher101 on 2012-01-05
> **mamamia88 said:**
> True I would much rather have a pc hooked up to a monitor and have my consoles hooked up to the same monitor but neatly stacked up on some kind of shelf then waste time on a case mod.     It is doable but just not practical.  They already have something similar [http://www.ign.com/articles/2010/09/07/finally-a-gaming-pc-with-a-built-in-xbox-360](http://www.ign.com/articles/2010/09/07/finally-a-gaming-pc-with-a-built-in-xbox-360) but it's probably more hassle than it's worth.

Nice for an overpriced PC, but mine is better (except CPU and that i have only one GPU and no SSDs) and i only paid 980 &#8364;...still to go up to the same performance of the PC only (no built in Xbox :D) i had to pay only 500 &#8364; for an additional GTX 570 and SSDs...

edit: noticed i got offtopic. I apologize for for that

---

### Post by JDShu on 2012-01-05
> **thig1002 said:**
> I don't recall saying I expected something to materialize. Nor did I realize I said I wanted "help" or anyone to build it for me. Also, I posted this in The Community Cafe for a reason. Because I think it is a good idea that could generate a discussion. I fully intend to attempt this "wish" after I do a little research, which by the was is what posting in this forum was for: Getting some feedback from fellow users who may have something intelligent to say.


**Stop being a troll.**

Wow, chill, I was giving advice.

You're honestly not going to get a lot of meaningful information from a forum thread on UF. When I say research, I mean figure out what you need to know over google or some other search engine, and find out the possibilities yourself. Ask questions about specific things that you don't know. From what I gather in your OP, you have no clue at all where to start. That's why from where I stand, It looks more like an attempt to get people worked up about something that you probably will never achieve. Feel free to prove me wrong :)

---

### Post by thig1002 on 2012-01-05
Actually, there would be a way to do that... Hard, maybe close to impossible, yes... But maybe...

In theory, link the mother boards... maybe? I mean, lets assume they use the same type processor (which they don't, I don't think) or "could" use the same type processor... Maybe they could share RAM even? And then find a disc drive that both the 360 and PS3 will recognize...

Oh, wait. That's most likely impossible. Microsoft and Sony would never let that be a possibility.
But, maybe installing their motherboards onto a backplane, and having some form of central controller. A simple GRUB type menu to select the system you want to play....

But at any rate, not what I'm looking into. Nice thought though.

---

### Post by Lucradia on 2012-01-05
You can't build the gamer's dream in the united states, specifically due to this:
> **thig1002 said:**
> [LIST]
[*]Must be based on open source emulators, as well as open source OS.
[*]Assume that the machine running this has the hardware to run each and every emulator.
[/LIST]

It's illegal for emulators to run ROMs, emulators must play the original media, or else nothing. This includes NES, SNES, Sega Genesis, GameBoy, etc. (This is why the FCII Twin/etc. is perfectly legal.)

For instance, in order to play a PlayStation 2 game legally:

1. You must own a PlayStation 2 system, and never sell it as long as you plan to play the emulator.

2. The BIOS for your PlayStation 2 must be dumped, by you, yourself, by any means. (A BIOS is required to use the emulator.)

3. You cannot get the BIOS from off the Internet, this is illegal. (At least in the USA)

4. You cannot get ROMs (Digital copies of games from ROM Sites) to play with the games, as they too, are illegal. (See Nintendo's policy on backing up game cartridges to computer disk. This policy has been on their site since before the GameCube.)

5. You must have a DVD-Capable machine to run the original disk copies of the games you bought for PlayStation 2.

To follow these steps in the USA, you need five things:

A.) You need a fat PS2 (NOT a slim PS2, you can't dump its BIOS.)

B.) A FAT**_16_** USB Drive that's 8 GB or Less (PS2s can't recognize more.)

C.) A PlayStation One disk (IE: Legend of Legaia) not a copy or bootleg.

D.) A cheat device for PS2. (Favorable: Codebreaker) (NOT PSOne cheat device)

E.) The bootstrap injection file, edited to respond to the PSOne game you chose and the proper tool needed to dump the BIOS.

Without these, it's impossible to dump a BIOS for PS2; thus impossible to play PS2 games on your computer if you don't. (The method above will not work on a backwards compatible PlayStation 3.)

---

### Post by thig1002 on 2012-01-05
I wasn't aware of how deep the legal terms actually ran... That kind of kills things if this is to be done legally.

---

### Post by Lucradia on 2012-01-05
Changed FAT32 to FAT16, boy is it ever 2 AM.

Even with the specs in my sig, btw, PS2 games will still run sub-par to the actual system. Mainly, people use emulators nowadays to test source code, etc. Honestly, I'd rather see people use emulators in reverse. As in, use an emulator to make a game for the console.

---

### Post by thig1002 on 2012-01-05
Lucradia, that is a brilliant idea, especially for the PS2 or PS3. But when writing for the xbox360, you can connect your pc and xbox together over the network to test what you have wrote.

---

### Post by whiskeylover on 2012-01-05
Get all your favorite consoles and duct tape them together. Then duct tape them to the back of your TV.

There, you have it. One system that does everything (although not technically emulates.)

You're welcome.

---

### Post by imachavel on 2012-01-05
> **thig1002 said:**
> I was aware that emulators for the ps3 and xbox360 weren't out yet. The Original xbox does infact have an emulator, but it can only run one game at the moment (Halo: Combat Evolved) and it requires some pretty heavy system resources.
 
I beleive emulators for modern systems can be built, maybe not for the practical computer, but as I mentioned before: This is "Proof of Concept". I am willing to build a machine to handle it, but to be honest I couldn't donate two cents in the knowledge of designing an emulator.
 
Really, I'm more interested in the design of a Custom Ubuntu/Linux app to run this. Not like an installed application, but more so like an OS in itself.
 
I've been thinking on how Citrix XenApp works, and I think that would be a goood base for how I want this to work. I know there is an Ubuntu version of XenApp, but I have yet to research it.
 
In essence the client would only need two things: A blazing fast ethernet connection, and a good graphics card. The server would handle everything else... Assuming that model is even plausable.

citrix xen app is something you have to pay for? I thought it was. virtual box(oracle) has many free apps but not so much citrix or maybe I'm wrong. Why an emulator? zsnes emulator works great. I have no quarrel with it. But why an entirely new emulator? Why not something such as the ability to play any game through wine? most games don't work for wine, the ones that do have a lot of bugs at times. I'd love to know how to fix wine a bit, but am not a programmer. I have some games(red faction) metro 2033 that don't work that well(or at all.) can't say I've got a crap load of stuff so really I can't help much. But check this out:

[http://www.maxishine.com.au/forums/viewtopic.php?f=40&p=261061](http://www.maxishine.com.au/forums/viewtopic.php?f=40&p=261061)

it's coming out, and is going to change pixelation and tesselation forever. How would you emulate all that exists and will exist? I'd almost say you'd need a specific list of games that work, and a specific list that don't work, and a good idea of what you would want from the community. THEN maybe if you have some ideas we can all try out, I'd love to jump into this, as I've always wanted to be a programmer. Am I perfect with keeping up with bit processing, cores, ram, bus chip sets, bios configurations, boot configurations? No. Anyway gaming has little to do with that except gpu rendering. I could do just about anything from here if you had some ideas. Any?

---

### Post by imachavel on 2012-01-05
> **thig1002 said:**
> Lucradia, that is a brilliant idea, especially for the PS2 or PS3. But when writing for the xbox360, you can connect your pc and xbox together over the network to test what you have wrote.

what? you can? you mean they will recognize each other or are you saying they will share files? I've never ever heard of xbox 360 sharing with anything other then windows media center. If you have an idea on a way around this, let me know. THANKS :confused:

---

### Post by imachavel on 2012-01-05
> **Lucradia said:**
> Changed FAT32 to FAT16, boy is it ever 2 AM.

Even with the specs in my sig, btw, PS2 games will still run sub-par to the actual system. Mainly, people use emulators nowadays to test source code, etc. Honestly, I'd rather see people use emulators in reverse. As in, use an emulator to make a game for the console.

I'm surprised that worked. I tried converting a fat32 drive to ntfs and ended up losing a lot of files. I'm amazed that had anything to do with compatibility such as image rendering formats like direct x or open gl. honestly, I'm amazed you didn't lose a lot of files, I've always heard that converting a drive from one file system type to another is dangerous, that files should be backed up, and if anything reformat the drive. Of course this has the risk of every other setting/configuration but winblows has some weird ideas with how it changes things, and often screws up the way a worm eats an apple from the inside out.

let's not get off topic. What could you now play that you couldn't before?

---

### Post by Lucradia on 2012-01-05
> **imachavel said:**
> What could you now play that you couldn't before?

Some people also use emulators to play games that otherwise have game breaking glitches on the original consoles. For instance, in Ar Tonelico 2, there is a story boss that will crash the system if you didn't beat her in X Turns (And it wasn't a whole lot.) The codebreaker community released a PS2 cheat code (VERY long, I might add) to patch this glitch. They were able to do this with emulators, since emulators can view the address changes immediately. (You can also view address changes via Save dumping too, but that's mainly for stat changes.)

however, if you're interesting in developing for a console, specifically PS3. I would suggest calling SONY themselves, and asking if you can buy their dev console; which runs about 1000 USD.

---

### Post by mamamia88 on 2012-01-05
> **Lucradia said:**
> You can't build the gamer's dream in the united states, specifically due to this:


It's illegal for emulators to run ROMs, emulators must play the original media, or else nothing. This includes NES, SNES, Sega Genesis, GameBoy, etc. (This is why the FCII Twin/etc. is perfectly legal.)

For instance, in order to play a PlayStation 2 game legally:

1. You must own a PlayStation 2 system, and never sell it as long as you plan to play the emulator.

2. The BIOS for your PlayStation 2 must be dumped, by you, yourself, by any means. (A BIOS is required to use the emulator.)

3. You cannot get the BIOS from off the Internet, this is illegal. (At least in the USA)

4. You cannot get ROMs (Digital copies of games from ROM Sites) to play with the games, as they too, are illegal. (See Nintendo's policy on backing up game cartridges to computer disk. This policy has been on their site since before the GameCube.)

5. You must have a DVD-Capable machine to run the original disk copies of the games you bought for PlayStation 2.

To follow these steps in the USA, you need five things:

A.) You need a fat PS2 (NOT a slim PS2, you can't dump its BIOS.)

B.) A FAT**_16_** USB Drive that's 8 GB or Less (PS2s can't recognize more.)

C.) A PlayStation One disk (IE: Legend of Legaia) not a copy or bootleg.

D.) A cheat device for PS2. (Favorable: Codebreaker) (NOT PSOne cheat device)

E.) The bootstrap injection file, edited to respond to the PSOne game you chose and the proper tool needed to dump the BIOS.

Without these, it's impossible to dump a BIOS for PS2; thus impossible to play PS2 games on your computer if you don't. (The method above will not work on a backwards compatible PlayStation 3.)
There are usb devices that allow you to play original cartridges on your pc and even hook up the origianl controllers too.    I don't know if they work on linux though.  Something like that might be worth looking into.   Or you could just use emulators and find a fake usb controller than mimics the original

---

### Post by |{urse on 2012-01-06
> Any current desktop spec pc (with nvidia gpu) will be able to do the job and at the same time act as a media centre.

I assumed you were responding to the OP?!

---

### Post by thig1002 on 2012-01-06
> **imachavel said:**
> what? you can? you mean they will recognize each other or are you saying they will share files? I've never ever heard of xbox 360 sharing with anything other then windows media center. If you have an idea on a way around this, let me know. THANKS :confused:
 
Check this out: I know there's a way to easily either send the games to your xbox (maybe in realtime, I'm not sure).
[http://www.microsoft.com/download/en/details.aspx?id=23714](http://www.microsoft.com/download/en/details.aspx?id=23714)

---

### Post by thig1002 on 2012-01-06
I know very little (at the present time) about WINE and emulators. And I am strongest in the language of C++.... I will need to do some research and really "nail down" exactly what's possible, legal, and how much I am willing to do. But as soon as I have come to a desicion, maybe it could be a learning experience for the both of us.

---

### Post by Lucradia on 2012-01-07
> **thig1002 said:**
> I know very little (at the present time) about WINE and emulators. And I am strongest in the language of C++.... I will need to do some research and really "nail down" exactly what's possible, legal, and how much I am willing to do. But as soon as I have come to a desicion, maybe it could be a learning experience for the both of us.

Ask the people at ReactOS too.

clean-room reverse-engineering an emulator without needing a BIOS / etc. is perfectly legal, but it still has to play the original media (as per legal issues.) Though you could clean-room reverse engineer the BIOS too, if you could decompile it after dumping.

---

