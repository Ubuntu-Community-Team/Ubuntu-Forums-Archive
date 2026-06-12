---
title: "Ran ./configure for pidgin2.0.0.7beta"
date: 2007-04-30
forum: The Cafe
---

### Post by jfinkels on 2007-04-30
Here's a snippet of the output from ./configure from the new pidgin2.0.0.7beta source:
```

[...]
checking for Tk linkability... no
checking for snprintf... yes
checking for connect... (cached) yes
checking for me pot o' gold... no
checking for gethostid... yes
checking for lrand48... yes
checking for memcpy... yes
checking for memmove... yes
[...]

```
See anything unusual?

---

### Post by jdhore on 2007-04-30
> **jfinkels said:**
> Here's a snippet of the output from ./configure from the new pidgin2.0.0.7beta source:
```

[...]
checking for Tk linkability... no
checking for snprintf... yes
checking for connect... (cached) yes
checking for me pot o' gold... no
checking for gethostid... yes
checking for lrand48... yes
checking for memcpy... yes
checking for memmove... yes
[...]

```
See anything unusual?

LOL...love it...even in the README for it, they were talking about how to manually install a plugin and the plugin name was "kickass.c"

---

### Post by TravisNewman on 2007-04-30
That's brilliant! Did everything else work out for you?

---

### Post by jfinkels on 2007-04-30
> **panickedthumb said:**
> That's brilliant! Did everything else work out for you?

No actually, checkinstall was :( because there was a file already installed as a part of the binutils package and it couldn't be overwritten. That seems to happen a lot when I do checkinstall, it seems there are quite a few overlapping files :P.

I just found a deb out there on the intertubes.

---

