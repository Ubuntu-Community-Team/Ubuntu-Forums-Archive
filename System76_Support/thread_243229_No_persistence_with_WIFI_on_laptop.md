---
title: "No persistence with WIFI on laptop"
date: 2006-08-24
forum: System76 Support
---

### Post by eg-maverick on 2006-08-24
I have a new System76 laptop (in general, I really like it - thanks). I do however have a problem with the WIFI software/driver/hardware. I have wifi in my office, wifi at home, and my son has wifi at school. When I switch environments, I have to manually go into the system admin networking app to re-enter the WEP information and the correct SSID. There *has* to be a way to automatically switch between hotspots and wifi configs. I've tried adding the "Network Manager" from the add/remove programs utility but it doesn't appear.Thanks.
Craig

---

### Post by crichell on 2006-08-24
Hi Maverick,

Which model do you have?

You can install network-manager-gnome to manage wireless connections.

```
sudo apt-get install network-manager-gnome
```

Then reboot and you should see a new applet next to the clock.  By clicking on it you can choose your wireless network and enter the appropriate WEP key.  network-manager-gnome will keep track of the keys and once your in range automatically connect you to the "trusted" network.  "Trusted" because you opted to connect to it before.

---

### Post by frainbart on 2006-08-24
For my network-manager which shows up in the notification area, it automatically tries to connect to whatever I have connected to before. I only have to enter the WEP password once, and it remembers it. I left click on the icon and it lets you select whatever SSIDs are available.

---

### Post by eg-maverick on 2006-08-25
I entered the code as recommended and it seemed to install properly. The icon shows up in the notification toolbar. However, it says there is no network connection and there is an orange triangle with an exclamation point. And I did reboot. Obviously I do have a network connection (Wireless connection Eth1) as I am using it to get on this forum. 
Machine: Pangolin Centrino Duo 1.667, 1GB RAM.

Thanks,
Craig

---

### Post by crichell on 2006-08-25
We need to remove the wireless card from your interfaces file.

```
sudo gedit /etc/network/interfaces
```

You will see lines that look like:

```
iface eth1 inet dhcp
wireless-essid "Your ESSID"
auto eth1
```

Comment the lines out so they look like this

```
#iface eth1 inet dhcp
#wireless-essid "Your ESSID"
#auto eth1
```

Save and close the file.  Reboot and you should now see wireless networks when you click the drop down box.

---

### Post by eg-maverick on 2006-08-25
Carl,
Thanks. That was it. Seems like a pretty convoluted required set of steps to do something Windows can do out of the box. Nevertheless, it works and I am thankful for your help.
Craig

---

