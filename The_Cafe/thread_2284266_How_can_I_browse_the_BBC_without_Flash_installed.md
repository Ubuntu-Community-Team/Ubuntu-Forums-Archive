---
title: "How can I browse the BBC without Flash installed?"
date: 2015-06-28
forum: The Cafe
---

### Post by coldraven on 2015-06-28
I uninstalled Flash after the latest security bungles and also Chrome after they wanted to listen to everything that I say.

Now when I browse the BBC I get the "You need Flash" message, switching the user agent to an iPad and Firefox will not play mp4s.
I would prefer a solution using Firefox but I will use a different browser if that is the only way to do it.
Most of my search results are out of date, so has anyone solved this?

---

### Post by matt_symes on 2015-06-28
Hi

You can install pepper flash in Firefox without installing Chrome.

If you are interested then post back and I'll post instructions in my next post.

Kind regards

---

### Post by grahammechanical on 2015-06-28
Ubuntu Web Browser (aka, Browser) will access the BBC web site without flash being installed. But if we try to play video or audio we get the message that we need to install Flash. This will happen even if we have already installed Flash on the system for another browser. But for getting the news it is fine.

I also use Browser for accessing newspaper websites that are so heavily loaded with flash content adverts as to severely slow down Firefox or Chromium But they do not affect Browser.

Regards

---

### Post by coldraven on 2015-06-28
> **matt_symes said:**
> Hi

You can install pepper flash in Firefox without installing Chrome.

If you are interested then post back and I'll post instructions in my next post.

Kind regards
I've had a quick look at Pepperflash and it would be interesting. However, surely there's a browser out there which will play video MP4s and make the BBC think that I'm using an iPad or something. The user agent switcher that I'm using reverts back to the default string each time the browser starts.
Switching the user agent back and forth is annoying, when I go to Gmail it thinks I'm on a phone :(
It's this one: [http://chrispederick.com/work/user-agent-switcher/](http://chrispederick.com/work/user-agent-switcher/) 


Thanks for replying

---

### Post by matt_symes on 2015-06-28
Hi

if switching the user agent string works for you then what I would do is create a new Firefox profile.

In that profile I would add the Firefox about:config string general.useragent.override to change the useragent string for that new profile. You'll want to google general.useragent.override to see how to add it as it is not there by default.

You can then start Firefox using

```
firefox -ProfileManager --no-remote
```

from the terminal and picking your new profile.

After you have it working the edit the Firefox launcher icon as above.

I can't really help you more at the moment as I'm using my phone to type this and am afk and so these instructions are from memory.

BTW I use multiple Firefox profiles myself and the Ubuntu forums has its own profile.

Kind regards

---

### Post by coldraven on 2015-06-28
> **matt_symes said:**
> Hi

if switching the user agent string works for you then what I would do is create a new Firefox profile.

In that profile I would add the Firefox about:config string general.useragent.override to change the useragent string for that new profile. You'll want to google general.useragent.override to see how to add it as it is not there by default.

You can then start Firefox using

```
firefox -ProfileManager --no-remote
```

from the terminal and picking your new profile.

After you have it working the edit the Firefox launcher icon as above.

I can't really help you more at the moment as I'm using my phone to type this and am afk and so these instructions are from memory.

BTW I use multiple Firefox profiles myself and the Ubuntu forums has its own profile.

Kind regards

Thanks, it's too late at night for me to do anything but I shall look at it afresh tomorrow.

---

### Post by night_sky2 on 2015-06-28
Well, it's kinda hard to do without flash completely on the desktop, especially if you have needs beyond Youtube, Dailymotion or Vimeo.

I am not a Google Chrome user either.
 What I did to get the latest pepperflash working in Firefox is to install the Fresh Player Plugin + pepperflashplugin-nonfree (package)
See: [http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html](http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html)

If you are worried about Adobe's security flaws then you can set the plugin to ''Ask To Activate'' or use the Flashblock addon.
You'll then be able to activate Flash only in places that are absolutely necessery.

(For the record I use NoScript which is an awesome security tool and can manage Flash contents)

---

