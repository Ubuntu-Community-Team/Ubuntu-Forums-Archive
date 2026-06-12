---
title: "Change MAC address."
date: 2012-10-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by danbrownlow on 2012-10-15
Hey,

I often need to change my MAC address and when I was running 12.04 I was able to do this by using: 

```

sudo service network-manager stop
sudo ifconfig wlan0 hw ether xx:xx:xx:xx:xx:xx

```

But since upgrading to 12.10 I can't do this, when I try I get the message:

```
SIOCSIFHWADDR: Device or resource busy - You may need to down the interface
```

I checked online, and somewhere someone said that they were phasing out the "service" so instead I should try, "sudo stop network-manager", but I get the same message.

I've also tried using Macchanger and I get the same message, saying that the resource is busy.

Thank you.

---

### Post by GreatDanton on 2012-10-15
One workaround is to manually deselect enable networking at the top menu (take a look at the picture).

---

### Post by pqwoerituytrueiwoq on 2012-10-15
use this program: ***nm-connection-editor***
i have used it may times to change my mac

---

### Post by zika on 2012-10-16
Manually edit appropriate file in /etc/NetworkManager/system-connections/ ...
```
[802-3-ethernet]
...
mac-address=xx:xx:xx:xx:xx:xx
...
```To work with these files from CLI:```
nmcli con down id Name_of_the_file_in _folder_given_above
nmcli con up id Name_of_the_file_in _folder_given_above
```...

---

### Post by SlugSlug on 2012-10-16
or down it with 
```
sudo ifconfig wlan0 down
```bring it back with 

```
sudo ifconfig wlan0 up
```

---

