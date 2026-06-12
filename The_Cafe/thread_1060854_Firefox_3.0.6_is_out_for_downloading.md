---
title: "Firefox 3.0.6 is out for downloading"
date: 2009-02-05
forum: The Cafe
---

### Post by newbie2 on 2009-02-05
[http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)
:popcorn:

---

### Post by x33a on 2009-02-05
They have fixed some security issues, so we might see this in the repositories :)

---

### Post by SunnyRabbiera on 2009-02-05
Expect it soon, especially if its a major security issue...

---

### Post by Skripka on 2009-02-05
Hmmm....how many of my extensions will be broken by upgrading.... #-o

---

### Post by OrangeCrate on 2009-02-05
> **Skripka said:**
> Hmmm....how many of my extensions will be broken by upgrading.... #-o

Most likely none. This is an update, not an upgrade.

---

### Post by Polygon on 2009-02-05
complete list of bugs fixed:

[https://bugzilla.mozilla.org/buglist.cgi?keywords_type=anywords&keywords=fixed1.9.0.6+verified1.9.0.6](https://bugzilla.mozilla.org/buglist.cgi?keywords_type=anywords&keywords=fixed1.9.0.6+verified1.9.0.6)

security advisories fixed by 3.0.6:


> 
[http://www.mozilla.org/security/known-vulnerabilities/firefox30.html#firefox3.0.6](http://www.mozilla.org/security/known-vulnerabilities/firefox30.html#firefox3.0.6)
MFSA 2009-06  Directives to not cache pages ignored
MFSA 2009-05 XMLHttpRequest allows reading HTTPOnly cookies
MFSA 2009-04 Chrome privilege escalation via local .desktop files
MFSA 2009-03 Local file stealing with SessionStore
MFSA 2009-02 XSS using a chrome XBL method and window.eval
MFSA 2009-01 Crashes with evidence of memory corruption (rv:1.9.0.6)


other things:

> 
# Fixed several security issues.
# Fixed several stability issues.
# In previous versions of Firefox, some users experienced a problem where parts of the screen were not properly displaying after Firefox was open for long periods of time.
# Improved the ability for scripted commands (including those included in popular extensions like Adblock Plus) to work properly with plugins. (bug 438830)
# Removed the client user ID from crash reports.
# Fixed issues with the display of some Indic scripts.


---

### Post by binbash on 2009-02-05
thanks for the changelog

---

### Post by speedwell68 on 2009-02-05
I'll wait for it to hit the repositories.

---

### Post by Kar.ma on 2009-02-06
Hi. I've just known "Ubuntu Firefox" doesn't update by itself. Is there any way to update it manually?

Repository works only for "Mozilla Firefox", that is the one manually installed (or by Synaptics) isn't it?

I'm just trying to understand a little more, thank you

---

### Post by jespdj on 2009-02-06
No, the automatic update from the repository only works if you've installed it from the repository. It does not work for manually installed software.

Just wait a few days until the update is in the repository.

---

### Post by brookie on 2009-02-06
what is the drawback for manually updating software in ubunbu like i did in windows? 

i'm new to ubuntu but really like it. i was searching on how to add firefox to the repository to get the new firefox 3.06 and found this thread.

i also manually installed and update deluge from the deluge website because the deluge version in the repository is version 0.9.5.3-1 and they have made many fixes and are up to version 1.1.2 on the deluge site. 

anyhow, please let me know why manually downloading and installing sw upgrades is not a good idea in ubuntu. i still have those old windows habits no? :) 

thanks, brook

---

### Post by andrewabc on 2009-02-06
With these small firefox updates, you would normally get the update in a week, so it is easier to wait for it than having to manually downloading and installing it every time there is a release.

---

### Post by Darkhack on 2009-02-06
What I want to know is why it takes so long for these important security updates to hit the repos.  Isn't the point of open source that we can get updates out faster?  Microsoft gets criticized for their monthly updates but if Canonical is taking a week or longer to get them out, it isn't that much better.  I'm not trolling.  I honestly what to know why the procedure takes so long and why it's not just a quick fix and bam, it's in the repos.

---

### Post by Slug71 on 2009-02-06
Its in Jaunty already.

---

### Post by smartboyathome on 2009-02-06
I'm not going to be upgrading, mostly since I am already running Firefox 3.1 and because it would take a long time to compile, and by the time it was done compiling my computer would have overheated. I use the PGO version of Firefox, btw. :P

---

### Post by andrewabc on 2009-02-06
> **Darkhack said:**
> What I want to know is why it takes so long for these important security updates to hit the repos.  Isn't the point of open source that we can get updates out faster?  Microsoft gets criticized for their monthly updates but if Canonical is taking a week or longer to get them out, it isn't that much better.  I'm not trolling.  I honestly what to know why the procedure takes so long and why it's not just a quick fix and bam, it's in the repos.

Just because software is opensource does not mean it can be distributed in a timely manner. They are probably testing out the new firefox to make sure it works correctly with ubuntu. Not much use in releasing a new firefox to everyone if there is a bug which makes firefox not perform correctly.

I doubt canonical is holding back the latest version just to make its users more insecure. Firefox is a main program in ubuntu, and I'm sure it has priority over many other software packages.

I believe with the last firefox release 3.0.5, canonical had it in the repositories to download in less than 48 hours.

I believe if you enable "proposed" repository you can get updates sooner, but they could be unstable.

---

### Post by Kow on 2009-02-09
> **andrewabc said:**
> Just because software is opensource does not mean it can be distributed in a timely manner. They are probably testing out the new firefox to make sure it works correctly with ubuntu. Not much use in releasing a new firefox to everyone if there is a bug which makes firefox not perform correctly.

I doubt canonical is holding back the latest version just to make its users more insecure. Firefox is a main program in ubuntu, and I'm sure it has priority over many other software packages.

I believe with the last firefox release 3.0.5, canonical had it in the repositories to download in less than 48 hours.

I believe if you enable "proposed" repository you can get updates sooner, but they could be unstable.

I believe this update also involves xulrunner-1.9 which is also a pretty long build. Remember they're building for several archs and several releases (hardy and intrepid.) I reported it Friday night and within an hour it was replied to saying it is in the security build queue.

---

### Post by FuturePilot on 2009-02-09
> **Kow said:**
> I believe this update also involves xulrunner-1.9 which is also a pretty long build. Remember they're building for several archs and several releases (hardy and intrepid.) I reported it Friday night and within an hour it was replied to saying it is in the security build queue.

It's probably already done, but it can take up to a week to do the QA testing.

---

### Post by jespdj on 2009-02-09
Why is everybody so impatient? Firefox 3.0.5 -> 3.0.6 is not such a big deal.

---

### Post by Niksko on 2009-02-09
Good work Mozilla!

As an aside, for some reason my school switched over to Vista and decided they needed FOUR browsers. FF, IE, Safari and Chrome.

As another aside but slightly more on topic, when is Firefox getting 'rip out' tabs. I heard whisperings a while ago.

In the end, bug fixes are good.

</ramble>

-Nik

---

### Post by Kow on 2009-02-10
> **jespdj said:**
> Why is everybody so impatient? Firefox 3.0.5 -> 3.0.6 is not such a big deal.

It fixes security vulnerabilities. It SHOULD be a big deal, more so than feature additions.

---

### Post by social_flea on 2009-02-10
> **Kow said:**
> It fixes security vulnerabilities. It SHOULD be a big deal, more so than feature additions.

Running Firefox 3.0.6 right now from Ubuntu updates. It usually takes a while, till everything is tested I guess.

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.6) Gecko/2009020911 Ubuntu/8.04 (hardy) Firefox/3.0.6

