---
title: "Chromium Browser? Any Personal Insights?"
date: 2014-11-09
forum: Ubuntu, Linux and OS Chat
---

### Post by Daveski17 on 2014-11-09
I was wondering what experiences, good or bad, anyone has had with the Chromium browser. I've never used it, although I have used Chrome. Chromium is in the Ubuntu Software Centre and I was considering it as a back-up browser. 

So, what are the ups and downs with using it as a browser?

Thanks, Dave.

---

### Post by pfeiffep on 2014-11-09
I've been using Chromium on Linux for a couple of years and use FireFox as a backup. There are a few extra steps using Chromium - like installing Pepperflash - but I really don't think there's a major difference. 
Chromium is updated with software updater - my current version 37

---

### Post by Daveski17 on 2014-11-09
> **pfeiffep said:**
> I've been using Chromium on Linux for a couple of years and use FireFox as a backup. There are a few extra steps using Chromium - like installing Pepperflash - but I really don't think there's a major difference. 
Chromium is updated with software updater - my current version 37

OK thanks for the reply. I was wondering about the flash plug-in. Can Chromium be synched with Google like Chrome can?

---

### Post by vasa1 on 2014-11-09
Users of Chromium 37 need to be aware that it hasn't been updated for more than a month after Google Chrome has been updated to v38 with 159 security fixes (one of which deserved a prize payout of $27,633.70). 

This is not the first time Chromium hasn't been updated in a timely fashion vis-à-vis Google Chrome. Of course, Chromium is in "Universe", meaning that the responsibility to keep it updated lies with the "community" and not with Canonical.

I'd rather use a browser I know is updated promptly. I trust Firefox and Google Chrome.

---

### Post by Daveski17 on 2014-11-09
> **vasa1 said:**
> Users of Chromium 37 need to be aware that it hasn't been updated for more than a month after Google Chrome has been updated to v38 with 159 security fixes (one of which deserved a prize payout of $27,633.70). 

This is not the first time Chromium hasn't been updated in a timely fashion vis-à-vis Google Chrome. Of course, Chromium is in "Universe", meaning that the responsibility to keep it updated lies with the "community" and not with Canonical.

I'd rather use a browser I know is updated promptly. I trust Firefox and Google Chrome.

OK, thanks. I was only thinking of it as a back-up anyway.

---

### Post by JDorfler on 2014-11-09
Chromium/Chrome is "meh" in my opinion.  Certain things are nice, but for more control I prefer Firefox.

---

### Post by Tar_Ni on 2014-11-09
I used to be a Chromium user on Linux but I have been disappointed by the maintenance for updates and an annoying bug ( where pepperflash is recognized as flash 11.2) so I decided to ditch it. Since I don't trust Google Chrome with my data I've come back to Firefox as my main browser.

You might want to consider SRWare Iron too, I think it can make a perfect back up browser.

[http://www.srware.net/en/software_srware_iron.php](http://www.srware.net/en/software_srware_iron.php)

---

### Post by Daveski17 on 2014-11-09
> **JDorfler said:**
> Chromium/Chrome is "meh" in my opinion.  Certain things are nice, but for more control I prefer Firefox.

Yeah, Firefox has better and safer extensions as well. It works beautifully for me on Ubuntu. A back-up browser is always handy though.

---

### Post by Daveski17 on 2014-11-09
> **Tar_Ni said:**
> I used to be a Chromium user on Linux but I have been disappointed by the maintenance for updates and an annoying bug ( where pepperflash is recognized as flash 11.2) so I decided to ditch it. Since I don't trust Google Chrome with my data I've come back to Firefox as my main browser.

You might want to consider SRWare Iron too, I think it can make a perfect back up browser.

[http://www.srware.net/en/software_srware_iron.php](http://www.srware.net/en/software_srware_iron.php)

I used SRWare Iron before I ever used Chrome! It could be a bit buggy at times though. Still, it's a good alternative.

---

### Post by WinEunuchs2Unix on 2014-11-09
Not being very technical I find chromium about the same as chrome.  I like chrome for syncing my bookmarks between linux and windows, plus this machine and the other laptop as long as chrome or chromium is being used.  I hate the scrolling in chrome so I've revereted back to firefox for web browsing from time to time.

Firefox doesn't work for full screen flash player on the TV monitor so I load google just for that each time.

Chrome handles wide scale system zooming in windows and linux nicely-- you have to do this for old eyes on a 1920x1080 laptop.

Again being non-technical chrome and chromium are pretty much interchangeable words.

---

### Post by Daveski17 on 2014-11-09
> **WinEunuchs2Unix said:**
> Not being very technical I find chromium about the same as chrome.  I like chrome for syncing my bookmarks between linux and windows, plus this machine and the other laptop as long as chrome or chromium is being used.  I hate the scrolling in chrome so I've revereted back to firefox for web browsing from time to time.

Firefox doesn't work for full screen flash player on the TV monitor so I load google just for that each time.

Chrome handles wide scale system zooming in windows and linux nicely-- you have to do this for old eyes on a 1920x1080 laptop.

Again being non-technical chrome and chromium are pretty much interchangeable words.

I'm quite interested in the actual differences between Chromium and Chrome. Ostensibly the same, but Chromium is open source. Interesting.

---

### Post by craig10x on 2014-11-09
The main advantages of Chrome over Chromium is: 1) Pepperflash is already on there (no need to install)  2) Built in PDF Reader that is really neat  3) It puts a PPA in your software center so that as soon as the latest version is released, you get it immediately (no waiting)...With Chromium (version wise) you always lag behind...

