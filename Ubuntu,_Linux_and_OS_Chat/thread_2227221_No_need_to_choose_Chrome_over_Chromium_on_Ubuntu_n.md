---
title: "No need to choose Chrome over Chromium on Ubuntu now."
date: 2014-05-31
forum: Ubuntu, Linux and OS Chat
---

### Post by Tar_Ni on 2014-05-31
Hi,

Until recently to use a full-featured Chromium browser on Linux, the obvious and logical move was to get Google Chrome. But I discovered recently that it is no longer the case!

First of all, you can now  easily get the Chrome pepperflash plugin for Chromium on the Ubuntu software center.

A step by step guide is provided here: [https://wiki.ubuntu.com/Chromium/Getting-Flash](https://wiki.ubuntu.com/Chromium/Getting-Flash)

So that is done. The second biggest complaint was that there is no built-in PDF viewer in Chromium. That's true but a very simple solution exist and that can be found in the Chrome Web Store!

Just get the PDF viewer extension right here: [https://chrome.google.com/webstore/detail/pdf-viewer/oemmndcbldboiebfnladdacbdfmadadm](https://chrome.google.com/webstore/detail/pdf-viewer/oemmndcbldboiebfnladdacbdfmadadm)

Basicially it's the PDF viewer used for the Firefox browser (PDF.js) that uses the HTML5 technology to diplay the files in your browser. It's been adapted for Chromium/Chrome and maintanted by a developper so your extension will get updates.


Et voila! you've got a full-featured open source browser, that is Chromium, with the latest pepperflash and built-in PDF viewer!


***Some of you might already know all of this but I share it for those who don't.

---

### Post by Copper Bezel on 2014-05-31
Neat. I've become attached to Chrome's PDF viewer and the colorful icon - I don't really see a benefit of Chromium over Chrome - but that's really nice for people who want to keep a "purer" open source experience.

---

### Post by craig10x on 2014-05-31
Exactly, Chrome already has the pepperflash and the excellent pdf viewer built in...and it even puts a ppa into your software sources on the ubuntu updater so you get the newest version as soon as it is released (which is much quicker then chromium gets it)...

Anyway, how do you think ubuntu adds in the pepper flash plug in for you if you select chromium in the software center and check the box underneath that you want pepperflash installed also with it...
It EXTRACTS it from the licensed Chrome...;)  So, you may be using the open source version of chrome but you are still using chrome's flash plug in and pdf reader, so you are no longer PURE OPEN SOURCE anyway...
Sorry to be a "killjoy"...to me open or closed if it does what i need, i will take it gladly...:D

---

### Post by vasa1 on 2014-05-31
No reason to switch from Chrome to Chromium, as far as I'm concerned.

I recently did a rough comparison of CPU% usage viewing the same largish pdf file with pdf.js (in Firefox) and with Google Chrome with its built-in PDF viewer. The latter seemed more efficient.

Canonical's version of Chromium has, in the past, often been way, way outdated. Now that a Canonical employee is looking after things, matters may have improved. IDK. I stopped looking.

In my opinion, based on a reading of the second last row in the table near the top of [Differences between Google Chrome and Linux distro Chromium]("https://code.google.com/p/chromium/wiki/ChromiumBrowserVsGoogleChrome"), Chrome is a more tested product than Chromium.

FWIW, the description of Chromium in the repos is somewhat at variance with facts:>  Chromium serves as a base for Google Chrome, which is Chromium rebranded (name
 and logo) with very few additions such as usage tracking and an auto-updater
 system.
What auto-updater? Very few additions?

---

### Post by malspa on 2014-05-31
Hm. To each their own, I guess. For myself, there's been no need to choose Chrome over Chromium in Ubuntu for quite some time now, and I don't have Chrome installed in 14.04. As long as Chromium's in the repos and receives updates regularly, I'm happy.

---

### Post by Copper Bezel on 2014-05-31
The Chrome PDF viewer is the best one, for my purposes. I use it as the system default.

vasa1, the auto-updater applies only to Windows and Mac builds, since there's no system-wide update system.

---

### Post by vasa1 on 2014-06-01
> **Copper Bezel said:**
> ...
vasa1, the auto-updater applies only to Windows and Mac builds, since there's no system-wide update system.
Exactly. So mentioning it doesn't seem relevant.

---

### Post by philinux on 2014-06-01
Moved to Ubuntu Linux and OS chat.

---

### Post by Tar_Ni on 2014-06-01
Of course this thread is not to say that people should ditch Chrome and absolutely choose Chromium. We should use what works best for us.

Only that the two main complain about Chromium have been solved. It's now a full featured browser, perfectly capable for most users. You can easily install pepperflash and get a built-in PDF viewer in the Chrome Web Store.

That's great for those who want to support the open-source standard on Linux. I love Google Chrome don't get me wrong, but if I can use a decent and stable Chromium, that will be my choice.

> **craig10x said:**
> It EXTRACTS it from the licensed Chrome...;)  So, you may be using the open source version of chrome but you are still using chrome's flash plug in and pfd reader, so you are no longer PURE OPEN SOURCE anyway...

