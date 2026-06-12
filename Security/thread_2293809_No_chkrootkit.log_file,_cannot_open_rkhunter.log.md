---
title: "No chkrootkit.log file, cannot open rkhunter.log"
date: 2015-09-07
forum: Security
---

### Post by david434 on 2015-09-07
I just installed 15.04 amd-64.   ___________________________________________________This is what chkrootkit -q showed:  root@Computer99:~# chkrootkit -q  /usr/lib/python2.7/dist-packages/PyQt4/uic/widget-plugins/.noinit /lib/modules/3.19.0-15-generic/vdso/.build-id /lib/modules/3.19.0-26-generic/vdso/.build-id /lib/modules/3.19.0-15-generic/vdso/.build-id /lib/modules/3.19.0-26-generic/vdso/.build-id eth0: PACKET SNIFFER(/sbin/dhclient (deleted)[835]) user milo deleted or never logged from lastlog!  The tty of the following user process(es) were not found  in /var/run/utmp ! ! RUID          PID TTY    CMD ! root          859 tty7   /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch   _______________________________________________________________________________________________ 1) There is no chkrootkit log file  ______________________________________2) I cannot open the rkhunter.log file   _______________________________________ 3)  Unhide -v chksysinfo gives:  root@Computer99:~# unhide -v checksysinfo Unhide 20121229 Copyright © 2012 Yago Jesus & Patrick Gouin License GPLv3+*: GNU GPL version 3 or later [http://www.unhide-forensics.info](http://www.unhide-forensics.info)  NOTE : This version of unhide is for systems using Linux >= 2.6   Used options: verbose    
[*]Searching for Hidden processes through sysinfo() scanning  		WARNING : info.procs changed during test : 447 (was 445) 		WARNING : info.procs changed during test : 445 (was 447) 	1 HIDDEN Processes Found	sysinfo.procs reports 445 processes and ps sees 446 processes root@Computer99:~#     _________________________________________________________________Questions:   1) am I owned?      2)  how do I find the hidden process?  I am in Thailand, and last year I saw that updating Ubuntu from here made DNS poisoning begin.  So today I used a VPN into Europe to download the iso, verified the SHA256 and MD5, and had better luck that before getting rkhunter, clamav, and chkrootkit to work.  But still, I have one bad guy inside my machine, I bet.   Lastly)  is there a better product for scanning for rootkits on my OS?  Thank you!

---

### Post by david434 on 2015-09-08
How can I open my locked RKhunter file? ........................................................................At least it is there.

---

### Post by david434 on 2015-09-08
Results of unhide: 

```
Searching for Hidden processes through sysinfo() scanning
WARNING : info.procs changed during test : 447 (was 445)
        WARNING : info.procs changed during test : 445 (was 447)
    1 HIDDEN Processes Found    sysinfo.procs reports 445 processes and ps sees 446 processes
```

How can I find and eliminate this hidden process?...............................................................................................................................................................

---

### Post by david434 on 2015-09-08
/usr/lib/python2.7/dist-packages/PyQt4/uic/widget-plugins/.noinit 
/lib/modules/3.19.0-15-generic/vdso/.build-id /lib/modules/3.19.0-26-generic/vdso/.build-id
/lib/modules/3.19.0-15-generic/vdso/.build-id /lib/modules/3.19.0-26-generic/vdso/.build-id

---

### Post by patlkli on 2015-09-08
They are most probably false-positives.

Chkrootkit reports all hidden files (filenames starting with a dot) in /usr/lib, /usr/man and /lib.
There usually aren't that many hidden files in those directories, but there are *some*.

The first is [shipped in python-qt4]("http://packages.ubuntu.com/vivid/amd64/python-qt4/filelist").
The others are [part of the kernel image packages]("http://packages.ubuntu.com/vivid/amd64/linux-image-3.19.0-15-generic/filelist").

Also, if you look, the first file is even empty, so I'm pretty sure, there's nothing dangerous there.

---

### Post by patlkli on 2015-09-08
Did you try running unhide again? Are the results reproducable?

Again, considering [one of your other threads]("http://ubuntuforums.org/showthread.php?t=2293809"), I can tell you that it's not trivial to infiltrate an Ubuntu system, especially if you've hash-checked your installation image.

