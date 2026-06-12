---
title: "usb detected but cannot be read in unity8 or containers"
date: 2016-12-01
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-12-01
USB drive detected but no apps can read files. 


```

          ID-2: USB /dev/sdb model: PDM09_32G_B9J2.0 size: 32.3GB  

```

---

### Post by ventrical on 2016-12-01
reported bug against unity8

[https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1646655](https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1646655)

---

### Post by ventrical on 2016-12-01
> **ventrical said:**
> reported bug against unity8

[https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1646655](https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1646655)

Can somebody confirm this bug please ?

Additional Info:

Plugging in USB stick will not activate any GUI icon or notification in Unity8.
Running any .deb based xapp filemanager in a container cannot read contents or data on USB stick.

thnxs

Regards..

---

### Post by ventrical on 2016-12-05
This bug:  [https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1646655](https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1646655)

now includes the proper package unity8-desktop-session

could somebody confirm this so we can put the bump on this bug ?
Thanks..

---

### Post by ventrical on 2016-12-05
add on:

> 
This bug is across several from factors. Using inxi in xterm (within a container) the USB can be identified. With gnome-disk-utility it recognizes /sdb as Block Device. If there is an .ISO on the device it will recognize the header but there seems to be no share or no network with the USB device. 

Other xapps that can identify  /sdb show a 32K partition on the drive .. none that I have seen before using standard ubuntu or any other desktop or app for that matter. So it appears that there is a pre-emptive 32K buffer of some sort that is blocking a link with the USB?

Regards.


---

### Post by ventrical on 2016-12-05
Uhhh... corresponding with devs on this issue and doing some research about xenial sunsetting  optical media, there is a possibility that unity8/snappy/containers may be cloud exclusive. One's ability to use mobile (USB) storage may be very limited, however, there is work being done on these bugs which I greatly appreciate. Cloud computing and thin clients are the future. Renting cloud space is also a source of revenue to  pay for a tremendous overhead I suppose. Legacy support can always be a thorn in a developers side as kernels, video servers and processes develop forward.

Regards..

-Gtk for unity8 
-LXC containers non-privlidged so a real mountain to climb.

---

