---
title: "cant uninstall vmware product b/c machine is running but I can't stop it :("
date: 2009-06-10
forum: Virtualisation
---

### Post by steve101101 on 2009-06-10
I cannot uninstall vmware b/c a virtual machine is running. However when I try to use the player to stop it i get the following error.

[IMG]http://picasaweb.google.com/smarcus3/Screenshots#5345826064283228946[/IMG]

[IMG]http://lh4.ggpht.com/_dlvnQb5XyU8/SjAwe2igWxI/AAAAAAAAAH0/PVTmy8ogB0Y/s512/Screenshot.jpg[/IMG]

---

### Post by 123456789123456789123456 on 2009-06-10
you will get a message from me by your e-mail soon, however, are you trying to remove the virtual machine of xp, or are you trying to completely remove vmware, and it won't quit?  If it won't quit, go to system monitor, and tell it to kill the vmware process.  this will force ubuntu to quit the prgoram, it should be able to be removed after that.

---

### Post by steve101101 on 2009-06-10
either one i don't care. i tried to kill all the vmware process and have even tried rebooting but it doesn't help. 

here is what i get in the uninstall program.

[img]http://lh3.ggpht.com/_dlvnQb5XyU8/SjByZGP-e_I/AAAAAAAAAIs/TpFnHHFeLaA/s576/Screenshot-1.png.jpg[/img]

---

### Post by steve101101 on 2009-06-10
bump

---

### Post by Bölvaður on 2009-06-10
open a terminal, have that vmware open and type
```
xkill
```
and click the vmware

probably it will show you the same thing again.

So.... copy the output of this:


```
ps -e
```

you can try look through the list and see a possible suspect and kill it by either typing

