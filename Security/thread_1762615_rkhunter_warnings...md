---
title: "rkhunter warnings.."
date: 2011-05-19
forum: Security
---

### Post by lmn. on 2011-05-19
ran a rootkit hunter scan and there appears to be some problems with my pc. 

wondering if you could give any advice on how to fix any or all of what is wrong..?


[FONT=Courier New][15:38:43] Running Rootkit Hunter version 1.3.6 on v350
[
**[15:38:55] /usr/bin/awk                                      [ Warning ]**
[15:38:55] Warning: The file properties have changed:
[15:38:55]          File: /usr/bin/awk
[15:38:55]          Current hash: f6cd9975fff42a8e4e8336e3f930661d054574a1
[15:38:55]          Stored hash : 446f58c392a11b6c5fa34db845ea666a98b1903c
[15:38:55]          Current inode: 4204698    Stored inode: 4194385
[15:38:55]          Current file modification time: 1305712882 (18-May-2011 11:01:22)
[15:38:55]          Stored file modification time : 1305242621 (13-May-2011 00:23:41)

**[15:38:58] /usr/bin/lynx                                     [ Warning ]**
[15:38:58] Warning: The file '/usr/bin/lynx' exists on the system, but it is not present in the rkhunter.dat file.
**[15:38:58] /usr/bin/mail                                     [ Warning ]**
[15:38:58] Warning: The file '/usr/bin/mail' exists on the system, but it is not present in the rkhunter.dat file.
**[15:38:59] /usr/bin/rpm                                      [ Warning ]**
[15:38:59] Warning: The file '/usr/bin/rpm' exists on the system, but it is not present in the rkhunter.dat file.
**[15:39:02] /usr/bin/gawk                                     [ Warning ]**
[15:39:02] Warning: The file '/usr/bin/gawk' exists on the system, but it is not present in the rkhunter.dat file.
[15:39:03] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
**[15:39:03] /usr/bin/lynx.cur                                 [ Warning ]**
[15:39:03] Warning: The file '/usr/bin/lynx.cur' exists on the system, but it is not present in the rkhunter.dat file.
**[15:39:03] /usr/bin/bsd-mailx                                [ Warning ]**
[15:39:03] Warning: The file '/usr/bin/bsd-mailx' exists on the system, but it is not present in the rkhunter.dat file.

**[15:40:35]   Checking if SSH root access is allowed          [ Warning ]**
[15:40:35] Warning: The SSH and rkhunter configuration options should be the same:
[15:40:35]          SSH configuration option 'PermitRootLogin': yes
[15:40:35]          Rkhunter configuration option 'ALLOW_SSH_ROOT_USER': no
[15:40:35]   Checking if SSH protocol v1 is allowed          [ Not allowed ]
[15:40:35]   Checking for running syslog daemon              [ Found ]
[15:40:35]   Checking if syslog remote logging is allowed    [ Not allowed ]
[15:40:35] Performing filesystem checks
[15:40:35] Info: Starting test name 'filesystem'
[15:40:35] Info: SCAN_MODE_DEV set to 'THOROUGH'
**[15:40:36]   Checking /dev for suspicious file types         [ Warning ]**
[15:40:36] Warning: Suspicious file types found in /dev:
[15:40:36]          /dev/shm/pulse-shm-2621805882: data
[15:40:36]          /dev/shm/pulse-shm-2560764816: data
[15:40:36]          /dev/shm/pulse-shm-713018387: data
[15:40:36]          /dev/shm/pulse-shm-2774999103: data
[15:40:36]   Checking for hidden files and directories       [ Warning ]
[15:40:36] Warning: Hidden directory found: /etc/.java
[15:40:37] Warning: Hidden directory found: /dev/.udev
[15:40:37] Warning: Hidden directory found: /dev/.initramfs
[15:40:41]
[15:40:41] Info: Test 'apps' disabled
[15:40:41]
[15:40:41] System checks summary
[15:40:41] =====================
[15:40:41]
[15:40:41] File properties checks...
[15:40:41] Files checked: 135
**[15:40:41] Suspect files: 7**
[15:40:41]
[15:40:41] Rootkit checks...
[15:40:41] Rootkits checked : 245
[15:40:41] Possible rootkits: 0
[15:40:41]
[15:40:41] Applications checks...
[15:40:41] All checks skipped
[15:40:41]
[15:40:41] The system checks took: 1 minute and 57 seconds
[15:40:41]
[15:40:41] Info: End date is Thu May 19 15:40:41 BST 2011[/FONT]


apparently not infected, but I don't want to leave my system vulnerable.

Does anyone know if these problems pose a threat, and if they do, how can they be fixed?

cheers


*maybe this should be in general help..

---

### Post by spynappels on 2011-05-19
It is dangerous to use tools like rkhunter et al when a) you have no baseline to compare it with, and b) you are unclear what the results are and what the common false positives are.

