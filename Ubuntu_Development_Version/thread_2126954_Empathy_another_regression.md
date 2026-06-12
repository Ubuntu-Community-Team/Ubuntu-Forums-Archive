---
title: "Empathy another regression?"
date: 2013-03-18
forum: Ubuntu Development Version
---

### Post by Budovi on 2013-03-18
Hi all,

after today's update to 3.6.4-ubuntu1 I have no online contacts listed. It says "No online contacts", which is nonsense, or it shows blank window. I appear online and are able to retrieve messages.

So bugs are not fixed in this release, and as "big plus" Empathy is now super crappy useless app. :( 

I'm without working Empathy for approx. 2 months and it is making me mad, everything was working before (maybe I should consider downgrade, but I don't feel like I want to spent night with resolving dependencies). So it would be nice if you can suggest some replacement... (In the past, I used Pidgin but it is not really what I'm searching for. Something better would be great.)

Thanks for all your help.

P.S.: I have nothing against debugging empathy, but there is no progress in critical ("high") empathy bugs for a long time and I lost my patience now.

---

### Post by screaminj3sus on 2013-03-18
Empathy/UOA has been almost completely broken for me pretty much the whole cycle, basically only the google/facebook/windows live plugins work and the other ones are b0rked: [https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/1116449](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/1116449)

Wouldn't bother me if pidgin wasn't also totally broken in raring: [https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/1109251](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/1109251)


pretty ridiculous how all of this stuff is ignored, I thought 13.04 was supposed to be about quality? For me its mostly been introducing regressions from the already buggy 12.10...


EDIT: yeah its regressed even further for me now like in your post, now even google/facebook don't work. on a fresh updated 13.04 install they instantly fail to connect after creating accounts.

I don't have any issues with empathy or pidgin in other gnome 3.6 distro, its only ubuntu that keeps massively breaking them

---

### Post by balloons on 2013-03-20
> **screaminj3sus said:**
> Empathy/UOA has been almost completely broken for me pretty much the whole cycle, basically only the google/facebook/windows live plugins work and the other ones are b0rked: [https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/1116449](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/1116449)

Wouldn't bother me if pidgin wasn't also totally broken in raring: [https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/1109251](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/1109251)


pretty ridiculous how all of this stuff is ignored, I thought 13.04 was supposed to be about quality? For me its mostly been introducing regressions from the already buggy 12.10...


EDIT: yeah its regressed even further for me now like in your post, now even google/facebook don't work. on a fresh updated 13.04 install they instantly fail to connect after creating accounts.

I don't have any issues with empathy or pidgin in other gnome 3.6 distro, its only ubuntu that keeps massively breaking them

This is really weird -- everything works great for me in raring -- in fact, there was a little weirdness in 12.10 and most of 13.04 that went away within the last few weeks before feature freeze when the new stuff landed for online accounts. What's giving you trouble exactly? Link some bugs :-)

---

### Post by rrnbtter on 2013-03-20
Greetings,

> **guitara said:**
> This is really weird -- everything works great for me in raring -- in fact, there was a little weirdness in 12.10 and most of 13.04 that went away within the last few weeks before feature freeze when the new stuff landed for online accounts. What's giving you trouble exactly? Link some bugs :-)

Also interesting for me! When the indicator for Gajim bit the dirt I switched to Empathy as a fall back and it has worked just fine. I run the RC kernels and not the repo versions. Don't know if that has anything to do with it. Currently on 3.9RC3.  While we are on the communications subject you may be interested that Claws-mail now has fully integrated Indicators with the Unity Panel and also the Launcher. I am very happy to see this fixed and it is has been done in a really refined way. Big thanks to whoever is responsible.

---

### Post by screaminj3sus on 2013-03-20
> **guitara said:**
> This is really weird -- everything works great for me in raring -- in fact, there was a little weirdness in 12.10 and most of 13.04 that went away within the last few weeks before feature freeze when the new stuff landed for online accounts. What's giving you trouble exactly? Link some bugs :-)

Its worth noting that I reproduced all of these issues on *multiple* totally clean raring installs:


The two pidgin bugs appear related, and I suspect the issue causing the pidgin hang could also be the cause of the empathy issues:
[https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/1109251](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/1109251)
[https://bugs.launchpad.net/pidgin/+bug/1108056](https://bugs.launchpad.net/pidgin/+bug/1108056)

empathy:
[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/1116449](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/1116449)

And as I mentioned before, I also recently saw the same empathy regression that the OP is talking about in the OP,  I haven't seen a bug report for it yet though, and the other day I decided to switch to another distro anyway. Before this newest regression google talk, facebook, and windows live worked at least, but all of the other plugins have the weird "totally break over time" issue linked in one of the bug reports above (when i first set up accounts on a fresh install they work, but after a few reboots they break "permanently", even after I try removing/re-adding them and rebooting again, only way to get them working again was a clean install). The issues are very bizarre, and very annoying, and so far things have only gotten worse, so my hopes for raring being usable for me when its officially released are pretty low.

Just the fact that I was able to see these issues on totally clean installs and that the bug reports show multiple people as effected is enough for me to know its definitely not "just me". If you aren't having issues with empathy in raring you are probably very lucky. Its also worth noting that I've had none of these issues with the same versions of empathy and pidgin on other distros, something specific to ubuntu 13.04 is causing them.

---

### Post by Budovi on 2013-03-20
I have these bugs:
[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/1116281](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/1116281)
[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/1132151](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/1132151)

Also, only browser authenticated account plugins works for me (but did not try all of them). It is probably connected to both of these bugs.
(yes, that is the bug you linked)

Today, I had problem with "No online contacts" once, but it is not reproducible for now, so I cannot report that.

So basically, empathy works, but only partially, and some sort of luck have to be involved too. And these bugs should be fixed before release, I doubt if people could ignore them.

---

### Post by sonicb00m on 2013-03-21
I dont know what it is about Gnome but they think they know best and keep downgrading all their applications to the point that they barely offer any functionality. I gave up with Empathy last cycle. A great client turned into a piece of <snip> Don't get me started on the mess they have made with Nautilus. What is it with every file manager these days objecting to allowing you to set the location entry permanently without the Windows equivalent of a registry hack?

---

