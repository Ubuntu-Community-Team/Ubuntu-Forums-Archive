---
title: "certain commands not working in apparmor"
date: 2011-06-07
forum: Security
---

### Post by toolmania1 on 2011-06-07
I followed this thread:

[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

When I get to this part:

sudo genprof firefox

it does not work in the terminal.  Is this still supported for Ubuntu 11?

Also, I installed the profiles.  Is something supposed to happen now or do I need to configure them?

[FONT=Times New Roman]sudo apt-get install apparmor-profiles[/FONT]

---

### Post by Dave_L on 2011-06-08
I'm running 10.04.

The firefox profile was already present. It's part of the firefox package.  That's an old thread, so maybe it wasn't the case at that time.

To enable the firefox profile, I had to remove this symlink:
```
sudo rm /etc/apparmor.d/disable/usr.bin.firefox
```

That was the only profile that was disabled in that manner.

Then I (re-)loaded the profile:

```
sudo apparmor_parser -r /etc/apparmor.d/usr.bin.firefox
```

My understanding is that any profile in /etc/apparmor.d/ is automatically loaded when the apparmor service starts.  If you add or change a profile, the change will only take effect when that profile is explicitly reloaded or when apparmor is restarted.

A profile in /etc/apparmor.d/ can be disabled by placing a symbolic link to it in /etc/apparmor.d/disable/.

This shows which profiles are loaded, and whether they're in complain-mode or enforce-mode:

```
sudo service apparmor status
```

---

### Post by Soul-Sing on 2011-06-08
```
sudo aa-enforce firefox
```

(after: sudo apt-get install apparmor-profiles)

---

### Post by toolmania1 on 2011-06-08
That would make sense.  I saw that one of the output lines showed that the firefox profile was disabled.  Thanks!



> **Dave_L said:**
> I'm running 10.04.
 
The firefox profile was already present. It's part of the firefox package.  That's an old thread, so maybe it wasn't the case at that time.
 
To enable the firefox profile, I had to remove this symlink:
```
sudo rm /etc/apparmor.d/disable/usr.bin.firefox
```
 
That was the only profile that was disabled in that manner.
 
Then I (re-)loaded the profile:
 
```
sudo apparmor_parser -r /etc/apparmor.d/usr.bin.firefox
```
 
My understanding is that any profile in /etc/apparmor.d/ is automatically loaded when the apparmor service starts.  If you add or change a profile, the change will only take effect when that profile is explicitly reloaded or when apparmor is restarted.
 
A profile in /etc/apparmor.d/ can be disabled by placing a symbolic link to it in /etc/apparmor.d/disable/.
 
This shows which profiles are loaded, and whether they're in complain-mode or enforce-mode:
 
```
sudo service apparmor status
```

---

### Post by toolmania1 on 2011-06-08
Ok, I'll try it later tonight, thanks!


> **leoquant said:**
> ```
sudo aa-enforce firefox
```
 
(after: sudo apt-get install apparmor-profiles)

---

### Post by toolmania1 on 2011-06-10
I ran the 

sudo service apparmor status

I did not see Firefox anywhere in the list.  However, I did 

sudo aa-enforce Firefox

I was told that Firefox was in enforce mode.  

Here is the output of my status:

>sudo service apparmor status
apparmor module is loaded.
35 profiles are loaded.
13 profiles are in enforce mode.
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-thumbnailer
   /usr/bin/freshclam
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/chromium-browser/chromium-browser//browser_java
   /usr/lib/chromium-browser/chromium-browser//browser_openjdk
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/sbin/cupsd
   /usr/sbin/tcpdump
   /usr/share/gdm/guest-session/Xsession
22 profiles are in complain mode.
   /bin/ping
   /sbin/klogd
   /sbin/syslog-ng
   /sbin/syslogd
   /usr/lib/chromium-browser/chromium-browser
   /usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox
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
3 processes are in enforce mode :
   /sbin/dhclient (1572) 
   /usr/bin/freshclam (1168) 
   /usr/sbin/cupsd (1118) 
2 processes are in complain mode.
   /usr/sbin/avahi-daemon (548) 
   /usr/sbin/avahi-daemon (547) 
0 processes are unconfined but have a profile defined.


> **Dave_L said:**
> I'm running 10.04.

The firefox profile was already present. It's part of the firefox package.  That's an old thread, so maybe it wasn't the case at that time.

To enable the firefox profile, I had to remove this symlink:
```
sudo rm /etc/apparmor.d/disable/usr.bin.firefox
```That was the only profile that was disabled in that manner.

Then I (re-)loaded the profile:

```
sudo apparmor_parser -r /etc/apparmor.d/usr.bin.firefox
```My understanding is that any profile in /etc/apparmor.d/ is automatically loaded when the apparmor service starts.  If you add or change a profile, the change will only take effect when that profile is explicitly reloaded or when apparmor is restarted.

A profile in /etc/apparmor.d/ can be disabled by placing a symbolic link to it in /etc/apparmor.d/disable/.

This shows which profiles are loaded, and whether they're in complain-mode or enforce-mode:

```
sudo service apparmor status
```

---

### Post by toolmania1 on 2011-06-10
Thanks!

> **leoquant said:**
> ```
sudo aa-enforce firefox
```(after: sudo apt-get install apparmor-profiles)

---

### Post by toolmania1 on 2011-12-21
Does this still apply to Ubuntu 11.10?

---

### Post by Soul-Sing on 2011-12-28
don't know had to install apparmor-utils package for some apparmor commands

---

