---
title: "Google Chromium browser alpha for Linux"
date: 2009-05-23
forum: The Cafe
---

### Post by hyperdude111 on 2009-05-23
After many months of seeing the "This browser is not ready yet"


[IMG]http://www.linuxnewbieguide.org/userfiles/chromium.jpg[/IMG]


message informing you that it is a pre-alpha todays daily comes with the news  that chromium is now in the alpha stages. As a browser it does seem faster and cleaner looking than firefox.

As resources go of [www.google.com](www.google.com) chrome uses 12mb of RAM and firefox uses 86mb. 

All im waiting for now are the full menus and some plugins then it might become my main browser. 

I have noticed no big changes since the last daily but this is still a huge milestone towards "Google Chrome Linux".

**You can use the instructions to get the daily from their site or follow this [http://www.shivaranjan.com/2009/05/17/linux-how-to-install-chromium-google-chrome-web-browser-in-ubuntu-linux/](http://www.shivaranjan.com/2009/05/17/linux-how-to-install-chromium-google-chrome-web-browser-in-ubuntu-linux/) guide.

---

### Post by Warpnow on 2009-05-23
Isn't chromium just crossover chrome?

---

### Post by Sashin on 2009-05-23
No it's not. Crossover chrome is a windows port, this is the real native deal in alpha form.

Chromium is basically what chrome is before the logo goes on it. It's actually from Google.

---

### Post by sarah.fauzia on 2009-05-23
I think there are two versions, one of which is the CrossOver one and the other native using GTK. I'm not entirely sure, but I am hazarding that that is the case because in the screenshot, the browser appears to be using the native font.

---

### Post by ghindo on 2009-05-23
Little by little, step by step, Chrome is coming to Linux.  Thanks for the update!  Very exciting.

---

### Post by binbash on 2009-05-23
There are no 2 versions.Crossover one is using Google Chrome windows which is not native.Chromium is not Google Chrome.Stop calling chrome chrome chrome

---

### Post by Sashin on 2009-05-23
Chromium will be chrome when it's ready.

---

### Post by lovinglinux on 2009-05-23
I don't see anything about being alpha, just pre-alpha, which is already for days. Anyways, I still prefer Firefox with chromifox theme (see attach). I'm completely addicted to Firefox's extensions.

---

### Post by Tibuda on 2009-05-23
> **binbash said:**
> There are no 2 versions.Crossover one is using Google Chrome windows which is not native.Chromium is not Google Chrome.Stop calling chrome chrome chrome

Is the other way. Chrome is Chromium + Google logo.

---

### Post by marijus on 2009-05-23
you can get it here:
[https://edge.launchpad.net/~chromium-daily/+archive/ppa]("https://edge.launchpad.net/~chromium-daily/+archive/ppa")

i'm impressed.
check it out!

---

### Post by super.rad on 2009-05-23
No native 64 bit, shame as I keep hearing a lot about it but I have no 32bit apps installed so want to keep it that way

---

### Post by hyperdude111 on 2009-05-23
> **lovinglinux said:**
> I don't see anything about being alpha, just pre-alpha, which is already for days. Anyways, I still prefer Firefox with chromifox theme (see attach). I'm completely addicted to Firefox's extensions.
 
See my screenshot it says alpha.

---

### Post by biji on 2009-05-23
hmm no 64bit version.. but will try that :)

---

### Post by BXCracer on 2009-05-23
Wont even start for me. Shows "Illegal instruction" error.

---

### Post by biji on 2009-05-23
run very well and it is very fast!.. but some feature is still missing

---

### Post by xebian on 2009-05-23
> **biji said:**
> hmm no 64bit version.. but will try that :)

There is a 64-bit build, but it requires the ia32-libs.

---

### Post by davideotape on 2009-05-23
```
david@david-desktop:~$ chromium
The program 'chromium' is currently not installed.  You can install it by typing:
sudo apt-get install chromium
bash: chromium: command not found

david@david-desktop:~$ sudo apt-get install chromium
Reading package lists... Done
Building dependency tree       
Reading state information... Done
chromium is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

david@david-desktop:~$ chromium
The program 'chromium' is currently not installed.  You can install it by typing:
sudo apt-get install chromium
bash: chromium: command not found
david@david-desktop:~$ 

```

Any ideas? Chromium doesn't seem to be appering in my menus either.

---

### Post by mellowd on 2009-05-23
> **davideotape said:**
> ```
david@david-desktop:~$ chromium
The program 'chromium' is currently not installed.  You can install it by typing:
sudo apt-get install chromium
bash: chromium: command not found

david@david-desktop:~$ sudo apt-get install chromium
Reading package lists... Done
Building dependency tree       
Reading state information... Done
chromium is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

david@david-desktop:~$ chromium
The program 'chromium' is currently not installed.  You can install it by typing:
sudo apt-get install chromium
bash: chromium: command not found
david@david-desktop:~$ 

```

Any ideas? Chromium doesn't seem to be appering in my menus either.


Add this to /etc/apt/sources.list first

deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main


Then run an apt-get update and try again

---

### Post by philinux on 2009-05-23
```
chromium-browser
```

It appeared under Internet on mine. I just downloaded the ia32 deb and the browser deb.

---

### Post by ronacc on 2009-05-23
how did you install it ? I added the PPA to my software sources  with synaptic , reloaded and it installed ok .
observations : takes a long time to start but very fast once it does .

---

### Post by philinux on 2009-05-23
> **ronacc said:**
> how did you install it ? I added the PPA to my software sources  with synaptic , reloaded and it installed ok .
observations : takes a long time to start but very fast once it does .

Mine started from cold in less than 2 seconds flat. Loaded sky news website in a flash too. Way faster than firefox.

---

### Post by ronacc on 2009-05-23
maybe its because I'm 64bit and it was the first start , it thrashed my HD pretty good starting up , yes that was it I just shut it down and restarted and it was as you said the second start , and it seems even faster loading pages than Opera .It will be interesting to see if it remains that fast when its fully functional .

---

### Post by Regenweald on 2009-05-23
What's the reason for no native 64 bit ? I mean, for software developed within the last year and a half. Why still 32 bit dependence ?

---

### Post by philinux on 2009-05-23
> **ronacc said:**
> maybe its because I'm 64bit and it was the first start , it thrashed my HD pretty good starting up , yes that was it I just shut it down and restarted and it was as you said the second start , and it seems even faster loading pages than Opera .It will be interesting to see if it remains that fast when its fully functional .

I'm 64 bit and cold start was less than 2 seconds. Maybe something else like cron was running just as you started chromium.

---

### Post by mellowd on 2009-05-23
> **Regenweald said:**
> What's the reason for no native 64 bit ? I mean, for software developed within the last year and a half. Why still 32 bit dependence ?

Bigger install base?   it'll come eventually

---

### Post by davideotape on 2009-05-23
> **mellowd said:**
> Add this to /etc/apt/sources.list first

deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main


Then run an apt-get update and try again

Done that, but I edited out the deb-src bit. Is that what's causing the problem?

---

### Post by MacUntu on 2009-05-23
And it has any bad data octopus code removed? :D

---

### Post by lovinglinux on 2009-05-23
> **hyperdude111 said:**
> See my screenshot it says alpha.

I did, but my chromium still says pre-alpha and I didn't notice any changes. I'm using the official PPA for updates. Should I do anything else?

---

### Post by hyperdude111 on 2009-05-23
> **lovinglinux said:**
> I did, but my chromium still says pre-alpha and I didn't notice any changes. I'm using the official PPA for updates. Should I do anything else?

I'm using the daily PPA. If you are too try to update, if not change your ppa

---

### Post by lovinglinux on 2009-05-23
> **hyperdude111 said:**
> I'm using the daily PPA. If you are too try to update, if not change your ppa

Never mind. I've purged it and installed again. Now it says alpha like yours. Thanks. I will test to see what have changed.

I have another question. I like the concept of running each tab as a separate process, so if one tab crashes, you can still keep the others running. But how would I know which process to kill in case a tab crashes?

---

### Post by jmmL on 2009-05-23
> **davideotape said:**
> Done that, but I edited out the deb-src bit. Is that what's causing the problem?

My guess is that you're trying to install chromium, which is an arcade-style shooter if I remember correctly. You'll want to ```
apt-get install chromium-browser
```

---

### Post by albinootje on 2009-05-23
> **davideotape said:**
> 
Any ideas? Chromium doesn't seem to be appering in my menus either.

The package is called chromium-browser, not to confuse with another chromium :
```

$ apt-cache show chromium
--- cut ---
Description: fast paced, arcade-style, scrolling space shooter

```

---

### Post by Dougie187 on 2009-05-23
Seems to work great. And the chrome experiments work really well in it as well.

---

### Post by jmmL on 2009-05-23
Just decided to actually try it myself. They finally removed the dependency on msttcorefonts!

---

### Post by davideotape on 2009-05-23
> **albinootje said:**
> The package is called chromium-browser, not to confuse with another chromium :
```

$ apt-cache show chromium
--- cut ---
Description: fast paced, arcade-style, scrolling space shooter

```

Thanks for that, installed chromium-browser instead :P

Very quick for me, but without flash or gears it offers no big advantages over firefox for me at the moment. Shame that the top window border is still there, as that's one of the things I liked about google chrome on windows.

---

### Post by Giant Speck on 2009-05-23
I noticed yesterday that Chromium wasn't trying to use my GTK colors anymore, but was using my font.

I also noticed that Google added an option (so far the *only* options in the options menu) to automatically send usage statistics and crash reports to Google.  To the conspiracy theorists on the forum, this option is not checked by default.

I'm installing today's update right now.

---

### Post by Wiiboy on 2009-05-23
Hey,
The check box doesn't do anything.  It's just there.  

If you click it, and close the browser, it's unchecked when you start up again.

---

### Post by lovinglinux on 2009-05-23
Importing bookmarks still doesn't work.

---

### Post by OutOfReach on 2009-05-23
> **lovinglinux said:**
> Importing bookmarks still doesn't work.

really? I managed to import my firefox bookmarks long ago

---

### Post by lovinglinux on 2009-05-23
> **OutOfReach said:**
> really? I managed to import my firefox bookmarks long ago

I figured it out. It only imports from the Default profile.

---

### Post by ghindo on 2009-05-23
> **danielrmt said:**
> Is the other way. Chrome is Chromium + Google logo.Kind of.  Chrome is Chromium in addition to Google branding and Google data mining technologies.

---

### Post by Giant Speck on 2009-05-23
> **ghindo said:**
> Kind of.  Chrome is Chromium in addition to Google branding and Google data mining technologies.

Chrome really doesn't do much data mining by default.  Now if you were to check the box in options to allow Google to receive usage statistics and crash reports and if you kept Google as the default search engine, then maybe Google would get more information.  Most of the information that is exchanged between Google and the user is actually traveling *from *Google *to *the user, rather than the other way around.

---

### Post by CJ Master on 2009-05-23
> **lovinglinux said:**
> I don't see anything about being alpha, just pre-alpha, which is already for days. Anyways, I still prefer Firefox with chromifox theme (see attach). I'm completely addicted to Firefox's extensions.

Off topic, but does that theme blur the title bar like in vista?

---

