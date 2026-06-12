---
title: "Slow Startup"
date: 2020-03-13
forum: Ubuntu Development Version
---

### Post by rakeshshrs on 2020-03-13
It takes lots of time to boot.  systemd-analyze blame gives following output.
```
1min 1.837s plymouth-quit-wait.service                                         >    36.399s docker.service                                                     >
    29.352s dev-sda6.device                                                    >
    26.508s systemd-journal-flush.service                                      >
    22.891s apport-autoreport.service                                          >
    20.145s snapd.service                                                      >
    19.508s dev-loop33.device                                                  >
    19.170s dev-loop36.device                                                  >
    19.134s dev-loop22.device                                                  >
    19.008s dev-loop31.device                                                  >
    19.006s dev-loop32.device                                                  >
    19.004s dev-loop29.device                                                  >
    18.938s dev-loop34.device                                                  >
    18.904s dev-loop35.device                                                  >
    18.612s networkd-dispatcher.service                                        >
    17.835s nmbd.service                                                       >
    17.729s dev-loop11.device                                                  >
    17.621s dev-loop26.device                                                  >
    17.508s dev-loop19.device                                                  >
    17.441s dev-loop25.device                                                  >
    17.046s dev-loop27.device                                                  >
    16.931s dev-loop20.device                                                  >
    16.910s dev-loop23.device                                                  >
    16.636s dev-loop24.device                                                  >
    16.618s dev-loop30.device                                                  >
    16.405s dev-loop28.device                                                  >
    16.371s dev-loop15.device                                                  >
    16.315s dev-loop2.device                                                   >
    16.248s udisks2.service                                                    >
    15.447s dev-loop13.device                                                  >
    15.391s dev-loop18.device                                                  >
    15.114s dev-loop21.device                                                  >
    14.959s dev-loop5.device                                                   >
    14.918s dev-loop9.device                                                   >
    14.909s dev-loop10.device                                                  >
    14.059s dev-loop16.device                                                  >
    13.933s dev-loop12.device                                                  >
    13.829s dev-loop17.device                                                  >
    13.763s dev-loop8.device                                                   >
    13.668s dev-loop14.device                                                  >
    13.463s NetworkManager-wait-online.service                                 >
    13.383s dev-loop6.device                                                   >
    13.377s dev-loop1.device                                                   >
    13.329s dev-loop7.device                                                   >
    13.271s dev-loop0.device                                                   >
    13.216s dev-loop4.device                                                   >
    12.834s systemd-logind.service                                             >
    12.539s dev-loop3.device                                                   >
    12.212s accounts-daemon.service                                            >
    11.849s tomcat8.service                                                    >
    11.837s systemd-resolved.service                                           >
    10.965s grub-common.service                                                >
    10.858s apport.service                                                     >
    10.838s avahi-daemon.service                                               >
    10.767s preload.service                                                    >
    10.282s bluetooth.service                                                  >
    10.254s NetworkManager.service                                             >
    10.081s grub-initrd-fallback.service                                       >
     9.911s polkit.service                                                     >
     9.786s gpu-manager.service                                                >
     9.765s rsyslog.service                                                    >
     9.583s lm-sensors.service                                                 >
     9.485s switcheroo-control.service                                         >
     9.334s wpa_supplicant.service                                             >
     9.049s sysstat.service                                                    >
     8.714s ModemManager.service                                               >
     7.744s systemd-udevd.service                                              >
     6.372s apparmor.service                                                   >
     4.783s upower.service                                                     >
     4.207s colord.service                                                     >
     3.454s winbind.service                                                    >
     3.437s snap-atom-247.mount                                                >
     3.239s snap-atom-248.mount                                                >
     3.136s snap-code-25.mount                                                 >
     3.120s snap-code-26.mount                                                 >
     3.017s snap-core-8592.mount                                               >
     2.912s snap-core-8689.mount                                               >
     2.853s ssh.service                                                        >
     2.826s snap-core18-1650.mount                                             >
     2.778s snap-core18-1668.mount                                             >
     2.732s snap-gnome\x2d3\x2d26\x2d1604-97.mount                             >
     2.728s snap-gnome\x2d3\x2d26\x2d1604-98.mount                             >
     2.333s snap-gnome\x2d3\x2d28\x2d1804-110.mount                            >
     2.198s snap-gnome\x2d3\x2d28\x2d1804-116.mount                            >
     2.156s snap-gnome\x2dcalculator-536.mount                                 >
     2.035s snap-gnome\x2dcalculator-544.mount                                 >
     2.012s snap-gnome\x2dcharacters-375.mount                                 >
     1.967s snap-gnome\x2dcharacters-399.mount                                 >
     1.897s snap-gnome\x2dlogs-73.mount                                        >
     1.771s systemd-modules-load.service                                       >
     1.733s snap-gnome\x2dlogs-81.mount                                        >
     1.709s gdm.service                                                        >
     1.663s systemd-rfkill.service                                             >
     1.587s snap-gnome\x2dsystem\x2dmonitor-123.mount                          >
     1.567s systemd-timesyncd.service                                          >
     1.479s networking.service                                                 >
     1.452s fwupd.service                                                      >
     1.440s systemd-tmpfiles-setup.service                                     >
     1.435s snap-gnome\x2dsystem\x2dmonitor-127.mount                          >
     1.401s dns-clean.service                                                  >
     1.396s snap-gtk\x2dcommon\x2dthemes-1353.mount                            >
     1.369s snap-gtk\x2dcommon\x2dthemes-1440.mount                            >
     1.270s systemd-tmpfiles-setup-dev.service                                 >
     1.264s snap-notes-4.mount                                                 >
     1.192s snap-onenote\x2ddesktop-9.mount                                    >
     1.143s kerneloops.service                                                 >
     1.033s systemd-sysusers.service                                           >
     1.018s snap-postman-100.mount                                             >
      967ms snap-postman-99.mount                                              >
      954ms snap-projectlibre-3.mount                                          >
      922ms smbd.service                                                       >
      890ms systemd-sysctl.service                                             >
      849ms snap-pulseaudio-9.mount                                            >
      789ms e2scrub_reap.service                                               >
      766ms systemd-random-seed.service                                        >
      764ms systemd-journald.service                                           >
      761ms keyboard-setup.service                                             >
      758ms lvm2-monitor.service                                               >
      757ms systemd-udev-trigger.service                                       >
      735ms snap-rambox-10.mount                                               >
      715ms snapd.seeded.service                                               >
      682ms user@1000.service                                                  >
      679ms systemd-backlight@backlight:intel_backlight.service                >
      652ms ufw.service                                                        >
      641ms snap-rambox-11.mount                                               >
      569ms snap-tusk-29.mount                                                 >
      547ms snap-remmina-3968.mount                                            >
      474ms snap-remmina-3995.mount                                            >
      460ms pppd-dns.service                                                   >
      410ms alsa-restore.service                                               >
      393ms packagekit.service                                                 >
      356ms containerd.service                                                 >
      351ms openvpn.service                                                    >
      312ms snap-telegram\x2ddesktop-1038.mount                                >
      308ms snap-standard\x2dnotes-3.mount                                     >
      306ms ifupdown-pre.service                                               >
      302ms systemd-user-sessions.service                                      >
      287ms snap-standard\x2dnotes-4.mount                                     >
      282ms snap-telegram\x2ddesktop-1034.mount                                >
      273ms kmod-static-nodes.service                                          >
      255ms systemd-remount-fs.service                                         >
      248ms systemd-update-utmp.service                                        >
      226ms dev-disk-by\x2duuid-e083cc65\x2db9e7\x2d44c7\x2da139\x2dcf4e1fff729>
      204ms console-setup.service                                              >
      127ms dev-hugepages.mount                                                >
      126ms dev-mqueue.mount                                                   >
      124ms sys-kernel-debug.mount                                             >
      119ms blk-availability.service                                           >
       89ms user-runtime-dir@1000.service                                      >
       72ms systemd-update-utmp-runlevel.service                               >
       35ms plymouth-start.service                                             >
       31ms ureadahead-stop.service                                            >
       29ms setvtrgb.service                                                   >
       27ms rtkit-daemon.service                                               >
       20ms plymouth-read-write.service                                        >
       12ms finalrd.service                                                    >
        7ms docker.socket                                                      >
        6ms sys-kernel-config.mount                                            >
        5ms sys-fs-fuse-connections.mount                                      >
        5ms snapd.socket 
```

