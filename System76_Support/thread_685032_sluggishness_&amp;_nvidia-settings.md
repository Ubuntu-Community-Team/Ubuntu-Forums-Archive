---
title: "sluggishness &amp; nvidia-settings"
date: 2008-02-01
forum: System76 Support
---

### Post by atorch on 2008-02-01
Hi everyone,

I'm having a problem with sluggishness.

I've attached a screenshot of my system monitor; please take a look at it *before reading what follows.*

A:  I click once on a document on my desktop, simply to select it.  Then I press the arrow keys to quickly select others.  I'll pick one up and drag it around.  All of this happens with a noticeable delay between action & effect (it takes a noticeable amount of time for an icon I've clicked on to become highlighted), and my CPU usage spikes up noticeably.  If I check the "Processes" tab (while selecting icons on my desktop), I see that almost all running processes are at 0% CPU; sometimes one of them will climb to 2 or 3%, but never higher.  This is strange -- you'd think the parts (0+0+...+0+2) would add up to the whole (sometimes up to 90% CPU usage at the peaks), but they don't.

B:  I run nvidia-settings OR sudo nvidia-settings; CPU usage spikes as I change my display's resolution and refresh rate.  More on this later.

C:  I am doing the *exact* same thing as in A, but CPU usage is now constant at 1~3%, as expected.

B is a solution to the problem in A (since C is where I want to be), but *every time I restart my computer*, I'm back at A.

Now, more detail on what's happening at B:

I run either nvidia-settings or sudo nvidia-settings and then, under the "X Server Display Configuration Tab," I change the Resolution / Refresh Rate combination.

The Resolution / Refresh Rate combination can be one of three things:

Auto and Auto
1280x800 and Auto
1280x800 and 60Hz

No matter what the Resolution / Refresh Rate is, I change it to something else, and click apply.  After a few moments of my CPU spiking to 100% (you can see this in the graph), I click OK.  After that I click "Save to X Configuration File."  If I am running sudo nvidia-settings, the save works without any error and I'm done.  If I am running nvidia-settings without sudo, I get an error message about rewriting or saving to the X Config Backup File, probably because I don't have permission.

Whether or not I ran nvidia-settings as sudo, step B solves the problem *temporarily* -- that is, until I restart.

Now here's the strange part:
If I ran nvidia-settings with sudo, and restart my computer, the Resolution / Refresh Rate combination that I chose will be remembered by nvidia-settings.  However, I still get lag -- to fix it, I again have to change to something else.

But if I ran nvidia-settings without sudo (and restart my comptuer), the Resolution / Refresh rate combination will *not* be remembered by nvidia-settings; instead, it defaults back to the most recent combination that was saved with sudo.  

This is strange because it allows any member of the set of Resolution / Refresh Rate combinations to be either a solution to or a cause of the problem.  Neither combination is always best or always worst -- all that matters is that, every time I restart my computer, I *change* the Resolution / Refresh Rate from whatever if was before.  It does not matter *what* I change it to or what I change it from; all that matters is that it change.  And that fixes the problem -- temporarily, until I restart my computer, at which point I have to change it again.  

I might be shooting a dead horse at this point, but let me just give an example:

When I first noticed the lag, I ran nvidia-settings without sudo and changed from Auto-Auto to 1280x800-60Hz.  The lag is gone.

I restart the computer.  It's lagging again; and because I changed the settings without sudo, they've defaulted back to Auto-Auto.  This time I run *with* sudo and change from Auto-Auto to 1280x800-60Hz.  The lag is gone.

I restart the computer.  It's lagging again; but this time the settings are 1280x800-60Hz.  So I run settings with sudo and change back to Auto-Auto.  The lag is gone.

I restart the computer.  It's lagging again; the settings are Auto-Auto.  I sudo change them to 1280x800-Auto.  The lag is gone.

I restart.  Lagging again; the settings are 1280x800-Auto.  I sudo change them.  The lag is gone.

I restart.  Ad infinitum.

Phew.  Sorry for such a long post to explain something so simple, but I find the problem very strange and I wanted to give a thorough explanation.

So:  Any suggestions?  Lag is annoying; so is running nvidia-settings every time I restart.  I'd appreciate any help you can offer.

Thanks,
--Adrian

* The link below will take you to the same threat in the general forums. *

[http://ubuntuforums.org/showthread.php?t=686031](http://ubuntuforums.org/showthread.php?t=686031)

* Useful information from the above link:  running "top" during A tells me that Xorg is the process eating up my CPU. *

---

### Post by atorch on 2008-02-01
A tiny bit of additional info:

The first time I noticed this problem, and changed nvidia-settings, restarting the computer did *not* cause the problem to return.  For a while, I thought I'd fixed it.  And then it came back, seemingly randomly.  I can't think of anything I've done since then that would explain it, except changing my compiz settings.  This is all very bizarre to me.

---

### Post by thomasaaron on 2008-02-04
Not sure which thread you are asking us NOT to reply to. THIS one or THIS one...
[http://ubuntuforums.org/showthread.php?t=686031](http://ubuntuforums.org/showthread.php?t=686031)

1. Try turning off your desktop effects and see if it still happens.
2. See my signature...

---

### Post by atorch on 2008-02-04
1.  

Sorry for the "do not post here" confusion.  I thought I would get a ton of answers in the general forum (since it's so active), and that this thread would become irrelevant.  But that didn't happen.

Please keep posting in this one.

2.  

The lag goes away if I turn off my desktop effects.

3.

I'm using Ubuntu Gutsy Gibbon, my laptop is a pangolin (bought in 2008, so it's probably the most recent model), and the only things I've tried are nvidia-settings and (just now) turning off my desktop effects.

---

### Post by atorch on 2008-02-04
* I wish this were true...  but it isn't. *
I set my compiz / desktop settings to normal and everything is fine after a few restarts.  Consider this issue solved...

I still don't understand what the problem was before, although it must have had something to do with my particular mix of desktop effects.  (And I didn't have anything extreme turned on...)
* The stuff above is (unfortunately) false.  See below. *

A bit of useful (and accurate) info:
If I run "top" during the lag, I see that Xorg is eating up 10~100% of my CPU.  After changing nvidia-settings or turning desktop effects off then on again (ie, after making the lag go away), Xorg only eats up 0~2% CPU.

---

### Post by atorch on 2008-02-05
* Nevermind... I restarted again and the issue came back.

Here's another way to temporarily fix the lag: turn off desktop effects, then set them to normal, then edit them... *

---

