---
title: "Need help interpreting chkrootkit and rkhunter output log"
date: 2019-03-19
forum: Security
---

### Post by @gw7tppYFG6 on 2019-03-19
Hello, I need help interpreting these output logs and need to know if the following has any signs of rootkit or infection. I didn't log in for 2 days and was worried that I found a few things changed in my desktop (like Chromium UI changed despite not updating), even though I didn't do anything change anything last time I logged in. I'm especially concerned about the "```
The tty of the following user process(es) were not found in /var/run/utmp
```" and in rkhunter's "```
Checking for prerequisites WARNING
```" since last time I've scanned, it was never there when I scanned back then. 

_**[SIZE=2]CHKROOTKIT[/SIZE]**_:
```
ROOTDIR is `/'Checking `amd'...                                           not found
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
Checking `mail'...                                          not infected
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
Checking `sendmail'...                                      not infected
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
/usr/lib/debug/.build-id /lib/modules/4.18.0-16-generic/vdso/.build-id /lib/modules/4.18.0-15-generic/vdso/.build-id
/usr/lib/debug/.build-id /lib/modules/4.18.0-16-generic/vdso/.build-id /lib/modules/4.18.0-15-generic/vdso/.build-id
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
chkdirs: nothing detected
Checking `rexedcs'...                                       not found
Checking `sniffer'...                                       lo: not promisc and no packet sniffer sockets
wlx0c8c24bb8cda: PACKET SNIFFER(/sbin/wpa_supplicant[950], /sbin/wpa_supplicant[950], /sbin/dhclient[12049])
Checking `w55808'...                                        not infected
Checking `wted'...                                          chkwtmp: nothing deleted
Checking `scalper'...                                       not infected
Checking `slapper'...                                       not infected
Checking `z2'...                                            user ubuntu deleted or never logged from lastlog!
Checking `chkutmp'...                                        The tty of the following user process(es) were not found
 in /var/run/utmp !
