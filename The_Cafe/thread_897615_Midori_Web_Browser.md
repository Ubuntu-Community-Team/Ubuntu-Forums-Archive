---
title: "Midori Web Browser"
date: 2008-08-22
forum: The Cafe
---

### Post by Sef on 2008-08-22
Has anyone else used Midori Web Browser?  It's a small lightweight browser and very fast.  It is alpha, so still lots to do.  With the update to 0.17, it is much more stable now than before.  If you want to try it out, it is available in the universe repository.

---

### Post by ooobuntooo on 2008-08-22
I thought Midori was the name of Microsoft's new web-based OS.

---

### Post by Jengajam2 on 2008-08-22
> **ooobuntooo said:**
> I thought Midori was the name of Microsoft's new web-based OS.

Its also the name of a manga: "Midori Days". Anyway, I tried it, and all I say is that it runs about the same as firefox, but is alot better than opera.

---

### Post by zmjjmz on 2008-08-22
It is really fast in terms of rendering. I was unable to compile the latest version of WebKit, so my version doesn't support plugins (like flash), but if you can compile it it should work.

---

### Post by kirsis on 2008-08-22
I tried it out and immediatly noticed that if the address bar has focus and I press Tab, the search-box does not gain focus.

Also seems slower than Firefox (under a busy system. I'm compiling Mono frmo SVN and have a ton of other apps open). Though I wouldn't say my method was very scientific - I opened ubuntu.com and made it vertically larger/smaller repeatedly :)

Anyway, a browser without an integrated download manager as good as DownThemAll will never lure me away from firefox. It's the only FF extension I can't live without

---

### Post by Majorix on 2008-08-22
Do they even have a webpage? I tried searching for a Midori Browser on Google but got no signs of an official page. Sorry but I won't fall so easily :)

---

### Post by sandysandy on 2008-08-22
just downloaded it. seems to be Ok, maybe slightly slower than firefox.

however it does not support siteadvisor

