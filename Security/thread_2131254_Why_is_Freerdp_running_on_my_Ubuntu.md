---
title: "Why is Freerdp running on my Ubuntu?"
date: 2013-04-01
forum: Security
---

### Post by g_lev on 2013-04-01
Hello everyone.
(I wasn't really sure where to post this so I hope this is the right place. This is kindda of a Noob question.)
Going over my log files I've noticed that I have the following
```

Apr  1 10:35:19 ubuntu-os kernel: [   45.100482] type=1400 audit(1364801719.204:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=948 comm="apparmor_parser"
Apr  1 10:35:19 ubuntu-os kernel: [   45.100496] type=1400 audit(1364801719.204:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=922 comm="apparmor_parser"
Apr  1 10:35:19 ubuntu-os kernel: [   45.100741] type=1400 audit(1364801719.204:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=948 comm="apparmor_parser"
Apr  1 10:35:19 ubuntu-os kernel: [   45.100859] type=1400 audit(1364801719.204:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=922 comm="apparmor_parser"
Apr  1 10:35:19 ubuntu-os kernel: [   45.105113] type=1400 audit(1364801719.208:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=949 comm="apparmor_parser"
Apr  1 10:35:19 ubuntu-os kernel: [   45.105847] type=1400 audit(1364801719.208:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper//chromium_browser" pid=949 comm="apparmor_parser"
Apr  1 10:35:19 ubuntu-os kernel: [   45.106763] type=1400 audit(1364801719.208:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=946 comm="apparmor_parser"
Apr  1 10:35:19 ubuntu-os kernel: [   45.107021] type=1400 audit(1364801719.208:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=946 comm="apparmor_parser"
Apr  1 10:35:19 ubuntu-os kernel: [   45.110720] type=1400 audit(1364801719.212:13): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=952 comm="apparmor_parser"
Apr  1 10:35:19 ubuntu-os kernel: [   45.111459] type=1400 audit(1364801719.212:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=952 comm="apparmor_parser"

```

What disturbed me was the "lightdm-remote-session-freerdp" since I do not remote control my Ubuntu using [FreeDRP]("http://www.freerdp.com/") so why is it running on my system?

Thank you.

---

### Post by CharlesA on 2013-04-01
Run this please:

```
sudo lsof -i -n -P
```

Judging from the last entry in each line, those are related to apparmour, but the above command will tell for sure.

---

### Post by g_lev on 2013-04-01
Thank you for your help.
Here is the output
```

COMMAND    PID     USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
smbd       854     root   27u  IPv6   9892      0t0  TCP *:445 (LISTEN)
smbd       854     root   28u  IPv6   9893      0t0  TCP *:139 (LISTEN)
smbd       854     root   29u  IPv4   9894      0t0  TCP *:445 (LISTEN)
smbd       854     root   30u  IPv4   9895      0t0  TCP *:139 (LISTEN)
sshd       856     root    3u  IPv4   8563      0t0  TCP *:22 (LISTEN)
sshd       856     root    4u  IPv6   8565      0t0  TCP *:22 (LISTEN)
mysqld    1117    mysql   10u  IPv4  10331      0t0  TCP 127.0.0.1:3306 (LISTEN)
cupsd     1129     root   10u  IPv6  10003      0t0  TCP [::1]:631 (LISTEN)
cupsd     1129     root   11u  IPv4  10004      0t0  TCP 127.0.0.1:631 (LISTEN)
avahi-dae 1151    avahi   13u  IPv4   8811      0t0  UDP *:5353 
avahi-dae 1151    avahi   14u  IPv6   8812      0t0  UDP *:5353 
avahi-dae 1151    avahi   15u  IPv4   8813      0t0  UDP *:38511 
avahi-dae 1151    avahi   16u  IPv6   8814      0t0  UDP *:34439 
dhclient  1320     root    6u  IPv4   8990      0t0  UDP *:68 
dhclient  1320     root   20u  IPv4   8981      0t0  UDP *:7203 
dhclient  1320     root   21u  IPv6   8982      0t0  UDP *:34923 
dnsmasq   1377   nobody    4u  IPv4  10181      0t0  UDP 127.0.1.1:53 
dnsmasq   1377   nobody    5u  IPv4  10182      0t0  TCP 127.0.1.1:53 (LISTEN)
nmbd      1559     root    9u  IPv4   9184      0t0  UDP *:137 
nmbd      1559     root   10u  IPv4   9185      0t0  UDP *:138 
nmbd      1559     root   11u  IPv4   9187      0t0  UDP 192.168.2.102:137 
nmbd      1559     root   12u  IPv4   9188      0t0  UDP 192.168.2.255:137 
nmbd      1559     root   13u  IPv4   9189      0t0  UDP 192.168.2.102:138 
nmbd      1559     root   14u  IPv4   9190      0t0  UDP 192.168.2.255:138 
apache2   1583     root    3u  IPv4  11284      0t0  TCP *:80 (LISTEN)
apache2   1583     root    4u  IPv4  11287      0t0  TCP *:443 (LISTEN)
apache2   1833 www-data    3u  IPv4  11284      0t0  TCP *:80 (LISTEN)
apache2   1833 www-data    4u  IPv4  11287      0t0  TCP *:443 (LISTEN)
apache2   1834 www-data    3u  IPv4  11284      0t0  TCP *:80 (LISTEN)
apache2   1834 www-data    4u  IPv4  11287      0t0  TCP *:443 (LISTEN)
apache2   1835 www-data    3u  IPv4  11284      0t0  TCP *:80 (LISTEN)
apache2   1835 www-data    4u  IPv4  11287      0t0  TCP *:443 (LISTEN)
apache2   1836 www-data    3u  IPv4  11284      0t0  TCP *:80 (LISTEN)
apache2   1836 www-data    4u  IPv4  11287      0t0  TCP *:443 (LISTEN)
apache2   1837 www-data    3u  IPv4  11284      0t0  TCP *:80 (LISTEN)
apache2   1837 www-data    4u  IPv4  11287      0t0  TCP *:443 (LISTEN)
ubuntu-ge 2525      guy   12u  IPv4  20146      0t0  TCP 192.168.2.102:46670->91.189.94.25:80 (CLOSE_WAIT)
unity-sho 2905      guy    9u  IPv4  21498      0t0  TCP 192.168.2.102:38234->91.189.92.9:443 (CLOSE_WAIT)
unity-sho 2905      guy   13u  IPv4  73443      0t0  TCP 192.168.2.102:38287->91.189.92.9:443 (CLOSE_WAIT)
unity-sho 2905      guy   14u  IPv4  73474      0t0  TCP 192.168.2.102:38288->91.189.92.9:443 (CLOSE_WAIT)
unity-sco 3044      guy   18u  IPv4  70946      0t0  TCP 192.168.2.102:46957->173.194.70.101:443 (ESTABLISHED)
gvfsd-htt 3079      guy    7u  IPv4  22867      0t0  TCP 192.168.2.102:49034->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy    9u  IPv4  22508      0t0  TCP 192.168.2.102:49023->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   13u  IPv4  22882      0t0  TCP 192.168.2.102:49036->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   23u  IPv4  74074      0t0  TCP 192.168.2.102:49074->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   24u  IPv4  22511      0t0  TCP 192.168.2.102:49028->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   33u  IPv4  22888      0t0  TCP 192.168.2.102:49038->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   35u  IPv4  22849      0t0  TCP 192.168.2.102:49032->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   36u  IPv4  22515      0t0  TCP 192.168.2.102:49031->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   38u  IPv4  22509      0t0  TCP 192.168.2.102:49025->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   41u  IPv4  22883      0t0  TCP 192.168.2.102:49037->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   42u  IPv4  23624      0t0  TCP 192.168.2.102:49045->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   44u  IPv4  22842      0t0  TCP 192.168.2.102:49026->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   46u  IPv4  22512      0t0  TCP 192.168.2.102:49029->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   47u  IPv4  22858      0t0  TCP 192.168.2.102:49033->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   48u  IPv4  22513      0t0  TCP 192.168.2.102:49030->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   52u  IPv4  23607      0t0  TCP 192.168.2.102:49043->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   53u  IPv4  22843      0t0  TCP 192.168.2.102:49027->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   54u  IPv4  22839      0t0  TCP 192.168.2.102:49024->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   58u  IPv4  22878      0t0  TCP 192.168.2.102:49035->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   59u  IPv4  23611      0t0  TCP 192.168.2.102:49044->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   62u  IPv4  71787      0t0  TCP 192.168.2.102:49070->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   63u  IPv4  71624      0t0  TCP 192.168.2.102:49062->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   64u  IPv4  23581      0t0  TCP 192.168.2.102:49039->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   65u  IPv4  23582      0t0  TCP 192.168.2.102:49040->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   66u  IPv4  23583      0t0  TCP 192.168.2.102:49041->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   67u  IPv4  23584      0t0  TCP 192.168.2.102:49042->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   69u  IPv4  23629      0t0  TCP 192.168.2.102:49046->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   71u  IPv4  23632      0t0  TCP 192.168.2.102:49047->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   74u  IPv4  71626      0t0  TCP 192.168.2.102:49063->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   75u  IPv4  71705      0t0  TCP 192.168.2.102:49064->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   77u  IPv4  71707      0t0  TCP 192.168.2.102:49065->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   79u  IPv4  71709      0t0  TCP 192.168.2.102:49066->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   80u  IPv4  71711      0t0  TCP 192.168.2.102:49067->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   83u  IPv4  74076      0t0  TCP 192.168.2.102:49075->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   85u  IPv4  74072      0t0  TCP 192.168.2.102:49073->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   86u  IPv4  71712      0t0  TCP 192.168.2.102:49068->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   87u  IPv4  71713      0t0  TCP 192.168.2.102:49069->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   95u  IPv4  71597      0t0  TCP 192.168.2.102:49060->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy   99u  IPv4  71598      0t0  TCP 192.168.2.102:49061->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy  106u  IPv4  74091      0t0  TCP 192.168.2.102:49078->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy  113u  IPv4  74083      0t0  TCP 192.168.2.102:49076->199.27.77.192:80 (CLOSE_WAIT)
gvfsd-htt 3079      guy  120u  IPv4  74089      0t0  TCP 192.168.2.102:49077->199.27.77.192:80 (CLOSE_WAIT)
chrome    3567      guy   68u  IPv4  76958      0t0  TCP 192.168.2.102:44460->173.194.70.138:443 (ESTABLISHED)
chrome    3567      guy   97u  IPv4  77557      0t0  TCP 192.168.2.102:39412->173.194.70.120:443 (ESTABLISHED)
chrome    3567      guy   99u  IPv4  77559      0t0  TCP 192.168.2.102:48154->173.194.35.145:443 (ESTABLISHED)
chrome    3567      guy  102u  IPv4  78396      0t0  TCP 192.168.2.102:35676->173.194.44.55:443 (ESTABLISHED)
chrome    3567      guy  139u  IPv4  80068      0t0  TCP 192.168.2.102:46366->54.235.129.211:443 (ESTABLISHED)
chrome    3567      guy  147u  IPv4  79582      0t0  TCP 192.168.2.102:41623->173.194.70.125:5222 (ESTABLISHED)
chrome    3567      guy  150u  IPv4  80575      0t0  TCP 192.168.2.102:55395->38.127.167.7:443 (ESTABLISHED)
chrome    3567      guy  154u  IPv4  80577      0t0  TCP 192.168.2.102:44481->173.194.70.138:443 (ESTABLISHED)

```

---

### Post by CharlesA on 2013-04-01
Yeah, nothing related to remote access (except ssh) is running on your machine.

The entries in the OP is likely just due to apparmour.

---

### Post by g_lev on 2013-04-01
Thank you.
btw. I see
```

gvfsd-htt 3079      guy   46u  IPv4  22512      0t0  TCP 192.168.2.102:49029->199.27.77.192:80 (CLOSE_WAIT)

```
and [199.27.77.192]("http://www.ip-adress.com/whois/199.27.77.192") is belongs to [Skycache Inc]("https://www.google.co.il/search?client=ubuntu&channel=fs&q=Skycache+Inc&ie=utf-8&oe=utf-8&redir_esc=&ei=EphZUZWuCejR4QSYxYCwBA"). any idea why they listen on my samba?

---

### Post by CharlesA on 2013-04-01
That process is the gnome virtual file system, not Samba.

This might help:
[http://askubuntu.com/questions/112318/strange-connections-by-gvfsd-http-spawner](http://askubuntu.com/questions/112318/strange-connections-by-gvfsd-http-spawner)

I don't have that connection listed on my 12.04 box, but according to the page at askubuntu, it might have something to do with rhymnbox or anything internet aware program.

---

### Post by Soul-Sing on 2013-04-01
It is a hosting firm in the USA. But I see some info about realtime internet traffic analyzing also.
So: google, amazon (via the shopping lense) and Fastly.

Apr  1 10:35:19 ubuntu-os kernel: [   45.100741] type=1400 audit(1364801719.204:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=948 comm="apparmor_parser"

I am not sure bout this line. Yes it is "cached" by apparmor. but why?

---

### Post by CharlesA on 2013-04-01
It would probably be a good idea to check the status of apparmour then:
```
sudo apparmor_status
```
[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

---

### Post by g_lev on 2013-04-01
Thanks.
Here is the output:
```

apparmor module is loaded.
23 profiles are loaded.
23 profiles are in enforce mode.
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-previewer//sanitized_helper
   /usr/bin/evince-thumbnailer
   /usr/bin/evince-thumbnailer//sanitized_helper
   /usr/bin/evince//sanitized_helper
   /usr/bin/freshclam
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper
   /usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser
   /usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper
   /usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper//chromium_browser
   /usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper
   /usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser
   /usr/lib/telepathy/mission-control-5
   /usr/lib/telepathy/telepathy-*
   /usr/lib/telepathy/telepathy-*//sanitized_helper
   /usr/sbin/cupsd
   /usr/sbin/mysqld
   /usr/sbin/tcpdump
0 profiles are in complain mode.
4 processes have profiles defined.
4 processes are in enforce mode.
   /sbin/dhclient (1320) 
   /usr/bin/freshclam (1209) 
   /usr/sbin/cupsd (1129) 
   /usr/sbin/mysqld (1117) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.



```

---

### Post by CharlesA on 2013-04-01
I couldn't find much information about that message other than a dmesg from this page:
[http://tratt.net/laurie/research/pubs/files/metatracing_vms/results/0.3/linux_x86_1.html](http://tratt.net/laurie/research/pubs/files/metatracing_vms/results/0.3/linux_x86_1.html)

No mention of what OS they were running though (but I am guessing it is Ubuntu 12.10).

Here is a list of the packages in 12.10:
[http://packages.ubuntu.com/quantal/i386/lightdm-remote-session-freerdp/filelist](http://packages.ubuntu.com/quantal/i386/lightdm-remote-session-freerdp/filelist)

Not sure what to make of it though.

---

### Post by g_lev on 2013-04-02
I will dig into this further and will post if there will be any results.
Thank you very much for your time and effort. You've been a great help.

---

### Post by cariboo on 2013-04-02
I'm a little late to this thread, but if you want to disable remote login as well as other lightdm options, have a look at [this]("http://www.mattfischer.com/blog/?p=343") blog post

---

