---
title: "Implications of apparmor audit message ."
date: 2013-06-12
forum: Security
---

### Post by arroy_0209 on 2013-06-12
Today I noticed one audit message due to apparmor which I had never seen before. Can anybody please tell me its implications? The message is as follows:
```
kernel: [  269.134918] type=1400 audit(1371022513.925:29): apparmor="DENIED" operation="file_lock" parent=1 profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/home/user/.cache/mozilla/firefox/qpa3oxtz.default/OfflineCache/index.sqlite" pid=2228 comm="firefox" requested_mask="k" denied_mask="k" fsuid=1000 ouid=1000
```

---

### Post by slickymaster on 2013-06-12
There's an already reported Launchpad bug about this: [Bug #1169633]("https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1169633")

---

