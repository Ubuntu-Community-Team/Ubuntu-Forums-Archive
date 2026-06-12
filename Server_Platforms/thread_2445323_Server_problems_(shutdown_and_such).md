---
title: "Server problems (shutdown and such)"
date: 2020-06-12
forum: Server Platforms
---

### Post by Magniez on 2020-06-12
I'm totally at a loss. I installed a server and it kept crashing. So I  reinstalled it, with a RAID1 of 4To for good mesure. Everything was  fine, but it keeps crashing randomly. I think it could be a memory  problem, so I'll do a memcheck. In the meantime I give you the log from  the latest shutdown, it's quite weird.

```
Jun 12 09:13:16 kodi systemd-resolved[762]: message repeated 11 times: [ Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.]
Jun 12 09:13:39 kodi systemd[1]: unattended-upgrades.service: Succeeded.
Jun 12 09:13:39 kodi systemd[1]: Stopped Unattended Upgrades Shutdown.
```

I'll close the thread if memcheck finds any errors

---

### Post by mastablasta on 2020-06-12
do you have unnatended upgrades scheduled to shutdown the PC after they are done?

---

### Post by Magniez on 2020-06-12
I'm memtesting the computer right now so I can't check. How can I check when it will be back up ?

---

### Post by LHammonds on 2020-06-12
> **Magniez said:**
> I installed a serverWhat server?  You did not specify.  Was it 20.04 live installer from Ubuntu or some other flavor or from some unofficial source?

> **Magniez said:**
> it kept crashingThat is not standard behavior and typical of problems with physical hardware being defective or drivers not working or using incorrect drivers.

Based on your log, are you sure it is crashing or is it just shutting down after each upgrade? (Also not default behavior with any Ubuntu release)

As for apt settings, you can look for them in /etc/apt.

This file houses some settings but only about 2 or 3 are set by default: /etc/apt/apt.conf.d/50unattended-upgrades

LHammonds

---

### Post by Magniez on 2020-06-12
> **LHammonds said:**
> What server?  You did not specify.  Was it 20.04 live installer from Ubuntu or some other flavor or from some unofficial source?

That is not standard behavior and typical of problems with physical hardware being defective or drivers not working or using incorrect drivers.

Based on your log, are you sure it is crashing or is it just shutting down after each upgrade? (Also not default behavior with any Ubuntu release)

As for apt settings, you can look for them in /etc/apt.

This file houses some settings but only about 2 or 3 are set by default: /etc/apt/apt.conf.d/50unattended-upgrades

LHammonds

Official 20.04

As for physical defect it's why I checked with memtest for instance ? (no issue btw) 

And I said I'll check my config of unattended

EDIT : I deactivated unattended-upgrades

---

### Post by Magniez on 2020-06-28
After 2 weeks without any problems, the server is once again shuting down on its own, here's the log for the last event (2 shutdown today) 

