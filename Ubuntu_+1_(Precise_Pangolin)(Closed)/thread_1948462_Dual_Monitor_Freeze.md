---
title: "Dual Monitor Freeze"
date: 2012-03-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by gunksta on 2012-03-28
I'm having trouble connecting an external monitory to a fully updated 12.04 system and I'm trying to figure out if it is a bug (which I should report) or operator error (which I should not).

The system was upgraded from 11.10. When running on 11.10, the external monitory (20" Acer) worked as expected. The system is a Lenovo x220. More importantly, it is running an Intel i5 and is using the Sandy Bridge graphics stack.

Scenario - I get to work and plug my laptop into the external monitor (as well as power, network, keyboard, etc.) I then power up the system. When LightDM comes up, it clones the output to both screens. When I try to get into either Unity or Gnome-Shell, the system freezes. There are no errors recorded in my .xsession-errors file. It is empty.

The system is experiencing a complete hard freeze. I can not remote into the system to diagnose the problem. I am also, of course, unable to switch to a tty terminal or any other form of intervention to diagnose the issue.

As the system freezes, it _appears_ that the system has tried to set up the screens correctly (not cloned, as per my settings) but everything freezes before it can do much.

This did not happen when using 11.10. This appears to be an X problem, not Unity since I get the EXACT same behavior using Gnome3/Mutter.

Thoughts?

---

### Post by grahammechanical on 2012-03-28
I have no experience of using a laptop with an external monitor.

You say that you get to a LightDm log-in screen. Is this on both screens? Can you use either screen to log-in?

If the system loads and gets past the Plymouth splash screen and then gets to the LightDM log-in screen then I would guess that the X-Server is using both screens correctly. But I am ignorant of these things.

You say

> When LightDM comes up, it clones the output to both screens.

So, things are working as they should work up to the point that you log-in. How could it be an X-Server problem?

Is it possible for you to try with a different video driver?

A couple more questions.

Do you get to a desktop with the Unity top panel and the Launcher and the Dash? Or does this system freeze mean that all you get is the background wallpaper. And the same thing happens with Gnome 3 shell?

How long have you had this problem? Since the last update?

Regards.

---

### Post by gunksta on 2012-03-28
Unless X has changed, X resets when it goes into the Desktop. But, I could be wrong, perhaps it isn't an X-Server issue at all.

I never see the Dash or anything else. All I get is my wallpaper. Same end result with both Gnome3 and Unity desktops. That's why I think it is X, Gnome3 and Unity use different window managers. If it was a WM problem, seems like one would still work correctly.

The laptop only has an Intel video card, so unless I want to try out the VESA driver or something, I don't have too many options beyond the Intel drivers.

Which update exactly are you talking about? I get updates almost every day.  :-)

I upgraded from 11.10 Friday night (23rd). The problem has existed since the upgrade to 12.04.

---

### Post by grahammechanical on 2012-03-28
I asked about updates because when using a development release such as 12.04 Beta 1 then it is good to update daily. It sometimes fixes problems. It sometimes causes problems.

For example as couple of days ago an update brought in an update to Compiz that reset my Unity adjustments and when I tried to use Compiz configuration Settings Manager to put them back Compiz closed unexpectedly. The message telling me this gave me a option to re-launch Compiz and again it closed unexpectedly. But that problem has not happened since.

On the other hand, at the moment I cannot log in to Unity 2D because some of the packages are scheduled to be upgraded but they are not yet ready. These packages will be upgraded in a couple of days.

So, I was wondering if this problem of yours was due to something being partially upgraded and perhaps it might be fixed over the next few days.

I was wondering if there was a time when you were using 12.04 and things were working correctly.

I also had a problem a few weeks ago when an updated Nvidia driver did not handle the change over from LightDM to the desktop very well. I got a scrambled coloured mess on the screen for a few seconds. I thought it was the video driver but an update to unity-greeter fixed the problem.

Regards.

---

### Post by gunksta on 2012-03-28
This may very well get updated in a future update. I'm just trying to figure out if others are experiencing the same thing. I did a cursory bug hunt but came up empty. I may go ahead and file a bug report. My hardware combination is pretty typical.

---

### Post by gunksta on 2012-04-01
Still having this problem. I see others posting with concerns or problems with dual screens on 12.04 but I can't get far enough to praise/condemn any of the changes.

Not sure how to file a bug against a problem when I don't even know what package is causing the problem (for sure).

Any thoughts regarding how I could nail down if it is definitely an X problem? (Or tests to prove/disprove it is caused by some other package such as the Intel driver, Compiz, etc.)

---

