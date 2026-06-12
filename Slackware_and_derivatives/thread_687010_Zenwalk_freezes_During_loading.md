---
title: "Zenwalk freezes During loading"
date: 2008-02-03
forum: Slackware and derivatives
---

### Post by davidwrocklage on 2008-02-03
Hello, Brand new to Zenwalk.

My computer is partitioned to allow me to have 3 OS installed on  separate partitions.  First I loaded Zenwalk and loaded the Lilo using the simple interface. Rebooted and played with Zen, great I liked it. The only problem is that I wanted to use GRUB as my bootloader. SO I used my Ubuntu Live cd to reinstall Grub to my MBR, so now Grub was back and I used the following to add Zenwalk to GRUB

# Zenwalk Linux
title Zenwalk Linux
root (hd0,2)
kernel (hd0,2)/boot/vmlinuz root=/dev/hda3 vga=0x31A video=vesafb:mtrr,ywrap splash=silent
initrd (hd0,2)/boot/initrd.splash

So now when I reload Zenwalk is in my Grub and Launches.... Kind of

Zenwalk gets to the splashsceen that say to "press f2 to enter Verbose mode" and hangs

I thought well maybe this has something to do with switching from Lilo to Grub so I re-installed Zenwalk skipping the Lilo step and re-loaded again Zenwalk hangs at the same splashscreen. I really liked Zenwalk as I was playing around today and would like to get it back up and running.

any ideas??

Thanks in advance

---

### Post by bonzodog on 2008-02-05
Your problem is that Zenwalk does not see the root on /dev/**h**da3/, but /dev/**s**da3/.

---

