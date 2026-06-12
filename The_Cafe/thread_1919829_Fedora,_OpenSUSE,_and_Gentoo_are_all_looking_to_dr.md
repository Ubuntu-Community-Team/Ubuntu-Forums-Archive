---
title: "Fedora, OpenSUSE, and Gentoo are all looking to drop Compiz..."
date: 2012-02-03
forum: The Cafe
---

### Post by Version Dependency on 2012-02-03
From _[Phoronix]("http://www.phoronix.com/scan.php?page=news_item&px=MTA1MjI")_:
> While Fedora 17 has a massive amount of features to look forward to,  updates to Compiz is likely not on the agenda. In the coming days,  Compiz and its related packages for this compositing window manager are likely to be removed from the Fedora 17 package-list... One of the OpenSUSE guys responding on the _[Fedora list]("http://lists.fedoraproject.org/pipermail/devel/2012-February/162109.html")_:
> openSUSE is about to drop Compiz from the Distro (unless we grab a maintainer);And finally _[Gentoo]("http://archives.gentoo.org/gentoo-dev/msg_7890ae9f8247f2250655116b24af6f54.xml")_:
> # Jorge Manuel B. S. Vicetto <jmbsvicetto@g.o> (22 Jan 2012) 
# Mask compiz for last-rites unless someone steps up 
# to maintain it. Removal in 30 days.Looks like Ubuntu and Unity are the only things keeping Compiz afloat.

---

### Post by juancarlospaco on 2012-02-03
Maintaining in code or in packaging ...?

---

### Post by forrestcupp on 2012-02-03
As much as I hate to say it, I think Compiz is at the end of its days. It's been a good run, though. It's fun to think back to the days when we used to argue about whether Beryl or Compiz was better.

---

### Post by wojox on 2012-02-03
Looks like Mutter will do fine after all. :P

---

