---
title: "Strange activity"
date: 2011-04-29
forum: Security
---

### Post by GeorgeTI on 2011-04-29
Hello to everyone. I seek help regarding a series of... how do I call it? Out of the ordinary activities. Well, here goes:

1. When I use Transmission, the hard disk activity according to GKrellM skyrockets. I know this should be normal, but this happens at increased intensity lately. Usually the disk activity is about 10-400K, not the 20M it shows

2. When I use nmap on me (127.0.0.1) here are the results:

```
Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2011-04-29 14:48 EEST
Interesting ports on localhost (127.0.0.1):
Not shown: 991 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
25/tcp   open  smtp
53/tcp   open  domain
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
1723/tcp open  pptp
3128/tcp open  squid-http
```

Nmap done: 1 IP address (1 host up) scanned in 0.13 seconds

While I understand most of the ports, pptp, ipp and squid-http are a bit... off. Especially pptp.

3. Last night I noticed wireless lan activity (mostly by the blinking light of the router) and decided to shut down my PC. When I clicked the button top-right, the guest-session had a V by it. I do have the impression that this means the guest session is active, and I am fairly sure I did not activate it. Also, no, none other has physical access to my PC.

4. After that I looked at the logs for the guest account (which I had never enabled) I saw this at the syslog:

```
gdm-simple-slave[27346]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Apr 29 02:28:43 MyComputer acpid: client connected from 27348[0:0]
Apr 29 02:28:43 MyComputer acpid: 1 client rule loaded
Apr 29 02:28:46 MyComputer gdm-session-worker[27364]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Apr 29 02:28:46 MyComputer gdm-session-worker[27364]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Apr 29 02:28:46 MyComputer gdm-session-worker[27374]: WARNING: Could not copy file to cache: Error opening file '/var/cache/gdm/guest/dmrc': Permission denied
Apr 29 02:28:47 MyComputer kernel: [45136.967153] type=1503 audit(1304033327.927:27):  operation="capable" pid=27469 parent=27468 profile="/usr/share/gdm/guest-session/Xsession" name="dac_override"
Apr 29 02:28:47 MyComputer kernel: [45136.967159] type=1503 audit(1304033327.927:28):  operation="capable" pid=27469 parent=27468 profile="/usr/share/gdm/guest-session/Xsession" name="dac_read_search"
Apr 29 02:28:47 MyComputer rtkit-daemon[1790]: Sucessfully made thread 27477 of process 27477 (n/a) owned by 'guest' high priority at nice level -11.
Apr 29 02:28:47 MyComputer rtkit-daemon[1790]: Supervising 5 threads of 2 processes of 2 users.
Apr 29 02:28:48 MyComputer rtkit-daemon[1790]: Sucessfully made thread 27487 of process 27477 (n/a) owned by 'guest' RT at priority 5.
Apr 29 02:28:48 MyComputer rtkit-daemon[1790]: Supervising 6 threads of 2 processes of 2 users.
Apr 29 02:28:48 MyComputer rtkit-daemon[1790]: Sucessfully made thread 27497 of process 27477 (n/a) owned by 'guest' RT at priority 5.
Apr 29 02:28:48 MyComputer rtkit-daemon[1790]: Supervising 7 threads of 2 processes of 2 users.
Apr 29 02:28:48 MyComputer rtkit-daemon[1790]: Sucessfully made thread 27501 of process 27477 (n/a) owned by 'guest' RT at priority 5.
Apr 29 02:28:48 MyComputer rtkit-daemon[1790]: Supervising 8 threads of 2 processes of 2 users.
Apr 29 02:28:48 MyComputer rtkit-daemon[1790]: Sucessfully made thread 27505 of process 27505 (n/a) owned by 'guest' high priority at nice level -11.
Apr 29 02:28:48 MyComputer rtkit-daemon[1790]: Supervising 9 threads of 3 processes of 2 users.
Apr 29 02:28:48 MyComputer pulseaudio[27505]: pid.c: Daemon already running.
Apr 29 02:28:48 MyComputer kernel: [45137.901344] type=1503 audit(1304033328.864:29):  operation="open" pid=27480 parent=27374 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="::c" denied_mask="::c" fsuid=123 ouid=0 name="/etc/compizconfig/config"
Apr 29 02:28:48 MyComputer kernel: [45137.918962] type=1503 audit(1304033328.879:30):  operation="open" pid=27480 parent=27374 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="::c" denied_mask="::c" fsuid=123 ouid=0 name="/etc/compizconfig/config"
Apr 29 02:28:48 MyComputer kernel: [45137.919295] type=1503 audit(1304033328.879:31):  operation="open" pid=27480 parent=27374 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="::c" denied_mask="::c" fsuid=123 ouid=0 name="/etc/compizconfig/config"
Apr 29 02:28:48 MyComputer kernel: [45137.919432] type=1503 audit(1304033328.879:32):  operation="open" pid=27480 parent=27374 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="::c" denied_mask="::c" fsuid=123 ouid=0 name="/etc/compizconfig/config"
Apr 29 02:28:48 MyComputer kernel: [45137.919739] type=1503 audit(1304033328.879:33):  operation="open" pid=27480 parent=27374 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="::c" denied_mask="::c" fsuid=123 ouid=0 name="/etc/compizconfig/config"
Apr 29 02:28:48 MyComputer kernel: [45137.919878] type=1503 audit(1304033328.879:34):  operation="open" pid=27480 parent=27374 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="::c" denied_mask="::c" fsuid=123 ouid=0 name="/etc/compizconfig/config"
Apr 29 02:28:48 MyComputer kernel: [45137.920216] type=1503 audit(1304033328.883:35):  operation="open" pid=27480 parent=27374 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="::c" denied_mask="::c" fsuid=123 ouid=0 name="/etc/compizconfig/config"
Apr 29 02:28:53 MyComputer kernel: [45142.741277] __ratelimit: 3 callbacks suppressed
Apr 29 02:28:53 MyComputer kernel: [45142.741280] type=1503 audit(1304033333.703:37):  operation="mknod" pid=27455 parent=1 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="c::" denied_mask="c::" fsuid=123 ouid=123 name="/etc/gconf/gconf.xml.mandatory/.testing.writeability"
Apr 29 02:28:53 MyComputer kernel: [45142.741337] type=1503 audit(1304033333.703:38):  operation="mknod" pid=27455 parent=1 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="c::" denied_mask="c::" fsuid=123 ouid=123 name="/etc/gconf/gconf.xml.system/.testing.writeability"
Apr 29 02:28:53 MyComputer kernel: [45142.741373] type=1503 audit(1304033333.703:39):  operation="mknod" pid=27455 parent=1 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="c::" denied_mask="c::" fsuid=123 ouid=123 name="/etc/gconf/gconf.xml.defaults/.testing.writeability"
Apr 29 02:29:00 MyComputer kernel: [45149.854020] type=1503 audit(1304033340.816:40):  operation="mknod" pid=27588 parent=1 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="c::" denied_mask="c::" fsuid=123 ouid=123 name="/etc/gconf/gconf.xml.mandatory/.testing.writeability"
Apr 29 02:29:00 MyComputer kernel: [45149.854068] type=1503 audit(1304033340.816:41):  operation="mknod" pid=27588 parent=1 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="c::" denied_mask="c::" fsuid=123 ouid=123 name="/etc/gconf/gconf.xml.system/.testing.writeability"
Apr 29 02:29:00 MyComputer kernel: [45149.854104] type=1503 audit(1304033340.816:42):  operation="mknod" pid=27588 parent=1 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="c::" denied_mask="c::" fsuid=123 ouid=123 name="/etc/gconf/gconf.xml.defaults/.testing.writeability"
Apr 29 02:29:00 MyComputer gdm-session-worker[27592]: WARNING: Could not copy file to cache: Error opening file '/var/cache/gdm/guest/dmrc': Permission denied
Apr 29 02:29:01 MyComputer acpid: client 27348[0:0] has disconnected
Apr 29 02:29:01 MyComputer acpid: client connected from 1085[0:0]
Apr 29 02:29:01 MyComputer acpid: 1 client rule loaded
Apr 29 02:29:07 MyComputer gnome-screensaver-dialog: pam_sm_authenticate: Called
Apr 29 02:29:07 MyComputer gnome-screensaver-dialog: pam_sm_authenticate: username = [MyUser]
Apr 29 02:29:07 MyComputer gnome-screensaver-dialog: pam_sm_authenticate: /home/MyUser is already mounted
Apr 29 02:29:18 MyComputer sudo: pam_sm_authenticate: Called
Apr 29 02:29:18 MyComputer sudo: pam_sm_authenticate: username = [MyUser]
Apr 29 02:29:18 MyComputer sudo: pam_sm_authenticate: /home/MyUser is already mounted
Apr 29 02:30:01 MyComputer CRON[27715]: (root) CMD (if [ -x /usr/bin/gsmsmsrequeue ]; then /usr/bin/gsmsmsrequeue; fi)
Apr 29 02:30:19 MyComputer kernel: [45228.037928] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Apr 29 02:30:19 MyComputer kernel: [45228.038022] ===>rtl8192se_link_change():ieee->iw_mode is 2
Apr 29 02:30:20 MyComputer kernel: [45229.562283] ===>rtl8192se_link_change():ieee->iw_mode is 2
Apr 29 02:30:39 MyComputer kernel: Kernel logging (proc) stopped.
Apr 29 02:30:39 MyComputer rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="779" x-info="http://www.rsyslog.com"] exiting on signal 15.
```

