---
title: "Firefox 96.0 page load problems"
date: 2022-01-23
forum: The Cafe
---

### Post by curts on 2022-01-23
Is anybody else experiencing page load problems since the rollout of Firefox 96.0? Some pages I can *eventually* load after 1-3 tries (highlight the URL and press <Enter>), but that's real problem if it is a pop-page that is not loading on the first try.

I'm running Ubuntu 20.04.1.

--Curt

---

### Post by &amp;KyT$0P# on 2022-01-23
Not seeing that here.  What troubleshooting steps have you tried?

---

### Post by poorguy on 2022-01-23
No problems here either.

---

### Post by DuckHook on 2022-01-23
Running tickety-boo here.

[LIST=1]
[*]Try clearing your FF cache.
[*]If the problem does not go away, export your bookmarks (and, if you want, your history), then reset. Then, import everything.
[/LIST]

---

### Post by Autodave on 2022-01-25
Yes!  After a short while (5 minutes) it just locks up kinda.  New pages won't open, open pages scroll to a black screen.  Not liking it at all.  I will admit that a few days ago there was an update (don't know what was updated) and that helped a little....I can go 10 or 15 minutes now.  My wife's computer is the same way.

---

### Post by DuckHook on 2022-01-25
> **Autodave said:**
> Yes!  After a short while (5 minutes) it just locks up kinda.  New pages won't open, open pages scroll to a black screen.  Not liking it at all.  I will admit that a few days ago there was an update (don't know what was updated) and that helped a little....I can go 10 or 15 minutes now.  My wife's computer is the same way.
Revised report: My main box is fine. But an old laptop is now acting up in exactly this way. So far, I haven't had the time to investigate, but when I get around to it, I may try invoking it from a terminal session and looking at the output.

---

### Post by &amp;KyT$0P# on 2022-01-26
Autodave, do you have hardware acceleration enabled in Firefox?  If so, does [disabling it]("https://support.mozilla.org/en-US/kb/firefox-hangs-or-not-responding#w_turn-off-hardware-acceleration") make any difference?

---

### Post by DuckHook on 2022-01-26
> **halogen2 said:**
> …do you have hardware acceleration enabled in Firefox?  If so, does [disabling it]("https://support.mozilla.org/en-US/kb/firefox-hangs-or-not-responding#w_turn-off-hardware-acceleration") make any difference?
Thanks halogen2:

In my case, this solved it.

Something must have changed between FF updates—HW acceleration was no problem until now and is still fine in other machines. Odd.

---

### Post by Autodave on 2022-01-26
Autodave, do you have hardware acceleration enabled in Firefox?  If so, does [disabling it]("https://support.mozilla.org/en-US/kb/firefox-hangs-or-not-responding#w_turn-off-hardware-acceleration") make any difference?

Actually, I have no idea!  This is the way FF installed when I switched to 20.04 (clean install) almost 4 years ago.  Everything was fine until a couple weeks ago. when FF 96.0 was installed by the update manager.

Just checked....HW acceleration is not chosen.

---

### Post by &amp;KyT$0P# on 2022-01-26
> **DuckHook said:**
> Thanks halogen2:

In my case, this solved it.

You're welcome DuckHook. :KS

> **Autodave said:**
> Just checked....HW acceleration is not chosen.

As diagnostic tests:
[LIST]
[*]Does the issue exist in [Firefox Troubleshoot Mode]("https://support.mozilla.org/en-US/kb/diagnose-firefox-issues-using-troubleshoot-mode")?
[*]Does the issue exist in a new, separate, clean [Firefox profile]("https://support.mozilla.org/en-US/kb/profile-manager-create-remove-switch-firefox-profiles") with no extensions and all default settings?
[/LIST]

---

### Post by curts on 2022-02-02
Clearing cache made a small improvement, but load behavior was still periodically a problem. Starting in safe-mode was still problematic. Changing from specifically selected h/w acceleration back to 'Use recommended performance settings' does appear to have improved behavior, but need to evaluate for several days.

---

### Post by DuckHook on 2022-02-02
> **halogen2 said:**
> …does [disabling it]("https://support.mozilla.org/en-US/kb/firefox-hangs-or-not-responding#w_turn-off-hardware-acceleration") make any difference?

> **curts said:**
> …Changing from specifically selected h/w acceleration back to 'Use recommended performance settings' does appear to have improved behavior, but need to evaluate for several days.
I'm a bit confused…

The suggestion was to ***disable*** HW acceleration, whereas your post reads as if you just turned the setting to manual but left HW acceleration on. The recommendation was to disable it altogether by ***un***checking the box.

---

### Post by curts on 2022-02-04
Manual HW acceleration is selected by unchecking the 'Use recommended performance settings' box and checking the 'Use hardware acceleration when available' box. When the  'Use recommended performance settings' box is checked, the GUI hides the 'Use hardware acceleration when available' box, which implies the manual setting is overridden by the 'Use recommended performance settings' setting.

Unchecking both 'Use recommended performance settings' and 'Use hardware acceleration when available' is a different configuration, which I am not currently testing.

Thus far, after reverting to the 'Use recommended performance settings' selection I believe I am seeing further improvement, but page load reliability is still degraded for some web links compared to behavior before the Firefox update, e.g. some links require two or three attempts to get the page to load.

---

### Post by DuckHook on 2022-02-04
Yes, we are on the same page as far as your description of the setting goes. However, the default when "Use recommended performance settings" is on is to also turn *on* HW acceleration. halogen2's recommendation (and what worked for me) was to turn *off* HW acceleration. You can only do this by turning off recommended perf settings, then turning off HW accel.

In more depth:

It seems that the FF devs revamped HW acceleration in the latest update. This was supposed to improve rendering efficiency and play nice with newer video cards, but it had the unintended consequence of breaking some older GPUs and some unconventional motherboard designs. These forums are not the only place where issues are being raised, it's all over the Internet.

I don't understand why you are suddenly seeing a difference with "manual but HW accel on" and "recommended performance on". They amount to the same thing. The only reason to turn off "recommended" is to get to the HW acceleration and turn it off.

---

### Post by curts on 2022-02-06
Thanks for the clarification @DuckHook, as I had obviously misunderstood what the recommendation was. I have changed my settings to have HW acceleration turned off - now to see how that affects the browser behavior. I've also found the HTTPS Everywhere plug-in may have been causing some interference and my VPN was causing problems for a few pages.

---

### Post by DuckHook on 2022-02-07
Yes, sometimes problems are due to multiple causes. HTTPS Everywhere is a good setting to have on. It will flag some plain old HTTP sites as unsafe, but that's because they *are* unsafe. With the advent of free certificates (a big thank you to Let's Encrypt), there is no reason that sites are still on HTTP.

Your VPN may very well be a bottleneck. It depends on the quality of your provider and the server you are connected to.

The reason for HW acceleration is to take some of the load off your CPU and shift it to your GPU which is designed to handle things like video streams etc. If it is turned off, your GPU is bypassed and the whole rendering load is dumped onto your CPU. Depending on how old or low powered your CPU is, this might cause some dropped frames, hot running CPU, etc, but it should no longer freeze up your whole machine. My old laptop runs like a snail with HW acceleration off, but at least it runs, whereas it gave up the ghost when HW accel was on.

---

