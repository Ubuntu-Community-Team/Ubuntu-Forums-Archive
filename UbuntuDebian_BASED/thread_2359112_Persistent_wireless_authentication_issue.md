---
title: "Persistent wireless authentication issue"
date: 2017-04-20
forum: Ubuntu/Debian BASED
---

### Post by jacoballegre on 2017-04-20
Hi!
I'm a very new to these forums, and quite new to Linux itself really, so any help from experienced users would help me a lot :).

I have a Dell Inspiron 1545 laptop computer running the latest version of LXLE. In the last few days I have gone through Ubuntu 14.04 and Ubuntu 16.04 as well as LXLE trying to solve my issue, but since all three of the operating systems are based upon one another, the issue persists.

The issue in question is that whenever I try to connect to a wireless network, it will, of course, require authentication in the form of a password or encryption key. But when I enter the correct password, the computer will take about a half a minute to try and connect, fail, and ask for authentication again. This same issue has persisted through all three OSs, even after installing drivers for my wireless card.

The network controller for my laptop is a BroadCom Corporation BCM4312. 
I have no issues connecting via ethernet cable or a tethered USB device, in this case my Samsung Note 5.

I'm aware I'm likely leaving a lot of vital information out of this post, simply because I do not know what needs to be posted to solve the issue. If anyone knows how to fix this problem and needs me to post more information, just let me know and I will. I'm at my wits end with this issue. Thanks!

P.S. Yes, my wireless hardware switch is on. My computer recognizes all surrounding wireless networks, but fails to connect to any of them.

P.P.S. Preferably I would like for the solution to be pertinent to Ubuntu 16.04, but if there are any solutions for any of the three OSs, I will be happy with any one :)

---

### Post by wildmanne39 on 2017-04-20
Click on the wireless script in my signature and follow the directions for running it and posting the link created to pastebin here.

---

### Post by howefield on 2017-04-21
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by jacoballegre on 2017-04-21
Thanks wildmanne39 for the guidance!
Here's the pastebin link: [http://paste.ubuntu.com/24427707/](http://paste.ubuntu.com/24427707/)

I also followed the instructions found in "[SOLVED] How to install a driver for the Broadcom series of PCI wireless cards", and after locating and attempting to install the proper driver for my [14e4:4315] (rev 01) pci.id, the terminal informed me that I already had the driver and that it was already updated, yet of course the issue remains.

---

### Post by wildmanne39 on 2017-04-21
Is this the network you are trying to connect too JacobsWifi ? this is the firmware you installed firmware-b43-installer?
Thanks

---

### Post by jacoballegre on 2017-04-21
Correct, I am trying to connect to JacobsWifi, and firmware-b43-installer is the one that I tried to install from the Broadcom driver list, and found to already be installed and up-to-date.

(Thank you for working with me, I'm sure its tedious having to ask these questions that I should've already stated in the question itself)

---

### Post by wildmanne39 on 2017-04-22
No problem, no one starts out knowing any of this stuff.

Please go into network manager and set your settings to match the screenshots.

We may have to try the other driver but this is the one that should work the best.

