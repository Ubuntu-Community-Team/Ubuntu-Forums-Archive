---
title: "Server crash"
date: 2019-02-08
forum: Server Platforms
---

### Post by darkzea123 on 2019-02-08
[COLOR=#242729][FONT=Arial][FONT=inherit][FONT=inherit]
[COLOR=#242729][FONT=inherit]Hi People i use ubuntu a bit but not gone deep in to it so when things dont work im clueless on how fix them my current issue is i have a ubuntu server running on Intel DS-#1 Unmetered Bandwidth | Gigabit Conn. Any Linux/Windows* OS available! Intel Core i7-2600 - Quad Core (8t) 16GB RAM | 2x 3TB HDD Space[/FONT][/COLOR][/FONT][/FONT][/FONT][/COLOR][FONT=Arial][FONT=inherit]
[/FONT][/FONT]
[COLOR=#242729][FONT=Arial][FONT=inherit]Currently have ubuntu 18.04 server installed i have installed xfce & vnc4server (all working) i have downloaded 1000's of mkv vidoes with subtitles which i am converting to mp4 with this code
[/FONT]
> for f in *.mkv; do ffmpeg -i "$f" -y -vn -an -codec:s ass "$f.ass"; done
for i in *.mkv;   
do name=`echo "${i%.*}.mkv"`;   
ass="ass='$name'.ass"; 
echo "$ass";   ffmpeg -i "$i" -preset superfast  -vf "$ass" anime2/"${i%.mkv}.mp4"; done

[FONT=inherit]This all works fine no issue at all but at random amounts of time the server will crash and reboot but putty ssh will not show a reboot as it normally says the server has restarted if you login after a restart were as mine just shows last time i logged in there server has run for max off 22hrs on the code above with out crashing but it hasnt made it made past 24hrs sometimes it even crashes after 2hrs i assume it my code but the thing that gets me is when i did this exact same setup about 3 months ago i had 3 of the above scripts going on ultrafast with no crashes (i forgot to pay server bill in time and lost everything) if anyone has any idea of can help please do[/FONT]

[/FONT][/COLOR]

---

### Post by TheFu on 2019-02-08
mp4 and mkv are just containers.  It is very likely that you could playback the mkv file directly without issue.
However, if the player is stuck requiring .mp4 filenames, then you could very likely just copy the video and audio and subtitles/captions out of the mkv container into the mp4 container without any transcoding needed.  If you need more details about the specific tracks inside the mkv, there is mkvinfo tool. Extracting specific tracks is possible using mkvextract.

All my players prefer mkv containers and they support so many more capabilities than mp4, so I'm not good at going the other direction. But something like
**ffmpeg -i SOURCE.mkv -codec:a copy -codec:v copy TARGET.mp4** should work, but I haven't used ffmpeg for anything in a very long time.  Adding captions should be like you've shown, *-codec:s copy*, I'd guess.

Why transcode to mp4?  Doesn't make sense.

My main transcoding machine is very stable. It never crashes.  Only after a kernel update do I force a reboot.  I own the hardware, so there aren't any bills to pay to keep it running.

---

### Post by darkzea123 on 2019-02-08
Thanks for this but the videos have subtitles that dont show on html5 players with out pressing the subtitle button since i want the files to watchable with subs they need to be hardcoded with subtitles 

thank you though do you think that the reason my server crashing though?

---

### Post by Doug S on 2019-02-08
Is there any hint from any log file in /var/log?
Suggest you run this command always, for example in it's own ssh session:

```
sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,PkgTmp,PkgWatt,IRQ --interval 15
```turbostat is included in the linux-tools-common package. Watch mainly the processor package temperature, and is it getting hot.

Otherwise, we don't have a lot of information to go on.

Readers: Also look for comments and/or answers to the same question posted on [askubuntu]("https://askubuntu.com/questions/1116761/why-is-ubuntu-keep-crashing").

---

### Post by darkzea123 on 2019-02-08
Hi Thanks for the reply 
there a few files in the log section anyone i should keep an eye on alot off it looks alien to me 

ill run turbostat and see if that helps 
server ran for 3hrs this time before crashing

and thanks im the one that posted on askubuntu :)

---

### Post by Doug S on 2019-02-08
> **darkzea123 said:**
> there a few files in the log section anyone i should keep an eye on alot off it looks alien to me You need to search through them all, and yes it might take considerable time. Myself, I would start with /var/log/kern.log and /var/log/syslog.

The kern.log file includes a time since boot time stamp, in addition to the date and time, and so it is easy for one to find the spot where the re-boot occurred. Example:
```
Feb  1 10:01:21 s15 kernel: [133507.592678] capability: warning: `turbostat' uses 32-bit capabilities (legacy support in use)
Feb  1 14:29:23 s15 kernel: [149589.732394] perf: interrupt took too long (2501 > 2500), lowering kernel.perf_event_max_sample_rate to 79000
Feb  1 14:46:36 s15 kernel: [150623.326578] SGI XFS with ACLs, security attributes, realtime, no debug enabled
Feb  1 14:46:36 s15 kernel: [150623.334558] JFS: nTxBlock = 8192, nTxLock = 65536
Feb  1 14:46:36 s15 kernel: [150623.367992] ntfs: driver 2.1.32 [Flags: R/O MODULE].
Feb  1 14:46:36 s15 kernel: [[COLOR="#FF0000"]150623.420378[/COLOR]] QNX4 filesystem 0.2.3 registered.
Feb  1 14:50:00 s15 kernel: [    [COLOR="#FF0000"]0.000000[/COLOR]] microcode: microcode updated early to revision 0x2e, date = 2018-04-10
Feb  1 14:50:00 s15 kernel: [    0.000000] Linux version 5.0.0-rc4-boost (doug@s15) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.11)) #558 SMP PREEMPT Fri Feb 1 14:20:30 PST 2019
Feb  1 14:50:00 s15 kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-5.0.0-rc4-boost root=UUID=bcbc624b-892b-46ca-9e9e-102daf644170 ro ipv6.disable=1 consoleblank=300 cpuidle.governor=teo
Feb  1 14:50:00 s15 kernel: [    0.000000] KERNEL supported cpus:

```So in the example, I would look backwards from "Feb  1 14:50:00".

(However in my case, I asked it to re-boot, as shown in /var/log/auth.log:

```
Feb  1 14:49:05 s15 sudo:     doug : TTY=tty1 ; PWD=/home/doug ; USER=root ; [COLOR="#FF0000"]COMMAND=/sbin/shutdown -r now[/COLOR]
``` )

EDIT: Oh, I forgot. also see if there is anything in /var/crash . Although that stuff can be really hard to decipher.

---

### Post by darkzea123 on 2019-02-08
Hi so the error at time of shutdown is this 
> Feb  8 21:16:38 Ubuntu-1804-bionic-64-minimal kernel: [   33.985324] rfkill: input handler disabled
Fbit capabilities (legacy support in use)

thank you

Also my auth.log is filled with 1000's of people trying to login to my server constantly updating could this be the cause of the crashes?

---

### Post by Doug S on 2019-02-08
> **darkzea123 said:**
> Hi so the error at time of shutdown is this 

```
Feb 8 21:16:38 Ubuntu-1804-bionic-64-minimal kernel: [ 33.985324] rfkill: input handler disabled Fbit capabilities (legacy support in use) 
```
That actually doesn't make sense to me, because your uptime is only 34 seconds. I would have expected longer before a crash.

> **darkzea123 said:**
> Also my auth.log is filled with 1000's of people trying to login to my server constantly updating could this be the cause of the crashes?No, that would not be why it crashed. Now, we digress a little, but: You might want to consider changing the SSH port or implementing some sort of automatic identify and block bad guys iptables rules. I have been using this for many many years:

```
# Dynamic Badguy List. Detect and DROP Bad IPs that do password attacks on SSH.
# Once they are on the BADGUY list then DROP all packets from them.
#$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j LOG --log-prefix "SSH BAD:" --log-level info
#$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 5400 --name BADGUY_SSH -j DROP
# Sometimes make the lock time very long. Typically to try to get rid of coordinated attacks from China.
$IPTABLES -A INPUT -i $EXTIF -m recent --mask $BIT_MASK --update --hitcount 3 --seconds 90000 --name BADGUY_SSH -j LOG --log-prefix "SSH BAD:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -m recent --mask $BIT_MASK --update --hitcount 3 --seconds 90000 --name BADGUY_SSH -j DROP
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 -m recent --mask $BIT_MASK --set --name BADGUY_SSH -j ACCEPT