```
kill 3333
```
where 3333 can be what ever number the PID of the process is (which you'll find in the list)

or

```
killall firefox
```
where the name firefox will be replaced by your process name

---

### Post by steve101101 on 2009-06-11
here is the output

```

steven@steven-desktop:~$ ps -e
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:25 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:35 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:02 migration/2
   10 ?        00:00:23 ksoftirqd/2
   11 ?        00:00:00 watchdog/2
   12 ?        00:00:01 migration/3
   13 ?        00:00:24 ksoftirqd/3
   14 ?        00:00:00 watchdog/3
   15 ?        00:00:00 events/0
   16 ?        00:00:00 events/1
   17 ?        00:00:00 events/2
   18 ?        00:00:00 events/3
   19 ?        00:00:00 khelper
   20 ?        00:00:00 kstop/0
   21 ?        00:00:00 kstop/1
   22 ?        00:00:00 kstop/2
   23 ?        00:00:00 kstop/3
   24 ?        00:00:00 kintegrityd/0
   25 ?        00:00:00 kintegrityd/1
   26 ?        00:00:00 kintegrityd/2
   27 ?        00:00:00 kintegrityd/3
   28 ?        00:00:00 kblockd/0
   29 ?        00:00:00 kblockd/1
   30 ?        00:00:00 kblockd/2
   31 ?        00:00:00 kblockd/3
   32 ?        00:00:00 kacpid
   33 ?        00:00:00 kacpi_notify
   34 ?        00:00:00 cqueue
   35 ?        00:00:03 ata/0
   36 ?        00:00:02 ata/1
   37 ?        00:00:02 ata/2
   38 ?        00:00:02 ata/3
   39 ?        00:00:00 ata_aux
   40 ?        00:00:00 ksuspend_usbd
   41 ?        00:00:00 khubd
   42 ?        00:00:00 kseriod
   43 ?        00:00:00 kmmcd
   44 ?        00:00:00 btaddconn
   45 ?        00:00:00 btdelconn
   46 ?        00:00:02 pdflush
   47 ?        00:00:00 pdflush
   48 ?        00:00:06 kswapd0
   49 ?        00:00:00 aio/0
   50 ?        00:00:00 aio/1
   51 ?        00:00:00 aio/2
   52 ?        00:00:00 aio/3
   53 ?        00:00:00 ecryptfs-kthrea
   56 ?        00:00:00 scsi_eh_0
   57 ?        00:00:10 scsi_eh_1
   58 ?        00:00:09 scsi_eh_2
   59 ?        00:00:00 scsi_eh_3
   60 ?        00:00:00 kstriped
   61 ?        00:00:00 kmpathd/0
   62 ?        00:00:00 kmpathd/1
   63 ?        00:00:00 kmpathd/2
   64 ?        00:00:00 kmpathd/3
   65 ?        00:00:00 kmpath_handlerd
   66 ?        00:00:00 ksnapd
   67 ?        00:00:00 kondemand/0
   68 ?        00:00:01 kondemand/1
   69 ?        00:00:00 kondemand/2
   70 ?        00:00:00 kondemand/3
   71 ?        00:00:00 krfcommd
  844 ?        00:00:08 kjournald2
  978 ?        00:00:00 udevd
 1634 ?        00:00:00 kpsmoused
 2566 tty4     00:00:00 getty
 2567 tty5     00:00:00 getty
 2570 tty2     00:00:00 getty
 2572 tty3     00:00:00 getty
 2574 tty6     00:00:00 getty
 2647 ?        00:00:00 acpid
 2692 ?        00:00:02 syslogd
 2715 ?        00:00:00 dd
 2717 ?        00:00:00 klogd
 2740 ?        00:00:08 dbus-daemon
 3488 ?        00:00:00 chipcardd4
 3506 ?        00:00:01 nmbd
 3510 ?        00:00:00 smbd
 3518 ?        00:00:00 smbd
 3541 ?        00:00:00 winbindd
 3563 ?        00:00:10 hald
 3566 ?        00:00:03 console-kit-dae
 3629 ?        00:00:00 hald-runner
 3659 ?        00:00:00 hald-addon-inpu
 3660 ?        00:00:00 winbindd
 3702 ?        00:00:10 hald-addon-stor
 3703 ?        00:00:00 hald-addon-cpuf
 3704 ?        00:00:00 hald-addon-acpi
 3709 ?        00:00:10 hald-addon-stor
 3727 ?        00:00:00 bluetoothd
 3762 ?        00:00:00 gdm
 3765 ?        00:00:00 gdm
 3791 ?        00:00:00 NetworkManager
 3799 ?        00:00:00 wpa_supplicant
 3803 ?        00:00:00 nm-system-setti
 3815 ?        00:00:00 avahi-daemon
 3816 ?        00:00:00 avahi-daemon
 3839 ?        00:00:00 cupsd
 3868 ?        00:00:00 system-tools-ba
 3941 ?        00:00:00 atd
 3972 ?        00:00:00 cron
 4068 tty1     00:00:00 getty
 4069 ?        00:31:46 chipcardd4
 4445 ?        00:00:00 evolution-data-
 4495 ?        00:00:00 system-service-
 7993 ?        00:00:38 vmware-vmx
 8075 ?        00:00:00 winbindd
 8076 ?        00:00:00 winbindd
 9704 ?        00:00:00 thunderbird
 9716 ?        00:00:00 run-mozilla.sh
 9720 ?        00:00:22 thunderbird-bin
12185 ?        00:00:00 evolution-data-
12200 ?        00:00:00 evolution-data-
12362 ?        00:00:08 dropbox
13566 tty9     00:17:27 Xorg
13584 ?        00:00:00 gnome-keyring-d
13596 ?        00:00:00 x-session-manag
13728 ?        00:00:00 ssh-agent
13731 ?        00:00:01 gpg-agent
13736 ?        00:00:11 dbus-daemon
13737 ?        00:00:00 dbus-launch
13746 ?        00:34:21 pulseaudio
13747 ?        00:00:00 gconf-helper
13749 ?        00:00:04 gconfd-2
13760 ?        00:00:00 seahorse-agent
13763 ?        00:00:00 gvfsd
13769 ?        00:00:00 gvfs-fuse-daemo
13778 ?        00:00:04 gnome-settings-
13784 ?        00:01:54 compiz.real
13785 ?        00:00:26 gnome-panel
13786 ?        00:00:30 nautilus
13788 ?        00:00:00 bonobo-activati
13791 ?        00:00:00 gpodder
13792 ?        00:00:00 .conky_startup.
13796 ?        00:00:10 python
13800 ?        00:00:01 update-notifier
13805 ?        00:00:00 gvfs-hal-volume
13806 ?        00:00:00 trashapplet
13811 ?        00:00:00 evolution-alarm
13813 ?        00:00:00 gvfs-gphoto2-vo
13814 ?        00:00:00 nm-applet
13816 ?        00:00:00 gvfsd-trash
13827 ?        00:00:00 bluetooth-apple
13829 ?        00:00:01 notify-osd
13832 ?        00:00:00 gnome-power-man
13837 ?        00:00:01 cpufreq-applet
13839 ?        00:00:00 fast-user-switc
13845 ?        00:00:00 mixer_applet2
13847 ?        00:00:00 indicator-apple
13859 ?        00:00:00 evolution-data-
13862 ?        00:00:00 evolution-excha
13880 ?        00:00:00 sh
13881 ?        00:00:00 compiz-decorato
13883 ?        00:00:13 gtk-window-deco
13895 ?        00:00:00 gvfsd-burn
13913 ?        00:33:22 rhythmbox
13919 ?        00:18:37 conky
14202 ?        00:00:10 gnome-screensav
14502 ?        01:00:41 firefox
15360 ?        00:00:00 dhclient
16118 ?        00:00:00 evolution-data-
17007 ?        00:00:56 vmware-vmx <defunct>
18039 ?        00:00:00 gnome-terminal
18040 ?        00:00:00 gnome-pty-helpe
18041 pts/0    00:00:00 bash
18252 ?        00:00:01 vmplayer
19140 ?        00:00:00 vmware-unity-he
19312 pts/0    00:00:00 ps
24000 ?        00:00:00 evolution-data-
25559 ?        00:00:00 gvfsd-http
28889 ?        00:00:00 alltray
29248 ?        00:00:00 evolution-data-


```

I am able to stop vmware, but can't stop the machine that it says its running.

---

### Post by steve101101 on 2009-06-11
here is the output when vmware player is closed

```

steven@steven-desktop:~$ ps -e
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:25 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:35 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:02 migration/2
   10 ?        00:00:23 ksoftirqd/2
   11 ?        00:00:00 watchdog/2
   12 ?        00:00:01 migration/3
   13 ?        00:00:24 ksoftirqd/3
   14 ?        00:00:00 watchdog/3
   15 ?        00:00:00 events/0
   16 ?        00:00:00 events/1
   17 ?        00:00:00 events/2
   18 ?        00:00:00 events/3
   19 ?        00:00:00 khelper
   20 ?        00:00:00 kstop/0
   21 ?        00:00:00 kstop/1
   22 ?        00:00:00 kstop/2
   23 ?        00:00:00 kstop/3
   24 ?        00:00:00 kintegrityd/0
   25 ?        00:00:00 kintegrityd/1
   26 ?        00:00:00 kintegrityd/2
   27 ?        00:00:00 kintegrityd/3
   28 ?        00:00:00 kblockd/0
   29 ?        00:00:00 kblockd/1
   30 ?        00:00:00 kblockd/2
   31 ?        00:00:00 kblockd/3
   32 ?        00:00:00 kacpid
   33 ?        00:00:00 kacpi_notify
   34 ?        00:00:00 cqueue
   35 ?        00:00:03 ata/0
   36 ?        00:00:02 ata/1
   37 ?        00:00:02 ata/2
   38 ?        00:00:02 ata/3
   39 ?        00:00:00 ata_aux
   40 ?        00:00:00 ksuspend_usbd
   41 ?        00:00:00 khubd
   42 ?        00:00:00 kseriod
   43 ?        00:00:00 kmmcd
   44 ?        00:00:00 btaddconn
   45 ?        00:00:00 btdelconn
   46 ?        00:00:02 pdflush
   47 ?        00:00:00 pdflush
   48 ?        00:00:06 kswapd0
   49 ?        00:00:00 aio/0
   50 ?        00:00:00 aio/1
   51 ?        00:00:00 aio/2
   52 ?        00:00:00 aio/3
   53 ?        00:00:00 ecryptfs-kthrea
   56 ?        00:00:00 scsi_eh_0
   57 ?        00:00:10 scsi_eh_1
   58 ?        00:00:09 scsi_eh_2
   59 ?        00:00:00 scsi_eh_3
   60 ?        00:00:00 kstriped
   61 ?        00:00:00 kmpathd/0
   62 ?        00:00:00 kmpathd/1
   63 ?        00:00:00 kmpathd/2
   64 ?        00:00:00 kmpathd/3
   65 ?        00:00:00 kmpath_handlerd
   66 ?        00:00:00 ksnapd
   67 ?        00:00:00 kondemand/0
   68 ?        00:00:01 kondemand/1
   69 ?        00:00:00 kondemand/2
   70 ?        00:00:00 kondemand/3
   71 ?        00:00:00 krfcommd
  844 ?        00:00:08 kjournald2
  978 ?        00:00:00 udevd
 1634 ?        00:00:00 kpsmoused
 2566 tty4     00:00:00 getty
 2567 tty5     00:00:00 getty
 2570 tty2     00:00:00 getty
 2572 tty3     00:00:00 getty
 2574 tty6     00:00:00 getty
 2647 ?        00:00:00 acpid
 2692 ?        00:00:02 syslogd
 2715 ?        00:00:00 dd
 2717 ?        00:00:00 klogd
 2740 ?        00:00:08 dbus-daemon
 3488 ?        00:00:00 chipcardd4
 3506 ?        00:00:01 nmbd
 3510 ?        00:00:00 smbd
 3518 ?        00:00:00 smbd
 3541 ?        00:00:00 winbindd
 3563 ?        00:00:10 hald
 3566 ?        00:00:03 console-kit-dae
 3629 ?        00:00:00 hald-runner
 3659 ?        00:00:00 hald-addon-inpu
 3660 ?        00:00:00 winbindd
 3702 ?        00:00:10 hald-addon-stor
 3703 ?        00:00:00 hald-addon-cpuf
 3704 ?        00:00:00 hald-addon-acpi
 3709 ?        00:00:10 hald-addon-stor
 3727 ?        00:00:00 bluetoothd
 3762 ?        00:00:00 gdm
 3765 ?        00:00:00 gdm
 3791 ?        00:00:00 NetworkManager
 3799 ?        00:00:00 wpa_supplicant
 3803 ?        00:00:00 nm-system-setti
 3815 ?        00:00:00 avahi-daemon
 3816 ?        00:00:00 avahi-daemon
 3839 ?        00:00:00 cupsd
 3868 ?        00:00:00 system-tools-ba
 3941 ?        00:00:00 atd
 3972 ?        00:00:00 cron
 4068 tty1     00:00:00 getty
 4069 ?        00:31:48 chipcardd4
 4445 ?        00:00:00 evolution-data-
 4495 ?        00:00:00 system-service-
 7993 ?        00:00:38 vmware-vmx
 8075 ?        00:00:00 winbindd
 8076 ?        00:00:00 winbindd
 9704 ?        00:00:00 thunderbird
 9716 ?        00:00:00 run-mozilla.sh
 9720 ?        00:00:22 thunderbird-bin
12185 ?        00:00:00 evolution-data-
12200 ?        00:00:00 evolution-data-
12362 ?        00:00:08 dropbox
13566 tty9     00:17:34 Xorg
13584 ?        00:00:00 gnome-keyring-d
13596 ?        00:00:00 x-session-manag
13728 ?        00:00:00 ssh-agent
13731 ?        00:00:01 gpg-agent
13736 ?        00:00:11 dbus-daemon
13737 ?        00:00:00 dbus-launch
13746 ?        00:34:23 pulseaudio
13747 ?        00:00:00 gconf-helper
13749 ?        00:00:04 gconfd-2
13760 ?        00:00:00 seahorse-agent
13763 ?        00:00:00 gvfsd
13769 ?        00:00:00 gvfs-fuse-daemo
13778 ?        00:00:04 gnome-settings-
13784 ?        00:01:55 compiz.real
13785 ?        00:00:26 gnome-panel
13786 ?        00:00:30 nautilus
13788 ?        00:00:00 bonobo-activati
13791 ?        00:00:00 gpodder
13792 ?        00:00:00 .conky_startup.
13796 ?        00:00:10 python
13800 ?        00:00:01 update-notifier
13805 ?        00:00:00 gvfs-hal-volume
13806 ?        00:00:00 trashapplet
13811 ?        00:00:00 evolution-alarm
13813 ?        00:00:00 gvfs-gphoto2-vo
13814 ?        00:00:00 nm-applet
13816 ?        00:00:00 gvfsd-trash
13827 ?        00:00:00 bluetooth-apple
13829 ?        00:00:01 notify-osd
13832 ?        00:00:00 gnome-power-man
13837 ?        00:00:01 cpufreq-applet
13839 ?        00:00:00 fast-user-switc
13845 ?        00:00:00 mixer_applet2
13847 ?        00:00:00 indicator-apple
13859 ?        00:00:00 evolution-data-
13862 ?        00:00:00 evolution-excha
13880 ?        00:00:00 sh
13881 ?        00:00:00 compiz-decorato
13883 ?        00:00:13 gtk-window-deco
13895 ?        00:00:00 gvfsd-burn
13913 ?        00:33:22 rhythmbox
13919 ?        00:18:39 conky
14202 ?        00:00:10 gnome-screensav
14502 ?        01:01:01 firefox
15360 ?        00:00:00 dhclient
16118 ?        00:00:00 evolution-data-
17007 ?        00:00:56 vmware-vmx <defunct>
18039 ?        00:00:00 gnome-terminal
18040 ?        00:00:00 gnome-pty-helpe
18041 pts/0    00:00:00 bash
24000 ?        00:00:00 evolution-data-
24315 pts/0    00:00:00 ps
24316 ?        00:00:00 sh
24317 ?        00:00:00 sensors
24318 ?        00:00:00 grep
24319 ?        00:00:00 cut
24320 ?        00:00:00 cut
25559 ?        00:00:00 gvfsd-http
28889 ?        00:00:00 alltray
29248 ?        00:00:00 evolution-data-

```

---

### Post by steve101101 on 2009-06-11
anyone. please help. i just want to be able to run my vmware machine. :( :( :( :( :(

---

### Post by badook on 2009-06-11
run 'ps -e | grep 'vmware''
and run a kill for each process you get
e.g. 'kill 17007'

---

### Post by Bölvaður on 2009-06-11
7993 ?        00:00:38 vmware-vmx
vmware-vmx <defunct>

vmplayer

19140 ?        00:00:00 vmware-unity-he


some of these look mighty suspicious. Do what the guy above my told you.

you can also (as I said) just "killall wmware-vmx" or what ever the name of the process is.

---

### Post by bodhi.zazen on 2009-06-11
Use grep to filter the output of ps

```
ps aux | grep vmware
```

then kill

```
kill -9 xxx
```

where xxx is the PID (Process ID Number).

Or

```
killall vmware

kill -9 `pidof vmware`
```

Also vmware runs as a service, so ...

```
sudo /etc/init.d/vmware stop
```

It that fails, you can try rebooting

---

### Post by steve101101 on 2009-06-11
i tried running kill and sudo kill and the number of the process but it doens't stop :(

---

### Post by steve101101 on 2009-06-11
rebooted again then kill another vmware process then was able to uninstall. thanks for the help. :)

---

