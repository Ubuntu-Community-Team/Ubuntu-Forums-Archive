---
title: "How do I make a wireless network the default on my Starling netbook"
date: 2011-07-18
forum: System76 Support
---

### Post by tc101 on 2011-07-18
A few days ago I tried to connected to a neighbor's wireless network.  I didn't have the password so I didn't get in.  This was not as unethical as it might sound and I will explain the details if you want, but it is not my reason for asking the question.

Now every time I start my netbook, it tries to connect to  the neighbors network instead of our home network.  I have  to  go  in and select our home network every time I turn on the computer.  How do I make the home network the default again?

---

### Post by isantop on 2011-07-19
Ubuntu's network manager will try to connect to the strongest connection available, so I'm guessing the neighbor's WiFi is broadcasting more powerfully than your router is. What you can do is erase the configuration for your neighbor's WiFi, which will prevent it from trying to connect there. Click on the network icon in your upper panel, then click on "Edit Connections..." Click on the wireless tab, then find the settings for your neighbor's WiFi. Click on it, then click delete. Your Starling will now not try to connect to their WiFi, and should favor yours instead.

---

