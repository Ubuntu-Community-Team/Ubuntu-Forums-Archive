---
title: "Rootkit scans"
date: 2015-08-16
forum: Security
---

### Post by jammydodger2 on 2015-08-16
Hi All 
I am a relative new user and didnt have the firewall activated for at least a year
after running chkroot the results came back with these results 

```
Checking `chkutmp'... 
 The tty of the following user process(es) were not found
 in /var/run/utmp !
! RUID          PID TTY    CMD
! root         1670 tty7   /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
chkutmp: nothing deleted
```

sudo less rkhunter.log
This doesnt show up on Rkhunter scan but does on chkrootkit

Searching for Suckit rootkit...    Warning: /sbin/init INFECTED

and 

Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/usr/lib/python2.7/dist-packages/PyQt4/uic/widget-plugins/.noinit /usr/lib/jvm/.java-1.7.0-openjdk-amd64.jinfo


```
on rkhunter

Info: Found file '/usr/sbin/adduser': it is whitelisted for the 'script replacement' check.
Info: Found file '/usr/bin/ldd': it is whitelisted for the 'script replacement' check.
Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
Info: Found file '/bin/egrep': it is whitelisted for the 'script replacement' check.
[16:18:43]   /bin/fgrep [ OK ]
[16:18:44] Info: Found file '/bin/fgrep': it is whitelisted for the 'script replacement' check
.Info: Found file '/bin/which': it is whitelisted for the 'script replacement' check.
Info: Starting test name 'filesystem'
[16:19:48] Performing filesystem checks
[16:19:48] Info: SCAN_MODE_DEV set to 'THOROUGH'
[16:19:48]   Checking /dev for suspicious file types         [ Warning ]
[16:19:48] Warning: Suspicious file types found in /dev:
[16:19:48]          /dev/.udev/rules.d/root.rules: ASCII text
```

```
/usr/bin/unhide.rb    
 [ Warning ]
[16:18:39] Warning: The command '/usr/bin/unhide.rb' has been replaced by a scri
pt: /usr/bin/unhide.rb: Ruby script, ASCII text

Info: Starting test name 'hidden_ports'
[16:19:46] Checking for hidden ports                         [ Skipped ]
[16:19:46] Info: Unable to find the 'unhide-tcp' command

Warning: Hidden directory found: '/etc/.java: directory '
[16:19:48] Warning: Hidden directory found: '/dev/.udev: directory '
[16:19:48] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/i
nitramfs' 
```

 I have checked a few of these and some other users have come back as saying they are false positive given by scan


This one came back after Google search with no results Chkrootkit

Checking `chkutmp'... 
 The tty of the following user process(es) were not found
 in /var/run/utmp !
! RUID          PID TTY    CMD
! root         1670 tty7   /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
chkutmp: nothing deleted

Any help would be appreciated , with hindsight I should have been more security conscious from the start 
JD

---

