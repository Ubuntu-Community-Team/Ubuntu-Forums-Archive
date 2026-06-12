---
title: "hylafax server loses network connectivity"
date: 2012-02-15
forum: Server Platforms
---

### Post by manthony121 on 2012-02-15
In my office, we have replaced our fax machine with a dedicated computer running Ubuntu 10.04 (Desktop) and hylafax, hooked up to an external serial modem.  Everything works well, except for an odd, intermittent problem: the fax server will occasionally lose its connection to the LAN.  As the server is headless, when it does this, there is no way to see what is going on in any log files.  It won't respond to pings, or attempts to connect via SSH.  I even tried running a port scan on it using nmap, and all (low) ports were reported as filtered.

The first two times it happened, I re-booted, and everything was back to normal.  When it happened a third time, I decided to hook up a monitor and keyboard to see what was going on.  The computer looked normal from the outside: no unusual disk activity, the modem status lights were correct.  No faxes were being received or sent. I called the modem from another phone line and got the expected fax connect tone.  In the time it took me to bring in a monitor and keyboard, it was talking to the network again.  I couldn't find anything in any log files to indicate that anything unusual had occurred, or what it was doing during its outage.

I can't say how long the connectivity was down, but it was at least 2 or 3 minutes from the time I noticed it, possibly longer.

Any idea what would cause this sort of behavior?  The only thing the box does is to run hylafax and ntpd, plus the other generic ubuntu desktop processes.  It is the only box on my network that is truly headless, with no monitor, keyboard, or mouse connected.

My next step is going to be to write a script to ping the box about once a minute, and let that run for a few days, to see how often and for how long the connectivity drops out.  If anyone has any other ideas, I'd love to hear them.

---

### Post by Vegan on 2012-05-21
I wonder if the machine is stable

is it possible to use another machine to test?

---

### Post by rubylaser on 2012-05-22
Personally, I'd take a look at these and see if anything turns up.
```
/var/log/daemon.log
/var/log/kern.log
/var/log/messages
/var/log/syslog
```

Also, I'd setup Smokeping to ping that box for you and email you if it goes down.

---

### Post by SeijiSensei on 2012-05-24
I'd stick a new network card into the machine and see if that fixes the problem.

---

### Post by koenn on 2012-05-24
OP is 3 months old, people.

FWIW, i'd look for power safe / idle timeout settings

---

### Post by manthony121 on 2012-07-03
Thanks to all who made suggestions.  It turns out there is an issue with some CPUs that causes this problem.  It seems to be related to lack of input from the mouse for long periods.  The whole system goes to sleep, and doesn't wake up until someone moves the mouse.

Rebooting with "nolapic_timer" and "nohz=off" on the boot options line eliminated the problem.

How do I tag the OP "SOLVED"?

---

### Post by rubylaser on 2012-07-03
> **manthony121 said:**
> Thanks to all who made suggestions.  It turns out there is an issue with some CPUs that causes this problem.  It seems to be related to lack of input from the mouse for long periods.  The whole system goes to sleep, and doesn't wake up until someone moves the mouse.

Rebooting with "nolapic_timer" and "nohz=off" on the boot options line eliminated the problem.

How do I tag the OP "SOLVED"?

Thanks for the update.  You can mark it solved like [this]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

