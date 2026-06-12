---
title: "anyone wishes to share their chromium OS experience"
date: 2009-12-02
forum: The Cafe
---

### Post by rahilm on 2009-12-02
hey..I came to know that google has made its beta release of chromium OS available for download.

has any of you tried it..if so ..how is it??
since i  cannot download it..i am curious

I heard they have Gnome 2.24 and OOo 3.0

---

### Post by srt4play on 2009-12-02
I'm running it on my eeepc 901.  Where did you hear it has gnome and OOo? It's basically the chromium web browser with a clock, battery meter, network applet and a launcher tab with links to websites.  Why can't you download it?

---

### Post by phrostbyte on 2009-12-02
I've used it on a VM. It works pretty well for what it's suppose to do.

---

### Post by Regenweald on 2009-12-02
Really, there is nothing to experience. You log in. you browse the web. that's all you can do.

---

### Post by eriktheblu on 2009-12-02
I downloaded the VM image and ran in virtualbox.

It initially wouldn't recognize my Gmail account, but eventually I logged on after several attempts.

I found it to be quite slow. I'd much rather use Ubuntu with LXDE (80 MB idle RAM footprint) for a netbook. This may be from the virtualization, and it might be corrected.

Boot time was fast.

It was pretty much just Chrome browser, didn't see any other apps.

Couldn't figure out how to shut down.

Got bored, removed image, waiting for release.

---

### Post by Tibuda on 2009-12-02
> **rahilm said:**
> I heard they have Gnome 2.24 and OOo 3.0

No, someone have release a fake chrome os based on suse with gnome and ooo. The real chrome/ium os only have a modded chrome/ium browser. Only the source code was released([link]("http://src.chromium.org/cgi-bin/gitweb.cgi?p=chromiumos.git;a=summary")), but some people have created some vmware images from the source.

---

### Post by zagz on 2009-12-02
> **eriktheblu said:**
> 

Boot time was fast.


understatement :D

---

### Post by rahilm on 2009-12-03
Is this the fake one?
[HTML]http://getchrome.eu/download.php[/HTML]

---

### Post by Aflack on 2009-12-03
> **rahilm said:**
> Is this the fake one?
[HTML]http://getchrome.eu/download.php[/HTML]

hahahaha.

also, i think chrome os is a huge fail. my opinion. im not going to bother with it, as i dont use all google apps anyways.

---

### Post by PartisanEntity on 2009-12-03
I tried it, it works, but I wasn't able to do much with it because I use very few web based tools and services.

And as I mentioned in another thread, with bandwidth becoming less and less of an issue, I don't see how cloud computing is in any way better than a remote desktop session.

---

### Post by HappinessNow on 2009-12-03
> **PartisanEntity said:**
> I tried it, it works, but I wasn't able to do much with it because I use very few web based tools and services.

And as I mentioned in another thread, with bandwidth becoming less and less of an issue, I don't see how cloud computing is in any way better than a remote desktop session.read the article linked in this thread: [http://ubuntuforums.org/showthread.php?t=1343775](http://ubuntuforums.org/showthread.php?t=1343775)

---

### Post by Tibuda on 2009-12-03
> **rahilm said:**
> Is this the fake one?
[HTML]http://getchrome.eu/download.php[/HTML]

Yes, see footer on that link:
> Chrome OS is not related to Google. Service provided by SUSE Studio.

---

### Post by rahilm on 2009-12-03
damn...
from where do you get the original and how big is it?

---

### Post by NormanFLinux on 2009-12-03
Forget the Dell build. You need 8 GB for it and the download takes days. Try Hexxeh's 950 MB version that downloads fast. Cuts out all the bloat without losing any of the features. At the moment, wireless support is limited.

---

### Post by BrokenKingpin on 2009-12-03
I am surprised at how many people are interested in it. I guess it's probably because I am a power user (as are most of my friends) and don't want to be limited to a web browser as an OS. I have never been into this netbook/cloud computing stuff.

---

### Post by DesktopDiva on 2009-12-03
> **phrostbyte said:**
> I've used it on a VM. It works pretty well for what it's suppose to do.

I beg to disagree. It was supposed to make my web life and presence easier and faster but it made life really sllllooooowww. So for me that is a failure to deliver.

---

