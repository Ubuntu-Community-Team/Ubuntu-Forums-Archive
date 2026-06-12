---
title: "I can't believe how fast Opera is..."
date: 2006-05-19
forum: The Cafe
---

### Post by xXx 0wn3d xXx on 2006-05-19
I just installed Opera 9 on my Dapper 6.06 installation and it flies. I have used Firefox for over a year, but Opera is much faster ! The only thing I miss is the extensions but Opera is great. You can download Opera 9 from [ here. ](http://opera.com/download/index.dml?ver=9.0b)

---

### Post by S{yndrom}e on 2006-05-19
i heard that opera takes up alot of window space if you dont buy the pro version or something like that.

---

### Post by Ob1 on 2006-05-19
yea, i also find opera much faster.

---

### Post by Lord Illidan on 2006-05-19
[quote=S{yndrom}e]i heard that opera takes up alot of window space if you dont buy the pro version or something like that.[/quote]

Yes, but way back when Opera used to charge for the pro version, and put ads in its shareware version.
Now, it is freeware, I believe.. No ads. You only pay for support.

---

### Post by S{yndrom}e on 2006-05-19
> Yes, but way back when Opera used to charge for the pro version, and put ads in its shareware version.
Now, it is freeware, I believe.. No ads. You only pay for support.

Ahh i see i have to try it out then. If it don't like it ill just uninstall it.

Dont you just love sudo apt-get =P

---

### Post by xXx 0wn3d xXx on 2006-05-19
[QUOTE=Lord Illidan]Yes, but way back when Opera used to charge for the pro version, and put ads in its shareware version.
Now, it is freeware, I believe.. No ads. You only pay for support.[/QUOTE]
It is freeware and you can get free support on their forums. How do you block images in the new beta ? I try to right click an image but I don't get the option and nothing happens when I hold shift and click/right click the image. Any idea on how to fix this ?

---

### Post by shuttleworthwannabe on 2006-05-19
Notice how little cpu it uses cf to firefox. Opera is one of the first things I install on a clean dapper installation. They have also worked on it to be more gmail friendly. 

My only problem is that I can't play multimedia in opera, so I switch to ff to listen to cnn or bbc. I hope they fix this too.

---

### Post by Biltong (Dee) on 2006-05-19
Thanks for the info guys.
Now, what the heck are Opera Widgets?

---

### Post by Kernel Sanders on 2006-05-19
[QUOTE=MasterChief1234]It is freeware and you can get free support on their forums. How do you block images in the new beta ? I try to right click an image but I don't get the option and nothing happens when I hold shift and click/right click the image. Any idea on how to fix this ?[/QUOTE]

Its under the main options menu IIRC. Under content, and there's a blocked content button or something......

They should really have made it right clickable like in firefox tbh......

---

### Post by sup on 2006-05-19
> It is freeware and you can get free support on their forums. How do you block images in the new beta ? I try to right click an image but I don't get the option and nothing happens when I hold shift and click/right click the image. Any idea on how to fix this ?
Right-click anywhere on the page besides images - block content is third from the bottom.

---

### Post by n3tfury on 2006-05-19
[QUOTE=Biltong (Dee)]Thanks for the info guys.
Now, what the heck are Opera Widgets?[/QUOTE]

similar to gdesklets and moreso to [yahoo/konfabulator widgets]("http://widgets.yahoo.com/")

---

### Post by Biltong (Dee) on 2006-05-19
Thanks. More things to play with. Goodee :-)

---

### Post by mstlyevil on 2006-05-19
If you want the speed of Opera but the extentions of Firefox, then try Swiftfox.
It is like Epiphany on steroids.

---

### Post by xXx 0wn3d xXx on 2006-05-19
[QUOTE=mstlyevil]If you want the speed of Opera but the extentions of Firefox, then try Swiftfox.
It is like Epiphany on steroids.[/QUOTE]
I am already using Swiftfox but Opera is still alot faster then that. Firefox and Swiftfox seem to have a hard time with page rendering.

---

### Post by BarfBag on 2006-05-19
Opera is AMAZINGLY fast.  I would use it, but it doesn't support the MPlayer Browser Plug-in.  Anyone know of an alternative that works just as good (almost as good is acceptable) and is installable via apt-get?

