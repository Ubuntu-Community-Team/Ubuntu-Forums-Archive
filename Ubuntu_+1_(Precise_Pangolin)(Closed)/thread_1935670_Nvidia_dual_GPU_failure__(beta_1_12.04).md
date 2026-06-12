---
title: "Nvidia dual GPU failure  (beta 1 12.04)"
date: 2012-03-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by odror on 2012-03-04
I have a dual GPU system 4 monitors.

GPU 0: GeForce GT 440
GPU 1: GeForce GTX 550 Ti

Nvidia version: 295.20 linux-x86_64

I am only seeing one monitor
I get the following error in the "X server Configuration"
> Unable to load X Server Display Configuration page:

Failed to query name of display device
0x00100000 connected to GPU-1 'GeForce GTX 550 Ti'.

any help will be appreciated. Thanks

---

### Post by cariboo on 2012-03-04
Have yopu tried running:

```
sudo nvidia-xconfig
```

as it looks like one of your monitors is not being detected properly.

---

### Post by odror on 2012-03-05
> **cariboo907 said:**
> Have yopu tried running:

```
sudo nvidia-xconfig
```

as it looks like one of your monitors is not being detected properly.

I tried that. It did not solve the problem.

I solved the problem by copying an old xorg.conf file from a previously installed older version of ubuntu. Of course this does not tell what was wrong. I am guessing that it is a bug in X11/nvidia driver compatibility with the geforce 550 ti card.

---

