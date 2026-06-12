---
title: "Not sure if I should go 100% Ubuntu"
date: 2007-11-14
forum: Testimonials &amp; Experiences
---

### Post by MONODA on 2007-11-14
Hi I have been running ubuntu for about a month and things have never gone as promised. I know that no os is perfect but i have been having quite a few problems. For example, if I dont reboot my computer everyday then it slows down a lot(not what I was told, when I run amarok it always crashes, firefox always crashes, programs in fullscreen crash often, and the entire system just freezes sometimes. Basically I am saying that my linux install is not stable at all! My windows partition is more stable! if anyone could tell me anything about what I could do then it would help a lot. Also if anyone could tell me the task manager equiivilant in linux that would also be great.

---

### Post by insane_alien on 2007-11-14
the 'task manager' equivalent is system-monitor.

file bug reports on those applications. the devs need to know people are having issues before they can fix things.

---

### Post by hogwartsnigel on 2007-11-14
Monodo,
Stick with it and work out problem by problem.
After transfering from Windows I've found once configured the system I have is streaming along nicely but I had a few little hurdles. These forums are invaluable...report each individual problem in a thead (searching beforehand that the solution isn't already there). List as much info about your system etc in the text or signature....you'll get all the help you'll need and be glad you got rid of winDOSE.

Blessings

Nigel

---

### Post by MONODA on 2007-11-14
Oh by the way when I boot into ubuntu it says "failed to located memsource" for about 2 seconds and then boots normally. This also happened when I had feisty. I dont think this is a problem with the installation because I installed ubuntu twice and it happened both times. Could it be that ubuntu is not fully compatable with my computer? thank you so much for your help. I really dont want to go back to windows!!!

---

### Post by Inxsible on 2007-11-14
Monoda,

Have you tried asking questions about your problems on the forum?From your post count (currently 5), it doesn't seem like you asked many questions. 

This forum is here to help you transition to Ubuntu. But at the same time, you should not expect Linux to be Windows.

If you post your problems in detail along with your machine specs, people will definitely help you as much as they can

---

### Post by LowSky on 2007-11-14
> **MONODA said:**
> Hi I have been running ubuntu for about a month and things have never gone as promised. I know that no os is perfect but i have been having quite a few problems. For example, if I dont reboot my computer everyday then it slows down a lot(not what I was told, when I run amarok it always crashes, firefox always crashes, programs in fullscreen crash often, and the entire system just freezes sometimes. 

What version of *buntu are you using? 
KDE or Gnome?
What are your computer specs?
Are you using Compiz?
What video driver are you using?
Is it a certain website that always crashes, or random?
have you tried another Browser or music application?

---

### Post by zabien1970 on 2007-11-14
Also you didn't mention what kind of computer you have, depending on your hardware you may be better running fiesty instead of gutsy, older computers don't always do so well running the latest OS

---

### Post by MONODA on 2007-11-14
I am using Ubuntu Gnome. I have an hp dv6395 with 2gb ram core 2 duo 2.00 Ghz processor, Nvidia gefore go 7400 128. Yes I am running compiz, would that be the problem, I really wont run Ubuntu without it because it helps me so much with my work, you know the scale plugin and all. and firefox just crashes on random pages, I tried epiphany whichwas nice but doesnt have any extentions like adblock plus.

---

### Post by Inxsible on 2007-11-14
> **MONODA said:**
> I am using Ubuntu Gnome. I have an hp dv6395 with 2gb ram core 2 duo 2.00 Ghz processor, Nvidia gefore go 7400 128. Yes I am running compiz, would that be the problem, I really wont run Ubuntu without it because it helps me so much with my work, you know the scale plugin and all. and firefox just crashes on random pages, I tried epiphany whichwas nice but doesnt have any extentions like adblock plus.

I have a HP dv9000t, and everything worked out of the box for me. Since your compiz is working, it means that the Nvidia drivers are properly configured. 

For the browser you can use, Swiftweasel or Swiftfox which are based on Firefox, but are optimized for Linux and are a bit more stable. They also support ALL the add-ons that firefox does.

---

### Post by stimpack on 2007-11-14
I have had to ditch Firefox, it is so bad. The ultimate slap in the face however is that it is the Linux version that crashes and it crashes most on the ubuntuforums!.

Using Opera, which is nice, but PITA setting up a proxy to adblock properly, and I miss my FF addons soooooooooo much.

---

### Post by Inxsible on 2007-11-14
> **stimpack said:**
> I have had to ditch Firefox, it is so bad. The ultimate slap in the face however is that it is the Linux version that crashes and it crashes most on the ubuntuforums!.

Using Opera, which is nice, but PITA setting up a proxy to adblock properly, and I miss my FF addons soooooooooo much.

Swiftweasel or SwiftFox are your answers :D

SwiftWeasel has 32 bit and 64 bit debs available. Swiftfox only has 32 bit, but it also works in 64bit architecture.

---

### Post by MONODA on 2007-11-14
ok i just tried to launch amarok but it wouldnt launch (ichecked the taskbar) so i decided to uninstall it. I rwstarted but would not work. so i did cnrtl alt backspace and returned to the login menu but it looked different than how I had set it to look like but anyway when I finally restarted it said, "sda4has been mounted 38 times and has not been checked, a check has been forced. What is gong on!?!?! i dont even have an sda4!!

---

### Post by Inxsible on 2007-11-14
> **MONODA said:**
> ok i just tried to launch amarok but it wouldnt launch (ichecked the taskbar) so i decided to uninstall it. I rwstarted but would not work. so i did cnrtl alt backspace and returned to the login menu but it looked different than how I had set it to look like but anyway when I finally restarted it said, "sda4has been mounted 38 times and has not been checked, a check has been forced. What is gong on!?!?! i dont even have an sda4!!

Drives are automatically checked for errors after they are mounted about 30-35 times. You dont have to worry about it.

Post the output of ```
sudo fdisk -l
``` -l is lowercase L. That will show you what drives you have.

---

### Post by MONODA on 2007-11-14
O thanx sry about that I just remembered that I have a recovery drive for windows. O by the way is there a way to use microsoft office for linux, if I could I would completely get rid of windows. I know there is oppen office and Gnome office but they just dont cut it. Openoffice changes the formatting of files when saved in microsoft office type and doesnt have the features I want. btw I have a legal copy of ms office.

---

### Post by Inxsible on 2007-11-14
> **MONODA said:**
> O thanx sry about that I just remembered that I have a recovery drive for windows. O by the way is there a way to use microsoft office for linux, if I could I would completely get rid of windows. I know there is oppen office and Gnome office but they just dont cut it. Openoffice changes the formatting of files when saved in microsoft office type and doesnt have the features I want. btw I have a legal copy of ms office.
You can try using it in Wine, or Crossover Office. But I don't think people have had much success with MS Office in Wine. I keep away from all that :)

You can also install Windows in a VM and then use MS Office within it.

---

### Post by skyjacker on 2007-11-14
> **MONODA said:**
> O thanx sry about that I just remembered that I have a recovery drive for windows. O by the way is there a way to use microsoft office for linux, if I could I would completely get rid of windows. I know there is oppen office and Gnome office but they just dont cut it. Openoffice changes the formatting of files when saved in microsoft office type and doesnt have the features I want. btw I have a legal copy of ms office.
You could try "koffice suite. I switched from OO to that after I had so much trouble with OO since the upgrade to Gutsy. Haven't had any problems with it being compatable with MS office. Hang in there. Ask this forum for help 24-7

---

### Post by OffAxis on 2007-11-14
What applications from MS Office do you use?
You can get some standalone apps for some stuff.

I'll throw a 2nd for KOffice. I didn't much like openoffice, but tried to power through. Turns out I should've just started using KOffice earlier.

---

### Post by mivo on 2007-11-14
Nobody promised you anything, you know. ;) I haven't had a single crash of an application in 7.10 and I never turn off my computer. There is no difference in performance after one minute uptime or two weeks for me. I don't use KDE applications, though, since I did have crashing troubles with them a couple of months ago. I'd also try to migrate to OpenOffice, even if it may take some adjusting, unless you really and absolutely depend on 100% MS Office compatibility for your job.