---

### Post by newbie2 on 2009-02-10
> **social_flea said:**
> Running Firefox 3.0.6 right now from Ubuntu updates. It usually takes a while, till everything is tested I guess.

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.6) Gecko/2009020911 Ubuntu/8.04 (hardy) Firefox/3.0.6
me too 

Mozilla/5.0 (X11; U; Linux x86_64; nl; rv:1.9.0.6) Gecko/2009020911 Ubuntu/8.10 (intrepid) Firefox/3.0.6

;-)

---

### Post by wolfen69 on 2009-02-11
yeah! that's what i'm talkin about!

but seriously, it's a non-event.  :rolleyes:

---

### Post by jespdj on 2009-02-11
I just got the update from the repository (I'm running Hardy).

See? You just have to be patient.

And the security problems were not so big that it was a matter of "stop using Firefox IMMEDIATELY and wait for the fix".

---

### Post by neilevan814 on 2009-02-11
I installed Firefox-3.06 last night and it broke my panel icon from working.  I restored a backup of my system and everything is working fine with Firefox-3.05.  Anyone else finding this problme with Firefox-3.06?

---

### Post by pol666 on 2009-02-11
well, i'm not hurry... I have FF 3.04 still. :P

---

### Post by FuturePilot on 2009-02-11
> **neilevan814 said:**
> I installed Firefox-3.06 last night and it broke my panel icon from working.  I restored a backup of my system and everything is working fine with Firefox-3.05.  Anyone else finding this problme with Firefox-3.06?

All is fine here. I think you might want to make sure the launcher settings are correct. Try removing the launcher and re-adding it.

---

### Post by neilevan814 on 2009-02-12
I did remove and re add the launcher.  It was set for command line firefox %u so, I tried changing it to firefox, no go, then to firefox-3.0, no go, then when I reverted to firefox-3.05 the command is set with just firefox and all is well.  I haven't tried to reinstall the upgrade for firefox since I restored my back up...a little gun shy right now...

---

### Post by -jay- on 2009-02-12
> **neilevan814 said:**
> I installed Firefox-3.06 last night and it broke my panel icon from working.  I restored a backup of my system and everything is working fine with Firefox-3.05.  Anyone else finding this problme with Firefox-3.06?

nope was just you mine is working fine

---

### Post by jrusso2 on 2009-02-12
> **neilevan814 said:**
> I installed Firefox-3.06 last night and it broke my panel icon from working.  I restored a backup of my system and everything is working fine with Firefox-3.05.  Anyone else finding this problme with Firefox-3.06?


You installed from backup when all you had to do was make a new short cut?

---

### Post by GiveLove on 2009-03-03
Hi Everyone, :)

