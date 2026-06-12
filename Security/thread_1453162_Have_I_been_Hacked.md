---
title: "Have I been Hacked?"
date: 2010-04-12
forum: Security
---

### Post by ReggieRareBreed on 2010-04-12
New user to Ubuntu, please help.
:
Before you ask:
I do NOT have any Browsers open
I do NOT have any e-mail open.
I just re-booted and did netstat -npl and these are the results which I have no idea about????

```
root@reggie-desktop:~# netstat -npl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1688/cupsd      
tcp6       0      0 ::1:631                 :::*                    LISTEN      1688/cupsd      
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1265/dhclient   
udp        0      0 0.0.0.0:36452           0.0.0.0:*                           1110/avahi-daemon: 
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           1110/avahi-daemon: 
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     6070     1512/X              /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     9435     3138/gnome-keyring- /tmp/keyring-jb1GTC/socket
unix  2      [ ACC ]     STREAM     LISTENING     9677     3213/ssh-agent      /tmp/ssh-IxGcLL3153/agent.3153
unix  2      [ ACC ]     STREAM     LISTENING     13064    3369/evolution-alar /tmp/orbit-reggie/linc-d29-0-7a58ecf416e2
unix  2      [ ACC ]     STREAM     LISTENING     13126    3954/evolution-exch /tmp/orbit-reggie/linc-f72-0-7a58ecfb12a6
unix  2      [ ACC ]     STREAM     LISTENING     9729     3221/pulseaudio     /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     9732     3221/pulseaudio     /home/reggie/.pulse/68ffb467626687e0b95d4bf14bbb7292-runtime/native
unix  2      [ ACC ]     STREAM     LISTENING     9791     3228/gconfd-2       /tmp/orbit-reggie/linc-c9c-0-68409d8d45f9b
unix  2      [ ACC ]     STREAM     LISTENING     10017    3226/gconf-helper   /tmp/orbit-reggie/linc-c9a-0-6753219f4bbe9
unix  2      [ ACC ]     STREAM     LISTENING     10064    3238/seahorse-agent /tmp/seahorse-ImrvLM/S.gpg-agent
unix  2      [ ACC ]     STREAM     LISTENING     10107    3153/gnome-session  /tmp/.ICE-unix/3153
unix  2      [ ACC ]     STREAM     LISTENING     10156    3153/gnome-session  /tmp/orbit-reggie/linc-c51-0-2e2b69dc903dc
unix  2      [ ACC ]     STREAM     LISTENING     10242    3238/seahorse-agent /tmp/orbit-reggie/linc-ca6-0-319f6b1ac265e
unix  2      [ ACC ]     STREAM     LISTENING     10313    3138/gnome-keyring- /tmp/orbit-reggie/linc-c42-0-4c1e1e87d10ca
unix  2      [ ACC ]     STREAM     LISTENING     10319    3138/gnome-keyring- /tmp/keyring-jb1GTC/socket.ssh
unix  2      [ ACC ]     STREAM     LISTENING     10321    3138/gnome-keyring- /tmp/keyring-jb1GTC/socket.pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     10400    3274/gnome-settings /tmp/orbit-reggie/linc-cca-0-7fd2b9e1dff6c
unix  2      [ ACC ]     STREAM     LISTENING     10419    3275/seahorse-daemo /tmp/orbit-reggie/linc-ccb-0-15e440ba532f1
unix  2      [ ACC ]     STREAM     LISTENING     10567    3308/notify-osd     /tmp/orbit-reggie/linc-cec-0-20dfcf5a2d76e
unix  2      [ ACC ]     STREAM     LISTENING     10740    3309/metacity       /tmp/orbit-reggie/linc-ced-0-839f0d82783
unix  2      [ ACC ]     STREAM     LISTENING     10789    3346/gnome-panel    /tmp/orbit-reggie/linc-d12-0-35e03c94a4480
unix  2      [ ACC ]     STREAM     LISTENING     11076    3366/bonobo-activat /tmp/orbit-reggie/linc-d26-0-582eeda3e5
unix  2      [ ACC ]     STREAM     LISTENING     11473    3383/trashapplet    /tmp/orbit-reggie/linc-d37-0-16b1905544511
unix  2      [ ACC ]     STREAM     LISTENING     6569     1462/gdm-simple-sla @/tmp/gdm-greeter-UAPsUQmr
unix  2      [ ACC ]     STREAM     LISTENING     11631    3364/nautilus       /tmp/orbit-reggie/linc-d24-0-4f2345fd6581d
unix  2      [ ACC ]     STREAM     LISTENING     11639    3374/gnome-power-ma /tmp/orbit-reggie/linc-d2e-0-6e86f3a266cf9
unix  2      [ ACC ]     STREAM     LISTENING     11671    3408/gnome-screensa /tmp/orbit-reggie/linc-d43-0-37cf562071d56
unix  2      [ ACC ]     STREAM     LISTENING     11724    3389/nm-applet      /tmp/orbit-reggie/linc-d3d-0-413d276593e0d
unix  2      [ ACC ]     STREAM     LISTENING     11734    3402/update-notifie /tmp/orbit-reggie/linc-d4a-0-163035d99b90d
unix  2      [ ACC ]     STREAM     LISTENING     11749    3401/bluetooth-appl /tmp/orbit-reggie/linc-d49-0-549bec35aae78
unix  2      [ ACC ]     STREAM     LISTENING     11919    3433/indicator-appl /tmp/orbit-reggie/linc-d69-0-4a4866b551dbc
unix  2      [ ACC ]     STREAM     LISTENING     11971    3438/indicator-appl /tmp/orbit-reggie/linc-d6e-0-69e9ec0b6a1ea
unix  2      [ ACC ]     STREAM     LISTENING     12181    3483/indicator-sess /tmp/orbit-reggie/linc-d9b-0-4052ee82cda46
unix  2      [ ACC ]     STREAM     LISTENING     13213    3958/evolution-data /tmp/orbit-reggie/linc-f76-0-569ca2fe6dd59
unix  2      [ ACC ]     STREAM     LISTENING     13344    4012/gnome-nettool  /tmp/orbit-reggie/linc-fac-0-269bf209a7d30
unix  2      [ ACC ]     STREAM     LISTENING     145998   4652/gnome-terminal /tmp/orbit-reggie/linc-122c-0-3cc7289b1ec3c
unix  2      [ ACC ]     STREAM     LISTENING     2859     1/init              @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     5698     1377/acpid          /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     4420     1088/dbus-daemon    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     8626     1462/gdm-simple-sla @/tmp/gdm-session-hLVXftTZ
unix  2      [ ACC ]     STREAM     LISTENING     6235     1649/atieventsd     /var/run/atieventsd.socket
unix  2      [ ACC ]     STREAM     LISTENING     6069     1512/X              @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     5070     1111/hald           @/var/run/hald/dbus-K2VZSFhcDS
unix  2      [ ACC ]     STREAM     LISTENING     10106    3153/gnome-session  @/tmp/.ICE-unix/3153
unix  2      [ ACC ]     STREAM     LISTENING     6309     1688/cupsd          /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     9690     3217/dbus-daemon    @/tmp/dbus-2xYSL0qF40
unix  2      [ ACC ]     STREAM     LISTENING     5063     1110/avahi-daemon:  /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     5117     1111/hald           @/var/run/hald/dbus-Ssof8gM5XR
root@reggie-desktop:~#
```


