---
title: "How to start everytime in text mode"
date: 2011-09-27
forum: Server Platforms
---

### Post by sapientino on 2011-09-27
Hi all, i'm new here and i'm italian.
I'm making my stupid-home-server on an old Pentium 3 that has got 256 MB of ram.
The grafic interface is too much weighty for him.
How do I run it in text-mode?
:cry:

---

### Post by Off Topic on 2011-09-27
Install Ubuntu Server?

---

### Post by sapientino on 2011-09-27
No, i've got xubuntu

---

### Post by DavidBeijer on 2011-09-27
I think Off Topic meant you should install Ubuntu Server edition. It comes without a GUI, and thus has a way lower load...

---

### Post by haqking on 2011-09-27
You could install server, but if you want to stick with what you have then just boot into CLI and not GDM by editing your grub.

edit the following line to include the text part on the end

```
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
```

to this

```
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash text”
```

and then to update grub

```
sudo update-grub
```

you can restart X or GDM at anytime from the CLI if you wish

---

### Post by zeroseven0183 on 2011-09-27
After doing the above mentioned steps, don't forget to ```
sudo update-grub
```. The changes will take effect the next time you restart your computer.

---

### Post by haqking on 2011-09-27
> **zeroseven0183 said:**
> After doing the above mentioned steps, don't forget to ```
sudo update-grub
```. The changes will take effect the next time you restart your computer.

ahh yeah good point forgot that step.

Edited my post to reflect.

cheers, me need more coffee to function ;-)

---

### Post by DavidBeijer on 2011-09-27
You guys are of course right. Perhaps as a little bit of extra help, the file mentioned in the posts above is located in /etc/default/grub.

Good luck!

---

