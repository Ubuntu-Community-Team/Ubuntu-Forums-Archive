---
title: "Run Atlantica Online in Linux?"
date: 2009-09-03
forum: Wine
---

### Post by Kdar on 2009-09-03
Have anyone tried to run Atlantica Online in Linux?
I used to play this game few month ago on my Windows PC, wondering if I can get it running on my Ubuntu on Laptop.

---

### Post by Bölvaður on 2009-09-03
According to wikipedia this game is windows only game so look for the WINE section of this forum for any information about running windows only games on linux, they are the experts, this part of the forum is only for native linux games.

---

### Post by 569874123 on 2009-09-03
> **Bölvaður said:**
>  this part of the forum is only for native linux games.
Really? I see people asking about every emulator except wine or every emulator that can run without wine and it doesn't get moved.
Examples: Dosbox, ScummVM, PCSX2, Gen, SNES etc...

---

### Post by Bölvaður on 2009-09-03
> **569874123 said:**
> Really? I see people asking about every emulator except wine or every emulator that can run without wine and it doesn't get moved.
Examples: Dosbox, ScummVM, PCSX2, Gen, SNES etc...

emulators are native.

---

### Post by 569874123 on 2009-09-03
While it is true that wine is not a emulator. It is a _**native**_ compatibility layer.

---

### Post by Bölvaður on 2009-09-03
> **569874123 said:**
> While it is true that wine is not a emulator. It is a _**native**_ compatibility layer.
yes but the question wasnt about installing wine (which should be posted in the *absolute beginners talk* subforum) but about installing a windows game, which is not native.

The thread named [64-bit Genesis emulator]("http://ubuntuforums.org/showthread.php?t=1254730") is about the emulator, not how to get some game to work in it. That is the difference.

btw you did good in the teewords session if I can guess which one you were.

---

### Post by 569874123 on 2009-09-03
> **Bölvaður said:**
> yes but the question wasnt about installing wine (which should be posted in the *absolute beginners talk* subforum) but about installing a windows game, which is not native.

The thread named [64-bit Genesis emulator]("http://ubuntuforums.org/showthread.php?t=1254730") is about the emulator, not how to get some game to work in it. That is the difference.

btw you did good in the teewords session if I can guess which one you were.
Thanks for the clarification, but if someone where to ask a question regarding a game in any of the emulators mentioned, where should it be asked within the ubuntuforums?
PS: I didn't play teeworlds, only played Urt and Spring on UGN.
Off-topic:I hear that you are pro in fps ;P.

---

### Post by hikaricore on 2009-09-03
WINE posts belong in the WINE forum specifically and as has been mentioned WINE is not and emulator.
Every so often a new game crazy comes along and idiots flood the forum with questions about it, such was the case with Halo and World of Warcraft.
In an attempt to clean up the gaming forum the WINE forum was created and new rules were put in place to keep this area reserved for native titles.

I hope this explains things a little more clearly.

---

### Post by kenji_03 on 2009-09-22
Apparently Atlantica online [works with Wine]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=17754"), but on a different linux distribution : [Arch Linux (rolling release)]("http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=distribution&iId=526&sAction=view&sTitle=View+Distribution") : I personally could not get it working in Ubuntu 9.04.

