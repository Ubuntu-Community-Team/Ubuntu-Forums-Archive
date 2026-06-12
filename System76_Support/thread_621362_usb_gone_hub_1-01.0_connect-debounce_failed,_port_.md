---
title: "usb gone: hub 1-0:1.0: connect-debounce failed, port 8 disabled"
date: 2007-11-23
forum: System76 Support
---

### Post by ajlewis2 on 2007-11-23
I am running Feisty Ubuntu on a Darter.  I have never had a problem with usb until today.  I used the usb mouse several times this morning, then after the computer set for about an hour, I find that the mouse doesn't work.  It does work on my desktop.

usb sticks are working on the back and left side of the machine, but not on the right side usb.

The machine boots very slowly including extreme slowness in the post prior to seeing the grub menu.  On one boot the grub menu actually drew slowly.  

dmesg shows this repeatedly and I see the same interspersed as the machine is booting.

[  257.988000] hub 1-0:1.0: connect-debounce failed, port 4 disabled
[  259.908000] hub 1-0:1.0: connect-debounce failed, port 7 disabled
[  261.828000] hub 1-0:1.0: connect-debounce failed, port 8 disabled

I'm worried that hardware is broken on this machine since it is running so poorly even prior to grub loading.

Anita

---

### Post by ajlewis2 on 2007-11-23
A cold reboot after leaving it off for a few minutes has got rid of the problem.  I'm still wondering what happened, but my panic has gone. :)

Anita

---

### Post by thomasaaron on 2007-11-23
Hi, Anita.

If that happens again, unplug your mouse and go to a terminal. Enter this command:
tail -f /var/log/syslog

This will create a sort of system monitor.

Then plug your mouse back in and watch the monitor. See if anything is added to the last line of the log displayed.

This will let you know if your USB port is seeing the mouse.

Best,
Tom

---

### Post by ajlewis2 on 2008-01-28
How weird.  I have this problem again this morning and was just about to post about it.  I saw that there was a previous post and wouldn't you know, it was mine.  I had forgotten about having the problem before.  LOL

I did look at syslog, Thomas, and the usb is not seeing the mouse, but just giving that error message. I'll do a cold reboot and see how it goes.  If it doesn't come back, then I'll return to let you know.  Otherwise, assume a cold reboot with a 1 minute wait resolves it.

Anita

---

### Post by ajlewis2 on 2008-01-28
It wasn't quite so easy this time.  After turning the machine off and waiting a minute, when I restarted, it stuck at the first screen that says Intel.  It didn't move forward to grub.  That has happened before.  I find I am unable to turn the machine off witht the on/off button.

Usually I just remove the battery and then replace it and it will start back up. This time I tried using the thing to choose whether to boot from hard drive or cdrom.  I got a light blue background on the screen and eventually got to choose.  It then booted and gave me the message about the connect-debounce on 3 ports.  

So, I restarted and got the stuck on Intel situation. This time I removed the battery and then restarted.  The usb is back now.  

Anita

---

### Post by thomasaaron on 2008-01-28
You should be able to turn the machine off by holding the power button down for a while. But removing the battery to kill it is going to mess something up.

Does this problem occur when you boot with NOTHING in the USB ports? I'm just wondering if something is confusing it.

You might also try re-setting the cmos. Remove the battery and a/c adapter. On the bottom of the computer (approximately beneath the left touchpad button) is a little hole with a symbol beside it. The symbol looks like two arrows pointing towards a dot. Put a paperclip in the hole and depress the cmos reset switch for about 15 seconds. Then, re-attach your battery / a/c adapter and reboot.

---

### Post by ajlewis2 on 2008-01-28
> **thomasaaron said:**
> You should be able to turn the machine off by holding the power button down for a while. But removing the battery to kill it is going to mess something up.


I have tried holding the button down for a very long time and it doesn't turn off when it is stuck at the Intel logo for me.  

> 
Does this problem occur when you boot with NOTHING in the USB ports? I'm just wondering if something is confusing it.

I rarely boot without the usb mouse in, but never boot with more than that plugged in.  The mouse problem has happened only twice, last time was Nov. 2007.  The problem with the machine getting stuck at the Intel logo has happened maybe 6 times.

> 
You might also try re-setting the cmos.

Are you saying I should do that now when it is working?  Or should I wait until the usb goes out again and remember to try it then.  LOL.  Today I didn't even remember that I had the problem before.  I wonder if I will remember what I'm supposed to do when it happens again.

Or are you saying to try this the next time it gets stuck at the logo?  In that case what do you suggest I do to turn off the machine when pressing the on/off button for a while does not turn it off?  I could leave it sitting on the black and white screen for a couple of days that it would take it to run out of juice with nothing going. :)

Thanks for the help, Thomas.  You are much appreciated.

---

### Post by thomasaaron on 2008-01-29
I would go ahead and reset the cmos. If you do it according to my directions, it won't hurt anything. Might even help.

---

