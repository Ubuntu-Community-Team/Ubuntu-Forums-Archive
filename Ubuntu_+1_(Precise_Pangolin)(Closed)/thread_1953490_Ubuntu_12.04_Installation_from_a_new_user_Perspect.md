---
title: "Ubuntu 12.04 Installation from a new user Perspective"
date: 2012-04-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by KarmicKarmicChameleon on 2012-04-06
Well in response to this thread here:
[http://ubuntuforums.org/showthread.php?t=1933725&highlight=poulsbo](http://ubuntuforums.org/showthread.php?t=1933725&highlight=poulsbo)

I thought I'd document my wife's shot at Ubuntu from a longtime Windows perspective. 

Her background: 
Windows user. Typical "It doesnt work, run windows update!" mentality. 
She can change a hard drive and map a network share, but she can't do serious troubleshooting without calling out for help. If something is broken she'll try ctrl-alt-delete and then go for the old 5 second button push reboot. 

The target:
Dell Mini 10 with Poulsbo gma500. I bought two of these little easily pocketable machines for us back in 2010 and they've been great for her emailing and internetting (shopping) and for my slipping it into and out of my jacket for "situational awareness" :D

The install:
I let her do this herself, from start to current and I'll keep a running log. She might even take over herself after a while. She's installing Ubuntu because, as she put it, "It's what came up as the best for newbies when I searched Bing" (the article referenced Karmic and was dated 2009, lol)

The distro:
Ubuntu Precise, because it's on the main page although it's labeled Beta 2 which made her nervous. 

Begin:
First step, download the distro. And that's where the first bit of nervousness begins. She clicks on "Testing, testing..." and it brings her to the wiki Introduction the beta. 
"It sounds like it's not fixed yet. Where's the download link?"
She scrolls down without reading anything on that page AT ALL
and clicks on the download link and again she's met with choices that make no sense to her. 

The link leads to [http://mirrors.rit.edu/ubuntu-releases//precise/](http://mirrors.rit.edu/ubuntu-releases//precise/)

The choices (as you know) begin with .htaccess and end with templates. 

Being a windows user she pauses at the lack of direction and finally clicks on HTaccess. Her thinking is that she has to download everything on that page. 

Here I intervene and tell her she needs to pick something with an ISO extension. She looks at all of them and clicks on AMD Desktop. I intervene again and tell her she has an intel processor so she needs something to fit that. Already I've offered her more advice that I intended. :(

She finally chooses ubuntu-12.04-beta2-desktop-i386.iso.

Download is 30 mins. Stay tuned.

---

### Post by dontquoteme on 2012-04-06
lol, keep us updated.

Bet she's better with curlings tongs than you are. :)
Tell her AMD is equivalent to "Babyliss" and Intel is her "GHD's" and she'll get the hang of it without further explanation. ;p

---

### Post by grahammechanical on 2012-04-06
May I respectfully add that amd64 runs on Intel processors. Yes, it do.

It is time the labels were made clearer. 

i386 = 32bit operating system for 32bit processors both Intel and AMD. 

amd64 = 64bit operating system for 64bit processors both Intel and AMD.

The i386 will run on a 64bit processor as well as an 32bit processor but the amd64 will only run on a 64bit processor.

I had to work all that out when I was a sheepie and I chose Ubuntu for the same reason as your wife. I did  a lot of reading in Linux magazines. I installed on a blank hard disk. I certainly was nervous. I still get nervous when I do partitioning.

Regards.

P.S. When it is all installed show you wife this page:

[http://wiki.ubuntu-women.org/](http://wiki.ubuntu-women.org/)

---

### Post by Elfy on 2012-04-06
> I had to work all that out when I was a sheepie and I chose Ubuntu for the same reason as your wife. I did a lot of reading in Linux magazines. I install on a blank hard disk. I certainly was nervous.Another of those here.

---

### Post by Elfy on 2012-04-06
> **KarmicKarmicChameleon said:**
> ..
Begin:
First step, download the distro. And that's where the first bit of nervousness begins. She clicks on "Testing, testing..." and it brings her to the wiki Introduction the beta. 
"It sounds like it's not fixed yet. Where's the download link?"
She scrolls down without reading anything on that page AT ALL
and clicks on the download link and again she's met with choices that make no sense to her. 

The link leads to [http://mirrors.rit.edu/ubuntu-releases//precise/](http://mirrors.rit.edu/ubuntu-releases//precise/)

The choices (as you know) begin with .htaccess and end with templates. 

Being a windows user she pauses at the lack of direction and finally clicks on HTaccess. Her thinking is that she has to download everything on that page... A read of the page might have found the download button - which leads simply enough to a few simple choices - one more click and a big orange download button ;)

She did after all choose the development route - it should be harder :)

---

### Post by KarmicKarmicChameleon on 2012-04-06
> **dontquoteme said:**
> lol, keep us updated.

Bet she's better with curlings tongs than you are. :)
Tell her AMD is equivalent to "Babyliss" and Intel is her "GHD's" and she'll get the hang of it without further explanation. ;p

LOL! She said, "Oh! Now I get it!" 


> **grahammechanical said:**
> May I respectfully add that amd64 runs on Intel processors. Yes, it do....

P.S. When it is all installed show you wife this page:

[http://wiki.ubuntu-women.org/](http://wiki.ubuntu-women.org/)

I wasn't aware. Thanks!
And she says thanks for the link. She'll check it out when the experiemtn is over (at my recommendation so as not to move beyond her newbie status. I'm a tyrant, arne't I?)

> **forestpiskie said:**
> Another of those here.

I suspect many more new users are actively *trying* to migrate from Windows but the learning curve is causing many casual users to give up. Welcome to the club :) 
Hopefully this will help both developers (Please do read this) and newbies alike to make an easier transition.

> **forestpiskie said:**
> A read of the page might have found the download button - which leads simply enough to a few simple choices - one more click and a big orange download button ;)

She did after all choose the development route - it should be harder :)

