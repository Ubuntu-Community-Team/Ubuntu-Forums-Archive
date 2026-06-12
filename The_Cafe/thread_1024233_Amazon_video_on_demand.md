---
title: "Amazon video on demand"
date: 2008-12-28
forum: The Cafe
---

### Post by wildman4god on 2008-12-28
I was checkin' in on amazon's video download service that was wondows only, and they now support mac os, why do I bring this up at a linux forum, well simply because I think this is a good indicator that they might eventually support linux as well. They already support linux for their mp3 download service and now that they have added mac os x to the list that means they are interested in os's other that windows so I am hoping that in the next few months their video service will be supported under linux. :)

---

### Post by MaindotC on 2009-12-22
Hey just fyi - this is a GREAT alternative to running Netflix in a VM.  They have some free titles you can watch during the holidays and it worked just fine in firefox for me.  I dunno if they have the same amount of titles.

---

### Post by wilee-nilee on 2009-12-23
The downloads are DRM protected as well, but I was able to get my one download into windows play in VLC or the W12 media player in W7 I forget which one though. The downloads also come with a caveat of Amazon removing access so any downloaded should be saved. I don't think you can burn these to a DVD either, so personally I would rather just buy the DVD it has generally been the same price as a download.

---

### Post by MaindotC on 2009-12-23
> **wilee-nilee said:**
> The downloads are DRM protected as well, but I was able to get my one download into windows play in VLC or the W12 media player in W7 I forget which one though. The downloads also come with a caveat of Amazon removing access so any downloaded should be saved. I don't think you can burn these to a DVD either, so personally I would rather just buy the DVD it has generally been the same price as a download.

Dude, I'm not trying to circumvent anything or break anyone's copyright.  It's $10/mo - it's not going to set me back much! LoL just leave them as they are and don't burn anything :D

---

### Post by wilee-nilee on 2009-12-23
> **strAlan said:**
> Dude, I'm not trying to circumvent anything or break anyone's copyright.  It's $10/mo - it's not going to set me back much! LoL just leave them as they are and don't burn anything :D

Did I say you were trying to circumvent anything? I was only commenting on my experience.

Edit: I didn't realize I had hit the quote button, I wasn't meant to be directed at your comments.

---

### Post by 3rdalbum on 2009-12-23
Amazon's MP3 service only supports Ubuntu 32-bit, and their video download service is probably only cross-platform because they use a DRM provider that supports the Mac OS.

---

### Post by MaindotC on 2009-12-23
> **3rdalbum said:**
> Amazon's MP3 service only supports Ubuntu 32-bit, and their video download service is probably only cross-platform because they use a DRM provider that supports the Mac OS.

That is absolute BS - I use 64-bit and it works just fine for me, both their video AND mp3!!

---

### Post by BigBaaadBob on 2010-01-09
> **strAlan said:**
> That is absolute BS - I use 64-bit and it works just fine for me, both their video AND mp3!!

Linux Mint Helena x64 (based on Ubuntu Karmic) fresh install: when trying to do VOD using Firefox the Amazon VOD screen just says "loading" with the moving dots forever.

So, I'd like to know how you got this to work 'cuz it sure doesn't for me.

---

### Post by sdowney717 on 2010-01-09
works fine, I just tried a free movie

I had to run a bazillion commands in terminal to get it show something:lolflag:

---

### Post by jdunn on 2010-01-10
Doesn't work for me.  I'm using Karmic 64-bit with the latest 64-bit flash player (10.0 r42)

---

### Post by MaindotC on 2010-01-10
Well I'm not a dev so I don't know how to help you.  Mine just works.  The only thing I could think of is maybe your hardware is an issue (I have a rather new system as you can tell via my sig) or I have packages installed that may enable it to work properly.  Maybe ubuntu-restricted-extras?

---

### Post by schefter on 2010-03-29
I'm running Karmic 64, Firefox 3.5.8, and Shockwave Flash 10.0 r45 and I tried two free videos, they both worked fine. I also have something called the Totem 2.28.2 plugin for streaming video, don't know if that makes a difference. This is great because, unless it breaks in the future, I now have a source for streaming video native to Ubuntu.

---

### Post by IceDoE on 2010-06-09
Figured I'd just put in that I just tried to use it on my Ubuntu 10.04  64-bit machine. Works  perfect, smooth and clean. I've only been able to  test the previews and free stuff, as I haven't tried to purchase just  yet. Seems pretty promising though.