```
Jun 28 08:45:31 kodi systemd[1]: Starting Cleanup of Temporary Directories...
Jun 28 08:45:31 kodi systemd[1]: systemd-tmpfiles-clean.service: Succeeded.
Jun 28 08:45:31 kodi systemd[1]: Finished Cleanup of Temporary Directories.
Jun 28 08:46:12 kodi systemd-resolved[778]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Jun 28 08:46:12 kodi systemd-resolved[778]: message repeated 3 times: [ Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.]
Jun 28 08:46:47 kodi systemd[1]: Removed slice system-modprobe.slice.
Jun 28 08:46:47 kodi systemd[1]: Stopped target Cloud-init target.
Jun 28 08:46:47 kodi systemd[1]: Stopped target Graphical Interface.
Jun 28 08:46:47 kodi systemd[1]: Stopped target Timers.
Jun 28 08:46:47 kodi systemd[1]: apt-daily-upgrade.timer: Succeeded.
Jun 28 08:46:47 kodi systemd[1]: Stopped Daily apt upgrade and clean activities.
Jun 28 08:46:47 kodi systemd[1]: apt-daily.timer: Succeeded.
Jun 28 08:46:47 kodi systemd[1]: Stopped Daily apt download activities.
Jun 28 08:46:47 kodi systemd[1]: e2scrub_all.timer: Succeeded.
Jun 28 08:46:47 kodi systemd[1]: Stopped Periodic ext4 Online Metadata Check for All Filesystems.
Jun 28 08:46:47 kodi systemd[1]: fstrim.timer: Succeeded.
Jun 28 08:46:47 kodi systemd[1]: Stopped Discard unused blocks once a week.
Jun 28 08:46:47 kodi systemd[1]: fwupd-refresh.timer: Succeeded.
Jun 28 08:46:47 kodi systemd[1]: Stopped Refresh fwupd metadata regularly.
Jun 28 08:46:47 kodi systemd[1]: logrotate.timer: Succeeded.
Jun 28 08:46:47 kodi systemd[1]: Stopped Daily rotation of log files.
Jun 28 08:46:47 kodi systemd[1]: man-db.timer: Succeeded.
Jun 28 08:46:47 kodi systemd[1]: Stopped Daily man-db regeneration.
Jun 28 08:46:47 kodi systemd[1]: mdcheck_start.timer: Succeeded.
Jun 28 08:46:47 kodi systemd[1]: Stopped MD array scrubbing.
Jun 28 08:46:47 kodi systemd[1]: mdmonitor-oneshot.timer: Succeeded.
Jun 28 08:46:47 kodi systemd[1]: Stopped Reminder for degraded MD arrays.
Jun 28 08:46:47 kodi systemd[1]: motd-news.timer: Succeeded.
Jun 28 08:46:47 kodi systemd[1]: Stopped Message of the Day.
Jun 28 08:46:47 kodi systemd[1]: systemd-tmpfiles-clean.timer: Succeeded.
Jun 28 08:46:47 kodi systemd[1]: Stopped Daily Cleanup of Temporary Directories.
Jun 28 08:46:47 kodi systemd[1]: Stopped target System Time Synchronized.
Jun 28 08:46:47 kodi systemd[1]: Stopped target System Time Set.
Jun 28 08:46:47 kodi systemd[1]: lvm2-lvmpolld.socket: Succeeded.
Jun 28 08:46:47 kodi systemd[1]: Closed LVM2 poll daemon socket.
Jun 28 08:46:47 kodi systemd[1]: systemd-rfkill.socket: Succeeded.
Jun 28 08:46:47 kodi systemd[1]: Closed Load/Save RF Kill Switch Status /dev/rfkill Watch.
Jun 28 08:46:47 kodi systemd[1]: Stopping Accounts Service...
Jun 28 08:46:47 kodi systemd[1]: Stopping Availability of block devices...
Jun 28 08:46:47 kodi systemd[1]: cloud-final.service: Succeeded.
Jun 28 08:46:47 kodi systemd[1]: Stopped Execute cloud user/final scripts.
Jun 28 08:46:47 kodi systemd[1]: cloud-config.service: Succeeded.
Jun 28 08:46:47 kodi systemd[1]: Stopped Apply the settings specified in cloud-config.
Jun 28 08:46:47 kodi systemd[1]: Stopped target Cloud-config availability.
Jun 28 08:46:47 kodi systemd[1]: Stopping Create final runtime dir for shutdown pivot root...
Jun 28 08:46:47 kodi systemd[1]: Stopping minecraft server dodo...
Jun 28 08:46:47 kodi systemd[1]: Condition check resulted in Ubuntu core (all-snaps) system shutdown helper setup service being skipped.
Jun 28 08:46:47 kodi systemd[1]: Stopping Load/Save Random Seed...
Jun 28 08:46:47 kodi systemd[1]: Stopping Disk Manager...
Jun 28 08:46:47 kodi systemd[1]: Stopping Daemon for power management...
Jun 28 08:46:47 kodi blkdeactivate[13823]: Deactivating block devices:
Jun 28 08:46:47 kodi systemd[1]: accounts-daemon.service: Succeeded.
Jun 28 08:46:47 kodi systemd[1]: Stopped Accounts Service.
Jun 28 08:46:47 kodi systemd[1]: hibernation.service: Succeeded.
Jun 28 08:46:47 kodi systemd[1]: Stopped minecraft server dodo.
Jun 28 08:46:47 kodi systemd[1]: systemd-random-seed.service: Succeeded.
Jun 28 08:46:47 kodi systemd[1]: Stopped Load/Save Random Seed.
Jun 28 08:46:47 kodi systemd[1]: Stopped target Multi-User System.
Jun 28 08:46:47 kodi systemd[1]: Stopped target Login Prompts.
Jun 28 08:46:47 kodi ModemManager[859]: <info>  Caught signal, shutting down...
Jun 28 08:46:47 kodi systemd[1]: Stopping Modem Manager...
Jun 28 08:46:47 kodi systemd[1]: Stopping LSB: automatic crash report generation...
Jun 28 08:46:47 kodi systemd[1]: Stopping Deferred execution scheduler...
Jun 28 08:46:47 kodi avahi-daemon[791]: Got SIGTERM, quitting.
Jun 28 08:46:47 kodi avahi-daemon[791]: Leaving mDNS multicast group on interface enp3s0.IPv6 with address 2a01:cb14:327:6400:f279:59ff:fe70:8809.
Jun 28 08:46:47 kodi avahi-daemon[791]: Leaving mDNS multicast group on interface enp3s0.IPv4 with address 192.168.1.10.
Jun 28 08:46:47 kodi avahi-daemon[791]: Leaving mDNS multicast group on interface lo.IPv6 with address ::1.
Jun 28 08:46:47 kodi avahi-daemon[791]: Leaving mDNS multicast group on interface lo.IPv4 with address 127.0.0.1.
Jun 28 08:46:47 kodi systemd[1]: Stopping Avahi mDNS/DNS-SD Stack...
Jun 28 08:46:47 kodi systemd[1]: Stopping "Bot Cine"...
Jun 28 08:46:47 kodi blkdeactivate[13823]:   [UMOUNT]: unmounting md127 (md127) mounted on /media/NAS... skipping
Jun 28 08:46:47 kodi systemd[1]: Stopping Regular background program processing daemon...
Jun 28 08:46:47 kodi systemd[1]: Stopping Deluge Bittorrent Client Web Interface...
Jun 28 08:46:47 kodi dbus-daemon[793]: [system] Activating via systemd: service name='org.freedesktop.Avahi' unit='dbus-org.freedesktop.Avahi.service' requested by ':1.26' (uid=1000 pid=1070 comm="/usr/lib/x86_64-linux-gnu/kodi/kodi-x11 --standalo" label="unconfined")
Jun 28 08:46:47 kodi systemd[1]: Stopping LSB: GNOME Display Manager...
Jun 28 08:46:47 kodi systemd[1]: Stopping Getty on tty1...
Jun 28 08:46:47 kodi systemd[1]: Stopping LSB: Record successful boot for GRUB...
Jun 28 08:46:47 kodi systemd[1]: Stopping irqbalance daemon...
Jun 28 08:46:47 kodi xinit[979]: /usr/bin/xinit: connection to X server lost
```

