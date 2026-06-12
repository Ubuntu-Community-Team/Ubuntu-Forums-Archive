---
title: "Failed to Open Session for the Virtual Machine"
date: 2017-10-20
forum: Virtualisation
---

### Post by Rick St. George on 2017-10-20
What .. another problem after running "autoremove", "autoclean", "update", "upgrade", "dist-upgrade". Now I get this Error;

```

 Implementation of the USB 2.0 controller not found!
 Because the USB 2.0 controller state is part of the saved VM state, the VM cannot be started. To fix this problem, either install the 'Oracle VM VirtualBox Extension Pack' or disable USB 2.0 support in the VM settings.
 Note! This error could also mean that an incompatible version of the 'Oracle VM VirtualBox Extension Pack' is installed (VERR_NOT_FOUND).

```

Note: upon upgrading VirtualBox, I elected, upon prompting me, to have newer Extension Pak installed. 

Anyone have any suggestions? I need to this up ASAP as it containes my Trading System.

Thanks!
):P

---

### Post by ajgreeny on 2017-10-20
After updating the Extension pack did you restart the VM?

It is always needed for those changes to occur in the VM itself.

---

### Post by Rick St. George on 2017-10-20
> **ajgreeny said:**
> After updating the Extension pack did you restart the VM?
It is always needed for those changes to occur in the VM itself.

Yes, this is the next day. I have it working by disabling the USB connection. But I use that connection from time to time and need it to work.
Thanks AJ! Any suggestions? 

Note: After Upgrade shows only version 5.1.30r118389 whereas current version if 5.2 !?!

---

### Post by Rick St. George on 2017-10-22
Updated VirtualBox to v5.2. I notice in SETTINGS / USB, I enable USB 1 and it works OK. When running I can see USB devices.
If I enable USB 2.0 EHCI controller, it shows at the bottom of window "Invalid Settings Detected".  Same with USB 3.0.

Even though I have USB 3.0 available on Host, I wondering ... Whats the problem ???
Is this something to be concerned about, since it is working?
Thanks!

---

### Post by Rick St. George on 2017-10-23
Please NOTE: According to VirtualBox website [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads);
**[COLOR=#FF0000]Update:[/COLOR]** The Guest Additions image with the 5.2.0 release fails to work with recent Linux guest kernels. 
Therefore, we will have to wait for a FIX.

---

