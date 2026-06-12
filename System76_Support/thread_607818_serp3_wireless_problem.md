---
title: "serp3 wireless problem"
date: 2007-11-09
forum: System76 Support
---

### Post by deeGraYve on 2007-11-09
I have the following problem: sometimes when my wireless connection disappears (or at least that is what the applet says) it asks me for the wep key again and never turns back on, furthermore once it happens I am not able to run neither system monitor or even shell to check on what's happening, it simply won't start. the only way to get rid of it is to switch the power off (even Ctrl+Alt+Bckspc just hangs...as in it tries to restart but never finishes it - it can go for 30mins)
I tried to use the switch on the front panel, but once the applet starts slowing the machine - it doesn't even repsond to switch anymore.
any ideas on what can be causing that?

---

### Post by thomasaaron on 2007-11-09
When your wireless disconnects, make not of the exact time according to the clock in the upper right of your monitor.

Once you've rebooted run this command:
cat /var/log/messages > ~/Desktop/messages.txt

Then email me at support with the time and the file that the command created on your Desktop.

Best,
Tom

---

### Post by steveneddy on 2007-11-09
Hardware clock issues again, Thomas?

---

### Post by thomasaaron on 2007-11-09
No, it's just that it helps to know what time the failure occured when looking through the logs.

Otherwise, it leaves too much to my imagination.

---

