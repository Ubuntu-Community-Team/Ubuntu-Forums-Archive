---
title: "Network Card Disabled - Won't start on boot"
date: 2014-10-15
forum: Server Platforms
---

### Post by peridian on 2014-10-15
Ubuntu Server 14.04

Hi,

My device was not connected on its network card when Ubuntu was installed (picked option "Do not configure network" or some such).  Now I have connected it, and added the relevant text in /etc/network/interfaces

```

iface eth0 inet static
address 10.x.x.x
netmask 255.255.255.0
gateway 10.x.x.1

```

However, ifconfig never shows the device.  Running **sudo lshw -class network** shows the device as "* - network DISABLED"

After googling, I ran **sudo ip link list**, which showed the actual label for the interface as p1p1, so I updated the interfaces file from eth0 to p1p1 and rebooted.

The card still shows as disabled after reboot, although using ifconfig to configure and run the interface (**sudo ifconfig p1p1 up**) works, but does not pickup the interfaces file, nor does it remain up upon reboot.

If you disabled the network in the setup, how do you enable the interface from the command line once you're logged in?

Regards,
Rob.

---

### Post by davit2 on 2014-10-16
Hi, 
1.Open terminal and type

$ cd /etc/network/if-up.d
$ sudo touch net.sh
$ sudo chmod a+x net.sh
$ sudo vim net.sh

2.put these lines in net.sh file  and save file. (:wq)

#!/bin/bash
sudo ifconfig p1p1 up

3.reboot

---

### Post by peridian on 2014-10-16
Hi,

Followed those instructions exactly and rebooted twice to be sure.  No change.  I've checked in the BIOS that nothing is disabled by default, but the fact a manual command works makes me think that's not the issue.

Regards,
Rob.

---

### Post by nerdtron on 2014-10-16
Errors found in your config:

First: p1p1 is your interface so you should edit your /etc/network/interfaces file and change eth0 to p1p1.
Second: It won't start on boot because **you did not specify it to run on boot**. You need to add the line "auto p1p1"

Summary:
```

**auto p1p1**
iface p1p1 inet static
address 10.x.x.x
netmask 255.255.255.0
gateway 10.x.x.1

```

After reboot, let's see the result. If it still fails, paste the your complete /etc/network/interfaces file here.

---

### Post by peridian on 2014-10-16
Hi,

As per my first post, I had already changed the interface name.  However the file only had **auto lo** at the start, so I added **auto p1p1 **and rebooted.  That is now working as expected.

Thanks for the help.

Regards,
Rob.

---

