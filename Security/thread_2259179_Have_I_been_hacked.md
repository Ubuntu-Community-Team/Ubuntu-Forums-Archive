---
title: "Have I been hacked?"
date: 2015-01-02
forum: Security
---

### Post by sims080 on 2015-01-02
I recently installed 14.04.1 LTS trusty

I noticed some odd things. Cam light turned on and then off at start up. At one point the mouse was almost impossible to control. A file persistently xdh.php persistently attempted to download without any kind of initiation which caused all of the windows to wiggle. If I was hacked it must of happened last night because the cam light turned on when I started the laptop today. 

I am useless at interpretting this because I am noob. I realize it's a lot to look through. Thank you for the help.

```
[COLOR=#800000]sudo netstat -tup[/COLOR]

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp       28      0 192.168.0.19:34869      productsearch.ubu:https CLOSE_WAIT  2815/gvfsd-http 
tcp       28      0 192.168.0.19:41140      3rdpartymedia.ubu:https CLOSE_WAIT  2815/gvfsd-http 
tcp       28      0 192.168.0.19:44283      productsearch.ubu:https CLOSE_WAIT  2740/unity-scope-ho
tcp       28      0 192.168.0.19:41143      3rdpartymedia.ubu:https CLOSE_WAIT  2815/gvfsd-http 
tcp       28      0 192.168.0.19:43998      productsearch.ubu:https CLOSE_WAIT  2815/gvfsd-http 
tcp       28      0 192.168.0.19:37350      3rdpartymedia.ubu:https CLOSE_WAIT  2815/gvfsd-http 
tcp       28      0 192.168.0.19:37349      3rdpartymedia.ubu:https CLOSE_WAIT  2815/gvfsd-http 
tcp       28      0 192.168.0.19:37353      3rdpartymedia.ubu:https CLOSE_WAIT  2815/gvfsd-http 
tcp       28      0 192.168.0.19:43996      productsearch.ubu:https CLOSE_WAIT  2815/gvfsd-http 
tcp        0      0 192.168.0.19:32793      edge-star-shv-01-:https ESTABLISHED 3137/firefox    
tcp       28      0 192.168.0.19:41144      3rdpartymedia.ubu:https CLOSE_WAIT  2815/gvfsd-http 
tcp       28      0 192.168.0.19:34867      productsearch.ubu:https CLOSE_WAIT  2815/gvfsd-http 
tcp6       1      0 ip6-localhost:35996     ip6-localhost:ipp       CLOSE_WAIT  1193/cups-browsed
```