### Post by Linuxratty on 2012-02-03
I love Compiz!:( How can they do this?

---

### Post by kurt18947 on 2012-02-03
WHAT??! NO SPINNING CUBE??! Perhaps 2012 is the end of days after all 


:wink:

---

### Post by hhh on 2012-02-03
Compiz 0.8.4-4 is in Debian Squeeze, 0.8.4-5 is in Wheezy and Sid, and 0.9.2.1 is in experimental. I wouldn't worry just yet.

---

### Post by BrokenKingpin on 2012-02-03
I have not had a use for compiz for many years.

If you want spinning cubes use KDE.

---

### Post by Simian Man on 2012-02-03
Compiz started out as a proof of concept and was always just kind of a hack.  I'm not surprised distro maintainers are leaving it behind.

---

### Post by Linuxratty on 2012-02-03
> **hhh said:**
> Compiz 0.8.4-4 is in Debian Squeeze, 0.8.4-5 is in Wheezy and Sid, and 0.9.2.1 is in experimental. I wouldn't worry just yet.

Ahhh,good to hear.

---

### Post by tjeremiah on 2012-02-03
I need my scale plugin and pretty open and close animations.

---

### Post by CarpKing on 2012-02-04
I wonder if we'll see a return to Unity-Mutter...

...Or maybe Unity2D+KWin for 3D effects.

---

### Post by mips on 2012-02-04
> **forrestcupp said:**
> As much as I hate to say it, I think Compiz is at the end of its days. It's been a good run, though. It's fun to think back to the days when we used to argue about whether Beryl or Compiz was better.

I tried both and then decided I don't see the point. I definitely wont miss compiz

---

### Post by sffvba[e0rt on 2012-02-04
Typical, as soon as I enable wobbly windows I read this :p


404

---

### Post by JDShu on 2012-02-04
> **Simian Man said:**
> Compiz started out as a proof of concept and was always just kind of a hack.  I'm not surprised distro maintainers are leaving it behind.

I see this a lot, but I've always wondered what was hackish about Compiz?

---

### Post by Simian Man on 2012-02-04
> **JDShu said:**
> I see this a lot, but I've always wondered what was hackish about Compiz?

From an end-user perspective, there are places where it just doesn't integrate into the rest of your desktop well.  For example, if you try to use the mouse-over previews of your task bar, it would never show them for minimized windows.  This was a known issue that they basically couldn't fix (Kwin does not have this problem).  Also they need a whole category of "workaround" plugins to get around the fact that Compiz was badly designed and broke things with a number of applications.

Additionally the code became pretty much unmaintainable with the lone developer having to do a complete rewrite which has had little to no progress.  The project is a mess and is all but dead.

---

### Post by whatthefunk on 2012-02-04
My impression is that the developer is a little overwhelmed and therefore development has slowed to a near halt.  It had its place but its not really needed anymore...there are several alternatives.

---

### Post by JDShu on 2012-02-04
> **Simian Man said:**
> From an end-user perspective, there are places where it just doesn't integrate into the rest of your desktop well.  For example, if you try to use the mouse-over previews of your task bar, it would never show them for minimized windows.  This was a known issue that they basically couldn't fix (Kwin does not have this problem).  Also they need a whole category of "workaround" plugins to get around the fact that Compiz was badly designed and broke things with a number of applications.

Additionally the code became pretty much unmaintainable with the lone developer having to do a complete rewrite which has had little to no progress.  The project is a mess and is all but dead.

Ah I see, it was basically badly written. I had always thought it was due to being a hack "on top of" GNOME, which wouldn't really have solely been Compiz's fault. So do these problems propagate into Unity?

---

### Post by Pogeymanz on 2012-02-05
The only reason KWin doesn't share some of the same problems is because Compiz is desktop agnostic.

KWin only has to worry about working with Kicker inside of KDE. Compiz, believe it or not, is not just for Gnome2. It works in LXDE, XFCE, Gnome2, Gnome3 fallback, KDE, Unity of course, and as a standalone window manager.

Compiz is also infinitely more customizable than KWin (let alone other compositing WMs) and uses way less memory on my machines.

I don't think Compiz is dead, especially since Unity uses it. It would be sad if it became Unity-specific, though.

---

### Post by inobe on 2012-02-05
kwin is only at it's infancy, and it does what compiz did and then some.

[http://img4.imageshack.us/img4/536/snapshot1xa.jpg](http://img4.imageshack.us/img4/536/snapshot1xa.jpg)

[http://img96.imageshack.us/img96/1444/snapshot2iu.jpg](http://img96.imageshack.us/img96/1444/snapshot2iu.jpg)

[http://img21.imageshack.us/img21/3700/snapshot3w.jpg](http://img21.imageshack.us/img21/3700/snapshot3w.jpg)

the list was so long i needed to take three region selected screenshots:p



here are what others did [http://fitzcarraldoblog.wordpress.com/2011/04/27/pimping-my-desktop-have-kwin-desktop-effects-improved-in-kde-4-6-2/](http://fitzcarraldoblog.wordpress.com/2011/04/27/pimping-my-desktop-have-kwin-desktop-effects-improved-in-kde-4-6-2/)

---

### Post by CarpKing on 2012-02-05
> **tjeremiah said:**
> I need my scale plugin and pretty open and close animations.

Gnome-shell's "Activities Overview" works pretty much like the Scale Plugin (it even activates via upper left hot-corner, same as Compiz default).  

Mutter does animations on par with the simple Compiz ones (such as zoom and fade), though by default "close" doesn't seem to have one assigned (the window just disappears) and I'm not sure how configurable the animations are (not at all by default, of course).

---

### Post by MisterGaribaldi on 2012-02-05
Man... I go away for a while and look what happens!

Well, I think it's sad, but even more sad is that the better elements of it didn't get merged into X.org or Gnome / KDE / etc.

Then again, I wish Ubuntu would just use Gnome 3/Cinnamon, with the straight version of Gnome 3 with tweaks reserved for tablets and netbooks that benefit from an iOS-esq UI.

---

### Post by Simian Man on 2012-02-06
> **Pogeymanz said:**
> The only reason KWin doesn't share some of the same problems is because Compiz is desktop agnostic.

KWin only has to worry about working with Kicker inside of KDE. Compiz, believe it or not, is not just for Gnome2. It works in LXDE, XFCE, Gnome2, Gnome3 fallback, KDE, Unity of course, and as a standalone window manager.
That's not true at all.  Kwin works perfectly well as a standalone window manager or with Gnome, Xfce or LXDE.  The only thing that won't work is the window previews (at least not with the XFCE panel).  But as I pointed out Compiz can't do that properly with *any* panel.  The reason most people don't use Kwin except with KDE is likely because it has more dependencies.

Another benefit of Kwin is that you can use the same window manager regardless of whether or not you use desktop effects.  And by the way "Kicker" is dead as of KDE4.


> **Pogeymanz said:**
> Compiz is also infinitely more customizable than KWin (let alone other compositing WMs).
That is not true either.  As inobe showed, Kwin has a ton of effects.  I don't use half of the effects either Kwin or Compiz offer, so I don't know which has more, but it's definitely false to say Compiz has "infinitely" more.

---

### Post by Pogeymanz on 2012-02-06
> **Simian Man said:**
> That's not true at all.  Kwin works perfectly well as a standalone window manager or with Gnome, Xfce or LXDE.  The only thing that won't work is the window previews (at least not with the XFCE panel).  But as I pointed out Compiz can't do that properly with *any* panel.  The reason most people don't use Kwin except with KDE is likely because it has more dependencies.


Fair enough, but the dependencies issue does count. I imagine that you have to pull quite a bid of KDE to be able to not only run Kwin, but to then customize it via the settings dialog of KDE.

> **Simian Man said:**
> 
And by the way "Kicker" is dead as of KDE4.


Okay, I thought the panel was still called kicker.


> **Simian Man said:**
> 
That is not true either.  As inobe showed, Kwin has a ton of effects.  I don't use half of the effects either Kwin or Compiz offer, so I don't know which has more, but it's definitely false to say Compiz has "infinitely" more.

It's not the number of effects, necessarily. It's the customizability of each effect.

Take for example Compiz's scale plugin. KDE has a scale plugin, but we can only adjust its speed in a very coarse way. There are approximately 5 or so speeds to choose from. Compiz has several parameters that we can tweak to get the best amount of "bounciness" and speed and smoothness. Furthermore, these parameters can we can tweak all have continuous values between 0 and 50 with precision of four decimal places, making literally over 300,000 slightly different settings for one parameter, if I calculated that right.

Now, that's a pretty insignificant example, but there are other more important ones like key-bindings. Compiz has way more keyboard and mouse binding options for all of its plugins than KWin has. That's one of the biggest killers for me.

I could go through and list all the little reasons I like Compiz more, but my point is that KWin is far from strictly better than Compiz and Compiz does bring things to the table that no other WM does.

(Alt-tab is way better in Compiz, IMO, and the live preview desktop switching is awesome)

---

### Post by koleoptero on 2012-02-07
> **Pogeymanz said:**
> Now, that's a pretty insignificant example, but there are other more important ones like key-bindings. Compiz has way more keyboard and mouse binding options for all of its plugins than KWin has. That's one of the biggest killers for me.

EDIT: OK reread and I agree that the plugins in kwin aren't as configurable, but they work. Try some of the plugins in compiz in 11.10 that aren't enabled by default. Blur is one that comes to mind.

It's a shame if compiz will die imo, it is a great WM.

---

### Post by HansKisaragi on 2012-02-07
> **forrestcupp said:**
> As much as I hate to say it, I think Compiz is at the end of its days. It's been a good run, though. **It's fun to think back to the days when we used to argue about whether Beryl or Compiz was better**.

oh the memories! :KS

---

### Post by roachk71 on 2012-02-10
> **forrestcupp said:**
> As much as I hate to say it, I think Compiz is at the end of its days. It's been a good run, though. It's fun to think back to the days when we used to argue about whether Beryl or Compiz was better.

Yeah. IMHO Compiz looked pretty, but I'll bet that many of us would rather see better performance than resource-wasting eye-candy.

(As a side-note, I wonder if Sabayon's still being used, slow as it is?) *Style and efficiency don't mix.* \\:D/

---

### Post by screaminj3sus on 2012-02-11
> **Simian Man said:**
> From an end-user perspective, there are places where it just doesn't integrate into the rest of your desktop well.  For example, if you try to use the mouse-over previews of your task bar, it would never show them for minimized windows.  This was a known issue that they basically couldn't fix (Kwin does not have this problem).  Also they need a whole category of "workaround" plugins to get around the fact that Compiz was badly designed and broke things with a number of applications.

Additionally the code became pretty much unmaintainable with the lone developer having to do a complete rewrite which has had little to no progress.  The project is a mess and is all but dead.

This is why I think its totally absurd that canonical dropped mutter, and based unity off of compiz. Mutter did have problems when it was younger, but its MASSIVELY improved and I think in the long run staying with it would have been much smarter. Compiz is a lumbering giant. IMO both mutter and kwin have now surpassed it. I could care less about the stupid spinning cube.

Compiz's performance in 11.04 and 11.10 is pretty sad on my machines. Compiz 0.8.x is noticeably faster. In ubuntu 11.04 I used gnome classic with downgraded compiz for this reason.

Compiz has done a lot for the linux desktop, but I think the move to faster, more integrated compositors has been a long time coming.

I like unity, but I think using compiz was a poor implementation.

---

### Post by screaminj3sus on 2012-02-11
> **CarpKing said:**
> Gnome-shell's "Activities Overview" works pretty much like the Scale Plugin (it even activates via upper left hot-corner, same as Compiz default).  

Mutter does animations on par with the simple Compiz ones (such as zoom and fade), though by default "close" doesn't seem to have one assigned (the window just disappears) and I'm not sure how configurable the animations are (not at all by default, of course).
Mutter has the capability for options and plugins, just dont expect to see it from GNOME.

Cinnamon has already added some options to its mutter fork (muffin) for different animations and such.

And I think there are a few proof of concept mutter plugins around.

---

### Post by Pogeymanz on 2012-02-11
> **screaminj3sus said:**
> Compiz is a lumbering giant. IMO both mutter and kwin have now surpassed it. I could care less about the stupid spinning cube.

In what ways is Compiz a lumbering giant?

Disk space? I think my latest Compiz git build took up some 50MB.

Memory Use? My Compiz standalone session uses about 130MB RAM at startup, whereas my Openbox session (which runs identical apps sans the WM) uses about 100MB RAM.

EDIT: Oh, and disable the cube if you don't like it. KWin also has a "stupid spinning cube" plugin.

---

### Post by screaminj3sus on 2012-02-11
> **Pogeymanz said:**
> In what ways is Compiz a lumbering giant?

Disk space? I think my latest Compiz git build took up some 50MB.

Memory Use? My Compiz standalone session uses about 130MB RAM at startup, whereas my Openbox session (which runs identical apps sans the WM) uses about 100MB RAM.

EDIT: Oh, and disable the cube if you don't like it. KWin also has a "stupid spinning cube" plugin.

Its slow. I have two machines, one with intel ironlake graphics, one with ati hd2600. Compiz is significantly slower than gnome-shell/mutter or kde 4.8/kwin. Animations often visibly lag. The alt tab switcher will sometimes take 1-3 seconds to come up, on a cold boot the dash will take like 5 seconds to open (gnome-shell activities is always instant).

I am hoping for improvements in 12.04, but the whole compiz 0.9.x series has had serious performance issues on my machines. When it seems to just be getting slower since 0.8.x which runs well it doesn't give me much confidence. We'll see I guess.

Memory usage and disk space I am not concerned with, I just expect compositing to be smooth. Compiz seems to have fallen far behind in that area.

---

### Post by Pogeymanz on 2012-02-11
> **screaminj3sus said:**
> Its slow. I have two machines, one with intel ironlake graphics, one with ati hd2600. Compiz is significantly slower than gnome-shell/mutter or kde 4.8/kwin. Animations often visibly lag. The alt tab switcher will sometimes take 1-3 seconds to come up, on a cold boot the dash will take like 5 seconds to open (gnome-shell activities is always instant).

I am hoping for improvements in 12.04, but the whole compiz 0.9.x series has had serious performance issues on my machines. When it seems to just be getting slower since 0.8.x which runs well it doesn't give me much confidence. We'll see I guess.

Memory usage and disk space I am not concerned with, I just expect compositing to be smooth. Compiz seems to have fallen far behind in that area.

Strange. My Gnome-Shell is super laggy on my intel graphics computer. Kwin 4.8 is the first version that doesn't feel terrible on this computer as well.

Compiz has all kinds of advanced settings, so maybe some of those contribute to people having good or bad experiences with it.

---

### Post by smellyman on 2012-02-11
kwin 4.8 imo is the best window manager now.

super smooth and freature rich.  disaable effects or use them and it still is great.

I believe phoronix did benchmarks back with kwin4.6 comparted to other wm's and it came out on top.  4.8 has taken it to another leve.

---

### Post by inobe on 2012-02-11
kwin is essentially everything with or without affects.

---

### Post by screaminj3sus on 2012-02-11
> **Pogeymanz said:**
> Strange. My Gnome-Shell is super laggy on my intel graphics computer. Kwin 4.8 is the first version that doesn't feel terrible on this computer as well.

Compiz has all kinds of advanced settings, so maybe some of those contribute to people having good or bad experiences with it.

Previous versions of kwin did have terrible performance for me too, but 4.8 is great. Gnome-shell has always been smooth for me on intel graphics, since the the first gnome 3.0 release.

Compiz can't even handle resizing a window in "normal" mode without lagging like crazy for example. Mutter and kwin do it flawlessly. Compiz's performance isn't bad everywhere, some plugins like the desktop wall, and the scale plugin are really smooth, but in other areas it does seem too laggy.

My compiz settings are pretty much default, but with sync to vblank disabled, detect framerate disabled, and framerate set to 60.

---

### Post by deonis on 2012-02-11
I do not know where it all going. It is still almost a year to December 21 2012 :). Perhaps, Gnome community will want to implement some 3D effects in Metacity...  It will make more sense than having some third party program to do that.

---

### Post by Copper Bezel on 2012-02-12
[QUOTE=Pogeymanz]Strange. My Gnome-Shell is super laggy on my intel graphics computer. Kwin 4.8 is the first version that doesn't feel terrible on this computer as well.[/QUOTE]
Yeah, subjective experience tells very little, because it's all to do with configuration on the one hand and the particulars of the video card on the other. Mutter is not as snappy as Compiz / Emerald on my machine, but the Unity window decorator causes stutter when moving windows. It's really unpredictable what's going to perform best. 

But the main thing is, in terms of overhead as a WM, Compiz isn't actually that heavy. It doesn't play nicely with every graphics card, and some of the effects can be very intensive, even at their default settings (but of course you can crank down time steps and things.)

---

### Post by detroit/zero on 2012-02-12
> **forrestcupp said:**
> As much as I hate to say it, I think Compiz is at the end of its days. It's been a good run, though. It's fun to think back to the days when we used to argue about whether Beryl or Compiz was better.
Funny thing - I always thought Beryl was better. On the hardware I had at the time (two separate computers, a laptop and a desktop both running Feisty Fawn), Beryl ran lighter and was far more responsive and was more customizable. Compiz, of course, evolved over time to include the customizability (is that a word?) of Beryl and then some. I always felt it was resource-heavy (especially knowing Beryl would have done all the same things, but with 60% of the resources used), but it seemed to get worked out in the end.

In all actuality, spinning cubes and burning or wobbling windows do nothing to enhance productivity. It was a nice contrast to the bland and dated looks of XP, but it's an idea whose time has passed.

---

