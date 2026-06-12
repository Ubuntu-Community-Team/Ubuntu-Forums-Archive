---
title: "Chromium (Google Chrome dev) 3.0.197.0 (0) has serious upgrades!"
date: 2009-08-02
forum: The Cafe
---

### Post by wersdaluv on 2009-08-02
Chromium is currently on 3.0.197.0 (0) version while Google Chrome (for Linux) is ver 3.0.196.0. 

I just upgraded to the latest version and noticed that it has big upgrades. The most noticeable one is the correct window border. On GNOME, it used to have a metacity border. I don't know what the border is called now but it looks like the one on the Windows version without compositing. Another big upgrade is font rendering. Fonts look much nicer now, though they're not perfect in some cases yet but they're manageable enough.

I'm looking forward to a better gtk feel and a more Linux desktop-oriented window border. I just don't know how they're going to put the standard metacity or kwin on this thing. Other than those, the only bugs I noticed so far are the lack of scroll arrows (is that what they call "stepper"?) and the status on the bottom right does not automatically hide on mouse hover.

This could be my default browser on Ubuntu :D

---

### Post by jonathanysp on 2009-08-02
oh cool! i just noticed that as well, pretty nice. but i dont really get why google doesnt want the normal borders. It makes it look out of place, even in windows...and doesnt this make it harder to render on the screen? Anyways its getting better and better each release.

i hardly use the stepper things now since theres the scroll wheel and you can still move the scrollbar with middle clicks which is much faster. The only thing left is stable a stable flash plugin!

---

### Post by dragos240 on 2009-08-02
I'm checking out the latest svn build right now.

---

### Post by eldragon on 2009-08-02
> **jonathanysp said:**
> oh cool! i just noticed that as well, pretty nice. but i dont really get why google doesnt want the normal borders. 

thats easy, they want to asociate what goes on in the browser as your application framework, so they developed a GUI that resembles an operating system, they want people to get used to work within chrome, so that the transition to the google ecosystem isnt too steep in the future.

---

### Post by .Maleficus. on 2009-08-02
> **dragos240 said:**
> I'm checking out the latest svn build right now.
Are you using the chromium-browser package from AUR?  I see on 64-bit it's still downloading the i386 PPA.  Is that right?

Anyways, checking out the latest SVN now as well.  I've been using Chrome on Windows 7 for a while now and I love it.


Edit:  I'm getting the same error as [flammenwurfer]("http://bbs.archlinux.org/viewtopic.php?id=77135") here.  Guess it's time to try the 64-bit PPA and see what happens.

---

### Post by heyyy on 2009-08-02
can someone point me to the lauchpad page with browser package in order to install and the add the launchpad repos?

---

### Post by no1wantdthisname on 2009-08-02
> **heyyy said:**
> can someone point me to the lauchpad page with browser package in order to install and the add the launchpad repos?

[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

And window decorations can be set be right clicking the area right of the tab bar.

---

### Post by darco on 2009-08-02
Fantastic...I am running Mint x64 and was having issues w/the x32 flashplayer recently. This new upgrade fixes that....

chromium-browser-3.0.197.0~svn20090801r22243

darco

---

### Post by ubulette on 2009-08-02
I've just updated the package to remove its HTML5 codecs. The debacle between Apple, Google and Mozilla made me create two separate codec packages:

- chromium-codecs-ffmpeg with ogg, vorbis and theora
- chromium-codecs-ffmpeg-nonfree with the 3 above + H.264, MP3 and AAC

(the reason non-free includes the free codecs is that ffmpeg ships that within the same files).

The two packages conflict with each other. The free one will be installed by default (you have to dist/safe-upgrade).

Note: you need to wait for todays build for this to happen (>= 3.0.197.0~svn20090802r22252), don't update manually, it won't work.

(this will impact Arch, they seem to only repack the main deb)

---

### Post by darco on 2009-08-02
> **ubulette said:**
> I've just updated the package to remove its HTML5 codecs. The debacle between Apple, Google and Mozilla made me create two separate codec packages:

- chromium-codecs-ffmpeg with ogg, vorbis and theora
- chromium-codecs-ffmpeg-nonfree with the 3 above + H.264, MP3 and AAC

(the reason non-free includes the free codecs is that ffmpeg ships that within the same files).

The two packages conflict with each other. The free one will be installed by default (you have to dist/safe-upgrade).

Note: you need to wait for todays build for this to happen (>= 3.0.197.0~svn20090802r22252), don't update manually, it won't work.

(this will impact Arch, they seem to only repack the main deb)

Wow, its nice to have a Developer from Chromium in these forums!
Great job...I wish Chromium would develop a x64 bit browser but I already read why they arent at this stage....

darco

---

### Post by ubulette on 2009-08-02
> **darco said:**
> 
I wish Chromium would develop a x64 bit browser but I already read why they arent at this stage....


I have a prototype locally, it's almost there. I will update the packaging (used for the PPA) as soon as it's usable.

---

### Post by wersdaluv on 2009-08-02
> **jonathanysp said:**
> oh cool! i just noticed that as well, pretty nice. but i dont really get why google doesnt want the normal borders. It makes it look out of place, even in windows...and doesnt this make it harder to render on the screen? Anyways its getting better and better each release.

i hardly use the stepper things now since theres the scroll wheel and you can still move the scrollbar with middle clicks which is much faster. The only thing left is stable a stable flash plugin!
Yep. Stable flash plugin could be a deal breaker. The nice thing about their window border is that it saves screen space. Chrome and Chromium wants to be as minimalistic as possible

---

### Post by rajcan on 2009-08-02
> **wersdaluv said:**
> Yep. Stable flash plugin could be a deal breaker. The nice thing about their window border is that it saves screen space. Chrome and Chromium wants to be as minimalistic as possible

Well they're getting that, and even other browsers have picked up on that. Look at the new Safari 4 :D. My default browser on my XP vm.

---

### Post by hanzomon4 on 2009-08-02
Screenshot?

---

### Post by RATM_Owns on 2009-08-02
> **.Maleficus. said:**
> Are you using the chromium-browser package from AUR? 
The chromium-snapshot packages I made in the AUR which had 3 votes when I gave it to a guy now has like, 220 votes. :P

Here's my little Chromium updating script (downloads zip file from chromium.org).
[http://pastebin.com/f64a96676](http://pastebin.com/f64a96676)

Run it whenever. :P
It will unpack it into chrome-linux folder, then delete and replace it when you update it.

Improvements are welcome because it's a pretty crappy script. And it's written pretty ugly (by my terms, at least).

---

### Post by Chemical Imbalance on 2009-08-02
> **hanzomon4 said:**
> screenshot?

+1

---

### Post by keiichidono on 2009-08-02
> **chemical imbalance said:**
> +1

+2

---

### Post by Regenweald on 2009-08-02
my gnome window colour is grey though :)

For those in karmic and who'd like to use the ppa, this command will sort you out.
```

sudo add-apt-repository ppa:chromium-daily

```

---

### Post by Chemical Imbalance on 2009-08-02
> **regenweald said:**
> my gnome window colour is grey though :)

Woohoo
\\:D/

---

### Post by sertse on 2009-08-02
Umm, I'm sure native Chrome borders (as opposed to your WM) has been around for quite a while. The checkbox to switch between your WM and chrome native was available when you right clicked the tab bar etc. The recent change was only to make it default. 

The other changes are quitw recent though, I'll agree. Chrome would be my default browser but for this bug. The thought that sites could be blacklisted without a way to undo them is a show stopper for me.