Am I to understand correctly that the Firefox v3.0.6 update has been released to the Ubuntu repositories for Intrepid Ibex 8.10 to update automatically? 

If that's the case there must be something wrong with my Ubunto 8.10 as I have not had any updates. And Firefox is still at 3.0.5. 

I would appreciate a response when anyone is able. As I'm starting to be concerned that there is something not working correctly with the apt-get update software. 
Thanks.

---

### Post by FuturePilot on 2009-03-03
> **GiveLove said:**
> Hi Everyone, :)

Am I to understand correctly that the Firefox v3.0.6 update has been released to the Ubuntu repositories for Intrepid Ibex 8.10 to update automatically? 

If that's the case there must be something wrong with my Ubunto 8.10 as I have not had any updates. And Firefox is still at 3.0.5. 

I would appreciate a response when anyone is able. As I'm starting to be concerned that there is something not working correctly with the apt-get update software. 
Thanks.

Yes, it has been released for 8.10 for a while now. 
Perhaps posting the output of
```
cat /etc/apt/sources.list
```
might shed some light on your problem.

---

### Post by jespdj on 2009-03-04
> **GiveLove said:**
> Am I to understand correctly that the Firefox v3.0.6 update has been released to the Ubuntu repositories for Intrepid Ibex 8.10 to update automatically?
Yes, it has been out for a few weeks already, for Ubuntu 8.04 as well as 8.10.

Try this:
```
sudo apt-get update
```
to make Ubuntu look for updates.

---

### Post by GiveLove on 2009-03-04
Thank you so much for responding. I'm glad I posted something as I now know something is not working correctly.

