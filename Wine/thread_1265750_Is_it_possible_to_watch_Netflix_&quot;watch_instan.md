---
title: "Is it possible to watch Netflix &quot;watch instantly&quot; under XP's Firefox under Wine?"
date: 2009-09-13
forum: Wine
---

### Post by unckybob on 2009-09-13
Hi, 

I am trying to view Netflix "watch instantly" movies using the XP version of Firefox under Wine. 

I got the XP version of Firefox to install and it runs just fine. 

I need to install the "silverlight" plug-in in order to use the "watch instantly" feature from the Netflix website. When I try to install it with the Wine Windows Program Loader, it needs to extract some files. I get a message saying: 

Extraction faild: unable to find a volume for file extraction. Please verifiy that you have proper permissions. 

I think that this means that I need root permissions to install "silverlight" with the "Wine Windows Program Loader". 

Does this mean that I need to type in something in a terminal like: 

$sudo <Wine Windows Program Loader> silverlight 

?

And can someone show me the proper commands and syntax? 

Please help me, 
Bob

---

### Post by snowpine on 2009-09-13
Hi Bob, Netflix has chosen not to support Linux, unfortunately. You'll need Windows or Mac to watch instantly.

---

### Post by jrusso2 on 2009-09-13
The only way to watch Netflix on Linux is with a virtual machine loaded with Windows XP, Vista and maybe Windows 7

---

### Post by snowpine on 2009-09-13
Unfortunately Flash performance is worse in a Windows virtual machine running under Linux than in Windows. I recommend dual booting if you watch a lot of Netflix.

---

### Post by Defrector on 2009-09-13
There definitely is no linux support in Netflix, but that doesn't necessarily mean you can't hack it to think it is in windows.

Could try sudo if you're willing to fix things if they get gnarly. I do not know where the loader wants to put those files. If you can apply some verbose flags on the loader within the terminal it might give some clue. As usual, be careful with sudo (though I recklessly use it myself).

I would hope that a program would try to install itself nicely and compactly, but it's very possible that Silverlight wants to install things at the windows\system level.

EDIT: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14455&iTestingId=33333](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14455&iTestingId=33333)

... info on Silverlight. If you feel adventureous perhaps you can try to make it work better than it says?

---

### Post by unckybob on 2009-09-13
Thanks a lot you guys. And thanks for that website. I'm just a newbie so I'll hold  off on trying to make it work. If it weren't for your help, I probably would have wasted a lot of time trying to get it to work. 

Cheers, 
Bob

---

### Post by Tigersmind on 2009-09-14
Oh man!

Netflix used to work on Firefox under Linux. I haven't watched a movie in some time though, so it has stopped again. This stinks  :(

---

