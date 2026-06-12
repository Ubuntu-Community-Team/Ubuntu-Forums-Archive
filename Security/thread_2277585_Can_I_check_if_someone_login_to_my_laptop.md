---
title: "Can I check if someone login to my laptop?"
date: 2015-05-10
forum: Security
---

### Post by ntun2014 on 2015-05-10
I was at the library, and left my laptop alone for about 5 minutes when I went to the restroom. 
I logout of my account, and left the laptop with a locked screen. 
When I got back home, I noticed a Ethernet Lan connection in my network settings.
I have never used LAN before. The time suggested it was last used when I was in Library. 

Is it possible to check if someone logins to my laptop?

(I was learning web development, and used Filezilla one time though. Not sure if it was related to it.)

---

### Post by Bucky Ball on 2015-05-10
Welcome. When you noticed the ethernet connection was there an ethernet cable plugged in? If not, I'm not sure how you could have had an indication that there was one plugged in (as in an ethernet cable). That would only show when the ethernet cable is plugged in. Generally, wireless and ethernet will not run at the same time, therefore you'd be connected to one or the other, not both.

---

### Post by ntun2014 on 2015-05-10
I am using Kubuntu 15.04. 
When I open Connection editor, it shows as LAN in connection type.
The time of last used was when I was at the library. (I deleted the entry, so not very sure.)
All the other previous networks are shown as Wifi.

Update: Wifi entry at library was also there. Connection type was Wifi. I only connect to Wifi, so no idea about ethernet. I think they will show up in the list though.

---

### Post by cariboo on 2015-05-10
If you know the time when you went to the washroom, you can check /var/log/auth.log to see if someone had logged in.

---

### Post by QIII on 2015-05-10
I'm afraid to say that this is every computer security expert's nightmare.

Leaving a laptop unattended in a public place is just a bad thing.  There is a saying:  "Physical access is root access."  This is how State secrets get revealed and the personal information of thousands of victims gets exposed.

It doesn't matter that you locked your screen.  I could walk over to your laptop, reboot it, go to recovery mode, drop to root, mount your file system read/write, start the desktop, connect to the web, do whatever evil I wanted to do and clean up my tracks so you couldn't find them without very sophisticated knowledge and technology and then just reboot your machine.  All in the space of "five minutes" -- which is a subjective measurement.

When you came back to the machine, you would press a key to unlock your machine, see the login screen and never be the wiser.

If it were me, I would not bother to check to see if someone had intruded.  I would assume someone had.

Just my two cents.

However, the chances of my evil twin just having happened to be in the library at the same time as you are very small.  As cariboo says, check auth.log.  You may get lucky.  What I would look for is this:  A gap in auth.log entries starting a few minutes prior to when you logged out until the time you logged back in.  That would be a dead give-away that someone had compromised your machine.  Unfortunately, that would also mean someone had covered their tracks.

---

### Post by ntun2014 on 2015-05-10
Thanks all. I checked my log. Not sure if there is anything suspicious. 

