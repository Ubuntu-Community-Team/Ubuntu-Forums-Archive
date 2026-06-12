---
title: "AppArmour fails to start"
date: 2010-09-11
forum: Server Platforms
---

### Post by CoolDemon on 2010-09-11
I have a strange problem with ubuntu AppArmor. I have removed (along with dependencies) it before and deleted /etc/apparmor. Now I am trying to install it again. Aptitude could install it successfully. But I am always getting lot of error while starting the service and eventually apparmor fails to start. 

Any help? I am using ubuntu 10.04 server - x86 version.


```
root@ubuntu:~# service apparmor start
 * Starting AppArmor profiles                                                                                                                                AppArmor parser error in /etc/apparmor.d/bin.ping at line 14: Could not open '(null)'
AppArmor parser error in /etc/apparmor.d/sbin.klogd at line 13: Could not open '(null)'
AppArmor parser error in /etc/apparmor.d/sbin.syslogd at line 13: Could not open '(null)'
AppArmor parser error in /etc/apparmor.d/sbin.syslog-ng at line 14: Could not open '(null)'
AppArmor parser error in /etc/apparmor.d/usr.lib.dovecot.deliver at line 4: Could not open '(null)'
AppArmor parser error in /etc/apparmor.d/usr.lib.dovecot.dovecot-auth at line 4: Could not open '(null)'
AppArmor parser error in /etc/apparmor.d/usr.lib.dovecot.imap at line 4: Could not open '(null)'
AppArmor parser error in /etc/apparmor.d/usr.lib.dovecot.imap-login at line 4: Could not open '(null)'
AppArmor parser error in /etc/apparmor.d/usr.lib.dovecot.managesieve-login at line 4: Could not open '(null)'
AppArmor parser error in /etc/apparmor.d/usr.lib.dovecot.pop3 at line 4: Could not open '(null)'
AppArmor parser error in /etc/apparmor.d/usr.lib.dovecot.pop3-login at line 4: Could not open '(null)'
AppArmor parser error in /etc/apparmor.d/usr.sbin.avahi-daemon at line 3: Could not open '(null)'
AppArmor parser error in /etc/apparmor.d/usr.sbin.dnsmasq at line 3: Could not open '(null)'
AppArmor parser error in /etc/apparmor.d/usr.sbin.dovecot at line 4: Could not open '(null)'
AppArmor parser error in /etc/apparmor.d/usr.sbin.identd at line 13: Could not open '(null)'
AppArmor parser error in /etc/apparmor.d/usr.sbin.mdnsd at line 14: Could not open '(null)'
AppArmor parser error in /etc/apparmor.d/usr.sbin.nmbd at line 4: Could not open '(null)'
AppArmor parser error in /etc/apparmor.d/usr.sbin.nscd at line 14: Could not open '(null)'
AppArmor parser error in /etc/apparmor.d/usr.sbin.smbd at line 4: Could not open '(null)'
AppArmor parser error in /etc/apparmor.d/usr.sbin.traceroute at line 14: Could not open '(null)'
                                                                                                                                                      [fail]
root@ubuntu:~# ls /etc/apparmor/
functions  subdomain.conf
root@ubuntu:~# ls /etc/apparmor.d/
abstractions  disable         sbin.syslogd             usr.lib.dovecot.dovecot-auth       usr.lib.dovecot.pop3        usr.sbin.dovecot  usr.sbin.nscd
apache2.d     force-complain  sbin.syslog-ng           usr.lib.dovecot.imap               usr.lib.dovecot.pop3-login  usr.sbin.identd   usr.sbin.smbd
bin.ping      program-chunks  tunables                 usr.lib.dovecot.imap-login         usr.sbin.avahi-daemon       usr.sbin.mdnsd    usr.sbin.traceroute
cache         sbin.klogd      usr.lib.dovecot.deliver  usr.lib.dovecot.managesieve-login  usr.sbin.dnsmasq            usr.sbin.nmbd
root@ubuntu:~# ls /etc/apparmor.d/abstractions
root@ubuntu:~# ls /etc/apparmor.d/cache
bin.ping-027PG1        usr.lib.dovecot.deliver-3sTeqZ       usr.lib.dovecot.managesieve-login-174FSX  usr.sbin.dnsmasq-1pmkAV  usr.sbin.nmbd-1iJzv5
bin.ping-GsLL5f        usr.lib.dovecot.deliver-eTz5Tg       usr.lib.dovecot.managesieve-login-76pbc2  usr.sbin.dnsmasq-4mSnht  usr.sbin.nmbd-5YbEEq
bin.ping-GtM83Y        usr.lib.dovecot.deliver-GVu4eb       usr.lib.dovecot.managesieve-login-AwMRDq  usr.sbin.dnsmasq-DmgrGt  usr.sbin.nmbd-dxwHgf
bin.ping-hIXU9q        usr.lib.dovecot.deliver-I3FWLr       usr.lib.dovecot.managesieve-login-DhCgSs  usr.sbin.dnsmasq-f2ncm5  usr.sbin.nmbd-jlwwqY
bin.ping-Ki2PEp        usr.lib.dovecot.deliver-lmV9wq       usr.lib.dovecot.managesieve-login-ja5xdq  usr.sbin.dnsmasq-mDeh2e  usr.sbin.nmbd-OpGGZt
bin.ping-ozwJPW        usr.lib.dovecot.deliver-oGi3X1       usr.lib.dovecot.managesieve-login-jcxdah  usr.sbin.dnsmasq-pe9UHb  usr.sbin.nmbd-Q30OAr
bin.ping-SEpJkd        usr.lib.dovecot.deliver-QpZwYW       usr.lib.dovecot.managesieve-login-Kwjwtb  usr.sbin.dnsmasq-VrJh4X  usr.sbin.nmbd-UvbvSe
bin.ping-x0XS2p        usr.lib.dovecot.deliver-vmbgDs       usr.lib.dovecot.managesieve-login-mO6tRU  usr.sbin.dnsmasq-XdEXpq  usr.sbin.nmbd-ZfzpPV
sbin.klogd-6jVFzZ      usr.lib.dovecot.dovecot-auth-1J11Kr  usr.lib.dovecot.pop3-1Vodaq               usr.sbin.dovecot-1ej7Ze  usr.sbin.nscd-0FDlpr
sbin.klogd-6LjB9c      usr.lib.dovecot.dovecot-auth-6iMqAs  usr.lib.dovecot.pop3-8untiV               usr.sbin.dovecot-4qBSmq  usr.sbin.nscd-bouTVt
sbin.klogd-enCTZp      usr.lib.dovecot.dovecot-auth-7IRQ2a  usr.lib.dovecot.pop3-e6L5z2               usr.sbin.dovecot-gnuUwV  usr.sbin.nscd-EIIdFe
sbin.klogd-jVNCdq      usr.lib.dovecot.dovecot-auth-er9Jl2  usr.lib.dovecot.pop3-kUpINX               usr.sbin.dovecot-JmWx5b  usr.sbin.nscd-j8QMOf
sbin.klogd-Mit7Bg      usr.lib.dovecot.dovecot-auth-GZomVW  usr.lib.dovecot.pop3-login-0roEeV         usr.sbin.dovecot-s7WPEt  usr.sbin.nscd-JqH0eY
sbin.klogd-oytqF1      usr.lib.dovecot.dovecot-auth-I3PuAX  usr.lib.dovecot.pop3-login-7nWC5p         usr.sbin.dovecot-Sq3V94  usr.sbin.nscd-mMmuBq
sbin.klogd-q5luEW      usr.lib.dovecot.dovecot-auth-tHZcSg  usr.lib.dovecot.pop3-login-GAdYKX         usr.sbin.dovecot-xop60X  usr.sbin.nscd-sM3Ks5
sbin.klogd-Uop9yr      usr.lib.dovecot.dovecot-auth-Z68Kmq  usr.lib.dovecot.pop3-login-jaiq3g         usr.sbin.dovecot-XvHFBt  usr.sbin.nscd-XgC5LV
sbin.syslogd-0rh7yg    usr.lib.dovecot.imap-507VYs          usr.lib.dovecot.pop3-login-TJDydt         usr.sbin.identd-7T3tYX   usr.sbin.smbd-BbV7Be
sbin.syslogd-7tQCaq    usr.lib.dovecot.imap-8h5Fiq          usr.lib.dovecot.pop3-login-umTKmt         usr.sbin.identd-Aixdwf   usr.sbin.smbd-DjTbWr
sbin.syslogd-Bd8t6c    usr.lib.dovecot.imap-A1Jvi2          usr.lib.dovecot.pop3-login-VPtUNb         usr.sbin.identd-jQeOjq   usr.sbin.smbd-hx8JQ5
sbin.syslogd-epyACW    usr.lib.dovecot.imap-login-6X4hVs    usr.lib.dovecot.pop3-login-Vr5Lw2         usr.sbin.identd-MHfD74   usr.sbin.smbd-nOkLSt
sbin.syslogd-orq7ur    usr.lib.dovecot.imap-login-8MYWg2    usr.lib.dovecot.pop3-ONzdqt               usr.sbin.identd-NZNE2b   usr.sbin.smbd-PtT30q
sbin.syslogd-WzAdXp    usr.lib.dovecot.imap-login-b1HIwb    usr.lib.dovecot.pop3-soAgRb               usr.sbin.identd-UTfwDt   usr.sbin.smbd-pWcqwY
sbin.syslogd-XL3H41    usr.lib.dovecot.imap-login-dhWMPq    usr.lib.dovecot.pop3-u13lCq               usr.sbin.identd-XJqCtV   usr.sbin.smbd-QKiL50
sbin.syslogd-yIhvwZ    usr.lib.dovecot.imap-login-Lm8HlX    usr.lib.dovecot.pop3-uUEY6g               usr.sbin.identd-XXUUrt   usr.sbin.smbd-W0ESJf
sbin.syslog-ng-01ekUr  usr.lib.dovecot.imap-login-Pz6VZr    usr.sbin.avahi-daemon-3aSBu2              usr.sbin.mdnsd-35iSHq    usr.sbin.traceroute-aoAeaf
sbin.syslog-ng-7zJEGs  usr.lib.dovecot.imap-login-YmItch    usr.sbin.avahi-daemon-ffesbV              usr.sbin.mdnsd-ABwovY    usr.sbin.traceroute-CNOetY
sbin.syslog-ng-jdv3hb  usr.lib.dovecot.imap-login-YMoOUU    usr.sbin.avahi-daemon-jjTf6e              usr.sbin.mdnsd-FVFPjf    usr.sbin.traceroute-cXHPM5
sbin.syslog-ng-ocJ8ng  usr.lib.dovecot.imap-OG02XU          usr.sbin.avahi-daemon-lAbEKb              usr.sbin.mdnsd-kq2R0V    usr.sbin.traceroute-j0bp20
sbin.syslog-ng-P7uyZp  usr.lib.dovecot.imap-v3ZpPg          usr.sbin.avahi-daemon-mbxrtq              usr.sbin.mdnsd-Nu1nAt    usr.sbin.traceroute-jzBfAf
sbin.syslog-ng-rpnR01  usr.lib.dovecot.imap-vBUXas          usr.sbin.avahi-daemon-Se3fGX              usr.sbin.mdnsd-sNi3Dr    usr.sbin.traceroute-nbN3hu
sbin.syslog-ng-vszPsZ  usr.lib.dovecot.imap-WYDLzb          usr.sbin.avahi-daemon-t2IYit              usr.sbin.mdnsd-u6yRy5    usr.sbin.traceroute-q8MPUr
sbin.syslog-ng-y8Br2W  usr.lib.dovecot.imap-zx43nX          usr.sbin.avahi-daemon-xhPC8s              usr.sbin.mdnsd-v4k8Zb    usr.sbin.traceroute-RPTUXq
root@ubuntu:~#

```

---

### Post by hhlp on 2010-09-11
you can have information here :

[https://wiki.ubuntu.com/DebuggingApparmor]("https://wiki.ubuntu.com/DebuggingApparmor")

i add to the /etc/apparmor directory you can backup your apparmor directory and change with this ....

---

### Post by CoolDemon on 2010-09-11
Thanks a lot for your help. Unfortunately it did not work out well. 

You have sent me compressed _/etc/apparmor**.d**/_, perhaps you can also send me _/etc/apparmor_. I can try with that also.

My original idea was re-installing the package should solve this - unless there is some bug in the package.

Any other solution will also be appreciated. 
Thanks in advance.

---

### Post by CoolDemon on 2010-09-12
*Bringing to the top.*
This is still unsolved. Please help.

---

