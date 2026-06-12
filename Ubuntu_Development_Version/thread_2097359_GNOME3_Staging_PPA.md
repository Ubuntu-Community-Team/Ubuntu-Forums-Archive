---
title: "GNOME3 Staging PPA"
date: 2012-12-22
forum: Ubuntu Development Version
---

### Post by jbicha on 2012-12-22
In addition to the GNOME3 PPA and Rico's PPAs, we have a new [experimental PPA]("https://launchpad.net/~gnome3-team/+archive/gnome3-staging/") for raring which we are using to upload GNOME 3.7: ```
ppa:gnome3-team/gnome3-staging
```As Ubuntu's efforts are focused on GNOME 3.6, this PPA doesn't have the same level of quality and testing that goes into the regular GNOME3 PPA. GNOME 3.7 itself is still a work in progress.

I just uploaded gnome-control-center/gnome-settings-daemon 3.7.3 to the PPA. The most obvious regression it introduces is that external panels aren't working (they've never been officially supported by GNOME).

I've also uploaded gnome-shell 3.7.3. When I tested it I saw two major bugs: the user menu in the top right is missing, and using the keyboard to enter text in Shell dialogs (like Alt+F2, authentication prompts, unlocking the screen or the Activities Overview) doesn't work reliably. I reported both those bugs to GNOME but we've not figured out what the root cause is yet.

Unless you like broken things, you probably don't want this PPA yet. At least make sure you know how to use ppa-purge first.

On the other hand, it would help us and the GNOME developers out if you would give the PPA a try so that we can find and fix bugs before 3.8 is final. If you're interested in packaging, this is a great opportunity to get involved to help package the GNOME milestone releases.

---

### Post by mc4man on 2012-12-22
> **jbicha said:**
> 
On the other hand, it would help us and the GNOME developers out if you would give the PPA a try so that we can find and fix bugs before 3.8 is final. If you're interested in packaging, this is a great opportunity to get involved to help package the GNOME milestone releases.
Where do bug reports get filed? (or tagged?
(g-c-c was a no go

---

### Post by Stinger on 2012-12-23
@jbicha

As [I stated here]("http://ubuntuforums.org/showpost.php?p=12346815&postcount=48"), I would like to help out testing. :)

What would be the easiest way to get a RR-UGR installed ?

Install the daily build of the [Ubuntu-Server 13.04]("http://cdimage.ubuntu.com/ubuntu-server/daily/current/") and then install the [&#8220;ubuntu-gnome-meta&#8221; package]("https://launchpad.net/ubuntu/+source/ubuntu-gnome-meta") ?

Or do you recommend something else until [the bug in the build script]("http://ubuntuforums.org/showpost.php?p=12415841&postcount=5") is sorted out ?

BTW, the Gnome3 ppa doesn't seem to have any packages for Raring at all ?

---

### Post by VinDSL on 2012-12-24
> **jbicha said:**
> Unless you like broken things, you probably don't want this PPA [...]
Breakage! Yes!  That's what I'm talkin' about!!!  LoL! :D

Heh!  I'm in...

```

Commit Log for Sun Dec 23 21:17:07 2012


Upgraded the following packages:
eog (3.6.2-0ubuntu1) to 3.7.2-0ubuntu1~raring1
evince (3.6.1-1ubuntu1) to 3.7.1-0ubuntu1~raring1
evince-common (3.6.1-1ubuntu1) to 3.7.1-0ubuntu1~raring1
file-roller (3.6.3-1ubuntu2) to 3.7.1-0ubuntu1~raring1
gcr (3.6.2-0ubuntu1) to 3.7.2-0ubuntu1~raring1
gdm (3.6.1-0ubuntu1) to 3.7.2-0ubuntu1~raring1
gir1.2-evince-3.0 (3.6.1-1ubuntu1) to 3.7.1-0ubuntu1~raring1
gir1.2-gck-1 (3.6.2-0ubuntu1) to 3.7.2-0ubuntu1~raring1
gir1.2-gcr-3 (3.6.2-0ubuntu1) to 3.7.2-0ubuntu1~raring1
gir1.2-gdesktopenums-3.0 (3.7.2.2+git20121218.6bf6140a-0ubuntu1~12.10~ricotz0) to 3.7.3-0ubuntu1~raring1
gir1.2-gnomedesktop-3.0 (3.7.2-0ubuntu1~12.10~ricotz0.1) to 3.7.2-0ubuntu1~raring1
gir1.2-gtkclutter-1.0 (1.4.1+git20121211.e0bfbaf1-0ubuntu1~12.10~ricotz0) to 1.4.2-0ubuntu1
gir1.2-nautilus-3.0 (1:3.7.1+git20121102.570e9569-0ubuntu1~13.04~ricotz1) to 1:3.7.2-0ubuntu1~raring1
gjs (1.35.2+git20121210.8cf1c76f-0ubuntu1~12.10~ricotz0) to 1.35.3-0ubuntu1~raring1
glib-networking (2.34.2-0ubuntu1) to 2.35.3-0ubuntu1~raring3
glib-networking-common (2.34.2-0ubuntu1) to 2.35.3-0ubuntu1~raring3
glib-networking-services (2.34.2-0ubuntu1) to 2.35.3-0ubuntu1~raring3
gnome-contacts (3.6.2-0ubuntu1) to 3.7.3-0ubuntu1~raring2
gnome-control-center (1:3.6.3-0ubuntu9) to 1:3.7.3-0ubuntu1~raring2
gnome-control-center-data (1:3.6.3-0ubuntu9) to 1:3.7.3-0ubuntu1~raring2
gnome-desktop3-data (3.7.2-0ubuntu1~12.10~ricotz0.1) to 3.7.2-0ubuntu1~raring1
gnome-documents (3.6.2-1) to 3.7.3-0ubuntu1~raring1
gnome-font-viewer (3.6.2-0ubuntu1) to 3.7.3-0ubuntu1~raring1
gnome-icon-theme (3.6.2-0ubuntu1) to 3.7.0~git20121203.372f0e3a-0ubuntu1
gnome-icon-theme-full (3.6.2-0ubuntu1) to 3.7.0~git20121203.372f0e3a-0ubuntu1
gnome-keyring (3.6.2-0ubuntu1) to 3.7.2-0ubuntu1~raring1
gnome-mahjongg (1:3.6.1-0ubuntu2) to 1:3.7.2-0ubuntu1~raring1
gnome-session (3.6.2-0ubuntu2) to 3.7.2-0ubuntu1~raring1
gnome-session-bin (3.6.2-0ubuntu2) to 3.7.2-0ubuntu1~raring1
gnome-session-common (3.6.2-0ubuntu2) to 3.7.2-0ubuntu1~raring1
gnome-session-fallback (3.6.2-0ubuntu2) to 3.7.2-0ubuntu1~raring1
gnome-settings-daemon (3.6.3-0ubuntu4) to 3.7.3-0ubuntu1~raring1
gnome-sudoku (1:3.6.1-0ubuntu2) to 1:3.7.2-0ubuntu1~raring1
gnome-sushi (3.6.1-0ubuntu1) to 3.7.3-0ubuntu1~raring1
gsettings-desktop-schemas (3.7.2.2+git20121218.6bf6140a-0ubuntu1~12.10~ricotz0) to 3.7.3-0ubuntu1~raring1
iagno (1:3.6.1-0ubuntu2) to 1:3.7.2-0ubuntu1~raring1
libclutter-gtk-1.0-0 (1.4.1+git20121211.e0bfbaf1-0ubuntu1~12.10~ricotz0) to 1.4.2-0ubuntu1
libevdocument3-4 (3.6.1-1ubuntu1) to 3.7.1-0ubuntu1~raring1
libevview3-3 (3.6.1-1ubuntu1) to 3.7.1-0ubuntu1~raring1
libgck-1-0 (3.6.2-0ubuntu1) to 3.7.2-0ubuntu1~raring1
libgcr-3-1 (3.6.2-0ubuntu1) to 3.7.2-0ubuntu1~raring1
libgcr-3-common (3.6.2-0ubuntu1) to 3.7.2-0ubuntu1~raring1
libgjs0c (1.35.2+git20121210.8cf1c76f-0ubuntu1~12.10~ricotz0) to 1.35.3-0ubuntu1~raring1
libgnome-control-center1 (1:3.6.3-0ubuntu9) to 1:3.7.3-0ubuntu1~raring2
libgnome-desktop-3-4 (3.7.2-0ubuntu1~12.10~ricotz0.1) to 3.7.2-0ubuntu1~raring1
libgweather-3-1 (3.6.2-0ubuntu1) to 3.7.2-0ubuntu1~raring1
libgweather-common (3.6.2-0ubuntu1) to 3.7.2-0ubuntu1~raring1
libnautilus-extension1a (1:3.7.1+git20121102.570e9569-0ubuntu1~13.04~ricotz1) to 1:3.7.2-0ubuntu1~raring1
libpam-gnome-keyring (3.6.2-0ubuntu1) to 3.7.2-0ubuntu1~raring1
libwacom-common (0.6-1) to 0.7-0ubuntu1~raring1
libwacom2 (0.6-1) to 0.7-0ubuntu1~raring1
libyelp0 (3.6.2-0ubuntu1) to 3.7.3-0ubuntu1~raring1
lightsoff (1:3.6.1-0ubuntu2) to 1:3.7.2-0ubuntu1~raring1
nautilus (1:3.7.1+git20121102.570e9569-0ubuntu1~13.04~ricotz1) to 1:3.7.2-0ubuntu1~raring1
nautilus-data (1:3.7.1+git20121102.570e9569-0ubuntu1~13.04~ricotz1) to 1:3.7.2-0ubuntu1~raring1
quadrapassel (1:3.6.1-0ubuntu2) to 1:3.7.2-0ubuntu1~raring1
seahorse (3.6.3-0ubuntu1) to 3.7.2-0ubuntu1~raring1
swell-foop (1:3.6.1-0ubuntu2) to 1:3.7.2-0ubuntu1~raring1
vinagre (3.6.2-0ubuntu1) to 3.7.3-0ubuntu1~raring1
vino (3.6.2-0ubuntu1) to 3.7.3-0ubuntu1~raring1
yelp (3.6.2-0ubuntu1) to 3.7.3-0ubuntu1~raring1
yelp-xsl (3.6.1-1) to 3.7.2-0ubuntu1~raring1
zenity (3.6.0-0ubuntu1) to 3.7.2-0ubuntu1~raring1
zenity-common (3.6.0-0ubuntu1) to 3.7.2-0ubuntu1~raring1

```

BTW, it's working great, so far.

Bring it on...  :guitar:

---

### Post by VinDSL on 2012-12-24
> **jbicha said:**
> I've also uploaded gnome-shell 3.7.3. When I tested it [...] the user menu in the top right is missing [...]


This user menu :confused:


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-23-dec-2012-4(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-23-dec-2012-4.png")[/INDENT]

---

### Post by sgage on 2012-12-24
I gave it a try, and most everything seemed to work fine, except, as you noted, Gnome Shell. I ppa-purged it and will try again a little bit down the road.

---

### Post by VinDSL on 2012-12-24
> **sgage said:**
> I gave it a try, and most everything seemed to work fine, except, as you noted, Gnome Shell.[...]
Interesting!

GS is working perfectly for me, but Unity is a total mess.

The iconset, theme, fonts, et cetera (in Unity) are all back to default(s), even though various utilities are indicating that they are using my custom settings.

I reset Unity/Compiz, and it didn't do a thing, except change the icon size to the default size (48, I think).

I tried changing the wallpaper, several times, but all I'm seeing is a solid black background.

Heh!  This is great!  :D

---

### Post by VinDSL on 2012-12-24
From another thread...  ;)

> **grahammechanical said:**
> [...] I was reading a link to a blog the other day where a theme designer was complaining that every time he modified his theme to work with Gnome 3 the next development of Gnome 3 broke the theme.

I'll go change themes, in Unity, and see if that helps.

Then, again, that's probably why my user menu is working in GS...

---

### Post by VinDSL on 2012-12-24
Well, 3 hours (in Unity) later, I'm still scratching my head.

Compiz works fine.  I got bored and managed to setup a "rotating cube" without crashing the desktop, which, in itself, is rather odd.

dconf/gconf, gnome-tweak, ubuntu-tweak, et cetera reported nothing has changed in my custom settings, but Unity doesn't recognize any of them.  Nor, does changing any of these settings make any difference on the desktop.

GS is working fine, so, I'll use it tonight, and tackle Unity tomorrow, after all of the Christmas festivities.

---

### Post by mc4man on 2012-12-24
> **VinDSL said:**
> Well, 3 hours (in Unity) later, I'm still scratching my head.

Compiz works fine.  I got bored and managed to setup a "rotating cube" without crashing the desktop, which, in itself, is rather odd.

dconf/gconf, gnome-tweak, ubuntu-tweak, et cetera reported nothing has changed in my custom settings, but Unity doesn't recognize any of them.  Nor, does changing any of these settings make any difference on the desktop.

GS is working fine, so, I'll use it tonight, and tackle Unity tomorrow, after all of the Christmas festivities.
Well you'd have a new gtk (3.7.x), so that's bound to affect the light-themes/menus, ect.  & possibly some indicators.  Also the new g-c-c could be troublesome in an ubuntu session.

---

### Post by VinDSL on 2012-12-24
> **mc4man said:**
> Well you'd have a new gtk (3.7.x), so that's bound to affect the light-themes/menus, ect.  & possibly some indicators.  Also the new g-c-c could be troublesome in an ubuntu session.
Yep, there's definitely a "disconnect", for lack of a better word.  ;)

---

### Post by jbicha on 2012-12-25
Ok, gnome-shell should be working again. I had to disable a lightdm integration patch until we figure out how to get it working correctly without breaking the user menu. I haven't experienced the "unable to enter text with the keyboard" bug in gnome-shell dialogs in a couple days.

I can confirm the Unity theming bug. The PPA *does*  break some Unity design and integration so I don't think we'll push the troublesome packages to the GNOME3 PPA until those problems are fixed.

---

### Post by VinDSL on 2012-12-25
Sounds prudent.

I used GS for 9+ hours, today.  No problems here.

Just did an upgrade, via Synaptic.  Still no GS probs.

Unity is the "problem child", right now... ;)

---

### Post by mc4man on 2012-12-25
> **VinDSL said:**
> 
Unity is the "problem child", right now... ;)
As far as menus, ect. IIRC from about a month or so ago if you were to switch to a gtk 3.7+ supported  theme then for the most part a ubuntu session would be ok
Likely a very short list of such themes, then the only one I saw was the spartan adwaita

---

### Post by VinDSL on 2012-12-25
Here is my theming (is that a word?)...  :D


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-25-dec-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-25-dec-2012-2.png")[/INDENT]


Been working great in GS!

Sorry for being rudimentary, but...

@ To those having problems with the GS user menu not appearing:


**User Menu Present in Upper-Right-Corner**
[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-25-dec-2012-3(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-25-dec-2012-3.png")[/INDENT]


**User Menu NOT Present in Upper-Right-Corner**
[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-25-dec-2012-4(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-25-dec-2012-4.png")[/INDENT]


Have you checked the "Stealth Mode" settings, in your "Privacy" section?

---

### Post by VinDSL on 2012-12-26
Speaking of g-c-c...

I just stepped through all of the options, in the User Menu.

They all worked, except "Settings -> Hardware -> Power".

g-c-c exits, [S] with no error dialog [/S], when I click the "Power" icon.

**EDIT**

Error dialog...

```

(gnome-control-center:5442): GLib-GIO-ERROR **: Settings schema 'org.gnome.settings-daemon.plugins.power' does not contain a key named 'lid-close-ac-action'
Trace/breakpoint trap

```

---

### Post by mc4man on 2012-12-26
> **VinDSL said:**
> Here is my theming (is that a word?)...  :D


That theme seems to work out ok here with unity (only synaptic looks a bit weird

---

### Post by Harry33 on 2012-12-26
The Gnome3 Staging PPA works fine here too (with adwaita theming).
Also the old gnome-panel 3.6.2 is working (but not the session gnome classic no effects).
I am using nvidia-current (313.09) from xorg-edgers PPA.

---

### Post by Cavsfan on 2012-12-26
I am trying to be a will participant but, I am not into adding extra PPA's that you already know are going to break.
But, I have had Raring running fairly flawlessly not using unity but, classic gnome.
Have Compiz, Emerald, CCSM, the cube and Cairo Dock all working great. The cube rotates in 3D and I managed to put colors on the top and bottom.
I had to use Application Switcher in CCSM to get ALT+TAB to work in gnome.
I got VinDSL's conky installed and updated to match my system (and added 13.04 to my signature).  :D

Just going with the updates that come down the pipe. I had a hard time getting the thing to install as it was trying to use my USB drive 
and would only install when I turned it off. But, I haven't hardly been able to get it to break for the last week or so. I get an error occasionally but, it doesn't force a reboot or anything.

Am I doing it wrong? :confused:

---

### Post by kansasnoob on 2012-12-26
OK, I have two fresh mini.iso installs of Ubuntu-GNOME-Remix running and I want to see what's cooking with the new Gnome classic session (yes I know it's still in the works) so I think I'll keep one install pretty much pure Raring but I'd like to use this PPA with the other.

But I have a dumb question :redface:

Do you recommend using this PPA all by it's lonesome, or in combination with the standard Gnome3 PPA?

EDIT: I should have looked first. I see there are no Raring packages in the standard Gnome3 PPA yet.

---

### Post by kansasnoob on 2012-12-26
OK, now we're cooking!

The most notable sort of borkage is that gdm takes ages to "populate" (by that I mean to display session options or anything) if I have auto-login set to "off". If auto-login is set to "on" it's not noticeable. But just forcing a downgrade of gdm alone doesn't fix it.

I see no changes to the fallback/classic sessions on this fresh mini.iso install of Ubuntu-GNOME-Remix and 'gnome-panel' is still installable after installing the PPA. And after doing so you can still boot into "classic (no effects)" so I assume that is still a work-in-progress which isn't surprising :)

I'd almost bet the new classic session either gets a new package name or maybe it'll be added to the shell-extensions package in the repos :confused:

Pretty hard to try and second guess things at this point.

---

### Post by VinDSL on 2012-12-26
> **kansasnoob said:**
> 

I'd almost bet the new classic session either gets a new package name or maybe it'll be added to the shell-extensions package in the repos.

Pretty hard to try and second guess things at this point.[...]
Sounds like you pegged it...

SOURCE: [http://planet.gnome.org/](http://planet.gnome.org/)


[QUOTE=Bastien Nocera]

GNOME 3.7.3 just got released earlier today, and includes some great new work. I won't be posting screenshots, because some of the UIs aren't final, and we'll be iterating until 3.8 is released (and it's my birthday).

**Cleaning up**

We've cleaned up gnome-settings-daemon plug-ins, and gnome-control-center panels, **[COLOR="Red"]as well as removing the support code for GNOME Fallback, saving us around 10k lines of code[/COLOR]**.

gnome-control-center (now "Settings" in the UI) is faster to start, and gnome-settings-daemon require less code to write additional plug-ins.[...][/QUOTE]


[QUOTE=Matthias Clasen]

Before Thanksgiving I’ve caused some uproar and made people doubt our incurable stubbornness by first announcing the release team decision to drop fallback mode, and then that we’re going to be looking at supported extensions as a replacement. Some have been calling this ‘classic’ mode – I’m using the term ‘legacy’ here, since ‘classic’ may raise some false expectations.

Two weeks have passed since that initial announcement, so I thought it would be a good idea to give an update on what we have achieved so far.

**GNOME Legacy**

**[COLOR="Red"]We’ve decided to use the gnome-shell-extensions repository as the place where we collect the extensions that will be part of this effort. If you configure with –enable-extensions=classic-mode, we will install a small set of extensions.[/COLOR]**[...]

**Modern GNOME**

Does all this attention on legacy mean that we no longer believe in GNOME 3 ? Of course not ! There’s plenty of great new stuff coming to GNOME 3.8.[/QUOTE]

Also, this page may give some insights:  [https://live.gnome.org/EveryDetailMatters](https://live.gnome.org/EveryDetailMatters)

---

### Post by kansasnoob on 2012-12-26
> **VinDSL said:**
> Sounds like you pegged it...

SOURCE: [http://planet.gnome.org/](http://planet.gnome.org/)







Also, this page may give some insights:  [https://live.gnome.org/EveryDetailMatters](https://live.gnome.org/EveryDetailMatters)

Great info :guitar:

I have some hope for the new "classic-mode" because I've been cross-testing Cinnamon (both in Snowlinux and Mint), and pure Gnome3/gnome-shell in Ubuntu-GNOME-Remix. Gnome's Mutter WM far outperforms the Cinnamon fork - Muffin!

I think Mint has recognized that because Clem is talking about an Openbox version of Cinnamon:

[https://github.com/linuxmint/Roadmap](https://github.com/linuxmint/Roadmap)

> Rethink Cinnamon 2D, fallback to a non-shadow CPU-less intensive session in software rendering mode and/or Muffin/OpenBox (whatever happens, the user should know he's not running the "real" Cinnamon, he should be told why, and he should find himself with a working WM (even a minimalistic one like OpenBox)).


But right now it's "wait and see" time :D

EDIT: This is also a good read:

[http://www.phoronix.com/scan.php?page=news_item&px=MTIzMzE](http://www.phoronix.com/scan.php?page=news_item&px=MTIzMzE)

> Untz recognizes that this may cause some fallout in GNOME 3.8 so he recommends those potentially negatively affected to stick with GNOME 3.6 for the time being. "There might be cases where these improvements will not be good enough in 3.8 (or with the Mesa and llvmpipe versions available at that time), resulting in a GNOME version that people might not consider acceptable in terms of performance or hardware support. Things will improve with time, obviously, and 3.10 will solve more and more issues; hence I would recommend to people hitting such issues to stay with 3.6 for a few more months." 

---

### Post by Cavsfan on 2012-12-27
I know I am in a little over my head but, I took the plunge and added the PPA and am currently updating.
I guess if it aint broke, break it! :tongue: The PPA page says:
                                
    This PPA will be used to test uploads before they are copied to the main GNOME 3 PPA.
 **If they break your system, you get to keep both halves.**
:lol:

---

### Post by VinDSL on 2012-12-27
> **Cavsfan said:**
> I know I am in a little over my head but, I took the plunge and added the PPA and am currently updating [...]

Like Jeremy said, in his original post...

> **jbicha said:**
> Unless you like broken things, you probably don't want this PPA yet. **[COLOR="Red"]At least make sure you know how to use ppa-purge first[/COLOR]**.

Personally, I log into Unity and endure it, as long as I can.  

Then, I switch to GS, for the rest of the session.  ;)

I don't expect to wash & rinse anything, unless both DEs break, at the same time...

---

### Post by Cavsfan on 2012-12-27
> **VinDSL said:**
> Like Jeremy said, in his original post...



Personally, I log into Unity and endure it, as long as I can.  

Then, I switch to GS, for the rest of the session.  ;)

I don't expect to wash & rinse anything, unless both DEs break, at the same time...

It's just a test installation any way so I figured why not.

Oh and I do know how to use ppa purge.

I got it and rebooted and now the theme is all white and almost impossible to view.
I installed gnome-tweak-tool and tried to get it black like you pictures you posted but, could not quite get there from here.
The top and bottom panels are pretty much white with white text.

I'll play around with it again tomorrow. :D

---

### Post by VinDSL on 2012-12-27
> **Cavsfan said:**
> I got it and rebooted and now the theme is all white and almost impossible to view.[...]

I'll play around with it again tomorrow. :D
Hrm...

I've been toying with GS, since it became available.

Over time, I've used various PPAs.  Some PPAs were/are more stable than others.

Most recently, I've been using ricotz/testing:

[INDENT][https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)[/INDENT]


You *might* want to upgrade your system with these packages (e.g. fill some of the holes) then disable it, when you're done.

Basically, my setup is a standard GS install, upgraded with packages from ricotz/testing, and gnome3-team/gnome3-staging.

To be clear, the only unsupported packages that I'm currently checking/upgrading are from gnome3-team/gnome3-staging.  ;)

---

### Post by jbicha on 2012-12-27
> **VinDSL said:**
> 
They all worked, except "Settings -> Hardware -> Power".

g-c-c exits, [S] with no error dialog [/S], when I click the "Power" icon.

```

(gnome-control-center:5442): GLib-GIO-ERROR **: Settings schema 'org.gnome.settings-daemon.plugins.power' does not contain a key named 'lid-close-ac-action'
Trace/breakpoint trap

```

Fixed by disabling the Ubuntu power panel patches as the gnome-settings-daemon patch they depend on hasn't been ported to GNOME 3.7 yet.

---

### Post by Starks on 2012-12-28
Really nasty upstream bug

[Bug 690703 - Date and AM/PM missing from top bar](https://bugzilla.gnome.org/show_bug.cgi?id=690703)

Americans hate military time

---

### Post by zika on 2012-12-28
I've boarded Your train. But appearance of menus in Fallback(NOEffects) and appearance of Terminal and similar even in GS is very ugly... What am I missing?
Update&#8321;: Remembered that I need gnome-tweak-tool ... ;)
Update&#8322;: Nice... Just enough configurable settings for my taste...
Update&#8323;: You've got me hooked again...

---

### Post by Cavsfan on 2012-12-28
> **VinDSL said:**
> Hrm...

I've been toying with GS, since it became available.

Over time, I've used various PPAs.  Some PPAs were/are more stable than others.

Most recently, I've been using ricotz/testing:[INDENT][https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)[/INDENT]You *might* want to upgrade your system with these packages (e.g. fill some of the holes) then disable it, when you're done.

Basically, my setup is a standard GS install, upgraded with packages from ricotz/testing, and gnome3-team/gnome3-staging.

To be clear, the only unsupported packages that I'm currently checking/upgrading are from gnome3-team/gnome3-staging.  ;)

I tried adding the ricotz/testing PPA and everything seemed to go well but upon rebooting, nothing would open: tweak tool, firefox, etc.

So I installed ppa-purge and tried to purge both PPAs but, that didn't work:

```
cavsfan@cavsfan-MS-7529:~$ sudo ppa-purge ppa:ricotz/testing
Updating packages lists
PPA to be removed: ricotz testing
Warning:  Could not find package list for PPA: ricotz testing
``````
cavsfan@cavsfan-MS-7529:~$ sudo ppa-purge gnome3-team/gnome3-staging
Updating packages lists
PPA to be removed: gnome3-team/gnome3-staging ppa
Warning:  Could not find package list for PPA: gnome3-team/gnome3-staging ppa

```I think I broke it. :-s Time to reinstall I guess. I'll download a newer iso.
It was probably time any way. Nothing was breaking at all. ;)

---

### Post by VinDSL on 2012-12-28
> **zika said:**
> 
Update&#8323;: You've got me hooked again...


Rather addictive, yes?  :D


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-28-dec-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-28-dec-2012-1.png")[/INDENT]

---

### Post by VinDSL on 2012-12-28
> **Cavsfan said:**
> 
I think I broke it. :-s Time to reinstall I guess. I'll download a newer iso.
It was probably time any way. Nothing was breaking at all. ;)

Keep after it!

It's no fun, when things just work...  :)

---

### Post by VinDSL on 2012-12-29
w00t!  I figured out why Unity was looking janky, e.g. solid  black background on the desktop and switcher!

Actually, I discovered the 'problem' while playing around in LXDE.

I wanted to see what would happen if I didn't allow PCMANFM to control the desktop, and guess what?  It looked just like Unity.  LoL!  :D

Long-story-short, I allowed Nautilus to control the desktop in GS -- logged into Unity -- and Bingo!


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-28-dec-2012-3(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-28-dec-2012-3.png")[/INDENT]


Looks like grunt, with the defaults being "stickified", and all, but at least it's a start...  ;)

---

### Post by zika on 2012-12-29
> **VinDSL said:**
> Rather addictive, yes?  :DIt is, and fast...
It works nicely both from gdm and lightdm... I even seem to like it more with lightdm...
It works also nicely from .Xsession (startx) but I'm having problem finding way to start fallback from .Xsession... I'll have to investigate syntax for that today if time permits...
Many things are waiting to be discovered in this new GS...

---

### Post by kansasnoob on 2012-12-29
> **zika said:**
> It is, and fast...
It works nicely both from gdm and lightdm... I even seem to like it more with lightdm...
It works also nicely from .Xsession (startx) but I'm having problem finding way to start fallback from .Xsession... I'll have to investigate syntax for that today if time permits...
Many things are waiting to be discovered in this new GS...

The most amazing thing to me is the performance as compared to Mint's Muffin fork of Mutter and Ubuntu's Compiz ............. I'm at least guessing it's 90% a window manager thing. Time will tell :)

---

### Post by zika on 2012-12-29
> **kansasnoob said:**
> The most amazing thing to me is the performance as compared to Mint's Muffin fork of Mutter and Ubuntu's Compiz ............. I'm at least guessing it's 90% a window manager thing. Time will tell :)
I feel that it is faster with lightdm than with gdm but I was playing with fallback so... Yesterday I've spent whole day in vanilla GS&gdm... Like it...

---

### Post by Cavsfan on 2012-12-29
> **VinDSL said:**
> Keep after it!

It's no fun, when things just work...  :)

Well, I pretty much have it back like it was. The newer ISO gave some better apps than the one I initially used.
I forgot how much stuff you have to add to a fresh install to get it like you want it: Nvidia drivers, Compiz, CCSM, 
Cairo Dock, lm-sensors (and sudo sensors-detect), conky-all, conkywx, Emerald, getting the date to display, add fonts, gnome-session-fallback, 
the startup sound, and I am sure I left a few out.

Edit: Plus disabling firefox-globalmenu in Firefox, adding the desired add-ons and disabling the global menu bar (remove appmenu-gtk appmenu-gtk3 appmenu-qt). Plus installing flash and java.

At least this is the way I like my setup to be. 

I think I'll give it a couple of days and add the PPA and hopefully not break it this time. ;)

---

### Post by Cavsfan on 2012-12-31
I tried to load the PPA again with almost the same results. I also added the ricotz/testing PPA.

But, this time I managed to ppa-purge those and recover just like they were never added :)

With the only exception I see so far is that my Firefox settings including NoScript settings were annihilated. 

It may be that I have to give it some time because at first nothing would open when clicked on.
Then slowly some things would open even firefox. Since I now know how to get out of it with a purge I will try it again and give it some time.

Did any one else require some time for thing to "kick in"?

---

### Post by kansasnoob on 2012-12-31
> **Cavsfan said:**
> I tried to load the PPA again with almost the same results. I also added the ricotz/testing PPA.

But, this time I managed to ppa-purge those and recover just like they were never added :)

With the only exception I see so far is that my Firefox settings including NoScript settings were annihilated. 

It may be that I have to give it some time because at first nothing would open when clicked on.
Then slowly some things would open even firefox. Since I now know how to get out of it with a purge I will try it again and give it some time.

Did any one else require some time for thing to "kick in"?

The only problem I've noticed is that it takes several minutes for the GDM scrren to accept any input and respond. It's OK if you just use "auto-login" and never need to log out to change sessions or such.

I've thought about trying lightdm but I haven't been annoyed enough yet :D

---

### Post by Cavsfan on 2012-12-31
> **kansasnoob said:**
> The only problem I've noticed is that it takes several minutes for the GDM scrren to accept any input and respond. It's OK if you just use "auto-login" and never need to log out to change sessions or such.

I've thought about trying lightdm but I haven't been annoyed enough yet :D

OK, that must have been what I experienced. I'll try again and give it time.

I somewhere "chose" lightdm as I thought that was what we had to go with for Nvidia. 
But, the fact that I was presented with an option of GDM or lightdm, I should have known.
I thought they dropped GDM with Lucid.

---

### Post by VinDSL on 2013-01-01
Though I would throw this out, for public consumption...

These errors/warnings started appearing about a week ago, during incremental (semi-daily) updates & upgrades -- and, the list of packages (at the bottom of the dialog) is growing like a cancer.

```

Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
(Reading database ... 406805 files and directories currently installed.)
Preparing to replace postfix 2.9.3-2ubuntu2.1 (using .../postfix_2.9.5-1ubuntu1_i386.deb) ...
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
dpkg: error processing /var/cache/apt/archives/postfix_2.9.5-1ubuntu1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to replace yajhfc 0.5.2-1 (using .../yajhfc_0.5.3-1_all.deb) ...
Unpacking replacement yajhfc ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Errors were encountered while processing:
 /var/cache/apt/archives/postfix_2.9.5-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up man-db (2.6.3-3) ...
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up yajhfc (0.5.3-1) ...
Setting up postfix (2.9.3-2ubuntu2.1) ...
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up cups-bsd (1.6.1-0ubuntu13) ...
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
dpkg: error processing cups-bsd (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up cups (1.6.1-0ubuntu13) ...
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
dpkg: error processing cups (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for menu ...
[B][COLOR="Red"]Errors were encountered while processing:
 man-db
 postfix
 cups-bsd
 cups[/COLOR][/B]


```

*Gut feeling* tells me, as this "Russian Roulette" game continues, it's eventually going to hit a loaded cylinder, and result in some major breakage.

Just saying...

---

### Post by dino99 on 2013-01-01
hello bro, happy new year to you :)

looks like you get a perl issue; do you use some perl packages from a non genuine archive ?

---

### Post by VinDSL on 2013-01-01
> **dino99 said:**
> hello bro, happy new year to you :)

looks like you get a perl issue; do you use some perl packages from a non genuine archive ?
Happy New Year, Dino!

Official PPA AFAIK... 

I'll check it out later, today.  I'm on the trot, right now.

---

### Post by zika on 2013-01-02
I needed gnome-tweak-tool today to try some other theme because I see a problem in upper right corner of fallback session (fully upgraded to GS PPA) and I've got:
```
:~$ gnome-tweak-tool &
[1] 18307
INFO    : Schema missing summary org.gnome.settings-daemon.peripherals.gschema.xml (key repeat)
INFO    : Schema missing summary org.gnome.settings-daemon.peripherals.gschema.xml (key click)
INFO    : Schema missing summary org.gnome.settings-daemon.peripherals.gschema.xml (key click-volume)
INFO    : Schema missing summary org.gnome.settings-daemon.peripherals.gschema.xml (key bell-mode)
INFO    : Schema missing summary org.gnome.settings-daemon.peripherals.gschema.xml (key bell-pitch)
INFO    : Schema missing summary org.gnome.settings-daemon.peripherals.gschema.xml (key bell-duration)
WARNING : Error detecting shell
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell_extensions.py", line 172, in __init__
    shell = GnomeShellFactory().get_shell()
  File "/usr/lib/python2.7/dist-packages/gtweak/utils.py", line 39, in getinstance
    instances[cls] = cls()
  File "/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py", line 161, in __init__
    proxy = _ShellProxy()
  File "/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py", line 53, in __init__
    result, output = self.proxy.Eval('(s)', js)
  File "/usr/lib/python2.7/dist-packages/gi/overrides/Gio.py", line 171, in __call__
    None)
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 113, in function
    return info.invoke(*args, **kwargs)
GError: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.Shell was not provided by any .service files
INFO    : GSettings missing key org.gnome.nautilus.desktop (key computer-icon-visible)
Traceback (most recent call last):
  File "/usr/bin/gnome-tweak-tool", line 75, in <module>
    MainWindow()
  File "/usr/lib/python2.7/dist-packages/gtweak/mainwindow.py", line 41, in __init__
    model)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakview.py", line 58, in __init__
    self._model.load_tweaks()
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakmodel.py", line 147, in load_tweaks
    mods = __import__("gtweak.tweaks", globals(), locals(), tweak_files, 0)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell.py", line 209, in <module>
    class StaticWorkspaceTweak(Tweak):
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell.py", line 214, in StaticWorkspaceTweak
    _shell = GnomeShellFactory().get_shell()
  File "/usr/lib/python2.7/dist-packages/gtweak/utils.py", line 39, in getinstance
    instances[cls] = cls()
  File "/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py", line 161, in __init__
    proxy = _ShellProxy()
  File "/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py", line 53, in __init__
    result, output = self.proxy.Eval('(s)', js)
  File "/usr/lib/python2.7/dist-packages/gi/overrides/Gio.py", line 171, in __call__
    None)
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 113, in function
    return info.invoke(*args, **kwargs)
gi._glib.GError: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.Shell was not provided by any .service files

```

```
:~$ gnome-tweak-tool --test --debug &
[1] 21665
DEBUG   : No translated schema for org.gnome.desktop.input-sources (domain: gsettings-desktop-schemas)
DEBUG   : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.desktop.input-sources>
DEBUG   : Schema not translated org.gnome.settings-daemon.peripherals.keyboard (domain: gnome-settings-daemon)
DEBUG   : Schema not translated org.gnome.settings-daemon.peripherals.keyboard (domain: gnome-settings-daemon)
DEBUG   : Schema not translated org.gnome.settings-daemon.peripherals.keyboard (domain: gnome-settings-daemon)
DEBUG   : Schema not translated org.gnome.settings-daemon.peripherals.keyboard (domain: gnome-settings-daemon)
INFO    : Schema missing summary org.gnome.settings-daemon.peripherals.gschema.xml (key repeat)
INFO    : Schema missing summary org.gnome.settings-daemon.peripherals.gschema.xml (key click)
INFO    : Schema missing summary org.gnome.settings-daemon.peripherals.gschema.xml (key click-volume)
INFO    : Schema missing summary org.gnome.settings-daemon.peripherals.gschema.xml (key bell-mode)
INFO    : Schema missing summary org.gnome.settings-daemon.peripherals.gschema.xml (key bell-pitch)
INFO    : Schema missing summary org.gnome.settings-daemon.peripherals.gschema.xml (key bell-duration)
DEBUG   : Schema not translated org.gnome.settings-daemon.peripherals.keyboard (domain: gnome-settings-daemon)
DEBUG   : Schema not translated org.gnome.settings-daemon.peripherals.keyboard (domain: gnome-settings-daemon)
DEBUG   : Schema not translated org.gnome.settings-daemon.peripherals.keyboard (domain: gnome-settings-daemon)
DEBUG   : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.settings-daemon.peripherals.keyboard>
WARNING : Error detecting shell
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell_extensions.py", line 172, in __init__
    shell = GnomeShellFactory().get_shell()
  File "/usr/lib/python2.7/dist-packages/gtweak/utils.py", line 39, in getinstance
    instances[cls] = cls()
  File "/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py", line 161, in __init__
    proxy = _ShellProxy()
  File "/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py", line 53, in __init__
    result, output = self.proxy.Eval('(s)', js)
  File "/usr/lib/python2.7/dist-packages/gi/overrides/Gio.py", line 171, in __call__
    None)
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 113, in function
    return info.invoke(*args, **kwargs)
GError: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.Shell was not provided by any .service files
DEBUG   : No translated schema for org.gnome.desktop.interface (domain: gsettings-desktop-schemas)
DEBUG   : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.desktop.interface>
DEBUG   : Schema not translated org.gnome.desktop.wm.preferences (domain: gsettings-desktop-schemas)
DEBUG   : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.desktop.wm.preferences>
DEBUG   : Schema not translated org.gnome.settings-daemon.plugins.xsettings (domain: gnome-settings-daemon)
DEBUG   : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.settings-daemon.plugins.xsettings>
DEBUG   : No translated schema for org.gnome.desktop.background (domain: gsettings-desktop-schemas)
DEBUG   : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.desktop.background>
DEBUG   : Found desktop file: /usr/share/applications/nautilus.desktop
DEBUG   : User autostart desktop file: /home/zika/.config/autostart/nautilus-autostart.desktop
DEBUG   : Schema not translated org.gnome.nautilus.desktop (domain: nautilus)
DEBUG   : Schema not translated org.gnome.nautilus.desktop (domain: nautilus)
DEBUG   : Schema not translated org.gnome.nautilus.desktop (domain: nautilus)
DEBUG   : Schema not translated org.gnome.nautilus.desktop (domain: nautilus)
DEBUG   : Schema not translated org.gnome.nautilus.desktop (domain: nautilus)
DEBUG   : Schema not translated org.gnome.nautilus.desktop (domain: nautilus)
DEBUG   : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.nautilus.desktop>
INFO    : GSettings missing key org.gnome.nautilus.desktop (key computer-icon-visible)
DEBUG   : Schema not translated org.gnome.nautilus.preferences (domain: nautilus)
DEBUG   : Schema not translated org.gnome.nautilus.preferences (domain: nautilus)
DEBUG   : Schema not translated org.gnome.nautilus.preferences (domain: nautilus)
DEBUG   : Schema not translated org.gnome.nautilus.preferences (domain: nautilus)
DEBUG   : Schema not translated org.gnome.nautilus.preferences (domain: nautilus)
DEBUG   : Schema not translated org.gnome.nautilus.preferences (domain: nautilus)
DEBUG   : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.nautilus.preferences>
Traceback (most recent call last):
  File "/usr/bin/gnome-tweak-tool", line 75, in <module>
    MainWindow()
  File "/usr/lib/python2.7/dist-packages/gtweak/mainwindow.py", line 41, in __init__
    model)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakview.py", line 58, in __init__
    self._model.load_tweaks()
  File "/usr/lib/python2.7/dist-packages/gtweak/tweakmodel.py", line 147, in load_tweaks
    mods = __import__("gtweak.tweaks", globals(), locals(), tweak_files, 0)
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell.py", line 209, in <module>
    class StaticWorkspaceTweak(Tweak):
  File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_shell.py", line 214, in StaticWorkspaceTweak
    _shell = GnomeShellFactory().get_shell()
  File "/usr/lib/python2.7/dist-packages/gtweak/utils.py", line 39, in getinstance
    instances[cls] = cls()
  File "/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py", line 161, in __init__
    proxy = _ShellProxy()
  File "/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py", line 53, in __init__
    result, output = self.proxy.Eval('(s)', js)
  File "/usr/lib/python2.7/dist-packages/gi/overrides/Gio.py", line 171, in __call__
    None)
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 113, in function
    return info.invoke(*args, **kwargs)
gi._glib.GError: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.Shell was not provided by any .service files

```

---

### Post by grahammechanical on 2013-01-02
This staging ppa seems to have solved some issues for me. I now have in the top panel an icon that lets me switch keyboard layouts. And the system freezes that happened when closing utility and applications windows does not happen any more. Good stuff.

regards.

---

### Post by mc4man on 2013-01-02
> **grahammechanical said:**
> This staging ppa seems to have solved some issues for me.  And the system freezes that happened when closing utility and applications windows does not happen any more..

The system freezes on window closings is also fixed here with ppa though the ubuntu version still does so  & remains almost worthless
(- having gnome-shell, (gnome-shell --replace), running in a terminal on current workspace prevented/prevents the freezes

---

### Post by zika on 2013-01-03
Any idea how to change theme without gnome-tweak-tool?

---

### Post by Starks on 2013-01-03
Waiting for this commit to get pulled in

[http://git.gnome.org/browse/gnome-desktop/commit/?id=0940370f82730359a7771aae750136e3fe6bfaa9](http://git.gnome.org/browse/gnome-desktop/commit/?id=0940370f82730359a7771aae750136e3fe6bfaa9)

---

### Post by VinDSL on 2013-01-03
> **zika said:**
> Any idea how to change theme without gnome-tweak-tool?
Looks like dconf -> org.gnome.desktop.interface should do it...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-3-dec-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-3-dec-2012-1.png")[/INDENT]

---

### Post by zika on 2013-01-03
> **VinDSL said:**
> Looks like dconf -> org.gnome.desktop.interface should do it...
[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-3-dec-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-3-dec-2012-1.png")[/INDENT]Great! Thank You! Running to try...
Update&#8321;: Simple tools are always the best! It worked... I'll play with this again when I get some free time... Thank You! All the best!

---

### Post by Cavsfan on 2013-01-03
Tried this once again and got this:```

Fetched 20.2 MB in 25s (792 kB/s)                                                                                                                                                                                 
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 empathy : Depends: libtelepathy-logger3 (>= 0.2.10) but it is not installed
 libtelepathy-logger3-dbg : Depends: libtelepathy-logger3 (= 0.6.0-2~git1) but it is not installed
 telepathy-logger : Depends: libtelepathy-logger3 (= 0.6.0-2~git1) but it is not installed
E: Unmet dependencies. Try using -f.
cavsfan@cavsfan-MS-7529:
```Did a little search for "libtelepathy-logger3" and found a bug that was opened about 3 hours ago. 

[https://bugs.launchpad.net/ubuntu/+source/telepathy-logger/+bug/1095745](https://bugs.launchpad.net/ubuntu/+source/telepathy-logger/+bug/1095745)

Any idears?
I'm guessing everyone is getting this.

---

### Post by celluloid on 2013-01-03
> **Cavsfan said:**
> Tried this once again and got this:```

Fetched 20.2 MB in 25s (792 kB/s)                                                                                                                                                                                 
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 empathy : Depends: libtelepathy-logger3 (>= 0.2.10) but it is not installed
 libtelepathy-logger3-dbg : Depends: libtelepathy-logger3 (= 0.6.0-2~git1) but it is not installed
 telepathy-logger : Depends: libtelepathy-logger3 (= 0.6.0-2~git1) but it is not installed
E: Unmet dependencies. Try using -f.
cavsfan@cavsfan-MS-7529:
```Did a little search for "libtelepathy-logger3" and found a bug that was opened about 3 hours ago. 

[https://bugs.launchpad.net/ubuntu/+source/telepathy-logger/+bug/1095745](https://bugs.launchpad.net/ubuntu/+source/telepathy-logger/+bug/1095745)

Any idears?
I'm guessing everyone is getting this.

I can confirm I too receive that error message. :(
I'm sure it'll be fixed soon.

---

### Post by celluloid on 2013-01-03
> **celluloid said:**
> I can confirm I too receive that error message. :(
I'm sure it'll be fixed soon.

Looks like it's resolved. A full update works now :)

---

### Post by Cavsfan on 2013-01-04
> **celluloid said:**
> Looks like it's resolved. A full update works now :)

Wonder why I am still getting the same error. :confused:

---

### Post by Cavsfan on 2013-01-04
> **VinDSL said:**
> Looks like dconf -> org.gnome.desktop.interface should do it...
[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-3-dec-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-3-dec-2012-1.png")[/INDENT]

What do you have set for GTK-Color-Scheme for the foreground? I cannot see it.
All I can see is **selected_bg_color:#D3B37D**
On a white background like google the font color when I type is white which is invisable to me.
Thanks

---

### Post by Cavsfan on 2013-01-05
Deleted

---

### Post by VinDSL on 2013-01-06
> **dino99 said:**
> looks like you get a perl issue[...]

> **VinDSL said:**
> I'll check it out later, today.  I'm on the trot, right now.
I'm finally at juggernauts...

After days of tussling with this problem, which I believe to be caused by corrupt debconf perl modules, I'm now being blocked at any attempt to fix them by an unconfigured libpam0g:i386 package. LoL!

Oh, what a tangled web we weave!

I might have to swallow my pride and do a fresh install... :P

---

### Post by VinDSL on 2013-01-06
> **Cavsfan said:**
> What do you have set for GTK-Color-Scheme for the foreground? I cannot see it[...]
```
gtk-color-scheme: selected_bg_color:#D3B37D;**[COLOR="Red"]selected_fg_color:#3c3b37[/COLOR]**
```

---

### Post by dino99 on 2013-01-06
> **VinDSL said:**
> I'm finally at juggernauts...

After days of tussling with this problem, which I believe to be caused by corrupt debconf perl modules, I'm now being blocked at any attempt to fix them by an unconfigured libpam0g:i386 package. LoL!

Oh, what a tangled web we weave!

I might have to swallow my pride and do a fresh install... :P

First you can probably play with ppa-purge, then:

sudo dpkg-reconfigure -phigh -a
(can take a while, dont stop it yourself)

---

### Post by VinDSL on 2013-01-06
> **dino99 said:**
> First you can probably play with ppa-purge, then:

sudo dpkg-reconfigure -phigh -a
(can take a while, dont stop it yourself)
I tried purging this n' that,but got a lovely warning about deleting 137 packages (or whatever). It really is a wonderful message!  

You cannot simply type "Y". You actually have to type in a phrase, like "Yes, I want to go ahead and destroy my system!".  LoL!  :D

Here is the result of the dpkg-reconfigure command (above):

```
vindsl@Zuul:~$ sudo dpkg-reconfigure -phigh -a
[sudo] password for vindsl: 
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
vindsl@Zuul:~$ 
```

Nice, eh what?  :)

---

### Post by dino99 on 2013-01-06
yeah there is a conflict somewhere; so try to purge the less problematic ppa first, etc

or swallow your hat and reinstall  :p  ):P

---

### Post by riderplus on 2013-01-06
There are no updates available for evince (the old 3.6 is still there), eog and others. Why not? In the ppa package it says there are.

---

### Post by VinDSL on 2013-01-06
> **dino99 said:**
> yeah there is a conflict somewhere; so try to purge the less problematic ppa first, etc
Maybe I'll start with libpam...

What do you think?  Should I do it, Dino?  LoL!  :D


```
vindsl@Zuul:~$ sudo apt-get purge libpam0g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  activity-log-manager-common crda extlinux galculator gambas2-gb-gtk
  gambas2-gb-gtk-ext gambas2-gb-settings gambas2-runtime giblib1
  gir1.2-gst-plugins-base-0.10 gir1.2-gstreamer-0.10 gir1.2-gudev-1.0
  gir1.2-indicate-0.7 gir1.2-syncmenu-0.1 hylafax-client iw leafpad
  libgdata2.1-cil libglademm-2.4-1c2a libjs-underscore libmono-data-tds4.0-cil
  libmono-system-data4.0-cil libmono-system-enterpriseservices4.0-cil
  libmono-system-runtime-serialization4.0-cil
  libmono-system-transactions4.0-cil libmono-system-xml-linq4.0-cil
  libnewtonsoft-json4.5-cil libnuma1 libotf0 libqt4-test libqtassistantclient4
  librpmbuild3 librpmsign1 libsync-menu1 libtaglib2.1-cil libxmmsclient-glib1
  lxappearance lxinput lxmusic lxrandr lxsession-edit m17n-contrib m17n-db
  menu-xdg python-dirspec python-gpgme python-nautilus python-sip
  python3-chardet python3-debian python3-lxml python3-six rpm scrot sqlite3
  sqliteman-doc syslinux-themes-debian syslinux-themes-debian-wheezy tdb-tools
  unetbootin-translations wireless-crda wireless-regdb xarchiver xmms2-core
  xmms2-plugin-alsa xmms2-plugin-id3v2 xmms2-plugin-mad xmms2-plugin-vorbis
  xsane-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libcups2
The following packages will be REMOVED:
  account-plugin-aim* account-plugin-facebook* account-plugin-flickr*
  account-plugin-google* account-plugin-identica* account-plugin-jabber*
  account-plugin-salut* account-plugin-twitter* account-plugin-windows-live*
  account-plugin-yahoo* accountsservice* acpi-support* acpid*
  activity-log-manager* activity-log-manager-control-center* adduser*
  aisleriot* alsa-base* alsa-utils* anacron* apparmor* apport* apport-gtk*
  apt-xapian-index* aptdaemon* aptitude* at* avahi-autoipd* avahi-daemon*
  avahi-utils* bamfdaemon* banshee* banshee-extension-liveradio*
  banshee-extension-radiostationfetcher* banshee-extension-soundmenu*
  banshee-extensions-common* binfmt-support* bluez* bluez-alsa* bluez-cups*
  bluez-gstreamer* brasero* brltty* bsd-mailx* caribou* caribou-antler*
  checkbox* checkbox-gtk* clipgrab* colord* compiz* compiz-core* compiz-gnome*
  compiz-plugins* compiz-plugins-default* compiz-plugins-extra*
  compiz-plugins-main-default* compizconfig-backend-gconf*
  compizconfig-settings-manager* conkywx* console-setup* consolekit* cron*
  cryptsetup-bin* cups* cups-bsd* cups-client* cups-driver-gutenprint* dbus*
  dbus-x11* deja-dup-backend-gvfs* dkms* dmsetup* dnsmasq-base* doc-base*
  e2fsprogs* easy-stopwatch* eject* empathy* evince* evolution*
  evolution-data-server* evolution-plugins* firefox* firefox-globalmenu*
  firefox-gnome-support* flashplugin-installer* fontmatrix* friendly-recovery*
  fuse* fuse-utils* gambas2-gb-form* gambas2-gb-gui* gambas2-gb-qt*
  gconf-defaults-service* gconf-editor* gconf2* gcr* gdebi* gdm* gedit*
  gedit-plugins* geoclue* geoclue-ubuntu-geoip* ghostscript-x* gimp*
  gir1.2-caribou-1.0* gir1.2-gdata-0.0* gir1.2-gkbd-3.0* gir1.2-goa-1.0*
  gir1.2-mutter-3.0* gir1.2-networkmanager-1.0* gir1.2-rb-3.0*
  gir1.2-totem-1.0* gir1.2-tracker-0.14* gir1.2-ubuntuoneui-3.0*
  gir1.2-unique-3.0* gir1.2-webkit-3.0* gir1.2-xkl-1.0* gir1.2-zpj-0.0*
  gkbd-capplet* gksu* gnome* gnome-alsamixer* gnome-applets*
  gnome-applets-data* gnome-bluetooth* gnome-color-chooser*
  gnome-color-manager* gnome-contacts* gnome-control-center*
  gnome-control-center-signon* gnome-control-center-unity* gnome-core*
  gnome-disk-utility* gnome-documents* gnome-keyring* gnome-media*
  gnome-network-admin* gnome-online-accounts* gnome-panel*
  gnome-power-manager* gnome-screensaver* gnome-search-tool* gnome-session*
  gnome-session-bin* gnome-session-fallback* gnome-shell*
  gnome-shell-extensions* gnome-sushi* gnome-system-log* gnome-system-tools*
  gnome-terminal* gnome-themes-standard* gnome-user-guide* gnome-user-share*
  gparted* graphviz* grub-common* grub-gfxpayload-lists* grub-pc* grub-pc-bin*
  grub2-common* gstreamer0.10-gconf* gstreamer0.10-nice*
  gstreamer0.10-plugins-bad* gtk-recordmydesktop* guayadeque* gvfs*
  gvfs-backends* gvfs-daemons* gvfs-fuse* gwibber-service-facebook*
  gwibber-service-identica* gwibber-service-twitter* hamster-applet*
  hamster-indicator* hostname* hplip* hplip-cups* hylafax-server* ibus*
  ibus-pinyin* ibus-table* ifupdown* indicator-appmenu* indicator-datetime*
  indicator-power* indicator-printers* indicator-session* indicator-sound*
  initramfs-tools* initscripts* inkscape* irqbalance* jdownloader*
  jockey-common* jockey-gtk* kbd* kernel-package* kerneloops-daemon*
  keyboard-configuration* kmod* language-selector-common* libaudio2*
  libbamf3-0* libblkid1* libbonoboui2-0* libcanberra-pulse* libcaribou0*
  libcompizconfig0* libcryptsetup4* libdconf-qt0* libdevmapper-event1.02.1*
  libdevmapper1.02.1* libedata-book-1.2-15* libevolution* libfarstream-0.1-0*
  libfolks-eds25* libgdata13* libgdu0* libgksu2-0*
  libgnome-media-profiles-3.0-0* libgnome2-0* libgnome2-bin* libgnome2-common*
  libgnomekbd7* libgnomekbd8* libgnomeui-0* libgnomevfs2-0*
  libgnomevfs2-common* libgnomevfs2-extra* libgoa-1.0-0* libgpod-common*
  libgpod4* libgtkglext1* libgupnp-1.0-3* libgupnp-1.0-4* libgupnp-av-1.0-2*
  libgupnp-igd-1.0-3* libgupnp-igd-1.0-4* libimobiledevice2*
  libimobiledevice3* liblightdm-gobject-1-0* liblvm2app2.2* libm17n-0*
  libmount1* libmutter0a* libnice10* libnm-glib-vpn1* libnm-glib4* libnm-gtk0*
  libnm-util2* libnss-mdns* liboobs-1-5* libpam-cap* libpam-ck-connector*
  libpam-freerdp* libpam-gnome-keyring* libpam-modules* libpam-modules-bin*
  libpam-runtime* libpam-smbpass* libpam0g* libparted0debian1* libpurple0*
  libqscintilla2-8* libqt3-mt* libqt4-declarative* libqt4-designer*
  libqt4-help* libqt4-opengl* libqt4-scripttools* libqt4-svg* libqt4-webkit*
  libqtbamf1* libqtdee2* libqtgconf1* libqtgui4* libqtwebkit4* librasqal3*
  librdf0* libreoffice* libreoffice-base* libreoffice-base-core*
  libreoffice-calc* libreoffice-core* libreoffice-draw*
  libreoffice-emailmerge* libreoffice-gnome* libreoffice-gtk*
  libreoffice-help-en-gb* libreoffice-help-en-us* libreoffice-impress*
  libreoffice-math* libreoffice-pdfimport* libreoffice-writer*
  librhythmbox-core6* librygel-core-1.0-0* librygel-renderer-1.0-0*
  librygel-server-1.0-0* libsane* libslv2-9* libsm6* libsyncdaemon-1.0-1*
  libtelepathy-farstream2* libtotem0* libtracker-extract-0.14-0*
  libtracker-miner-0.14-0* libtracker-sparql-0.14-0* libubuntuoneui-3.0-1*
  libunique-1.0-0* libunique-3.0-0* libunity-2d-private0* libunity-webapps0*
  libutempter0* libuuid-perl* libuuid1* libwebkitgtk-1.0-0*
  libwebkitgtk-3.0-0* libwxgtk2.8-0* libwxsqlite3-2.8-0* libxapian22* libxaw7*
  libxklavier16* libxmu6* libxt6* libyelp0* libzapojit-0.0-0* lightdm*
  lightdm-remote-session-freerdp* lightdm-remote-session-uccsconfigure*
  lightread* linux-image-3.8.0-030800rc1-generic*
  linux-image-extra-3.8.0-030800rc1-generic* linux-sound-base* login*
  logrotate* lxde* lxde-core* mcp-account-manager-uoa* media-player-info*
  menulibre* metacity* mlocate* modemmanager* module-init-tools* mount*
  mountall* mutter* mythes-en-us* myunity* nautilus* nautilus-dropbox*
  nautilus-open-as-root* nautilus-open-terminal-here* nautilus-sendto*
  nautilus-sendto-empathy* network-manager* network-manager-gnome*
  network-manager-pptp* network-manager-pptp-gnome* ntfs-3g* ntfsprogs*
  nvidia-current-updates* nvidia-settings* openbox* openbox-themes*
  openssh-client* openssh-server* opera-next* parted* passwd* plymouth*
  plymouth-label* plymouth-theme-ubuntu-logo* plymouth-theme-ubuntu-text*
  pm-utils* policykit-1* policykit-1-gnome* postfix* powermgmt-base* ppp*
  pppconfig* pppoeconf* pptp-linux* printer-driver-gutenprint*
  printer-driver-hpcups* printer-driver-postscript-hp* procps* pulseaudio*
  pulseaudio-module-x11* pulseaudio-utils* python-compizconfig* python-gnome2*
  python-pam* python-qt4* python-ubuntu-sso-client*
  python-ubuntuone-control-panel* python-uno* python-webkit* python-wxgtk2.8*
  python-xapian* qupzilla* recordmydesktop* remote-login-service* resolvconf*
  rfkill* rhythmbox* rhythmbox-mozilla* rhythmbox-plugin-cdrecorder*
  rhythmbox-plugin-zeitgeist* rhythmbox-plugins* rhythmbox-ubuntuone* rsyslog*
  rtkit* rygel* rygel-playbin* rygel-preferences* rygel-tracker* samba*
  samba-common-bin* sane-utils* screen-resolution-extra* seahorse*
  sessioninstaller* shotwell* signon-plugin-oauth2* signon-ui* simple-scan*
  skype* skype-bin* software-properties-gtk* sound-juicer* spamassassin*
  speech-dispatcher* sqliteman* ssh* ssh-askpass-gnome* ssh-import-id*
  ssl-cert* sudo* synaptic* syslinux* system-tools-backends* telepathy-gabble*
  telepathy-haze* telepathy-mission-control-5* telepathy-salut* testdisk*
  thunderbird* thunderbird-globalmenu* thunderbird-locale-en*
  thunderbird-locale-en-gb* thunderbird-locale-en-us* tomboy* totem*
  totem-mozilla* totem-plugins* tracker* tracker-extract* tracker-gui*
  tracker-miner-fs* tracker-utils* ubuntu-docs* ubuntu-drivers-common*
  ubuntu-minimal* ubuntu-sso-client* ubuntu-sso-client-qt* ubuntu-standard*
  ubuntu-system-service* ubuntu-tweak* ubuntu-tweak-0* ubuntuone-client*
  ubuntuone-client-gnome* ubuntuone-control-panel* udev* udisks* udisks2* ufw*
  unetbootin* unity* unity-2d-launcher* unity-2d-panel* unity-2d-places*
  unity-2d-shell* unity-2d-spread* unity-greeter* unity-lens-applications*
  unity-lens-photos* unity-scope-gdocs* unity-scope-gdrive*
  unity-webapps-service* unoconv* upower* upstart* ureadahead*
  usb-creator-common* usb-creator-gtk* usbmuxd* util-linux* uuid-runtime*
  vino* wget* wpasupplicant* x11-apps* x11-session-utils* x11-utils*
  x11-xkb-utils* x11-xserver-utils* xdiagnose* xorg* xsane* xscreensaver*
  xscreensaver-data* xscreensaver-gl* xserver-common* xserver-xephyr*
  xserver-xorg* xserver-xorg-core* xserver-xorg-input-evdev*
  xserver-xorg-input-mouse* xserver-xorg-video-nouveau*
  xserver-xorg-video-vesa* xterm* xul-ext-ubufox* yelp* zeitgeist*
  zeitgeist-core* zeitgeist-datahub* zeitgeist-extension-fts* zenity*
The following packages will be upgraded:
  libcups2
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  e2fsprogs libblkid1 (due to e2fsprogs) libuuid1 (due to e2fsprogs)
  util-linux (due to e2fsprogs) hostname upstart (due to hostname) login
  libpam0g (due to login) libpam-runtime (due to login) libpam-modules (due to
  login) mount libmount1 (due to mount)
1 upgraded, 0 newly installed, 532 to remove and 93 not upgraded.
6 not fully installed or removed.
Need to get 0 B/192 kB of archives.
After this operation, 1,453 MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] 

```

---

### Post by dino99 on 2013-01-07
Removing that one is too scary, and probably will really break the system.

If you have deactivated all the ppas, then you get, into synaptic, a list of non genuine packages (under "status" synaptic tab selected in bottom left pane).
There, try to find the package(s) you can downgrade without having to accept the removal of other package(s).
I've often seen the case of only one downgraded package allow then to downgrade the others without trouble. Thats all the joice of that madness cross (recursive) dependencies.

---

### Post by Harry33 on 2013-01-07
There is a problem in Gnome3 Staging PPA now.

The newest gnome-desktop3_3.7.3-0ubuntu1~raring3
changed the name of the package
libgnome-desktop-3-4
to
libgnome-desktop-3-5.

A number of packages (like gnome-control-center, eog, nautilus) depend on libgnome-desktop-3-4.
So all those must be rebuilt before this installation.

---

### Post by VinDSL on 2013-01-07
> **dino99 said:**
> Removing that one is too scary, and probably will really break the system.

If you have deactivated all the ppas, then you get, into synaptic, a list of non genuine packages (under "status" synaptic tab selected in bottom left pane).

There, try to find the package(s) you can downgrade without having to accept the removal of other package(s).

I've often seen the case of only one downgraded package allow then to downgrade the others without trouble. Thats all the joice of that madness cross (recursive) dependencies.
Excellent idea(s)... Thanks!

I have several "half-installed" packages now. I can see these in the error dialogs (in CLI) and my system logs.

However, the "half-installed" libpam package is a deal breaker.  Without a functioning libpam, I cannot install, remove, upgrade or downgrade anything else.  

libpam is the linchpin.  Unless I can fix it, all will be lost.

BTW, there is one libpam component in the GNOME 3 Staging PPA.  That's the reason I'm bring it up in this thread.

I'm NOT declaring this component to be THE problem.  Just saying... ;)

---

### Post by dino99 on 2013-01-07
maybe you need to re-activate that ppa , to get around that libpam issue, to be able to downgrade the other package(s). I cant draw a straight howto, you have to try step by step.

---

### Post by VinDSL on 2013-01-07
> **dino99 said:**
> maybe you need to re-activate that ppa , to get around that libpam issue, to be able to downgrade the other package(s). I cant draw a straight howto, you have to try step by step.
This is a true conundrum -- and also the reason why I love testing.  :)

The original perl problem caused upgraded packages to only be "half-installed" and/or "half-configured" (actual terms from the system logs).

This didn't cause any major problems, until a libpam upgrade was "half-configured".  And, I haven't figured out a workaround yet.

The borked libpam package refuses to allow anything to be installed/removed/reinstalled/purged et cetera -- including itself. Thus, a double-whammy.

It appears to be a rather unique situation, and countless web searches have failed to produce any useful results.

The easy way out would be to simply divorce myself of the situation and do a fresh install, but where's the fun in that?!?!?

I never heard of libpam before it took a dump, and as a consequence of trying to fix it (and perl 5) I've discovered a whole new world of debug tools and methodologies that I didn't even know existed.  It's a learning experience, and experience is the best teacher, or so they say.  So, it's providing me with a quality education -- that's all.  ;)

Anyway, I'll keep chipping away at the mighty oak.

When I've had my fill, I'll dispatch my old install with a belch, and put Humpty Dumpty back together again.  In the meantime, I'm having fun!

---

### Post by Harry33 on 2013-01-08
> **VinDSL said:**
> This is a true conundrum -- and also the reason why I love testing.  :)

The original perl problem caused upgraded packages to only be "half-installed" and/or "half-configured" (actual terms from the system logs).

This didn't cause any major problems, until a libpam upgrade was "half-configured".  And, I haven't figured out a workaround yet.

The borked libpam package refuses to allow anything to be installed/removed/reinstalled/purged et cetera -- including itself. Thus, a double-whammy.

It appears to be a rather unique situation, and countless web searches have failed to produce any useful results.

The easy way out would be to simply divorce myself of the situation and do a fresh install, but where's the fun in that?!?!?

I never heard of libpam before it took a dump, and as a consequence of trying to fix it (and perl 5) I've discovered a whole new world of debug tools and methodologies that I didn't even know existed.  It's a learning experience, and experience is the best teacher, or so they say.  So, it's providing me with a quality education -- that's all.  ;)

Anyway, I'll keep chipping away at the mighty oak.

When I've had my fill, I'll dispatch my old install with a belch, and put Humpty Dumpty back together again.  In the meantime, I'm having fun!

Have you tried to reinstall critical packages by chrooting from a live-USB?

---

### Post by VinDSL on 2013-01-08
> **Harry33 said:**
> Have you tried to reinstall critical packages by chrooting from a live-USB?
No, but that's a good idea!

I burned a live-dvd yesterday.

I'll try that, in a couple of days.

Thanks, Harry!

---

### Post by jbicha on 2013-01-08
> **Harry33 said:**
> There is a problem in Gnome3 Staging PPA now.

The newest gnome-desktop3_3.7.3-0ubuntu1~raring3
changed the name of the package
libgnome-desktop-3-4
to
libgnome-desktop-3-5.

A number of packages (like gnome-control-center, eog, nautilus) depend on libgnome-desktop-3-4.
So all those must be rebuilt before this installation.

Actually, we're not going to rebuild everything against the new version of gnome-desktop3 as that's a lot of work and is rather fragile. (Every time the regular Ubuntu repositories update an affected package, we'd have to rebuild that package in the PPA so things don't break).

I just uploaded a [fix]("https://launchpad.net/ubuntu/+source/gnome-desktop3/3.6.2-0ubuntu5") for this to the regular raring repositories so run this command (in an hour or two, once it's built and published):

```
sudo apt-get install libgnome-desktop-3-4=3.6.2-0ubuntu5
```

I'm not sure that we can (cleanly) automatically fix this for those already using the GNOME3 Staging PPA as they have the 3.7.2 version of that library already installed.

---

### Post by jbicha on 2013-01-08
> **jbicha said:**
> I'm not sure that we can (cleanly) automatically fix this for those already using the GNOME3 Staging PPA as they have the 3.7.2 version of that library already installed.

Never mind. ricotz suggested that we just upload a fixed 3.7.2 version to the GNOME3 PPA (which users of the GNOME3 Staging PPA should also have enabled), which should fix this problem without the need to manually install libgnome-desktop-3-4.

---

### Post by riderplus on 2013-01-08
I used this staging ppa and the Keyboard Layout Indicator came back...finally. However, I'm having issues with the Romanian Layouts, I've already filed a bug [https://bugzilla.gnome.org/show_bug.cgi?id=691290](https://bugzilla.gnome.org/show_bug.cgi?id=691290) but they suspect it's Ubuntu-specific. The trouble is that the "Romanian" layout is the same with "Romanian(standard)", "Romanian(cedilla)", (Romanian(cedilla standard)" and all the other four Romanian layouts. I need "Romanian standard" back, it's a pain in the **** to use the simple "Romanian"  layout (I need to write diacritics with Alt+s or Alt+t and it takes longer when writing documents). When I try to change from "Romanian" to "Romanian(standard)" gnome-shell freezes, I have to log out-log in, I can see it displayed by the Layout Indicator on the top bar (shortcut: "ru", instead of "ro2", as it should have been indexed, before the problems with the Indicator they were displayed "ro1", "ro2", etc., i.e. in previous GNOME versions), but when I press it...it's just the simple Romanian layout, no trace of Romanian Standard. Can you fix this bug once and for all, I beg you!

---

### Post by kansasnoob on 2013-01-08
Hmmm, I'm testing an Ubuntu-GNOME-Remix installed via mini.iso and the only package conflicts I see are:

```
The following packages have been kept back:
  gir1.2-gnomedesktop-3.0 gnome-desktop3-data

```

I guess things get complicated if you have Ubuntu itself installed :D

---

### Post by riderplus on 2013-01-08
```
The following packages have been kept back:
  gdm gir1.2-gnomedesktop-3.0 gnome-desktop3-data

```

What does THIS have to do with the Romanian Keyboard Layout issue?

---

### Post by riderplus on 2013-01-08
...and it's not only the Romanian Layouts that suffer from this bug. When I tried adding Armenian (eastern) BUMP the top bar disappeared, I had to log out and log in, and, of course, the Armenian (eastern) Layout was not working.

---

### Post by zika on 2013-01-08
At least You have + to add layout...
Somewhere here is my post about not being able to add any other layout...
Luckily I was smart enough to add all of them during installation process...

---

### Post by kansasnoob on 2013-01-09
> **riderplus said:**
> ```
The following packages have been kept back:
  gdm gir1.2-gnomedesktop-3.0 gnome-desktop3-data

```

What does THIS have to do with the Romanian Keyboard Layout issue?

Nothing, I was just reflecting on the GNOME3 Staging PPA overall :D

---

### Post by VinDSL on 2013-01-09
> **dino99 said:**
> maybe you need to re-activate that ppa , to get around that libpam issue, to be able to downgrade the other package(s).[...]

> **Harry33 said:**
> Have you tried to reinstall critical packages by chrooting from a live-USB?
You aren't going to believe this...

I've been tied up at (real life) work, this week, and only have a few minutes of idle time here n' there to play around on the computer.

I just got home, updated my Facebook page, and decided to try yet another upgrade, before going to bed.

Guess what?!?!?  The dam broke, and 100's of upgrades came flooding in -- so many, in fact, that I got a warning notification that my root partition was running out of space.  It was almost as if the entire OS was re-installing itself. LoL!  :D

When all was said and done, I performed a cold reboot, and was greeted with a GDM login screen on a beautiful Debian background, instead of the usual monkey vomit LightDM screen.  

Alrighty then...

I'm in GS right now, and everything appears to be back to normal. Flying like the wind, it is!

I initiated an apt-get upgrade in CLI, just to make sure I wasn't dreaming.  

```
vindsl@Zuul:~$ sudo apt-get upgrade
[sudo] password for vindsl: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gir1.2-gnomedesktop-3.0 gnome-desktop3-data gnome-settings-daemon
The following packages will be upgraded:
  nvidia-settings
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 1,813 kB of archives.
After this operation, 13.3 kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
vindsl@Zuul:~$ 

```

Three upgrades are being held-back.

nvidia-settings is listed (which I pinned in Synaptic).

All the perl warnings and fatal libpam errors disappeared.

So, it looks like the assassins have failed again! ):P

Heh!  I'm gonna have to think about this one, for a while...

---

### Post by Harry33 on 2013-01-09
> **kansasnoob said:**
> Hmmm, I'm testing an Ubuntu-GNOME-Remix installed via mini.iso and the only package conflicts I see are:

```
The following packages have been kept back:
  gir1.2-gnomedesktop-3.0 gnome-desktop3-data

```I guess things get complicated if you have Ubuntu itself installed :D

Hi there Kansasnoob,
read the JBicha's comments nro #72 and #73 on this thread.
Also, I reported this issue on my comment before (#66).

So, try here:
[https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=raring](https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=raring)

The build has failed, so we have to wait a bit more.

---

### Post by Harry33 on 2013-01-09
> **VinDSL said:**
> You aren't going to believe this...

I've been tied up at (real life) work, this week, and only have a few minutes of idle time here n' there to play around on the computer.

I just got home, updated my Facebook page, and decided to try yet another upgrade, before going to bed.

Guess what?!?!?  The dam broke, and 100's of upgrades came flooding in -- so many, in fact, that I got a warning notification that my root partition was running out of space.  It was almost as if the entire OS was re-installing itself. LoL!  :D

When all was said and done, I performed a cold reboot, and was greeted with a GDM login screen on a beautiful Debian background, instead of the usual monkey vomit LightDM screen.  

Alrighty then...

I'm in GS right now, and everything appears to be back to normal. Flying like the wind, it is!

I initiated an apt-get upgrade in CLI, just to make sure I wasn't dreaming.  

```
vindsl@Zuul:~$ sudo apt-get upgrade
[sudo] password for vindsl: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gir1.2-gnomedesktop-3.0 gnome-desktop3-data gnome-settings-daemon
The following packages will be upgraded:
  nvidia-settings
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 1,813 kB of archives.
After this operation, 13.3 kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
vindsl@Zuul:~$ 

```Three upgrades are being held-back.

nvidia-settings is listed (which I pinned in Synaptic).

All the perl warnings and fatal libpam errors disappeared.

So, it looks like the assassins have failed again! ):P

Heh!  I'm gonna have to think about this one, for a while...

Fine,
However, do not try to upgrade Gnome-desktop3 packages from this Gnome3 Staging PPA.
Instead, get them from Gnome3 PPA (raring branch).
Here:
[https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=raring](https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=raring)

The build has failed, so we have to wait a bit more.

---

### Post by kansasnoob on 2013-01-09
> **Harry33 said:**
> Hi there Kansasnoob,
read the JBicha's comments nro #72 and #73 on this thread.
Also, I reported this issue on my comment before (#66).

So, try here:
[https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=raring](https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=raring)

The build has failed, so we have to wait a bit more.

It's all cool, I'm up to 3 held packages ATM:

```
The following packages have been kept back:
  gir1.2-gnomedesktop-3.0 gnome-desktop3-data gnome-settings-daemon

```

But nothings actually blown up yet :D

For being between what would normally be alpha 1 and alpha 2 I like what I see so far, I just wish I had a time machine so I could see GNOME 3.8 circa April :lolflag:

---

### Post by kyleabaker on 2013-01-09
> **kansasnoob said:**
> For being between what would normally be alpha 1 and alpha 2 I like what I see so far, I just wish I had a time machine so I could see GNOME 3.8 circa April :lolflag:

+"me"

:p

---

### Post by Harry33 on 2013-01-09
> **kansasnoob said:**
> It's all cool, I'm up to 3 held packages ATM:

```
The following packages have been kept back:
  gir1.2-gnomedesktop-3.0 gnome-desktop3-data gnome-settings-daemon

```But nothings actually blown up yet :D

For being between what would normally be alpha 1 and alpha 2 I like what I see so far, I just wish I had a time machine so I could see GNOME 3.8 circa April :lolflag:
Right,
The Gnome3 PPA build of gnome-desktop3 (3.7.2-0ubuntu1~raring3) is OK now and soon uploaded into that PPA repository.
So, after installing this packgage, it should be possible to retain the package libgnome-desktop-3-4 and still have the new libgnome-desktop-3-5 (from Gnome3 Staging PPA) installed (parallel installation).
This way other packages will not break.

---

### Post by kansasnoob on 2013-01-09
Something sort of odd to me :confused:

I was just fiddling with synaptic to parse what I had installed (having a bit of trouble playing an mp4) but don't worry about that ;)

The thing is you can see from this screenshot that I do have both the GNOME3 standard PPA and staging PPA installed, but only staging shows up in "origins":

[ATTACH]229781[/ATTACH]

Maybe it's just because there's only one package available from the standard PPA and it's being rebuilt?

But I also did this as an exercise to see if things played "hide-n-seek" like they sometimes do in Unity, and NO they don't :D

---

### Post by riderplus on 2013-01-09
I get this:```
The following packages have been kept back:
  gdm
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```
I can't upgrade gdm, it says "broken package". First it required libaudit1 and there was in no repo to download.

---

### Post by Harry33 on 2013-01-09
> **riderplus said:**
> I get this:```
The following packages have been kept back:
  gdm
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```I can't upgrade gdm, it says "broken package". First it required libaudit1 and there was in no repo to download.

Package libaudit1 seems to be in universe.
Try to enable that first.

---

### Post by riderplus on 2013-01-09
Has this problem been solved:


I used this staging ppa and the Keyboard Layout Indicator came  back...finally. However, I'm having issues with the Romanian Layouts,  I've already filed a bug [https://bugzilla.gnome.org/show_bug.cgi?id=691290](https://bugzilla.gnome.org/show_bug.cgi?id=691290)  but they suspect it's Ubuntu-specific. The trouble is that the  "Romanian" layout is the same with "Romanian(standard)",  "Romanian(cedilla)", (Romanian(cedilla standard)" and all the other four  Romanian layouts. I need "Romanian standard" back, it's a pain in the  **** to use the simple "Romanian"  layout (I need to write diacritics  with Alt+s or Alt+t and it takes longer when writing documents). When I  try to change from "Romanian" to "Romanian(standard)" gnome-shell  freezes, I have to log out-log in, I can see it displayed by the Layout  Indicator on the top bar (shortcut: "ru", instead of "ro2", as it should  have been indexed, before the problems with the Indicator they were  displayed "ro1", "ro2", etc., i.e. in previous GNOME versions), but when  I press it...it's just the simple Romanian layout, no trace of Romanian  Standard. Can you fix this bug once and for all, I beg you!

???

---

### Post by riderplus on 2013-01-09
NO, it has not been solved yet...I promise I will get drunk when it will be solved.

---

### Post by zika on 2013-01-09
> **riderplus said:**
> NO, it has not been solved yet...I promise I will get drunk when it will be solved.
In 10 minutes...? ;)

---

### Post by riderplus on 2013-01-09
So fast? Well, I'm optimistic about it, but...10 minutes...No, I don't think so. Only if you're fixing it :)

---

### Post by zika on 2013-01-09
> **riderplus said:**
> Has this problem been solved:


I used this staging ppa and the Keyboard Layout Indicator came  back...finally. However, I'm having issues with the Romanian Layouts,  I've already filed a bug [https://bugzilla.gnome.org/show_bug.cgi?id=691290](https://bugzilla.gnome.org/show_bug.cgi?id=691290)  but they suspect it's Ubuntu-specific. The trouble is that the  "Romanian" layout is the same with "Romanian(standard)",  "Romanian(cedilla)", (Romanian(cedilla standard)" and all the other four  Romanian layouts. I need "Romanian standard" back, it's a pain in the  **** to use the simple "Romanian"  layout (I need to write diacritics  with Alt+s or Alt+t and it takes longer when writing documents). When I  try to change from "Romanian" to "Romanian(standard)" gnome-shell  freezes, I have to log out-log in, I can see it displayed by the Layout  Indicator on the top bar (shortcut: "ru", instead of "ro2", as it should  have been indexed, before the problems with the Indicator they were  displayed "ro1", "ro2", etc., i.e. in previous GNOME versions), but when  I press it...it's just the simple Romanian layout, no trace of Romanian  Standard. Can you fix this bug once and for all, I beg you!

???

> **riderplus said:**
> NO, it has not been solved yet...I promise I will get drunk when it will be solved.

> **riderplus said:**
> So fast? Well, I'm optimistic about it, but...10 minutes...No, I don't think so. Only if you're fixing it :)

I was just counting minutes between You successive posts about the same problem... ):P

---

### Post by riderplus on 2013-01-09
Sorry but it seems just totally freaking out not to see this issue fixed once and for all. That's why I was so insistent.

---

### Post by dino99 on 2013-01-09
> **riderplus said:**
> Sorry but it seems just totally freaking out not to see this issue fixed once and for all. That's why I was so insistent.

insistent ? Have you sent a message to the dev ?
Or maybe you can collaborate with him to fix it ?

You know, here its a forum, and devs are rarely reading our prose here.

---

### Post by riderplus on 2013-01-09
> **dino99 said:**
> insistent ? Have you sent a message to the dev ?
Or maybe you can collaborate with him to fix it ?

You know, here its a forum, and devs are rarely reading our prose here.


YES, I did, and there was NO action taken so far! 
Please see [https://bugzilla.gnome.org/show_bug.cgi?id=691290](https://bugzilla.gnome.org/show_bug.cgi?id=691290) and [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1096901](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1096901)

Nobody wants to be assigned to the launchpad bug. Where are the developers, by the way?

---

### Post by zika on 2013-01-09
> **riderplus said:**
> YES, I did, and there was NO action taken so far! 
Please see [https://bugzilla.gnome.org/show_bug.cgi?id=691290](https://bugzilla.gnome.org/show_bug.cgi?id=691290) and [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1096901](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1096901)

Nobody wants to be assigned to the launchpad bug. Where are the developers, by the way?
As far as I can see, You've got initial answer and error is hard to reproduce...
That happened day before yesterday... I myself have bugs that are months old...
You think that this is the proper place to intensify the pressure?
Developers are kept at the safe place...

---

### Post by kansasnoob on 2013-01-09
I see 'libgnome-desktop-3-4' must've built properly now :D

All updated and running.

---

### Post by riderplus on 2013-01-09
> **zika said:**
> As far as I can see, You've got initial answer and error is hard to reproduce...
That happened day before yesterday... I myself have bugs that are months old...
You think that this is the proper place to intensify the pressure?
Developers are kept at the safe place...

I disagree that the error is hard to reproduce. You can try yourself (if you're using the staging ppa and 13.04 raring Ubuntu) to add for instance Romanian (cedilla) or Armenian (eastern) and see what happens. It's not hard to reproduce at all. It's just difficult to fix, that's the problem. I think the developers should care more about regressive bugs like this one than about "improvements". How can one improve something when one is confronted with regressiveness? This shouldn't have been an issue in 12.10. I expect improvements from the developers, not regressiveness.

---

### Post by VinDSL on 2013-01-09
> **Harry33 said:**
> Fine,
However, do not try to upgrade Gnome-desktop3 packages from this Gnome3 Staging PPA.
Instead, get them from Gnome3 PPA (raring branch).
Here:
[https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=raring](https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=raring)
Thanks!

> **kansasnoob said:**
> All updated and running.
Dittos!

**EDIT**

w00t! Just (successfully) installed Linux 3.8-rc2!

I'm back in the saddle again...  ;)

---

### Post by VinDSL on 2013-01-09
Man, I don't *know* what happened (maybe it was the QT4 upgrades), but...

This display is sharp as a tack, now!  Chrystal clear opacity, fonts never looked better or more readable, blah, blah, blah.

Unity even looks good.

Think I'll go try LXDE...

**EDIT**

Yep, LXDE looks foxy, too!

Still have a nagging problem with lxsession (need to stop it during the session 'cause it uses 100% CPU), but the display looks shockingly good!

Hrm...

Anyway, back to GS, and back on topic.  :)

---

### Post by Harry33 on 2013-01-10
> **VinDSL said:**
> Thanks!


Dittos!

**EDIT**

w00t! Just (successfully) installed Linux 3.8-rc2!

I'm back in the saddle again...  ;)

Linux 3.8-rc3 is already there.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-rc3-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-rc3-raring/)

---

### Post by zika on 2013-01-10
> **riderplus said:**
> I disagree that the error is hard to reproduce. You can try yourself (if you're using the staging ppa and 13.04 raring Ubuntu) to add for instance Romanian (cedilla) or Armenian (eastern) and see what happens. It's not hard to reproduce at all. It's just difficult to fix, that's the problem. I think the developers should care more about regressive bugs like this one than about "improvements". How can one improve something when one is confronted with regressiveness? This shouldn't have been an issue in 12.10. I expect improvements from the developers, not regressiveness.I'm just writting that You're ranting on wrong people... ):P

---

### Post by kansasnoob on 2013-01-10
> **VinDSL said:**
> Man, I don't *know* what happened (maybe it was the QT4 upgrades), but...

This display is sharp as a tack, now!  Chrystal clear opacity, fonts never looked better or more readable, blah, blah, blah.

Unity even looks good.

Think I'll go try LXDE...

**EDIT**

Yep, LXDE looks foxy, too!

Still have a nagging problem with lxsession (need to stop it during the session 'cause it uses 100% CPU), but the display looks shockingly good!

Hrm...

Anyway, back to GS, and back on topic.  :)

Yeah, things are downright flashy. With the exception of gdm things are very snappy too ....... no waiting for dash or most apps to open, it's just da' bomb :D

---

### Post by VinDSL on 2013-01-10
> **Harry33 said:**
> Linux 3.8-rc3 is already there.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-rc3-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-rc3-raring/)
Good!  I'll install that tonight.

Previous attempts to install 3.8-rc2 resulted in failure, with all of the libpam/perl issues I was experiencing.

I expect 3.8-rc3 will install just fine, now that these probs have magically disappeared.

---

### Post by Cavsfan on 2013-01-10
> **Harry33 said:**
> Fine,
However, do not try to upgrade Gnome-desktop3 packages from this Gnome3 Staging PPA.
Instead, get them from Gnome3 PPA (raring branch).
Here:
[https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=raring](https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=raring)

The build has failed, so we have to wait a bit more.

I had gotten a bit frustrated with this GS stuff and purged the PPAs both gnome3-staging and the ricotz/testing one.

I just added the one above and got updates and nothing really changed. 
Am I missing something? Do I need to add another PPA or tweak it or what?

---

### Post by Cavsfan on 2013-01-10
OK, I am getting a tad better at this. I installed the icons, and themes but, am wondering why there is no Shell Theme in Tweak tools.
And why is so many things dark like my cairo dock. Many of the items as you can see are black.
My cursor is on Gedit in the dock and you can see what it looks like.
But over all this is pretty cool! :D

Is it because of the missing Shell theme in Gnome Tweak tools?

And also do we report bugs caused by using this ppa? I had that happen a while ago and didn't know if I should report it or not. 

[[IMG]http://ompldr.org/taDB1Yw[/IMG]]("http://ompldr.org/vaDB1Yw")

---

### Post by VinDSL on 2013-01-10
> **Cavsfan said:**
> Am I missing something?
Did you install this?

[INDENT][https://extensions.gnome.org/extension/19/user-themes/](https://extensions.gnome.org/extension/19/user-themes/)[/INDENT]

---

### Post by VinDSL on 2013-01-10
> **VinDSL said:**
> I expect 3.8-rc3 will install just fine [...]
w00t!  This thing is flying, again, with 3.8-rc3!

I still can't figure out what borked this machine, or what fixed it.  LoL!  :D

Oh, well, bring on the breakage...

---

### Post by Harry33 on 2013-01-11
> **Cavsfan said:**
> I had gotten a bit frustrated with this GS stuff and purged the PPAs both gnome3-staging and the ricotz/testing one.

I just added the one above and got updates and nothing really changed. 
Am I missing something? Do I need to add another PPA or tweak it or what?

ATM, if you have all the packages installed from the Gnome3 Staging PPA, you do not need another PPA to be enabled.

---

### Post by Harry33 on 2013-01-11
> **VinDSL said:**
> w00t!  This thing is flying, again, with 3.8-rc3!

I still can't figure out what borked this machine, or what fixed it.  LoL!  :D

Oh, well, bring on the breakage...

The 3.8 rc3 is in the Raring repo too now.

Here:
[https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-0.2](https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-0.2)

---

### Post by VinDSL on 2013-01-11
> **Harry33 said:**
> The 3.8 rc3 is in the Raring repo too now.

Here:
[https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-0.2](https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-0.2)
~Cool

I'll install that tonight.

It's somewhat easier to get rid of stale kernels installed through the official PPA, than local installs, e.g. Ubu Tweak vs apt-get.

Plus, it's fun to see which patches the devs have applied.

Thanks!

---

### Post by Cavsfan on 2013-01-11
> **Harry33 said:**
> ATM, if you have all the packages installed from the Gnome3 Staging PPA, you do not need another PPA to be enabled.

Thanks for that info! What about reporting bugs? Do we still do that with this stuff?

---

### Post by riderplus on 2013-01-11
I did a fresh install of Ubuntu 13.04, then installed gnome-shell and gdm, then added the GNOME 3 team PPA and upgraded. Surprise! The Keyboard Layout Indicator is missing. Surreal!

---

### Post by Cavsfan on 2013-01-14
Everything seems to running pretty smooth in GS. 
But I could not see a lot of stuff with the GnomishDark theme and the ACYL_Icon_Theme_0.9.4 seemed too dark also, so I installed icon theme Buuf3.2, changed the gtk-theme to Radience and I likes it. :D

[[img]http://ompldr.org/taDJtOA[/img]](http://ompldr.org/vaDJtOA)

---

### Post by serdotlinecho on 2013-01-18
Search in dash is laggy and slow.

[http://youtu.be/d8HxhGZD-E4](http://youtu.be/d8HxhGZD-E4)

---

### Post by VinDSL on 2013-01-25
Working great, here...


[INDENT]**[COLOR="DarkRed"]Ubu 13.04 / Gnome-Shell 3.7.4.1 (Staging) / Linux 3.8-rc4 / Chromium 26 (Canary) / Conky 1.9.0 / Plank[/COLOR]**

[[IMG]http://vindsl.com/images/vindsl-desktop-25-jan-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-25-jan-2013-1.png")[/INDENT]

---

### Post by hugmenot on 2013-01-26
I am deeply saddened to see that they removed the ARGB visual on Gnome Terminal and now I can only get an opaque background in gnome-terminal.

Why?

---

### Post by kansasnoob on 2013-01-26
I'm running an Ubuntu-GNOME-Remix installed via mini.iso with both GNOME PPA's and for a few days 'gnome-tweak-tool' fails to launch. Anyone else seen that?

---

### Post by Cavsfan on 2013-01-26
> **kansasnoob said:**
> I'm running an Ubuntu-GNOME-Remix installed via mini.iso with both GNOME PPA's and for a few days 'gnome-tweak-tool' fails to launch. Anyone else seen that?

I did a clean install from the daily iso yesterday and when I added this PPA, gnome-tweak-tool, Firefox and many other things failed to launch.
It would just say "starting firefox" or whatever in the bottom panel and then disappear.
I had to purge it.

---

### Post by jbicha on 2013-01-26
> **kansasnoob said:**
> I'm running an Ubuntu-GNOME-Remix installed via mini.iso with both GNOME PPA's and for a few days 'gnome-tweak-tool' fails to launch. Anyone else seen that?

Yes, gnome-tweak-tool 3.7.4 crashes if gnome-shell isn't running which is a regression. Any volunteers to file the bug?

As of right now, the staging PPA causes several regressions if you use Unity.

---

### Post by mc4man on 2013-01-26
> **hugmenot said:**
> I am deeply saddened to see that they removed the ARGB visual on Gnome Terminal and now I can only get an opaque background in gnome-terminal.

Why?
I think that all was gone some time ago  with gnome-terminal-3.7.0, why? - because someone thought it was a good idea

---

### Post by mc4man on 2013-01-26
Seems quite broken here on a build-script iso install)built last week
1st. python3-pycurl wasn't installed, after that always fails on  - 
"Cannot access PPA blah, blah"
Ex.
> $ sudo add-apt-repository ppa:ricotz/docky[sudo] password for doug: 
Cannot access PPA ([https://launchpad.net/api/1.0/~ricotz/+archive/docky](https://launchpad.net/api/1.0/~ricotz/+archive/docky)) to get PPA information, please check your internet connection.


---

### Post by mc4man on 2013-01-26
at least here on Ubuntu GNOME Remix  iso install with staging ppa those windows always open very small. If re-sized, closed & re-opened go back to small size

---

### Post by mc4man on 2013-01-26
If set to "never" in "Turn screen off when inactive" after closing is reset to 1 min.
Other specific times are ok.
screens show setting to never & after re-opening

---

### Post by kansasnoob on 2013-01-26
> **jbicha said:**
> Yes, gnome-tweak-tool 3.7.4 crashes if gnome-shell isn't running which is a regression. Any volunteers to file the bug?

As of right now, the staging PPA causes several regressions if you use Unity.

At this point I think I'm too stupid to file a bug report regarding this ;)

Remember I'm using a pretty much clean "ubuntu-gnome-desktop" by using the mini.iso and installing "gnome-shell" followed by "ubuntu-gnome-desktop", but I did still have "gnome-session-fallback" installed :(

Then I purged it:

```
Start-Date: 2013-01-26  16:05:18
Commandline: /usr/sbin/synaptic
Purge: gnome-session-fallback:i386 (3.7.3-0ubuntu1~raring3)
End-Date: 2013-01-26  16:05:24

Start-Date: 2013-01-26  16:07:16
Commandline: apt-get autoremove
Remove: python3-oneconf:i386 (0.3.3), linux-headers-3.8.0-0:i386 (3.8.0-0.3), oneconf:i386 (0.3.3), python3-crypto:i386 (2.6-3), alacarte:i386 (3.7.3-0ubuntu1~raring1), linux-image-3.8.0-0-generic:i386 (3.8.0-0.3), python3-oauthlib:i386 (0.3.4-0ubuntu1), linux-image-extra-3.8.0-0-generic:i386 (3.8.0-0.3), python3-httplib2:i386 (0.7.7-1), python3-piston-mini-client:i386 (0.7.3+bzr68-0ubuntu1), linux-headers-3.8.0-0-generic:i386 (3.8.0-0.3), gnome-applets:i386 (3.5.92-0ubuntu1), gnome-panel:i386 (3.6.2-0ubuntu3), gnome-applets-data:i386 (3.5.92-0ubuntu1), gir1.2-panelapplet-4.0:i386 (3.6.2-0ubuntu3), gnome-panel-data:i386 (3.6.2-0ubuntu3)
End-Date: 2013-01-26  16:07:57
```

Now "tweak" is working properly :D

Just to be clear; "tweak" was NOT working properly even if I were logged into a standard gnome session as long as the old fallback session was installed. So maybe we need to "purge" that when upgrading from gnome version 3.6* to version 3.7* :confused:

I haven't tried an actual Ubuntu install + our GNOME remix at all in Raring because I simply detest Compiz + llvmpipe.

---

### Post by mc4man on 2013-01-26
> **jbicha said:**
> Yes, gnome-tweak-tool 3.7.4 crashes if gnome-shell isn't running which is a regression. Any volunteers to file the bug?

As of right now, the staging PPA causes several regressions if you use Unity.
The current g-t-t (3.7.4-0ubuntu1~raring1) in a unity only install doesn't crash here at all. Does produce a number of "GError"..." but none are fatal & the tools does whatever it can do on a unity install.

Ex. in attached

---

### Post by jbicha on 2013-01-26
> **mc4man said:**
> I think that all was gone some time ago  with gnome-terminal-3.7.0, why? - because someone thought it was a good idea

The patch to enable a translucent purple terminal by default (if you're using Ambiance or Radiance) was commented out a year ago because it no longer applied cleanly. I took a look at it tonight and got it working again for regular raring (3.6).

I also looked at doing the same for 3.7 but I noticed that the Background tab in Profile Preferences went missing. I filed a [bug]("https://bugzilla.gnome.org/692609") and I'll wait until that gets resolved before continuing to port the patch to 3.7.

The 'filechooser too small' bug is in GTK. We should look at backporting the fix to the staging PPA (some day GNOME developers will test their development release tarballs and make a new release when they break stuff…)

---

### Post by kansasnoob on 2013-01-27
There appear to be some rather serious dependency problems with my "pure-ish" Ubuntu-GNOME install. I wondered if 'gnome-tweak-tool' would break again if I installed another WM or DE, and the lightest thing I could think of was 'lubuntu-core' ---- NOT good:

```
lance@lance-desktop:~$ sudo apt-get install lubuntu-core
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  appmenu-gtk appmenu-gtk3 appmenu-qt avahi-utils bamfdaemon compiz
  compiz-core compiz-gnome compiz-plugins-default elementary-icon-theme
  freerdp-x11 geoclue geoclue-ubuntu-geoip gir1.2-gdata-0.0 gir1.2-goa-1.0
  gnome-control-center-unity gtk2-engines gtk3-engines-unico indicator-appmenu
  indicator-datetime indicator-power indicator-printers libbamf3-1
  libcompizconfig0 libdbusmenu-qt2 libdecoration0 libfm-data libfm-gtk-bin
  libfm-gtk-data libfm-gtk3 libfm3 libfreerdp-plugins-standard libfreerdp1
  libglade2-0 libglew1.8 libglewmx1.8 libid3tag0 libimlib2
  liblightdm-gobject-1-0 libmenu-cache2 libnux-4.0-0 libnux-4.0-common
  libobrender27 libobt0 libpackagekit-glib2-14 libpam-freerdp libprotobuf7
  libtimezonemap1 libunity-core-6.0-5 libunity-misc4 libunity-webapps0
  libwnck-common libwnck22 lightdm lightdm-gtk-greeter
  lightdm-remote-session-freerdp lightdm-remote-session-uccsconfigure
  lubuntu-artwork lubuntu-artwork-13-04 lubuntu-default-settings
  lubuntu-icon-theme lubuntu-lxpanel-icons lxmenu-data lxpanel lxsession
  lxsession-data lxshortcut nux-tools obconf openbox openbox-themes pcmanfm
  plymouth-theme-lubuntu-logo plymouth-theme-lubuntu-text python-cupshelpers
  python-gconf python-gnomekeyring python-pycurl python-smbc python3-crypto
  python3-httplib2 python3-oauthlib python3-pycurl remote-login-service
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev thin-client-config-agent unity unity-asset-pool
  unity-common unity-greeter unity-lens-applications unity-lens-files
  unity-lens-music unity-lens-photos unity-lens-shopping unity-lens-video
  unity-scope-gdocs unity-scope-gdrive unity-scope-musicstores
  unity-scope-video-remote unity-services unity-webapps-service
Suggested packages:
  gnome-exe-thumbnailer glew-utils amixer scrot galculator xscreensaver
  gpicview lxde-common menu ttf-dejavu libxml2-dev python-gnome2-doc
  libcurl4-gnutls-dev python-pycurl-dbg python3-crypto-dbg python-crypto-doc
  python3-pycurl-dbg
Recommended packages:
  hud
The following NEW packages will be installed:
  appmenu-gtk appmenu-gtk3 appmenu-qt avahi-utils bamfdaemon compiz
  compiz-core compiz-gnome compiz-plugins-default elementary-icon-theme
  freerdp-x11 geoclue geoclue-ubuntu-geoip gir1.2-gdata-0.0 gir1.2-goa-1.0
  gnome-control-center-unity gtk2-engines gtk3-engines-unico indicator-appmenu
  indicator-datetime indicator-power indicator-printers libbamf3-1
  libcompizconfig0 libdbusmenu-qt2 libdecoration0 libfm-data libfm-gtk-bin
  libfm-gtk-data libfm-gtk3 libfm3 libfreerdp-plugins-standard libfreerdp1
  libglade2-0 libglew1.8 libglewmx1.8 libid3tag0 libimlib2
  liblightdm-gobject-1-0 libmenu-cache2 libnux-4.0-0 libnux-4.0-common
  libobrender27 libobt0 libpackagekit-glib2-14 libpam-freerdp libprotobuf7
  libtimezonemap1 libunity-core-6.0-5 libunity-misc4 libunity-webapps0
  libwnck-common libwnck22 lightdm lightdm-gtk-greeter
  lightdm-remote-session-freerdp lightdm-remote-session-uccsconfigure
  lubuntu-artwork lubuntu-artwork-13-04 lubuntu-core lubuntu-default-settings
  lubuntu-icon-theme lubuntu-lxpanel-icons lxmenu-data lxpanel lxsession
  lxsession-data lxshortcut nux-tools obconf openbox openbox-themes pcmanfm
  plymouth-theme-lubuntu-logo plymouth-theme-lubuntu-text python-cupshelpers
  python-gconf python-gnomekeyring python-pycurl python-smbc python3-crypto
  python3-httplib2 python3-oauthlib python3-pycurl remote-login-service
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev thin-client-config-agent unity unity-asset-pool
  unity-common unity-greeter unity-lens-applications unity-lens-files
  unity-lens-music unity-lens-photos unity-lens-shopping unity-lens-video
  unity-scope-gdocs unity-scope-gdrive unity-scope-musicstores
  unity-scope-video-remote unity-services unity-webapps-service
0 upgraded, 105 newly installed, 0 to remove and 1 not upgraded.
Need to get 17.1 MB/17.1 MB of archives.
After this operation, 95.7 MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

Why would installing 'lubuntu-core' want to install compiz and unity?

But the plot thickens, installing the unbranded 'lxde-core' looks right:

```
lance@lance-desktop:~$ sudo apt-get install lxde-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libfm-data libfm-gtk-bin libfm-gtk-data libfm-gtk3 libfm3 libglade2-0
  libid3tag0 libimlib2 libjpeg-progs libjpeg-turbo-progs libmenu-cache2
  libobrender27 libobt0 libwnck-common libwnck22 lxde-common lxmenu-data
  lxpanel lxsession lxsession-data lxshortcut obconf openbox openbox-themes
  pcmanfm xscreensaver xscreensaver-data
Suggested packages:
  gnome-exe-thumbnailer lxlauncher gpicview menu ttf-dejavu libxml2-dev
  xfishtank xdaliclock xscreensaver-gl fortune qcam streamer gdm3
  kdm-gdmcompat
The following NEW packages will be installed:
  libfm-data libfm-gtk-bin libfm-gtk-data libfm-gtk3 libfm3 libglade2-0
  libid3tag0 libimlib2 libjpeg-progs libjpeg-turbo-progs libmenu-cache2
  libobrender27 libobt0 libwnck-common libwnck22 lxde-common lxde-core
  lxmenu-data lxpanel lxsession lxsession-data lxshortcut obconf openbox
  openbox-themes pcmanfm xscreensaver xscreensaver-data
0 upgraded, 28 newly installed, 0 to remove and 1 not upgraded.
Need to get 4,131 kB of archives.
After this operation, 21.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

So maybe it's an Lubuntu dependency problem :confused:

I've done just enough cross-testing to be certain that **this is NOT related in any way to either the GNOME3 PPA or the staging PPA**.

---

### Post by hugmenot on 2013-01-27
> **jbicha said:**
> I also looked at doing the same for 3.7 but I noticed that the Background tab in Profile Preferences went missing. I filed a [bug]("https://bugzilla.gnome.org/692609") and I'll wait until that gets resolved before continuing to port the patch to 3.7.

I told this Christian Persch guy already two years ago to please not remove ARGB visual from gnome-terminal.

He told me they want to simplify the dialog and the image background was problematic and caused some bugs.

The transparency went away in the same stroke even though the two things are independent.

I wrote him and he said that transparency could come back but he doesn’t see a good reason why transparency is necessary.

I wrote him to explain why I like it. Now a year later 3.7.1 comes out with transparency and ARGB visual removed. There’s no mention of this in the NEWS file and the commits in which this was removed are a confusung grab bag of unrelated changes, no good commit message and certainly not atomic.

So I wrote him why he didn’t listen to my suggestion to enable gtk_color_chooser_set_use_alpha()  in the background color dialog and then to put argb visual back in.

No more replies, he doesn’t want to discuss, apparently.

---

### Post by hugmenot on 2013-01-27
```


On Sa, 2013-01-26 at 11:56 +0100, Christian Persch wrote:
> > 
> > I’m pinning g-t to back to 3.6 now. But again, please don’t force
> > opaque background only because you wanted to get rid of a slider in
> > the dialog. Just enable gtk_color_chooser_set_use_alpha() and use the
> > rgba color.
> 
> Please see https://live.gnome.org/Terminal/FAQ for a way to enable
> transparency for terminals (and indeed *any* application's windows).
> All you need to run is a compositing window manager, which AFAIK
> ubuntu's «unity» is.

```

FYI the FAQ is a joke. The setting makes the whole window transparent, not only the background color.

---

### Post by zika on 2013-01-28
RR install fully up-to-date with GS PPAs...
Every atempt to use```
sudo service networking restart
```brings GS (GDM, either vanilla or Fallback) to its knees and very hard to recover without reboot... It makes it go in low resolution graphics mode, etc... Am I alone?
LightDM falls to its knees after this service call a bit more graciously, but, still, it falls...

---

### Post by Cavsfan on 2013-01-28
Deleted.

---

### Post by jbicha on 2013-01-28
> **mc4man said:**
> at least here on Ubuntu GNOME Remix  iso install with staging ppa those windows always open very small. If re-sized, closed & re-opened go back to small size

The filechooser bug has now been fixed (thanks ricotz for packaging a newer GTK git snapshot). There's actually a new feature that came along with the bug: the filechooser popup now remembers its size! Unfortunately it remembers the very small size for those of us who were using the broken GTK this past week. After logging out and logging back in, you can either resize it to where you like or run these commands to start with the default:
```

gsettings reset org.gtk.Settings.FileChooser window-size
gsettings reset org.gtk.Settings.FileChooser window-position

```

This also fixes a [bug]("https://bugzilla.gnome.org/show_bug.cgi?id=692571") where System Settings would display off-center when run outside of GNOME Shell.

---

### Post by Cavsfan on 2013-01-28
Deleted.

---

### Post by VinDSL on 2013-01-28
> **jbicha said:**
> The filechooser bug has now been fixed (thanks ricotz for packaging a newer GTK git snapshot). There's actually a new feature that came along with the bug: the filechooser popup now remembers its size!

```

gsettings reset org.gtk.Settings.FileChooser window-size
gsettings reset org.gtk.Settings.FileChooser window-position

```
w00t!  Works!

Thanks!  ;)

---

### Post by VinDSL on 2013-01-28
> **zika said:**
> RR install fully up-to-date with GS PPAs...
Every attempt to use```
sudo service networking restart
```brings GS (GDM, either vanilla or Fallback) to its knees and very hard to recover without reboot... It makes it go in low resolution graphics mode, etc... Am I alone?
Same results(s) here, zika (GDM)!

The wheel is still spinning, but the hamster is dead...  LoL!  :D

---

### Post by VinDSL on 2013-01-31
Heh!  Finally got rid of the Time & Date, in the panel.


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-31-jan-2013-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-31-jan-2013-2.png")[/INDENT]


Don't know why I waited so long -- been bugging me forever...

---

### Post by Harry33 on 2013-02-01
> **VinDSL said:**
> Heh!  Finally got rid of the Time & Date, in the panel.
Don't know why I waited so long -- been bugging me forever...

Well at first I thought when you said "Finally got rid of ..." that you meant
"I do not know what happened, but now it is gone". :D

Anyway, how did you do it?

---

### Post by VinDSL on 2013-02-01
> **Harry33 said:**
> Anyway, how did you do it?
Hi Harry,

Well, there are different ways of doing it, but the fastest (and most easily reversible) way is:

```
gksudo gedit /usr/share/gnome-shell/js/ui/panel.js

```

Simply comment out line 921...

```
const PANEL_ITEM_IMPLEMENTATIONS = {
    'activities': ActivitiesButton,
    'appMenu': AppMenuButton,
**[COLOR="Blue"]    //'dateMenu': imports.ui.dateMenu.DateMenuButton,[/COLOR]**
    'a11y': imports.ui.status.accessibility.ATIndicator,
    'volume': imports.ui.status.volume.Indicator,
    'battery': imports.ui.status.power.Indicator,
    'lockScreen': imports.ui.status.lockScreenMenu.Indicator,
    'logo': imports.gdm.loginDialog.LogoMenuButton,
    'keyboard': imports.ui.status.keyboard.InputSourceIndicator,
    'powerMenu': imports.gdm.powerMenu.PowerMenuButton,
    'userMenu': imports.ui.userMenu.UserMenuButton
};
```

Save & Restart

That's it...  ;)

---

### Post by hugmenot on 2013-02-01
[This commit]("http://git.gnome.org/browse/gnome-settings-daemon/commit/?id=b69b0d99fdc5319a809299146d281cfd06bf82e9") is also really stupid.

They bind the F2 key to mute the microphone, and write in the commit message they want to bind F20 for testing. But what they actually bound was F2, so now one cannot use F2 anymore.

---

### Post by Harry33 on 2013-02-01
> **hugmenot said:**
> [This commit]("http://git.gnome.org/browse/gnome-settings-daemon/commit/?id=b69b0d99fdc5319a809299146d281cfd06bf82e9") is also really stupid.

They bind the F2 key to mute the microphone, and write in the commit message they want to bind F20 for testing. But what they actually bound was F2, so now one cannot use F2 anymore.

+1

That one really bothers me. I need the F2 key for smoother working.

---

### Post by zika on 2013-02-02
gnome-control-center gnome-control-center-data are being kept back for quite some time...
Sort of I need gnome-control-center... ;)

---

### Post by Harry33 on 2013-02-02
> **zika said:**
> gnome-control-center gnome-control-center-data are being kept back for quite some time...
Sort of I need gnome-control-center... ;)

What version of gnome-control-center are you talking about?
Is it 3.7.4-0ubuntu1 ?

---

### Post by zika on 2013-02-02
> **Harry33 said:**
> What version of gnome-control-center are you talking about?
Is it 3.7.4-0ubuntu1 ?
Yes...
```
:~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gnome-control-center gnome-control-center-data
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
:~$ sudo aptitude full-upgrade 
The following packages will be upgraded: 
  gnome-control-center{b} gnome-control-center-data 
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,528 kB of archives. After unpacking 10.2 MB will be used.
The following packages have unmet dependencies:
 gnome-control-center : Depends: gnome-icon-theme (>= 3.7.4) but 3.7.3+git20121224.2af6b37d-0ubuntu1~13.04~ricotz0 is installed.
The following actions will resolve these dependencies:

      Remove the following packages:                                    
1)      gnome-control-center                                            
2)      gnome-control-center-signon                                     
3)      gnome-control-center-unity                                      
4)      indicator-datetime                                              
5)      indicator-power                                                 
6)      ubuntu-desktop                                                  

      Leave the following dependencies unresolved:                      
7)      gnome-bluetooth recommends gnome-control-center                 
8)      gnome-media recommends gnome-control-center                     
9)      gnome-online-accounts recommends gnome-control-center (>= 3.6.1)
10)     libaccount-plugin-1.0-0 recommends gnome-control-center-signon  
11)     mcp-account-manager-uoa recommends gnome-control-center-signon  
12)     unity-greeter recommends indicator-datetime                     
13)     unity-greeter recommends indicator-power                        
14)     gnome-panel recommends gnome-control-center                     
15)     gnome-shell recommends gnome-control-center                     
16)     unity recommends gnome-control-center-unity                     
17)     unity recommends indicator-datetime                             
18)     unity recommends indicator-power                                


Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:

     Keep the following packages at their current version:        
1)     gnome-control-center [1:3.6.3-0ubuntu12 (now, raring)]     
2)     gnome-control-center-data [1:3.6.3-0ubuntu12 (now, raring)]



Accept this solution? [Y/n/q/?] 
```

---

### Post by Harry33 on 2013-02-02
> **zika said:**
> Yes...
```
a:~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gnome-control-center gnome-control-center-data
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
zika@zika:~$ sudo apt-get dist-upg^Cde 
zika@zika:~$ sudo aptitude full-upgrade The following packages will be upgraded: 
  gnome-control-center{b} gnome-control-center-data 
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,528 kB of archives. After unpacking 10.2 MB will be used.
The following packages have unmet dependencies:
 gnome-control-center : Depends: gnome-icon-theme (>= 3.7.4) but 3.7.3+git20121224.2af6b37d-0ubuntu1~13.04~ricotz0 is installed.
The following actions will resolve these dependencies:

      Remove the following packages:                                    
1)      gnome-control-center                                            
2)      gnome-control-center-signon                                     
3)      gnome-control-center-unity                                      
4)      indicator-datetime                                              
5)      indicator-power                                                 
6)      ubuntu-desktop                                                  

      Leave the following dependencies unresolved:                      
7)      gnome-bluetooth recommends gnome-control-center                 
8)      gnome-media recommends gnome-control-center                     
9)      gnome-online-accounts recommends gnome-control-center (>= 3.6.1)
10)     libaccount-plugin-1.0-0 recommends gnome-control-center-signon  
11)     mcp-account-manager-uoa recommends gnome-control-center-signon  
12)     unity-greeter recommends indicator-datetime                     
13)     unity-greeter recommends indicator-power                        
14)     gnome-panel recommends gnome-control-center                     
15)     gnome-shell recommends gnome-control-center                     
16)     unity recommends gnome-control-center-unity                     
17)     unity recommends indicator-datetime                             
18)     unity recommends indicator-power                                


Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:

     Keep the following packages at their current version:        
1)     gnome-control-center [1:3.6.3-0ubuntu12 (now, raring)]     
2)     gnome-control-center-data [1:3.6.3-0ubuntu12 (now, raring)]



Accept this solution? [Y/n/q/?] 
```


OK, see this:
"Depends: gnome-icon-theme (>= 3.7.4) but 3.7.3+git20121224.2af6b37d-0ubuntu1~13.04~ricotz0 is installed."

You do not have all the packages from Gnome3 Staging PPA installed?
Install gnome-icon-theme 3.7.4 first.

---

### Post by zika on 2013-02-02
> **Harry33 said:**
> OK, see this:
"Depends: gnome-icon-theme (>= 3.7.4) but 3.7.3+git20121224.2af6b37d-0ubuntu1~13.04~ricotz0 is installed."

You do not have all the packages from Gnome3 Staging PPA installed?
Install gnome-icon-theme 3.7.4 first.
How? Where from...?
[https://launchpad.net/ubuntu/+source/gnome-icon-theme](https://launchpad.net/ubuntu/+source/gnome-icon-theme)

---

### Post by Harry33 on 2013-02-02
It seems we are hanving problems with Gnome3 Staging PPA now.
The GTK3 packages, particularly libgtk-3-0 (3.7.7+git...).
It depends on libxkbcommon0 (=0.2.0-0ubuntu1).
However, libxkbcommon0 version 0.2.0-0ubuntu3 is in the RR repos now,
and cannot be installed due to the libgtk-3-0 dependencies.

---

### Post by Harry33 on 2013-02-02
> **zika said:**
> How? Where from...?
[https://launchpad.net/ubuntu/+source/gnome-icon-theme](https://launchpad.net/ubuntu/+source/gnome-icon-theme)

By enabling Gnome3 Staging PPA.
This one:

[https://launchpad.net/~gnome3-team/+archive/gnome3-staging/](https://launchpad.net/~gnome3-team/+archive/gnome3-staging/)

---

### Post by zika on 2013-02-02
> **Harry33 said:**
> By enabling Gnome3 Staging PPA.
This one:

[https://launchpad.net/~gnome3-team/+archive/gnome3-staging/](https://launchpad.net/~gnome3-team/+archive/gnome3-staging/)
I've got my icons back with my alias given above...
I'll check this PPA right now...
Thank You for a leading hand...
It started with a borked system and I'll end up with a totaly new perspective... ;)
It still complaints about icons...
```
:~$ sudo apt-add-repository ppa:gnome3-team/gnome3-staging
[sudo] password for zika: 
You are about to add the following PPA to your system:
 This PPA will be used to test uploads before they are copied to the main GNOME 3 PPA.

If they break your system, you get to keep both halves.

To use this PPA, you should enable the main GNOME3 PPA too.
 More info: https://launchpad.net/~gnome3-team/+archive/gnome3-staging
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmp4cu1no/secring.gpg' created
gpg: keyring `/tmp/tmp4cu1no/pubring.gpg' created
gpg: requesting key 3B1510FD from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp4cu1no/trustdb.gpg: trustdb created
gpg: key 3B1510FD: public key "Launchpad PPA for GNOME3 Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
zika@zika:~$ UPALL
Ign http://archive.canonical.com raring InRelease
Ign http://extras.ubuntu.com raring InRelease                                   
Ign http://ppa.launchpad.net quantal InRelease                                  
Hit http://packages.medibuntu.org raring InRelease                              
Ign http://archive.ubuntu.com raring InRelease                                  
Hit http://archive.canonical.com raring Release.gpg                             
Ign http://ppa.launchpad.net raring InRelease                                   
Hit http://extras.ubuntu.com raring Release.gpg                                 
Ign http://archive.ubuntu.com raring-updates InRelease                          
Hit http://archive.canonical.com raring Release                                 
Hit http://extras.ubuntu.com raring Release                                     
Ign http://ppa.launchpad.net quantal InRelease
Ign http://archive.ubuntu.com raring-security InRelease                         
Ign http://ppa.launchpad.net raring InRelease                                   
Hit http://archive.canonical.com raring/partner amd64 Packages                  
Hit http://extras.ubuntu.com raring/main amd64 Packages                         
Ign http://archive.ubuntu.com raring-backports InRelease                        
Hit http://packages.medibuntu.org raring/free amd64 Packages                    
Ign http://ppa.launchpad.net raring InRelease                                   
Hit http://archive.canonical.com raring/partner i386 Packages                   
Hit http://extras.ubuntu.com raring/main i386 Packages                          
Hit http://archive.ubuntu.com raring Release.gpg                                
Ign http://ppa.launchpad.net raring InRelease                                   
Hit http://archive.ubuntu.com raring-updates Release.gpg                        
Hit http://packages.medibuntu.org raring/non-free amd64 Packages                
Ign http://ppa.launchpad.net raring InRelease                                   
Hit http://liquorix.net sid InRelease                                           
Hit http://archive.ubuntu.com raring-security Release.gpg                       
Ign http://ppa.launchpad.net raring InRelease                                   
Hit http://archive.ubuntu.com raring-backports Release.gpg                      
Ign http://ppa.launchpad.net raring InRelease                                   
Hit http://archive.ubuntu.com raring Release                                    
Hit http://packages.medibuntu.org raring/free i386 Packages                     
Ign http://ppa.launchpad.net raring InRelease                                   
Hit http://archive.ubuntu.com raring-updates Release                            
Ign http://ppa.launchpad.net raring InRelease                                   
Hit http://archive.ubuntu.com raring-security Release                           
Hit http://liquorix.net sid/main amd64 Packages                                 
Hit http://packages.medibuntu.org raring/non-free i386 Packages                 
Hit http://archive.ubuntu.com raring-backports Release                          
Hit http://ppa.launchpad.net quantal Release.gpg                                
Hit http://archive.ubuntu.com raring/main amd64 Packages                        
Hit http://ppa.launchpad.net raring Release.gpg                                 
Ign http://archive.canonical.com raring/partner Translation-en_US               
Ign http://extras.ubuntu.com raring/main Translation-en_US                      
Hit http://archive.ubuntu.com raring/restricted amd64 Packages                  
Hit http://ppa.launchpad.net quantal Release.gpg                                
Ign http://archive.canonical.com raring/partner Translation-en                  
Ign http://extras.ubuntu.com raring/main Translation-en                         
Hit http://archive.ubuntu.com raring/universe amd64 Packages                    
Hit http://ppa.launchpad.net raring Release.gpg                                 
Hit http://liquorix.net sid/future amd64 Packages                    
Hit http://archive.ubuntu.com raring/multiverse amd64 Packages                  
Get: 1 http://ppa.launchpad.net raring Release.gpg [316 B]           
Hit http://archive.ubuntu.com raring/main i386 Packages                         
Hit http://ppa.launchpad.net raring Release.gpg                                 
Hit http://ppa.launchpad.net raring Release.gpg                                 
Hit http://archive.ubuntu.com raring/restricted i386 Packages        
Hit http://ppa.launchpad.net raring Release.gpg                                 
Hit http://liquorix.net sid/main i386 Packages                                  
Hit http://archive.ubuntu.com raring/universe i386 Packages                     
Hit http://ppa.launchpad.net raring Release.gpg                      
Hit http://archive.ubuntu.com raring/multiverse i386 Packages        
Hit http://ppa.launchpad.net raring Release.gpg                                 
Hit http://ppa.launchpad.net raring Release.gpg                                 
Hit http://archive.ubuntu.com raring/main Translation-en             
Hit http://ppa.launchpad.net quantal Release                         
Hit http://liquorix.net sid/future i386 Packages                                
Hit http://ppa.launchpad.net raring Release                                     
Hit http://archive.ubuntu.com raring/multiverse Translation-en                  
Hit http://ppa.launchpad.net quantal Release                         
Hit http://ppa.launchpad.net raring Release                                     
Hit http://archive.ubuntu.com raring/restricted Translation-en                  
Get: 2 http://ppa.launchpad.net raring Release [9,752 B]                        
Hit http://archive.ubuntu.com raring/universe Translation-en                    
Hit http://archive.ubuntu.com raring-updates/main amd64 Packages                
Hit http://archive.ubuntu.com raring-updates/restricted amd64 Packages
Hit http://archive.ubuntu.com raring-updates/universe amd64 Packages 
Hit http://ppa.launchpad.net raring Release                                     
Hit http://archive.ubuntu.com raring-updates/multiverse amd64 Packages          
Hit http://ppa.launchpad.net raring Release                          
Hit http://archive.ubuntu.com raring-updates/main i386 Packages                 
Hit http://ppa.launchpad.net raring Release                                     
Hit http://archive.ubuntu.com raring-updates/restricted i386 Packages           
Hit http://ppa.launchpad.net raring Release                          
Hit http://ppa.launchpad.net raring Release                                     
Hit http://ppa.launchpad.net raring Release                                     
Hit http://archive.ubuntu.com raring-updates/universe i386 Packages             
Hit http://ppa.launchpad.net quantal/main amd64 Packages             
Hit http://archive.ubuntu.com raring-updates/multiverse i386 Packages
Hit http://ppa.launchpad.net quantal/main i386 Packages                         
Hit http://archive.ubuntu.com raring-updates/main Translation-en                
Hit http://ppa.launchpad.net raring/main amd64 Packages              
Hit http://archive.ubuntu.com raring-updates/multiverse Translation-en
Hit http://ppa.launchpad.net raring/main i386 Packages               
Hit http://archive.ubuntu.com raring-updates/restricted Translation-en          
Hit http://ppa.launchpad.net quantal/main amd64 Packages             
Hit http://archive.ubuntu.com raring-updates/universe Translation-en            
Hit http://ppa.launchpad.net quantal/main i386 Packages                         
Hit http://archive.ubuntu.com raring-security/main amd64 Packages    
Hit http://archive.ubuntu.com raring-security/restricted amd64 Packages
Hit http://archive.ubuntu.com raring-security/universe amd64 Packages           
Hit http://archive.ubuntu.com raring-security/multiverse amd64 Packages
Hit http://archive.ubuntu.com raring-security/main i386 Packages     
Hit http://ppa.launchpad.net raring/main Sources                                
Hit http://archive.ubuntu.com raring-security/restricted i386 Packages
Ign http://packages.medibuntu.org raring/free Translation-en_US      
Hit http://ppa.launchpad.net raring/main amd64 Packages              
Hit http://archive.ubuntu.com raring-security/universe i386 Packages            
Hit http://ppa.launchpad.net raring/main i386 Packages                          
Ign http://packages.medibuntu.org raring/free Translation-en         
Hit http://archive.ubuntu.com raring-security/multiverse i386 Packages
Ign http://packages.medibuntu.org raring/non-free Translation-en_US             
Get: 3 http://ppa.launchpad.net raring/main Sources [26.0 kB]        
Hit http://archive.ubuntu.com raring-security/main Translation-en               
Ign http://packages.medibuntu.org raring/non-free Translation-en                
Hit http://archive.ubuntu.com raring-security/multiverse Translation-en        
Get: 4 http://ppa.launchpad.net raring/main amd64 Packages [40.9 kB]  
Hit http://archive.ubuntu.com raring-security/restricted Translation-en        
Hit http://archive.ubuntu.com raring-security/universe Translation-en
Hit http://archive.ubuntu.com raring-backports/main amd64 Packages
Hit http://archive.ubuntu.com raring-backports/restricted amd64 Packages
Hit http://archive.ubuntu.com raring-backports/universe amd64 Packages          
Get: 5 http://ppa.launchpad.net raring/main i386 Packages [40.9 kB]
Hit http://archive.ubuntu.com raring-backports/multiverse amd64 Packages     
Hit http://archive.ubuntu.com raring-backports/main i386 Packages
Hit http://archive.ubuntu.com raring-backports/restricted i386 Packages
Hit http://archive.ubuntu.com raring-backports/universe i386 Packages
Hit http://archive.ubuntu.com raring-backports/multiverse i386 Packages   
Hit http://ppa.launchpad.net raring/main amd64 Packages
Hit http://ppa.launchpad.net raring/main i386 Packages
Hit http://archive.ubuntu.com raring-backports/main Translation-en
Hit http://ppa.launchpad.net raring/main Sources
Hit http://archive.ubuntu.com raring-backports/multiverse Translation-en
Hit http://ppa.launchpad.net raring/main amd64 Packages
Hit http://archive.ubuntu.com raring-backports/restricted Translation-en
Hit http://ppa.launchpad.net raring/main i386 Packages
Hit http://archive.ubuntu.com raring-backports/universe Translation-en
Hit http://ppa.launchpad.net raring/main amd64 Packages
Hit http://ppa.launchpad.net raring/main i386 Packages
Hit http://ppa.launchpad.net raring/main Sources
Hit http://ppa.launchpad.net raring/main amd64 Packages
Hit http://ppa.launchpad.net raring/main i386 Packages
Hit http://ppa.launchpad.net raring/main amd64 Packages
Hit http://ppa.launchpad.net raring/main i386 Packages
Hit http://ppa.launchpad.net raring/main amd64 Packages
Hit http://ppa.launchpad.net raring/main i386 Packages
Ign http://liquorix.net sid/future Translation-en_US
Ign http://liquorix.net sid/future Translation-en
Ign http://liquorix.net sid/main Translation-en_US
Ign http://liquorix.net sid/main Translation-en 
Ign http://archive.ubuntu.com raring/main Translation-en_US
Ign http://archive.ubuntu.com raring/multiverse Translation-en_US
Ign http://archive.ubuntu.com raring/restricted Translation-en_US
Ign http://archive.ubuntu.com raring/universe Translation-en_US
Ign http://archive.ubuntu.com raring-updates/main Translation-en_US
Ign http://archive.ubuntu.com raring-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com raring-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com raring-updates/universe Translation-en_US
Ign http://archive.ubuntu.com raring-security/main Translation-en_US
Ign http://archive.ubuntu.com raring-security/multiverse Translation-en_US      
Ign http://archive.ubuntu.com raring-security/restricted Translation-en_US      
Ign http://archive.ubuntu.com raring-security/universe Translation-en_US        
Ign http://archive.ubuntu.com raring-backports/main Translation-en_US           
Ign http://archive.ubuntu.com raring-backports/multiverse Translation-en_US     
Ign http://archive.ubuntu.com raring-backports/restricted Translation-en_US     
Ign http://archive.ubuntu.com raring-backports/universe Translation-en_US       
Ign http://ppa.launchpad.net quantal/main Translation-en_US                     
Ign http://ppa.launchpad.net quantal/main Translation-en                        
Ign http://ppa.launchpad.net raring/main Translation-en_US                      
Ign http://ppa.launchpad.net raring/main Translation-en                         
Ign http://ppa.launchpad.net quantal/main Translation-en_US                     
Ign http://ppa.launchpad.net quantal/main Translation-en                        
Ign http://ppa.launchpad.net raring/main Translation-en_US                      
Ign http://ppa.launchpad.net raring/main Translation-en                         
Ign http://ppa.launchpad.net raring/main Translation-en_US                      
Ign http://ppa.launchpad.net raring/main Translation-en                         
Ign http://ppa.launchpad.net raring/main Translation-en_US                      
Ign http://ppa.launchpad.net raring/main Translation-en                         
Ign http://ppa.launchpad.net raring/main Translation-en_US                      
Ign http://ppa.launchpad.net raring/main Translation-en                         
Ign http://ppa.launchpad.net raring/main Translation-en_US                      
Ign http://ppa.launchpad.net raring/main Translation-en                         
Ign http://ppa.launchpad.net raring/main Translation-en_US                      
Ign http://ppa.launchpad.net raring/main Translation-en                         
Ign http://ppa.launchpad.net raring/main Translation-en_US                      
Ign http://ppa.launchpad.net raring/main Translation-en                         
Ign http://ppa.launchpad.net raring/main Translation-en_US                      
Ign http://ppa.launchpad.net raring/main Translation-en                         
Fetched 118 kB in 8s (13.9 kB/s)                                                
                            
Current status: 113 updates [+113], 1678 new [+45].
Resolving dependencies...                
The following NEW packages will be installed:
  libgnome-desktop-3-5{a} libgweather-3-3{a} 
The following packages will be upgraded:
  accountsservice alacarte baobab eog evolution-data-server 
  evolution-data-server-common file-roller fontconfig fontconfig-config gcr 
  gdm gedit gedit-common gir1.2-accountsservice-1.0 gir1.2-clutter-1.0 
  gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gdesktopenums-3.0 gir1.2-gdkpixbuf-2.0 
  gir1.2-gnomedesktop-3.0 gir1.2-gtksource-3.0 gir1.2-mutter-3.0 
  gir1.2-pango-1.0 gir1.2-peas-1.0 gjs glib-networking 
  glib-networking-common glib-networking-services 
  gnome-accessibility-themes gnome-contacts gnome-control-center 
  gnome-control-center-data gnome-desktop3-data gnome-disk-utility 
  gnome-font-viewer gnome-icon-theme gnome-icon-theme-full 
  gnome-icon-theme-symbolic gnome-keyring gnome-mahjongg gnome-screenshot 
  gnome-session gnome-session-bin gnome-session-common 
  gnome-session-fallback gnome-settings-daemon gnome-shell 
  gnome-shell-common gnome-shell-extensions gnome-sudoku 
  gnome-system-monitor gnome-terminal gnome-terminal-data 
  gnome-themes-standard gnome-themes-standard-data gnome-tweak-tool 
  gsettings-desktop-schemas libaccountsservice0 libcamel-1.2-43 
  libclutter-1.0-0 libclutter-1.0-common libebackend-1.2-6 libebook-1.2-14 
  libecal-1.2-15 libedata-book-1.2-16 libedata-cal-1.2-20 
  libedataserver-1.2-17 libfontconfig1 libgck-1-0 libgcr-3-1 
  libgcr-3-common libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgjs0c 
  libgnome-control-center1 libgtksourceview-3.0-0 
  libgtksourceview-3.0-common libgweather-3-1 libgweather-common 
  libmutter0a libnautilus-extension1a libpam-gnome-keyring libpango1.0-0 
  libpeas-1.0-0 libpeas-common librsvg2-2 librsvg2-common libudisks2-0 
  libyelp0 mutter mutter-common nautilus-data seahorse udisks2 vino yelp 
  yelp-xsl zenity zenity-common 
99 packages upgraded, 2 newly installed, 0 to remove and 14 not upgraded.
Need to get 77.5 MB of archives. After unpacking 124 MB will be used.
Do you want to continue? [Y/n/?] 
Get: 1 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libfontconfig1 amd64 2.10.91-0ubuntu1~raring1 [335 kB]
Get: 2 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main fontconfig-config all 2.10.91-0ubuntu1~raring1 [249 kB]
Get: 3 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-shell-extensions all 3.7.4-0ubuntu1~raring1 [84.6 kB]
Get: 4 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-settings-daemon amd64 3.7.4-0ubuntu1~raring3 [1,095 kB]
Get: 5 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-font-viewer amd64 3.7.4-0ubuntu1~raring1 [69.6 kB]
Get: 6 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-control-center amd64 1:3.7.4-0ubuntu1~raring2 [2,901 kB]
Get: 7 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-control-center-data all 1:3.7.4-0ubuntu1~raring2 [3,469 kB]
Get: 8 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gdm amd64 3.7.3.1-0ubuntu1~raring2 [813 kB]
Get: 9 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-shell amd64 3.7.4.1-0ubuntu1~raring1 [296 kB]
Get: 10 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-shell-common all 3.7.4.1-0ubuntu1~raring1 [842 kB]                                                                                                                                                                                                             
Get: 11 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main fontconfig amd64 2.10.91-0ubuntu1~raring1 [403 kB]                                                                                                                                                                                                                   
Get: 12 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libpango1.0-0 amd64 1.32.6-0ubuntu1~raring2 [351 kB]                                                                                                                                                                                                                 
Get: 13 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main librsvg2-common amd64 2.37.0-0ubuntu1~raring1 [166 kB]                                                                                                                                                                                                               
Get: 14 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libgdk-pixbuf2.0-common all 2.27.1-0ubuntu1~raring1 [290 kB]                                                                                                                                                                                                         
Get: 15 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libgdk-pixbuf2.0-0 amd64 2.27.1-0ubuntu1~raring1 [159 kB]                                                                                                                                                                                                            
Get: 16 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main librsvg2-2 amd64 2.37.0-0ubuntu1~raring1 [241 kB]                                                                                                                                                                                                                    
Get: 17 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gir1.2-gdkpixbuf-2.0 amd64 2.27.1-0ubuntu1~raring1 [14.6 kB]                                                                                                                                                                                                         
Get: 18 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gir1.2-pango-1.0 amd64 1.32.6-0ubuntu1~raring2 [176 kB]                                                                                                                                                                                                              
Get: 19 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gir1.2-clutter-1.0 amd64 1.13.4-0ubuntu1~raring1 [200 kB]                                                                                                                                                                                                            
Get: 20 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libclutter-1.0-0 amd64 1.13.4-0ubuntu1~raring1 [537 kB]                                                                                                                                                                                                              
Get: 21 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gir1.2-gdesktopenums-3.0 amd64 3.7.4-0ubuntu1~raring1 [10.2 kB]                                                                                                                                                                                                      
Get: 22 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gsettings-desktop-schemas all 3.7.4-0ubuntu1~raring1 [311 kB]                                                                                                                                                                                                        
Get: 23 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-accessibility-themes all 3.7.4-0ubuntu1~raring1 [2,158 kB]                                                                                                                                                                                                     
Get: 24 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-themes-standard amd64 3.7.4-0ubuntu1~raring1 [230 kB]                                                                                                                                                                                                          
Get: 25 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-themes-standard-data all 3.7.4-0ubuntu1~raring1 [1,637 kB]                                                                                                                                                                                                     
Get: 26 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main zenity amd64 3.7.2-0ubuntu1~raring1 [233 kB]                                                                                                                                                                                                                         
Get: 27 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main zenity-common all 3.7.2-0ubuntu1~raring1 [3,474 kB]                                                                                                                                                                                                                  
Get: 28 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main mutter amd64 3.7.4-0ubuntu1~raring1 [252 kB]                                                                                                                                                                                                                         
Get: 29 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libmutter0a amd64 3.7.4-0ubuntu1~raring1 [491 kB]                                                                                                                                                                                                                    
Get: 30 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main mutter-common all 3.7.4-0ubuntu1~raring1 [786 kB]                                                                                                                                                                                                                    
Get: 31 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gir1.2-mutter-3.0 amd64 3.7.4-0ubuntu1~raring1 [239 kB]                                                                                                                                                                                                              
Get: 32 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-icon-theme all 3.7.4-0ubuntu1~raring1 [674 kB]                                                                                                                                                                                                                 
Get: 33 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-icon-theme-full all 3.7.4-0ubuntu1~raring1 [8,713 kB]                                                                                                                                                                                                          
Get: 34 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libgck-1-0 amd64 3.7.2-0ubuntu1~raring1 [202 kB]                                                                                                                                                                                                                     
Get: 35 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libgcr-3-common all 3.7.2-0ubuntu1~raring1 [129 kB]                                                                                                                                                                                                                  
Get: 36 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libgcr-3-1 amd64 3.7.2-0ubuntu1~raring1 [399 kB]                                                                                                                                                                                                                     
Get: 37 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libebackend-1.2-6 amd64 3.7.4-0ubuntu1~raring2 [188 kB]                                                                                                                                                                                                              
Get: 38 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main evolution-data-server amd64 3.7.4-0ubuntu1~raring2 [403 kB]                                                                                                                                                                                                          
Get: 39 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libebook-1.2-14 amd64 3.7.4-0ubuntu1~raring2 [191 kB]                                                                                                                                                                                                                
Get: 40 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libedata-book-1.2-16 amd64 3.7.4-0ubuntu1~raring2 [172 kB]                                                                                                                                                                                                           
Get: 41 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libedata-cal-1.2-20 amd64 3.7.4-0ubuntu1~raring2 [174 kB]                                                                                                                                                                                                            
Get: 42 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libgweather-common all 3.7.4-0ubuntu1~raring1 [2,308 kB]                                                                                                                                                                                                             
Get: 43 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libgweather-3-3 amd64 3.7.4-0ubuntu1~raring1 [60.5 kB]                                                                                                                                                                                                               
Get: 44 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main evolution-data-server-common all 3.7.4-0ubuntu1~raring2 [1,157 kB]                                                                                                                                                                                                   
Get: 45 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libcamel-1.2-43 amd64 3.7.4-0ubuntu1~raring2 [550 kB]                                                                                                                                                                                                                
Get: 46 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libedataserver-1.2-17 amd64 3.7.4-0ubuntu1~raring2 [254 kB]                                                                                                                                                                                                          
Get: 47 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libecal-1.2-15 amd64 3.7.4-0ubuntu1~raring2 [208 kB]                                                                                                                                                                                                                 
Get: 48 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libgjs0c amd64 1.35.4-0ubuntu1~raring1 [183 kB]                                                                                                                                                                                                                      
Get: 49 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libaccountsservice0 amd64 0.6.30-0ubuntu1~raring1 [96.5 kB]                                                                                                                                                                                                          
Get: 50 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main accountsservice amd64 0.6.30-0ubuntu1~raring1 [89.0 kB]                                                                                                                                                                                                              
Get: 51 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gir1.2-accountsservice-1.0 amd64 0.6.30-0ubuntu1~raring1 [13.7 kB]                                                                                                                                                                                                   
Get: 52 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gir1.2-gcr-3 amd64 3.7.2-0ubuntu1~raring1 [143 kB]                                                                                                                                                                                                                   
Get: 53 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gir1.2-gck-1 amd64 3.7.2-0ubuntu1~raring1 [136 kB]                                                                                                                                                                                                                   
Get: 54 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-desktop3-data all 3.7.4-0ubuntu1~raring1 [491 kB]                                                                                                                                                                                                              
Get: 55 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libgnome-desktop-3-5 amd64 3.7.4-0ubuntu1~raring1 [183 kB]                                                                                                                                                                                                           
Get: 56 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gir1.2-gnomedesktop-3.0 amd64 3.7.4-0ubuntu1~raring1 [123 kB]                                                                                                                                                                                                        
Get: 57 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gjs amd64 1.35.4-0ubuntu1~raring1 [14.3 kB]                                                                                                                                                                                                                          
Get: 58 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-icon-theme-symbolic all 3.7.4.1-0ubuntu1~raring0 [89.9 kB]                                                                                                                                                                                                     
Get: 59 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main nautilus-data all 1:3.7.4-0ubuntu1~raring1 [4,177 kB]                                                                                                                                                                                                                
Get: 60 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-session all 3.7.3-0ubuntu1~raring3 [155 kB]                                                                                                                                                                                                                    
Get: 61 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-session-fallback all 3.7.3-0ubuntu1~raring3 [147 kB]                                                                                                                                                                                                           
Get: 62 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-session-common all 3.7.3-0ubuntu1~raring3 [286 kB]                                                                                                                                                                                                             
Get: 63 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main vino amd64 3.7.4-0ubuntu1~raring1 [407 kB]                                                                                                                                                                                                                           
Get: 64 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-session-bin amd64 3.7.3-0ubuntu1~raring3 [252 kB]                                                                                                                                                                                                              
Get: 65 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-terminal amd64 3.7.2-0ubuntu1~raring1 [524 kB]                                                                                                                                                                                                                 
Get: 66 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-terminal-data all 3.7.2-0ubuntu1~raring1 [1,178 kB]                                                                                                                                                                                                            
Get: 67 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libudisks2-0 amd64 2.0.91-0ubuntu1~raring1 [127 kB]                                                                                                                                                                                                                  
Get: 68 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main udisks2 amd64 2.0.91-0ubuntu1~raring1 [334 kB]                                                                                                                                                                                                                       
Get: 69 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-disk-utility amd64 3.7.1-0ubuntu1~raring1 [788 kB]                                                                                                                                                                                                             
Get: 70 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libgtksourceview-3.0-0 amd64 3.7.2-0ubuntu1~raring1 [262 kB]                                                                                                                                                                                                         
Get: 71 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libgtksourceview-3.0-common all 3.7.2-0ubuntu1~raring1 [651 kB]                                                                                                                                                                                                      
Get: 72 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main alacarte all 3.7.3-0ubuntu1~raring1 [93.1 kB]                                                                                                                                                                                                                        
Get: 73 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main baobab amd64 3.7.4-0ubuntu1~raring1 [342 kB]                                                                                                                                                                                                                         
Get: 74 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libpeas-common all 1.7.0-0ubuntu1~raring1 [148 kB]                                                                                                                                                                                                                   
Get: 75 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libpeas-1.0-0 amd64 1.7.0-0ubuntu1~raring1 [158 kB]                                                                                                                                                                                                                  
Get: 76 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gir1.2-peas-1.0 amd64 1.7.0-0ubuntu1~raring1 [114 kB]                                                                                                                                                                                                                
Get: 77 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main eog amd64 3.7.4-0ubuntu1~raring1 [2,953 kB]                                                                                                                                                                                                                          
Get: 78 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libnautilus-extension1a amd64 1:3.7.4-0ubuntu1~raring1 [2,529 kB]                                                                                                                                                                                                    
Get: 79 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main file-roller amd64 3.7.2-0ubuntu1~raring1 [1,039 kB]                                                                                                                                                                                                                  
Get: 80 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gcr amd64 3.7.2-0ubuntu1~raring1 [316 kB]                                                                                                                                                                                                                            
Get: 81 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gir1.2-gtksource-3.0 amd64 3.7.2-0ubuntu1~raring1 [128 kB]                                                                                                                                                                                                           
Get: 82 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gedit amd64 3.7.3-0ubuntu1~raring2 [692 kB]                                                                                                                                                                                                                          
Get: 83 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gedit-common all 3.7.3-0ubuntu1~raring2 [1,660 kB]                                                                                                                                                                                                                   
Get: 84 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main glib-networking-common all 2.35.4-0ubuntu1~raring1 [46.0 kB]                                                                                                                                                                                                         
Get: 85 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main glib-networking amd64 2.35.4-0ubuntu1~raring1 [47.5 kB]                                                                                                                                                                                                              
Get: 86 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main glib-networking-services amd64 2.35.4-0ubuntu1~raring1 [13.9 kB]                                                                                                                                                                                                     
Get: 87 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-contacts amd64 3.7.3-0ubuntu1~raring2 [280 kB]                                                                                                                                                                                                                 
Get: 88 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-keyring amd64 3.7.2-0ubuntu1~raring1 [981 kB]                                                                                                                                                                                                                  
Get: 89 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-mahjongg amd64 1:3.7.4-0ubuntu1~raring1 [4,797 kB]                                                                                                                                                                                                             
Get: 90 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-screenshot amd64 3.7.4-0ubuntu1~raring1 [132 kB]                                                                                                                                                                                                               
Get: 91 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-sudoku amd64 1:3.7.4-0ubuntu1~raring1 [4,249 kB]                                                                                                                                                                                                               
Get: 92 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-system-monitor amd64 3.7.4-0ubuntu1~raring1 [2,324 kB]                                                                                                                                                                                                         
Get: 93 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-tweak-tool all 3.7.4-0ubuntu1~raring1 [91.7 kB]                                                                                                                                                                                                                
Get: 94 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libclutter-1.0-common all 1.13.4-0ubuntu1~raring1 [388 kB]                                                                                                                                                                                                           
Get: 95 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libgnome-control-center1 amd64 1:3.7.4-0ubuntu1~raring2 [1,547 kB]                                                                                                                                                                                                   
Get: 96 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libgweather-3-1 amd64 3.7.2-0ubuntu1~raring1 [54.8 kB]                                                                                                                                                                                                               
Get: 97 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libpam-gnome-keyring amd64 3.7.2-0ubuntu1~raring1 [266 kB]                                                                                                                                                                                                           
Get: 98 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main yelp-xsl all 3.7.4-0ubuntu1~raring1 [523 kB]                                                                                                                                                                                                                         
Get: 99 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main libyelp0 amd64 3.7.4-0ubuntu1~raring1 [181 kB]                                                                                                                                                                                                                       
Get: 100 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main yelp amd64 3.7.4-0ubuntu1~raring1 [790 kB]                                                                                                                                                                                                                          
Get: 101 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main seahorse amd64 3.7.2-0ubuntu1~raring1 [1,462 kB]                                                                                                                                                                                                                    
Fetched 77.5 MB in 1min 2s (1,237 kB/s)                                                                                                                                                                                                                                                                                                              
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 310290 files and directories currently installed.)
Preparing to replace libfontconfig1:amd64 2.10.2-0ubuntu1 (using .../libfontconfig1_2.10.91-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement libfontconfig1:amd64 ...
Preparing to replace fontconfig-config 2.10.2-0ubuntu1 (using .../fontconfig-config_2.10.91-0ubuntu1~raring1_all.deb) ...
Unpacking replacement fontconfig-config ...
Preparing to replace gnome-shell-extensions 3.6.0-0ubuntu1 (using .../gnome-shell-extensions_3.7.4-0ubuntu1~raring1_all.deb) ...
Unpacking replacement gnome-shell-extensions ...
Preparing to replace gnome-settings-daemon 3.6.4-0ubuntu3 (using .../gnome-settings-daemon_3.7.4-0ubuntu1~raring3_amd64.deb) ...
Unpacking replacement gnome-settings-daemon ...
Preparing to replace gnome-font-viewer 3.6.2-0ubuntu1 (using .../gnome-font-viewer_3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement gnome-font-viewer ...
Preparing to replace gnome-control-center 1:3.6.3-0ubuntu12 (using .../gnome-control-center_1%3a3.7.4-0ubuntu1~raring2_amd64.deb) ...
Unpacking replacement gnome-control-center ...
Preparing to replace gnome-control-center-data 1:3.6.3-0ubuntu12 (using .../gnome-control-center-data_1%3a3.7.4-0ubuntu1~raring2_all.deb) ...
Unpacking replacement gnome-control-center-data ...
Preparing to replace gdm 3.6.1-0ubuntu2 (using .../gdm_3.7.3.1-0ubuntu1~raring2_amd64.deb) ...
Unpacking replacement gdm ...
Preparing to replace gnome-shell 3.6.2-0ubuntu4 (using .../gnome-shell_3.7.4.1-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement gnome-shell ...
Preparing to replace gnome-shell-common 3.6.2-0ubuntu4 (using .../gnome-shell-common_3.7.4.1-0ubuntu1~raring1_all.deb) ...
Unpacking replacement gnome-shell-common ...
Preparing to replace fontconfig 2.10.2-0ubuntu1 (using .../fontconfig_2.10.91-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement fontconfig ...
Preparing to replace libpango1.0-0:amd64 1.30.1-1ubuntu1 (using .../libpango1.0-0_1.32.6-0ubuntu1~raring2_amd64.deb) ...
Unpacking replacement libpango1.0-0:amd64 ...
Preparing to replace librsvg2-common:amd64 2.36.4-1 (using .../librsvg2-common_2.37.0-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement librsvg2-common:amd64 ...
Preparing to replace libgdk-pixbuf2.0-common 2.26.5-0ubuntu4 (using .../libgdk-pixbuf2.0-common_2.27.1-0ubuntu1~raring1_all.deb) ...
Unpacking replacement libgdk-pixbuf2.0-common ...
Preparing to replace libgdk-pixbuf2.0-0:amd64 2.26.5-0ubuntu4 (using .../libgdk-pixbuf2.0-0_2.27.1-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement libgdk-pixbuf2.0-0:amd64 ...
Preparing to replace librsvg2-2:amd64 2.36.4-1 (using .../librsvg2-2_2.37.0-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement librsvg2-2:amd64 ...
Preparing to replace gir1.2-gdkpixbuf-2.0 2.26.5-0ubuntu4 (using .../gir1.2-gdkpixbuf-2.0_2.27.1-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement gir1.2-gdkpixbuf-2.0 ...
Preparing to replace gir1.2-pango-1.0 1.30.1-1ubuntu1 (using .../gir1.2-pango-1.0_1.32.6-0ubuntu1~raring2_amd64.deb) ...
Unpacking replacement gir1.2-pango-1.0 ...
Preparing to replace gir1.2-clutter-1.0 1.12.2-0ubuntu1 (using .../gir1.2-clutter-1.0_1.13.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement gir1.2-clutter-1.0 ...
Preparing to replace libclutter-1.0-0:amd64 1.12.2-0ubuntu1 (using .../libclutter-1.0-0_1.13.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement libclutter-1.0-0:amd64 ...
Preparing to replace gir1.2-gdesktopenums-3.0 3.6.1-0ubuntu1 (using .../gir1.2-gdesktopenums-3.0_3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement gir1.2-gdesktopenums-3.0 ...
Preparing to replace gsettings-desktop-schemas 3.6.1-0ubuntu1 (using .../gsettings-desktop-schemas_3.7.4-0ubuntu1~raring1_all.deb) ...
Unpacking replacement gsettings-desktop-schemas ...
Preparing to replace gnome-accessibility-themes 3.6.2-1ubuntu1 (using .../gnome-accessibility-themes_3.7.4-0ubuntu1~raring1_all.deb) ...
Unpacking replacement gnome-accessibility-themes ...

(gtk-update-icon-cache-3.0:26365): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.
Preparing to replace gnome-themes-standard:amd64 3.6.2-1ubuntu1 (using .../gnome-themes-standard_3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement gnome-themes-standard:amd64 ...
Preparing to replace gnome-themes-standard-data 3.6.2-1ubuntu1 (using .../gnome-themes-standard-data_3.7.4-0ubuntu1~raring1_all.deb) ...
Unpacking replacement gnome-themes-standard-data ...
Preparing to replace zenity 3.6.0-0ubuntu1 (using .../zenity_3.7.2-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement zenity ...
Preparing to replace zenity-common 3.6.0-0ubuntu1 (using .../zenity-common_3.7.2-0ubuntu1~raring1_all.deb) ...
Unpacking replacement zenity-common ...
Preparing to replace mutter 3.6.2-0ubuntu1 (using .../mutter_3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement mutter ...
Preparing to replace libmutter0a 3.6.2-0ubuntu1 (using .../libmutter0a_3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement libmutter0a ...
Preparing to replace mutter-common 3.6.2-0ubuntu1 (using .../mutter-common_3.7.4-0ubuntu1~raring1_all.deb) ...
Unpacking replacement mutter-common ...
Preparing to replace gir1.2-mutter-3.0 3.6.2-0ubuntu1 (using .../gir1.2-mutter-3.0_3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement gir1.2-mutter-3.0 ...
Preparing to replace gnome-icon-theme 3.6.2-0ubuntu1 (using .../gnome-icon-theme_3.7.4-0ubuntu1~raring1_all.deb) ...
Unpacking replacement gnome-icon-theme ...
Preparing to replace gnome-icon-theme-full 3.6.2-0ubuntu1 (using .../gnome-icon-theme-full_3.7.4-0ubuntu1~raring1_all.deb) ...
Unpacking replacement gnome-icon-theme-full ...
Preparing to replace libgck-1-0 3.6.2-0ubuntu1 (using .../libgck-1-0_3.7.2-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement libgck-1-0 ...
Preparing to replace libgcr-3-common 3.6.2-0ubuntu1 (using .../libgcr-3-common_3.7.2-0ubuntu1~raring1_all.deb) ...
Unpacking replacement libgcr-3-common ...
Preparing to replace libgcr-3-1 3.6.2-0ubuntu1 (using .../libgcr-3-1_3.7.2-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement libgcr-3-1 ...
Preparing to replace libebackend-1.2-6 3.7.4-0ubuntu1~13.04~ricotz1 (using .../libebackend-1.2-6_3.7.4-0ubuntu1~raring2_amd64.deb) ...
Unpacking replacement libebackend-1.2-6 ...
Preparing to replace evolution-data-server 3.7.4-0ubuntu1~13.04~ricotz1 (using .../evolution-data-server_3.7.4-0ubuntu1~raring2_amd64.deb) ...
Unpacking replacement evolution-data-server ...
Preparing to replace libebook-1.2-14 3.7.4-0ubuntu1~13.04~ricotz1 (using .../libebook-1.2-14_3.7.4-0ubuntu1~raring2_amd64.deb) ...
Unpacking replacement libebook-1.2-14 ...
Preparing to replace libedata-book-1.2-16 3.7.4-0ubuntu1~13.04~ricotz1 (using .../libedata-book-1.2-16_3.7.4-0ubuntu1~raring2_amd64.deb) ...
Unpacking replacement libedata-book-1.2-16 ...
Preparing to replace libedata-cal-1.2-20 3.7.4-0ubuntu1~13.04~ricotz1 (using .../libedata-cal-1.2-20_3.7.4-0ubuntu1~raring2_amd64.deb) ...
Unpacking replacement libedata-cal-1.2-20 ...
Preparing to replace libgweather-common 3.6.2-0ubuntu1 (using .../libgweather-common_3.7.4-0ubuntu1~raring1_all.deb) ...
Unpacking replacement libgweather-common ...
Selecting previously unselected package libgweather-3-3.
Unpacking libgweather-3-3 (from .../libgweather-3-3_3.7.4-0ubuntu1~raring1_amd64.deb) ...
Preparing to replace evolution-data-server-common 3.7.4-0ubuntu1~13.04~ricotz1 (using .../evolution-data-server-common_3.7.4-0ubuntu1~raring2_all.deb) ...
Unpacking replacement evolution-data-server-common ...
Preparing to replace libcamel-1.2-43 3.7.4-0ubuntu1~13.04~ricotz1 (using .../libcamel-1.2-43_3.7.4-0ubuntu1~raring2_amd64.deb) ...
Unpacking replacement libcamel-1.2-43 ...
Preparing to replace libedataserver-1.2-17 3.7.4-0ubuntu1~13.04~ricotz1 (using .../libedataserver-1.2-17_3.7.4-0ubuntu1~raring2_amd64.deb) ...
Unpacking replacement libedataserver-1.2-17 ...
Preparing to replace libecal-1.2-15 3.7.4-0ubuntu1~13.04~ricotz1 (using .../libecal-1.2-15_3.7.4-0ubuntu1~raring2_amd64.deb) ...
Unpacking replacement libecal-1.2-15 ...
Preparing to replace libgjs0c 1.34.0-0ubuntu1 (using .../libgjs0c_1.35.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement libgjs0c ...
Preparing to replace libaccountsservice0 0.6.29-1ubuntu5 (using .../libaccountsservice0_0.6.30-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement libaccountsservice0 ...
Preparing to replace accountsservice 0.6.29-1ubuntu5 (using .../accountsservice_0.6.30-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement accountsservice ...
Preparing to replace gir1.2-accountsservice-1.0 0.6.29-1ubuntu5 (using .../gir1.2-accountsservice-1.0_0.6.30-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement gir1.2-accountsservice-1.0 ...
Preparing to replace gir1.2-gcr-3 3.6.2-0ubuntu1 (using .../gir1.2-gcr-3_3.7.2-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement gir1.2-gcr-3 ...
Preparing to replace gir1.2-gck-1 3.6.2-0ubuntu1 (using .../gir1.2-gck-1_3.7.2-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement gir1.2-gck-1 ...
Preparing to replace gnome-desktop3-data 3.7.2-0ubuntu1~raring3 (using .../gnome-desktop3-data_3.7.4-0ubuntu1~raring1_all.deb) ...
Unpacking replacement gnome-desktop3-data ...
Selecting previously unselected package libgnome-desktop-3-5.
Unpacking libgnome-desktop-3-5 (from .../libgnome-desktop-3-5_3.7.4-0ubuntu1~raring1_amd64.deb) ...
Preparing to replace gir1.2-gnomedesktop-3.0 3.7.2-0ubuntu1~raring3 (using .../gir1.2-gnomedesktop-3.0_3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement gir1.2-gnomedesktop-3.0 ...
Preparing to replace gjs 1.34.0-0ubuntu1 (using .../gjs_1.35.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement gjs ...
Preparing to replace gnome-icon-theme-symbolic 3.6.2-0ubuntu1 (using .../gnome-icon-theme-symbolic_3.7.4.1-0ubuntu1~raring0_all.deb) ...
Unpacking replacement gnome-icon-theme-symbolic ...
Preparing to replace nautilus-data 1:3.7.2-0ubuntu1~13.04~ricotz0 (using .../nautilus-data_1%3a3.7.4-0ubuntu1~raring1_all.deb) ...
Unpacking replacement nautilus-data ...
Preparing to replace gnome-session 3.6.2-0ubuntu3 (using .../gnome-session_3.7.3-0ubuntu1~raring3_all.deb) ...
Unpacking replacement gnome-session ...
Preparing to replace gnome-session-fallback 3.6.2-0ubuntu3 (using .../gnome-session-fallback_3.7.3-0ubuntu1~raring3_all.deb) ...
Unpacking replacement gnome-session-fallback ...
Preparing to replace gnome-session-common 3.6.2-0ubuntu3 (using .../gnome-session-common_3.7.3-0ubuntu1~raring3_all.deb) ...
Unpacking replacement gnome-session-common ...
Preparing to replace vino 3.6.2-0ubuntu2 (using .../vino_3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement vino ...
Preparing to replace gnome-session-bin 3.6.2-0ubuntu3 (using .../gnome-session-bin_3.7.3-0ubuntu1~raring3_amd64.deb) ...
Unpacking replacement gnome-session-bin ...
Preparing to replace gnome-terminal 3.6.1-0ubuntu3 (using .../gnome-terminal_3.7.2-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement gnome-terminal ...
Preparing to replace gnome-terminal-data 3.6.1-0ubuntu3 (using .../gnome-terminal-data_3.7.2-0ubuntu1~raring1_all.deb) ...
Unpacking replacement gnome-terminal-data ...
Preparing to replace libudisks2-0:amd64 2.0.1-1 (using .../libudisks2-0_2.0.91-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement libudisks2-0:amd64 ...
Preparing to replace udisks2 2.0.1-1 (using .../udisks2_2.0.91-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement udisks2 ...
Preparing to replace gnome-disk-utility 3.6.1-1ubuntu1 (using .../gnome-disk-utility_3.7.1-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement gnome-disk-utility ...
Preparing to replace libgtksourceview-3.0-0:amd64 3.6.2-0ubuntu1 (using .../libgtksourceview-3.0-0_3.7.2-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement libgtksourceview-3.0-0:amd64 ...
Preparing to replace libgtksourceview-3.0-common 3.6.2-0ubuntu1 (using .../libgtksourceview-3.0-common_3.7.2-0ubuntu1~raring1_all.deb) ...
Unpacking replacement libgtksourceview-3.0-common ...
Preparing to replace alacarte 3.6.1-0ubuntu2 (using .../alacarte_3.7.3-0ubuntu1~raring1_all.deb) ...
Unpacking replacement alacarte ...
Preparing to replace baobab 3.6.4-0ubuntu1 (using .../baobab_3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement baobab ...
Preparing to replace libpeas-common 1.6.2-0ubuntu1 (using .../libpeas-common_1.7.0-0ubuntu1~raring1_all.deb) ...
Unpacking replacement libpeas-common ...
Preparing to replace libpeas-1.0-0 1.6.2-0ubuntu1 (using .../libpeas-1.0-0_1.7.0-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement libpeas-1.0-0 ...
Preparing to replace gir1.2-peas-1.0 1.6.2-0ubuntu1 (using .../gir1.2-peas-1.0_1.7.0-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement gir1.2-peas-1.0 ...
Preparing to replace eog 3.6.2-0ubuntu1 (using .../eog_3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement eog ...
Preparing to replace libnautilus-extension1a 1:3.7.2-0ubuntu1~13.04~ricotz0 (using .../libnautilus-extension1a_1%3a3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement libnautilus-extension1a ...
Preparing to replace file-roller 3.6.3-1ubuntu2 (using .../file-roller_3.7.2-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement file-roller ...
Preparing to replace gcr 3.6.2-0ubuntu1 (using .../gcr_3.7.2-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement gcr ...
Preparing to replace gir1.2-gtksource-3.0 3.6.2-0ubuntu1 (using .../gir1.2-gtksource-3.0_3.7.2-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement gir1.2-gtksource-3.0 ...
Preparing to replace gedit 3.6.2-0ubuntu1 (using .../gedit_3.7.3-0ubuntu1~raring2_amd64.deb) ...
Unpacking replacement gedit ...
Preparing to replace gedit-common 3.6.2-0ubuntu1 (using .../gedit-common_3.7.3-0ubuntu1~raring2_all.deb) ...
Unpacking replacement gedit-common ...
Preparing to replace glib-networking-common 2.35.1-0ubuntu1~13.04~ricotz0 (using .../glib-networking-common_2.35.4-0ubuntu1~raring1_all.deb) ...
Unpacking replacement glib-networking-common ...
Preparing to replace glib-networking:amd64 2.35.1-0ubuntu1~13.04~ricotz0 (using .../glib-networking_2.35.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement glib-networking:amd64 ...
Preparing to replace glib-networking-services 2.35.1-0ubuntu1~13.04~ricotz0 (using .../glib-networking-services_2.35.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement glib-networking-services ...
Preparing to replace gnome-contacts 3.6.2-0ubuntu1 (using .../gnome-contacts_3.7.3-0ubuntu1~raring2_amd64.deb) ...
Unpacking replacement gnome-contacts ...
Preparing to replace gnome-keyring 3.6.2-0ubuntu1 (using .../gnome-keyring_3.7.2-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement gnome-keyring ...
Preparing to replace gnome-mahjongg 1:3.6.1-0ubuntu3 (using .../gnome-mahjongg_1%3a3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement gnome-mahjongg ...
Preparing to replace gnome-screenshot 3.6.1-0ubuntu1 (using .../gnome-screenshot_3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement gnome-screenshot ...
Preparing to replace gnome-sudoku 1:3.6.1-0ubuntu3 (using .../gnome-sudoku_1%3a3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement gnome-sudoku ...
Preparing to replace gnome-system-monitor 3.6.1-0ubuntu1 (using .../gnome-system-monitor_3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement gnome-system-monitor ...
Preparing to replace gnome-tweak-tool 3.6.1-1 (using .../gnome-tweak-tool_3.7.4-0ubuntu1~raring1_all.deb) ...
Unpacking replacement gnome-tweak-tool ...
Preparing to replace libclutter-1.0-common 1.12.2-0ubuntu1 (using .../libclutter-1.0-common_1.13.4-0ubuntu1~raring1_all.deb) ...
Unpacking replacement libclutter-1.0-common ...
Preparing to replace libgnome-control-center1 1:3.6.3-0ubuntu12 (using .../libgnome-control-center1_1%3a3.7.4-0ubuntu1~raring2_amd64.deb) ...
Unpacking replacement libgnome-control-center1 ...
Preparing to replace libgweather-3-1 3.6.2-0ubuntu1 (using .../libgweather-3-1_3.7.2-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement libgweather-3-1 ...
Preparing to replace libpam-gnome-keyring 3.6.2-0ubuntu1 (using .../libpam-gnome-keyring_3.7.2-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement libpam-gnome-keyring ...
Preparing to replace yelp-xsl 3.6.1-1 (using .../yelp-xsl_3.7.4-0ubuntu1~raring1_all.deb) ...
Unpacking replacement yelp-xsl ...
Preparing to replace libyelp0 3.6.2-0ubuntu1 (using .../libyelp0_3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement libyelp0 ...
Preparing to replace yelp 3.6.2-0ubuntu1 (using .../yelp_3.7.4-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement yelp ...
Preparing to replace seahorse 3.6.3-0ubuntu1 (using .../seahorse_3.7.2-0ubuntu1~raring1_amd64.deb) ...
Unpacking replacement seahorse ...
Processing triggers for man-db ...
Processing triggers for libglib2.0-0:amd64 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...

(gtk-update-icon-cache:28824): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.

(gtk-update-icon-cache-3.0:28825): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.
Processing triggers for gconf2 ...
Processing triggers for menu ...
Processing triggers for ureadahead ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file...
Registering documents with scrollkeeper...
Processing triggers for shared-mime-info ...
Setting up fontconfig-config (2.10.91-0ubuntu1~raring1) ...
Installing new version of config file /etc/fonts/conf.avail/50-user.conf ...
Setting up libfontconfig1:amd64 (2.10.91-0ubuntu1~raring1) ...
Setting up libgdk-pixbuf2.0-common (2.27.1-0ubuntu1~raring1) ...
Setting up libgdk-pixbuf2.0-0:amd64 (2.27.1-0ubuntu1~raring1) ...
Setting up gir1.2-gdkpixbuf-2.0 (2.27.1-0ubuntu1~raring1) ...
Setting up fontconfig (2.10.91-0ubuntu1~raring1) ...
Regenerating fonts cache... done.
Setting up libpango1.0-0:amd64 (1.32.6-0ubuntu1~raring2) ...
Setting up gir1.2-pango-1.0 (1.32.6-0ubuntu1~raring2) ...
Setting up libclutter-1.0-0:amd64 (1.13.4-0ubuntu1~raring1) ...
Setting up gir1.2-clutter-1.0 (1.13.4-0ubuntu1~raring1) ...
Setting up gir1.2-gdesktopenums-3.0 (3.7.4-0ubuntu1~raring1) ...
Setting up gsettings-desktop-schemas (3.7.4-0ubuntu1~raring1) ...
Setting up mutter-common (3.7.4-0ubuntu1~raring1) ...
Setting up libmutter0a (3.7.4-0ubuntu1~raring1) ...
Setting up gir1.2-mutter-3.0 (3.7.4-0ubuntu1~raring1) ...
Setting up librsvg2-2:amd64 (2.37.0-0ubuntu1~raring1) ...
Setting up librsvg2-common:amd64 (2.37.0-0ubuntu1~raring1) ...
Setting up gnome-icon-theme (3.7.4-0ubuntu1~raring1) ...
Setting up libcamel-1.2-43 (3.7.4-0ubuntu1~raring2) ...
Setting up libgck-1-0 (3.7.2-0ubuntu1~raring1) ...
Setting up libgcr-3-common (3.7.2-0ubuntu1~raring1) ...
Setting up libgcr-3-1 (3.7.2-0ubuntu1~raring1) ...
Setting up evolution-data-server-common (3.7.4-0ubuntu1~raring2) ...
Setting up libedataserver-1.2-17 (3.7.4-0ubuntu1~raring2) ...
Setting up libecal-1.2-15 (3.7.4-0ubuntu1~raring2) ...
Setting up libgjs0c (1.35.4-0ubuntu1~raring1) ...
Setting up libaccountsservice0 (0.6.30-0ubuntu1~raring1) ...
Setting up gnome-desktop3-data (3.7.4-0ubuntu1~raring1) ...
Setting up libgnome-desktop-3-5 (3.7.4-0ubuntu1~raring1) ...
Setting up gnome-session-bin (3.7.3-0ubuntu1~raring3) ...
Setting up nautilus-data (1:3.7.4-0ubuntu1~raring1) ...
Setting up gnome-settings-daemon (3.7.4-0ubuntu1~raring3) ...
Installing new version of config file /etc/xdg/autostart/gnome-settings-daemon.desktop ...
Setting up gnome-session-common (3.7.3-0ubuntu1~raring3) ...
Setting up gnome-session (3.7.3-0ubuntu1~raring3) ...
Setting up gnome-session-fallback (3.7.3-0ubuntu1~raring3) ...
Setting up gnome-themes-standard-data (3.7.4-0ubuntu1~raring1) ...
Setting up gnome-themes-standard:amd64 (3.7.4-0ubuntu1~raring1) ...
Setting up zenity-common (3.7.2-0ubuntu1~raring1) ...
Setting up zenity (3.7.2-0ubuntu1~raring1) ...
Setting up mutter (3.7.4-0ubuntu1~raring1) ...
Setting up gnome-terminal-data (3.7.2-0ubuntu1~raring1) ...
Setting up gnome-terminal (3.7.2-0ubuntu1~raring1) ...
Setting up accountsservice (0.6.30-0ubuntu1~raring1) ...
Setting up gdm (3.7.3.1-0ubuntu1~raring2) ...
Installing new version of config file /etc/dconf/db/gdm.d/00-upstream-settings ...
Installing new version of config file /etc/dconf/db/gdm.d/locks/00-upstream-settings-locks ...
Setting up gnome-shell-common (3.7.4.1-0ubuntu1~raring1) ...
Setting up gir1.2-accountsservice-1.0 (0.6.30-0ubuntu1~raring1) ...
Setting up gir1.2-gck-1 (3.7.2-0ubuntu1~raring1) ...
Setting up gir1.2-gcr-3 (3.7.2-0ubuntu1~raring1) ...
Setting up gir1.2-gnomedesktop-3.0 (3.7.4-0ubuntu1~raring1) ...
Setting up gjs (1.35.4-0ubuntu1~raring1) ...
Setting up gnome-icon-theme-symbolic (3.7.4.1-0ubuntu1~raring0) ...
Setting up libebackend-1.2-6 (3.7.4-0ubuntu1~raring2) ...
Setting up libebook-1.2-14 (3.7.4-0ubuntu1~raring2) ...
Setting up libedata-book-1.2-16 (3.7.4-0ubuntu1~raring2) ...
Setting up libedata-cal-1.2-20 (3.7.4-0ubuntu1~raring2) ...
Setting up libgweather-common (3.7.4-0ubuntu1~raring1) ...
Setting up libgweather-3-3 (3.7.4-0ubuntu1~raring1) ...
Setting up evolution-data-server (3.7.4-0ubuntu1~raring2) ...
Setting up gnome-font-viewer (3.7.4-0ubuntu1~raring1) ...
Setting up gnome-control-center-data (1:3.7.4-0ubuntu1~raring2) ...
Setting up gnome-control-center (1:3.7.4-0ubuntu1~raring2) ...
Setting up gnome-accessibility-themes (3.7.4-0ubuntu1~raring1) ...
Setting up vino (3.7.4-0ubuntu1~raring1) ...

Configuration file `/etc/xdg/autostart/vino-server.desktop'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** vino-server.desktop (Y/I/N/O/D/Z) [default=N] ? y
Installing new version of config file /etc/xdg/autostart/vino-server.desktop ...
Setting up libudisks2-0:amd64 (2.0.91-0ubuntu1~raring1) ...
Setting up udisks2 (2.0.91-0ubuntu1~raring1) ...
Setting up gnome-disk-utility (3.7.1-0ubuntu1~raring1) ...
Setting up libgtksourceview-3.0-common (3.7.2-0ubuntu1~raring1) ...
Setting up libgtksourceview-3.0-0:amd64 (3.7.2-0ubuntu1~raring1) ...
Setting up alacarte (3.7.3-0ubuntu1~raring1) ...
Setting up baobab (3.7.4-0ubuntu1~raring1) ...
Setting up libpeas-common (1.7.0-0ubuntu1~raring1) ...
Setting up libpeas-1.0-0 (1.7.0-0ubuntu1~raring1) ...
Setting up gir1.2-peas-1.0 (1.7.0-0ubuntu1~raring1) ...
Setting up eog (3.7.4-0ubuntu1~raring1) ...
Setting up libnautilus-extension1a (1:3.7.4-0ubuntu1~raring1) ...
Setting up file-roller (3.7.2-0ubuntu1~raring1) ...
Setting up gcr (3.7.2-0ubuntu1~raring1) ...
Setting up gir1.2-gtksource-3.0 (3.7.2-0ubuntu1~raring1) ...
Setting up gedit-common (3.7.3-0ubuntu1~raring2) ...
Setting up gedit (3.7.3-0ubuntu1~raring2) ...
update-alternatives: using /usr/bin/gedit to provide /usr/bin/gnome-text-editor (gnome-text-editor) in auto mode
Setting up glib-networking-common (2.35.4-0ubuntu1~raring1) ...
Setting up glib-networking-services (2.35.4-0ubuntu1~raring1) ...
Setting up glib-networking:amd64 (2.35.4-0ubuntu1~raring1) ...
Setting up gnome-contacts (3.7.3-0ubuntu1~raring2) ...
Setting up gnome-keyring (3.7.2-0ubuntu1~raring1) ...

Configuration file `/etc/xdg/autostart/gnome-keyring-gpg.desktop'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** gnome-keyring-gpg.desktop (Y/I/N/O/D/Z) [default=N] ? y
Installing new version of config file /etc/xdg/autostart/gnome-keyring-gpg.desktop ...

Configuration file `/etc/xdg/autostart/gnome-keyring-pkcs11.desktop'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** gnome-keyring-pkcs11.desktop (Y/I/N/O/D/Z) [default=N] ? y
Installing new version of config file /etc/xdg/autostart/gnome-keyring-pkcs11.desktop ...

Configuration file `/etc/xdg/autostart/gnome-keyring-ssh.desktop'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** gnome-keyring-ssh.desktop (Y/I/N/O/D/Z) [default=N] ? y
Installing new version of config file /etc/xdg/autostart/gnome-keyring-ssh.desktop ...

Configuration file `/etc/xdg/autostart/gnome-keyring-secrets.desktop'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** gnome-keyring-secrets.desktop (Y/I/N/O/D/Z) [default=N] ? y
Installing new version of config file /etc/xdg/autostart/gnome-keyring-secrets.desktop ...
Setting up gnome-mahjongg (1:3.7.4-0ubuntu1~raring1) ...
Setting up gnome-screenshot (3.7.4-0ubuntu1~raring1) ...
Setting up gnome-sudoku (1:3.7.4-0ubuntu1~raring1) ...
Setting up gnome-system-monitor (3.7.4-0ubuntu1~raring1) ...
Setting up gnome-tweak-tool (3.7.4-0ubuntu1~raring1) ...
Setting up libclutter-1.0-common (1.13.4-0ubuntu1~raring1) ...
Setting up libgnome-control-center1 (1:3.7.4-0ubuntu1~raring2) ...
Setting up libgweather-3-1 (3.7.2-0ubuntu1~raring1) ...
Setting up libpam-gnome-keyring (3.7.2-0ubuntu1~raring1) ...
Setting up yelp-xsl (3.7.4-0ubuntu1~raring1) ...
Setting up libyelp0 (3.7.4-0ubuntu1~raring1) ...
Setting up yelp (3.7.4-0ubuntu1~raring1) ...
Setting up seahorse (3.7.2-0ubuntu1~raring1) ...
Setting up gnome-icon-theme-full (3.7.4-0ubuntu1~raring1) ...
Setting up gnome-shell (3.7.4.1-0ubuntu1~raring1) ...
Setting up gnome-shell-extensions (3.7.4-0ubuntu1~raring1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for libgdk-pixbuf2.0-0:amd64 ...
Processing triggers for menu ...
                                         
Current status: 14 updates [-99].
```

Not to mention:
```
:~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  account-plugin-aim account-plugin-jabber account-plugin-salut account-plugin-yahoo apturl brasero empathy eog evince gdm gnome-applets gnome-control-center gnome-control-center-signon gnome-control-center-unity gnome-icon-theme gnome-icon-theme-full gnome-icon-theme-symbolic gnome-panel gnome-screensaver gnome-session-fallback
  gnome-shell gnome-shell-extensions humanity-icon-theme ibus ibus-pinyin ibus-table indicator-datetime indicator-power libgtk-3-bin light-themes lightdm-remote-session-uccsconfigure mcp-account-manager-uoa metacity nautilus-sendto-empathy nautilus-share network-manager-gnome rhythmbox rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins rhythmbox-ubuntuone simple-scan software-center system-config-printer-gnome totem totem-mozilla totem-plugins ubuntu-artwork ubuntu-desktop ubuntu-mono unity unity-asset-pool unity-scope-musicstores
The following NEW packages will be installed:
  libsofia-sip-ua-glib3 libsofia-sip-ua0 telepathy-rakia
The following packages have been kept back:
  gir1.2-gtk-3.0 libevdocument3-4 libevview3-3 libgail-3-0 libgtk-3-0 libgtk-3-common nautilus
The following packages will be upgraded:
  empathy-common evince-common
2 upgraded, 3 newly installed, 55 to remove and 7 not upgraded.
Need to get 6,674 kB of archives.
After this operation, 74.4 MB disk space will be freed.
Do you want to continue [Y/n]? 
```
```
:~$ sudo aptitude full-upgrade 
The following NEW packages will be installed:
  account-plugin-empathy{ab} libsofia-sip-ua-glib3{a} libsofia-sip-ua0{a} telepathy-rakia{a} 
The following packages will be upgraded:
  empathy empathy-common evince evince-common gir1.2-gtk-3.0 libevdocument3-4 libevview3-3 libgail-3-0 libgtk-3-0{b} libgtk-3-bin libgtk-3-common mcp-account-manager-uoa nautilus nautilus-sendto-empathy 
14 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 20.9 MB of archives. After unpacking 42.3 MB will be used.
The following packages have unmet dependencies:
 account-plugin-yahoo : Depends: empathy (= 3.6.3-0ubuntu2) but 3.7.4-0ubuntu1~raring2 is to be installed.
                        Breaks: account-plugin-empathy but 3.7.4-0ubuntu1~raring2 is to be installed.
 account-plugin-aim : Depends: empathy (= 3.6.3-0ubuntu2) but 3.7.4-0ubuntu1~raring2 is to be installed.
                      Breaks: account-plugin-empathy but 3.7.4-0ubuntu1~raring2 is to be installed.
 account-plugin-empathy : Conflicts: account-plugin-aim but 3.6.3-0ubuntu2 is installed.
                          Conflicts: account-plugin-jabber but 3.6.3-0ubuntu2 is installed.
                          Conflicts: account-plugin-salut but 3.6.3-0ubuntu2 is installed.
                          Conflicts: account-plugin-yahoo but 3.6.3-0ubuntu2 is installed.
 account-plugin-salut : Depends: empathy (= 3.6.3-0ubuntu2) but 3.7.4-0ubuntu1~raring2 is to be installed.
                        Breaks: account-plugin-empathy but 3.7.4-0ubuntu1~raring2 is to be installed.
 libgtk-3-0 : Depends: libxkbcommon0 (= 0.2.0-0ubuntu1) but 0.2.0-0ubuntu3 is installed.
 account-plugin-jabber : Depends: empathy (= 3.6.3-0ubuntu2) but 3.7.4-0ubuntu1~raring2 is to be installed.
                         Breaks: account-plugin-empathy but 3.7.4-0ubuntu1~raring2 is to be installed.
The following actions will resolve these dependencies:

       Remove the following packages:                                                                            
1)       account-plugin-aim                                                                                      
2)       account-plugin-facebook                                                                                 
3)       account-plugin-flickr                                                                                   
4)       account-plugin-google                                                                                   
5)       account-plugin-identica                                                                                 
6)       account-plugin-jabber                                                                                   
7)       account-plugin-salut                                                                                    
8)       account-plugin-twitter                                                                                  
9)       account-plugin-windows-live                                                                             
10)      account-plugin-yahoo                                                                                    
11)      activity-log-manager-control-center                                                                     
12)      aisleriot                                                                                               
13)      alacarte                                                                                                
14)      apport-gtk                                                                                              
15)      apturl                                                                                                  
16)      audacious                                                                                               
17)      audacious-plugins                                                                                       
18)      bamfdaemon                                                                                              
19)      baobab                                                                                                  
20)      brasero                                                                                                 
21)      brasero-cdrkit                                                                                          
22)      compiz                                                                                                  
23)      compiz-gnome                                                                                            
24)      dconf-tools                                                                                             
25)      deja-dup                                                                                                
26)      deja-dup-backend-gvfs                                                                                   
27)      deja-dup-backend-ubuntuone                                                                              
28)      empathy                                                                                                 
29)      eog                                                                                                     
30)      evince                                                                                                  
31)      evolution-data-server                                                                                   
32)      file-roller                                                                                             
33)      gcalctool                                                                                               
34)      gconf-editor                                                                                            
35)      gcr                                                                                                     
36)      gdm                                                                                                     
37)      gedit                                                                                                   
38)      gir1.2-appindicator3-0.1                                                                                
39)      gir1.2-caribou-1.0                                                                                      
40)      gir1.2-clutter-1.0                                                                                      
41)      gir1.2-gcr-3                                                                                            
42)      gir1.2-gdata-0.0                                                                                        
43)      gir1.2-gkbd-3.0                                                                                         
44)      gir1.2-gnomebluetooth-1.0                                                                               
45)      gir1.2-gnomedesktop-3.0                                                                                 
46)      gir1.2-goa-1.0                                                                                          
47)      gir1.2-gtk-3.0                                                                                          
48)      gir1.2-gtksource-3.0                                                                                    
49)      gir1.2-mutter-3.0                                                                                       
50)      gir1.2-panelapplet-4.0                                                                                  
51)      gir1.2-peas-1.0                                                                                         
52)      gir1.2-rb-3.0                                                                                           
53)      gir1.2-totem-1.0                                                                                        
54)      gir1.2-ubuntuoneui-3.0                                                                                  
55)      gir1.2-vte-2.90                                                                                         
56)      gir1.2-webkit-3.0                                                                                       
57)      gir1.2-wnck-3.0                                                                                         
58)      gkbd-capplet                                                                                            
59)      gnome-applets                                                                                           
60)      gnome-bluetooth                                                                                         
61)      gnome-contacts                                                                                          
62)      gnome-control-center                                                                                    
63)      gnome-control-center-signon                                                                             
64)      gnome-control-center-unity                                                                              
65)      gnome-disk-utility                                                                                      
66)      gnome-font-viewer                                                                                       
67)      gnome-icon-theme                                                                                        
68)      gnome-icon-theme-full                                                                                   
69)      gnome-icon-theme-symbolic                                                                               
70)      gnome-keyring                                                                                           
71)      gnome-mahjongg                                                                                          
72)      gnome-media                                                                                             
73)      gnome-online-accounts                                                                                   
74)      gnome-orca                                                                                              
75)      gnome-panel                                                                                             
76)      gnome-power-manager                                                                                     
77)      gnome-screensaver                                                                                       
78)      gnome-screenshot                                                                                        
79)      gnome-session                                                                                           
80)      gnome-session-bin                                                                                       
81)      gnome-session-canberra                                                                                  
82)      gnome-session-fallback                                                                                  
83)      gnome-settings-daemon                                                                                   
84)      gnome-shell                                                                                             
85)      gnome-shell-extensions                                                                                  
86)      gnome-sudoku                                                                                            
87)      gnome-system-log                                                                                        
88)      gnome-system-monitor                                                                                    
89)      gnome-terminal                                                                                          
90)      gnome-themes-standard                                                                                   
91)      gnome-tweak-tool                                                                                        
92)      gnome-user-guide                                                                                        
93)      gnome-user-share                                                                                        
94)      gnomine                                                                                                 
95)      gstreamer1.0-clutter                                                                                    
96)      gtk3-engines-unico                                                                                      
97)      gucharmap                                                                                               
98)      gvfs-backends                                                                                           
99)      gwibber                                                                                                 
100)     gwibber-service-facebook                                                                                
101)     gwibber-service-identica                                                                                
102)     gwibber-service-twitter                                                                                 
103)     humanity-icon-theme                                                                                     
104)     ibus                                                                                                    
105)     ibus-gtk3                                                                                               
106)     ibus-pinyin                                                                                             
107)     ibus-table                                                                                              
108)     indicator-applet-complete                                                                               
109)     indicator-application                                                                                   
110)     indicator-appmenu                                                                                       
111)     indicator-datetime                                                                                      
112)     indicator-messages                                                                                      
113)     indicator-power                                                                                         
114)     indicator-printers                                                                                      
115)     indicator-session                                                                                       
116)     indicator-sound                                                                                         
117)     indicator-sync                                                                                          
118)     landscape-client-ui-install                                                                             
119)     language-selector-gnome                                                                                 
120)     libaccount-plugin-1.0-0                                                                                 
121)     libappindicator3-1                                                                                      
122)     libaudcore1                                                                                             
123)     libbamf3-1                                                                                              
124)     libbrasero-media3-1                                                                                     
125)     libcanberra-gtk3-0                                                                                      
126)     libcanberra-gtk3-module                                                                                 
127)     libcaribou0                                                                                             
128)     libclutter-1.0-0                                                                                        
129)     libclutter-gst-1.0-0                                                                                    
130)     libclutter-gst-2.0-0                                                                                    
131)     libclutter-gtk-1.0-0                                                                                    
132)     libcolord-gtk1                                                                                          
133)     libebackend-1.2-5                                                                                       
134)     libebackend-1.2-6                                                                                       
135)     libebook-1.2-14                                                                                         
136)     libecal-1.2-15                                                                                          
137)     libedata-book-1.2-15                                                                                    
138)     libedata-book-1.2-16                                                                                    
139)     libedata-cal-1.2-18                                                                                     
140)     libedata-cal-1.2-20                                                                                     
141)     libedataserver-1.2-17                                                                                   
142)     libevdocument3-4                                                                                        
143)     libevview3-3                                                                                            
144)     libfolks-eds25                                                                                          
145)     libgail-3-0                                                                                             
146)     libgcr-3-1                                                                                              
147)     libgdata13                                                                                              
148)     libgnome-bluetooth11                                                                                    
149)     libgnome-desktop-3-4                                                                                    
150)     libgnome-desktop-3-5                                                                                    
151)     libgnome-media-profiles-3.0-0                                                                           
152)     libgnomekbd8                                                                                            
153)     libgoa-1.0-0                                                                                            
154)     libgrip0                                                                                                
155)     libgtk-3-0                                                                                              
156)     libgtk-3-bin                                                                                            
157)     libgtkmm-3.0-1                                                                                          
158)     libgtksourceview-3.0-0                                                                                  
159)     libgtkspell-3-0                                                                                         
160)     libgucharmap-2-90-7                                                                                     
161)     libgweather-3-1                                                                                         
162)     libgweather-3-3                                                                                         
163)     libgwibber-gtk3                                                                                         
164)     libido3-0.1-0                                                                                           
165)     libindicator3-7                                                                                         
166)     libmutter0a                                                                                             
167)     libmx-1.0-2                                                                                             
168)     libnautilus-extension1a                                                                                 
169)     libnm-gtk0                                                                                              
170)     libpanel-applet-4-0                                                                                     
171)     libpeas-1.0-0                                                                                           
172)     librhythmbox-core6                                                                                      
173)     libsyncdaemon-1.0-1                                                                                     
174)     libtimezonemap1                                                                                         
175)     libtotem0                                                                                               
176)     libubuntuoneui-3.0-1                                                                                    
177)     libunity-core-6.0-5                                                                                     
178)     libunity-misc4                                                                                          
179)     libunity-webapps0                                                                                       
180)     libvte-2.90-9                                                                                           
181)     libwebkitgtk-3.0-0                                                                                      
182)     libwnck-3-0                                                                                             
183)     libyelp0                                                                                                
184)     light-themes                                                                                            
185)     lightdm-remote-session-freerdp                                                                          
186)     lightdm-remote-session-uccsconfigure                                                                    
187)     mcp-account-manager-uoa                                                                                 
188)     metacity                                                                                                
189)     mousetweaks                                                                                             
190)     mutter                                                                                                  
191)     nautilus                                                                                                
192)     nautilus-sendto                                                                                         
193)     nautilus-sendto-empathy                                                                                 
194)     nautilus-share                                                                                          
195)     network-manager-gnome                                                                                   
196)     network-manager-pptp-gnome                                                                              
197)     notification-daemon                                                                                     
198)     notify-osd                                                                                              
199)     onboard                                                                                                 
200)     oneconf                                                                                                 
201)     overlay-scrollbar                                                                                       
202)     overlay-scrollbar-gtk2                                                                                  
203)     overlay-scrollbar-gtk3                                                                                  
204)     pavucontrol                                                                                             
205)     policykit-1-gnome                                                                                       
206)     python-aptdaemon.gtk3widgets                                                                            
207)     python-ubuntu-sso-client                                                                                
208)     python-ubuntuone-control-panel                                                                          
209)     python3-aptdaemon.gtk3widgets                                                                           
210)     remmina                                                                                                 
211)     remmina-plugin-rdp                                                                                      
212)     remmina-plugin-vnc                                                                                      
213)     rhythmbox                                                                                               
214)     rhythmbox-mozilla                                                                                       
215)     rhythmbox-plugin-cdrecorder                                                                             
216)     rhythmbox-plugin-magnatune                                                                              
217)     rhythmbox-plugin-zeitgeist                                                                              
218)     rhythmbox-plugins                                                                                       
219)     rhythmbox-ubuntuone                                                                                     
220)     seahorse                                                                                                
221)     sessioninstaller                                                                                        
222)     shotwell                                                                                                
223)     simple-scan                                                                                             
224)     software-center                                                                                         
225)     software-properties-gtk                                                                                 
226)     stormcloud                                                                                              
227)     synaptic                                                                                                
228)     system-config-printer-gnome                                                                             
229)     telepathy-indicator                                                                                     
230)     thunderbird-gnome-support                                                                               
231)     totem                                                                                                   
232)     totem-mozilla                                                                                           
233)     totem-plugins                                                                                           
234)     transmission-gtk                                                                                        
235)     ubuntu-artwork                                                                                          
236)     ubuntu-desktop                                                                                          
237)     ubuntu-docs                                                                                             
238)     ubuntu-mono                                                                                             
239)     ubuntu-release-upgrader-gtk                                                                             
240)     ubuntu-sso-client                                                                                       
241)     ubuntu-sso-client-qt                                                                                    
242)     ubuntuone-client                                                                                        
243)     ubuntuone-client-gnome                                                                                  
244)     ubuntuone-control-panel                                                                                 
245)     ubuntuone-control-panel-qt                                                                              
246)     unity                                                                                                   
247)     unity-asset-pool                                                                                        
248)     unity-greeter                                                                                           
249)     unity-lens-photos                                                                                       
250)     unity-scope-gdocs                                                                                       
251)     unity-scope-gdrive                                                                                      
252)     unity-scope-musicstores                                                                                 
253)     unity-services                                                                                          
254)     unity-webapps-common                                                                                    
255)     unity-webapps-service                                                                                   
256)     update-manager                                                                                          
257)     update-notifier                                                                                         
258)     usb-creator-gtk                                                                                         
259)     vino                                                                                                    
260)     xdg-user-dirs-gtk                                                                                       
261)     xdiagnose                                                                                               
262)     xul-ext-unity                                                                                           
263)     xul-ext-websites-integration                                                                            
264)     yelp                                                                                                    
265)     zenity                                                                                                  

       Keep the following packages at their current version:                                                     
266)     account-plugin-empathy [Not Installed]                                                                  

       Leave the following dependencies unresolved:                                                              
267)     gksu recommends gnome-keyring                                                                           
268)     gnome-screensaver recommends gnome-power-manager | xfce4-power-manager                                  
269)     gvfs-daemons recommends policykit-1-gnome                                                               
270)     gwibber-service recommends gwibber-service-facebook                                                     
271)     gwibber-service recommends gwibber-service-twitter                                                      
272)     gwibber-service recommends gwibber-service-identica                                                     
273)     ibus recommends ibus-gtk3 | ibus-qt4 | ibus-clutter                                                     
274)     libaccount-plugin-1.0-0 recommends gnome-control-center-signon                                          
275)     libappindicator1 recommends indicator-application (>= 0.2.93)                                           
276)     libappindicator3-1 recommends indicator-application (>= 0.2.93)                                         
277)     libfolks25 recommends libfolks-eds25                                                                    
278)     libnotify4 recommends notification-daemon                                                               
279)     lightdm recommends unity-greeter | lightdm-greeter | lightdm-kde-greeter                                
280)     metacity recommends gnome-session | x-session-manager                                                   
281)     network-manager recommends network-manager-gnome | network-manager-kde | plasma-widget-networkmanagement
282)     network-manager-pptp recommends network-manager-pptp-gnome | plasma-widget-networkmanagement            
283)     onboard recommends gir1.2-appindicator3-0.1                                                             
284)     oneconf recommends software-center (>= 4.1.21)                                                          
285)     oneconf recommends update-notifier (>= 0.103)                                                           
286)     remmina-common recommends remmina                                                                       
287)     rhythmbox recommends notification-daemon                                                                
288)     rhythmbox recommends gvfs-backends                                                                      
289)     rhythmbox-data recommends rhythmbox                                                                     
290)     shotwell recommends account-plugin-facebook                                                             
291)     shotwell recommends account-plugin-google                                                               
292)     shotwell recommends account-plugin-flickr                                                               
293)     software-center recommends sessioninstaller                                                             
294)     ubuntu-desktop recommends activity-log-manager-control-center                                           
295)     ubuntu-desktop recommends aisleriot                                                                     
296)     ubuntu-desktop recommends apport-gtk                                                                    
297)     ubuntu-desktop recommends brasero                                                                       
298)     ubuntu-desktop recommends deja-dup                                                                      
299)     ubuntu-desktop recommends deja-dup-backend-ubuntuone                                                    
300)     ubuntu-desktop recommends gnome-bluetooth                                                               
301)     ubuntu-desktop recommends gnome-orca                                                                    
302)     ubuntu-desktop recommends gnome-screensaver                                                             
303)     ubuntu-desktop recommends gnomine                                                                       
304)     ubuntu-desktop recommends gwibber                                                                       
305)     ubuntu-desktop recommends ibus-gtk3                                                                     
306)     ubuntu-desktop recommends landscape-client-ui-install                                                   
307)     ubuntu-desktop recommends mousetweaks                                                                   
308)     ubuntu-desktop recommends nautilus-share                                                                
309)     ubuntu-desktop recommends network-manager-gnome                                                         
310)     ubuntu-desktop recommends network-manager-pptp-gnome                                                    
311)     ubuntu-desktop recommends onboard                                                                       
312)     ubuntu-desktop recommends overlay-scrollbar                                                             
313)     ubuntu-desktop recommends remmina                                                                       
314)     ubuntu-desktop recommends rhythmbox                                                                     
315)     ubuntu-desktop recommends rhythmbox-plugin-magnatune                                                    
316)     ubuntu-desktop recommends rhythmbox-ubuntuone                                                           
317)     ubuntu-desktop recommends shotwell                                                                      
318)     ubuntu-desktop recommends simple-scan                                                                   
319)     ubuntu-desktop recommends totem                                                                         
320)     ubuntu-desktop recommends totem-mozilla                                                                 
321)     ubuntu-desktop recommends transmission-gtk                                                              
322)     ubuntu-release-upgrader-gtk recommends gir1.2-webkit-3.0                                                
323)     ubuntuone-client recommends indicator-sync                                                              
324)     unity-greeter recommends indicator-application                                                          
325)     unity-greeter recommends indicator-datetime                                                             
326)     unity-greeter recommends indicator-power                                                                
327)     unity-greeter recommends indicator-session                                                              
328)     unity-greeter recommends indicator-sound                                                                
329)     unity-greeter recommends network-manager-gnome                                                          
330)     update-manager recommends software-properties-gtk (>= 0.71.2)                                           
331)     update-notifier recommends apport-gtk (>= 2.8-0ubuntu3)                                                 
332)     update-notifier recommends software-properties-gtk                                                      
333)     audacious-plugins recommends audacious (>= 2.4.3)                                                       
334)     audacious-plugins-data recommends audacious-plugins                                                     
335)     gnome-applets recommends gnome-media                                                                    
336)     gnome-applets recommends policykit-1-gnome                                                              
337)     gnome-panel recommends gnome-applets                                                                    
338)     gnome-panel-data recommends gnome-panel                                                                 
339)     indicator-applet-complete recommends indicator-session                                                  
340)     indicator-applet-complete recommends indicator-messages                                                 
341)     indicator-applet-complete recommends indicator-sound                                                    
342)     indicator-applet-complete recommends indicator-application                                              
343)     file-roller recommends sessioninstaller | packagekit                                                    
344)     gedit-common recommends gedit                                                                           
345)     gnome-control-center recommends gnome-online-accounts                                                   
346)     gnome-control-center recommends mousetweaks                                                             
347)     gnome-control-center recommends policykit-1-gnome                                                       
348)     nautilus recommends brasero (>= 2.26)                                                                   
349)     nautilus recommends gvfs-backends                                                                       
350)     gnome-terminal-data recommends gnome-terminal                                                           
351)     alacarte recommends gnome-panel | exo-utils                                                             
352)     empathy recommends gvfs-backends                                                                        
353)     empathy recommends telepathy-indicator                                                                  
354)     libpam-gnome-keyring recommends gnome-keyring                                                           
355)     gnome-shell recommends gnome-control-center                                                             
356)     gnome-shell recommends gnome-user-guide                                                                 
357)     empathy-common recommends yelp                                                                          
358)     nautilus-sendto-empathy recommends nautilus-sendto (>= 2.28.2-2)                                        
359)     libgtk-3-common recommends libgtk-3-0                                                                   
360)     gnome-control-center-data recommends gnome-control-center (>= 1:3.7.4-0ubuntu1~raring2)                 
361)     gnome-session-fallback recommends gnome-power-manager                                                   
362)     mcp-account-manager-uoa recommends gnome-control-center-signon                                          
363)     mcp-account-manager-uoa recommends account-plugin-empathy                                               
364)     mcp-account-manager-uoa recommends account-plugin-google                                                
365)     mcp-account-manager-uoa recommends account-plugin-facebook                                              
366)     mcp-account-manager-uoa recommends account-plugin-windows-live                                          
367)     unity recommends gnome-control-center-unity                                                             
368)     unity recommends indicator-application                                                                  
369)     unity recommends indicator-sound                                                                        
370)     unity recommends indicator-datetime                                                                     
371)     unity recommends indicator-messages                                                                     
372)     unity recommends indicator-power                                                                        
373)     unity recommends indicator-session                                                                      
374)     unity recommends indicator-sync                                                                         
375)     indicator-appmenu recommends indicator-applet | indicator-renderer                                      
376)     unity-lens-files recommends unity-scope-gdrive                                                          
377)     unity-lens-music recommends unity-scope-musicstores                                                     
378)     indicator-printers recommends indicator-applet (>= 0.2) | indicator-renderer                            
379)     unity-lens-photos recommends account-plugin-flickr                                                      
380)     unity-lens-photos recommends account-plugin-google                                                      
381)     unity-lens-photos recommends account-plugin-facebook                                                    


Accept this solution? [Y/n/q/?] 
```


For a joke at the end (I have not seen this error from early DOS times)
```
:~$ sudo aptitude safe-upgrade 
Resolving dependencies...                
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring_universe_binary-amd64_Packages - open (24: Too many open files)
E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring_restricted_binary-amd64_Packages - open (24: Too many open files)
E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring_main_binary-amd64_Packages - open (24: Too many open files)
E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring_universe_binary-amd64_Packages - open (24: Too many open files)
E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring_restricted_binary-amd64_Packages - open (24: Too many open files)
E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring_main_binary-amd64_Packages - open (24: Too many open files)
                                         
E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring_multiverse_binary-amd64_Packages - open (24: Too many open files)
E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring_universe_binary-amd64_Packages - open (24: Too many open files)
E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring_restricted_binary-amd64_Packages - open (24: Too many open files)
E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring_main_binary-amd64_Packages - open (24: Too many open files)
```...

---

### Post by Harry33 on 2013-02-03
> **hugmenot said:**
> [This commit]("http://git.gnome.org/browse/gnome-settings-daemon/commit/?id=b69b0d99fdc5319a809299146d281cfd06bf82e9") is also really stupid.

They bind the F2 key to mute the microphone, and write in the commit message they want to bind F20 for testing. But what they actually bound was F2, so now one cannot use F2 anymore.

This is fixed now.

---

### Post by Mr.JJ on 2013-02-03
I upgraded to the 13.04 from 12.10 yesterday, process was smooth. Then enabled the staging repo and updated/upgraded; shell, control ceter etc. were held back. So, did a distro upgrade, and was asked to remove 3/4 account plugins (aim/jabber/yahoo etc.), and no other removals.

Now when I shutdown, the screen goes blank, just like it is shutting down, but the hard disk keep working and the laptop is still powered on. Any ideas?

Also how to remove the metacity based fallback/classic session (when I remove metacity it also wants to remove gnome-shell)?

---

### Post by Harry33 on 2013-02-03
> **Mr.JJ said:**
> I upgraded to the 13.04 from 12.10 yesterday, process was smooth. Then enabled the staging repo and updated/upgraded; shell, control ceter etc. were held back. So, did a distro upgrade, and was asked to remove 3/4 account plugins (aim/jabber/yahoo etc.), and no other removals.

Now when I shutdown, the screen goes blank, just like it is shutting down, but the hard disk keep working and the laptop is still powered on. Any ideas?

Also how to remove the metacity based fallback/classic session (when I remove metacity it also wants to remove gnome-shell)?

You already opened a separate thread on this one.
[http://ubuntuforums.org/showthread.php?t=2111918](http://ubuntuforums.org/showthread.php?t=2111918)

---

### Post by VinDSL on 2013-02-03
I've been having an uber-irritating problem with Nautilus "3.7.4-0ubuntu1~raring1" the past week or so.

Anyone else experiencing the problem below?!?!?

This Nautilus 3.7.4 package is from the Gnome 3 Staging PPA...

```
vindsl@Zuul:~$ apt-cache policy nautilus
nautilus:
  Installed: 1:3.7.4-0ubuntu1~raring1
  Candidate: 1:3.7.4-0ubuntu1~raring1
  Version table:
 *** 1:3.7.4-0ubuntu1~raring1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
     1:3.6.3-0ubuntu5 0
        500 http://mirror.hmc.edu/ubuntu/ raring/main i386 Packages
     1:3.5.90.really.3.4.2-0ubuntu4.1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/main i386 Packages
     1:3.5.90.really.3.4.2-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main i386 Packages
vindsl@Zuul:~$ 
```


Sometimes a pic is worth 1000 words...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-3-feb-2013-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-3-feb-2013-2.png")[/INDENT]


What I've done here is:

[LIST]
[*]Opened Nautilus 3.7.4
[*]Randomly picked a file (any file works for POC)
[*]Right-clicked the "Properties" on .conkyrc
[/LIST]

As you can see, the filename (.conkyrc) is highlighted, by default.  This is normal.

However, if I place the mouse pointer on the highlighted name, and click it (any mouse button), Nautilus will crash and disappear.

Can someone try this, and let me know if Nautilus 3.7.4 crashes n' burns for you too, when you click the "Name" in "Basic Properties"?

Not sure if it's a bug, or something is janky with my install...

Thanks!  ;)

---

### Post by Mr.JJ on 2013-02-04
> **Harry33 said:**
> You already opened a separate thread on this one. 
Posted here since this is the gnome staging ppa thread and to know if anyone else here is facing the same issue.  

Any of you still have metacity installed? I thought that was supposed to be removed with the 3.8. When I try to remove it, shell is also going to be removed. Shell still has a dependency on metacity?

---

### Post by kansasnoob on 2013-02-04
> **Mr.JJ said:**
> Posted here since this is the gnome staging ppa thread and to know if anyone else here is facing the same issue.  

Any of you still have metacity installed? I thought that was supposed to be removed with the 3.8. When I try to remove it, shell is also going to be removed. Shell still has a dependency on metacity?

Do you have both the Gnome3 and Gnome3 Staging PPA's installed:

[https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=raring](https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=raring)

[https://launchpad.net/~gnome3-team/+archive/gnome3-staging](https://launchpad.net/~gnome3-team/+archive/gnome3-staging)

You need 'gnome-desktop3' package from the standard PPA in order for "staging" to work right.

---

### Post by Mr.JJ on 2013-02-04
> **kansasnoob said:**
> Do you have both the Gnome3 and Gnome3 Staging PPA's installed......
You need 'gnome-desktop3' package from the standard PPA in order for "staging" to work right.
No, I don't. But there is a gnome-desktop3 package in the staging ppa and I read somewhere that staging is now independent of gnome3 ppa.

Anyways, I will try your suggestion and will let you know the results, thanks.

---

### Post by kansasnoob on 2013-02-04
> **kansasnoob said:**
> Do you have both the Gnome3 and Gnome3 Staging PPA's installed:

[https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=raring](https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=raring)

[https://launchpad.net/~gnome3-team/+archive/gnome3-staging](https://launchpad.net/~gnome3-team/+archive/gnome3-staging)

You need 'gnome-desktop3' package from the standard PPA in order for "staging" to work right.

I'd been curious how this would react with [Rico's testing PPA]("https://launchpad.net/~ricotz/+archive/testing?field.series_filter=raring") so I took a look:

```
lance@lance-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
[B][COLOR="Red"]The following NEW packages will be installed:
  alacarte gir1.2-panelapplet-4.0 gnome-applets gnome-applets-data gnome-panel
  gnome-panel-data gnome-session-fallback libmozjs188-1.0[/COLOR][/B]
The following packages will be upgraded:
  gir1.2-atk-1.0 gir1.2-clutter-1.0 gir1.2-clutter-gst-2.0 gir1.2-freedesktop
  gir1.2-gdesktopenums-3.0 gir1.2-glib-2.0 gir1.2-gtk-3.0 gir1.2-mutter-3.0
  gir1.2-rb-3.0 gjs gnome-accessibility-themes gnome-icon-theme-symbolic
  gnome-shell gnome-shell-common gnome-shell-extensions gnome-sushi
  gnome-themes-standard gnome-themes-standard-data gsettings-desktop-schemas
  gstreamer1.0-clutter gtk2-engines-pixbuf libatk1.0-0 libatk1.0-data
  libclutter-1.0-0 libclutter-1.0-common libclutter-gst-2.0-0 libgail-3-0
  libgail-common libgail18 libgirepository-1.0-1 libgjs0c libglib2.0-0
  libglib2.0-bin libglib2.0-data libgtk-3-0 libgtk-3-bin libgtk-3-common
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libmutter0a librhythmbox-core6
  mutter mutter-common rhythmbox rhythmbox-data rhythmbox-mozilla
  rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins
51 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 49.7 MB/49.8 MB of archives.
After this operation, 77.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

So make sure you have the correct PPA(s) installed ;)

I'm dieing to take a look at Gnome 3.7.5 because I think it'll include the first look at the new "gnome-classic" :D

---

### Post by kansasnoob on 2013-02-04
> **Mr.JJ said:**
> No, I don't. But there is a gnome-desktop3 package in the staging ppa and I read somewhere that staging is now independent of gnome3 ppa.

Anyways, I will try your suggestion and will let you know the results, thanks.

Just FYI you can see what PPA's you have installed like this:

```
ls /etc/apt/sources.list.d
```

```
lance@lance-desktop:~$ ls /etc/apt/sources.list.d
gnome3-team-gnome3-raring.list
gnome3-team-gnome3-raring.list.save
gnome3-team-gnome3-staging-raring.list
gnome3-team-gnome3-staging-raring.list.save
ricotz-testing-raring.list

```

Unless you directly edited "/etc/apt/sources.list" which is now kind of frowned upon :)

Right now I'm purging "ricotz-testing-raring.list" because it's not what I want.

---

### Post by kansasnoob on 2013-02-04
Just adding, I'd also NOT use [Rico's Staging PPA]("https://launchpad.net/~ricotz/+archive/staging?field.series_filter=raring") since it depends on:

> WHILE USING THIS PPA MAKE SURE YOU ALSO ADDED THE GNOME3 PPA AND GNOME TESTING PPA!
ppa:gnome3-team/gnome3 ([https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3))
**[COLOR="Red"]ppa:ricotz/testing[/COLOR]** ([https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing))

So it's wait and see :D

I suppose the two different "staging" PPA's can be confusing :confused:

---

### Post by Mr.JJ on 2013-02-04
> **kansasnoob said:**
> I'd been curious how this would react with [Rico's testing PPA]("https://launchpad.net/~ricotz/+archive/testing?field.series_filter=raring") so I took a look:........
[B][COLOR=Red]The following NEW packages will be installed:
  alacarte gir1.2-panelapplet-4.0 gnome-applets gnome-applets-data gnome-panel
  gnome-panel-data gnome-session-fallback libmozjs188-1.0[/COLOR][/B]...........


Okay, my mistake.  Just checked and I do not have gnome session fallback (or panel/applets...) installed. It is just the metacity that is kept back and I guess this is the case with everyone (since u r not offered to install metacity with fallback session).  I don't know why (or where) there is still a dependency on metacity.

Also, the issue with shutdown must be something different then.

---

### Post by Mr.JJ on 2013-02-04
> **kansasnoob said:**
> .....I suppose the two different "staging" PPA's can be confusing :confused:

It is. Until a couple of pages back in this thread, I thought that everyone was talking about the ricotz staging ppa and wondered why I don't see many packages in there. 
Also the ricotz  ppas (testing and staging) are quite unstable. It actually broke my 12.10 install and I had to reinstall.

---

### Post by kansasnoob on 2013-02-04
> **Mr.JJ said:**
> It is. Until a couple of pages back in this thread, I thought that everyone was talking about the ricotz staging ppa and wondered why I don't see many packages in there. 
Also the ricotz  ppas (testing and staging) are quite unstable. It actually broke my 12.10 install and I had to reinstall.

If you're willing to try something that might blow things up run:

```
sudo apt-get install ubuntu-gnome-desktop
```

Then just select (n) and post the full output :)

ATM I don't think you can get an actual "gnome-session" to coexist peacefully with Ubuntu's Unity :(

But performance of an actual Ubuntu session has been so flaky for me since Precise that I've almost given up on Unity ever working right again.

---

### Post by Mr.JJ on 2013-02-04
> **kansasnoob said:**
> If you're willing to try something that might blow things up run:
```
sudo apt-get install ubuntu-gnome-desktop
```Then just select (n) and post the full output :)
ATM I don't think you can get an actual "gnome-session" to coexist peacefully with Ubuntu's Unity :(

Since I upgraded from ubuntu-gnome, no unity here and have the latest version installed :(
```
ubuntu-gnome-desktop is already the newest version.

```

---

### Post by VinDSL on 2013-02-04
> **kansasnoob said:**
> If you're willing to try something that might blow things up run:

```
sudo apt-get install ubuntu-gnome-desktop
```

Then just select (n) and post the full output :)



OMG!!!  LoL!  :D


```
vindsl@Zuul:~$ sudo apt-get install ubuntu-gnome-desktop
[sudo] password for vindsl: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  gir1.2-indicate-0.7
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview apturl
  deja-dup-backend-cloudfiles deja-dup-backend-s3 epiphany-browser
  epiphany-browser-data fonts-lklug-sinhala fonts-lyx fonts-sil-abyssinica
  fonts-sil-padauk fonts-tibetan-machine gnumeric gnumeric-common gnumeric-doc
  gstreamer0.10-alsa gwibber im-config itstool libabiword-2.9 libgdome2-0
  libgdome2-cpp-smart0c2a libgoffice-0.10-10 libgoffice-0.10-10-common
  libgtkmathview0c2a libgtkspell-3-0 libgwibber-gtk3 liblink-grammar4
  libloudmouth1-0 libots0 libpam-xdg-support libproxy1-plugin-gsettings
  libproxy1-plugin-networkmanager libtidy-0.99-0 libwhoopsie0 libwv-1.2-4
  link-grammar-dictionaries-en linux-headers-3.8.0-4
  linux-headers-3.8.0-4-generic linux-headers-generic
  linux-headers-generic-pae nautilus-share oneconf-common
  plymouth-theme-ubuntu-gnome-logo plymouth-theme-ubuntu-gnome-text
  pulseaudio-module-bluetooth pulseaudio-module-gconf python-boto
  python-cloudfiles python-debtagshw python-oneconf python3-aptdaemon.pkcompat
  software-center software-center-aptdaemon-plugins
  ubuntu-gnome-default-settings ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk update-manager update-manager-core
  update-notifier whoopsie yelp-tools
Suggested packages:
  epiphany-extensions libgraphite3 pango-graphite gnumeric-plugins-extra
  gwibber-service-flickr gwibber-service-statusnet gwibber-service-foursquare
Recommended packages:
  rhythmbox-plugin-magnatune
The following packages will be REMOVED:
  gnome gnome-core gnome-packagekit gnome-software-manager gnome-update-viewer
  im-switch packagekit packagekit-tools
The following NEW packages will be installed:
  abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview apturl
  deja-dup-backend-cloudfiles deja-dup-backend-s3 epiphany-browser
  epiphany-browser-data fonts-lklug-sinhala fonts-lyx fonts-sil-abyssinica
  fonts-sil-padauk fonts-tibetan-machine gnumeric gnumeric-common gnumeric-doc
  gstreamer0.10-alsa gwibber im-config itstool libabiword-2.9 libgdome2-0
  libgdome2-cpp-smart0c2a libgoffice-0.10-10 libgoffice-0.10-10-common
  libgtkmathview0c2a libgtkspell-3-0 libgwibber-gtk3 liblink-grammar4
  libloudmouth1-0 libots0 libpam-xdg-support libproxy1-plugin-gsettings
  libproxy1-plugin-networkmanager libtidy-0.99-0 libwhoopsie0 libwv-1.2-4
  link-grammar-dictionaries-en linux-headers-3.8.0-4
  linux-headers-3.8.0-4-generic linux-headers-generic
  linux-headers-generic-pae nautilus-share oneconf-common
  plymouth-theme-ubuntu-gnome-logo plymouth-theme-ubuntu-gnome-text
  pulseaudio-module-bluetooth pulseaudio-module-gconf python-boto
  python-cloudfiles python-debtagshw python-oneconf python3-aptdaemon.pkcompat
  software-center software-center-aptdaemon-plugins
  ubuntu-gnome-default-settings ubuntu-gnome-desktop
  ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk update-manager
  update-manager-core update-notifier whoopsie yelp-tools
0 upgraded, 65 newly installed, 8 to remove and 7 not upgraded.
Need to get 46.9 MB of archives.
After this operation, 170 MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
vindsl@Zuul:~$ 

```

---

### Post by Mr.JJ on 2013-02-04
Do any of you get the file search working from within the shell? The search options are set and even when I do a file search from tracker and from within the nautilus I get the files I am looking for.

But if I do the shell search I don't see the files. I don't see any files at all in the shell. I see folders, pictures/documents etc.,  listed (though I disabled both folders - in the search settings) but not the actual files. Anyone any different?

By the way the recursive search is working again in nautilus, which is awesome but not really fast.

---

### Post by kansasnoob on 2013-02-04
> **Mr.JJ said:**
> Since I upgraded from ubuntu-gnome, no unity here and have the latest version installed :(
```
ubuntu-gnome-desktop is already the newest version.

```

Jeremy Bicha would have to confirm this .... or call me a liar ;) .... but I don't think Ubuntu GNOME Remix has an official upgrade path as yet, at least it hasn't been thoroughly tested, so I wonder if things just got borked during the upgrade :confused:

I could be all wet though :redface:

I'd just expected an output similar to what *VinDSL* posted, in hopes that we could parse any missing depends or recommends.

---

### Post by mc4man on 2013-02-04
I'm wondering why tracker is a dependency of ubuntu-gnome-desktop? Don't see anything using it, it's disabled in nautilus & Videos (totem) doesn't have grilo support (libtracker-sparql-

It's shown issues in 12.10 with cpu usage, as far as 13.04 don't know cause I'm not using anymore (GS

---

### Post by Mr.JJ on 2013-02-05
> **kansasnoob said:**
> Jeremy Bicha would have to confirm this .... or call me a liar ;) .... but I don't think Ubuntu GNOME Remix has an official upgrade path as yet, at least it hasn't been thoroughly tested, so I wonder if things just got borked during the upgrade :confused:


Wonderful! So am I officially the first person on earth who upgraded ubuntu gnome? Can I have my certificate please?

Seriously, that might be the issue in here. But I can confirm that most of it went fine and smooth. The process worked as it should. The ppa got disabled, upgraded the packages (with just the ubuntu gnome packages, no unity), the new usc etc. were installed and no packages removed (I guess I removed the gnome session fallback sometime back). The new system works fine (except ofcourse shutdown and auto-lock screen).

---

### Post by Mr.JJ on 2013-02-05
> **mc4man said:**
> I'm wondering why tracker is a dependency of ubuntu-gnome-desktop? Don't see anything using it.........It's shown issues in 12.10 with cpu usage, as far as 13.04 don't know cause I'm not using anymore (GS

In a way, you make sense here. Tracker still uses high cpu cycles (96-100 %) and now we have application spcific search enabled in shell. But I read it somewhere that the results in the shell from nautilus still depends on the tracker (though the search within nautilus uses a diff backend). I could very well be wrong though. But apart from that tracker is pretty much useless (in my usecase at least)

---

### Post by VinDSL on 2013-02-05
> **VinDSL said:**
> I've been having an uber-irritating problem with Nautilus "3.7.4-0ubuntu1~raring1" the past week or so.

Anyone else experiencing the problem below?!?!?

I pinned-down this problem further...

Nautilus disappears when I'm looking at the properties on a remoter server (only).

If I click on the filename of the above pic (in Atlanta) Nautilus crashes n' burns.

If I click on it locally, Nautilus works fine...

---

### Post by Harry33 on 2013-02-06
We have some new 3.7.5 version packages in this Gnome3 Staging PPA now.
Working fine.

gnome-shell, mutter, gnome-control-center, gnome-settings-daemon and gnome-desktop3

---

### Post by kansasnoob on 2013-02-06
> **Harry33 said:**
> We have some new 3.7.5 version packages in this Gnome3 Staging PPA now.
Working fine.

gnome-shell, mutter, gnome-control-center, gnome-settings-daemon and gnome-desktop3

With those latest updates gdm is now working better than it has since I first began testing Raring + the staging PPA.

But I notice that gnome-tweak-tool once again fails to launch, and my previously installed extensions fail to work ............... oooh, uh, oh, just thought to check something :)

EDIT: I was being a dummy, I was logged into GNOME Classic :oops:

So logged into the standard GNOME session gnome-tweak-tool does launch okay, but it shows no shell theme, and therefore no extensions:

[ATTACH]231076[/ATTACH]

[ATTACH]231077[/ATTACH]

---

### Post by Harry33 on 2013-02-06
> **kansasnoob said:**
> With those latest updates gdm is now working better than it has since I first began testing Raring + the staging PPA.

But I notice that gnome-tweak-tool once again fails to launch, and my previously installed extensions fail to work ............... oooh, uh, oh, just thought to check something :)

EDIT: I was being a dummy, I was logged into GNOME Classic :oops:

So logged into the standard GNOME session gnome-tweak-tool does launch okay, but it shows no shell theme, and therefore no extensions:


We need to wait for gnome-shell-extensions_3.7.5

---

### Post by Mr.JJ on 2013-02-06
With the latest updates (3.7.5), shutdown, autolock are working fine again. (shutdown started working yesterday after gnome settings daemon update).

---

### Post by jbicha on 2013-02-06
> **Harry33 said:**
> We need to wait for gnome-shell-extensions_3.7.5

…which is now in the staging PPA. The GNOME Classic mode is surprisingly good for their first release.

---

### Post by Mr.JJ on 2013-02-06
> **Harry33 said:**
> We need to wait for gnome-shell-extensions_3.7.5

Or update the metadata? All extensions are working fine here. (Except 'search recently used files' extension, which doesn't seem to work with 3.7 branch due to the changes in Shell search)

---

### Post by VinDSL on 2013-02-06
> **Harry33 said:**
> We have some new 3.7.5 version packages in this Gnome3 Staging PPA now.

> **Harry33 said:**
> We need to wait for gnome-shell-extensions_3.7.5

> **jbicha said:**
> &#8230;which is now in the staging PPA.
Astonishing improvement!

The Applications Menu is actually usable now...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-7-feb-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-7-feb-2013-1.png")[/INDENT]

---

### Post by jppr on 2013-02-07
Maybe a silly question ... But why Gnome is not updated in the official repos :(

---

### Post by Mr.JJ on 2013-02-07
> **VinDSL said:**
> Astonishing improvement! The Applications Menu is actually usable now...  The network icon (in the panel) just went missing. Anyone else has this issue?   @VinDSL, In you screenshot I don't see it either.

---

### Post by jbicha on 2013-02-07
> **Mr.JJ said:**
> The network icon (in the panel) just went missing. Anyone else has this issue?   @VinDSL, In you screenshot I don't see it either.

That's fixed in [        ]("https://launchpad.net/%7Egnome3-team/+archive/gnome3-staging/+sourcepub/2967771/+listing-archive-extra")gnome-shell - 3.7.5-0ubuntu1~raring2 which should build shortly (or you can install gir1.2-nmgtk-1.0 manually).

---

### Post by kansasnoob on 2013-02-07
> **jbicha said:**
> …which is now in the staging PPA. The GNOME Classic mode is surprisingly good for their first release.

This is pretty good. I think a workspace switcher would be nice though ;)

And it'll take a while to find all of the new config files so I can start breaking things :D

---

### Post by kansasnoob on 2013-02-07
> **jppr said:**
> Maybe a silly question ... But why Gnome is not updated in the official repos :(

Raring will still use GNOME 3.6 because 3.8 isn't released until March and Raring is released in April, so there wouldn't be sufficient time to sync and test all of the changes.

---

### Post by VinDSL on 2013-02-07
> **Mr.JJ said:**
> The network icon (in the panel) just went missing. Anyone else has this issue?   @VinDSL, In you screenshot I don't see it either.
Some of the buttons are AWOL, on the panel.  

Maybe they renamed something-or-another, or the paths have changed.  I haven't had a chance to dig into it.  But, nothing is missing that I care about.

Also, it could be theme related.  The theme I'm running is pretty old -- amazing it works at all.

I got rid of the date & time button again.  Evidently, the update overwrote my modded "panel.js" file.  Anyway, that was my doing...

I'm sure the panel buttons will be back, sooner or later.  ;)

---

### Post by VinDSL on 2013-02-07
> **jbicha said:**
> That's fixed in [        ]("https://launchpad.net/%7Egnome3-team/+archive/gnome3-staging/+sourcepub/2967771/+listing-archive-extra")gnome-shell - 3.7.5-0ubuntu1~raring2 which should build shortly (or you can install gir1.2-nmgtk-1.0 manually).
Oops!  Should have kept reading.

Sorry...  :)

**EDIT**

Upgraded, and the network button is back.  Thanks!

Activities button is still missing -- but the hot corner works.  Just saying.

I have a *feeling* the activities button is hiding underneath the apps & places buttons.

I'm getting into Plank, anyway...  ;)

---

### Post by pferraro on 2013-02-07
The AMD64 build of gnome-shell-3.7.5-0ubuntu1~raring2 from the GNOME3 staging PPA still doesn't install for me.  Looking at the control file, it has a unfulfilled dependency on "libgjs0-libmozjs185-1.0".
However, the version from the ricotz testing ppa does install.

---

### Post by jbicha on 2013-02-07
> **pferraro said:**
> The AMD64 build of gnome-shell-3.7.5-0ubuntu1~raring2 from the GNOME3 staging PPA still doesn't install for me.  Looking at the control file, it has a unfulfilled dependency on "libgjs0-libmozjs185-1.0".
However, the version from the ricotz testing ppa does install.

That's because the ricotz testing PPA has migrated to mozjs188 and the GNOME3 Staging PPA has not.

---

### Post by Harry33 on 2013-02-08
> **pferraro said:**
> The AMD64 build of gnome-shell-3.7.5-0ubuntu1~raring2 from the GNOME3 staging PPA still doesn't install for me.  Looking at the control file, it has a unfulfilled dependency on "libgjs0-libmozjs185-1.0".
However, the version from the ricotz testing ppa does install.

Do not use the Gnome3 Staging PPA and the Ricotz Testing PPA at the same time.

---

### Post by ricotz on 2013-02-08
> **Harry33 said:**
> Do not use the Gnome3 Staging PPA and the Ricotz Testing PPA at the same time.

It is fine to use both if you keep your eyes open on updates. ;-)

---

### Post by VinDSL on 2013-02-08
> **ricotz said:**
> It is fine to use both if you keep your eyes open on updates. ;-)
That's what I've been doing... 

I started using the 'open-eyes' method of updating, back when the x-edger's PPA would bork my install, from time-to-time.  It was best to check for suitable updates, and apply them accordingly.  Blindly upgrading edger's was asking for trouble.

Speaking of updates...


[INDENT]**[COLOR="DarkRed"]Ubuntu 13.04 / Linux 3.8-rc6 / Gnome-Shell 3.7.5 (Staging) / Plank / Conky / ACYL / Chromium Canary[/COLOR]**

[[IMG]http://vindsl.com/images/vindsl-desktop-8-feb-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-8-feb-2013-1.png")[/INDENT]


The button icons, on the left-side of the panel are missing, otherwise everything is working fine...

---

### Post by kansasnoob on 2013-02-08
Does anyone happen to know where the config files reside for the new gnome-classic?

I don't see anything in dconf-editor, the only thing I've found so far is /usr/share/gnome-session/sessions/gnome-classic.session:

```
[GNOME Session]
Name=GNOME Classic
Name[ar]=&#1580;&#1606;&#1608;&#1605; &#1578;&#1602;&#1604;&#1610;&#1583;&#1610;&#1577;
Name[cs]=GNOME klasik
Name[es]=GNOME clásico
Name[gl]=GNOME clasico
Name[hu]=Klasszikus GNOME
Name[lt]=Klasikinis GNOME
Name[pl]=Klasyczne GNOME
Name[ru]=&#1058;&#1088;&#1072;&#1076;&#1080;&#1094;&#1080;&#1086;&#1085;&#1085;&#1099;&#1081; GNOME
Name[sl]=Obi&#269;ajno namizje GNOME
Name[sr]=&#1050;&#1083;&#1072;&#1089;&#1080;&#1095;&#1072;&#1085; &#1043;&#1085;&#1086;&#1084;
Name[sr@latin]=Klasi&#269;an Gnom
RequiredComponents=**[COLOR="Red"]gnome-shell-classic[/COLOR]**;gnome-settings-daemon;
IsRunnableHelper=/usr/lib/gnome-session/gnome-session-check-accelerated
FallbackSession=gnome-fallback
```

What truly is impressive about this version of GNOME so far is how well it performs on even low-end hardware:

```
VIA C7 CPU @ 1500MHz
VIA CN700/P4M800 Pro/P4M800 CE/VN800 Graphics [S3 UniChrome Pro] (rev 01)
VIA VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
1GB DDR2 RAM
```

Unless they screw something up it seems like Mutter is really pretty well tuned :D

I really wished Ubuntu had used something other than Compiz.

---

### Post by kansasnoob on 2013-02-08
> **VinDSL said:**
> That's what I've been doing... 

I started using the 'open-eyes' method of updating, back when the x-edger's PPA would bork my install, from time-to-time.  It was best to check for suitable updates, and apply them accordingly.  Blindly upgrading edger's was asking for trouble.

Speaking of updates...


[INDENT]**[COLOR="DarkRed"]Ubuntu 13.04 / Linux 3.8-rc6 / Gnome-Shell 3.7.5 (Staging) / Plank / Conky / ACYL / Chromium Canary[/COLOR]**

[[IMG]http://vindsl.com/images/vindsl-desktop-8-feb-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-8-feb-2013-1.png")[/INDENT]


The button icons, on the left-side of the panel are missing, otherwise everything is working fine...

I almost always parse my updates using Synaptic when I'm testing ....... it just makes things really, really easy :D

---

### Post by Mr.JJ on 2013-02-08
> **VinDSL said:**
> Activities button is still missing -- but the hot corner works.  Just saying.
I have a *feeling* the activities button is hiding underneath the apps & places buttons.

If you are talking about the legacy/classic session, then (AFAIK) it is by design, only the hot corner works.

In the shell search results, I don't see the 'settings' (GCC) section under the applications (I am using the mini.iso + ubuntu-gnome-desktop (without  install recommends). Anyone face this issue/has any ideas?

[Oh!, by the way, the mini.iso + ubuntu-gnome-desktop (without  install recommends) is a terrfic combination. This thing flies. Even after  upgrading from UGR12.10, my lap was still struggling (probably due to the  opensource ATI drivers). But this is superfast and super awesome. Even the  boot/shutdown takes only split-second. I will never install desktop  versions again :smile:]

---

### Post by zika on 2013-02-08
> **Harry33 said:**
> Do not use the Gnome3 Staging PPA and the Ricotz Testing PPA at the same time.By clumsy mistake I've turned both on... It is working nicely... Should I purge ricotz's PPAs...? Or should I march ahead bravely...? It seems faster with ricotz's upgrades (at least on this drm-next kernel)... ;)

---

### Post by dino99 on 2013-02-08
> **zika said:**
> By clumsy mistake I've turned both on... It is working nicely... Should I purge ricotz's PPAs...? Or should I march ahead bravely...? It seems faster with ricotz's upgrades (at least on this drm-next kernel)... ;)

[http://ubuntuforums.org/showpost.php?p=12498551&postcount=189](http://ubuntuforums.org/showpost.php?p=12498551&postcount=189)

---

### Post by jbicha on 2013-02-08
> **kansasnoob said:**
> Does anyone happen to know where the config files reside for the new gnome-classic?

I think the main pieces are
```

/usr/share/gnome-shell/modes/classic.json
/usr/share/gnome-session/sessions/gnome-classic.session
/usr/share/xsessions/gnome-classic.desktop

```And you can run this to switch to the classic mode without needing to log out first.
```
gnome-shell --mode=classic -r
``` Just run gnome-shell -r to get back to the regular mode.

> **kansasnoob said:**
> 
I really wished Ubuntu had used something other than Compiz.
Unity in Ubuntu 10.10 was built on mutter but performance was horrible.  I'm guessing Compiz will be dumped when Ubuntu moves to the next generation display server (Wayland or whatever) but that doesn't necessarily mean that Unity will use mutter.

> **VinDSL said:**
> 
The button icons, on the left-side of the panel are missing, otherwise everything is working fine...

Are you sure that you don't have the app menu extension enabled (or running GNOME Classic as has already been suggested?)

---

### Post by zika on 2013-02-08
> **dino99 said:**
> [http://ubuntuforums.org/showpost.php?p=12498551&postcount=189](http://ubuntuforums.org/showpost.php?p=12498551&postcount=189)I close my eyes only when I'm asleep. At that time no upgrades are possible because machine is off.. So, it seems, I'm fine... The only problem is if while eyes are open brain is on ondemand or even on powersave and not on performance... Which is true the most of the time... I even do not know if performance works on that processor...

---

### Post by kansasnoob on 2013-02-08
Cool the new "panel" objects are in /usr/share/gnome-shell/modes/classic.json:

```
{
    "parentMode": "user",
    "stylesheetName": "gnome-classic.css",
    "enabledExtensions": ["apps-menu@gnome-shell-extensions.gcampax.github.com","places-menu@gnome-shell-extensions.gcampax.github.com","alternate-tab@gnome-shell-extensions.gcampax.github.com","default-min-max@gnome-shell-extensions.gcampax.github.com","launch-new-instance@gnome-shell-extensions.gcampax.github.com","static-workspaces@gnome-shell-extensions.gcampax.github.com","window-list@gnome-shell-extensions.gcampax.github.com"],
    "panel": { "left": ["activities", "appMenu"],
               "center": [],
               "right": ["a11y", "keyboard", "volume", "bluetooth",
                         "network", "battery", "dateMenu", "userMenu"]
             }
}
```

Need to find a more appropriate name for the new classic "panels" so as not to be confused with gnome-panel ;)

But I see that it lists:

> "static-workspaces@gnome-shell-extensions.gcampax.github.com"

So maybe I just don't understand how workspace switching works in the new shell-classic session.

---

### Post by kansasnoob on 2013-02-08
Aha, hot corner upper left:

[ATTACH]231160[/ATTACH]

So this really is the best of both worlds :guitar:

---

### Post by kansasnoob on 2013-02-08
> **jbicha said:**
>  <snip>

Unity in Ubuntu 10.10 was built on mutter but performance was horrible.  I'm guessing Compiz will be dumped when Ubuntu moves to the next generation display server (Wayland or whatever) but that doesn't necessarily mean that Unity will use mutter.

 <snip>

Well I may be wrong blaming Compiz altogether but I could at least use Unity-2D on P4M800 graphics (or the fallback session) in Precise.

Quantal and Raring are just a no-go on that hardware, and also a horrible kludge even on this hardware which would run a standard Precise Unity session just fine:

> Intel Atom CPU  230 @ 1.60GHz
Intel 82945G/GZ Integrated Graphics Controller (rev 02)
Intel N10/ICH 7 Family High Definition Audio Controller (rev 01)
Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
2GB DDR2 RAM

The degradation occurred when they introduced 'llvmpipe'. Do you happen to know where GNOME is at regarding the use of 'llvmpipe' with Mutter?

---

### Post by Mr.JJ on 2013-02-09
> **Mr.JJ said:**
> In the shell search results, I don't see the 'settings' (GCC) section under the applications (I am using the mini.iso + ubuntu-gnome-desktop (without  install recommends). Anyone face this issue/has any ideas?

Okay, this is a known bug; See here: [https://bugzilla.gnome.org/show_bug.cgi?id=692483](https://bugzilla.gnome.org/show_bug.cgi?id=692483)

---

### Post by zika on 2013-02-09
Just a quick help needed: where is StartUpApplications settings now?
Thank You in advance...

---

### Post by dino99 on 2013-02-09
if logged as gnome classic: 

Applications -> System Tools -> prefs -> Startup applications

---

### Post by zika on 2013-02-09
> **dino99 said:**
> if logged as gnome classic: 

Applications -> System Tools -> prefs -> Startup applications
On that machine (that I was at that moment) GS was up and it was hard to do LogOut due to apps runnung... That is why I asked in this thread... I knew how to do that in Classic... But...
Thank You...

Update&#8321;: Is there a way of autohiding panels in Gnome Classic (GS)...? Autohiding works nicely in Fallback (GS)... Machine is up-to-date with (GS&ricotz)staging&testing ppas...

---

### Post by VinDSL on 2013-02-09
> **kansasnoob said:**
> I almost always parse my updates using Synaptic when I'm testing ....... it just makes things really, really easy :D
Heh!  I've always liked Synaptic...

The funny (odd) thing is, I have some Debian buds (on another forum) that think I'm crazy for using Synaptic.  They're always making snarky comments about Synaptic (and me, for using it).

They wouldn't use Synaptic if you put a gun in their collective mouths, and beat them with a rubber hose.  They're Aptitude snobs.

Different strokes...

> **zika said:**
> Should I purge ricotz's PPAs...? Or should I march ahead bravely...? It seems faster with ricotz's upgrades (at least on this drm-next kernel)... ;)
No need to purge ricotz's PPA, IMO.

The "meat" of the matter is the Gnome3 Staging PPA.  I always leave it enabled (checked) in the Synaptic repos.

I use the Gnome3/Ricotz PPAs occasionally, like salt/pepper.

Example: I just did a regular daily upgrade of all official and 3rd party repos, including Gnome3 Staging.

Then, I went back and enabled ricotz's PPA, refreshed, and *looked* at the available upgrades.  I wanted to 'spice' things up a bit, but I didn't want them all.

In Synaptic, doing a "Smart Upgrade" would have removed Gnome et cetera (probably due to it wishing to install mozjs188).  I didn't want to go down that path, yet.

Instead, I *looked* at what a "Default Upgrade" would accomplish, and was much happier with the packages it selected.

After doing a "Default Upgrade" of ricotz's PPA, I disabled (unchecked) it in the repos list, restarted, and everything appears to be working fine.

Anyway, I see no reason to purge ricotz's PPA.  Alternately, I see no reason to have it enabled all the time either, but that's just me.

Once again, different strokes...  ;)

> **jbicha said:**
> Are you sure that you don't have the app menu extension enabled (or running GNOME Classic as has already been suggested?)Good eye!

Yes, I've had the app menu extension enabled for so long, I forgot it was an extension. LoL!  :D

And, no, I'm not running Gnome Classic AFAIK.  Hard to tell, when you're dealing with Frankenstein's Monster, whose features sometimes meld together in strange ways, intentionally or unintentionally.

I switched back n' forth between Gnome & Classic via CLI.

They look very similar, but the window buttons (max/min/close) switch sides in Classic mode, plus it adds a lower panel.

The left-side in the upper panel look identical, regardless of which mode I'm running.

---

### Post by VinDSL on 2013-02-09
Hrm...  Just had an unusual experience!

After doing the (above) upgrades, this machine started dropping into Fallback Mode, when awaking from a screensaver blanking event.

That is, I would walk away from this machine for a few minutes (logged into GS) -- the screensaver would blank the display -- but,  when I woke it up, I was in Fallback Mode, not GS.

I started to compose a post about this situation, but got distracted with updating my Facebook account.  LoL!

When I finally got back to sorting it, I noticed there was a single upgrade available in Synaptic... gnome-screensaver 3.6.1-0ubuntu3.  Hello?!?!?

After upgrading gnome-screensaver, I saw a post by zika (in another thread) pointing to this video:  [http://mirror.linux.org.au/linux.conf.au/2013/mp4/The_real_story_behind_Wayland_and_X.mp4](http://mirror.linux.org.au/linux.conf.au/2013/mp4/The_real_story_behind_Wayland_and_X.mp4)

"Perfect test," me thinks...

I watched the video, sort of.  I fell asleep several times, but every time I awoke, the video was still playing, e.g. as if Caffeine was running in the background (which it wasn't).

"Great, now the screensaver is broken!"  :)

To my surprise, after the video completed, my monitor gently faded to black (screensaver blanked the display).  When I moved the mouse, the panel was missing, there was no transparency in Conky, and most everything else was missing.  My immediate thought was, "Okay, we're in Fallback Mode again, but...  This time, everything eventually popped back up, one component at a time.  And, I was still in GS.

If that wasn't spooky enough, that's basically what the video was talking about... the random way xorg-server draws windows, borders, et cetera (vs Wayland).

Anyway, unless I'm still dreaming, it looks like the new gnome-screensaver has some method of preventing your computer from falling asleep while watching videos.  The jury is still out, on GS coming back up, or Fallback Mode.

Anybody else experience this?

---

### Post by zika on 2013-02-10
> **VinDSL said:**
> Hrm...  Just had an unusual experience!

After doing the (above) upgrades, this machine started dropping into Fallback Mode, when awaking from a screensaver blanking event.

That is, I would walk away from this machine for a few minutes (logged into GS) -- the screensaver would blank the display -- but,  when I woke it up, I was in Fallback Mode, not GS.

I started to compose a post about this situation, but got distracted with updating my Facebook account.  LoL!

When I finally got back to sorting it, I noticed there was a single upgrade available in Synaptic... gnome-screensaver 3.6.1-0ubuntu3.  Hello?!?!?

After upgrading gnome-screensaver, I saw a post by zika (in another thread) pointing to this video:  [http://mirror.linux.org.au/linux.conf.au/2013/mp4/The_real_story_behind_Wayland_and_X.mp4](http://mirror.linux.org.au/linux.conf.au/2013/mp4/The_real_story_behind_Wayland_and_X.mp4)

"Perfect test," me thinks...

I watched the video, sort of.  I fell asleep several times, but every time I awoke, the video was still playing, e.g. as if Caffeine was running in the background (which it wasn't).

"Great, now the screensaver is broken!"  :)

To my surprise, after the video completed, my monitor gently faded to black (screensaver blanked the display).  When I moved the mouse, the panel was missing, there was no transparency in Conky, and most everything else was missing.  My immediate thought was, "Okay, we're in Fallback Mode again, but...  This time, everything eventually popped back up, one component at a time.  And, I was still in GS.

If that wasn't spooky enough, that's basically what the video was talking about... the random way xorg-server draws windows, borders, et cetera (vs Wayland).

Anyway, unless I'm still dreaming, it looks like the new gnome-screensaver has some method of preventing your computer from falling asleep while watching videos.  The jury is still out, on GS coming back up, or Fallback Mode.

Anybody else experience this?Some of MM players have switch to choose if You want it to prevent SS while You're watching a video... That might be turned on (I think that most of them has that as default) in Your case...
I had problem with waking from SS in GnomeClassic (GS) yesterday... In the meantime there was an gnome-scrensaver upgrade... So, I do not know if anything have changed with that upgrade...
It seems that LP is down (probably due to the storm) so...

---

### Post by Mr.JJ on 2013-02-10
The win+tab landed in shell. The alt+tab moved to the old windows based style. Now, win key is one stop shop for most functions, great!

@VinDSL, I read somewhere about the new changes that allow applications like media players to switch on the inhibit suspend. Probably that just landed.

---

### Post by VinDSL on 2013-02-10
> **zika said:**
> Some of MM players have switch to choose if You want it to prevent SS while You're watching a video... That might be turned on (I think that most of them has that as default) in Your case...
> **Mr.JJ said:**
> @VinDSL, I read somewhere about the new changes that allow applications like media players to switch on the inhibit suspend. Probably that just landed.
I wonder what mechanism 'they' are using?!?!?

BTW, I was watching the video in a [Chromium 26 (Canary)]("http://download-chromium.appspot.com/") tab via the QuickTime 7.6.6 / Totem 3.6.3 plugin(s). I watched that (45 min.) vid twice, yesterday -- no screen blanking either time, from start to finish. SS is set to blank >= 10 min.

I just checked my X settings, before, during, and after playback (my third viewing), and couldn't see any change(s).  

Status remained the same:
```
vindsl@Zuul:~$ xset q | grep -A1 -i dpms
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  [B][COLOR="Navy"]DPMS is Enabled
  Monitor is On[/COLOR][/B]
vindsl@Zuul:~$
```

It's obviously not using the power management system and/or using it in some enigmatic way.

If I manually turn off the screensaver blanking (there are undoubtedly other ways, like all_things_Linux), it looks like this:
```
vindsl@Zuul:~$ xset s off && xset dpms force on && xset -dpms

vindsl@Zuul:~$ xset q | grep -A1 -i dpms
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  **[COLOR="Navy"]DPMS is Disabled[/COLOR]**
vindsl@Zuul:~$ 

```

> **zika said:**
> I had problem with waking from SS in GnomeClassic (GS) yesterday... In the meantime there was an gnome-scrensaver upgrade... So, I do not know if anything have changed with that upgrade...
It seems that LP is down (probably due to the storm) so...
I'm still having issues with GS dropping into Fallback upon awakening.

And, yes, it seems 'the storm' has affected certain [NOC]("https://en.wikipedia.org/wiki/Network_operations_center")s / [Datacenter]("https://en.wikipedia.org/wiki/Data_center")s.  I had to switch (repo) mirrors yesterday, because the one I normally use was throwing checksum errors on Gnome3 Staging.

Thanks, for the feedback, guys! ;)

---

### Post by zika on 2013-02-10
> **Mr.JJ said:**
> @VinDSL, I read somewhere about the new changes that allow applications like media players to switch on the inhibit suspend. Probably that just landed.As far as I can remeber VLC is using old-scholl method... And even totem (I'm not sure) uses OS method... But, never say &#8222;never&#8220; everything is possible...

---

### Post by VinDSL on 2013-02-15
Things are looking up...


[INDENT]**[COLOR="Sienna"]Ubuntu 13.04 / Linux 3.8-rc7 / Gnome-Shell 3.7.5 (Staging) / Plank / Conky / ACYL / Chromium Canary[/COLOR]**

[[IMG]http://vindsl.com/images/vindsl-desktop-15-feb-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-15-feb-2013-1.png")[/INDENT]


Screensaver is working flawlessly, since I switched back to GDM.

Nautilus stopped crashing, when looking at file properties on remote servers.

Now, if 'they' can just get gnome-tweak-tool working.  Looks like a python bug, to me.

---

### Post by Mr.JJ on 2013-02-19
Do anyone know how to install gnome-shell-search-provider-nautilus? 
I don't get the documents/files in the shell search under nautilus, only folders.

By the way, I see 3.5.90 starts to flow in.

---

### Post by zika on 2013-02-20
Is it only me or is the menu with which to choose which session to start missing from GDM greeting screen?
Update&#8321;:It is there but it changed behaviour, in order to use it I have to lie that I'm not the user offered on the screen and then I'm given the choice of user and of session... ;)

---

### Post by VinDSL on 2013-02-20
> **zika said:**
> Is it only me or is the menu with which to choose which session to start missing from GDM greeting screen?
I just:
[LIST]
[*]Logged in normally
[*]Read your post
[*]Did a daily incremental upgrade
[*]Did a cold (re)boot, and
[*]Logged in again
[/LIST]

Sorry, but I didn't notice any difference in GDM behavior.

Happily, gnome-tweak-tool is back, but that's the only change I've noticed.  ;)

---

### Post by cole.mickens on 2013-02-20
Despite my past tribulations with NetworkManager, I'd like to try out the latest stable version, just released.

I'm aware neither PPA is likely to have it in the next 10 minutes, but I'm wondering what to do to get it "cleanly"? This staging PPA? Wait for it in the official GNOME3 PPA? Or will I just have to see if it's pulled into the official repos for raring?

---

### Post by jbicha on 2013-02-20
Cole, the new NetworkManager will be uploaded to the regular raring repositories soon (I'm thinking we'll see it this week or next). The version there already is only a few weeks old and was an "unstable snapshot" leading up to NM 0.9.8.

---

### Post by cole.mickens on 2013-02-20
> **jbicha said:**
> Cole, the new NetworkManager will be uploaded to the regular raring repositories soon (I'm thinking we'll see it this week or next). The version there already is only a few weeks old and was an "unstable snapshot" leading up to NM 0.9.8.

Fabulous. Thanks for the information jbicha!

---

### Post by zika on 2013-02-21
> **VinDSL said:**
> I just:
[LIST]
[*]Logged in normally
[*]Read your post
[*]Did a daily incremental upgrade
[*]Did a cold (re)boot, and
[*]Logged in again
[/LIST]

Sorry, but I didn't notice any difference in GDM behavior.

Happily, gnome-tweak-tool is back, but that's the only change I've noticed.  ;)
FS: unique GDM package with new (as a matter of fact somehow old, was like that at one stage some time ago) behaviour... ;)

---

### Post by VinDSL on 2013-02-21
I've been switching back n' forth between GDM & LightDM.

GDM has been working flawlessly for me.  In particular, I love the screensaver display (the one that appears after x minutes of disuse).  It was a large digital clock in the middle, with large, animated chevrons pointing toward it, lovely background, volume buttons in the upper panel, blah, blah, blah.  And, the desktop pops up immediately, when I tap the keyboard.

LightDM is the one that's giving me fits. Items in the upper panel are ghosted out (white on white colors). The custom wallpaper usually comes up in the login display, but not before flashing the 'monkey vomit' default wallpaper.  Recovering from the screensaver is a crapshoot, et cetera.

GDM login screen is a class act, these days!

LightDM looks/acts like an amateurish hack, IMO.  ;)

---

### Post by hugmenot on 2013-02-21
Would appreciate if someone could enlighten me what I did wrong (packages gratuitously uninstalled, etc.)

[LIST]
[*]My Empathy starts up, but has no credentials. When I click account settings in the Empathy window Gnome Control Center pops up with the icon view, but there is only Gnome&#8217;s online accounts visible, the signond based one disappeared (g-c-c version 3.7.5 from gnome3-staging PPA). How&#8217;s this supposed to work nowadays?
[*] Evolution 3.6 from main doesn&#8217;t start up with an error message that it can&#8217;t dinf some ecal widget
[*] When I click "Network settings" in the GS network dropdown nothing happens
[*] When I type "network" in the GS overview it only displays .desktop file entries of apps, but nothing from g-c-c (i.e., to reach the NM panel).
[*] With nautilus drawing the desktop, when I go into the overview, nautilus fades away, together with the desktop wallpaper, and I have a land gray while the overview is showing.
[/LIST]

---

### Post by Harry33 on 2013-02-22
The latest evince draws in both libarchive 12 and libarchive13.

Evince 3.7.90 (the packages libevdocument3-4) depends on libarchive13.
We have libarchive12 in RR now.
That is a dependency of libgxps2, which also libevdocument3-4 depends on.

It seems we need to have libgxps2 rebuilt against libarchive13 here in order to get rid of the older ABI libarchive12.

---

### Post by zika on 2013-02-22
```
:~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  evince ubuntu-desktop
The following NEW packages will be installed:
  libmozjs-17.0-0
The following packages have been kept back:
  file-roller libevdocument3-4
The following packages will be upgraded:
  gjs gnome-shell gnome-shell-common libevview3-3 libgjs0c
5 upgraded, 1 newly installed, 2 to remove and 2 not upgraded.
Need to get 3,566 kB of archives.
After this operation, 2,717 kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

``````
:~$ sudo aptitude full-upgrade 
The following NEW packages will be installed:
  libmozjs-17.0-0{a} 
The following packages will be REMOVED:
  libmozjs188-1.0{u} 
The following packages will be upgraded:
  evince file-roller{b} gjs gnome-shell gnome-shell-common 
  libevdocument3-4{b} libevview3-3 libgjs0c 
8 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 5,966 kB of archives. After unpacking 13.3 kB will be used.
The following packages have unmet dependencies:
 libevdocument3-4 : Depends: libarchive13 which is a virtual package.
 file-roller : Depends: libarchive13 which is a virtual package.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     evince                      
2)     file-roller                 
3)     libevdocument3-4            
4)     libevview3-3                
5)     ubuntu-desktop              



Accept this solution? [Y/n/q/?]
```

---

### Post by ricotz on 2013-02-22
Make sure you have raring-proposed enabled.

---

### Post by Harry33 on 2013-02-22
Zika,

You have enabled Gnome Testing PPA.
It is that PPA, where the libmoz17 is coming from.
I don't think Gnome Testing PPA should be enabled if Gnome3 Staging PPA is used.

And yes libarchive13 is in proposed ATM.

---

### Post by zika on 2013-02-22
> **Harry33 said:**
> Zika,

You have enabled Gnome Testing PPA.
It is that PPA, where the libmoz17 is coming from.
I don't think Gnome Testing PPA should be enabled if Gnome3 Staging PPA is used.

And yes libarchive13 is in proposed ATM.So You think I should pick one?
Gnome3Staging?
OK...

---

### Post by ricotz on 2013-02-22
> **zika said:**
> So You think I should pick one?
Gnome3Staging?
OK...

No, please use them all together. gnome3-staging is a dependency now for ricotz/testing

---

### Post by zika on 2013-02-22
> **zika said:**
> FS: unique GDM package with new (as a matter of fact somehow old, was like that at one stage some time ago) behaviour... ;)Sold: once I've ppa-purged ricotz/testing GDM welcome screen seems back to old...
[SIZE="4"]1.[/SIZE]
> **Harry33 said:**
> Zika,

You have enabled Gnome Testing PPA.
It is that PPA, where the libmoz17 is coming from.
I don't think Gnome Testing PPA should be enabled if Gnome3 Staging PPA is used.

And yes libarchive13 is in proposed ATM.

[SIZE="4"]2.[/SIZE]
> **ricotz said:**
> No, please use them all together. gnome3-staging is a dependency now for ricotz/testing
[img]https://upload.wikimedia.org/wikipedia/commons/2/22/Deliberations_of_Congress.jpg[/img]

Maybe it is time for both of You to elaborate: why... Pros&Cons... ;)

---

### Post by Harry33 on 2013-02-22
> **zika said:**
> Sold: once I've ppa-purged ricotz/testing GDM welcome screen seems back to old...
...
Maybe it is time for both of You to elaborate: why... Pros&Cons... ;)

This is of course my opinion, and it, after all, depends wheter you prefer the very latest git-versions (Gnome Testing PPA + Gnome3 Staging) or more stable point releases (only Gnome3 Staging).
However, should you choose Gnome Testing PPA, it is better to believe what Ricotz said: then both enabled.

---

### Post by Harry33 on 2013-02-22
> **Harry33 said:**
> The latest evince draws in both libarchive 12 and libarchive13.

Evince 3.7.90 (the packages libevdocument3-4) depends on libarchive13.
We have libarchive12 in RR now.
That is a dependency of libgxps2, which also libevdocument3-4 depends on.

It seems we need to have libgxps2 rebuilt against libarchive13 here in order to get rid of the older ABI libarchive12.

This is now solved with the latest libgxps2:

> [Jeremy Bicha]("http://www.mail-archive.com/search?l=raring-changes@lists.ubuntu.com&q=from:%22Jeremy+Bicha%22") [Fri, 22 Feb 2013 05:45:51 -0800]("http://www.mail-archive.com/search?l=raring-changes@lists.ubuntu.com&q=date:20130222") 
    libgxps (0.2.2-2ubuntu2) raring; urgency=low    * No-change rebuild against new libarchive

---

### Post by zika on 2013-02-22
> **Harry33 said:**
> This is of course my opinion, and it, after all, depends wheter you prefer the very latest git-versions (Gnome Testing PPA + Gnome3 Staging) or more stable point releases (only Gnome3 Staging).
However, should you choose Gnome Testing PPA, it is better to believe what Ricotz said: then both enabled.Of course: I did have enabled everything that was required... ;)
I'll live for a while with „more stable point releases“ to see how that goes...

---

### Post by kansasnoob on 2013-02-22
> **ricotz said:**
> No, please use them all together. gnome3-staging is a dependency now for ricotz/testing

I'm confused now, would you please provide links to the PPA's that should be used in combination :)

Also, are you and Jeremy Bicha working together here?

I'm honestly not just complaining but we need to know who's testing what :D

---

### Post by ricotz on 2013-02-22
> **kansasnoob said:**
> I'm confused now, would you please provide links to the PPA's that should be used in combination :)

Also, are you and Jeremy Bicha working together here?

I'm honestly not just complaining but we need to know who's testing what :D

Alright it wasn't that clear while I didn't quote the post I replied to.
The PPA descriptions should give one the needed hints what to add.

What I am saying is the if you want to use ppa:ricotz/testing you are suppose to add ppa:gnome3-team/gnome3 and ppa:gnome3-team/gnome3-staging too.
Although you can use the gnome3-team PPAs separately if you don't want to go for the git snapshots.

And yes, we are working together on the gnome3 PPAs.

---

### Post by kansasnoob on 2013-02-23
> **ricotz said:**
> Alright it wasn't that clear while I didn't quote the post I replied to.
The PPA descriptions should give one the needed hints what to add.

What I am saying is the if you want to use ppa:ricotz/testing you are suppose to add ppa:gnome3-team/gnome3 and ppa:gnome3-team/gnome3-staging too.
Although you can use the gnome3-team PPAs separately if you don't want to go for the git snapshots.

And yes, we are working together on the gnome3 PPAs.

Thank you :)

---

### Post by zika on 2013-02-24
Two new things this morning:
1. GDM stopped working after upgrade, did not have time to see what is going on, just jumped on xinit...
2. Should libmx-1.0-2 be removed, I can not decipher that from changelog
```
Calculating upgrade... Done
The following packages will be REMOVED:
  libcogl-pango0 libcogl11 libmx-1.0-2
The following NEW packages will be installed:
  libcogl-pango12 libcogl12 libgnome-desktop-3-7
The following packages will be upgraded:
  account-plugin-empathy empathy empathy-common gir1.2-cogl-1.0
  gir1.2-coglpango-1.0 gir1.2-gnomedesktop-3.0 gir1.2-totem-1.0
  gnome-control-center gnome-control-center-data gnome-settings-daemon
  gnome-shell gnome-shell-common gstreamer1.0-clutter libclutter-1.0-0
  libclutter-gst-1.0-0 libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libmutter0a
  libtotem0 mcp-account-manager-uoa mutter mutter-common
  nautilus-sendto-empathy totem totem-common totem-mozilla totem-plugins
27 upgraded, 3 newly installed, 3 to remove and 0 not upgraded.
```

---

### Post by Harry33 on 2013-02-24
> **zika said:**
> Two new things this morning:
1. GDM stopped working after upgrade, did not have time to see what is going on, just jumped on xinit...
2. Should libmx-1.0-2 be removed, I can not decipher that from changelog
```
Calculating upgrade... Done
The following packages will be REMOVED:
  libcogl-pango0 libcogl11 libmx-1.0-2
The following NEW packages will be installed:
  libcogl-pango12 libcogl12 libgnome-desktop-3-7
The following packages will be upgraded:
  account-plugin-empathy empathy empathy-common gir1.2-cogl-1.0
  gir1.2-coglpango-1.0 gir1.2-gnomedesktop-3.0 gir1.2-totem-1.0
  gnome-control-center gnome-control-center-data gnome-settings-daemon
  gnome-shell gnome-shell-common gstreamer1.0-clutter libclutter-1.0-0
  libclutter-gst-1.0-0 libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libmutter0a
  libtotem0 mcp-account-manager-uoa mutter mutter-common
  nautilus-sendto-empathy totem totem-common totem-mozilla totem-plugins
27 upgraded, 3 newly installed, 3 to remove and 0 not upgraded.
```


Hi there Zika, see my thread here for more info on this issue.

[http://ubuntuforums.org/showthread.php?t=2119505](http://ubuntuforums.org/showthread.php?t=2119505)

---

### Post by jbicha on 2013-02-24
> **zika said:**
> 
2. Should libmx-1.0-2 be removed, I can not decipher that from changelog

I doubt that you have anything that needs libmx so removing it should be fine. Removing the two old cogl libraries is intentional (libcogl11 and libcogl-pango0).

---

### Post by zika on 2013-02-24
> **jbicha said:**
> I doubt that you have anything that needs libmx so removing it should be fine. Removing the two old cogl libraries is intentional (libcogl11 and libcogl-pango0).
Removed libmx already, I figured that in my old but not yet gray-haired head... Other two are replaced with their new versions so...

---

### Post by hugmenot on 2013-02-24
So empathy can be configured using signon online accounts in the control center again.

But now it configures Evolution also, where I already have a traditionally configured Gmail POP account. So now I have a POP account and an IMAP account that I cannot delete and do not really want. And in the Online Accounts panel there is no mention of Evolution at all, only Empathy.

---

### Post by VinDSL on 2013-02-24
Heh!  Check out this mess...  :)

```
vindsl@Zuul:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**[COLOR="Blue"]The following packages have been kept back:[/COLOR]**
  account-plugin-empathy cheese cheese-common empathy empathy-common eog
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-gnomedesktop-3.0
  gir1.2-totem-1.0 gnome-contacts gnome-control-center
  gnome-control-center-data gnome-documents gnome-font-viewer gnome-session
  gnome-session-bin gnome-session-common gnome-session-fallback
  gnome-settings-daemon gnome-shell gnome-shell-common gstreamer1.0-clutter
  libcheese-gtk23 libcheese7 libclutter-1.0-0 libclutter-gst-2.0-0
  libclutter-gtk-1.0-0 libmutter0a libtotem0 mcp-account-manager-uoa mutter
  mutter-common nautilus nautilus-sendto-empathy totem totem-common
  totem-mozilla totem-plugins totem-plugins-extra
**[COLOR="Blue"]The following packages will be upgraded:[/COLOR]**
  baobab caribou caribou-antler gdm gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-clutter-gst-2.0 gir1.2-gdata-0.0 gir1.2-gtkclutter-1.0
  gir1.2-gtksource-3.0 gir1.2-mutter-3.0 gir1.2-nautilus-3.0 gjs
  gnome-control-center-signon gnome-desktop3-data gnome-shell-extensions
  libaccount-plugin-1.0-0 libcaribou-common libcaribou-gtk-module
  libcaribou-gtk3-module libcaribou0 libclutter-1.0-common libcogl-common
  libgdata-common libgdata13 libgjs0c libgnome-control-center1
  libgnome-desktop-3-4 libgtksourceview-3.0-0 libgtksourceview-3.0-common
  libnautilus-extension1a libsox-fmt-alsa libsox-fmt-base libsox2
  nautilus-data sox
**[COLOR="Blue"]36 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.[/COLOR]**
Need to get 16.3 MB/16.7 MB of archives.
After this operation, 2,265 kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
vindsl@Zuul:~$
```

---

### Post by jbicha on 2013-02-24
> **VinDSL said:**
> Heh!  Check out this mess...  :)

```
vindsl@Zuul:~$ sudo apt-get upgrade
```

I believe you'll need to do a dist-upgrade.

---

### Post by VinDSL on 2013-02-24
> **jbicha said:**
> I believe you'll need to do a dist-upgrade.
That's the prudent way to go, but I'm afraid to attempt it, a few hours before a Full Moon (Murphy's Law).  LoL!  :D

Synaptic "Smart Upgrade" looks much 'smarter' today, than it did 12 hours ago!  "Default Upgrade" is still a mess.

Last night, Synaptic wanted to remove gnome et al (Smart & Default Upgrades alike).


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-24-feb-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-24-feb-2013-1.png")[/INDENT]


Right now, it just wants to remove 3 libs, with nothing to be held-back.

Think I'll pull the trigger on that one first, and see what happens.

---

### Post by VinDSL on 2013-02-24
Synaptic "Smart Upgrade" put Humpty Dumpty back together again.  ;)

```
<SNIP>

Fetched 13.7 MB in 1min 11s (191 kB/s)
Reading package lists... Done
vindsl@Zuul:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
vindsl@Zuul:~$ 
```

And, it survived a cold boot.

When GDM appeared, ONBOARD was enabled.  ONBOARD popped up again on the desktop -- so, I disabled it.

The digital clock is back in the top panel -- need to go hack (get rid of) that again.  Happens after every major upgrade(s).

Dropbox asked for auth.  Guess I'll need to go through that, in various apps, for a while.

As "harry" said, desktop is opening outward, from a single point, in the middle of the display -- like a starburst effect from the '90s.  LoL!

I'll need to tron a bunch of extensions.  Some of them disappeared, after the reboot.  That was to be expected -- happens on every version upgrade.

Other than those few things, it looks like everything is going to work.

I'll putz around today, cleaning up the UI, and getting it back to where I had it set.  No show stoppers that I can see, so far.

Onward & upward!

---

### Post by zika on 2013-02-26
Been like this for days now:```
Calculating upgrade... Done
The following packages will be REMOVED:
  gir1.2-totem-1.0 libcogl11 libtotem0 totem totem-mozilla totem-plugins
The following packages will be upgraded:
  gir1.2-clutter-1.0 libclutter-1.0-0
2 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
Need to get 709 kB of archives.
After this operation, 4,110 kB disk space will be freed.
Do you want to continue [Y/n]?
```...

---

### Post by Harry33 on 2013-02-27
> **zika said:**
> Been like this for days now:```
Calculating upgrade... Done
The following packages will be REMOVED:
  gir1.2-totem-1.0 libcogl11 libtotem0 totem totem-mozilla totem-plugins
The following packages will be upgraded:
  gir1.2-clutter-1.0 libclutter-1.0-0
2 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
Need to get 709 kB of archives.
After this operation, 4,110 kB disk space will be freed.
Do you want to continue [Y/n]?
```...

At least you could remove the libcogl11 package, Your setup is using libcogl12 now.
Otherwise it seems that upgrading clutter-1.0 breaks totem.
So where are they coming from?
Is the clutter-1.0 from Gnome Testing PPA (v. 1.13.7+git...)
and totem from Gnome3 Staging PPA (v. 3.6.3-0ubuntu3)?

---

### Post by binary00mind on 2013-02-27
> **VinDSL said:**
> Synaptic "Smart Upgrade" looks much 'smarter' today, than it did 12 hours ago!  "Default Upgrade" is still a mess.

Last night, Synaptic wanted to remove gnome et al (Smart & Default Upgrades alike).

I am totally new to this "RingTailing" thing. I resisted leaving Lucid (and still am) but managed to find some space and gave a shot... 
I'm also confused about this Smart vs Default upgrade (in this edition). ..Wants to remove Gnome, I politely declined (for the next 24 hours LOL)
Maybe wrong place to ask, what theme do you use and this monitor on the right...help me LOL. Is this from the ppa?

It seems to me that what used to be hard is easy now days and what what was easy is hard (or harder) :o

---

### Post by zika on 2013-02-27
> **Harry33 said:**
> At least you could remove the libcogl11 package, Your setup is using libcogl12 now.
Otherwise it seems that upgrading clutter-1.0 breaks totem.
So where are they coming from?
Is the clutter-1.0 from Gnome Testing PPA (v. 1.13.7+git...)
and totem from Gnome3 Staging PPA (v. 3.6.3-0ubuntu3)?I have a „policy“ not to purge (at least manually) packages that are still nn official Ubuntu list in order to be able to easily ppa-purge possible offending PPA...
I'll check origin of these two packages... My bet iz ricotz... ;)

---

### Post by Harry33 on 2013-02-27
> **zika said:**
> I have a „policy“ not to purge (at least manually) packages that are still nn official Ubuntu list in order to be able to easily ppa-purge possible offending PPA...
I'll check origin of these two packages... My bet iz ricotz... ;)

If you have synaptic installed, you can see the real dependency issue from there.
Mark clutter-1.0 to be upgraded and see what is says.

---

### Post by zika on 2013-02-27
> **Harry33 said:**
> If you have synaptic installed, you can see the real dependency issue from there.
Mark clutter-1.0 to be upgraded and see what is says.Of course I've investigated that. No GUI is needed:```
The following packages will be upgraded: 
  gir1.2-clutter-1.0 libclutter-1.0-0{b} 
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 709 kB of archives. After unpacking 4,096 B will be used.
The following packages have unmet dependencies:
 libclutter-1.0-0 : Breaks: libcogl11 but 1.12.2-0ubuntu1 is installed.
The following actions will resolve these dependencies:

     Remove the following packages:              
1)     gir1.2-totem-1.0                          
2)     libcogl11                                 
3)     libtotem0                                 
4)     totem                                     
5)     totem-mozilla                             
6)     totem-plugins                             

     Leave the following dependencies unresolved:
7)     ubuntu-desktop recommends totem           
8)     ubuntu-desktop recommends totem-mozilla   


Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
:~$ sudo apt-get purge libcogl11
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gir1.2-totem-1.0* libcogl11* libtotem0* totem* totem-mozilla* totem-plugins*
0 upgraded, 0 newly installed, 6 to remove and 2 not upgraded.
After this operation, 4,114 kB disk space will be freed.
Do you want to continue [Y/n]? n
```As I wrote above, it seems that ricotz left dependency of totem and others still on libcogl11...
To emphasize: this is not a big deal, just annoyance when other packages need dist-upgrade... (like liquorix etc. ...)
New Totem is just being cooked for amd_64 as I write this in ppa:ricotz/staging so...
Update&#8321;: Resolved... Thank You Ricotz...

---

### Post by VinDSL on 2013-02-27
> **binary00mind said:**
> I'm also confused about this Smart vs Default upgrade (in this edition)...
I made a few changes in my Synaptic's Preferences.  One of them is:

**[COLOR="Blue"]Settings ->> Preferences ->> General ->> Making Changes ->> System Upgrade ->> Select "Always Ask" ->> Apply/OK[/COLOR]**

After that, when you Reload & Mark All Upgrades you will be given 2 choices for performing the upgrade:
[LIST=1]
[*]Default (which is basically the same as "sudo apt-get upgrade" in CLI)
[*]Smart Upgrade ( which is basically the same as "sudo apt-get dist-upgrade")
[/LIST]

Personally, I look at the changes (click Apply) on both Default Upgrade & Smart Upgrade, before committing to the changes.

Most times, IMO, you are better off using the Default Upgrade, however, there are times when doing a Smart Upgrade is the better choice.

I look specifically for what's going to be removed, and what's going to be held back.

Sometimes... even many times... doing ANY upgrade (on a dev release) will appear to clean your clock.

If things look too gnarly, you're better off waiting for a day or two before doing upgrades.  That's what I did, in the case above.  I just hung-out for about 12 hours, before attempting a Smart Upgrade, and everything turned out fine.


> **binary00mind said:**
> Maybe wrong place to ask, what theme do you use and this monitor on the right...help me LOL. Is this from the ppa?
Yeah, probably the wrong place, but briefly...

I enjoy customizing the UI, e.g. theme et al.  I've made too many changes to list them here.

Best place for getting info on doing stuff like this is in the monthly desktop showcase thread.  The mods/admins stickify it to the top of "The Community Cafe" sub-forum.

The current thread is:  [http://ubuntuforums.org/showthread.php?t=2111300](http://ubuntuforums.org/showthread.php?t=2111300)

Current desktop screenie:  [http://vindsl.com/images/vindsl-desktop-23-feb-2013-1.png](http://vindsl.com/images/vindsl-desktop-23-feb-2013-1.png)

The widgets, on the right-side, are a customization of an app called Conky.  There is a link in my sig, if you're interested.

Okay, back to our regular programming...  ;)

---

### Post by Harry33 on 2013-02-27
> **zika said:**
> 
...
As I wrote above, it seems that ricotz left dependency of totem and others still on libcogl11...
To emphasize: this is not a big deal, just annoyance when other packages need dist-upgrade... (like liquorix etc. ...)
New Totem is just being cooked for amd_64 as I write this in ppa:ricotz/staging so...
Update&#8321;: Resolved... Thank You Ricotz...

Here are the dependencies of the Gnome3 Staging PPA's totem.
So, totem depends on libcogl12.
But if the new clutter-1.0 breaks libcogl11, you either have to remove libcogl11 or not to upgrade clutter-1.0.

1) totem 3.6.3-0ubuntu3~raring1
[SIZE=2]Depends: libatk1.0-0 (>= 1.12.4)
libc6 (>= 2.4)
libcairo2 (>= 1.10.0)
libclutter-1.0-0 (>= 1.10.0)
libclutter-gtk-1.0-0 (>= 1.0.2)
**libcogl12 (>= 1.7.4)**
libdbus-glib-1-2 (>= 0.88)
libgdk-pixbuf2.0-0 (>= 2.22.0)
libglib2.0-0 (>= 2.33.14)
libgstreamer-plugins-base1.0-0 (>= 1.0.0)
libgstreamer1.0-0 (>= 1.0.0)
libgtk-3-0 (>= 3.5.12)
libnautilus-extension1a (>= 1:2.91)
libpango1.0-0 (>= 1.14.0)
libtotem-plparser17 (>= 2.32.4-2)
libtotem0 (>= 3.6.3-0ubuntu3~raring1)
libtotem0 (<< 3.7)
libx11-6
python (>= 2.7.1-0ubuntu2)
gstreamer1.0-clutter
gstreamer1.0-plugins-base (>= 0.11.93)
gstreamer1.0-plugins-good (>= 0.11.93)
gstreamer1.0-x
gnome-icon-theme (>= 2.15.90)
gnome-icon-theme-symbolic
totem-common (= 3.6.3-0ubuntu3~raring1)[/SIZE]

2) libtotem0 v. 3.6.3-0ubuntu3~raring1
Depends: libatk1.0-0 (>= 1.12.4)
libc6 (>= 2.14)
libcairo2 (>= 1.10.0)
libclutter-1.0-0 (>= 1.10.0)
libclutter-gtk-1.0-0 (>= 1.0.2)
**libcogl12 (>= 1.7.4)**
libgdk-pixbuf2.0-0 (>= 2.22.0)
libgirepository-1.0-1 (>= 0.9.2)
libglib2.0-0 (>= 2.33.0)
libgstreamer-plugins-base1.0-0 (>= 1.0.0)
libgstreamer1.0-0 (>= 1.0.0)
libgtk-3-0 (>= 3.5.2)
libice6 (>= 1:1.0.0)
libpango1.0-0 (>= 1.14.0)
libpeas-1.0-0 (>= 1.0.0)
libsm6
libtotem-plparser17 (>= 2.32.4-2)
libx11-6

3) tottem-mozilla v. 3.6.3-0ubuntu3~raring1[SIZE=3]
[SIZE=2]Depends: libc6 (>= 2.14)
libgcc1 (>= 1:4.1.1)
libglib2.0-0 (>= 2.33.0)
libstdc++6 (>= 4.1.1)
libtotem-plparser17 (>= 2.32.4-2)
totem (= 3.6.3-0ubuntu3~raring1)
dbus-x11 (>= 0.61)[/SIZE][/SIZE]

4) totem-plugins v. 3.6.3-0ubuntu3~raring1
Depends: totem (= 3.6.3-0ubuntu3~raring1)
libc6 (>= 2.7)
libgdk-pixbuf2.0-0 (>= 2.22.0)
libglib2.0-0 (>= 2.33.0)
libgtk-3-0 (>= 3.5.2)
liblircclient0
libtotem0 (>= 3.6.3-0ubuntu3~raring1)
libtotem0 (<< 3.7)
libxml2 (>= 2.7.4)
libzeitgeist-1.0-1 (>= 0.3.2)
python (>= 2.7.1-0ubuntu2)
python2.7
gir1.2-totem-1.0 (= 3.6.3-0ubuntu3~raring1)
gir1.2-gtk-3.0
gir1.2-gdkpixbuf-2.0
gir1.2-glib-2.0
gir1.2-pango-1.0
gir1.2-peas-1.0
python-gi (>= 2.90.3)
python-xdg
python-httplib2

5) gir1.2-totem-1.0 (= 3.6.3-0ubuntu3~raring1)
Depends: gir1.2-atk-1.0
gir1.2-freedesktop
gir1.2-gdkpixbuf-2.0
gir1.2-glib-2.0
gir1.2-gtk-3.0
gir1.2-pango-1.0
gir1.2-totem-plparser-1.0
libtotem0 (<< 3.7)
libtotem0 (>= 3.6.3-0ubuntu3~raring1)

---

### Post by zika on 2013-02-27
> **Harry33 said:**
> Here are the dependencies of the Gnome3 Staging PPA's totem.
So, totem depends on libcogl12.
But if the new clutter-1.0 breaks libcogl11, you either have to remove libcogl11 or not to upgrade clutter-1.0.

```
1) totem 3.6.3-0ubuntu3~raring1
[SIZE=2]Depends: libatk1.0-0 (>= 1.12.4)
libc6 (>= 2.4)
libcairo2 (>= 1.10.0)
libclutter-1.0-0 (>= 1.10.0)
libclutter-gtk-1.0-0 (>= 1.0.2)
**libcogl12 (>= 1.7.4)**
libdbus-glib-1-2 (>= 0.88)
libgdk-pixbuf2.0-0 (>= 2.22.0)
libglib2.0-0 (>= 2.33.14)
libgstreamer-plugins-base1.0-0 (>= 1.0.0)
libgstreamer1.0-0 (>= 1.0.0)
libgtk-3-0 (>= 3.5.12)
libnautilus-extension1a (>= 1:2.91)
libpango1.0-0 (>= 1.14.0)
libtotem-plparser17 (>= 2.32.4-2)
libtotem0 (>= 3.6.3-0ubuntu3~raring1)
libtotem0 (<< 3.7)
libx11-6
python (>= 2.7.1-0ubuntu2)
gstreamer1.0-clutter
gstreamer1.0-plugins-base (>= 0.11.93)
gstreamer1.0-plugins-good (>= 0.11.93)
gstreamer1.0-x
gnome-icon-theme (>= 2.15.90)
gnome-icon-theme-symbolic
totem-common (= 3.6.3-0ubuntu3~raring1)[/SIZE]

2) libtotem0 v. 3.6.3-0ubuntu3~raring1
Depends: libatk1.0-0 (>= 1.12.4)
libc6 (>= 2.14)
libcairo2 (>= 1.10.0)
libclutter-1.0-0 (>= 1.10.0)
libclutter-gtk-1.0-0 (>= 1.0.2)
**libcogl12 (>= 1.7.4)**
libgdk-pixbuf2.0-0 (>= 2.22.0)
libgirepository-1.0-1 (>= 0.9.2)
libglib2.0-0 (>= 2.33.0)
libgstreamer-plugins-base1.0-0 (>= 1.0.0)
libgstreamer1.0-0 (>= 1.0.0)
libgtk-3-0 (>= 3.5.2)
libice6 (>= 1:1.0.0)
libpango1.0-0 (>= 1.14.0)
libpeas-1.0-0 (>= 1.0.0)
libsm6
libtotem-plparser17 (>= 2.32.4-2)
libx11-6

3) tottem-mozilla v. 3.6.3-0ubuntu3~raring1[SIZE=3]
[SIZE=2]Depends: libc6 (>= 2.14)
libgcc1 (>= 1:4.1.1)
libglib2.0-0 (>= 2.33.0)
libstdc++6 (>= 4.1.1)
libtotem-plparser17 (>= 2.32.4-2)
totem (= 3.6.3-0ubuntu3~raring1)
dbus-x11 (>= 0.61)[/SIZE][/SIZE]

4) totem-plugins v. 3.6.3-0ubuntu3~raring1
Depends: totem (= 3.6.3-0ubuntu3~raring1)
libc6 (>= 2.7)
libgdk-pixbuf2.0-0 (>= 2.22.0)
libglib2.0-0 (>= 2.33.0)
libgtk-3-0 (>= 3.5.2)
liblircclient0
libtotem0 (>= 3.6.3-0ubuntu3~raring1)
libtotem0 (<< 3.7)
libxml2 (>= 2.7.4)
libzeitgeist-1.0-1 (>= 0.3.2)
python (>= 2.7.1-0ubuntu2)
python2.7
gir1.2-totem-1.0 (= 3.6.3-0ubuntu3~raring1)
gir1.2-gtk-3.0
gir1.2-gdkpixbuf-2.0
gir1.2-glib-2.0
gir1.2-pango-1.0
gir1.2-peas-1.0
python-gi (>= 2.90.3)
python-xdg
python-httplib2

5) gir1.2-totem-1.0 (= 3.6.3-0ubuntu3~raring1)
Depends: gir1.2-atk-1.0
gir1.2-freedesktop
gir1.2-gdkpixbuf-2.0
gir1.2-glib-2.0
gir1.2-gtk-3.0
gir1.2-pango-1.0
gir1.2-totem-plparser-1.0
libtotem0 (<< 3.7)
libtotem0 (>= 3.6.3-0ubuntu3~raring1)
```
Thank You for this effort... You probably did not notice the end of my prevoius message...
I've mentioned two+ messages ago that I've seen dependency tree but...
Isn't it nice to use &#8222;code&#8220; tags for such a list...?
Again: Thank You Ricotz...

---

### Post by Harry33 on 2013-02-27
> **zika said:**
> Thank You for this effort... You probably did not notice the end of my prevoius message...
I've mentioned two+ messages ago that I've seen dependency tree but...
Isn't it nice to use „code“ tags for such a list...?
Again: Thank You Ricotz...

I checked that when Gnome3 Staging PPA is enabled without Gnome Testing PPA, there is no problem installing totem.
After installation nothing is left to be removed.

---

### Post by zika on 2013-02-27
> **Harry33 said:**
> I checked that when Gnome3 Staging PPA is enabled without Gnome Testing PPA, there is no problem installing totem.
After installation nothing is left to be removed.As I mentioned several times here is Ricotz's PPA also turned on and that was a source of dependency issue that was sorted out with two (it was soved with the first) upgrades for totem and its friends today... I have a feeling that I'm not writting clearly enough so please confirm that You receive all the stuff that I write... ;)

---

### Post by ricotz on 2013-02-27
> **zika said:**
> As I mentioned several times here is Ricotz's PPA also turned on and that was a source of dependency issue that was sorted out with two (it was soved with the first) upgrades for totem and its friends today... I have a feeling that I'm not writting clearly enough so please confirm that You receive all the stuff that I write... ;)

You should mention that you are using ricotz/staging! So if something breaks while using it you are suppose to keep the pieces. ;)

---

### Post by zika on 2013-02-27
> **ricotz said:**
> You should mention that you are using ricotz/staging! So if something breaks while using it you are suppose to keep the pieces. ;)But I did... ;) I did mention that I'm using staging and I did keep the pieces, I even did not allow anything to break... Isn't that enough for an old geezer sush as I am?... 
[IMG]http://www.sherv.net/cm/emo/angry/angry-old-man-smiley-emoticon.gif[/IMG]
;)

---

### Post by Harry33 on 2013-02-28
> **zika said:**
> As I mentioned several times here is Ricotz's PPA also turned on and that was a source of dependency issue that was sorted out with two (it was soved with the first) upgrades for totem and its friends today... I have a feeling that I'm not writting clearly enough so please confirm that You receive all the stuff that I write... ;)

You did mention yes.
But still please be specific.
Currently there are at least 5 different PPA's of Rico Tzschichholz around:
1. Docky/Plank Testing
2. Experimental
3. Gnome Testing
4. Staging
5. Unstable

It was the nro 3 you meant.
:guitar:

---

### Post by zika on 2013-02-28
> **Harry33 said:**
> You did mention yes.
But still please be specific.
Currently there are at least 5 different PPA's of Rico Tzschichholz around:
1. Docky/Plank Testing
2. Experimental
3. Gnome Testing
4. Staging
5. Unstable

It was the nro 3 you meant.
:guitar:You're totally right... I was not thinking about other ppas... I thought just about G3... Mea culpa...
Nice way to try new Forum-SW...
Yes, I've just checked, those 2 I've mentioned (#3 & #4) are the only ones that deal with G3... ;)
I promise, next time, I will list ppas I use relevant to the problem at the table...
This time I've seen that Ricotz has new stuff about GStreamer so... Let the breakage resume...

---

### Post by mc4man on 2013-02-28
> **zika said:**
> 
This time I've seen that Ricotz has new stuff about GStreamer so... Let the breakage resume...
I see new gst* (1.1.x) in the experimental ppa. They are fairly interesting in that the gst-libav plugin is using the built-in libav source rather than the system shared as Debian/Ubuntu always uses.

Will solve the quicktime decoding issue in a more positive manner, (libav9 does multi-thread decoding better), than the fix coming for gst-1.0.x which will set the default back to 1 (no multi-thread.

Whether 13.04 plans to use libav-9 & gst-1.1 no idea, there **was** plenty of time for libav9 (released in early Jan.), but that was then, almost March...

(- libav9 would also fix ffaudio plugin in audacious though a simple 2 char source edit would have it enabled now with libav-8.x

---

### Post by VinDSL on 2013-03-01
Can someone help me understand this?  Not complaining, mind you...  :D

Since I started running Gnome 3 Staging...

When I use LightDM to login to Unity, it's a total mess -- I cannot change the default settings -- cannot use custom fonts, iconsets, blah, blah, blah.  

Looks like garbage!

I cannot even login to Unity at all, using GDM -- won't allow me to change the User and/or DE.

However, if I login to GS Stagiing (using either DM), open a terminal, and simply type:
```
unity
```

...Unity comes up picture-perfect -- everything the way it's supposed to be.  Hello?!?!?


[INDENT][[IMG]http://vindsl.com/images/Screenshot from 2013-03-01 18:30:57(650x520).png[/IMG]]("http://vindsl.com/images/Screenshot from 2013-03-01 18:30:57.png")[/INDENT]


[INDENT][[IMG]http://vindsl.com/images/Screenshot from 2013-03-01 18:31:45(650x520).png[/IMG]]("http://vindsl.com/images/Screenshot from 2013-03-01 18:31:45.png")[/INDENT]


How can this be :confused:

---

### Post by Mr.JJ on 2013-03-02
> **Mr.JJ said:**
> Do any of you get the file search working from  within the shell? The search options are set and even when I do a file  search from tracker and from within the nautilus I get the files I am  looking for

This bug is now fixed. But the bugfix need nautilus to be built with tracker support (bug report says the last version in ubuntu did not have tracker support). Without this we will not see the actual files/documents in the shell search.
> From cocimo cecchi in the bug report [https://bugzilla.gnome.org/show_bug.cgi?id=693195](https://bugzilla.gnome.org/show_bug.cgi?id=693195) : I now pushed a fix for this to git master, and verified it working correctly.
If you're testing packages and not building from source, make sure you're testing with a distribution that builds Nautilus with Tracker support enabled
(Ubuntu doesn't do that, at least the last version didn't).

---

### Post by mc4man on 2013-03-02
> **Mr.JJ said:**
> This bug is now fixed. But the bugfix need nautilus to be built with tracker support (bug report says the last version in ubuntu did not have tracker support). Without this we will not see the actual files/documents in the shell search.

Last I checked which admittedly was several months ago, nautilus with tracker enabled could lead to excessive cpu (don't remember if seen in both unity & Gs sessions

So maybe you should re-build the current ppa nautilus with tracker enabled & see how it performs (only takes a few minutes to build
(- have no real interest here in tracker unless it becomes default enabled & or provides something of value in a ubuntu session.

Edit: - don't particulary see any issue with nautilus (3.7.x) being built with 'enable-tracker=yes', whether that gives you whatever you're missing don't know, only using some of those ppa's for convience & to see when/what starts breaking a ubuntu session
(your bug link is invalid

---

### Post by VinDSL on 2013-03-02
Anyone else having issues with "intuitive" caribou-antler keyboards popping up, all over the place, for no reason?

One keyboard takes up half the display when I'm logging in via GDM.

A smaller one pops up on the desktop, when I first login.

Occasionally, one will pop up, when I click an indicator, in the top panel, and so forth, and so on.

These virtual keyboards disappear as soon as I mouse-over them,  but it's getting irritating. :P

**EDIT**

BTW...

```
vindsl@Zuul:~$ apt-cache policy caribou-antler
caribou-antler:
  Installed: 0.4.8-0ubuntu1~raring2
  Candidate: 0.4.8-0ubuntu1~raring2
  Version table:
 *** 0.4.8-0ubuntu1~raring2 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
     0.4.4-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ raring/universe i386 Packages
        500 http://samaritan.ucmerced.edu/ubuntu/ raring/universe i386 Packages
vindsl@Zuul:~$
```

---

### Post by cariboo on 2013-03-02
That's what they get for naming libraries after me. :-D

---

### Post by VinDSL on 2013-03-02
> **cariboo907 said:**
> That's what they get for naming libraries after me. :-D
Bwahahaha!  :D

---

### Post by jbicha on 2013-03-02
> **VinDSL said:**
> Anyone else having issues with "intuitive" caribou-antler keyboards popping up, all over the place, for no reason?


Why don't you just uninstall caribou-antler?

---

### Post by VinDSL on 2013-03-02
> **jbicha said:**
> Why don't you just uninstall caribou-antler?
Wants to remove gnome & gnome-core, along with caribou-antler.  :(

---

### Post by jbicha on 2013-03-02
Ok, and why do you need 'gnome' or 'gnome-core' installed? The ubuntu-gnome-desktop package is good enough for me. ;)

---

### Post by VinDSL on 2013-03-02
> **jbicha said:**
> Ok, and why do you need 'gnome' or 'gnome-core' installed? The ubuntu-gnome-desktop package is good enough for me. ;)
Okay, here goes... :D

BBL

---

### Post by VinDSL on 2013-03-02
Well, you aren't going to believe this, but... 

```
vindsl@Zuul:~$ apt-cache policy caribou-antler
caribou-antler:
  Installed: (none)
  Candidate: 0.4.8-0ubuntu1~raring2
  Version table:
     0.4.8-0ubuntu1~raring2 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ raring/main i386 Packages
        500 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main i386 Packages
     0.4.4-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ raring/universe i386 Packages
        500 http://samaritan.ucmerced.edu/ubuntu/ raring/universe i386 Packages

vindsl@Zuul:~$ apt-cache policy gnome
gnome:
  Installed: (none)
  Candidate: 1:3.4+7ubuntu3
  Version table:
     1:3.4+7ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ raring/universe i386 Packages
        500 http://samaritan.ucmerced.edu/ubuntu/ raring/universe i386 Packages

vindsl@Zuul:~$ apt-cache policy gnome-core
gnome-core:
  Installed: (none)
  Candidate: 1:3.4+7ubuntu3
  Version table:
     1:3.4+7ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ raring/universe i386 Packages
        500 http://samaritan.ucmerced.edu/ubuntu/ raring/universe i386 Packages

vindsl@Zuul:~$ apt-cache policy ubuntu-gnome-desktop
ubuntu-gnome-desktop:
  Installed: 0.7
  Candidate: 0.7
  Version table:
 *** 0.7 0
        500 http://archive.ubuntu.com/ubuntu/ raring/universe i386 Packages
        500 http://samaritan.ucmerced.edu/ubuntu/ raring/universe i386 Packages
        100 /var/lib/dpkg/status

```


Caribou-antler keyboards are still popping up!  Go figure...

At least I have a nice blue background now, on GRUB & Plymouth.  LoL!  :D

---

### Post by Mr.JJ on 2013-03-03
> **mc4man said:**
> ...have no real interest here in tracker unless it becomes default enabled & or provides something of value in a ubuntu session...
The gnome shell file/document search is one of the core areas of the gnome desktop. I don't think the staging or gnome 3 team ppa versions has to worry about the ubuntu session. We are not talking about the default repo version anyways.

> **mc4man said:**
> ...don't particulary see any issue with nautilus (3.7.x) being built with 'enable-tracker=yes'...
Thats good news!!!. Hopefully jeremy/ricotz will include this in the ppa.

> **mc4man said:**
> your bug link is invalid
Updated the post, the colon at the end was not part of the link.

---

### Post by VinDSL on 2013-03-09
Been getting this error, for the past week_or_so:

```
E: /var/cache/apt/archives/colord_0.1.30-0ubuntu3_i386.deb: trying to overwrite '/usr/share/colord/icons/color-munki-photo-ambient.svg', which is also in package libcolord-common 0.1.28-0ubuntu1~13.04~ricotz0
```

I've tried various tricks, to get rid of it, but no joy.

It's more of an annoyance than anything, but...

Anyone know how to fix this problem?!?!?

---

### Post by jbicha on 2013-03-09
Uninstall libcolord-common

---

### Post by Harry33 on 2013-03-09
> **VinDSL said:**
> Been getting this error, for the past week_or_so:

```
E: /var/cache/apt/archives/colord_0.1.30-0ubuntu3_i386.deb: trying to overwrite '/usr/share/colord/icons/color-munki-photo-ambient.svg', which is also in package libcolord-common 0.1.28-0ubuntu1~13.04~ricotz0
```

I've tried various tricks, to get rid of it, but no joy.

It's more of an annoyance than anything, but...

Anyone know how to fix this problem?!?!?

Where did you get the package libcolord-common (0.1.28-0ubuntu1) from?
There is no such package in RR repos.
Perhaps you could remove that one first.

---

### Post by VinDSL on 2013-03-09
> **jbicha said:**
> Uninstall libcolord-common
I'll give it a toss... Thanks!


> **Harry33 said:**
> Where did you get the package libcolord-common (0.1.28-0ubuntu1) from?
There is no such package in RR repos.
Perhaps you could remove that one first.
Looks like it was from Ricotz Testing (only Ricotz PPA I have enabled)...

```
vindsl@Zuul:~$ apt-cache policy libcolord-common
libcolord-common:
  Installed: 0.1.28-0ubuntu1~13.04~ricotz0
  Candidate: 0.1.28-0ubuntu1~13.04~ricotz0
  Version table:
 *** 0.1.28-0ubuntu1~13.04~ricotz0 0
        100 /var/lib/dpkg/status
vindsl@Zuul:~$
```

BBL  ;)

---

### Post by VinDSL on 2013-03-09
Worked a treat!

I got rid of that library.  Then, on the next go_around, colord upgraded without error.

Maybe that lib flew in, under the radar, last week -- a case of bad timing, on my part, or whatever.

Sometimes... something sneeks into a package that shouldn't be there.  It gets corrected almost immediately, but if you upgraded at (say) 9:00 AM, instead of 10:00 AM, you get the "surprise package". :D

I *suspect* something like that happened here...

---

### Post by VinDSL on 2013-03-10
Hrm.

Well, I wanted to wait n' see -- do a few restarts, cold boots -- et cetera, but...

Ever since I removed libcolord-common, I haven't seen any more caribou-antler virtual keyboards.

Coincidence? Maybe.

If you'll remember (a few posts above) I purged the caribou-antler package, but the keyboards kept popping up, on every login.

I had a gut feeling one of the libraries/scripts/binaries/whatever had the antler keyboards hard-coded into it.

Anyway, *fingers crossed*. Hopefully, the virtual keyboards are gone for good...

---

### Post by mc4man on 2013-03-10
For the most part seems ok here in _Gs session_, 2 small oddities  - org.gnome.desktop.interface gtk-color-scheme has no affect anymore & Videos always opens small, resizing, closing, re-opening has no effect (will have to put up a 3.7 Videos & see there

In an _ubuntu session_ things are fairly good until g-c-c & g-s-d are upgraded, those do cause issues. Prior to with everything else default installed/shared updated only a few - 
gnome-terminal looks bad in ambiance theme
gnome-screenshot doesn't work, produces an unclosable white window the size of screenshot
gtk2 (gtkrc) apps are not themed right in ambiance
(maybe a few more, nm-applet crash is one

After g-c-c/g-s-d - 
always has an undetermined g-s-d crash on log in
custom keyboard shortcuts are non-functional
occasionally unity launcher get whacked out with no icons
(probably a bit more, as time permits

On a positive gtk-3.7+ & nautilus-3.7.+ seem fine

---

### Post by VinDSL on 2013-03-10
> **mc4man said:**
> In an _ubuntu session_ [...]
My Unity sessions have been trashed, ever since I started running Gnome Staging. The thing is, Unity looks/acts horrible, only when I do a conventional login via GDM or LightDM.

However, I discovered that if I load Unity from inside a GS session (replace the Gnome-Shell DE with Unity) then Unity looks/works great -- never been better, actually.  Go figure!

All I do is:
[LIST]
[*]Login to GS via GDM
[*]Wait for GS to fully load (takes a minute or two on this rig)
[*]Open a terminal, type:
```
unity --replace
```[/LIST]
Unity will start replacing GS.

At some point, the terminal dialog will lag-out (and eventually timeout) on a warning message complaining:```
Compiz (decor) - Warn: No default decoration found, placement will not be correct.
```I simply close the terminal window when that happens -- Unity continues to load -- and life is good.

Kind of a convoluted way of starting Unity, but it works. :)

I'm at a loss to explain why Unity is so janky, when I start it from GDM or LightDM -- but, it works perfectly from inside a GS session.

---

### Post by mc4man on 2013-03-10
> **VinDSL said:**
> My Unity sessions have been trashed, ever since I started running Gnome Staging. The thing is, Unity looks/acts horrible, only when I do a conventional login via GDM or LightDM.

However, I discovered that if I load Unity from inside a GS session (replace the Gnome-Shell DE with Unity) then Unity looks/works great -- never been better, actually.  Go figure!

Will have to give that a curiosity try, - dumped the install I commented on above, may put a new *ppa one in later

At least here the unity session was sorta ok, especially with older g-c-c & g-s-d.

---

### Post by hugmenot on 2013-03-11
Using the Gnome3 and the Ricotz Testing PPAs I now get very choppy rendering in Gnome Shell and even a very choppy mouse cursor. It&#8217;s fine in mutter alone and metacity, and it&#8217;s even fine in the GS based GDM login screen.

Is anyone else seeing this? I have Intel graphics.

---

### Post by hugmenot on 2013-03-11
> **hugmenot said:**
> Using the Gnome3 and the Ricotz Testing PPAs I now get very choppy rendering in Gnome Shell and even a very choppy mouse cursor. It&#8217;s fine in mutter alone and metacity, and it&#8217;s even fine in the GS based GDM login screen.

Is anyone else seeing this? I have Intel graphics.

Whelp. After intense studying of gsettings keys (a freshly created user didn&#8217;t have this) I figured that I had screen magnifier on, with no magnification. There&#8217;s no way to tell that it is enabled. Must&#8217;ve hit the wrong keyboard shotcuts.

---

### Post by zika on 2013-03-12
Is there extension to hide top bar for us that are using Gnome3 PPAs?

---

### Post by VinDSL on 2013-04-08
They say, "A picture is worth 1000 words"...  ;)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-8-apr-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-8-apr-2013-1.png")[/INDENT]


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-8-apr-2013-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-8-apr-2013-2.png")[/INDENT]

This, too, shall pass. Not a Rhythmbox fanboi, anyway!

Just saying...

---

### Post by zika on 2013-04-09
> **VinDSL said:**
> They say, "A picture is worth 1000 words"...  ;)

This, too, shall pass. Not a Rhythmbox fanboi, anyway!

Just saying...
I can read 1000 words waiting for these pictures to show up... So, You are right...

---

### Post by philinux on 2013-04-09
Nice video review of 3.8

[http://www.techdrivein.com/2013/04/gnome-38-in-nutshell-video.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+techdrivein+%28Tech+Drive-in%29](http://www.techdrivein.com/2013/04/gnome-38-in-nutshell-video.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+techdrivein+%28Tech+Drive-in%29)

---

### Post by Cavsfan on 2013-04-09
Not sure if this has been covered alreadly but here it is:

Upcoming Features for 13.04
While Ubuntu GNOME 13.04 will ship with GNOME 3.6 by default (like 12.10), GNOME 3.8 will be available in the GNOME 3 PPA. 

[https://wiki.ubuntu.com/UbuntuGNOME/](https://wiki.ubuntu.com/UbuntuGNOME/)

So, 3.8 is optional. Once May 9th gets here I'll have a spare partition so I might try both 3.6 and 3.8 at the same time. :)

---

### Post by VinDSL on 2013-04-10
> **philinux said:**
> Nice video review of 3.8

[http://www.techdrivein.com/2013/04/gnome-38-in-nutshell-video.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+techdrivein+%28Tech+Drive-in%29](http://www.techdrivein.com/2013/04/gnome-38-in-nutshell-video.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+techdrivein+%28Tech+Drive-in%29)
WoW!

Wish I could make my 'search' work like that!  :)

---

### Post by VinDSL on 2013-04-10
> **zika said:**
> I can read 1000 words waiting for these pictures to show up... So, You are right...
Sorry!  :)

BTW, I got Rhythmbox working, thanks to your post [over here]("http://ubuntuforums.org/showthread.php?t=2133389&highlight=rhythmbox").

I also fixed another problem, too.

'rhythmbox-client' was causing Conky to hard-lock, every time I started Rhythmbox (I've been using 'rhythmbox-client' to print the 'title' in Conky).

I came up with code that uses 'qdbus/mpris' instead of 'rhythmbox-client'.  So far, so good...


```
${if_running rhythmbox}
${voffset -13}${font DroidSans:bold:size=8}${color4}RHYTHMBOX${offset 8}${color6}${voffset -2}${hr 1}${font}
${voffset 4}${font DroidSans:size=8.25}${color3}${if_match "${execpi 2 expr length "`qdbus org.mpris.MediaPlayer2.rhythmbox /\org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14-""`"}" >= "48"}${alignr 15}${scroll 38 4* ${execi 2 qdbus org.mpris.MediaPlayer2.rhythmbox /\org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14-""}}${font}${else}${alignc}${execi 2 qdbus org.mpris.MediaPlayer2.rhythmbox /\org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14-""}${font}${endif}${endif}

```

* Have you noticed that the new Ubu Forum software is wrapping long lines of code (see above)?
That's actually just 3-lines of code.  Looks fine in the editor, but displays terribly in the threads.

I have no control over this...  ;)

---

### Post by VinDSL on 2013-04-10
As a side-note...

The screen blanker has been working lately, more or less.  It doesn't trap me on the GDM login screen any more.

So, I turned screen blanking back on, during the session (15 minutes).

The problem now is, if the walk away from this machine for an extended length of time, it will awake from GDM, but during the rest of the session, the timeout drops from 15 minutes -> 30 seconds of inactivity.  Sheesh!

Guess I go turn-off the screen blanking again...

---

### Post by zika on 2013-04-11
> **VinDSL said:**
> Sorry!  :)
No problem... ;)

---

### Post by Cavsfan on 2013-04-11
> **VinDSL said:**
> ```
${if_running rhythmbox}
${voffset -13}${font DroidSans:bold:size=8}${color4}RHYTHMBOX${offset 8}${color6}${voffset -2}${hr 1}${font}
${voffset 4}${font DroidSans:size=8.25}${color3}${if_match "${execpi 2 expr length "`qdbus org.mpris.MediaPlayer2.rhythmbox /\org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14-""`"}" >= "48"}${alignr 15}${scroll 38 4* ${execi 2 qdbus org.mpris.MediaPlayer2.rhythmbox /\org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14-""}}${font}${else}${alignc}${execi 2 qdbus org.mpris.MediaPlayer2.rhythmbox /\org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14-""}${font}${endif}${endif}

```

* Have you noticed that the new Ubu Forum software is wrapping long lines of code (see above)?
That's actually just 3-lines of code.  Looks fine in the editor, but displays terribly in the threads.

I have no control over this...  ;)

I see just three lines of code the last being VERY long and it looks fine to me. It couldn't be my ginormous 28" monitor doing this could it? :p

---

### Post by mcellius on 2013-04-11
> **Cavsfan said:**
> I see just three lines of code the last being VERY long and it looks fine to me. It couldn't be my ginormous 28" monitor doing this could it? :p

Nah, I see just three lines of code even on my not-so-big laptop screen.

---

### Post by mc4man on 2013-04-11
> **VinDSL said:**
> Sorry!  :)

BTW, I got Rhythmbox working, thanks to your post [over here]("http://ubuntuforums.org/showthread.php?t=2133389&highlight=rhythmbox").

I also fixed another problem, too.

'rhythmbox-client' was causing Conky to hard-lock, every time I started Rhythmbox (I've been using 'rhythmbox-client' to print the 'title' in Conky).

I came up with code that uses 'qdbus/mpris' instead of 'rhythmbox-client'.  So far, so good...


```
${if_running rhythmbox}
${voffset -13}${font DroidSans:bold:size=8}${color4}RHYTHMBOX${offset 8}${color6}${voffset -2}${hr 1}${font}
${voffset 4}${font DroidSans:size=8.25}${color3}${if_match "${execpi 2 expr length "`qdbus org.mpris.MediaPlayer2.rhythmbox /\org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14-""`"}" >= "48"}${alignr 15}${scroll 38 4* ${execi 2 qdbus org.mpris.MediaPlayer2.rhythmbox /\org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14-""}}${font}${else}${alignc}${execi 2 qdbus org.mpris.MediaPlayer2.rhythmbox /\org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14-""}${font}${endif}${endif}

```

* Have you noticed that the new Ubu Forum software is wrapping long lines of code (see above)?
That's actually just 3-lines of code.  Looks fine in the editor, but displays terribly in the threads.

I have no control over this...  ;)

Not in firefox but certainly bad  in chromium & google-chrome

---

### Post by VinDSL on 2013-04-11
> **mc4man said:**
> Not in firefox but certainly bad  in chromium
OMG!!!  Why didn't I think of that?  :redface:

So, it's a rendering problem in Chromium (checked both stable & unstable)...

I'm in Fx right now, and it looks fine.  Hold on, I'll check Opera.

Yep, looks fine in Opera Next, too.  Well, shiver_me_timbers!  

Lesson learned.  I'll see if I can come up with a fix.

Thanks, all!

---

### Post by VinDSL on 2013-04-28
Don't know what changed, but...

As of today, I can now log into a Unity session via GDM, without issue(s).

Unity looks great. Gnome3 Staging looks great.

Wallpaper works in both DEs - custom icons - fonts - window decorations - panels - everything is perfect in Unity & GS 3.8.1 now!

---

### Post by Branimir on 2013-04-28
Are you sure. I have installed now gnome3/staging and ricotz testing. Wallpapers does not work in Unity. Actually background in Unity is complete mess...

---

### Post by cariboo on 2013-04-28
I just upgraded to Saucy, but the Gnome3 ppas are still only listing Raring, does anyone know if this will change soon?

---

### Post by VinDSL on 2013-04-28
> **Branimir said:**
> Are you sure. I have installed now gnome3/staging and ricotz testing. Wallpapers does not work in Unity. Actually background in Unity is complete mess...
Yep, Unity is working for me.

Here are [a couple of screenies]("http://ubuntuforums.org/showthread.php?t=2131337&page=21&p=12623414&viewfull=1#post12623414") from this morning.

And, I've cold-booted this machine several times since then.

The only way I could make Unity work, before today, was to log into GS, open a terminal window, and replace GS with Unity.

Now, I can directly log into Unity via GDM, without any monkeying around...

---

### Post by Harry33 on 2013-04-29
> **cariboo907 said:**
> I just upgraded to Saucy, but the Gnome3 ppas are still only listing Raring, does anyone know if this will change soon?

Perhaps the devs are waiting for new builds of the future Gnome 3.10.
The Gnome3 PPA (raring branch) will stay at Gnome 3.8.
Gnome Testing PPA, however, has already the saucy flavor uploaded.

---

### Post by VinDSL on 2013-05-04
Heh!  I *think* *3.9.1+git20130503.d9a4688e-0ubuntu1~13.10~ricotz0* broke Unity.

Either that, or today's Saucy upgrades...

Things are looking up!  I was getting bored.  :D

---

### Post by sammiev on 2013-05-04
> **VinDSL said:**
> Heh!  I *think* *3.9.1+git20130503.d9a4688e-0ubuntu1~13.10~ricotz0* broke Unity.

Either that, or today's Saucy upgrades...

Things are looking up!  I was getting bored.  :D

Shows much the same here. Ubuntu Tweak broken and same with sowtware center. The fun begins. :)

---

### Post by cariboo on 2013-05-04
I just updated to gnome-shell 3.9.1, and things seem to be working as they should, I don't have Unity installed on this system, so no problems there.

One thing I have found, if the systems goes into suspend, only the external monitor lights up when he system wakes up, my netbook screen stays black. I haven't bothered to look yet whether this is an early Saucy problem, or Gnome3.

---

### Post by VinDSL on 2013-05-05
> **sammiev said:**
> Shows much the same here. [...]> **cariboo907 said:**
> I just updated to gnome-shell 3.9.1, and things seem to be working as they should [...]
Well, drat!  False alarm. That was short-lived...

Unity is working fine, now.  I just shelled right into it.  :mad:

Must have been yet another example of bad timing.

I swear, for the past 12 hours, Unity was borked -- all I was seeing was a default blue Gnome wallpaper -- no panels -- no nothing.  And, none of the usual tricks worked.

I did several incremental upgrades today.  Something_or_another must have been missing earlier...

Thanks!

---

### Post by sammiev on 2013-05-05
> **VinDSL said:**
> Well, drat!  False alarm. That was short-lived...

Unity is working fine, now.  I just shelled right into it.  :mad:

Must have been yet another example of bad timing.

I swear, for the past 12 hours, Unity was borked -- all I was seeing was a default blue Gnome wallpaper -- no panels -- no nothing.  And, none of the usual tricks worked.

I did several incremental upgrades today.  Something_or_another must have been missing earlier...

Thanks!

Just did all the updates myself and did a cold boot after. Still no Unity for me. Freezes at the login screen but gnome3 staging is working good. Will look into more later.

---

### Post by VinDSL on 2013-05-05
> **sammiev said:**
> Just did all the updates myself and did a cold boot after. Still no Unity for me. Freezes at the login screen but gnome3 staging is working good. Will look into more later.
Sorry!  I should have stated that <the above> more clearly...

I still cannot log into a Unity session, the conventional way, using a Display Manager, e.g. via GDM/LightDM.  

However...

I can, once again, shell into Unity from a Gnome-Shell session, by replacing the DE via CLI.

Here's the drill:

[LIST]
[*]Boot
[*]Log into a Gnome-Shell session via GDM.
[*]Give GS a couple of minutes to fully load any/all shell scripts, extensions, et cetera.
[*]Open a terminal and run: ```
unity --replace &
```
[*]Unity will start replacing Gnome-Shell.
[*]At some point, the DE replacement process will hang.  This is normal.
[*]Close the terminal, and the process will complete itself.
[/LIST]

I might mention, this is how I've had to start Unity for months.  

It was only recently that I could start a Unity session successfully, via the Display Manager.  ;)

---

### Post by sammiev on 2013-05-05
> **VinDSL said:**
> Sorry!  I should have stated that <the above> more clearly...

I still cannot log into a Unity session, the conventional way, using a Display Manager, e.g. via GDM/LightDM.  

However...

I can, once again, shell into Unity from a Gnome-Shell session, by replacing the DE via CLI.

Here's the drill:

[LIST]
[*]Boot
[*]Log into a Gnome-Shell session via GDM.
[*]Give GS a couple of minutes to fully load any/all shell scripts, extensions, et cetera.
[*]Open a terminal and run: ```
unity --replace &
```
[*]Unity will start replacing Gnome-Shell.
[*]At some point, the DE replacement process will hang.  This is normal.
[*]Close the terminal, and the process will complete itself.
[/LIST]

I might mention, this is how I've had to start Unity for months.  

It was only recently that I could start a Unity session successfully, via the Display Manager.  ;)

Many Thanks. I can now get into Unity, video is a little screwy on exiting a program.

---

### Post by VinDSL on 2013-05-05
> **sammiev said:**
> Many Thanks. I can now get into Unity, video is a little screwy on exiting a program.
Welcome!

It's a workaround, for sure, but it's better than nothing (literally)...  :)

---

### Post by jbicha on 2013-05-18
> **VinDSL said:**
> Sorry!  I should have stated that <the above> more clearly...

I still cannot log into a Unity session, the conventional way, using a Display Manager, e.g. via GDM/LightDM.  



I believe I fixed that now for the GNOME3 Staging PPA by merging the Ubuntu changes to gnome-session into the PPA packaging. It should be possible to run Unity now on Saucy with the GNOME3 Staging PPA (for Raring) enabled.

I think the same work would need to be done to gnome-session in the regular GNOME3 PPA but I don't have the time to test it. The work should just be adding the new user session upstart file and updating debian/rules. It's a bit of an edge case anyway since Saucy uses logind but only the GNOME3 Staging PPA uses logind (the regular GNOME3 PPA does not) and we're hesitant to change that. It's more important for us to make sure regular Saucy works and that Raring works with or without the PPAs, whether users run Unity or GNOME. And I don't know if Unity needs an update for that upstart change too...

---

### Post by VinDSL on 2013-05-18
> **jbicha said:**
> I believe I fixed that now for the GNOME3 Staging PPA by merging the Ubuntu changes to gnome-session into the PPA packaging. It should be possible to run Unity now on Saucy with the GNOME3 Staging PPA (for Raring) enabled.[...]
Thanks!  I'll do an upgrade, and check back later.

I've been tracking a problem with Conky for 6 hours -- time for a break.  LoL!

BBL

---

### Post by VinDSL on 2013-05-18
w00t!  Worked!!!

Entered right through the front door (GDM) with head held high...  :D


```
vindsl@Zuul:~$ apt-cache policy gnome-shell
gnome-shell:
  Installed: 3.9.1+git20130516.2a550e64-0ubuntu1~13.10~ricotz0
```
[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-18-may-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-18-may-2013-1.png")[/INDENT]


```
vindsl@Zuul:~$ apt-cache policy unity
unity:
  Installed: 7.0.0daily13.04.18~13.04-0ubuntu1
```
[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-18-may-2013-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-18-may-2013-2.png")[/INDENT]


```
Distro Release: Ubuntu Saucy Salamander (development branch)
Kernel Release: Linux 3.9.2-030902-generic
Gnome Release: GNOME Shell 3.9.1
Unity Release: Unity 7.0.0
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.88
Xserver Xorg Core Branch: 2:1.13.4~git20130508+server-1.13-branch.10c42f57-0ubuntu0ricotz~raring

```


Thanks, again!

---

### Post by VinDSL on 2013-05-19
Oops!

I installed lubuntu-desktop last night.  Now, I can't log into Unity via GDM.

I answered the 'call' for more Lubuntu participation in +1.  That's what you get for being a nice guy.  LoL!  :D

Anyway, that or one of the incremental upgrades I did yesterday slammed the Unity door in my face, again.

GNOME3 Staging is still loading just fine, as always.

Just saying...

---

### Post by VinDSL on 2013-05-21
Okay...

Tried to start Unity from CLI, this morning, and I'm getting a seg fault, when the icons are loading, sooo...

I went into ccsm, and the Unity Plugin was disabled.  I tried to re-enable it, and OpenGL, Scale, and so forth, and so on, but no joy.

Technically, I CAN log into Unity via GDM, but I'm getting a "unity-panel-service: process not found" error because the Unity Plugin et al. is being disabled at startup, e.g. no panels.  It's just sitting dead, at the desktop, probably because of conflicts in my Unity setup -- wobbly windows, the cube, or whatever.  A reset is probably in order.  I'll try resetting Unity, when I get a chance, this afternoon... and, go from there.

Anyway, I judge this is a conflict in Unity, not a GDM/GNOME3 problem.  ;)

---

### Post by zika on 2013-05-22
Little bump on ricotz road:
```
The following packages will be upgraded:   libgtk-3-common 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,834 kB of archives. After unpacking 60.4 kB will be used.
The following packages have unmet dependencies:
 libgtk-3-bin : Depends: libgtk-3-common (= 3.9.1~git20130515.21565e67-0ubuntu1~13.10~ricotz0) but 3.9.1~git20130522.8b1740b9-0ubuntu1~13.10~ricotz0 is to be installed.
 libgtk-3-0 : Depends: libgtk-3-common (= 3.9.1~git20130515.21565e67-0ubuntu1~13.10~ricotz0) but 3.9.1~git20130522.8b1740b9-0ubuntu1~13.10~ricotz0 is to be installed.

```

Update&#8321;: bump removed while I was posting... Thank You ricotz...

---

### Post by VinDSL on 2013-05-22
> **zika said:**
> Little bump[...]
Heh!  Wish this bump could be ironed out...  :D

```
Errors were encountered while processing:
 rhythmbox-plugin-zeitgeist
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Been hitting it for a week or two.

---

### Post by zika on 2013-05-22
> **VinDSL said:**
> Heh!  Wish this bump could be ironed out...  :D

```
Errors were encountered while processing:
 rhythmbox-plugin-zeitgeist
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Been hitting it for a week or two.
I've removed RB completelly just at the start of that bump...
Never turned back...

---

### Post by VinDSL on 2013-05-22
> **zika said:**
> I've removed RB completelly just at the start of that bump...
Never turned back...
I prefer Guayadeque, but we're supposed to be testing... LoL! 

Actually, RB isn't too bad these days, if you implement the MPRIS plugin.

---

### Post by zika on 2013-05-22
> **VinDSL said:**
> I prefer Guayadeque, but we're supposed to be testing... LoL! 

Actually, RB isn't too bad these days, if you implement the MPRIS plugin.Clementine, Guayadeque and Audacious are more than adequate for me... At least first has MPRIS... ;)
If purity of testing would be a prerequisite I would not qualify for any kind of testing...

---

### Post by sgage on 2013-05-22
> **zika said:**
> I've removed RB completelly just at the start of that bump...
Never turned back...

RB also still has this streaming bug:

[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/1153934](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/1153934)

I've been using Audacious for streaming audio, and it works great. It actually integrates better with the MPRIS extension than RB does.

---

### Post by VinDSL on 2013-05-25
w00t!  Breakage!

Latest upgrades totally borked GDM -- hard-locks this box during boot process(es).  My best guess is, it's hardware related -- PS/2 keyboard goes dormant, et cetera.  Power button still works, though...  :)

Screen displays a torrent of errors -- happened to see "Gnome Display Manager [Failed]" scroll by after the umpteenth reset. Chalk up one for serendipity!

Switching to LightDM (haven't had to use it in ages).  That allowed me to boot, but once I logged into Gnome3 Staging, I noticed some of my extensions turned janky.  

Example:  Dock-to-Dock extension (arguably a personal hack - compiled from source) autohides regardless of the settings - wasn't authored to work with 3.9.1.

DBUS MPRIS looks to be dead, too.

Continuing...

---

### Post by Harry33 on 2013-05-25
> **VinDSL said:**
> w00t!  Breakage!

Latest upgrades totally borked GDM -- hard-locks this box during boot process(es).  My best guess is, it's hardware related -- PS/2 keyboard goes dormant, et cetera.  Power button still works, though...  :)

Screen displays a torrent of errors -- happened to see "Gnome Display Manager [Failed]" after the umpteenth reset. Chalk up one for serendipity!

Switching to LightDM (haven't had to use it in ages) allowed me to boot, but once I'm logged into Gnome3 Staging, some of my extensions turned janky.  

Example:  Dock-to-Dock extension (arguably a personal hack) autohides regardless of the settings - wasn't authored to work with 3.9.1.

DBUS MPRIS looks to be dead, too.

Continuing...

Hi VinDSL,

Could you have the same bug as I do.
After upgrading (from saucy-proposed) vte3, booting stopped to tty1.
Gdm just wont work.
However, I can command startx from tty1 and that works.
I downgraded vte3 (libvte-2.90-9 and libvte-2.90-common)) back to the version 0.34.2-0ubuntu2 and that solved the booting issue.

---

### Post by VinDSL on 2013-05-25
> **Harry33 said:**
> Hi VinDSL,

Could you have the same bug as I do.
After upgrading (from saucy-proposed) libvte9, booting stopped to tty1.
Gdm just wont work.
However, I can command startx from tty1 and that works.
I downgraded libvte9 back to the version 0.34.2-0ubuntu2 and that solved the booting issue.
Hi Harry,

I'll go check -- might have snuck in under the radar.

I *usually* check all the upgrades before committing them (especially "proposed", so called) but I was tired, last night.  I just pulled the trigger, powered-down, and went to bed.

Heh!  Nasty surprise, when I attempted a boot-up, this morning.  That woke me up...  LoL! :D

BBL

---

### Post by sammiev on 2013-05-25
I'm not broken yet but I do have to login twice.

---

### Post by VinDSL on 2013-05-25
Harry steered me down the correct path.  ;)

The libvte9 version was okay, but I had to downgrade three other packages...

[INDENT][ATTACH=CONFIG]243032[/ATTACH][/INDENT]

Switched back to GDM, and it's working again.

Still trying to figure out why DBUS MPRIS is broken.  

QDBUS isn't writing any data to '/usr/lib/i386-linux-gnu/qt5/bin/qdbus'.

Continuing...

---

### Post by VinDSL on 2013-05-25
Think I found my (MPRIS) problem... affects all DEs installed on this (saucy) desktop box BTW.

Interesting read!

BUG LINK:  [https://bugs.launchpad.net/ubuntu/+source/qtchooser/+bug/1176686](https://bugs.launchpad.net/ubuntu/+source/qtchooser/+bug/1176686)

> Hmm, this is a bit complicated. qtchooser shouldn't be installed on non-development machines [...] was patched to forcefully add /usr/lib/[your-arch]/qt4/bin to PATH which is why it works for most people now (but causes Qt5 to not be easily usable [...] since the addition is before /usr/bin).

**The root problem within qtchooser itself is that it handles qdbus the same as purely development oriented binaries, so qdbus cannot be installed to /usr/bin as before, so [B][COLOR="#A52A2A"]on non-development machines qdbus is not available at all[/COLOR]** via default PATH, regardless of multi-arch or not.[/B]

**[COLOR="#A52A2A"]One more change is that qdbus has now been split to its own qdbus-qt5 package in Debian, so it will come to saucy as well[/COLOR]**.

[...] regarding qtchooser itself, I'm not sure. The upstream probably hasn't considered multi-arch so far.

Looks like the devil has appeared at our doorsteps!  LoL!  :D


TEST BUILDS:  [https://launchpad.net/~canonical-qt5-edgers/+archive/qt5-beta-proper](https://launchpad.net/~canonical-qt5-edgers/+archive/qt5-beta-proper)


Guess I'll wait for the devs to sort this.  I don't like rolling back/pinning packages... 

It's not a deal-breaker for me, anyway.  I just like seeing the song titles in Conky.  :)

---

### Post by Harry33 on 2013-05-25
> **VinDSL said:**
> Harry steered me down the correct path.  ;)

The libvte9 version was okay, but I had to downgrade three other packages...[INDENT][ATTACH=CONFIG]243032[/ATTACH][/INDENT]

Switched back to GDM, and it's working again.

Still trying to figure out why DBUS MPRIS is broken.  

QDBUS isn't writing any data to '/usr/lib/i386-linux-gnu/qt5/bin/qdbus'.

Continuing...

Hi there,

So you have the working vte3 (version 0.34.2-0ubuntu2) installed.
It would be nice to know does gdm work in your setup, if you upgrade vte3 to the version 0.34.5-1ubuntu1.

---

### Post by VinDSL on 2013-05-26
> **Harry33 said:**
> So you have the working libvte9 (version 0.34.2-0ubuntu2) installed.
libvte9 was okay.  I didn't downgrade it...

```
vindsl@Zuul:~$ apt-cache policy libvte9
libvte9:
  Installed: 1:0.28.2-5ubuntu1
  Candidate: 1:0.28.2-5ubuntu1
  Version table:
 *** 1:0.28.2-5ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
```

This is a i386 computer.  I'm seeing that as the most recent version -- the only version available, actually.

I downgraded the other packages from 0.34.5-1ubuntu1 -> 0.34.2-0ubuntu2

That's what got GDM working again, for me.  ;)

Where did you find libvte9 0.34.2-0ubuntu2 ?  I cannot find it.

I wouldn't mind trying 0.35.5-1ubuntu1, but I searched and... no joy there either.

---

### Post by Harry33 on 2013-05-26
> **VinDSL said:**
> libvte9 was okay.  I didn't downgrade it...

```
vindsl@Zuul:~$ apt-cache policy libvte9
libvte9:
  Installed: 1:0.28.2-5ubuntu1
  Candidate: 1:0.28.2-5ubuntu1
  Version table:
 *** 1:0.28.2-5ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
```

This is a i386 computer.  I'm seeing that as the most recent version -- the only version available, actually.

I downgraded the other packages from 0.34.5-1ubuntu1 -> 0.34.2-0ubuntu2

That's what got GDM working again, for me.  ;)

Where did you find libvte9 0.34.2-0ubuntu2 ?  I cannot find it.

I wouldn't mind trying 0.35.5-1ubuntu1, but I searched and... no joy there either.

Sorry for this confusion I have made.
The vte3 version that does not work with gdm (I tested on AMD 64-bit and Intel 32-bit) is** 0.34.5-1ubuntu1**.
The vte3 version that works is **0.34.2-0ubuntu2**. That is here:
[https://launchpad.net/ubuntu/+source/vte3/1:0.34.2-0ubuntu2](https://launchpad.net/ubuntu/+source/vte3/1:0.34.2-0ubuntu2)

I am talking about two packages from the same source (vte3): libvte-2.90-9 and libvte-2.90-common.

---

### Post by VinDSL on 2013-05-26
> **Harry33 said:**
> Sorry for this confusion I have made.[...]
No problem!  Those particular version numbers are a real mind-twister.  LoL!  :D
> **Harry33 said:**
> The vte3 version that works is **0.34.2-0ubuntu2**. That is here:
[https://launchpad.net/ubuntu/+source/vte3/1:0.34.2-0ubuntu2](https://launchpad.net/ubuntu/+source/vte3/1:0.34.2-0ubuntu2)

I am talking about two packages from the same source (vte3): libvte-2.90-9 and libvte-2.90-common.
Yep, that's where I snagged the packages, yesterday (pictured above).

Those are the ones that successfully resurrected GDM...  ;)

---

### Post by Harry33 on 2013-05-26
> **VinDSL said:**
> No problem!  Those particular version numbers are a real mind-twister.  LoL!  :D

Yep, that's where I snagged the packages, yesterday (pictured above).

Those are the ones that successfully resurrected GDM...  ;)

Yes, I use those same packages, in order to keep gdm going. :D

---

### Post by VinDSL on 2013-05-26
Well...

I'm back to LightDM.  LoL!  :D

I've been chomping at the bit, trying to figure out of way to install Linux 3.10 on this legacy machine.

Finally came up with a winning combination, except GDM won't work, again...

```
Current Date/Time: Sun May 26 10:45:04 MST 2013
Distro Release: Ubuntu Saucy Salamander (development branch)
Kernel Release: Linux 3.10.0-031000rc2-generic
Gnome Release: GNOME Shell 3.9.1
Unity Release: unity 7.0.0

OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.2, 128 bits)
OpenGL version string:  2.1 Mesa 9.2.0

```

LLVMpipe generation is slow, e.g. laggy, but GNOME3 Staging fired right up.  

Desktop looked wretched on Linux 3.9.2, but Linux 3.10-rc2 worked a treat...

Anyway, this'll do, until I can come up with a patch for nVidia-304 (or official support is available).

---

### Post by VinDSL on 2013-05-26
Here's a weird one for you.  Gave me goosebumps...  Really!  :D

After 4 hours of LLVMpipe lagginess, I couldn't take it anymore, soooo I started looking for a solution.

Startpage (Google proxy search engine) didn't help much -- found zillions of posts complaining about it, but that was about it.

Funny thing was, some (respected names) in these forums said, they couldn't see any difference in performance, between nVidia drivers and Nouveau.  How could that be?!?!?

Then, it dawned on me.  My debug script was reporting VMware, Inc. to be the OpenGL vendor.  Hello :confused:

After pondering this for a while, I started thinking about "/etc/modprobe.d" et al.  Seems like I blacklisted Nouveau years ago.  That couldn't be it, right?  Otherwise, why is it working, albeit horrible slow, laggy, and consuming 100% CPU usage most of the time? 

Sure enough!  Even though I (myself) hadn't blacklisted Nouveau (or it had gone to null) there was a file in "/etc/modprobe.d" called "nvidia-installer-disable-nouveau.conf".

I renamed that file, with a different extension, and restarted Saucy.  Bingo!

Updated report...

```
Current Date/Time: Sun May 26 16:34:55 MST 2013
Distro Release: Ubuntu Saucy Salamander (development branch)
Kernel Release: Linux 3.10.0-031000rc2-generic
Gnome Release: GNOME Shell 3.9.1
Unity Release: unity 7.0.0

OpenGL vendor string:   **[COLOR="#0000CD"]nouveau[/COLOR]**
OpenGL renderer string:**[COLOR="#0000CD"] Gallium 0.4 on NV4B[/COLOR]**
OpenGL version string:  2.1 Mesa 9.2.0
```

w00t!  No more LLVMpipe -- no more lagginess!

This box is flying now!  I ran GTKPerf a few times, and the results/performance are indistinguishable from nVidia-304, now.

Makes me wonder how many 1000's of others are suffering from this Nouveau blacklist/VMware "problem".  ;)

---

### Post by VinDSL on 2013-05-26
Upgraded to Linux 3.10-rc3.  GDM is working again.

Don't know if it's related to the new kernel, or the Nouveau fix.

That's a wrap, for this weekend...  ;)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-26-may-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-26-may-2013-1.png")

* Ubu 13.10 Saucy / Gnome-Shell 3.9.1 Staging / Linux 3.10-rc3 / Nouveau Gallium 0.4 / Mesa Hack[/INDENT]

---

### Post by VMC on 2013-05-27
> **VinDSL said:**
> 
After 4 hours of LLVMpipe lagginess, I couldn't take it anymore, soooo I started looking for a solution.

Startpage (Google proxy search engine) didn't help much -- found zillions of posts complaining about it, but that was about it.

Funny thing was, some (respected names) in these forums said, they couldn't see any difference in performance, between nVidia drivers and Nouveau.  How could that be?!?!?

Then, it dawned on me.  My debug script was reporting VMware, Inc. to be the OpenGL vendor.  Hello :confused:

After pondering this for a while, I started thinking about "/etc/modprobe.d" et al.  Seems like I** blacklisted Nouveau years ago**.  That couldn't be it, right?  Otherwise, why is it working, albeit horrible slow, laggy, and consuming 100% CPU usage most of the time? 

Sure enough!  Even though I (myself) hadn't blacklisted Nouveau (or it had gone to null) there was a file in "/etc/modprobe.d" called "**nvidia-installer-disable-nouveau.conf**".

I renamed that file, with a different extension, and restarted Saucy.  Bingo!

Updated report...

```
Current Date/Time: Sun May 26 16:34:55 MST 2013
Distro Release: Ubuntu Saucy Salamander (development branch)
Kernel Release: Linux 3.10.0-031000rc2-generic
Gnome Release: GNOME Shell 3.9.1
Unity Release: unity 7.0.0

OpenGL vendor string:   **[COLOR=#0000CD]nouveau[/COLOR]**
OpenGL renderer string:**[COLOR=#0000CD] Gallium 0.4 on NV4B[/COLOR]**
OpenGL version string:  2.1 Mesa 9.2.0
```

w00t!  No more LLVMpipe -- no more lagginess!

This box is flying now!  I ran GTKPerf a few times, and the results/performance are indistinguishable from nVidia-304, now.

Makes me wonder how many 1000's of others are suffering from this Nouveau blacklist/VMware "problem".  ;)
I'm unsure exactly what this may mean, because if you install nvidia proprietary using "*.run" file it requires that nouveau be blacklisted  , and will create nvidia-installer-disable-nouveau.con for you. I read a few pages back, thinking this may reference something else, but couldn't find anything.

---

### Post by VinDSL on 2013-05-27
> **VMC said:**
> I'm unsure exactly what this may mean, because if you install nvidia proprietary using "*.run" file it requires that nouveau be blacklisted  , and will create nvidia-installer-disable-nouveau.con for you. I read a few pages back, thinking this may reference something else, but couldn't find anything.
Okay, here's my *thinking*...  ;)

I have a kernel fetish -- cannot stand it, unless I'm running the latest mainline kernel -- probably a psychological defect, second only to my addiction to Conky.

I tried to install Linux 3.10-rc1, last week, but this is a legacy machine, which requires nVidia 304.xx drivers (currently).

nVidia-304 has not been patched for Linux 3.10.  It causes the Linux 3.10 install to fail, because the initial nVidia module won't build.

Fast forward... I saw a benchmark comparison -- nVidia vs Nouveau -- while surfing the web.  Bottom line:  Nouveau performed slight better than the latest nVidia drivers, with the Mesa Hack that I already have installed.

I started thinking... why don't I just purge nVidia-304 and install Nouveau?!?!?  That way, I can install Linux 3.10 without having the nVidia drivers booger_things_up.

Sure enough, this worked, but I was stuck in LLVMpipe mode, which is slow as snot.

When I'd had my fill of the LLVMpipe lagginess, I started looking for a solution.  After all, some ppl said they couldn't see any difference in performance -- nVidia vs Nouveau.

As I was sitting here, mulling it over, drinking coffee, and listening to [90's Alternative Rock]("http://www.181.fm/playing.php?station=181-90salt&embed=1"), it occurred to me that I most assuredly had blacklisted Nouveau, in the past.  While I was checking into it, that's when I discovered that Nouveau was indeed blacklisted. Soooo, I renamed the conf file (disabled it) and restarted Saucy.

Dude, this thing came up like a ball_of_fire -- day n' night difference!  :)

I still don't know why the OpenGL vendor string said VMware, Inc. or why it changed to Nouveau.  By then, I was tired of playing around with it, and I had accomplished what I wanted to do, so I didn't investigate further.

Make sense?!?!?

**Nouveau Blacklisted: Super slow and laggy...**
```
Current Date/Time: Sun May 26 10:45:04 MST 2013
Distro Release: Ubuntu Saucy Salamander (development branch)
Kernel Release: Linux 3.10.0-031000rc2-generic
Gnome Release: GNOME Shell 3.9.1
Unity Release: unity 7.0.0

OpenGL vendor string:   **[COLOR="#0000CD"]VMware, Inc[/COLOR]**.
OpenGL renderer string: **[COLOR="#0000CD"]Gallium 0.4 on llvmpipe (LLVM 3.2, 128 bits)[/COLOR]**
OpenGL version string:  2.1 Mesa 9.2.0

```


**Nouveau Enabled: Performs fast (or faster) than nVidia-304...**
```
Current Date/Time: Sun May 26 16:34:55 MST 2013
Distro Release: Ubuntu Saucy Salamander (development branch)
Kernel Release: Linux 3.10.0-031000rc2-generic
Gnome Release: GNOME Shell 3.9.1
Unity Release: unity 7.0.0

OpenGL vendor string:   **[COLOR="#0000CD"]nouveau[/COLOR]**
OpenGL renderer string:**[COLOR="#0000CD"] Gallium 0.4 on NV4B[/COLOR]**
OpenGL version string:  2.1 Mesa 9.2.0
```

---

### Post by rezzo on 2013-05-31
Today update my 13.04 with gnome3 and stage ppa and something is broken, I can't use gnome shell. xD

---

### Post by VinDSL on 2013-05-31
> **rezzo said:**
> I can't use gnome shell. xD
Er...

Which Gnome-Shell? Gnome3 Staging 3.9.2 is working fine, here...  ;)

```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 12.12.06 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch:" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo  && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 12.12.06 (vindsl.com) ~
Current Date/Time: Fri May 31 15:38:25 MST 2013
Distro Release: Ubuntu Saucy Salamander (development branch)
Kernel Release: Linux 3.10.0-031000rc3-generic
Gnome Release: GNOME Shell 3.9.2
Unity Release: unity 7.0.0

OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV4B
OpenGL version string:  2.1 Mesa 9.2.0

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 106
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2+edgers
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Xserver Xorg Core Branch:
  Installed: 2:1.13.4~git20130508+server-1.13-branch.10c42f57-0ubuntu0ricotz~raring

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[02]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (338x270 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 
```

---

### Post by Harry33 on 2013-06-01
> **VinDSL said:**
> Er...

Which Gnome-Shell? Gnome3 Staging 3.9.2 is working fine, here...  ;)



And so is gnome-shell 3.8.2 + Gnome3 and Gnome3 Staging PPA too.

---

### Post by VinDSL on 2013-06-01
> **Harry33 said:**
> And so is gnome-shell 3.8.2 + Gnome3 and Gnome3 Staging PPA too.
Hi Harry,

By any chance, are you using edgers/saucy?

I've been putting off switching from edgers/raring -> edgers/saucy.  

*Thought* about doing it today, but edgers/saucy wants to hold-back pango 1.0 upgrades et al.

Flags are flying, and red-lights flashing, in my mind, you know?!?!?

Don't *feel* like playing Russian Roulette yet today (maybe later). Prudence is keeping me from pulling_the_trigger...   ;)

---

### Post by xeizo on 2013-06-01
I installled the whole gnome-shell stuff up to 3.9.2 on my incrementally upgraded 13.10, switched to GDM of course, it works rather well even though I had to make a few adjustments in gnome-tweak-tool for my liking. Luckily gtt worked in 3.8.2 before I did the last upgrade to 3.9.2, when gnome-tweak-tool became autoremoved but the changes were sticky. Anyway, basically it works, and with a more "stable" feel to it than any other earlier gnome-shell release I've tested. Looks promising, too early to say if it's preferrable to Unity but Nautilus crashes way to often in Unity these days not so in Gnome-Shell ...

---

### Post by zika on 2013-06-02
> **VinDSL said:**
> Hi Harry,

By any chance, are you using edgers/saucy?

[B] I've been putting off switching from edgers/raring -> edgers/saucy.  

*Thought* about doing it today, but edgers/saucy wants to hold-back pango 1.0 upgrades et al.
[/B]
Flags are flying, and red-lights flashing, in my mind, you know?!?!?

Don't *feel* like playing Russian Roulette yet today (maybe later). Prudence is keeping me from pulling_the_trigger...   ;)
Are You sure that comes from Xorg_Edgers...?
I've just glanced through that and dist-upgrade wants to strip whole install to the bare metal... ;)

---

### Post by VinDSL on 2013-06-02
> **zika said:**
> Are You sure that comes from Xorg_Edgers...?
I've just glanced through that and dist-upgrade wants to strip whole install to the bare metal... ;)
I didn't craft that question very well -- been coding all day, and my brain was fried.  LoL!  :D

Pango doesn't come from the edgers PPA.  However...

When I went to upgrade the edgers PPA to saucy, in Synaptic, pango (as you said) wanted to strip my install to the bare metal, and it freaked me out.

I went ahead and upgraded edgers manually, and let the sleeping pango dogs lay...

---

### Post by zika on 2013-06-02
In a zeitnot: any easy way to kill (as terminal as possible) on-screen keyboard on GDM login screen apart from click on keyboard button?

---

### Post by Harry33 on 2013-06-02
> **VinDSL said:**
> Hi Harry,

By any chance, are you using edgers/saucy?

I've been putting off switching from edgers/raring -> edgers/saucy.  

*Thought* about doing it today, but edgers/saucy wants to hold-back pango 1.0 upgrades et al.

Flags are flying, and red-lights flashing, in my mind, you know?!?!?

Don't *feel* like playing Russian Roulette yet today (maybe later). Prudence is keeping me from pulling_the_trigger...   ;)

I am using the nvidia-319 package from xorg-edgers.
However, I think pango1.0 issues are not due to edgers.
Instead, Gnome3 and Gnome Testing PPA's have different pango1.0 (1.34.1) than saucy's pango1.0 (1.32.5-5).
They depend of different libharfbuzz and that can create problems.

It seems after all it is a good idea to get rid of Gnome3 PPA (raring) and Gnome3 Staging PPA (raring) and thus Gnome Testing PPA too.

---

### Post by zika on 2013-06-02
> **Harry33 said:**
> I am using the nvidia-319 package from xorg-edgers.
However, I think pango1.0 issues are not due to edgers.
Instead, Gnome3 and Gnome Testing PPA's have different pango1.0 (1.34.1) than saucy's pango1.0 (1.32.5-5).
They depend of different libharfbuzz and that can create problems.

It seems after all it is a good idea to get rid of Gnome3 PPA (raring) and Gnome3 Staging PPA (raring) and thus Gnome Testing PPA too.I'm not sure if ppa-purge works for Ricotz and Gnome3, at least clean ppa-purge... ;)
Question: Is Gnome3 PPAs still needed for Ricotz's PPAs (E,S,T)?
I'ma asking because I can not derive a clean way of purging Ricotz's PPAs...
If there is a way please tell me... ;)

---

### Post by sgage on 2013-06-02
> **zika said:**
> I'm not sure if ppa-purge works for Ricotz and Gnome3, at least clean ppa-purge... ;)
Question: Is Gnome3 PPAs still needed for Ricotz's PPAs (E,S,T)?
I'ma asking because I can not derive a clean way of purging Ricotz's PPAs...
If there is a way please tell me... ;)

I've never been able to cleanly ppa-purge the ricotz PPA. I've had good luck with the gnome3-team PPAs though. The package versioning just gets to be a bit too weird in ricotz for ppa-purge to handle, it seems.

---

### Post by zika on 2013-06-02
> **sgage said:**
> I've never been able to cleanly ppa-purge the ricotz PPA. I've had good luck with the gnome3-team PPAs though. The package versioning just gets to be a bit too weird in ricotz for ppa-purge to handle, it seems.Yeap, G3 PPAs ppa-purge like it should...

---

### Post by Harry33 on 2013-06-02
> **zika said:**
> I'm not sure if ppa-purge works for Ricotz and Gnome3, at least clean ppa-purge... ;)
Question: Is Gnome3 PPAs still needed for Ricotz's PPAs (E,S,T)?
I'ma asking because I can not derive a clean way of purging Ricotz's PPAs...
If there is a way please tell me... ;)

Due to mixed dependencies even purging Gnome3 Staging PPA alone is a bit difficult now.
Saucy is using newer harfbuzz than those PPA's, yet the PPA's has got newer pango (depending on older harfbuzz).
So, it is difficult.
I did it manually source by source.

---

### Post by zika on 2013-06-02
> **Harry33 said:**
> Due to mixed dependencies even purging Gnome3 Staging PPA alone is a bit difficult now.
Saucy is using newer harfbuzz than those PPA's, yet the PPA's has got newer pango (depending on older harfbuzz).
So, it is difficult.
I did it manually source by source.
I managed to revert all except ricotz/testing...
For ricotz/experimental a little bit of juggling was needed around totem and gstreamer but I've managed that...
So, I'm left with only ricotz/testing and even attempts to do that by hand from Synaptic are unsuccesfull since I get a bare-metal offers...
I've tried with ```
sudo aptitude reinstall '?version(ricotz)'/saucy -s
```but even that gave me a list for removal bigger than a list of installed files I suppose... ;)
I've even tried with making a list by hand:```
dpkg -l |grep ricotz |grep ii
```... No way... But I'm getting closer... ;)

---

### Post by Harry33 on 2013-06-02
> **zika said:**
> I managed to revert all except ricotz/testing...
For ricotz/experimental a little bit of juggling was needed around totem and gstreamer but I've managed that...
So, I'm left with only ricotz/testing and even attempts to do that by hand from Synaptic are unsuccesfull since I get a bare-metal offers...
I've tried with ```
sudo aptitude reinstall '?version(ricotz)'/saucy -s
```but even that gave me a list for removal bigger than a list of installed files I suppose... ;)
I've even tried with making a list by hand:```
dpkg -l |grep ricotz |grep ii
```... No way... But I'm getting closer... ;)

Gnome Testing PPA is also quite difficult to disable because a number of sources (like gnome-shell) depends on other package versions in the same PPA,
So, downgrading one of them will usually leave broken dependencies left.
You need to manually install (with dpkg) in console or terminal several packages at the same time.
If you have already disabled all other PPA, why not download all sources there is in the Testing PPA and then install them from your HDD or SDD with dpkg, all at the same time.
If dpkg cannot configure them all, just repeat the same installing command and perhaps use --auto-reconfigure.

---

### Post by ricotz on 2013-06-03
Sometimes it might be better to wait for the needed rebuilds which in case of webkitgtk takes quite some time. ;)

---

### Post by zika on 2013-06-03
> **ricotz said:**
> Sometimes it might be better to wait for the needed rebuilds which in case of webkitgtk takes quite some time. ;)Just to clarify: I am not trying to turn ricotz/testing off because of broken (at this moment) dependencies but just to test vanilla Saucy... I do appreciate Your work and will be back to Your PPAs on other install without a shed of doubt... If I've got Your message right... ;)
To misuse Your message to ask You following (already asked here): Do we still need Gnome3 PPAs with Your PPAs since Gnome3 (some of them) do not have Saucy branch (really) active...? :popcorn:

---

### Post by ricotz on 2013-06-03
> **zika said:**
> Just to clarify: I am not trying to turn ricotz/testing off because of broken (at this moment) dependencies but just to test vanilla Saucy... I do appreciate Your work and will be back to Your PPAs on other install without a shed of doubt... If I've got Your message right... ;)
To misuse Your message to ask You following (already asked here): Do we still need Gnome3 PPAs with Your PPAs since Gnome3 (some of them) do not have Saucy branch (really) active...? :popcorn:

They are not strictly needed for *saucy* anymore. Although the systemd-enabled bits from Gnome3 Staging PPA are useful (gdm, g-c-c, g-s-d, gnome-session). Also the Gnome3 PPA has some newer versions too which aren't in saucy yet.

---

### Post by zika on 2013-06-03
> **ricotz said:**
> They are not strictly needed for *saucy* anymore. Although the systemd-enabled bits from Gnome3 Staging PPA are useful (gdm, g-c-c, g-s-d, gnome-session). Also the Gnome3 PPA has some newer versions too which aren't in saucy yet.So, in a nutshell we do want Raring branches of Gnome3 PPAs?
When we can expect Saucy branches?
I've gave up reverting to vanilla Saucy... ;)

---

### Post by VinDSL on 2013-06-04
> **Harry33 said:**
> [...] Gnome3 and Gnome Testing PPA's have different pango1.0 (1.34.1) than saucy's pango1.0 (1.32.5-5).

They depend of different libharfbuzz and that can create problems.
Everything got sorted, on my most recent dist-upgrade...

```
vindsl@Zuul:~$ apt-cache policy libharfbuzz0a
libharfbuzz0a:
  Installed: 0.9.18-3
  Candidate: 0.9.18-3
  Version table:
 *** 0.9.18-3 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
     0.9.18-3~raring1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ raring/main i386 Packages

vindsl@Zuul:~$ apt-cache policy libpango-1.0-0
libpango-1.0-0:
  Installed: 1.34.1-0ubuntu1~13.10~ricotz1
  Candidate: 1.34.1-0ubuntu1~13.10~ricotz1
  Version table:
 *** 1.34.1-0ubuntu1~13.10~ricotz1 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
     1.34.1-0ubuntu1~13.04~ricotz1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ raring/main i386 Packages
     1.32.5-5build1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
```

No bare-metal removal...  ;)

---

### Post by Harry33 on 2013-06-05
> **VinDSL said:**
> Everything got sorted, on my most recent dist-upgrade...

*********
No bare-metal removal...  ;)

:) I did the bare-metal removal. That went fine through.
Not going back to Gnome3 or Gnome3 Staging before they have a reasonable saucy branch in there.
Most of the raring branch packages in those PPA's are copied from saucy anyway.

---

### Post by zika on 2013-06-05
> **VinDSL said:**
> Everything got sorted, on my most recent dist-upgrade...

```
vindsl@Zuul:~$ apt-cache policy libharfbuzz0a
libharfbuzz0a:
  Installed: 0.9.18-3
  Candidate: 0.9.18-3
  Version table:
 *** 0.9.18-3 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
     0.9.18-3~raring1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ raring/main i386 Packages

vindsl@Zuul:~$ apt-cache policy libpango-1.0-0
libpango-1.0-0:
  Installed: 1.34.1-0ubuntu1~13.10~ricotz1
  Candidate: 1.34.1-0ubuntu1~13.10~ricotz1
  Version table:
 *** 1.34.1-0ubuntu1~13.10~ricotz1 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
     1.34.1-0ubuntu1~13.04~ricotz1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ raring/main i386 Packages
     1.32.5-5build1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
```

No bare-metal removal...  ;)
Yes, I've forgot to write here... It was cleared just after Ricotz's message here...
I'm back to full G3 and Ricotz involvement and...
Just to emphasize that I did not want to purge G3 and Ricotz's PPAs because of that libpango stuff but I wanted to try vanilla Saucy...
Experiment (even though not completelly experienced) was a success and there was a nice speed improvement while in vanilla Saucy... Still some things to be polished it seems...
But, as I wrote, I'm back now and I do not regret a second...

---

### Post by zika on 2013-06-06
```
The following packages will be upgraded:
  gdm
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/786 kB of archives.
After this operation, 286 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
(Reading database ... 349575 files and directories currently installed.)
Preparing to replace gdm 3.8.1.1-0ubuntu1+logind~raring5 (using .../gdm_3.8.1.1-0ubuntu2_amd64.deb) ...
Unpacking replacement gdm ...
dpkg: error processing /var/cache/apt/archives/gdm_3.8.1.1-0ubuntu2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/gdm/Gdm-1.0.typelib', which is also in package libgdm 3.8.1.1-0ubuntu1+logind~raring5
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for ureadahead ...
Errors were encountered while processing:
 /var/cache/apt/archives/gdm_3.8.1.1-0ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by VinDSL on 2013-06-06
Heh!  Thanks, for the warning, zika...  :)

---

### Post by VinDSL on 2013-06-06
@zika

I did an incremental upgrade earlier, today, but didn't upgrade GDM.  Everything went smoothly.

A few minutes ago, I noticed a GDM library was available now also, so I gave them a whirl.

A dialog box asked me if I wanted to accept the new GDM greeter changes, or keep the original.

I accepted the changes -- rebooted -- and everything is working fine...  ;)

---

### Post by zika on 2013-06-07
> **VinDSL said:**
> @zika

I did an incremental upgrade earlier, today, but didn't upgrade GDM.  Everything went smoothly.

A few minutes ago, I noticed a GDM library was available now also, so I gave them a whirl.

A dialog box asked me if I wanted to accept the new GDM greeter changes, or keep the original.

I accepted the changes -- rebooted -- and everything is working fine...  ;)I was sleeping until now, I'll try it again... No sweat, I use startx anyway... ;)
It did not ask me anything but it went well...:D

---

### Post by VinDSL on 2013-06-07
> **zika said:**
> [...] it went well...:D
Since upgrading...

The only obvious difference, that I noticed, is the login button now turns "Gnome Blue" while I'm typing my password.

I'm sure there were more changes included in the upgrade, other than purely cosmetic, but...

Just saying.

---

### Post by zika on 2013-06-07
> **VinDSL said:**
> Since upgrading...

The only obvious difference, that I noticed, is the login button now turns "Gnome Blue" while I'm typing my password.

I'm sure there were more changes included in the upgrade, other than purely cosmetic, but...

Just saying.
You've missed Ubuntu watermark at the bottom of login screen... ;)
Anybody know how to turn off on-screen keyboard?
I know how to turn it off when it pops up but I want to know how to prevent it popping up... ;)

---

### Post by zika on 2013-06-07
Little glitch:
```
dpkg: error processing  /var/cache/apt/archives/libwayland-client0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb  (--unpack):
 trying to overwrite  '/usr/lib/x86_64-linux-gnu/libwayland-client.so.0.1.0', which is also in  package libwayland0:amd64  1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0
```
```
dpkg: error processing  /var/cache/apt/archives/libwayland-cursor0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb  (--unpack):
 trying to overwrite  '/usr/lib/x86_64-linux-gnu/libwayland-cursor.so.0.0.0', which is also in  package libwayland0:amd64  1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0
```

---

### Post by VinDSL on 2013-06-07
> **zika said:**
> You've missed Ubuntu watermark at the bottom of login screen... ;)
Yes.  That Ubu logo popped up (for me) a few upgrades ago... maybe a week_or_so.

> **zika said:**
> Anybody know how to turn off on-screen keyboard?
I know how to turn it off when it pops up but I want to know how to prevent it popping up... ;)
OMG!!!

I had a problem with caribou-antler injecting itself, all over the place, starting on page-27...

LINK:  [http://ubuntuforums.org/showthread.php?t=2097359&page=27&p=12538476&viewfull=1#post12538476](http://ubuntuforums.org/showthread.php?t=2097359&page=27&p=12538476&viewfull=1#post12538476)

I just kept attacking it, until it finally went away.  Don't know exactly how I fixed the problem -- brute force, I guess.

Man, that thing was like a virus.  Good luck!

**EDIT**

I was re-reading the link (above) and unto the next page.

This *might* provide the answer...

LINK 2: [http://ubuntuforums.org/showthread.php?t=2097359&page=28&p=12550973&viewfull=1#post12550973](http://ubuntuforums.org/showthread.php?t=2097359&page=28&p=12550973&viewfull=1#post12550973)

---

### Post by zika on 2013-06-08
Plot is thickening:
```
:~$ sudo aptitude upgrade 
[sudo] password for zika: 
Resolving dependencies...                
The following NEW packages will be installed:
  libwayland-client0{a} libwayland-cursor0{a} 
The following partially installed packages will be configured:
  deja-dup deja-dup-backend-gvfs deja-dup-backend-ubuntuone eog 
  gir1.2-gtk-3.0 gir1.2-rb-3.0 gnome-calculator gnome-control-center 
  gnome-control-center-signon gnome-settings-daemon libaccount-plugin-1.0-0 
  libgail-3-0 libgnome-control-center1 libgtk-3-0 libgtk-3-bin 
  librhythmbox-core7 libunity-core-6.0-5 rhythmbox rhythmbox-mozilla 
  rhythmbox-plugin-cdrecorder rhythmbox-plugin-zeitgeist rhythmbox-plugins 
  rhythmbox-ubuntuone unity unity-scope-manpages unity-scope-musicstores 
  unity-services 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/35.8 kB of archives. After unpacking 156 kB will be used.
Do you want to continue? [Y/n/?] 
(Reading database ... 350818 files and directories currently installed.)
Unpacking libwayland-client0:amd64 (from .../libwayland-client0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libwayland-client0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libwayland-client.so.0.1.0', which is also in package libwayland0:amd64 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0
Unpacking libwayland-cursor0:amd64 (from .../libwayland-cursor0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libwayland-cursor0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libwayland-cursor.so.0.0.0', which is also in package libwayland0:amd64 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0
Errors were encountered while processing:
 /var/cache/apt/archives/libwayland-client0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb
 /var/cache/apt/archives/libwayland-cursor0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libgtk-3-0:amd64:
 libgtk-3-0:amd64 depends on libwayland-client0 (>= 1.0.2); however:
  Package libwayland-client0:amd64 is not installed.
 libgtk-3-0:amd64 depends on libwayland-cursor0 (>= 1.0.2); however:
  Package libwayland-cursor0:amd64 is not installed.

dpkg: error processing libgtk-3-0:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on libgtk-3-0 (>= 3.7.10); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-calculator:
 gnome-calculator depends on libgtk-3-0 (>= 3.3.16); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing gnome-calculator (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk-3-bin:
 libgtk-3-bin depends on libgtk-3-0 (>= 3.9.3~git20130605.2d4560ae-0ubuntu1~13.10~ricotz1); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing libgtk-3-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of deja-dup:
 deja-dup depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing deja-dup (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of librhythmbox-core7:
 librhythmbox-core7 depends on libgtk-3-0 (>= 3.6.0); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing librhythmbox-core7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center-signon:
 gnome-control-center-signon depends on gnome-control-center (>= 3.4.2-0ubuntu10); however:
  Package gnome-control-center is not configured yet.
 gnome-control-center-signon depends on libgtk-3-0 (>= 3.2.1); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing gnome-control-center-signon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libaccount-plugin-1.0-0:
 libaccount-plugin-1.0-0 depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing libaccount-plugin-1.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gir1.2-gtk-3.0:
 gir1.2-gtk-3.0 depends on libgtk-3-0 (>= 3.9.3~git20130605.2d4560ae-0ubuntu1~13.10~ricotz1); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing gir1.2-gtk-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-plugin-cdrecorder:
 rhythmbox-plugin-cdrecorder depends on libgtk-3-0 (>= 3.6.0); however:
  Package libgtk-3-0:amd64 is not configured yet.
 rhythmbox-plugin-cdrecorder depends on librhythmbox-core7 (>= 2.99.1+git20130530.1d5d9c98); however:
  Package librhythmbox-core7 is not configured yet.

dpkg: error processing rhythmbox-plugin-cdrecorder (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of deja-dup-backend-gvfs:
 deja-dup-backend-gvfs depends on deja-dup; however:
  Package deja-dup is not configured yet.

dpkg: error processing deja-dup-backend-gvfs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-control-center1:
 libgnome-control-center1 depends on libgtk-3-0 (>= 3.5.14); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing libgnome-control-center1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eog:
 eog depends on libgtk-3-0 (>= 3.6); however:
  Package libgtk-3-0:amd64 is not configured yet.
 eog depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.

dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity:
 unity depends on libgtk-3-0 (>= 3.1.6); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing unity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-settings-daemon:
 gnome-settings-daemon depends on libgtk-3-0 (>= 3.7.10); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing gnome-settings-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgail-3-0:amd64:
 libgail-3-0:amd64 depends on libgtk-3-0 (= 3.9.3~git20130605.2d4560ae-0ubuntu1~13.10~ricotz1); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing libgail-3-0:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-services:
 unity-services depends on libgtk-3-0 (>= 3.1); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing unity-services (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-plugins:
 rhythmbox-plugins depends on libgtk-3-0 (>= 3.6.0); however:
  Package libgtk-3-0:amd64 is not configured yet.
 rhythmbox-plugins depends on librhythmbox-core7 (= 2.99.1+git20130530.1d5d9c98-0ubuntu1~13.10~ricotz0); however:
  Package librhythmbox-core7 is not configured yet.
 rhythmbox-plugins depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.

dpkg: error processing rhythmbox-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox:
 rhythmbox depends on librhythmbox-core7 (= 2.99.1+git20130530.1d5d9c98-0ubuntu1~13.10~ricotz0); however:
  Package librhythmbox-core7 is not configured yet.
 rhythmbox depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.

dpkg: error processing rhythmbox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gir1.2-rb-3.0:
 gir1.2-rb-3.0 depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.
 gir1.2-rb-3.0 depends on librhythmbox-core7 (>= 2.99.1+git20130530.1d5d9c98); however:
  Package librhythmbox-core7 is not configured yet.

dpkg: error processing gir1.2-rb-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of deja-dup-backend-ubuntuone:
 deja-dup-backend-ubuntuone depends on deja-dup; however:
  Package deja-dup is not configured yet.

dpkg: error processing deja-dup-backend-ubuntuone (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-scope-manpages:
 unity-scope-manpages depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.

dpkg: error processing unity-scope-manpages (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-mozilla:
 rhythmbox-mozilla depends on rhythmbox (= 2.99.1+git20130530.1d5d9c98-0ubuntu1~13.10~ricotz0); however:
  Package rhythmbox is not configured yet.

dpkg: error processing rhythmbox-mozilla (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libunity-core-6.0-5:
 libunity-core-6.0-5 depends on unity-services (= 7.0.0daily13.06.07-0ubuntu1); however:
  Package unity-services is not configured yet.

dpkg: error processing libunity-core-6.0-5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-plugin-zeitgeist:
 rhythmbox-plugin-zeitgeist depends on rhythmbox (>= 2.99); however:
  Package rhythmbox is not configured yet.
 rhythmbox-plugin-zeitgeist depends on rhythmbox (<< 2.100); however:
  Package rhythmbox is not configured yet.

dpkg: error processing rhythmbox-plugin-zeitgeist (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-ubuntuone:
 rhythmbox-ubuntuone depends on rhythmbox (>= 2.95.5); however:
  Package rhythmbox is not configured yet.

dpkg: error processing rhythmbox-ubuntuone (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-scope-musicstores:
 unity-scope-musicstores depends on rhythmbox-ubuntuone; however:
  Package rhythmbox-ubuntuone is not configured yet.

dpkg: error processing unity-scope-musicstores (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgtk-3-0:amd64
 gnome-control-center
 gnome-calculator
 libgtk-3-bin
 deja-dup
 librhythmbox-core7
 gnome-control-center-signon
 libaccount-plugin-1.0-0
 gir1.2-gtk-3.0
 rhythmbox-plugin-cdrecorder
 deja-dup-backend-gvfs
 libgnome-control-center1
 eog
 unity
 gnome-settings-daemon
 libgail-3-0:amd64
 unity-services
 rhythmbox-plugins
 rhythmbox
 gir1.2-rb-3.0
 deja-dup-backend-ubuntuone
 unity-scope-manpages
 rhythmbox-mozilla
 libunity-core-6.0-5
 rhythmbox-plugin-zeitgeist
 rhythmbox-ubuntuone
 unity-scope-musicstores
```

---

### Post by Chanath on 2013-06-08
Gnome3 Staging PPA is for Raring, and the GS there is 3.8.3, whereas the GS already in Saucy repos is 3.8.2, or are we talking here about Gnome Testing PPA, where you can get GS 3.9.2 for Saucy? If so, shouldn't the Title of this thread be changed?:)

---

### Post by VinDSL on 2013-06-08
> **zika said:**
> Plot is thickening [...]
Broken dependencies here, too...

```
E: /var/cache/apt/archives/libwayland-client0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_i386.deb: trying to overwrite '/usr/lib/i386-linux-gnu/libwayland-client.so.0.1.0', which is also in package libwayland0:i386 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0

E: /var/cache/apt/archives/libwayland-cursor0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_i386.deb: trying to overwrite '/usr/lib/i386-linux-gnu/libwayland-cursor.so.0.0.0', which is also in package libwayland0:i386 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0
```

---

### Post by Harry33 on 2013-06-08
> **VinDSL said:**
> Broken dependencies here, too...

```
E: /var/cache/apt/archives/libwayland-client0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_i386.deb: trying to overwrite '/usr/lib/i386-linux-gnu/libwayland-client.so.0.1.0', which is also in package libwayland0:i386 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0

E: /var/cache/apt/archives/libwayland-cursor0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_i386.deb: trying to overwrite '/usr/lib/i386-linux-gnu/libwayland-cursor.so.0.0.0', which is also in package libwayland0:i386 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0
```

The package libwayland0 has now been into three packages: libwayland-client0, libwayland-cursor0 and libwayland-server0.
So you should remove the old libwayland0, or better purge it.

---

### Post by VinDSL on 2013-06-08
> **Harry33 said:**
> [Y]ou should remove the old libwayland0, or better purge it.
Okay, here goes...  :)

**EDIT**

Whoa!  It didn't like that.  Wanted to do the "bare-metal" thing.

Hope I won't need to reboot today.  Saucy is in a sad state, judging by the dependency errors.

Oh, well.  Lubuntu DE will probably boot, maybe.  

And, I have the good ol' Ubu 10.10 orphan, on another partition, so I won't be stranded.

---

### Post by zika on 2013-06-08
```
:~$ sudo apt-get purge libwayland0 
[sudo] password for zika: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libegl1-mesa : Depends: libwayland0 (>= 1.0.2) but it is not going to be installed
 libegl1-mesa-drivers : Depends: libwayland0 (>= 1.0.2) but it is not going to be installed
 libgtk-3-0 : Depends: libwayland-client0 (>= 1.0.2) but it is not going to be installed
              Depends: libwayland-cursor0 (>= 1.0.2) but it is not going to be installed
 weston : Depends: libwayland0 (>= 1.1.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
After latest upgrade:
```
:~$ sudo apt-get purge libwayland0 -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libegl1-mesa : Depends: libwayland-client0 (>= 1.0.2) but it is not going to be installed
                Depends: libwayland-server0 (>= 1.0.2) but it is not going to be installed
 libegl1-mesa-drivers : Depends: libwayland-client0 (>= 1.0.2) but it is not going to be installed
                        Depends: libwayland-server0 (>= 1.0.2) but it is not going to be installed
 libgtk-3-0 : Depends: libwayland-client0 (>= 1.0.2) but it is not going to be installed
              Depends: libwayland-cursor0 (>= 1.0.2) but it is not going to be installed
 weston : Depends: libwayland0 (>= 1.1.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
zika@zika:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libwayland-client0 libwayland-cursor0 libwayland-server0
The following NEW packages will be installed:
  libwayland-client0 libwayland-cursor0 libwayland-server0
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
30 not fully installed or removed.
Need to get 0 B/68.1 kB of archives.
After this operation, 265 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 350819 files and directories currently installed.)
Unpacking libwayland-client0:amd64 (from .../libwayland-client0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libwayland-client0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libwayland-client.so.0.1.0', which is also in package libwayland0:amd64 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0
Unpacking libwayland-cursor0:amd64 (from .../libwayland-cursor0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libwayland-cursor0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libwayland-cursor.so.0.0.0', which is also in package libwayland0:amd64 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0
Unpacking libwayland-server0:amd64 (from .../libwayland-server0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libwayland-server0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libwayland-server.so.0.0.0', which is also in package libwayland0:amd64 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0
Errors were encountered while processing:
 /var/cache/apt/archives/libwayland-client0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb
 /var/cache/apt/archives/libwayland-cursor0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb
 /var/cache/apt/archives/libwayland-server0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Just have to find a way to purge libwayland0 and not its dependencies...
Going to have lunch and think better with new calories obtained... ;)

---

### Post by VinDSL on 2013-06-08
> **zika said:**
> Just have to find a way to purge libwayland0 and not its dependencies...
Going to have lunch and think better with new calories obtained... ;)
Heh!  It's amazing how much testers think alike...  :D

---

### Post by zika on 2013-06-08
I've put a lot of hopes into this but alas...
```
:~$ sudo apt-get -f remove libwayland0 weston libwayland-server0+ libwayland-client0+ libwayland-cursor0+
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libwayland0 weston
The following NEW packages will be installed:
  libwayland-client0 libwayland-cursor0 libwayland-server0
0 upgraded, 3 newly installed, 2 to remove and 0 not upgraded.
30 not fully installed or removed.
Need to get 0 B/68.1 kB of archives.
After this operation, 988 kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 350819 files and directories currently installed.)
Unpacking libwayland-client0:amd64 (from .../libwayland-client0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libwayland-client0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libwayland-client.so.0.1.0', which is also in package libwayland0:amd64 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0
No apport report written because MaxReports is reached already
                                                              Unpacking libwayland-cursor0:amd64 (from .../libwayland-cursor0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libwayland-cursor0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libwayland-cursor.so.0.0.0', which is also in package libwayland0:amd64 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0
No apport report written because MaxReports is reached already
                                                              Unpacking libwayland-server0:amd64 (from .../libwayland-server0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libwayland-server0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libwayland-server.so.0.0.0', which is also in package libwayland0:amd64 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libwayland-client0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb
 /var/cache/apt/archives/libwayland-cursor0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb
 /var/cache/apt/archives/libwayland-server0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Even after calories I'm out of ideas...
```
:~$ sudo aptitude install weston_ libwayland0_ libwayland-server0+ libwayland-cursor0+ libwayland-client0+
The following NEW packages will be installed:
  libwayland-client0 libwayland-cursor0 libwayland-server0 
The following packages will be REMOVED:
  libwayland0{p} weston{p} 
The following partially installed packages will be configured:
  deja-dup deja-dup-backend-gvfs deja-dup-backend-ubuntuone eog 
  evolution-data-server gir1.2-gtk-3.0 gir1.2-rb-3.0 gnome-calculator 
  gnome-control-center gnome-control-center-signon gnome-settings-daemon 
  libaccount-plugin-1.0-0 libegl1-mesa libegl1-mesa-drivers libgail-3-0 
  libgnome-control-center1 libgtk-3-0 libgtk-3-bin librhythmbox-core7 
  libunity-core-6.0-5 rhythmbox rhythmbox-mozilla 
  rhythmbox-plugin-cdrecorder rhythmbox-plugin-zeitgeist rhythmbox-plugins 
  rhythmbox-ubuntuone unity unity-scope-manpages unity-scope-musicstores 
  unity-services 
0 packages upgraded, 3 newly installed, 2 to remove and 0 not upgraded.
Need to get 0 B/68.1 kB of archives. After unpacking 988 kB will be freed.
Do you want to continue? [Y/n/?] 
(Reading database ... 350819 files and directories currently installed.)
Unpacking libwayland-client0:amd64 (from .../libwayland-client0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libwayland-client0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libwayland-client.so.0.1.0', which is also in package libwayland0:amd64 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0
No apport report written because MaxReports is reached already
                                                              Unpacking libwayland-cursor0:amd64 (from .../libwayland-cursor0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libwayland-cursor0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libwayland-cursor.so.0.0.0', which is also in package libwayland0:amd64 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0
No apport report written because MaxReports is reached already
                                                              Unpacking libwayland-server0:amd64 (from .../libwayland-server0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libwayland-server0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libwayland-server.so.0.0.0', which is also in package libwayland0:amd64 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libwayland-client0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb
 /var/cache/apt/archives/libwayland-cursor0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb
 /var/cache/apt/archives/libwayland-server0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libgtk-3-0:amd64:
 libgtk-3-0:amd64 depends on libwayland-client0 (>= 1.0.2); however:
  Package libwayland-client0:amd64 is not installed.
 libgtk-3-0:amd64 depends on libwayland-cursor0 (>= 1.0.2); however:
  Package libwayland-cursor0:amd64 is not installed.

dpkg: error processing libgtk-3-0:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libegl1-mesa-drivers:amd64:
 libegl1-mesa-drivers:amd64 depends on libwayland-client0 (>= 1.0.2); however:
  Package libwayland-client0:amd64 is not installed.
 libegl1-mesa-drivers:amd64 depends on libwayland-server0 (>= 1.0.2); however:
  Package libwayland-server0:amd64 is not installed.

dpkg: error processing libegl1-mesa-drivers:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on libgtk-3-0 (>= 3.7.10); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-calculator:
 gnome-calculator depends on libgtk-3-0 (>= 3.3.16); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing gnome-calculator (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk-3-bin:
 libgtk-3-bin depends on libgtk-3-0 (>= 3.9.3~git20130605.2d4560ae-0ubuntu1~13.10~ricotz1); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing libgtk-3-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of deja-dup:
 deja-dup depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing deja-dup (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of librhythmbox-core7:
 librhythmbox-core7 depends on libgtk-3-0 (>= 3.6.0); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing librhythmbox-core7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libegl1-mesa:amd64:
 libegl1-mesa:amd64 depends on libwayland-client0 (>= 1.0.2); however:
  Package libwayland-client0:amd64 is not installed.
 libegl1-mesa:amd64 depends on libwayland-server0 (>= 1.0.2); however:
  Package libwayland-server0:amd64 is not installed.

dpkg: error processing libegl1-mesa:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center-signon:
 gnome-control-center-signon depends on gnome-control-center (>= 3.4.2-0ubuntu10); however:
  Package gnome-control-center is not configured yet.
 gnome-control-center-signon depends on libgtk-3-0 (>= 3.2.1); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing gnome-control-center-signon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libaccount-plugin-1.0-0:
 libaccount-plugin-1.0-0 depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing libaccount-plugin-1.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gir1.2-gtk-3.0:
 gir1.2-gtk-3.0 depends on libgtk-3-0 (>= 3.9.3~git20130605.2d4560ae-0ubuntu1~13.10~ricotz1); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing gir1.2-gtk-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-plugin-cdrecorder:
 rhythmbox-plugin-cdrecorder depends on libgtk-3-0 (>= 3.6.0); however:
  Package libgtk-3-0:amd64 is not configured yet.
 rhythmbox-plugin-cdrecorder depends on librhythmbox-core7 (>= 2.99.1+git20130530.1d5d9c98); however:
  Package librhythmbox-core7 is not configured yet.

dpkg: error processing rhythmbox-plugin-cdrecorder (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of deja-dup-backend-gvfs:
 deja-dup-backend-gvfs depends on deja-dup; however:
  Package deja-dup is not configured yet.

dpkg: error processing deja-dup-backend-gvfs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-control-center1:
 libgnome-control-center1 depends on libgtk-3-0 (>= 3.5.14); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing libgnome-control-center1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eog:
 eog depends on libgtk-3-0 (>= 3.6); however:
  Package libgtk-3-0:amd64 is not configured yet.
 eog depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.

dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity:
 unity depends on libgtk-3-0 (>= 3.1.6); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing unity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-settings-daemon:
 gnome-settings-daemon depends on libgtk-3-0 (>= 3.7.10); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing gnome-settings-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgail-3-0:amd64:
 libgail-3-0:amd64 depends on libgtk-3-0 (= 3.9.3~git20130605.2d4560ae-0ubuntu1~13.10~ricotz1); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing libgail-3-0:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-services:
 unity-services depends on libgtk-3-0 (>= 3.1); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing unity-services (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-plugins:
 rhythmbox-plugins depends on libgtk-3-0 (>= 3.6.0); however:
  Package libgtk-3-0:amd64 is not configured yet.
 rhythmbox-plugins depends on librhythmbox-core7 (= 2.99.1+git20130530.1d5d9c98-0ubuntu1~13.10~ricotz0); however:
  Package librhythmbox-core7 is not configured yet.
 rhythmbox-plugins depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.

dpkg: error processing rhythmbox-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-data-server:
 evolution-data-server depends on libgtk-3-0 (>= 3.0.0); however:
  Package libgtk-3-0:amd64 is not configured yet.

dpkg: error processing evolution-data-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox:
 rhythmbox depends on librhythmbox-core7 (= 2.99.1+git20130530.1d5d9c98-0ubuntu1~13.10~ricotz0); however:
  Package librhythmbox-core7 is not configured yet.
 rhythmbox depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.

dpkg: error processing rhythmbox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gir1.2-rb-3.0:
 gir1.2-rb-3.0 depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.
 gir1.2-rb-3.0 depends on librhythmbox-core7 (>= 2.99.1+git20130530.1d5d9c98); however:
  Package librhythmbox-core7 is not configured yet.

dpkg: error processing gir1.2-rb-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of deja-dup-backend-ubuntuone:
 deja-dup-backend-ubuntuone depends on deja-dup; however:
  Package deja-dup is not configured yet.

dpkg: error processing deja-dup-backend-ubuntuone (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-scope-manpages:
 unity-scope-manpages depends on gir1.2-gtk-3.0; however:
  Package gir1.2-gtk-3.0 is not configured yet.

dpkg: error processing unity-scope-manpages (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-mozilla:
 rhythmbox-mozilla depends on rhythmbox (= 2.99.1+git20130530.1d5d9c98-0ubuntu1~13.10~ricotz0); however:
  Package rhythmbox is not configured yet.

dpkg: error processing rhythmbox-mozilla (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libunity-core-6.0-5:
 libunity-core-6.0-5 depends on unity-services (= 7.0.0daily13.06.07-0ubuntu1); however:
  Package unity-services is not configured yet.

dpkg: error processing libunity-core-6.0-5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-plugin-zeitgeist:
 rhythmbox-plugin-zeitgeist depends on rhythmbox (>= 2.99); however:
  Package rhythmbox is not configured yet.
 rhythmbox-plugin-zeitgeist depends on rhythmbox (<< 2.100); however:
  Package rhythmbox is not configured yet.

dpkg: error processing rhythmbox-plugin-zeitgeist (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhythmbox-ubuntuone:
 rhythmbox-ubuntuone depends on rhythmbox (>= 2.95.5); however:
  Package rhythmbox is not configured yet.

dpkg: error processing rhythmbox-ubuntuone (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-scope-musicstores:
 unity-scope-musicstores depends on rhythmbox-ubuntuone; however:
  Package rhythmbox-ubuntuone is not configured yet.

dpkg: error processing unity-scope-musicstores (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgtk-3-0:amd64
 libegl1-mesa-drivers:amd64
 gnome-control-center
 gnome-calculator
 libgtk-3-bin
 deja-dup
 librhythmbox-core7
 libegl1-mesa:amd64
 gnome-control-center-signon
 libaccount-plugin-1.0-0
 gir1.2-gtk-3.0
 rhythmbox-plugin-cdrecorder
 deja-dup-backend-gvfs
 libgnome-control-center1
 eog
 unity
 gnome-settings-daemon
 libgail-3-0:amd64
 unity-services
 rhythmbox-plugins
 evolution-data-server
 rhythmbox
 gir1.2-rb-3.0
 deja-dup-backend-ubuntuone
 unity-scope-manpages
 rhythmbox-mozilla
 libunity-core-6.0-5
 rhythmbox-plugin-zeitgeist
 rhythmbox-ubuntuone
 unity-scope-musicstores
```

---

### Post by Harry33 on 2013-06-08
You need to purge libwayland0.
Also, you need to purge the old weston, which depends on libwayland0.
Here is the new weston (saucy-universe):
[https://launchpad.net/ubuntu/saucy/+source/weston/1.0.5-0ubuntu1b2](https://launchpad.net/ubuntu/saucy/+source/weston/1.0.5-0ubuntu1b2).

---

### Post by zika on 2013-06-08
> **Harry33 said:**
> You need to purge libwayland0.
Also, you need to purge the old weston, which depends on libwayland0.
Here is the new weston (saucy-universe):
[https://launchpad.net/ubuntu/saucy/+source/weston/1.0.5-0ubuntu1b2](https://launchpad.net/ubuntu/saucy/+source/weston/1.0.5-0ubuntu1b2).Yeah, I got that...
The question I have is simple: How?
If You read my post above I've tried in almost a dozen of ways, some of them quite unusual, but...
```
$ sudo dpkg -i weston_1.0.5-0ubuntu1b2_amd64.deb 
[sudo] password for zika: 
dpkg: warning: downgrading weston from 1.1.0+git20130515.9caf77bd-0ubuntu1~13.10~ricotz0 to 1.0.5-0ubuntu1b2
(Reading database ... 350819 files and directories currently installed.)
Preparing to replace weston 1.1.0+git20130515.9caf77bd-0ubuntu1~13.10~ricotz0 (using weston_1.0.5-0ubuntu1b2_amd64.deb) ...
Unpacking replacement weston ...
dpkg: dependency problems prevent configuration of weston:
 weston depends on libegl1-mesa (>= 8.0-2); however:
  Package libegl1-mesa:amd64 is not configured yet.
 weston depends on libegl1-mesa-drivers (>= 8.0-2); however:
  Package libegl1-mesa-drivers:amd64 is not configured yet.
 weston depends on libwayland-client0 (>= 1.0.2); however:
  Package libwayland-client0:amd64 is not installed.
 weston depends on libwayland-cursor0 (>= 1.0.2); however:
  Package libwayland-cursor0:amd64 is not installed.
 weston depends on libwayland-server0 (>= 1.0.2); however:
  Package libwayland-server0:amd64 is not installed.

dpkg: error processing weston (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 weston
```

---

### Post by dino99 on 2013-06-08
here is how i've fixed that madness:
- first i've failed to purge the old libwayland and the likes (all ricotz ppas desactivated since a while)
- as there was some ricotz's packages installed when the ppas were activated, i've tried to purge the 2 ppas: both activated into synaptic (each time) and repeated twice the madness due to cross dependencies. Got the most part purged only.
- then clean the system: autoremove, then apt-get -f install : here is the most scary part; i have accepted the removal of half bare-metal (:o ) glancing closely before hitting "Enter" key (no worry: dpkg or apt-get are not removed)
- Thats it, now updating/upgrading can be done: no more broken packages  :p
- finally an other autoremove and apt-get -f install later, the system is upgraded back, reinstalling the previous removed apps/libs (check with ubuntu-desktop)

The other way you can choose if you does not mind about the actual broken packages, ignore them untill some updates will land into the saucy archives.

---

### Post by VinDSL on 2013-06-08
> **zika said:**
> I've tried in almost a dozen of ways, some of them quite unusual, but...
Dittos...

I'm going to go update my Facebook page, and ponder the situation.

Maybe, I'll see the forest after I get away from the trees.  ;)

---

### Post by zika on 2013-06-08
I'll take door #3 for now... ;)

Update&#8321;: Sent a message to Ricotz so I'll kind of wait for a bit... ;)

---

### Post by VinDSL on 2013-06-08
> **zika said:**
> I'll take door #3 for now... ;)

[Bwahahahaha]("https://www.youtube.com/watch?v=nHQxaOKV6H0")!

---

### Post by VinDSL on 2013-06-08
w00t!  Think I finally hit the right combination...  ;)

```
vindsl@Zuul:~$ **[COLOR="#0000CD"]sudo dpkg -i --force-overwrite[/COLOR]** /var/cache/apt/archives/libwayland-client0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_i386.deb
[sudo] password for vindsl: 
(Reading database ... 460643 files and directories currently installed.)
Unpacking libwayland-client0:i386 (from .../libwayland-client0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_i386.deb) ...
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/lib/i386-linux-gnu/libwayland-client.so.0.1.0', which is also in package libwayland0:i386 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/lib/i386-linux-gnu/libwayland-client.so.0', which is also in package libwayland0:i386 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0
Setting up libwayland-client0:i386 (1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

vindsl@Zuul:~$ **[COLOR="#0000CD"]sudo dpkg -i --force-overwrite[/COLOR]** /var/cache/apt/archives/libwayland-server0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_i386.deb
(Reading database ... 460646 files and directories currently installed.)
Unpacking libwayland-server0:i386 (from .../libwayland-server0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_i386.deb) ...
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/lib/i386-linux-gnu/libwayland-server.so.0.0.0', which is also in package libwayland0:i386 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/lib/i386-linux-gnu/libwayland-server.so.0', which is also in package libwayland0:i386 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0
Setting up libwayland-server0:i386 (1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

vindsl@Zuul:~$ **[COLOR="#0000CD"]sudo dpkg -i --force-overwrite[/COLOR]** /var/cache/apt/archives/libwayland-cursor0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_i386.deb
(Reading database ... 460649 files and directories currently installed.)
Unpacking libwayland-cursor0:i386 (from .../libwayland-cursor0_1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1_i386.deb) ...
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/lib/i386-linux-gnu/libwayland-cursor.so.0.0.0', which is also in package libwayland0:i386 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/lib/i386-linux-gnu/libwayland-cursor.so.0', which is also in package libwayland0:i386 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0
Setting up libwayland-cursor0:i386 (1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

vindsl@Zuul:~$ 
```[INDENT]* Linefeeds added for easy reading.[/INDENT]


Everything is fully upgraded now (supposedly) -- no more errors reported.

I'll do a cold boot, and see what happens...

BBL

**EDIT**

Whew!  That was fun -- 10 hr 55 min of sheer terror, to be exact.

I'm gonna archive that command, before I forget, in Gnote. 

Wallpaper looks a little worse_for_wear, but everything is working fine.  LoL!  :D


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-8-jun-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-8-jun-2013-1.png")[/INDENT]

---

### Post by Harry33 on 2013-06-09
VinDSL,
It seems though you still have libwayland0 installed (because dpkg needs to overwrite) and that should be purged.

---

### Post by zika on 2013-06-09
Morning is always more clear than evening...
```
sudo dpkg  --purge libwayland0
```
did the trick... ;)

Now```
Setting up rhythmbox-plugin-zeitgeist (2.99.1+git20130606.051d8b96-0ubuntu1~13.10~ricotz0) ...
  File "/usr/lib/rhythmbox/plugins/rbzeitgeist/rbzeitgeist.py", line 40
    except RuntimeError, e:
                       ^
SyntaxError: invalid syntax

dpkg: error processing rhythmbox-plugin-zeitgeist (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 rhythmbox-plugin-zeitgeist
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
looks like a joke... ;)

---

### Post by Harry33 on 2013-06-09
Zika,

Try the rhythmbox (2.99.1-0ubuntu1) from official saucy,

---

### Post by zika on 2013-06-09
> **Harry33 said:**
> Zika,

Try the rhythmbox (2.99.1-0ubuntu1) from official saucy,Since I'm not a RB user and not a ZG user I'm OK...
I've had a problem like this already before and it is just the time for me to learn some of .py syntax...

---

### Post by VinDSL on 2013-06-09
> **Harry33 said:**
> VinDSL,
It seems though you still have libwayland0 installed (because dpkg needs to overwrite) and that should be purged.
Hrm...

```
vindsl@Zuul:~$ apt-cache policy libwayland.
libwayland-cursor0-dbg:
  Installed: (none)
  Candidate: 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1
  Version table:
     1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1 0
        500 http://ppa.launchpad.net/ricotz/staging/ubuntu/ saucy/main i386 Packages
     1.1.0-2ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
**[COLOR="#0000CD"]libwayland-server0:[/COLOR]**
  Installed: 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1
  Candidate: 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1
  Version table:
 *** 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1 0
        500 http://ppa.launchpad.net/ricotz/staging/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
     1.1.0-2ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
libwayland-dev:
  Installed: (none)
  Candidate: 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1
  Version table:
     1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1 0
        500 http://ppa.launchpad.net/ricotz/staging/ubuntu/ saucy/main i386 Packages
     1.1.0-2ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
libwayland0-dbg:
  Installed: (none)
  Candidate: 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0
  Version table:
     1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/staging/ubuntu/ saucy/main i386 Packages
libwayland-server0-dbg:
  Installed: (none)
  Candidate: 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1
  Version table:
     1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1 0
        500 http://ppa.launchpad.net/ricotz/staging/ubuntu/ saucy/main i386 Packages
     1.1.0-2ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
**[COLOR="#0000CD"]libwayland0:[/COLOR]**
  Installed: 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0
  Candidate: 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0
  Version table:
 *** 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/staging/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
**[COLOR="#0000CD"]libwayland-cursor0:[/COLOR]**
  Installed: 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1
  Candidate: 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1
  Version table:
 *** 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1 0
        500 http://ppa.launchpad.net/ricotz/staging/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
     1.1.0-2ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
**[COLOR="#0000CD"]libwayland-client0:[/COLOR]**
  Installed: 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1
  Candidate: 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1
  Version table:
 *** 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1 0
        500 http://ppa.launchpad.net/ricotz/staging/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
     1.1.0-2ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
libwayland-client0-dbg:
  Installed: (none)
  Candidate: 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1
  Version table:
     1.1.0+git20130418.cfec3aec-0ubuntu1~13.10~ricotz1 0
        500 http://ppa.launchpad.net/ricotz/staging/ubuntu/ saucy/main i386 Packages
     1.1.0-2ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
vindsl@Zuul:~$ 
```

I know that "libwayland-server0" snuck in there, while I was dancing on the keyboard.  I can probably remove it.

How about the rest of libwayland et al.  :confused:

Are you saying to nuke it all, or just "libwayland0"?

**EDIT**

Haven't had my first cup of "black magic" yet.  I'm brewing a pot, as I type...  :)

Looking at the results above, I would *guess* that anything ending in "~ricotz0" should NOT be installed -- thus, only...

[INDENT] "libwayland0: 1.1.0+git20130418.cfec3aec-0ubuntu1~13.10**[COLOR="#0000CD"]~ricotz0[/COLOR]**"[/INDENT]

...should go away, right?

Think I'll try that, after I wake-up a bit more...  ;)

**EDIT2**

Okay, here goes...

```
vindsl@Zuul:~$ sudo dpkg --purge libwayland0
[sudo] password for vindsl: 
(Reading database ... 489617 files and directories currently installed.)
Removing libwayland0:i386 ...
Purging configuration files for libwayland0:i386 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
vindsl@Zuul:~$ 

```

Let's see if it survives a cold boot.

**EDIT3**

Booted up just fine!

Thanks, Harry (and zika)!  ;)

---

### Post by VinDSL on 2013-06-09
> **zika said:**
> Morning is always more clear than evening...
```
sudo dpkg  --purge libwayland0
```
did the trick... ;)

Now```
Setting up rhythmbox-plugin-zeitgeist (2.99.1+git20130606.051d8b96-0ubuntu1~13.10~ricotz0) ...
  File "/usr/lib/rhythmbox/plugins/rbzeitgeist/rbzeitgeist.py", line 40
    except RuntimeError, e:
                       ^
SyntaxError: invalid syntax

dpkg: error processing rhythmbox-plugin-zeitgeist (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 rhythmbox-plugin-zeitgeist
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
looks like a joke... ;)
Been getting that pesky error for a few weeks.  I just ignore it.

Hacked that file every_which_way_to_sunday, to no avail.  Runtime error handling exception seems to be confused by the way it's being reraised -- probably the result of recent python upgrades.

I figure, they'll correct it sooner or later...  ;)

---

### Post by VinDSL on 2013-06-09
> **Harry33 said:**
> Try the rhythmbox (2.99.1-0ubuntu1) from official saucy,
Plays my music, podcasts, et cetera -- NO streaming audio!

MPRIS D-Bus doesn't work, of course.  Dev release won't be usable on the DE until it's fully cooked.

---

### Post by VinDSL on 2013-06-11
Is this article for real :confused:


SOURCE:  [Popular Ubuntu Gnome maintainer Jeremy Bicha steps down]("http://2buntu.com/1330/popular-ubuntu-gnome-maintainer-jeremy-bicha-steps-down/")
> You know him, you love him, and now, you'll also miss him. Jeremy Bicha, the long-time maintainer of Ubuntu's major Gnome packages, has made the decision to step down. He cites a lack of time (something all of us are feeling the pinch of these days) due to family and other issues.

Despite not being a fan of the recent damage changes to Gnome in the form of Gnome Shell, I did become quite familiar with Jeremy and his work, and I've been amazed at how quickly he's been able to get Gnome's newest packages into a PPA for us bleeding edge lovers to enjoy.

In Jeremy's place, will be Tim Lunn, an avid contributor, and Ubuntu+Gnome member.

I wish them both the best going forward, and look forward to seeing what lays in store for Gnome in Ubuntu in the future.


**EDIT**

I judge it must be true.  Jorge just pointed me toward Jeremy's official blog post... 


SOURCE:  [Moving On]("http://jeremy.bicha.net/2013/05/27/moving-on/")
> While I had been interested in Debian/Ubuntu packaging for a while, it was the release of GNOME 3 two years ago that gave me the opportunity to get involved significantly. As Ubuntu switched to Unity by default instead of a tweaked GNOME desktop, there was a need for contributors who cared about GNOME to step in and help out.

I&#8217;m sad to announce that due to immense personal and family responsibilities, I simply won&#8217;t have the time or ability to contribute to the Ubuntu GNOME effort much longer. I get a lot of happiness out of participating in a major open source software project. It is my charity work. I am very pleased that my volunteered computer skills can improve the lives of millions of people.

If you&#8217;ve been following the Ubuntu GNOME community, you have no doubt seen Tim Lunn&#8217;s work. Tim (darkxst) is an Ubuntu member, a GNOME Foundation member, and a Ubuntu Contributing Developer. He has submitted several fixes to gnome-shell, gdm, and other GNOME components. Tim is the clear choice to take over the Technical Lead role for Ubuntu GNOME.

After our first official release last month, this is a great time to pitch in. We can use additional packagers, testers, and more. The Ubuntu GNOME project is especially in need of help with QA &#8212; testing the development releases (and our PPAs) to identify problems, triage incoming bug reports, and certify the releases. Thanks!

:shock:

---

### Post by sammiev on 2013-06-11
Sooner or later we all move on from one thing or another. I know this as I did the same myself. Linux is my new hobby and family. I look forward to the work of the new programmer and their work. :)

---

### Post by VinDSL on 2013-06-13
n/m

---

### Post by jbicha on 2013-06-13
> **VinDSL said:**
> 
I judge "GNOME3 Staging" is dead in the water, e.g. this is the beginning_of_the_end for GNOME3 on Ubuntu.


Wow. Seriously. What are you talking about?

Have you seen all the GNOME 3.8 stuff that's [landed]("https://lists.ubuntu.com/archives/saucy-changes/2013-May/") in [Saucy]("https://lists.ubuntu.com/archives/saucy-changes/2013-June/")? From my perspective, the GNOME team has already pushed more new stuff and improvements this cycle to Ubuntu than any other flavor (besides the Unity team). We basically have the mostly final GNOME Shell in already for this release cycle and it's only been about 7 weeks. Of course, the Ubuntu flavors aren't competing with each other but **I'm very skeptical of any suggestions that any of the Ubuntu flavors are dead or nearly so**.

It's unclear where you frustration is directed. Rico is still maintaining the Ricotz PPA's for git snapshots. The GNOME  development.1 release is usually not very interesting; several of the big features don't really land until as late as .5 or .90. There will be GNOME 3.9.* stuff show up in the GNOME3 Saucy PPA whenever someone (not me this year) gets around to doing it. It's difficult to maintain the several different PPAs with backports and Ubuntu releases (and weird combinations of them) and working with the Ubuntu Desktop Team to not regress Unity while pushing updates for the GNOME desktop. Generally, the remaining missing pieces are because of Ubuntu-specific customizations (or from a different perspective, "GNOME regressions").

Just to pick one example, Nautilus 3.8 hasn't landed in Saucy yet and there are two remaining issues:
1. Concerns about the new Nautilus affecting desktop drawing in Unity (I don't think any developers really care about Metacity). That needs more investigation and testing to find out what specific scenarios work and don't work with Nautilus 3.6 and then with Nautilus 3.8. No one has volunteered to do that.
2. The Ubuntu developers and designers would like for there to be a nice New Document [entry]("http://pad.lv/1113648") in the right-click menu.

**I am not the Ubuntu GNOME project. The project will not be ending this year and if people like you help out, there is no chance of it ending in future years either.**

---

### Post by EgoGratis on 2013-06-13
Thank you for your hard work and i agree GNOME still has quite a few followers and Ubuntu currently still is GNOME based distro in my opinion. GNOME will have to rethink some stuff about GnomeShell:

[http://www.h-online.com/open/news/item/Red-Hat-confirms-GNOME-Classic-Mode-for-RHEL-7-1887469.html](http://www.h-online.com/open/news/item/Red-Hat-confirms-GNOME-Classic-Mode-for-RHEL-7-1887469.html)

Because there are no big players backing it up (stock GnomeShell) ATM anymore and then i think it will become more popular again and if that happens things will get a bit easier again!

---

### Post by cariboo on 2013-06-13
Thanks Jeremy, for all the work you've done to get Ubuntu Gnome off the ground.

---

### Post by VinDSL on 2013-06-13
> **jbicha said:**
> Wow. Seriously. What are you talking about?
Just mourning the lose...

Somebody always rises to the top, then... Boom!  They're gone.  Think I'd be used to it, by now.

Didn't mean to get all melodramatic.  It just slipped out.

Good luck to you, man!  Wish you well... ;)

---

### Post by mc4man on 2013-06-14
> **jbicha said:**
> 
Just to pick one example, Nautilus 3.8 hasn't landed in Saucy yet and there are two remaining issues:
1. Concerns about the new Nautilus affecting desktop drawing in Unity (I don't think any developers really care about Metacity). That needs more investigation and testing to find out what specific scenarios work and don't work with Nautilus 3.6 and then with Nautilus 3.8. No one has volunteered to do that.
2. The Ubuntu developers and designers would like for there to be a nice New Document [entry]("http://pad.lv/1113648") in the right-click menu.

The main issue here with 3.8  is that  the  unity7/compiz &   file manager not handling the Desktop compo is not presentable, no good at all
If the 'fix' is coming from the compiz side, well it would be ok when/if it happens. 
(with or without Desktop icons though sure many that use a desktop like to have a Desktop to put things on

Otherwise could be easier to keep & if needed fix 3.6 till Ubuntu dumps compiz

---

### Post by Stinger on 2013-06-14
Hi Jeremy 
I can understand your decision, but i'll miss your enthusiasm and skills.
I respect all Tim's hard work for Ubuntu-Gnome but it will not be the same without your input.

In one of the earlier Ubuntu releases ( I think it was 5.10 or 6.06 ) "Ubuntu" was explained in a [video by Nelson Mandela]("http://www.youtube.com/watch?v=HED4h00xPPA")
> **Respect, helpfulness, sharing, community, caring, trust, unselfishness.**   and I might add **openness**. 
Mark, please have a good look in the mirror and repeat the words you once build Ubuntu upon.
Then get this project back on tracks.

---

### Post by sgage on 2013-06-14
Hello Jeremy,

I just wanted to add my best wishes and thanks. Your work with Gnome in Ubuntu has been very useful and important, and very much appreciated. Good luck with whatever you do next!

---

### Post by zika on 2013-06-16
Virtual package is forgotten so packages are kept back... ;)

Update&#8321;: Found it in ppa:jr/ppa ...[B] ;)
[/B](small excursion into K-waters...)

---

### Post by VinDSL on 2013-06-16
> **zika said:**
> Virtual package is forgotten so packages are kept back... ;)

Update&#8321;: Found it in ppa:jr/ppa ...[B] ;)
[/B](small excursion into K-waters...)
Heh!  How, in the name of heaven, did you find that one?  :D

Talk about a needle_in_a_haystack...

Anyway, good job, detective!  ;)

---

### Post by VinDSL on 2013-06-18
GS 3.9.3 is here.

```
vindsl@Zuul:~$ apt-cache policy gnome-shell
gnome-shell:
  Installed: 3.9.3+git20130618.64b5ec0b-0ubuntu1~13.10~ricotz0
  Candidate: 3.9.3+git20130618.64b5ec0b-0ubuntu1~13.10~ricotz0
  Version table:
 *** 3.9.3+git20130618.64b5ec0b-0ubuntu1~13.10~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ saucy/main i386 Packages

```

Had to hack a _lot_ of json files...  ;)

---

### Post by QDR06VV9 on 2013-06-18
[/QUOTE] Update&#8321;: Found it in ppa:jr/ppa ...[B] ;)
[/B](small excursion into K-waters...)[/QUOTE]

 Been using KDE for about 3 weeks, haven't used KDE since 3.5 That being said I feel a hook setting in!:)

---

### Post by zika on 2013-06-21
```
he following packages will be REMOVED:
  gnome-session-fallback
The following packages will be upgraded:
  gnome-session gnome-session-common
```
Should I stay or should I go?
I do use fallback frequently...
Looked briefly in changelogs and did not find a quick answer... ;)

---

### Post by xeizo on 2013-06-21
> **zika said:**
> ```
he following packages will be REMOVED:
  gnome-session-fallback
The following packages will be upgraded:
  gnome-session gnome-session-common
```
Should I stay or should I go?
I do use fallback frequently...
Looked briefly in changelogs and did not find a quick answer... ;)

Fallback? What fallback, there's always the commandline, I should go  ;-)

On a more serious note, I stopped using the Gnome3 ppa:s since it got weird beyond repair ie froze the whole box including keyboard which is not everyday. That was an old install with 12.10 as the original base. I've started fresh with the Ubuntu-version of 13.10 from a week ago as base, and use only xorg-edgers, pulseaudo-testing and alsa-testing over standard saucy reps and daily kernels of course. In that incarnation gnome-shell is the most stable gnome-shell I've ever had  :-)

---

### Post by zika on 2013-06-21
> **xeizo said:**
> Fallback? What fallback, there's always the commandline, I should go  ;-)

On a more serious note, I stopped using the Gnome3 ppa:s since it got weird beyond repair ie froze the whole box including keyboard which is not everyday. That was an old install with 12.10 as the original base. I've started fresh with the Ubuntu-version of 13.10 from a week ago as base, and use only xorg-edgers, pulseaudo-testing and alsa-testing over standard saucy reps and daily kernels of course. In that incarnation gnome-shell is the most stable gnome-shell I've ever had  :-)I'll probably regret writing this yet today but GS from PPA proved seriously stable in last month or so for me, and a log of my mistakes is just available to everyone here on Forum(s)... ;)

---

### Post by dino99 on 2013-06-21
> **zika said:**
> I'll probably regret writing this yet today but GS from PPA proved seriously stable in last month or so for me, and a log of my mistakes is just available to everyone here on Forum(s)... ;)

from synaptic's package details:

fallback : This is a transitional package to ease upgrades to gnome-session-flashback.
It can be safely removed.

---

### Post by VinDSL on 2013-06-21
> **zika said:**
> ```
he following packages will be REMOVED:
  gnome-session-fallback
The following packages will be upgraded:
  gnome-session gnome-session-common
```
Should I stay or should I go?
I do use fallback frequently...
Looked briefly in changelogs and did not find a quick answer... ;)

> **dino99 said:**
> from synaptic's package details:

fallback : This is a transitional package to ease upgrades to gnome-session-flashback.
It can be safely removed.
I removed it last night, during an incremental upgrade.

Looks like it DID indeed remove fallback...

```
vindsl@Zuul:~$ apt-cache policy gnome-session-fallback
gnome-session-fallback:
  Installed: (none)
  Candidate: 3.8.2.1-0ubuntu1~raring3+logind3
  Version table:
     3.8.2.1-0ubuntu1~raring3+logind3 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main i386 Packages
     3.8.0-0ubuntu1~raring1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ raring/main i386 Packages
     3.6.2-0ubuntu7 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/universe i386 Packages
vindsl@Zuul:~$
```

I never use fallback, so no harm, no foul...

---

### Post by zika on 2013-06-21
Farewell Fallback, I'll miss You... ;(

Update&#8321;: Ups, Flashback works... ;)
If only keyboard shorcuts worked in FlashBack... :P

Update&#8322;: Just to (re)solve```
Setting up gnome-session-flashback (1:3.6.2-0ubuntu9) ...
update-alternatives: error: alternative path /usr/bin/gnome-session-fallback doesn't exist
dpkg: error processing gnome-session-flashback (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 gnome-session-flashback
E: Sub-process /usr/bin/dpkg returned an error code (1)


```Update&#8323;: Nothing one ```
sudo touch /usr/bin/gnome-session-fallback
```can not (re)solve... :P

---

### Post by jbicha on 2013-06-21
I made a few mistakes in this update. If you'll wait a few hours for the packages to publish, you should be able to dist-upgrade without a problem. gnome-session-flashback should replace gnome-session-fallback. If you do not have gnome-session-flashback installed then you won't have the option to log in to the gnome-panel session (which has been renamed GNOME Flashback).

---

### Post by zika on 2013-06-21
> **jbicha said:**
> I made a few mistakes in this update. If you'll wait a few hours for the packages to publish, you should be able to dist-upgrade without a problem. gnome-session-flashback should replace gnome-session-fallback. If you do not have gnome-session-flashback installed then you won't have the option to log in to the gnome-panel session (which has been renamed GNOME Flashback).
Mistakes are part of the process of growth... Thank You for nice work. Writing this (of course) from FlashBack-NoEffects... ;)
Are we to expect keyboard-shortcuts to work in some forseable future or should we (as I did) get used not to use them... :P ?

---

### Post by converted on 2013-06-21
I've already upgraded Ubuntu Gnome to 3.8 (very nice Ubuntu GNOME team and GNOME devs) using the GNOME Team PPA -- but I noticed I'm missing the privacy settings from the system settings dialogue, and there is some bugginess (such as when switching users) that I'm hoping adding the staging PPA will fix.  I can't seem to find an Ubuntu bug for the user switching, but I see it for lots of other distros out there, and I haven't looked that hard yet, I'll admit.  :-)

So I'm OK with the warning about breakage -- I understand this is a staging PPA.  But I want to be sure what I'm getting myself into - will adding this PPA and doing a dist-upgraded be *expected* to break extensions which are working with 3.8 from the Team PPA?  Any other huge regressions that are known?  I see the note above about waiting a few hours, so I'll definitely wait a bit!  ;-)

Thanks all!

---

### Post by dino99 on 2013-06-21
> **converted said:**
> I've already upgraded Ubuntu Gnome to 3.8 (very nice Ubuntu GNOME team and GNOME devs) using the GNOME Team PPA -- but I noticed I'm missing the privacy settings from the system settings dialogue, and there is some bugginess (such as when switching users) that I'm hoping adding the staging PPA will fix.  I can't seem to find an Ubuntu bug for the user switching, but I see it for lots of other distros out there, and I haven't looked that hard yet, I'll admit.  :-)

So I'm OK with the warning about breakage -- I understand this is a staging PPA.  But I want to be sure what I'm getting myself into - will adding this PPA and doing a dist-upgraded be *expected* to break extensions which are working with 3.8 from the Team PPA?  Any other huge regressions that are known?  I see the note above about waiting a few hours, so I'll definitely wait a bit!  ;-)

Thanks all!

glance at extensions.gnome.org : 3.8 extensions are ok, but very rare for 3.9

---

### Post by converted on 2013-06-21
> **dino99 said:**
> glance at extensions.gnome.org : 3.8 extensions are ok, but very rare for 3.9

^^ I didn't notice there were 3.9 packages in the staging PPA, whoops -- OK then in that case I'll do without it...  (Could swear I checked that though -- will go back and look again.)

---

### Post by VinDSL on 2013-06-21
> **zika said:**
> Mistakes are part of the process of growth... Thank You for nice work.

My mom told me I was a mistake.  I thanked her for the nice work, too...  LoL!  :D

---

### Post by zika on 2013-06-21
It's back:```
The following NEW packages will be installed:  gnome-session-fallback
The following packages will be upgraded:
  gir1.2-gst-plugins-base-1.0 gir1.2-panelapplet-4.0 gnome-panel
  gnome-panel-data gnome-session-flashback gstreamer1.0-alsa
  gstreamer1.0-plugins-base gstreamer1.0-plugins-base-apps gstreamer1.0-x
  libgstreamer-plugins-base1.0-0 libpanel-applet-4-0
11 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/2,992 kB of archives.
After this operation, 247 kB of additional disk space will be used.
Do you want to continue [Y/n]?
```Like a Phoenix... :P

---

### Post by dino99 on 2013-06-21
> **zika said:**
> It's back:```
The following NEW packages will be installed:  gnome-session-fallback

Do you want to continue [Y/n]?
```Like a Phoenix... :P

Looks like the "can be safely removed" is not yet true

---

### Post by zika on 2013-06-21
> **dino99 said:**
> Looks like the "can be safely removed" is not yet trueReviving it is a replacement for my touch-remedy, I suppose...
I was just joking...
Update&#8321;:```
:~$ sudo apt-get purge gnome-session-fallback
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-session-fallback*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 246 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 351348 files and directories currently installed.)
Removing gnome-session-fallback ...
```

---

### Post by converted on 2013-06-23
> > **dino99 said:**
> glance at extensions.gnome.org : 3.8 extensions are ok, but very rare for 3.9

> **converted said:**
> ^^ I didn't notice there were 3.9 packages in the staging PPA, whoops -- OK then in that case I'll do without it...  (Could swear I checked that though -- will go back and look again.)

For the record, adding the staging PPA did NOT upgrade me to 3.9 -- not sure if that was your implied message or not, but in case anyone else read it that way I wanted to point it out.

It also didn't fix my user switching problem, but made it a more graceful failure (I get thrown back to GDM instead of into a gnome-shell-less session that forces me to reboot from tty.)

It did give me the privacy settings tile though, and likely other improvements that haven't jumped out at me...

---

### Post by kurt18947 on 2013-06-23
> **dino99 said:**
> glance at extensions.gnome.org : 3.8 extensions are ok, but very rare for 3.9

:confused:  I show 150 extensions available for 3.9.0-6-generic, including the ones I use most.  I thought the version dependent extensions were fixed in 3.8 so they didn't have to be modified for each version.  The only one I'm missing is All in One Places.

---

### Post by dino99 on 2013-06-23
> **kurt18947 said:**
> :confused:  I show 150 extensions available for 3.9.0-6-generic, including the ones I use most.  I thought the version dependent extensions were fixed in 3.8 so they didn't have to be modified for each version.  The only one I'm missing is All in One Places.

hey kurt,
in case you were not fully awaken, we were talking about gnome-shell, not about the kernel :lolflag:
and for those not finding GS 3.9, its from ricotz testing of course.

---

### Post by converted on 2013-06-23
> **dino99 said:**
> 
and for those not finding GS 3.9, its from ricotz testing of course.

I think we've maybe been talking past each other.  :)  I never wanted 3.9.  I was concerned about any known issues adding the staging PPA (as opposed to just the Gnome3 PPA).

Already had this one:
[https://launchpad.net/~gnome3-team/+archive/gnome3/](https://launchpad.net/~gnome3-team/+archive/gnome3/)

Was asking on P41 about adding this one:
[https://launchpad.net/~gnome3-team/+archive/gnome3-staging](https://launchpad.net/~gnome3-team/+archive/gnome3-staging)


I thought this would be the right thread for that, given the title.  ;)

---

### Post by dino99 on 2013-06-23
> **converted said:**
> I think we've maybe been talking past each other.  :)  I never wanted 3.9.  I was concerned about any known issues adding the staging PPA (as opposed to just the Gnome3 PPA).

Already had this one:
[https://launchpad.net/~gnome3-team/+archive/gnome3/](https://launchpad.net/~gnome3-team/+archive/gnome3/)

Was asking on P41 about adding this one:
[https://launchpad.net/~gnome3-team/+archive/gnome3-staging](https://launchpad.net/~gnome3-team/+archive/gnome3-staging)


I thought this would be the right thread for that, given the title.  ;)

all these now mainly have "copy from saucy", so they are useless with saucy ;) and JB have stopped its work there too.

---

### Post by converted on 2013-06-23
> **dino99 said:**
> all these now mainly have "copy from saucy", so they are useless with saucy ;) and JB have stopped its work there too.

Oh hell. :mrgreen:

What I did NOT notice (originally found the thread in a google search) is that this is in the Ubuntu **+1 **forum. :facepalm:

---

### Post by markbl on 2013-06-23
> **converted said:**
> Oh hell. :mrgreen:
What I did NOT notice (originally found the thread in a google search) is that this is in the Ubuntu **+1 **forum. :facepalm:
I have done this also, it is an easy mistake to make. I always scroll up nowadays after a search just to check if I am in the +1 sub-forum. :)

---

### Post by VinDSL on 2013-06-23
> **markbl said:**
> I have done this also, it is an easy mistake to make. [...]
And, I have done this as well, numerous times.

Well, not in this particular case, but...

Some of the version numbers of this_or_that are too close.  All I see is the number, and not the name.  LoL!  :D

---

### Post by converted on 2013-06-24
Thanks both of you!  :-)

---

### Post by VinDSL on 2013-06-24
Welcome.

---

### Post by VinDSL on 2013-06-27
Kunstimuuseum, Estonia  :)

[INDENT]**[COLOR="#800000"]Ubuntu 13.10 / GNOME 3.9.3 Staging / Linux 3.10-rc7 Mainline / Conky 1.9.0 / ConkyWX 0.9.3-1[/COLOR]**

[[IMG]http://vindsl.com/images/vindsl-desktop-27-jun-2013-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-27-jun-2013-2.png")[/INDENT]


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-27-jun-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-27-jun-2013-1.png")[/INDENT]

---

### Post by QDR06VV9 on 2013-06-27
"GNOME3 Staging -- Looking Better All The Time
Kunstimuuseum, Estonia  

Ubuntu 13.10 / GNOME 3.9.3 Staging / Linux 3.10-rc7 Mainline / Conky 1.9.0 / ConkyWX 0.9.3-1"


GNOME3 Staging -- Looking Better All The Time
Kunstimuuseum, Estonia  

Ubuntu 13.10 / GNOME 3.9.3 Staging / Linux 3.10-rc7 Mainline / Conky 1.9.0 / ConkyWX 0.9.3-1
How much hacking? Or is it coming along smoothly...

---

### Post by VinDSL on 2013-06-27
> **runrickus said:**
> How much hacking? Or is it coming along smoothly...
That's sort of a trick question...  ;)

The only thing(s) I have to hack, on a regular basis are the extensions; which, themselves, are a hack (of sorts).

Extensions are the glue that holds GNOME3 together IMO.  Without them, you might as well run Unity; which is also a GNOME hack.  That said, most of the time, all I have to do is hack the json files.

The Dash-To-Dock extension (the dock on the left-side) has to be [compiled from source]("https://github.com/micheleg/dash-to-dock"), every time Ricotz upgrades gnome-shell, but that's no big deal.

I also skin the icons in gnome-tweak-tool, et cetera.

Then, there's the obligatory, unexpected dependency issues, and so forth, and so on.

All_in_all everything has gone smoothly enough.  Hasn't been boring...

---

### Post by QDR06VV9 on 2013-06-28
> **VinDSL said:**
> That's sort of a trick question...  ;)

The only thing(s) I have to hack, on a regular basis are the extensions; which, themselves, are a hack (of sorts).

Extensions are the glue that holds GNOME3 together IMO.  Without them, you might as well run Unity; which is also a GNOME hack.  That said, most of the time, all I have to do is hack the json files.

The Dash-To-Dock extension (the dock on the left-side) has to be [compiled from source]("https://github.com/micheleg/dash-to-dock"), every time Ricotz upgrades gnome-shell, but that's no big deal.

I also skin the icons in gnome-tweak-tool, et cetera.

Then, there's the obligatory, unexpected dependency issues, and so forth, and so on.

All_in_all everything has gone smoothly enough.  Hasn't been boring...

Yah! Pretty much what I hoped you would say, My first attempt with kernel 3.10rc7 and gnome ppas did not go so well, first time i HAVE HAD TO REINSATLL:(

But you got me hooked on gnome-shell,(LOL) So Im going to give it another Shot..
Thanks VinDSL:popcorn:

---

### Post by xeizo on 2013-06-28
> **runrickus said:**
> Yah! Pretty much what I hoped you would say, My first attempt with kernel 3.10rc7 and gnome ppas did not go so well, first time i HAVE HAD TO REINSATLL:(

But you got me hooked on gnome-shell,(LOL) So Im going to give it another Shot..
Thanks VinDSL:popcorn:

gnome-shell 3.8.2 with Nautilus 3.6.3 was very stable for me, no issues at all. Now it's gnome-shell 3.8.3 with Nautilus 3.8.2 in the repos and it crashes a lot, also apport have started to freeze the whole machine for minutes while it tries to report the new crashes. A clear regression. I've tried Ricotz gnome-shell 3.9.3 with Nautilus 3.8.2 earlier and it wasn't too stable either. It's seems Nautilus 3.6.3+ is the cause of the gnome-shell crashes, and apport do the freezing ...

Anyway, I''ve started to like gnome-shell a lot, with a skinned icon set it looks and feels more "clean" than Unity. Let's hope the work with packaging accellerates some so it gets more stable and polished. Ubuntu Gnome is the word  :-)

---

### Post by zika on 2013-06-28
On-screen-keyboard that bugged me before is fixed now in GDM... It gives way to mouse as it should... Nice!

---

### Post by QDR06VV9 on 2013-06-28
> **xeizo said:**
> gnome-shell 3.8.2 with Nautilus 3.6.3 was very stable for me, no issues at all. Now it's gnome-shell 3.8.3 with Nautilus 3.8.2 in the repos and it crashes a lot, also apport have started to freeze the whole machine for minutes while it tries to report the new crashes. A clear regression. I've tried Ricotz gnome-shell 3.9.3 with Nautilus 3.8.2 earlier and it wasn't too stable either. It's seems Nautilus 3.6.3+ is the cause of the gnome-shell crashes, and apport do the freezing ...

Anyway, I''ve started to like gnome-shell a lot, with a skinned icon set it looks and feels more "clean" than Unity. Let's hope the work with packaging accellerates some so it gets more stable and polished. Ubuntu Gnome is the word  :-)

gnome-shell 3.8.2 with Nautilus 3.6.3 Was quite the opposite for me But gnome-shell 3.8.2 with Nautilus 3.8.2
Is very nice smooth and Quick!:P

---

### Post by xeizo on 2013-06-28
> **runrickus said:**
> gnome-shell 3.8.2 with Nautilus 3.6.3 Was quite the opposite for me But gnome-shell 3.8.2 with Nautilus 3.8.2
Is very nice smooth and Quick!:P

Well, well, I'm back at the latest: gnome3, gnome3-staging and gnome3-testing fully updated. At least I can post this, so to some extent it do work ;-)

---

### Post by IanW on 2013-06-28
I much prefer Nautilus 3.8.2 to 3.6.x - Tree view came back! :D

---

### Post by VinDSL on 2013-07-06
Hrm...

Anybody else notice that their GDM greeter panel is missing?!?!?

All I am seeing is the default user login -- no session choices (Ubuntu, Lubuntu, OpenBox, et cetera).

Think I'll switch to LightDM temporarily, and see if it's working correctly.

**EDIT**

Doh!  n/m

Switched to LightDM and all session options were available.

Switched back to GDM, and realized you have to click on the the little gear/cog icon.

Carry on...  :)

---

### Post by zika on 2013-07-10
Something changed today with upgrade:
icons in Chromium (not in Chrome) and some of keys on on-screen kb at log-in (GDM) are funny...
No change in FF...
qt...?

---

### Post by VinDSL on 2013-07-10
> **zika said:**
> Something changed today[...]
I read your post, and did an upgrade -- lots of qt5 stuff in there, but first...

I had to struggle with broken packages and conflicts, due to Lubuntu, soooo...

I removed Lubuntu and force-overwrote some packages.  Everything finally upgraded.

I'll see if it survives a cold boot, now.  Wish me luck.  LoL!  :D

---

### Post by VinDSL on 2013-07-10
Everything looks fine, here, zika -- GDM looks normal -- dittos for Chromium 30... ;)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-10-jul-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-10-jul-2013-1.png")[/INDENT]


**EDIT**

BTW, just pulled-up Chromium 27 -- it looks fine, too...

---

### Post by VinDSL on 2013-07-10
Whoa!  just upgraded to GS 3.9.4, and it broke the 'User Themes' extension...

Heh!  I forgot how ugly GS was, without makeup.  :D

---

### Post by VinDSL on 2013-07-11
_UPDATE_

Tried everything, in my bag o' tricks, but can't get the new 'user-themes' extension working.

Anybody else having probs with '3.9.4~git20130708.9e5079bd-0ubuntu1~13.10~ricotz0'?

Killing my xserver, here...

---

### Post by mc4man on 2013-07-11
> **VinDSL said:**
> 

Heh!  I forgot how ugly GS was, without makeup.  :D
That's in the running for understatement of the year

---

### Post by VinDSL on 2013-07-14
> **mc4man said:**
> That's in the running for understatement of the year
LoL!  :D

'User Themes' shell extension is back today, after GS 3.9.4 upgrade(s).


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-14-jul-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-14-jul-2013-1.png")[/INDENT]


Thank you, devs!!!

---

### Post by zika on 2013-07-20
Lot of design/user_interface changes today...

---

### Post by VinDSL on 2013-07-20
> **zika said:**
> Lot of design/user_interface changes today...
w00t!

Solved all my glib problems...


EXTRA CREDIT READING:[INDENT][URL="http://ubuntuforums.org/showthread.php?t=2163484"]
[SOLVED] GiMP, PCManFM, [others] seg faulting[/URL]  :D[/INDENT]

---

### Post by d2kx on 2013-07-20
> **VinDSL said:**
> Everything looks fine, here, zika -- GDM looks normal -- dittos for Chromium 30... ;)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-10-jul-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-10-jul-2013-1.png")[/INDENT]

Much love to you for promoting Ektoplazm.

---

### Post by VinDSL on 2013-07-20
> **d2kx said:**
> Much love to you for promoting Ektoplazm.
My pleasure!  I owe them.  :D

It's been my favorite music site, for years...  ;)

---

### Post by VinDSL on 2013-07-20
Now that I got me GiMP back, here's how the latest GNOME3 Staging looks...


[INDENT][B][COLOR="#800000"]Ubu 13.10 / GS 3.9.4 / Linux 3.11-rc1 mainline kernel  / nVidia 304.88 (patched) / Conky /  ConkyWX 0.9.3

Shell Ext.: Dash to Dock (compiled), Icon Hider (hacked), User Themes, Workspace Indicator (hacked)[/COLOR][/B]

[[IMG]http://vindsl.com/images/vindsl-desktop-20-jul-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-20-jul-2013-1.png")[/INDENT]


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-20-jul-2013-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-20-jul-2013-2.png")[/INDENT]

---

### Post by VinDSL on 2013-07-20
WoW!  

They finally fixed the lower (notification) panel.  That thing had more issues than a New York magazine stand.

Before, for instance, it would notify me that I had (say) 13 messages, but as soon as I moused over the message notification, it disappeared.  Now, it's clickable, e.g. the panel actually pops up.

Heh!  They're getting there...

---

### Post by 749 on 2013-08-31
Has anyone succeded in upgrading the shell to version 3.9.90?
I'm using both gnome3 and gnome3-staging ppas and all I see after a reboot is the new wallpaper, but without even getting to GDM.

---

### Post by tista on 2013-08-31
> **749 said:**
> Has anyone succeded in upgrading the shell to version 3.9.90?
I'm using both gnome3 and gnome3-staging ppas and all I see after a reboot is the new wallpaper, but without even getting to GDM.

I can't get, too.
Seemed libgnome-desktop3, gnome-settings-daemon, and gnome-control-center were still in progress to do patchworks? If I rollbacked those packages to around 3.9.5, I could kick gnome-shell normally though...

But older gnome-control-center can't be worked yet with gnome-shell 3.9.90 series.

Regards,
Tista

---

### Post by VinDSL on 2013-08-31
> **749 said:**
> Has anyone succeded in upgrading the shell to version 3.9.90?
Yes, I've been running it for a week, or so.  Can't remember the exact date of the upgrade.

Only problem I've had is -- a majority of my 'old' shell extensions no longer work -- Icon Hider, et cetera.

Heh!  I *thought* I was the only person running Gnome3 Staging...  :D

```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~" && echo -n "Current Date/Time: " && TZ='UTC' date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Package: mesa-common-dev" && dpkg -s mesa-common-dev | sed 's/^/  /' | grep Version && echo || echo && echo "Package: xserver-xorg-core" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Package: xserver-common" && apt-cache policy xserver-common | grep Installed && echo || echo && echo "Package: xserver-xephyr" && apt-cache policy xserver-xephyr | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~
Current Date/Time: Sat Aug 31 14:13:05 UTC 2013
Distro Release: Ubuntu Saucy Salamander (development branch)
Kernel Release: Linux 3.11.0-031100rc7-generic
Gnome Release: GNOME Shell 3.9.90
Unity Release: unity 7.1.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.88

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 115
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.1.0-0ubuntu1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Package: mesa-common-dev
  Version: 9.2.0~git20130729+9.2.9b8ad643-0ubuntu0sarvatt

Package: xserver-xorg-core
  Installed: 2:1.14.2.901+git20130808+server-1.14-branch.bc41226f-0ubuntu0ricotz

Package: xserver-common
  Installed: 2:1.14.2.901+git20130808+server-1.14-branch.bc41226f-0ubuntu0ricotz

Package: xserver-xephyr
  Installed: 2:1.14.2.901+git20130808+server-1.14-branch.bc41226f-0ubuntu0ricotz

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[02]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 

```

---

### Post by 749 on 2013-08-31
> **VinDSL said:**
> Yes, I've been running it for a week, or so.  Can't remember the exact date of the upgrade.
So why isn't it working for me :-k
What ppas are you using, maybe you have also ricotz/testing?

---

### Post by VinDSL on 2013-08-31
> **749 said:**
> What ppas are you using, maybe you have also ricotz/testing?
I have ricotz/testing enabled, but...

I'm using the ricotz/staging version of gnome-shell currently.


[INDENT][[img]http://vindsl.com/images/vindsl-desktop-31-aug-2013-1(650x520).png[/img]]("http://vindsl.com/images/vindsl-desktop-31-aug-2013-1.png")[/INDENT]


Confusing, huh?  ;)

---

### Post by 749 on 2013-08-31
Wow, you're not on the bleeding edge, you're beyond that :D
I'll try that one (god bless btrfs snapshots).

---

### Post by VinDSL on 2013-08-31
I wish the gnome shell extension authors would catch-up.

It's tough enough keeping up with Gnome3 Staging.

We shouldn't have to rewrite *their* code, too...

---

### Post by tista on 2013-08-31
Guys,

OK. Today I've got 3.9.90 gnome-shell and the latest gnome-control-center...

[IMG]http://s8.postimg.org/4badiebsl/Screenshot_from_2013_09_01_01_03_40.png[/IMG]

Regards,
Tista

---

### Post by VinDSL on 2013-08-31
> **tista said:**
> OK. Today I've got 3.9.90 gnome-shell and the latest gnome-control-center...
Sweet!  

I'll go upgrade, right now.

I called up gnome-control-center, a few minutes ago, and it's still reporting Gnome 3.8.3

BBL

---

### Post by VinDSL on 2013-08-31
Whoa!  Sneaky!!!

I didn't know Tim had his own PPA.  :)

Okay, let's see if this box survives a reboot...

---

### Post by 749 on 2013-08-31
OK, I tried ricotz/testing, ricotz/staging and even ricotz/unstable, still can't get to GDM.
Obviously something is wrong with my system.. Back to raring + GNOME 3.8 for now.

---

### Post by VinDSL on 2013-08-31
> **749 said:**
> Back to raring + GNOME 3.8 for now.
That might be the best idea, for now, unless you enjoy breakage.  :)

The 'Tim' upgrades borked my install.  Gotta check the logs and see what's going on.

I snuck in via the terminal/keyboard -- one step forward, two steps backwards.


[INDENT][[img]http://vindsl.com/images/vindsl-desktop-31-aug-2-13-2(650x520).png[/img]]("http://vindsl.com/images/vindsl-desktop-31-aug-2-13-2.png")[/INDENT]


GDM is crashing x.org, so when I boot, I need to shell out, restart the x.org service, then load GS manually.

I'll leave a post, after I put Humpty Dumpty back together again...  ;)

---

### Post by zika on 2013-09-01
After vacation I've noticed that keyboard shortcuts do not work in my GS...
```
:~$ apt-cache policy gnome-shellgnome-shell:
  Installed: 3.9.90+git20130831.1d26161d-0ubuntu1~13.10~ricotz0
  Candidate: 3.9.90+git20130831.1d26161d-0ubuntu1~13.10~ricotz0
  Version table:
 *** 3.9.90+git20130831.1d26161d-0ubuntu1~13.10~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/staging/ubuntu/ saucy/main amd64 Packages
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ saucy/main amd64 Packages
        100 /var/lib/dpkg/status
     3.8.4-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
```
They work OK in Unity (in Unity I've lost some indicators, whole right side of top panel)...
Is it just some adjustment/tweak or...?

---

### Post by VinDSL on 2013-09-01
> **zika said:**
> After vacation I've noticed that keyboard shortcuts do not work in my GS...

They work OK in Unity (in Unity I've lost some indicators, whole right side of top panel)...
Is it just some adjustment/tweak or...?
It seems that 3.9.90 has ushered in a lot of changes, visible & invisible.  I'm discovering them one_at_a_time.  

It's like tip-toeing through a minefield, at this point.  I don't know of any adjustments/tweaks.  

I spent hours yesterday (to no avail) trying to get Plymouth/GDM working.  Something has fundamentally changed.  I still have to shell out, startx, then replace GS once I get to the desktop.  Then, I have to turn on the shell extensions, et cetera.  It's a lot of work, just getting a new session up n' running.

This morning's upgrades took care of a few problems, like Plank taking up 1/4 of my display. LoL!

Anyway, I *think* we need to be patient, and wait for all of the 3.9.90 upgrades to come dripping in.  If I had known it was going to be this way, I would have put off upgrading for another week or two.  Too late now!

Personally, I'm past the point of no return.  I don't plan on adjusting/tweaking/downgrading anything.  I'm just going to wait & see if future upgrades will iron out the problems.

Google'ing for workarounds has been fruitless.  I don't think there are many GS3 Staging testers out here.  ;)

---

### Post by zika on 2013-09-01
> **VinDSL said:**
> I don't think there are many GS3 Staging testers out here.  ;)At least two of us are present and typing... ;)

---

### Post by VinDSL on 2013-09-01
> **zika said:**
> At least two of us are present and typing... ;)

Aye!  Present and accounted for...

Just ran across this good read:  [http://worldofgnome.org/gnome-current-goals-stage-of-completion/](http://worldofgnome.org/gnome-current-goals-stage-of-completion/)

> [SIZE=+1]Gnome current Goals stage of completion[/SIZE]
bill toulas | August 26, 2013

With 29 days left until version 3.10 gets officially released,

 [COLOR="#0000CD"]**we already have reached the point where it&#8217;s all about bug fixing from now on**[/COLOR] [...]

Guess that says it all.  ;)

---

### Post by mc4man on 2013-09-01
Haven't seen any issue with using the gnome3 & staging ppa (also experimental for gst, that has a minor one
Started with ubuntu-gnome the upgraded from there, only problem was I didn't upgrade libbluetooth something, that prevented getting a gdm login screen till fixed.

Looking at the 3.90 nautilus - it's, to me, god-awful design. Seems unbalanced, wastes space by truncating the path/location bar, leaving a big space to search button. Then there is the close 'button' which is sitting right on the edge & isn't even a button.
Guess I don't understand design, to me the default, as in screen, looks like a piece of paper I'd crumple up & throw away.

On a positive note, the dnd hover opening the hovered folder seems a bit more delayed in 3.9 compared to 3.8 where I had to disable in one of the 4.5 used places to make usable.

On a neg. note can't stand the way synaptic resets package list after choosing a package, can make for needless scrolling back

Didn't look a keyboard shortcuts much other than ctrl+alt+T didn't work, does so after a simple reset

---

### Post by Wise Ferret on 2013-09-01
I do not know if this is the right place to post this, because the problem I experience exists in the gnome3 ppa, not in staging. I have seen other posts here with similar problems:

1. Start Control Centre -> press either "Region and Language" or "Keyboard".
Result: ```
(gnome-control-center:8771): GLib-GIO-ERROR **: Settings schema 'org.gnome.settings-daemon.plugins.media-keys' does not contain a key named 'switch-input-source'
Trace/breakpoint trap
```
2. Start Control Centre -> press "Brightness and Locking" (or sonething similar - my language is not English).
Result: ```
(gnome-control-center:8971): GLib-GIO-ERROR **: Settings schema 'org.gnome.settings-daemon.plugins.power' does not contain a key named 'idle-dim-battery'
Trace/breakpoint trap
```

---

### Post by mc4man on 2013-09-01
> **Wise Ferret said:**
> I do not know if this is the right place to post this, because the problem I experience exists in the gnome3 ppa, not in staging. I have seen other posts here with similar problems:

1. Start Control Centre -> press either "Region and Language" or "Keyboard".
Result: ```
(gnome-control-center:8771): GLib-GIO-ERROR **: Settings schema 'org.gnome.settings-daemon.plugins.media-keys' does not contain a key named 'switch-input-source'
Trace/breakpoint trap
```
2. Start Control Centre -> press "Brightness and Locking" (or sonething similar - my language is not English).
Result: ```
(gnome-control-center:8971): GLib-GIO-ERROR **: Settings schema 'org.gnome.settings-daemon.plugins.power' does not contain a key named 'idle-dim-battery'
Trace/breakpoint trap
```
Not sure where the first one originates as don't see here using g-c-c 3.9.90.1 from staging.

The 2nd one appeared whenever I re-installed nautilus as I was adjusting the toolbar, it came from 20_ubuntu-gnome-default-settings.gschema.override, 
The current in 3.9.90 is just plain "idle-dim" & there is no time setting, just true or false
It did not cause any issues as the key in the .override file was  simply ignored

What the ubuntu-gnome maintainers decide to do if no time is reintroduced I've no clue, I don't want any dimming anyway so got rid of the warning/error by editing the .override file to idle-dim = false & recompiling the glib schemas


In your case because you're just using gnome3 ppa can't really say where/what is expecting these apparently  non-existent keys, you'd need to track down. (or use the staging ppa with some care..

---

### Post by VinDSL on 2013-09-01
> **mc4man said:**
> Haven't seen any issue with using the gnome3 & staging ppa (also experimental for gst [...]
Interesting!

Everything was going smoothly, for me, until the last brace of 3.9.90 upgrades and additions.

Now, my install is buggier than a Motel 6.

That's okay.  I hate it when things just work...

---

### Post by mc4man on 2013-09-01
Decided for the moment to go with about this, may alter some margins  or some other small details. Likely will  use the dark adwaita as the active breadcrumb in a focused naut window is  really crap in the default light theme, shading, ect. is wrong.
 (- tend to use location more but still didn't like light ver, though the shading in dark version isn't much better, need to look for a new theme I guess, maybe a modified ambiance
Probably will leave up button separate from nav box to gain some space, for whatever reason I like the path/location bar to line up with sidebar & sidebar not to show ...  with default bookmarks, ect. (though again theme dependent

---

### Post by VinDSL on 2013-09-01
I haven't opened Files in a while (I use PCManFM).

Here's how my Nautilus/Files looks...

[INDENT][ATTACH=CONFIG]245915[/ATTACH][/INDENT]

---

### Post by QDR06VV9 on 2013-09-02
> **mc4man said:**
> Haven't seen any issue with using the gnome3 & staging ppa (also experimental for gst, that has a minor one
Started with ubuntu-gnome the upgraded from there, only problem was I didn't upgrade libbluetooth something, that prevented getting a gdm login screen till fixed.

Looking at the 3.90 nautilus - it's, to me, god-awful design. Seems unbalanced, wastes space by truncating the path/location bar, leaving a big space to search button. Then there is the close 'button' which is sitting right on the edge & isn't even a button.
Guess I don't understand design, to me the default, as in screen, looks like a piece of paper I'd crumple up & throw away.

On a positive note, the dnd hover opening the hovered folder seems a bit more delayed in 3.9 compared to 3.8 where I had to disable in one of the 4.5 used places to make usable.

[COLOR="#00FFFF"]On a neg. note can't stand the way synaptic resets package list after choosing a package, can make for needless scrolling back
[/COLOR]
Didn't look a keyboard shortcuts much other than ctrl+alt+T didn't work, does so after a simple reset
Amen and +1:p

---

### Post by QDR06VV9 on 2013-09-02
> **zika said:**
> At least two of us are present and typing... ;)

I confess I haven't been very vigilant lately been doing catch up!
but after reading the latest posts maybe I will wait for a bit??:redface:

---

### Post by VinDSL on 2013-09-02
gdm & libgdm upgrades came rolling in this morning.

I was hopeful, but all they did was get rid of the hideous blue gnome curtains, when gdm crashes xorg.

Now, I get a black screen and white mouse pointer, instead blue curtains. LoL!

Oh, well.  I guess it's an improvement...

---

### Post by VinDSL on 2013-09-02
> **runrickus said:**
> I confess I haven't been very vigilant lately been doing catch up!
but after reading the latest posts maybe I will wait for a bit??:redface:
Hrm...

mc4man indicated he isn't having any probs.

Maybe you'll get lucky.  :)

---

### Post by mc4man on 2013-09-02
> **VinDSL said:**
> Hrm...

mc4man indicated he isn't having any probs.

Maybe you'll get lucky.  :)
Just to note - I started with a fresh ubuntu-gnome image install, updated everything, then added the 2 ppa's & dist upgraded (That was the 2 ppa's as of a couple of days ago

---

### Post by VinDSL on 2013-09-02
I suspect that's what I'll need to do, but...

I'm not ready to give-up, yet.

Curiosity killed the cat, you know?  LoL!  :D

---

### Post by QDR06VV9 on 2013-09-03
> **VinDSL said:**
> Hrm...

mc4man indicated he isn't having any probs.

Maybe you'll get lucky.  :)

I am In :p
```
Distributor ID:	Ubuntu
Description:	Ubuntu Saucy Salamander (development branch)
Release:	13.10
Codename:	saucy
3.11.0-4-generic
GNOME Shell 3.9.90

```


_Ok did not hold up to a cold boot_ just got a black screen and monitor went to sleep.
Did fetch some updates prior to shuting down, Installed unity and nvidia-325 driver, will post back!

---

### Post by VinDSL on 2013-09-03
> **runrickus said:**
> I am In :p
~Cool

I'm in, too!  :)

I did an incremental upgrade, this morning, and something click'ed (no pun intended).

Didn't have time to restart after the upgrade(s), but everything booted up normally tonight.

One (or more) of these worked a charm:

```
click (0.4.1) to 0.4.2
click-dev (0.4.1) to 0.4.2
click-doc (0.4.1) to 0.4.2
gir1.2-mutter-3.0 (3.9.90+git20130827.a292d21b-0ubuntu1~13.10~ricotz0) to 3.9.91+git20130903.d50ea010-0ubuntu1~13.10~ricotz0
gnome-session (3.9.90-0ubuntu2~saucy1) to 3.9.90-0ubuntu2
gnome-session-bin (3.9.90-0ubuntu2~saucy1) to 3.9.90-0ubuntu2
gnome-session-common (3.9.90-0ubuntu2~saucy1) to 3.9.90-0ubuntu2
gnome-shell (3.9.90+git20130831.1d26161d-0ubuntu1~13.10~ricotz0) to 3.9.91+git20130902.fc26fb21-0ubuntu1~13.10~ricotz0
gnome-shell-common (3.9.90+git20130831.1d26161d-0ubuntu1~13.10~ricotz0) to 3.9.91+git20130902.fc26fb21-0ubuntu1~13.10~ricotz0
gnome-shell-extensions (3.9.90~git20130821.d0c17d03-0ubuntu1~13.10~ricotz0) to 3.9.91~git20130901.2b45617d-0ubuntu1~13.10~ricotz0
libmutter0c (3.9.90+git20130827.a292d21b-0ubuntu1~13.10~ricotz0) to 3.9.91+git20130903.d50ea010-0ubuntu1~13.10~ricotz0
libvlc5 (2.2.0~~git20130901+r2958-0~r104~ubuntu13.10.1) to 2.2.0~~git20130902+r2965-0~r104~ubuntu13.10.1
libvlccore5 (2.2.0~~git20130901+r2958-0~r104~ubuntu13.10.1) to 2.2.0~~git20130902+r2965-0~r104~ubuntu13.10.1
mutter (3.9.90+git20130827.a292d21b-0ubuntu1~13.10~ricotz0) to 3.9.91+git20130903.d50ea010-0ubuntu1~13.10~ricotz0
mutter-common (3.9.90+git20130827.a292d21b-0ubuntu1~13.10~ricotz0) to 3.9.91+git20130903.d50ea010-0ubuntu1~13.10~ricotz0
python3-click (0.4.1) to 0.4.2
vlc (2.2.0~~git20130901+r2958-0~r104~ubuntu13.10.1) to 2.2.0~~git20130902+r2965-0~r104~ubuntu13.10.1
vlc-data (2.2.0~~git20130901+r2958-0~r104~ubuntu13.10.1) to 2.2.0~~git20130902+r2965-0~r104~ubuntu13.10.1
vlc-nox (2.2.0~~git20130901+r2958-0~r104~ubuntu13.10.1) to 2.2.0~~git20130902+r2965-0~r104~ubuntu13.10.1
vlc-plugin-notify (2.2.0~~git20130901+r2958-0~r104~ubuntu13.10.1) to 2.2.0~~git20130902+r2965-0~r104~ubuntu13.10.1
vlc-plugin-pulse (2.2.0~~git20130901+r2958-0~r104~ubuntu13.10.1) to 2.2.0~~git20130902+r2965-0~r104~ubuntu13.10.1
```

I'm running on top of a Liquorix 3.10 kernel right now.

I'll try the 3.11 mainline kernel, after I submit this...

EDIT

3.11 Final booted up just fine, also.

Heh!  They fixed it.  Good job, devs!

---

### Post by QDR06VV9 on 2013-09-04
> **VinDSL said:**
> ~Cool

I'm in, too!  :)

I did an incremental upgrade, this morning, and something click'ed (no pun intended).

Didn't have time to restart after the upgrade(s), but everything booted up normally tonight.

One (or more) of these worked a charm:


I'm running on top of a Liquorix 3.10 kernel right now.

I'll try the 3.11 mainline kernel, after I submit this...

EDIT

3.11 Final booted up just fine, also.

Heh!  They fixed it.  Good job, devs!

Yes way better this morning!
Dose unity work for you?(not important though)

---

### Post by VinDSL on 2013-09-04
> **runrickus said:**
> Yes way better this morning!
Dose unity work for you?(not important though)
Unity hasn't worked in months.  Seg faults on me...

My understanding is Gnome3 & Unity went in two different directions.

Don't know if they'll ever fix it.

---

### Post by QDR06VV9 on 2013-09-04
> **VinDSL said:**
> Unity hasn't worked in months.  Seg faults on me...

My understanding is Gnome3 & Unity went in two different directions.

Don't know if they'll ever fix it.
Thought so.Mark is pretty commited to his Unity!:confused:

---

### Post by zika on 2013-09-04
Here Unity and GS work side by side with minor issues:
Unity has crippled top bar (missing right part)
GS does not react on any (even default and commonly used) keyboard shortcuts 
Beside that they cohabitate nocely...

---

### Post by QDR06VV9 on 2013-09-04
> **zika said:**
> Here Unity and GS work side by side with minor issues:
Unity has crippled top bar (missing right part)
GS does not react on any (even default and commonly used) keyboard shortcuts 
Beside that they cohabitate nocely...

I did my install from daily build gnome buntu, and then added unity-desktop just to test,
Just dosent matter if it worked or not I have become a gnome-shell guy..
or even KDE has grown on me.
Thanks zika
Regards

---

### Post by VinDSL on 2013-09-04
As a followup...

I haven't tried Unity today.  Let's see what happens.

```
vindsl@Zuul:~$ unity --replace &
[1] 11724
vindsl@Zuul:~$ unity-panel-service: no process found
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: cube
compiz (core) - Info: Starting plugin: cube
compiz (core) - Info: Loading plugin: rotate
compiz (core) - Info: Starting plugin: rotate
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: unityshell
Segmentation fault

```

Hrm...

No joy!

The missing panel service seems new, though.  ;)

---

### Post by mc4man on 2013-09-05
> **VinDSL said:**
> As a followup...

I haven't tried Unity today.  Let's see what happens.
Hrm...

No joy!

The missing panel service seems new, though.  ;)
Can't see much reason to run unity in a staging ppa install  but as Zika mentioned it will run sans the panel indicators

The actual error would be  - 
/usr/lib/unity/unity-panel-service: symbol lookup error: /usr/lib/x86_64-linux-gnu/libido3-0.1.so.0: undefined symbol: ubuntu_menu_item_factory_get_type

This is likely from the absence of a ubuntu specific patch to gtk, & or something else changed in gtk-3.9.xx
(defined in ubuntu_gtk_custom_menu_items.patch

---

### Post by VinDSL on 2013-09-06
~Cool!  I assumed everyone was having the same problem... all three of us.  LoL!  :D

I think I'll try to resurrect Unity, this weekend.

---

### Post by zika on 2013-09-07
It seems that I've lost GDM after this morning's upgrades... Heads up... ;)
After loosing LightDM via introducing Mir, I'm now on Slim/startx/xinit... ;)
Fun never stops...
I still have to find a way of resurecting GS and Unity through Slim/startx/xinit...
Long live Awesome/Enlightenment...
Never mind, around last midnight I lost access to my disk (I was changing fstab and I had to chroot sleepy and tired...)
Update&#8321;: Resurected both... (GS and Unity in GDM)...

---

### Post by VinDSL on 2013-09-07
> **zika said:**
> Never mind, around last midnight I lost access to my disk (I was changing fstab and I had to chroot sleepy and tired...)

Update&#8321;: Resurected both... (GS and Unity in GDM)...
We have an idiom around here, "Nothing good happens after midnight."

Glad to hear you got 'it' working again.

Thanks, for the heads-up!  ;)

---

### Post by VinDSL on 2013-09-07
Cheated death, again!

Just did an upgrade, and GDM is still working.

Gotta say, the GDM login screen (gdmgreeter) is looking sexier all the time...

---

### Post by zika on 2013-09-07
> **VinDSL said:**
> We have an idiom around here, "Nothing good happens after midnight."

Glad to hear you got 'it' working again.

Thanks, for the heads-up!  ;)
Chroot stuff ended minutes before midnight yesterday so Your idiom stands... ;)

---

### Post by VinDSL on 2013-09-08
Got bored, today, and removed Nautilus (never use it anyway) and network-manager.

Replaced NM with WiCD (wicked).  Why?

Got tired of looking at the x'ed-out NM app indicator, in the top panel.  LoL!

Working great, as usual.  Got WiCD installed on all of my machines now (lappy, netbook, usb thumb drives, desktop).

Come on in, the water is fine!  ;)

---

### Post by mc4man on 2013-09-08
> **VinDSL said:**
> 

Working great, as usual.  Got WiCD installed on all of my machines now (lappy, netbook, [COLOR="#0000CD"]usb thumb drives[/COLOR], desktop).
)
So how's an install on a thumb drive working out (usb2 or 3?

---

### Post by VinDSL on 2013-09-08
> **mc4man said:**
> So how's an install on a thumb drive working out (usb2 or 3?
USB2.  I'm currently running Peppermint on all portables.

Peppermint 4 OS (Lubuntu fork with LXDE DE and Xfwm4 WM) is shockingly fast on USB2.

I've tried many, many, OSs on bootable/persistent USB sticks.  Peppermint runs circles around them all.

---

### Post by VinDSL on 2013-09-11
[[Announcement] Introducing Gnome3-next PPA!]("https://lists.ubuntu.com/archives/ubuntu-gnome/2013-September/000669.html") (creds: kansasnoob)

> "It is important to note, that **[COLOR="#B22222"]if you are using gnome3-staging PPA, then you must add gnome3-next PPA[/COLOR]** as this will contain required dependencies for the staging ppa."

Tim Lunn
Technical Lead of Ubuntu GNOME


GNOME3 Next PPA (Launchpad):  [https://launchpad.net/~gnome3-team/+archive/gnome3-next](https://launchpad.net/~gnome3-team/+archive/gnome3-next)

---

### Post by QDR06VV9 on 2013-09-11
> **VinDSL said:**
> [[Announcement] Introducing Gnome3-next PPA!]("https://lists.ubuntu.com/archives/ubuntu-gnome/2013-September/000669.html") (creds: kansasnoob)




GNOME3 Next PPA (Launchpad):  [https://launchpad.net/~gnome3-team/+archive/gnome3-next](https://launchpad.net/~gnome3-team/+archive/gnome3-next)

Thanks VinDSL

---

### Post by philinux on 2013-09-11
bit more info here.

[http://www.webupd8.org/2013/09/new-gnome-310-ppa-announced-for-ubuntu.html](http://www.webupd8.org/2013/09/new-gnome-310-ppa-announced-for-ubuntu.html)

---

### Post by VinDSL on 2013-09-11
> **runrickus said:**
> Thanks VinDSL
Welcome.

---

### Post by VinDSL on 2013-09-12
[INDENT]**[COLOR="#800080"]Ubuntu 13.10 / Gnome-Shell 3.9.91 Staging / Linux 3.11 Final / Plank / Conky 1.9.0-3 / ConkyWX 0.9.3-1[/COLOR]**
[URL="http://vindsl.com/images/vindsl-desktop-11-sep-2013-1.png"]
[IMG]http://vindsl.com/images/vindsl-desktop-11-sep-2013-1(650x520).png[/IMG][/URL][/INDENT]

---

### Post by zika on 2013-09-13
Keyboard shortcuts and Fallbacks are working again...
FBs a little bit crippled panel-wise but I'm satisfied...

---

### Post by QDR06VV9 on 2013-09-13
> **VinDSL said:**
> [INDENT]**[COLOR="#800080"]Ubuntu 13.10 / Gnome-Shell 3.9.91 Staging / Linux 3.11 Final / Plank / Conky 1.9.0-3 / ConkyWX 0.9.3-1[/COLOR]**
[URL="http://vindsl.com/images/vindsl-desktop-11-sep-2013-1.png"]
[IMG]http://vindsl.com/images/vindsl-desktop-11-sep-2013-1(650x520).png[/IMG][/URL][/INDENT]

Love the Wallpaper!
Distributor ID:	Ubuntu
Description:	Ubuntu Saucy Salamander (development branch)
Release:	13.10
Codename:	saucy
3.11.0-4-generic
GNOME Shell 3.9.91
Running Good except for a few anoying App errors..(I can deal with though)

---

### Post by zika on 2013-09-16
There is some kerfuffle with dist-upgrade... Any idea what is happening with flashback etc...?
```
The following packages will be REMOVED:
  gnome-applets gnome-control-center-datetime gnome-panel
  gnome-session-flashback indicator-datetime libcamel-1.2-44 libebackend-1.2-6
  libecal-1.2-15 libedata-book-1.2-19 libedata-cal-1.2-20
  libedataserver-1.2-17 thunderbird-gnome-support
The following NEW packages will be installed:
  libcamel-1.2-45 libebackend-1.2-7 libecal-1.2-16 libedata-book-1.2-20
  libedata-cal-1.2-23 libedataserver-1.2-18
The following packages will be upgraded:
  evolution-data-server evolution-data-server-common evolution-data-server-uoa
  folks-common gir1.2-ebook-1.2 gir1.2-ebookcontacts-1.2
  gir1.2-edataserver-1.2 gnome-contacts gnome-shell gnome-shell-common
  libebook-1.2-14 libebook-contacts-1.2-0 libfolks-eds25 libfolks-telepathy25
  libfolks25 nautilus-sendto
16 upgraded, 6 newly installed, 12 to remove and 0 not upgraded.
Need to get 6,278 kB of archives.
After this operation, 452 kB of additional disk space will be used.
Do you want to continue [Y/n]? n
```
OK, I see lot of stuff is getting newer versions, but there is some stuff that I think I should keep... Am I wrong?

---

### Post by VinDSL on 2013-09-16
Yeah, I've been seeing that, the past 24 hours or so, too.

"Smart Upgrade", so called, wants to remove essential items.  "Default Upgrade" is willing to do a partial upgrade.

Personally, I'm willing to do neither.

This is one of those times that I'll forgo upgrades, and wait for things to simmer down.  ;)

---

### Post by ricotz on 2013-09-17
There was/is a huge problem with the e-d-s packaging.  Downgrade libebackend-1.2-6, libecal-1.2-15, libedata-cal-1.2-20 and libedataserver-1.2-17 to their 3.8.4 saucy versions while upgrading. This will resolve the e-d-s conflicts.  Or you can go for with the removals and reinstall gnome-applets, gnome-control-center-datetime, gnome-panel, gnome-session-flashback and indicator-datetime.  Sorry for those disruptions.

---

### Post by zika on 2013-09-17
> **ricotz said:**
> There was/is a huge problem with the e-d-s packaging.  Downgrade libebackend-1.2-6, libecal-1.2-15, libedata-cal-1.2-20 and libedataserver-1.2-17 to their 3.8.4 saucy versions while upgrading. This will resolve the e-d-s conflicts.  Or you can go for with the removals and reinstall gnome-applets, gnome-control-center-datetime, gnome-panel, gnome-session-flashback and indicator-datetime.  Sorry for those disruptions.Thank You for a hint and for all good work, no reason to apologize whatsoever... ;)
Update&#8321;: Dived into that well, together with introducing 3.12... So far so good...

---

### Post by VinDSL on 2013-09-17
> **zika said:**
> Thank You for a hint and for all good work, no reason to apologize whatsoever...

Dittos!

It's all in good fun, ricotz...  ;)

---

### Post by VinDSL on 2013-09-17
> **ricotz said:**
> There was/is a huge problem with the e-d-s packaging.  Downgrade libebackend-1.2-6, libecal-1.2-15, libedata-cal-1.2-20 and libedataserver-1.2-17 to their 3.8.4 saucy versions while upgrading. This will resolve the e-d-s conflicts.  Or you can go for with the removals and reinstall gnome-applets, gnome-control-center-datetime, gnome-panel, gnome-session-flashback and indicator-datetime.  Sorry for those disruptions.
Decided to take Door #2.

Downgrading libebackend-1.2-6, et cetera, would have stripped my install to bare-bones; apt-get wanted to remove 10's or 100's of core packages.

Wash, rinse, and restyle went well -- survived a cold boot.

Everything boot/loaded fine on Linux 3.12-rc1 mainline kernel / nouveau.

nVidia drivers still need to be patched for Linux 3.12 -- otherwise, all is back to normal.

Thanks!

---

### Post by VinDSL on 2013-09-17
WoW!  Everything is working great!  :D


[INDENT]**[COLOR="#800080"]Ubuntu 13.10 Beta 1 / Gnome-Shell 3.9.92 Staging / Linux 3.12-rc1 / Nouveau / Plank / Conky / ConkyWX [/COLOR]**
[URL="http://vindsl.com/images/vindsl-desktop-17-sep-2013-1.png"]
[IMG]http://vindsl.com/images/vindsl-desktop-17-sep-2013-1(650x520).png[/IMG][/URL][/INDENT]


Plymouth even works/looks better...

---

### Post by VinDSL on 2013-09-18
Hrm... 

Looks like GS3 Staging has been upgraded to 3.9.92 / 3.10RC.


SOURCE:  [http://www.phoronix.com/scan.php?page=news_item&px=MTQ2NDA](http://www.phoronix.com/scan.php?page=news_item&px=MTQ2NDA)
> **[SIZE=+1]GNOME Shell 3.10 Is Ready To Shine On Wayland[/SIZE]**

*Posted by Michael Larabel on September 17, 2013*

GNOME Shell 3.9.92 was released this morning as the GNOME Shell 3.10 release candidate. With this latest release of the core GNOME 3 user-interface, **[COLOR="#0000CD"]the Wayland branch has been merged[/COLOR]**! [...]

Yummy!  :)

---

### Post by zika on 2013-09-18
```
The following packages will be REMOVED:  gnome-applets gnome-panel gnome-session-flashback libgweather-3-3
The following NEW packages will be installed:
  libgweather-3-6 librhythmbox-core8
The following packages will be upgraded:
  evolution-data-server evolution-data-server-common evolution-data-server-uoa
  gir1.2-rb-3.0 gnome-settings-daemon libcamel-1.2-45 rhythmbox rhythmbox-data
  rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugins
```
again ... ;)

---

### Post by VinDSL on 2013-09-18
Dittos...

Again, I chose Door #2.  ;)

---

### Post by zika on 2013-09-18
Does it work again?
Update&#8321;: Hah, yes it does, now I have both libgweather, whatsoever...

---

### Post by zika on 2013-09-18
Now we have too young libgnome-desktop... ;)

---

### Post by VinDSL on 2013-09-18
> **zika said:**
> Now we have too young libgnome-desktop... ;)
~cool

I'm on the trot, right now, via free wifi hotspot and my trusty, old Peppermint 4 netbook.

I'll have to play with the young ones, when I get home.  :)

---

### Post by QDR06VV9 on 2013-09-18
> **VinDSL said:**
> ~cool

I'm on the trot, right now, via free wifi hotspot and my trusty, old Peppermint 4 netbook.

I'll have to play with the young ones, when I get home.  :)
The Young Ones seem to be behaveing just fine!
```
Description:	Ubuntu Saucy Salamander (development branch)
Release:	13.10
Codename:	saucy
GNOME Shell 3.9.92

```

---

### Post by VinDSL on 2013-09-18
> **runrickus said:**
> The Young Ones seem to be behaving just fine!
Yep, working fine here, too.

Looks like we're safe, for another 24 hours...  :)

* One oddity has cropped up -- extensions keep turning themselves off during boot/restart. 

Plus, my custom css files keep getting overwritten to the default settings, even when I didn't upgrade the extension(s).  

Maybe I'll try changing the octals to read-only.  Something has changed -- can't put a finger on it.

Weird!

---

### Post by QDR06VV9 on 2013-09-18
> **VinDSL said:**
> Yep, working fine here, too.

Looks like we're safe, for another 24 hours...  :)

* One oddity has cropped up -- extensions keep turning themselves off during boot/restart. 

Plus, my custom css files keep getting overwritten to the default settings, even when I didn't upgrade the extension(s).  

Maybe I'll try changing the octals to read-only.  Something has changed -- can't put a finger on it.

Weird!
```
Looks like we're safe, for another 24 hours...  :)Looks like we're safe, for another 24 hours...  :)
```
Your sense of humor cracks me up..
```
* One oddity has cropped up -- extensions keep turning themselves off during boot/restart. 
```
Yep same here.
Just had another update will see if anything has changed.

---

### Post by QDR06VV9 on 2013-09-18
Nope rebooted to no enabled extensions.
And it overwrites my apport config.

---

### Post by QDR06VV9 on 2013-09-19
This anomalie seems to happen only on the i386 or (32bit) installs?
1 Tower with saucy 32 bit && 1 Laptop 32 32 bit, upon reboot gnome-shell extensions get reset to none.
1 Tower with saucy 64 bit gnome-shell extenions upon reboot are good to go..
Well from a cold boot 7 Hours later no extensions were enabled on the 64 bit ethier.
Just a small deal, I can set them on login!

---

### Post by VinDSL on 2013-09-20
> **runrickus said:**
> This anomalie seems to happen only on the i386 or (32bit) installs? [...]

Well from a cold boot 7 Hours later no extensions were enabled on the 64 bit either.

Just a small deal, I can set them on login!
I'm only running a couple of extensions right now, so I'm enabling them via CLI:

```
vindsl@Zuul:~$ gnome-shell-extension-tool -e **[COLOR="#0000CD"]workspace-indicator[/COLOR]**@gnome-shell-extensions.gcampax.github.com | gnome-shell-extension-tool -e **[COLOR="#0000CD"]user-theme[/COLOR]**@gnome-shell-extensions.gcampax.github.com

```

Seems to be the easiest workaround for me.

Another oddity (might be a Thunderbird 24 bug): 

When I start a T-bird session, it asks me for some (but not all) of my account passwords, e.g. it's only saving some of the passwords.

Hrm...

---

### Post by zika on 2013-09-20
> **VinDSL said:**
> ~cool

I'm on the trot, right now, via free wifi hotspot and my trusty, old Peppermint 4 netbook.

I'll have to play with the young ones, when I get home.  :)It might be that my trial with devel=rolling backfired...
[http://ubuntuforums.org/showthread.php?t=2174436&p=12794015#post12794015](http://ubuntuforums.org/showthread.php?t=2174436&p=12794015#post12794015)
I sortde that OK, but it seems that we are rolling backwards...
I'll check with ftp as suggested by one member earlier in that thread...

---

### Post by QDR06VV9 on 2013-09-20
> **VinDSL said:**
> I'm only running a couple of extensions right now, so I'm enabling them via CLI:

```
vindsl@Zuul:~$ gnome-shell-extension-tool -e **[COLOR=#0000CD]workspace-indicator[/COLOR]**@gnome-shell-extensions.gcampax.github.com | gnome-shell-extension-tool -e **[COLOR=#0000CD]user-theme[/COLOR]**@gnome-shell-extensions.gcampax.github.com

```

Seems to be the easiest workaround for me.

Another oddity (might be a Thunderbird 24 bug): 

When I start a T-bird session, it asks me for some (but not all) of my account passwords, e.g. it's only saving some of the passwords.

Hrm...
Are they still enabled from cold boot ?
Nevermind I found out myself..

---

### Post by VinDSL on 2013-09-21
Extensions are sticking now, between sessions.

It happened after incremental upgrades, this morning.

```
Commit Log for Sat Sep 21 06:45:34 2013


Upgraded the following packages:
[B][COLOR="#0000CD"]gnome-control-center (1:3.9.92-0ubuntu1~saucy4) to 1:3.9.92-0ubuntu1~saucy5
gnome-control-center-data (1:3.9.92-0ubuntu1~saucy4) to 1:3.9.92-0ubuntu1~saucy5
libgnome-control-center1 (1:3.9.92-0ubuntu1~saucy4) to 1:3.9.92-0ubuntu1~saucy5[/COLOR][/B]
libqt5concurrent5 (5.0.2+dfsg1-7ubuntu8) to 5.0.2+dfsg1-7ubuntu9
libqt5core5 (5.0.2+dfsg1-7ubuntu8) to 5.0.2+dfsg1-7ubuntu9
libqt5dbus5 (5.0.2+dfsg1-7ubuntu8) to 5.0.2+dfsg1-7ubuntu9
libqt5gui5 (5.0.2+dfsg1-7ubuntu8) to 5.0.2+dfsg1-7ubuntu9
libqt5network5 (5.0.2+dfsg1-7ubuntu8) to 5.0.2+dfsg1-7ubuntu9
libqt5opengl5 (5.0.2+dfsg1-7ubuntu8) to 5.0.2+dfsg1-7ubuntu9
libqt5opengl5-dev (5.0.2+dfsg1-7ubuntu8) to 5.0.2+dfsg1-7ubuntu9
libqt5printsupport5 (5.0.2+dfsg1-7ubuntu8) to 5.0.2+dfsg1-7ubuntu9
libqt5sql5 (5.0.2+dfsg1-7ubuntu8) to 5.0.2+dfsg1-7ubuntu9
libqt5sql5-mysql (5.0.2+dfsg1-7ubuntu8) to 5.0.2+dfsg1-7ubuntu9
libqt5sql5-sqlite (5.0.2+dfsg1-7ubuntu8) to 5.0.2+dfsg1-7ubuntu9
libqt5test5 (5.0.2+dfsg1-7ubuntu8) to 5.0.2+dfsg1-7ubuntu9
libqt5widgets5 (5.0.2+dfsg1-7ubuntu8) to 5.0.2+dfsg1-7ubuntu9
libqt5xml5 (5.0.2+dfsg1-7ubuntu8) to 5.0.2+dfsg1-7ubuntu9
qt5-default (5.0.2+dfsg1-7ubuntu8) to 5.0.2+dfsg1-7ubuntu9
qt5-qmake (5.0.2+dfsg1-7ubuntu8) to 5.0.2+dfsg1-7ubuntu9
qtbase5-dev (5.0.2+dfsg1-7ubuntu8) to 5.0.2+dfsg1-7ubuntu9
qtbase5-dev-tools (5.0.2+dfsg1-7ubuntu8) to 5.0.2+dfsg1-7ubuntu9
qtbase5-doc (5.0.2+dfsg1-7ubuntu8) to 5.0.2+dfsg1-7ubuntu9

```

Take your pick. ;)

Probably the g-c-c upgrades...

---

### Post by QDR06VV9 on 2013-09-24
Gnome 3.10 is here!

---

### Post by zika on 2013-09-24
gnome-shell-extensions is slowing down if not halting progress here after successful start of 3.10...

---

### Post by JMB74 on 2013-09-24
Shell extensions built and OK here now.

---

### Post by QDR06VV9 on 2013-09-24
> **JMB74 said:**
> Shell extensions built and OK here now.

Same here!:p

---

### Post by zika on 2013-09-24
Same here. Thank You...

---

### Post by lonniehenry-gmail on 2013-09-27
I am finding that the extensions are not sticking for me either from a cold boot or when coming back from suspend. Any ideas to make that work?  I have all the gnome 3 ppas enabled.  3.10.0.1 gnome shell is the version.

---

### Post by VinDSL on 2013-09-27
> **lonniehenry-gmail said:**
> I am finding that the extensions are not sticking for me either from a cold boot or when coming back from suspend. Any ideas to make that work?
They quit sticking for me (again) too.

With everything changing, as fast as it, I haven't spent a lot of time, trying to put a finger on the prob.

They'll fix it, sooner or later...  ;)

---

### Post by QDR06VV9 on 2013-09-27
> **VinDSL said:**
> They quit sticking for me (again) too.

[COLOR=#0000cd]_With everything changing, as fast as it,_[/COLOR] I haven't spent a lot of time, trying to put a finger on the prob.

They'll fix it, sooner or later...  ;)

Yeah same here, I have been spending way too much time trying to sort out installing nvidia-drivers on kernel 3.12.
Funny thing is I have about 5 installs of saucy 32bit & 64bit and one of them sticks perfectly:confused:

---

### Post by VinDSL on 2013-09-27
> **runrickus said:**
> Funny thing is I have about 5 installs of saucy 32bit & 64bit and one of them sticks perfectly:confused:
Heh!  The following leaves me scratching my head...

I tweak a few files, every time GS is upgraded -- basically, aesthetic stuff.  I change a few things I can't stand to look at, like the butt fugly time/date menu (e.g. digital clock) in the middle of the upper panel.

One of the files I hack is:

/usr/share/gnome-shell/extensions/workspace-indicator@gnome-shell-extensions.gcampax.github.com/stylesheet.css


I change the default file from:

```
.panel-workspace-indicator {
	padding: 0 8px;
	background-color: rgba(200, 200, 200, .5);
	border: 1px solid #cccccc;
}
```


To:

```
.panel-workspace-indicator {
	padding: 1px 7px;
	background-color: rgba(000, 000, 000, .25);
	border: .5px solid #aaaaaa;
}
```


No big deal, right?

The funny thing is, this css file occasionally reverts back to the default code, in between upgrades.

LoL!  I don't understand the process taking place here -- never seen anything like it before.  

It's like my computer is haunted... :D

---

### Post by QDR06VV9 on 2013-09-28
> **VinDSL said:**
> 

It's like my computer is haunted... :D
Maybe Its a Hallowen Thing?;)
It has been a wild ride with saucy!!

---

### Post by VinDSL on 2013-09-28
> **runrickus said:**
> It has been a wild ride with saucy!!
Agreed!

When I get rid of the clock (/usr/share/gnome-shell/js/ui/panel.js):

```
<SNIP>


const PANEL_ITEM_IMPLEMENTATIONS = {
    'activities': ActivitiesButton,
    'aggregateMenu': AggregateMenu,
    'appMenu': AppMenuButton,
[s]    'dateMenu': imports.ui.dateMenu.DateMenuButton,    [/s]
    'a11y': imports.ui.status.accessibility.ATIndicator,
    'a11yGreeter': imports.ui.status.accessibility.ATGreeterIndicator,
    'keyboard': imports.ui.status.keyboard.InputSourceIndicator,
};


<SNIP>
```

...it sticks, until the next upgrade.

Why NOT the stylesheet  :confused:

Weird!

---

### Post by QDR06VV9 on 2013-09-28
> **VinDSL said:**
> 
...it sticks, until the next upgrade.

Why NOT the stylesheet  :confused:

Weird!
That panel is pretty touchy since gnome3 it might have to be wriiten like an extension?(just a thought) Like a whole new extension.
Info [http://en.wikipedia.org/wiki/Monkey_patch](http://en.wikipedia.org/wiki/Monkey_patch)

---

### Post by QDR06VV9 on 2013-10-01
Ok finally figured out the extensions not sticking!
sudo apt-get uninstall gnome-screensaver
Dont know why that bothered me soo baad..
Nevermind stiil _DONT_ stick.

---

### Post by Andrew_Fossey on 2013-10-04
A bug has filed at: [https://bugs.launchpad.net/ubuntu-gnome/+bug/1235072](https://bugs.launchpad.net/ubuntu-gnome/+bug/1235072)

---

### Post by VinDSL on 2013-10-04
> **Andrew_Fossey said:**
> A bug has filed at: [https://bugs.launchpad.net/ubuntu-gnome/+bug/1235072](https://bugs.launchpad.net/ubuntu-gnome/+bug/1235072)
Thanks! Added myself to the bug.

This is a real corker, isn't it?

Last night, just prior to shutting down this machine, my GPU locked up, e.g. nouveau crashed. I was actually closing some apps, prior to shutdown, when the lockup occured.  

So, I simply pressed the power button, on the computer case, to power down, and I went to bed.

This morning, when I booted up, the extensions loaded just fine at startup.

Thus, I judge, the startup problem is actually taking place during the shutdown process.

Put another way, since this machine didn't go through a normal shutdown process, the extensions worked just fine at startup.

It's a riddle, wrapped in an enigma...  LoL!  :D

This would be a good one for Doug -- wish he was running GS Staging.

---

### Post by mc4man on 2013-10-05
> **VinDSL said:**
> USB2.  I'm currently running Peppermint on all portables.

Peppermint 4 OS (Lubuntu fork with LXDE DE and Xfwm4 WM) is shockingly fast on USB2.

I've tried many, many, OSs on bootable/persistent USB sticks.  Peppermint runs circles around them all.
With my linux laptop pretty much ready for recycling tried an Ubuntu install to a usb 2.0 16gb drive. Was useful for some limited things though tended to get stuffed up & slow. (using a lenovo y580

Decided to install to an external ssd (screen), works remarkably well, for the moment will just run this way on  this laptop
(The next laptop I get will have to have UASP support for usb 3 & maybe eSATA

---

### Post by VinDSL on 2013-10-05
> **mc4man said:**
> [...] tried an Ubuntu install to a usb 2.0 16gb drive. Was useful for some limited things...

[...] external ssd (screen), works remarkably well... next laptop I get will have to have UASP support...
Nice!

I've read that USB3 & eSATA external drive performance is indistinguishable from internal drives.  UASP would be the frosting_on_the_cake, I suppose.  :)

I'll probably just keep running USB2 sticks.  I'm partial to SanDisk Cruzers, although I've been known to pick up a handful of no-name USB2 sticks from time_to_time, for 'loaning' to friends.  

My only requirement is, USB sticks must have retractable tips -- they're the only ones what survive rugged handling, e.g. carrying them in your pocket and/or dangling from a keychain.  ;)

That said, I've never tried GS Staging on a USB stick.  Wonder how that would run?!?!?

---

### Post by QDR06VV9 on 2013-10-07
> **VinDSL said:**
> 
That said, I've never tried GS Staging on a USB stick.  Wonder how that would run?!?!?

For Me it was very slow!
KDE was a little better outside of heavy apps like browsers, and media apps.
I ditched Gnome for KDE.

---

### Post by zika on 2013-10-10
Some packages are kept back...
Anything major happening?

---

### Post by QDR06VV9 on 2013-10-10
> **zika said:**
> Some packages are kept back...
Anything major happening?
Well took a regular update All good!:P
Then dist-upgrade, here is the output:```
The following packages will be REMOVED:
  nvidia-325
The following NEW packages will be installed:
  libsasl2-modules-db liburl-dispatcher1 linux-headers-3.11.0-12
  linux-headers-3.11.0-12-generic linux-image-3.11.0-12-generic
  linux-image-extra-3.11.0-12-generic linux-signed-image-3.11.0-12-generic
  nvidia-331 python-commandnotfound python-gdbm
The following packages will be upgraded:
  indicator-bluetooth libsasl2-2 linux-generic linux-headers-generic
  linux-image-generic linux-signed-image-generic nvidia-319 sessioninstaller
8 upgraded, 10 newly installed, 1 to remove and 0 not upgraded.
Need to get 146 MB of archives.
After this operation, 311 MB of additional disk space will be used.
Do you want to continue [Y/n]? 


```

Lets see whats new?
Everything hunky dorey here:P

---

### Post by zika on 2013-10-10
```
The following packages will be REMOVED:
  gdm gnome-shell gnome-shell-extensions
The following packages have been kept back:
  gjs xserver-xorg-video-nouveau
The following packages will be upgraded:
  gnome-shell-common
```
```
The following NEW packages will be installed:
  libgjs0e{ab} 
The following packages will be upgraded:
  gjs gnome-shell gnome-shell-common xserver-xorg-video-nouveau{b} 
4 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,516 kB of archives. After unpacking 544 kB will be used.
The following packages have unmet dependencies:
 libgjs0e : Conflicts: libgjs0d but 1.38.1-0ubuntu1~13.10~ricotz0 is installed.
 xserver-xorg-video-nouveau : Depends: xorg-video-abi-13 which is a virtual package.
The following actions will resolve these dependencies:


     Remove the following packages:                       
1)     gdm                                                
2)     gjs                                                
3)     gnome-shell                                        
4)     gnome-shell-extensions                             
5)     xserver-xorg-video-all                             
6)     xserver-xorg-video-nouveau                         


     Keep the following packages at their current version:
7)     libgjs0e [Not Installed]                      
```
```
sudo apt-get purge libgjs0d -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gkbd-3.0 gir1.2-gtop-2.0 gir1.2-mutter-3.0
  gir1.2-nmgtk-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-xkl-1.0 libgdm libmozjs-17.0-0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gdm* gjs* gnome-shell* gnome-shell-extensions* libgjs0d*
0 upgraded, 0 newly installed, 5 to remove and 2 not upgraded.
Purg gdm [3.10.0-0ubuntu1~saucy1]
Purg gnome-shell-extensions [3.10.0+git20131001.396f7f84-0ubuntu1~13.10~ricotz0]
Purg gnome-shell [3.10.0.1+git20131003.56c48734-0ubuntu1~13.10~ricotz0]
Purg gjs [1.37.6+git20130826.580ac8c3-0ubuntu1~13.10~ricotz0]
Purg libgjs0d [1.38.1-0ubuntu1~13.10~ricotz0]
```
```
sudo apt-get install libgjs0e -sReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gkbd-3.0 gir1.2-gtop-2.0 gir1.2-mutter-3.0
  gir1.2-nmgtk-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-xkl-1.0 gjs libgdm
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gjs
The following packages will be REMOVED:
  gdm gnome-shell gnome-shell-extensions libgjs0d
The following NEW packages will be installed:
  libgjs0e
The following packages will be upgraded:
  gjs
1 upgraded, 1 newly installed, 4 to remove and 2 not upgraded.
Remv gdm [3.10.0-0ubuntu1~saucy1]
Remv gnome-shell-extensions [3.10.0+git20131001.396f7f84-0ubuntu1~13.10~ricotz0]
Remv gnome-shell [3.10.0.1+git20131003.56c48734-0ubuntu1~13.10~ricotz0]
Inst gjs [1.37.6+git20130826.580ac8c3-0ubuntu1~13.10~ricotz0] (1.39.0~git20131002.1c6708d5-0ubuntu1~13.10~ricotz0 Staging PPA:13.10/saucy [amd64]) []
Remv libgjs0d [1.38.1-0ubuntu1~13.10~ricotz0] []
Inst libgjs0e (1.39.0~git20131002.1c6708d5-0ubuntu1~13.10~ricotz0 Staging PPA:13.10/saucy [amd64])
Conf libgjs0e (1.39.0~git20131002.1c6708d5-0ubuntu1~13.10~ricotz0 Staging PPA:13.10/saucy [amd64])
Conf gjs (1.39.0~git20131002.1c6708d5-0ubuntu1~13.10~ricotz0 Staging PPA:13.10/saucy [amd64])
```

---

### Post by QDR06VV9 on 2013-10-10
> **zika said:**
> ```
The following packages will be REMOVED:
  gdm gnome-shell gnome-shell-extensions
The following packages have been kept back:
  gjs xserver-xorg-video-nouveau
The following packages will be upgraded:
  gnome-shell-common
```
```
The following NEW packages will be installed:
  libgjs0e{ab} 
The following packages will be upgraded:
  gjs gnome-shell gnome-shell-common xserver-xorg-video-nouveau{b} 
4 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,516 kB of archives. After unpacking 544 kB will be used.
The following packages have unmet dependencies:
 libgjs0e : Conflicts: libgjs0d but 1.38.1-0ubuntu1~13.10~ricotz0 is installed.
 xserver-xorg-video-nouveau : Depends: xorg-video-abi-13 which is a virtual package.
The following actions will resolve these dependencies:


     Remove the following packages:                       
1)     gdm                                                
2)     gjs                                                
3)     gnome-shell                                        
4)     gnome-shell-extensions                             
5)     xserver-xorg-video-all                             
6)     xserver-xorg-video-nouveau                         


     Keep the following packages at their current version:
7)     libgjs0e [Not Installed]                      
```
```
sudo apt-get purge libgjs0d -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gkbd-3.0 gir1.2-gtop-2.0 gir1.2-mutter-3.0
  gir1.2-nmgtk-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-xkl-1.0 libgdm libmozjs-17.0-0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gdm* gjs* gnome-shell* gnome-shell-extensions* libgjs0d*
0 upgraded, 0 newly installed, 5 to remove and 2 not upgraded.
Purg gdm [3.10.0-0ubuntu1~saucy1]
Purg gnome-shell-extensions [3.10.0+git20131001.396f7f84-0ubuntu1~13.10~ricotz0]
Purg gnome-shell [3.10.0.1+git20131003.56c48734-0ubuntu1~13.10~ricotz0]
Purg gjs [1.37.6+git20130826.580ac8c3-0ubuntu1~13.10~ricotz0]
Purg libgjs0d [1.38.1-0ubuntu1~13.10~ricotz0]
```
```
sudo apt-get install libgjs0e -sReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gkbd-3.0 gir1.2-gtop-2.0 gir1.2-mutter-3.0
  gir1.2-nmgtk-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-xkl-1.0 gjs libgdm
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gjs
The following packages will be REMOVED:
  gdm gnome-shell gnome-shell-extensions libgjs0d
The following NEW packages will be installed:
  libgjs0e
The following packages will be upgraded:
  gjs
1 upgraded, 1 newly installed, 4 to remove and 2 not upgraded.
Remv gdm [3.10.0-0ubuntu1~saucy1]
Remv gnome-shell-extensions [3.10.0+git20131001.396f7f84-0ubuntu1~13.10~ricotz0]
Remv gnome-shell [3.10.0.1+git20131003.56c48734-0ubuntu1~13.10~ricotz0]
Inst gjs [1.37.6+git20130826.580ac8c3-0ubuntu1~13.10~ricotz0] (1.39.0~git20131002.1c6708d5-0ubuntu1~13.10~ricotz0 Staging PPA:13.10/saucy [amd64]) []
Remv libgjs0d [1.38.1-0ubuntu1~13.10~ricotz0] []
Inst libgjs0e (1.39.0~git20131002.1c6708d5-0ubuntu1~13.10~ricotz0 Staging PPA:13.10/saucy [amd64])
Conf libgjs0e (1.39.0~git20131002.1c6708d5-0ubuntu1~13.10~ricotz0 Staging PPA:13.10/saucy [amd64])
Conf gjs (1.39.0~git20131002.1c6708d5-0ubuntu1~13.10~ricotz0 Staging PPA:13.10/saucy [amd64])
```

What to Do?:confused:
I think I would wait a bit! Just my humble 2cents worth.
Good Luck !
Regards
Your last Quote box just showed up?? Hate it when that happens

---

### Post by zika on 2013-10-10
> **runrickus said:**
> What to Do?:confused:Your last Quote box just showed up?? Hate it when that happens> **runrickus said:**
> &#8222;I think I would wait a bit! Just my humble 2cents worth.&#8220;
I've send a message to Ricotz...

---

### Post by ricotz on 2013-10-10
Make sure to mention you are using ppa:ricotz/staging and be aware of that!  And yes, I am aware of it. ;) 
So if you are using ppa:gnome3-team/gnome3, ppa:gnome3-team/gnome3-stating, ppa:ricotz/testing and ppa:ricotz/staging you can assume the stability sinks in this order and the fun increases.

---

### Post by mc4man on 2013-10-10
One of the 'related' ppa's I find useful is the experimental for gstreamer, particularly the libav plugin which uses it's own libav rather than shared system libs.
Though it's a bit of a pita to use that ppa because it doesn't build all the gst packages for some reason & continually has a minor overwrite issue on updates

---

### Post by zika on 2013-10-10
> **ricotz said:**
> Make sure to mention you are using ppa:ricotz/staging and be aware of that!  And yes, I am aware of it. ;) 
So if you are using ppa:gnome3-team/gnome3, ppa:gnome3-team/gnome3-stating, ppa:ricotz/testing and ppa:ricotz/staging you can assume the stability sinks in this order and the fun increases.Yes I'm aware of that... I've embarked on that boat intentionally... I'm not complaining, just clumsy trying to be helpful... Stability is not my goal... ;) With every situation like this I seem to learn a bit more than before... For an old geezer like me that is enough...

---

### Post by ricotz on 2013-10-10
> **zika said:**
> Yes I'm aware of that... I've embarked on that boat intentionally... I'm not complaining, just clumsy trying to be helpful... Stability is not my goal... ;) With every situation like this I seem to learn a bit more than before... For an old geezer like me that is enough...  Simply disable ppa:ricotz/staging and update/upgrade. You can enable it after that if you insist.

---

### Post by zika on 2013-10-10
> **ricotz said:**
> Simply disable ppa:ricotz/staging and update/upgrade. You can enable it after that if you insist.Yawohl Master Yoda...
As I expected, it worked... Thak You Master Yoda... Even after staging is enabled again only gjs is kept back...

---

### Post by QDR06VV9 on 2013-10-10
> **zika said:**
> Yes I'm aware of that... I've embarked on that boat intentionally... I'm not complaining, just clumsy trying to be helpful... Stability is not my goal... ;) With every situation like this I seem to learn a bit more than before... _For an old geezer like me that is enough..._

Yes us Geezers are quite entertained over here in testing land!!:p

---

### Post by VinDSL on 2013-10-10
> **ricotz said:**
> [...] you can assume the stability sinks in this order and the fun increases.
Bwahahaha!  First LoL_of_the_day!

Thanks, for that...  :D

---

### Post by VinDSL on 2013-10-10
> **zika said:**
> Stability is not my goal... ;) With every situation like this I seem to learn a bit more than before...
Golden!

This is turning into a real adventure...

---

### Post by QDR06VV9 on 2013-10-10
> **VinDSL said:**
> Bwahahaha!  First LoL_of_the_day!

Thanks, for that...  :D
Where the [COLOR=#ffff00]hell[/COLOR] (Opps) heck have you been?
All this fun going on here and you leave ventrical,  zika, and myself out here towing the load,LOL!:P

---

### Post by VinDSL on 2013-10-10
Well, drat!

I'm doing an upgrade, right now, and nothing is being held back.

I wonder what I'm doing wrong  :confused:

---

### Post by VinDSL on 2013-10-10
> **runrickus said:**
> Where the [COLOR=#ffff00]heck[/COLOR] (Opps) heck have you been?
Heh! Haxor took over the exim server on my production site.

I had a half-million spams sitting in the cache.

A couple of them hit honeypots, and my ASP is threatening to suspend my account, if I don't take care of it.

Still trying to figure out how the perps did it...

Anyway, back on topic -- just couldn't resist commenting on those most-excellent replies.

---

### Post by QDR06VV9 on 2013-10-10
> **VinDSL said:**
> Well, drat!

I'm doing an upgrade, right now, and nothing is being held back.

I wonder what I'm doing wrong  :confused:

```
dist-upgrade & upgrade?
```
Ok thats just weird I rebooted to another partion and got held packages 3 I belive.
The funny thing is that it is on the same machine???? Upgrades were about 10 mins apart from system to system.

---

### Post by QDR06VV9 on 2013-10-10
> **VinDSL said:**
> Heh! Haxor took over the exim server on my production site.

I had a half-million spams sitting in the cache.

A couple of them hit honeypots, and my ASP is threatening to suspend my account, if I don't take care of it.

_Still trying to figure out how the perps did it..._

Anyway, back on topic -- just couldn't resist commenting on those most-excellent replies.

Most anoying!!:mad: script kiddies.

---

### Post by zika on 2013-10-15
Latest upgrade made me use startx singe GDM stopped cooperating...
```
Start-Date: 2013-10-15  13:47:59
Commandline: apt-get dist-upgrade
Install: libgjs0e:amd64 (1.39.0~git20131015.js24.c2b8cc34-0ubuntu1~13.10~ricotz0, automatic)
Upgrade: gnome-shell:amd64 (3.10.0.1+git20131014.5c5f2fdf-0ubuntu1~13.10~ricotz0, 3.10.0.1+git20131014.5c5f2fdf-0ubuntu1~13.10~ricotz10), gnome-shell-common:amd64 (3.10.0.1+git20131014.5c5f2fdf-0ubuntu1~13.10~ricotz0, 3.10.0.1+git20131014.5c5f2fdf-0ubuntu1~13.10~ricotz10), gjs:amd64 (1.38.1-0ubuntu1~13.10~ricotz0, 1.39.0~git20131015.js24.c2b8cc34-0ubuntu1~13.10~ricotz0)
Remove: libgjs0d:amd64 (1.38.1-0ubuntu1~13.10~ricotz0)
End-Date: 2013-10-15  13:48:11
```
Not a big deal, I'm actually enjoying it... ;)

---

### Post by VinDSL on 2013-10-31
w00t!

Finally got around to hacking the uber-ugly workspace-indicator button...


[INDENT][IMG]http://vindsl.com/images/workspace-indicator.png[/IMG][/INDENT]


EDIT:  /usr/share/gnome-shell/extensions/workspace-indicator@gnome-shell-extensions.gcampax.github.com/stylesheet.css

```
.panel-workspace-indicator {
	padding: 2px 6px;
	background-color: transparent !important;
	border-radius: 6px !important;
	border: 1px solid rgba(128,128,128,0.50); 
}
```

---

### Post by VinDSL on 2013-11-02
[INDENT]**[COLOR="#800080"]  Ubuntu 'Trusty' 14.04 (32 Bit) / Custom Linux 3.12-rc7 Kernel / GS 3.11.1 Staging  / Conky / ConkyWX[/COLOR]**

[[IMG]http://vindsl.com/images/vindsl-desktop-2-nov-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-2-nov-2013-1.png")[/INDENT]

---

### Post by QDR06VV9 on 2013-11-02
> **VinDSL said:**
> [INDENT]**[COLOR=#800080]  Ubuntu 'Trusty' 14.04 (32 Bit) / Custom Linux 3.12-rc7 Kernel / GS 3.11.1 Staging  / Conky / ConkyWX[/COLOR]**


[/INDENT]
 Vin Thats Looks Great..:o
How did you get the top panel transparent?

---

### Post by VinDSL on 2013-11-02
> **runrickus said:**
> How did you get the top panel transparent?
I use an 'older_than_dirt' GTK+ theme:  GnomishDark

I hacked the workspace-indictor css file and made it a trans button (documented a couple of posts back).

I still need to get rid of the $#@! clock - that thing is like a virus.  Grrr...

Looks like 'they' got rid of the '/usr/share/gnome-shell/js/ui/panel.js' file.  That's where I used to squash it.

Matter of fact, I'm going to see where they moved that function, right now.

Thanks for reminding me!  ;)

---

### Post by QDR06VV9 on 2013-11-03
> **VinDSL said:**
> I use an 'older_than_dirt' GTK+ theme:  GnomishDark

I hacked the workspace-indictor css file and made it a trans button (documented a couple of posts back).



Yes I follow all posts here..
I've been playing with /usr/share/gnome-shell/theme/gnome-shell.css
Then The #panel Well Here```
#panel {
    color: #ffffff;
    /*background-color: black;*/
    background-color: rgba(0,0,0,0.6);
    /*border-image: url("panel-border.svg") 1;*/
}
```
But it breaks my system:confused:

Sometimes I'm not the sharpest tool in the shed.
This should have been at the bottom
```
 background-color: rgba(0,0,0,0.6);
```
All's Welll that ends well..LOL
By the way VinDSL You stoled my Girl!  OMG Shes A Beauty..

---

### Post by VinDSL on 2013-11-17
Heh!  Totally borked my GS staging install, while upgrading 3.11.1 => 3.11.2

Got stuck in a 'partial upgrade' loop -- thought I could pull it off, but no joy.  GDM / GS / Mutter all disappeared.

Oh, well, it'll give me something to do today -- putting Humpty Dumpty back together again... :)

---

### Post by QDR06VV9 on 2013-11-17
> **VinDSL said:**
> 
Oh, well, it'll give me something to do today -- putting Humpty Dumpty back together again... :)

You just hate when things just work!;) 

But when I saw Nemo being removed it was a no GO!
The work flow with Nemo for me is a must...
```
Calculating upgrade... Done
The following packages will be REMOVED:
  cinnamon cinnamon-screensaver gir1.2-muffin-3.0 libcogl-pango12 libcogl12
  libmuffin0 libmuonprivate1 nemo nemo-fileroller nemo-preview nemo-terminal


```

---

### Post by VinDSL on 2013-11-17
> **runrickus said:**
> You just hate when things just work!;) 
This will be a fun one -- total breakage!  Yay!  :D

First impression is... ricotz/testing packages aren't playing nice with the other PPAs.

I need to check out my sources list(s).  I *know* it's a complete mess, at this stage.

Thankfully, I always have Ubu 10.10 at the ready.  ;)

---

### Post by QDR06VV9 on 2013-11-17
> **VinDSL said:**
> Ubu 10.10 at the ready[/COLOR].  ;)
That was also my guess also on ricotz PPA
[COLOR=#ff0000]Ubu 10.10 at the ready[/COLOR]. Mine is Solus Eveline _which is no more_(Poor Ikey:()

---

### Post by VinDSL on 2013-11-17
Hrm...

Well, I got GS to load again, but now my mouse pointer has disappeared.  

Evidently, GS isn't recognizing my display.

I'm tired of messing with it.  Tomorrow is a new day...  ;)

---

### Post by VinDSL on 2013-11-22
Heh!  That was a good one!

Took me four days to figure out how to get my pointer back in GS...  :D

```
vindsl@Zuul:~$ dconf write /org/gnome/settings-daemon/plugins/cursor/active false

```

---

### Post by zika on 2013-11-23
It seems that today is a stormy day here in 13.10. GS-PPA. Is is similar in 14.04?
Fonts and icons getting blown away... ;)

---

### Post by QDR06VV9 on 2013-11-23
> **VinDSL said:**
> Heh!  That was a good one!

[U]Took me four days to figure out how to get my pointer back in GS...  :D
[/U]
```
vindsl@Zuul:~$ dconf write /org/gnome/settings-daemon/plugins/cursor/active false

```

Vin I'm sorry to here that!
I Should have suggested that days ago, a few of us had that very problem a while back.
My apology SIr:(

---

### Post by VinDSL on 2013-11-23
> **zika said:**
> It seems that today is a stormy day here [...]

> **runrickus said:**
> [...] a few of us had that very problem a while back.
I'm gonna lay_low for a few days.  Too many things are in flux right now, e.g. everything is brittle and easily broken.

I'm going to take this opportunity to regroup -- clean the cruft out of my 'sources.list' -- and so forth, and so on -- basically prepare for proper 14.04 LTS testing.

It was fun figuring out the disappearing mouse pointer.  I discovered '[unclutter]("https://launchpad.net/ubuntu/+source/unclutter")' in the process.

> **DESCRIPTION**
       unclutter  removes the cursor image from the screen so that it does not
       obstruct the area you are looking at after it has not moved for a given
       time.   It  does  not  do this if the cursor is in the root window or a
       button is down.  It tries to ignore  jitter  (small  movements  due  to
       noise) if you have a mouse that twitches.

That's one of the joys of spending four days wracking your brain, trying to figure out a solution, you know?

You discover a lot of things that you wouldn't normally run across...  ;)

---

### Post by zika on 2013-11-23
> **VinDSL said:**
> I'm gonna lay_low for a few days.  Too many things are in flux right now, e.g. everything is brittle and easily broken.

I'm going to take this opportunity to regroup -- clean the cruft out of my 'sources.list' -- and so forth, and so on -- basically prepare for proper 14.04 LTS testing.

It was fun figuring out the disappearing mouse pointer.  I discovered '[unclutter]("https://launchpad.net/ubuntu/+source/unclutter")' in the process.



That's one of the joys of spending four days wracking your brain, trying to figure out a solution, you know?

You discover a lot of things that you wouldn't normally run across...  ;)I just said it was stormy, but nothing that a minute or less of thinking could not resolve. Experience gained here in U+1 comes as a good umbrella sometimes.
Unclutter went off my machine couple of cycles ago. You're all making me more and more impatient to embark on 14.04 but I'm stubborn this time playing with new Mesa and couple of other things that I do not have equivalent in PPAs for TT. ;)

---

### Post by VinDSL on 2013-11-23
> **zika said:**
> You're all making me more and more impatient to embark on 14.04 but I'm stubborn this time [...]
You're proceeding wisely.

I shouldn't have been so impetuous -- caused me several days of grief.  ;)

Jury is still out on 'unclutter'.  In a way, I like it, but it acts strangely when I'm scrolling with my mouse wheel.  Maybe there's a setting that can be tweaked.  If not, I'll probably dump it too...

---

### Post by zika on 2013-11-24
> **VinDSL said:**
> You're proceeding wisely.

I shouldn't have been so impetuous -- caused me several days of grief.  ;)
Word &#8222;wisely&#8220; is one of those words that I could not associate with me at any time in my life. Simply put, life threw some big stones towards my head these days and I'm just too preoccupied escaping them so...

> **VinDSL said:**
> Jury is still out on 'unclutter'.  In a way, I like it, but it acts strangely when I'm scrolling with my mouse wheel.  Maybe there's a setting that can be tweaked.  If not, I'll probably dump it too...I've felt much less clutter without unclutter. So... ;)

---

### Post by mc4man on 2013-11-24
> **VinDSL said:**
> Heh!  That was a good one!

Took me four days to figure out how to get my pointer back in GS...  :D

```
vindsl@Zuul:~$ dconf write /org/gnome/settings-daemon/plugins/cursor/active false

```
Interesting that you found that plugin to be more of an issue in gnome world than the occasional problems it creates in ubuntu land.
Been an ongoing problem since 13.10 though not all the time - 
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1238410](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1238410)
I get rid of the plugin as haven't found what good it does other than this feature which doesn't matter much here
[https://bugzilla.gnome.org/show_bug.cgi?id=687791](https://bugzilla.gnome.org/show_bug.cgi?id=687791)

---

### Post by VinDSL on 2013-11-24
> **mc4man said:**
> Interesting that you found that plugin to be more of an issue in gnome world than the occasional problems it creates in ubuntu land.[...]
Forensics (if you will) is my favorite part of the +1 experience.

I enjoy watching the community discovering and solving problems and/or coming up with workarounds, et cetera.

You are the best, IMO.  You're able to articulate problem(s), reduce it to 'paper' e.g. write out comprehensive bug reports, and effect change.  You never fail to amaze...

This 'disappearing mouse pointer', in GS Staging, was particularly vexing for me, because it's almost impossible to navigate with a pointer-less mouse.  Actually, I got so embroiled in figuring out how to navigate GS without a mouse, that I wasn't seeing the forest_for_the_trees.  It totally broke my concentration.

An epiphany came about, when I focused on the lack of a pointer in GDM.  Ultimately, the culprit was a simple plugin setting. Restoring the pointer on the desktop was an unexpected byproduct of fixing GDM -- call it dumb_luck.

I *think* this plugin setting was changed, during a recent upgrade, to accommodate touch screen users -- but, that's just a hunch.

Anyway, I finally got everything up n' running, albeit version 3.8.4-0ubuntu5...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-24-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-24-2013-1.png")[/INDENT]


That'll do for now.

After I've licked my wounds, for a few days, I'll jump back into the fray and install GS Staging again.  ;)

---

### Post by zika on 2013-11-25
> **VinDSL said:**
> Heh!  That was a good one!

Took me four days to figure out how to get my pointer back in GS...  :D

```
vindsl@Zuul:~$ dconf write /org/gnome/settings-daemon/plugins/cursor/active false

```I forgot to write: [http://ubuntuforums.org/showthread.php?t=2175433](http://ubuntuforums.org/showthread.php?t=2175433) ...

---

### Post by VinDSL on 2013-11-25
> **zika said:**
> I forgot to write: [http://ubuntuforums.org/showthread.php?t=2175433](http://ubuntuforums.org/showthread.php?t=2175433) ...
Thanks!

I wonder why they closed that thread!?!?!

Makes it hard to find, when they bury a story on the back page -- old newspaper trick... :p

---

### Post by QDR06VV9 on 2013-11-25
> **VinDSL said:**
> Thanks!

I wonder why they closed that thread!?!?!

Makes it hard to find, when they bury a story on the back page -- old newspaper trick... :p

On a side note, Control+Alt+F1 and Then Control+Alt+F7 also works!

---

### Post by zika on 2013-11-25
> **runrickus said:**
> On a side note, Control+Alt+F1 and Then Control+Alt+F7 also works!
As I wrote in a thread I've mentioned above, I think more than once, that kind of gymnastics did not work for me at the time I had problems with cursor. You do not have to yell, I am old but I can hear OK... ;)

---

### Post by QDR06VV9 on 2013-11-25
> **zika said:**
> As I wrote in a thread I've mentioned above, I think more than once, that kind of gymnastics did not work for me at the time I had problems with cursor. _You do not have to yell, I am old but I can hear OK..._;) 

How am i yelling? merely suggesting as it has worked for me and others.
I have nothing but _respect_ for you and everyone here in U+1
Regards

---

### Post by zika on 2013-11-25
> **runrickus said:**
> How am i yelling? merely suggesting as it has worked for me and others.
I have nothing but _respect_ for you and everyone here in U+1
Regards„!“...:guitar:

---

### Post by QDR06VV9 on 2013-11-25
> **zika said:**
> &#8222;!&#8220;...:guitar:

my post was not even directed to or at you, as i'm sure you already know.
this will be my last comment on this.
From the Latin, "to call" meaning of keyboard explanation point
One theory of its origin is that it was a Latin exclamation of joy or for additional emphasis. 

in forums it is my understanding that this is YELLING or SHOUTING, so if this "!" is yelling i am ignorant(lack of knowledge) to that. Feel free not to respond to any of my posts.:D sorry for being so off topic GNOME3 Staging PPA

---

### Post by cariboo on 2013-11-25
Could we please keep this thread on topic.

---

### Post by zika on 2013-11-27
Even though I'm still on SS I'm using SS branch of Gnome-Next and Ricotz branches...
Question: Did anybody try to (re)solve gdm waiting (due to libgdm1 not ready to present itself to the world, i.e. dependencies are a bit wrong)? Did anyone try to purge libgdm and then install libgdm1 and gir1.1.2-gdm-1.0. Than would mean to purge also gdm, gnome-shell and gnome-shell-extensions but I'm not sure that I would be able to install them after that (with libdrm1 installed) since I am afraid that they have strict dependency on libdrm... Any ideas?

---

### Post by QDR06VV9 on 2013-12-01
Booted to saucy today saw your post.
zika I have the same repos or ppa's as you do enabled, only diffrence is I am running 32bit (should be a non factor though)
Took the plunge today and everything went smoothly,
```
gnome-shell --version
GNOME Shell 3.11.2
```
The same icon & fonts blowouts acured & I only lost topicons on extensions.
Been playing with it for a couple of hours now, No show stopers yet.
Regards;)

---

### Post by zika on 2013-12-01
Yes, I've exchanged couple of e-mails with Tim and Ricitz and everything went well couple of days ago. Everything is nice now in GS world... At least in SS neighborhood I live in... ;)

---

### Post by QDR06VV9 on 2013-12-01
> **zika said:**
>  everything went well _couple of days ago_. Everything is nice now in GS world... At least in SS neighborhood I live in... ;)

Thought that might be the case, but I thought I would chime in just for reassurance.
Regards

---

### Post by zika on 2013-12-02
> **runrickus said:**
> Regards[img]http://www.sherv.net/cm/emo/word/hello-wave-smiley-emoticon.gif[/img]

---

### Post by QDR06VV9 on 2013-12-03
> **zika said:**
> [IMG]http://www.sherv.net/cm/emo/word/hello-wave-smiley-emoticon.gif[/IMG]

Thank You.:D That is very kind. ;)

---

### Post by ventrical on 2013-12-04
> **runrickus said:**
> How am i yelling? merely suggesting as it has worked for me and others.
I have nothing but _respect_ for you and everyone here in U+1
Regards


You are not yelling. That was an exclamation mark of discovery and sharing.  :)

Thanks for sharing that.

Regards..

---

### Post by QDR06VV9 on 2013-12-05
I had noticed that trusty had not upgraded nvidia so i went in and changed my sources list discovered that xedgers was on trusty
so I changed that to "devel" and got updates!:) And also got nvidia-settings back +1.
Still have to change some css sheets because they get overwritten?:confused:
And to change the wallpapers I have to restart my session<Alt+F2> <r> then hit enter.
Cairo-Dock will lockup at times but hey this testing..:D
And of course Extras still not populated yet. All is good though.
If someone would be kind enough to list there source list I would be greatfull;)
Ricotz had suggested enabling with testing a saucy entry, also but I get errors something like expecting "devel" but got "trusty"

---

### Post by tista on 2013-12-13
Guys,

A couple of days ago, I've added gnome3-staging PPA on my trusty, and so I've experienced a weird thing "Vanishing mouse pointer" on Gnome-Flashback session.. :(

**[Machine]**
Dell Vostro A90 (famous as Mini9 or Inspiron910)

**[GPU]**
Mesa DRI Intel(R) 945GME x86/MMX/SSE2 (showed in glxinfo)

**[Base System]**
Trusty daily build states 'up-to-date' just now

**[PPA]**
ppa:gnome3-team/gnome3-staging

**[Details in case]**
Once logging into Gnome session (means gnome-shell), I've confirmed that the mouse pointer shows and cntrols normally, but then I go back to GDM, logging into Gnome-Flashback (with metacity) again, I've missed mouse pointer at all...
You know this machine have not any touch-screen device already.

Even though it works pretty good as pointing device only without seeing!! haha.. was it a Joke in 13th Friday!? :P

Anyway we could solve this weird issue with gsettings:
```
gsettings set org.gnome.settings-daemon.plugins.cursor active false
```

Yep I suppose gnome-setting-daemon 3.11.2-0ubuntu1~trusty1 might have some issue with this case, but I haven't track this down yet though...

If someone had similar situations, hope this help you guys.

Best Regards,
Tista

---

### Post by mc4man on 2013-12-13
> **tista said:**
> Guys,

A couple of days ago, I've added gnome3-staging PPA on my trusty, and so I've experienced a weird thing "Vanishing mouse pointer" on Gnome-Flashback session.. :(


currently about here
[https://bugs.freedesktop.org/show_bug.cgi?id=59644](https://bugs.freedesktop.org/show_bug.cgi?id=59644)
or more general - 
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1238410](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1238410)

There's a new xserver (core) in -proposed that I'm using though haven't checked to see if it's any better (haven't had a missing cursor of late

---

### Post by tista on 2013-12-14
@mc4man

Thanks for info! ;)

And I've chekced out the xserver version:
**ii  xserver-xorg-core                    2:1.14.5-1ubuntu1**
If so, we already had that patched xserver core. grrrr :(

Regards,
Tista

---

### Post by SurfaceUnits on 2014-01-20
Where can i find a link to gnome3-team information dispersal. They apparently just put gnome 3.10 in the [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) saucy repo and I have 309 updates from them. I didn't know they were going to move 13.10 to gnome 3.10. Thnx

---

