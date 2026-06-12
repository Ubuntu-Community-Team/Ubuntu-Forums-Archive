---
title: "Systemd experience - U cycle"
date: 2014-05-18
forum: Ubuntu Development Version
---

### Post by startas on 2014-05-18
So, who has already tried using systemd ? What difference does it make ?

---

### Post by Elfy on 2014-05-18
I've got a systemd vm and a systemd hardware install - I don't actually the hardware as much as this one - but I do use it, I've not actually noticed any differences in the way the system works and feels. 

At least it's easy in 14.10 - no mucking about with PPAs involved :)

---

### Post by zika on 2014-05-18
I'm using it on 14.04 from rhe very first day and it works like a clock... ;)

---

### Post by Elfy on 2014-05-18
Swiss clock or 

[IMG]http://www.ananseproductions.com/wp-content/uploads/2011/08/broken-clock.jpg[/IMG]

?

:p

---

### Post by zika on 2014-05-18
> **Elfy said:**
> Swiss clock or 

[IMG]http://www.ananseproductions.com/wp-content/uploads/2011/08/broken-clock.jpg[/IMG]

?

:p;)
I did not peek inside, who knows...

---

### Post by rrnbtter on 2014-05-18
Greetings,
Its working perfectly for my limited needs. I think this is under heavy development so you shouldn't believe old posts on the subject. 

```
rrnbtter@rrnbtter-Satellite-L305:~$ cat /proc/1/comm
systemd

rrnbtter@rrnbtter-Satellite-L305:~$ systemctl list-units
UNIT                        LOAD   ACTIVE SUB       DESCRIPTION
proc-sys...t_misc.automount loaded active running   Arbitrary Executable File Fo
sys-devi...-sdb-sdb1.device loaded active plugged   Multi-Card
sys-devi...block-sdb.device loaded active plugged   Multi-Card
sys-devi...und-card0.device loaded active plugged   82801I (ICH9 Family) HD Audi
sys-devi...-net-eth0.device loaded active plugged   RTL8101E/RTL8102E PCI Expres
sys-devi...net-wlan0.device loaded active plugged   WLL3141 (Toshiba PA3613U-1MP
sys-devi...0-hci0:12.device loaded active plugged   /sys/devices/pci0000:00/0000
sys-devi...ooth-hci0.device loaded active plugged   /sys/devices/pci0000:00/0000
sys-devi...-sda-sda1.device loaded active plugged   WDC_WD5000BEVT-24A0RT0
sys-devi...-sda-sda2.device loaded active plugged   WDC_WD5000BEVT-24A0RT0
sys-devi...-sda-sda5.device loaded active plugged   WDC_WD5000BEVT-24A0RT0
sys-devi...-sda-sda6.device loaded active plugged   WDC_WD5000BEVT-24A0RT0
sys-devi...-sda-sda7.device loaded active plugged   WDC_WD5000BEVT-24A0RT0
sys-devi...block-sda.device loaded active plugged   WDC_WD5000BEVT-24A0RT0
sys-devi...block-sr0.device loaded active plugged   PIONEER_DVD-RW_DVRTD08A
sys-devi...tty-ttyS0.device loaded active plugged   /sys/devices/platform/serial
sys-devi...tty-ttyS1.device loaded active plugged   /sys/devices/platform/serial
sys-devi...ty-ttyS10.device loaded active plugged   /sys/devices/platform/serial
sys-devi...ty-ttyS11.device loaded active plugged   /sys/devices/platform/serial
sys-devi...ty-ttyS12.device loaded active plugged   /sys/devices/platform/serial
sys-devi...ty-ttyS13.device loaded active plugged   /sys/devices/platform/serial
sys-devi...ty-ttyS14.device loaded active plugged   /sys/devices/platform/serial
sys-devi...ty-ttyS15.device loaded active plugged   /sys/devices/platform/serial
sys-devi...ty-ttyS16.device loaded active plugged   /sys/devices/platform/serial
sys-devi...ty-ttyS17.device loaded active plugged   /sys/devices/platform/serial
sys-devi...ty-ttyS18.device loaded active plugged   /sys/devices/platform/serial
sys-devi...ty-ttyS19.device loaded active plugged   /sys/devices/platform/serial
sys-devi...tty-ttyS2.device loaded active plugged   /sys/devices/platform/serial
sys-devi...ty-ttyS20.device loaded active plugged   /sys/devices/platform/serial
sys-devi...ty-ttyS21.device loaded active plugged   /sys/devices/platform/serial
sys-devi...ty-ttyS22.device loaded active plugged   /sys/devices/platform/serial
sys-devi...ty-ttyS23.device loaded active plugged   /sys/devices/platform/serial
sys-devi...ty-ttyS24.device loaded active plugged   /sys/devices/platform/serial
sys-devi...ty-ttyS25.device loaded active plugged   /sys/devices/platform/serial
sys-devi...ty-ttyS26.device loaded active plugged   /sys/devices/platform/serial
sys-devi...ty-ttyS27.device loaded active plugged   /sys/devices/platform/serial
sys-devi...ty-ttyS28.device loaded active plugged   /sys/devices/platform/serial
sys-devi...ty-ttyS29.device loaded active plugged   /sys/devices/platform/serial
sys-devi...tty-ttyS3.device loaded active plugged   /sys/devices/platform/serial
sys-devi...ty-ttyS30.device loaded active plugged   /sys/devices/platform/serial
sys-devi...ty-ttyS31.device loaded active plugged   /sys/devices/platform/serial
sys-devi...tty-ttyS4.device loaded active plugged   /sys/devices/platform/serial
sys-devi...tty-ttyS5.device loaded active plugged   /sys/devices/platform/serial
sys-devi...tty-ttyS6.device loaded active plugged   /sys/devices/platform/serial
sys-devi...tty-ttyS7.device loaded active plugged   /sys/devices/platform/serial
sys-devi...tty-ttyS8.device loaded active plugged   /sys/devices/platform/serial
sys-devi...tty-ttyS9.device loaded active plugged   /sys/devices/platform/serial
sys-devi...ttyprintk.device loaded active plugged   /sys/devices/virtual/tty/tty
sys-module-fuse.device      loaded active plugged   /sys/module/fuse
sys-subs...ices-hci0.device loaded active plugged   /sys/subsystem/bluetooth/dev
sys-subs...s-hci0:12.device loaded active plugged   /sys/subsystem/bluetooth/dev
sys-subs...ices-eth0.device loaded active plugged   RTL8101E/RTL8102E PCI Expres
sys-subs...ces-wlan0.device loaded active plugged   WLL3141 (Toshiba PA3613U-1MP
-.mount                     loaded active mounted   /
boot.mount                  loaded active mounted   /boot
dev-hugepages.mount         loaded active mounted   Huge Pages File System
dev-mqueue.mount            loaded active mounted   POSIX Message Queue File Sys
home.mount                  loaded active mounted   /home
media-rr...microsd7g1.mount loaded active mounted   /media/rrnbtter/microsd7g1
proc-sys...infmt_misc.mount loaded active mounted   Arbitrary Executable File Fo
run-lock.mount              loaded active mounted   Lock Directory
run-user-1000-gvfs.mount    loaded active mounted   /run/user/1000/gvfs
run-user.mount              loaded active mounted   User Runtime Directory
sys-fs-f...onnections.mount loaded active mounted   FUSE Control File System
sys-kernel-debug.mount      loaded active mounted   Debug File System
cups.path                   loaded active waiting   CUPS Printer Service Spool
systemd-...ord-console.path loaded active waiting   Dispatch Password Requests t
systemd-...ssword-wall.path loaded active waiting   Forward Password Requests to
acpid.service               loaded active running   ACPI event daemon
apparmor.service            loaded active exited    LSB: AppArmor initialization
atd.service                 loaded active running   Deferred execution scheduler
avahi-daemon.service        loaded active running   Avahi mDNS/DNS-SD Stack
binfmt-support.service      loaded active exited    Enable support for additiona
bluetooth.service           loaded active running   Bluetooth service
brltty.service              loaded active running   Braille Device Support
clamav-freshclam.service    loaded active running   LSB: ClamAV virus database u
colord.service              loaded active running   Manage, Install and Generate
console-...em-start.service loaded active exited    Console System Startup Loggi
cups-browsed.service        loaded active running   Make remote CUPS printers av
dbus.service                loaded active running   D-Bus System Message Bus
debian-fixup.service        loaded active exited    Various fixups to make syste
dns-clean.service           loaded active exited    LSB: Cleans up any mess left
[email]getty@tty1.servic[/email]e          loaded active running   Getty on tty1
grub-common.service         loaded active exited    LSB: Record successful boot 
kerneloops.service          loaded active running   LSB: Tool to automatically c
lightdm.service             loaded active running   Light Display Manager
ModemManager.service        loaded active running   Modem Manager
NetworkManager.service      loaded active running   Network Manager
ondemand.service            loaded active exited    LSB: Set the CPU Frequency S
polkitd.service             loaded active running   Authenticate and Authorize U
pppd-dns.service            loaded active exited    LSB: Restore resolv.conf if 
rc-local.service            loaded active exited    /etc/rc.local Compatibility
resolvconf.service          loaded active exited    Nameserver information manag
rsyslog.service             loaded active running   System Logging Service
rtkit-daemon.service        loaded active running   RealtimeKit Scheduling Polic
saned.service               loaded active exited    LSB: SANE network scanner se
spamassassin.service        loaded active exited    spamassassin.service
speech-dispatcher.service   loaded active exited    LSB: Speech Dispatcher
systemd-journald.service    loaded active running   Journal Service
systemd-logind.service      loaded active running   Login Service
systemd-...les-load.service loaded active exited    Load Kernel Modules
systemd-remount-fs.service  loaded active exited    Remount Root and Kernel File
systemd-sysctl.service      loaded active exited    Apply Kernel Variables
systemd-...etup-dev.service loaded active exited    Create static device nodes i
systemd-...es-setup.service loaded active exited    Recreate Volatile Files and 
systemd-...-trigger.service loaded active exited    udev Coldplug all Devices
systemd-udevd.service       loaded active running   udev Kernel Device Manager
systemd-...sessions.service loaded active exited    Permit User Sessions
udev-finish.service         loaded active exited    Copy rules generated while t
udisks2.service             loaded active running   Disk Manager
upower.service              loaded active running   Daemon for power management
virtualbox.service          loaded active exited    LSB: VirtualBox Linux kernel
whoopsie.service            loaded active running   crash report submission daem
wpa_supplicant.service      loaded active running   WPA supplicant
acpid.socket                loaded active running   ACPID Listen Socket
avahi-daemon.socket         loaded active listening Avahi mDNS/DNS-SD Stack Acti
cups.socket                 loaded active listening CUPS Printing Service Socket
dbus.socket                 loaded active running   D-Bus System Message Bus Soc
syslog.socket               loaded active running   Syslog Socket
systemd-initctl.socket      loaded active listening /dev/initctl Compatibility N
systemd-journald.socket     loaded active running   Journal Socket
systemd-shutdownd.socket    loaded active listening Delayed Shutdown Socket
systemd-...d-control.socket loaded active listening udev Control Socket
systemd-udevd-kernel.socket loaded active running   udev Kernel Socket
dev-sda5.swap               loaded active active    /dev/sda5
basic.target                loaded active active    Basic System
bluetooth.target            loaded active active    Bluetooth
cryptsetup.target           loaded active active    Encrypted Volumes
getty.target                loaded active active    Login Prompts
graphical.target            loaded active active    Graphical Interface
local-fs-pre.target         loaded active active    Local File Systems (Pre)
local-fs.target             loaded active active    Local File Systems
multi-user.target           loaded active active    Multi-User System
network.target              loaded active active    Network
nss-lookup.target           loaded active active    Host and Network Name Lookup
paths.target                loaded active active    Paths
remote-fs-pre.target        loaded active active    Remote File Systems (Pre)
remote-fs.target            loaded active active    Remote File Systems
sockets.target              loaded active active    Sockets
sound.target                loaded active active    Sound Card
swap.target                 loaded active active    Swap
sysinit.target              loaded active active    System Initialization
syslog.target               loaded active active    Syslog
timers.target               loaded active active    Timers
systemd-...iles-clean.timer loaded active waiting   Daily Cleanup of Temporary D

LOAD   = Reflects whether the unit definition was properly loaded.
ACTIVE = The high-level unit activation state, i.e. generalization of SUB.
SUB    = The low-level unit activation state, values depend on unit type.

145 loaded units listed. Pass --all to see loaded but inactive units, too.
To show all installed unit files use 'systemctl list-unit-files'.
lines 131-153/153 (END)
```

---

### Post by Gyokuro on 2014-05-18
Systemd is great - more details and fine grained but it's something new to learn as most of the time I had to manage upstart system (Ubuntu, RHEL6 - debian with sysv was easy but sometimes sysv-rc was really frustrating).

---

### Post by zika on 2014-05-19
> **rrnbtter said:**
> Greetings, 
Its working perfectly for my limited needs. I think this is under heavy development so you shouldn't believe **old posts** on the subject.What „old posts“ in a thread one day old?
What „old posts“ about peace of SW that we've started using (being available) very recently...? ;)

---

### Post by grahammechanical on 2014-05-19
In Utopic if have seen updates to systemd packages and to upstart packages. Tell me when the switch over is complete and I may be able to give my user experience but the switch over should not be noticeable to the user, the general or ordinary user, that is.

---

### Post by zika on 2014-05-19
What is nice is the fact that SystemD works with 3.15, liquorix, libre-gnu-kernel, everything I've thrown into its hands...

---

### Post by fantab on 2014-05-23
> **startas said:**
> So, who has already tried using systemd ? What difference does it make ?

To learn more about systemd and its benefits, read [this post]("https://bbs.archlinux.org/viewtopic.php?pid=1149530#p1149530") on another forum.
[systemd- Ubuntu Wiki]("https://wiki.ubuntu.com/systemd")

