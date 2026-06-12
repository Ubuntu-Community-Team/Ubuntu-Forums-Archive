---
title: "Wifi Authentication"
date: 2012-07-02
forum: System76 Support
---

### Post by stangdaman on 2012-07-02
I've been having an issue on my Pangolin with wifi authentication since upgrading to 12.04. On boot up sometimes I connect right away to the network but than other times I just get the spinning graphic non stop in the upper right and then get prompted to enter my password which is saved and is correct as entered. When this happens it will never connect no matter how many times I enter it but sometimes a reboot will. other times this takes multiple reboots. 

I've noticed that most of the time if it connects or doesn't it is trying to connect before I've entered my keyring password. I'm not sure if that has anything to do with the issue. I am seeing the issue on multiple networks and my work laptop, that runs Vista, doesn't seem to have any problems. Any ideas would be appreciated.

I'm also having a completely separate issue with multi monitor support where I can only run in mirrored mode but this looks like it might be a known issue. Thanks in advance for the support.

---

### Post by ajgreeny on 2012-07-02
For your wifi problem, which I think sounds the same as mine on an old laptop with Lubuntu 12.04, but the same network manager as Ubuntu 12.04, try temporarily removing the wireless security, or changing it from WPA-PSK to WPA2-PSK, or vice versa, and then re-entering the password.

I have absolutely no idea why it worked for me, but it did, and I never have a problem now connecting quickly after booting.  All this assumes, of course, that you are using one or other of the WPA security systems.  I have no idea if it will work if you are on WEP, but you could try it; it will only take a couple of minutes.

---