---

### Post by LHammonds on 2020-06-28
Well, I don't recognize anything in that log that initiated the shutdown...the vast majority of it is notifications that services are being stopped after a shutdown was issued.

I noticed you have a desktop installed a several other packages.  I am not at all familiar with those...which might be causing the shutdown.  I just don't know because I do not see a smoking gun yet from what you have shown.  For all I know, Minecraft might have a schedule that says to update and shutdown/reboot after every upgrade.

I will have to defer to others on the forum.

I would recommend looking at more than one log though.  For each service you install, there will be an associated log (typically).  If you post any, please specify which logs are you posting.

LHammonds

---

### Post by Magniez on 2020-06-28
Except Minecraft is not even running, a script launch it when someone tries to connect on the relevant port, and the script is running as a service. I'll watch the logs of every service at the next shutdown. My hunch is still on the short circuit from the power button (it's a bit of a frankenstein build, the power button is actualy an old reset button from an old case, so maybe it's screwed up, don't know.) I don't see anything indicating power failure, the PSU is a corsair 450w from my girlfriend old rig, less than 5 years old, very good condition (it was behind a filter when used). Maybe the motherboard or the CPU is toasted, but the shutdown wouldn't be so clean I think, and thermals are good (it's a bit hot at home right now, so idle is 42/45 max, and it's rarely over 60). Very fristrating.

---

### Post by mastablasta on 2020-06-29
something issues a command to shutdown. yes it oculd be bad power key. but it could also be one of the services. other hardware doesn't seem to be an issue.

lugs should have shutdown command recorded somewhere.

---

### Post by Magniez on 2020-06-29
Bingo, it WAS the power button, scrapping in auuth.logg and searching power gave me that 

```
Jun 28 06:21:25 kodi systemd-logind[805]: Powering Off...
Jun 28 06:21:25 kodi systemd-logind[805]: System is powering down.
Jun 28 06:22:09 kodi systemd-logind[793]: Watching system buttons on /dev/input/event1 (Power Button)
Jun 28 06:22:09 kodi systemd-logind[793]: Watching system buttons on /dev/input/event0 (Power Button)
Jun 28 06:22:10 kodi systemd-logind[793]: Power key pressed.
Jun 28 06:22:10 kodi systemd-logind[793]: Powering Off...
Jun 28 06:22:10 kodi systemd-logind[793]: System is powering down.
Jun 28 06:22:10 kodi systemd-logind[793]: Power key pressed.
Jun 28 06:24:30 kodi systemd-logind[792]: Watching system buttons on /dev/input/event1 (Power Button)
Jun 28 06:24:30 kodi systemd-logind[792]: Watching system buttons on /dev/input/event0 (Power Button)
Jun 28 06:25:51 kodi systemd-logind[792]: Power key pressed.
Jun 28 06:25:51 kodi systemd-logind[792]: Powering Off...
Jun 28 06:25:51 kodi systemd-logind[792]: System is powering down.
Jun 28 08:30:34 kodi systemd-logind[818]: Watching system buttons on /dev/input/event1 (Power Button)
Jun 28 08:30:34 kodi systemd-logind[818]: Watching system buttons on /dev/input/event0 (Power Button)
Jun 28 08:46:47 kodi systemd-logind[818]: Power key pressed.
Jun 28 08:46:47 kodi systemd-logind[818]: Powering Off...
Jun 28 08:46:47 kodi systemd-logind[818]: System is powering down.
Jun 28 08:48:02 kodi systemd-logind[792]: Watching system buttons on /dev/input/event1 (Power Button)
Jun 28 08:48:02 kodi systemd-logind[792]: Watching system buttons on /dev/input/event0 (Power Button)
```

---

