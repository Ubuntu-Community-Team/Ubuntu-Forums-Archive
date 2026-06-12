---
title: "Unity 5.6 Testing -- the hud has come to unity 2d"
date: 2012-02-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by balloons on 2012-02-29
Another point release from the unity folks. Here's what's new:

[LIST]
[*]A lot of bug fixes, especially in areas surrounding the HUD!
[*]Unity-2d now includes HUD.
[*]Compiz fixes -- including this awesome performance increase by Daniel [https://bugs.launchpad.net/compiz-core/+bug/940139](https://bugs.launchpad.net/compiz-core/+bug/940139)
[*]Keybinding shortcut changes -- there was noise about switching the keybindings for switching workspace ones and moving windows. This has been reverted to the previous values again
[/LIST]

Install the unity team ppa as usual, run thru the tests and report back.. Let me know how this one "feels" for you. I'm trying it now, too early to tell :-)

[http://www.theorangenotebook.com/2012/02/unity-56-whats-new-and-call-for-testing.html](http://www.theorangenotebook.com/2012/02/unity-56-whats-new-and-call-for-testing.html)

---

### Post by jfernyhough on 2012-02-29
Nice, I'm installing just for the Compiz fixes. I like the idea of a 48% reduction in Compiz CPU use.

---

### Post by skewty on 2012-02-29
Anyone know when LIM is coming to Unity?

[http://www.webupd8.org/2012/02/new-locally-integrated-menubar-might.html]("http://www.webupd8.org/2012/02/new-locally-integrated-menubar-might.html")


Anyone know if the unity ppa will provide Unity 5.6 to ubuntu 11.10?  

I need a stable system for work but unity in 11.10 doesn't cut it for my needs.

---

### Post by jbicha on 2012-02-29
You can't run the new Unity on 11.10.

---

### Post by rg4w on 2012-02-29
> **skewty said:**
> Anyone know when LIM is coming to Unity?

[http://www.webupd8.org/2012/02/new-locally-integrated-menubar-might.html](http://www.webupd8.org/2012/02/new-locally-integrated-menubar-might.html)
Is it April 1 already? ;)

Seriously, first they conceal menus from the user, then they make them much more physically difficult to use by turning them all into hierarchical menus.

Who's doing the usability testing over there?

---

### Post by alphacrucis2 on 2012-02-29
This version is brilliant so far!

---

### Post by quequotion on 2012-03-01
This is in the normal unity team PPA?

Were these changes already in the staging PPA before?

Last night I had to purge everything from the unity team staging ppa.

Right click menus of all kinds were crashing compiz.

***UPDATE***

Both versions (regular PPA and staging PPA) have this issue.

The problem is with the "Shift switcher" plugin.
Disabling this plugin works around the bug.

Looks like nobody tested this plugin against the recent changes...

---

### Post by balloons on 2012-03-01
> **quequotion said:**
> This is in the normal unity team PPA?

Were these changes already in the staging PPA before?

Last night I had to purge everything from the unity team staging ppa.

Right click menus of all kinds were crashing compiz.

***UPDATE***

Both versions (regular PPA and staging PPA) have this issue.

The problem is with the "Shift switcher" plugin.
Disabling this plugin works around the bug.

Looks like nobody tested this plugin against the recent changes...

Get a bug filed for this. Thanks for isolating the issue :-) That should help them get things figured out.

---

### Post by zika on 2012-03-01
> **guitara said:**
> Another point release from the unity folks. Here's what's new:

[LIST]
[*]A lot of bug fixes, especially in areas surrounding the HUD!
[*]Unity-2d now includes HUD.
[*]Compiz fixes -- including this awesome performance increase by Daniel [https://bugs.launchpad.net/compiz-core/+bug/940139](https://bugs.launchpad.net/compiz-core/+bug/940139)
[*]Keybinding shortcut changes -- there was noise about switching the keybindings for switching workspace ones and moving windows. This has been reverted to the previous values again
[/LIST]

Install the unity team ppa as usual, run thru the tests and report back.. Let me know how this one "feels" for you. I'm trying it now, too early to tell :-)

[http://www.theorangenotebook.com/2012/02/unity-56-whats-new-and-call-for-testing.html](http://www.theorangenotebook.com/2012/02/unity-56-whats-new-and-call-for-testing.html)
I just see 5.4 everywhere. No 5.6 to be found. What am I doing wrong? ;)

---

### Post by ventrical on 2012-03-01
Here is what happened after I logged off and logged back in:

---

### Post by kaldor on 2012-03-01
> **zika said:**
> I just see 5.4 everywhere. No 5.6 to be found. What am I doing wrong? ;)

Same here. Installed PPA, updated, and it says 5.4 still.

---

### Post by ventrical on 2012-03-01
> **guitara said:**
> Another point release from the unity folks. Here's what's new:

[LIST]
[*]A lot of bug fixes, especially in areas surrounding the HUD!
[*]Unity-2d now includes HUD.
[*]Compiz fixes -- including this awesome performance increase by Daniel [https://bugs.launchpad.net/compiz-core/+bug/940139](https://bugs.launchpad.net/compiz-core/+bug/940139)
[*]Keybinding shortcut changes -- there was noise about switching the keybindings for switching workspace ones and moving windows. This has been reverted to the previous values again
[/LIST]

Install the unity team ppa as usual, run thru the tests and report back.. Let me know how this one "feels" for you. I'm trying it now, too early to tell :-)

[http://www.theorangenotebook.com/2012/02/unity-56-whats-new-and-call-for-testing.html](http://www.theorangenotebook.com/2012/02/unity-56-whats-new-and-call-for-testing.html)

Thanks guitara,

 Downloading the ppa completey reverted a workaround for the desktop cube flicker problem. Now compiz is continually crashing and sending error reports that I  tell it not to.

---

### Post by ventrical on 2012-03-01
It's settled down now and I am testing. It will take a little while...

---

### Post by ventrical on 2012-03-01
Well I finsihed it with a lot of skips and when it was done , ready to send report, it crashed , saying it did not enter e-mail .. never gave me a chance:)

I would try again .but testing is just about over ..

---

### Post by balloons on 2012-03-01
> **ventrical said:**
> Thanks guitara,

 Downloading the ppa completey reverted a workaround for the desktop cube flicker problem. Now compiz is continually crashing and sending error reports that I  tell it not to.

Yes the cube problem fix is still being worked on, and is not in this ppa.

---

### Post by balloons on 2012-03-01
> **kaldor said:**
> Same here. Installed PPA, updated, and it says 5.4 still.

I reported this as a bug.. Running unity --version when testing from these new ppa's will still say the old version.. They won't update it till they release. See this bug for the discussion.

[https://bugs.launchpad.net/unity/+bug/925016](https://bugs.launchpad.net/unity/+bug/925016)

Or are you talking about something else?

---

### Post by kaldor on 2012-03-01
> **guitara said:**
> I reported this as a bug.. Running unity --version when testing from these new ppa's will still say the old version.. They won't update it till they release. See this bug for the discussion.

[https://bugs.launchpad.net/unity/+bug/925016](https://bugs.launchpad.net/unity/+bug/925016)

Or are you talking about something else?

Ah, this is exactly it. Thanks :)

---

### Post by snkiz on 2012-03-02
Did they kick dodge out of 2D? its been my safe harbor

---

