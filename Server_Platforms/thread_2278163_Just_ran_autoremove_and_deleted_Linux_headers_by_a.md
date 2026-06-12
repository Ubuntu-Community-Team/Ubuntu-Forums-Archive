---
title: "Just ran autoremove and deleted Linux headers by accident. Not sure what these are?"
date: 2015-05-14
forum: Server Platforms
---

### Post by tbobker on 2015-05-14
So I actually wanted to remove apache from my vps server because I want to replace it with Nginx and ran 

sudo apt-get remove --purge apache2

I then ran dpkg --get-selections | grep -v deinstall and could see some references to apache:

apache2-bin
apache2-data

so then I ran sudo apt-get autoremove and didnt check what I was removing properly and just hit "y"!

Anyway, turns out the following were removed and I dont know if this is going to be a problem:

  linux-headers-3.13.0-49 linux-headers-3.13.0-49-generic
  linux-headers-3.13.0-51 linux-headers-3.13.0-51-generic
  linux-image-3.13.0-49-generic linux-image-3.13.0-51-generic
  linux-image-extra-3.13.0-49-generic linux-image-extra-3.13.0-51-generic

If someone can advise would appreciate it. I am still quite new to server admin.

---

### Post by darkod on 2015-05-14
As long as you have any kernel newer than 3.13.0-51 you should be fine. You can check the kernel loaded with:
```
uname -r
```

Also you can check a full list of installed kernels with:
```
dpkg --list | grep linux-image
```

In case you have removed the running kernel do not reboot until you install a new one.

PS. The latest kernel for 14:04 should be -52. You can always install it with:
```
sudo apt-get install linux-image-3.13.0-52-generic
```

That will install all dependancies like headers, and create entry for this latest kernel in the boot menu. It should boot it by default.

---

### Post by tbobker on 2015-05-14
ok so I entered uname -r says I am running 3.13.0-24-generic but when I list the kernals available it does have the latest kernal   linux-image-generic  3.13.0.52.59

Should I be running the latest version?

---

### Post by darkod on 2015-05-14
If you did not reboot the VPS in a while, the kernels will get installed when you run apt-get dist-upgrade but it will not load (boot) the latest kernel until next reboot. If you have -52 installed it should be safe to reboot. The list of autoremove does not show -52. But you do not have to reboot right now just because of this, it's up to you. The important thing is not to get yourself in a situation where you have no kernel. If you have -52 it looks ok.

Latest kernel is probably recommended to be used but that doesn't mean to reboot the server right away after each update. You can do it when ever you have the chance. It also depends on server usage and possibility to reboot it often or not.

---

### Post by tbobker on 2015-05-14
Darko, thanks. This worked.

---

