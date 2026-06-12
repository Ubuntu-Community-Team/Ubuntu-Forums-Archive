---
title: "Do you Use Chromium on Linux? Adobe Flash Will Stop Working From April"
date: 2014-01-09
forum: Ubuntu, Linux and OS Chat
---

### Post by philinux on 2014-01-09
[http://www.omgubuntu.co.uk/2014/01/chromium-npapi-flash-dropped-april-2014?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2014/01/chromium-npapi-flash-dropped-april-2014?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

I just spotted this news.

---

### Post by monkeybrain20122 on 2014-01-09
Not only flash, **all media plugins would not work then** (totem, gecko-mediaplayer which finally works for Chrome in 13.10), so there is even less reason to use Chromium (there never was any from my point of view, it is neither here nor there) 

But that would affect Chrome as well because other than flash, nothing else would work in Chrome, including pipelight (for Netflix, and other stuffs like Unity3d and Windows flash for drm content) So I don't know why everyone only focuses on flash, there are other formats on the web too. 

In any case Chrome's flash while up to date cannot play drm contents and hal doesn't work on pepper flash  so it is partially crippled. This move makes even Chrome rather useless on Linux. If you need up to date flash with the bonus of accessing drm contents you can now install pipelight on Firefox and use Windows flash if required (only as a secondary as it loads slower than native flash and some features don't work, I use galternatives to switch) Only Firefox offers a more complete overall experience for internet on Linux.

Good thing that Ubuntu hasn't switched to Chromium as default.

---

### Post by craig10x on 2014-01-09
@phillinux: that explains why Canonical has added the pepperflash plug in for chromium...if you check in synaptic package manager you will see it in your 14.04 development (i noticed it a few weeks ago)...all one has to do is install the package in synaptic and it will extract the plug in from chrome and add it to the chromium browser, so problem solved for both Chrome and Chromium on Ubuntu...

You firefox fans better hope that the new Shumway plug in which will be activated by default in Firefox 27 (coming in February) works well for that browser...
Me...i use Chrome myself, so no worries :D

---

### Post by Copper Bezel on 2014-01-09
I use Chrome exclusively, and I'm not exactly looking forward to not having Silverlight. *Again*&#8203;.

(Not that I think any of these plugin standards are necessary or "good" things, and I'd love a pure HTML5 world even with all the kinks and disadvantages that entails. I just don't like things breaking when I need them in the real world.)

---

### Post by monkeybrain20122 on 2014-01-09
> **craig10x said:**
> 
You firefox fans better hope that the new Shumway plug in which will be activated by default in Firefox 27 (coming in February) works well for that browser...
Me...i use Chrome myself, so no worries :D

As I said it affects not only flash. All NNAPI plugins won't work on  Chrome/Chromium, that include google-talk, totem etc  (e.g)   And you can't even use Chrome's flash on drmed sites  so it is still crippled if up to date. Hal works on Firefox's flash but  not on pepper, the Pipelight work around will no longer work in Chrome,so Chrome/Chromium will  be much crippled experience for Linux users, not sure why you are so smug about it.:)

---

### Post by Copper Bezel on 2014-01-09
There's absolutely no way Google would fail to upgrade their own Talk plugin for their own standards switch. On Linux, the new plugin will doubtless be late as always, but it'll be updated.

The old NNAPI Flash doesn't work reliably on any extant DRM'd sites, either, and Pipelight is still a hack. I hardly consider those *crippling* problems for the browser.

---

### Post by craig10x on 2014-01-09
Surely, they will come up with some 3rd party work arounds...don't you think? (for the other things you mentioned aside from the flash)...
By the way, wasn't being smug...i am hoping the shumway plug in does work well for firefox even though i am personally not a fan of the browser and prefer chrome/chromium...

I certainly wouldn't want your experience to be crippled either...all i meant is that it won't affect me since i use chrome...and as Copper Bezel said, no doubt google will make sure stuff like Talk plug in works on linux...you can be SURE of that...

---

### Post by monkeybrain20122 on 2014-01-09
shumway doesn't work at this point, I have it on Fedora, never works so far.

---

### Post by vasa1 on 2014-01-09
> **craig10x said:**
>  ... all one has to do is install the package in synaptic and it will extract the plug in from chrome and add it to the chromium browser ...
So Chromium users will need to have Chrome installed as well?

---

### Post by monkeybrain20122 on 2014-01-09
> **craig10x said:**
> Surely, they will come up with some 3rd party work arounds...don't you think? (for the other things you mentioned aside from the flash)...
By the way, wasn't being smug...i am hoping the shumway plug in does work well for firefox even though i am personally not a fan of the browser and prefer chrome/chromium...

I certainly wouldn't want your experience to be crippled either...all i meant is that it won't affect me since i use chrome...and as Copper Bezel said, no doubt google will make sure stuff like Talk plug in works on linux...you can be SURE of that...

Well I don't really use Chrome (just occasionally firing up to check if it is still working and for testing things like pipelight) and I hardly need flash (use Viewtube + Linterna Magica to replace flash on most popular sites,--sadly that won't work with Chrome anymore). So no, the change will not cripple **my** experience.:) But many Linux users do use Chrome so it is not good for the Linux platform if a popular browser is incapable of doing things which we expect from browsers. 

