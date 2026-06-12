---
title: "VMWare Server usb device detection error"
date: 2008-07-29
forum: Virtualisation
---

### Post by thefunnyman on 2008-07-29
A little information about my setup:
Host OS: Ubuntu Server 8.04  ( ssh server )
Guest 1: Ubuntu Server 8.04  ( file/print server )
Guest 2: Ubuntu Server 8.04  ( http server )

Alright, my print server build went fine, I enabled usb device detection and all was fine and dandy, usb devices were detected perfectly.  Then I installed vmware-tools, and now I'm getting errors when trying to configure my HP printer in the CUPS web interface.

relevant dmesg output:
```

[  111.647911] usb 1-1: new full speed USB device using uhci_hcd and address 6
[  111.780265] usb 1-1: device descriptor read/64, error -84
[  112.019349] usb 1-1: device descriptor read/64, error -84
[  112.250072] usb 1-1: new full speed USB device using uhci_hcd and address 7
[  112.379260] usb 1-1: device descriptor read/64, error -84
[  112.621152] usb 1-1: device descriptor read/64, error -84
[  112.850671] usb 1-1: new full speed USB device using uhci_hcd and address 8
[  112.882538] usb 1-1: device descriptor read/8, error -84
[  113.023229] usb 1-1: device descriptor read/8, error -71
[  113.252209] usb 1-1: new full speed USB device using uhci_hcd and address 9
[  113.291931] usb 1-1: device descriptor read/8, error -84
[  113.431704] usb 1-1: device descriptor read/8, error -71
[  296.948780] usb 1-1: new full speed USB device using uhci_hcd and address 10
[  297.079012] usb 1-1: device descriptor read/64, error -84
[  297.319333] usb 1-1: device descriptor read/64, error -84
[  297.549380] usb 1-1: new full speed USB device using uhci_hcd and address 11
[  297.679587] usb 1-1: device descriptor read/64, error -84
[  297.919820] usb 1-1: device descriptor read/64, error -84
[  298.150006] usb 1-1: new full speed USB device using uhci_hcd and address 12
[  298.185381] usb 1-1: device descriptor read/8, error -84
[  298.320407] usb 1-1: device descriptor read/8, error -71
[  298.550379] usb 1-1: new full speed USB device using uhci_hcd and address 13
[  298.585633] usb 1-1: device descriptor read/8, error -84
[  298.720835] usb 1-1: device descriptor read/8, error -71

```

Now, when installing vmware-tools, I did run 
```

sudo apt-get install build-essential linux-headers-`uname -r`

```

Can anyone explain to me what happened and how do I allow my VM to use the usb devices on my machine?

Thanks so much in advance.

thefunnyman

---

### Post by thefunnyman on 2008-07-31
bump...

---

### Post by meeck on 2008-10-13
Workaround: on host machine unload uhci_hcd  and load it again.

---

### Post by beyboo on 2008-11-02
[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=3862823](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=3862823)

---

### Post by ptaq666 on 2012-04-18
I have a similar problem, however I am unable to follow the instructions above, because I cannot create /proc/bus/usb directory. When I type 'sudo mkdir /proc/bus/usb' a receive an error:
[code]mkdir: cannot create`/proc/bus/usb': No such a file or directory[\code]

I also tried to unload uhci_hcd  and load it again. I typed 'modprobe uhci_hcd' and now, when I put my device into USB, dmesg returns NOTHING. The device is invisible :/

Could you help me to fix this, please?

---

