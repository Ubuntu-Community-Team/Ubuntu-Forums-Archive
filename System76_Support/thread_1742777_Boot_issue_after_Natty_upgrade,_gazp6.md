---
title: "Boot issue after Natty upgrade, gazp6"
date: 2011-04-29
forum: System76 Support
---

### Post by TheSqueak on 2011-04-29
I went through the Natty upgrade process yesterday, and everything worked perfectly up until it came time to reboot, at which point it came up with a grub error saying

```
error: symbol not found: 'grub_env_export'
grub rescue>
```

So I booted from a Natty LiveCD and purged and reinstalled grub-pc and grub-common (following some instructions on the forums for dealing with this problem)

That got it booting ok, but with a really crappy low resolution plymouth screen. After reinstalling the System76 drivers and playing with plymouth-manager, i've got it to the point that I see the proper plymouth animation at it's proper resolution when I shut down, but when I reboot there's nothing at all until the login screen.


(I don't think this is related, but the other minor issue i've run into is the background of my KMenu launcher is garbled - see [http://oi55.tinypic.com/96kkt0.jpg](http://oi55.tinypic.com/96kkt0.jpg) for what I mean)

---

