---
title: "&quot;Transaction is destructive&quot; error - Unable to halt or reboot"
date: 2015-04-07
forum: Ubuntu Development Version
---

### Post by enricobe on 2015-04-07
Hello,
today I have had a new problem with Xubuntu 15.04. The O.S. is up-to-date.

I have closed my notebook (no auto-suspension). When I have opened the lid the screen was black, switched off. I was able to start the screen by pressing the power button, which should have put the PC in stand-by, but I was still unable to unlock/shut down/reboot the system. 

I have started a command line interface by pressing CTRL+ALT+F1 and the following has happened:
[ATTACH=CONFIG]261162[/ATTACH]

---

### Post by zika on 2015-04-08
Halt is just for backwards compatibility. You should/might try appropriate option But, I would/do use:
```
sudo shutdown
```

---

### Post by enricobe on 2015-04-08
> **zika said:**
> Halt is just for backwards compatibility. You should/might try appropriate option But, I would/do use:
```
sudo shutdown
```

The same error has occured with "sudo reboot"

---

### Post by zika on 2015-04-08
> **enricobe said:**
> The same error has occured with "sudo reboot"As it should since that is from the same old tree, compatibility only.
```
sudo shutdown --r
```
or
```
sudo shutdown --reboot
```
should be used not to mention systemctl native commands.

---

