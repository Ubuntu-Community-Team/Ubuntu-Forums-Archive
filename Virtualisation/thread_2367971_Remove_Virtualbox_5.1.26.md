---
title: "Remove Virtualbox 5.1.26"
date: 2017-08-05
forum: Virtualisation
---

### Post by Hewjr100 on 2017-08-05
Can't seem to remove virtualbox.

```
sudo apt remove virtualbox[sudo] password for henry:          
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'virtualbox' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Henry

---

### Post by Bucky Ball on 2017-08-05
```
Package 'virtualbox' is not installed, so not removed
```

Don't understand, sorry. This message is saying Virtualbox is not installed. How did you install it in the first place and what makes you think it's installed now? Have a look in your package manager and see if that sees it as installed.

---

### Post by Hewjr100 on 2017-08-05
I installed it via CLI and set it up with windows 10 iso.  Got an error message about the kernel.  Problem is with EFI/Secure boot.  Went and did a fresh install with Legacy/Bios. Will install again and see what happens.

Henry

---

### Post by deadflowr on 2017-08-05
Is this virtualbox from Oracle or from the Ubuntu repositories?
If from Oracle, then maybe the name is virtualbox-5.1
Perhaps get a clear idea of the version/package name with
```
dpkg -l | grep virtualbox
```
will list all packages currently installed with virtualbox in the name.

---

### Post by Hewjr100 on 2017-08-05
Yes that was it was, Virtualbox 5.1.

Henry

---

