---
title: "The state of flash"
date: 2014-01-13
forum: The Cafe
---

### Post by kerryhall on 2014-01-13
I have heard that flash support for Linux has been deprecated. Any thoughts on this? Is the general plan to move to gnash? Or something else perhaps? 

Thanks for your opinions!

---

### Post by oldos2er on 2014-01-13
Moved to Cafe.

---

### Post by craig10x on 2014-01-13
Google Chrome (not Chromium) has the pepperflash which does always provide the latest flash (they have an agreement with adobe for that)....that is what i use myself...
Firefox 27 (out in February) will have the Shumway plug in but the firefox fans tell me that it doesn't work up to snuff as of yet...

The adobe flash plug in you get in ubuntu restricted extras is over 2 years old and will only get security updates for a few more years...adobe no longer makes a flash for linux other then the agreement to provide it through Chrome...

---

### Post by JDorfler on 2014-01-13
Seems Adobe likes shooting themselves in the foot.  SteamOS is coming out and Debian Linux will have a sizeable share of the market.  Just wait until professionals finally discover GIMP.

---

### Post by bcschmerker on 2014-01-13
> **craig10x said:**
> Google Chrome (not Chromium) has the pepperflash which does always provide the latest flash (they have an agreement with adobe for that)....that is what i use myself...
Firefox 27 (out in February) will have the Shumway plug in but the firefox fans tell me that it doesn't work up to snuff as of yet...

