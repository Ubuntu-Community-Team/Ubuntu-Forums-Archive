---
title: "Ubuntu Server 18.04 too slow to boot up."
date: 2018-04-30
forum: Server Platforms
---

### Post by polcas.uy on 2018-04-30
Hi there,

I've installed Ubuntu Server 18.04 as a VM to use as a web server and it's taking very long to boot up.  During the booting process 100 seconds go by without any notice of what's happening.  I have several 16.04 in production and this doesn't happen with them.

Here's dmesg output, the issue is between 9.91 and 107.38:

```
[    5.437236] sd 2:0:0:0: [sda] Attached SCSI disk
[    5.595979] hv_utils: Registering HyperV Utility Driver
[    5.601516] scsi host3: storvsc_host_t
[    5.603642] input: Microsoft Vmbus HID-compliant Mouse as /devices/0006:045E:0621.0001/input/input4
[    5.604162] hid 0006:045E:0621.0001: input: <UNKNOWN> HID v0.01 Mouse [Microsoft Vmbus HID-compliant Mouse] on
[    5.628020] psmouse serio1: trackpoint: failed to get extended button data, assuming 3 buttons
[    5.687359] hv_vmbus: registering driver hv_util
[    5.703794] hv_utils: Heartbeat IC version 3.0
[    5.723355] hv_utils: Shutdown IC version 3.0
[    5.736464] hv_utils: TimeSync IC version 3.0
[    5.752895] hv_utils: VSS IC version 5.0
[    7.876183] random: crng init done
[    9.916153] psmouse serio1: trackpoint: IBM TrackPoint firmware: 0x01, buttons: 3/3
[    9.918321] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/input/input3
[    9.919259] input: AT Translated Set 2 keyboard as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:07/VMBUS:01/d34b2567-b9b6-42b9-8778-0a4ec0b955bf/serio2/input/input5
[  107.388005] raid6: sse2x1   gen()  8598 MB/s
[  107.456011] raid6: sse2x1   xor()  6011 MB/s
[  107.520013] raid6: sse2x2   gen() 10094 MB/s
[  107.584007] raid6: sse2x2   xor()  6636 MB/s
[  107.648010] raid6: sse2x4   gen() 12081 MB/s
[  107.728009] raid6: sse2x4   xor()  7607 MB/s
[  107.812007] raid6: avx2x1   gen() 16748 MB/s
[  107.884006] raid6: avx2x1   xor() 11320 MB/s
[  107.948008] raid6: avx2x2   gen() 19159 MB/s
[  108.012007] raid6: avx2x2   xor() 11900 MB/s
[  108.076005] raid6: avx2x4   gen() 22272 MB/s
[  108.140008] raid6: avx2x4   xor() 14181 MB/s
[  108.159630] raid6: using algorithm avx2x4 gen() 22272 MB/s
[  108.182276] raid6: .... xor() 14181 MB/s, rmw enabled
[  108.200728] raid6: using avx2x2 recovery algorithm
[  108.245762] xor: automatically using best checksumming function   avx
[  108.287018] async_tx: api initialized (async)
[  108.643865] Btrfs loaded, crc32c=crc32c-intel
[  108.896072] print_req_error: I/O error, dev fd0, sector 0
[  108.900007] floppy: error 10 while reading block 0
[  109.032390] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[  109.364683] ip_tables: (C) 2000-2006 Netfilter Core Team
[  109.402600] systemd[1]: systemd 237 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ +LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN2 +IDN -PCRE2 default-hierarchy=hybrid)
[  109.425550] systemd[1]: Detected virtualization microsoft.
[  109.457009] systemd[1]: Detected architecture x86-64.
```

Any help would be appreciated!  Thanks.

---

### Post by LHammonds on 2018-04-30
Here is an analysis tool you can also use.  The below was copy/pasted from my server install dox:

[size=4]Boot Issues[/size]

```
systemd-analyze plot > /srv/samba/share/boot.xml
```
Open boot.xml in a web browser to examine the boot process to see if anything is taking longer than it should.