```
[COLOR=#800000]sudo lsof -i [/COLOR]

COMMAND    PID    USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
avahi-dae 1129   avahi   13u  IPv4  11640      0t0  UDP *:mdns 
avahi-dae 1129   avahi   14u  IPv6  11641      0t0  UDP *:mdns 
avahi-dae 1129   avahi   15u  IPv4  11642      0t0  UDP *:47940 
avahi-dae 1129   avahi   16u  IPv6  11643      0t0  UDP *:57255 
cups-brow 1193    root    6u  IPv6  19534      0t0  TCP ip6-localhost:35996->ip6-localhost:ipp (CLOSE_WAIT)
cups-brow 1193    root    8u  IPv4  17552      0t0  UDP *:ipp 
dhclient  1564    root    6u  IPv4  14633      0t0  UDP *:bootpc 
dhclient  1564    root   20u  IPv4  14623      0t0  UDP *:62657 
dhclient  1564    root   21u  IPv6  14624      0t0  UDP *:34023 
dnsmasq   1644  nobody    4u  IPv4  15720      0t0  UDP myhostname:domain 
dnsmasq   1644  nobody    5u  IPv4  15721      0t0  TCP myhostname:domain (LISTEN)
cupsd     2409    root   10u  IPv6  16602      0t0  TCP ip6-localhost:ipp (LISTEN)
cupsd     2409    root   11u  IPv4  16603      0t0  TCP localhost:ipp (LISTEN)
unity-sco 2740 myusername    4u  IPv4  25917      0t0  TCP 192.168.0.19:44283->productsearch.ubuntu.com:https (CLOSE_WAIT)
gvfsd-htt 2815 myusername    7u  IPv4  20072      0t0  TCP 192.168.0.19:34867->productsearch.ubuntu.com:https (CLOSE_WAIT)
gvfsd-htt 2815 myusername    8u  IPv4  18143      0t0  TCP 192.168.0.19:43996->productsearch.ubuntu.com:https (CLOSE_WAIT)
gvfsd-htt 2815 myusername   11u  IPv4  18145      0t0  TCP 192.168.0.19:43998->productsearch.ubuntu.com:https (CLOSE_WAIT)
gvfsd-htt 2815 myusername   18u  IPv4  19198      0t0  TCP 192.168.0.19:41144->3rdpartymedia.ubuntuone.com:https (CLOSE_WAIT)
gvfsd-htt 2815 myusername   19u  IPv4  19194      0t0  TCP 192.168.0.19:41140->3rdpartymedia.ubuntuone.com:https (CLOSE_WAIT)
gvfsd-htt 2815 myusername   20u  IPv4  19195      0t0  TCP 192.168.0.19:37349->3rdpartymedia.ubuntuone.com:https (CLOSE_WAIT)
gvfsd-htt 2815 myusername   24u  IPv4  18144      0t0  TCP 192.168.0.19:34869->productsearch.ubuntu.com:https (CLOSE_WAIT)
gvfsd-htt 2815 myusername   25u  IPv4  19196      0t0  TCP 192.168.0.19:37350->3rdpartymedia.ubuntuone.com:https (CLOSE_WAIT)
gvfsd-htt 2815 myusername   26u  IPv4  19197      0t0  TCP 192.168.0.19:41143->3rdpartymedia.ubuntuone.com:https (CLOSE_WAIT)
gvfsd-htt 2815 myusername   29u  IPv4  18150      0t0  TCP 192.168.0.19:37353->3rdpartymedia.ubuntuone.com:https (CLOSE_WAIT)

```

