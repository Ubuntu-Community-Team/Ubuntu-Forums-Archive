---
title: "Are updates installed automatically?"
date: 2015-03-18
forum: Ubuntu Studio
---

### Post by tpattgeek on 2015-03-18
I installed Ubuntu Studio in another attempt to replace my Windows desktop while having exceptional support for audio/video playback, but I had a few questions:

1. If I had an Internet connection during install, did it install type 1-3 updates automatically?  I was never prompted to do so like other distros.  Where can I verify?  Software Updater?

2. Out of the box, my Audacious playlist would not play.  I changed the Audacious audio setting from Pulse to ALSA and that resolved that, but then I started experiencing playback issues with mkv, streaming video, youtube, etc. where the video would play for 2-10 seconds then freeze, untimately freezing firefox for a minute or so.  The system had only been online for about 24 hours, but I said what the heck Ill just reboot, and that fixed it.  Is it possible some updates were installed and I wasn't notified of a required reoot?

3. When I got home yesterday, I noticed the indicator plugin on the top bar showed an envelope with an XChat notification.  I click it, and it wants me to confirm username and connect to a channel.  The Clear button is greyed out, but I would like to remove that envelope without having to remove the whole indicator plugin which removed my pulse/volume level and wifi indicator.

4. I'm also still extremely confused with pulse vs. alsa and how each one affects certain applications.  I've read where pulse is more crisp but mostly I've heard that it' gargabe.  My main concern is playback in Audacious and flash/streaming.  I know this is all pretty noob, but I'm getting there :)  Thank you!

---

### Post by ian-weisser on 2015-03-18
> **tpattgeek said:**
> did it install type 1-3 updates automatically?
What is a 'type 1-3' update?
When you installed, a check box asked if you wanted to install updates during the install. If unchecked, you didn't.

> **tpattgeek said:**
> Is it possible some updates were installed and I wasn't notified of a required reoot?
Very unlikely. The requirement for a reboot will show among your app indicators / notification pop-ups / systray.
Very few updates require a reboot.


Security updates are usually automatic.
Other updates (bugfixes, backports) are not automatic.
It's a setting, easily changable, in /etc/apt/apt.conf.d/50unattended-upgrades . The GUI version, software-properties-gtk/software-properties-qt has less (safer) functionality, since poor choices can quickly break your system.

---

