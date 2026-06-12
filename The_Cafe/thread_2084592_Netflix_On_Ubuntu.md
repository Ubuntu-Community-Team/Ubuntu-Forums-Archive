---
title: "Netflix On Ubuntu"
date: 2012-11-15
forum: The Cafe
---

### Post by dniMretsaM on 2012-11-15
It appears that I Heart Ubuntu's campaign to get Netflix running on Ubuntu [has paid off]("http://www.iheartubuntu.com/2012/11/netflix-on-ubuntu-is-here.html"). The setup doesn't look easy, but it might be worth it. I'm trying it out now to see how it works.

**How to install:**
You can install the Netflix app quite easily with these commands:
```
sudo apt-add-repository ppa:ehoover/compholio
sudo apt-get update
sudo apt-get install netflix-desktop
```**EXT2/3 Filesystems:**
Open up [FONT=Courier New]fstab[/FONT] in you favorite editor. If you use Gedit, you can run this:
```
gksudo gedit /etc/fstab
```Now you need to add [FONT=Courier New],user_xattr[/FONT] to the fourth column the root filesystem line. It should look similar to this:
```
UUID=94f7fc1e-fa27-4b24-99f3-4b461665a4a4       /       ext4    errors=remount-ro,user_xattr       0       1
```Then just remount your root filesystem:
```
sudo mount -o remount /
```

**Sound Issues:**
If you're having sound issues with WINE on a 64-bit machine, some users have found this helpful:
```
sudo apt-get install libasound2-plugins:i386
```

---

### Post by d98jh on 2012-11-16
Any luck? I'm on 64bit so I tried building in chroot but it doesn't seem to work. Firefox installs but when I open the Netflix site it doesn't seem to find the Silverlight plugin...

---

### Post by Lars Noodén on 2012-11-16
It's not really on Ubuntu, it's on Windows but available via WINE.  What has happened is that there is now a version of WINE which can handle the weirdness in the Netflix Windows client.  

