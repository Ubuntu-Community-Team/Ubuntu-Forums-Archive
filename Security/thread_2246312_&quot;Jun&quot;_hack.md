---
title: "&quot;Jun&quot; hack"
date: 2014-09-29
forum: Security
---

### Post by marsanyi on 2014-09-29
I think I've been hacked.

Noticed today that the net was pokey, a tell-tale.  System Status showed pretty constant uploading going on to somewhere, in bursts of several minutes, followed by periods of inactivity.

Last time I saw this sort of thing, I tracked it down to my cloud backup hogging the network.  This time, however, turning off all the backup/syncing software didn't clean it up.

Ran nethogs, which told me that I had two processes running that seemed to be doing a lot of up/down: /usr/bin/java, loaded early in the sequence (process 1702) and something called "/root/jun".  When the uploads kicked in, nethogs suddenly showed a couple of dozen connections from random ports on my machine to a selection of unknown IP addresses on their ports 80.  Did some snooping; the IP addresses I found are in the Philippines (!), one in Taiwan.

Fired up ufw, and set it to deny all outgoing connections.  The traffic immediately dropped to 0, but one of the CPUs on my machine jumped to 100% usage.  I theorized that it was the firewall intercepting a few gazillion connect requests from something on my machine to the outside world.  Maybe this "jun" thing?

I killed jun (with sudo killall).  The CPU usage dropped back to normal.  I went looking for "jun" and found it at /root/jun, just where nethogs said it was.  Gingerly removed it, removed the firewall rule disallowing outbound connections, all is well.  For a while.  Then, same symptoms.  Sure enough, "jun" was back in the process list, and back in the /root directory.

So there's some other rogue process that's reinstating "jun".  I don't know what it is, so I'm turning off outbound connections until I get it sussed.

Anybody else seen this?  Any suggestions as to finding the rogue process behind "jun"s creation?  FYI: Ubuntu 12.04LTS, up-to-date (inc. all the bash updates that have been coming down the pipe the last few days).  All help gratefully accepted.

---

### Post by bashiergui on 2014-09-29
Did you capture any packets before you took it offline?