More: [URL="https://unix.stackexchange.com/questions/5877/what-are-the-pros-cons-of-upstart-and-systemd"]
https://unix.stackexchange.com/questions/5877/what-are-the-pros-cons-of-upstart-and-systemd[/URL][URL="http://www.jonmasters.org/blog/2011/04/29/response-to-why-systemd/"]
http://www.jonmasters.org/blog/2011/04/29/response-to-why-systemd/[/URL]
[http://monolight.cc/2011/05/the-systemd-fallacy/](http://monolight.cc/2011/05/the-systemd-fallacy/)

I have been using 'systemd' on my Archlinux which has it as default since 2012.
Fedora too has been using it since probably the same time as Arch. (I don't know about other distros, however).
If managed properly 'systemd' can really speed up the 'boot time'. [Read this]("http://www.harald-hoyer.de/2013/11/13/fedora-boot-optimization/") to learn what can be done in fedora to speed up boot times.

There are mixed views out there about which is better, 'init' or 'systemd'.
Personally, I can't tell which is better overall, however I feel that 'systemd' is a bit faster.

My two cents...

---

### Post by hyperreal on 2014-05-23
I am glad Ubuntu will eventually adopt systemd as its default init system.  I find it quite cumbersome to enable/disable system services with Upstart, as I have to go to /etc/init and rename unneeded services to <service>.disabled.  It's really easy to use the 'service <service> stop|start|etc command to stop and start them, but there is no obvious way to disable services so that they don't start at boot time.  systemd is great when it comes to managing services and run levels.  I also enjoy the journald feature of systemd, which allows you to view the system log with the journalctl -f command.  I have noticed that a systemd reduces bootup time by a significant amount.

---

### Post by zika on 2014-05-26
> **hyperreal said:**
> I have noticed that a systemd reduces bootup time by a significant amount.It really does... I've tried &#8222;old school&#8220; this weekend on several machines and numbers show real improvement... Back to SystemD... ;)

---

### Post by cariboo on 2014-05-26
I don't suppose any one has installed bootchart and done some comparisons.

---

### Post by Elfy on 2014-05-27
> **cariboo907 said:**
> I don't suppose any one has installed bootchart and done some comparisons.

Just for you :)

Systemd 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=253486&d=1401173670[/IMG]

Upstart
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=253487&d=1401173670[/IMG]

[https://www.dropbox.com/s/skzoam9kox9soaq/hob-unicorn-utopic-20140527-1.png](https://www.dropbox.com/s/skzoam9kox9soaq/hob-unicorn-utopic-20140527-1.png)
[https://www.dropbox.com/s/tzw206fu5ik90x0/hob-unicorn-utopic-20140527-2.png](https://www.dropbox.com/s/tzw206fu5ik90x0/hob-unicorn-utopic-20140527-2.png)

---

### Post by startas on 2014-05-27
And how to be sure that ubuntu 14.10 uses systemd or upstart for boot ? How to switch between these two ? Because as i saw, all systemd packages are already installed by default.

---

### Post by Elfy on 2014-05-27
to boot with systemd in utopic is simple

boot, edit the boot line - find the '*linux* line and add init=/lib/systemd/systemd then F10 will boot with systemd instead of upstart

when you're sure all is ok you can edit grub and add it there

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash init=/lib/systemd/systemd "

don't forget to update grub after changing that

---

### Post by rrnbtter on 2014-05-27
Greetings,
/proc/1/comm will tell you what system you are running. Init = Upstart, systemd = systemd
systemctl list-units will give you more info if its systemd.

Regarding boot time I am getting 80sec for both systems running a stop watch from a cold start kernel selection to the Unity Task Bar. I don't see how it is helpfull to measure to the hand-off when the GUI isn't available. Timing it to the GUI takes the same time on my system.

---

### Post by rrnbtter on 2014-05-27
Greetings,
Previous post aside, I prefer the systemd. My system seems much smoother  now than with upstart.  With systemd Ubuntu/Unity compatibility in  heavy development it keeps getting even better. The word "out there" is  that it won't be default until 16.04 but I can't see a reason to use  anything else now. After all systemd isn't new it has been used by most  of the Linux mainstream community for a few years.

---

### Post by startas on 2014-05-27
And bootchart is kind of broken i think, my system boots in 10 seconds, but bootchart generated picture shows me over a minute :D

---

### Post by cariboo on 2014-05-27
I see a decrease from 26 to 17 seconds boot time when using systemd

[[IMG]http://i.imgur.com/zhBtfHq.png[/IMG]](http://imgur.com/zhBtfHq)

with systemd

[[IMG]http://i.imgur.com/yyFrbNs.png[/IMG]](http://imgur.com/yyFrbNs)

---

### Post by zika on 2014-05-27
I do not mind which one is faster to boot since I tend not to see that much in my everyday usage of computers... That is why I use *nix...
What I do see is a bit more stable work on bunch of very different kernels and combination of tasks... Tha is why I still use SystemD.

---

### Post by zika on 2014-05-29
You were writing about speed of boot process...
[http://ubuntuforums.org/showthread.php?t=2226708](http://ubuntuforums.org/showthread.php?t=2226708) led me to investigate purpose of file /etc/init.d/.legacy-bootordering which led me to investigate /etc/init.d/rc and that closed the circle in```
CONCURRENCY="none"
```which reminded me of```
CONCURRENCY="shell"
```which most of You might even do not recognize as it was a nice way of speeding boot process in early days of Ubuntu... Such atavism made me try removing aforementioned file and executing reboot... It is a nice surprise,```
CONCURRENCY="shell"
```rides again... So, one unfortunate mistake could make some boot(s) even twice faster... ;)

Update&#8321;: For weeks I've been searching for a culprit that messed with my console-setup (in tty*) and finally, reverting to UpStart for some other reason, I found it: SystemD... ;) That is my only &#8222;complaint about systemD so far but a one that might keep me from it for some time while I need that setup... In X all is OK and I have ways of overriding that if i need but in tty it is a bit struggle... ;)

Update&#8322;: If You encounter list of warnings while installing some packages (for example util-linux) due to insserv do not panic but simply do```
sudo touch /etc/init.d/.legacy-bootordering
```because these errors are due to this file missing... Afterwards You could remove it again... ;)

---

### Post by zika on 2014-06-12
It seems that PPA proposed here is not refreshed so often...?
When are we to expect new version of Systemd for 14.04 (2.14 I suppose, now it is 2.04...)...?

---

### Post by startas on 2014-06-12
Well, its not that systemd is not being updated, its that version 2.04 is the last version that supports some old features that ubuntu needs, and they are now "teaching" new version of systemd to emulate those old things that ubuntu needs, it can take some time, but they will probably do it until release of 14.10.

---

### Post by zika on 2014-06-12
> **startas said:**
> Well, its not that systemd is not being updated, its that version 2.04 is the last version that supports some old features that ubuntu needs, and they are now "teaching" new version of systemd to emulate those old things that ubuntu needs, it can take some time, but they will probably do it until release of 14.10.Thank You, I'll be patient... Good work...

---

### Post by zika on 2014-06-18
It seems that SystemD does not honor &#8222;text&#8220; as kernel boot option?
I'll check again once there is opportunity to do a restart of this machine of mine... ;)

---

### Post by Elfy on 2014-06-18
don't need text as an option here - I've just not got quiet or splash there 

GRUB_CMDLINE_LINUX_DEFAULT="init=/lib/systemd/systemd vga=798"

---

### Post by zika on 2014-06-18
> **Elfy said:**
> don't need text as an option here - I've just not got quiet or splash there 
GRUB_CMDLINE_LINUX_DEFAULT="init=/lib/systemd/systemd vga=798"Neither I do in UpStart/SystemD if I want to end up in GUI but as I want to end up in TTY(CLI) **text** is kernel-boot-line option that worked for years... ;) Presuming I did understand Your post correctly since I think You did not get mine... ;)

---

### Post by Elfy on 2014-06-18
nope - I tend to assume that people are using a default system, which in fact should be the default assumption on the forum ;)

that's why you'll never see me in the random threads about kernels that aren't installed by default :p

---

### Post by zika on 2014-06-18
> **Elfy said:**
> nope - I tend to assume that people are using a default system, which in fact should be the default assumption on the forum ;)
that's why you'll never see me in the random threads about kernels that aren't installed by default :pNicely written... ;)
Everyone has its curse and I do carry my own with a smile on my face... ;)
I'll restrain myself, promise...
Still „text“ does not work with SystemD and works nicely with UpStart... ;)

---

### Post by Elfy on 2014-06-18
:lol:

have fun :)

don't think that I'd not be interested to know how though

---

### Post by zika on 2014-06-18
> **Elfy said:**
> :lol:

have fun :)

don't think that I'd not be interested to **know how **thoughIn having fun? ;P
This is not only for (my) fun but for being prepared for questions from users... ;)
Enough of off-topic, restraints are on (my) side of wire(less)...
Update&#8321;: Even /etc/init/lightdm.override is not honored by SystemD...

---

### Post by Cavsfan on 2014-06-20
> **Elfy said:**
> don't need text as an option here - I've just not got quiet or splash there 

GRUB_CMDLINE_LINUX_DEFAULT="init=/lib/systemd/systemd vga=798"


> **Elfy said:**
> nope - I tend to assume that people are using a default system, which in fact should be the default assumption on the forum ;)

that's why you'll never see me in the random threads about kernels that aren't installed by default :p

I don't install beta kernels or anything that's not installed by default either. But, let's just say I wanted to try systemd.
What would I need to do. I see from System Monitor that systemd-logind and systemd-udevd are both running but appear to be sleeping with zero activity.
Is there anything else I need to do besides change the boot line?
What does the [COLOR=#ff0000]vga=798[/COLOR] mean? I tried man systemd and couldn't find anything about it.

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep systemd
ii  libpam-systemd:amd64                                  204-10ubuntu9                              amd64        system and service manager - PAM module
ii  libsystemd-daemon0:amd64                              204-10ubuntu9                              amd64        systemd utility library
ii  libsystemd-journal0:amd64                             204-10ubuntu9                              amd64        systemd journal utility library
ii  libsystemd-login0:amd64                               204-10ubuntu9                              amd64        systemd login utility library
ii  systemd                                               204-10ubuntu9                              amd64        system and service manager
rc  systemd-services                                      204-5ubuntu20                              amd64        systemd runtime services
ii  systemd-shim                                          6-3                                        amd64        shim for systemd

```

---

### Post by zika on 2014-06-20
Strictly speaking it does not have anything to do with SystemD...
Kernel-boot-parameter:```

 VGA Resolution Codes for GRUB & Lilo
--- Depth --
Colors  bits  640x480  800×600  1024×768  1152×864 1280×1024  1600×1200
   256    8   vga=769  vga=771   vga=773   vga=353   vga=775    vga=796
 32000    ?   vga=784  vga=787   vga=790   vga= ?    vga=793    vga= ? 
 65000   16   vga=785  vga=788   vga=791   vga=355   vga=794    vga=798
 16.7M   24   vga=786  vga=789   vga=792   vga=795   vga=799
```

---

### Post by Elfy on 2014-06-20
> **Cavsfan said:**
> ... But, let's just say I wanted to try systemd.
What would I need to do. ...
Is there anything else I need to do besides change the boot line?...

No - that's all, though you could if you wanted to edit the linux line in Grub when you boot to see - to use systemd all the time, edit grub default.

AS zika says the vga= bit is something else :)

---

### Post by Cavsfan on 2014-06-20
> **zika said:**
> Strictly speaking it does not have anything to do with SystemD...
Kernel-boot-parameter:```

 VGA Resolution Codes for GRUB & Lilo
--- Depth --
Colors  bits  640x480  800×600  1024×768  1152×864 1280×1024  1600×1200
   256    8   vga=769  vga=771   vga=773   vga=353   vga=775    vga=796
 32000    ?   vga=784  vga=787   vga=790   vga= ?    vga=793    vga= ? 
 65000   16   vga=785  vga=788   vga=791   vga=355   vga=794    vga=798
 16.7M   24   vga=786  vga=789   vga=792   vga=795   vga=799
```

Thanks but my monitor resolution is not listed. 
 
```
cavsfan@cavsfan-MS-7529:~$ xrandr
Screen 0: minimum 8 x 8, current 1920 x 1200, maximum 8192 x 8192
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected primary 1920x1200+0+0 (normal left inverted right x axis y axis) 593mm x 371mm
   1920x1200      60.0*+   59.9  
   1920x1080      60.0     59.9     60.1     60.0  
   1680x1050      60.0  
   1600x1200      60.0  
   1440x900       59.9  
   1400x1050      60.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1280x720       60.0     59.9  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   720x480        59.9     60.1  
   640x480        75.0     72.8     59.9  
   480x480        59.9  
HDMI-0 disconnected (normal left inverted right x axis y axis)
```


> **Elfy said:**
> No - that's all, though you could if you wanted to edit the linux line in Grub when you boot to see - to use systemd all the time, edit grub default.

AS zika says the vga= bit is something else :)

I've got a 1920x1200 monitor and I don't see the code any where. I found one for 256 bit color but would prefer 16.7M colors :p
Any Idears?

And don't hate me just because I've got a big monitor. ;)

---

### Post by Cavsfan on 2014-06-20
Or maybe based on this statement I could use vga=792.

"GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vga=792" will give you a 1024x768 resolution. 
You can choose one of these resolutions: 640×480, 800×600, 1024×768, 1280×1024, 1600×1200, 1920×1200

EDIT: it says that would deprecated video. :(

---

### Post by Elfy on 2014-06-20
> **Cavsfan said:**
> Or maybe based on this statement I could use vga=792.

"GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vga=792" will give you a 1024x768 resolution. 
You can choose one of these resolutions: 640×480, 800×600, 1024×768, 1280×1024, 1600×1200, 1920×1200

I' only had that because I'm using the nvidia driver. To be honest it's only something that's left over from something I was playing with - it's not in grub anymore here.

It's all a bit offtopic for this thread tbh.

---

### Post by Cavsfan on 2014-06-20
> **Elfy said:**
> I' only had that because I'm using the nvidia driver. To be honest it's only something that's left over from something I was playing with - it's not in grub anymore here.

It's all a bit offtopic for this thread tbh.

I have an nvidia driver too. 
In /etc/default/grub I have GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Would I just change that to GRUB_CMDLINE_LINUX_DEFAULT="init=/lib/systemd/systemd" then?

This is not offtopic. Not if I'm trying to test systemd right?

I have an Nvidia Geforce 9800GT 1GB mem fairly old now.

---

### Post by Elfy on 2014-06-20
To test systemd - yes you can add that to the line then upgrade grub.

That will have you running systemd all the time.

If you want to just try it without it being your default - edit the linux line from grub at boot, e will let you edit the current boot line, you can add the init= part and then F10 to boot

---

### Post by oldfred on 2014-06-21
This is now really old. Have not seen anyone with Ubuntu use vga=. Some other distributions still do.

 vga=xxx is a deprecated boot option
Use this with your monitor size in /etc/default/grub:
GRUB_GFXMODE=1024x768
replace "set gfxmode=auto" by "set gfxmode=1366x768"
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993)
"VGA Deprecated" Message on Boot
[http://ubuntuforums.org/showthread.php?t=1453524](http://ubuntuforums.org/showthread.php?t=1453524)

---

### Post by Cavsfan on 2014-06-23
Thanks! I'll try that soon. I have been dealing with other problems recently and my grand daughter's 2 year birthday party was Saturday. Sorry about getting off topic.

I think I wil just right that down and do it at boot time  		Elfy. I have 3 Ubuntu OSs, 2 Mint OSs and Windows 7 on this thing and don't want them all to use systemd.

So, I just get on the line of Utopic and where I see **quiet splash** I replace it with **init=/lib/systemd/systemd** - got it.

Thanks oldfred for the explanation! :) I have my grub resolution set like this **GRUB_GFXMODE=1920x1200-24**. 24 bit color depth and it works.

Then I'll be able to tell you about my Systemd experience which will be on topic. :)

---

### Post by Elfy on 2014-06-23
> **Cavsfan said:**
> ...
I think I wil just right that down and do it at boot time  		Elfy. I have 3 Ubuntu OSs, 2 Mint OSs and Windows 7 on this thing and don't want them all to use systemd.

So, I just get on the line of Utopic and where I see **quiet splash** I replace it with **init=/lib/systemd/systemd** - got it....

It will only be the system that you've edited the linux line of grub in = not all of them, certainly not the windows one :)

---

### Post by Cavsfan on 2014-06-23
Thanks! I'll try that soon. I have been dealing with other problems recently and my grand daughter's 2 year birthday party was Saturday. Sorry about getting off topic.

I think I will just right that down and do it at boot time Elfy. I have 3 Ubuntu OSs, 2 Mint OSs and Windows 7 on this thing and don't want them all to use systemd.

So, I just get on the line of Utopic, press "e" and where I see **quiet splash** I replace it with **init=/lib/systemd/systemd** - got it.

Thanks oldfred for the explanation! :) I have my grub resolution set like this **GRUB_GFXMODE=1920x1200-24**. 24 bit color depth and it works.

Then I'll be able to tell you about my Systemd experience which will be on topic. :)

---

### Post by Cavsfan on 2014-06-25
> **Elfy said:**
> It will only be the system that you've edited the linux line of grub in = not all of them, certainly not the windows one :)

I made a special entry in grub for systemd. I'll see how that works here shortly.

```
menuentry "Utopic Unicorn 14.10 (Devel Branch)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}
menuentry "Utopic Unicorn 14.10 systemd (Devel Branch)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro init=/lib/systemd/systemd
        initrd /initrd.img
}
menuentry "Utopic Unicorn 14.10 (Devel Branch) (Recovery Mode)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro recovery nomodeset
        initrd /initrd.img
}
```

---

### Post by Cavsfan on 2014-06-25
So I booted with systemd. Didn't even include the "quiet splash" in the line and it booted right up as it did before.
I see systemd is using 6.07M of memory but zero cpu usage. 

BTW I am in gnome flashback (with compiz) if that makes any difference.

I see in System Monitor that systemd, systemd-journald, systemd-logind and systemd-udevd are running but all sleeping.
I guess that would be normal?

---

### Post by fjgaude on 2014-06-25
It seems that systemd is not default in 14.10. I tried it and it worked just fine, and quick! But how would we go about making it permanent? What config file to edit, please?

Thanks!

---

### Post by Cavsfan on 2014-06-25
> **fjgaude said:**
> It seems that systemd is not default in 14.10. I tried it and it worked just fine, and quick! But how would we go about making it permanent? What config file to edit, please?

Thanks!

Did you not see this post on page 2? [http://ubuntuforums.org/showthread.php?t=2224798&page=2&p=13034320#post13034320](http://ubuntuforums.org/showthread.php?t=2224798&page=2&p=13034320#post13034320)

Oops I forgot to press F10. I'll retry that one.

---

### Post by Cavsfan on 2014-06-25
#-oF10 didn't have any effect since I have a special entry in grub for systemd. #-o

---

### Post by Cavsfan on 2014-06-25
I installed bootchart and rebooted. Once into systemd and there was no log in /var/log/bootchart. The folder was completely empty. But I could see that systemd was running.
Then I booted into Utopic normally and it did produce a bootchart log and a .png picture. I could see that init was runnning and systemd was not.

I booted again into Utopic with systemd and still no bootchart log. In a nutshell I didn't notice enough of a difference in bootup times between the two to matter.
So, for me this is getting boring. 

[img]http://letsgrowleaders.com/wp-content/uploads/2013/10/bored.png[/img]

;)

---

### Post by Elfy on 2014-06-25
no bootchart with systemd - closest I get is systemd-analyze

Startup finished in 3.891s (kernel) + 25.167s (userspace) = 29.059

---

### Post by Cavsfan on 2014-06-25
systemd-analyze returned this:

Startup finished in 4.455s (kernel) + 15.702s (userspace) = 20.158s

I know one thing Ubuntu anything boots up faster than windows 7. It takes many minutes to say the least whereas Ubuntu takes seconds to start and seconds to go into suspend mode. :)
But then my machine is getting old. I heard an SSD boots by the time you let your finger off of the button.

I purged the Upstart log so I can't compare but there is very little difference on my machine.

---

### Post by fjgaude on 2014-06-26
> **Cavsfan said:**
> Did you not see this post on page 2? [http://ubuntuforums.org/showthread.php?t=2224798&page=2&p=13034320#post13034320](http://ubuntuforums.org/showthread.php?t=2224798&page=2&p=13034320#post13034320)

Oops I forgot to press F10. I'll retry that one.

I did, I did... but when you update-grub and reboot the line gets overwritten.

Need to install systemd and uninstall startup?

---

### Post by Elfy on 2014-06-26
> **fjgaude said:**
> I did, I did... but when you update-grub and reboot the line gets overwritten.

Need to install systemd and uninstall startup?

To get it stay as the boot option

Edit /etc/default/grub

Add the init=/lib/systemd/systemd bit to 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash init=/lib/systemd/systemd"

save and then update grub. 

If you run systemd by editing the line in grub at boot - that is a one time thing - you have to do so each time for it to boot with systemd.

---

### Post by fjgaude on 2014-06-26
Thanks... it works... I knew there was something I was doing wrong! <smile>

---

### Post by Elfy on 2014-06-26
welcome :)

---

### Post by Cavsfan on 2014-06-26
Another approach to enable choosing between booting with systemd or upstart (normal) is to do this. Create a text file in your home directory and copy this into it:
 ```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Utopic Unicorn 14.10 systemd (Devel Branch)" {
    set root=(hd[COLOR=#ff0000]0,5[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=#ff0000]sda5[/COLOR] ro quiet splash init=/lib/systemd/systemd
        initrd /initrd.img
}
```

What you put between the quotes on the menuentry line is entirely up to you. You could put "xyz" and that is what that menu entry will appear as at boot. Just as long as you know what it is.
Then of course change that in [COLOR=#ff0000]red[/COLOR] to point to the partition your Utopic install is on; mine is on hard disk one partion 5.
Then save that file as **06_custom** and then copy it to /etc/grub.d/ **sudo cp ~/06_custom /etc/grub.d/06_custom**
Then make it executable **sudo chmod +x /etc/grub.d/06_custom** and then enter **sudo update-grub** and the next time you boot you will see this line as the 1st menu entry.
Normal boot and the rest of the normal grub entries will appear below that first line.

If you grow tired of seeing that entry either make it unexecutable **sudo chmod -x /etc/grub.d/06_custom** or delete it **sudo rm /etc/grub.d/06_custom**
Then enter **sudo update-grub** and upon next boot it will be gone.

---

### Post by Cavsfan on 2014-06-26
> **grahammechanical said:**
> In Utopic if have seen updates to systemd packages and to upstart packages. Tell me when the switch over is complete and I may be able to give my user experience but the switch over should not be noticeable to the user, the general or ordinary user, that is.

It would appear that it's time has come. I have been using it for a couple of days now and cannot really tell any difference; maybe a little faster startup time and maybe a little more stable even on this development system.
It's pre-installed and just a simple tweak to the kernel command and viola your using systemd instead of upstart. :)

---

### Post by fooman on 2014-06-30
been using systemd for most of june now and all seems good here.  can't say if its any faster...don't have any data to back it up.  but all in all i would say it "feels" a little faster and the stability is definitely there.  i have had zero issues since switching over.   whether using the default kernel or my custom compiled version....its all good.  

:guitar:

---

### Post by fjgaude on 2014-06-30
My unscientific test shows systemd to boot from grub to working screen in four seconds, as apposed to five for upstart. Yes, a little fast, but surely stable as far as I can tell. <smile>

---

### Post by dgls on 2014-07-04
Hi

I've got Xubuntu Utopic (daily 20-21 jun 2014).
I would enable systemd.( linux ... init=/lib/systemd/systemd quiet splash)

If I start systemd with "nosplash" option, plymouth doesn't shows (as aspected) and all run fine.
If I start systemd with "splash" option, plymouth starts, but booting process freezes.
systemd shows its boot messages and last message I can see is:

```
[ OK ] Started Accounts.Authorize Users to run privileged tasks...d-244ee7e56da4..evince...

```
What's wrong ?

---

### Post by grahammechanical on 2014-07-04
Hi, I hope you people are having fun. I have not been following this thread. And what a nice long thread it is, too. But I have just scanned through it. I would like to add a couple of things. Booting with systemd is one thing but Ubuntu will not be converted to systemd until all the tasks that upstart performs have been switched to systemd. My second offering is this link. The wiki.ubuntu systemd page might be accurate but it was written before the decision to switch to systemd and so I have been looking for something more recent.

[http://www.piware.de/2014/04/booting-ubuntu-with-systemd-test-packages-available/](http://www.piware.de/2014/04/booting-ubuntu-with-systemd-test-packages-available/)

[https://bugs.launchpad.net/ubuntu/+bugs?field.tag=systemd-boot](https://bugs.launchpad.net/ubuntu/+bugs?field.tag=systemd-boot)

Regards.

---

### Post by fjgaude on 2014-07-05
I've been booting using **systemd** for a few weeks now in 14.10 without issue. My full load, Skype, VBox, VLC, Goldendict dictionary, etc., all work fine. I guess I don't use any apps that are not ready under systemd.

---

### Post by VinDSL on 2014-07-09
> **Cavsfan said:**
> But then my machine is getting old. I heard an SSD boots by the time you let your finger off of the button.

SSDs rawk!

Peppermint Five (systemd) boots in 9 sec. on my 6 year-old Dell Latitude w/ SSD  :)

[http://vindsl.com/images/Cathulu-trusty-20140705-2.png](http://vindsl.com/images/Cathulu-trusty-20140705-2.png)

---

### Post by Elfy on 2014-07-09
last time I looked bootchart wasn't working with systemd - best you could see what systemd-analyze in a terminal

@vindsl - tried to attach that image - not having it, possibly size - if you want the image in the post make it smaller and redo it :)

---

### Post by pqwoerituytrueiwoq on 2014-07-09
> **VinDSL said:**
> SSDs rawk!

Peppermint Five (systemd) boots in 9 sec. on my 6 year-old Dell Latitude w/ SSD  :)

[http://vindsl.com/images/Cathulu-trusty-20140705-2.png](http://vindsl.com/images/Cathulu-trusty-20140705-2.png)
i put a cheap ssd (~440MB/s read) in a shiny new system with a Intel Pentium G3220 CPU and xubuntu 14.04 boots in 2.3s after post, that is so fast you don't even get to see the splash screen

---

### Post by zika on 2014-07-18
After having serious problems in using /etc/rc.local, /etc/modules, even /etc/modules-load.d (which, by the way, symlinks modules.conf to /etc/modules), resolvconf and several other (to me) important services I've put my testing of SystemD to a suspend. Not happy but not dissapointed either. It will get upgraded and fixed and I'll be back... ;)

---

### Post by Cavsfan on 2014-07-18
I think an update to cgmanager broke systemd at least for me. I'm using upstart as systemd fails to boot.
Here's the bug if any one else has the same problem with systemd [https://bugs.launchpad.net/ubuntu/+source/cgmanager/+bug/1344196](https://bugs.launchpad.net/ubuntu/+source/cgmanager/+bug/1344196)

---

### Post by startas on 2014-07-18
Well, for me cgmanager update fails to install, so systemd still works :)

---

### Post by Cavsfan on 2014-07-18
> **startas said:**
> Well, for me cgmanager update fails to install, so systemd still works :)