---

### Post by Daveski17 on 2014-11-09
> **craig10x said:**
> The main advantages of Chrome over Chromium is: 1) Pepperflash is already on there (no need to install)  2) Built in PDF Reader that is really neat  3) It puts a PPA in your software center so that as soon as the latest version is released, you get it immediately (no waiting)...With Chromium (version wise) you always lag behind...

OK, thanks. So, no real advantages with Chromium then?

---

### Post by vasa1 on 2014-11-09
> **Daveski17 said:**
> ... but Chromium is open source. Interesting.
And then, at least in the near future, we install the "non open source" pepper flash. That makes me smile.

Re. a backup browser, it would depend on how or for what specific purpose it is to be used. I have Seamonkey (purely for its html editor) and Xombrero which is a mean little webkit browser with a tiny footprint. Those who already have qt/kde stuff on their machine may not mind trying out Qupzilla (It uses DDG as its search engine). You can find what additional software will be pulled in **on your system** by running *apt-get install -s qupzilla*. The **-s** makes sure it's a dry run and doesn't need sudo. If you want to be frugal, try *apt-get install --no-install-recommends -s qupzilla* first. If things seem incomplete, you can always go back and do a complete install.

There are quite a few internet resources on Qupzilla but you'll get an executive summary with *apt-cache show qupzilla*.

---

### Post by craig10x on 2014-11-09
@Daveski17: I really can't see any particular advantage of using Chromium over Chrome...it's kind of Chrome with parts missing from it (lol) ;)
Why take a stripped down car when you can have it with some nice extra features for the same price? :mrgreen:

---

### Post by bcschmerker on 2014-11-10
Thanks for an opportunity to add an insight.  With Ubuntu® 12.04.5-LTS, I use Mozilla® Firefox® (packages: firefox, firefox-dbg, firefox-globalmenu, adobe-flashplugin, &c.) for most Web services not requiring a current Adobe® Flash Player®, but have been testing Chromium&#8482; (package: chromium-browser) with a PPA'd Adobe® Flash Player® for Google® Pepper&#8482; API (PPA:skunk/pepperflash) on Google® Services (primarily Google+® and YouTube&#8482;) and SingSnap®.  The few issues I've run across, notwithstanding recent hardware problems at my end, are due to loss of sync between the Ubuntu® Universe Repository (updates to chromium-browser) and updates to Google® Chrome&#8482; through the skunk PPA at Launchpad&#8482;.

Chromium&#8482; is supported with Extensions at the Google® Chrome Store®; one Extension that I can recommend is ScriptSafe&#8482;, a counterpart of InformAction® NoScript&#8482; with certain differences in function.  Be advised that ScriptSafe is somewhat stricter than NoScript in terms of server permissions for Javascript and plug-ins.

