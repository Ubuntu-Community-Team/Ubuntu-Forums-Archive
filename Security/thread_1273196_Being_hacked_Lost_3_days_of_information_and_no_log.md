---
title: "Being hacked? Lost 3 days of information and no log files"
date: 2009-09-23
forum: Security
---

### Post by seacyd on 2009-09-23
I encounter a strange situation: Log information on a computer is missing, sent emails are missing (3 days) and in one folder information is even back to an older state (possibly 2 month or more).

Has the computer being compromised overnight? 

Chronology of events:
Wednesday -1 week  - everything worked fine
Sunday  - everything worked fine
Monday - everything worked fine
Tuesday - everything worked fine

Today it was discovered that the database is at an old state (about 2 month old), sent emails are lost of last 3 days and no log files can be found for last 3 days (Sunday to Tuesday).


Kindly let me know your ideas and the best way to address this situation.


-- 
seacyd

---

### Post by cdenley on 2009-09-23
Maybe your hard drive failed, but worked fine when you rebooted. I've seen systems run for days with a failed hard drive. Everything seems to work fine as far as users can tell, but written data is only cached in memory and never makes it to the hard drive. When the write cache fills all your memory, then you notice the problems. I would expect I/O errors to appear on the console, though.

---

### Post by seacyd on 2009-09-23
Ok, thanks for sharing your idea about this issue.

What I did not tell you was that the computer was completely shutdown and restarted every new day. So I would guess the cache should have been written back to disk every day on shutdown.

What is strange is that I see in the directory /var/log the current log files as well as archieved log files. But there is the gap between 16th and 23rd (even though from 20th to 22nd there was activity)

```
(...)
-rw-r--r-- 1 root       root  78314 2009-09-16 11:48 Xorg.0.log.old
-rw-r--r-- 1 root       root 178235 2009-09-23 07:09 udev
(...)
```

There is only one user accessing the system regularly (family business). What I do not understand is, if somebody compromised the system, would this person not just modify the log files instead of deleting the log files completely?

If the system is compromised, are there possibilities to analyse it without having an intrusion detection system installed?

---

### Post by cdenley on 2009-09-23
They could have simply deleted the log files since it is easier than editing them. It would prevent you from determining where they are connecting from. I'm not sure why an attacker would delete logs such as Xorg.0.log within a certain date range, e-mail, or recent database records, though. If they were trying to be destructive, I would expect something like "rm -rf /", assuming they got root, or at least delete all e-mail and database records.

I think all you can do is inspect any logs that are still there, or search for rootkits or anything that may have been left behind. If you suspect your system is compromised, you can never be 100% sure it is safe to use until you inspect and backup important files then reinstall ubuntu.

What kind of servers do you use? Have you set a root password?
```

sudo netstat -tlnp

```

---

### Post by seacyd on 2009-09-23
Only CUPS, privoxy and tor are running: 

```
Aktive Internetverbindungen (Nur Server)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:8118          0.0.0.0:*               LISTEN      5246/privoxy    
tcp        0      0 0.0.0.0:631             0.0.0.0:*               LISTEN      2891/cupsd      
tcp        0      0 127.0.0.1:9050          0.0.0.0:*               LISTEN      2560/tor        
tcp6       0      0 :::631                  :::*                    LISTEN      2891/cupsd  
```

Additional information:

Thanks for the rootkit tip. I installed rkhunter but got only few warnings, which do not appear to be dangerous to me?:

```

   /usr/sbin/unhide                                         [ Warning ]
(...)
    /usr/sbin/unhide-linux26                                 [ Warning ]

[Press <ENTER> to continue]
 Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]

and in the log file this information is provided:
[17:12:07] Warning: Suspicious file types found in /dev:
[17:12:07]          /dev/shm/pulse-shm-190707849: data

```

---

### Post by cdenley on 2009-09-23
Is there a reason cups is listening for remote connections? Is your server a print server? Is it firewalled?

---

### Post by seacyd on 2009-09-23
No - actually I thought it was listening to the local 192.168 network only. I need to change this.

Is there any known exploit through CUPSD?

---

### Post by cdenley on 2009-09-23
Yes, depending on the version you're using, but AppArmor should prevent an attacker from deleting stuff.
[http://www.ubuntu.com/usn/usn-760-1](http://www.ubuntu.com/usn/usn-760-1)
Sevices can only bind to interfaces, not subnets. Generally, it either listens on the local loopback interface, or any interface.

---

### Post by seacyd on 2009-09-23
Thanks - I added the Listen lines (127.0.0.1:631 and not disclosed for 192.168.???.???) and Allow 192.168.???.0/24 within the various brackets  at cupsd.conf)

I executed the following apparmor command:
--
APPARMOR
# sudo apparmor_status 
apparmor module is loaded.
8 profiles are loaded.
8 profiles are in enforce mode.
   /usr/lib/connman/scripts/dhclient-script
   /usr/share/gdm/guest-session/Xsession
   /usr/sbin/tcpdump
   /usr/lib/cups/backend/cups-pdf
   /sbin/dhclient3
   /usr/sbin/cupsd
   /sbin/dhclient-script
   /usr/lib/NetworkManager/nm-dhcp-client.action