I have searched a bit through the forums, but found nothing relevant. I know I am being paranoid, but hey, paranoia can be fully justified if you look what can be done though a screen and a keyboard... and I do not talk about the movies, but the security tutorials. So, if you could be so kind and helpful, can you tell me:
-Is my machine compromised or I am just paranoid?
-If it is, how can I fix this? Is just re-installing Ubuntu going to solve the problem?

Thank you in advance.

P.S. the smilies represent 8 - )  I don't know how to disable them :P

---

### Post by SeijiSensei on 2011-04-29
> **GeorgeTI said:**
> 1. When I use Transmission, the hard disk activity according to GKrellM skyrockets. I know this should be normal, but this happens at increased intensity lately. Usually the disk activity is about 10-400K, not the 20M it shows

How busy the disk is depends on the number of peers and bandwidth.  The more chunks that arrive at your computer, the more disk activity you'll see.  You might try using the option in most clients to preallocate space for the torrent, but it usually doesn't matter much on Linux systems with ext3/ext4 file systems.

> 2. When I use nmap on me (127.0.0.1) here are the results:

127.0.0.1 has no firewalling.  Run nmap against the external IP address of the machine, and you're likely to see very different results.

---

### Post by GeorgeTI on 2011-04-29
Well, I just now did the nmap scan locally (192.168.1.69) and at my internet ip (from [www.whatismyip.com](www.whatismyip.com)) and the results were these:

```
Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2011-04-29 16:15 EEST
Interesting ports on MyComputer (192.168.1.69):
Not shown: 993 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
53/tcp   open  domain
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
1723/tcp open  pptp
3128/tcp open  squid-http
```

Nmap done: 1 IP address (1 host up) scanned in 0.19 seconds

Some ports are closed here, but the pptp and squid thing persist.

Now at the global ip address:
```
Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2011-04-29 16:16 EEST
Interesting ports on dsldevice.lan (XXX.XXX.XXX.XXX):
Not shown: 995 filtered ports
PORT     STATE SERVICE
21/tcp   open  ftp
23/tcp   open  telnet
80/tcp   open  http
443/tcp  open  https
1723/tcp open  pptp
```

Nmap done: 1 IP address (1 host up) scanned in 6.18 seconds

I noted that the nmap scanned my router and not me, but still there is the pptp service open. As far as I know, pptp is usually used with broadband usb-stick modems, or when you connect to a remote PC (I am not sure if Remote Desktop Viewer uses that port too). Is it normal for my computer to have this port open? I occasionally use a broadband USB modem, but not at that time, or this one.
I do fear I'll have to configure iptables o.o the horror....

---

### Post by matt_symes on 2011-04-29
Hi

> PORT STATE SERVICE
21/tcp open ftp
23/tcp open telnet
80/tcp open http
443/tcp open https
1723/tcp open pptp

What does ```
lsof -i
``` say ?

Kind regards

---

### Post by GeorgeTI on 2011-04-29
COMMAND    PID       USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
firefox-b 2394 MyUser   69u  IPv4  18553      0t0  TCP MyComputer.lan:55962->ww-in-f102.1e100.net:www (ESTABLISHED)

Well, now it is only Firefox (obviously :D). 
Anyone has any ideas about the whole guest thing? Is it any normal procedure that takes place? This 'guest' had started a process, and had some "open" and "mknod" operations going, and tried to open the compizconfig configuration and to create a file ".testing.writeability". It just doesn't make sense to me... Anyone else looked at the syslog section with Log File Viewer?

