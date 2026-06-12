---
title: "Hostapd passphrase issues"
date: 2010-11-06
forum: Server Platforms
---

### Post by Tombuddy on 2010-11-06
I really hope someone can help me out here. I am using Ubuntu server 10.10 and having an issue with hostapd daemon on reboot. Every time I restart the server, the hostapd daemon properly activates and my wireless network becomes visible. However, if I try to reconnect any clients the client reports that the wpa passphrase is incorrect.

Once I run sudo /etc/init.d/hostapd restart and wait about 10 seconds for the bridge to come back up everyone can connect fine again

Anyone have any suggestions? If I can't figure out a better workaround can anyone tell me how to run /etc/init.d/hostapd restart automatically after the system comes up?

---

