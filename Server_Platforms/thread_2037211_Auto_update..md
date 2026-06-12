---
title: "Auto update."
date: 2012-08-03
forum: Server Platforms
---

### Post by Xeneth on 2012-08-03
Issues with setting up an auto update.

I have been banging my head on this for some time, most can be found here:
[http://www.techsupportforum.com/forums/f64/crontab-is-not-liking-upgrade-650249.html](http://www.techsupportforum.com/forums/f64/crontab-is-not-liking-upgrade-650249.html)

Rundown is I cannot get my server to auto update.  Since I know next to nothing about scripting, I have simply tied a cron to do it, but I get an error.  This seems to be a known bug, so I am looking for alternatives. I even thought about a second server that does the updates and keeps the logs for all systems in my house, but that is a bit extreme.  I am hoping someone can help me out with this.  

And if you get into scripting, While I do want to learn, I have no exp. in python or any other languages. Just now learning bash scripting.

---

### Post by pqwoerituytrueiwoq on 2012-08-03
[https://help.ubuntu.com/10.04/serverguide/automatic-updates.html](https://help.ubuntu.com/10.04/serverguide/automatic-updates.html)

---

### Post by LHammonds on 2012-08-04
I setup my servers with a custom scripts to run the update/upgrade via a cron schedule.

Take a look in my sig for setting up an Ubuntu server and then find the post titled "APT Upgrade" to see how I do it.

I do a scripted upgrade so I can retain a log file as well as controlling exactly when the upgrades occur.  This helps with my Nagios server which monitors all my servers so it only reports unpatched systems "after" the point it should have already been updated.

LHammonds

---

### Post by HermanAB on 2012-08-04
Hmm, auto-update is also known as auto-screw-up...

It may be a good idea on a bug ridden Windows system where any update is usually an improvement, but on a Linux system, applying updates willy-nilly to a server is usually not a good idea.

---

### Post by LHammonds on 2012-08-05
For me, it is not so much about fixing bugs as it is closing known security holes.

The main problem with updates that I have seen in my short time with Linux was issues with grub updates causing systems to fail booting up.  But if you have a backup procedure in place, you should be able to restore if you cannot figure out how to fix it.

At my company, it is far worse letting a server go out of date due to not keeping up with patches than occasionally running into issues trying to keep the servers updated.  Basically failure due to inaction is worse than failure due to action.

If you have the manpower to scrutinize each patch for each server, that is awesome.  If you have test or backup systems you can run patches on 1st, even better.  But there are good reasons for auto-patching and good reasons for manual patching or not patching at all.  It depends on the situation and everyone needs to figure that out for themselves.

---

