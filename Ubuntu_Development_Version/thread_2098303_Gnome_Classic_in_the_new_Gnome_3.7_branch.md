---
title: "Gnome Classic in the new Gnome 3.7 branch"
date: 2012-12-26
forum: Ubuntu Development Version
---

### Post by Harry33 on 2012-12-26
I have upgraded my RR setup with the new Gnome3.7 branch.
Here I use the Gnome3 Staging PPA.

Well after upgrading everything, I noticed that the session Gnome Classic (No effects) does not work anymore.
However the session Gnome Classic works just fine.

Of course I could not upgrade the packages gnome-panel, gnome-panel-data and libpanel-applet-4-0. So these are still v. 3.6.2. The apckages metacity, metacity-common and libmetacity-private0a are v. 2.34.13.

---

### Post by kansasnoob on 2012-12-26
> **Harry33 said:**
> I have upgraded my RR setup with the new Gnome3.7 branch.
Here I use the Gnome3 Staging PPA.

Well after upgrading everything, I noticed that the session Gnome Classic (No effects) does not work anymore.
However the session Gnome Classic works just fine.

Of course I could not upgrade the packages gnome-panel, gnome-panel-data and libpanel-applet-4-0. So these are still v. 3.6.2. The apckages metacity, metacity-common and libmetacity-private0a are v. 2.34.13.

Probably not surprising since they said metacity and the fallback session would be history in 3.8. Is 3.7 just a sort of transitional version between 3.6 and 3.8?

I'm not well versed in how Gnome handles their releases :(

---

### Post by grahammechanical on 2012-12-26
> Is 3.7 just a sort of transitional version between 3.6 and 3.8?

From here:

[https://live.gnome.org/ThreePointSeven]("https://live.gnome.org/ThreePointSeven")

> GNOME 3.7.x is an unstable development series intended for testing and hacking purposes. GNOME uses odd minor version numbers to indicate development status, so this unstable 3.7.x series will become the official 3.8 stable release.

Regards.

---

### Post by kansasnoob on 2012-12-27
I certainly don't have this all figured out but it looks like the new "classic mode" is actually going to be a "GNOME Legacy" session:

[http://blogs.gnome.org/mclasen/2012/12/05/gnome-3-7-what-is-happening-now/](http://blogs.gnome.org/mclasen/2012/12/05/gnome-3-7-what-is-happening-now/)

---

### Post by jbicha on 2012-12-27
GNOME Classic (No Effects) "works" here with the GNOME3 Staging PPA. Some caveats are:

[LIST=1]
[*] metacity, gnome-panel, and gnome-applets do not currently have a maintainer (indicator-session, the piece of code that enables indicators to work in GNOME Fallback, doesn't really have a maintainer either, which helps to explain why 11.10 didn't include it)
[*]Support code and workarounds been removed from gnome-settings-daemon and gnome-control-center. You can see the full list at the [master bug]("https://bugzilla.gnome.org/show_bug.cgi?id=682858"). This is mostly mitigated in Ubuntu since the default configuration includes the Ubuntu "indicator" status menus. The Ubuntu developers will make it a high priority to ensure that the status menus still work but since Ubuntu 13.04 will be sticking with GNOME 3.6 there isn't pressure for them to do that work now.
[*]gnome-settings-daemon and gnome-control-center have some regressions and brokenness because several Ubuntu patches haven't been ported to the new version yet
[/LIST]
 You can try out GNOME's current "GNOME Classic" mode now by installing gnome-shell-extensions from the GNOME3 Staging PPA and selecting GNOME  Classic from the login screen. (The previous GNOME Classic sessions have been renamed back to GNOME Fallback).

---

### Post by kansasnoob on 2012-12-28
When I try to install 'gnome-shell-extensions' I get this:

```
lance@lance-desktop:~$ sudo apt-get install gnome-shell-extensions
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gir1.2-gtop-2.0
The following NEW packages will be installed:
  gir1.2-gtop-2.0 gnome-shell-extensions
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 103 kB of archives.
After this operation, 987 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ raring/main gir1.2-gtop-2.0 i386 2.28.4-3 [15.8 kB]
Get:2 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main gnome-shell-extensions all 3.7.3-0ubuntu1 [87.0 kB]
Fetched 103 kB in 6s (15.4 kB/s)                                               
Selecting previously unselected package gir1.2-gtop-2.0.
(Reading database ... 153216 files and directories currently installed.)
Unpacking gir1.2-gtop-2.0 (from .../gir1.2-gtop-2.0_2.28.4-3_i386.deb) ...
Selecting previously unselected package gnome-shell-extensions.
Unpacking gnome-shell-extensions (from .../gnome-shell-extensions_3.7.3-0ubuntu1_all.deb) ...
[B][COLOR="Red"]dpkg: error processing /var/cache/apt/archives/gnome-shell-extensions_3.7.3-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/share/gnome-session/sessions/gnome-classic.session', which is also in package gnome-session-fallback 3.7.2-0ubuntu1~raring1
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-shell-extensions_3.7.3-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR][/B]
lance@lance-desktop:~$ 

```

That was easily resolved by purging 'gnome-session-fallback'. I got logged into the new classic session, just now poking around.

For some reason gdm is eating my lunch, I might try 'lightdm' for a while just as a work-around.

---

### Post by paul_in_london on 2012-12-28
You should just be able to do:

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/gnome-shell-extensions_3.7.3-0ubuntu1_all.deb
```

---

### Post by paul_in_london on 2012-12-28
I was too slow for your edit! :smile:

---

### Post by kansasnoob on 2012-12-28
> **paul_in_london said:**
> I was too slow for your edit! :smile:

Sorry about that :oops:

---

### Post by kansasnoob on 2012-12-28
I'm surprised at how light this runs :)

I've done quite a bit of cross-testing on this same hardware over the past few weeks and Unity is a true kludge now, but performance was acceptable in 12.04 so I'm blaming Compiz until I learn different. And Cinnamon's Muffin fork of Mutter is almost as bad, I've tried it both with Mint and Snowlinux.

But GNOME seems to have Mutter very well tamed so I think this new classic session could be a great alternative. I do wish that the Panel Settings extension was available for 3.7, but otherwise I think this is pretty great.

[ATTACH]229233[/ATTACH]

[ATTACH]229234[/ATTACH]

[ATTACH]229235[/ATTACH]

---

### Post by OluszDes on 2012-12-28
> **Harry33 said:**
> I have upgraded my RR setup with the new Gnome3.7 branch.
Here I use the Gnome3 Staging PPA.

Well after upgrading everything, I noticed that the session Gnome Classic (No effects) does not work anymore.
However the session Gnome Classic works just fine.

Of course I could not upgrade the packages gnome-panel, gnome-panel-data and libpanel-applet-4-0. So these are still v. 3.6.2. The apckages metacity, metacity-common and libmetacity-private0a are v. 2.34.13.

If you need the Gnome Classic (No effects) session, how about adding this file to /usr/share/xsessions

> [Desktop Entry]
Name=GNOME Classic (No effects)
Exec=gnome-session --session=gnome-fallback
TryExec=gnome-session
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-3.0

and this to /usr/share/gnome-session/sessions

> [GNOME Session]
Name=GNOME fallback (Safe Mode)
RequiredComponents=gnome-panel;gnome-settings-daemon;
RequiredProviders=windowmanager;
DefaultProvider-windowmanager=metacity
DefaultProvider-notifications=notify-osd
DesktopName=GNOME

if matacity is not around, change it to gnome-wm, and see what would happen. You have to log out and in to get at the session.

---

### Post by jbicha on 2012-12-28
> **kansasnoob said:**
> When I try to install 'gnome-shell-extensions' I get this:

```

[B][COLOR="Red"]dpkg: error processing /var/cache/apt/archives/gnome-shell-extensions_3.7.3-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/share/gnome-session/sessions/gnome-classic.session', which is also in package gnome-session-fallback 3.7.2-0ubuntu1~raring1
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-shell-extensions_3.7.3-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR][/B]
lance@lance-desktop:~$ 

```


Thanks. That should have been fixed earlier today by gnome-session 3.7.2-0ubuntu1~raring2. I fixed it in raring's 3.6 version before my previous post here but forgot that the staging PPA had a newer version that needed fixing too.

---

### Post by zika on 2012-12-29
Any idea how to start gnome-fallback from .Xsession (startx)?
Gnome-session-fallback does not work anymore after installing gnome-shell...
It works nicely from both gdm and lightdm...

---

### Post by kansasnoob on 2012-12-29
> **zika said:**
> Any idea how to start gnome-fallback from .Xsession (startx)?
Gnome-session-fallback does not work anymore after installing gnome-shell...

I think the fallback session is intentionally deprecated now. I sort of did a roadmap here:

[http://ubuntuforums.org/showpost.php?p=12382253&postcount=1](http://ubuntuforums.org/showpost.php?p=12382253&postcount=1)

But since then I've also learned that the new "classic" session may be called "GNOME Legacy":

[http://blogs.gnome.org/mclasen/2012/12/05/gnome-3-7-what-is-happening-now/](http://blogs.gnome.org/mclasen/2012/12/05/gnome-3-7-what-is-happening-now/)

After using it just a bit, and flip-fopping back and forth with Ubuntu-GNOME-Remix 12.10 to compare some things against extensions not yet available in GNOME 3.7 (particularly "Panel settings"), I truly think this new "legacy" mode may be the perfect solution :)

---

### Post by zika on 2012-12-29
> **kansasnoob said:**
> I think the fallback session is intentionally deprecated now. I sort of did a roadmap here:

[http://ubuntuforums.org/showpost.php?p=12382253&postcount=1](http://ubuntuforums.org/showpost.php?p=12382253&postcount=1)

But since then I've also learned that the new "classic" session may be called "GNOME Legacy":

[http://blogs.gnome.org/mclasen/2012/12/05/gnome-3-7-what-is-happening-now/](http://blogs.gnome.org/mclasen/2012/12/05/gnome-3-7-what-is-happening-now/)

After using it just a bit, and flip-fopping back and forth with Ubuntu-GNOME-Remix 12.10 to compare some things against extensions not yet available in GNOME 3.7 (particularly "Panel settings"), I truly think this new "legacy" mode may be the perfect solution :)I was not precise enough...
Fallback is working if I invoke it either from {light,}dm but I do not see a way of invoking it from .Xsession (startx) as I used to do before... Even though it might be in user mode... I'll see...
I am writting this from fallback session in lightdm... Nice...

---

### Post by kansasnoob on 2012-12-29
I'm using a pure Ubuntu-GNOME-Remix install via mini.iso:

[http://ubuntuforums.org/showpost.php?p=12421017&postcount=17](http://ubuntuforums.org/showpost.php?p=12421017&postcount=17)

So if you're using an actual Ubuntu installation I'm sure things will differ :)

---

### Post by Harry33 on 2012-12-29
> **zika said:**
> Any idea how to start gnome-fallback from .Xsession (startx)?
Gnome-session-fallback does not work anymore after installing gnome-shell...
It works nicely from both gdm and lightdm...

Same here, I use gnome-fallback session from GDM.
However, the session gnome-fallback (no effects) session does not work.
Anyway, as I do not need it, I'm not going to try to fix this.

---

### Post by zika on 2012-12-29
> **kansasnoob said:**
> I'm using a pure Ubuntu-GNOME-Remix install via mini.iso:

[http://ubuntuforums.org/showpost.php?p=12421017&postcount=17](http://ubuntuforums.org/showpost.php?p=12421017&postcount=17)

So if you're using an actual Ubuntu installation I'm sure things will differ :)I did not quite get what You meant...

---

### Post by zika on 2012-12-29
> **Harry33 said:**
> Same here, I use gnome-fallback session from GDM.
However, the session gnome-fallback (no effects) session does not work.
Anyway, as I do not need it, I'm not going to try to fix this.Here gnome-fallback(no effects) work... Just writting from it... LightDM is even a better choice...
Just I did not figure out how to make it work without DM, straight into X (startx)...
[img]http://www.fun.24sata.rs/resources/funImg/28-12-2012/33/300/10972-d0d7474c488e4c5426b301a501cd60c1.jpg[/img]

---

### Post by Harry33 on 2012-12-29
> **zika said:**
> Here gnome-fallback(no effects) work... Just writting from it... LightDM is even a better choice...
Just I did not figure out how to make it work without DM, straight into X (startx)...
[IMG]http://www.fun.24sata.rs/resources/funImg/28-12-2012/33/300/10972-d0d7474c488e4c5426b301a501cd60c1.jpg[/IMG]

Perhaps because I have a very minimal setup, I may have crippled it by removing something it needs. No problem anyway because gnome-fallback is OK.

BTW. Is that dog yours? What is the breed?

---

### Post by zika on 2012-12-29
> **Harry33 said:**
> Perhaps because I have a very minimal setup, I may have crippled it by removing something it needs. No problem anyway because gnome-fallback is OK.

BTW. Is that dog yours? What is the breed?No it's not mine... I would not mind... It depicts my frustration at the moment of writing that post... Serendipity brought me to that picture at that very moment...

Update&#8321;: I've made it...
```
exec /usr/bin/gnome-session --session=gnome-fallback
```in .Xsession
It even works with```
mutter --replace
```
Idea came from [http://ubuntuforums.org/showpost.php?p=12425870&postcount=11](http://ubuntuforums.org/showpost.php?p=12425870&postcount=11) ... Thank You @OlusZDes! ...

---

### Post by kansasnoob on 2012-12-29
I have two Ubuntu-GNOME-remix mini.iso installs running, one is plain-Jane, no PPA's added and I noticed this change in 'gnome-session' today:

> gnome-session (3.6.2-0ubuntu3) raring; urgency=low

  * debian/patches/50_ubuntu_sessions.patch, 52_xdg_current_desktop.patch,
    debian/gnome-session-fallback.install:
    - Rename "GNOME Classic" back to "GNOME Fallback" to not conflict with
      the GNOME Shell 3.8 classic mode

 -- Jeremy Bicha <jbicha@ubuntu.com>  Thu, 27 Dec 2012 18:45:22 -0500

Not a big deal but it would be nice to know what the intended final outcome is?

Will the new classic be Gnome classic, or Gnome legacy?

---

### Post by jbicha on 2012-12-29
As of GNOME 3.7, the new mode for GNOME Shell is called "GNOME Classic".  That name may change before 3.8 is final though.

---

### Post by kansasnoob on 2012-12-29
> **jbicha said:**
> As of GNOME 3.7, the new mode for GNOME Shell is called "GNOME Classic".  That name may change before 3.8 is final though.

Cool :)

I really have to say though that I'm finding Gnome shell to be much more intuitive than I'd ever imagined. I'd just not had time to really use it until you created this remix.

Since 12.04 is supported so long I'd hope to be able to create more Gnome shell (or even Unity) converts by the time 16.06 rolls around :guitar:

---

