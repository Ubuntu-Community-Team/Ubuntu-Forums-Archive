---
title: "sudo genprof firefox   &lt;-- not working in terminal"
date: 2013-03-28
forum: Security
---

### Post by Traxster on 2013-03-28
Hello to all,


Need help with creating apparmor profile for firefox. Currently working [this]("http://ubuntuforums.org/showthread.php?t=1008906") tutorial. It seems like something may have been missed somewhere. By the way, I am using 12.10.


Any help would be greatly appreciated.


traxster

---

### Post by Soul-Sing on 2013-03-28
The apparmor-utils package contains command line utilities that you can use to change the AppArmor execution mode.

---

### Post by Traxster on 2013-03-28
> **Soul-Sing said:**
> The apparmor-utils package contains command line utilities that you can use to change the AppArmor execution mode.


'command not found' is the response when I enter 'sudo genprof firefox' in terminal. 


[[IMG]http://s3.postimg.org/ww3bquc4v/sudo_genprof_firefox.jpg[/IMG]]("http://postimg.org/image/ww3bquc4v/")

Any help would be greatly appreciated...


traxster

---

### Post by Soul-Sing on 2013-03-28
sudo apt-get install apparmor-utils
 Jamie Strandboge has made some default and restrictive apparmor profiles for Ubuntu and firefox. Why not taken them?

---

### Post by Traxster on 2013-03-28
> **Soul-Sing said:**
> sudo apt-get install apparmor-utils
 Jamie Strandboge has made some default and restrictive apparmor profiles for Ubuntu and firefox. Why not taken them?


I downloaded the apparmor profiles for ubuntu and firefox with the command you suggested, and apparmor is running on my computer, does that mean that all the profiles are running? Please excuse my ignorance. I am totally new at this....


traxster

---

### Post by Soul-Sing on 2013-03-28
sudo /etc/init.d/apparmor status
gives you the enforced/loaded profiles

sudo enforce <name>
etc etc
sudo /etc/init.d/apparmor reload   (and again)
sudo /etc/init.d/apparmor status

on my compu:
 sudo /etc/init.d/apparmor status 
[sudo] password for leor: 
apparmor module is loaded.
49 profiles are loaded.
26 profiles are in enforce mode.
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-previewer//sanitized_helper
   /usr/bin/evince-thumbnailer
   /usr/bin/evince-thumbnailer//sanitized_helper
   /usr/bin/evince//sanitized_helper
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/chromium-browser/chromium-browser//browser_java
   /usr/lib/chromium-browser/chromium-browser//browser_openjdk
   /usr/lib/chromium-browser/chromium-browser//sanitized_helper
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/firefox/firefox{,*[^s][^h]}
   /usr/lib/firefox/firefox{,*[^s][^h]}//browser_java
   /usr/lib/firefox/firefox{,*[^s][^h]}//browser_openjdk
   /usr/lib/firefox/firefox{,*[^s][^h]}//sanitized_helper
   /usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper
   /usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser
   /usr/sbin/cupsd
   /usr/sbin/mdnsd
   /usr/sbin/nmbd
   /usr/sbin/nscd
   /usr/sbin/ntpd
   /usr/sbin/smbd
   /usr/sbin/tcpdump
23 profiles are in complain mode.
   /bin/ping
   /sbin/klogd
   /sbin/syslog-ng
   /sbin/syslogd
   /usr/lib/chromium-browser/chromium-browser
   /usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox
   /usr/lib/chromium-browser/chromium-browser//xdgsettings
   /usr/lib/chromium-browser/chromium-browser//xdgsettings//null-2f
   /usr/lib/chromium-browser/chromium-browser//xdgsettings//null-30
   /usr/lib/chromium-browser/chromium-browser//xdgsettings//null-31
   /usr/lib/chromium-browser/chromium-browser//xdgsettings//null-32
   /usr/lib/dovecot/deliver
   /usr/lib/dovecot/dovecot-auth
   /usr/lib/dovecot/imap
   /usr/lib/dovecot/imap-login
   /usr/lib/dovecot/managesieve-login
   /usr/lib/dovecot/pop3
   /usr/lib/dovecot/pop3-login
   /usr/sbin/avahi-daemon
   /usr/sbin/dnsmasq
   /usr/sbin/dovecot
   /usr/sbin/identd
   /usr/{sbin/traceroute,bin/traceroute.db}
3 processes have profiles defined.
3 processes are in enforce mode.
   /sbin/dhclient (1549) 
   /usr/lib/firefox/firefox{,*[^s][^h]} (4820) 
   /usr/sbin/ntpd (1785) 
0 processes are in complain mode.

---

### Post by Traxster on 2013-03-28
> **Soul-Sing said:**
> sudo /etc/init.d/apparmor status
gives you the enforced/loaded profiles

sudo enforce <name>
etc etc
sudo /etc/init.d/apparmor reload   (and again)
sudo /etc/init.d/apparmor status




In terminal, i enter:   _sudo /etc/init.d/apparmor status_ the result I get is similar to yours (see pic below)

[[IMG]http://s17.postimg.org/xftey7qyj/Screenshot_from_2013_03_28_18_48_22.jpg[/IMG]]("http://postimg.org/image/xftey7qyj/")

then I enter:  _sudo enforce firefox_  i get a message saying command not found ( see pic below)

[[IMG]http://s22.postimg.org/3jz2porlp/Screenshot_from_2013_03_28_19_02_18.jpg[/IMG]]("http://postimg.org/image/3jz2porlp/")

then just for kicks, even though the sudo enforce firefox did not work I typed: _sudo /etc/init.d/apparmor reload_ (please see pic below)
notice the last 2 lines. It states it is skipping 2 profiles and one of them is firefox
[[IMG]http://s18.postimg.org/divt1tz05/Screenshot_from_2013_03_28_18_50_06.jpg[/IMG]]("http://postimg.org/image/divt1tz05/")


your input is greatly appreciated.

Traxster

---

### Post by maglinu on 2013-03-28
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox

---

### Post by Traxster on 2013-03-28
> **maglinu said:**
> sudo aa-enforce /etc/apparmor.d/usr.bin.firefox


that worked!! thank you, and all of those who contributed to this thread.


I will continue learning more about apparmor, and other utilities to help make our computers more secure..

thanks again


Traxster

---

### Post by maglinu on 2013-03-29
> **Traxster said:**
> 


.....I will continue learning more about apparmor.....


Traxster
Pleased to hear you've got it working-

and when you've learned more about apparmor perhaps you can let me know if the default firefox profile usefully confines the flashplayer plugin? I've not been able to suss that out:confused:;)

---

### Post by Traxster on 2013-07-14
> **maglinu said:**
> Pleased to hear you've got it working-

and when you've learned more about apparmor perhaps you can let me know if the default firefox profile usefully confines the flashplayer plugin? I've not been able to suss that out:confused:;)


will do

---

