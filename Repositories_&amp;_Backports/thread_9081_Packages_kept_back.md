---
title: "Packages kept back"
date: 2004-12-23
forum: Repositories &amp; Backports
---

### Post by Rottweiler on 2004-12-23
When doing 'apt-get upgrade' I get ...
   
   [font=Courier New][font=Lucida Console]```

   $ sudo apt-get -V upgrade
   Reading Package Lists... Done
   Building Dependency Tree... Done
   The following packages have been kept back:
      linux-image-2.6-386 (2.6.8.1-13 => 2.6.8.1-14)
      linux-restricted-modules-2.6-386 (2.6.8.1-13 => 2.6.8.1-14)
   0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
   [/font][font=Verdana]
```
   Any idea what to do about this? There are kernel updates I need to install.
 
 This is a new install of Warty. Thanks.[/font]
   [/font]

---

### Post by HiddenWolf on 2004-12-25
[QUOTE=Rottweiler]When doing 'apt-get upgrade' I get ...
   
   [font=Courier New][font=Lucida Console]```

   $ sudo apt-get -V upgrade
   Reading Package Lists... Done
   Building Dependency Tree... Done
   The following packages have been kept back:
      linux-image-2.6-386 (2.6.8.1-13 => 2.6.8.1-14)
      linux-restricted-modules-2.6-386 (2.6.8.1-13 => 2.6.8.1-14)
   0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
   [/font][font=Verdana]
```
   Any idea what to do about this? There are kernel updates I need to install.
 
 This is a new install of Warty. Thanks.[/font]
   [/font][/QUOTE]

Install the new packages manually, they are not updates but new versions.
reboot
Then in grub choose the new kernel, open synaptic, and remove the old kernel.

Do not try to remove the kernel-packages while you are running them, that would be rather painful.

---

### Post by Rottweiler on 2004-12-25
Thanks. Appeared the new kernel was already selected by default in /boot/menu.lst.

---

