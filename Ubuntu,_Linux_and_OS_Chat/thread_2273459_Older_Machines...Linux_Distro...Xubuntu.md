---
title: "Older Machines...Linux Distro...Xubuntu"
date: 2015-04-13
forum: Ubuntu, Linux and OS Chat
---

### Post by SolomonMan on 2015-04-13
All,
I have a 1.8 Ghz AMD machine with currently 1GB of Memory (single stick) and 40 GB drive. It has a DVD reader, a CDRom Burner, and a few USBs ports in it. I have 2 additional 1 Gig sticks of Memory for the machine but will need to confirm usability (pair ups etc).

I also have this relic Pentium III dual processor (Tyan Server Board) with a Gig of Memory (maxed out) and 160 GB Drive/CDRom/DVD/USB.

Both machines have a similar Wireless Cards ([COLOR=#000000][FONT=Verdana]TP-LINK| TL-WN751ND R)[/FONT][/COLOR]

I am looking to place these old machines (relics?), if possible, out in my Garages for use as the following;

1) YouTube Videos
2) Mp4 videos - Usually just Rips of videos I currently Own (Mostly Auto related stuff)
3) Ability to use Pandora/Spotify.
4) USB functionality
5) Maybe even use the  SiliconDust HDHomeRun Dual HDHR4-2US HD Digital Box that I use with my other home machines. (Not tried it in Linux as of yet)

So I have been trying Xubuntu and I like the interface but I have not been able to get either machine to work well with YouTube. (Not tried the MP4/Pandora/HomeRun) Also the USB functionality does not seem to cooperated at all on the Pentium III which is probably a configuration issue on my end.

Trying to cut my loses here (time wise) with other peoples experiences..

My question first is the Pentium III even powerful enough?  Pentium III seems to run Xubuntu well enough and will browse the web but YouTube is not even possible (usually firefox just dies in Youtube/or video is extremely lagging/choppy). Chrome is not supported on the Pentium III machine at all.  I have consider Chromium but not sure the route for flash...(pepperflash)?

Which Distro would you suggest for the above needs and what packages do I need to have installed to get the above working?

I have been a user on and off of Linux distros since 1998 but lately have been Ubuntu/Xubuntu focus.

Thanks for the help,
Chris

---

### Post by roger_1960 on 2015-04-13
Hi

I suspect that you have an issue with one or both machines not supporting SSE2 instructions.  If they do not, you cannot run Chrome above version 18 or chromium above version 34.  Also you have to use Flash player 11.1 or below.

Run this

> grep -w sse2 /proc/cpuinfo 

If it returns nothing then your cpu does not support SSE2

You laptops likely only have USB 1.0 ports (very slow)

To be honest I think you are trying to run modern multimedia with kit that is just too old :( of course someone may know how :)

Roger

---

### Post by grahammechanical on 2015-04-13
Do you still have Windows installed on those machines? Out of curiosity, how well would those Windows machines carry out the tasks that you wish to do? It seems to me that you want to do some video intensive stuff. How powerful are the graphic adapters?

Regards.

---

### Post by mörgæs on 2015-04-14
If sse2 is a problem there are some workarounds in the Old Hardware link in my signature.

---

### Post by SolomonMan on 2015-04-14
All,
Nope Windows is not on the machines any longer. 
 
