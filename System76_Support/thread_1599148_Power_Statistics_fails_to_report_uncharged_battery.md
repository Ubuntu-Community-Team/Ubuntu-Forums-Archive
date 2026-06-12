---
title: "Power Statistics fails to report uncharged battery"
date: 2010-10-17
forum: System76 Support
---

### Post by Dave_L on 2010-10-17
Starling Netbook (star3)

The Power Statistics (applet?) linked to the battery icon on the top panel almost always indicates that the battery is fully charged.

I've done some tests in which I disconnected the A/C adapter and let the netbook run on battery. The first time I did this, after a couple of hours, the display dimmed and I got a popup warning that the battery charge was critically low.  The applet, which I had periodically been checking, had continued to indicate that the battery was "fully charged". I reconnected the A/C; the battery apparently charged normally, but the applet continued to show "fully charged".

A day or so later, I repeated the test. This time the applet properly showed the battery discharging and charging.

Then I did the test a third time.  The applet behaved as in the first test. Although the battery discharged almost fully, the applet never indicated other than "fully charged".

What's going on? Is there a low-level status I could examine to reliably check the battery charge?

---

### Post by isantop on 2010-10-18
This is a known issue, and seems to be affecting other non-System76 computers as well. I appears to be an issue with Ubuntu. We'll continue to track this and notify everyone when a fix is out.

---

### Post by Dave_L on 2010-10-18
Thanks for the info.

I found another topic here about the upower daemon bug, with the tip that the command line utility acpi reports the correct battery status, so at least I can use that as a workaround.

---