```
[COLOR=#800000]car /vat/log/auth.log

[/COLOR]Jan  2 10:17:51 myhostname compiz: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Jan  2 10:17:51 myhostname compiz: PAM adding faulty module: pam_kwallet.so
Jan  2 10:17:51 myhostname compiz: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "myusername"
Jan  2 10:24:55 myhostname compiz: gkr-pam: unlocked login keyring
Jan  2 10:39:46 myhostname compiz: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Jan  2 10:39:46 myhostname compiz: PAM adding faulty module: pam_kwallet.so
Jan  2 10:39:46 myhostname compiz: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "myusername"
Jan  2 11:03:50 myhostname systemd-logind[1149]: Lid closed.
Jan  2 11:03:50 myhostname systemd-logind[1149]: Suspending...
Jan  2 11:03:51 myhostname dbus[797]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.43" (uid=0 pid=1809 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.3" (uid=0 pid=1157 comm="NetworkManager ")
Jan  2 11:04:18 myhostname systemd-logind[1149]: Failed to send delayed message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Jan  2 11:08:35 myhostname systemd-logind[1149]: Lid opened.
Jan  2 11:08:43 myhostname unix_chkpwd[4063]: password check failed for user (myusername)
Jan  2 11:08:43 myhostname compiz: pam_unix(lightdm:auth): authentication failure; logname= uid=1000 euid=1000 tty= ruser= rhost=  user=myusername
Jan  2 11:08:45 myhostname compiz: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Jan  2 11:08:45 myhostname compiz: PAM adding faulty module: pam_kwallet.so
Jan  2 11:08:45 myhostname compiz: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "myusername"
Jan  2 11:08:52 myhostname compiz: gkr-pam: unlocked login keyring
Jan  2 11:17:01 myhostname CRON[4282]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  2 11:17:01 myhostname CRON[4282]: pam_unix(cron:session): session closed for user root
Jan  2 11:36:49 myhostname compiz: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Jan  2 11:36:49 myhostname compiz: PAM adding faulty module: pam_kwallet.so
Jan  2 11:36:49 myhostname compiz: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "myusername"
Jan  2 11:37:34 myhostname systemd-logind[1149]: Lid closed.
Jan  2 11:37:34 myhostname systemd-logind[1149]: Suspending...
Jan  2 12:00:23 myhostname systemd-logind[1149]: Operation finished.
Jan  2 12:00:23 myhostname systemd-logind[1149]: Lid opened.
Jan  2 12:00:27 myhostname dbus[797]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.43" (uid=0 pid=1809 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.3" (uid=0 pid=1157 comm="NetworkManager ")
Jan  2 12:00:29 myhostname unix_chkpwd[5094]: password check failed for user (myusername)
Jan  2 12:00:29 myhostname compiz: pam_unix(lightdm:auth): authentication failure; logname= uid=1000 euid=1000 tty= ruser= rhost=  user=myusername
Jan  2 12:00:32 myhostname compiz: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Jan  2 12:00:32 myhostname compiz: PAM adding faulty module: pam_kwallet.so
Jan  2 12:00:32 myhostname compiz: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "myusername"
Jan  2 12:11:25 myhostname systemd-logind[1149]: Lid closed.
Jan  2 12:11:25 myhostname systemd-logind[1149]: Suspending...
Jan  2 12:11:25 myhostname dbus[797]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.43" (uid=0 pid=1809 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.3" (uid=0 pid=1157 comm="NetworkManager ")
Jan  2 12:22:24 myhostname dbus[797]: [system] Rejected send message, 3 matched rules; type="error", sender=":1.63" (uid=1000 pid=2132 comm="/usr/bin/pulseaudio --start --log-target=syslog ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.1" (uid=0 pid=1010 comm="/usr/sbin/bluetoothd ")
Jan  2 12:22:24 myhostname systemd-logind[1149]: Operation finished.
Jan  2 12:22:24 myhostname systemd-logind[1149]: Lid opened.
Jan  2 12:22:24 myhostname systemd-logind[1149]: Power key pressed.
Jan  2 12:22:24 myhostname dbus[797]: message repeated 3 times: [ [system] Rejected send message, 3 matched rules; type="error", sender=":1.63" (uid=1000 pid=2132 comm="/usr/bin/pulseaudio --start --log-target=syslog ") interface="(unset)" member="(unset)" error name="org.freedesktop.DBus.Error.UnknownMethod" requested_reply="0" destination=":1.1" (uid=0 pid=1010 comm="/usr/sbin/bluetoothd ")]
Jan  2 12:22:28 myhostname dbus[797]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.43" (uid=0 pid=1809 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.3" (uid=0 pid=1157 comm="NetworkManager ")
Jan  2 12:22:38 myhostname compiz: gkr-pam: unlocked login keyring
Jan  2 12:24:00 myhostname sudo: pam_unix(sudo:auth): authentication failure; logname=myusername uid=1000 euid=0 tty=/dev/pts/0 ruser=myusername rhost=  user=myusername
Jan  2 12:24:17 myhostname sudo:  myusername : TTY=pts/0 ; PWD=/home/myusername ; USER=root ; COMMAND=/usr/bin/apt-get install Rkhunter
Jan  2 12:24:17 myhostname sudo: pam_unix(sudo:session): session opened for user root by myusername(uid=0)
Jan  2 12:24:17 myhostname sudo: pam_unix(sudo:session): session closed for user root
Jan  2 12:24:40 myhostname sudo:  myusername : TTY=pts/0 ; PWD=/home/myusername ; USER=root ; COMMAND=/usr/bin/rkhunter --check
Jan  2 12:24:40 myhostname sudo: pam_unix(sudo:session): session opened for user root by myusername(uid=0)
Jan  2 12:25:36 myhostname sudo: pam_unix(sudo:session): session closed for user root
Jan  2 12:40:45 myhostname sudo:  myusername : TTY=pts/0 ; PWD=/home/myusername ; USER=root ; COMMAND=/usr/bin/apt-get install shutter
Jan  2 12:40:45 myhostname sudo: pam_unix(sudo:session): session opened for user root by myusername(uid=0)
Jan  2 12:45:40 myhostname sudo: pam_unix(sudo:session): session closed for user root
Jan  2 12:46:50 myhostname gnome-keyring-daemon[1925]: keyring alias directory: /home/myusername/.local/share/keyrings
Jan  2 12:49:08 myhostname systemd-logind[1116]: New seat seat0.
Jan  2 12:49:08 myhostname systemd-logind[1116]: Watching system buttons on /dev/input/event2 (Power Button)
Jan  2 12:49:08 myhostname systemd-logind[1116]: Watching system buttons on /dev/input/event5 (Video Bus)
Jan  2 12:49:08 myhostname systemd-logind[1116]: Watching system buttons on /dev/input/event1 (Power Button)
Jan  2 12:49:08 myhostname systemd-logind[1116]: Watching system buttons on /dev/input/event0 (Lid Switch)
Jan  2 12:49:10 myhostname lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Jan  2 12:49:10 myhostname lightdm: PAM adding faulty module: pam_kwallet.so
Jan  2 12:49:11 myhostname lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Jan  2 12:49:11 myhostname systemd-logind[1116]: New session c1 of user lightdm.
Jan  2 12:49:11 myhostname systemd-logind[1116]: Linked /tmp/.X11-unix/X0 to /run/user/112/X11-display.
Jan  2 12:49:13 myhostname lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Jan  2 12:49:13 myhostname lightdm: PAM adding faulty module: pam_kwallet.so
Jan  2 12:49:13 myhostname lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "myusername"
Jan  2 12:49:23 myhostname lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Jan  2 12:49:23 myhostname lightdm: pam_unix(lightdm:session): session opened for user myusername by (uid=0)
Jan  2 12:49:23 myhostname systemd-logind[1116]: New session c2 of user myusername.
Jan  2 12:49:23 myhostname systemd-logind[1116]: Linked /tmp/.X11-unix/X0 to /run/user/1000/X11-display.
Jan  2 12:49:25 myhostname gnome-keyring-daemon[1637]: couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files
Jan  2 12:49:25 myhostname dbus[808]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.44" (uid=0 pid=1644 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.3" (uid=0 pid=1043 comm="NetworkManager ")
Jan  2 12:49:25 myhostname gnome-keyring-daemon[1637]: message repeated 2 times: [ couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files]
Jan  2 12:49:27 myhostname gnome-keyring-daemon[1637]: The PKCS#11 component was already initialized
Jan  2 12:49:27 myhostname gnome-keyring-daemon[1637]: The GPG agent was already initialized
Jan  2 12:49:27 myhostname gnome-keyring-daemon[1637]: The SSH agent was already initialized
Jan  2 12:49:27 myhostname gnome-keyring-daemon[1637]: The Secret Service was already initialized
Jan  2 12:49:28 myhostname polkitd(authority=local): Registered Authentication Agent for unix-session:c2 (system bus name :1.67 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Jan  2 12:49:44 myhostname systemd-logind[1116]: Removed session c1.
Jan  2 13:03:56 myhostname sudo: pam_unix(sudo:auth): authentication failure; logname=myusername uid=1000 euid=0 tty=/dev/pts/0 ruser=myusername rhost=  user=myusername
Jan  2 13:04:04 myhostname sudo:  myusername : 3 incorrect password attempts ; TTY=pts/0 ; PWD=/home/myusername ; USER=root ; COMMAND=/bin/netstat -tup
Jan  2 13:04:18 myhostname sudo:  myusername : TTY=pts/0 ; PWD=/home/myusername ; USER=root ; COMMAND=/bin/bash
Jan  2 13:04:18 myhostname sudo: pam_unix(sudo:session): session opened for user root by myusername(uid=0)
Jan  2 13:04:26 myhostname sudo:     root : TTY=pts/0 ; PWD=/home/myusername ; USER=root ; COMMAND=/bin/netstat -tup
Jan  2 13:04:26 myhostname sudo: pam_unix(sudo:session): session opened for user root by myusername(uid=0)
Jan  2 13:04:26 myhostname sudo: pam_unix(sudo:session): session closed for user root
Jan  2 13:05:59 myhostname sudo: pam_unix(sudo:session): session closed for user root
Jan  2 13:06:17 myhostname sudo: pam_unix(sudo:auth): authentication failure; logname=myusername uid=1000 euid=0 tty=/dev/pts/0 ruser=myusername rhost=  user=myusername
Jan  2 13:06:26 myhostname sudo:  myusername : TTY=pts/0 ; PWD=/home/myusername ; USER=root ; COMMAND=/usr/bin/lsof -i
Jan  2 13:06:26 myhostname sudo: pam_unix(sudo:session): session opened for user root by myusername(uid=0)
Jan  2 13:06:26 myhostname sudo: pam_unix(sudo:session): session closed for user root
Jan  2 13:08:51 myhostname sudo:  myusername : TTY=pts/0 ; PWD=/home/myusername ; USER=root ; COMMAND=/bin/bash
Jan  2 13:08:51 myhostname sudo: pam_unix(sudo:session): session opened for user root by myusername(uid=0)
Jan  2 13:17:01 myhostname CRON[3809]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan  2 13:17:01 myhostname CRON[3809]: pam_unix(cron:session): session closed for user root
```