### Post by Giant Speck on 2009-05-23
> **CJ Master said:**
> Off topic, but does that theme blur the title bar like in vista?

It's actually a Compiz plugin that creates the blur effect, and not a particular theme.  You can make any theme do the blur effect, as long as you have supported hardware (read: not an Intel graphics card :().

---

### Post by lovinglinux on 2009-05-23
> **Giant Speck said:**
> It's actually a Compiz plugin that creates the blur effect, and not a particular theme.  You can make any theme do the blur effect, as long as you have supported hardware (read: not an Intel graphics card :().

Yes. That's right. You need to enable "Compiz Decoration Blur Type" in the "Emerald Settings" and the "Blur Windows" plugin in Compiz.

---

### Post by CJ Master on 2009-05-23
> **lovinglinux said:**
> Yes. That's right. You need to enable "Compiz Decoration Blur Type" in the "Emerald Settings" and the "Blur Windows" plugin in Compiz.

Ah, great. Thanks, both of you. :)

---

### Post by ghindo on 2009-05-23
> **Giant Speck said:**
> Chrome really doesn't do much data mining by default.  Now if you were to check the box in options to allow Google to receive usage statistics and crash reports and if you kept Google as the default search engine, then maybe Google would get more information.  Most of the information that is exchanged between Google and the user is actually traveling *from *Google *to *the user, rather than the other way around.It's a bit more than that:

[http://en.wikipedia.org/wiki/Google_chrome#Usage_tracking](http://en.wikipedia.org/wiki/Google_chrome#Usage_tracking)

---

### Post by Giant Speck on 2009-05-23
> **ghindo said:**
> It's a bit more than that:

[http://en.wikipedia.org/wiki/Google_chrome#Usage_tracking](http://en.wikipedia.org/wiki/Google_chrome#Usage_tracking)

Four out of those five tracking methods are optional.  The non-optional option, the RLZ identifier, seems pretty benign:

> 
You may notice a RLZ parameter in the URL when you do a Google search from the Google Chrome address bar. The RLZ parameter contains some encoded information (like when you downloaded Google Chrome and where you got it from). The RLZ parameter does not uniquely identify you nor is it used to target advertising. Google uses this information in aggregate to find out whether groups of people are using Google Chrome actively. Not all users have the same RLZ parameter. The RLZ parameter is based on where Google Chrome was download from, when it was installed, and when certain features were first used, like search.

 A RLZ parameter is sent to Google with every search done using the built-in search box. It is also sent separately on days when Google Chrome has been used or when certain significant events occur such as a successful installation of Google Chrome. The RLZ parameter is stored in the registry and may be updated from time to time. The code that makes this work is not included in the open source project ([http://www.chromium.org]("http://www.chromium.org/")) because it only applies to the version of the browser that Google distributes, Google Chrome.

---

### Post by dragos240 on 2009-05-23
> **lovinglinux said:**
> I don't see anything about being alpha, just pre-alpha, which is already for days. Anyways, I still prefer Firefox with chromifox theme (see attach). I'm completely addicted to Firefox's extensions.

Is that 7 or ubuntu with 7 theme. If it's ubuntu, it's very convincing.

---

### Post by Giant Speck on 2009-05-23
> **dragos240 said:**
> Is that 7 or ubuntu with 7 theme. If it's ubuntu, it's very convincing.

It's Ubuntu.  The panel and the scrollbars give it away.  :)

---

### Post by geoken on 2009-05-23
> **hyperdude111 said:**
> 
As resources go of [www.google.com](www.google.com) chrome uses 12mb of RAM and firefox uses 86mb. 

But Firefox's memory seems more stable. Chrome, and it's multi-process nature, seems to add 10 or more mb per tab. When I first start Chrome and FF my experiences are similar to yours, 20mb for Chrome and 80 for FF (when you said 11mb for chrome did you check the second process? over here Chrome launches with two processes, one taking up a hair under 12mb and one using a little over 8). I open 4 tabs in FF (Google, Digg, Ars and these forums) and the memory only jumps up by 2mb. I then open those same tabs in Chrome and the memory jumps to 80mb.

Here is a screen shot showing both chrome and firefox with the 4 afformentioned tabs open.

[IMG]http://i5.photobucket.com/albums/y169/geoken/chrome_tabs.jpg[/IMG]

---

### Post by ghindo on 2009-05-23
In addition, installing Google Chrome (at least on Windows) means that the Google Update service is running all the time.  That might not be the case for the Mac and Linux builds, but it sure is a pain with the Windows build.

---

### Post by Giant Speck on 2009-05-23
Is there an unbranded version of Chrome for Windows?  Is it possible to just use Chromium?

---

### Post by itreius on 2009-05-23
> **Giant Speck said:**
> Is there an unbranded version of Chrome for Windows?  Is it possible to just use Chromium?
[http://build.chromium.org/buildbot/snapshots/chromium-rel-xp/?C=M;O=D](http://build.chromium.org/buildbot/snapshots/chromium-rel-xp/?C=M;O=D)

Note that those are not stable versions.

---

### Post by lovinglinux on 2009-05-23
> **dragos240 said:**
> Is that 7 or ubuntu with 7 theme. If it's ubuntu, it's very convincing.

It's Ubuntu. I'm not exactly trying to mimic Windows 7, but actually making it look good with Firefox Chromifox theme. Until a few days ago my theme was a modified Dust Sand theme. But unfortunately, I'm never satisfied with the results. I don't like themes too bright or too dark and I usually end up with a dull [shade of grey](http://fmc.isgreat.org/). Since I use Firefox for a lot of stuff, I 'm trying to adapt my gtk/emerald theme to blend nicely with chromium colors. 

The theme currently used is a customized Clearlooks, with a modified "[Who Needs Windows 7?](http://compiz-themes.org/content/show.php/Who+Needs+Windows+7+%3F?content=105399)" emerald theme. The wallpaper is from Windows 7 until I get bored with it.

EDIT: attached another screenshot showing Nautilus and a piece of Firefox

---

### Post by michael37 on 2009-05-23
Do you recommend using version chromium_browser_2.0.x or chromium_browser_3.0.x from the daily builds for testing?

---

### Post by BwackNinja on 2009-05-23
Pics or it didn't happen!

---

### Post by Sashin on 2009-05-24
It was much better when it's fonts rendered properly and also when it used GTK colours.

---

### Post by mainalisuyog on 2009-05-24
that screenshot, would you mind telling me what the "watch tv" application is, and also, the lyrics conky you have.

---

### Post by Foaming Draught on 2009-05-24
Well OK, it is fast, but we're talking a fraction of a second or a second.  My add-ons and being able to navigate around Firefox with my eyes closed make Firefox incomparably more useful.  Nice to be able to keep an eye on Chromium, though.

---

### Post by MacUntu on 2009-05-24
To repeat my question: was the code reviewed? Can I be sure there's no Google voodoo hidden that collects all my important data like what porn I favor?

---

### Post by ghindo on 2009-05-24
> **xebian said:**
> There is a 64-bit build, but it requires the ia32-libs.What does that entail?

---

### Post by plun on 2009-05-24
> **MacUntu said:**
> To repeat my question: was the code reviewed? Can I be sure there's no Google voodoo hidden that collects all my important data like what porn I favor?

Just use "prOn-mode" >>  open a new incognito window...:D):P

---

### Post by sdowney717 on 2009-05-24
would google end up using any of this code in coming up with their own linux version?
Just how far are the code writers working on it now  willing to take chromium?
It is really fast.
If it supported plugins, add block, and I like to auto scroll with the mouse middle button, It could become the default browser.

---

### Post by sdowney717 on 2009-05-24
How do you like these images?

[IMG]http://farm4.static.flickr.com/3053/2823841098_5f31359a17.jpg?v=0[/IMG]

[IMG]http://www.adobetutorialz.com/content_images/AdobePhotoshop/ART-D/tutorial431/google-chrome-logo-design.jpg[/IMG]

---

### Post by philinux on 2009-05-24
> **ghindo said:**
> What does that entail?

[https://edge.launchpad.net/~chromium-daily/+archive/ppa/+files/ia32-libs-chromium-browser_0.01~ucd6~jaunty_amd64.deb](https://edge.launchpad.net/~chromium-daily/+archive/ppa/+files/ia32-libs-chromium-browser_0.01~ucd6~jaunty_amd64.deb)

Install that first, if you are using Jaunty thats all. From the link on the first post it's all there, all the versions are there.

---

### Post by -grubby on 2009-05-24
It's working about as well as the Windows version here, and I'm running on 64-bit.

---

### Post by plun on 2009-05-24
> **sdowney717 said:**
> How do you like these images?



Well, thats Google Chromes logo and not Chromium....

Chromium uses a blue one.


[[img]http://ubuntu-pics.de/thumb/14960/snapshot8_Cdcv7U.png[/img]](http://ubuntu-pics.de/bild/14960/snapshot8_Cdcv7U.png)

;)

---

### Post by BwackNinja on 2009-05-24
> **mainalisuyog said:**
> that screenshot, would you mind telling me what the "watch tv" application is, and also, the lyrics conky you have.
OT:
Its just a script that runs smplayer with special options for my tv tuner. And that's not conky, just some simple pygtk [http://ubuntuforums.org/showpost.php?p=7338453&postcount=1215](http://ubuntuforums.org/showpost.php?p=7338453&postcount=1215)

---

### Post by cl333r on 2009-05-24
Did anyone notice that it's already version 3? I thought they're trying to bring the 2nd version to Linux.

---

### Post by Nullack on 2009-05-24
> **MacUntu said:**
> To repeat my question: was the code reviewed? Can I be sure there's no Google voodoo hidden that collects all my important data like what porn I favor?

Wikipedia has a damming section on not being able to turn off a "feature" google put into Chrome. Dont know if its in Chrominium or not. Its concerning, for sure. Unless I see evidence to the contrary, Id say its still in there.

---

### Post by xebian on 2009-05-24
> **MacUntu said:**
> To repeat my question: was the code reviewed? ...?

Wot?  Aren't you supposed to?  ):P

---

### Post by MacUntu on 2009-05-25
Yeah, because I'm a code guru? :D

---

### Post by paradigm2 on 2009-05-25
> **sdowney717 said:**
> would google end up using any of this code in coming up with their own linux version?
Just how far are the code writers working on it now  willing to take chromium?
It is really fast.
If it supported plugins, add block, and I like to auto scroll with the mouse middle button, It could become the default browser.

The beauty of it is that anyone who is capable can help take it as far as they wish.  It is an open source project.  I wish I had the time and skill to help in the efforts now but unfortunately I have neither.

---

### Post by paradigm2 on 2009-05-25
> **cl333r said:**
> Did anyone notice that it's already version 3? I thought they're trying to bring the 2nd version to Linux.

Keep in mind this is chromium, not Chrome.  Chrome is merely based off of Chromium.

---

### Post by plun on 2009-05-28
I took the time and benchmark Chromium against Minefield

[[img]http://ubuntu-pics.de/thumb/15227/snapshot10_Ob1Olc.png[/img]](http://ubuntu-pics.de/bild/15227/snapshot10_Ob1Olc.png)

Intel E5200 and 2 GB Ram, Minefield is running with everything inside a ramfs, Chromium is extremely fast.....;)

Benchmarking tool
[http://service.futuremark.com/peacekeeper/index.action](http://service.futuremark.com/peacekeeper/index.action)

--

---

### Post by binbash on 2009-05-28
Chromium does not have plugins/add-ons, even an options page (not the null one :) ).It does not handle htaccess passwords and long list long list long list.Your benchmark is pretty useless.

---

### Post by plun on 2009-05-28
> **binbash said:**
> Your benchmark is pretty useless.

Well, Futuremarks benchmark is a "real world" tool.....  ;)

I can also notice this when I run Chromium.... just excellent !

---

### Post by davideotape on 2009-05-28
Just for kicks I did a little benchmarking myself. My results are attached. I've got an Intel(R) Core 2 CPU 6300 @ 1.86GHz, 2GB of DDR2 ram and a nvidia 9400gt, with BOINC running in the background.

Edit: Just performed acid 3 tests on each of the browsers. Results:

Firefox: 71
Chromium: 100 (but linktest failed)
Epiphany: 71
Opera: 85
Minefield: 94

(All scores are out of 100)

---

### Post by binbash on 2009-05-28
> **plun said:**
> Well, Futuremarks benchmark is a "real world" tool.....  ;)

I can also notice this when I run Chromium.... just excellent !

This does not matter.It will run faster, it does run faster on me also (3x) BUT this does not mean it will run faster when it is done  :)

---

### Post by plun on 2009-05-28
> **binbash said:**
> This does not matter.It will run faster, it does run faster on me also (3x) BUT this does not mean it will run faster when it is done  :)

Well I hope so  ;)...and that Mozilla devs maybe speeds up the linux-version of Firefox, something isn't good enough, I am also using a RAM disk for Firefox and its slower....

---

### Post by albinootje on 2009-05-28
> **plun said:**
> Well I hope so  ;)...and that Mozilla devs maybe speeds up the linux-version of Firefox, something isn't good enough, I am also using a RAM disk for Firefox and its slower....