Good but as zika mentioned you will sometimes have to boot with upstart to get updates. I did that and it updated fine but broke systemd. If you do that and it breaks systemd for you too add yourself to that bug report:
 [https://bugs.launchpad.net/ubuntu/+source/cgmanager/+bug/1344196](https://bugs.launchpad.net/ubuntu/+source/cgmanager/+bug/1344196)
I currently am the only one on it. :confused:

---

### Post by zika on 2014-07-18
> **Cavsfan said:**
> Good but as zika mentioned you will sometimes have to boot with upstart _**to get updates**_. I did that and it updated fine but broke systemd. If you do that and it breaks systemd for you too add yourself to that bug report:
 [https://bugs.launchpad.net/ubuntu/+source/cgmanager/+bug/1344196](https://bugs.launchpad.net/ubuntu/+source/cgmanager/+bug/1344196)
I currently am the only one on it. :confused:I did not write anything like that. What I did write is that there is way of circumventing some problems present in SystemD that prevent proper imbedding of some services so a trip to UPStart is a cure for that, getting files and triggers right, to say it litely: to finish setup of some packages that provide services.

---

### Post by Cavsfan on 2014-07-19
> **zika said:**
> I did not write anything like that. What I did write is that there is way of circumventing some problems present in SystemD that prevent proper imbedding of some services so a trip to UPStart is a cure for that, getting files and triggers right, to say it litely: to finish setup of some packages that provide services.

My bad I thought you posted that. Anyway it works for me. ;)

---

### Post by rrnbtter on 2014-07-21
Greetings,
Systemd fix installs with the new RC6 kernel. 

rrnbtter@Toshiba-Satellite-L305:~$ sysd
systemd
LSB Version:    core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:core-4.1-ia32:core-4.1-noarch:security-4.0-ia32:security-4.0-noarch:security-4.1-ia32:security-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu Utopic Unicorn (development branch)
Release:    14.10
Codename:    utopic
3.16.0-031600rc6-generic

---

### Post by Cavsfan on 2014-07-24
This fixed systemd for me. I was able to boot with it and everything is good.

[http://ubuntuforums.org/showthread.php?t=2234728&page=3&p=13081650#post13081650](http://ubuntuforums.org/showthread.php?t=2234728&page=3&p=13081650#post13081650)

---

### Post by zika on 2014-07-24
> **zika said:**
> After having serious problems in using /etc/rc.local, /etc/modules, even /etc/modules-load.d (which, by the way, symlinks modules.conf to /etc/modules), resolvconf and several other (to me) important services I've put my testing of SystemD to a suspend. Not happy but not disappointed either. It will get upgraded and fixed and I'll be back... ;)Forgot to write: my abstinence from SystemD was very short indeed. It kind of grew on me so I could not resist getting back to it and I did not regret that decision, again. Still same troubles but they can be either disregarded or circumvented.

---

### Post by Cavsfan on 2014-07-24
It booted a little faster the 2nd time:
```
cavsfan@cavsfan-MS-7529:~$ systemd-analyze
Startup finished in 4.405s (kernel) + 16.915s (userspace) = 21.320s
```

Once I seen in the bug that getting the 208 version fixed it I am back in it as well. ;)

