---
title: "display wavy flicker after upgrade to 12.04 alpha in dell lattitude"
date: 2012-02-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by aksbuntu on 2012-02-25
I upgraded to 12.04 alpha 1 a couple of weeks back. The only problem I used to have was GPU lockup. The fix was hard reboot. yesterday i upgraded again using "update-manager -d". After upgrade when I restarted the computer the display developed a wavy ripple/flicker. It got fixed by random tapping the laptop. I ran the upgrade manager again and after restart it again started showing wavy ripple/flicker. I could not get rid of that even after good amount of tapping or punching.

---

### Post by effenberg0x0 on 2012-02-25
> **aksbuntu said:**
> I upgraded to 12.04 alpha 1 a couple of weeks back. The only problem I used to have was GPU lockup. The fix was hard reboot. yesterday i upgraded again using "update-manager -d". After upgrade when I restarted the computer the display developed a wavy ripple/flicker. It got fixed by random tapping the laptop. I ran the upgrade manager again and after restart it again started showing wavy ripple/flicker. I could not get rid of that even after good amount of tapping or punching.

Tapping, punching, etc: Are you serious?

---

### Post by aksbuntu on 2012-02-25
well, that was a hyperbole, but tapping seemed to help but where exactly I can not tell...

I thought it could be graphic card problem but I'm sure if I can find that. I  formatted the computer completely then installed 11.10 but it did not help either.

---

### Post by effenberg0x0 on 2012-02-25
Ok, I was confused because considering your GPU is probably welded to your laptop motherboard, there are no moving parts that could benefit from mechanical impact.

Let's try logical/software before physical/hardware procedures.

1) When you boot, do you see anything reasonable, such as the BIOS information? Is the display OK at this point?
2) If you hold the shift key, do you get to the Grub menu?
3) If so, can you select the "Recovery Option"?
4) Letting it boot for a while, you should be presented with a recovery menu. If so select Network and accept when it asks you if its OK to remount '/' as Read/Write.

At this point, you're capable of fixing your PC. You can browse the logs at /var/log/*.log. Have a look at /var/log/Xorg.0.log to detect error messages related to VGA, for example. You can also use apt-get and wget to install, reinstall, download any needed software, thus you can follow any of the thousand of tutorials on how to install proper VGA drivers for your hardware.

By the way, what is the VGA brand/model? You can check that with
```
lspci | grep -i vga
```

Regards,
Effenberg

---

### Post by ventrical on 2012-02-26
> **aksbuntu said:**
> I upgraded to 12.04 alpha 1 a couple of weeks back. The only problem I used to have was GPU lockup. The fix was hard reboot. yesterday i upgraded again using "update-manager -d". After upgrade when I restarted the computer the display developed a wavy ripple/flicker. It got fixed by random tapping the laptop. I ran the upgrade manager again and after restart it again started showing wavy ripple/flicker. I could not get rid of that even after good amount of tapping or punching.


  I was just experimenting with an alpha 2 install and the installer caused just a terrible wavy flicker . It made my monitor look like an old tv set. Obviously  the raster is not auto-set.

---

