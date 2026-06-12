---
title: "Log file from rkhunter has warnings"
date: 2018-01-09
forum: Security
---

### Post by oygle on 2018-01-09
Installed rkhunter today and ran a check ..

```
sudo rkhunter -c
```

then viewed the log file. As the size of the logfile is large, will post the warnings ..

```

[16:00:45] Info: No mail-on-warning address configured
[16:00:45] Info: X will be automatically detected

[16:00:45] Info: Using syslog for some logging - facility/priority level is 'authpriv.warning'.

[16:00:55]   /usr/bin/lwp-request                            [ Warning ]
[16:00:55] Warning: The command '/usr/bin/lwp-request' has been replaced by a script: /usr/bin/lwp-request: a /usr/bin/perl -w script, ASCII text executable

[16:03:16] Info: Starting test name 'passwd_changes'
[16:03:16]   Checking for passwd file changes                [ Warning ]
[16:03:16] Warning: User 'postfix' has been added to the passwd file.
[16:03:16]
[16:03:16] Info: Starting test name 'group_changes'
[16:03:16]   Checking for group file changes                 [ Warning ]
[16:03:16] Warning: Group 'postfix' has been added to the group file.
[16:03:16] Warning: Group 'postdrop' has been added to the group file.
[16:03:16]   Checking root account shell history files       [ None found ]
[16:03:16]
[16:03:16] Info: Starting test name 'system_configs'
[16:03:16] Performing system configuration file checks
[16:03:16]   Checking for an SSH configuration file          [ Found ]
[16:03:16] Info: Found an SSH configuration file: /etc/ssh/sshd_config
[16:03:16] Info: Rkhunter option ALLOW_SSH_ROOT_USER set to 'no'.
[16:03:16] Info: Rkhunter option ALLOW_SSH_PROT_V1 set to '0'.
[16:03:16]   Checking if SSH root access is allowed          [ Warning ]
[16:03:16] Warning: The SSH and rkhunter configuration options should be the same:
[16:03:16]          SSH configuration option 'PermitRootLogin': prohibit-password
[16:03:16]          Rkhunter configuration option 'ALLOW_SSH_ROOT_USER': no
[16:03:16]   Checking if SSH protocol v1 is allowed          [ Not allowed ]
[16:03:16]   Checking for a running system logging daemon    [ Found ]
[16:03:16] Info: A running 'rsyslog' daemon has been found.

[16:03:16] Info: Starting test name 'filesystem'
[16:03:16] Performing filesystem checks
[16:03:16] Info: SCAN_MODE_DEV set to 'THOROUGH'
[16:03:17]   Checking /dev for suspicious file types         [ Warning ]
[16:03:17] Warning: Suspicious file types found in /dev:
[16:03:17]          /dev/shm/pulse-shm-2530832173: data
[16:03:17]          /dev/shm/pulse-shm-3471548845: data
[16:03:17]          /dev/shm/pulse-shm-2417026077: data
[16:03:17]          /dev/shm/pulse-shm-1389230103: data
[16:03:17]          /dev/shm/pulse-shm-2172323307: data
[16:03:18]          /dev/shm/pulse-shm-3031592724: data
[16:03:18]          /dev/shm/pulse-shm-8717739: data
[16:03:18]          /dev/shm/pulse-shm-2264548606: data
[16:03:18]          /dev/shm/pulse-shm-3112176386: data
[16:03:18]          /dev/shm/pulse-shm-2764677997: AmigaOS bitmap font
[16:03:18]   Checking for hidden files and directories       [ Warning ]
[16:03:18] Warning: Hidden directory found: /etc/.java
[16:03:18]   Checking for missing log files                  [ Skipped ]
[16:03:18]   Checking for empty log files                    [ Skipped ]
[16:04:31]
[16:04:31] Info: Test 'apps' disabled at users request.
[16:04:31]
[16:04:31] System checks summary
[16:04:31] =====================
[16:04:31]
[16:04:31] File properties checks...
[16:04:31] Files checked: 149
[16:04:31] Suspect files: 1
[16:04:31]
[16:04:31] Rootkit checks...
[16:04:31] Rootkits checked : 380
[16:04:31] Possible rootkits: 0
[16:04:31]
[16:04:31] Applications checks...
[16:04:31] All checks skipped
[16:04:31]
[16:04:31] The system checks took: 3 minutes and 46 seconds
[16:04:31]
[16:04:31] Info: End date is Tuesday 9 January  16:04:31 AEDT 2018

```

