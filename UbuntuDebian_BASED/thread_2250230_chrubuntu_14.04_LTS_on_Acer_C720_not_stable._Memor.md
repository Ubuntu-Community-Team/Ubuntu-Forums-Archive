---
title: "chrubuntu 14.04 LTS on Acer C720 not stable. Memory problem?"
date: 2014-10-27
forum: Ubuntu/Debian BASED
---

### Post by jbeale on 2014-10-27
I have Chrubuntu (Ubuntu 14.04 LTS) on an Acer C720 which runs OK for a few days, and then locks up, often when I am not actively using it. The system is on a firewalled LAN, not directly on the internet and it is always up, not sleeping. There is a remote ssh session that connects and transfers a large file through USB2 ethernet device (Asix AX88772) to a USB3 HDD. That happens every 30 seconds, running 24/7. There is apache2 running but not actively serving any pages, and that's basically it besides the standard daemons.  How would I go about debugging this?

```
user@chrubuntu:~$ uname -a
Linux chrubuntu 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```
I see this in /var/log/syslog :
```
Oct 27 08:00:14 chrubuntu kernel: [256877.165939] Core dump to |/usr/share/apport/apport 1986 7 0 1986 pipe failed
Oct 27 08:00:14 chrubuntu gnome-session[1684]: WARNING: Child process 1986 was already dead.
Oct 27 08:00:14 chrubuntu gnome-session[1684]: WARNING: Application 'compiz.desktop' killed by signal 7
Oct 27 08:00:14 chrubuntu gnome-session[1684]: WARNING: App 'compiz.desktop' respawning too quickly
Oct 27 08:00:14 chrubuntu gnome-session[1684]: CRITICAL: We failed, but the fail whale is dead. Sorry....

```
/var/log/apport.log is empty but I see this in /var/log/apport.log.1 :
```
ERROR: apport (pid 12758) Thu Oct 23 22:40:23 2014: called for pid 12633, signal 6, core limit 0
ERROR: apport (pid 12758) Thu Oct 23 22:40:23 2014: executable: /usr/lib/chromium-browser/chromium-browser (command line "chromium-browser\ --enable-pinch")
ERROR: apport (pid 12758) Thu Oct 23 22:40:23 2014: debug: session gdbus call: (true,)

ERROR: apport (pid 12758) Thu Oct 23 22:40:32 2014: wrote report /var/crash/_usr_lib_chromium-browser_chromium-browser.1000.crash
ERROR: apport (pid 17343) Fri Oct 24 05:08:58 2014: called for pid 1017, signal 11, core limit 18446744073709551615
ERROR: apport (pid 17343) Fri Oct 24 05:08:58 2014: ignoring implausibly big core limit, treating as unlimited
ERROR: apport (pid 17343) Fri Oct 24 05:08:58 2014: executable: /usr/bin/Xorg (command line "/usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch")
ERROR: apport (pid 17343) Fri Oct 24 05:08:58 2014: is_closing_session(): no DBUS_SESSION_BUS_ADDRESS in environment
ERROR: apport (pid 17343) Fri Oct 24 05:09:07 2014: wrote report /var/crash/_usr_bin_Xorg.0.crash

```
I also see that /var/crash/ contains:
```
-rw-r-----  1 root     whoopsie 8619674 Oct 24 07:03 _usr_bin_Xorg.0.crash
-rw-r--r--  1 root     whoopsie       0 Oct 24 07:03 _usr_bin_Xorg.0.upload
-rw-------  1 whoopsie whoopsie       0 Oct 24 07:04 _usr_bin_Xorg.0.uploaded
-rw-r-----  1 user     whoopsie   56296 Oct 27 07:52 _usr_bin_update-manager.1000.crash
-rw-r-----  1 user     whoopsie  123346 Oct 23 22:40 _usr_lib_chromium-browser_chromium-browser.1000.crash

```
The most recent crash log, from Oct. 27 ends with:
```
PythonArgs: ['/usr/bin/update-manager', '--no-update', '--no-focus-on-map']
Traceback:
 Traceback (most recent call last):
   File "/usr/bin/update-manager", line 114, in <module>
     app = UpdateManager(data_dir, options)
   File "/usr/lib/python3/dist-packages/UpdateManager/UpdateManager.py", line 113, in __init__
     self.options and self.options.use_proposed)
   File "/usr/lib/python3/dist-packages/UpdateManager/MetaReleaseGObject.py", line 44, in __init__
     MetaReleaseCore.__init__(self, useDevelopmentRelease, useProposed)
   File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 96, in __init__
     self.current_dist_name = get_dist()
   File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 221, in get_dist
     universal_newlines=True)
   File "/usr/lib/python3.4/subprocess.py", line 848, in __init__
     restore_signals, start_new_session)
   File "/usr/lib/python3.4/subprocess.py", line 1384, in _execute_child
     restore_signals, start_new_session, preexec_fn)
 OSError: [Errno 12] Cannot allocate memory
UserGroups: adm sudo
_LogindSession: /user/1000.user/c2.session

```
so it is out of memory? How can I avoid that?  When I run 'top' the largest process I ever see is "compiz" taking 3.7% of memory, and normally top shows the free memory between around 121000 to 162000 kbytes free.  Watching 'htop' for awhile I see Mem: 683/1875 MB up to 725/1875 MB.
```

top - 10:32:57 up  1:28,  5 users,  load average: 0.25, 0.21, 0.25
Tasks: 215 total,   2 running, 213 sleeping,   0 stopped,   0 zombie
%Cpu(s):  7.1 us,  2.4 sy,  0.0 ni, 90.2 id,  0.0 wa,  0.0 hi,  0.3 si,  0.0 st
KiB Mem:   1920844 total,  1794124 used,   126720 free,    15860 buffers
KiB Swap:        0 total,        0 used,        0 free.  1102460 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
23239 pi        20   0  109928   2048    996 S  14.9  0.1   0:02.05 sshd
23240 pi        20   0   12816    792    660 S   2.0  0.0   0:00.25 scp
 2642 user      20   0  426116   5772   2928 S   1.3  0.3   0:37.55 gvfsd-trash
    3 root      20   0       0      0      0 S   0.7  0.0   0:15.50 ksoftirqd/0
 2522 user      20   0 1495636  70824  21272 S   0.3  3.7   0:16.50 compiz
...

```

---

### Post by howefield on 2014-10-27
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

