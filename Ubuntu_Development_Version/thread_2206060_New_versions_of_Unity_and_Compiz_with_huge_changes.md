---
title: "New versions of Unity and Compiz with huge changes are now in proposed"
date: 2014-02-17
forum: Ubuntu Development Version
---

### Post by Mateusz Stachowski on 2014-02-17
These have all the things that landed in trunk so far in this cycle of development but developers still work on many things like High DPI support and Unity Lockscreen.

[https://launchpad.net/ubuntu/trusty/+source/unity/7.1.2+14.04.20140214.1-0ubuntu1](https://launchpad.net/ubuntu/trusty/+source/unity/7.1.2+14.04.20140214.1-0ubuntu1)

[https://launchpad.net/ubuntu/trusty/+source/compiz/1:0.9.11+14.04.20140214-0ubuntu1](https://launchpad.net/ubuntu/trusty/+source/compiz/1:0.9.11+14.04.20140214-0ubuntu1)

You will notice that there are also things that Sam Spilsbury been working on but it doesn't mean he is back contributing. Those things were originally worked on by him and know the current developers of Unity and Compiz made them applicable to the new codebase.

These will also bring up the new Unity decorations which should also resolve a long standing bug: [Panel should be right-clickable when window is maximised with global menu enabled]("https://bugs.launchpad.net/unity/+bug/1098419").

Also as you can see the right-click menus on decoration in Ambiance are black just like they should be from beginning.

[https://plus.google.com/108101042776723451522/posts/Zw4DdiKGhn4](https://plus.google.com/108101042776723451522/posts/Zw4DdiKGhn4)

---

### Post by Mateusz Stachowski on 2014-02-17
Update it looks like they have already being sponsored to main.

---

### Post by rrnbtter on 2014-02-17
Greetings, 
Very decent explanation of this update. Thanks!

---

### Post by mc4man on 2014-02-17
At least here they messed up gtk2 pretty good, ex. firefox, ccsm, the add attachment window here, ect

---

### Post by QDR06VV9 on 2014-02-17
Noticed that here also..

---

### Post by mc4man on 2014-02-17
I've also seeing some difficulty with l. click, doesn't always register on first attempt
(most noticeable in nautilus on folders

---

### Post by Mateusz Stachowski on 2014-02-17
> **mc4man said:**
> At least here they messed up gtk2 pretty good, ex. firefox, ccsm, the add attachment window here, ect

You need to install unity-settings-daemon and then after re-login it should be good.

---

### Post by Mateusz Stachowski on 2014-02-17
Also there will be another update to Unity which will restore gnome-settings-deamon support until unity-settings-deamon move from universe to main.

[https://launchpad.net/ubuntu/trusty/+source/unity/7.1.2+14.04.20140217-0ubuntu1](https://launchpad.net/ubuntu/trusty/+source/unity/7.1.2+14.04.20140217-0ubuntu1)

---

### Post by mc4man on 2014-02-17
> **Mateusz Stachowski said:**
> You need to install unity-settings-daemon and then after re-login it should be good.

That works...
Edit: fixed.. Now I have to see about getting rid of ctrl+alt+delete opening sys mon, my previous method isn't working
(can be user changed but like all compiz commands may not stick if not integrated..

---

### Post by Alan F on 2014-02-17
Window controls have moved from right to left, although the dconf setting still has them on the right.

Unity Tweak Tool will not run.

---

### Post by Mateusz Stachowski on 2014-02-17
> **mc4man said:**
> That works...
Now I have to see about getting rid of ctrl+alt+delete opening sys mon, my previous method isn't working
(can be user changed but like all compiz commands may not stick if not integrated..

I think that you should look in dconf-editor on this schema:

org > compiz > integrated

and then there are two keys command-21 '/usr/bin/gnome-system-monitor -p' and run-command 21 ['<Control><Alt>Delete'].

> **Alan F**

Window controls have moved from right to left, although the dconf setting still has them on the right.


Unity Tweak Tool will not run.

With new decorations you can't move the window controls and programs like unity-tweak-tool and ubuntu-tweak will probably need an update from developers of this programs.

---

### Post by Mateusz Stachowski on 2014-02-17
It appears that now when the unity-control-center is listing Unity and Compiz keyboard shortcuts you could enable the logout on Ctrl+Alt+Delete from system settings.

[https://bugs.launchpad.net/bugs/1271710](https://bugs.launchpad.net/bugs/1271710)

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/890747](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/890747)

> Admittedly, my solution was a bit lacking for a couple of reasons.

1. The new shortcut to bring up gnome-system-monitor -p was not present in System Settings->Keyboard->Shortcuts.
2. The old shortcut in Keyboard shortcuts to use Ctrl-Alt-Delete to Log out was still present.


This probably causes confusion for users and is kind of a bad design. So I'm going to fix this for at least Trusty.


I will make a new shortcut in Keyboard->Shortcuts that sets Ctrl-Alt-Del to open gnome-system-monitor -p. I will also set Log out to Disabled. This way, it is clear to the end user what is going on here and is also quite easy to set Ctrl-Alt-Delete back to Log out or something else entirely.


What I need to do is ask Design which heading they want the new shortcut to be under and what they want the wording to say.

---

### Post by mc4man on 2014-02-17
> **Mateusz Stachowski said:**
> It appears that now when the unity-control-center is listing Unity and Compiz keyboard shortcuts you could enable the logout on Ctrl+Alt+Delete from system settings.

[https://bugs.launchpad.net/bugs/1271710](https://bugs.launchpad.net/bugs/1271710)

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/890747](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/890747)

I see that there...
I've been doing something different, replacing that integrated command with one to run a script for window picker for window group.
(just a bit of laziness & killed 2 birds with one stone. 
Got it working again with compiz rebuild, not sure why it didn't 'take'  on 1st. attempt

---

### Post by ventrical on 2014-02-17
if you try and enable cube_gears and then disable it,  it will force you to Ctl+Alt+F1 if you are running a gnome-session-flashback(compiz).

Cube is very fast in unity but really slow in gnome-session-flashback.

---

### Post by ventrical on 2014-02-17
Windows Decorations enable wants to disable Unity Plugin.

---

### Post by Mateusz Stachowski on 2014-02-17
You can't enable the old decorations in Unity. That's why they were disabled.

---

### Post by xc3RnbFO8P on 2014-02-17
and the cube isn't working...

---

### Post by mc4man on 2014-02-17
> **Ringi said:**
> and the cube isn't working...

Works fine here, both in old install & a new one just put in.
Maybe - 
try latest unity build
install unity-settings-daemon
open ccsm & reset, sometimes when compiz/unity update things get unset

otherwise file bug (maybe some issue with your hardware?

---

### Post by xc3RnbFO8P on 2014-02-17
> **mc4man said:**
> Works fine here, both in old install & a new one just put in.
Maybe - 
try latest unity build
install **unity-settings-daemon**
open ccsm & reset, sometimes when compiz/unity update things get unset

otherwise file bug (maybe some issue with your hardware?

Thanks mc4man, solved :)

EDIT: ups this was Cairo Dock OpenGL

Unity didn't work so I tried to reset all in ccsm one by one and when I disable Skydome it worked again.

---

### Post by xc3RnbFO8P on 2014-02-17
I dont know if this is cause of my problem?

[[img]http://farm4.staticflickr.com/3717/12598709983_0e177d33ab_c.jpg[/img]](http://www.flickr.com/photos/96052779@N07/12598709983/)
[Screenshot from 2014-02-17 22:25:24](http://www.flickr.com/photos/96052779@N07/12598709983/) by [ringi_is](http://www.flickr.com/people/96052779@N07/), on Flickr

and now this

[[img]http://farm6.staticflickr.com/5514/12599144863_1d3a9c0fb3_c.jpg[/img]](http://www.flickr.com/photos/96052779@N07/12599144863/)
[Screenshot from 2014-02-17 23:09:35](http://www.flickr.com/photos/96052779@N07/12599144863/) by [ringi_is](http://www.flickr.com/people/96052779@N07/), on Flickr

---

### Post by Doug S on 2014-02-17
All I'll say on this thread, which might be the wrong thread, I don't know, is that my 14.04 Ubuntu Desktop VM is pretty broken right now. I have been updating it faithfully every day, and it was fine yesterday. From my perspective, the interesting thing here is that it seems broken in a somewhat similar way, yet also different, to my GNOME log in option which [has been broken since]("https://bugs.launchpad.net/ubuntu-gnome/+bug/1273276") about January 17th.
I've had several issues this cycle, and have learned not to get to excited for a day or two, as often the issues get sorted out.

Edit: My Unity Desktop is unusable right now, but My Gnome Desktop is usable, after I apply the workaround of using xrandr to set up the display manually.

---

### Post by monkeybrain20122 on 2014-02-17
Does edge flipping finally work without a hitch?

---

### Post by Mateusz Stachowski on 2014-02-17
Another new thing that Unity will get is ability to filter the windows by name in the spread!

[https://code.launchpad.net/~3v1n0/unity/spread-filter/+merge/206802](https://code.launchpad.net/~3v1n0/unity/spread-filter/+merge/206802)

---

### Post by mc4man on 2014-02-17
> **monkeybrain20122 said:**
> Does edge flipping finally work without a hitch?

Well since I put a new  compiz build in earlier I've left auto sort enabled, we'll see if it lasts over the course of a day or so...
(otherwise all seems pretty good, scroll on desktop bindings/xserver remain officially broken but that can be worked around.

---

### Post by mc4man on 2014-02-17
> **Ringi said:**
>  when I disable Skydome it worked again.
While I don't use, mainly just rotate thru 'scroll on desktop', it appears skydome is quite broken, causes all sorts of artifacts  here if enabled.

---

### Post by Hazzabin on 2014-02-17
> **mc4man said:**
> While I don't use, mainly just rotate thru 'scroll on desktop', it appears skydome is quite broken, causes all sorts of artifacts  here if enabled.


exact same here too, I get an 'inner' cube inside 4-6 other outer cubes

---

### Post by PJs Ronin on 2014-02-17
System borked here too (unity borked, xfce working fine-ish).

However, when I run System Settings I get this.   Now I'm all for convergence, but my desktop is not a phone and shouldn't, imo, have phone things embedded.

[ATTACH=CONFIG]250453[/ATTACH]

---

### Post by Hazzabin on 2014-02-17
I'm convinced now more than ever before, the devs are left-eyed and have to be left-handed to boot

cap that off with a wild weekend and manage to be able to screw up 14.04 Unity

I love challenges but but   :guitar:     I'm off to play some music

Sorry guys thats my "Rant" for the day

---

### Post by Cavsfan on 2014-02-19
My one complaint is that Window Decoration gets unchecked every time I logout/restart. I have Emerald window decorator installed.

[ATTACH=CONFIG]250480[/ATTACH]

This is on Gnome Flashback (with Compiz). The cube works great and spins fast.
I love the addition of Wizard to the eye candy though! :)

[[IMG]http://en.zimagez.com/miniature/screenshotfrom2014-02-19100551.png[/IMG]]("http://en.zimagez.com/zimage/screenshotfrom2014-02-19100551.php")

---

### Post by Doug S on 2014-02-19
I am still stuck with unity shell not working. Upon my first attempt to open system settings, compiz crashes. Via ssh, which is the only way I can communicate with the machine:```
doug@doug-desktop:/var/log$ [COLOR=#ff0000]tail -4 kern.log[/COLOR]
Feb 19 07:32:27 doug-desktop kernel: [    8.915743] random: nonblocking pool is initialized
Feb 19 07:34:12 doug-desktop kernel: [  113.232640] type=1006 audit(1392824052.300:86): pid=2618 uid=0 old auid=4294967295 new auid=1000 old ses=4294967295 new ses=1 res=1
Feb 19 07:36:30 doug-desktop kernel: [  251.157931] compiz[2355]: segfault at ffffffff88246d53 ip 00007ff3b7946c24 sp 00007fff7a19d1f0 error 5 in libc-2.18.so[7ff3b78ba000+1bc000]
Feb 19 07:36:32 doug-desktop kernel: [  253.019663] compiz[2763]: segfault at 7ff0ba897ff8 ip 00007ff17998e640 sp 00007fffe198b1b8 error 4 in libc-2.18.so[7ff1798fc000+1bc000]
``````
doug@doug-desktop:/var/log$ [COLOR=#ff0000]tail -17 syslog[/COLOR]
Feb 19 07:33:04 doug-desktop udisksd[2457]: Error probing device: Error sending ATA command IDENTIFY PACKET DEVICE to /dev/sr0: ATA command failed: error=0x20 count=0x00 status=0x50 (g-io-error-quark, 0)
Feb 19 07:33:04 doug-desktop dbus[526]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Feb 19 07:33:04 doug-desktop udisksd[2457]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Feb 19 07:34:12 doug-desktop kernel: [  113.232640] type=1006 audit(1392824052.300:86): pid=2618 uid=0 old auid=4294967295 new auid=1000 old ses=4294967295 new ses=1 res=1
Feb 19 07:34:20 doug-desktop dnsmasq[1208]: reading /etc/resolv.conf
Feb 19 07:34:20 doug-desktop dnsmasq[1208]: using nameserver 127.0.1.1#53
Feb 19 07:34:20 doug-desktop dnsmasq[1208]: using local addresses only for unqualified names
Feb 19 07:36:30 doug-desktop kernel: [  251.157931] compiz[2355]: segfault at ffffffff88246d53 ip 00007ff3b7946c24 sp 00007fff7a19d1f0 error 5 in libc-2.18.so[7ff3b78ba000+1bc000]
Feb 19 07:36:30 doug-desktop gnome-session[2139]: WARNING: Application 'compiz.desktop' killed by signal 11
Feb 19 07:36:30 doug-desktop gnome-session[2139]: WARNING: App 'compiz.desktop' respawning too quickly
Feb 19 07:36:30 doug-desktop gnome-session[2139]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Feb 19 07:36:32 doug-desktop kernel: [  253.019663] compiz[2763]: segfault at 7ff0ba897ff8 ip 00007ff17998e640 sp 00007fffe198b1b8 error 4 in libc-2.18.so[7ff1798fc000+1bc000]
Feb 19 07:36:32 doug-desktop gnome-session[2139]: WARNING: App 'compiz.desktop' respawning too quickly
Feb 19 07:36:32 doug-desktop gnome-session[2139]: WARNING: Application 'compiz.desktop' killed by signal 11
Feb 19 07:36:32 doug-desktop gnome-session[2139]: WARNING: App 'compiz.desktop' respawning too quickly
```

---

### Post by monkeybrain20122 on 2014-02-19
> **Cavsfan said:**
> 

This is on Gnome Flashback (with Compiz). The cube works great and spins fast.
I love the addition of Wizard to the eye candy though! :)


Is 3d windows still broken?

---

### Post by xc3RnbFO8P on 2014-02-19
> **monkeybrain20122 said:**
> Is 3d windows still broken?

Still broken here...

---

### Post by Cavsfan on 2014-02-20
> **monkeybrain20122 said:**
> Is 3d windows still broken?

> **Ringi said:**
> Still broken here...

Yes, still broken here. I hadn't been trying that option but when I just did it is too bad for me to screen print.

Also after I checked Windows Decorator, which I have to do each login, I opened CCSM and it immediately unchecked Windows Decorator.
I had to check it again.

---

### Post by mc4man on 2014-02-23
'borderless' existed for a few weeks back in 11.04 dev, reverted mainly because of unity-2d.
Unlike previously there is no user side means to go with 0px borders with the change to unity deco so have made a pitch to return it.
(myself would obviously want, sure others may not agree but as per usual it's only up to "Design"

---

### Post by 23dornot23d on 2014-02-24
Compiz runs nice - as long as its not got any decorations or windows

Short video [http://youtu.be/mGv807MsUOE](http://youtu.be/mGv807MsUOE)

---

### Post by xc3RnbFO8P on 2014-02-25
> **23dornot23d said:**
> Compiz runs nice - as long as its not got any decorations or windows

Short video [http://youtu.be/mGv807MsUOE](http://youtu.be/mGv807MsUOE)

This is not Unity?
There is no problem with Compiz in Cairo Dock OpenGL.

---

### Post by 23dornot23d on 2014-02-25
I never said it was unity ....... it is in xcfe4 ..... as a compiz --replace

Every other Desktop it either crashes or shoots all 8 cores to max.

I was trying to help - the main cause of problems with it seemed to show up as the border decorations .......

as without those enabled things tended to calm down somewhat ...........

But if you can explain how to get it running properly - I would be interested.

---

### Post by xc3RnbFO8P on 2014-02-25
> **23dornot23d said:**
> I never said it was unity ....... it is in xcfe4 ..... as a compiz --replace

Every other Desktop it either crashes or shoots all 8 cores to max.

I was trying to help - the main cause of problems with it seemed to show up as the border decorations .......

as without those enabled things tended to calm down somewhat ...........

But if you can explain how to get it running properly - I would be interested.

I don't have solution, maybe it has something to do with Transparent in Unity?

---

### Post by 23dornot23d on 2014-02-25
I can run conky and cairo-dock - or docky ...... the effects work ok including transparency

Take a look at this video .... the things get really screwed up once windows are added to it.

[http://youtu.be/H3XTe431EHc](http://youtu.be/H3XTe431EHc)

Maybe compiz is not meant to work anywhere else nowadays ........ whats your take on this ?

I have got around the decoration problem by compiling emerald ........ taken from some
easy instructions given here and providing very nice results.

[http://askubuntu.com/questions/287056/how-to-compile-install-emerald-window-manager-in-ubuntu-13-04-64bit](http://askubuntu.com/questions/287056/how-to-compile-install-emerald-window-manager-in-ubuntu-13-04-64bit)

Also have created another video in LXDE ....... still the same problems with the cube -

[http://youtu.be/NbGhx6IS4SU](http://youtu.be/NbGhx6IS4SU)

but much smoother with the windows and going around the cube ........ transparency works perfectly
as you will see demonstrated ......... but I still need to know how to set compiz up ..........

or will I have to compile that too .......... 

There must be a version that is up to date and working properly somewhere.

Will have a search soon ......... if nothing turns up on here .........

If anyone can think of some ways of getting new options or ensuring all dependencies are full filled - post a comment
can only help move forward with this - unless no one else has problems with it ........... must admit upgrading is never
as simple as a fresh install ..........

---

### Post by xc3RnbFO8P on 2014-02-25
> **23dornot23d said:**
> I can run conky and cairo-dock - or docky ...... the effects work ok including transparency

Take a look at this video .... the things get really screwed up once windows are added to it.

[http://youtu.be/H3XTe431EHc](http://youtu.be/H3XTe431EHc)

Maybe compiz is not meant to work anywhere else nowadays ........ whats your take on this ?

It make your desktop more alive, according to my friends, they don't see the purpose in it, its a toy, but I like it :)

Here is a video record with my webcam (this computer is useless when it comes to video recording)
[http://youtu.be/hBymLNpYZe0](http://youtu.be/hBymLNpYZe0)

---

### Post by 23dornot23d on 2014-02-26
That looks good - but I did notice it still glitches on the windows that sit on top of the background ........

_____________________________________________________________________________________

I had another go with mine ........ am getting there ..... now have transparency and end caps plus the background.

Still moving forward - little by little ........... [http://youtu.be/HIlNBLt_FVo](http://youtu.be/HIlNBLt_FVo)


A better example is here now have added conky to it .... [http://youtu.be/c7VBytSNlWA](http://youtu.be/c7VBytSNlWA)

---