Firefox 3.5 is suppose to do some Linux optimizing I've read. 

And to "the testers" in this thread : What about SwiftFox ? Why don't you test that too ?
And Midori, and other WebKit based browsers ?

---

### Post by davideotape on 2009-05-28
> **albinootje said:**
> Firefox 3.5 is suppose to do some Linux optimizing I've read. 

And to "the testers" in this thread : What about SwiftFox ? Why don't you test that too ?
And Midori, and other WebKit based browsers ?

Will do when I get back on my ubuntu machine :)

---

### Post by cl333r on 2009-05-28
> **albinootje said:**
> Firefox 3.5 is suppose to do some Linux optimizing I've read. 

So far it's just (slashdot and other) rumors. Check the latest 3.5 build on same computer with Linux and windows and see for yourself.

If there are plans for optimizations for Linux they won't make it into Firefox 3.5 cause Mozilla is prepping the RC already.

---

### Post by davideotape on 2009-05-29
> **albinootje said:**
> Firefox 3.5 is suppose to do some Linux optimizing I've read. 

And to "the testers" in this thread : What about SwiftFox ? Why don't you test that too ?
And Midori, and other WebKit based browsers ?

Can't test swiftfox because it acts like normal firefox. New results attached. And midori got 100 on acid 3.

---

### Post by albinootje on 2009-05-29
> **davideotape said:**
> Can't test swiftfox because it acts like normal firefox. New results attached. And midori got 100 on acid 3.

Interesting, thanks. :)

---

### Post by davideotape on 2009-05-29
> **albinootje said:**
> Interesting, thanks. :)

No problem ;) Any other browsers you'd like me to test whilst I'm at it?

---

### Post by albinootje on 2009-05-29
> **davideotape said:**
> No problem ;) Any other browsers you'd like me to test whilst I'm at it?

There's kazehakase, links2 (start with "links2 -g", and then "escape" to make the menus visible), and arora.

And where's the benchmark testing located, actually ?

---

