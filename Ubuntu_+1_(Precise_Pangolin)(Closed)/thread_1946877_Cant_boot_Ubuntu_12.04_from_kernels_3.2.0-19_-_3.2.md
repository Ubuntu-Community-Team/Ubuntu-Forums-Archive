---
title: "Cant boot Ubuntu 12.04 from kernels 3.2.0-19 - 3.2.0-20"
date: 2012-03-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by saksmlz on 2012-03-25
[HTML][/HTML]Everything is working with all kernels prior to version 3.2.0-19. 
Can't boot - means that it freezes and does nothing after pressing "Return" in the grub2 menu. Screen is black, cursor is blinking but nothing more. No HDD activity. I was waiting 10 minutes or more - nothing.

I added 'debug' to boot options, result is on the image. It freezes here:
[[img]http://www.freeimagehosting.net/t/7k37a.jpg[/img]](http://www.freeimagehosting.net/7k37a)

Can anyone help to debug further to figure out how to solve this problem?

---

### Post by kakalos12 on 2012-03-26
The same as me. I had this problem since kernel 3.2.0.18, And I decided to go back to ubuntu 11.10.
If you can boot from kernel 3.2.0.18, then use it instead.

---

### Post by matt_symes on 2012-03-26
Hi

It looks to be like the kernel is crashing while enumerating your PCI buses. The top of the stack track is missing though so i can't be 100% sure.

You could remove all non essential hardware and reboot and see if that fixes it. if it does not crash, you could then start plugging cards back in one after another, rebooting after each, until it crashes. That may help isolate the problem.

You can try the pci= (bios, nobios, biosirq etc) options as well if you want.....

.....however, it sounds like a kernel regression, especially as it was working. I would raise a bug report and use a working kernel.

Kind regards

---

### Post by saksmlz on 2012-03-28
It looks like this issue was fixed with linux-generic 3.2.0.20.22 kernel. Now it boots fine ;)

Thanks to all!

---

