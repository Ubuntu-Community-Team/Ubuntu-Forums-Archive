---
title: "Boot up time of Bionic flavours"
date: 2018-04-07
forum: Ubuntu Development Version
---

### Post by sudodus on 2018-04-07
How come the ultra light Lubuntu Bionic needs 40 seconds from the grub menu to the log in screen, while the corresponding Kubuntu and Xubuntu Bionic can do it in 10 seconds in my [Toshiba laptop](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/)?

All the operating systems were installed from the Bionic Beta-2 desktop 64-bit iso files and made up to date today (and reside in a new SSD connected via the internal SATA bay).

---

### Post by cariboo on 2018-04-07
Try:

```
systemd-analyze blame
```

to see what is taking longer on the system running Lubuntu.

---

### Post by sudodus on 2018-04-07
In the following data I don't see why Lubuntu is so much slower than Kubuntu and Xubuntu. Please help me interpret the data :-P

```

Boot time for Bionic Beta-2 installed and made up to date
---------------------------------------------------------
[COLOR="#0000CD"]Lubuntu amd64[/COLOR]
-------------
tester@tester-SATELLITE-PRO-C850-19W:~$ systemd-analyze critical-chain 
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @4.161s
&#9492;&#9472;multi-user.target @4.161s
  &#9492;&#9472;kerneloops.service @4.149s +11ms
    &#9492;&#9472;network-online.target @4.147s
      &#9492;&#9472;NetworkManager-wait-online.service @998ms +3.148s
        &#9492;&#9472;NetworkManager.service @788ms +207ms
          &#9492;&#9472;dbus.service @771ms
            &#9492;&#9472;basic.target @764ms
              &#9492;&#9472;sockets.target @764ms
                &#9492;&#9472;cups.socket @764ms
                  &#9492;&#9472;sysinit.target @760ms
                    &#9492;&#9472;cryptsetup.target @756ms
                      &#9492;&#9472;systemd-ask-password-wall.path @157ms
                        &#9492;&#9472;-.mount @155ms
                          &#9492;&#9472;system.slice @158ms
                            &#9492;&#9472;-.slice @155ms
tester@tester-SATELLITE-PRO-C850-19W:~$ systemd-analyze blame
          3.148s NetworkManager-wait-online.service
           574ms apt-daily.service
           543ms dev-sda1.device
           473ms plymouth-start.service
           353ms udisks2.service
           326ms systemd-journal-flush.service
           207ms NetworkManager.service
           196ms upower.service
           196ms systemd-rfkill.service
           144ms systemd-timesyncd.service
           129ms systemd-resolved.service
           120ms accounts-daemon.service
           114ms swapfile.swap
           107ms keyboard-setup.service
            99ms apparmor.service
            98ms grub-common.service
            93ms systemd-logind.service
            92ms systemd-udev-trigger.service
            90ms lightdm.service
            89ms plymouth-quit-wait.service
            86ms ModemManager.service
            67ms alsa-restore.service
            67ms wpa_supplicant.service
            65ms systemd-journald.service
            64ms apport.service
            57ms plymouth-read-write.service
            51ms systemd-tmpfiles-setup-dev.service
            50ms avahi-daemon.service
            49ms systemd-tmpfiles-setup.service
            47ms bluetooth.service
            47ms gpu-manager.service
            45ms pppd-dns.service
            40ms user@1000.service
            40ms systemd-modules-load.service
            39ms systemd-sysctl.service
            34ms setvtrgb.service
            31ms systemd-udevd.service
            21ms rsyslog.service
lines 1-38
-------------
[COLOR="#B22222"]Kubuntu amd64[/COLOR]
-------------
tester@tester-SATELLITE-PRO-C850-19W:~$ systemd-analyze critical-chain 
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @4.286s
&#9492;&#9472;multi-user.target @4.286s
  &#9492;&#9472;kerneloops.service @4.275s +10ms
    &#9492;&#9472;network-online.target @4.275s
      &#9492;&#9472;NetworkManager-wait-online.service @1.107s +3.166s
        &#9492;&#9472;NetworkManager.service @896ms +210ms
          &#9492;&#9472;dbus.service @706ms
            &#9492;&#9472;basic.target @696ms
              &#9492;&#9472;sockets.target @696ms
                &#9492;&#9472;snapd.socket @687ms +8ms
                  &#9492;&#9472;sysinit.target @679ms
                    &#9492;&#9472;systemd-timesyncd.service @525ms +152ms
                      &#9492;&#9472;systemd-tmpfiles-setup.service @480ms +39ms
                        &#9492;&#9472;systemd-journal-flush.service @239ms +240ms
                          &#9492;&#9472;systemd-journald.service @160ms +77ms
                            &#9492;&#9472;syslog.socket @159ms
                              &#9492;&#9472;system.slice @154ms                                                                                      
                                &#9492;&#9472;-.slice @152ms                                                                                         
tester@tester-SATELLITE-PRO-C850-19W:~$ systemd-analyze blame
          3.166s NetworkManager-wait-online.service                                                                                      
           790ms dev-sda5.device                                                                                                         
           351ms mpd.service                                                                                                             
           314ms udisks2.service                                                                                                         
           255ms thermald.service                                                                                                        
           240ms systemd-journal-flush.service                                                                                           
           210ms NetworkManager.service                                                                                                  
           209ms rsyslog.service                                                                                                         
           177ms systemd-logind.service                                                                                                  
           152ms systemd-timesyncd.service                                                                                               
           140ms apparmor.service                                                                                                        
           136ms systemd-resolved.service                                                                                                
           117ms keyboard-setup.service
           115ms snapd.service
           109ms ModemManager.service
           101ms accounts-daemon.service
           100ms systemd-udev-trigger.service
            94ms upower.service
            89ms swapfile.swap
            77ms systemd-journald.service
            75ms avahi-daemon.service
            73ms grub-common.service
            72ms wpa_supplicant.service
            71ms plymouth-quit-wait.service
            70ms plymouth-quit.service
            70ms alsa-restore.service
            61ms systemd-udevd.service
            54ms systemd-modules-load.service
            53ms apport.service
            48ms gpu-manager.service
            45ms pppd-dns.service
            40ms packagekit.service
            39ms systemd-tmpfiles-setup.service
            39ms systemd-tmpfiles-setup-dev.service
lines 1-34
------------
[COLOR="#008080"]Xubuntu i386[/COLOR]
-------------
tester@tester-SATELLITE-PRO-C850-19W:~$ systemd-analyze critical-chain 
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @4.565s
&#9492;&#9472;multi-user.target @4.565s
  &#9492;&#9472;hddtemp.service @4.542s +22ms
    &#9492;&#9472;network-online.target @4.541s
      &#9492;&#9472;NetworkManager-wait-online.service @1.378s +3.162s
        &#9492;&#9472;NetworkManager.service @1.140s +236ms
          &#9492;&#9472;dbus.service @1.110s
            &#9492;&#9472;basic.target @1.094s
              &#9492;&#9472;sockets.target @1.094s
                &#9492;&#9472;snapd.socket @1.092s +2ms
                  &#9492;&#9472;sysinit.target @1.090s
                    &#9492;&#9472;cryptsetup.target @1.083s
                      &#9492;&#9472;systemd-ask-password-wall.path @175ms
                        &#9492;&#9472;-.mount @166ms
                          &#9492;&#9472;system.slice @168ms
                            &#9492;&#9472;-.slice @166ms
tester@tester-SATELLITE-PRO-C850-19W:~$ systemd-analyze blame
          3.162s NetworkManager-wait-online.service
           776ms dev-sda6.device
           767ms plymouth-start.service
           314ms udisks2.service
           295ms upower.service
           236ms NetworkManager.service
           227ms systemd-journal-flush.service
           202ms systemd-rfkill.service
           162ms systemd-timesyncd.service
           162ms ModemManager.service
           132ms systemd-resolved.service
           130ms accounts-daemon.service
           129ms grub-common.service
           126ms keyboard-setup.service
           126ms apport.service
           119ms systemd-udev-trigger.service
           116ms speech-dispatcher.service
           109ms apparmor.service
           107ms systemd-journald.service
           107ms snapd.service
           104ms systemd-logind.service
            98ms wpa_supplicant.service
            96ms thermald.service
            95ms avahi-daemon.service
            88ms lightdm.service
            87ms plymouth-quit-wait.service
            84ms systemd-modules-load.service
            83ms bluetooth.service
            83ms systemd-tmpfiles-setup-dev.service
            82ms lm-sensors.service
            77ms swapfile.swap
            64ms alsa-restore.service
            60ms systemd-tmpfiles-setup.service
            55ms gpu-manager.service
            51ms pppd-dns.service
            40ms user@1000.service
            37ms systemd-udevd.service
            27ms rsyslog.service
            24ms systemd-sysctl.service
            22ms hddtemp.service
            21ms systemd-random-seed.service
            21ms polkit.service
            15ms plymouth-read-write.service
            12ms systemd-remount-fs.service
lines 1-44

```

