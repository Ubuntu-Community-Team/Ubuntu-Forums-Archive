---
title: "Getting Lubuntu close to being a &quot;gnome-classic&quot; replacement"
date: 2012-12-29
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2012-12-29
I've been working on this "on the side" and I'm definitely gaining ground, as they say a picture is worth a thousand words:

[ATTACH]229304[/ATTACH]

[ATTACH]229305[/ATTACH]

[ATTACH]229306[/ATTACH]

[ATTACH]229307[/ATTACH]

Caffeine works just as well as the old 'gnome-inhibit-applet' to control 'xscreensaver', and some people don't like the limitations of 'gnome-screensaver' now anyway.

I managed to get the "indicator-applet" to display cpu/system temps, but I need to rinse-n-repeat a few times before I can document how I did it.

The Clearlooks theme is easy to modify so it's fairly easy to get things to look quite "gnome-2-ish" :)

But there are a few minor frustrations ......... mostly just a matter of me needing to spend some time figuring out the LXDE and PCManFM config file structures, but there is absolutely no need for anyone to fear that the old desktop paradigm is dying :D

NOTE: This is a "mash-up" of both Quantal and Raring packages because some things are not yet available in Raring ;)

BTW I'm sure that others will prefer Xubuntu/Xfce and that's just fine.

---

### Post by A_T on 2012-12-30
> **kansasnoob said:**
> I've been working on this "on the side" and I'm definitely gaining ground, as they say a picture is worth a thousand words:

[ATTACH]229304[/ATTACH]

[ATTACH]229305[/ATTACH]

[ATTACH]229306[/ATTACH]

[ATTACH]229307[/ATTACH]

Caffeine works just as well as the old 'gnome-inhibit-applet' to control 'xscreensaver', and some people don't like the limitations of 'gnome-screensaver' now anyway.

I managed to get the "indicator-applet" to display cpu/system temps, but I need to rinse-n-repeat a few times before I can document how I did it.

The Clearlooks theme is easy to modify so it's fairly easy to get things to look quite "gnome-2-ish" :)

But there are a few minor frustrations ......... mostly just a matter of me needing to spend some time figuring out the LXDE and PCManFM config file structures, but there is absolutely no need for anyone to fear that the old desktop paradigm is dying :D

NOTE: This is a "mash-up" of both Quantal and Raring packages because some things are not yet available in Raring ;)

BTW I'm sure that others will prefer Xubuntu/Xfce and that's just fine.

I'm running Mate on Raring and it works well. I always liked the Gnome 2 desktop and for me this is the best alternative. The clearlooks-phenix-theme from the repositories works well with both GTK 2 and 3.

---

### Post by kansasnoob on 2012-12-30
> **A_T said:**
> I'm running Mate on Raring and it works well. I always liked the Gnome 2 desktop and for me this is the best alternative. The clearlooks-phenix-theme from the repositories works well with both GTK 2 and 3.

Did you just use the Quantal version of MATE?

I've tested the MATE version of Snowlinux and it's pretty impressive but I rather prefer "rolling my own" :)

---

### Post by A_T on 2012-12-30
> **kansasnoob said:**
> Did you just use the Quantal version of MATE?

I've tested the MATE version of Snowlinux and it's pretty impressive but I rather prefer "rolling my own" :)

yes I add the following line to my sources.list

```
deb http://packages.mate-desktop.org/repo/ubuntu quantal main
```

I haven't had any problems so far.

I think I'm a bit like you I prefer to build my own Ubuntu or Debian rather than use something like Snowlinux - although I'm sure there's nothing wrong with it.

---

### Post by jerrylamos on 2012-12-30
I have used Lubuntu as a sort of gnome replacement by adding Libre replacing chromium with firetox (chromium can't handle my bookmarks nearly as well as firefox)

Then I sit with leafpad I prefer gedit, pcmanfm I prefer nautilus, abi whatever which don't do what I want to do, ....

The other thing I've done is install lxde on top of ubuntu which has been a real struggle since during development logoff/logon to lxde frequently doesn't work.

So I test raring unity, then for a gnome like get the work done use linux mint 14 usually mate I'm not so sure about cinnamon.

Now I have 7" and 10.1" tablets with Android.  Unity at it's present stage with faster processors and equal or more memory just doesn't cut it, for what I'm able to do with Android. linux is still more general purpose for me.

---

### Post by kansasnoob on 2013-01-01
I keep figuring out more and more little things. Like copy-n-paste always seemed to be a bit of a kludge in Lubuntu (or even Xubuntu) and come to find out it has a lot to do with the default double-click mouse settings.

I plowed through Ubuntu's dconf and found that the default is 400 ms, whereas Lubuntu is 200 ms, and Xubuntu is 250 ms. It's amazing just how much difference a minor tweak like that effects overall performance and usability :)

---

### Post by ventrical on 2013-01-02
> **kansasnoob said:**
> I keep figuring out more and more little things. Like copy-n-paste always seemed to be a bit of a kludge in Lubuntu (or even Xubuntu) and come to find out it has a lot to do with the default double-click mouse settings.

