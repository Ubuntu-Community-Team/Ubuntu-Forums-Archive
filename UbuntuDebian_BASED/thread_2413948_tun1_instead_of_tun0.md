---
title: "tun1 instead of tun0?"
date: 2019-03-04
forum: Ubuntu/Debian BASED
---

### Post by pingaan on 2019-03-04
Hi,

Is it possible to rename the VPN connection to tun1 instead of tun0, when having only one VPN connection active?

Regards

---

### Post by raja.genupula on 2019-03-04
have you tried using `nmcli` ?

---

### Post by pingaan on 2019-03-04
No, you think it'd be possible with nmcli? This is actually concerns a Raspberry Pi, don't tell anyone! ;-)
Afaik nmcli is not native to Raspbian. Would it be possible in another way?

---

### Post by coffeecat on 2019-03-04
Raspbian. *Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by SeijiSensei on 2019-03-04
If you can edit the OpenVPN configuration file for the connection you can replace
```

dev tun

```
which dynamically allocates a tun device, with
```
dev tun1
```
to specify a device.

I've never used a GUI to set up OpenVPN connections, but then all my connections are [static]("https://openvpn.net/community-resources/static-key-mini-howto/").

---

### Post by pingaan on 2019-03-04
@SeijiSensei
That did the trick, thanks a lot!

---