I did run two rootkits but the only warning file was unhide.rb.

---

### Post by TheFu on 2015-01-02
Understand that the only way to detect rootkits is from alternate boot media, right?\

I didn't read everything above, but what I did see was just Ubuntu sending everything you searched for to different external vendors in case you wanted to buy something instead of run a program.  That is just ubuntu desktop doing what ubuntu desktop does.  If you don't like that, there are things you can do. Just ask.

Thanks for the code tags - having them on all the sections above would really help readability.

---

### Post by sims080 on 2015-01-02
Ok, I added the code tags. I didn't know you could only detect rootkits from alternate boot media.

---

### Post by TheFu on 2015-01-02
A rootkit modifies the running system and can hide anything while appearing to be fine.  To find them and many viruses, the only way is to mount the storage from outside the infected system to perform searches. Otherwise, the rootkit will simply hide itself from any processes searching for it in memory, the process table or on disk.

BTW - it appears you've left some prior formatting inside the code tags. Things aren't lining up correctly as a fixed-sized font should.
```

COMMAND     PID            USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME
sshd      19674            root    3u  IPv4  955490      0t0  TCP *:ssh (LISTEN)
ntpd      19731             ntp   18u  IPv4  954813      0t0  UDP localhost:ntp 
ntpd      19731             ntp   19u  IPv4  954814      0t0  UDP 192.168.122.1:ntp 

```See how these line up and are easy to read?

