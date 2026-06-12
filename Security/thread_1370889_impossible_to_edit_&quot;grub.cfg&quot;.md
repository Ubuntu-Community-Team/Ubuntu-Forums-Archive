---
title: "impossible to edit &quot;grub.cfg&quot;"
date: 2010-01-02
forum: Security
---

### Post by alex69 on 2010-01-02
Hi,
in order to customize my grub menu entries, I've just tried to edit the file grub.cfg (the old "menu.lst" in ubuntu 9.04) from the path /boot/grub/
My problem is that it seems impossible for me to modify that file, also with root permissions??!!

on the terminal I did:

```
sudo gedit /boot/grub/grub.cfg
```

Gedit opens but, when I tried to save the file, after  the changes (overwriting the old version)an error message appears telling that is a read-only file and cannot be modified.

there's anyone could help me to understand why I'm not able to change that config file?

thanks in advance
Alex

---

### Post by cariboo on 2010-01-02
Have a look [here]("https://wiki.ubuntu.com/Grub2"), you may have seen the notice at the top of grub.cfg, you aren't supposed to edit it directly. If you do want to edit grub.cfg ignoring the warning, make a backup copy first. All you have to do is change the permissions of grub.cfg to edit it. Once you are finished with the edit make sure to change the permission back to what they were originally.

The original permissions are 444, set them to 777 and you should have zero problems editing the file.

Remeber: **[COLOR="Red"]You should heed the warning at the top of the file[/COLOR]**

---

### Post by alex69 on 2010-01-06
It works, thank you very much :guitar:

Alex

---

