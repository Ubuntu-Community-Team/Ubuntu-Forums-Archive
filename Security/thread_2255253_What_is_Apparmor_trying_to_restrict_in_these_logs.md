---
title: "What is Apparmor trying to restrict in these logs?"
date: 2014-12-03
forum: Security
---

### Post by cogset on 2014-12-03
I have Apparmor set to complain mode for Firefox,when looking at the logs I can see a lot of lines like these:
```
type=1400 audit(1417508085.470:43): apparmor="ALLOWED" operation="open" parent=11591 profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/dev/ati/card0" pid=11596 comm="firefox" requested_mask="rw" denied_mask="rw" fsuid=1000 ouid=0
(...)
type=1400 audit(1417545036.453:1464): apparmor="ALLOWED" operation="open" parent=1 profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/sys/devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0/block/sdb/sdb2/uevent" pid=31170 comm="firefox" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
```
my question is,what is Apparmor trying to restrict Firefox from doing?

As I haven't figured out  yet  Apparmor,I take that in complain mode Firefox is asking for some permission on /dev/ati/card0 or my hard drive and Apparmor is denying that,although being in complain mode this just gets logged and Firefox can actually access those files -is that correct?

If so, what may Firefox be exactly doing, according to the log entries above? Accessing the graphic card for some hardware acceleration feature,maybe? 
And what about accessing the sdb2 device, which is my /root partition?

---

### Post by cogset on 2014-12-16
So, any hints? I'm particularly curious about the graphic card : what is Firefox so frequently trying   to do that Apparmor would deny (as far as I understand) if it weren't in complain mode?

---