Still - I don't see anything suspicious in that output.

---

### Post by HermanAB on 2015-01-04
Did you play with VNC?  99.999% of the time that is how newbs get hacked.

---

### Post by thnewguy on 2015-01-04
The logs don't look suspecious to me, but if you want to make sure, you could backup your files and re-install the operating system. See if your fresh install behaves the same way. Doing a fresh install is a pain, but it will probably insure your machine is not compromised.

---

### Post by cogset on 2015-01-05
> **TheFu said:**
> A rootkit modifies the running system and can hide anything while appearing to be fine.  To find them and many viruses, the only way is to mount the storage from outside the infected system to perform searches. Otherwise, the rootkit will simply hide itself from any processes searching for it in memory, the process table or on disk.


That makes sense, however does that also mean that running tools such as chrootkit and rkhunter from a running system (as routine checks) is basically worthless ?

So how do you use them from an alternate boot media? Supposing that I have a multiboot system or a live CD, how do I check the suspicious partition from there?

---

### Post by mastablasta on 2015-01-06
you mount the partition from live media and then run the scan on that partition. there are also specialised CD's that provide live OS that basically when oyu run them they download latest virus definistions and asuch and then only do the scan for malware.

do you have ssh installed? did you open port for ssh from outside? 
did you mistype your password?: [FONT=Arial]Jan  2 13:04:04 myhostname sudo:  myusername : 3 incorrect password attempts ; TTY=pts/0 ; PWD=/home/myusername ; USER=root ; COMMAND=/bin/netstat -tup