### Post by ajlewis2 on 2008-01-29
This morning I had the opportunity to reset the CMOS.  I booted the computer around 5:15.  Mouse worked.  Around 5:45 I unplugged the AC and carried the computer to another location to watch (and do) an exercise video.  After the video was over (around 6:05) I used the mouse to close Caffeine and moved the computer back to the desk. I plugged the AC back in.   Sometime after 6:30 I went to do mail and found the mouse dead.  I have the syslog and will trim it to that general time frame to see if there is something showing up.

So, I brought the system down and off.  I did the process of removing AC and battery and then resetting the CMOS.  If I don't have another incident, you will not hear about it and can assume that this helped. But I will try to get back with anything significant in the logs.

Anita

---

### Post by ajlewis2 on 2008-01-29
Here is the log from around the time when the usb went out.  It doesn't tell me much, but maybe someone else will see something here. I took out the date and the hostname just to make the lines shorter for viewing.  --Anita
=============



05:13:00 avahi-daemon[5720]: Server startup complete. Host name is.local. Local service cookie is 4169405013.
05:13:01 kernel: [   32.308000] ADDRCONF(NETDEV_UP): eth0_rename: link is not ready
05:13:01 /usr/sbin/cron[5845]: (CRON) INFO (pidfile fd = 3)
05:13:01 /usr/sbin/cron[5846]: (CRON) STARTUP (fork ok)
05:13:01 udevd-event[4427]: rename_netif: error changing net interface name eth0_rename to eth1: Device or resource busy
05:13:01 /usr/sbin/cron[5846]: (CRON) INFO (Running @reboot jobs)
05:13:01 kernel: [   32.784000] ADDRCONF(NETDEV_UP): eth0_rename: link is not ready
05:13:01 avahi-daemon[5720]: Joining mDNS multicast group on interface eth0_rename.IPv4 with address 192.168.1.47.
05:13:01 avahi-daemon[5720]: New relevant interface eth0_rename.IPv4 for mDNS.
05:13:01 avahi-daemon[5720]: Registering new address record for 192.168.1.47 on eth0_rename.IPv4.
05:13:02 kernel: [   33.908000] ADDRCONF(NETDEV_CHANGE): eth0_rename: link becomes ready
05:13:04 avahi-daemon[5720]: Registering new address record for fe80::218:deff:fe28:b622 on eth0_rename.*.
05:13:05 kernel: [   36.316000] [drm] Initialized drm 1.1.0 20060810
05:13:05 kernel: [   36.324000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
05:13:05 kernel: [   36.328000] [drm] Initialized i915 1.6.0 20060119 on minor 0
05:13:13 kernel: [   44.600000] eth0_rename: no IPv6 routers present
05:17:01 /USR/SBIN/CRON[6325]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
05:27:31 kernel: [  903.012000] ipw3945: association process canceled
05:52:54 -- MARK --
06:03:34 anacron[6377]: Anacron 2.3 started on 2008-01-29
06:03:34 anacron[6377]: Will run job `cron.daily' in 5 min.
06:03:34 anacron[6377]: Jobs will be executed sequentially
06:03:36 kernel: [ 3067.756000] hub 4-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
06:03:36 kernel: [ 3067.756000] usb 4-2: USB disconnect, address 2
06:03:36 hcid[5743]: HCI dev 0 down
06:03:36 hcid[5743]: Stopping security manager 0
06:03:36 hcid[5743]: Device hci0 has been disabled
06:03:36 hcid[5743]: HCI dev 0 unregistered
06:03:36 hcid[5743]: Unregister path: /org/bluez/hci0
06:03:36 hcid[5743]: Device hci0 has been removed
06:03:36 kernel: [ 3068.064000] usb 1-2: USB disconnect, address 2
06:03:39 kernel: [ 3070.244000] hub 2-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
06:03:39 kernel: [ 3071.172000] hub 2-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
06:03:40 kernel: [ 3072.100000] hub 2-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
06:03:41 kernel: [ 3073.028000] hub 2-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
06:03:43 kernel: [ 3074.948000] hub 2-0:1.0: connect-debounce failed, port 8 disabled
06:03:46 kernel: [ 3077.404000] hub 2-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
06:03:47 kernel: [ 3078.332000] hub 2-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
06:03:49 kernel: [ 3080.364000] hub 2-0:1.0: connect-debounce failed, port 4 disabled
06:03:51 kernel: [ 3082.284000] hub 2-0:1.0: connect-debounce failed, port 7 disabled
06:03:52 kernel: [ 3084.208000] hub 2-0:1.0: connect-debounce failed, port 8 disabled
06:03:55 kernel: [ 3086.440000] hub 2-0:1.0: connect-debounce failed, port 1 disabled
06:03:57 kernel: [ 3088.360000] hub 2-0:1.0: connect-debounce failed, port 4 disabled
06:03:59 kernel: [ 3090.284000] hub 2-0:1.0: connect-debounce failed, port 7 disabled
J

---

### Post by thomasaaron on 2008-01-30
OK. So that is BEFORE resetting the cmos, right?
If so, let's see if it happens again.

---

