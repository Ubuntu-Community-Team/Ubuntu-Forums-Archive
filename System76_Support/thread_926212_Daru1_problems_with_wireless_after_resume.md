---
title: "Daru1: problems with wireless after resume"
date: 2008-09-21
forum: System76 Support
---

### Post by perce on 2008-09-21
If I hibernate with the wireless switch off, then at resume the wireless will not work, and I have to remove and reload the module iwl3945 in order to make it work again.

---

### Post by thomasaaron on 2008-09-22
Have you tried inserting that module into any of these lines in /etc/default/acpi-support?

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""


If one of these options work, we can get it into the System76 driver.

---

### Post by perce on 2008-09-22
> **thomasaaron said:**
> Have you tried inserting that module into any of these lines in /etc/default/acpi-support?

Not yet because I didn't know what ACPI configuration files to modify. I'll make some tests and report the results.

---

### Post by farrukh_najmi on 2009-09-10
I am having the same problem. When I resume from suspend wireless stops working. The wireless connection appears to be connected but I cannot access the network.

I am on a brand new installation of Jaunty on a new Acer Aspire 5536-5883 laptop.

I am not sure which module I need to load/unload per various threads I have seen.

Please let me know if I can provide more specific information in order to get help.

---

### Post by thomasaaron on 2009-09-11
What wireless card are you using?

> lspci

We only have System76 computers to test with...
[http://system76.com](http://system76.com)

...but I'll do what I can.

---

