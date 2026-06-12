---
title: "Is aa-genprof broken?"
date: 2015-02-15
forum: Security
---

### Post by cgtdk on 2015-02-15
I've been trying to learn how to make my own AppArmor profiles, but I just can't seem to make it work. I have tried to make profiles for the Deluge and Transmission bittorrent clients using the aa-genprof tool from the apparmor-utils package. Below is an attempt with Transmission.

```
cgt@dpc4:~$ sudo aa-genprof transmission-gtk
[sudo] password for cgt: 
Writing updated profile for /usr/bin/transmission-gtk.
Setting /usr/bin/transmission-gtk to complain mode.

Before you begin, you may wish to check if a
profile already exists for the application you
wish to confine. See the following wiki page for
more information:
http://wiki.apparmor.net/index.php/Profiles

Please start the application to be profiled in
another window and exercise its functionality now.

Once completed, select the "Scan" option below in 
order to scan the system logs for AppArmor events. 

For each AppArmor event, you will be given the 
opportunity to choose whether the access should be 
allowed or denied.

Profiling: /usr/bin/transmission-gtk

[(S)can system log for AppArmor events] / (F)inish
Reading log entries from /var/log/syslog.
Updating AppArmor profiles in /etc/apparmor.d.

Profiling: /usr/bin/transmission-gtk

[(S)can system log for AppArmor events] / (F)inish
Reading log entries from /var/log/syslog.

Profiling: /usr/bin/transmission-gtk

[(S)can system log for AppArmor events] / (F)inish
Setting /usr/bin/transmission-gtk to enforce mode.

Reloaded AppArmor profiles in enforce mode.

Please consider contributing your new profile!
See the following wiki page for more information:
http://wiki.apparmor.net/index.php/Profiles

Finished generating profile for /usr/bin/transmission-gtk.
```

After starting aa-genprof (as shown above) I started Transmission and “exercised” it. I tried pressing S a couple of times in the terminal window in which aa-genprof was running to scan the syslog for AppArmor events, but it didn't seem to do anything. aa-genprof generated the following useless profile:

```
# Last Modified: Sun Feb 15 21:23:43 2015
#include <tunables/global>

/usr/bin/transmission-gtk {
  #include <abstractions/base>

  /usr/bin/transmission-gtk mr,

}
```

I had some torrents running in Transmission and it binds on a port, so I would think that it *would* generate some AppArmor events for me to allow or deny, but apparently not. Am I doing something wrong? I am running Xubuntu 14.10.

---

### Post by fugu2 on 2015-02-20
I was noticing today that it seems to not be working right, and then I saw your post. if you run ```
$ sudo apparmor_status
``` are you seeing a bunch of "//null-xxx" entries?

---

### Post by cgtdk on 2015-02-21
Yes, I did see //null something entries when I tried it with Deluge. I don't recall seeing them when I tried with Transmission. I deleted the profiles, but if it's useful in debugging the problem I'd gladly attempt to recreate it.

---

### Post by fugu2 on 2015-02-24
OK, so after looking into this a little bit more, I found that someone has submitted a bug in launchpad for this problem
[https://bugs.launchpad.net/apparmor/+bug/1399027](https://bugs.launchpad.net/apparmor/+bug/1399027)
```

logparser doesn't understand /var/log/messages format 

Bug Description

log parsing (part of libapparmor, used by aa-logprof and aa-genprof) doesn't understand the format in /var/log/messages, which means it doesn't find any events in it.
IIRC I've seen a similar report for the ubuntu syslog format on IRC.
Example log line from openSUSE:
2014-06-09T20:37:28.975070+02:00 geeko kernel: [21028.143765] type=1400 audit(1402339048.973:1421): apparmor="ALLOWED" operation="open" profile="/home/cb/linuxtag/apparmor/scripts/hello" name="/dev/tty" pid=14335 comm="hello" requested_mask="rw" denied_mask="rw" fsuid=1000 ouid=0
(Workaround: use auditd / audit.log)

```I'm not sure how to implement his suggested workaround but I'm going to try it out.

---

### Post by Stephen_Martin on 2015-07-28
Just for completeness this has now been fixed and a simple apt-get upgrade is all that is needed to fix this in Trusty. I tested today.

---

### Post by cgtdk on 2015-08-10
I am still experiencing the issue on Vivid.

Edit: I just found a on a Debian mailing list (they're having the same issue, apparently). Just install `auditd` (whatever that is) and now aa-genprof prompts me as it should.

[https://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg1340806.html](https://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg1340806.html)

---