(Note:  Adobe® Flash Player® for Google® Pepper&#8482; API (package: pepperflashplugin-nonfree) is directly supported in the Ubuntu® Multiverse Repositories for 14.04.1-LTS and newer releases.)

---

### Post by help_me2 on 2014-11-10
> **bcschmerker said:**
> Thanks for an opportunity to add an insight.  With Ubuntu® 12.04.5-LTS, I use Mozilla® Firefox® (packages: firefox, firefox-dbg, firefox-globalmenu, adobe-flashplugin, &c.) for most Web services not requiring a current Adobe® Flash Player®, but have been testing Chromium&#8482; (package: chromium-browser) with a PPA'd Adobe® Flash Player® for Google® Pepper&#8482; API (PPA:skunk/pepperflash) on Google® Services (primarily Google+® and YouTube&#8482;) and SingSnap®.  The few issues I've run across, notwithstanding recent hardware problems at my end, are due to loss of sync between the Ubuntu® Universe Repository (updates to chromium-browser) and updates to Google® Chrome&#8482; through the skunk PPA at Launchpad&#8482;.

Chromium&#8482; is supported with Extensions at the Google® Chrome Store®; one Extension that I can recommend is ScriptSafe&#8482;, a counterpart of InformAction® NoScript&#8482; with certain differences in function.  Be advised that ScriptSafe is somewhat stricter than NoScript in terms of server permissions for Javascript and plug-ins.

(Note:  Adobe® Flash Player® for Google® Pepper&#8482; API (package: pepperflashplugin-nonfree) is directly supported in the Ubuntu® Multiverse Repositories for 14.04.1-LTS and newer releases.)

Ummm, putting all those trademark and copyright symbols doesn't do anything to enhance your post. (they're actually annoying) You're free to discuss any product or company without fear of getting sued. I always wondered why people did that.

---

### Post by help_me2 on 2014-11-10
> **craig10x said:**
> @Daveski17: I really can't see any particular advantage of using Chromium over Chrome...it's kind of Chrome with parts missing from it (lol) ;)
Why take a stripped down car when you can have it with some nice extra features for the same price? :mrgreen:
I agree. Chromium is too stripped down for my needs. I enjoy media and flash. I'm sorry, but I refuse to go back to the days when I had to install flash manually. It just works, so I use Chrome.

---

### Post by vasa1 on 2014-11-10
> **help_me2 said:**
> Ummm, putting all those trademark and copyright symbols doesn't do anything to enhance your post. (they're actually annoying) You're free to discuss any product or company without fear of getting sued. I always wondered why people did that.+1. Just makes the post somewhat more difficult to read.

---

### Post by Daveski17 on 2014-11-10
> **vasa1 said:**
> And then, at least in the near future, we install the "non open source" pepper flash. That makes me smile.

Re. a backup browser, it would depend on how or for what specific purpose it is to be used. I have Seamonkey (purely for its html editor) and Xombrero which is a mean little webkit browser with a tiny footprint. Those who already have qt/kde stuff on their machine may not mind trying out Qupzilla (It uses DDG as its search engine). You can find what additional software will be pulled in **on your system** by running *apt-get install -s qupzilla*. The **-s** makes sure it's a dry run and doesn't need sudo. If you want to be frugal, try *apt-get install --no-install-recommends -s qupzilla* first. If things seem incomplete, you can always go back and do a complete install.

There are quite a few internet resources on Qupzilla but you'll get an executive summary with *apt-cache show qupzilla*.

Isn't Firefox open source but utilises Adobe flash (on Linux for now anyway)? I've used QupZilla on Windows but it broke one or two pages that I used regularly (including The Guardian newspaper and Photobucket). I also found its adblocker to be a tad sluggish updating. I liked it as a portable though and used it at work often. I used to use SeaMonkey quite a bit, although it isn't in the Software Centre. Sometimes downloaded Debian packages don't alway install well and I know next to nothing about Linux. I'm always wary of borking my system and having to reinstall Ubuntu, which can be done relatively quickly, my files are all backed up, but is annoying lol.

---

