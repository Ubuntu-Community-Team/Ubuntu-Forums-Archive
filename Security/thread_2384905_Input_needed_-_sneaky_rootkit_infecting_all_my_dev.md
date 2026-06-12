---
title: "Input needed - sneaky rootkit infecting all my devices (Ubuntu, Windows 10, OS X ++)"
date: 2018-02-13
forum: Security
---

### Post by xalu on 2018-02-13
Hey all,

**Short version:**
I tried to keep it brief and there is more to say, skip to the logs I posted if you don’t want to read and might be able to offer some advice.  I found that firefox’s omni.ja file was the target in my ubunu/lubuntu install but have had similar issues with chrome, edge,  safari etc. on windows, osx, and android.

I don't want to include the raw text as I'm not at all sure what it is, however it is using the  /usr/lib/firefox/browser/omni.ja file and I know this because once I removed it everything started working.  Now maybe I am wrong and something else is going on..however to have 1000 ports open and you haven't even typed anything into Firefox yet. 

Scan results from chkrootkit and rkhunter :  Attached at bottom as PDF’s


**Long version:**
So I've been grinding my head against this one a good couple of weeks, and I am getting somewhere but it's time for me to get some input. I've got something that either is capable of infecting windows / osx / android, and Ubuntu....or someone is really pissed off at me. I have issues on all devices that are all very similar. I thought it was external at first, and beefed up firewall with a new router but then discovered the requests were going out from my machines.


I believe (guessing) I have a rootkit installed in all my drives MBR, or something else. Maybe ram persistent or BIOS. I have results and some improvement after using chkrootkit. However,  I haven't had any issues with malware for a very long time so I wanted to have some eyes on my scan results of a brand new install. 

Every time I think I've got this issue solved it comes right back. First off it took me a while to get to chkrootkit and rkhunter because I was using window 10 when all this started. After trying multiple re-installs every possible anti-virus software that’s out there I decided I needed to come back to Ubuntu...and will be staying for a while I hope.

I installed Ubuntu. I set up ufw with gufw only allowing dns, http, https, and a few ports for spotify / private internet access. I also set my Xfinity gateway to max on firewall for IPV6 (basically suppose to block it) and set ipv4 to there version of Maximum. I was doing great for a good 5 or so days and just about ready to get back to working when I noticed some strange behavior. My firefox install was getting port hunger. I switched to chrome, not long after it was the same...so on and so forth.  I found chkrootkit and rkhunter which leads me here. 



I will have to fill in the details later but to sum up. I've had very little success getting any of them to admit there was any sign at all of malware despite the fact that all my devices have been opening hundreds (sometimes thousands) of  TCP ports and blasting out AWK requests. I have here a pdf that hopefully displays correctly. 

I am on lubuntu right now because the only clean disk I had was an old win7 dvd and an old hard drive that hadn’t been exposed. Afraid that I would immediately be infected when I connected my wifi I went for the smaller OS. I am burning an ubuntu disk now. 

