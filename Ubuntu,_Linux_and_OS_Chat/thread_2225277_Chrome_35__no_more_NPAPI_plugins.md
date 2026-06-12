---
title: "Chrome 35  no more NPAPI plugins"
date: 2014-05-20
forum: Ubuntu, Linux and OS Chat
---

### Post by monkeybrain20122 on 2014-05-20
got updated to Chrome 35 today, Google wiped out NPAPI plugins as promised. Went to about:plugins all the media plugins were wiped out. Went to Apple trailers, click a trailer and it told me to download quicktime (before gecko-mediaplayer/totem would just play)Went to a few other media sites and all has stopped working. With all the talks only fixating on flash Chrome has just become a rather crippled browser on Linux.

---

### Post by thiebaude on 2014-05-20
Yes totally agree, can't install netflix anymore on Chrome, I had to install it on Firefox :(

---

### Post by craig10x on 2014-05-20
Yeah...i lost quicktime too...can't play the itunes movie trailers...:(

Also, i noticed that i am getting different colors then i had before in the drop down url bar...and when in ubuntu forums, for example, if you point your mouse on a post and that balloon window comes up that shows a bit of a preview of the posting before you actually click on it, instead of having white letters on black background (Ubuntu ambiance theme) it's black letters on white background...anyone else getting that too? (in firefox the urls and balloon still are the old way)...could that have something to do with the removal of all those plug ins? or just changes in Chrome itself (theming perhaps)...i must say a am a bit puzzled...

I love Chrome though i can't understand why on the linux version they would knock out the quicktime plug in....flash i can understand (the old flash plug in isn't needed in Chrome anymore because of the much more current pepper version)...we don't have the option of downloading quicktime like windows and mac users do...I love linux but seems like it always gets treated like a "second banana"...grrr...maybe it's time for me to go back to windows...as the comedian Rodney Dangerfield use to say, "I don't get no respect" well, seems like linux often does not...:rolleyes:

Also, the java plug in got knocked out too...

---

### Post by craig10x on 2014-05-21
Well, i think i know why the balloon windows don't match the ambiance theme anymore and why the urls drop downs are different colors then before...see article in omg ubuntu...Chrome 35 is the first one with the new Aura Graphics Stack...supposed to be more compatible with the windows and mac versions of chrome and also brings in the new notifications window on top (i noticed i am getting those with my gmail notifier)...
This replaces GTK2 on Chrome...
[http://www.omgubuntu.co.uk/2014/05/google-chrome-35-linux-arrives-aura](http://www.omgubuntu.co.uk/2014/05/google-chrome-35-linux-arrives-aura)

---

### Post by monkeybrain20122 on 2014-05-21
> **craig10x said:**
> 
I love Chrome though i can't understand why on the linux version they would knock out the quicktime plug in...

Well not just quicktime, also windows media and all NPAPI plugins. This plan has been reported on many places months ago but the focus has always been on how Chromium may get flash and Youtube (while you don't even need flash to pay Youtube)
> .I love linux but seems like it always gets treated like a "second banana"...grrr...maybe it's time for me to go back to windows...as the comedian Rodney Dangerfield use to say, "I don't get no respect" well, seems like linux often does not...:rolleyes:

You can always join us to be one of many happy Firefox users, especially now that pepper flash may be coming to FF [http://www.webupd8.org/2014/05/fresh-player-plugin-pepper-flash.html](http://www.webupd8.org/2014/05/fresh-player-plugin-pepper-flash.html) :) I have been using this same developer's vdpau driver for intel to get hw accel for mplayer, it works quite well. :)

I remember reading in the pipelight  Q&A that the codes to support NPAPI plugins have not been removed from Chromium yet, they will probably be there til the end of the year. It is just that google's build has disabled them, so it is possible to build Chromium with pipelight support. If that is the case it would apply to other NPAPI plugins as well. So maybe it will come a time when Chromium is actually more capable and feature complete than Chrome. :)

---

### Post by craig10x on 2014-05-21
Now that would be weird...chromium more complete then chrome...yeah, it looks pretty barebones when i check the plugins page for chrome now...the other stuff i mentioned must relate to the new aura graphics stack, since it's not using GTK anymore...:(

Yeah, i know i could come over to firefox and the flash (fresh plug in) business you mentioned would certainly enhance it....though i am still more of a chrome guy, so would be tough to change...;)

---

### Post by deadflowr on 2014-05-21
> **craig10x said:**
> 
Yeah, i know i could come over to firefox and the flash (fresh plug in) business you mentioned would certainly enhance it....though i am still more of a chrome guy, so would be tough to change...;)

I thought it would be too, as I was an avid Chrome user.
But turns out, Firefox has worked quite well.
Flash might be old, but it at least works correctly...
Pepperflash seems to have something wrong every release.
IMHO-for the record:)

---

