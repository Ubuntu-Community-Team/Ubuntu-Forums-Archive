---
title: "kernel panics galore"
date: 2009-01-30
forum: System76 Support
---

### Post by Derath on 2009-01-30
I updated my system today, and while I don't remember everything that was updated, I do recall I believe it was restricted modules and pulseaudio were included in the update, either way, after shutting down and restarting much later, I am getting a LOT of random kernel panics (sometimes before kde starts, sometimes after).

I am attaching a log packet from a reboot after a few kernel panics.

panp4n
kde 4.1

---

### Post by thomasaaron on 2009-01-30
1. Run this command and then reboot.

sudo apt-get install linux-backports-modules-intrepid

2. If that doesn't fix it, go to System > Admin > System76 Driver (or wherever it is on Kubuntu) and click the Support tab and the Create button. Then post the log.tar file to this thread, and I'll have a look.

---

### Post by Derath on 2009-02-01
A couple notes on this, but first I did get it "fixed" I guess...

Round one: Installed backports, unfortunately because I didn't have source installed it wouldn't build the nvidia and vbox modules... tried completely removing and reinstalling backports, no error messages, when I rebooted though the nvidia and vbox modules failed to load and the system refused to start x.

Round two: Eventually x realized that something was wrong and I was able to get into x, when I did Update Manager yelled at me about some updates available, after installing the updates (which included another kernel update) and rebooted I got into kde again, unfortunately it didn't use the nvidia module (which did load in kernel just not in x) and several things yelled about not having desktop effects turned on (could have sworn I did have that turned on).

Round three: Heard about recent nvidia driver, check repos, and installed nvidia 180, restarted and seems like everything's working fine now.

Just thought I'd document what all I did.

---

