---
title: "Serval Pro NIC - Not detected by alt. installer"
date: 2011-11-23
forum: System76 Support
---

### Post by oxsyn on 2011-11-23
Hello,

I've got a system76 15" serval professional.  I'm attempting to install ubuntu 11.10 from the alternate installer (i've got some requirements the desktop installer won't handle) - but the alternative installer isn't detecting my NIC.

I can't find any information on my NIC anywhere on the support site.  I need to know what the make/model is so I can manually load the correct NIC module.

Help? :)  Thanks!

---

### Post by isantop on 2011-11-23
I need to know which model your Serval is so that I can look up the proper NIC. It should be on the bottom, and be similar to SerP6.

---

### Post by oxsyn on 2011-11-23
> **isantop said:**
> I need to know which model your Serval is so that I can look up the proper NIC. It should be on the bottom, and be similar to SerP6.

serp7

---

### Post by isantop on 2011-11-23
Here's the relevant line from lspci:

```
 04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01) 
```

---

### Post by oxseyn on 2011-11-23
> **isantop said:**
> Here's the relevant line from lspci:

```
 04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01) 
```

Isn't that the wireless adapter?

---

