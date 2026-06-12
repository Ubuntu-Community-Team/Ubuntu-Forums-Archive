---
title: "Tomcat 6 won't start at boot, but otherwise all is normal"
date: 2010-11-18
forum: Server Platforms
---

### Post by Lewisham on 2010-11-18
Hi all,
Long-time lurker, first time poster ;)

I'm having some trouble with Tomcat 6 after upgrading to 10.10. During the upgrade process, the installer hung while dealing with Tomcat 6, which required me to kill the upgrade and do some clean up, and then re-run `apt-get upgrade` again to get things going. This left some weirdness (like the MOTD for both 10.10 and 10.04 being shown on login), but otherwise things are OK.

The only remaining problem I have is Tomcat; it simply won't start when the server is booted. The information I have:

[LIST]
[*]Tomcat 6 runs normally when started with `sudo /etc/init.d/tomcat6 start`. No errors are thrown, everything works as expected.
[*]I used `rcconf` to try removing and reinstalling the rc scripts, this didn't help.
[*] I manually deleted all the rc scripts, then used `rcconf` again. The scripts all seem symlinked correctly to `/etc/init.d/tomcat6`, but it's just not coming up on boot.
[*] I ran `sudo grep "tomcat" /var/log/*.log` to see if something is appearing in the logs, but nothing of interest is there.
[/LIST]

How can I verify that Ubuntu is even trying to start Tomcat? As this is a development box, I am not adverse to a quick + dirty solution if there's some either simple way of getting it started at boot. I'm thinking the next Ubuntu release will see me blow away the server and start it fresh, but right now I'd just like a working box :)

Thanks all!

---

### Post by wongo888 on 2010-11-18
Duplicate MOTD is a known bug of the upgrade.

[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/659738](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/659738)

Check that the new script is executable by root:

```
$ cd /etc/init.d
$ sudo chmod 755 your_script
$ sudo chown root:root your_script

```

I'm running Tomcat 5 on CentOS and in that init.d script the log is defined in the script:

```
# Define the tomcat log file
TOMCAT_LOG="${TOMCAT_LOG:-/var/log/tomcat5/catalina.out}"

```

I haven't used Tc6 on Debian or Ubuntu so I'm not sure about where the log goes. It is probably similar.

---

### Post by Lewisham on 2010-11-19
Thanks for the reply, unfortunately it's not a permissions problem (I did try, just in case!).

The Tomcat logs are empty for the time period the server should be coming up... the last entries are the server being destroyed before a reboot. Ubuntu isn't even trying to start the server, but I know the scripts are in the rc folders. Is there a way to view Ubuntu's log of trying to start the server? As I said in my OP, just grepping for `tomcat` in /var/log didn't help :(

I'm still open to quick + dirty solutions :)

---

### Post by wongo888 on 2010-11-19
Check the default runlevel of your system:

```
$ cat /etc/init/rc-sysinit.conf | grep "env DEFAULT_RUNLEVEL"
env DEFAULT_RUNLEVEL=2

```

If you're at runlevel 2 then check the /rc2.d directory:

```
$ cd /etc/rc2.d/
$ ls -l
```

Ensure that your S symlink is there and it points to your init.d script.