You can poke around if you've got the time and desire. This might help (Pdf link)
[http://www.sans.org/score/checklists/ID_Linux.pdf](http://www.sans.org/score/checklists/ID_Linux.pdf)

I can't find anything legitimate relating to "jun" and java.

---

### Post by John_Ten on 2014-09-30
Well, it is probable you have a rootkit on your server, or an ssh backdoor or something.  Run chkrootkit, rkhunter maybe they will find something. Inspect the logs, boot from an usb stick(if you can) and inspect the machine from there, if it's an LKM(loadable kernel module)  rootkit it's pretty hard to find once it's loaded. Next time don't delete the jun program, try to examine it using "strings" or maybe run it in virtualbox or something if it's a binary to see what happens there if you wanna know what it is, but I think the jun program is the least of your problems, I think the big problem is someone compromised your machine and you need to find him.

---

### Post by marsanyi on 2014-09-30
Thanks for the pointer, I'll go try some of those tools.

I have a copy of "jun" quarantined.  Hexdump on the binary didn't show anything I recognized (strings of text, for example).

---

### Post by marsanyi on 2014-09-30
I'll check out chkrootkit, thanks.  I'm trying to figure out what's running that's behind all this and surgically exposing it.  We'll see how far I get.

---

### Post by bashiergui on 2014-09-30
If you can zip/tar jun and post it somewhere like dropbox, I'd like to analyze it.

look at the pdf I linked you and post any weird stuff you find in your system. If you took the box offline, then there's no danger in inspecting the machine.

---

### Post by marsanyi on 2014-09-30
I can do that, tar.gz'd the binary.  The raw binary is 1.22Mb, the compressed is 468K.  With whom should I share the link?

---

### Post by marsanyi on 2014-09-30
So ps -aux proves more useful than ps -A.  The /usr/bin/java job running low in the list is indeed my cloud backup, CrashPlan.  I see an entry for root, job 4794 (fairly late loaded) running /usr/bin/.sshd.  I expected one for /usr/sbin/sshd, as I have another Ubuntu machine running that.  Looking in /usr/bin for .sshd, I see a file with exactly the same filesize as "jun".

---

### Post by marsanyi on 2014-09-30
sudo lsof -p 4794 (.sshd) shows: 
```
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF    NODE NAME
.sshd   4794 root  cwd    DIR    8,1     4096       2 /
.sshd   4794 root  rtd    DIR    8,1     4096       2 /
.sshd   4794 root  txt    REG    8,1  1223123 8655397 /usr/bin/.sshd
.sshd   4794 root    0u   CHR    1,3      0t0    1029 /dev/null
.sshd   4794 root    1u   CHR    1,3      0t0    1029 /dev/null
.sshd   4794 root    2u   CHR    1,3      0t0    1029 /dev/null
.sshd   4794 root    3uW  REG    8,1        4  262150 /tmp/moni.lod

sudo lsof -p 4735 (jun) shows:
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF   NODE NAME
jun     4735 root  cwd    DIR    8,1     4096      2 /
jun     4735 root  rtd    DIR    8,1     4096      2 /
jun     4735 root  txt    REG    8,1  1223123 143352 /root/jun
jun     4735 root    0u   CHR    1,3      0t0   1029 /dev/null
jun     4735 root    1u   CHR    1,3      0t0   1029 /dev/null
jun     4735 root    2u   CHR    1,3      0t0   1029 /dev/null
jun     4735 root    3uW  REG    8,1        4 262147 /tmp/gates.lod
jun     4735 root    4u  IPv4 410946      0t0    TCP 192.168.2.200:39003->118.123.19.72:25000 (SYN_SENT)
```

---

### Post by Habitual on 2014-10-01
> **marsanyi said:**
> 
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF   NODE NAME
.sshd   4794 root  txt    REG    8,1  1223123 8655397 /usr/bin/.sshd

> **marsanyi said:**
>  sudo lsof -p 4735 (jun) shows:
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF   NODE NAME
jjun     4735 root  txt    REG    8,1  1223123 143352 /root/jun

Sure looks like you've been rooted.
I''d start by firewalling the Chinese IP of 118.123.19.72

and check the crons on the system for method of re-starting:
```
for i in /var/spool/cron/*; do echo $; sed 's/^//' $i; echo; done | grep -v "#"
```
If there is anything suspect, use comments (insert an "#" in front of them) on any suspicious crons and restart crond (however that's done on Ubuntu these days)
Also, if any of those cron entries are suspicious, after commenting them out, look at the files they are using in the cron.

and investigate the directories they are being called from.

Install and run rkhunter and carefully review /var/log/rkhunter.log when it's done.
Clean /tmp

It's not clear to me if you should change your root password with this infection on the system until after it's been cleaned.

---

### Post by marsanyi on 2014-10-01
Nothing suspicious in crontabs, I re-checked after you reminded me, thanks.

Thanks for the pointer to /tmp, though; I'd forgotten about that.  Looking in there, I see:
```
at-spi2
everpad-provider-robert.lock
everpad-robert.lock
gates.lod
hsperfdata_robert
hsperfdata_root
keyring-YP8d7j
moni.lod
orbit-robert
pulse-2L9K88eMlGn7
pulse-fdUoBFIGvjT3
pulse-PKdhtXMmr18n
qtsingleapp-homero-347d-3e9-lockfile
skype-2632
ssh-VErRICFx2509
tmp5td3cy
unity_support_test.0

```
So: the two .lod files referred to in the lsof output, and ssh-VE..., keyring-YP..., ...

I quarantined these onto a thumbdrive, and I'm incorporating them into the tarfile mentioned above.  Is anyone interested in examining them?

---

### Post by marsanyi on 2014-10-01
Sorry, got ahead of myself.  ssh-VE... is a directory containing a socket, "agent.2509".  "keyring-YP..." is a directory containing four sockets, "control", "gpg", "pkcs11", "ssh".  at-sp2 is a directory containing a socket, "socket-1771-1804289383".

---

### Post by marsanyi on 2014-10-01
More files in /tmp:
.ICE-unix
.winbindd/pipe
.X0-lock
.X11-unix/X0

---

### Post by marsanyi on 2014-10-01
Ran rkhunter.  Nice!  Saves a bunch of spelunking on my part.  sudo less /var/log/rkhunter.log | grep -C 1 "Warning" found a few things:

```
[10:47:42]   /usr/local/bin/rkhunter                         [ OK ]
[10:47:43]   /usr/sbin/adduser                               [ Warning ]
[10:47:43] Warning: The command '/usr/sbin/adduser' has been replaced by a script: /usr/sbin/adduser: a /usr/bin/perl script, ASCII text executable
[10:47:44]   /usr/sbin/chroot                                [ OK ]
--
[10:47:54]   /usr/bin/lastlog                                [ OK ]
[10:47:54]   /usr/bin/ldd                                    [ Warning ]
[10:47:54] Warning: The command '/usr/bin/ldd' has been replaced by a script: /usr/bin/ldd: Bourne-Again shell script, ASCII text executable
[10:47:54]   /usr/bin/less                                   [ OK ]
--
[10:48:04]   /usr/bin/mawk                                   [ OK ]
[10:48:04]   /usr/bin/lwp-request                            [ Warning ]
[10:48:04] Warning: The command '/usr/bin/lwp-request' has been replaced by a script: /usr/bin/lwp-request: a /usr/bin/perl -w script, ASCII text executable
[10:48:04]   /usr/bin/telnet.netkit                          [ OK ]
--
[10:48:20]   /bin/uname                                      [ OK ]
[10:48:20]   /bin/which                                      [ Warning ]
[10:48:20] Warning: The command '/bin/which' has been replaced by a script: /bin/which: POSIX shell script, ASCII text executable
[10:48:20]   /bin/dash                                       [ OK ]
--
[10:49:47] Info: Rkhunter option ALLOW_SSH_PROT_V1 set to '0'.
[10:49:47]   Checking if SSH root access is allowed          [ Warning ]
[10:49:47] Warning: The SSH and rkhunter configuration options should be the same:
[10:49:47]          SSH configuration option 'PermitRootLogin': yes
--
[10:49:48] Info: SCAN_MODE_DEV set to 'THOROUGH'
[10:49:52]   Checking /dev for suspicious file types         [ Warning ]
[10:49:52] Warning: Suspicious file types found in /dev:
[10:49:52]          /dev/.udev/rules.d/root.rules: ASCII text
[10:49:53]   Checking for hidden files and directories       [ Warning ]
[10:49:53] Warning: Hidden directory found: /etc/.java
[10:49:53] Warning: Hidden directory found: /dev/.udev
[10:49:53] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'
[10:49:53] Warning: Hidden file found: /usr/bin/.sshd: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, for GNU/Linux 2.2.5, not stripped
[10:49:53]   Checking for missing log files                  [ Skipped ]
```

- I'm not a Perl guy, but looking at the files warned as "replaced by a script" seemed OK.
- SSH root access has obviously been hacked.
- /dev/.udev/rules.d/root.rules shows

SUBSYSTEM=="block", ENV{MAJOR}=="8", ENV{MINOR}=="1", SYMLINK+="root"

which I see on my other Ubuntu system

- /etc/.java shows a directory .systemPrefs containing .systemRootModFile and .system.lock, which I see on my other Ubuntu system
- /dev/.udev has the root.rules file described above
- /usr/bin/.sshd is the suspect file we found in previous posts

So: I'm going to kill the running "jun" and ".sshd" processes, clear out /tmp and remove /usr/bin/.sshd, and see where I stand.

---

### Post by tgalati4 on 2014-10-01
Regarding *which*:

> tgalati4@Mint14-Extensa ~ $ which which
/usr/bin/which
tgalati4@Mint14-Extensa ~ $ ls -la /usr/bin/which
lrwxrwxrwx 1 root root 10 Dec 28  2012** /usr/bin/which -> /bin/which**
tgalati4@Mint14-Extensa ~ $ ls -la /bin/which
-rwxr-xr-x 1 root root 946 Sep 18  2012 /bin/which
tgalati4@Mint14-Extensa ~ $ cat /bin/which
#! /bin/sh
set -ef

if test -n "$KSH_VERSION"; then
	puts() {
		print -r -- "$*"
	}
else
	puts() {
		printf '%s\n' "$*"
	}
fi

ALLMATCHES=0

while getopts a whichopts
do
        case "$whichopts" in
                a) ALLMATCHES=1 ;;
                ?) puts "Usage: $0 [-a] args"; exit 2 ;;
        esac