I just find it strange that all the discussions focus on flash and in particular Youtube, as Youtube is the least to worry about. It has html5, flash 11.2 works fine and there are apps like minitube and Smtube(smplayer) so even if flash is discontinued tomorrow Youtube wouldn't be an issue. 

And as far as flash goes, I think Pipelight's wine hack is actually better than Chrome's pepper flash (it allows you to use up to date Windows flash on Linux browser when you need it,--I use galternatives as a switch for FF, in Chrome you have to enable/disable in about:plugins) because unlike pepper flash, you can even access drmed contents (but a bit glitchy comparing to native flash when the latter does work,--which is 99% of the time so I need the switch mechanism) But this is not going to work with Chrome any more as it uses NNAPI, --and as long as it works in FF there is less reason to want pepper flash.

---

### Post by ibjsb4 on 2014-01-09
I run 12o4 and I am under the impression that Flash for me is supported till 2017.  Is this still correct?

---

### Post by craig10x on 2014-01-09
@vasa1: if you are planning on moving into 14.04 when it is released, you could still use Chromium and simply install the pepperflash package that Ubuntu added to the software center as of 14.04 and you would be all set...if you are staying on an older version of ubuntu, then you would need Chrome (unless you manually install pepperflash using terminal comands that have been mentioned in various articles i have seen on the web about how to do it...Canonical just made it an easy 1 click install for 14.04)...

@monkeybrain20122: Not all videos play on you tube using html-5, so that could be a problem too...
You say Shumway doesn't work well?  Hmmm that could be a problem for firefox users then...

@lbjsb4: according to that article: the answer is NO...apparently adobe decided to stop support the linux flash plug in as of April of this year...it will still work of course, for some time, but you won't get any security updates for it, and that's not a good thing if you know what i mean...So if you are a firefox user, and shumway isn't working well you may need to consider Chrome for your flash needs...

---

### Post by ibjsb4 on 2014-01-09
> @lbjsb4: according to that article: the answer is NO...apparently adobe  decided to stop support the linux flash plug in as of April of this  year...it will still work of course, for some time, but you won't get  any security updates for it, and that's not a good thing if you know  what i mean...So if you are a firefox user, and shumway isn't working  well you may need to consider Chrome for your flash needs... 						

crap

---

### Post by monkeybrain20122 on 2014-01-09
> **craig10x said:**
> 
@monkeybrain20122: Not all videos play on you tube using html-5, so that could be a problem too...
You say Shumway doesn't work well?  Hmmm that could be a problem for firefox users then...
..

  Viewtube works fine with Youtube, it is just going to get more publicity then. flash 11.2 always works. Minitube works for all channels( maybe except some small private ones) and you don't even need to login for restricted contents. Smtube also works very well. So no, Youtube is not a problem.

---

### Post by craig10x on 2014-01-09
Yeah, i guess you should be ok with that old flash 11.2 until firefox gets shumway squared away better ;)
@lbjsb4: i guess you would be ok if you are using firefox...the old 11.2 i think still has a few more years support...just that it is getting a bit "long in the tooth" (lol)...

Chromium users will want to install pepperflash plug in for sure...Ubuntu makes it easier as of 14.04...they did the work for you...

---

### Post by monkeybrain20122 on 2014-01-09
> **craig10x said:**
> 
@lbjsb4: according to that article: the answer is NO...apparently adobe decided to stop support the linux flash plug in as of April of this year...it will still work of course, for some time, but you won't get any security updates for it, and that's not a good thing if you know what i mean...So if you are a firefox user, and shumway isn't working well you may need to consider Chrome for your flash needs...

That is not true. The article says
> The company stopped direct development of their Flash plugin for Linux  back in 2012. The final release, version 11.2, remains available from  the Adobe website and can be installed through the Ubuntu Software  Centre but, after this coming April, **won&#8217;t work in Chromium-based  browsers**. 

