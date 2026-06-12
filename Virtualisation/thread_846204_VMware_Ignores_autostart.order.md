---
title: "VMware Ignores autostart.order"
date: 2008-07-01
forum: Virtualisation
---

### Post by robgolding63 on 2008-07-01
Hi,
I have VMware running on Ubuntu Server 8.04, with a Domain Controller and Exchange Server VM.

I need the DC to come up before the Exchange server, but when using autostart.order, and autoStart.defaultStartDelay in the vmx and /etc/vmware/config files respectively, nothing changes and all VMs boot at one.

For one thing this hammers my host, and the guests encounter problems when booting as it is so slow, and also the Exchange Server doesn't come up properly as the DC isn't booted yet.

DC Config:
```

autostart = "poweron"
autostart.order = "10"

```

Exchange Config:
```

autostart = "poweron"
autostart.order = "20"

```

/etc/vmware/config:
```

autoStart.defaultStartDelay = "300"

```

If anyone can offer some help, it would be greatly appreciated.

Thanks,

Rob

---

### Post by robgolding63 on 2008-07-02
I've ended up scripting the process and placing a call to my script in **/etc/init.d/rc.local**.

If anyone is having the same problem or is just interested in my solution, the script looks like this:

```

#!/bin/bash

vmware-cmd /mnt/VMs/Zeus/Zeus.vmx start

sleep 240

vmware-cmd /mnt/VMs/apollo/apollo.vmx start

sleep 300

vmware-cmd /mnt/VMs/www/www.vmx start

```

So, does anybody have any comments or ideas as to my first problem, or just a way to improve my solution? :)

Rob

---