[http://code.google.com/p/chromium/issues/detail?id=15247](http://code.google.com/p/chromium/issues/detail?id=15247)

---

### Post by penguindrive on 2009-08-02
Chromium gets 4405 for me on the peacekeeper benchmark, the highest score I have observed. 
[http://service.futuremark.com/peacekeeper/index.action](http://service.futuremark.com/peacekeeper/index.action)

---

### Post by MikeTheC on 2009-08-02
Yeah, 3.0.196 is out for Mac OS X as well. I just installed it and I'm running it right now.

It's definitely one fast little browser. However, it's still miles away from being complete, and at least as far away from me switching to it. But, heck, one day... you never know.

---

### Post by JillSwift on 2009-08-02
> **penguindrive said:**
> Chromium gets 4405 for me on the peacekeeper benchmark, the highest score I have observed. 
[http://service.futuremark.com/peacekeeper/index.action](http://service.futuremark.com/peacekeeper/index.action)
What sort of machine are you running that on? Best my copy of Chrome manages is 1833.
(3.0.196.0 on a Pentium D 2.8Ghs, 2GB, 9400GT)

---

### Post by hanzomon4 on 2009-08-02
> **Regenweald said:**
> my gnome window colour is grey though :)

For those in karmic and who'd like to use the ppa, this command will sort you out.
```

sudo add-apt-repository ppa:chromium-daily

```

YaY

---

### Post by Vrekk on 2009-08-02
For me Chromium laned a score of 1942 while firefox 3.5 got a 813 :D

(2.66ghz PD dual core, 2GB ram, 8500gt, 64bit arch)

---

### Post by .Maleficus. on 2009-08-03
> **RATM_Owns said:**
> The chromium-snapshot packages I made in the AUR which had 3 votes when I gave it to a guy now has like, 220 votes. :P

Here's my little Chromium updating script (downloads zip file from chromium.org).
[http://pastebin.com/f64a96676](http://pastebin.com/f64a96676)

Run it whenever. :P
It will unpack it into chrome-linux folder, then delete and replace it when you update it.

Improvements are welcome because it's a pretty crappy script. And it's written pretty ugly (by my terms, at least).
Awesome, I'll install that tomorrow when I boot up Arch next, thanks for the heads up.

---

### Post by days_of_ruin on 2009-08-03
> **Regenweald said:**
> my gnome window colour is grey though :)

For those in karmic and who'd like to use the ppa, this command will sort you out.
```

sudo add-apt-repository ppa:chromium-daily

```

That's a sweet command, does it automatically get the key for you?
lp + ubuntu = EPIC WIN!

---

### Post by penguindrive on 2009-08-03
> **JillSwift said:**
> What sort of machine are you running that on? Best my copy of Chrome manages is 1833.
(3.0.196.0 on a Pentium D 2.8Ghs, 2GB, 9400GT)

An intel core 2 duo e7300 OC'd to 3.0ghz, 2 gb ddr2 ram, 8600gt.:)

---

### Post by Giant Speck on 2009-08-03
I could definitely make the switch if Java worked.

Did anyone else notice the option to get themes directly from Google?

---

### Post by kpkeerthi on 2009-08-03
Can chrome/chromium block Ads?

---

### Post by OutOfReach on 2009-08-03
> **Giant Speck said:**
> 
Did anyone else notice the option to get themes directly from Google?

Yep, but apparently the page doesn't exist yet.

---

### Post by Giant Speck on 2009-08-03
> **OutOfReach said:**
> Yep, but apparently the page doesn't exist yet.

Yeah, I noticed that, too.

I don't like the way Chromium looks when it tries to use my GTK theme, but I'd be willing to try out a couple themes from their website when they do eventually put it up.

---

### Post by Dobbie03 on 2009-08-03
what puts me off is that I cant get flash to work otherwise I would use Chromium.

---

### Post by Giant Speck on 2009-08-03
> **MattDobson said:**
> what puts me off is that I cant get flash to work otherwise I would use Chromium.

Take a good look at my thread:  [http://ubuntuforums.org/showthread.php?t=1207863](http://ubuntuforums.org/showthread.php?t=1207863)

There is some really helpful information in there.

---

### Post by hugmenot on 2009-08-03
Can anyone point me to a page that shows HTML5 embedded video to be working?

I&#8217;ve got ffmpeg-non-free installed from the repo, but any page with a video element I visit just downloads the file. No playback.

---

### Post by wersdaluv on 2009-08-03
Mine's weird. I made a correct flashplugin-alternative.so link. It worked without that, btw. I just had to "--enable-plugins". 

Now, I have the right firefox flashplugin-alternative.so link and the "--enable-plugins" flag. Flash videos play without sound. Any idea? :)

---

### Post by darco on 2009-08-03
> **kpkeerthi said:**
> Can chrome/chromium block Ads?

Yes...
Clink on a crx link (such as adsweep) and browse to chrome://extensions/ to check installation.

darco

---

### Post by bluebyt on 2009-08-03
Can someone confirm this bug, it happen to me on  my favorite website Deviantart.

1-Go to DeviantArt: [http://www.deviantart.com/]("http://www.deviantart.com/")

2-Navigate throught the menu example:Customization/Skin & themes

3- Click on any theme and go back one page.

Bug :The browser go back to the main page of Deviantart.

Let me know, I will post this bug later.

---

### Post by Giant Speck on 2009-08-03
> **bluebyt said:**
> Can someone confirm this bug, it happen to me on  my favorite website Deviantart.

1-Go to DeviantArt: [http://www.deviantart.com/](http://www.deviantart.com/)

2-Navigate throught the menu example:Customization/Skin & themes

3- Click on any theme and go back one page.

Bug :The browser go back to the main page of Deviantart.

Let me know, I will post this bug later.

That's not a Chromium bug.  That's a deviantART bug.  I've had that very same thing happen in Firefox.

---

### Post by bluebyt on 2009-08-03
> **Giant Speck said:**
> That's not a Chromium bug.  That's a deviantART bug.  I've had that very same thing happen in Firefox.

Nope never happened with firefox.

Edit: I just tried with Opera,Midori and it working good, only occurred when I used Chromium.

---

### Post by killthepoor187 on 2009-08-04
For those wondering about the new theme support, there are two available (to my knowledge).  Go [here]("http://download.cnet.com/8301-2007_4-10299814-12.html?part=rss&tag=feed&subj=TheDownloadBlog") (cnet.com) to check them out.

Hopefully the official themes page will be up soon.  :D

I ran a couple of benchmarks and chromium beat the crap out of ff 3.5.2 by a country mile.  And as far as stability goes, the most I've had to do was hit the reload button, and it's so fast it doesn't even matter.  :P

Chromium is my new linux browser at this point.  Alpha tag be damned, 3.0.197.0 is working like a champ for me.  :D

---

### Post by moster on 2009-08-04
Is there any way to block ads in chromium? I find it at least double faster on nmy box and I would like to SWITCH :)

---

### Post by Giant Speck on 2009-08-04
> **killthepoor187 said:**
> For those wondering about the new theme support, there are two available (to my knowledge).  Go [here]("http://download.cnet.com/8301-2007_4-10299814-12.html?part=rss&tag=feed&subj=TheDownloadBlog") (cnet.com) to check them out.

Hopefully the official themes page will be up soon.  :D

I like the idea of a color chooser.

---

### Post by quazi on 2009-08-04
Chromium seems more or less suitable for general use right now. For me, the only advantage that firefox has is its extensions (and it actually uses my emerald theme.  Chromium refuses to do so).

---

### Post by ubulette on 2009-08-04
> **hugmenot said:**
> Can anyone point me to a page that shows HTML5 embedded video to be working?

I’ve got ffmpeg-non-free installed from the repo, but any page with a video element I visit just downloads the file. No playback.

it's a known upstream bug, see [http://code.google.com/p/chromium/issues/detail?id=18329](http://code.google.com/p/chromium/issues/detail?id=18329). If you want to help, you may star the bug, its priority could raise.

---

### Post by Chemical Imbalance on 2009-08-04
I love this browser.  It is wicked fast (to judge my enthusiasm, I've never used the word "wicked" before :) ).

Firefox crawls compared to Chromium.

I will be switching when it is released provided NoScript or something similar is compatible with it.

Screen: 

[ATTACH]123613[/ATTACH]


edit: Does DNS prefetching have any disadvantages anyone can think of?

---

### Post by Regenweald on 2009-08-04
> **quazi said:**
> Chromium seems more or less suitable for general use right now. For me, the only advantage that firefox has is its extensions (and it actually uses my emerald theme.  Chromium refuses to do so).

i use emerald also, but because of the space saving design of chromium, i hope that there is a final option to accept the theme colours but ignore the window manager. I REALLY love the default when maximized.

---

### Post by quazi on 2009-08-04
> **Regenweald said:**
> i use emerald also, but because of the space saving design of chromium, i hope that there is a final option to accept the theme colours but ignore the window manager. I REALLY love the default when maximized.

Well, I like the look Chrome has in Windows 7 (transparent title bar).

So, the first site I've found to not work with the most up to date version of chromium is espn.com.

---

### Post by Giant Speck on 2009-08-04
Omg themes are working!

---

### Post by JillSwift on 2009-08-04
When is this supposed to show up on the PPA? And if it has... why ain't I seeing it?

I want the fun, too!

---

### Post by matthew.ball on 2009-08-04
There was a problem with the previous release where the Back/Return/Refresh buttons didn't update properly it appears to be fixed.

But, I have some creepy guy's face as my quit button? lol

---

### Post by wersdaluv on 2009-08-04
> **matthew.ball said:**
> There was a problem with the previous release where the Back/Return/Refresh buttons didn't update properly it appears to be fixed.

But, I have some creepy guy's face as my quit button? lol
Screenshot! :D

---

### Post by darco on 2009-08-04
> **wersdaluv said:**
> Screenshot! :D

[http://ubuntuforums.org/showthread.php?t=1231674](http://ubuntuforums.org/showthread.php?t=1231674)

darco

---

### Post by cc8balla on 2009-08-04
> **Regenweald said:**
> i use emerald also, but because of the space saving design of chromium, i hope that there is a final option to accept the theme colours but ignore the window manager. I REALLY love the default when maximized.

Right click on the titlebar > uncheck the box that says "Use System Title Bar and Borders"

Then go to Options > Personal Stuff > Set to GTK theme

Problem solved :P

---

### Post by Regenweald on 2009-08-05
> **cc8balla said:**
> Right click on the titlebar > uncheck the box that says "Use System Title Bar and Borders"

Then go to Options > Personal Stuff > Set to GTK theme

Problem solved :P

Great stuff man, thanks a lot :)
I totally read your post, tried it out, thought: 'oh cool' then read the ENTIRE post and realized you were replying to me in the first place! lol.
It's that time of night :)

---

### Post by wersdaluv on 2009-08-05
OMG I GOT THE GUY's FACE TOO! LOL

---

### Post by captaincrook on 2009-08-05
Any chance for an exif reader and potentially better adblock?

---

### Post by matthew.ball on 2009-08-05
> **wersdaluv said:**
> OMG I GOT THE GUY's FACE TOO! LOL
An easy fix, [http://ubuntuforums.org/showpost.php?p=7735526&postcount=54](http://ubuntuforums.org/showpost.php?p=7735526&postcount=54)

---

### Post by cc8balla on 2009-08-05
> **Regenweald said:**
> Great stuff man, thanks a lot :)
I totally read your post, tried it out, thought: 'oh cool' then read the ENTIRE post and realized you were replying to me in the first place! lol.
It's that time of night :)
Hahah :P

---

### Post by mrgnash on 2009-08-05
> **darco said:**
> Yes...
Clink on a crx link (such as adsweep) and browse to chrome://extensions/ to check installation.

darco

Google Chrome/Chromium only asks if you want to save a .crx file, rather than installing it.

---

### Post by wingnux on 2009-08-05
3.0.198 is out! =)

---

### Post by wersdaluv on 2009-08-05
> **wingnux said:**
> 3.0.198 is out! =)
Where did you get that? The chromium PPA doesnt release it yet

---

### Post by darco on 2009-08-05
its there now!

darco

---

### Post by wersdaluv on 2009-08-06
> **darco said:**
> its there now!

darco
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main #Chromium Daily <- here? 

I dont have it :(

EDIT:
Oh. No 64bit package yet

---

### Post by el-mar01 on 2009-08-06
Does anyone else have the problem where you scroll a page that contains flash it scrolls REALLY slowly ?? (I'm using the NVIDIA 190.18.03 drivers) .. a page with flash scrolls fine in Firefox.

---

### Post by OutOfReach on 2009-08-06
> **el-mar01 said:**
> Does anyone else have the problem where you scroll a page that contains flash it scrolls REALLY slowly ?? (I'm using the NVIDIA 190.18.03 drivers) .. a page with flash scrolls fine in Firefox.
Indeed it is somewhat sluggish, especially on a page with multiple flash videos embedded. Hopefully it'll be improved later on

---

### Post by wersdaluv on 2009-08-06
> **el-mar01 said:**
> Does anyone else have the problem where you scroll a page that contains flash it scrolls REALLY slowly ?? (I'm using the NVIDIA 190.18.03 drivers) .. a page with flash scrolls fine in Firefox.
Same here

---

### Post by moster on 2009-08-06
I have different problem. Look at occupied memory after surfing little  with few tabs open. I usually have 300/2000 and after chromium, even if I close it I get around 800/2000 occupied.

---

### Post by Giant Speck on 2009-08-06
> **el-mar01 said:**
> Does anyone else have the problem where you scroll a page that contains flash it scrolls REALLY slowly ?? (I'm using the NVIDIA 190.18.03 drivers) .. a page with flash scrolls fine in Firefox.

Weirdly enough, I have that problem in Firefox but not in Chromium.

---

### Post by Giant Speck on 2009-08-06
Oooh!  They changed the close, minimize, and maximize buttons!  They look less like Vista!

---

### Post by keiichidono on 2009-08-06
> **Giant Speck said:**
> Oooh!  They changed the close, minimize, and maximize buttons!  They look less like Vista!

Screenshot or GTFO.

---

### Post by Giant Speck on 2009-08-06
> **CalvinB said:**
> Screenshot or GTFO.

Screenshot attached!  :D

The buttons are the same for any theme.

---

### Post by keiichidono on 2009-08-06
> **Giant Speck said:**
> Screenshot attached!  :D

The buttons are the same for any theme.

Awesome. :cool:

---

### Post by Dougie187 on 2009-08-06
It appears they have removed Glen's face from the exit button as well?

Maybe they got tired of bug reports about it. For some reason my ppa isn't updating. Maybe it will soon.

---

### Post by wersdaluv on 2009-08-06
> **Dougie187 said:**
> It appears they have removed Glen's face from the exit button as well?

Maybe they got tired of bug reports about it. For some reason my ppa isn't updating. Maybe it will soon.
There's no 64bit package yet. Perhaps, you're on a 64bit Ubuntu

---

### Post by JillSwift on 2009-08-06
> **wersdaluv said:**
> There's no 64bit package yet. Perhaps, you're on a 64bit Ubuntu
I'm using 32 bit, and the PPA hasn't updated for me since 3.0.196.0

---

### Post by Giant Speck on 2009-08-06
> **JillSwift said:**
> I'm using 32 bit, and the PPA hasn't updated for me since 3.0.196.0

Are you just waiting for Update Manager to notify you of the update or are you actually opening a terminal and updating it manually?  Because that's what I had to do to update to 3.0.198.0.

---

### Post by Dougie187 on 2009-08-06
> **wersdaluv said:**
> There's no 64bit package yet. Perhaps, you're on a 64bit Ubuntu

I am, so I think I missed that earlier in the thread. Though, I didn't think the 64 bit package updated. I thought there was a 32 bit browser, and then some 64 bit compatibility libraries.

Mainly because there were more packages you had to install on 64 than just chromium-browser. Also though, 64 bit flash doesn't work, I have to use the 32 bit one in chromium. But I may have just done something wrong for that.

---

### Post by wersdaluv on 2009-08-06
> **JillSwift said:**
> I'm using 32 bit, and the PPA hasn't updated for me since 3.0.196.0
You must be using Chrome instead of Chromium.

---

### Post by Dougie187 on 2009-08-06
It would appear as if the 64 bit version was upgraded finally.

3.0.198.0

---

### Post by darco on 2009-08-06
> **Dougie187 said:**
> It would appear as if the 64 bit version was upgraded finally.

3.0.198.0

Well its FOR the x64 OS but its NOT an x64 browser...

darco

*edit* maybe Im wrong.....checking the ppa site

---

### Post by Regenweald on 2009-08-06
> **darco said:**
> Well its FOR the x64 OS but its NOT an x64 browser...

darco

*edit* maybe Im wrong.....checking the ppa site

Still depends on ia32libs, maybe the full 64bit is not ready yet.

---

### Post by Incense on 2009-08-06
Running the latest build, and it's really nice. So far stable, fast, and it looks great. Nice having a normal close button again.

---

### Post by Chemical Imbalance on 2009-08-06
Running 'chromium-browser --enable-plugins' doesn't get flash working for me.  I'm on 64 bit btw.

Yes, flash is installed through the repos for Firefox.

Do you have to manually create a link to chromium from firefox's plugins or is 'enable-plugins' enough?

Oh, and I like the new buttons much better, especially since mr.evil eye is gone.

---

### Post by ubulette on 2009-08-06
since yesterday, you can have a localized Chromium.

I've introduced _chromium-browser-l10n_ supporting ~50 languages:
 ar, bg, bn, ca, cs, da, de, el, en-GB, es-419, es, et, fi, fil, fr, gu, he,
 hi, hr, hu, id, it, ja, kn, ko, lt, lv, ml, mr, nb, nl, or, pl, pt-BR, pt-PT,
 ro, ru, sk, sl, sr, sv, ta, te, th, tr, uk, vi, zh-CN, zh-TW

It is optional and *not* needed if your desktop is in en-US.

---

### Post by hyperdude111 on 2009-08-06
> **Chemical Imbalance said:**
> Running 'chromium-browser --enable-plugins' doesn't get flash working for me.  I'm on 64 bit btw.

Yes, flash is installed through the repos for Firefox.

Do you have to manually create a link to chromium from firefox's plugins or is 'enable-plugins' enough?

Oh, and I like the new buttons much better, especially since mr.evil eye is gone.


Because 64bit is actually using the 32bit browser under ia32 libs flash wont work. Im just waiting for them to make a native 64 bit browser.

---

### Post by Regenweald on 2009-08-06
> **hyperdude111 said:**
> Because 64bit is actually using the 32bit browser under ia32 libs flash wont work. Im just waiting for them to make a native 64 bit browser.

me too, patiently i might add. Chromium, even in it's development state, seems to be the premier webkit implementation. In under 2 weeks it's become my default browser with opera as a backup.

the ia32libs are kind of big so i'll welcome true 64bit when it arrives :) updates on a 35down connection can be agonizing :)

---

### Post by OutOfReach on 2009-08-06
> **ubulette said:**
> since yesterday, you can have a localized Chromium.

I've introduced _chromium-browser-l10n_ supporting ~50 languages:
 ar, bg, bn, ca, cs, da, de, el, en-GB, es-419, es, et, fi, fil, fr, gu, he,
 hi, hr, hu, id, it, ja, kn, ko, lt, lv, ml, mr, nb, nl, or, pl, pt-BR, pt-PT,
 ro, ru, sk, sl, sr, sv, ta, te, th, tr, uk, vi, zh-CN, zh-TW

It is optional and *not* needed if your desktop is in en-US.

Nice, thanks for your hard work :)

---

### Post by Chemical Imbalance on 2009-08-06
> **hyperdude111 said:**
> Because 64bit is actually using the 32bit browser under ia32 libs flash wont work. Im just waiting for them to make a native 64 bit browser.

Ah, I forgot about that--thanks.

I guess my eee is getting some Chromium-love next then.

---

### Post by ubulette on 2009-08-06
> **hyperdude111 said:**
> Im just waiting for them to make a native 64 bit browser.

it's getting close. I'll sure shift the PPA to native once it's ready.

---

### Post by Giant Speck on 2009-08-06
Still waiting for Java... :?

---

### Post by Regenweald on 2009-08-06
> **ubulette said:**
> it's getting close. I'll sure shift the PPA to native once it's ready.

take your time :) 32bit libs or not, chromium is the fastest browser I've ever used. Gives usable browsing even when torrents are choking my bandwith.

---

### Post by darco on 2009-08-06
> **Chemical Imbalance said:**
> Running 'chromium-browser --enable-plugins' doesn't get flash working for me.  I'm on 64 bit btw.

Yes, flash is installed through the repos for Firefox.

Do you have to manually create a link to chromium from firefox's plugins or is 'enable-plugins' enough?

Oh, and I like the new buttons much better, especially since mr.evil eye is gone.

You can dump an x32 flash into the chromimum/plugins folder and it works fine...thats how i have it setup....

darco

---

### Post by darco on 2009-08-06
> **Regenweald said:**
> In under 2 weeks it's become my default browser with opera as a backup.



Heh, just like me! Hope its the x64 bit Opera 10b, right?

darco

---

### Post by wersdaluv on 2009-08-06
I'm on 64 bit. Flash videos don't have sound :| any idea?

---

### Post by donniezazen on 2009-08-06
Fully agree i am using 3.0.198.0 and its far better than chrome.

---

### Post by Regenweald on 2009-08-06
> **darco said:**
> Heh, just like me! Hope its the x64 bit Opera 10b, right?

darco

But of course! :) I have the latest build site bookmarked and check periodically, but no new builds for a while now...latest seems to be 4453 in qt4.

Edit; sorry to derail guys....

---

### Post by darco on 2009-08-07
> **Regenweald said:**
> But of course! :) I have the latest build site bookmarked and check periodically, but no new builds for a while now...latest seems to be 4453 in qt4.

Edit; sorry to derail guys....

4520 came out a few days ago....

darco

---

### Post by Dougie187 on 2009-08-07
With the new update it appears that facebook's security token has been revoked. Chrome doesn't like the idea of logging into facebook now.

Not that I care, but it's kind of funny.

---

### Post by Giant Speck on 2009-08-07
> **Dougie187 said:**
> With the new update it appears that facebook's security token has been revoked. Chrome doesn't like the idea of logging into facebook now.

Not that I care, but it's kind of funny.

I'm on 3.0.198.0 and I was able to log into Facebook just fine.

---

### Post by OutOfReach on 2009-08-07
I can confirm the problem with security certificates, I've tried with Myspace and Xbox Live, seems like it denies every site with an https connection.
I'm also using 3.0.198.0

---

### Post by darco on 2009-08-07
I just updated chromium (22729)and tested my wife's face book....

The server's security certificate is revoked!
You attempted to reach login.facebook.com, but the certificate that the server presented has been revoked by its issuer. This means that the security credentials the server presented absolutely should not be trusted. You may be communicating with an attacker. You should not proceed.

heh

darco

---

### Post by sertse on 2009-08-08
> **sertse said:**
> Chrome would be my default browser but for this bug. The thought that sites could be blacklisted without a way to undo them is a show stopper for me.

[http://code.google.com/p/chromium/issues/detail?id=15247](http://code.google.com/p/chromium/issues/detail?id=15247)

This pet bug was fixed yestersday. However,  the latest updates brought this annoying bug ;)

[http://code.google.com/p/chromium/issues/detail?id=18602](http://code.google.com/p/chromium/issues/detail?id=18602)

...Which is fixed and probably solved when the PPA gets the next daily build. 

I also experience the https/certificate errr when accessing facebook. Hope it gets fixed soon.

---

### Post by darco on 2009-08-08
Latest build has not fixed the https issue.....

darco

---

### Post by ubulette on 2009-08-08
> **darco said:**
> Latest build has not fixed the https issue.....

not built yet, just watch [https://edge.launchpad.net/~chromium-daily/+archive/ppa](https://edge.launchpad.net/~chromium-daily/+archive/ppa) (Build status needs to be green).

---

### Post by darco on 2009-08-08
> **ubulette said:**
> not built yet, just watch [https://edge.launchpad.net/~chromium-daily/+archive/ppa](https://edge.launchpad.net/~chromium-daily/+archive/ppa) (Build status needs to be green).

Thanks ubulette...updated,all is well......

darco

---

### Post by mrgnash on 2009-08-08
The official Google Chrome "unstable" branch seems to have been updated to 197 as well now, and I can already notice a lot of improvements/bug-fixes. Really great to see this project steaming ahead on Linux, as I used this browser extensively when I was forced to use Windows for a few months, and even at this stage of development it's totally awesome. All it needs now are vi key-bindings a-la Vimperator :P

---

### Post by Tipped OuT on 2009-08-08
Has Chrome crashed on anyone yet? Chrome always becomes unresponisive after sometime of using it, and I can't close it, or do anything to it, it's just stuck there.

---

### Post by wersdaluv on 2009-08-08
It does for me, because of flash

---

### Post by Regenweald on 2009-08-08
> **Tipped OuT said:**
> Has Chrome crashed on anyone yet? Chrome always becomes unresponisive after sometime of using it, and I can't close it, or do anything to it, it's just stuck there.

I don't use flash, but sometimes a page will just get stuck and unresponsive in which case i just close the tab and start fresh. This is not a frequent thing though.

---

### Post by moster on 2009-08-09
> **Tipped OuT said:**
> Has Chrome crashed on anyone yet? Chrome always becomes unresponisive after sometime of using it, and I can't close it, or do anything to it, it's just stuck there.

No, but uses ton of memory. It seems it has some leaks.

---

### Post by wingnux on 2009-08-11
3.0.201 is out! =)

Btw, does anyone know where can I read the changelog of those svn builds?

---

### Post by nortexoid on 2009-08-11
> **Regenweald said:**
> i use emerald also, but because of the space saving design of chromium, i hope that there is a final option to accept the theme colours but ignore the window manager. I REALLY love the default when maximized.

I really like the controls (radio buttons, scroll bars, etc.) used by chromium especially when using a dark theme, because dark themes NEVER work with firefox (and using custom CSS files are never quite satisfactory). But it would be nice to have chromium adopt all GTK elements, not just the window borders, which it doesn't even adopt properly.

One problem I've encountered using Emerald is that middle clicking anywhere in a chromium window displays backgrounds windows (from non-chromium apps) as it would if you clicked only on the title bar. In essence, the whole window has the behavior of a title bar on middle click! This is lame since default behavior for middle click is also opening links in new tab. Middle clicking links causes the link to open in a new tab but also displays all background windows.

Update: apparently the bug I mentioned above with emerald is fixed in the latest build (after 3.0.198.0).

---

### Post by nortexoid on 2009-08-11
> **Giant Speck said:**
> Are you just waiting for Update Manager to notify you of the update or are you actually opening a terminal and updating it manually?  Because that's what I had to do to update to 3.0.198.0.

How'd you update manually? There's a bug fix in the 3.9.201.0 release that I need. I'm updating from 3.0.198.0.

---

### Post by hyperdude111 on 2009-08-11
> **nortexoid said:**
> How'd you update manually? There's a bug fix in the 3.9.201.0 release that I need. I'm updating from 3.0.198.0.

```
sudo apt-get update && sudo apt-get install chromium-browser
```

---

### Post by Chemical Imbalance on 2009-08-11
I wish Chromium had a 'dump all cookies and privacy data upon close' function like firefox. 
 It annoys me having to clear this manually each time I close chromium.

I would like to see a bookmarks menu button on the default toolbar too instead of  having to hit ctrl+b every time (the bookmarks toolbar is way to big to keep on all the time).

---

### Post by nortexoid on 2009-08-11
> **hyperdude111 said:**
> ```
sudo apt-get update && sudo apt-get install chromium-browser
```

Thanks very much!

---

### Post by Giant Speck on 2009-08-11
Still no Java.  :(

---

### Post by darco on 2009-08-12
Things are moving along quickly....

---

### Post by hellmet on 2009-08-14
Very quickly.. And I'm really loving it! The main thing being its Open-source and without a EULA!
I just wish Google released the source code for GTalk.

---

### Post by renkinjutsu on 2009-08-14
> **Chemical Imbalance said:**
> I wish Chromium had a 'dump all cookies and privacy data upon close' function like firefox. 
 It annoys me having to clear this manually each time I close chromium.

I would like to see a bookmarks menu button on the default toolbar too instead of  having to hit ctrl+b every time (the bookmarks toolbar is way to big to keep on all the time).

then you should just use the incognito mode by default..
also, the bookmark bar can be hidden.. ctrl+b toggles it

---

### Post by Chemical Imbalance on 2009-08-14
> **renkinjutsu said:**
> 
also, the bookmark bar can be hidden.. ctrl+b toggles it

I know, I mentioned that.  It's annoying to have to toggle it.  There should be a button, say next to the refresh button, that gives you the bookmarks menu.

---

### Post by MarcusW on 2009-08-16
Am I the only one having problems with the download speed from the PPA? Seems to almost stop completely after a while. :S

---

### Post by Regenweald on 2009-08-17
Chromium seems to have trimmed a lot of fat, ppa download down to 14+ as opposed to 18+ megs. And always getting faster. What's going on under the hood ? :)

---

### Post by MarcusW on 2009-08-17
Now it works. :D What is the real difference between Chromium and Chrome? I mean, the "about" page seems kinda sketchy, seems like "chrome" is just switched to "chromium".

---

### Post by hyperdude111 on 2009-08-17
Hmm, i cant upgrade chromium.

Apparently a dependency I have not had a problem with so far is now an issue. 
> lib32stdc++6 (>= 4.4.0) but 4.3.3-5ubuntu4 is to be installed 

Weird thing is I cant find the version of the dependency they're talking about anywhere.


EDIT:
Ahh, apptitiude install works but not apt-get install.

---

### Post by MellonCollie on 2009-08-17
> **MarcusW said:**
> Now it works. :D What is the real difference between Chromium and Chrome? 

> Chromium is the name we have given to the open source project and the browser source code that we released and maintain at [www.chromium.org](www.chromium.org). One can compile this source code to get a fully working browser. Google takes this source code, and adds on the Google name and logo, an auto-updater system called GoogleUpdate, and RLZ (described later in this post), and calls this Google Chrome. 

[http://blog.chromium.org/2008/10/google-chrome-chromium-and-google.html](http://blog.chromium.org/2008/10/google-chrome-chromium-and-google.html)

.

---

### Post by MarcusW on 2009-08-17
So then Chromium is basically Chrome but without the EULA and a few minor differences? I'm looking forward to when Chromium has the same "abilities" as Firefox. I really like Chromium, both the speed and the ease of use. Firefox just seems to get slower for each version while all supporters say "Wow, new FF is fast!". :P

EDIT: The fact that chromium.org redirected to google code confused me in the same way the "about" page did though. ^^

---

### Post by adalal on 2009-08-18
So, when is Java going to be supported for this?... That is literally the only thing I'm waiting for.

---

### Post by graaant on 2009-08-18
> **adalal said:**
> So, when is Java going to be supported for this?... That is literally the only thing I'm waiting for.

Does java work with --enable-plugins?

---

### Post by Katalog on 2009-08-18
> **renkinjutsu said:**
> then you should just use the incognito mode by default..
also, the bookmark bar can be hidden.. ctrl+b toggles it

> **Chemical Imbalance said:**
> I know, I mentioned that.  It's annoying to have to toggle it.  There should be a button, say next to the refresh button, that gives you the bookmarks menu.

TOTALLY agree. I love Chromium to death (typing this reply from it right now), but it drives me nuts that you can't customize the toolbar. ](*,)

---

### Post by Katalog on 2009-08-18
> **graaant said:**
> Does java work with --enable-plugins?

Interesting question. When I type "about: plugins" in the toolbar it says that the Java plugins are enabled, but it doesn't seem to work on any of the Java test suites I've tried out. :confused:

---

### Post by misfitpierce on 2009-08-18
4.0.202.0 (23528)
I got that build and cant seem to download themes for it or it just shuts down and restarts which is odd... Oh well!

---

### Post by mrgnash on 2009-08-18
> **misfitpierce said:**
> 4.0.202.0 (23528)
I got that build and cant seem to download themes for it or it just shuts down and restarts which is odd... Oh well!

The themes are only for Windows at the moment.

---

### Post by hyperdude111 on 2009-08-18
> **mrgnash said:**
> The themes are only for Windows at the moment.

I have themes, just wait i'll attach a screenshot.

---

### Post by hyperdude111 on 2009-08-18
It wont let me edit the post with a screenshot so i'll post again.

---

### Post by mrgnash on 2009-08-18
> **hyperdude111 said:**
> It wont let me edit the post with a screenshot so i'll post again.

Oh ok. I stand corrected :oops:

---

### Post by Ric_NYC on 2009-08-18
How to install themes... (no command line needed.... :) )

[B]
Tools (the wrench icon on the right) > Options > Personal Stuff tab > Get Themes... Choose the theme you like... it will change the theme without restarting Chromium[/B].

---

### Post by hanzomon4 on 2009-08-18
This is one sick browser... Only issues because it's 32bit my qtcurve or whatever controls the look of gtk apps in kde doesn't work and I've got no sound in flash videos.

---

### Post by gjoellee on 2009-08-18
> **misfitpierce said:**
> 4.0.202.0 (23528)
I got that build and cant seem to download themes for it or it just shuts down and restarts which is odd... Oh well!

Hmmm....I can use themes with that version :confused:

---

### Post by hanzomon4 on 2009-08-18
Take that back sound works... buggy behavior in ubuntu regarding the mute key (for real I had to press mute then raise the volume, if I just pressed the unmute key the volume bar would go up but no sound would be heard)

---

### Post by Giant Speck on 2009-08-18
Still.  No.  Java...

---

### Post by Regenweald on 2009-08-18
Anyone having problems with downloads in build 4.0.202.0 (23607)? seems to hard exit on clicking of a download link.

---

### Post by graaant on 2009-08-19
Latest build 23670 seems to use gtk+ theme properly now in Kubuntu. Doesn't look so ugly. Definitely a big plus! :)

---

### Post by ubulette on 2009-08-19
Since last night (>= 4.0.203.0~), the Ubuntu amd64 debs are native x64 builds. No ia32 anymore. Hopefully, that would mean a better user experience.

if you've added some symlinks manually, you may have issues with the corresponding plugins. Try to remove them all, Chromium already knows where to look for system & user plugins.

If you find regressions, please file bugs following this [procedure]("https://wiki.ubuntu.com/Chromium/Debug")

Note: you can remove ia32-libs-chromium-browser if you want, it's no longer needed.

---

### Post by Regenweald on 2009-08-19
> **ubulette said:**
> Since last night (>= 4.0.203.0~), the Ubuntu amd64 debs are native x64 builds. No ia32 anymore. Hopefully, that would mean a better user experience.

if you've added some symlinks manually, you may have issues with the corresponding plugins. Try to remove them all, Chromium already knows where to look for system & user plugins.

If you find regressions, please file bugs following this [procedure]("https://wiki.ubuntu.com/Chromium/Debug")

Note: you can remove ia32-libs-chromium-browser if you want, it's no longer needed.

You really were not joking when you said native 64 bit was coming soon, thanks so much. Aptitude removed ia32 in the upgrade, imagine my surprise. Chromium is immediately responding faster. 

How can one remove symlinks ?

---

### Post by hanzomon4 on 2009-08-19
Dude... :guitar:

---

### Post by alphaniner on 2009-08-19
Anyone know if it's possible to enable auto-scrolling?

---

### Post by Regenweald on 2009-08-19
> **days_of_ruin said:**
> That's a sweet command, does it automatically get the key for you?
lp + ubuntu = EPIC WIN!

Guess you know by now, but yes it does :) sorry i missed the question man.
Talk about tardy!

---

### Post by darco on 2009-08-19
> **ubulette said:**
> Since last night (>= 4.0.203.0~), the Ubuntu amd64 debs are native x64 builds. No ia32 anymore. Hopefully, that would mean a better user experience.

if you've added some symlinks manually, you may have issues with the corresponding plugins. Try to remove them all, Chromium already knows where to look for system & user plugins.

If you find regressions, please file bugs following this [procedure]("https://wiki.ubuntu.com/Chromium/Debug")

Note: you can remove ia32-libs-chromium-browser if you want, it's no longer needed.

sweet.. just added the x64 flashplayer and it rocks w/chromium....great job!

---

### Post by alphaniner on 2009-08-19
To anyone who is having trouble installing a theme, I don't know if this is news but I was able to install themes by clicking on the name or pic in the Themes Gallery, then right-clicking 'Apply this theme' and selecting 'save link as...'.

-
In other news: Anyone else having trouble editing a post (here) using Chromium?  The little spinny-doodle appears but nothing else happens...

---

### Post by renkinjutsu on 2009-08-19
> **alphaniner said:**
> To anyone who is having trouble installing a theme, I don't know if this is news but I was able to install themes by clicking on the name or pic in the Themes Gallery, then right-clicking 'Apply this theme' and selecting 'save link as...'.

-
In other news: Anyone else having trouble editing a post (here) using Chromium?  The little spinny-doodle appears but nothing else happens...

just click "apply this theme" and it'll start downloading.. once it finishes, it applies the theme automatically

---

### Post by alphaniner on 2009-08-19
> **renkinjutsu said:**
> just click "apply this theme" and it'll start downloading.. once it finishes, it applies the theme automatically

For me, that causes Chromium to crash.  And I got the impression I'm not the only one.

---

### Post by Regenweald on 2009-08-19
> **alphaniner said:**
> For me, that causes Chromium to crash.  And I got the impression I'm not the only one.

I'd like to submit a bug trace, but the reporting package is 120 megs :( on a good day i get 30kb down... Any download seems to trigger the crash.

---

### Post by alphaniner on 2009-08-19
> **Regenweald said:**
> I'd like to submit a bug trace, but the reporting package is 120 megs :( on a good day i get 30kb down... Any download seems to trigger the crash.

Have you tried using ]right-click -> Save as...[ to download?

---

### Post by darco on 2009-08-19
I had a theme running prior to this latest upgrade and it works fine. When I do try to change the theme I get this error:

darco

---

### Post by Katalog on 2009-08-19
> **graaant said:**
> Does java work with --enable-plugins?

> **Katalog said:**
> Interesting question. When I type "about: plugins" in the toolbar it says that the Java plugins are enabled, but it doesn't seem to work on any of the Java test suites I've tried out. :confused:

Hm. Java must be enabled after all. I have libv8 and all that installed, but it doesn't show anything on any of the "official" Java test suites. But if I run the V8 or Sunspider tests, I do get results, so it must be working, right? :???:

---

### Post by darco on 2009-08-19
> **Katalog said:**
> Hm. Java must be enabled after all. I have libv8 and all that installed, but it doesn't show anything on any of the "official" Java test suites. But if I run the V8 or Sunspider tests, I do get results, so it must be working, right? :???:

ya, you're right...hmmm.

---

### Post by darco on 2009-08-19
I wanted to edit my previous comment but just like alphaniner says, its not working...
I wanted to mention that about:plugins now shows all plugins as it would if you ran that command in FF. Java is there , will test though..

darco

---

### Post by alphaniner on 2009-08-19
I can't view darco's image, it just darkens the visible part of the page when clicked.

---

### Post by darco on 2009-08-19
I wanted to edit my previous comment but just like alphaniner says, its not working...
I wanted to mention that about:plugins now shows all plugins as it would if you ran that command in FF. Java is there , will test though..

darco

*edit* I didnt double post ...chromimum is wacked, has a mind of its own..doing this from FF....

---

### Post by sandyd on 2009-08-19
ain't it at 4.0 now?
thats what the upgrade that i just did said....

---

### Post by Regenweald on 2009-08-19
> **alphaniner said:**
> Have you tried using ]right-click -> Save as...[ to download?

Shamefully, that did not even dawn on me :) but yeah, that works..clicking on a download link still does not. maybe with tomorrows updates, if it persists i'll bite the bullet and grab the bug report package.

---

### Post by Copernicus1234 on 2009-08-19
Funny, tried installing the browser and it said I needed the chrome ffmpeg stuff. Tried installing that and it said I needed the browser.

Dont have the time for this. :)

---

### Post by hyperdude111 on 2009-08-19
> **Copernicus1234 said:**
> Funny, tried installing the browser and it said I needed the chrome ffmpeg stuff. Tried installing that and it said I needed the browser.

Dont have the time for this. :)

Install them both at the same time, put " && " between commands.

---

### Post by itreius on 2009-08-19
Just found this via reddit. If you're annoyed by the dev page that shows up right after launching Chromium, you can get rid of it by adding this to the icon/launch command.

chrome://newtab

In which case, the full command would be

chromium-browser --enable-plugins chrome://newtab

No more of that tedious dev page, yay. :)

---

### Post by sandyd on 2009-08-19
My google chrome [see screenshot] says its version 4.0 . however, the google blog (at this time) only has a changelog for google chrome 4 / windows???

---

### Post by sandyd on 2009-08-19
WAIT!! oops. don't click the screenshot attachment if your using chrome. for me, it threw a the black screen over the page... but no picture appeared! had to reload the page to post this. then realized that chrome was so buggy, it couldn't use quickedit. aww....

---

### Post by Giant Speck on 2009-08-19
> **Katalog said:**
> Hm. Java must be enabled after all. I have libv8 and all that installed, but it doesn't show anything on any of the "official" Java test suites. But if I run the V8 or Sunspider tests, I do get results, so it must be working, right? :???:

Javascript != Java

---

### Post by moster on 2009-08-19
What is wrong? hit ALT+F2 and type ```
chromium-browser --enable-plugins
```
Everything is working just fine.

---

### Post by Giant Speck on 2009-08-19
> **moster said:**
> What is wrong? hit ALT+F2 and type ```
chromium-browser --enable-plugins
```Everything is working just fine.

Um, no it's not.  Java is not working yet, unless you have some magical Chromium browser in which Java (NOT JAVASCRIPT) works...

---

### Post by Ric_NYC on 2009-08-20
Quake Live doesn't work on Chrome.

I used Firefox to install the plugin...
BTW what kind of plugin is that?

---

### Post by hanzomon4 on 2009-08-20
> **Giant Speck said:**
> Um, no it's not.  Java is not working yet, unless you have some magical Chromium browser in which Java (NOT JAVASCRIPT) works...

What is java used for?

---

### Post by mrgnash on 2009-08-20
> **hanzomon4 said:**
> What is java used for?

Crap like [Blackboard](http://www.blackboard.com/).

---

### Post by Chemical Imbalance on 2009-08-20
Like the OP, does anybody know the changelog for the recent update.

It's at 4.0 now.

---

### Post by ubulette on 2009-08-21
> **Chemical Imbalance said:**
> Like the OP, does anybody know the changelog for the recent update.

It's at 4.0 now.

the closest thing to a human readable changelog is [http://googlechromereleases.blogspot.com/](http://googlechromereleases.blogspot.com/)
it's about Chrome, not Chromium but the delta is minimum.
It's a few days (often 1 week) behind the PPA.

---

### Post by gatorbrit on 2009-08-21
I successfully installed chromium, but when I fire it up I get this.   Any suggestions?

Cheers

---

### Post by ubulette on 2009-08-21
> **gatorbrit said:**
> I successfully installed chromium, but when I fire it up I get this.   Any suggestions?


it means the renderer for that particular tab crashed.
difficult to say more from a screenshot, without more information.
You may have some clues if you start in a terminal.
If you want to go to the bottom of it, please follow the instruction there: [https://wiki.ubuntu.com/Chromium/Debug](https://wiki.ubuntu.com/Chromium/Debug)

---

### Post by gatorbrit on 2009-08-21
This is what I get in the terminal when I try to refresh a page.  Sometimes I get a very brief glimpse of the page before the blue "Aw Snap" page.

```

[10422:10422:5320556205:ERROR:/build/buildd/chromium-browser-4.0.203.0~svn20090820r23815/build-tree/src/chrome/common/temp_scaffolding_stubs.h(72)] Not implemented reached in bool printing::PrintViewManager::OnRenderViewGone(RenderViewHost*)

```

---

### Post by moster on 2009-08-21
> **Giant Speck said:**
> Um, no it's not.  Java is not working yet, unless you have some magical Chromium browser in which Java (NOT JAVASCRIPT) works...

Yes... I did not even try java :)
Well, at least they delete that guy from right corner, obviously they are working something :)

---

### Post by Giant Speck on 2009-08-21
> **moster said:**
> Yes... I did not even try java :)
Well, at least they delete that guy from right corner, obviously they are working something :)