you often open and close the laptop... :P[/FONT]

---

### Post by cogset on 2015-01-07
> **mastablasta said:**
> you mount the partition from live media and then run the scan on that partition. there are also specialised CD's that provide live OS that basically when oyu run them they download latest virus definistions and asuch and then only do the scan for malware.


Just to be clear, I'm not the OP, I've just chimed in (BTW, my apologies to sims080  for jumping in) because I was interested in this particular aspect of running rkhunter from an alternate boot media.
So, assuming I have a dual boot system comprised of OS 1 and OS 2 and I want to check OS 1, I have to boot into OS 2 ,mount the OS 1 partition(s) and then just run rkhunter from OS 2? 
No further action in this example is required  to scan OS 1 with rkhunter?

---

### Post by fugu2 on 2015-01-07
> **cogset said:**
> Just to be clear, I'm not the OP, I've just chimed in (BTW, my apologies to sims080  for jumping in) because I was interested in this particular aspect of running rkhunter from an alternate boot media.
So, assuming I have a dual boot system comprised of OS 1 and OS 2 and I want to check OS 1, I have to boot into OS 2 ,mount the OS 1 partition(s) and then just run rkhunter from OS 2? 
No further action in this example is required  to scan OS 1 with rkhunter?

You really don't even need a duel boot if you have a spare usb drive lying around. Download your OS's *.iso file from ubuntu.com, ```
sudo apt-get install unetbootin
``` to install unetbootin. Run unetbootin to drop that iso file into your usb drive (WARNING: this may erase all of your data on that drive, so use a fresh drive if you can or backup your bytes). then boot up to the usb drive and scan your hard drive with your new liveusb.

---

### Post by cogset on 2015-01-08
> **fugu2 said:**
> You really don't even need a duel boot if you have a spare usb drive lying around. Download your OS's *.iso file from ubuntu.com, ```
sudo apt-get install unetbootin
``` to install unetbootin. Run unetbootin to drop that iso file into your usb drive (WARNING: this may erase all of your data on that drive, so use a fresh drive if you can or backup your bytes). then boot up to the usb drive and scan your hard drive with your new liveusb.

Well I said dual boot because I already have that ;), my question was not so much about which boot media to use (I reckon you have plenty to choose from, regarding usb sticks I think you don't even need unetbootin, as there is usb-creator installed by default in latest releases) but rather about the specific issue of rkhunter scanning external partitions : does it scan all mounted partitions by default, as part of a normal system scan?
I thought that  rkhunter only searched in specific paths in the installed system.

_**EDIT**:_ well, after reading more carefully the man pages looks like the option I'm after would be ```
chhrootkit -r [path_to_mounted_media]
``` and ```
rkhunter --rootdir [path_to_mounted_media]
``` unfortunately the latter is currently deprecated and removed as of version 1.4.0 .

---