! RUID          PID TTY    CMD
! gdm          1188 tty1   /usr/bin/Xwayland :1024 -rootless -terminate -accessx -core -listen 4 -listen 5 -displayfd 6
! gdm          1139 tty1   /usr/lib/gdm3/gdm-wayland-session gnome-session --autostart /usr/share/gdm/greeter/autostart
! gdm          1143 tty1   /usr/lib/gnome-session/gnome-session-binary --autostart /usr/share/gdm/greeter/autostart
! gdm          1153 tty1   /usr/bin/gnome-shell
! gdm          1592 tty1   /usr/lib/gnome-settings-daemon/gsd-a11y-settings
! gdm          1593 tty1   /usr/lib/gnome-settings-daemon/gsd-clipboard
! gdm          1596 tty1   /usr/lib/gnome-settings-daemon/gsd-color
! gdm          1597 tty1   /usr/lib/gnome-settings-daemon/gsd-datetime
! gdm          1598 tty1   /usr/lib/gnome-settings-daemon/gsd-housekeeping
! gdm          1599 tty1   /usr/lib/gnome-settings-daemon/gsd-keyboard
! gdm          1603 tty1   /usr/lib/gnome-settings-daemon/gsd-media-keys
! gdm          1607 tty1   /usr/lib/gnome-settings-daemon/gsd-mouse
! gdm          1608 tty1   /usr/lib/gnome-settings-daemon/gsd-power
! gdm          1611 tty1   /usr/lib/gnome-settings-daemon/gsd-print-notifications
! gdm          1612 tty1   /usr/lib/gnome-settings-daemon/gsd-rfkill
! gdm          1614 tty1   /usr/lib/gnome-settings-daemon/gsd-screensaver-proxy
! gdm          1618 tty1   /usr/lib/gnome-settings-daemon/gsd-sharing
! gdm          1619 tty1   /usr/lib/gnome-settings-daemon/gsd-smartcard
! gdm          1622 tty1   /usr/lib/gnome-settings-daemon/gsd-sound
! gdm          1629 tty1   /usr/lib/gnome-settings-daemon/gsd-wacom
! gdm          1589 tty1   /usr/lib/gnome-settings-daemon/gsd-xsettings
! gdm          1564 tty1   ibus-daemon --xim --panel disable
! gdm          1567 tty1   /usr/lib/ibus/ibus-dconf
! gdm          1644 tty1   /usr/lib/ibus/ibus-engine-simple
! gdm          1570 tty1   /usr/lib/ibus/ibus-x11 --kill-daemon
! ubuntu       1753 tty2   /usr/lib/xorg/Xorg vt2 -displayfd 3 -auth /run/user/1000/gdm/Xauthority -background none -noreset -keeptty -verbose 3
! ubuntu       2870 tty2   /usr/lib/chromium-browser/chromium-browser --type=renderer --field-trial-handle=8260880200916231517,9233794636305811938,131072 --disable-databases --service-pipe-token=1251321794872558370 --lang=en-US --enable-offline-auto-reload --enable-offline-auto-reload
! ubuntu       4206 tty2   /usr/lib/chromium-browser/chromium-browser --enable-pinch --incognito
! ubuntu       4308 tty2   /usr/lib/chromium-browser/chromium-browser --type=zygote
! ubuntu       4313 tty2   /usr/lib/chromium-browser/chromium-browser --type=zygote
! ubuntu       4363 tty2   /usr/lib/chromium-browser/chromium-browser --type=gpu-process --field-trial-handle=8260880200916231517,9233794636305811938,131072 --gpu-preferences=KAAAAAAAAACAAAAAAQAAAAAAAAAAAGAAAAAAAAEAAAAIAAAAAAAAAAgAAAAAAAAA --service-request-channel-token=1387488217851
! ubuntu       4600 tty2   /usr/lib/chromium-browser/chromium-browser --type=renderer --field-trial-handle=8260880200916231517,9233794636305811938,131072 --service-pipe-token=5044934009969977030 --lang=en-US --extension-process --enable-offline-auto-reload --enable-offline-auto-reload
! ubuntu       4637 tty2   /usr/lib/chromium-browser/chromium-browser --type=renderer --field-trial-handle=8260880200916231517,9233794636305811938,131072 --disable-databases --service-pipe-token=13878750919196923874 --lang=en-US --extension-process --enable-offline-auto-reload --enabl
! ubuntu       5823 tty2   /usr/lib/chromium-browser/chromium-browser --type=renderer --field-trial-handle=8260880200916231517,9233794636305811938,131072 --disable-databases --service-pipe-token=12857804531024528077 --lang=en-US --enable-offline-auto-reload --enable-offline-auto-reloa
! ubuntu       6884 tty2   /usr/lib/chromium-browser/chromium-browser --type=renderer --field-trial-handle=8260880200916231517,9233794636305811938,131072 --disable-databases --service-pipe-token=9594061185048611540 --lang=en-US --enable-offline-auto-reload --enable-offline-auto-reload
! ubuntu       8148 tty2   /usr/lib/chromium-browser/chromium-browser --type=renderer --field-trial-handle=8260880200916231517,9233794636305811938,131072 --disable-databases --service-pipe-token=5220117318914976710 --lang=en-US --enable-offline-auto-reload --enable-offline-auto-reload
! ubuntu      13296 tty2   /usr/lib/chromium-browser/chromium-browser --type=renderer --field-trial-handle=8260880200916231517,9233794636305811938,131072 --disable-databases --service-pipe-token=7155686280270847239 --lang=en-US --enable-offline-auto-reload --enable-offline-auto-reload
! ubuntu      13307 tty2   /usr/lib/chromium-browser/chromium-browser --type=renderer --field-trial-handle=8260880200916231517,9233794636305811938,131072 --disable-databases --service-pipe-token=922042104455081785 --lang=en-US --enable-offline-auto-reload --enable-offline-auto-reload-
! ubuntu      23781 tty2   /usr/lib/chromium-browser/chromium-browser --type=renderer --field-trial-handle=8260880200916231517,9233794636305811938,131072 --disable-databases --service-pipe-token=6142847871585141037 --lang=en-US --enable-offline-auto-reload --enable-offline-auto-reload
! ubuntu       2815 tty2   /usr/lib/deja-dup/deja-dup-monitor
! ubuntu       1751 tty2   /usr/lib/gdm3/gdm-x-session --run-script env GNOME_SHELL_SESSION_MODE=ubuntu gnome-session --session=ubuntu
! ubuntu       1762 tty2   /usr/lib/gnome-session/gnome-session-binary --session=ubuntu
! ubuntu       1886 tty2   /usr/bin/gnome-shell
! ubuntu       2595 tty2   /usr/bin/gnome-software --gapplication-service
! ubuntu       2026 tty2   /usr/lib/gnome-settings-daemon/gsd-a11y-settings
! ubuntu       2024 tty2   /usr/lib/gnome-settings-daemon/gsd-clipboard
! ubuntu       2031 tty2   /usr/lib/gnome-settings-daemon/gsd-color
! ubuntu       2034 tty2   /usr/lib/gnome-settings-daemon/gsd-datetime
! ubuntu       2095 tty2   /usr/lib/gnome-disk-utility/gsd-disk-utility-notify
! ubuntu       2027 tty2   /usr/lib/gnome-settings-daemon/gsd-housekeeping
! ubuntu       2040 tty2   /usr/lib/gnome-settings-daemon/gsd-keyboard
! ubuntu       2044 tty2   /usr/lib/gnome-settings-daemon/gsd-media-keys
! ubuntu       2038 tty2   /usr/lib/gnome-settings-daemon/gsd-mouse
! ubuntu       1993 tty2   /usr/lib/gnome-settings-daemon/gsd-power
! ubuntu       1996 tty2   /usr/lib/gnome-settings-daemon/gsd-print-notifications
! ubuntu       2064 tty2   /usr/lib/gnome-settings-daemon/gsd-printer
! ubuntu       1998 tty2   /usr/lib/gnome-settings-daemon/gsd-rfkill
! ubuntu       1999 tty2   /usr/lib/gnome-settings-daemon/gsd-screensaver-proxy
! ubuntu       2002 tty2   /usr/lib/gnome-settings-daemon/gsd-sharing
! ubuntu       2008 tty2   /usr/lib/gnome-settings-daemon/gsd-smartcard
! ubuntu       2009 tty2   /usr/lib/gnome-settings-daemon/gsd-sound
! ubuntu       2016 tty2   /usr/lib/gnome-settings-daemon/gsd-wacom
! ubuntu       2011 tty2   /usr/lib/gnome-settings-daemon/gsd-xsettings
! ubuntu       1919 tty2   ibus-daemon --xim --panel disable
! ubuntu       1923 tty2   /usr/lib/ibus/ibus-dconf
! ubuntu       2121 tty2   /usr/lib/ibus/ibus-engine-simple
! ubuntu       1925 tty2   /usr/lib/ibus/ibus-x11 --kill-daemon
! ubuntu       2099 tty2   nautilus-desktop
! root        13325 pts/0  /bin/sh /usr/sbin/chkrootkit
! root        13984 pts/0  ./chkutmp
! root        13986 pts/0  ps axk tty,ruser,args -o tty,pid,ruser,args
! root        13985 pts/0  sh -c ps axk "tty,ruser,args" -o "tty,pid,ruser,args"
! root        13324 pts/0  sudo chkrootkit
! ubuntu      13280 pts/0  bash
chkutmp: nothing deleted
Checking `OSX_RSPLUG'...                                    not tested
```