### Post by Daveski17 on 2014-11-10
> **bcschmerker said:**
> Thanks for an opportunity to add an insight.  With Ubuntu® 12.04.5-LTS, I use Mozilla® Firefox® (packages: firefox, firefox-dbg, firefox-globalmenu, adobe-flashplugin, &c.) for most Web services not requiring a current Adobe® Flash Player®, but have been testing Chromium™ (package: chromium-browser) with a PPA'd Adobe® Flash Player® for Google® Pepper™ API (PPA:skunk/pepperflash) on Google® Services (primarily Google+® and YouTube™) and SingSnap®.  The few issues I've run across, notwithstanding recent hardware problems at my end, are due to loss of sync between the Ubuntu® Universe Repository (updates to chromium-browser) and updates to Google® Chrome™ through the skunk PPA at Launchpad™.

Chromium™ is supported with Extensions at the Google® Chrome Store®; one Extension that I can recommend is ScriptSafe™, a counterpart of InformAction® NoScript™ with certain differences in function.  Be advised that ScriptSafe is somewhat stricter than NoScript in terms of server permissions for Javascript and plug-ins.

(Note:  Adobe® Flash Player® for Google® Pepper™ API (package: pepperflashplugin-nonfree) is directly supported in the Ubuntu® Multiverse Repositories for 14.04.1-LTS and newer releases.)

OK thanks for the insight.

---

### Post by Daveski17 on 2014-11-10
> **craig10x said:**
> @Daveski17: I really can't see any particular advantage of using Chromium over Chrome...it's kind of Chrome with parts missing from it (lol) ;)
Why take a stripped down car when you can have it with some nice extra features for the same price? :mrgreen:

Good point. I was intending it to be just a back-up if Firefox had any issues though.

---

### Post by vasa1 on 2014-11-10
> **Daveski17 said:**
> Isn't Firefox open source but utilises Adobe flash (on Linux for now anyway)? Absolutely. 
> **Daveski17 said:**
> I used to use SeaMonkey quite a bit, although it isn't in the Software Centre. ...There's a project called [Ubuntuzilla]("http://sourceforge.net/projects/ubuntuzilla/") which, sooner or later, has ppas of the latest stable Seamonkey build. And Ubuntuzilla has support at ubuntuforums.org [here]("http://ubuntuforums.org/forumdisplay.php?f=251").

---

### Post by Daveski17 on 2014-11-10
> **vasa1 said:**
> Absolutely. 
There's a project called [Ubuntuzilla]("http://sourceforge.net/projects/ubuntuzilla/") which, sooner or later, has ppas of the latest stable Seamonkey build. And Ubuntuzilla has support at ubuntuforums.org [here]("http://ubuntuforums.org/forumdisplay.php?f=251").

OK thanks for the info on Ubuntuzilla, it looks really useful.

---

### Post by Tar_Ni on 2014-11-10
> **craig10x said:**
> The main advantages of Chrome over Chromium is: 1) Pepperflash is already on there (no need to install)  2) Built in PDF Reader that is really neat  3) It puts a PPA in your software center so that as soon as the latest version is released, you get it immediately (no waiting)...With Chromium (version wise) you always lag behind...

The Chrome PDF reader has been open sourced early last summer, so Chromium, Iron and even now Opera has it as default. I would say the only 'advantage' of using Chrome over Chromium is to have the pepperflash plugin already installed and regular updates. chromium-browser does not have a particular schedule for updates, so on Ubuntu it is always days or sometimes weeks behind Google Chrome. I don't believe it is a critical point as a Linux system is less vulnerable than Windows for instance but if one sees that as an issue, I would suggest to use Iron instead, as the user can simply fetch the latest build on SWRIron's website when they are released.

Besides that there is really not much to be said, unless you are a die-hard Google user you will find Chrome more attractive for sure but if the idea is to avoid Google and it's awful trackrecord on privacy, then Chromium, Iron or Opera becomes much better options. I think they can now all use pepperflash, which can easily be installed in the Ubuntu software center. See: [https://wiki.ubuntu.com/Chromium/Getting-Flash](https://wiki.ubuntu.com/Chromium/Getting-Flash)

---

### Post by BazBear on 2014-11-10
Speaking of Firefox and it's older Flash player, you can install the Fresh Player plugin (instructions here [http://www.makeuseof.com/tag/how-to-get-chromes-latest-flash-player-to-work-in-firefox-on-linux/](http://www.makeuseof.com/tag/how-to-get-chromes-latest-flash-player-to-work-in-firefox-on-linux/)) that allows Firefox to use the latest Pepper Flash bundled with Chrome. Note that you need to have Chrome installed for it work, as Fresh Player is just a wrapper.

