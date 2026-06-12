---
title: "Can't login via ssh after some time."
date: 2007-10-14
forum: Server Platforms
---

### Post by DannyW on 2007-10-14
I have recently gone to university and left an Ubuntu box at home. It's running just pretty much the standard Ubuntu server from the alternate install, with no LAMP. I was also running btlaunchmany, a bittorrent client which scans a directory for .torrent files and downloads the torrents.

Every thing was working fine. Access via ssh was ok and access to it via ftp was also good, using vsftpd.

The box is still alive as I can ping it. When I try to login via ssh it freezes, right after I enter my password and press enter. I cannot close my ssh client by ctrl+c.

ftp logs in but times out when trying to get the directory listing.

This has happened twice, to resolve I must turn the box off and on again.

Anyone got any ideas why this would be happening?

If not, what log files would I have to check on the next boot to try to find the problem?

Thanks
Danny

---

### Post by anubhavrocks on 2007-10-14
The first thing you dhould check is syslog
```
cat /var/log/syslog
```
Also check if your box is running out of diskspace.

---

### Post by DannyW on 2007-10-14
syslog doesn't seem to give any useful information I'm afraid.

The following is a snippet of syslog. At 13:37 I called my parents at home to restart the system (take the power out and plug back in), it then booted up. (In fact, I called them before this and asked them to restart it, but it didn't boot up. Could not ping it - So I just asked them to try again, and it worked)

It was this morning (Oct 14) that I couldn't ssh or ftp into the server.

> Oct 13 16:17:01 phast /USR/SBIN/CRON[4675]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 13 16:44:14 phast -- MARK --
Oct 13 17:04:15 phast -- MARK --
Oct 13 17:17:01 phast /USR/SBIN/CRON[4678]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 13 17:44:16 phast -- MARK --
Oct 13 18:04:16 phast -- MARK --
Oct 13 18:17:01 phast /USR/SBIN/CRON[4682]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 13 18:44:18 phast -- MARK --
Oct 13 19:04:18 phast -- MARK --
Oct 14 13:37:26 phast syslogd 1.4.1#20ubuntu4: restart.
Oct 14 13:37:27 phast kernel: Inspecting /boot/System.map-2.6.20-15-server
Oct 14 13:37:27 phast kernel: Loaded 25134 symbols from /boot/System.map-2.6.20-15-server.
Oct 14 13:37:27 phast kernel: Symbols match kernel version 2.6.20.
Oct 14 13:37:27 phast kernel: No module symbols loaded - kernel modules not enabled.
Oct 14 13:37:27 phast kernel: [    0.000000] Linux version 2.6.20-15-server (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:41:34 UTC 2007 (Ubuntu 2.6.20-15.27-server)

...Followed by the boot sequence...

Also, here is my disk usage. Very simple setup, no custom mounts, just root. It won't be storing much. I will download files from it then delete them from the server.
> df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G  949M   33G   3% /
varrun                1.5G  172K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
procbususb            1.5G   68K  1.5G   1% /proc/bus/usb
udev                  1.5G   68K  1.5G   1% /dev
devshm                1.5G     0  1.5G   0% /dev/shm


Any other ideas?

Thanks,
Danny

---

### Post by anubhavrocks on 2007-10-14
Is there some sort of power management running?It seems somehow that the hard disk is acting up.Check your logs with something related  to that.

---

