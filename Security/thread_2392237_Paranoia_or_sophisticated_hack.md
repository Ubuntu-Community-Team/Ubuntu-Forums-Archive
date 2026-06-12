---
title: "Paranoia or sophisticated hack?"
date: 2018-05-18
forum: Security
---

### Post by mattmuffin on 2018-05-18
Hello,

Last night I left my laptop at the office to transfer a big backup file overnight. I left around 11:30pm and came back around 8:50am. First thing I noticed was a new window on Firefox for a muslim dating website, which is strange because I strictly surf professional websites from this laptop. No facebook, twitter, nor any news website.

I then noticed that my file transmission was idle. It showed no progression at all. The computer was overall slow, and I had several apps (Thunderbird, libreoffice) that had a popup "Wait or Froce Quit".

I proceeded to restart the computer but it kept looping through the spalsh screen as shutdown. I hard reset it and started to use it.

When I checked my command history, I came across this string:

"<9d><87><83>ü¤^_°(8)]¨ýä«" repeating itself over 1000 times, sometimes with this string: "<9d><87>å^O×JßÎ/¨³å^Z^U-Ô<98>6<83>ü¤^_°(8)]¨ýä«" . No regular history commands were found.

I checked for syslog file and found these lines:

```
May 17 20:19:52 MyComp kernel: [24826.890103] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:6c:38:a1:11:fe:c4:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=34575 PROTO=2
May 17 20:21:41 MyComp gnome-session[2378]: Nautilus-Share-Message: Called "net usershare info" but it failed: Failed to execute child process "net" (No such file or directory)
May 17 20:21:57 MyComp kernel: [24951.927664] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:6c:38:a1:11:fe:c4:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=34576 PROTO=2
```

A little further down and I found these:

