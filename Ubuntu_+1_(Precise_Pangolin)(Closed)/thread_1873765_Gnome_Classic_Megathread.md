---
title: "Gnome Classic Megathread"
date: 2011-11-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by cariboo on 2011-11-01
Please post all your gnome classic (gnome-session-fallback) hints tips and workarounds in this thread. It is my hope that we can create a digest/wiki page near the end of the development cycle so that all the cool stuff can be put in one place.

---

### Post by lucazade on 2011-11-02
At the moment no real tips but I can report my experience with gnome-panel gtk3.
I've tried it numerous times from its first release (included in gnome 3.0) to latest git version (3.3.2) that is not released yet.

Gnome panel is developed by Vincent Untz, this was the announce of the gtk3 porting:
[http://www.vuntz.net/journal/post/2011/04/13/gnome-panel-is-dead,-long-live-gnome-panel](http://www.vuntz.net/journal/post/2011/04/13/gnome-panel-is-dead,-long-live-gnome-panel)!

Issues still present in 3.3.2:
- css gradient background is not applied to the whole panel, some pieces are not skinned. this depends on the panel code and not to the theme.
- tray icons are usually misaligned, wrong padding and margin between borders and other icons.. a real mess!
- lack of app-indicators (this is probably more a canonical issue than a upstream one because are not adopted by gnome itself)
- taskbar buttons make a lot a artifacts and glitches, usually application icons on are not displayed until you over with the mouse.
- clock usually cut a part of it until you over it
- some applications like nautilus open two buttons on the taskbar when opening then one disappears.

these are the more evident and still not solved.. there are others but not so problematic..
Sincerly until gnome-panel matures enough I'll follow slickpanel development (taskbar+indicators in gtk3) and I'll use the great xfce4-panel.

---

### Post by lucazade on 2011-11-02
Just a note... there are also other alternatives panels like xtint2, lxpanel..  
both with pros and cons

---

### Post by robert shearer on 2011-11-02
Just the basics...
**alt+right-click** to on a panel to get the options menu.

For launchers in panels... navigate the Applications or Places menus to the item you want in the panel and drag and drop to the panel.
(some of the Places open in the background..eg Music folder launched from the panel seems to open behind other windows. Apps open in the foreground.

**Some** indicators work in the panels. **indicator-weather** works well. Install then drag from menu (Applications>Accessories) to panel as above.

---

### Post by tista on 2011-11-02
Guys,

OK... I could finally confirm that xfce4-panel was amazing!! :P

[[IMG]http://img337.imageshack.us/img337/7491/screenshotat20111102233.th.png[/IMG]](http://img337.imageshack.us/img337/7491/screenshotat20111102233.png)

---

### Post by xebian on 2011-11-02
> **tista said:**
> Guys,

OK... I could finally confirm that xfce4-panel was amazing!! :P

[[IMG]http://img337.imageshack.us/img337/7491/screenshotat20111102233.th.png[/IMG]](http://img337.imageshack.us/img337/7491/screenshotat20111102233.png)

That's a museum in Milwaukee, Wisconsin USA by an Spanish architect.

---

### Post by ventrical on 2011-11-02
I think it would be a good idea to have a continuance of GNOME Classic come the release of Precise. It will give others who have more legacy type systems the opportunity to still be part of the Ubuntu family, have the cutting edge kernels and updates of an LTS version and show that Ubuntu paints it's OS with a broad brush stroke.

---

### Post by kansasnoob on 2011-11-02
**[COLOR="Red"]Note[/COLOR]**: I'm trying to keep an updated version of Steps & Tweaks here:

[http://ubuntuforums.org/showpost.php?p=11465187&postcount=179](http://ubuntuforums.org/showpost.php?p=11465187&postcount=179)

Please consider this high risk ATM, I strongly recommend trying this only on a test installation. If you break it you own it. My initial focus is on gnome classic w/o effects ATM, so your mileage may vary if using gnome classic.

I began this with a fresh install of Oneiric, fully updated, and then upgraded to Precise on 11/02/2011.

Step #1:

I installed &#8216;gnome-session-fallback&#8217; which also installs the following dependencies:

alacarte 
gir1.2-panelapplet-4.0 
gnome-applets 
gnome-applets-data 
gnome-panel 
gnome-panel-data 
libpanel-applet-4-0
python-gmenu

Then log out and choose your preferred session before logging back in. 

****************************************************

NOTE: If you want to make the default session "gnome classic w/o effects" you must run this command in the terminal:

```
sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-fallback
```

Or if you want standard "gnome classic" run:

```
sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-classic
```

****************************************************

On initial boot you&#8217;ll see a slightly familiar, and yet different, &#8220;classic&#8221; looking desktop with both an upper and lower panel:

[ATTACH]206178[/ATTACH]

The menu layout is a bit different but it&#8217;s mostly a difference in rearrangement. A few minutes of browsing through the apps should familiarize you fairly quickly.

Two of the most notable changes are in how the panel(s) and applets are edited, moved, etc. You&#8217;ll find that you must now press an Alt key while right-clicking the panel and or applet to facilitate moving, editing, etc.

But you&#8217;ll also notice that you must now double-click on &#8220;Application launcher (Copy a launcher from the app menu)&#8221; in the &#8220;Add to panel&#8221; window to add application launchers. After double-clicking a new window opens and you can easily select which app to add.

 Step #2:

I prefer using only a lower panel, so now it&#8217;s time to do some rearranging ......... viola:

[ATTACH]206179[/ATTACH]

Note: I was very surprised here, no top &#8220;unity panel&#8221; after removing the top gnome-panel as I had in Oneiric. Let&#8217;s hope it stays that way.

Step #3:

I found the overlay-scrollbars to be inconsistent (worked in some apps, but not in others) so I purged:

liboverlay-scrollbar-0.2-0
liboverlay-scrollbar3-0.2-0
overlay-scrollbar

Step #4:

Since I find it useful, I also installed &#8216;gnome-tweak-tool&#8217;, but it does pull in a lot of other &#8220;junk&#8221;:

caribou
cups-pk-helper
gir1.2-accountsservice-1.0
gir1.2-caribou-1.0
gir1.2-clutter-1.0
gir1.2-cogl-1.0
gir1.2-coglpango-1.0
gir1.2-folks-0.6
gir1.2-gee-1.0
gir1.2-gkbd-3.0
gir1.2-json-1.0
gir1.2-mutter-3.0
gir1.2-networkmanager-1.0
gir1.2-polkit-1.0
gir1.2-telepathyglib-0.12
gir1.2-telepathylogger-0.2
gir1.2-upowerglib-1.0
gjs
gnome-icon-theme-full
gnome-shell
gnome-themes-standard
gnome-tweak-tool
libcaribou0
libclutter-1.0-0
libclutter-1.0-common
libcogl-common
libcogl-pango0
libcogl5
libgjs0c
libmozjs185-1.0
libmutter0
mesa-utils
mutter-common

Since disc space is not an issue for me I guess I don&#8217;t care though. It shows up in Other > Advanced Settings. The only things I change ATM is selecting &#8220;Show mounted volumes on desktop&#8221; under the Desktop tab, and under the Theme tab I select On for both Buttons and Menus have icons.

Step #5:

Might as well move the buttons:

&#65279;```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"
```

Getting pretty close to true &#8220;classic&#8221;:

[ATTACH]206180[/ATTACH]

Now I wish I could find a replacement for the screensaver inhibit-applet like I used in gnome 2, and a computertemp or sensors-applet, and I&#8217;m not sure what to expect as far as notifications.

Note: Regarding an inhibit applet please see post #29 regarding Caffeine.

I&#8217;d also like to have the scrollbars follow the same color as the titlebar like I could with clearlooks, so I have more tweaks to try.

Not bad for one afternoon of fiddling though.

---

### Post by kansasnoob on 2011-11-02
> **cariboo907 said:**
> Please post all your gnome classic (gnome-session-fallback) hints tips and workarounds in this thread. It is my hope that we can create a digest/wiki page near the end of the development cycle so that all the cool stuff can be put in one place.

Thanks for kicking this off :)

---

### Post by kansasnoob on 2011-11-02
First problem :(

Lightdm is not saving my default login so I always have to boot into Unity, then log out, then log back into classic w/o effects.

Since I followed Lubuntu during the Oneiric dev cycle, and it used lxdm, I'm stumped regarding how to change that :)

Can you help a dummy out :confused:

---

### Post by cbowman57 on 2011-11-02
Can't remember where I ran across this but you can try:

```
sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-fallback
sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-classic
sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-shell
```


[LIST=1]
[*]Gnome classic w/o effects
[*]Gnome classic
[*]Gnome shell
[/LIST]


*edited

---

### Post by kansasnoob on 2011-11-02
> **cbowman57 said:**
> Can't remember where I ran across this but you can try:

```
sudo /usr/lib/lightdm/lightdm-set-defaults --session gnome-shell
```

That kind of borked things, but using it in a Google search revealed that I needed to run:

```
sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-classic
```

But even that doesn't quite get me there as it drops me into classic rather than classic w/o effects ............ so I'm running Compiz instead of Metacity.

So I need to figure out lightdm's nomenclature for classic-2d :confused:

I'd hope providing a GUI to edit lightdm is on the top of the list for Precise .............. if it's truly going to be precise ;)

I'll be sure to hammer the devs, both at Launchpad and Ayatana, with the words "Precise must live up to it's name" ad nauseam :D

And, yes, I am kind of a jerk.

---

### Post by cbowman57 on 2011-11-02
Sorry about that, try gnome-fallback

---

### Post by kansasnoob on 2011-11-02
The answer is in the last post here:

[http://askubuntu.com/questions/71126/how-do-i-set-the-gnome-classic-login-to-be-the-default-with-autologin](http://askubuntu.com/questions/71126/how-do-i-set-the-gnome-classic-login-to-be-the-default-with-autologin)

---

### Post by kansasnoob on 2011-11-02
> **cbowman57 said:**
> Sorry about that, try gnome-fallback

Oops, we both posted at the same time :)

---

### Post by kansasnoob on 2011-11-02
> **cbowman57 said:**
> Sorry about that, try gnome-fallback

Hey, thanks a gazillion. I've followed some of your other work and you could be really useful here if you're inclined to partake in a retro project like this :)

I hope to see a lot of participation and many different opinions.

---

### Post by cbowman57 on 2011-11-02
@kansasnoob, appreciate that.

I'm still figuring all this stuff out, don't use fallback much but I stumble across little tidbits when I go exploring & am happy to help where I can.

I'm looking forward to the day when I can say, "I ran Gnome 3 before it was cool". :)


btw, I like to think that my current setup  is just Gnome on steroids.  The potential is really untapped.

---

### Post by kansasnoob on 2011-11-02
I just thought to add that the old "inhibit-applet" was part of the "GNOME Power Manager" project, and I assume that they felt it to be unnecessary with gnome3 ............ because it was going to work without it :confused:

Well, it doesn't! I have managed to improve on the screen "blanking" thing while trying to watch streaming video or DVD's but it ain't there yet :(

How do you suggest we entice the Gnome devs to get the inhibit applet back again?

I've only worked with Ubuntu on Launchpad and Ayatana, I've never ventured into Gnome dev land :redface:

Any thoughts?

---

### Post by cbowman57 on 2011-11-02
Nope, I haven't worked with any of them either.

Ubuntu does have an option to never turn the screen off, so an applet probably isn't too far off.

You know, I'm brainstorming this a little bit but if we knew what it is that toggles off the screen blanking adding it as a launcher probably isn't too far fetched. Not an applet, but almost as good.

---

### Post by kansasnoob on 2011-11-02
I haven't tried Caffeine since using it in Natty with Unity but I see they've made some headway with Oneiric:

[https://launchpad.net/~caffeine-developers/+archive/ppa](https://launchpad.net/~caffeine-developers/+archive/ppa)

If that works in the Unity "panel" I'd think we could figure out a way to port that to gnome-panel.

Just thinking out loud ATM, but my brain-fart may be someone else's brain-storm :D

---

### Post by cbowman57 on 2011-11-02
I'm switching to xscreensaver following these tips on Webupd8 [http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

then I'll try to install caffeine & see how it all works together.

---

### Post by kansasnoob on 2011-11-02
> **cbowman57 said:**
> I'm switching to xscreensaver following these tips on Webupd8 [http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

then I'll try to install caffeine & see how it all works together.

I'd done that in Oneiric but I'm going to try working through this with Precise. SABDFL chose the name and I plan to hammer the Canonical devs to truly make Precise live up to it's name :evil:

---

### Post by cbowman57 on 2011-11-02
Well caffeine does run in fallback mode on Precise, notification icon & everything.

Hammer'em til they give in. :)

---

### Post by kansasnoob on 2011-11-03
> **cbowman57 said:**
> Well caffeine does run in fallback mode on Precise, notification icon & everything.

Hammer'em til they give in. :)

How do you get Caffeine to run in gnome-panel :confused:

Or how do you access it in classic at all?

The best thing I've found so far is adding Sys settings to the panel, then selecting Screen and Never :)

---

### Post by kansasnoob on 2011-11-03
I'm also looking at ways to add a hardware temp applet back to the panel. Should be doable.

With that and a bit of theming what more could we ask for :lolflag:

---

### Post by cbowman57 on 2011-11-03
> **kansasnoob said:**
> How do you get Caffeine to run in gnome-panel :confused:

Or how do you access it in classic at all?

The best thing I've found so far is adding Sys settings to the panel, then selecting Screen and Never :)

In the preferences I toggled on Show tray icon, it automatically added itself to the panel.

---

### Post by lucazade on 2011-11-03
The readers of this thread might be interested in a small project I started lately.
It is a lightweight derivative of Ubuntu called Freezy that ships a classic panel setup among other cool features.

You can find more info in this support thread:
[http://ubuntuforums.org/showthread.php?t=1874552](http://ubuntuforums.org/showthread.php?t=1874552)

Nothing too serious, it is just for fun :D

---

### Post by kansasnoob on 2011-11-03
> **lucazade said:**
> The readers of this thread might be interested in a small project I started lately.
It is a lightweight derivative of Ubuntu called Freezy that ships a classic panel setup among other cool features.

You can find more info in this support thread:
[http://ubuntuforums.org/showthread.php?t=1874552](http://ubuntuforums.org/showthread.php?t=1874552)

Nothing too serious, it is just for fun :D

That looks really cool :)

I'll definitely be giving it a spin soon.

---

### Post by kansasnoob on 2011-11-03
> **cbowman57 said:**
> In the preferences I toggled on Show tray icon, it automatically added itself to the panel.

Bravo. I added the Oneiric version of Caffeine from:

[https://launchpad.net/~caffeine-developers/+archive/ppa](https://launchpad.net/~caffeine-developers/+archive/ppa)

Caffeine prefs shows up in "Other" in the app menu, so I chose to show in panel and viola:

[ATTACH]206222[/ATTACH]

Seems to work quite well :D

---

### Post by cbowman57 on 2011-11-03
> **kansasnoob said:**
> Bravo. I added the Oneiric version of Caffeine from:

[https://launchpad.net/~caffeine-developers/+archive/ppa]("https://launchpad.net/%7Ecaffeine-developers/+archive/ppa")

Seems to work quite well :D

It's always a plus when that happens. :)

---

### Post by effenberg0x0 on 2011-11-03
If possible, it would be nice it this thread was set as a sticky. Therefore every user that enter U+1 to express his desire to disable the launcher and get himself a more customizable and traditional session would have a chance to see that not only it is doable, but it is being done and also how to do it. He would see the pics you already posted of it, etc. I know not everyone reads stickies but....it's an attempt. Just a suggestion, of course.

---

### Post by cariboo on 2011-11-03
I'll just remove off topic posts, like the one above yours.

---

### Post by kansasnoob on 2011-11-03
> **cariboo907 said:**
> I'll just remove of topic posts, like the one above yours.

I'd like to add;

As close as I am to an acceptable "classic" look ATM I certainly plan on pursuing this further but my time at the desk will be limited for a few weeks so don't be surprised if I disappear for days at a time.

Just today I saw that Pinguy is planning a "Mate" release, and Mint has suggested the same. My goal is to show that neither is truly necessary :D

IMHO it's much better to tweak Ubuntu, hopefully very little as I've shown here. But this early in Precise dev things could, and likely will, blow up overnight :lolflag:

I've spent a little time already trying to find how to change the scrollbar (not overlay-scrollbar) color and font because I'm otherwise very happy with the overall look.

---

### Post by cariboo on 2011-11-03
+1, I feel the effort being put into Mate, is misplaced, if the effort was put into improving gnome classic, I think that would make everyone that won't use unity happy.

---

### Post by kansasnoob on 2011-11-04
Wow! As mentioned in post #8, step #2:

> I was very surprised here, no top &#8220;unity panel&#8221; after removing the top gnome-panel as I had in Oneiric.

I was very surprised today when I installed Oneiric, totally updated it, but **[COLOR="Red"]did not upgrade it to Precise[/COLOR]**, and I had no lingering unity top-panel :)

Some might think this is off-topic, but I specifically need to test differences as they occur in Precise. So I need a stable install to use as a baseline ;)

Specifically I needed to test this:

[https://launchpad.net/indicator-sysmonitor/+download](https://launchpad.net/indicator-sysmonitor/+download)

I can't get it to work in Precise so I needed to check out Ubuntu Oneiric :)

I also need to figure out update notifications. I run Ubuntu Oneiric 2D on one of my machines and I notice that even security updates seem to NOT show up like I think they should.

To clarify that; I use Lubuntu Oneiric on one machine but Ubuntu Oneiric-2D on another .......... I basically only know when security updates are available in the Ubuntu-2D DE by clicking on the goofy little "show me everything" icon in the top "unity panel that's not really a panel", or watching the Lubuntu install and just knowing that the same updates must be available for Ubuntu.

And, yes, I realize that must be a bug. But it's not one I'm willing to pursue ATM. I'm just one human being and I can only do so much!

Anyway I'm setting up a hopefully stable Oneiric classic w/o effects as a baseline for comparisons, but I don't feel it's stable enough to write a how-to.

But it looks pretty good.

---

### Post by cbowman57 on 2011-11-04
Just installed it to Precise, works without a problem.

[https://launchpad.net/indicator-sysmonitor/+download](https://launchpad.net/indicator-sysmonitor/+download)

* was running the wrong indicator, results the same as kansasnoob, failed to work.

---

### Post by kansasnoob on 2011-11-04
> **cbowman57 said:**
> Just installed it to Precise, works without a problem

[https://launchpad.net/indicator-sysmonitor/+download](https://launchpad.net/indicator-sysmonitor/+download)

Then it must be a conflict with something else I'd installed, or maybe my hardware :confused:

---

### Post by cbowman57 on 2011-11-04
> **kansasnoob said:**
> Then it must be a conflict with something else I'd installed, or maybe my hardware :confused:

Just wanted to rule out 12.04 for you.  I used the one at the top of the page, 0.3.9 in case maybe there is a difference between our versions.

---

### Post by kansasnoob on 2011-11-04
No good here.The best I can get is a borked icon with either no prefs dialogue or a dialogue that refuses to accept the proper sensor from lm-sensors :(

[ATTACH]206354[/ATTACH]

Absolutely can't select that sensor :confused:

---

### Post by cbowman57 on 2011-11-04
I was in error, that doesn't look like the one I ended up with, which is apparently the default system monitor indicator.

I just double checked & launched it from the menu.  Same result as yours, unable to activate any sensors & just a big red X in the panel.

---

### Post by lucazade on 2011-11-05
Indicator Applet has been ported to Gnome-Panel GTK3
[http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html](http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html)

I'm trying that out and are working great..

---

### Post by kansasnoob on 2011-11-05
> **cbowman57 said:**
> I was in error, that doesn't look like the one I ended up with, which is apparently the default system monitor indicator.

I just double checked & launched it from the menu.  Same result as yours, unable to activate any sensors & just a big red X in the panel.

That confused me at first also. System Monitor Indicator is sort of an unfortunate name as it's easily confused with System Monitor, and the two actually do quite different things.

I did read through some older bug reports and Ubuntu Answers, and I may file a bug report. But I see lucazade has a suggestion so I'm gonna check that out first :)

---

### Post by kansasnoob on 2011-11-05
I posted a question about indicator-sysmonitor here:

[https://answers.launchpad.net/indicator-sysmonitor/+question/177633](https://answers.launchpad.net/indicator-sysmonitor/+question/177633)

---

### Post by philinux on 2011-11-05
Interesting option.

[http://www.omgubuntu.co.uk/2011/11/unity-bliss-an-alternative-application-lens-for-ubuntu/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2011/11/unity-bliss-an-alternative-application-lens-for-ubuntu/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by robert shearer on 2011-11-06
> **philinux said:**
> Interesting option.

[http://www.omgubuntu.co.uk/2011/11/unity-bliss-an-alternative-application-lens-for-ubuntu/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2011/11/unity-bliss-an-alternative-application-lens-for-ubuntu/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

So this is an option for Unity...? and what relevance does it have to  Gnome **Classic** Megathread ??

Sorry, Phil but you've lost me here....:)
Maybe you meant to post to the...
[http://ubuntuforums.org/showthread.php?t=1695432](http://ubuntuforums.org/showthread.php?t=1695432)

---

### Post by jebus_beler on 2011-11-06
I already started a post here:

[http://ubuntuforums.org/showthread.php?t=1876469](http://ubuntuforums.org/showthread.php?t=1876469)

but now I think it would have been better to just ask in this thread since people seem to be experts.  For various reasons i need to ditch Unity and go back to Gnome classic.  I'm using the "Gnome Classics" option in lightdm, not the "Gnome Classics (no effects)" so I think this should be a compositing interface but I see no evidence of 3d effects.  Any idea why?  I also can't use compiz-setings-manager to configure anything.  

I'm mostly just interested in restoring usability effects such as alt-tab switchers, maybe expose, a desktop grid, etc...

To rephrase:  what WM is Gnome Classic using?  Metacity, compiz or a dumbed down Gnome 3?  How can I configure it  - shortcuts, etc..?  Ideally I would like 3d effects but failing that even a way to configure metacity (really, still??) would work for now.  Right now to switch between windows I have to use the task bar :-(

many thanks!

EDIT: I checked the process list and I am using metacity.  Why would it do that even when i chose to use gnome-classic not gnome-class without effects (from the lightdm window).  Is lightdm misconfigured?

---

### Post by cbowman57 on 2011-11-06
[COLOR=LightBlue][COLOR=DarkOrange]Original comment deleted[/COLOR].
[/COLOR]

---

### Post by lucazade on 2011-11-06
> **cbowman57 said:**
> Gnome 3 does not work with compiz.

Why do you say that?
Gnome3 works with compiz.. it is just gnome-shell that can't use compiz because it use Mutter.

I'd like to remember that Unity3D, Unity2D and Gnome-Fallback are Gnome3.
Gnome3 doesn't mean Gnome-shell.

---

### Post by cbowman57 on 2011-11-06
Just perpetuating an untruth I guess, I'll revise my post.

Not sure where I got that impression but if classic can also handle compiz it will make a lot of people very happy.

(I know my way around the shell pretty well, still trying to learn what I can about classic modes)

---

### Post by kansasnoob on 2011-11-06
ATM my greatest concern is how update notifications are handled. Knowing that such things are often borked in development releases I installed a fresh Oneiric, left it with the default Unity DE, and posted a query here:

[http://ubuntuforums.org/showthread.php?t=1876157](http://ubuntuforums.org/showthread.php?t=1876157)

I do realize that this changed as far back as Jaunty (if memory serves correctly) but with Gnome 2 we could get notifications back with:

```
gconftool-2 -s -t boolean /apps/update-notifier/auto_launch false
```

But not with Gnome 3 :(

OTOH that's not really any more of a problem with classic than with Unity, but from everything I've read that's a design decision - not a bug. Can't really say I understand that reasoning, I like to see when security updates are available as soon as they're available.

Not sure if anyone else has figured out how to display update notifications in a retro fashion or not, but it never hurts to ask :)

But beyond that I wanted to try and find a way of getting the Menu and Button icons back, along with showing mounted volumes on the desktop without installing 'gnome-tweak-tool' which installs a lot of unneeded dependencies as I showed in post #8.

The old gconf tweaks DON'T work:

```
gconftool-2 -s -t boolean /desktop/gnome/interface/buttons_have_icons true
gconftool-2 -s -t boolean /desktop/gnome/interface/menus_have_icons true
gconftool-2 -s -t boolean /apps/nautilus/desktop/volumes_visible true
```

But I did find that ubuntu-tweak does work:

Tweaks tab > Miscellaneous > Check both "Menus have icons" and "Buttons have icons"

Tweaks tab > Desktop icon settings > Check "Show mounted volumes on desktop"

It can also be used to move the titlebar button layout, and I have no real objection to using ubuntu-tweak, I mean it can be a very handy tool, but I find with many users offering too many "tweaks" in a GUI app can lead to disaster.

So I wonder if anyone knows how to get the Menu and Button icons back, and get the desktop to show mounted volumes without installing either 'ubuntu-tweak' or 'gnome-tweak-tool'?

Note: editing gconf does still work ATM for moving the titlebar button layout.

---

### Post by sgage on 2011-11-06
> **jebus_beler said:**
> I already started a post here:

[http://ubuntuforums.org/showthread.php?t=1876469](http://ubuntuforums.org/showthread.php?t=1876469)

but now I think it would have been better to just ask in this thread since people seem to be experts.  For various reasons i need to ditch Unity and go back to Gnome classic.  I'm using the "Gnome Classics" option in lightdm, not the "Gnome Classics (no effects)" so I think this should be a compositing interface but I see no evidence of 3d effects.  Any idea why?  I also can't use compiz-setings-manager to configure anything.  

I'm mostly just interested in restoring usability effects such as alt-tab switchers, maybe expose, a desktop grid, etc...

To rephrase:  what WM is Gnome Classic using?  Metacity, compiz or a dumbed down Gnome 3?  How can I configure it  - shortcuts, etc..?  Ideally I would like 3d effects but failing that even a way to configure metacity (really, still??) would work for now.  Right now to switch between windows I have to use the task bar :-(

many thanks!

EDIT: I checked the process list and I am using metacity.  Why would it do that even when i chose to use gnome-classic not gnome-class without effects (from the lightdm window).  Is lightdm misconfigured?

I am experiencing the same thing - haven't had a chance to look into it much yet. In the meantime, you can always run...

```
compiz --replace
```

Works fine here.

---

### Post by kansasnoob on 2011-11-06
> **jebus_beler said:**
> I already started a post here:

[http://ubuntuforums.org/showthread.php?t=1876469](http://ubuntuforums.org/showthread.php?t=1876469)

but now I think it would have been better to just ask in this thread since people seem to be experts.  For various reasons i need to ditch Unity and go back to Gnome classic.  I'm using the "Gnome Classics" option in lightdm, not the "Gnome Classics (no effects)" so I think this should be a compositing interface but I see no evidence of 3d effects.  Any idea why?  I also can't use compiz-setings-manager to configure anything.  

I'm mostly just interested in restoring usability effects such as alt-tab switchers, maybe expose, a desktop grid, etc...

To rephrase:  what WM is Gnome Classic using?  Metacity, compiz or a dumbed down Gnome 3?  How can I configure it  - shortcuts, etc..?  Ideally I would like 3d effects but failing that even a way to configure metacity (really, still??) would work for now.  Right now to switch between windows I have to use the task bar :-(

many thanks!

EDIT: I checked the process list and I am using metacity.  Why would it do that even when i chose to use gnome-classic not gnome-class without effects (from the lightdm window).  Is lightdm misconfigured?

I'm focusing solely on "classic w/o effects" ATM so I can't help with the compiz issue, but I typed a procedure in post# 8. I've repeated that process several times now without fail :)

But I'm currently trying to find a CLI way of being able to skip step #4 (installing ‘gnome-tweak-tool’) because it pulls in a load of unneeded dependencies for my purposes. 

I have found that the Oneiric alpha version of Ubuntu Tweak works as detailed in post #50 to get the Menu and Button icons back, and get the desktop to show mounted volumes, rather than having to install 'gnome-tweak-tool'.

Sorry I can't help with the compiz issue :(

---

### Post by cbowman57 on 2011-11-06
Doesn't ubuntu-tweak require compiz as a dependency?

---

### Post by lucazade on 2011-11-06
> **cbowman57 said:**
> Just perpetuating an untruth I guess, I'll revise my post.

Not sure where I got that impression but if classic can also handle compiz it will make a lot of people very happy.

(I know my way around the shell pretty well, still trying to learn what I can about classic modes)

ahaha ok.. no problem ;)

---

### Post by kansasnoob on 2011-11-06
> **cbowman57 said:**
> Doesn't ubuntu-tweak require compiz as a dependency?

The only things I've used it for so far are:

Tweaks tab > Miscellaneous > Check both "Menus have icons" and "Buttons have icons"

Tweaks tab > Desktop icon settings > Check "Show mounted volumes on desktop"

Tweaks tab > Window manager settings > Select "Window Titlebar Button Layout" > Right

And that's in a "classic w/o effects" session.

---

### Post by jebus_beler on 2011-11-06
> **kansasnoob said:**
> I'm focusing solely on "classic w/o effects" ATM so I can't help with the compiz issue, but I typed a procedure in post# 8. I've repeated that process several times now without fail :)


Thanks kansasnoob...will check it.  I have the feeling that dconf-editor should help since it works with unity 2d but installing it and checking it seems to have tons of options and I don't see an obvious one to e.g. configure alt-tab behaviour (now I'm thinking of just the 2d part of things).

I can switch to compiz as sgage suggested but I'm having suspend/resume problems which may be Unity or compiz related so for now I might just switch to 2d.  I guess I should look at your instructions kasnasnoob to see how to get it configured.  I don't really mind having a lot of packages installed.

---

### Post by cbowman57 on 2011-11-06
The reason I brought that up is that I install from mini.iso so I don't get any unity/compiz mixed in with my Gnome, so if I were to install ubuntu-tweak it would bring in compiz as a dependency.

I've used ubuntu-tweak until recently but out of curiousity, what tweaks does it do that gnome-tweak-tool doesn't?

---

### Post by kansasnoob on 2011-11-06
> **jebus_beler said:**
> Thanks kansasnoob...will check it.  I have the feeling that dconf-editor should help since it works with unity 2d but installing it and checking it seems to have tons of options and I don't see an obvious one to e.g. configure alt-tab behaviour (now I'm thinking of just the 2d part of things).

I can switch to compiz as sgage suggested but I'm having suspend/resume problems which may be Unity or compiz related so for now I might just switch to 2d.  I guess I should look at your instructions kasnasnoob to see how to get it configured.  I don't really mind having a lot of packages installed.

I also tried browsing through dconf-editor but I'm not smart enough to know what I'm doing :redface:

---

### Post by jebus_beler on 2011-11-06
> **kansasnoob said:**
> I'm focusing solely on "classic w/o effects" ATM so I can't help with the compiz issue, but I typed a procedure in post# 8. I've repeated that process several times now without fail :)

But I'm currently trying to find a CLI way of being able to skip step #4 (installing ‘gnome-tweak-tool’) because it pulls in a load of unneeded dependencies for my purposes. 

I have found that the Oneiric alpha version of Ubuntu Tweak works as detailed in post #50 to get the Menu and Button icons back, and get the desktop to show mounted volumes, rather than having to install 'gnome-tweak-tool'.

Sorry I can't help with the compiz issue :(

Kansasnoob I looked at your post but I'm not too worried about a lot of the issues you mentioned (i.e. inconsistent scrollbar, etc...).  I would like a coretmp and cpu monitor applet but these are not urgent as I'm using gkrellm (but if you figure it out I'd love to hear about it).

But its not clear to me from your post -- do you know how to configure keyboard shortcuts?  This is the most urgent thing for me.  I want to get alt-tab to work normally.  Now alt-ctrl-tab alternatives between the destkop and three panels but doesn't access my windows.  I didn't install all the debs in you mentioned in some of your earlier steps (gnome-panel, etc...) --- are those necessary for that?

---

### Post by kansasnoob on 2011-11-06
> **jebus_beler said:**
> Kansasnoob I looked at your post but I'm not too worried about a lot of the issues you mentioned (i.e. inconsistent scrollbar, etc...).  I would like a coretmp and cpu monitor applet but these are not urgent as I'm using gkrellm (but if you figure it out I'd love to hear about it).

But its not clear to me from your post -- do you know how to configure keyboard shortcuts?  This is the most urgent thing for me.  I want to get alt-tab to work normally.  Now alt-ctrl-tab alternatives between the destkop and three panels but doesn't access my windows.  I didn't install all the debs in you mentioned in some of your earlier steps (gnome-panel, etc...) --- are those necessary for that?

I'm still looking into a decent replacement for the 'gnome-sensors-applet'. No luck yet.

AFAIK the Gnome devs took the "one size fits all" approach regarding keyboard shortcuts:

[http://live.gnome.org/GnomeShell/CheatSheet](http://live.gnome.org/GnomeShell/CheatSheet)

Sort of like the old joke about Burger King's "have it your way" ads:

"You'll get it my way or no way at all"!

That seems to be more and more where Gnome and Ubuntu are both headed, **[COLOR="Red"]but[/COLOR]** I've discussed this with a few Linux "old-timers" and I understand this is quite typical from time to time as development progresses.

I guess the newest KDE was kind of the same way, don't know from personal experience though. But while looking for answers to my recent concern about update notifications I ran across this:

[http://www.webupd8.org/2011/10/configurable-notifyosd-notifications.html](http://www.webupd8.org/2011/10/configurable-notifyosd-notifications.html)

I argued (even with SABDLF himself) long ago that if Ubuntu didn't make 'notify-osd' configurable someone else would :D

I'm just glad Ubuntu has classic w/o effects working as well as they do.

---

### Post by kansasnoob on 2011-11-06
> **cbowman57 said:**
> The reason I brought that up is that I install from mini.iso so I don't get any unity/compiz mixed in with my Gnome, so if I were to install ubuntu-tweak it would bring in compiz as a dependency.

I've used ubuntu-tweak until recently but out of curiousity, what tweaks does it do that gnome-tweak-tool doesn't?

Ubuntu-tweak may have other options but it does nothing I need it to do that 'gnome-tweak-tool' does not do. I'm just trying to avoid the inclusion of all these dependencies:

> Step #4:

Since I find it useful, I also installed ‘gnome-tweak-tool’, but it does pull in a lot of other “junk”:

caribou
cups-pk-helper
gir1.2-accountsservice-1.0
gir1.2-caribou-1.0
gir1.2-clutter-1.0
gir1.2-cogl-1.0
gir1.2-coglpango-1.0
gir1.2-folks-0.6
gir1.2-gee-1.0
gir1.2-gkbd-3.0
gir1.2-json-1.0
gir1.2-mutter-3.0
gir1.2-networkmanager-1.0
gir1.2-polkit-1.0
gir1.2-telepathyglib-0.12
gir1.2-telepathylogger-0.2
gir1.2-upowerglib-1.0
gjs
gnome-icon-theme-full
gnome-shell
gnome-themes-standard
gnome-tweak-tool
libcaribou0
libclutter-1.0-0
libclutter-1.0-common
libcogl-common
libcogl-pango0
libcogl5
libgjs0c
libmozjs185-1.0
libmutter0
mesa-utils
mutter-common


From installing 'ubuntu-tweak' apt log shows:

> Start-Date: 2011-11-06  07:08:31
Commandline: apt-get install ubuntu-tweak
Install: gir1.2-unique-3.0:i386 (3.0.0-1ubuntu1, automatic), ubuntu-tweak:i386 (0.6.0-0~20111104~oneiric1), python-compizconfig:i386 (0.9.5.94-0ubuntu2, automatic), python-central:i386 (0.6.17, automatic)
End-Date: 2011-11-06  07:08:47

And I plan to continue testing only 'classic w/o effects' after installing a fresh Ubuntu from CD (soon to be DVD) or USB as I think that's where most people will start from ;)

I'm particularly concerned about the 10.04 LTS upgrades to 12.04 LTS. I imagine we'll hear a lot of complaining, so I want to have as simple of a plan (maybe a how-to) as possible to ease folks into the transition :)

I'd greatly prefer being able to change the "menus and buttons have icons" and "desktop shows mounted volumes" options without installing anything, just as I can edit the button layout with one simple command :D

---

### Post by cbowman57 on 2011-11-06
> **kansasnoob said:**
> I'd greatly prefer being able to change the "menus and buttons have icons" and "desktop shows mounted volumes" options without installing anything, just as I can edit the button layout with one simple command :D

Pretty sure it can be done with the dconf-editor that's packaged with dconf-tools (not sure if that's automatically included with a standard install or not)

Not sure how you'd do it from command line.

[ATTACH]206517[/ATTACH]    [ATTACH]206518[/ATTACH]

---

### Post by kansasnoob on 2011-11-06
> **cbowman57 said:**
> Pretty sure it can be done with the dconf-editor that's packaged with dconf-tools (not sure if that's automatically included with a standard install or not)

Not sure how you'd do it from command line.

[ATTACH]206517[/ATTACH]    [ATTACH]206518[/ATTACH]

Did you see my reply here:

[http://ubuntuforums.org/showpost.php?p=11431342&postcount=58](http://ubuntuforums.org/showpost.php?p=11431342&postcount=58)

> I also tried browsing through dconf-editor but I'm not smart enough to know what I'm doing 

Obviously the developer of 'ubuntu-tweak' knows what to change :D

---

### Post by cbowman57 on 2011-11-06
That's why I answered you in pictures.  :)

---

### Post by kansasnoob on 2011-11-06
> **cbowman57 said:**
> That's why I answered you in pictures.  :)

But I would think "show desktop icons" would give me more than I want, but I'll have a play-around session soon to see what happens :guitar:

I'm using the last good weather (for a while) day to do some of those "must-be-done" outdoor projects ;)

Between the lot of us I'm sure we'll figure this out. I've also been looking at psensor's config files to see if it couldn't be used as a viable replacement for 'gnome-sensors-applet'.

With so many great minds (mine is not one of them) coming together we'll find a way :D

---

### Post by cbowman57 on 2011-11-06
I'm a little curious as to the difference between w/ & w/out effects.

In w/out effects I'm able to toggle on things like compositing & reduced resources, which seems to perk things up some but might run counter to the w/out effects goal of this thread.

Oh yeah, within a couple months all the little tweaks we're frantically searching for will become common  knowledge. I have a feeling that Gnome 3 development is going to be much faster than it was with Gnome 2.

---

### Post by robert shearer on 2011-11-06
Re getting the desktop to show mounted volumes see...
[http://ubuntuforums.org/showpost.php?p=11339507&postcount=2](http://ubuntuforums.org/showpost.php?p=11339507&postcount=2)

This worked for me on a new install without any tweak tools or dconf editor.

cheers, Bob.

---

### Post by cbowman57 on 2011-11-06
> **robert shearer said:**
> Re getting the desktop to show mounted volumes see...
[http://ubuntuforums.org/showpost.php?p=11339507&postcount=2](http://ubuntuforums.org/showpost.php?p=11339507&postcount=2)

This worked for me on a new install without any tweak tools or dconf editor.

```

     gsettings set org.gnome.nautilus.desktop volumes-visible false 
    
     gsettings set org.gnome.nautilus.desktop volumes-visible true 
```cheers, Bob.

@kansasnoob, there's a good start for your installation script.

---

### Post by kansasnoob on 2011-11-06
> **robert shearer said:**
> Re getting the desktop to show mounted volumes see...
[http://ubuntuforums.org/showpost.php?p=11339507&postcount=2](http://ubuntuforums.org/showpost.php?p=11339507&postcount=2)

This worked for me on a new install without any tweak tools or dconf editor.

cheers, Bob.

Awesome! That even gives me some ideas about the other two :)

I don't care much if I blow up an installation, I mean I've been iso-testing for about 3 1/2 years, so reinstalling is almost fun ............ err, until I find a bug :(

But I never mind blowing up an installation :lolflag:

Although I did once hose a 22" widescreen monitor testing some xorg changes and that was a bit troubling :(

---

### Post by High Roller on 2011-11-07
Hi folks!

This article mentions Gnome 3 Fallback as potentially having a short shelf life.

[GNOME Shell Works Without GPU Driver Support]("http://www.phoronix.com/scan.php?page=news_item&px=MTAxMjI")

> Killing The GNOME3 Fall-Back?

As has been discussed in the past few days since the announcement of the milestone, once the latest Gallium3D LLVMpipe support is widespread and delivering decent performance, this may limit the life of GNOME developers maintaining the GNOME3 fall-back.

As said by Red Hat's Adam Williamson on the Fedora mailing list, "That's really a policy decision for the GNOME / Fedora desktop teams, not for ajax. But based on what they've said in the past, I expect that once most hardware that previously needed the fallback mode is covered, fallback mode will die. AIUI, fallback mode isn't meant to be a GNOME 2-by-stealth for Shell refuseniks, it's purely an attempt to accommodate hardware which doesn't support Shell." 

---

### Post by effenberg0x0 on 2011-11-07
Considering that many people point out that using a hardware accelerated desktop is providing them with a non-fluid experience, due to their GPU/RAM limitations, I wonder what the impacts of software rendering will be. Some GPU = Bad Experience. No GPU = Worse experience. 

Gallium3D/LLVM seem to be an amazing project for fast enough multi-core cpus, with enough RAM and, weirdly, a bad embedded GPU. A very specific situation, right?

Maybe (and I still doubt it) on a i7 / Phenom II X6 with enough RAM it will eventually beat a week motherboard embedded GPU performance. But it probably has it's weight on the performance of standard PCs, laptops, etc. I wouldn't bet on it as a good alternative for accelerated graphics on outdated hardware.

---

### Post by kansasnoob on 2011-11-07
> **High Roller said:**
> Hi folks!

This article mentions Gnome 3 Fallback as potentially having a short shelf life.

[GNOME Shell Works Without GPU Driver Support]("http://www.phoronix.com/scan.php?page=news_item&px=MTAxMjI")

I doubt they'll kill it before the release of 12.04 LTS though and, unless there are huge changes in the next few months, this appears to be a fairly simple project ;)

---

### Post by jfernyhough on 2011-11-07
Edited. I read the article.

---

### Post by kansasnoob on 2011-11-07
I managed to get the update notifications back in gnome-panel:

[ATTACH]206577[/ATTACH]

With this command:

```
gsettings set com.ubuntu.update-notifier auto-launch false
```

It's a bit different because the little notify icon with the + mark opens the pictured window when clicked, then clicking on the X in the upper right hand corner closes the little white notification but the typical update-notification remains.

Although, come to think of it, I'd previously also tried:

```
gconftool-2 -s -t boolean /apps/update-notifier/auto_launch false
```

I've been playing with this install a lot, so it's time for a fresh install to try things from scratch ;)

BTW that's in "Indicator Applet", I haven't tried with 'Indicator Applet Complete' yet.

---

### Post by kansasnoob on 2011-11-07
> **robert shearer said:**
> Re getting the desktop to show mounted volumes see...
[http://ubuntuforums.org/showpost.php?p=11339507&postcount=2](http://ubuntuforums.org/showpost.php?p=11339507&postcount=2)

This worked for me on a new install without any tweak tools or dconf editor.

cheers, Bob.

This helped me a lot :)

I now know how to structure the commands for editing dconf, so I can poke around and break all kinds of stuff ;)

---

### Post by kansasnoob on 2011-11-07
> **kansasnoob said:**
> I managed to get the update notifications back in gnome-panel:

[ATTACH]206577[/ATTACH]

With this command:

```
gsettings set com.ubuntu.update-notifier auto-launch false
```

It's a bit different because the little notify icon with the + mark opens the pictured window when clicked, then clicking on the X in the upper right hand corner closes the little white notification but the typical update-notification remains.

Although, come to think of it, I'd previously also tried:

```
gconftool-2 -s -t boolean /apps/update-notifier/auto_launch false
```

I've been playing with this install a lot, so it's time for a fresh install to try things from scratch ;)

BTW that's in "Indicator Applet", I haven't tried with 'Indicator Applet Complete' yet.

Wow! This even works in Unity:

```
gsettings set com.ubuntu.update-notifier auto-launch false
```

I was surprised:

[ATTACH]206596[/ATTACH]

---

### Post by ventrical on 2011-11-07
> **kansasnoob said:**
> I doubt they'll kill it before the release of 12.04 LTS though and, unless there are huge changes in the next few months, this appears to be a fairly simple project ;)


 If worse comes to worse  - on weaker machines - one can always use FVWM-Crystal from the repos.  It's not like end_users with legacy dated harware  are locked out or anything like that.

---

### Post by kansasnoob on 2011-11-07
Golly, gosh, gee whiz, I'm getting pretty close (until Precise updates break everything). Where I'm at right now:

Install 'gnome-session-fallback':

```
sudo apt-get install gnome-session-fallback
```

Set lightdm to boot classic w/o effects:

```
sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-fallback
```

Then reboot. After that you might like to axe the overlay-scrollbars, if so:

```
sudo apt-get purge liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0 overlay-scrollbar
```

Note: you may have to log out and log back in before you see a full change there.

Do you want the window buttons on the right? If so run:

```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"
```

How about putting the menu and button icons back? Easy:

```
gsettings set org.gnome.desktop.interface menus-have-icons true
```

```
gsettings set org.gnome.desktop.interface buttons-have-icons true
```

Now, getting the desktop to handle things properly again is a bit more complex, but not much. Start with:

```
gsettings set org.gnome.desktop.background show-desktop-icons true
```

But that will likely show 'mounted volumes' + computer, home, and trash icons. Which do you want to show? I want only mounted volumes so I run:

```
gsettings set org.gnome.nautilus.desktop volumes-visible true
```

```
gsettings set org.gnome.nautilus.desktop computer-icon-visible false
```

```
gsettings set org.gnome.nautilus.desktop home-icon-visible false
```

```
gsettings set org.gnome.nautilus.desktop trash-icon-visible false
```

Note: the obvious difference is "true" and "false" :)

Now let's get some update notifications back in "Indicator Applet":

```
gsettings set com.ubuntu.update-notifier auto-launch false
```

And we can get a decent replacement for the old inhibit applet from Caffeine:

[https://launchpad.net/~caffeine-developers/+archive/ppa](https://launchpad.net/~caffeine-developers/+archive/ppa)

In my small world that leaves two problems:

#1: Finding a decent replacement for the 'gnome-sensors-applet'.

#2: Fixing the theme so the standard scrollbars match the window decoration color.

We can do this, eh?

---

### Post by kansasnoob on 2011-11-07
One other thing I want to make perfectly clear here;

Yes, I'm pursuing "classic w/o effects", but that's just my preference.

If anyone cares to pursue classic with compiz here they're more than welcome to do so :D

No single person "owns" any thread at the forums as far as I know and I'm sure that this thread is open to all "Classic" talk, or anything even slightly related.

My personal goals are to pull this off with minimal effort, specifically NOT having to install a load of stuff from PPA's although that may be unavoidable.

---

### Post by sgage on 2011-11-07
Does anyone have any real information as to the future of "Gnome Classic"? Is this something that will continue to evolve, or is it going to be dropped by the wayside?

---

### Post by cbowman57 on 2011-11-07
> **sgage said:**
> Does anyone have any real information as to the future of "Gnome Classic"? Is this something that will continue to evolve, or is it going to be dropped by the wayside?

I've read that Gnome classic will eventually go away after the video requirements of the shell are reduced.

---

### Post by sgage on 2011-11-07
> **cbowman57 said:**
> I've read that Gnome classic will eventually go away after the video requirements of the shell are reduced.

That is unfortunate. Have you been paying any attention to the news from Linux Mint, that they are developing Gnome Shell Extensions that pretty much duplicate the old-school interface? I wonder how that will work out...

---

### Post by robert shearer on 2011-11-07
OK, I don't know if this still persists with PP  ??? (as I cannot get it to install...) but assuming the slow shutdown is still a problem (compared to Natty and earlier) then...
```
gksudo gedit /etc/init/network-manager.conf
```

and add this line..

[COLOR="Purple"]stop on runlevel [06][/COLOR]

so it looks like this..
```
# network-manager - network connection manager
#
# The Network Manager daemon manages the system's network connections,
# automatically switching between the best available.

description	"network connection manager"

start on (local-filesystems
	  and started dbus)
stop on stopping dbus
stop on runlevel [06]
expect fork
respawn

exec NetworkManager
```

 and reboot.

(credit to lucazade.  [http://ubuntuforums.org/showpost.php?p=11317331&postcount=25](http://ubuntuforums.org/showpost.php?p=11317331&postcount=25))

cheers, Bob.

---

### Post by kansasnoob on 2011-11-07
I think the only thing that matters ATM is whether the classic fall-back will disappear before 12.04 LTS is released :D

If we can come up with a decent fall-back for 12.04 I think that will give us a lot of time to develop gnome-shell extensions and/or give Canonical time to rethink Unity as it's sole DE ;)

Patience truly is a virtue.

---

### Post by kansasnoob on 2011-11-07
> **robert shearer said:**
> OK, I don't know if this still persists with PP  ??? (as I cannot get it to install...) but assuming the slow shutdown is still a problem (compared to Natty and earlier) then...
```
gksudo gedit /etc/init/network-manager.conf
```

and add this line..

[COLOR="Purple"]stop on runlevel [06][/COLOR]

so it looks like this..
```
# network-manager - network connection manager
#
# The Network Manager daemon manages the system's network connections,
# automatically switching between the best available.

description	"network connection manager"

start on (local-filesystems
	  and started dbus)
stop on stopping dbus
stop on runlevel [06]
expect fork
respawn

exec NetworkManager
```

 and reboot.

(credit to lucazade.  [http://ubuntuforums.org/showpost.php?p=11317331&postcount=25](http://ubuntuforums.org/showpost.php?p=11317331&postcount=25))

cheers, Bob.

I've had no trouble at all with networking or getting connected, but I'm using a simple wired network with a $30 Trendnet Router, no wireless at all.

---

### Post by lucazade on 2011-11-07
> **robert shearer said:**
> OK, I don't know if this still persists with PP  ??? (as I cannot get it to install...) but assuming the slow shutdown is still a problem (compared to Natty and earlier) then...
```
gksudo gedit /etc/init/network-manager.conf
```

and add this line..

[COLOR="Purple"]stop on runlevel [06][/COLOR]

so it looks like this..
```
# network-manager - network connection manager
#
# The Network Manager daemon manages the system's network connections,
# automatically switching between the best available.

description	"network connection manager"

start on (local-filesystems
	  and started dbus)
stop on stopping dbus
stop on runlevel [06]
expect fork
respawn

exec NetworkManager
```

 and reboot.

(credit to lucazade.  [http://ubuntuforums.org/showpost.php?p=11317331&postcount=25](http://ubuntuforums.org/showpost.php?p=11317331&postcount=25))

cheers, Bob.

I don't have PP because installed so I can't confirm that workaround it is still necessary.
In oneiric i use it to shutdown network services "correctly" and to improve shutdown time.

---

### Post by robert shearer on 2011-11-07
> **kansasnoob said:**
> I've had no trouble at all with networking or getting connected, but I'm using a simple wired network with a $30 Trendnet Router, no wireless at all.

No, I am referring to **slow shutdown/reboot times** where that config file causes the pause.
> * Asking all remaining processes to terminate... [OK]
* Killing all remaining processes... [fail]

not related to hardware or wireless but to config file.

The workaround quoted speeds up shutdown and reboot.
Thought you might like to try it...:)

---

### Post by kansasnoob on 2011-11-07
> **robert shearer said:**
> No, I am referring to **slow shutdown/reboot times** where that config file causes the pause.


not related to hardware or wireless but to config file.

The workaround quoted speeds up shutdown and reboot.
Thought you might like to try it...:)

Sorry, I wasn't paying adequate attention.

But I have no problem with shutdown, restart, or cold start. Things are super fast.

On my media box I'm using an old IDE drive and even it boots in about 50 seconds. On my work box with SATA 3 the boot time is under 30 seconds.

---

### Post by robert shearer on 2011-11-07
Fine, I am going to try another daily of PP and see if that will install.
If it does I look forward to such quickness as you have...:D

and will try the fix quoted otherwise.;)

(I only have IDE... truly ancient hardware all round hence the interest in fallback...)

Though the fix is for slow **shutdown** (and shutdown **before** rebooting) and **not the boot up times**.
Oneric without the fix took several seconds more than Natty.
With the amended config it shuts down before I can vacate my chair. (Both me and the hardware can be slow sometimes..:)

---

### Post by kansasnoob on 2011-11-07
> **robert shearer said:**
> Fine, I am going to try another daily of PP and see if that will install.
If it does I look forward to such quickness as you have...:D

and will try the fix quoted otherwise.;)

(I only have IDE... truly ancient hardware all round hence the interest in fallback...)

The dailies are borked using "something else", aka: manual partitioning:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/885654](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/885654)

---

### Post by robert shearer on 2011-11-07
> **kansasnoob said:**
> The dailies are borked using "something else", aka: manual partitioning:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/885654](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/885654)

Thanks !  you've saved me some bandwidth. I was just about to download but this is the problem I have been having...
Unfortunately both my machines are multi-boot so manual partitioning is what I need.
Guess I will wait a little longer..

---

### Post by cbowman57 on 2011-11-07
> **sgage said:**
> That is unfortunate. Have you been paying any attention to the news from Linux Mint, that they are developing Gnome Shell Extensions that pretty much duplicate the old-school interface? I wonder how that will work out...

Works quite well.   [ATTACH]206620[/ATTACH]

---

### Post by kansasnoob on 2011-11-07
Got a reply regarding System Monitor Indicator:

[https://answers.launchpad.net/indicator-sysmonitor/+question/177633](https://answers.launchpad.net/indicator-sysmonitor/+question/177633)

Someone else has it working in Oneiric so I must just be messing up some where :(

Hopefully someone will help walk me through it.

---

### Post by robert shearer on 2011-11-07
The old system monitor ??? alt-right click and add to panel.

The new indicator-multiload  ??? (Looks like the old system monitor, however, clicking it gives a menu showing usage stats in real time)

```
sudo apt-get install indicator-multiload
```

Appears in  Applications>System tools>System load indicator.
Navigate there then click on it's entry and it appears in the panel. Then right click on its panel icon and use preferences.

Or have I got the wrong thing ?? (Done on Oneric as I wait for PP)

EDIT, the only drawback seems to be that it does not scale to the panel.

Interesting thread....[http://ubuntuforums.org/showthread.php?t=1877099](http://ubuntuforums.org/showthread.php?t=1877099)
Interesting port....[http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html](http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html)

---

### Post by kansasnoob on 2011-11-08
> **robert shearer said:**
> The old system monitor ??? alt-right click and add to panel.

The new indicator-multiload  ??? (Looks like the old system monitor, however, clicking it gives a menu showing usage stats in real time)

```
sudo apt-get install indicator-multiload
```

Appears in  Applications>System tools>System load indicator.
Navigate there then click on it's entry and it appears in the panel. Then right click on its panel icon and use preferences.

Or have I got the wrong thing ?? (Done on Oneric as I wait for PP)

EDIT, the only drawback seems to be that it does not scale to the panel.

Interesting thread....[http://ubuntuforums.org/showthread.php?t=1877099](http://ubuntuforums.org/showthread.php?t=1877099)
Interesting port....[http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html](http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html)

This is what I was talking about:

[https://launchpad.net/indicator-sysmonitor](https://launchpad.net/indicator-sysmonitor)

More links:

[http://www.webupd8.org/2011/03/system-monitor-indicator-puts-cpu-and.html](http://www.webupd8.org/2011/03/system-monitor-indicator-puts-cpu-and.html)

[https://answers.launchpad.net/indicator-sysmonitor/+question/157470](https://answers.launchpad.net/indicator-sysmonitor/+question/157470)

I posted a screenshot here:

[http://ubuntuforums.org/showthread.php?t=1873765&page=4](http://ubuntuforums.org/showthread.php?t=1873765&page=4)

I've just been installing by running:

```
sudo apt-add-repository ppa:alexeftimie/ppa && sudo apt-get update && sudo apt-get install indicator-sysmonitor
```

Then it shows up in Accessories, but all I get is a borked icon in the panel that allows me to open the actual System Monitor :confused:

What I want is to display system temp(s) in the panel like I could with gnome-sensors-applet :)

---

### Post by kansasnoob on 2011-11-08
Well that does at least show up in Unity:

[ATTACH]206661[/ATTACH]

Not getting the temp thing working ATM, but it would appear that it will not work with gnome-panel anyway :(

I'm now looking at:

[https://launchpad.net/indicator-sensors](https://launchpad.net/indicator-sensors)

More on that later :)

---

### Post by kansasnoob on 2011-11-08
OK, I have Hardware Sensors Indicator also working in Unity:

[ATTACH]206664[/ATTACH]

Now back to the panel :)

---

### Post by kansasnoob on 2011-11-08
Need to use some of the forums space to post a screenshot of Hardware Sensors Indicator (aka indicator-sensors):

[ATTACH]206667[/ATTACH]

My question:

[https://answers.launchpad.net/indicator-sensors/+question/178033](https://answers.launchpad.net/indicator-sensors/+question/178033)

---

### Post by sgage on 2011-11-08
Hello Gnome Classic explorers!

Is there any way to get an incoming mail indicator in the system tray (this would be for Thunderbird? It would be a nice convenience, though I'm finding GC quite usable as-is.

Any pointers would be appreciated!

---

### Post by sgage on 2011-11-08
While I'm at it, how about a Rhythmbox indicator? That would be very nice!

[Edit: The Banshee indicator works, FYI.]

---

### Post by kansasnoob on 2011-11-08
I don't use Thunderbird or Rhythmbox but I wonder about this:

[http://ubuntuforums.org/showpost.php?p=11426920&postcount=41](http://ubuntuforums.org/showpost.php?p=11426920&postcount=41)

It didn't really suit my personal needs, but it looks pretty great :D

---

### Post by sgage on 2011-11-08
> **kansasnoob said:**
> I don't use Thunderbird or Rhythmbox but I wonder about this:

[http://ubuntuforums.org/showpost.php?p=11426920&postcount=41](http://ubuntuforums.org/showpost.php?p=11426920&postcount=41)

It didn't really suit my personal needs, but it looks pretty great :D

It's good enough! I get an "envelope" that turns green with incoming mail, and the volume indicator with the player controls in it.

Thanks for the heads up!

---

### Post by kansasnoob on 2011-11-08
I made some edits/additions to my questions about Hardware Sensors Indicator and System Monitor Indicator:

[https://answers.launchpad.net/indicator-sensors/+question/178033](https://answers.launchpad.net/indicator-sensors/+question/178033)

[https://answers.launchpad.net/indicator-sysmonitor/+question/177633](https://answers.launchpad.net/indicator-sysmonitor/+question/177633)

Can't hurt, eh?

---

### Post by kansasnoob on 2011-11-09
> **lucazade said:**
> Indicator Applet has been ported to Gnome-Panel GTK3
[http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html](http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html)

I'm trying that out and are working great..

I decided to have a look at the theme they were talking about this AM:

[ATTACH]206764[/ATTACH]

I sort of like that combination. The scrollbars are a bit easier for me to distinguish from the background, and they even darken when moused over.

And lightening the panel color makes most of the elements more distinguishable too.

It would be cool to have a list of where different themes could be downloaded from :)

---

### Post by cbowman57 on 2011-11-09
> **kansasnoob said:**
> I decided to have a look at the theme they were talking about this AM:

[ATTACH]206764[/ATTACH]

I sort of like that combination. The scrollbars are a bit easier for me to distinguish from the background, and they even darken when moused over.

And lightening the panel color makes most of the elements more distinguishable too.

It would be cool to have a list of where different themes could be downloaded from :)

Zukwito is in the Webupd8 ppa [http://www.webupd8.org/2011/03/announcing-webupd8-themes-ppa.html](http://www.webupd8.org/2011/03/announcing-webupd8-themes-ppa.html)

gnome-look.org is still a good resource [http://gnome-look.org/](http://gnome-look.org/)

* note * For Gnome classic modes you can use gkt3 & metacty themes

---

### Post by kansasnoob on 2011-11-09
> **cbowman57 said:**
> Zukwito is in the Webupd8 ppa [http://www.webupd8.org/2011/03/announcing-webupd8-themes-ppa.html](http://www.webupd8.org/2011/03/announcing-webupd8-themes-ppa.html)

gnome-look.org is still a good resource [http://gnome-look.org/](http://gnome-look.org/)

* note * For Gnome classic modes you can use gkt3 & metacty themes

Thanks for the tip about metacity :)

I'm still not quite in my happy spot but here's a blue on blue:

[ATTACH]206779[/ATTACH]

---

### Post by cbowman57 on 2011-11-09
No problem, it's nice to be able to mix gtk3 & metacity themes to get something that looks familiar.

Looks like you're well on your way to achieving that classic Gnome look.

---

### Post by kansasnoob on 2011-11-09
Oops, just noticed I butchered that screenshot a bit:

[ATTACH]206781[/ATTACH]

I wish I knew how to truly save a theme like this w/o the need to download a butt-load of packages :)

And it'd be cool in 'gnome-color-chooser' worked consistently with gnome3/gtk3 :)

---

### Post by kansasnoob on 2011-11-09
> **cbowman57 said:**
> No problem, it's nice to be able to mix gtk3 & metacity themes to get something that looks familiar.

Looks like you're well on your way to achieving that classic Gnome look.

I'm sort of scratching my head about why someone else didn't just do this :confused:

So many people are totally crapping the cage over Unity and/or gnome-shell, and it's not at all hard to do this :D

The two reasons I hadn't pursued it were:

(a) Simple time limitations that had nothing to do with computers.

(b) I devoted most of what little time I had to Lubuntu testing, and I plan on continuing that in Precise, particularly iso-testing.

No doubt there are some underlying problems like tweaking keyboard shortcuts, and getting compiz working, but I'll bet that's also doable :D

And just BTW, anyone should feel perfectly free to use anything they learn here and do as they please with it.

---

### Post by cariboo on 2011-11-09
> **kansasnoob said:**
> I'm sort of scratching my head about why someone else didn't just do this :confused:

So many people are totally crapping the cage over Unity and/or gnome-shell, and it's not at all hard to do this :D

The two reasons I hadn't pursued it were:

(a) Simple time limitations that had nothing to do with computers.

(b) I devoted most of what little time I had to Lubuntu testing, and I plan on continuing that in Precise, particularly iso-testing.

No doubt there are some underlying problems like tweaking keyboard shortcuts, and getting compiz working, but I'll bet that's also doable :D

And just BTW, anyone should feel perfectly free to use anything they learn here and do as they please with it.

I think many of the users that are complaining, really don't have a clue as to what they are doing, they installed a previous version, and it just worked, they haven't really learned anything about using a Linux distribution, and they are just using it the same way they used Windows.

The biggest problem is that Ubuntu has become to easy to use, and I would imagine that the most these users do is change the background picture, and maybe choose one of the available themes.

---

### Post by kansasnoob on 2011-11-11
Where I'm at ATM; I'm working on a single "copy-n-paste" command to flip Oneiric, and hopefully Precise, to classic w/o effects. I've tried this twice so far and it works fine, but I'd appreciate someone just copying it to gedit and having a peak, then making any suggestions:

```
sudo add-apt-repository ppa:jconti/gnome3 && sudo add-apt-repository ppa:caffeine-developers/ppa && sudo apt-get update && sudo apt-get install gnome-session-fallback caffeine indicator-applet indicator-applet-complete indicator-applet-session && sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-fallback && sudo apt-get purge liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0 overlay-scrollbar && gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close" && gsettings set org.gnome.desktop.interface menus-have-icons true && gsettings set org.gnome.desktop.interface buttons-have-icons true && gsettings set org.gnome.desktop.background show-desktop-icons true && gsettings set org.gnome.nautilus.desktop volumes-visible true && gsettings set org.gnome.nautilus.desktop computer-icon-visible false && gsettings set org.gnome.nautilus.desktop home-icon-visible false && gsettings set org.gnome.nautilus.desktop trash-icon-visible false && gsettings set com.ubuntu.update-notifier auto-launch false && gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true' && cp -a .config .config_OLD && cp -a .gconf .gconf_OLD && cp -a .gnome2 .gnome2_OLD
```

You have to confirm with enter or y + enter at four points (I sort of wish I could get it to just continue "quietly" with "yes" to all, but I don't know how):

> You are about to add the following PPA to your system:
 GNOME 3
 Ports of various applications to GNOME 3.
 More info: [https://launchpad.net/~jconti/+archive/gnome3](https://launchpad.net/~jconti/+archive/gnome3)
Press [ENTER] to continue or ctrl-c to cancel adding it

******

You are about to add the following PPA to your system:
 Caffeine
 The latest packages for Caffeine.


 More info: [https://launchpad.net/~caffeine-developers/+archive/ppa](https://launchpad.net/~caffeine-developers/+archive/ppa)
Press [ENTER] to continue or ctrl-c to cancel adding it

******

The following extra packages will be installed:
  alacarte gir1.2-panelapplet-4.0 gnome-applets gnome-applets-data gnome-panel
  gnome-panel-data gnome-session gnome-session-bin gnome-session-common
  libpanel-applet-4-0 libsqlite0 python-central python-gmenu python-kaa-base
  python-kaa-metadata python-sqlite python-xlib
Suggested packages:
  gnome-netstatus-applet deskbar-applet cpufrequtils evolution
  epiphany-browser desktop-base python-sqlite-dbg
The following NEW packages will be installed:
  alacarte caffeine gir1.2-panelapplet-4.0 gnome-applets gnome-applets-data
  gnome-panel gnome-panel-data gnome-session-fallback indicator-applet
  indicator-applet-complete indicator-applet-session libpanel-applet-4-0
  libsqlite0 python-central python-gmenu python-kaa-base python-kaa-metadata
  python-sqlite python-xlib
The following packages will be upgraded:
  gnome-session gnome-session-bin gnome-session-common
3 upgraded, 19 newly installed, 0 to remove and 198 not upgraded.
Need to get 10.5 MB/10.7 MB of archives.
After this operation, 46.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? 

******

The following packages will be REMOVED:
  liboverlay-scrollbar-0.2-0* liboverlay-scrollbar3-0.2-0* overlay-scrollbar*
0 upgraded, 0 newly installed, 3 to remove and 198 not upgraded.
After this operation, 307 kB disk space will be freed.
Do you want to continue [Y/n]? 


When the terminal output ends it's time to reboot. 

Note: if this was a fresh install and not yet updated you'll see the update-notification show up in the top Unity panel. You can either update now or after you reboot.

Then it just comes down to editing the panels as one wishes, going to Other > Caffeine preferences to set it up, and possibly disabling the Firefox and Thunderbird "Global Menu Bar integration extensions".

I've debated about just removing 'firefox-globalmenu' and 'thunderbird-globalmenu', not sure yet. That'd be easy to do.

Any thoughts?

After checking this out a bit more closely I think I'll do a "How I setup Oneiric classic w/o effects" thread in Main Support > Desktop Environments.

The only thing I dislike ATM is the color of the scrollbars, but all of the themes I've tried have certain flaws that I find worse than the default. Maybe someone will figure out how to change the scrollbar color to match the window decoration color consistently :)

Right now I'm going to type a "what this does" to explain what all that one command does. Posting stuff here at +1 is pretty safe because most of us do look before we leap, but not so in other parts of the forums ;)

---

### Post by leeper69 on 2011-11-11
Thanks for your thread kansasnoob it was vary helpful!

---

### Post by jerrrys on 2011-11-11
@kansasnoob

later today i will give your script a try on a minimal-fallback install.

use to be gnome-color-chooser would do wonders, but it no longer works in gtk3 and i have found no replacement for this great program

---

### Post by ronacc on 2011-11-11
copied and pasted your cmds from my precise gnome-shell 64bit install and on reboot selected gnome classic w/o effects , worked fine , looks good . Thanks !

---

### Post by kansasnoob on 2011-11-11
> **jerrrys said:**
> @kansasnoob

later today i will give your script a try on a minimal-fallback install.

use to be gnome-color-chooser would do wonders, but it no longer works in gtk3 and i have found no replacement for this great program

Not sure what you mean by "minimal". I've so far only tried this with a standard live-CD install of Oneiric, not a mini-iso.

And it's a bit problematic in Precise because you have to edit software sources to use some oneiric repos where necessary because not all precise repos are available yet :D

I'm still having trouble with the Precise iso's, not surprising at this stage of the game, so I'm still having to install Oneiric, then upgrade to Precise, then edit the "extras" repo source, then upgrade, ya-da, ya-da.

I hope no one gets over excited and starts advertising this just yet!

---

### Post by kansasnoob on 2011-11-11
I'm not nearly done, and I have to be away from the desk for a bit, but here's my "what the command does" explanation so far:

> Before you begin please understand that I'm no genius, far from it, but I wanted a Classic DE in Oneiric with the newest version of Gnome so I did some studying. **This is for "classic without effects" only!** I've never cared for compiz anyway and it seems to be difficult to get it to run in a classic Oneiric DE. So, **[COLOR="Red"]if you want compiz this thread is NOT for you[/COLOR]**, sorry.

Also, **[COLOR="Red"]there are no guarantees[/COLOR]**! I've tested this quite a bit, but only with fresh Oneiric installs. Your mileage may vary with installations that have other underlying problems. I can only say that it works for me, no more and no less.

Now, I have this reduced to one single command that you can "copy-n-paste" into gnome-terminal, but that comes after an explanation of what it does. **It's NOT a true script but rather just a bunch of commands strung together with 'space&&space'** like the typical 'sudo apt-get update && sudo apt-get upgrade'. So look at what it does a "chunk" at a time:

**First** it installs two PPA's:

[https://launchpad.net/~jconti/+archive/gnome3](https://launchpad.net/~jconti/+archive/gnome3)

[https://launchpad.net/~caffeine-developers/+archive/ppa](https://launchpad.net/~caffeine-developers/+archive/ppa)

The first allows you to add 'indicator-applet', 'indicator-applet-complete', and 'indicator-applet-session' to the panel applets displayed when you press Alt + right-click on a blank space in the panel to display "Add to panel". I personally only use 'indicator-applet' but your preferences may vary, the 'complete' version displays more notifications, such as mail.

The second allows you to install 'caffeine' which is a sweet replacement for the old 'gnome-inhibit-applet'. After completeing this and logging into the classic session you can setup Caffeine by going to Other > Caffeine preferences.

Screenshot of caffeine_prefs here.

**Second** it updates the package base and installs 'gnome-session-fallback', 'caffeine', 'indicator-applet', 'indicator-applet-complete', and 'indicator-applet-session'.

**Third** it sets lightdm to boot the classic w/o effects session by default.

**Fourth** it purges the overlay-scrollbars because I find them to be inconsistent and annoying in the classic DE.

**Fifth** it resets the window management buttons to the right side instead of the left.

**Sixth** it sets the desktop to display only mounted volumes. By default the desktop is not set to display anything. If you also want to display "Computer", "Home", or "Trash" on the desktop you'd need to run one of the commands in appendix #1 after this is all complete.

**Seventh** it sets the update-notifier to display in either 'indicator-applet' or 'indicator-applet-complete' as it used to, just because I like it that way.

**Eighth** it "kills" that "lock-screen" thing that requires you to enter a password after the screen-"blanker" activates. But the screen still does go black.

**Ninth**, and last, it backs up the new configuration files in Home > hidden so these "new" defaults can be "stored" and possibly restored if you totally break something down the road. You'd just need to rename any of the files with an "_OLD" suffix by removing only the "_OLD".



Of course "appendix #1" doesn't exist yet :)

Work in progress.

---

### Post by cbowman57 on 2011-11-11
Looking good kansasnoob.

As an aside, been checking out [Freezy linux]("http://freezylinux.altervista.org/"), for people wanting Gnome-fallback only (no shell or Unity) this is a good respin to start with.

---

### Post by ronacc on 2011-11-11
@ kansasnoob the 11/10 precise iso's installs work if you apply the fix in this thread post # 6 . [http://ubuntuforums.org/showthread.php?t=1874553 ](http://ubuntuforums.org/showthread.php?t=1874553 ) . that gets you past the partman lockup . I installed both lubuntu precise and ubuntu precise from them ( both 64 bit) .

edit: i applied you script to my ubuntu (gnome-shell) precise install , works good .

---

### Post by ronacc on 2011-11-11
oops , the ubuntu install is ok but the lubuntu install is locking up at "checking battery state" . I'm investigating now .

---

### Post by kansasnoob on 2011-11-11
> **cbowman57 said:**
> Looking good kansasnoob.

As an aside, been checking out [Freezy linux]("http://freezylinux.altervista.org/"), for people wanting Gnome-fallback only (no shell or Unity) this is a good respin to start with.

But Freezy doesn't use gnome-panel :)

---

### Post by lucazade on 2011-11-11
> **kansasnoob said:**
> But Freezy doesn't use gnome-panel :)

yes, it uses gnome-panel.
in first build I have temporary employed xfce4-panel because it allowed to use indicators... now that indicators are available for gnome-panel i've replaced xfce4-panel with gnome-panel itself ;)

---

### Post by kansasnoob on 2011-11-11
> **ronacc said:**
> @ kansasnoob the 11/10 precise iso's installs work if you apply the fix in this thread post # 6 . [http://ubuntuforums.org/showthread.php?t=1874553 ](http://ubuntuforums.org/showthread.php?t=1874553 ) . that gets you past the partman lockup . I installed both lubuntu precise and ubuntu precise from them ( both 64 bit) .

edit: i applied you script to my ubuntu (gnome-shell) precise install , works good .

Even with sparkers work-around I found it impossible to reliably install to anything but a blank drive and ATM I need to install reliably using the manual install method (stupidly named something else).

---

### Post by kansasnoob on 2011-11-11
> **lucazade said:**
> yes, it uses gnome-panel.
in first build I have temporary employed xfce4-panel because it allowed to use indicators... now that indicators are available for gnome-panel i've replaced xfce4-panel with gnome-panel itself ;)

Cool, when I tried it you were still using xfce4-panel. But I still prefer tweaking a default Ubuntu installation :)

That's just how I roll.

---

### Post by kansasnoob on 2011-11-11
I've added some stuff to my "what it does" regarding gnome-panel, etc:

> Before you begin please understand that I'm no genius, far from it, but I wanted a Classic DE in Oneiric with the newest version of Gnome so I did some studying. This is for "classic without effects" only! I've never cared for compiz anyway and it seems to be difficult to get it to run in a classic Oneiric DE. So, if you want compiz this thread is NOT for you, sorry.

Also, there are no guarantees! I've tested this quite a bit, but only with fresh Oneiric installs. Your mileage may vary with installations that have other underlying problems. I can only say that it works for me, no more and no less. And if you ask a question that's already answered in this thread I will get grumpy.

Now, I have this reduced to one single command that you can "copy-n-paste" into gnome-terminal, but that comes after an explanation of what it does. It's NOT a true script but rather just a bunch of commands strung together with 'space&&space' like the typical 'sudo apt-get update && sudo apt-get upgrade'. So look at what it does a "chunk" at a time:

First it installs two PPA's:

[https://launchpad.net/~jconti/+archive/gnome3](https://launchpad.net/~jconti/+archive/gnome3)

[https://launchpad.net/~caffeine-developers/+archive/ppa](https://launchpad.net/~caffeine-developers/+archive/ppa)

The first allows you to add 'indicator-applet', 'indicator-applet-complete', and 'indicator-applet-session' to the panel applets displayed when you press Alt + right-click on a blank space in the panel to display "Add to panel". I personally only use 'indicator-applet' but your preferences may vary, the 'complete' version displays more notifications, such as mail.

The second allows you to install 'caffeine' which is a sweet replacement for the old 'gnome-inhibit-applet'. After completing this and logging into the classic session you can setup Caffeine by going to Other > Caffeine preferences.

Screenshot of caffeine_prefs here.

Second it updates the package base and installs 'gnome-session-fallback', 'caffeine', 'indicator-applet', 'indicator-applet-complete', 'indicator-applet-session', and their dependencies. 

Third it sets lightdm to boot the classic w/o effects session by default.

Fourth it purges the overlay-scrollbars because I find them to be inconsistent and annoying in the classic DE.

Fifth it resets the window management buttons to the right side instead of the left.

Sixth it sets the desktop to display only mounted volumes. By default the desktop is not set to display anything. If you also want to display "Computer", "Home", or "Trash" on the desktop you'd need to run one of the commands in appendix #1 after this is all complete.

Seventh it sets the update-notifier to display in either 'indicator-applet' or 'indicator-applet-complete' as it used to, just because I like it that way.

Eighth it "kills" that "lock-screen" thing that requires you to enter a password after the screen-"blanker" activates. But the screen still does go black.

Ninth, and last, it backs up the new configuration files in Home > hidden so these "new" defaults can be "stored" and possibly restored if you totally break something down the road. You'd just need to rename any of the files with a "_OLD" suffix by removing only the "_OLD". More about that in appendix #2.

If you DO NOT want any of those things to happen this command is NOT for you! But I'll include a "one-step-at-a-time" list of commands in appendix #3.

********************************************************************************

Did you decide to go ahead? If so, once you've booted into the "new" classic desktop you'll notice that the menu(s) have changed! Yeah, maybe a bit, but you'll likely find what you want if you spend just a couple of minutes familiarizing yourself with the new menu layout, be sure to check the Other and System Tools categories.

But you also need to know that you now must hold down either Alt key while right-clicking on a panel or applet to be able to edit panel preferences or to add/edit/move/remove more applets. That was an intentional move by the Gnome devs.

And you also can't just add application applets by right-clicking it and selecting "add to panel". You must now open the "add-to-panel" window and selecting Application Launcher > Forward, then the window changes and you can click on the "bullet" to the left of each category to add any app in the menu to the panel.



No time for highlighting and such ATM.

I'll be back :)

---

### Post by kansasnoob on 2011-11-12
> **cbowman57 said:**
> Can't remember where I ran across this but you can try:

```
sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-fallback
sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-classic
sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-shell
```


[LIST=1]
[*]Gnome classic w/o effects
[*]Gnome classic
[*]Gnome shell
[/LIST]


*edited

I'm stuck on my "How I create a classic DE w/o effects" project because I also need to know how to set the Ubuntu & Ubuntu-2D sessions to boot as default :)

I must be able to return lightdm to it's default settings or provide info to boot the unity and unity-2D DE's.

I'm kind of anal retentive about specifics ;)

And I must be able to provide a method to revert :D

---

### Post by cbowman57 on 2011-11-12
Should be able to poke around in the ubuntu.desktop & ubuntu-2d.desktop (or whatever they are called) files & see what they execute.

That's my best guess anyway, I'd peek but I don't have unity.

---

### Post by effenberg0x0 on 2011-11-12
> **kansasnoob said:**
> I'm stuck on my "How I create a classic DE w/o effects" project because I also need to know how to set the Ubuntu & Ubuntu-2D sessions to boot as default :)

I must be able to return lightdm to it's default settings or provide info to boot the unity and unity-2D DE's.

I'm kind of anal retentive about specifics ;)

And I must be able to provide a method to revert :D

Hey Kansasnoob, I was thinking about it. 

- Many times you help someone at the forum and later you get a PM like "My dad/mom/teacher/boss/etc" is pissed at my changes and wants everything the way it was" lol. 

- I also though that maybe users will break the setup you propose accidentally, while performing future upgrades and installing softwares with other dependencies. How to keep the thing updated / working? (pin packages, etc)

- I've been learning that people not always can cut/paste a "one-liner" like the one you created without making mistakes and ending up with a partial thing, in a state that its hard for anyone to provide support (we can't, remotely, really understand the current state). Asking for logs is usually a joke.

If your project gets the popularity I think it will get, you'll see all of this plus people trying to run the script on RedHat, Windows, etc :) 

I was thinking that, maybe, you should PPA it as a script, that plans to deal with most situations you can think of (even if not all featured are immediately provided) and go working on it, getting supporters, etc. 

Then users can simply add the ppa, or replace all the command-line you created for something like "wget something.com/script.sh && chmod +x script.sh && sh script.sh". It is easier for them.

IMHO, I think the best option would be for you to put the thing on PPA, so you'll have the option to find collaborators to enhance / fix the script.

If you agree to this as an option, I have put together a basic script scope listing some functions that, once coded, could deal with some of the problematic situations. I use this scope at work, just made some adaptations for you. It is expected to provide options for support (auto catch / post logs), reinstall, uninstall/restore, auto-update, etc). If you want, I can help to code each of these functions, and others as you need them, but probably other supporters will help too.

It's just a suggestion /  scope anyway, if you feel that a script+ppa could be good. See what you think of it below.

```
#!/usr/bin/env bash -x
# Activates bash debug mode. Comment the following two lines before publishing
# releases.
set -x
set -v
###############################################################################
# Lines kept under 80 characters max for easier console editing! 
# Use hashes as guides on console / non-gui IDEs and editors. 
# Indentation = 4 spaces (no tabs).
###############################################################################
#
# classic_desktop.sh
#
# A script to safely implement a Classic Look to current Linux versions.
# 
# Kansasnoob et al <launchpad.net/~kansasnoob>, 2011
# Version 0.1, Nov. 2011
# Contributions by: 
#
#
#
#
#
#

###############################################################################
########## Changelog ##########################################################
###############################################################################
#
# 
#
#

###############################################################################
########## Usage ##############################################################
###############################################################################

###############################################################################
# USAGE: $classic_desktop {install | update | restore} {-f | -y | -v | -q | -d}
# EXAMPLE 1: $bash classic_ubuntu install
# EXAMPLE 2: #bash classic_ubuntu update
# EXAMPLE 3: $bash classic_ubuntu restore
#
# -f (--force): Disregards most error conditions and proceeds while possible.
#
# -y (--yes): Assumes "yes" to questions, where possible. Is also activated 
#             when users chooses -q (--quiet) mode.
#
# -v (--verbose): Outputs all messages to stdout and the log file. Useful for 
#                 advanced users.
#
# -q (--quiet): Supresses messages as much as possible. Auto activates the -y 
#               (--yes) option.
#
# -d (--debug): Prints debug information both to stdout and the log file.
#
###############################################################################

###############################################################################
########## Debug ##############################################################
###############################################################################
# An option to run the script in debug mode is added internally, as well as 
# defined as a command-line arumment. It also allows us to customize the debug
# mode.
###############################################################################

DEBUG=
DEBUG_MODE=

###############################################################################
########## Version Control#####################################################
###############################################################################
# We must try to stop users from attempting to use outdated script versions
# in their systems and auto-download up-to-date versions, unless the user uses
# a "force switch" in the command line. We must also know from where to 
# download an updated script version, if one is needed.
###############################################################################

SW_VERSION=
SW_HOST=

###############################################################################
########## Restrictions #######################################################
###############################################################################
# Applying some rules for restrictions is a good idea, as some users may 
# attempt to run this script in unsupported systems / versions. As far as we
# increase the user base, information regarding fixes for other platforms will
# be provided, which will change this restrictions.
###############################################################################

OS_ACCEPT=
OS_ACCEPT_VERSION=

###############################################################################
########## Basic Requirements #################################################
###############################################################################
# Some global options to make sure the script will work. A typical example is
# when users do not have proper $PATH or other environment variables. Another
# is that we have to make sure that basic commands we use will be available
# (e.g. apt, sed, which, awk, etc).
# We can store this requirements here and check/apply fixes to have them 
# available later, if needed.
##############################################################################
 
REQUIRED_PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/sbin:/bin
DISPLAY=
REQUIRED_CMDS=

##############################################################################
########## Internal Files ####################################################
##############################################################################
# Define the names and paths we will use exclusively to store information 
# for the script: log, backups, etc.  
##############################################################################

SW_DIR=
BACKUP_DIR=
LOG_FILE=

##############################################################################
########## Packages Sources ##################################################
##############################################################################
# Define the standard and alternate sources (repos, PPAs and standard hosts)
# to be used by the application in order to obtain the software needed. 
##############################################################################

REPO_SOURCES=
PPA_SOURCES=
INET_SOURCES=

CONFLICTING_REPO_SOURCES=
CONFLICTING_PPA_SOURCES=
CONFLICTING_INET_SOURCES=

##############################################################################
########## Packages###########################################################
##############################################################################
# Define the packages and files required by the script to achieve its goals,
# as well as those that will be removed. Some may need to be pinned, to avoid
# misconfiguration in upcoming system updates.
##############################################################################

REQUIRED_PACKAGES=
REQUIRED_INET_FILES= 

REMOVE_PACKAGES=
REMOVE_FILES=

PIN_PACKAGES=
FREEZE_FILES=

##############################################################################
########## Settings ##########################################################
##############################################################################
# Define the changes to system settings (gconf, gconf, gsettings, other config
# files) to be performed by the script in order to reach its objective. 
##############################################################################

DCONF_SETTINGS=
GCONF_SETTINGS=
GSETTING_SETTINGS=
CONFIG_FILES_SETTINGS=


##############################################################################
########## Functions #########################################################
##############################################################################
# All functions are inserted below in the order they should be ran in the case
# of a "install", the core-function ot the script (except for main). 
##############################################################################
 
function logger {
    DEBUG_ERROR=ERROR_AT_LOGGER
    # Simple function to enable logging and debugging output.
    # L1: screen only
    # L2: screen and log file
    # L3: L1+L2 + debug messages (if debugging is set to "on")
    LOG_LEVEL=$1
    LOG_MESSAGE=$2
    NOW=[$(date +%d/%m/%y_%H:%M:%S)]
    if [ -z $LOG_MESSAGE ]; then
        if [ $1 == "L1" ]; then
            echo "$2"
        else
            if [ $1 == "L2" ]; then
                if [ ! -e $LOG_FilE ]; then
                    echo "Internal error. $DEBUG_ERROR. Exiting..."
                    exit 1
                fi
            echo "$2"
            echo "${NOW} $2" >> $LOG_FILE
            else
                if [ $1 == "L3" -a $DEBUG== "on" ]; then
                    if [ ! -e $LOG_FilE ]; then
                    echo "Internal error. $DEBUG_ERROR. Exiting..."
                    exit 1
                fi
            echo "[Debug] $2"
            echo "[Debug] ${NOW} $2" >> $LOG_FILE
            fi
        fi
    fi
}

function pre_install {
    DEBUG_ERROR=ERROR_AT_PRE_INSTALL
    logger L3 "Entered pre_install"
    # It would be nice to do some basic checks before doing anything else. For
    # example, if the user is on a notebook, is there an acceptable amount of
    # energy, or is it on AC? 
    # TODO: *
    logger L2 "Performing basic verification in your system."
    logger L3 "Exiting pre_install"
}

function install_script {
    DEBUG_ERROR=ERROR_AT_INSTALL_SCRIPT
    logger L3 "Entered install_script"
    # Creates the script directory in user $HOME to host logs, backups, downloads,
    # etc
    # TODO: 
    # Check $USER and its $HOME permissions
    # Check for previously installed instances (avoid overwrites, loss of backups, etc)
    # Create program directory at user $HOME
    # Touch/Prepare requires files
    # Update crontab
    logger L2 "Installing Classic Desktop"
    logger L3 "Exiting install_script"
}

function check_inet {
    DEBUG_ERROR=ERROR_AT_CHECK_INET
    logger L3 "Entered check_inet"
    # Checks for a viable Internet Connection. If one is not found, attempts some
    # fixes to enable it.
    # TODO: *
    logger L3 "Exiting check_inet"
}

function check_sw_version {
    DEBUG_ERROR=ERROR_AT_CHECK_SW_VERSION
    logger L3 "Entered check_sw_version"
    # Checks online for a more recent version of the script. 
    # TODO: *
    logger L3 "Exiting chceck_sw_version"
}

function download_software {
    DEBUG_ERROR=ERROR_AT_DOWNLOAD_SOFTWARE
    logger L3 "Entered download_software"
    # Downloads a more recent version of the script. 
    # TODO: *
    logger L3 "Exiting download_software"
}

function display_changelog {
    DEBUG_ERROR=ERROR_AT_DISPLAY_CHANGELOG
    logger L3 "Entered display_changelog"
    # Shows the script changelog in case of an automatic update 
    # TODO: *
    logger L3 "Exiting display_changelog"
}


function check_restrictions {
    DEBUG_ERROR=ERROR_AT_CHECK_RESTICTIONS
    logger L3 "Entered check_restrictions"
    # Checks user system for the restrictions previously defined
    # TODO: *
    logger L3 "Exiting check_restrictions"
}

function check_requirements {
    DEBUG_ERROR=ERROR_AT_CHECK_REQUIREMENTS
    logger L3 "Check requirements"
    # Checks user system for the requirements previously defined
    # Attempts fixes when possible.
    # TODO: *
    logger L3 "Exiting check_requirements"
}

function check_required_sources {
    DEBUG_ERROR=ERROR_AT_CHECK_REQUIRED_SOURCES
    logger L3 "Entered check_requirements"
    # Checks if required sources are already configured, in which case they
    # shouldn't be readded. 
    # TODO: *
    logger L3 "Exiting check_required_sources"
}

function check_conflicting_sources {
    DEBUG_ERROR=ERROR_AT_CHECK_CONFLICTING_SOURCES
    logger L3 "Entering check_conflicting files"
    # Checks if conflicting sources are configured, in which case they must be
    # disabled.
    # TODO: *
    logger L3 "Exiting check_conflicting_sources"
}

function check_local_packages {
    DEBUG_ERROR=ERROR_AT_CHECK_LOCAL_PACKAGES
    logger L3 "Entered check_local_packages"
    # Checks if all or some of the required packages are already available, 
    # reducing the need for download / wasted bandidth for user and hosts.
    # TODO: *
    logger L3 "Exiting check_local_Packages"
}

function check_remote_packages {
    DEBUG_ERROR=ERROR_AT_CHECK_REMOTE_PACKAGES
    logger L3 "Entered check_remote_packages"
    # Checks if required remote packages are available at predefined sources. 
    # TODO: *
    logger L3 "Exiting check_remote_packages"
}

function simulate_packages_install {
    DEBUG_ERROR=ERROR_AT_SIMULATE_PACKAGES_INSTALL
    logger L3 "Entered simulate_packages_install"
    # Updates the list of packages to be installed considering dependencies.
    # Updates the list of removed packages (stored at the backup files).
    # TODO: *
    logger L3 "Exiting simulate_packages_install"
}

function prepare_system {
    DEBUG_ERROR=ERROR_AT_PREPARE_SYSTEM
    logger L3 "Entered prepare_system"
    # It's a good idea to check if the user is running processes that are needed or
    # that might interfere with the script processes (e.g. having more than one X 
    # has a lock in apt, etc).
    # TODO: *
    logger L3 "Exiting prepare_system"
}

function settings_backup {
    DEBUG_ERROR=ERROR_AT_SETTINGS_BACKUP
    logger L3 "Entered settings_backup"
    # Make dated backups of the settings files mentioned earlier in the pre-defined
    # backup location. 
    # TODO: *
    logger L3 "Exiting settings_backup"
}

function change_settings {
    DEBUG_ERROR=ERROR_AT_CHANGE_SETTINGS
    logger L3 "Entered change_settings"
    # Makes the pre-defined changes to configuration files.
    # TODO: *
    logger L3 "Exiting change_settings"
}

function install_packages {
    DEBUG_ERROR=ERROR_AT_INSTALL_PACKAGES
    logger L3 "Entered install_packages"
    # Installs all required packages
    # TODO: *
    logger L3 "Exiting install_packages"
}

function remove_packages {
    DEBUG_ERROR=ERROR_AT_REMOVE_PACKAGES
    logger L3 "Entered remove_packages"
    # Removes unneeded packages
    # TODO: *
    logger L3 "Exiting remove_packages"
}

function pin_packages {
    DEBUG_ERROR=ERROR_AT_PIN_PACKAGES
    logger L3 "Entered pin_packages"
    # Some packages may need to be "pinned" as well as sosme configuration files
    # may need to be frozen, to avoid misconfiguration in upcoming system updates.
    # TODO: *
    logger L3 "Exiting remove_packages"
}

function post_install {
    DEBUG_ERROR=ERROR_AT_POST_INSTALL
    logger L3 "Entered post_install"
    # Procedures to be executed after all the previous steps have been succesful.
    # Might include restart X, pop a dialog, reboot, etc.
    # TODO: *
    logger L3 "Exiting post_install"
}

function gather_support_information {
    DEBUG_ERROR=ERROR_AT_GATHER_SUPPORT_INFORMATION
    logger L3 "Entered gather_support_information"
    # Collects relevant information from user system and the script log and prepare
    # it to be posted at the support forum
    # TODO: *
    logger L3 "Exiting gather_support_information"
}

function publish_support_information {
    DEBUG_ERROR=ERROR_AT_PUBLISH_SUPPORT_INFORMATION
    logger L3 "Entered publish_support_information"
    # Publish relevant support information in the correct way (using code tags, 
    # etc), in the correct place (specific forum section) to enhance chances of 
    # user receiving adequate support.
    # TODO: *
    logger L3 "Exiting publish_support_information"
}

function main {
    DEBUG_ERROR=ERROR_AT_MAIN
    logger L3 "Entered main"
    # Invokes functions depending on command-line arguments and return codes.
    # TODO: *
    MAIN_ARG=$1
    detect_player
    do_cmd $MAIN_ARG
    logger L3 "Exiting main"
    exit 0
}

##############################################################################
########## End of Functions: Do not add functions below ######################
##############################################################################

##############################################################################
########## Command-line parser ###############################################
##############################################################################
# Although the use of getopts is not mandatory, it is adopted to support
# nested arguments like -fqy and parse them in a proper way. The script must
# take incoherent attempts and incompatible sets of arguments under 
# consideration and deal with it somehow.
##############################################################################
#
# Todo (Add Options for the implemented functions - as they are created/tested)
while getopts ":i" opt; do
  case $opt in
    a)
      echo "Selected Install!" >&2
      ;;
    \?)
      echo "Invalid option: -$OPTARG" >&2
      ;;
  esac
done

```

---

### Post by mc4man on 2011-11-12
> **kansasnoob said:**
> I'm stuck on my "How I create a classic DE w/o effects" project because I also need to know how to set the Ubuntu & Ubuntu-2D sessions to boot as default :)

I must be able to return lightdm to it's default settings or provide info to boot the unity and unity-2D DE's.

I'm kind of anal retentive about specifics ;)

And I must be able to provide a method to revert :D

Those commands (sudo /usr/lib/lightdm/lightdm-set-defaults -s ....) write to /etc/lightdm/lightdm.conf

But the setting in there is only used for autologin, if you boot to the login screen then whatever session is set in ~/.dmrc is what will be set on the greeter by 'default'

To further muddle that, at least here, if there are multiple user accounts & one is set to autologin then that's what happens on boot up - goes directly to that user

If more than one user is set to autologin then I believe it's 'last to set the autologin' option becomes the user booted to or restarted to, ( as in only 1 user can autologin at a time

You may be better off looking at writing a new session value to ~/.dmrc

unity3d is ubuntu
unity-2d is ubuntu-2d

---

### Post by ranch hand on 2011-11-13
> **mc4man said:**
> Those commands (sudo /usr/lib/lightdm/lightdm-set-defaults -s ....) write to /etc/lightdm/lightdm.conf

But the setting in there is only used for autologin, if you boot to the login screen then whatever session is set in ~/.dmrc is what will be set on the greeter by 'default'

To further muddle that, at least here, if there are multiple user accounts & one is set to autologin then that's what happens on boot up - goes directly to that user

If more than one user is set to autologin then I believe it's 'last to set the autologin' option becomes the user booted to or restarted to, ( as in only 1 user can autologin at a time

You may be better off looking at writing a new session value to ~/.dmrc

unity3d is ubuntu
unity-2d is ubuntu-2d
I would get the thing set the way you want it and then put everything from your ~/.relevant files in /etc/skel.  They are not ".hidden" files in /etc/skel.

That way it should give the same desktop to all users.

---

### Post by kansasnoob on 2011-11-13
> **effenberg0x0 said:**
> Hey Kansasnoob, I was thinking about it. 

- Many times you help someone at the forum and later you get a PM like "My dad/mom/teacher/boss/etc" is pissed at my changes and wants everything the way it was" lol. 

- I also though that maybe users will break the setup you propose accidentally, while performing future upgrades and installing softwares with other dependencies. How to keep the thing updated / working? (pin packages, etc)

- I've been learning that people not always can cut/paste a "one-liner" like the one you created without making mistakes and ending up with a partial thing, in a state that its hard for anyone to provide support (we can't, remotely, really understand the current state). Asking for logs is usually a joke.

If your project gets the popularity I think it will get, you'll see all of this plus people trying to run the script on RedHat, Windows, etc :) 

I was thinking that, maybe, you should PPA it as a script, that plans to deal with most situations you can think of (even if not all featured are immediately provided) and go working on it, getting supporters, etc. 

Then users can simply add the ppa, or replace all the command-line you created for something like "wget something.com/script.sh && chmod +x script.sh && sh script.sh". It is easier for them.

IMHO, I think the best option would be for you to put the thing on PPA, so you'll have the option to find collaborators to enhance / fix the script.

If you agree to this as an option, I have put together a basic script scope listing some functions that, once coded, could deal with some of the problematic situations. I use this scope at work, just made some adaptations for you. It is expected to provide options for support (auto catch / post logs), reinstall, uninstall/restore, auto-update, etc). If you want, I can help to code each of these functions, and others as you need them, but probably other supporters will help too.

It's just a suggestion /  scope anyway, if you feel that a script+ppa could be good. See what you think of it below.

```
#!/usr/bin/env bash -x
# Activates bash debug mode. Comment the following two lines before publishing
# releases.
set -x
set -v
###############################################################################
# Lines kept under 80 characters max for easier console editing! 
# Use hashes as guides on console / non-gui IDEs and editors. 
# Indentation = 4 spaces (no tabs).
###############################################################################
#
# classic_desktop.sh
#
# A script to safely implement a Classic Look to current Linux versions.
# 
# Kansasnoob et al <launchpad.net/~kansasnoob>, 2011
# Version 0.1, Nov. 2011
# Contributions by: 
#
#
#
#
#
#

###############################################################################
########## Changelog ##########################################################
###############################################################################
#
# 
#
#

###############################################################################
########## Usage ##############################################################
###############################################################################

###############################################################################
# USAGE: $classic_desktop {install | update | restore} {-f | -y | -v | -q | -d}
# EXAMPLE 1: $bash classic_ubuntu install
# EXAMPLE 2: #bash classic_ubuntu update
# EXAMPLE 3: $bash classic_ubuntu restore
#
# -f (--force): Disregards most error conditions and proceeds while possible.
#
# -y (--yes): Assumes "yes" to questions, where possible. Is also activated 
#             when users chooses -q (--quiet) mode.
#
# -v (--verbose): Outputs all messages to stdout and the log file. Useful for 
#                 advanced users.
#
# -q (--quiet): Supresses messages as much as possible. Auto activates the -y 
#               (--yes) option.
#
# -d (--debug): Prints debug information both to stdout and the log file.
#
###############################################################################

###############################################################################
########## Debug ##############################################################
###############################################################################
# An option to run the script in debug mode is added internally, as well as 
# defined as a command-line arumment. It also allows us to customize the debug
# mode.
###############################################################################

DEBUG=
DEBUG_MODE=

###############################################################################
########## Version Control#####################################################
###############################################################################
# We must try to stop users from attempting to use outdated script versions
# in their systems and auto-download up-to-date versions, unless the user uses
# a "force switch" in the command line. We must also know from where to 
# download an updated script version, if one is needed.
###############################################################################

SW_VERSION=
SW_HOST=

###############################################################################
########## Restrictions #######################################################
###############################################################################
# Applying some rules for restrictions is a good idea, as some users may 
# attempt to run this script in unsupported systems / versions. As far as we
# increase the user base, information regarding fixes for other platforms will
# be provided, which will change this restrictions.
###############################################################################

OS_ACCEPT=
OS_ACCEPT_VERSION=

###############################################################################
########## Basic Requirements #################################################
###############################################################################
# Some global options to make sure the script will work. A typical example is
# when users do not have proper $PATH or other environment variables. Another
# is that we have to make sure that basic commands we use will be available
# (e.g. apt, sed, which, awk, etc).
# We can store this requirements here and check/apply fixes to have them 
# available later, if needed.
##############################################################################
 
REQUIRED_PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/sbin:/bin
DISPLAY=
REQUIRED_CMDS=

##############################################################################
########## Internal Files ####################################################
##############################################################################
# Define the names and paths we will use exclusively to store information 
# for the script: log, backups, etc.  
##############################################################################

SW_DIR=
BACKUP_DIR=
LOG_FILE=

##############################################################################
########## Packages Sources ##################################################
##############################################################################
# Define the standard and alternate sources (repos, PPAs and standard hosts)
# to be used by the application in order to obtain the software needed. 
##############################################################################

REPO_SOURCES=
PPA_SOURCES=
INET_SOURCES=

CONFLICTING_REPO_SOURCES=
CONFLICTING_PPA_SOURCES=
CONFLICTING_INET_SOURCES=

##############################################################################
########## Packages###########################################################
##############################################################################
# Define the packages and files required by the script to achieve its goals,
# as well as those that will be removed. Some may need to be pinned, to avoid
# misconfiguration in upcoming system updates.
##############################################################################

REQUIRED_PACKAGES=
REQUIRED_INET_FILES= 

REMOVE_PACKAGES=
REMOVE_FILES=

PIN_PACKAGES=
FREEZE_FILES=

##############################################################################
########## Settings ##########################################################
##############################################################################
# Define the changes to system settings (gconf, gconf, gsettings, other config
# files) to be performed by the script in order to reach its objective. 
##############################################################################

DCONF_SETTINGS=
GCONF_SETTINGS=
GSETTING_SETTINGS=
CONFIG_FILES_SETTINGS=


##############################################################################
########## Functions #########################################################
##############################################################################
# All functions are inserted below in the order they should be ran in the case
# of a "install", the core-function ot the script (except for main). 
##############################################################################
 
function logger {
    DEBUG_ERROR=ERROR_AT_LOGGER
    # Simple function to enable logging and debugging output.
    # L1: screen only
    # L2: screen and log file
    # L3: L1+L2 + debug messages (if debugging is set to "on")
    LOG_LEVEL=$1
    LOG_MESSAGE=$2
    NOW=[$(date +%d/%m/%y_%H:%M:%S)]
    if [ -z $LOG_MESSAGE ]; then
        if [ $1 == "L1" ]; then
            echo "$2"
        else
            if [ $1 == "L2" ]; then
                if [ ! -e $LOG_FilE ]; then
                    echo "Internal error. $DEBUG_ERROR. Exiting..."
                    exit 1
                fi
            echo "$2"
            echo "${NOW} $2" >> $LOG_FILE
            else
                if [ $1 == "L3" -a $DEBUG== "on" ]; then
                    if [ ! -e $LOG_FilE ]; then
                    echo "Internal error. $DEBUG_ERROR. Exiting..."
                    exit 1
                fi
            echo "[Debug] $2"
            echo "[Debug] ${NOW} $2" >> $LOG_FILE
            fi
        fi
    fi
}

function pre_install {
    DEBUG_ERROR=ERROR_AT_PRE_INSTALL
    logger L3 "Entered pre_install"
    # It would be nice to do some basic checks before doing anything else. For
    # example, if the user is on a notebook, is there an acceptable amount of
    # energy, or is it on AC? 
    # TODO: *
    logger L2 "Performing basic verification in your system."
    logger L3 "Exiting pre_install"
}

function install_script {
    DEBUG_ERROR=ERROR_AT_INSTALL_SCRIPT
    logger L3 "Entered install_script"
    # Creates the script directory in user $HOME to host logs, backups, downloads,
    # etc
    # TODO: 
    # Check $USER and its $HOME permissions
    # Check for previously installed instances (avoid overwrites, loss of backups, etc)
    # Create program directory at user $HOME
    # Touch/Prepare requires files
    # Update crontab
    logger L2 "Installing Classic Desktop"
    logger L3 "Exiting install_script"
}

function check_inet {
    DEBUG_ERROR=ERROR_AT_CHECK_INET
    logger L3 "Entered check_inet"
    # Checks for a viable Internet Connection. If one is not found, attempts some
    # fixes to enable it.
    # TODO: *
    logger L3 "Exiting check_inet"
}

function check_sw_version {
    DEBUG_ERROR=ERROR_AT_CHECK_SW_VERSION
    logger L3 "Entered check_sw_version"
    # Checks online for a more recent version of the script. 
    # TODO: *
    logger L3 "Exiting chceck_sw_version"
}

function download_software {
    DEBUG_ERROR=ERROR_AT_DOWNLOAD_SOFTWARE
    logger L3 "Entered download_software"
    # Downloads a more recent version of the script. 
    # TODO: *
    logger L3 "Exiting download_software"
}

function display_changelog {
    DEBUG_ERROR=ERROR_AT_DISPLAY_CHANGELOG
    logger L3 "Entered display_changelog"
    # Shows the script changelog in case of an automatic update 
    # TODO: *
    logger L3 "Exiting display_changelog"
}


function check_restrictions {
    DEBUG_ERROR=ERROR_AT_CHECK_RESTICTIONS
    logger L3 "Entered check_restrictions"
    # Checks user system for the restrictions previously defined
    # TODO: *
    logger L3 "Exiting check_restrictions"
}

function check_requirements {
    DEBUG_ERROR=ERROR_AT_CHECK_REQUIREMENTS
    logger L3 "Check requirements"
    # Checks user system for the requirements previously defined
    # Attempts fixes when possible.
    # TODO: *
    logger L3 "Exiting check_requirements"
}

function check_required_sources {
    DEBUG_ERROR=ERROR_AT_CHECK_REQUIRED_SOURCES
    logger L3 "Entered check_requirements"
    # Checks if required sources are already configured, in which case they
    # shouldn't be readded. 
    # TODO: *
    logger L3 "Exiting check_required_sources"
}

function check_conflicting_sources {
    DEBUG_ERROR=ERROR_AT_CHECK_CONFLICTING_SOURCES
    logger L3 "Entering check_conflicting files"
    # Checks if conflicting sources are configured, in which case they must be
    # disabled.
    # TODO: *
    logger L3 "Exiting check_conflicting_sources"
}

function check_local_packages {
    DEBUG_ERROR=ERROR_AT_CHECK_LOCAL_PACKAGES
    logger L3 "Entered check_local_packages"
    # Checks if all or some of the required packages are already available, 
    # reducing the need for download / wasted bandidth for user and hosts.
    # TODO: *
    logger L3 "Exiting check_local_Packages"
}

function check_remote_packages {
    DEBUG_ERROR=ERROR_AT_CHECK_REMOTE_PACKAGES
    logger L3 "Entered check_remote_packages"
    # Checks if required remote packages are available at predefined sources. 
    # TODO: *
    logger L3 "Exiting check_remote_packages"
}

function simulate_packages_install {
    DEBUG_ERROR=ERROR_AT_SIMULATE_PACKAGES_INSTALL
    logger L3 "Entered simulate_packages_install"
    # Updates the list of packages to be installed considering dependencies.
    # Updates the list of removed packages (stored at the backup files).
    # TODO: *
    logger L3 "Exiting simulate_packages_install"
}

function prepare_system {
    DEBUG_ERROR=ERROR_AT_PREPARE_SYSTEM
    logger L3 "Entered prepare_system"
    # It's a good idea to check if the user is running processes that are needed or
    # that might interfere with the script processes (e.g. having more than one X 
    # has a lock in apt, etc).
    # TODO: *
    logger L3 "Exiting prepare_system"
}

function settings_backup {
    DEBUG_ERROR=ERROR_AT_SETTINGS_BACKUP
    logger L3 "Entered settings_backup"
    # Make dated backups of the settings files mentioned earlier in the pre-defined
    # backup location. 
    # TODO: *
    logger L3 "Exiting settings_backup"
}

function change_settings {
    DEBUG_ERROR=ERROR_AT_CHANGE_SETTINGS
    logger L3 "Entered change_settings"
    # Makes the pre-defined changes to configuration files.
    # TODO: *
    logger L3 "Exiting change_settings"
}

function install_packages {
    DEBUG_ERROR=ERROR_AT_INSTALL_PACKAGES
    logger L3 "Entered install_packages"
    # Installs all required packages
    # TODO: *
    logger L3 "Exiting install_packages"
}

function remove_packages {
    DEBUG_ERROR=ERROR_AT_REMOVE_PACKAGES
    logger L3 "Entered remove_packages"
    # Removes unneeded packages
    # TODO: *
    logger L3 "Exiting remove_packages"
}

function pin_packages {
    DEBUG_ERROR=ERROR_AT_PIN_PACKAGES
    logger L3 "Entered pin_packages"
    # Some packages may need to be "pinned" as well as sosme configuration files
    # may need to be frozen, to avoid misconfiguration in upcoming system updates.
    # TODO: *
    logger L3 "Exiting remove_packages"
}

function post_install {
    DEBUG_ERROR=ERROR_AT_POST_INSTALL
    logger L3 "Entered post_install"
    # Procedures to be executed after all the previous steps have been succesful.
    # Might include restart X, pop a dialog, reboot, etc.
    # TODO: *
    logger L3 "Exiting post_install"
}

function gather_support_information {
    DEBUG_ERROR=ERROR_AT_GATHER_SUPPORT_INFORMATION
    logger L3 "Entered gather_support_information"
    # Collects relevant information from user system and the script log and prepare
    # it to be posted at the support forum
    # TODO: *
    logger L3 "Exiting gather_support_information"
}

function publish_support_information {
    DEBUG_ERROR=ERROR_AT_PUBLISH_SUPPORT_INFORMATION
    logger L3 "Entered publish_support_information"
    # Publish relevant support information in the correct way (using code tags, 
    # etc), in the correct place (specific forum section) to enhance chances of 
    # user receiving adequate support.
    # TODO: *
    logger L3 "Exiting publish_support_information"
}

function main {
    DEBUG_ERROR=ERROR_AT_MAIN
    logger L3 "Entered main"
    # Invokes functions depending on command-line arguments and return codes.
    # TODO: *
    MAIN_ARG=$1
    detect_player
    do_cmd $MAIN_ARG
    logger L3 "Exiting main"
    exit 0
}

##############################################################################
########## End of Functions: Do not add functions below ######################
##############################################################################

##############################################################################
########## Command-line parser ###############################################
##############################################################################
# Although the use of getopts is not mandatory, it is adopted to support
# nested arguments like -fqy and parse them in a proper way. The script must
# take incoherent attempts and incompatible sets of arguments under 
# consideration and deal with it somehow.
##############################################################################
#
# Todo (Add Options for the implemented functions - as they are created/tested)
while getopts ":i" opt; do
  case $opt in
    a)
      echo "Selected Install!" >&2
      ;;
    \?)
      echo "Invalid option: -$OPTARG" >&2
      ;;
  esac
done

```

I've never created a PPA so I wouldn't know where to start :(

It could easily take months for me to learn how given the amount of time I have available. IMHO it comes down to a simple question of whether or not to share my limited knowledge or not. As currently written my "How I" includes a number of warnings such as:

> Before you begin please understand that I'm no genius (nor a dev)

if you want compiz this thread is NOT for you

Please DO read this all before beginning!

Also, there are no guarantees!

If you DO NOT want any of those things to happen this command is NOT for you!

Have I scared you off yet? If not and if you've decided to give this is a try here's the single command I use to convert Ubuntu Oneiric to Classic w/o effects (but please finish reading this post in it's entirety before continuing):

I'll also add something about double-clicking to highlight the content in code tags and right-clicking to select copy, then opening 'gnome-terminal', right-clicking within the terminal window and then selecting paste - a basic how-to copy-n-paste.

I'm also considering a "mostly" GUI option, including a "**sneak peek**" where a person would first only install 'gnome-session-fallback' using either the terminal or USC, then logging out, selecting "classic w/o effects", and poking around a bit in the menus, playing with the panel settings, etc.

That should be relatively safe because the default Unity settings can be restored by simply removing .config, .gconf, and .gnome2 in Home > hidden and then rebooting. I wish it were possible to do a "sneak-peek" using the Live CD but ATM that doesn't seem possible.

While it may be true that "Asking for logs is usually a joke" most of what I'd need to see in the event of a failure is in /var/log/apt/history.log and /var/log/apt/term.log so I'll try to plan a fairly simple method of copying those logs so the copies can be "compressed" and attached to a forum reply using the attachment tool.

Regardless I have considerable testing left to do. I always like to include a full procedure for reverting any and all changes if desired :D

---

### Post by kansasnoob on 2011-11-13
> **mc4man said:**
> Those commands (sudo /usr/lib/lightdm/lightdm-set-defaults -s ....) write to /etc/lightdm/lightdm.conf

But the setting in there is only used for autologin, if you boot to the login screen then whatever session is set in ~/.dmrc is what will be set on the greeter by 'default'

To further muddle that, at least here, if there are multiple user accounts & one is set to autologin then that's what happens on boot up - goes directly to that user

If more than one user is set to autologin then I believe it's 'last to set the autologin' option becomes the user booted to or restarted to, ( as in only 1 user can autologin at a time

You may be better off looking at writing a new session value to ~/.dmrc

unity3d is ubuntu
unity-2d is ubuntu-2d

Thanks for that info, very helpful :)

I hope for a GUI in 12.04 to change login settings.

---

### Post by kansasnoob on 2011-11-13
Where I'm at ATM, **please be sure to read the to-do list at the end, and know that [COLOR="Red"]I need to test and retest this to check for typos and other errors[/COLOR]**!

**********************************

Before you begin please understand that I'm no genius (nor a dev), far from it, but I wanted a Classic DE in Oneiric with the newest version of Gnome so I did some studying. **[COLOR="Red"]This is for "classic without effects" only![/COLOR]** I've never cared for compiz anyway and it seems to be difficult to get it to run in a classic Oneiric DE. So, **[COLOR="Red"]if you want compiz this thread is NOT for you[/COLOR]**, sorry. Please DO read this all before beginning!

Also, there are no guarantees! **I've tested this quite a bit, but only with fresh Oneiric installs.** Your mileage may vary with installations that have other underlying problems. I can only say that it works for me, no more and no less. And if you ask a question that's already answered in this thread I may very well get grumpy.

Now, I have this reduced to one single command that you can "copy-n-paste" into gnome-terminal, but that comes after an explanation of what it does and some basics about changes to the newest version of 'gnome-panel'. It's NOT a true script but rather just a bunch of commands strung together with 'space&&space' like the typical 'sudo apt-get update && sudo apt-get upgrade'. So look at what it does a "chunk" at a time:

**First** it installs two PPA's:

[https://launchpad.net/~jconti/+archive/gnome3](https://launchpad.net/~jconti/+archive/gnome3)

[https://launchpad.net/~caffeine-developers/+archive/ppa](https://launchpad.net/~caffeine-developers/+archive/ppa)

The first PPA allows you to add 'indicator-applet', 'indicator-applet-complete', and 'indicator-applet-session' to the panel applets displayed when you press Alt + right-click on a blank space in the panel to display "Add to panel". I personally only use 'indicator-applet' but your preferences may vary, the 'complete' version displays more "stuff".

The second PPA allows you to install 'caffeine' which is a sweet replacement for the old 'gnome-inhibit-applet'. After completing this and logging into the classic session you can setup Caffeine by going to Other > Caffeine preferences.

[ATTACH]207092[/ATTACH]

**Second** it updates the package base and installs 'gnome-session-fallback', 'caffeine', 'indicator-applet', 'indicator-applet-complete', 'indicator-applet-session', and their dependencies.

**Third** it sets lightdm to boot the classic w/o effects session by default.

**Fourth** it purges the overlay-scrollbars because I find them to be inconsistent and annoying in the classic DE.

**Fifth** it resets the window management buttons to the right side instead of the left.

**Sixth** it sets the desktop to display only mounted volumes. By default the desktop is not set to display anything. If you also want to display "Computer", "Home", or "Trash" on the desktop you'd need to run one of the commands in appendix #1 after this is all complete.

**Seventh** it sets the update-notifier to display in either 'indicator-applet' or 'indicator-applet-complete' as it used to, just because I like it that way.

**Eighth** it "kills" that "lock-screen" thing that requires you to enter a password after the screen-"blanker" activates. But the screen still does go black at the time displayed in System Tools > System Settings > Screen. (This is also where Caffeine becomes helpful).

**Ninth**, and last, it backs up the new configuration files in Home > hidden so these "new" defaults can be "stored" and possibly restored if you totally break something down the road. You'd just need to rename any of the files with an "_OLD" suffix by removing only the "_OLD". More about that in appendix #2.

**[COLOR="Red"]If you DO NOT want any of those things to happen this command is NOT for you![/COLOR]** But I'll include a "one-step-at-a-time" list of commands in appendix #3 for those who want to perform only part of the process.

This is what the default "new" classic DE will look like after performing this:

[ATTACH]207093[/ATTACH]

Thinking of going ahead? If so, you also must understand that once you've booted into the "new" classic desktop you'll notice that the menu(s) have changed as shown in the above screenshot, but I think you'll likely find what you want if you spend just a couple of minutes familiarizing yourself with the new menu layout, be sure to check the Other and System Tools categories. You'll find most of what you're used to seeing in System > Administration and System > Preferences is now just relocated.

You also need to know that you must now hold down either Alt key while right-clicking on a panel or applet to be able to edit panel preferences or to add/edit/move/remove more applets. That was an intentional move by the Gnome devs to prevent people from unintentionally breaking things. And you also can't just add application applets by right-clicking them and selecting "add to panel". You must now open the "add-to-panel" window and select Application Launcher > Forward, then the window changes and you can click on the "bullet" to the left of each category to add any app in the menu to the panel.

[ATTACH]207094[/ATTACH]

The next screenshot shows what my new DE looks like after applying my personal tweaks, it includes a compilation of Panel Properties settings. and what the Caffeine applet shows when clicked. Note here that in Panel Properties > Background I've found that 'Solid color' > Color > Color name #3F3E39 results in improved appearance of the Workspace Switcher. The only thing I rather dislike is the scrollbar "button" color - I'd prefer it to match the window decoration (dark gray), but I've found worse flaws in all other themes I've tried.

[ATTACH]207095[/ATTACH]

Have I scared you off yet? If not and if you've decided to give this is a try here's the single command I use to convert Ubuntu Oneiric to Classic w/o effects (**[COLOR="Red"]but please finish reading this post in it's entirety before continuing[/COLOR]**):

```
sudo add-apt-repository ppa:jconti/gnome3 && sudo add-apt-repository ppa:caffeine-developers/ppa && sudo apt-get update && sudo apt-get install gnome-session-fallback caffeine indicator-applet indicator-applet-complete indicator-applet-session && sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-fallback && sudo apt-get purge liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0 overlay-scrollbar && gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close" && gsettings set org.gnome.desktop.interface menus-have-icons true && gsettings set org.gnome.desktop.interface buttons-have-icons true && gsettings set org.gnome.desktop.background show-desktop-icons true && gsettings set org.gnome.nautilus.desktop volumes-visible true && gsettings set org.gnome.nautilus.desktop computer-icon-visible false && gsettings set org.gnome.nautilus.desktop home-icon-visible false && gsettings set org.gnome.nautilus.desktop trash-icon-visible false && gsettings set com.ubuntu.update-notifier auto-launch false && gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true' && cp -a .config .config_OLD && cp -a .gconf .gconf_OLD && cp -a .gnome2 .gnome2_OLD
```

**You'll have to confirm with enter or y + enter at four points:**

(1)
You are about to add the following PPA to your system:
GNOME 3
Ports of various applications to GNOME 3.
More info: [https://launchpad.net/~jconti/+archive/gnome3](https://launchpad.net/~jconti/+archive/gnome3)
Press [ENTER] to continue or ctrl-c to cancel adding it

(2)
You are about to add the following PPA to your system:
Caffeine
The latest packages for Caffeine.


More info: [https://launchpad.net/~caffeine-developers/+archive/ppa](https://launchpad.net/~caffeine-developers/+archive/ppa)
Press [ENTER] to continue or ctrl-c to cancel adding it

(3)
The following extra packages will be installed:
alacarte gir1.2-panelapplet-4.0 gnome-applets gnome-applets-data gnome-panel
gnome-panel-data gnome-session gnome-session-bin gnome-session-common
libpanel-applet-4-0 libsqlite0 python-central python-gmenu python-kaa-base
python-kaa-metadata python-sqlite python-xlib
Suggested packages:
gnome-netstatus-applet deskbar-applet cpufrequtils evolution
epiphany-browser desktop-base python-sqlite-dbg
The following NEW packages will be installed:
alacarte caffeine gir1.2-panelapplet-4.0 gnome-applets gnome-applets-data
gnome-panel gnome-panel-data gnome-session-fallback indicator-applet
indicator-applet-complete indicator-applet-session libpanel-applet-4-0
libsqlite0 python-central python-gmenu python-kaa-base python-kaa-metadata
python-sqlite python-xlib
The following packages will be upgraded:
gnome-session gnome-session-bin gnome-session-common
3 upgraded, 19 newly installed, 0 to remove and 198 not upgraded.
Need to get 10.5 MB/10.7 MB of archives.
After this operation, 46.6 MB of additional disk space will be used.
Do you want to continue [Y/n]?

(4)
The following packages will be REMOVED:
liboverlay-scrollbar-0.2-0* liboverlay-scrollbar3-0.2-0* overlay-scrollbar*
0 upgraded, 0 newly installed, 3 to remove and 198 not upgraded.
After this operation, 307 kB disk space will be freed.
Do you want to continue [Y/n]?

**Failure to properly confirm your intent will result in failure!** You'll know the terminal output has ended when you see the typical "lance@lance-desktop:~$". Of course unless your user-name is lance the name will differ. 

Note: if this was a fresh install and not yet updated you'll see the update-notification show up both in the top Unity panel and in gnome-panel after you reboot. You can either update now or after you reboot. If you remove the top gnome-panel from the classic session before updating you'll notice some remnants of the global-menu bar remain - don't worry that's fixed with the first round of updates.

When you first launch Firefox you may find that you need to go to Tools > Add-ons > Extensions and disable the Global Menu Bar integration extension. I don't use Thunderbird but I suspect you'll need to do likewise with it.

To Do list:

1: Possibly find or create a comprehensive but simple guide regarding the new gnome-panel.

2: I'm strongly thinking this should be posted only as an alternative after creating a "sneak-peek" guide using either GUI or CLI. This would allow me to eliminate the aforementioned appendices and simplify things greatly. Need time to think.

3: Vacuum carpet and bathe dogs :)

---

### Post by kansasnoob on 2011-11-13
Just thought to add that even though it says, "I've tested this quite a bit, but only with fresh Oneiric installs". That's not entirely true. I have tested it with Precise, most recently about 4 days ago :)

And my to do list should also include testing various things like backing up files for a "sneak peek" so one can easily revert to the standard unity DE, and something fairly comprehensive regarding lightdm :)

And, as always, all feedback is welcome. That's why I'm posting here first.

If you see something you disagree with please say something.

---

### Post by kansasnoob on 2011-11-13
Thinking out loud here. I think my number one thing "to do" needs to be testing that command on an install that is not set to auto-login.

I always set my installs to auto-login so it may well break those not set so :(

---

### Post by thered on 2011-11-13
Hi, haven't been here for a while :)

@kansasnoob:

OK, I've tried Unity and can't get away with it.

Prior to trying you command(s) I had already tried to invoke gnome classic using other sites and methods I've googled.

I get the option to choose different desktops when I 'switch user' but *none* of them work - it justs reverts to Unity.

I've run your code and the same happens - nothing!

So I'm scratching my head now.  Any ideas?

---

### Post by ranch hand on 2011-11-13
Well I still can't run an Ubuntu Live CD so I am going to try this from a netboot ISO.  I just want to clarify that I need to install the ubuntu-desktop and then these other things.

This will also give some answer to the auto-login question as I never use that.

What you have looks an awful lot like my GS setup.  Will have to see what it looks like in person.

---

### Post by kansasnoob on 2011-11-13
> **ranch hand said:**
> Well I still can't run an Ubuntu Live CD so I am going to try this from a netboot ISO.  I just want to clarify that I need to install the ubuntu-desktop and then these other things.

This will also give some answer to the auto-login question as I never use that.

What you have looks an awful lot like my GS setup.  Will have to see what it looks like in person.

Yes! I've not tried the mini-iso in some time but this is dependent on 'ubuntu-desktop'!

---

### Post by ronacc on 2011-11-13
tried your script and got theese errors ( fresh precise amd64 install with ubuntu repo gnome3 already installed )
there is an extraneous n at the very end of the caffeine-developers-ppa-precise.list removing that let me get further .

gpg: requesting key 569113AE from hkp server keyserver.ubuntu.com
gpg: key 569113AE: "Launchpad Caffeine" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
E: Type 'n' is not known on line 3 in source list /etc/apt/sources.list.d/caffeine-developers-ppa-precise.list
E: The list of sources could not be read.

and after correcting that 

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources [906 kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources [5,358 B]           
Fetched 965 kB in 13s (70.9 kB/s)                                              
W: Failed to fetch [http://ppa.launchpad.net/jconti/gnome3/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/jconti/gnome3/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

I think the name of the ppa is missing in the first error here and there is no precise for the jconti PPA only oneiric .

---

### Post by kansasnoob on 2011-11-13
> **thered said:**
> Hi, haven't been here for a while :)

@kansasnoob:

OK, I've tried Unity and can't get away with it.

Prior to trying you command(s) I had already tried to invoke gnome classic using other sites and methods I've googled.

I get the option to choose different desktops when I 'switch user' but *none* of them work - it justs reverts to Unity.

I've run your code and the same happens - nothing!

So I'm scratching my head now.  Any ideas?

Not much to go on there other than the fact that "I had already tried to invoke gnome classic using other sites and methods I've googled" which is troubling but ranch hand mentioned something that made me think right off the bat that I'd tried other procedures that ended up severely biting me where the sun don't shine.

In many of those other procedures the meta-package 'ubuntu-desktop' and many of it's dependencies were removed, so try beginning by installing 'ubuntu-desktop':

```
sudo apt-get install ubuntu-desktop
```

Then run my command again. If anything fails please copy-n-paste the output from the terminal into the next reply which should help immensely.

Please use code tags for the terminal output if possible :)

---

### Post by kansasnoob on 2011-11-13
> **ronacc said:**
> tried your script and got theese errors ( fresh precise amd64 install with ubuntu repo gnome3 already installed )
there is an extraneous n at the very end of the caffeine-developers-ppa-precise.list removing that let me get further .

gpg: requesting key 569113AE from hkp server keyserver.ubuntu.com
gpg: key 569113AE: "Launchpad Caffeine" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
E: Type 'n' is not known on line 3 in source list /etc/apt/sources.list.d/caffeine-developers-ppa-precise.list
E: The list of sources could not be read.

and after correcting that 

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources [906 kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources [5,358 B]           
Fetched 965 kB in 13s (70.9 kB/s)                                              
W: Failed to fetch [http://ppa.launchpad.net/jconti/gnome3/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/jconti/gnome3/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

I think the name of the ppa is missing in the first error here and there is no precise for the jconti PPA only oneiric .

I may have done a copy-n-paste error, but I've also wondered what happens now if the PPA is already installed :confused:

I'm just now starting to test this again, which is why I said:

> I need to test and retest this to check for typos and other errors!

I'm performing the first test right now :)

---

### Post by ronacc on 2011-11-13
ok got it up and running all except for that PPA with no name , did some hand editing and changed the jconti ppa to oneiric updated and reran the cmds. I was set for password login and gnome so I had to select gnome classic no effects from the login menu . everything seems to be there so maybe that no name ppa was a partial double paste .

---

### Post by kansasnoob on 2011-11-13
> **mc4man said:**
> Those commands (sudo /usr/lib/lightdm/lightdm-set-defaults -s ....) write to /etc/lightdm/lightdm.conf

But the setting in there is only used for autologin, if you boot to the login screen then whatever session is set in ~/.dmrc is what will be set on the greeter by 'default'

To further muddle that, at least here, if there are multiple user accounts & one is set to autologin then that's what happens on boot up - goes directly to that user

If more than one user is set to autologin then I believe it's 'last to set the autologin' option becomes the user booted to or restarted to, ( as in only 1 user can autologin at a time

You may be better off looking at writing a new session value to ~/.dmrc

unity3d is ubuntu
unity-2d is ubuntu-2d

Regarding this what I know so far is:

If NOT using auto-login the changes we make to '/usr/lib/lightdm/lightdm-set-defaults -s' do not seem to break anything, and selecting a session once, if not using auto-login, does seem to "stick".

So I mostly now need to just test the "ubuntu" and "ubuntu-2d" suffixes with "sudo /usr/lib/lightdm/lightdm-set-defaults -s SOME_SESSION".

Thanks for the help mc4man :D

---

### Post by kansasnoob on 2011-11-13
> **ronacc said:**
> ok got it up and running all except for that PPA with no name , did some hand editing and changed the jconti ppa to oneiric updated and reran the cmds. I was set for password login and gnome so I had to select gnome classic no effects from the login menu . everything seems to be there so maybe that no name ppa was a partial double paste .

Is that possibly a problem that should be reported to the caffeine team?

I just completed a new Oneiric install to do some testing (still no luck with Precise CD's) and the Oneiric version works OK.

I probably won't have time to test that any further today, and tomorrow I'll be tied up with unrelated issues.

---

### Post by kansasnoob on 2011-11-13
> **kansasnoob said:**
> I may have done a copy-n-paste error, but I've also wondered what happens now if the PPA is already installed :confused:

I'm just now starting to test this again, which is why I said:



I'm performing the first test right now :)

Trying to answer this question myself:

> I've also wondered what happens now if the PPA is already installed

Going to see right now, and I'm beginning with this:

```
ubuntu@ubuntu-desktop:~$ ls /etc/apt/sources.list.d
caffeine-developers-ppa-oneiric.list  jconti-gnome3-oneiric.list.save
jconti-gnome3-oneiric.list

```

Probably my last test of the day :)

I'll be trying Precise more beginning Tuesday.

---

### Post by ronacc on 2011-11-13
here is a copy of the start of your script ```
sudo add-apt-repository ppa:jconti/gnome3 && sudo add-apt-repository ppa:caffeine-developers/ppa
```
that /ppa at the end of ppa:caffeine-developers shouldn't be there .

edit : oops mabye I spoke too soon the caffeine-developers ppa shows it the way you have it .

---

### Post by ranch hand on 2011-11-13
> **kansasnoob said:**
> Yes! I've not tried the mini-iso in some time but this is dependent on 'ubuntu-desktop'!
Thanks for that confirmation.

I like the netboot images because they do not make my HDD sound like a rock crusher.  They also give you the ability to not install a lot of things you never use.

If you count the downloading of the regular images, Live or Alt, and the time you spend downloading things that need installed it takes about the same time.

I usually install the thing, boot to it and then right back out and back here and finish the install in chroot so that I can run boinc and whatever else I am doing with out any wasted time.

When I converted all my Ubuntu installs to Debian I did it that way too (2 partition installs just over writing the / partition).  I can do the fast net install, check to make sure the passwords work and come here and listen to tunes while watching the rest of the install if that is what blows my skirt up at the time.

Thanks again.  Will grab the image and probably do that this evening.

---

### Post by kansasnoob on 2011-11-13
> **kansasnoob said:**
> Trying to answer this question myself:



Going to see right now, and I'm beginning with this:

```
ubuntu@ubuntu-desktop:~$ ls /etc/apt/sources.list.d
caffeine-developers-ppa-oneiric.list  jconti-gnome3-oneiric.list.save
jconti-gnome3-oneiric.list

```

Probably my last test of the day :)

I'll be trying Precise more beginning Tuesday.

Still looking, but I need to document what happens if a PPA already exists, so:

```
ubuntu@ubuntu-desktop:~$ ls /etc/apt
apt.conf.d     sources.list    sources.list.save  trusted.gpg   trusted.gpg.d
preferences.d  sources.list.d  trustdb.gpg        trusted.gpg~
ubuntu@ubuntu-desktop:~$ ls /etc/apt/sources.list.d
caffeine-developers-ppa-oneiric.list  jconti-gnome3-oneiric.list.save
jconti-gnome3-oneiric.list
ubuntu@ubuntu-desktop:~$ sudo add-apt-repository ppa:jconti/gnome3 && sudo add-apt-repository ppa:caffeine-developers/ppa && sudo apt-get update && sudo apt-get install gnome-session-fallback caffeine indicator-applet indicator-applet-complete indicator-applet-session && sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-fallback && sudo apt-get purge liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0 overlay-scrollbar && gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close" && gsettings set org.gnome.desktop.interface menus-have-icons true && gsettings set org.gnome.desktop.interface buttons-have-icons true && gsettings set org.gnome.desktop.background show-desktop-icons true && gsettings set org.gnome.nautilus.desktop volumes-visible true && gsettings set org.gnome.nautilus.desktop computer-icon-visible false && gsettings set org.gnome.nautilus.desktop home-icon-visible false && gsettings set org.gnome.nautilus.desktop trash-icon-visible false && gsettings set com.ubuntu.update-notifier auto-launch false && gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true' && cp -a .config .config_OLD && cp -a .gconf .gconf_OLD && cp -a .gnome2 .gnome2_OLD
[sudo] password for ubuntu: 
You are about to add the following PPA to your system:
 GNOME 3
 Ports of various applications to GNOME 3.
 More info: https://launchpad.net/~jconti/+archive/gnome3
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.zdKlrwTPHJ --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 25259BF2B564FCE366DAF1D252A794126E3AB2D3
gpg: requesting key 6E3AB2D3 from hkp server keyserver.ubuntu.com
gpg: key 6E3AB2D3: "Launchpad Recent Notifications" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
You are about to add the following PPA to your system:
 Caffeine
 The latest packages for Caffeine.


 More info: https://launchpad.net/~caffeine-developers/+archive/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.c9PbPD76GG --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv DC2887936B4153CA9AFB151B0F678A01569113AE
gpg: requesting key 569113AE from hkp server keyserver.ubuntu.com
gpg: key 569113AE: "Launchpad Caffeine" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
Ign http://ppa.launchpad.net oneiric InRelease
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Ign http://security.ubuntu.com oneiric-security InRelease                      
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://us.archive.ubuntu.com oneiric InRelease                             
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://us.archive.ubuntu.com oneiric-backports InRelease                   
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://us.archive.ubuntu.com oneiric Release.gpg                           
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://us.archive.ubuntu.com oneiric-updates Release.gpg                   
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Hit http://security.ubuntu.com oneiric-security/universe Sources               
Hit http://security.ubuntu.com oneiric-security/multiverse Sources             
Hit http://security.ubuntu.com oneiric-security/main i386 Packages             
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages       
Hit http://us.archive.ubuntu.com oneiric-backports Release.gpg                 
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Hit http://us.archive.ubuntu.com oneiric Release                               
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://us.archive.ubuntu.com oneiric-updates Release                       
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Hit http://us.archive.ubuntu.com oneiric-backports Release                     
Hit http://us.archive.ubuntu.com oneiric/main Sources                          
Hit http://us.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://us.archive.ubuntu.com oneiric/universe Sources                      
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/main Sources                  
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Sources            
Hit http://us.archive.ubuntu.com oneiric-updates/universe Sources              
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Sources            
Hit http://us.archive.ubuntu.com oneiric-updates/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages      
Hit http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages        
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com oneiric-backports/main Sources                
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Sources          
Hit http://us.archive.ubuntu.com oneiric-backports/universe Sources
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com oneiric-backports/main i386 Packages          
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Hit http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Hit http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric/main Translation-en
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/universe Translation-en
Ign http://extras.ubuntu.com oneiric InRelease      
Hit http://extras.ubuntu.com oneiric Release.gpg    
Hit http://extras.ubuntu.com oneiric Release
Hit http://extras.ubuntu.com oneiric/main Sources
Hit http://extras.ubuntu.com oneiric/main i386 Packages
Ign http://extras.ubuntu.com oneiric/main TranslationIndex
Ign http://extras.ubuntu.com oneiric/main Translation-en_US
Ign http://extras.ubuntu.com oneiric/main Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-session-fallback is already the newest version.
caffeine is already the newest version.
indicator-applet is already the newest version.
indicator-applet-complete is already the newest version.
indicator-applet-session is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 198 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package liboverlay-scrollbar-0.2-0 is not installed, so not removed
Package liboverlay-scrollbar3-0.2-0 is not installed, so not removed
Package overlay-scrollbar is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 198 not upgraded.
ubuntu@ubuntu-desktop:~$ 

```

It looks like the Ubuntu devs have that handled:

```
ubuntu@ubuntu-desktop:~$ ls /etc/apt/sources.list.d
caffeine-developers-ppa-oneiric.list       jconti-gnome3-oneiric.list
caffeine-developers-ppa-oneiric.list.save  jconti-gnome3-oneiric.list.save

```

That is it looks like the old ".list" becomes ".list.save", rather like how zsync works :)

Much more testing to do but out of time ATM.

I'm seriously thinking that I should just forget about a Oneiric thread ATM. Or, if I do it, I'l just say it must begin with a fresh install.

---

### Post by cariboo on 2011-11-13
Moved 3 off topic posts to the jail.

---

### Post by thered on 2011-11-13
@cariboo

> Moved 3 off topic posts to the jail.

Then you should also edit posts or part of posts that evoke a response to groundless, unsubstantiated and untrue personal remarks about other posters. A response that you don't allow.

I don't want to start a war, it ain't that big a deal, but if I'm not allowed answer, in a polite, jocular manner, then those remarks should be expunged. 

Thank you.

---

### Post by kansasnoob on 2011-11-14
> **thered said:**
> @cariboo



Then you should also edit posts or part of posts that evoke a response to groundless, unsubstantiated and untrue personal remarks about other posters. A response that you don't allow.

I don't want to start a war, it ain't that big a deal, but if I'm not allowed answer, in a polite, jocular manner, then those remarks should be expunged. 

Thank you.

I hope I did that adequately myself :)

If you decide you'd like to have another go at this I'll be glad to try and help, although the amount of desk time I have varies greatly. Like I'll be away most of today.

Actually, I've now decided that the "single command" should be offered only as an "advanced" option, so I'll pursue a one-step-at-a-time how-to with both GUI and CLI options :D

---

### Post by kansasnoob on 2011-11-14
I've decided to try something different for Oneiric and since it will be for Oneiric only I'm going to pursue it elsewhere, probably in Main Support > Desktop Environments.

It will basically be a one-step-at-a-time guide with both CLI and GUI options. Basically begin by installing only 'gnome-session-fallback' and then move into an explanation of menu and panel changes.

That will have to include a bit about backing up configuration files or restoring unity/gnome-panel defaults, and probably next adding the 'jconti/gnome3' PPA so the 'indicator-applet', 'indicator-applet-complete', and 'indicator-applet-session' applets are included in "Add to panel".

Probably slip a bit in about Caffeine next, then move onto changing lightdm settings, and removing overlay-scrollbars if desired.

Then the rest (mostly) gets down to personalized tweaks, most of which can be done either via 'gnome-tweak-tool', Ubuntu tweak, or CLI.

It'll take a few days but I should be able to rely on external links for a lot of the detailed instruction.

---

### Post by kansasnoob on 2011-11-14
Actually a great start here:

[http://www.webupd8.org/2011/08/installing-using-classic-gnome-desktop.html](http://www.webupd8.org/2011/08/installing-using-classic-gnome-desktop.html)

Haven't really found anything comprehensive on editing the panels yet though so I'll probably do that myself.

---

### Post by ventrical on 2011-11-14
> **kansasnoob said:**
> I've decided to try something different for Oneiric and since it will be for Oneiric only I'm going to pursue it elsewhere, probably in Main Support > Desktop Environments.

It will basically be a one-step-at-a-time guide with both CLI and GUI options. Basically begin by installing only 'gnome-session-fallback' and then move into an explanation of menu and panel changes.

That will have to include a bit about backing up configuration files or restoring unity/gnome-panel defaults, and probably next adding the 'jconti/gnome3' PPA so the 'indicator-applet', 'indicator-applet-complete', and 'indicator-applet-session' applets are included in "Add to panel".

Probably slip a bit in about Caffeine next, then move onto changing lightdm settings, and removing overlay-scrollbars if desired.

Then the rest (mostly) gets down to personalized tweaks, most of which can be done either via 'gnome-tweak-tool', Ubuntu tweak, or CLI.

It'll take a few days but I should be able to rely on external links for a lot of the detailed instruction.


Thanks ! 

:)

---

### Post by ventrical on 2011-11-14
> **kansasnoob said:**
> Where I'm at ATM, **please be sure to read the to-do list at the end, and know that [COLOR=Red]I need to test and retest this to check for typos and other errors[/COLOR]**!

**********************************

Before you begin please understand that I'm no genius (nor a dev), far from it, but I wanted a Classic DE in Oneiric with the newest version of Gnome so I did some studying. **[COLOR=Red]This is for "classic without effects" only![/COLOR]** I've never cared for compiz anyway and it seems to be difficult to get it to run in a classic Oneiric DE. So, **[COLOR=Red]if you want compiz this thread is NOT for you[/COLOR]**, sorry. Please DO read this all before beginning!

Also, there are no guarantees! **I've tested this quite a bit, but only with fresh Oneiric installs.** Your mileage may vary with installations that have other underlying problems. I can only say that it works for me, no more and no less. And if you ask a question that's already answered in this thread I may very well get grumpy.

Now, I have this reduced to one single command that you can "copy-n-paste" into gnome-terminal, but that comes after an explanation of what it does and some basics about changes to the newest version of 'gnome-panel'. It's NOT a true script but rather just a bunch of commands strung together with 'space&&space' like the typical 'sudo apt-get update && sudo apt-get upgrade'. So look at what it does a "chunk" at a time:

**First** it installs two PPA's:

[https://launchpad.net/~jconti/+archive/gnome3]("https://launchpad.net/%7Ejconti/+archive/gnome3")

[https://launchpad.net/~caffeine-developers/+archive/ppa]("https://launchpad.net/%7Ecaffeine-developers/+archive/ppa")

The first PPA allows you to add 'indicator-applet', 'indicator-applet-complete', and 'indicator-applet-session' to the panel applets displayed when you press Alt + right-click on a blank space in the panel to display "Add to panel". I personally only use 'indicator-applet' but your preferences may vary, the 'complete' version displays more "stuff".

The second PPA allows you to install 'caffeine' which is a sweet replacement for the old 'gnome-inhibit-applet'. After completing this and logging into the classic session you can setup Caffeine by going to Other > Caffeine preferences.

[ATTACH]207092[/ATTACH]

**Second** it updates the package base and installs 'gnome-session-fallback', 'caffeine', 'indicator-applet', 'indicator-applet-complete', 'indicator-applet-session', and their dependencies.

**Third** it sets lightdm to boot the classic w/o effects session by default.

**Fourth** it purges the overlay-scrollbars because I find them to be inconsistent and annoying in the classic DE.

**Fifth** it resets the window management buttons to the right side instead of the left.

**Sixth** it sets the desktop to display only mounted volumes. By default the desktop is not set to display anything. If you also want to display "Computer", "Home", or "Trash" on the desktop you'd need to run one of the commands in appendix #1 after this is all complete.

**Seventh** it sets the update-notifier to display in either 'indicator-applet' or 'indicator-applet-complete' as it used to, just because I like it that way.

**Eighth** it "kills" that "lock-screen" thing that requires you to enter a password after the screen-"blanker" activates. But the screen still does go black at the time displayed in System Tools > System Settings > Screen. (This is also where Caffeine becomes helpful).

**Ninth**, and last, it backs up the new configuration files in Home > hidden so these "new" defaults can be "stored" and possibly restored if you totally break something down the road. You'd just need to rename any of the files with an "_OLD" suffix by removing only the "_OLD". More about that in appendix #2.

**[COLOR=Red]If you DO NOT want any of those things to happen this command is NOT for you![/COLOR]** But I'll include a "one-step-at-a-time" list of commands in appendix #3 for those who want to perform only part of the process.

This is what the default "new" classic DE will look like after performing this:

[ATTACH]207093[/ATTACH]

Thinking of going ahead? If so, you also must understand that once you've booted into the "new" classic desktop you'll notice that the menu(s) have changed as shown in the above screenshot, but I think you'll likely find what you want if you spend just a couple of minutes familiarizing yourself with the new menu layout, be sure to check the Other and System Tools categories. You'll find most of what you're used to seeing in System > Administration and System > Preferences is now just relocated.

You also need to know that you must now hold down either Alt key while right-clicking on a panel or applet to be able to edit panel preferences or to add/edit/move/remove more applets. That was an intentional move by the Gnome devs to prevent people from unintentionally breaking things. And you also can't just add application applets by right-clicking them and selecting "add to panel". You must now open the "add-to-panel" window and select Application Launcher > Forward, then the window changes and you can click on the "bullet" to the left of each category to add any app in the menu to the panel.

[ATTACH]207094[/ATTACH]

The next screenshot shows what my new DE looks like after applying my personal tweaks, it includes a compilation of Panel Properties settings. and what the Caffeine applet shows when clicked. Note here that in Panel Properties > Background I've found that 'Solid color' > Color > Color name #3F3E39 results in improved appearance of the Workspace Switcher. The only thing I rather dislike is the scrollbar "button" color - I'd prefer it to match the window decoration (dark gray), but I've found worse flaws in all other themes I've tried.

[ATTACH]207095[/ATTACH]

Have I scared you off yet? If not and if you've decided to give this is a try here's the single command I use to convert Ubuntu Oneiric to Classic w/o effects (**[COLOR=Red]but please finish reading this post in it's entirety before continuing[/COLOR]**):

```
sudo add-apt-repository ppa:jconti/gnome3 && sudo add-apt-repository ppa:caffeine-developers/ppa && sudo apt-get update && sudo apt-get install gnome-session-fallback caffeine indicator-applet indicator-applet-complete indicator-applet-session && sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-fallback && sudo apt-get purge liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0 overlay-scrollbar && gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close" && gsettings set org.gnome.desktop.interface menus-have-icons true && gsettings set org.gnome.desktop.interface buttons-have-icons true && gsettings set org.gnome.desktop.background show-desktop-icons true && gsettings set org.gnome.nautilus.desktop volumes-visible true && gsettings set org.gnome.nautilus.desktop computer-icon-visible false && gsettings set org.gnome.nautilus.desktop home-icon-visible false && gsettings set org.gnome.nautilus.desktop trash-icon-visible false && gsettings set com.ubuntu.update-notifier auto-launch false && gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true' && cp -a .config .config_OLD && cp -a .gconf .gconf_OLD && cp -a .gnome2 .gnome2_OLD
```**You'll have to confirm with enter or y + enter at four points:**

(1)
You are about to add the following PPA to your system:
GNOME 3
Ports of various applications to GNOME 3.
More info: [https://launchpad.net/~jconti/+archive/gnome3]("https://launchpad.net/%7Ejconti/+archive/gnome3")
Press [ENTER] to continue or ctrl-c to cancel adding it

(2)
You are about to add the following PPA to your system:
Caffeine
The latest packages for Caffeine.


More info: [https://launchpad.net/~caffeine-developers/+archive/ppa]("https://launchpad.net/%7Ecaffeine-developers/+archive/ppa")
Press [ENTER] to continue or ctrl-c to cancel adding it

(3)
The following extra packages will be installed:
alacarte gir1.2-panelapplet-4.0 gnome-applets gnome-applets-data gnome-panel
gnome-panel-data gnome-session gnome-session-bin gnome-session-common
libpanel-applet-4-0 libsqlite0 python-central python-gmenu python-kaa-base
python-kaa-metadata python-sqlite python-xlib
Suggested packages:
gnome-netstatus-applet deskbar-applet cpufrequtils evolution
epiphany-browser desktop-base python-sqlite-dbg
The following NEW packages will be installed:
alacarte caffeine gir1.2-panelapplet-4.0 gnome-applets gnome-applets-data
gnome-panel gnome-panel-data gnome-session-fallback indicator-applet
indicator-applet-complete indicator-applet-session libpanel-applet-4-0
libsqlite0 python-central python-gmenu python-kaa-base python-kaa-metadata
python-sqlite python-xlib
The following packages will be upgraded:
gnome-session gnome-session-bin gnome-session-common
3 upgraded, 19 newly installed, 0 to remove and 198 not upgraded.
Need to get 10.5 MB/10.7 MB of archives.
After this operation, 46.6 MB of additional disk space will be used.
Do you want to continue [Y/n]?

(4)
The following packages will be REMOVED:
liboverlay-scrollbar-0.2-0* liboverlay-scrollbar3-0.2-0* overlay-scrollbar*
0 upgraded, 0 newly installed, 3 to remove and 198 not upgraded.
After this operation, 307 kB disk space will be freed.
Do you want to continue [Y/n]?

**Failure to properly confirm your intent will result in failure!** You'll know the terminal output has ended when you see the typical "lance@lance-desktop:~$". Of course unless your user-name is lance the name will differ. 

Note: if this was a fresh install and not yet updated you'll see the update-notification show up both in the top Unity panel and in gnome-panel after you reboot. You can either update now or after you reboot. If you remove the top gnome-panel from the classic session before updating you'll notice some remnants of the global-menu bar remain - don't worry that's fixed with the first round of updates.

When you first launch Firefox you may find that you need to go to Tools > Add-ons > Extensions and disable the Global Menu Bar integration extension. I don't use Thunderbird but I suspect you'll need to do likewise with it.

To Do list:

1: Possibly find or create a comprehensive but simple guide regarding the new gnome-panel.

2: I'm strongly thinking this should be posted only as an alternative after creating a "sneak-peek" guide using either GUI or CLI. This would allow me to eliminate the aforementioned appendices and simplify things greatly. Need time to think.

3: Vacuum carpet and bathe dogs :)


  I really appreciate all the work you have done on this kansasnoob. I started a thread back in testimonials quite some time ago about this very topic ...but members kept assuring me that GNOME classic would be taken care of .. etc.. and arguments were made that  Unity is the way that Ubuntu is going .. and we better get used to it. I think that they are a lot of people working on this behind the scenes and perhaps they are just not enthusiastic as you are.

 Precise should have a STABLE GNOME DE o reven a Simple GNOME DE (like Simple Compiz Settings manager.) because there are a lot of ATI graphics cards that will work great with Unity 2D and GNOME simple and still run  some 3D games in the repositories - so Precise would certainly behoove itself to amalgamate some type of GNOME simple into the bootup options.

 Stay with it !!

---

### Post by seeker5528 on 2011-11-14
> **kansasnoob said:**
> I'm stuck on my "How I create a classic DE w/o effects" project because I also need to know how to set the Ubuntu & Ubuntu-2D sessions to boot as default :)

I must be able to return lightdm to it's default settings or provide info to boot the unity and unity-2D DE's.

I'm kind of anal retentive about specifics ;)

And I must be able to provide a method to revert :D

For future reference, all the .desktop files for the different sessions are in '/usr/share/xsessions/' so for example if you look there at 'ubuntu-2d.desktop' you see a line in the file "Exec=gnome-session --session=ubuntu-2d", whatever the '--session=' part is should be what you want to specify when you run lightdm-set-defaults to set the system wide default or change '~/.dmrc' to make the change user specific. 

If the user has selected a session in the session menu of their display manager at some point in the past, that would have, either in '~/.dmrc' or in some display manager specific way, set the session option for the user, overriding the system default.

> **mc4man said:**
> Those commands (sudo /usr/lib/lightdm/lightdm-set-defaults -s ....) write to /etc/lightdm/lightdm.conf

But the setting in there is only used for autologin, if you boot to the login screen then whatever session is set in ~/.dmrc is what will be set on the greeter by 'default'

Sounds like a bug to me if autologin doesn't use the same session type that would be used when stopping at the login screen and waiting for the user to log in.

> To further muddle that, at least here, if there are multiple user accounts & one is set to autologin then that's what happens on boot up - goes directly to that user

Wouldn't that be expected behavior? :confused:

Later, Seeker

---

### Post by kansasnoob on 2011-11-14
I just want to clarify things. I'm NOT giving up my project but effenberg0x0 made a lot of sense. That became apparent very soon.

I'm just going to approach this from a different angle because I've spent a considerable amount of time searching for ways to get close to a true "classic" DE in 11.10 and I'm finding it's just not that hard at all :D

While I have it figured out I now need to figure out how to best present that to "everyone". Every other how-to I can find seems to contain serious flaws and/or omissions so I'm trying to come up with something that will just work.

But I'm busy with real life issues so it could take a while. That's why we have the forums, especially +1 :)

Hopefully what's being shared here will spur others into creating guides, etc :D

---

### Post by kansasnoob on 2011-11-14
> **seeker5528 said:**
> For future reference, all the .desktop files for the different sessions are in '/usr/share/xsessions/' so for example if you look there at 'ubuntu-2d.desktop' you see a line in the file "Exec=gnome-session --session=ubuntu-2d", whatever the '--session=' part is should be what you want to specify when you run lightdm-set-defaults to set the system wide default or change '~/.dmrc' to make the change user specific. 

If the user has selected a session in the session menu of their display manager at some point in the past, that would have, either in '~/.dmrc' or in some display manager specific way, set the session option for the user, overriding the system default.



Sounds like a bug to me if autologin doesn't use the same session type that would be used when stopping at the login screen and waiting for the user to log in.



Wouldn't that be expected behavior? :confused:

Later, Seeker

Thank you, I think I have lightdm mostly figured out now ............. **think** is the key word :)

I already had a friend ask about changing themes and even before I said anything they said, "never mind" :)

I guess when I'm angry it shows ;)

---

### Post by effenberg0x0 on 2011-11-14
> **kansasnoob said:**
> I just want to clarify things. I'm NOT giving up my project but effenberg0x0 made a lot of sense. That became apparent very soon.

I'm just going to approach this from a different angle because I've spent a considerable amount of time searching for ways to get close to a true "classic" DE in 11.10 and I'm finding it's just not that hard at all :D

While I have it figured out I now need to figure out how to best present that to "everyone". Every other how-to I can find seems to contain serious flaws and/or omissions so I'm trying to come up with something that will just work.

But I'm busy with real life issues so it could take a while. That's why we have the forums, especially +1 :)

Hopefully what's being shared here will spur others into creating guides, etc :D

You're doing just fine. Let me tell you something that everyone that creates software, scripts, whatever will confirm to you:


[LIST]
[*]Creating something: 10% of the time
[*]Trying to make it easy, (as much as possible) universal, bulletproof, reversible, friendly, documented, etc: 20% of time
[*]Release and find out open flanks, things you haven't thought would even be possible, and try to do support to users: 50% of time
[*]Improve: 20% of time
[/LIST]
It always is the infamous PDCA (Plan, Do, Check, Act) cycle and it never is perfect. It can only get to be very good. Take your time on proper planning, it's always the most important thing.

---

### Post by jerrylamos on 2011-11-15
> I really appreciate all the work you have done on this kansasnoob. I started a thread back in testimonials quite some time ago about this very topic ...but members kept assuring me that GNOME classic would be taken care of .. etc.. and arguments were made that Unity is the way that Ubuntu is going .. and we better get used to it. I think that they are a lot of people working on this behind the scenes and perhaps they are just not enthusiastic as you are.

1.  Last posting I saw in Planet Ubuntu was that acceptance of the  "Unity" ubuntu versions was much lower than previous Ubuntu's.  Time will tell.

2.  I'm also running Lubuntu on a couple older test notebooks which isn't the full gnome capability but LXDM is of the traditional style desktop.  Do note I add gedit, samba for home network file sharing, Firefox, and when needed Libre Office writer.

3.  I'm keeping Lucid Lynx LTS and/or Meerkat partitions around in case of unstable Precise Pangolin screw ups.

4.  Main reason I run Unity-2D is to test whatever ubuntu development throws over the wall.  -3D is a real loser for me since I absolutely don't like fuzzy out of focus edges and blurry windows and Compiz chewing up cycles even when I'm running full screen applications like right now and everything Compiz is doing is absolutely useless.  

Have fun,

Jerry

---

### Post by kansasnoob on 2011-11-15
Back in [post #127]("http://ubuntuforums.org/showpost.php?p=11451297&postcount=127") effenberg0x0 (whom, along with many others here, has helped me immensely) said:

> I've been learning that people not always can cut/paste a "one-liner" like the one you created without making mistakes and ending up with a partial thing, in a state that its hard for anyone to provide support (we can't, remotely, really understand the current state). Asking for logs is usually a joke.

And I know that's true from past experiences of my own :(

So I'm going to do a trial and error post here regarding "copy-n-paste". I know that's not particularly an "Ubuntu +1" issue, but IMHO this is the safest place for "trials".

Here we go:

********************

Copying and pasting commands that are "wrapped" in code tags couldn't be simpler. First just move the mouse pointer to the "box" just below "Code:" and double-click to highlight the entire content as shown here:

[ATTACH]207236[/ATTACH]

Why is it important to double-click rather than just clicking on the left edge and dragging the mouse pointer to the right? Quite simply look at the two commands in "code tags" toward the bottom of that screenshot. 

You'll see that they both extend beyond the length of the "box" as indicated by the "scroll-bars" so if you "click-n-drag" rather than double-click you might end up with only a partial command.

In this second example I'm using the command at the bottom of the same page and I'm using "click-n-drag" rather than double-click:

[ATTACH]207237[/ATTACH]

But, since I mistakenly didn't "drag" to the very end, I ended up with:

> gconftool-2 --set "/apps/metacity/general/button_layout" --type string "

Instead of the intended:

> gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"

Simply double-clicking within the "Code:" box would have prevented that.

Then simply opening the terminal and selecting "paste" completes the copy-n-paste part of the procedure:

[ATTACH]207238[/ATTACH]

[ATTACH]207239[/ATTACH]

*******************

How good or bad of an idea is this?

Good idea but flawed presentation?

All opinions matter :)

Just BTW this is not because I'm rethinking my last position about largely disposing of the one-long-command, but even some single commnds extend past the end of the "Code:" box.

---

### Post by sgage on 2011-11-15
> **kansasnoob said:**
> Back in [post #127]("http://ubuntuforums.org/showpost.php?p=11451297&postcount=127") effenberg0x0 (whom, along with many others here, has helped me immensely) said:



And I know that's true from past experiences of my own :(

So I'm going to do a trial and error post here regarding "copy-n-paste". I know that's not particularly an "Ubuntu +1" issue, but IMHO this is the safest place for "trials".

Here we go:

********************

Copying and pasting commands that are "wrapped" in code tags couldn't be simpler. First just move the mouse pointer to the "box" just below "Code:" and double-click to highlight the entire content as shown here:

[ATTACH]207236[/ATTACH]

Why is it important to double-click rather than just clicking on the left edge and dragging the mouse pointer to the right? Quite simply look at the two commands in "code tags" toward the bottom of that screenshot. 

You'll see that they both extend beyond the length of the "box" as indicated by the "scroll-bars" so if you "click-n-drag" rather than double-click you might end up with only a partial command.

In this second example I'm using the command at the bottom of the same page and I'm using "click-n-drag" rather than double-click:

[ATTACH]207237[/ATTACH]

But, since I mistakenly didn't "drag" to the very end, I ended up with:



Instead of the intended:



Simply double-clicking within the "Code:" box would have prevented that.

Then simply opening the terminal and selecting "paste" completes the copy-n-paste part of the procedure:

[ATTACH]207238[/ATTACH]

[ATTACH]207239[/ATTACH]

*******************

How good or bad of an idea is this?

Good idea but flawed presentation?

All opinions matter :)

Just BTW this is not because I'm rethinking my last position about largely disposing of the one-long-command, but even some single commnds extend past the end of the "Code:" box.

How about a nice annotated shell script instead of cut'n'pasting from a code box? You could even comment everything out and have the user enable only those features that they understood and wanted.

Or just a step by step how-to. Big one-liner commands seem to always go wrong - no two systems ever seem to be the same.

---

### Post by kansasnoob on 2011-11-15
BTW I've been very busy but here's a simple new **uncompleted** text created in gedit:

[ATTACH]207241[/ATTACH]

Since I use gedit nothing's been spell checked yet, I'll do that later, but I have created a couple new screenshots that I think are better (sorry they're not included).

Lots more work to do, well not so much, it's just a matter of time allocation. But [B][COLOR="Red"]none of those commands have been tested for errors yet!
[/COLOR][/B]
Right now I'm taking a break from my "Oneiric classic project" and trying the newest Precise builds - maybe even the alternate image - just because I need a break and want to have some installer fun :D

---

### Post by kansasnoob on 2011-11-15
> **sgage said:**
> How about a nice annotated shell script instead of cut'n'pasting from a code box? You could even comment everything out and have the user enable only those features that they understood and wanted.

Or just a step by step how-to. Big one-liner commands seem to always go wrong - no two systems ever seem to be the same.

Regarding this:

> Or just a step by step how-to. Big one-liner commands seem to always go wrong - no two systems ever seem to be the same.

You obviously missed where I said there:

> Just BTW this is not because I'm rethinking my last position about largely disposing of the one-long-command, but even some single commnds extend past the end of the "Code:" box.


Which really refers to post #151 where I said:

> I've decided to try something different for Oneiric and since it will be for Oneiric only I'm going to pursue it elsewhere, probably in Main Support > Desktop Environments.

It will basically be a one-step-at-a-time guide with both CLI and GUI options. Basically begin by installing only 'gnome-session-fallback' and then move into an explanation of menu and panel changes.

That will have to include a bit about backing up configuration files or restoring unity/gnome-panel defaults, and probably next adding the 'jconti/gnome3' PPA so the 'indicator-applet', 'indicator-applet-complete', and 'indicator-applet-session' applets are included in "Add to panel".

Probably slip a bit in about Caffeine next, then move onto changing lightdm settings, and removing overlay-scrollbars if desired.

Then the rest (mostly) gets down to personalized tweaks, most of which can be done either via 'gnome-tweak-tool', Ubuntu tweak, or CLI.


But that new post has only to do with the need for a clear explanation about how to copy-n-paste commands.

I've since thought such a post needs to be led with a reference to avoiding malicious commands.

And I don't know how to create a shell script. Some day I may spend the time to learn how but ATM I want to share what limited knowledge I have in a method that I understand :)

---

### Post by sgage on 2011-11-15
> **kansasnoob said:**
> Regarding this:



You obviously missed where I said there:



Which really refers to post #151 where I said:



But that new post has only to do with the need for a clear explanation about how to copy-n-paste commands.

I've since thought such a post needs to be led with a reference to avoiding malicious commands.

And I don't know how to create a shell script. Some day I may spend the time to learn how but ATM I want to share what limited knowledge I have in a method that I understand :)

No, I didn't miss that. In fact, you put your finger on one reason why big one-liners are a bit spooky.

Anyway, a shell script is nothing but a text file. Nothing really to learn - you just put all those commands each on their own line. Any line prefaced by a # is a comment line and is not executed. If you put a # in front of an optional command, it is "commented out", and will not be executed unless the user edits the file and deletes the #, after reading the comment explaining what that command does.

To me, it's a much clearer way of presenting your sequence of commands. Just load your big old command line into gedit and hit enter after each command instead of && and you're good to go. 

I took your command line, made it into a script, and tweaked it to my preferences - see attached (you may have to set permissions to make it executable). Using the #, it's easy to turn lines on and off. Another nice thing about a script is you can just copy/paste single lines out of it into a terminal.

---

### Post by effenberg0x0 on 2011-11-15
> **sgage said:**
> How about a nice annotated shell script instead of cut'n'pasting from a code box? You could even comment everything out and have the user enable only those features that they understood and wanted.

Or just a step by step how-to. Big one-liner commands seem to always go wrong - no two systems ever seem to be the same.

I agree completely. Some conditions we would like to require, like "having a default Oneiric install" are subjective for the non-technical end-user. Wild guessing, he might have upgraded from Maverick and have legacy conflicting packages / settings, probably will find Kansasnoob thread after adding a ton of alternate PPAs, etc. Based on the feedback we see in terms of support requests after Kansasnoob posts his tutorial, we will have a better idea. And I can be totally wrong, sometimes users surprise us. But, unfortunately, not frequently enough :)

I, personally, gave up on the idea that end-users can read tutorials, perform whatever steps are asked in the right order, provide requested information, etc and went for automation scripts. See the scope I generally use on this thread, post [#127.]("http://ubuntuforums.org/showpost.php?p=11451297&postcount=127") If things get too complicated in terms of support when Kansasnoob publishes, I'll offer to fill in the functions in that script scope and automatize the entire process, as a contribution to his project. 

An example in automation is one of the things I do at work called  "Active Maintenance System (AMS)". It runs at every boot. So, for  example, a user boots to console (No vga driver? Wrong env vars?  Uninstalled critical packages? etc). Instead of opening a support  request to say that his screen is stuck on a dhcp or battery message  (unrelated, wastes time and money of support), he will see a message  saying that errors were detected and are being fixed. The system  auto-fixes whatever the problem is (hopefully) and puts him in a X  session automatically. If everything else fails, the system collects  proper info, auto publishes it to the right place, waits for a solution  (it's a xml file), download the solution, interpret it and apply it. No user interaction needed.

---

### Post by kansasnoob on 2011-11-15
I'm zsyncing some new Precise images ATM and I just wanted to add that anyone (or everyone) is welcome to take any part of what I'm doing and use it in any way they wish.

My personal goal is to show that Ubuntu has largely provided most of the tools needed to create a "classic" DE. The one thing that's slightly askew of that is the inability to add (or re-add) the 'indicator-applet', 'indicator-applet-complete', and 'indicator-applet-session' applets to the gnome-panel but I'd almost bet that'll be fixed in Precise.

I have no desire to detract from Ubuntu/Canonical's efforts to pursue the Unity DE, and I have no desire to create a new re-spin created on an Ubuntu base, although I did show some interest in UGR when it began towards the end of the Natty dev cycle. BTW it now appears UGR is dead!

I'm simply sick and tired of the FUD surrounding both Ubuntu and Gnome! During the Oneiric dev cycle I was busy with unrelated issues and I also shifted a great deal of my focus towards Lubuntu. Now I'm going to try and put a lot of the FUD to rest!

If cariboo907 finds this at all off-topic by all means feel free to toss it in the jail :)

I just want to clarify my intentions.

---

### Post by kansasnoob on 2011-11-15
Regarding both post #164 and #165 I'm just not comfortable with that ATM, but I will do some trials at some point.

May I assume that you both think a "copy-n-paste" from "Code:" how-to is a waste of time :confused:

After all that was the question :)

---

### Post by effenberg0x0 on 2011-11-15
> **kansasnoob said:**
> Regarding both post #164 and #165 I'm just not comfortable with that ATM, but I will do some trials at some point.

May I assume that you both think a "copy-n-paste" from "Code:" how-to is a waste of time :confused:

After all that was the question :)

No, not a waste of time at all. I just think that no matter how much effort you put into making this whole thing as detailed as you can (and I know how much goes into into trying to write the perfect how-to), users are users. They get anxious and jump steps, on purpose or for lack of focus, each has destroyed their system in a different way, etc. A good portion of users will be able to read and perform the steps you'll describe, but if 20% out of 1.000 users don't, you'll get crazy with support requests :) But it's not a waste of time, it's a trial, things never are perfect, even with with an automation script. You're going the right way. Things will evolve as they go. I can be totally wrong and users surprise me. 

If you ask them to copy/paste a one-liner, there's less chance they will forget/jump steps than if you post and describe commands separately (in my opinion). Maybe you can describe what each of the commands is doing in your tutorial and still offer the one-liner, or offer both, so users that feel uncomfortable with one way can have an alternate option.

---

### Post by effenberg0x0 on 2011-11-15
> **kansasnoob said:**
> I'm zsyncing some new Precise images ATM and I just wanted to add that anyone (or everyone) is welcome to take any part of what I'm doing and use it in any way they wish.

My personal goal is to show that Ubuntu has largely provided most of the tools needed to create a "classic" DE. The one thing that's slightly askew of that is the inability to add (or re-add) the 'indicator-applet', 'indicator-applet-complete', and 'indicator-applet-session' applets to the gnome-panel but I'd almost bet that'll be fixed in Precise.

I have no desire to detract from Ubuntu/Canonical's efforts to pursue the Unity DE, and I have no desire to create a new re-spin created on an Ubuntu base, although I did show some interest in UGR when it began towards the end of the Natty dev cycle. BTW it now appears UGR is dead!

I'm simply sick and tired of the FUD surrounding both Ubuntu and Gnome! During the Oneiric dev cycle I was busy with unrelated issues and I also shifted a great deal of my focus towards Lubuntu. Now I'm going to try and put a lot of the FUD to rest!

If cariboo907 finds this at all off-topic by all means feel free to toss it in the jail :)

I just want to clarify my intentions.

I think your intentions are clear for all of us. What I have tried, in my own troll way, to discuss in the infamous haters thread: Given that there are people that don't want to use Unity (and they have every right to), that people who want the classic look will probably go to great extents to re-enable it, that there are ridiculous / dangerous instructions arising everywhere on the net, a well made / secure / reversible way of doing that is a real need, considering this is the official forum. I wished things to be different but, at this point, I think there's no easy way to make things official here or in Ubuntu in general and the political way of doing things is just to boring. I support Ubuntu unconditionally, like (and use) Unity, and respect the development efforts put on it. But someone's gotta deal with the real world and support the users, all of them, including those that don't want Unity. Which is why I'm volunteering to whatever you need.

---

### Post by kansasnoob on 2011-11-15
> **effenberg0x0 said:**
> I think your intentions are clear for all of us. What I have tried, in my own troll way, to discuss in the infamous haters thread: Given that there are people that don't want to use Unity (and they have every right to), that people who want the classic look will probably go to great extents to re-enable it, that there are ridiculous / dangerous instructions arising everywhere on the net, a well made / secure / reversible way of doing that is a real need, considering this is the official forum. I wished things to be different but, at this point, I think there's no easy way to make things official here or in Ubuntu in general and the political way of doing things is just to boring. I support Ubuntu unconditionally, like (and use) Unity, and respect the development efforts put on it. But someone's gotta deal with the real world and support the users, all of them, including those that don't want Unity. Which is why I'm volunteering to whatever you need.

Couldn't agree more with that :)

Before this thread was started you'll remember that I asked about the sustainability of such a thread as this. I simply saw a need and wanted to pursue it :)

I was actually surprised at just how easy it was to get a fairly decent "classic" DE out of Oneiric. In other words there's a ton of FUD floating around harming Ubuntu and I don't like it!

---

### Post by sgage on 2011-11-15
> **kansasnoob said:**
> Regarding both post #164 and #165 I'm just not comfortable with that ATM, but I will do some trials at some point.

May I assume that you both think a "copy-n-paste" from "Code:" how-to is a waste of time :confused:

After all that was the question :)

Oh no! The fact of the matter is that you have identified the issues and the steps and written the commands - that's the main work. How it gets presented - whether a one liner, or cut'n'paste from a how-to, or a (very easily) customizable shell script is just icing on the cake. 

I took your one-liner and turned it into a shell script in 2 minutes. It was your work that made that no-effort. I hope you'll take a look at the script and see just how basic it is to make. You've already done the work!

:KS

---

### Post by cariboo on 2011-11-16
@kansasnoob, I fully support what you are doing, and if the thread wanders off topic for a couple of posts, I don't have a problem with that, I know it will be dragged back on topic again. :)

---

### Post by cbowman57 on 2011-11-16
@sgage, nice script btw.

I didn't run it but it's laid out so even somebody like me can make sense of it. :)

---

### Post by kansasnoob on 2011-11-16
Sitting here trying to figure out some financial stuff, I think we all love that, and my mind wandered off :)

It wandered into the thought of allowing folks a "test-drive" of sorts, which I'd mentioned before, and I'm wondering what would happen if a person were to create a new user account, then only install 'gnome-session-fallback', then log out and log back into the new user account selecting classic w/o effects?

That way if they totally trashed panel or DE settings fiddling around they'd not really have harmed their own account and all their personalized settings in their own /home would be left in tact :confused:

Any thoughts about that?

I guess it'd be worth trying in a couple of days just to see what happens.

---

### Post by effenberg0x0 on 2011-11-16
> **kansasnoob said:**
> Sitting here trying to figure out some financial stuff, I think we all love that, and my mind wandered off :)

It wandered into the thought of allowing folks a "test-drive" of sorts, which I'd mentioned before, and I'm wondering what would happen if a person were to create a new user account, then only install 'gnome-session-fallback', then log out and log back into the new user account selecting classic w/o effects?

That way if they totally trashed panel or DE settings fiddling around they'd not really have harmed their own account and all their personalized settings in their own /home would be left in tact :confused:

Any thoughts about that?

I guess it'd be worth trying in a couple of days just to see what happens.

It's a good idea. It would be easy to just add it to the commands also. Just add the guy, his $HOME, set a passwd, stop/start the DM.

sudo service lightdm stop
sudo useradd -d /home/new_username -m new_username 
sudo passwd new_username 
su -l new_username (Check: Is su OK? Or does he have to be really logged in to show in lightdm?)
sudo service lightdm start (Check: Is restarting the desktop enough? Not sure if the guy has to really be logged in, no su...)

I used useradd, instead of adduser because the second one it too interative (select shell, select home, etc - may confuse people). Also, it would be very easy to revert by simply moving /home/new_user/content_created.something except "dot" stuff (configs) to the default user home dir (UID 1000), chown the files back to him and remove the new user.

**EDIT: **Maybe (not sure, gotta test, running crazy in time now...) you could just export new values to $HOME, $USER, $USERNAME, $LOGNAME, $XAUTORITHY, pointing to a temporary directory (mktemp), copy necessary .config dirs from the default user there, sed them and run X. Would avoid the need to create and potentially remove a new temporary user later - would auto-reset at boot. There will probably be some caveats to solve though.

---

### Post by kansasnoob on 2011-11-16
I decided to see what happens in a guest session. It's pretty cool, don't know how Ubuntu pulled that of, but the guest session should actually be perfect for letting someone just piddle around a bit with panel settings and such.

Evidently whatever changes would typically be "stored" in home/hidden are always recreated each time you login to a guest session. So I could just recommend that folks login to a guest session, piddle around with the panels a bit to familiarize themselves, and only when they're comfortable make those changes they desire in their own account.

Friday I should have time to run through a full round of testing regarding that.

---

### Post by effenberg0x0 on 2011-11-16
> **kansasnoob said:**
> I decided to see what happens in a guest session. It's pretty cool, don't know how Ubuntu pulled that of, but the guest session should actually be perfect for letting someone just piddle around a bit with panel settings and such.

Evidently whatever changes would typically be "stored" in home/hidden are always recreated each time you login to a guest session. So I could just recommend that folks login to a guest session, piddle around with the panels a bit to familiarize themselves, and only when they're comfortable make those changes they desire in their own account.

Friday I should have time to run through a full round of testing regarding that.

It suddenly strikes me you could try a new approach. The Sound of Music approach.


> (Maria) Now children pay attention! Maria, the governess, will teach you how to have a classic gnome look!
(Maria) Do-re-mi-fa-so-la-ti
(Maria) Let's see if I can make it easy...

[I]Doe, a gnome, a female gnome
Ray, a lightening fast menu
Me, the same as $USERNAME
Far, two taskbars apart
Sew, sed 's/d/w/g' "sed"
La, can't think of anythingaaaa 
Tea, when you're out of coffeeeee
That will bring us back to Do! 

[/I](Maria) Good job children!
(Maria) Now sing this: sudo add-apt-repository ppa:jconti/gnome3 && sudo add-apt-repository ppa:caffeine-developers/ppa && sudo apt-get update && sudo apt-get install gnome-session-fallback caffeine indicator-applet indicator-applet-complete indicator-applet-session && sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-fallback && sudo apt-get purge liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0 overlay-scrollbar && gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close" && gsettings set org.gnome.desktop.interface menus-have-icons true && gsettings set org.gnome.desktop.interface buttons-have-icons true && gsettings set org.gnome.desktop.background show-desktop-icons true && gsettings set org.gnome.nautilus.desktop volumes-visible true && gsettings set org.gnome.nautilus.desktop computer-icon-visible false && gsettings set org.gnome.nautilus.desktop home-icon-visible false && gsettings set org.gnome.nautilus.desktop trash-icon-visible false && gsettings set com.ubuntu.update-notifier auto-launch false && gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true' && cp -a .config .config_OLD && cp -a .gconf .gconf_OLD && cp -a .gnome2 .gnome2_OL

(Children): WTF?
(Maria) Good luck in life.

---

### Post by sgage on 2011-11-16
> **effenberg0x0 said:**
> It suddenly strikes me you could try a new approach. The Sound of Music approach.

That makes it so much more user friendly! :KS

---

### Post by kansasnoob on 2011-11-17
I've been playing with Precise the past couple of days and here's where I'm at with it, **[COLOR="Red"]since things may change rapidly at this stage of development please let us know if you notice any changes[/COLOR]**:

Before beginning please understand that I'm no genius (nor a dev), far from it, but I wanted a Classic DE in Precise with the newest version of Gnome so I did some studying. **This is for "classic without effects" only!** I've never cared for compiz anyway and it seems to be difficult to get it to run in a classic Precise DE. So, **[COLOR="Red"]if you want compiz this thread is NOT for you[/COLOR]**, sorry. 

Also, there are no guarantees! I've tested this quite a bit, but only with fresh Ubuntu Precise installs. Your mileage may vary with installations that have other underlying problems. I can only say that it works for me, no more and no less. Please DO read this all before beginning and remember it's only for Ubuntu Precise!

The only thing I personally dislike about the entire default Ubuntu "classic theme" after applying all of my tweaks is the scrollbar "button" color - I'd prefer it to match the window decoration (dark gray), but I've found worse flaws in all other themes I've tried so far, so I'm just sticking with the default Ambiance theme. I honestly forget I'm even using Gnome 3 most of the time now.

************

Important note: This guide is heavily reliant on copy-n-pasting commands into gnome-terminal. Why? Quite simply not ALL of this can be completed using GUI tools like Ubuntu Tweak or 'gnome-tweak-tool', and installing 'gnome-tweak-tool' results in installing a great deal of unneeded packages, including 'gnome-shell', and my only concern is getting a "classic w/o effects" DE running efficiently.

But copying and pasting commands that are "wrapped" in code tags couldn't be simpler: 

[http://ubuntuforums.org/showpost.php?p=11459388&postcount=160](http://ubuntuforums.org/showpost.php?p=11459388&postcount=160)

Also, if I didn't include "sudo" in the command then it's not needed, and in rare instances may result in changed permissions, so just copy-n-paste!

************

First let's look at what I ended up with and then I'll explain how I got there:

[ATTACH]207388[/ATTACH]

You'll notice that I prefer only one panel at the bottom. I realize some may want two panels, or one at the top only, it's purely a matter of preference. Be patient and I'll do my best to explain things. Just FYI my panel layout (beginning from the left) consists of:

Hide button/Main Menu/Terminal/Workspace Switcher/Screenshot/Opera/Firefox/Window List/_________/Caffeine/Indicator Applet/Clock/Trash/Hide button

And you'll notice that the Indicator Applet displays: /Update notifier/Network widget/Mail widget/Volume widget

And this is as good a time as any to pause and discuss changes to the menu(s) and panel(s). You'll notice that the menu(s) have changed as shown in a later screenshot, but I think you'll likely find what you want if you just spend a couple of minutes familiarizing yourself with the new menu layout, be sure to check the Other and System Tools > System Settings categories. You'll find most of what you're used to seeing in System > Administration and System > Preferences is now just relocated.

You also need to know that you must now hold down either Alt key while right-clicking on a panel or applet to be able to edit panel preferences or to add/edit/move/remove more applets. That was an intentional move by the Gnome devs to prevent people from unintentionally breaking things. And you also can't just add application applets by right-clicking them and selecting "add to panel". You must now open the "add-to-panel" window and select Application Launcher > Forward, then the window changes and you can click on the "bullet" to the left of each category to display and add any app in the menu to the panel:

[ATTACH]207389[/ATTACH]

But lets also look at Panel Properties settings. Note here that in Panel Properties > Background I've found that 'Solid color' > Color > Color name #3F3E39 results in improved appearance of the Workspace Switcher.

[ATTACH]207390[/ATTACH]

Still interested? If so we start with two simple steps:

**Step #1**: The first step is very easy, you simply install the package 'gnome-session-fallback':

```
sudo apt-get install gnome-session-fallback
```

**Step #2**: I consider this important! Currently the "Add to panel" list of applets/widgets lacks 'indicator-applet', 'indicator-applet-complete', and 'indicator-applet-session'. In fairness a "light" version of the 'indicator-applet' exists in the default classic top panel at the far right, but if you should accidentily remove it you won't be able to restore it very easily. So I highly recommend installing this PPA and then installing it's version of 'indicator-applet', 'indicator-applet-complete', and 'indicator-applet-session':

[https://launchpad.net/~jconti/+archive/gnome3](https://launchpad.net/~jconti/+archive/gnome3)

Right now there is no Precise version of this PPA and the "edit" function in the Software Sources GUI appears to be broken as of 11/17/2011 so you must first run this command to install:

```
sudo add-apt-repository ppa:jconti/gnome3
```

Then change "precise" to "oneiric" in /etc/apt/sources.list.d/jconti-gnome3-precise.list using gedit:

```
gksudo gedit /etc/apt/sources.list.d/jconti-gnome3-precise.list
```

Remember to "save" before closing, then continue:

```
sudo apt-get update
```

```
sudo apt-get install indicator-applet indicator-applet-complete indicator-applet-session
```

Once that's done you're nearly ready to have a look at your new "classic" desktop, but due to the aforementioned changes in how panels and/or applets are edited I highly recommend a brief testdrive in a classic w/o effects Guest session just to get a feel for editing the panels/applets. It's perfectly safe to do so because the defaults are restored in a Guest session on every login (meaning no changes are saved). To try the classic DE in a Guest session simply choose to "switch user" and be sure to select the "classic w/o effects" session after clicking on Guest, no password is required.

Alternately you might consider creating a new user account for running classic in order to make the changes more permanent, but only in that new user account. That way your Unity settings will not be changed at all. You'd just choose which user account to log into and then you can later decide what you prefer. You can read more about creating a new user account here:

[https://help.ubuntu.com/11.10/ubuntu-help/user-accounts.html](https://help.ubuntu.com/11.10/ubuntu-help/user-accounts.html)

Whatever user account you choose to use, upon first boot the new classic DE should look like this:

[ATTACH]207391[/ATTACH]

Assuming you took a test drive, how did it go? Still interested? If so please consider two more things before logging into the new classic DE in your original user account:

**Step #3**: If you've customized Unity quite a bit and now have it nearly to your liking I highly recommend backing up some configuration files before applying any tweaks to the new classic DE so they can be restored at a later date if you decide to return to Unity, but this is totally optional:

```
cp -a .config .config_OLD
``` 

```
cp -a .gconf .gconf_OLD
``` 

```
cp -a .gnome2 .gnome2_OLD
```

Note: I'll provide more info regarding either restoring those files or restoring all out-of-box defaults later.

Now we can move on to other totally optional tweaks. Apply only those tweaks desired: 

**Tweak #1**: I find the overlay-scrollbars to be inconsistent and annoying in the classic DE so I remove them, but this is totally a matter of preference:

```
sudo apt-get purge liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0 overlay-scrollbar

```
Note: you may need to reboot for that change to fully take effect.

**Tweak #2**: I find the screen locking thing very annoying, I live alone and don't like having to enter my password everytime the screen-"blanker" acivates. So you can just go to System Tools > System Settings > Screen and select Lock = Off. Note; I call it a screen-"blanker" partly as a joke because it hardly resembles a screensaver anymore. This can also be done with Ubuntu Tweak.

**Tweak #3**: While we're talking about the screen-"blanker" let's talk about Caffeine:

[https://launchpad.net/~caffeine-developers/+archive/ppa](https://launchpad.net/~caffeine-developers/+archive/ppa)

In my original screenshot the caffeine applet shows up next to the indicator-applet. I find it to be a sweet replacement for the old 'gnome-inhibit-applet'. Once installed and set up it allows you to "inhibit" the screen-"blanking", I think a picture is worth a thousand words so here:

[ATTACH]207392[/ATTACH]

Should you choose to install it you can setup Caffeine by going to Other > Caffeine preferences. Installation is easy:

```
sudo add-apt-repository ppa:caffeine-developers/ppa
```

```
sudo apt-get update
```

```
sudo apt-get install caffeine
```

**Tweak #4**: I also prefer having the old style update notifications in the panel via indicator-applet so I run:

```
gsettings set com.ubuntu.update-notifier auto-launch false
```

Note: The remaining tweaks can also be applied using Ubuntu Tweak. Should you want to use Ubuntu Tweak you'll need to run these three commands:

```
sudo add-apt-repository ppa:tualatrix/next
```

```
sudo apt-get update
```

```
sudo apt-get install ubuntu-tweak
```

It then appears in the app menu under Other > Ubuntu Tweak. Just be aware that Ubuntu Tweak offers additional options that I have not tested, so I will not be able to help you sort out issues related to it's use! And I detest the "janitor"!

**Tweak #5**: Also totally optional, but I still personally prefer the window buttons on the right so I run:

```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"
```

Or using Ubuntu Tweak click on the Tweaks tab > Window Manager Settings and make the proper selection.

**Tweak #6**: I also dislike the missing menu and button icons so I run:

```
gsettings set org.gnome.desktop.interface menus-have-icons true
``` 

```
gsettings set org.gnome.desktop.interface buttons-have-icons true
```

Or using Ubuntu Tweak click on the Tweaks tab > Miscellaneous and make the proper selections.

**Tweak #7**: By default the desktop is not set to display any icons, but I personally want the desktop to display only mounted volumes (like when I plug in a USB drive).

Due to the number of commands required in this step, and the options of displaying any combination of "Mounted Volumes", "Computer", "Home", and "Trash" icons on the desktop I guess I'd have to recommend Ubuntu Tweak over the CLi in this step for all but advanced users.

That being the case in Ubuntu Tweak click on the Tweaks tab > Miscellaneous and make the proper selection.

But the most consistent CLI method I've found to remedy this is running the command:

```
gsettings set org.gnome.desktop.background show-desktop-icons true
```

But you might find that results in the desktop displaying "Mounted Volumes", "Computer", "Home", and "Trash" icons on the desktop. I personally want the desktop to display only mounted volumes so I additionally run:

```
gsettings set org.gnome.nautilus.desktop volumes-visible true
```

```
gsettings set org.gnome.nautilus.desktop computer-icon-visible false
```

```
gsettings set org.gnome.nautilus.desktop home-icon-visible false
```

```
gsettings set org.gnome.nautilus.desktop trash-icon-visible false
```

If you study those commands a bit you'll notice the apparent difference is the "true" or "false" at the very end of each command.

**Tweak #8**: Hardware Sensors Indicator is now working in gnome panel, but only with the versions of 'indicator-applet' and 'indicator-applet-complete' packaged in the PPA listed in Step #2. It's a great replacement for 'gnome-sensors-applet' or 'comtutertemp'. I posted more about it in posts [#185]("http://ubuntuforums.org/showpost.php?p=11466689&postcount=185") and [#187]("http://ubuntuforums.org/showpost.php?p=11466796&postcount=187").



**Tweak #9**: System Monitor Indicator is now working in gnome panel, but only with the versions of 'indicator-applet' and 'indicator-applet-complete' packaged in the PPA listed in Step #2. More about that it post [#208]("http://ubuntuforums.org/showpost.php?p=11473552&postcount=208").

---

### Post by kansasnoob on 2011-11-17
Things that currently need much more testing:

#1: It may no longer be neccessary for those who auto-login to "set" the default by running "sudo /usr/lib/lightdm/lightdm-set-defaults -s whatever_session", but I'm not sure.

#2: I'm not sure about the need to disable the global-menu addons in Firefox or Thunderbird. That's why it's ommitted in that last post.

#3: Need to followup on these two projects:

[https://launchpad.net/indicator-sensors](https://launchpad.net/indicator-sensors)

[https://launchpad.net/indicator-sysmonitor](https://launchpad.net/indicator-sysmonitor)

And I have to watch for things to completely break :D

---

### Post by TerryNewton on 2011-11-17
This is an interesting thread! I already discovered a while back that Gnome 3 could provide pretty much the same "experience" as good old Gnome 2 minus incompatible applets, but looks like even some of that is being addressed.

My concerns as far as pasted commands or scripts is 1) some users are so unfamiliar with the command line that they're bound to mess it up, close the window before completed, etc, and 2) what happens if the user re-runs the script or commands? So a scripted solution should at least avoid overwriting the previously saved backup settings (or make that a separate step), the other commands should be fairly safe if re-run but need to test and try to break it - if possible users will find a way. However for more "tricked out" configurations, a script is probably the way to go.

For ordinary users who can't deal with a command line, the easiest way to get classic gnome is to simply open the Ubuntu software center, type gnome-session-fallback in the search box, install it, log out and select one of the Gnome Classic sessions. No commands needed. In my testing with 12.04 desktop icons were already enabled, but if not the simplest way to fix that is install gnome-tweak-tool, which also pulls in Gnome Shell for another environment to play around in. Or get brave and open a terminal and type the gsettings commands. Or install gconf-tools and dconf-editor and (carefully) poke around. Some configurations look better if the compositing box is checked under metacity. Not crazy about how the bottom panel looked so I removed it and installed lxpanel instead, using a custom bash script to start it with a custom config that supplies only a window list depending on the $DESKTOP_SESSION variable - but that gets slightly advanced. Actually my favorite 12.04 environment at the moment is lxpanel only, copied the fallback session files (.session and .desktop) and edited to not start gnome panel. It's similar to LXDM but with nautilus handling the desktop.

Gnome Classic is mostly just like Gnome 2 (for me anyway) but the option to create desktop launchers isn't there any more. Existing menu items can be simply dragged to the desktop so not a big deal unless something custom is needed... I use the following script in ~/.gnome2/nautilus-scripts to create launchers pointing to anything...

#!/bin/bash
gnome-desktop-item-edit --create-new $(pwd) &

...save as CreateLauncher in nautilus-scripts and make it executable.

---

### Post by kansasnoob on 2011-11-17
It may very well be possible get by with only installing 'gnome-session-fallback' by the time Precise is released, or it may be blown all to heck - though I doubt it since we're mostly working from Debian testing in this cycle.

But, of the four "steps" I currently list:

I very much expect step #2 to no longer be needed at some point during Precise development.

It appears that step #4 may no longer be needed ATM

And step #3 is optional and I've actually questioned the wisdom behind it myself.

Then everything else is listed as an optional tweak, and most of those can be done using either Ubuntu Tweak or 'gnome-tweak-tool'.

So I think it may well come down to being nearly all a GUI operation for those who are CLI challenged ;)

---

### Post by cariboo on 2011-11-17
If as I suspect, that gnome classic will be available through the life of the LTS release, there is plenty of time for kansasnoob's script to be perfected, and howtos on the forum to be created.

If you've used Ubuntu to for any amount of time, you'll remember that back in 2006, it was nowhere as easy to setup the desktop as it is now, there were applications and scripts created by other users to install multimedia codecs and other applications, instructions on how to get the cube working and more.

I have faith in our members, that they will step up to the plate, and make it just as easy to setup the classic desktop, as it was previously.

As far as creating a GUI app to do the modifications needed, we can collaborate on that once kansasnoob's script has been finalized.

---

### Post by kansasnoob on 2011-11-17
> **cariboo907 said:**
> If as I suspect, that gnome classic will be available through the life of the LTS release, there is plenty of time for kansasnoob's script to be perfected, and howtos on the forum to be created.

If you've used Ubuntu to for any amount of time, you'll remember that back in 2006, it was nowhere as easy to setup the desktop as it is now, there were applications and scripts created by other users to install multimedia codecs and other applications, instructions on how to get the cube working and more.

I have faith in our members, that they will step up to the plate, and make it just as easy to setup the classic desktop, as it was previously.

As far as creating a GUI app to do the modifications needed, we can collaborate on that once kansasnoob's script has been finalized.

Even when I began using Ubuntu during Gutsy I recall having to use the CLI for as few things. I don't remember what the first was but someone listed the three commands, one on top of another, in one code box like:

```
command one
command two
command three
```

And I remember having quite a chuckle when I figured out that I needed to paste each one separately :D

---

### Post by kansasnoob on 2011-11-17
Hardware Sensors Indicator now working in gnome panel:

[ATTACH]207451[/ATTACH]

Look where I'm pointing in the lower right hand corner.

It's a bit sloppy to install ATM, and I'll be back to explain it, but I need to take the dogs for a "happy dance" walk ........... struttin' with two doxies :lolflag:

I think my pointing stinks. Look in the panel, I have only a bottom panel, between the Caffeine applet and the Indicator Applet. I'm lovin' it!

---

### Post by effenberg0x0 on 2011-11-17
@Kansasnoob 
Do you plan to also write the "How to undo" tutorial and, if so, in this level of detail? It's a lot of work. 

I have finally delivered something that was killing me at work and will start to try your instructions. I have created a script that clones and launches a default (ISO) of Oneiric or PP install in a VM, so I can do tests many times without having to install / reinstall the distro every time I test it. This will mainly be used to test your stuff.

---

### Post by kansasnoob on 2011-11-17
**[COLOR="Red"]Important:[/COLOR]** I discovered this AM that Hardware Sensors Indicator only works properly with the versions of 'indicator-applet' and 'indicator-applet-complete' packaged in this PPA:

[https://launchpad.net/~jconti/+archive/gnome3](https://launchpad.net/~jconti/+archive/gnome3)

About installing Hardware Sensors Indicator, the PPA is here:

[https://launchpad.net/~alexmurray/+archive/indicator-sensors](https://launchpad.net/~alexmurray/+archive/indicator-sensors)

But you'll see that no Precise version is available so you must run:

```
sudo add-apt-repository ppa:alexmurray/indicator-sensors
```

But then you must rename the repo version so it looks for "oneiric". You can first try to access Software Sources either through System Settings, Update Manager, or Synaptic but I've found the GUI to be unreliable lately. So you may have to manually edit "/etc/apt/sources.list.d/alexmurray-indicator-sensors-precise.list".

Clear :confused:

Then you must naturally update the package list:

```
sudo apt-get update
```

And install the package 'indicator-sensors':

```
sudo apt-get install indicator-sensors
```

Now "Hardware Sensors Indicator" should show up in System Tools. Frome here I think a picture is worth a thousand words:

[ATTACH]207452[/ATTACH]

I'm lovin' it!

Just BTW this works equally well in the Unity top panel.

---

### Post by kansasnoob on 2011-11-17
> **effenberg0x0 said:**
> @Kansasnoob 
Do you plan to also write the "How to undo" tutorial and, if so, in this level of detail? It's a lot of work. 

I have finally delivered something that was killing me at work and will start to try your instructions. I have created a script that clones and launches a default (ISO) of Oneiric or PP install in a VM, so I can do tests many times without having to install / reinstall the distro every time I test it. This will mainly be used to test your stuff.

Pursuing only "classic w/o effects" it so far appears that very little "UNDO" would be needed, but it's apparent I've given that some thought by including:

```
cp -a .config .config_OLD
cp -a .gconf .gconf_OLD
cp -a .gnome2 .gnome2_OLD

```

But I'm now looking at 'deja-dup' which I've personally never used. Believe me, I'm anal retentive about data loss and/or destroying an OS ;)

I've lost data to flood, fire, and a malicious ex-wife so I just have my own "back-up" plan which includes tupperware, many removable drives, and a fireproof gun safe :D

And I "save" often :)

---

### Post by kansasnoob on 2011-11-17
> **effenberg0x0 said:**
> @Kansasnoob 
Do you plan to also write the "How to undo" tutorial and, if so, in this level of detail? It's a lot of work. 

I have finally delivered something that was killing me at work and will start to try your instructions. I have created a script that clones and launches a default (ISO) of Oneiric or PP install in a VM, so I can do tests many times without having to install / reinstall the distro every time I test it. This will mainly be used to test your stuff.

Just thought to add:

Most of the things done in my latest "guide" in post #179 do no harm whatsoever to the default Ubuntu DE, but some can screw up untity-2d.

I am very mindful of that ;)

---

### Post by effenberg0x0 on 2011-11-17
> **kansasnoob said:**
> Just thought to add:

Most of the things done in my latest "guide" in post #179 do no harm whatsoever to the default Ubuntu DE, but some can screw up untity-2d.

I am very mindful of that ;)

As soon as I get to start the testing I'll try to report you in details how the procedure went, if any challenge was found, etc.

---

### Post by kansasnoob on 2011-11-18
I did some repeat testing this AM and I can confirm that it is no longer necessary to run "sudo /usr/lib/lightdm/lightdm-set-defaults -s whatever_session" even if you auto-login.

Just making a selection once makes it "stick", meaning one less step.

---

### Post by kansasnoob on 2011-11-19
I've really been thinking about the best way to present this and really two questions come to mind:

Question #1: How safe is it to post CLI guides?

Answer: While it's a bit rude to answer a question with a question my simple answer is, how safe is it, or has it been, to offer GUI tools such as the Computer Janitor, The Disk Utility, etc?

IMHO it simply comes down to presenting things as best one can, trying to provide ample warnings, and providing GUI options where reasonable.

If I decide to go forward with my Oneiric guide, which I beleive I will, I almost think it's **unreasonable** to offer much GUI info (other than setting up newly installed apps) because the use of PPA's is almost inevitable for an enjoyable outcome.

So if they can't be successful with what I now list as Step #1 and Step #2 in post #179 then why proceed at all?

Note: Just a reminder, that's really for Precise only as some improvements have already been made in Precise.

Also 'gnome-tweak-tool' installs too many unneeded packages for a "classic w/o effects" session which is my sole focus, and Ubuntu Tweak still has that dreaded janitor :(

Question #2: What if someone wants to go back to Unity?

Answer: I've given that quite a bit of thought. Just performing the aforementioned Step #1 and Step #2 really have no effect whatsover on the Unity or Unity-2D sessions.

I like the idea of recommending a brief "test-drive" in a guest session just so someone can familiarize themselves with editing the panels because no changes are saved.

And, as my Precise guide currently says in Step #3, if you've customized Unity quite a bit and now have it nearly to your liking I highly recommend backing up some configuration files before applying any tweaks to the new classic DE so they can be restored at a later date.

I do need to write a simple guide about how to restore those backed up configuation files, but that's easy, and it can be done either via CLI or GUI :)

I have however thought that even though I clearly warn I'm only focusing on "classic w/o effects" I should probably also add ".compiz" to the list of files to backup.

Any thoughts?

---

### Post by cbowman57 on 2011-11-19
I like your approach, it's effective & comprehensive, but nothing is entirely foolproof. 

I think it would be safe to assume that if a user has the desire to retain the traditional desktop they are also somewhat familiar with how to accomplish it.  They just need the recipe.

---

### Post by effenberg0x0 on 2011-11-19
Yes, backing up .compiz is a good idea. If a user has the desire to revert to Unity, having no compiz settings defined, there's a risk of logging on to a desktop with no panel/launcher (unusable) since this provided by the Unity Compiz plugin. Or even if the default settings are loaded successfully (they weren't until some time ago and it still is not rock solid), he may loose all his previous customizations to Unity appearance. Maybe the gconftool-2 command to activate (or ensure activation) of the Unity plugin should be mentioned in the "revert" part of it.

---

### Post by jacob lastman on 2011-11-19
[IMG]file:///home/phil/GNOME%20classic.png://[/IMG][IMG]http://ubuntuforums.org/home/GNOME%20classic.png[/IMG][IMG]http://ubuntuforums.org/home/Gnome%20classic.png[/IMG]

greetings - please see my post in community general 'coffee' forums....i use 10.10 with gnome 2.32 and it is fantastic....what else do you need?...i come from a highly technical work background and this can hardly be improved upon.

please allow an easy and quick 'desktop rollback' as we go forward

thanks for good work

---

### Post by kansasnoob on 2011-11-19
I'm back in painting mode ATM, meaning I'm mostly away from the desk, but I had a possibly silly idea and thought I'd toss it out here.

As previously mentioned I very much like the idea of providing a "sneak peak", and one way to briefly get a feel for how the new panels work is using a guest session.

If someone wants to play a bit longer they could easily create a new admin user account and then just dump it if they choose to go full-blown "classic w/o effects".

But I had a sort of odd idea, and I know some here have created Live CD's for various re-spins. Be mindful here that I have no problem with the direction anyone else has decided to take. That's the beauty of FOSS :)

In my particular situation I have no desire to create an installable re-spin, but I wonder if it's possible to create a Live CD/DVD (I'm guessing it would require a DVD) that is NOT installable, but that has all of my personalized tweaks applied just to use as a "test-drive"?

Is it possible? If so what live image creation tools are currently available and up to date?

I've seen that remastersys is no longer being developed, and I thought it wise to get some advice before seriously considering such a venture.

Just repeating, I specifically DO NOT want it to be installable! It's to be used only as a sneak-peak, then if folks like it they can follow a guide to apply only those tweaks that they desire to an actual Ubuntu installation.

Probably just a silly thought :(

---

### Post by cbowman57 on 2011-11-19
Remastersys is active again, and I've tested it with both 11.10 & 12.04.

With the recent improvements it would be super simple for you to create a respin to test your ideas with.

For anyone that just wants Gnome classic though I have no problem recommending [Freezy]("http://freezylinux.altervista.org/")[URL="http://freezylinux.altervista.org/http://freezylinux.altervista.org/"]
[/URL]

---

### Post by KBD47 on 2011-11-19
I'm mostly a noob at this stuff myself, but I've been playing around with the Gnome 2 fork MATE in Mint 12 RC and it is coming together nicely. I would think this should be available for Ubuntu or accessible to Ubuntu.
  MATE is not as nice as Gnome 2, but I find it easier to configure than Gnome 3 Fallback. Only two issues I have right now with MATE is that the font rendering could be better and sound control has to be managed on the desktop rather than from my fn up/down buttons on my keyboard. But I expect MATE will get better in time.
KBD47

---

### Post by ventrical on 2011-11-19
> **cbowman57 said:**
> Remastersys is active again, and I've tested it with both 11.10 & 12.04.

With the recent improvements it would be super simple for you to create a respin to test your ideas with.

For anyone that just wants Gnome classic though I have no problem recommending [URL="http://freezylinux.altervista.org/http://freezylinux.altervista.org/"]Freezy.
[/URL]


 I tried that a few weeks back .. even did an install of it.  Basically a nice re-mix of gnome.

---

### Post by cbowman57 on 2011-11-19
> **ventrical said:**
> I tried that a few weeks back .. even did an install of it.  Basically a nice re-mix of gnome.

If I wanted just Gnome classic & didn't want to try & configure it on my own that's the direction I would go.  However I do understand the point of this exercise. :)

---

### Post by ranch hand on 2011-11-19
> **cbowman57 said:**
> Remastersys is active again, and I've tested it with both 11.10 & 12.04.

With the recent improvements it would be super simple for you to create a respin to test your ideas with.

For anyone that just wants Gnome classic though I have no problem recommending [URL="http://freezylinux.altervista.org/http://freezylinux.altervista.org/"]Freezy.
[/URL]
Link did not work for me, gave some error about no index.

Did a search.  Hope this one works.
[http://freezylinux.altervista.org/](http://freezylinux.altervista.org/)

---

### Post by cbowman57 on 2011-11-19
Thanks ranch hand, I corrected the link.

---

### Post by sgage on 2011-11-19
> **ranch hand said:**
> Link did not work for me, gave some error about no index.

Did a search.  Hope this one works.
[http://freezylinux.altervista.org/](http://freezylinux.altervista.org/)

He doubled up the URL, that's all. BTW, I'm coming to you right now from Freezy. One panel (bottom), Chromium instead of Firefox. I've installed FF and Thunderbird, and it seems to be working fine.

I am interested in these excursions (Freezy, Mint, etc.) because I think that Ubuntu has the best repos, and the best default fonts and rendering. I have tried just about everything over the years, and nothing seems to look as good to my tired eyes as Ubuntu and its derivatives. So knowing that there are these "spins" out there is reassuring, because launcher/docky business on the left side is simply not for me. I just hope that Ubuntu doesn't drop Gnome Classic from PP.

---

### Post by cbowman57 on 2011-11-19
Are there any objections to requesting that a moderator relocate some of these Freezy comments to this thread?  [http://ubuntuforums.org/showthread.php?t=1874552&highlight=Freezy](http://ubuntuforums.org/showthread.php?t=1874552&highlight=Freezy)

I don't want to dilute this thread.

---

### Post by kansasnoob on 2011-11-19
> **cbowman57 said:**
> Are there any objections to requesting that a moderator relocate some of these Freezy comments to this thread?  [http://ubuntuforums.org/showthread.php?t=1874552&highlight=Freezy](http://ubuntuforums.org/showthread.php?t=1874552&highlight=Freezy)

I don't want to dilute this thread.

I think it's OK to leave the Freezy links and comments here. Lucazade has provided invaluable info since this thread began and I think we should be able display all "classic" Gnome 3 options.

I'm not so sure about Mate because it's truly not Gnome 3 :confused:

Not and sure are the keywords :D

I'm just not sure.

---

### Post by kansasnoob on 2011-11-19
> **ranch hand said:**
> Link did not work for me, gave some error about no index.

Did a search.  Hope this one works.
[http://freezylinux.altervista.org/](http://freezylinux.altervista.org/)

Are you still unable to install from any Ubuntu iso?

---

### Post by ranch hand on 2011-11-19
> **kansasnoob said:**
> Are you still unable to install from any Ubuntu iso?
Not since 10.04 final.  10.04RC was fine.

All the rest make the HDD sound like a rock crusher.

Strange thing is that Xubuntu and Lubuntu disks are fine.

The install Ubuntu 1204-testing I used a 11.10 mini and upgraded it.  Worked fine that far.  No way in hell is Ubuntu going on here.  Just won't install.  This worked up through Ubuntu 11.10-testing A1, the last time I actually installed Ubuntu.

Did the same thing for 2 installs of Xubuntu 12.04-testing.  Worked fine.

Debian Sid goes fine, Gnome3, Gnome Shell and all, has since those packages were in the experimental repo so I doubt it is related to anything other than some big improvement on Ubuntus part.

This is fine with me, I am happy where I am.  It does seem strange that an outfit would just write off fairly new, fairly common, mainstream hardware configurations.  Did buy this at that noted custom computer store - Walmart.  I think that is about as generic as it gets.

---

### Post by kansasnoob on 2011-11-20
System Monitor Indicator also working properly in 'gnome-panel' now:

[ATTACH]208064[/ATTACH]

[https://launchpad.net/indicator-sysmonitor](https://launchpad.net/indicator-sysmonitor)

But only with the versions of 'indicator-applet' and 'indicator-applet-complete' packaged in this PPA:

[https://launchpad.net/~jconti/+archive/gnome3](https://launchpad.net/~jconti/+archive/gnome3)

**[COLOR="Red"]Important update[/COLOR]**: As of June 10, 2012 only the Oneiric package is available but it does work in Precise! However the native 'indicator-applet' and 'indicator-applet-complete' packages in Precise are newer than those in the aforementioned packages in JConti's PPA.

So, if you want 'indicator-sysmonitor' in Precise, you need only download the .deb and install it :)

---

### Post by KBD47 on 2011-11-20
Watching this thread with interest. As mentioned earlier I have been trying out Mint 12 RC. Some others who have been trying it out also prefer Gnome  Classic even though Mint has the extensions to help it look more classic. Hoping very much Gnome Classic makes it into the LTS release next Spring.
  A couple of questions, I removed the bottom bar and moved the top bar to the bottom, using just one bar it has limited space and I'm not thrilled with the "Applications" and "Places" buttons as they are taking up too much space. Is there a way to replace that Applications Menu with just an Applications button? Is there a way to just have folders on my desktop in classic and do away with the "Places" button?
  Lastly, what do I lose choosing Classic w/o effects? Will it be much lighter/faster?
Thanks.
KBD47

---

### Post by kansasnoob on 2011-11-20
> **KBD47 said:**
> Watching this thread with interest. As mentioned earlier I have been trying out Mint 12 RC. Some others who have been trying it out also prefer Gnome  Classic even though Mint has the extensions to help it look more classic. Hoping very much Gnome Classic makes it into the LTS release next Spring.
  A couple of questions, I removed the bottom bar and moved the top bar to the bottom, using just one bar it has limited space and I'm not thrilled with the "Applications" and "Places" buttons as they are taking up too much space. Is there a way to replace that Applications Menu with just an Applications button? Is there a way to just have folders on my desktop in classic and do away with the "Places" button?
  Lastly, what do I lose choosing Classic w/o effects? Will it be much lighter/faster?
Thanks.
KBD47

Regarding this:

> I'm not thrilled with the "Applications" and "Places" buttons as they are taking up too much space. Is there a way to replace that Applications Menu with just an Applications button?

Yes, look at the first screenshot here:

[http://ubuntuforums.org/showpost.php?p=11465187&postcount=179](http://ubuntuforums.org/showpost.php?p=11465187&postcount=179)

If you Alt + Right-click on the panel it's called Main Menu. The one that displays Apps and Places is called Menu Bar.

Regarding this:

> Is there a way to just have folders on my desktop in classic and do away with the "Places" button?

I'm not totally sure if I understand you so I'm kind of guessing here. If you install Ubuntu Tweak:

[https://launchpad.net/~tualatrix/+archive/next](https://launchpad.net/~tualatrix/+archive/next)

By running these three commands:

```
sudo add-apt-repository ppa:tualatrix/next
```

```
sudo apt-get update
```

```
sudo apt-get install ubuntu-tweak
```

Then you'll find it in the app menu under Other > Ubuntu Tweak. **It "launches" very slowly the first time you use it because it has to "read" the existing configuration files**, but once it opens just click on the Tweaks tab and Desktop Icon Settings:

[ATTACH]207635[/ATTACH]

From there you can select what to show on the desktop:

[ATTACH]207636[/ATTACH]

I need a potty break but I'll be back regarding the rest :)

But before I go to go, please stay away from the Janitor! IMHO it's among the worst ideas I've ever seen in FOSS!

---

### Post by kansasnoob on 2011-11-20
Continuing with the last issue:

> do away with the "Places" button?

In the panel yes. But not in the main menu. I think that would be unwise anyway.

Regarding this:

> Lastly, what do I lose choosing Classic w/o effects? Will it be much lighter/faster?

AFAIK both Unity-2D and "classic w/o effects" run on Metacity, whereas Unity runs on Compiz and pure classic "should" also run on Compiz but so far does NOT w/o tweaking.

You'll notice that all of my potential "how-to" posts include statements such as:

> This is for "classic without effects" only! I've never cared for compiz anyway and it seems to be difficult to get it to run in a classic Precise DE. So, if you want compiz this thread is NOT for you, sorry.


---

### Post by KBD47 on 2011-11-20
Thank you! That solved my problem. Removing the other menu got rid of applications and places, installing the alternate menu gave me a smaller icon and has places inside the menu.
Thanks again.
KBD47

---

### Post by kansasnoob on 2011-11-20
> **KBD47 said:**
> Thank you! That solved my problem. Removing the other menu got rid of applications and places, installing the alternate menu gave me a smaller icon and has places inside the menu.
Thanks again.
KBD47

No thanks needed. I just wish I'd begun to look into this sooner :)

I truly forget that I'm running Gnome 3 until I have to use keyboard shortcuts. Still mind boggled about much of that, like consistently launching a GUI terminal :confused:

---

### Post by KBD47 on 2011-11-20
> **kansasnoob said:**
> No thanks needed. I just wish I'd begun to look into this sooner :)

I truly forget that I'm running Gnome 3 until I have to use keyboard shortcuts. Still mind boggled about much of that, like consistently launching a GUI terminal :confused:

Well I think what you are doing is very important, and everyone helping to keep the classic desktop alive are helping a lot. We've already seen much frustration at the change from classic gnome, and I think new users will feel comfortable using classic.
  BTW I'm in Classic w/o effects and I'm not noticing any difference, as in not missing anything thing. I mentioned using MATE in Mint, and I think it will get better, but right now Gnome Classic is much more polished and the font rendering is excellent compared to the weak font rendering in MATE. Also just tried Freezy and it has a lot of promise. Gnome Classic/Fallback definitely has a user base is Gnome will let it live for awhile.
Thanks again.
KBD47

---

### Post by kansasnoob on 2011-11-21
Just keeping everyone updated here about my intent to address this as somewhat of a how-to for Oneiric. I'd early on abandoned the idea of making it an actual "how-to" because I'm just not up to the task. So I'd thought of "My Oneiric Classic w/o effects and how I got there", but I'm now thinking about doing this a bit different.

My current thought is to start a thread in Main Support Cats > Desktop Environments and title the thread something like, "Oneiric classic w/o effects - close but still need help", which is true. I'd still like to learn much more about theming and other peoples tweaks. This thread is proof of what a group effort can accomplish :D

So why take this approach? Well, I think I have learned enough here - *right here in this thread* - that I truly am close, but I still don't know enough to "own" a how-to, but **I do want to share what I've learned here with a broader audience**.

Also I can't be sure how this will be received in other parts of the forums. I'm very much appreciative of cariboo907 kicking this off to help me out, but some other mods may not like the idea of pursuing 'gnome-session-fallback' :(

So, in the next day or two I'm going to jump on it and see what happens. Regardless of the outcome I'll have done my best to share my limited knowledge and then I can get on with testing both Ubuntu and Lubuntu "+1" which is what I truly like to do :D

Yes, I can be selfish and just focus on my own enjoyment, and I enjoy testing.

---

### Post by ranch hand on 2011-11-22
I think that sounds like a good plan.

I am sure that there are many people that would like this modification a whole lot.  That is what that sub forum is about so I don't see that there should be any problem with it.

There are probably folks there working on some of what you are doing even.  I doubt that they are doing the whole thing so you really would be a catalyst for folks getting together.  This would be a good thing.

---

### Post by robert shearer on 2011-11-22
Just a quick update for you Kansas,
Re slow shutdown/reboot...here
[http://ubuntuforums.org/showpost.php?p=11435644&postcount=83](http://ubuntuforums.org/showpost.php?p=11435644&postcount=83)

I have finally got Precise installed and was able to try this..
normal shutdown brought up the Ubuntu logo on the purple screen with 5 dots below it.
it took **3 passes** of all **5 dots** to shutdown or reboot.(about 15 seconds)
After modifying 
/etc/init/network-manager.conf
it took **one pass** of only **three dots** (about 3 seconds) to shutdown or reboot.
Might be more noticable on my old hardware...Celeron single-core 2.4ghz and 864 ram but as the fallback is for older hardware I hope this is useful to someone else ...:)
(note that it takes a reboot and shutdown cycle to take so it will work the **second** shutdown after application.)

** your** efforts with Fallback are very much appreciated and have helped me immensely, thanks..!

---

### Post by cariboo on 2011-11-22
> **kansasnoob said:**
> Just keeping everyone updated here about my intent to address this as somewhat of a how-to for Oneiric. I'd early on abandoned the idea of making it an actual "how-to" because I'm just not up to the task. So I'd thought of "My Oneiric Classic w/o effects and how I got there", but I'm now thinking about doing this a bit different.

My current thought is to start a thread in Main Support Cats > Desktop Environments and title the thread something like, "Oneiric classic w/o effects - close but still need help", which is true. I'd still like to learn much more about theming and other peoples tweaks. This thread is proof of what a group effort can accomplish :D

So why take this approach? Well, I think I have learned enough here - *right here in this thread* - that I truly am close, but I still don't know enough to "own" a how-to, but **I do want to share what I've learned here with a broader audience**.

Also I can't be sure how this will be received in other parts of the forums. I'm very much appreciative of cariboo907 kicking this off to help me out, but some other mods may not like the idea of pursuing 'gnome-session-fallback' :(

So, in the next day or two I'm going to jump on it and see what happens. Regardless of the outcome I'll have done my best to share my limited knowledge and then I can get on with testing both Ubuntu and Lubuntu "+1" which is what I truly like to do :D

Yes, I can be selfish and just focus on my own enjoyment, and I enjoy testing.

I'll fully support your thread in the Desktop Environment sub-forum, and when you're ready, even sticky it.

As far as the other mods go, we are mostly DE agnostic, we all use what works best for us, so there shouldn't be any problems. Some of us have already been linking to this thread when others are suggesting moving to a different distribution, as gnome classic seems to be ignored/unknown by others.

---

### Post by Elfy on 2011-11-22
> as far as the other mods go, we are mostly de agnostic,+1

---

### Post by cmcanulty on 2011-11-23
I just posted a new reply with the results of my many attempts to get a gnome classic desktop and I think I am now very close. Please look at my screenshots and tell me what you think. I still have had no luck getting a large black cursor like I had. The option is listed but doesn't work in unity or xfce4. Here is a link to the thread it is post #34
[http://ubuntuforums.org/showthread.php?p=11483985#post11483985](http://ubuntuforums.org/showthread.php?p=11483985#post11483985)

---

### Post by jerrrys on 2011-11-23
> **kansasnoob said:**
> Just keeping everyone updated here about my intent to address this as somewhat of a how-to for Oneiric. I'd early on abandoned the idea of making it an actual "how-to" because I'm just not up to the task. So I'd thought of "My Oneiric Classic w/o effects and how I got there", but I'm now thinking about doing this a bit different.

My current thought is to start a thread in Main Support Cats > Desktop Environments and title the thread something like, "Oneiric classic w/o effects - close but still need help", which is true. I'd still like to learn much more about theming and other peoples tweaks. This thread is proof of what a group effort can accomplish :D

So why take this approach? Well, I think I have learned enough here - *right here in this thread* - that I truly am close, but I still don't know enough to "own" a how-to, but **I do want to share what I've learned here with a broader audience**.

Also I can't be sure how this will be received in other parts of the forums. I'm very much appreciative of cariboo907 kicking this off to help me out, but some other mods may not like the idea of pursuing 'gnome-session-fallback' :(

So, in the next day or two I'm going to jump on it and see what happens. Regardless of the outcome I'll have done my best to share my limited knowledge and then I can get on with testing both Ubuntu and Lubuntu "+1" which is what I truly like to do :D

Yes, I can be selfish and just focus on my own enjoyment, and I enjoy testing.

I like it

---

### Post by kansasnoob on 2011-11-23
> **cmcanulty said:**
> I just posted a new reply with the results of my many attempts to get a gnome classic desktop and I think I am now very close. Please look at my screenshots and tell me what you think. I still have had no luck getting a large black cursor like I had. The option is listed but doesn't work in unity or xfce4. Here is a link to the thread it is post #34
[http://ubuntuforums.org/showthread.php?p=11483985#post11483985](http://ubuntuforums.org/showthread.php?p=11483985#post11483985)

I've never really messed with xfce4 enough to be of any help to you, sorry. I may be able to spin up an Xubuntu disc in a few days just to play and see what happens but right now I'm stuck focusing on my own thing :(

---

### Post by KBD47 on 2011-11-23
Here is my Mint 12 desktop using Gnome Classic.I deleted the bottom panel, moved the top panel to the bottom, and tweaked it a bit.
KBD47

---

### Post by tista on 2011-11-24
> **KBD47 said:**
> Here is my Mint 12 desktop using Gnome Classic.I deleted the bottom panel, moved the top panel to the bottom, and tweaked it a bit.
KBD47

@KBD47,

Wow! cool! :)

Mine's also attached here...
* Precise + gnome-fallback + mutter + gnome-panel + indicator-applets + my gtk theming...

Have a nice day!

---

### Post by KBD47 on 2011-11-24
Looking good tista!

---

### Post by VanillaMozilla on 2011-11-24
Elementary question:  What's the difference between gnome-fallback, gnome-classic, and gnome-shell?


(In case you want to know where I'm coming from, what I really want is my Gnome 2 back, preferably without having to rewrite Linux myself.  I've been tinkering with desktops on a spare computer, but have no great alternatives yet.  No Unity, thank you.)

---

### Post by cariboo on 2011-11-24
> **VanillaMozilla said:**
> Elementary question:  What's the difference between gnome-fallback, gnome-classic, and gnome-shell?


(In case you want to know where I'm coming from, what I really want is my Gnome 2 back, preferably without having to rewrite Linux myself.  I've been tinkering with desktops on a spare computer, but have no great alternatives yet.  No Unity, thank you.)

If you are going to be posting in this sub-forum **Ubuntu +1 (Precise Pangolin)**, you should at least read the thread you are posting in, your questions have already been asked and answered.

If you aren't running Precise, your question may be better asked in [Desktop Environments]("http://ubuntuforums.org/forumdisplay.php?f=329"). If you still want to use the discontinued and unmaintained older version of Gnome, Ubuntu isn't the distribution for you.

---

### Post by kansasnoob on 2011-11-24
Just wanted everyone to know I'm still working on the Oneiric thing. Naturally I test, test, and retest everything just because that's how I roll :)

Back in [post #191]("http://ubuntuforums.org/showpost.php?p=11468859&postcount=191") I'd reported that it was no longer necessary to use "sudo /usr/lib/lightdm/lightdm-set-defaults -s whatever_session"  in Precise if you auto-login, and that now appears to be true even in Oneiric.

Regardless I'm very close, but every time things change, like when bugs get fixed, I have to adapt and then retest.

In that case I needed to test all five Gnome DE boot options to be certain, and I had to start from a fresh install to be **absolutely** certain!

And I also have a bad case of the crud - must be swine flu because only a pig could look as nasty as I do right now and still be above ground :D

---

### Post by kansasnoob on 2011-11-24
> **cariboo907 said:**
> If you are going to be posting in this sub-forum **Ubuntu +1 (Precise Pangolin)**, you should at least read the thread you are posting in, your questions have already been asked and answered.

If you aren't running Precise, your question may be better asked in [Desktop Environments]("http://ubuntuforums.org/forumdisplay.php?f=329"). If you still want to use the discontinued and unmaintained older version of Gnome, Ubuntu isn't the distribution for you.

Other than a slight need for some help with themes I honestly am so close with classic (no effects) that I can't imagine going back to Gnome 2. I occasionally still boot into either Natty or Lucid to do something and I now find myself missing my newly tweaked Oneiric/Precise :D

OT, but the new Oneiric kernel may have a memory leak. That is, I notice since the kernel upgrade a few days ago that memory usage gradually climbs and climbs, but I can only deal with one thing at a time ;)

I'm about wiped out for today but I should soon have a "Oneiric classic tweaks & tips" thread up. I just want to be certain that my initial info is correct, but the devs are fixing bugs so fast it's hard for me to keep up :guitar:

---

### Post by kansasnoob on 2011-11-24
> **KBD47 said:**
> Here is my Mint 12 desktop using Gnome Classic.I deleted the bottom panel, moved the top panel to the bottom, and tweaked it a bit.
KBD47

I assume that's the Mate option :confused:

Unless you provide some details how is that anything other than an advertisement?

---

### Post by kansasnoob on 2011-11-24
I need to steal some electronic ink :)

******

Tweak #8: At this point I decided the window-management buttons really needed to be back on the right so I ran:

gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"

Note: to restore the defaults run:

gconftool-2 --set "/apps/metacity/general/button_layout" --type string "close,minimize,maximize:"

*******

Why did I need to steal that electronic ink? Well, most of the "guides" I've read either omitted how to revert to "out-of-box" or they had it wrong.

Now I have it in my symlinked doc drive, two flash drives, and a forum link. No way I'm losing that bugger :)

---

### Post by KBD47 on 2011-11-24
> **kansasnoob said:**
> I assume that's the Mate option :confused:

Unless you provide some details how is that anything other than an advertisement?

It's not MATE, it's Gnome 3 in Fallback Mode, aka Gnome Classic. It is essentially the same desktop you have in Oneiric with Gnome Classic installed.

---

### Post by kansasnoob on 2011-11-25
> **KBD47 said:**
> It's not MATE, it's Gnome 3 in Fallback Mode, aka Gnome Classic. It is essentially the same desktop you have in Oneiric with Gnome Classic installed.

Thanks :)

I was just curious. Did you use any of my tweaks to get there?

---

### Post by kansasnoob on 2011-11-25
I did the Oneiric thing:

[http://ubuntuforums.org/showthread.php?p=11488769#post11488769](http://ubuntuforums.org/showthread.php?p=11488769#post11488769)

I'm now going to test those commands on a fresh Oneiric to double check myself and then I'll remove that warning :)

---

### Post by ranch hand on 2011-11-25
Real fine work.  Good job.

---

### Post by KBD47 on 2011-11-25
> **kansasnoob said:**
> Thanks :)

I was just curious. Did you use any of my tweaks to get there?

I did it with just removing the bottom panel, dropping the top panel to the bottom, and moving and adding things to the panel. No major tweaks. I did some bigger tweaks to the MGSE desktop in Mint and updates knocked those out, so didn't want to try anything major until the final release of Mint 12. 
KBD47
edit--actually I think it was you, or someone here, who told me how to get rid of the application-places menu and add a regular menu, and how to add a home folder to the desktop, so thanks!

---

### Post by kansasnoob on 2011-11-26
Well, 120 views so far and no replies. I'll take that as good news for the time being :)

---

### Post by kansasnoob on 2011-11-26
> **ranch hand said:**
> Real fine work.  Good job.

I wish I had some clue why Ubuntu won't run for you but I'm totally clueless :confused:

---

### Post by kansasnoob on 2011-11-26
> **KBD47 said:**
> I did it with just removing the bottom panel, dropping the top panel to the bottom, and moving and adding things to the panel. No major tweaks. I did some bigger tweaks to the MGSE desktop in Mint and updates knocked those out, so didn't want to try anything major until the final release of Mint 12. 
KBD47
edit--actually I think it was you, or someone here, who told me how to get rid of the application-places menu and add a regular menu, and how to add a home folder to the desktop, so thanks!

Looks good, I've just never really cared that much for Mint, but I've learned stuff from testing Mint at various times :)

---

### Post by KBD47 on 2011-11-26
What I like about Mint is that it is pretty much the way I like it out of the box, no overlay scrollbars, no hidden menus, close/maximize/minimize buttons are on the right, codecs installed, so that it needs less tweaking both for myself and others I want to introduce Linux to.
KBD47

---

### Post by ranch hand on 2011-11-26
> **KBD47 said:**
> What I like about Mint is that it is pretty much the way I like it out of the box, no overlay scrollbars, no hidden menus, close/maximize/minimize buttons are on the right, codecs installed, so that it needs less tweaking both for myself and others I want to introduce Linux to.
KBD47
And I think you got a new one today.

---

### Post by KBD47 on 2011-11-26
Yes, Mint 12 was officially released today. I've been using the RC and stable versions since they were released. I think Clem and the other devs have tried to work miracles at making Gnome 3 Shell usable, but I still prefer Gnome Classic/Fallback.

---

### Post by kansasnoob on 2011-11-26
At some point I'm going to have to take a peak at what they did with Mate. Right now I have a lot of clean up to do before Precise alpha 1 iso-testing.

It's a bit tougher now that I test both Lubuntu and Ubuntu images, and both Desktop images and Alt images.

Add Ubuntu upgrade testing to the mix and it gets just crazy unless I have an actual plan in place :P

---

### Post by KBD47 on 2011-11-27
I think MATE has a lot of potential, but it needs some work and polish. I hope by the LTS releases next Spring it is much improved, especially if we end up losing Gnome Fallback, which I hope we don't.
BTW I'm a fan of Lubuntu, runs like lightning on my netbooks :-)
KBD47
PS--very cool thing about Fallback in Mint 12 is if you click on panel properties and choose solid color the panel becomes see-through showing the desktop background.

---

### Post by cmcanulty on 2011-11-27
I installed mint 12 yesterday and suddenly I had sound, wireless, and no poweroff issues fixed that no amount of tweaking could I fix in ubuntu 11.10. I still like mate (gnome 2 basically)best. Here is  a caveat though on all including mint screen is dim after every reboot. Also in mate last night I got a popup saying the mate panel unexpectantly closed and all my panel icons are gone even after reboot. So today I have to fix that. Also no system now will let me get a large cursor preferably black.I think gnome 3 will eventually be usable but every theme or tweak I tried involved a lot of work and still very buggy.

---

### Post by kansasnoob on 2011-11-27
> **cmcanulty said:**
> I installed mint 12 yesterday and suddenly I had sound, wireless, and no poweroff issues fixed that no amount of tweaking could I fix in ubuntu 11.10. I still like mate (gnome 2 basically)best. Here is  a caveat though on all including mint screen is dim after every reboot. Also in mate last night I got a popup saying the mate panel unexpectantly closed and all my panel icons are gone even after reboot. So today I have to fix that. Also no system now will let me get a large cursor preferably black.I think gnome 3 will eventually be usable but every theme or tweak I tried involved a lot of work and still very buggy.

The latest Mint is based on Ubuntu Oneiric, I have a Oneiric classic thread up:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

But that will NOT help you with Mint! As I said there, "I've tested this quite a bit, but only with fresh, fully updated Ubuntu Oneiric installs".

If you want to persist at trying Mate in Mint I think you should be posting at the Mint forums or here:

[http://ubuntuforums.org/showthread.php?t=1858282&highlight=Mate](http://ubuntuforums.org/showthread.php?t=1858282&highlight=Mate)

---

### Post by cariboo on 2011-11-27
All this talk about Mint is driving this thread off topic, If you want to discuss Mint, either do it iin[Other Distro/OS Talk,]("http://ubuntuforums.org/forumdisplay.php?f=401"), or better yet go to the [Mint forums]("http://forums.linuxmint.com/") to ask questions or to help out.

This is the Precise Testing and Discussion sub-forum, any discussion of other versions doesn't belong here.

---

### Post by kansasnoob on 2011-11-28
Time for a new To Do list :D

#1: Theming remains high on the list! I'd very much appreciate anyone sharing their favorite theme tweaks.

#2: I'm thinking of keeping a separate Precise install with these two PPA's installed:

[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)

I'm thinking that may provide somewhat of a sneak peak of future problems.

#3: Keep a close eye on the further deprecation of gtk2 and gconf,

I rather expect lots of stuff to blow up between now and the first Beta on March first ;)

Three whole months of super duper fun.

---

### Post by jerrrys on 2011-11-28
I have a basic GUI (starting point) in 11.10 by installing lightdm and fallback.

I hope that I can do the same in 12o4 with this ppa

[https://launchpad.net/ubuntu/precise/+package/gnome-session-fallback](https://launchpad.net/ubuntu/precise/+package/gnome-session-fallback)

---

### Post by cbowman57 on 2011-11-28
Don't even need the ppa with 12.04, you can get it right from the official repository.

Not sure about the live dailies but the alternate iso installs gnome shell & fallback along with Unity by default, at least it did a couple days ago.

---

### Post by jerrrys on 2011-11-28
Thanks cbowman57; that will make things a little easier.

---

### Post by kansasnoob on 2011-11-28
> **jerrrys said:**
> I have a basic GUI (starting point) in 11.10 by installing lightdm and fallback.

I hope that I can do the same in 12o4 with this ppa

[https://launchpad.net/ubuntu/precise/+package/gnome-session-fallback](https://launchpad.net/ubuntu/precise/+package/gnome-session-fallback)

Now I'm confused :lolflag:

---

### Post by jerrrys on 2011-11-28
Now I'm confused about your confusion :confused:

---

### Post by arpanaut on 2011-11-28
@jerrys, that is not a link to a PPA 
That package is part of the default repositories of Precise.

---

### Post by jerrrys on 2011-11-28
thus the confusion, thanks

---

### Post by jerrylamos on 2011-11-29
"Megathread" all right!!  

Anyway, used synaptic to install gnome-session-fallback O.K.  

Applications Places are there on the top panel, but where's "System"?  "power" switch was easy to install, alt-right click on the panel.

The answer for "System" could be somewhere in this -huge- thread?

Thanks,  Jerry

---

### Post by kansasnoob on 2011-11-29
> **jerrylamos said:**
> "Megathread" all right!!  

Anyway, used synaptic to install gnome-session-fallback O.K.  

Applications Places are there on the top panel, but where's "System"?  "power" switch was easy to install, alt-right click on the panel.

The answer for "System" could be somewhere in this -huge- thread?

Thanks,  Jerry

Start by reading my thread here:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

But I've not tried that with Precise in the past 5 or 6 days so something could break :)

It does however do a good job of explaining menu and panel changes, I hope. 

Tell me if you think it needs tweaking :)

---

### Post by jerrylamos on 2011-11-29
> **kansasnoob said:**
> Start by reading my thread here:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

But I've not tried that with Precise in the past 5 or 6 days so something could break :)

It does however do a good job of explaining menu and panel changes, I hope. 

Tell me if you think it needs tweaking :)
Thanks!

Most of what I was looking for is in Applications > Other.  I can deal with that, an extra click and mouse search.

I've been keeping a Lucid Lynx LTS around for doing real work with the "Unity" stuff for bug testing & passive reading.  I'll see if I can use fallback for real work.

Thanks for your useful info.

Jerry

---

### Post by cmcanulty on 2011-11-29
Please consider adding the clearlooks theme to 12.04 classic it is very easy to read all the menus. I find all the black with light text hard to see. Thank you.

---

### Post by jerrylamos on 2011-11-29
> **cmcanulty said:**
> Please consider adding the clearlooks theme to 12.04 classic it is very easy to read all the menus. I find all the black with light text hard to see. Thank you.

O.K., I'll bite, what keystrokes/mouse selections did you do to get clearlooks theme?

Thanks, Jerry

---

### Post by cmcanulty on 2011-11-29
I was making a suggestion to get it added to 12.04 classic

---

### Post by cariboo on 2011-11-29
> **cmcanulty said:**
> I was making a suggestion to get it added to 12.04 classic

You are welcome to create a howto, and add it to this thread.

---

### Post by jerrylamos on 2011-11-30
I'm getting used to gnome-session-fallback in a hurry.  Nice for someone like me who is a whole lot faster at Lucid Lynx than Natty Narwhal or Oneiric Ocelot or Precise Pangolin.

Just used synaptic to install gnome-session-fallback

drag & drop a couple applets from Applications to the top bar example firefox & terminal (for doing aptitude updates)

login choosing fallback

Oh, yes, put the min/max/close buttons on the right above the vertical scroll bar:
gconftool-2 --set /apps/metacity/general/button_layout --type string menu:minimize,maximize,close

of course on this netbook F11 for full screen

Wouldn't mind on my wide 16:9 notebook putting the top panel on the left, don't see how to do that.  

Would really like clearlooks.  When Unity went in the Appearance menu's went out. Newer ubuntu, less features. Foo.

Thanks everyone!  

Jerry

p.s. I still run unity just to see if there are any bugs on my various new to old pc's.  My view, tablets don't hold a candle in function to a good linux.  If I want to use a dumbed down tablet mostly good for reading and listening, I've got one.  If I want to do some useful work, this netbook with Lucid Lynx or "fallback" beats them silly on function for $248 same size as a 10.1" tablet.

---

### Post by kansasnoob on 2011-11-30
> **cmcanulty said:**
> Please consider adding the clearlooks theme to 12.04 classic it is very easy to read all the menus. I find all the black with light text hard to see. Thank you.

We're just end users here, we don't get to decide what themes will be ported into a release :)

I've tried playing with Clearlooks in gtk3 and it's a mess :(

I'm still expecting more deprecation of gconf during Precise dev which should prove to be both a challenge and hopefully an improvement moving forward with theming and such.

---

### Post by jerrylamos on 2011-11-30
> **kansasnoob said:**
> We're just end users here, we don't get to decide what themes will be ported into a release :)

I've tried playing with Clearlooks in gtk3 and it's a mess :(

I'm still expecting more deprecation of gconf during Precise dev which should prove to be both a challenge and hopefully an improvement moving forward with theming and such.

Kansasnoob, 

Many thanks for what you and the others are doing for us end users/testers.  Ubuntu still makes some claims about being customizable however some on the top end have some vision which removes some of the customization ability.

Jerry

---

### Post by kansasnoob on 2011-12-01
Just BTW a lot of window themes do work with the Adwaita gtk theme. A real easy one is Blubuntu:

[ATTACH]208312[/ATTACH]

It just takes a lot of experimentation and note taking. The Adwaita theme is in 'gnome-themes-standard'.

I'm still happiest ATM with the theme I posted about in that Oneiric thread.

---

### Post by jerrylamos on 2011-12-01
> **kansasnoob said:**
> Just BTW a lot of window themes do work with the Adwaita gtk theme. A real easy one is Blubuntu:

[ATTACH]208312[/ATTACH]

It just takes a lot of experimentation and note taking. The Adwaita theme is in 'gnome-themes-standard'.

I'm still happiest ATM with the theme I posted about in that Oneiric thread.

Installed gnome-themes-standard.  Now how do I access these themes and start them?

Thanks, Jerry

---

### Post by kansasnoob on 2011-12-01
> **jerrylamos said:**
> Installed gnome-themes-standard.  Now how do I access these themes and start them?

Thanks, Jerry

The easiest way to me is using either 'gnome-tweak-tool' which is in the repos or Ubuntu Tweak:

[https://launchpad.net/~tualatrix/+archive/next](https://launchpad.net/~tualatrix/+archive/next)

Note: Installing 'gnome-tweak-tool' also installs gnome-shell as a dependency!

I crunched the commands for my own favorite theme in step #11 here:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

I'm a "copy-n-paster" so once I figured out the basic commands I just look for the available themes in /usr/share/themes using ls:

```
lance@lance-AMD-desktop:~$ ls /usr/share/themes
AgingGorilla  Default              LowContrast  Shiki-Colors-Easy-Metacity
Ambiance      Emacs                Metabox      Shiki-Colors-Metacity
Atlanta       Esco                 Mist         Shiki-Colors-Striped-Metacity
Bright        HighContrast         Radiance     Simple
Clearlooks    HighContrastInverse  Raleigh      ThinIce
Crux          Industrial           Redmond      Zukitwo-Dark

``` 

But you have to poke around in the theme to see if it's compatible with gtk3 and/or metacity. It's a lot of fun playing, but you should expect some breakage :)

A lot of the themes have serious inconsistencies, I mean it might look great with some apps but absolutely horrible with others. I suspect that's due to the change from gtk2 to gtk3.

It's just going to take a while for people to create new themes, or fix old themes. I wish I knew how :D

You can always restore the out-of-box defaults by sending .gconf and .config to the trash and either rebooting or logging out and logging back in, but that tends to trash all of your previous customizations.

---

### Post by kansasnoob on 2011-12-01
One thing, I may have mentioned this before but it bears repeating, the ultimate goal is to kill .gconf altogether so a lot of what we're doing right now is going to blow up at some point!

If you look at that Oneiric thread you'll see most tweaks already occur in .config as indicated by the prefix "gsettings", where only a few occur in .gconf as indicated by "gconftool-2".

Bring on the breakage :D

Seriously I expect theme development to really take off after we reach that point though.

---

### Post by kansasnoob on 2011-12-01
I also see the WebUpd8 team has uploaded a bunch more themes to the PPA I use in that Oneiric thread:

[https://launchpad.net/~webupd8team/+archive/themes](https://launchpad.net/~webupd8team/+archive/themes)

So it's probably time to spend several hours playing again. The last time I really got into this I'd bloated /usr/share/themes to 1.2 GB :lolflag:

But I'd downloaded a heck of a lot of themes from Gnome art also. Beats the heck out of playing solitaire ;)

Note: That PPA is not yet ported to Precise so you have to change it's source designation from Precise to Oneiric ATM.

---

### Post by sgage on 2011-12-03
I am really liking Gnome Classic (No Effects), and have it set up to a nice 1-panel deal, to where it is just how I like it. Except...

I can not stand the "close window" animation of sort of collapsing boxes. It's slow and ugly. Of course, I can get rid of it by enabling "reduced resources" for Metacity. But then you get the hideous wire-frame stuff on moving and resizing windows. Just aweful. 

In the past, you could get rid of the wire-frame junk by simply enabling "assistive technologies", but I see no way to do that now. Does anyone know a way to have both NO close-window animation and NO wire-frame junk on window move/resize?

It doesn't sound like much, and it's not a show-stopper or anything, but it does rankle...

---

### Post by Peter Maunder on 2011-12-04
> Wouldn't mind on my wide 16:9 notebook putting the top panel on the left, don't see how to do that.  
You need to use the ALT key with the mouse right button to add panels to 11.10 Classic. To add a left panel, you need to add a right panel first from the bottom panel., then the left from the right, afterwards delete the unwanted right panel.
Bottom Panel -ALT Right Mouse> New Panel. Right Panel - ALT Right Mouse > New Panel. 
Right Panel - ALT Right Mouse > Delete This Panel. 
Cheers Peter

---

### Post by sgage on 2011-12-04
> **sgage said:**
> I am really liking Gnome Classic (No Effects), and have it set up to a nice 1-panel deal, to where it is just how I like it. Except...

I can not stand the "close window" animation of sort of collapsing boxes. It's slow and ugly. Of course, I can get rid of it by enabling "reduced resources" for Metacity. But then you get the hideous wire-frame stuff on moving and resizing windows. Just aweful. 

In the past, you could get rid of the wire-frame junk by simply enabling "assistive technologies", but I see no way to do that now. Does anyone know a way to have both NO close-window animation and NO wire-frame junk on window move/resize?

It doesn't sound like much, and it's not a show-stopper or anything, but it does rankle...

No ideas? 

BTW, mutter works just fine in the Gnome Classic (no effects) context. If the animations were a bit faster, it would be nice, but I can't for the life of me figure out how to configure it - googled all over the place.

Oh well, not critical.

---

### Post by sgage on 2011-12-04
Does anyone know definitively (heck, does the Gnome Project know definitively) what the future of Gnome Classic is going to be? I have heard conflicting stories about this, and I'm curious to know what the plan is...

---

### Post by tista on 2011-12-04
Hi sgage. ;)

Yeah I've also experienced such thing on metacity...
IMHO, today especially on precise, gconf settings of metacity didn't have any effectiveness anymore. as new method, we might have to shift to dconf... but now metacity unfortunately could not improve that way?

On mutter, we usually handle this dconf "org.gnome.desktop.wm".

Finally, gnome-shell would be ported to "unaccelerated desktop" maybe. ;) as far as I know it meant to be "gnome-classic", but anyway it sounds nice... then today gnome-panel seems to be frozen heavy developments in git, so I've sometimes encountered minor bugs on it, gnome3 devs're willing to purge gnome-panel project?

cheers.

---

### Post by cariboo on 2011-12-04
Fedora plans to drop gnome-classic in it's next release, as gnome-shell will now run on older systems with out acceleration. Seeing as several of the gnome devs are employed by RedHat, I can see gnome-classic support being dropped all together.

My personal feeling is that we'll see gnome-classic available until the end of Precises support.

---

### Post by tista on 2011-12-04
> **cariboo907 said:**
> Fedora plans to drop gnome-classic in it's next release, as gnome-shell will now run on older systems with out acceleration. Seeing as several of the gnome devs are employed by RedHat, I can see gnome-classic support being dropped all together.

My personal feeling is that we'll see gnome-classic available until the end of Precises support.

@cariboo907,

Same wish +1! ;)

Because of some GPU accel drivers mainly, we totally have to hunt some "classic" desktop experiences... So I also want Ubuntu devs to keep it available to the end of precise, please!!

And hopefully we would be happy if Ubuntu devs could polish the "Meta-classic" package up, I really happy whenever I want to build a minimum precise desktop environments. Although I know alternative iso could handle such minimum and "configurable" installation. :)

cheers.

---

### Post by kansasnoob on 2011-12-04
> **cariboo907 said:**
> Fedora plans to drop gnome-classic in it's next release, as gnome-shell will now run on older systems with out acceleration. Seeing as several of the gnome devs are employed by RedHat, I can see gnome-classic support being dropped all together.

My personal feeling is that we'll see gnome-classic available until the end of Precises support.

I already have a "back-up" plan in mind if the Ubuntu version of Gnome no longer supports "fallback". Basically just by installing the Debian version of 'gnome' from the repos which is typically about 2 versions behind Ubuntu's version.

But it's definitely sloppier and more difficult to tweak things so hopefully gnome version 3.4 will still have the fallback session. Once we get past Precise I don't care a whole lot :)

---

### Post by sgage on 2011-12-05
> **cariboo907 said:**
> Fedora plans to drop gnome-classic in it's next release, as gnome-shell will now run on older systems with out acceleration. Seeing as several of the gnome devs are employed by RedHat, I can see gnome-classic support being dropped all together.

My personal feeling is that we'll see gnome-classic available until the end of Precises support.

That's the impression I'm getting, too.

---

### Post by sgage on 2011-12-05
> **tista said:**
> @cariboo907,

Same wish +1! ;)

Because of some GPU accel drivers mainly, we totally have to hunt some "classic" desktop experiences... So I also want Ubuntu devs to keep it available to the end of precise, please!!

And hopefully we would be happy if Ubuntu devs could polish the "Meta-classic" package up, I really happy whenever I want to build a minimum precise desktop environments. Although I know alternative iso could handle such minimum and "configurable" installation. :)

cheers.

Lucazade's "Freezy" project is interesting along these lines...

---

### Post by sgage on 2011-12-05
> **kansasnoob said:**
> I already have a "back-up" plan in mind if the Ubuntu version of Gnome no longer supports "fallback". Basically just by installing the Debian version of 'gnome' from the repos which is typically about 2 versions behind Ubuntu's version.

But it's definitely sloppier and more difficult to tweak things so hopefully gnome version 3.4 will still have the fallback session. Once we get past Precise I don't care a whole lot :)

Some of the extensions coming out now for Gnome Shell are really quite nice, and you can get much of the old school panel effect. But I still prefer Classic. I hope it doesn't "cost" too much in time and attention to keep it supported and fine-tuned a while longer.

Time will tell...

---

### Post by ranch hand on 2011-12-06
> **kansasnoob said:**
> I already have a "back-up" plan in mind if the Ubuntu version of Gnome no longer supports "fallback". Basically just by installing the Debian version of 'gnome' from the repos which is typically about 2 versions behind Ubuntu's version.

But it's definitely sloppier and more difficult to tweak things so hopefully gnome version 3.4 will still have the fallback session. Once we get past Precise I don't care a whole lot :)
That will work for Gnome2 for a while.  As long as Squeeze is supported.  Wheezy is changing to Gnome3 and GS.

Gnome fall back may make it to release of Wheezy.  Not real sure.  It is there now but I don't know for how long.

---

### Post by kansasnoob on 2011-12-07
> **ranch hand said:**
> That will work for Gnome2 for a while.  As long as Squeeze is supported.  Wheezy is changing to Gnome3 and GS.

Gnome fall back may make it to release of Wheezy.  Not real sure.  It is there now but I don't know for how long.

Actually even the version of 'gnome' in Oneiric is "1:3.0+1ubuntu1" which is Gnome 3.0, whereas Oneiric itself is using Gnome 3.2.1.

With Gnome 3.4 not coming out until the end of March I'm not sure what to expect from Ubuntu. I recall reading at one point that only bits and pieces of 3.4 would be ported into Precise.

And I don't know what the status of the fallback session will be in 3.4. No need to worry though, there are too many other options to waste time fretting over it :D

---

### Post by ranch hand on 2011-12-07
> **kansasnoob said:**
> Actually even the version of 'gnome' in Oneiric is "1:3.0+1ubuntu1" which is Gnome 3.0, whereas Oneiric itself is using Gnome 3.2.1.

With Gnome 3.4 not coming out until the end of March I'm not sure what to expect from Ubuntu. I recall reading at one point that only bits and pieces of 3.4 would be ported into Precise.

And I don't know what the status of the fallback session will be in 3.4. No need to worry though, there are too many other options to waste time fretting over it :D
Sid is using Gnome Shell 3.2.1 so it makes sense that 12.04 is using that as it will be in testing pretty soon, what is there now is actually buggy 3.0.2.  3.2.1 works pretty well.

---

### Post by kansasnoob on 2011-12-11
Thanks to webupd8 I ran across some potentially helpful "classic_with_compiz" info:

[http://mandriver.users.sourceforge.net/classic-gnome-guide.html](http://mandriver.users.sourceforge.net/classic-gnome-guide.html)

Since I prefer metacity I'd appreciate others that prefer compiz to give things a whirl if they're do inclined :D

---

### Post by ventrical on 2011-12-11
> **sgage said:**
> Some of the extensions coming out now for Gnome Shell are really quite nice, and you can get much of the old school panel effect. But I still prefer Classic. I hope it doesn't "cost" too much in time and attention to keep it supported and fine-tuned a while longer.

Time will tell...

This is the problem. I built a dedicated machine (as I said I would ) to test and experiment GNOME Classic and GNOME (no effects) with Precise Pangolin. It is a PIII 600MHz with 655MB SDRAM (not a fast machine but works pretty good)  .. so the point is that GNOME as it stands now is very flat as compared to how GNOME worked under the 10.04 version and 10.10  kernels. However I can get Unity 2D  to run really well. (I'm surprised with such a slow processor) so it is hard to keep interested  especially how flat GNOME classic looks so far... and I would presume that in the not too distant future that an end_user would go to update their system and - BOOM!  all the hard work it took to tweak Gnome Classic desktop would be gone in a flicker. It happened (and is happening ) with XUBUNTU 10.04 so how can we be really sure that some dev will not pull the plug  on a GNOME Classic/Fallback tweak tool within Precise Pangolin??

---

### Post by sgage on 2011-12-11
> **ventrical said:**
> This is the problem. I built a dedicated machine (as I said I would ) to test and experiment GNOME Classic and GNOME (no effects) with Precise Pangolin. It is a PIII 600MHz with 655MB SDRAM (not a fast machine but works pretty good)  .. so the point is that GNOME as it stands now is very flat as compared to how GNOME worked under the 10.04 version and 10.10  kernels. However I can get Unity 2D  to run really well. (I'm surprised with such a slow processor) so it is hard to keep interested  especially how flat GNOME classic looks so far... and I would presume that in the not too distant future that an end_user would go to update their system and - BOOM!  all the hard work it took to tweak Gnome Classic desktop would be gone in a flicker. It happened (and is happening ) with XUBUNTU 10.04 so how can we be really sure that some dev will not pull the plug  on a GNOME Classic/Fallback tweak tool within Precise Pangolin??

Not sure what you mean by "flat" looking, but then, I'm not an eye-candy kind of guy. Anyway, it didn't take much work at all to make Gnome Classic (no effects) just fine for me. If they pull the plug on it (hopefully not until after PP is released), I'll figure something out. Probably end up with some Gnome Shell w/extensions kind of thing. I think the extensions and tweakability of Gnome Shell are going to improve greatly as we roll along, and a pretty simple and elegant Gnome 3 solution will be doable.

Or maybe that's just wishful thinking :KS

---

### Post by kansasnoob on 2011-12-11
> **ventrical said:**
> This is the problem. I built a dedicated machine (as I said I would ) to test and experiment GNOME Classic and GNOME (no effects) with Precise Pangolin. It is a PIII 600MHz with 655MB SDRAM (not a fast machine but works pretty good)  .. so the point is that GNOME as it stands now is very flat as compared to how GNOME worked under the 10.04 version and 10.10  kernels. However I can get Unity 2D  to run really well. (I'm surprised with such a slow processor) so it is hard to keep interested  especially how flat GNOME classic looks so far... and I would presume that in the not too distant future that an end_user would go to update their system and - BOOM!  all the hard work it took to tweak Gnome Classic desktop would be gone in a flicker. It happened (and is happening ) with XUBUNTU 10.04 so how can we be really sure that some dev will not pull the plug  on a GNOME Classic/Fallback tweak tool within Precise Pangolin??

You can never be sure that things won't blow up from day to day during a dev cycle. To me that's the whole reason to be involved in early testing :)

I have no doubt that things will change, hopefully the need for so many PPA's will improve, but with Gnome 3.4 coming just weeks before Precise I think there is good reason to believe that getting a basically "classic" look and feel will be possible.

If not I'll move on to plan C. This is plan B already for me, plan A was Lubuntu, but I really like the idea of a 5 year LTS so I decided this was worthwhile to pursue :D

---

### Post by kansasnoob on 2011-12-12
I recently ran across two new guides:

[http://mandriver.users.sourceforge.net/classic-gnome-guide.html](http://mandriver.users.sourceforge.net/classic-gnome-guide.html)

[http://www.flynsarmy.com/2011/11/how-to-make-ubuntu-11-10-more-usable/](http://www.flynsarmy.com/2011/11/how-to-make-ubuntu-11-10-more-usable/)

They both discuss a few things about Compiz so I thought I'd share them here :)

If anyone else happens to look at the latter of the two I'm curious about the two sections discussing "Classic Run menu" and "Enable Ctrl+Alt+Backspace". I didn't seem to find either option in Precise so I looked in a stable, fully updated Oneiric and still get lost :(

Regarding the Classic Run Menu it says:

> In Applications -> System Tools -> System Settings -> Shortcuts -> System set Show the Run Command Prompt to Alt+F2

But I assume that should be "Applications -> System Tools -> System Settings -> **Keyboards** -> Shortcuts -> System":

[ATTACH]208963[/ATTACH]

But I'll be darned if I can figure out how to change that from disabled to Alt+F2 :confused:

I know what it says at the bottom of the window but I guess I'm being dense.

Regarding Enable Ctrl+Alt+Backspace I'm just not finding it. I know it says:

> In Applications -> System Tools -> System Settings -> Typing -> Layout Options -> Layouts -> Options -> Key sequence to kill the X server check Control + Alt + Backspace

But I'm just not finding it. Any thoughts?

I can be quite dense at times :)

I hope someone else that loves Compiz will try some of the Compiz goodies.

---

### Post by sgage on 2011-12-12
> **kansasnoob said:**
> I recently ran across two new guides:

[http://mandriver.users.sourceforge.net/classic-gnome-guide.html](http://mandriver.users.sourceforge.net/classic-gnome-guide.html)

[http://www.flynsarmy.com/2011/11/how-to-make-ubuntu-11-10-more-usable/](http://www.flynsarmy.com/2011/11/how-to-make-ubuntu-11-10-more-usable/)

They both discuss a few things about Compiz so I thought I'd share them here :)

If anyone else happens to look at the latter of the two I'm curious about the two sections discussing "Classic Run menu" and "Enable Ctrl+Alt+Backspace". I didn't seem to find either option in Precise so I looked in a stable, fully updated Oneiric and still get lost :(

Regarding the Classic Run Menu it says:



But I assume that should be "Applications -> System Tools -> System Settings -> **Keyboards** -> Shortcuts -> System":

[ATTACH]208963[/ATTACH]

But I'll be darned if I can figure out how to change that from disabled to Alt+F2 :confused:

Yes. So when you get to System, click on 'show the run command prompt', then click on where it says 'disabled' - it will say 'new shortcut...' and just press Alt-F2 (or whatever you like) - voila!

---

### Post by kansasnoob on 2011-12-12
> **sgage said:**
> Yes. So when you get to System, click on 'show the run command prompt', then click on where it says 'disabled' - it will say 'new shortcut...' and just press Alt-F2 (or whatever you like) - voila!

Thanks, I figured I was just being dense :lolflag:

That's a cool option to have as I still find Ctrl + Alt + T to be fiddly and somewhat unreliable :)

---

### Post by cbowman57 on 2011-12-24
> **kansasnoob said:**
> I also tried browsing through dconf-editor but I'm not smart enough to know what I'm doing :redface:

  Ran across this, nice tool, not sure if there is a .deb for it.
[https://github.com/aericson/dconf-search](https://github.com/aericson/dconf-search)

---

### Post by ranch hand on 2011-12-25
Have you tried debconf?  I assume it is in the repo.  May not be what you are looking for but it is handy at times.

---

### Post by cariboo on 2011-12-25
Congrats to kansasnoob, for becoming a published author, with his article in the latest [Full Circle Magazine.]("http://fullcirclemagazine.org/issue-56/")

---

### Post by ranch hand on 2011-12-25
> **cariboo907 said:**
> Congrats to kansasnoob, for becoming a published author, with his article in the latest [Full Circle Magazine.]("http://fullcirclemagazine.org/issue-56/")
+436

Don't get too big headed now that you have hit the BIG TIME.

---

### Post by josephellengar on 2011-12-26
Hi. I have four questions regarding fallback mode, if it's okay for me to post them in this thread.

1) Why do I have no volume applet? I can't add one to the panel (not in the list) and there is none in my system tray.

2) Is there no way to make the screen autodim when I unplug my laptop? In the power options you can only do it manually.

3) Is there a way to put a time remaining, or a percent remaining, next to the battery icon in the system tray?

4) I changed my mouse with the gnome-tweak-tool, but I only get the "special arrows," such as the hand, rather than the normal one changed. Do you know why this might be? I have rebooted since I changed the mouse.

Thanks!

---

### Post by josephellengar on 2011-12-27
> **josephellengar said:**
> Hi. I have four questions regarding fallback mode, if it's okay for me to post them in this thread.
4) I changed my mouse with the gnome-tweak-tool, but I only get the "special arrows," such as the hand, rather than the normal one changed. Do you know why this might be? I have rebooted since I changed the mouse.

Thanks!

Fixed this one. I had to modify the keys in both the dconf-editor and the gconf-editor (why the hell are there two of them now?) and then I had to go into /usr/share/icons/default/index.theme and change that key to the cursor theme that I wanted.

---

### Post by kansasnoob on 2011-12-27
I have no idea about #2 and #3, but regarding #1 volume is displayed in either 'indicator-applet' or 'indicator-applet-complete' but they're not included in this version of gnome 3 so you need to use the PPA shown in step #2 here:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

You may find that even helps with steps #2 and #3. Let us know.

---

### Post by kansasnoob on 2011-12-27
> **josephellengar said:**
> Fixed this one. I had to modify the keys in both the dconf-editor and the gconf-editor (why the hell are there two of them now?) and then I had to go into /usr/share/icons/default/index.theme and change that key to the cursor theme that I wanted.

Regarding this, .gconf is gradually being killed :eek:

Remember that Oneiric was Ubuntu's first official iteration of gnome 3, specifically using gnome 3.2 (at least mostly).

If you look at my Oneiric guide you'll see that most settings are now changed using the prefix "gsettings", that's .dconf. But some still use "gconftool-2" which is .gconf :(

It all has to do with the change from gnome 2 to gnome 3, and gtk2 to gtk3, but .gconf is being killed. I just don't know how soon it'll be buried.

I think projects like Mate are likely to make the burial messy :lolflag:

---

### Post by kansasnoob on 2011-12-27
> **cbowman57 said:**
> Ran across this, nice tool, not sure if there is a .deb for it.
[https://github.com/aericson/dconf-search](https://github.com/aericson/dconf-search)

I think I have dconf/gsettings pretty well figured out :)

Sometimes it gets sloppy but I've figured out how to backup configuration files well enough that I'm no longer scared of major breakage.

For the most part it comes down to being fearless, taking notes, and being prepared to reinstall if things really blow up :)

---

### Post by kansasnoob on 2011-12-27
> **cariboo907 said:**
> Congrats to kansasnoob, for becoming a published author, with his article in the latest [Full Circle Magazine.]("http://fullcirclemagazine.org/issue-56/")

Yeah, I was shocked when they contacted me for permission to use that :)

I struggled a lot with just how to do that so I kept repeating fresh installs and asking myself, "what is bugging me the most right now"?

Then I just whacked away at it until it made some sense to me, but I'm still unsure about the final outcome :(

I rather think it would make more sense to install all desired PPA's first, then update and remove/install any needed packages, and then whack away at settings :)

---

### Post by cmcanulty on 2011-12-27
I was also wondering why dconf and gconf and they have different layouts and options I still can't get a large black cursor. I found the setting in gconf but where is it in dconf. I keep wondering are we all wasting our time trying to keep classic or are we going to be out of luck soon and have to go to xfce or another distro. I do like Ubuntu just hate the Unity and gnome 3 mess.Congrats on the full circle article it makes everything very easy to do.Now I can get a large cursor in nautilus and the desktop but it is still small in firefox. A lot of things that were no brainers in ubuntu take forever to find and tweak now.

---

### Post by kansasnoob on 2011-12-27
> **cmcanulty said:**
> I was also wondering why dconf and gconf and they have different layouts and options I still can't get a large black cursor. I found the setting in gconf but where is it in dconf. I keep wondering are we all wasting our time trying to keep classic or are we going to be out of luck soon and have to go to xfce or another distro. I do like Ubuntu just hate the Unity and gnome 3 mess.Congrats on the full circle article it makes everything very easy to do.

Could you post a screenshot of the cursor you want? I mean actually "in use" - a full-screen view so I know what I want to achieve. It's always hard to try and achieve something when you don't quite know what you're trying to achieve :)

I doubt we're wasting our time because gnome 3.4 won't be released until late March. So it's very likely that we'll still be able to achieve this in Precise before Lucid reaches end-of-life in April 2013 :)

I don't spend much time worrying, time wasted on worrying is a true waste of time whereas time spent on figuring something out almost always increases one's knowledge which can be used elsewhere.

---

### Post by cmcanulty on 2011-12-27
Here is a screenshot I have it set to 48 in gconf and that seems to work today but in a browser it is still tiny, always worked fine until 11.10 there is a mouse selector in advanced settings but it does nothing

---

### Post by josephellengar on 2011-12-27
> **kansasnoob said:**
> I have no idea about #2 and #3, but regarding #1 volume is displayed in either 'indicator-applet' or 'indicator-applet-complete' but they're not included in this version of gnome 3 so you need to use the PPA shown in step #2 here:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

You may find that even helps with steps #2 and #3. Let us know.

Thanks! I had read that article but missed the repository part of it. That fixed number 1 and 3. However, strangely enough the new indicator applet always has the "battery empty" icon on it (even when it's at 100%) and it doesn't support a bunch of icons such as checkgmail. Any idea how to solve those? Or are those programs just incompatible with the old indicator applets.

Also, has anybody figured out how to put a restart option in the shutdown menu? It's not in the included shutdown menu or the one from that repo.


EDIT: Reboot fixed the empty icon problem.

---

### Post by cmcanulty on 2011-12-27
Could someone please explain how to install the dconf search tool mentioned in post 292

---

### Post by josephellengar on 2011-12-27
> **cmcanulty said:**
> Could someone please explain how to install the dconf search tool mentioned in post 292

```

sudo apt-get install dconf-tools

```

---

### Post by cmcanulty on 2011-12-27
I have dconf-tools installed but I thought post 292 referred to a search tool for dconf. I can't find a search function in dconf-tools see link below
[https://github.com/aericson/dconf-search/tree/master/dconf_search]("https://github.com/aericson/dconf-search/tree/master/dconf_search")

---

### Post by effenberg0x0 on 2011-12-27
I don't have any dconf search tool per se. What I use is an undocumented option (dump) to dump everything to screen or file and grep what I need. Maybe it can help you. An example:

```

[09:00 PM][ahsl:AL-DESK:~/dev/ramdisk-manager/source/ahsl-patch-2011-12-27]
$ dconf dump / | grep -i "cursor"
cursor-theme='DMZ-White'

```Regards,
Effenberg

---

### Post by ventrical on 2011-12-28
> **kansasnoob said:**
> Yeah, I was shocked when they contacted me for permission to use that :)

I struggled a lot with just how to do that so I kept repeating fresh installs and asking myself, "what is bugging me the most right now"?

Then I just whacked away at it until it made some sense to me, but I'm still unsure about the final outcome :(

I rather think it would make more sense to install all desired PPA's first, then update and remove/install any needed packages, and then whack away at settings :)

Way to go kansasnoob!! :)

---

### Post by kansasnoob on 2011-12-28
Many of you may have noticed that I'm somewhat busy with Boot Info Script testing, but regardless of that you'd be doing me a huge favor if you posted Oneiric questions here:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

I ask that because I'm just now noticing some changes in Precise that I don't quite understand :(

With Precise Alpha 2 coming on February 2nd I expect many extreme changes over the next few weeks so it's going to be very important for us to know whether we're working on Oneiric or Precise :)

---

### Post by kansasnoob on 2011-12-28
> **cmcanulty said:**
> Here is a screenshot I have it set to 48 in gconf and that seems to work today but in a browser it is still tiny, always worked fine until 11.10 there is a mouse selector in advanced settings but it does nothing

That looks like DMZ-Black but I'll be darned if I can find a font change in dconf :(

I know that gnome 3 theming is still in it's infancy :D

---

### Post by kansasnoob on 2011-12-28
> **josephellengar said:**
> Thanks! I had read that article but missed the repository part of it. That fixed number 1 and 3. However, strangely enough the new indicator applet always has the "battery empty" icon on it (even when it's at 100%) and it doesn't support a bunch of icons such as checkgmail. Any idea how to solve those? Or are those programs just incompatible with the old indicator applets.

Also, has anybody figured out how to put a restart option in the shutdown menu? It's not in the included shutdown menu or the one from that repo.


EDIT: Reboot fixed the empty icon problem.

I don't even use gmail so I'm clueless :(

That said does 'checkgmail' work in Unity? Or Gnome Shell?

---

### Post by kansasnoob on 2011-12-28
> **cmcanulty said:**
> Could someone please explain how to install the dconf search tool mentioned in post 292

I didn't bother with it because it looked like a complication added to a complication added to another complication :lolflag:

---

### Post by josephellengar on 2011-12-28
> **kansasnoob said:**
> I don't even use gmail so I'm clueless :(

That said does 'checkgmail' work in Unity? Or Gnome Shell?

Yes. It works in both.

---

### Post by kansasnoob on 2011-12-30
Thought I'd bump this to see if anyone else can help with 'checkgmail' ;)

---

### Post by cmcanulty on 2011-12-30
Thanks I get black but the size is what I need. I poked around in dconf but can't find anything. I also tried size but nothing related to mouse or cursor

---

### Post by kansasnoob on 2011-12-30
> **cmcanulty said:**
> Thanks I get black but the size is what I need. I poked around in dconf but can't find anything. I also tried size but nothing related to mouse or cursor

I haven't figured that out either. I've always just preferred DMZ-White with the default font :D

---

### Post by kansasnoob on 2012-01-02
> **kansasnoob said:**
> Thought I'd bump this to see if anyone else can help with 'checkgmail' ;)

Thought I'd bump this again :)

Sooner or later someone that uses gmail will be able to answer the "checkgmail" dilemma :)

---

### Post by mc4man on 2012-01-02
Maybe an anomaly, anyway - 

Did a fresh install with 12/31 image & while the Classic session would load there was no Applications menu dropdown & alacarte would crash.

This fixed it, not something new, I remember happening in 11.04,  so if the above occurs something to keep in mind

```
sudo ln -s /etc/xdg/menus/gnome-applications.menu  /etc/xdg/menus/applications.menu
```

Probably won't file a bug on, rather see what next fresh install in a week or so brings...

---

### Post by mc4man on 2012-01-02
> **kansasnoob said:**
> Thought I'd bump this again :)

Sooner or later someone that uses gmail will be able to answer the "checkgmail" dilemma :)
I use gmail but prefer thru TB.
Anyway to see installed checkgmail, it seems to be semi-broken & can't auth.the username/password(401 error 
The only way to get somewhat working was to create a Startup App using this as the command. I'm sure it is missing some features?, someone using cg could file a bug on if not already

```
checkgmail -no_cookies
```

---

### Post by josephellengar on 2012-01-02
> **mc4man said:**
> I use gmail but prefer thru TB.
Anyway to see installed checkgmail, it seems to be semi-broken & can't auth.the username/password(401 error 
The only way to get somewhat working was to create a Startup App using this as the command. I'm sure it is missing some features?, someone using cg could file a bug on if not already

```
checkgmail -no_cookies
```

What's TB?

And if you use that command then the software doesn't have the delete/archive/mark spam abilities.

---

### Post by mc4man on 2012-01-02
> **josephellengar said:**
> What's TB?

And if you use that command then the software doesn't have the delete/archive/mark spam abilities.

Tb is thunderbird

Managed to fix the username/password issue here & checkgmail seems to work as intended.

Got the latest svn though maybe precise's version is ok.

Then patched with this patch, basically it removes 1 line & adds 3 lines. (you could open checkgmail & manually patch if desired., otherwise a simple command - 

[https://sourceforge.net/tracker/download.php?group_id=137480&atid=738663&file_id=423104&aid=3406322](https://sourceforge.net/tracker/download.php?group_id=137480&atid=738663&file_id=423104&aid=3406322)

contents of patch - 
```
 --- checkgmail	2011-09-08 09:42:57.066218240 +0200
+++ /usr/local/bin/checkgmail	2011-09-08 17:13:06.990218240 +0200
@@ -920,7 +920,8 @@
 			print "Error: No GALX input field found\n";
 			return "Error: No GALX input field found";
 		}
-		$post_galx = URI_escape(URI_unescape($1));
+		my $galx = URI_unescape($1);
+		$post_galx = URI_escape($galx);
 		
 		# Find the data to post
 		my $post_data;
@@ -936,6 +937,7 @@
 		my $post_req = HTTP::Request->new('POST' => "https://www.google.com/accounts/ServiceLoginAuth?service=mail");
 		$post_req->content_type('application/x-www-form-urlencoded');
 		$post_req->content($post_data);
+		$post_req->header('Cookie' => "GALX=$galx");
 		my $post_response = $ua->request($post_req);
 		if ($post_response->is_error) {
 			my $code = $response->code;


```

---

### Post by josephellengar on 2012-01-02
> **mc4man said:**
> Tb is thunderbird

Managed to fix the username/password issue here & checkgmail seems to work as intended.

Got the latest svn though maybe precise's version is ok.

Then patched with this patch, basically it removes 1 line & adds 3 lines. (you could open checkgmail & manually patch if desired., otherwise a simple command - 

[https://sourceforge.net/tracker/download.php?group_id=137480&atid=738663&file_id=423104&aid=3406322](https://sourceforge.net/tracker/download.php?group_id=137480&atid=738663&file_id=423104&aid=3406322)

contents of patch - 
```
 --- checkgmail	2011-09-08 09:42:57.066218240 +0200
+++ /usr/local/bin/checkgmail	2011-09-08 17:13:06.990218240 +0200
@@ -920,7 +920,8 @@
 			print "Error: No GALX input field found\n";
 			return "Error: No GALX input field found";
 		}
-		$post_galx = URI_escape(URI_unescape($1));
+		my $galx = URI_unescape($1);
+		$post_galx = URI_escape($galx);
 		
 		# Find the data to post
 		my $post_data;
@@ -936,6 +937,7 @@
 		my $post_req = HTTP::Request->new('POST' => "https://www.google.com/accounts/ServiceLoginAuth?service=mail");
 		$post_req->content_type('application/x-www-form-urlencoded');
 		$post_req->content($post_data);
+		$post_req->header('Cookie' => "GALX=$galx");
 		my $post_response = $ua->request($post_req);
 		if ($post_response->is_error) {
 			my $code = $response->code;


```

It must be Precise, because I have applied that patch to my Checkgmail so many times, both with and without sudo, and it has never worked, no matter what I do (in 10.10 and 11.10).

---

### Post by mc4man on 2012-01-02
> **josephellengar said:**
> It must be Precise, because I have applied that patch to my Checkgmail so many times, both with and without sudo, and it has never worked, no matter what I do (in 10.10 and 11.10).

Well, as far as in Precise the patch works fine, applied to both the latest svn & precise's version installed in /usr/bin & tested both scripts. screen is from patched precise packaged version,
 If I decide to keep will use the svn script instead though I'm ok with TB handling gmail.

(For 11.10 I'd get the svn, patch & see.

---

### Post by josephellengar on 2012-01-02
Never mind, I was using the wrong command. Got it working with more detailed instructions [here.]("http://forums.linuxmint.com/viewtopic.php?f=190&t=80615&sid=e74c8c4a2c9882c0cd2141ba16a8459a&start=20")

---

### Post by josephellengar on 2012-01-02
Okay, for anyone who wanted it, here is a patched checkgmail with an additional patch that I found that makes the panel background color option actually work (that had been really annoying me). All you have to do is 
1) Change the filename from checkgmail.pdf to checkgmail
2) move it to /usr/bin and overwrite the old one (after backing it up, of course :) )

I don't know what will happen if you try to update it later.

I had to rename it to .pdf because the forum would not let me upload a file of this size with other extensions and it would not let me upload a file with no extension at all.

---

### Post by mc4man on 2012-01-02
> I don't know what will happen if you try to update it later.If will likely get overwritten in /usr/bin

Because it's just a  script you don't really need the package installed, just put the script in a bin in your path.

Though one could leave the package version installed to be informed of any updates & use the currently patched script instead by placing in a bin dir.  that trumps /usr/bin

Either ~/bin or /usr/local/bin will do that.

---

### Post by kangarooks on 2012-01-03
> **cariboo907 said:**
> Please post all your gnome classic (gnome-session-fallback) hints tips and workarounds in this thread. It is my hope that we can create a digest/wiki page near the end of the development cycle so that all the cool stuff can be put in one place.

snip

I found the way to make 11.10 **behave and look exactly** like 10.04, using gnome3 technology.

This is how: [http://ubuntuforums.org/showpost.php?p=11581262&postcount=1](http://ubuntuforums.org/showpost.php?p=11581262&postcount=1)

---

### Post by jonnyboysmithy on 2012-01-03
> **kangarooks said:**
> snip

I found the way to make 11.10 **behave and look exactly** like 10.04, using gnome3 technology.

This is how: [http://ubuntuforums.org/showpost.php?p=11581262&postcount=1](http://ubuntuforums.org/showpost.php?p=11581262&postcount=1)
What is it like performance wise?

---

### Post by BlinkinCat on 2012-01-03
> **kangarooks said:**
> snip

I found the way to make 11.10 **behave and look exactly** like 10.04, using gnome3 technology.

This is how: [http://ubuntuforums.org/showpost.php?p=11581262&postcount=1](http://ubuntuforums.org/showpost.php?p=11581262&postcount=1)

Don't know if it's just me but I found the directions on your blog very hard to read - :(

---

### Post by kansasnoob on 2012-01-03
> **jonnyboysmithy said:**
> What is it like performance wise?

That's not much different than what I do:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

I just use more humility and less bravado :D

With Metacity I've encountered no performance problems, can't really comment on Compiz because I've always preferred Metacity.

---

### Post by kansasnoob on 2012-01-03
> **BlinkinCat said:**
> Don't know if it's just me but I found the directions on your blog very hard to read - :(

Me too. But I'm obviously biased :)

---

### Post by kangarooks on 2012-01-03
> **jonnyboysmithy said:**
> What is it like performance wise?

After dressing up and massaging my gnome3-classic setup into behaving like gnome2 and getting compiz i think it uses less cpu than previous gnome2 based system. I guess gnome3 guys made their libs more efficient. Tho it only is my personal opinion, i havent mesured it in anyway. 

From my point of view it works just as fast, if not faster, than 10.04

At the end of my conversion tutorial i posted some youtube vids, where you can see compiz in action. they were recoreded on my wind u100 netbook, which is not as fast as one might hope, but its snappy nevertheless

---

### Post by kangarooks on 2012-01-03
> **kansasnoob said:**
> 
I just use more humility and less bravado :D

With Metacity I've encountered no performance problems, can't really comment on Compiz because I've always preferred Metacity.

Awww... but i like bravado...  and i like my wobbly windows :D

Awesome that you got it going as well :) Upstream should really reconsider adding yours or mine patches into mainstream to make whole experience sane for all...

---

### Post by kangarooks on 2012-01-03
> **BlinkinCat said:**
> Don't know if it's just me but I found the directions on your blog very hard to read - :(

Sorry about that, i tried to make them conciese, to simply openup terminal and put into it stuff to transform 11.10 into 10.04 look-a-like, so in one sitting you end up after 10minutes or less with fully sane ubuntu experience.

I tried to provide background info all along the way quoting sources from which i took some ideas, i hope that helps.

---

### Post by kansasnoob on 2012-01-03
> **kangarooks said:**
> Awww... but i like bravado...  and i like my wobbly windows :D

Awesome that you got it going as well :) Upstream should really reconsider adding yours or mine patches into mainstream to make whole experience sane for all...

That will not happen. Gnome will continue towards gnome shell and Ubuntu will continue towards Unity.

If we can get a great "classic" in Precise that will satisfy me :D

Beyond that we'll see many. many re-spins, such as Mint's new Cinnamon DE. All in all I think this change, both by Gnome and Canonical, is probably the greatest thing to happen in FOSS in a very long time :D

---

### Post by cmcanulty on 2012-01-03
That panel color thing has been driving me nuts. Here we are patching and tweaking just to get back to a usable stable desktop.Thanks

---

### Post by kangarooks on 2012-01-03
> **cmcanulty said:**
> That panel color thing has been driving me  nuts. Here we are patching and tweaking just to get back to a usable  stable desktop.Thanks

Yeah, the color changes after 10.04 were rather poor and cold. This is why i initially put just remake of 10.04 themes on [my blog]("http://pleasanthacking.com/2011/08/15/nice-cozy-and-happy-ambiance-radiance-themes-from-lucid-10-04/"). That restored the sane desktop experience for a while. 

Now  that the unity came in without consent of the end user in 11.10  something had to be done and I did it. I also helped others to see, that  restoration of 10.04 look and feel is possible without much of  intrusion in 11.10 desktop, and with the use of gnome3-classic and  compiz - [http://ubuntuforums.org/showthread.php?t=1903363](http://ubuntuforums.org/showthread.php?t=1903363) (thanks to many others who ported packages to gnome3 to keep gnome2 workflow alive) :)

---

### Post by cariboo on 2012-01-03
@kangarooks, you need to fix your blog posting formatting, for some of us it is unreadable. Do you test it in more than one browser? See the screenshot

---

### Post by kangarooks on 2012-01-03
@cariboo907[[COLOR=#d40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=77104") Oh.. so some other guys were complaining about this and not the wording.. lol. 

Thanks for noticing it. I patched it up in proper code thingies, hope it will look better now. Wordpress acts strange sometimes on me, it does not entirely do things as sane as possible, i.e. i just noticed it doesnt like preformated stuff inside lists...

---

### Post by DJ DG on 2012-01-04
I've tweaked and tweaked 11, but I just cant deal with the new unity.  It's starting to feel like windows/apple.  What happened to having control over your own system?  Didn't most of use start using Linux so we could have control over our systems?

---

### Post by cariboo on 2012-01-04
> **DJ DG said:**
> I've tweaked and tweaked 11, but I just cant deal with the new unity.  It's starting to feel like windows/apple.  What happened to having control over your own system?  Didn't most of use start using Linux so we could have control over our systems?

Please stay on topic, what does this have to do with Precise and gnome classic?

---

### Post by DJ DG on 2012-01-04
Sorry, personal felling crept in.

---

### Post by kansasnoob on 2012-01-05
> **DJ DG said:**
> I've tweaked and tweaked 11, but I just cant deal with the new unity.  It's starting to feel like windows/apple.  What happened to having control over your own system?  Didn't most of use start using Linux so we could have control over our systems?

The whole idea behind this thread is to instruct someone how to get back to a retro look Gnome DE. I'm there with Metacity :D

I know some people will want Compiz but that's not my "thing":)

We're not here to change Canonical's decision to change to Unity. That decision has been made!!!!!!!!!!!

Put a fork in it! It's a done deal!

Our focus is how to tweak Ubuntu so we can get as close as possible to a "classic" DE :D

---

### Post by josephellengar on 2012-01-09
Okay, a few more questions that I've been unable to decipher:

1) Not sure if this is Gnome Classic or not, but how do I prevent a nautilus window from opening after I insert external media? I want it to automount, but not to open up a nautilus window automatically. Couldn't find the dconf and gconf keys that used to be associated with this.

2) I have my gnome panel autohiding. Is there a way to turn off the animation delay for showing the panel again, like in gnome 2 I could use a apps.gnome_panel.prefences and change delay to 0?

Otherwise, this is starting to look and feel pretty gnome-2-ey :D

Thanks!

---

### Post by cariboo on 2012-01-09
> **josephellengar said:**
> Okay, a few more questions that I've been unable to decipher:

1) Not sure if this is Gnome Classic or not, but how do I prevent a nautilus window from opening after I insert external media? I want it to automount, but not to open up a nautilus window automatically. Couldn't find the dconf and gconf keys that used to be associated with this.

You can set what nautilus does with media inserted, by going to Edit-> Preferences

> 2) I have my gnome panel autohiding. Is there a way to turn off the animation delay for showing the panel again, like in gnome 2 I could use a apps.gnome_panel.prefences and change delay to 0?

Otherwise, this is starting to look and feel pretty gnome-2-ey :D

Thanks!

---

### Post by josephellengar on 2012-01-09
> **cariboo907 said:**
> You can set what nautilus does with media inserted, by going to Edit-> Preferences

That doesn't work anymore. But I got an answer from my crosspost in another forum. You have to go to system settings -> removable media and then edit the settings there.

---

### Post by kansasnoob on 2012-01-15
Rearranged menus, Admin and Prefs are back:

[ATTACH]210894[/ATTACH]

[ATTACH]210895[/ATTACH]

[ATTACH]210896[/ATTACH]

---

### Post by cmcanulty on 2012-01-15
Wow, I love it, thanks

---

### Post by kansasnoob on 2012-01-15
> **cmcanulty said:**
> Wow, I love it, thanks

Don't thank me, I didn't change it. I just noticed it had been changed :D

Things will likely change a lot in the next few weeks.

---

### Post by kansasnoob on 2012-01-15
Both Nautilus and Brasero seem to be performing poorly in "classic" ATM, but not so much in Unity. I'm not going to try even reporting a bug at this point.

I wonder what "runs" when just choosing the default "copy to CD/DVD" app rather than using brasero :confused:

Just FYI; it's not uncommon for it to take several days, possibly even weeks, for some apps to catch up in a dev cycle. If this persists for a week I'll look into filing a bug report :D

---

### Post by kansasnoob on 2012-01-18
Theming as described in step #11 of my [Oneiric classic thread]("http://ubuntuforums.org/showthread.php?t=1886799") pretty badly broken after todays updates:

[ATTACH]211065[/ATTACH]

Even the standard Ambiance theme is sort of borked ATM. It looks like Adwaita may be the way to go for now :(

---

### Post by ronacc on 2012-01-18
> **kansasnoob said:**
> Both Nautilus and Brasero seem to be performing poorly in "classic" ATM, but not so much in Unity. I'm not going to try even reporting a bug at this point.

I wonder what "runs" when just choosing the default "copy to CD/DVD" app rather than using brasero :confused:

Just FYI; it's not uncommon for it to take several days, possibly even weeks, for some apps to catch up in a dev cycle. If this persists for a week I'll look into filing a bug report :D

I don't have a solution for nautilus but K3B is worth all the kde stuff it drags in , I gave up on brassero  a long time ago . I dutifully test it because thats what we do here but the first coaster and I install K3B .

---

### Post by kansasnoob on 2012-01-18
> **ronacc said:**
> I don't have a solution for nautilus but K3B is worth all the kde stuff it drags in , I gave up on brassero  a long time ago . I dutifully test it because thats what we do here but the first coaster and I install K3B .

I've used Xfburn oof and on for quite some time because Brasero has been flaky. Particularly after burning one image it seems one must restart X to get Brasero to burn an additional image :(

---

### Post by ubername on 2012-01-20
[http://ubuntuforums.org/showpost.php?p=11459388&postcount=160](http://ubuntuforums.org/showpost.php?p=11459388&postcount=160)

Hi Kansasnoob

RE you cut'n'paste guide - I don't know if anyone else mentioned this but I always use the mouse wheel (press) to paste.

So you can simply double click the command, move cursor to terminal and push the mouse wheel.

---

### Post by kangarooks on 2012-01-20
> **kansasnoob said:**
> Theming as described in step #11 of my [Oneiric classic thread]("http://ubuntuforums.org/showthread.php?t=1886799") pretty badly broken after todays updates:

[ATTACH]211065[/ATTACH]

Even the standard Ambiance theme is sort of borked ATM. It looks like Adwaita may be the way to go for now :(

have you tried my approach?

i made 11.10 exactly look and feel like 10.04, using gnome3 :) ( i also made gtk3 version of radiance10.04 color theme to match the default gtk2 version that was shipped with 10.04 )

so the problem of getting back to the gnome2 workflow is [SOLVED] \\:D/

check it out:
[http://ubuntuforums.org/showthread.php?t=1903363](http://ubuntuforums.org/showthread.php?t=1903363)
(you will find at the end some info on how i made that theme, which you might like when creating ambiance version of 10.04. i only use radiance, so i wasnt bothered with ambiance)

---

### Post by josephellengar on 2012-01-24
Anybody know how to make it so that icons on the desktop default to the smallest size possible? I can't find it. In gnome 2 you could change the default icon size in gconf but it's not in gconf or dconf now.

---

### Post by kansasnoob on 2012-01-25
> **josephellengar said:**
> Anybody know how to make it so that icons on the desktop default to the smallest size possible? I can't find it. In gnome 2 you could change the default icon size in gconf but it's not in gconf or dconf now.

That's not something I've even looked into :(

---

### Post by cmcanulty on 2012-01-25
Go to nautilus-edit-preferences-views-icon view defaults and set it to 33% or whatever you like.

---

### Post by josephellengar on 2012-01-25
> **cmcanulty said:**
> Go to nautilus-edit-preferences-views-icon view defaults and set it to 33% or whatever you like.
 
That doesn't change the desktop icons. I only see a change in the icons in the actual nautilus browser.

---

### Post by cmcanulty on 2012-01-25
It does on mine you might have to logout and in or do it under gksudo nautilus, not sure

---

### Post by kansasnoob on 2012-01-27
Currently the PPA versions of "indicator-applet" are borked in precise, but the "notification-area" works with some (but not all) items.

---

### Post by kansasnoob on 2012-01-29
Just discovered that 'hplip-gui' is pretty broken in both Oneiric and Precise "classic".

Not a huge thing but something I will follow up on as Beta 1 approaches :D

---

### Post by kansasnoob on 2012-02-05
Finally got around to testing a fresh Precise Alpha 2 with all updates applied and almost everything in [my Oneiric thread]("http://ubuntuforums.org/showthread.php?t=1886799") works :)

The theming is quite a mess but Radiance is usable, and both the ppa's in steps #7 and #8 are still on Oneiric so you must manually change the source.

[ATTACH]212073[/ATTACH]

---

### Post by kansasnoob on 2012-02-08
> **kansasnoob said:**
> Finally got around to testing a fresh Precise Alpha 2 with all updates applied and almost everything in [my Oneiric thread]("http://ubuntuforums.org/showthread.php?t=1886799") works :)

The theming is quite a mess but Radiance is usable, and both the ppa's in steps #7 and #8 are still on Oneiric so you must manually change the source.

[ATTACH]212073[/ATTACH]

Between todays 'gnome-panel' and 'light-themes' updates Ambiance appears to be working OK again. I haven't try any additional themes yet, I'll probably wait until Beta 1 before messing with themes :D

---

### Post by prusswan on 2012-02-09
> **robert shearer said:**
> Just the basics...
**alt+right-click** to on a panel to get the options menu.

For launchers in panels... navigate the Applications or Places menus to the item you want in the panel and drag and drop to the panel.
(some of the Places open in the background..eg Music folder launched from the panel seems to open behind other windows. Apps open in the foreground.

**Some** indicators work in the panels. **indicator-weather** works well. Install then drag from menu (Applications>Accessories) to panel as above.

with ccsm it will be alt+lmb+right-click from what I read in another thread, how unfortunate if intentional

---

### Post by philinux on 2012-02-12
Classic session hits precise.

 [http://www.webupd8.org/2012/02/more-classic-gnome-session-lands-in.html](http://www.webupd8.org/2012/02/more-classic-gnome-session-lands-in.html)

---

### Post by mc4man on 2012-02-12
> **philinux said:**
> Classic session hits precise.


Saw that the other day when checking out a small complaint concerning the window list, a decent improvement

Was looking at that when opening directories in nautilus from places the 'opening <whatever>' window list hangs around much too long

I guess it could be bothersome, don't use classic enough to really have a view.

Was able to stop that behavior by setting the StartupNotify=true line in /usr/share/applications/nautilus.desktop to false, whether a good idea not sure - in short time testing saw no ill effects

For interested  - LP bug & I added the existing gnome bug though don't think the upstream bug will go anywhere too soon
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/930768](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/930768)

---

### Post by kansasnoob on 2012-02-15
> **philinux said:**
> Classic session hits precise.

 [http://www.webupd8.org/2012/02/more-classic-gnome-session-lands-in.html](http://www.webupd8.org/2012/02/more-classic-gnome-session-lands-in.html)

Yes, one less PPA to add :D

I'll try to get somewhat of a guide posted here between Beta 1 and Beta 2.

---

### Post by kansasnoob on 2012-03-14
It's been a long time since I paid much attention to this. I also play with Lubuntu and I'm finding that the Precise version of Unity is pretty much totally user friendly.

Furthermore gnome-panel has been a bit borked recently but once Beta 2 gets here I'll be looking closer. I'm in no hurry but I wanted to basically bookmark something that looks promising:

 [http://www.webupd8.org/2012/03/unsettings-tool-to-disable-global-menu.html](http://www.webupd8.org/2012/03/unsettings-tool-to-disable-global-menu.html)

Right now I'm trying to figure out some netboot options and it's causing my brain to implode :D

---

### Post by jerrylamos on 2012-03-14
> **kansasnoob said:**
> It's been a long time since I paid much attention to this. I also play with Lubuntu and I'm finding that the Precise version of Unity is pretty much totally user friendly.

On this netbook, hiding unity launcher is working O.K. so I get all but one screen line for applications.

Unity still a bit of scramble finding applications and system functions since a sorted list is - ever - so much faster for me than looking all around a fuzzy foggy screen, finger sized meaningless hieroglyphs scattered around, and distracting semitransparent windows, trying to guess what unity name is for a system application.  Synaptic still works....  

I've seen pictures of pc, tablet, and "smart?" phone all with similar display and operating system.  If I had all 3 (I've a dumb cellphone) it might be handier? to dumb down the pc to smartphone limitations.  I can't imagine any "finger" method that can "touch" a keyboard and mouse.

Meanwhile I need to update Lubuntu on Thinkpad T40 to Beta.  Lubuntu A2 running fine, fast, easy.  Highly recommended if it will do your applications.

Jerry

---

### Post by screaminj3sus on 2012-03-14
> **jerrylamos said:**
> On this netbook, hiding unity launcher is working O.K. so I get all but one screen line for applications.

Unity still a bit of scramble finding applications and system functions since a sorted list is - ever - so much faster for me than looking all around a fuzzy foggy screen, finger sized meaningless hieroglyphs scattered around, and distracting semitransparent windows, trying to guess what unity name is for a system application.  Synaptic still works....  

I've seen pictures of pc, tablet, and "smart?" phone all with similar display and operating system.  If I had all 3 (I've a dumb cellphone) it might be handier? to dumb down the pc to smartphone limitations.  I can't imagine any "finger" method that can "touch" a keyboard and mouse.

Meanwhile I need to update Lubuntu on Thinkpad T40 to Beta.  Lubuntu A2 running fine, fast, easy.  Highly recommended if it will do your applications.

Jerry
The unity dash is really meant more to be searched, rather than trying to navigate it with the mouse... I pin all my commonly used apps to the launcher, and when i rarely need the dash I just search and hit enter.

---

### Post by waltclay on 2012-03-15
[solved] Changes I made by right-click in System Monitor>process table seemed to have stuck.

38 pages on this thread: time for forks.

tracker is gobbling up my resources. I've set low priority, but that's not good enough.

can I do anything but kill it?


Not responisble for my User CP: I'm not allowed to edit it. Gnome Classic

---

### Post by kansasnoob on 2012-04-01
I just ran through a "conversion to classic" for the first time in quite a while using my Oneiric guide:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

The only real caveats are:

* step #2 is no longer needed

* the PPA's used in step #7 and step #8 are still only available for Oneiric so you must edit software sources appropriately (or wait)

* I've not yet tried applying the theme described in step #11 because I want to take some time to try some newer themes

That's really it for now, little change really :D

---

### Post by kansasnoob on 2012-04-05
Sweet :guitar:


[ATTACH]215467[/ATTACH]

---

### Post by cariboo on 2012-04-05
Lookin' good kansasnoob. :)

---

### Post by mohegan on 2012-04-06
I have one problem with gnome-classic and COMPIZ.
In fullscreen, with flash videos, the gnome panels aren't hide. But with unity and compiz OR gnome-classic and metacity OR gnome-classic and mutter OR gnome-shell, it is OK.

I try this without success :
* put "OverrideGPUValidation=1" in /etc/adobe/mms.cfg.
* With compiz config, I select legacy_fullscreen in workarounds plugin.
* With compiz config, I select unredirect_fullscreen_windows in composite plugin.

I have an ATI card (HD 5800) with the default drivers.

Is it a bug or a configuration problem ?

---

### Post by kansasnoob on 2012-04-06
> **mohegan said:**
> I have one problem with gnome-classic and COMPIZ.
In fullscreen, with flash videos, the gnome panels aren't hide. But with unity and compiz OR gnome-classic and metacity OR gnome-classic and mutter OR gnome-shell, it is OK.

I try this without success :
* put "OverrideGPUValidation=1" in /etc/adobe/mms.cfg.
* With compiz config, I select legacy_fullscreen in workarounds plugin.
* With compiz config, I select unredirect_fullscreen_windows in composite plugin.

I have an ATI card (HD 5800) with the default drivers.

Is it a bug or a configuration problem ?

Lot's of problem with compiz + classic (which should be called "fallback" or "gnome-panel" or something):

[http://ubuntuforums.org/showthread.php?t=1939185](http://ubuntuforums.org/showthread.php?t=1939185)

[http://ubuntuforums.org/showthread.php?t=1953117](http://ubuntuforums.org/showthread.php?t=1953117)

I prefer just sticking with "no effects" which is Metacity when using classic or whatever you want to call it:

[http://ubuntuforums.org/showpost.php?p=11809483&postcount=375](http://ubuntuforums.org/showpost.php?p=11809483&postcount=375)

---

### Post by mohegan on 2012-04-07
I also try xfce with compiz and it works great.

Edit : If I disable the place plugin with compiz settings manager, it works !

---

### Post by ProntoAnthony on 2012-04-07
I have 2 problems since upgrading. The laptop's screen size is being misunderstood by gnome. Gnome seems to think the screen is twice as big as it really is, forcing me to scroll back and forth to see the left and right edges of the screen. In Unity there is no problem.

For some strange reason choosing Gnome Classic takes me to a Unity session.

I have no problem with Gnome (No effects). It takes me to a Gnome classic session.

The other problem is not specific the Gnome. I simply cannot figure out where to turn off the log-in drumbeat sound.

Suggestions are welcomed!

---

### Post by buzzmandt on 2012-04-07
> **ProntoAnthony said:**
> 

The other problem is not specific the Gnome. I simply cannot figure out where to turn off the log-in drumbeat sound.

Suggestions are welcomed!

one way is to remove it
```
sudo rm /usr/share/sounds/ubuntu/stereo/system-ready.ogg
```
but there might be a better way, that's how i did it since i don't like it anyway

---

### Post by cmcanulty on 2012-04-07
System settings-sound-sound effects-slide to 0

---

### Post by ProntoAnthony on 2012-04-07
Thanks for the suggestions for the sound issue.

---

### Post by cariboo on 2012-04-07
Another suggestion to turn off the system start and shutdown sound is System Setting->Startup Applications, and uncheck GNOME Login Sound. There is always more than one way to do something in a Linux distribution. :)

---

### Post by cmcanulty on 2012-04-08
ON my classic 11.10 startup applications is under Applications-other

---

### Post by mohegan on 2012-04-08
I have two little problem :
* With metacity, when I open programs (synaptic, terminal, ...), the focus doesn't change. So, I have to swith to the correct window. A few programs work well but not all. Any idea ?

* With compiz, the decoration isn't very good. In fact, the desktop icon and the windows selector in the bottom panel aren't look well. And, in the top panel, the text color menu (applications, shortcuts) isn't visible. I don't have this problem with metacity. (See the screenshots)

---

### Post by mohegan on 2012-04-08
In order to change the default sound and brightness notification (they don't look good by default), I have change the default icons. See the captures. Just use this commands and logout/login session :
```
cd /usr/share/icons/ubuntu-mono-dark/status/24
sudo cp audio-volume-low-panel.svg audio-volume-low.svg
sudo cp audio-volume-medium-panel.svg audio-volume-medium.svg
sudo cp audio-volume-high-panel.svg audio-volume-high.svg
sudo cp audio-volume-muted-panel.svg audio-volume-muted.svg 
sudo cp /usr/share/icons/gnome/scalable/status/display-brightness-symbolic.svg /usr/share/icons/ubuntu-mono-dark/status/
```

Edit : use "cp" command or "ln -s".

---

### Post by kansasnoob on 2012-04-11
**[COLOR="Red"]This is quite a preliminary look at classic (no effects) in Precise[/COLOR]**, you should expect changes almost daily in the first few weeks after the official release of Precise Pangolin, I will continue to add more info as it becomes available!

I also plan on adding some helpful hints, such as how to restore all defaults, how to speed up the process for repetitive conversions, etc. Just be a bit patient.

******************************************

**Important note**: This guide is almost totally reliant on copy-n-pasting commands into gnome-terminal. Why? Quite simply not ALL of this can be completed using GUI tools like Ubuntu Tweak or 'gnome-tweak-tool', and installing 'gnome-tweak-tool' results in installing a great deal of unneeded packages including 'gnome-shell', and my only concern is getting a "classic w/o effects" DE running efficiently. Should someone care to use either Ubuntu Tweak or 'gnome-tweak-tool' I have no problem with that, I just prefer the CLI.

But copying and pasting commands that are "wrapped" in code tags couldn't be simpler as I explained here:

[http://ubuntuforums.org/showpost.php?p=11459388&postcount=160](http://ubuntuforums.org/showpost.php?p=11459388&postcount=160)

Also, if I didn't include "sudo" in the command then it's not needed, and in rare instances may result in changed permissions, so please just copy-n-paste! If something appears to fail please copy the full output from the terminal and paste it into a reply here along with an explanation and I'll try my best to help you.

******************************************

For those who find it just too difficult to use the Unity desktop it's actually quite simple to get a classic look and feel in Ubuntu Precise. My focus has been on Classic (No effects) only, which uses Metacity, because I've never really cared for compiz anyway and from what I've seen it seems to be difficult to get it to run well in a classic DE. So, **[COLOR="Red"]if you want compiz this particular post is NOT for you[/COLOR]**, sorry.

Here's a screenshot of my Precise classic DE:

[ATTACH]215985[/ATTACH]

You'll notice that I prefer only one panel at the bottom. I realize some may want two panels, or one at the top only, it's purely a matter of preference. Be patient and I'll do my best to explain things. Just FYI my panel layout (beginning from the left) consists of:

Hide button/Main Menu/Terminal/Workspace Switcher/Screenshot/Firefox/Window List/________/Indicator Applet/Clock/Trash/Hide button

And the Indicator Applet displays: /Update notifier/Caffeine/Network widget/Mail widget/Volume widget

And this is as good a time as any to pause and discuss changes to the menu(s) and panel(s). You'll notice that the menu(s) have changed, but I think you'll likely find what you want if you just spend a couple of minutes familiarizing yourself with the new menu layout, be sure to check the System Tools > Administration, Prefernces, and System Settings categories. 

You also need to know that you must now hold down either Alt key while right-clicking on a panel or applet to be able to edit panel preferences or to add/edit/move/remove more applets. That was an intentional move by the Gnome devs to prevent people from unintentionally breaking things. And you also can't just add application applets by right-clicking them and selecting "add to panel" anymore. You must now open the "add-to-panel" window and select Application Launcher > Forward, then the window changes and you can click on the "bullet" to the left of each category to display and add any app in the menu to the panel:

[ATTACH]215940[/ATTACH]

But lets also look at my Panel Properties settings:

[ATTACH]215941[/ATTACH]

To be perfectly honest I now almost forget I'm even using Gnome 3 while running a classic (no effects) DE most of the time, but now it's time to move on to how I got there, one step at a time.

Step #1:

```
sudo apt-get install gnome-panel
```

Note: This does exactly the same as installing 'gnome-session-fallback' but why not keep it simple.

Step #2:

I highly recommend installing these so they'll be available for placement in the panel (only 'indicator-applet-complete' is available by default):

```
sudo apt-get install indicator-applet indicator-applet-session
```

When that is complete it's time to take your first look at the new "classic" DE by simply logging out, then clicking on the Ubuntu emblem to the right of your user name on the login screen, selecting Classic (No effects), entering your password, and logging back in.

Now, before continuing, please understand that all of these additional steps are optional. No two people want the exact same look, feel, or function out of a DE! This is just what I wanted. Pick and choose to suit your own desires.

**Note**: If you find the default terminal theme (white text on a purple background) as atrocious as I do just open the Terminal, click on Edit > Profile Preferences. Then click on the Colors tab and uncheck "Use colors from system theme", then select "Black on white" from the Built-in schemes.

Step #3:

I wanted to get the "Run Command Prompt" back by pressing Alt+F2 just as it was in Gnome 2. This can be quite useful if you should ever do something silly like remove both panels and need to launch the terminal or another application without being able to access the menu(s).

It really couldn't be much simpler, just go to System Tools > System Settings > Keyboard > Shortcuts > System and highlight the line that says "Show the run command prompt". Then just follow the instructions at the bottom of that window.

Step #4:

I found the screen lock thing very annoying, I live alone and don't like having to enter my password everytime the screen-"blanker" acivates. So you can just go to System Tools > System Settings > Brightness & Lock and select Lock = Off. (I call it a screen-"blanker" mostly as a joke because it hardly resembles a screensaver anymore).

Step #5:

In Unity the update-notifications now show up in the Launcher but without the Launcher we now get no persistent update notifications. Still no worries, I got it to show up in either 'indicator-applet' or 'indicator-applet-complete' in gnome-panel by running the command:

```
gsettings set com.ubuntu.update-notifier auto-launch false

```
You can revert that by running:

```
gsettings set com.ubuntu.update-notifier auto-launch true
```

Step #6:

At this point I decided the window-management buttons really needed to be back on the right so I ran:

```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"
```

Note: to restore the defaults run:

```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string "close,minimize,maximize:"
```

Step #7:

Even after moving the window-management buttons back to the right I wanted to improve the button appearance so I did the following:

```
sudo apt-get install shiki-colors-metacity-theme
```

```
gconftool-2 -s --type string /apps/metacity/general/theme Shiki-Colors-Metacity
```

To restore the default theme just run:

```
gconftool-2 -s --type string /apps/metacity/general/theme Ambiance
```

Step #8:

I found the overlay-scrollbars to be inconsistent and annoying in the classic DE so I removed them, but that was totally a matter of preference, and this is one of those steps that really seems to somewhat break Unity! Should you want to remove them run:

```
sudo apt-get purge liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0 overlay-scrollbar
```

Note: You'll likely have to reboot for that change to fully take effect.

Step #9:

I also dislike the missing menu and button icons so I run:

```
gsettings set org.gnome.desktop.interface menus-have-icons true
```

```
gsettings set org.gnome.desktop.interface buttons-have-icons true
```

Step #10:

This one is the hardest for me to explain. By default the Precise desktop is set to NOT display any icons, but it's possible for the desktop to display any combination of these icons/"actors":

```
Computer...........(computer-icon-visible)
Home...............(home-icon-visible)
Network............(network-icon-visible)
Trash..............(trash-icon-visible)
Mounted volumes....(volumes-visible)
```

But to do so you must first set the "stage" by running:

```
gsettings set org.gnome.desktop.background show-desktop-icons true
```

But that only sets the stage for the actors, now you must decide which actors you want on the stage. You're now the director.

After running that command either reboot or log out and log back in. When you get back to a blank DE background decide what you want displayed. (Hint, the "true" or "false" at the end of these commands is the key):

To show the Computer icon run:

```
gsettings set org.gnome.nautilus.desktop computer-icon-visible true
```

To hide the Computer icon run:

```
gsettings set org.gnome.nautilus.desktop computer-icon-visible false
```

To show the Home icon run:

```
gsettings set org.gnome.nautilus.desktop home-icon-visible true
```

To hide the Home icon run:

```
gsettings set org.gnome.nautilus.desktop home-icon-visible false
```

To show the Network icon run:

```
gsettings set org.gnome.nautilus.desktop network-icon-visible true
```

To hide the Network icon run:

```
gsettings set org.gnome.nautilus.desktop network-icon-visible false
```

To show the Trash icon run:

```
gsettings set org.gnome.nautilus.desktop trash-icon-visible true
```

To hide the Trash icon run:

```
gsettings set org.gnome.nautilus.desktop trash-icon-visible false

```
To show Mounted Volumes run:

```
gsettings set org.gnome.nautilus.desktop volumes-visible true
```

To hide Mounted Volumes run:

```
gsettings set org.gnome.nautilus.desktop volumes-visible false
```

Step #11:

You may or may not find that you need to disable the Firefox and/or Thunderbird global menu add-ons. To do so in Firefox just go to Tools > Add-ons > Global Menu Bar integration and select Disable. You'll then be prompted to restart Firefox. I don't use Thunderbird so I can't be sure of the specific procedure with it, but I'd think it's similar.

**Note**: The remainder of these steps require the installation of packages from PPA's!

Step #12:

Even having set Lock to Off I found it annoying to have the screen-"blanker" activate while trying to watch videos or such. In Gnome 2 I used to be able to use 'gnome-inhibit-applet' but it's not available in Gnome 3. No worries, I found a very good replacement, Caffeine:

[https://launchpad.net/~caffeine-developers/+archive/ppa](https://launchpad.net/~caffeine-developers/+archive/ppa)

In my original screenshot the caffeine applet shows up in the indicator-applet. I find it to be a sweet replacement for the old 'gnome-inhibit-applet'. Once installed and set up it allows you to "inhibit" the screen-"blanking". I think a picture is worth a thousand words so here:

[ATTACH]215945[/ATTACH]

Should you choose to install it you can setup Caffeine by going to System Tools > Preferences > Caffeine preferences. Installation is easy:

```
sudo add-apt-repository ppa:caffeine-developers/ppa
```

```
sudo apt-get update
```

```
sudo apt-get install caffeine
```


*********

I decided not to provide any info  about Hardware Sensors Indicator or System Monitor Indicator ATM because they involve using Oneiric packages, just be patient. I'll keep checking and I'll update things when possible.

***********

I need to add a bit this time about expediting the conversion process for those who need to convert numerous computers, and maybe a bit about restoring all defaults.

---

### Post by Jordy_224 on 2012-04-11
Greetings, 

   Are there any tips to install a **external ip connection widget **
   in the** genome-system-panel**

I want to detect all my** external ip** connections by checking the genome panel. 


Hopefully, I won't have to create my own script, to do this.

I should look similar to the following screenshot...

---

### Post by kansasnoob on 2012-04-11
> **Jordy_224 said:**
> Greetings, 

   Are there any tips to install a **external ip widget **
   in the** genome-system-panel**

I want to detect all my** external ip** connections by checking the genome panel. 


Hopefully, I won't have to create my own script, to do this.

I should look similar to the following screenshot...

I'm clueless :confused:

---

### Post by winh8r on 2012-04-12
I have just installed 12.04 on a new 30Gb partition on a desktop PC. 

**#1**)This is where I am at now, when I log in to a **Gnome Classic session** , I open a window, lets say it's Documents. This window opens in the extreme top left of the desktop , tight against the top panel. The window has no maximize, minimize or close buttons and cannot be moved dragged or resized.

On opening another window, it opens directly on top of the existing window and has the same issues, no buttons , cannot move/resize/grab etc.

The only way to close these windows is by right clicking on the bottom panel buttons and selecting "close"

Obviously this is less than ideal when I require to have two windows open at the same time for comparison or searching/moving files.

**#2)**To compound the issue further , when I log in to a** Gnome Classic session with No Effects**, the situation is the opposite. The first window opens in the centre of the desktop and has full functionality as regards grab/move/resize and also has all three buttons  to maximize, minimize and close.Subsequent windows open "offset" to the first window and behave as expected, with all functionality.

So the question here is: 

Is the **Gnome Classic** behaviour above at #1 "normal"?

If anything I would have expected to have been constrained when I was in a "**No Effects**" session and not the other way round.


All thoughts, comments,suggestions welcome. (And apologies in advance if I am missing something really obvious here!!)

see screenshots below if needed:

---

### Post by kansasnoob on 2012-04-12
> **winh8r said:**
> I have just installed 12.04 on a new 30Gb partition on a desktop PC. 

**#1**)This is where I am at now, when I log in to a **Gnome Classic session** , I open a window, lets say it's Documents. This window opens in the extreme top left of the desktop , tight against the top panel. The window has no maximize, minimize or close buttons and cannot be moved dragged or resized.

On opening another window, it opens directly on top of the existing window and has the same issues, no buttons , cannot move/resize/grab etc.

The only way to close these windows is by right clicking on the bottom panel buttons and selecting "close"

Obviously this is less than ideal when I require to have two windows open at the same time for comparison or searching/moving files.

**#2)**To compound the issue further , when I log in to a** Gnome Classic session with No Effects**, the situation is the opposite. The first window opens in the centre of the desktop and has full functionality as regards grab/move/resize and also has all three buttons  to maximize, minimize and close.Subsequent windows open "offset" to the first window and behave as expected, with all functionality.

So the question here is: 

Is the **Gnome Classic** behaviour above at #1 "normal"?

If anything I would have expected to have been constrained when I was in a "**No Effects**" session and not the other way round.


All thoughts, comments,suggestions welcome. (And apologies in advance if I am missing something really obvious here!!)

see screenshots below if needed:

I've found compiz to be a bit of a bloody mess which is why I've focused on (no effects) which uses Metacity, but something I'd try is opening /Home and clicking on View > Show hidden files.

There you should see a .compiz and a .compiz-1. Try renaming them something like .compiz_OLD and .compiz-1_OLD. Then either reboot or logout and back in to see what that changes.

I often do the same with .config, .gconf, .gnome2, etc to reset any previously customized settings.

---

### Post by kansasnoob on 2012-04-13
I need to personally test this to check for typos and such, but I'm already working on the Precise version of my Classic (no effects) how-to:

[http://ubuntuforums.org/showpost.php?p=11835822&postcount=389](http://ubuntuforums.org/showpost.php?p=11835822&postcount=389)

I need to test, retest, and test some more because I could have made errors and things still keep changing so please be patient.

---

### Post by winh8r on 2012-04-13
> **kansasnoob said:**
> I need to personally test this to check for typos and such, but I'm already working on the Precise version of my Classic (no effects) how-to:

[http://ubuntuforums.org/showpost.php?p=11835822&postcount=389](http://ubuntuforums.org/showpost.php?p=11835822&postcount=389)

I need to test, retest, and test some more because I could have made errors and things still keep changing so please be patient.

Thanks for your suggestions and the how-to is just great. I did try the first steps you mentioned, renaming the compiz-1 directory and so on but decided it would make more sense just to do a full re-install and stick with the Gnome Classic (no effects). I have followed your how-to , and would think that anyone having difficulty with getting it right will find it ideal.

Thank you for your efforts on this, they really make a difference.


I am another user who does not care much for fancy effects, and really just need functionality. The "No Effects" set up looks like it is going to be the way to go , for me anyway.

 The only down side to not having compiz for me at the moment is that I tend to work with 5 desktop workspaces, I use number three as my main one, and tend to "push" work from there into the adjacent desktops , either left or right depending on what further action is required on that piece of work as I process it, its a bit like sitting at your office desk and putting stuff on the left or the right hand side as you process it. 


Anyway, thanks for your help. Keep up the good work!!

---

### Post by kansasnoob on 2012-04-13
> **winh8r said:**
> Thanks for your suggestions and the how-to is just great. I did try the first steps you mentioned, renaming the compiz-1 directory and so on but decided it would make more sense just to do a full re-install and stick with the Gnome Classic (no effects). I have followed your how-to , and would think that anyone having difficulty with getting it right will find it ideal.

Thank you for your efforts on this, they really make a difference.


I am another user who does not care much for fancy effects, and really just need functionality. The "No Effects" set up looks like it is going to be the way to go , for me anyway.

 The only down side to not having compiz for me at the moment is that I tend to work with 5 desktop workspaces, I use number three as my main one, and tend to "push" work from there into the adjacent desktops , either left or right depending on what further action is required on that piece of work as I process it, its a bit like sitting at your office desk and putting stuff on the left or the right hand side as you process it. 


Anyway, thanks for your help. Keep up the good work!!

If you right click on the workspace switcher (w/o holding the alt key) it should display Preferences. Then if you click on Preferences you should be able to select the number you wish.

This said, I'm in a Unity session right now but I'll boot into a classic DE soon to double check.

---

### Post by dino99 on 2012-04-13
Gnome-classic (without effect) here on Precise i386 + nvidia-current: i still need to launch metacity to get the top bar with icons and multi workspaces. Otherwise dragging window is not possible.

---

### Post by kansasnoob on 2012-04-13
> **dino99 said:**
> Gnome-classic (without effect) here on Precise i386 + nvidia-current: i still need to launch metacity to get the top bar with icons and multi workspaces. Otherwise dragging window is not possible.

My first thought is: just after you reboot and the desktop loads press Alt+SysReq/PrtScn+k. That will log you out, then be absolutely certain that classic (no effects) is chosen.

If that fails then I'd try renaming hidden dot files as I spoke of here:

[http://ubuntuforums.org/showpost.php?p=11839601&postcount=393](http://ubuntuforums.org/showpost.php?p=11839601&postcount=393)

Typically .compiz, .compiz-1, .config, .gconf, and .gnome2. Then either reboot or restart X again to see if that improves things.

I haven't tried Precise in the last month or so on my Nvidia machine but I doubt it's gpu related.

---

### Post by kansasnoob on 2012-04-13
Still @ dino99;

Also do step #3 here:

[http://ubuntuforums.org/showpost.php?p=11835822&postcount=389](http://ubuntuforums.org/showpost.php?p=11835822&postcount=389)

It provides the old-school type of rescue options when no panel is available.

---

### Post by kansasnoob on 2012-04-14
Note to self, track this bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/981355](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/981355)

---

### Post by dino99 on 2012-04-14
> **kansasnoob said:**
> 

If that fails then I'd try renaming hidden dot files as I spoke of here:

[http://ubuntuforums.org/showpost.php?p=11839601&postcount=393](http://ubuntuforums.org/showpost.php?p=11839601&postcount=393)

Typically .compiz, .compiz-1, .config, .gconf, and .gnome2. Then either reboot or restart X again to see if that improves things.



Thanks Erick, that did it :)

---

### Post by kansasnoob on 2012-04-14
> **dino99 said:**
> Thanks Erick, that did it :)

Awesome :)

---

### Post by winh8r on 2012-04-14
thanks** kansasnoob**

I have at least got the classic gnome no effects up and running. There were some problems with keeping the desktop switcher windows in a single row , but a reboot seemed to cure the problem.

Thanks again.

---

### Post by georgelappies on 2012-04-14
> **kansasnoob said:**
> I'm just making notes to myself here to prepare for a Precise how-to like I did for [Oneiric classic w/o effects]("http://ubuntuforums.org/showthread.php?t=1886799"). **[COLOR="Red"]Please let me know if you see anything wrong here![/COLOR]**

**[COLOR="Red"]I added a lot this evening so there could be a multitude of typos and other errors - please proceed with caution![/COLOR]**

******************************************

**Important note**: This guide is almost totally reliant on copy-n-pasting commands into gnome-terminal. Why? Quite simply not ALL of this can be completed using GUI tools like Ubuntu Tweak or 'gnome-tweak-tool', and installing 'gnome-tweak-tool' results in installing a great deal of unneeded packages including 'gnome-shell', and my only concern is getting a "classic w/o effects" DE running efficiently. Should someone care to use either Ubuntu Tweak or 'gnome-tweak-tool' I have no problem with that, I just prefer the CLI.

But copying and pasting commands that are "wrapped" in code tags couldn't be simpler as I explained here:

[http://ubuntuforums.org/showpost.php?p=11459388&postcount=160](http://ubuntuforums.org/showpost.php?p=11459388&postcount=160)

Also, if I didn't include "sudo" in the command then it's not needed, and in rare instances may result in changed permissions, so please just copy-n-paste! If something appears to fail please copy the full output from the terminal and paste it into a reply here along with an explanation and I'll try my best to help you.

******************************************

For those who find it just too difficult to use the Unity desktop it's actually quite simple to get a classic look and feel in Ubuntu Precise. My focus has been on Classic (No effects) only, which uses Metacity, because I've never really cared for compiz anyway and from what I've seen it seems to be difficult to get it to run well in a classic DE. So, **[COLOR="Red"]if you want compiz this particular post is NOT for you[/COLOR]**, sorry.

Here's a screenshot of my Precise classic DE:

[ATTACH]215985[/ATTACH]

You'll notice that I prefer only one panel at the bottom. I realize some may want two panels, or one at the top only, it's purely a matter of preference. Be patient and I'll do my best to explain things. Just FYI my panel layout (beginning from the left) consists of:

Hide button/Main Menu/Terminal/Workspace Switcher/Screenshot/Firefox/Window List/________/Indicator Applet/Clock/Trash/Hide button

And the Indicator Applet displays: /Update notifier/Caffeine/Network widget/Mail widget/Volume widget

And this is as good a time as any to pause and discuss changes to the menu(s) and panel(s). You'll notice that the menu(s) have changed, but I think you'll likely find what you want if you just spend a couple of minutes familiarizing yourself with the new menu layout, be sure to check the System Tools > Administration, Prefernces, and System Settings categories. 

You also need to know that you must now hold down either Alt key while right-clicking on a panel or applet to be able to edit panel preferences or to add/edit/move/remove more applets. That was an intentional move by the Gnome devs to prevent people from unintentionally breaking things. And you also can't just add application applets by right-clicking them and selecting "add to panel" anymore. You must now open the "add-to-panel" window and select Application Launcher > Forward, then the window changes and you can click on the "bullet" to the left of each category to display and add any app in the menu to the panel:

[ATTACH]215940[/ATTACH]

But lets also look at my Panel Properties settings:

[ATTACH]215941[/ATTACH]

To be perfectly honest I now almost forget I'm even using Gnome 3 while running a classic (no effects) DE most of the time, but now it's time to move on to how I got there, one step at a time.

Step #1:

```
sudo apt-get install gnome-panel
```

Note: This does exactly the same as installing 'gnome-session-fallback' but why not keep it simple.

Step #2:

I highly recommend installing these so they'll be available for placement in the panel (only 'indicator-applet-complete' is available by default):

```
sudo apt-get install indicator-applet indicator-applet-session
```

When that is complete it's time to take your first look at the new "classic" DE by simply logging out, then clicking on the Ubuntu emblem to the right of your user name on the login screen, selecting Classic (No effects), entering your password, and logging back in.

Now, before continuing, please understand that all of these additional steps are optional. No two people want the exact same look, feel, or function out of a DE! This is just what I wanted. Pick and choose to suit your own desires.

**Note**: If you find the default terminal theme (white text on a purple background) as atrocious as I do just open the Terminal, click on Edit > Profile Preferences. Then click on the Colors tab and uncheck "Use colors from system theme", then select "Black on white" from the Built-in schemes.

Step #3:

I wanted to get the "Run Command Prompt" back by pressing Alt+F2 just as it was in Gnome 2. This can be quite useful if you should ever do something silly like remove both panels and need to launch the terminal or another application without being able to access the menu(s).

It really couldn't be much simpler, just go to System Tools > System Settings > Keyboard > Shortcuts > System and highlight the line that says "Show the run command prompt". Then just follow the instructions at the bottom of that window.

Step #4:

I found the screen lock thing very annoying, I live alone and don't like having to enter my password everytime the screen-"blanker" acivates. So you can just go to System Tools > System Settings > Brightness & Lock and select Lock = Off. (I call it a screen-"blanker" mostly as a joke because it hardly resembles a screensaver anymore).

Step #5:

In Unity the update-notifications now show up in the Launcher but without the Launcher we now get no persistent update notifications. Still no worries, I got it to show up in either 'indicator-applet' or 'indicator-applet-complete' in gnome-panel by running the command:

```
gsettings set com.ubuntu.update-notifier auto-launch false

```
You can revert that by running:

```
gsettings set com.ubuntu.update-notifier auto-launch true
```

Step #6:

At this point I decided the window-management buttons really needed to be back on the right so I ran:

```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"
```

Note: to restore the defaults run:

```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string "close,minimize,maximize:"
```

Step #7:

Even after moving the window-management buttons back to the right I wanted to improve the button appearance so I did the following:

```
sudo apt-get install shiki-colors-metacity-theme
```

```
gconftool-2 -s --type string /apps/metacity/general/theme Shiki-Colors-Metacity
```

To restore the default theme just run:

```
gconftool-2 -s --type string /apps/metacity/general/theme Ambiance
```

Step #8:

I found the overlay-scrollbars to be inconsistent and annoying in the classic DE so I removed them, but that was totally a matter of preference, and this is one of those steps that really seems to somewhat break Unity! Should you want to remove them run:

```
sudo apt-get purge liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0 overlay-scrollbar
```

Note: You'll likely have to reboot for that change to fully take effect.

Step #9:

I also dislike the missing menu and button icons so I run:

```
gsettings set org.gnome.desktop.interface menus-have-icons true
```

```
gsettings set org.gnome.desktop.interface buttons-have-icons true
```

Step #10:

This one is the hardest for me to explain. By default the Precise desktop is set to NOT display any icons, but it's possible for the desktop to display any combination of these icons/"actors":

```
Computer...........(computer-icon-visible)
Home...............(home-icon-visible)
Network............(network-icon-visible)
Trash..............(trash-icon-visible)
Mounted volumes....(volumes-visible)
```

But to do so you must first set the "stage" by running:

```
gsettings set org.gnome.desktop.background show-desktop-icons true
```

But that only sets the stage for the actors, now you must decide which actors you want on the stage. You're now the director.

After running that command either reboot or log out and log back in. When you get back to a blank DE background decide what you want displayed. (Hint, the "true" or "false" at the end of these commands is the key):

To show the Computer icon run:

```
gsettings set org.gnome.nautilus.desktop computer-icon-visible true
```

To hide the Computer icon run:

```
gsettings set org.gnome.nautilus.desktop computer-icon-visible false
```

To show the Home icon run:

```
gsettings set org.gnome.nautilus.desktop home-icon-visible true
```

To hide the Home icon run:

```
gsettings set org.gnome.nautilus.desktop home-icon-visible false
```

To show the Network icon run:

```
gsettings set org.gnome.nautilus.desktop network-icon-visible true
```

To hide the Network icon run:

```
gsettings set org.gnome.nautilus.desktop network-icon-visible false
```

To show the Trash icon run:

```
gsettings set org.gnome.nautilus.desktop trash-icon-visible true
```

To hide the Trash icon run:

```
gsettings set org.gnome.nautilus.desktop trash-icon-visible false

```
To show Mounted Volumes run:

```
gsettings set org.gnome.nautilus.desktop volumes-visible true
```

To hide Mounted Volumes run:

```
gsettings set org.gnome.nautilus.desktop volumes-visible false
```

Step #11:

You may or may not find that you need to disable the Firefox and/or Thunderbird global menu add-ons. To do so in Firefox just go to Tools > Add-ons > Global Menu Bar integration and select Disable. You'll then be prompted to restart Firefox. I don't use Thunderbird so I can't be sure of the specific procedure with it, but I'd think it's similar.

**Note**: The remainder of these steps require the installation of packages from PPA's!

Step #12:

Even having set Lock to Off I found it annoying to have the screen-"blanker" activate while trying to watch videos or such. In Gnome 2 I used to be able to use 'gnome-inhibit-applet' but it's not available in Gnome 3. No worries, I found a very good replacement, Caffeine:

[https://launchpad.net/~caffeine-developers/+archive/ppa](https://launchpad.net/~caffeine-developers/+archive/ppa)

In my original screenshot the caffeine applet shows up in the indicator-applet. I find it to be a sweet replacement for the old 'gnome-inhibit-applet'. Once installed and set up it allows you to "inhibit" the screen-"blanking". I think a picture is worth a thousand words so here:

[ATTACH]215945[/ATTACH]

Should you choose to install it you can setup Caffeine by going to System Tools > Preferences > Caffeine preferences. Installation is easy:

```
sudo add-apt-repository ppa:caffeine-developers/ppa
```

```
sudo apt-get update
```

```
sudo apt-get install caffeine
```


*********

I decided not to provide any info  about Hardware Sensors Indicator or System Monitor Indicator ATM because they involve using Oneiric packages, just be patient. I'll keep checking and I'll update things when possible.

***********

I need to add a bit this time about expediting the conversion process for those who need to convert numerous computers, and maybe a bit about restoring all defaults.

Excellent, thanks so much for this guide.

---

### Post by KBD47 on 2012-04-22
Nice guide :-) With a bit of tweaking gnome-panel makes a fine desktop.

I used this setup today on Ubuntu 12.04 and it looks and works great :-) Even though it is fairly easy to set up, it would be great if there was an actual Ubuntu spin with this desktop for newbies to download.

---

