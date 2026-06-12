---
title: "Blocky touchpad movements?"
date: 2009-05-02
forum: System76 Support
---

### Post by Vadi on 2009-05-02
After updaring my serp3 to 9.04, my touchpad decided to make my mouse go in "blocks" - it's not as smooth as my mouse is. Is anyone else experiencing this?

Also, sometimes a key will "hang" - even though I'm not pressing it down, and repeat it several times. Ie when I'm typing I'd get "yyyyyyyyyyyyyyyyes" all of a sudden instead of a "yes".

Both of these issues appeared on a clean install of 9.04 :/

---

### Post by drewbenn on 2009-05-02
I have a panv3.  I'm not having touchpad issues, but I am getting the multiple letters sometimes.  It's almost always been the 't' letter, although once it was a different letter near there.  I have a few crumbs in there that I haven't been able to get out, so I thought it was a physical issue -- it would be _great_ if it was a software issue that could be fixed! :)

---

### Post by Vadi on 2009-05-02
Pretty sure this is software as I did not have this issue before the update, and my keyboard is quite fine.

---

### Post by thomasaaron on 2009-05-02
I'm not getting any reports of touchpad problems. Try using a live CD and see if the problems occur there. If they do, you might have gotten a sketchy install.

---

### Post by drewbenn on 2009-05-02
Thomas, it's _really_ intermittent for me.  It's probably only happening once or twice a day when using the computer for several hours.  I can try running from a LiveCD for a while but if it doesn't happen, I don't think that necessarily proves anything.

Kind of talking aloud here: The one time it happened that I paid a lot of attention to it: the computer paused for a moment and then the keys repeated on the screen.  The keys I typed during the pause don't get printed to the screen, but keys typed after the pause show on the screen (I was in the middle of a sentence once when it happened: after the fact, several letters after the repeated key were missing).  So maybe (wild guess) something else is pausing, and a queue fills up with one key.

That's why I initially believed (and still would not be surprised to discover) that it was a physical problem: it acts as if I press a key, it sticks, and then unsticks a tiny bit later.  But there was no physical sensation of the key sticking.

Edit: I tried a LiveCD, and wrote a few paragraphs in OO.o Writer without seeing any problems, but everything feels so slow on the LiveCD that I gave up and rebooted to my normal system.

---

### Post by drewbenn on 2009-05-03
Okay, I was able to replicate it on the LiveCD, eventually.  I can also fairly reliably replicate it on my installed partition.  I just open Text Editor and start typing a couple letters as quickly as possible, like
fgfgfgfgfgfgfgfg
then I move the mouse pointer with the _touchpad_, and sometimes (maybe one in four?) I get the problem behavior.  If I move the pointer with my bluetooth mouse, I do not see the problem behavior.