---

### Post by flocculant on 2018-04-07
not sure that's designed to be of any use ;)

looked in logs ? not sure if every de has an .xsession-errors?

---

### Post by sudodus on 2018-04-07
This shows the total time, but not what to blame.

```

Boot time for Bionic Beta-2 installed and made up to date
---------------------------------------------------------
[COLOR="#0000CD"]Lubuntu amd64[/COLOR]
-------------
tester@tester-SATELLITE-PRO-C850-19W:~$ systemd-analyze time
Startup finished in 35.834s (kernel) + 4.282s (userspace) = 40.117s
graphical.target reached after 4.274s in userspace
-------------
[COLOR="#B22222"]Kubuntu amd64[/COLOR]
-------------
tester@tester-SATELLITE-PRO-C850-19W:~$ systemd-analyze time
Startup finished in 3.551s (kernel) + 4.371s (userspace) = 7.923s
graphical.target reached after 4.361s in userspace
------------
[COLOR="#008080"]Xubuntu i386[/COLOR]
------------
tester@tester-SATELLITE-PRO-C850-19W:~$ systemd-analyze time
Startup finished in 3.020s (kernel) + 4.574s (userspace) = 7.595s
graphical.target reached after 4.565s in userspace

```

@flocculant,

I must admit that I don't know what to look for in the log files. What would you suggest?

---

### Post by sudodus on 2018-04-07
After some random browsing in the log files, I found this difference between Lubuntu and Kubuntu: **clocksource**, which maybe is to blame. It is present only in Lubuntu's log file, and the time after it has increased a lot.

See the attached file.

---