```
May 17 20:39:01 MyComp org.gnome.zeitgeist.SimpleIndexer[2207]: ** (zeitgeist-fts:2955): WARNING **: Unable to get info on application://nautilus-autostart.desktop
May 17 20:39:04 MyComp systemd[1]: Starting Clean php session files...
May 17 20:39:04 MyComp systemd[1]: Started Clean php session files.
May 17 20:40:41 MyComp kernel: [26076.650144] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:6c:38:a1:11:fe:c4:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=34585 PROTO=2
May 17 20:40:44 MyComp sudo: pam_ecryptfs: pam_sm_authenticate: /home/user1 is already mounted

May 17 21:08:40 MyComp org.gtk.vfs.Daemon[2207]: ** (gvfsd:2317): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Connection refused by server
May 17 21:08:48 MyComp dbus[755]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
May 17 21:08:48 MyComp systemd[1]: Starting Hostname Service...
May 17 21:08:48 MyComp dbus[755]: [system] Successfully activated service 'org.freedesktop.hostname1'
May 17 21:08:48 MyComp systemd[1]: Started Hostname Service.
May 17 21:08:52 MyComp gnome-session[2378]: Nautilus-Share-Message: Called "net usershare info" but it failed: Failed to execute child process "net" (No such file or directory)
May 17 21:17:01 MyComp CRON[22004]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

May 17 22:24:53 MyComp kernel: [32328.831071] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:6c:38:a1:11:fe:c4:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=34635 PROTO=2
May 17 22:24:54 MyComp kernel: [32329.752973] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:cc:c7:60:2b:70:3e:08:00 SRC=192.168.1.43 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=47483 PROTO=2
May 17 22:26:25 MyComp dbus[755]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
May 17 22:26:25 MyComp systemd[1]: Starting Hostname Service...
May 17 22:26:26 MyComp dbus[755]: [system] Successfully activated service 'org.freedesktop.hostname1'
May 17 22:26:26 MyComp systemd[1]: Started Hostname Service.
May 17 22:26:59 MyComp kernel: [32454.278304] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:6c:38:a1:11:fe:c4:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=34636 PROTO=2
May 17 22:29:04 MyComp kernel: [32579.453201] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:6c:38:a1:11:fe:c4:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=34637 PROTO=2

May 17 22:44:51 MyComp dhclient[2118]: DHCPREQUEST of 192.168.1.49 on wlan0 to 192.168.1.254 port 67 (xid=0xca99fb4)
May 17 22:44:51 MyComp dhclient[2118]: DHCPACK of 192.168.1.49 from 192.168.1.254
May 17 22:44:51 MyComp NetworkManager[971]: <info>  [1526589891.9082]   address 192.168.1.49
May 17 22:44:51 MyComp NetworkManager[971]: <info>  [1526589891.9082]   plen 24 (255.255.255.0)
May 17 22:44:51 MyComp NetworkManager[971]: <info>  [1526589891.9083]   gateway 192.168.1.254
May 17 22:44:51 MyComp NetworkManager[971]: <info>  [1526589891.9083]   server identifier 192.168.1.254
May 17 22:44:51 MyComp NetworkManager[971]: <info>  [1526589891.9083]   lease time 86400
May 17 22:44:51 MyComp NetworkManager[971]: <info>  [1526589891.9084]   hostname 'MyComp'
May 17 22:44:51 MyComp NetworkManager[971]: <info>  [1526589891.9084]   nameserver '192.168.1.254'
May 17 22:44:51 MyComp NetworkManager[971]: <info>  [1526589891.9084]   domain name 'lan'
May 17 22:44:51 MyComp NetworkManager[971]: <info>  [1526589891.9085] dhcp4 (wlan0): state changed bound -> bound
May 17 22:44:51 MyComp dbus[755]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
May 17 22:44:51 MyComp dhclient[2118]: bound to 192.168.1.49 -- renewal in 30823 seconds.
May 17 22:44:51 MyComp systemd[1]: Starting Network Manager Script Dispatcher Service...
May 17 22:44:51 MyComp dbus[755]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 17 22:44:51 MyComp systemd[1]: Started Network Manager Script Dispatcher Service.
May 17 22:44:51 MyComp nm-dispatcher: req:1 'dhcp4-change' [wlan0]: new request (1 scripts)
May 17 22:44:51 MyComp nm-dispatcher: req:1 'dhcp4-change' [wlan0]: start running ordered scripts...

May 18 00:13:58 MyComp kernel: [38873.317207] BUG: unable to handle kernel NULL pointer dereference at 0000000000000058
May 18 00:13:58 MyComp kernel: [38873.317323] IP: [<ffffffff81850829>] _raw_spin_trylock+0x9/0x30
May 18 00:13:58 MyComp kernel: [38873.317404] PGD 0
May 18 00:13:58 MyComp kernel: [38873.317437] Oops: 0000 [#1] SMP
May 18 00:13:58 MyComp kernel: [38873.317488] Modules linked in: ctr ccm drbg ansi_cprng bnep uvcvideo arc4 videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 iwldvm videobuf2_core v4l2_common mac80211 videodev media btusb snd_hda_codec_hdmi btrtl btbcm btintel bluetooth intel_rapl iwlwifi x86_pkg_temp_thermal intel_powerclamp coretemp snd_hda_codec_conexant thinkpad_acpi snd_hda_codec_generic crct10dif_pclmul joydev input_leds crc32_pclmul serio_raw snd_hda_intel ghash_clmulni_intel snd_hda_codec aesni_intel snd_hda_core aes_x86_64 snd_hwdep lrw gf128mul glue_helper snd_pcm ablk_helper snd_seq_midi cryptd snd_seq_midi_event snd_rawmidi cfg80211 nvram mei_me snd_seq mei lpc_ich shpchp snd_seq_device snd_timer snd soundcore mac_hid kvm_intel kvm irqbypass ip6t_REJECT nf_reject_ipv6 nf_log_ipv6 xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT nf_reject_ipv4 nf_log_ipv4 nf_log_common xt_LOG xt_limit xt_tcpudp xt_addrtype nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat parport_pc nf_conntrack_ftp ppdev nf_conntrack iptable_filter lp ip_tables parport x_tables autofs4 hid_generic usbhid hid i915 i2c_algo_bit drm_kms_helper syscopyarea psmouse sysfillrect sysimgblt fb_sys_fops sdhci_pci e1000e ahci sdhci drm libahci ptp pps_core wmi fjes video
May 18 00:13:58 MyComp kernel: [38873.319286] CPU: 2 PID: 43 Comm: kswapd0 Not tainted 4.4.0-125-generic #150-Ubuntu
May 18 00:13:58 MyComp kernel: [38873.319371] Hardware name: LENOVO 4291BC2/4291BC2, BIOS 8DET69WW (1.39 ) 07/18/2013
May 18 00:13:58 MyComp kernel: [38873.319457] task: ffff88040b4c4600 ti: ffff8800d4e84000 task.ti: ffff8800d4e84000
May 18 00:13:58 MyComp kernel: [38873.319540] RIP: 0010:[<ffffffff81850829>]  [<ffffffff81850829>] _raw_spin_trylock+0x9/0x30
May 18 00:13:58 MyComp kernel: [38873.319641] RSP: 0018:ffff8800d4e87b90  EFLAGS: 00010246
May 18 00:13:58 MyComp kernel: [38873.319702] RAX: 0000000000000000 RBX: ffff88030db353c0 RCX: ffffffff00000000
May 18 00:13:58 MyComp kernel: [38873.319780] RDX: 0000000000000001 RSI: ffffffff8122aa00 RDI: 0000000000000058
May 18 00:13:58 MyComp kernel: [38873.319858] RBP: ffff8800d4e87b90 R08: ffff8800d4e87be8 R09: ffff8800d4e87d00
May 18 00:13:58 MyComp kernel: [38873.319937] R10: 0000000000030786 R11: 0000000000000220 R12: 0000000000000000
May 18 00:13:58 MyComp kernel: [38873.320016] R13: ffff8800d4e87be8 R14: ffff88030db35418 R15: ffff88030d893b00
May 18 00:13:58 MyComp kernel: [38873.320096] FS:  0000000000000000(0000) GS:ffff88041e280000(0000) knlGS:0000000000000000
May 18 00:13:58 MyComp kernel: [38873.320185] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
May 18 00:13:58 MyComp kernel: [38873.320250] CR2: 0000000000000058 CR3: 0000000001e0a000 CR4: 0000000000060670
May 18 00:13:58 MyComp kernel: [38873.320327] Stack:
May 18 00:13:58 MyComp kernel: [38873.320354]  ffff8800d4e87bd8 ffffffff8122bc1f ffff8800d4e87be8 ffff880404c7a000
May 18 00:13:58 MyComp kernel: [38873.320453]  ffff8800d4e87be8 00000000000002ca ffff8800d4e87cf8 000000000000eb3b
May 18 00:13:58 MyComp kernel: [38873.320574]  0000000000000000 ffff8800d4e87c10 ffffffff8122d56a ffff88030dbf48c0
May 18 00:13:58 MyComp kernel: [38873.320711] Call Trace:
May 18 00:13:58 MyComp kernel: [38873.320754]  [<ffffffff8122bc1f>] shrink_dentry_list+0x11f/0x330
May 18 00:13:58 MyComp kernel: [38873.320826]  [<ffffffff8122d56a>] prune_dcache_sb+0x5a/0x80
May 18 00:13:58 MyComp kernel: [38873.320895]  [<ffffffff8121796f>] super_cache_scan+0x11f/0x1b0
May 18 00:13:58 MyComp kernel: [38873.320966]  [<ffffffff811a673d>] shrink_slab.part.40+0x20d/0x430
May 18 00:13:58 MyComp kernel: [38873.321039]  [<ffffffff811aad38>] shrink_zone+0x2c8/0x2e0
May 18 00:13:58 MyComp kernel: [38873.321103]  [<ffffffff811abdce>] kswapd+0x51e/0x990
May 18 00:13:58 MyComp kernel: [38873.321165]  [<ffffffff811ab8b0>] ? mem_cgroup_shrink_node_zone+0x1c0/0x1c0
May 18 00:13:58 MyComp kernel: [38873.321247]  [<ffffffff810a3417>] kthread+0xe7/0x100
May 18 00:13:58 MyComp kernel: [38873.321307]  [<ffffffff810a3330>] ? kthread_create_on_node+0x1e0/0x1e0
May 18 00:13:58 MyComp kernel: [38873.321384]  [<ffffffff818510f5>] ret_from_fork+0x55/0x80
May 18 00:13:58 MyComp kernel: [38873.321452]  [<ffffffff810a3330>] ? kthread_create_on_node+0x1e0/0x1e0
May 18 00:13:58 MyComp kernel: [38873.321524] Code: 01 00 00 00 f0 0f b1 17 85 c0 75 06 48 89 d8 5b 5d c3 89 c6 e8 e9 d3 87 ff 66 90 48 89 d8 5b 5d c3 90 66 66 66 66 90 55 48 89 e5 <8b> 07 85 c0 74 04 31 c0 5d c3 ba 01 00 00 00 f0 0f b1 17 85 c0
May 18 00:13:58 MyComp kernel: [38873.322186] RIP  [<ffffffff81850829>] _raw_spin_trylock+0x9/0x30
May 18 00:13:58 MyComp kernel: [38873.322279]  RSP <ffff8800d4e87b90>
May 18 00:13:58 MyComp kernel: [38873.322321] CR2: 0000000000000058
May 18 00:13:58 MyComp kernel: [38873.350029] ---[ end trace db68424a5f38f31e ]---
May 18 00:15:21 MyComp kernel: [38956.559477] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:6c:38:a1:11:fe:c4:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=34688 PROTO=2
May 18 00:17:01 MyComp CRON[23745]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

And then a bunch of ^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@

I found similar things in the auth.log file.

Also, in Firefox, all my stored passwords had been removed. I only stored lame passwords, from the test version of apps, but still.

Any thoughts?

The /home/user1 is encrypted, but does it mean it appears encrypted to any attacker or is it decrypted to any attacker since an active uncrypted session (mine) was active?

Thanks!

---

### Post by TheFu on 2018-05-18
Welcome to the forums.

Nuke it from orbit.  That's the only way to be sure.

80% of what you've posted is normal log stuff. 
Stay patched.
Always have both a hardware AND software firewall.
Don't allow Javascript from untrusted websites.
Don't allow ads from untrusted websites.
Don't download/bittorrent from dodgy locations. Never get programs this way.
Do versioned backups, automatically, daily.  Backup storage should be remote, "pulled", not pushed and never available as a network share.  If you have backups already, compare the last known-untouched one with the system as it is now. What changed?
Don't run services that you don't understand or cannot secure.  For example, do you do php anything? If not, don't install it.
Don't have trivial passwords anywhere.  Use an external password manager, have random userids AND random, 40+ character passwords. Use certificates and "keys" whenever available.  For websites, a u2f device for 2FA would be good.
Don't trust other computers on the same LAN implicitly.  One of them may have been hacked and is being used to attack all other systems.

If someone took over one of the websites your browser was on, other tabs could be opened pointing anywhere.

If I had any doubt at all, I'd wipe the machine and restore from the last known, good, backup.

Check out the "Security" sub-forum sticky threads at the top.  Review those AND all the links provided.

---

### Post by mattmuffin on 2018-05-18
Thanks for the reply. Yes I've prepared a new disk for swapping it and getting rid of the current one. Most of what you've recommended is already done, as a caution i've proceeded to changing all known passwords from al of my possible accounts. Still need to change my auth keys. As a precaution I'm also wiping all servers and restore data (not programs) onto another one.

What's worrying me is the remaining 20% of what I describe, the one that is not normal lot stuff.

Still investigating to find out if any personal files were taken.

Thanks!

---

### Post by TheFu on 2018-05-18
How might they have gotten in?
What services does the machine run?  Which are running that you didn't setup?
Can you prove everything you've claimed above about the system?  It is often the situation that we don't really understand some things, so an extra set of eyes is useful.

OTOH, if you are new, it is probably just easier to wipe the machine and start fresh.

---

### Post by mattmuffin on 2018-05-18
> **TheFu said:**
> How might they have gotten in?
I left the computer on all night, plugged to the Internet at the office. We have a basic wireless setup, from a router hooked to the fiber.

The obvious way would be through SSH but I havent changed the default setting in sshd_config:
```

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   IdentityFile ~/.ssh/id_ecdsa
#   IdentityFile ~/.ssh/id_ed25519
#   Port 22
#   Protocol 2
#   Cipher 3des
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
#   ProxyCommand ssh -q -W %h:%p gateway.example.com
#   RekeyLimit 1G 1h
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

