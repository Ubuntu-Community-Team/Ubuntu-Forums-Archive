---
title: "Is this a credible attack vector?"
date: 2011-01-22
forum: Security
---

### Post by ticket on 2011-01-22
Could Ubuntu be compromised by the following Java attack:

You visit a website that runs a javascript program.
The javascript installs a log-in script (no special permission required),
or modifies an existing one.  
On user log-in, the script opens a port to another web site and sends user key presses to it (so that passwords can be found).
Unless you look at the log in scripts, how would you know you haven't been compromised?


Pardon my ignorance in these matters if the above is nonsense!

---

### Post by endotherm on 2011-01-22
well, javascript cannot usually place files outside the firefox cache, and without running as sudo, no script under a users account could open a port. if an apparmor profile is configured for firefox, the entire thing is out of the question.

the users account can create a "startup application" to run, but without sudo it can;t do anything really harmful to your system, just to the contents of your home directory unless you have signifigantly weakend the system file permissions (which most users would not do).

second, no script can really monitor global user keystrokes. that can;t be done from userspace, so sudo is definitely required to install such a peice of software.

---

### Post by ticket on 2011-01-22
Phew, thanks!

---

### Post by endotherm on 2011-01-22
if you are worried, download and install bleachbit, and run it to clear firefox's cache.
if you are worried about flash, instasll a firefox addon called better privacy to clear flash LSOs at browser shutdown.

---

### Post by nerdy_kid on 2011-01-22
> Phew, thanks!

aren't you glad you aren't running Windows XP?  :lolflag:

---

### Post by The Cog on 2011-01-23
Once a browser exploit is able to write other files in the user's home menu, it would be very easy to hide bad things. One suggestion I saw recently, for instance, was to edit .bashrc and alias sudo to a program that asks your password and forwards it to the baddies. It is a credible attack vector. bodhi.zazen advocates using apparmour to restrict the activities that firefox is allowed to perform, to prevent such things.

---

### Post by ticket on 2011-02-10
> **The Cog said:**
> bodhi.zazen advocates using apparmour to restrict the activities that firefox is allowed to perform, to prevent such things.

Is there a link to bodhi.zazen advice? How do you use apparmour to restrict firefox?  Thanks!


edit:  Hmm, in this

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

it says:

> Since Ubuntu 9.10 (Karmic), AppArmor ships with a profile for Firefox which is disabled by default. 

Is that bad news?

Am reading this & trying to understand :  [http://bodhizazen.net/Tutorials/](http://bodhizazen.net/Tutorials/)

I found this

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.10/usr.bin.firefox](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.10/usr.bin.firefox)

which starts with:

> # Bodhi.Zazen's current firefox 3.6 profile
# Please note this is for :
# Ubuntu 10.10
# Modified from an original profile from Jamie Strandboge <jamie@canonical.com>
# This file restricts access to system files and your home directory.

So this looks like what is needed to make firefox secure.
It also looks like you have to update it every time Ubuntu goes to a new release and when firefox updates. Is this the case?

---

### Post by uRock on 2011-02-10
If you use the Firefox profile in the repos, then you will receive an update for AppArmor  every time Firefox does an update.

You only have to enter one command to enable the Firefox definition, ```
rabbit@ronnie-desktop:~$ sudo enforce firefox
[sudo] password for rabbit: 
Setting /etc/apparmor.d/usr.bin.firefox to enforce mode.
rabbit@ronnie-desktop:~$ 

```And you can see here that the proper version for my Firefox is set to enforce. ```
rabbit@ronnie-desktop:~$ sudo /etc/init.d/apparmor status
apparmor module is loaded.
38 profiles are loaded.
[COLOR=Red]16 profiles are in enforce mode.[/COLOR]
   /sbin/dhclient3
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-thumbnailer
   /usr/bin/freshclam
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/chromium-browser/chromium-browser//browser_java
   /usr/lib/chromium-browser/chromium-browser//browser_openjdk
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
[COLOR=Red]   /usr/lib/firefox-3.6.13/firefox-*bin
   /usr/lib/firefox-3.6.13/firefox-*bin//browser_java
   /usr/lib/firefox-3.6.13/firefox-*bin//browser_openjdk[/COLOR]
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
8 processes have profiles defined.
3 processes are in enforce mode :
   /sbin/dhclient3 (13736) 
   /usr/bin/freshclam (1583) 
   /usr/sbin/cupsd (1282) 
3 processes are in complain mode.
   /usr/sbin/avahi-daemon (1299) 
   /usr/sbin/avahi-daemon (1300) 
   /usr/sbin/nmbd (1658) 
2 processes are unconfined but have a profile defined.
   /usr/sbin/smbd (1276) 
   /usr/sbin/smbd (1211) 
```

---

### Post by uRock on 2011-02-10
Being that I had the browser open while running the commands for the above post, AppArmor did not show Firefox as being an enforced process, but after restarting Firefox and running the status command you can see that Firefox as a process is being enforced. ```
4 processes are in enforce mode :
   /sbin/dhclient3 (13736) 
   /usr/bin/freshclam (1583) 
   [COLOR=Red]/usr/lib/firefox-3.6.13/firefox-*bin (16125)[/COLOR] 
   /usr/sbin/cupsd (1282) 

```

---

### Post by ticket on 2011-02-11
Thank you, uRock!

If I get brave enough to edit the installed firefox profile, will future updates overwrite my edits?

---

### Post by uRock on 2011-02-11
I am not sure. AppArmor is an animal that I haven't tamed yet.

---

