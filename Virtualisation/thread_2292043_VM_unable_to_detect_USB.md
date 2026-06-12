---
title: "VM unable to detect USB"
date: 2015-08-24
forum: Virtualisation
---

### Post by satimis on 2015-08-24
Hi all,

Host - Ubuntu 14.04
VM - Ubuntu 14.04
Oracle VirtualBox
USB - Samsung Galaxy S6 phone

Host detects the phone "Samsung Android"

On host terminal run;
&#10219; groups $satimis```

satimis adm cdrom sudo dip plugdev lpadmin sambashare vboxusers

```

VM
Settings -> USB 
check Enable USB Controller
check Enable USB 2.0 (EHCI) Controller
USB Device Filter
check New Filter1
all fields empty
Remote: Any

Please help.  Thanks

Regards
satimis

---

### Post by SeijiSensei on 2015-08-24
Did you install the Extension Pack in the guest?  Without it, USB is not available.

---

### Post by satimis on 2015-08-24
> **SeijiSensei said:**
> Did you install the Extension Pack in the guest?  Without it, USB is not available.
Hi,

Sorry, I forgot reboot PC after adding user to the group.  After reboot PC, now VM can detect Samsung Galaxy S6.

But still VM can't detect IPhone which is detected by the host

Edit:
Just discovered following warning on VM
```

Unable to mount SAMSUNG Android
unable to open MTP device '[usb:001,003]'
                          [OK]

```

But Samsung is under Devices on HOME

Regards
satimis

---

