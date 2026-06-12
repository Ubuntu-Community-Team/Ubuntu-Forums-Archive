---
title: "had openssh-server running and port 22 listening too"
date: 2016-06-09
forum: Security
---

### Post by a-you on 2016-06-09
I asked this in general help, but probably this is a better place to ask. And there I was too long winded.

Somehow openssh-server got installed more than a month ago, openssh-client too. Maybe because I was trying lxd and maybe by installing x2go. Anyway openssh-server has been running for more than a month AND I just realized that it was listening on port 22 all that time.

Is the default configuration of openssh-server enough to have protected my laptop in spite of that??

And what can I do to investigate whether I might have been hacked?

I have read all of the auth.log files and there are only entries that to me make sense, like:
```
Received SIGHUP; restarting.
Server listening on 0.0.0.0 port 22.
Server listening on :: port 22.
```
and occasionally:
```
Received signal 15; terminating.
```

Plus some entries early on (I think when I was trying lxd) along the lines of "Connection closed by 127.0.0.1..." and "Invalid user..." etc.

I just have a laptop connected *in Germany* to the internet via DSL, an ISP and an "Alice Modem WLAN 1421" with firmware "1.00.16". Ubuntu Studio 16.04 64 bit.

ANY thoughts, advice, help would be much appreciated.

---

### Post by deadflowr on 2016-06-09
Closed
I'll move your other open thread to this section.

Please do not post duplicate threads on the same subject.
Original thread:
[http://ubuntuforums.org/showthread.php?t=2327230]("http://ubuntuforums.org/showthread.php?t=2327230")

---

### Post by QIII on 2016-06-09
Please do not create duplicate threads in different areas of the forum.  It waters down the community's effort to help.  If you start getting answers here, folks will have no idea what TheFu has already helped you with.

If you would like the other thread moved, please use the "Report Post" button on your initial post in that thread and ask the Staff to move the thread.

Closed.

---

