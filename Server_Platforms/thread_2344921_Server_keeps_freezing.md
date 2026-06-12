---
title: "Server keeps freezing"
date: 2016-11-29
forum: Server Platforms
---

### Post by philled on 2016-11-29
I have a Ubuntu 16.04.1 LTS server which is acting as a KVM virtualisation host and it keeps freezing. It seems to be happening every few days. As a Linux server and an Ubuntu LTS it should never, ever, ever freeze - we're not talking Windows here after all! The server stays on but I can't SSH to it and when I go and see it in the server cupboard the screen isn't on and won't come on with a few taps of the keyboard. I have to force power off and restart it, which is not good.

After today's freeze I checked syslog and got this. It looks like it froze at Nov 29 02:10 until I force rebooted at Nov 29 19:18. I've highlighted a line in red which looks a bit suss but don't know if that's related to this or not.

```
Nov 28 11:39:01 hyv2 CRON[7056]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 28 12:09:01 hyv2 CRON[7157]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 28 12:17:01 hyv2 CRON[7210]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 28 12:39:01 hyv2 CRON[7247]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 28 13:09:01 hyv2 CRON[7335]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 28 13:17:01 hyv2 CRON[7391]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 28 13:39:01 hyv2 CRON[7426]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 28 14:09:01 hyv2 CRON[7510]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 28 14:17:01 hyv2 CRON[7563]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 28 14:39:01 hyv2 CRON[7606]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 28 15:09:01 hyv2 CRON[7695]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 28 15:17:01 hyv2 CRON[7750]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 28 15:39:01 hyv2 CRON[7789]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 28 15:42:01 hyv2 CRON[7835]: (root) CMD (   test -x /etc/cron.daily/popularity-contest && /etc/cron.daily/popularity-contest --crond)
Nov 28 16:09:01 hyv2 CRON[7845]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 28 16:17:01 hyv2 CRON[7898]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 28 16:39:01 hyv2 CRON[7919]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 28 17:09:01 hyv2 CRON[7968]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 28 17:17:01 hyv2 CRON[8012]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 28 17:39:01 hyv2 CRON[8019]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 28 18:09:01 hyv2 CRON[8076]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 28 18:17:01 hyv2 CRON[8122]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 28 18:39:01 hyv2 CRON[8137]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 28 19:09:01 hyv2 CRON[8204]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 28 19:17:01 hyv2 CRON[8250]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 28 19:39:01 hyv2 CRON[8268]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 28 19:41:28 hyv2 systemd[1]: Starting Cleanup of Temporary Directories...
Nov 28 19:41:28 hyv2 systemd-tmpfiles[8313]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
Nov 28 19:41:28 hyv2 systemd[1]: Started Cleanup of Temporary Directories.
Nov 28 20:09:01 hyv2 CRON[8362]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 28 20:17:01 hyv2 CRON[8416]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 28 20:39:01 hyv2 CRON[8453]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 28 21:09:01 hyv2 CRON[8538]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 28 21:17:01 hyv2 CRON[8602]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 28 21:39:01 hyv2 CRON[8642]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 28 22:09:01 hyv2 CRON[8689]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 28 22:17:01 hyv2 CRON[8733]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 28 22:39:01 hyv2 CRON[8777]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 28 23:09:01 hyv2 CRON[8870]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 28 23:17:01 hyv2 CRON[8923]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 28 23:39:01 hyv2 CRON[8955]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
[COLOR=#ff0000]Nov 28 23:44:56 hyv2 org.a11y.atspi.Registry[3019]: XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server "localhost:10.0"[/COLOR]
[COLOR=#ff0000]Nov 28 23:44:56 hyv2 org.a11y.atspi.Registry[3019]:       after 124 requests (124 known processed) with 0 events remaining.[/COLOR]
Nov 28 23:44:59 hyv2 systemd[1]: Stopping User Manager for UID 1000...
Nov 28 23:44:59 hyv2 systemd[2821]: Reached target Shutdown.
Nov 28 23:44:59 hyv2 systemd[2821]: Stopped target Default.
Nov 28 23:44:59 hyv2 systemd[2821]: Stopped target Basic System.
Nov 28 23:44:59 hyv2 systemd[2821]: Stopped target Timers.
Nov 28 23:44:59 hyv2 systemd[2821]: Stopped target Sockets.
Nov 28 23:44:59 hyv2 systemd[2821]: Stopped target Paths.
Nov 28 23:44:59 hyv2 systemd[2821]: Starting Exit the Session...
Nov 28 23:44:59 hyv2 systemd[2821]: Received SIGRTMIN+24 from PID 9016 (kill).
Nov 28 23:44:59 hyv2 systemd[1]: Stopped User Manager for UID 1000.
Nov 28 23:44:59 hyv2 systemd[1]: Removed slice User Slice of phill.
Nov 29 00:09:01 hyv2 CRON[9064]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 29 00:17:01 hyv2 CRON[9116]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 29 00:39:01 hyv2 CRON[9146]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 29 01:09:01 hyv2 CRON[9246]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 29 01:17:01 hyv2 CRON[9298]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 29 01:39:01 hyv2 CRON[9329]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 29 02:09:01 hyv2 CRON[9432]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && /usr/lib/php/sessionclean)
Nov 29 02:10:01 hyv2 CRON[9477]: (root) CMD (/usr/local/bin/phill/call_backup_vms_daily.sh)
Nov 29 02:10:01 hyv2 systemd[1]: Started Device-mapper event daemon.
Nov 29 02:10:02 hyv2 kernel: [110638.876057] FS-Cache: Loaded
Nov 29 02:10:02 hyv2 kernel: [110638.935293] FS-Cache: Netfs 'cifs' registered for caching
Nov 29 02:10:02 hyv2 kernel: [110638.935440] Key type cifs.spnego registered
Nov 29 02:10:02 hyv2 kernel: [110638.935467] Key type cifs.idmap registered
Nov 29 19:18:46 hyv2 rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="1477" x-info="http://www.rsyslog.com"] start
Nov 29 19:18:46 hyv2 rsyslogd-2222: command 'KLogPermitNonKernelFacility' is currently not permitted - did you already set it via a RainerScript command (v6+ config)? [v8.16.0 try http://www.rsyslog.com/e/2222 ]
Nov 29 19:18:46 hyv2 rsyslogd: rsyslogd's groupid changed to 108
Nov 29 19:18:46 hyv2 rsyslogd: rsyslogd's userid changed to 104
Nov 29 19:18:46 hyv2 systemd-modules-load[455]: Inserted module 'iscsi_tcp'
Nov 29 19:18:46 hyv2 loadkeys[451]: Loading /etc/console-setup/cached.kmap.gz
Nov 29 19:18:46 hyv2 systemd[1]: Started Set console keymap.
Nov 29 19:18:46 hyv2 systemd[1]: Started Create Static Device Nodes in /dev.
Nov 29 19:18:46 hyv2 systemd[1]: Starting udev Kernel Device Manager...
Nov 29 19:18:46 hyv2 systemd-modules-load[455]: Inserted module 'ib_iser'
Nov 29 19:18:46 hyv2 systemd[1]: Started Load Kernel Modules.
Nov 29 19:18:46 hyv2 systemd[1]: Mounting FUSE Control File System...
Nov 29 19:18:46 hyv2 systemd[1]: Starting Apply Kernel Variables...

```
Any ideas how I can troubleshoot this to stop it happening?