### Post by mc4man on 2018-04-07
Does the resolution of this thread have anything to do with your setup
[https://ubuntuforums.org/showthread.php?t=2323378](https://ubuntuforums.org/showthread.php?t=2323378)

---

### Post by sudodus on 2018-04-07
> **mc4man said:**
> Does the resolution of this thread have anything to do with your setup
[https://ubuntuforums.org/showthread.php?t=2323378](https://ubuntuforums.org/showthread.php?t=2323378)

Thanks for the link :-)

The funny thing is that Kubuntu and Xubuntu are installed in the same computer as the faulty Lubuntu. All of them are booted with the same settings in BIOS mode.

When at the log in screen, logging in and when logged in, Lubuntu is responsive as it should be. The problem seems to affect only the boot process.

---

### Post by flocculant on 2018-04-08
You could check dmesg - look for long wait times between entries there.

You could also set journalctl to be persistent between boots, then you'll be able to check between boots on different installs at least.

1 quick question - I see libcrypt in the screenie - do all 3 installs use encryption?

---

### Post by sudodus on 2018-04-08
I will start looking into dmesg.

All installations are basic with unencrypted ext4 file systems and unencrypted home.

```

tester@tester-SATELLITE-PRO-C850-19W:~$ sudo lsblk -fm
NAME   FSTYPE LABEL      UUID                                 MOUNTPOINT                 SIZE OWNER GROUP MODE
sda                                                                                    111,8G root  disk  brw-rw----
&#9500;&#9472;sda1 ext4   lubuntu-64 bbaa8c2c-38ef-4df3-bf48-49b5bc97ff1c /media/tester/lubuntu-64  28,1G root  disk  brw-rw----
&#9500;&#9472;sda2                                                                                     1K root  disk  brw-rw----
&#9500;&#9472;sda5 ext4   kubuntu-64 f4426133-397e-4cbb-81e3-1d783f94ce0c /media/tester/kubuntu-64  28,6G root  disk  brw-rw----
&#9500;&#9472;sda6 ext4   xubuntu-32 5729470b-9b91-4b42-8507-945760b839f0 /                           20G root  disk  brw-rw----
&#9500;&#9472;sda7 ext4              1ca86e1f-1885-447a-ab76-df90cf83df38                           17,6G root  disk  brw-rw----
&#9492;&#9472;sda8 ext4              d1b7b347-72a2-48f2-a728-3f1af2b03648                           17,5G root  disk  brw-rw----
sr0                                                                                     1024M root  cdrom brw-rw----
tester@tester-SATELLITE-PRO-C850-19W:~$ df -h
Filsystem      Storlek Använt Ledigt Anv% Monterat på
udev              1,9G      0   1,9G   0% /dev
tmpfs             392M   1,4M   391M   1% /run
/dev/sda6          20G   4,8G    14G  26% /
tmpfs             2,0G      0   2,0G   0% /dev/shm
tmpfs             5,0M   4,0K   5,0M   1% /run/lock
tmpfs             2,0G      0   2,0G   0% /sys/fs/cgroup
tmpfs             392M    16K   392M   1% /run/user/1000
/dev/sda5          29G   7,0G    20G  27% /media/tester/kubuntu-64
/dev/sda1          28G   5,0G    21G  20% /media/tester/lubuntu-64
tester@tester-SATELLITE-PRO-C850-19W:~$ 

```

Edit: I don't understand how to use dmesg to monitor the boot process.

---

### Post by flocculant on 2018-04-08
> **sudodus said:**
> I will start looking into dmesg....

Edit: I don't understand how to use dmesg to monitor the boot process.

I perhaps wasn't clear enough there :)

As a ridiculous example:

[    7.795797] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[10854.006950] usb 3-5: USB disconnect, device number 7

There's a 10847 second gap there. Look in dmesg for long waits during the first 40 or so seconds as that's what you're looking at. (Startup finished in 35.834s (kernel) + 4.282s (userspace) = 40.117s)

Also if you want to read it in a txt file then ```
dmesg > ~/Desktop/dmesg
``` or something :)

Hope that helps

---

### Post by sudodus on 2018-04-08
@flocculant,

Thanks for the detailed explanation.

**dmesg** tells me the same thing as what was shown in the screendump in post #6, that **clocksource** is to blame. It seems to take more than 30 seconds, if I understand things correctly.

Or is clocksource only indicating that something is taking time, but not shown explicitly?

Or is it the next command, that takes time, to prepare for the ext4 file system? But this *should* work like in Kubuntu and Xubuntu?

---

### Post by oldfred on 2018-04-08
dmesg was the old log file with Upstart:

 Older systems with Upstart
gksudo gedit /var/log/dmesg
sudo grep -E -i "error|warning" /var/log/dmesg  


   Newer systems with systemd:
systemd-analyze blame
[https://access.redhat.com/articles/systemd-cheat-sheet](https://access.redhat.com/articles/systemd-cheat-sheet) 

My 18.04 install from weeks ago on SSD seems to run ok. Standard Ubuntu, planning to convert to gnome-panel fallback, but have not done it yet.

But my full install to a flash drive is extremely slow. Not sure yet if a flash drive issue or because from latest 18.04.
I am seeing a lot of errors in syslog.
nm-applet[2011]: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed

---

### Post by sudodus on 2018-04-08
@oldfred,

Yes, I get some errors too, similar or the same as you describe.

But this long delay, that is only affecting Lubuntu is making me confused.

@everybody,

I am installing Lubuntu via the Ubuntu Server iso file now ...

---

### Post by sudodus on 2018-04-08
Lubuntu via the Ubuntu Server (and installing **lubuntu-desktop** into the text mode system) worked.

It is a little faster than the system installed via the Lubuntu desktop iso file, but still significantly slower than Kubuntu and Xubuntu.

- Clocksource is called but finishes quickly, no significant delay.

- But there are other delays, that come later in the boot sequence:
. network configuration of the ethernet connection 'enp3s0' (20 seconds)
. bluetooth configuration (7 seconds)

We should notice, that the setup of the network in the server installation is not general and portable as in the desktop installations (unless you tweak it afterwards, which I did, but it did not get faster).

Could it be, that **clocksource** time delay in Lubuntu (installed from the Lubuntu desktop iso) is actually taking the blame, while the **network** is configured? If that is the case, it seems that Kubuntu and Xubuntu use a better method for that purpose.

---

### Post by mc4man on 2018-04-08
edit: na.

If you remove quiet & the vt7handoff from the boot line (in grub screen press e) then lubuntu will output text during boot
(won't if vt7.. is there..?
Seems to hang after running some pre-mount script. So issue here occurs @
[    7.900283] ACPI: \_SB_.PCI0.PEG0.PEGP: failed to evaluate _DSM
[   35.908233] EXT4-fs (sdb6): mounted filesystem with ordered data mode. Opts: (null)

But if I also use nomodeset then would see the slowdown at same point as you. If I use nomodeset & specify a clocksource then it slows down after something else. 
So the issue isn't what's before the slowdown, it's during the first thing after which in all cases here is 
 EXT4-fs (sdb6): mounted filesystem with ordered data mode. Opts: (null)
It's taking a long time to mount the fs.. or be ready to mount the fs

---

### Post by sudodus on 2018-04-08
@mc4man,

Interesting analysis, which puts the blame on how to manage the file system (It's taking a long time to mount the fs.. or be ready to mount the fs).

Edit: I could repeat and verify your analysis :-) I checked the file system with **e2fsck -f**, but it made no difference, still 40 seconds to boot Lubuntu.

[hr][/hr]
@everybody,

I made another Lubuntu (64-bit) installation via Xubuntu Core (xubuntu-18.04-core-amd64.iso).

- Installed Xubuntu Core, which is very snappy, and on top installed lubuntu-desktop.

This way I got a Xubuntu-Lubuntu installed system, which boots much faster than Lubuntu, when booted from its own desktop file.

The attached screenshot shows what is taking most time in this case

- network configuration of the ethernet connection 'enp3s0' (4 seconds)
- bluetooth configuration (9 seconds)

These are the same tasks as when installed via Ubuntu Server, but the ethernet configuration is much faster when installed via Xubuntu [Core].

---

### Post by flocculant on 2018-04-09
> **sudodus said:**
> @mc4man,

Interesting analysis, which puts the blame on how to manage the file system (It's taking a long time to mount the fs.. or be ready to mount the fs).

Edit: I could repeat and verify your analysis :-) I checked the file system with **e2fsck -f**, but it made no difference, still 40 seconds to boot Lubuntu.

[hr][/hr]
@everybody,

I made another Lubuntu (64-bit) installation via Xubuntu Core (xubuntu-18.04-core-amd64.iso).

- Installed Xubuntu Core, which is very snappy, and on top installed lubuntu-desktop.

This way I got a Xubuntu-Lubuntu installed system, which boots much faster than Lubuntu, when booted from its own desktop file.

The attached screenshot shows what is taking most time in this case

- network configuration of the ethernet connection 'enp3s0' (4 seconds)
- bluetooth configuration (9 seconds)

These are the same tasks as when installed via Ubuntu Server, but the ethernet configuration is much faster when installed via Xubuntu [Core].

On a different note - I see you have r8169 there - are you affected by [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1760073](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1760073) ?

---

### Post by VMC on 2018-04-09
By comparision( Our hardware is different.)
dmesg:```
$ dmesg|grep clocksource
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 76450417870 ns
[    0.032081] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.054105] clocksource: Switched to clocksource hpet
[    0.072766] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    1.888122] tsc: Refined TSC clocksource calibration: 3013.705 MHz
[    1.888128] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2b70d7a0847, max_idle_ns: 440795224568 ns
[    2.912189] clocksource: Switched to clocksource tsc
```
journalctl:```
$ journalctl -b -err --no-pager|grep clocksource
Apr 08 22:02:07 bionic kernel: clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
Apr 08 22:02:07 bionic kernel: clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 76450417870 ns
Apr 08 22:02:07 bionic kernel: clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
```

How does the *ns* time compare?

---

### Post by sudodus on 2018-04-09
> **flocculant said:**
> On a different note - I see you have r8169 there - are you affected by [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1760073](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1760073) ?

I tested with the system installed from Xubuntu Core (amd64) with lubuntu-desktop, and the wired network works after resume.

Also the wireless access points are available (shown by the nm-applet). I connected to one of them, and it survives too after resume.

---

### Post by sudodus on 2018-04-09
> **VMC said:**
> By comparision( Our hardware is different.)
dmesg:```
$ dmesg|grep clocksource
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 76450417870 ns
[    0.032081] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.054105] clocksource: Switched to clocksource hpet
[    0.072766] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    1.888122] tsc: Refined TSC clocksource calibration: 3013.705 MHz
[    1.888128] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2b70d7a0847, max_idle_ns: 440795224568 ns
[    2.912189] clocksource: Switched to clocksource tsc
```
journalctl:```
$ journalctl -b -err --no-pager|grep clocksource
Apr 08 22:02:07 bionic kernel: clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
Apr 08 22:02:07 bionic kernel: clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 76450417870 ns
Apr 08 22:02:07 bionic kernel: clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
```

How does the *ns* time compare?

```

XuCore2Lubu-64

tester@tester-SATELLITE-PRO-C850-19W:~$ dmesg|grep clocksource
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.040433] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.911072] clocksource: Switched to clocksource hpet
[    0.925719] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    2.747991] tsc: Refined TSC clocksource calibration: 2494.334 MHz
[    2.748006] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x23f45126d86, max_idle_ns: 440795256522 ns
[    3.774156] clocksource: Switched to clocksource tsc
tester@tester-SATELLITE-PRO-C850-19W:~$ journalctl -b -err --no-pager|grep clocksource
apr 09 08:49:26 tester-SATELLITE-PRO-C850-19W kernel: clocksource: Switched to clocksource tsc
apr 09 08:49:26 tester-SATELLITE-PRO-C850-19W kernel: clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x23f45126d86, max_idle_ns: 440795256522 ns
apr 09 08:49:26 tester-SATELLITE-PRO-C850-19W kernel: tsc: Refined TSC clocksource calibration: 2494.334 MHz
apr 09 08:49:25 tester-SATELLITE-PRO-C850-19W kernel: clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
apr 09 08:49:25 tester-SATELLITE-PRO-C850-19W kernel: clocksource: Switched to clocksource hpet
apr 09 08:49:25 tester-SATELLITE-PRO-C850-19W kernel: clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
apr 09 08:49:25 tester-SATELLITE-PRO-C850-19W kernel: clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
apr 09 08:49:25 tester-SATELLITE-PRO-C850-19W kernel: clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
tester@tester-SATELLITE-PRO-C850-19W:~$

---

lubuntu-64 (the system with slow boot)

tester@tester-SATELLITE-PRO-C850-19W:~$ dmesg|grep clocksource
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.040431] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.910068] clocksource: Switched to clocksource hpet
[    0.925728] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    2.748099] tsc: Refined TSC clocksource calibration: 2494.337 MHz
[    2.748124] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x23f4544ecb4, max_idle_ns: 440795257849 ns
[    3.772377] clocksource: Switched to clocksource tsc
tester@tester-SATELLITE-PRO-C850-19W:~$ journalctl -b -err --no-pager|grep clocksource
apr 09 09:06:10 tester-SATELLITE-PRO-C850-19W kernel: clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
apr 09 09:06:10 tester-SATELLITE-PRO-C850-19W kernel: clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
apr 09 09:06:10 tester-SATELLITE-PRO-C850-19W kernel: clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
tester@tester-SATELLITE-PRO-C850-19W:~$

```

But as indicated by @mc4man, it seems the problem is managing the file system (It's taking a long time to mount the fs.. or be ready to mount the fs), which means that 'clocksource is innocent'.

---

### Post by monkeybrain20122 on 2018-04-09
There is this link about speeding up file system mounts, but it is over my head. [https://wiki.archlinux.org/index.php/Improving_performance/Boot_process](https://wiki.archlinux.org/index.php/Improving_performance/Boot_process)

---

### Post by mc4man on 2018-04-09
I've no clue as to why lubuntu is 30 sec or so slower, it just seems to have nothing to due with clocksource.
ex. - 5 slightly different boots with command, this is on a hybrid (optimus machine

> Default boot - 
Command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-13-generic.efi.signed root=UUID=cdc9940c-9a67-4c5c-af2b-b5b5f90d23df ro quiet splash vt.handoff=1

[    2.888111] usb 3-7: new full-speed USB device number 5 using xhci_hcd
[    3.037540] usb 3-7: New USB device found, idVendor=8087, idProduct=07dc
[    3.037543] usb 3-7: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.388227] clocksource: Switched to clocksource tsc
[    7.900268] ACPI: \_SB_.PCI0.PEG0.PEGP: failed to evaluate _DSM
[   34.778661] EXT4-fs (sdb6): mounted filesystem with ordered data mode. Opts: (null)


> nomodeset boot
Command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-13-generic.efi.signed root=UUID=cdc9940c-9a67-4c5c-af2b-b5b5f90d23df ro nomodeset

[    2.928062] usb 3-7: new full-speed USB device number 5 using xhci_hcd
[    3.077291] usb 3-7: New USB device found, idVendor=8087, idProduct=07dc
[    3.078422] usb 3-7: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.388232] clocksource: Switched to clocksource tsc
[   35.015978] EXT4-fs (sdb6): mounted filesystem with ordered data mode. Opts: (null)

> nomoseset, clocksource=acpi_pm boot
4:27 UTC 2018 (Ubuntu 4.15.0-13.14-generic 4.15.10)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-13-generic.efi.signed root=UUID=cdc9940c-9a67-4c5c-af2b-b5b5f90d23df ro nomodeset clocksource=acpi_pm

[    2.932107] usb 3-7: new full-speed USB device number 5 using xhci_hcd
[    3.081503] usb 3-7: New USB device found, idVendor=8087, idProduct=07dc
[    3.082645] usb 3-7: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[   34.985834] EXT4-fs (sdb6): mounted filesystem with ordered data mode. Opts: (null)
> 
nomodeset clocksource=hpet boot
Command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-13-generic.efi.signed root=UUID=cdc9940c-9a67-4c5c-af2b-b5b5f90d23df ro nomodeset clocksource=hpet

[    2.932086] usb 3-7: new full-speed USB device number 5 using xhci_hcd
[    3.081400] usb 3-7: New USB device found, idVendor=8087, idProduct=07dc
[    3.082541] usb 3-7: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[   35.072640] EXT4-fs (sdb6): mounted filesystem with ordered data mode. Opts: (null)
> 
nomodeset clocksource=tsc boot
Command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-13-generic.efi.signed root=UUID=cdc9940c-9a67-4c5c-af2b-b5b5f90d23df ro nomodeset clocksource=tsc

[    2.932145] usb 3-7: new full-speed USB device number 5 using xhci_hcd
[    3.081513] usb 3-7: New USB device found, idVendor=8087, idProduct=07dc
[    3.082649] usb 3-7: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.388262] clocksource: Switched to clocksource tsc
[   35.008068] EXT4-fs (sdb6): mounted filesystem with ordered data mode. Opts: (null)

for comparison default ubuntu boot, same machine
> Command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-13-generic.efi.signed root=UUID=e8def74e-6e50-4d6e-9adb-07d2b230cb55 ro quiet splash nouveau.runpm=0

[    2.964077] usb 3-7: new full-speed USB device number 5 using xhci_hcd
[    3.113431] usb 3-7: New USB device found, idVendor=8087, idProduct=07dc
[    3.113433] usb 3-7: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.117068] hidraw: raw HID events driver (C) Jiri Kosina
[    3.121519] usbcore: registered new interface driver usbhid
[    3.121519] usbhid: USB HID core driver
[    3.123655] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-2/input2
[    3.223610] Console: switching to colour frame buffer device 240x67
[    3.244871] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    3.250057] logitech-hidpp-device 0003:046D:402D.0004: hidraw1: USB HID v1.11 Keyboard [Logitech M560] on usb-0000:00:14.0-2:1
[    3.452246] clocksource: Switched to clocksource tsc
[    3.632000] raid6: sse2x1   gen() 11469 MB/s
[    3.680003] raid6: sse2x1   xor()  8133 MB/s
[    3.728002] raid6: sse2x2   gen() 13683 MB/s
[    3.776000] raid6: sse2x2   xor()  8859 MB/s
[    3.824004] raid6: sse2x4   gen() 16114 MB/s
[    3.872001] raid6: sse2x4   xor() 10128 MB/s
[    3.920000] raid6: avx2x1   gen() 22493 MB/s
[    3.967999] raid6: avx2x1   xor() 15273 MB/s
[    4.015998] raid6: avx2x2   gen() 26061 MB/s
[    4.063999] raid6: avx2x2   xor() 15901 MB/s
[    4.111999] raid6: avx2x4   gen() 29535 MB/s
[    4.160000] raid6: avx2x4   xor() 18920 MB/s
[    4.160000] raid6: using algorithm avx2x4 gen() 29535 MB/s
[    4.160001] raid6: .... xor() 18920 MB/s, rmw enabled
[    4.160001] raid6: using avx2x2 recovery algorithm
[    4.160740] xor: automatically using best checksumming function   avx       
[    4.161444] async_tx: api initialized (async)
[    4.187472] Btrfs loaded, crc32c=crc32c-intel
[    4.376622] EXT4-fs (sdb4): mounted filesystem with ordered data mode. Opts: (null)

