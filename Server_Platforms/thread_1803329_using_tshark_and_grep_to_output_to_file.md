---
title: "using tshark and |grep to output to file??"
date: 2011-07-13
forum: Server Platforms
---

### Post by SlugSlug on 2011-07-13
Hi am not sure why this does not work..

tshark |grep 'string' 

gives me what I want but

tshark |grep 'string'  >/tmp/outputfile

gives me an empty file

---

### Post by SlugSlug on 2011-07-15
bump

---

### Post by spynappels on 2011-07-15
> **SlugSlug said:**
> Hi am not sure why this does not work..

tshark |grep 'string' 

gives me what I want but

tshark |grep 'string'  >/tmp/outputfile

gives me an empty file

Dunno if it's a typo, but there should be a space between > and /tmp/outfile

Also, are you running tshark as sudo? Can your normal user write to /tmp/outfile? That section will not be done as sudo iirc, so it may work if you output to /home/user/outfile

---

### Post by SlugSlug on 2011-07-15
sorry yer there is a space,

and /tmp is writeable to current user (777)

---

### Post by soyatti on 2013-01-28
this works:

```
tshark -l | stdbuf -oL grep 'string' > dumpfile
```

---