You can view all your symlinks (I'm guessing it is called tomcat or similar):

```
$ ls -l /etc/rc?.d/*tomcat
```

You may want to restore the script defaults (see the update-rc.d man pages for more info):

```
$ sudo update-rc.d tomcat defaults
```

Note: On my CentOS box the Tomcat log doesn't have a *.log extension. It is called catalina.**out**

---

### Post by Lewisham on 2010-11-22
Still no luck :(

Perhaps I can hack it by writing my own script that launches the original Tomcat script again?

---

### Post by wongo888 on 2010-11-22
What does it say in your catalina.out? Anything?

You installed tc6 using apt-get, right?

Your init.d script is the one installed by apt-get?

Paste output for the following commands:

```
$ runlevel
$ ls -l /etc/init.d/
$ ls -l /etc/rc2.d/

```

---

### Post by Lewisham on 2010-11-22
catalina.out is empty for the timeframe it needs to have entries as Tomcat isn't starting... the last lines written to it will be the shutdown from before the reboot.

The init.d script is largely the same as the one from apt-get, but with some changes I made. During the upgrade I was offered the chance to override it, with the default to no. I chose no. I see no reason to think the init.d script itself is broken, because I'm starting the server with `sudo /etc/init.d/tomcat6 start` with no problems at all.

ls listings as requested:

```


cflewis@eisbox:~/argouml$ runlevel
N 2
cflewis@eisbox:~/argouml$ ls -l /etc/init.d/
total 260
lrwxrwxrwx 1 root root   21 2010-11-04 17:03 alsa-mixer-save -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 4106 2010-11-09 11:35 apparmor
lrwxrwxrwx 1 root root   21 2010-11-04 17:08 atd -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-11-04 17:09 avahi-daemon -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 1785 2010-02-17 06:00 binfmt-support
-rwxr-xr-x 1 root root 1091 2009-09-24 16:41 bluetooth
-rwxr-xr-x 1 root root 2341 2009-09-07 11:58 bootlogd
lrwxrwxrwx 1 root root   21 2010-11-04 16:24 console-setup -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-11-04 17:06 cron -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-11-04 17:04 cups -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-11-04 17:03 dbus -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-11-04 16:33 dmesg -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 1235 2009-02-20 09:56 dns-clean
-rwxr-xr-x 1 root root 5671 2008-08-20 03:50 fail2ban
lrwxrwxrwx 1 root root   21 2010-11-04 17:03 failsafe-x -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 1523 2010-05-27 02:22 fancontrol
-rwxr-xr-x 1 root root 1105 2009-12-07 14:37 grub-common
-rwxr-xr-x 1 root root 1329 2009-03-31 02:11 halt
lrwxrwxrwx 1 root root   21 2010-11-04 17:06 hostname -> /lib/init/upstart-job
-rwxr-xr-x 1 root root  242 2010-10-26 12:56 hudsonslave.sh
lrwxrwxrwx 1 root root   21 2010-11-04 16:22 hwclock -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-11-04 16:22 hwclock-save -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 5183 2009-02-18 13:41 hwclock.sh.dpkg-obsolete
lrwxrwxrwx 1 root root   21 2010-11-04 17:08 irqbalance -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 1293 2009-09-07 11:58 killprocs
-rwxr-xr-x 1 root root 1816 2009-01-23 10:48 klogd
-rwxr-xr-x 1 root root 2519 2010-07-15 11:25 lighttpd
-rwxr-xr-x 1 root root  869 2010-05-27 05:15 lm-sensors
lrwxrwxrwx 1 root root   21 2010-11-04 17:03 module-init-tools -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 5917 2009-09-09 09:31 mysql
-rwxr-xr-x 1 root root 2515 2009-05-14 02:29 mysql-ndb
-rwxr-xr-x 1 root root 1905 2009-05-14 02:29 mysql-ndb-mgm
-rwxr-xr-x 1 root root 2256 2009-12-03 08:04 networking
lrwxrwxrwx 1 root root   21 2010-11-04 17:03 network-interface -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-11-04 17:03 network-interface-security -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-11-04 17:12 network-manager -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 1822 2009-04-14 05:37 NetworkManager.dpkg-backup
-rwxr-xr-x 1 root root 3411 2009-09-20 00:55 nxsensor
-rwxr-xr-x 1 root root 2454 2009-09-20 00:55 nxserver
-rwxr-xr-x 1 root root  882 2009-03-31 02:11 ondemand
lrwxrwxrwx 1 root root   21 2010-11-17 22:25 plymouth -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-11-17 22:25 plymouth-log -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-11-17 22:25 plymouth-splash -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-11-17 22:25 plymouth-stop -> /lib/init/upstart-job
-rwxr-xr-x 1 root root  665 2009-06-22 00:19 policykit
-rwxr-xr-x 1 root root 2172 2009-01-02 09:02 portmap
-rwxr-xr-x 1 root root 1028 2010-08-05 08:51 postgresql
-rwxr-xr-x 1 root root 1027 2009-03-19 19:31 postgresql-8.3
-rwxr-xr-x 1 root root 1027 2010-10-06 08:32 postgresql-8.4
-rwxr-xr-x 1 root root  420 2009-02-20 10:25 pppd-dns
lrwxrwxrwx 1 root root   21 2010-11-04 17:03 procps -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 2228 2010-03-26 20:51 pulseaudio
-rwxr-xr-x 1 root root 8863 2009-09-07 11:58 rc
-rwxr-xr-x 1 root root  801 2009-09-07 11:58 rc.local
-rwxr-xr-x 1 root root  117 2009-09-07 11:58 rcS
-rw-r--r-- 1 root root 1510 2009-09-07 11:58 README
-rwxr-xr-x 1 root root  639 2009-03-31 02:11 reboot
-rwxr-xr-x 1 root root 4399 2010-06-14 03:19 rsync
lrwxrwxrwx 1 root root   21 2010-11-04 16:33 rsyslog -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 2271 2010-04-15 00:16 saned
lrwxrwxrwx 1 root root   21 2010-11-04 17:09 screen-cleanup -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 3252 2010-09-06 09:44 sendsigs
-rwxr-xr-x 1 root root  590 2009-03-31 02:11 single
-rw-r--r-- 1 root root 4271 2009-09-07 11:58 skeleton
-rwxr-xr-x 1 root root 2014 2009-10-12 22:26 speech-dispatcher
-rwxr-xr-x 1 root root 3704 2010-09-14 11:20 ssh
-rwxr-xr-x 1 root root  519 2009-09-07 11:58 stop-bootlogd
-rwxr-xr-x 1 root root 1095 2009-09-07 11:58 stop-bootlogd-single
-rwxr-xr-x 1 root root  551 2010-07-06 10:44 sudo
-rwxr-xr-x 1 root root 3582 2009-01-23 10:48 sysklogd
-rwxr-xr-x 1 root root 6358 2010-08-10 15:19 tomcat6
-rwxr-xr-x 1 root root 7130 2010-06-24 06:56 tomcat6.dpkg-dist
lrwxrwxrwx 1 root root   21 2010-11-04 17:03 udev -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-11-04 17:03 udev-finish -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-11-04 17:03 udevmonitor -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-11-04 17:03 udevtrigger -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-11-04 17:09 ufw -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 2787 2009-11-05 05:03 umountfs
-rwxr-xr-x 1 root root 2075 2009-10-13 21:16 umountnfs.sh
-rwxr-xr-x 1 root root 1809 2010-09-22 07:15 umountroot
-rwxr-xr-x 1 root root  810 2010-04-29 07:46 unattended-upgrades
-rwxr-xr-x 1 root root 1997 2009-09-07 11:58 urandom
-rwxr-xr-x 1 root root 1342 2010-03-19 14:16 winbind
-rwxr-xr-x 1 root root 1758 2010-08-09 03:20 x11-common
cflewis@eisbox:~/argouml$ ls -l /etc/rc2.d/
total 4
lrwxrwxrwx 1 root root  20 2010-11-17 22:51 K21postgresql -> ../init.d/postgresql
lrwxrwxrwx 1 root root  24 2009-09-24 22:43 K21postgresql-8.3 -> ../init.d/postgresql-8.3
lrwxrwxrwx 1 root root  24 2010-11-17 22:51 K21postgresql-8.4 -> ../init.d/postgresql-8.4
-rw-r--r-- 1 root root 677 2010-11-01 09:36 README
lrwxrwxrwx 1 root root  19 2009-09-14 13:48 S01policykit -> ../init.d/policykit
lrwxrwxrwx 1 root root  18 2009-09-14 13:12 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx 1 root root  15 2009-09-14 13:12 S11klogd -> ../init.d/klogd
lrwxrwxrwx 1 root root  23 2010-01-06 00:38 S17mysql-ndb-mgm -> ../init.d/mysql-ndb-mgm
lrwxrwxrwx 1 root root  19 2010-01-06 00:38 S18mysql-ndb -> ../init.d/mysql-ndb
lrwxrwxrwx 1 root root  15 2010-01-06 00:38 S19mysql -> ../init.d/mysql
lrwxrwxrwx 1 root root  20 2010-11-04 16:41 S20fancontrol -> ../init.d/fancontrol
lrwxrwxrwx 1 root root  24 2010-10-26 13:02 S20hudsonslave.sh -> ../init.d/hudsonslave.sh
lrwxrwxrwx 1 root root  27 2010-11-04 15:52 S20speech-dispatcher -> ../init.d/speech-dispatcher
lrwxrwxrwx 1 root root  17 2010-11-19 21:01 S20tomcat6 -> ../init.d/tomcat6
lrwxrwxrwx 1 root root  17 2009-09-26 15:27 S20winbind -> ../init.d/winbind
lrwxrwxrwx 1 root root  19 2009-09-20 01:08 S25bluetooth -> ../init.d/bluetooth
lrwxrwxrwx 1 root root  20 2009-09-14 13:48 S50pulseaudio -> ../init.d/pulseaudio
lrwxrwxrwx 1 root root  15 2010-11-04 17:16 S50rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root  15 2009-09-20 01:09 S50saned -> ../init.d/saned
lrwxrwxrwx 1 root root  19 2009-09-14 13:16 S70dns-clean -> ../init.d/dns-clean
lrwxrwxrwx 1 root root  18 2009-09-14 13:16 S70pppd-dns -> ../init.d/pppd-dns
lrwxrwxrwx 1 root root  14 2010-11-04 17:15 S75sudo -> ../init.d/sudo
lrwxrwxrwx 1 root root  24 2009-09-20 01:08 S90binfmt-support -> ../init.d/binfmt-support
lrwxrwxrwx 1 root root  18 2010-02-26 18:54 S91lighttpd -> ../init.d/lighttpd
lrwxrwxrwx 1 root root  18 2009-09-17 22:41 S99fail2ban -> ../init.d/fail2ban
lrwxrwxrwx 1 root root  21 2010-11-04 15:52 S99grub-common -> ../init.d/grub-common
lrwxrwxrwx 1 root root  18 2009-09-20 00:55 S99nxsensor -> ../init.d/nxsensor
lrwxrwxrwx 1 root root  18 2009-09-20 00:55 S99nxserver -> ../init.d/nxserver
lrwxrwxrwx 1 root root  18 2009-09-14 13:12 S99ondemand -> ../init.d/ondemand
lrwxrwxrwx 1 root root  18 2009-09-14 13:12 S99rc.local -> ../init.d/rc.local

```

Thanks for all your help, wongo, I appreciate your efforts :)

---

### Post by wongo888 on 2010-11-22
Okay, I installed Tc6 on a virtual machine running 10.04 and I noticed that you are starting Tc earlier (S20). On my system, they start Tc later (S92) after the other web servers. It may be nothing though.

```

lrwxrwxrwx   1 root root   17 2010-05-22 17:12 S91apache2 -> ../init.d/apache2
lrwxrwxrwx   1 root root   18 2010-05-23 10:34 S91lighttpd -> ../init.d/lighttpd
lrwxrwxrwx   1 root root   17 2010-11-22 07:03 S92tomcat6 -> ../init.d/tomcat6

```

You also said that your made changes to the init.d script. Have you tried running it in xtrace / debug mode?

```
$ sudo dash -x /etc/init.d/tomcat6 start
```

The verbose mode gives even more info.

```
$ sudo dash -xv /etc/init.d/tomcat6 start
```

If that is fruitless, then you might want to try commenting out the "set -e" at the top of the script and looking for errors on reboot.

```

# set -e

```

---