[SIZE=2]_**RKHUNTER**_[/SIZE]:
```
[ Rootkit Hunter version 1.4.6 ]

Checking system commands...


  Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]


  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preloaded libraries                         [ None found ]
    Checking LD_LIBRARY_PATH variable                        [ Not found ]


  Performing file properties checks
    Checking for prerequisites                               [ OK ]
    /usr/sbin/adduser                                        [ OK ]
    /usr/sbin/chroot                                         [ OK ]
    /usr/sbin/cron                                           [ OK ]
    /usr/sbin/groupadd                                       [ OK ]
    /usr/sbin/groupdel                                       [ OK ]
    /usr/sbin/groupmod                                       [ OK ]
    /usr/sbin/grpck                                          [ OK ]
    /usr/sbin/nologin                                        [ OK ]
    /usr/sbin/pwck                                           [ OK ]
    /usr/sbin/rsyslogd                                       [ OK ]
    /usr/sbin/useradd                                        [ OK ]
    /usr/sbin/userdel                                        [ OK ]
    /usr/sbin/usermod                                        [ OK ]
    /usr/sbin/vipw                                           [ OK ]
    /usr/sbin/unhide                                         [ OK ]
    /usr/sbin/unhide-linux                                   [ OK ]
    /usr/sbin/unhide-posix                                   [ OK ]
    /usr/sbin/unhide-tcp                                     [ OK ]
    /usr/bin/awk                                             [ OK ]
    /usr/bin/basename                                        [ OK ]
    /usr/bin/chattr                                          [ OK ]
    /usr/bin/cut                                             [ OK ]
    /usr/bin/diff                                            [ OK ]
    /usr/bin/dirname                                         [ OK ]
    /usr/bin/dpkg                                            [ OK ]
    /usr/bin/dpkg-query                                      [ OK ]
    /usr/bin/du                                              [ OK ]
    /usr/bin/env                                             [ OK ]
    /usr/bin/file                                            [ OK ]
    /usr/bin/find                                            [ OK ]
    /usr/bin/GET                                             [ OK ]
    /usr/bin/groups                                          [ OK ]
    /usr/bin/head                                            [ OK ]
    /usr/bin/id                                              [ OK ]
    /usr/bin/ipcs                                            [ OK ]
    /usr/bin/killall                                         [ OK ]
    /usr/bin/last                                            [ OK ]
    /usr/bin/lastlog                                         [ OK ]
    /usr/bin/ldd                                             [ OK ]
    /usr/bin/less                                            [ OK ]
    /usr/bin/locate                                          [ OK ]
    /usr/bin/logger                                          [ OK ]
    /usr/bin/lsattr                                          [ OK ]
    /usr/bin/lsof                                            [ OK ]
    /usr/bin/mail                                            [ OK ]
    /usr/bin/md5sum                                          [ OK ]
    /usr/bin/mlocate                                         [ OK ]
    /usr/bin/newgrp                                          [ OK ]
    /usr/bin/passwd                                          [ OK ]
    /usr/bin/perl                                            [ OK ]
    /usr/bin/pgrep                                           [ OK ]
    /usr/bin/pkill                                           [ OK ]
    /usr/bin/pstree                                          [ OK ]
    /usr/bin/rkhunter                                        [ OK ]
    /usr/bin/runcon                                          [ OK ]
    /usr/bin/sha1sum                                         [ OK ]
    /usr/bin/sha224sum                                       [ OK ]
    /usr/bin/sha256sum                                       [ OK ]
    /usr/bin/sha384sum                                       [ OK ]
    /usr/bin/sha512sum                                       [ OK ]
    /usr/bin/size                                            [ OK ]
    /usr/bin/sort                                            [ OK ]
    /usr/bin/ssh                                             [ OK ]
    /usr/bin/stat                                            [ OK ]
    /usr/bin/strace                                          [ OK ]
    /usr/bin/strings                                         [ OK ]
    /usr/bin/sudo                                            [ OK ]
    /usr/bin/tail                                            [ OK ]
    /usr/bin/telnet                                          [ OK ]
    /usr/bin/test                                            [ OK ]
    /usr/bin/top                                             [ OK ]
    /usr/bin/touch                                           [ OK ]
    /usr/bin/tr                                              [ OK ]
    /usr/bin/uniq                                            [ OK ]
    /usr/bin/users                                           [ OK ]
    /usr/bin/vmstat                                          [ OK ]
    /usr/bin/w                                               [ OK ]
    /usr/bin/watch                                           [ OK ]
    /usr/bin/wc                                              [ OK ]
    /usr/bin/wget                                            [ OK ]
    /usr/bin/whatis                                          [ OK ]
    /usr/bin/whereis                                         [ OK ]
    /usr/bin/which                                           [ OK ]
    /usr/bin/who                                             [ OK ]
    /usr/bin/whoami                                          [ OK ]
    /usr/bin/numfmt                                          [ OK ]
    /usr/bin/mawk                                            [ OK ]
    /usr/bin/lwp-request                                     [ Warning ]
    /usr/bin/bsd-mailx                                       [ OK ]
    /usr/bin/x86_64-linux-gnu-size                           [ OK ]
    /usr/bin/x86_64-linux-gnu-strings                        [ OK ]
    /usr/bin/telnet.netkit                                   [ OK ]
    /usr/bin/w.procps                                        [ OK ]
    /sbin/depmod                                             [ OK ]
    /sbin/fsck                                               [ OK ]
    /sbin/ifconfig                                           [ OK ]
    /sbin/ifdown                                             [ OK ]
    /sbin/ifup                                               [ OK ]
    /sbin/init                                               [ OK ]
    /sbin/insmod                                             [ OK ]
    /sbin/ip                                                 [ OK ]
    /sbin/lsmod                                              [ OK ]
    /sbin/modinfo                                            [ OK ]
    /sbin/modprobe                                           [ OK ]
    /sbin/rmmod                                              [ OK ]
    /sbin/route                                              [ OK ]
    /sbin/runlevel                                           [ OK ]
    /sbin/sulogin                                            [ OK ]
    /sbin/sysctl                                             [ OK ]
    /bin/bash                                                [ OK ]
    /bin/cat                                                 [ OK ]
    /bin/chmod                                               [ OK ]
    /bin/chown                                               [ OK ]
    /bin/cp                                                  [ OK ]
    /bin/date                                                [ OK ]
    /bin/df                                                  [ OK ]
    /bin/dmesg                                               [ OK ]
    /bin/echo                                                [ OK ]
    /bin/ed                                                  [ OK ]
    /bin/egrep                                               [ OK ]
    /bin/fgrep                                               [ OK ]
    /bin/fuser                                               [ OK ]
    /bin/grep                                                [ OK ]
    /bin/ip                                                  [ OK ]
    /bin/kill                                                [ OK ]
    /bin/less                                                [ OK ]
    /bin/login                                               [ OK ]
    /bin/ls                                                  [ OK ]
    /bin/lsmod                                               [ OK ]
    /bin/mktemp                                              [ OK ]
    /bin/more                                                [ OK ]
    /bin/mount                                               [ OK ]
    /bin/mv                                                  [ OK ]
    /bin/netstat                                             [ OK ]
    /bin/ping                                                [ OK ]
    /bin/ps                                                  [ OK ]
    /bin/pwd                                                 [ OK ]
    /bin/readlink                                            [ OK ]
    /bin/sed                                                 [ OK ]
    /bin/sh                                                  [ OK ]
    /bin/su                                                  [ OK ]
    /bin/touch                                               [ OK ]
    /bin/uname                                               [ OK ]
    /bin/which                                               [ OK ]
    /bin/kmod                                                [ OK ]
    /bin/systemd                                             [ OK ]
    /bin/systemctl                                           [ OK ]
    /bin/dash                                                [ OK ]
    /lib/systemd/systemd                                     [ OK ]


[Press <ENTER> to continue]




Checking for rootkits...


  Performing check of known rootkit files and directories
    55808 Trojan - Variant A                                 [ Not found ]
    ADM Worm                                                 [ Not found ]
    AjaKit Rootkit                                           [ Not found ]
    Adore Rootkit                                            [ Not found ]
    aPa Kit                                                  [ Not found ]
    Apache Worm                                              [ Not found ]
    Ambient (ark) Rootkit                                    [ Not found ]
    Balaur Rootkit                                           [ Not found ]
    BeastKit Rootkit                                         [ Not found ]
    beX2 Rootkit                                             [ Not found ]
    BOBKit Rootkit                                           [ Not found ]
    cb Rootkit                                               [ Not found ]
    CiNIK Worm (Slapper.B variant)                           [ Not found ]
    Danny-Boy's Abuse Kit                                    [ Not found ]
    Devil RootKit                                            [ Not found ]
    Diamorphine LKM                                          [ Not found ]
    Dica-Kit Rootkit                                         [ Not found ]
    Dreams Rootkit                                           [ Not found ]
    Duarawkz Rootkit                                         [ Not found ]
    Ebury backdoor                                           [ Not found ]
    Enye LKM                                                 [ Not found ]
    Flea Linux Rootkit                                       [ Not found ]
    Fu Rootkit                                               [ Not found ]
    ****`it Rootkit                                          [ Not found ]
    GasKit Rootkit                                           [ Not found ]
    Heroin LKM                                               [ Not found ]
    HjC Kit                                                  [ Not found ]
    ignoKit Rootkit                                          [ Not found ]
    IntoXonia-NG Rootkit                                     [ Not found ]
    Irix Rootkit                                             [ Not found ]
    Jynx Rootkit                                             [ Not found ]
    Jynx2 Rootkit                                            [ Not found ]
    KBeast Rootkit                                           [ Not found ]
    Kitko Rootkit                                            [ Not found ]
    Knark Rootkit                                            [ Not found ]
    ld-linuxv.so Rootkit                                     [ Not found ]
    Li0n Worm                                                [ Not found ]
    Lockit / LJK2 Rootkit                                    [ Not found ]
    Mokes backdoor                                           [ Not found ]
    Mood-NT Rootkit                                          [ Not found ]
    MRK Rootkit                                              [ Not found ]
    Ni0 Rootkit                                              [ Not found ]
    Ohhara Rootkit                                           [ Not found ]
    Optic Kit (Tux) Worm                                     [ Not found ]
    Oz Rootkit                                               [ Not found ]
    Phalanx Rootkit                                          [ Not found ]
    Phalanx2 Rootkit                                         [ Not found ]
    Phalanx2 Rootkit (extended tests)                        [ Not found ]
    Portacelo Rootkit                                        [ Not found ]
    R3dstorm Toolkit                                         [ Not found ]
    RH-Sharpe's Rootkit                                      [ Not found ]
    RSHA's Rootkit                                           [ Not found ]
    Scalper Worm                                             [ Not found ]
    Sebek LKM                                                [ Not found ]
    Shutdown Rootkit                                         [ Not found ]
    SHV4 Rootkit                                             [ Not found ]
    SHV5 Rootkit                                             [ Not found ]
    Sin Rootkit                                              [ Not found ]
    Slapper Worm                                             [ Not found ]
    Sneakin Rootkit                                          [ Not found ]
    'Spanish' Rootkit                                        [ Not found ]
    Suckit Rootkit                                           [ Not found ]
    Superkit Rootkit                                         [ Not found ]
    TBD (Telnet BackDoor)                                    [ Not found ]
    TeLeKiT Rootkit                                          [ Not found ]
    T0rn Rootkit                                             [ Not found ]
    trNkit Rootkit                                           [ Not found ]
    Trojanit Kit                                             [ Not found ]
    Tuxtendo Rootkit                                         [ Not found ]
    URK Rootkit                                              [ Not found ]
    Vampire Rootkit                                          [ Not found ]
    VcKit Rootkit                                            [ Not found ]
    Volc Rootkit                                             [ Not found ]
    Xzibit Rootkit                                           [ Not found ]
    zaRwT.KiT Rootkit                                        [ Not found ]
    ZK Rootkit                                               [ Not found ]


