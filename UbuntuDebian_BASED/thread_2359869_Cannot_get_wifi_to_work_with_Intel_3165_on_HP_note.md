---
title: "Cannot get wifi to work with Intel 3165 on HP notebook"
date: 2017-04-29
forum: Ubuntu/Debian BASED
---

### Post by austin-green on 2017-04-29
Grateful for suggestions on how to debug this.

Computer is HP notebook model 'HP 14-an006AU'.
Network controller Intel 3165.
Router is D-Link.
Connects wireless OK when same notebook is booted to Windows 10.
OS is Trisquel 7.0, derived from Ubuntu 14 I believe.
Linux kernel is 3.13.0-116-lowlatency.

Following directions here:
    [https://xargs.top/2016/01/14/ubuntu-14-04-3-install-intel-3165-network-adapter-driver/](https://xargs.top/2016/01/14/ubuntu-14-04-3-install-intel-3165-network-adapter-driver/)
downloaded drivers from
    [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.3/backports-4.3-1.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.3/backports-4.3-1.tar.gz)
and built successfully.
Downloaded firmware from:
    [https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7265-ucode-25.30.13.0.tgz](https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7265-ucode-25.30.13.0.tgz)
and copied iwlwifi-7265D-13.ucode to /lib/firmware.

Results from running wireless-info script:  [http://paste.ubuntu.com/24477127/](http://paste.ubuntu.com/24477127/)

On trying to connect manually (to the wireless router identified as 'Beakynet') via the Network Manager icon:
```

$ dmesg              
[ 3525.521588] wlan0: authenticate with 14:d6:4d:26:ce:36
[ 3525.523931] wlan0: send auth to 14:d6:4d:26:ce:36 (try 1/3)
[ 3525.525696] wlan0: authenticated
[ 3525.526926] wlan0: associate with 14:d6:4d:26:ce:36 (try 1/3)
[ 3525.529998] wlan0: RX AssocResp from 14:d6:4d:26:ce:36 (capab=0x431 status=10 aid=1024)
[ 3525.530016] wlan0: 14:d6:4d:26:ce:36 denied association (code=10)

```

---

### Post by wildmanne39 on 2017-04-29
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by austin-green on 2017-05-02
Nobody has looked at this thread since it was moved from Wireless/Networks :( but anyway here's an update.

Removed Trisquel and installed Xubuntu 16.04 instead, which worked 'out of the box'.  I guess the problem was either mismatching driver/kernel versions, or perhaps just kernel too old.  I'd still be interested to hear if anyone has a fix for the Trisquel installation, but for now I'm happy with Xubuntu.

---

