---
title: "Quick 6.06.1 LTS security updates question"
date: 2007-12-07
forum: Server Platforms
---

### Post by twill30 on 2007-12-07
Hi - installed 6.06.1 about 4 weeks ago and have been running the update, upgrade and dist-upgrade commands when prompted by Ubuntu's security site.

The thing I'm slightly confused about is whether the Ubuntu guys release ALL the necessary security updates into the repositories (for standard server packages such as Apache, OpenSSH etc) or whether you still have to grab them from elsewhere. For example:

Just ran an update etc and now see:

Apache 2.0.55-4ubuntu2.2
OpenSSH 4.2p1-7ubuntu3.1

But when I go to the Apache and OpenSSH sites I see recommendation to run Apache 2.0.61 and OpenSSH 4.7 -- these versions have obviously pushed on a little since the ones 6.06.1 LTS is installing on running update and upgrade.

Should I be looking elsewhere to pull things right up to date or can I rest assured that anything that's considered necessary for this particular release of Ubuntu will be included in the main repositories?

Thanks for your help!

---

### Post by p_quarles on 2007-12-07
You're safe. The long-term support version will continue to get *necessary* security upgrades until its end-of-life date (which is three years away for the server edition). 

You *will* see discrepancies between Ubuntu packaged versions and source code security updates. Vulnerabilities will be patched in both, but the patch applied to the source code may simply not work correctly with the Ubuntu package.

To keep track of what's being done, you can go to launchpad.com (the Ubuntu bug-tracking/development site) and look at the open cases for Ubuntu 6.06. Like I say, I don't think you have anything to worry about, but with security, it's always best to keep yourself informed.

---

### Post by twill30 on 2007-12-08
Thanks for the helpful reply. We spent ages deciding which server platform to opt for and went for 6.06 because of the long term support (we don't wish to spend ages each week searching about for updates and patches etc, and this version makes it easy).

It's great to have a forum where members seem to genuinely care about others. Thanks again!

---

