---
title: "small configure file question"
date: 2009-06-09
forum: Server Platforms
---

### Post by ghen on 2009-06-09
I know that # is used at the beginning of a line for comments, but what does ; do at the beginning of a line?

Like in smb.conf the line:

; guest account = nobody

---

### Post by koenn on 2009-06-09
> **ghen said:**
> I know that # is used at the beginning of a line for comments, but what does ; do at the beginning of a line?

Like in smb.conf the line:

; guest account = nobody


It's also a comment.

It comes from the use of  ; as "End Of Line" so that text following the ; isn't read/executed

---

### Post by amingv on 2009-06-09
This was at the top of smb.conf:

```
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
```

---

