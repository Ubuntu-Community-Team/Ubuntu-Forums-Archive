---
title: "Reboot shuts down instead"
date: 2022-07-09
forum: Server Platforms
---

### Post by mellopete on 2022-07-09
Hi. I'm running Ubuntu 20.04.4. LTS 5.4.0-121-generic. When the system reboots, it powers off instead. I migrated this system from bare metal to ESXi on the same AMD Ryzen 7 3700X. Let me know what other details I can provide to help find the problem. Thank you!

---

### Post by LHammonds on 2022-07-09
> **mellopete said:**
> When the system reboots, it powers off instead.
That is not enough information to go on.

You say "system reboots" are you talking about issuing a Guest Shutdown command from the vSphere Menu or are you talking about a crontab job that is automating reboots or are you talking about a command you type in?

Need to see the command being issued to perform the reboot.  It also wouldn't hurt to look at the logs to see what's going on there too.

Gathering these kinds of details often tends to help you resolve the problem yourself.

LHammonds

---

### Post by mellopete on 2022-07-09
Hi LHammonds. Thanks for the reply. It powers off when I issue a "sudo reboot" and also after an unattended upgrade which I have set to automatically restart. It doesn't happen every time. Sometimes it reboots normally. I looked at the log and I noticed some errors regarding hard drives. I do have the onboard sata ports passed through to the Ubuntu guest on ESXi in a hacky way (as seen here [https://gist.github.com/Hengjie/1520114890bebe8f805d337af4b3a064](https://gist.github.com/Hengjie/1520114890bebe8f805d337af4b3a064)). Could that be the cause? The drives work fine while the system is running. Here is the log:

```
Jul 08 05:30:00 systemd-logind[1445]: System is rebooting.
Jul 08 05:30:00 systemd[1]: unattended-upgrades.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Unattended Upgrades Shutdown.
Jul 08 05:30:00 systemd[1]: Removed slice system-modprobe.slice.
Jul 08 05:30:00 systemd[1]: Stopped target Cloud-init target.
Jul 08 05:30:00 systemd[1]: Stopped target Graphical Interface.
Jul 08 05:30:00 systemd[1]: Stopped target Host and Network Name Lookups.
Jul 08 05:30:00 systemd[1]: Stopped target Timers.
Jul 08 05:30:00 systemd[1]: apt-daily-upgrade.timer: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Daily apt upgrade and clean activities.
Jul 08 05:30:00 systemd[1]: apt-daily.timer: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Daily apt download activities.
Jul 08 05:30:00 systemd[1]: e2scrub_all.timer: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Periodic ext4 Online Metadata Check for All Filesystems.
Jul 08 05:30:00 systemd[1]: fstrim.timer: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Discard unused blocks once a week.
Jul 08 05:30:00 systemd[1]: fwupd-refresh.timer: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Refresh fwupd metadata regularly.
Jul 08 05:30:00 systemd[1]: logrotate.timer: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Daily rotation of log files.
Jul 08 05:30:00 systemd[1]: man-db.timer: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Daily man-db regeneration.
Jul 08 05:30:00 systemd[1]: motd-news.timer: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Message of the Day.
Jul 08 05:30:00 systemd[1]: systemd-tmpfiles-clean.timer: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Daily Cleanup of Temporary Directories.
Jul 08 05:30:00 systemd[1]: ua-timer.timer: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Ubuntu Advantage Timer for running repeated jobs.
Jul 08 05:30:00 systemd[1]: lvm2-lvmpolld.socket: Succeeded.
Jul 08 05:30:00 systemd[1]: Closed LVM2 poll daemon socket.
Jul 08 05:30:00 systemd[1]: systemd-rfkill.socket: Succeeded.
Jul 08 05:30:00 systemd[1]: Closed Load/Save RF Kill Switch Status /dev/rfkill Watch.
Jul 08 05:30:00 systemd[1]: Stopping Accounts Service...
Jul 08 05:30:00 systemd[1]: Stopping Availability of block devices...
Jul 08 05:30:00 systemd[1]: cloud-final.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Execute cloud user/final scripts.
Jul 08 05:30:00 systemd[1]: Stopped target Multi-User System.
Jul 08 05:30:00 systemd[1]: Stopped target Login Prompts.
Jul 08 05:30:00 ModemManager[1474]: <info>  caught signal, shutting down...
Jul 08 05:30:00 systemd[1]: Stopping Modem Manager...
Jul 08 05:30:00 systemd[1]: Stopping LSB: automatic crash report generation...
Jul 08 05:30:00 systemd[1]: Stopping Deferred execution scheduler...
Jul 08 05:30:00 systemd[1]: cloud-config.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Apply the settings specified in cloud-config.
Jul 08 05:30:00 systemd[1]: Stopped target Cloud-config availability.
Jul 08 05:30:00 systemd[1]: Stopped target Network is Online.
Jul 08 05:30:00 systemd[1]: NetworkManager-wait-online.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Network Manager Wait Online.
Jul 08 05:30:00 systemd[1]: Stopping Regular background program processing daemon...
Jul 08 05:30:00 systemd[1]: Stopping Create final runtime dir for shutdown pivot root...
Jul 08 05:30:00 systemd[1]: Stopping Getty on tty1...
Jul 08 05:30:00 systemd[1]: Stopping HPool miner: pete...
Jul 08 05:30:00 systemd[1]: lm-sensors.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Initialize hardware monitoring sensors.
Jul 08 05:30:00 systemd[1]: Stopping LVM event activation on device 8:3...
Jul 08 05:30:00 systemd[1]: Stopping Dispatcher daemon for systemd-networkd...
Jul 08 05:30:00 systemd[1]: Stopping Network Time Service...
Jul 08 05:30:00 ntpd[1520]: ntpd exiting on signal 15 (Terminated)
Jul 08 05:30:00 systemd[1]: Stopping System Logging Service...
Jul 08 05:30:00 ntpd[1520]: 159.89.86.140 local addr 192.168.12.7 -> <null>
Jul 08 05:30:00 ntpd[1520]: 64.246.132.14 local addr 192.168.12.7 -> <null>
Jul 08 05:30:00 ntpd[1520]: 50.205.244.39 local addr 192.168.12.7 -> <null>
Jul 08 05:30:00 ntpd[1520]: 185.125.190.58 local addr 192.168.12.7 -> <null>
Jul 08 05:30:00 ntpd[1520]: 91.189.91.157 local addr 192.168.12.7 -> <null>
Jul 08 05:30:00 systemd[1]: Stopping Self Monitoring and Reporting Technology (SMART) Daemon...
Jul 08 05:30:00 smartd[1442]: smartd received signal 15: Terminated
Jul 08 05:30:00 systemd[1]: snapd.seeded.service: Succeeded.
Jul 08 05:30:00 smartd[1442]: Device: /dev/sdc [SAT], state written to /var/lib/smartmontools/smartd.WDC_WD140EDFZ_11A0VA0-81G2KLEV.ata.state
Jul 08 05:30:00 systemd[1]: Stopped Wait until snapd is fully seeded.
Jul 08 05:30:00 smartd[1442]: Device: /dev/sdd [SAT], state written to /var/lib/smartmontools/smartd.WDC_WD140EDFZ_11A0VA0-Y5J30M5C.ata.state
Jul 08 05:30:00 systemd[1]: Stopping Snap Daemon...
Jul 08 05:30:00 smartd[1442]: Device: /dev/sde [SAT], state written to /var/lib/smartmontools/smartd.WDC_WD140EDFZ_11A0VA0-9LG77HUG.ata.state
Jul 08 05:30:00 systemd[1]: Condition check resulted in Ubuntu core (all-snaps) system shutdown helper setup service being skipped.
Jul 08 05:30:00 smartd[1442]: Device: /dev/sdf [SAT], state written to /var/lib/smartmontools/smartd.WDC_WD140EDFZ_11A0VA0-81G2M6KV.ata.state
Jul 08 05:30:00 systemd[1]: Stopping OpenBSD Secure Shell server...
Jul 08 05:30:00 smartd[1442]: Device: /dev/sdg [SAT], state written to /var/lib/smartmontools/smartd.WDC_WD140EDFZ_11A0VA0-9LGBTN5G.ata.state
Jul 08 05:30:00 systemd[1]: Stopping Login Service...
Jul 08 05:30:00 smartd[1442]: Device: /dev/sdh [SAT], state written to /var/lib/smartmontools/smartd.WDC_WD140EDFZ_11A0VA0-9MG7LJ4J.ata.state
Jul 08 05:30:00 systemd[1]: Stopping Load/Save Random Seed...
Jul 08 05:30:00 smartd[1442]: Device: /dev/sdi [SAT], state written to /var/lib/smartmontools/smartd.WDC_WD140EDFZ_11A0VA0-9LG7W5TA.ata.state
Jul 08 05:30:00 systemd[1]: Stopping Disk Manager...
Jul 08 05:30:00 sshd[1641]: Received signal 15; terminating.
Jul 08 05:30:00 systemd[1]: accounts-daemon.service: Succeeded.
Jul 08 05:30:00 rsyslogd[195293]:  message repeated 7 times: [[origin software="rsyslogd" swVersion="8.2001.0" x-pid="195293" x-info="https://www.rsyslog.com"] rsyslogd was HUPed]
Jul 08 05:30:00 systemd[1]: Stopped Accounts Service.
Jul 08 05:30:00 rsyslogd[195293]: [origin software="rsyslogd" swVersion="8.2001.0" x-pid="195293" x-info="https://www.rsyslog.com"] exiting on signal 15.
Jul 08 05:30:00 systemd[1]: networkd-dispatcher.service: Succeeded.
Jul 08 05:30:00 smartd[1442]: Device: /dev/sdj [SAT], state written to /var/lib/smartmontools/smartd.WDC_WD140EDFZ_11A0VA0-9LG7168G.ata.state
Jul 08 05:30:00 systemd[1]: Stopped Dispatcher daemon for systemd-networkd.
Jul 08 05:30:00 smartd[1442]: smartd is exiting (exit status 0)
Jul 08 05:30:00 systemd[1]: cron.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Regular background program processing daemon.
Jul 08 05:30:00 systemd[1]: atd.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Deferred execution scheduler.
Jul 08 05:30:00 apport[458240]:  * Stopping automatic crash report generation: apport
Jul 08 05:30:00 systemd[1]: getty@tty1.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Getty on tty1.
Jul 08 05:30:00 systemd[1]: ssh.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped OpenBSD Secure Shell server.
Jul 08 05:30:00 systemd[1]: rsyslog.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped System Logging Service.
Jul 08 05:30:00 systemd[1]: Removed slice system-getty.slice.
Jul 08 05:30:00 systemd[1]: Condition check resulted in Show Plymouth Reboot Screen being skipped.
Jul 08 05:30:00 systemd[1]: Stopping Permit User Sessions...
Jul 08 05:30:00 systemd[1]: smartmontools.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Self Monitoring and Reporting Technology (SMART) Daemon.
Jul 08 05:30:00 systemd[1]: systemd-user-sessions.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Permit User Sessions.
Jul 08 05:30:00 systemd[1]: systemd-random-seed.service: Succeeded.
Jul 08 05:30:00 snapd[371447]: main.go:155: Exiting on terminated signal.
Jul 08 05:30:00 apport[458240]:    ...done.
Jul 08 05:30:00 systemd[1]: Stopped Load/Save Random Seed.
Jul 08 05:30:00 systemd[1]: apport.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped LSB: automatic crash report generation.
Jul 08 05:30:00 systemd[1]: Stopped target Remote File Systems.
Jul 08 05:30:00 systemd[1]: Stopped target Remote File Systems (Pre).
Jul 08 05:30:00 systemd[1]: ntp.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Network Time Service.
Jul 08 05:30:00 systemd[1]: systemd-logind.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Login Service.
Jul 08 05:30:00 systemd[1]: Stopped target User and Group Name Lookups.
Jul 08 05:30:00 udisksd[1447]: udisks daemon version 2.8.4 exiting
Jul 08 05:30:00 blkdeactivate[458238]: Deactivating block devices:
Jul 08 05:30:00 ModemManager[1474]: <info>  ModemManager is shut down
Jul 08 05:30:00 NetworkManager[1429]: <info>  [1657272600.5551] modem-manager: ModemManager no longer available
Jul 08 05:30:00 systemd[1]: ModemManager.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Modem Manager.
Jul 08 05:30:00 systemd[1]: Stopping Authorization Manager...
Jul 08 05:30:00 blkdeactivate[458238]:   [SKIP]: unmount of ubuntu--vg-ubuntu--lv (dm-0) mounted on /
Jul 08 05:30:00 systemd[1]: polkit.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Authorization Manager.
Jul 08 05:30:00 systemd[1]: udisks2.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Disk Manager.
Jul 08 05:30:00 lvm[458246]:   pvscan[458246] PV /dev/sda3 online.
Jul 08 05:30:00 systemd[1]: blk-availability.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Availability of block devices.
Jul 08 05:30:00 systemd[1]: lvm2-pvscan@8:3.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped LVM event activation on device 8:3.
Jul 08 05:30:00 systemd[1]: Removed slice system-lvm2\x2dpvscan.slice.
Jul 08 05:30:00 systemd[1]: hpool-miner@pete.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped HPool miner: pete.
Jul 08 05:30:00 systemd[1]: Removed slice system-hpool\x2dminer.slice.
Jul 08 05:30:00 systemd[1]: Stopped target Network.
Jul 08 05:30:00 systemd[1]: Stopping Network Manager...
Jul 08 05:30:00 systemd[1]: Stopping Network Name Resolution...
Jul 08 05:30:00 NetworkManager[1429]: <info>  [1657272600.6481] caught SIGTERM, shutting down normally.
Jul 08 05:30:00 NetworkManager[1429]: <info>  [1657272600.6527] dhcp4 (ens33): canceled DHCP transaction
Jul 08 05:30:00 NetworkManager[1429]: <info>  [1657272600.6527] dhcp4 (ens33): state changed extended -> done
Jul 08 05:30:00 dbus-daemon[1428]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.6' (uid=0 pid=1429 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Jul 08 05:30:00 NetworkManager[1429]: <info>  [1657272600.6528] device (ens33): DHCPv4: trying to acquire a new lease within 90 seconds
Jul 08 05:30:00 dbus-daemon[1428]: [system] Activation via systemd failed for unit 'dbus-org.freedesktop.nm-dispatcher.service': Refusing activation, D-Bus is shutting down.
Jul 08 05:30:00 NetworkManager[1429]: <info>  [1657272600.6530] manager: NetworkManager state is now CONNECTED_SITE
Jul 08 05:30:00 NetworkManager[1429]: <info>  [1657272600.6596] exiting (success)
Jul 08 05:30:00 snapd[371447]: overlord.go:504: Released state lock file
Jul 08 05:30:00 systemd[1]: snapd.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Snap Daemon.
Jul 08 05:30:00 systemd[1]: NetworkManager.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Network Manager.
Jul 08 05:30:00 systemd[1]: Stopped target Network (Pre).
Jul 08 05:30:00 systemd[1]: Stopping D-Bus System Message Bus...
Jul 08 05:30:00 systemd[1]: systemd-resolved.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Network Name Resolution.
Jul 08 05:30:00 systemd[1]: dbus.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped D-Bus System Message Bus.
Jul 08 05:30:00 systemd[1]: Stopped target Basic System.
Jul 08 05:30:00 systemd[1]: Stopped target Paths.
Jul 08 05:30:00 systemd[1]: Stopped target Slices.
Jul 08 05:30:00 systemd[1]: Removed slice User and Session Slice.
Jul 08 05:30:00 systemd[1]: Stopped target Sockets.
Jul 08 05:30:00 systemd[1]: cloud-init-hotplugd.socket: Succeeded.
Jul 08 05:30:00 systemd[1]: Closed cloud-init hotplug hook socket.
Jul 08 05:30:00 systemd[1]: Stopping Cockpit Web Service Socket.
Jul 08 05:30:00 systemd[1]: dbus.socket: Succeeded.
Jul 08 05:30:00 systemd[1]: Closed D-Bus System Message Bus Socket.
Jul 08 05:30:00 systemd[1]: iscsid.socket: Succeeded.
Jul 08 05:30:00 systemd[1]: Closed Open-iSCSI iscsid Socket.
Jul 08 05:30:00 systemd[1]: snap.lxd.daemon.unix.socket: Succeeded.
Jul 08 05:30:00 systemd[1]: Closed Socket unix for snap application lxd.daemon.
Jul 08 05:30:00 systemd[1]: snapd.socket: Succeeded.
Jul 08 05:30:00 systemd[1]: Closed Socket activation for snappy daemon.
Jul 08 05:30:00 systemd[1]: syslog.socket: Succeeded.
Jul 08 05:30:00 systemd[1]: Closed Syslog Socket.
Jul 08 05:30:00 systemd[1]: uuidd.socket: Succeeded.
Jul 08 05:30:00 systemd[1]: Closed UUID daemon activation socket.
Jul 08 05:30:00 systemd[1]: cockpit.socket: Succeeded.
Jul 08 05:30:00 systemd[1]: Closed Cockpit Web Service Socket.
Jul 08 05:30:00 systemd[1]: Stopped target System Initialization.
Jul 08 05:30:00 systemd[1]: Stopped target Local Encrypted Volumes.
Jul 08 05:30:00 systemd[1]: systemd-ask-password-console.path: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Dispatch Password Requests to Console Directory Watch.
Jul 08 05:30:00 systemd[1]: systemd-ask-password-wall.path: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Forward Password Requests to Wall Directory Watch.
Jul 08 05:30:00 systemd[1]: cloud-init.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Initial cloud-init job (metadata service crawler).
Jul 08 05:30:00 systemd[1]: cloud-init-local.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Initial cloud-init job (pre-networking).
Jul 08 05:30:00 systemd[1]: systemd-sysctl.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Apply Kernel Variables.
Jul 08 05:30:00 systemd[1]: systemd-modules-load.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Load Kernel Modules.
Jul 08 05:30:00 systemd[1]: Stopping Update UTMP about System Boot/Shutdown...
Jul 08 05:30:00 systemd[1]: systemd-update-utmp.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Update UTMP about System Boot/Shutdown.
Jul 08 05:30:00 systemd[1]: systemd-tmpfiles-setup.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Create Volatile Files and Directories.
Jul 08 05:30:00 systemd-tmpfiles[458425]: [/run/finalrd-libs.conf:9] Duplicate line for path "/run/initramfs/lib64", ignoring.
Jul 08 05:30:00 finalrd[458426]: run-parts: executing /usr/share/finalrd/mdadm.finalrd setup
Jul 08 05:30:00 finalrd[458426]: run-parts: executing /usr/share/finalrd/open-iscsi.finalrd setup
Jul 08 05:30:00 systemd[1]: finalrd.service: Succeeded.
Jul 08 05:30:00 systemd[1]: Stopped Create final runtime dir for shutdown pivot root.
Jul 08 05:30:00 systemd[1]: Stopped target Local File Systems.
Jul 08 05:30:00 systemd[1]: Unmounting /boot/efi...
Jul 08 05:30:00 systemd[1]: Unmounting /mnt/sda1...
Jul 08 05:30:00 systemd[1]: Unmounting /mnt/sdb1...
Jul 08 05:30:00 systemd[1]: Unmounting /mnt/sdc1...
Jul 08 05:30:00 systemd[1]: Unmounting /mnt/sdd1...
Jul 08 05:30:00 systemd[1]: Unmounting /mnt/sde1...
Jul 08 05:30:00 systemd[1]: Unmounting /mnt/sdf1...
Jul 08 05:30:00 systemd[1]: Unmounting /mnt/sdg1...
Jul 08 05:30:00 systemd[1]: Unmounting /mnt/sdh1...
Jul 08 05:30:00 systemd[1]: Unmounting /mnt/sdi1...
Jul 08 05:30:00 systemd[1]: Unmounting /mnt/sdk1...
Jul 08 05:30:00 systemd[1]: Unmounting /mnt/sdl1...
Jul 08 05:30:00 systemd[1]: Unmounting /mnt/sdm1...
Jul 08 05:30:00 systemd[1]: Unmounting /run/snapd/ns/lxd.mnt...
Jul 08 05:30:00 systemd[1]: Unmounting Mount unit for core18, revision 2344...
Jul 08 05:30:01 kernel: XFS (sdk1): Unmounting Filesystem
Jul 08 05:30:01 systemd[1]: Unmounting Mount unit for core18, revision 2409...
Jul 08 05:30:01 systemd[1]: Unmounting Mount unit for core20, revision 1494...
Jul 08 05:30:01 systemd[1]: Unmounting Mount unit for core20, revision 1518...
Jul 08 05:30:01 systemd[1]: Unmounting Mount unit for lxd, revision 22526...
Jul 08 05:30:01 systemd[1]: Unmounting Mount unit for lxd, revision 22753...
Jul 08 05:30:01 systemd[1]: Unmounting Mount unit for snapd, revision 16010...
Jul 08 05:30:01 systemd[1]: Unmounting Mount unit for snapd, revision 16292...
Jul 08 05:30:01 systemd[1]: boot-efi.mount: Succeeded.
Jul 08 05:30:01 systemd[1]: Unmounted /boot/efi.
Jul 08 05:30:01 systemd[1]: snap-core20-1518.mount: Succeeded.
Jul 08 05:30:01 systemd[1]: Unmounted Mount unit for core20, revision 1518.
Jul 08 05:30:01 systemd[1]: snap-snapd-16010.mount: Succeeded.
Jul 08 05:30:01 systemd[1]: Unmounted Mount unit for snapd, revision 16010.
Jul 08 05:30:01 systemd[1]: Unmounting /boot...
Jul 08 05:30:01 systemd[1]: mnt-sdb1.mount: Succeeded.
Jul 08 05:30:01 systemd[1]: Unmounted /mnt/sdb1.
Jul 08 05:30:01 systemd[1]: mnt-sdm1.mount: Succeeded.
Jul 08 05:30:01 systemd[1]: Unmounted /mnt/sdm1.
Jul 08 05:30:01 systemd[1]: boot.mount: Succeeded.
Jul 08 05:30:01 systemd[1]: Unmounted /boot.
Jul 08 05:30:01 systemd[1]: mnt-sde1.mount: Succeeded.
Jul 08 05:30:01 systemd[1]: Unmounted /mnt/sde1.
Jul 08 05:30:01 systemd[1]: snap-core18-2409.mount: Succeeded.
Jul 08 05:30:01 systemd[1]: Unmounted Mount unit for core18, revision 2409.
Jul 08 05:30:01 systemd[1]: mnt-sdk1.mount: Succeeded.
Jul 08 05:30:01 systemd[1]: Unmounted /mnt/sdk1.
Jul 08 05:30:01 systemd[1]: snap-core18-2344.mount: Succeeded.
Jul 08 05:30:01 systemd[1]: Unmounted Mount unit for core18, revision 2344.
Jul 08 05:30:01 systemd[1]: snap-lxd-22526.mount: Succeeded.
Jul 08 05:30:01 systemd[1]: Unmounted Mount unit for lxd, revision 22526.
Jul 08 05:30:01 systemd[1]: snap-core20-1494.mount: Succeeded.
Jul 08 05:30:01 systemd[1]: Unmounted Mount unit for core20, revision 1494.
Jul 08 05:30:01 systemd[1]: snap-lxd-22753.mount: Succeeded.
Jul 08 05:30:01 systemd[1]: Unmounted Mount unit for lxd, revision 22753.
Jul 08 05:30:01 systemd[1]: snap-snapd-16292.mount: Succeeded.
Jul 08 05:30:01 systemd[1]: Unmounted Mount unit for snapd, revision 16292.
Jul 08 05:30:01 kernel: XFS (sdc1): Unmounting Filesystem
Jul 08 05:30:01 kernel: XFS (sde1): Unmounting Filesystem
Jul 08 05:30:01 kernel: XFS (sdl1): Unmounting Filesystem
Jul 08 05:30:01 systemd[1]: mnt-sdl1.mount: Succeeded.
Jul 08 05:30:01 systemd[1]: Unmounted /mnt/sdl1.
Jul 08 05:30:01 kernel: XFS (sdj1): Unmounting Filesystem
Jul 08 05:30:01 kernel: XFS (sdf1): Unmounting Filesystem
Jul 08 05:30:01 kernel: XFS (sdm1): Unmounting Filesystem
Jul 08 05:30:01 kernel: XFS (sdi1): Unmounting Filesystem
Jul 08 05:30:01 kernel: XFS (sdh1): Unmounting Filesystem
Jul 08 05:30:01 systemd[1]: mnt-sdi1.mount: Succeeded.
Jul 08 05:30:01 systemd[1]: Unmounted /mnt/sdi1.
Jul 08 05:30:01 kernel: XFS (sdg1): Unmounting Filesystem
Jul 08 05:30:01 systemd[1]: mnt-sda1.mount: Succeeded.
Jul 08 05:30:01 systemd[1]: Unmounted /mnt/sda1.
Jul 08 05:30:01 systemd[1]: mnt-sdc1.mount: Succeeded.
Jul 08 05:30:01 systemd[1]: Unmounted /mnt/sdc1.
Jul 08 05:30:01 systemd[1]: mnt-sdd1.mount: Succeeded.
Jul 08 05:30:01 systemd[1]: Unmounted /mnt/sdd1.
Jul 08 05:30:01 systemd[1]: mnt-sdf1.mount: Succeeded.
Jul 08 05:30:01 systemd[1]: Unmounted /mnt/sdf1.
Jul 08 05:30:01 systemd[1]: mnt-sdh1.mount: Succeeded.
Jul 08 05:30:01 systemd[1]: Unmounted /mnt/sdh1.
Jul 08 05:30:01 systemd[1]: mnt-sdg1.mount: Succeeded.
Jul 08 05:30:01 systemd[1]: Unmounted /mnt/sdg1.
Jul 08 05:30:01 kernel: XFS (sdd1): Unmounting Filesystem
Jul 08 05:30:01 kernel: XFS (sdb1): Unmounting Filesystem
Jul 08 05:30:01 systemd[1]: run-snapd-ns-lxd.mnt.mount: Succeeded.
Jul 08 05:30:01 systemd[1]: Unmounted /run/snapd/ns/lxd.mnt.
Jul 08 05:30:01 systemd[1]: Unmounting /run/snapd/ns...
Jul 08 05:30:01 systemd[1]: run-snapd-ns.mount: Succeeded.
Jul 08 05:30:01 systemd[1]: Unmounted /run/snapd/ns.
Jul 08 05:30:01 systemd[1]: Stopped target Local File Systems (Pre).
Jul 08 05:30:01 systemd[1]: Stopped target Swap.
Jul 08 05:30:01 systemd[1]: Deactivating swap /swap.img...
Jul 08 05:30:01 systemd[1]: Stopping Monitoring of LVM2 mirrors, snapshots etc. using dmeventd or progress polling...
Jul 08 05:30:01 multipathd[1169]: exit (signal)
Jul 08 05:30:01 multipathd[1169]: --------shut down-------
Jul 08 05:30:01 systemd[1]: Stopping Device-Mapper Multipath Device Controller...
Jul 08 05:30:01 systemd[1]: systemd-tmpfiles-setup-dev.service: Succeeded.
Jul 08 05:30:01 systemd[1]: Stopped Create Static Device Nodes in /dev.
Jul 08 05:30:01 systemd[1]: systemd-sysusers.service: Succeeded.
Jul 08 05:30:01 systemd[1]: Stopped Create System Users.
Jul 08 05:30:01 systemd[1]: multipathd.service: Succeeded.
Jul 08 05:30:01 systemd[1]: Stopped Device-Mapper Multipath Device Controller.
Jul 08 05:30:01 systemd[1]: swap.img.swap: Succeeded.
Jul 08 05:30:01 systemd[1]: Deactivated swap /swap.img.
Jul 08 05:30:01 systemd[1]: Reached target Unmount All Filesystems.
Jul 08 05:30:01 systemd[1]: systemd-remount-fs.service: Succeeded.
Jul 08 05:30:01 systemd[1]: Stopped Remount Root and Kernel File Systems.
Jul 08 05:30:01 kernel: ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jul 08 05:30:01 kernel: ata5.00: irq_stat 0x40000000
Jul 08 05:30:01 kernel: ata5.00: failed command: READ DMA
Jul 08 05:30:01 kernel: ata5.00: cmd c8/00:00:00:00:00/00:00:00:00:00/e0 tag 13 dma 131072 in
                                             res 41/02:00:00:00:00/00:00:00:00:00/00 Emask 0x1 (device error)
Jul 08 05:30:01 kernel: ata5.00: status: { DRDY ERR }
Jul 08 05:30:01 kernel: ata5.00: configured for UDMA/100
Jul 08 05:30:01 kernel: ata5: EH complete
Jul 08 05:30:02 kernel: ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jul 08 05:30:02 kernel: ata5.00: irq_stat 0x40000000
Jul 08 05:30:02 kernel: ata5.00: failed command: READ DMA
Jul 08 05:30:02 kernel: ata5.00: cmd c8/00:00:00:08:00/00:00:00:00:00/e0 tag 16 dma 131072 in
                                             res 41/02:00:00:00:00/00:00:00:00:00/00 Emask 0x1 (device error)
Jul 08 05:30:02 kernel: ata5.00: status: { DRDY ERR }
Jul 08 05:30:02 kernel: ata5.00: configured for UDMA/100
Jul 08 05:30:02 kernel: ata5: EH complete
Jul 08 05:30:02 kernel: ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jul 08 05:30:02 kernel: ata5.00: irq_stat 0x40000000
Jul 08 05:30:02 kernel: ata5.00: failed command: READ DMA
Jul 08 05:30:02 kernel: ata5.00: cmd c8/00:00:00:00:00/00:00:00:00:00/e0 tag 20 dma 131072 in
                                             res 41/02:00:00:00:00/00:00:00:00:00/00 Emask 0x1 (device error)
Jul 08 05:30:02 kernel: ata5.00: status: { DRDY ERR }
Jul 08 05:30:02 kernel: ata5.00: configured for UDMA/100
Jul 08 05:30:02 kernel: ata5: EH complete
Jul 08 05:30:03 kernel: ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jul 08 05:30:03 kernel: ata5.00: irq_stat 0x40000000
Jul 08 05:30:03 kernel: ata5.00: failed command: READ DMA
Jul 08 05:30:03 kernel: ata5.00: cmd c8/00:00:00:08:00/00:00:00:00:00/e0 tag 26 dma 131072 in
                                             res 41/02:00:00:00:00/00:00:00:00:00/00 Emask 0x1 (device error)
Jul 08 05:30:03 kernel: ata5.00: status: { DRDY ERR }
Jul 08 05:30:03 kernel: ata5.00: configured for UDMA/100
Jul 08 05:30:03 kernel: ata5: EH complete
Jul 08 05:30:03 kernel: ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jul 08 05:30:03 kernel: ata5.00: irq_stat 0x40000000
Jul 08 05:30:03 kernel: ata5.00: failed command: READ DMA
Jul 08 05:30:03 kernel: ata5.00: cmd c8/00:00:00:00:00/00:00:00:00:00/e0 tag 1 dma 131072 in
                                             res 41/02:00:00:00:00/00:00:00:00:00/00 Emask 0x1 (device error)
Jul 08 05:30:03 kernel: ata5.00: status: { DRDY ERR }
Jul 08 05:30:03 kernel: ata5.00: configured for UDMA/100
Jul 08 05:30:03 kernel: ata5: EH complete
Jul 08 05:30:03 kernel: ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jul 08 05:30:03 kernel: ata5.00: irq_stat 0x40000000
Jul 08 05:30:03 kernel: ata5.00: failed command: READ DMA
Jul 08 05:30:03 kernel: ata5.00: cmd c8/00:00:00:08:00/00:00:00:00:00/e0 tag 7 dma 131072 in
                                             res 41/02:00:00:00:00/00:00:00:00:00/00 Emask 0x1 (device error)
Jul 08 05:30:03 kernel: ata5.00: status: { DRDY ERR }
Jul 08 05:30:03 kernel: ata5.00: configured for UDMA/100
Jul 08 05:30:03 kernel: ata5: EH complete
Jul 08 05:30:04 kernel: ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jul 08 05:30:04 kernel: ata5.00: irq_stat 0x40000000
Jul 08 05:30:04 kernel: ata5.00: failed command: READ DMA
Jul 08 05:30:04 kernel: ata5.00: cmd c8/00:00:00:00:00/00:00:00:00:00/e0 tag 13 dma 131072 in
                                             res 41/02:00:00:00:00/00:00:00:00:00/00 Emask 0x1 (device error)
Jul 08 05:30:04 kernel: ata5.00: status: { DRDY ERR }
Jul 08 05:30:04 kernel: ata5.00: configured for UDMA/100
Jul 08 05:30:04 kernel: ata5: EH complete
Jul 08 05:30:04 kernel: ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jul 08 05:30:04 kernel: ata5.00: irq_stat 0x40000000
Jul 08 05:30:04 kernel: ata5.00: failed command: READ DMA
Jul 08 05:30:04 kernel: ata5.00: cmd c8/00:00:00:08:00/00:00:00:00:00/e0 tag 19 dma 131072 in
                                             res 41/02:00:00:00:00/00:00:00:00:00/00 Emask 0x1 (device error)
Jul 08 05:30:04 kernel: ata5.00: status: { DRDY ERR }
Jul 08 05:30:04 kernel: ata5.00: configured for UDMA/100
Jul 08 05:30:04 kernel: ata5: EH complete
Jul 08 05:30:05 kernel: ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jul 08 05:30:05 kernel: ata5.00: irq_stat 0x40000000
Jul 08 05:30:05 kernel: ata5.00: failed command: READ DMA
Jul 08 05:30:05 kernel: ata5.00: cmd c8/00:00:00:00:00/00:00:00:00:00/e0 tag 0 dma 131072 in
                                             res 41/02:00:00:00:00/00:00:00:00:00/00 Emask 0x1 (device error)
Jul 08 05:30:05 kernel: ata5.00: status: { DRDY ERR }
Jul 08 05:30:05 kernel: ata5.00: configured for UDMA/100
Jul 08 05:30:05 kernel: ata5: EH complete
Jul 08 05:30:05 kernel: ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jul 08 05:30:05 kernel: ata5.00: irq_stat 0x40000000
Jul 08 05:30:05 kernel: ata5.00: failed command: READ DMA
Jul 08 05:30:05 kernel: ata5.00: cmd c8/00:00:00:08:00/00:00:00:00:00/e0 tag 6 dma 131072 in
                                             res 41/02:00:00:00:00/00:00:00:00:00/00 Emask 0x1 (device error)
Jul 08 05:30:05 kernel: ata5.00: status: { DRDY ERR }
Jul 08 05:30:05 kernel: ata5.00: configured for UDMA/100
Jul 08 05:30:05 kernel: ata5: EH complete
Jul 08 05:30:05 kernel: ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jul 08 05:30:05 kernel: ata5.00: irq_stat 0x40000000
Jul 08 05:30:05 kernel: ata5.00: failed command: READ DMA
Jul 08 05:30:05 kernel: ata5.00: cmd c8/00:00:00:00:00/00:00:00:00:00/e0 tag 12 dma 131072 in
                                             res 41/02:00:00:00:00/00:00:00:00:00/00 Emask 0x1 (device error)
Jul 08 05:30:05 kernel: ata5.00: status: { DRDY ERR }
Jul 08 05:30:05 kernel: ata5.00: configured for UDMA/100
Jul 08 05:30:05 kernel: sd 5:0:0:0: [sdk] tag#12 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 08 05:30:05 kernel: sd 5:0:0:0: [sdk] tag#12 Sense Key : Hardware Error [current] 
Jul 08 05:30:05 kernel: sd 5:0:0:0: [sdk] tag#12 Add. Sense: No additional sense information
Jul 08 05:30:05 kernel: sd 5:0:0:0: [sdk] tag#12 CDB: Read(16) 88 00 00 00 00 00 00 00 00 00 00 00 01 00 00 00
Jul 08 05:30:05 kernel: blk_update_request: I/O error, dev sdk, sector 0 op 0x0:(READ) flags 0x0 phys_seg 32 prio class 0
Jul 08 05:30:05 kernel: ata5: EH complete
Jul 08 05:30:06 kernel: ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jul 08 05:30:06 kernel: ata5.00: irq_stat 0x40000000
Jul 08 05:30:06 kernel: ata5.00: failed command: READ DMA
Jul 08 05:30:06 kernel: ata5.00: cmd c8/00:00:00:08:00/00:00:00:00:00/e0 tag 18 dma 131072 in
                                             res 41/02:00:00:00:00/00:00:00:00:00/00 Emask 0x1 (device error)
Jul 08 05:30:06 kernel: ata5.00: status: { DRDY ERR }
Jul 08 05:30:06 kernel: ata5.00: configured for UDMA/100
Jul 08 05:30:06 kernel: sd 5:0:0:0: [sdk] tag#18 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 08 05:30:06 kernel: sd 5:0:0:0: [sdk] tag#18 Sense Key : Hardware Error [current] 
Jul 08 05:30:06 kernel: sd 5:0:0:0: [sdk] tag#18 Add. Sense: No additional sense information
Jul 08 05:30:06 kernel: sd 5:0:0:0: [sdk] tag#18 CDB: Read(16) 88 00 00 00 00 00 00 00 08 00 00 00 01 00 00 00
Jul 08 05:30:06 kernel: blk_update_request: I/O error, dev sdk, sector 2048 op 0x0:(READ) flags 0x0 phys_seg 32 prio class 0
Jul 08 05:30:06 kernel: ata5: EH complete
Jul 08 05:30:06 lvm[458780]:   1 logical volume(s) in volume group "ubuntu-vg" unmonitored
Jul 08 05:30:06 systemd[1]: lvm2-monitor.service: Succeeded.
Jul 08 05:30:06 systemd[1]: Stopped Monitoring of LVM2 mirrors, snapshots etc. using dmeventd or progress polling.
Jul 08 05:30:06 systemd[1]: Reached target Shutdown.
Jul 08 05:30:06 systemd[1]: Reached target Final Step.
Jul 08 05:30:06 systemd[1]: systemd-reboot.service: Succeeded.
Jul 08 05:30:06 systemd[1]: Finished Reboot.
Jul 08 05:30:06 systemd[1]: Reached target Reboot.
Jul 08 05:30:06 systemd[1]: Shutting down.
Jul 08 05:30:06 systemd-shutdown[1]: Syncing filesystems and block devices.
Jul 08 05:30:06 systemd-journald[557]: Journal stopped
-- Reboot --

```

---

### Post by LHammonds on 2022-07-09
```
failed command: READ DMA
```
Either your drive is dying or you have a cable that needs to be re-seated or the passthru is not working correctly.  I have not utilized passthru on my VM since it is not necessary for me so I'm unsure about that process.

LHammonds

---

### Post by mellopete on 2022-07-09
You think that would cause it to shutdown? I just got a SAS expander. I will install it soon and move those drives off of the onboard SATA ports. I guess we'll see if that solves it. Thanks again!

---