The bigger issue may be that, at least here, lubuntu does not show a splash screen during this extended boot. So it's just a black screen with no activity for 35 sec or so. ( only the default lubuntu above has splash but adding it back to any made no difference at all..

---

### Post by VMC on 2018-04-10
Mine boots as fast as xubuntu. I am using nouveau. The harward must be the issue:
```
System:    Host: bionic Kernel: 4.15.0-13-generic x86_64 bits: 64 Desktop: Xfce 4.12.3
           Distro: Ubuntu Bionic Beaver (development branch)
Machine:   Device: desktop System: HP-Pavilion product: AY652AA-ABA s5310y serial: N/A
           Mobo: PEGATRON model: Narra6 v: 6.01 serial: N/A BIOS: American Megatrends v: 5.17 date: 01/07/2010
CPU:       Dual core AMD Athlon II X2 250 (-MCP-) cache: 2048 KB
           clock speeds: max: 3000 MHz 1: 1800 MHz 2: 1800 MHz
Graphics:  Card: NVIDIA C61 [GeForce 6150SE nForce 430]
           Display Server: x11 (X.Org 1.19.6 ) drivers: nouveau (unloaded: modesetting,fbdev,vesa)
           Resolution: 1600x900@60.00hz
           OpenGL: renderer: NV4C version: 2.1 Mesa 18.0.0-rc5
Audio:     Card-1 NVIDIA MCP61 High Definition Audio driver: snd_hda_intel Sound: ALSA v: k4.15.0-13-generic
           Card-2 Pixart Imaging driver: USB Audio
Network:   Card: NVIDIA MCP61 Ethernet driver: forcedeth
           IF: enp0s7 state: up speed: 100 Mbps duplex: full mac: e0:cb:4e:9b:e8:4d
Drives:    HDD Total Size: 1000.2GB (4.3% used)
           ID-1: /dev/sda model: WDC_WD10EZEX size: 1000.2GB
Partition: ID-1: / size: 96G used: 4.2G (5%) fs: ext4 dev: /dev/sda6
           ID-2: swap-1 size: 2.10GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 26.5C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 154 Uptime: 23 min Memory: 742.6/3693.2MB Client: Shell (bash) inxi: 2.3.56
```

