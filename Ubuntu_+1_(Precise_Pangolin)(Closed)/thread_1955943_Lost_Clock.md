---
title: "Lost Clock"
date: 2012-04-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by miwinning on 2012-04-10
The title says it all really. Lost the clock in the panel, and cant find any way to bring it back!

---

### Post by dino99 on 2012-04-10
gnome-panel --replace

---

### Post by miwinning on 2012-04-10
> **dino99 said:**
> gnome-panel --replace

  gnome-panel is not installed. Is is that just for gnome-shell and not Unity?

---

### Post by jbicha on 2012-04-10
Perhaps

```
sudo apt-get install indicator-datetime
```

If that fixes it, pay a bit more attention to what apt-get or Update Manager asks you to remove.

---

### Post by miwinning on 2012-04-10
> **jbicha said:**
> Perhaps

```
sudo apt-get install indicator-datetime
```If that fixes it, pay a bit more attention to what apt-get or Update Manager asks you to remove.

 It was already installed. I used Synaptic to re-install it, then loged out and in again and the clock is back.

---

