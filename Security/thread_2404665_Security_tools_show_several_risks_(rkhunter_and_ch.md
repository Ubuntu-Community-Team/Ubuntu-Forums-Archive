---
title: "Security tools show several risks (rkhunter and chkrootkit)"
date: 2018-10-26
forum: Security
---

### Post by lbcunha1 on 2018-10-26
Hi Everyone!

I have run two tests in the system and a lot of itens were found.

Could you please help me to evaluate?

Regards and Thanks a lot!!

```
RKHUNTER:
[20:37:36]   /usr/bin/ipcs                                   [ Warning ]
[20:37:36] Warning: The file properties have changed:
[20:37:36]          File: /usr/bin/ipcs
[20:37:36]          Current inode: 10226470    Stored inode: 10226342
[20:37:36]          Current file modification time: 1532622057 (26-jul-2018 13:20:57)
[20:37:36]          Stored file modification time : 1526467297 (16-mai-2018 07:41:37)

[20:37:36]   /usr/bin/last                                   [ Warning ]
[20:37:36] Warning: The file properties have changed:
[20:37:36]          File: /usr/bin/last
[20:37:36]          Current inode: 10226472    Stored inode: 10226426
[20:37:36]          Current file modification time: 1532622057 (26-jul-2018 13:20:57)
[20:37:36]          Stored file modification time : 1526467297 (16-mai-2018 07:41:37)

[20:37:36]   /usr/bin/logger                                 [ Warning ]
[20:37:36] Warning: The file properties have changed:
[20:37:37]          File: /usr/bin/logger
[20:37:37]          Current inode: 10226441    Stored inode: 10223732
[20:37:37]          Current file modification time: 1532622057 (26-jul-2018 13:20:57)
[20:37:37]          Stored file modification time : 1526467297 (16-mai-2018 07:41:37)

[20:37:38]   /usr/bin/rkhunter                               [ Warning ]
[20:37:38] Warning: The file properties have changed:
[20:37:38]          File: /usr/bin/rkhunter
[20:37:38]          Current hash: 4fc010937549545e537d17dc421ebc5dd22a05f83984e24297db7454c97cf70c
[20:37:38]          Stored hash : 1923834546c47ee675259adf111d7d67a684f3b4669619cdee4bdca06ef4cf3f
[20:37:38]          Current inode: 10224551    Stored inode: 10224119
[20:37:38]          Current size: 575854    Stored size: 575855
[20:37:38]          Current file modification time: 1534039735 (11-ago-2018 23:08:55)
[20:37:38]          Stored file modification time : 1519408531 (23-fev-2018 14:55:31)

[20:37:39]   /usr/bin/size                                   [ Warning ]
[20:37:39] Warning: The file properties have changed:
[20:37:39]          File: /usr/bin/size
[20:37:39]          Current hash: 745c334d493c8a5180316d985efbfd9954426a350a97bbd6d7ba513acf7537de
[20:37:39]          Stored hash : 6b478d3775e102443e90fecc81069f6a400303f9dafa46aad3510bb7af7aad88
[20:37:39]          Current inode: 10227801    Stored inode: 10227785
[20:37:39]          Current file modification time: 1536766688 (12-set-2018 12:38:08)
[20:37:39]          Stored file modification time : 1526498451 (16-mai-2018 16:20:51)

[20:37:39]   /usr/bin/strings                                [ Warning ]
[20:37:39] Warning: The file properties have changed:
[20:37:39]          File: /usr/bin/strings
[20:37:39]          Current hash: 656ef18961273db4a5c04c70bcae2d6a3b0d7bc2f7b804fb63d891eb78273847
[20:37:39]          Stored hash : 9458ff5dd79759dc41788d91d15cb5d309bf1b25e3a439bc3d6ca6e3e7652d23
[20:37:39]          Current inode: 10227803    Stored inode: 10227787
[20:37:40]          Current file modification time: 1536766688 (12-set-2018 12:38:08)
[20:37:40]          Stored file modification time : 1526498451 (16-mai-2018 16:20:51)

[20:37:41]   /usr/bin/whatis                                 [ Warning ]
[20:37:41] Warning: The file properties have changed:
[20:37:41]          File: /usr/bin/whatis
[20:37:41]          Current hash: 4db12b03ae8a2b9bfdb8d275f71d60b08cf0cc6b92c13062f87960e98d34fc60
[20:37:41]          Stored hash : 9dca55b557385e2d7c47ba16372703ce1b1d7b80c5576ac5bd68c40e892e7353
[20:37:41]          Current inode: 10226591    Stored inode: 10224109
[20:37:41]          Current file modification time: 1533410172 (04-ago-2018 16:16:12)
[20:37:41]          Stored file modification time : 1523099733 (07-abr-2018 08:15:33)
[20:37:41]   /usr/bin/whereis                                [ Warning ]
[20:37:41] Warning: The file properties have changed:
[20:37:41]          File: /usr/bin/whereis
[20:37:41]          Current inode: 10226516    Stored inode: 10231478
[20:37:41]          Current file modification time: 1532622057 (26-jul-2018 13:20:57)
[20:37:41]          Stored file modification time : 1526467297 (16-mai-2018 07:41:37)

[20:37:42]   /usr/bin/lwp-request                            [ Warning ]
[20:37:42] Warning: The command '/usr/bin/lwp-request' has been replaced by a script: /usr/bin/lwp-request: Perl script text executable

[20:37:42]   /usr/bin/x86_64-linux-gnu-size                  [ Warning ]
[20:37:42] Warning: The file properties have changed:
[20:37:42]          File: /usr/bin/x86_64-linux-gnu-size
[20:37:42]          Current hash: 745c334d493c8a5180316d985efbfd9954426a350a97bbd6d7ba513acf7537de
[20:37:42]          Stored hash : 6b478d3775e102443e90fecc81069f6a400303f9dafa46aad3510bb7af7aad88
[20:37:42]          Current inode: 10224714    Stored inode: 10227770
[20:37:42]          Current file modification time: 1536766688 (12-set-2018 12:38:08)
[20:37:42]          Stored file modification time : 1526498451 (16-mai-2018 16:20:51)
[20:37:42]   /usr/bin/x86_64-linux-gnu-strings               [ Warning ]
[20:37:42] Warning: The file properties have changed:
[20:37:42]          File: /usr/bin/x86_64-linux-gnu-strings
[20:37:42]          Current hash: 656ef18961273db4a5c04c70bcae2d6a3b0d7bc2f7b804fb63d891eb78273847
[20:37:42]          Stored hash : 9458ff5dd79759dc41788d91d15cb5d309bf1b25e3a439bc3d6ca6e3e7652d23
[20:37:42]          Current inode: 10224715    Stored inode: 10227772
[20:37:42]          Current file modification time: 1536766688 (12-set-2018 12:38:08)
[20:37:42]          Stored file modification time : 1526498451 (16-mai-2018 16:20:51)

[20:37:43]   /sbin/fsck                                      [ Warning ]
[20:37:43] Warning: The file properties have changed:
[20:37:43]          File: /sbin/fsck
[20:37:43]          Current inode: 3014700    Stored inode: 3014986
[20:37:43]          Current file modification time: 1532622057 (26-jul-2018 13:20:57)
[20:37:43]          Stored file modification time : 1526467297 (16-mai-2018 07:41:37)
[
[20:37:45]   /sbin/sulogin                                   [ Warning ]
[20:37:45] Warning: The file properties have changed:
[20:37:45]          File: /sbin/sulogin
[20:37:45]          Current inode: 3014749    Stored inode: 3015012
[20:37:45]          Current file modification time: 1532622057 (26-jul-2018 13:20:57)
[20:37:45]          Stored file modification time : 1526467297 (16-mai-2018 07:41:37)

[20:37:47]   /bin/dmesg                                      [ Warning ]
[20:37:47] Warning: The file properties have changed:
[20:37:47]          File: /bin/dmesg
[20:37:47]          Current inode: 6422561    Stored inode: 6422543
[20:37:47]          Current file modification time: 1532622057 (26-jul-2018 13:20:57)
[20:37:47]          Stored file modification time : 1526467297 (16-mai-2018 07:41:37)

[20:37:48]   /bin/more                                       [ Warning ]
[20:37:48] Warning: The file properties have changed:
[20:37:49]          File: /bin/more
[20:37:49]          Current inode: 6424848    Stored inode: 6422546
[20:37:49]          Current file modification time: 1532622057 (26-jul-2018 13:20:57)
[20:37:49]          Stored file modification time : 1526467297 (16-mai-2018 07:41:37)
[20:37:49]   /bin/mount                                      [ Warning ]
[20:37:49] Warning: The file properties have changed:
[20:37:49]          File: /bin/mount
[20:37:49]          Current inode: 6422543    Stored inode: 6422539
[20:37:49]          Current file modification time: 1532622057 (26-jul-2018 13:20:57)
[20:37:49]          Stored file modification time : 1526467297 (16-mai-2018 07:41:37)

[20:38:50] Info: The minimum shared memory segment size to be checked (in bytes): 1048576 (1,0MB)
[20:38:50]   Checking for suspicious (large) shared memory segments [ Warning ]
[20:38:50] Warning: The following suspicious (large) shared memory segments have been found:
[20:38:50]          Process: /usr/bin/nautilus-desktop    PID: 2441    Owner: lcunha    Size: 128MB (configured size allowed: 1,0MB)
[20:38:50]          Process: /usr/lib/gnome-terminal/gnome-terminal-server    PID: 2706    Owner: lcunha    Size: 4,0MB (configured size allowed: 1,0MB)
[20:38:50]          Process: /usr/lib/firefox/firefox    PID: 7508    Owner: lcunha    Size: 7,6MB (configured size allowed: 1,0MB)
[20:38:50]          Process: /usr/lib/firefox/firefox    PID: 7508    Owner: lcunha    Size: 7,6MB (configured size allowed: 1,0MB)
[20:38:50]          Process: /usr/lib/firefox/firefox    PID: 7508    Owner: lcunha    Size: 2,8MB (configured size allowed: 1,0MB)
[20:38:50]          Process: /usr/lib/firefox/firefox    PID: 7508    Owner: lcunha    Size: 2,8MB (configured size allowed: 1,0MB)
[20:38:50]

[20:39:05]   Checking for hidden files and directories       [ Warning ]

[20:39:11] System checks summary
[20:39:11] =====================
[20:39:11]
[20:39:11] File properties checks...
[20:39:11] Files checked: 149
[20:39:11] Suspect files: 16
[20:39:11]
[20:39:11] Rootkit checks...
[20:39:11] Rootkits checked : 479
[20:39:11] Possible rootkits: 6
[20:39:11]
[20:39:11] Applications checks...
[20:39:12] All checks skipped
[20:39:12]
[20:39:12] The system checks took: 1 minute and 47 seconds
[20:39:12]
[20:39:12] Info: End date is sex out 26 20:39:12 -03 2018
[HR][/HR]
CHKROOTKIT:
[HR][/HR]
Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/usr/lib/debug/.build-id /usr/lib/jvm/.java-8-oracle.jinfo /usr/lib/jvm/java-8-oracle/lib/visualvm/profiler/.lastModified /usr/lib/jvm/java-8-oracle/lib/visualvm/platform/.lastModified /usr/lib/jvm/java-8-oracle/lib/visualvm/visualvm/.lastModified /usr/lib/jvm/java-8-oracle/lib/missioncontrol/p2/org.eclipse.equinox.p2.engine/profileRegistry/JMC.profile/.lock /usr/lib/jvm/java-8-oracle/lib/missioncontrol/p2/org.eclipse.equinox.p2.engine/profileRegistry/JMC.profile/.data /usr/lib/jvm/java-8-oracle/lib/missioncontrol/p2/org.eclipse.equinox.p2.engine/.settings /usr/lib/jvm/java-8-oracle/lib/missioncontrol/.eclipseproduct /usr/lib/python2.7/dist-packages/PyQt4/uic/widget-plugins/.noinit /usr/lib/python3/dist-packages/matplotlib/tests/baseline_images/.keep /usr/lib/python3/dist-packages/PyQt5/uic/widget-plugins/.noinit /lib/modules/4.15.0-36-generic/vdso/.build-id /lib/modules/4.15.0-38-generic/vdso/.build-id
/usr/lib/debug/.build-id /usr/lib/jvm/java-8-oracle/lib/missioncontrol/p2/org.eclipse.equinox.p2.engine/profileRegistry/JMC.profile/.data /usr/lib/jvm/java-8-oracle/lib/missioncontrol/p2/org.eclipse.equinox.p2.engine/.settings /lib/modules/4.15.0-36-generic/vdso/.build-id /lib/modules/4.15.0-38-generic/vdso/.build-id

Searching for anomalies in shell history files...           Warning: `//home/lcunha/.python-history' file size is zero

Checking `chkutmp'...                                        The tty of the following user process(es) were not found
 in /var/run/utmp !
! RUID          PID TTY    CMD
! gdm          1787 tty1   /usr/bin/Xwayland :1024 -rootless -terminate -accessx -core -listen 4 -listen 5 -displayfd 6
! gdm          1381 tty1   /usr/lib/gdm3/gdm-wayland-session gnome-session --autostart /usr/share/gdm/greeter/autostart
! gdm          1393 tty1   /usr/lib/gnome-session/gnome-session-binary --autostart /usr/share/gdm/greeter/autostart
! gdm          1462 tty1   /usr/bin/gnome-shell
! gdm          1852 tty1   /usr/lib/gnome-settings-daemon/gsd-a11y-settings
! gdm          1859 tty1   /usr/lib/gnome-settings-daemon/gsd-clipboard
! gdm          1860 tty1   /usr/lib/gnome-settings-daemon/gsd-color
! gdm          1863 tty1   /usr/lib/gnome-settings-daemon/gsd-datetime
! gdm          1864 tty1   /usr/lib/gnome-settings-daemon/gsd-housekeeping
! gdm          1867 tty1   /usr/lib/gnome-settings-daemon/gsd-keyboard
! gdm          1869 tty1   /usr/lib/gnome-settings-daemon/gsd-media-keys
! gdm          1872 tty1   /usr/lib/gnome-settings-daemon/gsd-mouse
! gdm          1873 tty1   /usr/lib/gnome-settings-daemon/gsd-power
! gdm          1876 tty1   /usr/lib/gnome-settings-daemon/gsd-print-notifications
! gdm          1878 tty1   /usr/lib/gnome-settings-daemon/gsd-rfkill
! gdm          1879 tty1   /usr/lib/gnome-settings-daemon/gsd-screensaver-proxy
! gdm          1881 tty1   /usr/lib/gnome-settings-daemon/gsd-sharing
! gdm          1886 tty1   /usr/lib/gnome-settings-daemon/gsd-smartcard
! gdm          1892 tty1   /usr/lib/gnome-settings-daemon/gsd-sound
! gdm          1895 tty1   /usr/lib/gnome-settings-daemon/gsd-wacom
! gdm          1846 tty1   /usr/lib/gnome-settings-daemon/gsd-xsettings
! gdm          1824 tty1   ibus-daemon --xim --panel disable
! gdm          1827 tty1   /usr/lib/ibus/ibus-dconf
! gdm          1907 tty1   /usr/lib/ibus/ibus-engine-simple
! gdm          1830 tty1   /usr/lib/ibus/ibus-x11 --kill-daemon
! lcunha       7565 tty2   /usr/lib/firefox/firefox -contentproc -childID 1 -isForBrowser -prefsLen 1 -prefMapSize 180077 -schedulerPrefs 0001,2 -parentBuildID 20181023214826 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/browser 7
! lcunha      21259 tty2   /usr/lib/firefox/firefox -contentproc -childID 11 -isForBrowser -prefsLen 5457 -prefMapSize 180077 -schedulerPrefs 0001,2 -parentBuildID 20181023214826 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/brows
! lcunha      21359 tty2   /usr/lib/firefox/firefox -contentproc -childID 12 -isForBrowser -prefsLen 5457 -prefMapSize 180077 -schedulerPrefs 0001,2 -parentBuildID 20181023214826 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/brows
! lcunha      22147 tty2   /usr/lib/firefox/firefox -contentproc -childID 14 -isForBrowser -prefsLen 5456 -prefMapSize 180077 -schedulerPrefs 0001,2 -parentBuildID 20181023214826 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/brows
! lcunha       7623 tty2   /usr/lib/firefox/firefox -contentproc -childID 2 -isForBrowser -prefsLen 133 -prefMapSize 180077 -schedulerPrefs 0001,2 -parentBuildID 20181023214826 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/browser
! lcunha       1994 tty2   /usr/lib/xorg/Xorg vt2 -displayfd 3 -auth /run/user/1000/gdm/Xauthority -background none -noreset -keeptty -verbose 3
! lcunha       2751 tty2   /usr/lib/deja-dup/deja-dup-monitor
! lcunha       7508 tty2   /usr/lib/firefox/firefox -new-window
! lcunha       1992 tty2   /usr/lib/gdm3/gdm-x-session --run-script env GNOME_SHELL_SESSION_MODE=ubuntu gnome-session --session=ubuntu
! lcunha       6531 tty2   gedit
! lcunha       2099 tty2   /usr/lib/gnome-session/gnome-session-binary --session=ubuntu
! lcunha       2240 tty2   /usr/bin/gnome-shell
! lcunha       2607 tty2   /usr/bin/gnome-software --gapplication-service
! lcunha       2378 tty2   /usr/lib/gnome-settings-daemon/gsd-a11y-settings
! lcunha       2379 tty2   /usr/lib/gnome-settings-daemon/gsd-clipboard
! lcunha       2380 tty2   /usr/lib/gnome-settings-daemon/gsd-color
! lcunha       2382 tty2   /usr/lib/gnome-settings-daemon/gsd-datetime
! lcunha       2466 tty2   /usr/lib/gnome-disk-utility/gsd-disk-utility-notify
! lcunha       2383 tty2   /usr/lib/gnome-settings-daemon/gsd-housekeeping
! lcunha       2385 tty2   /usr/lib/gnome-settings-daemon/gsd-keyboard
! lcunha       2389 tty2   /usr/lib/gnome-settings-daemon/gsd-media-keys
! lcunha       2392 tty2   /usr/lib/gnome-settings-daemon/gsd-mouse
! lcunha       2339 tty2   /usr/lib/gnome-settings-daemon/gsd-power
! lcunha       2340 tty2   /usr/lib/gnome-settings-daemon/gsd-print-notifications
! lcunha       2428 tty2   /usr/lib/gnome-settings-daemon/gsd-printer
! lcunha       2342 tty2   /usr/lib/gnome-settings-daemon/gsd-rfkill
! lcunha       2343 tty2   /usr/lib/gnome-settings-daemon/gsd-screensaver-proxy
! lcunha       2346 tty2   /usr/lib/gnome-settings-daemon/gsd-sharing
! lcunha       2359 tty2   /usr/lib/gnome-settings-daemon/gsd-smartcard
! lcunha       2360 tty2   /usr/lib/gnome-settings-daemon/gsd-sound
! lcunha       2364 tty2   /usr/lib/gnome-settings-daemon/gsd-wacom
! lcunha       2363 tty2   /usr/lib/gnome-settings-daemon/gsd-xsettings
! lcunha       2265 tty2   ibus-daemon --xim --panel disable
! lcunha       2273 tty2   /usr/lib/ibus/ibus-dconf
! lcunha       2487 tty2   /usr/lib/ibus/ibus-engine-simple
! lcunha       2275 tty2   /usr/lib/ibus/ibus-x11 --kill-daemon
! lcunha       2457 tty2   /usr/lib/x86_64-linux-gnu/indicator-application/indicator-application-service
! lcunha       2445 tty2   /usr/lib/x86_64-linux-gnu/indicator-messages/indicator-messages-service
! lcunha       2441 tty2   nautilus-desktop
! lcunha       2604 tty2   update-notifier
! lcunha       2565 tty2   zeitgeist-datahub
! lcunha       2717 pts/0  bash
! root         8142 pts/0  /bin/sh /usr/sbin/chkrootkit
! root         8809 pts/0  ./chkutmp
! root         8811 pts/0  ps axk tty,ruser,args -o tty,pid,ruser,args
! root         8810 pts/0  sh -c ps axk "tty,ruser,args" -o "tty,pid,ruser,args"

```

---

### Post by DuckHook on 2018-10-26
Welcome to the forums lbcunha1.

Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

Perhaps you misunderstand the use of tools like RKHunter and ChkRootKit. They are notorious for generating false positives. In fact, almost everything outputted is false positives. So unless you already have suspicions, asking forum members to parse through your output is no fairer than asking them to parse through, say, your 50-page commercial lease agreement. Anyone using these tools has to be prepared to devote hours or days into chasing down false positives and dead ends, which only you can do.

Do you have a specific reason for suspecting a root kit? If so, which app? Why? When? Then use these tools to help confirm/deny. You start from suspicions then use the tools as support; not start with the tools to raise further suspicions, because there is no limit to the suspicions that will be raised.

---

### Post by wyliecoyoteuk on 2018-10-27
Duckhook is right.

Unless you are running an internet exposed server, there is less reason to worry about Linux security than Windows.
If this is not the first time that you have run rkhunter, a lot of those may be due to updates.
You should always run 
```
sudo rkhunter --propupdate
```
After updating your system.

If you are worried, Lynis is a much more helpful tool for checking security.
If you run it it will highlight possible vulnerabilities and it will suggest ways of making your machine more secure.
```
sudo apt install lynis
sudo lynis audit system
```

---

### Post by lbcunha1 on 2018-10-27
DuckHook and wyliecoyoteuk Thanks by supporting me in this case.

The machine is used to host and improve VM (Virtual Machines). One the VM configuration is ok it is deployed as a VPS on public internet hosting providers. Then the answer is the system isn't exposed for public internet, but is exposed to the internal lan with some machines in Linux and Windows to simulate traffic and loading.

I have notice that several **.xxxx** files appears in the HD in **several folders**. It is the key point that starts the investigation. 

I have updated **RKhunter** and the results are:
```


/usr/bin/lwp-request                                     [ Warning ]
Checking for suspicious (large) shared memory segments   [ Warning ]
Checking for hidden files and directories                [ Warning ]

System checks summary
=====================

File properties checks...
    Files checked: 149
    Suspect files: 1

Rootkit checks...
    Rootkits checked : 479
    Possible rootkits: 4

```

As the Guys can see rkhunter has shown something in the aliened with the starting suspection: "Checking for hidden files and directories [ Warning ]"

The **Lynis** auditing has shown:

```


  * Check process listing for processes waiting for IO requests [PROC-3614] 
      https://cisofy.com/lynis/controls/PROC-3614/

  * Purge old/removed packages (187 found) with aptitude purge or dpkg --purge command. This will cleanup old configuration files, cron jobs and startup scripts. [PKGS-7346] 
      https://cisofy.com/lynis/controls/PKGS-7346/

  * Check what deleted files are still in use and why. [LOGG-2190] 
      https://cisofy.com/lynis/controls/LOGG-2190/

```

Regarding **Lynis**:
 
I have already cleaned up the cache and old pkg version. The apt has shown nothing to remove, but the audit has shown **187**.
The processes waiting would have something related to the CHKROOTKIT reporting several processes without tty?
The result: "Check what deleted files are still in use and why." would have something related to this amount of **.**files? I have never seen Deleted files in use.

Guys do you think that I have an issue related to system infected? If it is true, could you help me solve it?

Regards a thanks a lot!!!

---

### Post by wyliecoyoteuk on 2018-10-27
Check out the links in the lynis report, and the lynis logs.

To clean up all unwanted packages and config files:
[https://chr4.org/blog/2013/08/04/apt-get-cleanup-commands/](https://chr4.org/blog/2013/08/04/apt-get-cleanup-commands/)

There is certainly something going on, whether it is a root kit or not, I wouldn't know, but there seems to be a hung desktop session, have you tried a reboot?

---