### Post by monkeybrain20122 on 2015-06-28
You may try mpv + youtube-dl According to this, youtube-dl supports "bbc.co.uk: BBC iPlayer" [https://rg3.github.io/youtube-dl/supportedsites.html](https://rg3.github.io/youtube-dl/supportedsites.html)

There is a Firefox addon [https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/)

After installing the mpv addon you will see a mpv button on Firefox's menu bar. Nivagate to the video's page and click the button and a mpv window will open to play the video if youtube-dl works for the site. The mpv interface is kind of sparse, to control volume press 0 for increase, 9 for decrease. It may take a bit longer for the window to appear depending on the site, so to test that your installation is working you should go to sites that are known to work first (e.g Youtube, vimeo, dailymotion, ted tv etc)

To use the Firefox addon you need to install up to date mpv and youtube-dl in your system (don't get them from the repo!) You can get youtube-dl from [https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8](https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8) and mpv from either [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media) (trusty) or [https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test1](https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test1) (vivid)

**Edited:** Just tested. It works on [http://www.bbc.co.uk/programmes/p0255v2n](http://www.bbc.co.uk/programmes/p0255v2n) but not [http://www.bbc.co.uk/news/world-europe-33305019](http://www.bbc.co.uk/news/world-europe-33305019)
The first clip is not regionally restricted, but the actual programs on the site are, so I can't really test them since I am outside of the UK.

---

### Post by monkeybrain20122 on 2015-06-28
Alternately you can install Firefox nightly from a ppa and set the user agent string permanently. I think it can coexist with regular Firefox.

---

### Post by matt_symes on 2015-06-29
Hi

Well there's a whole bunch of solutions for you and it would not surprise me if more followed.

I have to agree with with night_sky2 though. How are you going to browse the web without Flash ? 

I'm no fan of Flash but I understand that, at the moment, it's still required for a good browsing experience.

It's easy to block Flash and only run Flash movies when you need them.

Kind regards

---

### Post by monkeybrain20122 on 2015-06-29
> **matt_symes said:**
> Hi

Well there's a whole bunch of solutions for you and it would not surprise me if more followed.

I have to agree with with night_sky2 though. How are you going to browse the web without Flash ? 

I'm no fan of Flash but I understand that, at the moment, it's still required for a good browsing experience.

It's easy to block Flash and only run Flash movies when you need them.

Kind regards

Actually, mpv+youtube-dl works for a lot of sites (even sites which are not explicitly supported) so if you just want to watch movies you can go very far without flash (there are problems when there are multiple flash videos on the same page, it will just play the first one) I have not been using flash for quite some times even though I have it (with freshplayer plugin)

freshplayer plugin is a good way to use up to date flash on Firefox but OP doesn't want flash at all. Also I think it is better to compile freshplayer (which is rather easy) than using webupd8's ppa. Since version 0.30 it is kind of buggy because of support for vaapi and vdpau decoding and one needs to set some compiling options to fix video freezing (at least on my machines) and still use hardware decoding.I don't know how webupd8 compiles freshplayer but june 1's version (0.24) is the last  perfectly working version from the ppa. All later updates have some problems. So I am compiling from source now (works fine if compile with the proper parameters)

---

### Post by matt_symes on 2015-06-29
Hi

> **monkeybrain20122 said:**
> Actually, mpv+youtube-dl works for a lot of sites (even sites which are not explicitly supported) so if you just want to watch movies you can go very far without flash (there are problems when there are multiple flash videos on the same page, it will just play the first one) I have not been using flash for quite some times even though I have it (with freshplayer plugin)

freshplayer plugin is a good way to use up to date flash on Firefox but OP doesn't want flash at all. Also I think it is better to compile freshplayer (which is rather easy) than using webupd8's ppa. Since version 0.30 it is kind of buggy because of support for vaapi and vdpau decoding and one needs to set some compiling options to fix video freezing (at least on my machines) and still use hardware decoding.I don't know how webupd8 compiles freshplayer but june 1's version (0.24) is the last  perfectly working version from the ppa. All later updates have some problems. So I am compiling from source now (works fine if compile with the proper parameters)

I agree with all everything you say although I have had no problems with the PPA so far.

I've used mplayer2 and youtube-dl for ages to view content from the terminal.

I do prefer to keep all my options open though and that is why I do have Flash.

Thanks for your post though as I'll take a look at mpv again as a replacement for mplayer.

If the OP doesn't want Flash then he has other options.

Kind regards

---

### Post by night_sky2 on 2015-06-29
> **monkeybrain20122 said:**
> freshplayer plugin is a good way to use up to date flash on Firefox but OP doesn't want flash at all.

True but as I understand it, the OP doesn't want flash *because *of security concerns.

By setting the plugin to ''Ask To Activate'', and only allowing flash contents on website he trusts, it greatly reduces any risks of malicious attack.

It seems to me that this would solve all of his flash issues instead of trying to find endless workarounds.

---

### Post by night_sky2 on 2015-06-29
> **monkeybrain20122 said:**
> Also I think it is better to compile  freshplayer (which is rather easy) than using webupd8's ppa. Since  version 0.30 it is kind of buggy because of support for vaapi and vdpau  decoding and one needs to set some compiling options to fix video  freezing (at least on my machines) and still use hardware decoding.I  don't know how webupd8 compiles freshplayer but june 1's version (0.24)  is the last  perfectly working version from the ppa. All later updates  have some problems. So I am compiling from source now (works fine if  compile with the proper parameters)

I use the webupd8 ppa and I have not experienced any trouble with it. It delivers my updates regularly in the Update Manager so that's very convenient.

But the Fresh Player Plugin is still very much a work in progress. And since the dev doesn't have access to Adobe's source code, it's a trial and error kind of thing.

 One may experience some possible glitches from time to time but overall it's stable (at least to me).

---

### Post by monkeybrain20122 on 2015-06-29
> **night_sky2 said:**
> I use the webupd8 ppa and I have not experienced any trouble with it. It delivers my updates regularly in the Update Manager so that's very convenient.
.

Maybe you don't have hardware decoding enabled (it has to be enabled in the .conf file even if compiled with hardware decoding support). It seems that all the latest problems are related to that, if disable hardware decoding in config file then all the problems disappear. 

But I want hardware decoding. On the hp netbook with amd card (using open driver) using vdpau cuts down cpu usage for 720 p from ~ 130% to around 30%, it is as good as the old trick to get flash 11.2 to use vdpau by messing with adobe's config file but it works everywhere instead of just Youtube like 11.2. On another Intel machine I have similar spectacular reduction on cpu usage using vaapi. Not as good as using mpv but still very nice.

---

### Post by speedwell68 on 2015-06-30
Why not just take your iPlayer usage out of the browser totally and use Kodi (aka XBMC) with one of the various BBC iPlayer addons that are available.  Or simply use the get_iplayer command line utility, if you don't like the command line there is a GUI frontend for it called GiPlayer, and download the MP4 files.

---

### Post by coldraven on 2015-06-30
> **monkeybrain20122 said:**
> You may try mpv + youtube-dl According to this, youtube-dl supports "bbc.co.uk: BBC iPlayer" [https://rg3.github.io/youtube-dl/supportedsites.html](https://rg3.github.io/youtube-dl/supportedsites.html)

There is a Firefox addon [https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/)

After installing the mpv addon you will see a mpv button on Firefox's menu bar. Nivagate to the video's page and click the button and a mpv window will open to play the video if youtube-dl works for the site. The mpv interface is kind of sparse, to control volume press 0 for increase, 9 for decrease. It may take a bit longer for the window to appear depending on the site, so to test that your installation is working you should go to sites that are known to work first (e.g Youtube, vimeo, dailymotion, ted tv etc)

To use the Firefox addon you need to install up to date mpv and youtube-dl in your system (don't get them from the repo!) You can get youtube-dl from [https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8](https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8) and mpv from either [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media) (trusty) or [https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test1](https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test1) (vivid)

**Edited:** Just tested. It works on [http://www.bbc.co.uk/programmes/p0255v2n](http://www.bbc.co.uk/programmes/p0255v2n) but not [http://www.bbc.co.uk/news/world-europe-33305019](http://www.bbc.co.uk/news/world-europe-33305019)
The first clip is not regionally restricted, but the actual programs on the site are, so I can't really test them since I am outside of the UK.

Sorry about the delay in replying, I've been distracted elsewhere.
I've done what you suggested above and sure enough I can watch the BBC iPlayer with mpv. However is does not work on their news front page for example here: [http://www.bbc.co.uk/news/world-africa-33318068](http://www.bbc.co.uk/news/world-africa-33318068). I might try the FreshPlayer method later today and I'll post back the results.
Many thanks to all who made suggestions.

---

### Post by buzzingrobot on 2015-06-30
The only time the BBC news site tells me to install Flash is when I do not have Flash installed and click on a a Flash link (typically, it's that black rectangle that the browser displays in lieu of a still image isn't available).

Whatever you use to view videos, the BBC site will know and log it.  Any responsible site would to understand its users. 

Given that, if you want to watch *Flash* videos, why not just install Flash and set it to "Ask to Activate"?

Canonical pushes out Flash updates released by Adobe very quickly, usually the same day in my experience. 

You can turn off much of the phoning home in Chrome via its settings.

If it's only a matter of BBC video, I'd install Flash and move on.  It's not like bbc.com is an amateurish operation.

---

### Post by coldraven on 2015-06-30
> **buzzingrobot said:**
> The only time the BBC news site tells me to install Flash is when I do not have Flash installed and click on a a Flash link (typically, it's that black rectangle that the browser displays in lieu of a still image isn't available).

Whatever you use to view videos, the BBC site will know and log it.  Any responsible site would to understand its users. 

Given that, if you want to watch *Flash* videos, why not just install Flash and set it to "Ask to Activate"?

Canonical pushes out Flash updates released by Adobe very quickly, usually the same day in my experience. 

You can turn off much of the phoning home in Chrome via its settings.

If it's only a matter of BBC video, I'd install Flash and move on.  It's not like bbc.com is an amateurish operation.
They might not be able to log me as I have Ghostery blocking trackers.
On their front page there are three:
Scorecard Research
ChartBeat
Soasta mpulse

But yes you're right, I will install the Pepper Flash when I get the time.

---

### Post by buzzingrobot on 2015-06-30
At a minimum, they know your IP. Every site does.

---

### Post by monkeybrain20122 on 2015-06-30
> **coldraven said:**
> 

But yes you're right, I will install the Pepper Flash when I get the time.

Actually I don't think you need pepper flash for the BBC, 11.2 should work. As far as the BBC is concerned I think the only advantage of freshplayer is hardware decoding, but at the moment it is glitchy and it may or may not work depending on your hardware. If it works it is pretty sweet.

---