[http://www.siteadvisor.com/](http://www.siteadvisor.com/)

regards

---

### Post by zmjjmz on 2008-08-22
Everyone should go to acid3.acidtests.org and see their results in Midori.

---

### Post by sandysandy on 2008-08-22
> **Majorix said:**
> Do they even have a webpage? I tried searching for a Midori Browser on Google but got no signs of an official page. Sorry but I won't fall so easily :)

see this

[http://www.twotoasts.de/index.php?/pages/midori_summary.html](http://www.twotoasts.de/index.php?/pages/midori_summary.html)

regards

---

### Post by DoubleClicker on 2008-08-22
> **Sef said:**
> Has anyone else used Midori Web Browser?  It's a small lightweight browser and very fast.  It is alpha, so still lots to do.  With the update to 0.17, it is much more stable now than before.  If you want to try it out, it is available in the universe repository.

Currently midori is at 0.0.19 and a there have been many improvements since 0.0.17,  for the latest builds of midori and webkit  add ```
deb http://ppa.launchpad.net/stemp/ubuntu hardy main 
``` to your sources

---

### Post by Sef on 2008-08-22
> Currently midori is at 0.0.19 and a there have been many improvements since 0.0.17, for the latest builds of midori and webkit add
Code:
deb [http://ppa.launchpad.net/stemp/ubuntu](http://ppa.launchpad.net/stemp/ubuntu) hardy main

Thank you for that.

---

### Post by cardinals_fan on 2008-08-22
It was very buggy on my system.  I'll stick with Kazehakase and Opera.

---

### Post by pt123 on 2008-08-22
The one that came with Hardy, 0.017 didn't work with gmail so I gave it the flick.

You can't also set the number of lines scrolled my the mousewheel, this is what makes Gecko browsers kick Webkit ones in Gnome.

---

### Post by zmjjmz on 2008-08-22
Guys, it's like pre-alpha release, so don't bash it for stability.

---

### Post by voltaire99 on 2008-08-26
I wat to use it as a secondary browser for a change of scenary with a little extra speed, but it crashes on sites with heavy flash use.  For example, try going to youtube.

---

### Post by binbash on 2008-08-26
> **zmjjmz said:**
> Guys, it's like pre-alpha release, so don't bash it for stability.

Then why should someone install it if something always crashes?

---

### Post by zmjjmz on 2008-08-26
> **binbash said:**
> Then why should someone install it if something always crashes?

To debug it.

---

### Post by AptlyNamed on 2008-09-09
Upgrading  Glib 2.16 from the Hardy repos to version 2.18 from the Intrepid repo  fixes the crashing.  See _[COLOR="Blue"][http://wiki.xfce.org/midori_faq](http://wiki.xfce.org/midori_faq) [/COLOR]_

I's a quite basic browser but it has some nice features, such as keyword searches using the urlbar, custom scripts and stylesheets, Webkit rendering engine, and it's lightweight. The _[COLOR="blue"][_Xorg memory ballooning]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/186354")[/COLOR] Firefox causes, and the frequent crashing of Firefox made me look for alternatives and I like Midori, even though I miss some of the  extensions and tricks that I got used to.

You can export firefox bookmarks to xbel format which Midori uses with the _[COLOR="blue"][syncplaces]("http://www.andyhalford.com/syncplaces/download.html")[/COLOR]_ Firefox extension.

Still this is indeed 'alpha' software, so it means it has missing features and rough edges. But it's starting to get usable.

---

### Post by ben2talk on 2008-11-23
> **Jengajam2 said:**
> Its also the name of a manga: "Midori Days". Anyway, I tried it, and all I say is that it runs about the same as firefox, but is alot better than opera.

I'm amazed. On my system, I find that opera fairly flies and renders beautifully, as does firefox - though firefox has a lead with it's extras and sheer power.

Midori is very light, and thus would feel very fast - if it did not disappear in a puff of smoke whenever I load a second tab. Also I find the rendering of the webkit browser lags far behind that of firefox and opera.

Epiphany is a worthy smaller brother to these two magnificent browsers, but Midori being in it's 0.0.21 early stages still requires a lot of work.

It looks extremely promising, but is yet to prove stable on my gnome setup.

---

### Post by chucky chuckaluck on 2008-11-23
> **zmjjmz said:**
> Everyone should go to acid3.acidtests.org and see their results in Midori.

now, if only it could remember my bookmarks...

---

### Post by billgoldberg on 2008-11-23
I tried it on my Asus Eeepc last week.

It's still unstable and I could not get flash to work.

It was pretty fast, but not usable yet.

I use Epiphany as light weigth browser, with adblock :) .

---

### Post by the yawner on 2008-11-23
You guys gave me an idea to try out the available webkit browsers instead of waiting out on how Google Chrome might appear on GNU/Linux. I got Midori _and_ Epiphany from this ppa: [https://launchpad.net/~webkit-team/+archive](https://launchpad.net/~webkit-team/+archive) and I'm trying both browsers now. So... I'm checking out how to enable flash support on both.

Edit:
Ok, both browsers crashed whenever I tried to play a youtube video. I'm using 8.04 and I've recently upgraded my flash plugin to version 10 from Adobe's website. I thought of reverting back to version 9 and so far flash worked on both browsers.

I'm liking Midori more so far over Epiphany. (I found it annoying that I had to install extensions for Epiphany to be able to open links in a new tab.)

---

### Post by Stemp on 2008-11-24
@the yawner : I'm currently uploading midori 0.1.0 and webkit r38688 into the webkit-team ppa for Hardy. Flash should not crash anymore ;)
I only test it in Intrepid, so any feedbacks will be nice.

---

### Post by the yawner on 2008-11-24
> **Stemp said:**
> @the yawner : I'm currently uploading midori 0.1.0 and webkit r38688 into the webkit-team ppa for Hardy. Flash should not crash anymore ;)
I only test it in Intrepid, so any feedbacks will be nice.

I read your post just now and I'm now upgrading my installation. Will post some feedback probably later as it's already way past midnight in my side of the world, and I better catch some sleep.

Thanks much by the way. :)

---

### Post by Stemp on 2008-11-30
midori 0.1.1 is out \o/ (and Webkit 38850)

---

### Post by Mr. Picklesworth on 2008-11-30
The Flash plugin killed Epiphany again (this time the Flash 10 64bit beta), so I eradicated Flash completely. Everything is way nicer now, for me. Now I can complain whenever clueless web developers build Flash-only content, and I can be way more productive in the absense of that awful proprietary thing. It's just like the good old days!

I also have a growing temptation to switch to Konqueror, although Epiphany's newly improved address bar autocomplete is holding me back for now. Midori is a decent alternative...

---

### Post by mirko_3 on 2009-01-07
But is it only me for whom both epiphany-webkit and midori won't open links in new tabs? 
That means that clicking on a google result won't work, as it should open a new tab...

---

### Post by Mr. Picklesworth on 2009-01-07
Epiphany-webkit presently has broken tab handling, and does not do cookies correctly. It's a known bug ;)
The Gecko version does tabs just fine, and the webkit version will probably not be considered stable until it does.

In the mean time, Do Not open tabs in the epiphany-webkit because there is a good chance the browser will then crash somehow.

---

### Post by Stemp on 2009-01-07
I don't know about epiphany-webkit (thanks to Mr. Picklesworth for the info) but no problems with midori.

---

### Post by mirko_3 on 2009-01-07
Uhm weird: in midori, if I right-click and select open in new tab, it opens fine. However if I click on a link that automatically would open up in a new tab/window, nothing at all happens. So to open up Google search results, I have to manually right-click and select open in new tab. 
Btw, I come from Opera, so I never new that Google results open up in new windows... annoying. They should open in new tabs!
So if no one else is seeing this do i report a bug? I'm using the webkit repo..

---

### Post by jrusso2 on 2009-01-07
I think it might turn out to be a decent web browser but its too early to tell.  Google Chrome might takes its place as the lightweight browser when the Linux version comes out.

---

### Post by Stemp on 2009-01-08
@mirko_3 : What version of midori and webkit are you using ?

---

### Post by mirko_3 on 2009-01-09
Midori: 0.1.1-1ubuntu1~intrepidppa3
Webkit: 1.0.1-4+r39572~intrepidppa1

I have this repo in my sources.list:  [http://ppa.launchpad.net/webkit-team/ubuntu](http://ppa.launchpad.net/webkit-team/ubuntu) intrepid main

I've always had this crashed and just assumed everyone had it...

---

### Post by SomeGuyDude on 2009-01-09
> **Jengajam2 said:**
> Its also the name of a manga: "Midori Days".

Also, a drink. And a character in Guitar Hero. :D

As for the browser, lightweight doesn't trump functionality in this case for me. Without my army of extensions my productivity plummets.

---

### Post by Stemp on 2009-01-10
@mirko_3 : Do you have the same problem with GtkLauncher ? 
```
/usr/lib/webkit-1.0/libexec/GtkLauncher
```

---

### Post by ghindo on 2009-01-10
I installed Midori from the repos on Ubuntu 8.10, opened it up, and navigated to Gmail.  Darn thing immediately crashed.

I think it'll be a while before I consider using it with any regularity.

---

### Post by Stemp on 2009-01-10
You installed midori and webkit from the webkit-team PPA or from the official repos ?

---

### Post by ghindo on 2009-01-10
> **Stemp said:**
> You installed midori and webkit from the webkit-team PPA or from the official repos ?From the Ubuntu repos.

---

### Post by Stemp on 2009-01-10
> **ghindo said:**
> From the Ubuntu repos.

Ok they are very outdated.
Midori and Webkit are under heavy development.

---

### Post by mirko_3 on 2009-01-10
> **Stemp said:**
> @mirko_3 : Do you have the same problem with GtkLauncher ? 
```
/usr/lib/webkit-1.0/libexec/GtkLauncher
```


Yeah, exactly the same problem.

---

### Post by andras artois on 2009-01-10
It's fasttttt. I only had a quick go with it but it loaded very fast and loaded web pages faster than firefox. The preferences could do with being more straight forward and customizable but then again it is a lightweight browser. 

Youtube worked perfectly with it. Very fast and loaded up straight away.

I didn't test it with multiple tabs or multiple flash.

Seems like a very promising browser. Would like to see some ad-blocking integrated with it or customizable scripts to allow it.

I was using the latest version in the hardy repositories? And the whatever webkit it decided to install with it.

---

### Post by Stemp on 2009-01-11
> **mirko_3 said:**
> Yeah, exactly the same problem.

Just tested it, and you're right. Webkit doesn't handle it.
In fact i'm always using the middle-button click, so I never notice this bug.

[QUOTE=andras artois]I was using the latest version in the hardy repositories? And the whatever webkit it decided to install with it.[/QUOTE]

There is hardy versions of midori and webkit in the webkit-team ppa if you want to test newer versions.

And for the «adblock » feature you could use a customize css : 

[midori FAQ]("http://wiki.xfce.org/midori_faq#user_styles")
[Ad Blocking user styles]("http://userstyles.org/styles/299")

---

### Post by Praxicoide on 2009-01-30
Very fast browser. I only have 128MB or RAM, so this is a great alternative. Flash works fine, though it crashed on youtube on the second or third video played.

A question: is there a way for it to use Java?

---

### Post by Rokurosv on 2009-01-30
I really like Midori, it's very fast. And it very lightweight, perfect when you wanna do a quick browse on the web

---

### Post by bruce89 on 2009-01-30
> **Praxicoide said:**
> A question: is there a way for it to use Java?

Any of the normal (Mozilla) browser plugins should work the same.

---

### Post by spikey_nick on 2009-02-09
Has anybody else had an issue where midori doesn't render six digit hex colors.  It can render named colors, and the three digit hex.

---

### Post by eragon100 on 2009-02-10
It crashes far too often for me. It chrashed when I tried to log in here, second try that worked. Then I want to youtube, got a question about language, tried to answer it, chrash. Second try, chrash. Then I ignored the question and played a video, worked fine. Then I tried to play a second video, worked fine. Third video, chrash.

Right now it sucks, but I do think it shows a lot of promise, it's nice to use because it is so fast. They really need to work on stability, tough :(

---

### Post by cb951303 on 2009-02-10
there are very good browser projects out there and midori is one of them. 

I think the most important reason why people still sticks with firefox (which is a resource hog) is the addons. For example I want to use epiphany (or midori when its stable) but I can't ditch downthemall or foxyproxy :(

---

### Post by Stemp on 2009-02-10
> **eragon100 said:**
> It crashes far too often for me. It chrashed when I tried to log in here, second try that worked. Then I want to youtube, got a question about language, tried to answer it, chrash. Second try, chrash. Then I ignored the question and played a video, worked fine. Then I tried to play a second video, worked fine. Third video, chrash.

Right now it sucks, but I do think it shows a lot of promise, it's nice to use because it is so fast. They really need to work on stability, tough :(

What version are you using ?
The webkit-team PPA ?
Because as you can see, I can log in UF without problem.

---

### Post by Stemp on 2009-02-10
> **spikey_nick said:**
> Has anybody else had an issue where midori doesn't render six digit hex colors.  It can render named colors, and the three digit hex.

Do you have an example ?

---

### Post by smartboyathome on 2009-02-10
I use the Arch version, but it doesn't work well with EyeOS, and even though I use the latest version of soup, cookies still don't work. Plus, I can't live without gmail notifier in Firefox. ;)

---

### Post by Markuz Nightwind on 2009-02-26
> **Stemp said:**
> What version are you using ?
The webkit-team PPA ?
Because as you can see, I can log in UF without problem.
I'm experiencing random crashes too with midori (using latest version from webkit-team ppa), reopening the page usually fixes the problem. I had also many rendering problems (on various phpbb3 forums) so i guess it's something related more to the webkit svn.

P.S. Btw just noticed new midori version is out, gonna try it soon :)

---

### Post by Stemp on 2009-02-26
> **Markuz Nightwind said:**
> P.S. Btw just noticed new midori version is out, gonna try it soon :)

The new version 0.1.3 is in my personal PPA. As there is a compilation problem with it (it need git-core to compile), I didn't put it in the webkit-team PPA and anyway the dev is going to release a good version in a few days.

---

### Post by Markuz Nightwind on 2009-02-26
Using your repository version since an hour and I can say it seems much smoother than the last 0.1.2 :O Didn't have any crash or rendering problem until now, just to let you know :)

Btw thanks for the fast answer and the packaging work ;)

Edit: Got the first crash right now lol. Well it's still an improvement over the old one that was crashing for me every 5 mins :P

---

### Post by Naiki Muliaina on 2009-02-26
Been using it on and off as my secound browser for  a long time, i love it ^^

---

### Post by DeadRobot on 2009-02-26
It crashes all the time for me.  :(

I'm trying to find an alternative to Firefox because Firefox is being all buggy.

I've settled on Opera. :)

---

### Post by Praxicoide on 2009-03-01
I'm using 0.1.3 from your repository and it works great, but it consistently crashes with Youtube videos, even if they are only embedded on a page. It displays the video OK, but trying to leave the page with the video (by clicking on another video, hitting home or back, or even writing another url) crashes the browser. Stragely, it works OK with Veoh.

Other than that, zero complaints.

---

### Post by Stemp on 2009-03-01
@Praxicoide : In fact it's not midori, it's WebKit fault. That's why I'm not pushing new versions into the webkit-team PPA and keep them into my own PPA.

---

### Post by Mark76 on 2009-03-01
Have any of you seen this?

[https://lists.ubuntu.com/archives/xubuntu-devel/2008-August/006489.html](https://lists.ubuntu.com/archives/xubuntu-devel/2008-August/006489.html)

---

### Post by binbash on 2009-03-01
This crashes all the time, especially at pages which contain flash

---

### Post by ynnhoj on 2009-03-01
> **Mark76 said:**
> Have any of you seen this?

[https://lists.ubuntu.com/archives/xubuntu-devel/2008-August/006489.html](https://lists.ubuntu.com/archives/xubuntu-devel/2008-August/006489.html)
hadn't noticed, but according to the date on the mailing list it's old news :o  interesting, anyhow!

---

### Post by Praxicoide on 2009-03-02
Yeah. I'm using Xubuntu, and that's what drew me to this browser in the first place when looking for a lighter alternative to Firefox (which this old computer can barely handle). I have to say that I love it. It's bound to become my favorite once this problem is sorted out.

Shame about the flash, though. I built WebKit from the nightly and the problem persists. Guess I'll stick to gecko for now...

---

### Post by Orlsend on 2009-03-02
Finally an upgrade for Midori! I really like Midori, but is so unstable. I hope 0.0.19 fixes the problems I had.

---

### Post by adamlau on 2009-03-02
Nice, but Arora feels more polished.

---

### Post by Stemp on 2009-03-18
New version of WebkitGtk+ (1.1.3) and Midori (0.1.4+git) have landed in Webkit-team PPA.

---

### Post by Stemp on 2009-03-29
Midori has now his own PPA :
[https://launchpad.net/~midori/+archive/ppa](https://launchpad.net/~midori/+archive/ppa)

The new 0.1.5 version is there.

Liferea with Webkit Backend has also his own PPA :
[https://launchpad.net/~liferea/+archive/ppa](https://launchpad.net/~liferea/+archive/ppa)

Version 1.5.14

These PPA need the Webkit-team PPA for Webkit and Libraries.

Have fun.

---

### Post by bigbrovar on 2009-03-29
I have tried Midori in the past although i love its speed and simplicity. it was very unstable and crashed must of the time. i wish the stability problem was fixed as it would be the perfect browser for my compaq mini netbook

---

### Post by Stemp on 2009-03-29
@bigbrovar : You should really give it a try now, version 0.1.5 with Webkit 1.1.3 is quite stable, of course it's still at an alpha/beta stage but it's really usable.
That's what i'm using on my Aspire One ;)

---

### Post by bigbrovar on 2009-03-29
> **Stemp said:**
> @bigbrovar : You should really give it a try now, version 0.1.5 with Webkit 1.1.3 is quite stable, of course it's still at an alpha/beta stage but it's really usable.
That's what i'm using on my Aspire One ;)
Great I would give it another try. Thanks

---

### Post by Mr. Picklesworth on 2009-03-29
> **Stemp said:**
> Midori has now his own PPA :
[https://launchpad.net/~midori/+archive/ppa](https://launchpad.net/~midori/+archive/ppa)

The new 0.1.5 version is there.

Liferea with Webkit Backend has also his own PPA :
[https://launchpad.net/~liferea/+archive/ppa](https://launchpad.net/~liferea/+archive/ppa)

Version 1.5.14

These PPA need the Webkit-team PPA for Webkit and Libraries.

Have fun.

Wow, thanks for the link to Liferea's PPA. I didn't realize they were working on that :)

INCREDIBLE improvement from the gecko versions. It's gone from being the heaviest feed reader (yet used grudgingly because it's the most functional) to the lightest and smoothest of the lot!

It even works with notify-osd now. (No actions for notification popups unless there should be).

---

### Post by Stemp on 2009-03-29
> **Mr. Picklesworth said:**
> Wow, thanks for the link to Liferea's PPA. I didn't realize they were working on that :)

INCREDIBLE improvement from the gecko versions. It's gone from being the heaviest feed reader (yet used grudgingly because it's the most functional) to the lightest and smoothest of the lot!

It even works with notify-osd now. (No actions for notification popups unless there should be).

I just uploaded the new 1.5.15 version for Jaunty, could you test it ?

---

### Post by binbash on 2009-03-29
I am gonna do a test drive on jaunty soon.Last time i used midori there have been a lot of flash crashes.I hope they are fixed because i want to replace firefox

---

### Post by binbash on 2009-03-29
Very fast, no crashes at flash sites and some games i have tried BUT there are 2 issues : 

I am using this deb : 

Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main midori 0.1.5-0+git20090328~jjwkt3 [462kB]

And it does not remember the history + it does not cache the swfs (videos games etc) and there is no icon (not menu entry, icon) at midori at gnome

---

### Post by Stemp on 2009-03-29
No history and no icons ? 
You are using both webkit-team and midori PPA ?

I tried it on my Aspire One and it was working just fine. 

I have to say I don't understand what is happening to you.

---

### Post by binbash on 2009-03-29
Yes i do.But i didn't do a reboot yet.I will report after reboot

---

### Post by tr4nce on 2009-03-29
Stemp great job! Thanks for compiling and uploading this new toys for all the "we want something lighter to browse our web related contents".

But, I am having this issue with latest Webkit from PPAs:

Whenever I try to open a url with a webkit back-end browser (epiphany-webkit 2.27.0 or latest Midori) I have a 10 - 15 seconds delay until it starts to load. Is there any possibility that this is a bug of the current webkit build or it's an option that can (or has) to be disabled and I haven't checked yet?

The funny thing is that when the browser end up displaying the url that you requested, the following urls related to it (for example if you do a search in google) works like a charm, with no delays no nothing. The first time that happened I thought that it was "the" ipv6 problem again, but no, firefox seems to work ok and IPV6 got into kernel with the last Jaunty update and I haven't got problems with it.

Strange isn't?

---

### Post by Stemp on 2009-03-30
> **tr4nce said:**
> Whenever I try to open a url with a webkit back-end browser (epiphany-webkit 2.27.0 or latest Midori) I have a 10 - 15 seconds delay until it starts to load. Is there any possibility that this is a bug of the current webkit build or it's an option that can (or has) to be disabled and I haven't checked yet?

The funny thing is that when the browser end up displaying the url that you requested, the following urls related to it (for example if you do a search in google) works like a charm, with no delays no nothing. The first time that happened I thought that it was "the" ipv6 problem again, but no, firefox seems to work ok and IPV6 got into kernel with the last Jaunty update and I haven't got problems with it.

Strange isn't?

DO you mean the last 1.3.3-3 from the PPA or just in all the 1.3.3 build ?
Because the last modifications in the PPA are about dropping the dbg files (they were very big and the PPA was sometime full).

I'm using midori on a Aspire One with Jaunty and it fly, so I'm really surprised (but I'm not using IPV6).

> **tr4nce said:**
> Stemp great job! Thanks for compiling and uploading this new toys for all the "we want something lighter to browse our web related contents".

And don't forget the real WebKit packagers from Debian, Mike Hommey and Gustavo Noronha Silva. They did an impressive job.

---

### Post by rizzeh on 2009-03-30
i found Midori to be very fast, but too much hard work. i'm keeping eye on its development though, hopefully bugs will get fixed without slowing it down :)

---

### Post by Exershio on 2009-03-30
I can't wait until Midori is a bit more stable. It is definitely the fastest graphical browser I've used and it uses webkit and gtk, which is perfect for my minimal desktop.

However, it crashes a lot on large websites for me, so I'll stick to firefox until it becomes more mature.

I'm keeping an eye on its progress ;)

---

### Post by pjalegria on 2009-03-30
I cant install Midori PPA version, dependacy error

---

### Post by Stemp on 2009-03-30
> **pjalegria said:**
> I cant install Midori PPA version, dependacy error

You need to add the [Webkit-team PPA]("https://launchpad.net/~webkit-team/+archive/ppa")

For Intrepid, add this line to your sources.list :
```
deb http://ppa.launchpad.net/webkit-team/ppa/ubuntu intrepid main
```

---

### Post by pjalegria on 2009-03-30
Im have Jaunty...

Midori 0.1.2.1 with Webkit-team PPA, thats not the lasted version

---

### Post by Stemp on 2009-03-30
> **pjalegria said:**
> Im have Jaunty...

Midori 0.1.2.1 with Webkit-team PPA, thats not the lasted version

You need both PPA.

Webkit-team PPA for WebkitGtk and midori PPA for midori.

On Jaunty you will have Webkit 1.1.3 and Midori 0.1.5 + git from today ;)

---

### Post by bigbrovar on 2009-03-30
> **Mr. Picklesworth said:**
> Wow, thanks for the link to Liferea's PPA. I didn't realize they were working on that :)

INCREDIBLE improvement from the gecko versions. It's gone from being the heaviest feed reader (yet used grudgingly because it's the most functional) to the lightest and smoothest of the lot!