---

### Post by mc4man on 2018-04-10
Here the machine tried on (have removed the lubuntu install)
```
$ inxi -SMGDPI
System:    Host: doug-Lenovo-IdeaPad-Y510P Kernel: 4.15.0-13-generic x86_64 bits: 64 Desktop: Gnome 
           Distro: Ubuntu Bionic Beaver (development branch) 
Machine:   Type: Laptop System: LENOVO product: 20217 v: Lenovo IdeaPad Y510P serial: N/A 
           Mobo: LENOVO model: VIQY0Y1 v: 31900058STD serial: N/A UEFI: LENOVO v: 74CN44WW(V3.05) 
           date: 09/18/2013 
Graphics:  Card-1: Intel 4th Gen Core Processor Integrated Graphics driver: i915 v: kernel 
           Card-2: NVIDIA GK107M [GeForce GT 755M] driver: nouveau v: kernel 
           Display Server: x11 (X.Org 1.19.6) driver: intel resolution: 1920x1080~60Hz 
           OpenGL: renderer: Mesa DRI Intel Haswell Mobile v: 4.5 Mesa 18.0.0-rc5 
Drives:    HDD Total Size: 488.13 GiB used: 32.01 GiB (6.6%) 
           ID-1: /dev/sda model: LITEONIT_LSS-24L size: 22.37 GiB 
           ID-2: /dev/sdb model: Crucial_CT500MX2 size: 465.76 GiB 
Partition: ID-1: / size: 91.17 GiB used: 32.01 GiB (35.1%) fs: ext4 dev: /dev/sdb4 
Info:      Processes: 240 Uptime: 39m Memory: 7.70 GiB used: 929.0 MiB (11.8%) Shell: bash inxi: 3.0.00 
```

