---
title: "[SOLVED] Ubuntu edgy server - apropos why no results?"
date: 2006-12-25
forum: Server Platforms
---

### Post by chrismyers on 2006-12-25
I have a server install of Ubuntu Edgy.

When I do an apropos xxx I always get "nothing appropriate" as a response. No matter what I search.

Does any one know why & how I may fix this?

As an amateur I find this tool useful.

Many thanks.

---

### Post by chrismyers on 2006-12-29
Bump.. :D

---

### Post by chrismyers on 2007-10-15
Over a year later I discovered why....

This happens on new installations where the manual database has not been created yet.

Simply run:

mandb

Now apropos works.

:-)

---

### Post by dewcansam on 2007-10-26
well actually 
```
$ sudo mandb
```

and for RH based linux use:
```
# makewhatis
```

---

