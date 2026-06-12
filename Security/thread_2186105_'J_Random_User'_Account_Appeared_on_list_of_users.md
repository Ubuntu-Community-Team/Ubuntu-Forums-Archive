---
title: "'J Random User' Account Appeared on list of users?"
date: 2013-11-05
forum: Security
---

### Post by XProflmfao on 2013-11-05
Hello everyone,

When I clicked on my Ubuntu power (start?) button on the top-right corner, a user account by the name of "J Random User" appeared on the list of users in-between the Guest account and my main account that I'm currently using. I restarted my computer and now the user account has disappeared. Should I be worried that my computer has been compromised by someone/something, or is there a logical explanation for this?

Edit: Just to clarify, I'm currently using Ubuntu 13.10.

---

### Post by QIII on 2013-11-05
[I]Moved to [B]Security Discussions.

[/B][/I]Jonn Q. Public, J Random User and J Random Hacker are folks you *don't *want to see...

---

### Post by cariboo on 2013-11-06
Have you got a remote desktop client, or desktop sharing enabled with a simple or no password?

---

### Post by Piesu on 2013-11-06
I got today exactly same issue, I didn't rebooted system yet - only disconnected it from Internet. I have ssh server and TeamViewer on my computer, but ssh shouldn't be a issue as my laptop isn't visible from Internet.

---

### Post by bashiergui on 2013-11-09
But how many users is it visible to on your WiFi network?

---

### Post by gjasso on 2013-11-18
I experienced exactly the same issue. I can confirm that the account disappeared after rebooting.

As a safety measure, I formatted my hard drive, reinstalled Ubuntu, and I am changing my passwords.

Is it possible that this is a bug, or was my system compromised? How could that have happened? How could this have been avoided?

---

### Post by iangeorgerichards on 2013-11-24
Spotting a "J Random User" is why I ended up at this message, it seeming to be the only relevant thing Google has revealed.
I noticed "J.Random User" in the list when I went to logoff five minutes ago.

---

### Post by bashiergui on 2013-11-24
To all three ussrs that saw "J Random User" show up, please run these commands and post the results
```
w
```and ```
sudo service --status-all
```
run them when you see the user account show up again and also right now.

---

### Post by bashiergui on 2013-11-24
Better yet just run this and post the output```
grep *random* /var/log/auth.log | less
```

---

### Post by letrec on 2013-11-25
Same here. New installation of Ubuntu 13.10.

Installed skype, emacs, vlc, clementin, vbox (and windows 8 in it), xchat, wireshark, htop, qbittorent, dropbox.

> <my-username>@metropolis:~$ sudo grep *random* /var/log/auth.log
Nov 25 22:09:23 metropolis sudo:    <my-username> : TTY=pts/0 ; PWD=/home/<my-username> ; USER=root ; COMMAND=/bin/grep *random* /var/log/auth.log

> 
<my-username>@metropolis:~$ w
 22:13:45 up  1:08,  2 users,  load average: 0,12, 0,24, 0,61
USER                   TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
<my-username>    tty7     :0               21:06    1:07m  4:07   0.15s init --user
<my-username>    pts/0    :0               22:04    1.00s  0.19s  0.00s w

> <my-username>@metropolis:~$ sudo service --status-all
 [ + ]  acpid
 [ + ]  anacron
 [ + ]  apparmor
 [ ? ]  apport
 [ + ]  avahi-daemon
 [ + ]  bluetooth
 [ - ]  brltty
 [ + ]  console-font
 [ + ]  console-setup
 [ + ]  cron
 [ + ]  cups
 [ + ]  cups-browsed
 [ - ]  dbus
 [ ? ]  dns-clean
 [ + ]  friendly-recovery
 [ - ]  grub-common
 [ ? ]  irqbalance
 [ - ]  kerneloops
 [ ? ]  killprocs
 [ + ]  kmod
 [ ? ]  lightdm
 [ ? ]  networking
 [ ? ]  ondemand
 [ - ]  openvpn
 [ ? ]  pppd-dns
 [ - ]  procps
 [ - ]  pulseaudio
 [ ? ]  rc.local
 [ + ]  resolvconf
 [ + ]  rfkill-restore
 [ + ]  rfkill-store
 [ - ]  rsync
 [ + ]  rsyslog
 [ + ]  saned
 [ ? ]  sendsigs
 [ + ]  setvtrgb
 [ ? ]  speech-dispatcher
 [ - ]  sudo
 [ + ]  udev
 [ ? ]  umountfs
 [ ? ]  umountnfs.sh
 [ ? ]  umountroot
 [ - ]  unattended-upgrades
 [ - ]  urandom
 [ ? ]  vboxautostart-service
 [ + ]  vboxballoonctrl-service
 [ + ]  vboxdrv
 [ + ]  vboxweb-service
 [ - ]  x11-common