It even works with notify-osd now. (No actions for notification popups unless there should be).
 i might be installing it on my compaq mini with the mie interface .. does any one knows if this ppa has packages for lpia

---

### Post by Stemp on 2009-03-30
> **bigbrovar said:**
> i might be installing it on my compaq mini with the mie interface .. does any one knows if this ppa has packages for lpia

Yes, both Webkit and Liferea PPA have LPIA versions.

---

### Post by pjalegria on 2009-03-30
Thanks, now its working... what about Midori icon? i dont have it...

---

### Post by Stemp on 2009-03-30
> **pjalegria said:**
> Thanks, now its working... what about Midori icon? i dont have it...

midori package recommend gnome-icon-theme, do you have it ? 

If it's not the problem, maybe I made a mistake in the package.
You'll probably have to launch this command :
```
sudo gtk-update-icon-cache -q -f -t /usr/share/icons/hicolor
```

---

### Post by lvlo on 2009-03-30
Hi there.

Is there way to change speed of scrolling? To do this in Firefox I'm using "mousewheel.horizscroll.withnokey.numlines" key in about:config.... is there something like that in Midori?

Anyway Midori 0.1.5 looks very good for me :)

---

### Post by Stemp on 2009-03-30
> **lvlo said:**
> Is there way to change speed of scrolling? .... is there something like that in Midori?

