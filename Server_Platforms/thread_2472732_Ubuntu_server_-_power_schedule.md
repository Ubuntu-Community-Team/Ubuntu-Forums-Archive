---
title: "Ubuntu server - power schedule"
date: 2022-03-10
forum: Server Platforms
---

### Post by uipojehdx on 2022-03-10
I run a headless ubuntu server in my home. It has Jellyfin and Roon on it but generally its not in use overnight. To save a bit on energy, I would like to power it down at 00.00 (12pm) and have it turn on again at 7am. Is there an easy way to do this?

---

### Post by TheFu on 2022-03-10
Powering down is easy. Put the /usr/sbin/shutdown command into root's crontab. I suspend a laptop nightly a few minutes after the nightly backups for it finish. If you need help with cron, ask.

I don't know how to power it up, unless your BIOS has a method.  Wake-on-LAN from another system could be scheduled. [https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan) Perhaps your wifi-connected cell phone can do it in the morning?  OTOH, if you use Jellyfin to record TV, which I do, if the phone isn't home and sending commands, then the recordings would all fail, since the computer wasn't running.  Wake-on-LAN is extremely system dependent and does require extra software. If you have some other, low-power computer that is on all the time, perhaps a raspberry pi is one of your media players, then you could have the pi send the wake-on-lan packet to the jellyfin system.

So ... my laptop is still suspended now because I haven't caused it to wake up yet today. It may not be used at all today, so anything it was expected to perform automatically (nothing but to backup and suspend), will not happen.

Google found this method to wake: [https://askubuntu.com/questions/113379/suspend-and-wake-pc-at-certain-time](https://askubuntu.com/questions/113379/suspend-and-wake-pc-at-certain-time)  I've never tried it. Most of my systems are doing things automatically around the clock. Some of these power-related things are different from release to release, so testing will be necessary. There is lots of information and caveats in the **rtcwake** manpage.

Good question. Thanks.

---

### Post by uipojehdx on 2022-03-10
Thanks for the reply. I have been reading around for a bit and was getting confused.

> **TheFu said:**
> If you need help with cron, ask.

I need help with cron! What command do you use?

Also, I do have a rpi running pi-hole, so that could be a possiblity. Also there is a Synology NAS as an option too - this is shutdown now over night.

---

### Post by TheFu on 2022-03-10
What, exactly, confuses you about cron?  I don't want to waste time covering things that you've already learned.  There is an ubuntu how-to for cron. Have you seen that?
Cron works 99% the same on all Unix-like OSes.  Don't confuse **cron** and **anacron**. Those are different. That is a common issue, but when you want to have things run at very specific times, anacron is useless. Anacron resolution is 1 day. Anything less than that is best effort and may not actually happen.  With cron, 1 minute is the resolution ... if you need something to start 34 seconds after a minute, then add a sleep 34s statement to the script to cause the delay. There might be a 1 second startup ( 0.25 sec delay could happen on a very busy machine or one with RAM over-committed while swapping happens).  
On an extremely busy machine, cron may not run at all. I've only seen this on undersized servers over 25 yrs ago, so while it is still part of the spec to not run crontabs on slammed machines, it really doesn't happen these days. 
MTAs (sendmail, postfix, exim) don't run under the same slammed machine conditions either.  The MTA issue is more common, but I haven't noticed it since the 1990s either.  Does it really matter if email is delayed 20 minutes when a server is beyond busy? Nope. 20 minutes would be exceptionally long time for a server to be slammed these days. It just doesn't happen.

Since this morning, I tested the **rtcwake** command on a Core i5 laptop here. It worked, at least from suspend.  I tested 120 and 600 seconds for the wake after a pm-suspend.  There's a way to have the command use times and dates instead of seconds. I didn't test that. The manpage seems clear. I didn't alter the EFI BIOS settings at all.  There was a write error with the rtcwake command, but it still worked, so I don't know what the issue was. I did use sudo, which is required because the permissions on the rtc0 device are 
```
[COLOR="#FF0000"]crw[/COLOR]------- 1 [COLOR="#FF0000"]root[/COLOR] root 249, 0 Feb 12 12:26 /dev/rtc0
```
Only root can write to it or read from it.

---

### Post by LHammonds on 2022-03-11
I agree with TheFu.  Use crontab to cleanly shutdown your services and server.  The startup is very dependent on what you have.  Check BIOS settings to see if there is a poweron capability to schedule it daily.   If not but your PC powers up when you initially plug in power, you might want to use a smartplug between your server and outlet and configure it to turn off/on when you want the server awake...but this can be problematic if you server did not shutdown...it would be like unplugging a running server which is never good.   The wake-on-lan (if you have that option and have it enabled) requires something else running to tickle it on the schedule you want it tickled which adds another layer of complexity and potential of failure (e.g. not having a running server during the day)

I have this at the top of my crontab files on every server as a reminder of correct syntax:

```

# Crontab SYNTAX:
#       __________ Minute (0-59)
#      / _________ Hour (0-23)
#     / /  _______ Day Of Month (1-31)
#    / /  /   ____ MONth (1-12)
#   / /  /   /   _ Day Of Week (0-7) (Sun = 0 or 7)
#  / /  /   /   /  -------------------------------------------------------------
# m h dom mon dow  command <arguments> > /dev/null 2>&1
```

I don't call the shutdown command directly on my servers (I have a lot of them).  I call a commonly-named bash script such as "shutdown.sh" or "reboot.sh" that has all the commands inside it to cleanly shutdown the various services which are different on each server.

LHammonds

---

### Post by TheFu on 2022-03-11
I'm not certain that systems will use **rtcwake** if the **shutdown** command is used.  I know that suspend is what I tested, not a full shutdown, but that's because the test system for this required 2FA to unlock the disk at boot, but not from suspend. I've never looked at hibernation due to security risks/failures of that method.  

Again, the caveats for rtcwake are in the manpage.

---

### Post by volkswagner on 2022-03-13
You may want to look into ACPI Wake.
I remember using it years ago with MythTV.
[https://www.mythtv.org/wiki/ACPI_Wakeup](https://www.mythtv.org/wiki/ACPI_Wakeup)

---

### Post by uipojehdx on 2022-03-15
Thanks for the replies. 

> ubuntu how-to for cron

This was helpful, I did have a read through. I have just edited the cron tab file adding. 05 00 * * * /sbin/shutdown -h now. I tested it beforehand with a different time which shut the server down. I then had a look in the bios of the gigabyte motherboard and there is a power on by alarm setting. I can select a time, so i have set for 7am. I will report back!

---