The adobe flash plug in you get in ubuntu restricted extras is over 2 years old and will only get security updates for a few more years...adobe no longer makes a flash for linux other then the agreement to provide it through Chrome...
I found as did craig10x, would that Adobe Systems ran Flash Player for LinUX at least as far as 11.7.700.nnn-LTS (Adobe® is providing long-term support for Flash Player 11.7 for Microsoft® Windows® 6-up and Apple® MacOS® X™ 10.7-up) rather than stalling it at 11.2.202.nnn; this way, users unable to utilize Google® Chrome™ would still have access to current shockwave-flash IFrames.  (I'm running Chromium™ with the PepperFlash™ player, and found that the PPAPI version of Flash Player 11.9.900.nnn performs as advertised, at least at SingSnap® and at various Google® Services.)

---

### Post by ibjsb4 on 2014-01-13
[http://ubuntuforums.org/showthread.php?t=2198551](http://ubuntuforums.org/showthread.php?t=2198551)

---

### Post by monkeybrain20122 on 2014-01-13
flash is a mess. While Chrome has up to date flash it is crippled. You can't access drmed contents with it (google videos, Amazon videos for examples) and outside those most websites would work with flash 11.2 anyway. 

As for drmed contents, there are work arounds for Firefox that won't work with Chrome. There is hal (which has a ppa for Saucy and Trusty) and there is also an option in Firefox to install Windows flash through pipelight (I suggest switching to it only when needed with something like galternatives ,--or the update-alternatives command,--as it is not as smooth as native flash when the latter does work) and this won't work in Chrome/Chromium starting April when google bans all NNAPI plugins from these browsers.

Finally there are non flash options to access popular sites like Youtube, Vimeo  etc with greasemonkey scripts like Viewtube and again this won't work on Chrome/Chromium after April. (there are also standalone Youtube viewers like minitube, so Youtube is the least of the problem even though it always gets the most attentions,--flash 11.2 also works and there is html5 option for many videos.)

So there are still more options for flash with Firefox than with Chrome.

---

### Post by mastablasta on 2014-01-14
so what will be the solution? flash stuff won't work on linux or will work slow/crippled? so basically it will only work on windows then?

---

### Post by Frogs Hair on 2014-01-14
I have enabled Shumway on the FF Nightly Browser and seems to work pretty well and I hope it has a future . The plug-in indicator that appears in the address bar when media is running offers the option to allow Adobe flash or not . 

[https://github.com/mozilla/shumway](https://github.com/mozilla/shumway)

---

### Post by Dave_L on 2014-01-14
What about archived files of types .swf and .flv?  Will they become unreadable at some point?  Is is safe to assume there will be a legacy player for those files in the future?

---

### Post by Frogs Hair on 2014-01-14
> What about archived files of types .swf and .flv?  Will they become  unreadable at some point?  Is is safe to assume there will be a legacy  player for those files in the future? 		

> Shumway is an HTML5 technology experiment that explores building a faithful and efficient renderer for the SWF file format without native code assistance. I don't know about FLV though. The full screen video quality using Shumway is superior to Flash on my computer, but has only been used with Youtube so far.

---

### Post by craig10x on 2014-01-14
@ Frogs Hair:  I was curious: how well does shumway work on stream radio (that uses flash)...i am talking about when you go to a radio station's website (like say KABC for example) and click on their stream tuner to listen to the broadcast) is it smooth and stable?  and how about flash videos on commercial websites or say on news video clips on say yahoo?

I read that Shumway was supposed to be turned on by default when firefox 27 comes out in February...anyone know anything about that?

Although i prefer Chrome myself...if the shumway plug in works well, i may occasionally use firefox for certain flash purposes...

---

### Post by Frogs Hair on 2014-01-14
The listen live link works at the link if that's the correct site. Shumway also works on local stations I use.   [http://player.listenlive.co/24571](http://player.listenlive.co/24571) 

Works here also. [http://www.crackle.com/](http://www.crackle.com/)

---

### Post by craig10x on 2014-01-14
Thanks...yep that would be the correct site...I'll have to try it when they put it on the default...

---

### Post by bcschmerker on 2014-01-14
> **Frogs Hair said:**
> I have enabled Shumway on the FF Nightly Browser and seems to work pretty well and I hope it has a future . The plug-in indicator that appears in the address bar when media is running offers the option to allow Adobe flash or not . 

[https://github.com/mozilla/shumway](https://github.com/mozilla/shumway)
Thanks for the heads up on the Shumway plug-in; I'll definitely check it out when Ubuntu® 14.04.1-LTS is RTM, as Mozilla® Firefox® should have it in release by that time.  Firefox® already has native W3C HTML 5 video handling for some Websites, a good secondary mode; YouTube™/Google® already runs HTML 5 on some platforms.

---

### Post by buzzingrobot on 2014-01-15
> **mastablasta said:**
> so what will be the solution? flash stuff won't work on linux or will work slow/crippled? so basically it will only work on windows then?

Whatever the answer will be, it won't be Flash, on any platform. Something else will replace it across the industry.  Or, a combination of things. 

Flash will linger in Windows longer than elsewhere simply because of the deadweight of all those Windows installs.

I don't know if Adobe makes, or ever made, any money from Flash. But, I can't believe they make money from cranking out the incessant security patches.

In the interim, Flash-for-Linux is frozen in place, still there, still working, and not going any place.

---

### Post by mastablasta on 2014-01-15
Adobe makes money from tools that create flash content. Kind of like they do/did with Adobe PDF reader.

so only chromium is an issue then since google ownt' allow certain api. firefox could basically use the old legacy version. unpatched though.

Chrome is not really a solution.

---

### Post by craig10x on 2014-01-15
@mastablasta:  I use Chrome and the pepperflash seems to work well most of the time...and it seems to be the only way to keep up to date flash now on linux...
for the firefox fans, hopefully the shumway plug in will work well for them and keep them up to date as well...

for Chromium, they will need to use the pepperflash plug in option that Canonical is providing starting in 14.04...

---

### Post by buzzingrobot on 2014-01-15
> **craig10x said:**
> @mastablasta:  I use Chrome ..and it seems to be the only way to keep up to date flash now on linux...


Linux gets the security patches. What is Adobe adding to Flash, beyond that, for other platforms?

I make little use of Flash other than the occasional embedded clip. Am I missing out on something?

---

### Post by craig10x on 2014-01-15
@buzzingrobot: I am not sure but the old linux plug in in our systems in 11.2 and the current one on pepper on my chrome is 12.0, so there has been like 8 newer versions since the old 11.2 was released several years ago....yes, it still gets security updates, but i would have to assume the newer versions of flash have some kind of improvements, otherwise wouldn't they just keep making the same version?
maybe some one else here knows the technical differences...

---

### Post by marianoa on 2014-01-15
if you enable flash to be used via pipelight, it will install the lastest flash version in wine and pipe all the flash content to the windows plugin showing the output in the browser (is the browser is supported by pipelight, Firefox and Chromium are among the supported ones). I've tried and it works perfectly both for flash and silverlight.

[https://launchpad.net/pipelight](https://launchpad.net/pipelight)

---

### Post by monkeybrain20122 on 2014-01-15
> **marianoa said:**
> if you enable flash to be used via pipelight, it will install the lastest flash version in wine and pipe all the flash content to the windows plugin showing the output in the browser (is the browser is supported by pipelight, Firefox and Chromium are among the supported ones). I've tried and it works perfectly both for flash and silverlight.

[https://launchpad.net/pipelight](https://launchpad.net/pipelight)

But wine flash have loading problem on some pages when native flash works, when they both work native flash is usually smoother. Wine flash also doesn't work for some audio thing (e.g google translate) but native flash does.
You can create a switching mechanism so that you only switch to Windows flash when you need to (basically for drmed contents, say Google videos) Install galternatives, open it, go to Mozilla flash  and add the path of pipelight flash.

---

### Post by monkeybrain20122 on 2014-01-15
> **craig10x said:**
> @buzzingrobot: I am not sure but the old linux plug in in our systems in 11.2 and the current one on pepper on my chrome is 12.0, so there has been like 8 newer versions since the old 11.2 was released several years ago....yes, it still gets security updates, but i would have to assume the newer versions of flash have some kind of improvements, otherwise wouldn't they just keep making the same version?
maybe some one else here knows the technical differences...

Most websites work even on flash 10 (how do I know? there are threads ever so often when people complain that for some reasons flash doesn't work and installing old flash somehow works, it is a bad idea for security reasons, but it works nevertheless). I don't find any difference between pepper flash and 11.2 other than the latter doesn't crash chrome while pepper flash does from time to time according to bug reports. Do you actually see any difference?

---

### Post by marianoa on 2014-01-15
@[COLOR=#000000]monkeybrain20122[/COLOR]
I'll keep it in mind, so far I haven't had any problem

---

### Post by monkeybrain20122 on 2014-01-15
> **marianoa said:**
> @[COLOR=#000000]monkeybrain20122[/COLOR]
I'll keep it in mind, so far I haven't had any problem

Webcam doesn't work with Pipelight flash.

---

### Post by marianoa on 2014-01-15
> **monkeybrain20122 said:**
> Webcam doesn't work with Pipelight flash.

Ok, I don't need to use the webcam with flash so, as I said, I haven't had any problem so far. I understand that pipelight is not the solution to all linux flash problems, I mentioned it as an option

---

### Post by monkeybrain20122 on 2014-01-15
> **marianoa said:**
> Ok, I don't need to use the webcam with flash so, as I said, I haven't had any problem so far. I understand that pipelight is not the solution to all linux flash problems, I mentioned it as an option

It is certainly an option (besides hal, which is deprecated and available through only ppa) to access drmed contents. Nothing else would work. I have installed it and setup galternatives to switch, it works very well like that.

---

### Post by monkeybrain20122 on 2014-01-16
> **Frogs Hair said:**
> The listen live link works at the link if that's the correct site. Shumway also works on local stations I use.   [http://player.listenlive.co/24571](http://player.listenlive.co/24571) 

Works here also. [http://www.crackle.com/](http://www.crackle.com/)

Doesn't work for me at all. I see the small "shumway" tag at the lower right corner of the flash box and that is it. Maybe I am using FF 26 though I am under the impression that you don't need FF27 beta for it to work. Did you configure it in some way?

---

### Post by Frogs Hair on 2014-01-16
Shumway was added to Nightly in version 27 which is now up to 29 . I found nothing to indicate when it may be added to stable versions . In Nightly, Shumway was  enabled  in about configuration. Though I am not using flash it is still required to be installed with option to allow flash as stated at the link. I am guessing the need to install flash will be removed in the future. Shumway is still  in the experimental development stage. 

[http://www.ghacks.net/2013/10/02/mozillas-flash-plugin-replacement-shumway-lands-firefox-nightly/](http://www.ghacks.net/2013/10/02/mozillas-flash-plugin-replacement-shumway-lands-firefox-nightly/)

---

### Post by monkeybrain20122 on 2014-01-16
> **Frogs Hair said:**
> Shumway was added to Nightly in version 27 which is now up to 29 . I found nothing to indicate when it may be added to stable versions . In Nightly, Shumway was  enabled  in about configuration. Though I am not using flash it is still required to be installed with option to allow flash as stated at the link. I am guessing the need to install flash will be removed in the future. Shumway is still  in the experimental development stage. 

[http://www.ghacks.net/2013/10/02/mozillas-flash-plugin-replacement-shumway-lands-firefox-nightly/](http://www.ghacks.net/2013/10/02/mozillas-flash-plugin-replacement-shumway-lands-firefox-nightly/)

Hi, on the github page [https://github.com/mozilla/shumway](https://github.com/mozilla/shumway) on the section "Exteension" if you click the .xpi link it will install shumway in Firefox. Since it is built-in in the daily build I assume that the install link is for Firefox stable.

I think flash needs to be installed because some sites would try to detect the presence of flash plugins (e.g [http://www.wimp.com/](http://www.wimp.com/)) so the requirement may have nothing to do with shumway per se. I suspect for that you don't really need Adobe's flash, any "flash plugin" would do (alternative "flash plugins" like gnash and totem-vegas that normally don't even work)  This is the case with a .js script I use for replacing flash. Since shumway doesn't work for me at all I can't test this hypothesis, you may want to check it out. :) If that is true Mozilla just have to make some kind of dummy "flash plugin" in the future to work with shumway.

---

### Post by Frogs Hair on 2014-01-16
> [COLOR=#000000]*flash it is still required to be installed with option to allow flash as stated at the link.*[/COLOR]

[http://www.ghacks.net/2013/10/02/moz...refox-nightly/]("http://www.ghacks.net/2013/10/02/mozillas-flash-plugin-replacement-shumway-lands-firefox-nightly/")

---

### Post by monkeybrain20122 on 2014-01-16
> **Frogs Hair said:**
> [http://www.ghacks.net/2013/10/02/moz...refox-nightly/]("http://www.ghacks.net/2013/10/02/mozillas-flash-plugin-replacement-shumway-lands-firefox-nightly/")

I think gnash will probably work too, as long as you choose the other alternative.

Edited: What happens if set shumway.ignoreCTP = true?

> shumway.ignoreCTP (boolean) - for Firefox 21 and up, the  extension is shown only when the click-to-play is enabled (see the  setting below). Set the value of this key to true to bypass  this check and always show the Shumway extension instead of the plug-in  (the browser must be restarted when this setting is modified);
[https://github.com/mozilla/shumway/wiki/Debugging-and-Configuring-Shumway](https://github.com/mozilla/shumway/wiki/Debugging-and-Configuring-Shumway)

---

### Post by monkeybrain20122 on 2014-01-16
While shumway doesn't work here, I do get the buttons to choose between shumway and "flash". 

On this partition (Fedora 19) I have no flash. It is an alternative flash plugin called Totem-mozilla-vegas. (I don't think that shumway not working has to do with me not having real flash because it doesn't work in Ubuntu either, where I do have flash installed)

---

### Post by Frogs Hair on 2014-01-16
Movie Playing

---

### Post by monkeybrain20122 on 2014-01-16
How do you know it is shumway? Your screenshot actually looks like flash (the player, the progress bar etc). Can you right click and see the info displayed? Thanks.

---

### Post by Frogs Hair on 2014-01-16
Because flash has to be allowed by using the options in the pop up near the address bar .

---

### Post by monkeybrain20122 on 2014-01-16
I tried the same link. I also configured flash to "always ask", I saw the little "shumway" tag at the lower right corner of the flash box. I clicked and it played like in your screenshot. But I right click the video to check and it turns out to be flash.

---

### Post by Frogs Hair on 2014-01-16
Shumway _is not independent of flash at this point_ and as described at  the links experimental. The code was not part of FF until Nightly 27. It  is not a working replacement for Flash at this time.

---

### Post by monkeybrain20122 on 2014-01-16
> **Frogs Hair said:**
> Shumway _is not independent of flash at this point_ and as described at  the links experimental. The code was not part of FF until Nightly 27. It  is not a working replacement for Flash at this time.

I know that. But the video is played in flash, at least on my FF26 stable with shumway installed, showing the buttons and all.

To ask differently, if you play that video and right click on it, what does it say?

---

### Post by mips on 2014-01-16
> **monkeybrain20122 said:**
> I know that. But the video is played in flash, at least on my FF26 stable with shumway installed, showing the buttons and all.

To ask differently, if you play that video and right click on it, what does it say?

I've got shumway extension in ff26 but I can't open any flash stuff without the flashplugin installed.

---

### Post by monkeybrain20122 on 2014-01-16
> **mips said:**
> I've got shumway extension in ff26 but I can't open any flash stuff without the flashplugin installed.

But can you open any video *with shumway* if flash is installed? I do have flash in Ubuntu.

---