Did you have good reason to suspect the presence of a rootkit? What appear to be problems are not really issues, just that some mail handling agents have been installed, possibly as part of a dependencies install and that there are some hidden files in your /dev directory.

---

### Post by lmn. on 2011-05-19
> **spynappels said:**
> It is dangerous to use tools like rkhunter et al when a) you have no baseline to compare it with, and b) you are unclear what the results are and what the common false positives are.

Did you have good reason to suspect the presence of a rootkit? What appear to be problems are not really issues, just that some mail handling agents have been installed, possibly as part of a dependencies install and that there are some hidden files in your /dev directory.

No baseline to compare it with? you mean comparing with results from a clean/fresh install?? 

how could it be dangerous?

nope, I didn't think I'd be infected, just wanted to check.

thanks :D

---

### Post by Joe of loath on 2011-05-19
rkhunter simply scans for changed files. If there's an update, obviously the affected files will be changed.

It's only useful on servers and the like, which are running 24/7 and rarely updated.

---

### Post by lmn. on 2011-05-19
> **Joe of loath said:**
> rkhunter simply scans for changed files. If there's an update, obviously the affected files will be changed.

It's only useful on servers and the like, which are running 24/7 and rarely updated.

OK thanks

should I look into integrity checking & auditing, or are these tools unnecessary on workstations?

It's more of an interest and less of a security paranoia..

---

### Post by ianc1 on 2011-05-19
Starting at the end, your last warning regarding suspicious files in /dev are all OK, I believe, as I have had these on all my Ubuntu installs.  When I first used rkhunter I searched for info on these and while being no security expert believe them to be OK.  There are options in the /etc/rkhunter.conf file to stop these warnings.

The penultimate warning regarding ssh root login is simply that - a warning - your system is allowing root login through ssh.  Whilst I don't use this I believe it can be turned off by changing one of the options in the sshd config file /etc/ssh/sshd_config.  See [http://ubuntuforums.org/showthread.php?t=1002167](http://ubuntuforums.org/showthread.php?t=1002167)

The other warnings are hard to diagnose.  Ideally rkhunter is installed on a clean system, updated, the settings in its cofig file set /etc/rkhunter.conf.  Then you would run```
sudo rkhunter --propupd
```it then gets a system baseline.  Future runs of rkhunter then compare file hashes to those of the clean system (I beleive).  I usually run it before and after an update, this way I then know if errors come from an update.  If so you can do another```
sudo rkhunter --propud
```to update its baseline.

Someone please correct me if I am wrong here.

The projects page, [http://rkhunter.sourceforge.net/](http://rkhunter.sourceforge.net/), has an excellent install guide at [http://sourceforge.net/apps/trac/rkhunter/wiki/SPRKH](http://sourceforge.net/apps/trac/rkhunter/wiki/SPRKH).  I installed using apt-get and then followed this.

I hope this helps.

---

### Post by lmn. on 2011-05-19
thanks for the links, root ssh being allowed definitely sounds like a vulnerability.

thanks again :D

---

### Post by spynappels on 2011-05-20
> **lmn. said:**
> thanks for the links, root ssh being allowed definitely sounds like a vulnerability.

thanks again :D

It is and it isn't. It is a vulnerability on systems where root is an actual user account which can be logged in as, but in Ubuntu the root account is locked/disabled by default, so it is not actually an issue.

---

### Post by Soul-Sing on 2011-05-20
a shorter version: [https://help.ubuntu.com/community/RKhunter](https://help.ubuntu.com/community/RKhunter)

---

### Post by ianc1 on 2011-05-23
Thanks for that link the bit out automating```
rkhunter --propupd
```is particularly useful.  If anyone hasn't looked at the link its:> ]To run **rkhunter --propupd**, automatic after software updates, put **[noparse]DPkg::Post-Invoke { "if [ -x /usr/bin/rkhunter ]; then /usr/bin/rkhunter --propupd; fi"; };[/noparse]** in */etc/apt/apt.conf.d/90rkhunter*, which you have to make via gkudo nautilus par example.(Or mkdir directoryname.) Although the smiley face should be :P but I can't seem to get rid of the smiley face.

Off to try that now.

---

