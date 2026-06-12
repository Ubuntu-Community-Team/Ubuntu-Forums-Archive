---
title: "[Solved] Firefox is so slow, is it becoming irrelevant"
date: 2016-08-16
forum: Ubuntu, Linux and OS Chat
---

### Post by kansasnoob on 2016-08-16
******Edit: It appears that a bad KVM switch may have been the culprit!**

I'm not easily given to flaming wars, and this is not meant as bashing Firefox, but over the past few weeks with 16.04.1 and 14.04.5 iso and upgrade testing I've been running Firefox with totally fresh profiles (so it's not due to cruft in an old profile) and when I go back to my daily driver (based on 14.04.1) I find both Chrome and Opera are downright snappy in comparison. This is all on the same hardware, and I did try Firefox on my daily driver with a fresh profile to be sure it wasn't a Xenial specific issue.

I had mostly switched from Firefox to Chrome and/or Opera anyway just for aesthetics sake (yes, Firefox has tried to become a near clone) but noticing how much slower Firefox has become is worrisome. It makes me wonder if they've just given up. I wouldn't have noticed this but since Firefox is the default browser when I'd file a bug using ubuntu-bug pkgname apport naturally opens Firefox as part of the process. So, is this just the sad state of affairs surrounding Firefox in general?

---

### Post by mastablasta on 2016-08-17
how did you measure "slowness" ?

i have plenty add ons in Firefox (some are now as default it seems). it doesn't load any slower than Chrome. maybe a bit longer. but once it is loaded i do not get slow page loading or anything like that. this is a very old profile. and i am not sure that profile alone should matter much.

[SIZE=2]https://en.wikipedia.org/wiki/Browser_speed_test
[/SIZE]

---

### Post by kansasnoob on 2016-08-17
It was most noticeable when typing into any web form. I first noticed it typing into Launchpad forms in the process of filing or editing bug reports. That made me think it was a Launchpad problem which led to me paying closer attention. When I'd  boot into my daily driver and open the same bug reports using Chrome or Opera response to my typing was basically instantaneous.

I had a mild stroke about 2 1/2 years ago that left my left hand slow and clumsy. That results in a ridiculously high rate of typos so I have to watch closely and "correct as I go". Using Firefox I'd frequently find my typing 20 to 30 characters ahead of what appeared on-screen, and I'm NOT a fast typist. I'd not seen that happen before so I began to pay attention and make comparisons.

But I most recently noticed it typing product reviews on Amazon and Ebay. Of course I wouldn't have even been trying to use Firefox for those tasks if my curiosity had not been peaked during iso/upgarde testing. I've read mixed reviews where some report sluggishness, but with no benchmarks to back up the claim. Where I have found reviews with benchmarks the results are almost indistinguishable.

The obvious solution is to just use what works best for me, something I constantly tell others when talking about default apps. For instance some prefer Totem, while others prefer VLC, and still others prefer some version of Mplayer. I had already made the switch to Chrome and only recently began using Opera out of curiosity for the first time in a few years.

I was just curious if others have noticed similar performance issues with Firefox.

---

### Post by mastablasta on 2016-08-17
i haven't noticed any slow response in forms. only long time to start Firefox. and we mostly have old PCs.

it could be graphics driver issue, the way it renders etc. yes, by all means use what works best for you.

---

### Post by poorguy on 2016-08-18
Give Slimjet a try.

[http://www.slimjet.com/](http://www.slimjet.com/)

After you install it go into settings and untick force adobe flash player on youtube.

---

### Post by SeijiSensei on 2016-08-18
I've had the experience occasionally of slow input speeds.  Usually they go away once I restart Firefox.

I also use the Lazarus add-on which may contribute some to this issue.

---

### Post by qamelian on 2016-08-18
I haven't noticed any slowness in Firefox here. If anything, I find it feels much faster than Chrome on my laptop.

---

### Post by kansasnoob on 2016-08-18
> **poorguy said:**
> Give Slimjet a try.

[http://www.slimjet.com/](http://www.slimjet.com/)

After you install it go into settings and untick force adobe flash player on youtube.

Never heard of that one. I'll give it a spin some time next week.

---

### Post by lisati on 2016-08-18
As a long-time user of FireFox, both on Windows and Ubuntu, I have noticed the occasional bout of sluggishness, and have wondered if what I perceive as increasing bloat on web pages is a contributing factor.

---

### Post by kansasnoob on 2016-08-18
I ran across something just moments ago that may have some effect on this. I was gone to the hospital for testing this AM and upon returning I started my puter, looked at all of my important stuff (like how slowly Amazon is processing my orders lately). It wasn't until I tried to reply to a PM that I found ***my keyboard was totally unresponsive and I was using Opera!*** It turned out to be my 10+ year old KVM switch!

I suppose it's possible that there was an odd coincidence where it just happened to occur when I'd use Firefox, but disappear when I'd switch browsers???? It seems like a very odd coincidence, but maybe Firefox is somehow more sensitive????? I think most (or all) modern browsers have some in-built protection against keyloggers so maybe Firefox's protection sensed a weak signal??????

I'll watch this for the next several days and see what happens with the KVM switch completely removed. Now it's time to order a new KVM switch :cry:

Why, why-oh-why, do things seem to break down all at once? The past six weeks have been insane!!!!! First the limited slip differential in my old Chevy gave up the ghost, then it was the clothes dryer, next a bearing in one of the blade hubs on my riding mower froze up and wrecked the whole hub & spindle assembly. Add the leaf blower and the shop vacuum to the list, and now this ](*,)

If I drank I'd tie on a good one :tongue:

---

### Post by mikodo on 2016-08-18
> **kansasnoob said:**
>  - Snippet from read post -

If I drank I'd tie on a good one 


I sympathize with you. Funny, or well, maybe not haha funny. Today, I was slogging through a 10- 11 hour task (again) to provide the financial details for court for our divorce. At one point I felt the same and briefly considered it. Only ten minutes ago I was giving thanks that I didn't give in.

I am too tired to read any more so I am not sure if you possibly solved the problem of FF being slow but, since I am here, I have many things I turn off in FF to make it quicker. I have kept a list of things I have done. Almost all are things people here, have recommended. PM me if you want to see it. Not today though. :)

Regards.

---

### Post by mastablasta on 2016-08-19
> **lisati said:**
> As a long-time user of FireFox, both on Windows and Ubuntu, I have noticed the occasional bout of sluggishness, and have wondered if what I perceive as increasing bloat on web pages is a contributing factor.

i have a 12 year old PC i upgraded a bit, and just today i was doing some work for for local society. i use gmail for my personal e-mail and the society i volunteer for also uses google apps (so gmail as well). the difference is that my gmail has fancy planets background, while i left the society's gmail blank (so i do not mistake which address i am sending from). anyway the blank one was so much more responsive in same firefox session different window. so yes it would seem there is plenty bloat arorund on the web these days. 

no script and similar add ons turn it off but then i guess it needs to process it first, so again sucking up the CPU.

or maybe i just need a new PC. :)

