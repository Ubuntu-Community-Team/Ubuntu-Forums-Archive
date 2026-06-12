---
title: "How can I get a list of users running processes?"
date: 2010-02-22
forum: Server Platforms
---

### Post by Underpants on 2010-02-22
I'm looking for a command that will give me a list of users (unique, dont name my user account 60 times) that are running processes on a system... Help?

---

### Post by tgalati4 on 2010-02-22
w

---

### Post by FuturePilot on 2010-02-22
```
w
```

Edit: tgalati4 beat me to it

---

### Post by Baneblade on 2010-02-22
I think that is the best reply I have ever seen.

Its also the shortest, most concise and actually contained the solution to the OP's question... in one character! Haha.

Well done.

---

### Post by Underpants on 2010-02-22
Indeed. Very funny, except it's not what I asked for.


```
ps –fa | awk ‘{print NR “ ” $1}’ | sort -u
```

---

### Post by tgalati4 on 2010-02-22
You can also use the negate switch with ps for some interesting results:

tgalati4@tpad-Gloria7 ~ $ ps -f -N -U tgalati4 -U root
UID        PID  PPID  C STIME TTY          TIME CMD
syslog    2257     1  0 Feb09 ?        00:00:03 /sbin/syslogd -u syslog
klog      2280     1  0 Feb09 ?        00:00:00 /sbin/klogd -P /var/run/klogd/km
108       2301     1  0 Feb09 ?        00:01:52 /bin/dbus-daemon --system
mail      2408     1  0 Feb09 ?        00:00:01 /usr/sbin/nullmailer-send -d
rwhod     2424     1  0 Feb09 ?        00:00:00 /usr/sbin/rwhod -b
rwhod     2430  2424  0 Feb09 ?        00:00:00 /usr/sbin/rwhod -b
111       2514     1  0 Feb09 ?        00:01:07 /usr/sbin/hald
111       2699  2581  0 Feb09 ?        00:00:00 hald-addon-acpi: listening on ac
avahi     2802     1  0 Feb09 ?        00:00:01 avahi-daemon: running [tpad-Glor
avahi     2808  2802  0 Feb09 ?        00:00:00 avahi-daemon: chroot helper
mail      7112  2408  0 20:04 ?        00:00:00 /usr/lib/nullmailer/smtp -

---

