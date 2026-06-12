---
title: "PAN-V3 + Hardy Heron crashing"
date: 2008-12-28
forum: System76 Support
---

### Post by Jerturner on 2008-12-28
My PAN-V3 system running Hardy Heron has been experiencing kernel panics lately (at least since Thanksgiving).  I don't know of any behavior or program that causes the problem; it seems to happen under a lot of different circumstances-- using firefox, vlc, or even when the screen is locked.

I have attached the /var/log/messages & /var/log/syslog files from the most recent crash.

---

### Post by thomasaaron on 2008-12-29
I'm not seeing anything in the logs that indicates a kernel panic. Did you create the logs immediately after the panic?

Also, please describe exactly what you are seeing.

You also might want to try to install linux-backports-modules (might be linux-backports-modules-hardy), reboot, and see if that fixes it.

---

### Post by Jerturner on 2008-12-30
After the kernel panic I restarted, logged back in, and then copied the logs to a personal directly.  I have attached new logs from a crash this morning.

I think it is a kernel panic because the two rightmost LED's start blinking, I think they are the caps and scroll lock keys.  Everything freezes and becomes unresponsive.  Trying to ping the machine times out.

linux-backports-modules-hardy-generic was already installed.

---

### Post by thomasaaron on 2008-12-30
Here is the error that occurs before the panic...

> Dec 30 11:16:30 ubuntu kernel: [ 1982.656993] console-kit-dae[5614]: segfault at 0 rip 7f69174230b0 rsp 7fff203574c8 error 4
Dec 30 11:39:53 ubuntu -- MARK --
Dec 30 11:59:53 ubuntu -- MARK --
Dec 30 12:16:18 ubuntu syslogd 1.5.0#1ubuntu1: restart.

Googling it shows associations with Xen, apport, MythTV and some bit torrent clients. Does any of that ring a bell.

Preceding that message are some wlan logs that might be significant. So, wireless might be involved too.

Are you connecting to an "n" router?
Have you installed any other wireless management software?

---

### Post by Jerturner on 2008-12-30
> **thomasaaron said:**
> Here is the error that occurs before the panic...



Googling it shows associations with Xen, apport, MythTV and some bit torrent clients. Does any of that ring a bell.

Preceding that message are some wlan logs that might be significant. So, wireless might be involved too.

Are you connecting to an "n" router?
Have you installed any other wireless management software?

That error is from "kill -9"-ing an ssh connection.  I have was able to reproduce that and it is not present in my other logs following crashes.

My router is not n capable just b & g.

---

### Post by thomasaaron on 2008-12-31
OK. In that case, can you please make not of exactly when the crash happens so that I can better focus on the correct error messages?

I see this one:

> Dec 30 11:59:53 ubuntu -- MARK --
Dec 30 12:09:02 ubuntu /USR/SBIN/CRON[8128]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Dec 30 12:16:18 ubuntu syslogd 1.5.0#1ubuntu1: restart.

...which would appear to be related to some cron job.

In the meantime, try re-installing backports modules. I realize you have the latest version in there, but this sounds a lot like a previous issue we've dealt with, in which backports modules solved the issue. It can't hurt to try.

---

### Post by thomasaaron on 2008-12-31
Also, how large are your log files?

/var/log/syslog
/var/log/messages

There is a bug out there that causes incredibly large log files and freezes the system.

If it's happening to you, I'll dig deeper...

---

### Post by Jerturner on 2008-12-31
Re-installing the backports did not seem to help since I got another crash since then.  I have attached the log files again, the crash happened sometime between 12:20 and 12:40.

I have also attached output from ls -s /var/log in size.txt.

---

### Post by thomasaaron on 2008-12-31
Thanks.  Here is the only thing that occurs betwixt 12:20 and 12:40...

messages...
> Dec 31 12:20:47 ubuntu kernel: [   64.787848] UDF-fs: Partition marked readonly; forcing readonly mount
Dec 31 12:20:47 ubuntu kernel: [   64.822092] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'THE_FUGITIVE_RERELEASE', timestamp 2001/03/28 16:00 (1ed4)
Dec 31 12:21:24 ubuntu pulseaudio[6346]: protocol-native.c: Failed to push data into queue
Dec 31 12:46:58 ubuntu syslogd 1.5.0#1ubuntu1: restart.

