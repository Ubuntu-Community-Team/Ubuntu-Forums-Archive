---
title: "The more I use Windows, the more I hate it."
date: 2007-06-23
forum: The Cafe
---

### Post by slavik on 2007-06-23
So, my main 40GB drive is partition into 2 partitions, 1 being Windows XP install, the other being for Apps and stuff (in case I had to reinstall, apps were still there). Well, about a week ago, Windows somehow managed to screw up the MFT (Master File Table) of the second partition. Not only that, it also destroyed the backup (don't ask, I don't know, I don't have the source code). Today, the actual install partition went nuts ... now some DLLs required by the kernel were missing. This is what Linus meant when he told Tenenbaum that MINIX has problems with its brain.

From work experience (as a tech in my college library):
One day, I get a call about a computer taking too long to boot up (40 minutes has passed since it was turned ona t that point). So, I go over to have a look. All I see is a blue background with the mouse pointer (right before the welcome screen). So, I reboot the system and the BIOS in the system tells me that there is a problem with the hard drive (reported by SMART). Had I not had a Knoppix DVD on my desk, getting files of this machine would've been a hassle (I would have to use another system and mount this drive secondary). What I did was boot into Knoppix, then using a quick perl script to copy everything off the offending drive onto a windows share on a computer next to me (I would have setup an ftp server on my system real quick if I had to).
1:0 (Linux vs. Windows)

Another day, we are told to do windows updates on something like 20 computers, so we reboot them with hdd protection off (the kind that rolls back changes) and into the administrative account. Then we go to the update web site and scan for updates and install them. This is 20 computers, during peak usage ... scanning took longer than the actual download/install. With Linux this process can be made noninteractive almost 100%. Thankfully, in the windows case, we had a WSUS server and then (almost by the closing time) we were able to pull updates from that instead of microsoft (there is also no way of telling windows where to look for updates).
2:0

I am pretty sure there are other situations I can come up with ... ooh, VBScript using ADSI ...

VBScript by itself is a horrible language.

Set stuff = CreateObject(~~~)
stuff2 = "hello"

when you assign objects, you ahve to use 'set', otherwise you don't use it (set x = 5 is a syntax error).

There are ADSI providers which allow you to do enat things (like get listings from active directory and check which group the user is in or some such), the problem is this:

Set objStuff = GetObject("WinNT://" & systemname & "/administrators") 'this actually returns a collection of objects (happens to be users in the administrators group)

the only way to iterate through them is:
for each objiterator in objStuff
'do stuff
next

because the collection is not an array or anything decent ... and you have to manually convert it to an array.
This is not to mention the lack of documentation of these ADSI providers (which can do some very powerful things). I've been through MSDN at least 10 times and some documentation contradicts what the book says or they have information which is in 1 place and not other (book or site).

Having an editor for VBScript doesn't help because most can't recognise the type of object being returned since it is called by name (which is a string and not a token/keyword by itself) ...

---

### Post by karellen on 2007-06-23
ok

---

### Post by djchandler on 2007-06-23
I just tried a motherboard swap on my wife's desktop that runs XP Home. **It was a nightmare, but it was at least *partially* my fault.**

Since I build our computers, MS considers me to be an OEM as well as an end-user. I was concerned about the cheap hardware I was using that I picked up in the returns area of a chain store who shall remain nameless. It wasn't a great MB to begin with, but it also had some damage to the second SATA port. Since I was going to use a PATA 160 GB HDD I had on hand as well as reuse some of her other parts, I wanted to assemble the box to test the hardware before installing an OS. I bought some cheap ram as well, and it needed tweaking too. I used her existing case because it is kind of nice with front USB ports, mic and headphone jacks, etc, without it looking like a spaceship. When I was satisfied with the hardware setup, at the last minute I thought I should check to make sure my EULA for the OEM copy of XP Home would still be legal. After my research, I determined everything was fine, so I tried to copy the old hdd to the 160gb hdd using Western Digital's software CD which boots DR DOS, and then lets you do all sorts of great things so you won't lose software settings etc. The BIOS was set to boot floppy first, then CD, then hdd0, which was the "new" 160 gb drive.

The old 80 gb drive was in side the box as slave on IDE0. I could not believe what happened next. Makes you wonder how underhanded MS really is. The GD 80 gb, not even listed in the BIOS boot order, was booting into Windows XP Home. No matter what I tried, that slave drive kept trying to boot. Thinking about it after the fact, I should have connected it through the USB port after booting the WD CD. I could have tried that, but I wasn't sure DR DOS would see it.


[B]This is the part that is important
[/B]
To make this long-winded story short, I called the MS 1-800-RULEGAL hotline to see if I was in fact somehow violating the EULA. Well, if you research this, some will say I was in violation, and some will say I was not. There is a provision in the OEM EULA that allows a mb swap, but some say it must be the exact same model mb. That ABIT KT7A has probably been out of production at least 5 years, so my chances of getting one were slim to say the least. Plus my motive was to upgrade her computer if her IT department decides to roll out Vista with Office 2007. She's a MOUS, or Microsoft Office User Specialist, certified by MS. She doesn't work in IT, but they call on her quite a lot to help other employees with their problems with MS Office apps. So that was why I was doing this.

Sorry for the digression. Anyway, the young lady at MS I was speaking to was no help whatsoever. She wouldn't tell if I was legal or not, and became confused about the problem I was having. She said she would have a tech contact me, because I was somewhat accusatory of MS's methods, thinking they had installed a rootkit or something, and maybe had screwed up the Master Boot Record while commandeering my hardware. I became somewhat irate with her attitude, and complete lack of understanding about what I was trying to ask, that was what I was doing in compliance with the EULA or not. Even though I wasn't raising my voice or using foul language in any way, she just hung up on me. Needless to say, I never got the tech contact, because she was so inept from the start she failed to record my email address properly. And that was before I became upset with her.

**End of important part**

So guess what. My wife's computer went back to her old hardware configuration, because she gets cranky when she can't get her e-mail at home. That new MB, AMD Athlon 64, and ram and all the rest of my goodies just replaced my old Ubuntu box. Right now I'm hooked up to our living room flat screen HDTV running Feisty. I'm wired into the home network, and I've been copying HDTV programs I have previously recorded from my other computer(s) and can now watch them on this set-up full screen. VLC has never failed to play anything I've thrown at it. If you don't have VLC, give it a try. It's in the default Synaptic repository database, and it's a great little program.

I called back customer service at MS today, and actually talked to someone very nice. But I also told her she just lost a Vista sale too. That was what I was eventually intending to do with my wife's computer, but I don't know if that will happen now or not. I gave my wife an account on this Ubuntu box in the living room, and she has a collection of digitally recorded programs about her hobby, I'll get her converted. It's only a matter of time, and further development of Wine, which improves with age.

I put an older Pinnacle TV tuner card in the Ubuntu box, and I'm going to start using MythTV. I can't wait to get that going. Eventually when Snapstream  gets to the point of asking for more money for an upgrade for Beyond TV , I'll move my HDTV/ATSC tuner out of my XP Pro box over to this Ubuntu box. The rendering of the HDTV programs I've previously recorded look great when played back with VLC.

Hey, all you people like I used to be running Ubuntu on older spare hardware or just toying around with it on a dual boot system. Get rid of those old P4s and Athlon XPs. It's time to really use this OS. It's mature enough to take on the big boys, and able to do just about anything they can do. If we could only get Adobe to consider porting their software to Open Source platforms. I would pay for their products just like I'm paying for them now to use under Windows. I really need the tools Adobe has to offer. They could do a lot of business with Linux users.

Any, the final point is, get something going to push the envelope of Linux development. It's time to tell Jobs, Ballmer, and Gates we don't need them anymore! ;)

