---
title: "boot to black"
date: 2012-02-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by rtalcott on 2012-02-25
hp dm4 2180....i5 with only Intel graphics...installed 12.04 (today's daily build)...installs fine but boots to a black screen AFTER an Ubuntu purple screen...i can hear the login sound...if I attach an external monitor and boot I can log in on the external and then disconnect it and my hp display comes on at the proper resolution...the Intel video drivers are installed...

what is the trick to get this thing to boot with a live onboard display?
rt

---

### Post by rtalcott on 2012-02-25
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=linux pci=noacpi"

After making the change to that line issue following command

$ sudo update-grub

Thank you!
[http://ubuntuforums.org/showthread.php?t=1817374](http://ubuntuforums.org/showthread.php?t=1817374)

---