I recorded a video with recordmydesktop but it's difficult to see what's happening because the mouse pointer disappears when I start typing, so you can only tell that the mouse moved because it briefly reappears.  If you think it would be useful (can't replicate the issue) I can upload it somewhere.

I think that the proper next steps (though I'm not sure I'm motivated to continue investigating) would be to (a) try again with an 8.10 Live CD to try to verify this is a new issue in 9.04 (as opposed to a physical issue with my keyboard), and (b) disable the touchpad (rmmod psmouse) and see if the problem reoccurs during normal operation (i.e. verify that I'm actually replicating the issue with those steps above, not a different issue).


I'm not sure if it's relevant or not, but I have an elantech (not synaptics) touchpad (does the serp3 have an elantech, also, or a synaptics touchpad?); and I believe there were some big changes in elantech support in 9.04.

For reference, here are some of the things that I did before noticing the link between the touchpad and the key repeats:
- replicated the issue for the first time after my previous post while playing boggle (apt-get install bsdgames; /usr/games/boggle). I don't think that game in particular or typing in the terminal in general are causes, but playing boggle entails a lot of typing in a short time period, so I think that just helped me replicate the issue.
- thought that Suspend was the culprit, because I couldn't replicate the issue (in my normal partition nor from the Live CD) immediately after booting up, but after a Suspend in my normal partition I did see the issue.  Later I was able to replicate the issue without doing a Suspend, so I could rule that out.
- looked for, and did not find, any messages in 'dmesg' near when the issue occurred.
- thought it was linked to the WLAN (I am on a WPA-secured network with a visible SSID).  I saw a bunch of "CTRL-EVENT-SCAN-RESULTS" lines at the end of wpa_supplicant.log, and I tried correlating their appearances in the log ("while true; do tail /var/log/wpa_supplicant.log; sleep 1; done" in a window (yeah, 'watch' would probably have been easier) while I typed a lot in a Text Editor window), but found that they were unrelated.
- tried several Google searches without success:
Searched for 	moving touchpad causes keys to repeat ubuntu
Searched for 	moving touchpad causes keys to repeat
Searched for 	CTRL-EVENT-SCAN-RESULTS delay
Searched for 	CTRL-EVENT-SCAN-RESULTS pause
Searched for 	CTRL-EVENT-SCAN-RESULTS pause key repeats
Searched for 	CTRL-EVENT-SCAN-RESULTS
Searched for 	9.04 key repeated several times
Searched for 	9.04 key repeats several times
Searched for 	9.04 stuck keys

---

### Post by mercmobily on 2009-05-04
Hi,

I have an HP Pavillion DV2570 with Ubuntu 9.04.

I can fully confirm this problem.

I debugged the issue as much as possible. What's happening is that the driver seems to be taking a while to *start* moving the mouse. Once it gets moving, it's fluid and everything.

I can only try and assume that _maybe_ the dwell click option in Ubuntu is creating the problem (System -> Preferences -> Mouse -> Accessibility. It's a nice feature, but it may well be the culprit here - maybe checking if the mouse is moving is getting in the way?

I have just come back from the HP service centre... they just happened to change touchpad 1 day before I upgraded to 9.04, and I blamed it on the new touchpad. They booted the machine with Vista, and voila', the problem had gone. OUCH!

Is there a bug in launchpad for this? It really needs to be reported... I am sure it affects a lot of people!

Merc.

Side note: I deeply regret upgrading to 9.04 ... now I have no visual effects (Intel card, will freeze) and, what's worse, no usable touchpad. OK, it _is_ usable, but... err...

---

### Post by thomasaaron on 2009-05-04
Yes, your computer has an elantech touchpad. And, yes, they've done quite a bit of work on it.

Before I start delving into this, did you try adjusting your repeat settings in System > Prefs > Keyboard?

---

### Post by mercmobily on 2009-05-05
Hi,

I played with every possible option in keyboard and mouse option settings, and didn't get anywhere.
My computer is basically unusable -- keeping sane, that is.

I can confirm that it looks like the driver takes a while to "wake up" when you start touching the touchpad. If you keep moving, it's smooth.

I will need to downgrade to 8.10 -- the only issue being that VirtualBox has already upgaded the virtual machine file and things will break. Arghhhhh...

Is something like this going to be anybody's priority, really? I think it's critical, but I can see how some people can say "at least it moves".

Shall I open an issue in the launchpad?

Merc.

---

### Post by mercmobily on 2009-05-05
Hi,

Is there any wya to downgrade to the previous driver, so that I can at least use my computer...?

If so, I can stick with the latest ubuntu (although no 3D... ugh) and help out with the problem...

Merc.

---

### Post by mercmobily on 2009-05-05
Hi,

I created a launchpad issue here:

[https://bugs.launchpad.net/ubuntu/+bug/372090](https://bugs.launchpad.net/ubuntu/+bug/372090)

What concerns me is that a lot of people won't even realise there is a problem -- they will just hate using their computers...

Plus although it's critical (I/O is critical...) I can see how this might take months and months to get fixed.. ugh :-(

Merc.

---

### Post by drewbenn on 2009-05-05
> **thomasaaron said:**
> Before I start delving into this, did you try adjusting your repeat settings in System > Prefs > Keyboard?

No, I had not tried changing that setting previously.  I tried it now, and was able to get rid of this behavior by increasing the 'Delay' setting, moving it from 'Short' toward 'Long' by about the same distance it already was from 'Short' (it's now just left of center).

So there is still a short delay when I tap the touchpad while typing, but the 'repeating keys' issue is gone.

Thanks!

---

### Post by mercmobily on 2009-05-05
Hi,

I am seeing the touchpad problems independently to the keyboard problem...

In fact, I have no problems at all with my keyboard!

Merc.

---

### Post by mercmobily on 2009-05-05
Hi,

One additional note: the touchpad works 1000000% OK with Windows Vista... that was a painful one to watch. Really.

Merc.

---

### Post by mercmobily on 2009-05-07
Hi,

I have the ugly feeling this is gonna stay broken for a long time...

It probably affects me and 6 other people...

:-(

Merc.

---

### Post by thomasaaron on 2009-05-07
Sorry, guys. This thread has gotten a little hectic, and I had difficulty following it.

**drewbenn**, I don't think your problem is the same as mercmobily's. Here are some excerpts from your posts:

> I have a panv3. I'm not having touchpad issues, but I am getting the multiple letters sometimes. It's almost always been the 't' letter, although once it was a different letter near there. I have a few crumbs in there that I haven't been able to get out, so I thought it was a physical issue -- it would be _great_ if it was a software issue that could be fixed! 


Okay, I was able to replicate it on the LiveCD, eventually. I can also fairly reliably replicate it on my installed partition. I just open Text Editor and start typing a couple letters as quickly as possible, like
fgfgfgfgfgfgfgfg
then I move the mouse pointer with the _touchpad_, and sometimes (maybe one in four?) I get the problem behavior. If I move the pointer with my bluetooth mouse, I do not see the problem behavior.

No, I had not tried changing that setting previously. I tried it now, and was able to get rid of this behavior by increasing the 'Delay' setting, moving it from 'Short' toward 'Long' by about the same distance it already was from 'Short' (it's now just left of center).

So there is still a short delay when I tap the touchpad while typing, but the 'repeating keys' issue is gone.

So, it sounds like you are good. You might buy some canned air and blow out your keyboard too.



**MERCMOBILY**, you said you upgraded to Jaunty. Please run your computer from a live Jaunty CD to see if the problem exists there. Since I'm not getting numerous complaints about this, I think it is most likely an upgrade glitch.

---

### Post by Vadi on 2009-05-07
My touchpad doesn't have the vertical or horizontal scrolling anymore either.

Looks like the touchpad driver was tinkered with quite heavily...

---

### Post by thomasaaron on 2009-05-07
Hi, Vadi. See if this works for you.

[http://ubuntuforums.org/showthread.php?t=1137724](http://ubuntuforums.org/showthread.php?t=1137724)

---

### Post by Vadi on 2009-05-07
I see. Yes, moving with two fingers works.

---

### Post by thomasaaron on 2009-05-07
OK, good. I don't really care for that particular feature, but I guess we're stuck with it!

---

### Post by farruinn on 2009-05-18
I just wanted to report that I am also seeing the same problem as Vadi and Mercmobily with my Serp4 on a fresh install of 9.04.  The movement is never fluid for me, though, like merc has described.  For example, moving the mouse in a diagonal direction makes it look like it's climbing a set of stairs.  Basically every time the mouse moves, it moves by 4-8 pixels instead of 1.  I don't have my liveCD handy, but I can check that too later this afternoon.  Movement with a USB mouse is fine.

This is from /var/log/xorg.conf during startup:
```
(II) config/hal: Adding input device ETPS/2 Elantech Touchpad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 0.99.3
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event8"
(II) ETPS/2 Elantech Touchpad: x-axis range 32 - 544
(II) ETPS/2 Elantech Touchpad: y-axis range 32 - 352
(II) ETPS/2 Elantech Touchpad: device does not report pressure, will use touch data.
(II) ETPS/2 Elantech Touchpad: finger width range 0 - 0
(II) ETPS/2 Elantech Touchpad: buttons: left right middle double triple
(--) ETPS/2 Elantech Touchpad touchpad found
(**) ETPS/2 Elantech Touchpad: always reports core events
(II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD)
(**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
(**) ETPS/2 Elantech Touchpad: (accel) filter chain progression: 2.00
(**) ETPS/2 Elantech Touchpad: (accel) filter stage 0: 20.00 ms
(**) ETPS/2 Elantech Touchpad: (accel) set acceleration profile 0
(--) ETPS/2 Elantech Touchpad touchpad found
```

I'm guessing the last few lines about acceleration are important, but I don't know what they mean or how to change them.

Changing the driver in xorg.conf from "mouse" to "synaptics" changes the output to this:
```
(II) config/hal: Adding input device ETPS/2 Elantech Touchpad
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event8"
(II) ETPS/2 Elantech Touchpad: x-axis range 32 - 544
(II) ETPS/2 Elantech Touchpad: y-axis range 32 - 352
(II) ETPS/2 Elantech Touchpad: device does not report pressure, will use touch data.
(II) ETPS/2 Elantech Touchpad: finger width range 0 - 0
(II) ETPS/2 Elantech Touchpad: buttons: left right middle double triple
(--) ETPS/2 Elantech Touchpad touchpad found
(**) ETPS/2 Elantech Touchpad: always reports core events
(II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD)
(**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
(**) ETPS/2 Elantech Touchpad: (accel) filter chain progression: 2.00
(**) ETPS/2 Elantech Touchpad: (accel) filter stage 0: 20.00 ms
(**) ETPS/2 Elantech Touchpad: (accel) set acceleration profile 0
[COLOR="Red"](WW) ETPS/2 Elantech Touchpad can't grab event device, errno=16[/COLOR]
(--) ETPS/2 Elantech Touchpad touchpad found
```

I also installed gsynaptics and experimented with the various settings but didn't have any luck there either.

---

### Post by Vadi on 2009-05-18
Yeah, same symptoms as farruinn. Not so bad since I mostly use a USB mouse, but when I am without it, the step-climbing isn't as nice.

---

### Post by agentjon on 2009-05-18
i had some touchpad issues on jaunty with my panv3.  

it sort of felt like the touchpad wasn't picking up my finger properly, resulting in stuttering, imprecise movements.  

i edited my xorg.conf as described here:
[http://strabes.wordpress.com/2006/11/04/change-touchpad-sensitivity-in-ubuntu/](http://strabes.wordpress.com/2006/11/04/change-touchpad-sensitivity-in-ubuntu/)
and it seems to have put everything back to normal

---

### Post by mercmobily on 2009-05-23
Hi,

I added a comment to the bug. Can you guys see if it's true, that the bug was there, although not as noticeable, in 8.10?

-------------------------
Hi,

I just wanted to add that I downgraded to Ubuntu 8.10 (I can't deal with computer freezes... I don't have a test machine, sorry :( ).

Now... the problem is _there_ as well! But, it's much more subtle. I think it's subtle enough to make people slightly hate their touchpad and Ubuntu in general, but it's not clear enough (not in 8.10) to go "Ah, that's what's happening!".

In 8.10 as well, there is a small delay from when the touchpad has input to when the driver actually does something about it. I must say the problem is WAY less in 8.10 than 9.04, but I _guarantee_ it's there. If you know it's there, you suddenly realise why you hate the touchpad and you see clearly the delay. In 9.04, the problem is multiplied by 5x (give or take), and that's why people noticed.

I am happy to provide whatever info you might need.

Merc.
--------------------------------------------------

---

### Post by mercmobily on 2009-05-23
@agentjon: I tried to do that for 8.10, and no, it didn't make it any better... The problem is subtle, but subtly very annoying...

---

