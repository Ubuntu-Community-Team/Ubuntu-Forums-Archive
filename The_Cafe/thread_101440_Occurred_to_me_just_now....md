---
title: "Occurred to me just now..."
date: 2005-12-09
forum: The Cafe
---

### Post by Jormundgand on 2005-12-09
I've just now been on a massive update spree (I've got the new Cairo-enabled Clearlooks which is sexygreat, Firefox 1.5 which is wunderbar and Gaim 2.0.0 which is excellent) and figured one of Ubuntu's real setbacks for we upwardly-mobile Linux users is the highly rigid update schedule Ubuntu sticks to. Obviously this is a good thing for users who don't want to experiment and are happy with their regular Web browser and office regime and don't have the time or inclination to fiddle with the latest gadgets.

So I figured, why not something of a spinoff (like Ubuntu did with Debian, or perhaps under more of a Kubuntu-style flag) with a more fluid update regime able to provide the latest flashy things like the new Clearlooks or an updated Gaim or whatever as they appear? This seemed to me to be what the backports repositories set out to do originally, but it seems to be failing spectacularly at that (missing packages galore). Regular Ubuntu makes me somewhat skittish about changing what the repositories provide, since they want me to think they are the be-all and end-all of what is "Ubuntu" - a separate "initiative" (if you like) might provide more of an exploratory bent.

Here's my thoughts on it: there would be levels of completion - "release", "release candidate", "development", something like that, each given their own repository; of course, the Ubuntu concept of free and nonfree repositories would probably still exist. The releases on CD/DVD would be snapshots of what is available at the time of release - the repositories continue to update smoothly and people effectively jump on board and join the ride, as it were.

Am I barking mad? Tell me what you think. I appreciate constructive criticism, and I don't at all expect this to be a realistic approach; it's just a thought I had.

---

### Post by bjweeks on 2005-12-09
Gaim 2.0 is not out yet. So do you want to try beta software or update to the latest stable version. If the latter try the backports. Also if you want the newest beta try dapper but its buggy.

---

### Post by ssam on 2005-12-09
i think the reason ubuntu moves so fast (good release every 6 months), is because the developers aren't affaid to experiment on the testing branch (currently dapper).

debian has quite strict rules for something to even make it onto the testing/unstable branches. these seem to make everything move at a slower pace.

atleast with ubuntu you know you will get hot new software (from kernel to desktop) in 6 months time.

the backports team do a good job of taking new software from dapper, and making it work in breezy. if you are savy enough to compile your own new versions maybe you could help them out.

---

### Post by Jormundgand on 2005-12-09
Six months is still quite a while to wait in terms of new stuff.

The backports team are doing a good job? There are many unresolved dependencies on their repositories. (Try installing pan or xcompmgr from backports. Both flagged up dependency problems for me while their stable relatives installed fine.)

I'll accept that Debian is stricter about things. I just would like there to be more fluidity in Ubuntu moving forward. I don't like the feeling of being stuck on one level looking up at some plateau which will come "in six months !!!". I'd rather it be a staircase, constantly upwardly-mobile, but the poor state (as I see it) of backports and lack of alternatives seems to take the edge off that.

And I'm not savvy enough to compile myself. More's the pity, really.

---

### Post by ow50 on 2005-12-09
[QUOTE=Jormundgand]I don't like the feeling of being stuck on one level looking up at some plateau which will come "in six months !!!". I'd rather it be a staircase, constantly upwardly-mobile, [...]
And I'm not savvy enough to compile myself.[/QUOTE]
Sounds to me like debian unstable is what you're looking for. It's got a constant flow of new packages and it might be a bit more stable than dapper.

Not giving updates to the stable version allows the developers to focus their efforts on the development version, which does pay off. Maintaning two or even three versions would be effort misplaced.

I find the Ubuntu release schedule quite reasonable. There are some apps that I like to update and I keep an eye on what gets added to dapper and then I build what I need. I quite like the build-it-yourself, do-it-at-your-own-risk style for updating as I don't need the very latest for more than maybe 20 apps.

---

### Post by matthew on 2005-12-09
Something like this may happen. Mark Shuttleworth himself proposed it. It was first discussed many moons ago with developers and "live on the edge" types as the primary audience. The things ow50 said are among the reasons it hasn't yet been done, but the idea is under consideration.

Here's the wiki page for the scoop:

[https://wiki.ubuntu.com/GrumpyGroundhog]("https://wiki.ubuntu.com/GrumpyGroundhog")

---

