---
title: "Checking for updates regularly"
date: 2012-10-12
forum: Server Platforms
---

### Post by martijntje on 2012-10-12
I am trying to monitor for updates for all of our servers automatically. We have a script that runs /usr/lib/update-notifier/update-motd-updates-available regularly to see if anything needs to be updated.

In addition to this, cron-apt has been installed, so that repositories are updated every night.

However, the script never shows anything new, until I login through SSH. It will then show all the updates and from that moment the monitoring script will pick them up.

Can anybody tell me what the login does that I have not done yet?

---