Yeah, and at the same time, they removed those horrible looking Vista buttons.

---

### Post by hyperdude111 on 2009-08-21
Now support NATIVE 64 bit.

---

### Post by ubulette on 2009-08-21
Starting from todays build, the 'inspector' module is no longer installed by default with Chromium if you use the Ubuntu PPA. As it is most probably only useful for web developers, I moved it to a dedicated package called **chromium-browser-inspector**. If you need it, just install it, otherwise, it saves you some download and disk space. This is similar to what I did with the **chromium-browser-l10n** package, useful for non en-US users.

---

### Post by wersdaluv on 2009-08-23
> **Giant Speck said:**
> Yeah, and at the same time, they removed those horrible looking Vista buttons.
I'm on the latest version at this time of writing, 4.0.203.0 (24081). The application shortcut feature is really cool but it doesn't work for me. Clicking "Create application shortcuts" from the menu asks me if I want to make a shortcut on the desktop but it doesn't make one even if I press "Create". 

Any idea how to make this work? What code would run a webapp into a Chromium app so I can make the shortcuts myself?

I find this better than Prism.

---

### Post by Regenweald on 2009-08-24
@ Ubulette, the FAQ needs to be updated. linux AND 64bit architectures are now well supported thanks to your hard work. :P
[http://dev.chromium.org/developers/faq](http://dev.chromium.org/developers/faq)

---

### Post by mybunche on 2009-08-24
After reading this article from Ars Technica
[http://arstechnica.com/open-source/news/2009/08/chromium-popularity-rising-on-ubuntu-gains-64-bit-support.ars]("http://arstechnica.com/open-source/news/2009/08/chromium-popularity-rising-on-ubuntu-gains-64-bit-support.ars")
I added the PPA for Ubuntu 8.04 and installed, started and imported my Firefox settings, enabled flash with --enable-plugins on startup command. 

And, WOW! This is fast, uses alot less CPU, accesses the hard drive way less, so far running with no problems.

A few hassles such as bookmarks still needs work, and quicktime plugin is not working. But I am very impressed so far.

---

### Post by bela42 on 2009-08-24
Hi,

I'm using 4.0.203.0 (24088) on Jaunty 64Bit. And it is really quite impressive, even flash works after adding --enable-plugins as stated above.

I just don't get why the Chromium window has no drop shadow, like all others. This is kind of annoying, I'd rather go with standard window decorations, if I could switch to those.

---

### Post by schmolch on 2009-08-24
Is it possible to configure a minimum font size in chromium.
I got some results when i googled this and it seems possible in windows.

---

### Post by schmolch on 2009-08-24
Is it possible to configure a minimum font size in chromium?
I got some results when i googled this and it seems possible in windows.

---

### Post by castrojo on 2009-08-24
> **wersdaluv said:**
> Any idea how to make this work? What code would run a webapp into a Chromium app so I can make the shortcuts myself? I find this better than Prism.

I don't think that works yet, you can modify or make your own shortcut like so on your panel on desktop, here's my gmail one:

chromium-browser --app=http://gmail.com

---

### Post by hetx on 2009-08-24
Ironically, mine, version 4.0.203.0 (24088), can't handle the image popup thing in this thread! Is that just me? I click a picture, get the dark area but no picture. I can scroll down out of the dark area.

---

### Post by Ric_NYC on 2009-08-24
> **hetx said:**
> Ironically, mine, version 4.0.203.0 (24088), can't handle the image popup thing in this thread! **Is that just me?** I click a picture, get the dark area but no picture. I can scroll down out of the dark area.


No.

---

### Post by quazi on 2009-08-24
Nah, Chromium isn't able to handle that yet.

---

### Post by sertse on 2009-08-24
No, it's actually a regression. Chromium was able to handle that in earlier builds.

---

### Post by darco on 2009-08-24
I normally dont run the browser from the command line so I dont know how long this error  has been around. Getting:
tk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

Running x64 Mint 7....running latest x64 build of Chromium

darco

---

### Post by wersdaluv on 2009-08-25
> **hetx said:**
> Ironically, mine, version 4.0.203.0 (24088), can't handle the image popup thing in this thread! Is that just me? I click a picture, get the dark area but no picture. I can scroll down out of the dark area.
Used to work here but it stopped working in the new build

---

### Post by simmeson on 2009-08-25
> **hetx said:**
> Ironically, mine, version 4.0.203.0 (24088), can't handle the image popup thing in this thread! Is that just me? I click a picture, get the dark area but no picture. I can scroll down out of the dark area.

Works fine here, I'm running 4.0.203.0 (24095).

---

### Post by wersdaluv on 2009-08-25
Big update a while ago! I now have sound on Flash videos and the download thingy now follows gtk! :D

---

### Post by northwestuntu on 2009-08-25
wow google chromium 4 64bit with flash is freaking fast!!! :P

im a diehard firefox user, but i must admit it's getting slow.  as soon they get some extensions i must have i might have to make chromium my default.

im still a little confused on the difference between chrome and chromium?

---

### Post by Ric_NYC on 2009-08-25
I'm using Chromium 80% of the time.

---

### Post by mybunche on 2009-08-26
Downloaded build 24230 today, and with the GTK theme I'm getting blue colour on the non-actives tabs. I have Hardy 8.04 brown default theme, and the blue don't look good. :(

That aside, flash is now working better.

---

### Post by wersdaluv on 2009-08-26
> **mybunche said:**
> Downloaded build 24230 today, and with the GTK theme I'm getting blue colour on the non-actives tabs. I have Hardy 8.04 brown default theme, and the blue don't look good. :(

That aside, flash is now working better.
Colors of inactive cabs look right on any of my gtk themes

---

### Post by mybunche on 2009-08-28
My blue colour tabs are now back to my beloved brown. :)
Running 4.0.204.0 Ubuntu build 24607, 28 August.

---

### Post by renkinjutsu on 2009-08-28
does chromium come with its own video player? why does the chromium daily build also download chromium ffmpeg codecs?

---

### Post by Tibuda on 2009-08-28
> **renkinjutsu said:**
> does chromium come with its own video player? why does the chromium daily build also download chromium ffmpeg codecs?

Maybe it has something to do with HTML5 video tag. Chromium/Chrome supports it?

---

### Post by ubulette on 2009-08-28
> **danielrmt said:**
> Maybe it has something to do with HTML5 video tag. Chromium/Chrome supports it?

indeed, it's for the HTML5 <audio> and <video> tags

---

### Post by Giant Speck on 2009-08-28
OH MY GOD!

Java works now!!!

---

### Post by Ric_NYC on 2009-08-28
> **Giant Speck said:**
> OH MY G*D!

Java works now!!!


Are you serious?

:)

Let me try.

---

### Post by Ric_NYC on 2009-08-28
Java is working... :)
There's another change that I noticed yesterday. Now there's the option of changing the language (Tools>Options>Under the Hood>Change fonts and Language settings>Languages).

---

### Post by Katalog on 2009-08-28
> **Giant Speck said:**
> OH MY GOD!

Java works now!!!

> **Ric_NYC said:**
> Are you serious?

:)