0 profiles are in complain mode.
1 processes have profiles defined.
1 processes are in enforce mode :
   /usr/sbin/cupsd (30466) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.
---

I further checked with "tiger" 
wajig install tiger

sudo tiger

Out of the lengthy report under /var/log/tiger I copy here some lines what I consider to be the most interesting:


# Checking listening processes 
--WARN-- [lin003w] The process `avahi-daemon' is listening on socket 36925
         (UDP on every interface) is run by avahi.
--WARN-- [lin003w] The process `avahi-daemon' is listening on socket 5353 (UDP
         on every interface) is run by avahi.
--WARN-- [lin002i] The process `cupsd' is listening on socket 631 (UDP) on
         every interface.
--WARN-- [lin003w] The process `ntpd' is listening on socket 123 (UDP on every
         interface) is run by ntp.
--WARN-- [lin003w] The process `ntpd' is listening on socket 123 (UDP on
         192.168.178.6 interface) is run by ntp.

# Looking for unusual device files...
--ALERT-- [fsys006a] Unexpected device files found:
crw------- 1 root root 5, 1 Jul 28 07:00 /lib/udev/devices/console
crw-r----- 1 root kmem 1, 2 Jul 28 07:00 /lib/udev/devices/kmem
brw------- 1 root root 7, 0 Jul 28 07:00 /lib/udev/devices/loop0
crw------- 1 root root 10, 200 Jul 28 07:00 /lib/udev/devices/net/tun
crw------- 1 root root 1, 3 Jul 28 07:00 /lib/udev/devices/null
crw------- 1 root root 108, 0 Jul 28 07:00 /lib/udev/devices/ppp
lrwxrwxrwx 1 root root 15 Jul 28 07:00 /lib/udev/devices/stderr -> /proc/self/fd/2


--
I further issued the command chkrootkit:

sudo chkrootkit

Nothing found.

---

### Post by openfly on 2009-09-23
Nothing is DIRECTLY indicative of an exploit.

You might want to checksum your kernel and core binaries and compare them to a stock build.  Do this with a livecd to be certain.

---

### Post by seacyd on 2009-09-24
Thanks for the tip:

I checked md5sum of the following files, all appear to be fine:

```
c052c7ef7eed49274a6f929ea46d80b8  vmlinuz-2.6.28-15-generic

8c55cc2b4b9ab893fd17acf80f0ce8d7  /usr/sbin/exim4
13408cbc2eb5c02107a94628e58ab496  /usr/lib/pt_chown
8d7d52a76c726cac931906dcc1e4a2aa  /usr/lib/openssh/ssh-keysign
6f194b76a4bd396ccd486c9423d0d249  /usr/bin/gpasswd
ca8fde040c4f9e97656be7bbd2e38760  /usr/bin/sudoedit
ca8fde040c4f9e97656be7bbd2e38760  /usr/bin/sudo
534048d07fd501602fa229805a7586d1  /bin/su
f799b022ccacd70f00b2343a6efb2ae9  /usr/bin/chsh
d64cea605d137954196bc46ee56001e9  /usr/lib/eject/dmcrypt-get-device
be6a4569264663afdd00f70545df0319  /usr/lib/policykit/polkit-resolve-exe-helper
0adca5154514899d48a30b391bb63a4a  /usr/lib/policykit/polkit-grant-helper-pam
caa511c650c544f12e830f2af3af2860  /usr/bin/X
5cc4ff60e4058586aa5ca15833a646db  /usr/bin/lppasswd
```
---

As further analysis tool I understand mactime might be useful. Unfortunately, I have not figured it out how to use it. I understand to use grave-robber first, but I get this error message to which I have not found any information on the Internet.

```
# grave-robber -v
cannot exec /bin/hostname: No such file or directory
cannot exec /bin/uname -n: No such file or directory
cannot exec /bin/df: No such file or directory

```
--
One further remark, regarding running servers, there is also exim4 running but tied to 127.0.0.1.:

netstat -tlnp

tcp        0      0 127.0.0.1:25            0.0.0.0:*              LISTEN      2875/exim4

---

### Post by Chayak on 2009-09-26
Though missing a few days of logs does raise flags there's nothing to really indicate a compromise.  Deleting the log files is a bit above script kiddie level as they don't tend to even be aware of logs or .bash_history files it's still far below someone skilled at linux hacking as they would "*grep -v <their source address>*" and write it out ot a file to remove all log entries specific to their ip. Then they overwrite the original log and touch it to match the date and time of the last log entry.

If there is no backdoor then you could have someone logging in with ssh.  There are thousands of ways to hide backdoors in *nix systems and a few of them are very hard to find even by experts.  My advise is to remove your network cable from the machine, copy your important files off onto an external harddrive after booting the machine from the live CD and then reinstall being sure to change your passwords.  I do security research and penetration testing for a living so I tend to lean on the safer side of things when it comes to a suspect machine or anomalous activity from a machine.

---

### Post by ApEkV2 on 2009-09-26
You could make a script that searches log files and greps for matching entries (like "sudo:" etc).
Put it in your crontab for daily execution, and send the output to a directory like ~/Public (for example).
So you could possibly find and log some unauthorized activity on your computer.

Here's an example of a script that does this.  (don't hate, I made it)
It searches Logs: system messages, auth.log, deamon.log, bash history. 
And outputs the results to ~/Public in the form of a txt file.

```
#!/bin/bash
znet=`netstat -a | grep 'LISTEN'`
zconn=`echo "$znet" | grep tcp`
zconn2=`sudo netstat -tlnp`

