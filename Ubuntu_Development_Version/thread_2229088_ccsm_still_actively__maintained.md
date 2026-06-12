---
title: "ccsm still actively  maintained"
date: 2014-06-11
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-06-11
From the several and frequent updates I have received for ccsm and plugins (plus compiz core) it looks like compiz and add-ons are not going away any time soon which is in contrary to the debates a few development cycles back where some would have ccsm obsoleted. This can only beg the question if  ccsm will be in the convergence scheme of things as time rolls on.

One of the major reasons why it is important to have ccsm maintained on the desktop form factor is because it is a selling point for Ubuntu to resellers who are running dead copies of Vista and 7 on perfectly good hardware. I had the opportunity to perform a demonstration for a large , local charity concern which are killing all these good machines with Vista installs. Running a live session and enabling the 'workspaces' in Unity panel was the catch all point  to then followup and point out Ubuntu's other attributes while keeping short attention spans focused. This was done  on a side by side terminal with another machine with Vista which was almost impossible to get any internet function at all with IE.

*note to moderator(s)*

Since this is topical to Utopic I ask to allow to have this thread stand here (as was done with Jorge Castro's thread about ccsm a few cycles ago).  I  just find it very interesting from a testing point of view that ccsm is all of a sudden getting a lot of attention.

Regards..


```
Get:110 http://archive.ubuntu.com/ubuntu/ utopic/universe compizconfig-settings-manager all 1:0.9.11+14.10.20140606-0ubuntu2 [575 kB]

```

---

### Post by Mateusz Stachowski on 2014-06-11
Unity 7 and therefore Compiz will be the default desktop in Ubuntu 14.10 and most likely in future releases. 

That is because Ubuntu developers decided to make a new flavour of Ubuntu with Unity 8 and Mir. They made that because those projects need a lot of testing and work on making it desktop friendly and future complete. In the meantime all the users that want to get the latest Ubuntu with new kernel and graphics stack and all the other packages and don't won't to be forced on using the experimental stuff can get exactly that with Utopic.

Also there are now [Ubuntu Desktop Next]("http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/") images available for testing with Unity 8 and Mir. There was a UDS session about that preview image. Check the news on [Web Upd8]("http://www.webupd8.org/2014/06/ubuntu-desktop-next-unity8-1410-utopic.html") which has links to those things and to the blueprint.

---

### Post by ventrical on 2014-06-11
> **Mateusz Stachowski said:**
> Unity 7 and therefore Compiz will be the default desktop in Ubuntu 14.10 and most likely in future releases. 

That is because Ubuntu developers decided to make a new flavour of Ubuntu with Unity 8 and Mir. They made that because those projects need a lot of testing and work on making it desktop friendly and future complete. In the meantime all the users that want to get the latest Ubuntu with new kernel and graphics stack and all the other packages and don't won't to be forced on using the experimental stuff can get exactly that with Utopic.

Also there are now [Ubuntu Desktop Next]("http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/") images available for testing with Unity 8 and Mir. There was a UDS session about that preview image. Check the news on [Web Upd8]("http://www.webupd8.org/2014/06/ubuntu-desktop-next-unity8-1410-utopic.html") which has links to those things and to the blueprint.

:) .. took about 15 minutes of tech difficulties to get to the unity8 preview session.  but I captured the spirit of it.

It's good to know that they decided not to scrap ccsm.



thnx

---

### Post by Alan F on 2014-06-11
> **ventrical said:**
> :) .. took about 15 minutes of tech difficulties to get to the unity8 preview session.  but I captured the spirit of it.

With the Ubuntu Desktop Next .iso I get only as far as the login screen then met with message "Failed to start session"

This happens both on the Live CD using User Name 'ubuntu-desktop-next' with blank password and also the entered user name/password on the installed version.

Any idea how to get past this?

Thanks

Edit - Just seen the comments on the WebUpd8 site. This is a common problem, the .iso is duff. Don't waste your time.

---

### Post by Cavsfan on 2014-06-11
I am glad ccsm and compiz are being developed too. I've been seeing lots of updates. It is a major selling point for Ubuntu and it doesn't take very much to make Vista look bad. It does that by itself. :p

I guess you could say I really only test the Gnome Flashback (with compiz) fork (or whatever you would call it) and I like the way it works with all the bells and whistles compiz brings to the picture.

---

### Post by ventrical on 2014-06-11
> **Alan F said:**
> With the Ubuntu Desktop Next .iso I get only as far as the login screen then met with message "Failed to start session"