Any assistance very much appreciated.  Reg

---

### Post by rookcifer on 2010-04-12
First of all *why* do you think you've been hacked?

And I see nothing suspicious in that log.

---

### Post by CharlesA on 2010-04-12
Running as root for a reason?

I don't see anything unusual about the netstat.

---

### Post by drvista on 2010-04-13
try 
$ nmap localhost

---

### Post by adam814 on 2010-04-13
I don't see anything suspicious there.  The only internet "servers" are dhclient, avahi, and cups.  All of those are normal enough.  All those below it are only listening on the loopback interface, not an actual network.

---

### Post by 3rdalbum on 2010-04-13
It all looks normal to me.

If you'd been given a rootkit, then your copy of netstat would be replaced with the rootkit's copy, which naturally would not show anything incriminating.

So if you have any reason to believe that you've been attacked, the best thing to do would be to boot up with a live CD and run a rootkit hunter from there.

---

### Post by ReggieRareBreed on 2010-04-15
Hi Guys, many thanx for the assistance, but...
After making my original post, I was re-booting my PC when this message appeared on my screen:

Ubuntu 9.10 reggierarebreed-desktop tty1
reggierarebreed-desktop login: [34687.757560] md: Stopping al md deices
[34688.728411] Inbound IN=etho OUT=MAC=**:**:**:**:(this is my MAC address here) :ae:00:1e:14:01:08:00
SRC=121.12.169.126 DST=**.***.**.*** (this is my ip address here) LEN=40 TOS=0X00 PREC=0X00 TTL=104 ID=256 PROT=TCP SPT=6000 DPT=1433 WINDOW=16384 RES=0X00 SYN URGP=0
[34688.750567] sd2:0:0:0: [sdb] Sychronizing SCSI Cache
[34688.750731] sd:0:0:0:0: [sdb] Stopping disk
[34688.909270] sd:0:0:1:0: [sdb] Sychronizing SCSI Cache
[34688.909463] sd:0:0:1:0: [sdb] Stopping disk
[34688.352761] ACPI: Preparing to enter system sleep state S5
[34688.35333* missed this number) Disabling non-boot CPUs ...

