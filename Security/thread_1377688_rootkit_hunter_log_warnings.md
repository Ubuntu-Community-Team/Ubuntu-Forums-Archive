---
title: "rootkit hunter log warnings"
date: 2010-01-10
forum: Security
---

### Post by Fika on 2010-01-10
Ok I wish I didn't have to keep posting here about this stuff but I've been using ubuntu for a few days now and the last two days while browsing with firefox I have had tabs opening by themselves which to me would be an indication of malware, along with a couple advertisement popups in the system tray. This has been since the last firefox upgrade so maybe that is the issue, I don't know. I have ran chkrootkit and rootkit hunter but found nothing. Any advice?  Ubuntu 9.10 32 bit

---

### Post by cariboo on 2010-01-10
It could be that your browser was hijacked, the problem has nothing to do with a root kit. Create a new firefox profile and see if the problem goes away.:

```
firefox -Profilemanager
```

---

### Post by BkkBonanza on 2010-01-10
Firefox can open new tabs when a script tries to open a new page. Some nasty sites do this kind of thing. Lots of people seem to like the NoScript add-on for Firefox and I'm pretty sure that will stop this kind of thing and worse. It's not always obvious because some of these scripts embed delay timers so the tab could open some time later.

---