The other possibility is # of other partitions on drive. Here sdb is the Os drive, there are 4 installed Os's prior to lubuntu

---

### Post by sudodus on 2018-04-10
I installed Lubuntu as the first system, and then added Kubuntu, Xubuntu and the combo-systems with lubuntu-desktop installed 'afterwards'. The number of partitions increased (at first only one, the Lubuntu partition (with a swapfile)), and it made no difference in boot time.

[hr][/hr]
I intend to install Lubuntu into some other computer(s) and check if this problem is specific to some particular hardware.

---

### Post by VMC on 2018-04-10
> **mc4man said:**
> Here the machine tried on (have removed the lubuntu install)
```
$ inxi -SMGDPI
System:    Host: doug-Lenovo-IdeaPad-Y510P Kernel: 4.15.0-13-generic x86_64 bits: 64 Desktop: Gnome 
           Distro: Ubuntu Bionic Beaver (development branch) 
Machine:   Type: Laptop System: LENOVO product: 20217 v: Lenovo IdeaPad Y510P serial: N/A 
           Mobo: LENOVO model: VIQY0Y1 v: 31900058STD serial: N/A UEFI: LENOVO v: 74CN44WW(V3.05) 
           date: 09/18/2013 
Graphics:  Card-1: Intel 4th Gen Core Processor Integrated Graphics driver: i915 v: kernel 
           Card-2: NVIDIA GK107M [GeForce GT 755M] driver: nouveau v: kernel 
           Display Server: x11 (X.Org 1.19.6) driver: intel resolution: 1920x1080~60Hz 
           OpenGL: renderer: Mesa DRI Intel Haswell Mobile v: 4.5 Mesa 18.0.0-rc5 
Drives:    HDD Total Size: 488.13 GiB used: 32.01 GiB (6.6%) 
           ID-1: /dev/sda model: LITEONIT_LSS-24L size: 22.37 GiB 
           ID-2: /dev/sdb model: Crucial_CT500MX2 size: 465.76 GiB 
Partition: ID-1: / size: 91.17 GiB used: 32.01 GiB (35.1%) fs: ext4 dev: /dev/sdb4 
Info:      Processes: 240 Uptime: 39m Memory: 7.70 GiB used: 929.0 MiB (11.8%) Shell: bash inxi: 3.0.00 
```

