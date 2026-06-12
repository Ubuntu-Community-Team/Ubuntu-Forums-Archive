---
title: "Panp6 karmic wireless flaky"
date: 2011-03-17
forum: System76 Support
---

### Post by factor2 on 2011-03-17
I've had a Pangolin running Karmic for about a year and I've had intermittent problems with wireless at home. It cannot connect, and also does not store the wep 64 password. The wireless card is Intel's Wifi Link 5100.

The router is Netgear WGR614 and there is no firmware to upgrade to at this moment. 

If I turn off the wireless using the keyboard (Fn F11) and turn it back on the antenna appears dead, and no longer picks up any wireless signals. The router shares the desk with the laptop. 

For a while if I rebooted wireless it would start working again. but that is no longer true.

---

### Post by isantop on 2011-03-17
Would it be possible to try it with a WPA key? That could make a difference.

---

### Post by factor2 on 2011-03-28
I've tried with WPA and I'm still evaluating. It cut out a few times, but with less frequency than WEP. 

I'm wondering now if it's at all an issue with the network manager? Most recently when it cut out I went into the wireless security within the nm-applet GUI and it had forgotten the saved password.

---

### Post by isantop on 2011-03-29
That's a possibility. Try running these commands from a terminal:

```
sudo apt-get clean
sudo apt-get install --reinstall network-manager
```

---

### Post by factor2 on 2011-04-21
> **isantop said:**
> Would it be possible to try it with a WPA key? That could make a difference.

That was it - WPA key is working consistently. Thanks!

---