---

### Post by Tar_Ni on 2014-11-10
> **BazBear said:**
> Speaking of Firefox and it's older Flash player, you can install the Fresh Player plugin (instructions here [http://www.makeuseof.com/tag/how-to-get-chromes-latest-flash-player-to-work-in-firefox-on-linux/](http://www.makeuseof.com/tag/how-to-get-chromes-latest-flash-player-to-work-in-firefox-on-linux/)) that allows Firefox to use the latest Pepper Flash bundled with Chrome. Note that you need to have Chrome installed for it work, as Fresh Player is just a wrapper.

You're right but the Fresh Player Plugin is still of 'alpha' quality, so I personally wouldn't use it quite yet. But why do you need to install Chrome and not just the Pepperflash plugin from the Ubuntu Software Center?

Anyway, I still think that HTML5 is the way forward, and already websites like Youtube and Dailymotion can work without flash. We know that there is engineers like Till Schneidereit at Mozilla working on Shumway full time. It may only be a matter of time before Firefox can do, for a large part, without the Adobe plugin.

What he posted on twitter recently is encouraging: [https://twitter.com/tschneidereit/status/527276562035380224](https://twitter.com/tschneidereit/status/527276562035380224)

---

### Post by Daveski17 on 2014-11-10
> **BazBear said:**
> Speaking of Firefox and it's older Flash player, you can install the Fresh Player plugin (instructions here [http://www.makeuseof.com/tag/how-to-get-chromes-latest-flash-player-to-work-in-firefox-on-linux/](http://www.makeuseof.com/tag/how-to-get-chromes-latest-flash-player-to-work-in-firefox-on-linux/)) that allows Firefox to use the latest Pepper Flash bundled with Chrome. Note that you need to have Chrome installed for it work, as Fresh Player is just a wrapper.

OK, thanks for the info. :cool:

---

### Post by Daveski17 on 2014-11-10
> **Tar_Ni said:**
> It may only be a matter of time before Firefox can do, for a large part, without the Adobe plugin.

I think we are all looking forward to that time.

---

### Post by vasa1 on 2014-11-10
> **Daveski17 said:**
> ... Sometimes downloaded Debian packages don't alway install well and I know next to nothing about Linux. ...
I suppose that by "Debian packages" you mean .deb files from any source other than the Ubuntu software center (USC). If that is so, it is a legitimate concern. However, just like browser extensions, one could always do a little research into the background of the .deb package.

As you use Linux, you'll find a few examples of "external" .deb packages (or other archives) recommended instead of the versions available in the USC. VirtualBox is one such example. [ownCloud]("http://ubuntuforums.org/showthread.php?t=2249580") is another. Then there's the whole world of ppas.

Edit: And specific to *buntu flavors in version 14.10 only, the screen recording program, guvcview, is broken (on 64-bit systems, I think). People may use cheese from the USC or get a fixed version by installing a ppa maintained by a guvcview developer: [https://bugs.launchpad.net/ubuntu/+source/guvcview/+bug/1373221](https://bugs.launchpad.net/ubuntu/+source/guvcview/+bug/1373221)

---

### Post by vasa1 on 2014-11-11
Good news. Chromium has been updated```
chromium-browser:
  Installed: (none)
  Candidate: 38.0.2125.111-0ubuntu0.14.10.1.1103
  Version table:
     38.0.2125.111-0ubuntu0.14.10.1.1103 0
        500 http://archive.ubuntu.com/ubuntu/ utopic-updates/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu/ utopic-security/universe amd64 Packages
     37.0.2062.94-0ubuntu1~pkg1065 0
        500 http://archive.ubuntu.com/ubuntu/ utopic/universe amd64 Packages

```

---

### Post by SagaciousKJB on 2014-11-11
I haven't been happy with the performance of FireFox at all.  I'm much happy with Chromium so far but I haven't tried Flash yet.  I don't know what is up with FireFox lately, I remember last time I looked it was on like version 3 then all the sudden 30 some odd versions?  And it's huge, so bloated...

I've currently been searching for a replacement browser and I'm liking Chromium.

---

### Post by Daveski17 on 2014-11-11
> **vasa1 said:**
> I suppose that by "Debian packages" you mean .deb files from any source other than the Ubuntu software center (USC). If that is so, it is a legitimate concern. However, just like browser extensions, one could always do a little research into the background of the .deb package.

As you use Linux, you'll find a few examples of "external" .deb packages (or other archives) recommended instead of the versions available in the USC. VirtualBox is one such example. [ownCloud]("http://ubuntuforums.org/showthread.php?t=2249580") is another. Then there's the whole world of ppas.

Edit: And specific to *buntu flavors in version 14.10 only, the screen recording program, guvcview, is broken (on 64-bit systems, I think). People may use cheese from the USC or get a fixed version by installing a ppa maintained by a guvcview developer: [https://bugs.launchpad.net/ubuntu/+source/guvcview/+bug/1373221](https://bugs.launchpad.net/ubuntu/+source/guvcview/+bug/1373221)

Yeah, I think that's what I meant lol. In the past when I've installed external .deb packages (like Chrome) the Software Centre has flagged them as potentially damaging or corrupted and I've often wondered whether it's contributed to system borks. Thanks for the info, I know less about Linux than I know about Windows (which isn't a lot). So I appreciate the help.

---

### Post by treb0r on 2014-11-11
> **SagaciousKJB said:**
> I haven't been happy with the performance of FireFox at all.  I'm much happy with Chromium so far but I haven't tried Flash yet.  I don't know what is up with FireFox lately, I remember last time I looked it was on like version 3 then all the sudden 30 some odd versions?  And it's huge, so bloated...

I have to respectfully disagree with that.

I work as a web developer and I spend my life using an array of browsers including both Firefox and Chromium. Firefox is by far my favourite. What has happend with Firefox recnetly is that they started competing with Chrome on a lot of fronts. The JS performance of Firefox is now almost on a par with Chrome. The new dev tools are also very cool indeed.

For me, the thing that makes Firefox special is it's independence. I don't trust Google and I prefer to stay away from their products, even those like Chromium that are realeased under an open source license.

---

### Post by Daveski17 on 2014-11-11
> **SagaciousKJB said:**
> I haven't been happy with the performance of FireFox at all.  I'm much happy with Chromium so far but I haven't tried Flash yet.  I don't know what is up with FireFox lately, I remember last time I looked it was on like version 3 then all the sudden 30 some odd versions?  And it's huge, so bloated...

I've currently been searching for a replacement browser and I'm liking Chromium.

I've started running Chromium with the Pepper Flash Player browser plug-in found in the Software Centre: [http://ubuntuforums.org/showthread.php?t=2252218](http://ubuntuforums.org/showthread.php?t=2252218)

So far, it's turned out to be a good alternative/back-up browser to Firefox. Firefox is still my default though.

---

### Post by Daveski17 on 2014-11-11
> **treb0r said:**
> I have to respectfully disagree with that.

I work as a web developer and I spend my life using an array of browsers including both Firefox and Chromium. Firefox is by far my favourite. What has happend with Firefox recnetly is that they started competing with Chrome on a lot of fronts. The JS performance of Firefox is now almost on a par with Chrome. The new dev tools are also very cool indeed.

For me, the thing that makes Firefox special is it's independence. I don't trust Google and I prefer to stay away from their products, even those like Chromium that are realeased under an open source license.

For a couple of years many have predicted the demise of Firefox, even claiming it would soon be extinct. It's still going strong however, albeit now supposedly with only 15% of the market. I have a feeling Fx will be with us for quite a while. I think the NoScript extension is a particularly good strategy for security on Linux.

---

### Post by Daveski17 on 2014-11-11
> **vasa1 said:**
> Good news. Chromium has been updated```
chromium-browser:
  Installed: (none)
  Candidate: 38.0.2125.111-0ubuntu0.14.10.1.1103
  Version table:
     38.0.2125.111-0ubuntu0.14.10.1.1103 0
        500 http://archive.ubuntu.com/ubuntu/ utopic-updates/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu/ utopic-security/universe amd64 Packages
     37.0.2062.94-0ubuntu1~pkg1065 0
        500 http://archive.ubuntu.com/ubuntu/ utopic/universe amd64 Packages

```

Yes, I got them early this morning. :guitar:

---

