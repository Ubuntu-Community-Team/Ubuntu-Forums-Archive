---
title: "Broke server during upgrade."
date: 2010-07-16
forum: Server Platforms
---

### Post by Insane_Machine on 2010-07-16
Hello everyone,

I was upgrading my server(32bit running ubuntu-server) from 9.04. I upgraded to 9.10, everything worked well. Then I upgraded to 10.04 however after downloading packages and halfway through installing them, I was disconnected from SSH, I was getting timed out on both the default and port 9004 that was created during the upgrade.

I checked the router after an hour or two, and the computer did not have an IP anymore. I hard rebooted it at this point, but it still did not come back online. 

I would have hooked up a keyboard and mouse to it, however I think my video card fried on it, i can't get signal on my LCD(power save). My question is what would the best way to go about getting it back and working.

---

### Post by ruffEdgz on 2010-07-16
The first thing I would do is get a Ubuntu LiveCD, pop it into the CD/DVD ROM drive, boot up the LiveCD environment and see if I mount and read the logs from the hard drive. 

If you could get some of that information (/var/log/messages, /var/log/kern.log, etc....), read it yourself or place some of it here, then that would be a better way to go with this problem.

Upgrading is never fun or easy but I hope nothing was perminently damaged on the system during the upgrade.

---

### Post by Insane_Machine on 2010-07-16
Could I SSH into the LiveCD distro?

---

### Post by ruffEdgz on 2010-07-16
You possibly could but you will still need to get it past the startup screen and tell it to load up the live CD.

I know the live CD will have a network but I'm not sure if they have sshd on. Might have to get back to you on that one.

If someone else knows if sshd is on when you boot into a live CD, that would be nice as well :D

---

### Post by Insane_Machine on 2010-07-19
Ok, I got my hands on a 7800GT and threw it in the server. Problem was that the upgrade stopped halfway through and the networking never came back on. After doing do-release-upgrade again, everything updated. Now it says i'm 10.04.

Now i've got image, but I have another problem on my hands. When it boots I get fuzzy/corrupted graphics. In BIOS it is clear, but once the splash screen starts i get corruption leading to alternating solid black and white lines. If I boot in recovery mode, it remains text, but all the text is fuzzy once it gets past grub. 

Anyone have any ideas on what to try?

---

### Post by Insane_Machine on 2010-07-20
No one has an idea of what to look into?

---