CORRECTION: The above was printed while I was logged in as a Desktop User, this is what was printed when I was logged in as root:
```
COMMAND    PID        USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
smbd       778        root   22u  IPv6   4320      0t0  TCP *:microsoft-ds (LISTEN)
smbd       778        root   23u  IPv6   4322      0t0  TCP *:netbios-ssn (LISTEN)
avahi-dae  868       avahi   13u  IPv4   4443      0t0  UDP *:mdns 
avahi-dae  868       avahi   14u  IPv4   4445      0t0  UDP *:44689 
named     1234        bind   20u  IPv6   5068      0t0  TCP *:domain (LISTEN)
named     1234        bind   21u  IPv4   5073      0t0  TCP localhost:domain (LISTEN)
named     1234        bind   22u  IPv4   5076      0t0  TCP localhost:953 (LISTEN)
named     1234        bind   23u  IPv6   5077      0t0  TCP localhost:953 (LISTEN)
named     1234        bind   25u  IPv4   9848      0t0  TCP MyComputer.lan:domain (LISTEN)
named     1234        bind  512u  IPv6   5067      0t0  UDP *:domain 
named     1234        bind  513u  IPv4   5072      0t0  UDP localhost:domain 
named     1234        bind  514u  IPv4   9847      0t0  UDP MyComputer.lan:domain 
exim4     1504 Debian-exim    3u  IPv4   5270      0t0  TCP localhost:smtp (LISTEN)
exim4     1504 Debian-exim    4u  IPv6   5271      0t0  TCP localhost:smtp (LISTEN)
pptpd     1536        root    6u  IPv4   5299      0t0  TCP *:1723 (LISTEN)
cupsd     1769        root    6u  IPv6   7160      0t0  TCP localhost:ipp (LISTEN)
cupsd     1769        root    7u  IPv4   7161      0t0  TCP localhost:ipp (LISTEN)
proftpd   1789     proftpd    1u  IPv6   7205      0t0  TCP *:ftp (LISTEN)
apache2   1843        root    4u  IPv6   7248      0t0  TCP *:www (LISTEN)
apache2   1847    www-data    4u  IPv6   7248      0t0  TCP *:www (LISTEN)
apache2   1848    www-data    4u  IPv6   7248      0t0  TCP *:www (LISTEN)
dhclient  2125        root    5w  IPv4   9445      0t0  UDP *:bootpc 
squid     2266       proxy    6u  IPv4   9928      0t0  UDP *:49829 
squid     2266       proxy   14u  IPv4  10020      0t0  TCP *:3128 (LISTEN)
squid     2266       proxy   15u  IPv4  10021      0t0  UDP *:icpv2 
nmbd      2275        root    9u  IPv4   9955      0t0  UDP *:netbios-ns 
nmbd      2275        root   10u  IPv4   9956      0t0  UDP *:netbios-dgm 
nmbd      2275        root   11u  IPv4   9958      0t0  UDP MyComputer.lan:netbios-ns 
nmbd      2275        root   12u  IPv4   9959      0t0  UDP MyComputer.lan:netbios-dgm 
```

Well, it seems pptp is just listening. Is it normal to even be listening? (Paranoia mode on :S)

---

### Post by matt_symes on 2011-04-29
Hi

Do you use VPNs at all ?

Kind regards

---

### Post by GeorgeTI on 2011-04-29
No, not VPN or any other services that open weird ports (at least to my knowledge). The squid service is still weird to be there, I don't remember setting up a proxy... but I don't know if it is supposed to run at all time either :/ The pptpd usually turns up when I use the broadband usb modem, but it should be ONLY then... shouldn't it?

---

### Post by matt_symes on 2011-04-29
Hi

You could just stop them both running as opposed to configuring iptables and see what falls over.

You need to find out why they are running. Check all applications running that may be using them.

Maybe pstree will help ?

Kind regards

---

### Post by GeorgeTI on 2011-04-29
Hmm, if it is to get my hands dirty with iptables, then I guess I'll do it right. I am using vuurmuur to configure the thing, so I guess I will block those ports to all services and see what happens. Sheesh, this thing seems to go deeper than I thought... Anyone knows a tool that shows disk usage for processes? It can't display that in the system monitor, and I keep getting random disk activity. Even without Transmission. Is there a possibility that Ubuntu has something akin to Windows' scheduled tasks, performing checks etc?
And finally, should I ask to move this to the absolute beginner talk?

---

### Post by rookcifer on 2011-04-30
If this is a desktop box and you've got open telnet and pptp ports without knowing why, then you've either installed/ran some service you don't need or you've got bigger, more nefarious, issues.

---

### Post by GeorgeTI on 2011-04-30
Well, it is a laptop, the telnet service is at the router and not my box, but the pptp is, and this is what makes me suspicious. It is only listening, for now anyway, but I do have the fair impression that it shouldn't. It shouldn't even be open in the first place. Am I mistaken?

---

### Post by GeorgeTI on 2011-04-30
It seems the guest session either just enables on its own (yeah right) or I really need to find out what is going on. Anyone of you has heard of a similar occasion? The v beside of Guest Session means the session is enabled, right?
I made some tests when using the Broadband usb modem. Here is what I got from nmap on my real address from ifconfig:

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2011-05-01 00:13 EEST
Interesting ports on XXX.XXX.XXX.XXX:
Not shown: 993 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
53/tcp   open  domain
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
1723/tcp open  pptp
3128/tcp open  squid-http

Nmap done: 1 IP address (1 host up) scanned in 2.38 seconds

I guess pptp is the usual here, but also squid... it is exactly like what I get when I use my home network. I guess these are the.. normal ports? Correct me if I am wrong, but the last two should NOT be there. Also, the whole Guest Session thing creeps me out. And I am fairly sure none has touched my PC. Any ideas on the matter?

---

