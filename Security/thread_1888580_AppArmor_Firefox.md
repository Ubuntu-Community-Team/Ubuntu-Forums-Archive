---
title: "AppArmor Firefox"
date: 2011-11-29
forum: Security
---

### Post by Merisi on 2011-11-29
I know that there is an AppArmor profile for Firefox but how do you get it to run?  I've tried numerous times and I can't seem to get the hang of it.  I've tried this [https://help.ubuntu.com/community/AppArmor#How%20can%20I%20enable%20AppArmor%20for%20Firefox?](https://help.ubuntu.com/community/AppArmor#How%20can%20I%20enable%20AppArmor%20for%20Firefox?)  but couldn't make sense of it.  I would really appreciate any help.  Thank you.

---

### Post by Dangertux on 2011-11-29
> **Merisi said:**
> I know that there is an AppArmor profile for Firefox but how do you get it to run?  I've tried numerous times and I can't seem to get the hang of it.  I've tried this [https://help.ubuntu.com/community/AppArmor#How%20can%20I%20enable%20AppArmor%20for%20Firefox?](https://help.ubuntu.com/community/AppArmor#How%20can%20I%20enable%20AppArmor%20for%20Firefox?)  but couldn't make sense of it.  I would really appreciate any help.  Thank you.

That's based on an older version of Ubuntu and quite a bit changed in the last few releases for Apparmor. If you're using Natty as your profile says the following should work for you

You need apparmor-utils first if you don't have them or aren't sure do the followign

```

sudo apt-get update && sudo apt-get install apparmor-utils

```

Then to enforce the profile

```

sudo aa-enforce usr.bin.firefox

```

To make sure it's being enforced run the following

```

sudo aa-status

```

It shoudl be listed under profiles in enforce mode. Hope this helps.

---

### Post by Merisi on 2011-11-29
I'm using Oneric, I can't change my profile as I've not got enough posts.  Will it still work?

Edit:  Just tried it and a lot has happened in terminal but I'm not sure what it will mean.

---

### Post by Dangertux on 2011-11-29
> **Merisi said:**
> I'm using Oneric, I can't change my profile as I've not got enough posts.  Will it still work?

Edit:  Just tried it and a lot has happened in terminal but I'm not sure what it will mean.


It should still work -- please post the out put of

```


sudo aa-status

```

---

### Post by Merisi on 2011-11-29
> **Dangertux said:**
> It should still work -- please post the out put of

```


sudo aa-status

```

apparmor module is loaded.
89 profiles are loaded.
17 profiles are in enforce mode.
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-thumbnailer
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/chromium-browser/chromium-browser//browser_java
   /usr/lib/chromium-browser/chromium-browser//browser_openjdk
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/firefox-8.0/firefox{,*[^s][^h]}
   /usr/lib/firefox-8.0/firefox{,*[^s][^h]}//browser_java
   /usr/lib/firefox-8.0/firefox{,*[^s][^h]}//browser_openjdk
   /usr/lib/lightdm/lightdm-guest-session-wrapper
   /usr/lib/telepathy/mission-control-5
   /usr/lib/telepathy/telepathy-*
   /usr/sbin/cupsd
   /usr/sbin/tcpdump
