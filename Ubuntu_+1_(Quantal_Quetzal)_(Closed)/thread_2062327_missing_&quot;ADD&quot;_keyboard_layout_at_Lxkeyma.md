---
title: "missing &quot;ADD&quot; keyboard layout at Lxkeymap"
date: 2012-09-24
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by GeorgeVita on 2012-09-24
I am [posting again]("http://ubuntuforums.org/showthread.php?t=1911677") my thoughts for an essential problem:
**Lubuntu needs an easy procedure to ADD multiple keyboard layouts** (at least two) and set the "hot key" to switch between layouts for non English speaking users (ex. users from Greece or Taiwan). 

This procedure could be included into **Lxkeymap** as reported to bug/wish [#904386]("https://bugs.launchpad.net/lxkeymap/+bug/904386")

More info from Ubuntu-1 (P.P):
> **GeorgeVita said:**
> Possible solution is via the terminal command:
```
setxkbmap -layout "us,gr" -option "grp:ctrl_shift_toggle"
```
which can be permanent by editing the same parameters into file /etc/default/keyboard

But using lxkeymap overrides above setting (after testing the keyboard layouts with lxkeymap the "hot key" stops changing them).


P.S. at this time I am using Lubuntu QQ daily live of 23-Sep-12

---

### Post by GeorgeVita on 2012-09-26
Lxkeymap developer says that he has fixed it but:

> From comment #10 of [https://bugs.launchpad.net/lxkeymap/+bug/904386](https://bugs.launchpad.net/lxkeymap/+bug/904386)

It is currently in the upstream version. The daily builds ship not the latest however. As I am not the maintainer of the Ubuntu package I really don't know if they will ship the fixed version or not.

How can we inform developers of Lubuntu to include the latest Lxkeymap version?

---