### Post by vasa1 on 2014-05-22
> **craig10x said:**
> ..., since it's not using GTK anymore...:(
...
Even the Arch guys aren't overjoyed: [https://bbs.archlinux.org/viewtopic.php?pid=1417681](https://bbs.archlinux.org/viewtopic.php?pid=1417681)

And this post points to some gtk remnants: [https://bbs.archlinux.org/viewtopic.php?pid=1417681#p1417681](https://bbs.archlinux.org/viewtopic.php?pid=1417681#p1417681)

But I just get back the prompt after running
```
ldd /usr/bin/google-chrome | grep gtk
```

Just to compare:
```
[06:35 PM] ~ $ ldd /usr/bin/xombrero | grep gtk
	libwebkitgtk-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libwebkitgtk-1.0.so.0 (0x00007f30a9405000)
	libgtk-x11-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0 (0x00007f30a8dc9000)
	libjavascriptcoregtk-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libjavascriptcoregtk-1.0.so.0 (0x00007f30a8520000)
[06:36 PM] ~ $ 
```

---

### Post by vasa1 on 2014-05-22
> **craig10x said:**
> ..., if you point your mouse on a post and that balloon window comes up that shows a bit of a preview of the posting before you actually click on it, instead of having white letters on black background (Ubuntu ambiance theme) it's black letters on white background...anyone else getting that too? ...
Seeing that too. Looks like all tooltips are affected. 

But it's odd that under Settings, Appearance, there's mention of "Use GTK+ theme" and "Use Classic Theme".

A visit to crbug.com may be entertaining ;)

