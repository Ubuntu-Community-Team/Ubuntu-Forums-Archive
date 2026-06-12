---
title: "Ubuntu Server with Kde 4.8 rc2: shutdown doesn't work"
date: 2012-01-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sonnet on 2012-01-15
I installed ubuntu server this morning (from image built on 14 of Janurary)
and installed kde-plasma-desktop on top of it.
KDM got automatically installed along with it.
All this has been tried in a vm with virtualbox.
Now my problem is that when I try to shut down the machine it doesn't work: nothing happens. Wheter I try shutdown or restart it's the same.
Is anyone experiencing the same?

---

### Post by BC59 on 2012-01-15
sudo halt is not working?

---

### Post by sonnet on 2012-01-15
I tried 'sudo halt' command in the Konsole and it  doesn't work either:
basically all the processes ends, and get to the line :
[42.896279 ] System halted
but then the screen on the vm remain like that and the machine doesn't shut down.

---

### Post by BC59 on 2012-01-15
Try ```
shutdown -h now
``` as well.

Sometimes the problem is resolved like this:

```
sudo nano /etc/default/grub
```
change > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
to
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
and finally
```
sudo update-grub2
```

---

### Post by sonnet on 2012-01-15
Thanks for your help,

> **BC59 said:**
> Try ```
shutdown -h now
``` as well.
this one works

> **BC59 said:**
> 
Sometimes the problem is resolved like this:

```
sudo nano /etc/default/grub
```
change 
to

and finally
```
sudo update-grub2
```
I tried and rechecked to be sure, but it doesn't have effect.

---

### Post by collisionystm on 2012-01-15
...............................................

the command to shutdown is

sudo shutdown -P 0

---

### Post by sonnet on 2012-01-15
> **collisionystm said:**
> ...............................................

the command to shutdown is

sudo shutdown -P 0

this one works too.

---