```
systemd-analyze blame
```
This shows a list of all running processes ordered by the time it took to initialize.  Be careful not to judge a process too harshly at 1st sight...it may have been waiting on another process to initialize 1st.

```
dmesg > /tmp/boot.txt
```
Open boot.txt and observe the order of events from the moment it starts its boot all the way to the end.  The events are ordered by time and it shows how much time has passed since the machine was turned on for that particular event to occur.

---

### Post by polcas.uy on 2018-04-30
Thank you.

In my message I posted the result of "dmesg" and it shows nothing between 9 and 107 seconds, which is what I'd like to know how to look into that period of time and know what is happening there.

I tried your suggestions and here are the results:
systemd-analyze plot > /srv/samba/share/boot.xml
This shows in the first line the Kernel taking 109 seconds and then all the other process and services and their time.  Everything looks perfect except those 109 seconds for the Kernel, but doesn't show anything within those 109 seconds so nothing else to look at there.

As for this one:
systemd-analyze blame
This apparently works for services other than the Kernel or at least after systemd is triggered so still doesn't show why the Kernel took 109 seconds, so nothing to look at here either.

Let me know if you have any other ideas.  Thanks!

---

### Post by LHammonds on 2018-05-01
Is this a base 18.04 server?  With nothing else added to it yet?  I'm setting up an 18.04 server today and can look at what mine is doing and post the results to see if there is a similar delay.

Whatever process that is running might be hitting a timeout scenario (like a 90-second timeout).  If we can replicate and document what hardware scenarios this occurs on and what software configurations, we can probably get this fixed.  There was a bug in the [unattended-upgrades]("https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1661611") script in 16.04 that caused reboot issues that was eventually fixed in 16.04.3

**EDIT:**

Here is the top of my log:

```
[    0.000000] Linux version 4.15.0-20-generic (buildd@lgw01-amd64-039) (gcc version 7.3.0 (Ubuntu 7.3.0-16ubuntu3)) #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 (Ubuntu 4.15.0-20.21-generic 4.15.17)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-4.15.0-20-generic root=/dev/mapper/LVG-root ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] Disabled fast string operations

```

Here is the middle part of my log where the delay occurs (seems to be mad about there not being a floppy drive...but I added a floppy and it made no difference):