Actually it's the PDF viewer of Firefox (PDF.js), an open source project, now adapted for Chromium/Chrome. 

As for Flash Player, of course it's proprietaty but unless you are a ''purist'' and don't use flash at all which is clearly unpractical for me, the pepperflash for Chrome works great. Things may change in the future though as Flash plugins will be a thing of past. ;)

---

### Post by Tar_Ni on 2014-06-01
> **vasa1 said:**
> Canonical's version of Chromium has, in the past, often been way, way outdated. Now that a Canonical employee is looking after things, matters may have improved. IDK. I stopped looking.

In my opinion, based on a reading of the second last row in the table near the top of [Differences between Google Chrome and Linux distro Chromium]("https://code.google.com/p/chromium/wiki/ChromiumBrowserVsGoogleChrome"), Chrome is a more tested product than Chromium.

My Chromium is at 34.1847.116 which is not much outdated. The build is very stable and that's crucial. The next update will comme eventually no doubt.

By the way I only use Chromium on Linux, because it's the right platform to use it. The dev do the job for you by choosing the right builds and pushing the update in the Ubuntu update Manager. On Windows it's really unconvenient for the unexperienced users.

I think it's friendlier on OSX than Windows with the FreeSMUG project, you have Pepperflash built-in and can even auto update with Sparkle: [http://www.macupdate.com/app/mac/36244/chromium](http://www.macupdate.com/app/mac/36244/chromium)

---

### Post by craig10x on 2014-06-01
Didn't know that about the pdf reader...interesting...

@vasa1:  as mentioned, it's in the mac and windows versions that Chrome has the system updater which looks for and installs the latest version of Chrome...since that apparently can't be done on the linux version, they instead install a ppa in your ubuntu updater which accomplishes the same purpose :)

Still, it's nice to have it all (flash, pdf viewer and ppa for newest version as soon as released) all pre-packaged as you get it in the actual Chrome version...and it does feel somewhat more polished then the chromium version which is what they use to develop Chrome on...

---

### Post by Tar_Ni on 2014-06-02
> **craig10x said:**
> Still, it's nice to have it all (flash, pdf viewer and ppa for newest version as soon as released) all pre-packaged as you get it in the actual Chrome version...and it does feel somewhat more polished then the chromium version which is what they use to develop Chrome on...

You have it all with Chromium as well. :) The browser and every plugins are maintained by developpers and updated with the Ubuntu Update Manager.

---

### Post by monkeybrain20122 on 2014-06-02
> **Tar_Ni said:**
> You have it all with Chromium as well. :) The browser and every plugins are maintained by developpers and updated with the Ubuntu Update Manager.

Just use Firefox. :)

---

### Post by vasa1 on 2014-06-02
Yawn.

---

### Post by Tar_Ni on 2014-06-03
> **monkeybrain20122 said:**
> Just use Firefox. :)

I used to be a Firefox user and I thought I knew what a fast browser was. Things changed when using Chromium/Chrome. :)

---

### Post by monkeybrain20122 on 2014-06-03
> **Tar_Ni said:**
> I used to be a Firefox user and I thought I knew what a fast browser was. Things changed when using Chromium/Chrome. :)

When was the last time you used Firefox? FF29 is faster than Chrome. Also since version 34/35 Chrome/Chromium no longer works with NPAPI plugins which basically mean all plugins on Linux, so they are not even fully functioning browsers any more. :)

---

