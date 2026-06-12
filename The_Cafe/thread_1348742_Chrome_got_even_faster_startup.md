---
title: "Chrome got even faster startup?"
date: 2009-12-07
forum: The Cafe
---

### Post by froggyswamp on 2009-12-07
I noticed for the last few days that Chrome takes like half a second to perform a **cold** startup, not to mention a warm one. Is it just me experiencing these ridiculously quick startup times?

---

### Post by NoaHall on 2009-12-07
I have almost instant start up. Do you have preload installed?

---

### Post by pwnst*r on 2009-12-07
> **froggyswamp said:**
> I noticed for the last few days that Chrome takes like half a second to perform a **cold** startup, not to mention a warm one. Is it just me experiencing these ridiculously quick startup times?

that's about right for me on *nix and windows.

---

### Post by froggyswamp on 2009-12-07
I mean for me a cold **startup** it used to take like a second and a half (several days ago), now it's almost instant, I wondered if somebody noticed it. Not that it matters a lot, I'm just impressed that it does a cold startup faster than gedit haha, that's ridiculous imho

---

### Post by gnomeuser on 2009-12-07
Those google folk, they know how to measure and improve their code.

---

### Post by speedwell68 on 2009-12-07
Do people actually sit there with a stopwatch timing how long it takes their browser to load?

---

### Post by froggyswamp on 2009-12-07
No, some people like me don't sit with a stopwatch, unfortunately I don't got one.

---

### Post by Sand &amp; Mercury on 2009-12-07
> **speedwell68 said:**
> Do people actually sit there with a stopwatch timing how long it takes their browser to load?
Some people are weird and actually do, but in this case you'd just notice it anyway.

---

### Post by Dark_Stang on 2009-12-07
I'm confused. Are we talking about the web browser or the operating system here?

---

### Post by froggyswamp on 2009-12-07
Web browser :)

---

### Post by murderslastcrow on 2009-12-07
No. It's disgustingly fast. Expect it to get better somehow.

---

### Post by murderslastcrow on 2009-12-07
P.S. If you have Linux, you have a stopwatch.

---

### Post by wulfgang on 2009-12-07
> **froggyswamp said:**
> Web browser :)
I'm sure the os will probably be under 10 seconds because all it is, is a web browser and a linux kernel.

---

### Post by RATM_Owns on 2009-12-07
> **speedwell68 said:**
> Do people actually sit there with a stopwatch timing how long it takes their browser to load?
We're nerds. It's all we have left.

For me, Chromium has nearly instant startup (using the latest Chromium build via the chromium-browser-bin package in Arch's AUR).

---

### Post by PurposeOfReason on 2009-12-07
> **wulfgang said:**
> I'm sure the os will probably be under 10 seconds because all it is, is a web browser and a linux kernel.
It's more around 2 if I remember right. I wish I could use chromium but I need vimperator.

---

### Post by earthpigg on 2009-12-07
it starts and runs fast as hell, even on my netbook.

it isn't as full featured as ff just yet, so ff is still my primary...


but i dont care about super fancy features on my netbook, what i do care about is using faster software to compensate for the weak CPU.

chromium thus fits nicely into that niche for me.

---

### Post by wavery on 2009-12-07
Chrome comes in Linux flavor?

---

### Post by Matthewthegreat on 2009-12-07
What a stopwatch? Type this into the terminal...

```
sudo apt-get install stopwatch
```

---

### Post by AllRadioisDead on 2009-12-07
You know what? This is getting ridiculous. Rightly put, it's disgustingly fast, and I think we as a community need to do something about it. Chromium is far too fast and needs to be slowed down, I think I'm going to write up a letter to Google complaining about the progress being made.

---

### Post by the yawner on 2009-12-07
Eh, just add a sleep command on your launcher. Problem solved.

---

### Post by PhoHammer on 2009-12-07
> **wavery said:**
> Chrome comes in Linux flavor?

Yes! You need it.

---

### Post by Ric_NYC on 2009-12-07
Chromium showing some strange black squares when I scroll the webpages after the last update.

Anyone having the same issue?



BTW: Chromium is my default browser. ;)

---

### Post by murderslastcrow on 2009-12-07
Hey, Ric- the update before this last one started causing this problem for me, and the new update today didn't fix it. It's a serious issue, not sure if it's been reported yet. Interestingly, the very same version of Chromium on my parents' PC, also using Intel graphics, doesn't have any issues.