I don't think so.
There is a zoom step in ~/.config/midori/config but nothing about scroll wheel.

---

### Post by Stemp on 2009-03-31
Webkit 1.1.4 is out, you can check the HTML5 media capabilities on :
[http://www.double.co.nz/video_test/](http://www.double.co.nz/video_test/)

---

### Post by ghindo on 2009-03-31
Thanks for keeping us up-to-date, Stemp - I appreciate it! :)

Edit:  I just realize that I have the Webkit team PPA enabled, but I think I'm still on WebKit 1.0.  How do I check what version of WebKit I have installed?

---

### Post by Stemp on 2009-03-31
> **ghindo said:**
> Thanks for keeping us up-to-date, Stemp - I appreciate it! :)

Edit:  I just realize that I have the Webkit team PPA enabled, but I think I'm still on WebKit 1.0.  How do I check what version of WebKit I have installed?

install package libwebkit-1.0-2 ;)

---

### Post by ghindo on 2009-03-31
Got it, thank you! :)

---

### Post by Praxicoide on 2009-04-03
Hi again,

So I wanted to try this again, since apparently the flash problem has been fixed. I removed and purged the midori and webkit I had, since they were builds, included this new PPA (I already had the webkit one), and installed them again.They installed fine (Midori 0.1.5-0 and libwebkit 1.0-2). Unfortunately I can't start Midori because it complains about needing libwebkit 1.0.so.1, which isn't there anymore. I tried purging it again and reinstalling to no avail. Is there a way to fix this?

EDIT: I fixed it, it seems there was another Midori executable under /usr/local/bin, which I had to delete). The flash problem is indeed solved. I'll be using Midori from now on, since my machine is pretty old. Thank you very much! I'll let you know how it goes.

