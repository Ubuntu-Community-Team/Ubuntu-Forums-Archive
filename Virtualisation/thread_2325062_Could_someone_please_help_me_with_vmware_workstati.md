---
title: "Could someone please help me with vmware workstation 12 pro on ubuntu 16.04"
date: 2016-05-18
forum: Virtualisation
---

### Post by Alone143 on 2016-05-18
Is anyone else having a problem starting vmware workstation 12 on ubuntu  16.04 , if so please let me know if you've found a solution . I've  searched all over the web for help to no avail and tried every possible  fix i can think of , any help at all would be greatly appreciated .  Thanks

---

### Post by Alone143 on 2016-05-22
Can anyone lead me in the right direction , Please . I welcome any advice or help at all . Surely there has to be someone out there kind enough to have mercy on me .

---

### Post by MAFoElffen on 2016-05-22
Is it not starting at all or is it trying to start and gets errors? If with errors. please tell ups the errors.

If no errors, then after trying to start it post the results of:
```

sudo dmesg | tail -n 25

```

---

### Post by Alone143 on 2016-05-23
Sorry for the late reply , work had me busy the past few days . It's not starting at all , the welcome box where you put in your email tries to appear . it shows up as a blank dailog not fully loaded and the disappears . And them nothing . Here is the output of that command , 


```
[ 3193.737723] vgaarb: this pci device is not a vga device
[ 3220.160182] vgaarb: this pci device is not a vga device
[ 3457.589389] vgaarb: this pci device is not a vga device
[ 3631.010167] vgaarb: this pci device is not a vga device
[ 3639.383676] vgaarb: this pci device is not a vga device
[ 3835.283600] vgaarb: this pci device is not a vga device
[ 3849.773748] vgaarb: this pci device is not a vga device
[ 4075.250314] vgaarb: this pci device is not a vga device
[ 4130.491394] userif-2: sent link down event.
[ 4130.491401] userif-2: sent link up event.
[ 4327.918966] vgaarb: this pci device is not a vga device
[ 4340.914125] vgaarb: this pci device is not a vga device
[ 4346.172023] vgaarb: this pci device is not a vga device
[ 4447.660110] vgaarb: this pci device is not a vga device
[ 4464.280153] vgaarb: this pci device is not a vga device
[ 4587.510459] vgaarb: this pci device is not a vga device
[ 4648.030415] vgaarb: this pci device is not a vga device
[ 4864.402793] vgaarb: this pci device is not a vga device
[ 5033.565501] vgaarb: this pci device is not a vga device
[ 5144.465796] vgaarb: this pci device is not a vga device
[ 5148.890534] vgaarb: this pci device is not a vga device
[ 5165.841740] vgaarb: this pci device is not a vga device
[ 5208.405770] vgaarb: this pci device is not a vga device
[ 5250.877043] vgaarb: this pci device is not a vga device
[ 5262.314858] vgaarb: this pci device is not a vga device
```

---

### Post by Alone143 on 2016-05-23
Thanks to anyone who would have given me help or advice , my problem is solved . It turns out it was the 4.5.4, 5 kernels causing the problems . I converted back to the 4.5.3 kernel and now it works just fine .

---

### Post by MAFoElffen on 2016-05-25
Glad to hear that you found a solution.

I'm wondering if 4.6.0 has the saem porblem or not... is made the mainline kernel PPA for Yakety on 2016.05.15

If solved, please return to this thread and mark your thread as Solved ([Link]("http://ubuntuforums.org/solved.php?do=marksolved&t=2325062")). That way it helps others to find a solution to their similar issue.

---