Oh, and I use Swiftweasel instead of Firefox, too, but didn't have Firefox issues when I did use it.

---

### Post by MONODA on 2007-11-14
well is there a way to bring up system monitor with a keystroke combination like in windows.

---

### Post by mivo on 2007-11-14
> **MONODA said:**
> well is there a way to bring up system monitor with a keystroke combination like in windows.

Alt+F2 and type *gnome-system-monitor*. You can probably bind it to a key as well.

By the way, if you have a bit of time and are interested, read [this article]("http://linux.oneandoneis2.org/LNW.htm"). It helped me when I switched from Windows to Linux.

---

### Post by CatKiller on 2007-11-14
Crashes and freezes are often hardware-related. Usually memory or power supply. Regardless of operating system.

---

### Post by philinux on 2007-11-14
For a quick shortcut

Find system monitor in the menu and right click then add to panel.

---

### Post by SonicSteve on 2007-11-14
> **CatKiller said:**
> Crashes and freezes are often hardware-related. Usually memory or power supply. Regardless of operating system.

I fix computers for a living. I find that quite often when someone complains that such and such a programs is crashing it is hardware related. A flakey Hard drive can cause many problems without even giving any signs of failure until you really test it. 
- Bad sectors
- spinup failures
These are the most common failures that occur and can often look like bad software.
I have yet to come across a linux app that is easy to use and gives good test features. HDtune is the best one I've found that is free for windows. I run the ultimate boot disk for windows to diagnose Hard drives.

---

### Post by Boondock5 on 2007-11-14
If I may be so bold.

I had a lot of the same problems initially discussed in the first post of this thread. At that time I was running the ADDON upgrade from fiesty. After a week of things getting slower and slower things finally stopped working all together firefox no worky, infact ended up with no internet access at all. that ended it for me.
I dumped gutsy, Reinstalled winders, downloaded a full version of gutsy, then burned it to disk, and installed it. all but one problem is gone. I have since even fixed it with alittle help from my friends here in the forums turned off all the previews of all music and video and walla no more trouble. very stable, very fast.

 It's that upgrade thing thats not so hot. Get the full version!

---

### Post by MONODA on 2007-11-14
I have scanned my hard drive and found no defects. Whenever I try to do something relatively hard on my system like copying all my music to my mp3 player, the app crashes then responds later... is this normal??? UUUGHHH!!! it just crashed in the middle of synchronizing!!! i am using rythmbox by the way.

---

### Post by Inxsible on 2007-11-14
If by crash, you mean it goes dark grey and then comes back. Thats normal, it only means that the app is busy and doing something in the background

---

### Post by Martin Witte on 2007-11-14
on wine you can install ms office, i tested myself version 2000 - that works, according to this [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3214](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3214) some apps of 2003 work as well, apparently 2007 does not work at all (yet?)

---

### Post by MONODA on 2007-11-14
well yeah that happened but it crashed ten seconds later... What can I do to sync music to my portable player?

---

### Post by Inxsible on 2007-11-14
> **MONODA said:**
> well yeah that happened but it crashed ten seconds later... What can I do to sync music to my portable player?
Use any number of apps available
1) amarok
2) rhythmbox
3) banshee
4) listen
5) songbird(altho I am not sure if this allows syncing)

---

### Post by MONODA on 2007-11-14
thanx for ur help but non of them could even detect either of my mp3 players (I have a sansa e260 and a creative zen micro) does anyone know a way to get them to work with linux. btw I tried Neutrino it does not work

---

### Post by MONODA on 2007-11-23
I really cant take it anymore, i installed Ubuntu thinking it would be better than windows but I was utterly wrong! Ever since I first installed it I have been having many problems. First of all, my computer restarts without any sign every so often, I am unable to suspend or hibernate, I cant connect to a wired and wireless network at the same time. All of this stuff works perfectly in both windows and mac and I really dont know why it doesnt in Ubuntu. I really want this to work. Please could someone tell me what is happening. Could it be my hardware is not compatible? thanks for your time.

---

