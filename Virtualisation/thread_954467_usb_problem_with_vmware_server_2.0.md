---
title: "usb problem with vmware server 2.0"
date: 2008-10-21
forum: Virtualisation
---

### Post by kalle_ka on 2008-10-21
I'm using vmware server 2.0 and have winXP SP3 as host and ubuntu 7.10 as guest.

I have added a usb controller via the Add hardware dialog and I have vmware tools installed.

The usb controller is configured to auto connect (I don't know about any other setting).

When I connect the usb device it shows up in the bottom uf the Vmware console (but all options, connect.. etc are greyed) and I cannot access the usb in Ubuntu.

I followed the instructions from [http://ubuntuforums.org/showpost.php...24&postcount=4](http://ubuntuforums.org/showpost.php...24&postcount=4)
but it still doesn't work.

I had it working with an older version of Vmware server (1.6 I think it was)

regards,

/Mattias

---

### Post by HelgeW on 2008-10-21
Hi Kalle,
i have toda the same problem with ubuntu host and windows client.
At the Console-view of server administration i found a drop down box for all found usb-devices. There you have to activate the device for the client.

I dont know about the GUI at windows, but i think it is the same WebGUI and you should found it there.

hope it help,
Helge

---

### Post by kalle_ka on 2008-10-21
Thanks, it helped. Now it works fine.

---