```
May  9 12:17:10 Kubuntu systemd-logind[709]: Watching system buttons on /dev/input/event3 (Power Button)
May  9 12:17:10 Kubuntu systemd-logind[709]: Watching system buttons on /dev/input/event5 (Video Bus)
May  9 12:17:10 Kubuntu systemd-logind[709]: Watching system buttons on /dev/input/event1 (Power Button)
May  9 12:17:10 Kubuntu systemd-logind[709]: Watching system buttons on /dev/input/event0 (Lid Switch)
May  9 12:17:10 Kubuntu systemd-logind[709]: Watching system buttons on /dev/input/event2 (Sleep Button)
May  9 12:17:16 Kubuntu sddm-helper: pam_unix(sddm-greeter:session): session opened for user sddm by (uid=0)
May  9 12:17:16 Kubuntu systemd-logind[709]: New session 1 of user sddm.
May  9 12:17:16 Kubuntu systemd: pam_unix(systemd-user:session): session opened for user sddm by (uid=0)
May  9 12:17:16 Kubuntu sddm-helper: pam_ck_connector(sddm-greeter:session): nox11 mode, ignoring PAM_TTY :0
May  9 12:17:26 Kubuntu sddm-helper: pam_kwallet(sddm:auth): pam_sm_authenticate
May  9 12:17:26 Kubuntu sddm-helper: pam_kwallet(sddm:setcred): pam_sm_setcred
May  9 12:17:26 Kubuntu sddm-helper: pam_unix(sddm:session): session opened for user joker by (uid=0)
May  9 12:17:26 Kubuntu systemd-logind[709]: New session 2 of user joker.
May  9 12:17:26 Kubuntu systemd: pam_unix(systemd-user:session): session opened for user joker by (uid=0)
May  9 12:17:27 Kubuntu sddm-helper: pam_ck_connector(sddm:session): nox11 mode, ignoring PAM_TTY :0
May  9 12:17:27 Kubuntu sddm-helper: pam_kwallet(sddm:session): pam_sm_open_session
May  9 12:17:27 Kubuntu sddm-helper: pam_kwallet(sddm:session): pam-kwallet: final socket path: /tmp//joker.socket
May  9 12:17:33 Kubuntu polkitd(authority=local): Registered Authentication Agent for unix-session:2 (system bus name :1.33 [/usr/lib/x86_64-linux-gnu/libexec/polkit-kde-authentication-agent-1], object path /org/kde/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
May  9 12:19:30 Kubuntu dbus[740]: [system] Rejected send message, 10 matched rules; type="method_return", sender=":1.55" (uid=0 pid=1571 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.6" (uid=0 pid=733 comm="/usr/sbin/NetworkManager --no-daemon ")
May  9 12:47:48 Kubuntu gnome-keyring-daemon[2349]: couldn't access control socket: /run/user/1000/keyring/control: No such file or directory
May  9 12:48:05 Kubuntu polkitd(authority=local): Operator of unix-session:2 successfully authenticated as unix-user:joker to gain TEMPORARY authorization for action org.kubuntu.qaptworker3.commitchanges for system-bus-name::1.79 [/usr/bin/muon-discover] (owned by unix-user:joker)
May  9 13:17:01 Kubuntu CRON[3619]: pam_unix(cron:session): session opened for user root by (uid=0)
May  9 13:17:01 Kubuntu CRON[3619]: pam_unix(cron:session): session closed for user root
May  9 13:26:40 Kubuntu polkitd(authority=local): Unregistered Authentication Agent for unix-session:2 (system bus name :1.33, object path /org/kde/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
May  9 13:26:47 Kubuntu gnome-keyring-daemon[2349]: g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
May  9 13:26:47 Kubuntu dbus[740]: [system] Rejected send message, 10 matched rules; type="method_return", sender=":1.55" (uid=0 pid=1571 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.6" (uid=0 pid=733 comm="/usr/sbin/NetworkManager --no-daemon ")
May  9 13:26:47 Kubuntu sddm-helper: pam_unix(sddm-greeter:session): session opened for user sddm by (uid=0)
May  9 13:26:47 Kubuntu systemd-logind[709]: New session 4 of user sddm.
May  9 13:26:47 Kubuntu sddm-helper: pam_ck_connector(sddm-greeter:session): nox11 mode, ignoring PAM_TTY :0
May  9 13:26:50 Kubuntu systemd-logind[709]: Removed session 1.
May  9 13:30:09 Kubuntu sddm-helper: pam_kwallet(sddm:auth): pam_sm_authenticate
May  9 13:30:09 Kubuntu sddm-helper: pam_kwallet(sddm:setcred): pam_sm_setcred
May  9 13:30:09 Kubuntu sddm-helper: pam_unix(sddm:session): session opened for user joker by (uid=0)
May  9 13:30:09 Kubuntu systemd-logind[709]: New session 5 of user joker.
May  9 13:30:09 Kubuntu sddm-helper: pam_ck_connector(sddm:session): nox11 mode, ignoring PAM_TTY :0
May  9 13:30:09 Kubuntu sddm-helper: pam_kwallet(sddm:session): pam_sm_open_session
May  9 13:30:09 Kubuntu sddm-helper: pam_kwallet(sddm:session): pam-kwallet: final socket path: /tmp//joker.socket
May  9 13:30:11 Kubuntu dbus[740]: [system] Rejected send message, 10 matched rules; type="method_return", sender=":1.55" (uid=0 pid=1571 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.6" (uid=0 pid=733 comm="/usr/sbin/NetworkManager --no-daemon ")
May  9 13:30:12 Kubuntu polkitd(authority=local): Registered Authentication Agent for unix-session:5 (system bus name :1.150 [/usr/lib/x86_64-linux-gnu/libexec/polkit-kde-authentication-agent-1], object path /org/kde/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
May  9 14:17:02 Kubuntu CRON[5216]: pam_unix(cron:session): session opened for user root by (uid=0)
May  9 14:17:02 Kubuntu CRON[5216]: pam_unix(cron:session): session closed for user root
May  9 15:17:01 Kubuntu CRON[5578]: pam_unix(cron:session): session opened for user root by (uid=0)
May  9 15:17:01 Kubuntu CRON[5578]: pam_unix(cron:session): session closed for user root
May  9 15:24:38 Kubuntu polkitd(authority=local): Unregistered Authentication Agent for unix-session:5 (system bus name :1.150, object path /org/kde/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
May  9 15:24:38 Kubuntu systemd-logind[709]: System is powering down
```

