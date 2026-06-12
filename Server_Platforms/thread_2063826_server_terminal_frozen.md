---
title: "server terminal frozen"
date: 2012-09-27
forum: Server Platforms
---

### Post by sona1111 on 2012-09-27
hello, i am running ubuntu server and the terminal has frozen except for blinking cursor after an error "usb 1-2: device descriptor read/64, error -71". I have tried ctrl q and c the ALT+printscreen REISUB with no success.  the server still works normally in the background, and i can log in and use it normally via SSH. is their a way to unfreeze the terminal?

(also of note is that the error is not understandable to me as the server has no usb devices at all, unless its talking about another usb here)

---

### Post by sona1111 on 2012-09-28
bump

---

### Post by Habitual on 2012-09-29
"the terminal has frozen except for blinking cursor" on bootup or after logging in graphically? It is **very** important for us to have the correct answer.

How did this get frozen? On bootup, or did you run a command after logging in? You said "terminal" but it is a common mistake calling it 'terminal' when it is the console, did you actually boot into a graphical desktop?

If you ran a command then you *could* login via ssh and kill that command.
For example. if you ran a command, then in a new terminal on the server, run

```
pidof -x command
``` and get the PID. Then 
```
kill pid_of_command
```If it is a bash script that you ran, then
```
killall -9 bash
``` does the job, but is kind of sloppy admin'ing if you ask me.
NOTE: This will kill every occurrence of bash.

```
ps -auxc
``` may help identify the process.

So, more info is required.

Please let us know...

---

### Post by sona1111 on 2012-09-29
thank you for the reply. I am not sure of the difference between "terminal" and "console", true. This is the server version of ubuntu (the forum is the server forum), and I was not aware that their was a graphical interface that could be run on the server version. (if their is, no, i am not currently running it) Because the entire operating system is text only, i suppose i could have just said the operating system was frozen, idk, sorry for being long winded. 

Their were no active commands running at the time. (like, in the terminal itself)

If you kill bash will it restart by itself? naturally, a power outage occurred recently, so its not frozen right now for me to test it, but this problem has occurred more then once in the past, so i would like to find a way to solve it incase it happens again.

---

### Post by Habitual on 2012-09-30
True re: server ... c-li, but some people install GUIs on their "servers", or use the term "server" for a LAMP install, etc....
so I asked for clarification. Sorry about that.

Even if the server is behaving at the moment, you could/should check the logs with 
```
grep "usb 1-2" /var/log/messages | grep error
```

Edit:
Power outages could damage the Filesystem, so you may wish to fsck with
```
sudo shutdown -rF
``` at the next opportunity and a fsck will happen on the reboot.

Killing all bash processes will NOT restart those same bash processes and my instruction should be disregarded since we are dealing with a c-li only server environment.

Check the logs and let us know.

Thank you,

---

### Post by sona1111 on 2012-09-30
i should have told you that i am running 11.10 on the server. 
the server has also been shut off badly a few times over the past year because of circuit breaker trips, so i will check the file system soon. 

also:
```
grep: /var/log/messages: No such file or directory
```
(i am assuming because its 11.10, excuse me for being a noob)

---

### Post by Habitual on 2012-09-30
[seems to be /var/log/syslog in 11.10]("http://ubuntuforums.org/showthread.php?t=1925053")

so...
```
sudo grep "usb 1-2" /var/log/syslog | grep - i error
``````
lsb_release -drc
``` will tell you exactly what OS/version you are running.

---

### Post by sona1111 on 2012-09-30
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric

the syslog does not go back far enough to find the error.

---

### Post by Habitual on 2012-09-30
ok, let's search the syslog archives with 
```
sudo zgrep "usb 1-2" /var/log/syslog* | grep - i error
```

Notice the [COLOR=Red]**z**[/COLOR] in "zgrep"
[COLOR=Black]
Please let us know...
[/COLOR]

---

### Post by sona1111 on 2012-10-01
cool, learned a new command today. thanks for being patient with me. here is the output for that:

```
/var/log/syslog.5.gz:Sep 26 19:44:27 xseries kernel: [415368.456023] usb 1-2: device descriptor read/64, error -71

```

---

### Post by Habitual on 2012-10-01
Most of the google hits for "xseries kernel" point to IBM hardware... which is curious.
Is this a physical piece of equipment or...
Is this a hosted environment? (this may point to virtual hardware).
Are you running a kernel image, *something other than* what's installed by the installation media?
How did this 11.10 get installed? Upgrade? Clean install?
Any 3rd Party "patches" applied, or other spurious software?

If this is  a non-virtual host, then what, if any, are the BIOS/CMOS options related to USB devices?