I have put in some extra plugins previously for media stuff, but nothing  particularly special.

---

### Post by wilee-nilee on 2010-06-09
> **IceDoE said:**
> Figured I'd just put in that I just tried to use it on my Ubuntu 10.04  64-bit machine. Works  perfect, smooth and clean. I've only been able to  test the previews and free stuff, as I haven't tried to purchase just  yet. Seems pretty promising though.

I have put in some extra plugins previously for media stuff, but nothing  particularly special.

I don't think their media player which is what you need to play the downloaded movies, works in Linux.
[http://www.amazon.com/gp/video/ontv/player](http://www.amazon.com/gp/video/ontv/player)

Are you sure your referencing the correct thing, you can watch previews no problem and purchase a converter to plug the etho wire in to for tv, but the Amazon player wont work on Linux for rented or purchased movies.

---

### Post by pt123 on 2010-06-09
but it probably doesn't cover the Australia, like their mp3 service.

---

### Post by nanonils on 2010-07-04
Amazon on Demand worked fine for me until about 2 weeks ago. I'm using Lucid 64bit and AoD is only a gray field no matter what browser I use (Chrome, FF, Opera). All other flash content works flawlessly. Another 32 bit Lucid installation of mine has no problem with AoD.
I suspect this may have something to do with the recently reported discontinuation support for Flash for 64bit Linux? Anyone else having the same problem?

---

### Post by MaindotC on 2010-07-04
If you'd like to try a clean installation of Flash 64-bit then please check out [this thread](http://ubuntuforums.org/showthread.php?p=9362819) where the developer of [Flash-Aid](http://flash-aid-extension.blogspot.com/) helped me get flash installed properly after I decided to root around and mess up things.  It may require manually removing files in /var/lib as you'll see in post 8.  This may help the problem you're having because I've never had an issue watching AoD and I wish I could do more to help those of you who aren't having any success.

---

### Post by nanonils on 2010-07-04
Thank you very much!
I'm working my way through the guide you posted and it looks like I'm running a fairly recent version of flash and not the one that gave you problems. Anyways, I'll tinker a bit with it. Not much to loose I guess.
     
File: /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r53

---

### Post by nanonils on 2010-07-04
Too bad, the 32 bit version also doesn't work. Will now try to manually remove things, then try again.

Weired. I didn't even have a folder... /usr/lib/adobe-flashplugin/ but I do have a folder /usr/lib/flashplugin-installer

---

### Post by nanonils on 2010-07-24
And suddenly, after today's kernel upgrade to 2.6.32-24 AoD works flawlessly. Full screen was sometimes a little jittery but there was an an NVDIA related kernel installation listed and that seems to have fixed it.

---

### Post by Ric_NYC on 2010-07-24
Netflix vs Amazon on Demand


Netflix..........**Watch as many movies as you want... $8,99 a month!**


Amazon on Demand.... (????)

---

### Post by jdunn on 2010-07-28
> **Ric_NYC said:**
> Netflix vs Amazon on Demand


Netflix..........**Watch as many movies as you want... $8,99 a month!**


Amazon on Demand.... (????)

I'm not sure if Netflix video on demand will work on linux.  My understanding is, you need Silverlight and I don't think Moonlight can handle DRM'd video.  Same is true for Amazon and Adobe Flash for linux.

---

### Post by Ric_NYC on 2010-07-28
I think none of them works on Ubuntu.

---

### Post by Ric_NYC on 2010-07-28
I think the "free stuff" from Amazon on Demand works on Ubuntu.


Click on "Get this episode" (Watch for free)
[http://www.amazon.com/gp/product/B0012QTT4O?pf_rd_p=1266774522&pf_rd_s=center-6&pf_rd_t=1401&pf_rd_i=1000496831&pf_rd_m=ATVPDKIKX0DER&pf_rd_r=1608TRJHC1RFBFY935E6](http://www.amazon.com/gp/product/B0012QTT4O?pf_rd_p=1266774522&pf_rd_s=center-6&pf_rd_t=1401&pf_rd_i=1000496831&pf_rd_m=ATVPDKIKX0DER&pf_rd_r=1608TRJHC1RFBFY935E6)

---

### Post by utkjamie on 2010-07-29
Amazon on Demand used to work for me but now (as of Lucid?), videos no longer load. Can't figure out why since 1) these appear to be Flash-based; and 2) they display fine using the Google Chrome browser.

It seems like Firefox has become less useful under Lucid. I seem to have all sorts of problems with Firefox now.

---

### Post by 2893493 on 2010-10-20
Just wanted to chime in here.  

I am currently watching a rental of 'Splice' from Amazon Video on Demand on Firefox 3.6.8 on a 32-bit Debian Squeeze install and it works just fine.

It's not really the GNU/Linux way (you're supposed to rely on your distro to package this stuff up nicely for you), but if you are having trouble with the software from your distro being out of date, or not compiled with the features you want, you always have the option to go offroad and download the most recent stuff from upstream.

In the case of these two pieces of software, installation is pretty simple, as they are both from commercial vendors.

Get the newest release of Firefox for Linux from here:  [http://www.getfirefox.com](http://www.getfirefox.com)

Just get the tarball (.tar.gz) and unpack it somewhere.  Now you have the newest Firefox.

Then get the newest Flash player from here:  [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Just get the tarball (.tar.gz) and unzip it somewhere.  Put the libflashplayer.so in the plugins/ directory inside the Firefox install you unpacked.  Now you have the newest Flash player.

You can then run Firefox by cd'ing in to the directory where you unzipped it, and typing:

$ ./firefox

Anyway, Amazon VOD does seem to work on Linux, and that makes me happy.  Even though I like Netflix's "Watch it Now" better as a service and don't intend to unsubscribe (yet), I'll be diverting some cash to Amazon since they've actually rolled out a service that works on Linux.

Thanks, Amazon.

---

### Post by Ric_NYC on 2010-10-20
> **2893493 said:**
> Just wanted to chime in here.  

I am currently watching a rental of 'Splice' from Amazon Video on Demand on Firefox 3.6.8 on a 32-bit Debian Squeeze install and it works just fine.

It's not really the GNU/Linux way (you're supposed to rely on your distro to package this stuff up nicely for you), but if you are having trouble with the software from your distro being out of date, or not compiled with the features you want, you always have the option to go offroad and download the most recent stuff from upstream.

In the case of these two pieces of software, installation is pretty simple, as they are both from commercial vendors.

Get the newest release of Firefox for Linux from here:  [http://www.getfirefox.com](http://www.getfirefox.com)

Just get the tarball (.tar.gz) and unpack it somewhere.  Now you have the newest Firefox.

Then get the newest Flash player from here:  [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Just get the tarball (.tar.gz) and unzip it somewhere.  Put the libflashplayer.so in the plugins/ directory inside the Firefox install you unpacked.  Now you have the newest Flash player.

You can then run Firefox by cd'ing in to the directory where you unzipped it, and typing:

$ ./firefox

Anyway, Amazon VOD does seem to work on Linux, and that makes me happy.  Even though I like Netflix's "Watch it Now" better as a service and don't intend to unsubscribe (yet), I'll be diverting some cash to Amazon since they've actually rolled out a service that works on Linux.

Thanks, Amazon.



Thanks for the news.
I'll try it.

---

### Post by 2893493 on 2010-10-21
Just to be clear, my post is referring to watching an Amazon VoD rental via in-browser streaming.  By all accounts, you still can't play movies you *download* from Amazon VoD until Amazon makes a native Linux player for them.

Amazon does support a native MP3 downloader application, so it's not too far fetched to imagine them supporting video on Linux in the future.

Let's hope.

---

### Post by PC_load_letter on 2010-10-21
Amazon VOD plays like a charm here on Karmic 64bit using FF 3.6.11 w/ the latest Flash plugin. No problems w/ Chrome either.

---

### Post by jmore9 on 2011-05-02
Well i could not get the paid for film to stream in firefox on ubuntu.  I also found this site which talks about mint.

[http://www.ainer.org/news/ubuntu-linux-mint-compatible-amazon-prime-unlimited-instant-video-streaming-now-available](http://www.ainer.org/news/ubuntu-linux-mint-compatible-amazon-prime-unlimited-instant-video-streaming-now-available)

Still trying to figure out you guys can watch the paid for films and i cannot.

---

### Post by Legendary_Bibo on 2011-05-02
Amazon VOD works OOTB on Ubuntu 10.10 for me. Perhaps it has to do with codecs.

---

### Post by lovinglinux on 2011-05-02
> **Ric_NYC said:**
> Netflix vs Amazon on Demand

Netflix..........**Watch as many movies as you want... $8,99 a month!**

Amazon on Demand.... (????)

Another service for US only.

I recently subscribed to a service in my country that is similar to Netflix. They deliver DVD and Blu-Ray at home and offer 3500 titles online. Although they are very efficient delivering new titles, including new blockbusters, the online catalog sucks.

I pay U$32 and I can have 3 DVDs at home. I can switch titles any day, except Sunday and Holidays. 

The best part is that it works on Linux. I just wish the online catalog improves with time.

---

### Post by Legendary_Bibo on 2011-05-02
> **lovinglinux said:**
> Another service for US only.

I recently subscribed to a service in my country that is similar to Netflix. They deliver DVD and Blu-Ray at home and offer 3500 titles online. Although they are very efficient delivering new titles, including new blockbusters, the online catalog sucks.

I pay U$32 and I can have 3 DVDs at home. I can switch titles any day, except Sunday and Holidays. 

The best part is that it works on Linux. I just wish the online catalog improves with time.

I keep paying for Netflix, and I don't really use it.

---

### Post by nanonils on 2011-05-03
No problems here on any of my Natty 64 bit systems. I tried Amazon Prime VOD in both Firefox and Chromium. What is the flash player you have installed? 
Sometimes it is better to use Chrome [[http://en.wikipedia.org/wiki/Chromium_(web_browser)]:](http://en.wikipedia.org/wiki/Chromium_(web_browser)]:) "By default, Chromium only supports Vorbis, Theora and WebM codecs for the HTML5 audio and video tags, while Google Chrome supports these in addition to H.264, AAC, and MP3. On 11 January 2011 the Chrome Product manager, Mike Jazayeri, announced that Chrome will no longer support the H.264 video format for its HTML 5 player, just as Chromium does not.[11] Certain Linux distributions may add support for other codecs to their customized versions of Chromium.[12]"

---

### Post by jmore9 on 2011-05-04
What do you use for the DRM ?  I have several that i purchased on my windows machine and i tried them in ubuntu and they do not play !.  They play in the windows machine with the ubox thingy.

---

### Post by jmore9 on 2011-05-04
Here is a screenshot of one drm protected movie from windows machine.  This is viewing it on vlc player.

---

### Post by nanonils on 2011-05-04
Unbox is for Windows only, no Mac or Linux ([http://www.amazon.com/gp/video/ontv/player](http://www.amazon.com/gp/video/ontv/player)). You can install it in a Windows Virtualbox under Ubuntu although that is a bit too much effort I think. Wine and CodeWeavers do not work for Unbox.

Do you use Unbox because you want to download movies rather than stream them? You can capture most Flash based movies - except Amazon's - (e.g. Youtube Movies service) from a temporary folder depending on what browser you use. You can also install a Chrome or Firefox app to download Flash based streaming movies.

I'm not so sure about the DRM you encounter. Are you able to play regular DVDs? If so it is most likely a Unbox specific encryption.
Here is a good guide how to get DVDs to work. [https://sites.google.com/site/easylinuxtipsproject/multimedia](https://sites.google.com/site/easylinuxtipsproject/multimedia)
You'll need  libdvdcss2 and other things (usually you'll be prompted under Natty now to install if that is available). Who knows, maybe it'll make whatever you downloaded work if it is not a Unbox specific encryption.

Good luck!

---

### Post by nanonils on 2011-05-04
Looking at your screenshot (it says Attack Los Angeles.wmv) and the Unbox specs ([http://en.wikipedia.org/wiki/Amazon_Instant_Video](http://en.wikipedia.org/wiki/Amazon_Instant_Video)) I think you will have no luck: Unbox is the good old Microsoft Windows Media Player with a customized, Windows-only encryption plugin that slaps a DRM on it.

You can easily rent and stream that movie though without any complicated interfaces or programs. If you simply suspend your computer after allowing the stream to fully download on your laptop (simply hit pause and observe the bottom green status bar to load all the way to the right, then suspend but not hibernate your computer) you might even be able to watch it on the go if that is what you want to achieve.

---

### Post by jmore9 on 2011-05-04
I my have been wrong but i was thinking this was about viewing amazon rental or purchsed movies.  The screenshot is from an drm protected amazom movie i purchased that is on my windows machine.  When i purchase a amazon video on demand video ( just got a .99 cent one to test ) it would not view nor could i download it because you need the ubox to do that.   And there is no ubox for linux.

It played but it was garbled.  When i inquired with Amazon about what could be done to get the DRM into linux so liunx users could watch the movies also they basicly said they do not support any operating system , but ubox will only work on mac or windows.

All the movies that i have access to on amazon i pay for and they do not stream in my version of Ubuntu 10.10.  They are encrypted.

Just wondering how to do that because it does not work for me.

---

### Post by nanonils on 2011-05-04
That is really weird. My problems went away in July of last July when updating. 
What are your settings (32 bit, what browser, what flash player)?

---

### Post by PC_load_letter on 2011-05-04
I'm not trying to get AoD working on Ubuntu or anything (just not interested), but I want to say that AoD works perfectly on my roku box streaming to the tv. All the promotional shows they have there works perfectly with my roku, which is by the way a linux box. 

So, there has to be a way to get it to work with Ubuntu.

---

### Post by jmore9 on 2011-05-04
Ah there lays my confusion !  You are using a Roku 3rd party viewer, i must have missed that some how.

Well now on to the quest for some kind of DRM plug in for ubuntu to allow me to watch these rentals .

---

### Post by SeijiSensei on 2011-05-04
There's a bit of confusion here.  Amazon offers [digital movies]("http://www.amazon.com/Instant-Video/b/ref=topnav_storetab_atv?ie=UTF8&node=16261631") in two formats.  One is a download-to-own service that works only with Amazon's proprietary player because the movies are encrypted.  Amazon also offers a streaming service that "rents" movies in Flash at 480p.  Here's Amazon's description of the difference between these services:

[quote=Amazon]Rental: This is a 48-hour rental. You will have 30 days to complete watching this rental online or to download it. If you choose to watch this rental online, you can watch on a PC, Mac or compatible device. If you choose to download this rental, you can download it to one TiVo or one Windows PC and you will have 30 days from the date of purchase to begin watching your rental. Once you start to watch online or begin a download you cannot change your viewing choice. Rentals can't be transferred to a portable device or downloaded to a Mac.

Purchase: When you buy a video, your viewing rights do not expire (except as provided in our Terms of Use). You can watch a purchased video online and download it to 2 locations (TiVo DVRs & Windows PCs). You can also transfer a video you own to 2 portable devices. Note: Some new release movies will become unavailable for viewing or downloading for an unspecified period of time due to licensing restrictions. You will be notified about this before we process your order.[/quote]

As an Amazon Prime member, I now have streaming access to a wide variety of material free-of-charge.  I probably broke even on the reduced shipping charges that come with a Prime membership.  Adding free movie rentals to my membership just made it a whole lot more valuable.

The movies streamed in Flash play fine on my 64-bit Kubuntu 11.04 machine with the 64-bit "[Square]("http://labs.adobe.com/downloads/flashplayer10_square.html")" Flash player from Adobe.  The download-to-own movies obviously won't play on Linux.

---

### Post by nanonils on 2011-05-04
I have an off-the-shelf 64bit 11.04 Ubuntu (Natty) and here is my screenshot of your movie streaming (as a trailer) in Chromium. 

I also tried Chrome and Firefox and they, too, play it without problems. It looks a bit small because I did not choose "full screen" view. It automatically toggles into high resolution if your wifi is good (I'm at a conference with a pathetic signal).

---

### Post by dsfitzpat on 2011-05-23
I've also had no problems with Amazon Instant Video, running 11.04 64-bit on my desktop, with the Adobe Square 64-bit flash plugin, in Firefox.  For example, I've got a subscription to the current season of Doctor Who ($1.89 per episode).  Every week I get an email from Amazon telling me that the latest episode is now available, and I can go to Amazon.com and stream the video.

The downloaded videos won't play on Ubuntu, but I have access to a laptop with a Windows partition I can use to download them if I decided I need offline access.

---

### Post by natron on 2011-07-24
I've been unable to get Amazon on Demand videos to play; the loading animation just plays continuously.

I'm an Amazon Prime subscriber, my setup is 10.04 32-bit with Flash 10.3. I've also tried the Flash 11 beta, the Flash Aid FF plugin and playing videos in both FF and Chrome. All yield the same loading screen result.

Youtube isn't problematic nor are other websites with "free" streaming content.

 

Any ideas? :confused:

---

### Post by Legendary_Bibo on 2011-07-24
> **natron said:**
> I've been unable to get Amazon on Demand videos to play; the loading animation just plays continuously.

I'm an Amazon Prime subscriber, my setup is 10.04 32-bit with Flash 10.3. I've also tried the Flash 11 beta, the Flash Aid FF plugin and playing videos in both FF and Chrome. All yield the same loading screen result.

Youtube isn't problematic nor are other websites with "free" streaming content.

 

Any ideas? :confused:

Try Opera. Chrome, Opera, and FF all have different engines so try the last of the three major browsers for Linux.

---

### Post by natron on 2011-07-25
> **Legendary_Bibo said:**
> Try Opera. Chrome, Opera, and FF all have different engines so try the last of the three major browsers for Linux.
Tried Opera, no dice. Thanks though. 

Does anyone with a 32-bit Ubuntu install (Ubuntu itself, not Flash) have AoD working for them?

---

### Post by wagnebr1 on 2011-12-11
> **natron said:**
> I've been unable to get Amazon on Demand videos to play; the loading animation just plays continuously.

I'm an Amazon Prime subscriber, my setup is 10.04 32-bit with Flash 10.3. I've also tried the Flash 11 beta, the Flash Aid FF plugin and playing videos in both FF and Chrome. All yield the same loading screen result.

Youtube isn't problematic nor are other websites with "free" streaming content.

 

Any ideas? :confused:

Same here.  Anyone have suggestions?

---

### Post by starchaser1 on 2012-01-15
I'm puzzled. I've been watching Amazon Prime VOD with Ubuntu 11.10 and the newest flash for at least a couple of months. 
It worked fine until last pm. When I went to watch the video in firefox, I hit play and got an amazon message in the player saying updating video player. 
This update failed and I can no longer watch from this laptop. Tried other flash installations and browsers, same result.
--

This am I decided to try an almost identical laptop running Ubuntu 10.10 and 
flash "11.1.102.55ubuntu0.10.10.1 (flashplugin-installer)" including "metapackage to pull in ttf-dejavu-core and ttf-dejavu-extra (ttf-dejavu)"

I cringed when I got the player updating message but 
all went well and I can watch from this other laptop.

--
I just went back and re-installed flash and the dejavu package on the Ubuntu 11.10 laptop. Error still exists. 
Any help would be appreciated, this is where I get my Star Trek fix! :popcorn:

thoughts?
thanks,
jeff

---

### Post by sdowney717 on 2012-01-15
[http://www.amazon.com/gp/feature.html?ie=UTF8&docId=1000128561](http://www.amazon.com/gp/feature.html?ie=UTF8&docId=1000128561)

are these free to watch?

---

### Post by starchaser1 on 2012-01-15
> **sdowney717 said:**
> [http://www.amazon.com/gp/feature.html?ie=UTF8&docId=1000128561](http://www.amazon.com/gp/feature.html?ie=UTF8&docId=1000128561)

are these free to watch?

yep.
some shows are free, and some only with amazon prime

---

### Post by sdowney717 on 2012-01-16
tested one and again it works fine on ubuntu 11.10
If you buy Amazon Prime then you pay $78 per year, get free shipping, and get a lot of video.
Netflix uses Amazon servers, But Amazon does not require MS Silverlight, so works fine with linux.

When I looked at Amazon Prime last year, they had fewer titles than Netflix, I figured they would pick up more. Any news on how they compare now?

---

### Post by jdunn on 2012-03-05
To Sdowney717 and others who have Amazon instant video working:
I'm not sure what's different for your installation.  Until recently (1-2 months ago) Amazon video worked fine for me.  Now, I get a progress dialog followed by an error message (see attached screenshot).  I tried the latest 64-bit flash plugin from Adobe.  Then, I tried the stock Adobe Flash plugin that comes with Ubuntu...No difference.  Other sites with Flash content display fine.

---

### Post by iveand on 2012-08-10
I have multiple machines I have been testing with.  For the one with NVIDIA graphics, I got the same error message as above when trying AoD.  Namely it got stuck in an error message saying I needed to update flash.

To solve that,

```
sudo apt-get install libhal1 hal
```

And then I removed the .adobe folder from my home directory.

HOWEVER, for my main machines that have INTEL graphics (no NVIDIA), I don't get the error message saying I need to update flash, but rather just the continual "loading" message as indicated by others.

So, still stuck in that regard on machines with INTEL graphics.  Hopefully can find a solution still.

---

### Post by Elfy on 2012-08-10
Please start a new support thread in a support forum.

Closed

---

