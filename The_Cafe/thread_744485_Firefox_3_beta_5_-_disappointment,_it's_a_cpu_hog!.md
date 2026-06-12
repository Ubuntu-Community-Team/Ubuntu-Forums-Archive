---
title: "Firefox 3 beta 5 - disappointment, it's a cpu hog!"
date: 2008-04-03
forum: The Cafe
---

### Post by olavjunior on 2008-04-03
I've been so satisfied with every beta of firefox 3. But the latest I downloaded today is a giant cpu eater! Had to downgrade to beta 4 :( Anybody else experience this?

---

### Post by wPwLUi3N on 2008-04-03
I share the same sentements. Beta 4 is better than beta 5 i hope the final version is light on resources.

---

### Post by esttorhe on 2008-04-03
[color=darkred][b]I guess we wont know until june
so far so good, i havent tried the beta 5, but i think i wont do it until beta 6 or final release thanks to your comments[/b][/color]

---

### Post by |2A|N on 2008-04-03
I have not experienced any change in resources so to speak with Beta 5 and as far as I know the next release is going to be a Pre-Release/ RC according to there nightly builds so there will be no beta 6.

---

### Post by Kernel Sanders on 2008-04-03
I can't reproduce this. Beta 5 is fine for me? What extensions are you using?

---

### Post by esttorhe on 2008-04-03
[color=darkred][b]mmm, i guess im going to try the beta 5 anyway
and wait until the pre-release

where do you found the information about no beta 6?
i wasnt able to find anything that seems like that on the site[/b][/color]

---

### Post by drascus on 2008-04-03
well you could always not use firefox 3 if it's really not that good. I hear that Icecat is really good. And it is pretty much the same thing a firefox the only difference is a bit of its code and the license.

---

### Post by Koori23 on 2008-04-03
I have not noticed Beta 5 being more resource intensive myself. However, I absolutely hate the drop down box in the address bar.

---

### Post by madjr on 2008-04-04
> **Koori23 said:**
> I have not noticed Beta 5 being more resource intensive myself. However, I absolutely hate the drop down box in the address bar.

i love the drop down box, but there might be an option to deactivate it in **about:config** or something...

i have beta 3 is light on resources.

---

### Post by jdong on 2008-04-04
I've heard a lot of reports ff3b5 is more CPU intensive with random CPU spiking than ff3b4. It sounds like a regression. That's why these are betas and not final releases!

---

### Post by olavjunior on 2008-04-04
> **Kernel Sanders said:**
> I can't reproduce this. Beta 5 is fine for me? What extensions are you using?

I'm using the same plugins as with the 4, and less of my extensions since not as many work with the 5 (ex speed dial) I use stumble upon and adblock plus...

---

### Post by herbster on 2008-04-04
Isn't the final release another beta, and every update another beta? Or did I just blow your mind?

---

### Post by Koori23 on 2008-04-04
> **herbster said:**
> Isn't the final release another beta, and every update another beta? Or did I just blow your mind?

Don't you go playing those Jedi mind tricks with me. If that's the case, Windows XP has been in Beta since 2001

 These questions you pose have plagued mankind for centuries, I'm afraid the collective wisdom of our current society cannot provide answers. 

Man.. that should be a fortune cookie. Sometimes I surprise myself

---

### Post by Therion on 2008-04-04
> **herbster said:**
> Isn't the final release another beta, and every update another beta? Or did I just blow your mind?
That's an ongoing debeta.


> **Koori23 said:**
> Don't you go playing those Jedi mind tricks with me.
This is not the browser you're looking for.  Move along.

---

### Post by pjalegria on 2008-04-04
Opera rules....:lolflag:

---

### Post by Koori23 on 2008-04-04
> **Therion said:**
> That's an ongoing debeta.



This is not the browser you're looking for.  Move along.


Oops.. It appears I used that phrase out of context. I shouldn't have used it at all. I've never seen Star Wars.

---

### Post by jdong on 2008-04-04
> **herbster said:**
> Isn't the final release another beta, and every update another beta? Or did I just blow your mind?

I don't know how your release engineers work, but no that's not supposed to be the case :)

---

### Post by Lord Illidan on 2008-04-04
> **jdong said:**
> I don't know how your release engineers work, but no that's not supposed to be the case :)

Unless you work at google.
-> points at Gmail

---

### Post by esttorhe on 2008-04-04
i wasnt able to make it work fine
i run it from the terminal and the console output was
> No es posible cargar el módulo de carga de imágenes: /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so: /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so

The first part is traslated as "Unable to load the images loader module" :S

---

### Post by SomeGuyDude on 2008-04-04
Swiftfox, which is somehow on 3.0pre1, is pretty dynamite.

---

### Post by mrgnash on 2008-04-05
> **pjalegria said:**
> Opera rules....:lolflag:

Yeah, I don't think that I would be able to say that with a straight face either.

---

### Post by D4niel on 2008-04-06
i have the same problem using beta 5...hope the next release will fix it..

---

### Post by jdong on 2008-04-06
Hmm I backported Firefox 3.0 beta 5 from Hardy and cannot reproduce any CPU problems.