---

### Post by SeijiSensei on 2016-11-29
Have you run memtest?

I don't see anything in the log that helps.  There's just a big void between the entry for  "Key type cifs.idmap registered" and your rebooting of the machine.  Do you mount a remote filesystem with CIFS?  What if you disable that?

---

### Post by alexjpowell on 2016-11-30
Does it freeze at the same time? After the same period of uptime?
If you're using intel graphics, maybe try here: [https://wiki.archlinux.org/index.php/intel_graphics#X_freeze.2Fcrash_with_intel_driver](https://wiki.archlinux.org/index.php/intel_graphics#X_freeze.2Fcrash_with_intel_driver)

---

### Post by gordintoronto on 2016-11-30
Please describe the hardware: motherboard, CPU, RAM, GPU.

My system would freeze from time to time until I disabled ACPI. Gigabyte MA770T-UD3P motherboard.

---

### Post by tinmanb on 2016-12-31
hi all and belated merry christmas
Happy new year...

i am new to the forum and been using ubuntu server for the past 10months. I have a similar issue...
running ubuntu 16.04.1 LTS Server on an HP Media Center m7640n pc with AMD Athlon(tm) 64 X2 Dual Core Processor 5000+, 2 cores. Based on the specs from HP , it has ASUS A8M2N-LA MB, GeForce 6150 LE Chipset, 2GB of ram and integrated graphics.  Did some research and upgraded the kernel to 4.9.0-040900rc3-generic on x86_64. The Server keeps freezing for and a pc restart (pressing the Power button off then on) to get it running again.
Attached is the system log just prior to the freeze:
```
Dec 30 21:12:55 Battist-UbuntuWeb systemd[1]: snapd.refresh.timer: Adding 2h 44min 49.749075s random time.
Dec 30 21:12:55 Battist-UbuntuWeb systemd[1]: apt-daily.timer: Adding 5h 10min 3.020641s random time.
Dec 30 21:13:03 Battist-UbuntuWeb kernel: [ 5770.340155] usb 1-8: reset high-speed USB device number 2 using ehci-pci
Dec 30 21:13:32 Battist-UbuntuWeb systemd[1]: Time has been changed
Dec 30 21:13:32 Battist-UbuntuWeb systemd[1]: snapd.refresh.timer: Adding 3h 25min 51.389035s random time.
Dec 30 21:13:32 Battist-UbuntuWeb systemd[1]: apt-daily.timer: Adding 9h 56min 25.277810s random time.
Dec 30 21:13:56 Battist-UbuntuWeb kernel: [ 5819.492056] usb 1-8: reset high-speed USB device number 2 using ehci-pci
Dec 30 21:14:08 Battist-UbuntuWeb systemd[1]: Time has been changed
Dec 30 21:14:08 Battist-UbuntuWeb systemd[1]: snapd.refresh.timer: Adding 1h 49min 805.839ms random time.
Dec 30 21:14:08 Battist-UbuntuWeb systemd[1]: apt-daily.timer: Adding 5h 6min 13.443475s random time.
Dec 30 21:14:45 Battist-UbuntuWeb systemd[1]: Time has been changed
Dec 30 21:14:45 Battist-UbuntuWeb systemd[1]: snapd.refresh.timer: Adding 3h 4min 25.286528s random time.
Dec 30 21:14:45 Battist-UbuntuWeb systemd[1]: apt-daily.timer: Adding 9h 37min 43.777826s random time.
Dec 30 21:14:50 Battist-UbuntuWeb kernel: [ 5864.548195] usb 1-8: reset high-speed USB device number 2 using ehci-pci
Dec 30 21:15:21 Battist-UbuntuWeb systemd[1]: Time has been changed
Dec 30 21:15:21 Battist-UbuntuWeb systemd[1]: snapd.refresh.timer: Adding 2min 3.647862s random time.
Dec 30 21:15:21 Battist-UbuntuWeb systemd[1]: apt-daily.timer: Adding 2h 35min 35.656702s random time.
Dec 30 21:15:35 Battist-UbuntuWeb kernel: [ 5905.512056] usb 1-8: reset high-speed USB device number 2 using ehci-pci
Dec 30 21:15:57 Battist-UbuntuWeb systemd[1]: Time has been changed
Dec 30 21:15:57 Battist-UbuntuWeb systemd[1]: snapd.refresh.timer: Adding 1h 47min 31.904754s random time.
Dec 30 21:15:57 Battist-UbuntuWeb systemd[1]: apt-daily.timer: Adding 5h 34min 11.515811s random time.
Dec 30 21:16:18 Battist-UbuntuWeb kernel: [ 5944.420042] usb 1-8: reset high-speed USB device number 2 using ehci-pci
Dec 30 21:16:34 Battist-UbuntuWeb systemd[1]: Time has been changed
Dec 30 21:16:34 Battist-UbuntuWeb systemd[1]: snapd.refresh.timer: Adding 50min 5.509473s random time.
Dec 30 21:16:34 Battist-UbuntuWeb systemd[1]: apt-daily.timer: Adding 8h 44min 7.227365s random time.
Dec 30 21:16:53 Battist-UbuntuWeb kernel: [ 5975.140083] usb 1-8: reset high-speed USB device number 2 using ehci-pci
Dec 30 21:17:05 Battist-UbuntuWeb CRON[5038]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 30 21:17:10 Battist-UbuntuWeb systemd[1]: Time has been changed
Dec 30 21:17:10 Battist-UbuntuWeb systemd[1]: snapd.refresh.timer: Adding 53min 36.387318s random time.
Dec 30 21:17:10 Battist-UbuntuWeb systemd[1]: apt-daily.timer: Adding 9h 41min 54.170691s random time.
Dec 30 21:17:34 Battist-UbuntuWeb kernel: [ 6012.008051] usb 1-8: reset high-speed USB device number 2 using ehci-pci
Dec 30 21:17:46 Battist-UbuntuWeb systemd[1]: Time has been changed
Dec 30 21:17:46 Battist-UbuntuWeb systemd[1]: snapd.refresh.timer: Adding 39min 17.007303s random time.
Dec 30 21:17:46 Battist-UbuntuWeb systemd[1]: apt-daily.timer: Adding 8h 59min 51.269802s random time.
Dec 30 21:18:13 Battist-UbuntuWeb kernel: [ 6046.820057] usb 1-8: reset high-speed USB device number 2 using ehci-pci
Dec 30 21:18:23 Battist-UbuntuWeb systemd[1]: Time has been changed
Dec 30 21:18:23 Battist-UbuntuWeb systemd[1]: snapd.refresh.timer: Adding 2h 43min 15.184938s random time.
Dec 30 21:18:23 Battist-UbuntuWeb systemd[1]: apt-daily.timer: Adding 9h 54min 10.655886s random time.
Dec 30 21:18:59 Battist-UbuntuWeb systemd[1]: Time has been changed
Dec 30 21:18:59 Battist-UbuntuWeb systemd[1]: snapd.refresh.timer: Adding 4h 7min 5.436308s random time.
Dec 30 21:18:59 Battist-UbuntuWeb systemd[1]: apt-daily.timer: Adding 10h 46min 17.208784s random time.
Dec 30 21:19:04 Battist-UbuntuWeb kernel: [ 6089.828076] usb 1-8: reset high-speed USB device number 2 using ehci-pci
Dec 31 14:03:27 Battist-UbuntuWeb rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="1844" x-info="http://www.rsyslog.com"] start
Dec 31 14:03:26 Battist-UbuntuWeb rsyslogd-2222: command 'KLogPermitNonKernelFacility' is currently not permitted - did you already set it via a RainerScript command (v6+ config)? [v8.16.0 try [http://www.rsyslog.com/e/2222](http://www.rsyslog.com/e/2222) ]
Dec 31 14:03:27 Battist-UbuntuWeb rsyslogd: rsyslogd's groupid changed to 108
```