EDIT2: OK, after a day of use I can safely say that it is pretty stable and it doesn't run, it flies. Good job and congratulations, in a short while the browser went from being usuable basically for testing purposes to being a viable and strong option for default browsing.

EDIT3: Yet another day of use and no problems whatsoever. I wanted to congratulate the developers for the wonderful download dialog. The Download Statusbar is actually one of the first things I get for Firefox whenever I install it. There needs to be a way to delete the stuff from the bar without actually opening it, though.

---

### Post by lvlo on 2009-04-18
I added feature request for "scrolling speed" option in Midori. If you need it too, please confirm...

[http://www.twotoasts.de/bugs/index.php?do=details&task_id=347](http://www.twotoasts.de/bugs/index.php?do=details&task_id=347)

---

### Post by sertse on 2009-04-26
Bumping this thread because I just discovered midori and I love it. I don't really notice the speed (FF is quick enough for me I suppose..), but it feels snappier. Most importantly it has full functionality - plugins, flash etc all work. 

Could use with an autoscroll option, perfect for the laptop and touchpad scrolling, not so much for the desktop and mousewheel.

---

### Post by Praxicoide on 2009-04-27
The Midori in the Jaunty repos is 0.12, which crashes all the time. In order to enjoy the very stable 0.16 under jaunty you have to add the webkit and midori ppas in the sources list.

Add the following to your /etc/apt/sources.list:

```

# WebKit
deb http://ppa.launchpad.net/webkit-team/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/webkit-team/ppa/ubuntu jaunty main

#Midori
deb http://ppa.launchpad.net/midori/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/midori/ppa/ubuntu jaunty main
```

Then type the following commands into a terminal:

```

gpg --keyserver keyserver.ubuntu.com --recv 2D9A3C5B && gpg --export -a 2D9A3C5B | sudo apt-key add -
gpg --keyserver keyserver.ubuntu.com --recv A69241F1 && gpg --export -a A69241F1 | sudo apt-key add -
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --reinstall midori
```

And you're done.

---

### Post by VCoolio on 2009-04-27
Thanks, I was looking for adding repos for a newer midori on Jaunty. But the sudo apt-get dist-upgrade is a really bad idea don't you think? When Karmic gets alpha-released your system would switch to that, wouldn't it? Correct me if I'm wrong, otherwise delete that line from your post.

---

### Post by Praxicoide on 2009-04-27
It wouldn't unless you change your repos. What could happen, though, is that other packages being held back could be installed. I'll change that line.

---

### Post by chucky chuckaluck on 2009-04-27
does it make any sense that midori would run faster without hal running?

---

### Post by Sef on 2009-05-22
Praxicoide > Thanks for the PPAs and how to update.   I would be intersted in seeing if this version is more stable as has been indicated.

Also I have a question:

> EDIT: I fixed it, it seems there was another Midori executable under /usr/local/bin, which I had to delete). The flash problem is indeed solved. I'll be using Midori from now on, since my machine is pretty old. Thank you very much! I'll let you know how it goes.

How exactly did you fix the problem?  Could you please explain step by step.  thank you.

---

### Post by Stemp on 2009-05-23
> **Sef said:**
> How exactly did you fix the problem?  Could you please explain step by step.  thank you.

With midori from the PPA there should be no problems with netscape plugins like flash (but java is not working).

So I guess you'll have to remove all prior versions and purge them.
Purge also the current version and remove ~/.config/midori/

Then reinstall the new version from PPA (also with webkit-team PPA libwebkit-1.0-2)

If flash is working with firefox it should work with midori.

---

### Post by Mark76 on 2009-05-28
Most browsers enable you to skip back or forth more than one page at a time. But I can't find this option in Midori.

Will it be included soon?

---

### Post by ghindo on 2009-05-28
By the way, there's a new Midori release out today:

[http://www.twotoasts.de/index.php?/archives/18-Activation,-detaching-and-feed-panel.html](http://www.twotoasts.de/index.php?/archives/18-Activation,-detaching-and-feed-panel.html)

---

### Post by Stemp on 2009-05-28
> **ghindo said:**
> By the way, there's a new Midori release out today:

And already in the Midori PPA :popcorn:

> **Mark76 said:**
> Most browsers enable you to skip back or forth more than one page at a time. But I can't find this option in Midori.

Will it be included soon?

You should fill a Bug/Whishlist in [Midori bugtracker]("http://www.twotoasts.de/bugs/") ;)

---

### Post by Mark76 on 2009-05-29
I seem to be having problems getting Sylpheed to open links in new tabs in Midori instead of a new window.

---

### Post by Stemp on 2009-05-29
> **Mark76 said:**
> I seem to be having problems getting Sylpheed to open links in new tabs in Midori instead of a new window.

From the Changelog of version 0.1.7 :
 + Implement Open new pages in: New window preference

Waybe this is the reason ? Before, this option was useless.

---

### Post by Mark76 on 2009-05-29
Why does Midori keep rendering the fonts in BBC web pages like this?

And why can't I open the goddamned preferences?

---

### Post by ghindo on 2009-05-29
> **Mark76 said:**
> Why does Midori keep rendering the fonts in BBC web pages like this?Looks fine to me.

---

### Post by Mark76 on 2009-05-29
I managed to (finally) open Preferences and the fonts are as default.

So wtf is going on?

---

### Post by sertse on 2009-05-29
> **Mark76 said:**
> Why does Midori keep rendering the fonts in BBC web pages like this?

And why can't I open the goddamned preferences?

I've seen it before, with all browsers. Sure it isn't a X thing?

Midori has been all fine for me so far, no issues.

---

### Post by ghindo on 2009-05-29
> **Mark76 said:**
> I managed to (finally) open Preferences and the fonts are as default.

So wtf is going on?I dunno.  Maybe it's your system fonts?

---

### Post by Mark76 on 2009-05-29
My system font doesn't look like that. And does Midori actually use them by default?  Most browsers use their own fonts unless you specifically tell them to use system fonts

---

### Post by Mark76 on 2009-05-29
Just to make sure I changed the system font.

And fonts in some pages are still rendering horribly

---

### Post by ghindo on 2009-05-29
> **Mark76 said:**
> My system font doesn't look like that. And does Midori actually use them by default?  Most browsers use their own fonts unless you specifically tell them to use system fontsI'm not sure.  From what I can tell, Midori is using my system fonts for that particular page.

---

### Post by Mark76 on 2009-05-29
> **sertse said:**
> I've seen it before, with all browsers. Sure it isn't a X thing?

Midori has been all fine for me so far, no issues.

If it is an X thing then I have no idea how to change it other than deleting Midori and using another browser.

---

### Post by gradinaruvasile on 2009-08-12
Same here

---

### Post by Jesus_Valdez on 2009-08-12
I can't update Midori: W: Falló al obtener [http://ppa.launchpad.net/midori/ppa/ubuntu/pool/main/m/midori/midori_0.1.9-1+git20090808~jjwkt1_amd64.deb](http://ppa.launchpad.net/midori/ppa/ubuntu/pool/main/m/midori/midori_0.1.9-1+git20090808~jjwkt1_amd64.deb)
  No pude resolver 'ppa.launchpad.net'

something like can't find ppa.launchpad.net and unable to get the .deb file.

I was wondering if someone else is having the same problem.

---

