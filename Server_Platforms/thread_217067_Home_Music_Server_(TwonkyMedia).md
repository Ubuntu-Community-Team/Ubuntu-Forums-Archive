---
title: "Home Music Server (TwonkyMedia)"
date: 2006-07-16
forum: Server Platforms
---

### Post by Kangaroo on 2006-07-16
Im thinking about getting myself on these Noxon Audio 2-Babies, but i don't want to turn on my PC everytime i want to listen to music. Insteat i'm thinking about getting myself a Via Eden platform (600Mhz Proc - passive cooling) and use it as a dedicated music server within my home network (with no monitor or keyboard attached, TwonkyMedia Server can be configured through web-interface)  

Ubuntu, as a server install, would probably my best bet to use as OS. Only some questions left: 

1.) How to make Ubuntu Server auto-connect to my WEP-protected WLAN upon boot ? 
2.) How to get Ubuntu to auto-login to my user account upon boot ? 
3.) Hot to get Ubuntu to auto-start twonky-server 
4.) What can i use to put new music on the Server's harddrive without having to attach a monitor or keyboard (FTP?) and how would that work ? 
5.) How to get Ubuntu to shutdown properly upon pressing the power button ? 

I'd know the answer to 1-4 if there was a GUI involved, but i want it to be a server install (fast boot-times). So how do i achieve this on CLI.

---

### Post by Kurt` on 2006-07-16
> **Kangaroo said:**
> 
2.) How to get Ubuntu to auto-login to my user account upon boot ? 
3.) Hot to get Ubuntu to auto-start twonky-server 
4.) What can i use to put new music on the Server's harddrive without having to attach a monitor or keyboard (FTP?) and how would that work ?

2) See 3.
3) Configure the twonky-server to automatically run at boot (doesn't require a user to be logged in automatically)
4) [Samba](http://ubuntuguide.org/wiki/Dapper#Samba_Server). Just share your music folder across your workgroup/domain, enter your user/pass, drag and drop your music. Simple enough. :)

Not sure about 1. and 5. though. Good luck.

---

### Post by nagilum on 2006-07-18
1) First you need the wireless-tools, then edit /etc/network/interfaces (see: 'man 5 interfaces' and 'man 7 wireless'). There's also wpa_supplicant if you consider migrating to WPA some time. Quick example:
```

auto wlan0
iface wlan0 inet dhcp
    wireless-essid MyNetwork
    wireless-enc s:MyWEPKey  # literal string passwords must be prefixed with  's:'

```

5) Install the acpid package, it installs a file /etc/acpi/powerbtn.sh which is executed every time the power button is pressed. Uncomment the 'shutdown -h now ...' line at the bottom and it should work (assuming your machine doesn't lack ACPI support; works fine on my ~2 year old VIA C3)

---

