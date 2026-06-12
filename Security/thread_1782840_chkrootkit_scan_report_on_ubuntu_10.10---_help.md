---
title: "chkrootkit scan report on ubuntu 10.10--- help"
date: 2011-06-15
forum: Security
---

### Post by karthik.k.nair on 2011-06-15
recently i scanned my Ubuntu desktop 10.10 for rootkits with chkrootkit software and its showing a suspicious files i m posting my scan results below pls anyone check it out and find is there anything really suspicious 
```

$ sudo chkrootkit
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
Checking `rpcinfo'...                                       not infected
Checking `rlogind'...                                       not found
Checking `rshd'...                                          not found
Checking `slogin'...                                        not infected
Checking `sendmail'...                                      not infected
Checking `sshd'...                                          not found
Checking `syslogd'...                                       not tested
Checking `tar'...                                           not infected
Checking `tcpd'...                                          not infected
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
Searching for suspicious files and dirs, it may take a while...[/COLOR] [COLOR=Red]The following suspicious files and directories were found:  
/usr/lib/xulrunner-1.9.2.17/.autoreg /usr/lib/jvm/java-6-sun-1.6.0.24/.systemPrefs /usr/lib/jvm/.java-6-sun.jinfo /usr/lib/jvm/.java-6-openjdk.jinfo /usr/lib/firefox-3.6.17/.autoreg /usr/lib/eclipse/plugins/org.eclipse.pde.build_3.5.2.R35x_20100114/.options /usr/lib/eclipse/plugins/org.eclipse.pde.build_3.5.2.R35x_20100114/.api_description /usr/lib/eclipse/plugins/org.eclipse.ui.intro.universal_3.2.300.v20090526/.options /usr/lib/eclipse/plugins/org.eclipse.ui.intro.universal_3.2.300.v20090526/.api_description /usr/lib/eclipse/plugins/org.eclipse.core.runtime.compatibility.registry_3.2.200.v20090429-1800/.api_description /usr/lib/eclipse/plugins/org.eclipse.jdt.debug_3.5.0.v20090526/.api_description /usr/lib/eclipse/plugins/org.eclipse.ui.workbench.compatibility_3.2.0.I20090429-1800/.api_description /usr/lib/eclipse/p2/org.eclipse.equinox.p2.engine/.settings /usr/lib/eclipse/p2/org.eclipse.equinox.p2.engine/profileRegistry/PlatformProfile.profile/.data /usr/lib/eclipse/p2/org.eclipse.equinox.p2.engine/profileRegistry/PlatformProfile.profile/.lock /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/28/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/177/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/14/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/73/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/80/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/15/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/126/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/77/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/67/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/32/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/96/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/76/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/31/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/105/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/63/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/129/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/146/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/75/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/.state.2 /usr/lib/eclipse/configuration/org.eclipse.osgi/.bundledata.3 /usr/lib/eclipse/configuration/org.eclipse.osgi/.lazy.2 /usr/lib/eclipse/configuration/org.eclipse.osgi/.manager /usr/lib/eclipse/configuration/org.eclipse.osgi/.manager/.fileTableLock /usr/lib/eclipse/configuration/org.eclipse.osgi/.manager/.fileTable.8 /usr/lib/eclipse/configuration/org.eclipse.osgi/.manager/.fileTable.7 /usr/lib/eclipse/.eclipseproduct /usr/lib/pymodules/python2.6/PyQt4/uic/widget-plugins/.noinit /usr/lib/pymodules/python2.6/.path
/usr/lib/eclipse/p2/org.eclipse.equinox.p2.engine/.settings /usr/lib/eclipse/p2/org.eclipse.equinox.p2.engine/profileRegistry/PlatformProfile.profile/.data /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/28/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/177/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/14/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/73/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/80/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/15/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/126/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/77/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/67/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/32/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/96/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/76/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/31/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/105/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/63/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/129/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/146/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/bundles/75/1/.cp /usr/lib/eclipse/configuration/org.eclipse.osgi/.manager[/COLOR]
[COLOR=DarkGreen]Searching for LPD Worm files and dirs...                    nothing found
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
Searching for suspect PHP files...                          nothing found
Searching for anomalies in shell history files...           nothing found
Checking `asp'...                                           not infected
Checking `bindshell'...                                     not infected
Checking `lkm'...                                           chkproc: nothing detected
chkdirs: nothing detected
Checking `rexedcs'...                                       not found
Checking `sniffer'...                                       lo: not promisc and no packet sniffer sockets
vboxnet0: not promisc and no packet sniffer sockets
Checking `w55808'...                                        not infected   x  
Checking `wted'...                                          chkwtmp: nothing deleted
Checking `scalper'...                                       not infected
Checking `slapper'...                                       not infected
Checking `z2'...                                            user xxxx deleted or never logged from lastlog!
user guest deleted or never logged from lastlog!
Checking `chkutmp'...                                       chkutmp: nothing deleted
Checking `OSX_RSPLUG'...                                    not infected