---

### Post by QIII on 2015-05-10
What is the 5 minute period where you were away from the machine?

---

### Post by ntun2014 on 2015-05-10
I guess 
13:26:50 to 13:30:09

---

### Post by Bucky Ball on 2015-05-10
Nothing there in that period:
```

May  9 13:26:50 Kubuntu systemd-logind[709]: Removed session 1.
May  9 13:30:09 Kubuntu sddm-helper: pam_kwallet(sddm:auth): pam_sm_authenticate
```

No activity at all while you were relieving yourself. 

Just curious, though. Someone is logging into your machine as user 'joker'. I'm presuming that is you? I'm also presuming this is you unlocking the screen after your 'comfort break':

```
May  9 13:30:09 Kubuntu systemd-logind[709]: New session 5 of _user joker_.
```

... and this earlier in the day:

```

May  9 12:48:05 Kubuntu polkitd(authority=local): Operator of unix-session:2 _successfully authenticated as unix-user:joker_ to gain TEMPORARY authorization for action org.kubuntu.qaptworker3.commitchanges for system-bus-name::1.79 [/usr/bin/muon-discover] (_owned by unix-user:joker_)
```

---

### Post by ntun2014 on 2015-05-10
Yeah. My username.
Looks like no one logged in. 
Thanks all.

---

### Post by Bucky Ball on 2015-05-10
There's nothing at all in the time period you specify. If you are satisfied, please mark the thread as solved to help others by following the second link in my signature.

Good luck. ;)

---

### Post by NoWayWin8 on 2015-06-18
Advice is really hit and miss around this place.

I'm surprised no one told this guy that the ethernet LAN interface is always created in Network Manager, even if you never use it. All you have to is look at Network Connections anytime after you boot and there "Wired Connection 1" is - it will even list it as last used "1 minute ago" (or however long ago you booted the system).

Still, its better than what microsoft tells people for every single problem ever (run "sfc scannow" which has never helped anyone with any problem and locks up the computer for HOURS while it scans the entire HDD - don't ever let anyone convince you MS is not run by evil sadistic people).

---

### Post by ant2ne on 2015-06-26
> **NoWayWin8 said:**
>  "sfc scannow" which has never helped anyone with any problem I frequently used sfc back when I was a windows admin and it resolved many issues. Particularly after a malware infection or other data/file system corruption. Perhaps it is more worthless on Windows 8 (which thankfully I've never had to work on) but to say it has "never helped" anyone is untrue. It does take some time to run. But so does your anti-virus scanner or check disk etc.

---

### Post by NoWayWin8 on 2015-06-29
> **ant2ne said:**
> I frequently used sfc back when I was a windows admin and it resolved many issues. Particularly after a malware infection or other data/file system corruption. Perhaps it is more worthless on Windows 8 (which thankfully I've never had to work on) but to say it has "never helped" anyone is untrue.
Sorry for the sweeping generalization, t was a little over the top. :)

I meant it for cases where the problem is clearly configuration-related and not indicative of malware.

A typical interaction.

User: "Fresh install, laptop Wifi won't connect! Halp!"
M$:  "Hi, I understand you are having a problem with your Internet. I would like to assist you. Please run sfc scannow"
(two hours later)
User:  "that didn't help." -.-

---

### Post by matt_symes on 2015-06-29
Hi 

If you do need to go to the washroom when in a public place, install and configure motion on your laptop to use your laptop webcam.

Install and configure webcam software on your smart phone (such as tiny cam - no endorsement) and view your webcam from your phone using the wifi. That's one of the things I do if I really need to.

Don't forget tripwire or other HIDS software.

I'll also unmount my encfs file system before i go and do the business.

Just some ideas for you.

EDIT:

...and always use a VPN or SSH connection on an untrusted network.

Kind regards

---

### Post by NoWayWin8 on 2015-06-29
I hope no one is misinterpreting my username. In context, it was (and is) inn support of [this](https://www.fsf.org/windows8) ;)

---

