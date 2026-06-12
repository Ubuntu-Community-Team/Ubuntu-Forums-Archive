---
title: "Ubuntu vs. Lubuntu vs. Chrome OS Flex"
date: 2024-03-20
forum: Ubuntu, Linux and OS Chat
---

### Post by karyk on 2024-03-20
New Ubuntu user, although I have used it a long time ago in the past.  Here are my impressions of these three OS's for light use.

1.  Chrome OS Flex is clearly the easiest to install and use, but has very limited apps, more limited than Chrome OS machines due to the lack of the Google Android Play Store.  Completely lacking seems to be any email client for non-Gmail accounts.

2.  Lubuntu is supposedly light weight, but I really don't notice a significant difference from Ubuntu using a low end machine with an N4000 processor.  Also the Firefox browser does not seem to be the most current on Lubuntu, which is concerning. It does have a very nice user manual system for help information. It does though oddly have more settings than Ubuntu for things like closing the lid power settings and mouse wheel scrolling.  Thunderbird needs to be installed.  The one pre-installed game cannot easily be deleted.

3.  Ubuntu comes with Thunderbird and Firefox, but also more fluff like games (which can be deleted).  The keyboard shortcuts setup seems better than Lubuntu, but again no controls for the lid on notebooks and limited mouse controls.  My Thunderbird is sometimes sluggish, but I think that's due to one of my old Comcast email accounts (Comcast is often problematic--no surprise).  One nice thing over Windows is it comes out of suspend (sleep) and lock screens much faster--your first keystroke actually records, so you need to use the first character of your log-on.  Oh, and it's now much more user friendly than whatever version I used many years ago.

Overall I'd suggest only using Chrome OS Flex if you only want to browse the web and read Gmail email.  I'm not sure how weak of a machine you need to have to need Lubuntu, but I really don't see another purpose for it.  I'd install Ubuntu instead.

Finally, the advice is to do a clean install of Ubuntu, and that is seemingly good advice.  I did have issues installing it over Lubuntu.

---

### Post by Impavidus on 2024-03-20
Welcome.

Just a few notes: Lubuntu and Ubuntu use the same repositories. They differ in their default settings and set of installed software, but the same software is available and when installed you'll get the same version. That is, assuming you installed the same version of the OS.

I don't know type numbers of CPUs. They do matter, but usually the amount of memory and the graphics hardware are more important when making a choice between Ubuntu and Lubuntu. And personal preference. Ubuntu is known for being less configurable than the flavours. That's a decision of the Gnome people.

---

### Post by guiverc on 2024-03-20
This may not be additional details to what @Impavidis already provided; but I'll give it anyway.

Lubuntu is a Ubuntu system.

Both are built by the same build system on the same infrastructure; the difference being the *seed* file that controls what is put on the ISO itself, and what is actually installed. 