output of the following commands as root, please...
```

lsusb
lspci
cat /etc/fstab
ls -[COLOR=Red]1[/COLOR] /boot/vm*

```NOTE: -[COLOR=Red]1 [COLOR=Black](That's a One, not lower case L)[/COLOR][/COLOR]

NOTE: As I don't know the cause, **I am merely looking for the obvious**, and other more experienced gurus may have something to contribute or offer as a solution.

Please let us know...

---

### Post by sona1111 on 2012-10-03
sorry for keeping you so long between replies, lot of work. 

anyway ill start with the output (as root)

lsusb:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04b3:4001 IBM Corp.
```

lspci
```
00:00.0 Host bridge: IBM Calgary PCI-X Host Bridge (rev 02)
00:01.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
00:03.0 USB Controller: NEC Corporation USB (rev 43)
00:03.1 USB Controller: NEC Corporation USB (rev 43)
00:03.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:0f.0 Host bridge: Broadcom CSB6 South Bridge (rev a0)
00:0f.1 IDE interface: Broadcom CSB6 RAID/IDE Controller (rev a0)
00:0f.3 ISA bridge: Broadcom GCLE-2 Host Bridge
01:00.0 Host bridge: IBM Calgary PCI-X Host Bridge (rev 02)
01:01.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5704 Gigabit Ethernet (rev 10)
01:01.1 Ethernet controller: Broadcom Corporation NetXtreme BCM5704 Gigabit Ethernet (rev 10)
01:02.0 SCSI storage controller: Adaptec AIC-9410W SAS (Razor ASIC non-RAID) (rev 08)
02:00.0 Host bridge: IBM Calgary PCI-X Host Bridge (rev 02)
02:01.0 Ethernet controller: Intel Corporation 82546EB Gigabit Ethernet Controller (Copper) (rev 01)
02:01.1 Ethernet controller: Intel Corporation 82546EB Gigabit Ethernet Controller (Copper) (rev 01)
04:00.0 Host bridge: IBM Calgary PCI-X Host Bridge (rev 02)
04:01.0 Ethernet controller: Intel Corporation 82546EB Gigabit Ethernet Controller (Copper) (rev 01)
04:01.1 Ethernet controller: Intel Corporation 82546EB Gigabit Ethernet Controller (Copper) (rev 01)
06:00.0 Host bridge: IBM Calgary PCI-X Host Bridge (rev 02)
06:01.0 Ethernet controller: Intel Corporation 82546EB Gigabit Ethernet Controller (Copper) (rev 01)
06:01.1 Ethernet controller: Intel Corporation 82546EB Gigabit Ethernet Controller (Copper) (rev 01)
08:00.0 Host bridge: IBM Calgary PCI-X Host Bridge (rev 02)
08:01.0 Ethernet controller: Intel Corporation 82546EB Gigabit Ethernet Controller (Copper) (rev 01)
08:01.1 Ethernet controller: Intel Corporation 82546EB Gigabit Ethernet Controller (Copper) (rev 01)
0a:00.0 Host bridge: IBM Calgary PCI-X Host Bridge (rev 02)
0c:00.0 Host bridge: IBM Calgary PCI-X Host Bridge (rev 02)

```

cat /etc/fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1 /home/sona/Videos/drive1 ext3 defaults 0 0
/dev/sdc1 /home/sona/Videos/drive2 ext3 defaults 0 0
# / was on /dev/sda1 during installation
UUID=289e5ba7-0c02-4ccf-89b2-4af34b0ddea4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=afb12a82-1b19-446a-b144-1c287bbf5b67 none            swap    sw              0       0
```

ls -1 /boot/vm*:
```
/boot/vmcoreinfo-3.0.0-12-generic
/boot/vmcoreinfo-3.0.0-15-generic
/boot/vmcoreinfo-3.0.0-16-generic
/boot/vmcoreinfo-3.0.0-17-generic
/boot/vmcoreinfo-3.0.0-19-generic
/boot/vmcoreinfo-3.0.0-20-generic
/boot/vmcoreinfo-3.0.0-21-generic
/boot/vmcoreinfo-3.0.0-22-generic
/boot/vmcoreinfo-3.0.0-24-generic
/boot/vmcoreinfo-3.0.0-25-generic
/boot/vmcoreinfo-3.0.0-26-generic
/boot/vmlinuz-3.0.0-12-generic
/boot/vmlinuz-3.0.0-15-generic
/boot/vmlinuz-3.0.0-16-generic
/boot/vmlinuz-3.0.0-17-generic
/boot/vmlinuz-3.0.0-19-generic
/boot/vmlinuz-3.0.0-20-generic
/boot/vmlinuz-3.0.0-21-generic
/boot/vmlinuz-3.0.0-22-generic
/boot/vmlinuz-3.0.0-24-generic
/boot/vmlinuz-3.0.0-25-generic
/boot/vmlinuz-3.0.0-26-generic

```


this is a physical system on a rack. It is an ibm xseries 366.

the installation came off a regular dvd, nothing else like drivers were installed unless it was automatic.

---

### Post by sona1111 on 2012-10-15
it happened again.

---