### Post by craig10x on 2014-06-03
Chrome is still nicer to use then firefox and has even better web page rendering...sorry, no sale ;) :D
I don't really use any sites where you have to have java (only one i did in the past was stock quote streamer on my brokerage site but i don't have that anymore) and as far as quicktime, well there are plenty of other movie trailer sites aside from itunes movie trailers...

---

### Post by monkeybrain20122 on 2014-06-03
> **craig10x said:**
> 
I don't really use any sites where you have to have java (only one i did in the past was stock quote streamer on my brokerage site but i don't have that anymore) and as far as quicktime, well there are plenty of other movie trailer sites aside from itunes movie trailers...

It is crippled if you have to avoid certain sites just because plugins don't work. ;) As I said before the only advantage of Chrome/Chromium over FF is hardware acceleration for html5 and flash (and built in h264 decoding, while in FF needs to install gstreamer-ffmppeg/gstreamer-libav). But if your cpu is powerful enough it probably doesn't matter. So for moderately weak machines I do tell people to use chrome for sites like vimeo where FF cannot play back smoothly (if it is too weak then there it is probably FF again using greasemonkey script + plugin ;)) Pepper flash is not really that much of a selling point now that you can easily use piplelight flash in FF and pepper-flash itself may be installable in FF soon.

---

### Post by craig10x on 2014-06-03
Well, maybe itunes i avoid but not the quote streamer...i got out of the market altogether (not because of chrome...lol)...but as i said, there are other sites i can watch movie trailers on as they use flash of course...
Also, i suspect those plug ins will be replaced (in their appropriate "wrapper") in Chrome by year's end because that's when the NPAPI plug ins will also be removed from windows and mac versions and you gotta KNOW that once that happens they aren't going to just leave it as it is now...Chrome is bundled with Internet Explorer on most computer manufacturer's window's systems these days and they would not stand for it, you can take that to the bank... ;)

---

### Post by Copper Bezel on 2014-06-04
> **monkeybrain20122 said:**
> When was the last time you used Firefox? FF29 is faster than Chrome. Also since version 34/35 Chrome/Chromium no longer works with NPAPI plugins which basically mean all plugins on Linux, so they are not even fully functioning browsers any more. :)
I tried Firefox again recently and was amazed how far it's come in being a Chrome alternative. It's faster, cleaner, and prettier than it's ever been, and it's very, very heavily influenced by Chrome's UI. Chrome still has some little extras I can't give up, like searching within a site from the omnibox. But for the first time, they seem comparable.

---

### Post by vasa1 on 2014-06-04
> **Copper Bezel said:**
> ... like searching within a site from the omnibox. ...
Hi, could you expand on that a bit? Do you mean something like *searchstring site:[www.something.com](www.something.com)*?

---

### Post by monkeybrain20122 on 2014-06-04
> **Copper Bezel said:**
> I tried Firefox again recently and was amazed how far it's come in being a Chrome alternative. It's faster, cleaner, and prettier than it's ever been, and it's very, very heavily influenced by Chrome's UI. Chrome still has some little extras I can't give up, like searching within a site from the omnibox. But for the first time, they seem comparable.

If you have many tabs open as I do Chrome is no alternative for FF, currently I have almost 300 tabs open in FF and it still loads faster than Chrome with may be only 10. Well I do understand that most people would not have that many open tabs. :)

---

### Post by bcschmerker on 2014-06-05
I'm running ongoing trials of Chromium&#8482; and its accompanying Adobe® Flash Player® for Google® Pepper&#8482; API under Ubuntu® 12.04.5-LTS, and Chromium&#8482; delivers well enough on Google® services and SingSnap®.  To date, Mozilla® Firefox® still has the overall advantage on availability of browser extensions.  Ubuntu® requires ppa:skunk/pepperflash to use the new plug-in on 13.10 and earlier; but supports it directly starting with 14.04-LTS (package: pepperflashplugin-nonfree).

---

### Post by malspa on 2014-06-05
I use Chromium most of the time here, but when it comes down to it, I'd be quite satisfied with either of these three (Chromium, Chrome, or Firefox). They each work quite well for the things I do here. A lot of it comes down to the user's personal preferences and browsing habits, seems to me. For example, if I liked to have tons of tabs open when the browser loads up, or if I liked using certain extensions, or lots of them, I'd probably prefer Firefox. I guess each of us has good reasons for using whatever browser(s) we've each chosen to use.

