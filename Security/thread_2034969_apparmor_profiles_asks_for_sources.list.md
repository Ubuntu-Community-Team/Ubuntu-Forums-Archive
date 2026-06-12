---
title: "apparmor profiles asks for sources.list"
date: 2012-07-29
forum: Security
---

### Post by Laiquendi on 2012-07-29
Hey, I'm using apparmor-utils like aa-logprof, but not without reading ofc ;)
Both firefox and thunderbird at some point asks to access (read) sources.list.
Why? Should I allow it?

I've been searching for answer but found nothing...

---

### Post by Hungry Man on 2012-07-29
It's probably for application compatibility/ interactions. Or it could be to verify the PPA is correct.

I'd just deny it and if anything breaks you'll know why.

---

### Post by Laiquendi on 2012-07-29
xD
Worse if thunderbird will slowly decay without updates or something ^^

Someone maybe knows what is the true meaning of this correlation? :P

edit:
If it's not clear - it asks me for read permission only so I assume it's quite safe to allow it?

---

### Post by Hungry Man on 2012-07-30
Reads are still unsafe. Knowing what's in that file could provide an attacker with very valuable information about your system.

We can assume that it needs it for *something* but whether you can live without that or not is the question. That's why I suggest using a Deny rule until you run into an issue.

---

### Post by Laiquendi on 2012-07-30
Ok I'll try. If I'll come out with something I'll post it ;)
Thanks for the replies.
Further suggestions are welcome! :)

---