---

### Post by Cavsfan on 2014-07-25
Anyone with SSD ran systemd-analyze? That has to be awesomely fast!

```
cavsfan@cavsfan-MS-7529:~$ systemd-analyze
Startup finished in 4.430s (kernel) + 17.440s (userspace) = 21.871s
```

I think I have a sata1 drive. :p

---

### Post by rrnbtter on 2014-07-25
Greetings,
rrnbtter@Toshiba-Satellite-L305:~$ systemd-analyze
Startup finished in 10.085s (kernel) + 30.596s (userspace) = 40.681s


I have a 500G WD SATA6 running on a SATA2 buss.

---

### Post by rrnbtter on 2014-07-26
Greetings,
rrnbtter@Toshiba-Satellite-L305:~$ sysda
Startup finished in 9.249s (kernel) + 22.686s (userspace) = 31.935s

I knocked off 9s by doing a complete removal of Braille. I think it installs and loads by default. Synaptic will clean it out.Go



rrnbtter@Toshiba-Satellite-L305:~$ sysda
Startup finished in 6.931s (kernel) + 22.318s (userspace) = 29.249s

Good grief! I knocked another 3s off by adding 'quiet splash' back into my grub.

---

### Post by PJs Ronin on 2014-07-26
Have been following this thread with interest.   I have two partitions, one is 14.04LTS and another which is a direct clone of that partition but upgraded to 14.10 and with systemd added.   My gut feel was that the systemd partition loaded faster and I got these numbers:```
pjsronin@utopic:~$ systemd-analyze
Startup finished in 7.398s (kernel) + 2.164s (userspace) = 9.563s
pjsronin@utopic:~$
```
I was pretty happy with that so I did a test.   I loaded the 14.04 partition and then did a restart and mandraulically timed the process until the lightdm login screen appeared back at the 14.04 partition... 34 seconds.   I then loaded the 14.10 partition, did a restart and timed it back to the 14.10 login screen... 34 seconds.

All on a 120Gb 840 EVO from a SATA 3Gb/s connector.   Not sure what that proves, if anything.

---

### Post by Cavsfan on 2014-08-01
Utopic testers you know that systemd has been fixed right? systemd 208 is in the repos:

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy systemd
systemd:
  Installed: 208-6ubuntu2
  Candidate: 208-6ubuntu2
  Version table:
 *** 208-6ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ utopic/main amd64 Packages
        100 /var/lib/dpkg/status
```

It seems to be working quite fine too. ;)

---

### Post by fjgaude on 2014-08-01
Okay, systemd seems to be installed by default.

frank@flash:~$ apt-cache policy systemd
systemd:
  Installed: 208-6ubuntu2
  Candidate: 208-6ubuntu2
  Version table:
 *** 208-6ubuntu2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic/main amd64 Packages
        100 /var/lib/dpkg/status
Now, fellows, could you tell me what it takes to run: systemd-analyze? I get:

frank@flash:~$ systemd-analyze
Failed to issue method call: No such property 'FirmwareTimestampMonotonic'

Help! And thanks!

---

### Post by Alan F on 2014-08-02
> **fjgaude said:**
> Okay, systemd seems to be installed by default.

frank@flash:~$ apt-cache policy systemd
systemd:
  Installed: 208-6ubuntu2
  Candidate: 208-6ubuntu2
  Version table:
 *** 208-6ubuntu2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic/main amd64 Packages
        100 /var/lib/dpkg/status
Now, fellows, could you tell me what it takes to run: systemd-analyze? I get:

frank@flash:~$ systemd-analyze
Failed to issue method call: No such property 'FirmwareTimestampMonotonic'

Help! And thanks!

Although Systemd is installed by default it is not activated. You are still booting with Upstart.

See Post #17 for details of how to activate Systemd.

Once Systemd is activated you will be able to use systemd-analyze in terminal.

My result ...

alan@alan-Ubuntu:~$ systemd-analyze
Startup finished in 3.357s (kernel) + 6.377s (userspace) = 9.734s
alan@alan-Ubuntu:~$

---

### Post by Cavsfan on 2014-08-02
It was working fine for me but it would not allow the computer to restart. It just hung there. I tried Cntl+Alt+F1 to login to GUI but couldn't enter anything.
I had to press the reset button to restart the system.
I'll try it again.

---

### Post by Alan F on 2014-08-02
Make sure that you add   "init=/lib/systemd/systemd", not "init=lib/systemd/systemd"

Omitting the / before lib will give the symptom you descibe (I know from experience!)

---

### Post by fjgaude on 2014-08-02
> **Alan F said:**
> Make sure that you add   "init=/lib/systemd/systemd", not "init=lib/systemd/systemd"

Omitting the / before lib will give the symptom you descibe (I know from experience!)

Thanks, Alan. It's working fine. 

frank@flash:~$ systemd-analyze
Startup finished in 1.162s (kernel) + 16.763s (userspace) = 17.926s

I have lots of stuff auto loaded. <smile>

---

### Post by Cavsfan on 2014-08-02
> **Alan F said:**
> Make sure that you add   "init=/lib/systemd/systemd", not "init=lib/systemd/systemd"

Omitting the / before lib will give the symptom you describe (I know from experience!)

It must have been a glitch yesterday,
I logged in via the Gnome Flashback (with Compiz) session.
I just rebooted via clicking on Shutdown from the top right panel, which takes me to the lightdm screen.
From there I again click on the top right icon and select Shutdown and then select the left part which is Restart. It works instantly this time.

Then I tried Restarting via the Logout icon in Cairo Dock and both worked great.

I am using the custom grub method I posted in post [_#58_]("http://ubuntuforums.org/showthread.php?t=2224798&page=6&p=13059146#post13059146") of this thread. But thanks for the info.

```
cavsfan@cavsfan-MS-7529:~$ systemd-analyze
Startup finished in 4.368s (kernel) + 16.706s (userspace) = 21.075s
```

Actually this is what my grub screen looks like: 3 entries for Utopic 1 - upstart, 2 - systemd and 3 - system recovery.

[[IMG]http://www.zimagez.com/miniature/20140629115939.jpg[/IMG]]("http://www.zimagez.com/zimage/20140629115939.php")

---

### Post by Cavsfan on 2014-08-02
I put it in suspend (sleep) and left for a couple hours. Came back and it was off. Don't know what caused that. It happened before then stopped. Weird.

---

### Post by fjgaude on 2014-08-03
I'm confused as to what systemd-analyze measures:

frank@flash:~$ systemd-analyze
Startup finished in 939ms (kernel) + 16.874s (userspace) = 17.814s

With a stop watch measures my startup from grub to useable desktop as **5.7** seconds with startup; with systemd, **4.6**.

From where to where is systemd-analyze measuring? When is **userspace** being measured? Anyone know? Thanks!

---

### Post by Cavsfan on 2014-08-03
> **fjgaude said:**
> I'm confused as to what systemd-analyze measures:

frank@flash:~$ systemd-analyze
Startup finished in 939ms (kernel) + 16.874s (userspace) = 17.814s

With a stop watch measures my startup from grub to useable desktop as **5.7** seconds with startup; with systemd, **4.6**.

From where to where is systemd-analyze measuring? When is **userspace** being measured? Anyone know? Thanks!

Check out **man systemd-analyze** in terminal for some information.

---

### Post by Cavsfan on 2014-08-03
**systemd-analyze critical-chain** provides some additional information.

```
cavsfan@cavsfan-MS-7529:~$ systemd-analyze critical-chain
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @17.020s
&#9492;&#9472;multi-user.target @17.020s
  &#9492;&#9472;[COLOR=#ff0000]kerneloops.service @16.897s +122ms[/COLOR]
    &#9492;&#9472;network-online.target @16.897s
      &#9492;&#9472;network.target @16.897s
        &#9492;&#9472;[COLOR=#ff0000]NetworkManager.service @8.652s +5.190s[/COLOR]
          &#9492;&#9472;basic.target @8.634s
            &#9492;&#9472;timers.target @8.632s
              &#9492;&#9472;systemd-tmpfiles-clean.timer @8.632s
                &#9492;&#9472;sysinit.target @8.632s
                  &#9492;&#9472;[COLOR=#ff0000]console-setup.service @3.204s +5.426s[/COLOR]
                    &#9492;&#9472;remote-fs.target @3.204s
                      &#9492;&#9472;local-fs.target @3.203s
                        &#9492;&#9472;[COLOR=#ff0000]run-lock.mount @3.199s +3ms[/COLOR]
                          &#9492;&#9472;local-fs-pre.target @3.199s
                            &#9492;&#9472;[COLOR=#ff0000]systemd-remount-fs.service @3.168s +30ms[/COLOR]
                              &#9492;&#9472;[COLOR=#ff0000]systemd-fsck-root.service @1.413s +1.753s[/COLOR]
                                &#9492;&#9472;systemd-journald.socket @1.136s
                                  &#9492;&#9472;-.mount @1.135s
                                    &#9492;&#9472;system.slice @1.434s
                                      &#9492;&#9472;-.slice @1.413s
cavsfan@cavsfan-MS-7529:~$ 

```

```
cavsfan@cavsfan-MS-7529:~$ systemd-analyze
Startup finished in 4.393s (kernel) + 17.024s (userspace) = 21.417s
```

I guess if you added all of the top numbers together they would equal the bottom numbers. But, that is a little too much work for me.

---

### Post by fjgaude on 2014-08-03
graphical.target @16.237s
&#9492;&#9472;multi-user.target @16.237s
  &#9492;&#9472;kerneloops.service @16.225s +11ms
    &#9492;&#9472;network-online.target @16.225s
      &#9492;&#9472;network.target @16.225s
        &#9492;&#9472;NetworkManager.service @926ms +147ms
          &#9492;&#9472;basic.target @920ms
            &#9492;&#9472;timers.target @919ms
              &#9492;&#9472;systemd-tmpfiles-clean.timer @919ms
                &#9492;&#9472;sysinit.target @919ms
                  &#9492;&#9472;console-setup.service @660ms +259ms
                    &#9492;&#9472;remote-fs.target @659ms
                      &#9492;&#9472;local-fs.target @658ms
                        &#9492;&#9472;run-user-1000-gvfs.mount @1.524s
                          &#9492;&#9472;run-user.mount @596ms +1ms
                            &#9492;&#9472;local-fs-pre.target @595ms
                              &#9492;&#9472;systemd-remount-fs.service @592ms +2ms
                                &#9492;&#9472;systemd-fsck-root.service @110ms +481ms
                                  &#9492;&#9472;systemd-journald.socket @85ms
                                    &#9492;&#9472;-.mount @84ms

frank@flash:~$ systemd-analyze
Startup finished in 900ms (kernel) + 16.239s (userspace) = 17.139s

Ubuntu Unity Linux on Z87 Haswell motherboard, ASRock Model Z87E-ITX with Intel i5-4670K CPU 3.4GHz (800MHz-4.0GHz overclock), HD4600 video, Titan CU30 cooler, 16G DDR3 G.Skill 2400MHz, Plextor M5S 256G and M5P 128G SSDs, WD VelociRaptor WD5000BHTZ 500G HDD, 300W SFX psu, latest UEFI BIOS 2.30. Suspend and Resume without issue. Booting fast, 5 to 20 seconds, from either Plextor SSD or VelociRaptor HDD in Lian Li PC-Q30X case.

It seems putting the init=/lib in the /etc/default/grub file doesn't work for now. Strange, it did a week ago. I added it to the grub line at boot up for this test.

Thanks for all the help, guys!

---

### Post by Cavsfan on 2014-08-05
As I mentioned in post #89 when awaking from suspend after a few hours of running Utopic booted with systemd it shutoff completely after putting it in suspend. 
Yesterday I booted into Trusty normally with upstart and left for about 6-7 hours, came back and it immediately woke from suspend by touching the keyboard.  
I've been running systemd on Utopic for 6 hours or so and no problems whatsoever.

I'll put it in suspend mode for a few hours again as soon as I get the opportunity and see if it reoccurs.

---

### Post by fjgaude on 2014-08-06
Well, I come out of suspend without issues, at least after an hour or so wait. Haven't been up to leaving the partition on all night and resume in the morning. So much changing now, we'll let it all be for awhile.

---

### Post by Cavsfan on 2014-08-07
> **fjgaude said:**
> Well, I come out of suspend without issues, at least after an hour or so wait. Haven't been up to leaving the partition on all night and resume in the morning. So much changing now, we'll let it all be for awhile.

Yeah right. We got a bunch of systemd updates just now so a lot is changing. I look and see that somehow I booted into Upstart. I probably need to reboot any way into systemd Utopic. :)

If any one else is booting with systemd and can report on a successful wakeup after a several hour suspend please let us know. It may be fixed I just haven't had a chance to try it yet.

---

### Post by fjgaude on 2014-08-07
It's not fixed. The code is not accessing the /default/grub file as best as I tell... it'll be fixed one of these days, before Beta. <grin>

---

### Post by Cavsfan on 2014-08-07
> **fjgaude said:**
> It's not fixed. The code is not accessing the /default/grub file as best as I tell... it'll be fixed one of these days, before Beta. <grin>

Did you not try my simple method of adding the ability to boot into upstart, systemd or recovery just by selecting it from the grub menu?

Just enter this in a text file:
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above. 
menuentry "Utopic Unicorn 14.10 (Devel Branch)" {
    set root=(hd[COLOR=#ff0000]0,5[/COLOR])
        linux /vmlinuz root=/dev/sd[COLOR=#ff0000]a5[/COLOR] ro quiet splash
        initrd /initrd.img
}
menuentry "Utopic Unicorn 14.10 systemd (Devel Branch)" {
    set root=(hd[COLOR=#ff0000]0,5[/COLOR])
        linux /vmlinuz root=/dev/sd[COLOR=#ff0000]a5[/COLOR] ro quiet splash init=/lib/systemd/systemd
        initrd /initrd.img
}
menuentry "Utopic Unicorn 14.10 (Devel Branch) (Recovery Mode)" {
    set root=(hd[COLOR=#ff0000]0,5[/COLOR])
        linux /vmlinuz root=/dev/sd[COLOR=#ff0000]a5[/COLOR] ro recovery nomodeset
        initrd /initrd.img
}
```

