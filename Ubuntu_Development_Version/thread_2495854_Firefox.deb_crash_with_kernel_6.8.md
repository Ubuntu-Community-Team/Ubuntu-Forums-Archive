---
title: "Firefox.deb crash with kernel 6.8"
date: 2024-03-05
forum: Ubuntu Development Version
---

### Post by corradoventu on 2024-03-05
Firefox.deb crash with kernel 6.8, Firefox snap is unaffected.
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/2055973](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/2055973)
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/2056123](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/2056123)

---

### Post by ajgreeny on 2024-03-05
How about using the .tar.bz archive and running directly from that?
I've been using Firefox that way since the snap was forced on the whole 'buntu family and it has been just about faultless.

---

### Post by corradoventu on 2024-03-05
I have no problem with FF snap, I sometimes starts firefox nightly just for test.

---

### Post by Claus7 on 2024-03-17
Hello,

> **ajgreeny said:**
> How about using the .tar.bz archive and running directly from that?...

it affects that too.

Regards!

---

### Post by corradoventu on 2024-03-17
Problem is due to bug: [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2046844](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2046844) so probably affect Firefox and many other apps in Ubuntu Noble, where AppArmor restrictions exist but not on different *buntu flavors and versions.

---

### Post by Claus7 on 2024-03-17
Hello,

> **corradoventu said:**
> Problem is due to bug: [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2046844](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2046844) so probably affect Firefox and many other apps in Ubuntu Noble, where AppArmor restrictions exist but not on different *buntu flavors and versions.

I followed your bug report from your OP and marked it too as affecting me. Indeed it seems a more widespread bug.

Regards!

---

### Post by ajgreeny on 2024-03-18
I have also added myself to the bug

I have now tried using the workaround shown in that bug you linked to at post #57 and using that firefox works as normal from the .tar.bz download.
Just out of interest I have also downloaded the firefox-nightly also as the .tar.bz and that works fine without the workaround, simply using the firefox executable without the need for that workaround.

---

### Post by corradoventu on 2024-03-19
I installed apparmor Beta3 from proposed and all firefox are now ok
```
Setting up apparmor (4.0.0-beta3-0ubuntu2) ...
Installing new version of config file /etc/apparmor.d/abstractions/authentication ...
Installing new version of config file /etc/apparmor.d/abstractions/crypto ...
Installing new version of config file /etc/apparmor.d/abstractions/kde-open5 ...
Installing new version of config file /etc/apparmor.d/firefox ...
Reloading AppArmor profiles 
```

---

### Post by ajgreeny on 2024-03-19
Was that firefox installed as a deb, or using the direct download, or perhaps both.

Either way it's good news now we have newer versions either of firefox (the nightly version 125) or the proposed apparmor version, to allow an alternative to the snap.

---

### Post by ajgreeny on 2024-03-20
I can now answer my own question re the .tar.bz of the current version of firefox, 123 using the proposed version of apparmor.
Unfortunately it still crashes the tabs at the moment on my systems even after a reboot.

The firefox-nightly, version 126 still works fine, not needing the workaround noted at [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2046844/comments/57](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2046844/comments/57)

---

### Post by Claus7 on 2024-03-21
Hello,

> **ajgreeny said:**
> I can now answer my own question re the .tar.bz of the current version of firefox, 123 using the proposed version of apparmor.
Unfortunately it still crashes the tabs at the moment on my systems even after a reboot.

...

ditto.

Regards!

---

### Post by ajgreeny on 2024-03-21
> **ajgreeny said:**
> I can now answer my own question re the .tar.bz of the current version of firefox, 123 using the proposed version of apparmor.
Unfortunately it still crashes the tabs at the moment on my systems even after a reboot.

The firefox-nightly, version 126 still works fine, not needing the workaround noted at [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2046844/comments/57](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2046844/comments/57)

And still the same with today's update of the .tar.bz to version 124; tabs still crashing, but presumably when the current 124 moves to the current nightly 126.

---

### Post by Claus7 on 2024-03-22
Hello,

> **ajgreeny said:**
> And still the same with today's update of the .tar.bz to version 124; tabs still crashing, ...

ditto.

Regards!

---

