---
title: "Unity 5.0 Staging PPA. Testing"
date: 2012-01-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by lucazade on 2012-01-07
There is a new PPA for Unity 2D/3D to test out latest bzr code.
At the moment it is just for Oneiric but I presume it will be soon available also for Precise because that code will be present in final release.

> This archive contains the latest builds generated from trunk, that have passed the unit tests, but didn't pass the user acceptance (autopilot) tests yet.
Unless you are a developer and know what you do here, you should probably use the "unity-team/ppa" instead.

Personally I'm looking forward to some fixes for the 2D version like the [long delay on session logout]("https://code.launchpad.net/~aacid/unity-2d/addSmallDelayOnQuit_812104") ,
missing window buttons on maximized LibreOffice,
[resizable/dynamic Launcher size]("https://code.launchpad.net/~fboucault/unity-2d/launcher_dynamic_size") and
the improved window switcher.

It is worth trying it and report bugs and experiences to launchpad :)

---

### Post by t1497f35 on 2012-01-07
Hm.. there's no link to the actual Unity ppa in your post, and the one I found through google contains unity which is like 36 weeks old.
[https://launchpad.net/~unity/+archive/ppa?field.series_filter=oneiric]("https://launchpad.net/%7Eunity/+archive/ppa?field.series_filter=oneiric")

and yes, I don't know what the improved window switcher will be like, but the current one is really bad (for me at least).

---

### Post by JMB74 on 2012-01-07
[https://launchpad.net/~unity-team/+archive/staging](https://launchpad.net/~unity-team/+archive/staging)

---

### Post by zika on 2012-01-07
> **t1497f35 said:**
> Hm.. there's no link to the actual Unity ppa in your post, and the one I found through google contains unity which is like 36 weeks old.
[https://launchpad.net/~unity/+archive/ppa?field.series_filter=oneiric]("https://launchpad.net/%7Eunity/+archive/ppa?field.series_filter=oneiric")

and yes, I don't know what the improved window switcher will be like, but the current one is really bad (for me at least).
[https://launchpad.net/~unity-team/+archive/staging](https://launchpad.net/~unity-team/+archive/staging) ?

---

### Post by lucazade on 2012-01-07
ops.. yes.. that is the correct link :)

thanks for pointing that out

---

### Post by mc4man on 2012-01-07
That can be a tricky ppa to use, best for an install you don't care about.
Atm there is likely a mismatch in libnux abi version which is an = for unity*, would be off by one.

Don't see much improved there for unity-2d over the daily ppa, many things wrong are still wrong, no sign of launcher icon size.
(- the issue with windows over launcher turned out to be a missing patch in metacity, still no fix released but at least 'known'.
Do wonder how much real use testing of unity-2d goes on, for almost 5 months the metacity deal existed without dev notice..

See a few new options in the unity plugin, nothing too spectacular - screen, highlighted & menu fade in ect.
The quicklists are somewhat transparent, if intended it's more annoying than nice. (new wording - "Unlock from launcher"

---

### Post by lucazade on 2012-01-07
@mc4man

true, it is a tricky ppa atm.. hope to see something good in the next months otherwise I'll continue to use the 'good' old gnome-fallback.

unity-2d really needs more love and probably more devs.. we'll see :)

---

### Post by mc4man on 2012-01-07
Anyway - for those wanting to try there was just an update to unity source which should match up with nux & allow installing unity & unity-2d, ect.

Edit - while not all that useful the ppa can be added to a precise install though atm you'd be responsible for providing your own nautilus packages.
(initially add the ppa, upgrade at least libunity/libunity-dev, build & install nautilus packages, upgrade the rest, ect.

Does fix some of the current unity issues with precise's nux packages, good to see they are fixed if  not as yet released..

---

### Post by mc4man on 2012-01-08
An alternate to the ppa for trying the current unity trunk is laid out here in the accepted reply, works well & easy to revert when & if desired

[http://askubuntu.com/questions/28470/how-do-i-build-unity-from-source](http://askubuntu.com/questions/28470/how-do-i-build-unity-from-source)

---

### Post by MacUntu on 2012-01-08
> **mc4man said:**
> An alternate to the ppa for trying the current unity trunk is laid out here in the accepted reply, works well & easy to revert when & if desired

[http://askubuntu.com/questions/28470/how-do-i-build-unity-from-source](http://askubuntu.com/questions/28470/how-do-i-build-unity-from-source)

+1

If you like your edge even more bleeding, try one of those merge proposals instead of lp:unity &#8594; [https://code.launchpad.net/~unity-team/unity/trunk/+activereviews](https://code.launchpad.net/~unity-team/unity/trunk/+activereviews) 

Happy debugging of screwed-up systems! :P

---

### Post by mc4man on 2012-01-10
The other advantage of a bzr build & local install is it allows testing/using the current state of nux/unity trunk & if one creates an add. user account, standard or admin, the current state of them in PP. 

(Atm the trunk is far better than 1.X/0.4.24 though obviously that could change and or somewhat  catch up.

---

### Post by lucazade on 2012-01-10
looking better at unity 2d there are some good additions:
- launcher is now trasparent also if metacity compositor is not enabled (good for netbooks)
- dash has window buttons in top left corner (like the 3d version)
- workspace switcher is faster and better defined

there are still some bugs here and there and some missing functions if compared with 3d version but nothing too big.

---

### Post by fjgaude on 2012-01-10
Wow,thank you guys for the work with Poulsbo... so close to being fully fixed.

I'll start testing 12.04 with Alpha2, 32-bit, on my Dell netbook.

---

### Post by lucazade on 2012-01-11
I've found an interesting todo inside source code of trunk unity2d..
it looks like launcher and dash are going to merge in a single component called 'shell'.. I believe unity2d will get a boost in development now that is used also in UbuntuTv.

> To obtain a full upstreamable merge of dash and launcher that mantains the full
feature set currently available we need to take care of the following tasks (ordered by severity):

= High =

* Shell window should be input-shaped so that the part that belongs to neither dash nor launcher does not receive input
  - This should also work correctly with the dash bottom-right corner which is already input shaped.
* The panel now has window buttons to close, minimize, maximize the dash. Make these work with the shell and remove the
  bottom-right maximize button we have now.
* Add back this Launcher feature: when alt+f1 is pressed and launcher already has focus, the shell window should be deactivated
  so the WM will give focus back to whatever window had it before.
* Put back Super+D to show desktop. Also make sure the behaviour from r.808 from trunk is implemented (display launcher when
  desktop is showing).

= Medium =

* Merge review 803 from lp:unity-2d ([launcher] Do not hide the launcher immediately after removing an icon. Fixes: [https://bugs.launchpad.net/bugs/884410](https://bugs.launchpad.net/bugs/884410). Reviewed by Tiago Salem Herrmann.)
* Add proper package transition from unity-2d-launcher+unity-2d-places to unity-2d-shell in debian/rules
* Put back in support for RTL
* Add cmd line option to choose which root QML file to load
* Put back support for struts and enable struts automatically when hide-mode is always visible
  (the dconf setting was already removed by partially merging revision 804 from trunk)
* Put back in support for 4-finger slide gesture (in a way that's not tied to the panel)
  - Put back support for launcher manualSliding
  - Implement locking in place when the slide goes over 240 units (check in unity-3d what should happen in the various hide modes) 
* We are doing IPC between components in the same process in various cases. This brings back
  bad memories and should be removed.

= Minor =

* Remove the LauncherClient as it's now just an empty class
* Tests were removed, do we need to put them back ?
* Move updateDashModeDependingOnScreenGeometry to QML
* Fix .bzrignore

---

### Post by lucazade on 2012-01-11
> **fjgaude said:**
> Wow,thank you guys for the work with Poulsbo... so close to being fully fixed.

I'll start testing 12.04 with Alpha2, 32-bit, on my Dell netbook.

If we are lucky Precise will support poulsbo natively.. crossing finger.
When all the bits will be ready I'll open a new thread about it :)

---

### Post by dino99 on 2012-01-11
Sadly the main work about Poulsbo is done into kernel 3.3, hopes PP will get it.

---

### Post by lucazade on 2012-01-11
@dino99
psb_gfx is already inside 3.2 and working good.. there are just a couple of bugs to iron out (blacklist vt.handoff=7 and remove 'poulsbo' stub module from ubu kernel) and fortunately are wip in launchpad :)
so it should be a matter of weeks... obviously no 3d or vaapi hd playback, but this is another story :)
(intel update emgd drivers pleeeease!)

---

### Post by fjgaude on 2012-01-11
> **lucazade said:**
> If we are lucky Precise will support poulsbo natively.. crossing finger.
When all the bits will be ready I'll open a new thread about it :)

We are ready to test it...

---

### Post by lucazade on 2012-01-11
new unity 5.0 ppa (both 2d and 3d) for precise:
[https://launchpad.net/~unity-team/+archive/ppa](https://launchpad.net/~unity-team/+archive/ppa)

[http://blog.didrocks.fr/post/Releasing-a-precise-Unity-5.0-to-Ubuntu-12.04](http://blog.didrocks.fr/post/Releasing-a-precise-Unity-5.0-to-Ubuntu-12.04)

only for the brave :)

---

### Post by zika on 2012-01-11
> **lucazade said:**
> new unity 5.0 ppa (both 2d and 3d) for precise:
[https://launchpad.net/~unity-team/+archive/ppa](https://launchpad.net/~unity-team/+archive/ppa)

[http://blog.didrocks.fr/post/Releasing-a-precise-Unity-5.0-to-Ubuntu-12.04](http://blog.didrocks.fr/post/Releasing-a-precise-Unity-5.0-to-Ubuntu-12.04)

only for the brave :)Thank You very much! For the first time after some time my Unity is working and it is working just fine... No need to fall-back to Unity2D... For an addicted user of OpenBox and FluxBox this is an interesting excursion...

---

### Post by 1roxtar on 2012-01-12
**UNITY 5.0 READY FOR TESTING**

[http://www.omgubuntu.co.uk/2012/01/unity-5-0-ready-for-testing/]("http://www.omgubuntu.co.uk/2012/01/unity-5-0-ready-for-testing/")

Has anyone upgraded and begun testing it yet?  I did and like the article poster says, "Unity 5.0 feels far more responsive than previous iterations; opening windows, transitions etc all seem &#8216;snappy&#8217;."  From what I gathered from the article is that most of the newer stuff is mainly under the hood with one visible change being the Ubuntu Button Dash Launcher has a new Quicklist for all your lenses (which I really like, personally).  I would like to see also see the Home Folder launcher get a Quicklist too.  What do you think?

*Please.  If you don't like Unity, take your rant somewhere else.  I would like to see feedback from users who are actually testing this newer version of Unity.

---

### Post by zika on 2012-01-12
[http://ubuntuforums.org/showthread.php?t=1905631](http://ubuntuforums.org/showthread.php?t=1905631)

Yes, that made me come back to Unity after quite some time (OpnBox, FluxBox)...

To Moderators: these two threads should be joined, if You wish... Thank You...

---

### Post by ubiquitin.jf on 2012-01-12
Custom colour selection? YE GODS, FINALLY!

---

### Post by kaldor on 2012-01-12
I can't seem to get this to work. I added the PPA, ran an *apt-get update*, and this is the result when trying to install:

```

$ sudo apt-get install unity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 unity : Depends: libunity-core-5.0-5 (>= 4.14.2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by Pilot6 on 2012-01-12
I compiled Unity from trunk. It works much better for me, because there is no bug with 2 X screens, when desktop randomly moved up and windows started to open with titles under the panel.
But there is a new bug. Dash is too small or contents are too big.
It happens that 'ALL' buttons in filtering are outside the border. And you have to maximize dash to cancel filtering.

---

### Post by PaulW2U on 2012-01-12
> **kaldor said:**
> I can't seem to get this to work. I added the PPA, ran an *apt-get update*

I installed it about an hour ago from the PPA. I have a number of files held back from upgrading and I did have to remove libunity-core-4.0-4(?) before I could get unity to install. 

I'm using it now, seems to work fine. I've run some of the tests and submitted the results. One or two keyboard short-cuts will have to be checked again but in the main a nice upgrade.

---

### Post by KdotJ on 2012-01-12
From the website:
> After upgrading to Unity 5.0 you will find a ‘Unity Testing Tool’ on your Launcher. If have 30 mins to spare you should run this to help provide feedback on Unity to the developers.

That is great, good to see that you can give direct feedback :)

I'm going to give this a whirl...

---

### Post by mc4man on 2012-01-12
You'll find some new additions in the plugin settings > experimental inc. setting how long the panel menu is displayed when opening an app, 0 > 10 sec range, a show desktop launcher item & in dconf you can choose to not display downloadable apps in the Dash apps menu, ect

---

### Post by philinux on 2012-01-12
Threads merged.

---

### Post by kaldor on 2012-01-12
> **PaulW2U said:**
> I installed it about an hour ago from the PPA. I have a number of files held back from upgrading and I did have to remove libunity-core-4.0-4(?) before I could get unity to install. 

I'm using it now, seems to work fine. I've run some of the tests and submitted the results. One or two keyboard short-cuts will have to be checked again but in the main a nice upgrade.

Amazed that I never thought of that. Thanks a bunch, worked a charm :)

---

### Post by shizz on 2012-01-12
Is this specific to precise alpha or is it a good idea to test it in 11.10?

---

### Post by kaldor on 2012-01-12
I've been using this for the last hour or so now. 

I'm disappointed that some people have stated that there are some performance improvements, or that the UI feels snappier in some cases. Apart from the extra features, I see no difference. I'm still suffering greatly from choppy window movement, animations, and scrolling.

Edit: I take that statement back- I forgot disable the Sync to Vblank option in CCSM (OpenGL) and now it's nearly perfect. The UI *does* feel much, much snappier than before. Now, if only my audio problems sort themselves out :)

---

### Post by PaulW2U on 2012-01-12
> **kaldor said:**
> The UI *does* feel much, much snappier than before. 

Glad to hear it. I've just put one application in each of the four workspaces and switching between them is very fast even on this old PC of mine.

---

### Post by kaldor on 2012-01-12
Just another small update.

After a while, it seems that window dragging begins to become slightly sluggish again. While still much better than before, it's a pretty weird issue.

---

### Post by mc4man on 2012-01-12
> **kaldor said:**
> Just another small update.

After a while, it seems that window dragging begins to become slightly sluggish again. While still much better than before, it's a pretty weird issue.

Been seeing the same lately, something seems to cause a bit of a slowdown after a while.
I generally can tell when opening a terminal, normally the term opens right away with the prompt. When things go a bit south the term opens right away but the prompt shows up after 1/2 to 1 sec.

Some of the supposed performance & display improvements are for the most part only when using open source video drivers & as far as horizontal tearing the fix is only on the desktop, doesn't extend to video playback where if one has tearing there are other factors.

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/861061](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/861061)
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/880707](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/880707)

---

### Post by effenberg0x0 on 2012-01-12
I've been using daily builds of unity for a while. I generally compile compiz, nux, unity from git/bzr every two days or so. My changes are small UI, with no real impact on usability or performance. 

It's good that every one is on the same page now. I agree to everyone that says Unity feels snappier, however, what I've been seeing for more than a month is that, after a couple hours, windows start to get sluggish when you move them, like if there was a leak of some sort. gnome-terminal, tilda, firefox, thunderbird are the examples in which I have certainly seen this effect.

---

### Post by kaldor on 2012-01-13
> **effenberg0x0 said:**
> 
It's good that every one is on the same page now. I agree to everyone that says Unity feels snappier, however, what I've been seeing for more than a month is that, after a couple hours, windows start to get sluggish when you move them, like if there was a leak of some sort. gnome-terminal, tilda, firefox, thunderbird are the examples in which I have certainly seen this effect.

It's not nearly that long for me. Give it 15 minutes of use and window lag begins.

---

### Post by effenberg0x0 on 2012-01-13
> **kaldor said:**
> It's not nearly that long for me. Give it 15 minutes of use and window lag begins.

Kaldor, do you see increased/increasing memory or CPU usage? What has been stopping me from reporting this is that although there *seems* to be some sort of leak, I cant detect any increase in mem/cpu usage. I have no significant errors/warnings in log files. Launching compiz/unity from a terminal, to try to get a glimpse of it's messages, also reveals no useful info. Yet, It feels like the PC is dying.

Example: Launching a terminal takes less than a second here, it's immediate. Moving the window like crazy side to side is entirely fluid, with no artifacts or delays. After 2 or 3 hours, even minimising it takes 5 to 10 seconds.

EDIT: Tested with NVIDIA 285.03, 285.05.09, 290.03, 290.06, 290.10 (all x86_64)

---

### Post by MacUntu on 2012-01-13
Leaks? What leaks?

[IMG]http://img.xrmb2.net/images/266804.png[/IMG]

---

### Post by philinux on 2012-01-13
> **shizz said:**
> Is this specific to precise alpha or is it a good idea to test it in 11.10?

[http://www.omgubuntu.co.uk/2012/01/unity-5-0-ready-for-testing/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2012/01/unity-5-0-ready-for-testing/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

Not a good idea to test out anything in your main stable machine. Unless you like breakage and can fix it.

---

### Post by ubiquitin.jf on 2012-01-13
Ooh, it's just appeared in the repos. Shame the dependencies are broken.

---

### Post by EgoGratis on 2012-01-13
> Unless you like breakage and can fix it.

It is a great learning experience. :)

---

### Post by kaldor on 2012-01-13
> **effenberg0x0 said:**
> Kaldor, do you see increased/increasing memory or CPU usage? What has been stopping me from reporting this is that although there *seems* to be some sort of leak, I cant detect any increase in mem/cpu usage. I have no significant errors/warnings in log files. Launching compiz/unity from a terminal, to try to get a glimpse of it's messages, also reveals no useful info. Yet, It feels like the PC is dying.

Example: Launching a terminal takes less than a second here, it's immediate. Moving the window like crazy side to side is entirely fluid, with no artifacts or delays. After 2 or 3 hours, even minimising it takes 5 to 10 seconds.

EDIT: Tested with NVIDIA 285.03, 285.05.09, 290.03, 290.06, 290.10 (all x86_64)

Yep. Exact same scenario here. Everything appears normal in the System Monitor application as well as in *top*. I am using the open source Radeon driver- no blobs or PPAs for graphics at all.

So yes, everything is working as it should, yet it feels like the performance of the windows is slowing down.

I originally thought the same as you (leak) but found no evidence of that. Glad to see someone else is having this issue, and with totally different hardware.

---

### Post by effenberg0x0 on 2012-01-13
> **kaldor said:**
> Yep. Exact same scenario here. Everything appears normal in the System Monitor application as well as in *top*. I am using the open source Radeon driver- no blobs or PPAs for graphics at all.

So yes, everything is working as it should, yet it feels like the performance of the windows is slowing down.

I originally thought the same as you (leak) but found no evidence of that. Glad to see someone else is having this issue, and with totally different hardware.

It bothers me that I am not seeing many people complain about it. If it's something that is caused by some very particular aspect of our hw/sw infrastructure, that doesn't affect a lot of people, we might get stuck with it for ages, as developers will have no viable info to debug it.

If you are into this sort of thing and have *a lot* of patience and some free time, you can try to find it. I'm struggling with the lack of time part of it. It's not too hard to profile C code, there are many available tools, etc. Unfortunately I was born without the set of neurons necessary to use OOP (working on it), but profiling C++ can't be that different. If we can profile to see what function(s) seem to be growing on execution time and/or memory, we can go deeper by setting a couple breakpoints in them and step through it (which will be the time consuming part of it, as the desktop will freeze at every breakpoint and, unless we use remote gdb, it will be hell) while looking at memory state. I think that, in theory, it would pinpoint where the problem is.

---

### Post by cariboo on 2012-01-13
Isn't the problem reported in bug #[lpbug]888039[/lpbug]?

So far it affects 22 people.

---

### Post by kaldor on 2012-01-14
> **effenberg0x0 said:**
> It bothers me that I am not seeing many people complain about it. If it's something that is caused by some very particular aspect of our hw/sw infrastructure, that doesn't affect a lot of people, we might get stuck with it for ages, as developers will have no viable info to debug it.

If you are into this sort of thing and have *a lot* of patience and some free time, you can try to find it. I'm struggling with the lack of time part of it. It's not too hard to profile C code, there are many available tools, etc. Unfortunately I was born without the set of neurons necessary to use OOP (working on it), but profiling C++ can't be that different. If we can profile to see what function(s) seem to be growing on execution time and/or memory, we can go deeper by setting a couple breakpoints in them and step through it (which will be the time consuming part of it, as the desktop will freeze at every breakpoint and, unless we use remote gdb, it will be hell) while looking at memory state. I think that, in theory, it would pinpoint where the problem is.

It is quite concerning, yes. It's an incredibly noticeable and annoying bug for me on one of my computers. My laptop which uses an NVIDIA card (as always, default OSS driver) suffers no such issue. My main PC is where I notice it. So yes, it seems like it might only affect some people; I hope this bug won't be pushed under the rug because of that.

I'm by no means a programmer, so I don't have the mindset or skills required to be able to pinpoint this issue (which is quite frustrating). I'm currently learning C# at college as a requirement, and it's not coming very easily for me :)

I'm going to keep taking a look at this throughout newer daily builds. Since I'll likely end up using Ubuntu 12.04 for a long time I want to make sure issues on my hardware will be gone by release. If there are any discoveries on this which would require testing, I'm willing to do that as long as it's not *too* complicated. 



> **cariboo907 said:**
> Isn't the problem reported in bug #[lpbug]888039[/lpbug]?

So far it affects 22 people.

Not quite. With me, it seems that even with the performance degradation the memory/cpu usage seems to stay normal. In that report, it looks like people are noticing spikes when dragging the windows.

---

### Post by effenberg0x0 on 2012-01-14
> **cariboo907 said:**
> Isn't the problem reported in bug #[lpbug]888039[/lpbug]?

So far it affects 22 people.

Yes, sorry, I expressed myself badly. It's not that not enough people reported it, it's just that no report is really targeted / direct / useful. If you read #888039, you'll see it's a "loose bug". It's the typical "6-months-to-a-year-or-more" report. A guy thinks it's nvidia related, the other thinks its fglrx, "last updates fixed it for me", "oh no they didn't", maybe an out of sync issue between monitor and composite rate, the weather in Jupiter, etc. Just wild guesses, no real info. 

In my experience, this type of bug is dangerous. It can go on until a blessed developer somehow manages to have a mysterious click in his mind and associate other error to this behaviour, or magically find something in one specific block of code within a gazillion other LOC, etc. In some rare cases a user decides to really work and provide some valuable debugging info. Aside from that, it's likely to not be fixed / forgotten between so many other urgent demands. 

It's different from bug reports like "The enter key doesn't work", "When I click on X, Y happens, but it should be Z", etc. It's a more subjective one.

---

### Post by kaldor on 2012-01-14
Just a note here.

I was using Precise today (all updates applied- everything newest) and took note to how long it took for the lag to set in. The first sign of lag, and I ran the "uptime" command. 31 minutes after bootup and the lag has started up.

Nothing suspicious in the System Monitor, and *top* shows the same.

I have 8 gb of RAM and an 8 core CPU; hardware is not a problem.

---

### Post by VinDSL on 2012-01-14
> **kaldor said:**
> I've been using this for the last hour or so now. 

I'm disappointed that some people have stated that there are some performance improvements, or that the UI feels snappier in some cases.[...]
Just started playing with it, too...

H-U-G-E difference in looks n' performance on this machine!

Here's a screenie...


[INDENT]**Ubuntu 12.04 alpha [COLOR="DarkOrange"] / [/COLOR] Conky 1.8.1 [COLOR="DarkOrange"] / [/COLOR] ACYL  [COLOR="DarkOrange"] / [/COLOR] Unity 5.0 [COLOR="DarkOrange"] / [/COLOR] nVidia 290.10 [COLOR="DarkOrange"] / [/COLOR] Liquorix 3.1 kernel**  [SIZE="1"]**( Click image to expand )**[/SIZE]

[[IMG]http://vindsl.com/images/vindsl-desktop-14-jan-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-14-jan-2012-2.png")[/INDENT]


Um... where did the "love handles" go (in CCSM)?!?!?  LoL!  :D

---

### Post by VinDSL on 2012-01-14
> **kaldor said:**
> I have 8 gb of RAM and an 8 core CPU; hardware is not a problem.
Aha!  There's the source of your disappointment!

You need to get yourself a "doorstop computer", like the rest of us.  :D

---

### Post by Henkdroid on 2012-01-14
Don't know if this is the right to put this but when I put unity 5.0 on mu oneiric install the terminal windows and notifications were really strange, sort-of washed out. The problem seemed to be linked to the panel transparency but that makes no sense.

---

### Post by VinDSL on 2012-01-14
> **Henkdroid said:**
> I put unity 5.0 on mu oneiric install the terminal windows and notifications were really strange, sort-of washed out.
Same here.

I noticed there are a LOT of new settings in CCSM.

I'm gonna play around with them next, and see what happens...

---

### Post by balloons on 2012-01-16
Just wanted to stop by the thread and say thanks to everyone who participated in this. The unity team plans on having several more of these, following a 2-3 week cadence and generally occurring right before the alpha/beta releases. Your testing makes not only the future 12.04 release better, but eases the potential problems for anyone running the alpha version and trying to work on/test other things.

+1

---

### Post by lucazade on 2012-01-16
so... next stop unity 5.2.x

[https://launchpad.net/unity/+milestone/5.2.0](https://launchpad.net/unity/+milestone/5.2.0)
[https://launchpad.net/unity-2d/+milestone/5.2.1](https://launchpad.net/unity-2d/+milestone/5.2.1)

:) happy testing

---

### Post by mc4man on 2012-01-16
> **lucazade said:**
> so... next stop unity 5.2.x

[https://launchpad.net/unity/+milestone/5.2.0](https://launchpad.net/unity/+milestone/5.2.0)
[https://launchpad.net/unity-2d/+milestone/5.2.1](https://launchpad.net/unity-2d/+milestone/5.2.1)

:) happy testing
Interesting to see what bugs are being workrd on.
One in partucular is too bad (that is from my perspective), it's been going on & off since natty, guess this time it will happen
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/689733](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/689733)

(basically the window spread from a l. click on launcher icon will now ignore any of that app's windows on other workspaces & only pull from current Ws.

 Pretty dumb idea

---

### Post by Pilot6 on 2012-01-18
I compiled Unity 5.0 from trunk yesterday. Now it works perfectly. The bug with cut contents of dash has been fixed.

---

### Post by Jdogzz on 2012-01-25
I read something about having problems with libnux and this PPA. Right now I can't install Unity-3d (package named unity) because of this error:

> The following packages have unmet dependencies:
 unity : Depends: libnux-abiversion-20111214

Has anyone been able to fix this besides waiting until it fixes itself? I have my system fully upgraded (both upgrade and dist-upgrade) and trying to install the unmet dependency results in it saying:


> Package libnux-abiversion-20111214 is a virtual package provided by:
  libnux-2.0-0 2.0.0-0ubuntu2 [Not candidate version]


---

### Post by mc4man on 2012-01-25
> **Jdogzz said:**
> I read something about having problems with libnux and this PPA. Right now I can't install Unity-3d (package named unity) because of this error:



Has anyone been able to fix this besides waiting until it fixes itself? I have my system fully upgraded (both upgrade and dist-upgrade) and trying to install the unmet dependency results in it saying:
Nux comes before unity so you'll need to wait for a new unity build after a new nux. (which won't be too long, building right now.

---

### Post by Jdogzz on 2012-01-26
Do you have a link where I can see the progress of the nux versions and when they're building?

---

### Post by psypher on 2012-01-31
Any update on this, still unable to install and fix Unity 3d and unity 2d is pretty much completely broken at this time. Unable to open the dash at all, just opens and crashes

---

### Post by jfernyhough on 2012-01-31
> **Henkdroid said:**
> Don't know if this is the right to put this but when I put unity 5.0 on mu oneiric install the terminal windows and notifications were really strange, sort-of washed out. The problem seemed to be linked to the panel transparency but that makes no sense.

Same here. Weirdly, upgrading to the 5.1 test version fixed this for me.
[https://launchpad.net/~unity-team/+archive/hud](https://launchpad.net/~unity-team/+archive/hud)

> **VinDSL said:**
> Same here.

I noticed there are a LOT of new settings in CCSM.

I'm gonna play around with them next, and see what happens...

No difference for me no matter the settings I chose. It's definitely Unity, though. Compiz by itself was (is) fine.

> **Jdogzz said:**
> I read something about having problems with  libnux and this PPA. Right now I can't install Unity-3d (package named  unity) because of this error:
Has anyone been able to fix this besides waiting until it fixes itself? I  have my system fully upgraded (both upgrade and dist-upgrade) and  trying to install the unmet dependency results in it saying:Have you checked '$ apt-cache policy libnux-2.0.0' ?

> **Jdogzz said:**
> Do you have a link where I can see the progress of the nux versions and when they're building?
[https://launchpad.net/ubuntu/+source/nux](https://launchpad.net/ubuntu/+source/nux)
(Google: launchpad libnux-2.0.0)

---

### Post by t1497f35 on 2012-01-31
Anyone knows what's the big difference between the latest [nux]("https://launchpad.net/ubuntu/+source/nux") 1.x and the newer 2.x ?

---

### Post by go7Ul1ai on 2012-01-31
Okay so I've just updated to 5.2.0 and can't really notice many improvements. Clicking the BFB just takes you to recently running applications.

I have however noticed a bit of lag when moving windows around, also my dual-monitor setup isn't running as intended with the latest update. I now have a launcher of both screens, maybe this is how it is meant to be intended??

---

### Post by jsevi83 on 2012-01-31
I've been using ppa:unity-team/staging in Oneric and it's working great, but today I noticed most of the packages are gone. Do you plan to keep Oneric updated until the final release of Precise, or is this ppa becoming "Precise only"?

---

### Post by balloons on 2012-01-31
> **lee.jarratt said:**
> Okay so I've just updated to 5.2.0 and can't really notice many improvements. Clicking the BFB just takes you to recently running applications.

I have however noticed a bit of lag when moving windows around, also my dual-monitor setup isn't running as intended with the latest update. I now have a launcher of both screens, maybe this is how it is meant to be intended??

I'm going to open a new thread on Unity 5.2 with some updates about what to expect and the new tests to run :-)

---

### Post by go7Ul1ai on 2012-01-31
> **guitara said:**
> I'm going to open a new thread on Unity 5.2 with some updates about what to expect and the new tests to run :-)

Brilliant, cheers :-)

---