### Post by baceman007 on 2009-10-16
I have been working on the Netflix/Ubuntu 9.04 problem for quite some time.
I offer the following obervations with no implied warranty.
I started with looking at the directions here 
[http://fatbuttlarry.blogspot.com/2009/02/netflix-ubuntu.html](http://fatbuttlarry.blogspot.com/2009/02/netflix-ubuntu.html)
but since this user had the most success with 8.04 I had to keep looking. Which lead me to this forum amongst many other places. 
At any rate here's what I did after trying the moonlight 1.99.5, Coral IETab, and User Agent Switcher combinations and only getting as far as the Active X is not enabled screen. I tried ies4linux as well. 

-- At this point I can get a instant movie to load to the point that I get the black backdrop with the swirling blue loading icon on Netflix in Firefox 3.5 run using Wine 1.1.3 with Silverlight 3 and some Windows Fonts installed as explained below.  

-- I added [http://wine.buggetdedicated.com/apt](http://wine.buggetdedicated.com/apt) edgy 
to the Third-Party Software tab under System -- Administration -- Software Sources and added an authentication certificate for winehq. 
[http://ubuntuforums.org/showthread.php?t=338400](http://ubuntuforums.org/showthread.php?t=338400)
this explains getting the winehq gpg key. If you don't have it you should just get a warning when installing. Adding it should make the warning go away forever. This allows you to install the most recent versions of Wine which may not be the stable releases.

-- I then went to System -- Administration -- Synaptic -- and installed Wine 1.1.3, wine-dev 1.1.3, and wine-gecko 1.0.0. Note: In theory after you add the source and refresh the package list, when prompted, the Update Manager should tell you that there is an update for Wine, or if you use Add/Remove to add Wine and then use the Update Manager (System -- Administration -- Update Manager) it should tell you. Anyway, I just used Synaptic so whatever floats your boat. 

-- I downloaded the Windows version of Firefox 3.5 from [www.Mozilla.com/Firefox3.5](www.Mozilla.com/Firefox3.5), went to Application -- Wine -- Browse C: drive and dropped the *.exe in there. I then double clicked on it and installed it. 

-- Launch Firefox 3.5 using Wine, go to Netflix and log in, then choose something to watch instantly. You will then be told to download Silverlight 3. Save the *.exe file for it and move it into your Wine C: drive as explained in the last step. 

-- Close Firefox and install Silverlight. If you go to Netflix again at this point you will get a font error stating that you must be a Crapple user if you're getting a font error. Of course you're not, but Netflix believes that people only use Windoze and OSXcrament so that's what you get. If they didn't believe this they would have just used something that already works on everyone's systems instead of painting themselves into a corner with Silverlight... I still like Netflix, but the whole Silverlight thing gets on my nerves...  

-- Anyway, to solve this font problem you need to move some Windows fonts into your Wine virtual C: drive\windows\fonts folder. I copied them from my legal copy of Windows in it's C:\Windows\Fonts folder. I have a dual boot setup so this was easy. I'm sure some linux font guru probably has a welcome substitution to this step that doesn't involve having to use Crapple or Microshaft fonts but that's what I did. 

-- Once you do this, at least for me, when I go to Netflix using Firefox 3.5 and Silverlight 3 run through Wine I get the movie to start to load, then my browser freezes and goes grey. Anyway, it's at least promising. 

-- I should mention that I'm using a Toshiba laptop that is using the generic Ubuntu video driver. I was never able to get fglrx to work totally so I went back to the generic. I sometimes get white lines on the right hand side of the screen when I scroll and 2ndary monitor support is not existent so perhaps I have larger problems and someone else, with a Dell for example, may have more luck with my steps. Perhaps the video driver has nothing to do with it at all. Anyway, I hope this helps someone out.

---

### Post by plinus on 2009-10-24
I would love to do this on linux, hear me ubuntu gurus as netflix has not been hearing what their audience wants, if only there was another company that offered movies on linux....

---

### Post by MaindotC on 2009-10-29
> **plinus said:**
> I would love to do this on linux, hear me ubuntu gurus as netflix has not been hearing what their audience wants, if only there was another company that offered movies on linux....

Remember, it's not that Netflix doesn't want to support Linux, it's that Linux users typically wish not to support DRM which is essential for Netflix to operate properly.

---

### Post by mjhouska on 2009-10-30
Yep It's a DRM issue. As for me I don't care I just want my functionality. we wouldnt have all those cool special effects if nobody was making a profit from movies. that said i"m also glad decss got cracked so i can watch my legally rented movie on my linux laptop.:popcorn:

---

### Post by cleopete on 2010-02-24
I swear, I have never seen so many people give so many detailed step by step instructions for making something not work.  Anyone who has spent five minutes trying to find a way to do Netflix in Linux knows: you can't. It's not a tech problem, it's a legal issue. That's it.  If you find a way, by all means share it.  Until then, please put a sock in it.  No more misleading thread headings, Netflix/M$ bashing (I loathe Microsoft as much as the next no-account geek, but c'mon, for once it's not their fault), and jack-off theoretical musings.  Just stop. Please.

I won't apologize for the rant either.  This is the gazillionth Google hit to a solution-implying thread, and I'm clearly not impeding ANY productive work.

---

### Post by Warren Watts on 2010-02-24
Why re-invent the wheel?  Watch your Netflix movies in XP and enjoy the show!

---

### Post by ElSlunko on 2010-02-24
Did my browser just step through a wormhole. I think I need more sleep.

---

### Post by bleys2112 on 2011-05-15
[rant]
Why is this thread marked as solved when obviously it is not?

Also, why do people insist on posting stuff like "you can't do that", "it will never work" or "just use windows"?  Honestly, if you are not going to contribute something meaningful towards an actual solution, just keep it to yourself.  Persistence and determination are the cornerstone of discovery and it is disheartening to read such negative and stifling remarks when there are those who may be on to something that potentially may benefit the entire linux using community as a whole.  I for one am not entirely convinced that this is not possible to achieve and will continue to remain so until I get a much more technically detailed explanation as to why this is allegedly impossible to accomplish.
[/rant]

Update: I read somewhere else to try the following:
Download silverlight into wine, go to userstyle.org download the  userscript that forces silverlight to run, change the code directory to  point to the .exe in the wine partition. It should work then. 		

I shall return with the results of this endeavor.

---

### Post by bobwyajnr on 2011-05-21
> **bleys2112 said:**
> [rant]
Why is this thread marked as solved when obviously it is not?

Also, why do people insist on posting stuff like "you can't do that", "it will never work" or "just use windows"?  Honestly, if you are not going to contribute something meaningful towards an actual solution, just keep it to yourself.  ...
[/rant]


Well done sir!! ):P

We wouldn't have the wonderful tool that is [get_iplayer]("http://linuxcentre.net/getiplayer") for the Beeb without a bit (well a lot actually) of perseverance on the part of Phil Lewis (original developer). It's actually got a better interface then the real BBC iPlayer app. (Never mind the fact I don't have to deal with all that flash garbage...)

Good luck with your Netflix endeavours... Down with evil MS DRM... :popcorn:

Bob

---

### Post by Xinux6 on 2011-05-22
The problem isn't DRM support for Netflix on Linux. The problem is licensing from the entertainment companies for their content to be played on linux. This comes directly from Netflix. They actually could get some companies to license their titles for linux but according to them there would be very few titles. Netflix really does not hate linux users.

---

### Post by bobwyajnr on 2011-05-23
> **Xinux6 said:**
> The problem isn't DRM support for Netflix on Linux. The problem is licensing from the entertainment companies for their content to be played on linux. This comes directly from Netflix. They actually could get some companies to license their titles for linux but according to them there would be very few titles. Netflix really does not hate linux users.

Ah. Is that simply due to size of the Linux user base? I am slightly puzzled - what difference does the OS make - a US subscriber is still a US subscriber - no?

The equivalent of Netflix - LoveFilm - in the UK probably doesn't have the scale (of users). They only offer very low quality streaming. But at least it is via a cross-platform Flash plugin...

Yours in ignorance (in the UK)...:popcorn:
Bob

---

### Post by doublemeat on 2011-05-25
> **bleys2112 said:**
> [rant]
Why is this thread marked as solved when obviously it is not?

Also, why do people insist on posting stuff like "you can't do that", "it will never work" or "just use windows"?  Honestly, if you are not going to contribute something meaningful towards an actual solution, just keep it to yourself.  Persistence and determination are the cornerstone of discovery and it is disheartening to read such negative and stifling remarks when there are those who may be on to something that potentially may benefit the entire linux using community as a whole.  I for one am not entirely convinced that this is not possible to achieve and will continue to remain so until I get a much more technically detailed explanation as to why this is allegedly impossible to accomplish.
[/rant]

Update: I read somewhere else to try the following:
Download silverlight into wine, go to userstyle.org download the  userscript that forces silverlight to run, change the code directory to  point to the .exe in the wine partition. It should work then. 		

I shall return with the results of this endeavor.

I agree with cleopete on this one. I have also never seen people posting so many detailed steps to not get something to work. The steps and the detail are then pretty pointless. Nobody has even gotten cruddy, choppy video to work - so nobody has really gotten "close". (The spinning blue thing is not "close" any more than a splash screen but nothing more is "close".)

I'm glad I stumbled on this thread early into my attempts to get Netflix to run on Wine! Saved me a whole bunch of hassle.

And please people, bashing companies that don't support their products on Linux is tiresome (and really really old...and insufferably unrealistic). Linux has an infinitesimal share of the target market for most mainstream applications. Period. (And IMO for some fairly good technical and usability reasons, above and beyond just not having millions for marketing. Most humans just don't appreciate "free as in beer and speech" like "we" do, they'd rather it just work without compiling their own stuff and hacking drivers and messing with xorg.conf and writing shell scripts.) 

If and until the market share numbers change - and/or until mainstream apps go fully HTML5/Javascript/locally cached "cloud"-based; then Linux just is not going to run many mainstream apps painlessly. (At least not without the valiant Wine efforts...which virtualization in some future form or another may eventually [unfortunately IMO] render moot. It already does more or less for me [all machines have 8-16 gb RAM specifically for virtualization], with the exception of VirtualBox reliably crashing on my Ubuntu 10.10 macbook.)

(While *I'm* ranting - another completely unfounded yarn I'm sick of hearing: "Your hardware problems are caused by Linux/BSD/etc. being a more advanced OS and working your machine harder.")

---

### Post by papibe on 2011-05-25
Google wants Netflix to work into their ChromeOS. That basically will mean some sort of HTML5 plug-in for the browser. And that would bring it to Linux.

Maybe not as fast as we all want, but I think it will happen. Read this [article]("http://www.omgubuntu.co.uk/2011/05/netflix-chrome-plugin-will-bring-on-demand-video-to-linux/").

Regards.

---

### Post by doublemeat on 2011-05-25
> **papibe said:**
> Google wants Netflix to work into their ChromeOS. That basically will mean some sort of HTML5 plug-in for the browser. And that would bring it to Linux.

Maybe not as fast as we all want, but I think it will happen. Read this [article]("http://www.omgubuntu.co.uk/2011/05/netflix-chrome-plugin-will-bring-on-demand-video-to-linux/").

Regards.

Good news, and a good point. Also, I just remembered (and don't seem to recall this fact being pointed out on this thread yet), that Netflix works on PS3...without Silverlight. Apparently they have hacked the Webkit engine to run on PS3 just for their app (which is a web app that looks like a native app).

It also works on iPhone, and some Android models (again...sans Silverlight).

So there's apparently no technical reason Netflix can't run on Linux...maybe the size of the additional market for them still just isn't worth the effort. (And/or maybe those other platforms are considered less threatening as far as DRM hacking / piracy goes...)

---

### Post by Swashbunglar on 2012-02-27
> **doublemeat said:**
> It also works on iPhone, and some Android models (again...sans Silverlight).

Ready for the real kicker... Android IS linux.... WTF neflix!
So saying it "can't" work on linux is BS.

---

### Post by forrestcupp on 2012-02-28
> **Swashbunglar said:**
> Ready for the real kicker... Android IS linux.... WTF neflix!
So saying it "can't" work on linux is BS.

Android uses the Linux kernel at the lowest level, but beyond that, it is absolutely nothing like the GNU/Linux based operating systems we use. Saying that Linux OSs should run Netflix because Android does is like saying that FreeBSD should be able to run all MacOS X software.

---

### Post by doublemeat on 2012-02-29
> **Swashbunglar said:**
> Ready for the real kicker... Android IS linux.... WTF neflix!
So saying it "can't" work on linux is BS.

Yeah not really so much. The tiniest (and customized) part of the Linux kernel, and that's it. It isn't even POSIX-compliant, doesn't have the userland tools, and the GUI and it's API has no resemblance to X-Windows (much less gnome or KDE) and is more tightly integrated into the kernel.

An analogy would be like saying the iPhone is Mac OS X. (Though maybe that is even less accessible of a concept to Linux users as just refuting the "Android=Linux" meme.)

Android is also usually locked from the factory so users can't gain root access. (I know many people unlock them - myself included - but it's a minority of users.) I'm sure a device that is much more locked down than a PC is a big part of studios "allowing" Netflix to have an Android app.

But really it's the the Linux market share issue, just no way around that.

Countless experts have argued that Linux' market share is greatly hampered by fragmentation. (Not to mention that one is pretty lucky to install any distro on a machine without significant fiddling.) But...those are two different and well-flogged topics than the Netflix issue!

I love threads like this that live a long time. I can't even remember why I first contributed to it, I'll have to go back and look. But for me, I've given up on the idea of Linux as an entertainment device. I don't watch TV, and any media I do consume is either through the PS3, or Netflix on Android or iPhone. (Yeah I carry both. What a dork.)

---

### Post by doublemeat on 2012-02-29
> **forrestcupp said:**
> Android uses the Linux kernel at the lowest level, but beyond that, it is absolutely nothing like the GNU/Linux based operating systems we use. Saying that Linux OSs should run Netflix because Android does is like saying that FreeBSD should be able to run all MacOS X software.

Well that was a more succinct and earlier version of my argument...

---

### Post by doublemeat on 2012-02-29
> **doublemeat said:**
> I've given up on the idea of Linux as an entertainment device.

I should point out though, that when hardware and virtualization software gets to the point where I can run media software i.e. Netflix, full-screen and tear/stutter free, then I'll probably use Linux as the base and Windows as the media portal. (Though Netflix in particular has tearing and terrible de-telecine-ing issues even natively.)

That point should be very soon. Gradually improving and expanding IOMMU/VT-d support will eventually render the race for improving virtualized acceleration graphics a moot point. (Kind of frustrating that the hardware support for it has been around since antiquity, relatively speaking, and getting it to work in virtualization software is either really expensive, or prohibitively fiddly for even typical advanced users.)

---

### Post by forrestcupp on 2012-02-29
> **doublemeat said:**
> (Kind of frustrating that the hardware support for it has been around since antiquity, relatively speaking, and getting it to work in virtualization software is either really expensive, or prohibitively fiddly for even typical advanced users.)

That's why it's best to just watch Netflix through a supported TV attached device, like it was designed for. Since I started watching Netflix in its intended way and using consoles for gaming, I've had a lot less headaches with Linux.

---

### Post by doublemeat on 2012-03-06
> **forrestcupp said:**
> That's why it's best to just watch Netflix through a supported TV attached device, like it was designed for. Since I started watching Netflix in its intended way and using consoles for gaming, I've had a lot less headaches with Linux.

That is not true. Netflix - specifically, the on-demand streaming service we are discussing, "was designed for" the Mac/PC web browser. That is all that was supported for years. In fact, it started out as Flash playback, then Silverlight came later. It has been "Computer-only" longer than it has been supported on other devices. 

I regularly use Netflix on PC, iPhone, Android, and PS3. I'm not crazy about how they are all radically different UXes (with Android and iOS at least being similar), but at least there's one advantage to that - they do seem to better take advantage of platform strengths and native conventions.

The PC/browser interface is objectively the most feature-complete version. It is the baseline against which the others are evaluated. (Whether or not it is a "better" experience than the others is a subjective issue.) Most new features start in the browser version. It also has the fewest playback issues (not surprisingly as it has a years head-start development-wise). 

I'm going to refrain from lecturing about getting facts straight, gloating, etc. (Mainly because I'm not, say, 16 yo.) :-)

But hey, if you prefer Netflix on devices, that's all good. I too use it more on PS3 and iPhone, than PC.

---

### Post by forrestcupp on 2012-03-06
Well, we could both lecture and debate about what Netflix streaming was "designed for". Unless you happen to work for Netflix, I doubt if either of us truly know. But one thing I do know is just because something is *launched* a certain way doesn't mean that is what it was designed for. 

I tend to think that it was designed to be watched on TVs through devices, but it was necessary for them to go ahead and launch on PCs to build up their library and user base while the devices were being prepared and created. Did you notice how quickly they worked to roll out Netflix on game consoles? That's because it's a lot quicker to create software for devices that would support it, and it takes a little longer to get it into embedded stuff.

I can almost guarantee that Netflix streaming was designed to be watched on TVs through TV attached devices, and smart TVs, themselves.

I will say that it also comes in handy on my Android tablet while I'm walking on the treadmill. ;)

---

### Post by doublemeat on 2012-03-06
Not to attack you personally (you seem like a wonderful person), but  your argument is so full of uninformed misinformation and  supposition-based assertions, that I think it would be instructive (in  more general terms than just this debate) to break it down:

> **forrestcupp said:**
> Well, we could both lecture and debate about what Netflix streaming was "designed for"

Actually we really don't have to do that. There is an objective truth, from Netflix.


> **forrestcupp said:**
> Unless you happen to work for Netflix, I doubt if either of us truly know.

I'm glad you said "doubt", because as it turns out, this is incorrect. (As you might have guessed!):

[LIST=1]
[*]I used to work for a Netflix competitor and helped sell it to a  (then) major competitor of Netflix. (Both startup and suitor shall  remain nameless - otherwise you could discover my true identity [and  then physical address etc.] with just a few clicks...this way it would  take more determination.) I then followed and still do follow Netflix  pretty closely, and have been a member for close to a decade. I've used  their streaming service since it arrived four years ago. Although I  don't have insider information on Netflix, we don't need any. The  relevant information to debunk this is public. So, you don't have to  take my industry-informed word for it...
[*]You can read Netlfix' quarterly earnings reports, including future  strategic plans for streaming, going back ten years since their IPO.
[*]Netflix publishes several blogs - most interestingly, a general  blog and a technical blog. Both include really great insights. In both  blogs (not just the technical one), they regularly discuss technical  innovations that almost always debut in the Silverlight client first.  Perusing this blog should settle this non-debate in your own heart and  mind, without taking my word for it.
[*]One reason (of several) that the browser version is the main  development focus and testbed, is because: A) It is much easier to code  for, and B) It is much much easier to deliver updates for. There is no  "update" mechanism required, as there is no installed client application  (cached yes installed no). With the browser version, you automatically  get whatever version is the latest (or at least whatever flight-testing  group you arbitrarily [or not] fall into). The PS3 version, for example,  includes a complete (ported and modified) Webkit application (just for  Netflix). It must be manually updated. (Or quasi-manual depending on how  you look at it.)
[*]And here is the clincher: More people use the browser version for  streaming, than almost all other couple-dozen versions combined. Kind of  makes sense to make that your focus. Any more questions?
[/LIST]
 **It might be worthwhile to re-read points 4 and especially 5.**