Please do:
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e wlan -e etwork | tail -n25
```
Make sure that all ethernet connections are unplugged first, because they will over ride your wifi connection.

Thanks

---

### Post by jacoballegre on 2017-04-22
After changing my network settings to match the screenshots, disconnecting my ethernet cable, and running the cat command, I tried to connect to my wifi network, and the same problem persisted. 

Here are the results of the cat command, for reference.

```
Apr 22 21:17:09 jacob-Inspiron-1545 NetworkManager[858]: <info> Policy set 'Wired connection 2' (usb0) as default for IPv4 routing and DNS.
Apr 22 21:17:09 jacob-Inspiron-1545 NetworkManager[858]: <info> Writing DNS information to /sbin/resolvconf
Apr 22 21:17:09 jacob-Inspiron-1545 NetworkManager[858]: <info> Activation (usb0) successful, device activated.
Apr 22 21:17:26 jacob-Inspiron-1545 NetworkManager[858]: <info> (usb0): IP6 addrconf timed out or failed.
Apr 22 21:17:26 jacob-Inspiron-1545 NetworkManager[858]: <info> Activation (usb0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 22 21:17:26 jacob-Inspiron-1545 NetworkManager[858]: <info> Activation (usb0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 22 21:17:26 jacob-Inspiron-1545 NetworkManager[858]: <info> Activation (usb0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Apr 22 21:19:35 jacob-Inspiron-1545 dhclient: receive_packet failed on usb0: Network is down
Apr 22 21:19:35 jacob-Inspiron-1545 NetworkManager[858]: <info> (usb0): carrier now OFF (device state 100, deferring action for 4 seconds)
Apr 22 21:19:35 jacob-Inspiron-1545 NetworkManager[858]: <info> (usb0): device state change: activated -> unmanaged (reason 'removed') [100 10 36]
Apr 22 21:19:35 jacob-Inspiron-1545 NetworkManager[858]: <info> (usb0): deactivating device (reason 'removed') [36]
Apr 22 21:19:36 jacob-Inspiron-1545 NetworkManager[858]: <info> (usb0): canceled DHCP transaction, DHCP client pid 2781
Apr 22 21:19:36 jacob-Inspiron-1545 NetworkManager[858]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/usb0/accept_ra': (2) No such file or directory
Apr 22 21:19:36 jacob-Inspiron-1545 NetworkManager[858]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/usb0/use_tempaddr': (2) No such file or directory
Apr 22 21:19:36 jacob-Inspiron-1545 NetworkManager[858]: <warn> (6) failed to find interface name for index
Apr 22 21:19:36 jacob-Inspiron-1545 NetworkManager[858]: nm_system_iface_flush_routes: assertion 'iface != NULL' failed
Apr 22 21:19:36 jacob-Inspiron-1545 NetworkManager[858]: <warn> (6) failed to find interface name for index
Apr 22 21:19:36 jacob-Inspiron-1545 NetworkManager[858]: <warn> DNS: plugin dnsmasq update failed
Apr 22 21:19:36 jacob-Inspiron-1545 NetworkManager[858]: <info> Removing DNS information from /sbin/resolvconf
Apr 22 21:19:36 jacob-Inspiron-1545 NetworkManager[858]: <info> (usb0): cleaning up...
Apr 22 21:19:36 jacob-Inspiron-1545 NetworkManager[858]: <warn> (6) failed to find interface name for index
Apr 22 21:19:36 jacob-Inspiron-1545 NetworkManager[858]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Apr 22 21:19:36 jacob-Inspiron-1545 NetworkManager[858]: <error> [1492913976.57221] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Apr 22 21:19:36 jacob-Inspiron-1545 NetworkManager[858]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Apr 22 21:19:36 jacob-Inspiron-1545 NetworkManager[858]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/net/usb0, iface: usb0)

```
It is also worth noting that prior to this post I was using LXLE, but I wiped and performed a fresh install of Ubuntu 14.04 to a) better match the screenshots and b) see if maybe it would work after following your previous tips (unfortunately it did not). Should I upgrade to Ubuntu 16.04 and then try again? Or do I need to do something else entirely?

---

### Post by wildmanne39 on 2017-04-22
So after you ran the command to post that output you installed 14.04? that output was to help me see what is wrong and if you changed Ubuntu's then it is not going to be the same.

I believe you need to install different firmware in 14.04, please post the output from the OS you are using now and the command I gave you to run.
Thanks

---

### Post by jacoballegre on 2017-04-27
Sorry, I worded that poorly. The output I posted is correct, I installed Ubuntu first and then ran the commands you told me to. The output is for my current OS (Ubuntu 14.04), not the previous one.

---

### Post by wildmanne39 on 2017-04-27
Please run the wireless script again and let's see where we are at since you are using 14.04 now.
Thanks

---

### Post by wildmanne39 on 2017-04-27
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