---

### Post by lisati on 2016-08-19
> **kansasnoob said:**
> 
If I drank I'd tie on a good one :tongue:

:lolflag: Frustrating, isn't it?

---

### Post by robbie 348 on 2016-08-19
I've noticed it's very slow to load my home page, from clicking the firefox icon to finished loading it takes 35 seconds, but from then on it's fine. This is on fairly new hardware and 8gb ram. 
It also doesn't seem to matter what I set as homepage either. When I use chrome, it is ready to go in 8 seconds.

---

### Post by ChuangTzu on 2016-08-19
try using the following addons to speed up Firefox:  NoScript and Ublock Origin

---

### Post by kurt18947 on 2016-08-19
> **kansasnoob said:**
> Never heard of that one. I'll give it a spin some time next week.

I have Slimjet & Vivaldi on different machines. No Google snoopware if I can avoid it. The only Firefox slowness I sometimes see if launching the program. Once open I see no issues that can't be laid to add-ons. If I have an issue with a web site and I trust it, I do Help -> Restart with Add-Ons Disabled. I believe Mozilla is rewriting significant parts of Firefox like replacing Gecko so they may not be paying a great deal of attention to noncritical problems with the existing browser.

---

### Post by pauljw on 2016-08-19
I came to Firefox from Netscape, so I've been using it since the beginning and have yet to find anything to compare.  Sometimes I've had to use it on inferior hardware and there was a bit of performance hit.  Mostly, as others have said, it's slow to load up initially, but once it's loaded it runs just fine.  It's long list of plugins is both a blessing and a curse.  Some of them will misbehave, some are quite bloated, while many have become indispensable like no-script, bluhell firewall and https everywhere.

I may not be the best person to answer regarding slowness as until just two years ago we were sharing a dialup connection amoung 3-5 devices, so patience was required.  :)

---

### Post by robbie 348 on 2016-08-20
> **ChuangTzu said:**
> try using the following addons to speed up Firefox:  NoScript and Ublock Origin
I do

---

### Post by ChuangTzu on 2016-08-20
another option is to use Seamonkey, you can download it from [http://www.seamonkey-project.org/](http://www.seamonkey-project.org/) , and run inside your home folder.  Or if you use Ubuntu Mate or installed Mate software boutique (Mate welcome) then you can install it from there and it will add seamonkey as a repo...  Not completely necessary though since Seamonkey includes a self updater.

---

### Post by kansasnoob on 2016-08-20
I'm convinced at this point that a flaky KVM switch was the root of the problem so my original assumption of this being a Firefox issue was wrong. Therefore I'm marking this solved.

---

### Post by pauljw on 2016-08-20
Glad you found the problem, and thanks for letting us know what you found.

---