[Netflix is available for Android/Linux](https://play.google.com/store/apps/details?id=com.netflix.mediaclient) so it would not be that hard to finish porting it to GNU/Linux so we can have it on Ubuntu.

---

### Post by forrestcupp on 2012-11-16
This is awesome. I have 64-bit, so I'll be waiting on the PPA. Hopefully these changes to get this working don't create any regressions in Wine.

> **Lars Noodén said:**
> It's not really on Ubuntu, it's on Windows but available via WINE.  What has happened is that there is now a version of WINE which can handle the weirdness in the Netflix Windows client. 

Running Windows apps in Wine is not the same as it being on Windows. You don't have to use a VM for this, so I'd say that it's legitimately running in Ubuntu, because Wine is not an emulator. :)

---

### Post by Lars Noodén on 2012-11-16
It may run under WINE but it is still a Windows version using the Windows APIs and all that.  They have it in them, technically, to make a native Linux version.  They already have for Android.  Porting it to regular Linux should be a small step.

Anyway, even it if is a small step forward of sorts, it is a step forward.

---

### Post by kansasnoob on 2012-11-16
> **Lars Noodén said:**
> It may run under WINE but it is still a Windows version using the Windows APIs and all that.  They have it in them, technically, to make a native Linux version.  They already have for Android.  Porting it to regular Linux should be a small step.

Anyway, even it if is a small step forward of sorts, it is a step forward.

My son bought a new chromebook (small for my taste) and tells me that Netflix works OK on it. So I'd think it should be possible.

---

### Post by evilsoup on 2012-11-16
Whoa.
*Yes*.

I'll *probably* wait for the PPA mentioned in the article, but this looks really cool! Does anyone know if it would be possible to install this version of wine alongside my current version, by compiling it differently?

This should work for other silverlight-DRM sites like Lovefilm, right? This issue is the only thing that stops me from recommending Ubuntu to people... obviously an official, supported solution would be best, but this is such great news.

The chromebook version uses a hardware chip for DRM, IIRC, so that's not really portable to Ubuntu.

---

### Post by moocow1452 on 2012-11-16
> **Lars Noodén said:**
> 
[Netflix is available for Android/Linux](https://play.google.com/store/apps/details?id=com.netflix.mediaclient) so it would not be that hard to finish porting it to GNU/Linux so we can have it on Ubuntu.

Um, then why haven't we seen anyone crack the app open and play it on a Linux install yet? I'd imagine there is some processor hoodoo involved, since ARM doesn't translate well to x86, and the DRM thing seems to be baked into the app over hardware.

EDIT: Netflix does have it in them to program a native Linux version, but the call is from up top, citing no Silverlight support to hold their hand for them. Which is silly, since the Android and Chrome OS versions work fine without Silverlight, but prodding them on the issue seems to not work in our benefit. [http://www.omgubuntu.co.uk/2012/09/netflix-no-change-in-our-plans-for-linux](http://www.omgubuntu.co.uk/2012/09/netflix-no-change-in-our-plans-for-linux)

---

### Post by dniMretsaM on 2012-11-16
Well, I ended up not compiling since I'm on a 64-bit system. I don't use Netflix much anyway, so I didn't figure the trouble would be worth it. Has anyone else given it a try yet? I would love to hear how it works.

Even though this isn't a native Netflix client, it's still an awesome step in the right direction.

---

### Post by HansKisaragi on 2012-11-16
While native Netflix would be awesome I dont see it happening..

I got Netflix on 4 devices so im happy.

---

### Post by jerome1232 on 2012-11-16
The only way for Netflix to come to Ubuntu natively is for Netflix to drop silverlight. They use a bit of DRM in silverlight that Microsoft refuses to license out to Desktop Linuxes or to allow to run in moonlight, although it has licensed it out to mobile phones running android, and blu-rays running linux kernels, and to streaming devices running linux kernels, and to OSX.

Chrome OS uses a hardware chip that handles the DRM, that's the only way Microsoft was going to license it.

The MS DRM is called PlayReady

---

### Post by sdowney717 on 2012-11-16
Netflix and MS Windows is in tight relationship.
They share board members I recall.
MS Windows hates free Linux so I don't expect anything good regarding same. they do get Chrome OS and Android but then that is not free as you have to buy the Chrome book or Android device.

---

### Post by evilsoup on 2012-11-16
I really don't think there's any need for conspiracy theories here; the UK company Lovefilm has a very similar streaming service that *also* relies on Silverlight. It's probably just that Microsoft have the best (for this purpose) DRM system, and see no compelling case to port it to Linux. No need to assume malice, really.

I can't wait for the PPA to come out...

---

### Post by HansKisaragi on 2012-11-16
I wish they would develop a new solution for streaming but that aint happening

---

### Post by jerome1232 on 2012-11-16
No conspiracy theory, Microsoft publicly stated the reason they won't license PlayReady to Linux on a Desktop is because they fear hackers will crack their DRM, which is ridiculous.

Silverlight runs via Moonlight in Linux, what doesn't is the PlayReady drm. All I'm stating is this is more Microsofts fault that it won't run on Linux than it is Netflix's fault. Honestly I'd rather watch it on one of my blu-rays or on my Wii and don't much care if it works on Linux or not, I do wish it worked on my Netbook while in Ubuntu however.

---

### Post by kansasnoob on 2012-11-16
Well I'm definitely going to try this Wine hack because I'd love to be able to watch Netflix vids on my HTPC rather than using Roku to stream to my crappy TV :shock:

I'm stuck in a no-mans-land where it's expensive to get decent TV or Internet so I can't afford both :(

And the EMI/RMI is horrible here due to industrial level grain production so wireless more than sucks!

I'd love to catch up on Deadwood, Supernatural, and The Walking Dead w/o having to install Windows so this is a potentially huge breakthrough!

I'm nursing some sick dogs ATM  but I'll try this very soon :guitar:

---

### Post by snowpine on 2012-11-16
> **kansasnoob said:**
> 
I'd love to catch up on Deadwood, Supernatural, and The Walking Dead w/o having to install Windows so this is a potentially huge breakthrough!


Netflix doesn't stream HBO shows like Deadwood. Walking Dead they have the first 2 seasons. Supernatural I've never seen--is it good?

---

### Post by sdowney717 on 2012-11-16
Just tried this following the compile and all and it cant find the silverlight plugin = fail.
Just read the comment section as many say the same thing
Firefox works ok.

---

### Post by BrokenKingpin on 2012-11-16
That looks like to much work. I stick to watching netflix on my PS3 and Boxee box.

---

### Post by kansasnoob on 2012-11-16
> **snowpine said:**
> Netflix doesn't stream HBO shows like Deadwood. Walking Dead they have the first 2 seasons. Supernatural I've never seen--is it good?

I thought I saw Deadwood in the list of DVD's available if I chose to get a DVD at a time :confused:

I saw the first season of the Walking Dead and I loved it, but then I had to cut the cord/cable :(

I started watching Supernatural on Hulu about one year ago, I can also watch it on "the CW" but that's very fiddly ... the ads suck.

Supernatural is kind of a quirky/corny show. A combo of sci-fi/horror with a taste of humor. But I'd love to see it from season 1 --> 

I've seroiusly been thinking about doing the DVD only thing with Netflix so I can enjoy in hi-def. It makes no sense to spend hundreds of dollars to buy a hi-def TV that can't get reception w/o a major investment.

BTW:

[http://movies.netflix.com/WiMovie/Deadwood/70157459?locale=en-US](http://movies.netflix.com/WiMovie/Deadwood/70157459?locale=en-US)

---

### Post by snowpine on 2012-11-16
> **kansasnoob said:**
> I thought I saw Deadwood in the list of DVD's available if I chose to get a DVD at a time :confused:

I saw the first season of the Walking Dead and I loved it, but then I had to cut the cord/cable :(

I started watching Supernatural on Hulu about one year ago, I can also watch it on "the CW" but that's very fiddly ... the ads suck.

Supernatural is kind of a quirky/corny show. A combo of sci-fi/horror with a taste of humor. But I'd love to see it from season 1 --> 

I've seroiusly been thinking about doing the DVD only thing with Netflix so I can enjoy in hi-def. It makes no sense to spend hundreds of dollars to buy a hi-def TV that can't get reception w/o a major investment.

BTW:

[http://movies.netflix.com/WiMovie/Deadwood/70157459?locale=en-US](http://movies.netflix.com/WiMovie/Deadwood/70157459?locale=en-US)

Yes, you can get Deadwood etc. on DVD.... and that has always worked just fine on Linux... we are only discussing their streaming service here (which hasn't work on Linux until now).

---

### Post by mamamia88 on 2012-11-16
> **jerome1232 said:**
> No conspiracy theory, Microsoft publicly stated the reason they won't license PlayReady to Linux on a Desktop is because they fear hackers will crack their DRM, which is ridiculous.

Silverlight runs via Moonlight in Linux, what doesn't is the PlayReady drm. All I'm stating is this is more Microsofts fault that it won't run on Linux than it is Netflix's fault. Honestly I'd rather watch it on one of my blu-rays or on my Wii and don't much care if it works on Linux or not, I do wish it worked on my Netbook while in Ubuntu however.

lol that's funny.   hackers will crack their drm one way or another so i don't see why they even bother.   the whole point of paying for netflix in the first place for me anyway is that i have a cheap way to watch a lot of content without piracy.

---

### Post by kansasnoob on 2012-11-16
> **snowpine said:**
> Yes, you can get Deadwood etc. on DVD.... and that has always worked just fine on Linux... **[COLOR="Red"]we are only discussing their streaming service here[/COLOR]** (which hasn't work on Linux until now).

I'm fully aware of that :)

But in post #17 you said, "Netflix doesn't stream HBO shows like Deadwood".

I honestly didn't know that there was a difference between what could be streamed or what I could get in the mail-box :)

Maybe I should just do the DVD by mail routine :confused:

---

### Post by snowpine on 2012-11-16
> **kansasnoob said:**
> I'm fully aware of that :)

But in post #17 you said, "Netflix doesn't stream HBO shows like Deadwood".

I honestly didn't know that there was a difference between what could be streamed or what I could get in the mail-box :)

Maybe I should just do the DVD by mail routine :confused:

Only a very small % of Netflix content is available for streaming. Frankly I don't understand why people make such a big deal over Netflix streaming. It's great if you want to watch reruns of Lost, but there are other Linux-friendly services that already let you do that.

---

### Post by jerome1232 on 2012-11-16
> **kansasnoob said:**
> 
Maybe I should just do the DVD by mail routine :confused:

There's a lot you can stream that you can't get on DVD as well. As much as I love my netflix, sometimes it makes me do this. ](*,)

Honestly 98% of our netflix is my son using the netflix for kids on our wii, they have a lot of pbs kids shows so it's great for him.

---

### Post by moocow1452 on 2012-11-16
> **snowpine said:**
> Only a very small % of Netflix content is available for streaming. Frankly I don't understand why people make such a big deal over Netflix streaming. It's great if you want to watch reruns of Lost, but there are other Linux-friendly services that already let you do that.

Mostly it's that Netflix is the single holdout in not playing well with non-flash webservices, it's the Coke in the streaming world to everything elses RC Cola, and it means something to play all the movies. Plus, they licensed a new season of Arrested Development for 2013, and have an unparalleled TV collection to binge, even considering Hulu Plus and Amazon Prime. (And by unparalleled, I mean Futurama.)

---

### Post by neu5eeCh on 2012-11-16
Hey, pretty cool. I wonder if MS will pull any dirty tricks to stop it? - if it's even possible...

---

### Post by evilsoup on 2012-11-16
This trick doesn't support the *latest* Silverlight; all they'd have to do to break it would be to make the version wine can run incompatible with their DRM & force all the Windows users to upgrade.

---

### Post by mamamia88 on 2012-11-16
> **evilsoup said:**
> This trick doesn't support the *latest* Silverlight; all they'd have to do to break it would be to make the version wine can run incompatible with their DRM & force all the Windows users to upgrade.

and why would they bother with that?

---

### Post by neu5eeCh on 2012-11-16
> **mamamia88 said:**
> and why would they bother with that?

Apple does it all the time. Apple would do it every day if they had to.  So why wouldn't Microsoft?

---

### Post by neu5eeCh on 2012-11-16
By the way, should I uninstall Crossover before I try installing this patched version of Wine? Any thoughts?

---

### Post by forrestcupp on 2012-11-16
> **sdowney717 said:**
> Just tried this following the compile and all and it cant find the silverlight plugin = fail.
Just read the comment section as many say the same thing
Firefox works ok.

Firefox has always worked with Wine without any hacks. Double fail. ;)

---

### Post by mamamia88 on 2012-11-16
> **VTPoet said:**
> Apple does it all the time. Apple would do it every day if they had to.  So why wouldn't Microsoft?

well first off netflix would have to switch the version of silverlight that works with it as well as pissing off all the people who don't know anything about computers when netflix stops working for no apparent reason.  how much control does microsoft have over netflix anyway?  they are still independent companies right?

---

### Post by Lightstar on 2012-11-17
Netflix works perfectly on android, which is linux.
I wonder if I could just load up android x86 in virtualbox or a dev version, with a netflix app... and use it that way

---

### Post by evilsoup on 2012-11-17
> **mamamia88 said:**
> and why would they bother with that?

I don't think they will, not any faster than old versions would naturally become obsolete anyway. All I'm saying is that they *could* do it, if they wanted to. 

[quote=Lightstar]Netflix works perfectly on android, which is linux.
I wonder if I could just load up android x86 in virtualbox or a dev version, with a netflix app... and use it that way[/quote]

It's been tried, it doesn't work.

---

### Post by dniMretsaM on 2012-11-17
Added a small update to the first post.

---

### Post by lovinglinux on 2012-11-17
I have found the PPA and it was updated 26 minutes ago with the netflix-desktop packages but they are still building.

[https://launchpad.net/~ehoover/+archive/compholio/+packages](https://launchpad.net/~ehoover/+archive/compholio/+packages)

---

### Post by lovinglinux on 2012-11-17
> **lovinglinux said:**
> I have found the PPA and it was updated 26 minutes ago with the netflix-desktop packages but they are still building.

[https://launchpad.net/~ehoover/+archive/compholio/+packages](https://launchpad.net/~ehoover/+archive/compholio/+packages)

The 32bit packages were built. The necessary packages are netflix-desktop and wine-compholio. I haven't tested yet.

---

### Post by sdowney717 on 2012-11-17
how do you add this ppa to the system?

---

### Post by moocow1452 on 2012-11-17
> **sdowney717 said:**
> how do you add this ppa to the system?

```
sudo add-apt-repository ppa:compholio

```

At least, once it's fully baked. Right now it's throwing up a 404, which I am guessing means, "I'm not quite ready yet."

---

### Post by mamamia88 on 2012-11-17
so how long until these patches get integrated into main branch wine?

---

### Post by lovinglinux on 2012-11-17
> **moocow1452 said:**
> ```
sudo add-apt-repository ppa:compholio

```

At least, once it's fully baked. Right now it's throwing up a 404, which I am guessing means, "I'm not quite ready yet."

Download the deb packages manually and install them.

---

### Post by lovinglinux on 2012-11-17
I have downloaded the packages from the ppa and installed without issues.It adds a Netflix icon to the application list, which launches a fullscreen Netflix window. Pretty cool. However, it doesn't recognize the silverlight plugin. It asks for me to download it, which I did, but then it still doesn't recognize it.

I am running a 64bit system and I suspect that is the issue. I have installed the 64bit netflix-desktop package, but the wine-compholio is 32bit only, as is the vanilla wine.

Anyone running it on a 32bit system?

---

### Post by moocow1452 on 2012-11-17
32bit system, same thing that happened yesterday. Asks for a Silverlight install, and doesn't recognise the one already there. I did manually patch wine and try that route, so maybe it has it's lines crossed. Also using Peppermint 3, and while it's using the precise archives, it may not play nice with something or other.

---

### Post by sdowney717 on 2012-11-17
Why does it work for some and not others. Must be some difference and I hope someone can find out. It does not work for me, asks to install silverlight.

You can go to a test site for silverlight to see if it works, for me it does not work.
[http://bubblemark.com/silverlight2.html](http://bubblemark.com/silverlight2.html)

I could see in future if Netflix requires silverlight v5 then v4 will never work.

---

### Post by moocow1452 on 2012-11-17
Me neither. I'm thinking it's an issue with the cobbled together WINE, since vanilla at least recognizes Silverlight, at least when I last tried it.

---

### Post by evilsoup on 2012-11-17
> **moocow1452 said:**
> ```
sudo add-apt-repository ppa:compholio

```At least, once it's fully baked. Right now it's throwing up a 404, which I am guessing means, "I'm not quite ready yet."

Actually, it's
```
sudo add-apt-repository ppa:ehoover/compholio
```

But I can't get netflix-desktop to install...
```
evilsoup@enchantment:~$ sudo apt-get install netflix-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 wine-compholio : Recommends: wine-gecko1.8 but it is not installable
                  Recommends: wine-mono0.0.8 but it is not installable
                  Conflicts: wine1.4 but 1.4-0ubuntu4.1 is to be installed
 wine1.4 : Depends: wine1.4-i386 (= 1.4-0ubuntu4.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
evilsoup@enchantment:~$ 
```

---

### Post by moocow1452 on 2012-11-17
Try downloading wine-compholio first or manually downloading the wine and netflix-debs, seems to mesh with adding the ppa.

---

### Post by evilsoup on 2012-11-17
I ended up using
```
sudo apt-get install wine-compholio+
```
which removed all my previous wine stuff, and then sudo apt-get install netflix-desktop worked... but it can't seem to detect the silverlight plugin...

---

### Post by weasel fierce on 2012-11-17
Installed the packages from the PPA, you still have to download firefox and silverlight it seems (navigate to the "program files" folder and do
wget -O Firefox-14.0.1.exe [http://download.mozilla.org/?product=firefox-14.0.1-funnelcake13&os=win&lang=en-US;](http://download.mozilla.org/?product=firefox-14.0.1-funnelcake13&os=win&lang=en-US;) wine Firefox-14.0.1.exe /S

wget -O Silverlight-4.exe [http://silverlight.dlservice.microsoft.com/download/6/A/1/6A13C54D-3F35-4082-977A-27F30ECE0F34/10329.00/runtime/Silverlight.exe;](http://silverlight.dlservice.microsoft.com/download/6/A/1/6A13C54D-3F35-4082-977A-27F30ECE0F34/10329.00/runtime/Silverlight.exe;) wine Silverlight-4.exe /q

as per the website instructions. 
I couldn't get the icon launcher to work, but if I run the firefox exe, and then go to Netflix, it works!
Watching right now :)


Holy smokes.. Netflix hack and Steam for linux, what's next?

---

### Post by dniMretsaM on 2012-11-17
It appears that the latest 64-bit builds of [FONT=Courier New]netflix-desktop[/FONT] failed. Guess I won't be trying it for a while.

---

### Post by weasel fierce on 2012-11-17
I should add, I am on 32 bit. 

Doesn't 64 bit Ubuntu support running 32 bit stuff anyways? Might be worth a shot, or is that not so easy?

---

### Post by dniMretsaM on 2012-11-17
Well, I'm downloading the latest build (0.1.0) on my 64-bit Quantal machine. I'll test it out and report back.

EDIT: Everything installs just fine, but I get error 1001 (which is a Silverlight-related issue). I'm going to see if I can get any information from the developer. Will post if I find out anything.

---

### Post by BluPhenix316 on 2012-11-18
> **dniMretsaM said:**
> Well, I'm downloading the latest build (0.1.0) on my 64-bit Quantal machine. I'll test it out and report back.

EDIT: Everything installs just fine, but I get error 1001 (which is a Silverlight-related issue). I'm going to see if I can get any information from the developer. Will post if I find out anything.

I know how to fix the 1001 error. You need to install mscorefonts.

---

### Post by dniMretsaM on 2012-11-18
> **BluPhenix316 said:**
> I know how to fix the 1001 error. You need to install mscorefonts.

Yep, just found that out. Installed it a few minutes ago and it works fine. For those who don't know how, run this command:
```
sudo apt-get install ttf-mscorefonts-installer
```

Anyway, some new packages are building as I write this. The [FONT=Courier New]netflix-desktop[/FONT] package will automatically pull in [FONT=Courier New]ttf-mscorefonts-installer[/FONT] as a dependency, and [FONT=Courier New]wine-compholio[/FONT] won't require the removal of vanilla WINE.

Also, there are apparently some issues with the EXT3 filesystem. Not exactly sure what they are or how to fix them, but I know that Erich is working on instructions regarding those problems.

---

### Post by sdowney717 on 2012-11-18
Works for me now:)

I opened  synaptic and did a total removal of all wine related stuff

Then add repository
 sudo add-apt-repository ppa:ehoover/compholio

Then did update
 sudo apt-get  update

Then did wine install
 sudo apt-get install wine-compholio+

Then did netflix desktop install
 sudo apt-get install netflix-desktop

I also did winecfg
 winecfg

Then find netflix desktop and click on icon, it will do some configuring


interesting to see netflix
this shows the progress, silverlight installs
```
scott@scott-P5QC:~$  sudo apt-get install netflix-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcogl8 libbabl-0.0-0 libgegl-0.0-0 kwrite p7zip kde-baseapps
  libtelepathy-farstream1 apport-hooks-medibuntu plasma-widget-folderview
  libllvm3.0
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  netflix-desktop
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,094 kB of archives.
After this operation, 15.2 MB of additional disk space will be used.
Get:1 http://ppa.launchpad.net/ehoover/compholio/ubuntu/ precise/main netflix-desktop i386 0.1.0~precise8 [6,094 kB]
Fetched 6,094 kB in 7s (790 kB/s)                                              
Selecting previously unselected package netflix-desktop.
(Reading database ... 657708 files and directories currently installed.)
Unpacking netflix-desktop (from .../netflix-desktop_0.1.0~precise8_i386.deb) ...
Processing triggers for update-notifier-common ...
netflix-desktop: downloading http://download.mozilla.org/?product=firefox-14.0.1-funnelcake13&os=win&lang=en-US
netflix-desktop: downloading http://silverlight.dlservice.microsoft.com/download/6/A/1/6A13C54D-3F35-4082-977A-27F30ECE0F34/10329.00/runtime/Silverlight.exe
netflix-desktop: downloading http://developer.netflix.com/files/Netflix_API2_57x57.png

Silverlight is provided by Microsoft in unmodified form only,
you may not redistribute the software.

Everything downloaded and installed.
Processing triggers for menu ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up netflix-desktop (0.1.0~precise8) ...
Processing triggers for menu ...

```

first pic shows purge existing wine to start fresh
second pic shows netflix running displaying Poirot

Netflix desktop opens in a full screen browser view, how to escape I hit function keys and was able to get a window.

---

### Post by evilsoup on 2012-11-18
I must have done something wrong, since it's not working for me... probably to do with installing it too early, before the PPA was properly ready. I guess I'll ppa-purge, and try again.

---

### Post by sdowney717 on 2012-11-18
My video card is likely not powerful enough as I notice that in the time I took to post the prior message with netflix paused, going back to netflix, the window had hung on the video. Hit space bar and the audio started and took a minute for the video to catch up and play.
Running an Nvidia geforce 8400gs with Nvidia drivers
I am on 12.04 ubuntu

---

### Post by lovinglinux on 2012-11-18
> **sdowney717 said:**
> Works for me now:)

I opened  synaptic and did a total removal of all wine related stuff

Then add repository
 sudo add-apt-repository ppa:ehoover/compholio

Then did update
 sudo apt-get  update

Then did wine install
 sudo apt-get install wine-compholio+

Then did netflix desktop install
 sudo apt-get install netflix-desktop

I also did winecfg
 winecfg

Then find netflix desktop and click on icon, it will do some configuring


interesting to see netflix
this shows the progress, silverlight installs
```
scott@scott-P5QC:~$  sudo apt-get install netflix-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcogl8 libbabl-0.0-0 libgegl-0.0-0 kwrite p7zip kde-baseapps
  libtelepathy-farstream1 apport-hooks-medibuntu plasma-widget-folderview
  libllvm3.0
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  netflix-desktop
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,094 kB of archives.
After this operation, 15.2 MB of additional disk space will be used.
Get:1 http://ppa.launchpad.net/ehoover/compholio/ubuntu/ precise/main netflix-desktop i386 0.1.0~precise8 [6,094 kB]
Fetched 6,094 kB in 7s (790 kB/s)                                              
Selecting previously unselected package netflix-desktop.
(Reading database ... 657708 files and directories currently installed.)
Unpacking netflix-desktop (from .../netflix-desktop_0.1.0~precise8_i386.deb) ...
Processing triggers for update-notifier-common ...
netflix-desktop: downloading http://download.mozilla.org/?product=firefox-14.0.1-funnelcake13&os=win&lang=en-US
netflix-desktop: downloading http://silverlight.dlservice.microsoft.com/download/6/A/1/6A13C54D-3F35-4082-977A-27F30ECE0F34/10329.00/runtime/Silverlight.exe
netflix-desktop: downloading http://developer.netflix.com/files/Netflix_API2_57x57.png

Silverlight is provided by Microsoft in unmodified form only,
you may not redistribute the software.

Everything downloaded and installed.
Processing triggers for menu ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up netflix-desktop (0.1.0~precise8) ...
Processing triggers for menu ...

```

first pic shows purge existing wine to start fresh
second pic shows netflix running displaying Poirot

Netflix desktop opens in a full screen browser view, how to escape I hit function keys and was able to get a window.

I tried the same method, but it complained about winecfg not being installed and suggested installing wine1.4, which I didn't do. Instead I tried to launch  Netflix Desktop and it prompted me to install Mono which I did. After completing Mono download it started and....

IT WORKS!!!!!!! WOOOHOOO!

Thanks a lot for the solution.

---

### Post by lovinglinux on 2012-11-18
After launching Netflix Dekstop, I hit F11 to leave fullscreen mode, then I can use Netflix fullscreen button.

---

### Post by sdowney717 on 2012-11-18
> **lovinglinux said:**
> After launching Netflix Dekstop, I hit F11 to leave fullscreen mode, then I can use Netflix fullscreen button.


None of the function buttons work anymore. 
Earlier I was even showing the Firefox file menu with one of the function keys.
I full screen using the silverlight full screen button, but still shows a gnome title bar at the top.

So how to make it take over the entire screen as before?
I am using the gnome3 desktop.

---

### Post by sdowney717 on 2012-11-18
Solved it
Too many chrome tabs open, perhaps 25 and a slow video card. Closed chrome and F11 toggles full screen ok.
But also found out cant do that if a video is running, so do the F11 key in the movie selection page.

F10 will show the menus.
If you click help then about, you can do an update to firefox.
It will run and update Firefox. Fiefox will update to ver 16
I did that and it is still fine.

So I am now using ver 16 funnelcake with netflix

You can also open a new tab, but it acts oddly

I dont see a way to opne an address bar to type a http web place.

---

### Post by dniMretsaM on 2012-11-18
> **sdowney717 said:**
> I dont see a way to opne an address bar to type a http web place.

You're not supposed to. The [FONT=Courier New]Netflix-desktop[/FONT] package is just supposed to be a standalone app. You can, however, use Firefox itself (the one installed in WINE) to browse around.

---

### Post by sdowney717 on 2012-11-18
Get this.
After I uodate to ver16 firefox, I can now got to wine directory and click the firefox Icon
It did a wine cdonfig update then 
It loads firefox with an address bar
then I can goto Netflix
login 
watch movie with the address bar!
Run this without the netflix desktop firefox.

---

### Post by sdowney717 on 2012-11-18
Wonder if Chrome for windows would work with this
Never been able to install Chrome under wine.

---

### Post by evilsoup on 2012-11-18
OK, it's working now... but the video's a little too jumpy for me, lol. But then, netbook etc.

Alt+D lets you go to other websites within the netflix app, if you want to... Lovefilm.com instant streaming wasn't working for me at all, though :(

---

### Post by sdowney717 on 2012-11-18
My video is smooth enough to watch. I can tell the video card lacks the power to feel effortless.

You can update to firefox v16 from firefox, just hit F10, click help about and upgrade it. Everything is still working including the version I have in the wine directory which shows adresses and tabs.

Silverlight 5 did some big improvements using hardware acceleration on the video. Wonder if that version could ever work with this.

---

### Post by weasel fierce on 2012-11-18
> **sdowney717 said:**
> Get this.
After I uodate to ver16 firefox, I can now got to wine directory and click the firefox Icon
It did a wine cdonfig update then 
It loads firefox with an address bar
then I can goto Netflix
login 
watch movie with the address bar!
Run this without the netflix desktop firefox.

Yeah, the desktop app doesn't work for me (it complains it can't find Firefox, so it's probably something fixable) but launching firefox in wine totally works :)

---

### Post by neu5eeCh on 2012-11-18
> **sdowney717 said:**
> Works for me now:)

I opened  synaptic and did a total removal of all wine related stuff

Then add repository
 sudo add-apt-repository ppa:ehoover/compholio

Then did update
 sudo apt-get  update  etc.....

I tried the same method. Installed Mono and nothing happens. Nothing works. Hmmm... I also got complaints about Gecko (?) and being unable to create a certain Firefox directory. I guess I'll purge and try to re-install?

---

### Post by lovinglinux on 2012-11-18
> **VTPoet said:**
> I tried the same method. Installed Mono and nothing happens. Nothing works. Hmmm... I also got complaints about Gecko (?) and being unable to create a certain Firefox directory. I guess I'll purge and try to re-install?

A purge is a good idea.

---

### Post by weasel fierce on 2012-11-18
Agreed, can't hurt to purge everything wine related in the package manager.

---

### Post by dniMretsaM on 2012-11-18
> **weasel fierce said:**
> Agreed, can't hurt to purge everything wine related in the package manager.

The latest builds shouldn't require you to remove vanilla WINE. Anyway, I added installation instructions to the first post, including what to do if you use EXT2/3.

---

### Post by weasel fierce on 2012-11-18
Gotcha. It's updating very rapidly. I installed last night, and already had an update this morning. 

Has anyone gotten the desktop app working btw?

---

### Post by dniMretsaM on 2012-11-18
> **weasel fierce said:**
> Gotcha. It's updating very rapidly. I installed last night, and already had an update this morning. 

Has anyone gotten the desktop app working btw?

The desktop app works just fine for me. I'm currently using [FONT=Courier New]netflix-desktop 0.1.0~quantal8[/FONT] and [FONT=Courier New]wine-compholio 1.5.17~quantal11[/FONT]. This is a 64-bit machine. Last nights builds worked just fine for me as well.

---

### Post by neu5eeCh on 2012-11-18
The install is complaining about a Gecko package needed for "applications embedding HTML". Do I install or cancel?

---

### Post by dniMretsaM on 2012-11-18
> **VTPoet said:**
> The install is complaining about a Gecko package needed for embedded HTML applications. Do I install it or cancel?

Yeah, go for it. That's a WINE thing in general, not specific to the Netflix app.

---

### Post by neu5eeCh on 2012-11-18
> **dniMretsaM said:**
> Yeah, go for it. That's a WINE thing in general, not specific to the Netflix app.

OK. Am installing. Now I get the following whine from wine:
> 
Error creating directory:

%SystemDrive%\Program Files\Mozilla Firefox\distribution

Click Cancel to stop the installation or Retry to try again.Do I need to install Wine 1.4. What does the following mean:

"Then did netflix desktop install
 sudo apt-get install netflix-desktop

I also did winecfg
 winecfg"

What does "I also did" mean? I notice that the next respondent did *not* install Wine 1.4, but the whole thing still worked for him?

**Edit:** OK. I canceled. Retry isn't working and isn't going to. Now I'm installing Wine 1.4. Argh! Why the _flip_ am I the only one who can't do this? :evil:

---

### Post by sdowney717 on 2012-11-18
Perhaps a permission problem regarding ownership with creating a directory
[http://ubuntuforums.org/showthread.php?t=1732304](http://ubuntuforums.org/showthread.php?t=1732304)

When doing this earlier, I failed to mention I had after purging the entire wine programs via synaptic, deleted my hidden .wine folder in my home directory.
Which I dont know makes a difference.

here is what I currently list as installed for wine listed out when doing a search for 'wine'
libkwineffects is I dont think a wine related program

---

### Post by dniMretsaM on 2012-11-18
> **VTPoet said:**
> OK. Am installing. Now I get the following whine from wine:
Do I need to install Wine 1.4. What does the following mean:

"Then did netflix desktop install
 sudo apt-get install netflix-desktop

I also did winecfg
 winecfg"

What does "I also did" mean? I notice that the next respondent did *not* install Wine 1.4, but the whole thing still worked for him?

OK. I canceled. Retry isn't working and isn't going to. Now I'm installing Wine 1.4. Argh! Why the &^%$ am I the only one who can't do this? :-?

I don't have any other versions of WINE installed. Just [FONT=Courier New]wine-compholio[/FONT]. Non of the other versions will work since you need some patches. You might also want to make sure you're using the latest versions of the packages. And are you using EXT2/3? As for the "I also did," I think he just means he ran the command [FONT=Courier New]winecfg[/FONT].

---

### Post by sdowney717 on 2012-11-18
> "I also did," I think he just means he ran the command winecfg
yes exactly true, whether needed or not.

I noticed when first clicking on the Netflix desktop icon, it ran a configuaration program which took a little while to complete.

---

### Post by neu5eeCh on 2012-11-18
@ dniMretsaM "As for the "I also did," I think he just means he ran the command [FONT=Courier New]winecfg[/FONT]."

Yes, but you can't run it without Wine 1.4 installed.

@ sdowney717 "Perhaps a permission problem regarding ownership with creating a directory..."

[strikethru]Possibly. Do I need to run Netflix-Desktop from the command line then, as Sudo?[/strikethru] Never mind. Didn't work.

---

### Post by dniMretsaM on 2012-11-18
> **VTPoet said:**
> Yes, but you can't run it without Wine 1.4 installed.

Then don't do it. It's not necessary (I didn't do it). Wine will do that itself the first time it runs, but it might take a while.

So what errors are you getting when you try to run the app?

---

### Post by sdowney717 on 2012-11-18
> Do I need to run Netflix-Desktop from the command line then, as Sudo
No, I just clicked on it. It ran a config program which took longer than I would have thought and then it was there, full screen netflix home page.

---

### Post by neu5eeCh on 2012-11-18
> **dniMretsaM said:**
> Then don't do it. It's not necessary (I didn't do it). Wine will do that itself the first time it runs, but it might take a while.

So what errors are you getting when you try to run the app?

This: 

> wine: cannot find 'C:\Program Files\Mozilla Firefox\firefox.exe'
So... what this tells me is that Firefox couldn't be installed because Wine 1.4 wasn't installed?!?

So, I've installed wine 1.4, purged both wine-comphio and netflix-desktop (including deleting the hidden folder in my home folder) and am re-installing both with wine 1.4 *present*. We'll see if I'm right...

---

### Post by weasel fierce on 2012-11-18
> **VTPoet said:**
> This: 

So... what this tells me is that Firefox couldn't be installed because Wine 1.4 wasn't installed?!?

So, I've installed wine 1.4, purged both wine-comphio and netflix-desktop (including deleting the hidden folder in my home folder) and am re-installing both with wine 1.4 *present*. We'll see if I'm right...

Running the desktop app from console, that's what I got as well.

If you run the firefox.exe with wine, it should work fine. (using the wine from the ppa, not regular wine)

---

### Post by neu5eeCh on 2012-11-18
> **weasel fierce said:**
> Running the desktop app from console, that's what I got as well.

If you run the firefox.exe with wine, it should work fine. (using the wine from the ppa, not regular wine)

Yeah. OK.

I got it to work by installing Wine 1.4 (winecfg) and *then* installing comphio and Netflix-Desktop.

I *officially* blame _y'all_.

On the other hand, in the interest of full-disclosure, I am using Xubuntu and was attempting to run Netflix-Desktop from Synapse. Until I installed Wine 1.4 [sudo apt-get install wine1.4], the Netflix-Desktop install didn't have a directory structure *into which* it could install Firefox, hence the error message that it couldn't create the Firefox directory.

In the meantime, it's flippin' cool to see Netflix on my Linux install! :guitar:

---

### Post by dniMretsaM on 2012-11-18
> **VTPoet said:**
> This: 

So... what this tells me is that Firefox couldn't be installed because Wine 1.4 wasn't installed?!?

So, I've installed wine 1.4, purged both wine-comphio and netflix-desktop (including deleting the hidden folder in my home folder) and am re-installing both with wine 1.4 *present*. We'll see if I'm right...

The Netflix app doesn't need WINE 1.4 (I don't have it and it works fine for me). Actually, it won't work with any other WINE than [FONT=Courier New]wine-compholio[/FONT] because of some patches that are necessary. A purge and a reinstall can't hurt, though.

Anyway, glad you got it working. Not entirely sure what the issue was, but whatever works.

---

### Post by neu5eeCh on 2012-11-18
> **dniMretsaM said:**
> The Netflix app doesn't need WINE 1.4 

My installation begs to differ.


> **dniMretsaM said:**
> (I don't have it and it works fine for me). Actually, it won't work with any other WINE than [FONT=Courier New]wine-compholio[/FONT] because of some patches that are necessary. A purge and a reinstall can't hurt, though.

Yeah... well... tell that to my fully functional battlest... I mean... netflix-desktop on wine 1.4.

---

### Post by Beardedturtle on 2012-11-18
> **evilsoup said:**
> Whoa.
*Yes*.

I'll *probably* wait for the PPA mentioned in the article, but this looks really cool! Does anyone know if it would be possible to install this version of wine alongside my current version, by compiling it differently?

This should work for other silverlight-DRM sites like Lovefilm, right? This issue is the only thing that stops me from recommending Ubuntu to people... obviously an official, supported solution would be best, but this is such great news.

The chromebook version uses a hardware chip for DRM, IIRC, so that's not really portable to Ubuntu.

PPA
[http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html](http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html)

---

### Post by lovinglinux on 2012-11-18
> **dniMretsaM said:**
> The desktop app works just fine for me. I'm currently using [FONT=Courier New]netflix-desktop 0.1.0~quantal8[/FONT] and [FONT=Courier New]wine-compholio 1.5.17~quantal11[/FONT]. This is a 64-bit machine. Last nights builds worked just fine for me as well.

I think he means the Firefox launcher saved inside the Desktop folder. It doesn't work for me. Only the Netflix Desktop launcher I access by searching gnome-shell/dash. I tried to copy the launcher and add it to the dock, but it doesn't work either.

---

### Post by sdowney717 on 2012-11-18
I am using gnome3 and can run firefox from this wine folder and play netflix. I actually prefer this over the netflix app.

lousy picture taken with my camera since I dont know how to screen capture that image.

---

### Post by Beardedturtle on 2012-11-18
> **sdowney717 said:**
> I am using gnome3 and can run firefox from this wine folder and play netflix. I actually prefer this over the netflix app.

lousy picture taken with my camera since I dont know how to screen capture that image.

Hit the print screen button on the keyboard.

---

### Post by spook1980 on 2012-11-18
he's running gnome shell, print screen won't do the trick, what he should do is search for screanshot from the dash, and do it that way.

---

### Post by weasel fierce on 2012-11-18
> **VTPoet said:**
> Yeah. OK.

I got it to work by installing Wine 1.4 (winecfg) and *then* installing comphio and Netflix-Desktop.

I *officially* blame _y'all_.

On the other hand, in the interest of full-disclosure, I am using Xubuntu and was attempting to run Netflix-Desktop from Synapse. Until I installed Wine 1.4 [sudo apt-get install wine1.4], the Netflix-Desktop install didn't have a directory structure *into which* it could install Firefox, hence the error message that it couldn't create the Firefox directory.

In the meantime, it's flippin' cool to see Netflix on my Linux install! :guitar:


Strange but hey, if it works, it works :D
It IS quite a cool feeling, isn't it?

as an aside, Vermont is awesome.

---

### Post by sdowney717 on 2012-11-18
I tried screenshot. What happens is it loads a browser window.
I have used screenshot a lot. 
It just wont take a pic of the gnome menu.

[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/29894](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/29894)
you can do a screenshot delay

---

### Post by neu5eeCh on 2012-11-18
> **weasel fierce said:**
> Strange but hey, if it works, it works :D
It IS quite a cool feeling, isn't it?

as an aside, Vermont is awesome.

It might have had something to do with trying to run it through Synapse, but I'm not sure why it should matter. 

And, yeah, I love Vermont. The only other place I could imagine living is maybe northern CA.

So... now that they've cracked this nut, what about Silverlight 5? How long are we going to be able to use Netflix with Silverlight 4, and does it matter? This is a flippin' amazing accomplishment in my view. I wonder if they're going to try to crack 5?

---

### Post by sdowney717 on 2012-11-18
> **VTPoet said:**
> It might have had something to do with trying to run it through Synapse, but I'm not sure why it should matter. 

And, yeah, I love Vermont. The only other place I could imagine living is maybe northern CA.

So... now that they've cracked this nut, what about Silverlight 5? How long are we going to be able to use Netflix with Silverlight 4, and does it matter? This is a flippin' amazing accomplishment in my view. I wonder if they're going to try to crack 5?

That would be very good as it brings video hardware acceleration.
So lower quality video cards will be very smooth

---

### Post by Beardedturtle on 2012-11-18
After following all steps Netflix will refuse to load and  firefox refuses to install from wine it will say access is denied

---

### Post by sdowney717 on 2012-11-18
I found if you right click the screen, silverlight presents a menu which includes an automatic upgrade.
If I checked it, I wonder if silverlight would upgrade itself and then break ability to play netflix?

here is a video site that requires I think silverlight5.
If you go there ad attempt an upgrade, you eventually will be suggested to install monkeylight v4

[http://rtl.nl/xl/#/u/749dc8fa-9976-4239-b392-75b849dc84c7](http://rtl.nl/xl/#/u/749dc8fa-9976-4239-b392-75b849dc84c7)

---

### Post by sdowney717 on 2012-11-18
> **Beardedturtle said:**
> After following all steps Netflix will refuse to load and  firefox refuses to install from wine it will say access is denied

What exactly did you do?

I did these steps
I also deleted .wine hidden folder in my home directory after purging wine. Another poster said he needed wine v1.4 to do a winecfg which I did not need.

> 
I opened synaptic and did a total removal of all wine related stuff

Then add repository
sudo add-apt-repository ppa:ehoover/compholio

Then did update
sudo apt-get update

Then did wine install
sudo apt-get install wine-compholio+

Then did netflix desktop install
sudo apt-get install netflix-desktop

I also did winecfg
winecfg

Then find netflix desktop and click on icon, it will do some configuring

after this it worked. I was able to logon

---

### Post by Beardedturtle on 2012-11-18
**wget -O Firefox-14.0.1.exe  [http://download.mozilla.org/?product=firefox-14.0.1-funnelcake13&os=win&lang=en-US;](http://download.mozilla.org/?product=firefox-14.0.1-funnelcake13&os=win&lang=en-US;)  wine Firefox-14.0.1.exe /S**


I get a corrupt file warning with this command.

---

### Post by GrubThemeArtist on 2012-11-18
> **Beardedturtle said:**
> **wget -O Firefox-14.0.1.exe  [http://download.mozilla.org/?product=firefox-14.0.1-funnelcake13&os=win&lang=en-US;](http://download.mozilla.org/?product=firefox-14.0.1-funnelcake13&os=win&lang=en-US;)  wine Firefox-14.0.1.exe /S**


I get a corrupt file warning with this command.

There's a PPA now.

[http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html](http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html)

---

### Post by sdowney717 on 2012-11-18
> **Beardedturtle said:**
> **wget -O Firefox-14.0.1.exe  [http://download.mozilla.org/?product=firefox-14.0.1-funnelcake13&os=win&lang=en-US;](http://download.mozilla.org/?product=firefox-14.0.1-funnelcake13&os=win&lang=en-US;)  wine Firefox-14.0.1.exe /S**


I get a corrupt file warning with this command.

Post number 100 shows how I did this. 
Worked for me

---

### Post by neu5eeCh on 2012-11-18
Just installed Netflix Desktop on my 64-bit system. Same problem. Had to install Wine 1.4 before it would work. Unless I installed Wine, the Netflix Desktop config had no place to install Firefox.

---

### Post by sdowney717 on 2012-11-18
> **VTPoet said:**
> Just installed Netflix Desktop on my 64-bit system. Same problem. Had to install Wine 1.4 before it would work. Unless I installed Wine, the Netflix Desktop config had no place to install Firefox.

64 bit issue ?
I am running 32 bit.
I had completely purged all wine and it installed ok.

---

### Post by sdowney717 on 2012-11-18
A bug exists which will be fixed if your using ext3 filesystem
[http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html](http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html)
> 
Anne Fairchild Guillaume Voisine • 2 hours ago

You need to edit the /usr/bin/netflix-desktop file. Line 32 is checking the wrong variable. It should be ${MTABXATTR} NOT ${MTABEXT} It's a bug.
2
•
Reply
•
Share ›

    Avatar
    Erich Hoover Anne Fairchild • an hour ago

    Thank you for pointing that out, I'll upload a fix shortly.
    0
    •
    Reply
    •
    Share ›


---

### Post by jerome1232 on 2012-11-18
It's working on my netbook with no modifications but it's too choppy to be of any use :(

Checking it's system specs I just realized I accidentally installed 64 bit 12.10 instead of 32 bit 12.04 on it. haha, I'll have to fix that. Seems to be cpu bound, it does work nativly on windows, I'm guessing there's some wine slowdown.

---

### Post by lovinglinux on 2012-11-18
> **sdowney717 said:**
> 64 bit issue ?
I am running 32 bit.
I had completely purged all wine and it installed ok.

I am running a 64bit and did not installed Wine 1.4 and it works. I also purged before installing the ppa, just like you did.

---

### Post by dniMretsaM on 2012-11-18
> **sdowney717 said:**
> 64 bit issue ?
I am running 32 bit.
I had completely purged all wine and it installed ok.

I installed it on my 64-bit machine with no issues. I'm wondering if you have to install a version of WINE once or it won't work (even if vanilla WINE isn't installed when running Netflix). I think I'll send Erich an email about it when I get home.

---

### Post by jerome1232 on 2012-11-18
> **dniMretsaM said:**
> I installed it on my 64-bit machine with no issues. I'm wondering if you have to install a version of WINE once or it won't work (even if vanilla WINE isn't installed when running Netflix). I think I'll send Erich an email about it when I get home.

My netbook was a fresh, unused install of 12.10 64 bit, hot off the usb stick. All I did was add the ppa, install wine-compoholio+, netflix-desktop, then started it up and it worked. It's literally the first thing I did after doing the updates on a fresh install.

---

### Post by lovinglinux on 2012-11-18
My experience so far:

[LIST=1]
[*]Installation from PPA was smooth, after purging vanila Wine and Crossover. It complained about Wine 1.4 when I tried to run winecfg, but I didn't install it. However I did install Mono as requested. Worked out of the box!!!

[*]Performance is great, with no stuttering. Video quality is good. I had the impression I was getting lower quality, but tested an HD movie and it was okay.

[*]Temperature while watching an HD movie is 60-65º Celsius, which is lower than running Netflix on a VM with XP.

[*]I am running Ubuntu 12.10 64bit with Gnome-Shell instead of Unity. My Notebook is an Asus A43E with an i5 CPU, 6GB of RAM and Intel HD 3000 graphics.
[/LIST]

---

### Post by weasel fierce on 2012-11-18
> **dniMretsaM said:**
> I installed it on my 64-bit machine with no issues. I'm wondering if you have to install a version of WINE once or it won't work (even if vanilla WINE isn't installed when running Netflix). I think I'll send Erich an email about it when I get home.

I had wine installed previously, and removed it before doing this, so there might be something to it.

---

### Post by neu5eeCh on 2012-11-18
On both my machines installation failed because there were no Window directories into which to install Firefox. Simple as that. I had to install Wine 1.4 in order to create the Windows directory structure.

---

### Post by weasel fierce on 2012-11-18
So that helps confirm it then. Interestingly purging wine might actually make more trouble, since it'd remove those structures, wouldn't it?

---

### Post by sdowney717 on 2012-11-18
> **weasel fierce said:**
> So that helps confirm it then. Interestingly purging wine might actually make more trouble, since it'd remove those structures, wouldn't it?

considering several people did purge and then installed ok then how could that come into play here?
I also removed my .wine home directory.
I was also able to run winecfg after the wine purge and new wine install.

---

### Post by weasel fierce on 2012-11-18
If in doubt, I blame Gnomes :)

---

### Post by neu5eeCh on 2012-11-18
> **sdowney717 said:**
> I was also able to run winecfg after the wine purge and new wine install.

OK, then you didn't uninstall wine. (?) According to apt-get, you couldn't have run winecfg without wine 1.4. Winecfg (again, according to apt-get) *depends* on wine 1.4. I'm wondering if some of you folks actually did what you think you did when you "purged" wine? Something doesn't add up.
[B]
Edit: [/B]Oh, scratch that. As you say, you re-installed wine. So how is what you did any different that what I did?

---

### Post by jerome1232 on 2012-11-18
On the 12.10 netbook, that was a fresh install. It can't run winecfg, but everything works. (aside from it being slow on netflix)

I have never installed wine on that netbook (aside from the wine-compholio+ package)

---

### Post by lovinglinux on 2012-11-18
I did some additional tests. 

- purged netflix and wine

- installed Wine 1.4, Crossover and Playonlinux

- Installed Firefox 16 and Silverlight on Wine 1.4, Crossover and Playonlinux

- Installed wine-compholio+ and netflix-desktop

- Only netflix-desktop works as expected with Netflix. Wine 1.4, Crossover and Playonlinux still work independently, but freeze when viewing Netflix.

Updated Firefox 14 to 16 from netflix-desktop and it stopped working. Removed, deleted the config folder and reinstalled netflix-desktop to make it work again.

---

### Post by sdowney717 on 2012-11-18
> **VTPoet said:**
> OK, then you didn't uninstall wine. (?) According to apt-get, you couldn't have run winecfg without wine 1.4. Winecfg (again, according to apt-get) *depends* on wine 1.4. I'm wondering if some of you folks actually did what you think you did when you "purged" wine? Something doesn't add up.
[B]
Edit: [/B]Oh, scratch that. As you say, you re-installed wine. So how is what you did any different that what I did?

The way I purged was using synaptic.
I searched for 'wine'
then right clicked the wine files and selected remove entirely with configuration

Of course afterwards, I installed the new patched wine from that repository for netflix.
Afterwards I ran winecfg and it ran.

---

### Post by sdowney717 on 2012-11-18
> **lovinglinux said:**
> I did some additional tests. 

- purged netflix and wine

- installed Wine 1.4, Crossover and Playonlinux

- Installed Firefox 16 and Silverlight on Wine 1.4, Crossover and Playonlinux

- Installed wine-compholio+ and netflix-desktop

- Only netflix-desktop works as expected with Netflix. Wine 1.4, Crossover and Playonlinux still work independently, but freeze when viewing Netflix.

Updated Firefox 14 to 16 from netflix-desktop and it stopped working. Removed, deleted the config folder and reinstalled netflix-desktop to make it work again.

I updated firefox to v16 from the Netflix app by hitting F10
to load menu. Then click help - about firefox

The small about window had an upgrade firefox button.
I clicked it upgraded to firefox v16
One of my screenshots I posted here shows it running netflix on v16

---

### Post by neu5eeCh on 2012-11-18
> **lovinglinux said:**
> I did some additional tests. 

- purged netflix and wine

- installed Wine 1.4, Crossover and Playonlinux

- Installed Firefox 16 and Silverlight on Wine 1.4, Crossover and Playonlinux

- Installed wine-compholio+ and netflix-desktop

- Only netflix-desktop works as expected with Netflix. Wine 1.4, Crossover and Playonlinux still work independently, but freeze when viewing Netflix.

Updated Firefox 14 to 16 from netflix-desktop and it stopped working. Removed, deleted the config folder and reinstalled netflix-desktop to make it work again.

Would be interested to see what would happen if you uninstalled Wine 1.4 without uninstalling wine-compholio+ and netflix-desktop, whether netflix desktop would still work?

---

### Post by neu5eeCh on 2012-11-18
> **sdowney717 said:**
> Of course afterwards, I installed the new patched wine from that repository for netflix.
Afterwards I ran winecfg and it ran.

What exactly did you install when you "installed the new patched wine"? sudo apt-get what? -- or what did you choose from synaptic?

---

### Post by sdowney717 on 2012-11-18
post number 56 listed what I did
page number 6

here is my synaptic showing only wine 1.5

---

### Post by sdowney717 on 2012-11-18
Ok, currently logged into tricia another user
ran winecfg and it runs
I had not done this yet.

```
tricia@scott-P5QC:~$ winecfg
wine: created the configuration directory '/home/tricia/.wine'
fixme:storage:create_storagefile Storage share mode not implemented.
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:iphlpapi:NotifyAddrChange (Handle 0x110e8d0, overlapped 0x110e8dc): stub
wine: configuration in '/home/tricia/.wine' has been updated.
tricia@scott-P5QC:~$ 


```

How would I get the netflix app to show up for this user?
Oh, It is now there!

---

### Post by neu5eeCh on 2012-11-18
> **sdowney717 said:**
> post number 56 listed what I did
page number 6

here is my synaptic showing only wine 1.5

Yeah. OK. 

> sudo apt-get install wine-compholio+


That's what I did too, but somehow that wasn't enough to create a directory for Firefox. So... no answer there...

---

### Post by axe.gs1 on 2012-11-18
Will this PPA be backported?  I'm still running 10.04, and ran into the failure with Silverlight when working on this.  

hoping...

---

### Post by neu5eeCh on 2012-11-18
> **axe.gs1 said:**
> Will this PPA be backported?  I'm still running 10.04, and ran into the failure with Silverlight when working on this.  

hoping...

I doubt it. Time to move on, don't ya' think? There are some excellent alternatives if you don't like Unity.

---

### Post by evilsoup on 2012-11-18
> **VTPoet said:**
> Yeah. OK. 


```
sudo apt-get install wine-compholio+                      
```That's what I did too, but somehow that wasn't enough to create a directory for Firefox. So... no answer there...

I would just like to say that I used that command because there was a conflict with regular wine, and putting a '+' at the end of a package name in apt-get forces that package to be favoured in the event of a conflict. And from what I've been reading, that problem should be fixed & there shouldn't be a conflict - so netflix-desktop should pull in wine-compholio as a dependency. No need to add it in a separate step.

The netflix-desktop program creates the directory structure at ~/.netflix-desktop either when it's installed or first run, rather than at ~/.wine, if that helps...

---

### Post by sdowney717 on 2012-11-18
ok here is the update to ver16.
you must take firefox off fullscreen hit F11
double click top bar to get window smaller
then hit F10 to display the menu
click help- about

firefox lists an update
click it
firefox downloads and restarts

here is before and after showing running with version14 then 16 after the update thru firefox itself

---

### Post by sdowney717 on 2012-11-18
> **VTPoet said:**
> I doubt it. Time to move on, don't ya' think? There are some excellent alternatives if you don't like Unity.

Install cinnamon works fine with netflix app
[http://askubuntu.com/questions/94201/how-do-i-install-the-cinnamon-desktop](http://askubuntu.com/questions/94201/how-do-i-install-the-cinnamon-desktop)

---

### Post by Werewolf6851 on 2012-11-18
I followed the instructions at
[http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html](http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html)

aka 
**sudo apt-add-repository ppa:ehoover/compholio**

[B]sudo apt-get update && sudo apt-get install netflix-desktop

[/B]it seemed to work, but when I when to play a movie I get an error

<quote>
Player Error
Error Code: 1001

We could not load the movie player. Please visit our help page for more details.
</quote>
==the help page was as follows==
<quote>
Silverlight Player Error

When you run into a problem loading the Netflix movie player:

If you are a Mac user, this may be caused by missing system fonts on your computer. If you use a font management system such as Suitcase, you might try the following steps | to address this problem:

    Check that at least one of these fonts is present in your HD/Library/Fonts folder:
        Arial (standard, bold, italic or bold italic)
        Verdana (standard, bold, italic or bold italic)
    If none of these fonts are present in the folder you'll need to install one:
        Locate one of these fonts elsewhere on your system, for example in the ~/Library/Fonts or /System/Library/Fonts folders
        Copy or move at least one of these fonts into your HD/Library/Fonts folder
    Attempt to play a movie again

If you don't use font management software or these steps don't solve the problem, please call us at 866-579-7113 and we'll help you solve the problem.
</quote>

I tried copying fonts from the windows partition but no avail

Wolf
Xubuntu 12.04 64 bit

---

### Post by sdowney717 on 2012-11-18
> **Werewolf6851 said:**
> I followed the instructions at
[http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html](http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html)

aka 
**sudo apt-add-repository ppa:ehoover/compholio**

[B]sudo apt-get update && sudo apt-get install netflix-desktop

[/B]it seemed to work, but when I when to play a movie I get an error

<quote>
Player Error
Error Code: 1001

We could not load the movie player. Please visit our help page for more details.
</quote>
==the help page was as follows==
<quote>
Silverlight Player Error

When you run into a problem loading the Netflix movie player:

If you are a Mac user, this may be caused by missing system fonts on your computer. If you use a font management system such as Suitcase, you might try the following steps | to address this problem:

    Check that at least one of these fonts is present in your HD/Library/Fonts folder:
        Arial (standard, bold, italic or bold italic)
        Verdana (standard, bold, italic or bold italic)
    If none of these fonts are present in the folder you'll need to install one:
        Locate one of these fonts elsewhere on your system, for example in the ~/Library/Fonts or /System/Library/Fonts folders
        Copy or move at least one of these fonts into your HD/Library/Fonts folder
    Attempt to play a movie again

If you don't use font management software or these steps don't solve the problem, please call us at 866-579-7113 and we'll help you solve the problem.
</quote>

I tried copying fonts from the windows partition but no avail

Wolf
Xubuntu 12.04 64 bit

As test, curious if you could try post 56 procedure on page 6 and see if it is any better,
also remove .wine and .netflix desktop hidden folder in your home directory before you reinstall

there may also be an issue with ext3 filesystems

---

### Post by GrubThemeArtist on 2012-11-18
Huh, I don't get why people are having to purge Wine.

I had Wine and Crossover installed, then I built Wine from git, and tried getting Netflix to work that way (which it didn't), then I just tried out the PPA and everything works fine.

---

### Post by spook1980 on 2012-11-19
> **Werewolf6851 said:**
> I followed the instructions at
[http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html](http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html)

aka 
**sudo apt-add-repository ppa:ehoover/compholio**

[B]sudo apt-get update && sudo apt-get install netflix-desktop

[/B]it seemed to work, but when I when to play a movie I get an error

<quote>
Player Error
Error Code: 1001

We could not load the movie player. Please visit our help page for more details.
</quote>
==the help page was as follows==
<quote>
Silverlight Player Error

When you run into a problem loading the Netflix movie player:

If you are a Mac user, this may be caused by missing system fonts on your computer. If you use a font management system such as Suitcase, you might try the following steps | to address this problem:

    Check that at least one of these fonts is present in your HD/Library/Fonts folder:
        Arial (standard, bold, italic or bold italic)
        Verdana (standard, bold, italic or bold italic)
    If none of these fonts are present in the folder you'll need to install one:
        Locate one of these fonts elsewhere on your system, for example in the ~/Library/Fonts or /System/Library/Fonts folders
        Copy or move at least one of these fonts into your HD/Library/Fonts folder
    Attempt to play a movie again

If you don't use font management software or these steps don't solve the problem, please call us at 866-579-7113 and we'll help you solve the problem.
</quote>

I tried copying fonts from the windows partition but no avail

Wolf
Xubuntu 12.04 64 bit

> **sdowney717 said:**
> As test, curious if you could try post 56 procedure on page 6 and see if it is any better,
also remove .wine and .netflix desktop hidden folder in your home directory before you reinstall

there may also be an issue with ext3 filesystems

I'm having the same issue 1001 error not using ext3 my file system is ext4 running ubuntu 12.04, i really don't want to have to do a reinstall either. msfonts are installed i dont know what the issue is

---

### Post by spook1980 on 2012-11-19
> **spook1980 said:**
> I'm having the same issue 1001 error not using ext3 my file system is ext4 running ubuntu 12.04, i really don't want to have to do a reinstall either. msfonts are installed i dont know what the issue is

got it this does the trick for all those with msfonts installed getting a 1001 error,

sudo apt-get install --reinstall ttf-mscorefonts-installer

---

### Post by monkeybrain2012 on 2012-11-19
Nice if they can get it working. I don't care for netflix myself but if this works I can put Ubuntu on a few people's computers now that the last hurdle is overcome. :)

BTW, does it only work on Ubuntu? I would think it should work on other distros too as long as you can compile wine.

---

### Post by lovinglinux on 2012-11-19
> **sdowney717 said:**
> I updated firefox to v16 from the Netflix app by hitting F10
to load menu. Then click help - about firefox

The small about window had an upgrade firefox button.
I clicked it upgraded to firefox v16
One of my screenshots I posted here shows it running netflix on v16

I did the same thing and it broke Netflix Desktop.

---

### Post by lovinglinux on 2012-11-19
> **VTPoet said:**
> Would be interested to see what would happen if you uninstalled Wine 1.4 without uninstalling wine-compholio+ and netflix-desktop, whether netflix desktop would still work?

It works without wine 1.4.

---

### Post by neu5eeCh on 2012-11-19
> **lovinglinux said:**
> It works without wine 1.4.

okay.

testing....

purging wine1.4....

aaaaaaaaaaaaand... yes sir'ee! It works without wine1.4. :)

Don't know why I needed it to install, but there you have it. The mystery continues...

---

### Post by spook1980 on 2012-11-19
Netflix on ubuntu runs like a dream, time to delete the windows partition

---

### Post by dniMretsaM on 2012-11-19
I did a few test installations (all on fresh Ubuntu installs). The first time, I got the error that VTPoet got. Installing vanilla WINE didn't help. I fixed the problem by purging [FONT=Courier New]netflix-desktop[/FONT], removing [FONT=Courier New]~/.netflix-deskotp/[/FONT], and reinstalling. The next two installs went without issue. I told Erich about this and he's looking into it.

---

### Post by Beardedturtle on 2012-11-19
It works but there is no sound. NOTHING AT ALL.

---

### Post by Werewolf6851 on 2012-11-19
Works on Xubuntu 12.04 64 bit.  

sudo apt-add-repository ppa:ehoover/compholio  

Removed all wine installations, deleted both hidden directories .wine and .netflix-desktop before retrying.  
Added ",user_xattr" to the fourth column of the root "/" line in fstab  

Then ran sudo apt-get install ttf-mscorefonts-installer 
sudo apt-get install netflix-desktop  

Video is bit choppy but I assuming that from just using on-motherboard video card.  
Wolf

---

### Post by theOGRE on 2012-11-19
This is great! I'm so happy I can finally watch netflix without kicking a kid off one of the game systems.  I was having these problems as well. Tried purge and reinstalling wine and such.  What seemed to finally work was when I removed ~/.netflix-desktop, as dniMretsaM  mentioned.

---

### Post by neu5eeCh on 2012-11-20
> **Beardedturtle said:**
> It works but there is no sound. NOTHING AT ALL.

Yeah... just tried installing Netflix on a friend's laptop. No sound. Nothing. Didn't have time to experiment.

**Edit: **I have the **black thumb** of linux. If there's an issue, I will have it.

---

### Post by Beardedturtle on 2012-11-20
> **VTPoet said:**
> Yeah... just tried installing Netflix on a friend's laptop. No sound. Nothing. Didn't have time to experiment.

**Edit: **I have the **black thumb** of linux. If there's an issue, I will have it.
Must be a WINE thing cause my games dont have sound must be a sound driver issue.

---

### Post by sdowney717 on 2012-11-20
An update was pushed out and afterwards I am having trouble with netflix desktop. 

trying to escape full screen I lose all mouse control, mouse is invisible and I can not stop back up or interact with the app or the computer. What I have been doing is logging out and log back in.
Moving the mouse will make the silverlight interactive on screen menus appear but no mouse.

I used to be able to hit F11 to toggle fullscreen.

back to running netflix in the firefox v16 full browser mode as the app is giving me issues.

---

### Post by Beardedturtle on 2012-11-20
I tried but cannot get audio out of wine no matter what settings I choose....uninstalling is not a option that would require redownloading steam and  3 games 10Gb total...as well as reinstalling netflix which was a 3 day nightmare.

---

### Post by sdowney717 on 2012-11-20
> **Beardedturtle said:**
> I tried but cannot get audio out of wine no matter what settings I choose....uninstalling is not a option that would require redownloading steam and  3 games 10Gb total...as well as reinstalling netflix which was a 3 day nightmare.

what does your winecfg look like, mine set to XP mode and can you play those test sounds?

---

### Post by Beardedturtle on 2012-11-20
> **sdowney717 said:**
> what does your winecfg look like, mine set to XP mode and can you play those test sounds?
Try it on XP and win 7 no go tried all the audio settings no go.

---

### Post by sdowney717 on 2012-11-20
> **Beardedturtle said:**
> Try it on XP and win 7 no go tried all the audio settings no go.

are you saying those test sounds in winecfg, you can not hear them?

how then can your games play sound?

---

### Post by Beardedturtle on 2012-11-20
> **sdowney717 said:**
> are you saying those test sounds in winecfg, you can not hear them?

how then can your games play sound?
That is the problem no sound in games or netflix. I came here from a failed bing and google searches for a fix. Torchlight 1 and 2 and Trine 2 play great but no sound.

---

### Post by BungaDunga on 2012-11-20
I also don't get sound. I have sound in my normal Wine prefix, but not the Netflix one.

Specifically, when I open up winecfg and swap to the audio tab, I see:

```
ALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave

```

It seems to be due to running a 32-bit Wine inside a 64-bit Ubuntu, see:
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/408615](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/408615)
And in gentoo:
[http://forums.gentoo.org/viewtopic-t-916116-start-0.html](http://forums.gentoo.org/viewtopic-t-916116-start-0.html)

HOWEVER, there's an easy easy fix.

```
sudo apt-get install libasound2-plugins:i386
```

seemed to do the trick.

---

### Post by Beardedturtle on 2012-11-20
> **BungaDunga said:**
> I also don't get sound. I have sound in my normal Wine prefix, but not the Netflix one.

Specifically, when I open up winecfg and swap to the audio tab, I see:

```
ALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave

```It seems to be due to running a 32-bit Wine inside a 64-bit Ubuntu, see:
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/408615](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/408615)
And in gentoo:
[http://forums.gentoo.org/viewtopic-t-916116-start-0.html](http://forums.gentoo.org/viewtopic-t-916116-start-0.html)

HOWEVER, there's an easy easy fix.

```
sudo apt-get install libasound2-plugins:i386
```seemed to do the trick.
 
Mine has HDA in front of the options for sound output and input. No ALSA or Pulseaudio.

---

### Post by Beardedturtle on 2012-11-20
> **BungaDunga said:**
> I also don't get sound. I have sound in my normal Wine prefix, but not the Netflix one.

Specifically, when I open up winecfg and swap to the audio tab, I see:

```
ALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave

```It seems to be due to running a 32-bit Wine inside a 64-bit Ubuntu, see:
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/408615](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/408615)
And in gentoo:
[http://forums.gentoo.org/viewtopic-t-916116-start-0.html](http://forums.gentoo.org/viewtopic-t-916116-start-0.html)

HOWEVER, there's an easy easy fix.

```
sudo apt-get install libasound2-plugins:i386
```seemed to do the trick.
Tried your trick and now the audio is 4x faster then normal >_< (games and netflix)

---

### Post by sdowney717 on 2012-11-21
I got stuck in the netflix app today. Mouse is working in the app, except can not x out of the program or do the upper left corner with gnome3.
So I could not close the app.

When it was stuck like this I tried alt-F2, this exposed the basic firefox menu. Then under file select exit and it closed.

---

### Post by sdowney717 on 2012-11-21
> **Beardedturtle said:**
> Tried your trick and now the audio is 4x faster then normal >_< (games and netflix)

You can try this. Someone in the wine forums had issues with sound speed and this helped.
[http://bugs.winehq.org/show_bug.cgi?id=31993](http://bugs.winehq.org/show_bug.cgi?id=31993)

> Erich Hoover 2012-11-07 17:26:47 CST
(In reply to comment #9)
> Update, I can play NetFlix on my 64bit Ubuntu after I created a 32bit PREFIX. 
> ...

Could you please create a new bug for the 64-bit failure and put a dependency
on this bug?

(In reply to comment #16)
> ...
> The sound and video problems come back after one movie or TV episode. I can
> resolve if I move the slider bar multiple times back and forth to 'sync' or
> 'slow' the sound and video to normal speed. Not sure if the logs would show
> this behaviour.

I've not noticed this particular issue, but when I do (rarely) notice audio
issues with Wine I've noticed that they can be resolved by executing
"**pulseaudio -k**".  You might give that a try.
Comment 18

---

### Post by dniMretsaM on 2012-11-21
> **sdowney717 said:**
> I got stuck in the netflix app today. Mouse is working in the app, except can not x out of the program or do the upper left corner with gnome3.
So I could not close the app.

When it was stuck like this I tried alt-F2, this exposed the basic firefox menu. Then under file select exit and it closed.

Use Alt+F4 to close it. AFAIK there is no way to use the close/minimize/maximize buttons.

---

### Post by sdowney717 on 2012-11-21
> **dniMretsaM said:**
> Use Alt+F4 to close it. AFAIK there is no way to use the close/minimize/maximize buttons.

I can see it needs to become more user friendly. Someone who does not know much about computers might use this app and when they cant exit will get ornery and pull the plug.

---

### Post by dniMretsaM on 2012-11-21
> **sdowney717 said:**
> I can see it needs to become more user friendly. Someone who does not know much about computers might use this app and when they cant exit will get ornery and pull the plug.

Send Erich an email about it. Personally, I have no problem with not having access to said buttons. I really don't think there are that many people who wont know how to close the window, but I suppose it couldn't hurt to have the buttons visible when you exit full screen.

---

### Post by sdowney717 on 2012-11-21
> **dniMretsaM said:**
> Send Erich an email about it. Personally, I have no problem with not having access to said buttons. I really don't think there are that many people who wont know how to close the window, but I suppose it couldn't hurt to have the buttons visible when you exit full screen.

found another way to configure the app, use alt+v and add the toolbars to get tabbed browsing, so far that works fine.
anyone doing the first tip?
> Tip: since the Netflix Desktop web app comes with just a window titlebar (no menu, tabs, address bar, etc.), if you want to use this custom Wine build with other websites that require the Microsoft Silverlight plugin, launch Firefox for Windows (Wine) from the newly created desktop shortcut. Or, to launch it from Unity&#8217;s Dash, search for &#8220;Mozilla Firefox&#8221; (the native Firefox application for Linux should show up as &#8220;Mozilla Firefox Browser&#8221; so the names are not identical).

Alternatively, in the Netflix Desktop web app, you can use F11 (to exit full screen), then press ALT + V and from the View > Toolbarmenu, enable the Menu Bar and Navigation Toolbar.
[http://www.reviewlinux.com/how-to-use-netflix-in-ubuntu-through-wine-ppa-available-9360.html](http://www.reviewlinux.com/how-to-use-netflix-in-ubuntu-through-wine-ppa-available-9360.html)

---

### Post by cybergalvez on 2012-11-21
This works great! Thansk for all the hard work now I don't have to start windows to watch Netflix!

---

### Post by Beardedturtle on 2012-11-21
> **sdowney717 said:**
> You can try this. Someone in the wine forums had issues with sound speed and this helped.
[http://bugs.winehq.org/show_bug.cgi?id=31993](http://bugs.winehq.org/show_bug.cgi?id=31993)

Thanks the pulseaudio thing failed lol but restarting the computer worked..but seems to be real buggy hopefully someone out there would make it user friendly. (to the point where you don't need a degree in programming to fix stuff)

---

### Post by Beardedturtle on 2012-11-21
> **sdowney717 said:**
> found another way to configure the app, use alt+v and add the toolbars to get tabbed browsing, so far that works fine.
anyone doing the first tip?
F11 no longer works.

---

### Post by moocow1452 on 2012-11-21
Fresh Quantic install on a Dell Latitude D610, finally got Silverlight to work, audio works, video doesn't. Probably my GFX card is being a stinker, but World of Goo seems to work okay via Steam... :-k

---

### Post by Bandit on 2012-11-21
I am curious what the performance difference is from using it on Windows -vs- Wine?

---

### Post by sdowney717 on 2012-11-21
> **Beardedturtle said:**
> F11 no longer works.

yes, things seem to be changing.
I can no longer F11 then hit corner 'x' to close the firefox app.

I found you can alt + v then select various toolbars to make it function with tabs and addresses.
With alt + v, you can also load the menu items to close program hit file then exit.

Now for some odd reason unknown to me, I have firefox v16 installed in wine. I can run a full version of firefox with all menus and tabs etc... from the wine folder and everything works including netflix.
I dont know exactly how this happened to me. I did have firefox installed in wine before loading the PPA and doing the Netflix install.

---

### Post by sdowney717 on 2012-11-21
> **Bandit said:**
> I am curious what the performance difference is from using it on Windows -vs- Wine?

My thoughts:
I have a very powerful quad core with a modern Nvidia 1GB vid card running win7 and it is flawlessly good on Netflix. It is running silverlight version 5 which added in hardware video acceleration which silverlight ver 4 lacks. 

When that win7 machine ran silverlight ver 4 I noticed a few video problems which made me eager to get ver5 working. 

The slower core 2 duo linux machine with an older 8400gs nvidia card is actually better than what the powerful win7 machine was able to put out with silverlight ver4 and we are only using silverlight ver4 on linux wine.

If they can get this to work with hardware acceleration as in silverlight ver5 it will be flawless. I have a feeling that if I put that 1gb nvidia card in my ubuntu machine it would be flawlessly perfect.

---

### Post by sffvba[e0rt on 2012-11-21
*Have Ubuntu?*  **Check!**
*Have netflix that can work on Ubuntu?*  **Check!**
*Live in a country you can use netflix?*  **Eh?!**

:cry:


404

---

### Post by BungaDunga on 2012-11-21
> **Bandit said:**
> I am curious what the performance difference is from using it on Windows -vs- Wine?

I'm running it on an old laptop (Dell d620... Intel GMA 950, yo) and it seems to work okay. I mean, it's a bit unstable, but when it's not crashing (which happens if I interact with a video too much) it seems to keep a good framerate. There's occasionally a quick audio stutter, but it's pretty tiny.

---

### Post by sdowney717 on 2012-11-21
They are working on getting silverlight ver 5 to work

[http://bugs.winehq.org/show_bug.cgi?id=31754](http://bugs.winehq.org/show_bug.cgi?id=31754)

---

### Post by dniMretsaM on 2012-11-21
> **Beardedturtle said:**
> F11 no longer works.

F11 works fine for me. There is no close button when it's not in full screen, though. There never was for me.

---

### Post by sdowney717 on 2012-11-21
> **dniMretsaM said:**
> F11 works fine for me. There is no close button when it's not in full screen, though. There never was for me.

so much variety of experience with this, I used to have all 3, min max x close

now all I have is x close and it does not close whe clicked which it used to do.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=227375&d=1353291990[/IMG]

---

### Post by dniMretsaM on 2012-11-21
> **sdowney717 said:**
> so much variety of experience with this, I used to have all 3, min max x close

now all I have is x close and it does not close whe clicked which it used to do.

I wonder if that has to do with the fact that you changed the Firefox version.

---

### Post by Bandit on 2012-11-22
> **not found said:**
> *Have Ubuntu?*  **Check!**
*Have netflix that can work on Ubuntu?*  **Check!**
*Live in a country you can use netflix?*  **Eh?!**

:cry:


404

LOL dont feel bad. I am moving to the Philippines in less then two months and no more Hulu or Netflix..

---

### Post by sdowney717 on 2012-11-22
Did a test
Created a new user
set desktop to Cinnamon
login
run winecfg
download and install firefox 17
install and run windows firefox17, no netflix working

Then run netflix desktop
config program runs
loads the app netflix works version 14
min-max-close all working fine

Then hit F11, then F10
click help about and update firefox to ver 17
Firefox restarts all working with netflix

Now close netflix app

Click on earlier Windows firefox 17 full install
runs and works on netfilx with a full browser implementation

Nice to see it working.

---

### Post by lovinglinux on 2012-11-22
> **spook1980 said:**
> Netflix on ubuntu runs like a dream, time to delete the windows partition

Exactly what I did 2 days ago. :)

---

### Post by lovinglinux on 2012-11-22
> **Bandit said:**
> I am curious what the performance difference is from using it on Windows -vs- Wine?

Performance is great for me. Better than using a VM. However I haven't tested on a dual boot and I deleted the Windows partition 2 days ago.

---

### Post by sdowney717 on 2012-11-22
I discovered that if you delete the .netflix-desktop directory, then when you rerun the Netflix Desktop icon, it registers any existing wine Firefox installs so they will then work with netflix. 

I actually prefer having netflix running in a tabbed browser window.

---

### Post by spook1980 on 2012-11-22
> **lovinglinux said:**
> Exactly what I did 2 days ago. :)

i was only using windows for netflix,

---

### Post by snowpine on 2012-11-22
Does anyone know if this will work in Debian?

---

### Post by mamamia88 on 2012-11-22
> **snowpine said:**
> Does anyone know if this will work in Debian?

should work on any distro since wine works on any distro.   compiling on arch right now from the AUR

---

### Post by sdowney717 on 2012-11-22
> **mamamia88 said:**
> should work on any distro since wine works on any distro.   compiling on arch right now from the AUR

Aren't they already compiled as says here?
[https://bbs.archlinux.org/viewtopic.php?id=153234](https://bbs.archlinux.org/viewtopic.php?id=153234)

---

### Post by mamamia88 on 2012-11-22
> **sdowney717 said:**
> Aren't they already compiled as says here?
[https://bbs.archlinux.org/viewtopic.php?id=153234](https://bbs.archlinux.org/viewtopic.php?id=153234)
the maintainer has a repository but if the package is in the AUR it isn't precompiled.   the pkgbuild is just instructions for downloading and compiling from source.   i'm just installing with yaourt but i have to leave soon so hopefully it finishes before i leave.  edit well it works but it's laggy and almost unusable.  gives me hope for the future though

---

### Post by tjwilli on 2012-11-23
This works great! Just saw the pilot for Star Trek. I grew up on Star Trek, but never saw that episode.  I didn't realize that Capt. Kirk didn't come until later.
:popcorn:

---

### Post by sdowney717 on 2012-11-24
I did an update this am and a new wine-compholio was downloaded.
Update also put in wine 1.5, so I now have 2 versions of wine where I only had one before?

SO go to watch netflix and the video was running very fast with squeaky sound and jittery.

SO, do a complete reboot and it is back to working.

here is pic of installed wines. Can I just remove wine 1.5?

---

### Post by evilsoup on 2012-11-24
It uses a customised version of wine 1.5 (that's what the wine-compholio package brings in) to run SIlverlight, so no, you need to keep it.

---

### Post by meldroc on 2012-11-24
Has anyone figured out any tricks to improving the frame rate?

Currently running Kubuntu 12.10 (64-bit), with the nVidia proprietary drivers on a system w/ an AMD Phenom II x4 965 (3.4GHZ), an nVidia GTX 550Ti video card, 8GB of RAM.

Netflix video is a little choppy, which is annoying, especially if I'm watching an action flick, so I'm wondering if anyone figured out ways to improve performance.

---

### Post by meldroc on 2012-11-24
> **sdowney717 said:**
> I did an update this am and a new wine-compholio was downloaded.
Update also put in wine 1.5, so I now have 2 versions of wine where I only had one before?

SO go to watch netflix and the video was running very fast with squeaky sound and jittery.

SO, do a complete reboot and it is back to working.

here is pic of installed wines. Can I just remove wine 1.5?

The squeaky fast sound may have been a pulseaudio glitch. "pulseaudio -k" restarts the sound server and has been known to fix this.

---

### Post by BarfBag on 2012-11-24
> **meldroc said:**
> has anyone figured out any tricks to improving the frame rate?

Currently running kubuntu 12.10 (64-bit), with the nvidia proprietary drivers on a system w/ an amd phenom ii x4 965 (3.4ghz), an nvidia gtx 550ti video card, 8gb of ram.

Netflix video is a little choppy, which is annoying, especially if i'm watching an action flick, so i'm wondering if anyone figured out ways to improve performance.

+1

---

### Post by sdowney717 on 2012-11-24
On netflix, do a search for example and then play some of the test videos to see if they have any judder.

I have read some of the judder is Netflix encoding issues and some is your PC - playback device.

Some videos Netflix did a better job and some not so good.

---

### Post by weasel fierce on 2012-11-24
yeah, I noticed it can differ by video. Some are quite solid, and some less so.

---

### Post by sdowney717 on 2012-11-25
> **weasel fierce said:**
> yeah, I noticed it can differ by video. Some are quite solid, and some less so.

[http://www.projectorcentral.com/judder_24p.htm?page=What-Causes-Judder](http://www.projectorcentral.com/judder_24p.htm?page=What-Causes-Judder)
Judder can be eliminated with frame interpolation. 

What Netflix perhaps does is some streams they have worked on adding in frames using some kind of video process and others they have done nothing. I have watched Amazon prime videos and not noticed judder and I have watched Netflix videos and not noticed judder. I have also seen lots of judder on Netflix, you can tell it is not perfectly fluid like. When we went from silverlight ver4 to silverlight ver5, this judder seemed to be much less.
Perhaps silverlight 5 with hardware accelerated video does some kind of video interpolation.

---

### Post by weasel fierce on 2012-11-25
On that topic. I got a popup about updating silverlight in firefox. Is that safe to do, or no ?

---

### Post by spook1980 on 2012-11-25
> **weasel fierce said:**
> On that topic. I got a popup about updating silverlight in firefox. Is that safe to do, or no ?

you can try if it breaks it, you can always delete the .netflix-desktop folder in your home folder. then relaunch netflix desktop.

---

### Post by spook1980 on 2012-11-25
and don't mean to get off topic here, but... shouldn't this topic be in the wine catagory?

---

### Post by mikodo on 2012-11-27
> **Bandit said:**
> LOL dont feel bad. I am moving to the Philippines in less then two months and no more Hulu or Netflix..Would a service like below help you guys?

                                  [http://support.unblock-us.com/customer/portal/articles/291505](http://support.unblock-us.com/customer/portal/articles/291505)

There are others, just google for them and read (some solutions appear free), to see if they would help.

Hope you find something applicable.

---

### Post by dniMretsaM on 2012-11-28
Netflix Desktop 0.2.0 was released today. It now uses Firefox 17.0.

---

### Post by King Dude on 2012-11-28
I'd be happy as all hell if there was a Netflix add-on for XBMC.

---

### Post by LuciferRex on 2012-11-28
> **dniMretsaM said:**
> Netflix Desktop 0.2.0 was released today. It now uses Firefox 17.0.

I downloaded it, and I can now actually WATCH Netflix on my laptop!

---

### Post by dniMretsaM on 2012-11-28
> **King Dude said:**
> I'd be happy as all hell if there was a Netflix add-on for XBMC.

I'm sure this could be compiled on XBMC, since it's just a patched WINE, FF, and SilverLight. Maybe suggest it to the devs or something.

---

### Post by tjeremiah on 2012-11-28
does the ppa created for this operation function well? I want to try this but dont want the whole process to be a headache.

---

### Post by randumari on 2012-11-28
I had netflix-desktop installed yesterday, but then I upgraded to 0.2 an hour ago.  Now I get sound only when loading a movie.

apt-show-versions netflix-desktop
netflix-desktop/quantal uptodate 0.2.0~quantal

apt-show-versions wine-compholio
wine-compholio 1.5.18~quantal installed: No available version in archive

I tried* rm -rf ~/.netflix-desktop*, as well as apt-get purging wine-compholio and netflix-desktop, as well as re-adding the ppa.  How do I downgrade?

sudo apt-get install netflix-desktop=0.1.0~quantal9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '0.1.0~quantal9' for 'netflix-desktop' was not found

---

### Post by dniMretsaM on 2012-11-28
> **tjeremiah said:**
> does the ppa created for this operation function well? I want to try this but dont want the whole process to be a headache.

Works great for me.

---

### Post by weasel fierce on 2012-11-28
> **dniMretsaM said:**
> Works great for me.

yeah, I haven't had issues either.

---

### Post by zer010 on 2012-11-29
Oh hell, looks like I have some catching up to do... I got the latest update from the ppa and I get the site, I get to browse, but actual playing gives me a black screen and after a while some sound (yay!?).. I've not gone through this thread in it's entirety, thus the footwork ahead.  However, I'm glad to see that it's working at all. Awesome! When I get more time, I'll definitely look into this.

---

### Post by arpanaut on 2012-11-29
WOW! 
My socks are officially knocked off.
This is impressive, now I will start getting my moneys worth from my Netflix subscription.
 I really hated having to boot Win to use Netflix, this is awesome!

YeeeeeHaw!

---

### Post by dniMretsaM on 2012-11-29
> **zer010 said:**
> Oh hell, looks like I have some catching up to do... I got the latest update from the ppa and I get the site, I get to browse, but actual playing gives me a black screen and after a while some sound (yay!?).. I've not gone through this thread in it's entirety, thus the footwork ahead.  However, I'm glad to see that it's working at all. Awesome! When I get more time, I'll definitely look into this.

Randumari has this issue as well. I don't, though, so I have no way of trying to figure out what's wrong.

---

### Post by oldrocker99 on 2012-11-29
Netflix-desktop returned a wine error with plugin-container.exe on my 32-bit 12.10 laptop, but it works fine on my 12.04 desktop. I did have to enter

pulseaudio -k

to get ungarbled sound, but now I can stream Netflix under Linux!

This. Is. BIG!

---

### Post by LuciferRex on 2012-11-29
> **oldrocker99 said:**
> This. Is. BIG!

This was the only thing I missed about running Windows on my lappy.

---

### Post by monkeybrain2012 on 2012-11-29
This is interesting. I don't care about Netflix but wouldn't mind doing some testing. I am planning to set up a trail account, is there any catch I should be aware of?

---

### Post by sdowney717 on 2012-11-30
Trying netflix another way by using chrome remote desktop and it works.

Installed remote desktop on both a win7 and ubuntu PC
On the win7 you do the enable remote desktop using a pin number, not the generate access code which for me does not work

Then run the app on the ubuntu PC
click your machine name farther down the list
enter the win7 pin number
and your in.

at the top of the window in the browser, click you can play with full screen mode and other options.

---

### Post by randumari on 2012-11-30
I figured out a couple problems I was having, which I'm sure were contributing to my netflix-desktop/wine issues:

One problem I figured out using "netflix-desktop --showdebug."  Because I have a 64-bit system, I had to use getlibs to get a 32 bit gnome-keyring shared object according to: [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/885492](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/885492)

Secondly, when I ran /opt/wine-compholio/bin/winecfg, it created a .wine directory in my home directory.  I deleted it and set my WINEPREFIX variable to $HOME/.netflix-desktop to get winecfg to create the directory structure there instead.  I've also uninstalled any wine packages that I could find on my system for simplicity.

I'm still only seeing a black screen but hearing audio when playing a movie.
I'm attaching my --showdebug output.  If someone could help, I'd greatly appreciate it.

---

### Post by sdowney717 on 2012-12-01
Try moving the window around, min, max resize. I have also noticed the black screen but not often. Moving the window brought it back.

---

### Post by BarfBag on 2012-12-01
> **monkeybrain2012 said:**
> This is interesting. I don't care about Netflix but wouldn't mind doing some testing. I am planning to set up a trail account, is there any catch I should be aware of?

They'll probably make you enter in your card number, but I've found them to be a pretty honest company.  You won't be charged as long as you cancel by the end of the trial.

---

### Post by tzoom84 on 2012-12-01
Any way I can install netflix-desktop on Ubuntu 11.10? I unfortunately won't be able to get up to 12.04 any time soon so I was wondering if there was potentially a manual install procedure?

---

### Post by dniMretsaM on 2012-12-01
> **tzoom84 said:**
> Any way I can install netflix-desktop on Ubuntu 11.10? I unfortunately won't be able to get up to 12.04 any time soon so I was wondering if there was potentially a manual install procedure?

The PPA works on 10.04-13.04, so you should be fine.

---

### Post by tzoom84 on 2012-12-01
Hmm. When I run the commands in the first post, I end up with:

```
xbmc@xbmc-server:/etc$ sudo apt-get install netflix-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package netflix-desktop

```

I found this page that, at the end of the comments section, made it seem it wasn't 11.10 compatible:
[https://plus.google.com/+LinuxNewsHere/posts/Y5DxnMktwbT](https://plus.google.com/+LinuxNewsHere/posts/Y5DxnMktwbT)

---

### Post by randumari on 2012-12-01
[COLOR=Black][sdowney717]("http://ubuntuforums.org/member.php?u=209280")[/COLOR], you figured it out!  I had to Alt+Left-Arrow to get to the netflix video selection screen in order to F11 to access the maximize button.  Actually, there are two sets of {close/minimize/maximize} buttons (the Netflix window and the window manager's top bar).  Once I clicked maximize on the window manager's top bar, the video appeared in the Netflix window!

I'm so happy that I can watch Netflix now :-)

---

### Post by tzoom84 on 2012-12-01
More on the compatibility 2-3 posts ago:

When I check out the PPA directory at [https://launchpad.net/~ehoover/+archive/compholio/](https://launchpad.net/~ehoover/+archive/compholio/), I see only:
0.2.0 raring, 0.2.0 quantal, 0.2.0 precise.

Unfortunately no 11.10 (ocelot). Anyone know of any tips to manually compile?
I followed the directions here: [http://ashu-geek.blogspot.com/2012/11/netflix-desktop-released-for-ubuntu.html](http://ashu-geek.blogspot.com/2012/11/netflix-desktop-released-for-ubuntu.html)

However, when I attempt to load a movie I get a Silverlight error: **"Silverlight Installation Problem, Error Code: 2104"**

---

### Post by pompel9 on 2012-12-01
I have tried to install netflix desktop more than once. The problem I have is that silverlight does not install with the netflix desktop. So until they fix this problem I have to use my PS3.
When I try to play a movie in netflix desktop I only get up that I have to install silverlight.

If anyone knows a fix for this I will be mighty grateful.

The laptop I try to use this one has ubuntu 12.04 64bit installed.

---

### Post by sdowney717 on 2012-12-01
> **randumari said:**
> [COLOR=Black][sdowney717]("http://ubuntuforums.org/member.php?u=209280")[/COLOR], you figured it out!  I had to Alt+Left-Arrow to get to the netflix video selection screen in order to F11 to access the maximize button.  Actually, there are two sets of {close/minimize/maximize} buttons (the Netflix window and the window manager's top bar).  Once I clicked maximize on the window manager's top bar, the video appeared in the Netflix window!

I'm so happy that I can watch Netflix now :-)

That's great!
I hope they can make silver-light ver 5 work, then we can get hardware accelerated video. I read a comment on the wine forum saying they need to do more work on wine3d.

---

### Post by Beardedturtle on 2012-12-01
Seems like if I made a change to Wine CFG I have to restart my machine other wise I would have accelerated sound issues.

---

### Post by sdowney717 on 2012-12-01
> **Beardedturtle said:**
> Seems like if I made a change to Wine CFG I have to restart my machine other wise I would have accelerated sound issues.

try running 

pulseaudio -k

it will kill and then restart pulseaudio

---

### Post by Beardedturtle on 2012-12-01
> **sdowney717 said:**
> try running 

pulseaudio -k

it will kill and then restart pulseaudio
I would get a terminal error message with that. IDK why but that is the way mine works.
:guitar:

---

### Post by tzoom84 on 2012-12-02
So I was able to get somewhere with a manual compile, running on Ubuntu 11.10, using directions from:
[http://ashu-geek.blogspot.com/2012/11/netflix-desktop-released-for-ubuntu.html](http://ashu-geek.blogspot.com/2012/11/netflix-desktop-released-for-ubuntu.html)

Seems as all compiles properly. But when I go to start a movie from Netflix, the screen just stays forever black. Processor and CPU usage is minimal. No blatent errors in the wine log (that I noticed). And no silverlight errors. 

Anyone experience anything similar?

---

### Post by cptrohn on 2012-12-02
Is there anyway to keep the Netflix desktop from opening in full screen by default?

---

### Post by lovinglinux on 2012-12-02
> **cptrohn said:**
> Is there anyway to keep the Netflix desktop from opening in full screen by default?

Hit F11 and close it. It will start windowed next time.

---

### Post by cptrohn on 2012-12-02
> **lovinglinux said:**
> Hit F11 and close it. It will start windowed next time.

Gracious!

---

### Post by sdowney717 on 2012-12-05
It was doing the install and hit a snag on msft core font installer.
I was shown a page with an <OK> which nothing would let me get past, no keys or clicks worked, so I closed the terminal

Now on rerun it is stuck, damaged, locked.

So how to fix this?

> scott@scott-P5QC:~$ sudo apt-get install netflix-desktop
[sudo] password for scott: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by sdowney717 on 2012-12-05
> 1. rm /var/lib/dpkg/lock
2. sudo dpkg --configure -a

Ok this started it going again, however msft core fonts???

---

### Post by sdowney717 on 2012-12-05
I had to reboot and reinstall and now getting stuck again

any ideas????

OK, HIT TAB then ENTER

and you can get past it.

---

### Post by sdowney717 on 2012-12-05
still broken for me with 64 bit, I get plugin container errors

You can fix by installing the binary Nvidia driver, so Netflix does not work with nouveau free driver.
backtrace.txt

```
Unhandled exception: page fault on write access to 0x7dd89000 in 32-bit code (0xf75d4696).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:f75d4696 ESP:0033c584 EBP:0033c644 EFLAGS:00010206(  R- --  I   - -P- )
 EAX:7e189a20 EBX:f7643ff4 ECX:03365a60 EDX:7dd88fe0
 ESI:7dd112d0 EDI:033c6290
Stack dump:
0x0033c584:  f6e00ff4 f6dd9551 7dd288c0 7e129280
0x0033c594:  033c6280 f6ffbff4 f6ffbff4 002071b8
0x0033c5a4:  002071cc f6f2fd2e 00000001 0033c624
0x0033c5b4:  0033c628 7e129280 7dc9b710 03200053
0x0033c5c4:  7dd112d0 7bc352df f6ecdfe0 00000000
0x0033c5d4:  00000000 00110000 00000011 f6ec8ff4
Backtrace:
=>0 0xf75d4696 (0x0033c644)
  1 0xf6f31cf0 (0x0033cae4)
  2 0xf6f35e91 (0x0033cb04)
  3 0xf6fbf58a (0x0033cb44)
  4 0xf71ad182 (0x0033cb64)
  5 0xf71a1b3c (0x0033cb94)
  6 0x01c70158 in npctrl (+0xa0157) (0x0033cbec)
  7 0x01c6ffb1 in npctrl (+0x9ffb0) (0x0033cc00)
  8 0x01c11a51 in npctrl (+0x41a50) (0x0033cc20)
  9 0x01c52272 in npctrl (+0x82271) (0x0033cc3c)
  10 0x01c50d54 in npctrl (+0x80d53) (0x0033cc4c)
  11 0x10a36e8c in xul (+0xa36e8b) (0x0033cd68)
  12 0x109d421a in xul (+0x9d4219) (0x0033cdb8)
  13 0x10a05a07 in xul (+0xa05a06) (0x0033cdd8)
  14 0x10a05b4f in xul (+0xa05b4e) (0x0033ce0c)
  15 0x10a200c4 in xul (+0xa200c3) (0x0033ce94)
  16 0x10a24a02 in xul (+0xa24a01) (0x0033cee8)
  17 0x10a2ae01 in xul (+0xa2ae00) (0x0033cf44)
  18 0x01c9befd in npctrl (+0xcbefc) (0x0033cf68)
  19 0x01c5ac9f in npctrl (+0x8ac9e) (0x0033cfd0)
  20 0x01c3cbfb in npctrl (+0x6cbfa) (0x0033cff0)
  21 0x01c1459d in npctrl (+0x4459c) (0x0033e0fc)
  22 0x01be38e6 in npctrl (+0x138e5) (0x0033f368)
  23 0x01be3bcc in npctrl (+0x13bcb) (0x0033f3d0)
  24 0x01be3d77 in npctrl (+0x13d76) (0x0033f418)
  25 0x01be3e0e in npctrl (+0x13e0d) (0x0033f454)
  26 0x01be3e62 in npctrl (+0x13e61) (0x0033f470)
  27 0x01be3f75 in npctrl (+0x13f74) (0x0033f484)
  28 0x01bd4702 in npctrl (+0x4701) (0x0033f4a0)
  29 0x7eb8758a (0x0033f4d0)
  30 0x7eb87cdc (0x0033f520)
  31 0x7eb8a2ed (0x0033f570)
  32 0x7eb4c43e (0x0033f660)
  33 0x10681639 in xul (+0x681638) (0x0033f69c)
  34 0x106847ca in xul (+0x6847c9) (0x0033f6cc)
  35 0x102ce32c in xul (+0x2ce32b) (0x0033f714)
  36 0x102bd101 in xul (+0x2bd100) (0x0033f730)
  37 0x10a410cf in xul (+0xa410ce) (0x0033fdf0)
  38 0x0040126a in plugin-container (+0x1269) (0x0033fe2c)
  39 0x004014a0 in plugin-container (+0x149f) (0x0033fe70)
  40 0x7b85c22c in kernel32 (+0x4c22b) (0x0033fe88)
  41 0x7b85d49f in kernel32 (+0x4d49e) (0x0033fec8)
  42 0x7bc73740 (0x0033fed8)
  43 0x7bc7621d (0x0033ffa8)
  44 0x7bc7371e (0x0033ffc8)
  45 0x7bc4a53e (0x0033ffe8)
0xf75d4696: movntq	%mm2,0x20(%edx)
Modules:
Module	Address			Debug info	Name (52 modules)
PE	  340000-  36d000	Deferred        nspr4
PE	  370000-  390000	Deferred        mozglue
PE	  390000-  3a8000	Deferred        smime3
PE	  3b0000-  3c8000	Deferred        nssutil3
PE	  3d0000-  3d7000	Deferred        plc4
PE	  3e0000-  3e7000	Deferred        plds4
PE	  3f0000-  3f6000	Deferred        mozalloc
PE	  400000-  406000	Export          plugin-container
PE	  410000-  65f000	Deferred        mozjs
PE	  660000-  6fe000	Deferred        nss3
PE	  700000-  725000	Deferred        ssl3
PE	  730000-  7f8000	Deferred        mozsqlite3
PE	  800000-  c2e000	Deferred        gkmedias
PE	 1bd0000- 1ccd000	Export          npctrl
PE	 1cd0000- 2290000	Deferred        agcore
PE	10000000-10eac000	Export          xul
PE	78050000-780b9000	Deferred        msvcp100
PE	78aa0000-78b5e000	Deferred        msvcr100
PE	7b810000-7b996000	Export          kernel32
PE	7bc10000-7bc14000	Deferred        ntdll
PE	7e100000-7e104000	Deferred        winex11
PE	7e250000-7e258000	Deferred        winspool
PE	7e290000-7e29e000	Deferred        setupapi
PE	7e2f0000-7e2f4000	Deferred        uxtheme
PE	7e320000-7e324000	Deferred        imm32
PE	7e340000-7e36e000	Deferred        comctl32
PE	7e440000-7e448000	Deferred        shlwapi
PE	7e4b0000-7e609000	Deferred        shell32
PE	7e6d0000-7e6d8000	Deferred        oleaut32
PE	7e7c0000-7e7c3000	Deferred        msimg32
PE	7e7e0000-7e7e3000	Deferred        usp10
PE	7e820000-7e829000	Deferred        msacm32
PE	7e850000-7e854000	Deferred        rpcrt4
PE	7e8d0000-7e8d8000	Deferred        ole32
PE	7e9c0000-7e9c4000	Deferred        version
PE	7e9e0000-7e9e7000	Deferred        gdi32
PE	7eaf0000-7eb2a000	Deferred        user32
PE	7ec20000-7ec92000	Deferred        winmm
PE	7ecd0000-7ecd4000	Deferred        iphlpapi
PE	7ecf0000-7ecf4000	Deferred        ws2_32
PE	7ed20000-7ed24000	Deferred        wsock32
PE	7ed40000-7ed44000	Deferred        advapi32
PE	7eff0000-7eff4000	Deferred        psapi
PE	f6e20000-f6e24000	Deferred        opengl32
PE	f6ee0000-f6ee4000	Deferred        wined3d
PE	f7190000-f7194000	Deferred        d3d9
PE	f7200000-f7203000	Deferred        netapi32
PE	f7230000-f726b000	Deferred        crypt32
PE	f72f0000-f7300000	Deferred        urlmon
PE	f7370000-f737a000	Deferred        mpr
PE	f73a0000-f73b7000	Deferred        wininet
PE	f7440000-f7444000	Deferred        dbghelp
Threads:
process  tid      prio (all id:s are in hex)
00000008 firefox.exe
	0000000d    0
	00000046    0
	00000045    0
	00000044    0
	00000043    0
	00000042    0
	00000041    0
	00000040    0
	0000003f    0
	0000003e    0
	0000003c    0
	0000003b    0
	0000003a    0
	00000039    0
	00000038    0
	00000037    0
	00000036    0
	00000035    0
	00000034    0
	00000033    0
	00000032    0
	00000031    0
	0000002f    0
	0000002e    0
	0000002d    0
	0000002c    0
	0000002b    0
	00000029   -1
	00000028    0
	00000027    0
	00000026    0
	00000025    0
	00000024    0
	00000023    0
	00000009    0
0000000e services.exe
	00000021    0
	00000020    0
	00000018    0
	00000017    0
	00000015    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001a    0
	00000019    0
	00000014    0
	00000013    0
0000001b plugplay.exe
	00000022    0
	0000001f    0
	0000001c    0
0000001d explorer.exe
	0000001e    0
00000047 (D) C:\Program Files\Mozilla Firefox\plugin-container.exe
	00000048    0
	00000030    0
	0000003d    0
	0000002a    0
	0000000b    0 <==
00000049 agcp.exe
	0000004a    0
System information:
    Wine build: wine-1.5.18
    Platform: i386
    Host system: Linux
    Host version: 3.2.0-34-generic
```

I will try installing wine1.4 which then says will use 411mb!
```
scott@scott-P5QC:~$ sudo apt-get install wine1.4
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  binfmt-support fonts-droid fonts-horai-umefont fonts-unfonts-core
  gnome-exe-thumbnailer icoutils imagemagick imagemagick-common libcapi20-3
  libcdt4 libencode-locale-perl libfile-listing-perl libfont-afm-perl
  libgettextpo0 libgif4 libgraph4 libgvc5 libhtml-form-perl
  libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl
  libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libio-socket-inet6-perl
  libio-socket-ssl-perl liblqr-1-0 liblwp-mediatypes-perl
  liblwp-protocol-https-perl libmagickcore4 libmagickcore4-extra
  libmagickwand4 libmailtools-perl libnet-http-perl libnet-ssleay-perl
  libnetpbm10 libpam-winbind libpathplan4 libsocket6-perl libtimedate-perl
  liburi-perl libwww-perl libwww-robotrules-perl netpbm ttf-droid ttf-umefont
  ttf-unfonts-core unrar winbind wine-gecko1.4 wine-gecko1.4:i386
  wine1.4-amd64 wine1.4-common wine1.4-i386:i386 winetricks
Suggested packages:
  libterm-readline-gnu-perl libterm-readline-perl-perl imagemagick-doc
  autotrace enscript gnuplot grads hp2xx html2ps libwmf-bin povray radiance
  texlive-base-bin transfig ufraw-batch libdata-dump-perl libcrypt-ssleay-perl
  libauthen-ntlm-perl dosbox
The following NEW packages will be installed:
  binfmt-support fonts-droid fonts-horai-umefont fonts-unfonts-core
  gnome-exe-thumbnailer icoutils imagemagick imagemagick-common libcapi20-3
  libcdt4 libencode-locale-perl libfile-listing-perl libfont-afm-perl
  libgettextpo0 libgif4 libgraph4 libgvc5 libhtml-form-perl
  libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl
  libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libio-socket-inet6-perl
  libio-socket-ssl-perl liblqr-1-0 liblwp-mediatypes-perl
  liblwp-protocol-https-perl libmagickcore4 libmagickcore4-extra
  libmagickwand4 libmailtools-perl libnet-http-perl libnet-ssleay-perl
  libnetpbm10 libpam-winbind libpathplan4 libsocket6-perl libtimedate-perl
  liburi-perl libwww-perl libwww-robotrules-perl netpbm ttf-droid ttf-umefont
  ttf-unfonts-core unrar winbind wine-gecko1.4 wine-gecko1.4:i386 wine1.4
  wine1.4-amd64 wine1.4-common wine1.4-i386:i386 winetricks
0 upgraded, 59 newly installed, 0 to remove and 0 not upgraded.
Need to get 152 MB of archives.
After this operation, 411 MB of additional disk space will be used.
Do you want to continue [Y/n]? y

```

---

### Post by sdowney717 on 2012-12-05
I solved it!
I needed to install the binary Nvidia driver, now it is working

I think will uninstall wine1.4

---

### Post by Returning Penguin on 2012-12-06
Hi everyone, I am new to ubuntu but was with suse until my laptop died and when my new laptop had windows 7 I rode it out but it crashed(which I expected) and am now running ubuntu 10.04. I am trying to install the netflix app and keep getting this: netflix-desktop cannot be found any help??

---

### Post by sdowney717 on 2012-12-06
> **Returning Penguin said:**
> Hi everyone, I am new to ubuntu but was with suse until my laptop died and when my new laptop had windows 7 I rode it out but it crashed(which I expected) and am now running ubuntu 10.04. I am trying to install the netflix app and keep getting this: netflix-desktop cannot be found any help??

Not well supported on that version?
What is your reason for not running a newer version of Ubuntu?
If you dislike the desktop, run cinnamon or gnome3

Gnome3 you can install extensions which mimic gnome2

---

### Post by tjeremiah on 2012-12-06
I installed from PPA. Everything appeared to have install. Click on Netflix-desktop and nothing loads. Try to run it in terminal and receive no message.

---

### Post by silverhaze06 on 2012-12-06
I already had wine installed before this so for some reason it made it not work. After I uninstalled wine, I reinstalled this thing according to the instructions. Now it's working. The only problem I'm having with it is entering/exiting out of fullscreen mode for the program. A lot of times it will cause me to not be able to close the program by clicking the x on the window and i cant click on anything in the unity panel. I have to hit f10 to bring the menu up and close it from there. and that doesnt show up while in fullscreen mode.

---

### Post by sdowney717 on 2012-12-07
> **silverhaze06 said:**
> I already had wine installed before this so for some reason it made it not work. After I uninstalled wine, I reinstalled this thing according to the instructions. Now it's working. The only problem I'm having with it is entering/exiting out of fullscreen mode for the program. A lot of times it will cause me to not be able to close the program by clicking the x on the window and i cant click on anything in the unity panel. I have to hit f10 to bring the menu up and close it from there. and that doesnt show up while in fullscreen mode.

Try this
while in the app before starting a movie
hit F11 if full screen
hit alt + v key

tell it to load the menu and navigation bars

close it then reopen and see it it has them showing and not full screened

---

### Post by silverhaze06 on 2012-12-07
I now notice 2 problems. Video playback is a little choppy in standard def, but still watchable. In HD mode, it only plays 1 frame every 1/3 of a second and is completely unwatchable... I'm thinking I need to change some setting in the wine configuration, but that part of wine is not in my application menu anymore. Anyone else have this problem?

---

### Post by silverhaze06 on 2012-12-07
> **sdowney717 said:**
> Try this
while in the app before starting a movie
hit F11 if full screen
hit alt + v key

tell it to load the menu and navigation bars

close it then reopen and see it it has them showing and not full screened


Like everything else, it only seems to work half the time if im lucky. Do you know anything about fixing the extremely choppy HD streams?

---

### Post by sdowney717 on 2012-12-07
> **silverhaze06 said:**
> Like everything else, it only seems to work half the time if im lucky. Do you know anything about fixing the extremely choppy HD streams?

That is likely due to Silverlight ver 4 being used. Silverlight ver 5 uses hardware accelerated video. On a win7 machine 4 core cpu with nvidia geforce 260 I noticed the difference between ver 4 and ver 5.

I think if you look up netflix judder you may find more info.

Also do a search for 'example' under netflix. They have encoded various videos which have no judder when watched from my ubuntu machine. So it could be that some Netflix video will look better and other worse depending on how much effort Netflix puts into them.
these examples play fairly smooth on my ubuntu pc.

I can watch Amazon prime video smooth as silk.
How does Amazon play for you? They have some free video.

---

### Post by silverhaze06 on 2012-12-07
> **sdowney717 said:**
> That is likely due to Silverlight ver 4 being used. Silverlight ver 5 uses hardware accelerated video. On a win7 machine 4 core cpu with nvidia geforce 260 I noticed the difference between ver 4 and ver 5.

I think if you look up netflix judder you may find more info.

Also do a search for 'example' under netflix. They have encoded various videos which have no judder when watched from my ubuntu machine. So it could be that some Netflix video will look better and other worse depending on how much effort Netflix puts into them.
these examples play fairly smooth on my ubuntu pc.

I can watch Amazon prime video smooth as silk.
How does Amazon play for you? They have some free video.

Yeah the sample movies on netflix were not quite as jittery, but still jittery. So for now ill have to set the quality down I guess. The sample movies I played on amazon prime were smooth as silk tho, like you said.

---

### Post by silverhaze06 on 2012-12-08
Or could it have something to do with the fact that the version of wine its running under is a 32bit version and im on a 64bit system?

---

### Post by weasel fierce on 2012-12-08
I got it to work on Kubuntu 64 bit, when I tested it on our new laptop, so that ought not to be the case

---

### Post by tcuc on 2012-12-08
my installation won't start... i ran "netflix-desktop --showdebug" and got the error "wine: cannot find 'C:\Program Files\Mozilla Firefox\firefox.exe'" 
so i checked my /.netflix-desktop/drive_c/Program Files folder and found no Firefox Folder... help? :P Does any one have the folder, could someone pack it in to a zip or something?

---

### Post by dniMretsaM on 2012-12-08
> **tcuc said:**
> my installation won't start... i ran "netflix-desktop --showdebug" and got the error "wine: cannot find 'C:\Program Files\Mozilla Firefox\firefox.exe'" 
so i checked my /.netflix-desktop/drive_c/Program Files folder and found no Firefox Folder... help? :P Does any one have the folder, could someone pack it in to a zip or something?

Remove the [FONT=Courier New]~/.netflix-desktop[/FONT] directory and reinstall the application.

---

### Post by tcuc on 2012-12-08
> **dniMretsaM said:**
> Remove the [FONT=Courier New]~/.netflix-desktop[/FONT] directory and reinstall the application.

Thanks, I deleted the "~.netflix-desktop/" and then installed netflix-desktop:i386 (sudo apt-get install netflix-desktop:i386) it worked grate on my Ubuntu 12.04 x64.

---

### Post by BarfBag on 2012-12-09
Having an issue on 12.04 x64.  The program installs through the terminal, but when I go to click on the icon; nothing happens at all.  Does anybody know what's going on here?

---

### Post by silverhaze06 on 2012-12-09
> **BarfBag said:**
> Having an issue on 12.04 x64.  The program installs through the terminal, but when I go to click on the icon; nothing happens at all.  Does anybody know what's going on here?

did you have wine installed at all before installing this? i had the same problem untill i uninstalled everything and did it again. i still had the problem a few times after, but then all of a sudden it just started working on its own for me.

---

### Post by pompel9 on 2012-12-09
> **BarfBag said:**
> Having an issue on 12.04 x64.  The program installs through the terminal, but when I go to click on the icon; nothing happens at all.  Does anybody know what's going on here?

I had the same problem. I solved it by purging and using autoremove.

```
sudo apt-get purge netflix-desktop:i386
```

and

```
sudo apt-get autoremove
```

Then I installed with this command.

```
sudo apt-get install netflix-desktop
```

That did the trick for me.

---

### Post by skublife on 2012-12-10
I've been having a problem with playback being at double speed. Any one know a fix for this? Everything else is working fine, I am on a 64 bit system.

---

### Post by JimSBjd on 2012-12-11
Okay - has this happened to anyone:

(after adding the ppa and doing apt-get update)

sudo apt-get install netflix-desktop results in error: Depends: wine-compholio (> 1.5.16) but is not installable

so next I tried sudo apt-get install wine-compholio, and it tells me that wine-compholio is not available, and "E: Package 'wine-compholio' has no installation candidate"

This error occurred on ubuntu 12.10 x64.  I have installed this no problem on 12.10 x86, but get this error on 64-bit.  

I did check and I have main, universe, restricted, and multiverse enabled.

---

### Post by sdowney717 on 2012-12-11
> **skublife said:**
> I've been having a problem with playback being at double speed. Any one know a fix for this? Everything else is working fine, I am on a 64 bit system.

try the command  pulseaudio -k

then rerun it.

---

### Post by dniMretsaM on 2012-12-11
> **JimSBjd said:**
> Okay - has this happened to anyone:

(after adding the ppa and doing apt-get update)

sudo apt-get install netflix-desktop results in error: Depends: wine-compholio (> 1.5.16) but is not installable

so next I tried sudo apt-get install wine-compholio, and it tells me that wine-compholio is not available, and "E: Package 'wine-compholio' has no installation candidate"

This error occurred on ubuntu 12.10 x64.  I have installed this no problem on 12.10 x86, but get this error on 64-bit.  

I did check and I have main, universe, restricted, and multiverse enabled.

Try installing again. It's possible you tried to install Netflix Desktop while the modified version of WINE was still building on launchpad. I'm running 12.10 with the latest version and am having no issues.

---

### Post by skublife on 2012-12-11
> **sdowney717 said:**
> try the command  pulseaudio -k

then rerun it.
That worked! Thanks a bunch, new to linux and have been having a "fun" time getting everything working.

---

### Post by jimothyr on 2012-12-12
Just to let the community know. This app also works on lovefilm in the uk.  Just ctrl-l to get a url input box and goto [www.lovefilm.com](www.lovefilm.com). Works pretty well. A little stuttery at times but watchable.

---

### Post by Pilot6 on 2012-12-12
Does this solution work with eurosport? They also use Silverlight with DRM.

---

### Post by compholio on 2012-12-12
> **JimSBjd said:**
> ...
sudo apt-get install netflix-desktop results in error: Depends: wine-compholio (> 1.5.16) but is not installable
...

Please try running the following command:
```
dpkg --print-foreign-architectures
```
If it does not output "i386" then that means that Multi-Arch support is disabled.  You can enable Multi-Arch by:
* Ubuntu 12.10:
```
sudo dpkg --add-architecture i386 && sudo apt-get update
```
* Ubuntu 12.04:
```
echo "foreign-architecture i386" | sudo tee /etc/dpkg/dpkg.cfg.d/multiarch && sudo apt-get update
```

---

### Post by silverhaze06 on 2012-12-12
At least this app is getting a little better with each update. I just cant wait until this is actually able to play video's in HD. It's still only playing 1 frame every half a second for me.

---

### Post by sselt on 2012-12-26
Is there instructions to manual compile?

---

### Post by Anders Stroem on 2012-12-26
> **silverhaze06 said:**
> At least this app is getting a little better with each update. I just cant wait until this is actually able to play video's in HD. It's still only playing 1 frame every half a second for me.

I'm not getting 2 fps as the above poster, but closer to 15 fps is still not good enough for watching a movie.

Hopefully, this project will improve over time, or Netflix might actually release a Linux client at some point.

---

### Post by pqwoerituytrueiwoq on 2012-12-26
> **sselt said:**
> Is there instructions to manual compile?
```
sudo apt-add-repository ppa:ehoover/compholio;sudo apt-get update;sudo apt-get install netflix-desktop gecko-mediaplayer
```
applicatsions->multimedia-> netflix desktop/search netflix desktop in the unity dash

---

### Post by arpanaut on 2012-12-26
I keep getting prompted to update silverlight from within the netflix-desktop,
If I allow this; is it going to screw-up things or is this the way it works?

I am very inexperienced with wine and am unsure how things are done.
Thanks!

---

### Post by pqwoerituytrueiwoq on 2012-12-26
wine uses a .wine folder in the home folder, the netflix desktop probably uses a similar folder if you copy it and then let it update and it fails you can just reset it from the backup

---

### Post by arpanaut on 2012-12-26
> **pqwoerituytrueiwoq said:**
> wine uses a .wine folder in the home folder, the netflix desktop probably uses a similar folder if you copy it and then let it update and it fails you can just reset it from the backup

Sounds like a plan.
Thanks!

---

### Post by sselt on 2012-12-28
> **pqwoerituytrueiwoq said:**
> ```
sudo apt-add-repository ppa:ehoover/compholio;sudo apt-get update;sudo apt-get install netflix-desktop gecko-mediaplayer
```applicatsions->multimedia-> netflix desktop/search netflix desktop in the unity dash

Thanks, however I was looking for compile instructions.

---

### Post by dardack on 2013-01-03
Anyone have this running on a 1st gen NVIDIA Ion and does it work?  Or does the Ion not able to handle it since not HW accelled.

---

### Post by neu5eeCh on 2013-01-03
> **arpanaut said:**
> I keep getting prompted to update silverlight from within the netflix-desktop,
If I allow this; is it going to screw-up things or is this the way it works?

I am very inexperienced with wine and am unsure how things are done.
Thanks!

Probably a week too late, but don't update silverlight.

---

### Post by neu5eeCh on 2013-01-03
> **Anders Stroem said:**
> I'm not getting 2 fps as the above poster, but closer to 15 fps is still not good enough for watching a movie.

Hopefully, this project will improve over time, or Netflix might actually release a Linux client at some point.

A wide variety of variables, not all related to power, appear to be at play. On my older HP 32 bit, Intel driven, laptop, the performance of the Netflix-Desktop is every bit as good as the Windows side. However, on my much more powerful 64 bit, Radeon driven 1080p VAIO, the performance is slower than the windows side and worse than on the much older and slower HP.

---

### Post by arpanaut on 2013-01-03
> **VTPoet said:**
> Probably a week too late, but don't update silverlight.
Thanks Man, I got distracted and let it be, then an update from the PPA did the silverlight upgrade for me.
I'll just let the system updates take care of things in the future.

---

### Post by eumpfenbach on 2013-01-06
Money.

It would be nice if the desktop could be minimized. I only see an "X" to exit. Maybe I'm missing it.

---

### Post by sdowney717 on 2013-01-08
> **eumpfenbach said:**
> Money.

It would be nice if the desktop could be minimized. I only see an "X" to exit. Maybe I'm missing it.

alt +v key then you can put in missing tool-navigation bars.
You can also update firefox from the about help menu.
And , you can delete the white round X in firefox add ons.

---

### Post by sdowney717 on 2013-01-08
frame rates, interesting talk about 24 vs 48 frames per second

[http://techland.time.com/2012/12/06/riddles-in-the-dark-the-hobbits-48-frames-per-second-explained/?iid=obnetwork](http://techland.time.com/2012/12/06/riddles-in-the-dark-the-hobbits-48-frames-per-second-explained/?iid=obnetwork)

some example showing this effect, which sometimes is very visible in Netflix. Something I have NOT noticed on Amazon prime or Hulu or youtube or even cbs on the net.

Netflix seems to have the noticeable judder, sometimes only tiny, sometimes a lot, which I have seen so bad sometimes I cant even stand to watch. And I find it very annoying that this happens. So I wonder what is different about netflix.
It might have something to do with interpolation where software fills in generating extra frames. And then I hear that dedicated player hardware, people say does not show the juddering. So then you can blame the software.

[http://www.red.com/learn/red-101/high-frame-rate-video](http://www.red.com/learn/red-101/high-frame-rate-video)

---

### Post by tjeremiah on 2013-01-09
> **sdowney717 said:**
> alt +v key then you can put in missing tool-navigation bars.
You can also update firefox from the about help menu.
And , you can delete the white round X in firefox add ons.

Psych :guitar:

---

### Post by pqwoerituytrueiwoq on 2013-01-09
> **tjeremiah said:**
> Psych :guitar:
probally does tno work if you clicked on a flash or silverlight item on the page
i know flash captures every key combo for me, i use ctrl+L a lot and it always annoys me

---

### Post by Curtis6767 on 2013-01-29
I installed this on 13.04 today and it seems to work, though I really haven't spent much time with it. Just loaded it and went to silverlight site that I visit, and silverlight worked.

But, I can't get it out of full-screen mode. Can someone help me with that?

Never mind. Found it. F11

BTW, to use the browser Alt+D gives you a drop down menu.

---

### Post by jhoyla on 2013-02-09
I'm using Wubi, and thus my filesystem is NTFS. How can I set the user_xattr property? My root disk doesn't even appear in FSTAB. I think it's provided by NTFS-3g, but I can't work out how to change the flags on it.

---

### Post by moocow1452 on 2013-02-09
Think we could get this working in a modified version of XBMCFlix?

---

### Post by tjeremiah on 2013-02-11
I went back to test this and I have to say that I am shocked :o . It is a tad bit behind Windows (occasional stutter every 2-5 mins or so.) but the video playback is defiantly watchable. Below are some screens, sig is my configuration.

---

### Post by aleaper on 2013-02-12
Okay so long time viewer of the forums since 09 and first time I have ever needed to post because I am literally stumped already. I've tried almost everything in this forum and just can not get it to work. For some odd reason every time even after adding [FONT=Courier New]user_xattr[/FONT] to the 4th column. After I try to open netflix it still give me "It appears that you do not have extended file system attributes enabled, please enable the user_xattr option for your filesystem and try again." Not to sure what else to do. I've purged everything and installed and still nothing. I'm using 12.10 64 bit. Thanks for the help.

---

### Post by Saeed Alalwan on 2013-02-19
I had a similar problem. I added [FONT=Courier New]user_xattr [/FONT]to the root partition and I was still getting the error. I have multiple partitions on my system and the way I fixed the problem is by adding  [FONT=Courier New]user_xattr[/FONT] to the home and root partitions. Hope this helps,

> **aleaper said:**
> Okay so long time viewer of the forums since 09 and first time I have ever needed to post because I am literally stumped already. I've tried almost everything in this forum and just can not get it to work. For some odd reason every time even after adding [FONT=Courier New]user_xattr[/FONT] to the 4th column. After I try to open netflix it still give me "It appears that you do not have extended file system attributes enabled, please enable the user_xattr option for your filesystem and try again." Not to sure what else to do. I've purged everything and installed and still nothing. I'm using 12.10 64 bit. Thanks for the help.

---

### Post by zaospawn on 2013-02-21
I run Ubuntu 12.10 dual boot through Wubi on my Windows 7 machine. The first 2 commands worked fine but when I did "sudo apt-get install netflix-desktop" here's what I got:

> brian@ubuntu:~$ sudo apt-get install netflix-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 netflix-desktop : Depends: wine-browser-installer but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
brian@ubuntu:~$

I have no idea how to install things outside the Software Center. Please be nice and easy on me, I am a technology noob and 100% new to Linux.

---

### Post by MadmanRB on 2013-02-21
> **zaospawn said:**
> I run Ubuntu 12.10 dual boot through Wubi on my Windows 7 machine. The first 2 commands worked fine but when I did "sudo apt-get install netflix-desktop" here's what I got:



I have no idea how to install things outside the Software Center. Please be nice and easy on me, I am a technology noob and 100% new to Linux.

If using software center try installing synaptic, it usually simplifies command line solutions

---

### Post by zaospawn on 2013-02-21
> **MadmanRB said:**
> If using software center try installing synaptic, it usually simplifies command line solutions

I tried doing it through Synaptic and I get the same series of error messages about dependencies and broken packages. I have no idea what I am doing :/

---

### Post by sdowney717 on 2013-02-22
> **zaospawn said:**
> I tried doing it through Synaptic and I get the same series of error messages about dependencies and broken packages. I have no idea what I am doing :/

post the response of these commands
[http://askubuntu.com/questions/223237/unable-to-correct-problems-you-have-held-broken-packages](http://askubuntu.com/questions/223237/unable-to-correct-problems-you-have-held-broken-packages)

---

### Post by aleaper on 2013-02-22
> **Saeed Alalwan said:**
> I had a similar problem. I added [FONT=Courier New]user_xattr [/FONT]to the root partition and I was still getting the error. I have multiple partitions on my system and the way I fixed the problem is by adding  [FONT=Courier New]user_xattr[/FONT] to the home and root partitions. Hope this helps,

I tried, but still no luck. Here's what I have so far. I took off the second   [FONT=Courier New]user_xattr[/FONT] and I originally had it after defaults on the other partition.
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=145e66f8-d481-4b2e-9125-37d6335b61ef /               ext4    errors=remount-ro,user_xattr 0       1
# /home was on /dev/sda6 during installation
UUID=938b987a-d64f-4a78-af4f-b376a991404b /home           ext3    defaults        0       2
```

---

### Post by MadmanRB on 2013-02-22
Well I think its broken now if you are using 64bit, arglefvlargleblarge, back to 32bit for me

---

### Post by CDR Services on 2013-02-23
What I did was first I installed wine application layer from the software center and agree to the ms fonts install. Then go here [http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html](http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html), Follow the instructions copy and paste those lines into terminal it worked in 12.04 lts the first time you run netflix it prompts you to install a couple more dependent plugins but it worked like a charm

---

### Post by MadmanRB on 2013-02-23
> **CDR Services said:**
> What I did was first I installed wine application layer from the software center and agree to the ms fonts install. Then go here [http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html](http://www.iheartubuntu.com/2012/11/ppa-for-netflix-desktop-app.html), Follow the instructions copy and paste those lines into terminal it worked in 12.04 lts the first time you run netflix it prompts you to install a couple more dependent plugins but it worked like a charm

I did all that, nope a no go.

---

### Post by zaospawn on 2013-02-23
I believe all the dependency/broken package issues I have is due to some Wubi quirk. From a link someone here shared I discovered that by doing this:

> sudo aptitude install netflix-desktop

The terminal found all the packages that need to be changed, removed, or repaired and then went through the motions of doing so.  By doing this it also installed all the versions and apps of Wine I needed among many missing libraries. After doing the command above I went ahead and did the original three commands from Post #1 and it worked like a charm. My advice for any Wubi users here to try aptitude instead of apt-get. Thanks everyone for your patience and diligence!

:D

---

### Post by send2 on 2013-02-23
This is how i installed Netflix on my machine, I am running Ubuntu 12.04 LTS, it should also work for 12.10:

[http://www.techdrivein.com/2012/11/howto-make-netflix-work-ubuntu1204-ubuntu1210-PPA.html](http://www.techdrivein.com/2012/11/howto-make-netflix-work-ubuntu1204-ubuntu1210-PPA.html)

I hope it helps someone.

---

### Post by aleaper on 2013-02-24
I've tried nearly everything said in this thread and I still get that same error still. 

> It appears that you do not have extended file system attributes enabled, please enable the user_xattr option for your filesystem and try again.

---

### Post by chevyiron420 on 2013-02-26
I have installed Netflix on two older laptops and it worked. However, I cant make it work for me on my desktop. Its a pentium4 3 ghz with 2 gig ram, running a fresh install of 12.04. When I click on the netflix icon It opens the page and lets me choose a movie. Then the screen scrambles a second, then either returns to the netflix page locked up, or the screen goes black. I'm disappointed.

---

### Post by MadmanRB on 2013-02-26
Yeah its a workaround alright, good if you can get it working its great but on some setups meh.

---

### Post by aleaper on 2013-02-28
So I was able to install it into one of my friends laptop's just fine. Came back home and I decided to purge anything I might have downloaded trying to make this work. Re did everything step by step and still no luck. I keep getting that same error.

> It appears that you do not have extended file system attributes enabled, please enable the user_xattr option for your filesystem and try again.

Any help?

---

### Post by oldos2er on 2013-02-28
[http://ubuntuforums.org/showthread.php?t=2097139](http://ubuntuforums.org/showthread.php?t=2097139)

---

### Post by aleaper on 2013-02-28
> **oldos2er said:**
> [http://ubuntuforums.org/showthread.php?t=2097139](http://ubuntuforums.org/showthread.php?t=2097139)

Google led me to that post a long time ago. Like I said back on page 29, post #282, I have read this whole thread and nothing has worked. Possibly the one I think that might work for me is the post #283 by [**[COLOR=#000000]Saeed Alalwan[/COLOR]**]("http://ubuntuforums.org/member.php?u=1790804") which I did put user_xattr on both partitions and it still did not work. I think that I might have put user_xattr on the wrong part of the second partition but not sure. Thanks for trying though. I tried looking through google and no luck either on other websites.

---

### Post by sdowney717 on 2013-03-01
> **aleaper said:**
> Google led me to that post a long time ago. Like I said back on page 29, post #282, I have read this whole thread and nothing has worked. Possibly the one I think that might work for me is the post #283 by [**[COLOR=#000000]Saeed Alalwan[/COLOR]**]("http://ubuntuforums.org/member.php?u=1790804") which I did put user_xattr on both partitions and it still did not work. I think that I might have put user_xattr on the wrong part of the second partition but not sure. Thanks for trying though. I tried looking through google and no luck either on other websites.

What type file system is on your computer?
I use ext4.

---

### Post by oldos2er on 2013-03-01
> **aleaper said:**
> Google led me to that post a long time ago. Like I said back on page 29, post #282, I have read this whole thread and nothing has worked. Possibly the one I think that might work for me is the post #283 by [**[COLOR=#000000]Saeed Alalwan[/COLOR]**]("http://ubuntuforums.org/member.php?u=1790804") which I did put user_xattr on both partitions and it still did not work. I think that I might have put user_xattr on the wrong part of the second partition but not sure. Thanks for trying though. I tried looking through google and no luck either on other websites.

Ah, forgive me for not reading through the entire thread. You really should ask this question in a support area, and as sdowney717 suggested, mention which file system you're using. I *think* the xattr fix requires ext4.

---

### Post by aleaper on 2013-03-01
> **sdowney717 said:**
> What type file system is on your computer?
I use ext4.

One is ext4 the other is ext3.

> **oldos2er said:**
> Ah, forgive me for not reading through the entire thread. You really  should ask this question in a support area, and as sdowney717 suggested,  mention which file system you're using. I *think* the xattr fix requires ext4.

Not a problem. Thanks for showing me where I could some extra help. I just figured I would ask here first before I made a thread about it.

---

### Post by sdowney717 on 2013-03-01
You have 2 partitions?
You can convert ext3 to ext4 without losing data

> To enable the ext4 features on an existing ext3 filesystem, use the command:
# tune2fs -O extents,uninit_bg,dir_index /dev/DEV
WARNING: Once you run this command, the filesystem will no longer be mountable using the ext3 filesystem!
After running this command (specifically, after setting the uninit_bg parameter), you MUST run fsck to fix up some on-disk structures that tune2fs has modified:
# e2fsck -fDC0 /dev/DEV


[https://ext4.wiki.kernel.org/index.php/Ext4_Howto](https://ext4.wiki.kernel.org/index.php/Ext4_Howto)

---

### Post by jacatone on 2013-03-02
I tried this with Ubuntu 10.10 and everything loaded OK, but I only get sound and no video. Anyone have a solution? Thanks.

---

### Post by tjeremiah on 2013-03-04
there was a recent update so check again.

---

### Post by slooksterpsv on 2013-03-04
I'm running 12.10 with Gnome-Shell fglrx version 9.0 and followed this guide, and it works, it runs, I can actually watch movies on Ubuntu. Really considering destroying Windows 8 - [http://www.techrepublic.com/blog/opensource/how-to-get-netflix-streaming-on-ubuntu-1210/4019](http://www.techrepublic.com/blog/opensource/how-to-get-netflix-streaming-on-ubuntu-1210/4019)

---

### Post by Stan Lanning on 2013-04-03
Is your home directory auto-mounted?  That caused me problems as you described (claim that I needed user_xattr).  Switching to an account with a local home directory took care of that.

---

### Post by mamamia88 on 2013-04-03
Still too choppy on a netbook with xubuntu.  Even though it worked fine on windows 7.  I don't really take it anywhere though and have and watch netflix mostly on my ps3 and have a nexus 7 and vita for on the go son not a really big deal.

---

### Post by WTMBEACH on 2013-04-03
It doesn't work for me, can anyone please give me some tips that I can use Netflix on my Ubuntu OS?

---

### Post by mJayk on 2013-04-03
> **slooksterpsv said:**
> I'm running 12.10 with Gnome-Shell fglrx version 9.0 and followed this guide, and it works, it runs, I can actually watch movies on Ubuntu. Really considering destroying Windows 8 - [http://www.techrepublic.com/blog/opensource/how-to-get-netflix-streaming-on-ubuntu-1210/4019](http://www.techrepublic.com/blog/opensource/how-to-get-netflix-streaming-on-ubuntu-1210/4019)


do eet :D

---

### Post by breezypt on 2013-04-06
I used to run Netflix through my bluray player, but then discovered that with Roku 3 box I can turn my LCD slightly older flat panel large screen TV into a smart TV with many , many apps. So I bought a Roku 3 box, I can stay in bed at night, plug in the head phones to the remote that came with Roku3 and it shuts off the TV sound and comes through the head phones, only problem is that it goes through bateries fast if you fall asleep with it on like I do, hence the point of having TV on when trying to sleep. But at least no one else in the house has to listen to TV at 2 in the morning. If my Roku box should fail I can always revert back to my bluray player where I have to get up and plug in an extention cord for earbuds to the TV so no one gets kept awake by the sound still workable though.

That being said it would be nice to have netflix play on my 22 inch wide screen monitor for unbunto, its smaller than my TV but it would save a lot on electric when surfing the web to have a movie playing too that I can go back and forth to.

As for Android, netflix plays the best on my LG Motion dual core processor than anything else, and I can use it as a queue too! And the Motion is way far from latest or greatest. but it is fast as hell, can miltitask on it, its just has a slightly smaller screen. But isn't Android Ice Cream Sandwich built on linux in the first place? If so than why can't netflix get it to work on a regular linux distro, such as Ubunto? Hint, hint???? ;)

---

### Post by chizzan on 2013-04-08
> **sdowney717 said:**
> try the command  pulseaudio -k

then rerun it.
Thank you sdowney717! Fixed my problem. (Ubuntu 12.04/ HP 23 AIO PC)

---

### Post by allovuhsudden on 2013-04-10
I'm running Ubuntu 12.10 and I successfully got this to work on my computer. I'm quite pleased, because I tried it before and it didn't work at all. One thing I did before was run 'sudo apt-get update' and then 'sudo apt-get upgrade' and then I ran the commands to install the Netflix Desktop app.

Thank you!

---

### Post by madjr on 2013-04-10
> **breezypt said:**
> I used to run Netflix through my bluray player, but then discovered that with Roku 3 box I can turn my LCD slightly older flat panel large screen TV into a smart TV with many , many apps. So I bought a Roku 3 box, I can stay in bed at night, plug in the head phones to the remote that came with Roku3 and it shuts off the TV sound and comes through the head phones, only problem is that it goes through bateries fast if you fall asleep with it on like I do, hence the point of having TV on when trying to sleep. But at least no one else in the house has to listen to TV at 2 in the morning. If my Roku box should fail I can always revert back to my bluray player where I have to get up and plug in an extention cord for earbuds to the TV so no one gets kept awake by the sound still workable though.

That being said it would be nice to have netflix play on my 22 inch wide screen monitor for unbunto, its smaller than my TV but it would save a lot on electric when surfing the web to have a movie playing too that I can go back and forth to.

As for Android, netflix plays the best on my LG Motion dual core processor than anything else, and I can use it as a queue too! And the Motion is way far from latest or greatest. but it is fast as hell, can miltitask on it, its just has a slightly smaller screen. But isn't Android Ice Cream Sandwich built on linux in the first place? If so than why can't netflix get it to work on a regular linux distro, such as Ubunto? Hint, hint???? ;)

- it's now running on Google Chrome OS even on html5.
so yes they can do it even if exclusive to Chrome.

But
maybe we can get it fully ported native when Ubuntu  phone ship.

---

### Post by randumari on 2013-04-12
[**[COLOR=#000000]jacatone[/COLOR]**]("http://ubuntuforums.org/member.php?u=36121"), try resizing your screen.

Anybody log into netflix this morning and get redirected to a silverlight download link?  Am currently unable to watch.

---

### Post by oldos2er on 2013-04-12
> **randumari said:**
> Anybody log into netflix this morning and get redirected to a silverlight download link?  Am currently unable to watch.

Got the same a couple days ago. I fixed it with ```
sudo apt-get purge netflix-desktop

[s]rm -rf ~/.wine/[/s]

rm -rf ~/.wine-browser/

sudo apt-get install netflix-desktop
```

I don't know if removing ~/.wine/ is actually necessary. Obviously if you have other Windows programs installed via wine (I don't) you'll want to make sure to backup anything before removing it.

Edit: It's not necessary to run rm -rf ~/.wine/

---

### Post by randumari on 2013-04-12
Ann, that did it, thanks!  HD is still choppy, but if I turn it off, I can get back to watching Eureka :-)

---

### Post by oldos2er on 2013-04-12
Glad it worked!

---

### Post by breezypt on 2013-04-13
> But
maybe we can get it fully ported native when Ubuntu  phone ship. Did you say *phone?* As in do they have plans for all us unfortunate android owners to let us sync our phones???  <snip>

---

### Post by breezypt on 2013-04-14
My apologies to my previous post, I was trying to make a light hearted joke. Won't happen again..

---

### Post by GeneralZod on 2013-04-16
Interesting:

[http://www.theverge.com/2013/4/15/4228248/netflix-plans-its-move-from-microsoft-silverlight-to-html5-video](http://www.theverge.com/2013/4/15/4228248/netflix-plans-its-move-from-microsoft-silverlight-to-html5-video)

---

### Post by tjeremiah on 2013-04-16
> **GeneralZod said:**
> Interesting:

[http://www.theverge.com/2013/4/15/4228248/netflix-plans-its-move-from-microsoft-silverlight-to-html5-video](http://www.theverge.com/2013/4/15/4228248/netflix-plans-its-move-from-microsoft-silverlight-to-html5-video)

I was just about to post this :). Hope this comes soon.

---

### Post by irv on 2013-04-16
I just read this and it is looking like it will be possible to view Netflix on Linux soon. Google needs to work on  building that third extension into the browser for this to happen.

---

### Post by Doombringer on 2013-05-11
I installed it using the PPA but whenever I login to netflix, I only get a black screen. tried purging/reinstalling, no luck.

I am on Intel SandyBridge video btw.

---

### Post by tjeremiah on 2013-05-12
> **Doombringer said:**
> I installed it using the PPA but whenever I login to netflix, I only get a black screen. tried purging/reinstalling, no luck.

I am on Intel SandyBridge video btw.

if you hear audio theres a chance you can still view the video by clicking on the bottom right corner area until you eventually click the fullscreen button. When you do, usually the video is then viewable.

---

### Post by Bryce_Herod on 2014-03-31
Thanks that was easy peasy.

---

### Post by help_me2 on 2014-03-31
You're better off installing XBMC in Ubuntu and watching any movie you want. Or get a Chromecast.

---

