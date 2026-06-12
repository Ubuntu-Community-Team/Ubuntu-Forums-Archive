---
title: "Shutdown not happening..."
date: 2013-09-11
forum: Ubuntu Development Version
---

### Post by TenPlus1 on 2013-09-11
The latest daily of Lubuntu 13.10 boots and works fine but has a few problems at the end of the day...  When I try to shutdown and select 'Logout' from the menu, nothing appears...  So into terminal I go and type 'sudo shutdown now' and it closes my display and sits there in terminal doing nothing...  Rebooring works ok but the only way I can safely shutdown my computer is using ALT GR, PRN SCRN + R E I S U B O...

---

### Post by TenPlus1 on 2013-09-12
Latest update fixed problem :P

---

### Post by TenPlus1 on 2013-09-19
Nope, still not displaying shutdown menu or closing properly in terminal...

---

### Post by QDR06VV9 on 2013-09-19
> **TenPlus1 said:**
> Nope, still not displaying shutdown menu or closing properly in terminal...

Im not using lubuntu but that has happened to me also, but i run cairo-dock and the shut down && reboot options worked well.
Just a thought.
Regards

---

### Post by grahammechanical on 2013-09-19
I use either of these two commands

```
sudo shutdown -h now
```
```
sudo shutdown -r now
```

-h = halt. -r = reboot.

It is possible that you are shutting down Ubuntu but not shutting down Linux that Ubuntu sits upon.

I am in the habit of daily updating the development branch in the hope that bugs get fixed. I am not disappointed too often. The weeks before release date are when the developers fix bugs instead of bring in new features. Things may turn out fine over the next few weeks. Alternatively, wait until Lubuntu 13.10 is released and reinstall and see if the problem has been fixed.

Regards.

---

### Post by grahammechanical on 2013-09-19
Sorry. I have deleted what turned out to be a double post.

---

### Post by TenPlus1 on 2013-09-21
I have installed the latest daily for Lubuntu 13.10 beta and now the shutdown menu is appearing and closing down properly...  weird!

---

### Post by jerrylamos on 2013-09-22
One of my 64 bit v-e-r-y    s-l-o-w  ....  in displaying the shutdown/restart choices and   v-e-r-y  s-l-o-w  shutting down.  I have a notebook 64 bit and a tower 32 bit no problem, all at or near the same level of saucy.

---