Let me try.

> **Ric_NYC said:**
> Java is working... :)
There's another change that I noticed yesterday. Now there's the option of changing the language (Tools>Options>Under the Hood>Change fonts and Language settings>Languages).

Hallelujah! Time to do my happy dance. :guitar:

---

### Post by Chemical Imbalance on 2009-08-28
> **katalog said:**
> hallelujah! Time to do my happy dance. :guitar:

W0oo H0oo0!  \\:D/

---

### Post by darco on 2009-08-29
and the Other Bookmark tab is full page now...sweet....that was annoying...
Now they need to work on the memory issues....mines running about 350mbs for7 tabs..ouch

Keep up the good work  :)

darco

---

### Post by Vrekk on 2009-08-29
> **darco said:**
> and the Other Bookmark tab is full page now...sweet....that was annoying...
Now they need to work on the memory issues....mines running about 350mbs for7 tabs..ouch

Keep up the good work  :)

darco

Same thing here, but other wise this is running flawlessly.

---

### Post by Colonel Kilkenny on 2009-08-29
> **darco said:**
> 
Now they need to work on the memory issues....mines running about 350mbs for7 tabs..ouch


The whole idea of memory is that applications should use it as much as possible. Chrome (or any other application) can use memory as much as it wants if it is also capable of releasing memory when other applications need more.