syslog...
> Dec 31 12:20:00 ubuntu avahi-daemon[5275]: Registering new address record for fe80::213:e8ff:fe1c:5329 on wlan0.*.
Dec 31 12:20:00 ubuntu ntpd[6706]: Listening on interface #6 wlan0, fe80::213:e8ff:fe1c:5329#123 Enabled
Dec 31 12:20:09 ubuntu kernel: [   62.017602] wlan0: no IPv6 routers present
Dec 31 12:20:47 ubuntu NetworkManager: <debug> [1230744047.295060] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_THE_FUGITIVE_RERELEASE'). 
Dec 31 12:20:47 ubuntu kernel: [   64.787848] UDF-fs: Partition marked readonly; forcing readonly mount
Dec 31 12:20:47 ubuntu kernel: [   64.822092] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'THE_FUGITIVE_RERELEASE', timestamp 2001/03/28 16:00 (1ed4)
Dec 31 12:21:24 ubuntu pulseaudio[6346]: protocol-native.c: Failed to push data into queue
Dec 31 12:46:58 ubuntu syslogd 1.5.0#1ubuntu1: restart.

I could be wrong, but that sure looks to me like your dvd drive was mounted and started trying to play "The Fugitive Release" and then pulse audio choked and crashed your system.

If this is the case, pulse audio was notoriously crappy in Hardy. It is much improved in Intrepid. I'd back up and do a fresh install with the latest drivers.

Also, I believe "ls -s" provides file sizes in blocks, and I'm not exactly sure what a block translates to in bytes. I think you may have to set that with --block-size= but I'm not sure, as I never really use it. Could you go to your /var/log folder and right-click it and select properties. I want to rule out that other bug before calling this a pulse-audio bug.

---

### Post by adingo on 2008-12-31
Sounds similar to a problem I've been having on Intrepid and wireless.  I don't know if Hardy has a similar issue or not, but for what it's worth:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276990](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276990)

I have the problem with  2.6.27-7, it was fixed with -8, but came back with -9, apparently because not all the fixes in -8 made it into -9.

---

### Post by thomasaaron on 2008-12-31
Hi, adingo.

I don't think that is it. There's no "n" router with this one.

---

### Post by albinootje on 2008-12-31
> **Jerturner said:**
> My PAN-V3 system running Hardy Heron has been experiencing kernel panics lately (at least since Thanksgiving).  I don't know of any behavior or program that causes the problem; it seems to happen under a lot of different circumstances-- using firefox, vlc, or even when the screen is locked.

I have attached the /var/log/messages & /var/log/syslog files from the most recent crash.

I think it makes more sense after a kernel panic or kernel oops to look at 
```

/var/log/kern.log
/var/log/kern.log.0
/var/log/syslog.0

```
too.
It's quite possible that after a reboot the logfiles get rotated, at least it does on the VPS-es that I use.

---

### Post by Jerturner on 2008-12-31
Seems that /var/log contains 12.7 megabytes.  The block size for the file I gave you seems to be defaulting to 1k blocks.

As for the pulse-audio error, it seems to occur for me when starting vlc for the first time after powering on the laptop.  Triggering that error does not seem to result in a kernel panic but I can't say for sure.  Is there any way I can disable pulse-audio so that we could try to rule that out?

---

### Post by thomasaaron on 2008-12-31
You may be able to do it by just running...
> 
killall pulseaudio

If it's not pulseaudio, we have a real quandry, though, because I'm not seeing anything else in the log files in that time frame that indicate what the problem would be.

12.7 MB for the log files wouldn't be indicative of the other bug I was thinking of.

---

### Post by Jerturner on 2009-01-07
I have experienced a few crashes with no pulseaudio processes running & with the sound disabled.  

I am starting to think the problem could be related to the wireless driver.  When switching off the wireless, and either going with a wired connection or no connection, results in the system being its regular rock solid self.  Has anyone else had stability issues with the 3945abg Intel wireless card?  (It could be a different wireless card, I am not near the laptop to check at the moment).

---

