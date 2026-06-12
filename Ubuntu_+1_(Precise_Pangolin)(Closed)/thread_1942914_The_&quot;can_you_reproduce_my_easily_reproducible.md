---
title: "The &quot;can you reproduce my easily reproducible bug?&quot; thread"
date: 2012-03-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by fluteflute on 2012-03-18
Here are some bugs that I can reproduce easily. Please can you see if you can reproduce them too by following the instructions within the bug report.

If you can reproduce the bug, please mark it as affecting you and perhaps add a comment about your hardware configuration (on Launchpad). If you cannot, please also write this on the bug report.

Everyone else: please add your easily reproducible bugs to this thread so we can all get testing!

[SIZE="1"](Sorry if someone has already made a thread like this)[/SIZE]

So to start: [Bug #954797: Unity shortcuts ctrl-alt-4 and 6 do not work in Precise]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/954797")

Multiple monitor users only: [Bug #954292: "Modal" dialogs do not appear as expected in multiple monitor setup]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/954292")

Possible only ATI Radeon HD users, but anyone please test: [Bug #927051 : On bootup, 'screenshot of shutdown' flashes up]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/927051")

---

### Post by neu5eeCh on 2012-03-18
Thanks, that's a useful list. Checked off the first one.

---

### Post by keithpeter on 2012-03-18
Hello fluteflute and all

Added myself to the first one, although this is actually a new facility to me!

Last one about boot up artifacts. I'm using nvidia GeForce GT520 card and the proprietary drivers. I get a 'mashed up' version of things on my desktop when booting up. The bit between the log-in screen and the desktop appearing. Its not simply the windows as before, but a pattern of small sections of windows, as if video memory is being read back in the wrong order. Does that sound like the same thing?

During testing I don't use autologin in case of breakage in one of the desktop environments...

---

### Post by ppd on 2012-03-19
I have one very easy to verify:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/941884](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/941884)

---

### Post by grahammechanical on 2012-03-19
Did anyone run the Checkbox Unity test suites? I did. I do not remember testing Ctrl+Alt+numpad4 or Ctrl+Alt+numpad6 as part of the tests.

Is this a bug in the sense that it does not do what it is intended to do or in the sense that it does not do what some people want it to do.

I did test Super+right arrow and Super+left arrow and that does work as intended.

It is a good idea that Ubuntu+1 be used to double check what we find. We do need some organised structure to it.

Ubuntu Quality and Assurance will improve if we can reduce bug overload.

I think that it is time we stopped calling disappointments with Ubuntu features or lack of them, bugs. It leads to a perception that Ubuntu is buggy.

Regards.

P.S. After further investigation I find that if you go the System Settings>Universal Access>Pointing and Clicking you will see a slider with the title Mouse Keys. It will let you turn on and off the feature to control the pointer using the keypad.

Is that the answer? Will somebody test this out please?

Also in System Settings>Keyboard>Shortcuts if you scroll down to the bottom you will see that moving to another workspace is controlled by the Ctrl+Alt+arrow key combination.

Do not forget that testing of the development branch means testing a default Ubuntu install and not a Ubuntu that we have modified to our tastes and likes.

---

### Post by fluteflute on 2012-03-19
> **keithpeter said:**
> Last one about boot up artifacts. I'm using nvidia GeForce GT520 card and the proprietary drivers. I get a 'mashed up' version of things on my desktop when booting up. The bit between the log-in screen and the desktop appearing. Its not simply the windows as before, but a pattern of small sections of windows, as if video memory is being read back in the wrong order. Does that sound like the same thing?

During testing I don't use autologin in case of breakage in one of the desktop environments...I definitely see the bug you metion, although it's not the same as (but likely related to) the one I reported.

> **ppd said:**
> I have one very easy to verify:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/941884](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/941884)I look forward to testing this when I get home.

> **grahammechanical said:**
> Did anyone run the Checkbox Unity test suites? I did. I do not remember testing Ctrl+Alt+numpad4 or Ctrl+Alt+numpad6 as part of the tests.

Is this a bug in the sense that it does not do what it is intended to do or in the sense that it does not do what some people want it to do.

I did test Super+right arrow and Super+left arrow and that does work as intended.This particular case is a bug in that Ctrl+Alt+numpad4 or Ctrl+Alt+numpad6 used to work in 11.10, but do not work in 12.04. 

Because laptop owners often don't have numberpads, it was decided to add Super+right arrow and Super+left arrow. However there is a Compiz limitation that you cannot have two keybindings for the same thing. So Ctrl+Alt+numpad4 and Ctrl+Alt+numpad6 have stopped working, until this is fixed.

---

### Post by Elfy on 2012-03-19
> **keithpeter said:**
> 
Last one about boot up artifacts. I'm using nvidia GeForce GT520 card and the proprietary drivers. I get a 'mashed up' version of things on my desktop when booting up. The bit between the log-in screen and the desktop appearing. Its not simply the windows as before, but a pattern of small sections of windows, as if video memory is being read back in the wrong order. Does that sound like the same thing?

If there is a bug report for this I'd be forced to +1 it. Same thing here with GeForce 8500 GT

---

### Post by fluteflute on 2012-03-20
> **keithpeter said:**
> Last one about boot up artifacts. I'm using nvidia GeForce GT520 card and the proprietary drivers. I get a 'mashed up' version of things on my desktop when booting up. The bit between the log-in screen and the desktop appearing. Its not simply the windows as before, but a pattern of small sections of windows, as if video memory is being read back in the wrong order. Does that sound like the same thing?> **forestpiskie said:**
> If there is a bug report for this I'd be forced to +1 it. Same thing here with GeForce 8500 GT

I've found a bug report for this: [https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/931967](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/931967)

And excitingly, the new 0.2.5-0ubuntu2 version of unity-greeter claims to fix it.

---

### Post by Elfy on 2012-03-20
> **fluteflute said:**
> I've found a bug report for this: [https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/931967](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/931967)

And excitingly, the new 0.2.5-0ubuntu2 version of unity-greeter claims to fix it.

Yea saw that.

Unfortuantely I get a similar issue with Xubuntu - though it is fleeting - I got that me too'd somewhere :)

---

### Post by fluteflute on 2012-03-20
> **forestpiskie said:**
> Yea saw that.

Unfortuantely I get a similar issue with Xubuntu - though it is fleeting - I got that me too'd somewhere :)The unity-greeter package is the LightDM login screen used by all desktop environments, so it may be fixed for you too! :)

---

### Post by howefield on 2012-03-20
> **fluteflute said:**
> And excitingly, the new 0.2.5-0ubuntu2 version of unity-greeter claims to fix it.

Yay, fixed over here.

---

### Post by Elfy on 2012-03-20
There's no unity-greeter in xubuntu - it uses something else :)

---

### Post by fluteflute on 2012-03-20
*removed*

(but see [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540816](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540816) if you want to know what this post was about)

---

### Post by Space_Balls on 2012-03-23
On all of my systems, pressing the escape key while on the lightdm greeter screen results in the xsever/lightdm restarting:

[LP #962932]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/962932")

---

### Post by fluteflute on 2012-03-24
This is a design issue (so maybe not entirely in the spirit of this thread :p)

[Bug #963731: Fixing Bug #950136 has caused a confusing Displays interface ]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/963731")

---

### Post by fluteflute on 2012-04-12
Here's an Update Manager annoyance:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/979994](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/979994)

---

### Post by Elfy on 2012-04-12
Odd - +1'd it

---

### Post by ubuntu27 on 2012-04-13
Can anyone reproduce the following bugs?


1) Unresponsive Windows bug: [https://bugs.launchpad.net/unity/+bug/976302](https://bugs.launchpad.net/unity/+bug/976302)


2) Parental Control does not run: [https://bugs.launchpad.net/ubuntu/+source/nanny/+bug/977015](https://bugs.launchpad.net/ubuntu/+source/nanny/+bug/977015)


3) Screen flickers or turns black upon running Super Tux Kart:

[https://bugs.launchpad.net/ubuntu/+source/supertuxkart/+bug/970599](https://bugs.launchpad.net/ubuntu/+source/supertuxkart/+bug/970599)


4) Image Viewer "**Comix**" flicks when opening a _large_ image:

[https://bugs.launchpad.net/ubuntu/+source/comix/+bug/975345](https://bugs.launchpad.net/ubuntu/+source/comix/+bug/975345)

---

### Post by fluteflute on 2012-04-13
> **ubuntu27 said:**
> Can anyone reproduce the following bugs?


1) Unresponsive Windows bug: [https://bugs.launchpad.net/unity/+bug/976302](https://bugs.launchpad.net/unity/+bug/976302)That one's nasty!


> **ubuntu27 said:**
> ) Parental Control does not run: [https://bugs.launchpad.net/ubuntu/+source/nanny/+bug/977015](https://bugs.launchpad.net/ubuntu/+source/nanny/+bug/977015)Lots of people have reported that - I marked yours and a few other reports as duplicates of another bug.

> **ubuntu27 said:**
> 3) Screen flickers or turns black upon running Super Tux Kart:

[https://bugs.launchpad.net/ubuntu/+source/supertuxkart/+bug/970599](https://bugs.launchpad.net/ubuntu/+source/supertuxkart/+bug/970599)Can't reproduce that one. The game doesn't freeze for me.


> **ubuntu27 said:**
> 4) Image Viewer "**Comix**" flicks when opening a _large_ image:

[https://bugs.launchpad.net/ubuntu/+source/comix/+bug/975345](https://bugs.launchpad.net/ubuntu/+source/comix/+bug/975345)Definitely get some graphics corruption. Not quite sure if it's exactly the same as what you're experiencing.

---

### Post by NHclimber on 2012-04-13
> **Space_Balls said:**
> On all of my systems, pressing the escape key while on the lightdm greeter screen results in the xsever/lightdm restarting:

[LP #962932]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/962932")

Nice. This is not fixed (or regressed).  Although the X server doesn't restart, lightdm is zombie-fied and restarted.

---

### Post by Elfy on 2012-04-15
Do you have a mount asa read/write option in your recovery menu ?

I don't :(

 [https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/982134](https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/982134)

---