---

### Post by Katalog on 2009-08-29
> **darco said:**
> Now they need to work on the memory issues....mines running about 350mbs for7 tabs..ouch

> **Colonel Kilkenny said:**
> The whole idea of memory is that applications should use it as much as possible. Chrome (or any other application) can use memory as much as it wants if it is also capable of releasing memory when other applications need more.

Is it possible that the high memory consumption it tied to the whole "sandboxing" thing that Chromium does? I guess what I'm really trying to ask is if Chromium is using a tab, could it be that it is it behaving like it's running an entirely separate instance of the browser, thus the high memory usage? I admittedly know very little about the underpinnings of this browser (although I love using it!)

---

### Post by wersdaluv on 2009-08-29
I'm still waiting for the new Yahoo! Mail to work...

---

### Post by Vrekk on 2009-08-30
> **wersdaluv said:**
> I'm still waiting for the new Yahoo! Mail to work...

What do you mean, yahoo mail seems to work fine for me.....:confused:

---

### Post by Colonel Kilkenny on 2009-08-30
> **Katalog said:**
> Is it possible that the high memory consumption it tied to the whole "sandboxing" thing that Chromium does? I guess what I'm really trying to ask is if Chromium is using a tab, could it be that it is it behaving like it's running an entirely separate instance of the browser, thus the high memory usage? I admittedly know very little about the underpinnings of this browser (although I love using it!)