> **forrestcupp said:**
> ...just because something is launched a  certain way doesn't mean that is what it was designed for.

See #s 4 and 5 above.

This isn't much of a debatable point though, at least semantically.  There are a couple dozen devices Netflix runs on. (Even Google Chrome  OS.) This assertion boils down to self-evidence: For each  platform/device Netflix runs on, of course: "it was designed for" it.

The point remains however, that Mac/PC browser+Silverlight version is  the first and primary development target, and is the most common target  for new features first.

Assuming Netflix is around for the long-haul, that fact may cease to be  true eventually. (I'm sure they foresee the inevitable irrelevancy of  the mainstream desktop OS just as well as anyone.) But it doesn't help  us to debate "might bes" in this context, in a void of objective fact.


> **forrestcupp said:**
> I tend to think that it was designed to be watched on TVs through devices

Again, we don't have to guess or "tend to think". The PC browser was the  first and primary target, and remains so; that isn't my opinion. (See second section.)

But sure, we can project arbitrarily into the future. In the future, I'm  sure Netflix would love to be part of your neural computing implant,  streaming any show or movie on-demand, direct to your optic nerve or  visual processing center (or maybe more conveniently - just drop it  instantly into your short-term memory). Or closer to present-day, I'm  sure they'd love to come standard on the firmware of all new TVs.

In either case, that doesn't mean that was what it was "designed for"  (to use your terminology) at first, or now, or next week, or next year.


> **forrestcupp said:**
> Did you notice how quickly they worked to roll out Netflix on game consoles?

It's no coincidence that Windows is the primary desktop target, and the XBox was the first gaming console. 

But, game consoles were not the first targets. While this statement  isn't a falsifiable assertion, what it *seems* to suggest is at worst  false, or at best not necessarily true. (That consoles were first -  and/or, are somehow easier ["quickly"].)


> **forrestcupp said:**
> That's because it's a lot quicker to create software for devices that  would support it, and it takes a little longer to get it into embedded  stuff.
These so-[you]-called "embedded stuff" were the first non-PC/browser  clients, not gaming consoles. There were two or three of them first out  of the gate before the XBox 360.

[LIST=1]
[*]"Embedded stuff", by number of devices, handily outnumber gaming  console clients (which might be kind of obvious with a couple dozen  clients as there are only so many game consoles).
[*]Linux-like OSes are the most common underlying platform for  non-game console devices. One (like me) could argue that Linux-ish  devices are easier to develop for than the three highly specific and  unique gaming consoles, as there would be a some chunk of code in common  among the various Linux devices.
[/LIST]
 Had you been more specific in what you meant by "embedded stuff" (e.g.  ruling out entertainment devices built on small-form general-purpose  computing hardware and running tweaked Linux kernels), I might be  inclined to agree with this assertion in principle. However, the state  of the actual world (e.g. point #1) would still challenge that notion.


> **forrestcupp said:**
> I can almost guarantee that Netflix  streaming was designed to be watched on TVs through TV attached devices,  and smart TVs, themselves.

I believe we've established that your "almost guarantee", plus 50 cents, will buy a pack of gum. ;-) (I don't find any perverse glee in that, BTW.)


> **forrestcupp said:**
> I will say that it also comes in handy on my  Android tablet while I'm walking on the treadmill. 

On this subjective assertion, we agree! (Even though I don't have an  Android tablet nor use a treadmill - though I have no objection to  either.)


Peace.

---

### Post by doublemeat on 2012-03-06
Not to attack you personally (you seem like a wonderful person), but your argument is so full of uninformed misinformation and supposition-based assertions, that I think it would be instructive (in more general terms than just this debate) to break it down:

> **forrestcupp said:**
> Well, we could both lecture and debate about what Netflix streaming was "designed for"

Actually we really don't have to do that. There is an objective truth, from Netflix.


> **forrestcupp said:**
> Unless you happen to work for Netflix, I doubt if either of us truly know.

I'm glad you said "doubt", because as it turns out, this is incorrect. (As you might have guessed!):

[LIST=1]
[*]     I used to work for a Netflix competitor and helped sell it to a (then) major competitor of Netflix. (Both startup and suitor shall remain nameless - otherwise you could discover my true identity [and then physical address etc.] with just a few clicks...this way it would take more determination.) I then followed and still do follow Netflix pretty closely, and have been a member for close to a decade. I've used their streaming service since it arrived four years ago. Although I don't have insider information on Netflix, we don't need any. The relevant information to debunk this is public. So, you don't have to take my industry-informed word for it...
[*]You can read Netlfix' quarterly earnings reports, including future strategic plans for streaming, going back ten years since their IPO.
[*]Netflix publishes several blogs - most interestingly, a general blog and a technical blog. Both include really great insights. In both blogs (not just the technical one), they regularly discuss technical innovations that almost always debut in the Silverlight client first. Perusing this blog should settle this non-debate in your own heart and mind, without taking my word for it.
[*]One reason (of several) that the browser version is the main development focus and testbed, is because: A) It is much easier to code for, and B) It is much much easier to deliver updates for. There is no "update" mechanism required, as there is no installed client application (cached yes installed no). With the browser version, you automatically get whatever version is the latest (or at least whatever flight-testing group you arbitrarily [or not] fall into). The PS3 version, for example, includes a complete (ported and modified) Webkit application (just for Netflix). It must be manually updated. (Or quasi-manual depending on how you look at it.)
[*]And here is the clincher: More people use the browser version for streaming, than almost all other couple-dozen versions combined. Kind of makes sense to make that your focus. Any more questions?
[/LIST]
 ** It might be worthwhile to re-read points 4 and especially 5.**


