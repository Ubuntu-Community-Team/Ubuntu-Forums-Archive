---
title: "SUDO - how secure is it?"
date: 2009-03-21
forum: Security
---

### Post by AlexenderReez on 2009-03-21
referring to ```
http://blog.banditdefense.com/2009/02/06/sudo-install-my-rootkit/
``` 

[COLOR="YellowGreen"]Before[/COLOR]
[PHP]m0rebel@ubuntu:~$ which sudo
/usr/bin/sudo
m0rebel@ubuntu:~$ ls -l /usr/bin/sudo
-rwsr-xr-x 1 root root 115136 2008-09-01 06:17 /usr/bin/sudo[/PHP]

somebody run script --->
[COLOR="Red"][B]
AFteR[/B][/COLOR]

[PHP]m0rebel@ubuntu:~$ which sudo
/home/m0rebel/.mozilla/.bin/sudo[/PHP]

should it be fixed ?

---

### Post by bodhi.zazen on 2009-03-21
I closed this thread as this type of issue has been discussed many many times.

That blog is noting more then social engineering and the fix is education. There is no linux code to patch. If a user runs an arbitrary script from an untrusted source as root the system can be cracked.

The security issues are :

1. Social engineering. Do not install applications from un trusted sources , problem solved. The entire exploit on that blog requires that you, the user, either install the said script or you yourself modify the path.

Installing or running code from untrusted sources is nothing more then running arbitrary code as root.

2. Escalation of privileges. Now that you have run a bad script , the intruder then becomes root.

This is bait and switch. If you ran arbitrary code, in step 1, you might as well run passwd and set a root password, what about wget to download a rootkit, or curl, or how about if the malignant script just installs a key logger ? You see, an intruder can target almost anything from sudo to su so the only protection is not to run code from untrusted sources.

The real problem in that blog is therefore not sudo, but social engineering. 

The fix is simple.

---