### Post by Jimleko211 on 2009-08-12
> **Jesus_Valdez said:**
> I can't update Midori: W: Falló al obtener [http://ppa.launchpad.net/midori/ppa/ubuntu/pool/main/m/midori/midori_0.1.9-1+git20090808~jjwkt1_amd64.deb]("http://ppa.launchpad.net/midori/ppa/ubuntu/pool/main/m/midori/midori_0.1.9-1+git20090808%7Ejjwkt1_amd64.deb")
  No pude resolver 'ppa.launchpad.net'

something like can't find ppa.launchpad.net and unable to get the .deb file.

I was wondering if someone else is having the same problem.
Launchpad may be down, I got the same problem trying to grab Chromium.

---

### Post by RJARRRPCGP on 2009-08-13
For me, Midori keeps having a segmentation fault, when at weather.com, IIRC. :evil:

---

### Post by MasterNetra on 2009-08-13
> **Sef said:**
> Has anyone else used Midori Web Browser?  It's a small lightweight browser and very fast.  It is alpha, so still lots to do.  With the update to 0.17, it is much more stable now than before.  If you want to try it out, it is available in the universe repository.

I've tried it, but for me when its too simple with no support for Flash and other such things. I'll wait until its out of alpha...or even better out of beta, before I'll try it again. Perhaps it will be a good browser later on, but for now, I'm not using it.

---

### Post by Jesus_Valdez on 2009-08-13
What do you mean with "no support for flash", I can surf flash based pages and sites like youtube with no problema.

---

### Post by RaZe42 on 2009-08-13
Umm... you must be using some old version of Midori, because the one I tried did support Flash without any problems...

EDIT: Jesus_Valdez beat me to it :P

---

### Post by sagara on 2010-05-05
is it just me or midori doesnt support autocomplete for URLs?

as in google + ctrl + enter = google.com

i'm currently using version 0.2.4

---

### Post by RJARRRPCGP on 2010-05-07
Update: Midori appears to be fine now. Recently, I can navigate the weather.com interface without Midori crashing.

---

### Post by northwestuntu on 2010-05-07
it's nice, but i like to have more options and extensions.

---

### Post by The Real Dave on 2010-05-07
I like Midori. For me, it has problems rendering some webpages correctly. It is however, quite light and quick, and I'll look forward to replacing Firefox on a certain rig with it. 

Nice work :)

---

### Post by themarker0 on 2010-05-07
I like midori, except... NO JAVA! I mean come'on! Thats all i need. Java!

---

### Post by Stemp on 2010-05-08
> **themarker0 said:**
> I like midori, except... NO JAVA! I mean come'on! Thats all i need. Java!

[http://stemp.wordpress.com/2010/02/24/webkitgtk-etand-java/](http://stemp.wordpress.com/2010/02/24/webkitgtk-etand-java/) ;)

---

### Post by CrimsonBizarre on 2010-05-08
I think it's great, especially as it intregrates perfectly with GTK (I'm using Global Menu Bar and the lack of support from every other browser was annoying me).

It's fast, and it does most things I need to do.

Only things keeping it from being my primary browser:

Need '+tab' button in the tab bar.
Needs scaleable search bar.
Need 'smart' address bar
When opening link in new tab, it must not switch to it immediately
When opening link in new tab, it must make it the last tab, not one to the right
When re-opening deleted tabs, they should open in their original place, not as the last tab
Need option to pick and choose what panels you want,
SPELL CHECK!
Needs to be even faster
Fix bugs.

Maybe I'm just too used to Opera

EDIT: I love the feature where: if you scroll with the scroll wheel in the tab bar, it changes tabs, I don't think I've seen a browser with this in before.

---

### Post by sertse on 2010-05-08
> **CrimsonBizarre said:**
> 
Need 'smart' address bar
When opening link in new tab, it must not switch to it immediately
When opening link in new tab, it must make it the last tab, not one to the right
Need option to pick and choose what panels you want,
SPELL CHECK!
EDIT: I love the feature where: if you scroll with the scroll wheel in the tab bar, it changes tabs, I don't think I've seen a browser with this in before.

Smart address bar: I don't know what you mean, but it has improved a bit these days ala firefox "awesome bar" style..
Must not switch to it immediately: Preferences -> Interface -> Check Open tabs in background
Make it open in last tab: Preferences -> Interface -> Uncheck Open tabs next to current
Pick and choose what panels you want: Right check the main panel: You can check/uncheck certain panels. To customise what buttons etc are on the navigation bar. Enable the toolbar editor extension. 
Spellcheck: Webkit problem, not Midori. It is fixed if you are using the latest versions of Webkit. If so, Preferences -> Behaviour ->Enable Spell Checking -> Type your language code
Scroll wheel changes tab: It works here.


I've been a heavy advocate of Midori since the days when it was reallly beta. It's come a long way. I actually use it as my main now, firefox installed mainly as a backup..

---

### Post by CrimsonBizarre on 2010-05-09
> **sertse said:**
> Smart address bar: I don't know what you mean, but it has improved a bit these days ala firefox "awesome bar" style..
Must not switch to it immediately: Preferences -> Interface -> Check Open tabs in background
Make it open in last tab: Preferences -> Interface -> Uncheck Open tabs next to current
Pick and choose what panels you want: Right check the main panel: You can check/uncheck certain panels. To customise what buttons etc are on the navigation bar. Enable the toolbar editor extension. 
Spellcheck: Webkit problem, not Midori. It is fixed if you are using the latest versions of Webkit. If so, Preferences -> Behaviour ->Enable Spell Checking -> Type your language code
Scroll wheel changes tab: It works here.


I've been a heavy advocate of Midori since the days when it was reallly beta. It's come a long way. I actually use it as my main now, firefox installed mainly as a backup..

Thanks! All worked apart from the panels thing. Toolbars are not the same as panels. The panels that are there are:

Bookmarks
History
Transfers
Console
Userscript
Netscape plugins
Extenstions

I want it to be cut down to just Bookmarks, History, and Transfers.

And what would be the language code for English (UK)?
EDIT: I found the language code, it is en-GB, but I still can't find how to disable certain panels.

---

### Post by chillicampari on 2010-05-09
> **CrimsonBizarre said:**
> ...

I want it to be cut down to just Bookmarks, History, and Transfers.

...

That's actually one of my favorite things (having all that in the panel). It's really easy to toggle user scripts, custom styles and extensions on and off the way it's laid out. 

I was missing the new tab button on the tab grid also but with the toolbar editor placed a new tab and close tab buttons in between the url and search bars. It feels pretty natural to me there.

---