I was having the same issues on this os since the ssd drive was used before during one of my re-installs. I tried to install with encryption (write over empty space to erase it but kept getting a message about insecure swap space which wasn't there. (possibly a hint at how its persisting across installs?)  I'm going to restart lubuntu and see if the omni.ja file comes back or changes.  I’ll be doing a ton of reading on the forum etc and I’ll post back here soon.

I'm slightly suspicious that it may be a combination of rootkit malware and live intrusion as I've seen changes happening while I am trying to stop the effects. Such as a menu tool opening in mac osx that I found only by checking recent files and then realizing it was open. I've tried who -a but never find anyone else.

I've collected a lot of logs from all the different platforms and I need to recover them from the infected hard drives. I will share more when I have it.  I've got much more to describe for all the different devices as each was slightly different, and creepy, in its own way. However the focus is on finding the definite source of this issue. This post is now much much longer than I intended, but with all the different OS’s its gotten complicated.

For now I humbly ask for any advice or input that may help get to the end of this long nightmare. I have someone waiting for me to finish a project and I really don't want to hand over a pile of malware.   


Important note for any who may find this during their struggle: Don't use USB sticks for OS installs when dealing with malware issues unless you make sure they are mounting read only..or you'll waste a whole LOT of time. Best to go with write once technology from the yesteryear’s  such as a CD / DVD disk :D

---

### Post by wyliecoyoteuk on 2018-02-14
Lynis may be of use.
Use a liveCD to examine the hard drive
the omin.ja is an archive, probably being used to launch the attacks.
try installing the noscript plugin
It may be a flash vuln.

---

### Post by xalu on 2018-02-16
Thanks for the tip. It very well could be the source of the infection as I was working on a react native package when this happened. 

Based on what I have seen so far this is what I believe is happening. It could easily be something else, but I have observed the events below live not just through log review.

Overview: Virus/Malware that can turn on/off wifi/Bluetooth/direct wifi. I had my android in airplane mode wifi off. Wifi came back and created an ap to connect. Either P2P Direct wifi or it will use standard wifi. I&#8217;ve seen this happen on both my macbook pro running latest OS X and on android samsung Note 5 running latest nouget. My note tried turing on mobile hotspot, I have a noroot firewall installed so it popped up. Also on my mac it would not let me shut off my wifi. It will also turn the mac back on if I turn it off unless I clear the NVRAM. 

I had a live cd going and it crashed before I could save to usb. I will load some more logs later. Here is a few for now:


The virus/malware  installs itself takes over the machine and commands (/sbin /bin /usr/run etc) while connecting over wifi with a socket listening on wifi. If you shut off wifi it will turn on, it will survive in ram, I found this out when I removed everything but the ram and dvd. It was still there. Once of the first folders it goes after is wpa_supplicant and bin etc.

It takes over services to open a path to connection: dbus, system.d, rsyslog, alsa-utils and possibly more. It masks its presence so you cannot see it in who, it&#8217;ll show as your uid.
 

I finally decided to test ram and there is was locked in memory causing errors. I cleared memory by hard resetting/powering off and on a few times. 


I just lost a bunch of logs and my write-up when the live cd crashed before I saved to usb. I had a good collection of scans with chkroot and rkhunter which I lost. The ones I have now look the same as the one I already attached.  So I'll attach a few snippets and when I have some time I hav more logs that I'll go through. 

I&#8217;m going to try to dump the ram with it loaded, and I want to see about the boot partition. Any thoughts/ideas please let me know.

Also, and idea on how to harden against it. I really am just trying to get to work :D

---

### Post by xalu on 2018-02-16
```

This is a mix of logs from a couple different time frames

b@lubuntu:~$ w 19:29:26 up 42 min,  2 users,  load average: 0.06, 0.07, 0.14
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
lubuntu  tty1     -                18:49   37:18   0.09s  0.02s -bash
bob      tty7     :0               18:52   41:11  52.65s  0.13s /usr/bin/lxses

F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
4 S     0     1     0  0  80   0 - 55004 -      ?        00:00:04 systemd
1 S     0     2     0  0  80   0 -     0 -      ?        00:00:00 kthreadd
1 S     0     4     2  0  60 -20 -     0 -      ?        00:00:00 kworker/0:0H
1 S     0     6     2  0  60 -20 -     0 -      ?        00:00:00 mm_percpu_wq
1 S     0     7     2  0  80   0 -     0 -      ?        00:00:00 ksoftirqd/0
1 S     0     8     2  0  80   0 -     0 -      ?        00:00:00 rcu_sched
1 S     0     9     2  0  80   0 -     0 -      ?        00:00:00 rcu_bh
1 S     0    10     2  0 -40   - -     0 -      ?        00:00:00 migration/0
5 S     0    11     2  0 -40   - -     0 -      ?        00:00:00 watchdog/0
1 S     0    12     2  0  80   0 -     0 -      ?        00:00:00 cpuhp/0
1 S     0    13     2  0  80   0 -     0 -      ?        00:00:00 cpuhp/1
5 S     0    14     2  0 -40   - -     0 -      ?        00:00:00 watchdog/1
1 S     0    15     2  0 -40   - -     0 -      ?        00:00:00 migration/1
1 S     0    16     2  0  80   0 -     0 -      ?        00:00:00 ksoftirqd/1
1 S     0    18     2  0  60 -20 -     0 -      ?        00:00:00 kworker/1:0H
1 S     0    19     2  0  80   0 -     0 -      ?        00:00:00 cpuhp/2
5 S     0    20     2  0 -40   - -     0 -      ?        00:00:00 watchdog/2
1 S     0    21     2  0 -40   - -     0 -      ?        00:00:00 migration/2
1 S     0    22     2  0  80   0 -     0 -      ?        00:00:00 ksoftirqd/2
1 S     0    24     2  0  60 -20 -     0 -      ?        00:00:00 kworker/2:0H
1 S     0    25     2  0  80   0 -     0 -      ?        00:00:00 cpuhp/3
5 S     0    26     2  0 -40   - -     0 -      ?        00:00:00 watchdog/3
1 S     0    27     2  0 -40   - -     0 -      ?        00:00:00 migration/3
1 S     0    28     2  0  80   0 -     0 -      ?        00:00:00 ksoftirqd/3
1 S     0    30     2  0  60 -20 -     0 -      ?        00:00:00 kworker/3:0H
5 S     0    31     2  0  80   0 -     0 -      ?        00:00:00 kdevtmpfs
1 S     0    32     2  0  60 -20 -     0 -      ?        00:00:00 netns
1 S     0    33     2  0  80   0 -     0 -      ?        00:00:00 kworker/0:1
1 S     0    34     2  0  80   0 -     0 -      ?        00:00:00 kworker/1:1
1 S     0    35     2  0  80   0 -     0 -      ?        00:00:00 khungtaskd
1 S     0    36     2  0  80   0 -     0 -      ?        00:00:00 oom_reaper
1 S     0    37     2  0  60 -20 -     0 -      ?        00:00:00 writeback
1 S     0    38     2  0  80   0 -     0 -      ?        00:00:00 kcompactd0
1 S     0    39     2  0  85   5 -     0 -      ?        00:00:00 ksmd
1 S     0    40     2  0  99  19 -     0 -      ?        00:00:00 khugepaged
1 S     0    41     2  0  60 -20 -     0 -      ?        00:00:00 crypto
1 S     0    42     2  0  60 -20 -     0 -      ?        00:00:00 kintegrityd
1 S     0    43     2  0  60 -20 -     0 -      ?        00:00:00 kblockd
1 S     0    44     2  0  80   0 -     0 -      ?        00:00:03 kworker/3:1
1 S     0    45     2  0  80   0 -     0 -      ?        00:00:00 kworker/2:1
1 S     0    46     2  0  60 -20 -     0 -      ?        00:00:00 ata_sff
1 S     0    47     2  0  60 -20 -     0 -      ?        00:00:00 md
1 S     0    48     2  0  60 -20 -     0 -      ?        00:00:00 edac-poller
1 S     0    49     2  0  60 -20 -     0 -      ?        00:00:00 devfreq_wq
1 S     0    50     2  0  60 -20 -     0 -      ?        00:00:00 watchdogd
1 S     0    53     2  0  80   0 -     0 -      ?        00:00:00 kauditd
1 S     0    54     2  0  80   0 -     0 -      ?        00:00:00 kswapd0
1 S     0    55     2  0  80   0 -     0 -      ?        00:00:00 ecryptfs-kthrea
1 S     0    97     2  0  60 -20 -     0 -      ?        00:00:00 kthrotld
1 S     0    98     2  0  60 -20 -     0 -      ?        00:00:00 acpi_thermal_pm
1 S     0   102     2  0  60 -20 -     0 -      ?        00:00:00 ipv6_addrconf
1 S     0   131     2  0  60 -20 -     0 -      ?        00:00:00 charger_manager
1 S     0   180     2  0  80   0 -     0 -      ?        00:00:00 scsi_eh_0
1 S     0   181     2  0  60 -20 -     0 -      ?        00:00:00 scsi_tmf_0
1 S     0   182     2  0  80   0 -     0 -      ?        00:00:00 scsi_eh_1
1 S     0   183     2  0  60 -20 -     0 -      ?        00:00:00 scsi_tmf_1
1 S     0   184     2  0  80   0 -     0 -      ?        00:00:00 scsi_eh_2
1 S     0   185     2  0  60 -20 -     0 -      ?        00:00:00 scsi_tmf_2
1 S     0   186     2  0  80   0 -     0 -      ?        00:00:00 scsi_eh_3
1 S     0   187     2  0  60 -20 -     0 -      ?        00:00:00 scsi_tmf_3
1 S     0   188     2  0  80   0 -     0 -      ?        00:00:00 scsi_eh_4
1 S     0   189     2  0  60 -20 -     0 -      ?        00:00:00 scsi_tmf_4
1 S     0   190     2  0  80   0 -     0 -      ?        00:00:00 scsi_eh_5
1 S     0   191     2  0  60 -20 -     0 -      ?        00:00:00 scsi_tmf_5
1 S     0   195     2  0  80   0 -     0 -      ?        00:00:00 kworker/u8:5
1 S     0   199     2  0  60 -20 -     0 -      ?        00:00:00 nvkm-disp
1 S     0   200     2  0  60 -20 -     0 -      ?        00:00:00 ttm_swap
1 S     0   203     2  0  80   0 -     0 -      ?        00:00:00 kworker/3:2
1 S     0   206     2  0  60 -20 -     0 -      ?        00:00:00 kworker/2:1H
1 S     0   207     2  0  60 -20 -     0 -      ?        00:00:00 kworker/3:1H
1 S     0   208     2  0  60 -20 -     0 -      ?        00:00:00 kworker/0:1H
1 S     0   209     2  0  60 -20 -     0 -      ?        00:00:00 kworker/1:1H
1 S     0   213     2  0  80   0 -     0 -      ?        00:00:00 kworker/0:2
1 S     0   315     2  0  60 -20 -     0 -      ?        00:00:00 loop0
4 S     0   885     1  0  80   0 - 16312 -      ?        00:00:00 systemd-journal
4 S     0   901     1  0  80   0 - 12039 -      ?        00:00:00 systemd-udevd
4 S     0   937     1  0  80   0 -  1125 -      ?        00:00:00 acpid
4 S     0   938     1  0  80   0 - 111424 -     ?        00:00:00 udisksd
4 S     0   941     1  0  80   0 - 118691 -     ?        00:00:00 NetworkManager
4 S     0   943     1  0  80   0 - 16419 -      ?        00:00:00 systemd-logind
4 S     0   944     1  0  80   0 - 106859 -     ?        00:00:00 ModemManager
4 S     0   945     1  0  80   0 -  9634 -      ?        00:00:00 irqbalance
4 S     0   947     1  0  80   0 -  8239 -      ?        00:00:00 cron
4 S     0   951     1  0  80   0 - 72289 -      ?        00:00:00 accounts-daemon
4 S     0   956     1  0  80   0 - 135901 -     ?        00:00:00 snapd
4 S     0  1002     1  0  80   0 - 72658 -      ?        00:00:00 polkitd
1 S     0  1051     2  0   9   - -     0 -      ?        00:00:00 irq/27-mei_me
1 S     0  1060     2  0  60 -20 -     0 -      ?        00:00:00 led_workqueue
4 S     0  1220     1  0  80   0 - 72578 -      ?        00:00:00 lightdm
4 S     0  1239     1  0  80   0 - 22173 -      tty1     00:00:00 login
4 S     0  1843     1  0  80   0 - 78387 -      ?        00:00:00 upowerd
4 S     0  1870  1828  0  80   0 - 20299 -      tty1     00:00:00 sudo
4 S     0  1871  1870  0  80   0 - 20206 -      tty1     00:00:00 su
4 S     0  1872  1871  0  80   0 -  5808 -      tty1     00:00:00 bash
4 S     0  1916  1872  0  80   0 - 20332 -      tty1     00:00:00 sudo
4 S     0  1917  1916  0  80   0 - 20206 -      tty1     00:00:00 su
4 S     0  1931  1918  0  80   0 - 20397 -      tty1     00:00:00 sudo
4 S     0  1932  1931  0  80   0 - 20206 -      tty1     00:00:00 su
4 S     0  1933  1932  0  80   0 -  5808 -      tty1     00:00:00 bash
4 R     0  1958  1220  2  80   0 - 205930 -     tty7     00:00:41 Xorg
4 S     0  2006  1220  0  80   0 - 66111 -      ?        00:00:00 lightdm
1 S     0  2115     2  0  80   0 -     0 -      ?        00:00:00 kworker/1:2
1 S     0  2721     2  0  80   0 -     0 -      ?        00:00:00 scsi_eh_6
1 S     0  2722     2  0  60 -20 -     0 -      ?        00:00:00 scsi_tmf_6
1 S     0  2723     2  0  80   0 -     0 -      ?        00:00:00 usb-storage
1 S     0  2855     2  0  80   0 -     0 -      ?        00:00:00 kworker/2:2
1 S     0  3136     2  0  80   0 -     0 -      ?        00:00:00 kworker/u8:0
1 S     0  3161     2  0  80   0 -     0 -      ?        00:00:00 kworker/u8:1

11:18:59 whoopsie: [11:18:59] online
11:18:59 nm-dispatcher: req:2 'connectivity-change': new request (1 scripts)
11:18:59 systemd: Started Network Manager Script Dispatcher Service.
11:18:59 dbus-daemon: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
11:18:59 systemd: Starting Network Manager Script Dispatcher Service...
11:18:59 whoopsie: [11:18:59] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/1
11:18:59 gsd-sharing: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit gnome-remote-desktop.service not loaded.
11:18:59 dbus-daemon: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
11:18:59 dhclient: bound to 10.234.81.11 -- renewal in 152 seconds.
11:18:59 NetworkManager: <info>  [1518779939.4810] manager: NetworkManager state is now CONNECTED_GLOBAL
11:18:59 whoopsie: [11:18:59] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
11:18:59 NetworkManager: <info>  [1518779939.4793] manager: NetworkManager state is now CONNECTED_LOCAL
11:18:59 avahi-daemon: Registering new address record for 10.234.81.11 on wlx00265a0e3fcb.IPv4.
11:18:59 NetworkManager: <info>  [1518779939.4767] dhcp4 (wlx00265a0e3fcb): state changed unknown -> bound
11:18:59 avahi-daemon: Joining mDNS multicast group on interface wlx00265a0e3fcb.IPv4 with address 10.234.81.11.
11:18:59 NetworkManager: <info>  [1518779939.4766] dhcp4 (wlx00265a0e3fcb):   nameserver '75.75.75.75'
11:18:59 dhclient: DHCPACK of 10.234.81.11 from 10.224.0.1
11:18:59 avahi-daemon: Registering new address record for fe80::f48e:efa3:688a:f261 on wlx00265a0e3fcb.*.
11:18:58 dhclient: DHCPDISCOVER on wlx00265a0e3fcb to 255.255.255.255 port 67 interval 3 (xid=0xedd6ce66)
11:18:57 NetworkManager: <info>  [1518779937.8884] dhcp4 (wlx00265a0e3fcb): dhclient started with pid 8280
11:18:55 wpa_supplicant: wlx00265a0e3fcb: CTRL-EVENT-REGDOM-CHANGE init=COUNTRY_IE type=COUNTRY alpha2=US
11:18:55 kernel: IPv6: ADDRCONF(NETDEV_CHANGE): wlx00265a0e3fcb: link becomes ready
11:18:55 kernel: wlx00265a0e3fcb: associated
11:18:55 NetworkManager: <info>  [1518779935.5169] device (wlx00265a0e3fcb): supplicant interface state: authenticating -> associating
11:18:55 wpa_supplicant: wlx00265a0e3fcb: Trying to associate with 84:00:2d:a8:4b:ba (SSID='xfinitywifi' freq=2462 MHz)
11:18:55 NetworkManager: <info>  [1518779935.5098] device (wlx00265a0e3fcb): supplicant interface state: scanning -> authenticating
11:18:55 kernel: wlx00265a0e3fcb: authenticate with 84:00:2d:a8:4b:ba
11:18:54 NetworkManager: <info>  [1518779934.3395] device (wlx00265a0e3fcb): supplicant interface state: inactive -> scanning
11:18:54 gnome-shell: JS WARNING: [resource:///org/gnome/shell/ui/modalDialog.js 218]: reference to undefined property "GdkX11Screen"
11:17:01 cron: pam_unix(cron:session): session closed for user root
11:17:01 sh: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
11:17:01 cron: pam_unix(cron:session): session opened for user root by (uid=0)
11:16:27 sudo: pam_unix(sudo:session): session closed for user root
11:16:23 systemd: Started Zeitgeist full-text search indexer.
11:16:23 dbus-daemon: Successfully activated service 'org.gnome.zeitgeist.SimpleIndexer'
11:16:23 zeitgeist-fts: Index must be upgraded. Doing full rebuild
11:16:23 zeitgeist-daemo: [31m[11:16:23.461980 WARNING][0m zeitgeist-daemon.vala:127: Unable to parse version info!
11:16:23 systemd: Starting Zeitgeist full-text search indexer...
11:16:23 dbus-daemon: Successfully activated service 'org.gnome.zeitgeist.Engine'
11:16:23 zeitgeist-daemo: zeitgeist-daemon.vala:477: Failed to open database "/home/ubuntu/.local/share/zeitgeist/activity.sqlite" (unable to open database file)
11:16:23 systemd: Starting Zeitgeist activity log service...
11:16:23 dbus-daemon: Activating via systemd: service name='org.gnome.zeitgeist.Engine' unit='zeitgeist.service'
11:16:18 systemd: Started Hostname Service.
11:16:18 dbus-daemon: [system] Successfully activated service 'org.freedesktop.hostname1'
11:16:18 systemd: Starting Hostname Service...
11:16:18 dbus-daemon: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
11:15:59 ModemManager: <info>  Couldn't check support for device at '/sys/devices/pci0000:00/0000:00:14.0/usb3/3-11/3-11.1': not supported by any plugin
11:15:57 kernel: IPv6: ADDRCONF(NETDEV_UP): wlx00265a0e3fcb: link is not ready
11:15:57 NetworkManager: <info>  [1518779757.3534] device (wlx00265a0e3fcb): state change: unavailable -> disconnected (reason 'supplicant-available', internal state 'managed')
11:15:57 wpa_supplicant: dbus: Failed to construct signal
11:15:57 kernel: IPv6: ADDRCONF(NETDEV_UP): wlx00265a0e3fcb: link is not ready


```

Quick add for bluetooth example:
```

02:30 lubuntu kernel: [11721.291187] [UFW BLOCK] IN= OUT=wlx00265a0e3fcb SRC=10.235.45.163 DST=10.224.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=1 ID=25430 DF PROTO=TCP SPT=51252 DPT=5355 WINDOW=29200 RES=0x00 SYN URGP=0 
Feb 16 22:02:44 lubuntu kernel: [11734.844767] [UFW BLOCK] IN= OUT=wlx00265a0e3fcb SRC=10.235.45.163 DST=224.0.0.251 LEN=146 TOS=0x00 PREC=0x00 TTL=255 ID=5546 DF PROTO=UDP SPT=5353 DPT=5353 LEN=126 
Feb 16 22:02:45 lubuntu kernel: [11736.239500] [UFW BLOCK] IN= OUT=wlx00265a0e3fcb SRC=fe80:0000:0000:0000:16b6:ce8c:28d5:9be8 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=166 TC=0 HOPLIMIT=255 FLOWLBL=461731 PROTO=UDP SPT=5353 DPT=5353 LEN=126 
Feb 16 22:02:52 lubuntu kernel: [11743.552673] usb 3-4.1: new full-speed USB device number 8 using xhci_hcd
Feb 16 22:02:53 lubuntu kernel: [11743.874507] usb 3-4.1: New USB device found, idVendor=0a12, idProduct=0001
Feb 16 22:02:53 lubuntu kernel: [11743.874509] usb 3-4.1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Feb 16 22:02:55 lubuntu kernel: [11746.210133] Bluetooth: Core ver 2.22
Feb 16 22:02:55 lubuntu kernel: [11746.210145] NET: Registered protocol family 31
Feb 16 22:02:55 lubuntu kernel: [11746.210146] Bluetooth: HCI device and connection manager initialized
Feb 16 22:02:55 lubuntu kernel: [11746.210148] Bluetooth: HCI socket layer initialized
Feb 16 22:02:55 lubuntu kernel: [11746.210149] Bluetooth: L2CAP socket layer initialized
Feb 16 22:02:55 lubuntu kernel: [11746.210152] Bluetooth: SCO socket layer initialized
Feb 16 22:02:55 lubuntu systemd[1]: Starting Load/Save RF Kill Switch Status...
Feb 16 22:02:55 lubuntu kernel: [11746.341446] usbcore: registered new interface driver btusb
Feb 16 22:02:55 lubuntu systemd[1]: Starting Bluetooth service...
Feb 16 22:02:55 lubuntu systemd[1]: Started Load/Save RF Kill Switch Status.
Feb 16 22:02:55 lubuntu bluetoothd[32575]: Bluetooth daemon 5.46
Feb 16 22:02:55 lubuntu systemd[1]: Started Bluetooth service.
Feb 16 22:02:55 lubuntu systemd[1]: Reached target Bluetooth.
Feb 16 22:02:55 lubuntu bluetoothd[32575]: Starting SDP server
Feb 16 22:02:55 lubuntu kernel: [11746.787638] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Feb 16 22:02:55 lubuntu kernel: [11746.787640] Bluetooth: BNEP filters: protocol multicast
Feb 16 22:02:55 lubuntu kernel: [11746.787646] Bluetooth: BNEP socket layer initialized
Feb 16 22:02:55 lubuntu dbus[940]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Feb 16 22:02:55 lubuntu bluetoothd[32575]: Bluetooth management interface 1.14 initialized
Feb 16 22:02:55 lubuntu NetworkManager[941]: <info>  [1518818575.9548] bluez: use BlueZ version 5
Feb 16 22:02:55 lubuntu systemd[1]: Starting Hostname Service...
Feb 16 22:02:56 lubuntu dbus[940]: [system] Successfully activated service 'org.freedesktop.hostname1'
Feb 16 22:02:56 lubuntu systemd[1]: Started Hostname Service.
Feb 16 22:03:06 lubuntu systemd[1]: Started Run anacron jobs.
Feb 16 22:03:21 lubuntu kernel: [11772.563376] [UFW BLOCK] IN= OUT=wlx00265a0e3fcb SRC=10.235.45.163 DST=208.101.3.245 LEN=60 TOS=0x00 PREC=0x00 TTL=1 ID=49348 DF PROTO=TCP SPT=38294 DPT=5355 WINDOW=29200 RES=0x00 SYN URGP=0 
Feb 16 22:03:46 lubuntu kernel: [11797.813551] [UFW BLOCK] IN= OUT=wlx00265a0e3fcb SRC=10.235.45.163 DST=91.189.89.239 LEN=60 TOS=0x00 PREC=0x00 TTL=1 ID=62990 DF PROTO=TCP SPT=39204 DPT=5355 WINDOW=29200 RES=0x00 SYN URGP=0 
Feb 16 22:03:48 lubuntu kernel: [11798.859217] [UFW BLOCK] IN= OUT=wlx00265a0e3fcb SRC=10.235.45.163 DST=224.0.0.251 LEN=146 TOS=0x00 PREC=0x00 TTL=255 ID=8279 DF PROTO=UDP SPT=5353 DPT=5353 LEN=126 
Feb 16 22:03:49 lubuntu kernel: [11800.241578] [UFW BLOCK] IN= OUT=wlx00265a0e3fcb SRC=fe80:0000:0000:0000:16b6:ce8c:28d5:9be8 DST=ff02:0000:0000:0000:0000:0000:0000:00fb LEN=166 TC=0 HOPLIMIT=255 FLOWLBL=461731 PROTO=UDP SPT=5353 DPT=5353 LEN=126 
Feb 16 22:04:08 lubuntu kernel: [11819.063846] [UFW BLOCK] IN= OUT=wlx00265a0e3fcb SRC=10.235.45.163 DST=54.149.36.237 LEN=60 TOS=0x00 PREC=0x00 TTL=1 ID=7243 DF PROTO=TCP SPT=48220 DPT=5355 WINDOW=29200 RES=0x00 SYN URGP=0 
Feb 16 22:04:11 lubuntu dhclient[32087]: DHCPREQUEST of 10.235.45.163 on wlx00265a0e3fcb to 10.224.0.1 port 67 (xid=0xbac4455)
Feb 16 22:04:11 lubuntu dhclient[32087]: DHCPACK of 10.235.45.163 from 10.224.0.1
Feb 16 22:04:11 lubuntu NetworkManager[941]: <info>  [1518818651.6363] dhcp4 (wlx00265a0e3fcb):   address 10.235.45.163
Feb 16 22:04:11 lubuntu NetworkManager[941]: <info>  [1518818651.6364] dhcp4 (wlx00265a0e3fcb):   plen 11 (255.224.0.0)
Feb 16 22:04:11 lubuntu NetworkManager[941]: <info>  [1518818651.6364] dhcp4 (wlx00265a0e3fcb):   gateway 10.224.0.1
Feb 16 22:04:11 lubuntu NetworkManager[941]: <info>  [1518818651.6364] dhcp4 (wlx00265a0e3fcb):   lease time 300
Feb 16 22:04:11 lubuntu NetworkManager[941]: <info>  [1518818651.6364] dhcp4 (wlx00265a0e3fcb):   nameserver '75.75.75.75'
Feb 16 22:04:11 lubuntu NetworkManager[941]: <info>  [1518818651.6365] dhcp4 (wlx00265a0e3fcb):   nameserver '75.75.76.76'

```

---

### Post by xalu on 2018-02-18
I was able to get clamav to scan by killing a a bunch of the services and deleting a few of the sbins the virus seems to use.  It detected the drives boot efi as corrupt..is that normal?

scan sumamry  clamscan (too long)
----------- SCAN SUMMARY -----------
Known viruses: 6415496
Engine version: 0.99.3
Scanned directories: 78268
Scanned files: 323516
Infected files: 19
Total errors: 23970
Not removed: 7
Data scanned: 13485.94 MB
Data read: 17081.45 MB (ratio 0.79:1)
Time: 1022.274 sec (17 m 2 s)


So I found ltrace and strace. Anyone offer some insight into what I am seeing. This is on a live cd I used to try to clean a drive. About to go for one more try installing a system hoping I cleaned the drive well en

There seems to be sockets that are waiting for certain calls at which point it does the below. I'm not 100% sure what it's doing up until it makes the tmp directory and writes the output. 
Here is dbus-daemon:
```
08:41:12 statfs("/sys/fs/selinux", 0x7ffdcacf7bb0) = -1 ENOENT (No such file or directory)
08:41:12 statfs("/selinux", 0x7ffdcacf7bb0) = -1 ENOENT (No such file or directory)
08:41:12 openat(AT_FDCWD, "/proc/filesystems", O_RDONLY|O_CLOEXEC) = 3
08:41:12 fstat(3, {st_mode=S_IFREG|000, st_size=0, ...}) = 0
08:41:12 read(3, "nodev\tsysfs\nnodev\trootfs\nnodev\tt"..., 1024) = 424
08:41:12 read(3, "", 1024)              = 0
08:41:12 close(3)                       = 0
08:41:12 access("/etc/selinux/config", F_OK) = -1 ENOENT (No such file or directory)
08:41:12 openat(AT_FDCWD, "/dev/null", O_RDWR) = 3
08:41:12 dup2(3, 0)                     = 0
08:41:12 close(3)                       = 0
08:41:12 write(2, "No configuration file specified."..., 33No configuration file specified.
) = 33
08:41:12 write(2, "dbus-daemon [--version] [--sessi"..., 218dbus-daemon [--version] [--session] [--system] [--config-file=FILE] [--print-address[=DESCRIPTOR]] [--print-pid[=DESCRIPTOR]] [--introspect] [--address=ADDRESS] [--nopidfile] [--nofork] [--fork] [--systemd-activation]
) = 218
08:41:12 exit_group(1)                  = ?
08:41:12 +++ exited with 1 +++AT_FDCWD, "/lib/x86_64-linux-gnu/libpcre.so.3", O_RDONLY|O_CLOEXEC) = 3
08:41:12 read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0 \25\0\0\0\0\0\0"..., 832) = 832
08:41:12 fstat(3, {st_mode=S_IFREG|0644, st_size=464824, ...}) = 0
08:41:12 mmap(NULL, 2560264, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f508c81d000
08:41:12 mprotect(0x7f508c88d000, 2097152, PROT_NONE) = 0
08:41:12 mmap(0x7f508ca8d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x70000) = 0x7f508ca8d000
08:41:12 close(3)                       = 0
08:41:12 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
08:41:12 openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libdl.so.2", O_RDONLY|O_CLOEXEC) = 3
08:41:12 read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220\16\0\0\0\0\0\0"..., 832) = 832
08:41:12 fstat(3, {st_mode=S_IFREG|0644, st_size=14632, ...}) = 0
08:41:12 mmap(NULL, 2109712, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f508c619000
08:41:12 mprotect(0x7f508c61c000, 2093056, PROT_NONE) = 0
08:41:12 mmap(0x7f508c81b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7f508c81b000
08:41:12 close(3)                       = 0
08:41:12 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
08:41:12 openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libgpg-error.so.0", O_RDONLY|O_CLOEXEC) = 3
08:41:12 read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P*\0\0\0\0\0\0"..., 832) = 832
08:41:12 fstat(3, {st_mode=S_IFREG|0644, st_size=84032, ...}) = 0
08:41:12 mmap(NULL, 2179304, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f508c404000
08:41:12 mprotect(0x7f508c418000, 2093056, PROT_NONE) = 0
08:41:12 mmap(0x7f508c617000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13000) = 0x7f508c617000
08:41:12 close(3)                       = 0
08:41:12 mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f508eb4e000
08:41:12 mmap(NULL, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f508eb4b000
08:41:12 arch_prctl(ARCH_SET_FS, 0x7f508eb4b8c0) = 0
08:41:12 mprotect(0x7f508d7b9000, 16384, PROT_READ) = 0
08:41:12 mprotect(0x7f508c617000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x7f508c81b000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x7f508d9dc000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x7f508ca8d000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x7f508cca5000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x7f508cecb000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x7f508d0d3000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x7f508d3da000, 8192, PROT_READ) = 0
08:41:12 mprotect(0x7f508dbf0000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x7f508ddf5000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x7f508e013000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x7f508e243000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x7f508e46f000, 8192, PROT_READ) = 0
08:41:12 mprotect(0x7f508e6f2000, 12288, PROT_READ) = 0
08:41:12 mprotect(0x7f508e941000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x55684d88a000, 8192, PROT_READ) = 0
08:41:12 mprotect(0x7f508eb6a000, 4096, PROT_READ) = 0
08:41:12 munmap(0x7f508eb54000, 76032)  = 0
08:41:12 set_tid_address(0x7f508eb4bb90) = 6236
08:41:12 set_robust_list(0x7f508eb4bba0, 24) = 0
08:41:12 rt_sigaction(SIGRTMIN, {sa_handler=0x7f508d7c8c70, sa_mask=[], sa_flags=SA_RESTORER|SA_SIGINFO, sa_restorer=0x7f508d7d6150}, NULL, 8) = 0
08:41:12 rt_sigaction(SIGRT_1, {sa_handler=0x7f508d7c8d00, sa_mask=[], sa_flags=SA_RESTORER|SA_RESTART|SA_SIGINFO, sa_restorer=0x7f508d7d6150}, NULL, 8) = 0
08:41:12 rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
08:41:12 prlimit64(0, RLIMIT_STACK, NULL, {rlim_cur=8192*1024, rlim_max=RLIM64_INFINITY}) = 0
08:41:12 brk(NULL)                      = 0x55684e178000
08:41:12 brk(0x55684e199000)            = 0x55684e199000
08:41:12 statfs("/sys/fs/selinux", 0x7ffdcacf7bb0) = -1 ENOENT (No such file or directory)
08:41:12 statfs("/selinux", 0x7ffdcacf7bb0) = -1 ENOENT (No such file or directory)
08:41:12 openat(AT_FDCWD, "/proc/filesystems", O_RDONLY|O_CLOEXEC) = 3
08:41:12 fstat(3, {st_mode=S_IFREG|000, st_size=0, ...}) = 0
08:41:12 read(3, "nodev\tsysfs\nnodev\trootfs\nnodev\tt"..., 1024) = 424
08:41:12 read(3, "", 1024)              = 0
08:41:12 close(3)                       = 0
08:41:12 access("/etc/selinux/config", F_OK) = -1 ENOENT (No such file or directory)
08:41:12 openat(AT_FDCWD, "/dev/null", O_RDWR) = 3
08:41:12 dup2(3, 0)                     = 0
08:41:12 close(3)                       = 0
08:41:12 write(2, "No configuration file specified."..., 33No configuration file specified.
) = 33
08:41:12 write(2, "dbus-daemon [--version] [--sessi"..., 218dbus-daemon [--version] [--session] [--system] [--config-file=FILE] [--print-address[=DESCRIPTOR]] [--print-pid[=DESCRIPTOR]] [--introspect] [--address=ADDRESS] [--nopidfile] [--nofork] [--fork] [--systemd-activation]
) = 218
08:41:12 exit_group(1)                  = ?
08:41:12 +++ exited with 1 +++00, 2093056, PROT_NONE) = 0
08:41:12 mmap(0x7f508dbf0000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xe000) = 0x7f508dbf0000
08:41:12 close(3)                       = 0
08:41:12 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
08:41:12 openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libpthread.so.0", O_RDONLY|O_CLOEXEC) = 3
08:41:12 read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\360a\0\0\0\0\0\0"..., 832) = 832
08:41:12 fstat(3, {st_mode=S_IFREG|0755, st_size=144776, ...}) = 0
08:41:12 mmap(NULL, 2221160, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f508d7c3000
08:41:12 mprotect(0x7f508d7dd000, 2093056, PROT_NONE) = 0
08:41:12 mmap(0x7f508d9dc000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x19000) = 0x7f508d9dc000
08:41:12 mmap(0x7f508d9de000, 13416, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f508d9de000
08:41:12 close(3)                       = 0
08:41:12 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
08:41:12 openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
08:41:12 read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340\22\2\0\0\0\0\0"..., 832) = 832
08:41:12 fstat(3, {st_mode=S_IFREG|0755, st_size=1960656, ...}) = 0
08:41:12 mmap(NULL, 4061792, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f508d3e3000
08:41:12 mprotect(0x7f508d5b9000, 2097152, PROT_NONE) = 0
08:41:12 mmap(0x7f508d7b9000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1d6000) = 0x7f508d7b9000
08:41:12 mmap(0x7f508d7bf000, 14944, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f508d7bf000
08:41:12 close(3)                       = 0
08:41:12 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
08:41:12 openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libgcrypt.so.20", O_RDONLY|O_CLOEXEC) = 3
08:41:12 read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\256\0\0\0\0\0\0"..., 832) = 832
08:41:12 fstat(3, {st_mode=S_IFREG|0644, st_size=1103800, ...}) = 0
08:41:12 mmap(NULL, 3200064, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f508d0d5000
08:41:12 mprotect(0x7f508d1db000, 2093056, PROT_NONE) = 0
08:41:12 mmap(0x7f508d3da000, 32768, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x105000) = 0x7f508d3da000
08:41:12 mmap(0x7f508d3e2000, 1088, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f508d3e2000
08:41:12 close(3)                       = 0
08:41:12 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
08:41:12 openat(AT_FDCWD, "/lib/x86_64-linux-gnu/librt.so.1", O_RDONLY|O_CLOEXEC) = 3
08:41:12 read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\"\0\0\0\0\0\0"..., 832) = 832
08:41:12 fstat(3, {st_mode=S_IFREG|0644, st_size=31744, ...}) = 0
08:41:12 mmap(NULL, 2128864, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f508cecd000
08:41:12 mprotect(0x7f508ced4000, 2093056, PROT_NONE) = 0
08:41:12 mmap(0x7f508d0d3000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6000) = 0x7f508d0d3000
08:41:12 close(3)                       = 0
08:41:12 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
08:41:12 openat(AT_FDCWD, "/lib/x86_64-linux-gnu/liblzma.so.5", O_RDONLY|O_CLOEXEC) = 3
08:41:12 read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340(\0\0\0\0\0\0"..., 832) = 832
08:41:12 fstat(3, {st_mode=S_IFREG|0644, st_size=153984, ...}) = 0
08:41:12 mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f508eb50000
08:41:12 mmap(NULL, 2248968, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f508cca7000
08:41:12 mprotect(0x7f508cccb000, 2097152, PROT_NONE) = 0
08:41:12 mmap(0x7f508cecb000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x24000) = 0x7f508cecb000
08:41:12 close(3)                       = 0
08:41:12 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
08:41:12 openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/liblz4.so.1", O_RDONLY|O_CLOEXEC) = 3
08:41:12 read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20\36\0\0\0\0\0\0"..., 832) = 832
08:41:12 fstat(3, {st_mode=S_IFREG|0644, st_size=96360, ...}) = 0
08:41:12 mmap(NULL, 2191456, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f508ca8f000
08:41:12 mprotect(0x7f508caa6000, 2093056, PROT_NONE) = 0
08:41:12 mmap(0x7f508cca5000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x16000) = 0x7f508cca5000
08:41:12 close(3)                       = 0
08:41:12 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
08:41:12 openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libpcre.so.3", O_RDONLY|O_CLOEXEC) = 3
08:41:12 read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0 \25\0\0\0\0\0\0"..., 832) = 832
08:41:12 fstat(3, {st_mode=S_IFREG|0644, st_size=464824, ...}) = 0
08:41:12 mmap(NULL, 2560264, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f508c81d000
08:41:12 mprotect(0x7f508c88d000, 2097152, PROT_NONE) = 0
08:41:12 mmap(0x7f508ca8d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x70000) = 0x7f508ca8d000
08:41:12 close(3)                       = 0
08:41:12 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
08:41:12 openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libdl.so.2", O_RDONLY|O_CLOEXEC) = 3
08:41:12 read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220\16\0\0\0\0\0\0"..., 832) = 832
08:41:12 fstat(3, {st_mode=S_IFREG|0644, st_size=14632, ...}) = 0
08:41:12 mmap(NULL, 2109712, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f508c619000
08:41:12 mprotect(0x7f508c61c000, 2093056, PROT_NONE) = 0
08:41:12 mmap(0x7f508c81b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7f508c81b000
08:41:12 close(3)                       = 0
08:41:12 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
08:41:12 openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libgpg-error.so.0", O_RDONLY|O_CLOEXEC) = 3
08:41:12 read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P*\0\0\0\0\0\0"..., 832) = 832
08:41:12 fstat(3, {st_mode=S_IFREG|0644, st_size=84032, ...}) = 0
08:41:12 mmap(NULL, 2179304, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f508c404000
08:41:12 mprotect(0x7f508c418000, 2093056, PROT_NONE) = 0
08:41:12 mmap(0x7f508c617000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13000) = 0x7f508c617000
08:41:12 close(3)                       = 0
08:41:12 mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f508eb4e000
08:41:12 mmap(NULL, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f508eb4b000
08:41:12 arch_prctl(ARCH_SET_FS, 0x7f508eb4b8c0) = 0
08:41:12 mprotect(0x7f508d7b9000, 16384, PROT_READ) = 0
08:41:12 mprotect(0x7f508c617000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x7f508c81b000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x7f508d9dc000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x7f508ca8d000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x7f508cca5000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x7f508cecb000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x7f508d0d3000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x7f508d3da000, 8192, PROT_READ) = 0
08:41:12 mprotect(0x7f508dbf0000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x7f508ddf5000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x7f508e013000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x7f508e243000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x7f508e46f000, 8192, PROT_READ) = 0
08:41:12 mprotect(0x7f508e6f2000, 12288, PROT_READ) = 0
08:41:12 mprotect(0x7f508e941000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x55684d88a000, 8192, PROT_READ) = 0
08:41:12 mprotect(0x7f508eb6a000, 4096, PROT_READ) = 0
08:41:12 munmap(0x7f508eb54000, 76032)  = 0
08:41:12 set_tid_address(0x7f508eb4bb90) = 6236
08:41:12 set_robust_list(0x7f508eb4bba0, 24) = 0
08:41:12 rt_sigaction(SIGRTMIN, {sa_handler=0x7f508d7c8c70, sa_mask=[], sa_flags=SA_RESTORER|SA_SIGINFO, sa_restorer=0x7f508d7d6150}, NULL, 8) = 0
08:41:12 rt_sigaction(SIGRT_1, {sa_handler=0x7f508d7c8d00, sa_mask=[], sa_flags=SA_RESTORER|SA_RESTART|SA_SIGINFO, sa_restorer=0x7f508d7d6150}, NULL, 8) = 0
08:41:12 rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
08:41:12 prlimit64(0, RLIMIT_STACK, NULL, {rlim_cur=8192*1024, rlim_max=RLIM64_INFINITY}) = 0
08:41:12 brk(NULL)                      = 0x55684e178000
08:41:12 brk(0x55684e199000)            = 0x55684e199000
08:41:12 statfs("/sys/fs/selinux", 0x7ffdcacf7bb0) = -1 ENOENT (No such file or directory)
08:41:12 statfs("/selinux", 0x7ffdcacf7bb0) = -1 ENOENT (No such file or directory)
08:41:12 openat(AT_FDCWD, "/proc/filesystems", O_RDONLY|O_CLOEXEC) = 3
08:41:12 fstat(3, {st_mode=S_IFREG|000, st_size=0, ...}) = 0
08:41:12 read(3, "nodev\tsysfs\nnodev\trootfs\nnodev\tt"..., 1024) = 424
08:41:12 read(3, "", 1024)              = 0
08:41:12 close(3)                       = 0
08:41:12 access("/etc/selinux/config", F_OK) = -1 ENOENT (No such file or directory)
08:41:12 openat(AT_FDCWD, "/dev/null", O_RDWR) = 3
08:41:12 dup2(3, 0)                     = 0
08:41:12 close(3)                       = 0
08:41:12 write(2, "No configuration file specified."..., 33No configuration file specified.
) = 33
08:41:12 write(2, "dbus-daemon [--version] [--sessi"..., 218dbus-daemon [--version] [--session] [--system] [--config-file=FILE] [--print-address[=DESCRIPTOR]] [--print-pid[=DESCRIPTOR]] [--introspect] [--address=ADDRESS] [--nopidfile] [--nofork] [--fork] [--systemd-activation]
) = 218
08:41:12 exit_group(1)                  = ?
08:41:12 +++ exited with 1 +++
```

and now sshagent you can see they are doing similiar things here. I have a few others and they also are doing it. Clamscan doesn't see them unless I can remove a ton of the files its using

```

08:41:12 execve("/usr/bin/ssh-agent", ["ssh-agent"], [/* 23 vars */]) = 0
08:41:12 access("/etc/suid-debug", F_OK) = -1 ENOENT (No such file or directory)
08:41:12 brk(NULL)                      = 0x55f26d2fa000
08:41:12 fcntl(0, F_GETFD)              = 0
08:41:12 fcntl(1, F_GETFD)              = 0
08:41:12 fcntl(2, F_GETFD)              = 0
08:41:12 access("/etc/suid-debug", F_OK) = -1 ENOENT (No such file or directory)
08:41:12 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
08:41:12 mmap(NULL, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f8ece10b000
08:41:12 access("/etc/ld.so.preload", R_OK) = -1 ENOENT (No such file or directory)
08:41:12 openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
08:41:12 fstat(3, {st_mode=S_IFREG|0644, st_size=76032, ...}) = 0
08:41:12 mmap(NULL, 76032, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f8ece0f8000
08:41:12 close(3)                       = 0
08:41:12 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
08:41:12 openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libcrypto.so.1.0.0", O_RDONLY|O_CLOEXEC) = 3
08:41:12 read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\35\6\0\0\0\0\0"..., 832) = 832
08:41:12 fstat(3, {st_mode=S_IFREG|0644, st_size=2349504, ...}) = 0
08:41:12 mmap(NULL, 4459392, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f8ecdaa6000
08:41:12 mprotect(0x7f8ecdcbc000, 2097152, PROT_NONE) = 0
08:41:12 mmap(0x7f8ecdebc000, 163840, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x216000) = 0x7f8ecdebc000
08:41:12 mmap(0x7f8ecdee4000, 11136, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f8ecdee4000
08:41:12 close(3)                       = 0
08:41:12 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
08:41:12 openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
08:41:12 read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340\22\2\0\0\0\0\0"..., 832) = 832
08:41:12 fstat(3, {st_mode=S_IFREG|0755, st_size=1960656, ...}) = 0
08:41:12 mmap(NULL, 4061792, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f8ecd6c6000
08:41:12 mprotect(0x7f8ecd89c000, 2097152, PROT_NONE) = 0
08:41:12 mmap(0x7f8ecda9c000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1d6000) = 0x7f8ecda9c000
08:41:12 mmap(0x7f8ecdaa2000, 14944, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f8ecdaa2000
08:41:12 close(3)                       = 0
08:41:12 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
08:41:12 openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libdl.so.2", O_RDONLY|O_CLOEXEC) = 3
08:41:12 read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220\16\0\0\0\0\0\0"..., 832) = 832
08:41:12 fstat(3, {st_mode=S_IFREG|0644, st_size=14632, ...}) = 0
08:41:12 mmap(NULL, 2109712, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f8ecd4c2000
08:41:12 mprotect(0x7f8ecd4c5000, 2093056, PROT_NONE) = 0
08:41:12 mmap(0x7f8ecd6c4000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7f8ecd6c4000
08:41:12 close(3)                       = 0
08:41:12 mmap(NULL, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f8ece0f5000
08:41:12 arch_prctl(ARCH_SET_FS, 0x7f8ece0f5740) = 0
08:41:12 mprotect(0x7f8ecda9c000, 16384, PROT_READ) = 0
08:41:12 mprotect(0x7f8ecd6c4000, 4096, PROT_READ) = 0
08:41:12 mprotect(0x7f8ecdebc000, 114688, PROT_READ) = 0
08:41:12 mprotect(0x55f26b590000, 8192, PROT_READ) = 0
08:41:12 mprotect(0x7f8ece10e000, 4096, PROT_READ) = 0
08:41:12 munmap(0x7f8ece0f8000, 76032)  = 0
08:41:12 openat(AT_FDCWD, "/dev/null", O_RDWR) = 3
08:41:12 close(3)                       = 0
08:41:12 getgid()                       = 0
08:41:12 setresgid(-1, 0, -1)           = 0
08:41:12 getgid()                       = 0
08:41:12 setgid(0)                      = 0
08:41:12 prctl(PR_SET_DUMPABLE, 0)      = 0
08:41:12 brk(NULL)                      = 0x55f26d2fa000
08:41:12 brk(0x55f26d31b000)            = 0x55f26d31b000
08:41:12 openat(AT_FDCWD, "/usr/lib/ssl/openssl.cnf", O_RDONLY) = 3
08:41:12 fstat(3, {st_mode=S_IFREG|0644, st_size=10835, ...}) = 0
08:41:12 read(3, "#\n# OpenSSL example configuratio"..., 1024) = 1024
08:41:12 read(3, "efault ca section\n\n#############"..., 1024) = 1024
08:41:12 read(3, "tions\ncert_opt \t= ca_default\t\t# "..., 1024) = 1024
08:41:12 read(3, " 'object'\n# types.\n[ policy_anyt"..., 1024) = 1024
08:41:12 read(3, "Netscape crash on BMPStrings or "..., 1024) = 1024
08:41:12 read(3, "challenge password\nchallengePass"..., 1024) = 1024
08:41:12 read(3, "X recommendations harmless if in"..., 1024) = 1024
08:41:12 read(3, "ue\n# So we do this instead.\nbasi"..., 1024) = 1024
08:41:12 read(3, " this to avoid interpreting an e"..., 1024) = 1024
08:41:12 read(3, "hat aren't\n# deprecated accordin"..., 1024) = 1024
08:41:12 read(3, " Policy if request did not speci"..., 1024) = 595
08:41:12 read(3, "", 1024)              = 0
08:41:12 close(3)                       = 0
08:41:12 getpid()                       = 6229
08:41:12 openat(AT_FDCWD, "/dev/urandom", O_RDONLY|O_NOCTTY|O_NONBLOCK) = 3
08:41:12 fstat(3, {st_mode=S_IFCHR|0666, st_rdev=makedev(1, 9), ...}) = 0
08:41:12 poll([{fd=3, events=POLLIN}], 1, 10) = 1 ([{fd=3, revents=POLLIN}])
08:41:12 read(3, "\240\365x\3\330\7Z\246\275~/\234\204\227\n\37\\\217\0061}\346\1'\234\357\220g\254\242\36M", 32) = 32
08:41:12 close(3)                       = 0
08:41:12 getuid()                       = 0
08:41:12 getpid()                       = 6229
08:41:12 getpid()                       = 6229
08:41:12 getpid()                       = 6229
08:41:12 getpid()                       = 6229
08:41:12 getpid()                       = 6229
08:41:12 getpid()                       = 6229
08:41:12 getpid()                       = 6229
08:41:12 getpid()                       = 6229
08:41:12 getpid()                       = 6229
08:41:12 getpid()                       = 6229
08:41:12 mkdir("/tmp/ssh-Lnrjp0kaWJab", 0700) = 0
08:41:12 umask(0177)                    = 022
08:41:12 socket(AF_UNIX, SOCK_STREAM, 0) = 3
08:41:12 bind(3, {sa_family=AF_UNIX, sun_path="/tmp/ssh-Lnrjp0kaWJab/agent.6229"}, 110) = 0
08:41:12 listen(3, 128)                 = 0
08:41:12 umask(022)                     = 0177
08:41:12 clone(child_stack=NULL, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7f8ece0f5a10) = 6230
08:41:12 close(3)                       = 0
08:41:12 fstat(1, {st_mode=S_IFREG|0664, st_size=75727, ...}) = 0
08:41:12 write(1, "SSH_AUTH_SOCK=/tmp/ssh-Lnrjp0kaW"..., 133SSH_AUTH_SOCK=/tmp/ssh-Lnrjp0kaWJab/agent.6229; export SSH_AUTH_SOCK;
SSH_AGENT_PID=6230; export SSH_AGENT_PID;
echo Agent pid 6230;
) = 133
08:41:12 exit_group(0)                  = ?
08:41:12 +++ exited with 0 +++29
08:41:12 getpid()                       = 6229
08:41:12 getpid()                       = 6229
08:41:12 getpid()                       = 6229
08:41:12 getpid()                       = 6229
08:41:12 getpid()                       = 6229
08:41:12 getpid()                       = 6229
08:41:12 mkdir("/tmp/ssh-Lnrjp0kaWJab", 0700) = 0
08:41:12 umask(0177)                    = 022
08:41:12 socket(AF_UNIX, SOCK_STREAM, 0) = 3
08:41:12 bind(3, {sa_family=AF_UNIX, sun_path="/tmp/ssh-Lnrjp0kaWJab/agent.6229"}, 110) = 0
08:41:12 listen(3, 128)                 = 0
08:41:12 umask(022)                     = 0177
08:41:12 clone(child_stack=NULL, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7f8ece0f5a10) = 6230
08:41:12 close(3)                       = 0
08:41:12 fstat(1, {st_mode=S_IFREG|0664, st_size=75727, ...}) = 0
08:41:12 write(1, "SSH_AUTH_SOCK=/tmp/ssh-Lnrjp0kaW"..., 133SSH_AUTH_SOCK=/tmp/ssh-Lnrjp0kaWJab/agent.6229; export SSH_AUTH_SOCK;
SSH_AGENT_PID=6230; export SSH_AGENT_PID;
echo Agent pid 6230;
) = 133
08:41:12 exit_group(0)                  = ?
08:41:12 +++ exited with 0 +++

```

an example of the node creation it causes:
```

EtherApe-INFO: New node: IP: 69.4.230.200. Number of nodes 114
EtherApe-INFO: New node: IP: 173.244.223.107. Number of nodes 115
EtherApe-INFO: New node: IP: 172.98.66.179. Number of nodes 116
EtherApe-INFO: New node: IP: 216.8.137.219. Number of nodes 117
EtherApe-INFO: New node: IP: 104.200.153.211. Number of nodes 118
EtherApe-INFO: New node: IP: 66.71.248.163. Number of nodes 119
EtherApe-INFO: New node: IP: 69.71.0.90. Number of nodes 120
EtherApe-INFO: New node: IP: 192.171.19.90. Number of nodes 121
EtherApe-INFO: New node: IP: 192.195.203.243. Number of nodes 122
EtherApe-INFO: New node: IP: 174.127.82.212. Number of nodes 123
EtherApe-INFO: New node: IP: 52.20.242.25. Number of nodes 124
EtherApe-INFO: New node: IP: 52.55.162.249. Number of nodes 125
EtherApe-INFO: New node: IP: 159.127.42.172. Number of nodes 126
EtherApe-INFO: New node: IP: 208.86.5.143. Number of nodes 127
EtherApe-INFO: New node: IP: 198.57.30.31. Number of nodes 128
EtherApe-INFO: New node: IP: 209.15.36.31. Number of nodes 129
EtherApe-INFO: New node: IP: 52.20.187.235. Number of nodes 130
EtherApe-INFO: New node: IP: 52.4.246.104. Number of nodes 131
EtherApe-INFO: New node: IP: 151.101.202.109. Number of nodes 132
EtherApe-INFO: New node: IP: 104.193.83.57. Number of nodes 133
EtherApe-INFO: New node: IP: 54.243.147.129. Number of nodes 134
EtherApe-INFO: New node: IP: 70.33.182.205. Number of nodes 135
EtherApe-INFO: New node: IP: 199.16.156.105. Number of nodes 136
EtherApe-INFO: New node: IP: 8.43.72.32. Number of nodes 137
EtherApe-INFO: New node: IP: 31.13.71.2. Number of nodes 138
EtherApe-INFO: New node: IP: 209.85.144.155. Number of nodes 139
EtherApe-INFO: New node: IP: 172.217.6.206. Number of nodes 140
EtherApe-INFO: New node: IP: 69.166.1.10. Number of nodes 141
EtherApe-INFO: New node: IP: 54.192.37.184. Number of nodes 142
EtherApe-INFO: New node: IP: 178.255.83.1. Number of nodes 143
EtherApe-INFO: New node: IP: 172.217.12.161. Number of nodes 144
EtherApe-INFO: New node: IP: 172.217.10.2. Number of nodes 145
EtherApe-INFO: New node: IP: 23.205.208.14. Number of nodes 146
EtherApe-INFO: New node: IP: 69.172.216.56. Number of nodes 147
EtherApe-INFO: New node: IP: 172.217.12.194. Number of nodes 148
EtherApe-INFO: New node: IP: 63.251.210.243. Number of nodes 149
EtherApe-INFO: New node: IP: 209.15.36.34. Number of nodes 150
EtherApe-INFO: New node: IP: 50.116.194.21. Number of nodes 151
EtherApe-INFO: New node: IP: 52.22.70.240. Number of nodes 152
EtherApe-INFO: New node: IP: 52.35.50.44. Number of nodes 153
EtherApe-INFO: New node: IP: 104.70.178.73. Number of nodes 154
EtherApe-INFO: New node: IP: 68.67.178.196. Number of nodes 155
EtherApe-INFO: New node: IP: 35.190.74.53. Number of nodes 156
EtherApe-INFO: New node: IP: 50.16.181.90. Number of nodes 157
EtherApe-INFO: New node: IP: 63.251.28.160. Number of nodes 158
EtherApe-INFO: New node: IP: 204.2.197.201. Number of nodes 159
EtherApe-INFO: New node: IP: 69.172.216.55. Number of nodes 160
EtherApe-INFO: New node: IP: 54.236.105.123. Number of nodes 161
EtherApe-INFO: New node: IP: 34.205.226.238. Number of nodes 162
EtherApe-INFO: New node: IP: 34.226.78.29. Number of nodes 163
EtherApe-INFO: New node: IP: 69.172.216.58. Number of nodes 164
EtherApe-INFO: New node: IP: 70.33.182.202. Number of nodes 165
EtherApe-INFO: New node: IP: 68.67.178.110. Number of nodes 166
EtherApe-INFO: New node: IP: 50.19.109.243. Number of nodes 167
EtherApe-INFO: New node: IP: 54.192.37.208. Number of nodes 168
EtherApe-INFO: New node: IP: 23.205.210.106. Number of nodes 169
EtherApe-INFO: New node: IP: 52.201.121.132. Number of nodes 170
EtherApe-INFO: New node: IP: 198.23.90.60. Number of nodes 171
EtherApe-INFO: New node: IP: 152.195.32.110. Number of nodes 172
EtherApe-INFO: New node: IP: 34.248.231.125. Number of nodes 173
EtherApe-INFO: delete node: IPv6: ff02::1:3. Number of nodes 172
EtherApe-INFO: delete node: IPv6: fe80::1708:567b:3fd5:a48f. Number of nodes 171
EtherApe-INFO: delete node: IP: 224.0.0.252. Number of nodes 170
EtherApe-INFO: delete node: IP: 23.216.132.226. Number of nodes 169
EtherApe-INFO: delete node: IP: 213.211.198.62. Number of nodes 168
EtherApe-INFO: delete node: IP: 193.99.144.77. Number of nodes 167
EtherApe-INFO: delete node: IP: 81.169.145.68. Number of nodes 166
EtherApe-INFO: delete node: IP: 35.162.60.68. Number of nodes 165
EtherApe-INFO: New node: IP: 23.216.132.226. Number of nodes 166

```

original chkrootkit
```
ROOTDIR is `/'
Checking `amd'...                                           not found
Checking `basename'...                                      not infected
Checking `biff'...                                          not found
Checking `chfn'...                                          not infected
Checking `chsh'...                                          not infected
Checking `cron'...                                          not infected
Checking `crontab'...                                       not infected
Checking `date'...                                          not infected
Checking `du'...                                            not infected
Checking `dirname'...                                       not infected
Checking `echo'...                                          not infected
Checking `egrep'...                                         not infected
Checking `env'...                                           not infected
Checking `find'...                                          not infected
Checking `fingerd'...                                       not found
Checking `gpm'...                                           not found
Checking `grep'...                                          not infected
Checking `hdparm'...                                        not infected
Checking `su'...                                            not infected
Checking `ifconfig'...                                      not infected
Checking `inetd'...                                         not infected
Checking `inetdconf'...                                     not found
Checking `identd'...                                        not found
Checking `init'...                                          not infected
Checking `killall'...                                       not infected
Checking `ldsopreload'...                                   not infected
Checking `login'...                                         not infected
Checking `ls'...                                            not infected
Checking `lsof'...                                          not infected
Checking `mail'...                                          not found
Checking `mingetty'...                                      not found
Checking `netstat'...                                       not infected
Checking `named'...                                         not found
Checking `passwd'...                                        not infected
Checking `pidof'...                                         not infected
Checking `pop2'...                                          not found
Checking `pop3'...                                          not found
Checking `ps'...                                            not infected
Checking `pstree'...                                        not infected
Checking `rpcinfo'...                                       not found
Checking `rlogind'...                                       not found
Checking `rshd'...                                          not found
Checking `slogin'...                                        not infected
Checking `sendmail'...                                      not found
Checking `sshd'...                                          not found
Checking `syslogd'...                                       not tested
Checking `tar'...                                           not infected
Checking `tcpd'...                                          INFECTED
Checking `tcpdump'...                                       not infected
Checking `top'...                                           not infected
Checking `telnetd'...                                       not found
Checking `timed'...                                         not found
Checking `traceroute'...                                    not found
Checking `vdir'...                                          not infected
Checking `w'...                                             not infected
Checking `write'...                                         not infected
Checking `aliens'...                                        no suspect files
Searching for sniffer's logs, it may take a while...        nothing found
Searching for rootkit HiDrootkit's default files...         nothing found
Searching for rootkit t0rn's default files...               nothing found
Searching for t0rn's v8 defaults...                         nothing found
Searching for rootkit Lion's default files...               nothing found
Searching for rootkit RSHA's default files...               nothing found
Searching for rootkit RH-Sharpe's default files...          nothing found
Searching for Ambient's rootkit (ark) default files and dirs... nothing found
Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/lib/modules/4.13.0-21-generic/vdso/.build-id
/lib/modules/4.13.0-21-generic/vdso/.build-id
Searching for LPD Worm files and dirs...                    nothing found
Searching for Ramen Worm files and dirs...                  nothing found
Searching for Maniac files and dirs...                      nothing found
Searching for RK17 files and dirs...                        nothing found
Searching for Ducoci rootkit...                             nothing found
Searching for Adore Worm...                                 nothing found
Searching for ShitC Worm...                                 nothing found
Searching for Omega Worm...                                 nothing found
Searching for Sadmind/IIS Worm...                           nothing found
Searching for MonKit...                                     nothing found
Searching for Showtee...                                    nothing found
Searching for OpticKit...                                   nothing found
Searching for T.R.K...                                      nothing found
Searching for Mithra...                                     nothing found
Searching for LOC rootkit...                                nothing found
Searching for Romanian rootkit...                           nothing found
Searching for Suckit rootkit...                             nothing found
Searching for Volc rootkit...                               nothing found
Searching for Gold2 rootkit...                              nothing found
Searching for TC2 Worm default files and dirs...            nothing found
Searching for Anonoying rootkit default files and dirs...   nothing found
Searching for ZK rootkit default files and dirs...          nothing found
Searching for ShKit rootkit default files and dirs...       nothing found
Searching for AjaKit rootkit default files and dirs...      nothing found
Searching for zaRwT rootkit default files and dirs...       nothing found
Searching for Madalin rootkit default files...              nothing found
Searching for Fu rootkit default files...                   nothing found
Searching for ESRK rootkit default files...                 nothing found
Searching for rootedoor...                                  nothing found
Searching for ENYELKM rootkit default files...              nothing found
Searching for common ssh-scanners default files...          nothing found
Searching for Linux/Ebury - Operation Windigo ssh...        not tested
Searching for 64-bit Linux Rootkit ...                      nothing found
Searching for 64-bit Linux Rootkit modules...               nothing found
Searching for Mumblehard Linux ...                          nothing found
Searching for Backdoor.Linux.Mokes.a ...                    nothing found
Searching for Malicious TinyDNS ...                         nothing found
Searching for Linux.Xor.DDoS ...                            nothing found
Searching for Linux.Proxy.1.0 ...                           nothing found
Searching for suspect PHP files...                          nothing found
Searching for anomalies in shell history files...           nothing found
Checking `asp'...                                           not infected
Checking `bindshell'...                                     not infected
Checking `lkm'...                                           chkproc: nothing detected
-220	/usr/share
-1	/usr/bin
-1	/usr/sbin
-20	/lib
chkdirs: Warning: Possible LKM Trojan installed
Checking `rexedcs'...                                       not found
Checking `sniffer'...                                       lo: not promisc and no packet sniffer sockets
wlx00265a0e3fcb: PACKET SNIFFER(/sbin/wpa_supplicant[3498], /sbin/wpa_supplicant[3498], /sbin/dhclient[3518])
Checking `w55808'...                                        not infected
Checking `wted'...                                          chkwtmp: nothing deleted
Checking `scalper'...                                       not infected
Checking `slapper'...                                       not infected
Checking `z2'...                                            user lubuntu deleted or never logged from lastlog!
user bob deleted or never logged from lastlog!
Checking `chkutmp'...                                        The tty of the following user process(es) were not found
 in /var/run/utmp !
! RUID          PID TTY    CMD
! ˜â…™â…š?â…œâ…â…žâ…Ÿâˆ•âˆ¶âŽ®â•±â§¶â§¸â«»â«½â¿°â¿±â¿²â¿³â¿´â¿µâ¿¶â¿·â¿¸â¿¹â¿ºâ¿»ã€€ã€‚ã€”ã€•ã€³ã‚*ã…¤ãˆãˆžãŽ®ãŽ¯ã†ãŸêž‰ï¸”ï¸•ï¸¿ï¹ï¹ž?ï¼Žï¼ï½¡ï¾*???ï¿¼ï¿½|159:4;high| -schedulerPrefs 0001,2 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/fire       0 â€§???????â€¯â€¹â€ºââ„â’âŸâ…“˜â…™â…š?â…œâ…â…žâ…Ÿâˆ•âˆ¶âŽ®â•±â§¶â§¸â«»â«½â¿°â¿±â¿²â¿³â¿´â¿µâ¿¶â¿·â¿¸â¿¹â¿ºâ¿»ã€€ã€‚ã€”ã€•ã€³ã‚*ã…¤ãˆãˆžãŽ®ãŽ¯ã†ãŸêž‰ï¸”ï¸•ï¸¿ï¹ï¹ž?ï¼Žï¼ï½¡ï¾*???ï¿¼ï¿½|159:4;high| -schedulerPrefs 0001,2 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/fire ¶â§¸â«»â«½â¿°â¿±â¿²â¿³â¿´â¿µâ¿¶â¿·â¿¸â¿¹â¿ºâ¿»ã€€ã€‚ã€”ã€•ã€³ã‚*ã…¤ãˆãˆžãŽ®ãŽ¯ã†ãŸêž‰ï¸”ï¸•ï¸¿ï¹ï¹ž?ï¼Žï¼ï½¡ï¾*???ï¿¼ï¿½|159:4;high| -schedulerPrefs 0001,2 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/fire
! ˜â…™â…š?â…œâ…â…žâ…Ÿâˆ•âˆ¶âŽ®â•±â§¶â§¸â«»â«½â¿°â¿±â¿²â¿³â¿´â¿µâ¿¶â¿·â¿¸â¿¹â¿ºâ¿»ã€€ã€‚ã€”ã€•ã€³ã‚*ã…¤ãˆãˆžãŽ®ãŽ¯ã†ãŸêž‰ï¸”ï¸•ï¸¿ï¹ï¹ž?ï¼Žï¼ï½¡ï¾*???ï¿¼ï¿½|159:4;high| -schedulerPrefs 0001,2 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/fire       0 â€§???????â€¯â€¹â€ºââ„â’âŸâ…“˜â…™â…š?â…œâ…â…žâ…Ÿâˆ•âˆ¶âŽ®â•±â§¶â§¸â«»â«½â¿°â¿±â¿²â¿³â¿´â¿µâ¿¶â¿·â¿¸â¿¹â¿ºâ¿»ã€€ã€‚ã€”ã€•ã€³ã‚*ã…¤ãˆãˆžãŽ®ãŽ¯ã†ãŸêž‰ï¸”ï¸•ï¸¿ï¹ï¹ž?ï¼Žï¼ï½¡ï¾*???ï¿¼ï¿½|159:4;high| -schedulerPrefs 0001,2 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/fire ¶â§¸â«»â«½â¿°â¿±â¿²â¿³â¿´â¿µâ¿¶â¿·â¿¸â¿¹â¿ºâ¿»ã€€ã€‚ã€”ã€•ã€³ã‚*ã…¤ãˆãˆžãŽ®ãŽ¯ã†ãŸêž‰ï¸”ï¸•ï¸¿ï¹ï¹ž?ï¼Žï¼ï½¡ï¾*???ï¿¼ï¿½|159:4;high| -schedulerPrefs 0001,2 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/fire
! bob          2787 pts/0  bash
! bob          3400 pts/0  watch tail syslog
! bob          3410 pts/0  watch tail /etc/log/syslog
! root         4472 pts/0  bash
! root         4471 pts/0  su
! root         3420 pts/0  sudo watch tail /etc/log/syslog
! root         4470 pts/0  sudo su
! root         3421 pts/0  watch tail /etc/log/syslog
! bob          3426 pts/1  bash
! root         4003 pts/1  bash
! root         4002 pts/1  su
! root         4001 pts/1  sudo su
! bob          4494 pts/2  bash
! root         4580 pts/2  /bin/sh /usr/sbin/chkrootkit
! root         5260 pts/2  ./chkutmp
! root         5262 pts/2  ps axk tty,ruser,args -o tty,pid,ruser,args
! root         5261 pts/2  sh -c ps axk "tty,ruser,args" -o "tty,pid,ruser,args"
! root         4577 pts/2  sudo chkrootkit
! bob          4508 pts/3  bash
! root         4558 pts/3  bash
! root         4557 pts/3  su
! root         4556 pts/3  sudo su
chkutmp: nothing deleted
Checking `OSX_RSPLUG'...                                    not tested

```
 
Theres a lot more and I'll be packaging it up if ever anyone needs it.. Hopefuly my next install goes well enough that I can move on #-o  ( and eventually figure out my  phone and mac :0 )

---

### Post by HermanAB on 2018-02-19
Well, it is unlikely, but not impossible, that you actually have a rootkit problem.  Tools like clamav and rkhunter will raise false alarms, so you need to look at the results carefully.

To see what is going on, run tcpdump and nethogs to see if there is any unwanted network activity.

---

### Post by iflowfor8hours on 2018-02-23
We're in the same boat it seems. I'm going the other route and trying to figure out what went into the shims that causes the malicious versions of journald and resolved to replace the existing ones. I've made some progress on the OSX version but nothing significant elsewhere. How have you been getting on?

---

### Post by xalu on 2018-02-26
Well my PC seems the most infected. The only OS that seems to have any luck is Qubes but its not compatible with some of my hardware. I may end up there eventually though.

My macbook appears clean after several reinstalls and wiping the drive / clearing ram on restart. 

I definitely have unwanted network activity. It's mostly arping, but I'll see if I can get anything else. 

I'm beginning to wonder if the infection  (or cause of infection) may also be present in my saved preferences for firefox. I've noticed that whenever I sign in to sync I get strange command line calls from firefox that are not there if I don't sign in.

---

### Post by kerry_s on 2018-02-26
have you checked for a router rootkit? it seems to me to infect so many devices/apps/os's in your internal network, it has to be somewhere your not looking.

---

### Post by xalu on 2018-02-27
> **kerry_s said:**
> have you checked for a router rootkit? it seems to me to infect so many devices/apps/os's in your internal network, it has to be somewhere your not looking.
I have a comcast tg1682 which I plan on replacing. I doubt I can scan/check it. I suppose I'll just swap it out. I also have a netgear Ive been using as a sidecar. It's definitely possible. I'll see if I can check the netgear at least.

Can anyone post the results of a chkrootkit scan while running firefox. Or what the command line looks like in system monitor. I'm usure of the baseline so it's hard to know if I'm just paranoid at this point. 

Here is the results from one of my scans.. They tend to resemble this:
```
! ˜â…™â…š?â…œâ…â…žâ…Ÿâˆ•âˆ¶âŽ®â•±â§¶â§¸â«»â«½â¿°â¿±â¿²â¿³â¿´â¿µâ¿¶â¿·â¿¸â¿¹â¿ºâ¿»ã€€ã€‚ã€”ã€•ã€³ã‚*ã…¤ãˆãˆžãŽ®ãŽ¯ã†ãŸêž‰ï¸”ï¸•ï¸¿ï¹ï¹ž?ï¼Žï¼ï½¡ï¾*???ï¿¼ï¿½|159:4;high| -schedulerPrefs 0001,2 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/fire       0 â€§???????â€¯â€¹â€ºââ„â’âŸâ…“˜â…™â…š?â…œâ…â…žâ…Ÿâˆ•âˆ¶âŽ®â•±â§¶â§¸â«»â«½â¿°â¿±â¿²â¿³â¿´â¿µâ¿¶â¿·â¿¸â¿¹â¿ºâ¿»ã€€ã€‚ã€”ã€•ã€³ã‚*ã…¤ãˆãˆžãŽ®ãŽ¯ã†ãŸêž‰ï¸”ï¸•ï¸¿ï¹ï¹ž?ï¼Žï¼ï½¡ï¾*???ï¿¼ï¿½|159:4;high| -schedulerPrefs 0001,2 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/fire ¶â§¸â«»â«½â¿°â¿±â¿²â¿³â¿´â¿µâ¿¶â¿·â¿¸â¿¹â¿ºâ¿»ã€€ã€‚ã€”ã€•ã€³ã‚*ã…¤ãˆãˆžãŽ®ãŽ¯ã†ãŸêž‰ï¸”ï¸•ï¸¿ï¹ï¹ž?ï¼Žï¼ï½¡ï¾*???ï¿¼ï¿½|159:4;high| -schedulerPrefs 0001,2 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/fire

```

---

### Post by kerry_s on 2018-02-27
why bother scanning, i would just delete the ~/.mozilla folder sign back into firefox, tada just like new.

i very much doubt your firefox sync is compromized, but you can choose what to sync, if anything it would be cookies you should avoid.

---

### Post by xalu on 2018-02-28
I think you are probably right. I am looking at commands I've only seen post infection so I am not very trusting of the running processes. I believe my system may be clean after several reinstalls and creating new install media several times. Tomorrow I'm receiving a clean dvd install disk so I'll be able to 100% certain.  I'm not seeing the rewrites and tmp directory issues I saw before so hopefully everything is good.  My network looks a lot better as well.

Worst case tomorrow I reinstall. 

lynis tool was a big help and obviously the chkrootkit/rkhunter/clamav tools. As a backup I've installed bitdefender and comodo linux to scan daily. HOPEFULLY this is the end but I've thought that before.  I also installed noscript, https everywhere, and adblock for firefox. I'm still not 100% sure about firefox but I'll post in firefox forums if the live cd doesn't clarify for me tomorrow.


iflowfor8hours, let me know what discoveries you make so I can keep an eye out. I am by no means an expert with all of this so any info would be useful for monitoring. 


Thanks for everyones input.

---

### Post by bnivihj2.dru on 2018-03-05
These are all IPs related to speedtest.net. 
You are not infected. 

Check the IP addresses against this:
[https://www.speedtestserver.com/](https://www.speedtestserver.com/)

If you wish to experience peace, provide peace for another.
Do not let the analysis of others destroy your inner peace. ~Internet Dalai Lama

---