It seems to happen a lot more in webpages that need to render flash. Hopefully this is fixed soon (I'm using the daily Chromium PPA for Karmic).

---

### Post by kemsiro on 2009-12-07
i got the same problem with rendering issue.
T___T

---

### Post by murderslastcrow on 2009-12-07
Anyone know if there's a bug report for this yet? I might make it myself in a few if not.

---

### Post by doorknob60 on 2009-12-07
My cold startup is about 1-2 seconds (still very vast), but after that it's very fast. I still stick with Firefox, one of the main reasons is there's no way to make Chromium look good with my GTK theme :P And all the addons I use are definately a nice bonus, but it's not a dealbreaker. Firefox's speed to me is still very acceptable.

---

### Post by Ric_NYC on 2009-12-07
> **murderslastcrow said:**
> Hey, Ric- the update before this last one started causing this problem for me, and the new update today didn't fix it. It's a serious issue, not sure if it's been reported yet. Interestingly, the very same version of Chromium on my parents' PC, also using Intel graphics, doesn't have any issues.

It seems to happen a lot more in webpages that need to render flash. Hopefully this is fixed soon (I'm using the daily Chromium PPA for Karmic).

> **kemsiro said:**
> i got the same problem with rendering issue.
T___T

> **murderslastcrow said:**
> Anyone know if there's a bug report for this yet? I might make it myself in a few if not.

I hope that's fixed ASAP.

---

### Post by steveneddy on 2009-12-07
I've stopped using FF 3.5 and started using Chrome as my default browser.

---

### Post by murderslastcrow on 2009-12-08
Good news you guys. The graphics corruption bug's been reported here. [http://code.google.com/p/chromium/issues/detail?id=29536](http://code.google.com/p/chromium/issues/detail?id=29536)

It's been solved in the recent SVN version, and will be packaged automatically soon. Look here for further detail. [http://code.google.com/p/chromium/issues/detail?id=29504](http://code.google.com/p/chromium/issues/detail?id=29504)

Do an update and it should be fixed.

---

### Post by Dobbie03 on 2009-12-08
Anyone know how to get the official Chrome not the Chromium?

---

### Post by murderslastcrow on 2009-12-08
Chromium is basically as official as it gets at the moment. I thought I saw a link on Google's site to the Ubuntu PPA at one point.

---

### Post by Knowle on 2009-12-08
> **MattDobson said:**
> Anyone know how to get the official Chrome not the Chromium?You can get it here.
[http://dev.chromium.org/getting-involved/dev-channel](http://dev.chromium.org/getting-involved/dev-channel)
[http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb](http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb) (dev 32 bit)
[http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_amd64_deb](http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_amd64_deb) (dev 64 bit)

---

### Post by treesurf on 2009-12-08
EDIT: sorry incorrect info, post retracted

---

### Post by madnessjack on 2009-12-08
> **speedwell68 said:**
> Do people actually sit there with a stopwatch timing how long it takes their browser to load?
No, but I sit there with a calendar and time Firefox sometimes :P

---

### Post by kemsiro on 2009-12-08
switch back to Firefox temporarily til Chrome provides an update

---

### Post by matthew.ball on 2009-12-08
> **murderslastcrow said:**
> Chromium is basically as official as it gets at the moment. I thought I saw a link on Google's site to the Ubuntu PPA at one point.
I had Chrome on Linux under Jaunty. But having installed Karmic since, I lost it - not entirely sure where I got it from (maybe Ubuntu Tweak?).

It was exactly the same as Chromium (minus daily-build), just had the google branding.

---

### Post by madnessjack on 2009-12-08
Just googled "chrome dev"

[http://www.chromium.org/getting-involved/dev-channel](http://www.chromium.org/getting-involved/dev-channel)

it's the google version btw

---

### Post by kemsiro on 2009-12-08
rendering issue fixed with the latest update :x

---

### Post by mkvnmtr on 2009-12-08
The rendering problem is not fixed on my unit. It has changed from random black boxes to other strange boxes. With a daily build it will get worked out soon.

---

### Post by kemsiro on 2009-12-08
really?

i updated to 4.0.267.0 (Ubuntu build 34029) and it's working flawlessly now.

---

### Post by Grifulkin on 2009-12-08
This might be a silly question but does anyone use Iron instead of Chromium or Chrome?

---

### Post by AllRadioisDead on 2009-12-08
> **Grifulkin said:**
> This might be a silly question but does anyone use Iron instead of Chromium or Chrome?
I'm actually using steel right now.

---

### Post by murderslastcrow on 2009-12-08
I was gonna' try Iron a while back, but I just don't find it necessary at the moment. Might try it in the future if I get a little scared of the scientists at Google.

---

### Post by AllRadioisDead on 2009-12-08
Woah, iron is actually a browser? I thought we were just trolling.
Looks cool!

---

### Post by madnessjack on 2009-12-09
Iron put adverts on the home page. Bit dubious isn't it?

---

### Post by Grifulkin on 2009-12-10
> **ihermit said:**
> Woah, iron is actually a browser? I thought we were just trolling.
Looks cool!

Very nice, that's quite funny actually.

---