### Post by Yes on 2010-05-09
Is there a way to enable smooth scrolling (or whatever it's called when you click the middle mouse button and scroll)?

---

### Post by themarker0 on 2010-05-09
> **Stemp said:**
> [http://stemp.wordpress.com/2010/02/24/webkitgtk-etand-java/](http://stemp.wordpress.com/2010/02/24/webkitgtk-etand-java/) ;)

How do i get that though? I installed Java, doesn't show up for me though...

---

### Post by chillicampari on 2010-05-09
> **Yes said:**
> Is there a way to enable smooth scrolling (or whatever it's called when you click the middle mouse button and scroll)?

I *think* something like that's supposed to be in the mouse gestures extension but I couldn't get it working when I just tried so might be wrong on that. But I'm using a trackball with 3-button emulation.

---

### Post by Stemp on 2010-05-10
> **themarker0 said:**
> How do i get that though? I installed Java, doesn't show up for me though...

You need webkit >= 1.1.22 and Sun Java (not OpenJDK)

---

### Post by Khakilang on 2010-05-10
I just add a friend in Facebook and her name is Midori Hayashi. Are they related?

---

### Post by CrimsonBizarre on 2010-05-10
> **chillicampari said:**
> That's actually one of my favorite things (having all that in the panel). It's really easy to toggle user scripts, custom styles and extensions on and off the way it's laid out. 

I was missing the new tab button on the tab grid also but with the toolbar editor placed a new tab and close tab buttons in between the url and search bars. It feels pretty natural to me there.
I've just come from Opera, where there were: bookmarks, history, downloads, unite, etc. in the panels, a lot of those I do not use, so I like to disable them so that they're just not there, I'd like to just disable a few in Midori as well.

---

### Post by themarker0 on 2010-05-10
> **Stemp said:**
> You need webkit >= 1.1.22 and Sun Java (not OpenJDK)

Thank you, i'll try when i get home tonight. :)

---

### Post by chillicampari on 2010-05-10
> **CrimsonBizarre said:**
> I've just come from Opera, where there were: bookmarks, history, downloads, unite, etc. in the panels, a lot of those I do not use, so I like to disable them so that they're just not there, I'd like to just disable a few in Midori as well.

Ahh.. I think I misunderstood. Yeah, that would be kind of cool to hide stuff you don't use. I poked around in the local config files in .config/midori but I didn't see a place to edit it (I did see the toolbar options so maybe it's in there somewhere and just not jumping out at me).

---

### Post by tibike on 2010-05-13
I have some sort of a bug using midori on lucid lynx. Whenever I google search I get a strange picture on the top left of my results. Like in this image. [IMG]http://dl.dropbox.com/u/257128/Screenshot-%E2%80%AAwhatever%20-%20Google%20Search%20-%20Midori.png[/IMG] 

Also aonther thingy. Middle mouse button press should do autoscroll (optionaly) not google search for the selected text, mainly because it disables the system wide "insert selected text" feature.

---

### Post by chillicampari on 2010-05-13
tibike, just for grins on the display error with Google results could you try: 
Preferences -> Network 
and change your browser identification to something else (not iPhone though) to see if it looks different?

---

### Post by tibike on 2010-05-14
thanks chillicampari, that helped!

---

### Post by CrimsonBizarre on 2010-05-20
> **chillicampari said:**
> tibike, just for grins on the display error with Google results could you try: 
Preferences -> Network 
and change your browser identification to something else (not iPhone though) to see if it looks different?
Thank you.

---

### Post by chillicampari on 2010-05-21
> **tibike said:**
> thanks chillicampari, that helped!

> **CrimsonBizarre said:**
> Thank you.

Cool, glad that helped! I was browsing the tasklist at [http://www.twotoasts.de/bugs/](http://www.twotoasts.de/bugs/) and that seems to be the solution right now for a few different things, but if the rendering issue carries to the next version (I think Google results changed *after* the current version, not positive on that though) it may be worthwhile for us to file a bug report to twotoasts on it, since this is just a temp workaround.

---

### Post by CrimsonBizarre on 2010-05-22
> **chillicampari said:**
> Ahh.. I think I misunderstood. Yeah, that would be kind of cool to hide stuff you don't use. I poked around in the local config files in .config/midori but I didn't see a place to edit it (I did see the toolbar options so maybe it's in there somewhere and just not jumping out at me).

That doesn't matter now. I just upgraded to 0.2.5 and they're at the bottom of the panel list and out of the way.

I've seen users on here with custom speed dials (changing the number of shortcuts you can have), how do you do this?

---

### Post by chillicampari on 2010-05-22
> **CrimsonBizarre said:**
> That doesn't matter now. I just upgraded to 0.2.5 and they're at the bottom of the panel list and out of the way.

I've seen users on here with custom speed dials (changing the number of shortcuts you can have), how do you do this?

Neat, new version. I'll have to check that out!

I can't guarantee it'll be exactly the same since we're on different versions now, but 
/usr/share/midori/res/ should have what you're looking for to mess around with. I'd probably back up the whole directory first.

---

### Post by sertse on 2010-05-22
> **CrimsonBizarre said:**
> 
I've seen users on here with custom speed dials (changing the number of shortcuts you can have), how do you do this?

It's available in the development version. You'll get it the next time the PPA updates...

---

### Post by CrimsonBizarre on 2010-05-23
> **sertse said:**
> It's available in the development version. You'll get it the next time the PPA updates...

Oh, good.
For it to replace Opera as my main browser, all that's left is:
Extendable search bar.
New tab button in tab bar.
Deleted tab button in tab bar
More stability.
Improved appearance (custom speed dial, less tall tabs (I know this depends on the GTK theme, but somehow Epiphany has smaller tabs with the same themes), etc.)
and tabs that 'squash' when there are to many

---

### Post by screaminj3sus on 2010-05-23
I have tried to like midori but its far too lacking and way too buggy, my biggest issue is bookamrks.

No real bookmark management; even worse than chrome's [lack of] bookmark management. Import bookmarks doesnt work. period. It ONLY supports xbel which NO browsers use. I have used multiple methods to covert firefox's bookmarks to xbel but midori still wont import them (version in ubuntu repos says "malformed document", version from ppa just crashes)

Thumbs down for me, a lot of work before it becomes usable. I also get rendering issues in a lot of sites.

For me chrome is the best browser in linux (and I don't even like chrome that much, I definitely prefer opera 10.5 and firefox in windows but they both suck in linux IMO. Opera is incredibly ugly in gnome, and firefox is a slow pig compared to the windows version. It starts up at least twice as fast in windows for me and in gnome it takes up half the damn screen unless you hide the menubar and the bookmark toolbar)

---

### Post by TortureQueen on 2010-07-28
I am interested in using Midori for everyday use.  (I would like to begin using FireFox for more sensitive things).  This is the first time I have heard of Midori.  How do you guys like it?

---

### Post by ubuntu27 on 2010-07-28
**EDIT**: Oops! Sorry for double post. Ignore this one. [It was an accident]

---

### Post by ubuntu27 on 2010-07-28
One aspect that I like about Midori is that I perceive it to be fast.

The down side for me is that when zooming the page, only the text (and not the images) zooms.

And I don't particularly care about bookmark management for the moment. I use that in Firefox.

---

### Post by sertse on 2010-07-28
> **ubuntu27 said:**
> 

The down side for me is that when zooming the page, only the text (and not the images) zooms.




Preferences -> Behaviour -> Zoom text and images

---

### Post by ubuntu27 on 2010-07-28
> **sertse said:**
> Preferences -> Behaviour -> Zoom text and images

Oh! Thank you Sertse. I never visited Midori's preference.

Now I can zoom the images alongside the text.
Why is it not the default settings?

Well, now I will try to use Midri as default for a little while, and see how it works.

---

### Post by keithrennie on 2010-07-31
> **Sef said:**
> Has anyone else used Midori Web Browser?  It's a small lightweight browser and very fast.  It is alpha, so still lots to do.  With the update to 0.17, it is much more stable now than before.  If you want to try it out, it is available in the universe repository.

Its now July 2010, and Midori has moved on a long way. I'm now on 0.2.2, running on Lucid Xubuntu, on an old Pentium III desktop that needs all the performance optimization it can get. I just found Midori by accident the other day, played with it out of curiosity and fell in love with it at first sight. It's now blazingly fast, clean and well designed and lots of nice little features like speed dial and search engine dialogue. I still keep Firefox and Epiphany enabled just in case, but Midori is definitely now my browser of choice and you can use Netscape plugins. 

One nice little tip in case anybody has the same problem. I also use Gmail, but Gmail doesnt recognize Midori, so it loads the basic html version that it uses for unrecognized browsers, and that is a very buggy experience (like it disables typing in some fields). You can get round this by telling Midori (in Edit/Preferences) to identify itself as Firefox and making sure that cookies and scripts are enabled. Gmail then obediently loads the full kit and caboodle. 

Best little browser in town, in my view.
:D:D:D

---

### Post by genjix on 2011-01-04
ZOMG!!! I've been using this browser for a week now and it is THE BEST. super fast, hasn't got all that junk like all the other browsers.

Just perfect. Set all the usual preferences I have (no menubar, open tabs without swithing focus to them...). If you type something in the address bar then you get the option to search google or wikipedia!! much more intuitive than chrome (in midori you just press down and enter when it pops up).

Anyone know how to configure the toolbar? I want to remove the new tab button on the left, and the show sidepanel, google search and trashbin on the right.

:lolflag: :guitar:

---

### Post by genjix on 2011-01-04
Really, WebKit is a great thing... Expect to see an explosion in features because the hard part of creating a browser (the html renderer) is done. Lots of browsers catering to everyone's different needs! that's the free software way :)

---

### Post by Rachel_Eliason on 2011-01-04
I have had midori sitting on my computer for awhile now. I like to have a second, or even third browser in case one goes buggy and I have to debug it. (I learned this the hard way, when firefox decided to open more than fifty help tabs every time I started it :p) I hadn't really used Midori until I saw this thread. It runs fast for me, with no bugs to speak off. I don't know that I will ditch firefox, but I might play with Midori some more.

---

### Post by Stemp on 2011-01-04
> **genjix said:**
> Anyone know how to configure the toolbar? I want to remove the new tab button on the left, and the show sidepanel, google search and trashbin on the right.

Menu Tools, Customize Toolbar ?

---

### Post by genjix on 2011-01-04
Nice ^^ that worked great (and I decided to keep the trashbin after realising that it's previously closed tabs)

great browser- 9/10... best one ever I think.

---

### Post by genjix on 2011-01-04
Nice ^^ that worked great (and I decided to keep the trashbin after realising that it's previously closed tabs)

great browser- 9/10... best one ever I think.

---

### Post by CrimsonBizarre on 2011-01-16
> Extendable search bar.
New tab button in tab bar.
Deleted tab button in tab bar
More stability.
[s]Improved appearance (custom speed dial, less tall tabs (I know this depends on the GTK theme, but somehow Epiphany has smaller tabs with the same themes), etc.)[/s]
and tabs that 'squash' when there are to many

My list of things I wanted to see, from May last year. They've managed to do one of the things since then. I'm still using 2.7 though, so there might be more.

A customisable tab bar would be great. I'd really like a "+" button next to the tabs like every other browser, and I'd prefer the "recently deleted tabs" button to be in the tab bar.

I quit using the search bar, so that's not really a problem. I'd prefer a lot more stability though - this is what I'd want done first.

EDIT: Just upgraded to the latest one. Seems they've fixed a lot of crashing problems.

---

### Post by Arleas on 2011-01-16
> **Jengajam2 said:**
> Its also the name of a manga: "Midori Days". Anyway, I tried it, and all I say is that it runs about the same as firefox, but is alot better than opera.

Doesn't it mean 'left' in japanese? Or is that 'migi'?

---

### Post by Spice Weasel on 2011-01-16
> **Arleas said:**
> Doesn't it mean 'left' in japanese? Or is that 'migi'?

Midori is green in Japanese.

---

### Post by stozi on 2011-03-18
Can anyone tell me how to get 'search as you type' in the latest release?

---

### Post by Lucradia on 2011-03-18
> **stozi said:**
> Can anyone tell me how to get 'search as you type' in the latest release?

If they added that, I hope they added an option to remove it in settings. I've always hated that chrome doesn't allow us to turn that off; hence I dislike chrome.

---

### Post by stozi on 2011-03-18
They have had it, I had it working, but fresh installed midori at latest version, and can't see how to make it work anymore. Should have backed up config file. durrr

---

### Post by MasterNetra on 2011-04-06
Anyone know how to access facebook normally with midori, i get a blasted text thing as though facebook believes midori is running on a phone or something...

---

### Post by Stemp on 2011-04-06
Facebook doesn't understand midori identity :(

You need to change it in Menu Edit, Preferences, Network, Identity to something like this :
Mozilla/5.0 (X11; U; Linux x86_64; fr-fr) AppleWebKit/531.2+ (KHTML, like Gecko) Version/5.0 Safari/531.2+

And then it will be fine ;)

---

### Post by MasterNetra on 2011-04-06
> **Stemp said:**
> Facebook doesn't understand midori identity :(

You need to change it in Menu Edit, Preferences, Network, Identity to something like this :
Mozilla/5.0 (X11; U; Linux x86_64; fr-fr) AppleWebKit/531.2+ (KHTML, like Gecko) Version/5.0 Safari/531.2+

And then it will be fine ;)

kk thanks

---

### Post by Lucradia on 2011-04-07
> **Stemp said:**
> Facebook doesn't understand midori identity :(

You need to change it in Menu Edit, Preferences, Network, Identity to something like this :
Mozilla/5.0 (X11; U; Linux x86_64; fr-fr) AppleWebKit/531.2+ (KHTML, like Gecko) Version/5.0 Safari/531.2+

And then it will be fine ;)

You have to change it back to midori for other (rare few) sites though, sadly.

---

### Post by kerryhall on 2011-09-20
> **CrimsonBizarre said:**
> Thanks! All worked apart from the panels thing. Toolbars are not the same as panels. The panels that are there are:

Bookmarks
History
Transfers
Console
Userscript
Netscape plugins
Extenstions

I want it to be cut down to just Bookmarks, History, and Transfers.

And what would be the language code for English (UK)?
EDIT: I found the language code, it is en-GB, but I still can't find how to disable certain panels.

Where is the list of language codes? Thanks!

---

### Post by CrimsonBizarre on 2011-11-02
> **kerryhall said:**
> Where is the list of language codes? Thanks!

There is a list available here: [http://msdn.microsoft.com/en-us/library/ms533052(v=vs.85).aspx](http://msdn.microsoft.com/en-us/library/ms533052(v=vs.85).aspx)

> **CrimsonBizarre said:**
> 
Extendable search bar.
New tab button in tab bar.
[s]Easily accessible list of recently deleted tabs[/s]
[s]More stability.
Improved appearance (custom speed dial, less tall tabs (I know this depends on the GTK theme, but somehow Epiphany has smaller tabs with the same themes), etc.)
and tabs that 'squash' when there are to many[/s]
4 things done from my list of things I would like to see that I posted in May 2010. Obviously more stability and support is obviously good but it's come a long way since May 2010. Although I've started using the middle mouse button for tab opening/closing now, I still think it would be great to have a new tab button in the tab bar like every other browser. I would also prefer there to be a list of recently deleted tabs available in a menu somewhere if I don't have the button added.

---