First thing, stop working in a root shell all the time.
It's a good thing to use sudo most of the time, because it's a constant reminder, that you're doing things with system-wide permissions.
When you're working in a root shell, it's IMHO much easier to forget that you're root and run commands which shouldn't be run as root.

The APT update process is pretty secure, since the package lists and the packages itself are GPG signed.
So even if someone interfered in your connection to the update servers (maybe using a MITM attack), your system would detect a mismatch in the signatures of the compromised packages.

It's good that you're wary of potential security threats, but the things you've reported in your various threads over the last hours present no real danger to the integrity of your system.

Also see my answer(s) on your other threads for explanations of the results you've encountered.

---

### Post by slickymaster on 2015-09-08
Threads merged.

Please do not create multiple threads, it dilutes the community&#8217;s efforts to provide support and causes confusion.

---

### Post by Habitual on 2015-09-08
I typically use directives like these in /etc/rkhunter.conf (and a Good Read, so PLEASE DO)
```
 ALLOWDEVFILE=/dev/.udev/rules.d/root.rules
ALLOWHIDDENDIR=/etc/.java
ALLOWHIDDENDIR=/etc/.udev
ALLOWHIDDENFILE=/dev/.initramfs
SCRIPTWHITELIST=/usr/sbin/adduser
SCRIPTWHITELIST=/usr/bin/ldd
SCRIPTWHITELIST=/usr/bin/lwp-request
SCRIPTWHITELIST=/bin/which
APP_WHITELIST="openssl:1.0.1f gpg:1.4.11 sshd:5.9p1"


```

You can test the config
```
rkhunter --config-check
```
You can write a log anywhere using
```
rkhunter -c -sk -l /path/to/file.log
```

chrootkit? meh, don't use it. Not updated enough. </opinion>
chkrootkit 0.49 is now available! (Release Date: Thu Jul 30 2009)
chkrootkit 0.50 is now available! (Release Date: Wed Jun 4 2014)