Here's the output for:
cat /etc/apt/sources.list

```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ intrepid main restricted
deb-src http://mirrors.ccs.neu.edu/archive.ubuntu.com/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ intrepid-updates main restricted
deb-src http://mirrors.ccs.neu.edu/archive.ubuntu.com/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ intrepid universe
deb-src http://mirrors.ccs.neu.edu/archive.ubuntu.com/ intrepid universe
deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ intrepid-updates universe
deb-src http://mirrors.ccs.neu.edu/archive.ubuntu.com/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ intrepid multiverse
deb-src http://mirrors.ccs.neu.edu/archive.ubuntu.com/ intrepid multiverse
deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ intrepid-updates multiverse
deb-src http://mirrors.ccs.neu.edu/archive.ubuntu.com/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ intrepid-security main restricted
deb-src http://mirrors.ccs.neu.edu/archive.ubuntu.com/ intrepid-security main restricted
deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ intrepid-security universe
deb-src http://mirrors.ccs.neu.edu/archive.ubuntu.com/ intrepid-security universe
deb http://mirrors.ccs.neu.edu/archive.ubuntu.com/ intrepid-security multiverse
deb-src http://mirrors.ccs.neu.edu/archive.ubuntu.com/ intrepid-security multiverse

```

And here's the output for:
sudo apt-get update

```
Get:1 http://mirrors.ccs.neu.edu intrepid Release.gpg [189B]
Ign http://mirrors.ccs.neu.edu intrepid/main Translation-en_US
Ign http://mirrors.ccs.neu.edu intrepid/restricted Translation-en_US
Ign http://mirrors.ccs.neu.edu intrepid/universe Translation-en_US
Ign http://mirrors.ccs.neu.edu intrepid/multiverse Translation-en_US
Get:2 http://mirrors.ccs.neu.edu intrepid-updates Release.gpg [189B]
Ign http://mirrors.ccs.neu.edu intrepid-updates/main Translation-en_US
Ign http://mirrors.ccs.neu.edu intrepid-updates/restricted Translation-en_US
Ign http://mirrors.ccs.neu.edu intrepid-updates/universe Translation-en_US
Ign http://mirrors.ccs.neu.edu intrepid-updates/multiverse Translation-en_US
Get:3 http://mirrors.ccs.neu.edu intrepid-security Release.gpg [189B]
Ign http://mirrors.ccs.neu.edu intrepid-security/main Translation-en_US
Ign http://mirrors.ccs.neu.edu intrepid-security/restricted Translation-en_US
Ign http://mirrors.ccs.neu.edu intrepid-security/universe Translation-en_US
Ign http://mirrors.ccs.neu.edu intrepid-security/multiverse Translation-en_US
Get:4 http://mirrors.ccs.neu.edu intrepid Release [65.9kB]
Get:5 http://mirrors.ccs.neu.edu intrepid-updates Release [51.2kB]
Get:6 http://mirrors.ccs.neu.edu intrepid-security Release [44.0kB] 
Get:7 http://mirrors.ccs.neu.edu intrepid/main Packages [1256kB]
Get:8 http://mirrors.ccs.neu.edu intrepid/restricted Packages [8408B]
Get:9 http://mirrors.ccs.neu.edu intrepid/main Sources [505kB]    
Get:10 http://mirrors.ccs.neu.edu intrepid/restricted Sources [3113B]
Get:11 http://mirrors.ccs.neu.edu intrepid/universe Packages [4542kB]
Get:12 http://mirrors.ccs.neu.edu intrepid/universe Sources [1981kB]           
Get:13 http://mirrors.ccs.neu.edu intrepid/multiverse Packages [199kB]         
Get:14 http://mirrors.ccs.neu.edu intrepid/multiverse Sources [95.8kB]         
Get:15 http://mirrors.ccs.neu.edu intrepid-updates/main Packages [295kB]       
Get:16 http://mirrors.ccs.neu.edu intrepid-updates/restricted Packages [6843B] 
Get:17 http://mirrors.ccs.neu.edu intrepid-updates/main Sources [91.0kB]       
Get:18 http://mirrors.ccs.neu.edu intrepid-updates/restricted Sources [2016B]  
Get:19 http://mirrors.ccs.neu.edu intrepid-updates/universe Packages [60.0kB]  
Get:20 http://mirrors.ccs.neu.edu intrepid-updates/universe Sources [15.2kB]   
Get:21 http://mirrors.ccs.neu.edu intrepid-updates/multiverse Packages [5200B] 
Get:22 http://mirrors.ccs.neu.edu intrepid-updates/multiverse Sources [2366B]  
Get:23 http://mirrors.ccs.neu.edu intrepid-security/main Packages [60.2kB]     
Get:24 http://mirrors.ccs.neu.edu intrepid-security/restricted Packages [1785B]
Get:25 http://mirrors.ccs.neu.edu intrepid-security/main Sources [18.0kB]      
Get:26 http://mirrors.ccs.neu.edu intrepid-security/restricted Sources [571B]  
Get:27 http://mirrors.ccs.neu.edu intrepid-security/universe Packages [26.0kB] 
Get:28 http://mirrors.ccs.neu.edu intrepid-security/universe Sources [5116B]   
Get:29 http://mirrors.ccs.neu.edu intrepid-security/multiverse Packages [1330B]
Get:30 http://mirrors.ccs.neu.edu intrepid-security/multiverse Sources [584B]  
Fetched 9344kB in 29s (319kB/s)                                                
Reading package lists... Done

```