Seems those 10 files, all 64 Mb each, are from pulse-audio ? They have todays date and the only audio was playing 2 videos, and I used "ffmpeg" to cut a video.

---

### Post by wyliecoyoteuk on 2018-01-09
Whenever you update software, add users, or carry out any similar low level system operations, you should run rkhunter --propupd.
That will get rid of some of the warnings, as you have added postfix since rkhunter was installed.

SSH root access should be disabled, as it is a security risk
The lwp-request script is not malicious :
[https://unix.stackexchange.com/questions/373718/rkhunter-gives-me-a-warning-for-usr-bin-lwp-request-what-should-i-do-debi](https://unix.stackexchange.com/questions/373718/rkhunter-gives-me-a-warning-for-usr-bin-lwp-request-what-should-i-do-debi)

.java is not a suspicious hidden directory

The pulseaudio files are shared memory accesses, you can disable pulse audio's use of shared memory if you want to.
You can avoid these warnings by whitelisting in rkhunter.conf

---

### Post by wyliecoyoteuk on 2018-01-09
If you want better system threat monitoring, try installing Lynis.

---

### Post by oygle on 2018-01-09
> **wyliecoyoteuk said:**
> Whenever you update software, add users, or carry out any similar low level system operations, you should run rkhunter --propupd.
That will get rid of some of the warnings, as you have added postfix since rkhunter was installed.

Okay. Yes, when I was doing the rkhunter install in synaptic, it wanted to do a Postfix install ?

> **wyliecoyoteuk said:**
> 
The lwp-request script is not malicious :
[https://unix.stackexchange.com/questions/373718/rkhunter-gives-me-a-warning-for-usr-bin-lwp-request-what-should-i-do-debi](https://unix.stackexchange.com/questions/373718/rkhunter-gives-me-a-warning-for-usr-bin-lwp-request-what-should-i-do-debi)

.java is not a suspicious hidden directory

The pulseaudio files are shared memory accesses, you can disable pulse audio's use of shared memory if you want to.
You can avoid these warnings by whitelisting in rkhunter.conf

Okay, thanks for the tips there. It seems the  path /dev/shm is not just for pulseaudio.  I was able to use the "lsof" command and saw that it is not just pulseaudio that uses /dev/shm . Noticed 'kate' and 'firefox' and 'web' , and as I closed those apps, the related files disappeared.

> **wyliecoyoteuk said:**
> 
SSH root access should be disabled, as it is a security risk

I needed to access files on the LAN months ago and setup  ssh - installed ..

openssh-client
openssh-server
openssh-sftp-server

and I think I set the firewall to only use port 22 locally. Months ago and haven't used it since, so will find out how to disable SSH root access, thanks.

> **wyliecoyoteuk said:**
> If you want better system threat monitoring, try installing Lynis.

Okay thanks, I will check that out. As a precaution (or it may be an overkill), I have installed clamav and running it now. It is very high on CPU usage though ( 25% )

---

### Post by wyliecoyoteuk on 2018-01-10
By default, rkhunter will always flag changes to users or groups.
Lynis is basically rkhunter on steroids, and a lot friendlier.
It audits your system, flags possible issues and makes suggestions.
Well worth trying. it is in the repositories.

---

### Post by oygle on 2018-01-11
> **wyliecoyoteuk said:**
> By default, rkhunter will always flag changes to users or groups.
Lynis is basically rkhunter on steroids, and a lot friendlier.
It audits your system, flags possible issues and makes suggestions.
Well worth trying. it is in the repositories.

Okay thanks. I did have another person question the validity of rkhunter. I will look at Lynis.  :)

---

### Post by wyliecoyoteuk on 2018-01-11
rkhunter is still valid, infact Lynis will check that it's there

---

### Post by oygle on 2018-01-12
> **wyliecoyoteuk said:**
> rkhunter is still valid, infact Lynis will check that it's there

Okay thanks.

---

### Post by Habitual on 2018-01-12
I wouldn't dismiss rkhunter just yet.
"[To avoid these warnings]("https://help.ubuntu.com/community/RKhunter")"

I run rk w\propupd every time I change something on the systems.
Example:
```
apt-get update && apt-get upgrade -y && rkhunter --propupd
```

/dev/shm/pulse-shm-2530832173: data appears to pulse audio.
Any time you update  (by adding software/users, software that  adds users :)
run propupd

---

### Post by HermanAB on 2018-01-14
Hmm, rkhunter should not be lightly discarded.

It should be thrown.  With great force.

---

### Post by oygle on 2018-01-15
> **Habitual said:**
> I wouldn't dismiss rkhunter just yet.
"[To avoid these warnings]("https://help.ubuntu.com/community/RKhunter")"

I run rk w\propupd every time I change something on the systems.
Example:
```
apt-get update && apt-get upgrade -y && rkhunter --propupd
```

/dev/shm/pulse-shm-2530832173: data appears to pulse audio.
Any time you update  (by adding software/users, software that  adds users :)
run propupd

Great, thanks for your help. Handy to know how to address false positives  :)