Ubuntu Desktop ISOs contain more *third party* & other packages (Nvidia, OEM kernel stack choices) than are provided by Lubuntu (*which has none*), and kernel stack defaults can differ (Lubuntu being a *flavor* will use GA for initial & .1 ISOs where Ubuntu Desktop uses HWE for all; all Desktop ISOs default to HWE for .2 & later); that can cause a *slight* difference post-install, but Lubuntu has those available too (*they're just not on the ISO so need to be installed post-install*)

The *firefox *package will be IDENTICAL between Ubuntu & Lubuntu, unless you're comparing different release ISOs (eg. 22.04.4 of both will be the same, as will 23.10 of each being the same, however a 22.04.3 of one & 22.04.4 of another will mean differences as one ISO was created six months later than the other), as builds for released systems are done whilst a *freeze* is *in place*, thus packages aren't changing.  This will not apply for *daily* images where no *freeze* is active.

Lubuntu has used the `calamares` installer since 18.10; where as the installer used by Ubuntu Desktop has varied based on release (*with two options for the last releases of 23.04 & 23.10*) thus installer can vary on release but you gave no details here. The installer will not impact the installer system, but options available that can influence install can differ which can.

You gave no release details; so no clear details can be provided; you were thus possibly comparing different release ISOs I suspect *(**firefox version on ISO should be identical in my view* *as all ISOs for a release occur at the same time, even if delayed by an hour etc - freeze remains in place to prevent differences*)

---

### Post by TheFu on 2024-03-21
> **karyk said:**
> New Ubuntu user, although I have used it a long time ago in the past.  Here are my impressions of these three OS's for light use.

1.  Chrome OS Flex....

2.  Lubuntu ...

3.  Ubuntu ...

Overall I'd suggest only using Chrome OS Flex if you only want to browse the web and read Gmail email.  I'm not sure how weak of a machine you need to have to need Lubuntu, but I really don't see another purpose for it.  I'd install Ubuntu instead.

Finally, the advice is to do a clean install of Ubuntu, and that is seemingly good advice.  I did have issues installing it over Lubuntu.

Thanks for sharing.  An N4000 CPU isn't low end compared to some CPUs people use.  Look at an N2000 or an AMD E-350 and try again.  It isn't just about performance.  There are many other considerations.

Ubuntu requires about 30GB for a basic install.  One of my Chromebooks came with a 16GB SSD.  Ubuntu won't fit.  Lubuntu did and left over 5GB of storage for data on the SSD.  

I've never used Flex, but if it is like ChomeOS, then it would be significantly more secure than any Ubuntu out of the box AND a light-weight, small, footprint.  ChromeOS running on a Chromebook that is currently supported is the most secure OS with networking that I know.

I find Lubuntu to have far too much bloat and the Gnome-based Ubuntu is completely unreasonable for what I want in a desktop.  I run Ubuntu without any DE.  The base Ubuntu OS fits in 7.5 GB of storage, if you are careful and don't load a desktop at all, then add a minimal GUI.  Of course, I'm different from nearly every other user, so most would be happy with the normal offers provided by Gnome, Mate, LXQt, XFCE or KDE DEs. I'm odd.

There are multiple options because there are all sorts of users and the full Ubuntu+Gnome with a heavy GPU requirement, lots of RAM, 30+GB of storage doesn't fit many user's needs.

With Linux, 1-size doesn't fit all. Thank Dog!

---

### Post by karyk on 2024-03-21
Unfortunately I don't remember for certain the release number of the Lubutu install, but it was the current LTS release from about two weeks ago.  Still, wouldn't a full update do an update for Firefox and not leave it in a prior version update?  I was running Lubuntu for approximately two weeks.  If not, that's a huge shortcoming.

---

### Post by karyk on 2024-03-21
Thanks.  I wish some of the sites I'd reviewed discussing the N4x00 CPUs prior to picking Lubuntu had mentioned that the CPU wasn't that critical, because I'm not all that limited on space.  4GB of ram is probably the biggest limitation for my uses.

Part of the reason I posted my first post was so that others comparing those three choices would have some better idea what to expect.  The additional information you and others have provided should help too.

Agree on Chrome OS security, and I'd continue to use it if the app situation were better.  In that regard though, Chrome OS Flex is probably more secure than Chrome OS.  If you've never used Chrome OS, I wouldn't recommend it for tablets, but if my Flex use is an indication a Chromebook would probably be acceptable.  If they made better hardware choices I'd prefer Android for tablets over ChromeOS, but as it is I have an Ipad (my only Apple device, ever).

---

### Post by TheFu on 2024-03-21
More speed is always better, but any CPU with more than 1500 passmarks should be fine for typical office applications.  

For video playback, the GPU and video codec support via hardware+drivers is more important.  That's why $200 Chromebooks from 2012 could playback 1080p youtube content - the GPU + drivers were setup specifically to ensure video playback of h.264, mpeg2, and vp8 videos worked well, regardless of how low-power the CPU may have been.

If you have an older GPU or low-end 4 yr old APU (that's a CPU+GPU on the same chip), then it is unlikely to support h.265/VP9 in hardware, so playback of those videos from youtube will suck.  OTOH, with a specific chromebook telling youtube which video codecs it supports in hardware decoding, YT can provide that type of video encoding as needed.

I've owned and used ChromeOS a few times.  However, after a few months, it became clear that it wasn't enough OS for my needs, so I'd wipe it and load a light-Ubuntu system.

Android has nearly zero security and even less privacy, so it isn't anywhere near the security of even MS-Windows, much less a properly installed and maintained Linux desktop.  There's a reason Android is called a "personal surveillance device". GrapheneOS, a fork of Android, may be more secure and more private. IDK.  

All devices with a cell phone modem inside are surveillance devices. That's a fact and it doesn't matter who the hardware vendor is.  Cellular devices all ping towers, even if we don't have a paid cell phone plan.  Keep your cell phone both in airplane mode and inside a Faraday pouch, if you want privacy.

I try to never give Apple any money, even indirectly. I have problems with their choice of partners and component build locations. Yesterday, I saw the CEO *kissing the ring* that disturbed me and I found offensive.  Call it a political disagreement.

---

### Post by coffeecat on 2024-03-21
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by karyk on 2024-03-21
I'm not a fan of Apple either, but the iPads are rather reasonably priced.  I needed a cellular version, and usb alt mode, which really limited my choice of tablets.

---

### Post by DuckHook on 2024-03-22
When I started over a decade ago, Lubuntu was lean and mean. It has since suffered from the same bloat that is now prevalent everywhere in computing&#8209;land.

It's important to note that sloth&#8209;like performance can not be blamed on the OS alone. Firefox is a massive app. So is Thunderbird. These are designed for newer system with enough resources, absent which, the experience is likely to be frustrating.

Moreover, none of us run computers for the sake of the OS. Productivity and even simple enjoyment is about the apps. Therefore, if you are finding the combo of Lubuntu/Firefox/T-Bird to be unbearable, then:

[LIST=1]
[*]So long as you insist on FF and T&#8209;Bird, there is no OS that will make your experience more enjoyable. The problem will be the bloated apps that you prefer, not the OS. But if you are okay switching to lightweight alternatives, then that will make a big improvement to your overall computing enjoyment.
[*]Lighter weight alternatives would be Epiphany for FF, Sylpheed for T&#8209;Bird, Abiword & Gnumeric for LibreOffice.
[*]Lubuntu used to ship with the above alternatives as defaults. The fact that it now ships with the bloated stuff only reinforces that fact that it is no longer a truly lightweight flavour.
[/LIST]
I no longer think that looking for a lighter OS is really that fruitful because the OS is no longer the most significant bottleneck. Though the OS still plays its part, it is far less significant than the apps you choose.

RE: Non&#8209;Apple tablets — have you tried Samsung? They have their own problems, but I find them to be acceptable cell&#8209;capable alternatives to Apple.

---

### Post by NormanFLinux on 2024-03-23
I have transformed elementary OS into a ChromeOS style system by adding web apps to it through the Google Chrome browser. No need to to worry about Linux support and I can run apps both offline and in the cloud. Its the best of both worlds.

---

### Post by TheFu on 2024-03-23
> **DuckHook said:**
>  
RE: Non&#8209;Apple tablets — have you tried Samsung? They have their own problems, but I find them to be acceptable cell&#8209;capable alternatives to Apple.

I had a $50 Amazon 8 inch tablet for years.  Scrubbed nearly all the Amazon stuff off it and used it as a normal Android tablet - book reader, media player, VPN client, pretty much anything to "consume" different information/media.  Worked great!  Just add f-droid for apps and avoid Amazon/Google app stores.  After 6+ yrs of daily use, one morning, it stopped working. Never figured out why. There was no warning.  Plenty of battery life too.

I'd had a 10 inch tablet, high end, when they first came out. That's how I knew that 10 inches was just too large.  Did everything, including running a light Ubuntu inside a chroot on this tablet, but it was just too slow. The Amazon tablet was faster.  That's what happens in 5 yrs.  Perhaps 4 hrs of battery life.

I lived without a tablet when the Amazon Fire died for a few days, then it became very clear that I wanted a replacement.  A little more speed, support for a larger microSD card, and a GPS were at the top of my needs.  Plus, Amazon's 8in tablet was $75 that week. I wasn't going to wait until it was $50 again ... in June/July.  

Did lots of research and ended up with a relatively cheap ($120) 8inch Samsung Galaxy Tab A7 Lite.  It arrived in a few days and I started purging google stuff from it.  Added f-droid and added my VPN, nextcloud, jellyfin, wallabag, Voice (audiobooks), stuff.  It was a little frustrating since the newer Android changed the security model to prevent access to data files by alternate apps.  I still struggle with that.  Added an off-line map/GPS tool (remember, no Google), and the GPS worked perfectly with OSM data.  Eventually, my nextcloud data sync of music, audiobooks magically started working with the stand-alone music player and audiobook player. I have no idea what made that possible - perhaps an OS update?

I miss a few things from the Fire Tablet (package tracking from amazon), but I'm so very happy to have the GPS. Most of the time, I'm reading ebooks or controlling video playback on a projector via Jellyfin ---> Kodi. Jellyfin transcodes videos to the format the raspberry pi can handle well.  Even on a pi v4, VP9 doesn't playback without losing audio sync.  OTOH, h.265 or h.264 work great, so I have the jellyfin server transcode anything that isn't mpeg2, h.264. h.265 to one of those video codecs. Same on the Tab-A7.  

Most Samsung tablets are overpriced 3x, like Apple's.  This 8in tablet is reasonable for what it provides, assuming you get it under $130.  I'm amazed at how much people will spend on what is basically a tracking device. That's what Android is - a way to track us.  Before Android, everyone online used fake names. It was Google that was able to bridge the fake, online, names with credit cards (and real names) when Android phones took off. Cell phone companies don't provide service for free and most people seem to sign up for a monthly payment to have that convenient service.  When I need cell service, I use a pre-paid SIM card, purchased with cash for a specific period of service.  For years, I'd top it off yearly with a $10 addon, bought with cash.  Keeping my real name anonymous was worth the slight hassle of doing that.  Then the cell company removed the plan and started charging $3/month.  I retained it until the pre-paid money ran out, then stopped.  Switched to a nearly free SIM that has extremely limited use plans.

Of course, if you have a tablet with a SIM data card, there are plans for that. Here there's an unlimited data plan that can be added onto a monthly voice/phone plan for $20/month extra.  A few friends use it to monitor their investment properties and cabins or beach home security cams.  For fun, we watch the cows grazing, live, from 4 states away.

The cellular data Samsung Tab variants run about $160 with Verizon and GSM models available.  A quick search today found 8.7 - 10.5 inch versions under $200.  But it is still Android and it would be hard for most people to avoid the google ecosystem.  Apple is better at hiding what they really do with the data, but being hidden and having better marketing doesn't actually change the truth.

---

### Post by karyk on 2024-03-23
The reasonably priced Samsung tablet has a crippled version of Dex, which is only wireless.  I need to connect via HDMI.  I actually ordered it and then cancelled once I realized that limitation.

---

### Post by DuckHook on 2024-03-23
It's not ideal, but IIRC a USB-C to HDMI cable/dongle will give you screen mirroring. You will get the big black bands vertically or horizontally (it's outright mirroring after all), but I find that it's not too bad. With a Bluetooth mouse+keyboard, it is usable as a desktop&#8209;like platform.

---

### Post by TheFu on 2024-03-23
> **karyk said:**
> The reasonably priced Samsung tablet has a crippled version of Dex, which is only wireless.  I need to connect via HDMI.  I actually ordered it and then cancelled once I realized that limitation.

[https://www.xda-developers.com/how-to-access-samsung-dex-mode-linux-chrome-os/](https://www.xda-developers.com/how-to-access-samsung-dex-mode-linux-chrome-os/)

I've used scrcpy  [https://github.com/Genymobile/scrcpy](https://github.com/Genymobile/scrcpy) to mirror my Android devices onto my Linux computers a year or two ago, if that's what you miss.  I haven't tried it with this tablet, but it worked with the Fire tablet and my last 3 Android phones, so I'm pretty certain it is a generic Android feature, not anything special.  It uses adb behind the scenes.

---