```

I do not have any FTP/SFTP services on. I only install software from the official ubuntu repo. The system is updated automatically via apticron.

> What services does the machine run?  Which are running that you didn't setup?

```
 $ service --status-all
 [ + ]  acpid
 [ + ]  alsa-utils
 [ - ]  anacron
 [ + ]  apparmor
 [ + ]  apport
 [ - ]  atd
 [ + ]  avahi-daemon
 [ + ]  bluetooth
 [ - ]  bootmisc.sh
 [ - ]  brltty
 [ - ]  cgmanager
 [ - ]  cgproxy
 [ - ]  checkfs.sh
 [ - ]  checkroot-bootclean.sh
 [ - ]  checkroot.sh
 [ + ]  console-setup
 [ + ]  cron
 [ - ]  cryptdisks
 [ - ]  cryptdisks-early
 [ + ]  cups
 [ + ]  cups-browsed
 [ + ]  dbus
 [ - ]  dns-clean
 [ + ]  grub-common
 [ - ]  hostname.sh
 [ - ]  hwclock.sh
 [ + ]  irqbalance
 [ - ]  kerneloops
 [ - ]  keyboard-setup.dpkg-bak
 [ - ]  killprocs
 [ + ]  kmod
 [ + ]  lightdm
 [ - ]  mountall-bootclean.sh
 [ - ]  mountall.sh
 [ - ]  mountdevsubfs.sh
 [ - ]  mountkernfs.sh
 [ - ]  mountnfs-bootclean.sh
 [ - ]  mountnfs.sh
 [ + ]  mysql
 [ + ]  network-manager
 [ + ]  networking
 [ + ]  nginx
 [ + ]  ondemand
 [ + ]  openvpn
 [ - ]  pcscd
 [ - ]  php5-fpm
 [ + ]  php7.0-fpm
 [ + ]  pkcsslotd
 [ - ]  plymouth
 [ - ]  plymouth-log
 [ + ]  postfix
 [ - ]  pppd-dns
 [ + ]  procps
 [ + ]  qemu-kvm
 [ + ]  rc.local
 [ + ]  resolvconf
 [ - ]  rsync
 [ + ]  rsyslog
 [ - ]  saned
 [ - ]  sendsigs
 [ + ]  speech-dispatcher
 [ + ]  thermald
 [ ? ]  thin
 [ + ]  trousers
 [ + ]  udev
 [ + ]  ufw
 [ - ]  umountfs
 [ - ]  umountnfs.sh
 [ - ]  umountroot
 [ + ]  unattended-upgrades
 [ + ]  urandom
 [ - ]  uuidd
 [ + ]  whoopsie
 [ - ]  x11-common