Changing the red to point to your Utopic partition and then saving it as **/etc/grub.d/06_custom** make it executable **sudo chmod +x /etc/grub.d/06_custom** and then **sudo update-grub**.
When you reboot those 3 entries will be the first 3 on top. The text is totally up to you as you will be the only one to see it.

It's working great for me and I haven't touched **/etc/default/grub**.

To reverse this: **chmod +x /etc/grub.d/06_custom** or **sudo rm /etc/grub.d/06_custom** and then **sudo update-grub** and it will be like you never touched grub.

Here is my **/etc/default/grub** file:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=11
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=60
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_FONT=/boot/grub/DejaVuSansMono.pf2 

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1920x1200-24

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by fjgaude on 2014-08-07
I'm not looking for work-a-rounds... just wanting to report bugs if I am sure of such. But thanks for your info, Cavcfan.

---

### Post by Elfy on 2014-08-08
> **Cavsfan said:**
> ...

If any one else is booting with systemd and can report on a successful wakeup after a several hour suspend please let us know. It may be fixed I just haven't had a chance to try it yet.

suspended just for you ;)

worked fine for me

---

### Post by cariboo on 2014-08-08
Has anyone else noticed that systemd doesn't seem to be a robust as upstart. I had a hard lockup pf my own making, and had to use the power button to shut the system down, on rebooting my system booted to a black screen with no cursor flashing, I did hear the system start sound, but couldn't do anything else. The only way to get the system back to the way it was, was to do a complete re-install, as even disabling systemd and re-installing the graphics driver from the recovery console didn't help.

---

### Post by Cavsfan on 2014-08-08
> **fjgaude said:**
> I'm not looking for work-a-rounds... just wanting to report bugs if I am sure of such. But thanks for your info, Cavcfan.

That is not technically a work-a-around it is more of an easy way to boot into either systemd or (normal) upstart. But if you like typing stuff in at the grub menu, that's up to you.

> **Elfy said:**
> suspended just for you ;)

worked fine for me

How long did you stay in suspend? I've done it for a while with no problem but that time was several hours and it turned completely off. Haven't tried it since.

---

### Post by Cavsfan on 2014-08-08
> **cariboo907 said:**
> Has anyone else noticed that systemd doesn't seem to be a robust as upstart. I had a hard lockup pf my own making, and had to use the power button to shut the system down, on rebooting my system booted to a black screen with no cursor flashing, I did hear the system start sound, but couldn't do anything else. The only way to get the system back to the way it was, was to do a complete re-install, as even disabling systemd and re-installing the graphics driver from the recovery console didn't help.

Wow! I haven't experienced anything like that. Either one is about the same on this old computer. I don't notice any discernible differences with the naked eye.
But systemd seems to be running fairly good here. Yesterday Firefox hung for a while and I rebooted.

---

### Post by fjgaude on 2014-08-08
Well, systemd causes a little faster boot but nothing else, on my main box that has multiple drives and partitions.

I have had it in suspend for many hours and come out of it without issue. Remember, I'm into Intel integrated graphics. So... I wait until systmed gets installed automatically.

---

### Post by DogMatix on 2014-08-08
It seems there are various idiosyncrasies with systemd that people are experiencing. I haven't had any issue resuming from suspend (intel graphics), even if left overnight. I have had booting to a black screen but a 'hard' restart has so far cleared that issue, no reinstalling required - not sure of the cause. 

My current issue with systemd in Utopic Lubuntu is that nm-applet in lxpanel reports no networking and 'Network Manager' is not running. However, my connection is working fine. Booting into Upstart and nm-applet reports correctly. Not had a chance to investigate this further as yet

---

### Post by startas on 2014-08-09
Still, have in mind, that systemd is still not fully adapted for ubuntu, and this is ubuntu development version, so various bugs are normal.

---

### Post by Cavsfan on 2014-08-09
Since we do know that systemd will be released as part of Utopic Unicorn, do we know if it will be the default grub boot option or will there be more than one option?
Or will it be as it is now where you have to modify grub to change it from booting with upstart to systemd?

---

### Post by DogMatix on 2014-08-09
@startas Yes I fully appreciate that systemd is still in testing as far as Ubuntu goes. Although my experience with using it in Debian 'Sid' with  an Openbox DE has been less troubled than with Utopic LXDE. (On the same hardware.)

@Cavsfan I was under the impression systemd wouldn't be default in Utopic, when it is released (I stand to be corrected?). A boot option would be nice though.

---

### Post by Cavsfan on 2014-08-10
> **DogMatix said:**
> @Cavsfan I was under the impression systemd wouldn't be default in Utopic, when it is released (I stand to be corrected?). A boot option would be nice though.

If it is not in the default grub menu at final release then the little addition to grub that I've posted in this thread at least twice :p will probably be the easiest way to get both upstart and systemd as options.
It is not a work around it is simply an addition to grub that will make it appear at the top of the grub menu. Unless you seriously like pressing e on the boot line and entering the necessary stuff every time you boot.

I will go the extra mile to make it easy as pie my own self.

---

### Post by oldos2er on 2014-08-10
Running 14.10 server (with X), systemd enabled in grub, recent updates seem to've fixed the Nvidia-related slowness issues for me (GeForce GT 640).

---

### Post by Cavsfan on 2014-08-12
Now we can check for blame. :p

```
cavsfan@cavsfan-MS-7529:~$ systemd-analyze blame
          4.982s ModemManager.service
          4.795s NetworkManager.service
          4.607s console-setup.service
          4.166s accounts-daemon.service
          3.685s thermald.service
          3.681s avahi-daemon.service
          3.655s systemd-logind.service
          3.547s lightdm.service
          3.477s ufw.service
          3.249s apparmor.service
          3.174s NetworkManager-wait-online.service
          2.159s loadcpufreq.service
          1.829s rsyslog.service
          1.805s networking.service
          1.727s systemd-udev-settle.service
          1.590s systemd-fsck-root.service
          1.308s grub-common.service
          1.216s binfmt-support.service
          1.072s systemd-tmpfiles-setup.service
          1.038s plymouth-read-write.service
           821ms systemd-modules-load.service
           695ms apport.service
           665ms lm-sensors.service
           569ms systemd-udev-trigger.service
           560ms resolvconf.service
           497ms ondemand.service
           476ms plymouth-start.service
           434ms dev-hugepages.mount
           420ms systemd-tmpfiles-setup-dev.service
           411ms upower.service
           410ms kmod-static-nodes.service
           364ms udisks2.service
           363ms dev-mqueue.mount
           351ms systemd-sysctl.service
           350ms polkitd.service
           327ms pppd-dns.service
           324ms saned.service
           294ms whoopsie.service
           285ms systemd-user-sessions.service
           240ms sys-kernel-debug.mount
           214ms systemd-journal-flush.service
           202ms user@111.service
           159ms systemd-update-utmp.service
           126ms colord.service
           116ms kerneloops.service
           110ms dns-clean.service
           110ms speech-dispatcher.service
            95ms proc-sys-fs-binfmt_misc.mount
            77ms rtkit-daemon.service
            74ms alsa-restore.service
            66ms user@1000.service
            64ms systemd-udevd.service
            54ms systemd-random-seed.service
            41ms udev-finish.service
            38ms dev-disk-by\x2duuid-e14dc02e\x2d6ea8\x2d4c95\x2db4d0\x2d9dc04d32294d.swap
            28ms rc-local.service
            24ms pulseaudio.service
            22ms systemd-remount-fs.service
             4ms cpufrequtils.service
             2ms run-lock.mount
             1ms systemd-update-utmp-runlevel.service
             1ms plymouth-quit-wait.service
             1ms run-user.mount
             1ms sys-fs-fuse-connections.mount
             1ms lvm2.service
lines 6-65/65 (END)

```

It seemed a bit faster today after installing the 3.16.0-7-generic kernel.

```
cavsfan@cavsfan-MS-7529:~$ systemd-analyze
Startup finished in 4.352s (kernel) + 16.517s (userspace) = 20.870s
```

I wonder if that time includes the really long time bios takes to find my connected Fantom 1TB USB drive. 
I know if I disconnect that it boots several seconds faster than with it connected.

---

### Post by fjgaude on 2014-08-12
Oh what a night!

```
frank@flash:~$ systemd-analyze blame
          6.404s NetworkManager-wait-online.service
           325ms systemd-udev-settle.service
           273ms vboxdrv.service
           267ms console-setup.service
           130ms NetworkManager.service
           114ms lightdm.service
           100ms ModemManager.service
            84ms accounts-daemon.service
            78ms thermald.service
            78ms avahi-daemon.service
            72ms systemd-logind.service
            69ms systemd-fsck@dev-disk-by\x2dlabel-BAKUP.service
            56ms apparmor.service
            53ms networking.service
            48ms systemd-fsck-root.service
            33ms grub-common.service
            32ms rtkit-daemon.service
            32ms systemd-modules-load.service
            30ms rsyslog.service
            26ms plymouth-start.service
            26ms systemd-udev-trigger.service
            25ms dev-mqueue.mount
            24ms kmod-static-nodes.service
            23ms colord.service
            22ms systemd-sysctl.service
            22ms dev-hugepages.mount
            22ms sys-kernel-debug.mount
            21ms udisks2.service
            20ms kerneloops.service
            18ms binfmt-support.service
            16ms lm-sensors.service
            15ms apport.service
            15ms user@1000.service
            11ms ondemand.service
            10ms plymouth-read-write.service
             9ms wpa_supplicant.service
             9ms polkitd.service
             9ms upower.service
             9ms alsa-restore.service
             9ms ufw.service
             9ms speech-dispatcher.service
             8ms pppd-dns.service
             7ms saned.service
             7ms proc-sys-fs-binfmt_misc.mount
             7ms resolvconf.service
             6ms dns-clean.service
             5ms media-BAKUP.mount
             4ms systemd-tmpfiles-setup-dev.service
             4ms bluetooth.service
             4ms rc-local.service
             4ms systemd-journal-flush.service
             3ms run-user.mount
             2ms systemd-user-sessions.service
             2ms home-database.mount
             2ms pulseaudio.service
             2ms run-lock.mount
             2ms dev-disk-by\x2duuid-4a924204\x2d3b8d\x2d4f6a\x2dbd0a\x2d8d26dd5
             2ms vboxweb-service.service
             2ms vboxballoonctrl-service.service
             1ms systemd-remount-fs.service
             1ms udev-finish.service
             1ms systemd-udevd.service
             1ms systemd-update-utmp-runlevel.service
             1ms whoopsie.service
             1ms systemd-update-utmp.service
             1ms plymouth-quit-wait.service
             1ms systemd-tmpfiles-setup.service
             1ms systemd-backlight@backlight:acpi_video0.service
             1ms systemd-random-seed.service
           931us sys-fs-fuse-connections.mount
           670us vboxautostart-service.service
           519us lvm2.service

frank@flash:~$ systemd-analyze
Startup finished in 1.200s (kernel) + 7.288s (userspace) = 8.488s
```

Oh what a night! The latest update brings things into focus, oh yea! That long wait at first is WiFi... I think direct LAN would be much faster. Will try it later as time permits.

---

### Post by fjgaude on 2014-08-12
Now, without WiFi, just LAN, we have a somewhat different story... does seem that things are changing now with the new kernel. My box quickness is really showing its stuff! <grin>

```
frank@flash:~$ systemd-analyze blame
          3.970s NetworkManager-wait-online.service
           469ms systemd-fsck-root.service
           320ms systemd-udev-settle.service
           276ms vboxdrv.service
           259ms console-setup.service
           136ms NetworkManager.service
           118ms lightdm.service
           105ms ModemManager.service
            90ms accounts-daemon.service
            78ms systemd-logind.service
            77ms avahi-daemon.service
            77ms thermald.service
            51ms apparmor.service
            50ms systemd-fsck@dev-disk-by\x2dlabel-BAKUP.service
            46ms networking.service
            39ms rsyslog.service
            35ms binfmt-support.service
            35ms grub-common.service
            33ms udisks2.service
            30ms systemd-modules-load.service
            30ms rtkit-daemon.service
            25ms plymouth-start.service
            23ms systemd-udev-trigger.service
            22ms dev-mqueue.mount
            21ms kmod-static-nodes.service
            20ms systemd-sysctl.service
            19ms dev-hugepages.mount
            19ms sys-kernel-debug.mount
            18ms lm-sensors.service
            17ms user@1000.service
            13ms apport.service
            12ms ondemand.service
            12ms upower.service
            11ms colord.service
            11ms plymouth-read-write.service
            10ms wpa_supplicant.service
            10ms media-BAKUP.mount
            10ms kerneloops.service
             9ms polkitd.service
             7ms proc-sys-fs-binfmt_misc.mount
             7ms speech-dispatcher.service
             7ms ufw.service
             7ms resolvconf.service
             7ms pppd-dns.service
             7ms alsa-restore.service
             6ms saned.service
             5ms whoopsie.service
             5ms systemd-tmpfiles-setup.service
             5ms dns-clean.service
             5ms systemd-tmpfiles-setup-dev.service
             4ms systemd-user-sessions.service
             4ms bluetooth.service
             3ms systemd-journal-flush.service
             2ms home-database.mount
             2ms pulseaudio.service
             2ms systemd-remount-fs.service
             2ms dev-disk-by\x2duuid-4a924204\x2d3b8d\x2d4f6a\x2dbd0a\x2d8d26dd5
             1ms systemd-backlight@backlight:acpi_video0.service
             1ms systemd-random-seed.service
             1ms systemd-localed.service
             1ms systemd-udevd.service
             1ms run-lock.mount
             1ms systemd-update-utmp.service
             1ms vboxautostart-service.service
             1ms vboxweb-service.service
             1ms vboxballoonctrl-service.service
             1ms rc-local.service
           918us systemd-update-utmp-runlevel.service
           865us run-user.mount
           836us sys-fs-fuse-connections.mount
           676us plymouth-quit-wait.service
           669us udev-finish.service
           558us lvm2.service

frank@flash:~$ systemd-analyze
Startup finished in 885ms (kernel) + 5.025s (userspace) = 5.911s
```

---

### Post by sammiev on 2014-08-12
Booting is faster but I never timed it but it is very noticeable.

My temperatures highs are lower than what I can remember for some time. 

It's a keeper.

---

### Post by craig10x on 2014-08-15
Just curious...systemd is not on by default in 14.04 is it?   I noticed it is installed on my 14.04 (when i check package manager) and i got updates for it today...that is why i was wondering...
Is it supposed to be on by default in 14.10?
And what does it do?  Thanks :D

---

