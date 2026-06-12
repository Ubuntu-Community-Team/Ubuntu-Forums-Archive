---
title: "Adobe releases its fourth security update to Flash in less than a month"
date: 2015-02-06
forum: Ubuntu, Linux and OS Chat
---

### Post by SeijiSensei on 2015-02-06
Since January 15th Adobe has rushed out **four** security updates for Flash.  Today's fixed a "zero-day" vulnerability that permitted "drive-by" infections.  I've now taken to using "Ask to Activate" as my default policy for Flash in Firefox so I can pick and choose where and when I want to view a Flash object.  I've turned off Flash for YouTube since they have now implemented HTML5 everywhere, but I still need it for other sites that haven't moved along yet.  At least with "Ask to Activate" you can decide whether to put yourself at risk on a case-by-case basis.

If you haven't yet updated Flash today, please run "sudo apt-get install flashplugin-installer" as soon as possible.

---

### Post by monkeybrain20122 on 2015-02-06
I have always set flash to ask to activate. mpv now has built in youtube-dl support which allows streaming on many sites without flash (see youtube-dl's long list of support sites) Now you can even use it with smplayer. e.g cnn

Youtube does implement html5 everywhere except for the 3d videos. Most hardware doesn't support html5-3d (I think you need a Nvidia card) but many people probably don't use/know about it anyway. But on Youtube there have always been many non flash options such as Viewtube (also works on a few other popular sites), standalone players such as smtube and minitube all of which perform better than flash (and html5) for weaker hardware. So while Youtube accounts for a lot of flash questions, it is the least one should worry about even if flash on Linux dies now.

---

### Post by SeijiSensei on 2015-02-06
I'm running the beta version of Firefox (v 36.0) which enables HTML5 from YouTube with the licensed H.264 decoder generously provided by Cisco.  It's available by installing the official "Mozilla Team" PPA at [https://launchpad.net/~mozillateam/+archive/ubuntu/firefox-next](https://launchpad.net/~mozillateam/+archive/ubuntu/firefox-next).

---

### Post by Erik1984 on 2015-02-06
Thanks for the Firefox tip.

---

### Post by monkeybrain20122 on 2015-02-06
The cisco h264 decoder is Firefox stable too, has been there at least since FF34 or perhaps before (now stable release is FF 35) No mozilla ppa, just stock Ubuntu offer.

---

### Post by SeijiSensei on 2015-02-06
Does the H.264 decoder come packaged with Firefox by default on 14.04?  I don't recall it being installed when I updated my browser from the ordinary repositories, but it was installed automatically alongside the beta.

---

### Post by monkeybrain20122 on 2015-02-06
> **SeijiSensei said:**
> Does the H.264 decoder come packaged with Firefox by default on 14.04?  I don't recall it being installed when I updated my browser from the ordinary repositories, but it was installed automatically alongside the beta.

Yeah, you just need to  do regular updates. Running 14.04 and ff35 here.

---

### Post by Mike_Walsh on 2015-02-07
Same here. FireFox 35 and 14.04; H.264's been there for a coupla releases now. Also got it in FireFox 35 in Puppy Linux, too. Haven't tried it, though; I'm not a big fan of YouTube (except for when I HAVE to use it).....

In Puppy, you simply go to Help (on the menu bar) and click on 'About'; it then updates from the 'About' window.

[ATTACH=CONFIG]259808[/ATTACH]

I've **always **had Flash in Linux set for 'Ask to activate'; wouldn't have it any other way, whether FF OR Chrome/Chromium.


Regards,

Mike.

---

### Post by sammiev on 2015-02-07
> **Mike_Walsh said:**
> Same here. FireFox 35 and 14.04; H.264's been there for a coupla releases now. Also got it in FireFox 35 in Puppy Linux, too. Haven't tried it, though; I'm not a big fan of YouTube (except for when I HAVE to use it).....

In Puppy, you simply go to Help (on the menu bar) and click on 'About'; it then updates from the 'About' window.

[ATTACH=CONFIG]259808[/ATTACH]


Regards,

Mike.

LOL in 15.04 we are still on FF34 unless you manually install FF35 or on.

---

### Post by Mike_Walsh on 2015-02-07
Well, I would assume that counts as a manual update, the way I do it in Puppy. I'm using the most recent distro, 'Tahrpup' 6,0 (based on Trusty, and only released back at the end of October), and the version supplied as standard is FF32. I came across the update mechanism quite by chance, since I, too, have been used to getting the regular updates through the normal channels in 14.04. I looked in the 'About' window when I was looking for some other information.....and as soon as you open it, it says 'checking for updates', then 'installing', followed by 'Please restart Firefox to use the updated version'; and, lo and behold, 32.1.27 (I think it was), suddenly became 35.01.

I'm QUITE happy with that, since many 'flavours' of Puppy (of which there are **scores**) are using some distinctly old versions. 'Slacko' 5.7.1, for instance, is still using FF17 (!), although it IS the ESR version ( the Extended Support Release)., with the old, pre-Australis interface.....which I have to confess to quite liking, actually! It **still** gets updates, too...


Regards,

Mike.

---

### Post by bashiergui on 2015-02-08
> **SeijiSensei said:**
> Since January 15th Adobe has rushed out four security updates for Flash.  Today's fixed a "zero-day" vulnerability that permitted "drive-by" infections.  I've now taken to using "Ask to Activate" as my default policy for Flash in Firefox so I can pick and choose where and when I want to view a Flash object.  I've turned off Flash for YouTube since they have now implemented HTML5 everywhere, but I still need it for other sites that haven't moved along yet.  At least with "Ask to Activate" you can decide whether to put yourself at risk on a case-by-case basis.

If you haven't yet updated Flash today, please run "sudo apt-get install flashplugin-installer" as soon as possible.Excellent advice.

To provide some perspective, these Adobe vulnerabilities have been getting exploited on the internet since December.  The exploit has been widely delivered using advertising networks on popular websites. They have been (as usual) targeting firefox and IE users on Windows. No known exploits have been seen against Mac or Linux. However, that doesn't mean they won't develop some.

Source on the exploits seen in the wild [http://arstechnica.com/security/2015/02/as-flash-0day-exploits-reach-new-level-of-meanness-what-are-users-to-do/](http://arstechnica.com/security/2015/02/as-flash-0day-exploits-reach-new-level-of-meanness-what-are-users-to-do/)

Patch Adobe ASAP. An ad blocker would also be beneficial.

---

### Post by Tar_Ni on 2015-02-08
Well that's good thing they are fixing them, at least it means they are doing their job. Quite clearly flash 11.2 is on life support, so that is to be expected. The sooner Mozilla can get rid of this darn plugin, the better.

I keep the Adobe plugin activated by default, for convenience with Adblock Edge+fanboy Ultimate list enabled to avoid Malvertising threats. But how can I add exclusions, such as Youtube or Dailymotion? I would like the use the HTML5 on those sites but when I set shockwave on ''ask to active'' in Firefox and block the Youtube request, I only get a grey screen where the video should be with an ''Activate Flash''. The HTML5 player doesn't work.

---

### Post by Erik1984 on 2015-02-08
[https://www.youtube.com/html5](https://www.youtube.com/html5)

---

### Post by Tar_Ni on 2015-02-08
> **Erik1984 said:**
> [https://www.youtube.com/html5](https://www.youtube.com/html5)

I was aware of that but I need to activate it each and every time by going to this link since I delete my cookies when exiting the browser.. No way will I allow Google to track me. So that is very inconvenient. Even when disabling the Adobe plugin, Youtube detect it's presence and ask me to manage my plugins... Unless I am mistaken, it seems the only way to make the HTML5 show up by default without having a tracking cookie planted in my computer is to remove the flash plugin altogether.

---

### Post by monkeybrain20122 on 2015-02-08
@Tar_Ni

You can use Viewtube and gecko-mediamplayer (or just totem's plugins, though not as good so I disabled them all and use gecko instead) on Youtube and dailymotion without flash at all. Install gecko-mediaplayer from repo. Install the greasemonkey addon, then restart firefox and install Viewtube [http://isebaro.com/viewtube/?ln=en](http://isebaro.com/viewtube/?ln=en)

Performance is much better than flash anyway especially if your machine is a bit slow but can use vdpau for hardware acceleration (Nvidia card with proprietary driver, a not so old amd card with open driver,--not sure about catalyst, or a not so old Intel card with libvdpau-va-gl1 either from a ppa or compile, the repo version is broken)

Also, if you simply disable flash both Youtube and dailymotion default to html5 (also other sites like Ted and Soundcloud)

> [COLOR=#000000]Even when disabling the Adobe plugin, Youtube detect it's presence and ask me to manage my plugins...[/COLOR]

You need to restart Firefox.

**Edited:** I found out recently that I can watch video streams from a lot of sites without flash using mpv (or mpv + Smplayer if you like a cool front end) thanks to its integration with youtube-dl  [http://blog.smplayer.info/](http://blog.smplayer.info/)  see How to play 1080p Video on Youtube..  If you set the option to [COLOR=#373737][FONT=Courier 10 Pitch]--ytdl-format=best,bestvideo+bestaudio instead of [/FONT][/COLOR][COLOR=#373737][FONT=Courier 10 Pitch]--ytdl-format=bestvideo+bestaudio you can stream from a long list of sites supported by youtube-dl always getting the best quality stream available and also getting 1080p if available on Youtube, if just best then best quality on other sites and 720p on Youtube (you can also use this option with plain mpv on the terminal)

list of sites supported [/FONT][/COLOR][http://rg3.github.io/youtube-dl/supportedsites.html](http://rg3.github.io/youtube-dl/supportedsites.html)[COLOR=#373737][FONT=Courier 10 Pitch]

For this you need 
a recent build of mpv [/FONT][/COLOR][https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)
Smplayer [https://launchpad.net/~rvm/+archive/ubuntu/ppa](https://launchpad.net/~rvm/+archive/ubuntu/ppa) (First one has smplayer too but a bit older than the latest, the feature to use vaapi for hardware decoding is missing in that version) 
up to date youtube-dl [https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8/+index?batch=75&direction=backwards&start=450](https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8/+index?batch=75&direction=backwards&start=450)

---

### Post by monkeybrain20122 on 2015-02-08
Related [https://www.eff.org/deeplinks/2015/01/new-drm-boss-same-old-boss](https://www.eff.org/deeplinks/2015/01/new-drm-boss-same-old-boss)

Good news. Flash's demise is one step closer.
Bad news. The open web is still not going to happen.
Worst news. Adobe still holds the key.

---

### Post by bashiergui on 2015-02-08
Meh. As soon as flash is replaced with HTML5 or anything else, that new thing will get attacked.

---

### Post by Erik1984 on 2015-02-08
> **Tar_Ni said:**
> I was aware of that but I need to activate it each and every time by going to this link since I delete my cookies when exiting the browser.. **No way will I allow Google to track me.** So that is very inconvenient. Even when disabling the Adobe plugin, Youtube detect it's presence and ask me to manage my plugins... Unless I am mistaken, it seems the only way to make the HTML5 show up by default without having a tracking cookie planted in my computer is to remove the flash plugin altogether.

In that case it may be better to not visit YouTube at all.

---

### Post by Tar_Ni on 2015-02-09
Thanks monkeybrain for these tips. But if Google is ditching  flash for Youtube and will soon default ot HTML5 than I suppose that solves my problem.  Dailymotion and Vimeo will probably follow suit as well as both feature an HMTL5 player when flash can't be detected. In the meantime, I  keep flash 11.2 for streaming services lagging behind, and it still  works for the vast majority of website. I might also try the Fresh  Player Plugin at some point too.

> **Erik1984 said:**
> In that case it may be better to not visit YouTube at all.

Why? I like Youtube, that's where the cool stuff is when it comes to video. I am fully aware that Google is recording everything I do on their streaming website, but once I exit Youtube, what I am doing is none of their business. The tracking stops there. ;)

---

### Post by Mike_Walsh on 2015-02-09
> **Erik1984 said:**
> In that case it may be better to not visit YouTube at all.

^^^ +1...!!


Regards,

Mike.

---

### Post by monkeybrain20122 on 2015-02-09
> **Tar_Ni said:**
> Thanks monkeybrain for these tips. But if Google is ditching  flash for Youtube and will soon default ot HTML5 than I suppose that solves my problem.  Dailymotion and Vimeo will probably follow suit as well as both feature an HMTL5 player when flash can't be detected. In the meantime, I  keep flash 11.2 for streaming services lagging behind, and it still  works for the vast majority of website. I might also try the Fresh  Player Plugin at some point too.


Vimeo has defaulted to html5 for quite a while. I am not even sure if flash works any more. I have flash set to 'ask to activate', but vimeo never asks, just plays videos in html5. But on my netbook I still prefer viewtube to html5, much smoother and can use hardware decoding.

---

### Post by monkeybrain20122 on 2015-02-09
> **Tar_Ni said:**
> 
Why? I like Youtube, that's where the cool stuff is when it comes to video. I am fully aware that Google is recording everything I do on their streaming website, but once I exit Youtube, what I am doing is none of their business. The tracking stops there. ;)

If you are so paranoid use a standalone Youtube viewer such as smtube or minitube. You don't need to open a web browser at all. ;) Get the latest version from ppa or developer's site(minitube), the repo versions are so outdated that they don't work any more.

---

### Post by monkeybrain20122 on 2015-02-09
> **Mike_Walsh said:**
> Well, I would assume that counts as a manual update, the way I do it in Puppy. I'm using the most recent distro, 'Tahrpup' 6,0 (based on Trusty, and only released back at the end of October), and the version supplied as standard is FF32. I came across the update mechanism quite by chance, since I, too, have been used to getting the regular updates through the normal channels in 14.04. I looked in the 'About' window when I was looking for some other information.....and as soon as you open it, it says 'checking for updates', then 'installing', followed by 'Please restart Firefox to use the updated version'; and, lo and behold, 32.1.27 (I think it was), suddenly became 35.01.
.

I think it depends on how you install firefox in puppy (puppy comes with a striped version of Firefox called something moon :)). One way through repo (same as Ubuntu's I think) and the other way click "install firefox" in the menu or pet store something, which I think basically installs from Mozilla. In the second case update by clicking about Firefox. 

Played with puppy for a few days. Audio didn't work so that was it. :)

---

