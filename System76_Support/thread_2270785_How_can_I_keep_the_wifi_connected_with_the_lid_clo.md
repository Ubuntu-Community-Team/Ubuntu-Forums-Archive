---
title: "How can I keep the wifi connected with the lid closed?"
date: 2015-03-25
forum: System76 Support
---

### Post by tatere2 on 2015-03-25
Power management is set to do nothing when the lid is closed and it's plugged in. But it still turns off wifi, which means all network backups etc. can't run. If the whole machine isn't suspended anyway, that is.

Is there anything I can do about this?

this is on a Kudu Pro running 14.04

---

### Post by jweber53 on 2015-04-17
Hi,
I just got a new Kudo Pro last week running Ubuntu 14.10. My WiFi stays connected with the lid closed. Maybe other power settings besides the lid closed affect it? I have
"Suspend when inactive" set to "Don't Suspend" for both plugin and battery.
"When power is  critically low" set to "Power Off"
"When the lid is closed" set to "Do Nothing" for both.

John

---

### Post by tatere2 on 2015-04-17
It turns out the problem was environmental, not with the laptop itself. The power would go out for a few minutes. That put the machine into battery mode, and that led it to suspend itself because the lid was closed. Once suspended, it says suspended, even when the power comes back.

So when I need the net connection to stay up, I'll have to either leave the lid open, or get a UPS and hope the power outage is shorter than its battery life.

---

