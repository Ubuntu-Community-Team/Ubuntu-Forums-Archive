---
title: "Theme Configuration"
date: 2018-03-22
forum: Ubuntu Development Version
---

### Post by Crimple on 2018-03-22
Hi.
I noticed that in Xubuntu 18.04 the Theme Configuration (see pic) is absent.
Why? Will it be so in the final release? Will it still be available to download through the Repositories?
Thanks.

---

### Post by Frogs Hair on 2018-03-22
There are some applications not showing up in Ubuntu Software that are in the repos, 18.04 is still Beta so you could try via the terminal. 

[https://launchpad.net/ubuntu/+source/gtk-theme-config](https://launchpad.net/ubuntu/+source/gtk-theme-config)


```
sudo apt install gtk-theme-config
```

---

### Post by Frogs Hair on 2018-03-22
Moved to *Ubuntu Development Version.*

---

### Post by Crimple on 2018-03-22
You see, this app is maintained by the Xubuntu developers and I was wondering if they're dropping it. It's quite a handy tool ;)

---

### Post by Frogs Hair on 2018-03-22
See the  launchpad link  posted . 

> Maintainer:
Xubuntu Developers


---

### Post by flocculant on 2018-03-22
> This release, we decided to remove the GTK Theme Configuration tool. It is no longer possible to override colors in all themes with a single application due to recent developments in GTK. It may return in a later release, but with limited functionality or theme support. 

It might return - current thinking is that IF it does, then it will likely not cover all themes.

---

### Post by Crimple on 2018-03-22
Thanks both :)

---

### Post by jbicha on 2018-03-22
The [Debian bug]("https://bugs.debian.org/886068") has some context.

---

### Post by Crimple on 2018-03-22
Thanks for the info.

---

### Post by flocculant on 2018-03-23
> **jbicha said:**
> The [Debian bug]("https://bugs.debian.org/886068") has some context.

Thanks for linking that.

---