```

[    2.407827] fbcon: svgadrmfb (fb0) is primary device
[    2.408061]  sda: sda1 sda2 < sda5 >
[    2.408355] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.416683] Console: switching to colour frame buffer device 100x37
[    2.422015] [drm] Initialized vmwgfx 2.14.0 20170612 for 0000:00:0f.0 on minor 0
[    2.904013] raid6: sse2x1   gen()  5852 MB/s
[    2.952019] raid6: sse2x1   xor()  5243 MB/s
[    3.000007] raid6: sse2x2   gen()  8286 MB/s
[    3.048015] raid6: sse2x2   xor()  5799 MB/s
[    3.096006] raid6: sse2x4   gen() 10031 MB/s
[    3.144006] raid6: sse2x4   xor()  7056 MB/s
[    3.144031] raid6: using algorithm sse2x4 gen() 10031 MB/s
[    3.144055] raid6: .... xor() 7056 MB/s, rmw enabled
[    3.144576] raid6: using ssse3x2 recovery algorithm
[    3.147891] xor: automatically using best checksumming function   avx       
[    3.150309] async_tx: api initialized (async)
[    3.677864] Btrfs loaded, crc32c=crc32c-intel
[    3.828099] print_req_error: I/O error, dev fd0, sector 0
[    3.828779] floppy: error 10 while reading block 0
[    3.980436] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   35.176032] print_req_error: I/O error, dev fd0, sector 0
[   35.176830] floppy: error 10 while reading block 0
[   35.523986] print_req_error: I/O error, dev fd0, sector 0
[   35.525151] floppy: error 10 while reading block 0
[   35.636026] print_req_error: I/O error, dev fd0, sector 0
[   35.636824] floppy: error 10 while reading block 0
[   35.748028] print_req_error: I/O error, dev fd0, sector 0
[   35.748845] floppy: error 10 while reading block 0
[   35.860024] print_req_error: I/O error, dev fd0, sector 0
[   35.860848] floppy: error 10 while reading block 0
[   35.940031] random: crng init done
[   35.972034] print_req_error: I/O error, dev fd0, sector 0
[   35.972845] floppy: error 10 while reading block 0
[   36.088029] print_req_error: I/O error, dev fd0, sector 0
[   36.089083] floppy: error 10 while reading block 0
[   36.200000] print_req_error: I/O error, dev fd0, sector 0
[   36.200853] floppy: error 10 while reading block 0
[   36.312028] print_req_error: I/O error, dev fd0, sector 0
[   36.312797] floppy: error 10 while reading block 0
[   36.424019] print_req_error: I/O error, dev fd0, sector 0
[   36.424782] floppy: error 10 while reading block 0
[   36.536020] floppy: error 10 while reading block 0
[   36.648020] floppy: error 10 while reading block 0
[   36.763999] floppy: error 10 while reading block 0
[   36.876026] floppy: error 10 while reading block 0
[   36.988092] floppy: error 10 while reading block 0
[   37.100033] floppy: error 10 while reading block 0
[   37.212015] floppy: error 10 while reading block 0
[   37.328001] floppy: error 10 while reading block 0
[   37.440033] floppy: error 10 while reading block 0
[   37.552011] floppy: error 10 while reading block 0
[   37.664038] floppy: error 10 while reading block 0
[   37.775990] floppy: error 10 while reading block 0
[   37.887995] floppy: error 10 while reading block 0
[   38.007995] floppy: error 10 while reading block 0
[   38.120017] floppy: error 10 while reading block 0
[   38.231991] floppy: error 10 while reading block 0
[   38.344015] floppy: error 10 while reading block 0
[   38.456018] floppy: error 10 while reading block 0
[   38.567989] floppy: error 10 while reading block 0
[   38.700005] floppy: error 10 while reading block 0
[   38.816011] floppy: error 10 while reading block 0
[   38.928040] floppy: error 10 while reading block 0
[   39.115834] EXT4-fs (dm-2): mounted filesystem with ordered data mode. Opts: (null)
[   40.167310] ip_tables: (C) 2000-2006 Netfilter Core Team
[   40.207204] systemd[1]: systemd 237 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ +LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN2 +IDN -PCRE2 default-hierarchy=hybrid)
[   40.209454] systemd[1]: Detected virtualization vmware.
[   40.210173] systemd[1]: Detected architecture x86-64.
[   40.256842] systemd[1]: Set hostname to <tema1-mariadb>.
[   40.940788] systemd[1]: Unnecessary job for /dev/mapper/LVG-usr was removed.
[   40.941973] systemd[1]: Reached target User and Group Name Lookups.
[   40.943835] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[   40.946449] systemd[1]: Created slice User and Session Slice.
[   40.948598] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[   40.951562] systemd[1]: Created slice System Slice.
[   41.339469] Loading iSCSI transport class v2.0-870.

```

And here is the bottom of my log:

```

[   43.561730] EDAC sbridge: Seeking for: PCI ID 8086:0ea0
[   43.561741] EDAC sbridge:  Ver: 1.1.2 
[   44.310424] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
[   44.316059] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[   44.490905] Adding 1949692k swap on /dev/mapper/LVG-swap.  Priority:-2 extents:1 across:1949692k FS
[   44.574961] ppdev: user-space parallel port driver
[   44.948442] EXT4-fs (dm-3): mounted filesystem with ordered data mode. Opts: (null)
[   44.983895] systemd-journald[596]: Received request to flush runtime journal from PID 1
[   46.035579] EXT4-fs (dm-8): mounted filesystem with ordered data mode. Opts: (null)
[   46.036373] EXT4-fs (dm-7): mounted filesystem with ordered data mode. Opts: (null)
[   46.055003] EXT4-fs (dm-5): mounted filesystem with ordered data mode. Opts: (null)
[   46.079905] EXT4-fs (dm-4): mounted filesystem with ordered data mode. Opts: (null)
[   46.124498] EXT4-fs (dm-6): mounted filesystem with ordered data mode. Opts: (null)
[   46.588997] IPv6: ADDRCONF(NETDEV_UP): ens32: link is not ready
[   46.592572] e1000: ens32 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[   46.605769] IPv6: ADDRCONF(NETDEV_CHANGE): ens32: link becomes ready
[   47.623286] audit: type=1400 audit(1525186016.815:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="lxc-container-default" pid=1074 comm="apparmor_parser"
[   47.623292] audit: type=1400 audit(1525186016.815:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="lxc-container-default-cgns" pid=1074 comm="apparmor_parser"
[   47.623295] audit: type=1400 audit(1525186016.815:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="lxc-container-default-with-mounting" pid=1074 comm="apparmor_parser"
[   47.623297] audit: type=1400 audit(1525186016.815:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="lxc-container-default-with-nesting" pid=1074 comm="apparmor_parser"
[   47.727068] audit: type=1400 audit(1525186016.919:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=1076 comm="apparmor_parser"
[   47.727074] audit: type=1400 audit(1525186016.919:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1076 comm="apparmor_parser"
[   47.727077] audit: type=1400 audit(1525186016.919:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=1076 comm="apparmor_parser"
[   47.727079] audit: type=1400 audit(1525186016.919:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1076 comm="apparmor_parser"
[   47.732758] audit: type=1400 audit(1525186016.927:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/lxc-start" pid=1077 comm="apparmor_parser"
[   47.758218] audit: type=1400 audit(1525186016.951:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/man" pid=1078 comm="apparmor_parser"
[   49.313154] new mount options do not match the existing superblock, will be ignored

```

LHammonds

---

### Post by gaupe on 2018-06-12
I had something similar with ubuntu18.04 lts in a vmwareesxi 5.1 environment.  What solved it for me was to go in to the bios of thevirtual machine and disable the floppy drive.

---

### Post by LHammonds on 2018-06-12
> **gaupe said:**
> I had something similar with ubuntu18.04 lts in a vmwareesxi 5.1 environment.  What solved it for me was to go in to the bios of thevirtual machine and disable the floppy drive.
That got rid of the multitude of floppy error messages but the amount of time booting did not change much.  There was still a 30 second delay here:

```
[    3.774372] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   35.652493] random: crng init done
```

LHammonds

---

### Post by Redsandro on 2018-07-20
Did you figure this out **@LHammonds**? I have a similar problem, on my Lenovo X1 Yoga laptop, after installing Ubuntu 18.04.

The kernel waits approximately exactly 30 seconds before everything else is started.

```
kernel: [    0.000000] microcode: microcode updated early to revision 0x84, date = 2018-01-21
kernel: [    0.000000] Linux version 4.15.0-23-generic (buildd@lgw01-amd64-055) (gcc version 7.3.0 (Ubuntu 7.3.0-16ubuntu3)) #25-Ubuntu SMP Wed May 23 18:02:16 UTC 2018 (Ubuntu 4.15.0-23.25-generic 4.15.18)
(snip)
kernel: [    4.372132] [drm] Reducing the compressed framebuffer size. This may lead to less power savings than a non-reduced-size. Try to increase stolen memory size if available in BIOS.
kernel: [    4.644008] raid6: sse2x1   gen() 13608 MB/s
kernel: [    4.692005] raid6: sse2x1   xor()  9868 MB/s
kernel: [    4.740007] raid6: sse2x2   gen() 16965 MB/s
kernel: [    4.788003] raid6: sse2x2   xor() 11378 MB/s
kernel: [    4.836007] raid6: sse2x4   gen() 19502 MB/s
kernel: [    4.884004] raid6: sse2x4   xor() 11934 MB/s
kernel: [    4.932002] raid6: avx2x1   gen() 26758 MB/s
kernel: [    4.980004] raid6: avx2x1   xor() 18220 MB/s
kernel: [    5.028003] raid6: avx2x2   gen() 32577 MB/s
kernel: [    5.076003] raid6: avx2x2   xor() 20233 MB/s
kernel: [    5.124002] raid6: avx2x4   gen() 36536 MB/s
kernel: [    5.172002] raid6: avx2x4   xor() 22001 MB/s
kernel: [    5.172003] raid6: using algorithm avx2x4 gen() 36536 MB/s
kernel: [    5.172003] raid6: .... xor() 22001 MB/s, rmw enabled
kernel: [    5.172004] raid6: using avx2x2 recovery algorithm
kernel: [    5.173852] xor: automatically using best checksumming function   avx       
kernel: [    5.183581] Btrfs loaded, crc32c=crc32c-intel
kernel: [   36.298453] EXT4-fs (nvme0n1p5): mounted filesystem with ordered data mode. Opts: (null)
kernel: [   36.402786] ip_tables: (C) 2000-2006 Netfilter Core Team
kernel: [   36.461704] systemd[1]: systemd 237 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ +LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN2 +IDN -PCRE2 default-hierarchy=hybrid)
kernel: [   36.480252] systemd[1]: Detected architecture x86-64.

```