This happens both on the Live CD using User Name 'ubuntu-desktop-next' with blank password and also the entered user name/password on the installed version.

Any idea how to get past this?

Thanks

Edit - Just seen the comments on the WebUpd8 site. This is a common problem, the .iso is duff. Don't waste your time.

Just seen this message after downloading 1GB of usless filespace  -> Not a COM32R Image:...

edit:

My mistake... one has to hit the Tab key to get a verbose install menu.. live , live- install etc..

;ie

```


boot: live


```

  I am installing now.

  The username and password method does not work on live-usb.

---

### Post by cariboo on 2014-06-12
Are you guys sure that ccsm/compiz are both still in development, and not just in bug fixing mode? I really can't see the devs adding new features, if they will both be going away in the forseeable future.

---

### Post by mc4man on 2014-06-12
All of the current updates for unity & compiz in 14.10 so far have been bug fixes.
( hopefully they make it to 14.04 thru SRU's/point releases 

> **Mateusz Stachowski said:**
> Unity 7 and therefore Compiz will be the default desktop in Ubuntu 14.10 and most likely in future releases. 


This sorta implies no converged Desktop release at some point, where did you get that impression from?

---

### Post by ventrical on 2014-06-12
> **cariboo907 said:**
> Are you guys sure that ccsm/compiz are both still in development, and not just in bug fixing mode? I really can't see the devs adding new features, if they will both be going away in the forseeable future.

Then why even waste the time to render bugfixes to mostly all of the compiz modules and depends? It doesn't make sense.

---

### Post by ventrical on 2014-06-12
According to some wikis, compiz is still be actively developed by a small team.

Here is next.

[https://code.launchpad.net/compiz](https://code.launchpad.net/compiz)


[URL="https://launchpad.net/compiz/0.9.12"]https://launchpad.net/compiz/0.9.12  
[/URL]

---

### Post by Mateusz Stachowski on 2014-06-12
> **mc4man said:**
> All of the current updates for unity & compiz in 14.10 so far have been bug fixes.
( hopefully they make it to 14.04 thru SRU's/point releases 



This sorta implies no converged Desktop release at some point, where did you get that impression from?

The first SRU for Compiz in 14.04 is just around the corner.

[https://code.launchpad.net/~townsend/compiz/0.9.11.1/+merge/222856](https://code.launchpad.net/~townsend/compiz/0.9.11.1/+merge/222856)

And yes Compiz is more in bug fix mode than active development. That said they have fix for a long standing and very important bugs in [0.9.12.0]("https://launchpad.net/compiz/+milestone/0.9.12.0") release.

[#607796]("https://bugs.launchpad.net/bugs/607796")	Launcher, Window management - Dragging and holding a selection over an entry in the Launcher should spread out windows belonging to that application

[#727904]("https://bugs.launchpad.net/bugs/727904")	Launcher, Window management - Switching between spreads when dragging a file over the Launcher is broken

I didn't meant that there won't be any release of Ubuntu with Unity 8 and Mir as default. I meant that 14.10 won't get these as default and possibly even 15.04. The developers will push Unity 8 and Mir as default when it will be reasonably usable on desktop.

You know that in its current state unity doesn't handle windowing so programs can be only launched as if they are in tablet mode and besides that Unity 8 on Mir doesn't even start or work without crashing on most PCs.

When I was trying out Unity 8 desktop session on Mir in Trusty I was getting crashes on Nouveau and when I opened a [bug]("https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1298914") report the developer responded with:

> Adding a Mir task, I'm not even sure if it's meant to work on nouveau...

Now when I tried the same on Utopic it was a little bit better and the crash happened latter than in Trusty but Unity 8 flickered and had other display issues (the names of the programs didn't display past the first letter).

---

### Post by ventrical on 2014-06-12
> **Mateusz Stachowski said:**
> The first SRU for Compiz in 14.04 is just around the corner.

[https://code.launchpad.net/~townsend/compiz/0.9.11.1/+merge/222856](https://code.launchpad.net/~townsend/compiz/0.9.11.1/+merge/222856)

And yes Compiz is more in bug fix mode than active development. That said they have fix for a long standing and very important bugs in [0.9.12.0]("https://launchpad.net/compiz/+milestone/0.9.12.0") release.

[#607796]("https://bugs.launchpad.net/bugs/607796")    Launcher, Window management - Dragging and holding a selection over an entry in the Launcher should spread out windows belonging to that application

[#727904]("https://bugs.launchpad.net/bugs/727904")    Launcher, Window management - Switching between spreads when dragging a file over the Launcher is broken

I didn't meant that there won't be any release of Ubuntu with Unity 8 and Mir as default. I meant that 14.10 won't get these as default and possibly even 15.04. The developers will push Unity 8 and Mir as default when it will be reasonably usable on desktop.

You know that in its current state unity doesn't handle windowing so programs can be only launched as if they are in tablet mode and besides that Unity 8 on Mir doesn't even start or work without crashing on most PCs.

When I was trying out Unity 8 desktop session on Mir in Trusty I was getting crashes on Nouveau and when I opened a [bug]("https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1298914") report the developer responded with:



Now when I tried the same on Utopic it was a little bit better and the crash happened latter than in Trusty but Unity 8 flickered and had other display issues (the names of the programs didn't display past the first letter).


Then it looks to be possible that Unity8 with Mir may be a flavour all it's own. That's not a bad idea. It could save a lot of headaches and keep compiz in the fold somehow with other flavours.

Regards..

---

### Post by mc4man on 2014-06-12
> **ventrical said:**
> Then it looks to be possible that Unity8 with Mir may be a flavour all it's own.

I'd be inclined to view that 'flavor' as Ubuntu
There does seem to be a willingness to add features as long as a bug report is attached, 1 ex.
[https://code.launchpad.net/~dcolascione/compiz/compiz/+merge/219112](https://code.launchpad.net/~dcolascione/compiz/compiz/+merge/219112)

---

### Post by ventrical on 2014-06-12
> **mc4man said:**
> I'd be inclined to view that 'flavor' as Ubuntu
There does seem to be a willingness to add features as long as a bug report is attached, 1 ex.
[https://code.launchpad.net/~dcolascione/compiz/compiz/+merge/219112](https://code.launchpad.net/~dcolascione/compiz/compiz/+merge/219112)


If that is the case then , what would the standard Unity desktop be? Unity-fallback? with-compiz/with xorg? I know that Trusty is pretty well locked with compiz for another 5 years of support .etc..so are  you saying the interim development cycles can kiss compiz goodbye ? :) lol

---

### Post by grahammechanical on 2014-06-12
According to this UOS session convergence will not be complete by the release of 14.10 so there is no point in putting convergence on the 14.10 roadmap. As far as I can understand things one of the motivations for having a Ubuntu-desktop-next ISO image is to avoid wrecking the 14.10 code and preventing it becoming a stable release.

[http://summit.ubuntu.com/uos-1406/meeting/22290/utopic-ue-unity8-mir-roadmap/](http://summit.ubuntu.com/uos-1406/meeting/22290/utopic-ue-unity8-mir-roadmap/)

There is a lot of work to do and the present focus is on bringing Ubuntu phones/tablets to RTM status. That is Ready To Manufacture/Market. It will be a point in the development of Ubuntu phones/tablets that means it is of suitable quality for Ubuntu OEM customers to install on their mobile devices. Sometime in September is the target date. Which brings it out of step with the desktop release pattern. And that is the reason for this session.

[http://summit.ubuntu.com/uos-1406/meeting/22310/development-1406-rtm-archive/](http://summit.ubuntu.com/uos-1406/meeting/22310/development-1406-rtm-archive/)

There will have to be configuration options for Unity 8 on the desktop. That will be expected by many users. These utilities have yet to be built. I think I saw something about it in either of those two sessions or in this session:

[http://summit.ubuntu.com/uos-1406/meeting/22283/utopic-ue-unity-api-roadmap/](http://summit.ubuntu.com/uos-1406/meeting/22283/utopic-ue-unity-api-roadmap/)

It was stated that one of the risks/challenges that comes with this push to bring Ubuntu phones/tablets to RTM status is that Ubuntu Unity 8 desktop gets neglected a little bit (my words not those of the presenter) and that will disappoint many of us, no doubt.

A question regarding CCSM? What does CCSM need to do that it at present cannot do? If CCSM is already sufficiently at an advanced stage of development then bug fixes, etc., may be all that is needed during the life of 14.04. Actually, the time period is less than five years because once 14.04 gets all its intended point releases support for the rest of the period is usually little more than security fixes and not improvements. If a user wants improvements then after two years they must install 16.04.

Will 15.04 be running on X and unity 7 or on Mir and unity 8? That is at present one of the known unknowns.

Regards.

---

### Post by mc4man on 2014-06-12
From a user perspective of those wanting unity+compiz then the only value of the short lived interim releases is bug fixes/improvements that can be applied to 14.04. 
The only other possible scenario where interim releases are of value (to these users) is if Ubuntu cannot produce a usable Desktop install of unity8 by 16.04
- & 'usable' may prove to be subjective, for ex. windows8 in whatever that default view is called is usable on my laptop but not to me so I use the desktop view  (or whatever it's called.

---

### Post by ventrical on 2014-06-12
> **grahammechanical said:**
> According to this UOS session convergence will not be complete by the release of 14.10 so there is no point in putting convergence on the 14.10 roadmap. As far as I can understand things one of the motivations for having a Ubuntu-desktop-next ISO image is to avoid wrecking the 14.10 code and preventing it becoming a stable release.
Regards.

  Yes, I believe I had mentioned this in another discussion of sorts or that several of us had touched on this point (don't know exactly which topic heading). It is perfectly logical. 

 I also want to thank you again for all of your other input into this matter with compiz/mir/xorg/unity8 and convergence. I see now that compiz and unity8 will not co-exist with each other. However, during my install of unity-next I did install compiz so as to work with gnome-session-flashback (compiz) desktop session and Unity8+mir is not affected by it's presence so, at least in these new , fresh stages of this development, there has been some divergence where the two are not conflicting with each other. So I surmised incorrectly when stating that compiz(ccsm) is actively being developed. (It was a little side note that someone had left that led me to believe that it was being actively developed and I erroneously assumed that it would converge or slip-stream into Mir.)

  It is good news however, that bugfixes are being committed actively for the duration of the Trusty cycle and the interim cycles until who knows when, at that point where unity8(n)+mir will become the new 'ubuntu'. At least those of us with hardware on the verge of obsolescence can still actively participate in beta testing Canonical/Ubuntu products. Perhaps xubuntu and lubuntu would consolidate to commit on standard xorg into the future and older machines can work with that while providing possibilities that compiz can be part of that graphical genre'.

Ad Opus Dilligenter.

Regards..

---

### Post by ventrical on 2014-06-12
> **mc4man said:**
> From a user perspective of those wanting unity+compiz then the only value of the short lived interim releases is bug fixes/improvements that can be applied to 14.04. 
The only other possible scenario where interim releases are of value (to these users) is if Ubuntu cannot produce a usable Desktop install of unity8 by 16.04
- & 'usable' may prove to be subjective, for ex. windows8 in whatever that default view is called is usable on my laptop but not to me so I use the desktop view  (or whatever it's called.


Thanks again mac4man.  I mis-spoke, somewhat, by using the word 'developed'.

I'll edit that out.

Regards..

---

### Post by mc4man on 2014-06-12
I won't say no dev at all, that branch merge proposal I linked is dev, not a bug fix. Just can't see Ubuntu (Canonical ) spending any effort on while they still believe they can offer a 'converged' product that people will use on their desktop installs.

(- atm converged means nothing here as I can't get an ubuntu phone or tablet & of  the 2 tablets I have, -   the nexus7 could take ubuntu, but  I have no intention of doing so, at least not until the battery is on it's far down downside.

Whether there is any life for compiz once it's out from the heavy foot of the unityshell plugin, no clue..

---

### Post by bregma2 on 2014-06-14
> **grahammechanical said:**
> 
Will 15.04 be running on X and unity 7 or on Mir and unity 8? That is at present one of the known unknowns.
The current plan is that Ubuntu 15.04 will be running Unity 7 by default.  Ubuntu 15.10 will run Unity 8 by default.  Canonical learned lessons from when Unity was brutally made the default before it was fully ready, and 6 months months will not be enough to get the sort of quality desktop Ubuntu users expect.  I say 6 months, because serious work on the desktop experience of Uniy 8 will not start until after the 14.10 release, since design work is focused on the mobile experiences first.

Unity 8 needs to be made the default on 15.10 to shake out all the quirks prior to the 16.04 LTS release.  Of course, plans can change to meet realities.

Although Unity 7 will be the default shipped for 14.10 and 15.04, Unity 8 will still be available as a preview for ongoing development and evaluation.  Just install the unity8-desktop-session-mir package from the archives and choose the Unity 8 session from the LightDM login screen.  It's much like the Gnome fallback session in that respect.  Think of it as a Unity fallforward session.

Compiz, and CCSM, will continue to be maintaned, actively, for the next two cycles.  No new features, just maintenance.  I don't know what the plans are after that, but it's Free software and if people are interested in maintaining it, there it is.  If no one is interested in maintaining it, so it goes.

---

### Post by mc4man on 2014-06-18
Taking a look at the current 14.04 SRU landings,  both unity & compiz will be getting what's in 14.10 currently. Later SRU's will likely continue that.
(- which makes sense to me as who cares if unity7/compiz  are bug fixed/improved in the upcoming 9 month releases if not for the benefit of 14.04.

---

### Post by philinux on 2014-06-24
A lot of effects are gone. Including the only one I really like "wobbly windows".

Moving windows is jerky without it. With it dead smooth.

---

### Post by mc4man on 2014-06-24
> **philinux said:**
> A lot of effects are gone. Including the only one I really like "wobbly windows".

Moving windows is jerky without it. With it dead smooth.
It's still shown here & works if enabled.
(- many other plugins don't work & likely never will, I believe a side effect of enabling GLES support in compiz which now is unnecessary with unity (8) ultimately dumping compiz

---

### Post by philinux on 2014-06-24
Under effects its not there for me

---

### Post by Cavsfan on 2014-06-24
That is odd. Wobbly windows works fine for me. 
I have Emerald windows decorator installed and it works although it is not compiz or maybe it is as it is started from CCSM at bootup.

[ATTACH=CONFIG]254214[/ATTACH]

The Wizard effect works well too.

---

### Post by mc4man on 2014-06-24
> **philinux said:**
> Under effects its not there for me
Do you have the compiz-plugins package installed (not default installed

---

### Post by ventrical on 2014-06-25
Wobbly works well here.  No Cube Gears, Windows 3D not! What helped me is that I unticked Desktop Cube/Appearance/Skydome/Skydome and /Animate Skydome. so now I can use Cube Deformation etc... Also .. reducing no. of Desttops to only 2 gives a nice flippity/floppity effect but multiple desktops still rotate and fade to transparent. etc..

---

### Post by Cavsfan on 2014-06-25
> **ventrical said:**
> Wobbly works well here.  No Cube Gears, Windows 3D not! What helped me is that I unticked Desktop Cube/Appearance/Skydome/Skydome and /Animate Skydome. so now I can use Cube Deformation etc... Also .. reducing no. of Desttops to only 2 gives a nice flippity/floppity effect but multiple desktops still rotate and fade to transparent. etc..

I still have 4 desktops and it rotates for as long as I hold down the keys. It will spin forever. I still have Desktop Cube/Appearance/Skydome just not animated. Cube Deformation also works here too.

---

### Post by ventrical on 2014-06-25
> **Cavsfan said:**
> I still have 4 desktops and it rotates for as long as I hold down the keys. It will spin forever. I still have Desktop Cube/Appearance/Skydome just not animated. Cube Deformation also works here too.



Rain effects work.
Expo works.
Widget Layer works.
Annotate (one of my favorites) works.
Splash works.
Benchmark works.
Screenshot works(whoops .. a small problem there .. it gets carfunkeled after a minute or so and locks up.. but will restore if you wait a minute or 2.)
Resize info will cause lockup if you maximize window. (workaround .. lock ccsm to unity panel then you can quit from panel without reboot).

Enable Show Repaint works but is useless as far as I am concerned.:)lol
Ring Switcher now works without a conflict in bindings to Unity Dash from <super key> It appears that it self conflict resolves the issue with a  couple second delay if you just hold down the super key.

Shift Switcher also works and conflict resolves with ignore.

Show mouse works.


All in all .. a lot of functions still work.

---

### Post by philinux on 2014-06-27
> **mc4man said:**
> Do you have the compiz-plugins package installed (not default installed

That package must have got removed somehow. I suspect PEBKAC.  Did it used to be called compiz-plugins-extra?
Or else I mistook the compiz-plugins-default for it.

Sorted now.

---

### Post by ventrical on 2014-06-27
plugin-extras me thinks..

---

### Post by Mateusz Stachowski on 2014-06-27
> **ventrical said:**
> plugin-extras me thinks..

compiz-plugins-extra is a transitional dummy package since Raring (13.04) and the extra plugins are in compiz-plugins package.

[http://packages.ubuntu.com/search?suite=all&section=all&arch=any&keywords=compiz-plugins-extra&searchon=names](http://packages.ubuntu.com/search?suite=all&section=all&arch=any&keywords=compiz-plugins-extra&searchon=names)

As for Compiz still actively maintained news looks like someone ports gtk-window-decorator the one used previously before the introduction of Unity decorations from GTK+ 2 to GTK+ 3.

---

