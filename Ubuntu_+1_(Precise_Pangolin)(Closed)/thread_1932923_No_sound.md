---
title: "No sound"
date: 2012-02-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by tad1073 on 2012-02-28
```
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
```

Dell Latitude D620 Laptop 

No sound.

---

### Post by matt_symes on 2012-02-28
Hi

Alsa muted ?

```
alsamixer
```

Pulse audio running correctly ?

```
ps aux | grep pulseaudio
```

Anything in syslog ?

```
cat /var/log/syslog
```

Drivers loaded correctly

```
lsmod | grep snd
```

It goes without saying, of course, that Precise is still in development.

Kind regards

---

### Post by tad1073 on 2012-02-28
```
 ps aux | grep pulseaudio
thomas    1743  0.0  0.2  99776  5728 ?        S<l  09:40   0:00 /usr/bin/pulseaudio --start --log-target=syslog
    1748  0.0  0.1  14112  2484 ?        S    09:40   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
    3195  0.0  0.0   4368   836 pts/1    R+   10:06   0:00 grep --color=auto pulseaudio
```

```
cat /var/log/syslog
Feb 28 10:02:11 thomlaptop rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="814" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Feb 28 10:02:22  anacron[972]: Job `cron.daily' terminated
Feb 28 10:02:22  anacron[972]: Normal exit (1 job run)
```

---

### Post by ScislaC on 2012-02-28
I had issues with loss of sound for a while. I tried all kinds of things and then finally after deleting ~/.pulse and after a restart (although logout and log back in was probably all that was necessary), all was working again. Worth a shot IMHO.

---

### Post by tad1073 on 2012-02-28
> **ScislaC said:**
> I had issues with loss of sound for a while. I tried all kinds of things and then finally after deleting ~/.pulse and after a restart (although logout and log back in was probably all that was necessary), all was working again. Worth a shot IMHO.

Thanks, that worked.

---

### Post by jerrylamos on 2012-03-24
> **ScislaC said:**
> I had issues with loss of sound for a while. I tried all kinds of things and then finally after deleting ~/.pulse and after a restart (although logout and log back in was probably all that was necessary), all was working again. Worth a shot IMHO.

Latest CD Build as of yesterday new install.

No sound.

Deleted everything in ~/.pulse

logged out and in

sound working O.K. now..

Thanks, Jerry

---