### Post by Elfy on 2014-08-15
No it is not on by default in 14.10, I doubt if it will be in 15.04 either ;)

---

### Post by Cavsfan on 2014-08-15
OK, I suspended it for an hour or more and it woke right up when I moved the mouse.
So, I guess it's good to go here. ;)

---

### Post by craig10x on 2014-08-15
@elfy: LOL...yeah, typical canonical...you know, lightening speed development ;)   thanks...i had a feeling that would be the case :D

---

### Post by Cavsfan on 2014-08-20
I've been booting Utopic with systemd and it has gotten much more stable and better IMO.
Even running Chromium with it's current problems everything is still looking good. 

I managed to be in it for 6 or more hours yesterday. No problems whatsoever. ;)

---

### Post by craig10x on 2014-08-20
I am still curious...what exactly does systemd do? Or supposed to do? ;)

---

### Post by rrnbtter on 2014-08-20
Greetings,

> **craig10x said:**
> I am still curious...what exactly does systemd do? Or supposed to do? ;)

It may quite possibly go beyond any explaination that I can give. However, Systemd is a alternate system handler from Upstart or SysV Init. It handles all calls between the User INPUT (KB, Mouse, USB, BT, etc) including those given by scripts (terminal) and the command line but also processes such as startup and shutdown. Systemd is backward compatible with Upstart and SysV via scripts but may have a whole array of commands that don't interprete over to the other two systems hence a learning curve is going to occur. I have been using SystemD from the first post in this thread and have had no problems other than those related to the Systemd-shim that was causing crashes for a few days until they got all of the compatibility updates out. The shim is supposed to allow a smooth (as possible) transition between the current command set and systemd. It going to be default so it makes no sense to me not to use it, this being the Dev section.

---

### Post by craig10x on 2014-08-20
Thanks....a bit confusing to follow but i think i get it ;) :D

---

### Post by rrnbtter on 2014-08-20
Greetings,
Some think that Canonical is switching to be consistant with the other Linux major players and particularly Daddy Debian. I think however it has more to do with the advantage they will have by not having to maintain their own (Cananical) system (Upstart) nor depending on SysV Init which may be having trouble keeping up with Unity 8 and other asperations. Due to it being used by Redhat and some other majors SystemD getting heavy support and maintainence. There is an element that doesn't like the switch, I suspect the same segment that bemoans the dropping or Gnome1, Grub1, and much of the small platform software and a few of the display softwares that have a lighter footprint. I personally think that Puppy Linux is doing a good job keeping those things alive and is mostly Ubuntu based although I don't know where they go after the next evolution to mir and U8. These are interesting times I think for myself since I like new ideas and love the Unity desktop plus everything else about Ubuntu and where it seem to be trying to go. I'm even willing to put up with an occasional Apport popup and live for the major crash which means a reinstall.

---

### Post by Cavsfan on 2014-08-21
Just got an update to systemd in the updates.

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep systemd
ii  libpam-systemd:amd64                                  208-8ubuntu1                               amd64        system and service manager - PAM module
ii  libsystemd-daemon0:amd64                              208-8ubuntu1                               amd64        systemd utility library
ii  libsystemd-journal0:amd64                             208-8ubuntu1                               amd64        systemd journal utility library
ii  libsystemd-login0:amd64                               208-8ubuntu1                               amd64        systemd login utility library
ii  systemd                                               208-8ubuntu1                               amd64        system and service manager
rc  systemd-services                                      204-5ubuntu20                              amd64        systemd runtime services
ii  systemd-shim                                          7-1                                        amd64        shim for systemd
```

Don't understand the deal with systemd-services though.

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy systemd-services
systemd-services:
  Installed: (none)
  Candidate: (none)
  Version table:
     204-5ubuntu20 0
        100 /var/lib/dpkg/status

```

---

### Post by rrnbtter on 2014-08-21
Greetings,

Systemd services are in /etc/systemd/services. Their names are mostly self descriptive. In addition to the ones that are there, there are many more espcially for the server market. Basically any script called by systemctl would be considered a service, much as the bash script "echo hello world" would be a bash service that commands the console to display the text "hello world". It is a service because it keeps you from having to type it yourself. Systemd scripts are just more advanced than bash scripts in the way that grub2 scripts are more advanced than grub scripts. Probably more appropriate for the server market and the main reason that it was picked up by Redhat, Suse and the like. This could also be influenceing Cananical to make the switch since it is getting a much smaller part of the server market.

---

### Post by Cavsfan on 2014-08-28
Systemd on Utopic Mate 14.10 ==> about 4 seconds faster:

```
cavsfan@cavsfan-MS-7529:~$ systemd-analyze
Startup finished in 4.238s (kernel) + 12.647s (userspace) = 16.886s
```

---

### Post by zika on 2014-09-21
Anyone did this:```
:~$ sudo apt-get install -s systemd-sysv
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ubuntu-minimal upstart ureadahead
The following NEW packages will be installed:
  systemd-sysv
0 upgraded, 1 newly installed, 3 to remove and 4 not upgraded.
Remv ubuntu-minimal [1.325]
Remv ureadahead [0.100.0-16]
Remv upstart [1.13.2-0ubuntu1] [friendly-recovery:amd64 ]
Inst systemd-sysv (208-8ubuntu4 Ubuntu:14.10/utopic [amd64])
Conf systemd-sysv (208-8ubuntu4 Ubuntu:14.10/utopic [amd64])
```...?
If the answer is "yes", what are pro's and what are con's...?
Too much depends still on upstart:```
:~$ sudo apt-get purge -s upstart-bin libupstart1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libunity-core-6.0-9* libupstart1* ubuntu-desktop* unity* unity-lens-applications* unity-services* upstart-bin*
0 upgraded, 0 newly installed, 7 to remove and 4 not upgraded.
Purg ubuntu-desktop [1.325]
Purg unity [7.3.1+14.10.20140915-0ubuntu1]
Purg unity-lens-applications [7.1.0+13.10.20131011-0ubuntu2]
Purg libunity-core-6.0-9 [7.3.1+14.10.20140915-0ubuntu1]
Purg unity-services [7.3.1+14.10.20140915-0ubuntu1]
Purg libupstart1 [1.13.2-0ubuntu1]
Purg upstart-bin [1.13.2-0ubuntu1]
```
New (for me, not per se) machine, (S/H GA-870A) did not want to boot from fresh install of UU so I had to go through TT and I get:```
:~$ systemd-analyze
Failed to issue method call: No such property 'FirmwareTimestampMonotonic'
```Anyone else?
Since this is fresh install I've bit the bullet:```
:~$ sudo apt-get install systemd-sysv
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ubuntu-minimal upstart ureadahead
The following NEW packages will be installed:
  systemd-sysv
0 upgraded, 1 newly installed, 3 to remove and 4 not upgraded.
Need to get 8546 B of archives.
After this operation, 785 kB disk space will be freed.
Do you want to continue? [Y/n] 
Get:1 http://archive.ubuntu.com/ubuntu/ utopic/universe systemd-sysv amd64 208-8ubuntu4 [8546 B]
Fetched 8546 B in 0s (15,3 kB/s)      
(Reading database ... 200677 files and directories currently installed.)
Removing ubuntu-minimal (1.325) ...
Removing ureadahead (0.100.0-16) ...
dpkg: upstart: dependency problems, but removing anyway as you requested:
 friendly-recovery depends on upstart | systemd-sysv; however:
  Package upstart is to be removed.
  Package systemd-sysv is not installed.