---

### Post by u666sa on 2020-03-13
Post /var/log/boot.log

---

### Post by HermanAB on 2020-03-14
Looks to me like a network problem.

In general, the solution to start-up speed problems is to avoid starting up - use suspend.

---

### Post by rakeshshrs on 2020-03-14
```
OK   Started Network Name Resolution
 OK   Started Remove Stale Onlinâ&#8364;¦ext4 Metadata Check Snapshots
 OK   Started Detect the availabâ&#8364;¦ deal with any system changes
 OK   Started Restore /etc/resolâ&#8364;¦re the ppp link was shut down
 OK   Started Resets System Activity Data Collector
 OK   Started GRUB failed boot detection
 OK   Started Initialize hardware monitoring sensors
 OK   Started LSB: automatic crash report generation
 OK   Started LSB: Record successful boot for GRUB
 OK   Started WPA supplicant
 OK   Started Switcheroo Control Proxy service
 OK   Started System Logging Service
 OK   Started Network Manager
 OK   Started Authorization Manager
 OK   Started Avahi mDNS/DNS-SD Stack
 OK   Reached target Network
 OK   Reached target Host and Network Name Lookups
         Starting Modem Manager..
         Starting Network Manager Wait Online..
         Starting Save/Restore Sound Card State..
         Starting Bluetooth service..
         Starting Manage, Install and Generate Color Profiles..
         Starting containerd container runtime..
 OK   Started Make remote CUPS printers available locally
         Starting MySQL Community Server..
         Starting OpenVPN service..
         Starting PostgreSQL Cluster 10-main..
         Starting PostgreSQL Cluster 12-main..
 OK   Started Service for snap aâ&#8364;¦ication pulseaudio.pulseaudio
         Starting OpenBSD Secure Shell server..
         Starting Hostname Service..
         Starting Load/Save RF Kill Switch Status..
         Starting Permit User Sessions..
 OK   Started LSB: Adaptive readahead daemon
 OK   Started OpenVPN service
         Stopping CUPS Scheduler..
 OK   Stopped CUPS Scheduler
 OK   Started CUPS Scheduler
 OK   Started Permit User Sessions
 OK   Started AnyDesk
         Starting GNOME Display Manager..
         Starting Hold until boot process finishes up..
 OK   Started Save/Restore Sound Card State
 OK   Reached target Sound Card
 OK   Started containerd container runtime
 OK   Started Bluetooth service
 OK   Reached target Bluetooth
 OK   Started Load/Save RF Kill Switch Status
 OK   Started Login Service
 OK   Started Unattended Upgrades Shutdown
 OK   Started Accounts Service
 OK   Started OpenBSD Secure Shell server
 OK   Started Hostname Service
 OK   Started GNOME Display Manager
 OK   Started Manage, Install and Generate Color Profiles
------------ Fri Mar 13 17:42:47 +0545 2020 ------------
ln: /tmp/mountroot-fail-hooks.d//scripts/init-premount/lvm2: No such file or directory
/dev/sda6: clean, 1887247/6160384 files, 12581964/24623360 blocks
 OK   Started Tell Plymouth To Write Out Runtime Data
 OK   Started Clean up any mess left by 0dns-up
 OK   Started Load AppArmor profiles
         Starting Raise network interfaces..
 OK   Started Raise network interfaces
 OK   Started udev Kernel Device Manager
         Starting Show Plymouth Boot Screen..
 OK   Started Show Plymouth Boot Screen
 OK   Started Forward Password Râ&#8364;¦s to Plymouth Directory Watch
 OK   Reached target Local Encrypted Volumes
 OK   Created slice system-systemd\x2dbacklight.slice
         Starting Load/Save Screen â&#8364;¦f backlight:intel_backlight..
 OK   Started Load/Save Screen Bâ&#8364;¦ of backlight:intel_backlight
 OK   Started Flush Journal to Persistent Storage
 OK   Listening on Load/Save RF â&#8364;¦itch Status /dev/rfkill Watch
         Starting Create Volatile Files and Directories..
         Starting Load/Save RF Kill Switch Status..
 OK   Started Load/Save RF Kill Switch Status
 OK   Started Create Volatile Files and Directories
         Starting Tell Plymouth To Write Out Runtime Data..
         Starting Show Plymouth Boot Screen..
------------ Fri Mar 13 17:43:07 +0545 2020 ------------
         Starting Network Name Resolution..
         Starting Network Time Synchronization..
         Starting Update UTMP about System Boot/Shutdown..
 OK   Started Tell Plymouth To Write Out Runtime Data
 OK   Started Show Plymouth Boot Screen
 OK   Started Update UTMP about System Boot/Shutdown
 OK   Started Network Time Synchronization
 OK   Reached target System Time Set
 OK   Reached target System Time Synchronized
 OK   Found device TOSHIBA_MQ01ABF050 5
         Activating swap /dev/disk/â&#8364;¦b9e7-44c7-a139-cf4e1fff7290..
 OK   Activated swap /dev/disk/bâ&#8364;¦5-b9e7-44c7-a139-cf4e1fff7290
 OK   Reached target Swap
 OK   Reached target System Initialization
 OK   Started ACPI Events Check
 OK   Started Process error repoâ&#8364;¦rting is enabled (file watch)
 OK   Started CUPS Scheduler
 OK   Started Trigger anacron every hour
 OK   Started Daily apt download activities
 OK   Started Daily apt upgrade and clean activities
 OK   Started Periodic ext4 Onliâ&#8364;¦ata Check for All Filesystems
 OK   Started Discard unused blocks once a week
 OK   Started Refresh fwupd metadata regularly
 OK   Started Daily rotation of log files
 OK   Started Daily man-db regeneration
 OK   Started Message of the Day
 OK   Started Clean PHP session files every 30 mins
 OK   Started Daily Cleanup of Temporary Directories
 OK   Reached target Paths
 OK   Reached target Timers
 OK   Listening on ACPID Listen Socket
 OK   Listening on Avahi mDNS/DNS-SD Stack Activation Socket
 OK   Listening on CUPS Scheduler
 OK   Listening on D-Bus System Message Bus Socket
         Starting Docker Socket for the API
         Starting Socket activation for snappy daemon
 OK   Listening on UUID daemon activation socket
 OK   Started Network Name Resolution
 OK   Listening on Docker Socket for the API
 OK   Listening on Socket activation for snappy daemon
 OK   Reached target Host and Network Name Lookups
 OK   Reached target Sockets
 OK   Reached target Basic System
         Starting Accounts Service..
 OK   Started ACPI event daemon
 OK   Started Run anacron jobs
         Starting LSB: automatic crash report generation..
         Starting Avahi mDNS/DNS-SD Stack..
         Starting Bluetooth service..
 OK   Started Regular background program processing daemon
 OK   Started CUPS Scheduler
 OK   Started D-Bus System Message Bus
         Starting Network Manager..
 OK   Started Save initial kernel messages after boot
         Starting Remove Stale Onliâ&#8364;¦t4 Metadata Check Snapshots..
 OK   Reached target Login Prompts
         Starting Detect the availaâ&#8364;¦eal with any system changes..
         Starting LSB: Record successful boot for GRUB..
         Starting GRUB failed boot detection..
 OK   Started irqbalance daemon
         Starting Initialize hardware monitoring sensors..
         Starting Dispatcher daemon for systemd-networkd..
 OK   Started Set the CPU Frequency Scaling governor
         Starting Authorization Manager..
         Starting Restore /etc/resoâ&#8364;¦ the ppp link was shut down..
         Starting LSB: Adaptive readahead daemon..
         Starting System Logging Service..
         Starting Snappy daemon..
         Starting Switcheroo Control Proxy service..
         Starting Resets System Activity Data Collector..
         Starting Login Service..
         Starting Disk Manager..
         Starting WPA supplicant..
 OK   Started Remove Stale Onlinâ&#8364;¦ext4 Metadata Check Snapshots
 OK   Started Detect the availabâ&#8364;¦ deal with any system changes
 OK   Started Restore /etc/resolâ&#8364;¦re the ppp link was shut down
 OK   Started Resets System Activity Data Collector
 OK   Started Initialize hardware monitoring sensors
 OK   Started GRUB failed boot detection
 OK   Started Bluetooth service
 OK   Started WPA supplicant
 OK   Started System Logging Service
 OK   Started Switcheroo Control Proxy service
 OK   Started Authorization Manager
 OK   Started Network Manager
 OK   Started Avahi mDNS/DNS-SD Stack
 OK   Reached target Bluetooth
 OK   Reached target Network
         Starting Modem Manager..
         Starting Network Manager Wait Online..
         Starting Save/Restore Sound Card State..
         Starting Manage, Install and Generate Color Profiles..
         Starting containerd container runtime..
 OK   Started Make remote CUPS printers available locally
         Starting MySQL Community Server..
         Starting OpenVPN service..
         Starting PostgreSQL Cluster 10-main..
         Starting PostgreSQL Cluster 12-main..
 OK   Started Service for snap aâ&#8364;¦ication pulseaudio.pulseaudio
         Starting OpenBSD Secure Shell server..
         Starting Hostname Service..
         Starting Permit User Sessions..
 OK   Started LSB: automatic crash report generation
 OK   Started containerd container runtime
 OK   Started OpenVPN service
 OK   Started Save/Restore Sound Card State
 OK   Reached target Sound Card
 OK   Started Permit User Sessions
 OK   Started AnyDesk
         Starting GNOME Display Manager..
         Starting Hold until boot process finishes up..
 OK   Started LSB: Record successful boot for GRUB
 OK   Started LSB: Adaptive readahead daemon
 OK   Started Login Service
 OK   Started Unattended Upgrades Shutdown
 OK   Started Hostname Service
 OK   Started Accounts Service
 OK   Started GNOME Display Manager
 OK   Started OpenBSD Secure Shell server
 OK   Started Manage, Install and Generate Color Profiles
         Starting Network Manager Script Dispatcher Service..
 OK   Started Network Manager Script Dispatcher Service
------------ Fri Mar 13 17:55:19 +0545 2020 ------------
ln: /tmp/mountroot-fail-hooks.d//scripts/init-premount/lvm2: No such file or directory
/dev/sda6: clean, 1887160/6160384 files, 12594456/24623360 blocks
 OK   Started Tell Plymouth To Write Out Runtime Data
 OK   Started Clean up any mess left by 0dns-up
 OK   Started Load AppArmor profiles
         Starting Raise network interfaces..
 OK   Started Raise network interfaces
 OK   Started udev Kernel Device Manager
         Starting Show Plymouth Boot Screen..
 OK   Started Show Plymouth Boot Screen
 OK   Started Forward Password Râ&#8364;¦s to Plymouth Directory Watch
 OK   Reached target Local Encrypted Volumes
 OK   Created slice system-systemd\x2dbacklight.slice
         Starting Load/Save Screen â&#8364;¦f backlight:intel_backlight..
 OK   Started Load/Save Screen Bâ&#8364;¦ of backlight:intel_backlight
 OK   Listening on Load/Save RF â&#8364;¦itch Status /dev/rfkill Watch
         Starting Load/Save RF Kill Switch Status..
 OK   Started Flush Journal to Persistent Storage
         Starting Create Volatile Files and Directories..
 OK   Started Load/Save RF Kill Switch Status
         Starting Tell Plymouth To Write Out Runtime Data..
         Starting Show Plymouth Boot Screen..
------------ Fri Mar 13 17:55:39 +0545 2020 ------------
 OK   Started Tell Plymouth To Write Out Runtime Data
 OK   Started Show Plymouth Boot Screen
         Starting Tell Plymouth To Write Out Runtime Data..
         Starting Show Plymouth Boot Screen..
------------ Fri Mar 13 17:55:40 +0545 2020 ------------
 OK   Started Tell Plymouth To Write Out Runtime Data
 OK   Started Show Plymouth Boot Screen
 OK   Started Create Volatile Files and Directories
         Starting Network Name Resolution..
         Starting Network Time Synchronization..
         Starting Update UTMP about System Boot/Shutdown..
 OK   Started Update UTMP about System Boot/Shutdown
 OK   Found device TOSHIBA_MQ01ABF050 5
         Activating swap /dev/disk/â&#8364;¦b9e7-44c7-a139-cf4e1fff7290..
 OK   Started Network Time Synchronization
 OK   Reached target System Time Set
 OK   Reached target System Time Synchronized
 OK   Activated swap /dev/disk/bâ&#8364;¦5-b9e7-44c7-a139-cf4e1fff7290
 OK   Reached target Swap
 OK   Reached target System Initialization
 OK   Started ACPI Events Check
 OK   Started Process error repoâ&#8364;¦rting is enabled (file watch)
 OK   Started CUPS Scheduler
 OK   Started Trigger anacron every hour
 OK   Started Daily apt download activities
 OK   Started Daily apt upgrade and clean activities
 OK   Started Periodic ext4 Onliâ&#8364;¦ata Check for All Filesystems
 OK   Started Discard unused blocks once a week
 OK   Started Refresh fwupd metadata regularly
 OK   Started Daily rotation of log files
 OK   Started Daily man-db regeneration
 OK   Started Message of the Day
 OK   Started Clean PHP session files every 30 mins
 OK   Started Daily Cleanup of Temporary Directories
 OK   Reached target Paths
 OK   Reached target Timers
 OK   Listening on ACPID Listen Socket
 OK   Listening on Avahi mDNS/DNS-SD Stack Activation Socket
 OK   Listening on CUPS Scheduler
 OK   Listening on D-Bus System Message Bus Socket
         Starting Docker Socket for the API
         Starting Socket activation for snappy daemon
 OK   Listening on UUID daemon activation socket
 OK   Listening on Docker Socket for the API
 OK   Listening on Socket activation for snappy daemon
 OK   Reached target Sockets
 OK   Reached target Basic System
         Starting Accounts Service..
 OK   Started ACPI event daemon
 OK   Started Run anacron jobs
         Starting LSB: automatic crash report generation..
         Starting Avahi mDNS/DNS-SD Stack..
         Starting Bluetooth service..
 OK   Started Regular background program processing daemon
 OK   Started CUPS Scheduler
 OK   Started D-Bus System Message Bus
         Starting Network Manager..
 OK   Started Save initial kernel messages after boot
         Starting Remove Stale Onliâ&#8364;¦t4 Metadata Check Snapshots..
 OK   Reached target Login Prompts
         Starting Detect the availaâ&#8364;¦eal with any system changes..
         Starting LSB: Record successful boot for GRUB..
         Starting GRUB failed boot detection..
 OK   Started irqbalance daemon
         Starting Initialize hardware monitoring sensors..
         Starting Dispatcher daemon for systemd-networkd..
 OK   Started Set the CPU Frequency Scaling governor
         Starting Authorization Manager..
         Starting Restore /etc/resoâ&#8364;¦ the ppp link was shut down..
         Starting LSB: Adaptive readahead daemon..
         Starting System Logging Service..
         Starting Snappy daemon..
         Starting Switcheroo Control Proxy service..
         Starting Resets System Activity Data Collector..
         Starting Login Service..
         Starting Disk Manager..
         Starting WPA supplicant..
 OK   Started Network Name Resolution
 OK   Started Remove Stale Onlinâ&#8364;¦ext4 Metadata Check Snapshots
 OK   Reached target Host and Network Name Lookups
 OK   Started Detect the availabâ&#8364;¦ deal with any system changes
 OK   Started Restore /etc/resolâ&#8364;¦re the ppp link was shut down
 OK   Started Resets System Activity Data Collector
 OK   Started Initialize hardware monitoring sensors
 OK   Started GRUB failed boot detection
 OK   Started Bluetooth service
 OK   Started System Logging Service
 OK   Started WPA supplicant
 OK   Started Switcheroo Control Proxy service
 OK   Started Authorization Manager
 OK   Reached target Bluetooth
         Starting Modem Manager..
         Starting Save/Restore Sound Card State..
         Starting Manage, Install and Generate Color Profiles..
 OK   Started Save/Restore Sound Card State
 OK   Reached target Sound Card
         Starting Hostname Service..
 OK   Started Avahi mDNS/DNS-SD Stack
 OK   Started Make remote CUPS printers available locally
 OK   Started LSB: automatic crash report generation
 OK   Started Network Manager
 OK   Reached target Network
         Starting Network Manager Wait Online..
         Starting containerd container runtime..
         Starting MySQL Community Server..
         Starting OpenVPN service..
         Starting PostgreSQL Cluster 10-main..
         Starting PostgreSQL Cluster 12-main..
 OK   Started Service for snap aâ&#8364;¦ication pulseaudio.pulseaudio
         Starting OpenBSD Secure Shell server..
         Starting Permit User Sessions..
 OK   Started OpenVPN service
 OK   Started LSB: Record successful boot for GRUB
 OK   Started containerd container runtime
 OK   Started Permit User Sessions
 OK   Started AnyDesk
         Starting GNOME Display Manager..
         Starting Hold until boot process finishes up..
 OK   Started LSB: Adaptive readahead daemon
 OK   Started Accounts Service
 OK   Started Hostname Service
 OK   Started Login Service
 OK   Started Unattended Upgrades Shutdown
 OK   Started GNOME Display Manager
 OK   Started Manage, Install and Generate Color Profiles
------------ Fri Mar 13 18:11:50 +0545 2020 ------------
ln: /tmp/mountroot-fail-hooks.d//scripts/init-premount/lvm2: No such file or directory
/dev/sda6: clean, 1887372/6160384 files, 12595945/24623360 blocks
 OK   Started Tell Plymouth To Write Out Runtime Data
 OK   Started Clean up any mess left by 0dns-up
 OK   Started Load AppArmor profiles
         Starting Raise network interfaces..
 OK   Started udev Kernel Device Manager
         Starting Show Plymouth Boot Screen..
 OK   Started Show Plymouth Boot Screen
 OK   Started Forward Password Râ&#8364;¦s to Plymouth Directory Watch
 OK   Reached target Local Encrypted Volumes
 OK   Started Raise network interfaces
 OK   Created slice system-systemd\x2dbacklight.slice
         Starting Load/Save Screen â&#8364;¦f backlight:intel_backlight..
 OK   Started Load/Save Screen Bâ&#8364;¦ of backlight:intel_backlight
 OK   Listening on Load/Save RF â&#8364;¦itch Status /dev/rfkill Watch
         Starting Load/Save RF Kill Switch Status..
         Starting Tell Plymouth To Write Out Runtime Data..
         Starting Show Plymouth Boot Screen..
------------ Fri Mar 13 18:12:09 +0545 2020 ------------
 OK   Started Tell Plymouth To Write Out Runtime Data
 OK   Started Show Plymouth Boot Screen
 OK   Started Load/Save RF Kill Switch Status
 OK   Started Flush Journal to Persistent Storage
         Starting Create Volatile Files and Directories..
 OK   Started Create Volatile Files and Directories
         Starting Network Name Resolution..
         Starting Network Time Synchronization..
         Starting Update UTMP about System Boot/Shutdown..
 OK   Started Update UTMP about System Boot/Shutdown
 OK   Found device TOSHIBA_MQ01ABF050 5
         Activating swap /dev/disk/â&#8364;¦b9e7-44c7-a139-cf4e1fff7290..
 OK   Activated swap /dev/disk/bâ&#8364;¦5-b9e7-44c7-a139-cf4e1fff7290
 OK   Reached target Swap
 OK   Started Network Time Synchronization
 OK   Reached target System Initialization
 OK   Started ACPI Events Check
 OK   Started Process error repoâ&#8364;¦rting is enabled (file watch)
 OK   Started CUPS Scheduler
 OK   Started Daily Cleanup of Temporary Directories
 OK   Reached target Paths
 OK   Reached target System Time Set
 OK   Reached target System Time Synchronized
 OK   Started Trigger anacron every hour
 OK   Started Daily apt download activities
 OK   Started Daily apt upgrade and clean activities
 OK   Started Periodic ext4 Onliâ&#8364;¦ata Check for All Filesystems
 OK   Started Discard unused blocks once a week
 OK   Started Refresh fwupd metadata regularly
 OK   Started Daily rotation of log files
 OK   Started Daily man-db regeneration
 OK   Started Message of the Day
 OK   Started Clean PHP session files every 30 mins
 OK   Reached target Timers
 OK   Listening on ACPID Listen Socket
 OK   Listening on Avahi mDNS/DNS-SD Stack Activation Socket
 OK   Listening on CUPS Scheduler
 OK   Listening on D-Bus System Message Bus Socket
         Starting Docker Socket for the API
         Starting Socket activation for snappy daemon
 OK   Listening on UUID daemon activation socket
 OK   Listening on Docker Socket for the API
 OK   Listening on Socket activation for snappy daemon
 OK   Reached target Sockets
 OK   Reached target Basic System
         Starting Accounts Service..
 OK   Started ACPI event daemon
 OK   Started Run anacron jobs
         Starting LSB: automatic crash report generation..
         Starting Avahi mDNS/DNS-SD Stack..
         Starting Bluetooth service..
 OK   Started Regular background program processing daemon
 OK   Started CUPS Scheduler
 OK   Started D-Bus System Message Bus
         Starting Network Manager..
 OK   Started Save initial kernel messages after boot
         Starting Remove Stale Onliâ&#8364;¦t4 Metadata Check Snapshots..
 OK   Reached target Login Prompts
         Starting Detect the availaâ&#8364;¦eal with any system changes..
         Starting LSB: Record successful boot for GRUB..
         Starting GRUB failed boot detection..
 OK   Started irqbalance daemon
         Starting Initialize hardware monitoring sensors..
         Starting Dispatcher daemon for systemd-networkd..
 OK   Started Set the CPU Frequency Scaling governor
         Starting Authorization Manager..
         Starting Restore /etc/resoâ&#8364;¦ the ppp link was shut down..
         Starting LSB: Adaptive readahead daemon..
         Starting System Logging Service..
         Starting Snappy daemon..
         Starting Switcheroo Control Proxy service..
         Starting Resets System Activity Data Collector..
         Starting Login Service..
         Starting Disk Manager..
         Starting WPA supplicant..
 OK   Started Remove Stale Onlinâ&#8364;¦ext4 Metadata Check Snapshots
 OK   Started Restore /etc/resolâ&#8364;¦re the ppp link was shut down
 OK   Started Network Name Resolution
 OK   Started Detect the availabâ&#8364;¦ deal with any system changes
 OK   Started Resets System Activity Data Collector
 OK   Started Initialize hardware monitoring sensors
 OK   Started GRUB failed boot detection
 OK   Started Bluetooth service
 OK   Started WPA supplicant
 OK   Started System Logging Service
 OK   Started Switcheroo Control Proxy service
 OK   Started Network Manager
 OK   Started Authorization Manager
 OK   Reached target Bluetooth
 OK   Reached target Network
 OK   Reached target Host and Network Name Lookups
         Starting Modem Manager..
         Starting Network Manager Wait Online..
         Starting Save/Restore Sound Card State..
         Starting Manage, Install and Generate Color Profiles..
         Starting containerd container runtime..
         Starting OpenVPN service..
 OK   Started Service for snap aâ&#8364;¦ication pulseaudio.pulseaudio
         Starting OpenBSD Secure Shell server..
         Starting Hostname Service..
         Starting Permit User Sessions..
 OK   Started containerd container runtime
 OK   Started OpenVPN service
 OK   Started Avahi mDNS/DNS-SD Stack
 OK   Started Make remote CUPS printers available locally
 OK   Started LSB: automatic crash report generation
 OK   Started Save/Restore Sound Card State
 OK   Reached target Sound Card
 OK   Started Permit User Sessions
 OK   Started AnyDesk
         Starting GNOME Display Manager..
         Starting Hold until boot process finishes up..
 OK   Started LSB: Record successful boot for GRUB
 OK   Started LSB: Adaptive readahead daemon
 OK   Started Accounts Service
 OK   Started Hostname Service
 OK   Started GNOME Display Manager
 OK   Started OpenBSD Secure Shell server
 OK   Started Login Service
 OK   Started Unattended Upgrades Shutdown
         Starting Network Manager Script Dispatcher Service..
 OK   Started Manage, Install and Generate Color Profiles
 OK   Started Network Manager Script Dispatcher Service
------------ Sat Mar 14 21:51:15 +0545 2020 ------------
ln: /tmp/mountroot-fail-hooks.d//scripts/init-premount/lvm2: No such file or directory
/dev/sda6: clean, 1887602/6160384 files, 12599419/24623360 blocks
 OK   Started Tell Plymouth To Write Out Runtime Data
 OK   Started Clean up any mess left by 0dns-up
 OK   Started Load AppArmor profiles
         Starting Raise network interfaces..
 OK   Started Raise network interfaces
 OK   Started udev Kernel Device Manager
         Starting Show Plymouth Boot Screen..
 OK   Started Show Plymouth Boot Screen
 OK   Started Forward Password Râ&#8364;¦s to Plymouth Directory Watch
 OK   Reached target Local Encrypted Volumes
 OK   Created slice system-systemd\x2dbacklight.slice
         Starting Load/Save Screen â&#8364;¦f backlight:intel_backlight..
 OK   Started Load/Save Screen Bâ&#8364;¦ of backlight:intel_backlight
 OK   Listening on Load/Save RF â&#8364;¦itch Status /dev/rfkill Watch
         Starting Load/Save RF Kill Switch Status..
         Starting Tell Plymouth To Write Out Runtime Data..
         Starting Show Plymouth Boot Screen..
------------ Sat Mar 14 21:51:34 +0545 2020 ------------
 OK   Started Tell Plymouth To Write Out Runtime Data
 OK   Started Show Plymouth Boot Screen
 OK   Started Load/Save RF Kill Switch Status
         Starting Tell Plymouth To Write Out Runtime Data..
         Starting Show Plymouth Boot Screen..
------------ Sat Mar 14 21:51:35 +0545 2020 ------------
 OK   Started Tell Plymouth To Write Out Runtime Data
 OK   Started Show Plymouth Boot Screen
 OK   Started Flush Journal to Persistent Storage
         Starting Create Volatile Files and Directories..
 OK   Found device TOSHIBA_MQ01ABF050 5
         Activating swap /dev/disk/â&#8364;¦b9e7-44c7-a139-cf4e1fff7290..
 OK   Started Create Volatile Files and Directories
         Starting Network Name Resolution..
         Starting Network Time Synchronization..
         Starting Update UTMP about System Boot/Shutdown..
 OK   Activated swap /dev/disk/bâ&#8364;¦5-b9e7-44c7-a139-cf4e1fff7290
 OK   Reached target Swap
 OK   Started Update UTMP about System Boot/Shutdown
 OK   Started Network Time Synchronization
 OK   Reached target System Initialization
 OK   Started ACPI Events Check
 OK   Started Process error repoâ&#8364;¦rting is enabled (file watch)
 OK   Started CUPS Scheduler
 OK   Started Daily Cleanup of Temporary Directories
 OK   Reached target Paths
 OK   Reached target System Time Set
 OK   Reached target System Time Synchronized
 OK   Started Trigger anacron every hour
 OK   Started Daily apt download activities
 OK   Started Daily apt upgrade and clean activities
 OK   Started Periodic ext4 Onliâ&#8364;¦ata Check for All Filesystems
 OK   Started Discard unused blocks once a week
 OK   Started Refresh fwupd metadata regularly
 OK   Started Daily rotation of log files
 OK   Started Daily man-db regeneration
 OK   Started Message of the Day
 OK   Started Clean PHP session files every 30 mins
 OK   Reached target Timers
 OK   Listening on ACPID Listen Socket
 OK   Listening on Avahi mDNS/DNS-SD Stack Activation Socket
 OK   Listening on CUPS Scheduler
 OK   Listening on D-Bus System Message Bus Socket
         Starting Docker Socket for the API
         Starting Socket activation for snappy daemon
 OK   Listening on UUID daemon activation socket
 OK   Listening on Docker Socket for the API
 OK   Listening on Socket activation for snappy daemon
 OK   Reached target Sockets
 OK   Reached target Basic System
         Starting Accounts Service..
 OK   Started ACPI event daemon
         Starting LSB: automatic crash report generation..
         Starting Avahi mDNS/DNS-SD Stack..
         Starting Bluetooth service..
 OK   Started Regular background program processing daemon
 OK   Started CUPS Scheduler
 OK   Started D-Bus System Message Bus
         Starting Network Manager..
 OK   Started Save initial kernel messages after boot
         Starting Remove Stale Onliâ&#8364;¦t4 Metadata Check Snapshots..
 OK   Reached target Login Prompts
         Starting Detect the availaâ&#8364;¦eal with any system changes..
         Starting LSB: Record successful boot for GRUB..
         Starting GRUB failed boot detection..
 OK   Started irqbalance daemon
         Starting Initialize hardware monitoring sensors..
         Starting Dispatcher daemon for systemd-networkd..
 OK   Started Set the CPU Frequency Scaling governor
         Starting Clean php session files..
         Starting Authorization Manager..
         Starting Restore /etc/resoâ&#8364;¦ the ppp link was shut down..
         Starting LSB: Adaptive readahead daemon..
         Starting System Logging Service..
         Starting Snappy daemon..
         Starting Switcheroo Control Proxy service..
         Starting Resets System Activity Data Collector..
         Starting Login Service..
         Starting Disk Manager..
         Starting WPA supplicant..
 OK   Started Restore /etc/resolâ&#8364;¦re the ppp link was shut down
 OK   Started Network Name Resolution
 OK   Started Remove Stale Onlinâ&#8364;¦ext4 Metadata Check Snapshots
 OK   Started Detect the availabâ&#8364;¦ deal with any system changes
 OK   Started Resets System Activity Data Collector
 OK   Started Initialize hardware monitoring sensors
 OK   Started GRUB failed boot detection
 OK   Started Bluetooth service
 OK   Started WPA supplicant
 OK   Started Switcheroo Control Proxy service
 OK   Started Network Manager
 OK   Started System Logging Service
 OK   Started Authorization Manager
 OK   Reached target Bluetooth
 OK   Reached target Network
 OK   Reached target Host and Network Name Lookups
         Starting Modem Manager..
         Starting Network Manager Wait Online..
         Starting Save/Restore Sound Card State..
         Starting Manage, Install and Generate Color Profiles..
         Starting containerd container runtime..
         Starting OpenVPN service..
 OK   Started Service for snap aâ&#8364;¦ication pulseaudio.pulseaudio
         Starting OpenBSD Secure Shell server..
         Starting Permit User Sessions..
 OK   Started OpenVPN service
 OK   Started Save/Restore Sound Card State
 OK   Reached target Sound Card
 OK   Started LSB: automatic crash report generation
 OK   Started Permit User Sessions
 OK   Started AnyDesk
         Starting GNOME Display Manager..
         Starting Hold until boot process finishes up..
 OK   Started Avahi mDNS/DNS-SD Stack
 OK   Started Make remote CUPS printers available locally
 OK   Started LSB: Record successful boot for GRUB
 OK   Started containerd container runtime
         Starting Hostname Service..
 OK   Started Login Service
 OK   Started Unattended Upgrades Shutdown
 OK   Started Hostname Service
 OK   Started LSB: Adaptive readahead daemon
 OK   Started Accounts Service
 OK   Started GNOME Display Manager
 OK   Started Manage, Install and Generate Color Profiles
 OK   Started OpenBSD Secure Shell server
```

