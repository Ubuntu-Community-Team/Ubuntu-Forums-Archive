---
title: "apcupsd not waking suspended server when battery loses charge"
date: 2013-07-01
forum: Server Platforms
---

### Post by finite9 on 2013-07-01
Running Ubuntu server 13.04, with APC500ES connected using USB cable.

apcupsd works fine when server is up and running.  As soon as battery is almost drained, it shuts down server.

However, I want to pm-suspend my server and only wake it when needed.  When I lose power during pm-suspend, and battery gets drained, server simply loses power, triggering an (EXT4-fs] recovery on next boot according to dmesg.

My concern is corrupt filesystems, and I have a RAID-0 plus a RAID-1 array that I do not want to suffer during powerloss.

Anyone know if apcupsd can be configured to wake up server to be able to do clean shutdown before battery is fully drained?

---

### Post by SeijiSensei on 2013-07-01
Take a look at the apccontrol script.  It allows you to customize how various events are handled.  You might need to write a small shell to do what you want.  I think all you need to do is point the SHUTDOWN environment variable to your script rather than having it run /sbin/shutdown as it does by default.

---

### Post by CharlesA on 2013-07-01
> **SeijiSensei said:**
> Take a look at the apccontrol script.  It allows you to customize how various events are handled.  You might need to write a small shell to do what you want.  I think all you need to do is point the SHUTDOWN environment variable to your script rather than having it run /sbin/shutdown as it does by default.

That should do it. I thought there was a setting that allowed the machine to turn back on after the battery was sufficiently charged.

EDIT: With that being said, I think it would be a better idea to have the machine power off entirely, then turn back on after the battery is sufficiently charged. This might help:
[http://askubuntu.com/questions/37097/can-apc-ups-wake-powered-off-machine-up-when-ac-power-is-back](http://askubuntu.com/questions/37097/can-apc-ups-wake-powered-off-machine-up-when-ac-power-is-back)

---

### Post by rubylaser on 2013-07-01
I believe the OP is saying that the computer is in pm-suspend state when it loses power and the APC takes over.  He wants the computer to "wakeup" when the power is lost to power down, and then wakeup when power is restored.  Frankly, if power is that much of an issue, I'd rather have my computer be either off or on so that apcupsd can safely shut it down (especially with a RAID0 array involved).  I'd leave it off when you aren't using it, and consider wake on LAN to wake the computer up when it's needed.

---

### Post by finite9 on 2013-07-02
Thanks rubylaser (you understood my request).  I sort of suspected this.  I use Wake On LAN/WAN from my mobile phone, which works great, so that is not an issue.  I'll have to reconfigure my BIOS to stop it turning on automatically every morning.

But having said that, really, I'm kind of surprised that apcupsd doesn't take this into account automatically.  Looks like a feature request needs to be sent off.

---

### Post by CharlesA on 2013-07-02
> **finite9 said:**
> Thanks rubylaser (you understood my request).  I sort of suspected this.  I use Wake On LAN/WAN from my mobile phone, which works great, so that is not an issue.  I'll have to reconfigure my BIOS to stop it turning on automatically every morning.

But having said that, really, I'm kind of surprised that apcupsd doesn't take this into account automatically.  Looks like a feature request needs to be sent off.

You could try their mailing lists: [http://www.apcupsd.com/](http://www.apcupsd.com/)

But their last stable release was back in 2011, so I dunno if they would even be able to implement this.

---

### Post by SeijiSensei on 2013-07-02
I think they'd probably suggest you handle this by writing a script to do what you want as I suggested before.

---