```

> Can you prove everything you've claimed above about the system?  It is often the situation that we don't really understand some things, so an extra set of eyes is useful.

OTOH, if you are new, it is probably just easier to wipe the machine and start fresh.

Well, about JS and ads running, I activated JS for my dev sites and a few public ones. I did have an ad blocker extension (Ghostery) but it shows as being disabled. Of course I'll wipe the disk, I'm just trying to asses the damage and figure out if there really was a hack or not. The corrupted .bash_history and the weird characters in some logs tipped me off, as well as the fact that all the saved PWD in Firefox were wiped. Saved passwords on Chromium are stil lthere but Chromuim wasnt running last night, only Firefox was.

Again, maybe I'm just paranoid. I've tried to decypher some of the strings found in the .bash_history to no avail.

Thanks anyway for your feedback!

---

### Post by TheFu on 2018-05-18
The default ssh server is available over the internet?  No firewalling or limiting who can connect?  NEVER allow passwords to connect to ssh over the internet. NEVER.

Those services aren't for a normal desktop. Which did you not specifically configure and setup?

I've been hacked through bluetooth before.  Best to remove all bluetooth stuff from all computing systems, IMHO.

Wifi isn't exactly secure either, BTW.  Always use a full VPN when connecting to wifi.  I'm confused as to why openvpn as a server is running on a laptop?

Also, the "services" command only knows about normal services. You'll want/need to check the process table and use netstat and lsof to get a complete list.

Which router ports are open to the world for this system - you know - for inbound connections?  What are the local  firewall rules?

---

### Post by mattmuffin on 2018-05-18
Sorry, my bad, the ssh file I quoted is ssh_config and not sshd_config (the sshd_config does nto exist on my client).

I haven't configured any firewall, I assumed ubuntu came up with a pre configured one (ufw):

$ sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

As for the services, openvpn, php*, thin, nginx, I installed. I agree with you BT should be disabled. I thought I did so by switching it off via the settings menu. I installed the openvpn client to connect to a private vpn network from one of our partners.

The routers port opened inbound are 80 443 5000 5001 61828 45469. The only FW rule I see on the rooter is blocking port 25.

---

### Post by TheFu on 2018-05-19
Looks like UFW is setup to deny all inbound, if I'm reading that correctly.  It is surprising that it was enabled if you didn't enable it. Ubuntu doesn't enable the kernel firewall by default since there aren't any services listening from a normal install.  

The router should block everything by default, then you should only open and forward very specific protocols and ports. Using 2 firewalls - router + server is smart since there will be a misconfiguration at some point.
I wouldn't allow php, thin to be accessed from outside the localhost. I'd use nginx as a reverse proxy and lock down from where connections are allwoed.
ssh should also have protections against brute force attack and most of the world shouldn't have any ssh connection ability to your system.  Just those very specific places. Same for openvpn.  If Muffinland is the only place that should have vpn/ssh access, then do not allow anywhere else that access.   Also, never use passwords over the internet.

What is happening on ports 5000/5001?  For some reason, I think those are dangerous usually and shouldn't be enabled off localhost.

I find it most likely that a browser redirect and bug was used against you.  Using javascript they could map and attack any other systems on the same subnet, from the inside.  That isn't likely, but it will become more common.

Hopefully, some others will look over all this stuff and provide their comments and views.  We aren't in a position to see what you can see. Not seeing the changes between backup sets really makes it impossible to **Know** what happened.

---

### Post by HermanAB on 2018-05-20
That "muslim dating website" looks like a classic "Evil Maid Attack" and I can only surmise that your office cleaner is Muslim.

Another re-install party is probably a good idea.

---

### Post by mohicann on 2018-06-03
Have you got a cat? In the past, they used to play piano when they were passing by during the night... Now, they tend to mess your computer up...

---

### Post by oldos2er on 2018-12-16
From the Code of Conduct: **Religion:** This is a forbidden topic forum wide. Please find another venue to exercise your freedom of speech on this topic.

Closed.

---

