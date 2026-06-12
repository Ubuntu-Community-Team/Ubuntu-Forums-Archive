---
title: "Monit problem with disk space checking"
date: 2008-09-18
forum: Server Platforms
---

### Post by sunpower on 2008-09-18
Hi folks,

The usual Monit directive (from the manual) for checking disk usage goes like this:

```
 check device rootfs with path /dev/hda1
  if space usage > 80% 5 times within 15 cycles 
     then alert 
```

I cannot get space checking to work.
This is what I am trying to do:

```
# Monitor root(/) filesystem
check device /dev/mapper/kiusa-root with path /
        if space usage > 80 % then alert
```


The manual of Monit fails to tell how the device name has to be used. I have LVM in place (with Hardy Heron). I really do not know what to have on the "check device rootfs with path /dev/hda1" line.

Typing "df" gives the following:

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/kiusa-root
                      78023688  40585488  34292472  55% /
varrun                  517328        56    517272   1% /var/run
varlock                 517328         0    517328   0% /var/lock
udev                    517328        60    517268   1% /dev
devshm                  517328         0    517328   0% /dev/shm
/dev/sda1               241116     25222    203446  12% /boot
```

On the other hand, sudo lvdisplay gives

```
  --- Logical volume ---
  LV Name                /dev/kiusa/root
  VG Name                kiusa
```


Nothing seems to work. Not /dev/kiusa/root nor /dev/mapper/kiusa-root , not root, not kiusa-root, not root, not rootfs, not fsroot.

What should I have on the "check device" to get it working. Now all I get with "sudo monit -t"
```
/etc/monit/monitrc:219: Error: syntax error 'check device'
```

Any help appreciated!

sunpower

---

### Post by Dedoimedo on 2008-09-18
Hello,

Try this:

```

# Monitor root(/) filesystem
check device kiusa-root with path /
        if space usage > 80 % then alert

```

Use the "rootfs" (whatever the real name is) without preceding slash ... use all of the names for your volume that you have tried earlier, in case this does not work.

I'll test at home over the weekend ...

Dedoimedo

---