If any daring souls are interested, see [https://launchpad.net/~ubuntu-backporters/+archive](https://launchpad.net/~ubuntu-backporters/+archive) for the APT repo.

---

### Post by mrgnash on 2008-04-06
No CPU problems here, either.

---

### Post by sports fan Matt on 2008-04-06
I cant reproduce it either..I only have Forecastfox enhanced and Yahoo maqil notifier as extensions and no cpu spike...if anything its faster then FF2

---

### Post by munkyeetr on 2008-04-06
> **Koori23 said:**
> I have not noticed Beta 5 being more resource intensive myself. However, I absolutely hate the drop down box in the address bar.

To disable the dropdown box:

1) Enter **about:config** in the address bar
2) Set **browser.url.maxRichResults**=**0**

---

### Post by stu2004 on 2008-04-19
just upgraded to ff3 beta 5. I don't have any extensions apart from the ubuntu one. I'm on hardy.

CPU usage is not great :-( 50% usage just for firefox.

hope the rc will be better. 5 < 4 if you see what i mean.

Stu

---

### Post by Kiri on 2008-04-19
I also have high CPU usage with FF beta. But I believe that it is actually a problem with the flash plugin in the linux version...

Those experiencing high CPU usage, check if you have the flash plugin installed, and if you are viewing a page with some flash in it (it might only be a header or something)

---

### Post by jdong on 2008-04-19
If you have Flash on hardy, **uninstall libflashsupport**, which is known to cause Flash to crash (and was demoted right before the RC). This could generate the high CPU usage as apport collects crash information in the background.

Otherwise, I've been running my two laptops on Hardy with FF3b5 without an issue.

---

### Post by Kiri on 2008-04-19
lib flashsupport is uninstalled on mine, but I still get the high CPU usage.
It is definately a flash issue, because I tried uninstalling flash and my firefox usage went from 30% to 2%

---

### Post by Sunflower1970 on 2008-04-19
I was having CPU spikes myself with FF3b5 which started yesterday. But mine was due to the recent update of the udpate manager. I removed update manager and all has been back to normal with FF3b5.

---

### Post by Jaxco on 2008-04-19
Hey guys, relative newb here... how do you instaall the FF3b5 package?  I have already downloaded it from the FF homepage and followed their instructions to the letter, to no avail.

Thanks in advance!! :guitar:

---

### Post by andrewabc on 2008-04-19
> **Jaxco said:**
> Hey guys, relative newb here... how do you instaall the FF3b5 package?  I have already downloaded it from the FF homepage and followed their instructions to the letter, to no avail.

Thanks in advance!! :guitar:

What version of ubuntu are you using?
I'm guessing gutsy.
If you are planning on updating to hardy in a week or two, I'd just wait until then. It comes with hardy by default.

I don't know how to install it in gutsy, sorry.

---

### Post by SuperSon!c on 2008-04-19
FF3b5 is the fastest of all the previous releases....in Windows XP.  for my ubuntu install, it's horrid.

---

### Post by TeraDyne on 2008-04-19
> **andrewabc said:**
> What version of ubuntu are you using?
I'm guessing gutsy.
If you are planning on updating to hardy in a week or two, I'd just wait until then. It comes with hardy by default.

I don't know how to install it in gutsy, sorry.

An LTS release is going to be released with beta software? Are you serious?

---

### Post by Jaxco on 2008-04-19
> **TeraDyne said:**
> An LTS release is going to be released with beta software? Are you serious?

i was wondering about that too... hmmmm

---

### Post by jdong on 2008-04-19
> **TeraDyne said:**
> An LTS release is going to be released with beta software? Are you serious?

The rationale is 3 years down the road, it is **highly unlikely** for the Firefox 2.0 series to still be supported by Mozilla and we'd be completely on our own to patch the browser security-wise, like what happened with Dapper.

---

### Post by Saint Angeles on 2008-04-19
firefox 3 beta 5 works just fine... why don't you take the time to try it?

it was a great idea to put it in hardy.

---

### Post by TeraDyne on 2008-04-19
> **Saint Angeles said:**
> firefox 3 beta 5 works just fine... why don't you take the time to try it?

it was a great idea to put it in hardy.

I have. As far as resources go, It's somewhat painful. I think I'll stick with SeaMonkey. Same for when I switch to Hardy.

---

### Post by jdong on 2008-04-19
Firefox 3 for me takes fewer resources than any other browser I've used to date. 22 tabs across a week's browsing and it's hovering around 95MB memory usage.

---

### Post by TBOL3 on 2008-04-19
> **TeraDyne said:**
> An LTS release is going to be released with beta software? Are you serious?

I don't think that's too much of a problem.  If you take a look at all of the gnome apps they ship by default, they are ugly, slow, and buggy (well, about half are anyway, some are clean, fast, and mostly bug free).

---

### Post by TeraDyne on 2008-04-19
> **TBOL3 said:**
> I don't think that's too much of a problem.  If you take a look at all of the gnome apps they ship by default, they are ugly, slow, and buggy (well, about half are anyway, some are clean, fast, and mostly bug free).

Point taken. Still, I wish they'd use a stable release for a key app in an LTS version, rather than relying on a beta. I mean, I'd love to see SeaMonkey by default, but I'd settle for a stable FF2 over a buggy CPU hog like FF3b5.

---

### Post by Polygon on 2008-04-19
only some people are experiencing the cpu issue. Im not experiencing it in either windows or linux.

and i would take ff3b5 over ff2 any day. The improvements are so much better.

---

### Post by perlluver on 2008-04-19
I'm hovering around 9 to 19 % with ff3b5 running, so no complaints from me.

---

### Post by jacob01 on 2008-04-19
I'm running firefox 3 beta 5 and I'm not experiencing and cpu usage issues.

---

### Post by jesusfreak107 on 2008-04-19
it does hog some memory when using flash, in my experience.  Just thought I would add another experience on there to corraborate the previous problems.  When running Pandora (internet radio that runs entirely off of flash), I have seen my FF3b5 take up as much as 180MB of RAM.  I have a good proccessor, so it does not slow it down, but it is still a hog.

---

### Post by TeraDyne on 2008-04-19
> **jesusfreak107 said:**
> it does hog some memory when using flash, in my experience.  Just thought I would add another experience on there to corraborate the previous problems.  When running Pandora (internet radio that runs entirely off of flash), I have seen my FF3b5 take up as much as 180MB of RAM.  I have a good proccessor, so it does not slow it down, but it is still a hog.

That may be my problem. I view a lot of YouTube videos, and flash might be what's hitting my processor, rather than FF itself. I'll look into it later, once I've installed Hardy on my laptop.

---

### Post by Kiri on 2008-04-20
> **TeraDyne said:**
> That may be my problem. I view a lot of YouTube videos, and flash might be what's hitting my processor, rather than FF itself. I'll look into it later, once I've installed Hardy on my laptop.

I can pretty much guarantee you its the flash plugin that is causing the CPU usage. Unfortunately that doesn't really help us unless you don't want to be able to use flash sites. 
I tried installing gnash (linux alternative to flash) yesterday but it had the same problems.

---

### Post by swoll1980 on 2008-04-20
The only thing I have noticed about ff3b5 is the improvements. For different people to say it's faster or slower than 2 is inconsistent and would seem impossible it's either one or the other or neither, not both. I would like to see something to back up the claims of faster or slower. When I used the system monitor the results for me were identical. I think a lot of this faster slower stuff is placebo

---

### Post by Saint Angeles on 2008-04-20
with compiz, ff3b5 (with 4 tabs open), pidgin, and mplayer (watching a dvd)... i'm only at 19% RAM usage and between 7 and 20 % CPU.

i'm awesome!

---

### Post by swoll1980 on 2008-04-20
+ what ever your using to see your resources

---

### Post by misfitpierce on 2008-04-20
Beta 5 does not hog my CPU. I love Beta 5 and it works fine for me.

---

### Post by Kiri on 2008-04-20
> **swoll1980 said:**
> The only thing I have noticed about ff3b5 is the improvements. For different people to say it's faster or slower than 2 is inconsistent and would seem impossible it's either one or the other or neither, not both. I would like to see something to back up the claims of faster or slower. When I used the system monitor the results for me were identical. I think a lot of this faster slower stuff is placebo

.

---

### Post by Polygon on 2008-04-20
[[IMG]http://img366.imageshack.us/img366/5778/test5il5.th.png[/IMG]](http://img366.imageshack.us/my.php?image=test5il5.png)

and thats even with pandora radio playing. (flash)

ill post a one of ubuntu later, but its mostly the same thing.

---

### Post by duncanmak on 2008-04-23
I run Gutsy on my eee pc, and I've been using beta 5 since the day it hit the PPA, and it was running just fine.

However, I've started experiencing major perf. degradation since this past weekend.

I think someone suggested that the problem might stem from the new update of 'update-manager'. Why is that the case? I tried removing it and I didn't see any improvement.

I also noticed that even when firefox is not using up 100% of my CPU, the Xorg process is still more active than usual.

Has anyone found a solution to this problem? It seems to me that it's a bug in the interaction between Xorg and firefox.

---

### Post by adityakavoor on 2008-04-23
Beta is buggy as hell

---

### Post by Enigmatic on 2008-04-24
How does one downgrade to beta 4? Beta 5 tends to use huge amounts of CPU, I have to restart Firefox quite often to try and get smoother performance. It often happens when selecting an address from the address bar history.

---

### Post by SuperSon!c on 2008-04-24
> **duncanmak said:**
> I run Gutsy on my eee pc, and I've been using beta 5 since the day it hit the PPA, and it was running just fine.

However, I've started experiencing major perf. degradation since this past weekend.

I think someone suggested that the problem might stem from the new update of 'update-manager'. Why is that the case? I tried removing it and I didn't see any improvement.

I also noticed that even when firefox is not using up 100% of my CPU, the Xorg process is still more active than usual.

Has anyone found a solution to this problem? It seems to me that it's a bug in the interaction between Xorg and firefox.

i have this EXACT same problem, even after a new install on both ubuntu and kubuntu, but REALLY bad on ubuntu.  for now i'm using opera. 

p.s. i must point out that i had no extensions/themes/add-ons installed.

---

### Post by Enigmatic on 2008-04-24
I tried this, seems to have worked thus far:

[http://ubuntuforums.org/showthread.php?p=4770985#post4770985](http://ubuntuforums.org/showthread.php?p=4770985#post4770985)

---

### Post by jsully1 on 2008-04-24
Thanks so much, that fixed it!

---

### Post by FuturePilot on 2008-04-24
> **Enigmatic said:**
> I tried this, seems to have worked thus far:

[http://ubuntuforums.org/showthread.php?p=4770985#post4770985](http://ubuntuforums.org/showthread.php?p=4770985#post4770985)

> **jsully1 said:**
> Thanks so much, that fixed it!

That only seems temporary. Give it some time, Firefox will get hungry again and eat your CPU and hard drive. :shock:

---

### Post by jdong on 2008-04-25
```

-rw-r--r--  1 jdong jdong  30M 2008-04-24 23:56 urlclassifier3.sqlite
-rw-r--r--  1 jdong jdong  154 2008-04-24 17:50 urlclassifierkey3.txt

```

Sweet mother.... that's either a bug or one hell of a price to pay for phishing protection!

---

### Post by castrojo on 2008-04-25
[https://bugs.edge.launchpad.net/ubuntu/+source/xorg/+bug/215728](https://bugs.edge.launchpad.net/ubuntu/+source/xorg/+bug/215728)

That is the relevant bug. Mozilla upstream is aware and working on a fix. Please subscribe to the bug if you have this issue, upstream will update and ask for help testing.

---

### Post by FuturePilot on 2008-04-25
> **jdong said:**
> ```

-rw-r--r--  1 jdong jdong  30M 2008-04-24 23:56 urlclassifier3.sqlite
-rw-r--r--  1 jdong jdong  154 2008-04-24 17:50 urlclassifierkey3.txt

```

Sweet mother.... that's either a bug or one hell of a price to pay for phishing protection!
yeah :shock: Just a while ago Firefox was trashing my hard drive for 10 minutes straight. 
> **whiprush said:**
> [https://bugs.edge.launchpad.net/ubuntu/+source/xorg/+bug/215728](https://bugs.edge.launchpad.net/ubuntu/+source/xorg/+bug/215728)

That is the relevant bug. Mozilla upstream is aware and working on a fix. Please subscribe to the bug if you have this issue, upstream will update and ask for help testing.

Oh good, upstream knows about it. Hopefully we will get a fix soon. :)

---

### Post by jdong on 2008-04-25
> **whiprush said:**
> [https://bugs.edge.launchpad.net/ubuntu/+source/xorg/+bug/215728](https://bugs.edge.launchpad.net/ubuntu/+source/xorg/+bug/215728)

That is the relevant bug. Mozilla upstream is aware and working on a fix. Please subscribe to the bug if you have this issue, upstream will update and ask for help testing.

Thanks! That's very good info to know :)

---

### Post by SuperSon!c on 2008-04-25
good deal, it's not placebo after all.  whoever brought that up earlier, i lol in your direction.

---

### Post by sveterv on 2008-04-25
I must agree, this beta is so sloooow. Even bookmarks menu scrolling is slower than in Firefox 2.0. I'm using realtime kernel, so now it's little more responsive, but I'm really disappointed. Sometimes, when browsing for longer time it just slows to the point where restarting it, is the only solution. I've not used earlier FF 3.0 betas, so don't know is this a problem of beta 5 or all the 3.0 versions. It's not that it uses CPU constantly at some high level, but it's more about worse responsiveness.

---

### Post by SuperSon!c on 2008-04-25
^it's only a problem in kubuntu/ubuntu for me.  all of the windows boxen i use do not show this behaviour at all and, to be honest, this version is the fastest version of all the ones i've used previous.

---

### Post by mrgnash on 2008-04-25
> **SuperSon!c said:**
> ^it's only a problem in kubuntu/ubuntu for me.  all of the windows boxen i use do not show this behaviour at all and, to be honest, this version is the fastest version of all the ones i've used previous.

Yep, as far as I know, the problem is confined to Fx3B5 on Ubuntu. Not that I am seeing the problem myself, but yeah.

---

### Post by SuperSon!c on 2008-04-25
i know they'll get this fixed fairly quickly, so that's good.  not that mind opera which is quite good, but i do miss some of my extensions and themes.

---

### Post by marcw on 2008-04-25
Until there's a permanent fixed posted for this problem, I'm using a workaround I saw in another thread.  Instead of using the default profile, create and use another profile from the Profile Manager.  firefox -ProfileManager

---

### Post by jdong on 2008-04-25
> **marcw said:**
> Until there's a permanent fixed posted for this problem, I'm using a workaround I saw in another thread.  Instead of using the default profile, create and use another profile from the Profile Manager.  firefox -ProfileManager

All of the workarounds involve either turning off the URL classifier in options or removing the urlclassifier3.sqlite file periodically... Creatinga  new profile is just a brute way of doing the latter.

---

### Post by soro2005 on 2008-04-26
> **jdong said:**
> All of the workarounds involve either turning off the URL classifier in options or removing the urlclassifier3.sqlite file periodically... Creatinga  new profile is just a brute way of doing the latter.

The bottom line is: It stinks! :mad: But then, we all knew that epiphany + webkit was the new firefox, didn't we? :) Too bad I need zotero and firebug. :(

Ok, this particular one is going to be sorted out quick. I wish that Firefox was as lean and mean as Epiphany, and you'd just install whatever modules you want/need. Those times are gone, it seems. :(

---

### Post by SuperSon!c on 2008-04-26
> **soro2005 said:**
> The bottom line is: It stinks! :mad: But then, we all knew that epiphany + webkit was the new firefox, didn't we? :) Too bad I need zotero and firebug. :(

Ok, this particular one is going to be sorted out quick. I wish that Firefox was as lean and mean as Epiphany, and you'd just install whatever modules you want/need. Those times are gone, it seems. :(

no, it's not the new FF.  this version of FF is the best of all the previous releases on Windows and i have no doubt it'll live up to that on *nix.

---

### Post by wolffangalchemist on 2008-04-26
I'm new to the beta and the only real problems i noticed was it crashes a lot when you watch videos on youtube and if theres a lot of gifs on a page your viewing other than that the speed with everything else is quite astounding.
i spend a lot of time on youtube though and it kinda does hog the cpu or graphics card when I'm using compiz fusion i just turn it off though. 
they really should have given us who upgraded to or installed hardy a option with this!
i expect the final version to be more efficient and hopefully this is the final beta.

---

### Post by rajeev1204 on 2008-04-26
Am i the only one who cant use ctl T to open a new tab? Happens randomly to me. atleast 50 % of the time.

---

### Post by JohnSearle on 2008-04-26
> **rajeev1204 said:**
> Am i the only one who cant use ctl T to open a new tab? Happens randomly to me. atleast 50 % of the time.

I've been using FF3-b5 since it's release, and I haven't had a ctrl-t problem yet. I've had the CPU issue, though. Seems to be somewhat mitigated by the removal of those 'key' files.

- John

---

### Post by aamukahvi on 2008-04-26
> **wolffangalchemist said:**
> I'm new to the beta and the only real problems i noticed was it crashes a lot when you watch videos on youtube
It crashes almost everytime on *any* site with Flash. Is this just my problem? Reinstall?

Epiphany w/ Gecko 1.9 & Flash works just fine. It hasn't crashed once!

---

### Post by pacrep on 2008-04-26
I beg to differ, I'm running 700mhz pIII firefox runs pretty fast on my system, using the default RC5. 13% of my 384Mb of ram, on my satellite connection. At times faster than my Vista FF2.0.13 using Fasterfox.

---

### Post by gwilson on 2008-04-26
I've had a number of problems with Firefox 3 Beta, Rajeev, and decided to go back to Firefox 2 until the new version is ready for general use. I may incur the wrath of some moderator by saying it, but I can't help wondering why they included beta software in the general release when they could simply have made the new version avaialble in the repositories when it was ready. Obviously, the Firefox developers (who should know) were of the opinion that Firefox 3 wasn't finished.

I may be an unsophisticated browser, but I don't really see all that much that's new and different other than the fact that Firefox 2 works and Firefox 3 does not.

---

### Post by misfitpierce on 2008-04-26
Well my CPU gets mid ranged when loading a page (normal) and then it goes right back down. CPU usage not a problem for me and flash and CTRL+T work 100% fine. No crashes or anything :) lol

---

### Post by jdong on 2008-04-26
(1)CTRL-T won't open a tab only if a Flash applet is currently having the focus. It could be a bug or a feature (i.e. otherwise flash applications cannot use the ctrl-t key combo or any other Firefox reserved combo for that matter)

(2) This is a **bug** in Firefox, not its designed behavior. Upstream and Ubuntu developers are aware of it and are working towards fixing it. IMO bugs like this should not be used to judge the merit of Firefox as a whole for comparing it with some other browser.

---

### Post by Lord DarkPat on 2008-04-26
Opera FTW!!! No, but seriously, I have used it for a while, Flash hates it, and I really like how it predicts some text on the website which you type in the add. bar. can't wait for it to come outta beta!!!

---

### Post by stef70 on 2008-04-28
Today, Firefox3b5 suddenly decided to eat my all CPU.

However, I managed to solve the problem by disabling the automatic update for the "Installed Add-ons" in the Advanced/Update preferences. I had to restart FF after that.   

Stef

---

### Post by iTronz on 2008-04-28
Hey guys, 

Sorry if I'm asking in the wrong place, but can anyone tell me how to downgrade to firefox beta 4 or firefox v2. Beta 5 is too buggy, the backward and forward buttons are grayed out and the address bar stays empty. 

Any help is appreciated :).

---

### Post by chameleonkid on 2008-04-28
I guess I don't still see why they wouldn't have included FF2 as the main browser then later on down the road make the switch to FF3. Why go with something in beta when theres something perfectly fine already. Oh well. I don't mind the new version but I miss the old behavior of the drop down address bar, and I can't go back to FF2 because for some reason mpegs won't play in the browser, but they do in FF3.

---

### Post by SuperSon!c on 2008-04-28
> **iTronz said:**
> Hey guys, 

Sorry if I'm asking in the wrong place, but can anyone tell me how to downgrade to firefox beta 4 or firefox v2. Beta 5 is too buggy, the backward and forward buttons are grayed out and the address bar stays empty. 

Any help is appreciated :).

do a search for firefox 3 in synaptic then check for complete removal and apply changes.  then, search for firefox 2 and check for installation.

---

### Post by stmiller on 2008-04-28
Firefox 3 has mega-improvements over FF2. Check out the release notes before you toss it out:

[http://www.mozilla.com/en-US/firefox/3.0b5/releasenotes/#whatsnew](http://www.mozilla.com/en-US/firefox/3.0b5/releasenotes/#whatsnew)

---

### Post by SuperSon!c on 2008-04-28
> **stmiller said:**
> Firefox 3 has mega-improvements over FF2. Check out the release notes before you toss it out:

[http://www.mozilla.com/en-US/firefox/3.0b5/releasenotes/#whatsnew](http://www.mozilla.com/en-US/firefox/3.0b5/releasenotes/#whatsnew)

overall yes, it's a big improvement, but this is a bug with ff4b5 on linux.  i don't have the cpu spike issue under windows using it.

---

### Post by qamelian on 2008-04-28
> **chameleonkid said:**
> I guess I don't still see why they wouldn't have included FF2 as the main browser then later on down the road make the switch to FF3. Why go with something in beta when theres something perfectly fine already. Oh well. I don't mind the new version but I miss the old behavior of the drop down address bar, and I can't go back to FF2 because for some reason mpegs won't play in the browser, but they do in FF3.
Maybe because FF2 wasn't fine for a lot of people. If you browse the forums a bit, you'll discover that most of the main complaints people have made about FF3 were also being made for FF2. Same problems, different users. Personally, you couldn't pay me to go back to FF2. It was not even close to the speed and stability of FF3 beta 5 on any of my systems. FF3 runs fine for me with literally none of the issue reported here. FF2 was always like skipping through a minefield; I never knew when or where it was going to blow up next!

---

### Post by stmiller on 2008-04-28
> **SuperSon!c said:**
> overall yes, it's a big improvement, but this is a bug with ff4b5 on linux.  i don't have the cpu spike issue under windows using it.

This is weird. I do not have this problem at all in Kubuntu 8.04 64bit. I'm using a Linux 32bit download of FF3b5 from mozilla.com though.

Could be related to the Ubuntu package of FFb3? Or some of the Ubuntu FF add-on stuff?

---

### Post by jdong on 2008-04-28
> **stmiller said:**
> This is weird. I do not have this problem at all in Kubuntu 8.04 64bit. I'm using a Linux 32bit download of FF3b5 from mozilla.com though.

Could be related to the Ubuntu package of FFb3? Or some of the Ubuntu FF add-on stuff?

No, it's a specific problem with the sqlite flushing technique that only affects certain sizes/states of the SQLite databases, and isn't always readily reproducible. I have one system that exhibits this bug and another system that does not, both using virtually identical setups and cloned firefox profiles.

---

### Post by dustinwind on 2008-04-30
i completely agree. Firefox 3 beta 4 is the best browser i've ever used.

anybody, please show me how to downgrade from beta 5 to beta 4

thank you

---

### Post by SuperSon!c on 2008-04-30
> **stmiller said:**
> This is weird. I do not have this problem at all in Kubuntu 8.04 64bit. I'm using a Linux 32bit download of FF3b5 from mozilla.com though.

Could be related to the Ubuntu package of FFb3? Or some of the Ubuntu FF add-on stuff?

no add-on's here.

---

### Post by egwest on 2008-05-01
I just uninstalled the darn thing and installed SeaMonkey. I was not liking some of the changes they made. Of course that is just me. I thought it was fine the way it was.
Sometimes I think they over do some changes. But again, it is just my point of view.

---

### Post by L1vingd3ad on 2008-05-07
I also have the same problem with CPU usage. It does get annoying at times but I still haven't tried the workaround of deleting the sql files. Will try later at home and see how it goes.

---

### Post by SupaSonic on 2008-05-07
I use beta 4 at work in Gutsy, and it ran smoothly until yesterday, when I had the CPU issue. After deleting the sqlite files though it's back to normal.

But beta5 is awful - it's slow, frequently hangs for a couple of seconds, requires restarts when flash becomes grey. It's a huge diappointment.

---

### Post by SuperSon!c on 2008-05-07
deleting that file is temporary.  i found myself deleting it every other day at least, so i'm on opera till that's fixed. where can we go to keep an eye on this issue?

---

### Post by plun on 2008-05-07
> **SuperSon!c said:**
> deleting that file is temporary.  i found myself deleting it every other day at least, so i'm on opera till that's fixed. where can we go to keep an eye on this issue?

Well, this bug is really tragic and was known before Hardy was released.

The update should be out now.  


[https://bugs.launchpad.net/firefox/+bug/215728](https://bugs.launchpad.net/firefox/+bug/215728)


:)

---

### Post by SuperSon!c on 2008-05-07
> **plun said:**
> Well, this bug is really tragic and was known before Hardy was released.

The update should be out now.  


[https://bugs.launchpad.net/firefox/+bug/215728](https://bugs.launchpad.net/firefox/+bug/215728)


:)

i wasn't using ubuntu much before hardy, just on and off.  thanks for the link.  is this something that will be an automatic update? i don't see anything there that says otherwise.

---

### Post by 23meg on 2008-05-07
Yes, it's in hardy-updates now. Just wait until it hits your repo.

---

### Post by SuperSon!c on 2008-05-07
thx mang

---

### Post by jdong on 2008-05-07
The update resolved these symptoms on my Macbook , at least it so seems for now. Will keep you guys posted if it comes back after a few days.

---

### Post by SuperSon!c on 2008-05-07
thx jdong.  like i said i've been using opera which mostly is fine except some flakiness in gmail, but last night i downloaded FF2 and christ is that slow compared to ff3b5.

---

### Post by geoken on 2008-05-07
Has anyone noticed any problems with these updates? I ran some updates yesterday (not sure if any firefox updates were in there). 

I started noticing some huge Firefox slowdowns yesterday. I get 5-10 second period of complete unresponsivenes every time I open a new tab. I also get this unresposivenes when I open a link in the same tab and sometimes I get it without even doing anything. 

I disabled Flash to rule that out as a problem (even though I was on sites with no Flash [gmail, this forum]) and it had no effect on the slowdowns.

The strange thing is that these problems only cropped up in the last day or so. Firefox 3b5 has been fine for me the rest of the time I've been on Hardy (since it was released).

---

### Post by SuperSon!c on 2008-05-07
> **geoken said:**
> Has anyone noticed any problems with these updates? I ran some updates yesterday (not sure if any firefox updates were in there). 

I started noticing some huge Firefox slowdowns yesterday. I get 5-10 second period of complete unresponsivenes every time I open a new tab. I also get this unresposivenes when I open a link in the same tab and sometimes I get it without even doing anything. 

I disabled Flash to rule that out as a problem (even though I was on sites with no Flash [gmail, this forum]) and it had no effect on the slowdowns.

well, for me anyway, that's the bug i already have. pre latest updates.

---

### Post by geoken on 2008-05-07
> **SuperSon!c said:**
> well, for me anyway, that's the bug i already have. pre latest updates.

I feel your pain then. It's basically unusable in this state. Hopefully I'll see an update when I get home tonight and it'll resolve this issue. If not, I'm fine going back to FF2 (I miss FireFTP any way)

---

### Post by noremac on 2008-05-07
I scanned through this thread and saw a few others had the same problem with me and that is RAM usage. Its been terrible for me in ff3b5. But it wasnt so bad at all when I was in my Ubuntu 7.10 installation. My conky never reported FF3b5 to be over 11 or 12%. 1GB of RAM so 110-120mb. Not bad. But once I reinstalled to Ubuntu 8.04, the number gets to 18-20% no problem. I have reinstalled the browser and removed my ./.mozilla folder, but nothing seems to help. I installed FF2 and it was actually BETTER as far as RAM usage. That is not good. I may try downgrading to FF3b4, if anyone here thinks that may help. Sounds like it was the best beta version. 

Any ideas?

-Cameron

---

### Post by Kiri on 2008-05-08
Found this:
[http://tombuntu.com/index.php/2008/05/07/firefox-3-excessive-disk-io-and-freezing/]("http://tombuntu.com/index.php/2008/05/07/firefox-3-excessive-disk-io-and-freezing/")

Might help some of you out..

---

### Post by SuperSon!c on 2008-05-08
the latest updates fixed my ff3b5 issue. hopefully everyone else is having the same luck.

---

### Post by SpookyET on 2008-05-08
Firefox on Ubuntu is rubbish compare to its Windows counterpart because it's not built the same way. It's not optimised. 

Check [https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/213708](https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/213708)

---

### Post by noremac on 2008-05-09
If I wanted to try downgrading to ff3b4, whats the best route to doing so? Installing from a tar? Or will it be on the repo's still?

If tar, whats the best source of downloading that? On Mozilla's site, it keeps refering you to the download page of ff3b5

---

### Post by SuperSon!c on 2008-05-09
> **SpookyET said:**
> Firefox on Ubuntu is rubbish compare to its Windows counterpart because it's not built the same way. It's not optimised. 

Check [https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/213708](https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/213708)

this is true. it's not the same under *nix.  opera's a bit faster, but doesn't play nice in gmail for me :/

---

### Post by SupaSonic on 2008-05-09
Just discovered something. I can't edit my post in ff3 beta 4, the buttons Save, Cancel, and Go Advanced don't work ) They work in FF2 though

---

### Post by SuperSon!c on 2008-05-09
> **SupaSonic said:**
> Just discovered something. I can't edit my post in ff3 beta 4, the buttons Save, Cancel, and Go Advanced don't work ) They work in FF2 though

i think i should thank you for your icon.

---

### Post by jmagsho on 2008-05-11
I too have noticed the processor spikes, but do not find that nearly as annoying as the other bugs I've encountered thus far - it seems that a simple right click will do whatever it feels like from time to time - sometimes I get right click other times I get menu dialog boxes, or it opens the bookmark site dialog - truly annoying and weird all at the same time.

---

### Post by SuperSon!c on 2008-05-11
> **jmagsho said:**
> I too have noticed the processor spikes, but do not find that nearly as annoying as the other bugs I've encountered thus far - it seems that a simple right click will do whatever it feels like from time to time - sometimes I get right click other times I get menu dialog boxes, or it opens the bookmark site dialog - truly annoying and weird all at the same time.

funny you mention that.  since i don't experience any such issues as previously mentioned or the issues you JUST mentioned in Windows, i experience those all the time in Ubuntu.  i always right click a link and open a new tab, but half the time the bookmark menu comes up or save link as, etc.  

sticking with opera for now.

---

### Post by Mateo on 2008-05-11
Hmm, all of the Hardy early-adopters told us that FF3 was lighter on resources.  Turns out not to be true.  Looks like Mozilla has turned into yet another software giant that ignores resource management through tightly written code.

---

### Post by nick09 on 2008-05-11
This is my results when I tested firefox 3 beta 5

```

============================================
RESULTS (means and 95% confidence intervals)
--------------------------------------------
Total:                  4862.2ms +/- 3.9%
--------------------------------------------

  3d:                    572.8ms +/- 7.5%
    cube:                208.8ms +/- 8.7%
    morph:               202.6ms +/- 13.6%
    raytrace:            161.4ms +/- 4.6%

  access:                772.4ms +/- 7.5%
    binary-trees:         79.4ms +/- 1.4%
    fannkuch:            342.8ms +/- 2.2%
    nbody:               196.4ms +/- 5.9%
    nsieve:              153.8ms +/- 42.2%

  bitops:                564.4ms +/- 1.0%
    3bit-bits-in-byte:   105.2ms +/- 1.5%
    bits-in-byte:        140.6ms +/- 4.0%
    bitwise-and:         127.4ms +/- 1.5%
    nsieve-bits:         191.2ms +/- 3.1%

  controlflow:            53.2ms +/- 1.0%
    recursive:            53.2ms +/- 1.0%

  crypto:                294.6ms +/- 2.5%
    aes:                 128.0ms +/- 5.0%
    md5:                  85.8ms +/- 6.7%
    sha1:                 80.8ms +/- 1.7%

  date:                  429.4ms +/- 4.2%
    format-tofte:        265.0ms +/- 4.8%
    format-xparb:        164.4ms +/- 3.4%

  math:                  486.6ms +/- 2.7%
    cordic:              206.2ms +/- 1.9%
    partial-sums:        174.8ms +/- 7.6%
    spectral-norm:       105.6ms +/- 0.6%

  regexp:                341.4ms +/- 17.1%
    dna:                 341.4ms +/- 17.1%

  string:               1347.4ms +/- 18.7%
    base64:              146.6ms +/- 6.7%
    fasta:               297.4ms +/- 5.3%
    tagcloud:            262.4ms +/- 14.5%
    unpack-code:         461.8ms +/- 41.5%
    validate-input:      179.2ms +/- 25.9%

```
From: [,%223d-morph%22:[210,185,194,186,238],%223d-raytrace%22:[166,160,167,152,162],%22access-binary-trees%22:[80,79,80,78,80],%22access-fannkuch%22:[339,339,353,339,344],%22access-nbody%22:[209,189,204,190,190],%22access-nsieve%22:[132,134,128,247,128],%22bitops-3bit-bits-in-byte%22:[106,105,107,104,104],%22bitops-bits-in-byte%22:[145,146,137,137,138],%22bitops-bitwise-and%22:[127,127,126,130,127],%22bitops-nsieve-bits%22:[190,186,198,194,188],%22controlflow-recursive%22:[53,54,53,53,53],%22crypto-aes%22:[127,135,131,125,122],%22crypto-md5%22:[81,81,91,89,87],%22crypto-sha1%22:[82,80,82,80,80],%22date-format-tofte%22:[271,254,254,275,271],%22date-format-xparb%22:[165,161,159,170,167],%22math-cordic%22:[209,209,204,207,202],%22math-partial-sums%22:[190,162,177,168,177],%22math-spectral-norm%22:[105,105,106,106,106],%22regexp-dna%22:[425,314,318,321,329],%22string-base64%22:[144,151,138,142,158],%22string-fasta%22:[285,304,289,293,316],%22string-tagcloud%22:[253,234,304,237,284],%22string-unpack-code%22:[391,692,370,313,543],%22string-validate-input%22:[155,228,153,149,211]}"]SunSpider JavaScript Benchmark]("http://webkit.org/perf/sunspider-0.9/sunspider-results.html?{%223d-cube%22:[208,201,230,191,214) Test.

I can't get opera installed because this computer is a AMD Athlon 64-bit.

If I could I would of used [Paste2]("http://www.paste2.org/new-paste") to compare the speeds.

---

### Post by Xanderfoxx on 2008-05-11
They are talking about a particular beta, on a particular platform. Just a minor bug.

---

### Post by Xanderfoxx on 2008-05-11
I happen to like it. I believe it to be a matter of taste, the thing you speak of.

But then, I'm being obvious. I have not noticed a change in resource usage, but I have a slightly more up-to-date system, so I would not notice such things unless I opened a memory monitor and watched for it.

---

### Post by cardinals_fan on 2008-05-11
I've always been bound to Firefox by the Google Toolbar, but just today I became Opera-only.  It's nice and fast :)

---

### Post by jmagsho on 2008-05-11
I have to agree - I find having it pop up all my bookmarks there to be far too annoying.  I can see where some might find it useful however I don't think it is all that intuitive - if you wanted to go to a site you had bookmarked why not just open up your bookmark folder?

---

### Post by northwestuntu on 2008-05-14
i love the new firefox myself.  not too many problems so far and runs quick.

---

### Post by bufsabre666 on 2008-05-14
theres only one feature that im waiting for to become an opera user, and thats the ability to highlight things and then drag them into IM and office windows, it may seem mundane but i do it so much its a feature i wouldnt give up, other than that i LOVE opera

---

### Post by uraldinho on 2008-05-14
If I knew I was going to hate FF3b5 so much, I wouldn't have upgraded to hardy. I also have FF2 but FF3 is the default in hardy, and I don't want to spend ages changing all my settings. 

Computers are about productivity and not making them work.

---

### Post by ubuntu-freak on 2008-05-14
Apart from the fact it closes sometimes, FF3 is pretty good. Disabling the security settings in it's preferences (not really needed in Linux) and deleting the urlclassifier files from /home/.mozilla/firefox/random.default stops it hogging your CPU as well. That's a bug by the way.
 
Nathan

---