### Post by Spruce28 on 2009-12-04
Everything works on the eeePC 901 as advertised (it's only a browser, chromium 4.0.253.0).  Boots to login in 15 sec from SD flash, another 5 sec to browser. Uses your gmail login.

I like it for what it is, has been stable past 12 hours.

Kind of like Splashtop in Beta.  You do get terminal <ctrl> t.

Chromium OS builds by Hexxeh.
[http://chromeos.hexxeh.net/](http://chromeos.hexxeh.net/)
Current release is Cherry.
ChromeOS-Cherry.tar.gz is 300mb, image is almost 1gb.

Dave

---

### Post by NormanFLinux on 2009-12-04
Hexxeh's new Cherry build released today, now supports Ralink and Broadcomm wireless cards. Word of warning to the wise: it boots up fast but you need to wait 5 minutes to allow it to detect wireless networks to connect to. Its a very minimalist OS, exactly the experience Google intended to deliver.

---

### Post by NormanFLinux on 2009-12-04
Marry the Chrome Browser to the new Glide OS Webtop coming Monday and I think it would be a killer platform. You'd no longer have to choose between "cloud" computing and a desktop - you can now run the best of both on your netbook!

---

### Post by riste on 2009-12-05
I went through the "build from source" path, since I saw their preferred build environment was Ubuntu anyway.  I had no problems building the 4GB image or running on an Asus Eee 900A. 
Login was confusing since it uses a google account to login before you get a chance to connect to a network, so I enabled the 'shared user' account and used that.  I couldn't connect to a hidden network, but a WPA network worked.  I was also confused by lack of system controls such as logout or shutdown. 
The only really disappointing thing to me was that although boot-up was very fast, browsing performance was still about the same speed I've seen in other systems such as the UNR / KNR netbook remixes, so there isn't much advantage for me.  I believe this is because of the browser writing history, cache, or other data to my slow flash drive.  Maybe RAM could be used for this instead -- it wouldn't bother me if it forgot who I was every time it booted.

---

### Post by cynicl12000 on 2009-12-05
I installed chrome in a virtual machine on my Windows box.  

My windows box already has the google browser installed, and I love it (I still have to use FF for some sites, but Chrome is efficient and clean, so I mostly use it); but I have to say that if you want to use anything other than a netbook, you probably won't get much out of their OS.

My ubuntu box has google's browser in beta version for Linux, which is missing a few niceties (i.e. printing), but works great for my needs.

I can't see a practical application of the OS when one can just install google's browser on the OS of your choice and you have a lot more options for applications and user experience.

---

### Post by NormanFLinux on 2009-12-05
The concept is to remove computing to "the cloud." You can't install or download anything. That means its safe from viruses and malware. You can execute all the tasks needed within the browser and as I mentioned, if that's not enough you can get one of the webtops online to co-exist with Chrome that in effect will give you a traditional desktop metaphor within the browser. Its not for every one. But its as close to a minimalist operating system as one can hope for that is exactly where Google is going to do things differently from Microsoft, Apple and the traditional Linux distros.

---

### Post by markp1989 on 2009-12-05
> **Spruce28 said:**
> Everything works on the eeePC 901 as advertised (it's only a browser, chromium 4.0.253.0).  Boots to login in 15 sec from SD flash, another 5 sec to browser. Uses your gmail login.

I like it for what it is, has been stable past 12 hours.

Kind of like Splashtop in Beta.  You do get terminal <ctrl> t.

Chromium OS builds by Hexxeh.
[http://chromeos.hexxeh.net/](http://chromeos.hexxeh.net/)
Current release is Cherry.
ChromeOS-Cherry.tar.gz is 300mb, image is almost 1gb.

Dave

i tried this , its nice, feels abit slugish when running from the 2nd ssd in my eee 900 (not sure if that is the os or the drive slowing it down)

do my changes get saved (like network logon) on shutdown?

i have to log in as the default account before i can connect to the wifi, seems pointless. how can i connect to wifi before login?

---

### Post by crimesaucer on 2009-12-05
What music player and video player does it use? How about video plugins and java and flash? I'm just wondering.


And has anyone tried that 64-bit build?

---

### Post by Tibuda on 2009-12-05
> **crimesaucer said:**
> What music player and video player does it use? How about video plugins and java and flash? I'm just wondering.

web based, off course! you can just open last.fm, pandora or similar.

---

### Post by markp1989 on 2009-12-05
i been using it most of the evining the only thing it is  missing is a chat program. i was hoping to be able to install an addon like yoono for firefox to chrome, but i dont know of any.

---

### Post by crimesaucer on 2009-12-05
> **danielrmt said:**
> web based, off course! you can just open last.fm, pandora or similar.

I just read the wikipedia page and it says it has apt-get as the package manager so I guess my question was pretty stupid since you should be able to download and install anything (or even build it yourself).

I would much rather use a real music player or movie player than a web app with crappy sound. 

Last.fm sounds terrible to me (don't know about pandora). Radio blog is another web based music site (also with bad sound quality). And any web based movies like Hulu are usually bad.

---

### Post by confused_user on 2009-12-05
i have read about this google os thing.  I personally can see any use for it, what is the point?

I'm not writing it off just yet but i would like to understand what their goal is with this (world domination not withstanding)

I can think of a few good reasons not to use it off the top of my head

1) it is designed for netbooks - you need an internet connection to do anything on it.  How many people have access to broadband internet whenever they use a netbook for what it is designed for - being on the move

2) actually i think number one is a pretty good reason.  picture this, your on your way to work on the train.  You want to get on with some work to pass the time.  Oops, no internet connection, cant work offline.

i've got strong concerns with googles attempts to etangle themselves in everyones data as well.  no way is it a good idea for everyone to store everything on that corporations systems.

---

### Post by Spruce28 on 2009-12-05
> **markp1989 said:**
> i tried this , its nice, feels abit slugish when running from the 2nd ssd in my eee 900 (not sure if that is the os or the drive slowing it down)

do my changes get saved (like network logon) on shutdown?

i have to log in as the default account before i can connect to the wifi, seems pointless. how can i connect to wifi before login?

It boots fast but as someone else pointed out, runs no faster as browser.

On the Cherry distro, login and password as 'facepunch'.  The second time you go in, use your own gmail login.  

There is no graceful way to exit that I can see. I just hit the power button a quick jab, usually saves.  Even from terminal is not a graceful exit.

Dave

---

### Post by Thelasko on 2009-12-05
I tried a VM image the other day.  It was not the "facepunch" version most people use.  I did some exploring and found it to basically be Linux underpinnings with the chromium browser as the only desktop environment (other than X11).  It really looks like a half hearted effort at an OS.

As a side note, I heard a few weeks ago that [Chromium is faster on an X11 environment]("http://tech.slashdot.org/story/09/11/03/1334203/X11-Chrome-Reportedly-Outperforms-Windows-and-Mac-Versions?from=rss") than in either Windows or Mac.  Now we know why!

I really feel like I get a better user experience running Chromium on Ubuntu than using Chromeos.

---

### Post by kagashe on 2009-12-05
I downloaded the USB image but it exceeded the size of my pen-drive (2 GB).

kagashe

---

### Post by markp1989 on 2009-12-06
> **kagashe said:**
> I downloaded the USB image but it exceeded the size of my pen-drive (2 GB).

kagashe


the facepunch image is 1gb when extracted.

---

### Post by rahilm on 2009-12-06
Well..its web based as i heard somewhere..
that makes it least useful for me...
we live in dark times

---

### Post by kagashe on 2009-12-06
> **markp1989 said:**
> the facepunch image is 1gb when extracted.
Please give me the link to download.

ok. Googled and [got it]("http://chromeos.hexxeh.net/").

kagashe

---

### Post by kagashe on 2009-12-07
I downloaded the ChromeOS Cherry and copied the image to 2 GB pendrive, and using it now to post here. The response to keyboard and mouse is very slow. After I type this sentence I have to wait a few seconds before the text appears on the browser.

I am using it on a Desktop with Pentium Celeron CPU.

kagashe

---

### Post by Sven6210 on 2009-12-07
I do not see why I shall even try ChomeOS. I expect more from an OS than only providing a web browser. So far I do not want to miss my Thunderbird, OpenOffice, Ekiga, Skype etc.

---

### Post by NormanFLinux on 2009-12-07
I think something that old would work better with a kiosk type OS like Xpud. If Hexxeh refines his build and starts adding a useful set of "cloud" tools - it could become a stripped down OS for older computers. Right now its just a browser and the way the tabs are arranged makes the Google Gears hard to find. It needs to mature first.

---

### Post by NormanFLinux on 2009-12-07
The "cloud tools" are there but not easily accessible at bootup. So Hexxeh will have to do a redesign of the interface to make it really usable for most people. That I think is going to happen in future builds now that hardware support is nearly about complete.

---