---

### Post by Habitual on 2018-01-17
> **oygle said:**
> Installed rkhunter today and ran a check ..

```
sudo rkhunter -c
```

then viewed the log file. As the size of the logfile is large, will post the warnings

An un-configured piece of software spitting out "Warnings" is not a false-positive ;)
Good news: Lots of help.

First thing I do is address the exclusions (for what is "allowed", or "what I know about")
Once those are vetted, then it is required to run
```
rkhunter --propupd
```

Once the baseline configuration is dealt with in /etc/rkhunter.conf, then run
```
rkhunter -C
``` 
to check your edits for errors. If hunter does not complain on  the -C (check config) switch,
then run
```
rkhunter -c -sk --rwo
```
-c is check
-sk is skip keypress and 
--rwo is Report Warnings Only 

if you don't want an email, after (assuming) you install one... use this
```
rkhunter -c -sk --rwo --nomow
```


I set this for my nightly cron job to update the 
```
0 0 * * * /usr/local/bin/rkhunter --update --nocolrs > /dev/null 2>&1
```

[https://ubuntuforums.org/showthread.php?t=2330034](https://ubuntuforums.org/showthread.php?t=2330034) has some of this same advice/info for this exact issue ;)

See also [https://www.digitalocean.com/community/tutorials/an-introduction-to-securing-your-linux-vps](https://www.digitalocean.com/community/tutorials/an-introduction-to-securing-your-linux-vps) for some good guidelines.

and [https://help.ubuntu.com/community/StricterDefaults#SSH_Root_Login](https://help.ubuntu.com/community/StricterDefaults#SSH_Root_Login)
discusses what you should do to prohibit root login via openssh-server.

I go over this in [https://ubuntuforums.org/showthread.php?t=2330034and](https://ubuntuforums.org/showthread.php?t=2330034and) it discusses the 
APP_WHITELIST= directive in /etc/rkhunter.conf and how to acquire specific settings for your environment.

this 
> **oygle said:**
> ```

[16:00:45] Info: No mail-on-warning address configured
[16:00:45] Info: X will be automatically detected
```
is corrected by installing am MTA (mail transport agent), such as postfix or exim

Postfix is dead simple. :)
After you have installed an MTA, edit /etc/rkhunter and use
```
MAIL-ON-WARNING="you@domain.com" 
MAIL_CMD=mail -s "[rkhunter] Warnings found for ${HOST_NAME}"
``` assumes postfix.

All of /etc/rkhunter.conf is liberally documented with #commented #examples

man rkhunter will co-sign what I've said.

program documentation is in /usr/local/share/doc/rkhunter-1.4.3 
or there abouts.
 
Let us know.

---

