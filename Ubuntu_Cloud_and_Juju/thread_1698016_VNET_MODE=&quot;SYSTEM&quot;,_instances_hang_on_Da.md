---
title: "VNET_MODE=&quot;SYSTEM&quot;, instances hang on DataSource"
date: 2011-03-01
forum: Ubuntu Cloud and Juju
---

### Post by silanea on 2011-03-01
Hallo!

I am stuck trying to get my instances to boot. My setup is really basic: All components are installed on one server which is set to VNET_MODE="SYSTEM" so I have the DHCP configuration for both my LAN and my instances in one place. I am aware that this is not the recommended setup but for my limited needs this appears to be the easiest way to run UEC.

Everything works great except for one thing: The Maverick UEC image hangs trying to get the DataSource from 169.254.169.254 which, as I understand, is not available when using SYSTEM mode. From some other forum post I gathered that boot should continue after 100 failed attempts and I could then access the instance. But this creates an unacceptable delay in the boot process. Is there any way to work around this? Either by preventing the instance from searching for that data (any hidden switches I could pass to the instance?), or by serving the information statically from my server? Since I will run at most a handful of instances and they will seldom change I would gladly apply a solution that requires doing things by hand.

Any chance of getting this to work?

Thank you!

silanea

---

### Post by kim0 on 2011-03-04
I think you need to pass this kernel param "ds=nocloud"
Either wait till the instance boots, and edit grub config file to add that. Or, if you launch new images frequently, rebundle and republish an image having that option built in

Read more at: [https://help.ubuntu.com/community/UEC/Images/KVMKernelOptions](https://help.ubuntu.com/community/UEC/Images/KVMKernelOptions)

---