72 profiles are in complain mode.
   /bin/ping
   /sbin/klogd
   /sbin/syslog-ng
   /sbin/syslogd
   /usr/lib/chromium-browser/chromium-browser
   /usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox
   /usr/lib/chromium-browser/chromium-browser//null-26
   /usr/lib/chromium-browser/chromium-browser//null-27
   /usr/lib/chromium-browser/chromium-browser//null-28
   /usr/lib/chromium-browser/chromium-browser//null-29
   /usr/lib/chromium-browser/chromium-browser//null-2a
   /usr/lib/chromium-browser/chromium-browser//null-2b
   /usr/lib/chromium-browser/chromium-browser//null-2c
   /usr/lib/chromium-browser/chromium-browser//null-2d
   /usr/lib/chromium-browser/chromium-browser//null-2e
   /usr/lib/chromium-browser/chromium-browser//null-2f
   /usr/lib/chromium-browser/chromium-browser//null-30
   /usr/lib/chromium-browser/chromium-browser//null-31
   /usr/lib/chromium-browser/chromium-browser//null-32
   /usr/lib/chromium-browser/chromium-browser//null-33
   /usr/lib/chromium-browser/chromium-browser//null-34
   /usr/lib/chromium-browser/chromium-browser//null-35
   /usr/lib/chromium-browser/chromium-browser//null-36
   /usr/lib/chromium-browser/chromium-browser//null-37
   /usr/lib/chromium-browser/chromium-browser//null-38
   /usr/lib/chromium-browser/chromium-browser//null-39
   /usr/lib/chromium-browser/chromium-browser//null-3a
   /usr/lib/chromium-browser/chromium-browser//null-3b
   /usr/lib/chromium-browser/chromium-browser//null-3c
   /usr/lib/chromium-browser/chromium-browser//null-3d
   /usr/lib/chromium-browser/chromium-browser//null-3e
   /usr/lib/chromium-browser/chromium-browser//null-3f
   /usr/lib/chromium-browser/chromium-browser//null-40
   /usr/lib/chromium-browser/chromium-browser//null-41
   /usr/lib/chromium-browser/chromium-browser//null-42
   /usr/lib/chromium-browser/chromium-browser//null-43
   /usr/lib/chromium-browser/chromium-browser//null-44
   /usr/lib/chromium-browser/chromium-browser//null-45
   /usr/lib/chromium-browser/chromium-browser//null-46
   /usr/lib/chromium-browser/chromium-browser//null-47
   /usr/lib/chromium-browser/chromium-browser//null-48
   /usr/lib/chromium-browser/chromium-browser//null-49
   /usr/lib/chromium-browser/chromium-browser//null-4a
   /usr/lib/chromium-browser/chromium-browser//null-4b
   /usr/lib/chromium-browser/chromium-browser//null-4c
   /usr/lib/chromium-browser/chromium-browser//null-4d
   /usr/lib/chromium-browser/chromium-browser//null-4e
   /usr/lib/chromium-browser/chromium-browser//null-4f
   /usr/lib/chromium-browser/chromium-browser//null-50
   /usr/lib/chromium-browser/chromium-browser//null-51
   /usr/lib/chromium-browser/chromium-browser//null-52
   /usr/lib/chromium-browser/chromium-browser//null-53
   /usr/lib/chromium-browser/chromium-browser//null-54
   /usr/lib/chromium-browser/chromium-browser//null-55
   /usr/lib/chromium-browser/chromium-browser//null-56
   /usr/lib/chromium-browser/chromium-browser//null-57
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
   /usr/sbin/mdnsd
   /usr/sbin/nmbd
   /usr/sbin/nscd
   /usr/sbin/smbd
   /usr/sbin/traceroute
5 processes have profiles defined.
3 processes are in enforce mode.
   /sbin/dhclient (1425) 
   /usr/lib/telepathy/mission-control-5 (1747) 
   /usr/sbin/cupsd (1063) 
2 processes are in complain mode.
   /usr/sbin/avahi-daemon (1128) 
   /usr/sbin/avahi-daemon (1130) 
0 processes are unconfined but have a profile defined.

---

### Post by Dangertux on 2011-11-29
> **Merisi said:**
> apparmor module is loaded.
89 profiles are loaded.
17 profiles are in enforce mode.
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-thumbnailer
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/chromium-browser/chromium-browser//browser_java
   /usr/lib/chromium-browser/chromium-browser//browser_openjdk
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/firefox-8.0/firefox{,*[^s][^h]}
   /usr/lib/firefox-8.0/firefox{,*[^s][^h]}//browser_java
   /usr/lib/firefox-8.0/firefox{,*[^s][^h]}//browser_openjdk
   /usr/lib/lightdm/lightdm-guest-session-wrapper
   /usr/lib/telepathy/mission-control-5
   /usr/lib/telepathy/telepathy-*
   /usr/sbin/cupsd
   /usr/sbin/tcpdump