done
shift $(($OPTIND - 1))

if [ "$#" -eq 0 ]; then
 ALLRET=1
else
 ALLRET=0
fi
case $PATH in
	(*[!:]:) PATH="$PATH:" ;;
esac
for PROGRAM in "$@"; do
 RET=1
 IFS_SAVE="$IFS"
 IFS=:
 case $PROGRAM in
  */*)
   if [ -f "$PROGRAM" ] && [ -x "$PROGRAM" ]; then
    puts "$PROGRAM"
    RET=0
   fi
   ;;
  *)
   for ELEMENT in $PATH; do
    if [ -z "$ELEMENT" ]; then
     ELEMENT=.
    fi
    if [ -f "$ELEMENT/$PROGRAM" ] && [ -x "$ELEMENT/$PROGRAM" ]; then
     puts "$ELEMENT/$PROGRAM"
     RET=0
     [ "$ALLMATCHES" -eq 1 ] || break
    fi
   done
   ;;
 esac
 IFS="$IFS_SAVE"
 if [ "$RET" -ne 0 ]; then
  ALLRET=1
 fi
done

exit "$ALLRET"


I'm sure there is a reason to use a symbolic link (in bold) for *which*.  I just don't know it.

A common technique for malware to hide itself is to make a link to a commonly-used utility.  So checking those utilities is a common security scan process.  It's up to you to determine if the utilities are genuine and unaltered.

More importantly, what is the contents of:

```
sudo su
ls -la /root/jun
```

Then run a *history* while still logged in as root:

```
history
```

Then examine  /var/log/auth.log and /var/log/auth.log.1 and post suspicious entries.

---

### Post by Habitual on 2014-10-01
I think those Warnings are to be expected for Ubu-flavored distros.
See also [http://sourceforge.net/p/rkhunter/mailman/message/31460254/](http://sourceforge.net/p/rkhunter/mailman/message/31460254/)

---

### Post by Habitual on 2014-10-01
You can also try 2 other tools
chkrootkit and [lynis]("http://cisofy.com/files/lynis-1.6.2.tar.gz")

unzip lynis and cd into the directory and run:
```
./lynis -c --auditor "Make a comment here" --cronjob
```
and view the log file at /var/log/lynis.log

wrt: chkrootkit, I have issue with software that's only been update every few years, so I don't use it.
chkrootkit 0.49 is now available! (Release Date: Thu Jul 30 2009)
chkrootkit 0.50 is now available! (Release Date: Wed Jun 4 2014)

---

### Post by marsanyi on 2014-10-01
Hmm.  I can no longer log in through gdm (or whatever 12.04 is using).  I _can_ login from tty1.  Keeping an eye on ps -aux and nethogs for an hour or so.

---

### Post by marsanyi on 2014-10-01
Re: gdm/lightm: my mistake, I removed /tmp and didn't create a new one with the right permissions.  Fixed.  I'll keep you posted on the activity.

---

### Post by bashiergui on 2014-10-01
> **marsanyi said:**
> Hmm.  I can no longer log in through gdm (or whatever 12.04 is using).  I _can_ login from tty1.  Keeping an eye on ps -aux and nethogs for an hour or so.
You're doing all this analysis while it is NOT networked, right?

FWIW I don't see the value of running chrootkit or rk hunter now. They don' do any good unless you have a good baseline to compare the results to.

---

### Post by marsanyi on 2014-10-01
Found another suspicious binary: /usr/bin/bsd-port/getty.  Same size as "jun".  Shows up on nethogs as a big uploader (when I let it).  Not present in my other Ubuntu install.

Spelunking through the logs, I found the intrusion from last Thursday:

```
---
Sep 25 15:45:53 ians-rig sshd[20767]: reverse mapping checking getaddrinfo for 205.85.178.61.xbky.lz.gs.dynamic.163data.com.cn [61.178.85.205] failed - POSSIBLE BREAK-IN ATTEMPT!
Sep 25 15:45:53 ians-rig sshd[20767]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.178.85.205  user=root
Sep 25 15:45:53 ians-rig sshd[20767]: pam_winbind(sshd:auth): getting password (0x00000388)
Sep 25 15:45:53 ians-rig sshd[20767]: pam_winbind(sshd:auth): pam_get_item returned a password
Sep 25 15:45:54 ians-rig sshd[20767]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Sep 25 15:45:56 ians-rig sshd[20767]: Failed password for root from 61.178.85.205 port 3192 ssh2
Sep 25 15:45:56 ians-rig sshd[20767]: pam_winbind(sshd:auth): getting password (0x00000388)
Sep 25 15:45:56 ians-rig sshd[20767]: pam_winbind(sshd:auth): pam_get_item returned a password
Sep 25 15:45:56 ians-rig sshd[20767]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Sep 25 15:45:58 ians-rig sshd[20767]: Failed password for root from 61.178.85.205 port 3192 ssh2
Sep 25 15:45:58 ians-rig sshd[20767]: pam_winbind(sshd:auth): getting password (0x00000388)
Sep 25 15:45:58 ians-rig sshd[20767]: pam_winbind(sshd:auth): pam_get_item returned a password
Sep 25 15:45:58 ians-rig sshd[20767]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Sep 25 15:46:00 ians-rig sshd[20767]: Failed password for root from 61.178.85.205 port 3192 ssh2
Sep 25 15:46:00 ians-rig sshd[20767]: pam_winbind(sshd:auth): getting password (0x00000388)
Sep 25 15:46:00 ians-rig sshd[20767]: pam_winbind(sshd:auth): pam_get_item returned a password
Sep 25 15:46:00 ians-rig sshd[20767]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Sep 25 15:46:02 ians-rig sshd[20767]: Failed password for root from 61.178.85.205 port 3192 ssh2
Sep 25 15:46:03 ians-rig sshd[20767]: pam_winbind(sshd:auth): getting password (0x00000388)
Sep 25 15:46:03 ians-rig sshd[20767]: pam_winbind(sshd:auth): pam_get_item returned a password
Sep 25 15:46:03 ians-rig sshd[20767]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Sep 25 15:46:04 ians-rig sshd[20767]: Failed password for root from 61.178.85.205 port 3192 ssh2
Sep 25 15:46:05 ians-rig sshd[20767]: pam_winbind(sshd:auth): getting password (0x00000388)
Sep 25 15:46:05 ians-rig sshd[20767]: pam_winbind(sshd:auth): pam_get_item returned a password
Sep 25 15:46:05 ians-rig sshd[20767]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Sep 25 15:46:07 ians-rig sshd[20767]: Failed password for root from 61.178.85.205 port 3192 ssh2
Sep 25 15:46:07 ians-rig sshd[20767]: Disconnecting: Too many authentication failures for root [preauth]
Sep 25 15:46:07 ians-rig sshd[20767]: PAM 5 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=61.178.85.205  user=root
Sep 25 15:46:07 ians-rig sshd[20767]: PAM service(sshd) ignoring max retries; 6 > 3
Sep 25 15:46:08 ians-rig sshd[20770]: reverse mapping checking getaddrinfo for 205.85.178.61.xbky.lz.gs.dynamic.163data.com.cn [61.178.85.205] failed - POSSIBLE BREAK-IN ATTEMPT!
Sep 25 15:46:09 ians-rig sshd[20770]: Accepted password for root from 61.178.85.205 port 1727 ssh2
Sep 25 15:46:09 ians-rig sshd[20770]: pam_unix(sshd:session): session opened for user root by (uid=0)
Sep 25 15:46:11 ians-rig sshd[20770]: pam_unix(sshd:session): session closed for user root
...
Sep 25 16:04:09 ians-rig sshd[21135]: Accepted password for root from 112.236.248.188 port 2106 ssh2
Sep 25 16:04:09 ians-rig sshd[21135]: pam_unix(sshd:session): session opened for user root by (uid=0)
Sep 25 16:04:25 ians-rig sshd[21135]: subsystem request for sftp by user root
Sep 25 16:05:43 ians-rig sshd[21479]: reverse mapping checking getaddrinfo for 82.169.88.117.broad.nj.js.dynamic.163data.com.cn [117.88.169.82] failed - POSSIBLE BREAK-IN ATTEMPT!
Sep 25 16:05:50 ians-rig sshd[21479]: Accepted password for root from 117.88.169.82 port 62230 ssh2
Sep 25 16:05:50 ians-rig sshd[21479]: pam_unix(sshd:session): session opened for user root by (uid=0)
Sep 25 16:06:01 ians-rig passwd[21702]: pam_unix(passwd:chauthtok): password changed for root
Sep 25 16:06:01 ians-rig passwd[21702]: pam_smbpass(passwd:chauthtok): password for (root/0) changed by (root/0)
Sep 25 16:06:01 ians-rig passwd[21702]: gkr-pam: couldn't update the login keyring password: no old password was entered
Sep 25 16:06:43 ians-rig sshd[21135]: Received disconnect from 112.236.248.188: 11: Disconnect requested by Windows SSH Client.
Sep 25 16:06:43 ians-rig sshd[21135]: pam_unix(sshd:session): session closed for user root
Sep 25 16:06:57 ians-rig sshd[21479]: pam_unix(sshd:session): session closed for user root
Sep 25 16:17:01 ians-rig CRON[21855]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 25 16:17:01 ians-rig CRON[21855]: pam_unix(cron:session): session closed for user root
Sep 25 16:35:42 ians-rig sshd[22172]: Accepted password for root from 222.186.42.224 port 2804 ssh2
Sep 25 16:35:42 ians-rig sshd[22172]: pam_unix(sshd:session): session opened for user root by (uid=0)
Sep 25 16:36:07 ians-rig sshd[22172]: Received disconnect from 222.186.42.224: 11: Disconnect requested by Windows SSH Client.
Sep 25 16:36:07 ians-rig sshd[22172]: pam_unix(sshd:session): session closed for user root
...
Sep 25 16:52:01 ians-rig lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Sep 25 16:52:01 ians-rig lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Sep 25 16:52:03 ians-rig lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "robert"
Sep 25 16:52:03 ians-rig dbus[1174]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.27" (uid=104 pid=2009 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.13" (uid=0 pid=1449 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Sep 25 16:52:08 ians-rig lightdm: pam_unix(lightdm:session): session closed for user lightdm
Sep 25 16:52:08 ians-rig lightdm: pam_unix(lightdm:session): session opened for user robert by (uid=0)
Sep 25 16:52:08 ians-rig lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Sep 25 16:52:10 ians-rig polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.53 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Sep 25 16:52:19 ians-rig dbus[1174]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.63" (uid=1001 pid=2825 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.13" (uid=0 pid=1449 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Sep 25 16:57:06 ians-rig sshd[3308]: reverse mapping checking getaddrinfo for 82.169.88.117.broad.nj.js.dynamic.163data.com.cn [117.88.169.82] failed - POSSIBLE BREAK-IN ATTEMPT!
Sep 25 16:57:13 ians-rig sshd[3308]: Accepted password for root from 117.88.169.82 port 62735 ssh2
Sep 25 16:57:13 ians-rig sshd[3308]: pam_unix(sshd:session): session opened for user root by (uid=0)
Sep 25 16:58:07 ians-rig sshd[3308]: pam_unix(sshd:session): session closed for user root
---
```

and away they go.  Lots of subsequent references to NT_STATUS_NO_SUCH_USER, Windows SSH Client, ...  So, my bad I believe, I had SSH up but allowed password-based access.

---

### Post by bashiergui on 2014-10-01
Deleted, irrelevant. Logs clearly indicate a successful ssh brute force attack.

---

### Post by QIII on 2014-10-01
Hello!

Please use code tags to enclose terminal output.  It makes this a lot easier to read and takes up less room.

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.
 
2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by marsanyi on 2014-10-01
Sorry,QIII, [**[COLOR=#C61919][B]**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=628170")will do.  Couldn't find a button on the HTML text input widget to do it for me, so I was lazy.

---

### Post by marsanyi on 2014-10-01
Thanks, Habitual, tgalati4, those four scripts look reasonable and show up as false-positive for Ubuntu.

bashiergui: yes, I'm offline while doing this analysis.  I forced "jun" to fire up once in a while by enabling the firewall and blocking all I/O; when I just disconnect the ethernet port eth0 goes away and "jun" doesn't even try.

---

### Post by marsanyi on 2014-10-01
Yes, isn't it?  However, I'm not running a webserver on this box.

---

### Post by marsanyi on 2014-10-01
Current status:
- found another duplicate, /usr/bin/bsd-port/getty, same file size.  Masquerading as /usr/sbin/getty.  Killed, removed.
- disabled ssh altogether so the bad guys can't log back in and set this all up again.
- monitoring ufw log, network traffic, nethogs, processes running, I tentatively opened up outgoing connections on the firewall.  So far, no unexpected activity: connections to Google, local ISP, DNS, the odd multicast ping from my router.  Going to monitor this for a while, then if all stays well start using network apps (mail, firefox)

---

### Post by Habitual on 2014-10-01
Yes, if you don't need ssh server, remove it. :)

firewall these IPs that logged in as root:
```
112.236.248.188
117.88.169.82
117.88.169.82
222.186.42.224
61.178.85.205
```

Change your root password.

**Make sure remote Admin capability on the router is disabled.**

---

### Post by tgalati4 on 2014-10-01
```
whois 112.236.248.188
```

You want to avoid IP's that serve cat food.

---

### Post by marsanyi on 2014-10-01
Yes to cat food IP addresses.  I turned off root password access, as per vanilla Ubuntu setup.  My router belongs to my ISP and I can't access it directly, so I'll just alert them and let them worry about it.

Thanks for all your help, guys.  Monitored the machine all day, looks like it's happy.  I'll stay paranoid for a few more days.  If anyone's interested in deconstructing the malware that the intruder(s) set up, I have the binaries quarantined on a memory stick and I'm happy to send them to you.

---

### Post by bashiergui on 2014-10-01
> [FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]and away they go. Lots of subsequent references to NT_STATUS_NO_SUCH_USER, Windows SSH Client, ... So, my bad I believe, I had SSH up but allowed password-based access.[/FONT]Let's call your attacker Jun. We know that Jun logged into your box on the 25th. You found him on the 27th. Jun had two days as root to do whatever he wanted on your computer, totally unimpeded. You found a couple processes he spawned. Odds are he did more than that. 

You never said what you use this box for. If it's anything sensitive or valuable then I would never trust that machine again until it is wiped and reimaged.

---

### Post by unspawn on 2014-10-02
> **marsanyi said:**
> ```
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF    NODE NAME .sshd   4794 root  txt    REG    8,1  1223123 8655397 /usr/bin/.sshd .sshd   4794 root    3uW  REG    8,1        4  262150 /tmp/moni.lod jun     4735 root    3uW  REG    8,1        4 262147 /tmp/gates.lod
``` While names don't mean anything at this stage both .lod reminded me of [BillGates botnet](http://securelist.com/analysis/publications/64361/versatile-ddos-trojan-for-linux/)... See if you can find more anomalous files and check your logs as well (all log files). If you want to run Rootkit Hunter please run it from [CVS](http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/rkhunter/?view=tar) as the current release doesn't have the new items you want to look for. Also, as foreign files were found with owner root, I agree the host should be isolated immediately while you investigate further. *BTW I would like a copy of the files. Could you please upload them here: [http://sourceforge.net/p/rkhunter/support-requests/](http://sourceforge.net/p/rkhunter/support-requests/) ?

---

### Post by bashiergui on 2014-10-02
> **unspawn said:**
> While names don't mean anything at this stage both .lod reminded me of [BillGates botnet]("http://securelist.com/analysis/publications/64361/versatile-ddos-trojan-for-linux/")... See if you can find more anomalous files and check your logs as well (all log files).Nice find! Now I want an image of this machine.

---

### Post by tgalati4 on 2014-10-03
There is a white-hat hacker culture in some countries where the goal is to simply break into machines and snoop around, but not do anything destructive.  Sort of like catch-and-release fishing.  It's possible that "jun" was such a hacker.  He got into your machine, mucked around a bit, and then left.  "Linux machine, not much fun here.  I will move on to other boxes."

It is quite unsettling to find droppings in your system though.

A Haiku:

White Hat Hackers blues?
Ssh and weak password.
Rat scat cleanup time.

---

### Post by unspawn on 2014-10-04
> **bashiergui said:**
> Nice find! Now I want an image of this machine. That indeed would be convenient eh? Getting access to all your fellow forum members data like /etc/shadow, SSH private keys, any correspondence, etc, etc... Are you in any way familiar with Privacy laws, practical forensics and NDAs? If not, what would the OP get out of you having a copy of his data? Just being curious, OK?

---

### Post by unspawn on 2014-10-04
> **tgalati4 said:**
> It's possible that "jun" was such a hacker.  He got into your machine, mucked around a bit, and then left.  "Linux machine, not much fun here.  I will move on to other boxes." If that was a conclusion based on facts, meaning having reviewed events, time line and evidence, that would make sense.  If you haven't, what purpose would speculating serve?  How would it, with all due respect, help the OP?

---

### Post by tgalati4 on 2014-10-04
Lots of suggestions have been given, but few responses by the OP.  No posting of the grepped auth.log as requested, no history file of root actions, no accurate timeline presented.  So yes, you are correct, speculation is not helpful.

---

### Post by bashiergui on 2014-10-04
> **unspawn said:**
> That indeed would be convenient eh? Getting access to all your fellow forum members data like /etc/shadow, SSH private keys, any correspondence, etc, etc... Are you in any way familiar with Privacy laws, practical forensics and NDAs? If not, what would the OP get out of you having a copy of his data? Just being curious, OK? The OP's computer was compromised and I'm interested in finding details about the attack because of my selfish curiosity. It apparently needs to be said: don't give images of your computer to random people you encounter on the internet.

[FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]From a much less selfish standpoint, I gave the OP a cheat sheet on investigating it himself, hopefully he does more of that if he doesn't reimage it.[/FONT]

I suppose it's relevant to point out that Jun had unfettered access to that very same sensitive data for a few days. Which reminds me to say to the OP
1. Change all your passwords
2. Replace all your crypto keys

---

### Post by marsanyi on 2014-10-07
Sorry, I've been away from my office for a few days so missed a bit of posting.  I infer from this that I'm the "OP".  My investigative efforts were posted as I went; of course, at the end of the process I wiped the system partition and reinstalled a virgin 12.04LTS image, and closed the SSH port, and re-did passwords, all before re-admitting the machine to the network.  I was just interested in trying to divine a little more from looking at the traces left by the hack, and providing information to the Net about symptoms, before the nuclear option :)

Thanks to you-all, I learned quite a bit from the effort.  I hope the log extracts and descriptions help someone else.

tgalati4: seems unlikely to me that this was benign.  The tell-tale was unthrottled uploads from my system to IPs in China and the Philippines, something I can't imagine a white-hat would countenance, nor do I think the intrusion was particularly skilled from the logs.

bashiergui: thanks to your suggestions more than any others, I found what I found.  I appreciate your spending the time to give me a cheat-sheet that kickstarted my investigation.

If there's anything else you-all think I need to do to carry on, now that I've closed off checking the infected system, I'd appreciate the suggestions.  Thanks.

---

### Post by marsanyi on 2014-10-07
Oh.  Also: updated ssh settings to disallow password-based entry, disallow root login.

---

