---
title: "when i update...."
date: 2005-04-10
forum: Repositories &amp; Backports
---

### Post by foobar on 2005-04-10
i originallly installed warty 4.10. i have updated many times (sudo apt-get update/upgrade). when i do this, im i updating/upgrading to the news release of ubuntu or just fixing the original version i installed?

in otherwords, if i update/upgrade now, would i have hoary 5.x or would i still have warty 4.10?

*Also, is there a command i can use in the console to find out what version i have and info about it?

thanks.   \\:D/

---

### Post by humanity_to_others on 2005-04-10
```
 i still have warty 4.10?
``` Yes If you want hoary then edit your /etc/apt/sources.list:
add three new adresses:
```
deb http://archive.ubuntu.com/ubuntu/ hoary-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary universe main restricted multiverse
deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted universe multiverse
```

---

### Post by foobar on 2005-04-12
thanks

---

