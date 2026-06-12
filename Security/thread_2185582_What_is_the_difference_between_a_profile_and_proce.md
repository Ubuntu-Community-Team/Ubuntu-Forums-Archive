---
title: "What is the difference between a profile and process being in apparmor enforce mode?"
date: 2013-11-03
forum: Security
---

### Post by arroy_0209 on 2013-11-03
I am using ubuntu12.04. I have tried to keep all apparmor profiles in enforce mode using the command: sudo aa-enforce /etc/apparmor.d/* Now the aa-status command shows that: 
> 
24 profiles are in enforce mode,
/sbin/dhclient
   /usr/bin/evince
.....
/usr/lib/firefox/firefox{,*[^s][^h]}
   /usr/lib/firefox/firefox{,*[^s][^h]}//browser_java
   /usr/lib/firefox/firefox{,*[^s][^h]}//browser_openjdk
   /usr/lib/firefox/firefox{,*[^s][^h]}//sanitized_helper
.....
/usr/share/gdm/guest-session/Xsession
.....
3 processes have profiles defined.
2 processes are in enforce mode.
   /usr/lib/firefox/firefox{,*[^s][^h]} (1183) 
   /usr/sbin/cupsd (434) 
0 processes are in complain mode.
1 processes are unconfined but have a profile defined.
   /usr/sbin/rsyslogd (913) 
 I do not understand what is meant by "/usr/lib/firefox/firefox{,*[^s][^h]}" first counted as profile (in enforce mode) and later as a process (in enforce mode). Why for example, "/usr/bin/evince" is only considered as "profile in enforce mode" and not as a process? Am I supposed to somehow enable the rest of the profiles as processes and keep them in enforce mode (for better security)? Also what does the number (1183) signify? I hope "/usr/sbin/rsyslogd (913)" which is "a processes unconfined, but have a profile defined" will be automatically in enforce mode after next reboot. If not, please explain about this too. Thanks.

---

### Post by Hungry Man on 2013-11-04
When it's talking about the profile it's saying that if the program is run it will run in enforced mode.

If the program isn't running, there is no process. If you were to run evince it would show that a process is being enforced.

If a process starts up before apparmor starts up it will be unconfined.

---