I got it installed just fine (had to use a full download, the quick-patcher didn't work) and the game updated through the official game patcher (loading screen), but I think I need directX or something as all I get are odd blocks and distorted characters.

---

### Post by RealG187 on 2009-11-16
[http://ubuntuforums.org/showthread.php?p=7991662](http://ubuntuforums.org/showthread.php?p=7991662)

I made a thread there too

---

### Post by AllRadioisDead on 2009-11-17
I can get the game to launch, but the title screen is messed up and it won't let me connect. The title screen might have something to do with my ATI HD 4850 card having poor drivers.

---

### Post by RealG187 on 2009-11-17
How did you get it to launch? Wine or Virtualbox?

I have had the same problem as you in Vbox, there are polygons on the background in the login screen and it's really slow.

---

### Post by AllRadioisDead on 2009-11-17
I was using wine. My best advice would be to install in windows, update fully, and then copy over your folder to wine and see if it runs.

---

### Post by RealG187 on 2009-11-18
I tried the copied files and wine doesn't work :(

---

### Post by mo3head on 2009-11-24
[http://g33kb0x.blogspot.com/2009/11/installing-vmwarebundle-on-ubuntu.html]("http://g33kb0x.blogspot.com/2009/11/installing-vmwarebundle-on-ubuntu.html")
Good luck!

---

### Post by RealG187 on 2009-11-25
Have you tested that or are you just spamming your blog?

---

### Post by mo3head on 2009-11-25
Well i wrote the tutorial, i made the pictures, wtf else you want? a video?

---

### Post by RealG187 on 2009-11-25
I didn't look, just seen you have few posts and posting an external link so I thought you might have been a spammer. I'll take a look.

I don't wanna try something unless I know it'll work.

EDIT: Seems good. I see you actually tested it with AO and not just assumed it would work. [http://operation420.net/forum/viewtopic.php?f=62&t=1103&p=4096#p4096](http://operation420.net/forum/viewtopic.php?f=62&t=1103&p=4096#p4096)

---

### Post by mo3head on 2009-11-25
Yea a 1poster posting an external link is kinda suspicious i guess:P
I just googled for a tutorial or something for atlantica online on ubuntu but for my disappointment i could only find people having problems running it :(
For myself it didnt even start with wine nor with cedega, so ye i tried vmware :)
Actually Atlantica online was one of the main reasons i even installed vmware.
I was kinda suprised though about the awsome d3d9 support of vmware :O
Its running without any flaws EXCEPT the yellow arrow you get when you put autorun on, for some reason its red lol.

---

### Post by AllRadioisDead on 2009-11-26
What kind of problems were you having trying to run it in wine?
What kind of GPU are you running?

---

### Post by mo3head on 2009-11-26
Atlantica didnt start at all with wine/wine1.2 nor cedega.
The progess was running but nothing appeared..
Graphiccard:Zotac geforce 9600GT, single GPU,512mb GDDR3

---

### Post by RealG187 on 2009-11-26
> **mo3head said:**
> Yea a 1poster posting an external link is kinda suspicious i guess:P
I just googled for a tutorial or something for atlantica online on ubuntu but for my disappointment i could only find people having problems running it :(
For myself it didnt even start with wine nor with cedega, so ye i tried vmware :)
Actually Atlantica online was one of the main reasons i even installed vmware.
I was kinda suprised though about the awsome d3d9 support of vmware :O
Its running without any flaws EXCEPT the yellow arrow you get when you put autorun on, for some reason its red lol.I didn't even know VM Ware had the graphics stiuff, I knew VirtualBox did but it doesn't work. In VM Ware (without the stuff) I would get error messages, Virtual Box didn't give the messages but the game was garbled.

---

### Post by RealG187 on 2009-12-07
Does this work with VM Ware server?

---

### Post by AllRadioisDead on 2009-12-07
> **mo3head said:**
> Atlantica didnt start at all with wine/wine1.2 nor cedega.
The progess was running but nothing appeared..
Graphiccard:Zotac geforce 9600GT, single GPU,512mb GDDR3
 Post terminal output.

---

### Post by AllRadioisDead on 2010-01-25
Nevermind, game works great.

---

### Post by KainPen on 2010-01-27
ihermit
Did you use VMware to get Atlantica running ??? or Wine?
New here and to the OS. I like what i see so far from it. There a few app I need to either find replacements for or see if they work in wine or some other way. 
 
Then I can take windows off my system all together. Atlantica is one of them.
Any suggestions on Anti-virus or malware prevention apps for Ubuntu. I under stand it a pretty virus free OS but will still like to have some protection.

---

### Post by AllRadioisDead on 2010-01-27
> **KainPen said:**
> ihermit
Did you use VMware to get Atlantica running ??? or Wine?
New here and to the OS. I like what i see so far from it. There a few app I need to either find replacements for or see if they work in wine or some other way. 
 
Then I can take windows off my system all together. Atlantica is one of them.
Any suggestions on Anti-virus or malware prevention apps for Ubuntu. I under stand it a pretty virus free OS but will still like to have some protection.
Game works great in wine. There's no real point to antivirus on linux, but if you still feel the need, there's [clamav]("http://www.clamav.net/").

---

### Post by KainPen on 2010-02-01
hey ihermit, tired to run atlantica the other day thru wine. and it fails to authecate with server. Can you send me walk thru on how you got it to work???  You do install thru wine or did you try to run if from windows directory?

---

### Post by AllRadioisDead on 2010-02-01
> **KainPen said:**
> hey ihermit, tired to run atlantica the other day thru wine. and it fails to authecate with server. Can you send me walk thru on how you got it to work???  You do install thru wine or did you try to run if from windows directory?
Yeah, that happened to me as well. Solved it by installing ie6 with winetricks. If you still have trouble after doing that, reinstall ie6 again and it should reconfigure everything again and work. I noticed the perfect world launcher was having the same problem.

---

### Post by KainPen on 2010-02-08
that did not work either.  you have anything else installed from Winetricks??? Direct X or .net packages???

---

### Post by RealG187 on 2010-02-11
> **KainPen said:**
> that did not work either.  you have anything else installed from Winetricks??? Direct X or .net packages???I don't think you are supposed to install Direct X in Wine, it has it's own direct X.

---

### Post by okuzster on 2010-03-01
it gives these errors before running:


failed to load shader library!
failed to register shader fx libraries!


and it runs like that:


[IMG]http://img.fotoambar.com/img/00000/f9f947dc859333156c11319e3c79c820.png[/IMG]



anyone can help me to fix it? thanks

---

### Post by AllRadioisDead on 2010-03-01
Looks to me like a problem with your graphics card, what kind of card are you running?

---

### Post by okuzster on 2010-03-01
it's onboard videocard, and my mainboard is asus m3a78-cm

---

### Post by RealG187 on 2010-03-03
Well this is retarded, it says my computer doens't have a 3D Graphics system supported by VM Ware workstation.

The people that make this game need to turn off all the unnecessary Graphics and/or need to learn how to program properly so the game works with Wine...

---

### Post by KainPen on 2010-03-10
i finaly got it to work but a lot of the textures just appares as white or blank like they are missing. From the fourms for the game i find a lot of people with G-force 6 and 7 series cards are haveing a ton of graphical error and system crashes. the game it sell if getting load with more and more bugs every patch. I have G-force 7600 or 900 don't remember the number GTO model. and i expeince a lot of these error when i run the game in windows. but when i run it in ubuntu the game is stable no crashes at all but as i said a ton of textures just appares as if they are blank. go figure. I am guessing bad programing and corrupt textures is the main problem in the game.  the game customer support is lack also. I my self just got screwed on 3 quest after the most recent patch took away 3 days worth of progress on them. might be time to move on to another free mmo. any of you guys try doing a private RO server in unbuntu?

---

### Post by AllRadioisDead on 2010-03-11
> **RealG187 said:**
> Well this is retarded, it says my computer doens't have a 3D Graphics system supported by VM Ware workstation.

The people that make this game need to turn off all the unnecessary Graphics and/or need to learn how to program properly so the game works with Wine...
Yes, the developers should cater to your needs.
The game isn't meant to run in a virtual machine.
> **KainPen said:**
> i finaly got it to work but a lot of the textures just appares as white or blank like they are missing. From the fourms for the game i find a lot of people with G-force 6 and 7 series cards are haveing a ton of graphical error and system crashes. the game it sell if getting load with more and more bugs every patch. I have G-force 7600 or 900 don't remember the number GTO model. and i expeince a lot of these error when i run the game in windows. but when i run it in ubuntu the game is stable no crashes at all but as i said a ton of textures just appares as if they are blank. go figure. I am guessing bad programing and corrupt textures is the main problem in the game.  the game customer support is lack also. I my self just got screwed on 3 quest after the most recent patch took away 3 days worth of progress on them. might be time to move on to another free mmo. any of you guys try doing a private RO server in unbuntu?
What does this have to do with wine?
> **okuzster said:**
> it's onboard videocard, and my mainboard is asus m3a78-cm
You'll need a dedicated video card to run a game like this in wine.

---

### Post by RealG187 on 2010-03-11
I can run the game in Windows just fine on my computer, do you think if I get a better graphics driver for Ubuntu it would work in VMWare?

---

### Post by AllRadioisDead on 2010-03-12
> **RealG187 said:**
> I can run the game in Windows just fine on my computer, do you think if I get a better graphics driver for Ubuntu it would work in VMWare?
 Once again...
The game is not meant to be played through a virtual machine. The 3D performance is nowhere near where it would be if you were running it on a real machine. Wine is your best bet. Unless you mean that you got it running in VMware in Windows, in which case it would simply be because of the weaker graphics drivers available for linux.

---

### Post by KainPen on 2010-03-15
> **ihermit said:**
> Yes, the developers should cater to your needs.
The game isn't meant to run in a virtual machine.
 
What does this have to do with wine?
 
You'll need a dedicated video card to run a game like this in wine.
 
It has to do with the fact the game is programed poorly and in wine or not there is going to be issuses with it.  the fact that the game runs smoothly and does not crash in wine. means wine is fine, but the game has issuse it self.  it jsut information for other that want to get the game running in wine.  Also to let people know that have those cards that it could be the video card that is an issuse also. 
 
I asked about RO private server to see if any one got that to run on wine. I see in Wine data base that the game has been tested and is running perfect. I was wondering about private sever so maybe i could run one for me and my friend when we have lan parties and what not.

---

### Post by AllRadioisDead on 2010-03-15
> **KainPen said:**
> It has to do with the fact the game is programed poorly and in wine or not there is going to be issuses with it. the fact that the game runs smoothly and does not crash in wine. means wine is fine, but the game has issuse it self. it jsut information for other that want to get the game running in wine. Also to let people know that have those cards that it could be the video card that is an issuse also. 
 
I asked about RO private server to see if any one got that to run on wine. I see in Wine data base that the game has been tested and is running perfect. I was wondering about private sever so maybe i could run one for me and my friend when we have lan parties and what not.
 What are you talking about? Wine is far from perfect. There's reason's why a lot of programs don't run correctly (or at all), and it's not because they weren't properly programmed. Last I checked, unless you work for Ndoors, you don't have access to the games source code anyways. The game runs fine on Windows (You know, the platform it was designed to run on) and it should be no surprise that a game like this doesn't run properly in wine. There are lots of newer games that can run perfectly (like WOW) and others that don't run so well at all (like Age of Conan for example).

---

### Post by KainPen on 2010-03-19
that just it the game does not run fine on windows. it crashes a lot for a lot of people read fourm at atlanitica website. if just funny that the game run completely stable under wine. There are graphical errors in wine but the game does not crash. but not the OS it was made to run on. the graphics are fine but the game crash. that in it self should tell you something about the programing. hell it could be wines in perfections that cause the game to run stable.

---

### Post by AllRadioisDead on 2010-03-19
> **KainPen said:**
> that just it the game does not run fine on windows. it crashes a lot for a lot of people read fourm at atlanitica website. if just funny that the game run completely stable under wine. There are graphical errors in wine but the game does not crash. but not the OS it was made to run on. the graphics are fine but the game crash. that in it self should tell you something about the programing. hell it could be wines in perfections that cause the game to run stable.
 Just because the game has bugs does not mean it hasn't been programmed properly, it means it has bugs. All games have bugs, visit the forums for any other MMO out there and you'll find people complaining about things. I haven't had the game crash under windows and it hasn't crashed under wine. It does not perform any better under wine than under windows, if anything there should be a performance drop due to the available graphics drivers.

---

### Post by RealG187 on 2010-03-19
So I am not the only one who has this game crash all the time? The devs say the game is only for Windows, but it sucks on Windows...

---

### Post by AllRadioisDead on 2010-03-19
> **RealG187 said:**
> So I am not the only one who has this game crash all the time? The devs say the game is only for Windows, but it sucks on Windows...
 How does it suck on Windows?

---

### Post by RealG187 on 2010-03-22
Because it crashes all the time

---

### Post by AllRadioisDead on 2010-03-23
What kind of hardware are you running it on? It runs fine for me.

---

### Post by KainPen on 2010-03-23
> **RealG187 said:**
> So I am not the only one who has this game crash all the time? The devs say the game is only for Windows, but it sucks on Windows...
 
[http://atlantica.ndoorsgames.com/center/ATForum/forums/thread-view.asp?tid=35234&posts=5&start=1](http://atlantica.ndoorsgames.com/center/ATForum/forums/thread-view.asp?tid=35234&posts=5&start=1)
 
[http://atlantica.ndoorsgames.com/center/ATForum/forums/thread-view.asp?tid=36209&posts=4&start=1](http://atlantica.ndoorsgames.com/center/ATForum/forums/thread-view.asp?tid=36209&posts=4&start=1)
 
[http://atlantica.ndoorsgames.com/center/ATForum/forums/thread-view.asp?tid=4961&posts=13&start=1](http://atlantica.ndoorsgames.com/center/ATForum/forums/thread-view.asp?tid=4961&posts=13&start=1)
 
[http://atlantica.ndoorsgames.com/center/ATForum/forums/thread-view.asp?tid=36076&posts=2&start=1](http://atlantica.ndoorsgames.com/center/ATForum/forums/thread-view.asp?tid=36076&posts=2&start=1)
 
[http://atlantica.ndoorsgames.com/center/ATForum/forums/thread-view.asp?tid=36678&posts=19&start=1](http://atlantica.ndoorsgames.com/center/ATForum/forums/thread-view.asp?tid=36678&posts=19&start=1)
 
 
just a few fourm post of bugs, you are not alone. all of these are on windows. i have not exprinced any of these under wine or any crashes
 
the last one is a huge graphical bug on windows. hmmmmm i think it more proof supporting my theroy of something wrong with the textures.
 
[http://en.wikipedia.org/wiki/Software_bug](http://en.wikipedia.org/wiki/Software_bug) = human error in programing aka bad programing.
 
two more for bonus
[http://atlantica.ndoorsgames.com/center/ATForum/forums/thread-view.asp?tid=35868&posts=51&highlight=black%20lines&highlightmode=1#M349733]("http://atlantica.ndoorsgames.com/center/ATForum/forums/thread-view.asp?tid=35868&posts=51&highlight=black%20lines&highlightmode=1#M349733")
 
[http://atlantica.ndoorsgames.com/center/ATForum/forums/thread-view.asp?tid=36310&posts=25&highlight=black%20lines&highlightmode=1#M358251](http://atlantica.ndoorsgames.com/center/ATForum/forums/thread-view.asp?tid=36310&posts=25&highlight=black%20lines&highlightmode=1#M358251)
 
not the recommend system req here [http://atlantica.ndoorsgames.com/center/pds/pds.asp](http://atlantica.ndoorsgames.com/center/pds/pds.asp)
Gforce 7 series hmmm people with 7 and below have problems and crashes. 
 
run in wine no more crash just messed up grahics

---

### Post by RealG187 on 2010-03-23
Does this game even work on Wine?

As far as I know the only way to sucessfully get it running on Windows: [http://operation420.net/forum/viewtopic.php?f=62&t=1103](http://operation420.net/forum/viewtopic.php?f=62&t=1103)

I have my HP Laptop and it runs AO fine in Windows (except all the crashing) but in VMWare 3D Acceleration doesn't work. Would it be because Ubuntu isn't using a driver that supports it but Windows is? VMWare makes it sound like my hardware doens't support it, but in Windows it does...

I think it's an Intel GMA 950, is there a way to find out in Ubuntu, In Windows I use Device Manager, but I am not in Windows...

---

### Post by _h_ on 2010-03-23
> **RealG187 said:**
> I have my HP Laptop and it runs AO fine in Windows (except all the crashing) but in VMWare 3D Acceleration doesn't work. Would it be because Ubuntu isn't using a driver that supports it but Windows is? VMWare makes it sound like my hardware doens't support it, but in Windows it does...

I think it's an Intel GMA 950, is there a way to find out in Ubuntu, In Windows I use Device Manager, but I am not in Windows...

Virtual software doesn't have 3D support, if very little support for it.

Also you can find out by running this command in terminal:

```
lspci
```

---

### Post by AllRadioisDead on 2010-03-23
> **RealG187 said:**
> Does this game even work on Wine?

As far as I know the only way to sucessfully get it running on Windows: [http://operation420.net/forum/viewtopic.php?f=62&t=1103](http://operation420.net/forum/viewtopic.php?f=62&t=1103)

I have my HP Laptop and it runs AO fine in Windows (except all the crashing) but in VMWare 3D Acceleration doesn't work. Would it be because Ubuntu isn't using a driver that supports it but Windows is? VMWare makes it sound like my hardware doens't support it, but in Windows it does...

I think it's an Intel GMA 950, is there a way to find out in Ubuntu, In Windows I use Device Manager, but I am not in Windows...

The game runs fine in Wine.
Also, you're never going to get it to run on a GMA950, sorry to break it to you. I'm surprised it ran at all, even in Windows and that's probably why it crashed. Most 3D games require a dedicated video card of some sort.

---

### Post by RealG187 on 2010-03-24
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

That's stupid that the game has so much unneeded video card requirements. That's what I hate about PC gaming, how video cards can be so expensive and have their own processors. Graphics aren't everything.

---

### Post by _h_ on 2010-03-24
So I decided to try this game, and the downloader doesn't work for me in Wine 1.1.41 at all. It just sits there and eats my CPU alive.

---

### Post by AllRadioisDead on 2010-03-25
> **RealG187 said:**
> 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

That's stupid that the game has so much unneeded video card requirements. That's what I hate about PC gaming, how video cards can be so expensive and have their own processors. Graphics aren't everything.
The game doesn't have unneeded video requirements, you just don't have a capable card.
They are outlined on the downloads page, and by the sounds of it you don't meet the recommended hardware requirements anyways. The GMA 950 card isn't meant for gaming on, so I don't see why you criticize the game developers.
```
Category	Recommened Requirements
OS	Windows XP/2000/Vista
CPU	Pentium 4 @ 2GHz or better
RAM	1GB or more
Video	GeForce 7600GS/ATI HD3450, 256MB or better(Graphic card supporting vertex pixel shader)
Hard Drive	20GB or more
Etc. Direct 9.0 or better
```


> **_h_ said:**
> So I decided to try this game, and the downloader doesn't work for me in Wine 1.1.41 at all. It just sits there and eats my CPU alive.
Try and find a full installer for the game, even if it's an older version and upgrade through the launcher, that should work.

---

### Post by KainPen on 2010-03-25
> **_h_ said:**
> So I decided to try this game, and the downloader doesn't work for me in Wine 1.1.41 at all. It just sits there and eats my CPU alive.
 I could not get downloader to work either i had to install on windows part. and then copy to wine folder.

---

### Post by _h_ on 2010-03-25
> **ihermit said:**
> Try and find a full installer for the game, even if it's an older version and upgrade through the launcher, that should work.

Found the client off GamersHell, 2.16GB but is downloading painfully slow. :(

> **KainPen said:**
> I could not get downloader to work either i had to install on windows part. and then copy to wine folder.

I don't have Windows on my laptop anymore, so I can't do this. :P

---

### Post by RealG187 on 2010-03-26
> **ihermit said:**
> The game doesn't have unneeded video requirements, you just don't have a capable card.My card is plenty capable I can do everything just fine on my laptop but play this stupid game. They really didn't need to make it have unnecessary graphical effects that most people just turn off anyways...

And if the games runs in Windows there is no reason why it shouldn't run in Linux...

---

### Post by KainPen on 2010-04-15
lastest patch to the game killed my wine. I can no longer play the game in wine.

---

### Post by fain on 2010-05-05
> **KainPen said:**
> lastest patch to the game killed my wine. I can no longer play the game in wine.

I am running it fine still on wine-1.1.43. Maybe try deleting your .wine folder and reconfigure it.

---

### Post by RealG187 on 2010-05-07
I tried on Wine not to long ago and the graphics were garbled... Can't remmeber what Wine I have, but I have Ubuntu 9.04 and my wine was updated twice from what I had from a while ago and I know the Wine I have is past 1.x and not 0.9.x...

---

### Post by AllRadioisDead on 2010-05-07
> **RealG187 said:**
> I tried on Wine not to long ago and the graphics were garbled... Can't remmeber what Wine I have, but I have Ubuntu 9.04 and my wine was updated twice from what I had from a while ago and I know the Wine I have is past 1.x and not 0.9.x...
 You don't have a graphics card, I doubt the game will run for you anyways.

---

### Post by KainPen on 2010-05-14
> **fain said:**
> I am running it fine still on wine-1.1.43. Maybe try deleting your .wine folder and reconfigure it.
 
maybe something change in the last 4-6 patches since i posted that. i had two this week alone.

---