---

### Post by bashiergui on 2013-11-25
None of that looked concerning. Multiple users having the same odd behavior make it unlikely that this is malicious. It looks a lot like a placeholder in dev code that went to production without being fixed.

---

### Post by Piesu on 2013-11-26
> **bashiergui said:**
> It looks a lot like a placeholder in dev code that went to production without being fixed.


I was thinking same thing, but wasn't able to find such string in sources. But maybe I wasn't able to find correct sources, as this problem could be created by many programs. 

Anyway, I didn't found other sensible way of unprivileged person getting into my system other then firefox or repository, I don't understand why he would like to show me that he get into, and didn't found anything else suspicious on computer.


Anyway, installed new system, I must be able to trust system. 

Anybody was able to find such string in any source code?

---

### Post by bashiergui on 2013-11-26
If you see the behavior again take some screen shots and submit a bug report to launchpad. Let the devs find it.

---

### Post by fdsuufijjejejejej on 2014-01-23
Just noticed this on 13.10... it's incredibly alarming

[ATTACH=CONFIG]249699[/ATTACH]



No other users are listed in the "Users" section. 



awk -F":" '{ print "Linux_name: " $1 "\t\tFull_Name: " $5 }' /etc/passwd yields:


```

Linux_name: root        Full_Name: root
Linux_name: daemon        Full_Name: daemon
Linux_name: bin        Full_Name: bin
Linux_name: sys        Full_Name: sys
Linux_name: sync        Full_Name: sync
Linux_name: games        Full_Name: games
Linux_name: man        Full_Name: man
Linux_name: lp        Full_Name: lp
Linux_name: mail        Full_Name: mail
Linux_name: news        Full_Name: news
Linux_name: uucp        Full_Name: uucp
Linux_name: proxy        Full_Name: proxy
Linux_name: www-data        Full_Name: www-data
Linux_name: backup        Full_Name: backup
Linux_name: list        Full_Name: Mailing List Manager
Linux_name: irc        Full_Name: ircd
Linux_name: gnats        Full_Name: Gnats Bug-Reporting System (admin)
Linux_name: nobody        Full_Name: nobody
Linux_name: libuuid        Full_Name: 
Linux_name: syslog        Full_Name: 
Linux_name: messagebus        Full_Name: 
Linux_name: usbmux        Full_Name: usbmux daemon,,,
Linux_name: dnsmasq        Full_Name: dnsmasq,,,
Linux_name: avahi-autoipd        Full_Name: Avahi autoip daemon,,,
Linux_name: kernoops        Full_Name: Kernel Oops Tracking Daemon,,,
Linux_name: rtkit        Full_Name: RealtimeKit,,,
Linux_name: whoopsie        Full_Name: 
Linux_name: speech-dispatcher        Full_Name: Speech Dispatcher,,,
Linux_name: avahi        Full_Name: Avahi mDNS daemon,,,
Linux_name: lightdm        Full_Name: Light Display Manager
Linux_name: pulse        Full_Name: PulseAudio daemon,,,
Linux_name: hplip        Full_Name: HPLIP system user,,,
Linux_name: colord        Full_Name: colord colour management daemon,,,
Linux_name: saned        Full_Name: 
Linux_name: ainola        Full_Name: Ainola
Linux_name: ntp        Full_Name:


```



Likely a gnome dev inserting test code as was mentioned above: [https://en.wikipedia.org/wiki/J._Random_Hacker](https://en.wikipedia.org/wiki/J._Random_Hacker)

---