So NAAPi Flash will still be supported til 2017, just that you can't use it on Chromium any more.

---

### Post by monkeybrain20122 on 2014-01-09
> **craig10x said:**
> Yeah, i guess you should be ok with that old flash 11.2 until firefox gets shumway squared away better ;)
@lbjsb4: i guess you would be ok if you are using firefox...the old 11.2 i think still has a few more years support...just that it is getting a bit "long in the tooth" (lol)...

Chromium users will want to install pepperflash plug in for sure...Ubuntu makes it easier as of 14.04...they did the work for you...

In the interim you can even use pipelight to get Windows's flash on FF for the small number of sites that require up to date flash and the funny thing is a couple of sites actually work by merely installing Windows flash without switching to it. For example [www.cp24.com]("http://www.cp24.com") did not worked with 11.2 before but after installing Windows' 11.9 even without switching to it the flash videos start working(right click to check flash version: 11.2) and there are a few other sites that would work (for example adobe's protected contents test site) with this trick but not with pepper flash. Pepper flash doesn't work for drmed contents but Windows' does.

Installing Hal would also make it possible to access drmed flash sites and there is a ppa for Trusty, but Hal doesn't work for pepper flash. So with pepper flash there is basically no way to view things such as Amazon videos.

So in balance even for flash the options on Chrome is rather limited by comparison.

---

### Post by d-cosner on 2014-01-09
I just installed Minitube 2.1.5 on Ubuntu 14.04 from the developers site. I watch a lot of music videos on YouTube and Minitube works very well.

---

### Post by monkeybrain20122 on 2014-01-09
> **d-cosner said:**
> I just installed Minitube 2.1.5 on Ubuntu 14.04 from the developers site. I watch a lot of music videos on YouTube and Minitube works very well.

Yep, only catch about minitube is that you have to compile it yourself (takes about 5 minutes) or pay $4 to get it from USC. :)  (the free version is out of date and broken, it should be removed from the repo) I don't mind donating to the guy even though I compiled.

---

### Post by d-cosner on 2014-01-09
It was free but there was a donation button. I did not have to compile Minitube, I selected the Software Center to install the package. The version currently in the 14.04 repos is way out of date and has not worked for a long time.

---

### Post by monkeybrain20122 on 2014-01-09
> **d-cosner said:**
> It was free but there was a donation button. I did not have to compile Minitube, I selected the Software Center to install the package. The version currently in the 14.04 repos is way out of date and has not worked for a long time.

There is an up to date version in the Ubuntu Software Centre by the name "minitube-ubuntu" (rather than just 'minitube') maintained by the developer himself and it costs $4. It is free if you grab the source code from the website and compile yourself (with the button if you want to donate)

Edited: OK, just checked the USC and it is free now. It was $3.99 last I checked..  I don't understand why it says the license is proprietary as the source codes are available under gpl3. I have compiled it (2.1.5) and all the features work.

---

### Post by Copper Bezel on 2014-01-09
> **monkeybrain20122 said:**
> So with pepper flash there is basically no way to view things such as Amazon videos.
It's interesting, since Chrome on Windows is meant to use Pepper as well. NNAPI isn't allowed in the Metro environment. Perhaps content providers like Amazon should simply stop using silly hacks to protect their content if they actually want to make it available to their customers. Given they haven't even released a video Cloud Player for Android, I'm not holding my breath.

---

### Post by monkeybrain20122 on 2014-01-09
> **Copper Bezel said:**
> It's interesting, since Chrome on Windows is meant to use Pepper as well. NNAPI isn't allowed in the Metro environment. Perhaps content providers like Amazon should simply stop using silly hacks to protect their content if they actually want to make it available to their customers. Given they haven't even released a video Cloud Player for Android, I'm not holding my breath.

I meant to say pepper flash on Linux.I suppose the Windows build would have drm capability enabled.

---

### Post by mips on 2014-01-09
Does not bother me, been using pepper in chromium. The day flash dies cannot come to soon :biggrin:

---

### Post by craig10x on 2014-01-09
It's probably why Canonical has added easy one click install of pepperflash for Chromium in 14.04...i guess they must have heard about it before we did ;)

---

### Post by ianmillington on 2014-01-24
Great in principle but as the Pepper Plugin for Linux doesn't support DRM it would appear you can forget sites like Chanel 4)D and Demand 5. Also, ironically, google movies it would appear.

---

