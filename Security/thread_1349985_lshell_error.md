---
title: "lshell error"
date: 2009-12-08
forum: Security
---

### Post by grandsatrap on 2009-12-08
I just installed LSHELL and now am getting this error when I login or type "lshell". All I did is install it and make a few minor changes to the lshell.conf file. I set the lshell.conf file back to the original and still get this error. I think that it would be ludicrous for me to go through and debug all 1000 lines of lshell.py

Has anyone else come across this problem?
 
```

Traceback (most recent call last):
  File "/usr/bin/lshell", line 24, in <module>
    import lshell
  File "/usr/lib/python2.5/site-packages/lshell.py", line 106
    + hisory_file
    ^
IndentationError: unexpected indent

```

---

### Post by grandsatrap on 2009-12-09
Apparently is fixed in the latest version (which I thought I had, but didn't).

---

