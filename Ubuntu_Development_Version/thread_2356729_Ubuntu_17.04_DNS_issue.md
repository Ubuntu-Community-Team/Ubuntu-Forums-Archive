---
title: "Ubuntu 17.04 DNS issue"
date: 2017-03-26
forum: Ubuntu Development Version
---

### Post by linuxyogi on 2017-03-26
Hi,

I just finished installing 17.04. I am using a ethernet connection, Problem is there is no name lookup by default when  Wired connection is set to DHCP (only). When I add 8.8.8.8 to  Additional DNS Servers name lookup works. Is this a known issue ?

---

### Post by wildmanne39 on 2017-03-26
Looks like you are effected by a bug, it is listed in this thread with a workaround, I suggest you  add your name to the bug report.
[https://ubuntuforums.org/showthread.php?t=2347827](https://ubuntuforums.org/showthread.php?t=2347827)
Post 7 for the workaround.

---

### Post by linuxyogi on 2017-03-26
Since the workaround is quite similar to what I have already done I will keep my existing settings and wait for a fix. 

Thanks for your reply.

---

### Post by dino99 on 2017-03-26
This bug is now solved with the latest network-manager v. 1.4.2-3ubuntu2 in Zesty.

network-manager (1.4.2-3ubuntu2) zesty; urgency=medium

  * Revert 98974a88 and 47c16e59 (network-manager switching from dnsmasq
    to resolved) because of bugs in resolved's resolution of CNAME
    records.  (LP: #1647031)

---

### Post by linuxyogi on 2017-03-26
> **dino99 said:**
> This bug is now solved with the latest network-manager v. 1.4.2-3ubuntu2 in Zesty.

network-manager (1.4.2-3ubuntu2) zesty; urgency=medium

  * Revert 98974a88 and 47c16e59 (network-manager switching from dnsmasq
    to resolved) because of bugs in resolved's resolution of CNAME
    records.  (LP: #1647031)

I tried removing 8.8.8.8 from Additional DNS Servers then Disconnect then reconnect by clicking Wired connection 1.

ping google.com has no reply.


This installation is fully updated.

---

### Post by dino99 on 2017-03-26
did you glanced at journalctl ?

journalctl | grep WARNING
journalctl | grep error

---

### Post by linuxyogi on 2017-03-26
> **dino99 said:**
> did you glanced at journalctl ?

journalctl | grep WARNING
journalctl | grep error

```
$ journalctl | grep WARNING
Mar 26 19:05:22 ubuntu gnome-session[1425]: gnome-session-binary[1425]: WARNING: Could not get session id for session. Check that logind is properly installed and pam_systemd is getting used at login.
Mar 26 19:05:22 ubuntu gnome-session-binary[1425]: WARNING: Could not get session id for session. Check that logind is properly installed and pam_systemd is getting used at login.
Mar 26 19:05:41 ubuntu zeitgeist-daemon[1898]: [13:35:41.437285 WARNING] zeitgeist-daemon.vala:127: Unable to parse version info!
Mar 26 19:05:41 ubuntu zeitgeist-daemon[1898]: [13:35:41.437532 WARNING] zeitgeist-daemon.vala:127: Unable to parse version info!
Mar 26 19:05:41 ubuntu zeitgeist-daemon[1898]: [13:35:41.525295 WARNING] zeitgeist-daemon.vala:127: Unable to parse version info!
Mar 26 19:05:41 ubuntu zeitgeist-daemon[1898]: [13:35:41.758227 WARNING] zeitgeist-daemon.vala:127: Unable to parse version info!
Mar 26 19:05:46 ubuntu zeitgeist-daemon[1898]: [13:35:46.357896 WARNING] zeitgeist-daemon.vala:127: Unable to parse version info!
Mar 26 19:09:53 ubuntu zeitgeist-daemon[1898]: [13:39:53.789497 WARNING] zeitgeist-daemon.vala:127: Unable to parse version info!
Mar 26 19:10:56 ubuntu zeitgeist-daemon[1898]: [13:40:56.156957 WARNING] zeitgeist-daemon.vala:127: Unable to parse version info!


```

```
$ journalctl | grep error
Mar 26 19:05:16 ubuntu kernel: EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Mar 26 19:05:17 ubuntu snapd[730]: 2017/03/26 19:05:17.877422 stateengine.go:98: state ensure error: Post https://search.apps.ubuntu.com/api/v1/snaps/metadata: dial tcp: lookup search.apps.ubuntu.com: Temporary failure in name resolution
Mar 26 19:05:17 ubuntu gpu-manager[758]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
Mar 26 19:05:17 ubuntu /usr/lib/snapd/snapd[730]: stateengine.go:98: state ensure error: Post https://search.apps.ubuntu.com/api/v1/snaps/metadata: dial tcp: lookup search.apps.ubuntu.com: Temporary failure in name resolution
Mar 26 19:05:21 ubuntu session-migration[1333]: Exited with an error
Mar 26 19:05:23 ubuntu gnome-session[1425]: Exited with an error
Mar 26 19:05:25 ubuntu dbus[769]: [system] Rejected send message, 1 matched rules; type="method_call", sender=":1.51" (uid=1000 pid=1357 comm="/usr/lib/x86_64-linux-gnu/indicator-sound/indicato") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.83" (uid=0 pid=1713 comm="/usr/lib/x86_64-linux-gnu/unity-greeter-session-br")
Mar 26 19:05:25 ubuntu dbus[769]: [system] Rejected send message, 1 matched rules; type="method_call", sender=":1.51" (uid=1000 pid=1357 comm="/usr/lib/x86_64-linux-gnu/indicator-sound/indicato") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.83" (uid=0 pid=1713 comm="/usr/lib/x86_64-linux-gnu/unity-greeter-session-br")
Mar 26 19:29:29 ubuntu nm-connection-e[3146]: Cannot save connection due to error: Editor initializing...
Mar 26 19:33:06 ubuntu compiz[1522]: FetchHTTP.prototype.start/request.onerror@chrome://messenger/content/accountcreation/fetchhttp.js:117:36
Mar 26 19:58:21 ubuntu nm-connection-e[5843]: Cannot save connection due to error: Editor initializing...
Mar 26 19:58:25 ubuntu nm-connection-e[5843]: Cannot save connection due to error: Invalid setting IPv4 Settings: IPv4 DNS server "8" invalid
Mar 26 19:58:25 ubuntu nm-connection-e[5843]: Cannot save connection due to error: Invalid setting IPv4 Settings: IPv4 DNS server "8." invalid
Mar 26 19:58:25 ubuntu nm-connection-e[5843]: Cannot save connection due to error: Invalid setting IPv4 Settings: IPv4 DNS server "8.8" invalid
Mar 26 19:58:25 ubuntu nm-connection-e[5843]: Cannot save connection due to error: Invalid setting IPv4 Settings: IPv4 DNS server "8.8." invalid
Mar 26 19:58:26 ubuntu nm-connection-e[5843]: Cannot save connection due to error: Invalid setting IPv4 Settings: IPv4 DNS server "8.8.8" invalid
Mar 26 19:58:26 ubuntu nm-connection-e[5843]: Cannot save connection due to error: Invalid setting IPv4 Settings: IPv4 DNS server "8.8.8." invalid
Mar 26 19:59:44 ubuntu nm-connection-e[6161]: Cannot save connection due to error: Editor initializing...
Mar 26 20:06:37 ubuntu nm-connection-e[7164]: Cannot save connection due to error: Editor initializing...


```

---

### Post by mc4man on 2017-03-26
There are likely any number of bugs concerning networking, internet access, none are from one cause.
In my case there has been no internet access in 17.04 for at least 3 months, no updates to NM or anything else  have solved. 
(-just checked with current Kubuntu beta & Ubuntu daily, still no Internet.

Again _here_ it's 'solved' by using google nameservers, this applies to both ethernet & wireless
Couple of month old bug, got some early attention but then sorta died ( what else is new with Ubuntu..
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1654918](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1654918)

This seems to also be your issue.

---

### Post by dino99 on 2017-03-27
Maybe try the solution given at: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1658921](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1658921)

---

### Post by Ewald_Jurgens on 2017-11-06
I solved it by changing in the following file the FallbackDNS

sudo nano /etc/systemd/resolved.conf

[Resolve]
#DNS=
FallbackDNS=89.101.251.228 89.101.251.229 208.67.222.222 208.67.222.220 8.8.8.8 8.8.4.4
#Domains=
#LLMNR=yes
#DNSSEC=no
#Cache=yes
#DNSStubListener=udp

I removed the # before Fallback DNS and added all the ip-addresses!
I noticed that when changing it in /etc/resolv.conf , it wouldn't save it after a reboot of the system, this method does.
The first 2 ip adresses are my provider's, the 2nd 2 are open DNS and the 3rd 2 are google DNS. You can ofcourse fill in any you want to use.
BTW no source.. I accidently stumbled onto this myself after a few days of trial and error

---

### Post by cariboo on 2017-11-06
Thread closed.

---

