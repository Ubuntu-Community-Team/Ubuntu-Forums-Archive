---
title: "Firefox won't display video frame after using twitter"
date: 2009-11-03
forum: System76 Support
---

### Post by cmnorton on 2009-11-03
I've entered a Firefox bug in launchpad [https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/473531](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/473531).

Basically, if I use Twittter under certain conditions -- I have not pinned the exact conditions down -- and then click on a link involving video and/or audio, Firefox will not display the video frame.

I'd love to know if there's a workaround for this.

My hardware is a Gazelle Ultra, running 9.10.

---

### Post by thomasaaron on 2009-11-04
That's kind of odd. Twitter is just a simple RAILS app. I wouldn't *think* it had anything to do with video. But I guess it is possible that Firefox has some bug that is crashing flash.

Run this command after video crashes...

cat /var/log/syslog | grep -i npviewer | grep -i segfault

If anything shows up, you know flash is crashing.

Question: Did you install 64-bit flash? If not, you are running 32-bit flash, and running this command (and rebooting) might help...

sudo apt-get install libadns1

---

### Post by cmnorton on 2009-11-05
Thanks. I'll keep looking at this. I did not install any separate flash program. I only installed the System76 driver(s).

---

