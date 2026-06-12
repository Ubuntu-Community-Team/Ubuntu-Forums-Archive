---
title: "Apparmor newb - thunderbird profile - Target the binary or the script?"
date: 2014-06-19
forum: Security
---

### Post by jcllings on 2014-06-19
So I'm setting up an apparmor profile for TBird. Question: Do I profile the script or the binary?:

```
user@machine:/usr/lib/thunderbird$ ls -l `which thunderbird`
lrwxrwxrwx 1 root root 33 Apr 28 14:02 /usr/bin/thunderbird -> ../lib/thunderbird/thunderbird.sh
user@machine:/usr/lib/thunderbird$  ls /usr/lib/thunderbird/thunderbird.sh
```

So as noted above what starts FF is this script:
/usr/lib/thunderbird/thunderbird.sh

Should I profile that or profile the binary which is called by the script. That is:
/usr/lib/thunderbird/thunderbird

Lets verify that's a binary:
```

user@machine:/usr/lib/thunderbird$ file /usr/lib/thunderbird/thunderbird
/usr/lib/thunderbird/thunderbird: ELF 64-bit LSB  executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=279f44b3bdcf15aed6e38ff723ca8b7bf68ff428, stripped 
```

So yes, it's a binary executable linked to some shared libs, exactly as expected. Perms?

```
user@machine:/usr/lib/thunderbird$ ls -l /usr/lib/thunderbird/thunderbird
-rwxr-xr-x 1 root root 93008 Apr 28 14:15 /usr/lib/thunderbird/thunderbird
```

Yep, world executable.

Guys, herein lies my problem. If I do the script, then I don't have the binary covered. If I do the binary then will it be covered if it is started by a script?

---