### Post by HermanAB on 2007-11-23
This is the wrong forum for complaints about Ubuntu.  Try this one: [http://support.microsoft.com/](http://support.microsoft.com/)

---

### Post by jingo811 on 2007-11-23
Your symptoms indicates nothing wrong.  That's how it's supposed to be with Linux.  If you want an OS that works right away then that's why Windows Vista and Mac OS charges money.
Linux charges you 0 cash.  **You want it too work then you need to invest your time**.  That's the price of admission into this exclusive and not so easy club.  Only the tough survives this test.  Best of lucks!

---

### Post by mivo on 2007-11-23
I disagree with the implication that Linux is "worse" or "not as easy" because it doesn't cost money. What a horrible take on the open source idea and Linux in general.

I also don't really think that it's very helpful to flame someone who is frustrated because they experience technical issues.

---

### Post by jingo811 on 2007-11-23
You can't solve everything on your 'puter all at once.  Break it down into pieces and just see where things leads.

---

### Post by Zero Prime on 2007-11-23
If you really want help we need your system specs.  What hardware do you have installed.

---

### Post by tiachopvutru on 2007-11-23
Well, seeing that the latest version of Ubuntu, from what I've heard, is considerably buggy than the past releases, I would say that's why as well as your hardware does not really like Ubuntu. With that said, I've heard many HP laptop users have better experience with Feisty Fawn (7.04) so you may want to try that version. It doesn't have as many features so you have to add them yourself, but it may be more stable for you. I won't guarantee it to 100%, though. In the end, however, it'll come down to your choice whether you'll keep Ubuntu or stay away from it; if you choose the latter, I'm hoping you're coming back in the future. :)

I realize this is suppose to be a help thread, sorry about that I can't offer any.

---

### Post by Dr Small on 2007-11-23
> **mivo said:**
> I disagree with the implication that Linux is "worse" or "not as easy" because it doesn't cost money. What a horrible take on the open source idea and Linux in general.

I also don't really think that it's very helpful to flame someone who is frustrated because they experience technical issues.
I agree with you.
Just because it is free and opensource does not mean it will not work out of the box.

All of my installations have worked, and then I had to do some minor tweaking to get the system the way I want it. Windows systems give you absolutely NO customization. It's standard and out of the box, so everyone has the same tastes.

But maybe, we can help you through your problems so you won't have to go back to Windows.

Dr Small

---

### Post by bitterbug on 2007-11-23
I'd just like to hijack this thread to tell Jingo that's an awesome avatar!
I actually had one of those stupid little phones you pull around on wheels when I was a baby!

I now return you to your regularly scheduled complaint thread.

---

### Post by Dr Small on 2007-11-23
> **bitterbug said:**
> I'd just like to hijack this thread to tell Jingo that's an awesome avatar!
I actually had one of those stupid little phones you pull around on wheels when I was a baby!

I now return you to your regularly scheduled complaint thread.
I think it is also a support thread..

---

### Post by nickpaton on 2007-11-23
I can appreciate the frustration when things go wrong like that.

How about seeing if we can help out.  What applications are you trying to use, and is there a particular program that you are using when the PC crashes.
Did you have any problems loading Ubuntu, and which version of Gutsy are you using - 32 or 64bit?

Try and give us as much information as possible.

I personally have an HP Compaq nx6125 laptop and an AMD XP3200 based PC, both of which run well on 32bit Gutsy.  Installing was so easy, especially all the various add on programs I needed.

To encourage you, a couple of us have been helping a Ubuntu noob who was a 100% Windows user.
He now has Gutsy 7.10 installed with wireless and wired network connections, and is sucessfully networked to his Xbox using Samba.  
He finds Ubuntu so stable that he will only now use Windows for one particular application.
He did say that there is a steep learning curve to installing and setting up Ubuntu, but in his opinion it's the best Linux distro by far, and was worth perservering with.

Good luck and let us know how we can help

Nick

---

### Post by Jerry N on 2007-11-23
> **Dr Small said:**
> I agree with you.
 Windows systems give you absolutely NO customization. It's standard and out of the box, so everyone has the same tastes.


I bet that's a big surprise to a lot of Windows XP users!!!  

Jerry

---

### Post by philinux on 2007-11-23
Ok give the guy a break it's not all rosie with some hardware.

to the OP post your problems one by one maybe we can fix em one by one.

---

### Post by Flying caveman on 2007-11-23
Well I though HermanAB's response was a little terse, but then read some of the OP's other posts.    Turns out some people are easier to help than others.

---

### Post by jflaker on 2007-11-23
> **jingo811 said:**
> Your symptoms indicates nothing wrong.  That's how it's supposed to be with Linux.  If you want an OS that works right away then that's why Windows Vista and Mac OS charges money.
Linux charges you 0 cash.  **You want it too work then you need to invest your time**.  That's the price of admission into this exclusive and not so easy club.  Only the tough survives this test.  Best of lucks!

Not true......Ubuntu DOES work out of the box, it is some hardware that may have issues as drivers are not readily available for ALL hardware.  So THERE, you may need to invest a little time to find compatible drivers.  

If you have issues, break them down into each individual problem and we can work through them.  VISTA does not install all hardware on ALL computers, What you are used to are OEM installs where special drivers are provided to make it work  Try installing Vista or XP on your hardware and I guarrantee that you will need to seek out and download at LEAST 3 drivers to get it working right (network, video and sound are usually not working on first try).

So, tell us what ails you and we will work throught it.

---

### Post by atlfalcons866 on 2007-11-23
I did the best thing ever today, THROWING OUT my windows vista disc cause vista sucks.

---

### Post by john262 on 2007-11-23
I suggest that you check out a Microsoft support group such as microsoft.public.internetexplorer.general. There is one poster after another with all  kinds of problems and all kinds of complaints. It's not just Ubuntu or Linux. Poeple have problems with any operating system, not just Ubuntu.

But having said that, if you stick with it you will eventually be glad you did. Hang out in these forums and read and learn. I doubt if there is any problem that you have that someone else hasn't had already and that hasn't been discussed in this forum. Once you get the hang of it, you will never go back. It's faster and more secure and more fun and more configurable and so much more. It's not just that it's free. Even if I had a million dollars, which I don't, LOL, I still wouldn't ever go back to Windows.

---

### Post by CCNA_student on 2007-11-23
As Zero Prime said, we need to know what hardware you have. Some companies do not give out much source code for their firmware, like Broadcom. I had a Broadcom Wireless NIC in my Gateway MX6124, and I had to replace with the Intel 2915ABG. And if it is that much trouble and you need your computer to work, you might have to use loser Xpoo. In fact, I still cannot get Totem Movie Player to play any encrypted DVD's, so I can watch almost no DVD's on my system still. And VLC only plays some DVD's on Linux and not others. Oh by the way, can any of you help me with that? There is not much else I can tell you for now.

---

### Post by aysiu on 2007-11-23
> **Dr Small said:**
> I think it is also a support thread..
No, it's not.

If you want to support the OP, do so in [one of these other threads](http://ubuntuforums.org/search.php?do=process&showposts=0&starteronly=1&exactname=1&searchuser=MONODA).

From the way this is phrased (including the subject title) and its vagueness, this is definitely a complaint thread, not a support thread.

---

### Post by erlyrisa on 2007-11-23
Funny how my windows PC has problems that you describe...

My Windows laptop...

-no Bluetooth.
-and wireless don't work

--Oh and I bought it from a large chain store.

--It's running XP SP2.

,as with linux. I think it has something todo with the Drivers.
...but with linux atleast, if I have the know how thier are great instructionals on writing your own drivers.
(then again thier is the same for windows)

---blame your driver Manufacturers.... you get what you pay for.
eg. I bought a $40 dolar MinidigiCam ... won't even attempt to try on Linux.

It's sad when you know that it would only take an extra day or 2 of programming to port a driver to Linux, but the manufacturers won't...
why...
they are OWNED... by ...

What's sadder, is if ithey ported it to OSX, than the code is already thier and ready for Linux, only the Frontend has to be redone - but NO! they still compile with the Frontend embedded!! -at least give us the Crux of the software then the Linux dudes will take care of the rest.

---

### Post by MONODA on 2007-11-24
Thank you all for your replies. I apologize for complaining like I did, i should have asked for support, but I was very angry when I wrote this thread because I had been working on something in open office when I hibernated and then was unabke to wake it up. My comp specs are in my signature. I really do like ubuntu much more than any other os but i was very frustrated when I wrote this thread. The things i am having most trouble with are when my computer restarts randomly. Why does this happen. Is there anything I can do to prevent it? Thank you. Also is there anyway to connect to a wired and a wireless network at the same time?

---

### Post by TenPlus1 on 2007-11-24
Ubuntu can work perfectly out-of-the-box on most systems but you have to remember that their will be hardware out there, especially the old stuff that will need your attention to get it working properly...

Unlike Windows, Ubuntu will give you access to loads of free software and is more secure to use on a basic install...  Patience is the key and in the end it is worth it...  My setup is exactly the way I want it and it far outperforms WinXP on many levels...

---

### Post by frankos44 on 2007-11-24
Ive installed Ubuntu from Edgy to Gutsy on many computers and never experienced problems like those you mentioned. Are you sure your hardware  is  stable. You could try:

1. Running a memory test from the Ubuntu installation (Memory problems cause all sorts of strange things on any OS

2. Is you BIOS set correctly. Its no good trying to run bits of hardware such as memory at the wrong clock speed. 

3. Do your memory sticks even match?

4. There are all sorts of issues with graphics cards, it might just be you need to try another. Ubuntu have done their best to support as many graphics cards as possible. Windows on the other hand have an unfair advantage in as much the first drivers written by most manufacturers are for windows.

Wireless networking is a piece of cake, I find it strange you are having problems with this too.

Obviously something silly is going on because Ubuntu is fast, secure and very usable. 

Maybe you need to cast your mind back when you first saw windows, you probable had your computer set up in advance and didn't even know what a driver was.

This isn't meant to offend but from your initial reaction, It sounds to me as if you lack some experience and I can understand you being frustrated. Complaining on the forum achieves nothing other than making everybody aware that you are a "tyre kicker", asking for help on the other hand will achieve far more.

I can assure you I have and still do experience nightmares with all operating systems in my line of work. 

After 30 years of experience in computing of which 15 years as a hardware engineer, 10 years a Microsoft software developer,  I think Linux is superior and would not consider windows as a viable choice ever again.

Give it a chance and i'm sure many people on here would be glad to help.

Frankos

---

### Post by MONODA on 2007-11-24
Thank you for your reply. but i have decided to reinstall ubuntu because i think my problems were caused from a faulty installation. Alos could you tell me how to connect to both a wired and wireless network at the same time?

---

### Post by jingo811 on 2007-11-24
> **jflaker said:**
> Not true......Ubuntu DOES work out of the box, it is some hardware that may have issues as drivers are not readily available for ALL hardware.  So THERE, you may need to invest a little time to find compatible drivers.  
......
......

That might be true for the majority of tests.  But one or 2 kernel upgrades and voila you no longer have a working Printer and Scanner anymore doesn't really qualify it to be titled "working out of the box".

That why you need to tell Linux newbies that Ubuntu is harder to use than Windows so they don't get some illusionary ideas of Ubuntu.  You always have to fix things on any Linux distro compared to Windows that usually never changes and moves.


> **MONODA said:**
> Thank you for your reply. but i have decided to reinstall ubuntu because i think my problems were caused from a faulty installation. Alos could you tell me how to connect to both a wired and wireless network at the same time?
Never tried to connect with both at once.  But there should be some networking manager icon next to the volume icon where you could switch the network NICs on and off.
But be prepared for not having wireless access I'd say from personal observation that 80% of Wireless NICs don't work right away without some heavy tinkering.


> **MONODA said:**
> 
Thank you all for your replies. I apologize for complaining like I did, i should have asked for support, but I was very angry when I wrote this thread because I had been working on something in open office when I hibernated and then was unabke to wake it up. My comp specs are in my signature. I really do like ubuntu much more than any other os but i was very frustrated when I wrote this thread. The things i am having most trouble with are when my computer restarts randomly. Why does this happen. Is there anything I can do to prevent it?

Been there feels like yesterday I did some good 'ol all out Linux complaining :-)
**Take this into consideration Ubuntu Feisty 7.04 has been used by the public since April 2007 Ubuntu Gutsy has been used by the public since October 2007 that's less than a month of existence time.  Feisty is stable Gutsy is well you do the math.**

---

### Post by MNICY on 2007-11-25
> **tiachopvutru said:**
> Well, seeing that the latest version of Ubuntu, from what I've heard, is considerably buggy than the past releases, I would say that's why as well as your hardware does not really like Ubuntu. With that said, I've heard many HP laptop users have better experience with Feisty Fawn (7.04) so you may want to try that version. It doesn't have as many features so you have to add them yourself, but it may be more stable for you. I won't guarantee it to 100%, though. In the end, however, it'll come down to your choice whether you'll keep Ubuntu or stay away from it; if you choose the latter, I'm hoping you're coming back in the future. :)

I realize this is suppose to be a help thread, sorry about that I can't offer any.

I dont agree. Ubuntu 7.10 is a GOD compaired to 7.04 :D
bugs? Where?

I only have problems when i get "sudo happy" :lolflag:
If i leave the major setting alone, and dont install any weird programs in alpha stages, then Ubuntu 7.10 seems stable, fast, and simply works.

---

### Post by MONODA on 2007-11-25
Thank you for ur replies but i reinstalled and everything is working fine. I think all my problems were my fault.

---

### Post by jingo811 on 2007-11-25
**** happens in the world of Linux all the time :)

---

### Post by AgentZ86 on 2007-11-25
> **MONODA said:**
> I really cant take it anymore, i installed Ubuntu thinking it would be better than windows but I was utterly wrong! Ever since I first installed it I have been having many problems. First of all, my computer restarts without any sign every so often, I am unable to suspend or hibernate, I cant connect to a wired and wireless network at the same time. All of this stuff works perfectly in both windows and mac and I really dont know why it doesnt in Ubuntu. I really want this to work. Please could someone tell me what is happening. Could it be my hardware is not compatible? thanks for your time.

Yes I can help with this.
I would suspect that you installed Ubunut before checking the hardware compatibility.Yes I believe its your hardware which is typical; Yes,linux  it's easier to install now days.But it sometimes is a pain but worth the effort to research as best you can with your hardware to see if anyone is using Ubuntu with said hardware and if there is any problems with it.

But like any OS including windows if your hardware is not compatible or has known issues with a particular OS etc. then it's not going to provide the sort of satisfaction your looking for. I found this out back when they came out with Win2k. I was having a problem with a game I was playing and never could get it working right, So after reinstallation and purchase of the new win2000 which was suppose to be more stable and better. Well the game worked out ok, but now all my hardware was not compatible and no drivers for my hardware at that time.
Whew and I had just bought some new stuff, printer,scanner,webcam etc. and low and behold win2000 did not have drivers nor did the manufacturer since the hardware I bought was not outdated, but no longer being manufactured. The were rolling out the new stuff that had win2000 drivers and it was very fustrating to find out that my new hardware only 2 months out of the box and I could not use it with windxp so I either had to go back to win98 and not play my game, or stay with win2000 and buy new hardware again.

Each and every OS including windows will have it's pros and cons but especially if the OS has not enough support for the hardware you plan to use or if the hardware does not have drivers for the OS etc. and so on.,

I learned this the hard way myself over the years. But keep in mind I've also had the similar effects on MS products as well as linux products.

The effect is the same on either type of OS which will be a definite dissatisfaction across the board.

Anyhow I know you will love Ubuntu and other linux OS's as long as your hardware is compatible in advance.

I've installed many OS's since I decided to be sure I had compatible hardware first prior to installation. 

And all OS's have been very pleasant fun and my computing experiences have been great every since.

Yes there can be bugs in All OS's including MS thats why they all keep coming out with patches and updates etc. Always making things better.

Anyhow I hope this helps as it's helps me over the years and FYI I am currently using Ubuntu Gutsy 7.10 and keep is updated daily and have not had any problems freezups lockups etc. I even installed windows games on here using wine, and also IE6 incase I absolutly had to see a site that required IE,  (note with wine let I've had better luck letting the graphics be controlled as disconnected from the windows manager and letting the application take control of it's own window just fyi)

To make a long story short compatible hardware will give the most out of your OS and I must say Ubuntu has been the best experience ever and I've installed just about every OS out there.

Also I have been reselling used IBM systems with Ubuntu on them. IBM seems to like Ubuntu OS.

Well thats all I know.

---

### Post by AgentZ86 on 2007-11-25
> **MONODA said:**
> Thank you all for your replies. I apologize for complaining like I did, i should have asked for support, but I was very angry when I wrote this thread because I had been working on something in open office when I hibernated and then was unabke to wake it up. My comp specs are in my signature. I really do like ubuntu much more than any other os but i was very frustrated when I wrote this thread. The things i am having most trouble with are when my computer restarts randomly. Why does this happen. Is there anything I can do to prevent it? Thank you. Also is there anyway to connect to a wired and a wireless network at the same time?

Curious about something ? 

Is this also happening in Windows ? cause is sounds like an overheating problem with the processor ? But it does not have to be I'm just speculating that this is a symptom of overheating.

---

### Post by MONODA on 2007-11-25
> **AgentZ86 said:**
>  IE6 incase I absolutly had to see a site that required IE.

you could have gotten the ie tab extension for firefox.

---

### Post by armandh on 2007-11-25
power supply problems
power line problems
intermittent hardware
even prior lightning damage to the MOBO
the 800 P-III with Ubuntu 7.04 my brother in law uses has one slot epoxied over, 
the interrupt is flaky [where the modem once was.]
don't forget aging power caps.

---

### Post by nickpaton on 2007-11-25
The OP has marked the thread Solved, so I guess he / she doesn't need any further help here.

---

### Post by Tulipe on 2007-11-25
This might be off-topic, but when I see all the comments here, and elsewhere in this forum, that is one of the reasons for me to let go of Windows and install Ubuntu, which is a great OS and works fine for me, and on 4 other pc's in my house.


Quote:
Originally Posted by AgentZ86 View Post
IE6 incase I absolutly had to see a site that required IE.
you could have gotten the ie tab extension for firefox.

Reply to Monoda : the IE tab in Firefox works only if you have installed IE.

---

### Post by MONODA on 2007-11-28
Hi i have started to use Ubuntu and like it very much but there are things that are stopping me from removing windows (i dual-boot). These things are that I am worried that I may need it some time and that Open office can not do some of the things that ms office can do. I have a recovery drive in my pc, if i install ubuntu completely on my main drive and keep my recovery drive the way it is, will i be able to recover windows later? thank you in advance. Also is there a way to save in ms office format from open office without messing up the formation. Whenever I save in ms office the margins get messed up.

---

### Post by mikewhatever on 2007-11-28
If you think you may need Windows, don't remove it. Keep dual booting and save yourself the trouble of recovering. The recovery drive you have should work, in case you do need to recover (Widows I assume).
Open Office can save documents in .doc and other MS only formats, but since you are planning to remove Windows, why would you need it? If you do keep Windows, then there is OO for it too, and if you ever get a document that does not render, use an online converter such as [http://www.zamzar.com/](http://www.zamzar.com/).

---

### Post by pebkac on 2007-11-28
> **MONODA said:**
> Also is there a way to save in ms office format from open office without messing up the formation. Whenever I save in ms office the margins get messed up.

Have you tried to save in *.RTF (rich text format?) It is more universal than *.doc (Microsoft Word). It works well for me anyway.

---

### Post by forestpixie on 2007-11-28
I'd agree with mikewhatever - apart from anything I'd say if you feel the need to ask the question I'd wait a while - if you've only been doing it since Oct I would carry on dual booting for the time being.

---

### Post by ericesque on 2007-11-28
I would agree with the general sentiment.  

I too 
have an itch to ditch 
that which is
 not the *nix.  

BUT hdd space is cheap.  My time is not.  If I need XP for some reason, I'd rather it be a simple reboot to a painful reinstall.

---

### Post by MONODA on 2007-12-06
I have used ubuntu for about a month and am very happy with it. even though i like it very much, it still has some problems that need to be sorted out and some things that need to be done. first of all i want to say that ubuntu is awesome but it has never really felt like my real os. I think this is because there are just some really big and weird problems. First of all is that sometimes ubuntu fails during shutdown, what i mean is when i try to shutdown, sometimes i see the loading screen for a second then i see, "failed to terminate" whatever application. also i get really random restarts. I am not the only one that is experiencing this for sure. ALSO i am unable to hibernate which is really annoying. I really wish they would stop making features for a while and fix all these weird problems. ive never had these problems with windows(except the shutdown error). dont get me wrong i dont prefer windows there are other problems but windows doesnt really have these super weird problems it just has A LOT of annoying ones. Thats what i have to say for problems now i want to say what Ubuntu needs to for it to become the ultimate OS. First of all there are two things that it needs that mac has. 1. Super fast boot-up(like mac's 30ish second one). 2. Laptops made by specifically for Ubuntu with a look and feel for it. This way you could be sure that everything is compatible and you could get a warranty. One more thing that Ubuntu needs is for the visual effects(compiz) to become more stable and stop interfering with the rest of the OS.(I know that it is coming). thats all I have to say. Comment as you wish.

---

### Post by bonzodog on 2007-12-06
um...
Could you maybe edit this post and break it up into separate paragraphs?

I'm actually finding it difficult to read.

We might be able to answer some of your queries then, when you clearly list them.

---

### Post by SunnyRabbiera on 2007-12-06
well it really depends, me I never had any shutdown issues though it might be related to the fact I own a desktop.
I heard there are some issues with shutdown on laptops and there might be a bug out there who knows.
I am hoping Hardy fixes a lot of issues though, as the 7 series of ubuntu has been rather disappointing.

---

### Post by Vince4Amy on 2007-12-06
I found the shutdown issues only happen on 7.10. The solution until 8.04 I've done is to install 7.04 and then update to the latest Kernel, there's nothing new in 7.10 I like anyway.

---

### Post by Nano Geek on 2007-12-06
It sounds like your hardware is going out if you are having random reboots and also having trouble shuting down in Windows and Linux.  

And as for Hibernating, that's a tricky area for Linux. Windows gets all of it's drivers from the manufactures, so of course it has no problem, but Linux has to code its own and because of the vast variety of hardware, it doesn't always work.

---

### Post by igknighted on 2007-12-06
> **MONODA said:**
> First of all there are two things that it needs that mac has. 1. Super fast boot-up(like mac's 30ish second one). 2. Laptops made by specifically for Ubuntu with a look and feel for it. This way you could be sure that everything is compatible and you could get a warranty. One more thing that Ubuntu needs is for the visual effects(compiz) to become more stable and stop interfering with the rest of the OS.(I know that it is coming). thats all I have to say. Comment as you wish.

For th first parts, file bug reports.

For the rest, you are comparing a hardware company to a software community... not really sure what you are getting at.

1)  Linux has drivers for thousands of devices built in to the kernel.  If you custom compiled linux for booting with the same amount of device support OSX has, it would probably boot faster.  Plus, with linux bios you can boot a linux system in like 10 seconds.  And that is a very fair comparisson, as Apple has full control of their bios too.

2) Perhaps... but is there a market?  I doubt it.  You probably couldn't get price competitive. I wouldn't pay more for a "pretty" laptop, I could simply mod it myself if I cared that much.  I feel like many linux users feel the same.  Plus, most of use (polls in the past have supported this) prefer to install ourselves rather than keep it the way it came, because many have their own little tweaks they use.  So I don't see this business really working.  Besides, unless you had mobo that you could run linux-bios on and other neat tricks as above, it really isn't worth it.  The only OEM that matters so far is Dell, because they are large enough to keep the costs down.

As for Compiz, I think it should be removed.  Period.  Don't get me wrong, I love the effects.  But Compiz is not a long-term solution.  It is a testbed for what will be mainlined into Metacity and Kwin.  Kwin in KDE4 already shows a lot of work on compositing, and it is appearing in the SVN for metacity too.  Xfce has long had simple compositing as well.  By merging these effects into gnome and kde, you will be adding features into an already stabe WM, whereas Compiz had to write a whole new WM.

---

### Post by Nano Geek on 2007-12-06
> **igknighted said:**
> As for Compiz, I think it should be removed.  Period.  Don't get me wrong, I love the effects.  But Compiz is not a long-term solution.  It is a testbed for what will be mainlined into Metacity and Kwin.  Kwin in KDE4 already shows a lot of work on compositing, and it is appearing in the SVN for metacity too.  Xfce has long had simple compositing as well.  By merging these effects into gnome and kde, you will be adding features into an already stabe WM, whereas Compiz had to write a whole new WM.But Compiz is totally different compared to Kwin and Metacity. To achieve the same effects in either one of those, it would basically call for a rewrite of the code, which would be harder than perfecting Compiz correct?

---

### Post by FuturePilot on 2007-12-06
> **igknighted said:**
> 

As for Compiz, I think it should be removed.  Period.  Don't get me wrong, I love the effects.  But Compiz is not a long-term solution.  It is a testbed for what will be mainlined into Metacity and Kwin.  Kwin in KDE4 already shows a lot of work on compositing, and it is appearing in the SVN for metacity too.  Xfce has long had simple compositing as well.  By merging these effects into gnome and kde, you will be adding features into an already stabe WM, whereas Compiz had to write a whole new WM.

Wow, this is very interesting. I'm very curious to see what will happen.

---

### Post by MONODA on 2007-12-06
Yeah I guess you are right (igknighted) for saying that you cant really compare the two. Also I kind of side with you for saying that compiz should be removed but I still think that some effects could be implemented without all the useless stuff. (I mean a lot of the features are really useful).
About the Ububook(macbook) i guess you are right but I searched a bit and found some sites like emperor linux and discovered that they modify and tweak the linux kernel which i dont really like. But the good thing about buying a computer with Ubuntu preinstalled is that you can be sure that everything is going to work and you wont have to pay for windows.

---

### Post by SunnyRabbiera on 2007-12-06
well granted there are other linux systems that boot faster then ubuntu, PClinux is WAAAAAAAAAAAAAAAAAAAAAAAAAAAAAY faster for example.
But it depends on what is bundled with the system

---

### Post by crimesaucer on 2007-12-06
> **MONODA said:**
> Yeah I guess you are right (igknighted) for saying that you cant really compare the two. Also I kind of side with you for saying that compiz should be removed but I still think that some effects could be implemented without all the useless stuff. (I mean a lot of the features are really useful).
About the Ububook(macbook) i guess you are right but I searched a bit and found some sites like emperor linux and discovered that they modify and tweak the linux kernel which i dont really like. But the good thing about buying a computer with Ubuntu preinstalled is that you can be sure that everything is going to work and you wont have to pay for windows.

If you don't like the useless plug-ins, then don't use them. Compiz Fusion has certain useful plug-ins that metacity, and xfwm4 don't have, so not everything is just corny effects.

I've tried the newest metacity svn with compositing and it can't even compare to Compiz Fusion (except for less cpu), and even though xfce4 with xfwm4 composting is good, there still are better features in Compiz Fusion. (Shift Switcher, Scale, Resize Info, Windows Rules, Place Windows, Move Windows, Add Helper, Resize Window, Reflection, Expo...)


Plus, you can save your profiles and import/export them... and Compiz Fusion with Emerald is about the easiest way to customize window decorations, make your own, or import/export themes.


As for your boot up problems, there are a number of ways you can make your boot up process faster. This is one way: [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491) 


And this is a Sidux list with different tweaks that make things faster most are the same for ubuntu. Check out the part for Starting services in concurrency mode: [http://sidux.com/PNphpBB2-viewtopic-t-3484-start-0.html](http://sidux.com/PNphpBB2-viewtopic-t-3484-start-0.html)

More lists for boot up and kernel hacks, and tweaking for a faster computer:
[http://ubuntuforums.org/showthread.php?t=189192](http://ubuntuforums.org/showthread.php?t=189192)
[http://feeds.feedburner.com/LinuxMonitor](http://feeds.feedburner.com/LinuxMonitor)
[http://www.linuxmonitor.net/blog/2007/03/ultimate-ubuntu-performance-tweaking.html](http://www.linuxmonitor.net/blog/2007/03/ultimate-ubuntu-performance-tweaking.html)
[http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)
[http://www.santa-li.com/linuxonbb.html](http://www.santa-li.com/linuxonbb.html)
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
[http://www.debianadmin.com/local-dns-cache-for-faster-browsing-on-ubuntu-system.html](http://www.debianadmin.com/local-dns-cache-for-faster-browsing-on-ubuntu-system.html)
[http://www.chinwong.com/index.php/site/article/ubuntu_speed_up_tips/](http://www.chinwong.com/index.php/site/article/ubuntu_speed_up_tips/)
[http://news.softpedia.com/news/Improve-Performance-in-Ubuntu-Edgy-47261.shtml](http://news.softpedia.com/news/Improve-Performance-in-Ubuntu-Edgy-47261.shtml)
[http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/)
[http://ubuntuforums.org/showthread.php?t=181107](http://ubuntuforums.org/showthread.php?t=181107)


... some of these are a little old, so research them, compare them and only change what you are comfortable with changing.


Sleep, Suspend, and Hibernate are issues with Linux distros... but this is LINUX. IT WAS FREE.... IT IS A WORK IN PROGRESS... you should know this from the start. Some things won't work like windows/apple... I use Archlinux and it boots very fast, but it has no laptop sleep, suspend, and hibernate... I could use a custom kernel to test those features but I don't really need my laptop to sleep, suspend, and hibernate because I just shut it off when I'm done with it.

---

### Post by igknighted on 2007-12-06
> **crimesaucer said:**
> If you don't like the useless plug-ins, then don't use them. Compiz Fusion has certain useful plug-ins that metacity, and xfwm4 don't have, so not everything is just corny effects.

Don't put words in my mouth.  I love the compiz plugins, I even have that horribly gaudy aquarium inside the cube on my desktop :).  But compiz is to me a proof of concept.  It explores everything that can be done, and then metacity and kwin make it stable and practical.  There is so much more to a window manager than decorations and effects... it handles everything.  And kwin and metacity have perfected everything, and are adding the bling on top.  Compiz is starting with the focus on hey, we can do <insert effect> (IIRC it started with the cube).  Point being from a stability and consistancy standpoint, metacity and kwin make great platforms to start from.

> **crimesaucer said:**
> I've tried the newest metacity svn with compositing and it can't even compare to Compiz Fusion (except for less cpu), and even though xfce4 with xfwm4 composting is good, there still are better features in Compiz Fusion. (Shift Switcher, Scale, Resize Info, Windows Rules, Place Windows, Move Windows, Add Helper, Resize Window, Reflection, Expo...)

Well, Compiz has been around for a couple years now, and KDE4 isn't due out until january.  And metacity just got compositing in SVN recently.  The effects will be added as the gnome/kde devs find them practical.  I am talking about potential, on how the WM arrangement could/should work in the future.  You can't look at a snapshot today to argue this point.  Besides, if you play with KDE4 for a while you will see that it has many of the things you mention (expo, shift switch, etc.).

> **crimesaucer said:**
> Plus, you can save your profiles and import/export them... and Compiz Fusion with Emerald is about the easiest way to customize window decorations, make your own, or import/export themes.


Emerald is OK, but I would prefer something integrated with the rest of the theme.  Thats whats nice about metacity and kwin... the themes typically come with entire system themes, not just the window borders.  And if it were to be determined that emerald theming types were desirable, I'm sure it would be minimal work to make it possible.

Look, I'm not bashing compiz.  I love it and use it all the time.  But I think it would be better for everyone if compiz did there thing to keep trying stuff out, but the meat and potatoes that everyone could benefit from ought to be ported back the existing, stable WM's.  I think this would advance the software a lot better than having an entire replacement WM.

---

### Post by crimesaucer on 2007-12-06
> **igknighted said:**
> Don't put words in my mouth.  I love the compiz plugins, I even have that horribly gaudy aquarium inside the cube on my desktop :).  But compiz is to me a proof of concept.  It explores everything that can be done, and then metacity and kwin make it stable and practical.  There is so much more to a window manager than decorations and effects... it handles everything.  And kwin and metacity have perfected everything, and are adding the bling on top.  Compiz is starting with the focus on hey, we can do <insert effect> (IIRC it started with the cube).  Point being from a stability and consistancy standpoint, metacity and kwin make great platforms to start from.

actually... I wasn't. I was responding to MONODA's comment bellow:

> **MONODA said:**
> Yeah I guess you are right (igknighted) for saying that you cant really compare the two. Also I kind of side with you for saying that compiz should be removed but I still think that some effects could be implemented without all the **[COLOR="Red"]useless stuff[/COLOR]**. (I mean a lot of the features are really useful).
About the Ububook(macbook) i guess you are right but I searched a bit and found some sites like emperor linux and discovered that they modify and tweak the linux kernel which i dont really like. But the good thing about buying a computer with Ubuntu preinstalled is that you can be sure that everything is going to work and you wont have to pay for windows.





> **igknighted said:**
> Well, Compiz has been around for a couple years now, and KDE4 isn't due out until january.  And metacity just got compositing in SVN recently.  The effects will be added as the gnome/kde devs find them practical.  I am talking about potential, on how the WM arrangement could/should work in the future.  You can't look at a snapshot today to argue this point.  Besides, if you play with KDE4 for a while you will see that it has many of the things you mention (expo, shift switch, etc.).

I've used Beryl since 1.1, and I've never really used metacity much until recently and I was a bit spoiled from the features of xfwm4 and Beryl/Compiz. I've never been on KDE so I never try to speak for something that I know nothing about. 

I also hope that all of the window managers (metacity, xfwm4, compiz fusion... etc.) add the best new features from any window manager out there, including Vista and OS X. Just look at the "Shift Switcher" plug-in, it's very similar to both Vista and OS X,  but it quickly became one of my favorite plug-ins. I wish xfwm4 and metacity had that plug-in (I probably use Compiz Fusion mostly for that plug-in and the ease of theme creation in Emerald). 


> **igknighted said:**
> Emerald is OK, but I would prefer something integrated with the rest of the theme.  Thats whats nice about metacity and kwin... the themes typically come with entire system themes, not just the window borders.  And if it were to be determined that emerald theming types were desirable, I'm sure it would be minimal work to make it possible.

I disagree here. I prefer to be able to be much more in control over buttons, opacity, shade, colors, size, effects, corners, radius, glows...font...etc.

I've made a pixmap theme for xfwm4 and it was difficult and looked like crap. I've also re-modded a metacity theme that looks nice, but it isn't close to how nice I can make a truglass or a vrunner theme (in about 5 minutes). There are so many more options with Emerald that I wish you could use Emerald without Compiz...

> **igknighted said:**
> Look, I'm not bashing compiz.  I love it and use it all the time.  But I think it would be better for everyone if compiz did there thing to keep trying stuff out, but the meat and potatoes that everyone could benefit from ought to be ported back the existing, stable WM's.  I think this would advance the software a lot better than having an entire replacement WM.

I didn't respond to your comment, but I also think Compiz should not be a default feature in any distro (unless Compiz Fusion makes a Linux distro of their own, with all their own features evolving into a complete eye candy version of everything.... panel, browser, desktop settings, file system, embedded drop down terminal...)

I use Archlinux that installs only a base install at first, and then you have to add everything else yourself. That's where I'm at. I got into Linux to try and build things, to add every feature myself if possible. I'm glad there are distros like Dreamlinux for other people that just want everything pre-installed... but I prefer to search the wiki pages and install everything in terminal, or build it from source. It makes my computer experience more fun to be hands on.

As for Ubuntu (which should come installed with more features for people new to Linux), I feel that metacity on gnome, xfwm4 on xfce4, or kwin on kde is the way ubuntu, xubuntu, and kubuntu should be the default WM, and then there should just be an easy option to add all packages in synaptic.

I love Compiz and both the "useful" and the "useless" plug-ins, but I installed the metacity svn with composting the minute I read about it on digg.com yesterday, because I like some things about gnome and metacity that xfce4 doesn't have (sounds, better panel...), and if I could run a lighter metacity (with composting) on gnome, then I wouldn't need to use Compiz on xfce4 to keep my resources low while having a nice "pretty" computer.

But after testing it for an hour or two, I decided it wasn't quite there yet, so I'll wait until later and hope they keep up the good work. I support all open source development and try not to disrespect anyone and their choices.

---

### Post by MONODA on 2007-12-09
Hi I have been using ubuntu since feisty and have come to find that it is the best os out there. The features, customization and applications are amazing. The one thing that I dont like about ubuntu(and its what is making me try a different distro) is that it raelly does not work. I know that it is impossible for all laptops to be supported and that ubuntu is not for everyone but I am not the only one having these problems. My problems since  I installed ubuntu have been: random reboots, unable to shutdown, MANY CRASHES, slow downs over time, unability to change resolution, network problems, sound and video barely ever work, and some more. I really dont want to give up on ubuntu (or linux in general) but I think that Ubuntu really isnt for me. I am thinking of trying out opensuse. If you could suggest other oses then that would be great. Thank yu for your time.

---

### Post by matthewcraig on 2007-12-09
You should be able to diagnose most of these problems through logfiles or whatever, but if you really want hardware that works well with Ubuntu, then you should consider purchasing a computer from a vendor who will stand behind their product.  Everything you mentioned is hardware related, so either you work hard to get Ubuntu working on your hardware or you buy an Ubuntu solution from someone who has already figured out the hardware compatibility issues.  Fact is that your hardware is tested to work on Windows, not Ubuntu.  We need to support hardware vendors who support Ubuntu by purchasing their products and services.

---

### Post by steveneddy on 2007-12-09
> **matthewcraig said:**
>   We need to support hardware vendors who support Ubuntu by purchasing their products and services.

Hear, hear!

[www.system76.com/](www.system76.com/)

---

### Post by Kubunteando on 2007-12-09
Can you post what is your hardware in detail?

Some of us may have some experience with it, and can give useful advices. The experience you get with Linux depends greatly in your hardware.

Other info that will help is:

- are you using 32 bits or 64 bits version?

- what drivers are you using for your hardware?

Another distro to have a look can be PCLinuxOS, but I think that everything depends on your hardware. If there are problems with the drivers, no matter what is your distro you will use. You will have still issues.

I have used several distros, including OpenSUSE, and PCLinuxOS, and I have always come back to Kubuntu.

---

### Post by MONODA on 2007-12-09
Yeah I figured out that HP laptops dont work well with linux. I would buy a computer that is well supported in linux but i just bought this one a few months ago with vista:(:(:(:(:(:(:(. I have heard of a lot of places to buy computers with linux preinstalled such as zareason.com and system76.com but I have never been too sure whether their products were good quality. by the way i am using the 32 bit version of ubuntu gutsy gibbon. I did not install any drivers personally, I was having these problems after a fresh install. I have also heard that ubuntu 7.* have been dissapointing, since i started using ubuntu in feisty I would not know. Is that true. And do you think 8.04 will be a big step forward. thank you.

---

### Post by Kubunteando on 2007-12-09
HP is not a bad option, but it is not top on the list.

I understand your concerns about the online manufacturers.
I am also looking for a Linux laptop, and the sure bet is Dell this far.

If you are using the 32bits version I think the issues come from the kernel itself, so you have to be check around and see if some new kernel version helps on some of them. Check [www.kernel,org](www.kernel,org).

That is a bit time consuming, and some compilation is needed.
And alternative is to try another distro with newer kernel.

For the graphic issues, check if you need to install any drivers.
If you have an nVidia card, sure you need to install the lastest nVidia drivers.

---

### Post by LinuxIsInnovation on 2007-12-09
Download support drivers wherever you get..
If vista runs smoothly, ubuntu should run smooter..
Change your window manager.

---

### Post by MNICY on 2007-12-09
My computer is a Compaq (which is owned by HP) and all the hardware works great with Ubuntu Gutsy 32 and 64 bit editions.

---

### Post by MONODA on 2007-12-11
For some reason I have never been able to completely trust Ubuntu with my computer. I found out that its  because it is VERY unstable (i am pretty sure its only because of hardware compatibility) and every day several apps crash and then the entire system crashes (nautilus and gnome-panel) and i try to run them again using the virtual terminals but it doesnt work. Besides that I am not having any problems at all. Could my problem be because of hardware? leave comments.

---

### Post by aysiu on 2007-12-11
Your hardware is probably functioning properly but not configured properly for Ubuntu. It's probably something to do with your /etc/X11/xorg.conf file. Did you install the right driver for your graphics card, for example?

---

### Post by matthewcraig on 2007-12-11
MONODA, my friend, this is the fifth message thread you started in the last two weeks about your indecision about Ubuntu.  Please reply to another one of your other threads rather than starting another:

[http://ubuntuforums.org/showthread.php?t=621450](http://ubuntuforums.org/showthread.php?t=621450) entitled, "I have had enough of ubuntu's problems!"
[http://ubuntuforums.org/showthread.php?t=622711](http://ubuntuforums.org/showthread.php?t=622711) entitled, "What ubuntu needs to become more popluar"
[http://ubuntuforums.org/showthread.php?t=625932](http://ubuntuforums.org/showthread.php?t=625932) entitled, "Not sure if I should go 100% Ubuntu"
[http://ubuntuforums.org/showthread.php?t=633272](http://ubuntuforums.org/showthread.php?t=633272) entitled, "Ubuntu just need a bit more to go to be the best"

One could get the idea that you're trolling, since in each new thread you complain about Ubuntu.

---

### Post by MONODA on 2007-12-11
Im pretty sure my drivers are working properly because I did not manually install any, and I did not edit the xorg.config file at all. All I did to set up Ubuntu was installing from the live cd. By the way I have had the same problems in every install I have had(I have reinstalled gutsy about 3 times and I am currently using a new installation). Anyway sorry about that matthewcraig I'll be sure to do that next time.

---

### Post by stchman on 2007-12-11
> **MONODA said:**
> For some reason I have never been able to completely trust Ubuntu with my computer. I found out that its  because it is VERY unstable (i am pretty sure its only because of hardware compatibility) and every day several apps crash and then the entire system crashes (nautilus and gnome-panel) and i try to run them again using the virtual terminals but it doesnt work. Besides that I am not having any problems at all. Could my problem be because of hardware? leave comments.

I have Ubuntu running on 2 computers and 1 laptop.  I would say Ubuntu is far more stable than Windows.  I use Ubuntu about 99% of the time.  I only use Windows for games and some M$ office stuff that OO does not do.

---

### Post by aysiu on 2007-12-11
> **MONODA said:**
> Im pretty sure my drivers are working properly because I did not manually install any, and I did not edit the xorg.config file at all. All I did to set up Ubuntu was installing from the live cd. By the way I have had the same problems in every install I have had(I have reinstalled gutsy about 3 times and I am currently using a new installation). Anyway sorry about that matthewcraig I'll be sure to do that next time.
Actually, that might be the problem.

If you have an Nvidia or ATI graphics card, you may have to manually install the driver.

---

### Post by stchman on 2007-12-11
> **matthewcraig said:**
> MONODA, my friend, this is the fifth message thread you started in the last two weeks about your indecision about Ubuntu.  Please reply to another one of your other threads rather than starting another:

[http://ubuntuforums.org/showthread.php?t=621450](http://ubuntuforums.org/showthread.php?t=621450) entitled, "I have had enough of ubuntu's problems!"
[http://ubuntuforums.org/showthread.php?t=622711](http://ubuntuforums.org/showthread.php?t=622711) entitled, "What ubuntu needs to become more popluar"
[http://ubuntuforums.org/showthread.php?t=625932](http://ubuntuforums.org/showthread.php?t=625932) entitled, "Not sure if I should go 100% Ubuntu"
[http://ubuntuforums.org/showthread.php?t=633272](http://ubuntuforums.org/showthread.php?t=633272) entitled, "Ubuntu just need a bit more to go to be the best"

One could get the idea that you're trolling, since in each new thread you complain about Ubuntu.

I don't think MONODA can make his mind up.  One minute he cannot stand Ubuntu and is going back to Windows and the next he is praising it.

---

### Post by aysiu on 2007-12-11
> **stchman said:**
> I don't think MONODA can make his mind up.  One minute he cannot stand Ubuntu and is going back to Windows and the next he is praising it.
I've merged a bunch of those threads together.

---

### Post by MONODA on 2007-12-11
Well Yeah I really like it much more than windows but I get really mad when the ENTIRE system crashes. Anyway how can I manually install the driver.  I would really appreciate any help. Thank you

---

### Post by aysiu on 2007-12-11
> **MONODA said:**
> Well Yeah I really like it much more than windows but I get really mad when the ENTIRE system crashes. Anyway how can I manually install the driver.  I would really appreciate any help. Thank you
Try this:
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

---

### Post by MONODA on 2007-12-11
I have already done that. What else could be my problem?

---

### Post by matthewcraig on 2007-12-11
Why do you not start a thread in the technical support forums, that specifically asks for technical help, monada ?  You're switching back and forth from talking about your hardware to software to windows to other topics, and it's taking up a lot of time.  You've generated over 100 responses asking for help with your computer.

My advice would be for you to purchase a computer with Ubuntu pre-installed, so you know it will all work with the Ubuntu operating system.

---