Removing upstart (1.13.2-0ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1) ...
Selecting previously unselected package systemd-sysv.
(Reading database ... 200629 files and directories currently installed.)
Preparing to unpack .../systemd-sysv_208-8ubuntu4_amd64.deb ...
Unpacking systemd-sysv (208-8ubuntu4) ...
Processing triggers for man-db (2.6.7.1-1) ...
:~$ sudo apt-get install systemd-sysv
Reading package lists... Done
Building dependency tree       
Reading state information... Done
systemd-sysv is already the newest version.
```... Next boot will show... ;) First, I'll see if I've got recovery mode anymore... ;)

I'm back with (almost) upstart-free install... ;) That was really fast and there were no interference of SystemD and UpStart messages as before... Ups, I forgot to check for recovery mode... Next time I do boot. Only nuisance I've noticed is```
systemd[1]: /etc/mtab is not a symlink or not pointing to /proc/self/mounts. This is not supported anymore. Please make sure to replace this file by a symlink to avoid incorrect or misleading mount(8) output.
```from dmesg... Nothing a simple```
ln -s /proc/self/mounts /etc/mtab
```could not solve, I suppose. It seems to work. Will dig deeper.

```
systemd-+-ModemManager-+-{gdbus}
        |              `-{gmain}
        |-NetworkManager-+-dhclient
        |                |-dnsmasq
        |                |-{NetworkManager}
        |                |-{gdbus}
        |                `-{gmain}
        |-accounts-daemon-+-{gdbus}
        |                 `-{gmain}
        |-agetty
        |-avahi-daemon---avahi-daemon
        |-colord-+-{gdbus}
        |        `-{gmain}
        |-cron
        |-cups-browsed
        |-dbus-daemon
        |-irqbalance
        |-kerneloops
        |-lightdm-+-Xorg---{Xorg}
        |         |-lightdm-+-upstart-+-at-spi-bus-laun-+-dbus-daemon
        |         |         |         |                 |-{dconf worker}
        |         |         |         |                 |-{gdbus}
        |         |         |         |                 `-{gmain}
        |         |         |         |-at-spi2-registr---{gdbus}
        |         |         |         |-bamfdaemon-+-{dconf worker}
        |         |         |         |            |-{gdbus}
        |         |         |         |            `-{gmain}
        |         |         |         |-compiz-+-{compiz}
        |         |         |         |        |-{dconf worker}
        |         |         |         |        |-{gdbus}
        |         |         |         |        |-{gmain}
        |         |         |         |        `-4*[{pool}]
        |         |         |         |-dbus-daemon
        |         |         |         |-dconf-service-+-{gdbus}
        |         |         |         |               `-{gmain}
        |         |         |         |-evolution-calen-+-{dconf worker}
        |         |         |         |                 |-{evolution-calen}
        |         |         |         |                 |-{gdbus}
        |         |         |         |                 |-{gmain}
        |         |         |         |                 `-{pool}
        |         |         |         |-evolution-sourc-+-{gdbus}
        |         |         |         |                 `-{gmain}
        |         |         |         |-firefox-+-plugin-containe-+-{Chrome_ChildThr}
        |         |         |         |         |                 |-{dconf worker}
        |         |         |         |         |                 |-{gdbus}
        |         |         |         |         |                 |-9*[{plugin-containe}]
        |         |         |         |         |                 `-{threaded-ml}
        |         |         |         |         |-4*[{Analysis Helper}]
        |         |         |         |         |-{Cache I/O}
        |         |         |         |         |-{Cache2 I/O}
        |         |         |         |         |-{Cert Verify}
        |         |         |         |         |-{DNS Resolver #1}
        |         |         |         |         |-{DNS Resolver #5}
        |         |         |         |         |-3*[{DOM Worker}]
        |         |         |         |         |-{Gecko_IOThread}
        |         |         |         |         |-{HTML5 Parser}
        |         |         |         |         |-{Hang Monitor}
        |         |         |         |         |-{Image Scaler}
        |         |         |         |         |-{ImageDecoder #4}
        |         |         |         |         |-{ImageDecoder #5}
        |         |         |         |         |-{ImageDecoder #6}
        |         |         |         |         |-{JS Watchdog}
        |         |         |         |         |-{MediaManager}
        |         |         |         |         |-{Net Predictor}
        |         |         |         |         |-{Proxy R~olution}
        |         |         |         |         |-{Socket Thread}
        |         |         |         |         |-{Timer}
        |         |         |         |         |-{URL Classifier}
        |         |         |         |         |-{dconf worker}
        |         |         |         |         |-{firefox}
        |         |         |         |         |-{gdbus}
        |         |         |         |         |-{gmain}
        |         |         |         |         |-{localStorage DB}
        |         |         |         |         |-{mozStorage #1}
        |         |         |         |         |-{mozStorage #2}
        |         |         |         |         |-{mozStorage #3}
        |         |         |         |         |-{mozStorage #4}
        |         |         |         |         |-{mozStorage #5}
        |         |         |         |         |-{mozStorage #6}
        |         |         |         |         |-{mozStorage #7}
        |         |         |         |         |-{mozStorage #8}
        |         |         |         |         `-{mozStorage #9}
        |         |         |         |-gconfd-2
        |         |         |         |-gnome-keyring-d-+-{dconf worker}
        |         |         |         |                 |-{gdbus}
        |         |         |         |                 |-{gnome-keyring-d}
        |         |         |         |                 `-{timer}
        |         |         |         |-gnome-session-+-deja-dup-monito-+-{dconf worker}
        |         |         |         |               |                 `-{gdbus}
        |         |         |         |               |-nautilus-+-{dconf worker}
        |         |         |         |               |          |-{gdbus}
        |         |         |         |               |          `-{gmain}
        |         |         |         |               |-nm-applet-+-{dconf worker}
        |         |         |         |               |           `-{gdbus}
        |         |         |         |               |-polkit-gnome-au-+-{dconf worker}
        |         |         |         |               |                 `-{gdbus}
        |         |         |         |               |-telepathy-indic-+-{dconf worker}
        |         |         |         |               |                 `-{gdbus}
        |         |         |         |               |-unity-fallback--+-{dconf worker}
        |         |         |         |               |                 `-{gdbus}
        |         |         |         |               |-update-notifier-+-{dconf worker}
        |         |         |         |               |                 |-{gdbus}
        |         |         |         |               |                 `-{gmain}
        |         |         |         |               |-zeitgeist-datah-+-{gdbus}
        |         |         |         |               |                 |-{gmain}
        |         |         |         |               |                 `-4*[{pool}]
        |         |         |         |               |-{dconf worker}
        |         |         |         |               |-{gdbus}
        |         |         |         |               `-{gmain}
        |         |         |         |-gnome-terminal-+-bash---pstree
        |         |         |         |                |-gnome-pty-helpe
        |         |         |         |                |-{dconf worker}
        |         |         |         |                |-{gdbus}
        |         |         |         |                `-{gmain}
        |         |         |         |-gvfs-afc-volume-+-{gdbus}
        |         |         |         |                 `-{gvfs-afc-volume}
        |         |         |         |-gvfs-gphoto2-vo---{gdbus}
        |         |         |         |-gvfs-mtp-volume---{gdbus}
        |         |         |         |-gvfs-udisks2-vo-+-{gdbus}
        |         |         |         |                 `-{gmain}
        |         |         |         |-gvfsd---{gdbus}
        |         |         |         |-gvfsd-burn---{gdbus}
        |         |         |         |-gvfsd-fuse-+-{gdbus}
        |         |         |         |            |-{gvfs-fuse-sub}
        |         |         |         |            `-2*[{gvfsd-fuse}]
        |         |         |         |-gvfsd-trash-+-{gdbus}
        |         |         |         |             `-{gmain}
        |         |         |         |-hud-service-+-{dconf worker}
        |         |         |         |             |-{gdbus}
        |         |         |         |             `-{gmain}
        |         |         |         |-ibus-daemon-+-ibus-dconf-+-{dconf worker}
        |         |         |         |             |            |-{gdbus}
        |         |         |         |             |            `-{gmain}
        |         |         |         |             |-ibus-engine-sim-+-{gdbus}
        |         |         |         |             |                 `-{gmain}
        |         |         |         |             |-ibus-ui-gtk3-+-{dconf worker}
        |         |         |         |             |              |-{gdbus}
        |         |         |         |             |              `-{gmain}
        |         |         |         |             |-{gdbus}
        |         |         |         |             `-{gmain}
        |         |         |         |-ibus-x11-+-{dconf worker}
        |         |         |         |          |-{gdbus}
        |         |         |         |          `-{gmain}
        |         |         |         |-indicator-appli---{gdbus}
        |         |         |         |-indicator-bluet-+-{dconf worker}
        |         |         |         |                 `-{gdbus}
        |         |         |         |-indicator-datet-+-{cal-client-dbus}
        |         |         |         |                 |-{dconf worker}
        |         |         |         |                 |-{gdbus}
        |         |         |         |                 |-{gmain}
        |         |         |         |                 `-{pool}
        |         |         |         |-indicator-keybo-+-{dconf worker}
        |         |         |         |                 `-{gdbus}
        |         |         |         |-indicator-messa-+-{dconf worker}
        |         |         |         |                 |-{gdbus}
        |         |         |         |                 `-{gmain}
        |         |         |         |-indicator-power-+-{dconf worker}
        |         |         |         |                 `-{gdbus}
        |         |         |         |-indicator-print-+-{dconf worker}
        |         |         |         |                 `-{gdbus}
        |         |         |         |-indicator-sessi-+-{dconf worker}
        |         |         |         |                 `-{gdbus}
        |         |         |         |-indicator-sound-+-{dconf worker}
        |         |         |         |                 |-{gdbus}
        |         |         |         |                 `-{gmain}
        |         |         |         |-mission-control-+-{dconf worker}
        |         |         |         |                 `-{gdbus}
        |         |         |         |-notify-osd-+-{dconf worker}
        |         |         |         |            `-{gdbus}
        |         |         |         |-oneconf-service-+-{dconf worker}
        |         |         |         |                 |-{gdbus}
        |         |         |         |                 `-{gmain}
        |         |         |         |-pulseaudio-+-{alsa-sink-ALC89}
        |         |         |         |            |-{alsa-sink-HDMI }
        |         |         |         |            `-{alsa-source-ALC}
        |         |         |         |-unity-panel-ser-+-{dconf worker}
        |         |         |         |                 `-{gdbus}
        |         |         |         |-unity-scope-loa-+-{dconf worker}
        |         |         |         |                 |-{gdbus}
        |         |         |         |                 `-{gmain}
        |         |         |         |-unity-settings--+-{dconf worker}
        |         |         |         |                 |-{gdbus}
        |         |         |         |                 `-{gmain}
        |         |         |         |-unity-webapps-s-+-{dconf worker}
        |         |         |         |                 `-{gdbus}
        |         |         |         |-2*[upstart-dbus-br]
        |         |         |         |-upstart-event-b
        |         |         |         |-upstart-file-br
        |         |         |         |-window-stack-br
        |         |         |         |-zeitgeist-daemo---{gdbus}
        |         |         |         `-zeitgeist-fts-+-cat
        |         |         |                         |-{gdbus}
        |         |         |                         `-{gmain}
        |         |         `-{gdbus}
        |         |-{gdbus}
        |         `-{gmain}
        |-polkitd-+-{gdbus}
        |         `-{gmain}
        |-preload
        |-rsyslogd-+-{in:imklog}
        |          |-{in:imuxsock}
        |          `-{rs:main Q:Reg}
        |-rtkit-daemon---2*[{rtkit-daemon}]
        |-systemd---(sd-pam)
        |-systemd-journal
        |-systemd-logind
        |-systemd-udevd
        |-udisksd-+-{cleanup}
        |         |-{gdbus}
        |         |-{gmain}
        |         `-{probing-thread}
        |-upowerd-+-{gdbus}
        |         `-{gmain}
        `-whoopsie-+-{gdbus}
                   `-{gmain}
```

Update&#8321;: Just one more glitch:```
[    8.025206] systemd[1]: [/lib/systemd/system/friendly-recovery.service:14] Executable path is not absolute, ignoring: dmesg --console-off
```

---

### Post by zika on 2014-10-10
After using SystemD for a while in Utopic on my „main“ machine I found it very good and nicely to control. Just grasping its syntax and it works like a charm.
I wrote about „text“ not honored in kernel boot line```
systemctl set-default multi-user.target
```is its equaivalent.
To kill DM (stop GUI)(go to level 3)```
systemctl isolate multi-user.target
```and to start GUI again(got to level 5)```
systemctl isolate graphical.target
```To prevent service from starting```
systemctl disable name_of_the.service
```or equivalent of .override file (containing „manual“) in /etc/init```
systemctl mask name_of_the.service
```To enable readahead (if You're using preload, and ven if You're not) try this, You might be surprised, no guarantee and nothing promised)```
systemctl enable systemd-readahead-collect.service
systemctl enable systemd-readahead-replay.service
```and many other nice things. Not to mention known stuff with stop, start etc.
Very nice indeed.
Update&#8321;: This is all used with upstart completely removed and systemd-sysv installed (ubuntu-minial, ureadahead and upstart removed, libupstart1 and upstart-bin still retained due to dependency of Unity and ubuntu-desktop upon them).
Update&#8322;: For those used to old stuff, [here]("https://fedoraproject.org/wiki/SysVinit_to_Systemd_Cheatsheet") is a nice list I've found today.
Update&#8323;: Caveat: When using```
systemctl set-default multi-user.target
```on one Intel laptop I got stuck on black screen on boot. Solution was to go to recovery mode, root shell, and issue```
systemctl set-default graphical.target
```and all was back and OK. So, that's learning curve for me. ;)

---

### Post by zika on 2014-10-18
> **Elfy said:**
> If you've not _specifically_ edited grub (either at boot or by editing /etc/default/grub) then you will be booting with upstart. You can only boot with systemd by making changes.With &#8222;clean&#8220; grub file I've been booting in SystemD (looking at messages that either scroll in front of me or in log-file(s)) even before I've purged UPStart from install. Only remnant (now) of UPStart:```
:~$ dpkg -l|grep upstart
ii  libupstart1:amd64                                     1.13.2-0ubuntu2
                            amd64        Upstart Client Library
ii  upstart-bin                                           1.13.2-0ubuntu2
                            amd64        event-based init daemon - essential binaries
```

---

### Post by Elfy on 2014-10-18
> **SpUpUz said:**
> how do i boot with upstart?

That's what this thread 'hijack' is about :)

> **ventrical said:**
> Read this first..

[http://askubuntu.com/questions/420917/how-can-i-replace-upstart-with-systemd](http://askubuntu.com/questions/420917/how-can-i-replace-upstart-with-systemd)

Not about replacing upstart with systemd

Regards..

> **zika said:**
> With „clean“ grub file I've been booting in SystemD (looking at messages that either scroll in front of me or in log-file(s)) even before I've purged UPStart from install. Only remnant (now) of UPStart:```
:~$ dpkg -l|grep upstart
ii  libupstart1:amd64                                     1.13.2-0ubuntu2
                            amd64        Upstart Client Library
ii  upstart-bin                                           1.13.2-0ubuntu2
                            amd64        event-based init daemon - essential binaries
```

Nor this.

_The long and short of it is - if you do NOTHING to a default *buntu installation - you boot upstart NOT systemd. _

---

### Post by zika on 2014-10-18
> **Elfy said:**
> _The long and short of it is - if you do NOTHING to a default *buntu installation - you boot upstart NOT systemd. _I've installed yesterday 14.10 daily on laptop (among others mine at workplace of mine) and... SystemD as far as I remember. Vanilla, first boot. I might be wrong, too fast in removing remnants of UPStart, but...
I'll check monday on next candidate for install.> **Elfy said:**
> That's what this thread 'hijack' is aboutSorry, I did not notice change of person asking question(s). I was focused on the question per se and (as usual) not on the person posting it. Mea culpa.

---

### Post by Elfy on 2014-10-18
systemd packages are installed - as we all know, but systemd isn't being used - systemd-analyze shows that

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=257323&d=1413634217[/IMG]

I'm not that concerned about thread content in here, just more concerned that the user asking how to boot with upstart doesn't get confused by all the trees in the wood ;)

The answer to their query is as I said :)

As long as you don't do anything to make an install boot with systemd - you aren't (at least not yet for anyone coming here during 15.04 or 15.10 or 16.04 :P )

---

### Post by zika on 2014-10-18
```
:~$ systemd-analyze Startup finished in 4.465s (kernel) + 18.483s (userspace) = 22.948s
:~$ dpkg -l systemd*Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                  Version                         Architecture                    Description
+++-=====================================================-===============================-===============================-===============================================================================================================
ii  systemd                                               208-8ubuntu8                    amd64                           system and service manager
ii  systemd-gui                                           1:3-2                           all                             transitional package for systemd-ui
rc  systemd-services                                      204-5ubuntu20.7                 amd64                           systemd runtime services
ii  systemd-shim                                          8-1                             amd64                           shim for systemd
ii  systemd-sysv                                          208-8ubuntu8                    amd64                           system and service manager - SysV links
ii  systemd-ui                                            3-2                             amd64                           graphical frontend for systemd

```New time(s) coming, pictures of Terminal... ;) systemd-service is virtual (dummy) package that is depreciated.
Yes, I did install systemd-sysv and purged upstart (in different order, of course) so I might be mislead i.e. I did not pay enough attention on first boot. What I'm sure is that it is SystemD (now) runing by default as it is the only candidate here. ;)
[Over&out]("http://www.linux.com/learn/tutorials/527639-managing-services-on-linux-with-systemd") :-\"
Update&#8321;: Forgot```
:~$ cat /etc/default/grub|grep LINUX_DEFAULT
GRUB_CMDLINE_LINUX_DEFAULT=""
``` OK, that might be because I've cleaned machine(s) from UpStart...

---

### Post by Elfy on 2014-10-18
> **zika said:**
> ```
:~$ systemd-analyze Startup finished in 4.465s (kernel) + 18.483s (userspace) = 22.948s
:~$ dpkg -l systemd*Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                  Version                         Architecture                    Description
+++-=====================================================-===============================-===============================-===============================================================================================================
ii  systemd                                               208-8ubuntu8                    amd64                           system and service manager
ii  systemd-gui                                           1:3-2                           all                             transitional package for systemd-ui
rc  systemd-services                                      204-5ubuntu20.7                 amd64                           systemd runtime services
ii  systemd-shim                                          8-1                             amd64                           shim for systemd
ii  systemd-sysv                                          208-8ubuntu8                    amd64                           system and service manager - SysV links
ii  systemd-ui                                            3-2                             amd64                           graphical frontend for systemd

```New time(s) coming, pictures of Terminal... ;) systemd-service is virtual (dummy) package that is depreciated.
Yes, I did install systemd-sysv and purged upstart (in different order, of course) so I might be mislead i.e. I did not pay enough attention on first boot. What I'm sure is that it is SystemD (now) runing by default as it is the only candidate here. ;)
[Over&out]("http://www.linux.com/learn/tutorials/527639-managing-services-on-linux-with-systemd") :-\"

I'm talking about a default install zika :)

Because I am as positive that systemd is NOT running from a vanilla install ;)

No need to over and out anything at all - we can always (at least I can) move posts to a new thread - probably a useful conversation to have 
given that *eventually* systemd will be default ...

---

### Post by zika on 2014-10-18
> **Elfy said:**
> I'm talking about a default install zika :)
Because I am as positive that systemd is NOT running from a vanilla install ;)So was I but I'm, as I wrote twice, not sure if I did purge UpStart during that first uptime of that machine. Not sure if I watched first boot screen or was there splash to cloud my perception. To many machines installed in last few days/weeks. Luckily all with 14.10 despite some serious boot and install obstacles/hurdles to be jumpd over. But, nice experience and something new learned. I hope that is not due to early dementia that I do perceive some of that as learning... ;)
> **Elfy said:**
> No need to over and out anything at all - we can always (at least I can) move posts to a new thread - probably a useful conversation to have given that *eventually* systemd will be default ...If I were moderating I would merge split from here with [http://ubuntuforums.org/showthread.php?t=2224798](http://ubuntuforums.org/showthread.php?t=2224798). I was just running from/out_of hijack-off-topic situation, nothing more and nothing less. ;)

---

### Post by ventrical on 2014-10-18
> **Elfy said:**
> 

Because I am as positive that systemd is NOT running from a vanilla install ;)



That's been the case here from day one. Early on I had thought it would be installed by default. Even Ubuntu-Desktop-next does not have systemd installed by default (but the packets are there).

---

### Post by Elfy on 2014-10-18
> **zika said:**
> ...
If I were moderating I would merge split from here with [http://ubuntuforums.org/showthread.php?t=2224798](http://ubuntuforums.org/showthread.php?t=2224798). I was just running from/out_of hijack-off-topic situation, nothing more and nothing less. ;)

worked for me - some comments seem a little odd as they refer to [http://ubuntuforums.org/showthread.php?t=2247949](http://ubuntuforums.org/showthread.php?t=2247949) but hey ho

---

### Post by zika on 2014-10-18
> **Elfy said:**
> hey hoDitto ;)

---

### Post by ventrical on 2014-10-18
> **zika said:**
> In these &#8222;two more ways&#8220; there is not any change in /atc/default/grub needed as I've written in a thread mentioned. Change back, as I wrote is a &#8222;simple&#8220; (mind the caveat I explained) purge of systemd-sysv or install of upstart since devs have done a good job and those two simply do not coexist together but do ask for other one when removed.

Ok.. thank you . I have an extra system that I am going to try and experiment with that method on. I'll leave my results in that systemd appropiate forum.

 I installed 

```

systemd-sysv

```

and it auto removed upstart. I
```

sudo apt-get purge upstart

```

 just because.

  I edit the grub file at /etc/default/grub and restored it back to quiet splash.

```

Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  upstart
Suggested packages:
  graphviz upstart-monitor
The following packages will be REMOVED:
  systemd-sysv
The following NEW packages will be installed:
  upstart
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 0 B/111 kB of archives.
After this operation, 574 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg: systemd-sysv: dependency problems, but removing anyway as you requested:
 friendly-recovery depends on upstart | systemd-sysv; however:
  Package upstart is not installed.
  Package systemd-sysv is to be removed.

(Reading database ... 537891 files and directories currently installed.)
Removing systemd-sysv (208-8ubuntu8) ...
Processing triggers for man-db (2.7.0.2-2) ...
Selecting previously unselected package upstart.
(Reading database ... 537875 files and directories currently installed.)
Preparing to unpack .../upstart_1.13.2-0ubuntu2_i386.deb ...
Unpacking upstart (1.13.2-0ubuntu2) ...
Processing triggers for man-db (2.7.0.2-2) ...
Processing triggers for dbus (1.8.8-1ubuntu2) ...
Setting up upstart (1.13.2-0ubuntu2) ...
Processing triggers for dbus (1.8.8-1ubuntu2) ...
ventrical@ventrical-desktop:~$ 

```

and you are right about devs doing good job.

edit

 The only caveat is that I had to edit out,

```

init=/lib/systemd/systemd

```

from grub menu. So it is very well automated.

---

### Post by Cavsfan on 2014-10-18
I have been booting exclusively with systemd for the most part.
```
cavsfan@cavsfan-MS-7529:~$ systemd-analyze
Startup finished in 4.485s (kernel) + 19.217s (userspace) = 23.703s
```
```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep systemd
ii  libpam-systemd:amd64                                  208-8ubuntu8                               amd64        system and service manager - PAM module
ii  libsystemd-daemon0:amd64                              208-8ubuntu8                               amd64        systemd utility library
ii  libsystemd-journal0:amd64                             208-8ubuntu8                               amd64        systemd journal utility library
ii  libsystemd-login0:amd64                               208-8ubuntu8                               amd64        systemd login utility library
ii  systemd                                               208-8ubuntu8                               amd64        system and service manager
rc  systemd-services                                      204-5ubuntu20                              amd64        systemd runtime services
ii  systemd-shim                                          8-1                                        amd64        shim for systemd
```

I guess that is how I stumbled upon that bug about systemd getting the time 4 hours behind for US EST.
I just happened to boot with upstart and the time was right. Then I seen the bug fix was just for upstart.

---

### Post by zika on 2014-10-18
> **Cavsfan said:**
> I guess that is how I stumbled upon that bug about systemd getting the time 4 hours behind for US EST.
I just happened to boot with upstart and the time was right. Then I seen the bug fix was just for upstart.Comes Monday I will probably be another brick in that wall since laptop I've installed 14.10 on Friday (alongside Windows, just for testing, Windows will be erased no later that Tuesday) exibits the same behavior. Main reason why I did not erase Windows is to test thsi time conundrum. Yes, it jumps two hours (|UTC-MyTime|=2) on every boot or something like that, did not have enough time to investigate that yesterday. Ideal platform to check my suggestion on UTC switch etc. Stay tuned. ;) In proper thread, of course, just finishing off-topic here.

---

### Post by Cavsfan on 2014-10-19
Anyone running Utopic with systemd experiencing the 4 hour behind time problem sign on to this bug if it affects you.

[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/1382208](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/1382208)

It was fixed for Upstart but remains broken in systemd.

---

### Post by Elfy on 2014-10-24
Snip from a -release e-mail
> 
 - Steady progress on the systemd transition, with a goal to
   switch over in the first half of the cycle.

---

### Post by Cavsfan on 2014-10-24
> **Elfy said:**
> Snip from a -release e-mail

> - Steady progress on the systemd transition, with a goal to
   switch over in the first half of the cycle.                      

Do you mean in Utopic Unicorn or Vivid Vervet systemd will become the default?

---

### Post by Elfy on 2014-10-24
ummm ... half way through the utopic cycle was about June ;)

---

### Post by rrnbtter on 2014-10-24
Greetings,
I have been running Systemd since the first post in this thread and I have never had a problem with my time function.  Neither with Systemd nor Upstart. I have used Systemd most of the duration except for the few days that Systemd-shim was causing problems. FYI

---

### Post by Cavsfan on 2014-10-24
> **Elfy said:**
> ummm ... half way through the utopic cycle was about June ;)

Hehe! :lol: Oh you meant developmental cycle? I thought you meant life cycle. That's a good thing as I put both options - Upstart and Systemd boot in my custom grub wiki.

> **rrnbtter said:**
> Greetings,
I have been running Systemd since the first post in this thread and I have never had a problem with my time function.  Neither with Systemd nor Upstart. I have used Systemd most of the duration except for the few days that Systemd-shim was causing problems. FYI

You're not in US Eastern Standard Time then are you? :)

---

### Post by rrnbtter on 2014-10-24
Greetings,

> **Cavsfan said:**
>  You're not in US Eastern Standard Time then are you?  

Sure am!  If that time zone is excluded from the problem..... Sorry I missed your memo! :)  Guess I can close that chapter.

---

### Post by Cavsfan on 2014-10-24
> **rrnbtter said:**
> Greetings,

[QUOTE=Cavsfan;13150961]You're not in US Eastern Standard Time then are you? :smile:

Sure am!  If that time zone is excluded from the problem..... Sorry I missed your memo! :)  Guess I can close that chapter.[/QUOTE]

I just booted Utopic Mate with systemd and it displayed that systemd-fsck detected a 4 hour time difference and fixed it. 
So, apparently it is fixed. Good deal! I'll go back to using systemd exclusively myself. :)

I remember EST being symlinked to another file when that problem initially occurred but can't find anything about it now. Oh well...

---

### Post by rrnbtter on 2014-10-24
Greetings,
@cavsfan, we just got a new systemd-shim in the downstream which could be the source of the fix. I've been getting continous updates which makes this interesting.

---

### Post by harry332 on 2014-10-25
Interested to know how many of you have already upgraded your setup with the new systemd (v. 215).
Compared to the old one a new libsystemd0 has been introduced, while the rest of the libsystemd-* libraries are deprecated.
These are now transitional packages because other packages (like dbus, pulseaudio and policykit-1) still depend on them.

Systemd 215 is in the Vivid proposed repo now.

I use solely systemd: with systemd-sysv installed and upstart, cgmanager, libcgmanager0 and systemd-shim purged.

---

### Post by zika on 2014-10-25
> **harry332 said:**
> Interested to know how many of you have already upgraded your setup with the new systemd (v. 215).
Compared to the old one a new libsystemd0 has been introduced, while the rest of the libsystemd-* libraries are deprecated.
These are now transitional packages because other packages (like dbus, pulseaudio and policykit-1) still depend on them.
Systemd 215 is in the Vivid proposed repo now.
I use solely systemd: with systemd-sysv installed and upstart, cgmanager, libcgmanager0 and systemd-shim purged.No UpStart here also but```
:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  indicator-datetime systemd-shim ubuntu-desktop unity-control-center unity-control-center-signon webaccounts-extension-common xul-ext-webaccounts
The following NEW packages will be installed:
  libsystemd0
The following packages will be upgraded:
  libpam-systemd libsystemd-daemon0 libsystemd-journal0 libsystemd-login0 libudev1 systemd systemd-sysv udev
8 upgraded, 1 newly installed, 7 to remove and 0 not upgraded.
Need to get 0 B/3657 kB of archives.
After this operation, 1365 kB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.
``````
libpam-systemd (208-8ubuntu8 => 215-5ubuntu1)
libsystemd-daemon0 (208-8ubuntu8 => 215-5ubuntu1)
libsystemd-journal0 (208-8ubuntu8 => 215-5ubuntu1)
libsystemd-login0 (208-8ubuntu8 => 215-5ubuntu1)
libudev1 (208-8ubuntu8 => 215-5ubuntu1)
systemd (208-8ubuntu8 => 215-5ubuntu1)
systemd-sysv (208-8ubuntu8 => 215-5ubuntu1)
udev (208-8ubuntu8 => 215-5ubuntu1)
```a bit too much stuff to purge at this moment. It almost got me this morning, I've accepted dist-upgrade, aforementioned stuff was purged, but I managed to get it back before trouble could peak its head... ;)
Waiting for fog to clear, hopefully soon.In the meantime I've found a bit of nice reading, just to clear what is going on: [http://ralph.soika.com/debian-jessie-systemd-shim/](http://ralph.soika.com/debian-jessie-systemd-shim/)

---

### Post by harry332 on 2014-10-25
> **zika said:**
> 
... ...
Waiting for fog to clear, hopefully soon.In the meantime I've found a bit of nice reading, just to clear what is going on: [http://ralph.soika.com/debian-jessie-systemd-shim/](http://ralph.soika.com/debian-jessie-systemd-shim/)

Right, the new systemd 215 will remove systemd-shim, which, after all was created because of upstart. Systemd does not use it.
However, if you already have removed upstart, you do not need systemd-shim either.
Just check that you have init=/lib/systemd/systemd in your kernel line.

Somebody told me that one can use the kernel line or systemd-sysv, but that both is not needed.
Well, if I remove the kernel line and have systemd-sysv installed, I do still get a kernel panic.
So at least my set up needs the kernel line there.

But about your link (ralph soika).
In my opinion gnome-shell does certainly not need systemd-shim, and at least in Ubuntu does not depend on it.

---

### Post by Elfy on 2014-10-25
Wondering if perhaps we might be better closing this thread and renaming it then starting a new one given that we're expecting systemd to land as default mid-cycle. It's likely to get unwieldy ...

---

### Post by zika on 2014-10-25
> **harry332 said:**
> Right, the new systemd 215 will remove systemd-shim, which, after all was created because of upstart. Systemd does not use it.
However, if you already have removed upstart, you do not need systemd-shim either.
Just check that you have init=/lib/systemd/systemd in your kernel line.No, for weeks, now. UpStartfree and fully (as possible, of course) SystemD set.
About systemd:shim, I know I do not need it but I need some of those packages that would be purgedif I would upgrade to 21, that is all I'm writing.
```
[COLOR=#000000][FONT=Ubuntu Mono]indicator-datetime systemd-shim ubuntu-desktop unity-control-center unity-control-center-signon webaccounts-extension-common xul-ext-webaccounts[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]Just because of that I do wait.

> **harry332 said:**
> Somebody told me that one can use the kernel line or systemd-sysv, but that both is not needed.
Well, if I remove the kernel line and have systemd-sysv installed, I do still get a kernel panic.
So at least my set up needs the kernel line there.I'm happy for quite some time with no-kernel line intervention and SystemD booting intself. Fast and nice.

> **harry332 said:**
> But about your link (ralph soika).
In my opinion gnome-shell does certainly not need systemd-shim, and at least in Ubuntu does not depend on it.I was not concerned (and still am not) with GS but it just helped me to put pieces together in this slow Saturday morning, noon or even afternoon now. Shopping, etc.

---

### Post by harry332 on 2014-10-25
> **zika said:**
> No, for weeks, now. UpStartfree and fully (as possible, of course) SystemD set.
About systemd:shim, I know I do not need it but I need some of those packages that would be purgedif I would upgrade to 21, that is all I'm writing.
```
[COLOR=#000000][FONT=Ubuntu Mono]indicator-datetime systemd-shim ubuntu-desktop unity-control-center unity-control-center-signon webaccounts-extension-common xul-ext-webaccounts[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]Just because of that I do wait.

I'm happy for quite some time with no-kernel line intervention and SystemD booting intself. Fast and nice.

I was not concerned (and still am not) with GS but it just helped me to put pieces together in this slow Saturday morning, noon or even afternoon now. Shopping, etc.

Sure, there are packages that cannot cope with systemd-sysv, and thus they need systemd-shim.
Note, that if you do not have the "init=/lib/systemd/systemd" kernel line and you do not have systemd-sysv installed, you are not fully using systemd, but instead, you are using sysvinit. You are actually booting with sysvinit.
You see installing systemd-sysv (and removing systemd-shim) "provides the links needed for systemd to replace sysvinit. Installing systemd-sysv will overwrite /sbin/init with a link to systemd."
But like you said, you need to wait because of other packages.

---

### Post by Cavsfan on 2014-10-25
> **rrnbtter said:**
> Greetings,
@cavsfan, we just got a new systemd-shim in the downstream which could be the source of the fix. I've been getting continous updates which makes this interesting.

I didn't notice that update but when I boot with systemd it shows that systend-fcsk (I believe that is the correct name) detects that the time is off by 4 hours possibly due to a BIOS setting and it says "corrected".

But, I just looked up and noticed the time shows to be off (behind) by 4 hours). This is after the 2nd boot. The first was with Upstart and the 2nd was with Systemd.

Hmmm... So, I don't know what is going on. It appeared to be fixed before.

This is in Utopic Mate after a fresh install from a final release ISO.

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep systemd
ii  libpam-systemd:amd64                        208-8ubuntu8                             amd64        system and service manager - PAM module
ii  libsystemd-daemon0:amd64                    208-8ubuntu8                             amd64        systemd utility library
ii  libsystemd-journal0:amd64                   208-8ubuntu8                             amd64        systemd journal utility library
ii  libsystemd-login0:amd64                     208-8ubuntu8                             amd64        systemd login utility library
ii  systemd                                     208-8ubuntu8                             amd64        system and service manager
ii  systemd-shim                                8-1                                      amd64        shim for systemd
```

---

### Post by Cavsfan on 2014-10-25
> **Elfy said:**
> Wondering if perhaps we might be better closing this thread and renaming it then starting a new one given that we're expecting systemd to land as default mid-cycle. It's likely to get unwieldy ...

Moving it would be a good idea out of the Vivid Vervet discussions as it pertains to Utopic as well. It's up to you though. :)

I booted a 3rd time (1st upstart, 2nd systemd and 3rd systemd) and the time is still off (behind) by 4 hours. I don't understand. :confused:

---

### Post by Cavsfan on 2014-10-25
I'm pretty sure it's still broken.

The changelog does not show a fix:

> systemd-shim (8-1) unstable; urgency=medium

  * Update watch file.
  * New upstream release.
    - Drop patches cherry-picked from upstream.
  * Add versioned dependency on cgmanager (>= 0.32) for new APIs.

 -- Steve Langasek <vorlon@debian.org>  Wed, 10 Sep 2014 15:51:34 +0000

Nor does the bug I filed: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/1382208](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/1382208)

---

### Post by cariboo on 2014-10-25
+1 to starting a new thread, seeing as we are now using Vivid. There is some good information i this thread, but if we keep it going as it is now, some the information may just get lost in all the noise.

---

### Post by Elfy on 2014-10-25
works for me :p

---