72 profiles are in complain mode.
   /bin/ping
   /sbin/klogd
   /sbin/syslog-ng
   /sbin/syslogd
   /usr/lib/chromium-browser/chromium-browser
   /usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox
   /usr/lib/chromium-browser/chromium-browser//null-26
   /usr/lib/chromium-browser/chromium-browser//null-27
   /usr/lib/chromium-browser/chromium-browser//null-28
   /usr/lib/chromium-browser/chromium-browser//null-29
   /usr/lib/chromium-browser/chromium-browser//null-2a
   /usr/lib/chromium-browser/chromium-browser//null-2b
   /usr/lib/chromium-browser/chromium-browser//null-2c
   /usr/lib/chromium-browser/chromium-browser//null-2d
   /usr/lib/chromium-browser/chromium-browser//null-2e
   /usr/lib/chromium-browser/chromium-browser//null-2f
   /usr/lib/chromium-browser/chromium-browser//null-30
   /usr/lib/chromium-browser/chromium-browser//null-31
   /usr/lib/chromium-browser/chromium-browser//null-32
   /usr/lib/chromium-browser/chromium-browser//null-33
   /usr/lib/chromium-browser/chromium-browser//null-34
   /usr/lib/chromium-browser/chromium-browser//null-35
   /usr/lib/chromium-browser/chromium-browser//null-36
   /usr/lib/chromium-browser/chromium-browser//null-37
   /usr/lib/chromium-browser/chromium-browser//null-38
   /usr/lib/chromium-browser/chromium-browser//null-39
   /usr/lib/chromium-browser/chromium-browser//null-3a
   /usr/lib/chromium-browser/chromium-browser//null-3b
   /usr/lib/chromium-browser/chromium-browser//null-3c
   /usr/lib/chromium-browser/chromium-browser//null-3d
   /usr/lib/chromium-browser/chromium-browser//null-3e
   /usr/lib/chromium-browser/chromium-browser//null-3f
   /usr/lib/chromium-browser/chromium-browser//null-40
   /usr/lib/chromium-browser/chromium-browser//null-41
   /usr/lib/chromium-browser/chromium-browser//null-42
   /usr/lib/chromium-browser/chromium-browser//null-43
   /usr/lib/chromium-browser/chromium-browser//null-44
   /usr/lib/chromium-browser/chromium-browser//null-45
   /usr/lib/chromium-browser/chromium-browser//null-46
   /usr/lib/chromium-browser/chromium-browser//null-47
   /usr/lib/chromium-browser/chromium-browser//null-48
   /usr/lib/chromium-browser/chromium-browser//null-49
   /usr/lib/chromium-browser/chromium-browser//null-4a
   /usr/lib/chromium-browser/chromium-browser//null-4b
   /usr/lib/chromium-browser/chromium-browser//null-4c
   /usr/lib/chromium-browser/chromium-browser//null-4d
   /usr/lib/chromium-browser/chromium-browser//null-4e
   /usr/lib/chromium-browser/chromium-browser//null-4f
   /usr/lib/chromium-browser/chromium-browser//null-50
   /usr/lib/chromium-browser/chromium-browser//null-51
   /usr/lib/chromium-browser/chromium-browser//null-52
   /usr/lib/chromium-browser/chromium-browser//null-53
   /usr/lib/chromium-browser/chromium-browser//null-54
   /usr/lib/chromium-browser/chromium-browser//null-55
   /usr/lib/chromium-browser/chromium-browser//null-56
   /usr/lib/chromium-browser/chromium-browser//null-57
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
   /usr/sbin/mdnsd
   /usr/sbin/nmbd
   /usr/sbin/nscd
   /usr/sbin/smbd
   /usr/sbin/traceroute
5 processes have profiles defined.
3 processes are in enforce mode.
   /sbin/dhclient (1425) 
   /usr/lib/telepathy/mission-control-5 (1747) 
   /usr/sbin/cupsd (1063) 
2 processes are in complain mode.
   /usr/sbin/avahi-daemon (1128) 
   /usr/sbin/avahi-daemon (1130) 
0 processes are unconfined but have a profile defined.


Yes Firefox is confined

```

/usr/lib/firefox-8.0/firefox{,*[^s][^h]}
   /usr/lib/firefox-8.0/firefox{,*[^s][^h]}//browser_java
   /usr/lib/firefox-8.0/firefox{,*[^s][^h]}//browser_openjdk

```

:-)

---

### Post by Merisi on 2011-11-29
> **Dangertux said:**
> Yes Firefox is confined

```

/usr/lib/firefox-8.0/firefox{,*[^s][^h]}
   /usr/lib/firefox-8.0/firefox{,*[^s][^h]}//browser_java
   /usr/lib/firefox-8.0/firefox{,*[^s][^h]}//browser_openjdk

```:-)

What advantages does it have by being confined?  Also thanks for the help :D

---

### Post by Dangertux on 2011-11-29
> **Merisi said:**
> What advantages does it have by being confined?  Also thanks for the help :D

Apparmor is a type of mandatory access control, which is different then discretionary access controls (file permissions). Basically it controls what objects on the hard drive an application has access to. So if that application is exploited, the attacker in theory would only be able to execute the innate functionality of the application as opposed to doing something more malicious in nature.

Hope that helps.

---