[Press <ENTER> to continue]




  Performing additional rootkit checks
    Suckit Rootkit additional checks                         [ OK ]
    Checking for possible rootkit files and directories      [ None found ]
    Checking for possible rootkit strings                    [ None found ]


  Performing malware checks
    Checking running processes for suspicious files          [ None found ]
    Checking for login backdoors                             [ None found ]
    Checking for sniffer log files                           [ None found ]
    Checking for suspicious directories                      [ None found ]
    Checking for suspicious (large) shared memory segments   [ Warning ]


  Performing Linux specific checks
    Checking loaded kernel modules                           [ OK ]
    Checking kernel module names                             [ OK ]


[Press <ENTER> to continue]




Checking the network...


  Performing checks on the network ports
    Checking for backdoor ports                              [ None found ]


  Performing checks on the network interfaces
    Checking for promiscuous interfaces                      [ None found ]


Checking the local host...


  Performing system boot checks
    Checking for local host name                             [ Found ]
    Checking for system startup files                        [ Found ]
    Checking system startup files for malware                [ None found ]


  Performing group and account checks
    Checking for passwd file                                 [ Found ]
    Checking for root equivalent (UID 0) accounts            [ None found ]
    Checking for passwordless accounts                       [ None found ]
    Checking for passwd file changes                         [ None found ]
    Checking for group file changes                          [ None found ]
    Checking root account shell history files                [ None found ]


  Performing system configuration file checks
    Checking for an SSH configuration file                   [ Not found ]
    Checking for a running system logging daemon             [ Found ]
    Checking for a system logging configuration file         [ Found ]
    Checking if syslog remote logging is allowed             [ Not allowed ]


  Performing filesystem checks
    Checking /dev for suspicious file types                  [ None found ]
    Checking for hidden files and directories                [ None found ]


