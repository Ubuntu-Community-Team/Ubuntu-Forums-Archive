---
title: "Apparmor Errors"
date: 2007-06-23
forum: Server Platforms
---

### Post by jsmidt on 2007-06-23
I installed apparmor following this guide:  [https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

Atfter I am done and rebooted when I do: "sudo apparmor_status"  I get:

```
$ sudo apparmor_status
apparmor module is not loaded.
```

When I do: "sudo /etc/init.d/apparmor start" I get:

```
$ sudo /etc/init.d/apparmor start
FATAL: Error inserting apparmor (/lib/modules/2.6.20-16-generic/apparmor/apparmor.ko): Resource temporarily unavailable
$Loading AppArmor module: Failed.
- could not start AppArmor: Failed.
return: 116: Illegal number: -1
```

When I do: "modprobe apparmor" I get:
```
$ sudo modprobe apparmor
FATAL: Error inserting apparmor (/lib/modules/2.6.20-16-generic/apparmor/apparmor.ko): Resource temporarily unavailable
```


Anybody have any ideas what I may be doing wrong?

---

### Post by sles on 2007-06-29
I have the same problem.
just after compilation and installation it worked, but after reboot I get 

/etc/init.d/apparmor restart
FATAL: Error inserting apparmor (/lib/modules/2.6.20-16-lowlatency/apparmor/apparmor.ko): Resource temporarily unavailable
$Loading AppArmor module: Failed.
- could not start AppArmor: Failed.
return: 116: Illegal number: -1

just because this is first time when I try to use apparmor, could somebody help me to solve this?

---

### Post by ubunuby on 2007-08-12
Edit: I fixed exact problem as listed by first poster by uninstalling all the apparmor packages with synaptic. The packages have to be installed and compiled in a very specific order.

Following [https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

Uninstall all the apparmor packages with synaptic. 

Then, install apparmor-modules-source and module-assistant and **only** those packages.

Then run the compile commands
sudo m-a -v -t prepare
sudo m-a -v -t -f build apparmor-modules
sudo m-a -v -t install apparmor-modules

and lastly install apparmor-profiles, apparmor-utils and apparmor.

after following this package installation order precisely my apparmor runs on boot.

---

### Post by sdfsdf on 2007-10-02
And don't work. When you restart the system you receive the same error message.
The solution is: You must run before "sudo rmmod capability"

Refer to ubuntu bug 122056: [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/122056](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/122056)

Good day.

---

### Post by 1337455 10534 on 2007-10-04
grrr:
same problem!!
FATAL: Error inserting apparmor (/lib/modules/2.6.20-16-generic/apparmor/apparmor.ko): Resource temporarily unavailable
$Loading AppArmor module: Failed.
- could not start AppArmor: Failed.
return: 116: Illegal number: -1
 System startup links for /etc/init.d/apparmor already exist.
 have not rebooted yet tho...

---

