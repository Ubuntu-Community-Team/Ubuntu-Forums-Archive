---
title: "kvm machines won't start after upgrade with security patches today"
date: 2019-11-13
forum: Security
---

### Post by jkleckner on 2019-11-13
A heads up that after an `apt upgrade` today of a 16.04 host, two virtual machines would not boot.

One is a fully-patch updated 16.04 vm and the other is a windows 8.1 vm.

Nothing obvious in the logs.

The host is: model name      : Intel(R) Core(TM)2 Quad CPU    Q9550  @ 2.83GHz

The vms are not overriding the cpu.

The 16.04 vm just sticks on the boot screen.

The windows one goes into a boot repair loop, complaining about:
SYSTEM THREAD EXCEPTION NOT HANDLED

Can't take the time now to debug further but thought I might give people a heads-up.

Here are the changes installed by the update:

```
committing changes in /etc after apt run


Package changes:
-grub-common 2.02~beta2-36ubuntu3.22 amd64
+grub-common 2.02~beta2-36ubuntu3.23 amd64
-grub-pc 2.02~beta2-36ubuntu3.22 amd64
-grub-pc-bin 2.02~beta2-36ubuntu3.22 amd64
-grub2-common 2.02~beta2-36ubuntu3.22 amd64
+grub-pc 2.02~beta2-36ubuntu3.23 amd64
+grub-pc-bin 2.02~beta2-36ubuntu3.23 amd64
+grub2-common 2.02~beta2-36ubuntu3.23 amd64
-intel-microcode 3.20190618.0ubuntu0.16.04.1 amd64
+intel-microcode 3.20191112-0ubuntu0.16.04.2 amd64
-linux-generic-hwe-16.04 4.15.0.66.86 amd64
+linux-generic-hwe-16.04 4.15.0.69.89 amd64
-linux-headers-generic-hwe-16.04 4.15.0.66.86 amd64
+linux-headers-4.15.0-69 4.15.0-69.78~16.04.1 all
+linux-headers-4.15.0-69-generic 4.15.0-69.78~16.04.1 amd64
+linux-headers-generic-hwe-16.04 4.15.0.69.89 amd64
+linux-image-4.15.0-69-generic 4.15.0-69.78~16.04.1 amd64
-linux-image-generic-hwe-16.04 4.15.0.66.86 amd64
+linux-image-generic-hwe-16.04 4.15.0.69.89 amd64
+linux-modules-4.15.0-69-generic 4.15.0-69.78~16.04.1 amd64
+linux-modules-extra-4.15.0-69-generic 4.15.0-69.78~16.04.1 amd64

```

---

### Post by deadflowr on 2019-11-13
There was a regression fix that came thru:
[https://usn.ubuntu.com/4185-3/]("https://usn.ubuntu.com/4185-3/")
Seems related.

---

### Post by TheFu on 2019-11-13
This sort of issue is why I patch on the weekends, not during the week, except for extreme, active, attacks, that impact a specific deployed package.

---

### Post by jkleckner on 2019-11-14
Yes, I can confirm that the update fixed the problem for both vms.

---

### Post by jkleckner on 2019-11-14
Yes, I agree.  Normally, I would only update on Saturday too.

---

