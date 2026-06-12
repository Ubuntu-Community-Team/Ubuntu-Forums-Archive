---
title: "rkhunter warnings"
date: 2012-03-21
forum: Server Platforms
---

### Post by DanHorniblow on 2012-03-21
Hi, I have a VPS running Ubuntu 10.04 LTS.

It is a email / web server that I have setup from following this tutorial [http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3]("http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3").

I have recently set up an email forward, so that any emails that go to the root account get forwarded to my personal one.

I keep getting emails from rkhunter saying "Please inspect this machine, because it may be infected."

I doubt it is infected has the server has very little usage and has not been running for that long. Never the less what are your thoughts, and how would I go about inspecting the machine?

Thanks Dan

---

### Post by jonobr on 2012-03-22
Hello


Just guessing at this one..... But if you run rkhunter the way it installs you will get false positives.
You have to tune your setup to compensate for these false positives.

My guess (and its a guess ) is that the automated execution is showing a positive and notifying you.

You can check by manually running rkhunter and seeing if you get any hits back.

[Here is ]("http://www.faqforge.com/linux/reconfigure-rkhunter-to-avoid-false-positive-warninngs-on-debian-5-0/") a note on false positives.

---

