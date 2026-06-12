---
title: "ubuntu lts many vulnerabilities despite long term support"
date: 2016-04-25
forum: Security
---

### Post by J_Me on 2016-04-25
I run updates regularly but it looks like that is pointless.[br]1[/br][https://www.wilderssecurity.com/threads/ubuntu-lts-many-vulnerabilities-despite-long-term-support.385386/](https://www.wilderssecurity.com/threads/ubuntu-lts-many-vulnerabilities-despite-long-term-support.385386/) [br]1[/br]Run this command form a terminal to see which packages are not supported. ```
ubuntu-support-status --show-unsupported
``` Should I be concerned about this. I have a ton of packages(168) from the repo's which turns out are not even supported.  Kubuntu 14.04 lts Thanks

---

### Post by QIII on 2016-04-25
There is already a lively discussion at [http://ubuntuforums.org/showthread.php?t=2321959](http://ubuntuforums.org/showthread.php?t=2321959)

---

### Post by PaulW2U on 2016-04-25
There's already a thread about this - [http://ubuntuforums.org/showthread.php?t=2321959](http://ubuntuforums.org/showthread.php?t=2321959).

Also see [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-April/016477.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-April/016477.html) which advises that ubuntu-support-status should no longer be used.

---

### Post by J_Me on 2016-04-25
Ok thank you.

---

### Post by QDR06VV9 on 2016-04-25
> **PaulW2U said:**
> There's already a thread about this - [http://ubuntuforums.org/showthread.php?t=2321959](http://ubuntuforums.org/showthread.php?t=2321959).

Also see [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-April/016477.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-April/016477.html) which advises that ubuntu-support-status should no longer be used.

Nice find PaulW2U I have been trying to get more info on this since this morning.
> Short answer: don't use ubuntu-support-status, it doesn't work.

Long answer: ubuntu-support-status is a deprecated tool that used to be used
when we had a 3y/5y split on desktop and server packages. It returns the
contents of the "Supported:" tag which hasn't been updated since Ubuntu 10.04
LTS. I've filed a bug to get it removed:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1574670](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1574670)

Marc. 
That explains a lot.

---

