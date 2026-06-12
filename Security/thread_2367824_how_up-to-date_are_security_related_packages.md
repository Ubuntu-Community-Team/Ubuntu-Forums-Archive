---
title: "how up-to-date are security related packages?"
date: 2017-08-03
forum: Security
---

### Post by thehighhat2 on 2017-08-03
I ran into strange behavior with apparmor where a customized profile failed to protect certain files.

I found this CVE (Spring 2017) that is marked fixed:

  [https://bugs.launchpad.net/apparmor/+bug/1668892](https://bugs.launchpad.net/apparmor/+bug/1668892)

However, the current version in all ubuntu release is still old, and seemingly vulnerable.


After a manual aa-enforce, the profile is working again.


So I guess what I am wondering is, just how current are security updates?


I use LTS branches only because of the notion that the the kernels are fairly hardened, and the stability & security is comprehensive and reliable.

Thoughts?

---

### Post by deadflowr on 2017-08-03
That particular issue was patched way back in March for all supported releases.
See: [https://usn.ubuntu.com/usn/usn-3247-1/]("https://usn.ubuntu.com/usn/usn-3247-1/")

Perhaps the fix isn't working the way it was intended.
Or the intent doesn't cover your particular setup...

---

### Post by thehighhat2 on 2017-08-04
so I am testing this and something is still very wrong with apparmor

steps:
0 ubuntu LTS
1 edit an apparmor profile to, for example, deny read to /some/path in the profile
2 aa-enforce the edited profile
3 confirm it works by opening the application, trying to read from /some/path
   you will see a access denied message
4 now chattr +i, chmod -w  the profile to prevent it from being changed
   confirm the profile still works by doing step 3
5  reboot
6  aa-status, with the application running, to confirm the profile is in enforce mode
7  try step 3 again
   ! note that the profile does not work because /some/path can be accessed

???? how is this possible

8  chattr -i  chmod u+w the profile
9  aa-enforce it again
10  do step 3 again, and note that the exact same profile now works properly   

11 now, reboot, and behold, the profile seems to work

so my question is this, why all of a sudden does a chattr +i chmod -w profile not properly load at boot?

---

### Post by thehighhat2 on 2017-08-04
ok. 

right after after i posted an update to this thread.  the problem went away.  

now all of a sudden, without any package changes, the immutble un-writeable profile suddenly works correctly.

inexplicable.

---

### Post by thehighhat2 on 2017-08-23
No good.

Lots of bad business in the apparmor profiles on ubuntu.  For example, the browser has write permissions to anywhere in $HOME.  See [https://unix.stackexchange.com/questions/308040/apparmor-firefox-profile-allows-read-and-write-to-anywhere-in-home-unless-explic](https://unix.stackexchange.com/questions/308040/apparmor-firefox-profile-allows-read-and-write-to-anywhere-in-home-unless-explic)

Removing firefox.  Switching to ESR.  Replace apparmor profile with locked down version.

---

