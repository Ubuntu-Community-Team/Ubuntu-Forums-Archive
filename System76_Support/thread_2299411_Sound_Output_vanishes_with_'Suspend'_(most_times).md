---
title: "Sound Output vanishes with 'Suspend' (most times)"
date: 2015-10-18
forum: System76 Support
---

### Post by dalinian on 2015-10-18
My new System76 Meerkat arrived on Wed 14 Oct 2015 with Ubuntu 15.04 pre-installed. On the whole, I'm delighted with its performance, but I've noticed one annoying deficiency, and I could use some help in eliminating it, please.

After bootup or login, sound output is set to 'HDMI / Displayport Built in Audio'. So my Meerkat's sound output is routed from its HDMI port, out to a Dell monitor, and onwards to a pair of stereo reference speakers - all of which works well, as expected. Here's how that looks in 'System Settings...' > 'Sound':
[ATTACH=CONFIG]265022[/ATTACH]
*Sound Output via HDMI - after booting up (with automatic login) or logging in*

The [Test Sound] button works as expected, with both speakers performing well. However ...

When I choose 'Suspend' from the session menu, the system will go to sleep, and wake up again on a key press, as expected - but it will usually awake with no sound output, as illustrated below:
[ATTACH=CONFIG]265023[/ATTACH]
*No Sound Output - after a 'Suspend' and wake cycle (intermittently)*

Clicking on the [Test Sound] button does nothing.

Occasionally, this fault doesn't occur, but on most 'Suspend'-&-wake instances, the Meetkat awakes with no sound output; so I have to log out and log in again to get sound output working again.

Can anybody please help me to eliminate this problem?

Thanks in advance for your time and attention.

---

### Post by dalinian on 2015-11-10
System76 technical support could not supply a solution to this problem.

However, in continuing to search for my own solution, I came across some Intel Troubleshooting suggestions for the Intel NUC Kit NUC5i5RYH (of which the Meerkat is a rebadged model) regarding 'HDMI audio not working on Mint 16* or Ubuntu*':

&#8226; '**Intel NUC Boards and Kits &#8211; Linux Support**'
» [http://www.intel.com/support/motherboards/desktop/sb/CS-034779.htm](http://www.intel.com/support/motherboards/desktop/sb/CS-034779.htm)

Having carried out step 1 - *"Make sure that your system is up-to-date using the Update Manager"* - I re-checked for a 'Sound Output vanishes with Suspend' baseline, only to discover than the this latest iteration of running the Ubuntu Software Updater appears to have fixed the problem: the 'HDMI / Displayport Built in Audio' item no longer vanishes though the Suspend-&-wake cycle, when the Meerkat is booted from its internal pre-installed Ubuntu 15.04 SSD (ie: it now matches with being booted from an Ubuntu 15.04 Live USB, as previously explored in searching for a solution).

---

### Post by Geoffrey_Arndt on 2015-11-20
I've also noted that there have been several (3 or 4) System76 driver updates during the past month or so.

---

