---
title: "Accedental uninstall network manager"
date: 2013-06-06
forum: Ubuntu Studio
---

### Post by Acepony on 2013-06-06
My system got corrupt from the update manager and could not load a driver for the desktop and then it went into Terminal when I rebooted. I managed to reinstall the OS but no wifi. Apparently I was not paying attention either. I uninstalled the network manager and now no wifi at all. I can't help but think I will be laughing at this later on when I finally write my first script thinking I hope this works. Studying terminal and learning from mistakes is so much fun. Sorry for my attitude but I feel really dumb right now. I am aggravated at my self but I think the only way to reinstall this network driver is either download it from another computer and transfer using flash a drive or reinstall everything. I really don't want to start from scratch.

I really appreciate all the help you guys give. I hope some day I would be able to help people as well but that is a discussion for another day. Thanks again I would be lost without you guys.

---

### Post by steeldriver on 2013-06-06
Do you have access to a wired ethernet connection? if so it should be pretty easy to bring up a connection via the command line (ifconfig eth0 up) without network-manager, and then install it normally from the online repository

If you only have wireless access, then it's still possible to bring up without n-m - should just need a suitable entry in your /etc/network/interfaces file

---

### Post by Acepony on 2013-06-06
I have a cell phone that I tether with  shows up under the command "sudolsusb" The tether is on but I don't know if it will use it as a network. Will I need a lan specifically?

---

### Post by Acepony on 2013-06-06
Sorry should have made this one post. Was not thinking.

---

### Post by steeldriver on 2013-06-06
I've never tried it with a tether, however if you know your wireless SSID and passphrase (I'm assuming it uses WPA not WEP), router IP, and your router provides everything else via DHCP, then editing your /etc/network/interfaces file to add something like

```

auto wlan0
iface wlan0 inet dhcp
    wpa-ssid YOUR_SSID
    wpa-psk YOUR_PASSPHRASE
dns-nameservers 192.168.1.1

```

(obviously replace the 192.168.1.1 with your router's actual LAN IP) and rebooting is probably enough to get wireless access. If your router doesn't act as a forwarding DNS server, then try something like

```

auto wlan0
iface wlan0 inet dhcp
    wpa-ssid YOUR_SSID
    wpa-psk YOUR_PASSPHRASE
dns-nameservers 8.8.8.8 8.8.4.4

```

(uses google's public DNS servers). If it works, you can re-install network-manager and network-manager-gnome and then edit that stuff back out of the file.

---

### Post by Acepony on 2013-06-06
It says that the command "auto" does not exist. Is there an alternative command?

---

### Post by steeldriver on 2013-06-06
what are you doing exactly? you need to edit the file with root privileges, either

```
gksudo gedit /etc/network/interfaces
```

or

```
sudo nano /etc/network/interfaces
```

Actually the 'auto wlan0' line isn't essential, you can leave it out and bring the interface up manually

---

### Post by Acepony on 2013-06-06
I am just going to reinstall the OS. I would be trying to create a  script that could cause charges to my cell phone account if I did it  wrong. I think I have you on a wild goose chase anyway. Sorry and Thanks

---

### Post by steeldriver on 2013-06-06
No problem, good luck

---

### Post by Sylos on 2013-06-07
> **Acepony said:**
> I am just going to reinstall the OS. I would be trying to create a  script that could cause charges to my cell phone account if I did it  wrong. I think I have you on a wild goose chase anyway. Sorry and Thanks

If you have an installation disk (CD/DVD) then you could just try installing network-manager again using Synaptic.

Cheers

---

### Post by Acepony on 2013-06-07
I managed to reinstall the OS. I tried the things that was listed on the other threads but when I typed sudo rfkill list it listed nothing.

Edit; Help would be great

---

### Post by Acepony on 2013-06-07
I got it fixed and wifi now works

---