Other reports are being merged into this: [https://code.google.com/p/chromium/issues/detail?id=348194](https://code.google.com/p/chromium/issues/detail?id=348194)

But a dev version no longer has the problem: [https://code.google.com/p/chromium/issues/detail?id=375659#c2](https://code.google.com/p/chromium/issues/detail?id=375659#c2)

So we'll just have to see if they can update stable with the fix.

---

### Post by craig10x on 2014-05-22
@vasa1: and i have the GTK+ Theme box checked (always have in fact)....i still get the black ambiance panel bar on top of course (since that isn't actually from the chrome browser itself) but the GTK+ aspects are knocked out from Chrome because of the change over to Aura...

Thanks for posting the links...for me, this really messes up chrome and i am not a big firefox fan...in fact (not an option on linux of course) i like internet explorer more then i like firefox...although i do appreciate deadflowr's encouragement :D

---

### Post by monkeybrain20122 on 2014-05-22
I hardly notice any difference in the way that Chrome looks, but then I only fire it up may be once or twice after every update for 10-15 minutes to see if anything is broken. :)

---

### Post by vasa1 on 2014-05-23
Just noticed that the url (in the omnibar) is selected by a single mouse click. IIRC, it took three clicks before.

---

### Post by craig10x on 2014-05-23
I wonder what is going to happen as far as the plugs ins that have been knocked out...if google will replace them with their own?  Ubuntu?  If the community will have to find a way? and what about the breakage caused by the aura switch away from gtk+? :(

Seems everything is "up in the air" now with this...I do like the new notifications thing on the top though...looks pretty neat when i get gmail notifications with my gmail notifier extension... :D

@monkeybrain20122:  Well, go into chrome and to ubuntu forums....then place your mouse over an forum topic...you know that small square windows that comes up to preview the first few sentences of the post (before you actually click on the post)....it used to be in ambiance them (white letters on black background) which it was able to do because chrome was still GTK+...

Now that aura has replaced it in chrome, that window box is black lettering on white background)...then go back to your firefox and do the same thing...firefox still displays with ambiance look because it is still GTK+ of course...So, some ubuntuish intergration has been lost in the change...also url colors on the drop down url menu are different (a lot of green) though that doesn't look bad...

---

### Post by monkeybrain20122 on 2014-05-23
> **craig10x said:**
> I wonder what is going to happen as far as the plugs ins that have been knocked out...if google will replace them with their own?  Ubuntu?  If the community will have to find a way? and what about the breakage caused by the aura switch away from gtk+? :(
.

The community may be able to do something with Chromium, but not very much they can do with Chrome. BTW, google is not doing this just on Linux, it is dropping support for NPAPI on Windows and Mac as well, but on these platforms there is a way to whitelist some plugins for a grace peroid (e.g quicktime) On those platforms google wouldn't dare to just pull the rung off people's feet like it does on Linux.

---

### Post by craig10x on 2014-05-23
Oh really, on the windows and mac platforms as well?  but i thought on those systems, those things run independently and don't actually have to be "plugged in" to the browser itself...i am not that technically oriented, but i assumed it worked differently then it does on linux...maybe someone can fill me in on that...if Chrome dropped support for those plug ins....would that mean that quicktime, java, and the other plugs ins they took out on linux would kill it for mac and windows as well?   If that were the case, i don't think Chrome would DARE do it on those platforms as their popularity now over Internet Explorer and Safari would quickly sink like real low low down...

---

### Post by monkeybrain20122 on 2014-05-23
> **craig10x said:**
> Oh really, on the windows and mac platforms as well?.

[http://www.pcworld.com/article/2049309/chrome-will-block-npapi-plugins-over-stability-security-concerns.html](http://www.pcworld.com/article/2049309/chrome-will-block-npapi-plugins-over-stability-security-concerns.html)

---

### Post by craig10x on 2014-05-24
I read the article...but still, i was under the impression that with windows and mac those type of things run directly on the system rather then only in the browser like they do on linux...
if they work the same as on linux, then windows and mac users would be complaining about it right now too but i haven't seen anything from them..only on on the linux forums...also, that would mean that the only browsers capable of running those things would be internet explorer and safari...firefox is going to drop them very likely also, based on what that article says...

So what happens to sites like itunes movie trailers (quicktime), streaming stock quotes on brokerage sites (java), etc...everyone just packs it in?

---

### Post by monkeybrain20122 on 2014-05-24
Firefox apparently won't drop the plugins, but will make them click to play. This has been the defauly for java for several releases, I always configure flash to click and play since the option is available (instead of using flashblock which is now unnecessary)
[http://mozilla.6506.n7.nabble.com/Mozilla-is-blocking-NPAPI-Plugin-td292582.html](http://mozilla.6506.n7.nabble.com/Mozilla-is-blocking-NPAPI-Plugin-td292582.html)

It is interesting the the PC world article mentioned quicktime as a a risky plugin, whereas on Linux we are not even using quicktime to play Apple contents. On Linux the media plugins are different (mainly mplayer for everything, really)

---

### Post by craig10x on 2014-05-25
I talked to my friend who is big on using windows (and mac)....he said this change wouldn't affect users of windows (and mac) because they use proprietary plugs ins for things like quicktime (which you download from apple for both windows and mac) and Java (same deal there of course) etc...pulling the NPAPI plugs ins only messes things up in linux because we use community based versions...so that's why i wonder what the ultimate solution will be for linux...

---

### Post by monkeybrain20122 on 2014-05-25
Whether plugins are proprietary or not has nothing to do with whether they are NPAPI, all Windows and Mac plugins are proprietary. Google says they will drop support for NPAPI plugins, that means all. But it hasn't kicked in for Windows and Mac yet and they will be phased out gradually with option to whitelist temporarily instead of so abruptly like on Linux.

---

### Post by craig10x on 2014-05-25
In that case, on all the systems (linux, mac, windows) the developers will have to figure out an alternative to NPAPI that will make those plug ins compatible with chrome and chromium (if it works in chromium it will also work in chrome of course)....i know you are a firefox guy, but a LOT of people use Chrome and Chromium on all 3 systems...

---

### Post by monkeybrain20122 on 2014-05-25
> **craig10x said:**
> In that case, on all the systems (linux, mac, windows) the developers will have to figure out an alternative to NPAPI that will make those plug ins compatible with chrome and chromium (if it works in chromium it will also work in chrome of course)....

Yeah that is exactly what Google says, NPAPI addons are already banned from Chrome store (actually for quite sometimes if I am not mistaken), Google expects developers to conform to their new standard.

---

### Post by monkeybrain20122 on 2014-05-25
The guys from pipelight have apparently come up with a patch to re-enable NPAPI plugins in Chromium. [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307989](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307989)

---

### Post by craig10x on 2014-05-26
Interesting...also, what i think will happen is that by year's end, Chrome is going to phase out the NPAPI plug ins on the Mac and Windows versions as well (we were unfortunate in that we got the "hit" first)...in the meanwhile, the developers of the proprietery versions of the various plug ins that got knocked out will probably be making agreements with google (same as adobe did with the pepperflash for chrome which is used on all Chrome platforms)...

Now, with the coming of Aura, Google Chrome can now develop everything cross platform since they will no longer need to have separate versions...anything developed for one version, will work in the others...
Once that happens (should be by the end of the year when the plug ins get phased out on mac and windows) then Chrome will be fully functional on Linux again...
This can be done with Chrome because of it's licensed nature...In Chromium's case (being the totally open source side of the project), patching appears to be the answer...

This i what i believe will happen, based on various articles i read online which i think gives me a clearer picture of what is going on.....Google's reasoning for banning the plug ins is that they bring down the level of security on the browser...take pepperflash for example, it has very good security provisions and is properly "sandboxed"...

---

### Post by d-cosner on 2014-05-26
From everything I have been reading here, it sounds like the absence of NPAPI plugins is just a temporary inconvenience. Who would want to run a crippled browser and surely this effects Chrome OS seeing that it is Linux based. Maybe we are reading this all wrong and Google wants to take care of things on the Linux side quicker to protect their interests.

---