### Post by davideotape on 2009-05-29
Testing is here: [http://service.futuremark.com/peacekeeper/index.action](http://service.futuremark.com/peacekeeper/index.action)

Results here: [http://spreadsheets.google.com/ccc?key=rSY4wLoH3DRwap3AmpAFKJQ](http://spreadsheets.google.com/ccc?key=rSY4wLoH3DRwap3AmpAFKJQ)

---

### Post by super.rad on 2009-05-29
Just running that test in a few browsers now, my results were (sorry no fancy spreadsheets like david lol)

Browser  --  Peacekeeper (Overall Score)  --  Acid3
Midori  --  3245  --  100
Arora  --  2580  --  98
Konqueror  --  1596  --  87
Kazehakase (Gecko  --  1237  --  71
Epiphany   --  1229  --  71
Shiretoko 3.5b4  --  1213  --  93
Firefox 3.0.10  --  1006  --  71
Kazehakase (Webkit)  --  Crashed  --  99

Some reason when using Kazehakase with the webkit backend as soon as I started the benchmarks it just closed
Didn't test Chrome as I'm on 64bit so don't want to install all the 32bit lib's just for a browser
Similar results to david although everything scored higher on mine (computer is a brand new build though) and kazehakase and epiphany were both above firefox for me

---

### Post by albinootje on 2009-05-29
> **davideotape said:**
> Testing is here: [http://service.futuremark.com/peacekeeper/index.action](http://service.futuremark.com/peacekeeper/index.action)

Results here: [http://spreadsheets.google.com/ccc?key=rSY4wLoH3DRwap3AmpAFKJQ](http://spreadsheets.google.com/ccc?key=rSY4wLoH3DRwap3AmpAFKJQ)

Thank you.

---

### Post by vishalrao on 2009-05-30
LOL @ [http://spot.livejournal.com/308370.html](http://spot.livejournal.com/308370.html)

:lolflag:

---

### Post by davideotape on 2009-05-30
> **vishalrao said:**
> LOL @ [http://spot.livejournal.com/308370.html](http://spot.livejournal.com/308370.html)

:lolflag:

LMAO. :lol:

---

### Post by ktp on 2009-05-30
> **vishalrao said:**
> LOL @ [http://spot.livejournal.com/308370.html](http://spot.livejournal.com/308370.html)

:lolflag:

:lolflag:

---

### Post by davideotape on 2009-05-30
> **super.rad said:**
> Similar results to david although everything scored higher on mine (computer is a brand new build though) and kazehakase and epiphany were both above firefox for me


Probbably cause I've got BOINC running I'm the background 24/7. And my pc is a bit old now.

---

### Post by perito on 2009-05-30
hi,
I wanted to ask if anyone knows when Google is planning to release the Linux version of Google Chrome: [http://www.google.com/chrome/intl/en/linux.html](http://www.google.com/chrome/intl/en/linux.html)

Also, what is the difference between the browser posted in the first post in this topic and the following: [http://codefighters.blogspot.com/2009/02/google-chrome-for-linux-users.html](http://codefighters.blogspot.com/2009/02/google-chrome-for-linux-users.html)

Finally, I wanted to ask if Ubuntu developers are considering making Google Chrome the default web browser of Ubuntu instead of Firefox?

Thanks

---

### Post by davideotape on 2009-05-30
> **perito said:**
> hi,
I wanted to ask if anyone knows when Google is planning to release the Linux version of Google Chrome: [http://www.google.com/chrome/intl/en/linux.html](http://www.google.com/chrome/intl/en/linux.html)

Also, what is the difference between the browser posted in the first post in this topic and the following: [http://codefighters.blogspot.com/2009/02/google-chrome-for-linux-users.html](http://codefighters.blogspot.com/2009/02/google-chrome-for-linux-users.html)

Finally, I wanted to ask if Ubuntu developers are considering making Google Chrome the default web browser of Ubuntu instead of Firefox?

Thanks

1. No one knows when chrome will appear for Linux. I've been signed up to the mailing list since the windows release, and haven't received anything.

2. I highly doubt the devs are even considering chromium as default, becasue firefox is a lot more mature, stable and has plugins.

---

### Post by Eestlane on 2009-05-30
No Chromium, but as the test results got popular already...

(CPU: Intel Pentium 4
GPU: ATI Radeon 9800 Pro
OS: Windows XP SP3)

---

### Post by Darkshade on 2009-05-30
If someone's interested in performance on slower computers see attached image and let me know if you want me to test another browser.

p.s. Seamonkey isn't included in the results because it kept crashing while performing the test.

---

### Post by hyperdude111 on 2009-05-31
After a couple of threads blog posts and even a lifehacker article saying chromeium linux had moved into alpha, well no more.

The latest daily instead of saying chromium alpha it says Chromium Dev Build, and the word alpha can no longer be found in the splash.

This is the new message.

Chromium Dev Build

```
This is an in-progress build of Chromium on Linux. The following significant chunks of functionality are known to be missing:
```

---

### Post by Sand &amp; Mercury on 2009-05-31
Even if it's not officially dubbed alpha, it's still in an alpha state for sure. They are making progress though. 'Development build' could mean alpha, or beta or pretty much anything pre release.

---

### Post by Giant Speck on 2009-05-31
I also noticed that this build is about five megabytes smaller than usual.

---

### Post by hyperdude111 on 2009-05-31
They were all about 20mb until this week whee they're about 15

---

### Post by speedwell68 on 2009-05-31
Things are begining to start happening with it.  You can customise your homepage and stuff now.

---

### Post by Giant Speck on 2009-05-31
> **speedwell68 said:**
> Things are begining to start happening with it.  You can customise your homepage and stuff now.

I tried that, but it didn't save my preferences.

---

### Post by Sand &amp; Mercury on 2009-05-31
Looks like they've been doing work on the options part of the browser. 'Basics' page has stuff to choose from now. I really am digging Chromium, I may end up using it as my default when it's done.

---

### Post by Hells_Dark on 2009-05-31
What a great dev team !

(But I still can't stand the tab bar blue :p)

---

### Post by ubulette on 2009-05-31
> **BXCracer said:**
> Wont even start for me. Shows "Illegal instruction" error.

strange, do you have an old processor without SSE2? I supposedly fixed that weeks ago but noone reported me anything since.
But maybe it's something else for you.

Could you please get me a proper backtrace?

I've written an how-to there: [https://wiki.ubuntu.com/Chromium/Debug](https://wiki.ubuntu.com/Chromium/Debug)

---

### Post by ubulette on 2009-05-31
> **super.rad said:**
> No native 64 bit, shame as I keep hearing a lot about it but I have no 32bit apps installed so want to keep it that way

Please read the PPA header:

```

FAQ:
* no native 64bit debs planed for now. The amd64 package is using ia32-libs.
See [http://dev.chromium.org/developers/design-documents/64-bit-support]("http://dev.chromium.org/developers/design-documents/64-bit-support") for the rationale.

```

---

### Post by ubulette on 2009-05-31
> **philinux said:**
> [https://edge.launchpad.net/~chromium-daily/+archive/ppa/+files/ia32-libs-chromium-browser_0.01~ucd6~jaunty_amd64.deb](https://edge.launchpad.net/~chromium-daily/+archive/ppa/+files/ia32-libs-chromium-browser_0.01~ucd6~jaunty_amd64.deb)

Install that first, if you are using Jaunty thats all. From the link on the first post it's all there, all the versions are there.

Please don't cherry pick debs like that. Add the full PPA instead.
The reason is that I maintain the necessary dependencies and ia32 tweaks for you.
If you decide to grab the debs manually, you're on your own, .ie. don't even bother looking for help.

---

### Post by ubulette on 2009-05-31
> **cl333r said:**
> Did anyone notice that it's already version 3? I thought they're trying to bring the 2nd version to Linux.

The version number has no real meaning. Or should I say, it's not the same meaning as the other projects.

Look at [http://bazaar.launchpad.net/~chromium-daily/chromium-browser/chromium-browser.head.daily/revision/166](http://bazaar.launchpad.net/~chromium-daily/chromium-browser/chromium-browser.head.daily/revision/166):

```

-chromium-browser (2.0.182.0~svn20090521r16618-0ubuntu1) UNRELEASED; urgency=low
+chromium-browser (3.0.182.0~svn20090522r16750-0ubuntu1) UNRELEASED; urgency=low

```

Basically, 2.0.182.x had enough features on Windows to make a release so they bumped the major version in the trunk, impacting all platforms. They could have used 3.0.0.0 but they didn't.
The 3rd number increases every few days, I'm unsure about its real meaning.

```

fta@cube:/data/bot/chromium-browser.head.daily $ bzr log | grep 'New upstream snapshot'
  * New upstream snapshot: 3.0.183.0 SVN 20090530r17289
  * New upstream snapshot: 3.0.183.0 SVN 20090529r17197
  * New upstream snapshot: 3.0.183.0 SVN 20090528r17077
  * New upstream snapshot: 3.0.183.0 SVN 20090527r16992
  * New upstream snapshot: 3.0.182.1 SVN 20090526r16872
  * New upstream snapshot: 3.0.182.1 SVN 20090525r16857
  * New upstream snapshot: 3.0.182.0 SVN 20090523r16844
  * New upstream snapshot: 3.0.182.0 SVN 20090523r16839
  * New upstream snapshot: 3.0.182.0 SVN 20090522r16818
  * New upstream snapshot: 3.0.182.0 SVN 20090522r16750
  * New upstream snapshot: 2.0.182.0 SVN 20090521r16618
  * New upstream snapshot: 2.0.182.0 SVN 20090520r16487
  * New upstream snapshot: 2.0.182.0 SVN 20090519r16386
  * New upstream snapshot: 2.0.181.0 SVN 20090518r16295
  * New upstream snapshot: 2.0.181.0 SVN 20090517r16261
  * New upstream snapshot: 2.0.181.0 SVN 20090516r16237
  * New upstream snapshot: 2.0.181.0 SVN 20090515r16158
  * New upstream snapshot: 2.0.181.0 SVN 20090514r16065
  * New upstream snapshot: 2.0.181.0 SVN 20090514r16052
  * New upstream snapshot: 2.0.181.0 SVN 20090513r15963
  * New upstream snapshot: 2.0.181.0 SVN 20090512r15864
  * New upstream snapshot: 2.0.181.0 SVN 20090511r15761
  * New upstream snapshot: 2.0.180.0 SVN 20090510r15737
  * New upstream snapshot: 2.0.180.0 SVN 20090509r15727
  * New upstream snapshot: 2.0.180.0 SVN 20090508r15648
  * New upstream snapshot: 2.0.179.0 SVN 20090507r15556
  * New upstream snapshot: 2.0.179.0 SVN 20090506r15422
  * New upstream snapshot: 2.0.178.0 SVN 20090505r15300
  * New upstream snapshot: 2.0.178.0 SVN 20090504r15212
  * New upstream snapshot: 2.0.178.0 SVN 20090503r15170
  * New upstream snapshot: 2.0.178.0 SVN 20090502r15142
  * New upstream snapshot: 2.0.178.0 SVN 20090501r15061
  * New upstream snapshot: 2.0.178.0 SVN 20090430r14953
  * New upstream snapshot: 2.0.178.0 SVN 20090429r14851
  * New upstream snapshot: 2.0.178.0 SVN 20090428r14739
  * New upstream snapshot: 2.0.177.0 SVN 20090427r14615
  * New upstream snapshot: 2.0.177.0 SVN 20090426r14559
  * New upstream snapshot: 2.0.177.0 SVN 20090425r14523
  * New upstream snapshot: 2.0.177.0 SVN 20090424r14438
  * New upstream snapshot: 2.0.177.0 SVN 20090423r14321
  * New upstream snapshot: 2.0.176.0 SVN 20090422r14200
  * New upstream snapshot: 2.0.176.0 SVN 20090421r14116
  * New upstream snapshot: 2.0.176.0 SVN 20090420r14034
  * New upstream snapshot: 2.0.175.0 SVN 20090418r14008
  * New upstream snapshot: 2.0.175.0 SVN 20090418r14004
  * New upstream snapshot: 2.0.175.0 SVN 20090417r13945
  * New upstream snapshot: 2.0.175.0 SVN 20090416r13847
  * New upstream snapshot: 2.0.175.0 SVN 20090415r13755
  * New upstream snapshot: 2.0.175.0 SVN 20090414r13668
  * New upstream snapshot: 2.0.174.0 SVN 20090413r13606
  * New upstream snapshot: 2.0.174.0 SVN 20090412r13572
  * New upstream snapshot: 2.0.174.0 SVN 20090411r13559
  * New upstream snapshot: 2.0.174.0 SVN 20090410r13520
  * New upstream snapshot: 2.0.174.0 SVN 20090409r13436
  * New upstream snapshot: 2.0.174.0 SVN 20090408r13368
  * New upstream snapshot: 2.0.174.0 SVN 20090407r13257
  * New upstream snapshot: 2.0.174.0 SVN 20090406r13174
  * New upstream snapshot: 2.0.173.0 SVN 20090405r13137
  * New upstream snapshot: 2.0.173.0 SVN 20090402r13016
  * New upstream snapshot: 2.0.173.0 SVN 20090401r12956
  * New upstream snapshot: 2.0.172.0 SVN 20090331r12873
  * New upstream snapshot: 2.0.172.0 SVN 20090330r12779
  * New upstream snapshot: 2.0.172.0 SVN 20090328r12752
  * New upstream snapshot: 2.0.172.0 SVN 20090328r12741
  * New upstream snapshot: 2.0.172.0 SVN 20090327r12672
  * New upstream snapshot: 2.0.172.0 SVN 20090326r12573
  * New upstream snapshot: 2.0.172.0 SVN 20090325r12470
  * New upstream snapshot: 2.0.172.0 SVN 20090324r12395
  * New upstream snapshot: 2.0.171.0 SVN 20090323r12294
  * New upstream snapshot: 2.0.171.0 SVN 20090322r12268
  * New upstream snapshot: 2.0.171.0 SVN 20090321r12248
  * New upstream snapshot: 2.0.171.0 SVN 20090320r12198
  * New upstream snapshot: 2.0.171.0 SVN 20090319r12158
  * New upstream snapshot: 2.0.171.0 SVN 20090319r12106
  * New upstream snapshot: 2.0.171.0 SVN 20090318r11987
  * New upstream snapshot: 2.0.171.0 SVN 20090317r11882
  * New upstream snapshot: 2.0.170.0 SVN 20090316r11783
  * New upstream snapshot: 2.0.170.0 SVN 20090316r11744
  * New upstream snapshot: 2.0.170.0 SVN 20090315r11715
  * New upstream snapshot: 2.0.170.0 SVN 20090314r11702
...

```

---

### Post by billyShears on 2009-05-31
> **ubulette said:**
> strange, do you have an old processor without SSE2? I supposedly fixed that weeks ago but noone reported me anything since.
But maybe it's something else for you.


I'm affected too ('ve got an athlon xp without sse2).
it seems that the problem is not fixed: [http://code.google.com/p/chromium/issues/detail?id=9007]("http://code.google.com/p/chromium/issues/detail?id=9007")

---

### Post by lovinglinux on 2009-05-31
Chromium gets 300% more points in [Peacekeeper](http://service.futuremark.com/peacekeeper/index.action) benchmark than Firefox on my machine. Is really impressive. Unfortunately, I'm still very dependent on several Firefox extensions to switch over Chromium.

---

### Post by djuliette on 2009-05-31
Has anyone gotten the extentions to work, or do they only work in chrome?
I tried this one with no result:

[http://blog.cleeki.com/?p=70](http://blog.cleeki.com/?p=70)

---

### Post by inportb on 2009-06-01
> **djuliette said:**
> Has anyone gotten the extentions to work, or do they only work in chrome?
I tried this one with no result:

[http://blog.cleeki.com/?p=70](http://blog.cleeki.com/?p=70)

Please read the splash page when starting Chromium...

---

### Post by djuliette on 2009-06-01
> **inportb said:**
> Please read the splash page when starting Chromium...

They are obviously working on it though, I tried loading the extension with 

sudo chromium-browser --enable-extensions --load-extension="~/Downloads/Cleeki_en_chrome_1.6.0.crx"

and chrome://extensions shows that it tried to load but had an error.

And as an aside they populated the general tab on the options window.

---

### Post by Zorael on 2009-06-02
I *want* to look forward to Chromium, but it's getting increasingly difficult after hearing them complain about their abstracted widget framework - invented because Windows' is lacking - doesn't translate to results consistent with Windows' one under the feature-complete frameworks available in Linux.

From what I understand (looking at Konqueror as the birthplace of KHTML which derives into webkit), their renderer would be *well* integrated with their framework if they'd opted to go with Qt. Saying that Qt apps look "foreign" is a bit confusing once you give a glance to how off-worldish Chrome looks on Windows.

edit: I mean, obviously they're going for their *own look* that doesn't look native under anything. So why not have it use a cross-platform framework from the get-go, then spend time on making it look the way they want? And it'd look that way. On Windows, as well as on Linux/*.

I get the feeling we'll get a sore port, spending needless cycles on translating their Windows workarounds into "native" framework calls.  Perhaps it'll even run faster with Chrome under Wine.

Please point out where I'm wrong; I could use a boost.

---

### Post by bizhat on 2009-06-02
When Google's Chrome web browser [debuted with much fanfare]("http://arstechnica.com/open-source/news/2008/09/hands-on-with-chrome-googles-browser-shines-mostly.ars") last year, it was Windows-only and not cross-platform compatible. The developers soon began working on Linux and Mac OS X ports of the browser's underlying open source Chromium code base. These ports are beginning to mature and could soon be ready for regular users.

In an early [discussion thread]("http://groups.google.com/group/chromium-dev/browse_thread/thread/b89ab99a0c848b89") about the strategy for porting the Chrome user interface to Windows, Google Chrome developer Ben Goodger expressed frustration with Linux user interface toolkits and commented that the platform's lack of consistency makes it difficult to know what to target.

"First of all let me generally comment that this entire situation is a clusterf*ck. I am not happy with the technical constraints imposed by Linux and its assorted UIs on Chrome's UI and feature set," he wrote. "There isn't dominant consensus around toolkit and HIG, there seems to be variance in commonly used software as to how it's constructed and what it matches, and I've not heard anyone glow about how they can create the coolest looking UIs with GTK."

For those who are unaware, Ben Goodger is a former employee of Mozilla and used to be the lead developer of the Firefox project. In his work on the Chrome browser he is drawing from his extensive experiences with the Firefox codebase. In his comment in the discussion thread, he suggests that Mozilla's approach--where a single user interface toolkit is made to reflect the native look and feel of each platform--is always going to produce imperfect results.
  After extensive discussion, the Chromium developers decided to build the Linux port with GTK+, the toolkit that is used by the popular GNOME desktop environment. This will eventually make it look and feel somewhat native on GNOME-based Linux distributions, such as Ubuntu.


get it from


[https://launchpad.net/~chromium-daily/+archive/ppa]("https://launchpad.net/%7Echromium-daily/+archive/ppa")



Source


[http://arstechnica.com]("http://arstechnica.com/open-source/news/2009/05/hands-on-google-chromium-browser-alpha-for-linux.ars")

---

### Post by Regenweald on 2009-06-02
Might i refer you ? :)
[http://ubuntuforums.org/showthread.php?t=1174494](http://ubuntuforums.org/showthread.php?t=1174494)

---

### Post by binbash on 2009-06-02
What is Google Chromium? As far as i know there are only Chromium and Google Chrome projects.

---

### Post by chucky chuckaluck on 2009-06-02
you can now use gtk themes for kde, as well. not sure what the problem is. it's not like chrome is eye candy.

---

### Post by legolas_w on 2009-06-02
I add 
```


deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main

```
 to sources.list and after I tried sudo apt-get update I get the following erro:

```

W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: You may want to run apt-get update to correct these problems


```

Can some one please let me know how to resolve it?

Thanks

---

### Post by -grubby on 2009-06-02
> **legolas_w said:**
> I add 
```


deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main

```
 to sources.list and after I tried sudo apt-get update I get the following erro:

```

W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: You may want to run apt-get update to correct these problems


```

Can some one please let me know how to resolve it?

Thanks

That error won't prevent you from installing it.

---

### Post by binbash on 2009-06-02
> **legolas_w said:**
> I add 
```


deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main

```
 to sources.list and after I tried sudo apt-get update I get the following erro:

```

W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: You may want to run apt-get update to correct these problems


```

Can some one please let me know how to resolve it?

Thanks

[http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html](http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html)

---

### Post by sports fan Matt on 2009-06-02
That script works well..Thanks!

---

### Post by Incognito-Here on 2009-06-02
Oh sh1t, what a mess!

```
#!/bin/sh

for gpg in `sudo aptitude update 2>&1 > /dev/null | grep NO_PUBKEY | sed -e 's/^.*\(........\)$/\1/g'`; do
    gpg --keyserver keyserver.ubuntu.com --recv $gpg
    gpg --export --armor $gpg | sudo apt-key add -
done
sudo aptitude update

```
This one works OK for me

---

### Post by adamvert on 2009-06-03
One thing I'd really like to know: has anyone worked out a way to make font hinting work properly?  All pages viewed in Chromium have slightly fuzzy text - although the text at the top, in the tabs and address bar, is fine.

I'm loving Chromium, the speed improvement over Firefox is amazing (although admittedly I've got waaaay too many extensions running with FF).

---

### Post by Hells_Dark on 2009-06-03
I love the way the history, downloads & co are totally into the browser as simple web pages.

---

### Post by hyperdude111 on 2009-06-03
> **adamvert said:**
> One thing I'd really like to know: has anyone worked out a way to make font hinting work properly?  All pages viewed in Chromium have slightly fuzzy text - although the text at the top, in the tabs and address bar, is fine.

I'm loving Chromium, the speed improvement over Firefox is amazing (although admittedly I've got waaaay too many extensions running with FF).

You need to install msstcore fonts

---

### Post by super.rad on 2009-06-03
> **super.rad said:**
> Just running that test in a few browsers now, my results were (sorry no fancy spreadsheets like david lol)

Browser  --  Peacekeeper (Overall Score)  --  Acid3
Midori  --  3245  --  100
Arora  --  2580  --  98
Konqueror  --  1596  --  87
Kazehakase (Gecko  --  1237  --  71
Epiphany   --  1229  --  71
Shiretoko 3.5b4  --  1213  --  93
Firefox 3.0.10  --  1006  --  71
Kazehakase (Webkit)  --  Crashed  --  99

Some reason when using Kazehakase with the webkit backend as soon as I started the benchmarks it just closed
Didn't test Chrome as I'm on 64bit so don't want to install all the 32bit lib's just for a browser
Similar results to david although everything scored higher on mine (computer is a brand new build though) and kazehakase and epiphany were both above firefox for me

Just tested Epiphany 2.27.2 (webkit version) Peacekeeper = 3123 Acid3 = 100

---

### Post by mxboy15u on 2009-06-03
> **hyperdude111 said:**
> You need to install msstcore fonts

How does one do that?

Edit: I installed what it said was a dummy package via synaptic, was that the correct package?

I am also getting that no public key error everytime I update now, any way of fixing that?

---

### Post by hyperdude111 on 2009-06-03
> **mxboy15u said:**
> How does one do that?

Edit: I installed what it said was a dummy package via synaptic, was that the correct package?

I am also getting that no public key error everytime I update now, any way of fixing that?

I also get that public key error but it wont stop you from updating.

---

### Post by adamvert on 2009-06-05
> **hyperdude111 said:**
> You need to install msstcore fonts

I've already got msttcorefonts installed, it's not that.  I read about a Chromium bug that meant it didn't pick up changes to the main Gnome font hinting settings, but I don't think that's the problem I'm having.

Here's an image showing Chromium and Firefox, to illustrate the problem.

---

### Post by pt123 on 2009-06-05
Today, Google has released preview versions for Mac & Linux
[http://news.cnet.com/8301-17939_109-10257538-2.html](http://news.cnet.com/8301-17939_109-10257538-2.html)

has links to down load
[http://dev.chromium.org/getting-involved/dev-channel](http://dev.chromium.org/getting-involved/dev-channel)

They have deb files

---

### Post by markharding557 on 2009-06-05
i think firefox or seamonkey is vastly superior

---

### Post by waldorf on 2009-06-05
has anyone been able to install google gears on this linux version of chrome? I can download the .xpi, but then it doesn't seem to want to install.

thanks

---

### Post by waldorf on 2009-06-05
has anyone been able to install google gears on this linux version of chrome? I can download the .xpi, but then it doesn't seem to want to install.

thanks

---

### Post by OutOfReach on 2009-06-05
> **waldorf said:**
> has anyone been able to install google gears on this linux version of chrome? I can download the .xpi, but then it doesn't seem to want to install.

thanks

According to the splash screen, it's not been implemented yet

---

### Post by waldorf on 2009-06-05
Ah, that would do it. Thanks!

---

### Post by WitchCraft on 2009-06-06
**Chris Keall** |         Saturday June 6 2009 - 07:47am         

                                                                        [IMG]http://www.nbr.co.nz/files/chrome_logo.jpg[/IMG]Good news: Mac and Linux versions of Google&#8217;s web browser have arrived.




Download:

[http://dev.chromium.org/getting-involved/dev-channel](http://dev.chromium.org/getting-involved/dev-channel)

Chromium (under Wine):
```

Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US) AppleWebKit/525.13 (KHTML, like Gecko) Version/3.1 Safari/525.13

```

Chrome (native)
```

Mozilla/5.0 (X11; U; Linux i686; en-US) AppleWebKit/531.0 (KHTML, like Gecko) Chrome/3.0.183.1 Safari/531.0

```

News Source:
[http://www.nbr.co.nz/article/google-warns-don-t-download-mac-linux-versions-chrome-103399](http://www.nbr.co.nz/article/google-warns-don-t-download-mac-linux-versions-chrome-103399)

---

### Post by Reiger on 2009-06-06
There's a testing PPA for quite some time now already. Much easier than to compile it from source, turn it into a deb and subsequently install through apt/dpkg.

---

### Post by binbash on 2009-06-06
[http://www.ubuntu-inside.me/2009/06/google-released-google-chrome-not.html](http://www.ubuntu-inside.me/2009/06/google-released-google-chrome-not.html)

---

### Post by Tibuda on 2009-06-06
> **Reiger said:**
> There's a testing PPA for quite some time now already. Much easier than to compile it from source, turn it into a deb and subsequently install through apt/dpkg.

That PPA is for unbranded Chromium, the opensource base for Chrome. This time Chrome was released, and with a deb package available. Check that link again.

---

### Post by WitchCraft on 2009-06-06
> **binbash said:**
> [http://www.ubuntu-inside.me/2009/06/google-released-google-chrome-not.html](http://www.ubuntu-inside.me/2009/06/google-released-google-chrome-not.html)

Oh, is it actually yesterdays news.


Yes I know that you could compile chrome for some time, but I did not have the time...

It's faster than Opera!

Actually, anybody knows whether flash does really not yet work, or whether one just has to install the plugin, maybe with some additional tweaking?

---

### Post by matmatmat on 2009-06-06
As far as I can see there is no way to install flash

---

### Post by DemonBob on 2009-06-06
> **matmatmat said:**
> As far as I can see there is no way to install flash

As stated via opening page...

> Google Chrome Dev Build

This is an in-progress build of Google Chrome on Linux. The following significant chunks of functionality are known to be missing:

Plugins, including Flash (so no YouTube, Hulu, etc.)
Printing
Complex text
Complex tab dragging
Gears support
Other parts of the browser are notably incomplete, poorly tuned and broken. User beware!

‘Chromium’ vs ‘Google Chrome’

Chromium is an open source browser project. Google Chrome is a browser from Google, based on the Chromium project.

This is a build of Google Chrome, released by Google for testing.

Don't file bugs without doing the work

Every minute spent triaging and de-duplicating bugs is a minute spent not fixing them. If you have a good bug report (e.g. includes a stack trace or a reduced test case), first verify it exists in the latest build, then verify it hasn't been filed already, then file your bug using the Linux-specific template.

How to help

Chromium is an open source project, and you are welcome to help out. We have documentation for developers as well as mailing lists and an IRC channel.

---

### Post by WitchCraft on 2009-06-06
> **DemonBob said:**
> As stated via opening page...


Oh, sorry I misread. I read flash plugins do not work (and thought maybe that's only for the default install script), but it actually says plugins don't work.

What's complex text, and what's gears?

---

### Post by matmatmat on 2009-06-06
[gears]("http://gears.google.com/")

---

### Post by simeon87 on 2009-06-06
I think I'll wait till it's a bit more usable :)

---

### Post by Pater Puff on 2009-06-06
chronium is much better! chrome is a beta version yet, and not really useable yet (as windows vista :D, will it proberly never be useable)

---

### Post by Tibuda on 2009-06-06
> **Pater Puff said:**
> chronium is much better! chrome is a beta version yet, and not really useable yet (as windows vista :D, will it proberly never be useable)

Linux Chrome is only a developer preview, and Chromium is only alpha.

---

### Post by Zerocool3001 on 2009-06-06
Since Google has now released a pre-alpha version of Chrome for Linux, has anyone had a chance to compare it to the open source Chromium builds available on Launchpad? I know that Chrome doesn't have working TLS yet, but are there any other pieces that one browser has and the other doesn't?


P.S. It seems interesting that the "developer" channel of Google Chrome only lists .debs for Linux.

[Google Chrome Developer Channel]("http://dev.chromium.org/getting-involved/dev-channel")
[Chromium on Launchpad]("https://launchpad.net/~chromium-daily/+archive/ppa")

---

### Post by OutOfReach on 2009-06-06
The Google Chrome that they released is pretty much just the latest build of Chromium, but rebranded with the Google Chrome name

---

### Post by hyperdude111 on 2009-06-06
> **OutOfReach said:**
> The Google Chrome that they released is pretty much just the latest build of Chromium, but rebranded with the Google Chrome name

It is exactly. The downloads that day were the exact same size.

---

### Post by donniezazen on 2009-06-06
I am still confused between Google Chrome and Chromium.

Are these two browsers same?

[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

[http://dev.chromium.org/getting-involved/dev-channel](http://dev.chromium.org/getting-involved/dev-channel)

Which is going to be Google Chrome that i use in windows?

Thanks,
SK

---

### Post by lovinglinux on 2009-06-06
> **soham_1207 said:**
> I am still confused between Google Chrome and Chromium.

Are these two browsers same?

[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

[http://dev.chromium.org/getting-involved/dev-channel](http://dev.chromium.org/getting-involved/dev-channel)

Which is going to be Google Chrome that i use in windows?

Thanks,
SK

They are the same, just different channels. I would use the PPA repository, which is updated more frequently (just a little bit ahead).

---

### Post by ddrichardson on 2009-06-06
I wish the version that they are using in Moblin was as stable - on the Aspire One it crashes a lot, usually when you click links to JavaScript. Just as well each window is seperate.

---

### Post by dragos240 on 2009-06-06
> **soham_1207 said:**
> I am still confused between Google Chrome and Chromium.

Are these two browsers same?

[https://launchpad.net/~chromium-daily/+archive/ppa]("https://launchpad.net/%7Echromium-daily/+archive/ppa")

[http://dev.chromium.org/getting-involved/dev-channel](http://dev.chromium.org/getting-involved/dev-channel)

Which is going to be Google Chrome that i use in windows?

Thanks,
SK

Cromium is the open source project behind google chrome, chrome is just chromium with the google colors and logo.

---

### Post by donniezazen on 2009-06-06
Are these two channels maintained by different organizations? Are these browsers in competition? If yes which one is going to go far ahead of other as one is maintained by the Google and other by an open source community?

Thanks for replies.
SK

---

### Post by OutOfReach on 2009-06-06
> **soham_1207 said:**
> Are these two channels maintained by different organizations? Are these browsers in competition? If yes which one is going to go far ahead of other as one is maintained by the Google and other by an open source community?

Thanks for replies.
SK

The way I understand it is that one of them (Chromium) is the actual project and all the work goes into that, and Chrome is the basically the result.

---

### Post by joey-elijah on 2009-06-06
> **OutOfReach said:**
> The way I understand it is that one of them (Chromium) is the actual project and all the work goes into that, and Chrome is the basically the result.

That's pretty much it! Google created Chromium and are the largest developers of Chromium. At various stages they take Chromium, stick their logo on it and push it out as Chrome.

---

### Post by t4ggs on 2009-06-06
im very excited

[http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb](http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb)

---

### Post by Zerocool3001 on 2009-06-06
> **joey-elijah said:**
> That's pretty much it! Google created Chromium and are the largest developers of Chromium. At various stages they take Chromium, stick their logo on it and push it out as Chrome.

There are some other slight differences. The builds for Ubuntu on launchpad incorporate all the work of the open source community (you can contribute if you'd like) but Chrome builds from Google contain pieces they want to use (i.e. mostly developed by them). A good example is TLS support. Chromium, the all open source project, has it. Google Chrome for linux doesn't include it yet. This means at the moment, Chromium is *slightly* more functional than Chrome.

Also, the PPA on launchpad is not the official repository for Chromium, but a Ubuntu build of it (they usually contain roughly the same bits).

---

### Post by CharmyBee on 2009-06-06
Being a developer release, don't be too excited.

---

### Post by Skripka on 2009-06-06
> **CharmyBee said:**
> Being a developer release, don't be too excited.

From all the prior threads we we've seen, the only differences between Chromium and the official Chrome package are branding.

---

### Post by WitchCraft on 2009-06-06
> **danielrmt said:**
> Linux Chrome is only a developer preview, and Chromium is only alpha.
 
For a developer preview, it works pretty good.
And there is always firefox/opera to fallback on.
 
Chromium on the other hand is completely unusable.
It usually crashes after less than a minute...
 
 
Now Chrome is very fast, and it does NOT crash.

---

### Post by Wiebelhaus on 2009-06-06
> **simeon87 said:**
> I think I'll wait till it's a bit more usable :)

It's very usable mate , But hey! I understand.

---

### Post by Sashin on 2009-06-06
Who told you that?

When Chrome was released for linux, Chromium was already a step ahead?

Both the same... what are you talking about...
If you right click the tab bar in chromium you get a menu and with chrome you don't.

It's really an oversimplification to say that chrome is just chromium with the logo.

---

### Post by Wiebelhaus on 2009-06-06
This is like the fifth thread , geez man.

I should just quote myself from the other threads.

---

### Post by lovinglinux on 2009-06-06
> **Wiebelhaus said:**
> This is like the fifth thread , geez man.

I should just quote myself from the other threads.

+1 Geez

Lock, merge, move to the recurring discussions or throw it in the dungeons please.

---

### Post by praveesh on 2009-06-06
Only gtk ?. Isn't there any qt chromium?

---

### Post by vishzilla on 2009-06-07
I guess Chromium corresponds to Chrome like Minefield corresponds to Firefox. I am still using the chromium daily builds on Arch.

@praveesh: Chrome is currently only using GTK+, for Qt you will have to wait for a fork ;)

---

### Post by swoll1980 on 2009-06-07
I have chrome, and chromium installed. Neither are using my gtk theme. What am I doing wrong.

---

### Post by Sashin on 2009-06-07
That was in a prior build, they took out GTK theming.

---

### Post by vishzilla on 2009-06-07
It doesn't follow the GTK theme.. I hope they don't keep it this way. I think that has to do with the Skia graphics library.. Its sad they didn't port it to pure GTK or Qt.

---

### Post by WitchCraft on 2009-06-08
> **vishzilla said:**
> It doesn't follow the GTK theme.. I hope they don't keep it this way. I think that has to do with the Skia graphics library.. Its sad they didn't port it to pure GTK or Qt.

Mine accepts the gtk theming.

> **praveesh said:**
> Only gtk ?. Isn't there any qt chromium?

QT? Why? QT is antiquated.

---

### Post by Zorael on 2009-06-08
> **WitchCraft said:**
> QT? Why? QT is antiquated.
Qt is suddenly antiquated? Very interesting!

---

### Post by ubulette on 2009-06-08
Obviously, there's a lot of confusion going on.
I've created the chromium-browser package and the associated daily PPA, I guess I should try to clarify.

Chromium is fully open source. It is developed by the Chromium Authors, meaning some Googlers plus the community, as listed here: [http://src.chromium.org/svn/trunk/src/AUTHORS](http://src.chromium.org/svn/trunk/src/AUTHORS)
You can get all the bits from svn and build it locally, you will end-up with something(*) which has a blue look: that's chromium.
(*) some files are mistakenly called chrome but they are really just chromium, that should be fixed eventually.

Chrome, or should I say Google Chrome, is using the same sources as chromium, plus some other sources not publicly available. It is built with some slightly different flags, and on a particular distro (iirc, it's the last LTS, Hardy), meaning a specific tool chain (gcc, binutils, etc.).
It is not something you can build locally, even by tweaking the flags, as some files are missing. For example, the branding files (Colorful icons), the google updater and probably more.

The daily PPA contains Chromium, not Chrome. It is of course unofficial, yet upstream is aware of that effort.
It's neither a fork, nor a different product. It's just a package like any other package in Ubuntu: upstream sources with some patches to make the thing build & run, and some integration with the desktop. The packaging itself is public, on LP.

It's built on all Ubuntu distros from Hardy to Karmic, using the native toolchain and system libs of each distro (hence producing slightly different binaries, with different optimizations and runtime checks & protections).

I try to keep the packaging in sync with all the good stuff the Chromium authors are bringing in. Sometimes, the daily PPA is making them nervous as it constantly exposes unfinished and untuned features, leading to unwanted bug reports.

I would say that using one or the other is a matter of taste.
Feature wise, it's almost a perfect match, you don't have much to gain, at least at this point. The difference is mostly on the upgrade side:

- with Chrome, you let Google decide when they send you updates and you send your crashes plus some infos to them.
You also have to report bugs directly to Google, not to Ubuntu. If I'm not mistaken, you can't resolve your backtraces locally after a crash, as the symbols are not available to you, only Google has them.
It's installed in /opt, as often with binaries from vendors.
You gain the branded name, already recognized by the Windows community.
You may or may not care about all this.

- with Chromium from the PPA, you're managing your updates like for everything else, and you're not submitting your crashes to them automatically.
You can submit your crashes, if you want to, by following this link: [https://wiki.ubuntu.com/Chromium/Debug](https://wiki.ubuntu.com/Chromium/Debug)
This has to be done properly as Google doesn't have our symbols to resolve backtraces against. They gladly accept complete bug reports from PPA users.

The reason I'm not accepting bugs for Chromium in Launchpad is because Chromium is not yet part of the repository and I don't have time to do this bug work myself.

There's still a lot of work to be done before Chromium enters the official Ubuntu repositories (this has been discussed at the last UDS in Barcelona). Chrome will probably never be in there, yet Google may want to put it in the Canonical repositories at some point.

---

### Post by Skripka on 2009-06-08
> **Zorael said:**
> Qt is suddenly antiquated? Very interesting!

I'll admit I LOL'd at that.

---

### Post by albinootje on 2009-06-08
> **ubulette said:**
> 
I've created the chromium-browser package and the associated daily PPA, I guess I should try to clarify.
Chromium is fully open source. 

Thanks for the long explanation, much appreciated, and very interesting to read! :)

---

### Post by vishzilla on 2009-06-08
> **WitchCraft said:**
> Mine accepts the gtk theming.
QT? Why? QT is antiquated.

What about the blue color? :)

---

### Post by WitchCraft on 2009-06-10
> **vishzilla said:**
> What about the blue color? :)

I like the blue color.
There just needs to be the window title bar removed, it needs damn much space on a laptop with a small screen.


And yes, QT is antiquated.
Use wxWidgets instead, that has by far the better interface/design/abstraction/languagebinding/license/nativeWidgets/speed/compatibility/linking/runtime (= BASICALLY EVERYTING).
It also brings an entire own browser (based on the Apple WebKit (=almost Chrome)), uses OpenGL (you can switch that off), has a decent MediaPlayer, supports Unicode (if you want) etc. etc. etc.

QT is to wxWidgets what a Ford-T is to a Ferrari - an antique.
I mean even the QT company name tells you everything: TROLLtech.

---

### Post by CJ Master on 2009-06-10
> **WitchCraft said:**
> I like the blue color.
There just needs to be the window title bar removed, it needs damn much space on a laptop with a small screen.


And yes, QT is antiquated.
Use wxWidgets instead, that has by far the better interface/design/abstraction/languagebinding/license/nativeWidgets/speed/compatibility/linking/runtime (= BASICALLY EVERYTING).
It also brings an entire own browser (based on the Apple WebKit (=almost Chrome)), uses OpenGL (you can switch that off), has a decent MediaPlayer, supports Unicode (if you want) etc. etc. etc.

QT is to wxWidgets what a Ford-T is to a Ferrari - an antique.
I mean even the QT company name tells you everything: TROLLtech.

wxWidgets is totally antiqued too, dude! I mean, BASICALLY EVERYTHING is all disfigured and a mess, and totally hard to progam. Not worth ANYBODY'S time.

What I'm trying to point out is, before bashing something, give some darn sources.

---

### Post by Closed_Port on 2009-06-10
> **WitchCraft said:**
> 
And yes, QT is antiquated.
Use wxWidgets instead, that has by far the better interface/design/abstraction/languagebinding/license/nativeWidgets/speed/compatibility/linking/runtime (= BASICALLY EVERYTING).
It also brings an entire own browser (based on the Apple WebKit (=almost Chrome)), uses OpenGL (you can switch that off), has a decent MediaPlayer, supports Unicode (if you want) etc. etc. etc.

QT is to wxWidgets what a Ford-T is to a Ferrari - an antique.
I mean even the QT company name tells you everything: TROLLtech.
This has to be the, how do I put it, most uniformed thing I've read for ages. :(

---

### Post by WitchCraft on 2009-06-10
> **CJ Master said:**
> wxWidgets is totally antiqued too, dude! I mean, BASICALLY EVERYTHING is all disfigured and a mess, and totally hard to progam. Not worth ANYBODY'S time.

What I'm trying to point out is, before bashing something, give some darn sources.

I'm not writing a dissertation here, and neither do I worry about formally correct quoting.

I use wxWidgets, and I used to use QT, so:
I am THE source, and this is MY opinion!

And, unlike QT, wxWidgets is definitely NO mess (with the exception of the WebKit, but that's because it is in development).

And if such a simple thing as wxWidgets is too hard for you, well, go use THE WOW (the wow what utter crap Vista) and program in VB.

---

### Post by ubulette on 2009-06-10
> **WitchCraft said:**
> I like the blue color.
There just needs to be the window title bar removed, it needs damn much space on a laptop with a small screen.

right click the *dark* blue area, you'll find the "Use system title bar and borders". Uncheck it.

---

### Post by CJ Master on 2009-06-10
> **WitchCraft said:**
> I'm not writing a dissertation here, and neither do I worry about formally correct quoting.

I use wxWidgets, and I used to use QT, so:
I am THE source, and this is MY opinion!

And, unlike QT, wxWidgets is definitely NO mess (with the exception of the WebKit, but that's because it is in development).

And if such a simple thing as wxWidgets is too hard for you, well, go use THE WOW (the wow what utter crap Vista) and program in VB.

I'm glad that's your opinion, because in your previous posts it sounded a lot like you were pushing it off as facts.

I use Qt (which I certainly don't find a mess.) I don't find wxWidgets complicated, I was making a point.

---

### Post by WitchCraft on 2009-06-10
> **CJ Master said:**
> I'm glad that's your opinion, because in your previous posts it sounded a lot like you were pushing it off as facts.

I use Qt (which I certainly don't find a mess.) I don't find wxWidgets complicated, I was making a point.

Well, to be fair, QT certainly has some advantages depending on how you see it. First, you may want your application to look the same everywhere. wxWidgets uses the native API's, so that's not possible, but QT uses its own widgets (which is why it is so bloated). [On the other hand, usually you want your applications to look native, which is something QT can't do]


And behind QT there is a corporation, while behind wxWidgets there is Julian Smart and some other people, so from an economic point of view it might be wiser to use QT, because it's not certain what happens to wxWidgets if Smart leaves.

But the other side of the coin is that wxWidgets is completely free, while QT costs a lot (unless you use GPL).

Now I like the GPL, but if you ever want to go commercial, it would be very unwise to give away the sources, and if you don't want to, you have to pay a lot for the QT license. Also, QT limits to shared libraries if it shall be free of charge, while wxWidgets can always be used whatever way you want - free of charge, because the license is BSDish. 

And if you want to go commercial/closed source, you can always do this with wxWidgets at no additional charge whatsoever, while QT will make your product expensive... (a price difference to competitors that the wxGuy can earn if he sells at the same price as the qtGuy)

Besides, if you're willing to spend as much money on wxWidgets support as you pay for the QT license, you sure as hell find somebody who will provide excellent wxSupport for your every wxNeed - far more excellent than the support you get with a QT license...

And may I remind that the QT license is the reason why the GNU project started GNOME, the GNU Network Object Model Environment, which is a replacement for QT-based KDE, and GNOME already has the bigger market share when it comes to business.

---

### Post by Closed_Port on 2009-06-10
> **WitchCraft said:**
> 
But the other side of the coin is that wxWidgets is completely free, while QT costs a lot (unless you use GPL).

*Sigh*
Qt is now also licensed under the LGPL, so you can use it for free even for closed projects. 

And I'd really like to see how you back up your claim that Gnome has the bigger market share when it comes to business. Thanks in advance.

---

### Post by WitchCraft on 2009-06-10
> **ubulette said:**
> right click the *dark* blue area, you'll find the "Use system title bar and borders". Uncheck it.

The dark blue area next to tabs? Doesn't work, no context menu there.

---

### Post by Closed_Port on 2009-06-10
> **WitchCraft said:**
> The dark blue area next to tabs? Doesn't work, no context menu there.
It works here.
Are you using the nightly builds?

---

### Post by WitchCraft on 2009-06-10
> **Closed_Port said:**
> *Sigh*
Qt is now also licensed under the LGPL, so you can use it for free even for closed projects. 

And I'd really like to see how you back up your claim that Gnome has the bigger market share when it comes to business. Thanks in advance.

Yes, but the LGPL means you cannot link statically.
That means you're forced to link dynamically.
And that means you have to install the runtime.
And that means you have to install the correct version of the runtime, and I've seen at least a dozen of QT applications which don't mention the runtime-version at all.

(You know, my favourite QT thing: Program faild to load: dll xy missing. Well, most people are lost when they see this message. I just go to a dll site and download the xy.dll. But then: Error, program failed to load: the dll.xy is not the correct version of QT [never mind mentioning which version would be right...])

Plus you need an installer for the runtime. QT does not offer it.
Well, you can distribute the shared libraries in the folder where your program resides in. But then, why use a shared library at all (that just makes decompilation far simpler)?

With wxWidgets, you just compile statically, then compress to reduce the executable size. Problem solved.

 (except for the webkit, which requires dynamic linking, because the webkit library is 250 MB in size).
And you can always link wxWidgets dynamically, if you want the same problems as QT. But hey, why worrying about the end user? When he buyed the product, what do you care about him/her anyway...

---

### Post by WitchCraft on 2009-06-10
> **Closed_Port said:**
> It works here.
Are you using the nightly builds?

No, I'm using the alpha version .deb of Chrome provided by google (Google Chrome Dev Build).
Where do I find nightly builds?

---

### Post by Closed_Port on 2009-06-10
> **WitchCraft said:**
> Yes, but the LGPL means you cannot link statically.
That means you're forced to link dynamically.

So, suddenly you casually admit that you were writing plain nonsense (well, actually you don't admit it, but simply gloss over it), only to come up with new complaints.
Yep, Qt is LGPL just like GTK+ you praised in your last post.

Nope, on a Linux system you don't have to install Qt, that's the job of the package manager. And Windows Installer can handle installing a .dll, thank you very much.

Qt releases stay compatible with a release cycle (Qt 4.x for example), so you don't have to worry about the corret version being installed.

On a final note:
I really don't know what on earth Qt did to you that you hate it with such a passion.
First you make the unsubstantiated and hilariously dumb claim that Qt is antiquated compared to wxwidgets.
After people pointed out that this was nonsense, you come with the old Qt is unfree because it is GPL Fud.
Then, after it has been pointed out to you that Qt is also available under the LGPL, you simply act as if you never said anything different and proceed to tell us about the perils of dynamic linking.

Don't get me wrong, if you prefer wxwidgets, more power to you and have fun using it, but please stop spewing this incredible nonsense and stop embarrassing yourself.

---

### Post by WitchCraft on 2009-06-10
> **Closed_Port said:**
> *Sigh*
Qt is now also licensed under the LGPL, so you can use it for free even for closed projects. 

And I'd really like to see how you back up your claim that Gnome has the bigger market share when it comes to business. Thanks in advance.

[http://dufoli.wordpress.com/2007/09/05/linux-marketshare/](http://dufoli.wordpress.com/2007/09/05/linux-marketshare/)

[http://digg.com/linux_unix/Linus_Torvalds_has_switched_to_GNOME](http://digg.com/linux_unix/Linus_Torvalds_has_switched_to_GNOME)
[http://ubuntuforums.org/showthread.php?t=518783](http://ubuntuforums.org/showthread.php?t=518783)

[http://oshelpdesk.org/wp-content/files/screenshot_006.png](http://oshelpdesk.org/wp-content/files/screenshot_006.png)


Windows  91.79%
Mac      7.43
Linux: 0.63

Internet Explorer 76.04%
Firefox: 16.8%
Safari: 5.59%

Google:77.04%
Yahoo: 12.76%
MSN/Live: 5.9%


Gnome 45%
KDE   35 %
XFCE   8%
Other 12 %


Ha, I can even back it up by numbers!

---

### Post by Closed_Port on 2009-06-10
> **WitchCraft said:**
> No, I'm using the alpha version .deb of Chrome provided by google (Google Chrome Dev Build).
Where do I find nightly builds?
Ah, I think that's the problem.

You can find nightly builds of chromium in the following ppa:
[https://edge.launchpad.net/~chromium-daily/+archive/ppa](https://edge.launchpad.net/~chromium-daily/+archive/ppa)

Using this it works for me.

---

### Post by Closed_Port on 2009-06-10
> **WitchCraft said:**
> 
Ha, I can even back it up by numbers!
No, you can't actually.
Where's the statistic that backs up your claim that "GNOME already has the bigger market share when it comes to business"?

---

### Post by WitchCraft on 2009-06-10
> **Closed_Port said:**
> So, suddenly you casually admit that you were writing plain nonsense (well, actually you don't admit it, but simply gloss over it), only to come up with new complaints.
Yep, Qt is LGPL just like GTK+ you praised in your last post.

It's correct that I didn't know it's LGPL meanwhile, last time I checked it was GPL.

But free means BSD license (to me), not GPL, and LGPL neither.




> **Closed_Port said:**
> 
Nope, on a Linux system you don't have to install Qt, that's the job of the package manager. 


And the package manager installs QT (300 MB+).
In case you ever noticed, this requires admin rights.
(which you most likely don't have on a non-private computer, for example at work...)


> **Closed_Port said:**
> 
And Windows Installer can handle installing a .dll, thank you very much.

Correct, but nobody writes the installer for you, and you shouldn't override other exising QT installations (different dll version - need to say more?)
Furthermore, Windows Installer is a bad product, don't use it if you don't have to.


> **Closed_Port said:**
> 
Qt releases stay compatible with a release cycle (Qt 4.x for example), so you don't have to worry about the corret version being installed.

You say it yourself, 4.x and 3.x.
And dll for 4.1 is != dll for 4.2 etc.
(not that you would realise the difference on the developer system)


> **Closed_Port said:**
> 
On a final note:
First you make the unsubstantiated and hilariously dumb claim that Qt is antiquated compared to wxwidgets.

Maybe antiquated is a bit harsh - since it is still being developed, but it's what I think.
Just look at the QT widgets - they look really awful (from a graphical point of view).
Like a fist in the eye...



> **Closed_Port said:**
> 
Yep, Qt is LGPL just like GTK+ you praised in your last post.


I didn't praise GTK+ (the webkit), actually a 250 MB shared library to add a bit of web capability is quite an overhead. 

Actually, the WebKit is the worst part of wxWidgets, but if you need it - it exists. But I don't think any sane mind is going to release a program with a 250 MB shared libary...

---

### Post by zekopeko on 2009-06-10
> **Closed_Port said:**
> No, you can't actually.
Where's the statistic that backs up your claim that "GNOME already has the bigger market share when it comes to business"?

it logically follows from GTK+ being LGPL for years before Qt. Bussiness like to have latitude when dealing with FOSS. check out red hat enterprise linux. it's built *gasp* on GNOME not KDE. not to mention that redhat and novell have been heavily investing in GNOME/GTK+ for years. not to mention ubuntu. so sorry to pop your bubble but KDE isn't exactly and enterprise solution for businesses.

---

### Post by Closed_Port on 2009-06-10
> **zekopeko said:**
> it logically follows from GTK+ being LGPL for years before Qt. Bussiness like to have latitude when dealing with FOSS. check out red hat enterprise linux. it's built *gasp* on GNOME not KDE. not to mention that redhat and novell have been heavily investing in GNOME/GTK+ for years. not to mention ubuntu. so sorry to pop your bubble but KDE isn't exactly and enterprise solution for businesses.

Look, you don't burst any bubbles, I'm actually writing this from Gnome. However, I'd like to see some actual numbers if someone makes a claim and so far, nobody seems to be able to provide anything. Instead I get attacked for even asking. 
And of course I'm getting the old FUD that Qt somehow wasn't businessfriendly compared to GTK, conveniently ignoring that you'll find more commercial software build with Qt than GTK. 
Also forget that Suse has been traditionally a very KDE-centric distro and that much of Novell's install base is still Kde-based, that Mandriva is quite a big player when it comes to desktop linux here in Europe and that there are quite large deployments like the LiMux project that use KDE.

I don't really care if Gnome or KDE has a larger install base in business, I'd just like some actual numbers.

---

### Post by WitchCraft on 2009-06-10
> **Closed_Port said:**
> No, you can't actually.
Where's the statistic that backs up your claim that "GNOME already has the bigger market share when it comes to business"?

Ok, that's right, and statistics are hard to find.


But some quotes:
Assume default desktop environment = will have larger market share

Novell:
> 
In upcoming versions of Novell enterprise applications, the default desktop environment will be GNOME. 


Redhat:
> 
Since we have a greater number of experienced GNOME hackers than we have of KDE hackers we are probably doing a better job with our modifications to GNOME than we are for KDE.



Red Hat and Novell are the two giant on enterprise linux.

Ubuntu is using gnome by default.

Torvalds hates gnome, but switched to gnome (had to) ...

And it's gnome that is on mobile devices (all the qt bloat doesn't fit in a mobile phone)
[http://www.infoworld.com/d/networking/gnome-extends-reach-mobile-and-embedded-devices-685](http://www.infoworld.com/d/networking/gnome-extends-reach-mobile-and-embedded-devices-685)

Linux enterprise application on Mobile Phones is quite likely the largest share of commercial linux's.

Google Chrome uses GTK instead of QT.
(remember, google also develops mobile phone platforms - just an arbitrary coincidence?)


... continue list here ...

maybe i'll still find a statistics that confirms what's quite obviously true.

---

### Post by zekopeko on 2009-06-10
> **Closed_Port said:**
> Look, you don't burst any bubbles, I'm actually writing this from Gnome. However, I'd like to see some actual numbers if someone makes a claim and so far, nobody seems to be able to provide anything. Instead I get attacked for even asking. whoaa! what does it matter from which DE you are writing this? and do show me where i "attacked" you. BTW i'm writing this from windows 7 using google chrome :D

>  
And of course I'm getting the old FUD that Qt somehow wasn't businessfriendly compared to GTK, conveniently ignoring that you'll find more commercial software build with Qt than GTK. 
this isn't FUD. it was a matter of fact. people didn't like Qt because the license for a single developer per year was in the range of 5000+ USD (for commercial apps). so why use a toolkit that you have to pay for for commercial apps when you have a toolkit that's free for development of closed source apps like GTK+? see, logic. less money for development == more profit later. and i don't think that they changed Qt's price for commercial development since nokia acquired trolltech.

> 
Also forget that Suse has been traditionally a very KDE-centric distro and that much of Novell's install base is still Kde-based, that Mandriva is quite a big player when it comes to desktop linux here in Europe and that there are quite large deployments like the LiMux project that use KDE. novell since 2005 defaults to gnome as does red hat (don't know if thye support KDE at all), as does ubuntu (kubuntu isn't a primary focus for canonical). so 3 of the largest commercial linux vendors use gnome as default desktop.
i wonder what one could ascertain from this information? hmmmm.... i wonder....

> 
I don't really care if Gnome or KDE has a larger install base in business, I'd just like some actual numbers.

googleing this is left to you. i tried but and combination of gnome and kde in the same search query end up with some gnome vs kde flamewar.

---

### Post by Closed_Port on 2009-06-10
> **WitchCraft said:**
> Ok, that's right, and statistics are hard to find.

And it's gnome that is on mobile devices (all the qt bloat doesn't fit in a mobile phone)
[http://www.infoworld.com/d/networking/gnome-extends-reach-mobile-and-embedded-devices-685](http://www.infoworld.com/d/networking/gnome-extends-reach-mobile-and-embedded-devices-685)

Linux enterprise application on Mobile Phones is quite likely the largest share of commercial linux's.

And Qt is now owned by Nokia. You know, Nokia, the mobile phone giant.

> **WitchCraft said:**
> 
Google Chrome uses GTK instead of QT.
(remember, google also develops mobile phone platforms - just an arbitrary coincidence?)

And Google Earth uses Qt.
(remember, google also develops mobile phone platforms - just an arbitrary coincidence?)

Anyway, you obviously made your assertion without having numbers to back it up.
But as this is a thread about chromium, I think we have taken it off topic and should better stop. So that'll be my final post on the subject.

---

### Post by zekopeko on 2009-06-10
> **WitchCraft said:**
> <snip what i said>

Torvalds hates gnome, but switched to gnome (had to) ...

he didn't like where early KDE4 releases were going. and using the preferences of the linux creator aren't considered arguments...

> 
And it's gnome that is on mobile devices (all the qt bloat doesn't fit in a mobile phone)
[http://www.infoworld.com/d/networking/gnome-extends-reach-mobile-and-embedded-devices-685](http://www.infoworld.com/d/networking/gnome-extends-reach-mobile-and-embedded-devices-685) lame. google some more. KDE has been ported (in parts) to nokia's maemo platform and symbian. saying "qt bloat doesn't fit in a mobile phone" is pure ignorance or intentional malice. your pick.

> 
Linux enterprise application on Mobile Phones is quite likely the largest share of commercial linux's. trueeeeeeeee. probably right or close to linux's server share.

> 
Google Chrome uses GTK instead of QT.
(remember, google also develops mobile phone platforms - just an arbitrary coincidence?) true. but it's not an argument for GTK since the google engineer working on the port of chrome used GTK because it was familiar for him and his team. they might have used Qt if it was familiar to them.

> 
... continue list here ...

maybe i'll still find a statistics that confirms what's quite obviously true.

and what would that be? that there are more Gnome desktops in use then KDE? that's true. but the statistics i can remember are just 5-10% in favor of Gnome.

---

### Post by WitchCraft on 2009-06-10
> **Closed_Port said:**
> Ah, I think that's the problem.

You can find nightly builds of chromium in the following ppa:
[https://edge.launchpad.net/~chromium-daily/+archive/ppa](https://edge.launchpad.net/~chromium-daily/+archive/ppa)

Using this it works for me.

Thanks, I'll try that.

---

### Post by WitchCraft on 2009-06-10
> **zekopeko said:**
> 
saying "qt bloat doesn't fit in a mobile phone" is pure ignorance or intentional malice. your pick.


Actually, that was intentional malice. 
I hate QT.

Sure you can do it with QT, too, since you need to implement the GTK widgets, too ;-)



But chances are that if a manufacturer can only choose one of GTK/KDE, he will probably choose gnome, because it's simply more popular, more people developing, etc.

But we will see. And I sincerely hope it's not gonna be KDE that wins.

---

### Post by BlazeFire247 on 2009-06-10
I want to use this for Ubuntu, but I'm a Firefox user (and a fan, too). I saw a Chrome theme for FF, but it doesn't support my version of Firefox :(

---

### Post by sertse on 2009-06-10
Been trying the chromium daily builds. Fast. Not featureful, but perfectly acceptable for my own uses which most of the is just browsing. I am live without extensions. 

gtk, but it doesn't integrate with my theme?

---

### Post by biji on 2009-06-10
> **WitchCraft said:**
> 
QT? Why? QT is antiquated.

Yup i agree.. qt is antiquated hahahah :p

---

### Post by lovinglinux on 2009-06-11
> **BlazeFire247 said:**
> I want to use this for Ubuntu, but I'm a Firefox user (and a fan, too). I saw a Chrome theme for FF, but it doesn't support my version of Firefox :(

[Chromifox Basic](https://addons.mozilla.org/en-US/firefox/addon/8782) - Firefox: 3.0 – 3.5.* 

[Chromifox Extreme](https://addons.mozilla.org/en-US/firefox/addon/10674) - Firefox: 3.1b1 – 3.6a1pre 

If you have an older version of Firefox, then it would be advisable to upgrade.

---

### Post by WitchCraft on 2009-06-13
> **biji said:**
> Yup i agree.. qt is antiquated hahahah :p

haha, the QT from the repositories crashes on my computer...
Must be the new glibc & kernel that runs on my computer - or it doesn't work on x64...

Edit:
And not so Haha: Sig 11 (SigSegv) on COMPILING!
Now, talking about bad technology, that never happend with wxWidgets...

---

### Post by Wiiboy on 2009-06-23
Today, I noticed that you can drag tabs from one window to another.  Chromium devs might actually be able to finish it up by the end of the month.

---

### Post by WitchCraft on 2009-06-24
> **Wiiboy said:**
> Today, I noticed that you can drag tabs from one window to another.  Chromium devs might actually be able to finish it up by the end of the month.

Cool.

And I noticed that Chrome now also can screw up the gnome bottom panel, that is to say after it already managed to screw up the top panel last week after a crash.

---

### Post by pt123 on 2009-06-24
they need to address the horrible font display

---

### Post by philcamlin on 2009-06-24
lol thats cool :popcorn:

---