She chose the huge "Download Now" button displayed prominently on the Ubuntu homepage, as any new user would do. She did not intentionally choose a development route, but rather was herded in that direction by the website - ala' Sheeple mode. Perhaps this should be addressed?



Thanks for the replies guys and girls. We love feedback!

Here's our next step:

Download finished, we moved to putting the ISO on a jump drive. Bing again told her that Universal-USB-Installer was the option to choose for this so she downloaded and used it to create a bootable jump drive on a 16gb drive. 

She moved (ok, she litterally RAN) the jumpdrive to her laptop and shoved it into the slot. She hit the button and Tada! It springs to life!

Then a black screen with a blinking cursor. Her face falls. "Is that normal?"

Twenty seconds later the Ubuntu loading screen arrives and she lights up again, only to be followed by red text that moves too fast to read. 

Then : Firmware file "b32/unicode...." text hits the screen and she thinks for sure it's broken. It blinks a few times, then the screen gets cut in half. 

She describes it, "It's a really pretty purple, but it looks like it's only using half of the screen." She wiggles the mouse and it artifacts. 
Just then the Install or Try screen pops up. She runs the mouse over it and it artifacts more (see pic) but she makes it to the partially exposed Install button and clicks. 

[IMG]http://i44.tinypic.com/5frhu1.jpg[/IMG]

---

### Post by KarmicKarmicChameleon on 2012-04-06
She finds that she can scroll to the bottom of the screen and it'll return the cursor to the top of the screen. This way she can "paint" the cursor over everything to make the only bit of screen showing either show the intended bottom or the intended top. 

"Is this going to hurt my computer?" she asks. 
She's really nervous at this point and says, "I'd probably quit right here if it was just me."

So there you go guys. Sheeple (no offense honey!) would quit the first time the "pretty" quits on the screen. Having prepared for this, I tell her we can still see half of the screen. Let's try to keep going as best as you can. 

She can see the install screen showing "Is connected to the internet" and "Download updates while installing". She also sees "Install 3rd party plugin" that (thankfully) tells her in plain english that it allows her to play MP3s. 

