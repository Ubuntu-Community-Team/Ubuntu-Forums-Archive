---
title: "Help-&quot;wifi not managed&quot;"
date: 2012-01-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Danny1977 on 2012-01-02
hi everyone, I have an issue with my wifi on a lenovo j3000 desktop, i have a dlink wda 1320 pci card installed, the network manager picks up the ethernet no problem and establishes a connection. I checked the help pages in the documentation and cannot find any hardware or driver issues. It was working great using a live cd. The pull down menu shows that the wireless adapter is not being managed. I have Ubuntu 12.04 installed. Any help is much appreciated. It is driving me crazy.](*,)

---

### Post by Iowan on 2012-01-02
Moved to **Ubuntu +1 (Precise Pangolin)**

---

### Post by wildmanne39 on 2012-01-02
Hi, 12.04 is unstable and is just for testing all question for it should be directed here.
[http://ubuntuforums.org/forumdisplay.php?f=412](http://ubuntuforums.org/forumdisplay.php?f=412)
Thanks

---

### Post by ronacc on 2012-01-03
When you say it connects to the ethernet do you mean wired or do you mean wireless ? Check your network connections and make sure your wireless is shown and check the settings .If your card requires firmware or proprietary driver you may need to add them , go to "system settings > additional drivers .

---

### Post by grahammechanical on 2012-01-03
The techniques for solving wireless problems are the same whatever version of Ubuntu we are using. And we do have a section called Networking and wireless. You can find suggestions in that section. The best that I can offer is this link:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

You will need to provide the information suggested by that guide. What steps have you taken to fix this problem? You might have to undo some of those steps. So, we need to know this.

It is my guess (and it is just a guess) that the message "not managed" means that network manager does not have control over the wireless adapter. This can happen if some other wireless manager has also been installed.

There are two commands that you can run:

```
cat /etc/network/interfaces
```

That will print the contents of the file interfaces. What is listed there? It should only be

> auto lo
iface lo inet loopback

If there is anything else written there then run this command

```
gksudo gedit /etc/network/interfaces
```

That will open the Gedit editor with administrator privileges and it will also load the file interfaces. You can then edit the file to remove any unnecessary lines and save it.

Then reboot. And you may find that Network manager is now managing your wireless adapter. Or may be not. Without more information it is not easy to come up with a fix.

Regards.

---

### Post by effenberg0x0 on 2012-01-04
I've seen a couple cases in which when the option "download updates during install" is used, it causes a static connection to persist after the install. In such cases, you can find stuff like this in /etc/network/interfaces:
```

auto wlan0 #Assuming wlan0 is the wlan card, found via iwconfig
iface wlan0 inet dhcp
wpa-ssid SomeSSID
wpa-psk SomePassword

```This should all be removed or commented out:
```

#auto wlan0
#iface wlan0 inet dhcp
#wpa-ssid SomeSSID
#wpa-psk SomePassword
 
```However, the wlan card is still not managed until it is set at **/etc/NetworkManager/NetworkManager.conf**. Some older Ubuntu seem to use **/etc/NetworkManager/nm-system-settings.conf**. One must make sure this file is set like this:
```

[ifupdown] 
managed=**true**

```

---