Probably it has something to do with "sandboxing" as well. Memory usage in browsers is always a trade off. Larger memory usage usually means that browsing is faster (larger caches etc.). Some browsers like Opera have very optimized cores because the same core is used on devices that have very limited resources and on devices that have big *** CPUs etc. 
So the browsers are just trying to find the balance where the memory usage, speed, etc. are optimal.

Chrome & Chromium both should have about:memory -page which tells more details about the real memory usage.

---

### Post by Vrekk on 2009-08-30
Well the fact that each tab is its own process (same with flash and other plugins) it dose use more memory, but it tends to make for a better overall browser.  Sometimes a tab will crash on my but because it was separate from the rest, my entire browser didn't.  Overal it is worth it

---

### Post by rifak on 2009-08-30
does anyone know when there will be some sort of bookmark sync option available?

---

### Post by wersdaluv on 2009-08-30
The new Yahoo! Mail?

---

### Post by Giant Speck on 2009-08-30
Yeah, it won't let me into the new Yahoo! Mail, either.  Not that I use Yahoo! Mail enough for it to matter, anyway.  :p

---

### Post by Kristofer Van Orton on 2009-08-30
I had no idea that there was even a ported version of Chrome...thanks! I'm downloading know haha

---

### Post by rifak on 2009-08-30
> **Kristofer Van Orton said:**
> I had no idea that there was even a ported version of Chrome...thanks! I'm downloading know haha