The other possibility is # of other partitions on drive. Here sdb is the Os drive, there are 4 installed Os's prior to lubuntu
I also have several partitions:
```
/dev/sda1: LABEL="WindowsPRO" UUID="E88C81DA8C81A3A2" TYPE="ntfs" PARTUUID="c881d74c-01"/dev/sda2: LABEL="ntfs" UUID="E2A61116A610ECB3" TYPE="ntfs" PARTUUID="c881d74c-02"
/dev/sda5: UUID="39f23cab-3322-438e-becd-56e468346656" TYPE="swap" PARTUUID="c881d74c-05"
/dev/sda6: LABEL="xfce" UUID="91414660-7d31-4c30-a47c-ac9710600035" TYPE="ext4" PARTUUID="c881d74c-06"
/dev/sda7: LABEL="manjaro" UUID="4e775ad7-588d-4742-9e28-43a4973004c3" TYPE="ext4" PARTUUID="c881d74c-07"
/dev/sda8: LABEL="lxde" UUID="3bf04a11-feb7-4af2-ae89-e611911b9f45" TYPE="ext4" PARTUUID="c881d74c-08"
/dev/sda9: LABEL="SAVE" UUID="e9d12e7c-7f32-4b2d-9296-c11df97f80f9" TYPE="ext4" PARTUUID="c881d74c-09"
```

---

### Post by sudodus on 2018-04-11
I installed Lubuntu and Xubuntu-Core (both amd64) into a Lenovo ThinkPad X131e with Intel i3 generation 2 . This computer is less powerful than the Toshiba with Intel i5 generation 3. I installed into an SSD connected via USB 3 and an external adapter. This SSD is older than the SSD in the Toshiba.

The boot time from the grub menu to the login screen for Lubuntu and Xubuntu are almost the same, measured with an external timer 13 and 14 seconds.

There is no significant delay for the root file system to be mounted.

```

ThinkPad-X131e
Intel(R) Core(TM) i3-2367M CPU @ 1.40GHz
---

Lubuntu: real clocktime to login screen = 13 s

tester@tester-ThinkPad-X131e:~$ systemd-analyze time
Startup finished in 13ms (firmware) + 5ms (loader) + 4.195s (kernel) + 5.496s (userspace) = 9.710s
graphical.target reached after 5.482s in userspace
tester@tester-ThinkPad-X131e:~$ 

---

Xubuntu-Core: real clocktime to login screen = 14 s

tester@tester-ThinkPad-X131e:~$ systemd-analyze time
Startup finished in 13ms (firmware) + 4ms (loader) + 4.132s (kernel) + 3.308s (userspace) = 7.459s
graphical.target reached after 3.294s in userspace
tester@tester-ThinkPad-X131e:~$ 

```

---

### Post by sudodus on 2018-04-11
I moved the USB SSD from the Thinkpad to the Toshiba, and the systems (installed in UEFI mode) were portable.

I booted them in the Toshiba, and the time from the grub menu to the login screen for Lubuntu and Xubuntu are almost the same, measured with an external timer

- 9 seconds with SSD connected via USB 3
- 7 seconds with SSD connected via SATA

So it seems that Lubuntu's slow boot in the Toshiba is caused by problems with the hardware or internal programming in the new SSD. This new SSD has 512 bytes logical sectors and 4096 bytes physical sectors (512/4096), while the old SSD has (512/512) sector size.

The funny thing is that Xubuntu and Kubuntu are not affected by those problems. What can cause this difference between the flavours?

---

### Post by mc4man on 2018-04-12
> **sudodus said:**
> I moved the USB SSD from the Thinkpad to the Toshiba, and the systems (installed in UEFI mode) were portable.

I booted them in the Toshiba, and the time from the grub menu to the login screen for Lubuntu and Xubuntu are almost the same, measured with an external timer

- 9 seconds with SSD connected via USB 3
- 7 seconds with SSD connected via SATA

So it seems that Lubuntu's slow boot in the Toshiba is caused by problems with the hardware or internal programming in the new SSD. This new SSD has 512 bytes logical sectors and 4096 bytes physical sectors (512/4096), while the old SSD has (512/512) sector size.

The funny thing is that Xubuntu and Kubuntu are not affected by those problems. What can cause this difference between the flavours?
I've no idea what my ssd uses, it's a Crucial_CT500MX2

What I also noticed is that booting to the live usb of lubuntu is fine, probably 3 times faster than what a lubuntu install will do here..

---

### Post by sudodus on 2018-04-12
@mc4man,

You can check the sectors of your SSD with

```
sudo parted -ls
```

---

### Post by mc4man on 2018-04-12
> **sudodus said:**
> @mc4man,

You can check the sectors of your SSD with

```
sudo parted -ls
```
shows

> Model: ATA Crucial_CT500MX2 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


---

### Post by sudodus on 2018-04-13
Thanks, @mc4man,

This supports the assumption, that there are problems for Lubuntu to manage SSDs with 4096 byte size physical sectors. But the other flavours of Ubuntu can manage it.

Let us hope that this can help the Lubuntu developer to find and squash the bug.

---

### Post by sudodus on 2018-04-13
@mc4man (and everybody else who is affected),

Please look at the bug report [#1763611 'Lubuntu bionic boots slower than the other Ubuntu flavours with some SSDs'](https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1763611)

and click 'This bug affects you' (if it does affect you) in order to confirm the bug.

---

### Post by sudodus on 2018-04-20
I think we have a solution to this bug in Lubuntu :-)

**Volker Kempter** (v-kempter) at Launchpad found this link, where **alci** found our bug and squashed it (I guess alci did not see our bug report).

[Slow boot, long kernel load time, due to wrong resume device](https://askubuntu.com/questions/1013830/slow-boot-long-kernel-load-time-due-to-wrong-resume-device)

I tried to summarize the findings in [Comment #17 in the bug report](https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1763611/comments/17)

[The whole bug report](https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1763611)

---

