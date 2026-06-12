---
title: "Q: Weekly fstrim &amp; Ubuntu 16.04LTS KVM guest freeze"
date: 2018-03-12
forum: Virtualisation
---

### Post by linuksguru on 2018-03-12
[COLOR=#000000][FONT=Helvetica]Hi ![/FONT][/COLOR]


[COLOR=#000000][FONT=Helvetica]I have problematic VM (Ubuntu 16.04 LTS) which randomly freezes about each 2 - 3 weeks at weekends (when load is close to zero).[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]No updates or kernel upgrades help.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Freeze is not detected by oVirt watchdog and VM is not automatically restarted (oVirt is virtualization management program atop of KVM).[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]Since it happens only on weekends, I suspect some weekly cron job may cause this.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Ubuntu 16.04 LTS is installed on qcow2 disk image (thin provision).[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]is it possible that fstrim (which discards / trims unused blocks) is a source of this problem ?
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]I'm using virtio-SCSI, Ubuntu thin provision disk formatted as ext4 boot + ext4 root + swap.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Disk image on ext4 RAID 1 (2 x hard drives, not SSD, HP SmartArray p410i hardware RAID card).[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]Thanks in advance.[/FONT][/COLOR]

---

### Post by TheFu on 2018-03-12
The hostOS isn't Ubuntu?  I would look at the host.

fstrim only applies to SSDs, so I don't see that as being relevant.

I've been using Ubuntu Server as my VM hosts for over a decade and since switching to KVM in 2010, haven't seen freezes that weren't caused by disk read failures.  Actually, with Ubuntu as the hostOS using libvirtd, the guests are paused to protect their data if there is any slight read issue - like a CRC failure from a bad cable. I've never seen this on RAID-backed storage.

So, as I always ask ... what do the log files show?  On the hostOS and on the guest?  Should be able to ask journalctl for the logs  by time.

---

### Post by linuksguru on 2018-03-12
> **TheFu said:**
> The hostOS isn't Ubuntu?  I would look at the host.

fstrim only applies to SSDs, so I don't see that as being relevant.

I've been using Ubuntu Server as my VM hosts for over a decade and since switching to KVM in 2010, haven't seen freezes that weren't caused by disk read failures.  Actually, with Ubuntu as the hostOS using libvirtd, the guests are paused to protect their data if there is any slight read issue - like a CRC failure from a bad cable. I've never seen this on RAID-backed storage.

So, as I always ask ... what do the log files show?  On the hostOS and on the guest?  Should be able to ask journalctl for the logs  by time.


Host is CentOS 7 and KVM managed by oVirt. Other VMs, including Windows, and heavy loaded database, continue running as usual (on same host node).
Both times VM froze I'm was away.
Will salvage old logs and post again...

---

### Post by linuksguru on 2018-03-13
According to this article 
[https://chrisirwin.ca/posts/discard-with-kvm/](https://chrisirwin.ca/posts/discard-with-kvm/)
its possible to fstrim mounted qcow2 images even with running OS (with VirtIO-SCSI and writeback cache enabled). 
This is exactly what weekly cron script does on Ubuntu LTS. I removed it.

---

### Post by TheFu on 2018-03-13
I tried to test is on a sparse VM here.  
**UPDATE**:
So I more carefully read that link you provided - enable SCSI, then virtio-scsi on another libvirt tab ... and I'm seeing sda device inside the VM.  The lsblk is showing expected storage too.  fstrim -a worked fine.  No errors.    Checked the logs after running fstrim and don't see any related issues in there. Just some QXL stuff, but since this isn't a desktop, don't think it matters.

In short, not seeing the issue here with fstrim or virtio-scsi.  Both are working.  Could it be something else?

Ideas?
[B]
Older post:[/B]
```
$ sudo fstrim /
fstrim: /: the discard operation is not supported
```

Looked at all 3 of my VM hosts.  2x 16.04 and 1x 14.04.  Neither of the 16.04 systems support virtio-scsi and the 14.04 system supports the passthru and block versions, but not the non-block version.
```
$ kvm -device ? 2>&1|grep virtio-scsi
name "virtio-scsi-device", bus virtio-bus
name "virtio-scsi-pci", bus PCI

```

---

### Post by linuksguru on 2018-03-13
I'm not sure that cause of freeze is fstrim. It happens only at weekends, at random time. Other weekly cron scripts are harmless like rkhunter.

Run on Ubuntu guest.
$ lspci | grep storage
00:06.0 SCSI storage controller: Red Hat, Inc Virtio SCSI

$ fstrim --all -v
/boot: 703,4 MiB (737554432 bytes) trimmed
/: 247,7 GiB (265987293184 bytes) trimmed

Another suspected cause is network drivers, devices or misconfiguration.
Although VM is frozen to death, oVirt KVM watchdog 6300ESB don't recognize it as dead, and VM not restarted automatically.
I had MATE GUI run at the beginning, and it in turn launched NetworkManager. Right now MATE is disabled, yet NetworkManager and ModemManager are still running. 
I'll disable them when will be back, afraid to do such network setting changes remotely - if something goes wrong and VM fails to go online it will be a big problem.

$ lspci | egrep -i --color 'network|ethernet'
00:03.0 Ethernet controller: Red Hat, Inc Virtio network device
00:05.0 Ethernet controller: Red Hat, Inc Virtio network device

$ tail interfaces
auto lo ens5
iface lo inet loopback

iface ens5 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        broadcast 192.168.1.255
#       up ip route add 192.168.1.0/24 via 192.168.1.1
        up ip route add default via 192.168.1.1 dev ens5

---

### Post by TheFu on 2018-03-13
16.04 interfaces - you probably want a "gateway" setting.
Networking switches to NetPlan with 17.10 and later. There are some bugs in it that matter to enterprises, it appears.

I purge all network-manager stuff.  It used to behave poorly. 
Also, I don't use DEs, so that could be an issue. I to run my primary desktop inside a KVM VM and use x2go for all GUI connectivity outside the LAN.  Inside the LAN, ssh -X.

I also purge all bluetooth stuff.

BTW, that fstrim command shouldn't work without a sudo.

Are you using LVM?  My test doesn't.  I use LVM on physical machines, not inside VMs.  There are times when I miss it, however.

---

### Post by linuksguru on 2018-03-13
All commands in my previous post executed as root.
oVirt node installed on LVM thin provision as required per instruction.
However, disk images are kept on RAID, formatted as ext4 and mounted as plain partition.

---

### Post by TheFu on 2018-03-13
> **linuksguru said:**
> All commands in my previous post executed as root.
oVirt node installed on LVM thin provision as required per instruction.
However, disk images are kept on RAID, formatted as ext4 and mounted as plain partition.

I asked because having a separate /boot/ seems a little odd without using FDE or LVM **inside** the VM.  Plain partition (sda1/2...) is what I'm seeing here. I suspect the fstrim is not the core issue, but I'll leave it as it is and will definitely notice (or have a user complain) if the VPN isn't available. ;)

LVM on RAID1 (mdadm) on the hostOS is fine.  That's what I have.  Stopped using HW-RAID around 2012.  Obviously, don't have oVirt - hasn't been ported and some other reasons.  Plus, with only 20-30 VMs, it really isn't worth the overhead for us.

BTW, I assumed non-root for 2 reasons.  $ <--- normal user prompt, # is customary for a root shell.  And Ubuntu doesn't enable root by default, though any sudoer can get it trivially. 

Did the logs having anything?

---

### Post by linuksguru on 2018-03-14
I examined logs in the time frame before freeze.

**syslog**
Just before crash:
Mar 11 23:55:01 myhost CRON[16483]: (getmail) CMD (/usr/local/bin/run-getmail.sh > /dev/null 2>> /dev/null)
Mar 11 23:55:01 myhost CRON[16484]: (root) CMD (/usr/local/ispconfig/server/server.sh 2>&1 | while read line; do echo `/bin/date` "$line" >> /var/log/ispconfig/cron.log; done)
Mar 11 23:55:01 myhost CRON[16485]: (root) CMD (/usr/local/ispconfig/server/cron.sh 2>&1 | while read line; do echo `/bin/date` "$line" >> /var/log/ispconfig/cron.log; done)
Mar 11 23:55:01 myhost CRON[16486]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)

Jobs associated with ISPConfig (bind, Apache, Dovecot, Postfix, Clamav control panel).
Nothing that (I hope) could crash system.

**kern.log**
There are endless attempts of NetworkManager to activate unused ens3 interface. 
I'll disable NetworkManager completely.
Current kernel 4.13.0-36-generic, with previous kernels problem was the same.

Mar 11 23:49:44 myhost NetworkManager[660]: <info>  [1520804984.3348] policy: auto-activating connection 'Wired connection 1'
Mar 11 23:49:44 myhost NetworkManager[660]: <info>  [1520804984.3372] device (ens3): Activation: starting connection 'Wired connection 1' (12f3002f-bf2b-3c50-961c-57a15d1865d1)
Mar 11 23:49:44 myhost NetworkManager[660]: <info>  [1520804984.3382] device (ens3): state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar 11 23:49:44 myhost NetworkManager[660]: <info>  [1520804984.3404] device (ens3): state change: prepare -> config (reason 'none') [40 50 0]
Mar 11 23:49:44 myhost NetworkManager[660]: <info>  [1520804984.3418] device (ens3): state change: config -> ip-config (reason 'none') [50 70 0]
Mar 11 23:49:44 myhost NetworkManager[660]: <info>  [1520804984.3428] dhcp4 (ens3): activation: beginning transaction (timeout in 45 seconds)
Mar 11 23:49:44 myhost NetworkManager[660]: <info>  [1520804984.3478] dhcp4 (ens3): dhclient started with pid 16197
Mar 11 23:50:29 myhost NetworkManager[660]: <warn>  [1520805029.2756] dhcp4 (ens3): request timed out
Mar 11 23:50:29 myhost NetworkManager[660]: <info>  [1520805029.2757] dhcp4 (ens3): state changed unknown -> timeout
Mar 11 23:50:29 myhost NetworkManager[660]: <info>  [1520805029.2921] dhcp4 (ens3): canceled DHCP transaction, DHCP client pid 16197
Mar 11 23:50:29 myhost NetworkManager[660]: <info>  [1520805029.2922] dhcp4 (ens3): state changed timeout -> done
Mar 11 23:50:29 myhost NetworkManager[660]: <info>  [1520805029.2927] device (ens3): state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Mar 11 23:50:29 myhost NetworkManager[660]: <info>  [1520805029.2931] policy: disabling autoconnect for connection 'Wired connection 1'.
Mar 11 23:50:29 myhost NetworkManager[660]: <warn>  [1520805029.2933] device (ens3): Activation: failed for connection 'Wired connection 1'
Mar 11 23:50:29 myhost NetworkManager[660]: <info>  [1520805029.2955] device (ens3): state change: failed -> disconnected (reason 'none') [120 30 0]

**faillog**
160KB in size yet unreadable in text editor.

---

### Post by TheFu on 2018-03-14
Anything interesting from journalctl? Kernel, boot, or other errors?  Should be similar to what you already have, but ...

faillog is both a log file and a program.   $ **faillog -a** will show it.  Mine is 200Kb too, but only has about 40 records.  The system I looked at was a new install about 10 days ago (failed SSD).

---

### Post by linuksguru on 2018-03-14
faillog -a shows nothing useful, 0 failed logins.
[B]journalctl -k -b -p err
[/B]-- NO entries --
I run
**dpkg -l | awk {'print $2'} | xargs | debsums | grep -v 'OK'**
in order to verify if any of installed files/packages is corrupt.

/usr/share/locale-langpack/en/LC_MESSAGES/libidn.mo                     REPLACED
--- and similar
/usr/share/jailkit/jk_lib.pyc                                             FAILED
/usr/lib/python3/dist-packages/cupshelpers/__pycache__/__init__.cpython-35.pyc FAILED
--- and similar

Last seem to relate to Python cache files.
Reinstalled jailkit just for insurance.
VM in average uses only 1.25GB out of 8 GB allocated RAM.
Disabled Network manager and IPV6, enabled SYN cookies in custom-sysctl.conf.

net.ipv4.tcp_syncookies = 1
net.ipv4.tcp_max_syn_backlog = 2048
net.ipv4.tcp_synack_retries = 3

net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

vm.swappiness = 10
vm.vfs_cache_pressure = 50

 For now I've run out of options. Have to wait and see if freeze happens again.

---

