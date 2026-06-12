---
title: "Fedora Grub Help?"
date: 2009-09-21
forum: The Cafe
---

### Post by Blacklightbulb on 2009-09-21
I'm trying to install Grub on a /boot partition of fedora. How do I go around this? I've already tried using grub-install but it turns out the menu.lst is not created.

---

### Post by Blacklightbulb on 2009-09-21
Ok so now I used update-grub to get a menu.lst but still it isn't configured correctly. How to I enter the menu option to load Fedora kernel?

---

### Post by calrogman on 2009-09-21
```
sudo update-grub
```


And here's a sample menu entry, configure to your needs.
```
title		Linux
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28 root=/dev/sda1 ro quiet
initrd		/boot/initrd.img-2.6.28
```

---

### Post by Blacklightbulb on 2009-09-21
> **calrogman said:**
> ```
sudo update-grub
```
And here's a sample menu entry, configure to your needs.
```
title        Linux
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28 root=/dev/sda1 ro quiet
initrd        /boot/initrd.img-2.6.28
```

Thanks for your help! I rearranged menu.lst 
But now when I choose the fedora option, the computer hangs at:

```
Starting up....
``` 

Then I press ESC and it displays:

```
Could not start boot splash image: No such file or directory
```

However I have splash.xpm.gz and it's path is listed correctly in menu.lst!

Also, I get the fedora screen (boot splash) while in the Grub menu?! 

Any ideas?

---

### Post by Blacklightbulb on 2009-09-21
Solved thanks!:)

---

