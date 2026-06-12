---
title: "Programs quitting spontaneously or not starting"
date: 2010-06-16
forum: Ubuntu Studio
---

### Post by hreichgott on 2010-06-16
I just started having this problem this morning.  I tried to start up the following programs and they didn't open:
Aeolus
Ardour GTK2
Jack EQ

I wondered if JACK had to be running in order to start these programs.  I started JACK Control.  JACK would not start because another JACK server was already running somewhere.

I checked System Monitor to see what was running.  System Monitor started up, then promptly quit.

I tried to open Ubuntu Software Center and it spontaneously quit.

I rebooted.  Same behavior.  I tried System Monitor and Ubuntu Software Center a few times; they stay open sometimes, and other times they spontaneously quit an instant after opening.  I don't do anything differently the times that they stay running.

Once I got System Monitor to stay open, I could see on the processes list that Aeolus, Jack EQ etc. actually start (they show up on the list of processes) but quit before their GUIs appear.

OpenOffice and Firefox (at least) run normally.

Any suggestions?

---