She clicks the MP3 button checkbox first with a "heck yeah" and then clicks the "Download updates" box. "That's like Windows Update, right?"
She clicks Continue.
No more hiccups through the install (aside from only showing half the screen) until she gets to the timezone and language choices. 
See pic:

[IMG]http://i40.tinypic.com/21oo41t.jpg[/IMG]

---

### Post by KarmicKarmicChameleon on 2012-04-06
A better pic:

[IMG]http://i44.tinypic.com/dox5wg.jpg[/IMG]

---

### Post by xyzzyman on 2012-04-06
That screen is filthy... She clearly has been too busy in the kitchen lately. Good man! :lolflag:

---

### Post by KarmicKarmicChameleon on 2012-04-06
She discovered that she can use the cursor and "paint" the top of the page on the screen or run it through to the bottom and it'll reappear on the top, which allows her to paint the bottom of the display on the screen that is used. That sounds confusing, right? 
She seemed delighted when she figured this out so I let her continue...

Retrieving updates commenced as normal, albeit in half screen. This made the "previews" slideshow a little awkward:
[IMG]http://i41.tinypic.com/17vh1v.jpg[/IMG]

---

### Post by KarmicKarmicChameleon on 2012-04-06
> **xyzzyman said:**
> That screen is filthy... She clearly has been too busy in the kitchen lately. Good man! :lolflag:

LOL She had a fit about it and cleaned it for the next pic. She was mortified. I told her she needed to stop doing her hair (hairspray) when she listens to music on it.

---

### Post by Elfy on 2012-04-06
> **KarmicKarmicChameleon said:**
> LOL She had a fit about it and cleaned it for the next pic. She was mortified. I told her she needed to stop doing her hair (hairspray) when she listens to music on it.

:lol:

---

### Post by KarmicKarmicChameleon on 2012-04-06
She was quite a trooper I think, having to paint the screen with the cursor to get it installed. It did crash though with the following screen:

[IMG]http://i42.tinypic.com/jpwx9e.jpg[/IMG]


She said, "At least it got sent to the developer and maybe they'll fix it so it works right. That's good." But she does want to give it another go so we rebooted and started the install again....

I think I mentioned that rebooting is her go-to when something goes wrong with Windows :)

EDIT: Forgot to add that getting her set up with a launchpad account through the half-screen was fun. :) She did submit the report though, after which Ubuntu booted off of the jump drive but didn't say "You're running on the jump drive" so she thought it had fixed itself! AHHH!

We then rebooted to do another attempt at installation.

---

### Post by Elfy on 2012-04-06
I'd make sure the burn and download are good first.

[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

You can get the md5sum from wherever you ended up downloading from :)

---

### Post by KarmicKarmicChameleon on 2012-04-06
> **forestpiskie said:**
> I'd make sure the burn and download are good first.

[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

You can get the md5sum from wherever you ended up downloading from :)

Exactly, and we did although she said she would never have thought to do so. I think we can rule out a newbie attempting iso verification. 

Her bugtracker link is here:
[https://bugs.launchpad.net/bugs/975408](https://bugs.launchpad.net/bugs/975408)

---

### Post by KarmicKarmicChameleon on 2012-04-06
The next attempt ended exactly the same. She says she's done until "they get it fixed". She did mention that she'd watch for an email from the bugtracking group to see if it gets fixed. 

From her: "Ask them if they know what I should do to fix it on the forums, because I might do that if I had nothing else to do."

So I guess it's out there. Anyone have any ideas?

---

### Post by Elfy on 2012-04-06
To be frank I would try 

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

It might be that using a kernel boot option might help but we've nothing to go on - other than it's a polished up and cleaned Dell :p 

If you want to try then 

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Have fun :)

---

### Post by xyzzyman on 2012-04-06
Maybe this shows an official Ubuntu Windows app that downloads the correct ISO (With resume support), verify the MD5 and then make a bootable USB with it?

---