zombies=`ps aux | awk '{ print $8 " " $2 }' | grep -w Z`

znewfile=`date +%b-%d-%T`
zmonth=`date +%b`
zday=`date +%e`

zlog1=`cat /var/log/messages | grep "kernel:"`
zlog2=`echo "$zlog1" | grep "$zmonth $zday"`

zlog3=`cat /var/log/auth.log | grep "sudo:"`
zlog8=`cat /var/log/auth.log | grep "dbus-daemon:"`
zlog4=`echo "$zlog3" | grep "$zmonth $zday"`
zlog9=`echo "$zlog8" | grep "$zmonth $zday"`

zlog5=`cat /var/log/daemon.log | grep "init:"`
zlog7A=`cat /var/log/daemon.log | grep "started"`
zlog6=`echo "$zlog5" | grep "$zmonth $zday"`
zlog7=`echo "$zlog7A" | grep "$zmonth $zday"`

bashH=`cat ~/.bash_history`

echo "This is a daily log check: $znewfile" > ~/Public/$znewfile.txt
echo -e "Logs: Listening TCP ports, Zombies, system messages, auth.log, deamon.log, bash history: \r " >> ~/Public/$znewfile.txt
echo "LISTENING TCP PORTS" >> ~/Public/$znewfile.txt
echo "$zconn" >> ~/Public/$znewfile.txt
echo "$zconn2" >> ~/Public/$znewfile.txt
echo "ZOMBIES (there usually are none)" >> ~/Public/$znewfile.txt
echo -e "$zombies\r" >> ~/Public/$znewfile.txt
echo "MESSAGES LOG" >> ~/Public/$znewfile.txt
echo -e "$zlog2\r" >> ~/Public/$znewfile.txt
echo "AUTH.LOG" >> ~/Public/$znewfile.txt
echo "$zlog4" >> ~/Public/$znewfile.txt
echo -e "$zlog9\r" >> ~/Public/$znewfile.txt
echo "DAEMON.LOG" >> ~/Public/$znewfile.txt
echo "$zlog6" >> ~/Public/$znewfile.txt
echo -e "$zlog7\r" >> ~/Public/$znewfile.txt
echo "BASH HISTORY" >> ~/Public/$znewfile.txt
echo "$bashH" >> ~/Public/$znewfile.txt 
```

[color=red] EDIT: just figured out that date was wrong (should be +%b-%d-%T), and some other changes. [/color]

---

### Post by seacyd on 2009-09-30
Thank you all for your replies! 

@ApEkV2: Thanks for your script - I have implemented it at my system.

---

### Post by ApEkV2 on 2009-09-30
No problem.

---

### Post by seacyd on 2009-11-01
Here a concluding update to the puzzling situation  - when I finally got hands on the system physically, instead of remotely, I discovered more strange patterns: Emails that got pulled from the server twice, even though everything was downloaded the day before, files magically disappearing... 

The solution to the riddle was:

* The **system had 2 identicial partitions** - cloned one's. Both partitions were sharing the **same UUID** and fstab used the UUID to identify the root parition. So, the good news is, there was no hacking or intrusion into the system. All syslogs are complete, however they were put on 2 separate root disk partitions.

As the fstab was setup to boot via UUID, the system sort of randomly (or is there a logic pattern behind this?) chose the one or the other partition to boot from. On one day the original partition got booted, on the other day it was the cloned or fake original one. On a low usage system this kind of mirroring of drives caused only little irritation (email downloaded twice) but did not really cause any further confusion; until some day this September. 

For completeness, here are some links and commands that might come useful for handling a similar situation:

Show UUID:
ls -al /dev/disk/by-uuid
blkid

fstab - check if UUID is used
# MyBook Partition 6 (Musik)
UUID=123b0f18-456a-4a92-a17e-123ef2ec0456    /media/mymountname  ext3  defaults,users,noatime,noauto    0    0

tune2fs -U 

Links:
[http://www.cyberciti.biz/faq/linux-finding-using-uuids-to-update-fstab/](http://www.cyberciti.biz/faq/linux-finding-using-uuids-to-update-fstab/)
[http://wiki.linuxquestions.org/wiki/Tune2fs](http://wiki.linuxquestions.org/wiki/Tune2fs)
[http://ubuntuforums.org/showthread.php?t=326871](http://ubuntuforums.org/showthread.php?t=326871)
[http://linux.byexamples.com/archives/321/fstab-with-uuid/](http://linux.byexamples.com/archives/321/fstab-with-uuid/)

---

