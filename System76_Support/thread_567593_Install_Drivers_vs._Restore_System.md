---
title: "Install Drivers vs. Restore System?"
date: 2007-10-04
forum: System76 Support
---

### Post by octathlon on 2007-10-04
(Using a new Pangolin -- panv3)

Just to clarify, with System76 Driver: I'm a little confused as to the difference between doing the "Install Drivers" and the "Restore System".  After the last couple of kernel updates, I ran Install Drivers to fix the sound, which worked fine.  Is there any reason at all that I should have run the "Restore System" instead?  

Any reason NOT to use Restore System, other than the fact that I would lose my xorg.conf modications (changed to color depth of 16 to avoid banding).

I've also noticed that since the first kernel update after getting the machine, coming back from suspend does not restore my wireless connection anymore--I have to restart the system to get it going again. Would Restore System do anything that Install Drivers doesn't do, that might fix this?

---

### Post by thomasaaron on 2007-10-05
It may.

It dumps in an xorg.conf and, I think, the /etc/default/acpi-support file in some models. I'd have to check, but it wouldn't hurt to try.

The wireless not coming back was dealt with in a bug report...
[https://bugs.launchpad.net/system76/+bug/122298](https://bugs.launchpad.net/system76/+bug/122298)
...and, I believe, implemented in the System 76 driver.

---

### Post by octathlon on 2007-10-06
Thanks for the info.

I ran Restore System, but it still isn't connecting properly after resuming -- the icon keeps doing the animation thing like it's trying and failing to connect.  I think it's a Network Manager problem where it is not using the network password from the keyring.  

However, I was able to get it to connect by clicking on "Connect to other wireless network", then clicking Cancel, which causes NM to show Disconnected (the icon that looks like 2 terminals with a red X). Then, I clicked on my wireless network in the list and it connected. I think this procedure makes NM start the connection from scratch and it goes and gets the password from the keyring.

As for the bug report ... I saw that doing Restore System did replace the acpi-support file, but it did not add network-manager to this line:

STOP_SERVICES="mysql "

I guess that is not done for Pangolins -- it doesn't seem to be necessary since NM is still running after suspend/resume anyway... so I did not modify the file as suggested in the bug report.

---

### Post by thomasaaron on 2007-10-08
Yeah, that sounds like a bug in Network Manager.
But, I wonder if it is happening on other machines.

---

### Post by imhavoc on 2007-10-08
My DU2 often doesn't resume correctly after a suspend.

I've noticed that the wireless card is recognized as a wired card and not as a wireless card. The network manager will not use the wrongly identified card to connect to wireless networks.

At that point, I'm left with a shotdown/reboot as the only solution to the problem.

---

### Post by thomasaaron on 2007-10-09
That's interesting.

How are you getting that, exactly?

I'm wondering if it is related to the DarU2's inability to connect to a wired connection if the machine was started without the ethernet cable inserted.

---

### Post by gaussian on 2007-10-09
> **imhavoc said:**
> My DU2 often doesn't resume correctly after a suspend.

I've noticed that the wireless card is recognized as a wired card and not as a wireless card. The network manager will not use the wrongly identified card to connect to wireless networks.

At that point, I'm left with a shotdown/reboot as the only solution to the problem.

I was having all these problems. Try the solution suggested in:

[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

under suspend support. That fixed all my DARU2 suspend problems (except the fact that it is s1, not s3, but that is not a biggie). If you don't want to go that far (modifying scripts), next time the network does not come up after suspend try (you might have to sudo for this):

/etc/dbus-1/event.d/25NetworkManager stop

Wait for a while and then:

/etc/dbus-1/event.d/25NetworkManager start 

Hope this helps

---

### Post by imhavoc on 2007-10-09
> **thomasaaron said:**
> That's interesting.

How are you getting that, exactly?

I'm wondering if it is related to the DarU2's inability to connect to a wired connection if the machine was started without the ethernet cable inserted.

Tom,

It may be. I've noticed that if I forget to plug into the network before powering up, I'm pretty much hosed. Powercycle is required.

The times that the wireless refuses to (re)connect, I can open WirelessAssistant, and it simply reports, "no wireless card found" and exists. I can run ifconfig, and I get eth0 and eth1 listed (as well as eth1:avah).

To complicate things, I'm running KDE, and I know that KDE's network manager can be a real pain in the backside sometimes. I've had to go so far as to manually kill it in the past to get basic network functionality from KDE apps when all of the Gnome apps worked perfectly.

---

### Post by imhavoc on 2007-10-09
> **gaussian said:**
> I was having all these problems. Try the solution suggested in:

[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

under suspend support. That fixed all my DARU2 suspend problems (except the fact that it is s1, not s3, but that is not a biggie). If you don't want to go that far (modifying scripts), next time the network does not come up after suspend try (you might have to sudo for this):

/etc/dbus-1/event.d/25NetworkManager stop

Wait for a while and then:

/etc/dbus-1/event.d/25NetworkManager start 

Hope this helps

Gaussian,

I'll try that next time. I'll see if I can force a failure of the wireless some time in the next couple of days.

thanks.

---