```Where:
```
# The location of the iptables program
#
IPTABLES=/sbin/iptables

#Setting the EXTERNAL and INTERNAL interfaces and addresses for the network
#
EXTIF="enp4s0"
INTIF="enp2s0"
EXTIP="XXX.XXX.XXX.XXX"
INTNET="192.168.111.0/24"
INTIP="192.168.111.1/32"
UNIVERSE="0.0.0.0/0"

#Arbitrary bit mask for the automatic IP blocking stuff (v2.08)
#
BIT_MASK="255.255.252.0"

```Note that as the attacks (mainly from China) became more and more sophisticated, a couple of years ago I switched to include "BIT_MASK", in an attempt to catch bad-guys merely switching to a different IP address on the same sub-net once they got blocked.

Anyway, the saga continues, and now I use ipset and block China, Russia, Ukraine, and Hong Kong entirely.
The only reason I use port 22 for SSH is that I study this stuff.

---

### Post by darkzea123 on 2019-02-08
Thanks for that! i was planning on using fail2ban but your method is so much better thank you! also please see the kern log and see if im missing somthing 

also my server is hour fast from gmt time 
[https://paste.ubuntu.com/p/zpWgCcwD3j/](https://paste.ubuntu.com/p/zpWgCcwD3j/)

Okay just had another crash turbostat 
> 76.82   3501    52183   78      63.8777.75   3500    55463   77      64.24
75.50   3500    51345   76      63.38
77.72   3501    57085   76      64.11
75.57   3501    45935   77      63.47
77.44   3501    44054   78      64.08
85.25   3502    50709   78      67.14
82.90   3502    58741   77      65.51
83.92   3502    57566   79      65.44
77.00   3501    60917   77      64.18
73.40   3499    43614   76      62.93
73.07   3503    43194   77      62.74
77.28   3503    50751   78      64.28
78.11   3503    52697   78      63.72
68.91   3501    43562   73      61.21
73.49   3500    42152   77      62.66
74.75   3499    45482   77      63.15
77.48   3500    46568   77      64.23
74.71   3503    41944   76      63.30
68.00   3504    35398   76      60.71
70.30   3500    38768   75      61.47
66.40   3504    33375   74      60.11
71.07   3502    36678   76      61.82
72.16   3502    37990   75      62.10
72.48   3502    37816   76      62.27
77.46   3500    43585   77      63.96
77.66   3501    43820   77      64.26
71.65   3501    44293   76      62.13
72.05   3501    37165   76      62.17
73.78   3501    39425   76      62.78
75.31   3502    39419   76      63.36
72.30   3503    37341   76      62.32
72.96   3504    36480   77      62.46
74.56   3503    38445   77      63.01
75.90   3500    45448   76      63.62
78.57   3502    41927   77      64.59
75.17   3502    39253   76      63.47
75.75   3501    40047   77      63.74
76.90   3501    42042   77      64.10
73.33   3501    39489   78      62.78
72.59   3501    39317   76      62.59
70.93   3502    39938   76      61.81
74.86   3501    41211   76      63.19
76.18   3502    43238   77      63.72
75.76   3501    40807   75      63.77
73.31   3502    40649   75      62.42
72.55   3501    46434   77      62.42




Auth log 
> 
Feb  9 00:00:04 Ubuntu-1804-bionic-64-minimal systemd-logind[865]: Watching system buttons on /dev/input/event1 (Power Button)
Feb  9 00:00:04 Ubuntu-1804-bionic-64-minimal systemd-logind[865]: Watching system buttons on /dev/input/event0 (Power Button)
Feb  9 00:00:04 Ubuntu-1804-bionic-64-minimal systemd-logind[865]: Watching system buttons on /dev/input/event2 (AT Translated Set 2 keyboard)
Feb  9 00:00:04 Ubuntu-1804-bionic-64-minimal systemd-logind[865]: New seat seat0.
Feb  9 00:00:08 Ubuntu-1804-bionic-64-minimal sshd[1084]: Server listening on 0.0.0.0 port 22.
Feb  9 00:00:08 Ubuntu-1804-bionic-64-minimal sshd[1084]: Server listening on :: port 22.
Feb  9 00:00:11 Ubuntu-1804-bionic-64-minimal gdm-launch-environment]: pam_unix(gdm-launch-environment:session): session opened for user gnome-initial-setup by (uid=0)
Feb  9 00:00:11 Ubuntu-1804-bionic-64-minimal systemd-logind[865]: New session c1 of user gnome-initial-setup.
Feb  9 00:00:11 Ubuntu-1804-bionic-64-minimal systemd: pam_unix(systemd-user:session): session opened for user gnome-initial-setup by (uid=0)
Feb  9 00:00:15 Ubuntu-1804-bionic-64-minimal gnome-keyring-daemon[1205]: couldn't access control socket: /run/user/123/keyring/control: No such file or directory
Feb  9 00:00:21 Ubuntu-1804-bionic-64-minimal sshd[1276]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=218.92.1.146  user=root
Feb  9 00:00:23 Ubuntu-1804-bionic-64-minimal sshd[1276]: Failed password for root from 218.92.1.146 port 46523 ssh2
Feb  9 00:00:26 Ubuntu-1804-bionic-64-minimal sshd[1276]: Failed password for root from 218.92.1.146 port 46523 ssh2
Feb  9 00:00:26 Ubuntu-1804-bionic-64-minimal gnome-keyring-daemon[1474]: another secret service is running
Feb  9 00:00:28 Ubuntu-1804-bionic-64-minimal sshd[1276]: Failed password for root from 218.92.1.146 port 46523 ssh2
[FONT=arial black]**Feb  9 00:00:28 Ubuntu-1804-bionic-64-minimal sshd[1276]: Received disconnect from 218.92.1.146 port 46523:11:  [preauth]**[/FONT]
Feb  9 00:00:28 Ubuntu-1804-bionic-64-minimal sshd[1276]: Disconnected from authenticating user root 218.92.1.146 port 46523 [preauth]
Feb  9 00:00:28 Ubuntu-1804-bionic-64-minimal sshd[1276]: PAM 2 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=218.92.1.146  user=root
Feb  9 00:00:42 Ubuntu-1804-bionic-64-minimal dbus-daemon[845]: [system] Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
Feb  9 00:01:13 Ubuntu-1804-bionic-64-minimal sshd[1503]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=218.92.1.146  user=root
Feb  9 00:01:14 Ubuntu-1804-bionic-64-minimal sshd[1503]: Failed password for root from 218.92.1.146 port 27035 ssh2
Feb  9 00:05:27 Ubuntu-1804-bionic-64-minimal sshd[1693]: Accepted password for root from [FONT=arial black]**myip**[/FONT] port 62106 ssh2
Feb  9 00:05:27 Ubuntu-1804-bionic-64-minimal sshd[1693]: pam_unix(sshd:session): session opened for user root by (uid=0)
Feb  9 00:05:27 Ubuntu-1804-bionic-64-minimal systemd: pam_unix(systemd-user:session): session opened for user root by (uid=0)
Feb  9 00:05:27 Ubuntu-1804-bionic-64-minimal systemd-logind[865]: New session 2 of user root.

kern log 
> Feb  8 23:57:38 Ubuntu-1804-bionic-64-minimal kernel: [ 9694.714128] [UFW BLOCK] IN=enp4s0 OUT= MAC=c8:60:00:5e:bd:41:84:c1:c1:76:aa:6e:08:00 SRC=125.227.220.138 DST=78.47.166.105 LEN=40 TOS=0x00 PREC=0x00 TTL=244 ID=12514 PROTO=TCP SPT=47110 DPT=1433 WINDOW=1024 RES=0x00 SYN URGP=0 
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00Feb  9 00:00:04 Ubuntu-1804-bionic-64-minimal kernel: [    0.000000] Linux version 4.15.0-45-generic (buildd@lgw01-amd64-031) (gcc version 7.3.0 (Ubuntu 7.3.0-16ubuntu3)) #48-Ubuntu SMP Tue Jan 29 16:28:13 UTC 2019 (Ubuntu 4.15.0-45.48-generic 4.15.18)

---

### Post by TheFu on 2019-02-08
To look through all the log files, 
```
egrep -i 'error|warn' /var/log/*g
```

That narrows down the files and provides the line number and text ... look just above the error.


If you move ssh to a different port, pretty much all the attacks will stop.  Then put in fail2ban.  If you change the port at the router and leave the default on the server (port translation), then fail2ban is pre-configured.  If you don't/can't modify the router to do the translation, then the fail2ban config must be altered for the ssh jail with the new port.

ipset totally rocks. Block about 8,000 subnets using it and add a few more every week. Same countries and a few more as Doug.  This all depends on where your clients (customers and sales teams) might be whether you can block as aggressively.  Allowing key-only access to ssh solves lots of issues too, but it is best not to even have the log entries for 20K attempts a day.

---

### Post by TheFu on 2019-02-08
Please use **code** tags whenever posting command output/logs.  Much easier to read for us. We are used to monospace fonts, which "code" tags do.

---

### Post by SeijiSensei on 2019-02-08
> also my server is hour fast from gmt time 

You probably have the wrong timezone. Check the contents of /etc/timezone.

---

### Post by Doug S on 2019-02-08
All those NULL characters (/00/00) in your kern.log file are due to the crash.

The turbostat output suggests that your processor is not getting too hot. (hot, but not too hot).
By the way, my main test server has the "K" version of the same Intel processor as you, i7-2600K.

The pastbin kern.log doesn't reveal the reasons for the crashes. Although it is interesting how many times the max perf interrupt rate steps down. For example, this is fairly normal:

```
Feb  8 21:03:27 Ubuntu-1804-bionic-64-minimal kernel: [13075.874962] perf: interrupt took too long (2524 > 2500), lowering kernel.perf_event_max_sample_rate to 79000
```but I think this is    not so normal:

```
Feb  7 20:27:06 Ubuntu-1804-bionic-64-minimal kernel: [18968.250853] perf: interrupt took too long (5059 > 5032), lowering kernel.perf_event_max_sample_rate to 39500
```Perhaps a red herring though, not sure.

Where is this kernel from?:```
Linux version 4.15.0-45-generic (buildd@lgw01-amd64-031) (gcc version 7.3.0 (Ubuntu 7.3.0-16ubuntu3)) #48-Ubuntu SMP Tue Jan 29 16:28:13 UTC 2019 (Ubuntu 4.15.0-45.48-generic 4.15.18)
```I did not realize this was a minimal install (even though it is written everywhere). Your computer is more than capable of a normal server installation.

Suggest you try a normal kernel (either generic or low latency):
```
4.15.0-45-generic #48-Ubuntu SMP Tue Jan 29 16:28:13 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```

Here is the turbostat output for my system, fully loaded CPUs:```
doug@s15:~$ sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,PkgTmp,PkgWatt,IRQ --interval 15
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt
100.00  3500    120540  79      63.91
100.00  3500    120508  79      63.94
100.00  3500    120527  79      64.00
100.00  3500    120550  79      64.03
100.00  3500    120508  80      64.06
100.00  3500    120532  79      64.01

```

---