The system log is the same all the time just prior to freezing.
Any help would be much appreciated.

---

### Post by gordintoronto on 2016-12-31
Hi Tinman,

It's generally better to start a new thread, rather than jump onto one which is only marginally similar to your problem.

Have you tried acpi=off? See Full Circle Magazine issue 111, page 43.

---

### Post by tinmanb on 2017-01-01
Hi Gord and thank you.

I will start a new thread next time.
I will try "acpi=off" and keep you posted.

Should i start a new thread if it doesn't work or continued on this one?

---

### Post by cariboo on 2017-01-01
@tinmanb, it would be better to start a new thread.

---

### Post by tinmanb on 2017-01-05
[COLOR=#000000]Hi All.[/COLOR]
[COLOR=#000000]For starters, i want to thank gordintoronto for his assistance.[/COLOR]

[COLOR=#000000]As a recap, I'm running 16.04.1 LTS Server with kernel v4.7-rc3 on a hp media center m7640n with [/COLOR][COLOR=#393939][FONT=arial]AMD Athlon(tm) 64 X2 Dual Core Processor 5000+, 2 cores and server kept freezing. It would never stay up for more than 2hrs without me turning it off and on.
[/FONT][/COLOR][COLOR=#000000]To solve this issue, i backed up the necessary files (html, SQL, etc), Fresh install of 16.04, did all the updates and in the grub, turned apci=off, quiet, splash, and set intel_idle.max_cstate to 1. the current kernel, after the fresh install and updates is now [/COLOR][COLOR=#393939][FONT=arial]4.4.0-57-generic and all seems to be running with out and issues. So far its been up for 13hrs and still going.

Thank you again gordintoronto[/FONT][/COLOR]

---

