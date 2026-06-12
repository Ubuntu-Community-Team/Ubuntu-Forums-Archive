---
title: "Connectivity gone after libnl upgrade"
date: 2016-01-29
forum: Ubuntu/Debian BASED
---

### Post by Correctrix on 2016-01-29
Hi.

I'm running Zorin, an Ubuntu spin-off.  Last night, I did "sudo apt-get update ; sudo apt-get upgrade ; sudo shutdown -h now" and let the computer power off.  This morning, it has no internet.  The system-tray icon that lets me fiddle with my ethernet or wifi connection is absent.

I've run "cat /var/log/dpkg.log | grep 'install\ \|upgrade' " and so I can see that the last packages installed or upgraded last night are as follows:

```
2016-01-30 01:34:57 upgrade libnl-route-3-200:amd64 3.2.21-1 3.2.21-1ubuntu1
2016-01-30 01:34:58 upgrade libnl-genl-3-200:amd64 3.2.21-1 3.2.21-1ubuntu1
2016-01-30 01:34:59 upgrade libnl-3-200:amd64 3.2.21-1 3.2.21-1ubuntu1

```

These libraries seem to be network-related, which confirms that they are likely to be the problem.

How have they broken my internet access and how can I repair it?

---

### Post by Irihapeti on 2016-01-29
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by Correctrix on 2016-01-30
Also discussed here: [http://zoringroup.com/forum/viewtopic.php?f=5&t=11467&p=51264](http://zoringroup.com/forum/viewtopic.php?f=5&t=11467&p=51264)

---

### Post by howefield on 2016-01-30
Possibly more helpfully here : [http://ubuntuforums.org/showthread.php?t=2311705](http://ubuntuforums.org/showthread.php?t=2311705)

---

### Post by Correctrix on 2016-01-30
> **howefield said:**
> Possibly more helpfully here : [http://ubuntuforums.org/showthread.php?t=2311705](http://ubuntuforums.org/showthread.php?t=2311705)
Thanks.

It's a pity this got moved out of Networking into Other OS, when it's a networking issue caused by Ubuntu updates, and not packages from anywhere else.  Anyway, I've marked it as SOLVED.

---

### Post by howefield on 2016-01-30
> **Correctrix said:**
> Thanks.

It's a pity this got moved out of Networking into Other OS, when it's a networking issue caused by Ubuntu updates, and not packages from anywhere else.  Anyway, I've marked it as SOLVED.

Well no, the thread (which to be honest is pretty superfluous, given a cursory search of the forums would have given you the above linked thread) is in the correct place.

Also for information, if you do not know what you are doing it may be best to turn off the proposed repository.

---

