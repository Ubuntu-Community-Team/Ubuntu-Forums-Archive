---
title: "Bluetooth not working"
date: 2013-10-29
forum: System76 Support
---

### Post by Zukaro on 2013-10-29
I have a Bonobo Extreme running Ubuntu 13.04.

Recently I tried a workaround to get GmailChecker to work as I wanted a way of knowing when I got emails (the unity gmail thing doesn't do anything at all unless I'm already on the gmail site), so I tried this workaround: [http://www.webupd8.org/2013/05/how-to-get-systray-whitelist-back-in.html](http://www.webupd8.org/2013/05/how-to-get-systray-whitelist-back-in.html)

After doing this I can't use bluetooth AT ALL.  The icon no longer appears in the systray (all other icons appear just fine), and when I go to the bluetooth settings under the system settings it tells me that there's no bluetooth adapter.  I tried removing the ppa and then doing another

```
sudo-apt-get update && sudo apt-get upgrade
```

But the issue still persists.  I also tried reinstalling the System76 drivers as well as restoring them to factory defaults.  Aboslutely nothing works.

---

### Post by Zukaro on 2013-10-29
It seems to have started working again now (although I'm not sure what I did, if anything).

---

