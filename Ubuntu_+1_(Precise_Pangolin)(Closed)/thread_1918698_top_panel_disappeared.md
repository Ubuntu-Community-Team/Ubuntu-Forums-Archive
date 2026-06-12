---
title: "top panel disappeared"
date: 2012-02-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sonicb00m on 2012-02-01
Today when logging in my top panel has disappeared. This happens on both Unity and Unity 2D.

I upgraded to Unity Testing 5.2 and when I logged in the top panel had reappeared.

Now after a reboot it has disappeared again.

Anyone know how to get it back permanently?

---

### Post by sonicb00m on 2012-02-01
Seems to be related to the intel video driver.

I did 

```

apt-get install --reinstall install xserver-xorg-video-intel
dpkg-reconfigure xserver-xorg

```
And logged back in and the top panel reappeared.

After logging out and back in the top panel has disappeared again. Some compositing problem maybe?

---

### Post by sonicb00m on 2012-02-02
Seems to be a problem with the IGP i3 graphics. I installed my ATI card and now the top panel is running fine.

---