---

### Post by papangul on 2006-05-20
You may try mozplugger plug-in but it's a little difficult to set-up.

---

### Post by shuttleworthwannabe on 2006-05-20
So I was right, Opera does have a multimedia problem. Has anyone figured out how ro fix this: I test on cnn and bbc, and on both I have issues with playing theor videos. FF plays fine. I have all the required codecs installed. Do we have to point Opera to the w32codecs that FF uses?? Like a symlink or something?? I am not a guru, but just making the analogy from other programs.

I am so happy someone has also discovered the power of opera. For me Opera has a small footprint, and light on the resources.

tah

---

### Post by sophtpaw on 2006-05-20
[QUOTE=MasterChief1234]I just installed Opera 9 on my Dapper 6.06 installation and it flies. I have used Firefox for over a year, but Opera is much faster ! The only thing I miss is the extensions but Opera is great. You can download Opera 9 from [ here. ](http://opera.com/download/index.dml?ver=9.0b)[/QUOTE]
 love how Opera operates - fast. But how does one get mplayer to work? I don't know how to bring all the pluggins over, so my opera is not as functional or shall i say operatic, as i'd like it to be.

---

### Post by siimo on 2006-05-20
[QUOTE=mstlyevil]If you want the speed of Opera but the extentions of Firefox, then try Swiftfox.
It is like Epiphany on steroids.[/QUOTE]
:mrgreen:  dude!  this swiftfox thing is nothing but just a recompiled firefox with changed names and optimized for particular cpus, i used to do that too back in the day ( [http://pryan.org/firefox/siimo/](http://pryan.org/firefox/siimo/) ) but it doesn't make any notable improvements so i stopped.  

Swiftfox has nothing to do with Epiphany. :-?

---

### Post by DigitalDuality on 2006-05-20
I for 2-3 weeks now used Flock exclusively and applied the Firefox tweaks to it.  

Flock out of the box runs faster than firefox, comes with functionality i'd already  install via plugins anyways on Firefox, and has a slicker GUI.

After doing the following

>  Kill the amount of RAM Firefox uses for it's cache feature
Here's how to fix it:
1. type "about:config" (no quotes) in the browser.
2. Find browser.sessionhistory.max_total_viewer
2. set it's value to "0"

Page Load Time
Alter the entries as follows:
Set "network.http.pipelining" to "true"
Set "network.http.proxy.pipelining" to "true"
Set "network.http.pipelining.maxrequests" to some number like 30.



It runs beautifully.

---

### Post by bored2k on 2006-05-20
[CENTER]Xubuntu 6.06 + Opera + uTorrent (wine) = One powerful and wicked light machine.[/CENTER]

---

### Post by G Morgan on 2006-05-20
Opera is great but Firefoxs resource management can improve dramatically with a short trip into about:config. The worse culprit for memory over usage is the fact it stores 8 pages for every tab open when I specifically never use forward and back but just tab everything. Just cut it down to 1 and the resource side improves greatly with little or no slowdown if you do tab everything like me.

Also you can actually cap the memory firefox uses in about:config as well. I'm not sure how to do this though you'd have to search mozillazine.

//edit - I've just read the post above which says exactly the same as what I've said//

---

### Post by Disabled on 2006-05-20
Ok, for all the ones who are trying opera, here is a useful link, with a lot of information on how to use this powerful browser: [30 days to become a opera lover]("http://operalover.tntluoma.com/")

Only one other thing:
Firefox is a 8.1 Mb download, and it gives you only the browser;
Opera is a 5.2 Mb download (the 9 beta) and you get also a Mail client, Bittorrent client, a Presentation Tool (OperaShow), an RSS client, and a lot more... :P

(Yes, i am a opera fan :P)

---

### Post by fuscia on 2006-05-20
if you want fast, try this patched version of dillo - [http://teki.jpn.ph/pc/software/index-e.shtml](http://teki.jpn.ph/pc/software/index-e.shtml)

(it's more useful than regular dillo.)

---

### Post by DigitalDuality on 2006-05-20
[QUOTE=Disabled]Ok, for all the ones who are trying opera, here is a useful link, with a lot of information on how to use this powerful browser: [30 days to become a opera lover]("http://http://operalover.tntluoma.com/")

Only one other thing:
Firefox is a 8.1 Mb download, and it gives you only the browser;
Opera is a 5.2 Mb download (the 9 beta) and you get also a Mail client, Bittorrent client, a Presentation Tool (OperaShow), an RSS client, and a lot more... :P

(Yes, i am a opera fan :P)[/QUOTE]

FF has RSS support..

Opera's bit torrent client is awful on all OSes.

---

### Post by bored2k on 2006-05-20
[QUOTE=DigitalDuality]FF has RSS support..

Opera's bit torrent client is awful on all OSes.[/QUOTE]
I agree. I don't think any serious bittorrent user would use it.

---

### Post by jdong on 2006-05-20
Opera is a pretty cool browser. Undoubtedly it's much less resource intensive than Firefox. I personally prefer Firefox's interface better... Opera's interface just has too much for me to put up with.

I wish Opera was open source too... I still feel more secure using Firefox...

Also, Opera still has rendering issues, especially with AJAX sites like Google Calendar.

---

### Post by ctgray on 2006-05-21
If you want to tweak Firefox you should try [this guide.]("http://www.tweakguides.com/Firefox_1.html") I tried to use Opera but I've become used to the way Firefox works and looks that I just keep it.

---

### Post by sophtpaw on 2006-05-21
[QUOTE=Disabled]Ok, for all the ones who are trying opera, here is a useful link, with a lot of information on how to use this powerful browser: [30 days to become a opera lover]("http://http://operalover.tntluoma.com/")

Only one other thing:
Firefox is a 8.1 Mb download, and it gives you only the browser;
Opera is a 5.2 Mb download (the 9 beta) and you get also a Mail client, Bittorrent client, a Presentation Tool (OperaShow), an RSS client, and a lot more... :P

(Yes, i am a opera fan :P)[/QUOTE]


That link took me to microsoft.com :confused:

There were threee posts in a row about Opera's issues with multimedia for example mplayerplugin etc. Would be great to have a solution to this posted. Instead alot of details of how to make Firefox faster or other fast browsers, hmmm....?

---

### Post by sup on 2006-05-21
> There were threee posts in a row about Opera's issues with multimedia for example mplayerplugin etc. Would be great to have a solution to this posted. Instead alot of details of how to make Firefox faster or other fast browsers, hmmm....?
Well I think it is not easily possible and it might not be for a long time (years or so - if yuo are interested why, try to search opera forums for mplayer plugin)), at least when it comes to linux. This [http://forums.gentoo.org/viewtopic.php?p=3297093#3297093]("http://forums.gentoo.org/viewtopic.php?p=3297093#3297093") gets it semi-work but with no controls like play/pause and it seems to me it odes not play as many videos as firefox does either. Then again, I think Firefox under linux plays fewer videos than opera under Windows.

I personally do not mind since I hardly ever watch videos. 

Also, flash is - at least for me - slower with Opera (beta1, maybe that is the problem, I do not remeber whethet it was as slow for regular 8.5 as well) then with firefox. Otherwise, Opera rocks.

BTW:bittorrent client is not supposed to be used for some serous pirating or anything similar, it is just a tool that does not force you to open an external application when you come across a torrent file on the internet - and I think that it is really neat since I otherwise do not use torrents. ANd it is even better now when it does not rehash the downloading files when Opera is  restarted.

---

### Post by commodore on 2006-05-21
Opera is technically good, but it's not open source! Even if there wouldn't be Firefox I still wouldn't use Opera because I have to support free/ open source software.

---

### Post by RacerII on 2006-05-21
I cant install it , get a dependency problem:

xlib6g/xlibs

Edit: the tar package does seem to work...

---

### Post by papangul on 2006-05-21
If I am not mistaken, this forum runs on non open-source software. And if I remember correctly , someone once had asked ubuntu_geek about that and he replied that he believes there is place for both open source and closed source in real world. 
Anyway, exception is the rule and to me opera is the exception.

---

### Post by papangul on 2006-05-21
[QUOTE=RacerII]I cant install it , get a dependency problem:

xlib6g/xlibs[/QUOTE]
You are using dapper, I guess, click on my sig.

---

### Post by imagine on 2006-05-21
[QUOTE=G Morgan]Opera is great but Firefoxs resource management can improve dramatically with a short trip into about:config. The worse culprit for memory over usage is the fact it stores 8 pages for every tab open[/QUOTE]
Opera caches *every* page you *ever* opened since Opera was started, so that's not really a point for Firefox =)

Opera is a power-browser and I like to refer to it as the vi of the browsers. I use it exclusively since four years and from time to time I still discover things which I didn't know before, even without any extensions.
[There can only be one](http://www.google.com/search?q=Best+browser+on+earth%3F&num=1) =)

---

### Post by Disabled on 2006-05-21
Fixed the link :P And i agree with Sup regarding bittorrent client: if you download 1 file every month or so is very useful :)

Ah, i didn't mentioned the Vocal feature (i don't remember is name) cause you must download a 5 Mb file and the chat cause i think it's only for the windows version.

Regarding the fact opera isn't opensouce... well, i like open source, but it does't mean i'm going to use only open source software. Opera, for my personal taste, is a lot better than Firefox, so i use opera :)

---

### Post by Alpha_toxic on 2006-05-21
> **bored2k][CENTER]Xubuntu 6.06 + Opera + uTorrent (wine) = One powerful and wicked light machine.[/CENTER][/QUOTE]
Same here :), only it's Kubuntu for me  said:**
> Opera is technically good, but it's not open source! Even if there wouldn't be Firefox I still wouldn't use Opera because I have to support free/ open source software.
I personaly don't care that much if a program is OS or not. What matters is does it WORK and HOW it works, and Opera works great. Of course it would be even better if it was OS, but you have to respect a dev's decision to go OS or not. It's his program/source after all. An example I allways give in this case is : a good cheff will never tell you the secrets behind his cooking, though you still eat it and admire him if it tastes good.

---

### Post by zenwhen on 2006-05-21
[QUOTE=imagine]Opera caches *every* page you *ever* opened since Opera was started, so that's not really a point for Firefox =)

Opera is a power-browser and I like to refer to it as the vi of the browsers. I use it exclusively since four years and from time to time I still discover things which I didn't know before, even without any extensions.
[There can only be one](http://www.google.com/search?q=Best+browser+on+earth%3F&num=1) =)[/QUOTE]

This post borders [zealotry]("http://dictionary.reference.com/search?q=zealotry"), and could very likely cause trolling and flaming to occur in this thread. This post was made to state that this thread will be watched for trolling from this point on. Don't let it happen.

---

### Post by G Morgan on 2006-05-21
Nobody is saying Opera isn't a very good browser but Firefox v Opera is exactly the same as Vim v Emacs. Nobody can truely say one is better than the other and the reality is both have their advantages and most people will use whichever one best suits their requirements. As it stands I like extensions so Firefox is my preference. If somebody tells me they prefer ultimate efficiency and aren't too worried about the ability to customise I will point them to Opera.

As for the OSS v proprietry. I believe that the goal should be that an OSS alternative should always be available. As bad as the likes of MS are there will always be a place for proprietry software and some companies are not criminal. Provided that companies do not try for lockins and support open standards I'm happy enough. The day MSO documents can be opened by any productivity suite will be a good one and will as good as be end the monopoly.

---

### Post by ice60 on 2006-05-21
[QUOTE=shuttleworthwannabe]So I was right, Opera does have a multimedia problem. Has anyone figured out how ro fix this: I test on cnn and bbc, and on both I have issues with playing theor videos. FF plays fine. I have all the required codecs installed. Do we have to point Opera to the w32codecs that FF uses?? Like a symlink or something?? I am not a guru, but just making the analogy from other programs.

I am so happy someone has also discovered the power of opera. For me Opera has a small footprint, and light on the resources.

tah[/QUOTE]
if you have problems with media and Opera you can use [Download embeds](http://userjs.org/scripts/general/enhancements/download-embeds) it works with all the BBC stuff.

i did a howto for Opera which shows how to get userjs to work
[http://www.ubuntuforums.org/showthread.php?t=157277](http://www.ubuntuforums.org/showthread.php?t=157277)

---

### Post by whatrucrazy on 2006-05-21
for myself opera is the go when feeling impatient, its is simply so much faster than firefox i just can't help myself.
that said, firefox is superior in almost all other ways: aesthetically, open source, better multimedia support, multiple-tabbed home pages...

if speed is your *only* conern though, the choice would seem clear. 
if only firefox could be sped up to opera levels, then i'd never leave.

---

### Post by shuttleworthwannabe on 2006-05-21
[QUOTE=ice60]if you have problems with media and Opera you can use [Download embeds](http://userjs.org/scripts/general/enhancements/download-embeds) it works with all the BBC stuff.

i did a howto for Opera which shows how to get userjs to work
[http://www.ubuntuforums.org/showthread.php?t=157277](http://www.ubuntuforums.org/showthread.php?t=157277)[/QUOTE]

I am having PITA of a time getting meultimedia to work in Opera, and your suggestion was a relief, but alas, I have to admit I can't get it to work. How do I get it to work. I also install googlesuggest and it works fine, so I know I have the userjs location in opera workking. But when I double-click on the video target, it opens the window (no image no sound) but no option to download. Am i mising somehting?

---

### Post by ice60 on 2006-05-21
[QUOTE=shuttleworthwannabe]I am having PITA of a time getting meultimedia to work in Opera, and your suggestion was a relief, but alas, I have to admit I can't get it to work. How do I get it to work. I also install googlesuggest and it works fine, so I know I have the userjs location in opera workking. But when I double-click on the video target, it opens the window (no image no sound) but no option to download. Am i mising somehting?[/QUOTE]
to get the 'download embeds' to work you have to double-click on the correct part of the window and a new link will appear, so try in a few different places (generally near the top where it should play in an embedded player). in very rare cases the embedded link is invisible. do you have a link?

pretty much most media works for me now apart from things which use the quicktime-plugin (maybe because i use totem for quicktime) that's when i use download-embeds. 

it's probably not connected but the last thing i did to get more things working with Opera was install Mozilla-mplayer (i'd done a few manual things at the same time too, that's why i'm not certain it will help)

---

### Post by shuttleworthwannabe on 2006-05-21
thanks will check

---

### Post by NeoChaosX on 2006-05-21
Is there a way to move the tab bar beneath the address bar in Opera (so it looks like Firefox)? It's a minor nitpick, but I'd jump to Opera in a heartbeat if it could.

---

### Post by ice60 on 2006-05-21
> thanks will check
if you can't get it to work post a link.

BTW, i have mozplugger installed too and a symlink to it here -
```
/usr/lib/opera/plugins
```
the link is from here
```
/usr/lib/mozilla/plugins/mozplugger.so
```

---

### Post by fuscia on 2006-05-21
[QUOTE=NeoChaosX]Is there a way to move the tab bar beneath the address bar in Opera (so it looks like Firefox)? It's a minor nitpick, but I'd jump to Opera in a heartbeat if it could.[/QUOTE]

try under tools>appearance. i think you can, but i can't remember how. there are also some alternate panel setups somewhere on this page - [http://my.opera.com/community/customize/](http://my.opera.com/community/customize/)

---

### Post by sup on 2006-05-22
> pretty much most media works for me now apart from things which use the quicktime-plugin (maybe because i use totem for quicktime) that's when i use download-embeds.
What plugin do you use for multimedia - gxine or mplayer or something else?
There are many possibilities listed here[http://www.opera.com/linux/docs/plugins/]("http://www.opera.com/linux/docs/plugins/"); most of which I never heard of.

---

### Post by Alpha_toxic on 2006-05-22
[QUOTE=NeoChaosX]Is there a way to move the tab bar beneath the address bar in Opera (so it looks like Firefox)? It's a minor nitpick, but I'd jump to Opera in a heartbeat if it could.[/QUOTE]
If you don't use the main bar (99% of people don't), just go to customize and drag-drop all buttons from the address bar to the main bar, then remove all the default buttons from the main bar and set it to "images only".
I've found that Opera is surprisingly customizeable, countrary to what most people think, it just needs a bit of creativity from the user.

---

### Post by ice60 on 2006-05-22
[QUOTE=sup]What plugin do you use for multimedia - gxine or mplayer or something else?
There are many possibilities listed here[http://www.opera.com/linux/docs/plugins/]("http://www.opera.com/linux/docs/plugins/"); most of which I never heard of.[/QUOTE]
hi, i'm using Mplayer. i just did the tests on [this](http://fredrik.hubbe.net/plugger/test.html) page and all the video stuff works for me apart from 'AVI (radius cinepak)', in that case i can double-click on the page and the 'Download EMBED' appears

---

### Post by sup on 2006-05-22
> hi, i'm using Mplayer. i just did the tests on this page and all the video stuff works for me apart from 'AVI (radius cinepak)', in that case i can double-click on the page and the 'Download EMBED' appears

I see, and how did you get it to work? Did you followed these [http://www.opera.com/linux/docs/plugins/install/#mplayer]("http://www.opera.com/linux/docs/plugins/install/#mplayer") instructions or something else? Did you change the source code according to howto that appeared on gentoo forums (link should be in one of earlier posts in this thread)?
Also, do the play/pause buttons and like work for you?

---

### Post by zubrug on 2006-05-22
I learned to love opera when using linspire, it worked perfectly. Have never even thought of switching back.
Really, a seperate browser and email client?

---

### Post by jdong on 2006-05-22
To be more fair in the Opera vs Firefox, OSS vs Proprietary debate, we do have to give Opera some credit for their support of all platforms.

I believe Opera does a great job of supporting Linux and a whole heck of a lot of Linux flavors at that. I think Opera is managing all of its customers with decent respect and regard to individual preferences.


On the note of browser speed, resource usage is clearly and undoubtedly a Firefox flaw, and somewhat due to that, Firefox is not exactly a speed cham either. Quite a bit of the speed hit is due to internationalization-friendliness and future-proofing (pango font rendering and cairo widgets are the main causes for Firefox being so ridiculously slow in Breezy and early Dapper)... I believe Firefox deals with right-to-left languages and other i18n aspects a lot better than Opera does.


Another browser to try is Epiphany if you are looking for a speed boost over Firefox. There are some feature losses, but for the everyday browsing tasks it's worth it IMO. Also, Epiphany uses the Firefox Gecko engine for rendering, so it'll render pages just as well as Firefox.

---

### Post by shuttleworthwannabe on 2006-05-22
I would second jdong on the epiphany suggestion; I rely on Opera for most of the browsing needs, but when I want to view embeded vidoes I use epiphany (until I can get the mutlimedia working in Opera that is).

---

### Post by ice60 on 2006-05-22
[QUOTE=sup]I see, and how did you get it to work? Did you followed these [http://www.opera.com/linux/docs/plugins/install/#mplayer]("http://www.opera.com/linux/docs/plugins/install/#mplayer") instructions or something else? Did you change the source code according to howto that appeared on gentoo forums (link should be in one of earlier posts in this thread)?
Also, do the play/pause buttons and like work for you?[/QUOTE]
i wish i could give you an ABC for what i did, but i made lots of changes over a few months.

all i can say for certain is i installed mozilla-mplayer and mozplugger
```
sudo apt-get install mozilla-mplayer mplayer-fonts mozplugger
```

i also used opera -debugplugin to debug my plugins (i still have some plugin failures, but i'm happy anyway) then looked up any **[plugin failed ]** to see how to fix them.
```
opera -debugplugin
```

i found this thread, i'm not sure if it's been posted here.
[http://my.opera.com/community/forums/topic.dml?id=131761](http://my.opera.com/community/forums/topic.dml?id=131761)

sometimes when i pause things restarting the stream just goes back to the start of the stream again. 

i'm happy with the way things work for me, AFAIK i'm able to watch everything, but perhaps others with the same settings i have would find problems with the setup thinking it could be better ???

---

### Post by bruce89 on 2006-05-22
I can't believe it's not butter!

Sorry, I couldn't resist.

---