I checked this ip address from another PC and found the source in China ??
Not to sure what is going on with my PC as this is a 'clean install', formatted hard drive and new version of Ubuntu 9.10

When I re-booted my PC there were NO browsers, e-mail or any application connected to the Internet.

Just a little concerned....

Have a nice day... Reg

---

### Post by OpSecShellshock on 2010-04-15
Looks like it's just a port scan. Happens all the time. You'd only need to worry if you had MS-SQL server listening on port 1433 and have that port forwarded in your hardware router. Since you're on a desktop build, I doubt that's the case.

---

### Post by ReggieRareBreed on 2010-04-15
> **OpSecShellshock said:**
> Looks like it's just a port scan. Happens all the time. You'd only need to worry if you had MS-SQL server listening on port 1433 and have that port forwarded in your hardware router. Since you're on a desktop build, I doubt that's the case.

Being a newbie, still learning and a little over cautious, many thanx.. Reg

---

### Post by LeeDaugherty on 2010-04-15
It's one of the greatest things about Ubuntu, coming from Windows.  You can relax now.  Don't do anything stupid of course, but the world isn't out to get you, and there are alot more people watching your back.  It is correct to be paranoid on Windows boxes of any weird sign, but it's safe here.  It's unfortunate, but port scans happen on every public ip less than every 5 minutes, and yes you will find most come from our economy-boosters across the sea.  It's annoying, but 99% of the time, they aren't going to waste their time with a linux box.  It's much easier to rem-ploit a Windows machine.  If it still keeps you up at night, look up some how-tos on how to shut off extrapalous ICMP responses.  If you don't respond when they scan you, it's like it never happend.

And it might be easier to read if you did 'netstat -tunlap' (and easier to remember).  It'll just give you the info you want.

---

### Post by TBABill on 2010-04-15
Here's some comfort for you to make you happy you are on Ubuntu and not Windows. Last night I got home from work and found my Win 7 laptop had a strange "virus scan" running in the lower right corner and prompting me to "fix" all the viruses it had found.  I could not get to file manager, c:\, Avast (my antivirus) or any other control app. I rebooted to see if I could quickly get to something...no joy.
 
Anyway, the program had a name and an icon on both the desktop and menu that looked fairly legit. i had an option to continue to run unprotected, but all that did was loop me back to the beginning where it tried to create fear of the viruses it claimed to have found and get me to activate it so it could fix the problem. I followed the prompts to allow it just so I would know what it was doing without me inputting any data and it went right to a credit card input screen. BIG RED FLAG!!
 
After a couple failed reboots, a blue screen of death and some other fighting I just booted into safe mode, found the path to the file(s) and deleted via command prompt. It was buried in a hidden folder (in Win explorer) called Program Data (not program files) and it was just a series of numbers as a folder with a single .exe file with the same name. 
 
It was an easy fix, but that thing could have really caused issues if it were a better trojan. My kids must have gotten the machine infected while I was at work, but on a Linux machine the file would have just sat dormant. Now I know why I love my Linux laptop more than the Win one!!!

---