unhide warnings from rkhunter are a non-issue. Happens on brand spanking new systems with rkhunter's default.conf
Once you are certain as can be your system (I wouldn't include chkrootkit results in this decision) is ok as it is, run
```
rkhunter --propupd
```
then re-run
```
rkhunter -c -sk -l /path/to/file.log
```
check the output for "Warning:" messages.

Let us know.

---

### Post by david434 on 2015-09-08
Thanks for your reply.  I don't often work in a root shell, but I did here.

Yes, the results are reproducible.

---

### Post by david434 on 2015-09-08
I appreciate your help here.  I'll run those commands.

---

### Post by david434 on 2015-09-08
Good!  I made a new log file in a new location for rkhunter.  Rkhunter came up clean, but I cannot open the file.  It says I do not have permissions.

(There was one warning under "checking for prerequisites")

So how do I make a file for which I have permission to open it?

---

### Post by david434 on 2015-09-08
Let me tell you something:  Ubuntu already provides enough confusion, and so I agree with you totally.

Next time I'll stick to one problem.  This is my first time here.

---

### Post by Habitual on 2015-09-08
Show me the exact command you used please.

---

### Post by patlkli on 2015-09-08
Please also check the permissions of the log file with ```
ls -l /path/to/rkhunter.log
```

You should be able to give yourself read permissions on the file with ```
sudo chmod +r /path/to/rkhunter.log
```

---

### Post by david434 on 2015-09-09
```


     ls -l /path/to/rkhunter.log
          sudo chmod +r /path/to/rkhunter.log


```



@patlkli
Thank you!  I was able to open my rkhunter log file with the code you provided above.

Here are the interesting results:

Checking /dev for suspicious file types         [ Warning ]
[00:04:35] Warning: Suspicious file types found in /dev:
[00:04:35]          /dev/shm/pulse-shm-1756028082: data
[00:04:35]          /dev/shm/pulse-shm-2258500333: data
[00:04:35]          /dev/shm/pulse-shm-3125172509: data
[00:04:35]          /dev/shm/pulse-shm-41493610: data
[00:04:35]          /dev/shm/pulse-shm-3070563570: data
[00:04:35]          /dev/shm/ecryptfs-milo-Private: ASCII text
[00:04:35]          /dev/shm/pulse-shm-870582922: data
[00:04:35]          /dev/shm/pulse-shm-1029997964: data
[00:04:35]   Checking for hidden files and directories       [ Warning ]
[00:04:35] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'

and

Performing malware checks
[00:04:24]
[00:04:24] Info: Test 'deleted_files' disabled at users request.
[00:04:24]
[00:04:24] Info: Starting test name 'running_procs'
[00:04:27]   Checking running processes for suspicious files [ None found ]
[00:04:27]
[00:04:27] Info: Test 'hidden_procs' disabled at users request.
[00:04:27]
[00:04:27] Info: Test 'suspscan' disabled at users request.


and


[00:04:35] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'


So, what do you people think?  Are these results a matter of concern?  Thanks.  I am learning.  Every little bit is encouraging.

---

### Post by patlkli on 2015-09-09
> **david434 said:**
> 
Checking /dev for suspicious file types         [ Warning ]
[00:04:35] Warning: Suspicious file types found in /dev:
[00:04:35]          /dev/shm/pulse-shm-1756028082: data
[00:04:35]          /dev/shm/pulse-shm-2258500333: data
[00:04:35]          /dev/shm/pulse-shm-3125172509: data
[00:04:35]          /dev/shm/pulse-shm-41493610: data
[00:04:35]          /dev/shm/pulse-shm-3070563570: data
[00:04:35]          /dev/shm/ecryptfs-milo-Private: ASCII text
[00:04:35]          /dev/shm/pulse-shm-870582922: data
[00:04:35]          /dev/shm/pulse-shm-1029997964: data
[00:04:35]   Checking for hidden files and directories       [ Warning ]
[00:04:35] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'


RKHunter reports pretty much everything in /dev as suspicious, what's not standardized.

All those pulse-shm-* files are shared memory files of the PulseAudio sound server.
The ecryptfs-*-Private file is the file in which ecryptfs manages when to re-encrypt the filesystem.

Both of them are not a security concern. You can whitelist them in your /etc/rkhunter.conf using:
```

ALLOWDEVFILE=/dev/shm/pulse-shm-*
ALLOWDEVFILE=/dev/shm/ecryptfs-*

```

In fact if you search for ALLOWDEVFILE in /etc/rkhunter.conf, you will find, that the pulse-shm-* whitelist is actually already there as a suggestion.

> **david434 said:**
> 
Performing malware checks
[00:04:24]
[00:04:24] Info: Test 'deleted_files' disabled at users request.
[00:04:24]
[00:04:24] Info: Starting test name 'running_procs'
[00:04:27]   Checking running processes for suspicious files [ None found ]
[00:04:27]
[00:04:27] Info: Test 'hidden_procs' disabled at users request.
[00:04:27]
[00:04:27] Info: Test 'suspscan' disabled at users request.


These are the tests which are disabled in the default rkhunter.conf from the repository.
If you wish to enable them, please search for DISABLE_TESTS in the configuration and read the comment sections above it.
Those will explain why (at least some of) the tests are disabled by default.

> **david434 said:**
> 
[00:04:35] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'


Another non-standardized file/symlink in /dev, but nothing to worry about. You can whitelist it using:
```

ALLOWHIDDENFILE="/dev/.initramfs"

```

> **david434 said:**
> 
So, what do you people think? Are these results a matter of concern? Thanks. I am learning. Every little bit is encouraging.


I'm pretty sure, nothing of this presents any security issue.
If you still have any questions about all of this, feel free to ask.

---

### Post by Habitual on 2015-09-09
> **david434 said:**
> So, what do you people think?  Are these results a matter of concern?  Thanks.  I am learning.  Every little bit is encouraging.
Everything is covered in /etc/rkhunter.conf # See comments there. 
Ask about them here.
I covered some exclusions at [http://ubuntuforums.org/showthread.php?t=2293809&p=13352475#post13352475](http://ubuntuforums.org/showthread.php?t=2293809&p=13352475#post13352475)

---

### Post by david434 on 2015-09-10
Thank Patlkli and Habitual for your help.  I will read Habitual's article on exclusions.  And I see I need to do some whitelisting.  Very good.  I feel a lot better about my Ubuntu OS.

---

### Post by Habitual on 2015-09-10
You are very welcome.

---