```

---

### Post by mikewhatever on 2011-06-15
Regardless of how suspicious Sun java is, you should update 1.6.0.24 to 1.6.0.26.
[http://www.h-online.com/security/news/item/Oracle-patches-critical-Java-security-vulnerabilities-1256382.html](http://www.h-online.com/security/news/item/Oracle-patches-critical-Java-security-vulnerabilities-1256382.html)

---

### Post by kimda on 2011-06-15
Looks like a false positive. You can also run rkhunter to see if it finds anything. 

If you want to run chkrootkit to only show possible errors run i t like this. 
```
sudo chkrootkit -q
```

---

### Post by linuxonbute on 2011-06-15
I have had my gmail account hacked but now seems to be ok. Ran chkrootkit and rkhunter.

chkrootkit said:
/usr/lib/xulrunner-1.9.2.17/.autoreg /usr/lib/jvm/java-6-sun-1.6.0.24/lib/visualvm/visualvm/.lastModified /usr/lib/jvm/java-6-sun-1.6.0.24/lib/visualvm/platform/.lastModified /usr/lib/jvm/java-6-sun-1.6.0.24/lib/visualvm/profiler/.lastModified /usr/lib/jvm/java-6-sun-1.6.0.24/.systemPrefs /usr/lib/jvm/.java-6-openjdk.jinfo /usr/lib/jvm/.java-6-sun.jinfo /usr/lib/firefox-3.6.17/.autoreg /usr/lib/pymodules/python2.6/.path

wlan0: PACKET SNIFFER(/sbin/wpa_supplicant[1141], /sbin/dhclient3[16510])
user norman deleted or never logged from lastlog!


and rkhunter:
 Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

and from rkhunter.log:
[20:45:32] /bin/egrep                                        [ OK ]
[20:45:32] Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[20:45:32] /bin/fgrep                                        [ OK ]
[20:45:32] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check
plus various others whitelisted 

 Performing filesystem checks
[20:31:11] Info: Starting test name 'filesystem'
[20:31:11] Info: SCAN_MODE_DEV set to 'THOROUGH'
[20:31:11]   Checking /dev for suspicious file types         [ Warning ]
[20:31:11] Warning: Suspicious file types found in /dev:
[20:31:11]          /dev/shm/pulse-shm-4045762719: data
[20:31:11]          /dev/shm/pulse-shm-2066612898: data
[20:31:11]          /dev/shm/pulse-shm-2042531880: data
[20:31:11]          /dev/shm/pulse-shm-767485232: data
[20:31:11]          /dev/shm/pulse-shm-51730790: data
[20:31:11]          /dev/shm/pulse-shm-3236142999: data
[20:31:11]          /dev/shm/pulse-shm-2902958564: data
[20:31:12]   Checking for hidden files and directories       [ Warning ]
[20:31:12] Warning: Hidden directory found: /etc/.java
[20:31:12] Warning: Hidden directory found: /dev/.udev
[20:31:12] Warning: Hidden directory found: /dev/.initramfs


I have seen the post about Java and will update it but I wonder about the others.
Any comments welcome

---

### Post by uRock on 2011-06-15
You will see an warning every time a software gets upgraded when using rkhunter and chrootkit.

Moved to Security Discussions.

---

### Post by linuxonbute on 2011-06-15
> **uRock said:**
> You will see an warning every time a software gets upgraded when using rkhunter and chrootkit.

  
So do I just ignore them?
And what about this bit?
[20:31:12]   Checking for hidden files and directories       [ Warning ]
[20:31:12] Warning: Hidden directory found: /etc/.java
[20:31:12] Warning: Hidden directory found: /dev/.udev
[20:31:12] Warning: Hidden directory found: /dev/.initramfs

---

### Post by uRock on 2011-06-15
> **linuxonbute said:**
> So do I just ignore them?
And what about this bit?
[20:31:12]   Checking for hidden files and directories       [ Warning ]
[20:31:12] Warning: Hidden directory found: /etc/.java
[20:31:12] Warning: Hidden directory found: /dev/.udev
[20:31:12] Warning: Hidden directory found: /dev/.initramfs

initramfs gets updated with every set up updates and the other two were most likely part of a recent update.

---

### Post by linuxonbute on 2011-06-15
Great thanks for the help.

---

### Post by fonsi2099 on 2011-09-05
Now I need some help!!
after  I run: $ sudo chkrootkit -q
I get that PACKET SNIFFER ??

/usr/lib/jvm/.java-6-openjdk.jinfo /usr/lib/pymodules/python2.6/.path /usr/lib/pymodules/python2.6/PyQt4/uic/widget-plugins/.noinit /usr/lib/pymodules/python2.7/.path /usr/lib/pymodules/python2.7/PyQt4/uic/widget-plugins/.noinit

wlan0: PACKET SNIFFER(/sbin/wpa_supplicant[1345], /sbin/dhclient[1552])
user fonsi deleted or never logged from lastlog!

WHAT CAN I DO NOW?
MANY THANKS FOR YOUR HELP!

---