Between "[FONT=Courier New]Btrfs loaded[/FONT]" and "[FONT=Courier New]EXT4-fs: mounted filesystem[/FONT]" are thirty (30) seconds! What is happening here?

On the terminal, "[FONT=Courier New]systemd-analyze plot[/FONT]" just shows "kernel", and "[FONT=Courier New]systemd-analyze blame[/FONT]" does not show anything out of the ordinary.

---

### Post by LHammonds on 2018-07-21
> **Redsandro said:**
> Did you figure this out **@LHammonds**? I have a similar problem, on my Lenovo X1 Yoga laptop, after installing Ubuntu 18.04.

Negative.  I even [started a new thread](https://ubuntuforums.org/showthread.php?t=2393756) on it and documented the issue as much as I could (without my floppy drive issue in the way).

I have several 18.04 servers live now but booting takes 30 seconds longer than it used to on 16.04...but thankfully, I do not reboot Linux servers often.  And when I do reboot, it is typically around midnight when it detects "/var/run/reboot-required"

LHammonds

---

### Post by Redsandro on 2018-07-23
> **LHammonds said:**
> Negative. 

I figured out the problem for my case. Maybe it will work for you too.

I had this issue both on upgrade and *on clean install*.

Something auto-configured a swap/resume partition, and then the partition was reformatted and had a different UUID than was configured.

When I removed the UUID from [FONT=Courier New]/etc/initramfs-tools/conf.d/resume[/FONT] so that the file is like this:

```
RESUME=none
```

Then update the initramfs with the new settings by running: [FONT=Courier New]sudo update-initramfs -u[/FONT]

The 30 second delay is now gone, and my laptop boots unbelievably fast. I was disappointed first, but now I'm actually impressed. After GRUB it takes about 4-5 seconds.

Hope this helps.

---

### Post by LHammonds on 2018-07-24
Not the case for me.  The conf.d folder exists but the resume file does not.

I did verify that dm-0 exists and is the root LVM.

```
# dmsetup info /dev/dm-0
Name:              LVG-root
State:             ACTIVE
Read Ahead:        256
Tables present:    LIVE
Open count:        1
Event number:      0
Major, minor:      253, 0
Number of targets: 2
UUID: LVM-blahblahblahblahblahblahblahblahblah

```

Also made sure to list all volumes to ensure nothing was magically added during setup (like a swap volume).  Everything is how I configured it during install and valid.
```
# dmsetup ls
LVG-srv (253:5)
LVG-opt (253:6)
LVG-root        (253:0)
LVG-bak (253:4)
LVG-tmp (253:3)
LVG-usr (253:1)
LVG-var (253:2)
LVG-home        (253:7)
```

```
# blkid
/dev/sda1: LABEL="boot" UUID="blahblahblahblahblahblahblahblahblah" TYPE="ext2" PARTUUID="blahblahblah"
/dev/sda5: UUID="blahblahblahblahblahblahblahblahblah" TYPE="LVM2_member" PARTUUID="blahblahblah"
/dev/sdb1: UUID="blahblahblahblahblahblahblahblahblah" TYPE="LVM2_member" PARTUUID="blahblahblah"
/dev/mapper/LVG-root: LABEL="root" UUID="blahblahblahblahblahblahblahblahblah" TYPE="ext4"
/dev/mapper/LVG-usr: LABEL="usr" UUID="blahblahblahblahblahblahblahblahblah" TYPE="ext4"
/dev/mapper/LVG-var: LABEL="var" UUID="blahblahblahblahblahblahblahblahblah" TYPE="ext4"
/dev/mapper/LVG-tmp: LABEL="tmp" UUID="blahblahblahblahblahblahblahblahblah" TYPE="ext4"
/dev/mapper/LVG-bak: LABEL="bak" UUID="blahblahblahblahblahblahblahblahblah" TYPE="ext4"
/dev/mapper/LVG-srv: LABEL="srv" UUID="blahblahblahblahblahblahblahblahblah" TYPE="ext4"
/dev/mapper/LVG-opt: LABEL="opt" UUID="blahblahblahblahblahblahblahblahblah" TYPE="ext4"
/dev/mapper/LVG-home: LABEL="home" UUID="blahblahblahblahblahblahblahblahblah" TYPE="ext4"
```

---

### Post by mzemsk on 2018-08-29
I have the same problem with "crng init done".
My Ubuntu 18 server is running under MS server 2016 Hyper-v virtualization solution.
I tried to download last image of Ubuntu via torrent and installed second VM, but no luck, an error still here.
 Maybe my information would be helpful for problem resolving.


 ```
root@maindb-master:/home/pa# uname -r
4.15.0-33-generic

``` 

```


root@maindb-master:/home/pa# systemd-analyze
Startup finished in 3min 40.384s (kernel) + 9.377s (userspace) = 3min 49.761s
graphical.target reached after 7.150s in userspace
``` 


```
[    3.959777] hid 0006:045E:0621.0001: input: <UNKNOWN> HID v0.01 Mouse [Microsoft Vmbus HID-compliant Mouse] on
[    3.961890] hv_utils: Heartbeat IC version 3.0
[    3.964587] hv_utils: Shutdown IC version 3.0
[    3.966292] hv_utils: TimeSync IC version 4.0
[    3.968791] hv_utils: VSS IC version 5.0
[    4.204137] psmouse serio1: trackpoint: failed to get extended button data, assuming 3 buttons
[    8.497068] psmouse serio1: trackpoint: IBM TrackPoint firmware: 0x01, buttons: 3/3
[    8.505665] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/input/input3
[    8.509469] input: AT Translated Set 2 keyboard as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:07/VMBUS:01/d34b2567-b9b6-42b9-8778-0a4ec0b955bf/serio2/inp$
[   16.428110] random: crng init done
[   16.428115] random: 7 urandom warning(s) missed due to ratelimiting
[  221.416066] raid6: sse2x1   gen()  3405 MB/s
[  221.464076] raid6: sse2x1   xor()  1938 MB/s
[  221.512035] raid6: sse2x2   gen()  3323 MB/s
[  221.562630] raid6: sse2x2   xor()  2522 MB/s
[  221.612035] raid6: sse2x4   gen()  4944 MB/s


```

```
root@maindb-master:/home/pa# systemd-analyze blame
         2.270s cloud-init-local.service
          1.564s cloud-init.service
          1.203s cloud-config.service
          1.201s dev-sda2.device
          1.066s apparmor.service
          1.013s cloud-final.service
           852ms networkd-dispatcher.service
           691ms accounts-daemon.service
           677ms snapd.service
           607ms grub-common.service
           571ms lxd-containers.service
           520ms iscsid.service
           510ms ebtables.service
           502ms systemd-journal-flush.service
           355ms apport.service
           316ms thermald.service
           304ms keyboard-setup.service
           279ms systemd-logind.service
           269ms systemd-udev-trigger.service
           267ms systemd-timesyncd.service
           253ms systemd-modules-load.service
           236ms snap-core-4486.mount
           210ms systemd-resolved.service
           204ms ufw.service
           201ms rsyslog.service
           196ms sys-kernel-debug.mount
           193ms systemd-remount-fs.service
           193ms dev-mqueue.mount
           181ms polkit.service
           180ms ssh.service
           159ms user@1000.service
           154ms lvm2-monitor.service
           137ms setvtrgb.service
           136ms console-setup.service
           133ms plymouth-read-write.service
           129ms systemd-journald.service
           123ms blk-availability.service
           118ms systemd-sysctl.service
           116ms systemd-user-sessions.service


```

And there are similar problems:
[https://forum.manjaro.org/t/testing-update-2018-04-30-kernels-trizen-compiz/46125/9](https://forum.manjaro.org/t/testing-update-2018-04-30-kernels-trizen-compiz/46125/9)
[https://forum.manjaro.org/t/boot-delay-random-crng-init-done/47182/3](https://forum.manjaro.org/t/boot-delay-random-crng-init-done/47182/3)
[https://forum.mxlinux.org/viewtopic.php?t=45498](https://forum.mxlinux.org/viewtopic.php?t=45498)
[https://unix.stackexchange.com/questions/442698/when-i-log-in-it-hangs-until-crng-init-done](https://unix.stackexchange.com/questions/442698/when-i-log-in-it-hangs-until-crng-init-done)

Also I tried to install last kernel (4.18.0 from 20180812) but without luck. Problem still here.


              
The next step was to install cryptsetup, the answer was "cryptsetup is already last version".
I've tried every advice I can found.

As a last try I moved VM to other Hyper-V machine and problem resolved!!! I don't know how but it works without any delay.
 First server configuration (VM start delay present):
[http://i68.tinypic.com/2hf2kd2.jpg](http://i68.tinypic.com/2hf2kd2.jpg)
Second server configuration (no start delay):
[http://i63.tinypic.com/21cyw4x.png](http://i63.tinypic.com/21cyw4x.png)

 Any thoughts?

---

### Post by LHammonds on 2018-08-29
In [my thread](https://ubuntuforums.org/showthread.php?t=2393756&p=13787032#post13787032), I have isolated my issue to manual partitioning of LVM.  When you use "Guided - Use entire disk" it never seems to have this issue.

When choosing Manual LVM, it crops up every single time.  I have not yet figured out a way to keep this from happening when choosing manual LVM.

LHammonds

---

### Post by mzemsk on 2018-08-30
Default partitioning is not my choice, so I created partitions manually. 

```
Device         Start        End    Sectors  Size Type
/dev/sda1       2048       4095       2048    1M BIOS boot
/dev/sda2       4096   83890175   83886080   40G Linux filesystem
/dev/sda3   83890176  125833215   41943040   20G Linux swap
/dev/sda4  125833216 3733606399 3607773184  1.7T Linux filesystem
```

```
root@db-master:/home/pa# cat /etc/fstab
UUID=10847906-aaa7-11e8-948a-00155d4c2301 none swap sw 0 0
UUID=0b56cbc8-aaa7-11e8-948a-00155d4c2301 / ext4 defaults 0 0
UUID=115437d6-aaa7-11e8-948a-00155d4c2301 /var ext4 defaults 0 0
```

As you can see, I have no LVM and "EXT4-fs (dm-0):" errors.

---

### Post by LHammonds on 2018-08-30
Ah, that is good to know.  I will test a manual partitioning scheme and update my thread.

Out of curiosity, if you create a test VM and pick "Guided" for either option, does it boot quickly without the delay in your environment?

LHammonds

---

### Post by mzemsk on 2018-08-31
ok, I'll try.

---

### Post by mzemsk on 2018-09-03
I reinstalled Ubuntu server from last image 18.04.1 with guided partitioning, as a result I get quicker system boot:

[ATTACH=CONFIG]280961[/ATTACH]

But delay still here, no so long as previous, but it's a fact.

The second try was Debian (newest image) installation and there is no any delay!

---