> **forrestcupp said:**
> ...just because something is launched a certain way doesn't mean that is what it was designed for.

See #s 4 and 5 above.

This isn't much of a debatable point though, at least semantically. There are a couple dozen devices Netflix runs on. (Even Google Chrome OS.) This assertion boils down to self-evidence: For each platform/device Netflix runs on, of course: "it was designed for" it.

The point remains however, that Mac/PC browser+Silverlight version is the first and primary development target, and is the most common target for new features first.

Assuming Netflix is around for the long-haul, that fact may cease to be true eventually. (I'm sure they foresee the inevitable irrelevancy of the mainstream desktop OS just as well as anyone.) But it doesn't help us to debate "might bes" in this context, in a void of objective fact.


> **forrestcupp said:**
> I tend to think that it was designed to be watched on TVs through devices

Again, we don't have to guess or "tend to think". The PC browser was the first and primary target, and remains so; that isn't my opinion. (See second section.)

But sure, we can project arbitrarily into the future. In the future, I'm sure Netflix would love to be part of your neural computing implant, streaming any show or movie on-demand, direct to your optic nerve or visual processing center (or maybe more conveniently - just drop it instantly into your short-term memory). Or closer to present-day, I'm sure they'd love to come standard on the firmware of all new TVs.

In either case, that doesn't mean that was what it was "designed for" (to use your terminology) at first, or now, or next week, or next year.


> **forrestcupp said:**
> Did you notice how quickly they worked to roll out Netflix on game consoles?

It's no coincidence that Windows is the primary desktop target, and the XBox was the first gaming console.

But, game consoles were not the first targets. While this statement isn't a falsifiable assertion, what it *seems* to suggest is at worst false, or at best not necessarily true. (That consoles were first - and/or, are somehow easier ["quickly"].)


> **forrestcupp said:**
> That's because it's a lot quicker to create software for devices that would support it, and it takes a little longer to get it into embedded stuff.

These so-[you]-called "embedded stuff" were the first non-PC/browser clients, not gaming consoles. There were two or three of them first out of the gate before the XBox 360.

[LIST=1]
[*]"Embedded stuff", by number of devices, handily outnumber gaming console clients (which might be kind of obvious with a couple dozen clients as there are only so many game consoles).
[*]Linux-like OSes are the most common underlying platform for non-game console devices. One (like me) could argue that Linux-ish devices are easier to develop for than the three highly specific and unique gaming consoles, as there would be a some chunk of code in common among the various Linux devices.
[/LIST]
 Had you been more specific in what you meant by "embedded stuff" (e.g. ruling out entertainment devices built on small-form general-purpose computing hardware and running tweaked Linux kernels), I might be inclined to agree with this assertion in principle. However, the state of the actual world (e.g. point #1) would still challenge that notion.


> **forrestcupp said:**
> I can almost guarantee that Netflix streaming was designed to be watched on TVs through TV attached devices, and smart TVs, themselves.

I believe we've established that your "almost guarantee", plus 50 cents, will buy a pack of gum. (I don't find any perverse glee in that, BTW.)


> **forrestcupp said:**
> I will say that it also comes in handy on my Android tablet while I'm walking on the treadmill. 

On this subjective assertion, we agree! (Even though I don't have an Android tablet nor use a treadmill - though I have no objection to either.)


Peace.

---

### Post by forrestcupp on 2012-03-07
Wow! That's some post to be posted twice. I got double thrashed! Lol. :)

> **doublemeat said:**
> 
It's no coincidence that Windows is the primary desktop target, and the XBox was the first gaming console.

But, game consoles were not the first targets. While this statement isn't a falsifiable assertion, what it *seems* to suggest is at worst false, or at best not necessarily true. (That consoles were first - and/or, are somehow easier ["quickly"].)
That's not what I was implying at all. What I was implying was that it is much easier to roll out an app for a Wii or 360 than it is to get Netflix Streaming into "embedded stuff" that doesn't already support it, and it takes time to manufacture and build a user base of "embedded stuff" that does support it. By "embedded stuff", contextually, it's obvious that I'm talking about things like DVD/Blu Ray players, smart TVs, and devices like Roku or the WD TV Live.

So with your great big, long argument, you've done a good job of proving that they launched streaming for the PC, that they use that platform as a test bed for new features, and that up until this point, that has been the most used platform for streaming.

What you didn't prove is that when they came up with the concept of Netflix streaming, watching their movies and shows on a PC is what they envisioned. It still just makes sense to me that they created Netflix streaming with a goal of being able to watch those things on a TV, which is where most people watch TV shows and movies in their homes. So I'll add to what I said. Just because something is launched a certain way and they even use that way as a testbed for new features, it doesn't necessarily mean that's how they envisioned the outcome. It takes time and steps to get to your goal. And since you admitted that you never worked for Netflix and you don't have insider information, I guess you probably don't know what their initial goal was any more than I do.

---

### Post by NadirPoint on 2012-03-07
I might be starting to understand the purpose of "marketing."

---

### Post by doublemeat on 2012-03-07
People who think they know everything are a great annoyance to those of us who do.

---

### Post by Micaiah on 2013-02-22
Netflix can be watched on XP as explained here

[http://itspecials.blogspot.com/2013/02/using-netflix-on-microsoft-windows-xp.html](http://itspecials.blogspot.com/2013/02/using-netflix-on-microsoft-windows-xp.html)

---