actually, i think Chrome is based off of chromium...am i right? correct me if im wrong

from here: [http://dev.chromium.org/Home](http://dev.chromium.org/Home)
on the left side, it reads "Google Chrome is built with open source code from Chromium"

---

### Post by Kristofer Van Orton on 2009-08-30
well theres no mistake thats definetley what it says there :P so maybe thats the case but I was looking for a version of chrome when i first got ubuntu and couldn't find one until now anyway

---

### Post by hanzomon4 on 2009-08-30
> **Giant Speck said:**
> OH MY GOD!

Java works now!!!

how and is it for 64bit?

---

### Post by darco on 2009-08-30
oops......the edit button in this forum still does not work w/Chromium.....

---

### Post by darco on 2009-08-30
If you are currently running FF and flash x64, chromium will pick up it automatically. Also the developer just stated the "--enable-plugins flag is no longer needed" but I still need it enabled for some reason. Flash x64 and Java work flawlessly on my x64 bit system

darco

---

### Post by mrgnash on 2009-08-30
I'm using the official Google Chrome branch and just wanted to know if the latest version of Chromium also features the regression where the window doesn't completely abide GTK theming?

---

### Post by Regenweald on 2009-08-30
> **Kristofer Van Orton said:**
> well theres no mistake thats definetley what it says there :P so maybe thats the case but I was looking for a version of chrome when i first got ubuntu and couldn't find one until now anyway

Rather than downloading constantly, for the newest daily updates, add this ppa with this command:

```

sudo add-apt-repository ppa:chromium-daily

```

> **darco said:**
> oops......the edit button in this forum still does not work w/Chromium.....

I've found that you can right click the edit link and open in a new tab, then just refresh the original page. This works for viewing images in the forum also.

---

### Post by orlox on 2009-08-30
> **Regenweald said:**
> Rather than downloading constantly, for the newest daily updates, add this ppa with this command:

```

sudo add-apt-repository ppa:chromium-daily

```



I've found that you can right click the edit link and open in a new tab, then just refresh the original page. This works for viewing images in the forum also.

add-apt-repository???? There is such a thing??? I always do it by manually creating a *.list file in /etc/apt/sources.list.d, saving the GPG key to a text file, and adding it with software sources T.T

does this command add the key to the repository??

---

### Post by Regenweald on 2009-08-30
> **orlox said:**
> add-apt-repository???? There is such a thing??? I always do it by manually creating a *.list file in /etc/apt/sources.list.d, saving the GPG key to a text file, and adding it with software sources T.T

does this command add the key to the repository??

It does indeed :) try it out, something new i saw over in Karmic testing and Discussion. easy peasy :)

Edit: original thread, [http://ubuntuforums.org/showthread.php?t=1213538](http://ubuntuforums.org/showthread.php?t=1213538)
Much thanks to Jacobmp92.

---

### Post by Chemical Imbalance on 2009-08-30
> **Regenweald said:**
> It does indeed :) try it out, something new i saw over in Karmic testing and Discussion. easy peasy :)

Edit: original thread, [http://ubuntuforums.org/showthread.php?t=1213538](http://ubuntuforums.org/showthread.php?t=1213538)
Much thanks to Jacobmp92.

Thanks for that.  I learned something too.

---

### Post by Regenweald on 2009-08-31
makes you just want to go trawling for new ppas doesn't it ? :) I know i did...

---

### Post by bluebyt on 2009-08-31
Please google add an option to when opening link in new tab, automatically switch to new tab. I know you can use shortcut ctrl-shift but this is not convenient.

 When I click on a link, it's because I want to see the page associated with that link.  I don't want to have to click on the link, then have to click on the new tab displaying that linked page.

By the way the menu on the website deviantart work now!

---

### Post by hanzomon4 on 2009-08-31
> **Regenweald said:**
> Rather than downloading constantly, for the newest daily updates, add this ppa with this command:

```

sudo add-apt-repository ppa:chromium-daily

```



I've found that you can right click the edit link and open in a new tab, then just refresh the original page. This works for viewing images in the forum also.

Sick!! Had no idea we had an add-apt-repository

---

### Post by MarcusW on 2009-09-01
The development really is lightningfast. :) Way better than firefox, and still alpha build.

---

### Post by 243kof on 2009-09-01
Am I the only one annoyed by the lack of middle-click scrolling on Chromium? Why wouldn't they implement such a basic feature? A bug has already been filed here: [http://code.google.com/p/chromium/issues/detail?id=17689]("http://code.google.com/p/chromium/issues/detail?id=17689"), but there  has hardly been any feedback. It's a shame really, because otherwise the browser is so cool! Without this I can't bother to make the plugins work.. :)

---

### Post by wersdaluv on 2009-09-01
> **243kof said:**
> Am I the only one annoyed by the lack of middle-click scrolling on Chromium? Why wouldn't they implement such a basic feature? A bug has already filed here: [http://code.google.com/p/chromium/issues/detail?id=17689]("http://code.google.com/p/chromium/issues/detail?id=17689"), but there  has hardly been any feedback. It's a shame really, because otherwise the browser is so cool! Without this I can't bother to make plugins work.. :)
Firefox doesn't have it as well, right? It's fine for me because I use middle clicking for opening new tabs anyway. I think, that's much more important.

---

### Post by Giant Speck on 2009-09-01
> **243kof said:**
> Am I the only one annoyed by the lack of middle-click scrolling on Chromium? Why wouldn't they implement such a basic feature? A bug has already been filed here: [http://code.google.com/p/chromium/issues/detail?id=17689](http://code.google.com/p/chromium/issues/detail?id=17689), but there  has hardly been any feedback. It's a shame really, because otherwise the browser is so cool! Without this I can't bother to make the plugins work.. :)

That's a feature that didn't even get implemented in the Windows version of Google Chrome until the beta builds of version 2.0.  Hopefully, though, we'll see it soon.  I miss that feature, too.

---

### Post by sertse on 2009-09-01
> **wersdaluv said:**
> Firefox doesn't have it as well, right?

Umm, in firefox it's in Preferences -> Advanced -> General -> "Use autoscrolling". Even when it's turned on, middle clicking on links still opens thme in new tabs.

I agree, it's a nice feature to have, reduces hand strain a bit. Epiphany webkit (with its extensions) had it, but it still had some bugs...

---

### Post by Mateo on 2009-09-05
I can't install it, because of incompatibilities with libasound2, libc6, and a few others.  Help?

---

### Post by Vrekk on 2009-09-08
Has anyone else noticed both Chromium AND Google Chrome?  I know chrome is based off of chromium but whats the main difference between the two? And i mean what would be noticed on my end, not just the fact that one has Google's name on it.

---

### Post by gymophett on 2009-09-08
> **Vrekk said:**
> Has anyone else noticed both Chromium AND Google Chrome?  I know chrome is based off of chromium but whats the main difference between the two? And i mean what would be noticed on my end, not just the fact that one has Google's name on it.

Mostly nothing. Chromium is just a project to make Google Chrome for Linux based on the Chrome code. But Google is making a Chrome for Linux also.
So I have no idea?

---

### Post by OutOfReach on 2009-09-08
> **Vrekk said:**
> Has anyone else noticed both Chromium AND Google Chrome?  I know chrome is based off of chromium but whats the main difference between the two? And i mean what would be noticed on my end, not just the fact that **one has Google's name on it.**

you just answered your own question :)
that's pretty much the only difference.
Basically, Google Chrome *is* Chromium, Chromium is the working product and Google Chrome is the final product, makes sense?

---

### Post by Giant Speck on 2009-09-08
> **Vrekk said:**
> Has anyone else noticed both Chromium AND Google Chrome?  I know chrome is based off of chromium but whats the main difference between the two? And i mean what would be noticed on my end, not just the fact that one has Google's name on it.

Chromium is the open-source project from which Google Chrome is based.  The only thing Google adds to Google Chrome that Chromium itself doesn't already have is Google's branding.

---

### Post by Vrekk on 2009-09-08
> **Giant Speck said:**
> Chromium is the open-source project from which Google Chrome is based.  The only thing Google adds to Google Chrome that Chromium itself doesn't already have is Google's branding.

Idk google has to add SOMETHING.  I just ran both against the peacekeeper brower benchmarker and Chromium 4.0.207.0 scored a 1535 while Google Chrome 4.0.206.0 scored a 2002.... Ill test it again on the next releases to see if they come closer or something.

BTW OFF TOPIC.
when did that report abuse thing get under the profile stuff?
<-------

---

### Post by Giant Speck on 2009-09-08
> **Vrekk said:**
> BTW OFF TOPIC.
when did that report abuse thing get under the profile stuff?
<-------

That's always been there; they just changed the icon is all.  The new icon has been there for a couple days now.

---

### Post by dannew on 2009-09-08
> **Vrekk said:**
> Has anyone else noticed both Chromium AND Google Chrome?  I know chrome is based off of chromium but whats the main difference between the two? And i mean what would be noticed on my end, not just the fact that one has Google's name on it.