### Post by cpatrick08 on 2012-04-06
try one of the daily builds at [http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/) and see if that works better

---

### Post by mcellius on 2012-04-06
I got that same error message and found that if I chose Try Ubuntu I could then install the Precise beta by choosing the Install button from the desktop; I was never able to get it to work by choosing "Install Ubuntu" from that screen that gives both options.

---

### Post by KarmicKarmicChameleon on 2012-04-06
I'm back! I hate it when work gets in the way of experiments. Grr!

Moving forward, we have to remember that the average person would have entirely **QUIT UBUNTU ALTOGETHER BEFORE NOW**. At this point we're moving with the idea that the person is rather dedicated to leaving Windows or has some sort of OCD lol. Or a love for torture :)

The option mcellius suggested (she says, "Thank you!") gave her a full screen. Her first thought was "The start menu's on the left side. That's different." 
Second thing she said was, "It's pretty though."

[IMG]http://i44.tinypic.com/24w7ua9.jpg[/IMG]

She started an install from that menu and it seemed to have completed perfectly, however at boot after the installation she was greeted with a black screen. She waited a few minutes and  still no go. So off she went to the daily build (Thanks cpatrick08!). 

Stay tuned...

---

### Post by KarmicKarmicChameleon on 2012-04-06
Well the "daily build" failed install with this message:

[IMG]http://i39.tinypic.com/34xqgqq.jpg[/IMG]

She typed "Default" and "UI" and gave up without researching it further.

---

### Post by nm_geo on 2012-04-06
> **KarmicKarmicChameleon said:**
> Well the "daily build" failed install with this message:

[IMG]http://i39.tinypic.com/34xqgqq.jpg[/IMG]

She typed "Default" and "UI" and gave up without researching it further.

That sure looks like a badly copied/formed iso on the flash drive.  It has been entirely to long ago for me to remember how those windows usb-creator work with current daily builds?  Okay, I guess I could test that myself as I still have a XP partition on my Dell laptop.

---

### Post by NHclimber on 2012-04-06
Wow! I have really enjoyed reading this thread. Thanks for sharing.

---

### Post by KarmicKarmicChameleon on 2012-04-06
Thanks NHClimber. She's getting pretty frustrated at this point. I've started a re-download of the current 04/06/2012 build. 
We'll try again later tonight after she's gotten a second wind.

---

### Post by nm_geo on 2012-04-06
> **KarmicKarmicChameleon said:**
> Thanks NHClimber. She's getting pretty frustrated at this point. I've started a re-download of the current 04/06/2012 build. 
We'll try again later tonight after she's gotten a second wind.

i did create a daily build of the Lubuntu amd64 with unebootin earlier and fired it up and it did come up live.  I did not install as I had other things going on.  Perhaps Lubuntu might serve her better not as pretty LOL but works really well on low resources.

---

### Post by iowabeakster on 2012-04-06
Thanks to you and your wife!  This thread makes me smile.

I still consider myself a ignoramus with linux (although my first experiences were 12+ years ago).  I would guess that I am not really a noob anymore, but an intermediate "user" at this point.  I should be ashamed that I am not more proficient.  

With a windows crash about 2-3 years ago, my wife and I became full time Ubuntu (Xubuntu) users (single boot).  I do most of the "linux stuff" (aka: keep system working properly), she is a basic "user".  She loves it.  She insists on having linux/Ubuntu installed on her new laptop (shipping as we speak).  It'll be dual-boot, at least for a few months, until 12.04 matures.

I am sure my wife would have similar difficulties if I weren't involved.  With me keeping everything working, she has loved being a basic user with Xubuntu.  I have to say that my job keeping the system working is remarkably easy for me now.  Anymore, I just need to recompile the module for the proprietary video driver with every update of the kernel and X server.  Occasionally, I might need to hunt down some source code through synaptic if the update didn't include it... then just go through the routine of shutting down the X server and sh the video driver installer script.  Which at this point I can do blindfolded.   :confused:

My brother introduced and helped me with my early linux use (and still my major support, if needed).  It was him personally, that allowed me to get to this point.  Without him, I would never been able to make the jump to being a full-time single-boot linux user. 

Now, I've got to support my wife's linux use.  Yeah, if Linux/Ubuntu is to ever be an everyday-everyuser OS on the PC... noob support really needs to be addressed.  Until then, linux is just going to be for geeks.  And I mean "geeks" as a truly sincere compliment.

Good luck to you and your wife.  I love the experiment...and thread.

(don't let her get too irritated...)

---

### Post by kurt18947 on 2012-04-07
I'm not sure if this is an issue or not but if the "universal installer" is the same as what I tried, I didn't have much luck with it.  I've stuck with Unetbootin - works in Windows & Linux.  She & you seem to be going about it right.  Don't mess with a machine that *has* to work in 6 hours and don't take it too seriously.

---

### Post by BigCityCat on 2012-04-07
I never have any luck with the installer with beta releases. I have been able to get it to work with the alternate install cd every time. It's not much different.

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

---

### Post by BigCityCat on 2012-04-07
I like to go here for inspiration.

[http://www.sevenforums.com/system-security/](http://www.sevenforums.com/system-security/)

---

### Post by ubuntu27 on 2012-04-08
Hi KarmicKarmicChameleon! ):P

I like your thread and posts. I'll pray that your experiment will be sucessfull.


By the way, where are you downloading the ISO to? Is it a Windows computer or Ubuntu (or other Linux)?

If you are using Ubuntu, you can install [zsync]("apt://zsync") to allow you to download the the changes in iso automatically so you don't have to download a new iso again. In another words zsync compares that current iso that you have with the one on the server, if the server is newer (there are changes), then it will start downloading the different parts and put it in your iso. 
You get to save time, power, electricity, and money :guitar:

here are guides on how to use zsync:

[https://help.ubuntu.com/community/ZsyncCdImage](https://help.ubuntu.com/community/ZsyncCdImage)

[http://drivard.com/2012/01/13/use-zsync-to-download-ubuntu-latest-build-iso-file/](http://drivard.com/2012/01/13/use-zsync-to-download-ubuntu-latest-build-iso-file/)

[https://www.youtube.com/watch?v=5KDszldKO8w](https://www.youtube.com/watch?v=5KDszldKO8w)

 

Like everyone says, you should use the Daily Live ISO, instead of Beta since Beta is already "outdated".

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)


If your computer is just a few years old, then it most likely supports 64-bit. So you might want to try the AMD64 one.



Good luck!

---

### Post by continuous on 2012-04-09
Thanks for the blow by blow account...I really cringed when she managed to get the end of the install only to be confronted with gobbledegook!

To be fair, installing windows is never that easy either - especially if you no longer have the "drivers" cd that makes the video work properly, the network work, sound etc. 
Get her to download windows 8 and install that to give her a bit more of a perspective. I'm a little surprised you got her to try the beta2 version - her initial concern was indeed warranted.

Anyhow, such is software. I hope she perseveres, succeeds and really takes ownership of her machine - that is where most of us came from remember?

---

### Post by SirWeazel on 2012-04-10
I have this same netbook.... It is tougher than one would think to get this ubuntu or any linux distro fully working on it. You are suffering from the infamous GMA500 video problem. There is a thread dedicated to this issue and it grows so fast trying to read it all is like trying to read the Harry Potter series in an hour. I've got some links to the important parts that you will need. I'll try and point you in an easy direction. There is a custom iso of ubuntu 11.10 that installs nicely without a problem (only unity 2d works correctly though). I'll post back when i find my thread with references.

---

### Post by SirWeazel on 2012-04-10
Check out:
[http://ubuntuforums.org/showpost.php?p=11427075&postcount=13](http://ubuntuforums.org/showpost.php?p=11427075&postcount=13)

and probably might help to view the whole thread also

[http://ubuntuforums.org/showthread.php?t=1863615](http://ubuntuforums.org/showthread.php?t=1863615)

---