[Press <ENTER> to continue]






System checks summary
=====================


File properties checks...
    Files checked: 149
    Suspect files: 1


Rootkit checks...
    Rootkits checked : 479
    Possible rootkits: 3


Applications checks...
    All checks skipped


The system checks took: 3 minutes and 49 seconds


All results have been written to the log file: /var/log/rkhunter.log


One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)
```

Would appreciate the help.

---

### Post by wildmanne39 on 2019-03-19
*Thread moved to **Security a more appropriate sub-forum**.*

---

### Post by @gw7tppYFG6 on 2019-03-19
Also, the rkhunter output here doesn't have the prerequisite warning because it's the 4th scan I did, it only appeared in the first one. It stopped appearing after I updated rkhunter, however it may not be the case because I had the same thing happen to me without updating rkhunter and simply re-scanned again. I don't remember what was detected but it wasn't just "large shared memory segments", "tcpd" and "lwp". I would have just went my own way but seeing as how my desktop has been messed with, I can't play it safe.

---

### Post by dakkmaddy on 2019-03-19
Whenever I get a weird file, i like to upload it to [https://www.virustotal.com/#/home/upload](https://www.virustotal.com/#/home/upload). You get the benefit of multiple traditional and new age engines scanning the file, the community gets intel.

---

### Post by HermanAB on 2019-03-19
These tools are quite useless.  I would not waste my time with it.

---

### Post by @gw7tppYFG6 on 2019-03-19
Forgot to say this but, may I ask what does "prerequisite" means in the rkhunter output log? I've searched about it being infected or what it means if it's detected to be by rkhunter, but couldn't find anything. Can anyone tell me?

---

### Post by Irihapeti on 2019-03-20
I agree with HermanAB. In over 10 years, I can't recall ever seeing anyone helped by using these tools. On the other hand, I've seen lots of people go through unnecessary anxiety (including myself when I first started using Ubuntu).

---

### Post by @gw7tppYFG6 on 2019-03-20
Well, it's good to have both prevention and treatment, right? Plus, nobody said that there's only one way to use Ubuntu.
It's another good way to learn as well, as a beginner.

Now, anyone willing to help me understand this?

---

### Post by HermanAB on 2019-03-20
If you are really worried about your system being subverted, enable App Armor and configure it properly.  Rkhunter etc, won't help you.

---

### Post by TheFu on 2019-03-20
I've never seen anything besides false positives from  Rkhunter.

---

### Post by @gw7tppYFG6 on 2019-03-23
Hey, I've found something new when I scanned again. This time, someone knew the password. I don't know how but all I know is that rkhunter detected a few things that were infected:
```
/sbin/init
/sbin/runlevel
/bin/systemd
/bin/systemctl
/lib/systemd/systemd
```

The following were changed:
```
Checking for passwd file changes
Checking for group file changes
Checking /dev for suspicious file types

```

I've updated rkhunter again and all but "Checking /dev for suspicious file types" was the only one that didn't change.

Should I be worried?

---

### Post by TheFu on 2019-03-23
> **TheFu said:**
> I've never seen anything besides false positives from  Rkhunter.

I've never seen anything besides false positives from RkHunter.  Seems you have expectations that may not map to what this tool can accomplish.  If you want to look for files that get modified over time, use versioned backups.  Look through the changed files after every backup.  If you don't remember
a) changing the file
b) installing a new package
c) removing an old package
d) updating the package

Then I'd be worried.  This assumes you have the memory/logs to see those changes.  Plus, you need versioned backups anyway for 1,001 other reasons, including getting a rootkit.

---

### Post by @gw7tppYFG6 on 2019-03-23
Something happened and I was supposed to add that I just uninstalled a few packages that I don't use often and installed and uninstalled Wine. Is this the cause behind those warnings? I just want to know why and what is the cause behind those warnings.

---