I plowed through Ubuntu's dconf and found that the default is 400 ms, whereas Lubuntu is 200 ms, and Xubuntu is 250 ms. It's amazing just how much difference a minor tweak like that effects overall performance and usability :)


Hawkeye! :)

---

### Post by lykwydchykyn on 2013-01-02
The biggest annoyance for me in LXDE was always the menu.  About half my programs would end up in "Other", even when they legitimately belonged in another category. It didn't look like there were any improvements to the menu in the pipeline, but I notice your menu doesn't have an "other" category.  Is this fixed now or did you manually customize the menu?

---

### Post by kansasnoob on 2013-01-02
> **lykwydchykyn said:**
> The biggest annoyance for me in LXDE was always the menu.  About half my programs would end up in "Other", even when they legitimately belonged in another category. It didn't look like there were any improvements to the menu in the pipeline, but I notice your menu doesn't have an "other" category.  Is this fixed now or did you manually customize the menu?

I've started playing with LXMenuEditor:

[http://lxmed.sourceforge.net/index.html](http://lxmed.sourceforge.net/index.html)

But I keep blowing things up :oops:

---

### Post by amjjawad on 2013-03-29
> **lykwydchykyn said:**
> The biggest annoyance for me in LXDE was always the menu.  About half my programs would end up in "Other", even when they legitimately belonged in another category. It didn't look like there were any improvements to the menu in the pipeline, but I notice your menu doesn't have an "other" category.  Is this fixed now or did you manually customize the menu?

Hi,

I have never seen "other" on Lubuntu since 10.04 until now. Are we talking about LXDE or Lubuntu?

---

### Post by amjjawad on 2013-03-29
> **kansasnoob said:**
> I've been working on this "on the side" and I'm definitely gaining ground, as they say a picture is worth a thousand words:

[ATTACH]229304[/ATTACH]

[ATTACH]229305[/ATTACH]

[ATTACH]229306[/ATTACH]

[ATTACH]229307[/ATTACH]

Caffeine works just as well as the old 'gnome-inhibit-applet' to control 'xscreensaver', and some people don't like the limitations of 'gnome-screensaver' now anyway.

I managed to get the "indicator-applet" to display cpu/system temps, but I need to rinse-n-repeat a few times before I can document how I did it.

The Clearlooks theme is easy to modify so it's fairly easy to get things to look quite "gnome-2-ish" :)

But there are a few minor frustrations ......... mostly just a matter of me needing to spend some time figuring out the LXDE and PCManFM config file structures, but there is absolutely no need for anyone to fear that the old desktop paradigm is dying :D

NOTE: This is a "mash-up" of both Quantal and Raring packages because some things are not yet available in Raring ;)

BTW I'm sure that others will prefer Xubuntu/Xfce and that's just fine.

Hi,

Just to make sure we are on the same boat/page. Are you trying to achieve similar experience/environment to GNOME 2 by using Lubuntu? 

On a side note: Before my passion and obsession for Lubuntu started, I used to love GNOME2 and Ubuntu 10.04 was my favorite. Well, that is history now :D

---

### Post by lykwydchykyn on 2013-03-30
> **amjjawad said:**
> Hi,

I have never seen "other" on Lubuntu since 10.04 until now. Are we talking about LXDE or Lubuntu?

I honestly don't remember; I've installed LXDE on so many distros, and I don't have anything running Lubuntu at the moment.  The "other" menu has been an annoyance for me in LXDE in general.  That's why I found it notable that this was missing.

---

### Post by kansasnoob on 2013-03-30
> **amjjawad said:**
> Hi,

Just to make sure we are on the same boat/page. Are you trying to achieve similar experience/environment to GNOME 2 by using Lubuntu? 

On a side note: Before my passion and obsession for Lubuntu started, I used to love GNOME2 and Ubuntu 10.04 was my favorite. Well, that is history now :D

Basically yes. In fact i can get almost everything to behave as though I were using Gnome 2. The one thing I haven't figured out is why in GNOME you can highlight text, then click anywhere on that page to copy or cut, but with Openbox/Lubuntu you must focus the mouse directly over the highlighted text. But Clearlooks still works perfectly in Lubuntu :)

And it looks like I may have Julien talked into pursuing a LTS for 14.04! I proposed 30 to 36 months.

---

### Post by EgoGratis on 2013-03-30
Situation is improving bit by bit for users that would like to use GNOME but don't feel comfortable using GnomeShell:

[http://www.h-online.com/open/news/item/GNOME-3-8-brings-polish-and-new-Classic-Mode-1832713.html](http://www.h-online.com/open/news/item/GNOME-3-8-brings-polish-and-new-Classic-Mode-1832713.html)

The problem is you have to have decent GPU acceleration if you don't want to have slow DE but i do imagine this is not to hard to achieve nowadays. There are still issues like why can't i rotate the cube... but i do see possibility Classic Mode would become used/loved again. I don't think GnomeShell in the state it is today (the whole paradigm/concept) will become something used/loved by huge user base but i do see possibility for GNOME to pull it off with Classic Mode to some extent.

---

### Post by EgoGratis on 2013-03-30
And imagine Ubuntu would give the edge to GNOME 3 Classic Mode again like it did with GNOME 2. It could work but yes now we have other "fancy shells" and we have to see what they will achieve first.

P.S. But it's nice to know there still is something we could call Classic Mode officially supported by GNOME team!

---

### Post by cortman on 2013-03-30
> **kansasnoob said:**
> I've been working on this "on the side" and I'm definitely gaining ground, as they say a picture is worth a thousand words:

I love Lubuntu as well; the team is turning out some really amazing looking UIs and the whole system is still solid and lightweight.

When you're ready to write up a wiki page with all your tweaks and configs, let me know. :p

---

### Post by vasa1 on 2013-03-30
> **lykwydchykyn said:**
> The biggest annoyance for me in LXDE was always the menu.  About half my programs would end up in "Other", even when they legitimately belonged in another category. It didn't look like there were any improvements to the menu in the pipeline, but I notice your menu doesn't have an "other" category.  Is this fixed now or did you manually customize the menu?
I'm using pure (= no other DE) 12.10 Lubuntu. I don't see "other". Could you put up a pic of your issue? Maybe in a thread of its own?

---

### Post by screaminj3sus on 2013-03-31
xfce is closer to gnome classic than lxde

---

### Post by lykwydchykyn on 2013-03-31
> **vasa1 said:**
> I'm using pure (= no other DE) 12.10 Lubuntu. I don't see "other". Could you put up a pic of your issue? Maybe in a thread of its own?

I appreciate that all the Lubuntu enthusiasts are ready to help me with this issue, but please notice the use of past tense in my post.  I don't generally use LXDE anymore except on the occasional server or ad-hoc test system where I don't want to download a huge desktop environment.  If Lubuntu has fixed the "other" problem in the menu, great; glad to hear it.  I was *mentioning* that this was a problem for me in the past specifically because I did not see it in the OP's screenshots.

---

### Post by vasa1 on 2013-03-31
> **lykwydchykyn said:**
> I appreciate that all the Lubuntu enthusiasts are ready to help me with this issue, but please notice the use of past tense in my post. ...
Ubuntu is used by people with varying grammatical competence. That's my excuse for why I don't parse posts punctiliously. Will do so in future ;)

---

### Post by José Serra on 2013-03-31
> **lykwydchykyn said:**
> I honestly don't remember; I've installed LXDE on so many distros, and I don't have anything running Lubuntu at the moment.  The "other" menu has been an annoyance for me in LXDE in general.  That's why I found it notable that this was missing.
I have seen it in Raspbian (Raspberry Pi).

Regards

---

### Post by shantiq on 2013-04-01
a few related [tips]("http://ubuntuforums.org/showthread.php?t=2124966") here. also [here]("http://ubuntuforums.org/showthread.php?t=2036527&p=12569952#post12569952")...   i used fallback to give myself a sort of Karmic look but with 13.04   ...   some of the info might be of pertinence here

[ATTACH=CONFIG]240801[/ATTACH]

[http://i53.fastpic.ru/big/2013/0328/50/8373ba4b6c36541fc6434aed1c719450.png](http://i53.fastpic.ru/big/2013/0328/50/8373ba4b6c36541fc6434aed1c719450.png)

---

### Post by kansasnoob on 2013-04-01
> **screaminj3sus said:**
> xfce is closer to gnome classic than lxde

Why? Or maybe I should say "how so"? Just because it has a top panel?

One of the things I really like about Lubuntu is that if you've installed a different flavor you can simply install 'lubuntu-core' to get the basic DE and then you can pick and choose what packages you want to add beyond that :)

---

### Post by kansasnoob on 2013-04-01
> **shantiq said:**
> a few related [tips]("http://ubuntuforums.org/showthread.php?t=2124966") here. also [here]("http://ubuntuforums.org/showthread.php?t=2036527&p=12569952#post12569952")...   i used fallback to give myself a sort of Karmic look but with 13.04   ...   some of the info might be of pertinence here

[ATTACH=CONFIG]240801[/ATTACH]

[http://i53.fastpic.ru/big/2013/0328/50/8373ba4b6c36541fc6434aed1c719450.png](http://i53.fastpic.ru/big/2013/0328/50/8373ba4b6c36541fc6434aed1c719450.png)

I made some notes about that also:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

---

### Post by shantiq on 2013-04-01
> **kansasnoob said:**
> I made some notes about that also:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

 Cool Kansas; we should start a retroclub for the guys who want to live in the past &#10026; personally i am a fan of the Warty Warthog desktop image and gnome 2 around Karmic about perfect for the next 20 years insofar's i am concerned ...   good to make all this info available...   Linux is about customization and choice   ...   These are possible routes and the info need be available;   i know we are a minority , but minorities matter     ... &#9775;

---

