---
title: "software-properties"
date: 2024-02-20
forum: Ubuntu Development Version
---

### Post by Hreinsi on 2024-02-20
Software-proterties not starting. just installed last Daily but no change. Is this common problem ? Software & Updates

---

### Post by Hewjr100 on 2024-02-20
I have the same problem. Cannot open Software and set Ubuntu Pro or and and remove other software.

Henry

---

### Post by deadflowr on 2024-02-20
Reported here:
[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/2053228](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/2053228)

---

### Post by Claus7 on 2024-02-24
Hello,

same bug appears by opening synaptic package manager and picking up repositories, which is responsible for the same configurations mentioned above. 

Regards!

---

### Post by Hewjr100 on 2024-02-24
> **Claus7 said:**
> Hello,

same bug appears by opening synaptic package manager and picking up repositories, which is responsible for the same configurations mentioned above. 

Regards!
  

Good to know, thanks.

Henry

---

### Post by corradoventu on 2024-03-22
Problem solved by the version currently in proposed 
[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/2053228](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/2053228)

---

### Post by Hreinsi on 2024-03-27
werry good seems to be working :)

---

### Post by ajgreeny on 2024-03-27
I have tried to upgrade to the proposed version in my fully upgraded Xubuntu 24.04 but I can not do it as the software-properties-common and python3-software-properties are also requiring changes that are blocked with a comment that I have held-packages that stop it.  I have searched and can find no held packages so your workaround is not a success for me.
Any clues?

I have upgraded apparmor and libapparmor to the proposed version without a problem so I know proposed repos are enabled.

---

### Post by corradoventu on 2024-03-28
On my Ubuntu Noble software-properties-gtk new version is just arrived, no more in proposed.
```
corrado@corrado-n5-nn-0324:~$ apt policy software-properties-gtk
software-properties-gtk:
  Installed: 0.99.44
  Candidate: 0.99.44
  Version table:
 *** 0.99.44 500
        500 http://archive.ubuntu.com/ubuntu noble/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu noble/main i386 Packages
        100 /var/lib/dpkg/status

```

---

### Post by ajgreeny on 2024-03-28
Not on my Xubuntu yesterday so I'll try again today with a normal upgrade rather than the proposed repos which are disabled now.

---

### Post by Frogs Hair on 2024-03-28
Same with Ubuntu Budgie, I had planned to wait for updates and try again.

---

### Post by ajgreeny on 2024-03-28
The proposed version arrived with my Xubuntu today so problem now solved.

---