---

### Post by Copper Bezel on 2014-06-05
I turn off the delayed rendering and loading in Firefox. I never have more than a dozen tabs open and want them rendered and ready for me when I switch to them.

vasa1, yes, you can type all that, but in Chrome, there's a feature where the omnibox autocompletes domains and then selects known search providers from under that domain with tab completion. So I can search Amazon products by typing ama[Tab] [thing].

---

### Post by vasa1 on 2014-06-05
> **Copper Bezel said:**
> ..., there's a feature where the omnibox autocompletes domains and then selects known search providers from under that domain with tab completion. So I can search Amazon products by typing ama[Tab] [thing].
> Use a prediction service to help complete searches and URLs typed in the address bar or the app launcher search boxIs that it? Nice to know. I'll turn it on and give it a try.

---

### Post by Copper Bezel on 2014-06-05
Might be. I've never tried turning it on and off. But yeah, it's one of my favorite features in Chrome and worth the trying.

---

### Post by Tar_Ni on 2014-06-06
A really nice feature of Chromium/Chrome (that I've just discovered recently) is the ability to create webapp shortcut in the Launcher and desktop. That's awesome. It's way better and more functional than the (still experimental) Unity integration plug-in in Firefox.

> **bcschmerker said:**
> I'm running ongoing trials of Chromium&#8482; and its accompanying Adobe® Flash Player® for Google® Pepper&#8482; API under Ubuntu® 12.04.5-LTS, and Chromium&#8482; delivers well enough on Google® services and SingSnap®.  To date, Mozilla® Firefox® still has the overall advantage on availability of browser extensions.  Ubuntu® requires ppa:skunk/pepperflash to use the new plug-in on 13.10 and earlier; but supports it directly starting with 14.04-LTS (package: pepflashplugin-nonfree).

Don't forget to add the PDF viewer (PDF.js) addon in Chromium to display files directly in the browser, if you need this feautre.

It can be found in the Chrome Web Store:  [https://chrome.google.com/webstore/detail/pdf-viewer/oemmndcbldboiebfnladdacbdfmadadm](https://chrome.google.com/webstore/detail/pdf-viewer/oemmndcbldboiebfnladdacbdfmadadm)

---

### Post by Copper Bezel on 2014-06-06
Yeah, I've found it more useful than the Unity feature as well, and for longer. I remember either before the shortcut creation was implemented or before I discovered it just creating .desktop files for Chrome's app mode + gmail or another webapp address and sticking those in the launcher. Nice to keep particularly appy sites separate from the browser window.

---

### Post by Tar_Ni on 2014-06-06
And flash works, which can make a nice Youtube app in the launcher. :)

---

### Post by monkeybrain20122 on 2014-06-06
> **Tar_Ni said:**
> And flash works, which can make a nice Youtube app in the launcher. :)

This is better
[http://smplayer.sourceforge.net/en/smtube](http://smplayer.sourceforge.net/en/smtube)
You don't need flash for Youtube.

---

### Post by craig10x on 2014-06-06
You Tube is actually on html5 now...at least it is on my chrome...it defaults automatically to it and all the videos play fine...

---

### Post by Copper Bezel on 2014-06-06
Yep. = ) Although I always seem to end up with a lot of tabs up when I trawl YouTube, so.... = )

Oh - YouTube's commercial videos are still Flash-based, though.

---

### Post by monkeybrain20122 on 2014-06-07
> **Copper Bezel said:**
> Yep. = ) Although I always seem to end up with a lot of tabs up when I trawl YouTube, so.... = )

Oh - YouTube's commercial videos are still Flash-based, though.

Smtube can access all of them, you don't even need to log in to Google ti watch videos that have been flagged. :)

---

### Post by Copper Bezel on 2014-06-07
Well, as I said, I have a use case for watching YouTube in-browser, anyway. 

But the YouTube apps I've played with largely lack functionality I expect. I'm pretty happy with the Android mobile app, and I don't think it would be unduly limiting on the desktop, but it would still be a tossup between using that and just staying in-browser.

I don't feel any pressing need to avoid using Flash on the desktop. I look forward to it becoming obsolete, but for now, I like to have a browser that can access content even when that content's packaging is substandard.

---