The difference between Chromium and Chrome is explained here:
[http://blog.chromium.org/2008/10/google-chrome-chromium-and-google.html]("http://blog.chromium.org/2008/10/google-chrome-chromium-and-google.html")

---

### Post by purgatori on 2009-09-08
I've been trying to think why I just can't seem to stick with using Chrome as my default browser, and it occurs to me that without autoscroll OR vi-like keybindings (a-la Vimperator, or Uzbl), the navigation is pretty horrible. I just get a little sick of click click click, drag, click click click.

---

### Post by binbash on 2009-09-08
> **dannew said:**
> The difference between Chromium and Chrome is explained here:
[http://blog.chromium.org/2008/10/google-chrome-chromium-and-google.html]("http://blog.chromium.org/2008/10/google-chrome-chromium-and-google.html")

Thanks for the link!

---

### Post by ubulette on 2009-09-08
> **Vrekk said:**
> Idk google has to add SOMETHING.  I just ran both against the peacekeeper brower benchmarker and Chromium 4.0.207.0 scored a 1535 while Google Chrome 4.0.206.0 scored a 2002.... Ill test it again on the next releases to see if they come closer or something

when you say something like that, could you please give enough information so that we can reproduce. I mean, which build of Chromium was that? the PPA or the upstream dev builds? which distro? (karmic, jaunty, hardy..?). with or without plugins and extensions..

EDIT: that and if it's 32 or 64bits. Also, try to use the same version.

---

### Post by matthew.ball on 2009-09-14
Extensions are available.

I have just enabled ad-block myself.
[http://penguininside.blogspot.com/2009/08/how-to-setup-chromium-google-chrome.html](http://penguininside.blogspot.com/2009/08/how-to-setup-chromium-google-chrome.html), so yeah, to everyone who was interested.

---

### Post by wersdaluv on 2009-09-14
> **matthew.ball said:**
> Extensions are available.

I have just enabled ad-block myself.
[http://penguininside.blogspot.com/2009/08/how-to-setup-chromium-google-chrome.html](http://penguininside.blogspot.com/2009/08/how-to-setup-chromium-google-chrome.html), so yeah, to everyone who was interested.
Yeahehehh! Cool! :D 

Thanks!!!

---

### Post by wersdaluv on 2009-09-14
> **matthew.ball said:**
> Extensions are available.

I have just enabled ad-block myself.
[http://penguininside.blogspot.com/2009/08/how-to-setup-chromium-google-chrome.html](http://penguininside.blogspot.com/2009/08/how-to-setup-chromium-google-chrome.html), so yeah, to everyone who was interested.
Yeahehehh! Cool! :D 

Thanks!!!

---

### Post by johnjust on 2009-09-14
I'm not sure if this is related to the browser or not, but a couple seconds after I opened it for the first time, GNOME completely crashed back to the login screen.

What log would have the info I should be looking at?

---

### Post by wersdaluv on 2009-09-14
> **johnjust said:**
> I'm not sure if this is related to the browser or not, but a couple seconds after I opened it for the first time, GNOME completely crashed back to the login screen.

What log would have the info I should be looking at?
Doesn't seem to be related to the browser. Run chromium-browser on the terminal and see if there are relevant error messages. hmmm

---

### Post by darco on 2009-09-14
Hmm....adsweep has always worked......

Anyways, havent received a new build since the 8th? Ubulette, whats going on?

darco

---

### Post by rifak on 2009-09-14
does anyone else not have scroll arrows on the top and bottom of the scrollbar of the chromium window? this seems like an odd thing to not include...?

---

### Post by JerecDrak2 on 2009-09-14
> **darco said:**
> Hmm....adsweep has always worked......

Anyways, havent received a new build since the 8th? Ubulette, whats going on?

darco

I think this is perhaps because from the 9th onwards extensions have been switched on by default, and the launchpad ppa has been experiencing build issues since then. You can check on the build status [here]("https://launchpad.net/%7Echromium-daily/+archive/ppa")

At the time of writing packages were being built, hopefully they will be successful this time so we can catch up!

Also switham, I don't have arrows at the top or bottom of my scrollbars either.

---

### Post by wersdaluv on 2009-09-14
> **switham said:**
> does anyone else not have scroll arrows on the top and bottom of the scrollbar of the chromium window? this seems like an odd thing to not include...?
We don't have the "steppers" yet and it's not intended to be that way. AFAIK, they're still working hard to integrate chromium to GTK+ :) Let's just wait.

---

### Post by rifak on 2009-09-14
> **wersdaluv said:**
> We don't have the "steppers" yet and it's not intended to be that way. AFAIK, they're still working hard to integrate chromium to GTK+ :) Let's just wait.

ahhh gotchya. thanks

---

### Post by darco on 2009-09-14
> **JerecDrak2 said:**
> I think this is perhaps because from the 9th onwards extensions have been switched on by default, and the launchpad ppa has been experiencing build issues since then. You can check on the build status [here]("https://launchpad.net/%7Echromium-daily/+archive/ppa")

At the time of writing packages were being built, hopefully they will be successful this time so we can catch up!

Also switham, I don't have arrows at the top or bottom of my scrollbars either.

Ya, the day I mention it, is the day an update finally goes thru!.....
Yes the PPA is where I normally view an update building.....
thxs

---

### Post by ubulette on 2009-09-15
> **darco said:**
> Ya, the day I mention it, is the day an update finally goes thru!.....
Yes the PPA is where I normally view an update building.....
thxs

It's a daily PPA, meaning it's *automatically* populated by a bot (that I wrote). Dailies may break at any time, until someone (a human) fixes them. There's no guaranty that fixes arrive promptly, it's maintained in best effort mode (by only 1 person in case of chromium, me).
Some fixes are trivial, some require a lot of efforts. The last few days were red because of several regressions in a backend tool. All but one have been sorted out. The last one (impacting only hardy) has been identified. 

For more information about daily builds, see [http://castrojo.wordpress.com/2009/08/21/making-daily-builds/](http://castrojo.wordpress.com/2009/08/21/making-daily-builds/) and [http://www.asoftsite.org/s9y/archives/164-ubuntu-network-manager-team-offers-daily-builds-for-trunk-aka-0.8-now.html](http://www.asoftsite.org/s9y/archives/164-ubuntu-network-manager-team-offers-daily-builds-for-trunk-aka-0.8-now.html)

---

### Post by johnjust on 2009-09-15
> **wersdaluv said:**
> Doesn't seem to be related to the browser. Run chromium-browser on the terminal and see if there are relevant error messages. hmmm

Thanks for the reply, After my GNOME crashed again while playing WoW yesterday, I chalked it up to my Nvidia Beta driver, which I've since upgraded to the newest stable release.  I definitely thought the browser causing that type of crash was a little weird, but everything seems fine now.

---

### Post by hoppipolla on 2009-09-15
No complaints here ^_^

---

### Post by rifak on 2009-09-17
the most recent update gets rid of the need for the --enable-plugins flag. im might be speaking too soon, but im pretty sure no flags are needed any longer. im using extensions (AdSweep, Xmarks), plugins, and flash without any flags. its coming along very smoothly. i am so happy with this browser

---

### Post by Ric_NYC on 2009-09-17
Is printing working now?

---

### Post by Spaced on 2009-09-23
Hi everybody,

I am a "subscriber" of the Chromium daily updates and I must say I am generally very satisfied with this browser. Yet, the problem that keeps me away from switching completely to Chromium is the impossibility to load my Yahoo! Mail account in the "New" interface. When I try to access, Chromium simply tells me that it can't load the "New Yahoo! Mail" and that I have to load the "classical" interface. No way of making it work.
I haven't read very much about this issue, but I guess it should happen to every Yahoo! Mail user. Or not?

---

### Post by wersdaluv on 2009-09-23
> **Spaced said:**
> Hi everybody,

I am a "subscriber" of the Chromium daily updates and I must say I am generally very satisfied with this browser. Yet, the problem that keeps me away from switching completely to Chromium is the impossibility to load my Yahoo! Mail account in the "New" interface. When I try to access, Chromium simply tells me that it can't load the "New Yahoo! Mail" and that I have to load the "classical" interface. No way of making it work.
I haven't read very much about this issue, but I guess it should happen to every Yahoo! Mail user. Or not?
Same issue here :)

---

### Post by Vrekk on 2009-09-23
I think the yahoo thing may be more of a problem on their end

OH and look!  Html5 video tags!

[http://www.double.co.nz/video_test/](http://www.double.co.nz/video_test/)

---

### Post by wersdaluv on 2009-09-23
Yahoo! Mail works very well on Chrome on windows. It must be a user agent thing. Hmmm

---

### Post by missmoondog on 2009-09-26
read most of these pages and not seeing where anyone is saying how to start chrome in incognito mode all the time.

i know how to do that in windows.

thank you

---

### Post by rifak on 2009-09-26
use this command:
```
chromium-browser -incognito
```

---

### Post by missmoondog on 2009-09-28
not exactly what i was looking for, but works.

here's what i found that is more along the lines of what i'm looking for. found in another search. i don't have gnome or the edit menu, on right clicking, but i think that's available through synaptic, right?

I'm not sure how to change settings in Xubuntu, but if it's like Gnome:
If the icon for chromium is on a bar or the desktop you can do it in the same way as Windows, right click, and add --incognito after chromium-browser on the command line. To edit it in the Gnome Applications menu, right click on Applications, click Edit Menus, scroll to Internet -> Chromium, click Properties and do the same as above.


thanks

---

### Post by sertse on 2009-10-09
Personally, for a while now, I'm getting freezes and hangs when I visit sites with flash. The page may sometimes half load then it happens. Disabling makes it go right though. Maybe it's just me ...

32bit

---

### Post by Giant Speck on 2009-10-09
I love the application shortcuts feature.  I use it for PandoraFM.  Coincidentally, PandoraFM finally works on Chrome now.

---

### Post by inaninck on 2010-01-24
> **Katalog said:**
> Hallelujah! Time to do my happy dance. :guitar:

Not for me...

This page
[http://javatester.org/version.html](http://javatester.org/version.html)

doesn't show what it should when Java works.

Firefox = OK

What can I do?:confused:

---

### Post by k64 on 2010-01-24
Actually, I personally like Chromium OS 0.4.22.8

---

### Post by AllRadioisDead on 2010-01-24
> **k64 said:**
> Actually, I personally like Chromium OS 0.4.22.8
What does that have to do with anything?
It sounds more like you're showing off that you use chromium OS.

---

### Post by dannew on 2010-01-24
> **inaninck said:**
> Not for me...

This page
[http://javatester.org/version.html](http://javatester.org/version.html)

doesn't show what it should when Java works.

Firefox = OK

What can I do?:confused:

Maybe this helps:
[http://www.google.com/support/forum/p/Chrome/thread?tid=3dfa247aa1eb956c&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=3dfa247aa1eb956c&hl=en)

---

