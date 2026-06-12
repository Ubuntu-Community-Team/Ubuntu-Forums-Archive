---
title: "weird apparmor log for steam app"
date: 2016-11-11
forum: Security
---

### Post by tribble43 on 2016-11-11
I'm writing a profile for a steam app (rpg mo) and I'm encountering a weird log message that's preventing me from running this in enforcing mode.  The name in the log, which normally references a file, has a long hexidecimal string (which is very similar to the profile string, except it's longer):

> audit: type=1400 audit(1478868500.268:26228): apparmor="DENIED" operation="open" profile=2F686F6D652F627269616E2F2E737465616D2F737465616D2F737465616D617070732F636F6D6D6F6E2F525047204D4F2F6E77 name=2F686F6D652F627269616E2F2E737465616D2F737465616D2F737465616D617070732F636F6D6D6F6E2F525047204D4F2F69637564746C2E646174 pid=26773 comm="nw" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000


I was wondering if anyone knows what exactly it's trying to tell me or how I can fix this.  Nothing really shows up if I just set it to complain mode, and even if I just create a global glob it still gives the same error.  One of the last rules that was added was cx permissions in /dev/shm, so idk if that's related at all.

edit:  I (sort of) figured it out on my own.  The hexidecimal string is actually a pathname.  I converted it back to text using vim & xxd.  Most of the stuff appearing like this is stuff related to icu, libjson, and the font cache.

---

