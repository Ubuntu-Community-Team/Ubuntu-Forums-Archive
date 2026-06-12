---
title: "xorg crashes -bug"
date: 2015-10-16
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-10-16
Xorg crashed after update/upgrade.



[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1506714](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1506714)

---

### Post by syntaxerror74 on 2015-10-16
Questioning my crystal ball revealed...you must be using compiz.

Because the original bug (note: yours has been marked 'duplicate') is compiz related, and there are no complaints of Openbox users yet.
Might even explain why I've had no problems here on Lubuntu (yet).

---

### Post by ventrical on 2015-10-16
> **syntaxerror74 said:**
> Questioning my crystal ball revealed...you must be using compiz.

Because the original bug (note: yours has been marked 'duplicate') is compiz related, and there are no complaints of Openbox users yet.
Might even explain why I've had no problems here on Lubuntu (yet).

It's a raw xubuntu install that I have been updating from the beginning of 15.10 cycle. No compiz.

 I'll check again.

---

### Post by ventrical on 2015-10-16
No compiz. Bug is provoked by calling .xinitrc with invalid desktop. Solved: edit in correct desktop configuration; ie;

> 
exec razor-desktop


---

### Post by syntaxerror74 on 2015-10-20
Congrats dude! You might help hundreds of other users that may be running into the same problem the next days and weeks.

P.S. I don't have an ".xinitrc" at all, as I've just noticed.
However, 'locate' revealed a system-wide xinitrc in /etc/X11/xinit/xinitrc (barely anything essential in there, though)
And there is another 50-systemd-user.sh in .../xinitrc.d/ with only the following line
```

systemctl --user import-environment DISPLAY XAUTHORITY
``` Presumably, Xubuntu and Lubuntu will handle the X Window startup procedure way more differently than it ought to be assumed, considering they're both "just" Ubuntu flavors.

---

### Post by ventrical on 2015-10-20
My apologies. I forgot to mention that the above solution only seems to work with upstart at the moment. I had to fall back to a stable install. I got it working in wily current (upstart) but it is not as sharp and quick as is 14.04 .. so there are some problems...

Regards..

oh yeah.. and another weird thing... on stable the .xinitrc is in /home/ by default.

So we have:
(upstart)
.xinitrc in /home/

with wily (xubuntu) we have to choose (upstart) in GRuB
.xinitrc has to be *created* and will only exist in /home/user_name/ however , it can still be invoked from that directory. I usually use .xinitrc with ubuntu-desktop, not xubuntu-desktop so I have some more experimenting to do. I didn't think that different DEs would have different file conventions with .xinitrc. I'll check and see.

regards..

---

### Post by zika on 2015-10-21
> **syntaxerror74 said:**
> Congrats dude! You might help hundreds of other users that may be running into the same problem the next days and weeks.

P.S. I don't have an ".xinitrc" at all, as I've just noticed.
However, 'locate' revealed a system-wide xinitrc in /etc/X11/xinit/xinitrc (barely anything essential in there, though)
And there is another 50-systemd-user.sh in .../xinitrc.d/ with only the following line
```

systemctl --user import-environment DISPLAY XAUTHORITY
``` Presumably, Xubuntu and Lubuntu will handle the X Window startup procedure way more differently than it ought to be assumed, considering they're both "just" Ubuntu flavors.Code given as difference is a simple patch to overcome lack of more versatile DM. Also to help with those that use (wrongly) sudo with StartX. Simple```
env|grep XA
```would show You.

---

### Post by Chanath on 2015-10-21
Practically no problem with my Openbox install. No compiz and no specific DE.:D

---

