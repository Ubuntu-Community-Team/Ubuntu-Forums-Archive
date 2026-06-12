---
title: "Can't get Debian Jessie to run on qemu"
date: 2016-06-13
forum: Virtualisation
---

### Post by matthew65536 on 2016-06-13
I have been trying to run Raspbian (a form of Debian for the Raspberry pi, because it is arm based), and i found out there is a way to run it on linux/windows using a program known as Qemu, and i used the following command to run it. "qemu-system-arm -kernel kernel-qemu-4.4.11-jessie -cpu arm1176 -m 256 -M versatilepb -no-reboot -serial stdio -append "root=/dev/sda2 rootfstype=ext4 rw init=/bin/bash" -hda 2016-05-27-raspbian-jessie.img", and when i run it, i got a kernel panic when i tried to start it, i will show that in a screenshot, and since i don't know what it means, i'm hoping someone could help me, any help is appreciated. [https://drive.google.com/open?id=0B8CpTJFFAL4dMks1Vl9VTDRZYzQ](https://drive.google.com/open?id=0B8CpTJFFAL4dMks1Vl9VTDRZYzQ)

---

### Post by deadflowr on 2016-06-13
*Thread moved to **Virtualisation**.*

---

### Post by MAFoElffen on 2016-06-15
You said you used the command
```

"qemu-system-arm -kernel kernel-qemu-4.4.11-jessie -cpu arm1176 -m 256 -M versatilepb -no-reboot -serial stdio -append [COLOR=#ff0000]"[/COLOR]root=/dev/sda2 rootfstype=ext4 rw init=/bin/bash" -hda 2016-05-27-raspbian-jessie.img"

```
I am assuming you made a typo posting that here, as there is are double quotation marks around your append option, that I use single quotation marks there.

What you said there was to use the qemu-system-arm utility to emulate an ARM 1176 processor. Use 256 mb of virtual memory. Set the vm machine name to "verstilepb" ... (<-- You know you can change that to anything right? Not just the machine name in all the canned tutorials.) Set the serial output to console. Use the file named "2016-05-27-raspbian-jessie.img" as a hard disk. Your append line looks good... Which leaves your kernel boot option...

When booting Debian from qemu, I may be wrong, but I successfully use 

```

qemu-system-arm -M debain8-01 -cpu cortex-a8 -m 256 -hda debian8.img -kernel vmlinuz -append 'root=/dev/sda rootwait' -net nic,macaddr=00:16:3e:00:00:03 -net tap

```
But that is on an installed image that I created in qemu... that had a single partition in the image file, using the defualt install, which creates an intrafs file to boot from, which vmlinuz boots. the rootwait option helps with booting the image, for things to be in place, before preceding...

Does that help?

---