---

### Post by microsoft92sucks on 2007-06-29
I'm not reading all that but I agree every time I use Windows (which is as little as possible) I get mad at the Computer I really hate that OS not because the Evil company behind it (Microsoft) but because it suck. It doesn't even compare to Linux yet it's much more comely used. Its BULL if you ask me.

---

### Post by Zzl1xndd on 2007-06-29
Welcome to the club, the real trick is finding like minded people I know a few but sitting around people that have only ever used windows is enough to drive you a little more nuts.

---

### Post by cunawarit on 2007-06-29
I love XP!

---

### Post by nocturn on 2007-06-29
Well, I actually didn't use windows from 2002-2004 because my job was based on Unix (solaris with Gnome desktops) and I do not run windows at home (windows-free since 1999).

Halfway in 2004, I switched jobs, getting a windows XP desktop computer.
In the last half year, I was actually thinking that windows wasn't so bad (memories of crashes and problems where fading).

So, I started my new job and one of the first things that I realized is that windows was far worse then I remembered.  Not that the other systems where perfect, but the sheer amount of problems I had every week blew me away...

It still does (I still have an XP desktop, but I'm a Linux sysadmin).  My single desktop requires more patching, maintenance, reboots and crashes then most of my servers together...

---

### Post by beercz on 2007-06-29
Use Windows :-(

I get frustrated by Windows :-(

I feel better after reading this:

[http://lap.umd.edu/computer_rage/Tech_Report/written_comments/win_mst.html](http://lap.umd.edu/computer_rage/Tech_Report/written_comments/win_mst.html)

---

### Post by phrostbyte on 2007-06-29
Yeah same way with me. I first used Ubuntu, then went back to Windows XP, but I was so used to how nicely Ubuntu worked, I switched back. I think this is common. :p

---

### Post by eXisor on 2007-06-29
slavik and djchandler: You both assume and presume and it is all FUD, FUD & FUD

Sorry to say but all your posts do is reflect your cluelessness. It is not the XP, it is u.

slavik: 

1) The way u updated 20 MS machines is daft. Check out [www.microsoft.com/corporate](www.microsoft.com/corporate). Typically, one downloads the updates to a local server and then rolls them out to the networked machines. Daft, I tell u.

2) VBScript is derived from Visual Basic and hence uses similar syntax. It would not be VBScipt if it did not, and it is daft to expect different. Similarly Javascript follows java syntax.

djchandler: 

The OS has nothing to do with boot sequence or boot device. There is a conflict, most likely because the hardware master/slave switch on the back of the XP ide was/is still set to master. In any event, what u accuse Xp of is impossible. That is not how it works.

Please people, I know MS is not great, but really.... 
.

---

### Post by daynah on 2007-06-29
Vista just froze on me in class and I lost my notes up to this point. But Ubuntu wont install. I need a drink.

---

### Post by graabein on 2007-06-29
I feel you man (without reading the whole post) cause I've been using Windows XP since the Feisty upgrade screwed up my Ubuntu install. When I get more time on my hands and my patience has run out I'll do a clean install of Feisty...

BTW does anyone know if there's a wiki for doing clean install and then hooking up with the previous partition of  **/home**?

---

### Post by siimo on 2007-06-29
Ever hear about C# and PowerShell ?

---

### Post by djchandler on 2007-06-30
> **eXisor said:**
> slavik and djchandler: 
...
.

Too all,

I censored this due to excessive facetiousness on my part. See below. Sorry for the publicly fanning the flames. I called out the DJFD.  

Sincerely,
D. J. Chandler

---

### Post by sloggerkhan on 2007-06-30
At this point I couldn't live without Ubuntu. (Or a similarly useful and easy to use free OS)

Windows drives me nuts very quickly.

At my job we use all kinds of dumb, slow, and painful tricks to work around the lack of "sudo" and "su" equivalents in windows....
Even the few times you can actually use "run as" to do something as an admin, it comes up with an annoying GUI dialog box...

---

### Post by conanm4 on 2007-06-30
I agree I don't like XP that much, but there are areas where Ubuntu and Linux in general needs to improve. Surround sound 5.1 from a stereo file as an example, there are several pieces of code for the .asoundrc file and one works for everything but some games have distorted audio and it does cause a slight pop in audio every 30 seconds or so. Other stuff too like commercial apps need to find it's way on Linux as an addition to the great free software. I do think Ubuntu is good for some people, but definitely not all. This isn't a fanboy thing I just think there is definitely room for improvement.

---

### Post by SoulinEther on 2007-06-30
> **djchandler said:**
> Hey, all you people like I used to be running Ubuntu on older spare hardware or just toying around with it on a dual boot system. Get rid of those old P4s and Athlon XPs. It's time to really use this OS.

I don't even have that good of a processor in my computer -- if I throw this out, I'll be totally ... Ubuntuless! NO!!!!!

And I agree. Windows really stinks. What gets ME most is Microsoft's EULA... for God's sake, I pay Microsoft for Windows... can't they leave me alone? No. You have to activate. And you can't use it on more than one computer.

And what really tickles me is how they try to solve your problem if you received an illegal copy of Windows either on a CD or pre-installed: You have to buy ... *ANOTHER*... copy of Windows to replace it.

To hell with that. If my windows ever said that to me, it wouldn't have touched my computer again...

then again, I've had the same computer for the past 4 years, so that's never been a problem for me. :P

---

### Post by rrinker on 2007-06-30
To point one, that there's no way to tell Windows where to get updates from - yes, there is. If you have a WSUS server you would want to create a machine policy that tells each workstation to get updates from the WSUS server instead of going out to the Windows Update site, otherwise the WSUS server is pretty much useless.

 As for Linux, IMO the biggest obstacle to widespread Linux adoption is that there are simply too many 'flavors' I tried 3 others with varying degrees of success until I discovered Ubuntu. I've installed Ubuntu on machines of all performance levels and so far it has just worked, unlike the other variation I've tried. Of course my first Linux install was back int he day when a 386 25MHz computer was a fast machine and you had to compile it all yourself. Outside of X, it was rock solid and faster than Windows 3.1. Linux has come a long way since those days.

 I've not made a 100% Ubuntu box yet, simply because there are a few things I need to run that just do not work in an XP VM or with WINE. I do spend more time in Ubuntu these days, at east on my home machine. I was tempted to put Ubuntu on my laptop as the primary OS, but I just know if I did, I will have to help out a client and won't be able to do what I need to under Linux (I install and support Windows networks, Exchange server, and SQL Server, as well as do some application development). I do have  portable Ubuntu - I run it in a VM under XP on the laptop.

 I guess what I'm getting at is that I am in no way a fanatic on either side. Windows is far from perfect, but so is Linux. Each has its strengths and weaknesses. Depending on your needs, one may be better than the other, but the wild anti-Windows sentiments are just out in left field. I've been using XP since the day the official release became available. Even broke my own rule and UPGRADED my Windows 2000 machine instead of doing a clean install. It worked fine, and continues to work fine even though that machine has been long since retired. 

 Pick one, pick the other, in the meantime I'll use both and be happy.

                                  --Randy

---

### Post by eXisor on 2007-06-30
EDIT: I've self-censored my post. Again.

djchandler: Our pm's are doing a better job of resolving this :)

.

---

### Post by djchandler on 2007-06-30
> **eXisor said:**
> EDIT: I've self-censored my post. Again.

djchandler: Our pm's are doing a better job of resolving this :)

.

eXisor,

I quite agree. All is well everybody. Our differences have been settled privately. The pm's have been great. I'm editing the facetious one above ASAP.

DJ

---

### Post by djchandler on 2007-06-30
> **SoulinEther said:**
> I don't even have that good of a processor in my computer -- if I throw this out, I'll be totally ... Ubuntuless! NO!!!!!

And I agree. Windows really stinks. What gets ME most is Microsoft's EULA... for God's sake, I pay Microsoft for Windows... can't they leave me alone? No. You have to activate. And you can't use it on more than one computer.

And what really tickles me is how they try to solve your problem if you received an illegal copy of Windows either on a CD or pre-installed: You have to buy ... *ANOTHER*... copy of Windows to replace it.

To hell with that. If my windows ever said that to me, it wouldn't have touched my computer again...

then again, I've had the same computer for the past 4 years, so that's never been a problem for me. :P

SoulinEther,

I didn't mean to be condescending in any way at all. Please forgive me. Some of us need to cut the cord to Microsoft, myself included. Sometimes I forget how international this community is, and that some of us aren't as fortunate in terms of access to newer hardware for various reasons. We need to start a thread or group, something like "Hardware Wish List" and see if somebody has some spare parts laying around, and then some sort of exchange or clearing house to help each other. Anybody have any ideas? We in the USA need to be very careful about export laws. Some countries are restricted as to what can be sent from here.

DJ

---

### Post by SoulinEther on 2007-06-30
Oh, no, don't get the wrong impression - I was just kidding. I get what you were saying, just trying to make a joke, hehe.

---

### Post by djchandler on 2007-06-30
That's good. It wasn't too long ago I was in the same boat.

We have the luxury of three computers for only two people--I am just spoiled. If we had one computer, it would probably be more up-to-date than the three we have, but I do not like laptop keyboards and pointing devices in general, and I have a tendency to fill up HDD space much more quickly than my wife. It is easier to manage the big chunks of data I create and then have to throw away this way. So we have three in places where we are likely to use them: one connected to our home entertainment center, one in her office, and one in my "dungeon," where I also "manage" my "museum" of computer parts. Also, I like to tinker with the hardware and such. One can not do that so much with a laptop.

DJ

---

### Post by nate22 on 2007-06-30
i personaly dont see all the HATe on MS.. ive been a LOONG time MS user and have no problem with it 
true linux is HELLLLAAAA better than MS or ms ever will be.. but heres the thing

i can go out to walmart buy a software and KNOW it will wrk on my computer..well to an extent


dont get me wrong fellas i love linux but  people like [this]("http://lap.umd.edu/computer_rage/Tec...s/win_mst.html") deserve thier coputer to break EVERY SINGLE DAY

we all know MS is bad..but not THAT bad
hell ive had my share of linux crashes


all im saying is like it or not MS is alot more user friendly to everyday ppl,

and old man that doesnt know alot about computers can go out buy MS buy software and get going

---

### Post by samschoice on 2007-06-30
Well, in the years I used windows, I never got a hard core virus. Every virus I got were tiny little internet explorer exploits. However, all the productivity time I lost doing tons of virus scans, and running defrags using Windows can't be recovered. The cost of keeping windows safe is an unspoken labor cost.

Now, who needs windows ? Most little old ladies don't need windows. If they just want to surf the web and have pretty good security, they should use Linux and not windows.

However, I do think most small business might still need windows yet because they need Quick Books, which is not available in Linux, as far as I know. Also AutoCad is not in Linux either.

---

### Post by Ralob on 2007-06-30
You know what grinds my gears about Windows? Not that is takes so long to boot up after only being installed a month. But how long it takes to shut down. I swear, I have waited in front of my computer for several minutes while Windows gets itself together Eventually it just says "to hell with it" and shuts down. With Ubuntu, boot up and shut down are always so fast that I can't get over how smooth it all runs. Windows only ran like that for a short time after you defragged your harddrive or reinstalled the OS. That being said, I have nothing personal against Microsoft, only Windows' inherent instability and design flaws. :P

---

### Post by logos34 on 2007-06-30
> However, all the productivity time I lost doing tons of virus scans, and running defrags using Windows can't be recovered. The cost of keeping windows safe is an unspoken labor cost.

Yeah, all those hours and hours of your life wasted running av and Defender spyware scans!  Plus that junk hogs all your memory and slows everything down.
> 
But how long it takes to shut down. I swear, I have waited in front of my computer for several minutes while Windows gets itself together Eventually it just says "to hell with it" and shuts down.

Come to think of it, it is kinda funny the way it does that...My big beef now is how long the thing is taking to boot up...actually it's shouldn't be an issue because I almost never go into windows anymore, but nevertheless it is still there and should work properly, and besides I keep it mainly to help out people trying to migrate to linux or dual-boot.  But the other day I downloaded that HUGE SP2 pack for windows XP x64 pro and a bunch of security patches, and it totally borked the thing.  Takes an eternity for the desktop to load where it previously took like 30-35 secs.  I finally uninstalled it in disgust, but that didn't help, so I suppose it's something in the security updates.  It's all buggy now--mouse, windows, menus...Anyone else have the same experience with the recent updates?  What a piece ofgarbage.  (Good thing it's free--I'm running the 'trial' version of x64 and have been for the last year and a half.  All you have to do is reinstall every four months).

---

### Post by djchandler on 2007-07-01
You guys have raised a really important issue., Seriously, how big a deal is it to already have part of Acrobat Reader, or Quick Time partially loaded just to read a short PDF, or run a little .MOV file. Stuff like that just absolutely drives me crazy. If I want to read the PDF, give me a way to save it or go directly to it instead of linking to another HTML or javascript or some other roundabout way to get to it. The same goes for multimedia files. What about all the plug-ins for your browsers? Every body wants their stuff resident in memory just so the average user really does need more ram, just for all the resident stuff. I have to clean up this kind of junk on my wife's computer all the time. More people need to know how to use MSCONFIG.EXE and customize their start-up process to speed it up. I do, but the so-called free stuff sometimes isn't so free when it comes to your time.

Adobe is especially bad about this, but I suppose they are trying to help their end-users protect their end-product, as in intellectual property rights. I am an Adobe end-user, and I don't want people stealing my end-product, but that should be left up to the end user of the development software to manage. How hard could it be? In the case of Quick Time wanting ram dedicated to their "free" movie player, that's just Apple slowing things down from the start. Apple is not the nicest company to do business with either. But I digress, as usual.

I do not understand the need for a bunch of these types of programs loading at start-up and be resident in ram. It really doesn't make that PDF file come up *that* much faster. If I want to burn a DVD, I'll wait for a program to load, I am not that impatient. Don't they realize, it's starting-up and shutting down Windows itself we find so hard to sit through. If Windows was stable enough to stay up and running for more than a couple of days of hard use, than it would be okay. But when you need to restart several times a day, it's a real drag.

---

### Post by slavik on 2007-07-02
> **rrinker said:**
> To point one, that there's no way to tell Windows where to get updates from - yes, there is. If you have a WSUS server you would want to create a machine policy that tells each workstation to get updates from the WSUS server instead of going out to the Windows Update site, otherwise the WSUS server is pretty much useless.


I am not the AD admin where I work (i work under 1) ... but how do you get Windows to actually check for updates when there is a group policy to check WSUS server? What if I do not actually host the updates?

Here's another one, how do I force certain programs to be upgraded along with system updates? (WSUS doesn't do this, and SMS is pretty expensive). Meta-packages were invented for a reason ;)

---