I am almost positive it does not have SSE2 but I did not try;
[COLOR=#000000][I]grep -w sse2 /proc/cpuinfo

[/I][/COLOR]As I am currently not at my house garage. I did look up (cpu-upgrade.com) the faster CPU motherboard combo as I bought it on Ebay a while back (over a year ago) and still had it in my email history.

The page says the processor is MMX/SSE.

The Pentium III I know does not supports SSE2. 

So with this all in mind I picked up today a [Hp Compaq DC5800 Computer MT Core 2 Duo E7400 2.80 Ghz w/80 GB HD/2 GB RAM/DVDRW]("http://www.ebay.com/itm/131482796674?_trksid=p2057872.m2749.l2649&ssPageName=STRK%3AMEBIDX%3AIT"). I have the extra ram laying around to bump it up to 4 Gig. The price of this used machine was about the price of a Raspberry Pi. I am still coping with the dirt cheap prices recently I have found PC hardware for locally (19 inch used flat screens $10, 17 inch 7$, this PC ). I have been in IBM PCs since the 8088 processor was king not to mention the old 8 bit stuff I played with as a kid. 

Anyways I have a laptop with similar specs  to the [Hp Compaq DC5800]("http://www.ebay.com/itm/131482796674?_trksid=p2057872.m2749.l2649&ssPageName=STRK%3AMEBIDX%3AIT") that runs everything in Windows so I will assume this new to me machine will accomplish the garage machine issue. I am actually tempted to pick up another machine for the other garage but this was the fastest they had in stock. They had 2.4 and 2.6 Duos for less money...I wonder if they would be a worthwhile investement? They had one missing a hard drive that was considerably cheaper and I have a SSD 120 Gig laying around which would be a good pairing....

I will read the mentioned  Bringing the Old hardware back to life link as both of these old machines first mentioned have 1.2 Gig Floppies and 1.44 Floppies which I have still have a Tote or two of that need to be read and archived. Also the machines first mentioned have era correct video cards. I believe the Pentium III has a 256 Meg Dual DSub Video card. I believe the 1.8 GHz machine had a 1 GB intel card. If not I have a few video cards laying around that are 1Gb. 

I appreciate all the help!
Chris 





[COLOR=#000000][/COLOR]

---

### Post by Mike_Walsh on 2015-04-14
If you still want to try and bring the PIII back to useful life with Linux, then 'Puppy' Linux might be worth a try...

There's over 400 different versions of Puppy extant...many of which are remasters that have been put together for specific purposes. Have a look here:- 

[https://archive.org/search.php?query=collection%3Apuppylinux&sort=-publicdate](https://archive.org/search.php?query=collection%3Apuppylinux&sort=-publicdate)

Several of these have been specifically designed for PIII-era hardware, and even earlier.


Regards,

Mike.

---

### Post by SolomonMan on 2015-04-14
All,
I have had a machine with Puppy Linux before and I had some issue with Flash (had to be version 9.X) and sound not working. 

This was for an old machine for my 6 year old daughter.

I never traced the sound issue down...The flash version was not a big issue.

I will take a look at puppy again. I tried Antix on the 1.8 machine and it did not boot but went to the boot option screen and after selection.... sat saying 100% Loaded.

Thanks
Chris

---

### Post by Mike_Walsh on 2015-04-14
> **SolomonMan said:**
> 

I never traced the sound issue down...The flash version was not a big issue.



Hmm. In fact, the sound issue is still an ongoing argument, between the proponents of PulseAudio, and those who prefer AlsaMixer..! Bearing in mind your lack of SSE2's, have a look at Wary. It's specially designed to work with REALLY old hardware; but even so, you might be better off with something like AnitaOS....or even LegacyOS. That one is designed for hardware of the mid- to late 1990's.....the Pentium II/III generation.

BTW: I'm possibly not a good judge of where the threshold lies for the 'true' Puppy distros (those that were designed to be absolutely minimal, though feature-packed...and designed for the hardware standards of 12-13 years ago). Although my machine is 10 years old, it was 'top-spec' for its time, and over the last couple of years has been seriously upgraded...not the kind of machine Barry Kauler originally conceived the idea of 'Puppy' for!


Regards,

Mike.

---

### Post by SolomonMan on 2015-04-15
All,
As luck would have it...Had the 1.8 Running in the office for the past few days and the thing went down. 

No power.

Gotta do the steps;

[LIST]
[*]Plug the power supply into the wall.
[*]Find the big 24 pin connector that connects to the motherboard.
[*]Connect the GREEN wire to the adjacent BLACK wire.
[*]Check if the power supply's fan starts up.
[/LIST]

Honestly I am going to do the above just to see how much I am throwing out....If not all of it.....LOL!

Thanks again,
Chris

---

### Post by Tar_Ni on 2015-04-16
> **SolomonMan said:**
> My question first is the Pentium III even powerful enough?  Pentium III seems to run Xubuntu well enough and will browse the web but YouTube is not even possible (usually firefox just dies in Youtube/or video is extremely lagging/choppy). Chrome is not supported on the Pentium III machine at all.  I have consider Chromium but not sure the route for flash...(pepperflash)?

I think a Pentium III is too weak to even run Xfce (Xubuntu) properly. I would suggest LXDE (Lubuntu) instead for optimal performances on these specs.

As for advanced internet services such as Youtube, it is recommended to have at least 1GB of RAM. Otherwise, lags are to be expected. The Youtube website is ressource-hungry.

But what you could try is using VLC Media Player or SMPlayer (available in the 'Buntu Software Center) to play Youtube videos locally on your computer. They both support network streaming for Youtube so in this way you will avoid going through flash player at all or rely on the HTML5 online Youtube player to play your videos. You only need the URL. On a personal note, I find that the quality is usually better this way on the average hardware.

Edit: You might also want to try the Midori browser instead of Firefox on your old Pentium III. It's a very lightweight browser (also available on the 'Buntu Software Center) that can help you browse the web without memory hog.

---

### Post by monkeybrain20122 on 2015-04-16
> **Tar_Ni said:**
> I think a Pentium III is too weak to even run Xfce (Xubuntu) properly. I would suggest LXDE (Lubuntu) instead for optimal performances on these specs.

As for advanced internet services such as Youtube, it is recommended to have at least 1GB of RAM. Otherwise, lags are to be expected. The Youtube website is ressource-hungry.

But what you could try is using VLC Media Player or SMPlayer (available in the 'Buntu Software Center) to play Youtube videos locally on your computer. They both support network streaming for Youtube so in this way you will avoid going through flash player at all or rely on the HTML5 online Youtube player to play your videos. You only need the URL. On a personal note, I find that the quality is usually better this way on the average hardware.

Or, [http://isebaro.com/viewtube/?ln=en](http://isebaro.com/viewtube/?ln=en)

Install gecko-mediaplayer, install the greasemonkey addon for FF, restart FF, go to the website above to install the Viewtube script. Now Youtube videos (as well as other supported sites) will play in a gnome-mplayer window. I think OP plays videos in 720p if available, so OP may be should switch to lower resolution if that doesn't work.

HTML5 actually doesn't work much better than flash on old hardware, still very resource hungry. Chrome is more efficient in using html5 because it supports hardware accel on reasonably recent graphic card but doubt that it would work on OP's machine. Viewtube is optimal for OP's condition IMO

(A similar but less convenient way would be to use youtube-dl + mpv to stream videos on Youtube and other supported sites either with command line or using Smplayer as front end, but it may be a turn off to have to open the web browser and go to the video site just to copy the url instead of click and play like Viewtube, this method however allows streaming 1080p and even higher on youtube, but that would probably be moot for OP)

---

### Post by Tar_Ni on 2015-04-16
> **monkeybrain20122 said:**
> Install gecko-mediaplayer, install the greasemonkey addon for FF, restart FF, go to the website above to install the Viewtube script. Now Youtube videos (as well as other supported sites) will play in a gnome-mplayer window. **I think OP plays videos in 720p if available, so OP may be should switch to lower resolution if that doesn't work.**

I doubt you can watch 720p videos on a Pentium III. :-\"

Here's what I would personally do, quite simply:

- Wipe off the hardrive and install Lubuntu 14.04.2

- Install the ligthweight Midori Browser (you can then get Adobe Flash 11.2 if needed at all). Midori works well with Spotify and Pandora.

- Download the Lubuntu restricted extras (for video codecs)

-Install SMplayer to search for and watch Youtube videos as well as support for Mp4 videos as the OP mentions.

You then have an old' box to do some limited computing but that's good Linux recycling.

---

### Post by monkeybrain20122 on 2015-04-16
> **Tar_Ni said:**
> I doubt you can watch 720p videos on a Pentium III. :-\"
.

That's why I said change the setting in Viewtube to lower resolution (standard resolution should work, if not switch to low) No need for flash or HTML5 (believe me HTML5 is just as painful as flash on that machine), and no need to cut and paste url. :p

 Don't think it will work with Midori. You don't really need a 'light weight' browser provided that you don't open many tabs, don't visit pages with lots of images/animations (or install NoScript), install adblock, and disable flash (or set it to ask to activiate)

---

### Post by Tar_Ni on 2015-04-16
> **monkeybrain20122 said:**
> You don't really need a 'light weight' browser provided that you don't open many tabs, don't visit pages with lots of images/animations (or install NoScript), install adblock, and disable flash (or set it to ask to activiate)

There is some advantages of using a stripped down - yet fully functional - browser like Midori on (very) old hardware. For one: performance. Midori is very fast (webkit engine) and easy on ressources. It's my #1 choice for browsing with such hardware. You can deal with quite a few open tabs with no problem at all on a PC with less than a gig of RAM. Besides, it has it's own built-in adblocker (that can be disabled) so you don't need any more extensions.

I think Midori is underrated, though I wouldn't necesserely recommend it for PCs that can handle more, the truth is, it can do most of the things that that other big browers do.

Of course, that doesn't mean Firefox or Chromium, 'can't do the work' to some extent but using Midori on a Pentium III with 512MB-1GB RAM will definitly lower your memory footprint and improve performance.

> **monkeybrain20122 said:**
> That's why I said change the setting in  Viewtube to lower resolution (standard resolution should work, if not  switch to low) No need for flash or HTML5 (believe me HTML5 is just as  painful as flash on that machine), and no need to cut and paste url. [IMG]http://ubuntuforums.org/images/smilies/icon_razz.gif[/IMG]

You don't need to cut and past Youtube URL with SMplayer, you can search them with the SMTube function. I would recommend it before VLC in this case, so you don't need to open your browser at all (hence lowering RAM usage).

[http://smtube.sourceforge.net/](http://smtube.sourceforge.net/)

---

### Post by monkeybrain20122 on 2015-04-16
Yes, smtube is a great Youtube browser. But Viewtube works also for other popular sites like Dailymotion and Vimeo, and some porn sites apparently (honestly never tried them :)) So OP should have both.

---

### Post by mattharris4 on 2015-04-17
> **Tar_Ni said:**
> There is some advantages of using a stripped down - yet fully functional - browser like Midori on (very) old hardware. For one: performance. Midori is very fast (webkit engine) and easy on ressources. It's my #1 choice for browsing with such hardware. You can deal with quite a few open tabs with no problem at all on a PC with less than a gig of RAM. Besides, it has it's own built-in adblocker (that can be disabled) so you don't need any more extensions.

I think Midori is underrated, though I wouldn't necesserely recommend it for PCs that can handle more, the truth is, it can do most of the things that that other big browers do.

Of course, that doesn't mean Firefox or Chromium, 'can't do the work' to some extent but using Midori on a Pentium III with 512MB-1GB RAM will definitly lower your memory footprint and improve performance.

You don't need to cut and past Youtube URL with SMplayer, you can search them with the SMTube function. I would recommend it before VLC in this case, so you don't need to open your browser at all (hence lowering RAM usage).

[http://smtube.sourceforge.net/](http://smtube.sourceforge.net/)

I actually installed Midori on my P4 3.0GHz desktop computer with 3.2GB of usable RAM a while back and can confirm that it is much less resource-hungry (according to my task manager at least 80% less compared to Firefox and Chrome in a worst-case scenario).  However, in my limited use some features of websites did not work as designed.  For example pictures on newspaper sites where you click an arrow to advance to the next picture did not work as designed, each picture had to be displayed in a more cumbersome manner and videos did not play at all.  However, if all you are doing is reading text pages it may be a good option for older computers (obviously not applicable in this case).

Tar's assertion that Midori will run with only a gig or less RAM used including background and OS functions is only true with lighter OSes, though.  With Edubuntu running at idle will take up 1100MB of RAM by itself, SFGate.com running with 7-8 tabs open will bump that to about 1300MB using Midori and about 2200MB using Firefox or Chrome/Chromium.  I haven't tried Midori on my Lubuntu laptop (it is a year old or so but it has a weak power-saver processor that is slow IMO, it runs better with a lighter OS even though it has 4GB of RAM) but extrapolating these numbers to its usual 300MB at idle I would guess Midori would run at about 500MB whereas Firefox runs about 1200MB assuming Midori works with LXDE in a similar manner as it does with Gnome.

---

### Post by Tar_Ni on 2015-04-17
> **mattharris4 said:**
> I actually installed Midori on my P4 3.0GHz desktop computer with 3.2GB of usable RAM a while back and can confirm that it is much less resource-hungry (according to my task manager at least 80% less compared to Firefox and Chrome in a worst-case scenario).  However, in my limited use some features of websites did not work as designed.  For example pictures on newspaper sites where you click an arrow to advance to the next picture did not work as designed, each picture had to be displayed in a more cumbersome manner and videos did not play at all.  However, if all you are doing is reading text pages it may be a good option for older computers (obviously not applicable in this case).

When was the last time you used it? Because Midori has improved in the last 2 years of developpement. My last experience with it was 3 months ago on a friends's old Dell Dimension desktop and I encountered none of the issues you mentionned. The Adobe Flash 11.2 plugin works perfectly with it and I could watch just about anything flash-related as well as HTML5.

Here is a FAQ that gives solutions to just about every problem one might accounter with Midori:

[http://midori-browser.org/faqs/](http://midori-browser.org/faqs/)

> **mattharris4 said:**
> Tar's assertion that Midori will run with only a gig or less RAM used including background and OS functions is only true with lighter OSes, though.  With Edubuntu running at idle will take up 1100MB of RAM by itself, SFGate.com running with 7-8 tabs open will bump that to about 1300MB using Midori and about 2200MB using Firefox or Chrome/Chromium.  I haven't tried Midori on my Lubuntu laptop (it is a year old or so but it has a weak power-saver processor that is slow IMO, it runs better with a lighter OS even though it has 4GB of RAM) but extrapolating these numbers to its usual 300MB at idle I would guess Midori would run at about 500MB whereas Firefox runs about 1200MB assuming Midori works with LXDE in a similar manner as it does with Gnome.

If your hadware can work great with Ubuntu, Xubuntu or Lubuntu (so if you can claim at least 1GB of RAM and a Pentium 4 or higher) I would probably not recommend using Midori, at least not as primary browser. Clearly there are better choices. Where Mirdori is at it's best is dealing with old hardware and (very) limited ressources. I think it's an awesome alternative, that allows for decent mutli-tabs web browsing even on a 15 years old computer.

---

### Post by mattharris4 on 2015-04-22
> **Tar_Ni said:**
> When was the last time you used it? Because Midori has improved in the last 2 years of developpement. My last experience with it was 3 months ago on a friends's old Dell Dimension desktop and I encountered none of the issues you mentionned. The Adobe Flash 11.2 plugin works perfectly with it and I could watch just about anything flash-related as well as HTML5.

Here is a FAQ that gives solutions to just about every problem one might accounter with Midori:

[http://midori-browser.org/faqs/](http://midori-browser.org/faqs/)

If your hadware can work great with Ubuntu, Xubuntu or Lubuntu (so if you can claim at least 1GB of RAM and a Pentium 4 or higher) I would probably not recommend using Midori, at least not as primary browser. Clearly there are better choices. Where Mirdori is at it's best is dealing with old hardware and (very) limited ressources. I think it's an awesome alternative, that allows for decent mutli-tabs web browsing even on a 15 years old computer.

I installed and tried Midori mainly out of curiosity.  I actually tried it out about three weeks ago, the picture issue came up on the SFGate website.  I do see where it is a good option for those skirting the hardware minimums.  Admittedly I only played with Midori for an hour or so and did not attempt to diagnose the picture display and video issues.  I have Pepper Flash (which is updated once a month or so) as well as the very outdated Adobe Flash 11.2 installed on my computer (for what I do this is next to useless to me, hence the Pepper Flash install).

---

