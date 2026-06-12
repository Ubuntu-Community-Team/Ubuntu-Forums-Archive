---
title: "bluetooth in centrino wireless-n 2230"
date: 2013-04-02
forum: System76 Support
---

### Post by kazzmir on 2013-04-02
I have the pangolin performance 12.10 laptop with an Intel Centrino Wireless-N 2230

```

02:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)

```

Supposedly this controller has built-in bluetooth support but I can't figure out how to enable it. When I plug a usb bluetooth dongle in the dongle works fine. Is there a way to use bluetooth with the builtin adapter?

---

### Post by isantop on 2013-04-02
What model system do you have? Did you upgrade the card manually? We've never sold a 2230.

---

### Post by kazzmir on 2013-04-02
Oops, its not a pangolin, its a gazelle. I have not upgraded the card manually.

Model: gazp8
Intel Centrino 1030 - 802.11 b/g/n Wireless LAN + Bluetooth Combo Module

But lspci is reporting that I have a 2230..

---

### Post by kazzmir on 2013-04-04
Bump

---

### Post by isantop on 2013-04-05
You can try pressing Fn+F12. That said, it sounds like you may have a bad or the wrong card.

---

### Post by kazzmir on 2013-04-05
Uhm, haha wow! Pressing Fn+F12 worked!

This just appeared
```

$ dmesg | tail
[680667.431287] usb 3-4: new full-speed USB device number 67 using xhci_hcd
[680667.561825] usb 3-4: New USB device found, idVendor=8087, idProduct=07da
[680667.561830] usb 3-4: New USB device strings: Mfr=0, Product=0, SerialNumber=0

```

And bluetooth shows up in rfkill
```

$ rfkill list
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
4: hci1: Bluetooth
        Soft blocked: no
        Hard blocked: no

```

---

### Post by isantop on 2013-04-05
The Fn+F12 hotkey physically switches the Bluetooth portion of the card on and off.

---