---

### Post by rakeshshrs on 2020-03-14
There seems to be lots of service that are in startup as seen above.  Can we suspend some of them?

---

### Post by TheFu on 2020-03-14
which OS and release?

---

### Post by rakeshshrs on 2020-03-14
It's Ubuntu 20.04. I had same problem when I had 18.04 too. Upgraded 2 weeks ago.
It's dual boot with Windows 10.

---

### Post by oldfred on 2020-03-14
Do you use snaps? Or can use .deb standard installs?
I remove all snaps.

Slow Boot --------------------------------
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

[https://askubuntu.com/questions/1187117/slow-boot-boot-19-10-tried-almost-everything](https://askubuntu.com/questions/1187117/slow-boot-boot-19-10-tried-almost-everything) & 

[https://askubuntu.com/questions/1018576/what-does-networkmanager-wait-online-service-do](https://askubuntu.com/questions/1018576/what-does-networkmanager-wait-online-service-do) & 
[https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service](https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service)

turned off NetworkManager-wait with systemctl
changed from quiet splash to noplymouth, will see boot process rather than Ubuntu logo
sudo apt install libblockdev-crypto2 libblockdev-mdraid2
turned off printer when rebooting
removed snaps

If UEFI firmware update not supported (yet)
sudo apt-get purge fwupd
I just reinstalled it as it supposedly will start to support my new SSD. And it now at least recognizes my motherboard.

Biggest improvement was from throwing newer hardware at it. New NVMe drive.
fred@fred-Z170N-focal:~$ systemd-analyze
Startup finished in 3.373s (kernel) + 5.482s (userspace) = 8.856s 
graphical.target reached after 5.472s in userspace

---

### Post by TheFu on 2020-03-15
> **rakeshshrs said:**
> It's Ubuntu 20.04. I had same problem when I had 18.04 too. Upgraded 2 weeks ago.
It's dual boot with Windows 10.

Dude, 20.04 isn't released.  It is alpha software.  This post needs to be moved to the Development Ubuntu sub-forum.  Thank you for testing pre-release software.  New is the enemy of stable.

---

### Post by oldfred on 2020-03-15
Moved to development release.

---

### Post by VMC on 2020-03-15
```
sudo apt purge snapd
```

Also what device is SDA6? Hard drive or usb. What did you install it on.

---

### Post by edkmho on 2020-03-20
is it possible to disable snap???

I wanted to disable not to remove entirely.

Any help will be much appreciated.

---

### Post by zika on 2020-03-21
Yes:```
 :~$ apt search snapdSorting... Done
Full Text Search... Done
fuse-emulator-utils/focal 1.4.3-1 amd64
  The Free Unix Spectrum Emulator - Utilities


gir1.2-snapd-1/focal,now 1.56-0ubuntu1 amd64 [installed,automatic]
  Typelib file for libsnapd-glib1


golang-github-snapcore-snapd-dev/focal 2.44+20.04 all
  snappy development go packages.


libsnapd-glib-dev/focal 1.56-0ubuntu1 amd64
  GLib snapd library (development files)


libsnapd-glib1/focal,now 1.56-0ubuntu1 amd64 [installed,automatic]
  GLib snapd library


libsnapd-qt-dev/focal 1.56-0ubuntu1 amd64
  Qt snapd library (development files)


libsnapd-qt1/focal 1.56-0ubuntu1 amd64
  Qt snapd library


node-snapdragon/focal 0.12.0+repack-2 all
  Fast, pluggable and easy-to-use parser-renderer factory


node-snapdragon-node/focal 3.0.0-1 all
  Snapdragon utility to create a new AST node in some node


node-snapdragon-token/focal 4.0.0-1 all
  Create a snapdragon token


node-snapdragon-util/focal 5.0.1-1 all
  Utilities for the snapdragon parser/compiler


qml-module-snapd/focal 1.56-0ubuntu1 amd64
  Snapd QML module


snap-confine/focal 2.44+20.04 amd64
  Transitional package for snapd


snapd/focal 2.44+20.04 amd64
  Daemon and tooling that enable snap packages


snapd-glib-tests/focal 1.56-0ubuntu1 amd64
  GLib snapd library (installed tests)


snapd-xdg-open/focal 2.44+20.04 amd64
  Transitional package for snapd-xdg-open


ubuntu-core-launcher/focal 2.44+20.04 amd64
  Transitional package for snapd


ubuntu-core-snapd-units/focal 2.44+20.04 all
  transitional dummy package


zsnapd/focal 0.8.9d-2 all
  ZFS Snapshot Daemon written in python


zsnapd-rcmd/focal 0.8.9d-2 all
  Remote sshd command checker for ZFS Snapshot Daemon
```... I did remove it (almost) all. Before removing be sure that You've installed all non-snap replacements...

---

### Post by webaake on 2020-03-21
That snap stuff scares me. Seems way too cumbersome and taxing. Seems smart to stay with 18.04 LTS as long as possible and see where 20.04 really amounts to. Not all Canonicals ideas are fruitful.

---