I hope you can find an answer to fix this problem.
Thanks again.:)

---

### Post by GiveLove on 2009-03-04
I think I fixed it on my own. After my prior posts, it occurred to me that I should trying changing repositories. I changed it to "Server for United States". And after downloading files to check for updates, I suddenly had 89 updates to download and install, which Firefox 3.0.6 was one of them. Yikes! I hope no one pwned my PC in the meantime! 8-[

Generally when I install Ubuntu, in "Software Sources" I use the feature "Select Best Server" to have it look for the closest/fastest software repository. Which the nea.edu server was the result which I chose. Now I'm wondering, what was at fault? The repository, or something within Ubuntu 8.10? 

I have to say, it's kind of scary to not have any feedback from apt-get that it is not getting updates. Had I known that when it happened I would have immediately looked into correcting it. Now I have to make the same change on my other Ubuntu PC.

Thanks for helping out. :)

---

### Post by FuturePilot on 2009-03-04
> **GiveLove said:**
> I think I fixed it on my own. After my prior posts, it occurred to me that I should trying changing repositories. I changed it to "Server for United States". And after downloading files to check for updates, I suddenly had 89 updates to download and install, which Firefox 3.0.6 was one of them. Yikes! I hope no one pwned my PC in the meantime! 8-[

Generally when I install Ubuntu, in "Software Sources" I use the feature "Select Best Server" to have it look for the closest/fastest software repository. Which the nea.edu server was the result which I chose. Now I'm wondering, what was at fault? The repository, or something within Ubuntu 8.10? 

I have to say, it's kind of scary to not have any feedback from apt-get that it is not getting updates. Had I known that when it happened I would have immediately looked into correcting it. Now I have to make the same change on my other Ubuntu PC.

Thanks for helping out. :)
Usually the mirrors are a few weeks behind the main repos.

---

### Post by andrewabc on 2009-03-04
> **FuturePilot said:**
> Usually the mirrors are a few weeks behind the main repos.

Some mirrors are only 6-24 hours behind. Others 1 week. I make sure to not use a mirror that is "a few weeks behind". I havn't seen many of those.

See mirror list here:
[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by GiveLove on 2009-03-05
I don't think this was a matter of a repo that is a bit behind. As I would have gotten other updates besides Firefox. Prior to fixing this problem, I hadn't had any updates for at least two weeks, maybe more. Besides, looking at the link from andrewabc, the repo I had selected is up to date. At this point I'm inclined to think the problem was on the operating system side.

---

