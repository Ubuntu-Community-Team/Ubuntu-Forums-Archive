---
title: "Unity 5.10 Testing"
date: 2012-04-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by balloons on 2012-04-05
Unity 5.10 is going to be landing tomorrow (Friday April 6th @ 1500 UTC or so). I will post a more formal announce at that time on my blog, but you guys are old hats at this. I wanted to give you the heads up.

You'll need the unity ppa as usual:

[https://launchpad.net/~unity-team/+archive/ppa](https://launchpad.net/~unity-team/+archive/ppa)
sudo add-apt-repository ppa:unity-team/ppa
sudo apt-get update && sudo apt-get dist-upgrade

Changes will be mostly bug fixes

[LIST]
[*]New version of compiz 0.9.7.4
[*]Keybindings changes
[LIST]
[*]Ctrl + Super + D Minimises all windows
[*]Ctrl + Super + Cursor up Maximizes the current window
[*]Ctrl + Super + Cursor down Restores or minimises current window
[*]Ctrl + Super + Cursor Left or Right Semi-maximises current window
[/LIST]
[*]Unity 2D and Unity 3D has right edge support for sticky edge detection
[/LIST]

You'll have the weekend more or less to test. Starting Monday, the devs will be prepping it for migration to precise.

---

### Post by balloons on 2012-04-06
Just adding there's a video walkthrough of this by Alan Pope:

[http://www.youtube.com/watch?v=AgL957zo5QM](http://www.youtube.com/watch?v=AgL957zo5QM)

If your curious how to do it, watch his video and learn.

---

### Post by grahammechanical on 2012-04-06
I am up for it. Anyone else going to join in?

---

### Post by mc4man on 2012-04-06
That would be compiz 0.9.7.6, 
(overall the more they fix compiz the worse it gets

---

### Post by neu5eeCh on 2012-04-06
> **mc4man said:**
> That would be compiz 0.9.7.6, don't know about those bindings, seems to stay on the 0.9.7.4 ones
(overall the more they fix compiz the worse it gets

I wouldn't know. I haven't been able to run compiz (load 3D) for almost two weeks now.

---

### Post by cariboo on 2012-04-06
I'm out of time for today, but I'll run the tests tomorrow.

---

### Post by mcellius on 2012-04-06
I did it, ran all the tests.  It passed almost all the tests (I think maybe two didn't work as expected), and all-told it took a couple hours.  But I learned some new things about Unity from it: some keyboard shortcuts and things I hadn't known about, although I have been using Unity for eleven months.  It helped to understand the HUD, too.

Overall, Unity seems snappy and very-well-behaved.  Solid and reliable.

---

### Post by mc4man on 2012-04-06
> **VTPoet said:**
> I wouldn't know. I haven't been able to run compiz (load 3D) for almost two weeks now.

Still curious - have you tried logging into ubuntu (3d), opening ccsm & unsetting/setting the core plugins? (composite, opengl, unity, ect.

As far as the 0.9.7.5 compiz - now I can add to the 'flashing' list restoring windows from 'show desktop'
So that's now - 
cube/rotate (unless hacked
expo
show desktop return
Additionally minimized windows are blank in 'spread' (scale

Edit: can also add  - choosing a custom backround color in unity-settings lasts till anything is done after setting

---

### Post by neu5eeCh on 2012-04-07
> **mc4man said:**
> Still curious - have you tried logging into ubuntu (3d), opening ccsm & unsetting/setting the core plugins? (composite, opengl, unity, ect.

No, but I _just did_. I went right for the jugular, disabling OpenGL. That pretty much borked the system, but that's OK. I rebooted from TTY (since I don't know how to re-enable from the command line).

I logged back in and now I've got compiz! But here's the strange thing: The Dash Button is not translucent (or maybe it is? I can't tell...). Normally, this would suggest (I think) that I'm using 2D, but everything else behaves like 3D. :-s So... well... there you have it. I'll be jinxed.
[IMG]https://poemshape.files.wordpress.com/2012/04/button.jpg[/IMG]

---

### Post by mc4man on 2012-04-07
> **VTPoet said:**
> No, but I _just did_. I went right for the jugular, disabling OpenGL. That pretty much borked the system, but that's OK. I rebooted from TTY (since I don't know how to re-enable from the command line).

I logged back in and now I've got compiz! But here's the strange thing: The Dash Button is not translucent (or maybe it is? I can't tell...). Normally, this would suggest (I think) that I'm using 2D, but everything else behaves like 3D. :-s So... well... there you have it. I'll be jinxed.

The Dash button (& launcher tint), is colored  depending on Desktop background, there is an override in unity settings but it can not use or produce black so it just gives other colors or grey
[https://bugs.launchpad.net/unity/+bug/924586](https://bugs.launchpad.net/unity/+bug/924586)

( I want a dark launcher, dash & non-favorite icons so only choice atm is set a single rgb, some opacity & set icons to Edge illumination ('Backlight and Edge ill... toggles' here

---

### Post by kaldor on 2012-04-07
The launcher won't stay the colour that I set it to, and instead uses the desktop background colour. If I change it in CCSM, it changes back to the background colour as soon as I interact with it.

I really miss the dark coloured Dash and Ubuntu button too :)

---

### Post by mc4man on 2012-04-07
> **kaldor said:**
> The launcher won't stay the colour that I set it to, and instead uses the desktop background colour. If I change it in CCSM, it changes back to the background colour as soon as I interact with it.

I really miss the dark coloured Dash and Ubuntu button too :)
2 seperate issue
getting a dark launcher like before seems almost impossible, if black was allowed it would be easy
Closest I can come ATM is in screen, not entirely happy about, hopefully they will allow black at some point

In the testing 5.10 there is this bug which causes any custom color setting to be 'ignored' as soon as you do anything after setting
[https://bugs.launchpad.net/unity/+bug/975350](https://bugs.launchpad.net/unity/+bug/975350)

---

### Post by kaldor on 2012-04-07
> **mc4man said:**
> 2 seperate issue
getting a dark launcher like before seems almost impossible, if black was allowed it would be easy
Closest I can come ATM is in screen, not entirely happy about, hopefully they will allow black at some point

In the testing 5.10 there is this bug which causes any custom color setting to be 'ignored' as soon as you do anything after setting
[https://bugs.launchpad.net/unity/+bug/975350](https://bugs.launchpad.net/unity/+bug/975350)

Nice, I just +1'd it. 

Yeah, I really want to have the dark dash back. I also think there should be an option to change this in the Appearance window too (Default Launcher or Adaptive Colours).

---

### Post by mc4man on 2012-04-07
> **kaldor said:**
> Nice, I just +1'd it. 

Yeah, I really want to have the dark dash back. I also think there should be an option to change this in the Appearance window too (Default Launcher or Adaptive Colours).

If the bug I linked in post 10 is addressed then using #000000 with some opacity would give the dark launcher, if you do it now you get dark everything

The other side issue is notification - you can't edit the color there
What I use to use is the 0.9.32-0ubuntu3 version from precise - that gives a nice dark notify box

(- to see I also just installed the 11.10 deb, (works fine) & then re-built & installed the notify package/source from here which gives more options - maybe he'll do a precise specific package

[https://launchpad.net/~leolik/+archive/leolik/+packages](https://launchpad.net/~leolik/+archive/leolik/+packages)

(I can't stand the default 10 sec notify time so always rebuild & lower or have previously tested that ppa which allows adjusting the display time

---

### Post by balloons on 2012-04-09
> **mc4man said:**
> That would be compiz 0.9.7.6, 
(overall the more they fix compiz the worse it gets

Yea -- there versioning gets me sometimes also, but sure enough:


~$ compiz --version
Compiz 0.9.7.6

---

### Post by mc4man on 2012-04-09
Just to re-comment on darkening the Dash - 
in the unity plugin settings > background the opacity setting, while affecting both the Dash & launcher, it has a much more noticeable affect on the Dash.  
The downside is to use that setting you must use a new color, for some that would be fine, for others it will just produce an awful launcher
(for the most part increasing the opacity significantly creates a terrible looking launcher

This may become more apparent now that the no blur option has been 'fixed' in 5.10, though it appears no blur will yet again use a lightly tinted transparent dash. To make it more usable the opacity would need to be increased in the background settings, again screwing up the launcher

What's really needed is a separate opacity for the dash  & or a no blur that makes sense

---

### Post by palimmo on 2012-04-11
I'm trying. And I still have the same problems:
- HUD doesn't work: it is disturbed by Multiload System Monitor.
[https://bugs.launchpad.net/unity/+bug/962984](https://bugs.launchpad.net/unity/+bug/962984)
- Blank window when I restore a previously minimized window
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/877778](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/877778)
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/938658](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/938658)

---

### Post by mcellius on 2012-04-12
I added the repository and got Unity 5.10 the day it came out.  I ran the tests that day, too.

At least, I think I did.  When I check the version:

```
unity --version
```

I get:

```
unity 5.8.0
```

Did they just forget to change the version it reports?

---

### Post by mc4man on 2012-04-12
> **mcellius said:**
> I added the repository and got Unity 5.10 the day it came out.  I ran the tests that day, too.

At least, I think I did.  When I check the version:

```
unity --version
```

I get:

```
unity 5.8.0
```

Did they just forget to change the version it reports?

The testing ppa is/was 5.8+ merges, basically 5.10
Anyway 5.10 has released & been built so you should now or shortly see an upgrade (they may be in 'proposed' first, I'm running it (5.10.0-0ubuntu1) now, alot of good fixes, some bad...

---

### Post by palimmo on 2012-04-13
> **palimmo said:**
> I'm trying. And I still have the same problems:
- HUD doesn't work: it is disturbed by Multiload System Monitor.
[https://bugs.launchpad.net/unity/+bug/962984](https://bugs.launchpad.net/unity/+bug/962984)
- Blank window when I restore a previously minimized window
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/877778](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/877778)
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/938658](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/938658)


Both SOLVED! :guitar:

---

### Post by palimmo on 2012-04-13
> **palimmo said:**
> Both SOLVED! :guitar:

HUD works... but there is still an "interference" with Indicator multiload.
But it is usable.

---

