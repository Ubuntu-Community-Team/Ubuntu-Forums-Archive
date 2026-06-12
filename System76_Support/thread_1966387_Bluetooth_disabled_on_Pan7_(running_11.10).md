---
title: "Bluetooth disabled on Pan7 (running 11.10)"
date: 2012-04-27
forum: System76 Support
---

### Post by svasan on 2012-04-27
Hi,

Bluetooth is disabled on my laptop and I'm not able to turn it back on. I tried Fn+F12 and that did not turn it on. I tried 'sudo service restart bluetooth'; that also didn't help.

I've had this problem for a while and don't remember if it started with 11.10 upgrade or before. I was just ignoring it so far.

Also, System Settings -> System76 Driver was giving me an error msg when I tried to open it. That may  have been from the 11.10 upgrade. I downloaded the latest driver deb, installed it and clicked 'Restore' and then restarted. My bluetooth problem still exists.

I saw this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/714862](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/714862) but don't know if that applies to a pan7 or not. Wanted to check here first to see if anyone has any ideas on whats going on. Any suggestions?

thanks.

---

### Post by isantop on 2012-04-27
> **svasan said:**
> Hi,

Bluetooth is disabled on my laptop and I'm not able to turn it back on. I tried Fn+F12 and that did not turn it on. I tried 'sudo service restart bluetooth'; that also didn't help.

I've had this problem for a while and don't remember if it started with 11.10 upgrade or before. I was just ignoring it so far.

Also, System Settings -> System76 Driver was giving me an error msg when I tried to open it. That may  have been from the 11.10 upgrade. I downloaded the latest driver deb, installed it and clicked 'Restore' and then restarted. My bluetooth problem still exists.

I saw this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/714862](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/714862) but don't know if that applies to a pan7 or not. Wanted to check here first to see if anyone has any ideas on whats going on. Any suggestions?

thanks.

That bug doesn't apply to the PanP7. We've never used Atheros cards in our systems. 

Go ahead and create a LiveCD of Ubuntu 12.04 LTS, and try using bluetooth from there. My guess is that there's a small software problem, and running from fresh software will clear it up.

---

### Post by svasan on 2012-05-12
> **isantop said:**
> Go ahead and create a LiveCD of Ubuntu 12.04 LTS, and try using bluetooth from there.  My guess is that there's a small software problem, and running from fresh software will clear it up. 

Instead of creating the LiveCD, I just upgraded my system. I've not had a problem before with upgrades and I was planning to upgrade anyway. But that turned out to be a mistake. The upgrade went through without problems (except that I had to uninstall skype) but after the restart wireless also doesn't work. (My mac and phone are able to connect fine). I see "device not managed" in the UI. Bluetooth still doesn't work. I also re-installed the system76 drivers after the upgrade. Didn't help.

I gave up on using the laptop for a while but just filed a support ticket on system76 website today. Hopefully I hear back soon.I'll update once I get things fixed.

---

